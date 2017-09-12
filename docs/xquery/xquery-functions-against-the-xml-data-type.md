---
title: "Funções XQuery em relação ao tipo de dados xml | Microsoft Docs"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- XQuery, functions
- xml data type [SQL Server], XQuery
- functions [SQL Server], XQuery
ms.assetid: 8df0877d-a03f-4ca9-b84e-908c4bb42b5e
caps.latest.revision: 37
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f950e3bbeb239537bc606c38469b9fb79e36837b
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="xquery-functions-against-the-xml-data-type"></a>Funções XQuery em tipos de dados xml
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Este tópico e seus subtópicos descrevem as funções que você pode usar ao especificar XQuery em relação a **xml** tipo de dados. Para as especificações do W3C, consulte [http://www.w3.org/TR/2004/WD-xpath-functions-20040723](http://go.microsoft.com/fwlink/?LinkId=4873).  
  
 As funções XQuery pertencem ao namespace http://www.w3.org/2004/07/xpath-functions. As especificações de W3C usam o prefixo de namespace "fn:" para descrever essas funções. Você não tem que especificar explicitamente o prefixo de namespace "fn:" quando estiver usando as funções. Por causa disso e para melhorar a legibilidade, os prefixos de namespace geralmente não são usados nesta documentação.  
  
 A tabela a seguir lista as funções XQuery que têm suporte em relação a **xml**tipo de dados.  
  
|Categoria|Nome da função|  
|--------------|-------------------|  
|[Funções em valores numéricos](http://msdn.microsoft.com/library/d5740a32-b174-43b9-b64d-1cc6edc50cff)|[Ceiling](../xquery/numeric-values-functions-ceiling.md)|  
||[Floor](../xquery/numeric-values-functions-floor.md)|  
||[Arredondar](../xquery/numeric-values-functions-round.md)|  
|[Funções XQuery em valores de cadeia de caracteres](http://msdn.microsoft.com/library/2dccefef-5d90-4f56-bda7-4c1954d8a730)|[concat](../xquery/functions-on-string-values-concat.md)|  
||[contém](../xquery/functions-on-string-values-contains.md)|  
||[subcadeia de caracteres](../xquery/functions-on-string-values-substring.md)|  
||[minúsculas função &#40; XQuery &#41;](../xquery/functions-on-string-values-lower-case.md)|  
||[comprimento de cadeia de caracteres](../xquery/functions-on-string-values-string-length.md)|  
||[Função &#40; de letras maiusculas XQuery &#41;](../xquery/functions-on-string-values-upper-case.md)|  
|Funções em valores boolianos|[não](../xquery/functions-on-boolean-values-not-function.md)|  
|[Funções em nós](http://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)|[número](../xquery/functions-on-nodes-number.md)|  
||[Função local-name (XQuery)](../xquery/functions-on-nodes-local-name.md)|  
||[Função namespace-uri (XQuery)](../xquery/functions-on-nodes-namespace-uri.md)|  
|[Funções de contexto](http://msdn.microsoft.com/library/f7d8af33-9de9-450c-a667-23dee3129b5f)|[último](../xquery/context-functions-last-xquery.md)|  
||[posição](../xquery/context-functions-position-xquery.md)|  
|[Funções em sequências](http://msdn.microsoft.com/library/672d2795-53ab-49c2-bf24-bc81a47ecd3f)|[vazio](../xquery/functions-on-sequences-empty.md)|  
||[valores distintos](../xquery/functions-on-sequences-distinct-values.md)|  
||[Função ID (XQuery)](../xquery/functions-on-sequences-id.md)|  
|[Funções de agregação &#40; XQuery &#41;](http://msdn.microsoft.com/library/be647ef1-291e-4a5d-ab18-07c759efe176)|[contagem](../xquery/aggregate-functions-count.md)|  
||[AVG](../xquery/aggregate-functions-avg.md)|  
||[min](../xquery/aggregate-functions-min.md)|  
||[Max](../xquery/aggregate-functions-max.md)|  
||[soma](../xquery/aggregate-functions-sum.md)|  
|[Funções de construtor &#40; XQuery &#41;](../xquery/constructor-functions-xquery.md)|[Funções de construtor](../xquery/constructor-functions-xquery.md)|  
|[Funções do Acessador de Dados](../xquery/data-accessor-functions.md)|[cadeia de caracteres](../xquery/data-accessor-functions-string-xquery.md)|  
||[dados](../xquery/data-accessor-functions-data-xquery.md)|  
|[Funções do construtor booliano &#40; XQuery &#41;](http://msdn.microsoft.com/library/fa907f39-d4b7-4495-b829-c788928e0f64)|[Função True (XQuery)](../xquery/boolean-constructor-functions-true-xquery.md)|  
||[Função False (XQuery)](../xquery/boolean-constructor-functions-false-xquery.md)|  
|[Funções relacionadas a QNames &#40; XQuery &#41;](http://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)|[Expanded-QName (XQuery)](../xquery/functions-related-to-qnames-expanded-qname.md)|  
||[local-nome-do-QName (XQuery)](../xquery/functions-related-to-qnames-local-name-from-qname.md)|  
||[namespace-uri-de-QName (XQuery)](../xquery/functions-related-to-qnames-namespace-uri-from-qname.md)|  
|[Funções de extensão XQuery do SQL Server](http://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)|[função SQL: Column (XQuery)](../xquery/xquery-extension-functions-sql-column.md)|  
||[função SQL: Variable (XQuery)](../xquery/xquery-extension-functions-sql-variable.md)|  
  
## <a name="see-also"></a>Consulte também  
 [Métodos de tipos de dados xml](../t-sql/xml/xml-data-type-methods.md)   
 [Referência de linguagem XQuery &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)   
 [Dados XML &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)  
  
  