---
title: sp_helptrigger (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helptrigger
- sp_helptrigger_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helptrigger
ms.assetid: e486d39b-771d-488d-a786-7136433a2203
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 61c6c78c302266ce3a9e29c432e1a913c263d704
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="sphelptrigger-transact-sql"></a>sp_helptrigger (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retorna o tipo ou os tipos de gatilhos DML definidos na tabela especificada para o banco de dados atual. sp_helptrigger não pode ser usado com gatilhos DDL. Consulta o [procedimentos armazenados do sistema](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md) exibição do catálogo.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_helptrigger [ @tabname = ] 'table'   
     [ , [ @triggertype = ] 'type' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@tabname=** ] **'***tabela***'**  
 É o nome da tabela do banco de dados atual para a qual as informações de gatilho devem ser retornadas. *tabela* é **nvarchar(776)**, sem padrão.  
  
 [  **@triggertype=** ] **'***tipo***'**  
 É o tipo de gatilho DML sobre o qual retornar informações. *tipo* é **char(6)**, com um padrão NULL, e pode ser um destes valores.  
  
|Value|Description|  
|-----------|-----------------|  
|**DELETE**|Retorna informações do gatilho DELETE.|  
|**INSERT**|Retorna informações do gatilho INSERT.|  
|**UPDATE**|Retorna informações do gatilho UPDATE.|  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 0 (êxito) ou 1 (falha)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 A tabela a seguir mostra as informações contidas no conjunto de resultados.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**trigger_name**|**sysname**|Nome do gatilho.|  
|**trigger_owner**|**sysname**|Nome do proprietário da tabela em que o gatilho é definido.|  
|**isupdate**|**Int**|1 = Gatilho UPDATE<br /><br /> 0 = Não é um gatilho UPDATE|  
|**isdelete**|**Int**|1 = Gatilho DELETE<br /><br /> 0 = Não é um gatilho DELETE|  
|**propriedade IsInsert**|**Int**|1 = Gatilho INSERT<br /><br /> 0 = Não é um gatilho INSERT|  
|**isafter**|**Int**|1 = Gatilho AFTER<br /><br /> 0 = Não é um gatilho AFTER|  
|**isinsteadof**|**Int**|1 = Gatilho INSTEAD OF<br /><br /> 0 = Não é um gatilho INSTEAD OF|  
|**trigger_schema**|**sysname**|Nome do esquema ao qual o gatilho pertence.|  
  
## <a name="permissions"></a>Permissões  
 Requer [configuração de visibilidade de metadados](../../relational-databases/security/metadata-visibility-configuration.md) permissão na tabela.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir executa `sp_helptrigger` para produzir informações sobre o(s) gatilho(s) na tabela `Person.Person`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helptrigger 'Person.Person';  
```  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos armazenados do mecanismo de banco de dados &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
