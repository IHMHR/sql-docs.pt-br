---
title: Conjunto de linhas DISCOVER_JOBS | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e9d0d836d8fe44041aa541d71d86be327647dab9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="discoverjobs-rowset"></a>Conjunto de linhas DISCOVER_JOBS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Oferece informações sobre os trabalhos ativos em execução no servidor. O trabalho é uma parte do comando que executa uma tarefa específica em nome desse comando.  
  
## <a name="rowset-columns"></a>Colunas do conjunto de linhas  
 O conjunto de linhas **DISCOVER_JOBS** contém as colunas a seguir.  
  
|Nome da coluna|Indicador de tipo|Comprimento|Description|  
|-----------------|--------------------|------------|-----------------|  
|**JOB_CREATION_TIME**|**DBTYPE_DBTIMESTAMP**||A data e a hora do servidor UTC em que o trabalho foi criado.|  
|**JOB_DESCRIPTION**|**DBTYPE_WSTR**||A descrição do trabalho atribuída pelo serviço do servidor.|  
|**JOB_EXECUTION_TIME_MS**|**DBTYPE_I8**||A hora, em milissegundos, em que o trabalho está ativo.|  
|**JOB_ID**|**DBTYPE_I4**||O identificador exclusivo do trabalho.|  
|**JOB_START_TIME**|**DBTYPE_DBTIMESTAMP**||A data e a hora do servidor UTC em que o trabalho foi iniciado.|  
|**JOB_THREADPOOL_ID**|**DBTYPE_I4**||O pool de threads do qual o trabalho atual foi iniciado.|  
|**JOB_TOTAL_TIME_MS**|**DBTYPE_I8**||A hora, em milissegundos, desde o início do trabalho.|  
|**SPID**|**DBTYPE_I4**||A ID da sessão.|  
  
 Este conjunto de linhas do esquema não é classificado.  
  
## <a name="restriction-columns"></a>Colunas de restrição  
 O conjunto de linhas **DISCOVER_JOBS** pode ser restringido nas colunas listadas na tabela a seguir.  
  
|Nome da coluna|Indicador de tipo|Estado de restrição|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|Opcional.|  
|JOB_ID|DBTYPE_I4|Opcional.|  
|JOB_DESCRIPTION|DBTYPE_WSTR|Opcional.|  
|JOB_THREADPOOL_ID|DBTYPE_I4|Opcional.|  
|JOB_MIN TOTAL_TIME_MS|DBTYPE_I8|Opcional.|  
  
## <a name="see-also"></a>Consulte também  
 [XML for Analysis conjuntos de linhas de esquema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
