---
title: Instruções SQL inseridas pelo usuário | Microsoft Docs
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
- user-entered SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], entered by user
ms.assetid: 109af162-93ba-425a-8fe5-49c7dc7cc784
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1be7159d7f56226c94b6cbfa335883b73df15de1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sql-statements-entered-by-the-user"></a>Instruções SQL inseridas pelo usuário
Aplicativos que executam a análise ad hoc também costuma permitem que o usuário insira as instruções SQL diretamente. Por exemplo:  
  
```  
SQLCHAR *     Statement, SqlState[6], Msg[SQL_MAX_MESSAGE_LENGTH];  
SQLSMALLINT   i, MsgLen;  
SQLINTEGER    NativeError;  
SQLRETURN     rc1, rc2;  
  
// Prompt user for SQL statement.  
GetSQLStatement(Statement);  
  
// Execute the statement directly. Because it will be executed only once,  
// do not prepare it.  
rc1 = SQLExecDirect(hstmt, Statement, SQL_NTS);  
  
// Process any errors or returned information.  
if ((rc1 == SQL_ERROR) || rc1 == SQL_SUCCESS_WITH_INFO) {  
   i = 1;  
   while ((rc2 = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, SqlState, &NativeError,  
         Msg, sizeof(Msg), &MsgLen)) != SQL_NO_DATA) {  
      DisplayError(SqlState, NativeError, Msg, MsgLen);  
      i++;  
   }  
}  
```  
  
 Essa abordagem simplifica a codificação de aplicativo; o aplicativo se baseia no usuário para criar a instrução SQL e na fonte de dados para verificar a validade da instrução. Como é difícil escrever uma interface gráfica do usuário que expõe adequadamente a complexidade do SQL, simplesmente pedindo que o usuário insira o texto da instrução SQL pode ser uma alternativa melhor. No entanto, isso requer que o usuário sabe não apenas SQL, mas também o esquema da fonte de dados que está sendo consultada. Alguns aplicativos fornecem uma interface gráfica do usuário pelo qual o usuário pode criar uma instrução SQL básica e também fornecem uma interface de texto com a qual o usuário pode modificar.
