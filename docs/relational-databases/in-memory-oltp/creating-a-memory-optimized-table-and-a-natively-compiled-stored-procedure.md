---
title: Criando uma tabela com otimização de memória e um procedimento armazenado compilado nativamente | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 48a9a0a3-930f-477b-bd0f-e82e77999ecc
caps.latest.revision: 35
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 70492396abb68aa48db0b807a6158d8b144442a2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure"></a>Criando uma tabela com otimização de memória e um procedimento armazenado compilado nativamente
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Este tópico contém um exemplo que apresenta a você a sintaxe do OLTP na memória.  
  
 Para permitir que um aplicativo use o OLTP na memória, você precisa concluir as seguintes tarefas:  
  
-   Criar um grupo de arquivos de dados com otimização de memória e adicionar um contêiner ao grupo de arquivos.  
  
-   Criar índices e tabelas com otimização de memória. Para obter mais informações, consulte [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).  
  
-   Carregar dados na tabela com otimização de memória e atualizar as estatísticas após carregar os dados e antes de criar os procedimentos armazenados compilados. Para obter mais informações, consulte [Estatísticas para tabelas com otimização de memória](../../relational-databases/in-memory-oltp/statistics-for-memory-optimized-tables.md).  
  
-   Criar procedimentos armazenados compilados nativamente para acessar dados em tabelas com otimização de memória. Para obter mais informações, consulte [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md). Você também pode usar um [!INCLUDE[tsql](../../includes/tsql-md.md)] tradicional e interpretado para acessar dados em tabelas com otimização de memória.  
  
-   Conforme a necessidade, migrar dados das tabelas existentes para tabelas com otimização de memória.  
  
 Para obter informações sobre como usar [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] para criar tabelas com otimização de memória, consulte [Suporte ao SQL Server Management Studio para OLTP in-memory](../../relational-databases/in-memory-oltp/sql-server-management-studio-support-for-in-memory-oltp.md).  
  
 O exemplo de código a seguir exige um diretório chamado c:\Data.  
  
