---
title: Opzioni di spostamento per SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/27/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: In questo articolo viene descritto come migliorare i tempi di caricamento delle pagine per SharePoint Online mediante l'utilizzo di esplorazione gestita o lo spostamento basato sulla ricerca nella pubblicazione classica.
ms.openlocfilehash: 6b2ee613d0cc6a6df92eb9b53374087a0ac2e5b7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541384"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="66d8c-103">Opzioni di spostamento per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="66d8c-103">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="66d8c-104">In questo articolo viene descritto come migliorare i tempi di caricamento delle pagine per SharePoint Online mediante l'utilizzo di esplorazione gestita o lo spostamento basato sulla ricerca nella pubblicazione classica.</span><span class="sxs-lookup"><span data-stu-id="66d8c-104">This article describes how to improve page load times for SharePoint Online by using managed navigation or search-driven navigation in Classic publishing.</span></span>
  
<span data-ttu-id="66d8c-105">SharePoint Online con pubblicazione classica abilitata sono presenti due aree di spostamento; Struttura di spostamento globale e struttura di spostamento corrente.</span><span class="sxs-lookup"><span data-stu-id="66d8c-105">SharePoint Online with classic publishing enabled has two navigation areas; Global Navigation and Current Navigation.</span></span>
  
<span data-ttu-id="66d8c-106">Struttura di spostamento globale è il menu di spostamento superiore durante la struttura di spostamento corrente rappresenta la parte o una struttura di spostamento sinistra o verso destra nel contesto varia a seconda di configurazione di lingua e pagina master utilizzata.</span><span class="sxs-lookup"><span data-stu-id="66d8c-106">Global navigation is the top navigation menu while Current Navigation is the side or in-context left/right navigation dependent on the language configuration and master page utilized.</span></span>
  
<span data-ttu-id="66d8c-107">Struttura di spostamento può impatto negativo sulle prestazioni per l'intero portale come spesso è configurato per l'utilizzo a livello di portale e pertanto è un importante elemento di un sito di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="66d8c-107">Navigation can negatively impact performance for the entire Portal as it is often configured for portal-wide use and as such is an important element of any SharePoint site.</span></span>
  
<span data-ttu-id="66d8c-108">Struttura di spostamento non è l'opzione di esplorazione consigliato in SharePoint Online è stata progettata per una topologia locale con limitazione per motivi di sicurezza e questa struttura fa sì che le chiamate di un sovraccarico del server e influisce sulle prestazioni quando viene utilizzata.</span><span class="sxs-lookup"><span data-stu-id="66d8c-108">Structural navigation is not the recommended navigation option in SharePoint Online as it was designed for an On-premise topology with security trimming and this design causes excessive server calls and impacts performance when it is used.</span></span>
  
<span data-ttu-id="66d8c-p101">Di progettazione è stato modificato con l'introduzione di siti di SharePoint moderno dove moderno dispone di una gerarchia di siti bidimensionale semplificata. Ciò è semplificato esplorazione con una gerarchia semplificata che ha eliminato problemi di prestazioni relative alla struttura di spostamento.</span><span class="sxs-lookup"><span data-stu-id="66d8c-p101">That design has changed with the introduction of Modern SharePoint sites where Modern has a simplified flattened site hierarchy. This has simplified navigation with a simplified hierarchy that has eliminated performance issues related to navigation.</span></span>
  
<span data-ttu-id="66d8c-p102">Sono disponibili due opzioni di spostamento della finestra principale di SharePoint, nonché un terzo, l'approccio personalizzato, basate sulla ricerca. In alternativa, opzione relativamente più comuni e una quarta consiste nel creare un Provider di spostamento personalizzato. Esaminare [le soluzioni di spostamento per i portali di SharePoint Online](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) per informazioni su un provider di spostamento personalizzato.</span><span class="sxs-lookup"><span data-stu-id="66d8c-p102">There are two main out-of-the-box navigation options in SharePoint as well as a third, custom, search-driven approach. Alternatively, a fourth and fairly popular option is to build a Custom Navigation Provider. Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) for guidance on a Custom navigation provider.</span></span> 
  
<span data-ttu-id="66d8c-114">Ogni opzione presenta vantaggi e gli svantaggi, come descritto nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="66d8c-114">Each option has pros and cons as outlined in the following table.</span></span>
  
