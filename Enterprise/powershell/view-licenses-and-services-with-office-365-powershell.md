---
title: Visualizzare le licenze e i servizi con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Viene illustrato come utilizzare Office 365 PowerShell per visualizzare informazioni sui piani di licenza, i servizi e le licenze disponibili nell'organizzazione di Office 365.
ms.openlocfilehash: 8ee2c834063ea80388662c1f36f4524715f98a58
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747455"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="498a1-103">Visualizzare le licenze e i servizi con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="498a1-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="498a1-104">Ogni sottoscrizione di Office 365 è costituita dai seguenti elementi:</span><span class="sxs-lookup"><span data-stu-id="498a1-104">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="498a1-105">**Piani di gestione delle licenze** Questi sono noti anche come piani di licenza o piani di Office 365.</span><span class="sxs-lookup"><span data-stu-id="498a1-105">**Licensing plans** These are also known as license plans or Office 365 plans.</span></span> <span data-ttu-id="498a1-106">I piani di gestione delle licenze definiscono i servizi di Office 365 che sono disponibili per gli utenti.</span><span class="sxs-lookup"><span data-stu-id="498a1-106">Licensing plans define the Office 365 services that are available to users.</span></span> <span data-ttu-id="498a1-107">La sottoscrizione di Office 365 potrebbe contenere più piani di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="498a1-107">Your Office 365 subscription may contain multiple licensing plans.</span></span> <span data-ttu-id="498a1-108">Un esempio di piano di gestione delle licenze sarebbe Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="498a1-108">An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="498a1-109">**Servizi offerti** Questi sono noti anche come piani di servizio.</span><span class="sxs-lookup"><span data-stu-id="498a1-109">**Services** These are also known as service plans.</span></span> <span data-ttu-id="498a1-110">I servizi sono i prodotti, le caratteristiche e le funzionalità di Office 365 disponibili in ogni piano di licenze, ad esempio Exchange Online e Office Professional Plus.</span><span class="sxs-lookup"><span data-stu-id="498a1-110">Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus.</span></span> <span data-ttu-id="498a1-111">Gli utenti possono disporre di più licenze tramite diversi piani di licenza che garantiscono l'accesso ai diversi servizi.</span><span class="sxs-lookup"><span data-stu-id="498a1-111">Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="498a1-112">**Licenze** Ogni piano di gestione delle licenze contiene il numero di licenze acquistate.</span><span class="sxs-lookup"><span data-stu-id="498a1-112">**Licenses** Each licensing plan contains the number of licenses that you purchased.</span></span> <span data-ttu-id="498a1-113">Assegnare licenze agli utenti in modo che possano usare i servizi di Office 365 definiti dal piano di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="498a1-113">You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan.</span></span> <span data-ttu-id="498a1-114">Ogni account utente richiede almeno una licenza da un piano di gestione delle licenze, in modo che possano accedere a Office 365 e utilizzare i servizi.</span><span class="sxs-lookup"><span data-stu-id="498a1-114">Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="498a1-115">È possibile utilizzare Office 365 PowerShell per visualizzare i dettagli sui piani di licenza, le licenze e i servizi disponibili nella propria organizzazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="498a1-115">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization.</span></span> <span data-ttu-id="498a1-116">Per ulteriori informazioni sui prodotti, le caratteristiche e i servizi disponibili in diverse sottoscrizioni di Office 365, vedere [office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span><span class="sxs-lookup"><span data-stu-id="498a1-116">For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="498a1-117">Usare il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="498a1-117">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="498a1-118">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="498a1-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="498a1-119">Per visualizzare informazioni di riepilogo sui piani di gestione delle licenze e sulle licenze disponibili per ogni piano, eseguire il comando riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="498a1-119">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="498a1-120">I risultati contengono le seguenti informazioni:</span><span class="sxs-lookup"><span data-stu-id="498a1-120">The results contain the following information:</span></span>
  
