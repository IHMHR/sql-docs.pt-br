---
title: dm_os_cluster_properties (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_cluster_properties_TSQL
- sys.dm_os_cluster_properties
- dm_os_cluster_properties_TSQL
- dm_os_cluster_properties
dev_langs:
- TSQL
helpviewer_keywords:
- dm_os_cluster_properties
- sys.dm_os_cluster_properties
ms.assetid: 6d82e770-fba7-49e0-9a0c-3b34b393e4a7
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0547df42a00699539bde5a8fe918d97b61f63371
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmosclusterproperties-transact-sql"></a>sys.dm_os_cluster_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retorna uma linha com as configurações atuais para as propriedades de recurso de cluster do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identificadas neste tópico. Nenhum dado será retornado se essa exibição for executada em uma instância autônoma do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Essas propriedades são usadas para definir os valores que afetam a detecção de falha, o tempo de resposta da falha e o log de monitoração o status de integridade da instância do cluster de failover do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  

|Nome da coluna|Propriedade|Description|  
|-----------------|--------------|-----------------|  
|VerboseLogging|bigint|O nível de log para o cluster de failover do SQL Server. O log detalhado pode ser ativado para fornecer detalhes adicionais nos logs de erros para solução de problemas. Um dos valores seguintes:<br /><br /> 0 – O log está desativado (padrão)<br /><br /> 1 – Apenas erros<br /><br /> 2 – Erros e avisos<br /><br /> Para obter mais informações, consulte [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md).|  
|SqlDumperDumpFlags|bigint|Sinalizadores de despejo do SQLDumper determinam o tipo de arquivos de despejo gerados pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. A configuração padrão é 0.|  
|SqlDumperDumpPath|nvarchar(260)|O local onde o utilitário SQLDumper gera os arquivos de despejo.|  
|SqlDumperDumpTimeOut|bigint|O valor de tempo limite em milissegundos para o utilitário SQLDumper gerar um despejo no caso de uma falha do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. O valor padrão é 0.|  
|FailureConditionLevel|bigint|Define as condições sob as quais o cluster de failover do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve apresentar uma falha ou reiniciar. O valor padrão é 3. Para obter uma explicação detalhada ou para alterar as configurações de propriedade, consulte [Configure FailureConditionLevel Property Settings](../../sql-server/failover-clusters/windows/configure-failureconditionlevel-property-settings.md).|  
|HealthCheckTimeout|bigint|O valor do tempo limite de quanto tempo a DLL de recursos do Mecanismo de Banco de Dados do SQL Server deve aguardar por informações de integridade do servidor antes de considerar a instância do SQL Server como sem resposta. O valor de tempo limite é expresso em milissegundos. O padrão é 60000. Para obter mais informações ou para alterar essa configuração de propriedade, consulte [Configure HealthCheckTimeout Property Settings](../../sql-server/failover-clusters/windows/configure-healthchecktimeout-property-settings.md).|  
  
## <a name="permissions"></a>Permissões  
 Exige permissões de VIEW SERVER STATE na instância do cluster de failover do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir usa sys. dm_os_cluster_properties para retornar as configurações de propriedades do recurso de cluster de failover do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
```  
SELECT VerboseLogging, SqlDumperDumpFlags, SqlDumperDumpPath, SqlDumperDumpTimeOut, FailureConditionLevel, HealthCheckTimeout  
FROM sys.dm_os_cluster_properties;  
```  
  
 Este é um exemplo de conjunto de resultados.  
  
|VerboseLogging|SqlDumperDumpFlags|SqlDumperDumpPath|SqlDumperDumpTimeOut|FailureConditionLevel|HealthCheckTimeout|  
|--------------------|------------------------|-----------------------|--------------------------|---------------------------|------------------------|  
|0|0|NULL|0|3|60000|  
  
  
