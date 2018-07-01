---
title: Siti Internet in Microsoft Azure che utilizzano SharePoint Server 2013
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 0d93ff4a-8fbd-42b8-9227-d817dba0046d
description: "Sintesi: I siti Internet che utilizzano SharePoint Server 2013 traggono vantaggio dall'essere ospitati in servizi infrastruttura di Azure. In questo articolo sono disponibili risorse utili per progettare e implementare questa soluzione."
ms.openlocfilehash: a2444cdf98e861530131d55ae80fc661f730ba57
ms.sourcegitcommit: 9f57825b10f20e3813732372541128ef187d52c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "20161789"
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="24eaa-104">Siti Internet in Microsoft Azure che utilizzano SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="24eaa-104">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>

 <span data-ttu-id="24eaa-p102">**Riepilogo: I siti Internet** che utilizzano SharePoint Server 2013 traggono vantaggio dall'essere ospitati in servizi infrastruttura di Azure. In questo articolo sono disponibili risorse utili per progettare e implementare questa soluzione.</span><span class="sxs-lookup"><span data-stu-id="24eaa-p102">**Summary:** Internet sites that use SharePoint Server 2013 benefit by being hosted in Azure Infrastructure Services. This article provides resources for designing and implementing this solution.</span></span>
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a><span data-ttu-id="24eaa-107">Utilizzare i servizi infrastruttura di Azure per i siti Internet</span><span class="sxs-lookup"><span data-stu-id="24eaa-107">Using Azure Infrastructure Services for Internet sites</span></span>

<span data-ttu-id="24eaa-p103">Microsoft Azure fornisce un'opzione interessante per ospitare siti Internet basati su SharePoint Server 2013. I vantaggi includono quanto segue:</span><span class="sxs-lookup"><span data-stu-id="24eaa-p103">Microsoft Azure provides a compelling option for hosting Internet sites based on SharePoint Server 2013. Advantages include the following:</span></span>
  
- <span data-ttu-id="24eaa-110">Focalizzazione sullo sviluppo di un sito efficiente anziché sulla creazione dell'infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="24eaa-110">Focus on developing a great site instead of building infrastructure.</span></span>
    
- <span data-ttu-id="24eaa-111">Flessibilità per ridimensionare la soluzione basata su richiesta aumentando e riducendo.</span><span class="sxs-lookup"><span data-stu-id="24eaa-111">Flexibility to scale your solution based on demand by scaling out and in.</span></span>
    
- <span data-ttu-id="24eaa-112">Pagare solo per le risorse necessarie e utilizzate.</span><span class="sxs-lookup"><span data-stu-id="24eaa-112">Pay only for the resources that you need and use.</span></span>
    
- <span data-ttu-id="24eaa-113">Sfruttare Azure Active Directory per gli account cliente.</span><span class="sxs-lookup"><span data-stu-id="24eaa-113">Take advantage of Azure Active Directory for customer accounts.</span></span>
    
- <span data-ttu-id="24eaa-114">Aggiungere funzionalità che non sono attualmente disponibili in Office 365, ad esempio report e analisi completi.</span><span class="sxs-lookup"><span data-stu-id="24eaa-114">Add features that are not currently available in Office 365, such as deep reporting and analytics.</span></span>
    
## <a name="resources"></a><span data-ttu-id="24eaa-115">Risorse</span><span class="sxs-lookup"><span data-stu-id="24eaa-115">Resources</span></span>

<span data-ttu-id="24eaa-116">Le seguenti illustrazioni tecniche e i seguenti articoli forniscono informazioni su come progettare e implementare siti Internet in Azure utilizzando SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="24eaa-116">The following technical illustrations and articles provide information about how to design and implement Internet sites in Azure by using SharePoint Server 2013.</span></span>
  
