---
title: Chamadas de procedimento armazenado de envio em lote | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: dbb2279b3a32fd2929a7e9e626a0481ea38fefd0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="batching-stored-procedure-calls"></a>Processando em lote as chamadas de procedimento armazenado
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client automaticamente processa em lotes chamadas de procedimento armazenado para o servidor quando apropriado. O driver só faz isso quando é usada a sequência de escape de ODBC CALL; não o faz para a instrução EXECUTE [!INCLUDE[tsql](../../includes/tsql-md.md)]. O processamento em lote de chamadas de procedimento armazenado pode reduzir o número de viagens de ida e volta ao servidor e aumentar significativamente o desempenho.  
  
 O driver processa em lote as chamadas de procedimento ao servidor quando você executa um lote que contém várias sequências de escape de ODBC CALL. Também processa em lote as chamadas de procedimento quando matrizes de parâmetro associadas são usadas com uma sequência de escape de ODBC CALL. Por exemplo, se você usar qualquer associação de parâmetro por linha ou ligar uma matriz com cinco elementos aos parâmetros de uma instrução SQL ODBC CALL, quando **SQLExecute** ou **SQLExecDirect** é chamado, o driver envia um único lote com cinco chamadas de procedimento para o servidor.  
  
## <a name="see-also"></a>Consulte também  
 [Executando procedimentos armazenados](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
