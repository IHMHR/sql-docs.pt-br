---
title: Comparando a tarefa de Script e o componente Script | Microsoft Docs
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], comparing to Script component
- Script component [Integration Services], comparing to Script task
ms.assetid: 4b73753a-4239-491b-b7a6-abc63ba83d2d
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0413b4b88a1f0326dad1ba261aea647cefd43302
ms.contentlocale: pt-br
ms.lasthandoff: 08/03/2017

---
# <a name="comparing-the-script-task-and-the-script-component"></a>Comparando a tarefa Script e o componente Script
  A tarefa de Script, disponível na janela do fluxo de controle do [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] designer e o componente Script, disponível na janela do fluxo de dados, têm finalidades bem distintas um [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pacote. A tarefa é uma ferramenta de fluxo de controle de uso general, enquanto o componente serve como uma origem, transformação ou destino no fluxo de dados. Apesar das diferentes finalidades, a tarefa Script e o componente Script possuem algumas semelhanças nas ferramentas de codificação que eles usam e nos objetos do pacote que são disponibilizados para o desenvolvedor. A compreensão dessas semelhanças e diferenças pode ajudá-lo a usar a tarefa e o componente de forma mais eficaz.  
  
## <a name="similarities-between-the-script-task-and-the-script-component"></a>Semelhanças entre a tarefa Script e o componente Script  
 A tarefa Script e o componente Script compartilham os recursos em comum a seguir.  
  
|Recurso|Description|  
|-------------|-----------------|  
|Dois modos de design-tempo|Na tarefa e no componente, você começa especificando propriedades no editor e, depois, alterna para o ambiente de desenvolvimento para escrever código.|  
|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA)|A tarefa e o componente usam o mesmo VSTA IDE e dão suporte ao código escrito em [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.|  
|Scripts pré-compilados|A partir do [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)], todos os scripts são pré-compilados. Em versões anteriores, você podia especificar se os scripts foram pré-compilados.<br /><br /> O script é pré-compilado em código binário, permitindo maior rapidez na execução, mas isso resulta no aumento do tamanho do pacote.|  
|Depuração|A tarefa e o componente dão suporte a pontos de interrupção e passa pelo código durante a depuração no ambiente de design. Para obter mais informações, consulte [codificando e depurando a tarefa Script](../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md) e [codificando e depurando o componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).|  
  
## <a name="differences-between-the-script-task-and-the-script-component"></a>Diferenças entre a tarefa Script e o componente Script  
 Convém destacar as diferenças a seguir entre a tarefa Script e o componente Script.  
  
