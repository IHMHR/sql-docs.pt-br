---
title: SQLFreeStmt | Microsoft Docs
ms.custom: 
ms.date: 11/23/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e84e2d33e2c6c6a56b0f69f95091b99c81593f9e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="sqlfreestmt"></a>SQLFreeStmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Em geral   
      **SQLFreeStmt** não é recomendado no ODBC 3.0 e posterior. No entanto se o aplicativo precisa reutilizar a instrução ainda use **SQLFreeStmt** com o **SQL_RESET_PARAMS** e **SQL_UNBIND** opções). Você também pode usar [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md), [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md), [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md), [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md), e [ SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) para substituir ou duplicam a função do **SQLFreeStmt** e devem ser usadas em vez disso.  
  
 Em geral, é mais eficiente reutilizar instruções que to descartá-los e alocar novos. No entanto em algumas situações, como a reutilização de instruções, SQLFreeStmt ainda deve ser usada.  
  
## <a name="see-also"></a>Consulte também  
 [Função SQLFreeStmt](http://go.microsoft.com/fwlink/?LinkId=59346)   
 [Detalhes da implementação da API do ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  