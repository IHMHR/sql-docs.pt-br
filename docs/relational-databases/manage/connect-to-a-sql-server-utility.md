---
title: Conectar a um Utilitário do SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: maintenance-plans
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b9b90b8d-241f-4b74-ac14-de7b10ea1821
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fe13b8a6a490df258977d263e5fb9ddbe2f19a08
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="connect-to-a-sql-server-utility"></a>Conectar a um Utilitário do SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Para que você possa se conectar a um Utilitário do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , é necessário criar um UCP (ponto de controle do utilitário). Para obter mais informações, consulte [Recursos e tarefas do utilitário do SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  
  
 Para exibir e gerenciar a integridade de recurso do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) para conectar-se a um Utilitário do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Para conectar-se a um Utilitário do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] por meio do SSMS:  
  
1.  Inicie o SSMS.  
  
2.  No SSMS, conecte-se a uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Clique em **Exibir** e em **Gerenciador do Utilitário**.  
  
4.  No painel de navegação do Gerenciador do Utilitário, clique em ![](../../relational-databases/manage/media/connect-to-utility.gif "Connect_to_Utility")**Conectar ao Utilitário**.  
  
5.  Na caixa de diálogo **Conectar ao Servidor** , especifique o nome da instância UCP e depois clique em **Conectar**.  
  
6.  Exiba o painel de navegação do Gerenciador do Utilitário para ver um modo de exibição de árvore dos recursos do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no UCP.  
  
 Criar um novo UCP também conecta ao Utilitário do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obter mais informações, veja [Criar um ponto de controle do Utilitário do SQL Server &#40;Utilitário do SQL Server&#41;](../../relational-databases/manage/create-a-sql-server-utility-control-point-sql-server-utility.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Recursos e tarefas do Utilitário do SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Exibir resultados da política de integridade de recursos &#40;Utilitário do SQL Server&#41;](../../relational-databases/manage/view-resource-health-policy-results-sql-server-utility.md)  
  
  
