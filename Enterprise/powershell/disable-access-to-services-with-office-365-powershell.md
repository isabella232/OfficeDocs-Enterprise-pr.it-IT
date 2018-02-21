---
title: Disattivare l'accesso ai servizi con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Questo articolo viene illustrato come utilizzare Office 365 PowerShell per disabilitare l'accesso ai servizi di Office 365 per gli utenti dell'organizzazione.
ms.openlocfilehash: 61d92a1a0c55a381f10fedbb43403dd099fcb69b
ms.sourcegitcommit: 07416472be80566370c30631aff740177b37b24c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2018
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="446a8-103">Disattivare l'accesso ai servizi con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="446a8-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="446a8-104">**Riepilogo:** Questo articolo viene illustrato come utilizzare Office 365 PowerShell per disabilitare l'accesso ai servizi di Office 365 per gli utenti dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="446a8-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="446a8-p101">Quando un account Office 365 viene assegnato una licenza da un piano di licenze, servizi di Office 365 vengono resi disponibili per l'utente da tale licenza. Tuttavia, è possibile controllare i servizi di Office 365 che l'utente può accedere. Ad esempio, anche se la licenza consente l'accesso a SharePoint Online, è possibile disattivare l'accesso a esso. In realtà, è possibile utilizzare Office 365 PowerShell per disabilitare l'accesso a un numero qualsiasi di servizi per:</span><span class="sxs-lookup"><span data-stu-id="446a8-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>

- <span data-ttu-id="446a8-109">Un singolo account.</span><span class="sxs-lookup"><span data-stu-id="446a8-109">An individual account.</span></span>
    
- <span data-ttu-id="446a8-110">Un gruppo di account.</span><span class="sxs-lookup"><span data-stu-id="446a8-110">A group of accounts.</span></span>
    
- <span data-ttu-id="446a8-111">Tutti gli account nell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="446a8-111">All accounts in your organization.</span></span>
    
## <a name="before-you-begin"></a><span data-ttu-id="446a8-112">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="446a8-112">Before you begin</span></span>
<span data-ttu-id="446a8-113"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="446a8-113"></span></span>

