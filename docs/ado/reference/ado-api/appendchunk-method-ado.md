---
title: Método AppendChunk (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::AppendChunk
- Field20::AppendChunk
helpviewer_keywords:
- AppendChunk method [ADO]
ms.assetid: c648b5a8-d4f1-4d16-836e-3957feb03617
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ba8020b9bf2666ba3b2ab0ffe9156c771360c95
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="appendchunk-method-ado"></a>Método AppendChunk (ADO)
Acrescenta dados a um texto grande ou dados binários [campo](../../../ado/reference/ado-api/field-object.md), ou um [parâmetro](../../../ado/reference/ado-api/parameter-object.md) objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
object.AppendChunk Data  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *objeto*  
 Um **campo** ou **parâmetro** objeto.  
  
 *Dados*  
 Um **Variant** que contém os dados para acrescentar ao objeto.  
  
## <a name="remarks"></a>Remarks  
 Use o **AppendChunk** método em um **campo** ou **parâmetro** objeto preenchê-lo com dados binários longos ou de caractere. Em situações em que a memória do sistema é limitada, você pode usar o **AppendChunk** método para manipular valores longos em partes em vez de em sua totalidade.  
  
## <a name="field"></a>Campo  
 Se o **adFldLong** bit no [atributos](../../../ado/reference/ado-api/attributes-property-ado.md) propriedade de um **campo** objeto é definido como **true**, você pode usar o  **AppendChunk** método para esse campo.  
  
 A primeira **AppendChunk** chamar em um **campo** objeto grava dados para o campo, substituindo os dados existentes. Subsequentes **AppendChunk** adicionam chamadas aos dados existentes. Se você está anexando um campo de dados e, em seguida, você pode definir ou ler o valor de outro campo no registro atual, o ADO pressupõe que você tiver terminado de anexar os dados para o primeiro campo. Se você chamar o **AppendChunk** método no primeiro campo novamente, ADO interpreta a chamada como um novo **AppendChunk** operação e substitui os dados existentes. Acessar campos em outros [registros](../../../ado/reference/ado-api/recordset-object-ado.md) objetos que não são clones do primeiro **registros** objeto não interromperá **AppendChunk** operações.  
  
 Se não houver nenhum registro atual ao chamar **AppendChunk** em uma **campo** do objeto, ocorrerá um erro.  
  
> [!NOTE]
>  O **AppendChunk** método não funcionará em **campo** objetos de um [registro Object (ADO)](../../../ado/reference/ado-api/record-object-ado.md) objeto. Ele não executará qualquer operação e produzirá um erro de tempo de execução.  
  
## <a name="parameter"></a>Parâmetro  
 Se o **adParamLong** bit no **atributos** propriedade de um **parâmetro** objeto é definido como **true**, você pode usar o  **AppendChunk** método para esse parâmetro.  
  
 A primeira **AppendChunk** chamar em um **parâmetro** objeto grava dados para o parâmetro, substituindo os dados existentes. Subsequentes **AppendChunk** chama um **parâmetro** objeto acrescentar dados existentes do parâmetro. Um **AppendChunk** chamada que transmite um valor nulo descarta todos os dados de parâmetro.  
  
## <a name="applies-to"></a>Aplica-se a  
  
|||  
|-|-|  
|[Objeto Field](../../../ado/reference/ado-api/field-object.md)|[Objeto Parameter](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>Consulte também  
 [AppendChunk e GetChunk métodos exemplo (VB)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vb.md)   
 [AppendChunk e GetChunk métodos exemplo (VC + +)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vc.md)   
 [Propriedade Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)   
 [Método GetChunk (ADO)](../../../ado/reference/ado-api/getchunk-method-ado.md)
