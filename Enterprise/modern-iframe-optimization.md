---
title: Ottimizzare gli iFrame nelle pagine classiche e moderne del sito di pubblicazione di SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/17/2019
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
description: Informazioni su come ottimizzare le prestazioni degli iFrame nelle pagine classiche e moderne del sito di pubblicazione di SharePoint Online.
ms.openlocfilehash: 676407108db1669240df76438ff2b8739c4eaac1
ms.sourcegitcommit: c7764503422922cb333b05d54e8ebbdb894df2f9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/18/2019
ms.locfileid: "37028223"
---
# <a name="optimize-iframes-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a><span data-ttu-id="814df-103">Ottimizzare gli iFrame nelle pagine classiche e moderne del sito di pubblicazione di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="814df-103">Optimize iFrames in SharePoint Online modern and classic publishing site pages</span></span>

<span data-ttu-id="814df-104">Gli iFrame possono essere utili per visualizzare in anteprima contenuto complesso, ad esempio video o altri elementi multimediali.</span><span class="sxs-lookup"><span data-stu-id="814df-104">iFrames can be useful for previewing rich content such as videos or other media.</span></span> <span data-ttu-id="814df-105">Tuttavia, poiché gli iFrame caricano una pagina distinta nella pagina del sito di SharePoint, il contenuto caricato nell'iFrame potrebbe contenere immagini, video o altri elementi di grandi dimensioni che incidono sui tempi di caricamento complessivi della pagina e che non è possibile controllare nella pagina.</span><span class="sxs-lookup"><span data-stu-id="814df-105">However, because iFrames load a separate page within the SharePoint site page, content loaded in the iFrame could contain large images, videos or other elements that can contribute to overall page load times and that you cannot control on the page.</span></span> <span data-ttu-id="814df-106">Questo articolo illustra come determinare il modo in cui gli iFrame nelle pagine influiscono sulla latenza percepita dall'utente e su come risolvere i problemi comuni.</span><span class="sxs-lookup"><span data-stu-id="814df-106">This article will help you understand how to determine how iFrames in your pages affect user perceived latency, and how to remediate common issues.</span></span>

>[!NOTE]
><span data-ttu-id="814df-107">Per altre informazioni sulle prestazioni nei siti moderni di SharePoint Online, vedere [Prestazioni nell'esperienza moderna di SharePoint](https://docs.microsoft.com/it-IT/sharepoint/modern-experience-performance).</span><span class="sxs-lookup"><span data-stu-id="814df-107">For more information about performance in SharePoint Online modern sites, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/it-IT/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts-using-iframes"></a><span data-ttu-id="814df-108">Usare lo strumento Diagnostica pagine per SharePoint per analizzare le Web part che usano iFrame</span><span class="sxs-lookup"><span data-stu-id="814df-108">Use the Page Diagnostics for SharePoint tool to analyze web parts using iFrames</span></span>

<span data-ttu-id="814df-109">Lo **strumento Diagnostica pagine per SharePoint** è un'estensione del browser per Chrome e per [Microsoft Edge versione 77 o successive](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8) che consente di analizzare le pagine del sito di pubblicazione di SharePoint sia classiche che moderne.</span><span class="sxs-lookup"><span data-stu-id="814df-109">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="814df-110">Lo strumento fornisce un report per ogni pagina analizzata che mostra le prestazioni della pagina rispetto a un set di criteri di prestazioni definito.</span><span class="sxs-lookup"><span data-stu-id="814df-110">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="814df-111">Per installare e conoscere lo strumento Diagnostica pagine per SharePoint, visitare [Usare lo strumento Diagnostica pagine per SharePoint Online](page-diagnostics-for-spo.md).</span><span class="sxs-lookup"><span data-stu-id="814df-111">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="814df-112">Quando si analizza una pagina del sito di SharePoint con lo strumento Diagnostica pagine per SharePoint, è possibile visualizzare le informazioni sulle Web part che contengono iFrame nel riquadro _Diagnostic tests_ (Test diagnostici).</span><span class="sxs-lookup"><span data-stu-id="814df-112">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about web parts containing iFrames in the _Diagnostic tests_ pane.</span></span> <span data-ttu-id="814df-113">La metrica di base è la stessa per le pagine classiche e moderne.</span><span class="sxs-lookup"><span data-stu-id="814df-113">The baseline metric is the same for modern and classic pages.</span></span>

<span data-ttu-id="814df-114">I risultati possibili includono:</span><span class="sxs-lookup"><span data-stu-id="814df-114">Possible results include:</span></span>

- <span data-ttu-id="814df-115">**Attention required** (rosso): attenzione richiesta, la pagina contiene **tre o più** Web part che usano iFrame</span><span class="sxs-lookup"><span data-stu-id="814df-115">**Attention required** (red): The page contains **three or more** web parts using iFrames</span></span>
- <span data-ttu-id="814df-116">**Improvement opportunities** (giallo): opportunità di miglioramento, la pagina contiene **una o due** Web part che usano iFrame</span><span class="sxs-lookup"><span data-stu-id="814df-116">**Improvement opportunities** (yellow): The page contains **one or two** web parts using iFrames</span></span>
- <span data-ttu-id="814df-117">**No action required** (verde): nessuna azione necessaria, la pagina non contiene Web part che usano iFrame</span><span class="sxs-lookup"><span data-stu-id="814df-117">**No action required** (green): The page contains no web parts using iFrames</span></span>

<span data-ttu-id="814df-118">Se il risultato **Web parts using iFrames detected** (Rilevate Web che usano iFrame) compare nella sezione **Improvement opportunities** o **Attention required** dei risultati, fare clic sul risultato per vedere le Web part che contengono iFrame.</span><span class="sxs-lookup"><span data-stu-id="814df-118">If the **Web parts using iFrames detected** result appears in either the **Improvement opportunities** or **Attention required)** section of the results, you can click the result to see the web parts that contain iFrames.</span></span>

