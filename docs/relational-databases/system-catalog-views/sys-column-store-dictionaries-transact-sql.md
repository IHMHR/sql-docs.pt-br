---
title: sys. column_store_dictionaries (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.column_store_dictionaries_TSQL
- column_store_dictionaries
- column_store_dictionaries_TSQL
- sys.column_store_dictionaries
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_dictionaries catalog view
ms.assetid: 56efd563-2f72-4caf-94e3-8a182385c173
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 5a68d3d0b898b3acbccccb2a0e87c467692dccbe
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="syscolumnstoredictionaries-transact-sql"></a>sys.column_store_dictionaries (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Contém uma linha para cada dicionário usado em índices columnstore otimizados para memória xVelocity. Dicionários são usados para codificar alguns, mas não todos os tipos de dados; portanto, nem todas as colunas em um índice columnstore têm dicionários. Um dicionário pode existir como um dicionário primário (para todos os segmentos) e, possivelmente, para outros dicionários secundários usados para um subconjunto de segmentos da coluna.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**hobt_id**|**bigint**|A ID do heap ou o índice de árvore B (hobt) para a tabela que tem seu índice columnstore.|  
|**column_id**|**Int**|ID da coluna columnstore começando com 1. A primeira coluna tem ID = 1, a segunda coluna tem ID = 2, etc.|  
|**dictionary_id**|**Int**|Pode haver dois tipos de dicionários, global e locais, associados um segmento de coluna. Um dictionary_id 0 representa o dicionário global que é compartilhado entre todos os segmentos de colunas (uma para cada grupo de linhas) para essa coluna.|  
|**version**|**Int**|Versão de formato do dicionário.|  
|**type**|**Int**|Tipo de dicionário:<br /><br /> 1 – hash dicionário contendo **int** valores<br /><br /> 2 – Não usado<br /><br /> 3 – Dicionário de hash que contém valores de cadeia de caracteres<br /><br /> 4 – hash de dicionário contendo **float** valores<br /><br /> Para obter mais informações sobre dicionários, consulte [guia de índices Columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md).|  
|**last_id**|**Int**|A última ID de dados no dicionário.|  
|**entry_count**|**bigint**|Número de entradas no dicionário.|  
|**on_disc_size**|**bigint**|Tamanho do dicionário em bytes.|  
|**partition_id**|**bigint**|Indica a ID da partição. É exclusivo em um banco de dados.|  
  
## <a name="permissions"></a>Permissões  
 Todas as colunas requerem no mínimo a permissão VIEW DEFINITION na tabela. As colunas a seguir retornam nulo a menos que o usuário também tenha **selecione** permissão: last_id, entry_count, data_ptr.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obter mais informações, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Consulte também  
 [Exibições de catálogo de objeto&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Exibições de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Consultando o catálogo de sistema do SQL Server perguntas Frequentes](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Guia de Índices Columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [Guia de Índices Columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
  

