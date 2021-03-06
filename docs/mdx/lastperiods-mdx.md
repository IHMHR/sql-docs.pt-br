---
title: LastPeriods (MDX) | Microsoft Docs
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
- LASTPERIODS
dev_langs:
- kbMDX
helpviewer_keywords:
- LastPeriods function
ms.assetid: a15df7a1-b261-48ed-aacc-d2804db8dbf7
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 35d093cbb4fea7cf02aef5835afc300f8cf74698
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="lastperiods-mdx"></a>LastPeriods (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retorna um conjunto de membros até e inclusive um membro especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
LastPeriods(Index [ ,Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argumentos  
 *Index*  
 Uma expressão numérica válida que especifica vários períodos.  
  
 *Member_Expression*  
 Uma linguagem MDX válida que retorna um membro.  
  
## <a name="remarks"></a>Remarks  
 Se o número especificado de períodos for positivo, o **LastPeriods** retorna um conjunto de membros que começa com o membro defasagem *índice* -1 da expressão de membro especificado e termina com o membro especificado. O número de membros retornados pela função é igual a *índice*.  
  
 Se o número especificado de períodos for negativo, o **LastPeriods** função retorna um conjunto de membros que começa com o membro especificado e termina com o membro que lidera (- *índice* - 1) do membro especificado. O número de membros retornados pela função é igual ao valor absoluto do *índice*.  
  
 Se o número especificado de períodos for zero, o **LastPeriods** função retorna o conjunto vazio. Isso é diferente de **latência** função, que retorna o membro especificado se 0 for especificado.  
  
 Se um membro não for especificado, o **LastPeriods** função usa **Time.CurrentMember**. Se nenhuma dimensão for marcada como uma dimensão Tempo, a função será analisada e executada sem um erro, mas causará um erro de célula no aplicativo cliente.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir retorna o valor de medida padrão durante o segundo, terceiro e quarto trimestres fiscais do ano fiscal 2002.  
  
```  
SELECT LastPeriods(3,[Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002]) ON 0  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  Esse exemplo também pode ser escrito usando o operador : (dois-pontos):  
>   
>  `[Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002]: [Date].[Fiscal].[Fiscal Quarter].[Q2 FY 2002]`  
  
 O exemplo a seguir retorna o valor de medida padrão durante o primeiro trimestre fiscal do ano fiscal 2002. Embora o número especificado de períodos seja três, apenas um pode ser retornado porque não há períodos anteriores no ano fiscal.  
  
```  
SELECT LastPeriods  
   (3,[Date].[Fiscal].[Fiscal Quarter].[Q1 FY 2002]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de função MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
