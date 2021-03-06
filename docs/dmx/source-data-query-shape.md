---
title: FORMA (DMX) | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SHAPE
dev_langs:
- DMX
helpviewer_keywords:
- SHAPE statement
- multiple data sources
ms.assetid: b9526ec2-40bc-4bf5-b4e5-774f71075065
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 0c31d8d4725d90200f7f2811f974ffd9b98bcaa2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsource-data-querygt---shape"></a>&lt;consulta de fonte de dados&gt; -forma
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Combina consultas de várias fontes de dados em uma tabela hierárquica única (ou seja, uma tabela com tabelas aninhadas), que se torna a tabela de caso do modelo de mineração.  
  
 A sintaxe completa do **forma** comando está documentado no [!INCLUDE[msCoName](../includes/msconame-md.md)] Data Access Components (MDAC) Software Development Kit (SDK).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
SHAPE {<master query>}  
APPEND ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS <column table name>  
[  
     ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS < column table name>  
...  
]       
```  
  
## <a name="arguments"></a>Argumentos  
 *consulta mestre*  
 Consulta que retorna a tabela pai.  
  
 *consulta de tabela filho*  
 Consulta que retorna a tabela aninhada.  
  
 *coluna mestre*  
 Coluna da tabela pai para identificar linhas filho no resultado de uma consulta de tabela filho.  
  
 *coluna filho*  
 Coluna da tabela filho para identificar linhas pai no resultado de uma consulta mestre.  
  
 *nome da coluna de tabela*  
 Nome de coluna recentemente adicionada à tabela pai da tabela aninhada.  
  
## <a name="remarks"></a>Remarks  
 É preciso classificar as consultas pela coluna que relaciona a tabela pai à tabela filho.  
  
## <a name="examples"></a>Exemplos  
 Você pode usar o exemplo a seguir em um [INSERT INTO &#40;DMX&#41; ](../dmx/insert-into-dmx.md) instrução para treinar um modelo que contém uma tabela aninhada. As duas tabelas dentro a **forma** instrução são relacionadas por meio de **OrderNumber** coluna.  
  
```  
SHAPE {  
    OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber  
    FROM vAssocSeqOrders ORDER BY OrderNumber')  
} APPEND (  
    {OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber, model FROM   
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}  
  RELATE OrderNumber to OrderNumber)   
```  
  
## <a name="see-also"></a>Consulte também  
 [&#60;consulta de fonte de dados&#62;](../dmx/source-data-query.md)   
 [Extensões de mineração de dados &#40;DMX&#41; instruções de definição de dados](../dmx/dmx-statements-data-definition.md)   
 [Extensões de mineração de dados &#40;DMX&#41; instruções de manipulação de dados](../dmx/dmx-statements-data-manipulation.md)   
 [Extensões de mineração de dados & #40; DMX & #41; Referência de instrução](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
