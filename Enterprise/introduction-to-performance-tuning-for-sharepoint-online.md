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
ms.openlocfilehash: 07938770d711477126f78fc583e8d2533ba5c1d1
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219876"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="067b3-103">Introduzione all'ottimizzazione delle prestazioni per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="067b3-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="067b3-104">In questo articolo viene illustrato quali aspetti specifici, è necessario prendere in considerazione durante la progettazione di pagine per ottimizzare le prestazioni di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="067b3-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
     
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="067b3-105">Metriche di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="067b3-105">SharePoint Online metrics</span></span>

<span data-ttu-id="067b3-106">Le seguenti metriche generali per SharePoint Online forniscono dati reali sulle prestazioni:</span><span class="sxs-lookup"><span data-stu-id="067b3-106">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="067b3-107">Velocità di caricamento delle pagine</span><span class="sxs-lookup"><span data-stu-id="067b3-107">How fast pages load</span></span>
    
- <span data-ttu-id="067b3-108">Numero di round trip necessari per ogni pagina</span><span class="sxs-lookup"><span data-stu-id="067b3-108">How many round trips required per page</span></span>
    
- <span data-ttu-id="067b3-109">Problemi con il servizio</span><span class="sxs-lookup"><span data-stu-id="067b3-109">Issues with the service</span></span>
    
- <span data-ttu-id="067b3-110">Altri aspetti che causano la riduzione delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="067b3-110">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="067b3-111">Conclusioni in base ai dati</span><span class="sxs-lookup"><span data-stu-id="067b3-111">Conclusions reached because of the data</span></span>

<span data-ttu-id="067b3-112">I dati dicono:</span><span class="sxs-lookup"><span data-stu-id="067b3-112">The data tells us:</span></span>
  
- <span data-ttu-id="067b3-113">La maggior parte delle pagine garantisce buone prestazioni con SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="067b3-113">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="067b3-114">Le pagine non personalizzate si caricano molto rapidamente.</span><span class="sxs-lookup"><span data-stu-id="067b3-114">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="067b3-115">OneDrive for Business, i siti del team e le pagine di sistema, ad esempio _layouts e così via, si caricano tutti rapidamente.</span><span class="sxs-lookup"><span data-stu-id="067b3-115">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="067b3-116">La pagina più lenta di 1% di SharePoint Online impiega più di 5.000 millisecondi per caricarsi.</span><span class="sxs-lookup"><span data-stu-id="067b3-116">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="067b3-p101">È possibile utilizzare un semplice test di benchmark per misurare le prestazioni confrontando il tempo di caricamento del proprio portale con il tempo di caricamento della home page di OneDrive for Business, perché utilizza alcune funzionalità personalizzate. Questo spesso sarà il primo passaggio che il supporto chiederà di completare durante la risoluzione dei problemi relativi alle prestazioni di rete.</span><span class="sxs-lookup"><span data-stu-id="067b3-p101">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features. This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="067b3-119">Utilizzare un account utente standard per il controllo delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="067b3-119">Use a standard user account when checking performance</span></span>

<span data-ttu-id="067b3-120">Un amministratore della raccolta siti, proprietario del sito, Editor o collaboratore appartengono a gruppi di sicurezza aggiuntive, disporre di autorizzazioni aggiuntive e pertanto sono elementi aggiuntivi che SharePoint viene caricato in una pagina.</span><span class="sxs-lookup"><span data-stu-id="067b3-120">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="067b3-121">Questa opzione è disponibile per SharePoint Online e SharePoint locale, ma in uno scenario in locale differenze saranno la stessa facilità inosservate come SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="067b3-121">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="067b3-122">Per valutare correttamente come una pagina verrà eseguite per gli utenti, è consigliabile utilizzare un account utente standard per evitare di caricare la creazione di controlli e un aumento del traffico relative ai gruppi di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="067b3-122">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="067b3-123">Categorie di connessione per l'ottimizzazione delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="067b3-123">Connection categories for performance tuning</span></span>

<span data-ttu-id="067b3-p102">È possibile classificare le connessioni tra il server e l'utente in tre componenti principali. Prendere in considerazione tali componenti durante la progettazione delle pagine di SharePoint Online per comprendere i tempi di caricamento.</span><span class="sxs-lookup"><span data-stu-id="067b3-p102">You can categorize the connections between the server and the user into three main components. Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="067b3-126">**Server** I server che ospita Microsoft nei Data Center.</span><span class="sxs-lookup"><span data-stu-id="067b3-126">**Server** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="067b3-127">**Rete** Microsoft network, Internet e la rete locale tra i Data Center e gli utenti.</span><span class="sxs-lookup"><span data-stu-id="067b3-127">**Network** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="067b3-128">**Browser** Dove viene caricata la pagina.</span><span class="sxs-lookup"><span data-stu-id="067b3-128">**Browser** Where the page is loaded.</span></span>
    
