---
title: Elemento BeginTransaction (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d8f88c11759ae746bbe6bb586fdb467d96b70f1e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="begintransaction-element-xmla"></a>Elemento BeginTransaction (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Inicia uma transação na sessão atual com uma instância do [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
  
<Command>  
   <BeginTransaction />  
</Command>  
```  
  
## <a name="element-characteristics"></a>Características do elemento  
  
|Característica|Descrição|  
|--------------------|-----------------|  
|Comprimento e tipo de dados|Nenhuma|  
|Valor padrão|Nenhuma|  
|Cardinalidade|0-n: Elemento opcional que pode ocorrer mais de uma vez.|  
  
## <a name="element-relationships"></a>Relações do elemento  
  
|Relação|Elemento|  
|------------------|-------------|  
|Elementos pai|[Comando](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Elementos filho|Nenhuma|  
  
## <a name="remarks"></a>Remarks  
 O **BeginTransaction** comando inicia uma transação ativa na sessão atual. Se uma transação ativa já existir, a instância do [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] aumentará a contagem de referência de transações para a sessão atual. Se não existir, a instância iniciará uma nova transação e definirá a contagem de referência de sessão atual como 1. Se uma transação ativa for explicitamente especificada usando o **BeginTransaction** de comando, todos os comandos subsequentes serão executados na transação especificada explicitamente.  
  
 Quando a sessão atual for encerrada e a contagem de referência de transações for maior que zero, todas as transações ativas serão revertidas.  
  
 Se não houver nenhuma transação ativa especificada explicitamente na sessão atual, cada comando emitido na sessão atual será executando em uma transação definida implicitamente. A transação implícita é confirmada se o comando tiver sucesso ou revertida se o comando falhar.  
  
## <a name="see-also"></a>Consulte também  
 [Elemento Cancel &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [Elemento CommitTransaction &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)   
 [Elemento RollbackTransaction &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)   
 [Comandos & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
