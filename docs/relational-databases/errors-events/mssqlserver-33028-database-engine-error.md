---
title: MSSQLSERVER_33028 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 33028 (Database Engine error)
ms.assetid: c5cec0e4-0bcd-4907-826f-e7d835cfcb37
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c04a937f0275f4fb310836b9dbde5ebe7f76f681
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver33028"></a>MSSQLSERVER_33028
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalhes  
  
|||  
|-|-|  
|Nome do produto|SQL Server|  
|ID do evento|33028|  
|Origem do evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbólico|SEC_CRYPTOPROV_CANTOPENSESSION|  
|Texto da mensagem|Não é possível abrir a sessão para %S_MSG '%.*ls'. Código de erro do provedor: %d.|  
  
## <a name="explanation"></a>Explicação  
O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] não pôde abrir o provedor criptográfico listado na mensagem de erro. O provedor criptográfico forneceu o código de erro listado. Você talvez precise contatar seu provedor criptográfico para obter mais informações sobre o erro.  
  
|Código do erro|Description|  
|--------------|---------------|  
|0|Sucesso. Nenhum erro.|  
|1|Falha. Ocorreu um erro não especificado ou inesperado. Não há informações adicionais disponíveis.|  
|2|Buffer insuficiente. Não foi possível alocar espaço para o provedor criptográfico.|  
|3|Sem suporte. Não há suporte para o provedor criptográfico nesta versão. Selecione outro provedor criptográfico.|  
|4|Não encontrado. O provedor criptográfico especificado não está presente ou você não tem autorização para acessar os arquivos.|  
|5|Falha de autorização. Talvez uma senha ou um nome de usuário incorreto tenha sido fornecido durante a criação da credencial. Pode ocorrer quando a credencial não existe.|  
|6|Argumento inválido. Um argumento inválido foi passado ao provedor criptográfico.|  
  
## <a name="user-action"></a>Ação do usuário  
Resolva o erro ou contate o provedor criptográfico para obter mais informações.  
  
