---
title: Disattivare l'accesso ai servizi con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/28/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Utilizzare Office 365 PowerShell per disabilitare l'accesso ai servizi di Office 365 per gli utenti.
ms.openlocfilehash: 32c43a47e1547e85488cb5158bd7392d79c8a4fb
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/18/2019
ms.locfileid: "35781836"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="f54b2-103">Disattivare l'accesso ai servizi con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="f54b2-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="f54b2-104">**Riepilogo:** Viene illustrato come utilizzare Office 365 PowerShell per disabilitare l'accesso ai servizi di Office 365 per gli utenti dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="f54b2-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="f54b2-105">Quando a un account di Office 365 viene assegnata una licenza da un piano di gestione delle licenze, i servizi di Office 365 vengono resi disponibili all'utente dalla licenza.</span><span class="sxs-lookup"><span data-stu-id="f54b2-105">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license.</span></span> <span data-ttu-id="f54b2-106">Tuttavia, è possibile controllare i servizi di Office 365 che l'utente può accedere.</span><span class="sxs-lookup"><span data-stu-id="f54b2-106">However, you can control the Office 365 services that the user can access.</span></span> <span data-ttu-id="f54b2-107">Ad esempio, anche se la licenza consente l'accesso al servizio SharePoint Online, è possibile disabilitarne l'accesso.</span><span class="sxs-lookup"><span data-stu-id="f54b2-107">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="f54b2-108">È possibile utilizzare PowerShell per disabilitare l'accesso a qualsiasi numero di servizi per uno specifico piano di gestione delle licenze per:</span><span class="sxs-lookup"><span data-stu-id="f54b2-108">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="f54b2-109">Un singolo account.</span><span class="sxs-lookup"><span data-stu-id="f54b2-109">An individual account.</span></span>
    
- <span data-ttu-id="f54b2-110">Un gruppo di account.</span><span class="sxs-lookup"><span data-stu-id="f54b2-110">A group of accounts.</span></span>
    
- <span data-ttu-id="f54b2-111">Tutti gli account nell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="f54b2-111">All accounts in your organization.</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="f54b2-112">Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f54b2-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="f54b2-113">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="f54b2-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="f54b2-114">Successivamente, utilizzare questo comando per visualizzare i piani di licenza disponibili, noti anche come AccountSkuIds:</span><span class="sxs-lookup"><span data-stu-id="f54b2-114">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

