---
title: Indicadores | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- SQL Server Native Client OLE DB provider, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
ms.assetid: 7d9076f2-bf9c-452e-b816-70371a0c1644
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c764e39fe336d85c9b4fd94294bf20a97fb3edaa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="bookmarks"></a>Indicadores
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Os indicadores permitem que os consumidores voltem rapidamente para uma linha. Com os indicadores, os consumidores podem acessar linhas aleatoriamente com base no valor do indicador. A coluna do indicador é a coluna 0 no conjunto de linhas. O consumidor define o valor de campo dwFrag da estrutura associada como DBCOLUMNSINFO_ISBOOKMARK para indicar que a coluna é usada como um indicador. O consumidor também define a propriedade DBPROP_BOOKMARKS do conjunto de linhas como VARIANT_TRUE. Isso permite que a coluna 0 esteja presente no conjunto de linhas. O **irowsetlocate:: Getrowsat** método é usado para buscar linhas, iniciando com a linha especificada como um deslocamento de um indicador.  
  
## <a name="see-also"></a>Consulte também  
 [Conjuntos de linhas](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
