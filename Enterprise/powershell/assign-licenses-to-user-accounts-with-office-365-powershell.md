---
title: Assegnare le licenze agli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
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
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123293"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="48674-103">Assegnare le licenze agli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="48674-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="48674-104">**Riepilogo:**  Questo articolo viene illustrato come utilizzare Office 365 PowerShell assegna una licenza di Office 365 per gli utenti senza licenza.</span><span class="sxs-lookup"><span data-stu-id="48674-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="48674-p101">Gestione delle licenze gli account utente in Office 365 è importante in quanto gli utenti non possono utilizzare i servizi di Office 365 fino a quando non è stato concesso in licenza il proprio account. È possibile utilizzare Office 365 PowerShell in modo efficiente assegnare licenze agli account senza licenza, soprattutto più account.</span><span class="sxs-lookup"><span data-stu-id="48674-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="48674-107">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="48674-107">Before you begin</span></span>
<span data-ttu-id="48674-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="48674-108"></span></span>

- <span data-ttu-id="48674-p102">Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="48674-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="48674-p103">Utilizzare il cmdlet **Get-MsolAccountSku** per visualizzare i piani di gestione delle licenze disponibili e il numero di licenze disponibili in ogni piano all'interno dell'organizzazione. Il numero di licenze disponibili in ogni piano è **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Per ulteriori informazioni sulle licenze di piani, le licenze e servizi, vedere [le licenze di visualizzazione e dei servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="48674-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="48674-114">Per trovare gli account senza licenza all'interno dell'organizzazione, eseguire il comando`Get-MsolUser -All -UnlicensedUsersOnly`</span><span class="sxs-lookup"><span data-stu-id="48674-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="48674-p104">È possibile assegnare licenze solo per gli account utente con la proprietà **UsageLocation** impostata su un valido ISO 3166-1 alpha-codice di paese 2. Ad esempio, ci per gli Stati Uniti e FR per Francia. Alcuni servizi di Office 365 non sono disponibili in alcune nazioni. Per ulteriori informazioni, vedere [About restrizioni relative alla licenza](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="48674-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="48674-p105">Per trovare gli account di cui non sono un valore **UsageLocation** , eseguire il comando `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Per impostare il valore **UsageLocation** su un account, utilizzare la sintassi `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Ad esempio `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span><span class="sxs-lookup"><span data-stu-id="48674-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="48674-122">Se si utilizza il cmdlet **Get-MsolUser** senza utilizzare il `-All` parametro, vengono restituiti solo i primi 500 account.</span><span class="sxs-lookup"><span data-stu-id="48674-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>

## <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="48674-123">Assegnazione delle licenze agli account utente</span><span class="sxs-lookup"><span data-stu-id="48674-123">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="48674-124">Per assegnare una licenza a un utente, utilizzare la sintassi seguente in Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="48674-124">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="48674-125">Questo esempio viene assegnata una licenza per il `litwareinc:ENTERPRISEPACK` piano di licenze (Office 365 Enterprise E3) all'utente senza licenza `belindan@litwareinc.com`.</span><span class="sxs-lookup"><span data-stu-id="48674-125">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="48674-126">Per assegnare una licenza a più utenti privi di licenza, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="48674-126">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="48674-127">**Note**</span><span class="sxs-lookup"><span data-stu-id="48674-127">**Notes**</span></span>
  
- <span data-ttu-id="48674-128">Non è possibile assegnare più licenze a un utente dallo stesso piano di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="48674-128">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="48674-129">Se non si dispone di una quantità sufficiente di licenze disponibili, le licenze vengono assegnate agli utenti nell'ordine in cui vengono restituiti dal cmdlet **Get-MsolUser** finché non vengono esaurite le licenze disponibili.</span><span class="sxs-lookup"><span data-stu-id="48674-129">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="48674-130">In questo esempio consente di assegnare licenze dal `litwareinc:ENTERPRISEPACK` piano di licenze (Office 365 Enterprise E3) a tutti gli utenti senza licenza.</span><span class="sxs-lookup"><span data-stu-id="48674-130">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="48674-131">In questo esempio vengono assegnate le stesse licenze agli utenti senza licenza del reparto vendite negli Stati Uniti.</span><span class="sxs-lookup"><span data-stu-id="48674-131">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="48674-132">Nuovo utente di Office 365?</span><span class="sxs-lookup"><span data-stu-id="48674-132">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="48674-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="48674-133">See also</span></span>
<span data-ttu-id="48674-134"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="48674-134"></span></span>

<span data-ttu-id="48674-135">Vedere i seguenti argomenti aggiuntivi sulla gestione degli utenti con Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="48674-135">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="48674-136">Creare gli account utente</span><span class="sxs-lookup"><span data-stu-id="48674-136">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="48674-137">Eliminare e ripristinare gli account utente</span><span class="sxs-lookup"><span data-stu-id="48674-137">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="48674-138">Account utente di blocco</span><span class="sxs-lookup"><span data-stu-id="48674-138">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="48674-139">Rimuovere licenze dagli account utente</span><span class="sxs-lookup"><span data-stu-id="48674-139">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="48674-140">Per ulteriori informazioni sui cmdlet utilizzati in questa procedura, vedere i seguenti argomenti:</span><span class="sxs-lookup"><span data-stu-id="48674-140">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="48674-141">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="48674-141">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="48674-142">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="48674-142">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="48674-143">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="48674-143">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="48674-144">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="48674-144">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="48674-145">Select-Object</span><span class="sxs-lookup"><span data-stu-id="48674-145">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="48674-146">Where-Object</span><span class="sxs-lookup"><span data-stu-id="48674-146">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

