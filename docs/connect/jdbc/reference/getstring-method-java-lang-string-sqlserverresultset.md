---
title: Método (Java) (SQLServerResultSet) getString | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.getString (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8a98c8a8-61d0-40c9-9335-25a87b732dc3
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f615ce3f4f9fcd883ccb9f8ebc380c5e71e1a4eb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="getstring-method-javalangstring-sqlserverresultset"></a>getString método (Java) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera o valor do nome da coluna designada na linha atual deste [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) de objeto como um **cadeia de caracteres** na linguagem de programação Java.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public java.lang.String getString(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *columnName*  
  
 Um **cadeia de caracteres** que contém o nome da coluna.  
  
## <a name="return-value"></a>Valor de retorno  
 Um **cadeia de caracteres** valor.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Esse método getString é especificado pelo método getString na interface Java.SQL. resultset.  
  
 Todas as colunas no SQL Server podem ser retornadas como uma String. Isso significa que um **cadeia de caracteres** representação de todos os tipos baseados em número e baseados em caracteres e uma representação de cadeia de caracteres hexadecimais de colunas binárias, como binary, varbinary, varbinary (max), imagem, timestamp e uniqueidentifier, podem ser retornado.  
  
 Os tipos que diferenciam local, como money, smallmoney, datetime, smalldatetime, float, real, decimal e numeric, retornarão o formato toString() canônico para o valor subjacente do tipo.  
  
 Tipos definidos pelo usuário são retornados como hexadecimal **cadeia de caracteres** valores.  
  
## <a name="see-also"></a>Consulte também  
 [Método getString &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)   
 [Membros de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