|<span data-ttu-id="66d8c-115">**Esplorazione strutturale**</span><span class="sxs-lookup"><span data-stu-id="66d8c-115">**Structural navigation**</span></span>|<span data-ttu-id="66d8c-116">**Esplorazione gestita**</span><span class="sxs-lookup"><span data-stu-id="66d8c-116">**Managed navigation**</span></span>|<span data-ttu-id="66d8c-117">**Esplorazione basata sulla ricerca**</span><span class="sxs-lookup"><span data-stu-id="66d8c-117">**Search-driven navigation**</span></span>||<span data-ttu-id="66d8c-118">**Provider di spostamento personalizzato**</span><span class="sxs-lookup"><span data-stu-id="66d8c-118">**Custom Navigation Provider**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
| <span data-ttu-id="66d8c-119">Pro:</span><span class="sxs-lookup"><span data-stu-id="66d8c-119">Pros:</span></span>  <br/>  <span data-ttu-id="66d8c-120">Semplice da configurare</span><span class="sxs-lookup"><span data-stu-id="66d8c-120">Easy to configure</span></span>  <br/>  <span data-ttu-id="66d8c-121">Limitato per motivi di sicurezza</span><span class="sxs-lookup"><span data-stu-id="66d8c-121">Security-trimmed</span></span>  <br/>  <span data-ttu-id="66d8c-122">Si aggiorna automaticamente man mano che i siti vengono aggiunti</span><span class="sxs-lookup"><span data-stu-id="66d8c-122">Automatically updates as sites are added</span></span>  <br/> | <span data-ttu-id="66d8c-123">Pro:</span><span class="sxs-lookup"><span data-stu-id="66d8c-123">Pros:</span></span>  <br/>  <span data-ttu-id="66d8c-124">Facile da gestire</span><span class="sxs-lookup"><span data-stu-id="66d8c-124">Easy to maintain</span></span>  <br/>  <span data-ttu-id="66d8c-125">Opzione consigliata</span><span class="sxs-lookup"><span data-stu-id="66d8c-125">Recommended option</span></span>  <br/> | <span data-ttu-id="66d8c-126">Pro:</span><span class="sxs-lookup"><span data-stu-id="66d8c-126">Pros:</span></span>  <br/>  <span data-ttu-id="66d8c-127">Limitato per motivi di sicurezza</span><span class="sxs-lookup"><span data-stu-id="66d8c-127">Security-trimmed</span></span>  <br/>  <span data-ttu-id="66d8c-128">Si aggiorna automaticamente man mano che i siti vengono aggiunti</span><span class="sxs-lookup"><span data-stu-id="66d8c-128">Automatically updates as sites are added</span></span>  <br/>  <span data-ttu-id="66d8c-129">Tempo di caricamento rapido e struttura dell'esplorazione memorizzata nella cache</span><span class="sxs-lookup"><span data-stu-id="66d8c-129">Fast loading time and locally cached navigation structure</span></span>  <br/> || <span data-ttu-id="66d8c-130">Vantaggi:</span><span class="sxs-lookup"><span data-stu-id="66d8c-130">Pros:</span></span>  <br/>    <br/>  <span data-ttu-id="66d8c-131">Scelta più ampia / opzioni disponibili</span><span class="sxs-lookup"><span data-stu-id="66d8c-131">Wider choice / options available</span></span>  <br/>  <span data-ttu-id="66d8c-132">Caricamento rapido quando la memorizzazione nella cache viene utilizzato in modo corretto</span><span class="sxs-lookup"><span data-stu-id="66d8c-132">Fast loading when caching is used correctly</span></span>  <br/> |
| <span data-ttu-id="66d8c-133">Contro:</span><span class="sxs-lookup"><span data-stu-id="66d8c-133">Cons:</span></span>  <br/> <span data-ttu-id="66d8c-134">**Scelta non consigliata**</span><span class="sxs-lookup"><span data-stu-id="66d8c-134">**Not recommended**</span></span> <br/> <span data-ttu-id="66d8c-135">**Influisce sulle prestazioni**</span><span class="sxs-lookup"><span data-stu-id="66d8c-135">**Impacts performance**</span></span> <br/> | <span data-ttu-id="66d8c-136">Contro:</span><span class="sxs-lookup"><span data-stu-id="66d8c-136">Cons:</span></span>  <br/>  <span data-ttu-id="66d8c-137">Non si aggiorna automaticamente per riflettere la struttura del sito</span><span class="sxs-lookup"><span data-stu-id="66d8c-137">Not automatically updated to reflect site structure</span></span>  <br/>  <span data-ttu-id="66d8c-138">Influisce sulle prestazioni se è abilitata la rimozione di sicurezza</span><span class="sxs-lookup"><span data-stu-id="66d8c-138">Impacts performance if security trimming is enabled</span></span>  <br/> | <span data-ttu-id="66d8c-139">Contro:</span><span class="sxs-lookup"><span data-stu-id="66d8c-139">Cons:</span></span>  <br/>  <span data-ttu-id="66d8c-140">Non è possibile ordinare facilmente i siti</span><span class="sxs-lookup"><span data-stu-id="66d8c-140">No ability to easily order sites</span></span>  <br/>  <span data-ttu-id="66d8c-141">Richiede la personalizzazione della pagina master (necessarie competenze tecniche)</span><span class="sxs-lookup"><span data-stu-id="66d8c-141">Requires customization of the master page (technical skills required)</span></span>  <br/> || <span data-ttu-id="66d8c-142">Contro:</span><span class="sxs-lookup"><span data-stu-id="66d8c-142">Cons:</span></span>  <br/>  <span data-ttu-id="66d8c-143">Sviluppo personalizzato è obbligatorio</span><span class="sxs-lookup"><span data-stu-id="66d8c-143">Custom development is required</span></span>  <br/>  <span data-ttu-id="66d8c-144">Origine dati esterna / cache memorizzati è necessario ad esempio Azure</span><span class="sxs-lookup"><span data-stu-id="66d8c-144">External data source / cache stored is needed e.g. Azure</span></span>  <br/> |
   
