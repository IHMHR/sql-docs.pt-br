---
title: Instruções RESTORE para restaurar, recuperar e gerenciar backups (T-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- restoring files [SQL Server], RESTORE statement
- RESTORE statement, about restore operations
- database restores [SQL Server], RESTORE statement
- restoring databases [SQL Server], RESTORE statement
- database backups [SQL Server], RESTORE statement
- backing up databases [SQL Server], RESTORE statement
- file restores [SQL Server], RESTORE statement
- transaction log backups [SQL Server], RESTORE statement
ms.assetid: fb29a151-f312-4f85-b857-5deeca0de8ce
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 003f3adce58a228e4965f91c1104ff33b60b8398
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="restore-statements-for-restoring-recovering-and-managing-backups-transact-sql"></a>instruções RESTORE para restaurar, recuperar e gerenciar backups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdbmi-xxxx-xxx-md.md )]

  Esta seção descreve as instruções RESTORE para backups. Além da instrução RESTORE {DATABASE | LOG} principal para restaurar e recuperar backups, várias instruções RESTORE auxiliares podem ajudá-lo a gerenciar seus backups e a planejar suas sequências de restauração. São comandos RESTORE auxiliares: RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY, RESTORE REWINDONLY e RESTORE VERIFYONLY.  
  
[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]

> [!IMPORTANT]  
>  Em versões anteriores do SQL Server, qualquer usuário poderia obter informações sobre conjuntos e dispositivos de backup usando as instruções Transact-SQL RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY e RESTORE VERIFYONLY. Como elas revelam informações sobre o conteúdo dos arquivos de backup, no [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e em versões posteriores, essas instruções exigem a permissão CREATE DATABASE. Com essa exigência, seus arquivos e suas informações de backup estão mais protegidos do que nas versões anteriores. Para obter informações sobre essa permissão, veja [Permissões de banco de dados GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
## <a name="in-this-section"></a>Nesta seção  
  
|de|Description|  
|---------------|-----------------|  
|[RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)|Descreve as instruções de Transact-SQL RESTORE DATABASE e RESTORE LOG usadas para restaurar e recuperar um banco de dados de backups obtidos por meio do comando BACKUP. RESTORE DATABASE é usado para bancos de dados sob modelos de recuperação. RESTORE LOG é usado apenas sob os modelos de recuperação completa e com log de operações em massa. RESTORE DATABASE também pode ser usado para reverter um banco de dados a um instantâneo do banco de dados.|  
|[Argumentos de RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md)|Documenta os argumentos descritos nas seções de "Sintaxe" da instrução RESTORE e do conjunto associado de instruções auxiliares: RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY, RESTORE REWINDONLY e RESTORE VERIFYONLY. Há suporte para a maioria dos argumentos apenas por um subconjunto dessas seis instruções. O suporte a cada argumento é indicado na descrição do argumento.|  
|[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)|Descreve a instrução de Transact-SQL RESTORE FILELISTONLY, que é usada para retornar um conjunto de resultados contendo uma lista dos bancos de dados e arquivos de log contidas no conjunto de backups.|  
|[RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)|Descreve a instrução de Transact-SQL RESTORE HEADERONLY, que é usada para retornar um conjunto de resultados que contém todas as informações de cabeçalho de backup de todos os conjuntos de backups em um dispositivo de backup em particular.|  
|[RESTORE LABELONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-labelonly-transact-sql.md)|Descreve a instrução de Transact-SQL RESTORE LABELONLY, que é usada para retornar um conjunto de resultados contendo informações sobre a mídia de backup identificada pelo dispositivo de backup determinado.|  
|[RESTORE REWINDONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)|Descreve a instrução de Transact-SQL RESTORE REWINDONLY, que é usada para retroceder e fechar dispositivos de fita que foram deixados abertos pelas instruções BACKUP ou RESTORE executadas com a opção NOREWIND.|  
|[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)|Descreve a instrução de Transact-SQL RESTORE VERIFYONLY, que é usada para verificar o backup, mas não o restaura, e examina se o conjunto de backup está completo e se todo o backup está legível; não tenta verificar a estrutura dos dados.|  
  
## <a name="see-also"></a>Consulte Também  
 [Fazer backup e restaurar bancos de dados do SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  
