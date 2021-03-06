---
title: Usando o conjunto de expressões | Microsoft Docs
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
dev_langs:
- kbMDX
helpviewer_keywords:
- expressions [MDX], set
- tuples
- set expressions [MDX]
ms.assetid: 88d65872-0cbe-4c95-b36f-e1aa4ac8ed07
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 26ebed881d32bb9d550ae9630ee7b60cb15cd153
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="using-set-expressions"></a>Usando expressões de conjunto
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Um conjunto é composto por uma lista ordenada de nenhuma ou algumas tuplas. Um conjunto que não contém nenhuma tupla é conhecido como um conjunto vazio.  
  
 A expressão completa de um conjunto consiste em nenhuma ou algumas tuplas especificadas explicitamente, entre chaves:  
  
 {[{ *Tuple_expression* | *Member_expression* } [, { *Tuple_expression* | *Member_expression* }]...]}  
  
 As expressões de membro especificadas em uma expressão de conjunto são convertidas em expressões de tupla de um membro.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra duas expressões de conjunto usadas nos eixos Colunas e Linhas de uma consulta:  
  
 `SELECT`  
  
 `{[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]} ON COLUMNS,`  
  
 `{([Product].[Product Categories].[Category].&[4], [Date].[Calendar].[Calendar Year].&[2004]),`  
  
 `([Product].[Product Categories].[Category].&[1], [Date].[Calendar].[Calendar Year].&[2003]),`  
  
 `([Product].[Product Categories].[Category].&[3], [Date].[Calendar].[Calendar Year].&[2004])}`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 No eixo Colunas, o conjunto  
  
 {[Medidas].[Valor das Vendas pela Internet], [Medidas].[Valor do Imposto da Internet]}  
  
 consiste em dois membros da dimensão Medidas. No eixo Linhas, o conjunto  
  
 {([Produto].[Categorias de Produto].[Categoria].&[4], [Data].[Calendário].[Ano Civil].&[2004]),  
  
 ([Produto].[Categorias de Produto].[Categoria].&[1], [Data].[Calendário].[Ano Civil].&[2003]),  
  
 ([Produto].[Categorias de Produto].[Categoria].&[3], [Data].[Calendário].[Ano Civil].&[2004])}  
  
 consiste em três tuplas, cada uma contendo duas referências explícitas aos membros da hierarquia Categorias de Produto da dimensão Produto e da hierarquia Calendário da dimensão Data.  
  
 Para obter exemplos de funções que retornam conjuntos, consulte [trabalhando com membros, tuplas e conjuntos de &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md).  
  
## <a name="see-also"></a>Consulte também  
 [Expressões &#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
