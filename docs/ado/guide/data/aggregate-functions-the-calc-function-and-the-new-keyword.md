---
title: Agregar funções, a função de CÁLCULO e a nova palavra-chave | Microsoft Docs
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
- data shaping [ADO], functions
- CALC function [ADO]
- NEW keyword [ADO]
- aggregate functions [ADO]
ms.assetid: 0590b466-2a36-49a2-868e-028ef5e49394
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1e3af3e37caacae09f4ee57bc251f7ebcabfb04e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="aggregate-functions-the-calc-function-and-the-new-keyword"></a>Funções de agregação, a função de CÁLCULO e a palavra-chave NEW
Modelagem de dados oferece suporte a funções a seguir. O nome atribuído o capítulo que contém a coluna a ser operado é o *capítulo alias*.  
  
 Um alias de capítulo pode ser totalmente qualificado, consistindo de cada nome de coluna de capítulo à esquerda até o capítulo que contém o *nome de coluna,* todos separados por pontos. Por exemplo, se o capítulo pai, Cap1, contém um capítulo filho, chap2, que tem uma coluna de quantidade amt, e o nome qualificado seria chap1.chap2.amt.  
  
|Funções de agregação|Description|  
|-------------------------|-----------------|  
|SUM (*capítulo alias*. *nome da coluna*)|Calcula a soma de todos os valores na coluna especificada.|  
|AVG(*chapter-alias*.*column-name*)|Calcula a média de todos os valores na coluna especificada.|  
|MAX(*chapter-alias*.*column-name*)|Calcula o valor máximo na coluna especificada.|  
|MIN(*chapter-alias*.*column-name*)|Calcula o valor mínimo na coluna especificada.|  
|CONTAGEM (*capítulo alias*[. *nome da coluna*])|Conta o número de linhas em que o alias especificado. Se uma coluna for especificada, somente as linhas para o qual essa coluna é Null não são incluídas na contagem.|  
|STDEV(*chapter-alias*.*column-name*)|Calcula o desvio padrão da coluna especificada.|  
|ANY(*chapter-alias*.*column-name*)|Um valor da coluna especificada. QUALQUER tem um valor previsível somente quando o valor da coluna é o mesmo para todas as linhas do capítulo.<br /><br /> **Observação** se a coluna não contiver o mesmo valor para todas as linhas do capítulo, o comando de forma arbitrariamente retorna um dos valores como o valor de qualquer função.|  
  
|expressão calculada|Description|  
|---------------------------|-----------------|  
|CÁLCULO (*expressão*)|Calcula uma expressão arbitrária, mas apenas na linha do **registros** que contém a função de CÁLCULO. Qualquer expressão usando esses [do Visual Basic for Applications (VBA) funções](../../../ado/guide/data/visual-basic-for-applications-functions.md) é permitido.|  
  
|Palavra-chave NEW|Description|  
|-----------------|-----------------|  
|NOVO *tipo de campo* [(*largura* &#124; *escala* &#124; *precisão* &#124; *erro*[, *escala* &#124; *erro*])]|Adiciona uma coluna vazia do tipo especificado para o **registros**.|  
  
 O *tipo de campo* passado com a nova palavra-chave pode ser qualquer um dos seguintes tipos de dados.  
  
|Tipos de dados OLE DB|Tipo de dados de ADO equivalent(s)|  
|-----------------------|-----------------------------------|  
|DBTYPE_BSTR|adBSTR|  
|DBTYPE_BOOL|adBoolean|  
|DBTYPE_DECIMAL|adDecimal|  
|DBTYPE_UI1|adUnsignedTinyInt|  
|DBTYPE_I1|adTinyInt|  
|DBTYPE_UI2|adUnsignedSmallInt|  
|DBTYPE_UI4|adUnsignedInt|  
|DBTYPE_I8|adBigInt|  
|DBTYPE_UI8|adUnsignedBigInt|  
|DBTYPE_GUID|adGuid|  
|DBTYPE_BYTES|adBinary, AdVarBinary, adLongVarBinary|  
|DBTYPE_STR|adChar, adVarChar, adLongVarChar|  
|DBTYPE_WSTR|adWChar, adVarWChar, adLongVarWChar|  
|DBTYPE_NUMERIC|adNumeric|  
|DBTYPE_DBDATE|adDBDate|  
|DBTYPE_DBTIME|adDBTime|  
|DBTYPE_DBTIMESTAMP|adDBTimeStamp|  
|DBTYPE_VARNUMERIC|adVarNumeric|  
|DBTYPE_FILETIME|adFileTime|  
|DBTYPE_ERROR|adError|  
  
 Quando o novo campo é do tipo decimal (OLE DB, DBTYPE_DECIMAL, ou no ADO, adDecimal), você deve especificar os valores de precisão e escala.  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de modelagem de dados](../../../ado/guide/data/data-shaping-example.md)   
 [Gramática de forma formal](../../../ado/guide/data/formal-shape-grammar.md)   
 [Modelar comandos em geral](../../../ado/guide/data/shape-commands-in-general.md)