- <span data-ttu-id="446a8-p102">Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="446a8-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="446a8-p103">Il cmdlet **Get-MsolAccountSku** per visualizzare i piani di gestione delle licenze disponibili e i servizi di Office 365 disponibili in questi piani. Per ulteriori informazioni, vedere [le licenze di visualizzazione e dei servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="446a8-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="446a8-118">Per visualizzare la prima e dopo i risultati delle procedure di questo argomento, vedere [visualizzare i dettagli di licenza e il servizio di account con Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="446a8-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="446a8-p104">È disponibile uno script di PowerShell che consente di automatizzare le procedure descritte in questo argomento. In particolare, lo script consente di visualizzare e disabilitare i servizi nella propria organizzazione Office 365, tra cui oscillazione. Per ulteriori informazioni, vedere [disattivare l'accesso a oscillazione con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="446a8-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="446a8-122">Se si utilizza il cmdlet **Get-MsolUser** senza utilizzare il parametro _All_ , vengono restituiti solo gli account 500 utente primo.</span><span class="sxs-lookup"><span data-stu-id="446a8-122">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>
    
## <a name="specific-office-365-services-for-specific-users-for-a-single-licensing-plan"></a><span data-ttu-id="446a8-123">Servizi specifici di Office 365 per utenti specifici per un singolo piano di licenze</span><span class="sxs-lookup"><span data-stu-id="446a8-123">Specific Office 365 services for specific users for a single licensing plan</span></span>
  
<span data-ttu-id="446a8-124">Per disabilitare un set specifico di servizi di Office 365 per gli utenti da un singolo piano di licenze, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="446a8-124">To disable a specific set of Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="446a8-125">Identificare i servizi indesiderati nel piano di licenze utilizzando la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="446a8-125">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="446a8-126">Nell'esempio seguente crea un oggetto **LicenseOptions** che consente di disabilitare i servizi Office Online e SharePoint Online nel piano di licenze denominato `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="446a8-126">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="446a8-127">Utilizzare l'oggetto **LicenseOptions** dal passaggio 1 in uno o più utenti.</span><span class="sxs-lookup"><span data-stu-id="446a8-127">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="446a8-128">Per creare un nuovo account con i servizi disabilitati, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="446a8-128">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="446a8-129">Nell'esempio seguente viene creato un nuovo account per Allie Bellew che consente di assegnare la licenza e di disabilitare i servizi descritti nel passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="446a8-129">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="446a8-130">Per ulteriori informazioni sulla creazione di account utente in Office 365 PowerShell, vedere [creare gli account utente con Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="446a8-130">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="446a8-131">Per disabilitare i servizi per un utente dotato di una licenza esistente, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="446a8-131">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="446a8-132">In questo esempio vengono disabilitati i servizi per l'utente BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="446a8-132">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="446a8-133">Per disabilitare i servizi descritti nel passaggio 1 per tutti gli utenti con licenza esistenti, specificare il nome del piano di Office 365 dalla visualizzazione del cmdlet **Get-MsolAccountSku** (ad esempio **litwareinc: enterprisepack**) e quindi eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="446a8-133">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="446a8-134">Per disabilitare i servizi per un gruppo di utenti esistenti, utilizzare uno dei metodi seguenti per identificare gli utenti:</span><span class="sxs-lookup"><span data-stu-id="446a8-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="446a8-135">**Filtrare gli account in base a un attributo account esistente** A tale scopo, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="446a8-135">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="446a8-136">Nell'esempio seguente consente di disabilitare i servizi per gli utenti del reparto vendite negli Stati Uniti.</span><span class="sxs-lookup"><span data-stu-id="446a8-136">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="446a8-137">**Utilizzare un elenco di account specifici** A tale scopo, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="446a8-137">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="446a8-138">Creare un file di testo contenente un account su ogni riga come riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="446a8-138">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    <span data-ttu-id="446a8-139">In questo esempio il file di testo è c:\\documenti\\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="446a8-139">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="446a8-140">Eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="446a8-140">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="446a8-141">Per disabilitare i servizi di Office 365 per gli utenti mentre sono assegnandoli a un piano di licenze, vedere [disabilitare l'accesso ai servizi durante l'assegnazione delle licenze utente](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="446a8-141">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
## <a name="specific-office-365-services-for-users-from-all-licensing-plans"></a><span data-ttu-id="446a8-142">Servizi di Office 365 specifici per gli utenti da tutti i piani di gestione delle licenze</span><span class="sxs-lookup"><span data-stu-id="446a8-142">Specific Office 365 services for users from all licensing plans</span></span>
  
<span data-ttu-id="446a8-143">Per disabilitare i servizi di Office 365 per gli utenti in tutti i piani di gestione delle licenze disponibili, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="446a8-143">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="446a8-144">Copiare e incollare lo script seguente nel Blocco note.</span><span class="sxs-lookup"><span data-stu-id="446a8-144">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="446a8-145">Personalizzare i valori seguenti per il proprio ambiente:</span><span class="sxs-lookup"><span data-stu-id="446a8-145">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="446a8-146">_<UndesirableService>_In questo esempio, utilizzeremo Office Online e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="446a8-146">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="446a8-147">_<Account>_In questo esempio, utilizzeremo belindan@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="446a8-147">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="446a8-148">Lo script personalizzato avrà l'aspetto seguente:</span><span class="sxs-lookup"><span data-stu-id="446a8-148">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="446a8-p105">Salvare lo script come `RemoveO365Services.ps1` in un percorso facile da trovare. In questo esempio, si verrà salvare il file in `C:\\O365 Scripts`.</span><span class="sxs-lookup"><span data-stu-id="446a8-p105">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in `C:\\O365 Scripts`.</span></span>
    
4. <span data-ttu-id="446a8-151">Eseguire lo script in Office 365 PowerShell utilizzando il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="446a8-151">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  & "C:\O365 Scripts\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="446a8-152">Per annullare gli effetti di una di queste procedure (vale a dire per abilitare di nuovo i servizi disattivati), eseguire di nuovo la procedura, ma utilizzare il valore `$null` per il parametro _DisabledPlans_ .</span><span class="sxs-lookup"><span data-stu-id="446a8-152">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="446a8-153">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="446a8-153">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)


## <a name="all-office-365-services-for-all-users-for-a-single-licensing-plan"></a><span data-ttu-id="446a8-154">Tutti i servizi di Office 365 per tutti gli utenti per un singolo piano di licenze</span><span class="sxs-lookup"><span data-stu-id="446a8-154">All Office 365 services for all users for a single licensing plan</span></span>
 
<span data-ttu-id="446a8-155">Per disabilitare tutti i servizi di Office 365 per tutti gli utenti in un piano di licenze specifico, specificare il nome del piano delle licenze per $acctSKU (ad esempio **litwareinc: enterprisepack**) e quindi eseguire questi comandi nella finestra di comando PowerShell:</span><span class="sxs-lookup"><span data-stu-id="446a8-155">To disable all Office 365 services for all users in a specific licensing plan, specify the licensing plan name for $acctSKU (such as **litwareinc:ENTERPRISEPACK**), and then run these commands in the PowerShell command window:</span></span>

```
$acctSKU="<AccountSkuId>"
$servicesList=(Get-MsolAccountSku | Select -ExpandProperty ServiceStatus).ServicePlan.ServiceName
$lo = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans $servicesList
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -ObjectID $_.ObjectID -LicenseOptions $lo}
```

## <a name="new-to-office-365"></a><span data-ttu-id="446a8-156">Nuovo utente di Office 365?</span><span class="sxs-lookup"><span data-stu-id="446a8-156">New to Office 365?</span></span>
<span data-ttu-id="446a8-157"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="446a8-157"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="446a8-158">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="446a8-158">See also</span></span>
<span data-ttu-id="446a8-159"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="446a8-159"></span></span>

<span data-ttu-id="446a8-160">Vedere i seguenti argomenti aggiuntivi sulla gestione degli utenti con Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="446a8-160">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="446a8-161">Eliminare e ripristinare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="446a8-161">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="446a8-162">Eliminare e ripristinare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="446a8-162">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="446a8-163">Bloccare gli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="446a8-163">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="446a8-164">Assegnare le licenze agli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="446a8-164">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="446a8-165">Creare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="446a8-165">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="446a8-166">Per ulteriori informazioni sui cmdlet utilizzati in questa procedura, vedere i seguenti argomenti:</span><span class="sxs-lookup"><span data-stu-id="446a8-166">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="446a8-167">Get-Content</span><span class="sxs-lookup"><span data-stu-id="446a8-167">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="446a8-168">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="446a8-168">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="446a8-169">Nuovo MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="446a8-169">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="446a8-170">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="446a8-170">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="446a8-171">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="446a8-171">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="446a8-172">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="446a8-172">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="446a8-173">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="446a8-173">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="446a8-174">Where-Object</span><span class="sxs-lookup"><span data-stu-id="446a8-174">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

