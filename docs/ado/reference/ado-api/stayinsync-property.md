---
title: Propriedade StayInSync | Microsoft Docs
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
- Recordset20::StayInSync
- Recordset20::put_StayInSync
- Recordset20::PutStayInSync
- Recordset20::get_StayInSync
- Recordset20::GetStayInSync
helpviewer_keywords:
- StayInSync property
ms.assetid: 502d69b5-dc9a-455d-b115-a03bd39a552b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d4e5067036aaaf36c60a134f825012fdc5facf75
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="stayinsync-property"></a>Propriedade StayInSync
Indica, em um hierárquica [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objeto, se a referência para os registros filho subjacente (isto é, o *capítulo*) é alterado quando a linha pai posicione as alterações.  
  
## <a name="settings-and-return-values"></a>Configurações e valores de retorno  
 Define ou retorna um **booliano** valor. O valor padrão é **True**. Se **True**, o capítulo será atualizado se o pai **registros** alterações de objeto linha posição; se **False**, o capítulo continuará a fazer referência a dados no capítulo anterior mesmo que o pai **registros** objeto alterado posição da linha.  
  
## <a name="remarks"></a>Remarks  
 Essa propriedade se aplica a conjuntos de registros hierárquicos, como aqueles com suporte a [Microsoft Data Shaping Service para OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)e deve ser definido no pai **registros** antes do filho  **Conjunto de registros** é recuperado. Essa propriedade simplifica a navegação hierárquicos conjuntos de registros.  
  
## <a name="applies-to"></a>Aplica-se a  
 [Objeto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de propriedade StayInSync (VB)](../../../ado/reference/ado-api/stayinsync-property-example-vb.md)   
 [Microsoft Data Shaping Service para OLE DB (provedor de serviços de ADO)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)
