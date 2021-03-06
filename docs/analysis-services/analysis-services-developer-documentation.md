---
title: Documentação do desenvolvedor do Analysis Services | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 978819f3b8af369942dde2c3c18d6ca117489633
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="analysis-services-developer-documentation"></a>Documentação do desenvolvedor do Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]

No Analysis Services, quase todos os objetos e carga de trabalho são programável e geralmente não há mais de uma abordagem para escolher.  Opções incluem escrever um código gerenciado, script ou usando os padrões abertos como XMLA e MSOLAP se seus requisitos de solução impedirem usando o .NET framework.

## <a name="what-you-can-accomplish-in-code"></a>O que você pode fazer no código
Cenários de programação típicos incluem o servidor e implantação de banco de dados, administração, modelo e criação de banco de dados e acesso a dados de seus aplicativos personalizados e relatórios que consomem dados do Analysis Services. Comum a todos esses cenários é uma fixa arquitetura e o objeto de definição hierarquia, com operações bem compreendidas que abrangem a definição de dados, processamento e cargas de trabalho de consulta.

Embora os objetos e cargas de trabalho são programáveis, eles não são extensíveis. Especificamente, você não pode criar cartuchos de dados personalizados que recuperam dados de fontes de dados sem suporte, personalizam ou substituir os comportamentos de mecanismo de fórmula ou armazenamento, nem você pode criar novos tipos de objeto de metadados em um servidor, o banco de dados ou o modelo.

Para elaborar ainda mais o último ponto sobre a criação de novos tipos de objeto: enquanto você não pode criar um novo tipo de objeto, você pode criar objetos calculados criados de código ou expressões em tempo de execução. Nem tudo em seu modelo precisa ser predefinidos e mapeado para uma estrutura de dados existente. Além disso, você pode estender o esquema por meio de anotações no AMO para transmitir informações específicas do objeto para o aplicativo cliente.

## <a name="choose-a-platform-or-approach-to-development"></a>Escolha uma plataforma ou uma abordagem de desenvolvimento
O Analysis Services fornece várias maneiras de personalizar uma solução por meio de código, mas a maioria dos desenvolvedores usar as APIs gerenciadas ou o script.

- APIs gerenciadas incluem [AMO e TOM](http://msdn.microsoft.com/library/mt436122.aspx) para definição de dados e tarefas administrativas, e [ADOMD.NET](http://msdn.microsoft.com/library/mt465769.aspx) para suporte a consultas no código do cliente. No SQL Server 2016, o AMO é atualizado para usar os novos metadados de tabela para modelos criados ou atualizados para o nível de compatibilidade 1200 e superior.

- Script geralmente pode obter os mesmos resultados como um programa executável, possivelmente menos trabalho.

  - Você pode escrever um script do PowerShell usando os componentes do Analysis Services PowerShell que chamam os tipos de AMO diretamente. No PowerShell, você também pode criar e executar o ASSL/XMLA ou script TMSL (no JSON).

  - ASSL e TMSL são linguagens de script que fornecem os objetos usados em descobrir e executar operações. Que tipo de script que você usa depende do servidor, banco de dados ou modelo subjacente.

  - Modelos de tabela ou bancos de dados no nível de compatibilidade 1200 e superior usam o modelo de script TMSL (linguagem tabela), que está em JSON.

  - Modelos multidimensionais e tabulares em níveis de compatibilidade 1050-1103 usar Scripting linguagem ASSL (Analysis Services), que é a extensão de serviços de análise do padrão aberto XMLA.

  - Você pode gerar script ASSL ou TMSL no Management Studio. Você também pode usar **Exibir código** no SQL Server Data Tools para exibir a definição de modelo em ASSL ou TMSL.

- Embora seja possível criar uma solução baseada em padrões abertos de XMLA e MDX, é muito raro para fazer isso. Não há nenhuma documentação diferente de XMLA e referência MDX para ajudar você e a maioria dos comunidade e suporte do fórum desenhos de experiências com .NET ou tecnologias (MSOLAP) nativas.

## <a name="programming-in-analysis-services"></a>Programação do Analysis Services
[Programação de mineração de dados](../analysis-services/data-mining-programming.md) descreve as abordagens que criam soluções que incluem objetos de mineração de dados.

[Programação de modelo multidimensional](../analysis-services/multidimensional-models/multidimensional-model-programming.md) descreve as tarefas de desenvolvimento e abordagens para integrar objetos de modelo multidimensional em uma solução personalizada.

[Tabela de modelo de programação para 1200 de nível de compatibilidade e superior](../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md)
**novo no SQL Server 2016**.  Resume as interfaces e as linguagens de script usadas para trabalhar com a tabela 1200 e maior modelos programaticamente.

[Programação de modelo tabular para 1050 de níveis de compatibilidade por meio de 1103](../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md) esta documentação é destinada a desenvolvedores que dão suporte a modelos de tabela em níveis de compatibilidade anteriores. Ele descreve as extensões CSDL que definem um modelo de tabela em sintaxe XML. Ele também inclui informações sobre a sintaxe e as definições de modelo de objeto de tabela.

[Analysis Services Management Objects (AMO)](https://msdn.microsoft.com/library/mt436122.aspx) documentação de referência do desenvolvedor para o provedor gerenciado, Analysis Services Management Objects (AMO) para a definição de dados e administração, inclusive processamento.

[O ADOMD.NET](http://msdn.microsoft.com/library/mt465769.aspx) documentação de referência do desenvolvedor para o provedor gerenciado, ADOMD.NET, usado para dados programáticos acessar e consultar as cargas de trabalho.

[Conjuntos de linhas de esquema do Analysis Services](../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md) descreve os conjuntos de linhas de esquema que fornecem informações sobre o estado do servidor, as operações de servidor e objetos de banco de dados.

[XML for Analysis &#40;XMLA&#41; referência](../analysis-services/xmla/xml-for-analysis-xmla-reference.md) conceitos de XMLA descreve que podem ajudá-lo a entender como o XMLA contribui com sua solução personalizada. Ele também descreve o nível de conformidade com a especificação do XMLA 1.1.

[Linguagem de script do Analysis Services &#40;ASSL para XMLA&#41; ](../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md) descreve as extensões ASSL para XMLA. O ASSL fornece uma definição de dados e uma linguagem de manipulação para os modelos multidimensionais do Analysis Services que complementa a especificação de XMLA.

[Linguagem de script de modelo de tabela &#40;TMSL&#41; referência](../analysis-services/tabular-model-scripting-language-tmsl-reference.md) TMSL é uma representação JSON de modelos tabulares no nível de compatibilidade 1200 e superior. Definições de objeto são com base em construções de metadados de tabela como tabela, coluna e relação em vez de metadados multidimensionais que possam estar familiarizado se você for novo para modelagem de dados do Analysis Services no modo de tabela.

[Referência do Analysis Services PowerShell](../analysis-services/powershell/analysis-services-powershell-reference.md) documenta os cmdlets usados para funções administrativas, mais o uso geral **Invoke-ASCmd** cmdlet que aceita qualquer script ou consulta como entrada.

## <a name="see-also"></a>Consulte também
[Referência técnica ](../analysis-services/powershell/technical-reference-ssas.md) 
 [de consulta e referência de linguagem de expressão &#40;do Analysis Services&#41;](http://msdn.microsoft.com/library/gg492188.aspx)