<span data-ttu-id="66d8c-p103">L'opzione più appropriata per il sito dipenderà alle specifiche esigenze di siti e le funzionalità tecniche. Se si ha familiarità con una pagina master personalizzata e alcune funzionalità nell'organizzazione per gestire le modifiche che possono verificarsi nella pagina master predefinita per SharePoint Online, l'opzione basate sulla ricerca genereranno un'esperienza utente ottimale. Se si desidera semplice metà strada tra la struttura di spostamento della casella e la ricerca, l'esplorazione gestita è un'opzione ottima. È possibile mantenere l'opzione di esplorazione gestita tramite la configurazione, non comporta i file di personalizzazione di codice e è significativamente più veloce rispetto della casella struttura di spostamento.</span><span class="sxs-lookup"><span data-stu-id="66d8c-p103">The most appropriate option for your site will depend on your site requirements and on your technical capability. If you are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the search-driven option will produce the best user experience. If you want a simple middle ground between the out-of-the-box structural navigation and search, then the managed navigation is a very good option. The managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than the out-of-the-box structural navigation.</span></span>
  
<span data-ttu-id="66d8c-p104">Semplificando la struttura globale del portale classica in modo analogo moderno, aiuta a con le prestazioni e scalabilità anche globali. Ciò significa che invece una singola raccolta siti con centinaia o migliaia di sedi (Web secondari), una soluzione migliore deve disporre di molte raccolte siti con poche siti secondari (Web secondari).</span><span class="sxs-lookup"><span data-stu-id="66d8c-p104">Simplifying the overall structure of your Classic Portal much like Modern, helps with overall performance and scale as well. What this means is that instead of having a single Site Collection with hundreds / thousands of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>
  
