---
title: MSSQLSERVER_1101 | Microsoft Docs
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
- 1101 (Database Engine error)
ms.assetid: d63b67d5-59f5-4f77-904e-5ba67f2dd850
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bfce911fe1d8efe6ad24e8fbfcea9f413b7bb4ee
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver1101"></a>MSSQLSERVER_1101
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalhes  
  
|||  
|-|-|  
|Nome do produto|SQL Server|  
|ID do evento|1101|  
|Origem do evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbólico|NOALLOCPG|  
|Texto da mensagem|Não foi possível alocar uma nova página ao banco de dados '%.*ls' devido a espaço em disco insuficiente no grupo de arquivos '%.\*ls'. Crie o espaço necessário descartando objetos no grupo de arquivos, adicionando arquivos ao grupo de arquivos ou definindo o aumento automático para arquivos existentes no grupo de arquivos.|  
  
## <a name="explanation"></a>Explicação  
Não há espaço disponível em disco em um grupo de arquivos.  
  
## <a name="user-action"></a>Ação do usuário  
As ações a seguir podem criar espaço disponível no grupo de arquivos.  
  
-   Ative o AUTOGROW.  
  
-   Adicione mais arquivos ao grupo de arquivos.  
  
-   Libere espaço em disco descartando índices ou tabelas desnecessários no grupo de arquivos.  
  
