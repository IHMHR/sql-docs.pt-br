---
title: Iniciar o Utilitário sqlcmd | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology:
- database-engine
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
caps.latest.revision: 41
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 09c222a27879ac90871be7f84314a675b3fe6be2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sqlcmd---start-the-utility"></a>sqlcmd – Iniciar o utilitário
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  O utilitário [sqlcmd](../../tools/sqlcmd-utility.md) permite digitar instruções [!INCLUDE[tsql](../../includes/tsql-md.md)] , procedimentos do sistema e arquivos de script no prompt de comando, no Editor de Consultas em modo SQLCMD, em um arquivo de script do Windows ou em uma etapa de trabalho do sistema operacional (Cmd.exe) de um trabalho do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.
> [!NOTE]  
>  A Autenticação do Windows é o modo de autenticação padrão do **sqlcmd**. Para usar a Autenticação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , você deve especificar um nome de usuário e uma senha usando as opções **-U** e **-P** .  
  
> [!NOTE]  
>  Por padrão, o [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] é instalado como a instância nomeada **sqlexpress**.  
  
### <a name="start-the-sqlcmd-utility-and-connect-to-a-default-instance-of-sql-server"></a>Inicie o utilitário sqlcmd e conecte-se a uma instância padrão do SQL Server  
  
1.  No menu **Iniciar** , clique em **Executar**. Na caixa **Abrir** digite **cmd**e, então, clique em **OK** para abrir uma janela do prompt de comando. (Caso não tenha se conectado a essa instância do [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] anteriormente, você poderá precisar configurar o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para aceitar conexões.)  
  
2.  No prompt de comando, digite **sqlcmd**.  
  
3.  Pressione ENTER.  
  
     Agora você tem uma conexão confiável com a instância padrão do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que está sendo executada em seu computador.  
  
     **1>** é o prompt do **sqlcmd** que especifica o número de linha. A cada vez que você pressiona ENTER, aparece um número seguinte ao anterior.  
  
4.  Para encerrar a sessão **sqlcmd** , digite **EXIT** no prompt **sqlcmd** .  
  
### <a name="start-the-sqlcmd-utility-and-connect-to-a-named-instance-of-sql-server"></a>Inicie o utilitário sqlcmd e se conectar a uma instância nomeada do SQL Server  
  
1.  Abra uma janela do prompt de comando e digite **sqlcmd -S***myServer\instanceName*. Substitua *myServer\instanceName* pelo nome do computador e a instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] com a qual você deseja se conectar.  
  
2.  Pressione ENTER.  
  
     O prompt do **sqlcmd** (1>) indica que você está conectado à instância especificada do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    > [!NOTE]  
    >  As instruções [!INCLUDE[tsql](../../includes/tsql-md.md)] digitadas são armazenadas em um buffer. Elas são executadas como um lote quando o comando GO é encontrado.  
  
## <a name="see-also"></a>Consulte Também  
 [Executar arquivos de script Transact-SQL usando sqlcmd](../../relational-databases/scripting/sqlcmd-run-transact-sql-script-files.md)  
  
  
