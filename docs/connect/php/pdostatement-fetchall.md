---
title: PDOStatement::fetchAll | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be74188a-77cd-4d19-b16e-77278373c979
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8e2d4b63c1ff67ab74f01918041a8c89703431df
ms.contentlocale: pt-br
ms.lasthandoff: 09/09/2017

---
# <a name="pdostatementfetchall"></a>PDOStatement::fetchAll
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Retorna as linhas em um conjunto de resultados em uma matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
array PDOStatement::fetchAll([ $fetch_style[, $column_index ][, ctor_args]] );  
```  
  
#### <a name="parameters"></a>Parâmetros  
$*fetch_style*: um símbolo (inteiro) especificando o formato dos dados da linha. Consulte [PDOStatement::fetch](../../connect/php/pdostatement-fetch.md) para obter uma lista de valores. PDO::FETCH_COLUMN também é permitido. PDO::FETCH_BOTH é o padrão.  
  
$*column_index*: um valor inteiro que representa a coluna a ser retornada se $*fetch_style* é PDO:: fetch_column. 0 é o padrão.  
  
$*ctor_args*: uma matriz de parâmetros para um construtor de classe quando $*fetch_style* é fetch_class ou PDO:: fetch_obj.  
  
## <a name="return-value"></a>Valor de retorno  
Uma matriz das linhas restantes do conjunto de resultados, ou false em caso de falha na chamada do método.  
  
## <a name="remarks"></a>Comentários  
O suporte para PDO foi adicionado na versão 2.0 dos [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Exemplo  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   print "-----------\n";  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetchall(PDO::FETCH_BOTH);  
   print_r( $result );  
   print "\n-----------\n";  
  
   print "-----------\n";  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetchall(PDO::FETCH_NUM);  
   print_r( $result );  
   print "\n-----------\n";  
  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetchall(PDO::FETCH_COLUMN, 1);  
   print_r( $result );  
   print "\n-----------\n";  
  
   class cc {  
      function __construct( $arg ) {  
         echo "$arg\n";  
      }  
  
      function __toString() {  
         echo "To string\n";  
      }  
   };  
  
   $stmt = $conn->query( 'SELECT TOP(2) * FROM Person.ContactType' );  
   $all = $stmt->fetchAll( PDO::FETCH_CLASS, 'cc', array( 'Hi!' ));  
   var_dump( $all );  
?>  
```  
  
## <a name="see-also"></a>Consulte também  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
