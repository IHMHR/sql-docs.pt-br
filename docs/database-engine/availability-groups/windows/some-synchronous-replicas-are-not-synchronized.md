---
title: Algumas réplicas síncronas não são sincronizadas | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.agp5synchronized.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: e58ed56e-4c30-42e6-a9fc-a8c401620e02
caps.latest.revision: 11
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0edbc7e52b279dc7b14b550526dd3c1b14b29c27
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="some-synchronous-replicas-are-not-synchronized"></a>Algumas réplicas síncronas não são sincronizadas
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>Introdução  
  
|||  
|-|-|  
|**Nome da Política**|Estado de sincronização de dados de réplicas síncronas|  
|**Problema**|Algumas réplicas síncronas não são sincronizadas.|  
|**Categoria**|**Aviso**|  
|**Faceta**|grupo de disponibilidade|  
  
## <a name="description"></a>Description  
 Essa política acumula o estado de sincronização de dados de todas as réplicas de disponibilidade e verifica se há réplicas de disponibilidade que não estão no estado de sincronização esperado. A política está em um estado não íntegro quando o estado de qualquer réplica assíncrona não é SYNCHRONIZING e o estado de qualquer réplica síncrona não é SYNCHRONIZED. Caso contrário, o estado da política é íntegro.  
  
> [!NOTE]  
>  Para esta versão do [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], as informações sobre as possíveis causas e soluções estão localizadas em [Algumas réplicas síncronas não estão sincronizadas](http://go.microsoft.com/fwlink/p/?LinkId=220853) no Wiki do TechNet.  
  
## <a name="possible-causes"></a>Causas possíveis  
 Neste grupo de disponibilidade, pelo menos uma réplica síncrona não está sincronizada no momento. O estado de sincronização de réplica pode ser SYNCHONIZING ou NOT SYNCHRONIZING.  
  
## <a name="possible-solution"></a>Solução possível  
 Use o estado da política de réplica de disponibilidade para localizar a réplica de disponibilidade com o estado de sincronização incorreto e, depois, resolva o problema na réplica de disponibilidade.  
  
## <a name="see-also"></a>Consulte Também  
 [Visão geral dos grupos de disponibilidade AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Usar o Painel AlwaysOn &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
