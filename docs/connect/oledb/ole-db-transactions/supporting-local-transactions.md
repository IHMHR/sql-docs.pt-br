---
title: Dando suporte a transações locais | Microsoft Docs
description: Transações locais no Driver do OLE DB para SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- OLE DB Driver for SQL Server, transactions
- local transactions [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: de00c4aac3125209bb56a1867f07b1f395804cc8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="supporting-local-transactions"></a>Dando suporte a transações locais
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Uma sessão delimita o escopo da transação para um Driver OLE DB para a transação local do SQL Server. Quando, na direção de um consumidor, o Driver OLE DB para SQL Server envia uma solicitação para uma instância conectada do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a solicitação constitui uma unidade de trabalho para o Driver OLE DB para SQL Server. Transações locais sempre quebram uma ou mais unidades de trabalho em um único OLE DB Driver para a sessão do SQL Server.  
  
 Uma única unidade de trabalho usando o Driver do OLE DB padrão para o modo de confirmação automática do SQL Server, será tratada como o escopo de uma transação local. Apenas uma unidade participa da transação local. Quando uma sessão é criada, o Driver OLE DB para SQL Server inicia uma transação para a sessão. Na conclusão bem-sucedida de uma unidade de trabalho, o trabalho é confirmado. Em caso de falha, qualquer trabalho começado é revertido e o erro é relatado ao consumidor. Em ambos os casos, o Driver OLE DB para SQL Server inicia uma nova transação local para a sessão para que todo o trabalho é realizado em uma transação.  
  
 O Driver OLE DB para o consumidor do SQL Server pode direcionar um controle mais preciso sobre o escopo de transação local usando o **ITransactionLocal** interface. Quando uma sessão do consumidor inicia uma transação, todas as unidades de trabalho de sessão entre a transação Iniciar ponto e as eventuais **confirmar** ou **anular** chamadas de método são tratadas como uma unidade atômica. O Driver OLE DB para SQL Server inicia uma transação quando instruído a fazer isso pelo consumidor implicitamente. Se o consumidor não solicitar retenção, a sessão reverterá para o comportamento pai em nível de transação, geralmente o modo de confirmação automática.  
  
 O Driver OLE DB para SQL Server dá suporte a **itransactionlocal:: Starttransaction** parâmetros da seguinte maneira.  
  
|Parâmetro|Description|  
|---------------|-----------------|  
|*isoLevel*[in]|O nível de isolamento a ser usado com esta transação. Em transações locais, o Driver OLE DB para SQL Server suporta o seguinte:<br /><br /> **ISOLATIONLEVEL_UNSPECIFIED**<br /><br /> **ISOLATIONLEVEL_CHAOS**<br /><br /> **ISOLATIONLEVEL_READUNCOMMITTED**<br /><br /> **ISOLATIONLEVEL_READCOMMITTED**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_CURSORSTABILITY**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_SERIALIZABLE**<br /><br /> **ISOLATIONLEVEL_ISOLATED**<br /><br /> **ISOLATIONLEVEL_SNAPSHOT**<br /><br /> <br /><br /> Observação: Começando com [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], ISOLATIONLEVEL_SNAPSHOT é válido para o *isoLevel* argumento ou não o controle de versão está habilitado para o banco de dados. Porém, ocorrerá um erro se o usuário tentar executar uma instrução e o controle de versão não estiver habilitado e/ou o banco de dados não for somente leitura. Além disso, o erro XACT_E_ISOLATIONLEVEL ocorrerá se ISOLATIONLEVEL_SNAPSHOT for especificado como o *isoLevel* quando conectado a uma versão do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] anteriores [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].|  
|*isoFlags*[in]|O Driver OLE DB para SQL Server retornará um erro de qualquer valor diferente de zero.|  
|*pOtherOptions*[in]|Se não for nulo, o Driver OLE DB para SQL Server solicita o objeto de opções da interface. O Driver OLE DB para SQL Server retornará XACT_E_NOTIMEOUT se o objeto de opções *ulTimeout* membro não é zero. O Driver OLE DB para SQL Server ignora o valor da *szDescription* membro.|  
|*pulTransactionLevel*[out]|Se não for NULL, o Driver OLE DB para SQL Server retornará o nível aninhado da transação.|  
  
 Para transações locais, o Driver OLE DB para SQL Server implementa **ITransaction:: Abort** parâmetros da seguinte maneira.  
  
