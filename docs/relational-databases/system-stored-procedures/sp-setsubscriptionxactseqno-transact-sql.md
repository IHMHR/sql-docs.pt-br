---
title: sp_setsubscriptionxactseqno (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
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
- sp_setsubscriptionxactseqno
- sp_setsubscriptionxactseqno_TSQL
helpviewer_keywords:
- sp_setsubscriptionxactseqno
ms.assetid: cdb4e0ba-5370-4905-b03f-0b0c6f080ca6
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f59325c709b8d16d5e120a135d5d9f9697692b1e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="spsetsubscriptionxactseqno-transact-sql"></a>sp_setsubscriptionxactseqno (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Usado durante a solução de problemas para especificar o LSN (número de sequência de log) da próxima transação a ser aplicada pelo Agente de Distribuição no Assinante, o que permite que o agente ignore uma transação com falha. Esse procedimento armazenado é executado no assinante no banco de dados de assinatura. Sem suporte para Assinantes não SQLServer.  
  
> [!CAUTION]  
>  O uso incorreto desse procedimento armazenado ou a especificação incorreta de um valor LSN pode fazer com que o Agente de Distribuição reverta as alterações que já tinham sido aplicadas no Assinante ou ignore todas as alterações restantes.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_setsubscriptionxactseqno [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @xact_seqno = ] xact_seqno   
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@publisher=** ] **'***publicador***'**  
 É o nome do Publicador. *publicador* é **sysname**, sem padrão.  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 É o nome do banco de dados de publicação. *publisher_db* é **sysname**, sem padrão. Para um publicador não SQL Server, *publisher_db* é o nome do banco de dados de distribuição.  
  
 [  **@publication=** ] **'***publicação***'**  
 É o nome da publicação. *publicação* é **sysname**, sem padrão. Quando o agente de distribuição é compartilhado por mais de uma publicação, você deve especificar um valor de ALL para *publicação*.  
  
 [  **@xact_seqno=** ] *xact_seqno*  
 É o LSN da próxima transação no Distribuidor a ser aplicada no Assinante. *xact_seqno* é **varbinary (16)**, sem padrão.  
  
## <a name="result-set"></a>Conjunto de resultados  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**XACT_SEQNO ORIGINAL**|**varbinary(16)**|É o LSN original da próxima transação a ser aplicada no Assinante.|  
|**XACT_SEQNO ATUALIZADO**|**varbinary(16)**|É o LSN atualizado da próxima transação a ser aplicada no Assinante.|  
|**CONTAGEM DE FLUXO DE ASSINATURA**|**Int**|O número de fluxos de assinatura usado durante a última sincronização.|  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="remarks"></a>Remarks  
 **sp_setsubscriptionxactseqno** é usado em replicação transacional.  
  
 **sp_setsubscriptionxactseqno** não pode ser usado em uma topologia de replicação transacional ponto a ponto.  
  
 **sp_setsubscriptionxactseqno** pode ser usado para ignorar uma transação específica que está causando um erro quando aplicada ao assinante. Quando há uma falha e depois que o agente de distribuição é interrompida, chame [sp_helpsubscriptionerrors &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helpsubscriptionerrors-transact-sql.md) no distribuidor para recuperar o valor xact_seqno da transação com falha e, em seguida, chamar **sp_setsubscriptionxactseqno**, passando esse valor para *xact_seqno*. Isso assegurará que somente os comandos após esse LSN sejam processados.  
  
 Especifique um valor de **0** para *xact_seqno* para entregar todos os comandos pendentes no banco de dados de distribuição para o assinante.  
  
 **sp_setsubscriptionxactseqno** pode falhar se o agente de distribuição usar fluxos de várias assinaturas.  
  
 Quando esse erro ocorre, você deve executar o Agente de Distribuição com um fluxo de uma única assinatura. Para obter mais informações, consulte [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
## <a name="permissions"></a>Permissões  
 Somente membros do **sysadmin** função de servidor fixa ou **db_owner** pode executar a função de banco de dados fixa **sp_setsubscriptionxactseqno**.  
  
  
