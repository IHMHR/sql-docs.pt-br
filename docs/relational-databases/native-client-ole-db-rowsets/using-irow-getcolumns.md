---
title: 'Usando IRow:: Getcolumns | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
ms.assetid: 1f5d2e03-e6fe-4ea1-b71d-55d02b5d59ae
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b7b32051a7758b47d1c629ccc77773277d088991
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="using-irowgetcolumns"></a>Usando IRow::GetColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  O **IRow** implementação permite acesso sequencial somente de encaminhamento para as colunas. Você pode acessar todas as colunas na linha com uma única chamada para **IRow:: Getcolumns** ou chame **IRow:: Getcolumns** várias vezes sempre que você acessa várias colunas na linha.  
  
 As várias chamadas para **IRow:: Getcolumns** não devem se sobrepor. Por exemplo, se a primeira chamada para **IRow:: Getcolumns** recupera colunas 1, 2 e 3, a segunda chamada para **IRow:: Getcolumns** deve chamar as colunas 4, 5 e 6. Se chamadas posteriores para **IRow:: Getcolumns** se sobrepõem, o sinalizador de status (campo dwstatus em DBCOLUMNACCESS) é definido como DBSTATUS_E_UNAVAILABLE.  
  
## <a name="see-also"></a>Consulte também  
 [Buscando uma única linha com IRow](../../relational-databases/native-client-ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
