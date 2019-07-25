---
title: Aggiungere un dominio a un tenancy client con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 'Riepilogo: utilizzare Windows PowerShell per Office 365 per aggiungere un nome di dominio alternativo al tenant di un cliente esistente.'
ms.openlocfilehash: 60088a9eafa1f5380eef2cc0240b0f5b5b02fe0f
ms.sourcegitcommit: 68181eca8e43ea7f5dfd89cbaf587bc0c260ca7e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2019
ms.locfileid: "35853229"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="248e9-103">Aggiungere un dominio a un tenancy client con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)</span><span class="sxs-lookup"><span data-stu-id="248e9-103">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="248e9-104">**Sintesi:** Utilizzare Windows PowerShell per Office 365 per aggiungere un nome di dominio alternativo al tenant di un cliente esistente.</span><span class="sxs-lookup"><span data-stu-id="248e9-104">**Summary:** Use Windows PowerShell for Office 365 to add an alternate domain name to an existing customer tenant.</span></span>
  
<span data-ttu-id="248e9-105">È possibile creare e associare nuovi domini al tenancy del cliente con Windows PowerShell per Office 365 in modo più rapido rispetto all’interfaccia di amministrazione di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="248e9-105">You can create and associate new domains with your customer's tenancy with Windows PowerShell for Office 365 faster than using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="248e9-106">I partner di autorizzazione accesso delegato (DAP, Delegated Access Permission) sono partner di Syndication e Cloud Solution Provider (CSP).</span><span class="sxs-lookup"><span data-stu-id="248e9-106">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="248e9-107">Di solito, rappresentano fornitori di rete o telecomunicazioni di altre aziende.</span><span class="sxs-lookup"><span data-stu-id="248e9-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="248e9-108">Consentono di raggruppare le sottoscrizioni Office 365 nelle offerte di servizio per i clienti.</span><span class="sxs-lookup"><span data-stu-id="248e9-108">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="248e9-109">Quando vendono un abbonamento a Office 365, vengono loro concesse automaticamente le autorizzazioni Amministra per conto terzi ai tenancy dei clienti in modo che possano amministrare ed effettuare report sui tenancy dei clienti.</span><span class="sxs-lookup"><span data-stu-id="248e9-109">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="248e9-110">Che cosa è necessario sapere prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="248e9-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="248e9-p102">Le procedure descritte in questo argomento richiedono all'utente di connettersi a Windows PowerShell per Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="248e9-p102">The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="248e9-113">Sono necessarie anche le credenziali di amministratore tenant del partner.</span><span class="sxs-lookup"><span data-stu-id="248e9-113">You also need your partner tenant administrator credentials.</span></span>
  
<span data-ttu-id="248e9-114">Sono necessarie anche le informazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="248e9-114">You also need the following information:</span></span>
  
- <span data-ttu-id="248e9-115">È necessario il nome di dominio completo (FQDN) che desidera il cliente.</span><span class="sxs-lookup"><span data-stu-id="248e9-115">You need the fully qualified domain name (FQDN) that your customer wants.</span></span>
    
- <span data-ttu-id="248e9-116">È necessario il **TenantId** del cliente.</span><span class="sxs-lookup"><span data-stu-id="248e9-116">You need the customer's **TenantId**.</span></span>
    
