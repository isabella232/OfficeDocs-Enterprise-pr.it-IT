---
title: Informazioni sulle prestazioni di rete di Office 365 (anteprima)
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
description: Informazioni sulle prestazioni di rete di Office 365 (anteprima)
ms.openlocfilehash: 2e57ffabec5b2172cb36f10135406ddda95bc1c5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106357"
---
# <a name="office-365-network-performance-insights-preview"></a><span data-ttu-id="1f365-103">Informazioni sulle prestazioni di rete di Office 365 (anteprima)</span><span class="sxs-lookup"><span data-stu-id="1f365-103">Office 365 network performance insights (preview)</span></span>

<span data-ttu-id="1f365-104">Le pagine di Microsoft 365 Admin Center Network performance mostrano Office 365 Network Insights che possono essere utili per la progettazione di perimetri di rete per le posizioni di Office.</span><span class="sxs-lookup"><span data-stu-id="1f365-104">The Microsoft 365 Admin Center network performance pages show Office 365 network insights which can help in designing network perimeters for your office locations.</span></span> <span data-ttu-id="1f365-105">Sono disponibili cinque informazioni specifiche sulla rete che possono essere visualizzate per ogni posizione di Office.</span><span class="sxs-lookup"><span data-stu-id="1f365-105">There are five specific network insights that may be shown for each office location.</span></span>

>[!IMPORTANT]
><span data-ttu-id="1f365-106">Suggerimenti per le prestazioni di rete, approfondimenti e valutazioni nell'interfaccia di amministrazione di Microsoft 365 è attualmente in stato di anteprima ed è disponibile solo per i tenant di Office 365 che sono stati registrati nel programma di anteprima delle funzionalità.</span><span class="sxs-lookup"><span data-stu-id="1f365-106">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="backhauled-network-egress"></a><span data-ttu-id="1f365-107">Uscita di rete con backhauling</span><span class="sxs-lookup"><span data-stu-id="1f365-107">Backhauled network egress</span></span>

<span data-ttu-id="1f365-108">La distanza tra la posizione dell'utente e l'uscita di rete è maggiore di 500 miglia (800 km) e questo dovrebbe influire negativamente sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="1f365-108">The distance from the user location to the network egress is greater than 500 miles (800 kilometers) and this is expected to be impacting performance.</span></span> <span data-ttu-id="1f365-109">L'uscita locale più vicina all'utente è consigliata.</span><span class="sxs-lookup"><span data-stu-id="1f365-109">Local egress closer to the user is recommended.</span></span>

<span data-ttu-id="1f365-110">Ciò indica che la distanza tra l'area di lavoro e l'uscita di rete è superiore a 500 miglia.</span><span class="sxs-lookup"><span data-stu-id="1f365-110">This identifies that the distance between the office location and the network egress is more than 500 miles.</span></span> <span data-ttu-id="1f365-111">La posizione di Office è identificata da una posizione del computer client offuscata e il percorso dell'uscita di rete viene identificato utilizzando l'indirizzo IP inverso nei database delle posizioni.</span><span class="sxs-lookup"><span data-stu-id="1f365-111">The office location is identified by an obfuscated client machine location and the network egress location is identified by using reverse IP Address to location databases.</span></span> <span data-ttu-id="1f365-112">La posizione di Office potrebbe non essere accurata se i servizi di posizione di Windows sono disabilitati nei computer.</span><span class="sxs-lookup"><span data-stu-id="1f365-112">The office location may be inaccurate if Windows Location Services is disabled on machines.</span></span> <span data-ttu-id="1f365-113">La posizione di uscita della rete potrebbe non essere accurata se le informazioni sul database degli indirizzi IP inversi non sono accurate.</span><span class="sxs-lookup"><span data-stu-id="1f365-113">The network egress location may be inaccurate if the reverse IP Address database information is inaccurate.</span></span>

<span data-ttu-id="1f365-114">I dettagli relativi a questa intuizione includono l'ubicazione dell'ufficio, la posizione di uscita della rete e la distanza tra di essi.</span><span class="sxs-lookup"><span data-stu-id="1f365-114">Details for this insight include the office location, the network egress location, and the distance between them.</span></span>

<span data-ttu-id="1f365-115">Per questa intuizione si consiglia l'uscita di rete più vicina alla posizione di Office in modo che la connettività possa essere instradata in maniera ottimale alla rete Microsoft su Internet e su Office 365 Service front doors.</span><span class="sxs-lookup"><span data-stu-id="1f365-115">For this insight we would recommend network egress closer to the office location so that connectivity can route optimally to Microsoft's network on the Internet and onto Office 365 service front doors.</span></span> <span data-ttu-id="1f365-116">Dopo aver chiuso l'uscita di rete per gli utenti, le posizioni di Office consentono anche di migliorare le prestazioni in futuro, in quanto Microsoft espande entrambi i punti di rete di presenza e le porte anteriori del servizio Office 365 in futuro.</span><span class="sxs-lookup"><span data-stu-id="1f365-116">Having close network egress to users office locations also allows for improved performance in the future as Microsoft expands both network points of presence and Office 365 service front doors in the future.</span></span>

