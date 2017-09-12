---
title: Inserir (XML DML) | Microsoft Docs
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- XML DML [SQL Server]
- inserting nodes
- insert keyword [XML DML]
- insert XML DML statement
ms.assetid: 0c95c2b3-5cc2-4c38-9e25-86493096c442
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f995a0dcd0b91c0835c4121a7a2072c2a586f35
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="insert-xml-dml"></a>inserir (XML DML)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Insere um ou mais nós identificados por *Expression1* como nós filhos ou irmãos do nó identificado por *Expression2*.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
insert   
      Expression1 (  
                 {as first | as last} into | after | before  
                                    Expression2  
                )  
```  
  
## <a name="arguments"></a>Argumentos  
 *Expression1*  
 Identifica um ou mais nós para inserir. Isso pode ser uma instância XML constante; uma referência a uma instância de tipo de dados XML digitada da mesma coleção de esquema XML no qual o método modificado está sendo aplicado; uma instância de tipo de dados XML não digitada usando autônomo **SQL: Column**/**SQL: Variable** função; ou uma expressão XQuery. A expressão pode resultar em um nó, e também um nó de texto, ou em uma sequência ordenada de nós. Não pode ser resolvida no nó de raiz (/). Se a expressão resultar em um valor ou sequência de valores, os valores serão inseridos como um único nó de texto com um espaço separando cada valor na sequência. Se você especificar vários nós como constantes, os nós serão incluídos em parênteses e separados por vírgulas. Não é possível inserir sequências heterogêneas como uma sequência de elementos, atributos ou valores. Se *Expression1* resolve para uma sequência vazia, nenhuma inserção ocorrerá e nenhum erro será retornado.  
  
 into  
 Nós identificados por *Expression1* são inseridos como descendentes diretos (nós filhos) do nó identificado por *Expression2*. Se o nó no *Expression2* já tem um ou mais nós filho, você deve usar o **como primeiro** ou **último** para especificar onde você deseja que o novo nó adicionado. Por exemplo, no início ou no fim da lista de filhos, respectivamente. O **como primeiro** e **último** palavras-chave são ignoradas quando forem inseridos atributos.  
  
 after  
 Nós identificados por *Expression1* são inseridos diretamente como irmãos após o nó identificado por *Expression2*. O **depois** palavra-chave não pode ser usado para inserir atributos. Por exemplo, não pode ser usada para inserir um construtor de atributo ou para retornar um atributo de um XQuery.  
  
 before  
 Nós identificados por *Expression1* são inseridos diretamente como irmãos antes do nó identificado por *Expression2*. O **antes de** palavra-chave não pode ser usada quando estão sendo inseridos atributos. Por exemplo, não pode ser usada para inserir um construtor de atributo ou para retornar um atributo de um XQuery.  
  
 *Expression2*  
 Identifica um nó. Nós identificados em *Expression1* são inseridos em relação ao nó identificado por *Expression2*. Isso pode ser uma expressão XQuery que retorna uma referência a um nó que existe no documente atualmente referenciado. Se mais de um nó for retornado, a inserção falhará. Se *Expression2* retorna uma sequência vazia, nenhuma inserção ocorrerá e nenhum erro será retornado. Se *Expression2* não for estatisticamente um singleton, será retornado um erro estático. *Expression2* não pode ser uma instrução de processamento, comentário ou atributo. Observe que *Expression2* deve ser uma referência a um nó existente no documento e não um nó construído.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-inserting-element-nodes-into-the-document"></a>A. Inserção de nós de elemento no documento  
 O exemplo a seguir ilustra como inserir elementos em um documento. Primeiro, um documento XML é atribuído a uma variável do **xml** tipo. Em seguida, por meio de várias **inserir** instruções XML DML, o exemplo ilustra como nós de elemento são inseridos no documento. Depois de cada inserção, a instrução SELECT exibe o resultado.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;         
SET @myDoc = '<Root>         
    <ProductDescription ProductID="1" ProductName="Road Bike">         
        <Features>         
        </Features>         
    </ProductDescription>         
</Root>'  ;       
SELECT @myDoc;     
-- insert first feature child (no need to specify as first or as last)         
SET @myDoc.modify('         
insert <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>   
into (/Root/ProductDescription/Features)[1]') ;  
SELECT @myDoc ;        
-- insert second feature. We want this to be the first in sequence so use 'as first'         
set @myDoc.modify('         
insert <Warranty>1 year parts and labor</Warranty>          
as first         
into (/Root/ProductDescription/Features)[1]         
')  ;       
SELECT @myDoc  ;       
-- insert third feature child. This one is the last child of <Features> so use 'as last'         
SELECT @myDoc         
SET @myDoc.modify('         
insert <Material>Aluminium</Material>          
as last         
into (/Root/ProductDescription/Features)[1]         
')         
SELECT @myDoc ;        
-- Add fourth feature - this time as a sibling (and not a child)         
-- 'after' keyword is used (instead of as first or as last child)         
SELECT @myDoc  ;       
set @myDoc.modify('         
insert <BikeFrame>Strong long lasting</BikeFrame>   
after (/Root/ProductDescription/Features/Material)[1]         
')  ;       
SELECT @myDoc;  
GO  
```  
  
 Observe que várias expressões de caminho neste exemplo especificam" [1]" como um requisito de digitação estática. Isso assegura um único nó de destino.  
  
