---
title: Opzioni di spostamento per SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: In questo articolo vengono descritti i siti delle opzioni di spostamento con la pubblicazione di SharePoint abilitata in SharePoint Online. La scelta e la configurazione della struttura di spostamento incidono in modo significativo sulle prestazioni e sulla scalabilità dei siti in SharePoint Online. Questo articolo non è applicabile ai siti del team classici.
ms.openlocfilehash: 10b4e1cbad4fbb570affe43feb6773aa59c5f2f3
ms.sourcegitcommit: 77a25920511c54d7d613f552bdff7ad14cdd8324
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2019
ms.locfileid: "36385204"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="45b57-105">Opzioni di spostamento per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="45b57-105">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="45b57-106">In questo articolo vengono descritti i siti delle opzioni di spostamento con la pubblicazione di SharePoint abilitata in SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="45b57-106">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online.</span></span> <span data-ttu-id="45b57-107">La scelta e la configurazione della struttura di spostamento incidono in modo significativo sulle prestazioni e sulla scalabilità dei siti in SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="45b57-107">The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span>

## <a name="overview"></a><span data-ttu-id="45b57-108">Panoramica</span><span class="sxs-lookup"><span data-stu-id="45b57-108">Overview</span></span>

<span data-ttu-id="45b57-109">La configurazione del provider di spostamento può influire in modo significativo sulle prestazioni per l'intero sito e è necessario prendere in considerazione attentamente la scelta di un provider di spostamento e una configurazione in grado di ridimensionare efficacemente i requisiti di un sito di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="45b57-109">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site.</span></span> <span data-ttu-id="45b57-110">Sono disponibili due provider di spostamento fuori dalla casella, nonché implementazioni di spostamento personalizzate.</span><span class="sxs-lookup"><span data-stu-id="45b57-110">There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="45b57-111">La prima opzione, lo [**spostamento gestito (metadati)**](#using-managed-navigation-and-metadata-in-sharepoint-online)è consigliata ed è una delle opzioni predefinite in SharePoint Online. Tuttavia, si consiglia di disabilitare la limitazione di sicurezza a meno che non sia necessario.</span><span class="sxs-lookup"><span data-stu-id="45b57-111">The first option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), is recommended, and is one of the default options in SharePoint Online; however, we recommend that security trimming be disabled unless required.</span></span> <span data-ttu-id="45b57-112">La limitazione di sicurezza è abilitata come impostazione di protezione per il provider di spostamento. Tuttavia, molti siti non richiedono il sovraccarico della limitazione di sicurezza poiché gli elementi di spostamento spesso sono coerenti per tutti gli utenti del sito.</span><span class="sxs-lookup"><span data-stu-id="45b57-112">Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site.</span></span> <span data-ttu-id="45b57-113">Con la configurazione consigliata per disabilitare la limitazione di sicurezza, questo provider di spostamento non richiede l'enumerazione della struttura del sito ed è altamente scalabile con un impatto sulle prestazioni accettabile.</span><span class="sxs-lookup"><span data-stu-id="45b57-113">With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="45b57-114">La seconda opzione, ovvero [**struttura di spostamento strutturale**](#using-structural-navigation-in-sharepoint-online), **non è un'opzione di spostamento consigliata in SharePoint Online**.</span><span class="sxs-lookup"><span data-stu-id="45b57-114">The second option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), **is NOT a recommended navigation option in SharePoint Online**.</span></span> <span data-ttu-id="45b57-115">Questo provider di spostamento è stato creato per una topologia locale con supporto limitato in SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="45b57-115">This navigation provider was designed for an on-premises topology has limited support in SharePoint Online.</span></span> <span data-ttu-id="45b57-116">Anche se fornisce alcuni set di funzionalità aggiuntivi rispetto ad altre opzioni di spostamento, queste funzionalità, tra cui la limitazione della sicurezza e l'enumerazione della struttura del sito, sono a costo di eccessive chiamate ai server e incidono sulla scalabilità e sulle prestazioni quando vengono utilizzate.</span><span class="sxs-lookup"><span data-stu-id="45b57-116">While it provides some additional set of capabilities versus other navigation options, these features, including security trimming and site structure enumeration, comes at a cost of excessive server calls and impacts scalability and performance when it is used.</span></span> <span data-ttu-id="45b57-117">I siti che utilizzano l'esplorazione strutturata che consumano risorse eccessive possono essere soggetti a limitazione.</span><span class="sxs-lookup"><span data-stu-id="45b57-117">Sites using structured navigation that consume excessive resources may be subject to throttling.</span></span>

<span data-ttu-id="45b57-118">Oltre ai provider di spostamento fuori campo, molti clienti hanno implementato con successo implementazioni di spostamento personalizzate alternative.</span><span class="sxs-lookup"><span data-stu-id="45b57-118">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations.</span></span> <span data-ttu-id="45b57-119">Una classe comune di implementazioni di spostamento personalizzate abbraccia modelli di progettazione con rendering client che archiviano una cache locale dei nodi di spostamento.</span><span class="sxs-lookup"><span data-stu-id="45b57-119">One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes.</span></span> <span data-ttu-id="45b57-120">Per ulteriori informazioni, vedere **[script sul fianco client](#using-search-driven-client-side-scripting)** basato sulla ricerca in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="45b57-120">(See **[Search-driven client-side scripting](#using-search-driven-client-side-scripting)** in this article.)</span></span>

<span data-ttu-id="45b57-121">Questi provider di spostamento hanno un paio di vantaggi principali:</span><span class="sxs-lookup"><span data-stu-id="45b57-121">These navigation providers have a couple of key advantages:</span></span> 
- <span data-ttu-id="45b57-122">In genere funzionano bene con i progetti di pagina reattivi.</span><span class="sxs-lookup"><span data-stu-id="45b57-122">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="45b57-123">Sono estremamente scalabili e performanti perché è possibile eseguire il rendering senza costi di risorse (e aggiornare in background dopo un timeout).</span><span class="sxs-lookup"><span data-stu-id="45b57-123">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span> 
- <span data-ttu-id="45b57-124">Tali provider di spostamento possono recuperare i dati di spostamento utilizzando diverse strategie, che vanno dalle configurazioni statiche semplici ai vari provider di dati dinamici.</span><span class="sxs-lookup"><span data-stu-id="45b57-124">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span> 

<span data-ttu-id="45b57-125">Un esempio di provider di dati prevede l'utilizzo di una struttura di **spostamento basata sulla ricerca**, che consente la flessibilità per l'enumerazione dei nodi di spostamento e la gestione efficiente del taglio di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="45b57-125">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span> 

<span data-ttu-id="45b57-126">Sono disponibili altre opzioni popolari per la creazione di **provider di spostamento personalizzati**.</span><span class="sxs-lookup"><span data-stu-id="45b57-126">There are other popular options to build **Custom navigation providers**.</span></span> <span data-ttu-id="45b57-127">Leggere le [soluzioni di navigazione per i portali di SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) per ulteriori informazioni sulla creazione di un provider di spostamento personalizzato.</span><span class="sxs-lookup"><span data-stu-id="45b57-127">Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="45b57-128">Vantaggi e svantaggi delle opzioni di spostamento di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="45b57-128">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="45b57-129">Nella tabella seguente sono riepilogati i vantaggi e gli svantaggi di ogni opzione.</span><span class="sxs-lookup"><span data-stu-id="45b57-129">The following table summarizes the pros and cons of each option.</span></span> 


|<span data-ttu-id="45b57-130">Esplorazione gestita</span><span class="sxs-lookup"><span data-stu-id="45b57-130">Managed navigation</span></span>  |<span data-ttu-id="45b57-131">Esplorazione strutturale</span><span class="sxs-lookup"><span data-stu-id="45b57-131">Structural navigation</span></span>  |<span data-ttu-id="45b57-132">Esplorazione basata sulla ricerca</span><span class="sxs-lookup"><span data-stu-id="45b57-132">Search-driven navigation</span></span>  |<span data-ttu-id="45b57-133">Provider di spostamento personalizzato</span><span class="sxs-lookup"><span data-stu-id="45b57-133">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="45b57-134">Professionisti</span><span class="sxs-lookup"><span data-stu-id="45b57-134">Pros:</span></span><br/><br/><span data-ttu-id="45b57-135">Facile da gestire</span><span class="sxs-lookup"><span data-stu-id="45b57-135">Easy to maintain</span></span><br/><span data-ttu-id="45b57-136">Opzione consigliata</span><span class="sxs-lookup"><span data-stu-id="45b57-136">Recommended option</span></span><br/>     |<span data-ttu-id="45b57-137">Professionisti</span><span class="sxs-lookup"><span data-stu-id="45b57-137">Pros:</span></span><br/><br/><span data-ttu-id="45b57-138">Semplice da configurare</span><span class="sxs-lookup"><span data-stu-id="45b57-138">Easy to configure</span></span><br/><span data-ttu-id="45b57-139">Protezione ritagliata</span><span class="sxs-lookup"><span data-stu-id="45b57-139">Security trimmed</span></span><br/><span data-ttu-id="45b57-140">Viene aggiornato automaticamente con l'aggiunta di contenuto</span><span class="sxs-lookup"><span data-stu-id="45b57-140">Automatically updates as content is added</span></span><br/>|<span data-ttu-id="45b57-141">Professionisti</span><span class="sxs-lookup"><span data-stu-id="45b57-141">Pros:</span></span><br/><br/><span data-ttu-id="45b57-142">Protezione ritagliata</span><span class="sxs-lookup"><span data-stu-id="45b57-142">Security trimmed</span></span><br/><span data-ttu-id="45b57-143">Si aggiorna automaticamente man mano che i siti vengono aggiunti</span><span class="sxs-lookup"><span data-stu-id="45b57-143">Automatically updates as sites are added</span></span><br/><span data-ttu-id="45b57-144">Tempo di caricamento rapido e struttura dell'esplorazione memorizzata nella cache</span><span class="sxs-lookup"><span data-stu-id="45b57-144">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="45b57-145">Professionisti</span><span class="sxs-lookup"><span data-stu-id="45b57-145">Pros:</span></span><br/><br/><span data-ttu-id="45b57-146">Scelta più ampia di opzioni disponibili</span><span class="sxs-lookup"><span data-stu-id="45b57-146">Wider choice of options available</span></span><br/><span data-ttu-id="45b57-147">Caricamento veloce quando la memorizzazione nella cache viene utilizzata correttamente</span><span class="sxs-lookup"><span data-stu-id="45b57-147">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="45b57-148">Molte opzioni funzionano bene con la progettazione delle pagine reattive</span><span class="sxs-lookup"><span data-stu-id="45b57-148">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="45b57-149">Contro</span><span class="sxs-lookup"><span data-stu-id="45b57-149">Cons:</span></span><br/><br/><span data-ttu-id="45b57-150">Non si aggiorna automaticamente per riflettere la struttura del sito</span><span class="sxs-lookup"><span data-stu-id="45b57-150">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="45b57-151">Impatto delle prestazioni se la limitazione di sicurezza è abilitata</span><span class="sxs-lookup"><span data-stu-id="45b57-151">Impacts performance if security trimming is enabled</span></span><br/>|<span data-ttu-id="45b57-152">Contro</span><span class="sxs-lookup"><span data-stu-id="45b57-152">Cons:</span></span><br/><br/><span data-ttu-id="45b57-153">**Non consigliato**</span><span class="sxs-lookup"><span data-stu-id="45b57-153">**Not recommended**</span></span><br/><span data-ttu-id="45b57-154">**Impatto sulle prestazioni e sulla scalabilità**</span><span class="sxs-lookup"><span data-stu-id="45b57-154">**Impacts performance and scalability**</span></span><br/><span data-ttu-id="45b57-155">**Soggette a limitazione**</span><span class="sxs-lookup"><span data-stu-id="45b57-155">**Subject to throttling**</span></span><br/>|<span data-ttu-id="45b57-156">Contro</span><span class="sxs-lookup"><span data-stu-id="45b57-156">Cons:</span></span><br/><br/><span data-ttu-id="45b57-157">Non è possibile ordinare facilmente i siti</span><span class="sxs-lookup"><span data-stu-id="45b57-157">No ability to easily order sites</span></span><br/><span data-ttu-id="45b57-158">Richiede la personalizzazione della pagina master (necessarie competenze tecniche)</span><span class="sxs-lookup"><span data-stu-id="45b57-158">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="45b57-159">Contro</span><span class="sxs-lookup"><span data-stu-id="45b57-159">Cons:</span></span><br/><br/><span data-ttu-id="45b57-160">Lo sviluppo personalizzato è obbligatorio</span><span class="sxs-lookup"><span data-stu-id="45b57-160">Custom development is required</span></span><br/><span data-ttu-id="45b57-161">L'origine dati esterna/cache memorizzata è necessaria ad esempio Azure</span><span class="sxs-lookup"><span data-stu-id="45b57-161">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="45b57-162">L'opzione più appropriata per il sito dipende dai requisiti del sito e dalle proprie capacità tecniche.</span><span class="sxs-lookup"><span data-stu-id="45b57-162">The most appropriate option for your site will depend on your site requirements and on your technical capability.</span></span> <span data-ttu-id="45b57-163">Se si desidera un provider di navigazione esterno scalabile, quindi l'esplorazione gestita con la limitazione della sicurezza disabilitata è un'ottima opzione.</span><span class="sxs-lookup"><span data-stu-id="45b57-163">If you want a scalable out-of-the-box navigation provider, then Managed navigation with security trimming disabled is a very good option.</span></span>

<span data-ttu-id="45b57-164">L'opzione di spostamento gestito può essere mantenuta tramite la configurazione, non comporta file di personalizzazione del codice ed è significativamente più veloce rispetto alla struttura di spostamento strutturale.</span><span class="sxs-lookup"><span data-stu-id="45b57-164">The Managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than structural navigation.</span></span> <span data-ttu-id="45b57-165">Se si richiede la riduzione della sicurezza e si ha dimestichezza con una pagina master personalizzata e si dispone di una certa funzionalità nell'organizzazione per gestire le modifiche che possono verificarsi nella pagina master predefinita per SharePoint Online, l'opzione basata sulla ricerca potrebbe produrre una migliore esperienza utente.</span><span class="sxs-lookup"><span data-stu-id="45b57-165">If you require security trimming and are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the Search-driven option may produce a better user experience.</span></span> <span data-ttu-id="45b57-166">Se si dispone di requisiti più complessi, è possibile che il provider di spostamento personalizzato sia la scelta giusta.</span><span class="sxs-lookup"><span data-stu-id="45b57-166">If you have more complex requirements, then a custom navigation provider may be the right choice.</span></span> <span data-ttu-id="45b57-167">La struttura di spostamento strutturale non è consigliata.</span><span class="sxs-lookup"><span data-stu-id="45b57-167">Structural navigation is NOT recommended.</span></span>

<span data-ttu-id="45b57-168">Infine, è importante tenere presente che SharePoint aggiunge ulteriori provider di spostamento e funzionalità per le moderne architetture di siti di SharePoint, sfruttando una gerarchia di siti più appiattita e un modello hub-and-spoke con i siti hub di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="45b57-168">Finally, it’s important to note that SharePoint is adding additional navigation providers and functionality for modern SharePoint site architectures leveraging a more flattened site hierarchy and a hub-and-spoke model with SharePoint hub sites.</span></span> <span data-ttu-id="45b57-169">In questo modo è possibile ottenere numerosi scenari che non richiedono l'utilizzo della caratteristica di pubblicazione di SharePoint e queste configurazioni di spostamento sono ottimizzate per la scalabilità e la latenza all'interno di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="45b57-169">This allows many scenarios to be achieved that do NOT require the use of SharePoint Publishing feature, and these navigation configurations are optimized for scalability and latency within SharePoint Online.</span></span> <span data-ttu-id="45b57-170">Si noti che l'applicazione dello stesso principio: semplificare la struttura complessiva del sito di pubblicazione di SharePoint in una struttura più piatta, spesso contribuisce anche alle prestazioni generali e alla scalabilità.</span><span class="sxs-lookup"><span data-stu-id="45b57-170">Note that applying the same principle - simplifying the overall structure of your SharePoint Publishing site to a flatter structure, often helps with overall performance and scale as well.</span></span> <span data-ttu-id="45b57-171">Ciò significa che, invece di disporre di una singola raccolta siti con centinaia di Site (Web secondari), un approccio migliore consiste nell'avere molte raccolte siti con pochissimi sottositi (Web secondari).</span><span class="sxs-lookup"><span data-stu-id="45b57-171">What this means is that instead of having a single Site Collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="45b57-172">Utilizzo dell'esplorazione e dei metadati gestiti in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="45b57-172">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="45b57-173">L'esplorazione gestita è un'altra opzione che è possibile utilizzare per ricreare la maggior parte delle stesse funzionalità della struttura di spostamento strutturale.</span><span class="sxs-lookup"><span data-stu-id="45b57-173">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation.</span></span> <span data-ttu-id="45b57-174">I metadati gestiti possono essere configurati in modo da abilitare o disabilitare la limitazione di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="45b57-174">Managed metadata can be configured to have security trimming enabled or disabled.</span></span> <span data-ttu-id="45b57-175">Una volta configurata con la limitazione della sicurezza disabilitata, l'esplorazione gestita è piuttosto efficiente poiché carica tutti i collegamenti di spostamento con un numero costante di chiamate del server.</span><span class="sxs-lookup"><span data-stu-id="45b57-175">When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls.</span></span> <span data-ttu-id="45b57-176">L'abilitazione della limitazione della sicurezza, tuttavia, nega alcuni dei vantaggi dell'esplorazione gestita e i clienti possono scegliere di esplorare una delle soluzioni di spostamento personalizzate per ottimizzare le prestazioni e la scalabilità.</span><span class="sxs-lookup"><span data-stu-id="45b57-176">Enabling security trimming, however, negates some of the advantages of managed navigation, and customers may choose to explore one of the custom navigation solutions for optimal performance and scalability.</span></span>

<span data-ttu-id="45b57-177">Molti siti non richiedono la limitazione della sicurezza, in quanto la struttura di spostamento è spesso coerente per tutti gli utenti del sito.</span><span class="sxs-lookup"><span data-stu-id="45b57-177">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site.</span></span> <span data-ttu-id="45b57-178">Se la limitazione di sicurezza è disabilitata e viene aggiunto un collegamento alla struttura di spostamento a cui non è consentito l'accesso a tutti gli utenti, il collegamento verrà comunque visualizzato, ma comporterà un messaggio di accesso negato.</span><span class="sxs-lookup"><span data-stu-id="45b57-178">If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message.</span></span> <span data-ttu-id="45b57-179">Non vi è alcun rischio di accesso involontario al contenuto.</span><span class="sxs-lookup"><span data-stu-id="45b57-179">There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="45b57-180">Come implementare l'esplorazione gestita e i risultati</span><span class="sxs-lookup"><span data-stu-id="45b57-180">How to implement managed navigation and the results</span></span>

<span data-ttu-id="45b57-181">Sono disponibili numerosi articoli su Docs.Microsoft.com per informazioni dettagliate sull'esplorazione gestita, ad esempio, vedere [Overview of Managed Navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span><span class="sxs-lookup"><span data-stu-id="45b57-181">There are several articles on Docs.Microsoft.com about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="45b57-182">Per implementare l'esplorazione gestita, è necessario configurare i termini con gli URL corrispondenti alla struttura di spostamento del sito.</span><span class="sxs-lookup"><span data-stu-id="45b57-182">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of  the site.</span></span> <span data-ttu-id="45b57-183">L'esplorazione gestita può anche essere curata manualmente per sostituire la struttura di spostamento strutturale in molti casi.</span><span class="sxs-lookup"><span data-stu-id="45b57-183">Managed navigation can even be manually curated to replace structural navigation in many cases.</span></span> <span data-ttu-id="45b57-184">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="45b57-184">For example:</span></span>

![Struttura del sito di SharePoint Online](media/SPONavOptionsListOfSites.png)

<span data-ttu-id="45b57-186">L'esempio seguente mostra le prestazioni della struttura di spostamento complessa utilizzando l'esplorazione gestita.</span><span class="sxs-lookup"><span data-stu-id="45b57-186">The following example shows the performance of the complex navigation using managed navigation.</span></span>

![Prestazioni dell'esplorazione complessa tramite l'esplorazione gestita](media/SPONavOptionsComplexNavPerf.png)

<span data-ttu-id="45b57-188">L'utilizzo dell'esplorazione gestita migliora costantemente le prestazioni rispetto all'approccio di spostamento strutturale.</span><span class="sxs-lookup"><span data-stu-id="45b57-188">Using managed navigation consistently improves performance compared to the structural navigation approach.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="45b57-189">Utilizzo dell'esplorazione strutturale in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="45b57-189">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="45b57-190">Questa è la struttura di spostamento fuori campo utilizzata per impostazione predefinita ed è la soluzione più semplice, ma come tale ha un costo elevato di prestazioni.</span><span class="sxs-lookup"><span data-stu-id="45b57-190">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off.</span></span> <span data-ttu-id="45b57-191">Non richiede alcuna personalizzazione e un utente non tecnico può anche aggiungere facilmente elementi, nascondere gli elementi e gestire la struttura di spostamento dalla pagina impostazioni.</span><span class="sxs-lookup"><span data-stu-id="45b57-191">It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page.</span></span> <span data-ttu-id="45b57-192">Questo è tuttavia valido anche per l'esplorazione gestita, pertanto è consigliabile utilizzare l'esplorazione gestita in modo che possa essere anche facilmente gestita e controllata e con prestazioni migliorate.</span><span class="sxs-lookup"><span data-stu-id="45b57-192">This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well with improved performance.</span></span>

![Struttura di spostamento strutturale con i siti secondari visualizzati selezionati](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="45b57-194">Attivazione dell'esplorazione strutturale in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="45b57-194">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="45b57-195">Per illustrare le prestazioni in una soluzione SharePoint Online con esplorazione strutturale e opzione per mostrare i siti secondari attivate.</span><span class="sxs-lookup"><span data-stu-id="45b57-195">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on.</span></span> <span data-ttu-id="45b57-196">Di seguito è riportata una schermata delle impostazioni disponibili nella pagina di **spostamento** **delle impostazioni** \> del sito.</span><span class="sxs-lookup"><span data-stu-id="45b57-196">Below is a screenshot of settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![Schermata che mostra i siti secondari](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="45b57-198">Analisi delle prestazioni dell'esplorazione strutturale in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="45b57-198">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="45b57-199">Per analizzare le prestazioni di una pagina di SharePoint, utilizzare la scheda **rete** degli strumenti di sviluppo F12 in Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="45b57-199">To analyze the performance of a SharePoint page, use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![Schermata che mostra la scheda Rete degli strumenti di sviluppo F12](media/SPONavOptionsNetworks.png)
  
1. <span data-ttu-id="45b57-201">Nella scheda **Rete**, fare clic nella pagina aspx in caricamento, quindi fare clic sulla scheda **Dettagli**.</span><span class="sxs-lookup"><span data-stu-id="45b57-201">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span><br/> <span data-ttu-id="45b57-202">![Schermata che mostra la scheda dei dettagli](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span><span class="sxs-lookup"><span data-stu-id="45b57-202">![Screenshot showing the details tab](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span></span><br/>
2. <span data-ttu-id="45b57-203">Fare clic su **Intestazioni di risposta**.</span><span class="sxs-lookup"><span data-stu-id="45b57-203">Click **Response headers**.</span></span> <br/><span data-ttu-id="45b57-204">![Schermata scheda Dettagli](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span><span class="sxs-lookup"><span data-stu-id="45b57-204">![Screenshot of Details tab](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span></span><br/><span data-ttu-id="45b57-205">SharePoint restituisce alcune informazioni diagnostiche utili nelle intestazioni di risposta.</span><span class="sxs-lookup"><span data-stu-id="45b57-205">SharePoint returns some useful diagnostic information in its response headers.</span></span> 
3. <span data-ttu-id="45b57-206">Una delle informazioni più utili è **SPRequestDuration** , ovvero il valore, in millisecondi, della durata della richiesta di elaborazione sul server.</span><span class="sxs-lookup"><span data-stu-id="45b57-206">One of the most useful pieces of information is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server.</span></span> <span data-ttu-id="45b57-207">Nella schermata seguente l'opzione **Mostra i siti secondari** non è selezionata per l'esplorazione strutturale.</span><span class="sxs-lookup"><span data-stu-id="45b57-207">In the following screenshot **show subsites** is unchecked for the structural navigation.</span></span> <span data-ttu-id="45b57-208">Questo significa che è presente solo il collegamento della raccolta di siti nel riquadro di esplorazione globale:</span><span class="sxs-lookup"><span data-stu-id="45b57-208">This means that there is only the site collection link in the global navigation:</span></span><br/><span data-ttu-id="45b57-209">![Schermata che mostra i tempi di caricamento come durata richiesta](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span><span class="sxs-lookup"><span data-stu-id="45b57-209">![Screenshot showing load times as request duration](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span></span><br/>
4. <span data-ttu-id="45b57-210">La chiave **SPRequestDuration** presenta un valore di 245 millisecondi.</span><span class="sxs-lookup"><span data-stu-id="45b57-210">The **SPRequestDuration** key has a value of 245 milliseconds.</span></span> <span data-ttu-id="45b57-211">Questo valore rappresenta il tempo necessario per restituire la richiesta.</span><span class="sxs-lookup"><span data-stu-id="45b57-211">This represents the time it took to return the request.</span></span> <span data-ttu-id="45b57-212">Poiché esiste un solo elemento di spostamento nel sito, questo è un valido riferimento per il modo in cui si comporta SharePoint Online senza spostamento intenso.</span><span class="sxs-lookup"><span data-stu-id="45b57-212">Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation.</span></span> <span data-ttu-id="45b57-213">Nella schermata successiva viene mostrato il modo in cui l'aggiunta nei siti secondari influisce su questa chiave.</span><span class="sxs-lookup"><span data-stu-id="45b57-213">The next screen shot shows how adding in the subsites affects this key.</span></span><br/><span data-ttu-id="45b57-214">![Schermata che illustra una durata richiesta di 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span><span class="sxs-lookup"><span data-stu-id="45b57-214">![Screenshot showing a request duration of 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span></span><br/>
  
<span data-ttu-id="45b57-215">L'aggiunta dei siti secondari ha aumentato significativamente il tempo necessario per restituire la richiesta di pagina per questo sito di esempio relativamente semplice.</span><span class="sxs-lookup"><span data-stu-id="45b57-215">Adding the subsites has significantly increased the time it takes to return the page request for this relatively simple sample site.</span></span> <span data-ttu-id="45b57-216">Le gerarchie di siti complesse, incluse le pagine in navigazione e altre opzioni di configurazione e topologia, possono aumentare drasticamente ulteriormente questo impatto.</span><span class="sxs-lookup"><span data-stu-id="45b57-216">Complex site hierarchies, including pages in navigation, and other configuration and topology options can dramatically increase this impact even further.</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="45b57-217">Utilizzo di script sul lato client basato sulla ricerca</span><span class="sxs-lookup"><span data-stu-id="45b57-217">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="45b57-218">Utilizzando la ricerca è possibile utilizzare gli indici sviluppati in background tramite la ricerca per indicizzazione continua.</span><span class="sxs-lookup"><span data-stu-id="45b57-218">Using search you can leverage the indexes that are built up in the background using continuous crawl.</span></span> <span data-ttu-id="45b57-219">I risultati della ricerca vengono recuperati dall'indice di ricerca e i risultati sono limitati per motivi di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="45b57-219">The search results are pulled from the search index and the results are security-trimmed.</span></span> <span data-ttu-id="45b57-220">Questo è in genere più veloce rispetto ai provider di spostamento esterno alla casella quando è richiesta la limitazione della sicurezza.</span><span class="sxs-lookup"><span data-stu-id="45b57-220">This is generally faster than out-of-the-box navigation providers when security trimming is required.</span></span> <span data-ttu-id="45b57-221">Utilizzando la ricerca per l'esplorazione strutturale, soprattutto se si dispone di una struttura di siti complessa, è possibile velocizzare notevolmente tempi di caricamento delle pagine.</span><span class="sxs-lookup"><span data-stu-id="45b57-221">Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably.</span></span> <span data-ttu-id="45b57-222">Il principale vantaggio di questa esplorazione gestita è che è possibile beneficiare della limitazione per motivi di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="45b57-222">The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="45b57-223">Questo approccio implica la creazione di una pagina master personalizzata e la sostituzione del codice di spostamento predefinito con codice HTML personalizzato.</span><span class="sxs-lookup"><span data-stu-id="45b57-223">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML.</span></span> <span data-ttu-id="45b57-224">Seguire questa procedura illustrata nell'esempio seguente per sostituire il codice di spostamento nel file `seattle.html`.</span><span class="sxs-lookup"><span data-stu-id="45b57-224">Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`.</span></span> <span data-ttu-id="45b57-225">In questo esempio viene aperto il `seattle.html` file e sostituito l'intero elemento `id=”DeltaTopNavigation”` con codice HTML personalizzato.</span><span class="sxs-lookup"><span data-stu-id="45b57-225">In this example, you will open the `seattle.html` file and replace the whole element `id=”DeltaTopNavigation”` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="45b57-226">Esempio: sostituire il codice di spostamento fuori dalla casella in una pagina master</span><span class="sxs-lookup"><span data-stu-id="45b57-226">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1.  <span data-ttu-id="45b57-227">Andare alla pagina Impostazioni sito.</span><span class="sxs-lookup"><span data-stu-id="45b57-227">Navigate to the Site Settings page.</span></span>
2.  <span data-ttu-id="45b57-228">Aprire la raccolta di pagine master facendo clic su **Pagine master**.</span><span class="sxs-lookup"><span data-stu-id="45b57-228">Open the master page gallery by clicking **Master Pages**.</span></span>
3.  <span data-ttu-id="45b57-229">Da qui è possibile passare alla raccolta e scaricare il file `seattle.master`.</span><span class="sxs-lookup"><span data-stu-id="45b57-229">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4.  <span data-ttu-id="45b57-230">Modificare il codice utilizzando un editor di testo ed eliminare il blocco di codice nella schermata seguente.</span><span class="sxs-lookup"><span data-stu-id="45b57-230">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![Eliminare il blocco di codice visualizzato](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="45b57-232">Rimuovere il codice tra i `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` tag `<\SharePoint:AjaxDelta>` e e sostituirlo con il seguente frammento:</span><span class="sxs-lookup"><span data-stu-id="45b57-232">Remove the code between the `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

```
<div id="loading">
  <!--Replace with path to loading image.-->
  <div style="background-image: url(''); height: 22px; width: 22px; ">
  </div>
</div>
<!-- Main Content-->
<div id="navContainer" style="display:none">
    <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
        </a>
        <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
            <li class="static dynamic-children level1">
                <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
               
                 <!-- ko if: children.length > 0-->
                    <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                <!-- ko if: children.length == 0-->   
                    <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->   
                </a>
               
                <!-- ko if: children.length > 0-->                                                       
                <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                    <li class="dynamic level2">
                        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
         
          <!-- ko if: children.length > 0-->
          <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
           <!-- /ko -->
          <!-- ko if: children.length == 0-->
          <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>                 
          <!-- /ko -->   
                        </a>
          <!-- ko if: children.length > 0-->
         <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
          <li class="dynamic level3">
           <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
           </a>
          </li>
         </ul>
           <!-- /ko -->
                    </li>
                </ul>
                <!-- /ko -->
            </li>
        </ul>
    </div>
</div>
```
<br/>
6. <span data-ttu-id="45b57-233">Sostituire l'URL nel tag Anchor dell'immagine di caricamento all'inizio, con un collegamento a un'immagine di caricamento nella raccolta siti.</span><span class="sxs-lookup"><span data-stu-id="45b57-233">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection.</span></span> <span data-ttu-id="45b57-234">Dopo aver apportato le modifiche, rinominare il file, quindi caricarlo nella raccolta di pagine master.</span><span class="sxs-lookup"><span data-stu-id="45b57-234">After you have made the changes, rename the file and then upload it to the master page gallery.</span></span> <span data-ttu-id="45b57-235">Ciò genera un nuovo file con estensione master.</span><span class="sxs-lookup"><span data-stu-id="45b57-235">This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="45b57-236">Questo codice HTML è il codice di base che verrà precompilato dai risultati della ricerca restituiti dal codice JavaScript.</span><span class="sxs-lookup"><span data-stu-id="45b57-236">This HTML is the basic markup that will be populated by the search results returned from JavaScript code.</span></span> <span data-ttu-id="45b57-237">Sarà necessario modificare il codice per modificare il valore di var root = "URL della raccolta siti", come illustrato nel seguente frammento:</span><span class="sxs-lookup"><span data-stu-id="45b57-237">You will need to edit the code to change the value for var root = “site collection URL” as demonstrated in the following snippet:</span></span><br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. <span data-ttu-id="45b57-238">I risultati vengono assegnati alla matrice self. Nodes e una gerarchia è costituita dagli oggetti tramite LINQ. js che assegnano l'output a una matrice self. Hierarchy.</span><span class="sxs-lookup"><span data-stu-id="45b57-238">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.hierarchy.</span></span> <span data-ttu-id="45b57-239">Questa matrice è l'oggetto in cui è associato il codice HTML.</span><span class="sxs-lookup"><span data-stu-id="45b57-239">This array is the object that is bound to the HTML.</span></span> <span data-ttu-id="45b57-240">Questa operazione viene eseguita nella funzione toggleView() passando l'oggetto utente alla funzione ko.applyBinding().</span><span class="sxs-lookup"><span data-stu-id="45b57-240">This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="45b57-241">Quindi, in questo modo la matrice di gerarchia va associata al codice HTML seguente:</span><span class="sxs-lookup"><span data-stu-id="45b57-241">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

<span data-ttu-id="45b57-242">I gestori eventi per `mouseenter` e `mouseexit` vengono aggiunti all'esplorazione di livello principale per gestire i menu a discesa dei siti secondari, che vengono eseguiti nella `addEventsToElements()` funzione.</span><span class="sxs-lookup"><span data-stu-id="45b57-242">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="45b57-243">Nell'esempio di esplorazione complessa, un caricamento di pagina aggiornato senza la memorizzazione nella cache locale indica che il tempo trascorso nel server è stato ridotto dall'esplorazione strutturale di benchmark per ottenere un risultato simile a quello dell'approccio di spostamento gestito.</span><span class="sxs-lookup"><span data-stu-id="45b57-243">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="45b57-244">Informazioni sul file JavaScript...</span><span class="sxs-lookup"><span data-stu-id="45b57-244">About the JavaScript file...</span></span>

<span data-ttu-id="45b57-245">Di seguito è riportato l'intero file JavaScript:</span><span class="sxs-lookup"><span data-stu-id="45b57-245">The entire JavaScript file is as follows:</span></span>

```
//Models and Namespaces
var SPOCustom = SPOCustom || {};
SPOCustom.Models = SPOCustom.Models || {}
SPOCustom.Models.NavigationNode = function () {

    this.Url = ko.observable("");
    this.Title = ko.observable("");
    this.Parent = ko.observable("");

};

var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
var baseUrl = root + "/_api/search/query?querytext=";
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

var baseRequest = {
    url: "",
    type: ""
};


//Parses a local object from JSON search result.
function getNavigationFromDto(dto) {
    var item = new SPOCustom.Models.NavigationNode();
    if (dto != undefined) {

        var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');

        if (webTemplate != "APP") {
            item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
            item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
            item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
        }

    }
    return item;
}

function getSearchResultsValue(results, key) {

    for (i = 0; i < results.length; i++) {
        if (results[i].Key == key) {
            return results[i].Value;
        }
    }
    return null;
}

//Parse a local object from the serialized cache.
function getNavigationFromCache(dto) {
    var item = new SPOCustom.Models.NavigationNode();

    if (dto != undefined) {

        item.Title(dto.Title);
        item.Url(dto.Url);
        item.Parent(dto.Parent);
    }

    return item;
}

/* create a new OData request for JSON response */
function getRequest(endpoint) {
    var request = baseRequest;
    request.type = "GET";
    request.url = endpoint;
    request.headers = { ACCEPT: "application/json;odata=verbose" };
    return request;
};

/* Navigation Module*/
function NavigationViewModel() {
    "use strict";
    var self = this;
    self.nodes = ko.observableArray([]);
    self.hierarchy = ko.observableArray([]);;
    self.loadNavigatioNodes = function () {
        //Check local storage for cached navigation datasource.
        var fromStorage = localStorage["nodesCache"];
        if (false) {
            var cachedNodes = JSON.parse(localStorage["nodesCache"]);

            if (cachedNodes && timeStamp) {
                //Check for cache expiration. Currently set to 3 hrs.
                var now = new Date();
                var diff = now.getTime() - timeStamp;
                if (Math.round(diff / (1000 * 60 * 60)) < 3) {

                    //return from cache.
                    var cacheResults = [];
                    $.each(cachedNodes, function (i, item) {
                        var nodeitem = getNavigationFromCache(item, true);
                        cacheResults.push(nodeitem);
                    });

                    self.buildHierarchy(cacheResults);
                    self.toggleView();
                    addEventsToElements();
                    return;
                }
            }
        }
        //No cache hit, REST call required.
        self.queryRemoteInterface();
    };

    //Executes a REST call and builds the navigation hierarchy.
    self.queryRemoteInterface = function () {
        var oDataRequest = getRequest(query);
        $.ajax(oDataRequest).done(function (data) {
            var results = [];
            $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {

                if (i == 0) {
                    //Add root element.
                    var rootItem = new SPOCustom.Models.NavigationNode();
                    rootItem.Title("Root");
                    rootItem.Url(root);
                    rootItem.Parent(null);
                    results.push(rootItem);
                }
                var navItem = getNavigationFromDto(item);
                results.push(navItem);
            });
            //Add to local cache
            localStorage["nodesCache"] = ko.toJSON(results);

            localStorage["nodesCachedAt"] = new Date().getTime();
            self.nodes(results);
            if (self.nodes().length > 0) {
                var unsortedArray = self.nodes();
                var sortedArray = unsortedArray.sort(self.sortObjectsInArray);

                self.buildHierarchy(sortedArray);
                self.toggleView();
                addEventsToElements();
            }
        }).fail(function () {
            //Handle error here!!
            $("#loading").hide();
            $("#error").show();
        });
    };
    self.toggleView = function () {
        var navContainer = document.getElementById("navContainer");
        ko.applyBindings(self, navContainer);
        $("#loading").hide();
        $("#navContainer").show();

    };
    //Uses linq.js to build the navigation tree.
    self.buildHierarchy = function (enumerable) {
        self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
            return d.Parent() == null;
        }, function (parent, child) {
            if (parent.Url() == null || child.Parent() == null)
                return false;
            return parent.Url().toUpperCase() == child.Parent().toUpperCase();
        }).ToArray());

        self.sortChildren(self.hierarchy()[0]);
    };


    self.sortChildren = function (parent) {

        // sjip processing if no children
        if (!parent || !parent.children || parent.children.length === 0) {
            return;
        }

        parent.children = parent.children.sort(self.sortObjectsInArray2);

        for (var i = 0; i < parent.children.length; i++) {
            var elem = parent.children[i];

            if (elem.children && elem.children.length > 0) {
                self.sortChildren(elem);
            }
        }
    };

    // ByHierarchy method breaks the sorting in chrome and firefix 
    // we need to resort  as ascending
    self.sortObjectsInArray2 = function (a, b) {
        if (a.item.Title() > b.item.Title())
            return 1;
        if (a.item.Title() < b.item.Title())
            return -1;
        return 0;
    };


    self.sortObjectsInArray = function (a, b) {
        if (a.Title() > b.Title())
            return -1;
        if (a.Title() < b.Title())
            return 1;
        return 0;
    }
}

//Loads the navigation on load and binds the event handlers for mouse interaction.
function InitCustomNav() {
    var viewModel = new NavigationViewModel();
    viewModel.loadNavigatioNodes();
}

function addEventsToElements() {
    //events.
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

``` 

<span data-ttu-id="45b57-246">Per riepilogare il codice sopra riportato nella `jQuery $(document).ready` funzione viene `viewModel object` creata e quindi viene chiamata la `loadNavigationNodes()` funzione su quell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="45b57-246">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called.</span></span> <span data-ttu-id="45b57-247">Questa funzione carica la gerarchia di spostamento precedentemente creata memorizzata nell'archiviazione locale di HTML5 del browser client o chiama la funzione `queryRemoteInterface()`.</span><span class="sxs-lookup"><span data-stu-id="45b57-247">This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="45b57-248">`QueryRemoteInterface()`Compila una richiesta utilizzando la `getRequest()` funzione con il parametro di query definito in precedenza nello script e quindi restituisce i dati dal server.</span><span class="sxs-lookup"><span data-stu-id="45b57-248">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server.</span></span> <span data-ttu-id="45b57-249">Questi dati sono sostanzialmente una matrice di tutti i siti nella raccolta di siti rappresentati come oggetti di trasferimento dei dati con alcune proprietà.</span><span class="sxs-lookup"><span data-stu-id="45b57-249">This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span> 

<span data-ttu-id="45b57-250">Questi dati vengono quindi analizzati negli oggetti definiti `SPO.Models.NavigationNode` in precedenza che utilizzano `Knockout.js` per creare proprietà osservabili per l'utilizzo da parte dei dati per l'associazione dei valori nel codice HTML definito in precedenza.</span><span class="sxs-lookup"><span data-stu-id="45b57-250">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span> 

<span data-ttu-id="45b57-251">Gli oggetti vengono quindi inseriti in una matrice di risultati.</span><span class="sxs-lookup"><span data-stu-id="45b57-251">The objects are then put into a results array.</span></span> <span data-ttu-id="45b57-252">Questa matrice viene analizzata in JSON utilizzando Knockout e memorizzata nell'archivio locale del browser per migliorare le prestazioni su caricamenti di pagina futuri.</span><span class="sxs-lookup"><span data-stu-id="45b57-252">This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="45b57-253">Vantaggi di questo approccio</span><span class="sxs-lookup"><span data-stu-id="45b57-253">Benefits of this approach</span></span>

<span data-ttu-id="45b57-254">Uno dei principali vantaggi di [questo approccio](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) consiste nel fatto che tramite l'archiviazione locale di HTML5 la struttura di spostamento viene archiviata localmente per l'utente al successivo caricamento della pagina.</span><span class="sxs-lookup"><span data-stu-id="45b57-254">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span> <span data-ttu-id="45b57-255">Si ottengono miglioramenti delle prestazioni principali utilizzando l'API di ricerca per l'esplorazione strutturale; tuttavia, sono necessarie alcune capacità tecniche per eseguire e personalizzare questa funzionalità.</span><span class="sxs-lookup"><span data-stu-id="45b57-255">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span> 

<span data-ttu-id="45b57-256">Nell' [implementazione di esempio](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), i siti vengono ordinati in modo analogo a quello della struttura di spostamento strutturale fuori campo. ordine alfabetico.</span><span class="sxs-lookup"><span data-stu-id="45b57-256">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order.</span></span> <span data-ttu-id="45b57-257">Se si desidera deviare da questo ordine, diventa più complesso lo sviluppo e la manutenzione.</span><span class="sxs-lookup"><span data-stu-id="45b57-257">If you wanted to deviate from this order, it would be more complicated to develop and maintain.</span></span> <span data-ttu-id="45b57-258">Inoltre, questo approccio richiede di deviare dalle pagine master supportate.</span><span class="sxs-lookup"><span data-stu-id="45b57-258">Also, this approach requires you to deviate from the supported master pages.</span></span> <span data-ttu-id="45b57-259">Se non viene mantenuta la pagina master personalizzata, il sito verrà escluso dagli aggiornamenti e dai miglioramenti che Microsoft apporta alle pagine master.</span><span class="sxs-lookup"><span data-stu-id="45b57-259">If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="45b57-260">Il [codice sopra](#about-the-javascript-file) riportato presenta le dipendenze seguenti:</span><span class="sxs-lookup"><span data-stu-id="45b57-260">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="45b57-261">jQueryhttp://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="45b57-261">jQuery - http://jquery.com/</span></span>
- <span data-ttu-id="45b57-262">KnockoutJS -http://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="45b57-262">KnockoutJS - http://knockoutjs.com/</span></span>
- <span data-ttu-id="45b57-263">LINQ. js- http://linqjs.codeplex.com/o github.com/neuecc/LINQ.js</span><span class="sxs-lookup"><span data-stu-id="45b57-263">Linq.js - http://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="45b57-264">La versione corrente di LinqJS non contiene il metodo ByHierarchy utilizzato nel codice precedente e interrompe il codice di spostamento.</span><span class="sxs-lookup"><span data-stu-id="45b57-264">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code.</span></span> <span data-ttu-id="45b57-265">Per risolvere il cosa, aggiungere il metodo seguente al file LINQ. js prima della riga `Flatten: function ()`.</span><span class="sxs-lookup"><span data-stu-id="45b57-265">To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

```
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);
    
     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;

    return new Enumerable(function() {
         var enumerator;
         var index = 0;

        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };

        return new IEnumerator(

        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }

                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```
  
## <a name="related-topics"></a><span data-ttu-id="45b57-266">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="45b57-266">Related topics</span></span>

[<span data-ttu-id="45b57-267">Panoramica dell'esplorazione gestita in SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="45b57-267">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

