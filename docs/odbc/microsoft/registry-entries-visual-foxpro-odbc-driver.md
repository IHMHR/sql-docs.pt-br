---
title: Entradas do registro (Driver ODBC do Visual FoxPro) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registry keys [ODBC]
- Visual FoxPro ODBC driver [ODBC], registry entries
- keys [ODBC]
- FoxPro ODBC driver [ODBC], registry entries
ms.assetid: 1a63d92d-ca3a-46ae-911f-6788292c801e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6a975ff73eb4b2ef48af05ccfdf595ae9c3233f0
ms.contentlocale: pt-br
ms.lasthandoff: 09/09/2017

---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>Entradas do registro (Driver ODBC do Visual FoxPro)
Quando você instala o Driver de ODBC do Visual FoxPro, o programa de instalação atualiza o registro do sistema, na chave do registro HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCInst.ini, para adicionar uma nova chave chamada Microsoft Visual FoxPro Driver. Sob essa chave, valores descritos na tabela a seguir são adicionados.  
  
|Nome do valor|Tipo de valor|Valor|  
|----------------|----------------|-----------|  
|APILevel|REG_SZ|"1"|  
|ConnectFunctions|REG_SZ|"YYN"|  
|Driver|REG_SZ|Caminho do sistema para o arquivo vfpodbc|  
|DriverODBCVer|REG_SZ|"02.50"|  
|FileExtns|REG_SZ|"*. dbf,\*. cdx\*.fpt"|  
|FileUsage|REG_SZ|"1"|  
|Instalação|REG_SZ|Caminho do sistema para o arquivo vfpodbc|  
|SQLLevel|REG_SZ|"0"|  
  
 O programa de instalação também adiciona a chave "Visual FoxPro arquivos", que representa o driver do Visual FoxPro padrão, a chave de HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini do sistema. Sob essa chave, o programa de instalação adiciona os valores descritos na tabela a seguir.  
  
|Nome do valor|Tipo de valor|Valor|  
|----------------|----------------|-----------|  
|Driver|REG_SZ|Caminho do sistema para o arquivo vfpodbc|  
  
 Cada vez que você adicionar uma fonte de dados do Visual FoxPro ODBC para sua configuração de ODBC, uma nova chave é adicionada para esse nome de fonte de dados. Os valores da fonte de dados correspondem aos valores definidos no **a instalação do Visual FoxPro ODBC** caixa de diálogo, conforme listado na tabela a seguir.  
  
|Nome do valor (palavra-chave)|Tipo de valor|Valor|  
|----------------------------|----------------|-----------|  
|Agrupar|REG_SQ|Nenhum suporte para a sequência de agrupamento|  
|Description|REG_SZ|Descrição da fonte de dados do usuário|  
|Driver||Caminho do sistema para o arquivo vfpodbc|  
|Exclusive||Sim ou não|  
|BackgroundFetch||Sim ou não|  
|SourceDB|REG_SZ|Caminho. Arquivo DBC|  
|SourceType|REG_SZ|"DBC" ou "DBF"|  
  
 Você não deve acessar essas informações diretamente. qualquer administração do registro é tratada pelo administrador de ODBC quando você adicionar, modificar ou excluir uma fonte de dados.  
  
 Você pode usar algumas dessas palavras-chave e valores como parâmetros de [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) função da API do ODBC.