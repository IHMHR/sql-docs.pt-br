---
title: Método getFunctionColumns (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e2b0e0f7-717c-48e6-bcd2-a325d938a833
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d0b3a45d117f665922b7078921aa9b8a2959717b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="getfunctioncolumns-method-sqlserverdatabasemetadata"></a>Método getFunctionColumns (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera uma descrição do sistema do catálogo especificado - ou parâmetros de função do usuário e tipo de retorno.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public ResultSet getFunctionColumns(java.lang.String catalog,  
                       java.lang.String schemaPattern,  
                       java.lang.String functionNamePattern  
                       java.lang.String columnNamePattern)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *catalog*  
  
 Um **cadeia de caracteres** que contém o nome do catálogo. Se for uma cadeia de caracteres vazia "", o resultado incluirá as funções sem um catálogo. Se for **nulo**, o nome do catálogo não é usado para pesquisa.  
  
 *schemaPattern*  
  
 Um **cadeia de caracteres** que contém o padrão de nome de esquema. Se for uma cadeia de caracteres vazia "", o resultado incluirá as funções sem um esquema. Se for **nulo**, o nome do esquema não é usado para pesquisa.  
  
 *functionNamePattern*  
  
 Um **cadeia de caracteres** que contém o nome de uma função.  
  
 *columnNamePattern*  
  
 Um **cadeia de caracteres** que contém o nome de um parâmetro.  
  
## <a name="return-value"></a>Valor de retorno  
 Um [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objeto.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Esse método getFunctionColumns é especificado pelo método getFunctionColumns na interface DatabaseMetadata.  
  
 Esse método retorna apenas as funções e os parâmetros correspondentes ao nome do esquema e da função especificados, além do nome do parâmetro dentro do catálogo especificado.  
  
 Todas as linhas do conjunto de resultados incluem as seguintes colunas para uma descrição de parâmetro, uma descrição de coluna ou um tipo de retorno:  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|FUNCTION_CAT|**String**|O nome do banco de dados no qual a função reside.|  
|FUNCTION_SCHEM|**String**|O esquema da função.|  
|FUNCTION_NAME|**String**|O nome da função.|  
|COLUMN_NAME|**String**|O nome de um parâmetro ou coluna.|  
|COLUMN_TYPE|**short**|**O tipo da coluna. Pode ser um dos seguintes valores:**<br /><br /> functionColumnUnknown (0): Tipo desconhecido.<br /><br /> functionColumnIn (1): Parâmetro de entrada.<br /><br /> functionColumnInOut (2): Parâmetro de entrada/saída.<br /><br /> functionColumnOut (3): Parâmetro de saída.<br /><br /> functionReturn (4): Valor de retorno da função.<br /><br /> functionColumnResult (5): Um parâmetro ou uma coluna é uma coluna no conjunto de resultados.|  
|DATA_TYPE|**smallint**|Os dados do SQL digite o valor de Types.|  
|TYPE_NAME|**String**|O nome do tipo de dados.|  
|PRECISION|**Int**|O número total de dígitos significativos.|  
|LENGTH|**Int**|O comprimento dos dados em bytes.|  
|SCALE|**short**|O número de dígitos à direita da vírgula decimal.|  
|RADIX|**short**|A base para tipos numéricos.|  
|NULLABLE|**short**|Indica se o valor de parâmetro ou retornado pode conter um **nulo** valor.<br /><br /> **Pode ser um dos seguintes valores:**<br /><br /> functionNoNulls (0): O valor NULL não é permitido.<br /><br /> functionNullable (1): O valor NULL é permitido.<br /><br /> functionNullableUnknown (2): Desconhecido.|  
|REMARKS|**String**|Os comentários sobre uma coluna ou um parâmetro.|  
|COLUMN_DEF|**String**|O valor padrão da coluna.<br /><br /> **Observação:** essas informações estão disponíveis com [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] e é específico do driver JDBC.|  
|SQL_DATA_TYPE|**smallint**|Essa coluna é o mesmo que o **DATA_TYPE** coluna, exceto para o **datetime** e ISO **intervalo** tipos de dados.<br /><br /> **Observação:** essas informações estão disponíveis com [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] e é específico do driver JDBC.|  
|SQL_DATETIME_SUB|**smallint**|O **datetime** ISO **intervalo** subcódigo se o valor de **SQL_DATA_TYPE** é **SQL_DATETIME** ou **SQL_INTERVAL**. Para tipos de dados diferente de **datetime** e ISO **intervalo**, essa coluna será NULL.<br /><br /> **Observação:** essas informações estão disponíveis com [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] e é específico do driver JDBC.|  
|CHAR_OCTET_LENGTH|**Int**|O tamanho máximo dos parâmetros ou colunas binários ou baseados em caractere. Para outros tipos de dados, ele é NULL.|  
|ORDINAL_POSITION|**Int**|Para parâmetros de entrada e saída, ele representa a posição começando em 1.<br /><br /> Para colunas do conjunto de resultados, é a posição da coluna no conjunto de resultados começando em 1.<br /><br /> Para o valor de retorno, é 0.|  
|IS_NULLABLE|**String**|Determina a nulidade de um parâmetro ou de uma coluna.<br /><br /> Pode ser um dos seguintes valores:<br /><br /> **Sim**: O parâmetro ou coluna pode incluir valores NULL.<br /><br /> **NÃO**: O parâmetro ou coluna não pode incluir valores NULL.<br /><br /> Cadeia de caracteres vazia (""): Desconhecida.|  
|SS_TYPE_CATALOG_NAME|**String**|O nome do catálogo que contém o tipo definido pelo usuário (UDT).|  
|SS_TYPE_SCHEMA_NAME|**String**|O nome do esquema que contém o UDT (tipo definido pelo usuário).|  
|SS_UDT_CATALOG_NAME|**String**|O UDT (tipo definido pelo usuário) do nome totalmente qualificado.|  
|SS_UDT_SCHEMA_NAME|**String**|O nome do catálogo em que é definido um nome da coleção de esquemas XML. Se o nome do catálogo não pode ser encontrado, essa variável conterá uma cadeia de caracteres vazia.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|**String**|O nome do esquema no qual é definido um nome da coleção de esquemas XML. Se não for possível localizar o nome do esquema, essa cadeia de caracteres estará vazia.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|**String**|O nome de uma coleção de esquemas XML. Se não for possível localizar o nome, essa cadeia de caracteres estará vazia.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|**String**|O nome do catálogo que contém o tipo definido pelo usuário (UDT).|  
|SS_XML_SCHEMACOLLECTION_NAME|**String**|O nome do esquema que contém o UDT (tipo definido pelo usuário).|  
|SS_DATA_TYPE|**tinyint**|O [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipo de dados que é usado pelos procedimentos armazenados estendidos.<br /><br /> **Observação** para obter mais informações sobre os tipos de dados retornado por [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], consulte "Tipos de dados (Transact-SQL)" em [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Manuais Online.|  
  
## <a name="see-also"></a>Consulte também  
 [Membros SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
