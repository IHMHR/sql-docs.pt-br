---
title: sys.DM os_memory_objects (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_memory_objects
- sys.dm_os_memory_objects
- sys.dm_os_memory_objects_TSQL
- dm_os_memory_objects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_objects dynamic management view
ms.assetid: 5688bcf8-5da9-4ff9-960b-742b671d7096
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 11efea1b06a23b4d5345b6ee325147955e91a98d
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmosmemoryobjects-transact-sql"></a>sys.dm_os_memory_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retorna objetos da memória que estão alocados no momento pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Você pode usar **sys.DM os_memory_objects** para analisar o uso de memória e identificar memória possíveis perdas.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**memory_object_address**|**varbinary(8)**|Endereço do objeto de memória. Não permite valor nulo.|  
|**parent_address**|**varbinary(8)**|Endereço do objeto de memória pai. Permite valor nulo.|  
|**pages_allocated_count**|**Int**|**Aplica-se a**: do [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ao [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Número de páginas que são alocadas por esse objeto. Não permite valor nulo.|  
|**pages_in_bytes**|**bigint**|**Aplica-se a**: do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ao [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Quantidade de memória em bytes alocada por essa instância do objeto de memória. Não permite valor nulo.|  
|**creation_options**|**Int**|Somente para uso interno. Permite valor nulo.|  
|**bytes_used**|**bigint**|Somente para uso interno. Permite valor nulo.|  
|**type**|**nvarchar(60)**|Tipo de objeto de memória.<br /><br /> Isso indica algum componente à qual pertence este objeto de memória ou a função do objeto de memória. Permite valor nulo.|  
|**name**|**varchar(128)**|Somente para uso interno. Anulável.|  
|**memory_node_id**|**smallint**|ID de um nó de memória que está sendo usado por esse objeto de memória. Não permite valor nulo.|  
|**creation_time**|**datetime**|Somente para uso interno. Permite valor nulo.|  
|**max_pages_allocated_count**|**Int**|**Aplica-se a**: do [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ao [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Número máximo de páginas alocadas por esse objeto de memória. Não permite valor nulo.|  
|**page_size_in_bytes**|**Int**|**Aplica-se a**: do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ao [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Tamanho das páginas em bytes alocadas por esse objeto. Não permite valor nulo.|  
|**max_pages_in_bytes**|**bigint**|Quantidade máxima de memória sempre usada por esse objeto de memória. Não permite valor nulo.|  
|**page_allocator_address**|**varbinary(8)**|Endereço de memória do alocador de página. Não permite valor nulo. Para obter mais informações, consulte [sys.DM os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md).|  
|**creation_stack_address**|**varbinary(8)**|Somente para uso interno. Permite valor nulo.|  
|**sequence_num**|**Int**|Somente para uso interno. Permite valor nulo.|  
|**partition_type**|**Int**|O tipo de partição:<br /><br /> 0 - objeto não particionável de memória<br /><br /> 1 - objeto de memória particionável, atualmente, não é particionado<br /><br /> 2 - o objeto de memória particionável, particionado por nó NUMA. Em um ambiente com um único nó NUMA, isso é equivalente a 1.<br /><br /> 3 - o objeto de memória particionável, particionado por CPU.|  
|**contention_factor**|**real**|Um valor que especifica contenção neste objeto de memória, com 0 indicando que não há contenção. O valor é atualizado sempre que um determinado número de alocações de memória feito contenção refletindo durante esse período. Aplica-se somente aos objetos de memória isenta de threads.|  
|**waiting_tasks_count**|**bigint**|Número de esperas nesse objeto de memória. Esse contador é incrementado sempre que a memória é alocada do objeto de memória. O incremento é o número de tarefas que estão aguardando para acesso a este objeto de memória. Aplica-se somente aos objetos de memória isenta de threads. Este é um valor de esforço melhor sem uma garantia de exatidão.|  
|**exclusive_access_count**|**bigint**|Especifica a frequência na qual esse objeto de memória foi acessado exclusivamente. Aplica-se somente aos objetos de memória isenta de threads.  Este é um valor de esforço melhor sem uma garantia de exatidão.|  
|**pdw_node_id**|**Int**|**Aplica-se a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> O identificador para o nó que essa distribuição é no.|  
  
 **partition_type**, **contention_factor**, **waiting_tasks_count**, e **exclusive_access_count** ainda não foram implementadas no [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
## <a name="permissions"></a>Permissões

Em [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requer `VIEW SERVER STATE` permissão.   
Em [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], requer o `VIEW DATABASE STATE` no banco de dados.   

## <a name="remarks"></a>Remarks  
 Os objetos de memória são heaps. Eles fornecem alocações que possuem uma granularidade maior do que a fornecida pelos administradores de memória. Os componentes do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usam objetos de memória, em vez de administradores de memória. Os objetos de memória usam a interface do alocador de página do administrador de memória para alocar páginas. Eles não usam interfaces de memória virtuais ou compartilhadas. Dependendo dos padrões de alocação, os componentes podem criar tipos diferentes de objetos de memória para alocar regiões de tamanho arbitrário.  
  
 O tamanho de página típico para um objeto de memória é 8 KB. Entretanto, objetos de memória incrementais podem ter tamanhos de página que variam de 512 bytes a 8 KB.  
  
> [!NOTE]  
>  O tamanho de página não é uma alocação máxima. Na verdade, o tamanho de página é a granularidade de alocação com suporte oferecida por um alocador de página e é implementado por um administrador de memória. Você pode solicitar alocações com mais de 8 KB de objetos de memória.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir retorna a quantidade de memória alocada em cada tipo de objeto de memória.  
  
```  
SELECT SUM (pages_in_bytes) as 'Bytes Used', type   
FROM sys.dm_os_memory_objects  
GROUP BY type   
ORDER BY 'Bytes Used' DESC;  
GO  
```  
  
## <a name="see-also"></a>Consulte também  
  [Sistema operacional SQL Server relacionadas exibições de gerenciamento dinâmico &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)  
  
  


