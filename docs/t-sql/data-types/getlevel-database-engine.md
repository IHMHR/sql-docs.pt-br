---
title: GetLevel (mecanismo de banco de dados) | Microsoft Docs
ms.custom: 
ms.date: 07/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GetLevel
- GetLevel_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetLevel [Database Engine]
ms.assetid: 81577d7e-8ff6-4e73-b7f4-94c03d4921e7
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aac401d8fbe9546404f44f5fa2455f9e9c5dfe9d
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="getlevel-database-engine"></a>GetLevel (Mecanismo de Banco de Dados)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retorna um inteiro que representa a profundidade do nó *isso* na árvore.
  
## <a name="syntax"></a>Sintaxe  
  
```sql
-- Transact-SQL syntax  
node.GetLevel ( )   
```  
  
```sql
-- CLR syntax  
SqlInt16 GetLevel ( )   
```  
  
## <a name="return-types"></a>Tipos de retorno  
**Tipo de retorno do SQL Server: smallint**
  
**Tipo de retorno CLR: SqlInt16**
  
## <a name="remarks"></a>Comentários  
Usado para determinar o nível de um ou mais nós ou para filtrar os nós de membros de um nível especificado. A raiz da hierarquia é nível 0.
  
GetLevel é muito útil para índices de pesquisa de primeira amplitude. Para obter mais informações, consulte [dados hierárquicos &#40; SQL Server &#41; ](../../relational-databases/hierarchical-data-sql-server.md).
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-returning-the-hierarchy-level-as-a-column"></a>A. Retornando o nível de hierarquia como uma coluna  
O exemplo a seguir retorna uma representação de texto do **hierarchyid**e, em seguida, o nível de hierarquia como o **EmpLevel** coluna para todas as linhas na tabela:
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode,   
OrgNode.GetLevel() AS EmpLevel, *  
FROM HumanResources.EmployeeDemo;  
```  
  
### <a name="b-returning-all-members-of-a-hierarchy-level"></a>B. Retornando todos os membros de um nível de hierarquia  
O seguinte exemplo retorna todas as linhas na tabela no nível de hierarquia 2:
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode,   
OrgNode.GetLevel() AS EmpLevel, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetLevel() = 2;  
```  
  
### <a name="c-returning-the-root-of-the-hierarchy"></a>C. Retornando a raiz da hierarquia  
O seguinte exemplo retorna a raiz da árvore do nível de hierarquia:
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode,   
OrgNode.GetLevel() AS EmpLevel, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetLevel() = 0;  
```  
  
### <a name="d-clr-example"></a>D. Exemplo de CLR  
O trecho de código a seguir chama o método GetLevel ():
  
```sql
this.GetLevel()  
```  
  
## <a name="see-also"></a>Consulte também
[Referência de método de tipo de dados hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Dados hierárquicos &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
