---
title: "Usando as anotações SQL: Identity e | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- sql:guid
- annotated XSD schemas, IDENTITY-type columns
- annotated XSD schemas, GUID values
- DiffGrams [SQLXML], annotations
- identity annotation
- XSD schemas [SQLXML], GUID values
- GUIDs [SQLXML]
- guid annotation
- sql:identity
- IDENTITY-type column
- XSD schemas [SQLXML], IDENTITY-type columns
- updategrams [SQLXML], GUID values
ms.assetid: 7661dfd0-6573-4692-a8f1-3597adcd33c4
caps.latest.revision: "24"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8a40eb7a4573ea11b597860f8ea4005fc5908bdb
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a>Usando as anotações sql:identity e sql:guid
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Você pode especificar o **Identity** e **SQL** anotações em um esquema XSD em qualquer nó que mapeia para uma coluna de banco de dados em [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Enquanto o formato do diagrama de atualização oferece suporte a **updg: a identidade** e **updg: GUID** atributos, o formato DiffGram não. O **updg: a identidade** atributo define o comportamento ao atualizar uma coluna de tipo de identidade. O **updg: GUID** atributo permite obter um valor GUID da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e usá-lo no diagrama de atualização. Para obter mais informações e exemplos de funcionamento, consulte [inserindo dados usando diagramas de atualização XML &#40; SQLXML 4.0 &#41; ](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
 O **Identity** e **SQL** anotações estendem essa funcionalidade a DiffGrams.  
  
 Quando você executa um DiffGram, ele é primeiro convertido em um diagrama de atualização e, em seguida, o diagrama de atualização é executado. Especificando o **Identity** e **SQL** anotações no esquema XSD, você está na verdade definindo o comportamento de um diagrama de atualização. Assim, todas as anotações são descritas no contexto de um diagrama de atualização. As anotações podem ser usadas para DiffGrams e diagramas de atualização; entretanto, os diagramas de atualização já fornecem um modo mais avançado de tratar valores de GUID e identidade.  
  
 O **Identity** e **SQL** anotações podem ser definidas em um elemento de conteúdo complexo.  
  
## <a name="sqlidentity-annotation"></a>Anotação sql:identity  
 Você pode especificar o **Identity** anotação no esquema XSD em qualquer nó que mapeia para uma coluna de banco de dados do tipo de identidade. O valor especificado para esta anotação define como a coluna do tipo IDENTITY é atualizada (usando o valor fornecido no diagrama de atualização para modificar a coluna ou ignorando o valor; nesse caso, um valor gerado pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] será usado para esta coluna).  
  
 O **Identity** anotação pode ser atribuída a dois valores:  
  
 ignore  
 Direciona o diagrama de atualização para ignorar qualquer valor que seja fornecido no diagrama de atualização para essa coluna e para depender do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para gerar o valor da identidade.  
  
 useValue  
 Direciona o diagrama de atualização para usar o valor que é fornecido no diagrama de atualização para atualizar a coluna do tipo IDENTITY. Um diagrama de atualização não verifica se a coluna é um valor de identidade ou não.  
  
 Se o diagrama Especifica um valor para a coluna de tipo de identidade, o **Identity = "useValue"** deve ser especificado no esquema.  
  
## <a name="sqlguid-annotation"></a>Anotação sql:guid  
 Um diagrama de atualização pode fazer o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gerar um valor de GUID e então usar esse valor no diagrama de atualização. No contexto de DiffGrams, você pode usar o **SQL** anotação para especificar se deseja usar um valor GUID que é gerado pelo SQL Server ou usar o valor que é fornecido no diagrama de atualização para essa coluna.  
  
 O **SQL** anotação pode ser atribuída a dois valores:  
  
 generate  
 Especifica que o GUID gerado pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] seja usado para essa coluna na operação de atualização.  
  
 useValue  
 Especifica que o valor especificado no diagrama de atualização seja usado para a coluna. Este é o valor padrão.  
  
  