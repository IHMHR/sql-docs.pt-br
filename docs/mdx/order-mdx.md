---
title: Ordem (MDX) | Microsoft Docs
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
- ORDER
dev_langs:
- kbMDX
helpviewer_keywords:
- Order function
ms.assetid: 84acff52-2443-4424-a09e-694e6f14c109
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: bfb3e7e9aba3b60df80d599a8f7443b91c7b7b6e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="order-mdx"></a>Order (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Organiza membros de um conjunto especificado, preservando opcionalmente ou quebrando a hierarquia.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Numeric expression syntax  
Order(Set_Expression, Numeric_Expression   
[ , { ASC | DESC | BASC | BDESC } ] )  
  
String expression syntax  
Order(Set_Expression, String_Expression   
[ , { ASC | DESC | BASC | BDESC } ] )  
  
```  
  
## <a name="arguments"></a>Argumentos  
 *Set_Expression*  
 Uma expressão MDX (Multidimensional Expressions) válida que retorna um conjunto.  
  
 *Numeric_Expression*  
 Uma expressão numérica válida, geralmente uma linguagem MDX de coordenadas de célula, que retorna um número.  
  
 *String_Expression*  
 Uma expressão de cadeia de caracteres válida, geralmente uma expressão MDX válida de coordenadas de célula, que retorna um número expresso como uma cadeia de caracteres.  
  
## <a name="remarks"></a>Remarks  
 O **ordem** função pode ser hierárquica (conforme especificado por meio a **ASC** ou **DESC** sinalizador) ou não hierárquico (conforme especificado por meio de **BASC** ou **BDESC** sinalizador; o **B** significa "quebra de hierarquia"). Se **ASC** ou **DESC** for especificado, o **ordem** função primeiro organizará os membros de acordo com sua posição na hierarquia e, em seguida, ordenará cada nível. Se **BASC** ou **BDESC** for especificado, o **ordem** função organiza os membros do conjunto independentemente da hierarquia. Nenhum sinalizador for especificado, **ASC** é o padrão.  
  
 Se o **ordem** função é usada com um conjunto onde duas ou mais hierarquias são interjuntadas e o **DESC** sinalizador for usado, somente os membros da última hierarquia no conjunto são ordenados. Esta é uma alteração do Analysis Services 2000 onde foram ordenadas todas as hierarquias no conjunto.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir retorna, do **Adventure Works** de cubo, o número de pedidos do revendedor para todos os trimestres do calendário da hierarquia de calendário na dimensão Data. O **ordem** função reordena o conjunto para o eixo de linhas. O **ordem** função ordena o conjunto por `[Reseller Order Count]` em ordem hierárquica descendente conforme determinado pelo `[Calendar]` hierarquia.  
  
 `SELECT`  
  
 `Measures.[Reseller Order Count] ON COLUMNS,`  
  
 `Order(`  
  
 `[Date].[Calendar].[Calendar Quarter].MEMBERS`  
  
 `,Measures.[Reseller Order Count]`  
  
 `,DESC`  
  
 `) ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Observe como neste exemplo, quando o **DESC** sinalizador é alterado para **BDESC**, a hierarquia é interrompida e a lista de trimestres do calendário é retornada sem consideração para a hierarquia:  
  
 `SELECT`  
  
 `Measures.[Reseller Order Count] ON COLUMNS,`  
  
 `Order(`  
  
 `[Date].[Calendar].[Calendar Quarter].MEMBERS`  
  
 `,Measures.[Reseller Order Count]`  
  
 `,BDESC`  
  
 `) ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 O exemplo a seguir retorna a medida Valor das Vendas do Revendedor para as cinco subcategorias principais de vendas dos produtos, independentemente da hierarquia, com base no Lucro Bruto do Revendedor. O **subconjunto** função é usada para retornar somente as 5 primeiras tuplas no conjunto de após o resultado é ordenado com a **ordem** função.  
  
 `SELECT Subset`  
  
 `(Order`  
  
 `([Product].[Product Categories].[SubCategory].members`  
  
 `,[Measures].[Reseller Gross Profit]`  
  
 `,BDESC`  
  
 `)`  
  
 `,0`  
  
 `,5`  
  
 `) ON 0`  
  
 `FROM [Adventure Works]`  
  
 O exemplo a seguir usa o **classificação** função para classificar os membros da hierarquia cidade com base na medida do valor de vendas de revendedor e, em seguida, exibe-os na ordem de classificação. Usando o **ordem** funcionar para organizar pela primeira vez o conjunto de membros da hierarquia cidade, a classificação é feita apenas uma vez e, em seguida, seguida por uma verificação linear antes de ser apresentada na ordem de classificação.  
  
```  
WITH   
SET OrderedCities AS Order  
   ([Geography].[City].[City].members  
   , [Measures].[Reseller Sales Amount], BDESC  
   )  
MEMBER [Measures].[City Rank] AS Rank  
   ([Geography].[City].CurrentMember, OrderedCities)  
SELECT {[Measures].[City Rank],[Measures].[Reseller Sales Amount]}  ON 0   
,Order  
   ([Geography].[City].[City].MEMBERS  
   ,[City Rank], ASC)  
    ON 1  
FROM [Adventure Works]  
```  
  
 O exemplo a seguir retorna o número de produtos no conjunto que são exclusivos, usando o **ordem** função para solicitar as tuplas não vazias antes de utilizar o **filtro** função. O **CurrentOrdinal** função é usada para comparar e eliminar associações.  
  
```  
WITH MEMBER [Measures].[PrdTies] AS Count  
   (Filter  
      (Order  
        (NonEmpty  
          ([Product].[Product].[Product].Members  
          , {[Measures].[Reseller Order Quantity]}  
          )  
       , [Measures].[Reseller Order Quantity]  
       , BDESC  
       ) AS OrdPrds  
    , (OrdPrds.CurrentOrdinal < OrdPrds.Count   
       AND [Measures].[Reseller Order Quantity] =   
          ( [Measures].[Reseller Order Quantity]  
            , OrdPrds.Item  
               (OrdPrds.CurrentOrdinal  
               )  
            )  
         )  
         OR (OrdPrds.CurrentOrdinal > 1   
            AND [Measures].[Reseller Order Quantity] =   
               ([Measures].[Reseller Order Quantity]  
               , OrdPrds.Item  
                  (OrdPrds.CurrentOrdinal-2)  
                )  
             )  
          )  
       )  
SELECT {[Measures].[PrdTies]} ON 0  
FROM [Adventure Works]  
```  
  
 Para entender como o **DESC** sinalizador funciona com conjuntos de tuplas, primeiro considere os resultados da consulta a seguir:  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
,[Measures].[Tax Amount], DESC)  
ON 1  
FROM [Adventure Works]  
  
```  
  
 No eixo de Linhas, você pode consultar que os Sales Territory Groups foram colocados em ordem decrescente por Tax Amount, como segue: North America, Europe, Pacific, NA. Agora veja o que acontece se nós interjuntarmos o conjunto de grupos de território de vendas com o conjunto de subcategorias de produtos e aplicar o **ordem** funcionam da mesma forma, da seguinte maneira:  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
*  
{[Product].[Product Categories].[subCategory].Members}  
,[Measures].[Tax Amount], DESC)  
ON 1  
FROM [Adventure Works]  
  
```  
  
 Enquanto o conjunto de Product Subcategories foi colocado em ordem decrescente e hierárquica, os Sales Territory Groups agora não são classificados e aparecem na ordem que eles aparecem na hierarquia: Europe, NA, North America e Pacific. Isto é porque somente a última hierarquia no conjunto de tuplas, Product Subcategories, é classificado. Para reproduzir o comportamento do Analysis Services 2000, use uma série de aninhados **gerar** funções para classificar cada conjunto antes de interjuntar, por exemplo:  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
GENERATE(  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
,[Measures].[Tax Amount], DESC)  
,  
ORDER(  
[Sales Territory].[Sales Territory].CURRENTMEMBER  
*  
{[Product].[Product Categories].[subCategory].Members}  
,[Measures].[Tax Amount], DESC))  
ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de função MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
