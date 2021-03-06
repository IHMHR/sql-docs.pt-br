---
title: sp_publisherproperty (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_publisherproperty
- sp_publisherproperty_TSQL
helpviewer_keywords:
- sp_publisherproperty
ms.assetid: 0ed1ebc1-a1bd-4aed-9f46-615c5cf07827
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 647bd0de356a8a31c531a027dffeca88cd8c3083
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sppublisherproperty-transact-sql"></a>sp_publisherproperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Exibe ou altera as propriedades do publicador para não -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] editores. Esse procedimento armazenado é executado no Distribuidor.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_publisherproperty [ @publisher = ] 'publisher'   
   [ , [ @propertyname = ] 'propertyname' ]   
   [ , [ @propertyvalue = ] 'propertyvalue' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [**@publisher** =] **'***publicador***'**  
 É o nome do Publicador heterogêneo. *publicador* é **sysname**, sem padrão.  
  
 [**@propertyname** =] **'***propertyname***'**  
 É o nome da propriedade que está sendo definida. *PropertyName* é **sysname**, e pode ser um dos valores a seguir.  
  
|Value|Description|  
|-----------|-----------------|  
|**xactsetbatching**|Se forem agrupadas transações no Publicador em conjuntos transacionalmente consistentes para processamento subsequente, conhecidos como Xactsets. Um valor de **habilitado** significa que Xactsets podem ser criados, que é o padrão. Um valor de **desabilitado** significa que Xactsets existentes são processados por nenhum novos Xactsets é criadas.|  
|**xactsetjob**|Se o trabalho Xactset estiver habilitado para a criação de Xactsets. Um valor de **habilitado** significa que o trabalho de Xactset é executado periodicamente para criar Xactsets no publicador. Um valor de **desabilitado** significa que os Xactsets só são criados pelo Log Reader Agent quando ele controla alterações no publicador.|  
|**xactsetjobinterval**|Intervalo entre execuções do trabalho de Xactset, em minutos.|  
  
 Quando *propertyname* for omitido todas as propriedades configuráveis são retornadas.  
  
 [**@propertyvalue** =] **'***propertyvalue***'**  
 É o novo valor da configuração da propriedade. *PropertyValue* é **sysname**, com um valor padrão de NULL. Quando *propertyvalue* for omitido, a configuração atual da propriedade é retornada.  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**propertyname**|**sysname**|Retorna as propriedades de publicação seguintes que podem ser definidas:<br /><br /> **xactsetbatching**<br /><br /> **xactsetjob**<br /><br /> **xactsetjobinterval**|  
|**PropertyValue**|**sysname**|É a configuração atual da propriedade no **propertyname** coluna.|  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="remarks"></a>Remarks  
 **sp_publisherproperty** é usado em replicação transacional não[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] editores.  
  
 Quando apenas *publicador* for especificado, o conjunto de resultados inclui as configurações atuais para todas as propriedades que podem ser definidas.  
  
 Quando *propertyname* for especificado, somente a propriedade nomeada aparece no conjunto de resultados.  
  
 Quando todos os parâmetros são especificados, a propriedade é alterada e um conjunto de resultados não é retornado.  
  
 Ao alterar o **xactsetjobinterval** propriedade para um trabalho em execução, você deve reiniciar o trabalho para o novo intervalo entre em vigor.  
  
## <a name="permissions"></a>Permissões  
 Somente membros do **sysadmin** pode executar a função de servidor fixa no distribuidor **sp_publisherproperty**.  
  
## <a name="see-also"></a>Consulte também  
 [Configurar o trabalho do conjunto de transações para um Publicador Oracle &#40;programação Transact-SQL de replicação&#41;](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
