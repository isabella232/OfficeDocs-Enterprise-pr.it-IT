---
title: Multi-Geo Capabilities in OneDrive e SharePoint Online in Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Espandere la presenza di Office 365 a più aree geografiche con funzionalità multi-geo in OneDrive e SharePoint Online.
ms.openlocfilehash: 2c5de533aaaace68e51b747cd62a53b9572bcaec
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="325c6-103">Multi-Geo Capabilities in OneDrive e SharePoint Online in Office 365</span><span class="sxs-lookup"><span data-stu-id="325c6-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="325c6-p101">Con Multi-Geo Capabilities in SharePoint Online e OneDrive, l'organizzazione può espandere la presenza di Office 365 a più aree geografiche e/o paesi all'interno del tenant esistente. Al momento questa funzionalità è disponibile in anteprima. Invitare il team degli account Microsoft ad iscrivere la propria società multi-nazionale all'anteprima di OneDrive Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="325c6-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. This feature is currently in preview. Reach out to your Microsoft Account Team to sign up your Multi-National Company for the OneDrive Multi-Geo preview.</span></span>
  
<span data-ttu-id="325c6-107">Con OneDrive Multi-Geo, è possibile effettuare il provisioning e archiviano i dati statici nelle posizioni geo selezionata per soddisfare i requisiti di residenza dati e contemporaneamente sbloccare il (in inglese) globale da esperienze moderno produttività della forza lavoro consentita.</span><span class="sxs-lookup"><span data-stu-id="325c6-107">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="325c6-108">Ecco come possono utilizzare la funzionalità multi-geo nell'organizzazione:</span><span class="sxs-lookup"><span data-stu-id="325c6-108">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="325c6-109">Fungere da una impresa connessa globale con un singolo tenant di Office 365 che distribuisce in più località geografiche.</span><span class="sxs-lookup"><span data-stu-id="325c6-109">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="325c6-110">Soddisfare i requisiti di residenza dei dati mediante la creazione e l'hosting dei dati a riposo all'interno di località geografiche specifiche.</span><span class="sxs-lookup"><span data-stu-id="325c6-110">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="325c6-111">Offrire agli utenti satellite le stesse esperienze di produttività moderna degli utenti in località centrali.</span><span class="sxs-lookup"><span data-stu-id="325c6-111">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="325c6-112">Consentire agli utenti di spostarsi tra le località geografiche al cambiamento di ruolo, mentre l'accesso al contenuto viene conservato inalterato.</span><span class="sxs-lookup"><span data-stu-id="325c6-112">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="325c6-113">Personalizzare i criteri di condivisione per ogni località geografica e i criteri di prevenzione della perdita dei dati per ogni sito.</span><span class="sxs-lookup"><span data-stu-id="325c6-113">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="325c6-114">Designare responsabili di eDiscovery per località geografica e consentire che regolino i casi personalizzati per tale località.</span><span class="sxs-lookup"><span data-stu-id="325c6-114">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="325c6-115">Scegliere spazi dei nomi dell’URL univoci (ad esempio, ContosoEUR.sharepoint.com) per le località geografiche aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="325c6-115">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="325c6-116">Consolidare i dati in locale dell’area nel tenant multi-geo di Office 365.</span><span class="sxs-lookup"><span data-stu-id="325c6-116">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="325c6-p102">In una configurazione multi-geo tenant Office 365 è costituita da una posizione centralizzata (noto anche come il percorso predefinito) e uno o più percorsi geo satellitari. Il concetto principale di multi-geo è un singolo tenancy verrà estendersi su una più località geografica. In un tenant multi-geo, le informazioni sui percorsi geo, gruppi e informazioni utente, sono gestite in Azure Active Directory (AAD). Dal momento che le informazioni di tenant gestite centralmente e sincronizzate in ogni località geografica, condivisione ed esperienze che coinvolgono tutti gli utenti della società e contengono consapevolezza globale.</span><span class="sxs-lookup"><span data-stu-id="325c6-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>
  
## <a name="sample-multi-geo-tenant-configuration"></a><span data-ttu-id="325c6-121">Configurazione di esempio multi-geo tenant</span><span class="sxs-lookup"><span data-stu-id="325c6-121">Sample multi-geo tenant configuration</span></span>

