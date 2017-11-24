---
title: sp_help_fulltext_tables_cursor (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_tables_cursor
- sp_help_fulltext_tables_cursor_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help_fulltext_tables_cursor
ms.assetid: 155791eb-8832-4596-8487-7fc70dfba5b9
caps.latest.revision: "25"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef0fa0c119c293e085d68124ee44dee378fb99d1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="sphelpfulltexttablescursor-transact-sql"></a>sp_help_fulltext_tables_cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Usa um cursor ao retornar uma lista de tabelas que são registradas para indexação de texto completo.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Use a nova **fulltext_indexes** exibição do catálogo. Para obter mais informações, consulte [fulltext_indexes &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md).  
  
||  
|-|  
|**Aplica-se a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] até a [versão atual](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].|  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_help_fulltext_tables_cursor [ @cursor_return = ] @cursor_variable OUTPUT   
     [ , [ @fulltext_catalog_name = ] 'fulltext_catalog_name' ]   
     [ , [ @table_name = ] 'table_name' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@cursor_return=** ]  *@cursor_variable*  SAÍDA  
 É a variável de saída do tipo **cursor**. O cursor é somente leitura, rolável e dinâmico.  
  
 [  **@fulltext_catalog_name=** ] **'***fulltext_catalog_name***'**  
 É o nome do catálogo de texto completo. *fulltext_catalog_name* é **sysname**, com um padrão NULL. Se *fulltext_catalog_name* for omitido ou for NULL, todas as tabelas indexadas de texto completo associadas com o banco de dados são retornadas. Se *fulltext_catalog_name* for especificado, mas *table_name* for omitido ou for NULL, as informações de índice de texto completo são recuperadas para cada tabela indexada de texto completo associada a este catálogo. Se ambos os *fulltext_catalog_name* e *table_name* for especificado, uma linha é retornada se *table_name* associado *fulltext_catalog_name*; Caso contrário, ocorrerá um erro.  
  
 [  **@table_name=**] **'***table_name***'**  
 É o nome de uma ou duas partes da tabela para a qual são solicitados metadados de texto completo. *table_name* é **nvarchar (517)**, com um valor padrão de NULL. Se apenas *table_name* for especificado, apenas as linhas relevantes para *table_name* é retornado.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 0 (êxito) ou (1) falha  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_OWNER**|**sysname**|Proprietário da tabela. Esse é o nome do usuário de banco de dados que criou a tabela.|  
|**TABLE_NAME**|**sysname**|Nome da tabela.|  
|**FULLTEXT_KEY_INDEX_NAME**|**sysname**|Índice que impõe a restrição UNIQUE na coluna designada como a coluna de chave exclusiva.|  
|**FULLTEXT_KEY_COLID**|**int**|ID de coluna do índice exclusivo identificado por FULLTEXT_KEY_NAME.|  
|**FULLTEXT_INDEX_ACTIVE**|**int**|Especifica se as colunas marcadas para indexação de texto completo nessa tabela são elegíveis para consultas:<br /><br /> 0 = Inativo<br /><br /> 1 = Ativo|  
|**FULLTEXT_CATALOG_NAME**|**sysname**|Catálogo de texto completo no qual os dados de índice de texto completo residem.|  
  
## <a name="permissions"></a>Permissões  
 As permissões de execução usam como padrão membros da função **pública** .  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir retorna os nomes das tabelas indexadas de texto completo associadas ao catálogo de texto completo `Cat_Desc`.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @mycursor CURSOR;  
EXEC sp_help_fulltext_tables_cursor @mycursor OUTPUT, 'Cat_Desc';  
FETCH NEXT FROM @mycursor;  
WHILE (@@FETCH_STATUS <> -1)  
   BEGIN  
      FETCH NEXT FROM @mycursor;  
   END;  
CLOSE @mycursor;  
DEALLOCATE @mycursor;  
GO   
```  
  
## <a name="see-also"></a>Consulte também  
 [INDEXPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/indexproperty-transact-sql.md)   
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [sp_fulltext_table &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-fulltext-table-transact-sql.md)   
 [sp_help_fulltext_tables &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-transact-sql.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  