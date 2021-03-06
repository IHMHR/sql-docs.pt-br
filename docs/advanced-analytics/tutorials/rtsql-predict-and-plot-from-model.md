---
title: Prever e diagrama de modelo de (R no início rápido do SQL) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3809b8f6dbf84de04b84c7f4a6bdd5c492e2bdcd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="predict-and-plot-from-model-r-in-sql-quickstart"></a>Prever e diagrama de modelo de (R no início rápido do SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Para executar _pontuação_ usando novos dados, obter um dos modelos treinados da tabela e, em seguida, chamar um novo conjunto de dados no qual basear as previsões. A pontuação é um termo usado muitas vezes em ciência de dados para significar a geração de previsões, as probabilidades ou outros valores com base nos novos dados inseridos em um modelo treinado.

## <a name="create-the-table-of-new-speeds"></a>Criar a tabela de novas velocidades

Notou que os dados de treinamento originais param em uma velocidade de 25 milhas por hora? Isso ocorre porque os dados originais são baseados em um teste de 1920.

Poderíamos imaginar quanto tempo levaria um automóvel da década de 1920 para parar, supondo que ele poderia alcançar uma velocidade de 60 mph ou até mesmo 100 mph? Para responder essa pergunta, você deve fornecer alguns novos valores de velocidade.

```sql
CREATE TABLE [dbo].[NewCarSpeed]([speed] [int] NOT NULL,
    [distance] [int]  NULL) ON [PRIMARY]
GO
INSERT [dbo].[NewCarSpeed] (speed)
VALUES (40),  (50),  (60), (70), (80), (90), (100)
```

## <a name="predict-stopping-distance"></a>Prever a distância de parada

Agora, sua tabela pode conter vários modelos de R, todos criados com diferentes parâmetros ou algoritmos ou treinados em diferentes subconjuntos de dados.

![rsql_basictut_listofmodels](media/rsql-basictut-listofmodels.png)

Para obter previsões com base em um modelo específico, você deve escrever um script SQL que faz o seguinte:

1. Obtém o modelo desejado
2. Obtém os novos dados de entrada
3. Chama uma função de previsão de R que é compatível com o modelo

Neste exemplo, porque o modelo se baseia o **rxLinMod** algoritmo fornecido como parte do **RevoScaleR** pacote, chame o [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) função, em vez de R genérico `predict` função.

```sql
DECLARE @speedmodel varbinary(max) = (SELECT model FROM [dbo].[stopping_distance_models] WHERE model_name = 'latest model');
EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
            current_model <- unserialize(as.raw(speedmodel));
            new <- data.frame(NewCarData);
            predicted.distance <- rxPredict(current_model, new);
            str(predicted.distance);
            OutputDataSet <- cbind(new, ceiling(predicted.distance));
            '
    , @input_data_1 = N' SELECT speed FROM [dbo].[NewCarSpeed] '
    , @input_data_1_name = N'NewCarData'
    , @params = N'@speedmodel varbinary(max)'
    , @speedmodel = @speedmodel
WITH RESULT SETS (([new_speed] INT, [predicted_distance] INT))
```

+ Use uma instrução SELECT para obter um único modelo de tabela e passe-o como um parâmetro de entrada.
+  Depois de recuperar o modelo da tabela, chame a função `unserialize` no modelo.

    > [!TIP] 
    > Verifique também o novo [funções de serialização](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) fornecida pelo RevoScaleR, que oferece suporte a [em tempo real de pontuação](../../advanced-analytics/real-time-scoring.md).
+  Aplicar a função `rxPredict` com os argumentos apropriados para o modelo e fornecer os novos dados de entrada.
+  No exemplo, o `str` função é adicionada durante a fase de teste para verificar se o esquema de dados que está sendo retornado de R. Você pode remover a instrução mais tarde.
+ Os nomes de coluna usados no script R não são necessariamente passados para a saída do procedimento armazenado. Aqui usamos a cláusula com resultados para definir alguns novos nomes de coluna.

**Resultados**

![rsql_basictut_scoringresults_smalldata](media/rsql-basictut-scoringresults-smalldata.PNG)

## <a name="perform-scoring-in-parallel"></a>Executar pontuação em paralelo

As previsões voltaram rapidamente nesse pequeno conjunto de dados. Porém, suponhamos que você precisasse de muitas previsões com muita rapidez? Há muitas maneiras de acelerar as operações no SQL Server, mais se as operações podem ser processadas em paralelo. Para a pontuação específica, uma maneira fácil é adicionar o parâmetro *@parallel* para `sp_execute_external_script` e definir o valor para **1**.

Suponhamos que você tenha uma tabela muito maior de velocidades de carro possíveis, compondo centenas de milhares de valores. Há muitos scripts T-SQL de exemplo da comunidade para ajudar você a gerar tabelas de números, portanto, não os reproduziremos aqui. Digamos que você tenha uma coluna contendo muitos números inteiros e deseja usá-lo como entrada para `speed` no modelo.

Para fazer isso, basta executar a mesma consulta de previsão, mas substituir o conjunto de dados maior e adicionar o `@parallel = 1` argumento.

```sql
DECLARE @speedmodel varbinary(max) = (select model from [dbo].[stopping_distance_models] where model_name = 'default model');
EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
            current_model <- unserialize(as.raw(speedmodel));
            new <- data.frame(NewCarData);
            predicted.distance <- rxPredict(current_model, new);
            OutputDataSet <- cbind(new, ceiling(predicted.distance));
            '
    , @input_data_1 = N' SELECT [speed] FROM [dbo].[HugeTableofCarSpeeds] '
    , @input_data_1_name = N'NewCarData'
    , @parallel = 1
    , @params = N'@speedmodel varbinary(max)'
    , @speedmodel = @speedmodel
WITH RESULT SETS (([new_speed] INT, [predicted_distance] INT))
```

+ Execução paralela geralmente fornece benefícios somente quando estiver trabalhando com dados muito grandes. O mecanismo de banco de dados SQL pode decidir que a execução paralela não será necessário. Além disso, a consulta de SQL que obtém seus dados deve ser capaz de gerar um plano de consulta paralelo.

+ Ao usar a opção para execução paralela, você **deve** especificar o esquema de resultados de saída com antecedência, usando a cláusula WITH RESULT SETS. Especificar o esquema de saída com antecedência permite ao SQL Server agregar os resultados de vários conjuntos de dados paralelos que, caso contrário, poderia conter esquemas desconhecidos.

+ Se você estiver *treinamento* um modelo, em vez de *pontuação*, este parâmetro geralmente não têm um efeito. Dependendo do tipo de modelo, a criação de modelo pode exigir que todas as linhas sejam lidas antes da criação de resumos.

+ Para obter os benefícios do processamento paralelo ao treinar seu modelo, é recomendável que você use uma da **RevoScaleR** algoritmos. Esses algoritmos são projetados para distribuir o processamento automaticamente, mesmo se você não especificar <code>@parallel =1</code> na chamada para `sp_execute_external_script`. Para obter orientação sobre como obter o melhor desempenho com algoritmos de RevoScaleR, consulte [distribuída e a computação paralela com ScaleR no Microsoft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing).

## <a name="create-an-r-plot-of-the-model"></a>Criar uma plotagem R do modelo

Muitos clientes, incluindo o SQL Server Management Studio, não podem exibir diretamente gráficos plotados criado usando [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Em vez disso, o processo geral para gerar gráficos de R é criar o gráfico como parte do seu código R e, em seguida, gravar a imagem em um arquivo.

Como alternativa, você pode retornar o objeto serializado plotagem binários para qualquer aplicativo que pode exibir imagens.

O exemplo a seguir demonstra como criar um gráfico simples usando uma função de plotagem incluída por padrão no R. A imagem é enviada para o arquivo especificado e para uma variável SQL pelo procedimento armazenado.

```sql
 EXECUTE sp_execute_external_script
 @language = N'R'
 , @script = N'
     imageDir <- ''C:\\temp\\plots'';
     image_filename = tempfile(pattern = "plot_", tmpdir = imageDir, fileext = ".jpg")
     print(image_filename);
     jpeg(filename=image_filename,  width=600, height = 800);
     print(plot(distance~speed, data=InputDataSet, xlab="Speed", ylab="Stopping distance", main = "1920 Car Safety"));
     abline(lm(distance~speed, data = InputDataSet));
     dev.off();
     OutputDataSet <- data.frame(data=readBin(file(image_filename, "rb"), what=raw(), n=1e6));
     '
  , @input_data_1 = N'SELECT speed, distance from [dbo].[CarSpeed]'
  WITH RESULT SETS ((plot varbinary(max)));
```

+ O `tempfile` função retorna uma cadeia de caracteres que pode ser usada como um nome de arquivo, mas o arquivo ainda não foi gerado.
+ Para argumentos para `tempfile`, você pode especificar um prefixo e extensão de arquivo, bem como o diretório. Para verificar o nome completo do arquivo e o caminho, imprimir uma mensagem usando `str()`.
+ A função `jpeg` cria um dispositivo R com os parâmetros especificados.
+ Depois de criar o gráfico, você pode adicionar mais recursos visuais a ele. Nesse caso, uma linha de regressão é adicionada usando `abline`.
+ Após terminar de adicionar os recursos de plotagem, é necessário fechar o dispositivo de gráficos usando a função `dev.off()`.
+ A função `readBin` usa um arquivo para leitura, uma especificação de formato e o número de registros. O `rb`* * ' palavra-chave indica que o arquivo for binário em vez de texto.

**Resultados**

![rsql_basictut_plotresult_small](media/rsql-basictut-plotresult-small.png)

Se você quiser criar gráficos mais elaborados usando alguns dos excelentes pacotes de gráficos para R, recomendamos os artigos a seguir. Ambas as opções exigem o popular pacote **ggplot2**.

+ [Classificação de empréstimo usando o SQL Server 2016 R Services](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/09/27/loan-classification-using-sql-server-2016-r-services/): cenário de ponta a ponta com base em dados de seguros. Requer o **remodelar** pacote.
+ [Criar gráficos e gráficos usando R](../../advanced-analytics/tutorials/walkthrough-create-graphs-and-plots-using-r.md)

## <a name="conclusions"></a>Conclusões

A integração de R com o SQL Server torna mais fácil implantar soluções de R em grande escala, aproveitando os melhores recursos de R e de bancos de dados relacionais, para manipulação de dados de alto desempenho e rápida análise de R. 

Consulte estes recursos adicionais para obter mais exemplos de R:

+  [Tutoriais do SQL Server R](../../advanced-analytics/tutorials/sql-server-r-tutorials.md)

    Continue aprendendo sobre as soluções R com o SQL Server, por meio de cenários de ponta a ponta criados pelas equipes de desenvolvimento de ciência de dados da Microsoft e serviços de R.

+ [Tutoriais do SQL Server Python](../../advanced-analytics/tutorials/sql-server-python-tutorials.md)

    Para SQL Server 2017, use o poder do contexto de computação remoto e escalonável algoritmo com a linguagem Python.

+ [Tutoriais e dados de exemplo para o Microsoft R](https://docs.microsoft.com/r-server/r/tutorial-introduction)

    Saiba como usar os novos pacotes de RevoScaleR para criar modelos e transformar dados.

+ [Introdução ao MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)

    Saiba mais sobre a algoritmos da Microsoft Research de aprendizado de máquina rápida e escalonável.
