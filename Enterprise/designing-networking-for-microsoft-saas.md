---
title: Progettazione di rete per Microsoft SaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: "Riepilogo: Informazioni su come ottimizzare la rete per l'accesso ai servizi SaaS di Microsoft, tra cui Office 365, Microsoft Intune e Dynamics 365."
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872267"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="b66f1-103">Progettazione di rete per Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="b66f1-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="b66f1-104">**Riepilogo:** Informazioni su come ottimizzare la rete per l'accesso ai servizi SaaS di Microsoft, tra cui Office 365, Microsoft Intune e Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="b66f1-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="b66f1-105">Ottimizzazione della rete per i servizi Microsoft SaaS richiede la configurazione di interno e ai dispositivi di indirizzare le diverse categorie di traffico ai servizi Microsoft SaaS edge.</span><span class="sxs-lookup"><span data-stu-id="b66f1-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="b66f1-106">Passaggi di preparazione della rete per i servizi Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="b66f1-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="b66f1-107">Eseguire la procedura seguente per ottimizzare la rete per i servizi Microsoft SaaS:</span><span class="sxs-lookup"><span data-stu-id="b66f1-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="b66f1-108">Consultare la sezione **Procedura per predisporre la rete per i servizi cloud Microsoft** in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="b66f1-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="b66f1-109">Aggiungere una connessione Internet a ciascuno degli uffici.</span><span class="sxs-lookup"><span data-stu-id="b66f1-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="b66f1-110">Verificare che il provider di servizi Internet per tutte le connessioni Internet utilizzare un server DNS con un indirizzo IP locale.</span><span class="sxs-lookup"><span data-stu-id="b66f1-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="b66f1-111">Esaminare i hairpins di rete, intermedie destinazioni, ad esempio servizi di protezione basato su cloud ed eliminarle se possibile.</span><span class="sxs-lookup"><span data-stu-id="b66f1-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="b66f1-112">Configurare i dispositivi edge per ignorare l'elaborazione per l'ottimizzazione e consentire le categorie di traffico SaaS Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b66f1-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="b66f1-113">Ottimizzare il traffico ai SaaS servizi di Microsoft</span><span class="sxs-lookup"><span data-stu-id="b66f1-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="b66f1-114">Esistono tre categorie di traffico SaaS Microsoft:</span><span class="sxs-lookup"><span data-stu-id="b66f1-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="b66f1-115">Ottimizzazione</span><span class="sxs-lookup"><span data-stu-id="b66f1-115">Optimize</span></span>

  <span data-ttu-id="b66f1-116">Necessario per la connettività a ogni servizio Microsoft SaaS e rappresentano oltre il 75% di larghezza di banda SaaS Microsoft, le connessioni e volume di dati.</span><span class="sxs-lookup"><span data-stu-id="b66f1-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="b66f1-117">Consenti</span><span class="sxs-lookup"><span data-stu-id="b66f1-117">Allow</span></span>

  <span data-ttu-id="b66f1-118">Necessari per la connettività a specifici SaaS Microsoft dei servizi e funzionalità ma non sono i cursori sensibili alle prestazioni di rete e latenza a quelli della categoria Ottimizza.</span><span class="sxs-lookup"><span data-stu-id="b66f1-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="b66f1-119">Predefinita</span><span class="sxs-lookup"><span data-stu-id="b66f1-119">Default</span></span>

  <span data-ttu-id="b66f1-p101">Rappresentano SaaS Microsoft services e le dipendenze esistenti che non richiedono alcun ottimizzazione. È inoltre possibile considerare il traffico di categoria predefinita come normale traffico Internet.</span><span class="sxs-lookup"><span data-stu-id="b66f1-p101">Represent Microsoft SaaS services and dependencies that do not require any optimization. You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="b66f1-122">**Nella figura 1: Configurazione consigliata per il traffico SaaS Microsoft per tutti gli uffici**</span><span class="sxs-lookup"><span data-stu-id="b66f1-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![Nella figura 1: Configurazione consigliata per il traffico SaaS Microsoft per tutti gli uffici](media/Network-Poster/SaaS1.png)

<span data-ttu-id="b66f1-124">Nella figura 1 viene illustrata la configurazione consigliata di tutti gli uffici, incluse le succursali e quelle regionale o centrale, in cui:</span><span class="sxs-lookup"><span data-stu-id="b66f1-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="b66f1-125">Categorie **predefinite** e generale traffico Internet viene indirizzato a sedi che utilizzano i server proxy e ad altri dispositivi edge per garantire la protezione contro i rischi di sicurezza basato su Internet.</span><span class="sxs-lookup"><span data-stu-id="b66f1-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="b66f1-126">**Ottimizza** e **Consenti** traffico categoria viene inoltrato direttamente al bordo del Microsoft network front-end più vicina office contenente l'utente connesso, ignorando proxy server e altri dispositivi edge.</span><span class="sxs-lookup"><span data-stu-id="b66f1-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="b66f1-127">Dispositivi di rete (WAN SD) definito software WAN nelle succursali separano il traffico in modo che:</span><span class="sxs-lookup"><span data-stu-id="b66f1-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="b66f1-128">Categorie **predefinite** e generale Internet del traffico a un ufficio centrale o internazionale tramite backbone WAN.</span><span class="sxs-lookup"><span data-stu-id="b66f1-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="b66f1-129">Traffico categoria **Ottimizza** e **Consenti** passa al provider di servizi Internet che fornisce la connessione a Internet locale.</span><span class="sxs-lookup"><span data-stu-id="b66f1-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="b66f1-130">Per altre informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="b66f1-130">For more information, see:</span></span>
  
- [<span data-ttu-id="b66f1-131">Principi di connettività di rete</span><span class="sxs-lookup"><span data-stu-id="b66f1-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="b66f1-132">Pianificazione della rete e della migrazione per Office 365</span><span class="sxs-lookup"><span data-stu-id="b66f1-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="b66f1-133">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="b66f1-133">Next step</span></span>

[<span data-ttu-id="b66f1-134">Progettazione di rete per Microsoft Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="b66f1-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="b66f1-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b66f1-135">See also</span></span>

[<span data-ttu-id="b66f1-136">Rete di Microsoft Cloud per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="b66f1-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="b66f1-137">Risorse sull'architettura IT di Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="b66f1-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

