---
title: Propriedades de memória compartilhada | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 730c784c1c7f92bf0c8fc81f66484b57354f7c31
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MTE
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="shared-memory-properties"></a>Propriedades da memória compartilhada
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Use a página **Protocolo** na caixa de diálogo **Propriedades de Memória Compartilhada** para habilitar ou desabilitar o protocolo de memória compartilhada. A memória compartilhada é o protocolo mais simples de usar e não precisa de configurações. Como os clientes que usam o protocolo de memória compartilhada só podem se conectar a uma instância do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executada no mesmo computador, ele não é útil para a maior parte da atividade de banco de dados. Use o protocolo de memória compartilhada para solucionar problemas quando você suspeitar que outros protocolos estejam configurados incorretamente.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve ser reiniciado para habilitar ou desabilitar o protocolo.  
  
## <a name="options"></a>Opções  
 **Enabled**  
 Os valores possíveis são **Sim** e **Não**. O protocolo de memória compartilhada é desabilitado por padrão.  
  
## <a name="see-also"></a>Consulte Também  
 [Escolhendo um protocolo de rede](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [Criando uma cadeia de conexão válida usando o protocolo de memória compartilhada](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  
