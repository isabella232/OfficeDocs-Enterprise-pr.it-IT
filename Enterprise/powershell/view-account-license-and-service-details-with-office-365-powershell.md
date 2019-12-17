---
title: Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Viene illustrato come utilizzare Office 365 PowerShell per determinare i servizi di Office 365 assegnati agli utenti.
ms.openlocfilehash: 08e44476ea746b7e8298355e3adc5d0401261acd
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072288"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="98e30-103">Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="98e30-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="98e30-104">In Office 365, le licenze provenienti da piani di licenza (denominati anche SKU o piani di Office 365) offrono agli utenti l'accesso ai servizi di Office 365 definiti per tali piani.</span><span class="sxs-lookup"><span data-stu-id="98e30-104">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans.</span></span> <span data-ttu-id="98e30-105">Tuttavia, un utente potrebbe non avere accesso a tutti i servizi disponibili in una licenza che gli è attualmente assegnata.</span><span class="sxs-lookup"><span data-stu-id="98e30-105">However, a user might not have access to all the services that are available in a license that's currently assigned to them.</span></span> <span data-ttu-id="98e30-106">È possibile utilizzare Office 365 PowerShell per visualizzare lo stato dei servizi negli account utente.</span><span class="sxs-lookup"><span data-stu-id="98e30-106">You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

<span data-ttu-id="98e30-107">Per ulteriori informazioni sui piani di licenza, la licenza e i servizi, vedere [View licences and Services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="98e30-107">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="98e30-108">Usare il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="98e30-108">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="98e30-109">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="98e30-109">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="98e30-110">Successivamente, elencare i piani di licenza per il tenant con questo comando.</span><span class="sxs-lookup"><span data-stu-id="98e30-110">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="98e30-111">Utilizzare questi comandi per elencare i servizi disponibili in ogni piano di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="98e30-111">Use these commands to list the services that are available in each licensing plan.</span></span>

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

<span data-ttu-id="98e30-112">Utilizzare questi comandi per elencare le licenze assegnate a un account utente.</span><span class="sxs-lookup"><span data-stu-id="98e30-112">Use these commands to list the licenses that are assigned to a user account.</span></span>

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="98e30-113">Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="98e30-113">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="98e30-114">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="98e30-114">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="98e30-115">Successivamente, eseguire il comando seguente per elencare i piani di gestione delle licenze disponibili nell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="98e30-115">Next, run this command to list the licensing plans that are available in your organization.</span></span> 

```powershell
Get-MsolAccountSku
```
>[!Note]
><span data-ttu-id="98e30-116">PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per Windows PowerShell e i cmdlet con **MSOL** all'interno del nome.</span><span class="sxs-lookup"><span data-stu-id="98e30-116">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="98e30-117">Per continuare a usare i cmdlet, è necessario eseguirli in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="98e30-117">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="98e30-118">Successivamente, eseguire il comando seguente per elencare i servizi disponibili in ogni piano di licenze e l'ordine in cui sono elencati (il numero di indice).</span><span class="sxs-lookup"><span data-stu-id="98e30-118">Next, run this command to list the services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus
```
  
<span data-ttu-id="98e30-119">Utilizzare questo comando per elencare le licenze assegnate a un utente e l'ordine in cui sono elencate (il numero di indice).</span><span class="sxs-lookup"><span data-stu-id="98e30-119">Use this command to list the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

>[!Note]
><span data-ttu-id="98e30-120">Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro _All_, vengono restituiti solo i primi 500 account.</span><span class="sxs-lookup"><span data-stu-id="98e30-120">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
>
   

### <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="98e30-121">Per visualizzare i servizi per un account utente</span><span class="sxs-lookup"><span data-stu-id="98e30-121">To view services for a user account</span></span>

<span data-ttu-id="98e30-122">Per visualizzare tutti i servizi di Office 365 a cui un utente ha accesso, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="98e30-122">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="98e30-123">In questo esempio vengono illustrati i servizi ai quali l'utente BelindaN@litwareinc.com ha accesso.</span><span class="sxs-lookup"><span data-stu-id="98e30-123">This example shows the services to which the user BelindaN@litwareinc.com has access.</span></span> <span data-ttu-id="98e30-124">Vengono indicati i servizi associati a tutte le licenze assegnate al suo account.</span><span class="sxs-lookup"><span data-stu-id="98e30-124">This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="98e30-125">Questo esempio mostra i servizi ai quali l'utente BelindaN@litwareinc.com ha accesso dalla prima licenza assegnata al suo account (il numero di indice è 0).</span><span class="sxs-lookup"><span data-stu-id="98e30-125">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="98e30-126">Per visualizzare tutti i servizi per un utente a cui sono state assegnate *più licenze*, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="98e30-126">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```powershell
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```
 
## <a name="see-also"></a><span data-ttu-id="98e30-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="98e30-127">See also</span></span>

[<span data-ttu-id="98e30-128">Gestire gli account utente, le licenze e i gruppi con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="98e30-128">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="98e30-129">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="98e30-129">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="98e30-130">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="98e30-130">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
