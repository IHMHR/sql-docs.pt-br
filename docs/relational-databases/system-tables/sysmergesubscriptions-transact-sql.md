---
title: sysmergesubscriptions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysmergesubscriptions_TSQL
- sysmergesubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergesubscriptions system table
ms.assetid: 6adc78da-991d-4c08-98c3-ecb4762e0e99
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2af51b3b46c9e4a939106ed32ed378d0d5e6cee1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sysmergesubscriptions-transact-sql"></a>sysmergesubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contém uma linha para cada Assinante conhecido e é uma tabela local no Publicador. Essa tabela é armazenada nos bancos de dados de publicação e assinatura.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|subscriber_server|**sysname**|A ID do servidor. Usada para mapear o campo srvid para um valor específico de servidor ao migrar uma cópia do banco de dados de assinatura para um servidor diferente.|  
|db_name|**sysname**|O nome do banco de dados inscrito.|  
|pubid|**uniqueidentifier**|A ID da publicação da qual a assinatura atual foi criada.|  
|datasource_type|**Int**|O tipo de fonte de dados:<br /><br /> **0** = [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> **2** = jet OLE DB.|  
|subid|**uniqueidentifier**|O número de identificação exclusivo para Assinatura.|  
|replnickname|**binary**|O apelido compactado para a réplica.|  
|replicastate|**uniqueidentifier**|Um identificador exclusivo que é usado para determinar se a sincronização anterior teve êxito, comparando o valor no Publicador com o valor no Assinante.|  
|status|**tinyint**|O status da assinatura:<br /><br /> **0** = inativo.<br /><br /> **1** = ativo.<br /><br /> **2** = excluído.|  
|subscriber_type|**Int**|O tipo de assinante:<br /><br /> **1** = global.<br /><br /> **2** = local.<br /><br /> **3** = anônimo.|  
|subscription_type|**Int**|O tipo de assinatura:<br /><br /> **0** = push.<br /><br /> **1** = pull.<br /><br /> **2** = anônimo.|  
|sync_type|**tinyint**|O tipo de sincronização:<br /><br /> **1** = automático.<br /><br /> **2** não = nenhuma sincronização.|  
|descrição|**nvarchar(255)**|Uma descrição breve da assinatura.|  
|priority|**real**|Especifica a prioridade da assinatura e permite a implementação de resolução de conflito com base em prioridade. É igual a **0,00** para todas as assinaturas locais ou anônimas.|  
|recgen|**bigint**|O número da última geração recebida.|  
|recguid|**uniqueidentifier**|A ID exclusiva da última geração recebida.|  
|sentgen|**bigint**|Número da última geração enviada.|  
|sentguid|**uniqueidentifier**|A ID exclusiva da última geração enviada.|  
|schemaversion|**Int**|O número do último esquema recebido.|  
|schemaguid|**uniqueidentifier**|A ID exclusiva do último esquema recebido.|  
|last_validated|**datetime**|O **datetime** da última validação bem-sucedida de dados do assinante.|  
|attempted_validate|**datetime**|A última **datetime** tentativa de validação na assinatura.|  
|last_sync_date|**datetime**|O **datetime** da sincronização.|  
|last_sync_status|**Int**|O status da assinatura:<br /><br /> **0** = todos os trabalhos estão esperando para iniciar.<br /><br /> **1** = um ou mais trabalhos estão iniciando.<br /><br /> **2** = todos os trabalhos foram executados com êxito.<br /><br /> **3** = pelo menos um trabalho está em execução.<br /><br /> **4** = todos os trabalhos estão agendados e ociosos.<br /><br /> **5** = pelo menos um trabalho está tentando executar após uma falha anterior.<br /><br /> **6** = pelo menos um trabalho falhou em executar com êxito.|  
|last_sync_summary|**sysname**|A descrição dos últimos resultados da sincronização.|  
|metadatacleanuptime|**datetime**|A última **datetime** que os metadados expirados foi removido de tabelas do sistema de replicação de mesclagem.|  
|partition_id|**Int**|Identifica a partição pré-computada à qual a assinatura pertence.|  
|cleanedup_unsent_changes|**bit**|Identifica que os metadados de alterações não enviadas foram limpos no Assinante.|  
|replica_version|**Int**|Identifica a versão do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para o Assinante ao qual a assinatura pertence, que pode ser um dos seguintes valores:<br /><br /> **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<br /><br /> **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
|supportability_mode|**Int**|Somente para uso interno.|  
|application_name|**nvarchar(128)**|Somente para uso interno.|  
|subscriber_number|**Int**|Somente para uso interno.|  
|last_makegeneration_datetime|**datetime**|A última **datetime** que o processo de makegeneration executou para o publicador. Para obter mais informações, consulte o parâmetro - MakeGenerationInterval em [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md).|  
  
## <a name="see-also"></a>Consulte também  
 [Tabelas de replicação &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
