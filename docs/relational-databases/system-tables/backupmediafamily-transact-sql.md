---
title: backupmediafamily (Transact-SQL) | Microsoft Docs
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
- backupmediafamily
- backupmediafamily_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backupmediafamily system table
- backup media [SQL Server], backupmediafamily system table
ms.assetid: ee16de24-3d95-4b2e-a094-78df2514d18a
caps.latest.revision: 46
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: da7d59170e9ed3ed9a1808e03e792474c22afddd
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="backupmediafamily-transact-sql"></a>backupmediafamily (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contém uma linha para cada família de mídia. Se uma família de mídia residir em um conjunto de mídias espelhado, a família terá uma linha separada para cada espelho no conjunto de mídias. Essa tabela é armazenada no **msdb** banco de dados.  
    
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**media_set_id**|**Int**|Número de identificação exclusivo que identifica o conjunto de mídias do qual esta família é um membro. Referências **backupmediaset (media_set_id)**|  
|**family_sequence_number**|**tinyint**|Posição desta família de mídias no conjunto de mídias.|  
|**media_family_id**|**uniqueidentifier**|Número de identificação exclusivo que identifica a família de mídias. Pode ser NULL.|  
|**media_count**|**Int**|Número de mídias na família. Pode ser NULL.|  
|**logical_device_name**|**nvarchar(128)**|Nome do dispositivo de backup no **sys.backup_devices.name**. Se esse for um dispositivo de backup temporário (em vez de um dispositivo de backup permanente que existe no **backup_devices**), o valor de **logical_device_name** é NULL.|  
|**physical_device_name**|**nvarchar(260)**|Nome físico do dispositivo de backup. Pode ser NULL. Este campo é compartilhado entre o processo de backup e restauração. Ele pode conter o caminho de destino de backup original ou o caminho de origem de restauração original. Dependendo se backup ou restauração ocorreu pela primeira vez em um servidor de banco de dados. Observe que as restaurações consecutivas no mesmo arquivo de backup não atualizará o caminho, independentemente de sua localização no momento da restauração. Por isso, **physical_device_name** campo não pode ser usado para ver o caminho de restauração usado.|  
|**device_type**|**tinyint**|Tipo de dispositivo de backup:<br /><br /> 2 = Disco<br /><br /> 5 = Fita<br /><br /> 7 = Dispositivo virtual<br /><br /> 9 = armazenamento do azure<br /><br /> 105 = Um dispositivo de backup.<br /><br /> Pode ser NULL.<br /><br /> Todos os nomes de dispositivos permanentes e números de dispositivo podem ser encontrados em **backup_devices**.|  
|**physical_block_size**|**Int**|Tamanho do bloco físico usado para gravar a família de mídias. Pode ser NULL.|  
|**mirror**|**tinyint**|Número de espelhos (0-3).|  
  
## <a name="remarks"></a>Remarks  
 RESTORE VERIFYONLY FROM *backup_device* WITH LOADHISTORY preenche as colunas da **backupmediaset** tabela com os valores apropriados do cabeçalho de conjunto de mídias.  
  
 Para reduzir o número de linhas nessa tabela e em outras tabelas de histórico e de backup, execute o [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) procedimento armazenado.  
  
## <a name="see-also"></a>Consulte também  
 [Backup e restauração tabelas &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [conjunto de backup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Tabelas do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
