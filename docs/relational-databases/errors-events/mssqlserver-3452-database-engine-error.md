---
title: MSSQLSERVER_3452 | Microsoft Docs
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
helpviewer_keywords:
- 3452 (Database Engine error)
ms.assetid: bf838f02-7186-4b33-b01e-361b0c02de1f
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: af56e2f7eca2ef1988f8d75b217968b347bc33b7
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver3452"></a>MSSQLSERVER_3452
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalhes  
  
|||  
|-|-|  
|Nome do produto|SQL Server|  
|ID do evento|3452|  
|Origem do evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbólico|REC_CHECKIDENTITY|  
|Texto da mensagem|A recuperação do banco de dados '%.*ls' (%d) detectou uma possível inconsistência do valor da identidade na ID da tabela %d. Execute DBCC CHECKIDENT ('%.\*ls').|  
  
## <a name="explanation"></a>Explicação  
Durante a atualização para o [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], o processo para recuperar os valores de identidade no banco de dados encontrou uma inconsistência nos metadados.  
  
## <a name="user-action"></a>Ação do usuário  
Execute DBCC CHECKIDENT.  
  
