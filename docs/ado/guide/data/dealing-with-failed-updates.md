---
title: Lidando com atualizações com falha | Microsoft Docs
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
- updates [ADO], dealing with failed updates
ms.assetid: 299c37bd-19ff-4261-8571-b9665687e075
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1cd4088f20c949cd3a732b43cd5d9312c04387ef
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="dealing-with-failed-updates"></a>Lidando com atualizações com falha
Quando uma atualização é concluída com erros, como resolver os erros depende a natureza e a severidade dos erros e a lógica do seu aplicativo. No entanto, se o banco de dados for compartilhado com outros usuários, um erro comum é que outra pessoa modificar o campo antes de fazer. Esse tipo de erro é chamado de um conflito. ADO detectará essa situação e relata um erro.  
  
## <a name="remarks"></a>Remarks  
 Se houver erros de atualização, eles serão capturados em uma rotina de tratamento de erros. Filtre o conjunto de registros com a constante adFilterConflictingRecords para que somente as linhas conflitantes são visíveis. Neste exemplo, a estratégia de resolução de erro é apenas imprimir o autor nomes e sobrenomes (au_fname e au_lname).  
  
 O código para alertar o usuário para o conflito de atualização tem esta aparência:  
  
```  
objRs.Filter = adFilterConflictingRecords  
objRs.MoveFirst  
Do While Not objRst.EOF  
   Debug.Print "Conflict: Name =  "; objRs!au_fname; " "; objRs!au_lname  
   objRs.MoveNext  
Loop  
```  
  
## <a name="see-also"></a>Consulte também  
 [Modo de lote](../../../ado/guide/data/batch-mode.md)
