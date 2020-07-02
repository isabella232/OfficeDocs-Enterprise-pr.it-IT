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
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="daf7f-103">Aggiungere un dominio a un tenancy client con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)</span><span class="sxs-lookup"><span data-stu-id="daf7f-103">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

<span data-ttu-id="daf7f-104">È possibile creare e associare nuovi domini alla locazione del cliente con Windows PowerShell per Microsoft 365 più velocemente rispetto all'interfaccia di amministrazione di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="daf7f-104">You can create and associate new domains with your customer's tenancy with Windows PowerShell for Microsoft 365 faster than using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="daf7f-105">I partner di autorizzazione accesso delegato (DAP, Delegated Access Permission) sono partner di Syndication e Cloud Solution Provider (CSP).</span><span class="sxs-lookup"><span data-stu-id="daf7f-105">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="daf7f-106">Di solito, rappresentano fornitori di rete o telecomunicazioni di altre aziende.</span><span class="sxs-lookup"><span data-stu-id="daf7f-106">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="daf7f-107">Essi bundle Microsoft 365 abbonamenti nelle loro offerte di servizi ai propri clienti.</span><span class="sxs-lookup"><span data-stu-id="daf7f-107">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="daf7f-108">Quando vendono un abbonamento a Microsoft 365, vengono concesse automaticamente amministra per conto di (AOBO) le autorizzazioni per il cliente locazione in modo che possano amministrare e segnalare sul locazione cliente.</span><span class="sxs-lookup"><span data-stu-id="daf7f-108">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="daf7f-109">Che cosa è necessario sapere prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="daf7f-109">What do you need to know before you begin?</span></span>

<span data-ttu-id="daf7f-110">The procedures in this topic require you to connect to Windows PowerShell for Office 365.</span><span class="sxs-lookup"><span data-stu-id="daf7f-110">The procedures in this topic require you to connect to Windows PowerShell for Office 365.</span></span> <span data-ttu-id="daf7f-111">For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="daf7f-111">For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="daf7f-112">Sono necessarie anche le credenziali di amministratore tenant del partner.</span><span class="sxs-lookup"><span data-stu-id="daf7f-112">You also need your partner tenant administrator credentials.</span></span>
  
<span data-ttu-id="daf7f-113">Sono necessarie anche le informazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="daf7f-113">You also need the following information:</span></span>
  
- <span data-ttu-id="daf7f-114">È necessario il nome di dominio completo (FQDN) che desidera il cliente.</span><span class="sxs-lookup"><span data-stu-id="daf7f-114">You need the fully qualified domain name (FQDN) that your customer wants.</span></span>
    
- <span data-ttu-id="daf7f-115">È necessario il **TenantId** del cliente.</span><span class="sxs-lookup"><span data-stu-id="daf7f-115">You need the customer's **TenantId**.</span></span>
    
- <span data-ttu-id="daf7f-116">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy.</span><span class="sxs-lookup"><span data-stu-id="daf7f-116">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy.</span></span> <span data-ttu-id="daf7f-117">For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span><span class="sxs-lookup"><span data-stu-id="daf7f-117">For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span></span>
    
