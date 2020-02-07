---
title: Disattivare l'accesso ai servizi con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Utilizzare Office 365 PowerShell per disabilitare l'accesso ai servizi di Office 365 per gli utenti.
ms.openlocfilehash: eb6099ce5a41d0ea0d09aba0b737be00912ffbdc
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841572"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="6c495-103">Disattivare l'accesso ai servizi con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="6c495-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="6c495-104">Quando a un account di Office 365 viene assegnata una licenza da un piano di gestione delle licenze, i servizi di Office 365 vengono resi disponibili all'utente dalla licenza.</span><span class="sxs-lookup"><span data-stu-id="6c495-104">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license.</span></span> <span data-ttu-id="6c495-105">Tuttavia, è possibile controllare i servizi di Office 365 che l'utente può accedere.</span><span class="sxs-lookup"><span data-stu-id="6c495-105">However, you can control the Office 365 services that the user can access.</span></span> <span data-ttu-id="6c495-106">Ad esempio, anche se la licenza consente l'accesso al servizio SharePoint Online, è possibile disabilitarne l'accesso.</span><span class="sxs-lookup"><span data-stu-id="6c495-106">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="6c495-107">È possibile utilizzare PowerShell per disabilitare l'accesso a qualsiasi numero di servizi per uno specifico piano di gestione delle licenze per:</span><span class="sxs-lookup"><span data-stu-id="6c495-107">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="6c495-108">Un singolo account.</span><span class="sxs-lookup"><span data-stu-id="6c495-108">An individual account.</span></span>
- <span data-ttu-id="6c495-109">Un gruppo di account.</span><span class="sxs-lookup"><span data-stu-id="6c495-109">A group of accounts.</span></span>
- <span data-ttu-id="6c495-110">Tutti gli account nell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="6c495-110">All accounts in your organization.</span></span>

>[!Note]
><span data-ttu-id="6c495-111">Vi sono dipendenze di servizio di Office 365 che possono impedire la disabilitazione di un servizio specificato quando altri servizi dipendono da esso.</span><span class="sxs-lookup"><span data-stu-id="6c495-111">There are Office 365 service dependencies that can prevent you from disabling a specified service when other services depend on it.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="6c495-112">Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6c495-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="6c495-113">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="6c495-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="6c495-114">Successivamente, utilizzare questo comando per visualizzare i piani di licenza disponibili, noti anche come AccountSkuIds:</span><span class="sxs-lookup"><span data-stu-id="6c495-114">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
><span data-ttu-id="6c495-115">PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per Windows PowerShell e i cmdlet con **MSOL** all'interno del nome.</span><span class="sxs-lookup"><span data-stu-id="6c495-115">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="6c495-116">Per continuare a usare i cmdlet, è necessario eseguirli in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6c495-116">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="6c495-117">Per ulteriori informazioni, vedere [visualizzare le licenze e i servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="6c495-117">For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="6c495-118">Per visualizzare i risultati precedenti e successivi delle procedure descritte in questo argomento, vedere [View account License and Service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="6c495-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="6c495-119">Uno script PowerShell è disponibile per rendere automatiche le procedure descritte in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="6c495-119">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="6c495-120">Nello specifico, lo script consente di visualizzare e disabilitare i servizi nella propria organizzazione di Office 365, tra cui Sway.</span><span class="sxs-lookup"><span data-stu-id="6c495-120">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="6c495-121">Per ulteriori informazioni, vedere [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="6c495-121">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="6c495-122">Disabilitare servizi specifici di Office 365 per utenti specifici per uno specifico piano di gestione delle licenze</span><span class="sxs-lookup"><span data-stu-id="6c495-122">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="6c495-123">Per disabilitare un set specifico di servizi di Office 365 per gli utenti per uno specifico piano di gestione delle licenze, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="6c495-123">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a><span data-ttu-id="6c495-124">Passaggio 1: identificare i servizi indesiderati nel piano di gestione delle licenze utilizzando la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="6c495-124">Step 1: Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

