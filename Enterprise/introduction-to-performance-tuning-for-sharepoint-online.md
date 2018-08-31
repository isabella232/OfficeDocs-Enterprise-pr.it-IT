---
title: Introduzione all'ottimizzazione delle prestazioni per SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: In questo articolo viene illustrato quali aspetti specifici, è necessario prendere in considerazione durante la progettazione di pagine per ottimizzare le prestazioni di SharePoint Online.
ms.openlocfilehash: 96aeec19a6b582d0dc8701cd2e99329ec8ce156b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541125"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="ecc3e-103">Introduzione all'ottimizzazione delle prestazioni per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ecc3e-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="ecc3e-104">In questo articolo viene illustrato quali aspetti specifici, è necessario prendere in considerazione durante la progettazione di pagine per ottimizzare le prestazioni di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
  
## <a name="in-this-article"></a><span data-ttu-id="ecc3e-105">In questo articolo</span><span class="sxs-lookup"><span data-stu-id="ecc3e-105">In this article</span></span>

- <span data-ttu-id="ecc3e-106">[Metriche di SharePoint Online](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics) e [le conclusioni raggiunto causa dei dati](introduction-to-performance-tuning-for-sharepoint-online.md#data)</span><span class="sxs-lookup"><span data-stu-id="ecc3e-106">[SharePoint Online metrics](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics) and [Conclusions reached because of the data](introduction-to-performance-tuning-for-sharepoint-online.md#data)</span></span>
    
- [<span data-ttu-id="ecc3e-107">Utilizzare un account utente standard per il controllo delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="ecc3e-107">Use a standard user account when checking performance</span></span>](introduction-to-performance-tuning-for-sharepoint-online.md#standuser)
    
- <span data-ttu-id="ecc3e-108">[Categorie di connessione per l'ottimizzazione delle prestazioni](introduction-to-performance-tuning-for-sharepoint-online.md#connect): [connessione al Server](introduction-to-performance-tuning-for-sharepoint-online.md#server), [connessioni di rete](introduction-to-performance-tuning-for-sharepoint-online.md#network)e [connessione del Browser](introduction-to-performance-tuning-for-sharepoint-online.md#browser)</span><span class="sxs-lookup"><span data-stu-id="ecc3e-108">[Connection categories for performance tuning](introduction-to-performance-tuning-for-sharepoint-online.md#connect): [Server connection](introduction-to-performance-tuning-for-sharepoint-online.md#server), [Network connection](introduction-to-performance-tuning-for-sharepoint-online.md#network), and [Browser connection](introduction-to-performance-tuning-for-sharepoint-online.md#browser)</span></span>
    
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="ecc3e-109">Metriche di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ecc3e-109">SharePoint Online metrics</span></span>
<span data-ttu-id="ecc3e-110"><a name="spometrics"> </a></span><span class="sxs-lookup"><span data-stu-id="ecc3e-110"></span></span>

<span data-ttu-id="ecc3e-111">Le seguenti metriche generali per SharePoint Online forniscono dati reali sulle prestazioni:</span><span class="sxs-lookup"><span data-stu-id="ecc3e-111">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="ecc3e-112">Velocità di caricamento delle pagine</span><span class="sxs-lookup"><span data-stu-id="ecc3e-112">How fast pages load</span></span>
    
- <span data-ttu-id="ecc3e-113">Numero di round trip necessari per ogni pagina</span><span class="sxs-lookup"><span data-stu-id="ecc3e-113">How many round trips required per page</span></span>
    
- <span data-ttu-id="ecc3e-114">Problemi con il servizio</span><span class="sxs-lookup"><span data-stu-id="ecc3e-114">Issues with the service</span></span>
    
- <span data-ttu-id="ecc3e-115">Altri aspetti che causano la riduzione delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="ecc3e-115">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="ecc3e-116">Conclusioni in base ai dati</span><span class="sxs-lookup"><span data-stu-id="ecc3e-116">Conclusions reached because of the data</span></span>
<span data-ttu-id="ecc3e-117"><a name="data"> </a></span><span class="sxs-lookup"><span data-stu-id="ecc3e-117"></span></span>

<span data-ttu-id="ecc3e-118">I dati dicono:</span><span class="sxs-lookup"><span data-stu-id="ecc3e-118">The data tells us:</span></span>
  
- <span data-ttu-id="ecc3e-119">La maggior parte delle pagine garantisce buone prestazioni con SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-119">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="ecc3e-120">Le pagine non personalizzate si caricano molto rapidamente.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-120">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="ecc3e-121">OneDrive for Business, i siti del team e le pagine di sistema, ad esempio _layouts e così via, si caricano tutti rapidamente.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-121">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="ecc3e-122">La pagina più lenta di 1% di SharePoint Online impiega più di 5.000 millisecondi per caricarsi.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-122">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="ecc3e-p101">È possibile utilizzare un semplice test di benchmark per misurare le prestazioni confrontando il tempo di caricamento del proprio portale con il tempo di caricamento della home page di OneDrive for Business, perché utilizza alcune funzionalità personalizzate. Questo spesso sarà il primo passaggio che il supporto chiederà di completare durante la risoluzione dei problemi relativi alle prestazioni di rete.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-p101">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features. This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="ecc3e-125">Utilizzare un account utente standard per il controllo delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="ecc3e-125">Use a standard user account when checking performance</span></span>
<span data-ttu-id="ecc3e-126"><a name="standuser"> </a></span><span class="sxs-lookup"><span data-stu-id="ecc3e-126"></span></span>

<span data-ttu-id="ecc3e-127">Un amministratore della raccolta siti, proprietario del sito, Editor o collaboratore appartengono a gruppi di sicurezza aggiuntive, disporre di autorizzazioni aggiuntive e pertanto sono elementi aggiuntivi che SharePoint viene caricato in una pagina.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-127">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="ecc3e-128">Questa opzione è disponibile per SharePoint Online e SharePoint locale, ma in uno scenario in locale differenze saranno la stessa facilità inosservate come SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-128">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="ecc3e-129">Per valutare correttamente come una pagina verrà eseguite per gli utenti, è consigliabile utilizzare un account utente standard per evitare di caricare la creazione di controlli e un aumento del traffico relative ai gruppi di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-129">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="ecc3e-130">Categorie di connessione per l'ottimizzazione delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="ecc3e-130">Connection categories for performance tuning</span></span>
<span data-ttu-id="ecc3e-131"><a name="connect"> </a></span><span class="sxs-lookup"><span data-stu-id="ecc3e-131"></span></span>

<span data-ttu-id="ecc3e-p102">È possibile classificare le connessioni tra il server e l'utente in tre componenti principali. Prendere in considerazione tali componenti durante la progettazione delle pagine di SharePoint Online per comprendere i tempi di caricamento.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-p102">You can categorize the connections between the server and the user into three main components. Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="ecc3e-134">**Server.** I server che ospita Microsoft nei Data Center.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-134">**Server.** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="ecc3e-135">**Network.** Microsoft network, Internet e la rete locale tra i Data Center e gli utenti.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-135">**Network.** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="ecc3e-136">**Browser.** Dove viene caricata la pagina.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-136">**Browser.** Where the page is loaded.</span></span>
    
<span data-ttu-id="ecc3e-p103">All'interno di queste tre connessioni in genere esistono cinque motivi che causano il 95% delle pagine lente. Ciascuna di queste situazioni è illustrata in questo articolo:</span><span class="sxs-lookup"><span data-stu-id="ecc3e-p103">Within these three connections there are typically five reasons that cause 95% of slow pages. Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="ecc3e-139">Problemi di navigazione</span><span class="sxs-lookup"><span data-stu-id="ecc3e-139">Navigation issues</span></span>
    
- <span data-ttu-id="ecc3e-140">Rollup contenuto</span><span class="sxs-lookup"><span data-stu-id="ecc3e-140">Content roll up</span></span>
    
- <span data-ttu-id="ecc3e-141">File di grandi dimensioni</span><span class="sxs-lookup"><span data-stu-id="ecc3e-141">Large files</span></span>
    
- <span data-ttu-id="ecc3e-142">Numero elevato di richieste al server</span><span class="sxs-lookup"><span data-stu-id="ecc3e-142">Many requests to the server</span></span>
    
- <span data-ttu-id="ecc3e-143">Elaborazione di Web Part</span><span class="sxs-lookup"><span data-stu-id="ecc3e-143">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="ecc3e-144">Connessione al server</span><span class="sxs-lookup"><span data-stu-id="ecc3e-144">Server connection</span></span>
<span data-ttu-id="ecc3e-145"><a name="server"> </a></span><span class="sxs-lookup"><span data-stu-id="ecc3e-145"></span></span>

<span data-ttu-id="ecc3e-146">Molti dei problemi che influiscono sulle prestazioni di SharePoint locale valgono anche per SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-146">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="ecc3e-p104">Come previsto, è necessario prestare maggiore controllo sul funzionamento dei server con SharePoint locale. Con SharePoint Online le cose sono leggermente diverse. Più lavoro si fa fare al server, maggiore sarà il tempo necessario per il rendering di una pagina. Con SharePoint, la causa principale a questo proposito sono le pagine complesse con più web part.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-p104">As you would expect, you have far more control over how servers perform with on-premises SharePoint. With SharePoint Online things are a little different. The more work you make a server do, the longer it takes to render a page. With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="ecc3e-151">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ecc3e-151">SharePoint Online</span></span>
  
![Schermata del server online](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="ecc3e-153">SharePoint</span><span class="sxs-lookup"><span data-stu-id="ecc3e-153">SharePoint</span></span>
  
![Schermata del server in locale](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="ecc3e-p105">Con SharePoint Online, alcune richieste di pagine potrebbero effettivamente finire per chiamare più server. Si potrebbe finire con una matrice di richieste tra i server per una singola richiesta. Tali interazioni sono costose da una prospettiva di caricamento della pagina e rendono le operazioni lente.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-p105">With SharePoint Online, certain page requests may actually end up calling multiple servers. You could end up with a matrix of requests between servers for an individual request. These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="ecc3e-158">Esempi di tali interazioni da server a server sono:</span><span class="sxs-lookup"><span data-stu-id="ecc3e-158">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="ecc3e-159">Da Web a SQL Server</span><span class="sxs-lookup"><span data-stu-id="ecc3e-159">Web to SQL Servers</span></span>
    
- <span data-ttu-id="ecc3e-160">Da Web ai server applicazioni</span><span class="sxs-lookup"><span data-stu-id="ecc3e-160">Web to application servers</span></span>
    
<span data-ttu-id="ecc3e-p106">L'altra operazione che può rallentare le interazioni del server è la mancanza della cache. A differenza di SharePoint locale, esiste una possibilità molto piccola di raggiungere lo stesso server di una pagina visitata in precedenza. Ciò rende la memorizzazione degli oggetti nella cache obsoleta.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-p106">The other thing that can slow down server interactions is cache misses. Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="ecc3e-163">Connessione di rete</span><span class="sxs-lookup"><span data-stu-id="ecc3e-163">Network connection</span></span>
<span data-ttu-id="ecc3e-164"><a name="network"> </a></span><span class="sxs-lookup"><span data-stu-id="ecc3e-164"></span></span>

<span data-ttu-id="ecc3e-p107">Con SharePoint locale che non utilizzano una rete WAN, è possibile utilizzare una connessione ad alta velocità tra Data Center e gli utenti finali. In generale, aspetti sono facile da gestire da un punto di vista di rete.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-p107">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users. Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="ecc3e-167">Con SharePoint Online, esistono alcuni ulteriori fattori da considerare; ad esempio:</span><span class="sxs-lookup"><span data-stu-id="ecc3e-167">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="ecc3e-168">La rete Microsoft</span><span class="sxs-lookup"><span data-stu-id="ecc3e-168">The Microsoft network</span></span>
    
- <span data-ttu-id="ecc3e-169">Internet</span><span class="sxs-lookup"><span data-stu-id="ecc3e-169">The Internet</span></span>
    
- <span data-ttu-id="ecc3e-170">Il provider di servizi Internet</span><span class="sxs-lookup"><span data-stu-id="ecc3e-170">The ISP</span></span>
    
<span data-ttu-id="ecc3e-171">Indipendentemente dalla versione di SharePoint (e di rete) utilizzata, le operazioni che in genere rendono la rete occupata sono:</span><span class="sxs-lookup"><span data-stu-id="ecc3e-171">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="ecc3e-172">Payload di grandi dimensioni</span><span class="sxs-lookup"><span data-stu-id="ecc3e-172">Large payload</span></span>
    
- <span data-ttu-id="ecc3e-173">Numero elevato di file</span><span class="sxs-lookup"><span data-stu-id="ecc3e-173">Many files</span></span>
    
- <span data-ttu-id="ecc3e-174">Grande distanza fisica con il server</span><span class="sxs-lookup"><span data-stu-id="ecc3e-174">Large physical distance to the server</span></span>
    
<span data-ttu-id="ecc3e-p108">Una funzionalità che è possibile utilizzare in SharePoint Online è Microsoft CDN (rete CDN). Una rete CDN è fondamentalmente una raccolta distribuita dei server distribuiti tra più centri dati. Con una rete CDN, il contenuto delle pagine può essere ospitato in un server all'incirca il client anche se il client è lontana dal Server di origine SharePoint. Microsoft utilizzerà questo più in futuro per archiviare le istanze locali di pagine che non possono essere personalizzate, ad esempio SharePoint Online admin home page. Per ulteriori informazioni su CDN, vedere [reti di distribuzione del contenuto](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).</span><span class="sxs-lookup"><span data-stu-id="ecc3e-p108">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network). A CDN is basically a distributed collection of servers deployed across multiple datacenters. With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server. Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page. For more information about CDNs, see [Content delivery networks](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).</span></span>
  
<span data-ttu-id="ecc3e-p109">Un elemento che è necessario tenere presente ma sul quale potrebbe non essere possibile agire, è la velocità della connessione del provider di servizi Internet. Uno strumento di test di velocità semplice indica la velocità della connessione.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-p109">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP. A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="ecc3e-182">Connessione del browser</span><span class="sxs-lookup"><span data-stu-id="ecc3e-182">Browser connection</span></span>
<span data-ttu-id="ecc3e-183"><a name="browser"> </a></span><span class="sxs-lookup"><span data-stu-id="ecc3e-183"></span></span>

<span data-ttu-id="ecc3e-184">Esistono alcuni fattori da considerare con il browser Web dal punto di vista delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-184">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="ecc3e-p110">Visitare pagine complesse inciderà sulle prestazioni. La maggior parte dei browser hanno a disposizione una cache di piccole dimensioni (circa 90MB), mentre la media pagina web viene in genere circa 1.6 MB. Non richiedere tempo che deve ottenere esaurite.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-p110">Visiting complex pages will affect performance. Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB. This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="ecc3e-p111">Larghezza di banda può essere anche un problema. Ad esempio, se un utente è la riproduzione di video in un'altra sessione, si inciderà sulle prestazioni della pagina di SharePoint. Quando si non possono impedire agli utenti di flussi multimediali, è possibile controllare il modo in cui che carica una pagina per gli utenti.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-p111">Bandwidth may also be an issue. For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page. While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="ecc3e-191">Vedere gli articoli seguenti per diverse tecniche di personalizzazione di pagina SharePoint Online e altre procedure consigliate per ottenere prestazioni ottimali.</span><span class="sxs-lookup"><span data-stu-id="ecc3e-191">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="ecc3e-192">Opzioni di spostamento per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ecc3e-192">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="ecc3e-193">Utilizzare lo strumento di diagnostica di pagina per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ecc3e-193">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="ecc3e-194">Ottimizzazione delle immagini per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ecc3e-194">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="ecc3e-195">Ritardo caricamento immagini e JavaScript in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ecc3e-195">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="ecc3e-196">Minimizzazione e creazione di bundle in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ecc3e-196">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="ecc3e-197">Utilizzo delle reti di distribuzione del contenuto</span><span class="sxs-lookup"><span data-stu-id="ecc3e-197">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="ecc3e-198">Utilizzo di Web Part ricerca contenuto invece di Web Part Query contenuto per migliorare le prestazioni di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ecc3e-198">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="ecc3e-199">Capacità di pianificazione test di carico e SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ecc3e-199">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="ecc3e-200">Diagnosi dei problemi delle prestazioni con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ecc3e-200">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="ecc3e-201">Utilizzo della cache oggetti con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ecc3e-201">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="ecc3e-202">Procedura: Evitare la limitazione o il blocco in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ecc3e-202">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

