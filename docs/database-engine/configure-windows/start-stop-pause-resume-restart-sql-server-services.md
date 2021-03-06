---
title: Iniciar, parar, pausar, retomar e reiniciar os serviços SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 02/26/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, start and stop services
- stopping SQL Server Agent
- parameters [SQL Server], startup options
- SQL Server, startup options
- Database Engine [SQL Server], starting and stopping services
- pausing SQL Server
- PowerShell [SQL Server], starting and stopping services
- single-user mode [SQL Server], starting in
- SQL Server Management Studio [SQL Server], starting or stopping services
- stopping SQL Server Browser service
- starting SQL Server Agent
- default instances [SQL Server], starting and stopping
- SQL Server Agent, starting and stopping
- command prompt [SQL Server], starting and stopping SQL Server services
- continuing SQL Server
- starting SQL Server Database Engine
- net stop commands [SQL Server]
- command prompt [SQL Server], SQL Browser service
- Configuration Manager, start and stop services
- resuming SQL Server
- startup options [SQL Server]
- named instances [SQL Server], starting and stopping
- net start commands [SQL Server]
- SQL Server, starting and stopping
- stopping SQL Server
- starting SQL Server Browser service
- SQL Server Database Engine setting startup options
- administering SQL Server, starting and stopping services
- Management Studio [SQL Server], starting or stopping services
ms.assetid: 32660a02-e5a1-411a-9e57-7066ca459df6
caps.latest.revision: 20
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2e0ca8a8db9121cb224f84ef38e4f03b0f8239f4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="start-stop-pause-resume-restart-sql-server-services"></a>Iniciar, parar, pausar, retomar e reiniciar os serviços SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
 > Para obter o conteúdo relacionado a versões anteriores do SQL Server, consulte [Iniciar, parar, pausar, retomar e reiniciar o serviço SQL Server Agent ou SQL Server Browser do Mecanismo de Banco de Dados](https://msdn.microsoft.com/en-US/library/hh403394(SQL.120).aspx).

  Este tópico descreve como iniciar, parar, pausar, retomar ou reiniciar o [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent ou o serviço [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser usando o Gerenciador de Configurações do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , o  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], os comandos **net** de um prompt de comando, [!INCLUDE[tsql](../../includes/tsql-md.md)]ou o PowerShell.  
  
-   **Antes de começar:**  
  
    -   [O que são estes serviços?](#Services)  
  
    -   [Informações adicionais](#MoreInformation)  
  
    -   [Segurança](#Security)  
  
-   **Instruções usando:**  
  
    -   [SQL Server Configuration Manager](#SSCMProcedure)  
  
    -   [SQL Server Management Studio](#SSMSProcedure)  
  
    -   [Comandos net em uma janela do prompt de comando](#CommandPrompt)  
  
    -   [Transact-SQL](#TsqlProcedure)  
  
    -   [PowerShell](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Services"></a> O que é o serviço [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , o serviço [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e o serviço [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser?  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] são programas executáveis usados como um serviço do Windows. Programas executados como um serviço do Windows podem continuar operando sem exibir qualquer atividade na tela do computador.  
  
 **[!INCLUDE[ssDE](../../includes/ssde-md.md)] serviço**  
 O processo executável que é o [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. O [!INCLUDE[ssDE](../../includes/ssde-md.md)] pode ser a instância padrão (limite de uma por computador) ou pode ser uma de muitas instâncias nomeadas do [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Use o Gerenciador de Configurações do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para determinar quais instâncias do [!INCLUDE[ssDE](../../includes/ssde-md.md)] são instaladas no computador. A instância padrão (se você instalá-la) é listada como **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER)**. As instâncias nomeadas (se você instalá-las) são listadas como **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (<instance_name>)**. Por padrão, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express é instalado como **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLEXPRESS)**.  
  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Serviço do Agent**  
 Um serviço Windows que executa tarefas administrativas agendadas, chamadas trabalhos e alertas. Para obter mais informações, consulte [SQL Server Agent](http://msdn.microsoft.com/library/8d1dc600-aabb-416f-b3af-fbc9fccfd0ec). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent não está disponível em todas as edições do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obter uma lista de recursos com suporte nas edições do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consulte [Recursos com suporte nas edições do SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Serviço Navegador**  
 Um serviço Windows que escuta solicitações de entrada para recursos do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e fornece informações de clientes sobre instâncias do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instaladas no computador. Uma única instância do serviço [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser é usada para todas as instâncias do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instaladas no computador.  
  
###  <a name="MoreInformation"></a> Informações adicionais  
  
-   Pausar o serviço [!INCLUDE[ssDE](../../includes/ssde-md.md)] impede que novos usuários se conectem ao [!INCLUDE[ssDE](../../includes/ssde-md.md)], mas os usuários que já estão conectados podem continuar trabalhando até que suas conexões sejam interrompidas. Use a pausa quando você quiser esperar que os usuários concluam o trabalho antes de parar o serviço. Isso os permite que eles concluam as transações em andamento. Retomar permite que o [!INCLUDE[ssDE](../../includes/ssde-md.md)] aceite novas conexões novamente. Não é possível pausar ou retomar o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Service.  
  
-   O Gerenciador de Configurações do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] exibem o status atual dos serviços usando os ícones a seguir.  
  
     **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .**  
  
    -   Uma seta verde no ícone próximo ao nome do serviço indica que ele foi iniciado.  
  
    -   Um quadrado vermelho no ícone próximo ao nome do serviço indica que ele foi parado.  
  
    -   Duas linhas azuis verticais no ícone próximo ao nome do serviço indicam que ele foi pausado.  
  
    -   Quando o [!INCLUDE[ssDE](../../includes/ssde-md.md)]for reiniciado, um quadrado vermelho indicará que o serviço parou e uma seta verde indicará que ele foi iniciado com êxito.  
  
     **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
    -   Uma seta branca em um ícone de círculo verde próximo ao nome do serviço indica que ele foi iniciado.  
  
    -   Um quadrado branco nem um ícone de círculo vermelho próximo ao nome do serviço indica que ele foi parado.  
  
    -   Duas linhas brancas verticais em um ícone de círculo azul próximo ao nome do serviço indicam que ele foi pausado.  
  
-   Ao usar o Gerenciador de Configurações do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], somente opções que são possíveis estarão disponíveis. Por exemplo, se o serviço já foi iniciado, **Iniciar** estará indisponível.  
  
-   Durante a execução em um cluster, o serviço [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] é gerenciador melhor com o uso do Administrador de Cluster.  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Por padrão, apenas membros do grupo de administradores local podem iniciar, interromper, pausar, retomar ou reiniciar um serviço. Para conceder a capacidade de gerenciar serviços a não administradores, consulte [Como conceder aos usuários direitos para gerenciar serviços no Windows Server 2003](http://support.microsoft.com/kb/325349). (O processo é semelhante em outras versões do Windows.)  
  
 Parar o [!INCLUDE[ssDE](../../includes/ssde-md.md)] usando o comando **SHUTDOWN** do [!INCLUDE[tsql](../../includes/tsql-md.md)] requer a associação às funções de servidor fixas **sysadmin** ou **serveradmin** e não é transferível.  
  
##  <a name="SSCMProcedure"></a> Usando o Gerenciador de Configurações [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
#### <a name="starting-includessnoversionincludesssnoversion-mdmd-configuration-manager"></a>Iniciando o Gerenciador de Configurações [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
1.  No menu **Iniciar** , aponte para **Todos os Programas**, aponte para [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], aponte para **Ferramentas de Configuração**e clique em **SQL Server Configuration Manager**.  
  
     Como o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager é um snap-in do programa Console de Gerenciamento [!INCLUDE[msCoName](../../includes/msconame-md.md)] e não um programa autônomo, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager não aparece como um aplicativo nas versões mais recentes do Windows. Estes são os caminhos para as últimas quatro versões quando o Windows está instalado na unidade C.  
  
    |||  
    |-|-|  
    |[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016|C:\Windows\SysWOW64\SQLServerManager13.msc|  
    |[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|C:\Windows\SysWOW64\SQLServerManager12.msc|  
    |[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|C:\Windows\SysWOW64\SQLServerManager11.msc|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|C:\Windows\SysWOW64\SQLServerManager10.msc|  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-an-instance-of-the-includessdenoversionincludesssdenoversion-mdmd"></a>Para iniciar, parar, pausar, retomar ou reiniciar a instância do [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]  
  
1.  Iniciar o Gerenciador de Configurações [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando as instruções acima.  
  
2.  (Se a caixa de diálogo **Controle de Conta de Usuário** aparecer, clique em **Sim**.  
  
3.  No [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, no painel esquerdo, clique em **Serviços do SQL Server**.  
  
4.  No painel de resultados, clique com o botão direito do mouse em **SQL Server (MSSQLServer)** ou em uma instância nomeada e clique em **Iniciar**, **Parar**, **Pausar**, **Retomar**ou **Reiniciar**.  
  
5.  Clique em **OK** para fechar o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.  
  
> [!NOTE]  
>  Para iniciar uma instância do [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] com opções de inicialização, consulte [Configurar opções de inicialização do servidor &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md).  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-includessnoversionincludesssnoversion-mdmd-browser-or-an-instance-of-the-includessnoversionincludesssnoversion-mdmd-agent"></a>Para iniciar, parar, pausar, retomar ou reiniciar a instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser ou uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
1.  Iniciar o Gerenciador de Configurações [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando as instruções acima.  
  
2.  (Se a caixa de diálogo **Controle de Conta de Usuário** aparecer, clique em **Sim**.  
  
3.  No [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, no painel esquerdo, clique em **Serviços do SQL Server**.  
  
4.  No painel de resultados, clique com o botão direito do mouse em **Navegador do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**, **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent (MSSQLServer)** ou **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent (<instance_name>)** para a instância nomeada e clique em **Iniciar**, **Parar**, **Pausar**, **Retomar** ou **Reiniciar**.  
  
5.  Clique em **OK** para fechar o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.  
  
> [!NOTE]  
>  O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent não pode ser colocado em pausa.  
  
##  <a name="SSMSProcedure"></a> Usando o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-an-instance-of-the-includessdenoversionincludesssdenoversion-mdmd"></a>Para iniciar, parar, pausar, retomar ou reiniciar a instância do [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]  
  
1.  No Pesquisador de Objetos, conecte-se à instância do [!INCLUDE[ssDE](../../includes/ssde-md.md)], clique com o botão direito do mouse na instância do [!INCLUDE[ssDE](../../includes/ssde-md.md)] que você deseja iniciar e clique em **Iniciar**, **Parar**, **Pausar**, **Retomar**ou **Reiniciar**.  
  
     Ou, em Servidores Registrados, clique com o botão direito do mouse na instância do [!INCLUDE[ssDE](../../includes/ssde-md.md)] que você deseja iniciar, aponte para **Controle de Serviço**e clique em **Iniciar**, **Parar**, **Pausar**, **Retomar**ou **Reiniciar**.  
  
2.  (Se a caixa de diálogo **Controle de Conta de Usuário** aparecer, clique em **Sim**.  
  
3.  Quando solicitado a indicar se você deseja executar a ação, clique em **Sim**.  
  
#### <a name="to-start-stop-or-restart-the-an-instance-of-the-includessnoversionincludesssnoversion-mdmd-agent"></a>Para iniciar, parar ou reiniciar uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
1.  No Pesquisador de Objetos, conecte-se à instância do [!INCLUDE[ssDE](../../includes/ssde-md.md)], clique com o botão direito do mouse no **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent**e clique em **Iniciar**, **Parar**ou **Reiniciar**.  
  
2.  (Se a caixa de diálogo **Controle de Conta de Usuário** aparecer, clique em **Sim**.  
  
3.  Quando solicitado a indicar se você deseja executar a ação, clique em **Sim**.  
  
##  <a name="CommandPrompt"></a> Na janela Prompt de Comando usando comandos net  
 Os serviços do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] podem ser iniciados, parados ou pausados com o uso de comandos [!INCLUDE[msCoName](../../includes/msconame-md.md)]  **net** do Windows.  
  
###  <a name="dbDefault"></a> Para iniciar a instância padrão do [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   Em um prompt de comando, digite um dos seguintes comandos:  
  
     **net start "SQL Server (MSSQLSERVER)"**  
  
     -ou-  
  
     **net start MSSQLSERVER**  
  
###  <a name="dbNamed"></a> Para iniciar uma instância nomeada do [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   Em um prompt de comando, digite um dos comandos a seguir. Substitua *\<instancename>* pelo nome da instância que você deseja gerenciar.  
  
     **net start "SQL Server (** *instancename* **)"**  
  
     -ou-  
  
     **net start MSSQL$** *instancename*  
  
###  <a name="dbStartup"></a> Para iniciar o [!INCLUDE[ssDE](../../includes/ssde-md.md)] com opções de inicialização  
  
-   Adicione opções de inicialização ao final da instrução **net start "SQL Server (MSSQLSERVER)"** , separadas por espaço. Quando começar usando **net start**, as opções de inicialização usam uma barra (/) em vez de um hífen (-).  
  
     **net start "SQL Server (MSSQLSERVER)" /f /m**  
  
     -ou-  
  
     **net start MSSQLSERVER /f /m**  
  
    > [!NOTE]  
    >  Para obter mais informações sobre as opções de inicialização, consulte [Opções de inicialização do serviço Mecanismo de Banco de Dados](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
###  <a name="agDefault"></a> Para iniciar o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent na instância padrão do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Em um prompt de comando, digite um dos seguintes comandos:  
  
     **net start "SQL Server Agent (MSSQLSERVER)"**  
  
     -ou-  
  
     **net start SQLSERVERAGENT**  
  
###  <a name="agNamed"></a> Para iniciar o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent em uma instância nomeada do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Em um prompt de comando, digite um dos comandos a seguir. Substitua *instancename* pelo nome da instância que você deseja gerenciar.  
  
     **net start "SQL Server Agent(** *instancename* **)"**  
  
     -ou-  
  
     **net start SQLAgent$** *instancename*  
  
 Para obter informações sobre como executar o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent em modo detalhado para solução de problemas, consulte [sqlagent90 Application](../../tools/sqlagent90-application.md).  
  
###  <a name="Browser"></a> Para iniciar o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser  
  
-   Em um prompt de comando, digite um dos seguintes comandos:  
  
     **net start "SQL Server Browser"**  
  
     -ou-  
  
     **net start SQLBrowser**  
  
###  <a name="pauseStop"></a> Para pausar ou parar os serviços na janela Prompt de Comando  
  
-   Para pausar ou parar serviços, modifique os comandos das maneiras a seguir.  
  
    -   Para pausar um serviço, substitua **net start** por **net pause**.  
  
    -   Para pausar um serviço, substitua **net start** com **net pause**.  
  
##  <a name="TsqlProcedure"></a> Usando o Transact-SQL  
 O [!INCLUDE[ssDE](../../includes/ssde-md.md)] pode ser parado com a instrução **SHUTDOWN** .  
  
#### <a name="to-stop-the-includessdeincludesssde-mdmd-using-includetsqlincludestsql-mdmd"></a>Para parar o [!INCLUDE[ssDE](../../includes/ssde-md.md)] usando [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
-   Para aguardar a conclusão de instruções [!INCLUDE[tsql](../../includes/tsql-md.md)] e procedimentos armazenados em execução atualmente e parar o [!INCLUDE[ssDE](../../includes/ssde-md.md)], execute a instrução a seguir.  
  
    ```sql  
    SHUTDOWN;   
    ```  
  
-   Para parar o [!INCLUDE[ssDE](../../includes/ssde-md.md)] imediatamente, execute a instrução a seguir.  
  
    ```sql  
    SHUTDOWN WITH NOWAIT;   
    ```  
  
 Para obter mais informações sobre a instrução **SHUTDOWN**, consulte [SHUTDOWN &#40;Transact-SQL&#41;](../../t-sql/language-elements/shutdown-transact-sql.md).  
  
##  <a name="PowerShellProcedure"></a> Usando o PowerShell  
  
#### <a name="to-start-and-stop-includessdeincludesssde-mdmd-services"></a>Para iniciar e parar os serviços [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
1.  Em uma janela Prompt de Comando, inicie o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell executando o comando a seguir.  
  
    ```ms-dos  
    sqlps  
    ```  
  
2.  Em um prompt de comando do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell, executando o comando a seguir. Substitua `computername` pelo nome do seu computador.  
  
    ```powershell  
    # Get a reference to the ManagedComputer class.  
    CD SQLSERVER:\SQL\computername  
    $Wmi = (get-item .).ManagedComputer  
  
    ```  
  
3.  Identifique o serviço que você deseja parar ou iniciar. Escolha uma das linhas a seguir. Substitua `instancename` pelo nome da instância nomeada.  
  
    -   Para obter uma referência à instância padrão do [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQLSERVER']  
        ```  
  
    -   Para obter uma referência a uma instância nomeada do [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQL$instancename']  
        ```  
  
    -   Para obter uma referência ao serviço [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent na instância padrão do [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLSERVERAGENT']  
        ```  
  
    -   Para obter uma referência ao serviço [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent em uma instância nomeada do [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLAGENT$instancename']  
        ```  
  
    -   Para obter uma referência ao serviço [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser.  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLBROWSER']  
        ```  
  
4.  Conclua o exemplo para iniciar e parar o serviço selecionado.  
  
    ```powershell  
    # Display the state of the service.  
    $DfltInstance  
    # Start the service.  
    $DfltInstance.Start();  
    # Wait until the service has time to start.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    # Stop the service.  
    $DfltInstance.Stop();  
    # Wait until the service has time to stop.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    ```  
  
## <a name="see-also"></a>Consulte Também  
 [Visão geral da documentação de instalação do SQL Server](http://msdn.microsoft.com/library/2620439a-f9d3-4b3c-9968-48f60b4bb9a5)   
 [Exibir e ler arquivos de log da Instalação do SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)   
 [SQL Server Configuration Manager](../../relational-databases/sql-server-configuration-manager.md)   
 [Iniciar o SQL Server com a configuração mínima](../../database-engine/configure-windows/start-sql-server-with-minimal-configuration.md)   
 [Recursos com suporte nas edições do SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)  
  
  

