---
title: Método (Java.IO. InputStream, long) updateAsciiStream | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d426e8b9-62b7-49f8-9863-8697fd3a7085
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2a316ac4ec748789e908887b05a8727591d60f1d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="updateasciistream-method-javalangstring-javaioinputstream-long"></a>Método updateAsciiStream (java.lang.String, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Atualiza a coluna designada com um valor de fluxo ASCII que terá o número de bytes especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void updateAsciiStream(java.lang.String columnName,  
                              java.io.InputStream streamValue,  
                              long length)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *columnName*  
  
 Um **cadeia de caracteres** que contém o nome da coluna.  
  
 *streamValue*  
  
 Um objeto InputStream.  
  
 *Comprimento*  
  
 O comprimento do fluxo.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Esse método updateAsciiStream é especificado pelo método updateAsciiStream na interface Java.SQL. resultset.  
  
 Esse método passa caracteres ASCII (bytes) de um objeto InputStream para colunas de caracteres conversíveis, que são o intervalo ASCII [0x00 – 0x7F] do Unicode e 874, 932, 936, 949, 950 e 1250 a 1258 páginas de código. Esse método executa uma conversão na página de agrupamento de destino. A tentativa de atualizar uma coluna de destino não conversível fará com que uma exceção seja lançada. Para colunas binárias, são passados bytes brutos.  
  
 Se o comprimento do fluxo for diferente do especificado no *comprimento* parâmetro, o driver JDBC lançará uma exceção quando a linha for atualizada ou inserida.  
  
 Se o comprimento do fluxo for desconhecido, o *comprimento* parâmetro pode ser definido como -1 para indicar que o driver deve aceitar o fluxo independentemente de seu tamanho. Com sqljdbc4.jar, é recomendável que você use o método do JDBC 4.0 [método updateAsciiStream &#40;Java, Java.IO. InputStream&#41; ](../../../connect/jdbc/reference/updateasciistream-method-java-lang-string-java-io-inputstream.md) quando o aplicativo quiser atualizar a coluna de um fluxo cujo comprimento é desconhecido.  
  
## <a name="see-also"></a>Consulte também  
 [Método updateAsciiStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)   
 [Membros de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