<span data-ttu-id="66d8c-151">Questo sono disponibili ulteriori opzioni di implementazione della scalabilità per il servizio, consente di evitare la messa tutto il contenuto in un database di grande e infine maggiore flessibilità per lo spostamento e soprattutto sicurezza.</span><span class="sxs-lookup"><span data-stu-id="66d8c-151">This provides additional scaling options in the service, avoids putting all content into one big database and ultimately allows greater flexibility for navigation and more importantly security.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="66d8c-152">Utilizzo dell'esplorazione strutturale in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="66d8c-152">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="66d8c-p105">Questa è la struttura di spostamento della casella utilizzato per impostazione predefinita ed è la soluzione più semplice ma è pertanto un compromesso prestazioni costosa. Non richiede alcuna personalizzazione e utente tecnico può inoltre possibile aggiungere elementi, nascondere gli elementi e gestire la struttura di spostamento dalla pagina delle impostazioni. Si tratta tuttavia true per l'esplorazione gestita in modo, si consiglia di utilizzare l'esplorazione gestita come che può anche essere facilmente gestiti e controllati anche.</span><span class="sxs-lookup"><span data-stu-id="66d8c-p105">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off. It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page. This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well.</span></span>
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="66d8c-156">Attivazione dell'esplorazione strutturale in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="66d8c-156">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="66d8c-p106">Per illustrare come le prestazioni in una soluzione di SharePoint Online standard con struttura di spostamento e Mostra i siti secondari opzione attivato. Di seguito è una cattura di schermata impostazioni presenti nella pagina **Impostazioni sito** \> **struttura di spostamento**.</span><span class="sxs-lookup"><span data-stu-id="66d8c-p106">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on. Below is a screen shot settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![Schermata che mostra i siti secondari](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="66d8c-160">Analisi delle prestazioni dell'esplorazione strutturale in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="66d8c-160">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="66d8c-161">Per analizzare le prestazioni di una pagina di SharePoint utilizzare la scheda **Rete** degli strumenti di sviluppo F12 in Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="66d8c-161">To analyze the performance of a SharePoint page use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![Schermata che mostra la scheda Rete degli strumenti di sviluppo F12](media/e2aed8af-0843-487a-8b68-4f5260a2685e.png)
  
<span data-ttu-id="66d8c-163">Nella scheda **Rete**, fare clic nella pagina aspx in caricamento, quindi fare clic sulla scheda **Dettagli**.</span><span class="sxs-lookup"><span data-stu-id="66d8c-163">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span> 
  
![Schermata che mostra la scheda dei dettagli](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)
  
<span data-ttu-id="66d8c-165">Fare clic su **Intestazioni di risposta**.</span><span class="sxs-lookup"><span data-stu-id="66d8c-165">Click **Response headers**.</span></span>
  
![Schermata scheda Dettagli](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)
  
<span data-ttu-id="66d8c-p107">SharePoint restituisce alcune informazioni diagnostiche utili nelle intestazioni di risposta. Una delle più utili è **SPRequestDuration** che è il valore in millisecondi, del tempo che impiega una richiesta per essere elaborata sul server.</span><span class="sxs-lookup"><span data-stu-id="66d8c-p107">SharePoint returns some useful diagnostic information in its response headers. One of the most useful is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server.</span></span> 
  
<span data-ttu-id="66d8c-p108">Nella schermata seguente **Mostra i siti secondari** non è selezionata per la struttura di spostamento. Ciò significa che non vi è solo il collegamento di raccolta siti nel riquadro di spostamento globale:</span><span class="sxs-lookup"><span data-stu-id="66d8c-p108">In the following screen shot **show subsites** is unchecked for the structural navigation. This means that there is only the site collection link in the global navigation:</span></span> 
  
![Schermata che mostra i tempi di caricamento come durata richiesta](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)
  
<span data-ttu-id="66d8c-p109">Il tasto **SPRequestDuration** ha un valore di 245 millisecondi. Rappresenta il tempo impiegato per restituire la richiesta. Poiché esiste un solo elemento di spostamento nel sito, questo è un riscontro valido per modalità SharePoint Online esegue senza spostamento spessi. Nella schermata successiva viene illustrato l'aggiunta nei siti secondari su questa chiave.</span><span class="sxs-lookup"><span data-stu-id="66d8c-p109">The **SPRequestDuration** key has a value of 245 milliseconds. This represents the time it took to return the request. Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation. The next screen shot shows how adding in the subsites affects this key.</span></span> 
  
![Schermata che illustra una durata richiesta di 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)
  
<span data-ttu-id="66d8c-177">L'aggiunta di siti secondari ha aumentato sensibilmente il tempo necessario per restituire la richiesta della pagina.</span><span class="sxs-lookup"><span data-stu-id="66d8c-177">Adding the subsites has significantly increased the time it takes to return the page request.</span></span>
  
<span data-ttu-id="66d8c-178">I vantaggi derivanti dall'utilizzo di esplorazione strutturata regolare è che si possono facilmente organizzare l'ordine, nascondere i siti, aggiungere pagine, i risultati vengono tagliati sicurezza e non è differiscono dalle pagine master supportate utilizzate in SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="66d8c-178">The advantages of using the regular structured navigation is that you can easily organize the order, hide sites, add pages, the results are security-trimmed, and you are not deviating from the supported master pages used in SharePoint Online.</span></span>
  
## <a name="using-managed-navigation-and-managed-metadata-in-sharepoint-online"></a><span data-ttu-id="66d8c-179">Usare l'esplorazione gestita e i metadati gestiti di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="66d8c-179">Using managed navigation and managed metadata in SharePoint Online</span></span>

