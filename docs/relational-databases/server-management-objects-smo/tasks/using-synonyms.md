---
title: "Usando sinônimos | Microsoft Docs"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: synonyms [SMO]
ms.assetid: db0a9022-9549-43e5-b6b3-deb236f05fb8
caps.latest.revision: "49"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fd77a87430f9b9405c9b6bc900f924cba66368ad
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="using-synonyms"></a>Usando sinônimos
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Um sinônimo é um nome alternativo para um objeto no escopo do esquema. No SMO, os sinônimos são representados pelo <xref:Microsoft.SqlServer.Management.Smo.Synonym> objeto. O objeto <xref:Microsoft.SqlServer.Management.Smo.Synonym> é um filho do objeto <xref:Microsoft.SqlServer.Management.Smo.Database>. Isso significa que sinônimos só são válidos dentro do escopo do banco de dados no qual eles são definidos. No entanto, o sinônimo pode se referir a objetos em outro banco de dados, ou em uma instância remota do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 O objeto que recebe um nome alternativo é conhecido como o objeto base. A propriedade do nome do objeto <xref:Microsoft.SqlServer.Management.Smo.Synonym> é o nome alternativo fornecido ao objeto base.  
  
## <a name="example"></a>Exemplo  
 Para os exemplos de código a seguir, selecione o ambiente de programação, o modelo de programação e a linguagem de programação para criar seu aplicativo. Para obter mais informações, consulte [criar um Visual C &#35; Projeto SMO no Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-synonym-in-visual-c"></a>Criando um sinônimo no Visual C#  
 O exemplo de código mostra como criar um sinônimo ou um nome alternativo para um objeto com escopo de esquema. Aplicativos cliente podem usar uma única referência para o objeto base através de um sinônimo, em vez de usar um nome com várias partes para fazer referência ao objeto base.  
  
```csharp  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Synonym object variable by supplying the   
            //parent database, name, and schema arguments in the constructor.   
            //The name is also a synonym of the name of the base object.   
            Synonym syn = new Synonym(db, "Shop", "Sales");  
  
            //Specify the base object, which is the object on which   
            //the synonym is based.   
            syn.BaseDatabase = "AdventureWorks2012";  
            syn.BaseSchema = "Sales";  
            syn.BaseObject = "Store";  
            syn.BaseServer = srv.Name;  
  
            //Create the synonym on the instance of SQL Server.   
            syn.Create();  
        }  
```  
  
## <a name="creating-a-synonym-in-powershell"></a>Criando um sinônimo no PowerShell  
 O exemplo de código mostra como criar um sinônimo ou um nome alternativo para um objeto com escopo de esquema. Aplicativos cliente podem usar uma única referência para o objeto base através de um sinônimo, em vez de usar um nome com várias partes para fazer referência ao objeto base.  
  
```powershell  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#And the database object corresponding to Adventureworks  
$db = $srv.Databases["AdventureWorks2012"]  
  
$syn = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Synonym `  
-argumentlist $db, "Shop", "Sales"  
  
#Specify the base object, which is the object on which the synonym is based.  
$syn.BaseDatabase = "AdventureWorks2012"  
$syn.BaseSchema = "Sales"  
$syn.BaseObject = "Store"  
$syn.BaseServer = $srv.Name  
  
#Create the synonym on the instance of SQL Server.  
$syn.Create()  
```  
  
## <a name="see-also"></a>Consulte também  
 [CREATE SYNONYM &#40;Transact-SQL&#41;](../../../t-sql/statements/create-synonym-transact-sql.md)  
  
  