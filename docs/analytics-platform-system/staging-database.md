---
title: Usando um banco de dados de preparo - Parallel Data Warehouse | Microsoft Docs
description: SQL Server Parallel Data Warehouse (PDW) usa um banco de dados de preparo para armazenar dados temporariamente durante o processo de carregamento.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 73822c1495fa5f83d9a8ba37325a025999f94530
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="using-a-staging-database-in-parallel-data-warehouse-pdw"></a>Usando um banco de dados de preparo no Parallel Data Warehouse (PDW)
SQL Server Parallel Data Warehouse (PDW) usa um banco de dados de preparo para armazenar dados temporariamente durante o processo de carregamento. Por padrão, o SQL Server PDW usa o banco de dados de destino do banco de dados temporário, o que pode causar a fragmentação de tabela. Para reduzir a fragmentação de tabela, você pode criar um banco de dados de preparo definido pelo usuário. Ou, quando a reversão de uma falha de carregamento não é uma preocupação, você pode usar o fastappend carregar modo para melhorar o desempenho, ignorando a tabela temporária e carregar diretamente na tabela de destino.  
  
## <a name="StagingDatabase"></a>Noções básicas de banco de dados de preparo  
Um *banco de dados de preparo* é um usuário criado PDW banco de dados que armazena dados temporariamente enquanto ele é carregado no dispositivo. Quando um banco de dados de preparo é especificado para uma carga, o dispositivo pela primeira vez, copia os dados para o banco de dados de preparo e, em seguida, copia os dados de tabelas temporárias no banco de dados de preparo para tabelas permanentes no banco de dados de destino.  
  
Quando um banco de dados de preparo não for especificado para uma carga, ServerPDW SQL cria as tabelas temporárias no banco de dados de destino e as usa para armazenar os dados carregados antes de ele insere os dados carregados em tabelas de destino permanente.  
  
Quando uma carga utiliza o *modo fastappend*, ServerPDW SQL ignora o uso de tabelas temporárias completamente e anexa os dados diretamente à tabela de destino. O modo fastappend melhora o desempenho de carga para cenários ELT onde os dados são carregados em uma tabela que é uma tabela temporária do ponto de vista do aplicativo. Por exemplo, um processo ELT pode carregar dados em uma tabela temporária, processar os dados eliminando eliminação e limpeza e, em seguida, insira os dados na tabela de fatos de destino. Nesse caso, não é necessário para PDW para carregar primeiro os dados em uma tabela temporária interna antes de inserir os dados na tabela temporária do aplicativo. O modo fastappend evita a etapa de carga extra, o que melhora significativamente o desempenho de carga. Para usar o modo fastappend, você deve usar o modo de várias transações, o que significa que a recuperação de uma falha ou anulada carga deve ser tratada pelo seu próprio processo de carregamento.  
  
**Benefícios do banco de dados de preparo**  
  
É o principal benefício de um banco de dados de preparo reduzir a fragmentação de tabela. Se um banco de dados de preparo não for usado, os dados são carregados em tabelas temporárias no banco de dados de destino. Quando tabelas temporárias são criadas e descartadas no banco de dados de destino, as páginas para as tabelas temporárias e tabelas permanentes se tornam intercaladas. Ao longo do tempo, a fragmentação de tabela ocorre e afeta o desempenho. Por outro lado, um banco de dados de preparo garante que as tabelas temporárias são criadas e descartadas em um espaço de arquivo separado que as tabelas permanentes.  
  
**Estruturas de tabela de banco de dados de preparo**  
  
A estrutura de armazenamento para cada tabela de banco de dados depende da tabela de destino.  
  
-   Para carregamento em um heap ou índice columnstore clusterizado, a tabela de preparo é um heap.  
  
-   Para carregamento em um índice clusterizado rowstore, a tabela de preparo é um índice clusterizado rowstore.  
  
## <a name="Permissions"></a>Permissões  
Requer a permissão de criar (para criar uma tabela temporária) do banco de dados de preparo. 

<!-- MISSING LINKS

For more information, see [Grant Permissions to load data](grant-permissions-to-load-data.md).  

-->
  
## <a name="CreatingStagingDatabase"></a>Práticas recomendadas para criar um banco de dados de preparo  
  
1.  Deve haver apenas um banco de dados de preparo por dispositivo. O banco de dados de preparo pode ser compartilhado por todos os trabalhos de carga para todos os bancos de dados de destino.  
  
2.  O tamanho do banco de dados de preparo é específica do cliente. Inicialmente, quando você primeiro preencher o dispositivo, o banco de dados de preparo deve ser grande o suficiente para acomodar os trabalhos de carregamento inicial. Esses trabalhos de carga tendem a ser grandes, como vários carregamentos podem ocorrer simultaneamente. Depois de concluíram os trabalhos de carregamento inicial e o sistema está em produção, o tamanho de cada carga de trabalho é provavelmente será menor. Quando as cargas são pequenas, você pode reduzir o tamanho do banco de dados de preparo para acomodar as carga menores. Para reduzir o tamanho, você pode remover o banco de dados de preparo e criá-la novamente com alocações menores de tamanho, ou você pode usar o [ALTER DATABASE](../t-sql/statements/alter-database-parallel-data-warehouse.md) instrução.  
  
    Ao criar o banco de dados de preparo, use as diretrizes a seguir.  
  
    -   O tamanho da tabela replicada deve ser o tamanho estimado, por nó de computação, de todas as tabelas replicadas serão carregados simultaneamente. Normalmente, o tamanho é 25-30 GB.  
  
    -   O tamanho da tabela distribuída deve ser o tamanho estimado, por dispositivo, de todas as tabelas distribuídas que irá carregar simultaneamente.  
  
    -   O tamanho do log é normalmente semelhante para o tamanho da tabela replicada.  
  
## <a name="Examples"></a>Exemplos  
  
### <a name="a-create-a-staging-database"></a>A. Criar um banco de dados de preparo 
O exemplo a seguir cria um teste banco de dados, Stagedb, para uso com todos os carrega no dispositivo. Suponha que você estima que cinco tabelas de tamanho de que 5 GB carregará simultaneamente replicadas. Essa simultaneidade resulta em alocar pelo menos 25 GB para o tamanho replicado. Suponha que você estima que seis distribuído tabelas de tamanhos 100, 200, 400, 500, 500 e 550 GB carregará simultaneamente. Essa simultaneidade resulta em alocar pelo menos 2250 GB para o tamanho da tabela distribuída.  
  
```sql  
CREATE DATABASE Stagedb  
WITH (  
  
    AUTOGROW = ON,  
  
    REPLICATED_SIZE = 25 GB,  
  
    DISTRIBUTED_SIZE = 2250 GB,  
  
    LOG_SIZE = 25 GB  
  
);  
```  

<!-- MISSING LINKS
 
## See Also  
[Common metadata query examples](metadata-query-examples.md)  

-->
  
