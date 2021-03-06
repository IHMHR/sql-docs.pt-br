---
title: sp_dropanonymousagent (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
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
- sp_dropanonymousagent
- sp_dropanonymousagent_TSQL
helpviewer_keywords:
- sp_dropanonymousagent
ms.assetid: 4cb96efa-9358-44a3-a8ee-a7e181bed089
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 10b75c7c2e083a09dbebfc720487511397a1af90
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="spdropanonymousagent-transact-sql"></a>sp_dropanonymousagent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Descarta um agente anônimo para monitoramento de replicação no distribuidor do Publicador. Esse procedimento armazenado é executado no Publicador, em qualquer banco de dados.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_dropanonymousagent [ @subid= ] sub_id    , [ @type= ] type  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@subid=**] *sub_id*  
 É o identificador global de uma assinatura anônima. *sub_id* é **uniqueidentifier**, sem padrão. Esse identificador pode ser recuperado no assinante usando **sp_helppullsubscription**. O valor de **subid** campo do conjunto de resultados retornado é esse identificador global.  
  
 [  **@type=**] *tipo*  
 É o tipo de assinatura. *tipo* é **int**, sem padrão. Os valores válidos são **1** ou **2**. Especifique **1**, se a replicação de instantâneo ou replicação transacional usando o agente de distribuição. Especifique **2**, se usar o agente de mesclagem de replicação de mesclagem.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="remarks"></a>Remarks  
 **sp_dropanonymousagent** é usado em todos os tipos de replicação.  
  
 Esse procedimento armazenado é usado para descartar agentes de assinatura anônimos e não pode ser usado para descartar assinaturas conhecidas.  
  
## <a name="permissions"></a>Permissões  
 Somente membros do **db_owner** função de banco de dados fixa no banco de dados de distribuição pode executar **sp_dropanonymousagent**.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos armazenados de replicação &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
