---
title: Diagnóstico de tratamento de regras | Microsoft Docs
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
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], diagnostic handling rules
- SQLGetDiagRec function [ODBC], diagnostic handling rules
- diagnostic information [ODBC], SqlGetDiagRec
ms.assetid: 74387c3a-d6b3-4c35-b209-b9612602b20a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dea78f0cc67c7eeeb4f18cbdee4fcb9e4ac757f6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="diagnostic-handling-rules"></a>Regras de manipulação de diagnóstico
As regras a seguir controlam a manipulação de diagnóstica no **SQLGetDiagRec** e **SQLGetDiagField**.  
  
 Para todos os componentes ODBC:  
  
-   Não substituir, alter ou máscara erros ou avisos recebidos de outro componente do ODBC.  
  
-   Pode adicionar um registro de status adicionais quando receber uma mensagem de diagnóstico de outro componente do ODBC. O registro adicionado deve adicionar o valor das informações reais à mensagem original.  
  
 Para o ODBC componente interfaces diretamente de uma fonte de dados:  
  
-   Necessário prefixar seu identificador de fornecedor, o seu identificador de componente e o identificador da fonte de dados para a mensagem de diagnóstica recebida da fonte de dados.  
  
-   Deve preservar o código de erro nativo da fonte de dados.  
  
-   Deve preservar a mensagem de diagnóstico da fonte de dados.  
  
 Para qualquer componente do ODBC que gera um erro ou aviso, independentemente da fonte de dados:  
  
-   Forneça o SQLSTATE correto para o erro ou aviso.  
  
-   Deve gerar o texto da mensagem de diagnóstico.  
  
-   Necessário prefixar seu identificador de fornecedor e seu identificador de componente para a mensagem de diagnóstica.  
  
-   Deve retornar um código de erro nativo, se um estiver disponível e significativo.  
  
 Para o componente ODBC que interage com o Gerenciador de Driver:  
  
-   Os argumentos de saída deve ser inicializado **SQLGetDiagRec** e **SQLGetDiagField**.  
  
-   Formate e retornar as informações de diagnóstico como argumentos de saída **SQLGetDiagRec** e **SQLGetDiagField** quando essa função é chamada.  
  
 Para um componente ODBC que não seja o Gerenciador de Driver:  
  
-   Configure o SQLSTATE com base no erro nativo. Para drivers baseados em arquivo e os drivers baseados em DBMS que não usam um gateway, o driver deve definir o SQLSTATE. Para drivers baseados em DBMS que usam um gateway, o driver ou um gateway que ofereça suporte a ODBC pode definir o SQLSTATE.
