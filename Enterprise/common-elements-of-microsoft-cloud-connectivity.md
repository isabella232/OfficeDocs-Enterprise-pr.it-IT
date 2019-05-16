---
title: Elementi comuni della connettività cloud Microsoft
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
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: "Riepilogo: informazioni sugli elementi comuni dell'infrastruttura di rete e su come preparare la rete."
ms.openlocfilehash: f092e3fb0a2f009aa7c6bbb14229fe98b35700ea
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068112"
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a><span data-ttu-id="5d61a-103">Elementi comuni della connettività cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="5d61a-103">Common elements of Microsoft cloud connectivity</span></span>

 <span data-ttu-id="5d61a-104">**Riepilogo:** Comprendere gli elementi comuni dell'infrastruttura di rete e come preparare la rete.</span><span class="sxs-lookup"><span data-stu-id="5d61a-104">**Summary:** Understand the common elements of networking infrastructure and how to prepare your network.</span></span>
  
<span data-ttu-id="5d61a-105">L'integrazione della rete con il cloud di Microsoft consente di accedere facilmente a una vasta gamma di servizi.</span><span class="sxs-lookup"><span data-stu-id="5d61a-105">Integrating your networking with the Microsoft cloud provides optimal access to a broad range of services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a><span data-ttu-id="5d61a-106">Passaggi per preparare la rete per i servizi cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="5d61a-106">Steps to prepare your network for Microsoft cloud services</span></span>
<span data-ttu-id="5d61a-107"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="5d61a-107"></span></span>

<span data-ttu-id="5d61a-108">Per la rete locale:</span><span class="sxs-lookup"><span data-stu-id="5d61a-108">For your on-premises network:</span></span>
  
1. <span data-ttu-id="5d61a-109">Analizzare i computer client e ottimizzare l'hardware di rete, i driver software, le impostazioni del protocollo e i browser Internet.</span><span class="sxs-lookup"><span data-stu-id="5d61a-109">Analyze your client computers and optimize for network hardware, software drivers, protocol settings, and Internet browsers.</span></span>
    
2. <span data-ttu-id="5d61a-110">Analizzare la rete locale per la latenza del traffico e il routing ottimale per il dispositivo perimetrale Internet.</span><span class="sxs-lookup"><span data-stu-id="5d61a-110">Analyze your on-premises network for traffic latency and optimal routing to the Internet edge device.</span></span>
    
3. <span data-ttu-id="5d61a-111">Analizzare la capacità e le prestazioni del dispositivo perimetrale Internet e ottimizzare i livelli di traffico più alti.</span><span class="sxs-lookup"><span data-stu-id="5d61a-111">Analyze the capacity and performance of your Internet edge device and optimize for higher levels of traffic.</span></span>
    
<span data-ttu-id="5d61a-112">Per la connessione a Internet:</span><span class="sxs-lookup"><span data-stu-id="5d61a-112">For your Internet connection:</span></span>
  
1. <span data-ttu-id="5d61a-113">Analizzare la latenza tra il dispositivo perimetrale Internet (ad esempio il firewall esterno) e le posizioni internazionali del servizio cloud Microsoft a cui ci si connette.</span><span class="sxs-lookup"><span data-stu-id="5d61a-113">Analyze the latency between your Internet edge device (such as your external firewall) and the regional locations of the Microsoft cloud service to which you are connecting.</span></span>
    
2. <span data-ttu-id="5d61a-114">Analizzare la capacità e l'utilizzo della connessione Internet corrente e aggiungere capacità, se necessario.</span><span class="sxs-lookup"><span data-stu-id="5d61a-114">Analyze the capacity and utilization of your current Internet connection and add capacity if needed.</span></span> <span data-ttu-id="5d61a-115">In alternativa, aggiungere una connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="5d61a-115">Alternately, add an ExpressRoute connection.</span></span>
    
## <a name="microsoft-cloud-connectivity-options"></a><span data-ttu-id="5d61a-116">Opzioni di connettività cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="5d61a-116">Microsoft cloud connectivity options</span></span>
<span data-ttu-id="5d61a-117"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="5d61a-117"></span></span>

<span data-ttu-id="5d61a-118">Utilizzare la pipe Internet esistente o una connessione ExpressRoute a Office 365, Azure e Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="5d61a-118">Use your existing Internet pipe or an ExpressRoute connection to Office 365, Azure, and Dynamics 365.</span></span>
  
<span data-ttu-id="5d61a-119">**Figura 1: opzioni per la connettività cloud Microsoft**</span><span class="sxs-lookup"><span data-stu-id="5d61a-119">**Figure 1: Options for Microsoft cloud connectivity**</span></span>

![Figura 1: opzioni per la connettività cloud Microsoft](media/Network-Poster/CommonElements.png)

  
<span data-ttu-id="5d61a-121">Nella figura 1 viene illustrato come è possibile connettere una rete locale a offerte cloud di Microsoft utilizzando la propria pipe Internet o ExpressRoute esistente.</span><span class="sxs-lookup"><span data-stu-id="5d61a-121">Figure 1 shows how an on-premises network can be connected to Microsoft cloud offerings using their existing Internet pipe or ExpressRoute.</span></span> <span data-ttu-id="5d61a-122">La pipe Internet rappresenta una DMZ e può disporre dei componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="5d61a-122">The Internet pipe represents a DMZ and can have the following components:</span></span>
  
