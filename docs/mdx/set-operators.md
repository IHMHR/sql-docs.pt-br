---
title: Operadores de conjunto | Microsoft Docs
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
- set operators [MDX]
ms.assetid: 83500d2e-44b3-49eb-a221-3ce5a58277a5
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 161234bf6f72beb7548cfb5dc7ad3602f4903110
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="set-operators"></a>Operadores de conjunto
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Na linguagem MDX, os operadores de conjunto executam operações em membros ou conjuntos e retornam um conjunto. Frequentemente você usa os operadores de conjunto como uma alternativa para várias funções de conjunto na linguagem MDX.  
  
 O MDX oferece suporte a operadores de conjunto listados na tabela a seguir.  
  
|Operador|Description|  
|--------------|-----------------|  
|[- (Exceto)](../mdx/except-mdx-operator.md)|Retorna a diferença entre dois conjuntos, removendo membros duplicados.<br /><br /> Esse operador é funcionalmente equivalente ao [exceto](../mdx/except-mdx-function.md) função.|  
|[* (Produto cruzado)](../mdx/crossjoin-mdx-operator-reference.md)|Retorna o produto cruzado de dois conjuntos.<br /><br /> Esse operador é funcionalmente equivalente ao [Crossjoin](../mdx/crossjoin-mdx.md) função.|  
|[: (Intervalo)](../mdx/range-mdx.md)|Retorna um conjunto ordenado naturalmente, com dois membros especificados como pontos de extremidade, e todos os membros entre os dois membros especificados incluídos como membros do conjunto.|  
|[+ (União)](../mdx/union-mdx-operator-reference.md)|Retorna uma união de dois conjuntos, exceto membros duplicados.<br /><br /> Esse operador é funcionalmente equivalente ao [união &#40;MDX&#41; ](../mdx/union-mdx.md) função.|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de função MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)   
 [Referência de operador MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Operadores &#40;sintaxe MDX&#41;](../mdx/operators-mdx-syntax.md)  
  
  
