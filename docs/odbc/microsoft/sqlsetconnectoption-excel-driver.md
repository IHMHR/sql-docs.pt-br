---
title: SQLSetConnectOption (Driver do Excel) | Microsoft Docs
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
- SQLSetConnectOption function [ODBC], Excel Driver
- Excel driver [ODBC], SQLSetConnectOption
ms.assetid: 528d21d1-4516-4497-9da4-7b87d77e622a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 47f212a362715d43f522cd4e36bced9ce18825d2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetconnectoption-excel-driver"></a>SQLSetConnectOption (Driver do Excel)
> [!NOTE]  
>  Este tópico fornece informações específicas de Driver do Excel. Para obter informações gerais sobre esta função, consulte o tópico apropriado em [referência da API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|fOption|Comentário|  
|-------------|-------------|  
|SQL_ACCESS_MODE|O fOption SQL_ACCESS_MODE pode ser definido como SQL_MODE_READ_ONLY ou SQL_MODE_READ_WRITE. No entanto, o driver não impede que atualizações se SQL_ACCESS_MODE for definido como SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|O driver do Microsoft Excel só dá suporte a SQL_AUTOCOMMIT sendo definido como (o estado padrão), porque eles não dão suporte a transações.|  
|SQL_CURRENT_QUALIFIER|Tem suporte.|  
|SQL_LOGIN_TIMEOUT|Sem suporte.|  
|SQL_OPT_TRACE|Tem suporte.|  
|SQL_OPT_TRACEFILE|Tem suporte.|  
|SQL_PACKET_SIZE|Sem suporte.|  
|SQL_QUIET_MODE|Sem suporte.|  
|SQL_TRANSLATE_DLL|Sem suporte.|  
|SQL_TRANSLATION_OPTION|Sem suporte.|  
|SQL_TXN_ISOLATION|Sem suporte.|
