---
title: dbo.sysdownloadlist (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dbo.sysdownloadlist
- sysdownloadlist_TSQL
- dbo.sysdownloadlist_TSQL
- sysdownloadlist
dev_langs:
- TSQL
helpviewer_keywords:
- sysdownloadlist system table
ms.assetid: 71087a4c-e829-488e-aa7d-a9476e2b4779
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4390fe628a879b36b42ffd1a3c3209e910eb125c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="dbosysdownloadlist-transact-sql"></a>dbo.sysdownloadlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Mantém a fila de instruções de download para todos os servidores de destino.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**Int**|Coluna de identidade que fornece a sequência de inserção natural de linhas.|  
|**source_server**|**sysname**|Nome do servidor de origem.|  
|**operation_code**|**tinyint**|Código de operação para o trabalho:<br /><br /> **1** = INS (INSERIR)<br /><br /> **2** = UPD (ATUALIZAÇÃO)<br /><br /> **3** = DEL (DELETE)<br /><br /> **4** = START<br /><br /> **5** = PARAR|  
|**object_type**|**tinyint**|Código de tipo de objeto.|  
|**object_id** <sup>1</sup>|**uniqueidentifier**|Número de identificação do objeto.|  
|**target_server**|**sysname**|Nome do servidor de destino.|  
|**error_message**|**nvarchar(1024)**|Mensagem de erro se o servidor de destino encontrar um erro ao processar a linha em particular.|  
|**date_posted**|**datetime**|Data e hora em que o trabalho foi postado no servidor de destino.|  
|**date_downloaded**|**datetime**|Data e hora em que o trabalho foi baixado pela última vez.|  
|**status**|**tinyint**|Status do trabalho:<br /><br /> **0** = ainda não baixado<br /><br /> **1** = baixado com êxito|  
|**deleted_object_name**|**sysname**|Nome do objeto excluído.|  
  
 <sup>1</sup> o **object_id** coluna pode ser um valor de **-1**, que corresponde a um valor ALL se a **operation_code** coluna é um valor de exclusão.  
  
  
