---
title: sys.pdw_health_component_status_mappings (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4272cfad-5ad7-493d-9edd-d9111619bda0
caps.latest.revision: 7
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4b2d572b79c15c369e33190c183c249de3b8fb0c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="syspdwhealthcomponentstatusmappings-transact-sql"></a>sys.pdw_health_component_status_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Define o mapeamento entre o [!INCLUDE[ssDW](../../includes/ssdw-md.md)] status do componente e os nomes definidos pelo fabricante do componente.  
  
|Nome da coluna|Tipo de dados|Description|Intervalo|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**Int**|Identificador exclusivo da propriedade.<br /><br /> property_id e identificação_do_componente physical_name formam a chave para este modo de exibição.|NOT NULL|  
|identificação_do_componente|**Int**|A ID do componente. Consulte [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> property_id e identificação_do_componente physical_name formam a chave para este modo de exibição.|NOT NULL|  
|physical_name|**nvarchar(32)**|Nome da propriedade conforme definido pelo fabricante.<br /><br /> property_id e identificação_do_componente physical_name formam a chave para este modo de exibição.|NOT NULL|  
|logical_name|**nvarchar(255)**|Nome da propriedade conforme definido pelo [!INCLUDE[ssDW](../../includes/ssdw-md.md)].|NOT NULL<br /><br /> 0 - a instância do dispositivo é exclusiva.<br /><br /> 1 - dispositivo instância não é exclusiva.|  
  
## <a name="see-also"></a>Consulte também  
 [SQL Data Warehouse e exibições de catálogo do Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