|Parâmetro|Description|  
|---------------|-----------------|  
|*pboidReason*[in]|Ignorado se definido. Pode ser NULL com segurança.|  
|*fRetaining*[in]|Quando TRUE, uma nova transação é iniciada implicitamente para a sessão. A transação deve ser confirmada ou encerrada pelo consumidor. Quando for falso, o Driver OLE DB para SQL Server reverterá ao modo de confirmação automática para a sessão.|  
|*fAsync*[in]|Não há suporte para anulação assíncrona pelo Driver OLE DB para SQL Server. O Driver OLE DB para SQL Server retorna XACT_E_NOTSUPPORTED se o valor não é FALSE.|  
  
 Para transações locais, o Driver OLE DB para SQL Server implementa **ITransaction:: Commit** parâmetros da seguinte maneira.  
  
|Parâmetro|Description|  
|---------------|-----------------|  
|*fRetaining*[in]|Quando TRUE, uma nova transação é iniciada implicitamente para a sessão. A transação deve ser confirmada ou encerrada pelo consumidor. Quando for falso, o Driver OLE DB para SQL Server reverterá ao modo de confirmação automática para a sessão.|  
|*grfTC*[in]|Assíncrona e a fase um retorna não são suportados pelo Driver OLE DB para SQL Server. O Driver OLE DB para SQL Server retorna XACT_E_NOTSUPPORTED para qualquer valor diferente de XACTTC_SYNC.|  
|*grfRM*[in]|Deve ser 0.|  
  
 O Driver OLE DB para SQL Server conjuntos de linhas na sessão são preservados em um local de confirmação ou anulação da operação com base nos valores das propriedades do conjunto de linhas DBPROP_ABORTPRESERVE e DBPROP_COMMITPRESERVE. Por padrão, essas propriedades são VARIANT_FALSE e todos os OLE DB Driver para SQL Server conjuntos de linhas na sessão são perdidas após uma operação de anulação ou confirmar a operação.  
  
 O Driver OLE DB para SQL Server não implementa o **ITransactionObject** interface. Uma tentativa do consumidor de recuperar uma referência na interface retorna E_NOINTERFACE.  
  
 Este exemplo usa **ITransactionLocal**.  
  
```  
// Interfaces used in the example.  
IDBCreateSession*   pIDBCreateSession   = NULL;  
ITransaction*       pITransaction       = NULL;  
IDBCreateCommand*   pIDBCreateCommand   = NULL;  
IRowset*            pIRowset            = NULL;  
  
HRESULT             hr;  
  
// Get the command creation and local transaction interfaces for the  
// session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
if (FAILED(hr = pIDBCreateCommand->QueryInterface(IID_ITransactionLocal,  
    (void**) &pITransaction)))  
    {  
    // Process error. Release any references and return.  
    }  
  
// Start the local transaction.  
if (FAILED(hr = ((ITransactionLocal*) pITransaction)->StartTransaction(  
    ISOLATIONLEVEL_REPEATABLEREAD, 0, NULL, NULL)))  
    {  
    // Process error from StartTransaction. Release any references and  
    // return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then terminate.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, XACTTC_SYNC, 0)))  
        {  
        // Get error from failed commit.  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>Consulte também  
 [Transações](../../oledb/ole-db-transactions/transactions.md)   
 [Trabalhando com isolamento de instantâneo](../../oledb/features/working-with-snapshot-isolation.md)  
  
  
