---
title: Edição de registros existentes | Microsoft Docs
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- editing data [ADO], existing records
ms.assetid: 17ce1263-5897-452a-9ea5-c7f96b33df65
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6caa67868172118f7e70b1781b7fbb08ec22641
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="editing-existing-records"></a>Editar os registros existentes
Para editar os registros existentes, mova para a linha que você deseja editar e alterar o **valor** propriedade dos campos que você deseja alterar. Para obter mais informações sobre o **campo** do objeto **valor** propriedade, consulte [examinando dados](../../../ado/guide/data/examining-data.md). Dependendo de seu tipo de cursor, você usará **atualização** ou **UpdateBatch** para enviar as alterações de volta para a fonte de dados. Para obter mais informações, consulte [atualizando e persistir dados](../../../ado/guide/data/updating-and-persisting-data.md).  
  
 É geralmente mais eficiente usar um procedimento armazenado com um objeto de comando para executar atualizações, bem como para executar outras operações, como um procedimento armazenado não exige a criação de um cursor. Para obter mais informações sobre cursores, consulte [Noções básicas sobre cursores e bloqueios](../../../ado/guide/data/understanding-cursors-and-locks.md).