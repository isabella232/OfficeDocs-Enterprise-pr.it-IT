---
title: Visualizzare le licenze e i servizi con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/31/2018
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
ms.openlocfilehash: dab6b8f1828c6be4d32bb2432437d23328653560
ms.sourcegitcommit: 6dd4ac5808d72406578fcc7be6590dd7a99cebea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/31/2018
ms.locfileid: "27466875"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="ceb95-103">Visualizzare le licenze e i servizi con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="ceb95-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="ceb95-104">**Riepilogo:** Viene illustrato come utilizzare Office 365 PowerShell per visualizzare informazioni sulle licenze piani, servizi e le licenze disponibili nell'organizzazione Office 365.</span><span class="sxs-lookup"><span data-stu-id="ceb95-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="ceb95-105">Ogni sottoscrizione a Office 365 sono disponibili i seguenti elementi:</span><span class="sxs-lookup"><span data-stu-id="ceb95-105">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="ceb95-p101">**Piani di gestione delle licenze** Vi sono detti anche piani di licenza o piani di Office 365. Piani di gestione delle licenze definiscano i servizi di Office 365 disponibili agli utenti. La sottoscrizione a Office 365 può contenere più piani di gestione delle licenze. Un piano di licenze di esempio è E3 Enterprise di Office 365.</span><span class="sxs-lookup"><span data-stu-id="ceb95-p101">**Licensing plans** These are also known as license plans or Office 365 plans. Licensing plans define the Office 365 services that are available to users. Your Office 365 subscription may contain multiple licensing plans. An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="ceb95-p102">**Servizi** Questi sono noti anche come piani di servizio. Servizi sono i prodotti Office 365, caratteristiche e funzionalità disponibili in ogni piano di licenze, ad esempio, Exchange Online e Office Professional Plus. Gli utenti possono avere più di licenze assegnate loro da diversi piani di gestione delle licenze cui concedono l'accesso a diversi servizi.</span><span class="sxs-lookup"><span data-stu-id="ceb95-p102">**Services** These are also known as service plans. Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus. Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="ceb95-p103">**Licenze** Ogni piano di licenze contiene il numero di licenze acquistate. Consigliabile assegnare licenze agli utenti in modo che utilizzino i servizi di Office 365 definiti per il piano di licenze. Ogni account utente deve disporre almeno una licenza da un piano di licenze affinché possano accedere a Office 365 e utilizzare i servizi.</span><span class="sxs-lookup"><span data-stu-id="ceb95-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="ceb95-p104">È possibile utilizzare Office 365 PowerShell per visualizzare i dettagli sui piani di gestione delle licenze disponibili, le licenze e servizi all'interno dell'organizzazione Office 365. Per ulteriori informazioni sui prodotti, funzionalità e i servizi disponibili in diverse sottoscrizioni a Office 365, vedere [Opzioni di pianificazione di Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span><span class="sxs-lookup"><span data-stu-id="ceb95-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="ceb95-118">Informazioni preliminari</span><span class="sxs-lookup"><span data-stu-id="ceb95-118">Before you begin</span></span>

