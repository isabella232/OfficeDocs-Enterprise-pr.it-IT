---
title: Assegnare le licenze agli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: Informazioni su come utilizzare Office 365 PowerShell per assegnare una licenza di Office 365 a utenti senza licenza.
ms.openlocfilehash: ea2c889834c70095474fbc2957768746d92fe8cc
ms.sourcegitcommit: 9dfaeff7a1625a7325bb94f3eb322fc161ce066b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/18/2019
ms.locfileid: "40261339"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="d67d5-103">Assegnare le licenze agli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d67d5-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="d67d5-104">Gli utenti non possono utilizzare i servizi di Office 365 finché all'account non è stata assegnata una licenza da un piano di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="d67d5-104">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="d67d5-105">È possibile utilizzare Office 365 PowerShell per assegnare rapidamente le licenze agli account senza licenza.</span><span class="sxs-lookup"><span data-stu-id="d67d5-105">You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 

>[!Note]
><span data-ttu-id="d67d5-106">Gli account utente devono essere assegnati a un percorso.</span><span class="sxs-lookup"><span data-stu-id="d67d5-106">User accounts must be assigned a location.</span></span> <span data-ttu-id="d67d5-107">È possibile eseguire questa operazione dalle proprietà di un account utente nell'interfaccia di amministrazione di Microsoft 365 o da PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d67d5-107">You can do this from the properties of a user account in the Microsoft 365 admin center or from PowerShell.</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d67d5-108">Usare il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="d67d5-108">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d67d5-109">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="d67d5-109">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="d67d5-110">Successivamente, elencare i piani di licenza per il tenant con questo comando.</span><span class="sxs-lookup"><span data-stu-id="d67d5-110">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="d67d5-111">Successivamente, ottenere il nome di accesso dell'account a cui si desidera aggiungere una licenza, noto anche come nome dell'entità utente (UPN).</span><span class="sxs-lookup"><span data-stu-id="d67d5-111">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="d67d5-112">Successivamente, verificare che l'account utente disponga di una posizione di utilizzo assegnata.</span><span class="sxs-lookup"><span data-stu-id="d67d5-112">Next, ensure that the user account has a usage location assigned.</span></span>

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

<span data-ttu-id="d67d5-113">Se non è stata assegnata alcuna posizione di utilizzo, è possibile assegnarne una con questi comandi:</span><span class="sxs-lookup"><span data-stu-id="d67d5-113">If there is no usage location assigned, you can assign one with these commands:</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

<span data-ttu-id="d67d5-114">Infine, specificare il nome di accesso dell'utente e il nome del piano di licenza ed eseguire questi comandi.</span><span class="sxs-lookup"><span data-stu-id="d67d5-114">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d67d5-115">Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d67d5-115">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d67d5-116">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="d67d5-116">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="d67d5-117">Eseguire il `Get-MsolAccountSku` comando per visualizzare i piani di gestione delle licenze disponibili e il numero di licenze disponibili in ogni piano dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="d67d5-117">Run the `Get-MsolAccountSku` command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="d67d5-118">Il numero di licenze disponibili in ogni piano è **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span><span class="sxs-lookup"><span data-stu-id="d67d5-118">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="d67d5-119">Per ulteriori informazioni sui piani di licenza, le licenze e i servizi, vedere [View licences and Services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="d67d5-119">For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

