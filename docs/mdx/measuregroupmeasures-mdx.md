---
title: MeasureGroupMeasures (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- MeasureGroupMeasures function
ms.assetid: 69d9b205-1ca7-4741-9ca9-c7926bc87ead
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: bad3fd8693c2d12cdf4a79801cc7d56ec050971a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="measuregroupmeasures-mdx"></a>MeasureGroupMeasures (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retorna um conjunto de medidas que pertence ao grupo de medidas especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
MEASUREGROUPMEASURES(MeasureGroupName)  
```  
  
## <a name="arguments"></a>Argumentos  
 *MeasureGroupName*  
 Uma expressão de cadeia de caracteres válida que contém o nome do grupo de medidas a partir do qual o conjunto de medidas será recuperado.  
  
## <a name="remarks"></a>Remarks  
 A cadeia de caracteres especificada deve coincidir exatamente com o nome do grupo de medidas. Os colchetes para nomes de grupo de medidas com espaços não são necessários.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir retorna todas as medidas no grupo de medidas Vendas da Internet no cubo Adventure Works.  
  
```  
SELECT MeasureGroupMeasures('Internet Sales') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de função MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
