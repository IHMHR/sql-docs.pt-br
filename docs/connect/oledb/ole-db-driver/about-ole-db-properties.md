---
title: Sobre propriedades OLE DB | Microsoft Docs
description: Sobre propriedades OLE DB
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, properties
- OLE DB Driver for SQL Server, properties
- properties [OLE DB]
- property values [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: baeb2e6e9bbc565b705d22110deae918c07b5dbf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="about-ole-db-properties"></a>Sobre propriedades OLE DB
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Os consumidores definem valores de propriedade para solicitar um comportamento de objeto específico. Por exemplo, os consumidores usam propriedades para especificar as interfaces a serem expostas por um conjunto de linhas. Eles obtêm os valores de propriedade para determinar os recursos de um objeto, como um conjunto de linhas, uma sessão ou um objeto de fonte de dados.  
  
 Cada propriedade tem um valor, um tipo, uma descrição e um atributo de leitura/gravação e, no caso de propriedades de conjunto de linhas, um indicador que determina se ela pode ser aplicada por coluna.  
  
 Uma propriedade é identificada por um GUID e um inteiro que representam a ID de propriedade. Um conjunto de propriedades é um conjunto de todas as propriedades que compartilham o mesmo GUID. Além dos conjuntos de propriedade predefinidos OLE DB, o Driver OLE DB para SQL Server implementa propriedades e conjuntos de propriedades específicas do provedor neles. Cada propriedade pertence a um ou mais grupos de propriedades. Um grupo de propriedades é o grupo de todas as propriedades que se aplicam a um objeto específico. Alguns grupos de propriedades incluem o grupo de propriedades de inicialização, o grupo de propriedades de fonte de dados, o grupo de propriedades de sessão, o grupo de propriedades de conjunto de linhas, o grupo de propriedades de tabela e o grupo de propriedades de coluna. Há propriedades em cada um desses grupos de propriedade.  
  
 A definição dos valores de propriedade envolve:  
  
1.  Determinar as propriedades para as quais definir valores.  
  
2.  Determinar os conjuntos de propriedades que contêm as propriedades identificadas.  
  
3.  Alocar uma matriz de estruturas DBPROPSET, uma para cada conjunto de propriedades identificadas.  
  
4.  Alocar uma matriz de estruturas DBPROP para cada conjunto de propriedades. O número de elementos em cada matriz é o número de propriedades (identificadas na Etapa 1) que pertencem ao conjunto de propriedades.  
  
5.  Preencher a estrutura DBPROP para cada propriedade.  
  
6.  Preencher as informações (GUID do conjunto de propriedades, contagem do número de elementos e um ponteiro para a matriz DBPROP correspondente) na estrutura DBPROPSET para cada conjunto de propriedades.  
  
7.  Chamar um método para definir propriedades e passar a contagem e a matriz de estruturas DBPROPSET.  
  
## <a name="see-also"></a>Consulte também  
 [Criando um Driver do OLE DB para o aplicativo do SQL Server](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)   
 [Propriedades (OLE DB)](http://go.microsoft.com/fwlink/?LinkId=112207)  
  
  
