---
title: Instalar o SQL Server 2017 máquina Learning Services (no banco de dados) no Windows | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 577d5266c98211949db8d1992bf559161d8ee97d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="install-sql-server-2017-machine-learning-services-in-database-on-windows"></a>Instalar o SQL Server 2017 máquina Learning Services (no banco de dados) no Windows 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

O componente de serviços de aprendizado de máquina do SQL Server adiciona a análise preditiva no banco de dados e algoritmos de aprendizado de máquina, visualização e análise estatística. Bibliotecas de função estão disponíveis em R e Python e executado como script externo em uma instância do mecanismo de banco de dados. 

Este artigo explica como instalar o componente de aprendizado de máquina executando o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistente de instalação e seguir as instruções na tela.

## <a name="bkmk_prereqs"> </a> Lista de verificação de pré-instalação

+ A instalação do SQL Server 2017 é necessária se você deseja instalar os serviços de aprendizado de máquina com suporte a linguagem R, Python ou ambos. Se, em vez disso, você tem a mídia de instalação do SQL Server 2016, você pode instalar [SQL Server 2016 R Services (no banco de dados)](sql-r-services-windows-install.md) para obter suporte de linguagem R.

+ Uma instância do mecanismo de banco de dados é necessária. Você não pode instalar apenas R ou recursos de Python, embora você pode adicioná-los incrementalmente para uma instância existente.

+ Não instale os serviços de aprendizado de máquina em um cluster de failover. O mecanismo de segurança usado para isolar processos de R e Python não é compatível com um ambiente de cluster de failover do Windows Server.

+ Não instale os serviços de aprendizado de máquina em um controlador de domínio. A parte de serviços de aprendizado de máquina do programa de instalação falhará.

+ Não instale **recursos compartilhados** > **Server de aprendizado de máquina (autônomo)** no mesmo computador que está executando uma instância no banco de dados. Um servidor autônomo competirão para os mesmos recursos, prejudicando o desempenho de ambas as instalações.

+ Instalação lado a lado com outras versões do R e Python é aceito, mas não recomendada. É possível porque a instância do SQL Server usa suas próprias cópias as distribuições de R e Anaconda do código-fonte aberto. Mas não é recomendado, pois executando o código que usa o R e Python no computador do SQL Server fora do SQL Server pode causar vários problemas:
    
  + Usar uma biblioteca diferente e o executável diferente e obter resultados diferentes, que é feito quando você estiver executando no SQL Server.
  + Scripts de R e Python em execução em bibliotecas externas não podem ser gerenciados pelo SQL Server, levando a contenção de recursos.
  
> [!IMPORTANT]
> Após a conclusão da instalação, certifique-se de concluir as etapas de pós-configuração descritas neste artigo. Essas etapas incluem a habilitar o SQL Server para usar scripts externos e adicionar contas necessárias para o SQL Server executar trabalhos de R e Python em seu nome. Alterações de configuração geralmente requerem uma reinicialização da instância, ou uma reinicialização do serviço Launchpad.

## <a name="get-the-installation-media"></a>Obtenha a mídia de instalação

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

## <a name="run-setup"></a>Executar a instalação

Para instalações locais, você deve executar a Instalação como um administrador. Se você instalar o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de um compartilhamento remoto, deverá usar uma conta de domínio que tenha permissões de leitura e de execução no compartilhamento remoto.

1. Inicie o Assistente de instalação para SQL Server 2017. Você pode baixar 
  
2. Sobre o **instalação** guia, selecione **instalação autônoma do novo SQL Server ou adicionar recursos a uma instalação existente**.

   ![Instalar os serviços no banco de dados de aprendizado de máquina](media/2017setup-installation-page-mlsvcs.PNG)
   
