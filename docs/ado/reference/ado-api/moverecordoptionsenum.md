---
title: MoveRecordOptionsEnum | Microsoft Docs
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
- MoveRecordOptionsEnum
helpviewer_keywords:
- MoveRecordOptionsEnum enumeration [ADO]
ms.assetid: f53c2ce4-1021-4a45-92b8-775e8bebad99
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 18508d9103b0be9a0dae3cff013ca2732a00035c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="moverecordoptionsenum"></a>MoveRecordOptionsEnum
Especifica o comportamento do [registro](../../../ado/reference/ado-api/record-object-ado.md) objeto [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md) método.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adMoveUnspecified**|-1|Padrão. Executa a operação de movimentação padrão: A operação falhará se o arquivo de destino ou o diretório já existe e a operação Atualizar links de hipertexto.|  
|**adMoveOverWrite**|1|Substitui o arquivo de destino ou o diretório, mesmo se ele já existe.|  
|**adMoveDontUpdateLinks**|2|Modifica o comportamento padrão de **MoveRecord** método por não atualizar os links de hipertexto da fonte de **registro**. O comportamento padrão depende de recursos do provedor. Operação de movimentação atualiza links se o provedor é compatível com. Se o provedor não pode corrigir links ou se esse valor não for especificado, a movimentação bem-sucedida mesmo quando links não foram corrigidos.|  
|**adMoveAllowEmulation**|4|Solicita que o provedor tentará simular a movimentação (usando as operações de exclusão, upload e download). Se a tentativa de mover o **registro** falhar porque a URL de destino está em um servidor diferente ou atendido por um provedor diferente do código-fonte, isso pode causar maior latência ou perda de dados, devido aos recursos de provedor diferente quando movendo recursos entre os provedores.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Constantes não têm equivalentes do ADO/WFC.  
  
## <a name="applies-to"></a>Aplica-se a  
 [Método MoveRecord (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
