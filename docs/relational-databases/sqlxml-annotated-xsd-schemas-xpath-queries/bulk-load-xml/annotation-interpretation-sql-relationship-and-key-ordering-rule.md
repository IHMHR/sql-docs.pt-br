---
title: "SQL: Relationship e a regra de ordenação de chaves (SQLXML 4.0) | Microsoft Docs"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- key ordering rules [SQLXML]
- relationship annotation
ms.assetid: 914cb152-09f5-4b08-b35d-71940e4e9986
caps.latest.revision: "23"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2d36ae25139287c52076310e91d0a8bdabcdaf03
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="annotation-interpretation---sqlrelationship-and-key-ordering-rule"></a>Interpretação de anotação - SQL: Relationship e a regra de ordenação de chave
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Como o XML Bulk Load gera registro à medida que seus nós entram no escopo e envia esses registros para a Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] conforme seus nós saem do escopo, os dados para o registro devem estar presentes no escopo do nó.  
  
 Considere o seguinte esquema XSD, no qual a relação um-para-muitos entre  **\<cliente >** e  **\<ordem >** elementos (um cliente pode fazer muitos pedidos) é especificado usando o  **\<SQL: Relationship >** elemento:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"<>   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustCustOrder"  
          parent="Cust"  
          parent-key="CustomerID"  
          child="CustOrder"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customers" sql:relation="Cust" >  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="CustomerID"  type="xsd:integer" />  
       <xsd:element name="CompanyName" type="xsd:string" />  
       <xsd:element name="City"        type="xsd:string" />  
       <xsd:element name="Order"   
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder" >  
         <xsd:complexType>  
          <xsd:attribute name="OrderID" type="xsd:integer" />  
         </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Como o  **\<cliente >** nó de elemento entra no escopo, o XML Bulk Load gera um registro de cliente. Este registro permanece até que o XML Bulk Load lê  **\</Customer >**. No processamento de  **\<ordem >** nó de elemento, o XML Bulk Load usa  **\<SQL: Relationship >** para obter o valor da coluna de chave estrangeira CustomerID da tabela CustOrder do  **\<cliente >** pai elemento, pois o  **\<ordem >** o elemento não especifica o **CustomerID** atributo. Isso significa que na definição de  **\<cliente >** elemento, você deve especificar o **CustomerID** atributo no esquema antes de especificar  **\<sql: relação >**. Caso contrário, quando um  **\<ordem >** elemento entra no escopo, o XML Bulk Load gera um registro para a tabela CustOrder e quando o XML em massa Load atingir o  **\</Order >** término de marca, ele envia o registro de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sem o valor da coluna de chave estrangeira CustomerID.  
  
 Salve o esquema fornecido neste exemplo como SampleSchema.xml.  
  
### <a name="to-test-a-working-sample"></a>Para testar um exemplo de funcionamento  
  
1.  Crie estas tabelas:  
  
    ```  
    CREATE TABLE Cust (  
                  CustomerID     int          PRIMARY KEY,  
               CompanyName    varchar(20)  NOT NULL,  
                  City           varchar(20)  DEFAULT 'Seattle')  
    GO  
    CREATE TABLE CustOrder (  
                  OrderID        varchar(10) PRIMARY KEY,  
               CustomerID     int         FOREIGN KEY REFERENCES                                          Cust(CustomerID))  
    GO  
    ```  
  
2.  Salve os dados de exemplo a seguir como SampleXMLData.xml:  
  
    ```  
    <ROOT>    
      <Customers>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City>NY</City>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
        <CustomerID>1111</CustomerID>  
      </Customers>  
      <Customers>  
        <CompanyName>Toms Spezialitten</CompanyName>  
         <City>LA</City>    
        <Order OrderID="3" />  
        <CustomerID>1112</CustomerID>  
      </Customers>  
      <Customers>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
        <CustomerID>1113</CustomerID>  
      </Customers>  
    </ROOT>  
    ```  
  
3.  Para executar o XML Bulk Load, salve e execute o seguinte exemplo do [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) como MySample.vbs:  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Transaction=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
     O resultado é que o XML Bulk Load insere um valor NULL na coluna de chave estrangeira CustomerID da tabela CustOrder. Se você revisar os dados de exemplo do XML para que o  **\<CustomerID >** elemento filho aparece antes do  **\<ordem >** elemento filho, você obterá o resultado esperado: o XML Bulk Load Insere o valor de chave estrangeira especificado na coluna.  
  
 Este é o esquema XDR equivalente:  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
   <ElementType name="CustomerID"  />  
   <ElementType name="CompanyName" />  
   <ElementType name="City"        />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust" >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
                 <sql:relationship  
                        key-relation    ="Cust"  
                        key             ="CustomerID"  
                        foreign-key     ="CustomerID"  
                        foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
</Schema>  
```  
  
  