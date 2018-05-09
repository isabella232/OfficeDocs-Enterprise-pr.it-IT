---
title: Disabilitare l'accesso ai servizi durante l'assegnazione di licenze utente
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/07/2018
ms.audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Informazioni su come assegnare licenze ad account utente e disabilitare i piani di servizio specifici nello stesso momento usando PowerShell di Office 365.
ms.openlocfilehash: 7567d84490cdb3db7c149a51c4f2f04d39cad9ce
ms.sourcegitcommit: def3e311db9322e469753bac59ff03624349b140
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2018
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="01de6-103">Disabilitare l'accesso ai servizi durante l'assegnazione di licenze utente</span><span class="sxs-lookup"><span data-stu-id="01de6-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="01de6-104">**Sintesi**: Informazioni su come assegnare licenze ad account utente e disabilitare i piani di servizio specifici nello stesso momento usando PowerShell di Office 365.</span><span class="sxs-lookup"><span data-stu-id="01de6-104">**Summary:**  Learn how to assign licenses to user accounts and disable specific service plans at the same time using Office 365 PowerShell.</span></span>
  
<span data-ttu-id="01de6-p101">Le sottoscrizioni a Office 365 includono piani di servizio per i singoli servizi. Gli amministratori di Office 365 spesso devono disabilitare alcuni piani quando assegnano le licenze agli utenti. Con le istruzioni disponibili in questo articolo, è possibile assegnare una licenza di Office 365 durante la disabilitazione di piani di servizio specifici usando PowerShell per un singolo account utente o più account utente.</span><span class="sxs-lookup"><span data-stu-id="01de6-p101">Office 365 subscriptions come with service plans for individual services. Office 365 administrators often need to disable certain plans when assigning licenses to users. With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="01de6-108">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="01de6-108">Before you begin</span></span>

<span data-ttu-id="01de6-p102">Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="01de6-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a><span data-ttu-id="01de6-111">Raccogliere informazioni sulle sottoscrizioni e sui piani di servizi</span><span class="sxs-lookup"><span data-stu-id="01de6-111">Collect information about subscriptions and service plans</span></span>

<span data-ttu-id="01de6-112">Eseguire il comando per visualizzare le sottoscrizioni correnti:</span><span class="sxs-lookup"><span data-stu-id="01de6-112">Run this command to see your current subscriptions:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="01de6-113">Nella visualizzazione del comando  `Get-MsolAccountSku`:</span><span class="sxs-lookup"><span data-stu-id="01de6-113">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="01de6-p103">**AccountSkuId** è un abbonamento per l'organizzazione nel formato \<OrganizationName>:\<Subscription>. \<OrganizationName> è il valore fornito dall'utente al momento della registrazione in Office 365 ed è univoco per la propria organizzazione. Il valore \<Subscription> è per una sottoscrizione specifica. Ad esempio, per litwareinc:ENTERPRISEPACK, il nome dell'organizzazione è litwareinc e il nome della sottoscrizione è ENTERPRISEPACK (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="01de6-p103">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format. The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization. The \<Subscription> value is for a specific subscription. For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="01de6-118">**ActiveUnits** è il numero di licenze acquistate per la sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="01de6-118">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="01de6-119">**WarningUnits** è il numero di licenze in una sottoscrizione non rinnovata e che scadrà dopo il periodo di prova di 30 giorni.</span><span class="sxs-lookup"><span data-stu-id="01de6-119">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="01de6-120">**ConsumedUnits** è il numero di licenze assegnate agli utenti per la sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="01de6-120">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="01de6-p104">Tenere presente che AccountSkuId per la sottoscrizione di Office 365 contenente gli utenti a cui assegnare la licenza. Inoltre, assicurarsi che siano disponibili licenze sufficienti da assegnare (sottrarre **ConsumedUnits** da **ActiveUnits** ).</span><span class="sxs-lookup"><span data-stu-id="01de6-p104">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license. Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="01de6-123">Successivamente, eseguire il comando per visualizzare i dettagli relativi i piani di servizi di Office 365 che sono disponibili in tutte le sottoscrizioni:</span><span class="sxs-lookup"><span data-stu-id="01de6-123">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="01de6-124">Dalla visualizzazione di questo comando, stabilire quali piani di servizio si desidera disattivare quando si assegnano le licenze agli utenti.</span><span class="sxs-lookup"><span data-stu-id="01de6-124">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="01de6-125">Ecco un elenco parziale dei piani di servizio e i servizi di Office 365 corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="01de6-125">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>
  
