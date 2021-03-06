---
title: Usando modos de lote e AddNew em imediata | Microsoft Docs
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
- AddNew method [ADO]
- ADO, editing data
- ADO, adding data
- editing data [ADO], AddNew method
ms.assetid: ed314bb9-e188-4658-a68c-a2abc49610be
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c66b250780e3b12ae9590796a062426f89920de
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="using-addnew-in-immediate-and-batch-modes"></a>Usando modos de lote e AddNew em imediata
O comportamento do **AddNew** método depende do modo de atualização do **Recordset** objeto e se você passa o *FieldList* e *valores*argumentos.  
  
 No modo de atualização imediata (no qual o provedor grava as alterações à fonte de dados subjacente quando você chamar o **atualizar** método), chamar o **AddNew** método sem conjuntos de argumentos de  **EditMode** propriedade **adEditAdd.** O provedor armazena em cache localmente as alterações de valor de campo. Chamando o **atualização** método posta o novo registro no banco de dados e redefine o **EditMode** propriedade **adEditNone.** Se você passar o *FieldList* e *valores* argumentos, o ADO envia imediatamente o novo registro no banco de dados (sem **atualização** chamada é necessária); o **EditMode**  não altera o valor da propriedade (**adEditNone**).  
  
 No modo de atualização em lotes, chamando o **AddNew** método sem conjuntos de argumentos de **EditMode** propriedade **adEditAdd**. O provedor armazena em cache localmente as alterações de valor de campo. Chamando o **atualização** método adiciona o novo registro para o atual **registros** e redefine o **EditMode** propriedade **adEditNone**, mas o provedor não postar as alterações no banco de dados subjacentes até que você chame o **UpdateBatch** método. Se você passar o *FieldList* e *valores* argumentos, ADO envia o novo registro para o provedor de armazenamento em cache; você precisa chamar o **UpdateBatch** método para lançar o novo Registre o banco de dados subjacente. Para obter mais informações sobre **atualização** e **UpdateBatch**, consulte [atualizando e persistir dados](../../../ado/guide/data/updating-and-persisting-data.md).