<span data-ttu-id="1f365-117">Questa intuizione è abbreviata in "uscita" in alcune visualizzazioni di riepilogo.</span><span class="sxs-lookup"><span data-stu-id="1f365-117">This insight is abbreviated as "Egress" in some summary views.</span></span>

## <a name="better-performance-detected-for-customers-near-you"></a><span data-ttu-id="1f365-118">Migliorare le prestazioni rilevate per i clienti nelle vicinanze</span><span class="sxs-lookup"><span data-stu-id="1f365-118">Better performance detected for customers near you</span></span>

<span data-ttu-id="1f365-119">Poiché un numero significativo di clienti nell'area metropolitana ha prestazioni migliori rispetto agli utenti dell'organizzazione in questa posizione di ufficio.</span><span class="sxs-lookup"><span data-stu-id="1f365-119">Since a significant number of customers in your metro area have better performance than users in your organization at this office location.</span></span>

<span data-ttu-id="1f365-120">In questo modo vengono analizzate le prestazioni aggregate dei clienti di Office 365 nella stessa città del percorso di Office.</span><span class="sxs-lookup"><span data-stu-id="1f365-120">This looks at the aggregate performance of Office 365 customers in the same city as this office location.</span></span>

![Prestazioni di rete relative](Media/m365-mac-perf/m365-mac-perf-relative-perf.png)

<span data-ttu-id="1f365-122">Viene calcolata la percentuale di clienti di Office 365 nella stessa città in bucket di prestazioni migliori.</span><span class="sxs-lookup"><span data-stu-id="1f365-122">We calculate the percentage of Office 365 customers in the same city in better performance buckets.</span></span> <span data-ttu-id="1f365-123">Se questo numero è pari al 10% di più, viene visualizzato l'Insight sulla rete.</span><span class="sxs-lookup"><span data-stu-id="1f365-123">If this number if 10% of more then we show the network insight.</span></span>

<span data-ttu-id="1f365-124">Questa intuizione è abbreviata in "peer" in alcune visualizzazioni di riepilogo.</span><span class="sxs-lookup"><span data-stu-id="1f365-124">This insight is abbreviated as "Peers" in some summary views.</span></span>

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a><span data-ttu-id="1f365-125">Utilizzo di una porta anteriore del servizio Exchange Online non ottimale</span><span class="sxs-lookup"><span data-stu-id="1f365-125">Use of a non-optimal Exchange Online service front door</span></span>

<span data-ttu-id="1f365-126">L'utente non è connesso a un'ottima porta di servizio di Office 365 e questo dovrebbe influire negativamente sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="1f365-126">The user is not connecting to an optimal Office 365 service front door and this is expected to be impacting performance.</span></span>

<span data-ttu-id="1f365-127">Vengono elencate le porte anteriori del servizio Exchange Online che sono adatte per l'utilizzo da parte di Office location City con buone prestazioni.</span><span class="sxs-lookup"><span data-stu-id="1f365-127">We list Exchange Online service front doors which are suitable for use from the office location city with good performance.</span></span> <span data-ttu-id="1f365-128">Se il test corrente Mostra l'utilizzo di una porta di ingresso del servizio Exchange Online non presente nell'elenco, verrà chiamato questo suggerimento.</span><span class="sxs-lookup"><span data-stu-id="1f365-128">If the current test shows use of an Exchange Online service front door not on this list, then we call out this recommendation.</span></span>

<span data-ttu-id="1f365-129">L'utilizzo di una porta anteriore del servizio Exchange Online non ottimale può essere causato da un backhaul della rete prima dell'uscita della rete aziendale, nel qual caso è consigliabile l'uscita di rete locale e diretta.</span><span class="sxs-lookup"><span data-stu-id="1f365-129">Use of a non-optimal Exchange Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="1f365-130">Potrebbe anche essere causato dall'utilizzo di un server resolver DNS ricorsivo remoto, nel qual caso si consiglia di allineare il server resolver ricorsivo DNS con l'uscita di rete.</span><span class="sxs-lookup"><span data-stu-id="1f365-130">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

<span data-ttu-id="1f365-131">Questa intuizione è abbreviata in "routing" in alcune visualizzazioni di riepilogo.</span><span class="sxs-lookup"><span data-stu-id="1f365-131">This insight is abbreviated as "Routing" in some summary views.</span></span>

## <a name="use-of-non-optimal-sharepoint-online-service-front-door"></a><span data-ttu-id="1f365-132">Utilizzo di porta anteriore del servizio SharePoint Online non ottimale</span><span class="sxs-lookup"><span data-stu-id="1f365-132">Use of non-optimal SharePoint Online service front door</span></span>