3. Na página **Seleção de Recursos** , selecione estas opções:
  
    -   **Serviços do Mecanismo de Banco de Dados**
  
         Para usar o R e Python com o SQL Server, você deve instalar uma instância do mecanismo de banco de dados. Você pode usar um padrão ou uma instância nomeada.
  
    -   **Serviços de Machine Learning (no banco de dados)**
  
         Esta opção instala os serviços de banco de dados que oferecem suporte a R e execução do script de Python.

    -   **R**

        Marque esta opção para adicionar o Microsoft R pacotes interpretador e R. o código-fonte aberto 

    -   **Python**

        Marque esta opção para adicionar os pacotes do Microsoft Python, o executável do Python 3.5 e selecione bibliotecas da distribuição Anaconda.
        
        ![Recurso de opções de R e Python](media/2017setup-features-page-mls-rpy.png "opções de configuração para Python")

        > [!NOTE]
        > 
        > Não selecione a opção para **Server de aprendizado de máquina (autônomo)**. A opção para instalar o servidor de aprendizado de máquina em **recursos compartilhados** é destinado para uso em um computador separado.

4. Sobre o **consentimento para instalar o R** página, selecione **aceitar**. Este contrato de licença abrange Microsoft R Open, que inclui uma distribuição das ferramentas, junto com pacotes de R aprimorados e provedores de conectividade da equipe de desenvolvimento da Microsoft e pacotes de base de R de código-fonte aberto.

5. Sobre o **consentimento para instalar o Python** página, selecione **aceitar**. O contrato de licença de software livre de Python também aborda Anaconda e ferramentas relacionadas, além de algumas novas bibliotecas Python da equipe de desenvolvimento da Microsoft.
     
     ![Contrato de licença de Python](media/2017setup-python-license.png "contrato para Python de licença")
  
    > [!NOTE]
    >  Se o computador que está usando não tiver acesso à internet, você pode pausar o programa de instalação neste momento para baixar os instaladores separadamente. Para obter mais informações, consulte [instalar componentes de aprendizado de máquina sem acesso à internet](../install/sql-ml-component-install-without-internet-access.md).
  
     Selecione **aceitar**, aguarde até que o **próximo** botão se torna ativo e, em seguida, selecione **próximo**.
  
6. Sobre o **pronto para instalar** página, verifique se essas seleções são incluídas e selecione **instalar**.
  
    + Serviços do Mecanismo de Banco de Dados
    + Serviços de Machine Learning (No Banco de Dados)
    + R, Python ou ambos

    Anote o local da pasta no caminho `..\Setup Bootstrap\Log` onde os arquivos de configuração são armazenados. Quando a instalação for concluída, você pode examinar os componentes instalados no arquivo de resumo.

## <a name="restart-the-service"></a>Reinicie o serviço.

Quando a instalação for concluída, reinicie o mecanismo de banco de dados antes de prosseguir para a próxima, permitindo a execução do script.

Reiniciar o Nom automaticamente reinicia relacionado [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] serviço.

Você pode reiniciar o serviço usando o botão direito do mouse **reiniciar** comando para a instância no SSMS, ou usando o **serviços** painel no painel de controle ou usando [SQL Server Configuration Manager ](../../relational-databases/sql-server-configuration-manager.md).

## <a name="bkmk_enableFeature"></a>Habilitar a execução do script externo

