---
title: Método Cancel (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerStatement.cancel
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 276bd9c1-9329-4fc9-9622-ed673c83a12d
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e1386c17a98b623fee4bf25df949467f5996684d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="cancel-method-sqlserverstatement"></a>Método cancel (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Cancela a instrução SQL que está sendo executada por esse [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public final void cancel()  
```  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Esse método de cancelamento é especificado pelo método na interface Java.SQL. Statement Cancelar.  
  
 Ao executar uma instrução que produz um único conjunto de resultados grande, apenas de encaminhamento, somente leitura, você pode estar interessado apenas em algum conjunto inicial de linhas no conjunto de resultados retornado. Nesse caso, o aplicativo pode chamar o [Cancelar](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md) método do objeto de instrução associado antes de fechar o resultado definido para minimizar o tempo de processamento necessário para descartar as linhas desnecessárias restantes. Ao decidir se essa técnica será usada ou não, é recomendável considerar a compensação entre o tempo de processamento que seria economizado e o tempo e a viagem de ida e volta adicional ao servidor, necessários para cancelar a execução.  
  
## <a name="see-also"></a>Consulte também  
 [Membros SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
