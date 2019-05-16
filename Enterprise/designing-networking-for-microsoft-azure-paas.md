---
title: Progettazione di rete per Microsoft Azure PaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: "Riepilogo: informazioni su come ottimizzare la rete per l'accesso a Microsoft Azure PaaS."
ms.openlocfilehash: fafc3de1c5f755e891da6c07ae8993fb869bc5e1
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067822"
---
# <a name="designing-networking-for-microsoft-azure-paas"></a><span data-ttu-id="1d7be-103">Progettazione di rete per Microsoft Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="1d7be-103">Designing networking for Microsoft Azure PaaS</span></span>

 <span data-ttu-id="1d7be-104">**Riepilogo:** Informazioni su come ottimizzare la rete per l'accesso a Microsoft Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="1d7be-104">**Summary:** Understand how to optimize your network for access to Microsoft Azure PaaS.</span></span>
  
<span data-ttu-id="1d7be-105">L'ottimizzazione della rete per le app PaaS di Azure necessita di una larghezza di banda Internet adeguata e può richiedere la distribuzione del traffico di rete in più siti o app.</span><span class="sxs-lookup"><span data-stu-id="1d7be-105">Optimizing networking for Azure PaaS apps requires adequate Internet bandwidth and can require the distribution of network traffic across multiple sites or apps.</span></span>
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a><span data-ttu-id="1d7be-106">Procedura di pianificazione per l'hosting di applicazioni PaaS dell'organizzazione in Azure</span><span class="sxs-lookup"><span data-stu-id="1d7be-106">Planning steps for hosting organization PaaS applications in Azure</span></span>

