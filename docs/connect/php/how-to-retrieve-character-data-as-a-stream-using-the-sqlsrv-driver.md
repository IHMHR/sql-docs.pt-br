---
title: Recuperar dados de caracteres como um fluxo usando o Driver SQLSRV | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retrieving data, as a character stream
- streaming data
ms.assetid: 3c0dbca4-abfc-4449-b133-66c819681840
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 30d0b0884b258d494ffadcb3d44b76f197a445a5
ms.contentlocale: pt-br
ms.lasthandoff: 09/09/2017

---
# <a name="how-to-retrieve-character-data-as-a-stream-using-the-sqlsrv-driver"></a>Como recuperar dados de caractere como um fluxo usando o driver SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Recuperação de dados como um fluxo só está disponível no driver SQLSRV do [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]e não está disponível no driver PDO_SQLSRV.  
  
O driver SQLSRV aproveita os fluxos do PHP para recuperar grandes quantidades de dados do servidor. O exemplo neste tópico demonstra como recuperar dados de caractere como um fluxo.  
  
## <a name="example"></a>Exemplo  
O exemplo a seguir recupera uma linha da tabela *Production.ProductReview* do banco de dados AdventureWorks. O campo *Comments* da linha retornada é recuperado como um fluxo e exibido usando a função [fpassthru](http://go.microsoft.com/fwlink/?LinkId=217496) do PHP.  
  
A recuperação de dados como um fluxo é efetuada usando [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md) e [sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md) com o tipo de retorno especificado como um fluxo de caractere. O tipo de retorno é especificado usando a constante **SQLSRV_PHPTYPE_STREAM**. Para obter informações sobre **sqlsrv** constantes, consulte [constantes &#40; Drivers da Microsoft para PHP para SQL Server &#41; ](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).  
  
O exemplo supõe que o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e o banco de dados [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) estejam instalados no computador local. Toda a saída será gravada no console quando o exemplo for executado a partir da linha de comando.  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the Transact-SQL query. */  
$tsql = "SELECT ReviewerName,   
               CONVERT(varchar(32), ReviewDate, 107) AS [ReviewDate],  
               Rating,   
               Comments   
         FROM Production.ProductReview   
         WHERE ProductReviewID = ? ";  
  
/* Set the parameter value. */  
$productReviewID = 1;  
$params = array( $productReviewID);  
  
/* Execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if( $stmt === false )  
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the data. The first three fields are retrieved  
as strings and the fourth as a stream with character encoding. */  
if(sqlsrv_fetch( $stmt ) === false )  
{  
     echo "Error in retrieving row.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
echo "Name: ".sqlsrv_get_field( $stmt, 0 )."\n";  
echo "Date: ".sqlsrv_get_field( $stmt, 1 )."\n";  
echo "Rating: ".sqlsrv_get_field( $stmt, 2 )."\n";  
echo "Comments: ";  
$comments = sqlsrv_get_field( $stmt, 3,   
                             SQLSRV_PHPTYPE_STREAM(SQLSRV_ENC_CHAR));  
fpassthru($comments);  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
Como nenhum tipo de retorno do PHP é especificado para os três primeiros campos, cada campo é retornado de acordo com seu tipo do PHP padrão. Para obter informações sobre os tipos de dados padrão do PHP, consulte [Default PHP Data Types](../../connect/php/default-php-data-types.md). Para obter informações sobre como especificar tipos de retorno do PHP, consulte [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
## <a name="see-also"></a>Consulte também  
[Recuperando dados](../../connect/php/retrieving-data.md)  
[Recuperando dados como um fluxo usando o driver SQLSRV](../../connect/php/retrieving-data-as-a-stream-using-the-sqlsrv-driver.md)  
[Sobre exemplos de código na documentação](../../connect/php/about-code-examples-in-the-documentation.md)  
  