<span data-ttu-id="f54b2-115">Per ulteriori informazioni, vedere [visualizzare le licenze e i servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="f54b2-115">For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="f54b2-116">Per visualizzare i risultati precedenti e successivi delle procedure descritte in questo argomento, vedere [View account License and Service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="f54b2-116">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="f54b2-117">Uno script PowerShell è disponibile per rendere automatiche le procedure descritte in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="f54b2-117">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="f54b2-118">Nello specifico, lo script consente di visualizzare e disabilitare i servizi nella propria organizzazione di Office 365, tra cui Sway.</span><span class="sxs-lookup"><span data-stu-id="f54b2-118">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="f54b2-119">Per ulteriori informazioni, vedere [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="f54b2-119">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="f54b2-120">Disabilitare servizi specifici di Office 365 per utenti specifici per uno specifico piano di gestione delle licenze</span><span class="sxs-lookup"><span data-stu-id="f54b2-120">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="f54b2-121">Per disabilitare un set specifico di servizi di Office 365 per gli utenti per uno specifico piano di gestione delle licenze, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f54b2-121">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="f54b2-122">Identificare i servizi indesiderati nel piano di gestione delle licenze utilizzando la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="f54b2-122">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

  <span data-ttu-id="f54b2-123">Nell'esempio seguente viene creato un oggetto **LicenseOptions** che Disabilita i servizi Office e SharePoint Online nel piano di gestione delle licenze `litwareinc:ENTERPRISEPACK` denominato (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="f54b2-123">The following example creates a **LicenseOptions** object that disables the Office and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="f54b2-124">Utilizzare l'oggetto **LicenseOptions** del passaggio 1 su uno o più utenti.</span><span class="sxs-lookup"><span data-stu-id="f54b2-124">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="f54b2-125">Per creare un nuovo account con i servizi disabilitati, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="f54b2-125">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

  <span data-ttu-id="f54b2-126">Nell'esempio seguente viene creato un nuovo account per Allie Bellew che assegna la licenza e Disabilita i servizi descritti nel passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="f54b2-126">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

  <span data-ttu-id="f54b2-127">Per ulteriori informazioni sulla creazione di account utente in Office 365 PowerShell, vedere [creare account utente con office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="f54b2-127">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="f54b2-128">Per disabilitare i servizi per un utente dotato di una licenza esistente, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="f54b2-128">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

  <span data-ttu-id="f54b2-129">In questo esempio vengono disabilitati i servizi per l'utente BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="f54b2-129">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="f54b2-130">Per disabilitare i servizi descritti nel passaggio 1 per tutti gli utenti con licenza esistenti, specificare il nome del piano di Office 365 dalla visualizzazione del cmdlet **Get-MsolAccountSku** (ad esempio **litwareinc: ENTERPRISEPACK**) e quindi eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="f54b2-130">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  <span data-ttu-id="f54b2-131">Se si utilizza il cmdlet **Get-MsolUser** senza utilizzare il parametro _All_ , vengono restituiti solo i primi account utente 500.</span><span class="sxs-lookup"><span data-stu-id="f54b2-131">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>


  - <span data-ttu-id="f54b2-132">Per disabilitare i servizi per un gruppo di utenti esistenti, utilizzare uno dei metodi seguenti per identificare gli utenti:</span><span class="sxs-lookup"><span data-stu-id="f54b2-132">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="f54b2-133">**Filtrare gli account in base a un attributo account esistente** A tale scopo, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="f54b2-133">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  <span data-ttu-id="f54b2-134">Nell'esempio seguente vengono disabilitati i servizi per gli utenti nel reparto vendite degli Stati Uniti.</span><span class="sxs-lookup"><span data-stu-id="f54b2-134">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="f54b2-135">**Utilizzare un elenco di account specifici** A tale scopo, eseguire la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="f54b2-135">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="f54b2-136">Creare un file di testo contenente un account su ogni riga come riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f54b2-136">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="f54b2-137">In questo esempio, il file di testo è C\\: My\\Documents. txt.</span><span class="sxs-lookup"><span data-stu-id="f54b2-137">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="f54b2-138">Eseguire il comando riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f54b2-138">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="f54b2-139">Se si desidera disabilitare l'accesso ai servizi per più piani di gestione delle licenze, ripetere le istruzioni sopra riportate per ogni piano di gestione delle licenze, garantendo che:</span><span class="sxs-lookup"><span data-stu-id="f54b2-139">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="f54b2-140">Agli account utente è stato assegnato il piano di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="f54b2-140">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="f54b2-141">I servizi da disabilitare sono disponibili nel piano di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="f54b2-141">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="f54b2-142">Per disabilitare i servizi di Office 365 per gli utenti mentre si assegnano a un piano di gestione delle licenze, vedere [disabilitare l'accesso ai servizi durante l'assegnazione di licenze utente](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="f54b2-142">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="f54b2-143">Nuovo utente di Office 365?</span><span class="sxs-lookup"><span data-stu-id="f54b2-143">New to Office 365?</span></span>
<span data-ttu-id="f54b2-144"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="f54b2-144"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="f54b2-145">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f54b2-145">See also</span></span>
<span data-ttu-id="f54b2-146"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="f54b2-146"></span></span>

<span data-ttu-id="f54b2-147">Vedere i seguenti argomenti aggiuntivi sulla gestione degli utenti con Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f54b2-147">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="f54b2-148">Eliminare e ripristinare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f54b2-148">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="f54b2-149">Eliminare e ripristinare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f54b2-149">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="f54b2-150">Bloccare gli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f54b2-150">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="f54b2-151">Assegnare le licenze agli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f54b2-151">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="f54b2-152">Creare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f54b2-152">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