<span data-ttu-id="66d8c-180">L'esplorazione gestita è un'altra opzione predefinita che è possibile utilizzare per ricreare lo stesso tipo di funzionalità dell'esplorazione strutturale.</span><span class="sxs-lookup"><span data-stu-id="66d8c-180">Managed navigation is another out-of-the-box option that you can use to recreate the same sort of functionality as structural navigation.</span></span>
  
<span data-ttu-id="66d8c-p110">Il vantaggio di utilizzo dei metadati gestiti è è molto più veloce per recuperare i dati rispetto all'utilizzo di contenuto da query per creare la struttura del sito. Anche se è che molto più rapidamente non è possibile alla protezione di limitare i risultati in modo se un utente non dispone dell'accesso a un determinato sito, il collegamento ancora mostrerà ma porterà a un messaggio di errore.</span><span class="sxs-lookup"><span data-stu-id="66d8c-p110">The advantage of using managed metadata is that it is much faster to retrieve the data than using content by query to build the site navigation. Although it is much faster there is no way to security trim the results so if a user doesn't have access to a given site, the link will still show but will lead to an error message.</span></span>
  
 <span data-ttu-id="66d8c-183">**Come implementare l'esplorazione gestita e i risultati**</span><span class="sxs-lookup"><span data-stu-id="66d8c-183">**How to implement managed navigation and the results**</span></span>
  
<span data-ttu-id="66d8c-184">Esistono diversi articoli di TechNet sui dettagli dell'esplorazione gestita, ad esempio, vedere [Panoramica dell'esplorazione gestita in SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).</span><span class="sxs-lookup"><span data-stu-id="66d8c-184">There are several articles on TechNet about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).</span></span>
  
<span data-ttu-id="66d8c-p111">Per implementare l'esplorazione gestita, è necessario disporre di autorizzazioni di amministratore per l'archivio dei termini. Impostando termini con URL che corrispondono alla struttura di una raccolta di siti, è possibile utilizzare l'esplorazione gestita per sostituire l'esplorazione strutturale. Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="66d8c-p111">In order to implement managed navigation, you need to have term store administrator permissions. By setting up terms with URLs that match the structure of a site collection, managed navigation can be used to replace structural navigation. For example:</span></span>
  
![Schermata di esempio Subsite1](media/4155b4da-ccff-4e2a-92de-7803ac62982b.png)
  
<span data-ttu-id="66d8c-189">L'esempio seguente mostra le prestazioni della struttura di spostamento complessa utilizzando l'esplorazione gestita.</span><span class="sxs-lookup"><span data-stu-id="66d8c-189">The following example shows the performance of the complex navigation using managed navigation.</span></span>
  
![Schermata di esempio SPRequestDuration](media/72257528-0ec6-48b0-85a5-efeb7432db5b.png)
  
<span data-ttu-id="66d8c-191">L'utilizzo dell'esplorazione gestita in modo coerente migliora le prestazioni rispetto all'approccio dell'esplorazione strutturale della Query contenuto.</span><span class="sxs-lookup"><span data-stu-id="66d8c-191">Using managed navigation consistently improves performance compared to the content by query structural navigation approach.</span></span>
  
## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="66d8c-192">Utilizzo di script sul lato client basato sulla ricerca</span><span class="sxs-lookup"><span data-stu-id="66d8c-192">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="66d8c-p112">Utilizzando la ricerca è possibile utilizzare gli indici sviluppati in background tramite la ricerca per indicizzazione continua. Ciò significa che non sono presenti query di contenuto pesante. I risultati della ricerca vengono recuperati dall'indice di ricerca e i risultati sono limitati per motivi di sicurezza. Ciò è più veloce rispetto all'utilizzo di query contenuto. Utilizzando la ricerca per l'esplorazione strutturale, soprattutto se si dispone di una struttura di siti complessa, è possibile velocizzare notevolmente tempi di caricamento delle pagine. Il principale vantaggio di questa esplorazione gestita è che è possibile beneficiare della limitazione per motivi di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="66d8c-p112">Using search you can leverage the indexes that are built up in the background using continuous crawl. This means there are no heavy content queries. The search results are pulled from the search index and the results are security-trimmed. This is faster than using regular content queries. Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably. The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>
  
