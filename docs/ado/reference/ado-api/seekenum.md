---
title: SeekEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SeekEnum
helpviewer_keywords:
- SeekEnum enumeration [ADO]
ms.assetid: f0ec0c92-8253-47c6-9a14-e5dbccbad219
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0fcf7dabb3c12f7919c317c7ecabeaf51995fe85
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="seekenum"></a>SeekEnum
Especifica o tipo de [busca](../../../ado/reference/ado-api/seek-method.md) para executar.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adSeekFirstEQ**|1|Procura a primeira chave igual a *KeyValues*.|  
|**adSeekLastEQ**|2|Busca a última chave igual a *KeyValues*.|  
|**adSeekAfterEQ**|4|Procura uma chave igual a *KeyValues* ou depois que teria ocorrido correspondentes.|  
|**adSeekAfter**|8|Procura uma chave depois de onde uma correspondência com *KeyValues* teria ocorrido.|  
|**adSeekBeforeEQ**|16|Procura uma chave igual a *KeyValues*ou antes que teria ocorrido correspondentes.|  
|**adSeekBefore**|32|Buscas imediatamente antes de uma chave quando uma correspondência com *KeyValues* teria ocorrido.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Pacote: **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.Seek.FIRSTEQ|  
|AdoEnums.Seek.LASTEQ|  
|AdoEnums.Seek.AFTEREQ|  
|AdoEnums.Seek.AFTER|  
|AdoEnums.Seek.BEFOREEQ|  
|AdoEnums.Seek.BEFORE|  
  
## <a name="applies-to"></a>Aplica-se a  
 [Método Seek](../../../ado/reference/ado-api/seek-method.md)
