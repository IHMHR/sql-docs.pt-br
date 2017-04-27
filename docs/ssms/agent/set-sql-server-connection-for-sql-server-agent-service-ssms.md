---
title: "Definir a conexão do SQL Server para o Serviço SQL Server Agent | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, connections
- connections [SQL Server], SQL Server Agent service
ms.assetid: 28b6178b-0a9e-4f2c-8562-7a62d2d2a285
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4129f5324f4b93efb98e9bd437571daa0bc404a1
ms.lasthandoff: 04/11/2017

---
# <a name="set-the-sql-server-connection-for-the-sql-server-agent-service-sql-server-management-studio"></a>Set the SQL Server Connection for the SQL Server Agent Service (SQL Server Management Studio)
Este tópico descreve como definir a conexão entre o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent e o [!INCLUDE[ssDE](../../includes/ssde_md.md)] no [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. O serviço do [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent pode se conectar a uma instância local do SQL Server usando autenticação do Windows.  
  
**Neste tópico**  
  
-   **Antes de começar:**  
  
    [Limitações e restrições](#Restrictions)  
  
    [Segurança](#Security)  
  
-   **Para definir a conexão do SQL Server para o SQL Server Agent, usando:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Antes de começar  
  
### <a name="Restrictions"></a>Limitações e restrições  
  
-   O Pesquisador de Objetos só exibirá o nó [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent se você tiver permissão para usá-lo.  
  
-   A partir do [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)], o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent deixou de ter suporte à autenticação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . Essa opção só está disponível para a administração de versões antigas do [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
### <a name="Security"></a>Segurança  
  
#### <a name="Permissions"></a>Permissões  
Para executar suas funções, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent deve ser configurado de modo a usar as credenciais de uma conta que seja membro da função de servidor fixa **sysadmin** no [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. A conta deve ter as seguintes permissões do Windows:  
  
-   Fazer logon como um serviço (SeServiceLogonRight)  
  
-   Substituir um token de nível de processo (SeAssignPrimaryTokenPrivilege)  
  
-   Ignorar verificação completa (SeChangeNotifyPrivilege)  
  
-   Ajustar cotas de memória para um processo (SeIncreaseQuotaPrivilege)  
  
Para obter mais informações sobre as permissões do Windows necessárias para a conta de serviço do [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, consulte [Selecionar uma conta para o serviço do SQL Server Agent](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) e [Setting Up Windows Service Accounts (Configurando as contas de serviço do Windows)](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014).  
  
## <a name="SSMSProcedure"></a>Usando o SQL Server Management Studio  
  
#### <a name="to-set-the-sql-server-connection"></a>Para definir a conexão do SQL Server  
  
1.  No **Pesquisador de Objetos,**clique no sinal de mais para expandir o servidor que você deseja definir com uma conexão como seu Serviço SQL Server Agent.  
  
2.  Clique com o botão direito do mouse em **SQL Server Agent** e selecione **Propriedades**.  
  
3.  Na caixa de diálogo **Propriedades do SQL Server Agent***sever_name* , em **Selecionar uma página**, clique em **Conexão**.  
  
4.  Em **Conexão do SQL Server**, selecione **Usar Autenticação do Windows** para permitir que o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent se conecte a uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] [!INCLUDE[ssDE](../../includes/ssde_md.md)] com Autenticação do [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows. Conexões com bancos de dados do [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] e versões posteriores exigem a Autenticação do Windows.  
  
