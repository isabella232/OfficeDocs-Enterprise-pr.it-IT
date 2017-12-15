---
title: Disattivare l'accesso ai servizi con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Viene illustrato come utilizzare Office 365 PowerShell per aggiungere o rimuovere l'accesso ai servizi di Office 365 per gli utenti nell'organizzazione.
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="1856f-103">Disattivare l'accesso ai servizi con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="1856f-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="1856f-104">**Riepilogo:** Viene illustrato come utilizzare Office 365 PowerShell per aggiungere o rimuovere l'accesso ai servizi di Office 365 per gli utenti nell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="1856f-104">**Summary:** Explains how to use Office 365 PowerShell to add or remove access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="1856f-p101">Quando un account Office 365 viene assegnato una licenza da un piano di licenze, servizi di Office 365 vengono resi disponibili per l'utente da tale licenza. Tuttavia, è possibile controllare i servizi di Office 365 che l'utente può accedere. Ad esempio, anche se la licenza consente l'accesso a SharePoint Online, è possibile disattivare l'accesso a esso. In realtà, è possibile utilizzare Office 365 PowerShell per disabilitare l'accesso a un numero qualsiasi di servizi per:</span><span class="sxs-lookup"><span data-stu-id="1856f-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>
- <span data-ttu-id="1856f-109">Un singolo account.</span><span class="sxs-lookup"><span data-stu-id="1856f-109">An individual account.</span></span>
    
- <span data-ttu-id="1856f-110">Un gruppo di account.</span><span class="sxs-lookup"><span data-stu-id="1856f-110">A group of accounts.</span></span>
    
