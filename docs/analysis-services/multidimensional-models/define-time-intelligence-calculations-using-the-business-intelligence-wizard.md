---
title: Definir cálculos de inteligência de tempo usando o Assistente de Business Intelligence | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2d3659fd80d09f5f0b5ec17301606b23810df3fe
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="define-time-intelligence-calculations-using-the-business-intelligence-wizard"></a>Definir cálculos de inteligência de tempo com o Assistente de Business Intelligence
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  O aprimoramento de inteligência de tempo é um aprimoramento de cubo que adiciona cálculos de tempo (ou exibições de tempo) a uma hierarquia selecionada. Esse aprimoramento oferece suporte às seguintes categorias de cálculos:  
  
-   Período até a data.  
  
-   Crescimento de período sobre período.  
  
-   Médias móveis.  
  
-   Comparações de período paralelas.  
  
 Você aplica a inteligência de tempo a cubos que têm uma dimensão de tempo. (Uma dimensão de tempo é uma dimensão cuja propriedade **Type** está definida como **Time**.) Além disso, os atributos de tempo da dimensão também devem ter a configuração apropriada (como Anos ou Meses) para a propriedade **Type** . A propriedade **Type** de ambas as dimensões e seus atributos será configurada corretamente se você usar o Assistente para Dimensões para criar a dimensão de tempo.  
  
 Para adicionar inteligência de tempo a um cubo, use o Assistente de Business Intelligence e selecione a opção **Definir inteligência de tempo** na página **Escolher Aprimoramento** . Esse assistente orientará você durante as etapas para selecionar a hierarquia à qual você deseja adicionar a inteligência de tempo e especificar quais membros da hierarquia terão a inteligência de tempo aplicada a eles. Na última página do assistente, você verá as alterações que serão feitas ao banco de dados do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] para adicionar a inteligência de tempo selecionada.  
  
## <a name="selecting-a-time-hierarchy"></a>Selecionando uma hierarquia de tempo  
 Na página **Escolher Cálculos e Hierarquia de Destino** , selecione a hierarquia de tempo à qual será aplicado o aprimoramento de tempo. Você pode aplicar o aprimoramento de tempo somente a uma hierarquia sempre que executar o Assistente de Business Intelligence. Para aplicar o aprimoramento a mais de uma hierarquia de tempo, execute o assistente novamente.  
  
 Depois de selecionar uma hierarquia de tempo, na lista **Cálculos de tempo disponíveis** , selecione os cálculos que se aplicam à hierarquia. Os cálculos listados dependem dos níveis da hierarquia e da configuração da propriedade **Type** de cada nível. Por exemplo, uma hierarquia Anos aceita Desde o Início do Ano e Crescimento Ano a Ano, mas não a hierarquia Trimestres.  
  
> [!NOTE]  
>  O arquivo de modelo Timeintelligence.xml define os cálculos de tempo listados em **Cálculos de tempo disponíveis**. Se os cálculos listados não satisfizerem suas necessidades, você pode alterar os cálculos existentes ou adicionar novos cálculos ao arquivo Timeintelligence.xml.  
  
> [!TIP]  
>  Para exibir uma descrição para um cálculo, use as setas para cima e para baixo para realçar esse cálculo.  
  
## <a name="apply-time-views-to-members"></a>Aplicar exibições de tempo aos membros  
 Na página **Definir Escopo de Cálculos** , especifique os membros aos quais se aplicam as novas exibições de tempo. Você pode aplicar as novas exibições de tempo a um destes objetos:  
  
-   **Membros de uma dimensão de contas** Na página **Definir Escopo de Cálculos** , a lista **Medidas disponíveis** contém dimensões de contas. As dimensões de contas têm suas propriedades **Type** definidas como **Account**. Se houver dimensões de contas mas elas não aparecerem na lista **Medidas disponíveis** , você poderá usar o Assistente de Business Intelligence para aplicar a inteligência de conta a essa dimensão. Para obter mais informações, consulte [Adicionar inteligência de conta a uma dimensão](../../analysis-services/multidimensional-models/bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
-   **Medidas** Em vez de especificar uma dimensão de contas, você pode especificar as medidas às quais se aplicam as exibições de tempo. Nesse caso, selecione as exibições às quais se aplicam os cálculos de tempo. Por exemplo, ativos e passivos são dados acumulados no ano; portanto, você não aplica um cálculo Desde o Início do Ano a medidas de ativos e passivos.  
  
## <a name="viewing-the-time-intelligence-enhancement"></a>Exibindo o aprimoramento de inteligência de tempo  
 Na última página do Assistente de Business Intelligence, é possível exibir as alterações que serão feitas no banco de dados do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Para um aprimoramento de inteligência de tempo, o assistente mudará a dimensão de tempo selecionada, a exibição da fonte de dados associada e o cubo associado conforme descrito na tabela a seguir.  
  
|Objeto|Alterar|  
|------------|------------|  
|Dimensão de tempo|Adicionar um atributo para cada cálculo (ou exibição).|  
|Exibição da fonte de dados|Adiciona uma coluna calculada à tabela de tempo para cada novo atributo da dimensão de tempo.|  
|Cube|Adiciona um membro calculado que define o código MDX para executar o cálculo.|  
  
## <a name="see-also"></a>Consulte também  
 [Criar membros calculados](../../analysis-services/multidimensional-models/create-calculated-members.md)  
  
  
