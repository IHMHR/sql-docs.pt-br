---
title: StripCalculatedMembers (MDX) | Microsoft Docs
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
- STRIPCALCULATEDMEMBERS
dev_langs:
- kbMDX
helpviewer_keywords:
- StripCalculatedMembers function
ms.assetid: c71725df-f435-4454-9122-6729ddad8cc7
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 91724b263f658baed8715cf68be0c30d4bbd82c4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="stripcalculatedmembers-mdx"></a>StripCalculatedMembers (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retorna um conjunto gerado, removendo membros calculados de um conjunto especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
StripCalculatedMembers(Set_Expression)   
```  
  
## <a name="arguments"></a>Argumentos  
 *Set_Expression*  
 Uma expressão MDX (Multidimensional Expressions) válida que retorna um conjunto.  
  
## <a name="remarks"></a>Remarks  
 O **StripCalculatedMembers** função remove membros calculados de um conjunto. Membros calculados podem ser adicionados a um conjunto usando o [AddCalculatedMembers](../mdx/addcalculatedmembers-mdx.md) função, que retorna os membros calculados definidos no servidor ou membros calculados que foram adicionados na própria consulta usando a sintaxe WITH MEMBER.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir remove todos os membros calculados da consulta.  
  
```  
WITH MEMBER Measures.MemberName AS   
   [Date].[Calendar].[July 1, 2003].Properties('Name')  
MEMBER Measures.MemberVal AS   
   [Date].[Calendar].[July 1, 2003].Properties('Member_Value')  
MEMBER Measures.MemberKey AS   
   [Date].[Calendar].[July 1, 2003].Properties('Key')  
MEMBER Measures.MemberID AS   
   [Date].[Calendar].[July 1, 2003].Properties('ID')  
MEMBER Measures.MemberCaption AS   
   [Date].[Calendar].[July 1, 2003].Properties('Caption')  
MEMBER Measures.DayName AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day Name', TYPED)  
MEMBER Measures.DayNameTyped AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day Name')  
MEMBER Measures.DayofWeek AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Week')  
MEMBER Measures.DayofMonth AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Month')  
MEMBER Measures.DayofYear AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Year')  
  
SELECT StripCalculatedMembers(  
   { Measures.DefaultMember  
   , Measures.MemberName  
   , Measures.MemberVal  
   , Measures.MemberKey  
   , Measures.MemberID  
   , Measures.MemberCaption  
   , Measures.DayName  
   , Measures.DayNameTyped  
   , Measures.DayofWeek  
   , Measures.DayofMonth  
   , Measures.DayofYear  
   }  
   )  ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de função MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
