---
title: IsLeaf (MDX) | Microsoft Docs
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
- ISLEAF
dev_langs:
- kbMDX
helpviewer_keywords:
- IsLeaf function
ms.assetid: 54862bb3-acc2-4711-ac5a-faa9e9de3721
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: c9ad05f5e3cbde532bd3da76f24df2b7206c74eb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="isleaf-mdx"></a>IsLeaf (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retorna se um membro especificado for um membro folha.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
IsLeaf(Member_Expression)   
```  
  
## <a name="arguments"></a>Argumentos  
 *Member_Expression*  
 Uma linguagem MDX válida que retorna um membro.  
  
## <a name="remarks"></a>Remarks  
 O **IsLeaf** função retorna **true** se o membro especificado for um membro folha. Caso contrário, a função retorna **false**.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir retorna TRUE se [Date].[Fiscal].CurrentMember for um membro folha:  
  
 `WITH MEMBER MEASURES.ISLEAFDEMO AS`  
  
 `IsLeaf([Date].[Fiscal].CURRENTMEMBER)`  
  
 `SELECT {MEASURES.ISLEAFDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Consulte também  
 [Referência de função MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
