---
title: Suporte para tipos de data e hora de sql_variant | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-date-time
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sql_variant data type
ms.assetid: 12ff1ea6-e2cc-40e6-910c-3126974a90b3
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 66727e962bc0887b78ea177c6faed05c5cc2a8c8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sqlvariant-support-for-date-and-time-types"></a>Suporte para tipos de data e hora de sql_variant
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Este tópico descreve como o **sql_variant** tipo de dados oferece suporte à funcionalidade aprimorada de data e hora.  
  
 O atributo de coluna SQL_CA_SS_VARIANT_TYPE é usado para retornar o tipo C de uma coluna de resultado variável. [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] apresenta um atributo adicional, SQL_CA_SS_VARIANT_SQL_TYPE, que define o tipo SQL de uma coluna de resultado variável no (IRD) do descritor de linha de implementação. SQL_CA_SS_VARIANT_SQL_TYPE também pode ser usado no descritor de parâmetro de implementação (IPD) para especificar o tipo SQL de um SQL_SS_TIME2 ou parâmetro SQL_SS_TIMESTAMPOFFSET que tem o tipo de SQL_C_BINARY C associado ao tipo SQL_SS_VARIANT.  
  
 Os novos tipos SQL_SS_TIME2 e SQL_SS_TIMESTAMPOFFSET podem ser definidos por SQLColAttribute. SQL_CA_SS_VARIANT_SQL_TYPE pode ser retornado por SQLGetDescField.  
  
 Em colunas de resultado, o driver será convertido da variante em tipos de data/hora. Para obter mais informações, consulte [conversões de SQL para C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md). Durante a associação a SQL_C_BINARY, o comprimento do buffer deve ser grande o suficiente para receber o struct correspondente ao tipo SQL.  
  
 Para os parâmetros SQL_SS_TIME2 e SQL_SS_TIMESTAMPOFFSET, o driver converterá valores de C para **sql_variant** valores, conforme descrito na tabela a seguir. Se um parâmetro for associado como SQL_C_BINARY e o tipo de servidor for SQL_SS_VARIANT, ele será tratado como um valor binário, a menos que o aplicativo tenha definido SQL_CA_SS_VARIANT_SQL_TYPE como outro tipo SQL. Nesse caso, SQL_CA_SS_VARIANT_SQL_TYPE tem precedência; ou seja, caso SQL_CA_SS_VARIANT_SQL_TYPE seja definido, ele substitui o comportamento padrão de dedução do tipo SQL variável do tipo C.  
  
|Tipo de C|Tipo de servidor|Comentários|  
|------------|-----------------|--------------|  
|SQL_C_CHAR|varchar|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado.|  
|SQL_C_WCHAR|nvarcar|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado.|  
|SQL_C_TINYINT|smallint|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado.|  
|SQL_C_STINYINT|smallint|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado.|  
|SQL_C_SHORT|smallint|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado.|  
|SQL_C_SSHORT|smallint|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado.|  
|SQL_C_USHORT|int|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado.|  
|SQL_C_LONG|int|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado.|  
|SQL_C_SLONG|int|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado.|  
|SQL_C_ULONG|bigint|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado.|  
|SQL_C_SBIGINT|bigint|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado.|  
|SQL_C_FLOAT|real|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado.|  
|SQL_C_DOUBLE|float|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado.|  
|SQL_C_BIT|bit|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado.|  
|SQL_C_UTINYINT|tinyint|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado.|  
|SQL_C_BINARY|varbinary|SQL_CA_SS_VARIANT_SQL_TYPE não é definido.|  
|SQL_C_BINARY|time|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIME2<br /><br /> Escala é definida como SQL_DESC_PRECISION (o *DecimalDigits* parâmetro **SQLBindParameter**).|  
|SQL_C_BINARY|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIMESTAMPOFFSET<br /><br /> Escala é definida como SQL_DESC_PRECISION (o *DecimalDigits* parâmetro **SQLBindParameter**).|  
|SQL_C_TYPE_DATE|date|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado.|  
|SQL_C_TYPE_TIME|time(0)|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado.|  
|SQL_C_TYPE_TIMESTAMP|datetime2|Escala é definida como SQL_DESC_PRECISION (o *DecimalDigits* parâmetro **SQLBindParameter**).|  
|SQL_C_NUMERIC|Decimal|Precisão é definida como SQL_DESC_PRECISION (o *ColumnSize* parâmetro **SQLBindParameter**).<br /><br /> Escala é definida como SQL_DESC_SCALE (o *DecimalDigits* parâmetro de SQLBindParameter).|  
|SQL_C_SS_TIME2|time|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado|  
|SQL_C_SS_TIMESTAMPOFFSET|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE é ignorado|  
  
## <a name="see-also"></a>Consulte também  
 [Data e hora melhorias & #40; ODBC & #41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
