---
title: Architettura degli scenari cloud ibridi Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: "Riepilogo: informazioni sull'architettura delle offerte cloud ibride di Microsoft."
ms.openlocfilehash: 513e45629a7092803cc644241d84985a37e43876
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068322"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a><span data-ttu-id="d349c-103">Architettura degli scenari cloud ibridi Microsoft</span><span class="sxs-lookup"><span data-stu-id="d349c-103">Architecture of Microsoft hybrid cloud scenarios</span></span>

 <span data-ttu-id="d349c-104">**Riepilogo:** Comprendere l'architettura delle offerte cloud ibride di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d349c-104">**Summary:** Understand the architecture of Microsoft's hybrid cloud offerings.</span></span>
  
<span data-ttu-id="d349c-105">Utilizzare un approccio architettonico per pianificare e implementare scenari basati su cloud ibrido con i servizi cloud e le piattaforme Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d349c-105">Use an architectural approach to plan and implement hybrid cloud scenarios with Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="d349c-106">**Figura 1: stack cloud ibrido Microsoft**</span><span class="sxs-lookup"><span data-stu-id="d349c-106">**Figure 1: The Microsoft hybrid cloud stack**</span></span>

![Stack del cloud ibrido Microsoft](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
<span data-ttu-id="d349c-108">Nella figura 1 viene mostrato lo stack del cloud ibrido Microsoft e il relativo layer, che include i locali, la rete, l'identità, le app e gli scenari e la categoria del servizio cloud (Microsoft SaaS, Azure PaaS e Azure PaaS).</span><span class="sxs-lookup"><span data-stu-id="d349c-108">Figure 1 shows the Microsoft hybrid cloud stack and its layer, which include on-premises, network, Identity, apps and scenarios, and the category of cloud service (Microsoft SaaS, Azure PaaS, and Azure PaaS).</span></span>
  
<span data-ttu-id="d349c-109">Il livello Apps and Scenarios contiene gli scenari specifici del cloud ibrido descritti in dettaglio negli articoli aggiuntivi di questo modello.</span><span class="sxs-lookup"><span data-stu-id="d349c-109">The Apps and scenarios layer has the specific hybrid cloud scenarios that are detailed in the additional articles of this model.</span></span> <span data-ttu-id="d349c-110">I livelli Identity, Network e on-premises possono essere comuni alle categorie del servizio cloud (SaaS, PaaS o PaaS).</span><span class="sxs-lookup"><span data-stu-id="d349c-110">The Identity, Network, and On-premises layers can be common to the categories of cloud service (SaaS, PaaS, or PaaS).</span></span>
  
- <span data-ttu-id="d349c-111">Locale</span><span class="sxs-lookup"><span data-stu-id="d349c-111">On-premises</span></span>
    
    <span data-ttu-id="d349c-112">L'infrastruttura locale per gli scenari ibridi può includere server per SharePoint, Exchange, Skype for business e applicazioni line-of-business.</span><span class="sxs-lookup"><span data-stu-id="d349c-112">On-premises infrastructure for hybrid scenarios can include servers for SharePoint, Exchange, Skype for Business, and line of business applications.</span></span> <span data-ttu-id="d349c-113">È inoltre possibile includere archivi dati (database, elenchi, file).</span><span class="sxs-lookup"><span data-stu-id="d349c-113">It can also include data stores (databases, lists, files).</span></span> <span data-ttu-id="d349c-114">Senza le connessioni di ExpressRoute, è necessario consentire l'accesso agli archivi dati locali tramite un proxy inverso o rendendo il server o i dati accessibili nella DMZ o nell'Extranet.</span><span class="sxs-lookup"><span data-stu-id="d349c-114">Without ExpressRoute connections, access to the on-premises data stores must be allowed through a reverse proxy or by making the server or data accessible on your DMZ or extranet.</span></span>
    
- <span data-ttu-id="d349c-115">Rete</span><span class="sxs-lookup"><span data-stu-id="d349c-115">Network</span></span>
    
    <span data-ttu-id="d349c-116">Sono disponibili due opzioni per la connettività alle piattaforme e ai servizi cloud Microsoft: la tubazione Internet esistente e la ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="d349c-116">There are two choices for connectivity to Microsoft cloud platforms and services: your existing Internet pipe and ExpressRoute.</span></span> <span data-ttu-id="d349c-117">Utilizzare una connessione ExpressRoute se sono importanti le prestazioni prevedibili.</span><span class="sxs-lookup"><span data-stu-id="d349c-117">Use an ExpressRoute connection if predictable performance is important.</span></span> <span data-ttu-id="d349c-118">È possibile utilizzare una connessione ExpressRoute per connettersi direttamente ai servizi SaaS di Microsoft (Office 365 e Dynamics 365), ai servizi di PaaS di Azure e ai servizi di IaaS di Azure.</span><span class="sxs-lookup"><span data-stu-id="d349c-118">You can use one ExpressRoute connection to connect directly to Microsoft SaaS services (Office 365 and Dynamics 365), Azure PaaS services, and Azure IaaS services.</span></span>
    
- <span data-ttu-id="d349c-119">Identità</span><span class="sxs-lookup"><span data-stu-id="d349c-119">Identity</span></span>
    
    <span data-ttu-id="d349c-120">Per l'infrastruttura di identità cloud, esistono due modi per andare, a seconda della piattaforma cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d349c-120">For cloud identity infrastructure, there are two ways to go, depending on the Microsoft cloud platform.</span></span> <span data-ttu-id="d349c-121">Per SaaS e Azure PaaS, integrare l'infrastruttura di identità locale con Azure AD o con la Federazione con l'infrastruttura di identità locale o con i provider di identità di terze parti.</span><span class="sxs-lookup"><span data-stu-id="d349c-121">For SaaS and Azure PaaS, integrate your on-premises identity infrastructure with Azure AD or federate with your on-premises identity infrastructure or third-party identity providers.</span></span> <span data-ttu-id="d349c-122">Per le macchine virtuali in esecuzione in Azure, è possibile estendere l'infrastruttura di identità locale, ad esempio servizi di dominio Active Directory, alle reti virtuali (reti virtuali) in cui risiedono le macchine virtuali.</span><span class="sxs-lookup"><span data-stu-id="d349c-122">For VMs running in Azure, you can extend your on-premises identity infrastructure, such as Active Directory Domain Services (AD DS), to the virtual networks (VNets) where your VMs reside.</span></span>
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a><span data-ttu-id="d349c-123">Scenari di cloud ibridi per il processo di adozione di cloud in tre fasi</span><span class="sxs-lookup"><span data-stu-id="d349c-123">Hybrid cloud scenarios for the three-phase cloud adoption process</span></span>

<span data-ttu-id="d349c-124">Molte imprese, tra cui quelle di Microsoft, utilizzano un approccio trifasico per l'adozione del cloud.</span><span class="sxs-lookup"><span data-stu-id="d349c-124">Many enterprises, including Microsoft's, use a three-phase approach to adopting the cloud.</span></span> <span data-ttu-id="d349c-125">Gli scenari di cloud ibridi possono svolgere un ruolo in ogni fase.</span><span class="sxs-lookup"><span data-stu-id="d349c-125">Hybrid cloud scenarios can play a role in each phase.</span></span>
  
1. <span data-ttu-id="d349c-126">Spostamento dei carichi di lavoro di produttività in SaaS</span><span class="sxs-lookup"><span data-stu-id="d349c-126">Move productivity workloads to SaaS</span></span>
    
    <span data-ttu-id="d349c-127">Per i carichi di lavoro di produttività che attualmente sono o devono rimanere in locale, gli scenari ibridi consentono di integrarli con le rispettive controparti cloud.</span><span class="sxs-lookup"><span data-stu-id="d349c-127">For productivity workloads that currently are or must stay on-premises, hybrid scenarios allow them to be integrated with their cloud counterparts.</span></span>
    
2. <span data-ttu-id="d349c-128">Sviluppare applicazioni nuove e moderne in Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="d349c-128">Develop new and modern applications in Azure PaaS</span></span>
    
    <span data-ttu-id="d349c-129">Le applicazioni ibride di PaaS di Azure possono sfruttare in modo sicuro il server locale o le risorse di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="d349c-129">Azure PaaS hybrid applications can securely leverage on-premises server or storage resources.</span></span>
    
3. <span data-ttu-id="d349c-130">Spostare le applicazioni esistenti in Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="d349c-130">Move existing applications to Azure IaaS</span></span>
    
    <span data-ttu-id="d349c-131">Per gli scenari di Lift-and-Shift e Build-in-the-cloud, le applicazioni basate su server in esecuzione nelle macchine virtuali di Azure offrono un semplice provisioning e ridimensionamento.</span><span class="sxs-lookup"><span data-stu-id="d349c-131">For lift-and-shift and build-in-the-cloud scenarios, server-based applications running on Azure VMs provide easy provisioning and scaling.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="d349c-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d349c-132">See Also</span></span>

[<span data-ttu-id="d349c-133">Cloud ibrido Microsoft per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="d349c-133">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="d349c-134">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="d349c-134">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

