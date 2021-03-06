---
title: Usando anotações em esquemas XSD (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, about annotated XSD schemas
- annotations [SQLXML]
- relationships [SQLXML]
- relationships [SQLXML], hierarchical relationships
- hierarchical relationships [SQLXML]
- mapping schema [SQLXML], scenarios for using
ms.assetid: 78f318a4-7a36-473b-9852-a4bae6940ce5
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: f3e44d91a958441e421259b7257df49f14883eb0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="using-annotations-in-xsd-schemas-sqlxml-40"></a>Usando anotações em esquemas XSD (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  No [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0, a linguagem de esquema XSD dá suporte a anotações de forma semelhante às anotações introduzidas na linguagem de esquema XDR (XML-Data Reduced). Há anotações adicionais introduzidas no XSD para as quais não há suporte no XDR.  
  
 Essas anotações podem ser usadas dentro do esquema XSD para especificar o mapeamento de XML para relacional. Isso inclui o mapeamento entre elementos e atributos no esquema XSD para tabelas (exibições) e colunas nos bancos de dados.  
  
 Se você não especificar as anotações, será utilizado o mapeamento padrão. Por padrão, um elemento XSD com um tipo complexo é mapeado para um nome de tabela (exibição) no banco de dados especificado, e um elemento ou atributo com um tipo simples é mapeado para a coluna com o mesmo nome que o elemento ou o atributo.  
  
 Essas anotações também podem ser usadas para especificar as relações hierárquicas em XML, representando assim as relações no banco de dados, pois um esquema XSD é simplesmente uma exibição XML de dados relacionais.  
  
 Esta seção fornece descrições das anotações que podem ser usadas com esquemas XSD e exemplos de sua utilização.  
  
> [!NOTE]  
>  Todos os exemplos nesta seção especificam consultas XPath simples no esquema XSD anotado descrito em cada exemplo. É presumido que haja familiaridade com a linguagem XPath.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Anotações XSD &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/xsd-annotations-sqlxml-4-0.md)  
 Lista as anotações que podem ser usadas com esquemas XSD, suas descrições e as anotações equivalentes para XDR.  
  
 [Mapeamento de padrão de atributos e elementos XSD para tabelas e colunas &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
 Explica o mapeamento padrão e fornece exemplos de tarefas relacionados a ele.  
  
 [Mapeamento explícito de atributos e elementos XSD para tabelas e colunas &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns.md)  
 Explica o mapeamento explícito com o **SQL: Relation** e **SQL: Field** anotações e fornece exemplos.  
  
 [Especificando relações usando SQL: Relationship &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
 Descreve e fornece exemplos do **SQL: Relationship** anotação.  
  
 [Especificando o atributo SQL: Inverse em SQL: Relationship &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)  
 Descreve o **SQL: Inverse** anotação.  
  
 [Criando elementos constantes usando sql: constante é &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)  
 Descreve e fornece exemplos do **sql: constante é** anotação.  
  
 [Excluindo elementos de esquema do documento XML resultante usando sql: mapeado &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)  
 Descreve e fornece exemplos do **sql: mapeado** anotação.  
  
 [Filtrando valores usando SQL: limit-campo e SQL: limit-valor &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/filtering-values-using-sql-limit-field-and-sql-limit-value-sqlxml-4-0.md)  
 Descreve e fornece exemplos do **SQL: limit-campo** e **SQL: limit-valor** anotações.  
  
 [Identificando colunas de chave usando SQL: Key-campos &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)  
 Descreve e fornece exemplos do **SQL: Key-campos** anotação.  
  
 [Especificar um destino Namespace usando o atributo targetNamespace &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
 Descreve e fornece exemplos do **targetNamespace** atributo.  
  
 [Criando válido ID, IDREF e IDREFS tipo atributos usando SQL: prefix &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)  
 Descreve e fornece exemplos do **SQL: prefix** anotação.  
  
 [Coerções de tipo de dados e a anotação SQL: DataType &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)  
 Descreve e fornece exemplos do **SQL: DataType** anotação.  
  
 [Mapeando tipos de dados XSD para tipos de dados XPath &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/mapping-xsd-data-types-to-xpath-data-types-sqlxml-4-0.md)  
 Fornece uma tabela que compara tipos de dados XSD, XDR e XPath e lista as conversões relevantes do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Criando seções CDATA usando SQL: Use-cdata &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)  
 Descreve e fornece exemplos do **SQL: Use-dados** anotação.  
  
 [Solicitando referências URL a dados BLOB usando sql: encode &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)  
 Descreve e fornece exemplos do **sql: encode** anotação.  
  
 [Recuperando dados não consumidos usando SQL: overflow-campo &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/retrieving-unconsumed-data-using-the-sql-overflow-field-sqlxml-4-0.md)  
 Descreve e fornece exemplos do **SQL: overflow-campo** anotação.  
  
 [Ocultando elementos e atributos usando sql:hide](../../relational-databases/sqlxml-annotated-xsd-schemas-using/hiding-elements-and-attributes-by-using-sql-hide.md)  
 Descreve e fornece exemplos do **SQL: Hide** anotação.  
  
 [Usando as anotações sql:identity e sql:guid](../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-the-sql-identity-and-sql-guid-annotations.md)  
 Descreve e fornece exemplos do **Identity** e **SQL** anotações.  
  
 [Especificando a profundidade em relações recursivas usando sql:max-depth](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)  
 Descreve e fornece exemplos do **SQL: max-profundidade** anotação.  
  
## <a name="see-also"></a>Consulte também  
 [Anotado considerações de segurança do esquema &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)  
  
  