<span data-ttu-id="067b3-p103">All'interno di queste tre connessioni in genere esistono cinque motivi che causano il 95% delle pagine lente. Ciascuna di queste situazioni è illustrata in questo articolo:</span><span class="sxs-lookup"><span data-stu-id="067b3-p103">Within these three connections there are typically five reasons that cause 95% of slow pages. Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="067b3-131">Problemi di navigazione</span><span class="sxs-lookup"><span data-stu-id="067b3-131">Navigation issues</span></span>
    
- <span data-ttu-id="067b3-132">Rollup contenuto</span><span class="sxs-lookup"><span data-stu-id="067b3-132">Content roll up</span></span>
    
- <span data-ttu-id="067b3-133">File di grandi dimensioni</span><span class="sxs-lookup"><span data-stu-id="067b3-133">Large files</span></span>
    
- <span data-ttu-id="067b3-134">Numero elevato di richieste al server</span><span class="sxs-lookup"><span data-stu-id="067b3-134">Many requests to the server</span></span>
    
- <span data-ttu-id="067b3-135">Elaborazione di Web Part</span><span class="sxs-lookup"><span data-stu-id="067b3-135">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="067b3-136">Connessione al server</span><span class="sxs-lookup"><span data-stu-id="067b3-136">Server connection</span></span>

<span data-ttu-id="067b3-137">Molti dei problemi che influiscono sulle prestazioni di SharePoint locale valgono anche per SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="067b3-137">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="067b3-p104">Come previsto, è necessario prestare maggiore controllo sul funzionamento dei server con SharePoint locale. Con SharePoint Online le cose sono leggermente diverse. Più lavoro si fa fare al server, maggiore sarà il tempo necessario per il rendering di una pagina. Con SharePoint, la causa principale a questo proposito sono le pagine complesse con più web part.</span><span class="sxs-lookup"><span data-stu-id="067b3-p104">As you would expect, you have far more control over how servers perform with on-premises SharePoint. With SharePoint Online things are a little different. The more work you make a server do, the longer it takes to render a page. With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="067b3-142">SharePoint Server in locale</span><span class="sxs-lookup"><span data-stu-id="067b3-142">SharePoint Server on-premises</span></span>
  
