---
title: PredictVariance (DMX) | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- PredictVariance
dev_langs:
- DMX
helpviewer_keywords:
- PredictVariance function
ms.assetid: 3c535237-083a-4102-bdfe-9f3c929e7b2c
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 6f8aff8d02e787aa598290a040552a3d2e8e1af5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="predictvariance-dmx"></a>PredictVariance (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retorna a variação de uma coluna especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
PredictVariance(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>Aplica-se a  
 Uma coluna escalar.  
  
## <a name="return-type"></a>Tipo de retorno  
 Um valor escalar do tipo especificado pelo  *\<referência de coluna escalar >*.  
  
## <a name="remarks"></a>Remarks  
 Se a referência de coluna for discreta, **PredictVariance** retornará 0 porque a variação não pode ser calculada a partir de valores discretos.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir usa uma associação de previsão natural para determinar se um indivíduo é provavelmente um comprador de bicicletas, com base no modelo de mineração da TM da árvore de decisão, e determina também a variação da previsão.  
  
```  
SELECT  
  [Bike Buyer],  
  PredictVariance([Bike Buyer]) AS [Variance]  
FROM  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>Consulte também  
 [Extensões de mineração de dados &#40;DMX&#41; referência de função](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funções &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Funções de previsão geral &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
