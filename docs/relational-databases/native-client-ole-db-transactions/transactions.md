---
title: Transações | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: 3b41e33a-c1ca-4b2a-9464-312b0ed3ca89
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d17bc8a8460f8d83cd495943a9c7a0ceefd0f54a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="transactions"></a>Transactions
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor do OLE DB Native Client implementa o suporte de transação local. O consumidor pode usar transações distribuídas ou coordenadas pelo Coordenador de Transações Distribuídas da Microsoft (MS DTC). Para os consumidores que necessitam de controle de transação que abrange várias sessões, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor do OLE DB Native Client pode unir transações iniciadas e mantidas pelo MS DTC.  
  
 Por padrão, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor do OLE DB Native Client usa um modo de transação de confirmação automática, onde cada ação discreta na sessão de um consumidor compreende uma transação completa em uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] modo de confirmação automática do provedor OLE DB Native Client é local e transações de confirmação automática nunca englobam mais que uma única sessão.  
  
 O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor do OLE DB Native Client expõe a **ITransactionLocal** interface, permitindo que o consumidor usar explicitamente e implicitamente iniciar transações em uma única conexão a uma instância de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor do OLE DB Native Client não dá suporte a transações locais aninhadas.  
  
## <a name="in-this-section"></a>Nesta seção  
  
-   [Dando suporte a transações locais](../../relational-databases/native-client-ole-db-transactions/supporting-local-transactions.md)  
  
-   [Dando suporte a transações distribuídas](../../relational-databases/native-client-ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [Níveis de isolamento &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>Consulte também  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