|<span data-ttu-id="01de6-126">**Piano di servizio**</span><span class="sxs-lookup"><span data-stu-id="01de6-126">**Service plan**</span></span>|<span data-ttu-id="01de6-127">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="01de6-127">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="01de6-128">SWAY</span><span class="sxs-lookup"><span data-stu-id="01de6-128">SWAY</span></span>  <br/> |<span data-ttu-id="01de6-129">Sway</span><span class="sxs-lookup"><span data-stu-id="01de6-129">Sway</span></span>  <br/> |
|<span data-ttu-id="01de6-130">INTUNE_O365</span><span class="sxs-lookup"><span data-stu-id="01de6-130">INTUNE_O365</span></span>  <br/> |<span data-ttu-id="01de6-131">Gestione dispositivi mobili in Office 365</span><span class="sxs-lookup"><span data-stu-id="01de6-131">Mobile Device Management for Office 365</span></span>  <br/> |
|<span data-ttu-id="01de6-132">YAMMER_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="01de6-132">YAMMER_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="01de6-133">Yammer</span><span class="sxs-lookup"><span data-stu-id="01de6-133">Yammer</span></span>  <br/> |
|<span data-ttu-id="01de6-134">RMS_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="01de6-134">RMS_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="01de6-135">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="01de6-135">Azure Rights Management (RMS)</span></span>  <br/> |
|<span data-ttu-id="01de6-136">OFFICESUBSCRIPTION</span><span class="sxs-lookup"><span data-stu-id="01de6-136">OFFICESUBSCRIPTION</span></span>  <br/> |<span data-ttu-id="01de6-137">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="01de6-137">Office Professional Plus</span></span>  <br/> |
|<span data-ttu-id="01de6-138">MCOSTANDARD</span><span class="sxs-lookup"><span data-stu-id="01de6-138">MCOSTANDARD</span></span>  <br/> |<span data-ttu-id="01de6-139">Skype for Business online</span><span class="sxs-lookup"><span data-stu-id="01de6-139">Skype for Business Online</span></span>  <br/> |
|<span data-ttu-id="01de6-140">SHAREPOINTWAC</span><span class="sxs-lookup"><span data-stu-id="01de6-140">SHAREPOINTWAC</span></span>  <br/> |<span data-ttu-id="01de6-141">Office Online</span><span class="sxs-lookup"><span data-stu-id="01de6-141">Office Online</span></span>  <br/> |
|<span data-ttu-id="01de6-142">SHAREPOINTENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="01de6-142">SHAREPOINTENTERPRISE</span></span>  <br/> |<span data-ttu-id="01de6-143">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="01de6-143">SharePoint Online</span></span>  <br/> |
|<span data-ttu-id="01de6-144">EXCHANGE_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="01de6-144">EXCHANGE_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="01de6-145">Exchange Online, piano 2</span><span class="sxs-lookup"><span data-stu-id="01de6-145">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="01de6-146">Dopo aver creato AccountSkuId e i piani di servizio da disabilitare, è possibile assegnare licenze per un singolo utente o per più utenti.</span><span class="sxs-lookup"><span data-stu-id="01de6-146">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
## <a name="for-a-single-user"></a><span data-ttu-id="01de6-147">Per un utente singolo</span><span class="sxs-lookup"><span data-stu-id="01de6-147">For a single user</span></span>

<span data-ttu-id="01de6-p105">Per un singolo utente, immettere il nome dell'entità utente dell'account utente, AccountSkuId e l'elenco dei piani di servizio per disattivare e rimuovere il testo esplicativo e i caratteri \< e >. Successivamente, eseguire i comandi risultanti nel prompt dei comandi di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01de6-p105">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters. Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

<span data-ttu-id="01de6-150">Ecco un blocco di comando di esempio per l'account denominato belindan@contoso.com, per la licenza contoso:ENTERPRISEPACK e i piani di servizio da disabilitare sono RMS_S_ENTERPRISE, SWAY, INTUNE_O365 e YAMMER_ENTERPRISE:</span><span class="sxs-lookup"><span data-stu-id="01de6-150">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
```
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

## <a name="for-multiple-users"></a><span data-ttu-id="01de6-151">Per più utenti</span><span class="sxs-lookup"><span data-stu-id="01de6-151">For multiple users</span></span>

<span data-ttu-id="01de6-p106">Per eseguire questa attività di amministrazione per più utenti, creare un file CSV contenente i campi UserPrincipalName e UsageLocation. Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="01de6-p106">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="01de6-154">Successivamente, immettere il percorso dei file CSV di input e output, l'ID SKU dell'account e l'elenco dei piani di servizio da disabilitare, quindi eseguire i comandi risultanti nel prompt dei comandi di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01de6-154">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $AccountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="01de6-155">Blocco di comando di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="01de6-155">This PowerShell command block:</span></span>
  
- <span data-ttu-id="01de6-156">Visualizza il nome dell'entità utente di ogni utente.</span><span class="sxs-lookup"><span data-stu-id="01de6-156">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="01de6-157">Assegna licenze personalizzate a ogni utente.</span><span class="sxs-lookup"><span data-stu-id="01de6-157">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="01de6-158">Crea un file CSV con tutti gli utenti che sono stati elaborati e mostra il relativo stato della licenza.</span><span class="sxs-lookup"><span data-stu-id="01de6-158">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="01de6-159">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="01de6-159">See also</span></span>

[<span data-ttu-id="01de6-160">Disattivare l'accesso ai servizi con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="01de6-160">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="01de6-161">Disattivare l'accesso a Sway con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="01de6-161">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="01de6-162">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="01de6-162">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="01de6-163">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="01de6-163">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

