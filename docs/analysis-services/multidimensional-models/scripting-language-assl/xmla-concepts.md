---
title: Conceitos de XMLA | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a347b48dd0b725f5b7279250ff6b666318a82d39
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="xmla-concepts"></a>Conceitos de XMLA
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  O padrão XMLA (XML for Analysis) oferece suporte a acesso a dados para fontes de dados que residem na World Wide Web. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] implementa XMLA por especificação XMLA 1.1.  
  
 O XMLA (XML for Analysis) é um protocolo XML baseado em SOAP, criado especificamente para acesso a dados universal para qualquer fonte de dados multidimensional padrão residente na Web. XMLA também elimina a necessidade de implantar um componente de cliente que expõe um modelo de objeto de componente (COM) ou [!INCLUDE[msCoName](../../../includes/msconame-md.md)] interfaces do .NET Framework. O XMLA é otimizado para a Internet, quando viagens de ida e volta ao servidor são onerosas em termos de tempo e de recursos e quando conexões com estado para uma fonte de dados podem limitar conexões do usuário no servidor.  
  
 O XMLA é o protocolo nativo para [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], usado para todas as interações entre um aplicativo cliente e uma instância de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. O [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] oferece suporte completo ao XML for Analysis 1.1 e também oferece extensões para oferecer suporte ao gerenciamento de metadados, gerenciamento de sessão e a recursos de bloqueio. O AMO (Objetos de Gerenciamento de Análise) e o ADOMD.NET usam o protocolo XMLA ao se comunicarem com uma instância do [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="handling-xmla-communications"></a>Manipulando comunicações do XMLA  
 O padrão aberto XMLA descreve dois métodos geralmente acessíveis: **Discover** e **Execute**. Esses métodos usam a arquitetura de cliente e de servidor acoplada de forma flexível suportada pelo XML para manipular informações de entrada e de saída sobre uma instância do [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 O **Discover** método obtém informações e metadados de um serviço Web. Essas informações podem incluir uma lista de fontes de dados disponíveis, como também informações sobre qualquer um dos provedores de fontes de dados. As propriedades definem dados obtidos de uma fonte de dados e dão forma a eles. O **Discover** é um método comum para definir os vários tipos de informações de um aplicativo cliente pode exigir de fontes de dados em [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instâncias. As propriedades e a interface genérica oferecem extensibilidade sem exigir que você reescreva funções existentes em um aplicativo cliente.  
  
 O **Execute** método permite que os aplicativos sejam executados comandos específicos do provedor em fontes de dados XMLA.  
  
 Embora o protocolo XMLA seja otimizado para aplicativos Web, também poderá ser usado para aplicativos orientados à LAN. Os aplicativos a seguir podem aproveitar os benefícios desta API baseada em XML:  
  
-   Aplicativos cliente/servidor que exigem tecnologia flexível entre os clientes e o servidor  
  
-   Aplicativos cliente/servidor que tenham como destino vários sistemas operacionais  
  
-   Clientes que não exigem estado significante para aumentar a capacidade do servidor  
  
## <a name="xmla-and-the-unified-dimensional-model"></a>XMLA e o modelo dimensional unificado  
 O XMLA é o protocolo usado por aplicativos de business intelligence que empregam a metodologia UDM (modelo dimensional unificado)  
  
  