|Recurso|Tarefa Script|Componente Script|  
|-------------|-----------------|----------------------|  
|Fluxo de controle / Fluxo de dados|A tarefa Script é configurada na guia Fluxo de Controle do designer e é executada fora do fluxo de dados do pacote.|O componente Script é configurado na página Fluxo de Dados do designer e representa uma origem, transformação ou destino na tarefa Fluxo de Dados.|  
|Finalidade|Uma tarefa Script pode realizar praticamente qualquer tarefa para fins gerais.|Especifique se você deseja criar uma origem, transformação ou destino com o componente Script.|  
|Execução|Uma tarefa Script executa código personalizado em algum ponto no fluxo de trabalho do pacote. A menos que você coloque isso em um contêiner de loop ou em um manipulador de eventos, ele só será executado uma vez.|Um componente Script também é executado uma vez, mas costuma executar sua rotina de processamento principal uma vez para cada linha de dados do fluxo de dados.|  
|Editor|O **Editor da tarefa Script** tem três páginas: **geral**, **Script**, e **expressões**. Somente o **ReadOnlyVariables** e **ReadWriteVariables**, e **ScriptLanguage** propriedades afetam diretamente o código que você pode gravar.|O **Editor de transformação scripts** tem até quatro páginas: **colunas de entrada**, **entradas e saídas**, **Script**, e **gerenciadores de Conexão**. Os metadados e propriedades que você configura em cada uma dessas páginas determinam os membros das classes base que são gerenciadas automaticamente para seu uso na codificação.|  
|Interação com o pacote|No código escrito para uma tarefa de Script, você deve usar o **Dts** propriedade para acessar outros recursos do pacote. O **Dts** propriedade é um membro do **ScriptMain** classe.|No código do componente Script, você usa propriedades de acessador tipado para acessar determinados recursos do pacote, tais como variáveis e gerenciadores de conexões.<br /><br /> O **PreExecute** método pode acessar somente as variáveis somente leitura. O **PostExecute** método pode acessar somente leitura e variáveis de leitura/gravação.<br /><br /> Para obter mais informações sobre esses métodos, consulte [codificando e depurando o componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).|  
|Usando variáveis|A tarefa Script usa o <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> propriedade o **Dts** objeto para acessar variáveis que estão disponíveis por meio da tarefa <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> e <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> propriedades. Por exemplo:<br /><br /> [Visual Basic]<br /><br /> `Dim myVar as String` <br /> `myVar = Dts.Variables(“MyStringVariable”).Value.ToString`<br /><br /> [C#]<br /><br /> `string myVar;` <br /> `myVar = Dts.Variables["MyStringVariable"].Value.ToString();`|O componente Script usa propriedades do acessador tipado da classe base gerada automaticamente, criada a partir das propriedades <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReadOnlyVariables%2A> e <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReadWriteVariables%2A> do componente. Por exemplo:<br /><br /> [Visual Basic]<br /><br /> `Dim myVar as String` <br /> `myVar = Me.Variables.MyStringVariable`<br /><br /> [C#]<br /><br /> `string myVar;` <br /> `myVar = this.Variables.MyStringVariable;`|  
|Usando conexões|A tarefa Script usa o <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> propriedade o **Dts** objeto para gerenciadores de conexão de acesso definidos no pacote. Por exemplo:<br /><br /> [Visual Basic]<br /><br /> `Dim myFlatFileConnection As String` <br /> `myFlatFileConnection = _     DirectCast(Dts.Connections("Test Flat File Connection").AcquireConnection(Dts.Transaction), _     String)`<br /><br /> [C#]<br /><br /> `string myFlatFileConnection;` <br /> `myFlatFileConnection = (Dts.Connections["Test Flat File Connection"].AcquireConnection(Dts.Transaction) as String);`|O componente Script usa propriedades do acessador tipado da classe base gerada automaticamente, criada a partir da lista de gerenciadores de conexões digitada pelo usuário na página Gerenciadores de Conexões do editor. Por exemplo:<br /><br /> [Visual Basic]<br /><br /> `Dim connMgr As IDTSConnectionManager100` <br /> `connMgr = Me.Connections.MyADONETConnection`<br /><br /> [C#]<br /><br /> `IDTSConnectionManager100 connMgr;` <br /> `connMgr = this.Connections.MyADONETConnection;`|  
|Gerando eventos|A tarefa Script usa o <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> propriedade o **Dts** objeto para gerar eventos. Por exemplo:<br /><br /> [Visual Basic]<br /><br /> `Dts.Events.FireError(0, "Event Snippet", _     ex.Message & ControlChars.CrLf & ex.StackTrace, _     "", 0)`<br /><br /> [C#]<br /><br /> `Dts.Events.FireError(0, "Event Snippet", ex.Message + "\r" + ex.StackTrace, "", 0);`|O componente Script gera erros, avisos e mensagens informativas através dos métodos da interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> retornados pela propriedade <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A>. Por exemplo:<br /><br /> [Visual Basic]<br /><br /> `Dim myMetadata as IDTSComponentMetaData100 myMetaData = Me.ComponentMetaData myMetaData.FireError(...)`|  
|Log|A tarefa Script usa o <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> método o **Dts** habilitado de objeto para registrar informações para provedores de log. Por exemplo:<br /><br /> [Visual Basic]<br /><br /> `Dim bt(0) As Byte Dts.Log("Test Log Event", _     0, _     bt)`<br /><br /> [C#]<br /><br /> `byte[] bt = new byte[0];` <br /> `Dts.Log("Test Log Event", 0, bt);`|O componente Script usa o método <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> da classe base gerada automaticamente para registrar informações para provedores de log habilitados. Por exemplo:<br /><br /> [Visual Basic]<br /><br /> `Dim bt(0) As Byte`<br /><br /> `Me.Log("Test Log Event", _`<br /><br /> `0, _`<br /><br /> `bt)`<br /><br /> [C#]<br /><br /> `byte[] bt = new byte[0]; this.Log("Test Log Event", 0, bt);`|  
|Retornando resultados|A tarefa Script usa o <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> propriedade e opcional <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> propriedade o **Dts** objeto notificar o tempo de execução de seus resultados.|O componente Script é executado como parte da tarefa Fluxo de Dados e não relata resultados através de uma dessas propriedades.|  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo o pacote com a tarefa de Script](../../integration-services/extending-packages-scripting/task/extending-the-package-with-the-script-task.md)   
 [Estendendo o fluxo de dados com o componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)   
  
  