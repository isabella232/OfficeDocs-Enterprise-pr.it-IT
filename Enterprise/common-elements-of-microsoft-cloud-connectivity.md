---
title: "Elementi comuni della connettività cloud Microsoft"
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
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: 'Riepilogo: Informazioni su come preparare la rete e gli elementi comuni dell''infrastruttura di rete.'
ms.openlocfilehash: 9dffcae28283c9f8b8c219284554225645435e0a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a><span data-ttu-id="b8f1f-103">Elementi comuni della connettività cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="b8f1f-103">Common elements of Microsoft cloud connectivity</span></span>

 <span data-ttu-id="b8f1f-104">**Riepilogo:** Informazioni su come preparare la rete e gli elementi comuni dell'infrastruttura di rete.</span><span class="sxs-lookup"><span data-stu-id="b8f1f-104">**Summary:** Understand the common elements of networking infrastructure and how to prepare your network.</span></span>
  
<span data-ttu-id="b8f1f-105">L'integrazione della rete con il cloud di Microsoft consente di accedere facilmente a una vasta gamma di servizi.</span><span class="sxs-lookup"><span data-stu-id="b8f1f-105">Integrating your networking with the Microsoft cloud provides optimal access to a broad range of services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a><span data-ttu-id="b8f1f-106">Passaggi per preparare la rete di servizi cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="b8f1f-106">Steps to prepare your network for Microsoft cloud services</span></span>
<span data-ttu-id="b8f1f-107"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="b8f1f-107"></span></span>

<span data-ttu-id="b8f1f-108">Per la rete locale:</span><span class="sxs-lookup"><span data-stu-id="b8f1f-108">For your on-premises network:</span></span>
  
1. <span data-ttu-id="b8f1f-109">Analizzare i computer client e ottimizzare per l'hardware di rete, driver software, le impostazioni del protocollo e browser Internet.</span><span class="sxs-lookup"><span data-stu-id="b8f1f-109">Analyze your client computers and optimize for network hardware, software drivers, protocol settings, and Internet browsers.</span></span>
    
2. <span data-ttu-id="b8f1f-110">Analisi della rete locale per il traffico latenza e il routing ottimale per il dispositivo edge Internet.</span><span class="sxs-lookup"><span data-stu-id="b8f1f-110">Analyze your on-premises network for traffic latency and optimal routing to the Internet edge device.</span></span>
    
3. <span data-ttu-id="b8f1f-111">Analizzare le capacità e prestazioni del dispositivo edge Internet e ottimizzare per più alti livelli di traffico.</span><span class="sxs-lookup"><span data-stu-id="b8f1f-111">Analyze the capacity and performance of your Internet edge device and optimize for higher levels of traffic.</span></span>
    
<span data-ttu-id="b8f1f-112">Per la connessione a Internet:</span><span class="sxs-lookup"><span data-stu-id="b8f1f-112">For your Internet connection:</span></span>
  
1. <span data-ttu-id="b8f1f-113">Analizzare la latenza tra il dispositivo edge Internet (ad esempio, il firewall esterno) e i percorsi regionali del servizio cloud Microsoft a cui si effettua la connessione.</span><span class="sxs-lookup"><span data-stu-id="b8f1f-113">Analyze the latency between your Internet edge device (such as your external firewall) and the regional locations of the Microsoft cloud service to which you are connecting.</span></span>
    
2. <span data-ttu-id="b8f1f-p101">Analizzare le capacità e l'utilizzo della connessione Internet corrente e, se necessario, aggiungere capacità. In alternativa, aggiungere una connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="b8f1f-p101">Analyze the capacity and utilization of your current Internet connection and add capacity if needed. Alternately, add an ExpressRoute connection.</span></span>
    
## <a name="microsoft-cloud-connectivity-options"></a><span data-ttu-id="b8f1f-116">Opzioni di integrazione applicativa Microsoft cloud</span><span class="sxs-lookup"><span data-stu-id="b8f1f-116">Microsoft cloud connectivity options</span></span>
<span data-ttu-id="b8f1f-117"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="b8f1f-117"></span></span>

<span data-ttu-id="b8f1f-118">Utilizzare il canale Internet esistente o una connessione ExpressRoute a Office 365 e Azure Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="b8f1f-118">Use your existing Internet pipe or an ExpressRoute connection to Office 365, Azure, and Dynamics 365.</span></span>
  
<span data-ttu-id="b8f1f-119">**Figura 1: Opzioni per la connettività cloud Microsoft**</span><span class="sxs-lookup"><span data-stu-id="b8f1f-119">**Figure 1: Options for Microsoft cloud connectivity**</span></span>

![Figura 1:  Opzioni per la connettività di Microsoft Cloud](images/Network_Poster/CommonElements.png)

  
<span data-ttu-id="b8f1f-p102">Nella figura 1 viene illustrato come una rete locale può essere connesso a offerte cloud Microsoft utilizzando la propria pipe Internet esistente o ExpressRoute. Il canale Internet rappresenta una DMZ e può avere i seguenti componenti:</span><span class="sxs-lookup"><span data-stu-id="b8f1f-p102">Figure 1 shows how an on-premises network can be connected to Microsoft cloud offerings using their existing Internet pipe or ExpressRoute. The Internet pipe represents a DMZ and can have the following components:</span></span>
  
