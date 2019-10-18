---
title: Ottimizzare il peso delle pagine moderne del sito in SharePoint Online
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
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Informazioni su come ottimizzare il peso delle pagine moderne del sito in SharePoint Online.
ms.openlocfilehash: 5e2231468363f58faeac1d7b21e06cd4fa790cf8
ms.sourcegitcommit: c7764503422922cb333b05d54e8ebbdb894df2f9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/18/2019
ms.locfileid: "37028213"
---
# <a name="optimize-page-weight-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="a83b9-103">Ottimizzare il peso delle pagine moderne del sito in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a83b9-103">Optimize page weight in SharePoint Online modern site pages</span></span>

<span data-ttu-id="a83b9-104">Le pagine moderne del sito di SharePoint Online contengono codice serializzato necessario per il rendering del contenuto della pagina, incluse le immagini, il testo, gli oggetti nell'area del contenuto sotto le barre di spostamento e di comando e altri codici HTML che formano la struttura della pagina.</span><span class="sxs-lookup"><span data-stu-id="a83b9-104">SharePoint Online modern site pages contain serialized code that is required to render page content of the page, including images, text, objects in the content area underneath navigation/command bars and other HTML code that forms the framework of the page.</span></span> <span data-ttu-id="a83b9-105">Il peso della pagina è una misura di questo codice HTML e deve essere limitato per garantire tempi di caricamento delle pagine ottimali.</span><span class="sxs-lookup"><span data-stu-id="a83b9-105">Page weight is a measurement of this HTML code, and should be limited to ensure optimal page load times.</span></span>

<span data-ttu-id="a83b9-106">Questo articolo spiega come ridurre il peso della pagina nelle pagine moderne del sito.</span><span class="sxs-lookup"><span data-stu-id="a83b9-106">This article will help you understand how to reduce page weight in your modern site pages.</span></span>

