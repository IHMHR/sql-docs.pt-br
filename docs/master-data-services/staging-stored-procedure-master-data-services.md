---
title: Preparando procedimento armazenado (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 04/01/2016
ms.prod: sql
ms.prod_service: mds
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
caps.latest.revision: 15
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: a201d7ac283aed1fe96b8cf978e8f520827bb0de
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="staging-stored-procedure-master-data-services"></a>Preparando procedimento armazenado (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Ao iniciar o processo de preparo no [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], você usa um entre três procedimentos armazenados.  
  
-   stg.udp_\<name>_Leaf  
  
-   stg.udp_\<name>_Consolidated  
  
-   stg.udp_\<name>_Relationship  
  
 Onde nome é o nome da tabela de preparo que foi especificada quando a entidade foi criada.  
  
## <a name="staging-process-stored-procedure-parameters"></a>Parâmetros do procedimento armazenado do processo de preparo  
 A tabela a seguir lista os parâmetros desses procedimentos armazenados.  
  
|Parâmetro|Description|  
|---------------|-----------------|  
|**VersionName**<br /><br /> Obrigatório|O nome da versão. Pode ou não diferenciar maiúsculas de minúsculas, dependendo de sua configuração de agrupamento do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|  
|**LogFlag**<br /><br /> Obrigatório|Determina se as transações são registradas em log durante o processo de preparo. Os valores possíveis são:<br /><br /> **0**: não registrar transações em log.<br /><br /> **1**: registrar transações em log.<br /><br /> <br /><br /> Para obter mais informações sobre transações, consulte [Transações &#40;Master Data Services&#41;](../master-data-services/transactions-master-data-services.md).|  
|**BatchTag**<br /><br /> Necessário, exceto pelo serviço Web|O valor **BatchTag** conforme especificado na tabela de preparo.|  
|**Batch_ID**<br /><br /> Necessário apenas pelo serviço Web|O valor **Batch_ID** , conforme especificado na tabela de preparo.|  
|**Nome do Usuário**|Parâmetro opcional|  
|**ID de usuário**|Parâmetro opcional|  
  
### <a name="staging-process-stored-procedure-example"></a>Exemplo de procedimento armazenado do processo de preparo  
 O exemplo a seguir mostra como iniciar o processo de preparo por meio do procedimento armazenado de preparo.  
  
```  
USE [DATABASE_NAME]  
GO  
  
EXEC[stg].[udp_name_Leaf]  
      @VersionName = N'VERSION_1',  
@LogFlag = 1,  
@BatchTag = N'batch1'  
      @UserName=N’domain\user’  
  
GO  
  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Procedimento armazenado de validação &#40;Master Data Services&#41;](../master-data-services/validation-stored-procedure-master-data-services.md)   
 [Exibir erros que ocorrem durante o preparo &#40;Master Data Services&#41;](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md)  
  
  
