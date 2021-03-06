---
title: Suporte do Scale Out para Alta Disponibilidade do SSIS (SQL Server Integration Services) | Microsoft Docs
ms.description: This article describes how to configure SSIS Scale Out for high availability
ms.custom: ''
ms.date: 12/19/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: scale-out
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: craigg
ms.openlocfilehash: 8cd79327b3733de9f7463f1d5f9d8f924b58a46b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="scale-out-support-for-high-availability"></a>Suporte do Scale Out para alta disponibilidade

No SSIS Scale Out, a alta disponibilidade do lado do Trabalho do Scale Out é fornecida com a execução de pacotes com vários Trabalhos do Scale Out.

No lado do Mestre do Scale Out, a alta disponibilidade é obtida com o [Always On para o Catálogo do SSIS](../catalog/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb) e o clustering de failover do Windows. Nesta solução, várias instâncias de Mestre do Scale Out são hospedadas em um cluster de failover do Windows. Quando o serviço Mestre do Scale Out ou o SSISDB está inativo no nó primário, o serviço ou o SSISDB no nó secundário continua aceitando as solicitações do usuário e se comunicando com os Trabalhos do Scale Out.

Como alternativa, a alta disponibilidade no lado do Mestre do Scale Out pode ser obtida com a instância de cluster de failover do SQL Server. Consulte [Suporte do Scale Out para alta disponibilidade por meio da instância de cluster de failover do SQL Server](scale-out-failover-cluster-instance.md).

Para configurar a alta disponibilidade no lado do Mestre do Scale Out com o Always On para o catálogo do SSIS, siga estas etapas:

