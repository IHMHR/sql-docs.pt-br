---
title: Sessões | Microsoft Docs
description: Sessões no Driver do OLE DB para SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- OLE DB Driver for SQL Server, sessions
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: d5aed67da19db68097f57f689ad0a26692d75f63
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sessions"></a>Sessões
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Um Driver OLE DB para a sessão do SQL Server representa uma única conexão a uma instância de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 O Driver OLE DB para SQL Server requer que as sessões delimitem espaço de transação para uma fonte de dados. Todos os objetos de comando criados de um objeto de sessão específico participam da transação local ou distribuída do objeto de sessão.  
  
 O primeiro objeto de sessão criado na fonte de dados inicializada recebe a conexão do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] estabelecida na inicialização. Quando todas as referências nas interfaces do objeto de sessão são liberadas, a conexão com a instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] torna-se disponível a outro objeto de sessão criado na fonte de dados.  
  
 Um objeto de sessão adicional criado na fonte de dados estabelece sua própria conexão com a instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] conforme especificado pela fonte de dados. A conexão com a instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] é cancelada quando o aplicativo libera todas as referências aos objetos criados naquela sessão.  
  
 O exemplo a seguir demonstra como usar o Driver OLE DB para SQL Server para se conectar a um [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] banco de dados:  
  
