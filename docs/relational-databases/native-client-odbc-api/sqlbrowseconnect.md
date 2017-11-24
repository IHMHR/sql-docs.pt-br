---
title: SQLBrowseConnect | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLBrowseConnect function
ms.assetid: 57faf388-c7ca-4696-9845-34e0a10cc5f7
caps.latest.revision: "54"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cbe505cb8cd07efc04274725513dd8143bec688f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="sqlbrowseconnect"></a>SQLBrowseConnect
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLBrowseConnect** usa palavras-chave que podem ser categorizadas em três níveis de informações de conexão. Para cada palavra-chave, a tabela a seguir indica se uma lista de valores válidos é retornada e se a palavra-chave é opcional.  
  
## <a name="level-1"></a>Nível 1  
  
|Palavra-chave|Lista retornada?|Opcional?|Description|  
|-------------|--------------------|---------------|-----------------|  
|DSN|N/A|Não|Nome da fonte de dados retornada por **SQLDataSources**. A palavra-chave DSN não poderá ser usada se a palavra-chave DRIVER for usada.|  
|DRIVER|N/A|Não|Microsoft® [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nome do driver ODBC do Native Client é {[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11}. A palavra-chave DRIVER não pode ser usada se a palavra-chave DSN for usada.|  
  
## <a name="level-2"></a>Nível 2  
  
|Palavra-chave|Lista retornada?|Opcional?|Description|  
|-------------|--------------------|---------------|-----------------|  
|SERVER|Sim|Não|O nome do servidor na rede onde a fonte de dados reside. O termo "(local)" pode ser inserido como o servidor; nesse caso uma cópia local do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pode ser usada, mesmo quando se trata de uma versão sem-rede.|  
|UID|Não|Sim|ID de logon do usuário.|  
|PWD|Não|Sim (depende do usuário)|Senha especificada pelo usuário.|  
|APP|Não|Sim|Nome do aplicativo que chama **SQLBrowseConnect**.|  
|WSID|Não|Sim|ID da estação de trabalho. Normalmente, é o nome de rede do computador no qual o aplicativo é executado.|  
  
## <a name="level-3"></a>Nível 3  
  
|Palavra-chave|Lista retornada?|Opcional?|Description|  
|-------------|--------------------|---------------|-----------------|  
|DATABASE|Sim|Sim|O nome do banco de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|LANGUAGE|Sim|Sim|O idioma nacional usado por [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 **SQLBrowseConnect** ignora os valores do banco de dados e LINGUAGEM de palavras-chave armazenados nas definições de fonte de dados ODBC. Se o banco de dados ou o idioma especificado na cadeia de conexão passada para **SQLBrowseConnect** é inválido, **SQLBrowseConnect** retorna SQL_NEED_DATA e os atributos de conexão de nível 3.  
  
 Os seguintes atributos são definidos chamando [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md), determinar o conjunto de resultados retornado por **SQLBrowseConnect**.  
  
|Atributo|Description|  
|---------------|-----------------|  
|SQL_COPT_SS_BROWSE_CONNECT|Se ele for definido como SQL_MORE_INFO_YES, **SQLBrowseConnect** retorna uma cadeia de caracteres estendida de propriedades do servidor.<br /><br /> A seguir está um exemplo de cadeia de caracteres estendida retornada por **SQLBrowseConnect**:<br /><br /> <br /><br /> `ServerName\InstanceName;Clustered:No;Version:8.00.131`<br /><br /> <br /><br /> Nessa cadeia de caracteres, ponto-e-vírgulas separam várias partes das informações sobre o servidor. Use vírgulas para separar diferentes instâncias do servidor.|  
|SQL_COPT_SS_BROWSE_SERVER|Se for especificado um nome de servidor, **SQLBrowseConnect** retornará informações para o servidor especificado. Se SQL_COPT_SS_BROWSE_SERVER estiver definido como NULL, **SQLBrowseConnect** retorna informações para todos os servidores no domínio.<br /><br /> <br /><br /> Observe que, devido a problemas de rede, **SQLBrowseConnect** pode não receber uma resposta oportuna de todos os servidores. Portanto, a lista de servidores retornada pode variar para cada solicitação.|  
|SQL_COPT_SS_BROWSE_CACHE_DATA|Quando o atributo SQL_COPT_SS_BROWSE_CACHE_DATA é definido como SQL_CACHE_DATA_YES, você pode buscar dados em partes quando o comprimento do buffer não é grande o suficiente para manter o resultado. Esse comprimento é especificado no argumento BufferLength para SQLBrowseConnect.<br /><br /> SQL_NEED_DATA é retornado quando mais dados estiverem disponíveis. SQL_SUCCESS é retornado quando não há mais dados a serem recuperados.<br /><br /> O padrão é SQL_CACHE_DATA_NO.|  
  
## <a name="sqlbrowseconnect-support-for-high-availability-disaster-recovery"></a>Suporte de SQLBrowseConnect a alta disponibilidade e recuperação de desastre  
 Para obter mais informações sobre como usar **SQLBrowseConnect** para se conectar a um [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] de cluster, consulte [SQL Server Native Client Support for High Availability, Disaster Recovery](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqlbrowseconnect-support-for-service-principal-names-spns"></a>Suporte de SQLBrowseConnect a SPNs (nomes de entidade de serviço)  
 Quando uma conexão é aberta, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client define SQL_COPT_SS_MUTUALLY_AUTHENTICATED e SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD como o método de autenticação usado para abrir a conexão.  
  
 Para obter mais informações sobre os SPNs, consulte [nomes da entidade de serviço &#40; SPNs &#41; em conexões de cliente &#40; ODBC &#41; ](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="change-history"></a>Histórico de alterações  
  
|Conteúdo atualizado|  
|---------------------|  
|SQL_COPT_SS_BROWSE_CACHE_DATA documentado.|  
  
## <a name="see-also"></a>Consulte também  
 [Função SQLBrowseConnect](http://go.microsoft.com/fwlink/?LinkId=59329)   
 [Detalhes da implementação da API do ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  