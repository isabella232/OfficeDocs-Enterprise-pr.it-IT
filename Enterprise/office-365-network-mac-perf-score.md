---
title: Valutazione della rete di Office 365 (Preview)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Valutazione della rete di Office 365 (Preview)
ms.openlocfilehash: f919eeb2771095502865b4a5079b91eb8d7efe36
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106350"
---
# <a name="office-365-network-assessment-preview"></a><span data-ttu-id="3f90a-103">Valutazione della rete di Office 365 (Preview)</span><span class="sxs-lookup"><span data-stu-id="3f90a-103">Office 365 network assessment (preview)</span></span>

<span data-ttu-id="3f90a-104">La valutazione della rete di Office 365 indica l'impatto dell'esperienza utente relativa dalla connettività di rete del cliente.</span><span class="sxs-lookup"><span data-stu-id="3f90a-104">The Office 365 network assessment indicates the relative user experience impact from customer network connectivity.</span></span> <span data-ttu-id="3f90a-105">L'impatto di qualsiasi connettività di rete di Microsoft è escluso da questo per consentire ai clienti di ottimizzare le progettazioni di rete per le quali sono responsabili.</span><span class="sxs-lookup"><span data-stu-id="3f90a-105">The impact of any Microsoft owned network connectivity is excluded from this to enable customers to optimize network designs for which they are responsible.</span></span>

<span data-ttu-id="3f90a-106">Viene calcolato in base alle misure che influiscono sull'esperienza degli utenti nei carichi di lavoro chiave di Office 365 e che vengono visualizzate come percentuali con un intervallo compreso tra 0 e 100.</span><span class="sxs-lookup"><span data-stu-id="3f90a-106">It is calculated from measurements that impact user experience in key Office 365 workloads and shown as a percentage with a range of 0 to 100.</span></span>

<span data-ttu-id="3f90a-107">Un punteggio di rete molto basso suggerisce che i client di Office 365 avranno problemi significativi per la connessione o il reattivo degli utenti.</span><span class="sxs-lookup"><span data-stu-id="3f90a-107">A very low network score suggests that Office 365 clients will have significant problems connecting or remaining user responsive.</span></span> <span data-ttu-id="3f90a-108">Un punteggio di 80% rappresenta la connettività di rete in cui non è consigliabile ricevere reclami da parte dell'utente sull'esperienza utente di Office 365 a causa delle prestazioni di rete.</span><span class="sxs-lookup"><span data-stu-id="3f90a-108">A score of 80% represents network connectivity where you should not expect to receive user complaints about your Office 365 user experience due to your network performance.</span></span> <span data-ttu-id="3f90a-109">Man mano che vengono apportati miglioramenti alla connettività di rete, questo punteggio aumenterà insieme all'esperienza utente.</span><span class="sxs-lookup"><span data-stu-id="3f90a-109">As network connectivity improvements are made, this score will increase along with user experience.</span></span>

>[!IMPORTANT]
><span data-ttu-id="3f90a-110">Suggerimenti per le prestazioni di rete, approfondimenti e valutazioni nell'interfaccia di amministrazione di Microsoft 365 è attualmente in stato di anteprima ed è disponibile solo per i tenant di Office 365 che sono stati registrati nel programma di anteprima delle funzionalità.</span><span class="sxs-lookup"><span data-stu-id="3f90a-110">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="3f90a-111">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="3f90a-111">Exchange Online</span></span>

<span data-ttu-id="3f90a-112">Per Exchange Online, viene misurata la latenza TCP dal computer client al front end server di Exchange.</span><span class="sxs-lookup"><span data-stu-id="3f90a-112">For Exchange Online the TCP latency from the client machine to the Exchange front end server is measured.</span></span> <span data-ttu-id="3f90a-113">Questo può influire sulla distanza che la rete percorre nei clienti LAN e WAN.</span><span class="sxs-lookup"><span data-stu-id="3f90a-113">This can be impacted by the distance the network travels over the customers LAN and WAN.</span></span> <span data-ttu-id="3f90a-114">Può anche essere influenzato da dispositivi o servizi di intermediazione di rete che ritardano la connettività o causano il rimandato dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="3f90a-114">It can also be impacted by network intermediary devices or services which delay the connectivity or cause packets to be resent.</span></span>

## <a name="sharepoint-online"></a><span data-ttu-id="3f90a-115">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3f90a-115">SharePoint Online</span></span>

<span data-ttu-id="3f90a-116">Per SharePoint Online, la velocità di download disponibile per un utente per l'accesso a un documento viene misurata.</span><span class="sxs-lookup"><span data-stu-id="3f90a-116">For SharePoint Online the download speed available for a user to access a document is measured.</span></span> <span data-ttu-id="3f90a-117">Questo può essere influenzato dalla larghezza di banda disponibile nei circuiti di rete tra il computer client e la rete di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3f90a-117">This can be impacted by the bandwidth available on network circuits between the client machine and Microsoft’s network.</span></span> <span data-ttu-id="3f90a-118">È inoltre spesso influenzato dalla congestione della rete che esiste nei colli di bottiglia nei dispositivi di rete complessi o nelle aree Wi-Fi con una copertura scadente.</span><span class="sxs-lookup"><span data-stu-id="3f90a-118">It is also often impacted by network congestion that exists in bottlenecks in complex network devices or in poor coverage Wi-Fi areas.</span></span>

## <a name="microsoft-teams"></a><span data-ttu-id="3f90a-119">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3f90a-119">Microsoft Teams</span></span>

