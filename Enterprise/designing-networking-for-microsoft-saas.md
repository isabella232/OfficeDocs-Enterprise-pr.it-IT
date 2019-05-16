---
title: Progettazione di rete per Microsoft SaaS
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
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: "Riepilogo: informazioni su come ottimizzare la rete per l'accesso ai servizi SaaS di Microsoft, tra cui Office 365, Microsoft Intune e Dynamics 365."
ms.openlocfilehash: 695e3255bf1afcb5314985caccb15ead410d93f6
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067772"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="3b3f5-103">Progettazione di rete per Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="3b3f5-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="3b3f5-104">**Riepilogo:** Informazioni su come ottimizzare la rete per l'accesso ai servizi SaaS di Microsoft, tra cui Office 365, Microsoft Intune e Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="3b3f5-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="3b3f5-105">Ottimizzare la rete per servizi SaaS Microsoft richiede la configurazione di dispositivi interni e periferici per instradare le diverse categorie di traffico ai servizi SaaS Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3b3f5-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="3b3f5-106">Passaggi per preparare la rete per i servizi SaaS di Microsoft</span><span class="sxs-lookup"><span data-stu-id="3b3f5-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="3b3f5-107">Seguire questa procedura per ottimizzare la rete per i servizi SaaS di Microsoft:</span><span class="sxs-lookup"><span data-stu-id="3b3f5-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="3b3f5-108">Consultare la sezione **Procedura per predisporre la rete per i servizi cloud Microsoft** in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="3b3f5-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="3b3f5-109">Aggiungere una connessione Internet a ciascuno degli uffici.</span><span class="sxs-lookup"><span data-stu-id="3b3f5-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="3b3f5-110">Verificare che gli ISP per tutte le connessioni Internet utilizzino un server DNS con un indirizzo IP locale.</span><span class="sxs-lookup"><span data-stu-id="3b3f5-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="3b3f5-111">Esaminare i tornanti di rete, le destinazioni intermedie, ad esempio i servizi di sicurezza basati sul cloud, ed eliminarli se possibile.</span><span class="sxs-lookup"><span data-stu-id="3b3f5-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="3b3f5-112">Configurare i dispositivi perimetrali in modo da ignorare l'elaborazione per le categorie ottimizzazione e Consenti del traffico SaaS di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3b3f5-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="3b3f5-113">Ottimizzazione del traffico per i servizi SaaS di Microsoft</span><span class="sxs-lookup"><span data-stu-id="3b3f5-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="3b3f5-114">Esistono tre categorie di traffico SaaS Microsoft:</span><span class="sxs-lookup"><span data-stu-id="3b3f5-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="3b3f5-115">Ottimizzazione</span><span class="sxs-lookup"><span data-stu-id="3b3f5-115">Optimize</span></span>

  <span data-ttu-id="3b3f5-116">Necessario per la connettività a tutti i servizi SaaS di Microsoft e rappresentare oltre il 75% della larghezza di banda, delle connessioni e del volume di dati di Microsoft SaaS.</span><span class="sxs-lookup"><span data-stu-id="3b3f5-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="3b3f5-117">Consenti</span><span class="sxs-lookup"><span data-stu-id="3b3f5-117">Allow</span></span>

  <span data-ttu-id="3b3f5-118">Necessario per la connettività a specifici servizi e caratteristiche di Microsoft SaaS, ma non sono sensibili alle prestazioni e alla latenza di rete come quelli della categoria optimize.</span><span class="sxs-lookup"><span data-stu-id="3b3f5-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="3b3f5-119">Predefinita</span><span class="sxs-lookup"><span data-stu-id="3b3f5-119">Default</span></span>

  <span data-ttu-id="3b3f5-120">Rappresentano i servizi e le dipendenze di Microsoft SaaS che non richiedono alcuna ottimizzazione.</span><span class="sxs-lookup"><span data-stu-id="3b3f5-120">Represent Microsoft SaaS services and dependencies that do not require any optimization.</span></span> <span data-ttu-id="3b3f5-121">È possibile gestire il traffico di categoria predefinito come il traffico Internet normale.</span><span class="sxs-lookup"><span data-stu-id="3b3f5-121">You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="3b3f5-122">**Figura 1: configurazione consigliata per il traffico SaaS di Microsoft per tutte le sedi**</span><span class="sxs-lookup"><span data-stu-id="3b3f5-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![Figura 1: configurazione consigliata per il traffico SaaS di Microsoft per tutte le sedi](media/Network-Poster/SaaS1.png)

<span data-ttu-id="3b3f5-124">Nella figura 1 viene illustrata la configurazione consigliata di tutti gli uffici, tra cui le succursali e quelle regionali o centrali, in cui:</span><span class="sxs-lookup"><span data-stu-id="3b3f5-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="3b3f5-125">La categoria **predefinita** e il traffico Internet generale vengono instradati agli uffici che dispongono di server proxy e di altri dispositivi perimetrali per garantire la protezione contro i rischi di sicurezza basati su Internet.</span><span class="sxs-lookup"><span data-stu-id="3b3f5-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="3b3f5-126">**Ottimizzare** e **consentire** il traffico delle categorie viene inoltrato direttamente al server perimetrale di Microsoft Network front-end più vicino all'ufficio che contiene l'utente che esegue la connessione, ignorando il proxy e altri dispositivi perimetrali.</span><span class="sxs-lookup"><span data-stu-id="3b3f5-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="3b3f5-127">I dispositivi di rete wide area (SD-WAN) definiti dal software nelle succursali distaccano il traffico in modo che:</span><span class="sxs-lookup"><span data-stu-id="3b3f5-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="3b3f5-128">La categoria **predefinita** e il traffico Internet generale passano a un ufficio centrale o regionale sulla backbone WAN.</span><span class="sxs-lookup"><span data-stu-id="3b3f5-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="3b3f5-129">**Ottimizzare** e **consentire** il traffico di categoria passa all'ISP che fornisce la connessione Internet locale.</span><span class="sxs-lookup"><span data-stu-id="3b3f5-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="3b3f5-130">Per ulteriori informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="3b3f5-130">For more information, see:</span></span>
  
- [<span data-ttu-id="3b3f5-131">Principi di connettività di rete</span><span class="sxs-lookup"><span data-stu-id="3b3f5-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="3b3f5-132">Pianificazione della rete e della migrazione per Office 365</span><span class="sxs-lookup"><span data-stu-id="3b3f5-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="3b3f5-133">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="3b3f5-133">Next step</span></span>

[<span data-ttu-id="3b3f5-134">Progettazione di rete per Microsoft Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="3b3f5-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="3b3f5-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3b3f5-135">See also</span></span>

[<span data-ttu-id="3b3f5-136">Rete di Microsoft Cloud per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="3b3f5-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="3b3f5-137">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="3b3f5-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

