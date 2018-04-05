---
title: Configurare la ricerca di OneDrive per Business Multi-Geo
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Informazioni su come configurare la ricerca in un ambiente multi-geo.
ms.openlocfilehash: 5aa1e9eb189e00dbed8f575e88046b661341bf52
ms.sourcegitcommit: 21cc62118b78b76d16ef12e2c3eff2c0c789e3d0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/05/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="acdbf-103">Configurare la ricerca di OneDrive per Business Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="acdbf-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="acdbf-104">In un ambiente Multi-Geo SharePoint Online (SPO), un'organizzazione può avere un tenant di Office 365, ma archiviare il contenuto di SharePoint in più posizioni geografiche - una posizione centrale e uno o più satellitare geo percorsi.</span><span class="sxs-lookup"><span data-stu-id="acdbf-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="acdbf-p101">Ogni località geografica ha indice di ricerca e Centro ricerche. Quando un utente esegue la ricerca, la query viene disposta a tutti gli indici e i risultati restituiti vengono uniti.</span><span class="sxs-lookup"><span data-stu-id="acdbf-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="acdbf-p102">Ad esempio, un utente in un'unica posizione geografica può eseguire ricerche per contenuto archiviato in un'altra posizione geografica o per il contenuto in un sito di SharePoint che è limitato a una posizione geografica diversi. Se l'utente ha accesso a tale contenuto, ricerca verrà visualizzato il risultato.</span><span class="sxs-lookup"><span data-stu-id="acdbf-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="acdbf-109">Quale ricerca client funzioni correttamente in un ambiente Multi-Geo?</span><span class="sxs-lookup"><span data-stu-id="acdbf-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="acdbf-110">Questi client possono restituire risultati da tutti i percorsi geo:</span><span class="sxs-lookup"><span data-stu-id="acdbf-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="acdbf-111">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="acdbf-111">OneDrive for Business</span></span>

-   <span data-ttu-id="acdbf-112">Delve</span><span class="sxs-lookup"><span data-stu-id="acdbf-112">Delve</span></span>

-   <span data-ttu-id="acdbf-113">Home page di SharePoint</span><span class="sxs-lookup"><span data-stu-id="acdbf-113">The SharePoint home page</span></span>

-   <span data-ttu-id="acdbf-114">Centro ricerche</span><span class="sxs-lookup"><span data-stu-id="acdbf-114">The Search Center</span></span>

-   <span data-ttu-id="acdbf-115">Applicazioni di ricerca personalizzate che utilizzano l'API di ricerca di SharePoint</span><span class="sxs-lookup"><span data-stu-id="acdbf-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="acdbf-116">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="acdbf-116">OneDrive for Business</span></span>

<span data-ttu-id="acdbf-117">Come configurare l'ambiente Multi-Geo, gli utenti che la ricerca in OneDrive ottenere i risultati da tutti i percorsi geo.</span><span class="sxs-lookup"><span data-stu-id="acdbf-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="acdbf-118">Delve</span><span class="sxs-lookup"><span data-stu-id="acdbf-118">Delve</span></span>

<span data-ttu-id="acdbf-119">Come configurare l'ambiente Multi-Geo, gli utenti che la ricerca in Delve ottenere i risultati da tutti i percorsi geo.</span><span class="sxs-lookup"><span data-stu-id="acdbf-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="acdbf-p103">Il feed Delve e la scheda profilo vengono visualizzate solo le anteprime dei file vengono archiviati nella posizione **centrale** . Per i file archiviati in percorsi geo satellitari, l'icona per il tipo di file verrà visualizzato.</span><span class="sxs-lookup"><span data-stu-id="acdbf-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="acdbf-122">Home page di SharePoint</span><span class="sxs-lookup"><span data-stu-id="acdbf-122">The SharePoint home page</span></span>

