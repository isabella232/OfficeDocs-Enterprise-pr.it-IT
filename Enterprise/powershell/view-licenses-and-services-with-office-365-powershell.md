---
title: Visualizzare le licenze e i servizi con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
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
description: Viene illustrato come utilizzare Office 365 PowerShell per visualizzare informazioni sulle licenze piani, servizi e le licenze disponibili nell'organizzazione Office 365.
ms.openlocfilehash: e4c4a0570cafd3d9cb775dd99c5f75da613715e3
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546537"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="ad5dd-103">Visualizzare le licenze e i servizi con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="ad5dd-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="ad5dd-104">**Riepilogo:** Viene illustrato come utilizzare Office 365 PowerShell per visualizzare informazioni sulle licenze piani, servizi e le licenze disponibili nell'organizzazione Office 365.</span><span class="sxs-lookup"><span data-stu-id="ad5dd-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="ad5dd-105">Ogni sottoscrizione a Office 365 sono disponibili i seguenti elementi:</span><span class="sxs-lookup"><span data-stu-id="ad5dd-105">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="ad5dd-p101">**Piani di gestione delle licenze** Vi sono detti anche piani di licenza o piani di Office 365. Piani di gestione delle licenze definiscano i servizi di Office 365 disponibili agli utenti. La sottoscrizione a Office 365 può contenere più piani di gestione delle licenze. Un piano di licenze di esempio è E3 Enterprise di Office 365.</span><span class="sxs-lookup"><span data-stu-id="ad5dd-p101">**Licensing plans** These are also known as license plans or Office 365 plans. Licensing plans define the Office 365 services that are available to users. Your Office 365 subscription may contain multiple licensing plans. An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="ad5dd-p102">**Servizi** Questi sono noti anche come piani di servizio. Servizi sono i prodotti Office 365, caratteristiche e funzionalità disponibili in ogni piano di licenze, ad esempio, Exchange Online e Office Professional Plus. Gli utenti possono avere più di licenze assegnate loro da diversi piani di gestione delle licenze cui concedono l'accesso a diversi servizi.</span><span class="sxs-lookup"><span data-stu-id="ad5dd-p102">**Services** These are also known as service plans. Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus. Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="ad5dd-p103">**Licenze** Ogni piano di licenze contiene il numero di licenze acquistate. Consigliabile assegnare licenze agli utenti in modo che utilizzino i servizi di Office 365 definiti per il piano di licenze. Ogni account utente deve disporre almeno una licenza da un piano di licenze affinché possano accedere a Office 365 e utilizzare i servizi.</span><span class="sxs-lookup"><span data-stu-id="ad5dd-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="ad5dd-p104">È possibile utilizzare Office 365 PowerShell per visualizzare i dettagli sui piani di gestione delle licenze disponibili, le licenze e servizi all'interno dell'organizzazione Office 365. Per ulteriori informazioni sui prodotti, funzionalità e i servizi disponibili in diverse sottoscrizioni a Office 365, vedere [Opzioni di pianificazione di Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span><span class="sxs-lookup"><span data-stu-id="ad5dd-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="ad5dd-118">Utilizzare grafico modulo di Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad5dd-118">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="ad5dd-119">Primo, [la connessione al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="ad5dd-119">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="ad5dd-120">Per visualizzare le informazioni di riepilogo sui piani di licenza correnti e le licenze disponibili per ciascun piano, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ad5dd-120">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="ad5dd-121">I risultati contengono le seguenti informazioni:</span><span class="sxs-lookup"><span data-stu-id="ad5dd-121">The results contain the following information:</span></span>
  
- <span data-ttu-id="ad5dd-122">**SkuPartNumber:** Mostra i piani di gestione delle licenze disponibili per l'organizzazione >, ad esempio `ENTERPRISEPACK` è il nome del sistema per Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="ad5dd-122">**SkuPartNumber:** Show the available licensing plans for your organization> For example, `ENTERPRISEPACK` is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="ad5dd-123">**Abilitato:** Numero di licenze acquistate per un piano di licenze specifico.</span><span class="sxs-lookup"><span data-stu-id="ad5dd-123">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="ad5dd-124">**ConsumedUnits:** Numero di licenze assegnate agli utenti di un piano di licenze specifico.</span><span class="sxs-lookup"><span data-stu-id="ad5dd-124">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="ad5dd-125">Per visualizzare informazioni dettagliate sui servizi Office 365 sono disponibili in tutti i piani di licenza, prima di visualizzare un elenco di piani di licenza.</span><span class="sxs-lookup"><span data-stu-id="ad5dd-125">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

<span data-ttu-id="ad5dd-126">Successivamente, memorizzare le informazioni di piani di licenza in una variabile.</span><span class="sxs-lookup"><span data-stu-id="ad5dd-126">Next, store the license plans information in a variable.</span></span>

````
$licenses = Get-AzureADSubscribedSku
````

<span data-ttu-id="ad5dd-127">Successivamente, visualizzare i servizi in un piano di licenza specifici.</span><span class="sxs-lookup"><span data-stu-id="ad5dd-127">Next, display the services in a specific license plan.</span></span>

````
$licenses[<index>].ServicePlan
````

<span data-ttu-id="ad5dd-128">\<indice > è un numero intero che specifica il numero della riga del piano di licenza dalla visualizzazione del `Get-AzureADSubscribedSku | Select SkuPartNumber` command meno 1.</span><span class="sxs-lookup"><span data-stu-id="ad5dd-128">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="ad5dd-129">Ad esempio, se la visualizzazione del `Get-AzureADSubscribedSku | Select SkuPartNumber` si tratta di comando:</span><span class="sxs-lookup"><span data-stu-id="ad5dd-129">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

