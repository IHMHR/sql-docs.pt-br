---
title: sp_dropmergepartition (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
- sp_dropmergepartition_TSQL
- sp_dropmergepartition
helpviewer_keywords:
- sp_dropmergepartition
ms.assetid: 1be511c1-79ff-4947-9379-78d83b7b8945
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 890a265b51b5048f135401ac6e80fc7066bc5c24
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="spdropmergepartition-transact-sql"></a>sp_dropmergepartition (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Remove uma partição para um filtro de linha com parâmetros de uma publicação. Esse procedimento armazenado é executado no Publicador, no banco de dados publicador. Esse procedimento armazenado também remove o trabalho de instantâneo correspondente e arquivos de instantâneo para a partição.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_dropmergepartition [ @publication = ] 'publication'  
        , [ @suser_sname = ] 'suser_sname'  
        , [ @host_name = ] 'host_name'  
```  
  
## <a name="arguments"></a>Argumentos  
 [ **@publication**] = **'***publicação***'**  
 É o nome da publicação. *publicação* é **sysname**, sem padrão.  
  
 [ **@suser_sname**=] **'***suser_sname***'**  
 É o valor da [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) função no assinante usado para definir a partição. *suser_sname* é **sysname**, sem padrão.  
  
 [ **@host_name** =] **'***host_name***'**  
 É o valor da [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) função no assinante usado para definir a partição. *HOST_NAME* é **sysname**, sem padrão.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="remarks"></a>Remarks  
 **sp_dropmergepartition** é usado em replicação de mesclagem.  
  
## <a name="permissions"></a>Permissões  
 Somente membros do **sysadmin** função de servidor fixa ou **db_owner** pode executar a função de banco de dados fixa **sp_dropmergepartition**.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciar partições para uma publicação de mesclagem com filtros parametrizados](../../relational-databases/replication/publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)  
  
  
