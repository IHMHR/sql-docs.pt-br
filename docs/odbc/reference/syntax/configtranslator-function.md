---
title: Função ConfigTranslator | Microsoft Docs
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
- ConfigTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigTranslator
helpviewer_keywords:
- ConfigTranslator [ODBC]
ms.assetid: 7c22f07e-36de-425b-aa67-e32a84afae92
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5b38bc6340ec456ce180eb2a9cc266d5b8a19305
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="configtranslator-function"></a>Função ConfigTranslator
**Conformidade**  
 Versão introduzidas: ODBC 2.0  
  
 **Resumo**  
 **ConfigTranslator** retorna uma opção de conversão padrão para um conversor. Pode ser o tradutor de DLL ou uma DLL de instalação separados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
BOOL ConfigTranslator(  
     HWND     hwndParent,  
     DWORD *  pvOption);  
```  
  
## <a name="arguments"></a>Argumentos  
 *hwndParent*  
 [Entrada] Identificador da janela pai. A função não exibirá caixas de diálogo se o identificador é nulo.  
  
 *pvOption*  
 [Saída] Uma opção de conversão de 32 bits.  
  
## <a name="returns"></a>Retorna  
 A função retorna TRUE se for bem-sucedida, FALSO se ele falhar.  
  
## <a name="diagnostics"></a>diagnóstico  
 Quando **ConfigTranslator** retorna FALSE, um tipo de  *\*pfErrorCode* valor é postado para o buffer de erro de instalador por uma chamada para **SQLPostInstallerError**e pode ser obtida chamando **SQLInstallerError**. A seguinte tabela lista o  *\*pfErrorCode* valores que podem ser retornados por **SQLInstallerError** e explica cada uma no contexto dessa função.  
  
|*\*pfErrorCode*|Erro|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Identificador de janela inválido|O *hwndParent* argumento era nulo ou inválido.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Erro específico do driver ou do conversor|Um erro específico do driver para o qual não há nenhum erro de instalador ODBC definido. O *SzError* argumento em uma chamada para o **SQLPostInstallerError** a função deve conter a mensagem de erro específica do driver.|  
|ODBC_ERROR_INVALID_OPTION|Opção de conversão inválido|O *pvOption* argumento continha um valor inválido.|  
  
## <a name="comments"></a>Comentários  
 Se o conversor oferece suporte a apenas uma opção de conversão única, **ConfigTranslator** retorna TRUE e define *pvOption* para a opção de 32 bits. Caso contrário, ele determina a opção de conversão padrão a ser usado. **ConfigTranslator** pode exibir uma caixa de diálogo com a qual um usuário seleciona uma opção de conversão padrão.  
  
## <a name="related-functions"></a>Funções relacionadas  
  
|Para obter informações sobre|Consulte|  
|---------------------------|---------|  
|Obtendo uma opção de conversão|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Selecionar um conversor|[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|Definir uma opção de conversão|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
