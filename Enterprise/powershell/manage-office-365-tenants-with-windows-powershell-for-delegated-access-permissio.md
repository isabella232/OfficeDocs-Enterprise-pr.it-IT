---
title: Gestire tenant Office 365 con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: 'Riepilogo: utilizzare Windows PowerShell per gestire i tenancy dei propri clienti tramite Office 365.'
ms.openlocfilehash: f4c6f1a0275e9b483a30b31564426b62241029bf
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="88202-103">Gestire tenant Office 365 con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)</span><span class="sxs-lookup"><span data-stu-id="88202-103">Manage Office 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="88202-104">**Sintesi:** Utilizzare Windows PowerShell per gestire i tenancy dei propri clienti tramite Office 365.</span><span class="sxs-lookup"><span data-stu-id="88202-104">**Summary:** Use Windows PowerShell for Office 365 to manage your customer tenancies.</span></span>
  
<span data-ttu-id="88202-p101">Windows PowerShell agevola i Partner di Syndication e Cloud Solution Provider (CSP) nell'amministrazione e nella creazione di report sulle impostazioni dei tenancy dei clienti che non sono disponibili nell'interfaccia di amministrazione di Office 365. Tenere presente che le autorizzazioni Amministra per conto terzi (AOBO, Administer On Behalf Of) sono necessarie all'account amministratore del partner per connettersi ai tenancy dei clienti.</span><span class="sxs-lookup"><span data-stu-id="88202-p101">Windows PowerShell allows Syndication and Cloud Solution Provider (CSP) partners to easily administer and report on customer tenancy settings that are not available in the Office 365 admin center. Note that Administer on Behalf Of (AOBO) permissions are required for the partner administrator account to connect to its customer tenancies.</span></span>
  
<span data-ttu-id="88202-p102">I partner di autorizzazione accesso delegato (DAP, Delegated Access Permission) sono partner di Syndication e Cloud Solution Provider (CSP). Di solito, rappresentano fornitori di rete o telecomunicazioni di altre aziende. Consentono di raggruppare le sottoscrizioni Office 365 nelle offerte di servizio per i clienti. Quando vendono una sottoscrizione a Office 365, ricevono automaticamente le autorizzazioni Amministra per conto terzi per itenancy cliente, al fine di gestire ed eseguire segnalazioni per tutti i tenancy dei clienti.</span><span class="sxs-lookup"><span data-stu-id="88202-p102">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners. They are frequently network or telecom providers to other companies. They bundle Office 365 subscriptions into their service offerings to their customers. When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to thecustomer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="88202-111">Che cosa è necessario sapere prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="88202-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="88202-p103">Le procedure descritte in questo argomento richiedono all'utente di connettersi a Windows PowerShell per Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="88202-p103">The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="88202-114">Sono necessarie anche le credenziali di amministratore tenant del partner.</span><span class="sxs-lookup"><span data-stu-id="88202-114">You also need your partner tenant administrator credentials.</span></span>
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="88202-115">Operazione desiderata</span><span class="sxs-lookup"><span data-stu-id="88202-115">What do you want to do?</span></span>

### <a name="list-all-tenant-ids"></a><span data-ttu-id="88202-116">Elencare tutti gli ID tenant</span><span class="sxs-lookup"><span data-stu-id="88202-116">List all tenant IDs</span></span>

> [!NOTE]
> <span data-ttu-id="88202-p104">Se si dispone di più di 500 tenant, definire l'ambito della sintassi del cmdlet con  _-All_ o _-MaxResultsParameter_. Questo è applicabile agli altri cmdlet che possono fornire un output di grandi dimensioni, come **Get-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="88202-p104">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span></span>
  
<span data-ttu-id="88202-119">Per elencare tutti gli ID tenant dei clienti ai quali si ha accesso, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="88202-119">To list all customer tenant Ids that you have access to, run this command.</span></span>
  
```
Get-MsolPartnerContract -All | Select-Object -TenantId
```

<span data-ttu-id="88202-120">In questo modo verrà visualizzato un elenco di tutti i tenant dei clienti tramite **TenantId**.</span><span class="sxs-lookup"><span data-stu-id="88202-120">This will display a listing of all your customer tenants by **TenantId**.</span></span>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a><span data-ttu-id="88202-121">Ottenere un ID tenant tramite il nome di dominio</span><span class="sxs-lookup"><span data-stu-id="88202-121">Get a tenant ID by using the domain name</span></span>

