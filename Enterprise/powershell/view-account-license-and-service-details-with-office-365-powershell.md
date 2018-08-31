---
title: Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/27/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Questo articolo viene illustrato come utilizzare Office 365 PowerShell per determinare i servizi di Office 365 che sono stati assegnati agli utenti.
ms.openlocfilehash: 78608c3a52151c115eaf80b5315bb71b61e62356
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223108"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="81aa8-103">Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="81aa8-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="81aa8-104">**Riepilogo:** Questo articolo viene illustrato come utilizzare Office 365 PowerShell per determinare i servizi di Office 365 che sono stati assegnati agli utenti.</span><span class="sxs-lookup"><span data-stu-id="81aa8-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="81aa8-p101">In Office 365, concede in licenza da Gestione licenze piani (anche denominato SKU o Office 365 dei piani) è possibile accedere ai servizi definiti per i piani di Office 365. Tuttavia, un utente potrebbe non avere accesso a tutti i servizi disponibili in una licenza attualmente assegnati a loro. È possibile utilizzare Office 365 PowerShell per visualizzare lo stato dei servizi per gli account utente.</span><span class="sxs-lookup"><span data-stu-id="81aa8-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="81aa8-108">Informazioni preliminari</span><span class="sxs-lookup"><span data-stu-id="81aa8-108">Before you begin</span></span>

- <span data-ttu-id="81aa8-p102">Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="81aa8-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="81aa8-111">Utilizzare i comandi `Get-MsolAccountSku` e `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` per trovare le informazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="81aa8-111">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="81aa8-112">I piani di gestione delle licenze che sono disponibili nell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="81aa8-112">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="81aa8-113">I servizi che sono disponibili in ogni piano di gestione delle licenze e l'ordine in cui sono elencati (il numero di indice).</span><span class="sxs-lookup"><span data-stu-id="81aa8-113">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="81aa8-114">Per ulteriori informazioni sulle licenze di piani di licenza e servizi, vedere [le licenze di visualizzazione e dei servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="81aa8-114">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="81aa8-115">Utilizzare il comando `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` per individuare le licenze che sono assegnate a un utente e l'ordine in cui sono elencati (numero di indice).</span><span class="sxs-lookup"><span data-stu-id="81aa8-115">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="81aa8-116">Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro _All_, vengono restituiti solo i primi 500 account.</span><span class="sxs-lookup"><span data-stu-id="81aa8-116">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    

## <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="81aa8-117">Per visualizzare i servizi per un account utente</span><span class="sxs-lookup"><span data-stu-id="81aa8-117">To view services for a user account</span></span>

<span data-ttu-id="81aa8-118">Per visualizzare tutti i servizi di Office 365 che un utente ha accesso, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="81aa8-118">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="81aa8-p103">In questo esempio vengono illustrati i servizi al quale BelindaN@litwareinc.com l'utente dispone dell'accesso. Mostra i servizi associati a tutte le licenze che sono assegnate al suo account.</span><span class="sxs-lookup"><span data-stu-id="81aa8-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="81aa8-121">Questo esempio mostra i servizi ai quali l'utente BelindaN@litwareinc.com ha accesso dalla prima licenza assegnata al suo account (il numero di indice è 0).</span><span class="sxs-lookup"><span data-stu-id="81aa8-121">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="81aa8-122">Per trovare tutti gli utenti con licenza che sono stati abilitati o disabilitati per servizi specifici, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="81aa8-122">To find all the licensed users who have been enabled or not enabled for specific services, use the following syntax:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

<span data-ttu-id="81aa8-123">In questi esempi vengono usate le informazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="81aa8-123">These examples use the following information:</span></span>
  
- <span data-ttu-id="81aa8-124">La licenza che consente di accedere ai servizi di Office 365 che siamo interessati è la licenza prima che viene assegnata a tutti gli utenti (numero di indice è 0).</span><span class="sxs-lookup"><span data-stu-id="81aa8-124">The license that gives access to the Office 365 services that we're interested in is the first license that's assigned to all users (the index number is 0).</span></span>
    
- <span data-ttu-id="81aa8-p104">I servizi di Office 365 che siamo interessati sono Skype per Business Online ed Exchange Online. Per le licenze che sono associate il piano di licenze, Skype Business online è il servizio 6 elencato (5 è il numero di indice), ed Exchange Online è il servizio 9 elencati (il numero di indice è 8).</span><span class="sxs-lookup"><span data-stu-id="81aa8-p104">The Office 365 services that we're interested in are Skype for Business Online and Exchange Online. For the licenses that are associated with the licensing plan, Skype for Business Online is the 6th service listed (the index number is 5), and Exchange Online is the 9th service listed (the index number is 8).</span></span>
    
<span data-ttu-id="81aa8-127">Questo esempio vengono restituite tutte con licenza gli utenti abilitati per Skype per Business Online ed Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="81aa8-127">This example returns all licensed users who are enabled for Skype for Business Online and Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="81aa8-128">In questo esempio restituisce tutti gli utenti con licenza non abilitati per Skype Business Online o Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="81aa8-128">This example returns all licensed users who aren't enabled for Skype for Business Online or Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="81aa8-129">Per visualizzare tutti i servizi per un utente che è stato assegnato *più licenze*, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="81aa8-129">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="see-also"></a><span data-ttu-id="81aa8-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="81aa8-130">See also</span></span>

<span data-ttu-id="81aa8-131">Vedere i seguenti argomenti aggiuntivi sulla gestione degli utenti con Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="81aa8-131">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="81aa8-132">Creare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="81aa8-132">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="81aa8-133">Eliminare e ripristinare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="81aa8-133">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="81aa8-134">Bloccare gli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="81aa8-134">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="81aa8-135">Assegnare le licenze agli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="81aa8-135">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="81aa8-136">Rimuovere le licenze dagli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="81aa8-136">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="81aa8-137">Per ulteriori informazioni sui cmdlet utilizzati in questa procedura, vedere i seguenti argomenti:</span><span class="sxs-lookup"><span data-stu-id="81aa8-137">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="81aa8-138">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="81aa8-138">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="81aa8-139">Format-List</span><span class="sxs-lookup"><span data-stu-id="81aa8-139">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="81aa8-140">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="81aa8-140">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="81aa8-141">Select-Object</span><span class="sxs-lookup"><span data-stu-id="81aa8-141">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="81aa8-142">Where-Object</span><span class="sxs-lookup"><span data-stu-id="81aa8-142">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="81aa8-143">Nuovo utente di Office 365?</span><span class="sxs-lookup"><span data-stu-id="81aa8-143">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]