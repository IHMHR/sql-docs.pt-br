---
title: Classe de evento Broker:Connection | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: event-classes
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Broker:Connection event class
ms.assetid: d3e505f2-0a43-486f-aa92-9c8e49b2dfea
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8af1659f9f4d7532136a8d21adbf45e0afa77f5b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="brokerconnection-event-class"></a>classe de evento Broker:Connection
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gera um evento **Broker:Connection** para informar o status de uma conexão de transporte gerenciado pelo Service Broker.  
  
## <a name="brokerconnection-event-class-data-columns"></a>Colunas de dados da classe de evento Broker:Connection  
  
|Coluna de dados|Tipo|Description|Número da coluna|Filtrável|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|O nome do aplicativo cliente que criou a conexão com uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Essa coluna é populada com os valores passados pelo aplicativo e não com o nome exibido do programa.|10|Sim|  
|**ClientProcessID**|**int**|A ID atribuída pelo computador host ao processo em que está sendo executado o aplicativo cliente. Essa coluna de dados será populada se a ID do processo do cliente for fornecida pelo cliente.|9|Sim|  
|**DatabaseID**|**int**|A ID do banco de dados especificada pela instrução de *banco de dados* USE ou a ID do banco de dados padrão se nenhuma instrução de *banco de dados*USE tiver sido emitida para determinada instância. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] exibirá o nome do banco de dados se a coluna de dados **ServerName** for capturada no rastreamento e o servidor estiver disponível. Determine o valor de um banco de dados usando a função **DB_ID** .|3|Sim|  
|**Erro**|**int**|O número da ID de mensagem em **sys.messages** para o texto no evento. Se esse evento informar um erro, ele será o número de erro do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|31|não|  
|**EventClass**|**int**|O tipo de classe de evento capturado. Sempre **138** para **Broker:Connection**.|27|não|  
|**EventSequence**|**int**|Número de sequência para esse evento.|51|não|  
|**EventSubClass**|**nvarchar**|O estado da conexão. Para esse evento, a subclasse é um dos valores a seguir.<br /><br /> <br /><br /> **Connecting**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está iniciando uma conexão de transporte.<br /><br /> **Connected**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] estabeleceu uma conexão de transporte.<br /><br /> **Connect Failed**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] falhou em estabelecer uma conexão de transporte.<br /><br /> **Closing**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está encerrando a conexão de transporte.<br /><br /> **Closed**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] encerrou a conexão de transporte.<br /><br /> **Accept**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aceitou uma conexão de transporte de outra instância.<br /><br /> **Send IO Error**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] encontrou um erro de transporte ao enviar uma mensagem.<br /><br /> **Receive IO Error**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] encontrou um erro de transporte ao receber uma mensagem.|21|Sim|  
|**GUID**|**uniqueidentifier**|A ID de ponto de extremidade desta conexão.|54|não|  
|**HostName**|**nvarchar**|O nome do computador no qual o cliente está sendo executado. Essa coluna de dados será populada se o nome do host for fornecido pelo cliente. Para determinar o nome do host, use a função **HOST_NAME** .|8|Sim|  
|**IntegerData**|**int**|O número de horas em que esta conexão esteve fechada.|25|Sim|  
|**IsSystem**|**int**|Indica se o evento ocorreu em um processo do sistema ou do usuário.<br /><br /> 0 = usuário<br /><br /> 1 = sistema|60|não|  
|**LoginSid**|**imagem**|Número SID (identificação de segurança) do usuário que fez logon. Cada SID é exclusivo para cada logon no servidor.|41|Sim|  
|**NTDomainName**|**nvarchar**|O domínio do Windows ao qual o usuário pertence.|7|Sim|  
|**NTUserName**|**nvarchar**|O nome do usuário proprietário da conexão que gerou este evento.|6|Sim|  
|**ObjectName**|**nvarchar**|O identificador de conversa do diálogo.|34|não|  
|**ServerName**|**nvarchar**|O nome da instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que está sendo rastreada.|26|não|  
|**SPID**|**int**|A ID de processo do servidor atribuída pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ao processo associado ao cliente.|12|Sim|  
|**StartTime**|**datetime**|O horário no qual o evento foi iniciado, quando disponível.|14|Sim|  
|**TextData**|**ntext**|O texto da mensagem de erro referente ao evento. Em eventos que não informam um erro, esse campo fica vazio. A mensagem de erro pode ser do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou do Windows.|1|Sim|  
|**TransactionID**|**bigint**|ID da transação atribuída pelo sistema.|4|não|  
  
## <a name="see-also"></a>Consulte Também  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
