---
title: DELETE (DMX) | Microsoft Docs
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
- DELETE
dev_langs:
- DMX
helpviewer_keywords:
- DELETE statement [DMX]
- mining structures [DMX], clearing
- clearing mining models
- deleting mining models
- mining models [Analysis Services], clearing
- deleting mining structures
ms.assetid: 5a8204c3-a3df-4d97-9c1d-d997d24c70e3
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 4537efcd717b43465e12eadff4d567a179841ed2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="delete-dmx"></a>DELETE (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Limpa um modelo de mineração, uma estrutura de mineração ou uma estrutura de mineração e todos os modelos de mineração associados, dependendo das cláusulas DMX (Data Mining Extensions) usadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
DELETE FROM [MINING MODEL] <model>[.CONTENT]  
DELETE FROM [MINING STRUCTURE] <structure>[.CONTENT]|[.CASES]  
```  
  
## <a name="arguments"></a>Argumentos  
 *modelo*  
 Identificador de modelo.  
  
 *estrutura*  
 Identificador de estrutura.  
  
## <a name="remarks"></a>Remarks  
 Se você não especificar **modelo de MINERAÇÃO** ou **estrutura de MINERAÇÃO**, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] procura o tipo de objeto com base no nome e, em seguida, processa o objeto correto. Se o servidor contiver uma estrutura de mineração e um modelo de mineração com nomes idênticos, um erro será retornado.  
  
 A tabela a seguir descreve o resultado de se usarem as diferentes formas da sintaxe.  
  
|de|Resultado|  
|---------------|------------|  
|DELETE FROM MINING STRUCTURE*\<estrutura >*<br /><br /> ou<br /><br /> DELETE FROM MINING STRUCTURE*\<estrutura >*. CONTEÚDO|Executa ProcessClear na estrutura de mineração. Todo o conteúdo é limpo da estrutura de mineração e de seus modelos de mineração associados.|  
|DELETE FROM MINING STRUCTURE*\<estrutura >*. CASOS|Executa ProcessClearStructureOnly na estrutura de mineração. Todo o conteúdo é limpo da estrutura de mineração, deixando intactos os modelos de mineração associados. O detalhamento dos modelos de mineração associados falhará após a estrutura de mineração ter sido desmarcada.|  
|Excluir de MINING MODEL*\<modelo >*<br /><br /> ou<br /><br /> Excluir de MINING MODEL*\<modelo >*. CONTEÚDO|Executa ProcessClear no modelo de mineração, mas deixa os valores de estado intacto. Os valores de estado consistem nos estados possíveis de uma coluna. Por exemplo, os valores de estado de uma coluna de sexo seriam masculino e feminino.|  
  
 Para obter mais informações sobre tipos de processamento, consulte [tipo de elemento &#40;XMLA&#41;](../analysis-services/xmla/xml-elements-properties/type-element-xmla.md).  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir remove todo o conteúdo do modelo de NB_Sample.  
  
```  
DELETE FROM NB_Sample.CONTENT  
```  
  
## <a name="see-also"></a>Consulte também  
 [Extensões de mineração de dados &#40;DMX&#41; instruções de definição de dados](../dmx/dmx-statements-data-definition.md)   
 [Extensões de mineração de dados &#40;DMX&#41; instruções de manipulação de dados](../dmx/dmx-statements-data-manipulation.md)   
 [Extensões de mineração de dados & #40; DMX & #41; Referência de instrução](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
