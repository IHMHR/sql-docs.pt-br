---
title: sys.dm_exec_describe_first_result_set_for_object (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_describe_first_result_set_for_object_TSQL
- sys.dm_exec_describe_first_result_set_for_object
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_describe_first_result_set_for_object catalog view
ms.assetid: 63b0fde7-95d7-4ad7-a219-a9feacf1bd89
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6d2be99ba8101c76ed8d8225c7fe3efdedd35198
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmexecdescribefirstresultsetforobject-transact-sql"></a>sys.dm_exec_describe_first_result_set_for_object (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Essa função de gerenciamento dinâmico usa uma @object_id como um parâmetro e descreve os metadados do primeiro resultado para o módulo com esse ID. O @object_id especificado pode ser a identificação de um [!INCLUDE[tsql](../../includes/tsql-md.md)] procedimento armazenado ou uma [!INCLUDE[tsql](../../includes/tsql-md.md)] gatilho. Se for a ID de qualquer objeto (como exibição, tabela, função ou procedimento CLR), um erro será especificado nas colunas de erro do resultado.  
  
 **sys.DM exec_describe_first_result_set_for_object** tem o mesmo resultado definição do conjunto de [sys.DM exec_describe_first_result_set &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md) e é semelhante a [SP _ describe_first_result_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md).  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sys.dm_exec_describe_first_result_set_for_object   
    ( @object_id , @include_browse_information )  
```  
  
## <a name="arguments"></a>Argumentos  
 *@object_id*  
 O @object_id de um [!INCLUDE[tsql](../../includes/tsql-md.md)] procedimento armazenado ou uma [!INCLUDE[tsql](../../includes/tsql-md.md)] gatilho. @object_id é o tipo **int**.  
  
 *@include_browse_information*  
 @include_browse_information é o tipo **bit**. Se definido como 1, cada consulta será analisada como se tivesse uma opção FOR BROWSE na consulta. Retorna colunas-chave adicionais e informações de tabela de origem.  
  
## <a name="table-returned"></a>Tabela retornada  
 Estes metadados comuns são retornados como um conjunto de resultados com uma linha para cada coluna nos metadados de resultados. Cada linha descreve o tipo e a nulidade da coluna no formato descrito na seção a seguir. Se a primeira instrução não existir para todo caminho de controle, um conjunto de resultados com zero linhas será retornado.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**is_hidden**|**bit**|Especifica se a coluna é uma coluna extra adicionada para fins de informações de navegação e que ela não é exibida realmente no conjunto de resultados.|  
|**column_ordinal**|**Int**|Contém a posição ordinal da coluna no conjunto de resultados. Posição da primeira coluna será especificada como 1.|  
|**name**|**sysname**|Conterá o nome da coluna se um nome puder ser determinado. Caso contrário, é NULL.|  
|**is_nullable**|**bit**|Contém o valor 1 se a coluna permitir NULLs, 0 se a coluna não permitir NULLs e 1 se não for possível determinar se a coluna permite valores nulos.|  
|**system_type_id**|**Int**|Contém o system_type_id do tipo de dados da coluna como especificado em sys. Types. Para tipos de CLR, embora a coluna system_type_name retorne NULL, essa coluna retornará o valor 240.|  
|**system_type_name**|**nvarchar(256)**|Contém o nome do tipo de dados. Inclui argumentos (como comprimento, precisão, escala) especificados para o tipo de dados da coluna. Se o tipo de dados for um tipo de alias definido pelo usuário, o tipo de sistema subjacente será especificado aqui. Se for um tipo de CLR definido pelo usuário, NULL será retornado nessa coluna.|  
|**max_length**|**smallint**|Comprimento máximo (em bytes) da coluna.<br /><br /> -1 = a coluna de tipo de dados é **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, ou **xml**.<br /><br /> Para **texto** colunas, o **max_length** valor será 16 ou o valor definido por **sp_tableoption 'text in row'**.|  
|**precisão**|**tinyint**|Precisão da coluna, se tiver base numérica. Caso contrário, retorna 0.|  
|**scale**|**tinyint**|Escala da coluna, se tiver base numérica. Caso contrário, retorna 0.|  
|**collation_name**|**sysname**|Nome do agrupamento da coluna, se baseada em caracteres. Caso contrário, retornará NULL.|  
|**user_type_id**|**Int**|Para tipos de CLR e alias, contém o user_type_id do tipo de dados da coluna como especificado em sys.types. Caso contrário, é NULL.|  
|**user_type_database**|**sysname**|Para tipos de CLR e de alias, contém o nome do banco de dados no qual o tipo é definido. Caso contrário, é NULL.|  
|**user_type_schema**|**sysname**|Para tipos de CLR e de alias, contém o nome do esquema no qual o tipo é definido. Caso contrário, é NULL.|  
|**user_type_name**|**sysname**|Para tipos de CLR e de alias, contém o nome do tipo. Caso contrário, é NULL.|  
|**assembly_qualified_type_name**|**nvarchar(4000)**|Para tipos de CLR, retorna o nome do assembly e da classe que define o tipo. Caso contrário, é NULL.|  
|**xml_collection_id**|**Int**|Contém o xml_collection_id do tipo de dados da coluna como especificado em sys.columns. Essa coluna retornará NULL se o tipo retornado não estiver associado uma coleção de esquemas XML.|  
|**xml_collection_database**|**sysname**|Contém o banco de dados no qual a coleção de esquemas XML associada a esse tipo está definida. Essa coluna retornará NULL se o tipo retornado não estiver associado uma coleção de esquemas XML.|  
|**xml_collection_schema**|**sysname**|Contém o esquema no qual a coleção de esquemas XML associada a esse tipo está definida. Essa coluna retornará NULL se o tipo retornado não estiver associado uma coleção de esquemas XML.|  
|**xml_collection_name**|**sysname**|Contém o nome da coleção de esquemas XML associada a esse tipo. Essa coluna retornará NULL se o tipo retornado não estiver associado uma coleção de esquemas XML.|  
|**is_xml_document**|**bit**|Retornará 1 se o tipo de dados retornado for o XML e esse tipo for garantido de ser um documento XML completo (incluindo um nó raiz), em vez de um fragmento XML. Caso contrário, retorna 0.|  
|**is_case_sensitive**|**bit**|Retornará 1 se a coluna for de um tipo de cadeia de caracteres com diferenciação de maiúsculas e minúsculas e 0 se não for.|  
|**is_fixed_length_clr_type**|**bit**|Retornará 1 se a coluna for de um tipo de CLR de comprimento fixo e 0 se não for.|  
|**source_server**|**sysname**|Nome do servidor de origem retornado pela coluna neste resultado (se a origem for um servidor remoto). O nome é fornecido como ele aparece em sys.  Retornará NULL se a coluna tiver origem no servidor local, ou se ele não puder ser determinado qual servidor de origem. Será populado somente se informações de navegação são solicitadas.|  
|**source_database**|**sysname**|Nome do banco de dados de origem retornado pela coluna neste resultado. Retornará NULL se o banco de dados não puder ser determinado. Será populado somente se informações de navegação são solicitadas.|  
|**source_schema**|**sysname**|Nome do esquema de origem retornado pela coluna neste resultado. Retornará NULL se o esquema não puder ser determinado. Será populado somente se informações de navegação são solicitadas.|  
|**source_table**|**sysname**|Nome da tabela de origem retornado pela coluna neste resultado. Retornará NULL se a tabela não puder ser determinada. Será populado somente se informações de navegação são solicitadas.|  
|**source_column**|**sysname**|Nome da coluna de origem retornada pela coluna neste resultado. Retornará NULL se a coluna não puder ser determinada. Será populado somente se informações de navegação são solicitadas.|  
|**is_identity_column**|**bit**|Retornará 1 se a coluna for uma coluna de identidade; caso contrário, retornará 0. Retornará NULL caso não seja possível determinar se a coluna é uma coluna de identidade.|  
|**is_part_of_unique_key**|**bit**|Retornará 1 se a coluna fizer parte de um índice exclusivo (incluindo restrição exclusiva e primária); caso contrário, retornará 0. Retornará NULL caso não seja possível determinar se a coluna faz parte de um índice exclusivo. Será populado somente se informações de navegação forem solicitadas.|  
|**is_updateable**|**bit**|Retornará 1 se a coluna for uma coluna atualizável; caso contrário, retornará 0. Retornará NULL caso não seja possível determinar se a coluna é atualizável.|  
|**is_computed_column**|**bit**|Retornará 1 se a coluna for uma coluna computada; caso contrário, retornará 0. Retorna NULL se não puder ser determinado que a coluna é uma coluna computada.|  
|**is_sparse_column_set**|**bit**|Retornará 1 se a coluna for uma coluna esparsa; caso contrário, retornará 0. Retornará NULL caso não seja possível determinar se a coluna faz parte de um conjunto de colunas esparsas.|  
|**ordinal_in_order_by_list**|**smallint**|A posição dessa coluna na lista ORDER BY. Retornará NULL se a coluna não for exibida na lista ORDER BY ou se a lista ORDER BY não puder ser determinada exclusivamente.|  
|**order_by_list_length**|**smallint**|Comprimento da lista ORDER BY. Retornará NULL se não houver uma lista ORDER BY ou se a lista ORDER BY não puder ser determinada exclusivamente. Observe que este valor será o mesmo para todas as linhas retornadas por sp_describe_first_result_set.|  
|**order_by_is_descending**|**smallint NULL**|Se o ordinal_in_order_by_list não for NULL, o **order_by_is_descending** coluna relatará a direção da cláusula ORDER BY para essa coluna. Caso contrário, relatará NULL.|  
|**error_number**|**Int**|Contém o número do erro retornado pela função. Conterá NULL se nenhum erro tiver ocorrido na coluna.|  
|**error_severity**|**Int**|Contém a severidade do erro retornado pela função. Conterá NULL se nenhum erro tiver ocorrido na coluna.|  
|**error_state**|**Int**|Contém a mensagem de estado retornada pela função. Se nenhum erro ocorreu. a coluna conterá NULL.|  
|**error_message**|**nvarchar(4096)**|Contém a mensagem retornada pela função. Se nenhum erro ocorreu, a coluna conterá NULL.|  
|**error_type**|**Int**|Contém um inteiro que representa o erro que é retornado. Mapeia para error_type_desc. Consulte a lista sob comentários.|  
|**error_type_desc**|**nvarchar(60)**|Contém uma pequena cadeia de caracteres maiúsculos que representa o erro sendo retornado. Mapeia para error_type. Consulte a lista sob comentários.|  
  
## <a name="remarks"></a>Remarks  
 Essa função usa o mesmo algoritmo como **sp_describe_first_result_set**. Para obter mais informações, consulte [sp_describe_first_result_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md).  
  
 A tabela a seguir lista os tipos de erros e suas descrições  
  
|error_type|error_type|Description|  
|-----------------|-----------------|-----------------|  
|1|MISC|Todos os erros que não são descritos de outra forma.|  
|2|SYNTAX|Um erro de sintaxe ocorreu no lote.|  
|3|CONFLICTING_RESULTS|O resultado não pôde ser determinado devido a um conflito entre duas primeiras instruções possíveis.|  
|4|DYNAMIC_SQL|O resultado não pôde ser determinado devido a um SQL dinâmico que poderia retornar o primeiro resultado.|  
|5|CLR_PROCEDURE|O resultado não pôde ser determinado devido a um procedimento armazenado de CLR que poderia retornar o primeiro resultado.|  
|6|CLR_TRIGGER|O resultado não pôde ser determinado devido a um gatilho CLR que poderia retornar o primeiro resultado.|  
|7|EXTENDED_PROCEDURE|O resultado não pôde ser determinado devido a um procedimento armazenado estendido que poderia retornar o primeiro resultado.|  
|8|UNDECLARED_PARAMETER|O resultado não pôde ser determinado por que o tipo de dados de uma ou mais das colunas do conjunto de resultados depende de um parâmetro não declarado.|  
|9|RECURSION|O resultado não pôde ser determinado porque o lote contém uma instrução recursiva.|  
|10|TEMPORARY_TABLE|O resultado não pôde ser determinado porque o lote contém uma tabela temporária e não é suportado pelo **sp_describe_first_result_set** .|  
|11|UNSUPPORTED_STATEMENT|O resultado não pôde ser determinado porque o lote contém uma instrução que não é suportada pelo **sp_describe_first_result_set** (por exemplo, FETCH, REVERT, etc.).|  
|12|OBJECT_ID_NOT_SUPPORTED|O @object_id passado para a função é não suportado (ou seja, não um procedimento armazenado)|  
|13|OBJECT_ID_DOES_NOT_EXIST|O @object_id passado para a função não foi encontrada no catálogo do sistema.|  
  
## <a name="permissions"></a>Permissões  
 Requer permissão para executar o @tsql argumento.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-returning-metadata-with-and-without-browse-information"></a>A. Retornando metadados com e sem informações de procura  
 O exemplo a seguir cria um procedimento armazenado chamado TestProc2 que retorna dois conjuntos de resultados. Em seguida, o exemplo demonstra que **sys.DM exec_describe_first_result_set** retorna informações sobre o primeiro conjunto de resultados no procedimento, com e sem informações de procura.  
  
```  
CREATE PROC TestProc2  
AS  
SELECT object_id, name FROM sys.objects ;  
SELECT name, schema_id, create_date FROM sys.objects ;  
GO  
  
SELECT * FROM sys.dm_exec_describe_first_result_set_for_object(OBJECT_ID('TestProc2'), 0) ;  
SELECT * FROM sys.dm_exec_describe_first_result_set_for_object(OBJECT_ID('TestProc2'), 1) ;  
GO  
```  
  
### <a name="b-combining-the-sysdmexecdescribefirstresultsetforobject-function-and-a-table-or-view"></a>B. Combinando a função sys.dm_exec_describe_first_result_set_for_object e uma tabela ou exibição  
 O exemplo a seguir usa os dois a exibição de catálogo do sistema Procedures e **sys.DM exec_describe_first_result_set_for_object** função para exibir metadados para os conjuntos de resultados de todos os procedimentos armazenados de [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] banco de dados.  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT p.name, r.*   
FROM sys.procedures AS p  
CROSS APPLY sys.dm_exec_describe_first_result_set_for_object(p.object_id, 0) AS r;  
GO  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [sp_describe_first_result_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)   
 [sp_describe_undeclared_parameters &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md)   
 [sys.dm_exec_describe_first_result_set &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md)  
  
  
