---
title: MSSQLSERVER_2530 | Microsoft Docs
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
ms.assetid: 5d4be07a-38a5-4b25-819c-4dcb4636cc15
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0f3c112576fe769325c6ded074afd407d49ad340
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver2530"></a>MSSQLSERVER_2530
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalhes  
  
|||  
|-|-|  
|Nome do produto|SQL Server|  
|ID do evento|2530|  
|Origem do evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbólico|DBCC_INDEX_IS_OFFLINE|  
|Texto da mensagem|O índice "%.*ls" na tabela "%.\*ls" está desabilitado.|  
  
## <a name="explanation"></a>Explicação  
A instrução DBCC não pode continuar porque o índice especificado está desabilitado. Depois que um índice é desabilitado, ele permanece em estado desabilitado até que seja reconstruído ou descartado e recriado.  
  
## <a name="user-action"></a>Ação do usuário  
  
1.  Habilite o índice desabilitado usando um dos seguinte métodos:  
  
    -   Instrução ALTER INDEX com a cláusula REBUILD  
  
    -   CREATE INDEX com a cláusula DROP_EXISTING  
  
    -   DBCC DBREINDEX  
  
2.  Execute novamente a instrução DBCC.  
  
## <a name="see-also"></a>Consulte Também  
[Habilitar índices e restrições](~/relational-databases/indexes/enable-indexes-and-constraints.md)  
[ALTER INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/alter-index-transact-sql.md)  
[CREATE INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/create-index-transact-sql.md)  
[DBCC DBREINDEX &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-dbreindex-transact-sql.md)  
  