>[!Note]
><span data-ttu-id="d67d5-120">PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per Windows PowerShell e i cmdlet con **MSOL** all'interno del nome.</span><span class="sxs-lookup"><span data-stu-id="d67d5-120">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="d67d5-121">Per continuare a usare i cmdlet, è necessario eseguirli in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d67d5-121">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="d67d5-122">Per trovare gli account senza licenza nell'organizzazione, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="d67d5-122">To find the unlicensed accounts in your organization, run this command.</span></span>

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="d67d5-123">È possibile assegnare licenze solo agli account utente con la proprietà **UsageLocation** impostata su un codice paese ISO 3166-1 Alpha-2 valido.</span><span class="sxs-lookup"><span data-stu-id="d67d5-123">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="d67d5-124">Ad esempio, US per gli Stati Uniti e FR per la Francia.</span><span class="sxs-lookup"><span data-stu-id="d67d5-124">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="d67d5-125">Alcuni servizi di Office 365 non sono disponibili in alcuni paesi.</span><span class="sxs-lookup"><span data-stu-id="d67d5-125">Some Office 365 services aren't available in certain countries.</span></span> <span data-ttu-id="d67d5-126">Per ulteriori informazioni, vedere [informazioni sulle restrizioni di licenza](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="d67d5-126">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="d67d5-127">Per trovare account che non dispongono di un valore **UsageLocation** , eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="d67d5-127">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="d67d5-128">Per impostare il valore **UsageLocation** su un account, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="d67d5-128">To set the **UsageLocation** value on an account, run this command.</span></span>

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="d67d5-129">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="d67d5-129">For example:</span></span>

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="d67d5-130">Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro **-All**, vengono restituiti solo i primi 500 account.</span><span class="sxs-lookup"><span data-stu-id="d67d5-130">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="d67d5-131">Assegnazione di licenze agli account utente</span><span class="sxs-lookup"><span data-stu-id="d67d5-131">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="d67d5-132">Per assegnare una licenza a un utente, utilizzare il seguente comando in Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d67d5-132">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="d67d5-133">In questo esempio viene assegnata una licenza dal piano di gestione delle licenze **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) all'utente non autorizzato **\@litwareinc.com**:</span><span class="sxs-lookup"><span data-stu-id="d67d5-133">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan\@litwareinc.com**:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="d67d5-134">Per assegnare una licenza a tutti gli utenti senza licenza, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="d67d5-134">To assign a license to all unlicensed users, run this command.</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
><span data-ttu-id="d67d5-135">Non è possibile assegnare più licenze a un utente dallo stesso piano di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="d67d5-135">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="d67d5-136">Se non si dispone di una quantità sufficiente di licenze disponibili, le licenze vengono assegnate agli utenti nell'ordine in cui vengono restituiti dal cmdlet **Get-MsolUser** finché non vengono esaurite le licenze disponibili.</span><span class="sxs-lookup"><span data-stu-id="d67d5-136">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="d67d5-137">In questo esempio vengono assegnate le licenze dal piano di gestione delle licenze **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) a tutti gli utenti senza licenza:</span><span class="sxs-lookup"><span data-stu-id="d67d5-137">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="d67d5-138">In questo esempio vengono assegnate le stesse licenze agli utenti senza licenza del reparto vendite negli Stati Uniti:</span><span class="sxs-lookup"><span data-stu-id="d67d5-138">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d67d5-139">Spostare un utente in una sottoscrizione diversa (piano di licenza) con il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="d67d5-139">Move a user to a different subscription (license plan) with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d67d5-140">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="d67d5-140">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="d67d5-141">Successivamente, ottenere il nome di accesso dell'account utente per il quale si desidera cambiare le sottoscrizioni, noto anche come nome dell'entità utente (UPN, User Principal Name).</span><span class="sxs-lookup"><span data-stu-id="d67d5-141">Next, get the sign-in name of the user account for which you want switch subscriptions, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="d67d5-142">Successivamente, elencare le sottoscrizioni (piani di licenza) per il tenant con questo comando.</span><span class="sxs-lookup"><span data-stu-id="d67d5-142">Next, list the subscriptions (license plans) for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="d67d5-143">Successivamente, elencare le sottoscrizioni che l'account utente ha attualmente con questi comandi.</span><span class="sxs-lookup"><span data-stu-id="d67d5-143">Next, list the subscriptions that the user account currently has with these commands.</span></span>

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

<span data-ttu-id="d67d5-144">Identificare la sottoscrizione che l'utente ha attualmente (la sottoscrizione da) e l'abbonamento a cui l'utente sta spostando (la sottoscrizione a).</span><span class="sxs-lookup"><span data-stu-id="d67d5-144">Identify the subscription the user currently has (the FROM subscription) and the subscription to which the user is moving (the TO subscription).</span></span>

<span data-ttu-id="d67d5-145">Infine, specificare i nomi delle sottoscrizioni da e verso (SKU Part Number) ed eseguire questi comandi.</span><span class="sxs-lookup"><span data-stu-id="d67d5-145">Finally, specify the TO and FROM subscription names (SKU part numbers) and run these commands.</span></span>

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$licenses.AddLicenses = @()
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

<span data-ttu-id="d67d5-146">È possibile verificare la modifica della sottoscrizione per l'account utente con questi comandi.</span><span class="sxs-lookup"><span data-stu-id="d67d5-146">You can verify the change in subscription for the user account with these commands.</span></span>

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a><span data-ttu-id="d67d5-147">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d67d5-147">See also</span></span>

[<span data-ttu-id="d67d5-148">Gestire gli account utente, le licenze e i gruppi con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d67d5-148">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="d67d5-149">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="d67d5-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d67d5-150">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="d67d5-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
