---
title: Infrastruttura IT ed esigenze di Contoso
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5d6a58b8-bec3-4629-9737-8733c7b7ec92
description: "Riepilogo: Comprendere la struttura di base di Contoso locale come la propria attività è necessario possono essere soddisfatti dall'offerte cloud di Microsoft e l'infrastruttura IT."
ms.openlocfilehash: e500aa1f3105c1e605d0d3c1d5f66651acb82b34
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915731"
---
# <a name="contosos-it-infrastructure-and-needs"></a><span data-ttu-id="51c7a-103">Infrastruttura IT ed esigenze di Contoso</span><span class="sxs-lookup"><span data-stu-id="51c7a-103">Contoso's IT infrastructure and needs</span></span>

 <span data-ttu-id="51c7a-104">**Riepilogo:** Acquisire familiarità con la struttura di base di Contoso locale come la propria attività è necessario possono essere soddisfatti dall'offerte cloud di Microsoft e l'infrastruttura IT.</span><span class="sxs-lookup"><span data-stu-id="51c7a-104">**Summary:** Understand the basic structure of Contoso's on-premises IT infrastructure and how its business needs can be met by Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="51c7a-105">Contoso è in fase di transizione da un locale, l'infrastruttura IT centralizzata per uno inclusi cloud che incorpora carichi di lavoro per la produttività personale basato su cloud, le applicazioni e gli scenari ibridi.</span><span class="sxs-lookup"><span data-stu-id="51c7a-105">Contoso is in the process of transitioning from an on-premises, centralized IT infrastructure to a cloud-inclusive one that incorporates cloud-based personal productivity workloads, applications, and hybrid scenarios.</span></span>
  
## <a name="contosos-existing-it-infrastructure"></a><span data-ttu-id="51c7a-106">Infrastruttura IT esistente di Contoso</span><span class="sxs-lookup"><span data-stu-id="51c7a-106">Contoso's existing IT infrastructure</span></span>

<span data-ttu-id="51c7a-107">Contoso utilizza un principalmente centralizzato sull'infrastruttura IT, con centri dati applicazione nella sede centrale Parigi locale.</span><span class="sxs-lookup"><span data-stu-id="51c7a-107">Contoso uses a mostly centralized on-premises IT infrastructure, with application datacenters in the Paris headquarters.</span></span>
  
<span data-ttu-id="51c7a-108">**Nella figura 1: Infrastruttura IT Contoso**</span><span class="sxs-lookup"><span data-stu-id="51c7a-108">**Figure 1: Contoso's existing IT infrastructure**</span></span>

![Infrastruttura IT esistente di Contoso](media/Contoso-Poster/Existing-IT.png)
  
<span data-ttu-id="51c7a-110">Nella figura 1 viene illustrata una sede con centri dati applicazione, DMZ e Internet.</span><span class="sxs-lookup"><span data-stu-id="51c7a-110">Figure 1 shows a headquarters office with application datacenters, a DMZ, and the Internet.</span></span>
  
<span data-ttu-id="51c7a-111">In Contoso DMZ, fornire diversi set dei server:</span><span class="sxs-lookup"><span data-stu-id="51c7a-111">In Contoso's DMZ, different sets of servers provide:</span></span>
  
- <span data-ttu-id="51c7a-112">Accesso remoto per l'inoltro di intranet e del web Contoso per i propri colleghi in sede Paris.</span><span class="sxs-lookup"><span data-stu-id="51c7a-112">Remote access to the Contoso intranet and web proxying for workers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="51c7a-113">Hosting per il sito web pubblico Contoso, da cui i clienti possono ordinare prodotti, Web part o forniture.</span><span class="sxs-lookup"><span data-stu-id="51c7a-113">Hosting for the Contoso public web site, from which customers can order products, parts, or supplies.</span></span>
    
- <span data-ttu-id="51c7a-114">Per i partner di Contoso extranet per partner comunicazione e collaborazione di hosting.</span><span class="sxs-lookup"><span data-stu-id="51c7a-114">Hosting for the Contoso partner extranet for partner communication and collaboration.</span></span>
    
## <a name="contosos-business-needs"></a><span data-ttu-id="51c7a-115">Esigenze aziendali di Contoso</span><span class="sxs-lookup"><span data-stu-id="51c7a-115">Contoso's business needs</span></span>

<span data-ttu-id="51c7a-116">Di seguito sono le esigenze aziendali di Contoso in ordine di priorità:</span><span class="sxs-lookup"><span data-stu-id="51c7a-116">Here are Contoso's business needs in priority order:</span></span>
  