>[!NOTE]
><span data-ttu-id="a83b9-107">Per ulteriori informazioni sulle prestazioni nei portali moderni di SharePoint Online, vedere [Prestazioni nell'esperienza moderna di SharePoint](https://docs.microsoft.com/it-IT/sharepoint/modern-experience-performance).</span><span class="sxs-lookup"><span data-stu-id="a83b9-107">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/it-IT/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-weight"></a><span data-ttu-id="a83b9-108">Usare lo strumento Diagnostica pagine per SharePoint per analizzare il peso delle pagine</span><span class="sxs-lookup"><span data-stu-id="a83b9-108">Use the Page Diagnostics for SharePoint tool to analyze page weight</span></span>

<span data-ttu-id="a83b9-109">Lo **strumento Diagnostica pagine per SharePoint** è un'estensione del browser per Chrome e per la [versione di Microsoft Edge 77 o versioni successive](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8), che consente di analizzare sia le pagine di pubblicazione moderne che quelle classiche di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="a83b9-109">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="a83b9-110">Lo strumento fornisce un report per ogni pagina analizzata che mostra le prestazioni della pagina rispetto a un set di criteri di prestazioni definito.</span><span class="sxs-lookup"><span data-stu-id="a83b9-110">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="a83b9-111">Per installare e conoscere lo strumento Diagnostica pagine per SharePoint, visitare [Usare lo strumento Diagnostica pagine per SharePoint Online](page-diagnostics-for-spo.md).</span><span class="sxs-lookup"><span data-stu-id="a83b9-111">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="a83b9-112">Quando si analizza una pagina del sito di SharePoint con lo strumento Diagnostica pagine per SharePoint, è possibile visualizzare le informazioni sulla pagina nel risultato **Peso della pagina inferiore a 500 KB** del riquadro _Test diagnostici_.</span><span class="sxs-lookup"><span data-stu-id="a83b9-112">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about page in the **Page weight under 500KB** result of the _Diagnostic tests_ pane.</span></span> <span data-ttu-id="a83b9-113">Il risultato sarà verde se il peso della pagina è inferiore al valore della linea di base, mentre sarà rosso se il peso della pagina supera il valore della linea di base.</span><span class="sxs-lookup"><span data-stu-id="a83b9-113">The result will appear in green if the page weight is under the baseline value, and red if the page weight exceeds the baseline value.</span></span>

<span data-ttu-id="a83b9-114">I risultati possibili includono:</span><span class="sxs-lookup"><span data-stu-id="a83b9-114">Possible results include:</span></span>

- <span data-ttu-id="a83b9-115">**Attenzione richiesta** (rosso): il peso della pagina supera 500 KB</span><span class="sxs-lookup"><span data-stu-id="a83b9-115">**Attention required** (red): Page weight exceeds 500KB</span></span>
- <span data-ttu-id="a83b9-116">**Nessuna azione richiesta** (verde): il peso della pagina è inferiore a 500 KB</span><span class="sxs-lookup"><span data-stu-id="a83b9-116">**No action required** (green): Page weight is under 500KB</span></span>

<span data-ttu-id="a83b9-117">Se il risultato del **Peso della pagina inferiore a 500 KB** viene visualizzato nella sezione **Attenzione richiesta**, è possibile fare clic sul risultato per consultare le informazioni dettagliate.</span><span class="sxs-lookup"><span data-stu-id="a83b9-117">If the **Page weight under 500KB** result appears in the **Attention required** section, you can click the result for details.</span></span>

![Risultati delle Richieste a SharePoint](media/modern-portal-optimization/pagediag-page-weight.png)

## <a name="remediate-page-weight-issues"></a><span data-ttu-id="a83b9-119">Risolvere i problemi di peso delle pagine</span><span class="sxs-lookup"><span data-stu-id="a83b9-119">Remediate page weight issues</span></span>

<span data-ttu-id="a83b9-120">Se il peso della pagina supera 500 KB, è possibile migliorare i tempi complessivi di caricamento delle pagine, riducendo il numero di Web part e limitando il contenuto della pagina a un livello appropriato.</span><span class="sxs-lookup"><span data-stu-id="a83b9-120">If page weight exceeds 500KB, you can improve overall page load time by reducing the number of web parts and limiting page content to an appropriate degree.</span></span>

<span data-ttu-id="a83b9-121">Le indicazioni generali per ridurre il peso della pagina includono:</span><span class="sxs-lookup"><span data-stu-id="a83b9-121">General guidance for reducing page weight includes:</span></span>

- <span data-ttu-id="a83b9-122">Limitare il contenuto della pagina a un livello ragionevole e usare più pagine per i contenuti correlati.</span><span class="sxs-lookup"><span data-stu-id="a83b9-122">Limit the page content to a reasonable amount and use multiple pages for related content.</span></span>
- <span data-ttu-id="a83b9-123">Ridurre al minimo l'uso delle Web part con contenitori delle proprietà di grandi dimensioni.</span><span class="sxs-lookup"><span data-stu-id="a83b9-123">Minimize the use of web parts that have large property bags.</span></span>
- <span data-ttu-id="a83b9-124">Usare le viste di rollup non interattive, se possibile.</span><span class="sxs-lookup"><span data-stu-id="a83b9-124">Use non-interactive rollup views when possible.</span></span>
- <span data-ttu-id="a83b9-125">Ottimizzare le dimensioni delle immagini ridimensionando le immagini in modo appropriato, usando formati di immagine compressi e verificando che vengano scaricati da una rete CDN.</span><span class="sxs-lookup"><span data-stu-id="a83b9-125">Optimize image sizes by sizing images appropriately, using compressed image formats and ensuring that they are downloaded from a CDN.</span></span>

<span data-ttu-id="a83b9-126">Per altre informazioni sulle indicazioni per ridurre il peso della pagina, vedere l'articolo seguente:</span><span class="sxs-lookup"><span data-stu-id="a83b9-126">You can find additional guidance for limiting page weight in the following article:</span></span>

- [<span data-ttu-id="a83b9-127">Ottimizzare le prestazioni delle pagine in SharePoint</span><span class="sxs-lookup"><span data-stu-id="a83b9-127">Optimize page performance in SharePoint</span></span>](https://docs.microsoft.com/it-IT/sharepoint/dev/general-development/optimize-page-performance-in-sharepoint)

<span data-ttu-id="a83b9-128">Prima di eseguire le revisioni delle pagine per correggere i problemi di prestazioni, prendere nota del tempo di caricamento delle pagine nei risultati dell'analisi.</span><span class="sxs-lookup"><span data-stu-id="a83b9-128">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="a83b9-129">Eseguire di nuovo lo strumento dopo la revisione per verificare se il nuovo risultato ora rientra nei parametri di riferimento e controllare il tempo di caricamento della nuova pagina per verificare se è migliorato.</span><span class="sxs-lookup"><span data-stu-id="a83b9-129">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![Risultati del tempo di caricamento delle pagine](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="a83b9-131">Il tempo di caricamento delle pagine può variare in base a un'ampia varietà di fattori, ad esempio il carico di rete, l'ora del giorno e altre condizioni transitorie.</span><span class="sxs-lookup"><span data-stu-id="a83b9-131">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="a83b9-132">È consigliabile verificare il tempo di caricamento delle pagine alcune volte prima e dopo aver apportato modifiche per ottenere la media dei risultati.</span><span class="sxs-lookup"><span data-stu-id="a83b9-132">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="a83b9-133">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="a83b9-133">Related topics</span></span>

[<span data-ttu-id="a83b9-134">Ottimizzare le prestazioni di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a83b9-134">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="a83b9-135">Ottimizzare le prestazioni di Office 365</span><span class="sxs-lookup"><span data-stu-id="a83b9-135">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="a83b9-136">Prestazioni nell'esperienza moderna di SharePoint</span><span class="sxs-lookup"><span data-stu-id="a83b9-136">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/it-IT/sharepoint/modern-experience-performance.md)

[<span data-ttu-id="a83b9-137">Reti per la distribuzione di contenuti</span><span class="sxs-lookup"><span data-stu-id="a83b9-137">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="a83b9-138">Usare la rete per la distribuzione di contenuti di Office 365 con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a83b9-138">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
