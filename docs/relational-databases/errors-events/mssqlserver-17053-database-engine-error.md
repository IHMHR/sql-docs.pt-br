---
title: MSSQLSERVER_17053 | Microsoft Docs
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
- 17053 (Database Engine error)
ms.assetid: e0a01f3d-d0aa-4c38-8bcc-82e59de50512
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 50ab0081458e3d370741a46e8ab65b51ea61357a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver17053"></a>MSSQLSERVER_17053
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalhes  
  
|||  
|-|-|  
|Nome do produto|SQL Server|  
|ID do evento|17053|  
|Origem do evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbólico|OS_ERROR|  
|Texto da mensagem|%ls: %ls erros do sistema operacional foram encontrados.|  
  
## <a name="explanation"></a>Explicação  
Ocorreu um erro genérico do sistema operacional.  Não desmarque a informação resultante.  
  
## <a name="user-action"></a>Ação do usuário  
Normalmente, isso ocorre com algum outro erro e pode ser usado para ajudar a diagnosticar essa falha. Os exemplos podem incluir falhas em leituras ou gravações de dados ou em arquivos de log, operações de leitura/gravação no Registro ou outras falhas inesperadas da Win32API.  
  