1. <span data-ttu-id="51c7a-117">Rispettare le normative internazionali</span><span class="sxs-lookup"><span data-stu-id="51c7a-117">Adhere to regional regulatory requirements</span></span>
    
    <span data-ttu-id="51c7a-118">Per evitare multe e mantenere una buona relazioni con gli enti pubblici hanno locale, Contoso deve garantire la conformità alle normative di archiviazione e la crittografia dei dati.</span><span class="sxs-lookup"><span data-stu-id="51c7a-118">To prevent fines and maintain good relations with local governments, Contoso must ensure compliance with data storage and encryption regulations.</span></span>
    
2. <span data-ttu-id="51c7a-119">Migliorare la gestione di fornitori e partner</span><span class="sxs-lookup"><span data-stu-id="51c7a-119">Improve vendor and partner management</span></span>
    
    <span data-ttu-id="51c7a-p101">Partner extranet è durata e costosa da gestire. Contoso desidera sostituire con una soluzione basata su cloud che utilizza l'autenticazione federata.</span><span class="sxs-lookup"><span data-stu-id="51c7a-p101">The partner extranet is aging and expensive to maintain. Contoso wants to replace it with a cloud-based solution that uses federated authentication.</span></span>
    
3. <span data-ttu-id="51c7a-122">Migliorare la produttività della forza lavoro mobile, la gestione dei dispositivi e accesso</span><span class="sxs-lookup"><span data-stu-id="51c7a-122">Improve mobile workforce productivity, device management, and access</span></span>
    
    <span data-ttu-id="51c7a-123">Forza lavoro mobile sola Contoso è l'espansione ed è la gestione dei dispositivi per garantire un accesso più efficiente alle risorse e protezione della proprietà intellettuale.</span><span class="sxs-lookup"><span data-stu-id="51c7a-123">Contoso's mobile-only workforce is expanding and needs device management to ensure intellectual property protection and more efficient access to resources.</span></span>
    
4. <span data-ttu-id="51c7a-124">Riduzione dell'infrastruttura di accesso remoto</span><span class="sxs-lookup"><span data-stu-id="51c7a-124">Reduce remote access infrastructure</span></span>
    
    <span data-ttu-id="51c7a-125">Spostando le risorse normalmente utilizzate da dipendenti remoti nel cloud, Contoso verrà risparmiare denaro grazie alla riduzione dei costi di manutenzione e supporto per la propria soluzione di accesso remoto.</span><span class="sxs-lookup"><span data-stu-id="51c7a-125">By moving resources commonly accessed by remote workers to the cloud, Contoso will save money by reducing maintenance and support costs for their remote access solution.</span></span>
    
5. <span data-ttu-id="51c7a-126">Implementare la scalabilità verso il basso centri dati locali</span><span class="sxs-lookup"><span data-stu-id="51c7a-126">Scale down on-premises datacenters</span></span>
    
    <span data-ttu-id="51c7a-127">Datacenter Contoso contenere centinaia di server, alcuni dei quali esegue legacy o archiviazione funzioni che distrarre il personale IT di gestione dei carichi di lavoro valore elevato per l'azienda.</span><span class="sxs-lookup"><span data-stu-id="51c7a-127">The Contoso datacenters contain hundreds of servers, some of which are running legacy or archival functions that distract IT staff from maintaining high business value workloads.</span></span>
    
6. <span data-ttu-id="51c7a-128">Risorse di elaborazione e di archiviazione di implementare la scalabilità verticale per l'elaborazione di fine del quarto</span><span class="sxs-lookup"><span data-stu-id="51c7a-128">Scale-up computing and storage resources for end-of-quarter processing</span></span>
    
    <span data-ttu-id="51c7a-129">Proiezione di elaborazione e gestione dell'inventario e contabilità fine del quarto è necessario aumentare a breve termine nel server e archiviazione.</span><span class="sxs-lookup"><span data-stu-id="51c7a-129">End-of-quarter financial accounting and projection processing along with inventory management requires short-term increases in servers and storage.</span></span>
    
## <a name="mapping-contosos-business-needs-to-microsofts-cloud-offerings"></a><span data-ttu-id="51c7a-130">Mapping aziendali di Contoso è necessario offerte cloud di Microsoft</span><span class="sxs-lookup"><span data-stu-id="51c7a-130">Mapping Contoso's business needs to Microsoft's cloud offerings</span></span>

<span data-ttu-id="51c7a-131">Basato su un'analisi delle offerte cloud di Microsoft, Contoso del reparto IT determinato il mapping seguente:</span><span class="sxs-lookup"><span data-stu-id="51c7a-131">Based on an analysis of Microsoft's cloud offerings, Contoso's IT department determined the following mapping:</span></span>
  
