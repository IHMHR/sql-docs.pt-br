---
title: AffectEnum | Microsoft Docs
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- AffectEnum
helpviewer_keywords:
- AffectEnum enumeration [ADO]
ms.assetid: 1ab921a0-6c57-43b4-9291-701b2599f3e8
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 63bf19b58ddd79dc684011b56287f35107e568af
ms.contentlocale: pt-br
ms.lasthandoff: 09/09/2017

---
# <a name="affectenum"></a>AffectEnum
Especifica quais registros são afetados por uma operação.  
  
|Constante|Valor|Description|  
|--------------|-----------|-----------------|  
|**adAffectAll**|3|Se não houver um [filtro](../../../ado/reference/ado-api/filter-property.md) aplicada para o **registros**, afeta todos os registros.<br /><br /> Se o **filtro** está definida como um critério de cadeia de caracteres (como "Autor = 'Smith'"), em seguida, a operação afeta o capítulo atual de registros visíveis.<br /><br /> Se o **filtro** está definida como um membro do [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md) ou uma matriz de indicadores e, em seguida, a operação afetará todas as linhas do **registros**. **Observação:****adAffectAll** está oculto no Pesquisador de objetos do Visual Basic.  |  
|**adAffectAllChapters**|4|Afeta todos os registros em todos os capítulos irmão do **registros**, incluindo aqueles não visíveis por meio de qualquer **filtro** que está sendo aplicado.|  
|**adAffectCurrent**|1|Afeta somente o registro atual.|  
|**adAffectGroup**|2|Afeta somente os registros que satisfazem atual [filtro](../../../ado/reference/ado-api/filter-property.md) configuração de propriedade. Você deve definir o **filtro** propriedade para um **FilterGroupEnum** valor ou uma matriz de **indicadores** para usar essa opção.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Pacote: **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.Affect.ALL|  
|AdoEnums.Affect.ALLCHAPTERS|  
|AdoEnums.Affect.CURRENT|  
|AdoEnums.Affect.GROUP|  
  
## <a name="applies-to"></a>Aplica-se a  
  
|||  
|-|-|  
|[Método CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|[Método Delete (Conjunto de registros ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|  
|[Método Resync](../../../ado/reference/ado-api/resync-method.md)|[Método UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|