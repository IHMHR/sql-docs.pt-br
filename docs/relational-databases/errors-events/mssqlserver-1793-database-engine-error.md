---
title: MSSQLSERVER_1793 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 808db1d0-acc1-41d0-9287-8a5455001a02
caps.latest.revision: 6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d17e5512007c3aa0a1259114f4f650c23ea6fe0a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver1793"></a>MSSQLSERVER_1793
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalhes  
  
|||  
|-|-|  
|Nome do produto|SQL Server|  
|ID do evento|1793|  
|Origem do evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbólico|FILESTREAM_BASEDATA_NEED_SAME_PARTITION|  
|Texto da mensagem|Não é possível remover o índice '%.*ls', pois um esquema de partição não está especificado para os dados de FILESTREAM.|  
  
## <a name="explanation"></a>Explicação  
Essa mensagem ocorre quando você tenta remover um índice clusterizado de uma tabela que contém dados FILESTREAM e especifica uma cláusula **MOVE TO** para os dados base, mas não especifica uma cláusula **FILESTREAM_ON** para os dados FILESTREAM.  
  
## <a name="user-action"></a>Ação do usuário  
Ao remover um índice clusterizado em uma tabela que contém dados FILESTREAM, use um das seguintes opções:  
  
-   Especifique uma cláusula **MOVE TO** para os dados base e uma cláusula **FILESTREAM_ON** para os dados FILESTREAM.  
  
-   Não especifique uma cláusula **MOVE TO** para os dados base nem uma cláusula **FILESTREAM_ON** para os dados FILESTREAM.  
  
O exemplo a seguir falha porque um esquema de partição foi especificado para os dados básicos, mas não foi especificado para os dados FILESTREAM.  
  
```Transact-SQL  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY] )  
GO  
```  
  
O exemplo a seguir é bem-sucedido, porque uma cláusula **MOVE TO** para os dados base e uma cláusula **FILESTREAM_ON** para os dados FILESTREAM são especificadas.  
  
```Transact-SQL  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY], filestream_on 'default' )  
GO  
```  
  
O exemplo a seguir também é bem-sucedido, porque uma cláusula **MOVE TO** para os dados base e uma cláusula **FILESTREAM_ON** para os dados FILESTREAM não são especificadas.  
  
```Transact-SQL  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF )  
GO  
```  
  
