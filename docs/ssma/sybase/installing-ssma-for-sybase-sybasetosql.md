---
title: Instalando o SSMA para SAP ASE (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/29/2017
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
ms.assetid: 8d5a4ce6-b747-46e3-9184-645d56e8b35c
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 336012819c23b02ac0527a70da930c5b74686e7a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="installing-ssma-for-sap-ase-sybasetosql"></a>Instalando o SSMA para SAP ASE (SybaseToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSMA (Migration Assistant) para o SAP Adaptive Server Enterprise (ASE) consiste em um aplicativo cliente que você usa para realizar uma migração do SAP ASE para [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou banco de dados do SQL Azure. Ele também contém um pacote de extensão que oferece suporte à migração de dados e o uso das funções do sistema ASE em seus bancos de dados migrados.  
  
Instale o aplicativo cliente no computador do qual você planeja executar as etapas de migração. Instalar os arquivos de pacote de extensão no computador que está executando [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] no qual os bancos de dados migrados devem ser hospedadas.  
  
## <a name="upgrading-ssma-for-sap-ase"></a>Atualizando o SSMA para SAP ASE  
Se você quiser atualizar para uma versão posterior do SSMA para SAP ASE, primeiro você deve desinstalar o cliente e o pacote de extensão do servidor. Em seguida, instale a versão mais recente.  
  
Se você abrir um projeto de uma versão anterior do SSMA para SAP ASE, SSMA perguntará se você deseja converter o projeto para a versão mais recente. Clique em **Sim** para trabalhar com o projeto na versão mais recente do SSMA.  
  
## <a name="contents"></a>Sumário  
  
|Artigo|Description|  
|---------|---------------|  
|[Instalando o SSMA para SAP ASE cliente &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)|Fornece informações sobre e instruções para instalar o SSMA para cliente SAP ASE.|  
|[Instalando componentes do SSMA no SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)|Fornece informações e instruções para instalar o pacote de extensão em instâncias do [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|[Removendo o SSMA para SAP ASE componentes &#40;SybaseToSQL&#41;](../../ssma/sybase/removing-ssma-for-sybase-components-sybasetosql.md)|Fornece instruções para desinstalar o cliente do pacote de programa e a extensão.|  
  
## <a name="see-also"></a>Consulte também  
[Migrando SAP ASE bancos de dados para o SQL Server - banco de dados do SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
