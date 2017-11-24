---
title: sys.DM fts_outstanding_batches (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_fts_outstanding_batches
- dm_fts_outstanding_batches_TSQL
- sys.dm_fts_outstanding_batches_TSQL
- sys.dm_fts_outstanding_batches
dev_langs: TSQL
helpviewer_keywords:
- troubleshooting [SQL Server], full-text search
- sys.dm_fts_outstanding_batches dynamic management view
ms.assetid: c4d697ed-c906-4c28-b137-036a25e13c84
caps.latest.revision: "13"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ab9d21dfa1c3aefb34f59dde7d4af5141e483682
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmftsoutstandingbatches-transact-sql"></a>sys.dm_fts_outstanding_batches (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retorna informações sobre cada lote de indexação de texto completo.  
  
  |Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|ID do banco de dados|  
|catalog_id|**int**|Identificação do catálogo de texto completo.|  
|table_id|**int**|ID da tabela que contém o índice de texto completo.|  
|batch_id|**int**|ID do Lote|  
|memory_address|**varbinary (8)**|O endereço de memória do objeto do lote.|  
|crawl_memory_address|**varbinary (8)**|Endereço de memória do objeto de rastreamento (objeto pai).|  
|memregion_memory_address|**varbinary (8)**|Endereço de memória da região de memória da memória de compartilhamento de saída do host daemon do filtro (fdhost.exe).|  
|hr_batch|**int**|O código de erro mais recente do lote.|  
|is_retry_batch|**bit**|Indica se este é um lote de repetição:<br /><br /> 0 = Não<br /><br /> 1 = Sim|  
|retry_hints|**int**|Tipo de repetição necessária para o lote:<br /><br /> 0 = Nenhuma repetição<br /><br /> 1 = Repetição de multi-thread<br /><br /> 2 = Repetição de thread único<br /><br /> 3 = Repetição de único e multi-thread<br /><br /> 5 = Repetição final de multi-thread<br /><br /> 6 = Repetição final de thread único<br /><br /> 7 = Repetição final de único e multi-thread|  
|retry_hints_description|**nvarchar(120)**|Descrição do tipo de repetição necessária:<br /><br /> SEM REPETIÇÃO<br /><br /> REPETIÇÃO DE MULTI-THREAD<br /><br /> REPETIÇÃO DE THREAD ÚNICO<br /><br /> REPETIÇÃO DE ÚNICO E MULTI-THREAD<br /><br /> REPETIÇÃO FINAL DE MULTI-THREAD<br /><br /> REPETIÇÃO FINAL DE THREAD ÚNICO<br /><br /> REPETIÇÃO FINAL DE ÚNICO E MULTI-THREAD|  
|doc_failed|**bigint**|Número de documentos do lote que falharam.|  
|batch_timestamp|**timestamp**|O valor do carimbo de data/hora obtido quando o lote foi criado.|  
  
## <a name="permissions"></a>Permissões  
Em [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requer `VIEW SERVER STATE` permissão.   
Em [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] camadas Premium, requer o `VIEW DATABASE STATE` no banco de dados. Em [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] camadas Standard e Basic, requer o **administrador do servidor** ou um **administrador do Active Directory do Azure** conta.  
 
## <a name="examples"></a>Exemplos  
 O exemplo a seguir localiza o número de lotes que está sendo processado para cada tabela na instância de servidor.  
  
```  
SELECT database_id, table_id, COUNT(*) AS batch_count FROM sys.dm_fts_outstanding_batches GROUP BY database_id, table_id ;  
GO  
```  
  
## <a name="see-also"></a>Consulte também  
 [Pesquisa de texto completo e exibições de gerenciamento dinâmico de pesquisa semântica e funções &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Pesquisa de Texto Completo](../../relational-databases/search/full-text-search.md)  
  
  