---
title: Introdução ao monitoramento do Analysis Services com o SQL Server Profiler | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7b3c2dcec84956cd83c09a6c9be1d70975df67cc
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="introduction-to-monitoring-analysis-services-with-sql-server-profiler"></a>Introdução ao monitoramento do Analysis Services com o SQL Server Profiler
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  É possível usar o [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] para monitorar eventos gerados por uma instância do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Usando o [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], você pode fazer o seguinte:  
  
-   Monitorar o desempenho de uma instância do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
-   Depurar as instruções da linguagem MDX.  
  
-   Identificar as instruções MDX executadas lentamente.  
  
-   Testar as instruções MDX na fase de desenvolvimento de um projeto, percorrendo as instruções para confirmar se o código funciona conforme o esperado.  
  
-   Solucionar problemas no [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] capturando eventos em um sistema de produção e repeti-los em um sistema de teste. Essa abordagem é útil para testar ou depurar propósitos e permite que os usuários continuem a usar o sistema de produção sem interferência.  
  
-   Auditar e revisar atividades ocorridas em uma instância do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Um administrador de segurança pode revisar qualquer um dos eventos auditados. A revisão inclui o êxito ou a falha de uma tentativa de logon e o êxito ou a falha das permissões ao acessar instruções e objetos.  
  
-   Exibir dados sobre os eventos capturados na tela ou capturar e salvar dados sobre cada evento em um arquivo ou na tabela do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para análise ou reprodução futura. Ao repetir os dados, é possível executar novamente os eventos salvos conforme ocorreram originalmente, seja em tempo real ou passo a passo.  
  
## <a name="using-sql-server-profiler"></a>Usando o SQL Server Profiler  
 Para usar o [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] para criar ou repetir rastreamentos, você deve ser um membro da função de servidor [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Se você for um membro da função de servidor [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , inicie o [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] a partir do grupo de programas [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no menu **Iniciar** .  
  
 Ao usar o [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], observe o seguinte:  
  
-   As definições de rastreamento são armazenadas no banco de dados do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] usando a instrução CREATE.  
  
-   Vários rastreamentos podem ser executados ao mesmo tempo.  
  
-   Várias conexões podem receber eventos do mesmo rastreamento.  
  
-   Um rastreamento pode continuar quando o [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] parar e for reiniciado.  
  
    > [!NOTE]  
    >  As senhas não são reveladas em eventos de rastreamento, mas são substituídas por ****** no evento.  
  
 Para obter o desempenho ideal, use o [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] para monitorar somente os eventos pelos quais você tem maior interesse. O monitoramento de muitos eventos pode causar sobrecarga e aumentar muito a tabela ou o arquivo de rastreamento, especialmente durante o monitoramento em um longo período de tempo. Além disso, use a filtragem para limitar a quantidade de dados coletados e impedir o aumento em excesso dos rastreamentos.  
  
## <a name="see-also"></a>Consulte também  
 [Eventos de rastreamento do Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)   
 [Criar rastreamentos do Profiler para reprodução & #40; Analysis Services & #41;](../../analysis-services/instances/create-profiler-traces-for-replay-analysis-services.md)  
  
  