1. Abra o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > Você pode baixar e instalar a versão apropriada nesta página: [baixar o SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
    > 
    > Você também pode testar a versão de visualização de [Studio de operações SQL](https://docs.microsoft.com/sql/sql-operations-studio/what-is), que oferece suporte a tarefas administrativas e consultas no SQL Server.
  
2. Conecte-se à instância onde você instalou os serviços de aprendizado de máquina, clique em **nova consulta** para abrir uma janela de consulta e execute o seguinte comando:

   ```SQL
   sp_configure
   ```

    O valor da propriedade `external scripts enabled`, deve ser **0** neste momento. Isso ocorre porque o recurso está desativado por padrão. O recurso deve ser habilitado explicitamente por um administrador antes de executar scripts R ou Python.
    
3.  Para habilitar o recurso de script externo, execute a seguinte instrução:
    
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
    
    Se você já tiver ativado o recurso para a linguagem R, não execute reconfigurar uma segunda vez de Python. A plataforma de extensibilidade subjacente oferece suporte a ambas as linguagens.

4. Reinicie o serviço SQL Server da instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Reiniciar o serviço do SQL Server também automaticamente reinicia relacionado [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] serviço.

    Você pode reiniciar o serviço usando o botão direito do mouse **reiniciar** comando para a instância no SSMS, ou usando o **serviços** painel no painel de controle ou usando [SQL Server Configuration Manager ](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>Verifique a instalação

Use as etapas a seguir para verificar se todos os componentes usados para iniciar o script externo estão em execução.

1. No SQL Server Management Studio, abra uma nova janela de consulta e execute o seguinte comando:
    
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```

    O **run_value** agora deve ser definido como 1.
    
2. Abra o **serviços** painel ou o SQL Server Configuration Manager e verifique se **serviço Launchpad do SQL Server** está em execução. Você deve ter um serviço para cada instância do mecanismo de banco de dados que tem o R ou Python instalado. Reinicie o serviço se não estiver em execução. Para obter mais informações, consulte [componentes para dar suporte à integração do Python](../python/new-components-in-sql-server-to-support-python-integration.md). 
   
3. Se estiver executando a barra inicial, você poderá executar scripts R e Python simples para verificar se os tempos de execução de script externos podem se comunicar com o SQL Server.

   Abra uma nova **consulta** janela no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], e, em seguida, executar um script como o seguinte:
    
    + Para R
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    + Para Python
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'Python',
    @script=N'
    OutputDataSet = InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

 **Resultados**

    O script pode demorar um pouco enquanto para ser executado na primeira vez que o tempo de execução do script externo é carregado. Os resultados devem ser algo assim:

    | hello |
    |----|
    | 1|


> [!NOTE]
> Títulos usados no script Python ou colunas não são retornados, por design. Para adicionar nomes de coluna de saída, você deve especificar o esquema para o conjunto de dados retornado. Faça isso usando o parâmetro com resultados do procedimento armazenado, nomear as colunas e especificando o tipo de dados SQL.
> 
> Por exemplo, você pode adicionar a linha a seguir para gerar um nome arbitrário de coluna: `WITH RESULT SETS ((Col1 AS int))`

## <a name="additional-configuration"></a>Configuração adicional

Se a etapa de verificação de script externo foi bem-sucedida, você pode executar comandos de Python do SQL Server Management Studio, o código do Visual Studio ou qualquer outro cliente que pode enviar instruções T-SQL para o servidor.

Se você receber um erro ao executar o comando, examine as etapas de configuração adicionais nesta seção. Talvez seja necessário fazer configurações adicionais de apropriado para o serviço ou o banco de dados.

Cenários comuns que exigem alterações adicionais incluem:

* [Configurar o firewall do Windows para conexões de entrada](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)
* [Habilitar protocolos de rede adicionais](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Habilitar conexões remotas](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [Estender permissões internas para usuários remotos](#bkmk_configureAccounts)
* [Conceder permissão para executar scripts externos](#permissions-external-script)
* [Conceder acesso a bancos de dados individuais](#permissions-db)

> [!NOTE]
> Nem todas as alterações listadas são necessárias, e nenhum pode ser necessária. Requisitos dependem de seu esquema de segurança, onde você instalou o SQL Server e como você espera que os usuários a se conectar ao banco de dados e executar scripts externos. Dicas de solução de problemas adicionais podem ser encontradas aqui: [perguntas frequentes sobre atualização e instalação](../r/upgrade-and-installation-faq-sql-server-r-services.md)

###  <a name="bkmk_configureAccounts"></a> Habilitar autenticação implícita para o grupo de contas da barra inicial

Durante a instalação, um número de novas contas de usuário do Windows são criadas com a finalidade de executar tarefas no token de segurança do serviço [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Quando um usuário envia um script Python ou R de um cliente externo, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ativa uma conta de trabalho disponíveis. Em seguida, ele mapeia para a identidade do usuário da chamada e executa o script em nome do usuário.

Isso é chamado de *autenticação implícita*, e é um serviço de mecanismo de banco de dados. Este serviço oferece suporte a execução segura de scripts externos no SQL Server 2016 e 2017 do SQL Server.

Exiba essas contas no grupo de usuários do Windows, **SQLRUserGroup**. Por padrão, 20 contas de trabalho são criadas, que geralmente é mais do que suficiente para executar o script externo trabalhos.

> [!IMPORTANT]
> O grupo de trabalho é denominado **SQLRUserGroup** independentemente se você instalou o R ou Python. Há um único grupo para cada instância.

Se você precisa executar os scripts de um cliente de ciência de dados remotos, e você estiver usando autenticação do Windows, há considerações adicionais. Essas contas de trabalho devem receber permissão para entrar para a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instância em seu nome.

1. Em [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], no Pesquisador de objetos, expanda **segurança**. Em seguida, clique com botão direito **logons**e selecione **novo logon**.
2. No **logon - novo** caixa de diálogo, selecione **pesquisa**.
3. Selecione **tipos de objeto**e selecione **grupos**. Limpe tudo.
4. Em **insira o nome do objeto para selecionar**, tipo *SQLRUserGroup*e selecione **verificar nomes**.
5. O nome do grupo local associado ao serviço Launchpad da instância deverá ser resolvido para algo como *instancename\SQLRUserGroup*. Escolha **OK**.
6. Por padrão, o grupo é atribuído para o **pública** função, e tem permissão para conectar-se ao mecanismo de banco de dados.
7. Escolha **OK**.

> [!NOTE]
> Se você usar um **logon SQL** para executar scripts em um contexto de computação do SQL Server, esta etapa adicional não é necessária.

### <a name="permissions-external-script"></a> Conceder aos usuários permissão para executar scripts externos

Se você instalou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] por conta própria e você está executando scripts de R ou Python em sua própria instância, você normalmente executa scripts como administrador. Portanto, você tem permissão implícita em várias operações e todos os dados no banco de dados.

A maioria dos usuários, no entanto, não tem tais permissões elevadas. Por exemplo, os usuários em uma organização que usam logons do SQL Server para acessar o banco de dados geralmente não têm permissões elevadas. Portanto, para cada usuário que está usando o R ou Python, você deve conceder aos usuários dos serviços de aprendizado de máquina a permissão para executar scripts externos em cada banco de dados onde o idioma é usado. Aqui está como:

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!NOTE]
> As permissões não são específicas para a linguagem de script com suporte. Em outras palavras, não há níveis de permissão separados para o script R versus script Python. Se você precisar manter permissões separadas para esses idiomas, instale o R e Python em instâncias separadas.

### <a name="permissions-db"></a> Conceder permissões de language (DDL) para bancos de dados de sua definição de leitura, gravação ou dados de usuários

Enquanto um usuário está em execução de scripts, o usuário talvez precise ler dados de outros bancos de dados. O usuário também precisará criar novas tabelas para armazenar os resultados e gravar dados em tabelas.

Para cada conta de usuário do Windows ou logon SQL que está executando os scripts de R ou Python, certifique-se de que ele tem as permissões apropriadas no banco de dados específico: `db_datareader`, `db_datawriter`, ou `db_ddladmin`.

Por exemplo, a seguinte [!INCLUDE[tsql](../../includes/tsql-md.md)] declaração fornece o logon do SQL *MySQLLogin* os direitos para executar consultas T-SQL *ML_Samples* banco de dados. Para executar essa instrução, o logon SQL já deve existir no contexto de segurança do servidor.

```SQL
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

Para obter mais informações sobre as permissões incluídas em cada função, consulte [funções de nível de banco de dados](../../relational-databases/security/authentication-access/database-level-roles.md).


### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>Criar uma fonte de dados ODBC para a instância no cliente de ciência de dados

Você pode criar uma solução em um computador de cliente de ciência de dados de aprendizado de máquina. Se você precisar executar código usando o computador do SQL Server como o contexto de computação, você tem duas opções: acessar a instância usando um logon SQL ou usando um Windows da conta.

+ Para logons do SQL Server: Verifique se o logon tem permissões apropriadas no banco de dados em que você está lendo dados. Você pode fazer isso adicionando *conectem* e *selecione* permissões, ou adicionando o logon para o `db_datareader` função. Para criar objetos, atribuir `DDL_admin` direitos. Se você deve salvar dados em tabelas, adicionar ao `db_datawriter` função.

+ Para autenticação do Windows: talvez seja necessário criar uma fonte de dados ODBC no cliente de ciência de dados que especifica o nome da instância e outras informações de conexão. Para obter mais informações, consulte [administrador de fonte de dados ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator).

## <a name="suggested-optimizations"></a>Otimizações sugeridas

Agora que você tem que tudo funcione, você também poderá otimizar o servidor para suportar o aprendizado de máquina ou modelos de classificação de instalação.

### <a name="add-more-worker-accounts"></a>Adicionar mais contas de trabalho

Se você espera que muitos usuários em execução simultaneamente scripts, você pode aumentar o número de contas de trabalho que são atribuídos ao serviço barra inicial. Para obter mais informações, consulte [modificar o pool de conta de usuário para serviços de aprendizado de máquina do SQL Server](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

### <a name="optimize-the-server-for-script-execution"></a>Otimizar o servidor para execução de script

As configurações padrão para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instalação destinam-se para otimizar o equilíbrio do servidor para uma variedade de serviços que são suportados pelo mecanismo de banco de dados, que pode incluir a extração, transformação e carregamento (ETL) processos, relatórios, auditoria, e aplicativos que usam [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dados. Portanto, as configurações padrão, você pode encontrar recursos de aprendizagem de máquina, às vezes, são restritos ou limitados, especialmente em operações com uso intensivo de memória.

Para garantir que os trabalhos de aprendizado de máquina são priorizados e recursos adequadamente, é recomendável que você use o administrador de recursos do SQL Server para configurar um pool de recursos externos. Você também poderá alterar a quantidade de memória alocada para o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mecanismo de banco de dados ou aumentar o número de contas que são executados sob o [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] service.

- Para configurar um pool de recursos de gerenciamento de recursos externos, consulte [criar um pool de recursos externos](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Para alterar a quantidade de memória reservada para o banco de dados, consulte [opções de configuração de memória do servidor](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- Para alterar o número de contas de R que pode ser iniciado por [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], consulte [modificar o pool de conta de usuário para o aprendizado de máquina](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

Se você estiver usando a Standard Edition e não possuem o administrador de recursos, você pode usar eventos estendidos e exibições de gerenciamento dinâmico (DMVs), bem como eventos do Windows de monitoramento, para ajudar a gerenciar os recursos do servidor. Para obter mais informações, consulte [monitoramento e gerenciamento de serviços de R](../r/managing-and-monitoring-r-solutions.md) e [monitoramento e gerenciamento de serviços de Python](../python/managing-and-monitoring-python-solutions.md).

### <a name="install-additional-r-packages"></a>Instalar pacotes R adicionais

As soluções de R que você criar para o SQL Server podem chamar funções básicas de R, funções do packes properietary instalado com o SQL Server e pacotes de R de terceiros compatíveis com a versão do código-fonte aberto R instalado pelo SQL Server.

Pacotes que você desejar usar do SQL Server deverão ser instalados na biblioteca padrão usada pela instância. Se você tiver uma instalação separada do R no computador, ou se você instalou pacotes nas bibliotecas do usuário, você não poderá usar esses pacotes do T-SQL.

O processo de instalação e gerenciamento de pacotes de R é diferente no SQL Server 2016 e 2017 do SQL Server. No SQL Server 2016, um administrador de banco de dados deve instalar os pacotes de R que os usuários precisam. No SQL Server de 2017, você pode configurar grupos de usuários para compartilhar pacotes em um nível por banco de dados ou configurar as funções de banco de dados para permitir que os usuários instalem seus próprios pacotes. Para obter mais informações, consulte [pacote de gerenciamento](../r/r-package-management-for-sql-server-r-services.md).


## <a name="get-help"></a>Obter ajuda

Precisa de ajuda com a instalação ou atualização? Para obter respostas a perguntas comuns e problemas conhecidos, consulte o seguinte artigo:

* [Atualização e instalação perguntas Frequentes – serviços de aprendizado de máquina](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Para verificar o status da instalação da instância e corrigir problemas comuns, tente esses relatórios personalizados.

* [Relatórios personalizados do SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Próximas etapas

Os desenvolvedores de R podem começar com alguns exemplos simples e conheça os fundamentos de como funciona o R com o SQL Server. Para a próxima etapa, consulte os links a seguir:

+ [Tutorial: Executar R no T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Tutorial: Análise de no banco de dados para os desenvolvedores de R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Os desenvolvedores de Python podem Saiba como usar o Python com o SQL Server por esses tutoriais a seguir:

+ [Tutorial: Executar Python em T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Tutorial: Análise de no banco de dados para desenvolvedores Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Para exibir exemplos de aprendizado de máquina com base em cenários do mundo real, consulte [tutoriais de aprendizado de máquina](../tutorials/machine-learning-services-tutorials.md).
