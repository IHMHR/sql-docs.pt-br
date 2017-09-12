---
title: Elemento DataType (ASSL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DataType Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DataType
helpviewer_keywords:
- DataType element
ms.assetid: efe6f717-8288-4ca2-85ed-9b63d27c02d8
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1e1cdd832a006148a8d72c8e7931ae4d662bce00
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="datatype-element-assl"></a>Elemento DataType (ASSL)
  Define o tipo de dados do elemento associado.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
  
<DataItem> <!-- or Measure -->  
   ...  
   <DataType>...</DataType>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Características do elemento  
  
|Característica|Descrição|  
|--------------------|-----------------|  
|Comprimento e tipo de dados|Cadeia de caracteres (enumeração)|  
|Valor padrão|Nenhuma|  
|Cardinalidade|0-1: elemento obrigatório que pode ocorrer apenas uma vez.|  
  
## <a name="element-relationships"></a>Relações do elemento  
  
|Relação|Elemento|  
|------------------|-------------|  
|Elemento pai|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md), [medidas](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
|Elementos filho|Nenhuma|  
  
## <a name="remarks"></a>Comentários  
 Os valores para **DataType** são definidos no **System.Data.OleDb.OleDbType** enumeração. No entanto, apenas os valores de enumeração na tabela a seguir são válidos no **DataType** elemento.  
  
|Valor|Description|  
|-----------|-----------------|  
|*BigInt*|Um inteiro de 64 bytes com sinal. Esse tipo de dados mapeado para o **Int64** tipo de dados na [!INCLUDE[msCoName](../../../includes/msconame-md.md)] de tipo do .NET Framework e os dados DBTYPE_I8 no OLE DB.|  
|*Bool*|Um valor booliano. Esse tipo de dados mapeado para o **booliano** tipo de dados no .NET Framework e o tipo de dados DBTYPE_BOOL no OLE DB.|  
|*Moeda*|Um valor de moeda variando de -2<sup>63</sup> (ou -922.337.203.685.477,5808) a 2<sup>63</sup>-1 (ou + 922.337.203.685.477,5807) com uma precisão de dez milésimos de uma unidade monetária. Esse tipo de dados mapeado para o **Decimal** tipo de dados no .NET Framework e o tipo de dados DBTYPE_CY no OLE DB.|  
|*Data*|Dados de data, armazenados como um número de ponto flutuante de precisão dupla. A parte inteira é o número de dias desde 30 de dezembro de 1899, enquanto a parte fracionária é uma fração de um dia. Esse tipo de dados mapeado para o **DateTime** tipo de dados no .NET Framework e o tipo de dados DBTYPE_DATE no OLE DB.|  
|*Duplo*|Número de ponto flutuante de precisão dupla dentro do intervalo de - 1, 79E 308 a 1, 79E 308. Esse tipo de dados mapeado para o **duplo** tipo de dados no .NET Framework e o tipo de dados DBTYPE_R8 no OLE DB.|  
|*Integer*|Um inteiro de 32 bytes com sinal. Esse tipo de dados mapeado para o **Int32** tipo de dados no .NET Framework e o tipo de dados DBTYPE_I4 no OLE DB.|  
|*Single*|Número de ponto flutuante de precisão única dentro do intervalo de - 3, 40E + 38, até 3, 40E + 38. Esse tipo de dados mapeado para o **único** tipo de dados no .NET Framework e o tipo de dados DBTYPE_R4 no OLE DB.|  
|*SmallInt*|Um inteiro com sinal de 16 bits. Esse tipo de dados mapeado para o **Int16** tipo de dados no .NET Framework e o tipo de dados DBTYPE_I2 no OLE DB.|  
|*TinyInt*|Um inteiro com sinal de 8 bits. Esse tipo de dados mapeado para o **SByte** tipo de dados no .NET Framework e o tipo de dados DBTYPE_I1 no OLE DB.|  
|*UnsignedBigInt*|Um inteiro não assinado de 64 bits. Esse tipo de dados mapeado para o **UInt64** tipo de dados no .NET Framework e o tipo de dados DBTYPE_UI8 no OLE DB.|  
|*UnsignedInt*|Um inteiro não assinado de 32 bits. Esse tipo de dados mapeado para o **UInt32** tipo de dados no .NET Framework e o tipo de dados DBTYPE_UI4 no OLE DB.|  
|*UnsignedSmallInt*|Um inteiro sem sinal de 16 bits. Esse tipo de dados mapeado para o **UInt16** tipo de dados no .NET Framework e o tipo de dados DBTYPE_UI2 no OLE DB.|  
|*WChar*|Um fluxo com terminação nula de caracteres Unicode. Esse tipo de dados mapeado para o **cadeia de caracteres** tipo de dados no .NET Framework e o tipo de dados DBTYPE_WSTR no OLE DB.|  
|*Herdado*|O tipo de dados a **DataItem** contidos no [fonte](../../../analysis-services/scripting/properties/source-element-measure-assl.md) elemento do **medidas** elemento.<br /><br /> Observação: Aplicável somente a **medidas** elementos.|  
  
## <a name="see-also"></a>Consulte também  
 [Propriedades &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  