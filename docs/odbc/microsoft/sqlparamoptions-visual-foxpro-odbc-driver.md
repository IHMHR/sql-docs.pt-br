---
title: Para SQLParamOptions (Driver ODBC do Visual FoxPro) | Microsoft Docs
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
- SQLParamOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 7f94a6e2-9c34-405c-b2b0-304d94269715
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bdced0993d2efc27a2fb40091576c47b931e892a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sqlparamoptions-visual-foxpro-odbc-driver"></a>Para SQLParamOptions (Driver ODBC do Visual FoxPro)
> [!NOTE]  
>  Este tópico contém informações específicas do Driver ODBC do Visual FoxPro. Para obter informações gerais sobre esta função, consulte o tópico apropriado em [referência da API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Suporte: completo  
  
 Conformidade de API de ODBC: Nível 1  
  
 Permite que um aplicativo especificar vários valores para o conjunto de parâmetros atribuído por [SQLBindParameter](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md). A capacidade de especificar vários valores para um conjunto de parâmetros é útil para inserções em massa e outro trabalho que exija a fonte de dados para processar a mesma instrução SQL várias vezes com vários valores de parâmetro. Por exemplo, um aplicativo pode especificar três conjuntos de valores para o conjunto de parâmetros associados a um **inserir** instrução e, em seguida, execute o **inserir** Inserir instrução uma vez para executar os três operações.  
  
 Para obter mais informações, consulte [para SQLParamOptions](../../odbc/reference/syntax/sqlparamoptions-function.md) no *referência do programador de ODBC*.