<span data-ttu-id="1f365-133">L'utente non si connette al portale principale del servizio SharePoint Online più vicino.</span><span class="sxs-lookup"><span data-stu-id="1f365-133">The user is not connecting to the closest SharePoint Online service front door.</span></span> <span data-ttu-id="1f365-134">Questo dovrebbe influire sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="1f365-134">This is expected to be impacting performance.</span></span>

<span data-ttu-id="1f365-135">Identificare la porta di ingresso del servizio SharePoint Online a cui si connette il client di test.</span><span class="sxs-lookup"><span data-stu-id="1f365-135">We identify the SharePoint Online service front door that the test client is connecting to.</span></span> <span data-ttu-id="1f365-136">Quindi, per la città Ubicazione di Office, viene confrontato con il servizio SharePoint Online previsto per la città.</span><span class="sxs-lookup"><span data-stu-id="1f365-136">Then for the office location city we compare that to the expected SharePoint Online service front door for that city.</span></span> <span data-ttu-id="1f365-137">In caso contrario, è consigliabile eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="1f365-137">If it doesn't match, then we make this recommendation.</span></span>

<span data-ttu-id="1f365-138">Questa intuizione è abbreviata in "AFD" in alcune visualizzazioni di riepilogo.</span><span class="sxs-lookup"><span data-stu-id="1f365-138">This insight is abbreviated as "Afd" in some summary views.</span></span>

## <a name="low-download-speed-from-sharepoint-front-door"></a><span data-ttu-id="1f365-139">Velocità di download bassa dalla porta di ingresso di SharePoint</span><span class="sxs-lookup"><span data-stu-id="1f365-139">Low download speed from SharePoint front door</span></span>

<span data-ttu-id="1f365-140">È stata rilevata una velocità di download di rete ottimale che ha un impatto sul tempo necessario per caricare i documenti da OneDrive for business.</span><span class="sxs-lookup"><span data-stu-id="1f365-140">Sub optimal network download speed detected which impacts how long it takes to load documents from OneDrive for Business.</span></span>

<span data-ttu-id="1f365-141">La velocità di download che un utente può ottenere dalle porte frontali di servizio di SharePoint Online e OneDrive for business è misurata in megabyte al secondo (MBps).</span><span class="sxs-lookup"><span data-stu-id="1f365-141">The download speed that a user can get from SharePoint Online and OneDrive for Business service front doors is measured in megabytes per second (MBps).</span></span> <span data-ttu-id="1f365-142">Se questo valore è inferiore a 1 MBps, verrà fornita questa panoramica.</span><span class="sxs-lookup"><span data-stu-id="1f365-142">If this value is less than 1 MBps then we provide this insight.</span></span>

<span data-ttu-id="1f365-143">Per migliorare la velocità di download, potrebbe essere necessario aumentare la larghezza di banda di un utente.</span><span class="sxs-lookup"><span data-stu-id="1f365-143">To improve download speed that a user can get bandwidth may need to be increased.</span></span> <span data-ttu-id="1f365-144">In alternativa, è possibile che vi sia una congestione della rete tra i computer degli utenti nell'ubicazione dell'ufficio e la porta di servizio di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="1f365-144">Alternatively, there may be network congestion between user machines at the office location and the SharePoint Online service front door.</span></span> <span data-ttu-id="1f365-145">A volte viene chiamato perdita congestizia e limita la velocità di download disponibile per gli utenti anche se è disponibile una larghezza di banda sufficiente.</span><span class="sxs-lookup"><span data-stu-id="1f365-145">This is sometimes called congestive loss and it restricts the download speed available to users even if sufficient bandwidth is available.</span></span>

<span data-ttu-id="1f365-146">Questa intuizione è abbreviata come "velocità effettiva" in alcune visualizzazioni di riepilogo.</span><span class="sxs-lookup"><span data-stu-id="1f365-146">This insight is abbreviated as "Throughput" in some summary views.</span></span>

## <a name="related-topics"></a><span data-ttu-id="1f365-147">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="1f365-147">Related topics</span></span>

[<span data-ttu-id="1f365-148">Suggerimenti relativi alle prestazioni di rete nell'interfaccia di amministrazione di Microsoft 365 (anteprima)</span><span class="sxs-lookup"><span data-stu-id="1f365-148">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="1f365-149">Valutazione della rete di Office 365 (Preview)</span><span class="sxs-lookup"><span data-stu-id="1f365-149">Office 365 network assessment (preview)</span></span>](office-365-network-mac-perf-score.md)

[<span data-ttu-id="1f365-150">Strumento di onboarding di rete di Office 365 nell'interfaccia di amministrazione di M365 (anteprima)</span><span class="sxs-lookup"><span data-stu-id="1f365-150">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
