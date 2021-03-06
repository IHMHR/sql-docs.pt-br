---
title: APP_NAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- APP_NAME_TSQL
- APP_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- name checking for current session [SQL Server]
- sessions [SQL Server], application names
- applications [SQL Server], names
- current session application names
- APP_NAME function
ms.assetid: e491e192-9b30-4243-bc19-33c133fe08a8
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9d9652c25875fb1edb5d09e4e283fd7393b523a6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="appname-transact-sql"></a>APP_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Uma função que retorna o nome do aplicativo para a sessão atual, se o aplicativo define esse valor de nome.
  
> [!IMPORTANT]  
>  O cliente fornece o nome do aplicativo e o valor do nome de aplicativo não é verificado de nenhuma forma. Não use **APP_NAME** como parte de uma verificação de segurança.  
  
![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxe  
  
```sql
  
APP_NAME  ( )  
```  
  
## <a name="return-types"></a>Tipos de retorno  
**nvarchar(128)**
  
## <a name="remarks"></a>Remarks  
Use a **APP_NAME** para distinguir entre diferentes aplicativos, como uma maneira de executar ações diferentes para esses aplicativos. Por exemplo, **APP_NAME** pode distinguir entre diferentes aplicativos para permitir um formato de data diferente para cada aplicativo. Ela também pode permitir o retorno de uma mensagem informativa para determinados aplicativos.
  
Para definir um nome de aplicativo no [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], clique em **Opções** na caixa de diálogo **Conectar ao Mecanismo de Banco de Dados**. Na guia **Parâmetros de Conexão Adicionais**, forneça um atributo **app** no formato `;app='application_name'`
  
## <a name="example"></a>Exemplo  
Esse exemplo verifica se o aplicativo cliente que iniciou esse processo é uma sessão do `SQL Server Management Studio` e fornece uma data no formato US ou ANSI.
  
```sql
USE AdventureWorks2012;  
GO  
IF APP_NAME() = 'Microsoft SQL Server Management Studio - Query'  
PRINT 'This process was started by ' + APP_NAME() + '. The date is ' + CONVERT ( varchar(100) , GETDATE(), 101) + '.';  
ELSE   
PRINT 'This process was started by ' + APP_NAME() + '. The date is ' + CONVERT ( varchar(100) , GETDATE(), 102) + '.';  
GO  
```  
  
## <a name="see-also"></a>Confira também
[Funções do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
[Funções](../../t-sql/functions/functions.md)
  
  
