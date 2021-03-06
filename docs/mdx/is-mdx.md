---
title: É (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- IS
dev_langs:
- kbMDX
helpviewer_keywords:
- IS operator
ms.assetid: dc8c0b91-3bb1-49e5-8d70-57545baaa8e0
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: a4422a686a35799c210f81d5e60fa44ca3c5aeae
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="is-mdx"></a>IS (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Executa uma comparação lógica em duas expressões de objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Expression1 IS ( Expression2 | NULL )  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *Expression1*  
 Uma expressão MDX (Multidimensional Expressions) válida que retorna uma referência de objeto MDX.  
  
 *Expression2*  
 Uma expressão MDX válida que retorna uma referência de objeto MDX.  
  
## <a name="return-value"></a>Valor de retorno  
 Um valor booliano que retorna **true** se ambos os argumentos se referem ao mesmo objeto; caso contrário, **false**. Se o **nulo** palavra-chave for especificado, o operador retornará **true** se *Expression1* é **nulo**; caso contrário, **false**.  
  
## <a name="remarks"></a>Remarks  
 O **IS** operador geralmente é usado para determinar se tuplas e membros são idempotentes, o que significa que eles são precisamente equivalentes.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir mostra como usar o **IS** operador para verificar se o membro atual em um eixo é um membro específico:  
  
 `With`  
  
 `//Returns TRUE if the currentmember is Bikes`  
  
 `Member [Measures].[IsBikes?] AS`  
  
 `[Product].[Category].CurrentMember IS [Product].[Category].&[1]`  
  
 `SELECT`  
  
 `{[Measures].[IsBikes?]} ON 0,`  
  
 `[Product].[Category].[Category].Members ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
## <a name="see-also"></a>Consulte também  
 [Referência de operador MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
