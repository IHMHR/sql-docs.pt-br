---
title: Gateway padrão | Microsoft Docs
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
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], gateways
- standard gateways [ODBC]
- gateways [ODBC]
ms.assetid: b8341492-2141-4bab-80bd-f2752223079e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6bcff520d89d9f188292f8d30632a9e05e358efa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="standard-gateway"></a>Gateway padrão
Um *gateway* é um software que faz com que um DBMS para se parecer com o outro. Ou seja, o gateway aceita a interface de programação, a gramática SQL e dados de fluxo de protocolo de um único DBMS e converte-o para a interface de programação, gramática SQL, e protocolo do DBMS oculto. Por exemplo, aplicativos escritos para usar o Microsoft® SQL Server™ também podem acessar dados do DB2 por meio do Gateway de DB2 Micro Decisionware; Este produto faz com que o DB2 para se parecer com o SQL Server. Quando os gateways são usados, um gateway diferente deve ser escrito para cada banco de dados de destino.  
  
 Embora os gateways estão limitados pelas diferenças de arquitetura entre DBMSs, eles são um bom candidato para padronização. No entanto, se todos os DBMSs padronizar a interface de programação, gramática de SQL e dados de fluxo de protocolo de um único DBMS, cujo DBMS é escolhido como o padrão? Certamente nenhum fornecedor DBMS comercial é provavelmente concorda padronizar os produtos. E se uma interface de programação padrão, a gramática de SQL e o protocolo de fluxo de dados são desenvolvidos, nenhum gateway é necessária.
