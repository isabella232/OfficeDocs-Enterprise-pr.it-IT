---
title: Architettura degli scenari cloud ibridi Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: "Riepilogo: Comprendere l'architettura di ibrida offerte cloud di Microsoft."
ms.openlocfilehash: 8a0c5c37c2e0dfd0c6641128b1cee89c89e16441
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914921"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a><span data-ttu-id="9e9be-103">Architettura degli scenari cloud ibridi Microsoft</span><span class="sxs-lookup"><span data-stu-id="9e9be-103">Architecture of Microsoft hybrid cloud scenarios</span></span>

 <span data-ttu-id="9e9be-104">**Riepilogo:** Acquisire familiarità con l'architettura di ibrida offerte cloud di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9e9be-104">**Summary:** Understand the architecture of Microsoft's hybrid cloud offerings.</span></span>
  
<span data-ttu-id="9e9be-105">Utilizzare un approccio dell'architettura per pianificare e implementare scenari basati su cloud ibrida con servizi cloud Microsoft e piattaforme.</span><span class="sxs-lookup"><span data-stu-id="9e9be-105">Use an architectural approach to plan and implement hybrid cloud scenarios with Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="9e9be-106">**Nella figura 1: Microsoft ibrida cloud stack**</span><span class="sxs-lookup"><span data-stu-id="9e9be-106">**Figure 1: The Microsoft hybrid cloud stack**</span></span>