### <a name="b-inserting-multiple-elements-into-the-document"></a>B. Inserção de vários elementos no documento  
 No exemplo a seguir, um documento é atribuído primeiro a uma variável do **xml** tipo. Em seguida, uma sequência de dois elementos, que representa os recursos do produto, é atribuída a uma segunda variável do **xml** tipo. Essa sequência é inserida na primeira variável.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc = N'<Root>             
<ProductDescription ProductID="1" ProductName="Road Bike">             
    <Features> </Features>             
</ProductDescription>             
</Root>';  
DECLARE @newFeatures xml;  
SET @newFeatures = N'<Warranty>1 year parts and labor</Warranty>            
<Maintenance>3 year parts and labor extended maintenance is available</Maintenance>';           
-- insert new features from specified variable            
SET @myDoc.modify('             
insert sql:variable("@newFeatures")             
into (/Root/ProductDescription/Features)[1] ')             
SELECT @myDoc;  
GO  
```  
  
### <a name="c-inserting-attributes-into-a-document"></a>C. Inserção de atributos em um documento  
 O exemplo a seguir ilustra como os atributos são inseridos em um documento. Primeiro, um documento é atribuído a um **xml** variável de tipo. Em seguida, uma série de **inserir** instruções XML DML é usado para inserir atributos no documento. Depois de cada inserção de atributo, a instrução SELECT exibe o resultado.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml ;            
SET @myDoc =   
'<Root>             
    <Location LocationID="10" >             
        <step>Manufacturing step 1 at this work center</step>             
        <step>Manufacturing step 2 at this work center</step>             
    </Location>             
</Root>' ;  
SELECT @myDoc  ;          
-- insert LaborHours attribute             
SET @myDoc.modify('             
insert attribute LaborHours {".5" }             
into (/Root/Location[@LocationID=10])[1] ') ;           
SELECT @myDoc  ;          
-- insert MachineHours attribute but its value is retrived from a sql variable @Hrs             
DECLARE @Hrs float ;            
SET @Hrs =.2   ;          
SET @myDoc.modify('             
insert attribute MachineHours {sql:variable("@Hrs") }             
into   (/Root/Location[@LocationID=10])[1] ');            
SELECT @myDoc;             
-- insert sequence of attribute nodes (note the use of ',' and ()              
-- around the attributes.             
SET @myDoc.modify('             
insert (              
           attribute SetupHours {".5" },             
           attribute SomeOtherAtt {".2"}             
        )             
into (/Root/Location[@LocationID=10])[1] ');             
SELECT @myDoc;  
GO  
```  
  
### <a name="d-inserting-a-comment-node"></a>D. Inserção de um nó de comentário  
 Nesta consulta, um documento XML é atribuído primeiro a uma variável do **xml** tipo. Em seguida, XML DML é usado para inserir um nó de comentário depois do primeiro elemento <`step`>.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;             
SET @myDoc =   
'<Root>             
    <Location LocationID="10" >             
        <step>Manufacturing step 1 at this work center</step>             
        <step>Manufacturing step 2 at this work center</step>             
    </Location>             
</Root>' ;           
SELECT @myDoc;             
SET @myDoc.modify('             
insert <!-- some comment -->             
after (/Root/Location[@LocationID=10]/step[1])[1] ');            
SELECT @myDoc;  
GO  
```  
  
### <a name="e-inserting-a-processing-instruction"></a>E. Inserção de uma instrução de processamento  
 A consulta a seguir, um documento XML é atribuído primeiro a uma variável do **xml** tipo. Em seguida, a palavra-chave XML DML é usada para inserir uma instrução de processamento no início do documento.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc =   
'<Root>   
    <Location LocationID="10" >   
        <step>Manufacturing step 1 at this work center</step>   
        <step>Manufacturing step 2 at this work center</step>   
    </Location>   
</Root>' ;  
SELECT @myDoc ;  
SET @myDoc.modify('   
insert <?Program = "Instructions.exe" ?>   
before (/Root)[1] ') ;  
SELECT @myDoc ;  
GO  
```  
  
### <a name="f-inserting-data-using-a-cdata-section"></a>F. Inserção de dados que usam uma seção CDATA  
 Quando você insere texto que inclui caracteres inválidos no XML, como < ou >, você poderá usar seções CDATA para inserir os dados conforme mostrado na consulta a seguir. A consulta especifica uma seção CDATA, mas é adicionada como nó de texto com caracteres inválidos convertidos em entidades. Por exemplo, ' <' é salvo como &lt;.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;             
SET @myDoc =   
'<Root>             
    <ProductDescription ProductID="1" ProductName="Road Bike">             
        <Features> </Features>             
    </ProductDescription>             
</Root>' ;            
SELECT @myDoc ;            
SET @myDoc.modify('             
insert <![CDATA[ <notxml> as text </notxml> or cdata ]]>   
into  (/Root/ProductDescription/Features)[1] ') ;   
SELECT @myDoc ;  
GO  
```  
  
 A consulta insere um nó de texto no elemento <`Features`>:  
  
```  
<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features> <notxml> as text </notxml> or cdata </Features>  
</ProductDescription>  
</Root>       
```  
  
### <a name="g-inserting-text-node"></a>G. Inserção de nó de texto  
 Nesta consulta, um documento XML é atribuído primeiro a uma variável do **xml** tipo. Em seguida, XML DML é usado para inserir um nó de texto como o primeiro filho do elemento <`Root`>. O construtor de texto é usado para especificar o texto.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc = '<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  
</Features>  
</ProductDescription>  
</Root>'  
SELECT @myDoc;  
set @myDoc.modify('  
 insert text{"Product Catalog Description"}   
 as first into (/Root)[1]  
');  
SELECT @myDoc;  
```  
  
### <a name="h-inserting-a-new-element-into-an-untyped-xml-column"></a>H. Inserção de um novo elemento em uma coluna xml não digitada  
 O exemplo a seguir aplica XML DML para atualizar uma instância XML armazenada em um **xml** coluna de tipo:  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE T (i int, x xml);  
go  
INSERT INTO T VALUES(1,'<Root>  
    <ProductDescription ProductID="1" ProductName="Road Bike">  
        <Features>  
            <Warranty>1 year parts and labor</Warranty>  
            <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
        </Features>  
    </ProductDescription>  
</Root>');  
go  
-- insert a new element  
UPDATE T  
SET x.modify('insert <Material>Aluminium</Material> as first  
  into   (/Root/ProductDescription/Features)[1]  
');  
GO  
```  
  
 Novamente, quando o nó do elemento <`Material`> for inserido, a expressão de caminho deverá retornar um único destino. Isso é especificado explicitamente somando um [1] no final da expressão.  
  
```  
-- check the update  
SELECT x.query(' //ProductDescription/Features')  
FROM T;  
GO  
```  
  
### <a name="i-inserting-based-on-an-if-condition-statement"></a>I. Inserção baseada em uma instrução de condição se  
 No exemplo a seguir, uma condição IF é especificada como parte de Expression1 no **inserir** instrução XML DML. Se a condição for True (verdadeira), um atributo será adicionado ao elemento <`WorkCenter`>.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc =   
'<Root>  
    <Location LocationID="10" LaborHours="1.2" >  
        <step>Manufacturing step 1 at this work center</step>  
    <step>Manufacturing step 2 at this work center</step>  
    </Location>  
</Root>';  
SELECT @myDoc  
SET @myDoc.modify('  
insert  
if (/Root/Location[@LocationID=10])  
then attribute MachineHours {".5"}  
else ()  
    as first into   (/Root/Location[@LocationID=10])[1] ');  
SELECT @myDoc;  
GO  
```  
  
 O exemplo a seguir é semelhante, exceto pelo fato do **inserir** instrução XML DML insere um elemento no documento se a condição for True. Isto é, se o elemento <`WorkCenter`> tiver menos que ou for igual a dois elementos filhos <`step`>.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc =   
'<Root>  
    <Location LocationID="10" LaborHours="1.2" >  
        <step>Manufacturing step 1 at this work center</step>  
        <step>Manufacturing step 2 at this work center</step>  
    </Location>  
</Root>';  
SELECT @myDoc;  
SET @myDoc.modify('  
insert  
if (count(/Root/Location/step) <= 2)  
then element step { "This is a new step" }  
else ()  
    as last into   (/Root/Location[@LocationID=10])[1] ');  
SELECT @myDoc;  
GO  
```  
  
 Este é o resultado:  
  
```  
<Root>  
 <WorkCenter WorkCenterID="10" LaborHours="1.2">  
  <step>Manufacturing step 1 at this work center</step>  
  <step>Manufacturing step 2 at this work center</step>  
  <step>This is a new step</step>  
 </WorkCenter>  
```  
  
### <a name="j-inserting-nodes-in-a-typed-xml-column"></a>J. Inserção de nós em uma coluna xml digitada  
 Este exemplo insere um elemento e um atributo em um XML armazenado em um tipo de instruções de fabricação **xml** coluna.  
  
 No exemplo, você primeiro crie uma tabela (T) com um tipo **xml** coluna no banco de dados AdventureWorks. Depois, você copia a instância XML de instruções de fabricação da coluna Instructions na tabela ProductModel para a tabela T. Em seguida, as inserções são aplicadas ao XML na tabela T.  
  
```  
USE AdventureWorks;  
GO            
DROP TABLE T;  
GO             
CREATE TABLE T(ProductModelID int primary key,    
Instructions xml (Production.ManuInstructionsSchemaCollection));  
GO  
INSERT T              
    SELECT ProductModelID, Instructions             
    FROM Production.ProductModel             
    WHERE ProductModelID=7;  
GO             
SELECT Instructions             
FROM T;  
-- now insertion begins             
--1) insert a new manu. Location. The <Root> specified as              
-- expression 2 in the insert() must be singleton.      
UPDATE T   
set Instructions.modify('   
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";   
insert <MI:Location LocationID="1000" >   
           <MI:step>New instructions go here</MI:step>   
         </MI:Location>   
as first   
into   (/MI:root)[1]   
') ;  
  
SELECT Instructions             
FROM T ;  
-- 2) insert attributes in the new <Location>             
UPDATE T             
SET Instructions.modify('             
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";             
insert attribute LaborHours { "1000" }             
into (/MI:root/MI:Location[@LocationID=1000])[1] ');   
GO             
SELECT Instructions             
FROM T ;  
GO             
--cleanup             
DROP TABLE T ;  
GO             
```  
  
## <a name="see-also"></a>Consulte também  
 [Comparar XML digitado com XML não digitado](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Criar instâncias de dados XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [Métodos de tipos de dados xml](../../t-sql/xml/xml-data-type-methods.md)   
 [Linguagem de modificação de dados XML &#40; XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