## <a name="1-prerequisites"></a>1. Prerequisites
Configurar um cluster de failover do Windows. Confira a postagem no blog [Installing the Failover Cluster Feature and Tools for Windows Server 2012](http://blogs.msdn.com/b/clustering/archive/2012/04/06/10291601.aspx) (Instalando o recurso Cluster de Failover e as Ferramentas para o Windows Server 2012) para obter instruções. Instale o recurso e as ferramentas em todos os nós de cluster.

## <a name="2-install-scale-out-master-on-the-primary-node"></a>2. Instalar o Mestre do Scale Out no nó primário
Instale os Serviços de Mecanismo de Banco de Dados do SQL Server, o Integration Services e o Mestre do Scale Out no nó primário do Mestre do Scale Out. 

Durante a instalação, faça o seguinte:

### <a name="21-set-the-account-running-scale-out-master-service-to-a-domain-account"></a>2.1 Defina a conta que executa o serviço Mestre do Scale Out com uma conta de domínio
Essa conta deve poder acessar o SSISDB no nó secundário no cluster de failover do Windows no futuro. Já que o serviço Mestre do Scale Out e o SSISDB podem fazer failover separadamente, eles podem não estar no mesmo nó após o failover.

![Configuração do servidor de alta disponibilidade](media/ha-server-config.PNG)

### <a name="22-include-the-dns-host-name-for-the-scale-out-master-service-in-the-cns-of-the-scale-out-master-certificate"></a>2.2 Inclua o nome do host DNS do serviço Mestre do Scale Out nos CNs do certificado do Mestre do Scale Out

Esse nome do host é usado no ponto de extremidade do Mestre do Scale Out. 

![Configuração do mestre de alta disponibilidade](media/ha-master-config.PNG)

## <a name="3-install-scale-out-master-on-the-secondary-node"></a>3. Instalar o Mestre do Scale Out no nó secundário
Instale os Serviços de Mecanismo de Banco de Dados do SQL Server, o Integration Services e o Mestre do Scale Out no nó secundário do Mestre do Scale Out. 

Use o mesmo certificado do Mestre do Scale Out usado no nó primário. Exporte o certificado SSL do Mestre do Scale Out no nó primário com uma chave privada e instale-o no repositório de certificados Raiz do computador local no nó secundário. Selecione esse certificado durante a instalação do Mestre do Scale Out no nó secundário.

![Configuração do mestre de alta disponibilidade 2](media/ha-master-config2.PNG)

> [!NOTE]
> Configure vários Mestres do Scale Out de backup repetindo essas operações para o Mestre do Scale Out nos outros nós secundários.

## <a name="4-set-up-ssisdb-always-on"></a>4. Configurar o Always On do SSISDB

Siga as instruções para configurar o Always On para o SSISDB em [Always On para o Catálogo do SSIS (SSISDB)](../catalog/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb).

Além disso, é necessário criar um ouvinte do grupo de disponibilidade para o grupo de disponibilidade ao qual o SSISDB será adicionado. Consulte [Criar ou configurar um ouvinte de grupo de disponibilidade](../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).

## <a name="5-update-the-scale-out-master-service-configuration-file"></a>5. Atualizar o arquivo de configuração de serviço do Mestre do Scale Out
Atualize o arquivo de configuração de serviço do Mestre do Scale Out, `\<drive\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config`, nos nós primários e secundários. Atualize **SqlServerName** para *[Nome DNS do Ouvinte do Grupo de Disponibilidade],[Porta]*.

## <a name="6-enable-package-execution-logging"></a>6. Habilitar log de execução de pacote

O log no SSISDB é feito pelo logon **##MS_SSISLogDBWorkerAgentLogin##**, cuja senha é gerada automaticamente. Para fazer com que o log funcione em todas as réplicas do SSISDB, faça o seguinte

### <a name="61-change-the-password-of-msssislogdbworkeragentlogin-on-the-primary-sql-server"></a>6.1 Altere a senha de **##MS_SSISLogDBWorkerAgentLogin##** no SQL Server primário

### <a name="62-add-the-login-to-the-secondary-sql-server"></a>6.2 Adicione o logon ao SQL Server secundário

### <a name="63-update-the-connection-string-used-for-logging"></a>6.3 Atualize a cadeia de conexão usada para o log.
Chame o procedimento armazenado `[catalog].[update_logdb_info]` com os seguintes valores de parâmetro:

-   `@server_name = '[Availability Group Listener DNS name],[Port]' `

-   `@connection_string = 'Data Source=[Availability Group Listener DNS name],[Port];Initial Catalog=SSISDB;User Id=##MS_SSISLogDBWorkerAgentLogin##;Password=[Password]];'`

## <a name="7-configure-the-scale-out-master-service-role-of-the-windows-failover-cluster"></a>7. Configure a função de serviço do Mestre do Scale Out do cluster de failover do Windows

1.  No Gerenciador de Cluster de Failover, conecte-se ao cluster do Scale Out. Selecione o cluster. Selecione **Ação** no menu e, em seguida, selecione **Configurar Função**.

2.  Na caixa de diálogo **Assistente para Alta Disponibilidade**, selecione **Serviço Genérico** na página **Selecionar Função**. Selecione o Mestre do SQL Server Integration Services Scale Out 14.0 na página **Selecionar Serviço**.

3.  Na página **Ponto de Acesso para Cliente**, insira o nome do host DNS do serviço Mestre do Scale Out.

    ![Assistente de Alta Disponibilidade 1](media/ha-wizard1.PNG)

4.  Conclua o assistente.

## <a name="8-update-the-scale-out-master-address-in-ssisdb"></a>8. Atualizar o endereço do Mestre do Scale Out no SSISDB

No SQL Server primário, execute o procedimento armazenado `[catalog].[update_master_address]` com o valor de parâmetro `@MasterAddress = N'https://[Scale Out Master service DNS host name]:[Master Port]'`. 

## <a name="9-add-the-scale-out-workers"></a>9. Adicionar os Trabalhos do Scale Out

Agora, você pode adicionar Trabalhos do Scale Out com a ajuda do [Gerenciador do Integration Services Scale Out](integration-services-ssis-scale-out-manager.md). Insira `[SQL Server Availability Group Listener DNS name],[Port]` na página de conexão.

## <a name="next-steps"></a>Próximas etapas
Para saber mais, veja os tópicos a seguir:
-   [Mestre do SSIS (Integration Services) Scale Out](integration-services-ssis-scale-out-master.md)
-   [Trabalho do SSIS (Integration Services) Scale Out](integration-services-ssis-scale-out-worker.md)