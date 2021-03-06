---
title: Método SetPermissions (ADOX) | Microsoft Docs
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
- User25::SetPermissions
- User25::raw_SetPermissions
- _Group25::SetPermissions
- _Group25::raw_SetPermissions
helpviewer_keywords:
- SetPermissions method [ADOX]
ms.assetid: b7f925d7-b05c-4376-bb49-f8d2c17b8b24
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3178c472bfeb58361ae6d7d889d82d3823b09469
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="setpermissions-method-adox"></a>Método SetPermissions (ADOX)
Especifica as permissões para um [grupo](../../../ado/reference/adox-api/group-object-adox.md) ou [usuário](../../../ado/reference/adox-api/user-object-adox.md) em um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
GroupOrUser.SetPermissions Name, ObjectType, Action, Rights [, Inherit] [, ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *Nome*  
 Um **cadeia de caracteres** valor que especifica o nome do objeto para o qual definir permissões.  
  
 *ObjectType*  
 Um **longo** valor que pode ser um do [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) constantes, que especifica o tipo de objeto para o qual obter as permissões.  
  
 *Ação*  
 Um **longo** valor que pode ser um do [ActionEnum](../../../ado/reference/adox-api/actionenum.md) constantes que especifica o tipo de ação a ser executada ao definir as permissões.  
  
 *Direitos*  
 Um **longo** valor que pode ser um bitmask de um ou mais o [RightsEnum](../../../ado/reference/adox-api/rightsenum.md) constantes, que indica os direitos para definir.  
  
 *Herdar*  
 Opcional. Um **longo** valor que pode ser um do [InheritTypeEnum](../../../ado/reference/adox-api/inherittypeenum.md) constantes, que especifica como os objetos herdarão essas permissões. O valor padrão é **adInheritNone**.  
  
 *ObjectTypeId*  
 Opcional. Um **Variant** valor que especifica o GUID de um tipo de objeto de provedor que não é definido pela especificação do OLE DB. Esse parâmetro é necessário se *ObjectType* é definido como **adPermObjProviderSpecific**; caso contrário, ele não é usado.  
  
## <a name="remarks"></a>Remarks  
 Um erro ocorrerá se o provedor não oferece suporte para configurar direitos de acesso para usuários ou grupos.  
  
> [!NOTE]
>  Ao chamar **SetPermissions**, a configuração de ações como **adAccessRevoke** substitui as configurações do *direitos* parâmetro. Não defina *ações* para **adAccessRevoke** se você quiser que os direitos especificados no *direitos* parâmetro entrem em vigor.  
  
## <a name="applies-to"></a>Aplica-se a  
  
|||  
|-|-|  
|[Objeto Group (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[Objeto User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de métodos de SetPermissions (VB) e GetPermissions](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Método GetPermissions (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)   
 [Propriedade Name (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)
