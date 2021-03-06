---
title: Executar arquivos de script Transact-SQL usando sqlcmd | Microsoft Docs
ms.custom: ''
ms.date: 07/15/2016
ms.prod: sql
ms.prod_service: sql-tools
ms.technology:
- database-engine
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- transact sql scripts
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 9c135c5826f72b31fe52186f99d121b69b0cbd20
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sqlcmd---run-transact-sql-script-files"></a>sqlcmd – Executar arquivos de script do Transact-SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
 Use **sqlcmd** para executar um arquivo de script do Transact-SQL. Um arquivo de script do Transact-SQL é um arquivo de texto que pode conter uma combinação de instruções Transact-SQL, comandos **sqlcmd** e variáveis de script.  

## <a name="create-a-script-file"></a>Criar um arquivo de script  
 Para criar um arquivo de script simples do Transact-SQL usando o Bloco de Notas, siga estas etapas:  
  
1.  Clique em **Iniciar**, selecione **Todos os Programas**, vá até **Acessórios**e, depois, clique em **Bloco de Notas**.  
  
2.  Copie e cole o seguinte código do Transact-SQL no Bloco de Notas:  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT p.FirstName + ' ' + p.LastName AS 'Employee Name',  
    a.AddressLine1, a.AddressLine2 , a.City, a.PostalCode   
    FROM Person.Person AS p   
       INNER JOIN HumanResources.Employee AS e   
            ON p.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.BusinessEntityAddress bea   
            ON bea.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.Address AS a   
            ON a.AddressID = bea.AddressID;  
    GO  
    ```  
  
3.  Salve o arquivo como **myScript.sql** na unidade C.  
  
## <a name="run-the-script-file"></a>Executar o arquivo de script  
  
1.  Abra uma janela do prompt de comando.  
  
2.  Na janela do Prompt de Comando, digite: **sqlcmd -S myServer\nomeInstância -i C:\myScript.sql**  
  
3.  Pressione ENTER.  
  
 Uma lista de nomes e endereços de funcionários do [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] é escrita na janela do prompt de comando.  

## <a name="save-the-output-to-a-text-file"></a>Salvar a saída em um arquivo de texto
  
1.  Abra uma janela do prompt de comando.  
  
2.  Na janela do Prompt de comando, digite: **sqlcmd -S myServer\nomeInstância -i C:\myScript.sql -o C:\EmpAdds.txt**  
  
3.  Pressione ENTER.  
  
 Nenhuma saída é retornada na janela de prompt de comando. Em vez disso, a saída é enviada ao arquivo EmpAdds.txt. Você pode verificar essa saída abrindo o arquivo EmpAdds.txt.  
  
## <a name="see-also"></a>Consulte Também  
 [Iniciar o utilitário sqlcmd](../../relational-databases/scripting/sqlcmd-start-the-utility.md)   
 [Utilitário sqlcmd](../../tools/sqlcmd-utility.md)  
  
  
