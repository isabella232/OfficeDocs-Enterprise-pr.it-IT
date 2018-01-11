---
title: Progettazione di rete per Microsoft Azure PaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: 'Riepilogo: Informazioni su come ottimizzare la rete per l''accesso a Microsoft Azure PaaS.'
ms.openlocfilehash: 8ea344b5c18f9224b1a939a05c6e5a4eda2eeec5
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="designing-networking-for-microsoft-azure-paas"></a><span data-ttu-id="dfbd2-103">Progettazione di rete per Microsoft Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="dfbd2-103">Designing networking for Microsoft Azure PaaS</span></span>

 <span data-ttu-id="dfbd2-104">**Riepilogo:** Informazioni su come ottimizzare la rete per l'accesso a Microsoft Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="dfbd2-104">**Summary:** Understand how to optimize your network for access to Microsoft Azure PaaS.</span></span>
  
<span data-ttu-id="dfbd2-105">L'ottimizzazione della rete per le app PaaS di Azure necessita di una larghezza di banda Internet adeguata e può richiedere la distribuzione del traffico di rete in più siti o app.</span><span class="sxs-lookup"><span data-stu-id="dfbd2-105">Optimizing networking for Azure PaaS apps requires adequate Internet bandwidth and can require the distribution of network traffic across multiple sites or apps.</span></span>
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a><span data-ttu-id="dfbd2-106">Passaggi di pianificazione per l'hosting di applicazioni PaaS organizzazione in Azure</span><span class="sxs-lookup"><span data-stu-id="dfbd2-106">Planning steps for hosting organization PaaS applications in Azure</span></span>

<span data-ttu-id="dfbd2-107">Inserire qui il corpo della sezione.</span><span class="sxs-lookup"><span data-stu-id="dfbd2-107">Insert section body here.</span></span>
  
