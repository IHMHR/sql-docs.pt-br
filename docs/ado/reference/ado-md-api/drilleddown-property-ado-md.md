---
title: Propriedade DrilledDown (ADO MD) | Microsoft Docs
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
- DrilledDown
- Member::DrilledDown
helpviewer_keywords:
- DrilledDown property [ADO MD]
ms.assetid: bf39dd36-fc7a-4f6e-86c0-fa71430c0d86
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c34f12d84c53d782b2629a408d9182ac36a37db0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="drilleddown-property-ado-md"></a>Propriedade DrilledDown (ADO MD)
Indica se filhos logo após o [membro](../../../ado/reference/ado-md-api/member-object-ado-md.md) no eixo.  
  
## <a name="return-values"></a>Valores de retorno  
 Retorna um **booliano** valor e é somente leitura. **DrilledDown** retorna **True** se não houver nenhum membro filho do membro atual no eixo. **DrilledDown** retorna **False** se o membro atual tiver um ou mais membros filho no eixo.  
  
## <a name="remarks"></a>Remarks  
 Use o **DrilledDown** propriedade para determinar se há pelo menos um filho desse membro no eixo imediatamente após esse membro. Essa informação é útil ao exibir o membro.  
  
 Essa propriedade só é suportada em [membro](../../../ado/reference/ado-md-api/member-object-ado-md.md) objetos que pertencem a um [posição](../../../ado/reference/ado-md-api/position-object-ado-md.md) objeto. Ocorre um erro quando essa propriedade é referenciada em **membro** objetos que pertencem a um [nível](../../../ado/reference/ado-md-api/level-object-ado-md.md) objeto.  
  
## <a name="applies-to"></a>Aplica-se a  
 [Objeto Member (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade ParentSameAsPrev (ADO MD)](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)
