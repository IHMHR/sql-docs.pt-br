---
title: Elemento SessionID (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ebda55754f2a6613c3f69347d2ad418796dd4358
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="sessionid-element-xmla"></a>Elemento SessionID (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Identifica uma sessão ativa na qual executar o elemento pai [Cancel](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
  
<Cancel>  
   ...  
   <SessionID>...</SessionID>  
   ...  
</Cancel>  
```  
  
## <a name="element-characteristics"></a>Características do elemento  
  
|Característica|Descrição|  
|--------------------|-----------------|  
|Comprimento e tipo de dados|String|  
|Valor padrão|Nenhuma|  
|Cardinalidade|0-1: elemento obrigatório que pode ocorrer apenas uma vez.|  
  
## <a name="element-relationships"></a>Relações do elemento  
  
|Relação|Elemento|  
|------------------|-------------|  
|Elementos pai|[Cancelar](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)|  
|Elementos filho|Nenhuma|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [Elemento CancelAssociated & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/cancelassociated-element-xmla.md)   
 [Elemento ConnectionID & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md)   
 [Elemento SPID & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md)   
 [Propriedades & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