<span data-ttu-id="ad5dd-130">Quindi il comando per visualizzare i servizi per il piano di licenza ENTERPRISEPREMIUM è la seguente:</span><span class="sxs-lookup"><span data-stu-id="ad5dd-130">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

````
$licenses[2].ServicePlan
````

<span data-ttu-id="ad5dd-p105">ENTERPRISEPREMIUM è la terza riga. Di conseguenza, il valore di indice è (3 - 1) o 2.</span><span class="sxs-lookup"><span data-stu-id="ad5dd-p105">ENTERPRISEPREMIUM is the third row. Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="ad5dd-133">Per un elenco completo dei piani di licenza (noto anche come i nomi dei prodotti), i piani di servizio inclusi e i rispettivi nomi descrittivi corrispondenti, vedere [i nomi di prodotti e gli identificatori di piano di servizio per la gestione delle licenze](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="ad5dd-133">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="ad5dd-134">Utilizzare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad5dd-134">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="ad5dd-135">Primo, [la connessione al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="ad5dd-135">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="ad5dd-p106">È disponibile uno script di PowerShell che consente di automatizzare le procedure descritte in questo argomento. In particolare, lo script consente di visualizzare e disabilitare i servizi nella propria organizzazione Office 365, tra cui oscillazione. Per ulteriori informazioni, vedere [disattivare l'accesso a oscillazione con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="ad5dd-p106">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script lets you view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="ad5dd-139">Per visualizzare le informazioni di riepilogo sui piani di licenza correnti e le licenze disponibili per ciascun piano, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ad5dd-139">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="ad5dd-140">I risultati contengono le seguenti informazioni:</span><span class="sxs-lookup"><span data-stu-id="ad5dd-140">The results contain the following information:</span></span>
  
- <span data-ttu-id="ad5dd-p107">**AccountSkuId:** Mostra i piani di gestione delle licenze disponibili per l'organizzazione utilizzando la sintassi `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ è il valore fornito al momento è registrato in Office 365 ed è univoco per l'organizzazione. Il _<LicensingPlan>_ valore è lo stesso per tutti gli utenti. Ad esempio, nel valore `litwareinc:ENTERPRISEPACK`, è il nome della società `litwareinc`e il nome del piano delle licenze `ENTERPRISEPACK`, ovvero il nome del sistema per Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="ad5dd-p107">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="ad5dd-145">**ActiveUnits:** Numero di licenze acquistate per un piano di licenze specifico.</span><span class="sxs-lookup"><span data-stu-id="ad5dd-145">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="ad5dd-146">**WarningUnits:** Numero di licenze di un piano di licenze che non sono rinnovato e che scadranno dopo il periodo di prova di 30 giorni.</span><span class="sxs-lookup"><span data-stu-id="ad5dd-146">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="ad5dd-147">**ConsumedUnits:** Numero di licenze assegnate agli utenti di un piano di licenze specifico.</span><span class="sxs-lookup"><span data-stu-id="ad5dd-147">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="ad5dd-148">Per visualizzare informazioni dettagliate sui servizi Office 365 sono disponibili in tutti i piani di licenza, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ad5dd-148">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="ad5dd-p108">Nella tabella seguente vengono illustrati i piani di servizio di Office 365 e i relativi nomi descrittivi per i servizi più comuni. Elenco di piani di servizio potrebbe essere diverso.</span><span class="sxs-lookup"><span data-stu-id="ad5dd-p108">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="ad5dd-151">**Piano di servizio**</span><span class="sxs-lookup"><span data-stu-id="ad5dd-151">**Service plan**</span></span>|<span data-ttu-id="ad5dd-152">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="ad5dd-152">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="ad5dd-153">Sway</span><span class="sxs-lookup"><span data-stu-id="ad5dd-153">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="ad5dd-154">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ad5dd-154">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="ad5dd-155">Yammer</span><span class="sxs-lookup"><span data-stu-id="ad5dd-155">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="ad5dd-156">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="ad5dd-156">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="ad5dd-157">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="ad5dd-157">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="ad5dd-158">Skype for Business online</span><span class="sxs-lookup"><span data-stu-id="ad5dd-158">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="ad5dd-159">Office Online</span><span class="sxs-lookup"><span data-stu-id="ad5dd-159">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="ad5dd-160">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ad5dd-160">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="ad5dd-161">Exchange Online, piano 2</span><span class="sxs-lookup"><span data-stu-id="ad5dd-161">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="ad5dd-162">Per un elenco completo dei piani di licenza (noto anche come i nomi dei prodotti), i piani di servizio inclusi e i rispettivi nomi descrittivi corrispondenti, vedere [i nomi di prodotti e gli identificatori di piano di servizio per la gestione delle licenze](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="ad5dd-162">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="ad5dd-163">Per visualizzare informazioni dettagliate sui servizi Office 365 sono disponibili in un piano di licenze specifico, utilizzare la sintassi seguente.</span><span class="sxs-lookup"><span data-stu-id="ad5dd-163">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="ad5dd-164">In questo esempio vengono illustrati i servizi di Office 365 che sono disponibili nel piano di licenze litwareinc: enterprisepack (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="ad5dd-164">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a><span data-ttu-id="ad5dd-165">Nuovo utente di Office 365?</span><span class="sxs-lookup"><span data-stu-id="ad5dd-165">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="ad5dd-166">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ad5dd-166">See also</span></span>


[<span data-ttu-id="ad5dd-167">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad5dd-167">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="ad5dd-168">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="ad5dd-168">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ad5dd-169">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="ad5dd-169">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