- <span data-ttu-id="1856f-111">Tutti gli account nell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="1856f-111">All accounts in your organization.</span></span>
    
 <span data-ttu-id="1856f-112">**Contenuto:** [La versione breve (istruzioni senza spiegazioni)](disable-access-to-services-with-office-365-powershell.md#ShortVersion) [Versione estesa (istruzioni con spiegazioni dettagliate)](disable-access-to-services-with-office-365-powershell.md#LongVersion) [Vedere anche](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span><span class="sxs-lookup"><span data-stu-id="1856f-112">**Contents:**[The short version (instructions without explanations)](disable-access-to-services-with-office-365-powershell.md#ShortVersion)[The long version (instructions with detailed explanations)](disable-access-to-services-with-office-365-powershell.md#LongVersion)[See also](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="1856f-113">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="1856f-113">Before you begin</span></span>
<span data-ttu-id="1856f-114"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="1856f-114"></span></span>

- <span data-ttu-id="1856f-p102">Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="1856f-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="1856f-p103">Il cmdlet **Get-MsolAccountSku** per visualizzare i piani di gestione delle licenze disponibili e i servizi di Office 365 disponibili in questi piani. Per ulteriori informazioni, vedere[le licenze di visualizzazione e dei servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="1856f-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see[View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="1856f-119">Per visualizzare la prima e dopo i risultati delle procedure di questo argomento, vedere [visualizzare i dettagli di licenza e il servizio di account con Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="1856f-119">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="1856f-p104">È disponibile uno script di PowerShell che consente di automatizzare le procedure descritte in questo argomento. In particolare, lo script consente di visualizzare e disabilitare i servizi nella propria organizzazione Office 365, tra cui oscillazione. Per ulteriori informazioni, vedere [disattivare l'accesso a oscillazione con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="1856f-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="1856f-123">Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro _All_, vengono restituiti solo i primi 500 account.</span><span class="sxs-lookup"><span data-stu-id="1856f-123">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="1856f-124">Versione breve (istruzioni senza spiegazioni)</span><span class="sxs-lookup"><span data-stu-id="1856f-124">The short version (instructions without explanations)</span></span>
<span data-ttu-id="1856f-125"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="1856f-125"></span></span>

<span data-ttu-id="1856f-p105">In questa sezione vengono illustrate le procedure in modo chiaro e senza informazioni superflue. Se si hanno altre domande o si desiderano ulteriori informazioni, è possibile leggere il resto dell'argomento.</span><span class="sxs-lookup"><span data-stu-id="1856f-p105">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="1856f-128">Per disabilitare i servizi di Office 365 per gli utenti da un singolo piano di licenze, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="1856f-128">To disable Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="1856f-129">Identificare i servizi indesiderati nel piano di licenze utilizzando la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="1856f-129">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="1856f-130">Questo esempio viene creato un oggetto **LicenseOptions** che consente di disabilitare i servizi Office Online e SharePoint Online nel piano di licenze denominato `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="1856f-130">This example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="1856f-131">Utilizzare l'oggetto **LicenseOptions** dal passaggio 1 in uno o più utenti.</span><span class="sxs-lookup"><span data-stu-id="1856f-131">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="1856f-132">Per creare un nuovo account con i servizi disabilitati, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="1856f-132">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="1856f-133">In questo esempio viene creato un nuovo account per Allie Bellew che consente di assegnare la licenza e disabilitare i servizi descritti nel passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="1856f-133">This example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="1856f-134">Per ulteriori informazioni sulla creazione di account utente in Office 365 PowerShell, vedere [creare gli account utente con Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="1856f-134">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="1856f-135">Per disabilitare i servizi per un utente dotato di una licenza esistente, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="1856f-135">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="1856f-136">In questo esempio vengono disabilitati i servizi per l'utente BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="1856f-136">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="1856f-137">Per disabilitare i servizi descritti nel passaggio 1 per tutti gli utenti con licenza esistenti, specificare il nome del piano di Office 365 dalla visualizzazione del cmdlet **Get-MsolAccountSku** (ad esempio **litwareinc: enterprisepack** ) e quindi eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="1856f-137">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - <span data-ttu-id="1856f-138">Per disabilitare i servizi per un gruppo di utenti esistenti, utilizzare uno dei metodi seguenti per identificare gli utenti:</span><span class="sxs-lookup"><span data-stu-id="1856f-138">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="1856f-139">**Filtrare gli account in base a un attributo account esistente** A tale scopo, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="1856f-139">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="1856f-140">In questo esempio vengono disabilitati i servizi per gli utenti nel reparto vendite degli Stati Uniti.</span><span class="sxs-lookup"><span data-stu-id="1856f-140">This example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="1856f-141">**Utilizzare un elenco di account specifici** A tale scopo, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="1856f-141">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="1856f-142">Creare un file di testo contenente un account su ogni riga come riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="1856f-142">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

    <span data-ttu-id="1856f-143">In questo esempio il file di testo è c:\\documenti\\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="1856f-143">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="1856f-144">Eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="1856f-144">Run the following command:</span></span>
    
  ```
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="1856f-145">Per disabilitare i servizi di Office 365 per gli utenti mentre sono assegnandoli a un piano di licenze, vedere [disabilitare l'accesso ai servizi durante l'assegnazione delle licenze utente](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="1856f-145">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
<span data-ttu-id="1856f-146">Per disabilitare i servizi di Office 365 per gli utenti in tutti i piani di gestione delle licenze disponibili, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="1856f-146">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="1856f-147">Copiare e incollare lo script seguente nel Blocco note.</span><span class="sxs-lookup"><span data-stu-id="1856f-147">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="1856f-148">Personalizzare i valori seguenti per il proprio ambiente:</span><span class="sxs-lookup"><span data-stu-id="1856f-148">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="1856f-149">_<UndesirableService>_In questo esempio, utilizzeremo Office Online e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="1856f-149">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="1856f-150">_<Account>_In questo esempio, utilizzeremo belindan@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="1856f-150">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="1856f-151">Lo script personalizzato avrà l'aspetto seguente:</span><span class="sxs-lookup"><span data-stu-id="1856f-151">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="1856f-p106">Salvare lo script come `RemoveO365Services.ps1` in un percorso facile da trovare. In questo esempio, si verrà salvare il file in " `C:\\O365 Scripts`".</span><span class="sxs-lookup"><span data-stu-id="1856f-p106">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in " `C:\\O365 Scripts`".</span></span>
    
4. <span data-ttu-id="1856f-154">Eseguire lo script in Office 365 PowerShell utilizzando il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="1856f-154">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="1856f-155">Per annullare gli effetti di una di queste procedure (vale a dire per abilitare di nuovo i servizi disattivati), eseguire di nuovo la procedura, ma utilizzare il valore `$null` per il parametro _DisabledPlans_ .</span><span class="sxs-lookup"><span data-stu-id="1856f-155">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value  `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="1856f-156">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="1856f-156">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="1856f-157">Versione estesa (istruzioni con spiegazioni dettagliate)</span><span class="sxs-lookup"><span data-stu-id="1856f-157">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="1856f-158"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="1856f-158"></span></span>

<span data-ttu-id="1856f-p107">Per impostazione predefinita, tutti i servizi vengono attivati quando si esegue una licenza tramite Office 365 PowerShell. E spesso che è un'ottima soluzione: ciò significa che è possibile in modo semplice e rapido assegnare licenze agli utenti senza dover specificare l'attivazione lungo il modo in cui ogni servizio.</span><span class="sxs-lookup"><span data-stu-id="1856f-p107">By default, all services are enabled when you issue a license by using Office 365 PowerShell. And often that's a good thing: that means that you can quickly and easily assign licenses to users without having to specify that each and every service be enabled along the way.</span></span>
  
<span data-ttu-id="1856f-p108">Detto che, tuttavia, è anche vero che si desidera limitare i servizi disponibili alcuni utenti; ad esempio, forse alcuni utenti devono disporre di accesso a Office Professional Plus, Skype per Business Online ed Exchange Online, ma gli stessi utenti non hanno accesso a SharePoint Online o in Office Online. È possibile limitare gli account in che modo? In realtà, è possibile. Per spiegare il funzionamento, è necessario un approccio in due passaggi per affrontare il problema:</span><span class="sxs-lookup"><span data-stu-id="1856f-p108">Having said that, however, it's also true that you might want to restrict the services available some of your users; for example, maybe some users should have access to Office Professional Plus, Skype for Business Online, and Exchange Online, but those same users shouldn't have access to SharePoint Online or to Office Online. Can you restrict accounts in that fashion? As it turns out, you can. To help explain how this works, let's take a two-step approach to tackling this problem:</span></span>
  
1. <span data-ttu-id="1856f-165">Assegna all'utente una licenza di Office 365 che attiva automaticamente tutti i servizi.</span><span class="sxs-lookup"><span data-stu-id="1856f-165">Assign the user an Office 365 license that automatically enables all the services.</span></span>
    
2. <span data-ttu-id="1856f-166">Esegui un paio di comandi di Office 365 PowerShell che disattivano servizi specifici per tale utente.</span><span class="sxs-lookup"><span data-stu-id="1856f-166">Run a pair of Office 365 PowerShell commands that disable specified services for that user.</span></span>
    
<span data-ttu-id="1856f-p109">È stata già inclusi nel file passaggio 1: il nostro utente (Belinda Newman) dispone di una licenza di Office 365 che lei consente di accedere a tutti i servizi di Office 365. Tuttavia, si desidera modificare l'account di Belinda in modo che l'utente non dispone dell'accesso a SharePoint Online ( `SHAREPOINTENTERPRISE`) o in Office Online ( `SHAREPOINTWAC`). Ma come stiamo è previsto?</span><span class="sxs-lookup"><span data-stu-id="1856f-p109">We've already taken care of step 1: our user (Belinda Newman) has an Office 365 license that provides her with access to all the Office 365 services. However, we want to modify Belinda's account so that she doesn't have access to SharePoint Online ( `SHAREPOINTENTERPRISE`) or to Office Online ( `SHAREPOINTWAC`). But how are we supposed to do that?</span></span>
  
<span data-ttu-id="1856f-p110">Ecco come. Per iniziare, dobbiamo utilizzare il cmdlet **New-MsolLicenseOptions** per creare un oggetto **LicenseOption** contenente i servizi in cui deve essere disabilitati. In caso di Belinda, si desidera disabilitare `SHAREPOINTENTERPRISE` e `SHAREPOINTWAC`, in modo che si utilizza questo comando:</span><span class="sxs-lookup"><span data-stu-id="1856f-p110">Here's how. To begin with, we're going to use the **New-MsolLicenseOptions** cmdlet to create a **LicenseOption** object that contains the services that we want disabled. In Belinda's case, we want to disable `SHAREPOINTENTERPRISE` and `SHAREPOINTWAC`, so we use this command:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="1856f-p111">Vedere come funziona? Si specifica il piano di licenze ( `litwareinc:ENTERPRISEPACK`) e indica ogni dei servizi da disabilitato, separando i servizi di con una virgola.</span><span class="sxs-lookup"><span data-stu-id="1856f-p111">See how that works? You specify the licensing plan ( `litwareinc:ENTERPRISEPACK`) and then indicate each of the services that you want disabled, separating those services by using commas.</span></span>
  
> [!NOTE]
> <span data-ttu-id="1856f-p112">Verificare che il nuovo oggetto **LicenseOption** sono archiviati in una variabile. Nell'esempio precedente è stato utilizzato `$x`, sebbene sia possibile utilizzare qualsiasi nome di variabile valido di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1856f-p112">Make sure you store your new **LicenseOption** object in a variable. In the preceding example, we used `$x`, although you can use any valid Windows PowerShell variable name.</span></span> 
  
<span data-ttu-id="1856f-177">A questo punto è possibile utilizzare il seguente comando per disabilitare l'accesso di Belinda per i due servizi:</span><span class="sxs-lookup"><span data-stu-id="1856f-177">At this point we can use the following command to disable Belinda's access to the two services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="1856f-p113">Nulla di complicato in questo caso, entrambi: è sufficiente chiamare il cmdlet **Set-MsolUserLicense** e includere il parametro _LicenseOptions_ , con la variabile ( `$x`) contenente i piani di cui si desidera disabilitare. E cosa è visualizzata ora se si analizzerà in informazioni sulla licenza di Belinda eseguendo il comando: `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? Viene visualizzato questo:</span><span class="sxs-lookup"><span data-stu-id="1856f-p113">Nothing too fancy here, either: we just call the **Set-MsolUserLicense** cmdlet and include the _LicenseOptions_ parameter, along with the variable ( `$x`) containing the plans we want to disable. And what do we see now if we take a peek at Belinda's license information by running the command:  `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? We see this:</span></span>
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

<span data-ttu-id="1856f-p114">Molto interessante, vero? E, naturalmente, è possibile eseguire la stessa operazione a più utenti se si desidera. Ad esempio, questi comandi disabilitino gli stessi due servizi tutti gli utenti con licenza. Specificare il nome del piano di Office 365 dalla visualizzazione del cmdlet **Get-MsolAccountSku** (ad esempio **litwareinc: enterprisepack** ) e quindi eseguire tali programmi.</span><span class="sxs-lookup"><span data-stu-id="1856f-p114">Pretty cool, huh? And, of course, we could do this same thing to multiple users if we wanted to. For example, these commands disable the same two services for all our licensed users. Specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run them.</span></span>
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

<span data-ttu-id="1856f-p115">Tenere presente che Belinda ancora disponga di una licenza di Office 365 valida; è sufficiente che ora che dispone dell'accesso ai servizi di un numero inferiore. Prima che è stato disabilitato i due servizi, Belinda disponeva newsfeed, OneDrive e SharePoint Online siti:</span><span class="sxs-lookup"><span data-stu-id="1856f-p115">Keep in mind that Belinda still has a valid Office 365 license; it's just that now she has access to fewer services. Before we disabled the two services, Belinda had access to newsfeeds, OneDrive, and SharePoint Online sites:</span></span>
  
![Utente con accesso a SharePoint.](images/o365_powershell_with_sharepoint.png)
  
<span data-ttu-id="1856f-188">Ora queste opzioni non sono più disponibili per lei:</span><span class="sxs-lookup"><span data-stu-id="1856f-188">Now those options are no longer available to her:</span></span>
  
![Utente senza accesso a SharePoint.](images/o365_powershell_without_sharepoint.png)
  
<span data-ttu-id="1856f-190">Questo è esattamente ciò che volevamo accadesse.</span><span class="sxs-lookup"><span data-stu-id="1856f-190">Which is exactly what we hoped would happen.</span></span>
  
<span data-ttu-id="1856f-p116">E se si modifica il presente in un secondo momento: è possibile abilitare di nuovo questi servizi? Ma certo. Per riattivare tutti i servizi per un utente, è sufficiente utilizzare questo comando per creare l'oggetto **LicenseOption** seguente:</span><span class="sxs-lookup"><span data-stu-id="1856f-p116">And what if we change our mind later on: is it possible to re-enable these services? You bet it is. To re-enable all the services for a user, just use this command to create the following **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="1856f-p117">Qual è il comando? Per iniziare con la costante di Windows PowerShell `$null` significa "nothing". (Oppure nel leggermente più tecnico Java significa "valore null.") Come si ricorderà, quando si utilizza il cmdlet **New-MsolLicenseOptions** è disponibile indicare i servizi che si desidera disattivata. In questo caso, non vogliamo che uno dei servizi da disabilitare. Che possono provocare a pensare che è possibile utilizzare un comando simile al seguente, un comando di cui non viene specificato un valore per il parametro _DisabledPlans_ :</span><span class="sxs-lookup"><span data-stu-id="1856f-p117">What does that command do? To begin with, the Windows PowerShell constant  `$null` means "nothing." (Or, in slightly-more technical language, it means a "null value.") As you recall, when we use the **New-MsolLicenseOptions** cmdlet we have to indicate the services that we want disabled. In this case, we don't want any of the services to be disabled. That might lead you to believe that we could use a command like the following, a command where we don't specify a value for the _DisabledPlans_ parameter:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

<span data-ttu-id="1856f-p118">Tuttavia, che non funzionano. Al contrario, verrà generato un messaggio di errore:</span><span class="sxs-lookup"><span data-stu-id="1856f-p118">However, that won't work. Instead, it generates an error message:</span></span>
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
<span data-ttu-id="1856f-201">Fortunatamente per noi, impostare il valore del parametro `$null` funziona:</span><span class="sxs-lookup"><span data-stu-id="1856f-201">Fortunately for us, setting the parameter value to  `$null` does work:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="1856f-202">Ciò significa semplicemente che, quando eseguiamo il cmdlet **Set-MsolUserLicense** , si stiamo dicendo a **Set-MsolUserLicense** che non vogliamo che venga disattivato alcun servizio per Belinda:</span><span class="sxs-lookup"><span data-stu-id="1856f-202">This simply means that, when we run the **Set-MsolUserLicense** cmdlet, we're telling **Set-MsolUserLicense** that we don't want Belinda to have any disabled services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="1856f-203">E, logicamente, se nessuno dei servizi viene disattivato significa che tutti i servizi sono attivati.</span><span class="sxs-lookup"><span data-stu-id="1856f-203">And, logically enough, if none of the services are disabled that must mean that all of the services are enabled.</span></span>
  
<span data-ttu-id="1856f-p119">Ora che comprendere come funziona tutto ciò, verrà illustrato come è possibile rilasciare una licenza e disattivare i servizi specificati e tutti con lo stesso comando. Che sembra molto importante, ma, in realtà, questa operazione è molto ad esso: è sufficiente includere sia _AddLicenses_ e _LicenseOptions_ parametri nello stesso comando. In altre parole, creare innanzitutto l'oggetto **LicenseOption** :</span><span class="sxs-lookup"><span data-stu-id="1856f-p119">Now that you understand how this all works, let's show you how you can issue a license and disable specified services, and all with the same command. That sounds pretty impressive, but, to be honest, there's really nothing to it: you just include both the  _AddLicenses_ and the _LicenseOptions_ parameters in the same command. In other words, you first create your **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="1856f-207">E, come detto in precedenza, si utilizza sia _AddLicenses_ e _LicenseOptions_ parametri nel comando:</span><span class="sxs-lookup"><span data-stu-id="1856f-207">And then, as noted previously, you use both the  _AddLicenses_ and the _LicenseOptions_ parameters in your command:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

<span data-ttu-id="1856f-208">Che comando invierà a Belinda Newman una nuova licenza, ma una licenza in cui Skype Business online ( `SHAREPOINTWAC`) e SharePoint Online ( `SHAREPOINTENTERPRISE`) sono entrambi disattivati.</span><span class="sxs-lookup"><span data-stu-id="1856f-208">That command will issue Belinda Newman a new license, but a license in which Skype for Business Online ( `SHAREPOINTWAC`) and SharePoint Online ( `SHAREPOINTENTERPRISE`) are both disabled.</span></span>
  
[<span data-ttu-id="1856f-209">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="1856f-209">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a><span data-ttu-id="1856f-210">Nuovo utente di Office 365?</span><span class="sxs-lookup"><span data-stu-id="1856f-210">New to Office 365?</span></span>
<span data-ttu-id="1856f-211"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="1856f-211"></span></span>

||
|:-----|
|<span data-ttu-id="1856f-p120">![L'icona breve di apprendimento LinkedIn](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New a Office 365?**         Scopri corsi video gratuiti per **i professionisti IT e gli amministratori di Office 365**, per offerto da Learning LinkedIn.</span><span class="sxs-lookup"><span data-stu-id="1856f-p120">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for **Office 365 admins and IT pros**, brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="1856f-214">See also</span><span class="sxs-lookup"><span data-stu-id="1856f-214">See also</span></span>
<span data-ttu-id="1856f-215"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="1856f-215"></span></span>

<span data-ttu-id="1856f-216">Vedere i seguenti argomenti aggiuntivi sulla gestione degli utenti con Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1856f-216">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="1856f-217">Eliminare e ripristinare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1856f-217">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="1856f-218">Eliminare e ripristinare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1856f-218">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="1856f-219">Bloccare gli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1856f-219">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="1856f-220">Assegnare le licenze agli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1856f-220">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="1856f-221">Creare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1856f-221">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="1856f-222">Per ulteriori informazioni sui cmdlet utilizzati in questa procedura, vedere i seguenti argomenti:</span><span class="sxs-lookup"><span data-stu-id="1856f-222">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="1856f-223">Get-Content</span><span class="sxs-lookup"><span data-stu-id="1856f-223">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="1856f-224">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="1856f-224">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="1856f-225">Nuovo MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="1856f-225">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="1856f-226">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="1856f-226">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="1856f-227">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="1856f-227">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="1856f-228">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="1856f-228">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="1856f-229">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="1856f-229">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="1856f-230">Where-Object</span><span class="sxs-lookup"><span data-stu-id="1856f-230">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
[<span data-ttu-id="1856f-231">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="1856f-231">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  

