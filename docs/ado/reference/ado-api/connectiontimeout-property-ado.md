---
title: Propriedade ConnectionTimeout (ADO) | Microsoft Docs
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
- Connection15::ConnectionTimeout
helpviewer_keywords:
- ConnectionTimeout property [ADO]
ms.assetid: 8904a403-1383-4b4b-b53d-5c01d6f5deac
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2b60682fdc85cf7f24c21e5ac4a2f2efc9d3fb30
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="connectiontimeout-property-ado"></a>Propriedade ConnectionTimeout (ADO)
Indica por quanto tempo a aguardar ao estabelecer uma conexão antes de encerrar a tentativa e gerar um erro.  
  
## <a name="settings-and-return-values"></a>Configurações e valores de retorno  
 Define ou retorna um **longo** valor que indica, em segundos, o tempo de espera para a conexão abrir. O padrão é 15.  
  
## <a name="remarks"></a>Remarks  
 Use o **ConnectionTimeout** propriedade em uma [Conexão](../../../ado/reference/ado-api/connection-object-ado.md) se os atrasos de rede de tráfego ou pesada de uso do servidor faça necessárias abandono de uma tentativa de conexão do objeto. Se o tempo desde o **ConnectionTimeout** configuração da propriedade decorrido antes da abertura da conexão, ocorrerá um erro e ADO cancela a tentativa. Se você definir a propriedade como zero, o ADO aguardará indefinidamente até que a conexão é aberta. Verifique se o provedor ao qual você está escrevendo código oferece suporte a **ConnectionTimeout** funcionalidade.  
  
 O **ConnectionTimeout** propriedade é leitura/gravação quando a conexão é fechada e somente leitura quando ela é aberta.  
  
## <a name="applies-to"></a>Aplica-se a  
 [Objeto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de propriedades de estado (VB), ConnectionTimeout e ConnectionString](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [Exemplo de propriedades de estado (VC + +), ConnectionTimeout e ConnectionString](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [Propriedade CommandTimeout (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)
