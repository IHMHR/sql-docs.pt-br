---
title: Usando o ADO para publicação na Internet | Microsoft Docs
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
- ADO, Internet publishing
- publishing to Internet [ADO]
- Internet publishing [ADO]
- urls [ADO]
ms.assetid: d399fce4-b70b-418f-8110-3deb3448863c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4adf31cd66246cd078bb31dc99ac5e8025f04636
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="using-ado-for-internet-publishing"></a>Usando o ADO para publicação na Internet
[O provedor OLE DB para Internet Publishing](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md) mostra um exemplo específico de acesso a dados heterogêneos com ADO. Embora os exemplos nesta seção serão específicos usando o provedor de publicação de Internet, os princípios demonstrados devem ser semelhantes ao usar ADO com outros provedores de dados heterogêneos, como um provedor para um armazenamento de email.  
  
## <a name="urls"></a>URLs  
 Uniform Resource Locators (URLs) pode ser usado como uma alternativa para cadeias de caracteres de conexão e o texto de comando para especificar fontes de dados e o local dos arquivos e diretórios. Você pode usar URLs com existente [Conexão](../../../ado/reference/ado-api/connection-object-ado.md) e **registros** objetos e com o **registro** e **fluxo** objetos.  
  
 Para obter mais informações sobre como usar URLs, consulte [Absolute e URLs relativas](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="record-fields"></a>Campos de registro  
 A diferença de distinção entre dados heterogêneos e dados homogêneos destina-se que o primeiro, cada linha de dados, ou **registro**, pode ter um conjunto diferente de colunas, ou **campos**. Para dados homogêneos, cada linha tem o mesmo conjunto de colunas. Para obter mais informações sobre os campos específicos para o provedor de publicação, consulte [registros e campos extras Provider-Supplied](../../../ado/guide/data/records-and-provider-supplied-fields.md).  
  
### <a name="appending-new-fields"></a>Acrescentar novos campos  
 Vários objetos ADO foram aprimorados para trabalhar junto com **registro** e **fluxo** objetos.  
  
-   O [campos](../../../ado/reference/ado-api/fields-collection-ado.md) coleção [Append](../../../ado/reference/ado-api/append-method-ado.md) método, que cria e adiciona um [campo](../../../ado/reference/ado-api/field-object.md) objeto à coleção, também pode especificar o valor da **campo**.  
  
-   O [atualização](../../../ado/reference/ado-api/update-method.md) método finaliza a adição ou exclusão de campos para a coleção.  
  
-   Como um atalho e alternativa para o **Append** método, você pode criar campos atribuindo um valor para um campo indefinido ou excluído anteriormente.  
  
 Esta seção contém os tópicos a seguir.  
  
-   [O Provedor OLE DB para publicação na Internet](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)  
  
-   [Cenário de publicação na Internet](../../../ado/guide/data/internet-publishing-scenario.md)  
  
-   [URLs absolutas e relativas](../../../ado/guide/data/absolute-and-relative-urls.md)  
  
-   [Registros e campos fornecidos pelo provedor](../../../ado/guide/data/records-and-provider-supplied-fields.md)  
  
## <a name="see-also"></a>Consulte também  
 [Objeto de registro (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Objeto de fluxo (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)   
 [Histórico ADO](../../../ado/guide/ado-history.md)
