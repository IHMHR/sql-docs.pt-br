---
title: MSSQLSERVER_21889 | Microsoft Docs
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
- 21889 (Database Engine error)
ms.assetid: ae199540-7986-4cc2-b782-cd22793236d3
caps.latest.revision: 6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 459cefda7e1744188ba84ab4d0d43318f8d53bda
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver21889"></a>MSSQLSERVER_21889
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalhes  
  
|||  
|-|-|  
|Nome do produto|SQL Server|  
|ID do evento|21889|  
|Origem do evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbólico|SQLErrorNum21889|  
|Texto da mensagem|A instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] '% s' não é um publicador de replicação. Execute **sp_adddistributor** na instância '%s' do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] com o distribuidor '%s' para permitir que a instância hospede o banco de dados de publicação '%s'. Certifique-se de especificar as mesmas informações de logon e senha que foram usadas para o publicador original.|  
  
## <a name="explanation"></a>Explicação  
Para hospedar o banco de dados publicador, a instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve ser um publicador de replicação. **sp_validate_redirected_publisher** chama **sp_helpdistributor** no servidor remoto para determinar se o servidor é um publicador de replicação. Esse erro é retornado quando a execução do procedimento armazenado **sp_helpdistributor** indica que a instância de destino do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] não é um publicador de replicação.  
  
## <a name="user-action"></a>Ação do usuário  
Execute **sp_adddistributor** na instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que hospeda o banco de dados publicador. Ao executar **sp_adddistributor**, especifique o distribuidor correto. Use o mesmo valor para o parâmetro *@password* que foi usado quando **sp_adddistributor** foi executado inicialmente no distribuidor.  
  
