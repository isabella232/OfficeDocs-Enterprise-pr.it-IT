---
title: Ottimizzare le immagini nelle pagine moderne di siti di SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Informazioni su come ottimizzare le immagini nelle pagine moderne di siti di SharePoint Online.
ms.openlocfilehash: 68e2f79e1f768cfc93feb4f26f8b2fbeca5d6b83
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2019
ms.locfileid: "39814224"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="ee642-103">Ottimizzare le immagini nelle pagine moderne di siti di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ee642-103">Optimize images in SharePoint Online modern site pages</span></span>

<span data-ttu-id="ee642-104">Questo articolo spiega come ottimizzare le immagini nelle pagine moderne di siti di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ee642-104">This article will help you understand how to optimize images in SharePoint Online modern site pages.</span></span>

<span data-ttu-id="ee642-105">Per informazioni su come ottimizzare le immagini in siti di pubblicazione classici, vedere [Ottimizzazione delle immagini per SharePoint Online](image-optimization-for-sharepoint-online.md).</span><span class="sxs-lookup"><span data-stu-id="ee642-105">For information about optimizing images in classic publishing sites, see [Image optimization for SharePoint Online](image-optimization-for-sharepoint-online.md)..</span></span>

>[!NOTE]
><span data-ttu-id="ee642-106">Per altre informazioni sulle prestazioni nei portali moderni di SharePoint Online, vedere [Prestazioni nell'esperienza moderna di SharePoint](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span><span class="sxs-lookup"><span data-stu-id="ee642-106">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a><span data-ttu-id="ee642-107">Usare lo strumento Diagnostica pagine per SharePoint per analizzare l'ottimizzazione delle immagini</span><span class="sxs-lookup"><span data-stu-id="ee642-107">Use the Page Diagnostics for SharePoint tool to analyze image optimization</span></span>

<span data-ttu-id="ee642-108">Lo **strumento Diagnostica pagine per SharePoint** è un'estensione del browser per Chrome e per la [versione 77 o successiva di Microsoft Edge](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) che consente di analizzare le pagine classiche e moderne di siti di pubblicazione di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="ee642-108">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="ee642-109">Per ogni pagina analizzata lo strumento fornisce un report che mostra le prestazioni della pagina rispetto a un set definiti di criteri delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="ee642-109">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="ee642-110">Per installare Diagnostica pagine per SharePoint e saperne di più su questo strumento, vedere [Usare lo strumento Diagnostica pagine per SharePoint Online](page-diagnostics-for-spo.md).</span><span class="sxs-lookup"><span data-stu-id="ee642-110">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="ee642-111">Quando si analizza un sito moderno di SharePoint con lo strumento Diagnostica pagine per SharePoint, è possibile visualizzare le informazioni sulle immagini di grandi dimensioni nel riquadro _Test diagnostici_.</span><span class="sxs-lookup"><span data-stu-id="ee642-111">When you analyze a SharePoint modern site with the Page Diagnostics for SharePoint tool, you can see information about large images in the _Diagnostic tests_ pane.</span></span>

<span data-ttu-id="ee642-112">I risultati possibili includono:</span><span class="sxs-lookup"><span data-stu-id="ee642-112">Possible results include:</span></span>

- <span data-ttu-id="ee642-113">**Attenzione** (rosso): la pagina contiene **una o più** immagini di dimensioni superiori a 300 KB</span><span class="sxs-lookup"><span data-stu-id="ee642-113">**Attention required** (red): The page contains **one or more** images over 300KB in size</span></span>
- <span data-ttu-id="ee642-114">**Non è richiesto alcun intervento** (verde): la pagina non contiene immagini di dimensioni superiori a 300 KB</span><span class="sxs-lookup"><span data-stu-id="ee642-114">**No action required** (green): The page contains no images over 300KB in size</span></span>

<span data-ttu-id="ee642-115">Se nella sezione dei risultati **Attenzione** viene visualizzato il risultato **Sono state rilevate immagini di grandi dimensioni**, è possibile fare clic sul risultato per visualizzare altri dettagli.</span><span class="sxs-lookup"><span data-stu-id="ee642-115">If the **Large images detected** result appears in the **Attention required** section of the results, you can click the result to see additional details.</span></span>

![Risultati dello strumento Diagnostica pagine](media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a><span data-ttu-id="ee642-117">Risolvere i problemi relativi a immagini di grandi dimensioni</span><span class="sxs-lookup"><span data-stu-id="ee642-117">Remediate large image issues</span></span>

<span data-ttu-id="ee642-118">Se una pagina contiene immagini di dimensioni superiori a 300 KB, selezionare il risultato **Sono state rilevate immagini di grandi dimensioni** per visualizzare le immagini di dimensioni eccessive.</span><span class="sxs-lookup"><span data-stu-id="ee642-118">If a page contains images over 300KB in size, select the **Large images detected** result to see which images are too large.</span></span> <span data-ttu-id="ee642-119">Nelle pagine moderne di SharePoint Online i rendering delle immagini vengono forniti e ridimensionati automaticamente a seconda delle dimensioni della finestra del browser e della risoluzione del monitor client.</span><span class="sxs-lookup"><span data-stu-id="ee642-119">In modern SharePoint Online pages, renditions of images are automatically provided and sized depending on the size of the browser window and the resolution of the client monitor.</span></span> <span data-ttu-id="ee642-120">È consigliabile ottimizzare sempre le immagini per l'uso Web prima di caricarle in SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ee642-120">You should always optimize images for web use prior to upload to SharePoint Online.</span></span> <span data-ttu-id="ee642-121">Le dimensioni e la risoluzione di immagini di grandi dimensioni verranno ridotte automaticamente e questa riduzione può influire sul rendering.</span><span class="sxs-lookup"><span data-stu-id="ee642-121">Very large images will be automatically reduced in size and resolution which can result in unexpected rendering characteristics.</span></span>

<span data-ttu-id="ee642-122">Prima di revisionare le pagine per correggere i problemi di prestazioni, prendere nota del tempo di caricamento delle pagine nei risultati dell'analisi.</span><span class="sxs-lookup"><span data-stu-id="ee642-122">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="ee642-123">Eseguire di nuovo lo strumento dopo la revisione per verificare se il nuovo risultato è compreso nello standard di base e controllare il nuovo tempo di caricamento della pagina per verificare se c'è stato un miglioramento.</span><span class="sxs-lookup"><span data-stu-id="ee642-123">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![Risultati del tempo di caricamento delle pagine](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="ee642-125">Il tempo di caricamento delle pagine dipende da numerosi fattori, ad esempio il carico di rete, l'ora del giorno e altre condizioni transitorie.</span><span class="sxs-lookup"><span data-stu-id="ee642-125">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="ee642-126">È consigliabile verificare il tempo di caricamento delle pagine alcune volte prima e dopo aver apportato modifiche in modo da ottenere una media dei risultati.</span><span class="sxs-lookup"><span data-stu-id="ee642-126">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="ee642-127">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="ee642-127">Related topics</span></span>

[<span data-ttu-id="ee642-128">Ottimizzare le prestazioni di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ee642-128">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="ee642-129">Ottimizzare le prestazioni di Office 365</span><span class="sxs-lookup"><span data-stu-id="ee642-129">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="ee642-130">Prestazioni nell'esperienza moderna di SharePoint</span><span class="sxs-lookup"><span data-stu-id="ee642-130">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[<span data-ttu-id="ee642-131">Reti per la distribuzione di contenuti</span><span class="sxs-lookup"><span data-stu-id="ee642-131">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="ee642-132">Usare la rete per la distribuzione di contenuti di Office 365 con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ee642-132">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
