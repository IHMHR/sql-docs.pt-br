---
title: Dicas de junção (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|queries
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Join Hint
- Join_Hint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- HASH join hint
- REMOTE join hint
- LOOP join hint
- join hints
- MERGE join hint
- hints [SQL Server], join
ms.assetid: 09069f4a-f2e3-4717-80e1-c0110058efc4
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b350421cd40a23f6fdebefa797b22367f1ef6a58
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="hints-transact-sql---join"></a>Dicas (Transact-SQL) – junção
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Dicas de junção especificam que o otimizador de consulta força uma estratégia de junção entre duas tabelas no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Para obter informações gerais sobre junções e a sintaxe de junção, confira [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md).  
  
> [!IMPORTANT]  
>  Como o otimizador de consulta do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] costuma selecionar o melhor plano de execução para uma consulta, é recomendável que as dicas, como \<join_hint>, sejam usadas apenas como um último recurso por desenvolvedores e administradores de banco de dados experientes.
  
 **Aplica-se a:**  
  
 [DELETE](../../t-sql/statements/delete-transact-sql.md)  
  
 [SELECT](../../t-sql/queries/select-transact-sql.md)  
  
 [UPDATE](../../t-sql/queries/update-transact-sql.md)  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
<join_hint> ::=   
     { LOOP | HASH | MERGE | REMOTE }  
```  
  
## <a name="arguments"></a>Argumentos  
 LOOP | HASH | MERGE  
 Especifica que a junção na consulta deve usar loop, hash ou mesclagem. O uso de LOOP | HASH | MERGE JOIN força uma junção específica entre duas tabelas. LOOP não pode ser especificado com RIGHT ou FULL como um tipo de junção.  
  
 REMOTE  
 Especifica que a operação de junção é executada no site da tabela direita. Isso é útil quando a tabela esquerda é uma tabela local e a tabela direita é uma tabela remota. REMOTE deverá ser usado somente quando a tabela esquerda tiver menos linhas do que a tabela direita.  
  
 Se a tabela direita for local, a junção será executada localmente. Se ambas as tabelas forem remotas, mas de fontes de dados diferentes, REMOTE fará com que a junção seja executada no site da tabela direita. Se ambas as tabelas forem tabelas remotas da mesma fonte de dados, REMOTE não será requerido.  
  
 REMOTE não poderá ser usado quando um dos valores que são comparados no predicado de junção for lançado em um agrupamento diferente usando a cláusula COLLATE.  
  
 REMOTE poderá ser usado somente para operações de INNER JOIN.  
  
## <a name="remarks"></a>Remarks  
 Dicas de junção são especificadas na cláusula FROM de uma consulta. Dicas de Junção forçam uma estratégia de junção entre duas tabelas. Se uma dica de junção for especificada para qualquer uma das duas tabelas, o otimizador de consulta forçará a ordem de junção automaticamente para todas as tabelas associadas na consulta, com base na posição das palavras-chave ON. Quando CROSS JOIN for usado sem a cláusula ON, poderão ser usados parênteses para indicar a ordem da junção.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-using-hash"></a>A. Usando HASH  
 O exemplo a seguir especifica que a operação `JOIN` na consulta é executada por uma junção `HASH`. O exemplo usa o banco de dados [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT p.Name, pr.ProductReviewID  
FROM Production.Product AS p  
LEFT OUTER HASH JOIN Production.ProductReview AS pr  
ON p.ProductID = pr.ProductID  
ORDER BY ProductReviewID DESC;  
```  
  
### <a name="b-using-loop"></a>B. Usando LOOP  
 O exemplo a seguir especifica que a operação `JOIN` na consulta é executada por uma junção `LOOP`. O exemplo usa o banco de dados [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
DELETE FROM Sales.SalesPersonQuotaHistory   
FROM Sales.SalesPersonQuotaHistory AS spqh  
    INNER LOOP JOIN Sales.SalesPerson AS sp  
    ON spqh.SalesPersonID = sp.SalesPersonID  
WHERE sp.SalesYTD > 2500000.00;  
GO  
```  
  
### <a name="c-using-merge"></a>C. Usando MERGE  
 O exemplo a seguir especifica que a operação `JOIN` na consulta é executada por uma junção `MERGE`. O exemplo usa o banco de dados [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT poh.PurchaseOrderID, poh.OrderDate, pod.ProductID, pod.DueDate, poh.VendorID   
FROM Purchasing.PurchaseOrderHeader AS poh  
INNER MERGE JOIN Purchasing.PurchaseOrderDetail AS pod   
    ON poh.PurchaseOrderID = pod.PurchaseOrderID;  
GO  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Hints &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql.md)  
  
  