- <span data-ttu-id="248e9-p103">Il nome di dominio completo deve essere registrato con un registrar di DNS (Domain Name Service), come GoDaddy. Per ulteriori informazioni su come registrare pubblicamente un nome di dominio, vedere [Come acquistare un nome di dominio](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span><span class="sxs-lookup"><span data-stu-id="248e9-p103">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span></span>
    
- <span data-ttu-id="248e9-p104">È necessario conoscere la procedura per aggiungere un record TXT alla zona DNS registrata per il proprio registrar. Per ulteriori informazioni su come aggiungere un record TXT, vedere [Creare record DNS presso un provider di hosting DNS per Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). Se queste procedure non funzionano, è necessario trovare quelle adatte al proprio registrar.</span><span class="sxs-lookup"><span data-stu-id="248e9-p104">You need to know how to add a TXT record to the registered DNS zone for your DNS registrar. For more information on how to add a TXT record, see [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). If those procedures don't work for you, you will need to find the procedures for your DNS registrar.</span></span>
    
## <a name="create-domains"></a><span data-ttu-id="248e9-122">Creare domini</span><span class="sxs-lookup"><span data-stu-id="248e9-122">Create domains</span></span>

 <span data-ttu-id="248e9-p105">Probabilmente i propri clienti richiederanno la creazione di domini aggiuntivi da associare ai loro tenancy perché non vogliono che il dominio principale per rappresentare le loro identità aziendali a livello mondiale sia quello predefinito, vale a dire <domain>.onmicrosoft.com sia quello principale che rappresenta le identità aziendali al mondo. La procedura seguente illustra i passaggi per creare un nuovo dominio associato alla tenancy del cliente.</span><span class="sxs-lookup"><span data-stu-id="248e9-p105">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.</span></span>
  
> [!NOTE]
> <span data-ttu-id="248e9-125">Per eseguire alcune di queste operazioni, è necessario che l'account amministratore partner con cui si esegue l'accesso debba essere impostato su **amministrazione completa** per l'impostazione **assegna accesso amministrativo alle società supportate** nell'ambito dei dettagli dell'account di amministratore nell' Interfaccia di amministrazione di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="248e9-125">To perform some of these operations, the partner administrator account you sign in with must be set to **Full administration** for the **Assign administrative access to companies you support** setting found in the details of the admin account in the Microsoft 365 admin center.</span></span> <span data-ttu-id="248e9-126">Per ulteriori informazioni sulla gestione dei ruoli di amministratore del partner, vedere[Partner: offrire l'amministrazione delegata](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span><span class="sxs-lookup"><span data-stu-id="248e9-126">For more information on managing partner administrator roles, see[Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span></span> 
  
### <a name="create-the-domain-in-azure-active-directory"></a><span data-ttu-id="248e9-127">Creare il dominio in Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="248e9-127">Create the domain in Azure Active Directory</span></span>

<span data-ttu-id="248e9-128">Questo comando consente di creare il dominio in Azure Active Directory ma non di associarlo al dominio registrato pubblicamente.</span><span class="sxs-lookup"><span data-stu-id="248e9-128">This command creates the domain in Azure Active Directory but does not associate it with the publicly registered domain.</span></span> <span data-ttu-id="248e9-129">Questo si verifica quando si prova di essere proprietari del dominio registrato pubblicamente in Microsoft Office 365 per aziende.</span><span class="sxs-lookup"><span data-stu-id="248e9-129">That comes when you prove that you own the publicly registered domain to Microsoft Office 365 for enterprises.</span></span>
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

### <a name="get-the-data-for-the-dns-txt-verification-record"></a><span data-ttu-id="248e9-130">Recuperare i dati per il record di verifica TXT DNS</span><span class="sxs-lookup"><span data-stu-id="248e9-130">Get the data for the DNS TXT verification record</span></span>

 <span data-ttu-id="248e9-p108">Office 365 genererà i dati specifici da inserire nel record di verifica TXT DNS. Per ottenere i dati, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="248e9-p108">Office 365 will generate the specific data that you need to place into the DNS TXT verification record. To get the data, run this command.</span></span>
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

<span data-ttu-id="248e9-133">Si otterrà quanto segue:</span><span class="sxs-lookup"><span data-stu-id="248e9-133">This will give you output like:</span></span>
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> <span data-ttu-id="248e9-134">Questo testo sarà necessario per creare il record TXT nella zona DNS registrata pubblicamente.</span><span class="sxs-lookup"><span data-stu-id="248e9-134">You will need this text to create the TXT record in the publicly registered DNS zone.</span></span> <span data-ttu-id="248e9-135">Copiarlo e salvarlo.</span><span class="sxs-lookup"><span data-stu-id="248e9-135">Be sure to copy and save it.</span></span> 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a><span data-ttu-id="248e9-136">Aggiungere un record TXT per l'area DNS registrata pubblicamente</span><span class="sxs-lookup"><span data-stu-id="248e9-136">Add a TXT record to the publically registered DNS zone</span></span>

<span data-ttu-id="248e9-137">Prima che Office 365 inizi ad accettare il traffico diretto al nome di dominio registrato pubblicamente, è necessario dimostrare di essere il proprietario e disporre delle autorizzazioni di amministratore per il dominio.</span><span class="sxs-lookup"><span data-stu-id="248e9-137">Before Office 365 will start accepting traffic that is directed to the publicly registered domain name, you must prove that you own and have administrator permissions to the domain.</span></span> <span data-ttu-id="248e9-138">È possibile dimostrare di essere il proprietario del dominio creando un record TXT nel dominio.</span><span class="sxs-lookup"><span data-stu-id="248e9-138">You prove you own the domain by creating a TXT record in the domain.</span></span> <span data-ttu-id="248e9-139">Un record TXT non produce alcun effetto sul dominio e può essere eliminato dopo aver confermato la proprietà del dominio.</span><span class="sxs-lookup"><span data-stu-id="248e9-139">A TXT record doesn't do anything in your domain, and it can be deleted after your ownership of the domain is established.</span></span> <span data-ttu-id="248e9-140">Per creare il record TXT, seguire le procedure descritte in [Creare record DNS presso un provider di hosting DNS per Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span><span class="sxs-lookup"><span data-stu-id="248e9-140">To create the TXT records, follow the procedures at [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span></span> <span data-ttu-id="248e9-141">Se queste procedure non funzionano, è necessario trovare quelle adatte al proprio registrar DNS.</span><span class="sxs-lookup"><span data-stu-id="248e9-141">If those procedures don't work for you , you need to find the procedures for your DNS registrar.</span></span>
  
<span data-ttu-id="248e9-p111">Confermare la creazione del record TXT tramite nslookup. Seguire questa sintassi:</span><span class="sxs-lookup"><span data-stu-id="248e9-p111">Confirm the successful creation of the TXT record via nslookup. Follow this syntax.</span></span>
  
```
nslookup -type=TXT <FQDN of registered domain>
```

<span data-ttu-id="248e9-144">Si otterrà quanto segue:</span><span class="sxs-lookup"><span data-stu-id="248e9-144">This will give you output like:</span></span>
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a><span data-ttu-id="248e9-145">Dimostrare la proprietà del dominio in Office 365</span><span class="sxs-lookup"><span data-stu-id="248e9-145">Validate domain ownership in Office 365</span></span>

<span data-ttu-id="248e9-p112">In quest'ultimo passaggio, viene convalidato in Office 365 di essere i proprietari del dominio registrato pubblicamente. Dopo questo passaggio, Office 365 inizierà ad accettare il traffico instradato al nuovo nome di dominio. Per completare la procedura di registrazione e creazione del dominio, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="248e9-p112">In this last step, you validate to Office 365 that you own the publically registered domain. After this step, Office 365 will begin accepting traffic routed to the new domain name. To complete the domain creation and registration process, run this command.</span></span> 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="248e9-149">Questo comando non restituisce alcun output, pertanto, per confermare che ha avuto esito positivo, eseguire il comando riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="248e9-149">This command won't return any output, so to confirm that this worked, run this command.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="248e9-150">Si otterrà un risultato simile al seguente</span><span class="sxs-lookup"><span data-stu-id="248e9-150">This will return something like this</span></span>
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a><span data-ttu-id="248e9-151">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="248e9-151">See also</span></span>

#### 

[<span data-ttu-id="248e9-152">Guida per partner</span><span class="sxs-lookup"><span data-stu-id="248e9-152">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

