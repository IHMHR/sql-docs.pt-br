---
title: XML for Analysis (XMLA) referência | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 514e886357fe388a344b7b434bf7042bab5375e7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="xml-for-analysis--xmla-reference"></a>XML for Analysis (XMLA) referência
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] usa o protocolo XML for Analysis (XMLA) para controlar toda a comunicação entre aplicativos cliente e uma instância do Analysis Services. No seu nível mais básico, outras bibliotecas de cliente como o ADOMD.NET e AMO constroem solicitações e decodificam respostas no XMLA, servindo como um intermediário a uma instância do Analysis Services, que usa XMLA exclusivamente.  
  
 Para dar suporte à descoberta e manipulação de dados nos formatos multidimensionais e tabulares, a especificação XMLA define dois métodos geralmente acessíveis, [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) e [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)e um coleção de tipos de dados e elementos XML. Uma vez que o XML permite uma arquitetura de cliente e servidor livremente acoplada, ambos os métodos controlam as informações de entrada e saída no formato XML. O Analysis Services é compatível com a especificação XMLA 1.1, especificação, mas também estende-o para incluir a capacidade de definição e manipulação de dados, implementada como anotações no **Discover** e **Execute** métodos. A sintaxe de XML estendida é chamada de ASSL (Analysis Services Scripting Language). O ASSL baseia-se na especificação de XMLA sem quebrá-la. A interoperabilidade baseada em XMLA é assegurada se você usar somente XMLA, ou XMLA e ASSL juntos.  
  
 Como programador, você poderá usar o XMLA como uma interface de programação se os requisitos de solução especificarem protocolos padrão, como XML, SOAP e HTTP. Os programadores e administradores também podem usar XMLA de maneira ad hoc para recuperar informações dos comandos de servidor ou execução.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Description|  
|-----------|-----------------|  
|[Elementos XML & #40; XMLA & #41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)|Descreve elementos na especificação XMLA.|  
|[Tipos de dados XML &#40;XMLA&#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)|Descreve tipos de dados na especificação XMLA.|  
|[Conformidade XML for Analysis &#40;XMLA&#41;](../../analysis-services/xmla/xml-for-analysis-compliance-xmla.md)|Descreve o nível de conformidade com a especificação do XMLA 1.1.|  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Desenvolvendo com o Analysis Services Scripting Language & #40; ASSL & #41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
  
 [XML for Analysis conjuntos de linhas de esquema](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
 [Desenvolvendo com ADOMD.NET](../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
 [Desenvolvendo com o Analysis Management Objects & #40; AMO & #41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
  
## <a name="see-also"></a>Consulte também  
 [Noções básicas sobre a arquitetura do Microsoft OLAP](../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
