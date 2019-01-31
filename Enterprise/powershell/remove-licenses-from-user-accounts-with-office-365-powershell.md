---
title: Rimuovere le licenze dagli account utente con Office 365 PowerShell
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Viene illustrato come per rimuovere licenze di Office 365 che sono stati precedentemente assegnate agli utenti di Office 365 PowerShell.
ms.openlocfilehash: 5b5f4550a5fade7f95669ad455aebd5d5f7fbf34
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651220"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="d3a19-103">Rimuovere le licenze dagli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3a19-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="d3a19-104">**Riepilogo:** Viene illustrato come per rimuovere licenze di Office 365 che sono stati precedentemente assegnate agli utenti di Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d3a19-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d3a19-105">Usare il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="d3a19-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d3a19-106">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="d3a19-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="d3a19-107">Successivamente, elencare i piani di licenza per il tenant con questo comando.</span><span class="sxs-lookup"><span data-stu-id="d3a19-107">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="d3a19-108">Successivamente, ottenere il nome di accesso dell'account per cui si desidera rimuovere una licenza, noto anche come il nome principale (UPN).</span><span class="sxs-lookup"><span data-stu-id="d3a19-108">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="d3a19-109">Infine, specificare l'accesso e la licenza per pianificare i nomi utente, rimuovere i caratteri lt"e gt _" ed eseguire questi comandi.</span><span class="sxs-lookup"><span data-stu-id="d3a19-109">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d3a19-110">Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3a19-110">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d3a19-111">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="d3a19-111">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

   
<span data-ttu-id="d3a19-112">Per visualizzare le informazioni sulla licenza piano (**AccountSkuID** ) nella propria organizzazione, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="d3a19-112">To view the licensing plan (**AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="d3a19-113">Visualizzare le licenze e i servizi con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="d3a19-113">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="d3a19-114">Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3a19-114">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="d3a19-115">Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro _-All_, vengono restituiti solo i primi 500 account.</span><span class="sxs-lookup"><span data-stu-id="d3a19-115">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="d3a19-116">Rimozione di licenze dall'account utente</span><span class="sxs-lookup"><span data-stu-id="d3a19-116">Removing licenses from user accounts</span></span>

<span data-ttu-id="d3a19-117">Per rimuovere le licenze da un account utente esistente, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="d3a19-117">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="d3a19-118">In questo esempio viene rimossa la `litwareinc:ENTERPRISEPACK` licenza (Office 365 Enterprise E3) dall'account utente BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="d3a19-118">This example removes the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="d3a19-119">Per rimuovere le licenze da un gruppo di utenti con licenza esistenti, utilizzare uno dei metodi seguenti:</span><span class="sxs-lookup"><span data-stu-id="d3a19-119">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="d3a19-120">**Filtrare gli account in base a un attributo account esistente** A tale scopo, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="d3a19-120">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="d3a19-121">In questo esempio viene rimossa la `litwareinc:ENTERPRISEPACK` le licenze (Office 365 Enterprise E3) da tutti gli account per gli utenti del reparto vendite negli Stati Uniti.</span><span class="sxs-lookup"><span data-stu-id="d3a19-121">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="d3a19-122">**Utilizzare un elenco di account specifici** A tale scopo, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="d3a19-122">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="d3a19-123">Creare e salvare un file di testo contenente un account su ogni riga come riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="d3a19-123">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="d3a19-124">Utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="d3a19-124">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="d3a19-125">In questo esempio viene rimossa la `litwareinc:ENTERPRISEPACK` licenza (Office 365 Enterprise E3) gli account utente definito nel file C:\My Documents\Accounts.txt del testo.</span><span class="sxs-lookup"><span data-stu-id="d3a19-125">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="d3a19-126">Per rimuovere le licenze da tutti gli account utente esistenti, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="d3a19-126">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="d3a19-127">In questo esempio viene rimossa la `litwareinc:ENTERPRISEPACK` licenza (Office 365 Enterprise E3) da tutti i membri esistenti con contratto multilicenza gli account utente.</span><span class="sxs-lookup"><span data-stu-id="d3a19-127">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="d3a19-p101">Un altro modo per liberare una licenza è eliminando l'account utente. Per ulteriori informazioni, vedere [eliminare e ripristinare gli account utente con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="d3a19-p101">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d3a19-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d3a19-130">See also</span></span>

[<span data-ttu-id="d3a19-131">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3a19-131">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="d3a19-132">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="d3a19-132">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d3a19-133">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="d3a19-133">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

    
## <a name="new-to-office-365"></a><span data-ttu-id="d3a19-134">Nuovo utente di Office 365?</span><span class="sxs-lookup"><span data-stu-id="d3a19-134">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

