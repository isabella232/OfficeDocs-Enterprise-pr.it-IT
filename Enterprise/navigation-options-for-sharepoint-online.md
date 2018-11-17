---
title: Opzioni di spostamento per SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: In questo articolo vengono descritti lo spostamento opzioni siti con pubblicazione di SharePoint abilitati in SharePoint Online. La configurazione della struttura di spostamento e la scelta influisce sulle notevolmente le prestazioni e scalabilità dei siti di SharePoint Online.
ms.openlocfilehash: 5a190ca643c20b6644ca1eecdac2a4a2e281a09e
ms.sourcegitcommit: 45633b7034ee98d0cd833db9743f283b638237f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "26547178"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="47f8f-104">Opzioni di spostamento per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="47f8f-104">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="47f8f-p102">In questo articolo vengono descritti lo spostamento opzioni siti con pubblicazione di SharePoint abilitati in SharePoint Online. La configurazione della struttura di spostamento e la scelta influisce sulle notevolmente le prestazioni e scalabilità dei siti di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p102">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online. The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span>

## <a name="overview"></a><span data-ttu-id="47f8f-107">Panoramica</span><span class="sxs-lookup"><span data-stu-id="47f8f-107">Overview</span></span>

<span data-ttu-id="47f8f-p103">Configurazione del provider di spostamento può ridurre notevolmente le prestazioni per l'intero sito e un'attenta valutazione deve essere prese per selezionare un provider di spostamento e la configurazione ridimensiona in modo efficace per i requisiti di un sito di SharePoint. Esistono due provider di spostamento della finestra, nonché le implementazioni di spostamento personalizzato.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p103">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site. There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="47f8f-p104">La prima opzione, [**esplorazione gestita (metadati)**](#using-managed-navigation-and-metadata-in-sharepoint-online), è consigliabile e tra le opzioni predefinite in SharePoint Online, Tuttavia, si consiglia la disabilitazione di limitazione per motivi di sicurezza se non necessario. Limitazione per motivi di sicurezza è abilitata come impostazione sicura per impostazione predefinita per il provider di spostamento; Tuttavia, molti siti non richiedono l'overhead di sicurezza di limitazione per motivi poiché gli elementi di spostamento sono spesso coerenti per tutti gli utenti del sito. Con la configurazione consigliata per disabilitare la limitazione per motivi di sicurezza, il provider di spostamento non richiede l'enumerazione struttura del sito e altamente scalabile con un impatto sulle prestazioni accettabili.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p104">The first option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), is recommended, and is one of the default options in SharePoint Online; however, we recommend that security trimming be disabled unless required. Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site. With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="47f8f-p105">La seconda opzione, la [**struttura di spostamento**](#using-structural-navigation-in-sharepoint-online), **non un'opzione di spostamento consigliato in SharePoint Online**. Questo provider di spostamento è stato progettato per il supporto di SharePoint Online è limitato una topologia locale. Mentre offre alcuni altri set di funzionalità e altre opzioni di spostamento, queste caratteristiche, tra cui limitazione per motivi di sicurezza e sull'enumerazione struttura del sito, ha un costo di chiamate un sovraccarico del server e le prestazioni e scalabilità impatti quando viene utilizzata. Siti che utilizzano structed spostamento che utilizzano risorse eccessive possono essere soggetto di limitazione.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p105">The second option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), **is NOT a recommended navigation option in SharePoint Online**. This navigation provider was designed for an on-premises topology has limited support in SharePoint Online. While it provides some additional set of capabilities versus other navigation options, these features, including security trimming and site structure enumeration, comes at a cost of excessive server calls and impacts scalability and performance when it is used. Sites using structed navigation that consume excessive resources may be subject to throttling.</span></span>

<span data-ttu-id="47f8f-p106">Oltre ai provider di spostamento della finestra, molti clienti hanno implementato con successo implementazioni di spostamento personalizzato alternativi. Una classe comune delle implementazioni di spostamento personalizzato prestare modelli di progettazione viene eseguito il rendering client che archiviano una cache locale di nodi. Vedere **[creazione di script sul lato client basate sulla ricerca](#using-search-driven-client-side-scripting)** in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p106">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations. One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes. (See **[Search-driven client-side scripting](#using-search-driven-client-side-scripting)** in this article.)</span></span>

<span data-ttu-id="47f8f-120">Tali provider spostamento hanno due vantaggi principali:</span><span class="sxs-lookup"><span data-stu-id="47f8f-120">These navigation providers have a couple of key advantages:</span></span> 
- <span data-ttu-id="47f8f-121">In genere con cui lavorano anche progettazioni di pagina risponde.</span><span class="sxs-lookup"><span data-stu-id="47f8f-121">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="47f8f-122">Sono estremamente scalabili e ad alte prestazioni dal momento che è possibile eseguire il rendering con alcun costo della risorsa (e l'aggiornamento in background dopo un intervallo di timeout).</span><span class="sxs-lookup"><span data-stu-id="47f8f-122">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span> 
- <span data-ttu-id="47f8f-123">Tali provider spostamento può recuperare dati di spostamento con diverse strategie, compresi tra configurazioni statiche semplice per vari provider di dati dinamico.</span><span class="sxs-lookup"><span data-stu-id="47f8f-123">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span> 

<span data-ttu-id="47f8f-124">Un esempio di un provider di dati consiste nell'utilizzare una **struttura di spostamento basata sulla ricerca**, che consente la flessibilità per l'enumerazione dei nodi di spostamento e la gestione efficiente motivi di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="47f8f-124">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span> 

<span data-ttu-id="47f8f-p107">Sono disponibili altre opzioni più comuni per creare **provider di spostamento personalizzato**. Esaminare [le soluzioni di spostamento per i portali di SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) per ulteriori informazioni sulla creazione di un provider di spostamento personalizzato.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p107">There are other popular options to build **Custom navigation providers**. Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="47f8f-127">Opzioni di spostamento vantaggi e svantaggi di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="47f8f-127">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="47f8f-128">Nella tabella seguente sono riepilogati i vantaggi e gli svantaggi di ogni opzione.</span><span class="sxs-lookup"><span data-stu-id="47f8f-128">The following table summarizes the pros and cons of each option.</span></span> 


|<span data-ttu-id="47f8f-129">Esplorazione gestita</span><span class="sxs-lookup"><span data-stu-id="47f8f-129">Managed navigation</span></span>  |<span data-ttu-id="47f8f-130">Esplorazione strutturale</span><span class="sxs-lookup"><span data-stu-id="47f8f-130">Structural navigation</span></span>  |<span data-ttu-id="47f8f-131">Esplorazione basata sulla ricerca</span><span class="sxs-lookup"><span data-stu-id="47f8f-131">Search-driven navigation</span></span>  |<span data-ttu-id="47f8f-132">Provider di spostamento personalizzato</span><span class="sxs-lookup"><span data-stu-id="47f8f-132">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="47f8f-133">Pro:</span><span class="sxs-lookup"><span data-stu-id="47f8f-133">Pros:</span></span><br/><br/><span data-ttu-id="47f8f-134">Facile da gestire</span><span class="sxs-lookup"><span data-stu-id="47f8f-134">Easy to maintain</span></span><br/><span data-ttu-id="47f8f-135">Opzione consigliata</span><span class="sxs-lookup"><span data-stu-id="47f8f-135">Recommended option</span></span><br/>     |<span data-ttu-id="47f8f-136">Pro:</span><span class="sxs-lookup"><span data-stu-id="47f8f-136">Pros:</span></span><br/><br/><span data-ttu-id="47f8f-137">Semplice da configurare</span><span class="sxs-lookup"><span data-stu-id="47f8f-137">Easy to configure</span></span><br/><span data-ttu-id="47f8f-138">Per motivi di sicurezza</span><span class="sxs-lookup"><span data-stu-id="47f8f-138">Security trimmed</span></span><br/><span data-ttu-id="47f8f-139">Viene aggiornato automaticamente con l'aggiunta di contenuto</span><span class="sxs-lookup"><span data-stu-id="47f8f-139">Automatically updates as content is added</span></span><br/>|<span data-ttu-id="47f8f-140">Vantaggi:</span><span class="sxs-lookup"><span data-stu-id="47f8f-140">Pros:</span></span><br/><br/><span data-ttu-id="47f8f-141">Per motivi di sicurezza</span><span class="sxs-lookup"><span data-stu-id="47f8f-141">Security trimmed</span></span><br/><span data-ttu-id="47f8f-142">Si aggiorna automaticamente man mano che i siti vengono aggiunti</span><span class="sxs-lookup"><span data-stu-id="47f8f-142">Automatically updates as sites are added</span></span><br/><span data-ttu-id="47f8f-143">Tempo di caricamento rapido e struttura dell'esplorazione memorizzata nella cache</span><span class="sxs-lookup"><span data-stu-id="47f8f-143">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="47f8f-144">Vantaggi:</span><span class="sxs-lookup"><span data-stu-id="47f8f-144">Pros:</span></span><br/><br/><span data-ttu-id="47f8f-145">Più ampia scelta delle opzioni disponibili</span><span class="sxs-lookup"><span data-stu-id="47f8f-145">Wider choice of options available</span></span><br/><span data-ttu-id="47f8f-146">Caricamento rapido quando la memorizzazione nella cache viene utilizzato in modo corretto</span><span class="sxs-lookup"><span data-stu-id="47f8f-146">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="47f8f-147">Molte opzioni funzionano bene con struttura delle pagine risponde</span><span class="sxs-lookup"><span data-stu-id="47f8f-147">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="47f8f-148">Contro:</span><span class="sxs-lookup"><span data-stu-id="47f8f-148">Cons:</span></span><br/><br/><span data-ttu-id="47f8f-149">Non si aggiorna automaticamente per riflettere la struttura del sito</span><span class="sxs-lookup"><span data-stu-id="47f8f-149">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="47f8f-150">Influisce sulle prestazioni se è abilitata la rimozione di sicurezza</span><span class="sxs-lookup"><span data-stu-id="47f8f-150">Impacts performance if security trimming is enabled</span></span><br/>|<span data-ttu-id="47f8f-151">Contro:</span><span class="sxs-lookup"><span data-stu-id="47f8f-151">Cons:</span></span><br/><br/><span data-ttu-id="47f8f-152">**Scelta non consigliata**</span><span class="sxs-lookup"><span data-stu-id="47f8f-152">**Not recommended**</span></span><br/><span data-ttu-id="47f8f-153">**Influisce sulle prestazioni e scalabilità**</span><span class="sxs-lookup"><span data-stu-id="47f8f-153">**Impacts performance and scalability**</span></span><br/><span data-ttu-id="47f8f-154">**Soggetti a limitazione delle richieste**</span><span class="sxs-lookup"><span data-stu-id="47f8f-154">**Subject to throttling**</span></span><br/>|<span data-ttu-id="47f8f-155">Contro:</span><span class="sxs-lookup"><span data-stu-id="47f8f-155">Cons:</span></span><br/><br/><span data-ttu-id="47f8f-156">Non è possibile ordinare facilmente i siti</span><span class="sxs-lookup"><span data-stu-id="47f8f-156">No ability to easily order sites</span></span><br/><span data-ttu-id="47f8f-157">Richiede la personalizzazione della pagina master (necessarie competenze tecniche)</span><span class="sxs-lookup"><span data-stu-id="47f8f-157">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="47f8f-158">Contro:</span><span class="sxs-lookup"><span data-stu-id="47f8f-158">Cons:</span></span><br/><br/><span data-ttu-id="47f8f-159">Sviluppo personalizzato è obbligatorio</span><span class="sxs-lookup"><span data-stu-id="47f8f-159">Custom development is required</span></span><br/><span data-ttu-id="47f8f-160">Origine dati esterna / cache memorizzati è necessario ad esempio Azure</span><span class="sxs-lookup"><span data-stu-id="47f8f-160">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="47f8f-p108">L'opzione più appropriata per il sito dipenderà alle specifiche esigenze di siti e le funzionalità tecniche. Se si desidera che un provider di spostamento della casella scalabile, spostamento gestite con limitazione per motivi di sicurezza disabilitato è un'opzione ottima.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p108">The most appropriate option for your site will depend on your site requirements and on your technical capability. If you want a scalable out-of-the-box navigation provider, then Managed navigation with security trimming disabled is a very good option.</span></span> 

<span data-ttu-id="47f8f-p109">È possibile mantenere l'opzione di esplorazione gestita tramite la configurazione, non implicano l'utilizzo di file di personalizzazione di codice ed è notevolmente più veloce di struttura di spostamento. Se si richiedono la limitazione per motivi di sicurezza e ha familiarità con una pagina master personalizzata e alcune funzionalità nell'organizzazione per gestire le modifiche che possono verificarsi nella pagina master predefinita per SharePoint Online, l'opzione basate sulla ricerca potrebbe verificarsi un migliore esperienza utente. Se si dispone di più complesse, un provider di spostamento personalizzato può essere la scelta ideale. Struttura di spostamento non è consigliato.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p109">The Managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than structural navigation. If you require security trimming and are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the Search-driven option may produce a better user experience. If you have more complex requirements, then a custom navigation provider may be the right choice. Structural navigation is NOT recommended.</span></span>

<span data-ttu-id="47f8f-p110">Infine, è importante tenere presente che SharePoint viene aggiunta di provider di spostamento aggiuntivi e le funzionalità per sfruttare una gerarchia del sito più bidimensionale e un modello hub and spoke con i siti hub SharePoint moderne architetture del sito SharePoint. In questo modo molti scenari da raggiungere che non richiedono l'utilizzo della caratteristica Pubblicazione di SharePoint e le configurazioni di spostamento sono ottimizzate per la scalabilità e latenza in SharePoint Online. Si noti che l'applicazione lo stesso principio - semplificando la struttura complessiva del sito di pubblicazione di SharePoint a una struttura più lineare, aiuta a con le prestazioni complessive e proporzioni anche. Ciò significa che anziché una singola raccolta siti con centinaia di siti (Web secondari), una soluzione migliore deve disporre di molte raccolte siti con poche siti secondari (Web secondari).</span><span class="sxs-lookup"><span data-stu-id="47f8f-p110">Finally, it’s important to note that SharePoint is adding additional navigation providers and functionality for modern SharePoint site architectures leveraging a more flattened site hierarchy and a hub-and-spoke model with SharePoint hub sites. This allows many scenarios to be achieved that do NOT require the use of SharePoint Publishing feature, and these navigation configurations are optimized for scalability and latency within SharePoint Online. Note that applying the same principle - simplifying the overall structure of your SharePoint Publishing site to a flatter structure, often helps with overall performance and scale as well. What this means is that instead of having a single Site Collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="47f8f-171">Utilizzo di esplorazione gestita e metadati in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="47f8f-171">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="47f8f-p111">Esplorazione gestita è un'altra opzione di predefinite che è possibile utilizzare per ricreare la maggior parte delle stesse funzionalità struttura di spostamento. Metadati gestiti possono essere configurati per disporre di limitazione per motivi di sicurezza abilitate o disabilitate. Nelle configurazioni con limitazione per motivi di sicurezza disabilitato, esplorazione gestita è relativamente efficiente in caso di caricamento tutti i collegamenti di spostamento con un numero di chiamate server costante. Abilitazione della sicurezza limitazione per motivi, tuttavia, Nega alcuni dei vantaggi dell'esplorazione gestita e clienti possono scegliere di esplorare una delle soluzioni di spostamento personalizzata per ottimizzare le prestazioni e scalabilità.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p111">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation. Managed metadata can be configured to have security trimming enabled or disabled. When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls. Enabling security trimming, however, negates some of the advantages of managed navigation, and customers may choose to explore one of the custom navigation solutions for optimal performance and scalability.</span></span>

<span data-ttu-id="47f8f-p112">Numero di siti non richiedono una limitazione per motivi di sicurezza, come la struttura di spostamento è spesso coerenza per tutti gli utenti del sito. Se la rimozione di sicurezza è disattivata e viene aggiunto un collegamento alla struttura non tutti gli utenti hanno accesso a, il collegamento indicherà che ancora ma porterà a un messaggio di accesso negato. Non esiste alcun rischio di accesso non intenzionale al contenuto.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p112">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site. If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message. There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="47f8f-179">Come implementare l'esplorazione gestita e i risultati</span><span class="sxs-lookup"><span data-stu-id="47f8f-179">How to implement managed navigation and the results</span></span>

<span data-ttu-id="47f8f-180">Esistono diversi articoli su Docs.Microsoft.com sui dettagli dell'esplorazione gestita, ad esempio, vedere [Panoramica dell'esplorazione gestita in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span><span class="sxs-lookup"><span data-stu-id="47f8f-180">There are several articles on Docs.Microsoft.com about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="47f8f-p113">Per implementare esplorazione gestita, è impostare termini gli URL corrispondente alla struttura di spostamento del sito. Esplorazione gestita può anche essere curated manualmente per sostituire struttura di spostamento in molti casi. Per esempio:</span><span class="sxs-lookup"><span data-stu-id="47f8f-p113">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of  the site. Managed navigation can even be manually curated to replace structural navigation in many cases. For example:</span></span>

![Struttura dei siti SharePoint Online](media/SPONavOptionsListOfSites.png)

<span data-ttu-id="47f8f-185">L'esempio seguente mostra le prestazioni della struttura di spostamento complessa utilizzando l'esplorazione gestita.</span><span class="sxs-lookup"><span data-stu-id="47f8f-185">The following example shows the performance of the complex navigation using managed navigation.</span></span>

![Prestazioni di navigazione complesse utilizzando esplorazione gestita](media/SPONavOptionsComplexNavPerf.png)

<span data-ttu-id="47f8f-187">Utilizzo dell'esplorazione gestita in modo coerente migliora le prestazioni rispetto al metodo struttura di spostamento.</span><span class="sxs-lookup"><span data-stu-id="47f8f-187">Using managed navigation consistently improves performance compared to the structural navigation approach.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="47f8f-188">Utilizzo dell'esplorazione strutturale in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="47f8f-188">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="47f8f-p114">Questa è la struttura di spostamento della casella utilizzato per impostazione predefinita ed è la soluzione più semplice ma è pertanto un compromesso prestazioni costosa. Non richiede alcuna personalizzazione e utente tecnico può inoltre possibile aggiungere elementi, nascondere gli elementi e gestire la struttura di spostamento dalla pagina delle impostazioni. Si tratta tuttavia anche true per l'esplorazione gestita in modo, si consiglia di utilizzare l'esplorazione gestita come che è possibile inoltre facilmente gestiti e controllati anche con un miglioramento delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p114">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off. It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page. This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well with improved performance.</span></span>

![Struttura di spostamento con i siti secondari Mostra selezionata](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="47f8f-193">Attivazione dell'esplorazione strutturale in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="47f8f-193">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="47f8f-p115">Per illustrare come le prestazioni in una soluzione di SharePoint Online standard con struttura di spostamento e Mostra i siti secondari opzione attivato. Di seguito è riportata una schermata delle impostazioni presenti nella pagina **Impostazioni sito** \> **struttura di spostamento**.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p115">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on. Below is a screenshot of settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![Schermata che mostra i siti secondari](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="47f8f-197">Analisi delle prestazioni dell'esplorazione strutturale in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="47f8f-197">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="47f8f-198">Per analizzare le prestazioni di una pagina di SharePoint, utilizzare la scheda di **rete** F12 gli strumenti di sviluppo in Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="47f8f-198">To analyze the performance of a SharePoint page, use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![Schermata che mostra la scheda Rete degli strumenti di sviluppo F12](media/SPONavOptionsNetworks.png)
  
1. <span data-ttu-id="47f8f-200">Nella scheda **Rete**, fare clic nella pagina aspx in caricamento, quindi fare clic sulla scheda **Dettagli**.</span><span class="sxs-lookup"><span data-stu-id="47f8f-200">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span><br/> <span data-ttu-id="47f8f-201">![Schermata che mostra la scheda dei dettagli](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span><span class="sxs-lookup"><span data-stu-id="47f8f-201">![Screenshot showing the details tab](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span></span><br/>
2. <span data-ttu-id="47f8f-202">Fare clic su **Intestazioni di risposta**.</span><span class="sxs-lookup"><span data-stu-id="47f8f-202">Click **Response headers**.</span></span> <br/><span data-ttu-id="47f8f-203">![Schermata scheda Dettagli](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span><span class="sxs-lookup"><span data-stu-id="47f8f-203">![Screenshot of Details tab](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span></span><br/><span data-ttu-id="47f8f-204">SharePoint restituisce alcune informazioni utili per la diagnostiche delle intestazioni di risposta.</span><span class="sxs-lookup"><span data-stu-id="47f8f-204">SharePoint returns some useful diagnostic information in its response headers.</span></span> 
3. <span data-ttu-id="47f8f-p116">Uno dei componenti maggiormente utili di informazioni è **SPRequestDuration** è il valore espresso in millisecondi, di una richiesta di tempo richiesto per l'elaborazione sul server. Nella schermata seguente **Mostra i siti secondari** è selezionata per la struttura di spostamento. Ciò significa che non vi è solo il collegamento di raccolta siti nel riquadro di spostamento globale:</span><span class="sxs-lookup"><span data-stu-id="47f8f-p116">One of the most useful pieces of information is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server. In the following screenshot **show subsites** is unchecked for the structural navigation. This means that there is only the site collection link in the global navigation:</span></span><br/><span data-ttu-id="47f8f-208">![Schermata che mostra i tempi di caricamento come durata richiesta](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span><span class="sxs-lookup"><span data-stu-id="47f8f-208">![Screenshot showing load times as request duration](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span></span><br/>
4. <span data-ttu-id="47f8f-p117">Il tasto **SPRequestDuration** ha un valore di 245 millisecondi. Rappresenta il tempo impiegato per restituire la richiesta. Poiché esiste un solo elemento di spostamento nel sito, questo è un riscontro valido per modalità SharePoint Online esegue senza spostamento spessi. Nella schermata successiva viene illustrato l'aggiunta nei siti secondari su questa chiave.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p117">The **SPRequestDuration** key has a value of 245 milliseconds. This represents the time it took to return the request. Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation. The next screen shot shows how adding in the subsites affects this key.</span></span><br/><span data-ttu-id="47f8f-213">![Schermata che illustra una durata richiesta di 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span><span class="sxs-lookup"><span data-stu-id="47f8f-213">![Screenshot showing a request duration of 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span></span><br/>
  
<span data-ttu-id="47f8f-p118">Aggiunta di siti secondari è aumentata in modo significativo il tempo che necessario per restituire la richiesta della pagina per il sito di esempio relativamente semplice. Gerarchie di siti complessi, incluse le pagine nella struttura di spostamento e configurazione e altre opzioni di topologia possono aumentare notevolmente ulteriormente tale impatto.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p118">Adding the subsites has significantly increased the time it takes to return the page request for this relatively simple sample site. Complex site hierarchies, including pages in navigation, and other configuration and topology options can dramatically increase this impact even further.</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="47f8f-216">Utilizzo di script sul lato client basato sulla ricerca</span><span class="sxs-lookup"><span data-stu-id="47f8f-216">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="47f8f-p119">Utilizzo di ricerca è possibile utilizzare gli indici vengono sviluppati in background tramite ricerca per indicizzazione continua. I risultati della ricerca vengono estratti dall'indice di ricerca e i risultati vengono tagliati sicurezza. Si tratta in genere più provider di spostamento della casella rapido durante la limitazione per motivi di protezione è necessario. Utilizzo della ricerca per la struttura di spostamento, in particolare se si dispone di una struttura del sito complessa, velocizzare il caricamento notevolmente ora della pagina. Il vantaggio principale di questo oggetto su esplorazione gestita è vantaggiosa limitazione per motivi di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p119">Using search you can leverage the indexes that are built up in the background using continuous crawl. The search results are pulled from the search index and the results are security-trimmed. This is generally faster than out-of-the-box navigation providers when security trimming is required. Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably. The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="47f8f-p120">Questo approccio prevede la creazione di una pagina master personalizzata e sostituendo il codice di struttura di spostamento della casella con HTML personalizzati. Eseguire la procedura descritta nell'esempio seguente per sostituire il codice di struttura di spostamento nel file `seattle.html`. In questo esempio, si aprirà la `seattle.html` di file e sostituire l'intero elemento `id=”DeltaTopNavigation”` con il codice HTML personalizzato.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p120">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML. Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`. In this example, you will open the `seattle.html` file and replace the whole element `id=”DeltaTopNavigation”` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="47f8f-225">Esempio: Sostituire il codice di struttura di spostamento della finestra in una pagina master</span><span class="sxs-lookup"><span data-stu-id="47f8f-225">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1.  <span data-ttu-id="47f8f-226">Andare alla pagina Impostazioni sito.</span><span class="sxs-lookup"><span data-stu-id="47f8f-226">Navigate to the Site Settings page.</span></span>
2.  <span data-ttu-id="47f8f-227">Aprire la raccolta di pagine master facendo clic su **Pagine master**.</span><span class="sxs-lookup"><span data-stu-id="47f8f-227">Open the master page gallery by clicking **Master Pages**.</span></span>
3.  <span data-ttu-id="47f8f-228">Da qui è possibile spostarsi tra la raccolta e scaricare il file `seattle.master`.</span><span class="sxs-lookup"><span data-stu-id="47f8f-228">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4.  <span data-ttu-id="47f8f-229">Modificare il codice utilizzando un editor di testo ed eliminare il blocco di codice nella schermata seguente.</span><span class="sxs-lookup"><span data-stu-id="47f8f-229">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![Eliminare il blocco di codice riportato](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="47f8f-231">Rimuovere il codice tra il `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` e `<\SharePoint:AjaxDelta>` tags e sostituirlo con il frammento di codice seguente:</span><span class="sxs-lookup"><span data-stu-id="47f8f-231">Remove the code between the `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

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
6. <span data-ttu-id="47f8f-p121">Sostituire l'URL nel caricamento dell'immagine tag di ancoraggio all'inizio, con un collegamento a un'immagine nella raccolta siti. Dopo aver apportato le modifiche, rinominare il file e quindi caricare nella raccolta pagine master. Verrà generato un nuovo file con estensione master.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p121">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection. After you have made the changes, rename the file and then upload it to the master page gallery. This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="47f8f-p122">In questo codice HTML è il markup di base che verrà popolato per i risultati della ricerca restituiti dal codice JavaScript. È necessario modificare il codice per modificare il valore di var radice = "URL della raccolta siti" come illustrato nel frammento di seguito:</span><span class="sxs-lookup"><span data-stu-id="47f8f-p122">This HTML is the basic markup that will be populated by the search results returned from JavaScript code. You will need to edit the code to change the value for var root = “site collection URL” as demonstrated in the following snippet:</span></span><br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. <span data-ttu-id="47f8f-p123">I risultati vengono assegnati alla matrice self.nodes e viene creata una gerarchia dagli oggetti utilizzando linq.js assegnazione l'output a una matrice self.hierarchy. Questa matrice è l'oggetto che viene associato al codice HTML. Questa operazione viene eseguita nella funzione toggleView() passando l'oggetto self-alla funzione ko.applyBinding().</span><span class="sxs-lookup"><span data-stu-id="47f8f-p123">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.hierarchy. This array is the object that is bound to the HTML. This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="47f8f-240">In questo modo quindi la matrice di gerarchia per l'associazione ai HTML seguenti:</span><span class="sxs-lookup"><span data-stu-id="47f8f-240">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

<span data-ttu-id="47f8f-241">I gestori eventi per `mouseenter` e `mouseexit` vengono aggiunti al riquadro di spostamento principale per gestire i menu a discesa sito secondario che viene effettuata nel `addEventsToElements()` funzione.</span><span class="sxs-lookup"><span data-stu-id="47f8f-241">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="47f8f-242">In questo esempio di navigazione complesse, una pagina nuova carico senza mostrato nella cache locale il tempo impiegato per il server è stato eliminato verso il basso da benchmark struttura di spostamento per ottenere un risultato simile come il metodo di esplorazione gestita.</span><span class="sxs-lookup"><span data-stu-id="47f8f-242">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="47f8f-243">Sul file JavaScript...</span><span class="sxs-lookup"><span data-stu-id="47f8f-243">About the JavaScript file...</span></span>

<span data-ttu-id="47f8f-244">Di seguito è riportato l'intero file JavaScript:</span><span class="sxs-lookup"><span data-stu-id="47f8f-244">The entire JavaScript file is as follows:</span></span>

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

<span data-ttu-id="47f8f-p124">Per riassumere il codice indicato nella precedente il `jQuery $(document).ready` funzione non esiste un `viewModel object` creato e quindi la `loadNavigationNodes()` funzione per tale oggetto viene chiamato. Questa funzione viene caricato eseguire una gerarchia di spostamento compilata precedentemente memorizzata nell'archivio locale HTML5 del browser del client o chiama la funzione `queryRemoteInterface()`.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p124">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="47f8f-p125">`QueryRemoteInterface()`Crea una richiesta tramite il `getRequest()` funzione con il parametro di query definito in precedenza nello script e quindi restituisce dati dal server. Questi dati sono fondamentalmente una matrice di tutti i siti della raccolta siti rappresentati come oggetti di trasferimento dati diverse proprietà.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p125">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span> 

<span data-ttu-id="47f8f-249">Questi dati viene quindi analizzati in definita in precedenza `SPO.Models.NavigationNode` gli oggetti che utilizzano `Knockout.js` per creare proprietà presenza da utilizzare per i valori di tale associazione a HTML definita in precedenza.</span><span class="sxs-lookup"><span data-stu-id="47f8f-249">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span> 

<span data-ttu-id="47f8f-p126">Gli oggetti vengono quindi inseriti in una matrice dei risultati. Questa matrice viene analizzata in JSON utilizzando foratura e memorizzata nell'archivio locale del browser per migliorare le prestazioni nella pagina future carichi.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p126">The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="47f8f-252">Vantaggi di questo approccio</span><span class="sxs-lookup"><span data-stu-id="47f8f-252">Benefits of this approach</span></span>

<span data-ttu-id="47f8f-p127">Uno dei vantaggi principale di [questo metodo](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) è che utilizzando HTML5 archiviazione locale, la struttura di spostamento viene archiviato in locale per l'utente al successivo che momento del caricamento della pagina. È possibile ottenere miglioramenti delle prestazioni principali di utilizzare l'API di ricerca per la struttura di spostamento; Tuttavia, ha alcune funzionalità tecniche per l'esecuzione e personalizzare questa funzionalità.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p127">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page. We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span> 

<span data-ttu-id="47f8f-p128">Nell' [esempio di implementazione](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), i siti vengono ordinati allo stesso modo di casella struttura di spostamento; ordine alfabetico. Se si desidera diversi da quest'ordine, potrebbe risultare più complessa sviluppare e gestire. Inoltre, questo approccio richiede diversi dalle pagine master supportate. Se la pagina master personalizzata non viene mantenuta, il sito verrà perdere: aggiornamenti e i miglioramenti che Microsoft consente alle pagine master.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p128">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order. If you wanted to deviate from this order, it would be more complicated to develop and maintain. Also, this approach requires you to deviate from the supported master pages. If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="47f8f-259">Il [precedente codice](#about-the-javascript-file) ha le dipendenze seguenti:</span><span class="sxs-lookup"><span data-stu-id="47f8f-259">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="47f8f-260">jQuery-http://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="47f8f-260">jQuery - http://jquery.com/</span></span>
- <span data-ttu-id="47f8f-261">KnockoutJS-http://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="47f8f-261">KnockoutJS - http://knockoutjs.com/</span></span>
- <span data-ttu-id="47f8f-262">LINQ.js - http://linqjs.codeplex.com/, o github.com/neuecc/linq.js</span><span class="sxs-lookup"><span data-stu-id="47f8f-262">Linq.js - http://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="47f8f-p129">La versione corrente di LinqJS non contiene il metodo ByHierarchy utilizzato nel codice precedente e interromperà il codice di struttura di spostamento. Per risolvere questo problema, aggiungere il metodo seguente al file Linq.js prima della riga `Flatten: function ()`.</span><span class="sxs-lookup"><span data-stu-id="47f8f-p129">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code. To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

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
  
## <a name="related-topics"></a><span data-ttu-id="47f8f-265">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="47f8f-265">Related topics</span></span>

[<span data-ttu-id="47f8f-266">Panoramica dell'esplorazione gestita in SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="47f8f-266">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

