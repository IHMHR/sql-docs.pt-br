---
title: Método getEncrypt (SQLServerDataSource) | Microsoft Docs
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
- getEncrypt Method (SQLServerDataSource)
apilocation:
- getEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 1cdb12dd-6e6f-4bbd-8f5f-9e630f3ee2c9
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9262c2fb18160f5072d21a71c082bd00d17fc302
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="getencrypt-method-sqlserverdatasource"></a>Método getEncrypt (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retorna um **booliano** valor que indica se a propriedade encrypt está habilitada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public boolean getEncypt()  
```  
  
## <a name="return-value"></a>Valor de retorno  
 **True** se criptografar está habilitado. Caso contrário, **false**.  
  
## <a name="remarks"></a>Remarks  
 Se a propriedade de criptografia é definida como **true**, o [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] garante que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] usará criptografia SSL para todos os dados enviados entre o cliente e o servidor se o servidor tem um certificado instalado.  
  
 Se a propriedade de criptografia é não especificada ou definida como **false**, o driver não forçará o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] para oferecer suporte à criptografia SSL. Se o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] instância não está configurada para forçar a criptografia SSL, é estabelecida uma conexão sem criptografia. Se o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] instância é configurada para forçar a criptografia SSL, o [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] automaticamente irá habilitar a criptografia SSL quando em execução no corretamente configurado a máquina Virtual Java (JVM), caso contrário, a conexão será encerrada e o driver irá gerar um erro. Se a propriedade de criptografia não for definida, o [getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md) método retorna o valor padrão de **false**.  
  
## <a name="see-also"></a>Consulte também  
 [Membros de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
