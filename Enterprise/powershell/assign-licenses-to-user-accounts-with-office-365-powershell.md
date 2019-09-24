---
title: Assegnare le licenze agli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/05/2019
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
ms.openlocfilehash: 4351feaa1dbe9d657ed8df54a74410991834ea5d
ms.sourcegitcommit: c16ab90d0b9902228ce4337f1c64900592936cce
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2019
ms.locfileid: "37108216"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="c5f2f-103">Assegnare le licenze agli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c5f2f-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="c5f2f-104">**Riepilogo:**  Informazioni su come utilizzare Office 365 PowerShell per assegnare una licenza di Office 365 a utenti senza licenza.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-104">**Summary:**  How to use Office 365 PowerShell to assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="c5f2f-105">Gli utenti non possono utilizzare i servizi di Office 365 finché all'account non è stata assegnata una licenza da un piano di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-105">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="c5f2f-106">È possibile utilizzare Office 365 PowerShell per assegnare rapidamente le licenze agli account senza licenza.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-106">You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 

>[!Note]
><span data-ttu-id="c5f2f-107">Gli account utente devono essere assegnati a un percorso.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-107">User accounts must be assigned a location.</span></span> <span data-ttu-id="c5f2f-108">È possibile eseguire questa operazione dalle proprietà di un account utente nell'interfaccia di amministrazione di Microsoft 365 o da PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-108">You can do this from the properties of a user account in the Microsoft 365 admin center or from PowerShell.</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="c5f2f-109">Usare il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="c5f2f-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="c5f2f-110">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="c5f2f-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="c5f2f-111">Successivamente, elencare i piani di licenza per il tenant con questo comando.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-111">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="c5f2f-112">Successivamente, ottenere il nome di accesso dell'account a cui si desidera aggiungere una licenza, noto anche come nome dell'entità utente (UPN).</span><span class="sxs-lookup"><span data-stu-id="c5f2f-112">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="c5f2f-113">Successivamente, verificare che l'account utente disponga di una posizione di utilizzo assegnata.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-113">Next, ensure that the user account has a usage location assigned.</span></span>

```
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

<span data-ttu-id="c5f2f-114">Se non è stata assegnata alcuna posizione di utilizzo, è possibile assegnarne una con questi comandi:</span><span class="sxs-lookup"><span data-stu-id="c5f2f-114">If there is no usage location assigned, you can assign one with these commands:</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

<span data-ttu-id="c5f2f-115">Infine, specificare il nome di accesso dell'utente e il nome del piano di licenza ed eseguire questi comandi.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-115">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="c5f2f-116">Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c5f2f-116">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="c5f2f-117">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="c5f2f-117">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="c5f2f-118">Eseguire il comando **Get-MsolAccountSku** per visualizzare i piani di gestione delle licenze disponibili e il numero di licenze disponibili in ogni piano dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-118">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="c5f2f-119">Il numero di licenze disponibili in ogni piano è **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-119">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="c5f2f-120">Per ulteriori informazioni sui piani di licenza, le licenze e i servizi, vedere [View licences and Services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="c5f2f-120">For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="c5f2f-121">Per trovare gli account senza licenza nell'organizzazione, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-121">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="c5f2f-122">È possibile assegnare licenze solo agli account utente con la proprietà **UsageLocation** impostata su un codice paese ISO 3166-1 Alpha-2 valido.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-122">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="c5f2f-123">Ad esempio, US per gli Stati Uniti e FR per la Francia.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-123">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="c5f2f-124">Alcuni servizi di Office 365 non sono disponibili in alcuni paesi.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-124">Some Office 365 services aren't available in certain countries.</span></span> <span data-ttu-id="c5f2f-125">Per ulteriori informazioni, vedere [informazioni sulle restrizioni di licenza](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="c5f2f-125">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="c5f2f-126">Per trovare account che non dispongono di un valore **UsageLocation** , eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-126">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="c5f2f-127">Per impostare il valore **UsageLocation** su un account, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-127">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="c5f2f-128">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="c5f2f-128">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="c5f2f-129">Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro **-All**, vengono restituiti solo i primi 500 account.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-129">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="c5f2f-130">Assegnazione di licenze agli account utente</span><span class="sxs-lookup"><span data-stu-id="c5f2f-130">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="c5f2f-131">Per assegnare una licenza a un utente, utilizzare il seguente comando in Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-131">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="c5f2f-132">In questo esempio viene assegnata una licenza dal piano di gestione delle licenze **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) all'utente non autorizzato **\@litwareinc.com**:</span><span class="sxs-lookup"><span data-stu-id="c5f2f-132">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan\@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="c5f2f-133">Per assegnare una licenza a molti utenti senza licenza, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-133">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
><span data-ttu-id="c5f2f-134">Non è possibile assegnare più licenze a un utente dallo stesso piano di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-134">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="c5f2f-135">Se non si dispone di una quantità sufficiente di licenze disponibili, le licenze vengono assegnate agli utenti nell'ordine in cui vengono restituiti dal cmdlet **Get-MsolUser** finché non vengono esaurite le licenze disponibili.</span><span class="sxs-lookup"><span data-stu-id="c5f2f-135">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="c5f2f-136">In questo esempio vengono assegnate le licenze dal piano di gestione delle licenze **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) a tutti gli utenti senza licenza:</span><span class="sxs-lookup"><span data-stu-id="c5f2f-136">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="c5f2f-137">In questo esempio vengono assegnate le stesse licenze agli utenti senza licenza del reparto vendite negli Stati Uniti:</span><span class="sxs-lookup"><span data-stu-id="c5f2f-137">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="c5f2f-138">Nuovo utente di Office 365?</span><span class="sxs-lookup"><span data-stu-id="c5f2f-138">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="c5f2f-139">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c5f2f-139">See also</span></span>

[<span data-ttu-id="c5f2f-140">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c5f2f-140">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="c5f2f-141">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="c5f2f-141">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c5f2f-142">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="c5f2f-142">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
