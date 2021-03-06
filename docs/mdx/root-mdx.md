---
title: Raiz (MDX) | Microsoft Docs
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
- Root
dev_langs:
- kbMDX
helpviewer_keywords:
- Root function
ms.assetid: f6c42e87-5a52-4e43-9dd1-ca757f2db79c
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 5865092286f65e69fed97142dc07fa51c9510446
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="root-mdx"></a>Root (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retorna uma tupla que consiste o **todos os** membros de cada hierarquia de atributo dentro do escopo atual em um cubo, dimensão ou tupla. Para obter mais informações sobre escopo, consulte [instrução SCOPE &#40;MDX&#41;](../mdx/mdx-scripting-scope.md).  
  
> [!NOTE]  
>  Se uma hierarquia de atributo não tem um **todos os** membro, tupla contém o membro padrão para a hierarquia.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Cube syntax  
Root ()  
Dimension syntax  
Root( Dimension_Name )  
Tuple syntax  
Root( Tuple_Expression )  
```  
  
## <a name="arguments"></a>Argumentos  
 *Dimension_Name*  
 Uma expressão de cadeia de caracteres válida que especifica um nome de dimensão.  
  
 *Tuple_Expression*  
 Uma linguagem MDX válida que retorna uma tupla.  
  
## <a name="remarks"></a>Remarks  
 Se nenhum nome de dimensão ou uma expressão de tupla for especificada, o **raiz** função retorna uma tupla que contém o **todos os** membro (ou o membro padrão se o **todos os** membro não existir) de cada hierarquia de atributo no cubo. A ordem dos membros na tupla se baseia na sequência na qual as hierarquias de atributo são definidas no cubo.  
  
 Se um nome de dimensão for especificado, o **raiz** função retorna uma tupla que contém o **todos os** membro (ou o membro padrão se o **todos os** membro não existir) de cada hierarquia de atributo na dimensão especificada com base no contexto do membro atual. A ordem dos membros na tupla se baseia na sequência na qual as hierarquias de atributo são definidas na dimensão.  
  
> [!NOTE]  
>  Se um nome de hierarquia for especificado, o **tupla** função escolherá o nome da dimensão do nome da hierarquia especificada.  
  
 Se uma expressão de tupla for especificada, o **raiz** função retorna uma tupla que contém a interseção da tupla especificada e o **todos os** membros de todos os outros atributos de dimensão não incluídos explicitamente na tupla especificada.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir retorna a tupla que contém o **todos os** membro (ou o padrão se o **todos os** membro não existir) de cada hierarquia no cubo Adventure Works.  
  
```  
SELECT Root()ON 0  
FROM [Adventure Works]  
```  
  
 O exemplo a seguir retorna a tupla que contém o **todos os** membro (ou o padrão se o **todos os** membro não existir) de cada hierarquia na dimensão data no cubo Adventure Works e o valor do membro especificado da dimensão de medidas que faz interseção com esses membros padrão.  
  
```  
SELECT Root([Date]) ON 0  
FROM [Adventure Works]  
WHERE [Measures].[Order Count]  
```  
  
 O exemplo a seguir retorna a tupla que contém o membro da tupla especificado (1º de julho de 2001, junto com o **todos os** membro (ou o padrão se o **todos os** membro não existir) de cada hierarquia não especificada na data dimensão cubo Adventure Works e o valor do membro especificado da dimensão de medidas que faz interseção com esses membros.  
  
```  
SELECT Root([Date].[July 1, 2001]) ON 0  
FROM [Adventure Works]  
WHERE [Measures].[Order Count]  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de função MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
