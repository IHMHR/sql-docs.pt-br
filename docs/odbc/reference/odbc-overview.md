---
title: Visão geral do ODBC | Microsoft Docs
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
- ODBC [ODBC]
- ODBC [ODBC], about ODBC
ms.assetid: 233315bd-2b7f-4b20-9978-e920e1ea9a07
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 39ab7586ebc1cd63d028caab0d3c2f09b82c7172
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-overview"></a>Visão geral do ODBC
Conectividade de banco de dados aberto (ODBC) é uma interface de programação de aplicativo amplamente aceito (API) para acesso ao banco de dados. Ele é baseado nas especificações do Open Group e ISO/IEC Interface de nível de chamada (CLI) para o banco de dados APIs e usa a linguagem SQL (Structured Query) como sua linguagem de acesso de banco de dados.  
  
 ODBC é projetado para máximo *interoperabilidade* -ou seja, a capacidade de um único aplicativo para acessar os sistemas de gerenciamento de outro banco de dados (DBMSs) com o mesmo código-fonte. Aplicativos de banco de dados chamam funções na interface do ODBC, que são implementadas em módulos específicos ao banco de dados chamados *drivers*. O uso de drivers isola os aplicativos de chamadas de banco de dados específicos da mesma forma que os drivers de impressora isolar programas de processamento de texto de comandos específicos da impressora. Como drivers são carregados em tempo de execução, um usuário só precisa adicionar um novo driver para acessar um DBMS novo; não é necessário recompilar ou vincular novamente o aplicativo.  
  
 Esta seção contém os tópicos a seguir.  
  
-   [Por que o ODBC foi criado?](../../odbc/reference/why-was-odbc-created.md)  
  
-   [O que é o ODBC?](../../odbc/reference/what-is-odbc.md)  
  
-   [ODBC e a CLI padrão](../../odbc/reference/odbc-and-the-standard-cli.md)