```sql  
CREATE DATABASE imoltp   
GO  
  
--------------------------------------  
-- create database with a memory-optimized filegroup and a container.  
ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA   
ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod   
ALTER DATABASE imoltp SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT=ON  
GO  
  
USE imoltp  
GO  
  
-- create a durable (data will be persisted) memory-optimized table  
-- two of the columns are indexed  
  CREATE TABLE dbo.ShoppingCart (   
    ShoppingCartId INT IDENTITY(1,1) PRIMARY KEY NONCLUSTERED,  
    UserId INT NOT NULL INDEX ix_UserId NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000),   
    CreatedDate DATETIME2 NOT NULL,   
    TotalPrice MONEY  
    ) WITH (MEMORY_OPTIMIZED=ON)   
  GO  
  
 -- create a non-durable table. Data will not be persisted, data loss if the server turns off unexpectedly  
 CREATE TABLE dbo.UserSession (   
   SessionId INT IDENTITY(1,1) PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=400000),   
   UserId int NOT NULL,   
   CreatedDate DATETIME2 NOT NULL,  
   ShoppingCartId INT,  
   INDEX ix_UserId NONCLUSTERED HASH (UserId) WITH (BUCKET_COUNT=400000)   
 )   
 WITH (MEMORY_OPTIMIZED=ON, DURABILITY=SCHEMA_ONLY)   
 GO  
  
-- insert data into the tables  
INSERT dbo.UserSession VALUES (342, SYSDATETIME(), 4)   
INSERT dbo.UserSession VALUES (65, SYSDATETIME(), NULL)   
INSERT dbo.UserSession VALUES (8798, SYSDATETIME(), 1)   
INSERT dbo.UserSession VALUES (80, SYSDATETIME(), NULL)   
INSERT dbo.UserSession VALUES (4321, SYSDATETIME(), NULL)   
INSERT dbo.UserSession VALUES (8578, SYSDATETIME(), NULL)   
  
INSERT dbo.ShoppingCart VALUES (8798, SYSDATETIME(), NULL)   
INSERT dbo.ShoppingCart VALUES (23, SYSDATETIME(), 45.4)   
INSERT dbo.ShoppingCart VALUES (80, SYSDATETIME(), NULL)   
INSERT dbo.ShoppingCart VALUES (342, SYSDATETIME(), 65.4)   
GO  
  
-- verify table contents   
  SELECT * FROM dbo.UserSession   
  SELECT * FROM dbo.ShoppingCart   
  GO  
  
--  update statistics on memory-optimized tables   
  UPDATE STATISTICS dbo.UserSession WITH FULLSCAN, NORECOMPUTE   
  UPDATE STATISTICS dbo.ShoppingCart WITH FULLSCAN, NORECOMPUTE   
  GO  
  
-- in an explicit transaction, assign a cart to a session and update the total price.   
-- SELECT/UPDATE/DELETE statements in explicit transactions   
  BEGIN TRAN   
   UPDATE dbo.UserSession SET ShoppingCartId=3 WHERE SessionId=4   
   UPDATE dbo.ShoppingCart SET TotalPrice=65.84 WHERE ShoppingCartId=3   
 COMMIT   
 GO   
  
 -- verify table contents   
 SELECT *   
 FROM dbo.UserSession u JOIN dbo.ShoppingCart s on u.ShoppingCartId=s.ShoppingCartId   
 WHERE u.SessionId=4   
 GO  
  
-- natively compiled stored procedure for assigning a shopping cart to a session   
 CREATE PROCEDURE dbo.usp_AssignCart @SessionId int   
 WITH NATIVE_COMPILATION, SCHEMABINDING   
 AS   
 BEGIN ATOMIC   
 WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
  
  DECLARE @UserId INT,  
          @ShoppingCartId INT  
  
  SELECT @UserId=UserId, @ShoppingCartId=ShoppingCartId   
  FROM dbo.UserSession WHERE SessionId=@SessionId  
  
  IF @UserId IS NULL   
  THROW 51000, N'The session or shopping cart does not exist.', 1  
  
  UPDATE dbo.UserSession SET ShoppingCartId=@ShoppingCartId WHERE SessionId=@SessionId   
 END   
 GO  
  
 EXEC usp_AssignCart 1   
 GO  
  
-- natively compiled stored procedure for inserting a large number of rows   
-- this demonstrates the performance of native procs   
 CREATE PROCEDURE dbo.usp_InsertSampleCarts @InsertCount int   
 WITH NATIVE_COMPILATION, SCHEMABINDING   
 AS   
 BEGIN ATOMIC   
 WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
  
  DECLARE @i int = 0  
  
  WHILE @i < @InsertCount   
  BEGIN   
    INSERT INTO dbo.ShoppingCart VALUES (1, SYSDATETIME() , NULL)   
    SET @i += 1   
  END  
  
END   
GO  
  
-- insert 1,000,000 rows   
 EXEC usp_InsertSampleCarts 1000000   
 GO  
  
---- verify the rows have been inserted   
 SELECT COUNT(*) FROM dbo.ShoppingCart   
 GO  
  
-- sample memory-optimized tables for sales orders and sales order details  
CREATE TABLE dbo.SalesOrders   
(  
   so_id INT NOT NULL PRIMARY KEY NONCLUSTERED,  
   cust_id INT NOT NULL,  
   so_date DATE NOT NULL INDEX ix_date NONCLUSTERED,  
   so_total MONEY NOT NULL,  
   INDEX ix_date_total NONCLUSTERED (so_date DESC, so_total DESC)  
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
CREATE TABLE dbo.SalesOrderDetails  
(  
   so_id INT NOT NULL,  
   lineitem_id INT NOT NULL,  
   product_id INT NOT NULL,  
   unitprice MONEY NOT NULL,  
  
   CONSTRAINT PK_SOD PRIMARY KEY NONCLUSTERED (so_id,lineitem_id)  
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
-- memory-optimized table type for collecting sales order details  
CREATE TYPE dbo.SalesOrderDetailsType AS TABLE  
(  
   so_id INT NOT NULL,  
   lineitem_id INT NOT NULL,  
   product_id INT NOT NULL,  
   unitprice MONEY NOT NULL,  
  
   PRIMARY KEY NONCLUSTERED (so_id,lineitem_id)  
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
-- stored procedure that inserts a sales order, along with its details  
CREATE PROCEDURE dbo.InsertSalesOrder @so_id INT, @cust_id INT, @items dbo.SalesOrderDetailsType READONLY  
WITH NATIVE_COMPILATION, SCHEMABINDING  
AS BEGIN ATOMIC WITH   
(  
   TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
   LANGUAGE = N'us_english'  
)  
   DECLARE @total MONEY  
   SELECT @total = SUM(unitprice) FROM @items  
   INSERT dbo.SalesOrders VALUES (@so_id, @cust_id, getdate(), @total)  
   INSERT dbo.SalesOrderDetails SELECT so_id, lineitem_id, product_id, unitprice FROM @items  
END  
GO  
  
-- insert a sample sales order  
DECLARE @so_id INT = 18,  
       @cust_id INT = 8,  
       @items dbo.SalesOrderDetailsType  
INSERT @items  VALUES   
       (@so_id, 1, 4, 43),   
       (@so_id, 2, 3, 3),   
       (@so_id, 3, 8, 453),   
       (@so_id, 4, 5, 76),   
       (@so_id, 5, 4, 43)  
EXEC dbo.InsertSalesOrder @so_id, @cust_id, @items  
GO  
  
-- verify the content of the tables  
SELECT   
       so.so_id,  
       so.so_date,  
       sod.lineitem_id,  
       sod.product_id,  
       sod.unitprice  
FROM dbo.SalesOrders so JOIN dbo.SalesOrderDetails sod on so.so_id=sod.so_id  
ORDER BY so.so_id, sod.lineitem_id  
  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Exemplos de código de OLTP na memória](../../relational-databases/in-memory-oltp/in-memory-oltp-code-samples.md)  
  
  