|<span data-ttu-id="24eaa-117">**Risorsa**</span><span class="sxs-lookup"><span data-stu-id="24eaa-117">**Resource**</span></span>|<span data-ttu-id="24eaa-118">**Ulteriori informazioni**</span><span class="sxs-lookup"><span data-stu-id="24eaa-118">**More information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="24eaa-119">**Siti Internet SharePoint Server 2013 in Azure**</span><span class="sxs-lookup"><span data-stu-id="24eaa-119">**SharePoint Server 2013 Internet sites in Azure**</span></span> <br/> <span data-ttu-id="24eaa-120">[![Immagine di siti Internet in Azure con SharePoint](images/MS_AZ_SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="24eaa-120">[![Image of Internet sites in Azure using SharePoint](images/MS_AZ_SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> <br/> <span data-ttu-id="24eaa-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552) \| [           ](https://go.microsoft.com/fwlink/p/?LinkId=392551) [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  </span><span class="sxs-lookup"><span data-stu-id="24eaa-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span></span> <br/> |<span data-ttu-id="24eaa-122">Questo modello di architettura descrive le attività di progettazione e le scelte di architettura consigliate per i siti Internet in Azure.</span><span class="sxs-lookup"><span data-stu-id="24eaa-122">This architecture model outlines key design activities and recommended architecture choices for Internet sites in Azure.</span></span>  <br/> |
|<span data-ttu-id="24eaa-123">**Esempio di progettazione: Siti Internet in Azure per SharePoint Server 2013**</span><span class="sxs-lookup"><span data-stu-id="24eaa-123">**Design sample: Internet Sites in Azure for SharePoint Server 2013**</span></span> <br/> <span data-ttu-id="24eaa-124">[![Anteprima della struttura di esempio: siti Internet in Microsoft Azure per SharePoint 2013](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="24eaa-124">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> <br/> <span data-ttu-id="24eaa-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549) \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span><span class="sxs-lookup"><span data-stu-id="24eaa-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span></span> <br/> |<span data-ttu-id="24eaa-126">Utilizzare questo esempio di progettazione come punto di partenza per la propria architettura.</span><span class="sxs-lookup"><span data-stu-id="24eaa-126">Use this design sample as a starting point for your own architecture.</span></span>  <br/> |
|<span data-ttu-id="24eaa-127">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span><span class="sxs-lookup"><span data-stu-id="24eaa-127">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span></span> <br/> |<span data-ttu-id="24eaa-128">In questo articolo viene descritto come progettare le architetture Azure e ospitare le soluzioni SharePoint.</span><span class="sxs-lookup"><span data-stu-id="24eaa-128">This article describes how to design Azure architectures to host SharePoint solutions.</span></span>  <br/> |

   
<span data-ttu-id="24eaa-129">**Partecipare alla discussione**</span><span class="sxs-lookup"><span data-stu-id="24eaa-129">**Join the discussion**</span></span>

|<span data-ttu-id="24eaa-130">**Contattaci**</span><span class="sxs-lookup"><span data-stu-id="24eaa-130">**Contact us**</span></span>|<span data-ttu-id="24eaa-131">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="24eaa-131">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="24eaa-132">**Ottenere la soluzione necessaria**</span><span class="sxs-lookup"><span data-stu-id="24eaa-132">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="24eaa-p104">Microsoft sta creando documenti contenenti soluzioni che fanno riferimento a numerosi prodotti e servizi. Fornire commenti e suggerimenti sulle soluzioni tra server proposte o richiedere una soluzione specifica inviando un'e-mail all'indirizzo [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).</span><span class="sxs-lookup"><span data-stu-id="24eaa-p104">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="24eaa-135">**Partecipare alla discussione sulle soluzioni**</span><span class="sxs-lookup"><span data-stu-id="24eaa-135">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="24eaa-p105">Se si è appassionati di soluzioni basate sul cloud, prendere in considerazione l'idea di accedere al Cloud Adoption Advisory Board (CAAB) per connettersi con una community più ampia e vivace di sviluppatori di contenuti Microsoft, professionisti del settore e clienti di tutto il mondo. Per accedervi, diventare un membro dell'[area CAAB (Cloud Adoption Advisory Board)](https://aka.ms/caab) della Community tecnica Microsoft e inviare una breve e-mail all'indirizzo [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Chiunque può leggere i contenuti correlati alla community nel [blog di CAAB](https://blogs.technet.com/b/solutions_advisory_board/). Tuttavia, i membri CAAB ricevono inviti a webinar privati che descrivono le nuove soluzioni e risorse relative all'adozione del cloud.  </span><span class="sxs-lookup"><span data-stu-id="24eaa-p105">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="24eaa-140">**Ottenere l'immagine visualizzata**</span><span class="sxs-lookup"><span data-stu-id="24eaa-140">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="24eaa-p106">Se si desidera una copia modificabile dell'immagine visualizzata in questo articolo, Microsoft si occuperà di inviarla. Inviare la propria richiesta tramite e-mail, includendo l'URL e il titolo dell'immagine, all'indirizzo [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span><span class="sxs-lookup"><span data-stu-id="24eaa-p106">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="24eaa-143">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="24eaa-143">See Also</span></span>

[<span data-ttu-id="24eaa-144">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="24eaa-144">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)



