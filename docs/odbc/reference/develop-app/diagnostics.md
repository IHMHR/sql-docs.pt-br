---
title: Diagnóstico | Microsoft Docs
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
- diagnostic information [ODBC]
- functions [ODBC], diagnostic information
- diagnostic information [ODBC], about diagnostic information
ms.assetid: 450abd88-90a1-4fbc-b417-8efbdd8e1dea
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d2db5f46fc157015f035775ac185fb9005de8a6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="diagnostics"></a>diagnóstico
Funções em ODBC retornam informações de diagnóstico de duas maneiras. O código de retorno indica o êxito ou falha da função, geral, enquanto os registros de diagnóstico fornecem informações detalhadas sobre a função. Pelo menos um registro de diagnóstico, o registro de cabeçalho, será retornada mesmo se a função tiver êxito.  
  
 Informações de diagnóstico são usadas em tempo de desenvolvimento para capturar erros de programação como identificadores inválidos e erros de sintaxe em instruções de SQL embutido. Ele é usado em tempo de execução para capturar erros e avisos, como truncamento de dados, violações de acesso e erros de sintaxe em instruções SQL inseridas pelo usuário.  
  
 Esta seção contém os tópicos a seguir.  
  
-   [Códigos de retorno](../../../odbc/reference/develop-app/return-codes-odbc.md)  
  
-   [Registros de diagnóstico](../../../odbc/reference/develop-app/diagnostic-records.md)  
  
-   [Usando SQLGetDiagRec e SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Implementando SQLGetDiagRec e SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Exemplos de tratamento de diagnóstico](../../../odbc/reference/develop-app/diagnostic-handling-examples.md)
