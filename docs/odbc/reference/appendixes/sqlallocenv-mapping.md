---
title: Mapeamento de SQLAllocEnv | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 75c17775183ba1bcb3164015679adf49a76f6828
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sqlallocenv-mapping"></a>Mapeamento de SQLAllocEnv
Quando um aplicativo chama **SQLAllocEnv** por meio de um ODBC 3 *. x* driver, a chamada para **SQLAllocEnv**(*phenv*) é mapeado para **SQLAllocHandle** da seguinte maneira:  
  
1.  O Gerenciador de Driver aloca um identificador de ambiente e o retorna ao aplicativo. As chamadas de Gerenciador de Driver **SQLSetEnvAttr** para definir o atributo de ambiente SQL_ATTR_ODBC_VERSION como SQL_OV_ODBC2.  
  
2.  Quando o aplicativo estabelece a primeira conexão para um driver, chama o Gerenciador de Driver  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     no driver com *OutputHandlePtr* definida como *phenv*.