- <span data-ttu-id="ceb95-p105">Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="ceb95-p105">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="ceb95-p106">È disponibile uno script di PowerShell che consente di automatizzare le procedure descritte in questo argomento. In particolare, lo script consente di visualizzare e disabilitare i servizi nella propria organizzazione Office 365, tra cui oscillazione. Per ulteriori informazioni, vedere [disattivare l'accesso a oscillazione con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="ceb95-p106">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script lets you view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
## <a name="view-information-about-licensing-plans-and-the-available-licenses"></a><span data-ttu-id="ceb95-124">Visualizzare informazioni sui piani di gestione delle licenze e sulle licenze disponibili</span><span class="sxs-lookup"><span data-stu-id="ceb95-124">View information about licensing plans and the available licenses</span></span>

<span data-ttu-id="ceb95-125">Per visualizzare le informazioni di riepilogo sui piani di licenza correnti e le licenze disponibili per ciascun piano, eseguire il comando seguente in Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ceb95-125">To view summary information about your current licensing plans and the available licenses for each plan, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="ceb95-126">I risultati contengono le seguenti informazioni:</span><span class="sxs-lookup"><span data-stu-id="ceb95-126">The results contain the following information:</span></span>
  
- <span data-ttu-id="ceb95-p107">**AccountSkuId:** Mostra i piani di gestione delle licenze disponibili per l'organizzazione utilizzando la sintassi `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ è il valore fornito al momento è registrato in Office 365 ed è univoco per l'organizzazione. Il _<LicensingPlan>_ valore è lo stesso per tutti gli utenti. Ad esempio, nel valore `litwareinc:ENTERPRISEPACK`, è il nome della società `litwareinc`e il nome del piano delle licenze `ENTERPRISEPACK`, ovvero il nome del sistema per Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="ceb95-p107">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="ceb95-131">**ActiveUnits:** Numero di licenze che hai gli acquisti per un piano di licenze specifico.</span><span class="sxs-lookup"><span data-stu-id="ceb95-131">**ActiveUnits:** Number of licenses that you've purchases for a specific licensing plan.</span></span>
    
- <span data-ttu-id="ceb95-132">**WarningUnits:** Numero di licenze di un piano di licenze che non sono rinnovato e che scadranno dopo il periodo di prova di 30 giorni.</span><span class="sxs-lookup"><span data-stu-id="ceb95-132">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="ceb95-133">**ConsumedUnits:** Numero di licenze assegnate agli utenti di un piano di licenze specifico.</span><span class="sxs-lookup"><span data-stu-id="ceb95-133">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="ceb95-134">Per visualizzare informazioni dettagliate sui servizi Office 365 sono disponibili in tutti i piani di licenza, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ceb95-134">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="ceb95-p108">Nella tabella seguente vengono illustrati i piani di servizio di Office 365 e i relativi nomi descrittivi per i servizi più comuni. Elenco di piani di servizio potrebbe essere diverso.</span><span class="sxs-lookup"><span data-stu-id="ceb95-p108">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="ceb95-137">**Piano di servizio**</span><span class="sxs-lookup"><span data-stu-id="ceb95-137">**Service plan**</span></span>|<span data-ttu-id="ceb95-138">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="ceb95-138">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="ceb95-139">Sway</span><span class="sxs-lookup"><span data-stu-id="ceb95-139">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="ceb95-140">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ceb95-140">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="ceb95-141">Yammer</span><span class="sxs-lookup"><span data-stu-id="ceb95-141">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="ceb95-142">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="ceb95-142">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="ceb95-143">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="ceb95-143">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="ceb95-144">Skype for Business online</span><span class="sxs-lookup"><span data-stu-id="ceb95-144">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="ceb95-145">Office Online</span><span class="sxs-lookup"><span data-stu-id="ceb95-145">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="ceb95-146">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ceb95-146">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="ceb95-147">Exchange Online, piano 2</span><span class="sxs-lookup"><span data-stu-id="ceb95-147">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="ceb95-148">Per un elenco completo dei piani di licenza (noto anche come i nomi dei prodotti), i piani di servizio inclusi e i rispettivi nomi descrittivi corrispondenti, vedere [i nomi di prodotti e gli identificatori di piano di servizio per la gestione delle licenze](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="ceb95-148">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="ceb95-149">Per visualizzare informazioni dettagliate sui servizi Office 365 sono disponibili in un piano di licenze specifico, utilizzare la sintassi seguente.</span><span class="sxs-lookup"><span data-stu-id="ceb95-149">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="ceb95-150">In questo esempio vengono illustrati i servizi di Office 365 che sono disponibili nel piano di licenze litwareinc: enterprisepack (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="ceb95-150">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="new-to-office-365"></a><span data-ttu-id="ceb95-151">Nuovo utente di Office 365?</span><span class="sxs-lookup"><span data-stu-id="ceb95-151">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="ceb95-152">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ceb95-152">See also</span></span>

- [<span data-ttu-id="ceb95-153">Visualizzare gli utenti con e senza licenza con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="ceb95-153">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [<span data-ttu-id="ceb95-154">Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ceb95-154">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
- [<span data-ttu-id="ceb95-155">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="ceb95-155">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)