![Stack cloud ibrido Microsoft](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
<span data-ttu-id="9e9be-108">Nella figura 1 viene illustrato lo stack di cloud Microsoft ibrida e il relativo livello, che comprendono locale, rete, identità, applicazioni e gli scenari e la categoria del servizio cloud (SaaS Microsoft Azure PaaS e Azure PaaS).</span><span class="sxs-lookup"><span data-stu-id="9e9be-108">Figure 1 shows the Microsoft hybrid cloud stack and its layer, which include on-premises, network, Identity, apps and scenarios, and the category of cloud service (Microsoft SaaS, Azure PaaS, and Azure PaaS).</span></span>
  
<span data-ttu-id="9e9be-p101">Il livello applicazioni e gli scenari contiene gli scenari di cloud ibrida specifica che sono descritti negli articoli aggiuntivi di questo modello. L'identità, rete e locali livelli possono essere comuni per le categorie di servizio cloud (SaaS, PaaS o PaaS).</span><span class="sxs-lookup"><span data-stu-id="9e9be-p101">The Apps and scenarios layer contains the specific hybrid cloud scenarios that are detailed in the additional articles of this model. The Identity, Network, and On-premises layers can be common to the categories of cloud service (SaaS, PaaS, or PaaS).</span></span>
  
- <span data-ttu-id="9e9be-111">Locale</span><span class="sxs-lookup"><span data-stu-id="9e9be-111">On-premises</span></span>
    
    <span data-ttu-id="9e9be-p102">Infrastruttura locale per gli scenari ibridi può includere i server per SharePoint, Exchange, Skype per le aziende e applicazioni line of business. Inoltre possibile includere archivi dati (database, elenchi, i file). Senza connessioni ExpressRoute, è necessario consentire l'accesso per gli archivi dati locali tramite un proxy inverso o rendere il server o i dati accessibile nella DMZ o extranet.</span><span class="sxs-lookup"><span data-stu-id="9e9be-p102">On-premises infrastructure for hybrid scenarios can include servers for SharePoint, Exchange, Skype for Business, and line of business applications. It can also include data stores (databases, lists, files). Without ExpressRoute connections, access to the on-premises data stores must be allowed through a reverse proxy or by making the server or data accessible on your DMZ or extranet.</span></span>
    
- <span data-ttu-id="9e9be-115">Rete</span><span class="sxs-lookup"><span data-stu-id="9e9be-115">Network</span></span>
    
    <span data-ttu-id="9e9be-p103">Sono disponibili due opzioni per la connettività a Microsoft cloud piattaforme e servizi: il canale Internet esistente ed ExpressRoute. Utilizzare una connessione ExpressRoute se le prestazioni prevedibile sono importanti. È possibile utilizzare una connessione ExpressRoute per la connessione direttamente a Microsoft SaaS services (Office 365 e Dynamics 365), servizi di Azure PaaS e servizi di Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="9e9be-p103">There are two choices for connectivity to Microsoft cloud platforms and services: your existing Internet pipe and ExpressRoute. Use an ExpressRoute connection if predictable performance is important. You can use one ExpressRoute connection to connect directly to Microsoft SaaS services (Office 365 and Dynamics 365), Azure PaaS services, and Azure IaaS services.</span></span>
    
- <span data-ttu-id="9e9be-119">Identità</span><span class="sxs-lookup"><span data-stu-id="9e9be-119">Identity</span></span>
    
    <span data-ttu-id="9e9be-p104">Per l'infrastruttura di identità cloud, esistono due modi per accedere, a seconda della piattaforma Microsoft cloud. Per SaaS e Azure PaaS, integrare l'infrastruttura di identità in locale con Azure Active Directory o la federazione con i provider di identità locale dell'infrastruttura o di terze parti dell'identità. Per le macchine virtuali in esecuzione in Azure, è possibile estendere l'infrastruttura di identità in locale, ad esempio Windows Server Active Directory, per le reti virtuali (VNets) in cui si trovano nelle macchine virtuali.</span><span class="sxs-lookup"><span data-stu-id="9e9be-p104">For cloud identity infrastructure, there are two ways to go, depending on the Microsoft cloud platform. For SaaS and Azure PaaS, integrate your on-premises identity infrastructure with Azure AD or federate with your on-premises identity infrastructure or third-party identity providers. For VMs running in Azure, you can extend your on-premises identity infrastructure, such as Windows Server AD, to the virtual networks (VNets) where your VMs reside.</span></span>
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a><span data-ttu-id="9e9be-123">Scenari basati su cloud ibrida per il processo di adozione cloud tre fasi</span><span class="sxs-lookup"><span data-stu-id="9e9be-123">Hybrid cloud scenarios for the three-phase cloud adoption process</span></span>

<span data-ttu-id="9e9be-p105">Molte aziende, tra cui Microsoft, utilizzano un approccio tre fasi per adottando nel cloud. Scenari basati su cloud ibrida possono avere un ruolo di ogni fase.</span><span class="sxs-lookup"><span data-stu-id="9e9be-p105">Many enterprises, including Microsoft's, use a three-phase approach to adopting the cloud. Hybrid cloud scenarios can play a role in each phase.</span></span>
  
1. <span data-ttu-id="9e9be-126">Spostare i carichi di lavoro per la produttività SaaS</span><span class="sxs-lookup"><span data-stu-id="9e9be-126">Move productivity workloads to SaaS</span></span>
    
    <span data-ttu-id="9e9be-127">Per la produttività dei carichi di lavoro che sono attualmente o deve rimanere in locale, scenari ibridi consentono loro di essere integrate con le relative controparti cloud.</span><span class="sxs-lookup"><span data-stu-id="9e9be-127">For productivity workloads that currently are or must stay on-premises, hybrid scenarios allow them to be integrated with their cloud counterparts.</span></span>
    
2. <span data-ttu-id="9e9be-128">Sviluppare applicazioni nuove e moderne in Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="9e9be-128">Develop new and modern applications in Azure PaaS</span></span>
    
    <span data-ttu-id="9e9be-129">Applicazioni ibrida PaaS Azure in modo sicuro utilizzo delle risorse di archiviazione o server locale.</span><span class="sxs-lookup"><span data-stu-id="9e9be-129">Azure PaaS hybrid applications can securely leverage on-premises server or storage resources.</span></span>
    
3. <span data-ttu-id="9e9be-130">Spostare le applicazioni esistenti per Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="9e9be-130">Move existing applications to Azure IaaS</span></span>
    
    <span data-ttu-id="9e9be-131">Per scenari ascensore MAIUSC e compilazione nel cloud, le applicazioni basate su server in esecuzione su macchine virtuali di Azure offrono il provisioning di tipo semplice e la scala.</span><span class="sxs-lookup"><span data-stu-id="9e9be-131">For lift-and-shift and build-in-the-cloud scenarios, server-based applications running on Azure VMs provide easy provisioning and scaling.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="9e9be-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9e9be-132">See Also</span></span>

[<span data-ttu-id="9e9be-133">Cloud ibrido Microsoft per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="9e9be-133">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="9e9be-134">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="9e9be-134">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="9e9be-135">Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT</span><span class="sxs-lookup"><span data-stu-id="9e9be-135">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



