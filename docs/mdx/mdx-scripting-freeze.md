---
title: Instrução FREEZE (MDX) | Microsoft Docs
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
- FREEZE
dev_langs:
- kbMDX
helpviewer_keywords:
- FREEZE statement
- locking cell values [MDX]
ms.assetid: 59f1e860-6f37-41af-97d6-7708bdaac933
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: f122428b224f22dfd1899a77787ec86e65314280
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-scripting---freeze"></a>Script MDX - CONGELAR
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Bloqueia os valores de célula de um subcubo especificado para seus valores atuais. Quando os valores de célula são bloqueados, as alterações nas outras células não têm nenhum efeito nas células que estão bloqueadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
FREEZE Subcube_Expression   
```  
  
## <a name="arguments"></a>Argumentos  
 *Subcube_Expression*  
 Uma linguagem MDX válida que retorna um subcubo.  
  
## <a name="remarks"></a>Remarks  
 O **CONGELAR** instrução bloqueia os valores de células em um subcubo especificado, impedindo que instruções subsequentes no MDX script alterem seus valores em cálculo subsequente passa.  
  
 No exemplo a seguir, A e B representam subcubos em um script de cálculo MDX:  
  
```  
B = 2;  
A = B;  
B = 3  
```  
  
 Nesse momento, A e B são iguais a 3.  
  
 Agora podemos inserir a **congelar** função para bloquear as células no subcubo:  
  
```  
B = 2;  
A = B;  
FREEZE(A);  
B = 3  
```  
  
 Agora, A é igual a 2 e B é igual a 3.  
  
## <a name="see-also"></a>Consulte também  
 [Instruções de script MDX & #40; MDX & #41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
