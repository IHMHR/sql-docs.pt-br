---
title: Exemplo de diagnóstico do Driver baseada em arquivo | Microsoft Docs
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
- file-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: 0575fccd-4641-478d-a3cc-5a764e35bae2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d58072bebac57eca8976064b85a25999475a9586
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="file-based-driver-diagnostic-example"></a>Exemplo de diagnóstico baseada em arquivo de Driver
Um driver baseada em arquivo atua como um driver ODBC e uma fonte de dados. Portanto, ele pode gerar erros e avisos, como um componente em uma conexão ODBC e como uma fonte de dados. Como também é o componente que faz interface com o Gerenciador de Driver, formatos e retorna os argumentos para **SQLGetDiagRec**.  
  
 Por exemplo, se um driver de Microsoft® para dBASE não foi possível alocar memória suficiente, ele pode retornar os seguintes valores de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY001"  
Native Error:      42052  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver]Unable to allocate sufficient memory."  
```  
  
 Como esse erro não foi relacionado à fonte de dados, o driver somente adicionadas prefixos à mensagem de diagnóstico do fornecedor ([Microsoft]) e o driver ([ODBC Driver dBASE]).  
  
 Se o driver não foi possível encontrar o arquivo Employee. dbf, ele pode retornar os seguintes valores de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1305  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver][dBASE]No such table or object"  
```  
  
 Como esse erro foi relacionado à fonte de dados, o driver adicionado o formato de arquivo da fonte de dados ([dBASE]) como um prefixo para a mensagem de diagnóstica. Como o driver também era o componente de interagir com a fonte de dados, ele adicionou prefixos para o fornecedor ([Microsoft]) e o driver ([ODBC Driver dBASE]).
