---
title: C para exemplos de conversão de dados SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], examples
- data conversions from C to SQL types [ODBC], examples
ms.assetid: 9f390afc-d8b8-4286-b559-98b3b8781f3d
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fcba6d92970d0e0b5490f4c24506fe8bb2951217
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="c-to-sql-data-conversion-examples"></a>C para exemplos de conversão de dados SQL
Os exemplos a seguir ilustram como o driver converte dados de C para dados do SQL:  
  
|Identificador de tipo C|Valor de dados C|Tipo SQL<br /><br /> identificador|Coluna<br /><br /> comprimento|Dados SQL<br /><br /> value|SQLSTATE|  
|-----------------------|------------------|-----------------------------|-----------------------|------------------------|--------------|  
|SQL_C_CHAR|abcdef\0 [a]|SQL_CHAR|6|abcdef|n/d|  
|SQL_C_CHAR|abcdef\0 [a]|SQL_CHAR|5|abcde|22001|  
|SQL_C_CHAR|1234.56\0 [a]|SQL_DECIMAL|8 [b]|1234.56|n/d|  
|SQL_C_CHAR|1234.56\0 [a]|SQL_DECIMAL|7 [b]|1234.5|22001|  
|SQL_C_CHAR|1234.56\0 [a]|SQL_DECIMAL|4|----|22003|  
|SQL_C_FLOAT|1234.56|SQL_FLOAT|n/d|1234.56|n/d|  
|SQL_C_FLOAT|1234.56|SQL_INTEGER|n/d|1234|22001|  
|SQL_C_FLOAT|1234.56|SQL_TINYINT|n/d|----|22003|  
|SQL_C_TYPE_DATE|1992,12,31 [c]|SQL_CHAR|10|1992-12-31|n/d|  
|SQL_C_TYPE_DATE|1992,12,31 [c]|SQL_CHAR|9|----|22003|  
|SQL_C_TYPE_DATE|1992,12,31 [c]|SQL_TIMESTAMP|n/d|1992-12-31 00:00:00.0|n/d|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000 [d]|SQL_CHAR|22|1992-12-31 23:45:55.12|n/d|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000 [d]|SQL_CHAR|21|1992-12-31 23:45:55.1|22001|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000 [d]|SQL_CHAR|18|----|22003|  
  
 [a] "\0" representa um byte nulo de terminação. O byte nulo de terminação é necessário somente se o comprimento dos dados é SQL_NTS.  
  
 [b] em além para bytes de números, um byte é necessário para um logon e outro bytes é necessária para o ponto decimal.  
  
 [c] o os números na lista são armazenados nos campos da estrutura de SQL_DATE_STRUCT.  
  
 [d] o os números na lista são armazenados nos campos da estrutura de SQL_TIMESTAMP_STRUCT.
