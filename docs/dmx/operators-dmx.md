---
title: Operadores (DMX) | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- operators [DMX]
- DMX [Analysis Services], operators
- Data Mining Extensions [Analysis Services], operators
ms.assetid: e453e570-1ad1-4604-892f-6130308936ac
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 0924501c9bee458ff7c9cc6d9d6e57889621be71
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="operators-dmx"></a>Operadores (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Você pode usar operadores de extensões DMX (Data Mining) para executar a aritmética, comparação, concatenação e operações lógicas em uma consulta em [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 O [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] usa os operadores para executar as seguintes ações:  
  
-   Pesquisa de valores ou objetos que atendem a uma condição específica.  
  
-   Implementar uma decisão entre valores ou expressões.  
  
 O DMX usa várias categorias de operadores, descritas nas seções a seguir. Para obter informações adicionais sobre operadores individuais, consulte [extensões DMX &#40;DMX&#41; referência de operador](../dmx/data-mining-extensions-dmx-operator-reference.md).  
  
|Categoria de operador|Tipo de operação|  
|-----------------------|-----------------------|  
|[Operadores aritméticos &#40;DMX&#41;](../dmx/operators-arithmetic.md)|Realiza adição, subtração, multiplicação ou divisão.|  
|[Operadores de comparação &#40;DMX&#41;](../dmx/operators-comparison.md)|Comparam um valor contra outro valor ou contra uma expressão.|  
|[Operadores lógicos &#40;DMX&#41;](../dmx/operators-logical.md)|Testam a legitimidade de uma condição, como AND, OR ou NOT.|  
|[Operadores unários &#40;DMX&#41;](../dmx/operators-unary.md)|Executam uma operação em um operando único.|  
  
 Use os operadores para combinar expressões menores em DMX em expressões mais complexas. Em expressões complexas, os operadores são avaliados em ordem, com base na definição [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] de prioridade do operador. Os operadores com alta prioridade são executados antes dos operadores com prioridade baixa. Para obter mais informações sobre expressões, consulte [expressões &#40;DMX&#41;](../dmx/expressions-dmx.md).  
  
 Quando expressões simples são combinadas para formar uma expressão complexa, o tipo de dados da expressão resultante é determinado pela combinação das regras para operadores com as regras de prioridade para o tipo de dados. Se o resultado for um caractere ou um valor Unicode, o [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] determinará o agrupamento do resultado pela combinação das regras para os operadores com as regras para prioridade de agrupamento. Há também regras que determinam a precisão, a escala e a extensão do resultado, com base na precisão, na escala e na extensão das expressões simples.  
  
## <a name="see-also"></a>Consulte também  
 [Extensões de mineração de dados & #40; DMX & #41; Referência](../dmx/data-mining-extensions-dmx-reference.md)   
 [Extensões de mineração de dados &#40;DMX&#41; referência de função](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Extensões de mineração de dados & #40; DMX & #41; Referência de instrução](../dmx/data-mining-extensions-dmx-statements.md)   
 [Extensões de mineração de dados &#40;DMX&#41; convenções de sintaxe](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Extensões de mineração de dados &#40;DMX&#41; elementos de sintaxe](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Funções de previsão geral &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Estrutura e o uso de consultas de previsão DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Compreendendo a instrução DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
