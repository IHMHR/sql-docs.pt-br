---
title: Opções de Validação de Assinatura (assinaturas transacionais) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.validate.options.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: fd66ad1f-df01-4240-9e89-8f41bff12c1e
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 546a8f6e13cef68a25de66b1a9a75bb9d582a3d9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="subscription-validation-options-transactional-subscriptions"></a>Opções de Validação de Assinatura (assinaturas transacionais)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Use a caixa de diálogo **Opções de Validação de Assinatura** para especificar se a validação deve usar somente uma contagem de linha ou uma contagem de linhas e uma soma de verificação binária.  
  
## <a name="options"></a>Opções  
 **Verifique se o Assinante tem o mesmo número de linhas dos dados replicados que o Publicador**  
 Selecione o tipo de validação de contagem de linhas a ser executado. Para publicações Oracle, a única opção disponível é **Calcular uma contagem de linhas real consultando as tabelas diretamente**.  
  
 **Comparar as somas de verificação para verificar os dados da linha**  
 Além de contar o número de linhas no Publicador e no Assinante, uma soma de verificação de todos os dados é calculada usando o algoritmo de soma de verificação binária. Se a contagem de linhas falhar, a soma de verificação não será executada.  
  
 **Interromper o Distribution Agent após a conclusão da validação**  
 Por padrão, o Distribution Agent executa continuamente. Selecione essa opção para interromper o agente depois que validação for executada. Isso permite verificar se validação teve êxito antes de continuar replicando dados para o Assinante.  
  
## <a name="see-also"></a>Consulte Também  
 [Validar dados no assinante](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [Validar os dados replicados](../../relational-databases/replication/validate-replicated-data.md)  
  
  
