---
title: Administrar servidores com o SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], administering
ms.assetid: 938bb035-e07a-4082-9f93-229d9feb6b06
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 024175506b041ae9c62585dbdcc05da4b84bea02
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="administer-servers-with-sql-server-management-studio"></a>Gerenciar servidores com o SQL Server Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[msCoName](../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] é um cliente administrativo rico e integrado, projetado para satisfazer os requisitos de gerenciamento de servidor do administrador do [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] e do Banco de Dados SQL do Azure. No [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)], as tarefas administrativas são realizadas com o Pesquisador de Objetos, que permite conectar-se a qualquer servidor da família [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] e procurar conteúdo de forma gráfica. Um servidor pode ser uma instância do [!INCLUDE[ssDE](../includes/ssde_md.md)], do [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)], do [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion_md.md)], do [!INCLUDE[ssISnoversion](../includes/ssisnoversion_md.md)] ou do Banco de Dados SQL do Azure.  
  
Os componentes de ferramentas do [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] incluem os Servidores Registrados, o Pesquisador de Objetos, o Gerenciador de Soluções, o Explorador de Modelos, a página Detalhes do Pesquisador de Objetos e a janela de documentos. Para exibir uma ferramenta, no menu **Exibir** , clique no nome da ferramenta. Para exibir a ferramenta Editor de Consultas, clique no botão **Nova Consulta** na barra de ferramentas.  
  
> [!IMPORTANT]  
> O tráfego de rede entre o [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] e o [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] não é criptografado por padrão. Não trabalhe com dados confidenciais (inclusive senhas) no [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] a menos que você tenha definido uma conexão criptografada. Para obter mais informações, veja [Como habilitar conexões criptografadas no Mecanismo de Banco de Dados (SQL Server Configuration Manager)](http://msdn.microsoft.com/en-us/e1e55519-97ec-4404-81ef-881da3b42006).  
  
Use o [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] para:  
  
-   Servidores registrados.  
  
-   Conecte-se a uma instância do [!INCLUDE[ssDE](../includes/ssde_md.md)], do [!INCLUDE[ssAS](../includes/ssas_md.md)], do [!INCLUDE[ssRS](../includes/ssrs_md.md)], do  [!INCLUDE[ssIS](../includes/ssis_md.md)] ou do Banco de Dados SQL do Azure.  
  
-   Configurar propriedades de servidor.  
  
-   Gerenciar banco de dados e objetos [!INCLUDE[ssAS](../includes/ssas_md.md)] , como cubos, dimensões e assemblies.  
  
-   Criar objetos, como bancos de dados, tabelas, cubos, usuários de banco de dados e logons.  
  
-   Administrar arquivos e grupos de arquivos.  
  
-   Anexar ou desanexar bancos de dados.  
  
-   Iniciar ferramentas de script.  
  
-   Administrar segurança.  
  
-   Exibir logs do sistema.  
  
-   Monitorar a atividade atual.  
  
-   Configurar replicação.  
  
-   Administrar índices de texto completo.  
  
Para iniciar e parar o [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] ou o [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] Agent, use o [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] Configuration Manager.  
  
## <a name="see-also"></a>Consulte Também  
[Usar o SQL Server Management Studio](../ssms/use-sql-server-management-studio.md)  
[Como exibir propriedades do servidor (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/55f3ac04-5626-4ad2-96bd-a1f1b079659d)  
  
