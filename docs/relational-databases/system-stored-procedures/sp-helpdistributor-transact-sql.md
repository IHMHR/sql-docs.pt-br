---
title: sp_helpdistributor (Transact-SQL) | Microsoft Docs
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
- sp_helpdistributor_TSQL
- sp_helpdistributor
helpviewer_keywords:
- sp_helpdistributor
ms.assetid: 37b0983e-3b69-4f0f-977e-20efce0a0b97
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: e634d01d6bf241d6d626fb6c28038aa6175b2468
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sphelpdistributor-transact-sql"></a>sp_helpdistributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Lista informações sobre o distribuidor, o banco de dados de distribuição, o diretório de trabalho, e [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conta de usuário do agente. Esse procedimento armazenado é executado no Publicador, no banco de dados de publicação ou em qualquer banco de dados.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_helpdistributor [ [ @distributor= ] 'distributor' OUTPUT ]  
    [ , [ @distribdb= ] 'distribdb' OUTPUT ]  
    [ , [ @directory= ] 'directory' OUTPUT ]  
    [ , [ @account= ] 'account' OUTPUT ]  
    [ , [ @min_distretention= ] min_distretention OUTPUT ]  
    [ , [ @max_distretention= ] max_distretention OUTPUT ]  
    [ , [ @history_retention= ] history_retention OUTPUT ]  
    [ , [ @history_cleanupagent= ] 'history_cleanupagent' OUTPUT ]  
    [ , [ @distrib_cleanupagent = ] 'distrib_cleanupagent' OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @local = ] 'local' ]  
    [ , [ @rpcsrvname= ] 'rpcsrvname' OUTPUT ]  
    [ , [ @publisher_type = ] 'publisher_type' OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@distributor=**] **'***distribuidor***'** saída  
 É o nome do distribuidor. O distribuidor é **sysname**, com um padrão de **%**, que é o único valor que retorna um conjunto de resultados.  
  
 [  **@distribdb=**] **'***distribdb***'** saída  
 É o nome do banco de dados de distribuição. *distribdb* é **sysname**, com um padrão de **%**, que é o único valor que retorna um conjunto de resultados.  
  
 [  **@directory=**] **'***diretório***'** saída  
 É o diretório de trabalho. *diretório* é **nvarchar (255)**, com um padrão de **%**, que é o único valor que retorna um conjunto de resultados.  
  
 [  **@account=**] **'***conta***' saída**  
 É a conta de usuário do [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. *conta*é **nvarchar (255)**, com um padrão de **%**, que é o único valor que retorna um conjunto de resultados.  
  
 [  **@min_distretention=**] *min_distretention * saída**  
 É o período mínimo de retenção da distribuição, em horas. *min_distretention* é **int**, com um padrão de **-1**.  
  
 [  **@max_distretention=**] *max_distretention * saída**  
 É o período máximo de retenção da distribuição, em horas. *max_distretention* é **int**, com um padrão de **-1**.  
  
 [  **@history_retention=**] *history_retention * saída**  
 É o período de retenção do histórico, em horas. *history_retention* é **int**, com um padrão de **-1**.  
  
 [  **@history_cleanupagent=**] **'***history_cleanupagent***' saída**  
 É o nome do agente de limpeza do histórico. *history_cleanupagent* é **nvarchar (100)**, com um padrão de **%**, que é o único valor que retorna um conjunto de resultados.  
  
 [  **@distrib_cleanupagent =**] **'***distrib_cleanupagent***' saída**  
 É o nome do trabalho do agente de limpeza da distribuição. *distrib_cleanupagent* é **nvarchar (100)**, com um padrão de **%**, que é o único valor que retorna um conjunto de resultados.  
  
 [  **@publisher=**] **'***publicador***'**  
 É o nome do Publicador. *publicador* é **sysname**, com um padrão NULL.  
  
 [  **@local=**] **'***local***'**  
 Especifica se o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve obter valores de servidor local. *local* é **nvarchar (5)**, com um padrão NULL.  
  
 [  **@rpcsrvname=**] **'***rpcsrvname***' saída**  
 É o nome do servidor que envia chamadas de procedimento remoto. *rpcsrvname* é **sysname**, com um padrão de **%**, que é o único valor que retorna um conjunto de resultados.  
  
 [ **@publisher_type**=] **'***publisher_type***' saída**  
 É o tipo do Publicador. *publisher_type* é **sysname**, com um padrão de **%**, que é o único valor que retorna um conjunto de resultados.  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**Distribuidor**|**sysname**|Nome do Distribuidor.|  
|**Banco de dados de distribuição**|**sysname**|Nome do banco de dados de distribuição.|  
|**Diretório**|**nvarchar(255)**|Nome do diretório de trabalho.|  
|**Conta**|**nvarchar(255)**|Nome da conta de usuário do Windows|  
|**retenção de distrib min**|**Int**|Período mínimo de retenção de distribuição.|  
|**retenção de distrib max**|**Int**|Período máximo de retenção de distribuição.|  
|**retenção de histórico**|**Int**|Período de retenção do histórico|  
|**Agente de limpeza de histórico**|**nvarchar(100)**|Nome do agente de limpeza do histórico.|  
|**Agente de limpeza de distribuição**|**nvarchar(100)**|Nome do agente de limpeza da Distribuição.|  
|**nome do servidor RPC**|**sysname**|Nome do Distribuidor local ou remoto.|  
|**nome de logon de RPC**|**sysname**|Logon usado para chamadas de procedimento remoto ao Distribuidor remoto.|  
|**tipo de publicador**|**sysname**|Tipo de Publicador, que pode ser um dos seguintes:<br /><br /> **MSSQLSERVER**<br /><br /> **ORACLE**<br /><br /> **ORACLE GATEWAY**|  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="remarks"></a>Remarks  
 **sp_helpdistributor** é usado em todos os tipos de replicação.  
  
 Se um ou mais parâmetros de saída são especificados durante a execução **sp_helpdistributor**, todos os parâmetros de saída definidos como NULL terão valores atribuídos na saída e nenhum conjunto de resultados será retornado. Se nenhum parâmetro de saída for especificado, um conjunto de resultados será retornado.  
  
## <a name="permissions"></a>Permissões  
 O seguinte conjunto de resultados colunas ou parâmetros de saída são retornados aos membros do **sysadmin** a função de servidor fixa no publicador e o **db_owner** função de banco de dados fixa no banco de dados de publicação:  
  
|Coluna de conjunto de resultados|Parâmetro de saída|  
|-----------------------|----------------------|  
|account|**@account**|  
|min distrib retention|**@min_distretention**|  
|max distrib retention|**@max_distretention**|  
|history retention|**@history_retention**|  
|history cleanup agent|**@history_cleanupagent**|  
|distribution cleanup agent|**@distrib_cleanupagent**|  
|rpc login name|none|  
  
 A coluna de conjunto de resultados seguinte é retornada aos usuários na lista de acesso à publicação no Distribuidor:  
  
-   directory  
  
 As colunas de conjunto de resultados a seguir são retornadas a todos os usuários.  
  
|Coluna de conjunto de resultados|Parâmetro de saída|  
|-----------------------|----------------------|  
|distributor|**@distributor**|  
|distribution database|**@distribdb**|  
|rpc server name|**@rpcsrvname**|  
|publisher type|**@publisher_type**|  
  
## <a name="see-also"></a>Consulte também  
 [Exibir e modificar propriedades de Publicador e Distribuidor](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  
