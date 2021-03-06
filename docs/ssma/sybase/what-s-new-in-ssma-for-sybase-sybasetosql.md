---
title: Novidades do SSMA para SAP ASE (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 2be0cf8d-6dbe-443a-abbd-036249922205
caps.latest.revision: 21
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 86a54f8dce44607b91437a89043ff98fdd670ad5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="whats-new-in-ssma-for-sap-ase-sybasetosql"></a>Novidades do SSMA para SAP ASE (SybaseToSQL)
Este tópico lista SSMA para alterações de SAP ASE (anteriormente SSMA para Sybase) em cada versão. 

## <a name="ssma-v77"></a>O SSMA v7.7
A versão v7.7 do SSMA para SAP ASE contém as seguintes alterações:
- SSMA para SAP ASE foi aprimorado com correções de destino que melhoram a métrica de qualidade e a conversão.
- A versão de 32 bits do SSMA para SAP ASE com base na demanda popular, está de volta. Em comparação com a implementação anterior (antes da v 7.4), existem dois pacotes de instalador, mas eles não podem ser instalados lado a lado. Como resultado, você deve escolher a versão mais adequada com base nos componentes de conectividade, que você tem. Sempre é preferível usar a versão de 64 bits, se possível.

> [!IMPORTANT]
> Com a v 7.4 do SSMA e versões posteriores, o .net 4.5.2 é um pré-requisito de instalação.

## <a name="ssma-v76"></a>O SSMA v7.6
A versão v7.6 do SSMA para SAP ASE contém as seguintes alterações:
- SSMA para SAP ASE foi aprimorado com correções de destino que melhoram a qualidade e a conversão de métricas e com suporte para SQL Server 2017 (visualização pública). Suporte para SQL Server 2017 em Windows e Linux está em visualização pública e não deve ser usado para migrações de produção.
- SSMA para SAP ASE foi atualizado para dar suporte à conversão do Sybase funções.

> [!IMPORTANT]
> Com v 7.4 do SSMA e versões posteriores, .net 4.5.2 é um pré-requisito de instalação e a versão de 32 bits da ferramenta foi descontinuada.

## <a name="ssma-v75"></a>V 7.5 do SSMA
A versão v 7.5 do SSMA para SAP ASE contém as seguintes alterações:
-   Aprimorado com vários aprimoramentos para assegurar maior acessibilidade para pessoas com deficiências.
-   Atualizado para oferecer suporte para sintaxe criar ou substituir.

> [!IMPORTANT]
> O .net 4.5.2 é um pré-requisito de instalação v SSMA 7.5. Além disso, começando com v 7.4, a versão de 32 bits do SSMA está sendo descontinuada.  

## <a name="ssma-v74"></a>V 7.4 do SSMA
A versão v 7.4 do SSMA for Sybase contém as seguintes alterações:
- O **tempo limite da consulta** opção agora está disponível durante a descoberta de objeto de esquema na origem e no destino.
![opção de tempo limite de consulta](../media/query-timeout_red.png)
- A métrica de qualidade e a conversão foi aprimorada com correções de destino, com base nos comentários dos clientes.

> [!IMPORTANT]
> O .net 4.5.2 é um pré-requisito de instalação v 7.4 do SSMA. Além disso, começando com v 7.4, a versão de 32 bits do SSMA está sendo descontinuada.  

## <a name="ssma-v73"></a>O SSMA 7.3
A versão 7.3 do SSMA for Sybase contém as seguintes alterações:
- Métrica de qualidade e conversão aprimorada com correções de destino com base nos comentários dos clientes.
- Estrutura de extensibilidade do SSMA exposta por meio de itens a seguir:
  - Exporte funcionalidade a um projeto do SQL Server Data Tools (SSDT).
    -   Agora você pode exportar os scripts de esquema do SSMA para um projeto do SSDT. Você pode usar os scripts de esquema para fazer alterações de esquema adicionais e implantar seu banco de dados.
![Comando de projeto SSDT Salvar como](../media/export-schema-scripts_red.png)
  - Bibliotecas que podem ser consumidas por SSMA para realizar conversões personalizados.
    - Agora você pode construir o código que pode lidar com conversões de sintaxe personalizada e conversões que anteriormente não foram manipulados por SSMA.
      - Instruções sobre como construir um conversor personalizado estão disponíveis nesta postagem de blog, [recursos de conversão do estendendo o SQL Server Migration Assistant](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/).
      - Projeto de exemplo para a conversão pode ser baixar este [postagem de blog](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/).

## <a name="ssma-v72"></a>V 7.2 do SSMA
A versão v 7.2 do SSMA for Sybase contém as seguintes alterações:
- Métrica de qualidade e conversão aprimorada com correções de destino com base nos comentários dos clientes.
- Aprimoramentos de telemetria para fornecer melhor pontos de dados para solucionar problemas do cliente e melhorar as taxas de conversão do SSMA.

## <a name="ssma-v71"></a>V 7.1 do SSMA
A versão v 7.1 do SSMA para Access contém as seguintes alterações:
- 2017 do SQL Server no Windows e Linux CTP1 agora é uma plataforma de destino com suporte para migração. Este recurso está na visualização técnica e oferece suporte à movimentação de dados e esquema para servidores de SQL de destino.
- O SSMA agora dá suporte a atualizações automáticas para baixar a versão mais recente do SSMA assim que ele está disponível.
- Binários instaláveis do SSMA agora são entregues por meio de arquivos de pacote do Windows installer (. msi).

**Recursos**

[Estendendo o recursos de conversão do SQL Server Migration Assistant](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)

[Avaliar e migrar dados de plataformas de dados não Microsoft para SQL Server *(com exemplo de Oracle)*](https://blogs.msdn.microsoft.com/datamigration/2016/11/16/sql-server-migration-assistant-how-to-assess-and-migrate-databases-from-non-microsoft-data-platforms-to-sql-server/) 

## <a name="may-2016"></a>Maio de 2016  
A versão de maio de 2016 do SSMA for Sybase contém as seguintes alterações:  

-  Adicionado suporte para SQL Server 2016.
-  Removida a seleção de instalador para .net 2.0.
-  Dependência do pacote de extensão atualizada do .net 3.5 para o .net 4.0.
-  Fixa "salvar o projeto" e "Abrir projeto" comandos do Console SSMA.
-  Comando fixa "securepassword" para o Console do SSMA.
-  Correção de contagem de objetos para o carregamento inicial.
-  Correção do bug nas configurações globais.

## <a name="march-2016"></a>Março de 2016  
A versão de visualização de março de 2016 do SSMA for Sybase contém as seguintes alterações:  
  
-  Adicionado suporte para migração para o SQL Server 2016.  
  
## <a name="january-2016"></a>Janeiro de 2016  
A versão de manutenção de janeiro de 2016 do SSMA for Sybase contém as seguintes alterações:  
  
-  Item de Menu de Log de exibição adicionado para o SSMA (RFC 5706203).  
-  Telemetria adicionada. 
  
## <a name="july-2014"></a>Julho de 2014  
A versão de julho de 2014 do SSMA for Sybase contém as seguintes alterações:  
  
-  Conversão de código de banco de dados do Azure SQL aprimorado.  
-  Movido funcionalidade do pacote de extensão para o esquema para oferecer suporte a banco de dados de SQL do Azure.  
-  Melhorias de desempenho adicionados testado para bancos de dados com mais de 10 mil objetos.  
-  Aprimoramentos da interface do usuário adicionais para lidar com um grande número de objetos.  
-  Adicionada a habilidade para realçar "bem conhecidas" esquemas LOB (de modo que podem ser ignoradas na conversão).  
-  Melhorias de velocidade de conversão adicional.  
-  Adicionada a habilidade de Mostrar contagens de objetos na interface do usuário. 
-  Tamanho do relatório reduzida em mais de 25%.  
-  Mensagens de erro aprimoradas para construções não analisadas.  
  
## <a name="april-2014"></a>Abril de 2014  
A versão de abril de 2014 do SSMA for Sybase contém as seguintes alterações:  
  
-   Adicionado suporte do MS SQL Server 2014.  
-   Bugs corrigidos sobre conversão para o Azure.  
-   Bugs corrigidos sobre páginas de relatório invisível no Internet Explorer 10.  
  
## <a name="january-2012"></a>Janeiro de 2012  
A versão de janeiro de 2012 do SSMA for Sybase contém as seguintes alterações:  
  
-   Adicionado suporte para conversão de gatilho de reversão.  
-   Fornecida a correção para converter@ROWCOUNT e @@ERROR na mesma instrução SET.  
  
## <a name="july-2011"></a>Julho de 2011  
A versão de julho de 2011 do SSMA for Sybase contém as seguintes alterações:  
  
-   Melhor relatórios de erros durante a migração de dados.  
  
## <a name="april-2011"></a>Abril de 2011  
A versão de abril de 2011 do SSMA for Sybase contém as seguintes alterações:  
  
-   Produto "SSMA para Sybase" consolidado, o que dá suporte a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "Denali" e SQL Azure.  
-   Adicionado suporte para a conexão e a migração para [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "Denali".  
-   Adicionado um novo recurso para converter e migrar bancos de dados Sybase para o SQL Azure.  
-   Mecanismo de migração aprimorada de dados do lado do cliente, dando suporte a migração paralela de dados.  
-   Desempenho de migração de dados aprimorada com simples e Bulk logged modelos de recuperação.  
-   Adicionada a capacidade de converter corretamente e migrar bancos de dados Sybase diferencia maiusculas de minúsculas para maiusculas e minúsculas do SQL Server.  
-   Adicionado suporte para conversão de instruções de junção do Sybase ASE não-ANSI para instruções de junção ANSI do SQL Server foi estendido para excluir e atualizar as instruções.  
-   Fornecer opções de conectividade adicional para conectar a servidores Sybase ASE usando o provedor do Sybase ASE ODBC e provedores Sybase ASE ADO.Net.  
-   Remover a dependência em um banco de dados separado chamado **SysDB**, que contém as funções de emulação do Sybase (instaladas como parte do pacote de extensão).  
-   Adicionada a habilidade para instalar o SSMA para Sybase pacote de extensão no [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] clusters.  
-   Adicionada compatibilidade com versões anteriores de projetos criados por versões anteriores do SSMA (v 4.0 e v 4.2).  
-   Adicionada a capacidade de instalar o SSMA para Sybase v 5.0 produto-lado a lado (SxS) com as versões mais antigas do SSMA (v 4.0 e v 4.2).  
  
## <a name="july-2010"></a>Julho de 2010  
A versão de julho de 2010 do SSMA for Sybase contém as seguintes alterações:  
  
-   Adicionado suporte para migração para o SQL Server 2008 R2.  
-   Adicionado um novo aplicativo de Console SSMA para execução de linha de comando.  
-   Adicionado suporte para migração de dados usando os mecanismos de migração de dados do lado do cliente e do servidor.  
-   Adicionado suporte para a instrução "SELECT personalizado" na migração de dados.  
-   Adicionado suporte para migração do Sybase ASE 15.0.3 e 15,5.  
  
## <a name="june-2008"></a>Junho de 2008  
A versão de junho de 2008 do SSMA for Sybase contém as seguintes alterações:  
  
-   Adicionado o SSMA testador, que testa automaticamente a conversão do objeto de banco de dados e a migração de dados feitas pelo SSMA. Depois que todas as etapas de migração do SSMA estiverem concluídas, use o SSMA testador para verificar objetos convertidos funcionam da mesma forma e que todos os dados foi transferido corretamente.  
-   Conversão de versão anterior do SQL adicionado. Usuário agora pode especificar tabela temporária (e outro objeto) declarações para cada procedimento de origem a ser usada na conversão.  
-   Foram incluídos aperfeiçoamentos na conversão do objeto:  
    -   Une conversão revisado.  
    -   Agregações e agregações sem tem que/grupo por cláusulas.  
    -   A função de identidade com uma instrução SELECT INTO.  
    -   Restrições em cluster e índices em somente dados bloqueados.  
    -   Tabelas temporárias criadas pelo SELECT INTO.  
    -   Restrições de / índices para tabelas temporárias.  
    -   Novo [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] há suporte para tipos de data/hora de 2008.  
    -   Suporte a tipos de dados e conectividade 15.0 Sybase.  
  
## <a name="may-2007"></a>Maio de 2007  
A versão de maio de 2007 do SSMA for Sybase contém as seguintes alterações:  
  
-   Adicionada a capacidade de carregar o conteúdo do banco de dados mais rapidamente ao salvar um projeto.  
-   Adicionado suporte para comentários inseridos pelo usuário no SQL Server formatada de modo SQL.  
-   Foram incluídos aperfeiçoamentos na conversão do objeto.  
  
O arquivo de Ajuda não foi atualizado para esta versão. Para obter mais informações, consulte a seção Notas da documentação mais adiante neste tópico.  
  
## <a name="november-2006"></a>Novembro de 2006  
A versão de novembro de 2006 do SSMA for Sybase contém as seguintes alterações:  
  
-   Adicionadas novas configurações globais:  
    -   Você pode optar por mostrar números de linha na janela do editor.  
    -   Você pode configurar o SSMA para perguntar antes de substituir objetos duplicados ou sempre ou nunca substituir objetos duplicados durante a conversão do esquema.  
-   Adicionou uma nova opção de conversão que lhe permite configurar como o SSMA trata as situações a seguir:  
    -   Uma instrução CAST ou CONVERT que contém uma cadeia de caracteres binária.  
    -   Verifica se há valores nulos em expressões de igualdade.  
    -   Tabelas de proxy.  
    -   Números de erro da mensagem de usuário para RAISERROR.  
    -   Instruções de atualização que contêm identificadores não resolvidos.  
-   Adicionou uma nova opção de migração que lhe permite especificar como o SSMA deve manipular datas que estão fora de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] intervalo de datas.  
-   Adicionado um **formatado SQL** definição no **SQL** guia, que formata o código para melhor legibilidade.  
-   Correções de bug que incluem o seguinte:  
    -   O SSMA agora converte o bloqueio de tabela *tabela* IN {compartilhado | Instruções de modo exclusivo} com a adição de uma dica TABLOCK ou TABLOCKX para a consulta SELECT subsequente na tabela.  
    -   As conversões necessárias agora são adicionadas quando tipos binários são usados em expressões de caractere.  
    -   Melhorias de desempenho e de memória.  
  
## <a name="july-2006"></a>Julho de 2006  
A versão de julho de 2006 do SSMA for Sybase foi a versão inicial.  
  
## <a name="see-also"></a>Consulte também  
[Introdução ao SSMA for Sybase &#40;SybaseToSQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)