```  
int main()  
{  
    // Interfaces used in the example.  
    IDBInitialize*      pIDBInitialize      = NULL;  
    IDBCreateSession*   pIDBCreateSession   = NULL;  
    IDBCreateCommand*   pICreateCmd1        = NULL;  
    IDBCreateCommand*   pICreateCmd2        = NULL;  
    IDBCreateCommand*   pICreateCmd3        = NULL;  
  
    // Initialize COM.  
    if (FAILED(CoInitialize(NULL)))  
    {  
        // Display error from CoInitialize.  
        return (-1);  
    }  
  
    // Get the memory allocator for this task.  
    if (FAILED(CoGetMalloc(MEMCTX_TASK, &g_pIMalloc)))  
    {  
        // Display error from CoGetMalloc.  
        goto EXIT;  
    }  
  
    // Create an instance of the data source object.  
    if (FAILED(CoCreateInstance(CLSID_MSOLEDBSQL, NULL,  
        CLSCTX_INPROC_SERVER, IID_IDBInitialize, (void**)  
        &pIDBInitialize)))  
    {  
        // Display error from CoCreateInstance.  
        goto EXIT;  
    }  
  
    // The InitFromPersistedDS function   
    // performs IDBInitialize->Initialize() establishing  
    // the first application connection to the instance of SQL Server.  
    if (FAILED(InitFromPersistedDS(pIDBInitialize, L"MyDataSource",  
        NULL, NULL)))  
    {  
        goto EXIT;  
    }  
  
    // The IDBCreateSession interface is implemented on the data source  
    // object. Maintaining the reference received maintains the   
    // connection of the data source to the instance of SQL Server.  
    if (FAILED(pIDBInitialize->QueryInterface(IID_IDBCreateSession,  
        (void**) &pIDBCreateSession)))  
    {  
        // Display error from pIDBInitialize.  
        goto EXIT;  
    }  
  
    // Releasing this has no effect on the SQL Server connection  
    // of the data source object because of the reference maintained by  
    // pIDBCreateSession.  
    pIDBInitialize->Release();  
    pIDBInitialize = NULL;  
  
    // The session created next receives the SQL Server connection of  
    // the data source object. No new connection is established.  
    if (FAILED(pIDBCreateSession->CreateSession(NULL,  
        IID_IDBCreateCommand, (IUnknown**) &pICreateCmd1)))  
    {  
        // Display error from pIDBCreateSession.  
        goto EXIT;  
    }  
  
    // A new connection to the instance of SQL Server is established to support the  
    // next session object created. On successful completion, the  
    // application has two active connections on the SQL Server.  
    if (FAILED(pIDBCreateSession->CreateSession(NULL,  
        IID_IDBCreateCommand, (IUnknown**) &pICreateCmd2)))  
    {  
        // Display error from pIDBCreateSession.  
        goto EXIT;  
    }  
  
    // pICreateCmd1 has the data source connection. Because the  
    // reference on the IDBCreateSession interface of the data source  
    // has not been released, releasing the reference on the session  
    // object does not terminate a connection to the instance of SQL Server.  
    // However, the connection of the data source object is now   
    // available to another session object. After a successful call to   
    // Release, the application still has two active connections to the   
    // instance of SQL Server.  
    pICreateCmd1->Release();  
    pICreateCmd1 = NULL;  
  
    // The next session created gets the SQL Server connection  
    // of the data source object. The application has two active  
    // connections to the instance of SQL Server.  
    if (FAILED(pIDBCreateSession->CreateSession(NULL,  
        IID_IDBCreateCommand, (IUnknown**) &pICreateCmd3)))  
    {  
        // Display error from pIDBCreateSession.  
        goto EXIT;  
    }  
  
EXIT:  
    // Even on error, this does not terminate a SQL Server connection   
    // because pICreateCmd1 has the connection of the data source   
    // object.  
    if (pICreateCmd1 != NULL)  
        pICreateCmd1->Release();  
  
    // Releasing the reference on pICreateCmd2 terminates the SQL  
    // Server connection supporting the session object. The application  
    // now has only a single active connection on the instance of SQL Server.  
    if (pICreateCmd2 != NULL)  
        pICreateCmd2->Release();  
  
    // Even on error, this does not terminate a SQL Server connection   
    // because pICreateCmd3 has the connection of the   
    // data source object.  
    if (pICreateCmd3 != NULL)  
        pICreateCmd3->Release();  
  
    // On release of the last reference on a data source interface, the  
    // connection of the data source object to the instance of SQL Server is broken.  
    // The example application now has no SQL Server connections active.  
    if (pIDBCreateSession != NULL)  
        pIDBCreateSession->Release();  
  
    // Called only if an error occurred while attempting to get a   
    // reference on the IDBCreateSession interface of the data source.  
    // If so, the call to IDBInitialize::Uninitialize terminates the   
    // connection of the data source object to the instance of SQL Server.  
    if (pIDBInitialize != NULL)  
    {  
        if (FAILED(pIDBInitialize->Uninitialize()))  
        {  
            // Uninitialize is not required, but it fails if an  
            // interface has not been released. Use it for  
            // debugging.  
        }  
        pIDBInitialize->Release();  
    }  
  
    if (g_pIMalloc != NULL)  
        g_pIMalloc->Release();  
  
    CoUninitialize();  
  
    return (0);  
}  
```  
  
 Conectar-se o Driver do OLE DB para objetos de sessão do SQL Server para uma instância de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pode gerar uma sobrecarga significativa para aplicativos que criam e liberam objetos de sessão. A sobrecarga pode ser minimizada ao gerenciar Driver OLE DB para objetos de sessão do SQL Server com eficiência. OLE DB Driver para aplicativos do SQL Server pode manter o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] conexão de um objeto de sessão ativo, mantendo uma referência pelo menos uma interface do objeto.  
  
 Por exemplo, manter um pool de referências a objeto de criação de comando mantém ativas as conexões a esses objetos de sessão no pool. Como objetos de sessão são necessários, o código de manutenção do pool transmite um válido **IDBCreateCommand** ponteiro de interface para o método de aplicativo que solicita a sessão. Quando o método do aplicativo não necessita mais da sessão, o método retorna o ponteiro de interface para o código de manutenção do pool em vez de liberar a referência do aplicativo ao objeto de criação de comando.  
  
> [!NOTE]  
>  No exemplo anterior, o **IDBCreateCommand** interface é usada como o **ICommand** interface implementa o **GetDBSession** método, o único método no escopo de conjunto de linhas ou de comando que permite que um objeto determinar a sessão na qual ele foi criado. Portanto, um objeto de comando, e somente um objeto de comando, permite que um aplicativo recupere um ponteiro de objeto de fonte de dados a partir do qual outras sessões são criadas.  
  
## <a name="see-also"></a>Consulte também  
 [Objetos de fonte de dados & #40; OLE DB & #41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
