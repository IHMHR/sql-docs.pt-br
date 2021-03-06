---
title: Alterando módulos T-SQL compilados nativamente | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 010318a0-6807-47c3-8ecc-bb7cb60513f0
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8e6229b5b7c8ad03b6a8fbabb317d470eadb4c69
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="altering-natively-compiled-t-sql-modules"></a>Altering Natively Compiled T-SQL Modules
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  No [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] (e posterior) e no [!INCLUDE[ssSDS](../../includes/sssds-md.md)] você pode executar operações ALTER em procedimentos armazenados compilados nativamente e outros módulos do T-SQL compilados nativamente, como UDFs escalares e gatilhos usando a instrução ALTER.  
  
 Ao executar ALTER em um módulo do T-SQL compilado nativamente, o módulo é recompilado usando uma nova definição. Enquanto a recompilação estiver em andamento, a versão antiga do módulo continuará disponível para execução. Uma vez concluída a compilação, as execuções de módulo serão descarregadas e a nova versão do módulo será instalada. Ao alterar um módulo do T-SQL compilado nativamente, é possível modificar as opções a seguir.  
  
-   Parâmetros  
  
-   EXECUTE AS  
  
-   TRANSACTION ISOLATION LEVEL  
  
-   LANGUAGE  
  
-   DATEFIRST  
  
-   DATEFORMAT  
  
-   DELAYED_DURABILITY  
  
> [!NOTE]  
>  Os módulos do T-SQL compilados nativamente não podem ser convertidos em módulos compilados não nativamente. Os módulos do T-SQL compilados não nativamente não podem ser convertidos em módulos compilados nativamente.  
  
 Para obter mais informações sobre a funcionalidade ALTER PROCEDURE e a sintaxe, consulte [ALTER PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-procedure-transact-sql.md)  
  
 Você pode executar sp_recompile em módulos T-SQL compilados nativamente, o que faz com que o módulo recompile na próxima execução.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma tabela com otimização de memória (T1) e um procedimento armazenado compilado nativamente (SP1) que seleciona todas as colunas de T1. Em seguida, o SP1 é alterado para remover a cláusula EXECUTE AS, alterar LANGUAGE e selecionar apenas uma coluna (C1) de T1.  
  
```  
CREATE TABLE [dbo].[T1]  
(  
[c1] [int] NOT NULL,  
[c2] [float] NOT NULL,  
CONSTRAINT [PK_T1] PRIMARY KEY NONCLUSTERED ([c1])  
)WITH ( MEMORY_OPTIMIZED = ON , DURABILITY = SCHEMA_AND_DATA )  
GO  
  
CREATE PROCEDURE [dbo].[usp_1]  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH  
(  
 TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english'  
)  
 SELECT c1, c2 from dbo.T1  
END  
GO  
  
ALTER PROCEDURE [dbo].[usp_1]  
WITH NATIVE_COMPILATION, SCHEMABINDING  
AS BEGIN ATOMIC WITH  
(  
 TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'Dutch'  
)  
 SELECT c1 from dbo.T1  
END  
GO  
  
```  
  
  