<span data-ttu-id="66d8c-p113">Questo approccio implica la creazione di una pagina master personalizzata e la sostituzione del codice di spostamento predefinito con codice HTML personalizzato. Seguire questa procedura per sostituire il codice della struttura di spostamento nel file seattle.html.</span><span class="sxs-lookup"><span data-stu-id="66d8c-p113">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML. Follow this procedure to replace the navigation code in the file seattle.html.</span></span>
  
<span data-ttu-id="66d8c-201">In questo esempio, si verrà aprire il file seattle.html e sostituire l'intero elemento **id = "DeltaTopNavigation"** con il codice HTML personalizzato.</span><span class="sxs-lookup"><span data-stu-id="66d8c-201">In this example, you will open the seattle.html file and replace the whole element **id="DeltaTopNavigation"** with the custom HTML code.</span></span> 
  
 <span data-ttu-id="66d8c-202">**Esempio: per sostituire il codice della struttura di spostamento predefinito in una pagina master**</span><span class="sxs-lookup"><span data-stu-id="66d8c-202">**Example: To replace the out-of-the-box navigation code in a master page**</span></span>
  
1. <span data-ttu-id="66d8c-203">Andare alla pagina **Impostazioni sito**.</span><span class="sxs-lookup"><span data-stu-id="66d8c-203">Navigate to the **Site Settings** page.</span></span> 
    
2. <span data-ttu-id="66d8c-204">Aprire la raccolta di pagine master facendo clic su **Pagine master**.</span><span class="sxs-lookup"><span data-stu-id="66d8c-204">Open the master page gallery by clicking **Master Pages**.</span></span>
    
3. <span data-ttu-id="66d8c-205">Da qui è possibile spostarsi all'interno della raccolta e scaricare il file **seattle.master**.</span><span class="sxs-lookup"><span data-stu-id="66d8c-205">From here you can navigate through the library and download the file **seattle.master**.</span></span>
    
4. <span data-ttu-id="66d8c-206">Modificare il codice utilizzando un editor di testo ed eliminare il blocco di codice nella schermata seguente.</span><span class="sxs-lookup"><span data-stu-id="66d8c-206">Edit the code using a text editor and delete the code block in the following screen shot.</span></span>
    
    ![Schermata del codice DeltaTopNavigation da eliminare](media/70db2cd2-660d-4e0d-9d5c-a5df331c73b4.png)
  
5. <span data-ttu-id="66d8c-208">Rimuovere il codice tra il \<SharePoint:AjaxDelta id = "DeltaTopNavigation"\> e \<\SharePoint:AjaxDelta\> tags e sostituirlo con il frammento di codice seguente:</span><span class="sxs-lookup"><span data-stu-id="66d8c-208">Remove the code between the \<SharePoint:AjaxDelta id="DeltaTopNavigation"\> and \<\SharePoint:AjaxDelta\> tags and replace it with the following snippet:</span></span>
    
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

6. <span data-ttu-id="66d8c-p114">Sostituire l'URL nel caricamento dell'immagine tag di ancoraggio all'inizio, con un collegamento a un'immagine nella raccolta siti. Dopo aver apportato le modifiche, rinominare il file e quindi caricare nella raccolta pagine master. Verrà generato un nuovo file con estensione master.</span><span class="sxs-lookup"><span data-stu-id="66d8c-p114">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection. After you have made the changes, rename the file and then upload it to the master page gallery. This generates a new .master file.</span></span>
    
