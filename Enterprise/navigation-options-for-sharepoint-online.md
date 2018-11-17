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
# <a name="navigation-options-for-sharepoint-online"></a>Opzioni di spostamento per SharePoint Online

In questo articolo vengono descritti lo spostamento opzioni siti con pubblicazione di SharePoint abilitati in SharePoint Online. La configurazione della struttura di spostamento e la scelta influisce sulle notevolmente le prestazioni e scalabilità dei siti di SharePoint Online.

## <a name="overview"></a>Panoramica

Configurazione del provider di spostamento può ridurre notevolmente le prestazioni per l'intero sito e un'attenta valutazione deve essere prese per selezionare un provider di spostamento e la configurazione ridimensiona in modo efficace per i requisiti di un sito di SharePoint. Esistono due provider di spostamento della finestra, nonché le implementazioni di spostamento personalizzato.

La prima opzione, [**esplorazione gestita (metadati)**](#using-managed-navigation-and-metadata-in-sharepoint-online), è consigliabile e tra le opzioni predefinite in SharePoint Online, Tuttavia, si consiglia la disabilitazione di limitazione per motivi di sicurezza se non necessario. Limitazione per motivi di sicurezza è abilitata come impostazione sicura per impostazione predefinita per il provider di spostamento; Tuttavia, molti siti non richiedono l'overhead di sicurezza di limitazione per motivi poiché gli elementi di spostamento sono spesso coerenti per tutti gli utenti del sito. Con la configurazione consigliata per disabilitare la limitazione per motivi di sicurezza, il provider di spostamento non richiede l'enumerazione struttura del sito e altamente scalabile con un impatto sulle prestazioni accettabili.

La seconda opzione, la [**struttura di spostamento**](#using-structural-navigation-in-sharepoint-online), **non un'opzione di spostamento consigliato in SharePoint Online**. Questo provider di spostamento è stato progettato per il supporto di SharePoint Online è limitato una topologia locale. Mentre offre alcuni altri set di funzionalità e altre opzioni di spostamento, queste caratteristiche, tra cui limitazione per motivi di sicurezza e sull'enumerazione struttura del sito, ha un costo di chiamate un sovraccarico del server e le prestazioni e scalabilità impatti quando viene utilizzata. Siti che utilizzano structed spostamento che utilizzano risorse eccessive possono essere soggetto di limitazione.

Oltre ai provider di spostamento della finestra, molti clienti hanno implementato con successo implementazioni di spostamento personalizzato alternativi. Una classe comune delle implementazioni di spostamento personalizzato prestare modelli di progettazione viene eseguito il rendering client che archiviano una cache locale di nodi. Vedere **[creazione di script sul lato client basate sulla ricerca](#using-search-driven-client-side-scripting)** in questo articolo.

Tali provider spostamento hanno due vantaggi principali: 
- In genere con cui lavorano anche progettazioni di pagina risponde.
- Sono estremamente scalabili e ad alte prestazioni dal momento che è possibile eseguire il rendering con alcun costo della risorsa (e l'aggiornamento in background dopo un intervallo di timeout). 
- Tali provider spostamento può recuperare dati di spostamento con diverse strategie, compresi tra configurazioni statiche semplice per vari provider di dati dinamico. 

Un esempio di un provider di dati consiste nell'utilizzare una **struttura di spostamento basata sulla ricerca**, che consente la flessibilità per l'enumerazione dei nodi di spostamento e la gestione efficiente motivi di sicurezza. 

Sono disponibili altre opzioni più comuni per creare **provider di spostamento personalizzato**. Esaminare [le soluzioni di spostamento per i portali di SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) per ulteriori informazioni sulla creazione di un provider di spostamento personalizzato.
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>Opzioni di spostamento vantaggi e svantaggi di SharePoint Online

Nella tabella seguente sono riepilogati i vantaggi e gli svantaggi di ogni opzione. 


|Esplorazione gestita  |Esplorazione strutturale  |Esplorazione basata sulla ricerca  |Provider di spostamento personalizzato  |
|---------|---------|---------|---------|
|Pro:<br/><br/>Facile da gestire<br/>Opzione consigliata<br/>     |Pro:<br/><br/>Semplice da configurare<br/>Per motivi di sicurezza<br/>Viene aggiornato automaticamente con l'aggiunta di contenuto<br/>|Vantaggi:<br/><br/>Per motivi di sicurezza<br/>Si aggiorna automaticamente man mano che i siti vengono aggiunti<br/>Tempo di caricamento rapido e struttura dell'esplorazione memorizzata nella cache<br/>|Vantaggi:<br/><br/>Più ampia scelta delle opzioni disponibili<br/>Caricamento rapido quando la memorizzazione nella cache viene utilizzato in modo corretto<br/>Molte opzioni funzionano bene con struttura delle pagine risponde<br/>|
|Contro:<br/><br/>Non si aggiorna automaticamente per riflettere la struttura del sito<br/>Influisce sulle prestazioni se è abilitata la rimozione di sicurezza<br/>|Contro:<br/><br/>**Scelta non consigliata**<br/>**Influisce sulle prestazioni e scalabilità**<br/>**Soggetti a limitazione delle richieste**<br/>|Contro:<br/><br/>Non è possibile ordinare facilmente i siti<br/>Richiede la personalizzazione della pagina master (necessarie competenze tecniche)<br/>|Contro:<br/><br/>Sviluppo personalizzato è obbligatorio<br/>Origine dati esterna / cache memorizzati è necessario ad esempio Azure<br/>|

L'opzione più appropriata per il sito dipenderà alle specifiche esigenze di siti e le funzionalità tecniche. Se si desidera che un provider di spostamento della casella scalabile, spostamento gestite con limitazione per motivi di sicurezza disabilitato è un'opzione ottima. 

È possibile mantenere l'opzione di esplorazione gestita tramite la configurazione, non implicano l'utilizzo di file di personalizzazione di codice ed è notevolmente più veloce di struttura di spostamento. Se si richiedono la limitazione per motivi di sicurezza e ha familiarità con una pagina master personalizzata e alcune funzionalità nell'organizzazione per gestire le modifiche che possono verificarsi nella pagina master predefinita per SharePoint Online, l'opzione basate sulla ricerca potrebbe verificarsi un migliore esperienza utente. Se si dispone di più complesse, un provider di spostamento personalizzato può essere la scelta ideale. Struttura di spostamento non è consigliato.

Infine, è importante tenere presente che SharePoint viene aggiunta di provider di spostamento aggiuntivi e le funzionalità per sfruttare una gerarchia del sito più bidimensionale e un modello hub and spoke con i siti hub SharePoint moderne architetture del sito SharePoint. In questo modo molti scenari da raggiungere che non richiedono l'utilizzo della caratteristica Pubblicazione di SharePoint e le configurazioni di spostamento sono ottimizzate per la scalabilità e latenza in SharePoint Online. Si noti che l'applicazione lo stesso principio - semplificando la struttura complessiva del sito di pubblicazione di SharePoint a una struttura più lineare, aiuta a con le prestazioni complessive e proporzioni anche. Ciò significa che anziché una singola raccolta siti con centinaia di siti (Web secondari), una soluzione migliore deve disporre di molte raccolte siti con poche siti secondari (Web secondari).


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>Utilizzo di esplorazione gestita e metadati in SharePoint Online

Esplorazione gestita è un'altra opzione di predefinite che è possibile utilizzare per ricreare la maggior parte delle stesse funzionalità struttura di spostamento. Metadati gestiti possono essere configurati per disporre di limitazione per motivi di sicurezza abilitate o disabilitate. Nelle configurazioni con limitazione per motivi di sicurezza disabilitato, esplorazione gestita è relativamente efficiente in caso di caricamento tutti i collegamenti di spostamento con un numero di chiamate server costante. Abilitazione della sicurezza limitazione per motivi, tuttavia, Nega alcuni dei vantaggi dell'esplorazione gestita e clienti possono scegliere di esplorare una delle soluzioni di spostamento personalizzata per ottimizzare le prestazioni e scalabilità.

Numero di siti non richiedono una limitazione per motivi di sicurezza, come la struttura di spostamento è spesso coerenza per tutti gli utenti del sito. Se la rimozione di sicurezza è disattivata e viene aggiunto un collegamento alla struttura non tutti gli utenti hanno accesso a, il collegamento indicherà che ancora ma porterà a un messaggio di accesso negato. Non esiste alcun rischio di accesso non intenzionale al contenuto.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>Come implementare l'esplorazione gestita e i risultati

Esistono diversi articoli su Docs.Microsoft.com sui dettagli dell'esplorazione gestita, ad esempio, vedere [Panoramica dell'esplorazione gestita in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).

Per implementare esplorazione gestita, è impostare termini gli URL corrispondente alla struttura di spostamento del sito. Esplorazione gestita può anche essere curated manualmente per sostituire struttura di spostamento in molti casi. Per esempio:

![Struttura dei siti SharePoint Online](media/SPONavOptionsListOfSites.png)

L'esempio seguente mostra le prestazioni della struttura di spostamento complessa utilizzando l'esplorazione gestita.

![Prestazioni di navigazione complesse utilizzando esplorazione gestita](media/SPONavOptionsComplexNavPerf.png)

Utilizzo dell'esplorazione gestita in modo coerente migliora le prestazioni rispetto al metodo struttura di spostamento.
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>Utilizzo dell'esplorazione strutturale in SharePoint Online

Questa è la struttura di spostamento della casella utilizzato per impostazione predefinita ed è la soluzione più semplice ma è pertanto un compromesso prestazioni costosa. Non richiede alcuna personalizzazione e utente tecnico può inoltre possibile aggiungere elementi, nascondere gli elementi e gestire la struttura di spostamento dalla pagina delle impostazioni. Si tratta tuttavia anche true per l'esplorazione gestita in modo, si consiglia di utilizzare l'esplorazione gestita come che è possibile inoltre facilmente gestiti e controllati anche con un miglioramento delle prestazioni.

![Struttura di spostamento con i siti secondari Mostra selezionata](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>Attivazione dell'esplorazione strutturale in SharePoint Online

Per illustrare come le prestazioni in una soluzione di SharePoint Online standard con struttura di spostamento e Mostra i siti secondari opzione attivato. Di seguito è riportata una schermata delle impostazioni presenti nella pagina **Impostazioni sito** \> **struttura di spostamento**.
  
![Schermata che mostra i siti secondari](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>Analisi delle prestazioni dell'esplorazione strutturale in SharePoint Online

Per analizzare le prestazioni di una pagina di SharePoint, utilizzare la scheda di **rete** F12 gli strumenti di sviluppo in Internet Explorer. 
  
![Schermata che mostra la scheda Rete degli strumenti di sviluppo F12](media/SPONavOptionsNetworks.png)
  
1. Nella scheda **Rete**, fare clic nella pagina aspx in caricamento, quindi fare clic sulla scheda **Dettagli**.<br/> ![Schermata che mostra la scheda dei dettagli](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)<br/>
2. Fare clic su **Intestazioni di risposta**. <br/>![Schermata scheda Dettagli](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)<br/>SharePoint restituisce alcune informazioni utili per la diagnostiche delle intestazioni di risposta. 
3. Uno dei componenti maggiormente utili di informazioni è **SPRequestDuration** è il valore espresso in millisecondi, di una richiesta di tempo richiesto per l'elaborazione sul server. Nella schermata seguente **Mostra i siti secondari** è selezionata per la struttura di spostamento. Ciò significa che non vi è solo il collegamento di raccolta siti nel riquadro di spostamento globale:<br/>![Schermata che mostra i tempi di caricamento come durata richiesta](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)<br/>
4. Il tasto **SPRequestDuration** ha un valore di 245 millisecondi. Rappresenta il tempo impiegato per restituire la richiesta. Poiché esiste un solo elemento di spostamento nel sito, questo è un riscontro valido per modalità SharePoint Online esegue senza spostamento spessi. Nella schermata successiva viene illustrato l'aggiunta nei siti secondari su questa chiave.<br/>![Schermata che illustra una durata richiesta di 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)<br/>
  
Aggiunta di siti secondari è aumentata in modo significativo il tempo che necessario per restituire la richiesta della pagina per il sito di esempio relativamente semplice. Gerarchie di siti complessi, incluse le pagine nella struttura di spostamento e configurazione e altre opzioni di topologia possono aumentare notevolmente ulteriormente tale impatto.

## <a name="using-search-driven-client-side-scripting"></a>Utilizzo di script sul lato client basato sulla ricerca

Utilizzo di ricerca è possibile utilizzare gli indici vengono sviluppati in background tramite ricerca per indicizzazione continua. I risultati della ricerca vengono estratti dall'indice di ricerca e i risultati vengono tagliati sicurezza. Si tratta in genere più provider di spostamento della casella rapido durante la limitazione per motivi di protezione è necessario. Utilizzo della ricerca per la struttura di spostamento, in particolare se si dispone di una struttura del sito complessa, velocizzare il caricamento notevolmente ora della pagina. Il vantaggio principale di questo oggetto su esplorazione gestita è vantaggiosa limitazione per motivi di sicurezza.

Questo approccio prevede la creazione di una pagina master personalizzata e sostituendo il codice di struttura di spostamento della casella con HTML personalizzati. Eseguire la procedura descritta nell'esempio seguente per sostituire il codice di struttura di spostamento nel file `seattle.html`. In questo esempio, si aprirà la `seattle.html` di file e sostituire l'intero elemento `id=”DeltaTopNavigation”` con il codice HTML personalizzato.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>Esempio: Sostituire il codice di struttura di spostamento della finestra in una pagina master

1.  Andare alla pagina Impostazioni sito.
2.  Aprire la raccolta di pagine master facendo clic su **Pagine master**.
3.  Da qui è possibile spostarsi tra la raccolta e scaricare il file `seattle.master`.
4.  Modificare il codice utilizzando un editor di testo ed eliminare il blocco di codice nella schermata seguente.<br/>![Eliminare il blocco di codice riportato](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. Rimuovere il codice tra il `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` e `<\SharePoint:AjaxDelta>` tags e sostituirlo con il frammento di codice seguente:<br/>

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
6. Sostituire l'URL nel caricamento dell'immagine tag di ancoraggio all'inizio, con un collegamento a un'immagine nella raccolta siti. Dopo aver apportato le modifiche, rinominare il file e quindi caricare nella raccolta pagine master. Verrà generato un nuovo file con estensione master.<br/>
7. In questo codice HTML è il markup di base che verrà popolato per i risultati della ricerca restituiti dal codice JavaScript. È necessario modificare il codice per modificare il valore di var radice = "URL della raccolta siti" come illustrato nel frammento di seguito:<br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. I risultati vengono assegnati alla matrice self.nodes e viene creata una gerarchia dagli oggetti utilizzando linq.js assegnazione l'output a una matrice self.hierarchy. Questa matrice è l'oggetto che viene associato al codice HTML. Questa operazione viene eseguita nella funzione toggleView() passando l'oggetto self-alla funzione ko.applyBinding().<br/>In questo modo quindi la matrice di gerarchia per l'associazione ai HTML seguenti:<br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

I gestori eventi per `mouseenter` e `mouseexit` vengono aggiunti al riquadro di spostamento principale per gestire i menu a discesa sito secondario che viene effettuata nel `addEventsToElements()` funzione.

In questo esempio di navigazione complesse, una pagina nuova carico senza mostrato nella cache locale il tempo impiegato per il server è stato eliminato verso il basso da benchmark struttura di spostamento per ottenere un risultato simile come il metodo di esplorazione gestita.

### <a name="about-the-javascript-file"></a>Sul file JavaScript...

Di seguito è riportato l'intero file JavaScript:

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

Per riassumere il codice indicato nella precedente il `jQuery $(document).ready` funzione non esiste un `viewModel object` creato e quindi la `loadNavigationNodes()` funzione per tale oggetto viene chiamato. Questa funzione viene caricato eseguire una gerarchia di spostamento compilata precedentemente memorizzata nell'archivio locale HTML5 del browser del client o chiama la funzione `queryRemoteInterface()`.

`QueryRemoteInterface()`Crea una richiesta tramite il `getRequest()` funzione con il parametro di query definito in precedenza nello script e quindi restituisce dati dal server. Questi dati sono fondamentalmente una matrice di tutti i siti della raccolta siti rappresentati come oggetti di trasferimento dati diverse proprietà. 

Questi dati viene quindi analizzati in definita in precedenza `SPO.Models.NavigationNode` gli oggetti che utilizzano `Knockout.js` per creare proprietà presenza da utilizzare per i valori di tale associazione a HTML definita in precedenza. 

Gli oggetti vengono quindi inseriti in una matrice dei risultati. Questa matrice viene analizzata in JSON utilizzando foratura e memorizzata nell'archivio locale del browser per migliorare le prestazioni nella pagina future carichi.

### <a name="benefits-of-this-approach"></a>Vantaggi di questo approccio

Uno dei vantaggi principale di [questo metodo](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) è che utilizzando HTML5 archiviazione locale, la struttura di spostamento viene archiviato in locale per l'utente al successivo che momento del caricamento della pagina. È possibile ottenere miglioramenti delle prestazioni principali di utilizzare l'API di ricerca per la struttura di spostamento; Tuttavia, ha alcune funzionalità tecniche per l'esecuzione e personalizzare questa funzionalità. 

Nell' [esempio di implementazione](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), i siti vengono ordinati allo stesso modo di casella struttura di spostamento; ordine alfabetico. Se si desidera diversi da quest'ordine, potrebbe risultare più complessa sviluppare e gestire. Inoltre, questo approccio richiede diversi dalle pagine master supportate. Se la pagina master personalizzata non viene mantenuta, il sito verrà perdere: aggiornamenti e i miglioramenti che Microsoft consente alle pagine master.

Il [precedente codice](#about-the-javascript-file) ha le dipendenze seguenti:

- jQuery-http://jquery.com/
- KnockoutJS-http://knockoutjs.com/
- LINQ.js - http://linqjs.codeplex.com/, o github.com/neuecc/linq.js

La versione corrente di LinqJS non contiene il metodo ByHierarchy utilizzato nel codice precedente e interromperà il codice di struttura di spostamento. Per risolvere questo problema, aggiungere il metodo seguente al file Linq.js prima della riga `Flatten: function ()`.

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
  
## <a name="related-topics"></a>Argomenti correlati

[Panoramica dell'esplorazione gestita in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