<span data-ttu-id="acdbf-p104">Come configurare l'ambiente Multi-Geo, gli utenti visualizzeranno news, siti di recenti e seguiti da più posizioni geo nella loro home page di SharePoint. Se si utilizza la casella di ricerca nella home page di SharePoint, si otterranno risultati uniti da più posizioni geo.</span><span class="sxs-lookup"><span data-stu-id="acdbf-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="acdbf-125">Centro ricerche</span><span class="sxs-lookup"><span data-stu-id="acdbf-125">The Search Center</span></span>

<span data-ttu-id="acdbf-p105">Dopo la Multi-Geo environment è stata impostata, ogni Centro ricerche continua a Mostra solo i risultati dalla posizione geografica. Gli amministratori devono [modificare le impostazioni di ogni Centro ricerche](#_Set_up_a_1) per ottenere i risultati da tutti i percorsi geo. Gli utenti che la ricerca nel sito Centro ricerche in un secondo momento, ottenere i risultati da tutti i percorsi geo.</span><span class="sxs-lookup"><span data-stu-id="acdbf-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="acdbf-129">Applicazioni di ricerca personalizzate</span><span class="sxs-lookup"><span data-stu-id="acdbf-129">Custom search applications</span></span>

<span data-ttu-id="acdbf-p106">Come di consueto, applicazioni di ricerca personalizzate interagiscono con gli indici di ricerca tramite l'API REST di ricerca di SharePoint esistente. Per ottenere i risultati da alcuni o tutti i percorsi di livello geografico, l'applicazione deve essere [chiamata l'API e includere i nuovi parametri di query Multi-Geo](#_Get_custom_search) nella richiesta. In questo modo viene attivata una ventola fuori la query per tutti i percorsi geo.</span><span class="sxs-lookup"><span data-stu-id="acdbf-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="acdbf-133">Che cos'è diverse informazioni sulla ricerca in un ambiente Multi-Geo?</span><span class="sxs-lookup"><span data-stu-id="acdbf-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="acdbf-134">Alcune funzionalità di ricerca è possibile acquisire familiarità con, funziona in modo diverso in un ambiente Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="acdbf-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="acdbf-135"><strong>Caratteristica</strong></span><span class="sxs-lookup"><span data-stu-id="acdbf-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="acdbf-136"><strong>Come funziona</strong></span><span class="sxs-lookup"><span data-stu-id="acdbf-136"><strong>How does it work</strong></span></span></th>
<th align="left"><span data-ttu-id="acdbf-137"><strong>Soluzione</strong></span><span class="sxs-lookup"><span data-stu-id="acdbf-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="acdbf-138">Risultati alzati di livello</span><span class="sxs-lookup"><span data-stu-id="acdbf-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="acdbf-p107">È possibile creare le regole di query con risultati alzati di livello a diversi livelli: per l'intero tenant, per una raccolta siti o per un sito. In un ambiente Multi-Geo, definire i risultati alzati di livello a livello di <strong>tenant</strong> per alzare di livello i risultati ai siti Centro ricerche in <strong>tutte le</strong> posizioni geo. Se è <strong>solo</strong> scopo di ottenere risultati nel Centro ricerche nella posizione geografica della raccolta siti o del sito, definire i risultati a livello di <strong>raccolta siti</strong> o del <strong>sito</strong> .</span><span class="sxs-lookup"><span data-stu-id="acdbf-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="acdbf-142">Se non è necessario risultati alzati di livello diversi per ogni località geografica, ad esempio regole per i viaggi, è consigliabile definire alzati di livello i risultati a livello di tenant.</span><span class="sxs-lookup"><span data-stu-id="acdbf-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="acdbf-143">Criteri di affinamento ricerca</span><span class="sxs-lookup"><span data-stu-id="acdbf-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="acdbf-p108">Ricerca restituisce i criteri di affinamento ricerca da tutti i percorsi geografica di un tenant e aggrega loro. L'aggregazione è tenterà, il che significa che il numero di criteri di affinamento ricerca potrebbe non essere precisi al 100%. Per la maggior parte degli scenari basate sulla ricerca, questa accuratezza è sufficiente.</span><span class="sxs-lookup"><span data-stu-id="acdbf-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient.</span></span></td>
<td align="left"><span data-ttu-id="acdbf-147">Per le applicazioni basate sulla ricerca che dipendono dal livello di completezza criteri di affinamento ricerca, eseguire una query ogni località geografica in modo indipendente senza utilizzare Multi-Geo fanout.</span><span class="sxs-lookup"><span data-stu-id="acdbf-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="acdbf-148">Ricerca multi-Geo non supporta il bucket dinamico per criteri di affinamento ricerca numerici.</span><span class="sxs-lookup"><span data-stu-id="acdbf-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="acdbf-149">Utilizzare il <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">parametro "Discretize"</a> di criteri di affinamento ricerca numerici.</span><span class="sxs-lookup"><span data-stu-id="acdbf-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="acdbf-150">ID documento</span><span class="sxs-lookup"><span data-stu-id="acdbf-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="acdbf-151">Se si sta sviluppando un'applicazione basata sulla ricerca dipende dal documento ID, si noti che gli ID documento in un ambiente Multi-Geo non sono univoci tra diverse ubicazioni geo, sono univoci per ogni località geografica.</span><span class="sxs-lookup"><span data-stu-id="acdbf-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="acdbf-p109">È stata aggiunta una colonna che identifica la posizione geografica. Utilizzare questa colonna per garantire l'univocità. Questa colonna è denominata "GeoLocationSource".</span><span class="sxs-lookup"><span data-stu-id="acdbf-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="acdbf-155">Numero di risultati</span><span class="sxs-lookup"><span data-stu-id="acdbf-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="acdbf-156">Pagina dei risultati della ricerca vengono mostrati i risultati combinati dalle posizioni geo, ma non è possibile pagina oltre 500 risultati.</span><span class="sxs-lookup"><span data-stu-id="acdbf-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="acdbf-157">Cosa non è supportata per la ricerca in un ambiente Multi-Geo?</span><span class="sxs-lookup"><span data-stu-id="acdbf-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="acdbf-158">Alcune delle funzionalità di ricerca è possibile acquisire familiarità con, non sono supportate in un ambiente Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="acdbf-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="acdbf-159"><strong>Funzionalità di ricerca</strong></span><span class="sxs-lookup"><span data-stu-id="acdbf-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="acdbf-160"><strong>Nota</strong></span><span class="sxs-lookup"><span data-stu-id="acdbf-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="acdbf-161">Autenticazione di App</span><span class="sxs-lookup"><span data-stu-id="acdbf-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="acdbf-162">App sola autenticazione (accesso privilegiato da servizi) non è supportata in ricerca Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="acdbf-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="acdbf-163">Utenti guest</span><span class="sxs-lookup"><span data-stu-id="acdbf-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="acdbf-164">Gli utenti guest risultati solo dalla posizione geografica esegue la ricerca da.</span><span class="sxs-lookup"><span data-stu-id="acdbf-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="acdbf-165">Funzionamento consente ricerche in un ambiente Multi-Geo?</span><span class="sxs-lookup"><span data-stu-id="acdbf-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="acdbf-166">**Tutti** i client di ricerca utilizzano l'API REST di ricerca di SharePoint esistente per interagire con gli indici di ricerca.</span><span class="sxs-lookup"><span data-stu-id="acdbf-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>
<img src="media/configure-search-for-multi-geo_image1-1.png" />

1. <span data-ttu-id="acdbf-167">Un client di ricerca chiama l'endpoint REST di ricerca con la proprietà query EnableMultiGeoSearch = true.</span><span class="sxs-lookup"><span data-stu-id="acdbf-167">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="acdbf-168">La query viene inviata a tutti i percorsi geo nel tenant.</span><span class="sxs-lookup"><span data-stu-id="acdbf-168">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="acdbf-169">Risultati di ricerca ogni località geografica vengono uniti e classificati.</span><span class="sxs-lookup"><span data-stu-id="acdbf-169">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="acdbf-170">Il client ottiene risultati di ricerca unificata.</span><span class="sxs-lookup"><span data-stu-id="acdbf-170">The client gets unified search results.</span></span>



<span data-ttu-id="acdbf-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Si noti che è non unire i risultati della ricerca fino a quando non risultati abbiamo ricevuto da tutti i percorsi di livello geografico. Ciò significa che le ricerche Multi-Geo latenza aggiuntiva rispetto alle ricerche in un ambiente con una sola geo posizione.</span><span class="sxs-lookup"><span data-stu-id="acdbf-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don’t merge the search results until we’ve received results from all the geo locations. This means that Multi-Geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="acdbf-173">Ottenere un centro ricerche per visualizzare i risultati da tutti i percorsi geo</span><span class="sxs-lookup"><span data-stu-id="acdbf-173">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="acdbf-174">È necessario impostare ogni verticale singolarmente ogni Centro ricerche ha diversi verticali.</span><span class="sxs-lookup"><span data-stu-id="acdbf-174">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="acdbf-175">Assicurarsi di eseguire la procedura seguente con un account che dispone dell'autorizzazione per modificare la pagina dei risultati di ricerca e la Web Part risultati di ricerca.</span><span class="sxs-lookup"><span data-stu-id="acdbf-175">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="acdbf-176">Passare alla pagina dei risultati della ricerca (vedere l' [elenco](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) di ricerca pagine dei risultati)</span><span class="sxs-lookup"><span data-stu-id="acdbf-176">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="acdbf-p111">Selezionare il verticale di configurare, fare clic sull'icona ingranaggio **Impostazioni** nell'angolo in alto a destra e quindi fare clic su **Modifica pagina**. Verrà visualizzata la pagina dei risultati della ricerca in modalità di modifica.</span><span class="sxs-lookup"><span data-stu-id="acdbf-p111">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

     ![](media/configure-search-for-multi-geo_image2.png)
1.  <span data-ttu-id="acdbf-p112">Nella Web Part risultati di ricerca spostare il puntatore verso l'alto a destra della Web Part fare clic sulla freccia e quindi fare clic su **Modifica Web Part** dal menu. Riquadro degli strumenti della Web Part risultati ricerca verrà visualizzata sotto la barra multifunzione nella parte superiore destra della pagina.![](media/configure-search-for-multi-geo_image3.png)</span><span class="sxs-lookup"><span data-stu-id="acdbf-p112">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu. The Search Results Web Part tool pane opens under the ribbon in the top right of the page. ![](media/configure-search-for-multi-geo_image3.png)</span></span>

1.  <span data-ttu-id="acdbf-181">Nel riquadro strumenti Web Part, nella sezione **Impostazioni** in **risultati controllano le impostazioni**, selezionare **Mostra Multi-Geo risultati** per ottenere la Web Part risultati di ricerca per visualizzare i risultati da tutti i percorsi geo.</span><span class="sxs-lookup"><span data-stu-id="acdbf-181">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="acdbf-182">Fare clic su **OK** per salvare le modifiche e chiudere il riquadro strumenti della Web Part.</span><span class="sxs-lookup"><span data-stu-id="acdbf-182">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="acdbf-183">Verificare le modifiche apportate a Web Part risultati di ricerca fare clic su **Archiviazione** nella scheda pagina del menu principale.</span><span class="sxs-lookup"><span data-stu-id="acdbf-183">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="acdbf-184">Pubblicare le modifiche utilizzando il collegamento contenuto nella nota nella parte superiore della pagina.</span><span class="sxs-lookup"><span data-stu-id="acdbf-184">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="acdbf-185">Ottenere le applicazioni di ricerca personalizzate da visualizzare i risultati di alcuni o tutti i percorsi geo</span><span class="sxs-lookup"><span data-stu-id="acdbf-185">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="acdbf-p113">Applicazioni di ricerca personalizzate ottenere i risultati da posizioni geo tutte o alcune, specificando i parametri di query con la richiesta per l'API REST di ricerca di SharePoint. In base ai parametri di query, la query viene disposta in tutti i percorsi geo o in alcuni percorsi geo. Ad esempio, se è necessario solo per un sottoinsieme delle posizioni geo per trovare le informazioni rilevanti di query, è possibile controllare la ventola fuori solo a queste. Se la richiesta ha esito positivo, l'API REST di ricerca di SharePoint restituisce i dati di risposta.</span><span class="sxs-lookup"><span data-stu-id="acdbf-p113">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="acdbf-190">Parametri di query</span><span class="sxs-lookup"><span data-stu-id="acdbf-190">Query parameters</span></span>

<span data-ttu-id="acdbf-p114">EnableMultiGeoSearch - questo è un valore Boolean che specifica se la query deve disposta per gli indici delle altre posizioni geo del tenant Multi-Geo. Impostare su **true** per estendere le query. **false** per non ventaglio la query. Il valore predefinito è **false**. Se non si include questo parametro, la query viene disposta **non** in altre posizioni geo. Se si utilizza il parametro in un ambiente che non è più Geo, il parametro viene ignorato.</span><span class="sxs-lookup"><span data-stu-id="acdbf-p114">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="acdbf-p115">TipoClient - questa è una stringa. Immettere un nome di client univoci per ogni applicazione di ricerca. Se non si include questo parametro, la query viene disposta **non** in altre posizioni geo.</span><span class="sxs-lookup"><span data-stu-id="acdbf-p115">ClientType - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="acdbf-p116">MultiGeoSearchConfiguration - si tratta di un elenco facoltativo di quali geo percorsi Multi-Geo tenant per ventaglio la query su quando **EnableMultiGeoSearch** è **true**. Se si non include questo parametro o lasciare vuoto, la query viene disposta in tutti i percorsi geo. Per ogni località geografica, immettere gli elementi seguenti nel formato JSON:</span><span class="sxs-lookup"><span data-stu-id="acdbf-p116">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="acdbf-202">Elemento</span><span class="sxs-lookup"><span data-stu-id="acdbf-202">Item</span></span></th>
<th align="left"><span data-ttu-id="acdbf-203">Descrizione</span><span class="sxs-lookup"><span data-stu-id="acdbf-203">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="acdbf-204">PercorsoDati</span><span class="sxs-lookup"><span data-stu-id="acdbf-204">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="acdbf-205">Posizione geografica, ad esempio nomi.</span><span class="sxs-lookup"><span data-stu-id="acdbf-205">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="acdbf-206">EndPoint</span><span class="sxs-lookup"><span data-stu-id="acdbf-206">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="acdbf-207">L'endpoint a cui connettersi, ad esempiohttps://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="acdbf-207">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="acdbf-208">SourceId</span><span class="sxs-lookup"><span data-stu-id="acdbf-208">SourceId</span></span></td>
<td align="left"><span data-ttu-id="acdbf-209">GUID dell'origine dei risultati, ad esempio B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span><span class="sxs-lookup"><span data-stu-id="acdbf-209">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="acdbf-p117">Se si omette PercorsoDati o EndPoint oppure un PercorsoDati viene duplicato, la richiesta ha esito negativo. [È possibile ottenere informazioni sul punto finale della località geografica del tenant utilizzando Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span><span class="sxs-lookup"><span data-stu-id="acdbf-p117">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="acdbf-212">Dati di risposta</span><span class="sxs-lookup"><span data-stu-id="acdbf-212">Response data</span></span>

<span data-ttu-id="acdbf-p118">MultiGeoSearchStatus – questa è una proprietà che restituisce l'API di ricerca di SharePoint in risposta alla richiesta. Il valore della proprietà corrisponde a una stringa e vengono fornite le informazioni seguenti relative ai risultati che restituisce l'API di ricerca di SharePoint:</span><span class="sxs-lookup"><span data-stu-id="acdbf-p118">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="acdbf-215">Valore</span><span class="sxs-lookup"><span data-stu-id="acdbf-215">Value</span></span></th>
<th align="left"><span data-ttu-id="acdbf-216">Descrizione</span><span class="sxs-lookup"><span data-stu-id="acdbf-216">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="acdbf-217">Completo</span><span class="sxs-lookup"><span data-stu-id="acdbf-217">Full</span></span></td>
<td align="left"><span data-ttu-id="acdbf-218">Completo dei risultati di <strong>tutti</strong> i percorsi geo.</span><span class="sxs-lookup"><span data-stu-id="acdbf-218">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="acdbf-219">Parziale</span><span class="sxs-lookup"><span data-stu-id="acdbf-219">Partial</span></span></td>
<td align="left"><span data-ttu-id="acdbf-p119">Risultati parziali da uno o più percorsi geo. I risultati sono incompleti a causa di un errore temporaneo.</span><span class="sxs-lookup"><span data-stu-id="acdbf-p119">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="acdbf-222">Utilizzo del servizio REST di query</span><span class="sxs-lookup"><span data-stu-id="acdbf-222">Query using the REST service</span></span>

<span data-ttu-id="acdbf-p120">Con una richiesta GET, specificare i parametri di query nell'URL. Con una richiesta POST è passare i parametri di query nel corpo in formato JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="acdbf-p120">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>

#### <a name="request-headers"></a><span data-ttu-id="acdbf-225">Intestazioni delle richieste</span><span class="sxs-lookup"><span data-stu-id="acdbf-225">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="acdbf-226">Nome</span><span class="sxs-lookup"><span data-stu-id="acdbf-226">Name</span></span></th>
<th align="left"><span data-ttu-id="acdbf-227">Valore</span><span class="sxs-lookup"><span data-stu-id="acdbf-227">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="acdbf-228">Content-Type</span><span class="sxs-lookup"><span data-stu-id="acdbf-228">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="acdbf-229">applicazione/json; odata = verbose</span><span class="sxs-lookup"><span data-stu-id="acdbf-229">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="acdbf-230">Esempio di convocazione GET che viene disposta in **tutti i** percorsi geo</span><span class="sxs-lookup"><span data-stu-id="acdbf-230">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="acdbf-231">https:// \<tenant\>/\_api/ricerca/query?querytext = proprietà & "sharepoint" = 'EnableMultiGeoSearch:true' & TipoClient =' personale\_client\_id'</span><span class="sxs-lookup"><span data-stu-id="acdbf-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="acdbf-232">Esempio di convocazione GET a ventaglio **alcune** posizioni geo</span><span class="sxs-lookup"><span data-stu-id="acdbf-232">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="acdbf-233">https:// <tenant>/_api/search/query?querytext = 'sito' & TipoClient = 'my_client_id' & proprietà ='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration: [{PercorsoDati\:"Nome"\,Endpoint\:"https\: contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{PercorsoDati\:"Può"\,Endpoint\:" https\://contosoCAN.sharepoint-df.com "}]'</span><span class="sxs-lookup"><span data-stu-id="acdbf-233">https:// <tenant>/_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\:"NAM"\,Endpoint\:"https\://contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"CAN"\,Endpoint\:"https\://contosoCAN.sharepoint-df.com"}]'</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="acdbf-234">Esempio di convocazione di POST che viene disposta in **tutti i** percorsi geo</span><span class="sxs-lookup"><span data-stu-id="acdbf-234">Sample POST request that’s fanned out to **all** geo locations</span></span>

    {
        "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="acdbf-235">Esempio di convocazione di POST che viene disposta in **alcuni** percorsi geo</span><span class="sxs-lookup"><span data-stu-id="acdbf-235">Sample POST request that’s fanned out to **some** geo locations</span></span>


    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }

### <a name="query-using-csom"></a><span data-ttu-id="acdbf-236">Query utilizza CSOM</span><span class="sxs-lookup"><span data-stu-id="acdbf-236">Query using CSOM</span></span>

<span data-ttu-id="acdbf-237">Ecco una query di esempio CSOM che viene disposta in **tutti i** percorsi geo:</span><span class="sxs-lookup"><span data-stu-id="acdbf-237">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