1. <span data-ttu-id="dfbd2-108">Passare attraverso la sezione **operazioni per preparare la rete di servizi cloud Microsoft** in [elementi comuni di integrazione applicativa di Microsoft cloud](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="dfbd2-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="dfbd2-109">Ottimizzare la larghezza di banda Internet utilizzando i passaggi da 2 a 4 della sezione **passaggi per la preparazione della rete per i servizi Microsoft SaaS** nella [Progettazione di rete per Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span><span class="sxs-lookup"><span data-stu-id="dfbd2-109">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
    
3. <span data-ttu-id="dfbd2-110">Stabilire se sono necessari una connessione ExpressRoute in Azure.</span><span class="sxs-lookup"><span data-stu-id="dfbd2-110">Determine whether you need an ExpressRoute connection to Azure.</span></span>
    
4. <span data-ttu-id="dfbd2-111">Per carichi di lavoro basate sul web, determinare se è necessario Azure Application Gateway.</span><span class="sxs-lookup"><span data-stu-id="dfbd2-111">For web-based workloads, determine whether you need the Azure Application Gateway.</span></span>
    
5. <span data-ttu-id="dfbd2-112">Per la distribuzione del traffico agli endpoint diversi nel centro dati diversi, determinare se è necessario Azure Traffic Managerhttp.</span><span class="sxs-lookup"><span data-stu-id="dfbd2-112">For distribution of traffic to different endpoints in different data centers, determine whether you need Azure Traffic Manager.</span></span>
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a><span data-ttu-id="dfbd2-113">Larghezza di banda Internet per le applicazioni PaaS organizzazione</span><span class="sxs-lookup"><span data-stu-id="dfbd2-113">Internet bandwidth for organization PaaS applications</span></span>

<span data-ttu-id="dfbd2-p101">Organizzazione applicazioni ospitate in Azure PaaS richiedono larghezza di banda Internet per gli utenti intranet. Sono disponibili due opzioni:</span><span class="sxs-lookup"><span data-stu-id="dfbd2-p101">Organization applications hosted in Azure PaaS require Internet bandwidth for intranet users. There are two options:</span></span>
  
- <span data-ttu-id="dfbd2-p102">**Opzione 1:** Utilizzare la pipe esistente, ottimizzata per il traffico Internet con la capacità di gestire i carichi di picco. Vedere[Progettazione di rete per Microsoft SaaS](designing-networking-for-microsoft-saas.md) per edge Internet, l'utilizzo di client e considerazioni sulle operazioni IT.</span><span class="sxs-lookup"><span data-stu-id="dfbd2-p102">**Option 1:** Use your existing pipe, optimized for Internet traffic with the capacity to handle peak loads. See[Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md) for Internet edge, client usage, and IT operations considerations.</span></span>
    
- <span data-ttu-id="dfbd2-118">**Opzione 2:** Per ampia larghezza di banda o bassa latenza delle esigenze, utilizzare una connessione ExpressRoute in Azure.</span><span class="sxs-lookup"><span data-stu-id="dfbd2-118">**Option 2:** For high-bandwidth or low latency needs, use an ExpressRoute connection to Azure.</span></span>
    
<span data-ttu-id="dfbd2-119">**Nella figura 1: Opzioni di connessione per la connessione di servizi di Azure PaaS**</span><span class="sxs-lookup"><span data-stu-id="dfbd2-119">**Figure 1: Connection options for connecting the Azure PaaS services**</span></span>

![Figura 1: Opzioni di connessione per i servizi PaaS di Azure](images/Network_Poster/PaaS1.png)
  
<span data-ttu-id="dfbd2-121">Una rete locale la connessione a servizi di Azure PaaS attraverso un canale Internet o ExpressRoute illustrato nella figura 1.</span><span class="sxs-lookup"><span data-stu-id="dfbd2-121">Figure 1 shows an on-premises network connecting to Azure PaaS services over an Internet pipe or ExpressRoute.</span></span>
  
## <a name="azure-application-gateway"></a><span data-ttu-id="dfbd2-122">Azure Application Gateway</span><span class="sxs-lookup"><span data-stu-id="dfbd2-122">Azure Application Gateway</span></span>

<span data-ttu-id="dfbd2-123">Livello di applicazione di routing e il bilanciamento del carico servizi che consentono di creare un soluzione scalabile e altamente disponibile front-end web in Azure per applicazioni web, servizi cloud e macchine virtuali.</span><span class="sxs-lookup"><span data-stu-id="dfbd2-123">Application-level routing and load balancing services that let you build a scalable and highly-available web front end in Azure for web apps, cloud services, and virtual machines.</span></span> 
  
<span data-ttu-id="dfbd2-124">**Figura 2: Applicazioni Azure Gateway**</span><span class="sxs-lookup"><span data-stu-id="dfbd2-124">**Figure 2: Azure Application Gateway**</span></span>

![Figura 2: Servizio Gateway di applicazioni Azure](images/Network_Poster/PaaS2.png)
  
<span data-ttu-id="dfbd2-126">Nella figura 2 viene Azure Application Gateway e come utente richiede da Internet può essere instradate a Azure web App, servizi cloud o macchine virtuali.</span><span class="sxs-lookup"><span data-stu-id="dfbd2-126">Figure 2 shows the Azure Application Gateway and how user requests from the Internet can be routed to Azure web apps, cloud services, or virtual machines.</span></span>
  
<span data-ttu-id="dfbd2-127">Application Gateway attualmente supporta il recapito di livello applicazione 7 per le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="dfbd2-127">Application Gateway currently supports layer 7 application delivery for the following:</span></span>
  
- <span data-ttu-id="dfbd2-128">Bilanciamento del carico HTTP</span><span class="sxs-lookup"><span data-stu-id="dfbd2-128">HTTP load balancing</span></span>
    
- <span data-ttu-id="dfbd2-129">Affinità basata sui cookie di sessione</span><span class="sxs-lookup"><span data-stu-id="dfbd2-129">Cookie-based session affinity</span></span>
    
- <span data-ttu-id="dfbd2-130">Offload SSL</span><span class="sxs-lookup"><span data-stu-id="dfbd2-130">SSL offload</span></span>
    
<span data-ttu-id="dfbd2-131">Per ulteriori informazioni, vedere [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span><span class="sxs-lookup"><span data-stu-id="dfbd2-131">For more information, see [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span></span>
  
## <a name="azure-traffic-manager"></a><span data-ttu-id="dfbd2-132">Azure Traffic Manager</span><span class="sxs-lookup"><span data-stu-id="dfbd2-132">Azure Traffic Manager</span></span>

<span data-ttu-id="dfbd2-133">Distribuzione del traffico a endpoint distinti, che può includere servizi cloud o applicazioni web Azure in datacenter diversi oppure endpoint esterno.</span><span class="sxs-lookup"><span data-stu-id="dfbd2-133">Distribution of traffic to different endpoints, which can include cloud services or Azure web apps located in different data centers or external endpoints.</span></span>
  
<span data-ttu-id="dfbd2-134">Gestione del traffico vengono utilizzati i metodi di distribuzione seguenti:</span><span class="sxs-lookup"><span data-stu-id="dfbd2-134">Traffic Manager uses the following routing methods:</span></span>
  
- <span data-ttu-id="dfbd2-135">**Failover:** I punti finali sono nei data center Azure uguali o diversi e si desidera utilizzare un endpoint principale per tutto il traffico, ma fornisce backup nel caso in cui l'endpoint backup o il primario non sono disponibili.</span><span class="sxs-lookup"><span data-stu-id="dfbd2-135">**Failover:** The endpoints are in the same or different Azure datacenters and you want to use a primary endpoint for all traffic, but provide backups in case the primary or the backup endpoints are unavailable.</span></span>
    
- <span data-ttu-id="dfbd2-136">**Round robin:** Si desidera distribuire il carico in una serie di endpoint nello stesso datacenter o tra i datacenter diversi.</span><span class="sxs-lookup"><span data-stu-id="dfbd2-136">**Round robin:** You want to distribute load across a set of endpoints in the same datacenter or across different datacenters.</span></span>
    
- <span data-ttu-id="dfbd2-137">**Prestazioni:** Sono presenti endpoint in posizioni geografiche diverse e si desidera richiedente ai client di utilizzare l'endpoint "più vicino" in termini di più bassa latenza.</span><span class="sxs-lookup"><span data-stu-id="dfbd2-137">**Performance:** You have endpoints in different geographic locations and you want requesting clients to use the "closest" endpoint in terms of the lowest latency.</span></span>
    
<span data-ttu-id="dfbd2-138">Di seguito è riportato un esempio di tre distribuiti geograficamente web app.</span><span class="sxs-lookup"><span data-stu-id="dfbd2-138">Here is an example for three geographically-distributed web apps.</span></span>
  
<span data-ttu-id="dfbd2-139">**Figura 3: Azure Traffic Managerhttp**</span><span class="sxs-lookup"><span data-stu-id="dfbd2-139">**Figure 3: Azure Traffic Manager**</span></span>

![Figura 3: Gestione traffico di Azure](images/Network_Poster/PaaS3.png)
  
<span data-ttu-id="dfbd2-p103">Nella figura 3 viene illustrato il processo di base di gestione del traffico viene utilizzato per instradare le richieste per le applicazioni web diverse Azure tre negli Stati Uniti, Europa e Asia. Nell'esempio:</span><span class="sxs-lookup"><span data-stu-id="dfbd2-p103">Figure 3 shows the basic process that Traffic Manager uses to route requests to three different Azure web apps in United States, Europe, and Asia. In the example:</span></span>
  
1. <span data-ttu-id="dfbd2-143">Una query DNS utente per un sito web che URL Ottiene indirizzati a Azure Traffic Managerhttp, che restituisce il nome di un'app web regionali, in base il metodo di routing delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="dfbd2-143">A user DNS query for a web site URL gets directed to Azure Traffic Manager, which returns the name of a regional web app, based on the performance routing method.</span></span>
    
2. <span data-ttu-id="dfbd2-144">L'utente avvia il traffico con l'app web internazionali in Europa.</span><span class="sxs-lookup"><span data-stu-id="dfbd2-144">The user initiates traffic with the regional web app in Europe.</span></span>
    
<span data-ttu-id="dfbd2-145">Per ulteriori informazioni, vedere [Gestione del traffico](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="dfbd2-145">For more information, see [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dfbd2-146">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dfbd2-146">See Also</span></span>

[<span data-ttu-id="dfbd2-147">Rete cloud Microsoft per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="dfbd2-147">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="dfbd2-148">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="dfbd2-148">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="dfbd2-149">Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT</span><span class="sxs-lookup"><span data-stu-id="dfbd2-149">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



