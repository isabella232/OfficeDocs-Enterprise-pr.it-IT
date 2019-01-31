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
description: Questo articolo viene illustrato come utilizzare Office 365 PowerShell assegna una licenza di Office 365 per gli utenti senza licenza.
ms.openlocfilehash: ab9b66065e20d0c2d6cfb673dac24ee2ab79e831
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651181"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="69d3b-103">Assegnare le licenze agli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="69d3b-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="69d3b-104">**Riepilogo:**  Questo articolo viene illustrato come utilizzare Office 365 PowerShell assegna una licenza di Office 365 per gli utenti senza licenza.</span><span class="sxs-lookup"><span data-stu-id="69d3b-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="69d3b-p101">Gli utenti non possono utilizzare i servizi di Office 365 fino a quando il proprio account è stato assegnato una licenza da un piano di licenze. È possibile utilizzare Office 365 PowerShell rapidamente assegnare licenze agli account senza licenza.</span><span class="sxs-lookup"><span data-stu-id="69d3b-p101">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan. You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="69d3b-107">Usare il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="69d3b-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="69d3b-108">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="69d3b-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="69d3b-109">Successivamente, elencare i piani di licenza per il tenant con questo comando.</span><span class="sxs-lookup"><span data-stu-id="69d3b-109">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="69d3b-110">Successivamente, ottenere il nome di accesso dell'account che si desidera aggiungere una licenza, noto anche come il nome principale (UPN).</span><span class="sxs-lookup"><span data-stu-id="69d3b-110">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="69d3b-111">Infine, specificare il nome di accesso utente e il nome del piano di licenza ed eseguire questi comandi.</span><span class="sxs-lookup"><span data-stu-id="69d3b-111">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="69d3b-112">Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="69d3b-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="69d3b-113">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="69d3b-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="69d3b-p102">Eseguire il comando **Get-MsolAccountSku** per visualizzare i piani di gestione delle licenze disponibili e il numero di licenze disponibili in ogni piano all'interno dell'organizzazione. Il numero di licenze disponibili in ogni piano è **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Per ulteriori informazioni sulle licenze di piani, le licenze e servizi, vedere [le licenze di visualizzazione e dei servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="69d3b-p102">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="69d3b-117">Per trovare gli account senza licenza all'interno dell'organizzazione, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="69d3b-117">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
<span data-ttu-id="69d3b-p103">È possibile assegnare solo le licenze agli account utente che la proprietà **UsageLocation** è impostata su un valido ISO 3166-1 alpha-codice di paese 2. Ad esempio, ci per gli Stati Uniti e FR per Francia. Alcuni servizi di Office 365 non sono disponibili in alcune nazioni. Per ulteriori informazioni, vedere [About restrizioni relative alla licenza](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="69d3b-p103">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="69d3b-122">Per trovare gli account di cui non sono un valore **UsageLocation** , eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="69d3b-122">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="69d3b-123">Per impostare il valore **UsageLocation** su un account, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="69d3b-123">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="69d3b-124">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="69d3b-124">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="69d3b-125">Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro **-All**, vengono restituiti solo i primi 500 account.</span><span class="sxs-lookup"><span data-stu-id="69d3b-125">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="69d3b-126">Assegnazione delle licenze agli account utente</span><span class="sxs-lookup"><span data-stu-id="69d3b-126">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="69d3b-127">Per assegnare una licenza a un utente, utilizzare il seguente comando in Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69d3b-127">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="69d3b-128">Questo esempio viene assegnata una licenza dal **litwareinc: enterprisepack** (Office 365 Enterprise E3) licenze piano per l' utente senza licenza **belindan@litwareinc.com**:</span><span class="sxs-lookup"><span data-stu-id="69d3b-128">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="69d3b-129">Per assegnare una licenza a molti utenti senza licenza, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="69d3b-129">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | ForEach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```
  
>[!Note]
><span data-ttu-id="69d3b-p104">È possibile assegnare più licenze a un utente dal piano di licenze stesso. Se non è sufficiente licenze disponibili, le licenze vengono assegnate agli utenti nell'ordine in cui si sta restituiti dal cmdlet **Get-MsolUser** fino ad esaurimento le licenze disponibili.</span><span class="sxs-lookup"><span data-stu-id="69d3b-p104">You can't assign multiple licenses to a user from the same licensing plan. If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="69d3b-132">In questo esempio consente di assegnare licenze dal piano di licenze **litwareinc: enterprisepack** (Office 365 Enterprise E3) a tutti gli utenti senza licenza:</span><span class="sxs-lookup"><span data-stu-id="69d3b-132">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="69d3b-133">In questo esempio consente di assegnare licenze stesse agli utenti senza licenza del reparto vendite negli Stati Uniti:</span><span class="sxs-lookup"><span data-stu-id="69d3b-133">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="69d3b-134">Nuovo utente di Office 365?</span><span class="sxs-lookup"><span data-stu-id="69d3b-134">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="69d3b-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="69d3b-135">See also</span></span>

[<span data-ttu-id="69d3b-136">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="69d3b-136">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="69d3b-137">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="69d3b-137">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="69d3b-138">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="69d3b-138">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