1. <span data-ttu-id="1d7be-107">Consultare la sezione **Procedura per predisporre la rete per i servizi cloud Microsoft** in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="1d7be-107">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="1d7be-108">Ottimizzare la larghezza di banda Internet utilizzando i passaggi 2-4 della **procedura per preparare la rete per i servizi SaaS di Microsoft** nella sezione [progettazione di rete per Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span><span class="sxs-lookup"><span data-stu-id="1d7be-108">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
    
3. <span data-ttu-id="1d7be-109">Determinare se è necessaria una connessione di ExpressRoute a Azure.</span><span class="sxs-lookup"><span data-stu-id="1d7be-109">Determine whether you need an ExpressRoute connection to Azure.</span></span>
    
4. <span data-ttu-id="1d7be-110">Per i carichi di lavoro basati sul Web, determinare se è necessario il gateway dell'applicazione Azure.</span><span class="sxs-lookup"><span data-stu-id="1d7be-110">For web-based workloads, determine whether you need the Azure Application Gateway.</span></span>
    
5. <span data-ttu-id="1d7be-111">Per la distribuzione del traffico verso endpoint diversi in diversi Data Center, determinare se è necessario Azure Traffic Manager.</span><span class="sxs-lookup"><span data-stu-id="1d7be-111">For distribution of traffic to different endpoints in different data centers, determine whether you need Azure Traffic Manager.</span></span>
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a><span data-ttu-id="1d7be-112">Larghezza di banda Internet per le applicazioni di PaaS dell'organizzazione</span><span class="sxs-lookup"><span data-stu-id="1d7be-112">Internet bandwidth for organization PaaS applications</span></span>

<span data-ttu-id="1d7be-113">Le applicazioni dell'organizzazione ospitate in Azure PaaS richiedono la larghezza di banda Internet per gli utenti Intranet.</span><span class="sxs-lookup"><span data-stu-id="1d7be-113">Organization applications hosted in Azure PaaS require Internet bandwidth for intranet users.</span></span> <span data-ttu-id="1d7be-114">Esistono due opzioni:</span><span class="sxs-lookup"><span data-stu-id="1d7be-114">There are two options:</span></span>
  
- <span data-ttu-id="1d7be-115">**Opzione 1:** Utilizzare la tubazione esistente, ottimizzata per il traffico Internet con la capacità di gestire i carichi di picco.</span><span class="sxs-lookup"><span data-stu-id="1d7be-115">**Option 1:** Use your existing pipe, optimized for Internet traffic with the capacity to handle peak loads.</span></span> <span data-ttu-id="1d7be-116">Vedere[progettazione della rete per](designing-networking-for-microsoft-saas.md) le considerazioni relative a Microsoft SaaS per Internet Edge, utilizzo client e operazioni it.</span><span class="sxs-lookup"><span data-stu-id="1d7be-116">See[Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md) for Internet edge, client usage, and IT operations considerations.</span></span>
    
- <span data-ttu-id="1d7be-117">**Opzione 2:** Per le esigenze di bassa latenza e larghezza di banda elevata, utilizzare una connessione ExpressRoute a Azure.</span><span class="sxs-lookup"><span data-stu-id="1d7be-117">**Option 2:** For high-bandwidth or low latency needs, use an ExpressRoute connection to Azure.</span></span>
    
<span data-ttu-id="1d7be-118">**Figura 1: opzioni di connessione per la connessione dei servizi di PaaS di Azure**</span><span class="sxs-lookup"><span data-stu-id="1d7be-118">**Figure 1: Connection options for connecting the Azure PaaS services**</span></span>

![Figura 1: opzioni di connessione per i servizi di PaaS di Azure](media/Network-Poster/PaaS1.png)
  
<span data-ttu-id="1d7be-120">Nella figura 1 viene illustrata una rete locale che si connette ai servizi di PaaS di Azure su una pipe Internet o ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="1d7be-120">Figure 1 shows an on-premises network connecting to Azure PaaS services over an Internet pipe or ExpressRoute.</span></span>
  
## <a name="azure-application-gateway"></a><span data-ttu-id="1d7be-121">Gateway dell'applicazione di Azure</span><span class="sxs-lookup"><span data-stu-id="1d7be-121">Azure Application Gateway</span></span>

<span data-ttu-id="1d7be-122">Servizi di routing a livello di applicazione e di bilanciamento del carico che consentono di creare un front-end Web scalabile e a disponibilità elevata in Azure per le applicazioni Web, i servizi cloud e le macchine virtuali.</span><span class="sxs-lookup"><span data-stu-id="1d7be-122">Application-level routing and load balancing services that let you build a scalable and highly-available web front end in Azure for web apps, cloud services, and virtual machines.</span></span> 
  
<span data-ttu-id="1d7be-123">**Figura 2: gateway di applicazioni di Azure**</span><span class="sxs-lookup"><span data-stu-id="1d7be-123">**Figure 2: Azure Application Gateway**</span></span>

![Figura 2: servizio gateway dell'applicazione Azure](media/Network-Poster/PaaS2.png)
  
<span data-ttu-id="1d7be-125">Nella figura 2 viene mostrato il gateway dell'applicazione di Azure e come le richieste degli utenti da Internet possono essere instradate a Azure Web Apps, servizi cloud o macchine virtuali.</span><span class="sxs-lookup"><span data-stu-id="1d7be-125">Figure 2 shows the Azure Application Gateway and how user requests from the Internet can be routed to Azure web apps, cloud services, or virtual machines.</span></span>
  
<span data-ttu-id="1d7be-126">Il gateway applicazione supporta attualmente il recapito delle applicazioni Layer 7 per gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="1d7be-126">Application Gateway currently supports layer 7 application delivery for the following:</span></span>
  
- <span data-ttu-id="1d7be-127">Bilanciamento del carico HTTP</span><span class="sxs-lookup"><span data-stu-id="1d7be-127">HTTP load balancing</span></span>
    
- <span data-ttu-id="1d7be-128">Affinità di sessione basata su cookie</span><span class="sxs-lookup"><span data-stu-id="1d7be-128">Cookie-based session affinity</span></span>
    
- <span data-ttu-id="1d7be-129">Offload SSL</span><span class="sxs-lookup"><span data-stu-id="1d7be-129">SSL offload</span></span>
    
<span data-ttu-id="1d7be-130">Per ulteriori informazioni, vedere [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span><span class="sxs-lookup"><span data-stu-id="1d7be-130">For more information, see [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span></span>
  
## <a name="azure-traffic-manager"></a><span data-ttu-id="1d7be-131">Azure Traffic Manager</span><span class="sxs-lookup"><span data-stu-id="1d7be-131">Azure Traffic Manager</span></span>

<span data-ttu-id="1d7be-132">Distribuzione del traffico verso endpoint diversi, che possono includere servizi cloud o Azure Web Apps ubicati in diversi Data Center o endpoint esterni.</span><span class="sxs-lookup"><span data-stu-id="1d7be-132">Distribution of traffic to different endpoints, which can include cloud services or Azure web apps located in different data centers or external endpoints.</span></span>
  
<span data-ttu-id="1d7be-133">Traffic Manager utilizza i seguenti metodi di routing:</span><span class="sxs-lookup"><span data-stu-id="1d7be-133">Traffic Manager uses the following routing methods:</span></span>
  
- <span data-ttu-id="1d7be-134">**Failover:** Gli endpoint sono nello stesso datacenter di Azure o in altri centri dati e si desidera utilizzare un endpoint primario per tutto il traffico, ma fornire backup nel caso in cui gli endpoint primari o di backup non siano disponibili.</span><span class="sxs-lookup"><span data-stu-id="1d7be-134">**Failover:** The endpoints are in the same or different Azure datacenters and you want to use a primary endpoint for all traffic, but provide backups in case the primary or the backup endpoints are unavailable.</span></span>
    
- <span data-ttu-id="1d7be-135">**Round Robin:** Si desidera distribuire il carico in un set di endpoint nello stesso datacenter o in diversi datacenter.</span><span class="sxs-lookup"><span data-stu-id="1d7be-135">**Round robin:** You want to distribute load across a set of endpoints in the same datacenter or across different datacenters.</span></span>
    
- <span data-ttu-id="1d7be-136">**Prestazioni:** Si dispone di endpoint in diverse posizioni geografiche e si desidera richiedere ai client di utilizzare l'endpoint "più vicino" in termini di latenza più bassa.</span><span class="sxs-lookup"><span data-stu-id="1d7be-136">**Performance:** You have endpoints in different geographic locations and you want requesting clients to use the "closest" endpoint in terms of the lowest latency.</span></span>
    
<span data-ttu-id="1d7be-137">Di seguito è riportato un esempio per tre app Web geograficamente distribuite.</span><span class="sxs-lookup"><span data-stu-id="1d7be-137">Here is an example for three geographically-distributed web apps.</span></span>
  
<span data-ttu-id="1d7be-138">**Figura 3: gestione traffico di Azure**</span><span class="sxs-lookup"><span data-stu-id="1d7be-138">**Figure 3: Azure Traffic Manager**</span></span>

![Figura 3: gestione traffico di Azure](media/Network-Poster/PaaS3.png)
  
<span data-ttu-id="1d7be-140">Nella figura 3 viene illustrato il processo di base utilizzato da Traffic Manager per instradare le richieste a tre diverse app Web di Azure in Stati Uniti, Europa e Asia.</span><span class="sxs-lookup"><span data-stu-id="1d7be-140">Figure 3 shows the basic process that Traffic Manager uses to route requests to three different Azure web apps in United States, Europe, and Asia.</span></span> <span data-ttu-id="1d7be-141">Nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="1d7be-141">In the example:</span></span>
  
1. <span data-ttu-id="1d7be-142">Una query DNS dell'utente per l'URL di un sito Web viene indirizzata a Azure Traffic Manager, che restituisce il nome di un'app web regionale, in base al metodo di routing delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="1d7be-142">A user DNS query for a web site URL gets directed to Azure Traffic Manager, which returns the name of a regional web app, based on the performance routing method.</span></span>
    
2. <span data-ttu-id="1d7be-143">L'utente avvia il traffico con l'app web regionale in Europa.</span><span class="sxs-lookup"><span data-stu-id="1d7be-143">The user initiates traffic with the regional web app in Europe.</span></span>
    
<span data-ttu-id="1d7be-144">Per ulteriori informazioni, vedere [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="1d7be-144">For more information, see [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="next-step"></a><span data-ttu-id="1d7be-145">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="1d7be-145">Next step</span></span>

[<span data-ttu-id="1d7be-146">Progettazione di rete per Microsoft Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="1d7be-146">Designing networking for Microsoft Azure IaaS</span></span>](designing-networking-for-microsoft-azure-iaas.md)
 
## <a name="see-also"></a><span data-ttu-id="1d7be-147">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1d7be-147">See also</span></span>

[<span data-ttu-id="1d7be-148">Rete di Microsoft Cloud per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="1d7be-148">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="1d7be-149">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="1d7be-149">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