- <span data-ttu-id="5d61a-123">**Firewall interno:** Una barriera tra la rete attendibile e quella non attendibile.</span><span class="sxs-lookup"><span data-stu-id="5d61a-123">**Internal firewall:** A barrier between your trusted network and an untrusted one.</span></span> <span data-ttu-id="5d61a-124">Esegue il filtraggio del traffico (in base alle regole) e il monitoraggio.</span><span class="sxs-lookup"><span data-stu-id="5d61a-124">Performs traffic filtering (based on rules) and monitoring.</span></span>
    
- <span data-ttu-id="5d61a-125">**Carico di lavoro esterno:** Siti Web o altri carichi di lavoro resi disponibili per gli utenti esterni su Internet.</span><span class="sxs-lookup"><span data-stu-id="5d61a-125">**External workload:** Web sites or other workloads made available to external users on the Internet.</span></span>
    
- <span data-ttu-id="5d61a-126">**Server proxy:** Richieste di servizi per il contenuto Web per conto di utenti Intranet.</span><span class="sxs-lookup"><span data-stu-id="5d61a-126">**Proxy server:** Services requests for web content on behalf of intranet users.</span></span> <span data-ttu-id="5d61a-127">Un proxy inverso consente richieste inbound indesiderate.</span><span class="sxs-lookup"><span data-stu-id="5d61a-127">A reverse proxy permits unsolicited inbound requests.</span></span>
    
- <span data-ttu-id="5d61a-128">**Firewall esterno:** Consente il traffico in uscita e il traffico in ingresso specificato.</span><span class="sxs-lookup"><span data-stu-id="5d61a-128">**External firewall:** Allows outbound traffic and specified inbound traffic.</span></span> <span data-ttu-id="5d61a-129">È in grado di eseguire la conversione degli indirizzi, l'ispezione dei pacchetti, la rottura SSL e il controllo o la prevenzione della perdita di</span><span class="sxs-lookup"><span data-stu-id="5d61a-129">Can perform address translation, packet inspection, SSL Break and Inspect, or data loss prevention.</span></span>
    
- <span data-ttu-id="5d61a-130">**Connessione WAN a ISP:** Una connessione basata su portatore a un ISP, che si occupa di peer con Internet per la connettività e il routing.</span><span class="sxs-lookup"><span data-stu-id="5d61a-130">**WAN connection to ISP:** A carrier-based connection to an ISP, who peers with the Internet for connectivity and routing.</span></span>
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a><span data-ttu-id="5d61a-131">Aree di rete comuni a tutti i servizi cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="5d61a-131">Areas of networking common to all Microsoft cloud services</span></span>
<span data-ttu-id="5d61a-132"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="5d61a-132"></span></span>

<span data-ttu-id="5d61a-133">È necessario prendere in considerazione queste aree di networking quando si adotta uno dei servizi cloud di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5d61a-133">You need to consider these areas of networking when adopting any of Microsoft's cloud services.</span></span>
  
- <span data-ttu-id="5d61a-134">**Prestazioni Intranet:** Le prestazioni alle risorse basate su Internet soffriranno se la rete Intranet, compresi i computer client, non è ottimizzata.</span><span class="sxs-lookup"><span data-stu-id="5d61a-134">**Intranet performance:** Performance to Internet-based resources will suffer if your intranet, including client computers, is not optimized.</span></span>
    
- <span data-ttu-id="5d61a-135">**Dispositivi perimetrali:** I dispositivi ai margini della rete sono punti di uscita e possono includere i NAT (Network Address Translator), i server proxy (inclusi i proxy inversi), i firewall, i dispositivi di rilevamento delle intrusioni o una combinazione.</span><span class="sxs-lookup"><span data-stu-id="5d61a-135">**Edge devices:** Devices at the edge of your network are egress points and can include Network Address Translators (NATs), proxy servers (including reverse proxies), firewalls, intrusion detection devices, or a combination.</span></span>
    
- <span data-ttu-id="5d61a-136">**Connessione Internet:** La connessione WAN all'ISP e a Internet deve disporre di capacità sufficiente per gestire i carichi di picco.</span><span class="sxs-lookup"><span data-stu-id="5d61a-136">**Internet connection:** Your WAN connection to your ISP and the Internet should have enough capacity to handle peak loads.</span></span> <span data-ttu-id="5d61a-137">È inoltre possibile utilizzare una connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="5d61a-137">You can also use an ExpressRoute connection.</span></span>
    
- <span data-ttu-id="5d61a-138">**DNS Internet:** A, AAAA, CNAME, MX, PTR e altri record per individuare Microsoft Cloud o i servizi ospitati nel cloud.</span><span class="sxs-lookup"><span data-stu-id="5d61a-138">**Internet DNS:** A, AAAA, CNAME, MX, PTR and other records to locate Microsoft cloud or your services hosted in the cloud.</span></span> <span data-ttu-id="5d61a-139">Ad esempio, potrebbe essere necessario un record CNAME per l'app ospitata in Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="5d61a-139">For example, you might need a CNAME record for your app hosted in Azure PaaS.</span></span>
    

## <a name="next-step"></a><span data-ttu-id="5d61a-140">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="5d61a-140">Next step</span></span>

[<span data-ttu-id="5d61a-141">ExpressRoute per la connettività cloud di Microsoft</span><span class="sxs-lookup"><span data-stu-id="5d61a-141">ExpressRoute for Microsoft cloud connectivity</span></span>](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a><span data-ttu-id="5d61a-142">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5d61a-142">See also</span></span>

<span data-ttu-id="5d61a-143"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="5d61a-143"></span></span>

[<span data-ttu-id="5d61a-144">Rete di Microsoft Cloud per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="5d61a-144">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="5d61a-145">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="5d61a-145">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