![Risultato dello strumento Diagnostica pagine](media/modern-portal-optimization/pagediag-iframe-yellow.png)

## <a name="remediate-iframe-performance-issues"></a><span data-ttu-id="814df-120">Risolvere i problemi di prestazioni degli iFrame</span><span class="sxs-lookup"><span data-stu-id="814df-120">Remediate iFrame performance issues</span></span>

<span data-ttu-id="814df-121">Usare il risultato **Web parts using iFrames detected** (Rilevate Web che usano iFrame) nello strumento Diagnostica pagine per determinare quali Web part contengono iFrame e potrebbero contribuire a rallentare i tempi di caricamento delle pagine.</span><span class="sxs-lookup"><span data-stu-id="814df-121">Use the **Web parts using iFrames detected** result in the Page Diagnostic tool to determine which web parts contain iFrames and may be contributing to slow page load times.</span></span>

<span data-ttu-id="814df-122">Gli iFrame sono intrinsecamente lenti perché caricano una pagina esterna separata che include tutto il contenuto associato, come elementi JavaScript, CSS e framework, aumentando potenzialmente il sovraccarico della pagina del sito di un fattore di due o più.</span><span class="sxs-lookup"><span data-stu-id="814df-122">iFrames are inherently slow because they load a separate external page including all associated content such as javascript, CSS and framework elements, potentially increasing the overhead of the site page by a factor of two or more.</span></span>

<span data-ttu-id="814df-123">Seguire le indicazioni riportate di seguito per garantire un uso ottimale degli iFrame.</span><span class="sxs-lookup"><span data-stu-id="814df-123">Follow the guidance below to ensure optimal use of iFrames.</span></span>

- <span data-ttu-id="814df-124">Se possibile, usare immagini al posto degli iFrame se l'anteprima è piccola o non interattiva.</span><span class="sxs-lookup"><span data-stu-id="814df-124">When possible, use images instead of iFrames if the preview is small to begin with or non-interactive.</span></span>
- <span data-ttu-id="814df-125">Se è necessario usare gli iFrame, ridurne il numero al minimo e/o spostarli all’esterno del viewport.</span><span class="sxs-lookup"><span data-stu-id="814df-125">If iFrames must be used, minimize the number and/or move them out of the viewport.</span></span>
- <span data-ttu-id="814df-126">I file di Office incorporati, come i file di Word, Excel e PowerPoint, sono interattivi, ma sono lenti da caricare.</span><span class="sxs-lookup"><span data-stu-id="814df-126">Embedded Office files like Word, Excel and PowerPoint are interactive, but are slow to load.</span></span> <span data-ttu-id="814df-127">Anteprime delle immagini con un collegamento al documento completo offriranno spesso prestazioni migliori.</span><span class="sxs-lookup"><span data-stu-id="814df-127">Image thumbnails with a link to the full document will often perform better.</span></span>
- <span data-ttu-id="814df-128">I video di YouTube e i feed di Twitter incorporati tendono a offrire prestazioni migliori negli iFrame, ma questi tipi di incorporamento vanno usati con giudizio.</span><span class="sxs-lookup"><span data-stu-id="814df-128">Embedded YouTube videos and Twitter feeds tend to perform better in iFrames, but use these kinds of embeds judiciously.</span></span>
- <span data-ttu-id="814df-129">Le Web part isolate rappresentano un'eccezione accettabile, ma ridurne al minimo il numero e l'impiego nel viewport.</span><span class="sxs-lookup"><span data-stu-id="814df-129">Isolated web parts are a reasonable exception, but minimize their number and placement in the viewport.</span></span>
- <span data-ttu-id="814df-130">Se un iFrame si trova all'esterno del viewport, è consigliabile usare un _IntersectionObserver_ per posticipare il rendering dell'iFrame al momento in cui diventa visibile.</span><span class="sxs-lookup"><span data-stu-id="814df-130">If an iFrame is located out of the viewport, consider using an _IntersectionObserver_ to delay rendering the iFrame until it comes into view.</span></span>

<span data-ttu-id="814df-131">Prima di eseguire le revisioni delle pagine per correggere i problemi di prestazioni, prendere nota del tempo di caricamento delle pagine nei risultati dell'analisi.</span><span class="sxs-lookup"><span data-stu-id="814df-131">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="814df-132">Eseguire di nuovo lo strumento dopo la revisione per verificare se il nuovo risultato ora rientra nei parametri di riferimento e controllare il tempo di caricamento della nuova pagina per verificare se è migliorato.</span><span class="sxs-lookup"><span data-stu-id="814df-132">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![Risultati del tempo di caricamento delle pagine](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="814df-134">Il tempo di caricamento delle pagine può variare in base a un'ampia varietà di fattori, ad esempio il carico di rete, l'ora del giorno e altre condizioni transitorie.</span><span class="sxs-lookup"><span data-stu-id="814df-134">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="814df-135">È consigliabile verificare il tempo di caricamento delle pagine alcune volte prima e dopo aver apportato modifiche per ottenere la media dei risultati.</span><span class="sxs-lookup"><span data-stu-id="814df-135">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="814df-136">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="814df-136">Related topics</span></span>

[<span data-ttu-id="814df-137">Ottimizzare le prestazioni di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="814df-137">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="814df-138">Ottimizzare le prestazioni di Office 365</span><span class="sxs-lookup"><span data-stu-id="814df-138">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="814df-139">Prestazioni nell'esperienza moderna di SharePoint</span><span class="sxs-lookup"><span data-stu-id="814df-139">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/it-IT/sharepoint/modern-experience-performance.md)
