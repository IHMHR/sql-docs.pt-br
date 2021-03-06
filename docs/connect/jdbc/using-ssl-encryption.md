---
title: Usando a criptografia SSL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8e566243-2f93-4b21-8065-3c8336649309
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5444946843576f87b6887d2bc9446d0a93d5106d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="using-ssl-encryption"></a>Usando criptografia SSL
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Criptografia do Secure Sockets Layer (SSL) permite a transmissão de dados criptografados pela rede entre uma instância de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e um aplicativo cliente.  
  
 O Protocolo SSL é um protocolo que estabelece um canal de comunicação seguro para impedir a intercepção de informações críticas ou confidenciais pela rede e outras comunicações de Internet. O SSL permite o cliente e o servidor autentiquem a identidade um do outro. Depois que os participantes são autenticados, o SSL fornece conexões criptografadas entre eles para transmissão de mensagem segura.  
  
 O [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornece uma infraestrutura para habilitar e desabilitar a criptografia em uma conexão específica com base no usuário especificado propriedades de conexão e as configurações de cliente e servidor. O usuário pode especificar o local de repositório de certificados e senha, um nome de host a ser usado para validar o certificado, e quando criptografar o canal de comunicação.  
  
 A habilitação da criptografia SSL aumenta a segurança dos dados transmitidos pelas redes entre instâncias do [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e aplicativos. Porém, a habilitação da criptografia reduz o desempenho.  
  
 Os tópicos nesta seção descrevem como o [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] versão dá suporte à criptografia SSL, inclusive novas propriedades de conexão e como você pode configurar o repositório de confiança no lado do cliente.  
  
> [!NOTE]  
>  O **hostNameInCertificate** propriedade de conexão é recomendada para validar um certificado SSL.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Description|  
|-----------|-----------------|  
|[Noções básicas sobre suporte a SSL](../../connect/jdbc/understanding-ssl-support.md)|Descreve como o [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] oferece suporte à criptografia SSL.|  
|[Conectando-se com criptografia SSL](../../connect/jdbc/connecting-with-ssl-encryption.md)|Descreve como se conectar a um [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] banco de dados usando as novas propriedades de conexão específicas do SSL.|  
|[Configurando o cliente para criptografia SSL](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md)|Descreve como configurar o repositório de confiança padrão do lado do cliente e como importar um certificado privado para o repositório de confiança do computador cliente.|  
  
## <a name="see-also"></a>Consulte também  
 [Protegendo aplicativos do JDBC Driver](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
