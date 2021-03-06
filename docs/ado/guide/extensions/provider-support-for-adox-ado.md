---
title: Suporte do provedor para ADOX (ADO) | Microsoft Docs
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
helpviewer_keywords:
- ADOX provider support [ADO]
ms.assetid: 64234ce5-dc46-4c8a-a316-61956b6b9abb
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 48f0e58ce794f53a123267b664e8c4c933976fe7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="provider-support-for-adox-ado"></a>Suporte do provedor para ADOX (ADO)
Determinados recursos do ADOX não têm suportados, dependendo do seu provedor de dados OLE DB. ADOX é totalmente compatível com o [OLE DB Provider for Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md). Recursos sem suporte com o [Microsoft OLE DB Provider para SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), o [Microsoft OLE DB Provider para ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md), ou o [Microsoft OLE DB Provider for Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md) são listados nas tabelas a seguir. Não há suporte para ADOX por outros provedores de OLE DB do Microsoft.  
  
## <a name="microsoft-ole-db-provider-for-sql-server"></a>Provedor Microsoft OLE DB para SQL Server  
  
|Objeto ou coleção|Restrição de uso|  
|--------------------------|-----------------------|  
|**Tabelas** coleção|Propriedades são somente leitura antes da criação do objeto e somente leitura ao fazer referência a um objeto existente.|  
|**Modos de exibição** coleção|**Modos de exibição** não tem suporte.|  
|**Procedimentos** coleção|O **Append** e **excluir** métodos não são suportados.|  
|**Procedimento** objeto|O **comando** não há suporte para a propriedade.|  
|**Chaves** coleção|O **Append** e **excluir** métodos não são suportados.|  
|**Os usuários** coleção|**Os usuários** não tem suporte.|  
|**Grupos de** coleção|**Grupos de** não tem suporte.|  
  
## <a name="microsoft-ole-db-provider-for-odbc"></a>Microsoft OLE DB Provider para ODBC  
  
|Objeto ou coleção|Restrição de uso|  
|--------------------------|-----------------------|  
|**Catálogo** objeto|O **criar** método não é suportado.|  
|**Tabelas** coleção|O **Append** e **excluir** métodos não são suportados. Propriedades são somente leitura antes da criação do objeto e somente leitura ao fazer referência a um objeto existente.|  
|**Procedimentos** coleção|O **Append** e **excluir** métodos não são suportados.|  
|**Procedimento** objeto|O **comando** não há suporte para a propriedade.|  
|**Índices** coleção|O **Append** e **excluir** métodos não são suportados.|  
|**Chaves** coleção|O **Append** e **excluir** métodos não são suportados.|  
|**Os usuários** coleção|**Os usuários** não tem suporte.|  
|**Grupos de** coleção|**Grupos de** não tem suporte.|  
  
## <a name="microsoft-ole-db-provider-for-oracle"></a>Microsoft OLE DB Provider for Oracle  
  
|Objeto ou coleção|Restrição de uso|  
|--------------------------|-----------------------|  
|**Catálogo** objeto|O **criar** método não é suportado.|  
|**Tabelas** coleção|O **Append** e **excluir** métodos não são suportados. Propriedades são somente leitura antes da criação do objeto e somente leitura ao fazer referência a um objeto existente.|  
|**Modos de exibição** coleção|O **Append** e **excluir** métodos não são suportados.|  
|**Exibição** objeto|O **comando** não há suporte para a propriedade.|  
|**Procedimentos** objeto|O **Append** e **excluir** métodos não são suportados.|  
|**Procedimento** objeto|O **comando** não há suporte para a propriedade.|  
|**Índices** coleção|O **Append** e **excluir** métodos não são suportados.|  
|**Chaves** coleção|O **Append** e **excluir** métodos não são suportados.|  
|**Os usuários** coleção|**Os usuários** não tem suporte.|  
|**Grupos de** coleção|**Grupos de** não tem suporte.|
