---
title: Trabalhando com tipos de dados no fluxo de dados | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom data flow components [Integration Services], mapping data types
- data flow components [Integration Services], mapping data types
- data types [Integration Services], converting
ms.assetid: 941260d0-4ec3-4bf0-ab48-2b26733e6b24
caps.latest.revision: 52
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f020b16fd9609c64ed6a421c9c9f5e593d70276b
ms.contentlocale: pt-br
ms.lasthandoff: 08/03/2017

---
# <a name="working-with-data-types-in-the-data-flow"></a>Trabalhando com tipos de dados no fluxo de dados
  Ao desenvolver um componente de fluxo de dados personalizado no Integration Services, você trabalha constantemente com tipos de dados por meio da cópia de dados entre os buffers de fluxo de dados e a transformação de valores. As informações deste tópico ajudam você a escolher os tipos de dados corretos do [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] e a usar os métodos corretos quando estiver trabalhando com eles.  
  
## <a name="inserting-data-into-the-data-flow"></a>Inserindo dados no fluxo de dados  
 O <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> classe fornece uma série de **definir** métodos para copiar dados em colunas do buffer e uma série correspondente de **obter** métodos para recuperar dados das colunas do buffer. As tabelas a seguir mostram a você qual método usar com cada [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] tipo de dados.  
  
### <a name="set-methods-to-use-with-data-types"></a>Defina os métodos a serem utilizados com os tipos de dados  
 A tabela a seguir lista o tipo de dados na primeira coluna e, em seguida, lista correspondente **definir** e **obter** métodos.  
  
|Tipo de Dados|Método Set|Método Get|  
|---------------|----------------|----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_BOOL>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetBoolean%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetBoolean%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_BYTES>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetBytes%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetBytes%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_CY>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDecimal%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDecimal%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DATE>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDateTime%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDateTime%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBDATE>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDate%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDate%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIME>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetTime%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetTime%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIME2>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetTime%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetTime%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDateTime%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDateTime%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP2>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDateTime%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDateTime%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMPOFFSET>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDateTimeOffset%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDateTimeOffset%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DECIMAL>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDecimal%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDecimal%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_FILETIME>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDateTime%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDateTime%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_GUID>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetGuid%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetGuid%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I1>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetSByte%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetSByte%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I2>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetInt16%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetInt16%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I4>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetInt32%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetInt32%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I8>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetInt64%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetInt64%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_IMAGE>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddBlobData%2A>ou<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddBlobData%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetBlobData%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NTEXT>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddBlobData%2A>ou<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddBlobData%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetBlobData%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NULL>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetNull%2A>|Não há nenhum **obter** método é aplicável a este tipo de dados.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NUMERIC>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDecimal%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDecimal%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_R4>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetSingle%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetSingle%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_R8>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDouble%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetDouble%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_STR>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetString%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetString%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_TEXT>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddBlobData%2A>ou<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddBlobData%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetBlobData%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI1>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetByte%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetByte%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI2>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetUInt16%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetUInt16%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI4>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetUInt32%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetUInt32%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI8>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetUInt64%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetUInt64%2A>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_WSTR>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetString%2A>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.GetString%2A>|  
  
### <a name="data-types-to-use-with-the-set-methods"></a>Tipos de dados para usar com os métodos Set  
  
|Método Set|Tipo de Dados|  
|----------------|---------------|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddBlobData%2A>ou<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddBlobData%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_IMAGE>, <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NTEXT> ou <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_TEXT>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetBoolean%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_BOOL>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetByte%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI1>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetBytes%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_BYTES>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDate%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBDATE>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDateTime%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DATE>, <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP>, <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP2> ou <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_FILETIME>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDateTimeOffset%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMPOFFSET>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDecimal%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_CY>, <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DECIMAL> ou <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NUMERIC>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetDouble%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_R8>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetGuid%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_GUID>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetInt16%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I2>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetInt32%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I4>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetInt64%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I8>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetNull%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NULL>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetSByte%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I1>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetSingle%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_R4>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetString%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_STR>ou<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_WSTR>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetTime%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIME>ou<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIME2>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetUInt16%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI2>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetUInt32%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI4>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetUInt64%2A>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI8>|  
  
## <a name="mapping-data-types-in-the-data-flow"></a>Mapeando tipos de dados no fluxo de dados  
 Ao mover dados de fontes até transformações para destinos, um componente de fluxo de dados às vezes deve converter tipos de dados entre o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] tipos definidos no <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType> enumeração e tipos de dados gerenciados do [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] definido no **sistema** namespace. Além disso, às vezes, um componente precisa converter um tipo de dados do [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] em outro para que o tipo possa ser convertido em um tipo gerenciado.  
  
