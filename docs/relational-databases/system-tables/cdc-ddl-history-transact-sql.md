---
title: ddl_history (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- cdc.ddl_history_TSQL
- cdc.ddl_history
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.ddl_history
ms.assetid: cb97ea71-da2f-441a-bbd2-db1f5f48ab49
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: c65fd834ac53f7d1835e9c7641dbe6d6fb78d082
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="cdcddlhistory-transact-sql"></a>cdc.ddl_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retorna uma linha para cada alteração de linguagem de definição de dados (DDL) feita nas tabelas que estão habilitadas para captura de dados de alteração. Você pode usar esta tabela para determinar quando uma alteração de DDL ocorre em uma tabela de origem e qual foi a alteração. As tabelas de origem que não tiverem tido alterações de DDL não terão entradas nesta tabela.  
  
 É recomendável não consultar diretamente as tabelas do sistema. Em vez disso, execute o [sp_cdc_get_ddl_history](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql.md) procedimento armazenado.  
   
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**source_object_id**|**Int**|A identificação da tabela de origem na qual a DDL foi aplicada.|  
|**object_id**|**Int**|ID da tabela de alteração associada a uma instância de captura da tabela de origem.|  
|**required_column_update**|**bit**|Indica que o tipo de dados de uma coluna capturada foi modificado na tabela de origem. Esta modificação alterou a coluna na tabela de alteração.|  
|**ddl_command**|**nvarchar(max)**|Instrução DDL aplicada à tabela de origem.|  
|**ddl_lsn**|**binary(10)**|Número de sequência de log (LSN) associado com a confirmação da modificação de DDL.|  
|**ddl_time**|**datetime**|Data e hora em que a alteração de DDL foi feita na tabela de origem.|  
  
## <a name="see-also"></a>Consulte também  
 [sys.sp_cdc_help_change_data_capture &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
  
  
