---
title: Multi-Geo Capabilities in OneDrive e SharePoint Online in Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 1/24/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: "Le funzionalità multi-geo in OneDrive e SharePoint Online, l'organizzazione può espandere la presenza di Office 365 a più aree geografiche e/o paesi all'interno del tenant esistente."
ms.openlocfilehash: d53da13d5a6a6d5add9da69a3bca9fcdfa39bbd0
ms.sourcegitcommit: 38d43444cf5e03527aa75f670efb2de0f48f847d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="913e4-103">Multi-Geo Capabilities in OneDrive e SharePoint Online in Office 365</span><span class="sxs-lookup"><span data-stu-id="913e4-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="913e4-p101">Con Multi-Geo Capabilities in SharePoint Online e OneDrive, l'organizzazione può espandere la presenza di Office 365 a più aree geografiche e/o paesi all'interno del tenant esistente. Al momento questa funzionalità è disponibile in anteprima. Invitare il team degli account Microsoft ad iscrivere la propria società multi-nazionale all'anteprima di OneDrive Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="913e4-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. This feature is currently in preview. Reach out to your Microsoft Account Team to sign up your Multi-National Company for the OneDrive Multi-Geo preview.</span></span>
  
<span data-ttu-id="913e4-107">Con OneDrive Multi-Geo, è possibile effettuare il provisioning e archiviare dati al resto nelle posizioni geo selezionata per soddisfare i requisiti di residenza dati e contemporaneamente sbloccare il (in inglese) globale da esperienze moderno produttività della forza lavoro consentita.</span><span class="sxs-lookup"><span data-stu-id="913e4-107">With OneDrive Multi-Geo, you can provision and store data-at-rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="913e4-108">Ecco come possono utilizzare la funzionalità multi-geo nell'organizzazione:</span><span class="sxs-lookup"><span data-stu-id="913e4-108">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="913e4-109">Fungere da una impresa connessa globale con un singolo tenant di Office 365 che distribuisce in più località geografiche.</span><span class="sxs-lookup"><span data-stu-id="913e4-109">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="913e4-110">Soddisfare i requisiti di residenza dei dati mediante la creazione e l'hosting dei dati a riposo all'interno di località geografiche specifiche.</span><span class="sxs-lookup"><span data-stu-id="913e4-110">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="913e4-111">Offrire agli utenti satellite le stesse esperienze di produttività moderna degli utenti in località centrali.</span><span class="sxs-lookup"><span data-stu-id="913e4-111">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="913e4-112">Consentire agli utenti di spostarsi tra le località geografiche al cambiamento di ruolo, mentre l'accesso al contenuto viene conservato inalterato.</span><span class="sxs-lookup"><span data-stu-id="913e4-112">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="913e4-113">Personalizzare i criteri di condivisione per ogni località geografica e i criteri di prevenzione della perdita dei dati per ogni sito.</span><span class="sxs-lookup"><span data-stu-id="913e4-113">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="913e4-114">Designare responsabili di eDiscovery per località geografica e consentire che regolino i casi personalizzati per tale località.</span><span class="sxs-lookup"><span data-stu-id="913e4-114">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="913e4-115">Scegliere spazi dei nomi dell’URL univoci (ad esempio, ContosoEUR.sharepoint.com) per le località geografiche aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="913e4-115">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="913e4-116">Consolidare i dati in locale dell’area nel tenant multi-geo di Office 365.</span><span class="sxs-lookup"><span data-stu-id="913e4-116">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="913e4-117">Per ulteriori informazioni e per visualizzare una dimostrazione, vedere [Introduzione a Multi-Geo disponibili in Office 365 e relativa configurazione](https://youtu.be/3d9-Vt2fArk) e il[poster della panoramica Multi-Geo](https://technet.microsoft.com/library/dn782272.aspx).</span><span class="sxs-lookup"><span data-stu-id="913e4-117">For more information, and to see a demonstration, see [Introducing Multi-Geo capabilities in Office 365 and how to configure them](https://youtu.be/3d9-Vt2fArk) and the[Multi-Geo overview poster](https://technet.microsoft.com/library/dn782272.aspx).</span></span>
  
<span data-ttu-id="913e4-p102">In una configurazione multi-geo, il tenant di Office 365 è costituito da una località centrale (anche nota come località predefinita) e una o più località geografiche satellite. Il concetto chiave di multi-geo è che un singolo tenancy includerà più località geografiche. In un tenant Multi-Geo, le informazioni su località geografiche, gruppi e le informazioni utente, vengono acquisite in Azure Active Directory (AAD). Poiché le informazioni del tenant sono acquisite in modo centralizzato e sincronizzate in ogni località geografica, la condivisione e le esperienze coinvolgono tutti gli utenti della società.</span><span class="sxs-lookup"><span data-stu-id="913e4-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as a default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>
  
## <a name="sample-multi-geo-tenant-configuration"></a><span data-ttu-id="913e4-122">Configurazione di esempio multi-geo tenant</span><span class="sxs-lookup"><span data-stu-id="913e4-122">Sample multi-geo tenant configuration</span></span>

<span data-ttu-id="913e4-123">Con un tenant con posizioni geografiche diverse, Contoso, con una località centrale del Nord America, può espandere fino a località geografiche satelliti in Europa e Australia entro i limiti dell’organizzazione singola di Contoso.com. Gli utenti con un percorso dati preferito impostato su Europa avranno OneDrive in Europa, mentre gli utenti con un percorso dati preferito in Nord America avranno OneDrive negli Stati Uniti.</span><span class="sxs-lookup"><span data-stu-id="913e4-123">By using a multi-geo tenant, Contoso, with a central location of North America, can expand to satellite geo locations in Europe, and Australia under the single organization umbrella of Contoso.com. Users with their preferred data location set to Europe will have their OneDrive in Europe while users with their preferred data location in North America will have their OneDrive in the US.</span></span>
  
![Mappa del mondo, che mostra geo percorsi per Contoso e gli altri percorsi geo disponibili](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="913e4-125">Ottenere le funzionalità di Multi-Geo con tre semplici passaggi</span><span class="sxs-lookup"><span data-stu-id="913e4-125">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="913e4-126">Configurare multi-geo è semplice:</span><span class="sxs-lookup"><span data-stu-id="913e4-126">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="913e4-127">Abilitare il tenant di Office 365 per multi-geo.</span><span class="sxs-lookup"><span data-stu-id="913e4-127">Enable your Office 365 tenant for multi-geo.</span></span>
    
2. <span data-ttu-id="913e4-128">Aggiungere le località satellite.</span><span class="sxs-lookup"><span data-stu-id="913e4-128">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="913e4-129">Configurare gli account utente per la località appropriata.</span><span class="sxs-lookup"><span data-stu-id="913e4-129">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="913e4-130">Disponibilità e stato di Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="913e4-130">Multi-Geo status and availability</span></span>

<span data-ttu-id="913e4-131">OneDrive Multi-Geo è attualmente disponibile in queste aree geografiche e paesi:</span><span class="sxs-lookup"><span data-stu-id="913e4-131">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="913e4-132">Asia-Pacifico</span><span class="sxs-lookup"><span data-stu-id="913e4-132">Asia-Pacific</span></span>
    
- <span data-ttu-id="913e4-133">Australia</span><span class="sxs-lookup"><span data-stu-id="913e4-133">Australia</span></span>
    
- <span data-ttu-id="913e4-134">Canada</span><span class="sxs-lookup"><span data-stu-id="913e4-134">Canada</span></span>
    
- <span data-ttu-id="913e4-135">Unione Europea (EMEA)</span><span class="sxs-lookup"><span data-stu-id="913e4-135">European Union (EMEA)</span></span>
    
- <span data-ttu-id="913e4-136">India</span><span class="sxs-lookup"><span data-stu-id="913e4-136">India</span></span>
    
- <span data-ttu-id="913e4-137">Giappone</span><span class="sxs-lookup"><span data-stu-id="913e4-137">Japan</span></span>
    
- <span data-ttu-id="913e4-138">Regno Unito</span><span class="sxs-lookup"><span data-stu-id="913e4-138">United Kingdom</span></span>
    
- <span data-ttu-id="913e4-139">Stati Uniti (Nord America)</span><span class="sxs-lookup"><span data-stu-id="913e4-139">United States (North America)</span></span>
    
- <span data-ttu-id="913e4-140">Sud Corea</span><span class="sxs-lookup"><span data-stu-id="913e4-140">South Korea</span></span>
    
> [!NOTE]
> <span data-ttu-id="913e4-141">India e Sud Corea sono attualmente disponibili solo per i clienti con licenze e indirizzi di fatturazione in queste località geografiche.</span><span class="sxs-lookup"><span data-stu-id="913e4-141">India and South Korea are currently only available for customers with licenses and billing addresses in those geo locations.</span></span> 
  
<span data-ttu-id="913e4-142">Prossime località geografiche:</span><span class="sxs-lookup"><span data-stu-id="913e4-142">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="913e4-143">Francia</span><span class="sxs-lookup"><span data-stu-id="913e4-143">France</span></span>
    
<span data-ttu-id="913e4-144">Servizi disponibili:</span><span class="sxs-lookup"><span data-stu-id="913e4-144">Available services:</span></span>
  
- <span data-ttu-id="913e4-145">Exchange Online - in anteprima</span><span class="sxs-lookup"><span data-stu-id="913e4-145">Exchange Online - in preview</span></span>
    
- <span data-ttu-id="913e4-146">OneDrive for Business - in anteprima</span><span class="sxs-lookup"><span data-stu-id="913e4-146">OneDrive for Business - in preview</span></span>
    
- <span data-ttu-id="913e4-147">SharePoint Online - in corso di sviluppo</span><span class="sxs-lookup"><span data-stu-id="913e4-147">SharePoint Online - in development</span></span>
    

