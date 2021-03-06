---
title: Executando comandos em uma fonte de dados analíticos | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 01f7c32643c4e0a48f2451de37729f919b057208
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="executing-commands-against-an-analytical-data-source"></a>Executando comandos em uma fonte de dados analíticos
  Depois de estabelecer uma conexão com uma fonte de dados analíticos, você poderá usar um objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> para executar comandos nessa fonte de dados e retornar resultados dela. Esses comandos podem recuperar dados usando MDX (Multidimensional Expressions), DMX (Data Mining Extensions) ou até mesmo uma sintaxe limitada de SQL. Além disso, você poderá usar comandos ASSL (Analysis Services Scripting Language) para modificar o banco de dados subjacente.  
  
## <a name="creating-a-command"></a>Criando um comando  
 Antes de executar um comando, você deverá criá-lo. Você pode criar um comando usando um destes métodos:  
  
-   O primeiro método usa o construtor <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>, que pode fazer com que um comando seja executado na fonte de dados, e usa um objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> no qual o comando será executado.  
  
-   O segundo método usa o método <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.CreateCommand%2A> do objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 O texto do comando a ser executado pode ser consultado e modificado por meio da propriedade <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.CommandText%2A>. Os comandos criados por você não precisam retornar dados depois de executados.  
  
## <a name="running-a-command"></a>Executar um comando  
 Depois que criar um objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>, existem vários métodos <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> que o seu comando poderá usar para executar diversas ações. A tabela a seguir lista algumas dessas ações.  
  
|Para|Use este método|  
|--------|---------------------|  
|Retornar resultados como um fluxo de dados|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> para retornar um objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|  
|Retornar um objeto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A>|  
|Executar comandos que não retornam linhas|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteNonQuery%2A>|  
|Retornar um **XMLReader** objeto que contém os dados em XML para um formato compatível com o Analysis (XMLA)|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A>|  
  
### <a name="example-of-running-a-command"></a>Exemplo de execução de um comando  
 Este exemplo usa o <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> para executar um comando XMLA que processará o **Adventure Works DW** cubo no servidor local, sem retornar dados.  
  
 [!code-cs[Adomd.NetClient#ExecuteXMLAProcessCommand](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/executing-commands-again_1.cs)]  
  
  