|<span data-ttu-id="51c7a-132">**Software come servizio (SaaS)**</span><span class="sxs-lookup"><span data-stu-id="51c7a-132">**Software as a Service (SaaS)**</span></span>|<span data-ttu-id="51c7a-133">**Piattaforma as a Service (PaaS Azure)**</span><span class="sxs-lookup"><span data-stu-id="51c7a-133">**Platform as a Service (Azure PaaS )**</span></span>|<span data-ttu-id="51c7a-134">**Infrastructure as a Service (Azure IaaS)**</span><span class="sxs-lookup"><span data-stu-id="51c7a-134">**Infrastructure as a Service (Azure IaaS )**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="51c7a-135">**Office 365:** Applicazioni di principale per la produttività personale e di gruppo nel cloud.</span><span class="sxs-lookup"><span data-stu-id="51c7a-135">**Office 365:** Primary personal and group productivity applications in the cloud.</span></span> <br/> <span data-ttu-id="51c7a-136">Le esigenze aziendali: 1 3 5</span><span class="sxs-lookup"><span data-stu-id="51c7a-136">Business needs: 1 3 5</span></span>  <br/> |<span data-ttu-id="51c7a-137">Ospitare vendite e supporto di documenti e informazioni sui sistemi utilizzando applicazioni basate su cloud.</span><span class="sxs-lookup"><span data-stu-id="51c7a-137">Host sales and support documents and information systems using cloud-based apps.</span></span>  <br/> <span data-ttu-id="51c7a-138">Esigenza azienda: 3</span><span class="sxs-lookup"><span data-stu-id="51c7a-138">Business need: 3</span></span>  <br/> |<span data-ttu-id="51c7a-139">Spostare i sistemi legacy e archiviare i server basati su cloud.</span><span class="sxs-lookup"><span data-stu-id="51c7a-139">Move archival and legacy systems to cloud-based servers.</span></span>  <br/> <span data-ttu-id="51c7a-140">Esigenza azienda: 5</span><span class="sxs-lookup"><span data-stu-id="51c7a-140">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="51c7a-p102">**Dynamics 365:** Utilizzare la gestione di fornitori e clienti basata su cloud. Rimuovere partner extranet nella DMZ.</span><span class="sxs-lookup"><span data-stu-id="51c7a-p102">**Dynamics 365:** Use cloud-based customer and vendor management. Remove partner extranet in the DMZ. </span></span><br/> <span data-ttu-id="51c7a-143">Esigenza azienda: 2</span><span class="sxs-lookup"><span data-stu-id="51c7a-143">Business need: 2</span></span>  <br/> |<span data-ttu-id="51c7a-144">Applicazioni per dispositivi mobili sono basati sul cloud, anziché Parigi basate su Data Center.</span><span class="sxs-lookup"><span data-stu-id="51c7a-144">Mobile applications are cloud-based, rather than Paris datacenter-based.</span></span>  <br/> <span data-ttu-id="51c7a-145">Le esigenze aziendali: 4 3</span><span class="sxs-lookup"><span data-stu-id="51c7a-145">Business needs: 3 4</span></span>  <br/> |<span data-ttu-id="51c7a-146">Eseguire la migrazione dei dati da centri dati locali e le applicazioni di utilizzo poco.</span><span class="sxs-lookup"><span data-stu-id="51c7a-146">Migrate low-use apps and data out of on-premises datacenters.</span></span>  <br/> <span data-ttu-id="51c7a-147">Esigenza azienda: 5</span><span class="sxs-lookup"><span data-stu-id="51c7a-147">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="51c7a-148">**Intune/EMS:** Gestire iOS e dispositivi Android.</span><span class="sxs-lookup"><span data-stu-id="51c7a-148">**Intune/EMS:** Manage iOS and Android devices.</span></span> <br/> <span data-ttu-id="51c7a-149">Esigenza azienda: 3</span><span class="sxs-lookup"><span data-stu-id="51c7a-149">Business need: 3</span></span>  <br/> ||<span data-ttu-id="51c7a-150">Aggiungere server temporanei e archiviazione per esigenze di elaborazione di fine del trimestre.</span><span class="sxs-lookup"><span data-stu-id="51c7a-150">Add temporary servers and storage for end-of-quarter processing needs.</span></span>  <br/> <span data-ttu-id="51c7a-151">Esigenza azienda: 6</span><span class="sxs-lookup"><span data-stu-id="51c7a-151">Business need: 6</span></span>  <br/> |
   
## <a name="see-also"></a><span data-ttu-id="51c7a-152">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="51c7a-152">See Also</span></span>

[<span data-ttu-id="51c7a-153">Contoso nel Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="51c7a-153">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="51c7a-154">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="51c7a-154">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="51c7a-155">Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT</span><span class="sxs-lookup"><span data-stu-id="51c7a-155">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