<span data-ttu-id="325c6-122">Con un tenant con posizioni geografiche diverse, Contoso, con una località centrale del Nord America, può espandere fino a località geografiche satelliti in Europa e Australia entro i limiti dell’organizzazione singola di Contoso.com. Gli utenti con un percorso dati preferito impostato su Europa avranno OneDrive in Europa, mentre gli utenti con un percorso dati preferito in Nord America avranno OneDrive negli Stati Uniti.</span><span class="sxs-lookup"><span data-stu-id="325c6-122">By using a multi-geo tenant, Contoso, with a central location of North America, can expand to satellite geo locations in Europe, and Australia under the single organization umbrella of Contoso.com. Users with their preferred data location set to Europe will have their OneDrive in Europe while users with their preferred data location in North America will have their OneDrive in the US.</span></span>
  
![Mappa del mondo, che mostra geo percorsi per Contoso e gli altri percorsi geo disponibili](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="325c6-124">Ottenere le funzionalità di Multi-Geo con tre semplici passaggi</span><span class="sxs-lookup"><span data-stu-id="325c6-124">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="325c6-125">Configurare multi-geo è semplice:</span><span class="sxs-lookup"><span data-stu-id="325c6-125">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="325c6-p103">Collaborare con il team amministrativo per aggiungere il piano di servizio _Multi-Geo disponibili in Office 365_ . Sono contenute informazioni per aggiungere il numero di licenze necessarie.</span><span class="sxs-lookup"><span data-stu-id="325c6-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="325c6-128">Aggiungere le località satellite.</span><span class="sxs-lookup"><span data-stu-id="325c6-128">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="325c6-129">Configurare gli account utente per la località appropriata.</span><span class="sxs-lookup"><span data-stu-id="325c6-129">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="325c6-130">Disponibilità e stato di Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="325c6-130">Multi-Geo status and availability</span></span>

<span data-ttu-id="325c6-131">OneDrive Multi-Geo è attualmente disponibile in queste aree geografiche e paesi:</span><span class="sxs-lookup"><span data-stu-id="325c6-131">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="325c6-132">Asia-Pacifico</span><span class="sxs-lookup"><span data-stu-id="325c6-132">Asia-Pacific</span></span>
    
- <span data-ttu-id="325c6-133">Australia</span><span class="sxs-lookup"><span data-stu-id="325c6-133">Australia</span></span>
    
- <span data-ttu-id="325c6-134">Canada</span><span class="sxs-lookup"><span data-stu-id="325c6-134">Canada</span></span>
    
- <span data-ttu-id="325c6-135">Unione Europea (EMEA)</span><span class="sxs-lookup"><span data-stu-id="325c6-135">European Union (EMEA)</span></span>
    
- <span data-ttu-id="325c6-136">Giappone</span><span class="sxs-lookup"><span data-stu-id="325c6-136">Japan</span></span>
    
- <span data-ttu-id="325c6-137">Regno Unito</span><span class="sxs-lookup"><span data-stu-id="325c6-137">United Kingdom</span></span>
    
- <span data-ttu-id="325c6-138">Stati Uniti (Nord America)</span><span class="sxs-lookup"><span data-stu-id="325c6-138">United States (North America)</span></span>
    
- <span data-ttu-id="325c6-139">Corea</span><span class="sxs-lookup"><span data-stu-id="325c6-139">Korea</span></span>
      
<span data-ttu-id="325c6-140">Prossime località geografiche:</span><span class="sxs-lookup"><span data-stu-id="325c6-140">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="325c6-141">Francia</span><span class="sxs-lookup"><span data-stu-id="325c6-141">France</span></span>
- <span data-ttu-id="325c6-142">India</span><span class="sxs-lookup"><span data-stu-id="325c6-142">India</span></span>
    
## <a name="getting-started"></a><span data-ttu-id="325c6-143">Introduzione</span><span class="sxs-lookup"><span data-stu-id="325c6-143">Getting started</span></span>

<span data-ttu-id="325c6-p104">Per iniziare a OneDrive per Business Multi-Geo, il primo passaggio consiste nel [pianificare il OneDrive for Business Multi-Geo ambiente](plan-for-multi-geo.md). Avanti, [informazioni sull'amministrazione di un ambiente multi-geo](administering-a-multi-geo-environment.md) e [come gli utenti osserveranno un ambiente multi-geo](multi-geo-user-experience.md). Quando si è pronti a impostare OneDrive per Business Multi-Geo, [configurare il tenant per multi-geo](multi-geo-tenant-configuration.md), quindi [spostare tutti i siti OneDrive esistenti per la nuova posizione geografica](move-onedrive-between-geo-locations.md) e [configurare la ricerca](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="325c6-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