- <span data-ttu-id="b8f1f-p103">**Firewall interno:** Barriera tra la rete attendibile e uno non attendibile. Esegue il traffico filtro (in base alle regole) e il monitoraggio.</span><span class="sxs-lookup"><span data-stu-id="b8f1f-p103">**Internal firewall:** A barrier between your trusted network and an untrusted one. Performs traffic filtering (based on rules) and monitoring.</span></span>
    
- <span data-ttu-id="b8f1f-125">**Il carico di lavoro esterno:** Siti Web o altri carichi di lavoro rese disponibili per gli utenti esterni su Internet.</span><span class="sxs-lookup"><span data-stu-id="b8f1f-125">**External workload:** Web sites or other workloads made available to external users on the Internet.</span></span>
    
- <span data-ttu-id="b8f1f-p104">**Server proxy:** Gestisce le richieste di contenuto web per conto degli utenti intranet. Un proxy inverso consente le richieste in ingresso non richiesto.</span><span class="sxs-lookup"><span data-stu-id="b8f1f-p104">**Proxy server:** Services requests for web content on behalf of intranet users. A reverse proxy allows unsolicited inbound requests.</span></span>
    
- <span data-ttu-id="b8f1f-p105">**Firewall esterno:** Consente il traffico in uscita e il traffico in ingresso specificato. Consente di eseguire conversione degli indirizzi.</span><span class="sxs-lookup"><span data-stu-id="b8f1f-p105">**External firewall:** Allows outbound traffic and specified inbound traffic. Can perform address translation.</span></span>
    
- <span data-ttu-id="b8f1f-130">**Connessione WAN al provider di servizi Internet:** Una connessione basata su gestore di telefonia per un provider di servizi Internet, che peer per il routing e la connettività Internet.</span><span class="sxs-lookup"><span data-stu-id="b8f1f-130">**WAN connection to ISP:** A carrier-based connection to an ISP, who peers with the Internet for connectivity and routing.</span></span>
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a><span data-ttu-id="b8f1f-131">Aree di rete comune a tutti i servizi cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="b8f1f-131">Areas of networking common to all Microsoft cloud services</span></span>
<span data-ttu-id="b8f1f-132"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="b8f1f-132"></span></span>

<span data-ttu-id="b8f1f-133">È necessario prendere in considerazione queste aree di rete adottando uno dei servizi cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b8f1f-133">You need to consider these areas of networking when adopting any of Microsoft's cloud services.</span></span>
  
- <span data-ttu-id="b8f1f-134">**Delle prestazioni di rete intranet:** Per le risorse basate su Internet rallentamento delle prestazioni se la rete intranet, tra cui i computer client, non è ottimizzata.</span><span class="sxs-lookup"><span data-stu-id="b8f1f-134">**Intranet performance:** Performance to Internet-based resources will suffer if your intranet, including client computers, is not optimized.</span></span>
    
- <span data-ttu-id="b8f1f-135">**Dispositivi di server perimetrali:** Dispositivi in corrispondenza del bordo della rete sono i punti di uscita e possono includere (Network Address Translator), server proxy (inclusi i proxy inversi), i firewall, i dispositivi di rilevamento delle intrusioni o una combinazione.</span><span class="sxs-lookup"><span data-stu-id="b8f1f-135">**Edge devices:** Devices at the edge of your network are egress points and can include Network Address Translators (NATs), proxy servers (including reverse proxies), firewalls, intrusion detection devices, or a combination.</span></span>
    
- <span data-ttu-id="b8f1f-p106">**Connessione Internet:** Connessione WAN al provider di servizi Internet e Internet dovrebbe avere sufficiente capacità per gestire i carichi di picco. È inoltre possibile utilizzare una connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="b8f1f-p106">**Internet connection:** Your WAN connection to your ISP and the Internet should have enough capacity to handle peak loads. You can also use an ExpressRoute connection.</span></span>
    
- <span data-ttu-id="b8f1f-p107">**Internet DNS:** A, AAAA, CNAME, MX, PTR e altri record per individuare Microsoft cloud o i servizi ospitati nel cloud. Ad esempio, si potrebbe essere necessario un record CNAME per l'app ospitate in Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="b8f1f-p107">**Internet DNS:** A, AAAA, CNAME, MX, PTR and other records to locate Microsoft cloud or your services hosted in the cloud. For example, you might need a CNAME record for your app hosted in Azure PaaS.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="b8f1f-140">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b8f1f-140">See Also</span></span>

<span data-ttu-id="b8f1f-141"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="b8f1f-141"></span></span>

[<span data-ttu-id="b8f1f-142">Rete cloud Microsoft per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="b8f1f-142">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="b8f1f-143">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="b8f1f-143">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="b8f1f-144">Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT</span><span class="sxs-lookup"><span data-stu-id="b8f1f-144">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