> [!NOTE]  
>  Os arquivos de mapeamento em formato XML que são instalados por padrão em C:\Program Files\Microsoft SQL Server\130\DTS\MappingFiles não são relacionados ao mapeamento de tipo de dados discutido neste tópico. Esses arquivos mapeiam tipos de dados de uma versão do banco de dados ou sistema para outro (por exemplo, do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] para o Oracle) e são usados apenas pelo Assistente de Importação e Exportação do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Para obter mais informações sobre esses arquivos de mapeamento, consulte [SQL Server Import and Export Wizard](~/integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md).  
  
### <a name="mapping-between-integration-services-and-managed-data-types"></a>Mapeando entre os tipos de dados gerenciados e do Integration Services   
 O <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A> e os métodos <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A> mapeiam tipos de dados [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] para tipos de dados gerenciados.  
  
> [!CAUTION]  
>  Os desenvolvedores devem utilizar esses métodos da classe <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> com cuidado e podem desejar codificar seus próprios métodos de mapeamento de tipo de dados que são mais adequados para as necessidades exclusivas de seus componentes personalizados. Os métodos existentes não consideram a precisão ou a escala numérica ou outras propriedades relacionadas intimamente ao próprio tipo de dados. O [!INCLUDE[msCoName](../../../includes/msconame-md.md)] pode modificar ou remover esses métodos ou modificar os mapeamentos que eles executam em uma versão futura do [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
 A tabela a seguir lista como os métodos <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A> e <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A> mapeiam vários tipos de dados do [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] para tipos de dados gerenciados.  
  
|Tipo de dados do Integration Services|Mapeia para este tipo de dado gerenciado|  
|------------------------------------|------------------------------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_WSTR>|System.String|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_BYTES>|Array of System.Byte|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP>|System.DateTime|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP2>|System.DateTime|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMPOFFSET>|System.DateTimeOffset|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBDATE>|System.DateTime|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIME>|System.TimeSpan|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIME2>|System.TimeSpan|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DATE>|System.DateTime|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_FILETIME>|System.DateTime|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NUMERIC>|System.Decimal|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_GUID>|System.Guid|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I1>|System.SByte|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I2>|System.Int16|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I4>|System.Int32|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I8>|System.Int64|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_BOOL>|System.Boolean|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_R4>|System.Single|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_R8>|System.Double|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI1>|System.Byte|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI2>|System.UInt16|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI4>|System.UInt32|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_UI8>|System.UInt64|  
  
### <a name="mapping-integration-services-data-types-to-fit-managed-data-types"></a>Mapeando tipos de dados do Integration Services para se ajustarem aos tipos de dados gerenciados  
 Às vezes, um componente de fluxo de dados também tem que converter um tipo de dado do [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] em outro antes daquele tipo poder ser convertido em um tipo gerenciado. O <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A> mapas de classe do método [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] tipos de dados para outros [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] tipos de dados que, em seguida, podem ser mapeados para tipos de dados gerenciados usando o <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A> método.  
  
> [!CAUTION]  
>  Os desenvolvedores devem utilizar esses métodos da classe <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> com cuidado e podem desejar codificar seus próprios métodos de mapeamento de tipo de dados que são mais adequados para as necessidades exclusivas de seus componentes personalizados. Os métodos existentes não consideram a precisão ou a escala numérica ou outras propriedades relacionadas intimamente ao próprio tipo de dados. O [!INCLUDE[msCoName](../../../includes/msconame-md.md)] pode modificar ou remover esses métodos ou modificar os mapeamentos que eles executam em uma versão futura do [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
 A tabela seguinte lista como o método <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A> mapeia tipos de dados do [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] para outros tipos de dados do [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
|Tipos de dados originais do Integration Services|Mapeia para este tipo de dado do Integration Services|  
|---------------------------------------------|-------------------------------------------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DECIMAL>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NUMERIC>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_CY>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NUMERIC>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DATE>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBDATE>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_FILETIME>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP2>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIMESTAMP>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIME>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_DBTIME2>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_BOOL>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_I4>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_TEXT>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_WSTR>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_NTEXT>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_WSTR>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_STR>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_WSTR>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_IMAGE>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DataType.DT_BYTES>|  
  
> [!NOTE]  
>  O método <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A> não retorna um valor para o tipo de dado DT_DBTIMESTAMPOFFSET e ocorre uma <xref:Microsoft.SqlServer.Dts.Pipeline.UnsupportedBufferDataTypeException>. Você deve converter o tipo de dado DT_DBTIMESTAMPOFFSET em um dos tipos de dados de data/hora do [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] que podem ser mapeados para um tipo de dado gerenciado. Para obter uma lista de tipos de dados de data/hora do [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] que podem ser mapeados para tipos de dados gerenciados, consulte a tabela na seção anterior, "Mapeamento entre os tipos de dados gerenciados e do Integration Services". Para obter informações sobre como converter tipos de dados, consulte [tipos de dados do Integration Services](../../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A>   
 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A>   
 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>   
 [Tipos de dados do Integration Services](../../../integration-services/data-flow/integration-services-data-types.md)  
  
  
