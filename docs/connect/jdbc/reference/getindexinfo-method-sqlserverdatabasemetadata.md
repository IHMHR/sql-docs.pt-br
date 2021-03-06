---
title: Método getIndexInfo (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getIndexInfo
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8a677cc6-8e33-4e57-8678-0849345aa8d0
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cef7b37818e5bc7bf46c7181a3816edd5bbad860
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="getindexinfo-method-sqlserverdatabasemetadata"></a>Método getIndexInfo (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera uma descrição dos índices e estatísticas para a tabela especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public java.sql.ResultSet getIndexInfo(java.lang.String cat,  
                                       java.lang.String schema,  
                                       java.lang.String table,  
                                       boolean unique,  
                                       boolean approximate)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *CAT*  
  
 Um **cadeia de caracteres** que contém o nome do catálogo.  
  
 *schema*  
  
 Um **cadeia de caracteres** que contém o nome do esquema.  
  
 *table*  
  
 Um **cadeia de caracteres** que contém o nome da tabela.  
  
 *Exclusivo*  
  
 **True** se apenas índices de valores exclusivos forem retornados. **False** se todos os índices são retornados.  
  
 *aproximado*  
  
 **True** se os resultados refletirem valores aproximados ou desatualizados. **False** se os resultados forem precisos.  
  
## <a name="return-value"></a>Valor de retorno  
 Um [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objeto.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Esse método getIndexInfo é especificado pelo método getIndexInfo na interface DatabaseMetadata.  
  
 O conjunto de resultados retornado pelo método getIndexInfo conterá as seguintes informações:  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|O nome do banco de dados no qual a tabela especificada reside.|  
|TABLE_SCHEM|**String**|O esquema da tabela.|  
|TABLE_NAME|**String**|O nome da tabela.|  
|NON_UNIQUE|**booleano**|Indica se os valores de índice podem ser não exclusivos.|  
|INDEX_QUALIFIER|**String**|O nome do proprietário do índice. Ele será nulo quando TYPE for tableIndexStatistic.|  
|INDEX_NAME|**String**|O nome do índice.|  
|TYPE|**short**|O tipo do índice. Pode ser um dos seguintes valores:<br /><br /> tableIndexStatistic (0)<br /><br /> tableIndexClustered (1)<br /><br /> tableIndexHashed (2)<br /><br /> tableIndexOther (3)|  
|ORDINAL_POSITION|**short**|A posição ordinal da coluna no índice. A primeira coluna no índice é 1.|  
|COLUMN_NAME|**String**|O nome da coluna.|  
|ASC_OR_DESC|**String**|A ordem usada no agrupamento do índice. Pode ser um dos seguintes valores:<br /><br /> A (crescente)<br /><br /> D (decrescente)<br /><br /> NULL (não aplicável)<br /><br /> **Observação:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] sempre retorna "A".  |  
|CARDINALITY|**Int**|O número de linhas na tabela ou os valores exclusivos no índice.|  
|PAGES|**Int**|O número de páginas usadas para armazenar o índice ou a tabela.|  
|FILTER_CONDITION|**String**|A condição do filtro.<br /><br /> **Observação:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] sempre retorna null.  |  
  
> [!NOTE]  
>  Para obter mais informações sobre os dados retornados pelo método getIndexInfo, consulte "sp_indexes (Transact-SQL)" em [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Manuais Online.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como usar o método getIndexInfo para retornar informações sobre os índices e estatísticas da tabela Person. Contact no [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] banco de dados de exemplo.  
  
```  
public static void executeGetIndexInfo(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getIndexInfo("AdventureWorks", "Person", "Contact", false, true);  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Métodos SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membros SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