<span data-ttu-id="6c495-125">Nell'esempio seguente viene creato un oggetto **LicenseOptions** che Disabilita i servizi Office e SharePoint Online nel piano di gestione delle licenze `litwareinc:ENTERPRISEPACK` denominato (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="6c495-125">The following example creates a **LicenseOptions** object that disables the Office and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a><span data-ttu-id="6c495-126">Passaggio 2: utilizzare l'oggetto **LicenseOptions** del passaggio 1 su uno o più utenti.</span><span class="sxs-lookup"><span data-stu-id="6c495-126">Step 2: Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
<span data-ttu-id="6c495-127">Per creare un nuovo account con i servizi disabilitati, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="6c495-127">To create a new account that has the services disabled, use the following syntax:</span></span>
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

<span data-ttu-id="6c495-128">Nell'esempio seguente viene creato un nuovo account per Allie Bellew che assegna la licenza e Disabilita i servizi descritti nel passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="6c495-128">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

<span data-ttu-id="6c495-129">Per ulteriori informazioni sulla creazione di account utente in Office 365 PowerShell, vedere [creare account utente con office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="6c495-129">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="6c495-130">Per disabilitare i servizi per un utente dotato di una licenza esistente, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="6c495-130">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

<span data-ttu-id="6c495-131">In questo esempio vengono disabilitati i servizi per l'utente BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="6c495-131">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

<span data-ttu-id="6c495-132">Per disabilitare i servizi descritti nel passaggio 1 per tutti gli utenti con licenza esistenti, specificare il nome del piano di Office 365 dalla visualizzazione del cmdlet **Get-MsolAccountSku** (ad esempio **litwareinc: ENTERPRISEPACK**) e quindi eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="6c495-132">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 <span data-ttu-id="6c495-133">Se si utilizza il cmdlet **Get-MsolUser** senza utilizzare il parametro _All_ , vengono restituiti solo i primi account utente 500.</span><span class="sxs-lookup"><span data-stu-id="6c495-133">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>

<span data-ttu-id="6c495-134">Per disabilitare i servizi per un gruppo di utenti esistenti, utilizzare uno dei metodi seguenti per identificare gli utenti:</span><span class="sxs-lookup"><span data-stu-id="6c495-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
<span data-ttu-id="6c495-135">**Metodo 1. Filtrare gli account in base a un attributo account esistente**</span><span class="sxs-lookup"><span data-stu-id="6c495-135">**Method 1. Filter the accounts based on an existing account attribute**</span></span> 

<span data-ttu-id="6c495-136">A tal fine, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="6c495-136">To do this, use the following syntax:</span></span>
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="6c495-137">Nell'esempio seguente vengono disabilitati i servizi per gli utenti nel reparto vendite degli Stati Uniti.</span><span class="sxs-lookup"><span data-stu-id="6c495-137">The following example disables the services for users in the Sales department in the United States.</span></span>
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="6c495-138">**Metodo 2: utilizzare un elenco di account specifici**</span><span class="sxs-lookup"><span data-stu-id="6c495-138">**Method 2: Use a list of specific accounts**</span></span> 

<span data-ttu-id="6c495-139">A tal fine, procedere come segue:</span><span class="sxs-lookup"><span data-stu-id="6c495-139">To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="6c495-140">Creare un file di testo contenente un account su ogni riga come riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="6c495-140">Create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="6c495-141">In questo esempio, il file di testo è C\\: My\\Documents. txt.</span><span class="sxs-lookup"><span data-stu-id="6c495-141">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="6c495-142">Eseguire il comando riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="6c495-142">Run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="6c495-143">Se si desidera disabilitare l'accesso ai servizi per più piani di gestione delle licenze, ripetere le istruzioni sopra riportate per ogni piano di gestione delle licenze, garantendo che:</span><span class="sxs-lookup"><span data-stu-id="6c495-143">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="6c495-144">Agli account utente è stato assegnato il piano di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="6c495-144">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="6c495-145">I servizi da disabilitare sono disponibili nel piano di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="6c495-145">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="6c495-146">Per disabilitare i servizi di Office 365 per gli utenti mentre si assegnano a un piano di gestione delle licenze, vedere [disabilitare l'accesso ai servizi durante l'assegnazione di licenze utente](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="6c495-146">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="6c495-147">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6c495-147">See also</span></span>

[<span data-ttu-id="6c495-148">Gestire gli account utente, le licenze e i gruppi con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6c495-148">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="6c495-149">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="6c495-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="6c495-150">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="6c495-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