![Schermata del server in locale](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="067b3-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="067b3-144">SharePoint Online</span></span>
  
![Schermata del server online](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="067b3-p105">Con SharePoint Online, alcune richieste di pagine potrebbero effettivamente finire per chiamare più server. Si potrebbe finire con una matrice di richieste tra i server per una singola richiesta. Tali interazioni sono costose da una prospettiva di caricamento della pagina e rendono le operazioni lente.</span><span class="sxs-lookup"><span data-stu-id="067b3-p105">With SharePoint Online, certain page requests may actually end up calling multiple servers. You could end up with a matrix of requests between servers for an individual request. These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="067b3-149">Esempi di tali interazioni da server a server sono:</span><span class="sxs-lookup"><span data-stu-id="067b3-149">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="067b3-150">Da Web a SQL Server</span><span class="sxs-lookup"><span data-stu-id="067b3-150">Web to SQL Servers</span></span>
    
- <span data-ttu-id="067b3-151">Da Web ai server applicazioni</span><span class="sxs-lookup"><span data-stu-id="067b3-151">Web to application servers</span></span>
    
<span data-ttu-id="067b3-p106">L'altra operazione che può rallentare le interazioni del server è la mancanza della cache. A differenza di SharePoint locale, esiste una possibilità molto piccola di raggiungere lo stesso server di una pagina visitata in precedenza. Ciò rende la memorizzazione degli oggetti nella cache obsoleta.</span><span class="sxs-lookup"><span data-stu-id="067b3-p106">The other thing that can slow down server interactions is cache misses. Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="067b3-154">Connessione di rete</span><span class="sxs-lookup"><span data-stu-id="067b3-154">Network connection</span></span>

<span data-ttu-id="067b3-p107">Con SharePoint locale che non utilizzano una rete WAN, è possibile utilizzare una connessione ad alta velocità tra Data Center e gli utenti finali. In generale, aspetti sono facile da gestire da un punto di vista di rete.</span><span class="sxs-lookup"><span data-stu-id="067b3-p107">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users. Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="067b3-157">Con SharePoint Online, esistono alcuni ulteriori fattori da considerare; ad esempio:</span><span class="sxs-lookup"><span data-stu-id="067b3-157">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="067b3-158">La rete Microsoft</span><span class="sxs-lookup"><span data-stu-id="067b3-158">The Microsoft network</span></span>
    
- <span data-ttu-id="067b3-159">Internet</span><span class="sxs-lookup"><span data-stu-id="067b3-159">The Internet</span></span>
    
- <span data-ttu-id="067b3-160">Il provider di servizi Internet</span><span class="sxs-lookup"><span data-stu-id="067b3-160">The ISP</span></span>
    
<span data-ttu-id="067b3-161">Indipendentemente dalla versione di SharePoint (e di rete) utilizzata, le operazioni che in genere rendono la rete occupata sono:</span><span class="sxs-lookup"><span data-stu-id="067b3-161">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="067b3-162">Payload di grandi dimensioni</span><span class="sxs-lookup"><span data-stu-id="067b3-162">Large payload</span></span>
    
- <span data-ttu-id="067b3-163">Numero elevato di file</span><span class="sxs-lookup"><span data-stu-id="067b3-163">Many files</span></span>
    
- <span data-ttu-id="067b3-164">Grande distanza fisica con il server</span><span class="sxs-lookup"><span data-stu-id="067b3-164">Large physical distance to the server</span></span>
    
<span data-ttu-id="067b3-p108">Una funzionalità che è possibile utilizzare in SharePoint Online è Microsoft CDN (rete CDN). Una rete CDN è fondamentalmente una raccolta distribuita dei server distribuiti tra più centri dati. Con una rete CDN, il contenuto delle pagine può essere ospitato in un server all'incirca il client anche se il client è lontana dal Server di origine SharePoint. Microsoft utilizzerà questo più in futuro per archiviare le istanze locali di pagine che non possono essere personalizzate, ad esempio SharePoint Online admin home page. Per ulteriori informazioni su CDN, vedere [reti di distribuzione del contenuto](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).</span><span class="sxs-lookup"><span data-stu-id="067b3-p108">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network). A CDN is basically a distributed collection of servers deployed across multiple datacenters. With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server. Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page. For more information about CDNs, see [Content delivery networks](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).</span></span>
  
<span data-ttu-id="067b3-p109">Un elemento che è necessario tenere presente ma sul quale potrebbe non essere possibile agire, è la velocità della connessione del provider di servizi Internet. Uno strumento di test di velocità semplice indica la velocità della connessione.</span><span class="sxs-lookup"><span data-stu-id="067b3-p109">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP. A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="067b3-172">Connessione del browser</span><span class="sxs-lookup"><span data-stu-id="067b3-172">Browser connection</span></span>

<span data-ttu-id="067b3-173">Esistono alcuni fattori da considerare con il browser Web dal punto di vista delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="067b3-173">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="067b3-p110">Visitare pagine complesse inciderà sulle prestazioni. La maggior parte dei browser hanno a disposizione una cache di piccole dimensioni (circa 90MB), mentre la media pagina web viene in genere circa 1.6 MB. Non richiedere tempo che deve ottenere esaurite.</span><span class="sxs-lookup"><span data-stu-id="067b3-p110">Visiting complex pages will affect performance. Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB. This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="067b3-p111">Larghezza di banda può essere anche un problema. Ad esempio, se un utente è la riproduzione di video in un'altra sessione, si inciderà sulle prestazioni della pagina di SharePoint. Quando si non possono impedire agli utenti di flussi multimediali, è possibile controllare il modo in cui che carica una pagina per gli utenti.</span><span class="sxs-lookup"><span data-stu-id="067b3-p111">Bandwidth may also be an issue. For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page. While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="067b3-180">Vedere gli articoli seguenti per diverse tecniche di personalizzazione di pagina SharePoint Online e altre procedure consigliate per ottenere prestazioni ottimali.</span><span class="sxs-lookup"><span data-stu-id="067b3-180">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="067b3-181">Opzioni di spostamento per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="067b3-181">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="067b3-182">Utilizzare lo strumento di diagnostica di pagina per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="067b3-182">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="067b3-183">Ottimizzazione delle immagini per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="067b3-183">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="067b3-184">Ritardo caricamento immagini e JavaScript in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="067b3-184">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="067b3-185">Minimizzazione e creazione di bundle in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="067b3-185">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="067b3-186">Utilizzo delle reti di distribuzione del contenuto</span><span class="sxs-lookup"><span data-stu-id="067b3-186">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="067b3-187">Utilizzo di Web Part ricerca contenuto invece di Web Part Query contenuto per migliorare le prestazioni di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="067b3-187">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="067b3-188">Capacità di pianificazione test di carico e SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="067b3-188">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="067b3-189">Diagnosi dei problemi delle prestazioni con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="067b3-189">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="067b3-190">Utilizzo della cache oggetti con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="067b3-190">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="067b3-191">Procedura: Evitare la limitazione o il blocco in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="067b3-191">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

