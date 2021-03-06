---
title: sqlsrv_cancel | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- sqlsrv_cancel
apitype: NA
helpviewer_keywords:
- sqlsrv_cancel
- API Reference, sqlsrv_cancel
ms.assetid: 75798c9b-f711-445d-9b8f-ba4d405ca50a
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c6173e20a99622a42264591c3a83024fda5d2bd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsrvcancel"></a>sqlsrv_cancel
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cancela uma instrução. Isso significa que qualquer resultado pendente para a instrução será descartado. Depois que essa função é chamada, a instrução pode ser executada novamente se ele tiver sido preparada com [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md). Não é necessário chamar essa função se todos os resultados associados à instrução tiverem sido consumidos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sqlsrv_cancel( resource $stmt)  
```  
  
#### <a name="parameters"></a>Parâmetros  
*$stmt*: A instrução a ser cancelada.  
  
## <a name="return-value"></a>Valor de retorno  
Um valor booliano: **true** se a operação foi bem-sucedida. Caso contrário, **false**.  
  
## <a name="example"></a>Exemplo  
O seguinte exemplo tem como alvo o [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) de banco de dados para executar uma consulta, em seguida, consome e conta os resultados até que a variável *$salesTotal* atinja um valor especificado. Os resultados da consulta restantes são, então, descartados. O exemplo supõe que o SQL Server e o banco de dados AdventureWorks estejam instalados no computador local. Toda a saída será gravada no console quando o exemplo for executado da linha de comando.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Prepare and execute the query. */  
$tsql = "SELECT OrderQty, UnitPrice FROM Sales.SalesOrderDetail";  
$stmt = sqlsrv_prepare( $conn, $tsql);  
if( $stmt === false )  
{  
     echo "Error in statement preparation.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
if( sqlsrv_execute( $stmt ) === false)  
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Initialize tracking variables. */  
$salesTotal = 0;  
$count = 0;  
  
/* Count and display the number of sales that produce revenue  
of $100,000. */  
while( ($row = sqlsrv_fetch_array( $stmt)) && $salesTotal <=100000)  
{  
     $qty = $row[0];  
     $price = $row[1];  
     $salesTotal += ( $price * $qty);  
     $count++;  
}  
echo "$count sales accounted for the first $$salesTotal in revenue.\n";  
  
/* Cancel the pending results. The statement can be reused. */  
sqlsrv_cancel( $stmt);  
?>  
```  
  
## <a name="comments"></a>Comentários  
Uma instrução é preparada e executada usando a combinação de [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) e [sqlsrv_execute](../../connect/php/sqlsrv-execute.md) pode ser executada novamente com **sqlsrv_execute** após chamar **sqlsrv_cancel**. Uma instrução que é executada com [sqlsrv_query](../../connect/php/sqlsrv-query.md) não pode ser executada novamente depois de chamar **sqlsrv_cancel**.  
  
## <a name="see-also"></a>Consulte também  
[Referência da API do driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Conectando-se ao servidor](../../connect/php/connecting-to-the-server.md)

[Recuperando dados](../../connect/php/retrieving-data.md)

[Sobre exemplos de código na documentação](../../connect/php/about-code-examples-in-the-documentation.md)

[sqlsrv_free_stmt](../../connect/php/sqlsrv-free-stmt.md)

  
