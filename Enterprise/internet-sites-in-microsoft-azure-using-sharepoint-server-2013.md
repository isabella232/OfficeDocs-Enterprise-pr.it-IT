---
title: Siti Internet in Microsoft Azure che utilizzano SharePoint Server 2013
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Architecture
ms.assetid: 0d93ff4a-8fbd-42b8-9227-d817dba0046d
description: "Sintesi: I siti Internet che utilizzano SharePoint Server 2013 traggono vantaggio dall'essere ospitati in servizi infrastruttura di Azure. In questo articolo sono disponibili risorse utili per progettare e implementare questa soluzione."
ms.openlocfilehash: 7791da6954aea49b9292967fe32311c529bedc69
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41845097"
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="fb739-104">Siti Internet in Microsoft Azure che utilizzano SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="fb739-104">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>

 <span data-ttu-id="fb739-p102">**Riepilogo: I siti Internet** che utilizzano SharePoint Server 2013 traggono vantaggio dall'essere ospitati in servizi infrastruttura di Azure. In questo articolo sono disponibili risorse utili per progettare e implementare questa soluzione.</span><span class="sxs-lookup"><span data-stu-id="fb739-p102">**Summary:** Internet sites that use SharePoint Server 2013 benefit by being hosted in Azure Infrastructure Services. This article provides resources for designing and implementing this solution.</span></span>
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a><span data-ttu-id="fb739-107">Utilizzare i servizi infrastruttura di Azure per i siti Internet</span><span class="sxs-lookup"><span data-stu-id="fb739-107">Using Azure Infrastructure Services for Internet sites</span></span>

<span data-ttu-id="fb739-p103">Microsoft Azure fornisce un'opzione interessante per ospitare siti Internet basati su SharePoint Server 2013. I vantaggi includono quanto segue:</span><span class="sxs-lookup"><span data-stu-id="fb739-p103">Microsoft Azure provides a compelling option for hosting Internet sites based on SharePoint Server 2013. Advantages include the following:</span></span>
  
- <span data-ttu-id="fb739-110">Focalizzazione sullo sviluppo di un sito efficiente anziché sulla creazione dell'infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="fb739-110">Focus on developing a great site instead of building infrastructure.</span></span>
    
- <span data-ttu-id="fb739-111">Flessibilità per ridimensionare la soluzione basata su richiesta aumentando e riducendo.</span><span class="sxs-lookup"><span data-stu-id="fb739-111">Flexibility to scale your solution based on demand by scaling out and in.</span></span>
    
- <span data-ttu-id="fb739-112">Pagare solo per le risorse necessarie e utilizzate.</span><span class="sxs-lookup"><span data-stu-id="fb739-112">Pay only for the resources that you need and use.</span></span>
    
- <span data-ttu-id="fb739-113">Sfruttare Azure Active Directory per gli account cliente.</span><span class="sxs-lookup"><span data-stu-id="fb739-113">Take advantage of Azure Active Directory for customer accounts.</span></span>
    
- <span data-ttu-id="fb739-114">Aggiungere funzionalità che non sono attualmente disponibili in Office 365, ad esempio report e analisi completi.</span><span class="sxs-lookup"><span data-stu-id="fb739-114">Add features that are not currently available in Office 365, such as deep reporting and analytics.</span></span>
    
## <a name="resources"></a><span data-ttu-id="fb739-115">Risorse</span><span class="sxs-lookup"><span data-stu-id="fb739-115">Resources</span></span>

<span data-ttu-id="fb739-116">Le seguenti illustrazioni tecniche e i seguenti articoli forniscono informazioni su come progettare e implementare siti Internet in Azure utilizzando SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="fb739-116">The following technical illustrations and articles provide information about how to design and implement Internet sites in Azure by using SharePoint Server 2013.</span></span>
  
|<span data-ttu-id="fb739-117">**Risorsa**</span><span class="sxs-lookup"><span data-stu-id="fb739-117">**Resource**</span></span>|<span data-ttu-id="fb739-118">**Ulteriori informazioni**</span><span class="sxs-lookup"><span data-stu-id="fb739-118">**More information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="fb739-119">**Siti Internet SharePoint Server 2013 in Azure**</span><span class="sxs-lookup"><span data-stu-id="fb739-119">**SharePoint Server 2013 Internet sites in Azure**</span></span> <br/> <span data-ttu-id="fb739-120">[![Immagine di siti Internet in Azure con SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="fb739-120">[![Image of Internet sites in Azure using SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> <br/> <span data-ttu-id="fb739-121">[](https://go.microsoft.com/fwlink/p/?LinkId=392552)\| PDF [           ](https://go.microsoft.com/fwlink/p/?LinkId=392551) [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  </span><span class="sxs-lookup"><span data-stu-id="fb739-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span></span> <br/> |<span data-ttu-id="fb739-122">Questo modello di architettura descrive le attività di progettazione e le scelte di architettura consigliate per i siti Internet in Azure.</span><span class="sxs-lookup"><span data-stu-id="fb739-122">This architecture model outlines key design activities and recommended architecture choices for Internet sites in Azure.</span></span>  <br/> |
|<span data-ttu-id="fb739-123">**Esempio di progettazione: Siti Internet in Azure per SharePoint Server 2013**</span><span class="sxs-lookup"><span data-stu-id="fb739-123">**Design sample: Internet Sites in Azure for SharePoint Server 2013**</span></span> <br/> <span data-ttu-id="fb739-124">[![Anteprima della struttura di esempio: siti Internet in Microsoft Azure per SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="fb739-124">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> <br/> <span data-ttu-id="fb739-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549) \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span><span class="sxs-lookup"><span data-stu-id="fb739-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span></span> <br/> |<span data-ttu-id="fb739-126">Utilizzare questo esempio di progettazione come punto di partenza per la propria architettura.</span><span class="sxs-lookup"><span data-stu-id="fb739-126">Use this design sample as a starting point for your own architecture.</span></span>  <br/> |
|<span data-ttu-id="fb739-127">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span><span class="sxs-lookup"><span data-stu-id="fb739-127">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span></span> <br/> |<span data-ttu-id="fb739-128">In questo articolo viene descritto come progettare le architetture Azure e ospitare le soluzioni SharePoint.</span><span class="sxs-lookup"><span data-stu-id="fb739-128">This article describes how to design Azure architectures to host SharePoint solutions.</span></span>  <br/> |

## <a name="see-also"></a><span data-ttu-id="fb739-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fb739-129">See Also</span></span>

[<span data-ttu-id="fb739-130">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="fb739-130">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)