- <span data-ttu-id="daf7f-118">È necessario conoscere la procedura per aggiungere un record TXT alla zona DNS registrata per il proprio registrar.</span><span class="sxs-lookup"><span data-stu-id="daf7f-118">You need to know how to add a TXT record to the registered DNS zone for your DNS registrar.</span></span> <span data-ttu-id="daf7f-119">Per ulteriori informazioni su come aggiungere un record TXT, vedere [Add DNS Records to Connect Your Domain](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span><span class="sxs-lookup"><span data-stu-id="daf7f-119">For more information on how to add a TXT record, see [Add DNS records to connect your domain](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span></span> <span data-ttu-id="daf7f-120">Se queste procedure non funzionano, è necessario trovare quelle adatte al proprio registrar.</span><span class="sxs-lookup"><span data-stu-id="daf7f-120">If those procedures don't work for you, you will need to find the procedures for your DNS registrar.</span></span>
    
## <a name="create-domains"></a><span data-ttu-id="daf7f-121">Creare domini</span><span class="sxs-lookup"><span data-stu-id="daf7f-121">Create domains</span></span>

 <span data-ttu-id="daf7f-122">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world.</span><span class="sxs-lookup"><span data-stu-id="daf7f-122">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world.</span></span> <span data-ttu-id="daf7f-123">This procedure walks you through creating a new domain associated with your customer's tenancy.</span><span class="sxs-lookup"><span data-stu-id="daf7f-123">This procedure walks you through creating a new domain associated with your customer's tenancy.</span></span>
  
> [!NOTE]
> <span data-ttu-id="daf7f-124">Per eseguire alcune di queste operazioni, è necessario che l'account di amministratore del partner con cui si esegue l'accesso sia impostato su **amministrazione completa** per l'impostazione **assegna accesso amministrativo alle società supportate** in informazioni dettagliate sull'account di amministratore nell'interfaccia di amministrazione di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="daf7f-124">To perform some of these operations, the partner administrator account you sign in with must be set to **Full administration** for the **Assign administrative access to companies you support** setting found in the details of the admin account in the Microsoft 365 admin center.</span></span> <span data-ttu-id="daf7f-125">Per ulteriori informazioni sulla gestione dei ruoli di amministratore partner, vedere [Partners: offer Delegated Administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span><span class="sxs-lookup"><span data-stu-id="daf7f-125">For more information on managing partner administrator roles, see [Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span></span> 
  
### <a name="create-the-domain-in-azure-active-directory"></a><span data-ttu-id="daf7f-126">Creare il dominio in Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="daf7f-126">Create the domain in Azure Active Directory</span></span>

<span data-ttu-id="daf7f-127">Questo comando consente di creare il dominio in Azure Active Directory ma non di associarlo al dominio registrato pubblicamente.</span><span class="sxs-lookup"><span data-stu-id="daf7f-127">This command creates the domain in Azure Active Directory but does not associate it with the publicly registered domain.</span></span> <span data-ttu-id="daf7f-128">Viene fornito quando si dimostra di essere proprietari del dominio registrato a Microsoft Microsoft 365 per le aziende.</span><span class="sxs-lookup"><span data-stu-id="daf7f-128">That comes when you prove that you own the publicly registered domain to Microsoft Microsoft 365 for enterprises.</span></span>
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

>[!Note]
><span data-ttu-id="daf7f-129">PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per Windows PowerShell e i cmdlet con **MSOL** all'interno del nome.</span><span class="sxs-lookup"><span data-stu-id="daf7f-129">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="daf7f-130">Per continuare a usare i cmdlet, è necessario eseguirli in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="daf7f-130">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="get-the-data-for-the-dns-txt-verification-record"></a><span data-ttu-id="daf7f-131">Recuperare i dati per il record di verifica TXT DNS</span><span class="sxs-lookup"><span data-stu-id="daf7f-131">Get the data for the DNS TXT verification record</span></span>

 <span data-ttu-id="daf7f-132">Microsoft 365 genererà i dati specifici che è necessario inserire nel record di verifica TXT DNS.</span><span class="sxs-lookup"><span data-stu-id="daf7f-132">Microsoft 365 will generate the specific data that you need to place into the DNS TXT verification record.</span></span> <span data-ttu-id="daf7f-133">Per ottenere i dati, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="daf7f-133">To get the data, run this command.</span></span>
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

<span data-ttu-id="daf7f-134">Si otterrà quanto segue:</span><span class="sxs-lookup"><span data-stu-id="daf7f-134">This will give you output like:</span></span>
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> <span data-ttu-id="daf7f-135">Questo testo sarà necessario per creare il record TXT nella zona DNS registrata pubblicamente.</span><span class="sxs-lookup"><span data-stu-id="daf7f-135">You will need this text to create the TXT record in the publicly registered DNS zone.</span></span> <span data-ttu-id="daf7f-136">Copiarlo e salvarlo.</span><span class="sxs-lookup"><span data-stu-id="daf7f-136">Be sure to copy and save it.</span></span> 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a><span data-ttu-id="daf7f-137">Aggiungere un record TXT per l'area DNS registrata pubblicamente</span><span class="sxs-lookup"><span data-stu-id="daf7f-137">Add a TXT record to the publically registered DNS zone</span></span>

<span data-ttu-id="daf7f-138">Prima che Microsoft 365 inizi ad accettare il traffico indirizzato al nome di dominio registrato pubblicamente, è necessario dimostrare di essere proprietari e disporre delle autorizzazioni di amministratore per il dominio.</span><span class="sxs-lookup"><span data-stu-id="daf7f-138">Before Microsoft 365 will start accepting traffic that is directed to the publicly registered domain name, you must prove that you own and have administrator permissions to the domain.</span></span> <span data-ttu-id="daf7f-139">È possibile dimostrare di essere il proprietario del dominio creando un record TXT nel dominio.</span><span class="sxs-lookup"><span data-stu-id="daf7f-139">You prove you own the domain by creating a TXT record in the domain.</span></span> <span data-ttu-id="daf7f-140">Un record TXT non produce alcun effetto sul dominio e può essere eliminato dopo aver confermato la proprietà del dominio.</span><span class="sxs-lookup"><span data-stu-id="daf7f-140">A TXT record doesn't do anything in your domain, and it can be deleted after your ownership of the domain is established.</span></span> <span data-ttu-id="daf7f-141">Per creare i record TXT, seguire le procedure illustrate in [Add DNS Records to Connect Your Domain](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span><span class="sxs-lookup"><span data-stu-id="daf7f-141">To create the TXT records, follow the procedures at [Add DNS records to connect your domain](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span></span> <span data-ttu-id="daf7f-142">Se queste procedure non funzionano, è necessario trovare quelle adatte al proprio registrar DNS.</span><span class="sxs-lookup"><span data-stu-id="daf7f-142">If those procedures don't work for you , you need to find the procedures for your DNS registrar.</span></span>
  
<span data-ttu-id="daf7f-143">Confirm the successful creation of the TXT record via nslookup.</span><span class="sxs-lookup"><span data-stu-id="daf7f-143">Confirm the successful creation of the TXT record via nslookup.</span></span> <span data-ttu-id="daf7f-144">Follow this syntax.</span><span class="sxs-lookup"><span data-stu-id="daf7f-144">Follow this syntax.</span></span>
  
```
nslookup -type=TXT <FQDN of registered domain>
```

<span data-ttu-id="daf7f-145">Si otterrà quanto segue:</span><span class="sxs-lookup"><span data-stu-id="daf7f-145">This will give you output like:</span></span>
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-microsoft-365"></a><span data-ttu-id="daf7f-146">Convalidare la proprietà del dominio in Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="daf7f-146">Validate domain ownership in Microsoft 365</span></span>

<span data-ttu-id="daf7f-147">In questo ultimo passaggio, è possibile convalidare a Microsoft 365 che si è proprietari del dominio registrato pubblicamente.</span><span class="sxs-lookup"><span data-stu-id="daf7f-147">In this last step, you validate to Microsoft 365 that you own the publically registered domain.</span></span> <span data-ttu-id="daf7f-148">Dopo questo passaggio, Microsoft 365 inizierà ad accettare il traffico instradato al nuovo nome di dominio.</span><span class="sxs-lookup"><span data-stu-id="daf7f-148">After this step, Microsoft 365 will begin accepting traffic routed to the new domain name.</span></span> <span data-ttu-id="daf7f-149">Per completare la procedura di registrazione e creazione del dominio, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="daf7f-149">To complete the domain creation and registration process, run this command.</span></span> 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="daf7f-150">Questo comando non restituisce alcun output, pertanto, per confermare che ha avuto esito positivo, eseguire il comando riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="daf7f-150">This command won't return any output, so to confirm that this worked, run this command.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="daf7f-151">Si otterrà un risultato simile al seguente</span><span class="sxs-lookup"><span data-stu-id="daf7f-151">This will return something like this</span></span>
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a><span data-ttu-id="daf7f-152">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="daf7f-152">See also</span></span>

#### 

[<span data-ttu-id="daf7f-153">Guida per partner</span><span class="sxs-lookup"><span data-stu-id="daf7f-153">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