- <span data-ttu-id="498a1-121">**SkuPartNumber:** Visualizza i piani di gestione delle licenze disponibili per l'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="498a1-121">**SkuPartNumber:** Shows the available licensing plans for your organization.</span></span> <span data-ttu-id="498a1-122">Ad esempio, `ENTERPRISEPACK` è il nome del piano di licenza per Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="498a1-122">For example, `ENTERPRISEPACK` is the license plan name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="498a1-123">**Attivato:** Il numero di licenze acquistate per uno specifico piano di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="498a1-123">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="498a1-124">**ConsumedUnits:** Il numero di licenze assegnate agli utenti da uno specifico piano di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="498a1-124">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="498a1-125">Per visualizzare i dettagli relativi ai servizi di Office 365 disponibili in tutti i piani di licenza, è necessario innanzitutto visualizzare un elenco dei piani di licenza.</span><span class="sxs-lookup"><span data-stu-id="498a1-125">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="498a1-126">Successivamente, archiviare le informazioni relative ai piani di licenza in una variabile.</span><span class="sxs-lookup"><span data-stu-id="498a1-126">Next, store the license plans information in a variable.</span></span>

```powershell
$licenses = Get-AzureADSubscribedSku
```

<span data-ttu-id="498a1-127">Successivamente, visualizzare i servizi in un piano di licenza specifico.</span><span class="sxs-lookup"><span data-stu-id="498a1-127">Next, display the services in a specific license plan.</span></span>

```powershell
$licenses[<index>].ServicePlans
```

<span data-ttu-id="498a1-128">\<index> è un valore integer che specifica il numero di riga del piano di licenza dalla visualizzazione del `Get-AzureADSubscribedSku | Select SkuPartNumber` comando (-1).</span><span class="sxs-lookup"><span data-stu-id="498a1-128">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="498a1-129">Ad esempio, se la visualizzazione del `Get-AzureADSubscribedSku | Select SkuPartNumber` comando è la seguente:</span><span class="sxs-lookup"><span data-stu-id="498a1-129">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

<span data-ttu-id="498a1-130">Successivamente, il comando per visualizzare i servizi per il piano di licenza di ENTERPRISEPREMIUM è il seguente:</span><span class="sxs-lookup"><span data-stu-id="498a1-130">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

```powershell
$licenses[2].ServicePlans
```

