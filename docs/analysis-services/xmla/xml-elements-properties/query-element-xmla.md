---
title: Consultar o elemento (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9670f46123a80c4cb14b4439a7a296adc0973353
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="query-element-xmla"></a>Elemento Query (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contém uma consulta dentro de [consultas](../../../analysis-services/xmla/xml-elements-properties/queries-element-xmla.md) coleção usada pelo [DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md) comando durante a otimização baseada em uso.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
  
<Queries>  
   ...  
   <Query>...</Query>  
   ...  
</Queries>  
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
|Elementos pai|[Consultas](../../../analysis-services/xmla/xml-elements-properties/queries-element-xmla.md)|  
|Elementos filho|Nenhuma|  
  
## <a name="remarks"></a>Remarks  
 O comando **DesignAggregations** oferece suporte para a otimização baseada em uso incluindo um ou mais elementos **Query** na coleção **Queries** do comando. Cada elemento **Query** representa uma meta de consulta usada pelo processo de design para definir agregações que se destinam às consultas usadas com mais frequência. Você pode especificar suas próprias metas ou usar as informações armazenadas por uma instância do [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] no log de consultas para recuperar informações sobre as consultas usadas com mais frequência.  
  
 Se você estiver criando agregações iterativamente, você só precisa transmitir as metas de consulta no primeiro **DesignAggregations** o comando porque a [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instância armazena essas metas e utiliza essas consultas durante subsequentes **DesignAggregations** comandos. Após transmitir as metas de consulta no primeiro comando **DesignAggregations** de um processo iterativo, qualquer comando **DesignAggregations** subsequente que contém metas de consulta na propriedade **Queries** gerará um erro.  
  
 O elemento **Query** contém um valor delimitado por vírgula com os seguintes argumentos:  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *Frequência*  
 Um fator de ponderação que corresponde ao número de vezes que a consulta foi executada previamente. Se o elemento **Query** representa uma nova consulta, o valor *Frequency* representa o fator de ponderação usado pelo processo de design para avaliar a consulta. À medida que o valor de frequência fica maior, o peso colocado na consulta durante processo de design aumenta.  
  
 *Conjunto de dados*  
 Uma sequência numérica que especifica quais atributos de uma dimensão devem ser incluídos na consulta. Essa sequência deve ter o mesmo número de caracteres do número de atributos na dimensão. Zero (0) indica que o atributo na posição ordinal especificada não está incluído na consulta para a dimensão especificada e um (1) indica que o atributo na posição ordinal especificada está incluído na consulta para a dimensão especificada.  
  
 Por exemplo, a sequência “011” faz referência a uma consulta que envolve uma dimensão com três atributos, dos quais o segundo e o terceiro estão incluídos na consulta.  
  
> [!NOTE]  
>  Alguns atributos não são considerados no conjunto de dados. Para obter mais informações sobre os atributos excluídos, consulte [Properties (XMLA)](../../../analysis-services/xmla/xml-elements-properties/query-element-xmla.md).  
  
 Cada dimensão no grupo de medidas que contém o design de agregação é representado por um valor *Dataset* no elemento **Query** . A ordem de valores *Dataset* deve coincidir com a ordem de dimensões incluída no grupo de medidas.  
  
## <a name="see-also"></a>Consulte também  
 [Projetando agregações & #40; XMLA & #41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/designing-aggregations-xmla.md)   
 [Propriedades & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
