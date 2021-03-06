---
title: Suporte a tradução no Analysis Services | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 882434c2bd0a194a2ecbe21a62d3b22964b30f09
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="translation-support-in-analysis-services"></a>Suporte a tradução no Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]

  Em um modelo de dados do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , você pode inserir várias traduções de uma legenda ou uma descrição para fornecer cadeias de caracteres específicas da cultura baseadas no LCID. Para modelos multidimensionais, as traduções podem ser adicionadas para o nome do banco de dados, objetos de cubo e objetos de dimensão do banco de dados. Para modelos de tabela, você pode traduzir descrições e legendas de tabela e coluna.  
  
 A definição de uma tradução cria os metadados e legenda traduzida dentro do modelo, mas para renderizar cadeias de caracteres localizadas em um aplicativo cliente, você deverá definir a propriedade **Language** no objeto ou passar um parâmetro **Culture** ou **Locale Identifier** na cadeia de conexão (por exemplo, definindo `LocaleIdentifier=1036` para retornar cadeias de caracteres em francês).  
  
 Planeje o uso de **Locale Identifier** se desejar dar suporte a várias traduções simultâneas do mesmo objeto em idiomas diferentes. Definir a propriedade **Language** funciona, mas isso também afeta o processamento e as consultas, o que pode ter consequências indesejadas. Definir **Locale Identifier** é a melhor opção porque ele é usado somente para retornar cadeias de caracteres traduzidas.  
  
 Uma tradução consiste em um identificador de localidade (LCID), uma legenda traduzida para o objeto (por exemplo, a dimensão ou o nome do atributo) e, opcionalmente, uma associação a uma coluna que fornece valores de dados no idioma de destino. Você pode ter várias traduções, mas só pode usar uma para determinada conexão. Não há limite teórico no número de traduções que você pode inserir no modelo, mas cada tradução adiciona complexidade ao teste e todas as traduções devem compartilhar o mesmo agrupamento, então, quando criar a solução, tenha essas restrições naturais em mente.  
  
> [!TIP]  
>  Você pode usar os aplicativos cliente, como o Excel, o Management Studio e o SQL Server Profiler para retornar cadeias de caracteres traduzidas. Consulte [Dicas de globalização e práticas recomendadas &#40;Analysis Services&#41;](../analysis-services/globalization-tips-and-best-practices-analysis-services.md) para obter detalhes.  
  
## <a name="how-to-add-translated-metadata-to-model-in-analysis-services"></a>Como adicionar metadados traduzidos para o modelo no Analysis Services  
 Visite esses links para obter instruções passo a passo:  
  
-   [Traduções em modelos de tabela &#40;Analysis Services&#41;](../analysis-services/tabular-models/translations-in-tabular-models-analysis-services.md)  
  
-   [Traduções em modelos multidimensionais &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)  
  
## <a name="see-also"></a>Consulte também  
 [Cenários de globalização para o Analysis Services](../analysis-services/globalization-scenarios-for-analysis-services.md)   
 [Idiomas e agrupamentos & #40; Analysis Services & #41;](../analysis-services/languages-and-collations-analysis-services.md)   
 [Definir ou alterar o agrupamento de coluna](../relational-databases/collations/set-or-change-the-column-collation.md)   
 [Dicas de globalização e práticas recomendadas & #40; Analysis Services & #41;](../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  
