---
title: Item (membro) (MDX) | Microsoft Docs
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
f1_keywords:
- ITEM
dev_langs:
- kbMDX
helpviewer_keywords:
- Item function
ms.assetid: 71cca249-910b-4ecd-9097-1a17b224e219
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 48944238630565e6a8655cb10a3f6c7d8adddbdf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="item-member-mdx"></a>Item (Membro) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retorna um membro de uma tupla especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Tuple_Expression.Item( Index )  
```  
  
## <a name="arguments"></a>Argumentos  
 *Tuple_Expression*  
 Uma linguagem MDX válida que retorna uma tupla.  
  
 *Index*  
 Uma expressão numérica válida que especifica o membro específico através da posição dentro da tupla a ser retornada.  
  
## <a name="remarks"></a>Remarks  
 O **Item** função retorna um membro da tupla especificada. A função retorna o membro encontrado na posição de base zero especificada por *índice*.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir retorna o membro `[2003]` - o primeiro item na tupla `[Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).` - nas colunas :  
  
 `SELECT`  
  
 `{( [Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).Item(0)} ON 0`  
  
 `,{[Measures].[Reseller Sales Amount]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Consulte também  
 [Referência de função MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
