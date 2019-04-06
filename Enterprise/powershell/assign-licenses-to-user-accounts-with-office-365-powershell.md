---
title: Assegnare le licenze agli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/29/2019
ms.audience: Admin
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
description: Viene illustrato come utilizzare Office 365 PowerShell per assegnare una licenza di Office 365 agli utenti senza licenza.
ms.openlocfilehash: 5040249f29ac8390db5b2933fc04fb1d01f0af2c
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931765"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="a71c6-103">Assegnare le licenze agli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a71c6-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="a71c6-104">**Riepilogo:**  Viene illustrato come utilizzare Office 365 PowerShell per assegnare una licenza di Office 365 agli utenti senza licenza.</span><span class="sxs-lookup"><span data-stu-id="a71c6-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="a71c6-105">Gli utenti non possono utilizzare i servizi di Office 365 finché all'account non è stata assegnata una licenza da un piano di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="a71c6-105">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="a71c6-106">È possibile utilizzare Office 365 PowerShell per assegnare rapidamente le licenze agli account senza licenza.</span><span class="sxs-lookup"><span data-stu-id="a71c6-106">You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="a71c6-107">Usare il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="a71c6-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="a71c6-108">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="a71c6-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="a71c6-109">Successivamente, elencare i piani di licenza per il tenant con questo comando.</span><span class="sxs-lookup"><span data-stu-id="a71c6-109">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="a71c6-110">Successivamente, ottenere il nome di accesso dell'account a cui si desidera aggiungere una licenza, noto anche come nome dell'entità utente (UPN).</span><span class="sxs-lookup"><span data-stu-id="a71c6-110">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="a71c6-111">Infine, specificare il nome di accesso dell'utente e il nome del piano di licenza ed eseguire questi comandi.</span><span class="sxs-lookup"><span data-stu-id="a71c6-111">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="a71c6-112">Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a71c6-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="a71c6-113">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="a71c6-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="a71c6-114">Eseguire il comando **Get-MsolAccountSku** per visualizzare i piani di gestione delle licenze disponibili e il numero di licenze disponibili in ogni piano dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="a71c6-114">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="a71c6-115">Il numero di licenze disponibili in ogni piano è **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span><span class="sxs-lookup"><span data-stu-id="a71c6-115">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="a71c6-116">Per ulteriori informazioni sui piani di licenza, le licenze e i servizi, vedere [View licences and Services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="a71c6-116">For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="a71c6-117">Per trovare gli account senza licenza nell'organizzazione, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="a71c6-117">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
<span data-ttu-id="a71c6-118">È possibile assegnare licenze solo agli account utente con la proprietà **UsageLocation** impostata su un codice paese ISO 3166-1 Alpha-2 valido.</span><span class="sxs-lookup"><span data-stu-id="a71c6-118">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="a71c6-119">Ad esempio, US per gli Stati Uniti e FR per la Francia.</span><span class="sxs-lookup"><span data-stu-id="a71c6-119">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="a71c6-120">Alcuni servizi di Office 365 non sono disponibili in alcuni paesi.</span><span class="sxs-lookup"><span data-stu-id="a71c6-120">Some Office 365 services aren't available in certain countries.</span></span> <span data-ttu-id="a71c6-121">Per ulteriori informazioni, vedere [informazioni sulle restrizioni di licenza](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="a71c6-121">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="a71c6-122">Per trovare account che non dispongono di un valore **UsageLocation** , eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="a71c6-122">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="a71c6-123">Per impostare il valore **UsageLocation** su un account, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="a71c6-123">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="a71c6-124">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="a71c6-124">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="a71c6-125">Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro **-All**, vengono restituiti solo i primi 500 account.</span><span class="sxs-lookup"><span data-stu-id="a71c6-125">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="a71c6-126">Assegnazione di licenze agli account utente</span><span class="sxs-lookup"><span data-stu-id="a71c6-126">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="a71c6-127">Per assegnare una licenza a un utente, utilizzare il seguente comando in Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a71c6-127">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="a71c6-128">In questo esempio viene assegnata una licenza dal piano di gestione delle licenze **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) all'utente senza licenza **Belindan@litwareinc.com**:</span><span class="sxs-lookup"><span data-stu-id="a71c6-128">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="a71c6-129">Per assegnare una licenza a molti utenti senza licenza, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="a71c6-129">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | ForEach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```
  
>[!Note]
><span data-ttu-id="a71c6-130">Non è possibile assegnare più licenze a un utente dallo stesso piano di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="a71c6-130">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="a71c6-131">Se non si dispone di una quantità sufficiente di licenze disponibili, le licenze vengono assegnate agli utenti nell'ordine in cui vengono restituiti dal cmdlet **Get-MsolUser** finché non vengono esaurite le licenze disponibili.</span><span class="sxs-lookup"><span data-stu-id="a71c6-131">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="a71c6-132">In questo esempio vengono assegnate le licenze dal piano di gestione delle licenze **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) a tutti gli utenti senza licenza:</span><span class="sxs-lookup"><span data-stu-id="a71c6-132">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="a71c6-133">In questo esempio vengono assegnate le stesse licenze agli utenti senza licenza del reparto vendite negli Stati Uniti:</span><span class="sxs-lookup"><span data-stu-id="a71c6-133">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="a71c6-134">Nuovo utente di Office 365?</span><span class="sxs-lookup"><span data-stu-id="a71c6-134">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="a71c6-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a71c6-135">See also</span></span>

[<span data-ttu-id="a71c6-136">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a71c6-136">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="a71c6-137">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="a71c6-137">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="a71c6-138">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="a71c6-138">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
