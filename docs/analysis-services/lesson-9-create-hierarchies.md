---
title: 'Lição 10: Criar hierarquias | Microsoft Docs'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d4c1fc4905c52351b61a4e79b2ff21f47501f337
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="lesson-9-create-hierarchies"></a>Lição 9: Criar hierarquias
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

Nesta lição, você criará hierarquias. Hierarquias são grupos de colunas organizados em níveis; por exemplo, uma hierarquia Geografia poderia ter subníveis para País, Estado, Município e Cidade. As hierarquias podem aparecer separadas de outras colunas em uma lista de campo de aplicativo cliente de relatório, tornando mais fácil para os usuários clientes navegarem e incluírem itens em um relatório. Para obter mais informações, consulte [hierarquias](../analysis-services/tabular-models/hierarchies-ssas-tabular.md).  
  
Para criar hierarquias, você usará o designer de modelo no *exibição de diagrama*. Não há suporte para criar e gerenciar hierarquias na exibição de dados.  
  
Tempo estimado para concluir esta lição: **20 minutos**  
  
## <a name="prerequisites"></a>Pré-requisitos  
Este tópico faz parte de um tutorial de modelo de tabela, que deve ser concluído na ordem. Antes de executar as tarefas nesta lição, você deve ter concluído a lição anterior: [lição 8: criar perspectivas](../analysis-services/lesson-8-create-perspectives.md).  
  
## <a name="create-hierarchies"></a>Criar hierarquias  
  
#### <a name="to-create-a-category-hierarchy-in-the-dimproduct-table"></a>Para criar uma hierarquia de categoria na tabela DimProduct  
  
1.  No designer de modelo (exibição de diagrama), clique com botão direito do **DimProduct** tabela > **criar hierarquia**. A nova hierarquia aparece na parte inferior da janela de tabela. Renomeie a hierarquia **categoria**.  
  
2.  Clique e arraste o **ProductCategoryName** coluna para o novo **categoria** hierarquia.  
  
3.  No **categoria** hierarquia, clique com botão direito do **ProductCategoryName** > **Renomear**e, em seguida, digite **categoria**.  
  
    > [!NOTE]  
    > A renomeação de uma coluna em uma hierarquia não renomeia essa coluna na tabela. Uma coluna em uma hierarquia é apenas uma representação da coluna na tabela.  
  
4.  Clique e arraste o **ProductSubcategoryName** coluna para o **categoria** hierarquia. Renomeie- **subcategoria**. 
  
5.  Clique com botão direito do **ModelName** coluna > **adicionar à hierarquia**e, em seguida, selecione **categoria**. Faça o mesmo para **EnglishProductName**. Renomeie as colunas na hierarquia de **modelo** e **produto**.  

    ![como tabular-lesson9-categoria](../analysis-services/media/as-tabular-lesson9-category.png)
  
#### <a name="to-create-hierarchies-in-the-dimdate-table"></a>Para criar hierarquias na tabela DimDate  
  
1.  No **DimDate** da tabela, crie uma nova hierarquia chamada **calendário**.  
  
3.  Adicione a seguintes colunas na ordem:

    *  CalendarYear
    *  CalendarSemester
    *  CalendarQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
    
4.  No **DimDate** de tabela, crie um **Fiscal** hierarquia. Inclua as seguintes colunas:  
  
    *  FiscalYear
    *  FiscalSemester
    *  FiscalQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
  
5.  Por fim, no **DimDate** de tabela, crie um **ProductionCalendar** hierarquia. Inclua as seguintes colunas:  
    *  CalendarYear
    *  WeekNumberOfYear
    *  DayNumberOfWeek
  
 ## <a name="whats-next"></a>O que vem a seguir?
Vá para a próxima lição: [lição 10: criar partições](../analysis-services/lesson-10-create-partitions.md). 
  
  
