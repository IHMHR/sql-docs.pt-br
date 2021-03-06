---
title: Definindo e identificando objetos (XMLA) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7b3db6fdcd8d9e6bd604d310f8d7858a4a91180e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="defining-and-identifying-objects-xmla"></a>Definindo e identificando objetos (XMLA)
  Os objetos são identificados nos comandos XMLA (XML for Analysis) pela utilização de identificadores de objeto e de referências de objeto, definidas por elementos da ASSL (Analysis Services Scripting Language) e por comandos XMLA.  
  
## <a name="object-identifiers"></a>Identificadores de objeto  
 Um objeto é identificado usando o identificador exclusivo do objeto conforme definido em uma instância do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Identificadores de objeto podem ser explicitamente especificados ou podem ser determinados pela instância do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] quando o [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cria o objeto. Você pode usar o [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) método para recuperar identificadores de objeto para subsequentes **Discover** ou [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) chamadas de método.  
  
## <a name="object-references"></a>Referências de objeto  
 Vários comandos XMLA, como [excluir](../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md) ou [processo](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md), use uma referência de objeto para fazer referência a um objeto de uma maneira não ambígua. Uma referência de objeto contém o identificador do objeto no qual um comando é executado e os identificadores do objeto de seus ancestrais. Por exemplo, a referência de objeto de uma partição contém o identificador do objeto da partição, além de identificadores de objeto do grupo de medidas, do cubo e do banco de dados pais dessa partição.  
  
## <a name="object-definitions"></a>Definições do objeto  
 O [criar](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md) e [Alter](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) comandos no XMLA criam ou alteram, respectivamente, objetos em um [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instância. As definições para os objetos são representadas por um [ObjectDefinition](../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md) elemento que contém elementos da ASSL. Identificadores de objeto podem ser especificados explicitamente para todos os principais e muitos dos objetos secundários por meio de [ID](../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md) elemento. Se o **ID** elemento não for usado, o [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instância fornece um identificador exclusivo, com uma convenção de nomenclatura que depende do objeto a ser identificado. Para obter mais informações sobre como usar o **criar** e **Alter** comandos para definir objetos, consulte [criando e alterando objetos &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/creating-and-altering-objects-xmla.md).  
  
## <a name="see-also"></a>Consulte também  
 [Elemento de objeto & #40; XMLA & #41;](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)   
 [Elemento ParentObject &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md)   
 [Elemento Source &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)   
 [Elemento de destino & #40; XMLA & #41;](../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)   
 [Desenvolvendo com XMLA no Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
