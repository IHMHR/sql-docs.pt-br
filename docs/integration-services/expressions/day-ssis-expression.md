---
title: DAY (Expressão SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: expressions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- DAY function
- dates [Integration Services], DAY
ms.assetid: d8447187-49df-45b7-a98e-142ad44fd3e2
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 95bf0d009a9d93c0ffc03f95265fbe7cf89e0c17
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="day-ssis-expression"></a>DAY (Expressão SSIS)
  Retorna um inteiro que representa a parte do dia em uma data.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
DAY(date)  
```  
  
## <a name="arguments"></a>Argumentos  
 *date*  
 É uma expressão que retorna uma data válida ou uma cadeia de caracteres em formato de data.  
  
## <a name="result-types"></a>Tipos de resultado  
 DT_I4  
  
## <a name="remarks"></a>Remarks  
 DAY retornará um resultado nulo se o argumento for nulo.  
  
 Um literal de data deve ser convertido explicitamente em um dos tipos de dados de data. Para obter mais informações, consulte [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
> [!NOTE]  
>  A expressão não é validada quando um literal de data é convertido explicitamente em um destes tipos de dados de data: DT_DBTIMESTAMPOFFSET e DT_DBTIMESTAMP2.  
  
 A função DAY é mais resumida, mas equivale a usar a DATEPART ("Dia", data).  
  
## <a name="expression-examples"></a>Exemplos de expressões  
 Este exemplo retorna o número do dia em um literal de data. Se a data estiver no formato "mm/dd/aaaa", este exemplo retornará 23.  
  
```  
DAY((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 Este exemplo retorna o inteiro que representa o dia na coluna **ModifiedDate** .  
  
```  
DAY(ModifiedDate)  
```  
  
 Este exemplo retorna o inteiro que representa o dia da data atual.  
  
```  
DAY(GETDATE())  
```  
  
## <a name="see-also"></a>Consulte Também  
 [DATEADD &#40;Expressão do SSIS&#41;](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEDIFF &#40;Expressão do SSIS&#41;](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART &#40;Expressão do SSIS&#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [MONTH &#40;Expressão do SSIS&#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [YEAR &#40;Expressão do SSIS&#41;](../../integration-services/expressions/year-ssis-expression.md)   
 [Funções &#40;Expressão do SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
