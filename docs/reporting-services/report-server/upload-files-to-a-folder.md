---
title: Carregar arquivos em uma pasta | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-server
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
- files [Reporting Services]
- folders [Reporting Services], uploading files to
ms.assetid: 2f99a288-d4aa-4c64-b310-e457a2aef2c5
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: dc7ec7802dc229fe3272f6204d3aede698ede150
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="upload-files-to-a-folder"></a>Carregar arquivos em uma pasta
  Você pode carregar arquivos do sistema de arquivos e armazená-los como itens gerenciados em um banco de dados do servidor de relatório. O que acontece quando o arquivo é carregado depende do tipo de arquivo.  
  
-   Carregar um arquivo .rdl é equivalente a publicar um relatório.  
  
-   O carregamento de qualquer outro arquivo adiciona esse arquivo ao banco de dados do servidor de relatório como um único objeto binário. Esses arquivos são publicados em um servidor de relatório como um recurso. Os recursos podem ser qualquer tipo de arquivo. Se a extensão do arquivo corresponder com um tipo MIME conhecido, um ícone desse tipo MIME será usado para identificar o tipo de recurso. Caso contrário, um ícone de arquivo genérico indica um recurso.  
  
> [!NOTE]  
>  Você não pode carregar um arquivo de fonte de dados de relatório (.rds) para criar uma fonte de dados compartilhada. Um arquivo .rds só é usado no Designer de Relatórios. Esse arquivo não pode fornecer o conteúdo para um item de fonte de dados compartilhada definido e gerenciado pelo Gerenciador de Relatórios. Como alternativa do carregamento, é possível gravar um script que cria uma fonte de dados compartilhada com base em um arquivo .rds.  
  
 O tamanho de arquivo máximo para itens carregados é determinado por [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]. Por padrão, o tamanho máximo é de 4 megabytes (MB).  
  
 Visualmente, os arquivos carregados em um banco de dados do servidor de relatório são representados na hierarquia de pastas com os seguintes ícones.  
  
 ![Ícone Relatório](../../reporting-services/report-server/media/hlp-16doc.gif "Ícone Relatório")  
ícone de relatório  
  
 ![Ícone de modelo](../../reporting-services/report-server/media/model-icon.gif "Ícone de modelo")  
ícone de modelo de relatório  
  
 ![Ícone Recurso genérico](../../reporting-services/report-server/media/hlp-16file.gif "Ícone Recurso genérico")  
ícone de recurso genérico  
  
 Ao ser carregado, o arquivo sempre é colocado na pasta que está selecionada atualmente. Você pode navegar até a pasta na qual deseja incluir o item primeiro ou carregar um arquivo e, em seguida, movê-lo para um local final posteriormente.  
  
 Para carregar um arquivo, use o Gerente de Relatórios. O carregamento de arquivos em um servidor de relatório depende das tarefas que fazem parte de sua atribuição de função. Se a segurança padrão for usada, os administradores locais poderão adicionar itens a um servidor de relatório. Se Meus Relatórios estiver habilitado, qualquer usuário que tiver uma pasta Meus Relatórios terá permissão para carregar itens nessa pasta. Se atribuições de função personalizadas forem utilizadas, a atribuição de função deve incluir tarefas que ofereçam suporte para o gerenciamento de pastas.  
  
|Para fazer isso|Inclua estas tarefas|  
|----------------|-------------------------|  
|Carregar um arquivo .rdl em uma pasta|Gerenciar relatórios|  
|Carregar qualquer arquivo como um objeto binário|Gerenciar recursos|  
|Exibir o conteúdo de uma pasta|Exibir recursos, exibir relatórios|  
  
## <a name="see-also"></a>Consulte Também  
 [Gerenciador de Relatórios &#40;Modo Nativo do SSRS&#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)   
 [Concedendo permissões em um servidor de relatório no modo nativo](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)   
 [Tarefas e permissões](../../reporting-services/security/tasks-and-permissions.md)   
 [Carregar um arquivo ou relatório &#40;Gerenciador de Relatórios&#41;](../../reporting-services/reports/upload-a-file-or-report-report-manager.md)  
  
  