<span data-ttu-id="498a1-131">ENTERPRISEPREMIUM è la terza riga.</span><span class="sxs-lookup"><span data-stu-id="498a1-131">ENTERPRISEPREMIUM is the third row.</span></span> <span data-ttu-id="498a1-132">Pertanto, il valore di indice è (3-1) oppure 2.</span><span class="sxs-lookup"><span data-stu-id="498a1-132">Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="498a1-133">Per un elenco completo dei piani di licenza (noti anche come nomi di prodotto), per i piani di servizio inclusi e per i nomi descrittivi corrispondenti, vedere [nomi di prodotti e identificatori di piani di servizio per la gestione delle licenze](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="498a1-133">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="498a1-134">Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="498a1-134">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="498a1-135">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="498a1-135">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="498a1-136">Uno script PowerShell è disponibile per rendere automatiche le procedure descritte in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="498a1-136">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="498a1-137">Nello specifico, lo script consente di visualizzare e disabilitare i servizi nella propria organizzazione di Office 365, tra cui Sway.</span><span class="sxs-lookup"><span data-stu-id="498a1-137">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="498a1-138">Per ulteriori informazioni, vedere [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="498a1-138">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="498a1-139">Per visualizzare informazioni di riepilogo sui piani di gestione delle licenze e sulle licenze disponibili per ogni piano, eseguire il comando riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="498a1-139">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku
```

<span data-ttu-id="498a1-140">I risultati contengono le seguenti informazioni:</span><span class="sxs-lookup"><span data-stu-id="498a1-140">The results contain the following information:</span></span>
  
- <span data-ttu-id="498a1-141">**AccountSkuId:** Visualizzare i piani di gestione delle licenze disponibili per l'organizzazione utilizzando `<CompanyName>:<LicensingPlan>`la sintassi.</span><span class="sxs-lookup"><span data-stu-id="498a1-141">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.</span></span>  <span data-ttu-id="498a1-142">_<CompanyName>_ è il valore specificato quando si è registrato in Office 365 ed è univoco per l'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="498a1-142">_<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization.</span></span> <span data-ttu-id="498a1-143">Il _<LicensingPlan>_ valore è lo stesso per tutti.</span><span class="sxs-lookup"><span data-stu-id="498a1-143">The _<LicensingPlan>_ value is the same for everyone.</span></span> <span data-ttu-id="498a1-144">Ad esempio, nel valore `litwareinc:ENTERPRISEPACK`, il nome della società è `litwareinc`e il nome `ENTERPRISEPACK`del piano di gestione delle licenze, che è il nome di sistema per Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="498a1-144">For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="498a1-145">**ActiveUnits:** Il numero di licenze acquistate per uno specifico piano di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="498a1-145">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="498a1-146">**WarningUnits:** Il numero di licenze in un piano di gestione delle licenze che non sono state rinnovate e che scadranno dopo il periodo di tolleranza di 30 giorni.</span><span class="sxs-lookup"><span data-stu-id="498a1-146">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="498a1-147">**ConsumedUnits:** Il numero di licenze assegnate agli utenti da uno specifico piano di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="498a1-147">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="498a1-148">Per visualizzare i dettagli relativi ai servizi di Office 365 disponibili in tutti i piani di licenza, eseguire il comando riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="498a1-148">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="498a1-149">Nella tabella seguente vengono illustrati i piani di servizio di Office 365 e i relativi nomi descrittivi per i servizi più comuni.</span><span class="sxs-lookup"><span data-stu-id="498a1-149">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="498a1-150">L'elenco dei piani di servizio degli utenti potrebbe essere diverso.</span><span class="sxs-lookup"><span data-stu-id="498a1-150">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="498a1-151">**Piano di servizio**</span><span class="sxs-lookup"><span data-stu-id="498a1-151">**Service plan**</span></span>|<span data-ttu-id="498a1-152">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="498a1-152">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="498a1-153">Sway</span><span class="sxs-lookup"><span data-stu-id="498a1-153">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="498a1-154">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="498a1-154">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="498a1-155">Yammer</span><span class="sxs-lookup"><span data-stu-id="498a1-155">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="498a1-156">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="498a1-156">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="498a1-157">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="498a1-157">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="498a1-158">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="498a1-158">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="498a1-159">Ufficio</span><span class="sxs-lookup"><span data-stu-id="498a1-159">Office</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="498a1-160">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="498a1-160">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="498a1-161">Exchange Online, piano 2</span><span class="sxs-lookup"><span data-stu-id="498a1-161">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="498a1-162">Per un elenco completo dei piani di licenza (noti anche come nomi di prodotto), per i piani di servizio inclusi e per i nomi descrittivi corrispondenti, vedere [nomi di prodotti e identificatori di piani di servizio per la gestione delle licenze](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="498a1-162">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="498a1-163">Per visualizzare i dettagli sui servizi di Office 365 disponibili in uno specifico piano di gestione delle licenze, utilizzare la seguente sintassi.</span><span class="sxs-lookup"><span data-stu-id="498a1-163">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="498a1-164">In questo esempio vengono illustrati i servizi di Office 365 disponibili nel piano di gestione delle licenze litwareinc: ENTERPRISEPACK (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="498a1-164">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a><span data-ttu-id="498a1-165">Nuovo utente di Office 365?</span><span class="sxs-lookup"><span data-stu-id="498a1-165">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="498a1-166">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="498a1-166">See also</span></span>

[<span data-ttu-id="498a1-167">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="498a1-167">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="498a1-168">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="498a1-168">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="498a1-169">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="498a1-169">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