<span data-ttu-id="88202-p105">Per ottenere il **TenantId** per il tenant di un cliente specifico per nome di dominio, eseguire questo comando. Sostituire _<nomedominio.onmicrosoft.com>_ con il nome di dominio effettivo del tenant del cliente desiderato.</span><span class="sxs-lookup"><span data-stu-id="88202-p105">To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span></span>
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object -TenantId
```

### <a name="list-all-domains-for-a-tenant"></a><span data-ttu-id="88202-124">Elencare tutti i domini per un tenant</span><span class="sxs-lookup"><span data-stu-id="88202-124">List all domains for a tenant</span></span>

<span data-ttu-id="88202-p106">Per ottenere tutti i domini per il tenant di un cliente qualsiasi, eseguire questo comando. Sostituire  _<customer TenantId value>_ con il valore effettivo.</span><span class="sxs-lookup"><span data-stu-id="88202-p106">To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

<span data-ttu-id="88202-127">Se sono stati registrati ulteriori domini, verranno restituiti tutti i domini associati al **TenantId** del cliente.</span><span class="sxs-lookup"><span data-stu-id="88202-127">If you have registered additional domains, this will return all domains associated with the customer **TenantId**.</span></span>
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a><span data-ttu-id="88202-128">Ottenere un mapping di tutti i tenant e i domini registrati</span><span class="sxs-lookup"><span data-stu-id="88202-128">Get a mapping of all tenants and registered domains</span></span>

<span data-ttu-id="88202-p107">La versione precedente di Windows PowerShell per i comandi di Office 365 mostrava come recuperare gli ID tenant o i domini, ma non entrambi contemporaneamente e senza fornire un mapping chiaro tra di loro. Questo comando consente di generare un elenco di tutti gli ID tenant dei clienti e i relativi domini.</span><span class="sxs-lookup"><span data-stu-id="88202-p107">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all. This command generates a listing of all your customer tenant IDs and their domains.</span></span>
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a><span data-ttu-id="88202-131">Ottenere tutti gli utenti per un tenant</span><span class="sxs-lookup"><span data-stu-id="88202-131">Get all users for a tenant</span></span>

<span data-ttu-id="88202-p108">Questo comando consente di visualizzare lo stato **UserPrincipalName**, **DisplayName** e **isLicensed** per tutti gli utenti di un tenant particolare. Sostituire _<customer TenantId value>_ con il valore effettivo.</span><span class="sxs-lookup"><span data-stu-id="88202-p108">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a><span data-ttu-id="88202-134">Ottenere tutti i dettagli di un utente</span><span class="sxs-lookup"><span data-stu-id="88202-134">Get all details about a user</span></span>

<span data-ttu-id="88202-p109">Se si desidera visualizzare tutte le proprietà per un utente particolare, eseguire questo comando. Sostituire _<customer TenantId value>_  e _<user principal name value>_ con i valori effettivi.</span><span class="sxs-lookup"><span data-stu-id="88202-p109">If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span></span>
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a><span data-ttu-id="88202-137">Aggiungere utenti, impostare opzioni e assegnare licenze</span><span class="sxs-lookup"><span data-stu-id="88202-137">Add users, set options, and assign licenses</span></span>

<span data-ttu-id="88202-p110">La creazione in blocco, configurazione e gestione di licenze degli utenti di Office 365 è particolarmente efficiente utilizzando Windows PowerShell per Office 365. In questa procedura di due passaggi, prima vengono create le voci per tutti gli utenti che si desidera aggiungere in un file CSV (con valori delimitati da virgole), per poi importare tale file usando Windows PowerShell per Office 365.</span><span class="sxs-lookup"><span data-stu-id="88202-p110">The bulk creation, configuration, and licensing of Office 365 users is particularly efficient by using Windows PowerShell for Office 365. In this two-step process, you first create entries for all the users you want to add in a comma-separated value (CSV) file and then import that file by using Windows PowerShell for Office 365.</span></span> 
  
#### <a name="create-a-csv-file"></a><span data-ttu-id="88202-140">Creare un file CSV</span><span class="sxs-lookup"><span data-stu-id="88202-140">Create a CSV file</span></span>

<span data-ttu-id="88202-141">Creare un file CSV utilizzando questo formato:</span><span class="sxs-lookup"><span data-stu-id="88202-141">Create a CSV file by using this format:</span></span>
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
<span data-ttu-id="88202-142">dove:</span><span class="sxs-lookup"><span data-stu-id="88202-142">where:</span></span>
  
- <span data-ttu-id="88202-p111">**UsageLocation**: questo valore è costituito dal codice paese ISO di due lettere dell'utente. I codici paese ISO sono disponibili nella piattaforma[Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). Il codice per gli Stati Uniti, ad esempio, è US e quello per il Brasile è BR.</span><span class="sxs-lookup"><span data-stu-id="88202-p111">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR.</span></span> 
    
- <span data-ttu-id="88202-p112">**LicenseAssignment**: questo valore utilizza il seguente formato: `syndication-account:<PROVISIONING_ID>`. Ad esempio, se si assegnano licenze O365_Business_Premium agli utenti del tenant dei clienti, il valore **LicenseAssignment** sarà simile al seguente: **syndication-account:O365_Business_Premium**. I PROVISIONING_ID sono disponibili nel portale per i partner Syndication al quale è stato effettuato l'accesso come partner Syndication o CSP.</span><span class="sxs-lookup"><span data-stu-id="88202-p112">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span></span>
    
#### <a name="import-the-csv-file-and-create-the-users"></a><span data-ttu-id="88202-149">Importare il file CSV e creare gli utenti</span><span class="sxs-lookup"><span data-stu-id="88202-149">Import the CSV file and create the users</span></span>

<span data-ttu-id="88202-p113">In seguito alla creazione del file CSV, eseguire questo comando per creare account utente con password senza scadenza che l'utente deve modificare al primo accesso e con cui viene assegnata la licenza specificata. Sostituire il nome del file CSV corretto.</span><span class="sxs-lookup"><span data-stu-id="88202-p113">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.</span></span>
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a><span data-ttu-id="88202-152">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="88202-152">See also</span></span>

#### 

[<span data-ttu-id="88202-153">Guida per partner</span><span class="sxs-lookup"><span data-stu-id="88202-153">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=533477)