<span data-ttu-id="3f90a-120">Per Microsoft teams la qualità della rete viene misurata come latenza UDP, jitter UDP e perdita di pacchetti UDP.</span><span class="sxs-lookup"><span data-stu-id="3f90a-120">For Microsoft Teams the Network quality is measured as UDP latency, UDP jitter, and UDP packet loss.</span></span> <span data-ttu-id="3f90a-121">UDP viene utilizzato per la connettività multimediale di chiamata e di audioconferenza per Microsoft teams.</span><span class="sxs-lookup"><span data-stu-id="3f90a-121">UDP is used for call and conferencing audio and video media connectivity for Microsoft Teams.</span></span> <span data-ttu-id="3f90a-122">Questo può influire sugli stessi fattori di latenza e velocità di download, oltre agli spazi di connettività nel supporto UDP di una rete, poiché UDP è configurato separatamente per il protocollo TCP più comune.</span><span class="sxs-lookup"><span data-stu-id="3f90a-122">This can be impacted by the same factors as for latency and download speed in addition to connectivity gaps in a network’s UDP support since UDP is configured separately to the more common TCP protocol.</span></span>

## <a name="tenant-network-score-and-office-location-network-score"></a><span data-ttu-id="3f90a-123">Punteggio di rete tenant e posizione di rete di Office location</span><span class="sxs-lookup"><span data-stu-id="3f90a-123">Tenant network score and office location network score</span></span>

<span data-ttu-id="3f90a-124">Un punteggio di rete misura la progettazione del perimetro di rete di una posizione di Office alla rete di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3f90a-124">A network score measures the design of the network perimeter of an office location to Microsoft’s network.</span></span> <span data-ttu-id="3f90a-125">I miglioramenti apportati al perimetro della rete sono migliori in ogni posizione di Office o in cui è possibile aggregare la connettività di rete possono essere presenti miglioramenti che influiscono su più percorsi.</span><span class="sxs-lookup"><span data-stu-id="3f90a-125">Improvements to the network perimeter is best done at each office location, or where network connectivity is aggregated there may be improvements that impact multiple locations.</span></span>
<span data-ttu-id="3f90a-126">Viene visualizzato un punteggio di rete per l'intero tenant di Office 365 nella pagina Panoramica delle prestazioni di rete e uno specifico punteggio di rete per ogni posizione di Office rilevata nella pagina di riepilogo di tale percorso.</span><span class="sxs-lookup"><span data-stu-id="3f90a-126">We show a network score for the whole Office 365 tenant on the network performance overview page and a specific network score for each detected office location on that location’s summary page.</span></span>

## <a name="network-score-panel"></a><span data-ttu-id="3f90a-127">Pannello Punteggio di rete</span><span class="sxs-lookup"><span data-stu-id="3f90a-127">Network score panel</span></span>

<span data-ttu-id="3f90a-128">Ogni punteggio di rete se per il tenant o per una specifica posizione di Office viene visualizzato un riquadro con informazioni dettagliate sul punteggio.</span><span class="sxs-lookup"><span data-stu-id="3f90a-128">Each network score whether for the tenant or for a specific office location shows a panel with details about the score.</span></span> <span data-ttu-id="3f90a-129">Questo pannello Visualizza un grafico a barre dello score sia come percentuale che come punti totali per ogni carico di lavoro del componente, compresi solo i carichi di lavoro in cui sono stati ricevuti i dati di misurazione.</span><span class="sxs-lookup"><span data-stu-id="3f90a-129">This panel shows a bar chart of the score both as a percentage and as the total points for each component workload including only workloads where measurement data was received.</span></span> <span data-ttu-id="3f90a-130">Per un punteggio di rete per la posizione di Office viene mostrato anche un benchmark che è il mediano di tutti i client di Office 365 che hanno segnalato dati nella stessa città del percorso dell'ufficio.</span><span class="sxs-lookup"><span data-stu-id="3f90a-130">For an office location network score we also show a benchmark which is the median of all Office 365 clients that reported data in the same City as your office location.</span></span>

<span data-ttu-id="3f90a-131">La ripartizione dei punteggi nel pannello Visualizza il punteggio per ogni carico di lavoro del componente.</span><span class="sxs-lookup"><span data-stu-id="3f90a-131">The score breakdown in the panel shows the score for each of the component workloads.</span></span>

<span data-ttu-id="3f90a-132">La cronologia dei punteggi Visualizza gli ultimi 30 giorni dello score e del benchmark.</span><span class="sxs-lookup"><span data-stu-id="3f90a-132">The score history shows the past 30 days of the score and the benchmark.</span></span>

## <a name="related-topics"></a><span data-ttu-id="3f90a-133">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="3f90a-133">Related topics</span></span>

[<span data-ttu-id="3f90a-134">Suggerimenti relativi alle prestazioni di rete nell'interfaccia di amministrazione di Microsoft 365 (anteprima)</span><span class="sxs-lookup"><span data-stu-id="3f90a-134">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="3f90a-135">Informazioni sulle prestazioni di rete di Office 365 (anteprima)</span><span class="sxs-lookup"><span data-stu-id="3f90a-135">Office 365 network performance insights (preview)</span></span>](office-365-network-mac-perf-insights.md)

[<span data-ttu-id="3f90a-136">Strumento di onboarding di rete di Office 365 nell'interfaccia di amministrazione di M365 (anteprima)</span><span class="sxs-lookup"><span data-stu-id="3f90a-136">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
