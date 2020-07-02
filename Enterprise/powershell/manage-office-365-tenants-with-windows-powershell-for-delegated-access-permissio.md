---
title: Gestire i tenant Microsoft 365 con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegate Access Permissions)
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
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: 'Riepilogo: utilizzare Windows PowerShell per Microsoft 365 per gestire le locazione del cliente.'
ms.openlocfilehash: a57f66ec02f5ba69006c17a9cf734e622017b8fb
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998232"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Gestire i tenant Microsoft 365 con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegate Access Permissions)

Windows PowerShell consente ai partner di syndication e Cloud Solution Provider (CSP) di amministrare e segnalare facilmente le impostazioni di locazione dei clienti che non sono disponibili nell'interfaccia di amministrazione di Microsoft 365. Tenere presente che le autorizzazioni Amministra per conto terzi (AOBO, Administer On Behalf Of) sono necessarie all'account amministratore del partner per connettersi ai tenancy dei clienti.
  
I partner di autorizzazione accesso delegato (DAP, Delegated Access Permission) sono partner di Syndication e Cloud Solution Provider (CSP). Di solito, rappresentano fornitori di rete o telecomunicazioni di altre aziende. Essi bundle Microsoft 365 abbonamenti nelle loro offerte di servizi ai propri clienti. Quando vendono un abbonamento a Microsoft 365, vengono concesse automaticamente amministra per conto di (AOBO) le autorizzazioni per il cliente locazione in modo che possano amministrare e segnalare sul locazione cliente.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Che cosa è necessario sapere prima di iniziare

The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).
  
Sono necessarie anche le credenziali di amministratore tenant del partner.
  
## <a name="what-do-you-want-to-do"></a>Operazione desiderata

### <a name="list-all-tenant-ids"></a>Elencare tutti gli ID tenant

> [!NOTE]
> If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.
  
Per elencare tutti gli ID tenant dei clienti ai quali si ha accesso, eseguire questo comando.
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

In questo modo verrà visualizzato un elenco di tutti i tenant dei clienti tramite **TenantId**.

>[!Note]
>PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per Windows PowerShell e i cmdlet con **MSOL** all'interno del nome. Per continuare a usare i cmdlet, è necessario eseguirli in Windows PowerShell.
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>Ottenere un ID tenant tramite il nome di dominio

To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>Elencare tutti i domini per un tenant

To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

Se sono stati registrati ulteriori domini, verranno restituiti tutti i domini associati al **TenantId** del cliente.
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>Ottenere un mapping di tutti i tenant e i domini registrati

The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all. This command generates a listing of all your customer tenant IDs and their domains.
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>Ottenere tutti gli utenti per un tenant

This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>Ottenere tutti i dettagli di un utente

If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>Aggiungere utenti, impostare opzioni e assegnare licenze

La creazione in blocco, la configurazione e la gestione delle licenze degli utenti di Microsoft 365 sono particolarmente efficienti utilizzando Windows PowerShell per Office 365. In questa procedura di due passaggi, prima vengono create le voci per tutti gli utenti che si desidera aggiungere in un file CSV (con valori delimitati da virgole), per poi importare tale file usando Windows PowerShell per Office 365. 
  
#### <a name="create-a-csv-file"></a>Creare un file CSV

Creare un file CSV utilizzando questo formato:
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
dove:
  
- **UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR. 
    
- **LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.
    
#### <a name="import-the-csv-file-and-create-the-users"></a>Importare il file CSV e creare gli utenti

After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>Vedere anche

#### 

[Guida per partner](https://go.microsoft.com/fwlink/p/?LinkId=533477)

