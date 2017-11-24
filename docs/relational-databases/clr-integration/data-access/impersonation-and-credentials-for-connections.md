---
title: "Representação e credenciais para conexões | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- authentication [CLR integration]
- user impersonation [CLR integration]
- credentials [CLR integration]
- database objects [CLR integration], security
ms.assetid: 293dce7d-1db2-4657-992f-8c583d6e9ebb
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0815ae6b182f371eb171cf577e89a50adb9cdac4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="impersonation-and-credentials-for-connections"></a>Representação e credenciais para conexões
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]No [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] integração common language runtime (CLR), usando a autenticação do Windows é complexa, mas é mais segura do que usando a autenticação do SQL Server. Quando usar a Autenticação do Windows, lembre-se das considerações a seguir.  
  
 Por padrão, um processo do SQL Server que se conecta ao Windows adquire o contexto de segurança da conta de serviço do Windows para SQL Server. Todavia, é possível mapear uma função CLR para uma identidade proxy, de modo que suas conexões de saída tenham um contexto de segurança diferente daquele da conta de serviço do Windows.  
  
 Em alguns casos, talvez você queira representar o chamador usando a **SqlContext.WindowsIdentity** propriedade em vez de executar como a conta de serviço. O **WindowsIdentity** instância representa a identidade do cliente que é chamado de código de chamada e só está disponível quando o cliente usou a autenticação do Windows. Depois de obter o **WindowsIdentity** instância, você pode chamar **representar** para alterar o token de segurança do thread e, em seguida, abra conexões ADO.NET em nome do cliente.  
  
 Depois de chamar SQLContext.WindowsIdentity.Impersonate, você não pode acessar dados locais e você não pode acessar os dados do sistema. Para acessar os dados novamente, você precisa chamar WindowsImpersonationContext.Undo.  
  
 O exemplo a seguir mostra como representar o chamador usando a **SqlContext.WindowsIdentity** propriedade.  
  
 Visual C#  
  
```  
WindowsIdentity clientId = null;  
WindowsImpersonationContext impersonatedUser = null;  
  
clientId = SqlContext.WindowsIdentity;  
  
// This outer try block is used to protect from   
// exception filter attacks which would prevent  
// the inner finally block from executing and   
// resetting the impersonation.  
try  
{  
   try  
   {  
      impersonatedUser = clientId.Impersonate();  
      if (impersonatedUser != null)  
         return GetFileDetails(directoryPath);  
         else return null;  
   }  
   finally  
   {  
      if (impersonatedUser != null)  
         impersonatedUser.Undo();  
   }  
}  
catch  
{  
   throw;  
}  
```  
  
> [!NOTE]  
>  Para obter informações sobre alterações de comportamento na representação, consulte [alterações recentes em recursos do mecanismo de banco de dados no SQL Server 2016](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md).  
  
 Além disso, se você obteve a instância de identidade do [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, por padrão não poderá propagar essa instância para outro computador; a infraestrutura de segurança do Windows impõe essa restrição por padrão. Porém, há um mecanismo chamado "delegação" que permite a propagação de identidades do Windows por vários computadores. Você pode aprender mais sobre delegação no artigo da TechNet, "[transição de protocolo Kerberos e delegação restrita](http://go.microsoft.com/fwlink/?LinkId=50419)".  
  
## <a name="see-also"></a>Consulte também  
 [Objeto SqlContext](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  