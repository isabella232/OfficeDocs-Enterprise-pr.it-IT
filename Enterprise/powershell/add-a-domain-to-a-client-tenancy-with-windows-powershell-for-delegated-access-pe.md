---
title: Aggiungere un dominio a un tenancy client con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 'Riepilogo: utilizzare Windows PowerShell per Microsoft 365 per aggiungere un nome di dominio alternativo al tenant di un cliente esistente.'
ms.openlocfilehash: 6ba706c1fc0b2e2b43687ac582a40f36a2a3387c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997362"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>Aggiungere un dominio a un tenancy client con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)

È possibile creare e associare nuovi domini alla locazione del cliente con Windows PowerShell per Microsoft 365 più velocemente rispetto all'interfaccia di amministrazione di Microsoft 365.
  
I partner di autorizzazione accesso delegato (DAP, Delegated Access Permission) sono partner di Syndication e Cloud Solution Provider (CSP). Di solito, rappresentano fornitori di rete o telecomunicazioni di altre aziende. Essi bundle Microsoft 365 abbonamenti nelle loro offerte di servizi ai propri clienti. Quando vendono un abbonamento a Microsoft 365, vengono concesse automaticamente amministra per conto di (AOBO) le autorizzazioni per il cliente locazione in modo che possano amministrare e segnalare sul locazione cliente.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Che cosa è necessario sapere prima di iniziare

The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).
  
Sono necessarie anche le credenziali di amministratore tenant del partner.
  
Sono necessarie anche le informazioni seguenti:
  
- È necessario il nome di dominio completo (FQDN) che desidera il cliente.
    
- È necessario il **TenantId** del cliente.
    
- The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).
    
- È necessario conoscere la procedura per aggiungere un record TXT alla zona DNS registrata per il proprio registrar. Per ulteriori informazioni su come aggiungere un record TXT, vedere [Add DNS Records to Connect Your Domain](https://go.microsoft.com/fwlink/p/?LinkId=532542). Se queste procedure non funzionano, è necessario trovare quelle adatte al proprio registrar.
    
## <a name="create-domains"></a>Creare domini

 Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.
  
> [!NOTE]
> Per eseguire alcune di queste operazioni, è necessario che l'account di amministratore del partner con cui si esegue l'accesso sia impostato su **amministrazione completa** per l'impostazione **assegna accesso amministrativo alle società supportate** in informazioni dettagliate sull'account di amministratore nell'interfaccia di amministrazione di Microsoft 365. Per ulteriori informazioni sulla gestione dei ruoli di amministratore partner, vedere [Partners: offer Delegated Administration](https://go.microsoft.com/fwlink/p/?LinkId=532435). 
  
### <a name="create-the-domain-in-azure-active-directory"></a>Creare il dominio in Azure Active Directory

Questo comando consente di creare il dominio in Azure Active Directory ma non di associarlo al dominio registrato pubblicamente. Viene fornito quando si dimostra di essere proprietari del dominio registrato a Microsoft Microsoft 365 per le aziende.
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

>[!Note]
>PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per Windows PowerShell e i cmdlet con **MSOL** all'interno del nome. Per continuare a usare i cmdlet, è necessario eseguirli in Windows PowerShell.
>

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>Recuperare i dati per il record di verifica TXT DNS

 Microsoft 365 genererà i dati specifici che è necessario inserire nel record di verifica TXT DNS. Per ottenere i dati, eseguire questo comando.
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

Si otterrà quanto segue:
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> Questo testo sarà necessario per creare il record TXT nella zona DNS registrata pubblicamente. Copiarlo e salvarlo. 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>Aggiungere un record TXT per l'area DNS registrata pubblicamente

Prima che Microsoft 365 inizi ad accettare il traffico indirizzato al nome di dominio registrato pubblicamente, è necessario dimostrare di essere proprietari e disporre delle autorizzazioni di amministratore per il dominio. È possibile dimostrare di essere il proprietario del dominio creando un record TXT nel dominio. Un record TXT non produce alcun effetto sul dominio e può essere eliminato dopo aver confermato la proprietà del dominio. Per creare i record TXT, seguire le procedure illustrate in [Add DNS Records to Connect Your Domain](https://go.microsoft.com/fwlink/p/?LinkId=532542). Se queste procedure non funzionano, è necessario trovare quelle adatte al proprio registrar DNS.
  
Confirm the successful creation of the TXT record via nslookup. Follow this syntax.
  
```
nslookup -type=TXT <FQDN of registered domain>
```

Si otterrà quanto segue:
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-microsoft-365"></a>Convalidare la proprietà del dominio in Microsoft 365

In questo ultimo passaggio, è possibile convalidare a Microsoft 365 che si è proprietari del dominio registrato pubblicamente. Dopo questo passaggio, Microsoft 365 inizierà ad accettare il traffico instradato al nuovo nome di dominio. Per completare la procedura di registrazione e creazione del dominio, eseguire questo comando. 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Questo comando non restituisce alcun output, pertanto, per confermare che ha avuto esito positivo, eseguire il comando riportato di seguito.
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Si otterrà un risultato simile al seguente
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a>Vedere anche

#### 

[Guida per partner](https://go.microsoft.com/fwlink/p/?LinkID=533477)

