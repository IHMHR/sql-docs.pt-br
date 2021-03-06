---
title: Especificar conexões para extensões de processamento de dados personalizadas | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-data
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- custom data processing extensions [Reporting Services]
- IDbConnection interface, connection strings
- impersonation [Reporting Services]
- IDbConnectionExtension interface, connection strings
- data sources [Reporting Services], security
- connection strings [Reporting Services]
- credentials [Reporting Services]
- authentication [Reporting Services]
- external data sources [Reporting Services]
- data processing extensions [Reporting Services], connections
ms.assetid: 2cddc9ea-0e28-4350-80ae-332412908e47
caps.latest.revision: 20
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f1bef72f7a07df727462e569c8b0971dcfa2f696
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="specify-connections-for-custom-data-processing-extensions"></a>Especificar conexões para extensões de processamento de dados personalizadas
  Você pode criar ou usar extensões de processamento de dados personalizados de terceiros em um servidor de relatório para aprimorar o recurso de processamento das fontes de dados compatíveis ou para oferecer suporte a tipos adicionais de fontes de dados que não estão disponíveis em uma instalação padrão do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . As conexões são tratadas de modo diferente dependendo da implementação. As implementações a seguir estão disponíveis para extensões de processamento de dados:  
  
-   Provedores de dados [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] personalizados (se os dados forem acessados por meio de fontes de dados DB2.NET, Oracle, ODP.NET ou Teradata, você poderá usar um provedor de dados .NET personalizados)  
  
-   Extensões de processamento de dados personalizados que dão suporte para <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>  
  
-   Extensões de processamento de dados personalizados que dão suporte para <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>  
  
> [!NOTE]  
>  Entre em contato com seu provedor de terceiros para saber como sua extensão de processamento de dados personalizados é implementada.  
  
## <a name="impersonation-and-custom-data-processing-extensions"></a>Representação e extensões de processamento de dados personalizados  
 Se a sua extensão de processamento de dados personalizados se conecta a fontes de dados que usam a representação, use o método Open nas interfaces <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> ou <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> para fazer a solicitação. Se preferir, armazene o objeto de identidade de usuário (System.Security.Principal.WindowsIdentity) e, em seguida, reutilize-o nas outras APIs de extensão de processamento de dados.  
  
 Em versões anteriores do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], todas as extensões de processamento de dados personalizados eram chamadas de acordo com a representação de usuário. Nesta versão, somente o método Open será chamado conforme a representação do usuário. Se houver uma extensão de processamento de dados existente que precise de segurança integrada, modifique seu código para usar o método Open ou armazenar o objeto de identidade de usuário.  
  
