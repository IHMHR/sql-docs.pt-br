---
title: Propriedades (MDX) | Microsoft Docs
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
- Properties
dev_langs:
- kbMDX
helpviewer_keywords:
- Properties function
ms.assetid: 2d8442c5-30c4-4fd1-99ea-9845b6533e41
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 17d866d9a98c4ca7cc3fb3ce4586e54ab0439d72
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="properties-mdx"></a>Properties (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retorna uma cadeia de caracteres ou um valor com rigidez de tipos que contém um valor de propriedade do membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Member_Expression.Properties(Property_Name [, TYPED])  
```  
  
## <a name="arguments"></a>Argumentos  
 *Member_Expression*  
 Uma linguagem MDX válida que retorna um membro.  
  
 *Property_Name*  
 Uma expressão de cadeia de caracteres válida de um nome de propriedade de membro.  
  
## <a name="remarks"></a>Remarks  
 O **propriedades** função retorna o valor do membro especificado para a propriedade do membro especificado. A propriedade de membro pode ser qualquer uma das propriedades intrínsecas do membro, como **nome**, **ID**, **chave**, ou **legenda**, ou pode ser uma propriedade do membro definidas pelo usuário. Para obter mais informações, consulte [propriedades intrínsecas do membro &#40;MDX&#41; ](../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md) e [propriedades do membro definidas pelo usuário &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md).  
  
 Por padrão, o valor é forçado a ser uma cadeia de caracteres. Se **TYPED** for especificado, o valor de retorno terá rigidez de tipos.  
  
-   Se o tipo de propriedade for intrínseco, a função retornará o tipo original de membro.  
  
-   Se o tipo de propriedade é definida pelo usuário, o tipo do valor de retorno é o mesmo que o tipo do valor de retorno de **MemberValue** função.  
  
> [!NOTE]  
>  Propriedades ('Key') retornam o mesmo resultado como Key0 com exceção de chaves compostas. Propriedades ('Key') retornarão nulo para chaves compostas. Use a chave*x* sintaxe para chaves compostas, conforme ilustrado no exemplo. Propriedades ('Key0'), Propriedades ('Key1'), Propriedades ('Key2') etc. formam coletivamente a chave composta.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir retorna propriedades de membro intrínsecas e definidas pelo usuário, utilizando o argumento TYPED para retornar o valor com rigidez de tipos para a propriedade de membro Dia Nome.  
  
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
  
SELECT {Measures.MemberName  
   , Measures.MemberVal  
   , Measures.MemberKey  
   , Measures.MemberID  
   , Measures.MemberCaption  
   , Measures.DayName  
   , Measures.DayNameTyped  
   , Measures.DayofWeek  
   , Measures.DayofMonth  
   , Measures.DayofYear  
   }  ON 0  
FROM [Adventure Works]  
```  
  
 O exemplo a seguir mostra o uso da chave*x* propriedade.  
  
```  
WITH   
MEMBER Measures.MemberKey AS   
   [Customer].[Customer Geography].[State-Province].&[QLD]&[AU].Properties('Key')  
MEMBER Measures.MemberKey0 AS   
   [Customer].[Customer Geography].[State-Province].&[QLD]&[AU].Properties('Key0')  
MEMBER Measures.MemberKey1 AS   
   [Customer].[Customer Geography].[State-Province].&[QLD]&[AU].Properties('Key1')  
  
SELECT {Measures.MemberKey  
   , Measures.MemberKey0  
   , Measures.MemberKey1     
   }  ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [Usando propriedades do membro & #40; MDX & #41;](../analysis-services/multidimensional-models/mdx/mdx-member-properties.md)   
 [Referência de função MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