7. <span data-ttu-id="66d8c-p115">In questo codice HTML è il markup di base che verrà popolato per i risultati della ricerca restituiti dal codice JavaScript. È necessario modificare il codice seguente per modificare il valore per il `var root = "site collection URL"` come illustrato nel frammento di seguito:</span><span class="sxs-lookup"><span data-stu-id="66d8c-p115">This HTML is the basic markup that will be populated by the search results returned from JavaScript code. You will need to edit the following code to change the value for the  `var root = "site collection URL"` as demonstrated in the following snippet:</span></span> 
    
  ```
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  ```

    <span data-ttu-id="66d8c-214">Di seguito è riportato l'intero file JavaScript:</span><span class="sxs-lookup"><span data-stu-id="66d8c-214">The entire JavaScript file is as follows:</span></span>
    
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
  var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&amp;trimduplicates=false&amp;rowlimit=300";
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
              if (cachedNodes &amp;&amp; timeStamp) {
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
              if (elem.children &amp;&amp; elem.children.length > 0) {
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
  
  ```

     <span data-ttu-id="66d8c-215">$("li.level1").mouseover (funzione () {</span><span class="sxs-lookup"><span data-stu-id="66d8c-215">$("li.level1").mouseover(function () {</span></span> 
  
<span data-ttu-id="66d8c-216">posizione var = $(this).position();</span><span class="sxs-lookup"><span data-stu-id="66d8c-216">var position = $(this).position();</span></span>
  
<span data-ttu-id="66d8c-217">$(this).find("ul.level2").css ({larghezza: 100, sinistra: position.left + 10, dall'alto: 50});</span><span class="sxs-lookup"><span data-stu-id="66d8c-217">$(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });</span></span>
    
     }) 
  
<span data-ttu-id="66d8c-218">.MOUSEOUT (funzione () {</span><span class="sxs-lookup"><span data-stu-id="66d8c-218">.mouseout(function () {</span></span>
  
<span data-ttu-id="66d8c-219">$(this).find("ul.level2").css ({sinistra:-99999 principali: 0});</span><span class="sxs-lookup"><span data-stu-id="66d8c-219">$(this).find("ul.level2").css({ left: -99999, top: 0 });</span></span>
  
<span data-ttu-id="66d8c-220">});</span><span class="sxs-lookup"><span data-stu-id="66d8c-220"></span></span>
  
<span data-ttu-id="66d8c-221">$("li.level2").mouseover (funzione () {</span><span class="sxs-lookup"><span data-stu-id="66d8c-221">$("li.level2").mouseover(function () {</span></span>
  
<span data-ttu-id="66d8c-222">posizione var = $(this).position();</span><span class="sxs-lookup"><span data-stu-id="66d8c-222">var position = $(this).position();</span></span>
  
<span data-ttu-id="66d8c-223">console.log(JSON.stringify(Position));</span><span class="sxs-lookup"><span data-stu-id="66d8c-223">console.log(JSON.stringify(position));</span></span>
  
<span data-ttu-id="66d8c-224">$(this).find("ul.level3").css ({larghezza: 100, sinistra: position.left + 95, dall'alto: position.top});</span><span class="sxs-lookup"><span data-stu-id="66d8c-224">$(this).find("ul.level3").css({ width: 100, left: position.left + 95, top: position.top});</span></span>
    
     }) 
  
<span data-ttu-id="66d8c-225">.MOUSEOUT (funzione () {</span><span class="sxs-lookup"><span data-stu-id="66d8c-225">.mouseout(function () {</span></span>
  
<span data-ttu-id="66d8c-226">$(this).find("ul.level3").css ({sinistra:-99999 principali: 0});</span><span class="sxs-lookup"><span data-stu-id="66d8c-226">$(this).find("ul.level3").css({ left: -99999, top: 0 });</span></span>
  
<span data-ttu-id="66d8c-227">});</span><span class="sxs-lookup"><span data-stu-id="66d8c-227"></span></span>
    
    } _spBodyOnLoadFunctionNames.push("InitCustomNav");
    
    To summarize the code shown above in the jQuery **[$(document).ready]** function there is a **[viewModel]** object created and then the **[loadNavigationNodes()]** function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function **[queryRemoteInterface()]**. 
    
    **[QueryRemoteInterface()]** builds a request using the **[getRequest()]** function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties. This data is then parsed into the previously defined **[SPO.Models.NavigationNode]** objects which use Knockout.js to create observable properties for use by data binding the values into the HTML that we defined earlier. The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads. 
    
8. <span data-ttu-id="66d8c-p116">Successivamente, i risultati vengono assegnati alla matrice **[self.nodes]** e viene creata una gerarchia dagli oggetti utilizzando linq.js assegnazione l'output a una matrice **[self.heirarchy]**. Questa matrice è l'oggetto che viene associato al codice HTML. Questa operazione viene eseguita nella funzione **[toggleView()]** passando l'oggetto self-alla funzione **[ko.applyBinding()]** . In questo modo quindi la matrice di gerarchia per l'associazione ai HTML seguenti:</span><span class="sxs-lookup"><span data-stu-id="66d8c-p116">Next, the results are assigned to the **[self.nodes]** array and a hierarchy is built out of the objects using linq.js assigning the output to an array **[self.heirarchy]**. This array is the object that is bound to the HTML. This is done in the **[toggleView()]** function by passing the self object to the **[ko.applyBinding()]** function. This then causes the hierarchy array to be bound to the following HTML:</span></span> 
    
  ```
  <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
  ```

    <span data-ttu-id="66d8c-232">Infine, vengono aggiunti i gestori eventi per **[mouseenter]** e **[mouseexit]** per lo spostamento principale per gestire i menu a discesa sito secondario che viene eseguito nella funzione **[addEventsToElements()]** .</span><span class="sxs-lookup"><span data-stu-id="66d8c-232">Finally, the event handlers for **[mouseenter]** and **[mouseexit]** are added to the top-level navigation to handle the subsite drop-down menus which is done in the **[addEventsToElements()]** function.</span></span> 
    
    <span data-ttu-id="66d8c-233">I risultati del riquadro di spostamento possono essere visualizzati nella schermata di seguito:</span><span class="sxs-lookup"><span data-stu-id="66d8c-233">The results of the navigation can be seen in the screen shot below:</span></span>
    
    ![Schermata dei risultati della struttura di spostamento](media/020d34d2-942a-431b-9b26-6d2c8a6fde30.png)
  
    <span data-ttu-id="66d8c-235">Questo esempio di navigazione complessa in cui una nuova pagina si carica senza memorizzazione nella cache locale mostra che il tempo impiegato sul server è stato ridotto rispetto all'esplorazione strutturale predefinita per ottenere un risultato simile a quello dell'esplorazione gestita.</span><span class="sxs-lookup"><span data-stu-id="66d8c-235">In our complex navigation example a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>
    
    ![Schermata di SPRequestDuration 301](media/307d7caf-e83a-40d9-a551-91d842521d03.png)
  
    <span data-ttu-id="66d8c-237">Uno dei principali vantaggi di questo approccio è che con l'archiviazione locale HTML5, la struttura di spostamento è archiviata in locale per l'utente la volta successiva che carica la pagina.</span><span class="sxs-lookup"><span data-stu-id="66d8c-237">One major benefit of this approach is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span>
    
<span data-ttu-id="66d8c-p117">Si ottengono miglioramenti delle prestazioni principali utilizzando l'API di ricerca per l'esplorazione strutturale; tuttavia, sono necessarie alcune capacità tecniche per eseguire e personalizzare questa funzionalità. Nell'esempio di implementazione, i siti vengono ordinati in base alla stessa stregua dell'esplorazione strutturale predefinita; in ordine alfabetico. Se si desidera deviare da questo ordine, diventa più complesso lo sviluppo e la manutenzione. Inoltre, questo approccio richiede di deviare dalle pagine master supportate. Se non viene mantenuta la pagina master personalizzata, il sito verrà escluso dagli aggiornamenti e dai miglioramenti che Microsoft apporta alle pagine master.</span><span class="sxs-lookup"><span data-stu-id="66d8c-p117">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality. In the example implementation, the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order. If you wanted to deviate from this order, it would be more complicated to develop and maintain. Also, this approach requires you to deviate from the supported master pages. If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>
  
<span data-ttu-id="66d8c-243">Nel codice precedente ha le dipendenze seguenti:</span><span class="sxs-lookup"><span data-stu-id="66d8c-243">The above code has the following dependencies:</span></span>
  
- <span data-ttu-id="66d8c-244">jQuery-[http://jquery.com/](http://jquery.com/)</span><span class="sxs-lookup"><span data-stu-id="66d8c-244">jQuery - [http://jquery.com/](http://jquery.com/)</span></span>
    
- <span data-ttu-id="66d8c-245">KnockoutJS-[http://knockoutjs.com/](http://knockoutjs.com/)</span><span class="sxs-lookup"><span data-stu-id="66d8c-245">KnockoutJS - [http://knockoutjs.com/](http://knockoutjs.com/)</span></span>
    
- <span data-ttu-id="66d8c-246">LINQ.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), o [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)</span><span class="sxs-lookup"><span data-stu-id="66d8c-246">Linq.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), or [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)</span></span>
    
<span data-ttu-id="66d8c-p118">La versione corrente di LinqJS non contiene il metodo ByHierarchy utilizzato nel codice precedente e interromperà il codice di struttura di spostamento. Per risolvere questo problema, aggiungere il metodo seguente al file Linq.js prima della riga "Flatten: funzione ()".</span><span class="sxs-lookup"><span data-stu-id="66d8c-p118">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code. To fix this, add the following method to the Linq.js file before the line "Flatten: function ()".</span></span>
  
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