## <a name="connections-for-custom-net-framework-data-providers"></a>Conexões para provedores de dados personalizados do .NET Framework  
 Ao configurar um relatório para usar uma fonte de dados específica, defina propriedades que determinam o tipo da fonte de dados, a cadeia de conexão e as credenciais, usados para acessar a fonte de dados. A tabela a seguir descreve os tipos de credencial com suporte nos provedores de dados [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . Para obter mais informações sobre como definir propriedades de fontes de dados de relatórios, confira [Especificar informações de credenciais e de conexão para fontes de dados de relatório](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md).  
  
|Credenciais|Conexões|  
|-----------------|-----------------|  
|Segurança integrada|Se o provedor de dados oferecer suporte para esse recurso, use a segurança integrada do Windows. A solicitação é enviada com as credenciais do usuário atual.<br /><br /> Ao definir a cadeia de conexão, não se esqueça de incluir argumentos que especificam a segurança integrada (por exemplo, uma conexão com uma fonte de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pode incluir **Integrated Security=SSPI** na cadeia de conexão).|  
|Autenticação do Windows|Se o provedor de dados oferecer suporte para esse recurso, use uma conta de usuário de domínio do Windows. O servidor de relatório representa a conta de usuário antes que a extensão de processamento de dados seja chamada.<br /><br /> Ao definir a cadeia de conexão, não se esqueça de incluir argumentos que especificam a segurança integrada (por exemplo, uma conexão com uma fonte de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pode incluir **Integrated Security=SSPI** na cadeia de conexão).|  
|Credenciais de banco de dados|As conexões feitas por um provedor de dados .NET personalizados não oferecem suporte para a autenticação de banco de dados. Em todos os casos, o servidor de relatório interromperá a conexão.|  
|Nenhuma credencial|Você pode usar a opção Nenhuma credencial com provedores de dados .NET personalizados. Se a conta de execução autônoma for especificada, a cadeia de conexão determinará as credenciais que são usadas. O servidor de relatório representa a conta de execução autônoma para fazer a conexão.<br /><br /> Se a conta de execução autônoma não for definida, o servidor de relatório interromperá a conexão. Para obter mais informações sobre como definir a conta, consulte [Configurar a conta de execução autônoma &#40;Gerenciador de configurações do SSRS&#41;](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).|  
  
## <a name="connections-for-idbconnection"></a>Conexões para IDbConnection  
 Se você estiver usando uma extensão de processamento de dados personalizados que dá suporte somente para <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>, especifique a conexão da seguinte maneira:  
  
1.  Configure a conta de execução autônoma. A conexão dessa conta é obrigatória para conexões feitas com **IDbConnection**. O servidor de relatório representa a conta ao fazer a conexão.  
  
2.  Configure as propriedades de fonte de dados no relatório para usar **Nenhuma credencial**.  
  
3.  Coloque as credenciais usadas para conectar-se à fonte de dados na cadeia de conexão.  
  
 Ao usar **IDbConnection**, os seguintes tipos de credencial não têm suporte: segurança integrada, contas de usuário do Windows e credenciais de banco de dados. Se uma conexão de fonte de dados usar essas opções, a conexão será interrompida no servidor de relatório.  
  
## <a name="connections-for-idbconnectionextension"></a>Conexões para IDbConnectionExtension  
 Se você estiver usando uma extensão de processamento de dados personalizados que dá suporte para <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>, especifique a conexão da seguinte maneira:  
  
|Credenciais|Conexões|  
|-----------------|-----------------|  
|Segurança integrada|Se o provedor de dados der suporte para esse recurso, use a segurança integrada do Windows com extensões de processamento de dados personalizados que usam **IDbConnectionExtension**.<br /><br /> Ao definir a cadeia de conexão, não se esqueça de incluir argumentos que especificam a segurança integrada (por exemplo, uma conexão com uma fonte de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pode incluir **Integrated Security=SSPI** na cadeia de conexão).|  
|Autenticação do Windows|Se o provedor de dados der suporte para esse recurso, use uma conta de usuário do domínio do Windows para extensões de processamento de dados personalizados que usam **IDbConnectionExtension**.<br /><br /> O servidor de relatório representa a conta de usuário antes que a extensão de processamento de dados seja chamada. Ao definir a cadeia de conexão, não se esqueça de incluir argumentos que especificam a segurança integrada (por exemplo, uma conexão com uma fonte de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pode incluir **Integrated Security=SSPI** na cadeia de conexão).|  
|Credenciais de banco de dados|Você pode usar a autenticação de banco de dados para configurar conexões para extensões de processamento de dados personalizados que usam **IDbConnectionExtension**.|  
|Nenhuma credencial|Se a conta de execução autônoma for especificada, a cadeia de conexão determinará as credenciais que são usadas.<br /><br /> Se a conta de execução autônoma não for definida, o servidor de relatório interromperá a conexão.|  
  
## <a name="see-also"></a>Consulte Também  
 [Configurar a conta de execução autônoma &#40;Gerenciador de configurações do SSRS&#41;](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)   
 [Especificar informações de credenciais e de conexão para fontes de dados de relatório](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Conexões de dados, fontes de dados e cadeias de conexão &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Implementando uma extensão de processamento de dados](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Gerenciador de Relatórios &#40;Modo Nativo do SSRS&#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)   
 [Criar, excluir ou modificar uma fonte de dados compartilhada &#40;Gerenciador de Relatórios&#41;](http://msdn.microsoft.com/library/cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2)   
 [Configurar propriedades de fonte de dados para um relatório &#40;Gerenciador de Relatórios&#41;](../../reporting-services/report-data/configure-data-source-properties-for-a-report-report-manager.md)  
  
  
