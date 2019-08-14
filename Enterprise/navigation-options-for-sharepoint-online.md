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
# <a name="navigation-options-for-sharepoint-online"></a>Opzioni di spostamento per SharePoint Online

In questo articolo vengono descritti i siti delle opzioni di spostamento con la pubblicazione di SharePoint abilitata in SharePoint Online. La scelta e la configurazione della struttura di spostamento incidono in modo significativo sulle prestazioni e sulla scalabilità dei siti in SharePoint Online.

## <a name="overview"></a>Panoramica

La configurazione del provider di spostamento può influire in modo significativo sulle prestazioni per l'intero sito e è necessario prendere in considerazione attentamente la scelta di un provider di spostamento e una configurazione in grado di ridimensionare efficacemente i requisiti di un sito di SharePoint. Sono disponibili due provider di spostamento fuori dalla casella, nonché implementazioni di spostamento personalizzate.

La prima opzione, lo [**spostamento gestito (metadati)**](#using-managed-navigation-and-metadata-in-sharepoint-online)è consigliata ed è una delle opzioni predefinite in SharePoint Online. Tuttavia, si consiglia di disabilitare la limitazione di sicurezza a meno che non sia necessario. La limitazione di sicurezza è abilitata come impostazione di protezione per il provider di spostamento. Tuttavia, molti siti non richiedono il sovraccarico della limitazione di sicurezza poiché gli elementi di spostamento spesso sono coerenti per tutti gli utenti del sito. Con la configurazione consigliata per disabilitare la limitazione di sicurezza, questo provider di spostamento non richiede l'enumerazione della struttura del sito ed è altamente scalabile con un impatto sulle prestazioni accettabile.

La seconda opzione, ovvero [**struttura di spostamento strutturale**](#using-structural-navigation-in-sharepoint-online), **non è un'opzione di spostamento consigliata in SharePoint Online**. Questo provider di spostamento è stato creato per una topologia locale con supporto limitato in SharePoint Online. Anche se fornisce alcuni set di funzionalità aggiuntivi rispetto ad altre opzioni di spostamento, queste funzionalità, tra cui la limitazione della sicurezza e l'enumerazione della struttura del sito, sono a costo di eccessive chiamate ai server e incidono sulla scalabilità e sulle prestazioni quando vengono utilizzate. I siti che utilizzano l'esplorazione strutturata che consumano risorse eccessive possono essere soggetti a limitazione.

Oltre ai provider di spostamento fuori campo, molti clienti hanno implementato con successo implementazioni di spostamento personalizzate alternative. Una classe comune di implementazioni di spostamento personalizzate abbraccia modelli di progettazione con rendering client che archiviano una cache locale dei nodi di spostamento. Per ulteriori informazioni, vedere **[script sul fianco client](#using-search-driven-client-side-scripting)** basato sulla ricerca in questo articolo.

Questi provider di spostamento hanno un paio di vantaggi principali: 
- In genere funzionano bene con i progetti di pagina reattivi.
- Sono estremamente scalabili e performanti perché è possibile eseguire il rendering senza costi di risorse (e aggiornare in background dopo un timeout). 
- Tali provider di spostamento possono recuperare i dati di spostamento utilizzando diverse strategie, che vanno dalle configurazioni statiche semplici ai vari provider di dati dinamici. 

Un esempio di provider di dati prevede l'utilizzo di una struttura di **spostamento basata sulla ricerca**, che consente la flessibilità per l'enumerazione dei nodi di spostamento e la gestione efficiente del taglio di sicurezza. 

Sono disponibili altre opzioni popolari per la creazione di **provider di spostamento personalizzati**. Leggere le [soluzioni di navigazione per i portali di SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) per ulteriori informazioni sulla creazione di un provider di spostamento personalizzato.
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>Vantaggi e svantaggi delle opzioni di spostamento di SharePoint Online

Nella tabella seguente sono riepilogati i vantaggi e gli svantaggi di ogni opzione. 


|Esplorazione gestita  |Esplorazione strutturale  |Esplorazione basata sulla ricerca  |Provider di spostamento personalizzato  |
|---------|---------|---------|---------|
|Professionisti<br/><br/>Facile da gestire<br/>Opzione consigliata<br/>     |Professionisti<br/><br/>Semplice da configurare<br/>Protezione ritagliata<br/>Viene aggiornato automaticamente con l'aggiunta di contenuto<br/>|Professionisti<br/><br/>Protezione ritagliata<br/>Si aggiorna automaticamente man mano che i siti vengono aggiunti<br/>Tempo di caricamento rapido e struttura dell'esplorazione memorizzata nella cache<br/>|Professionisti<br/><br/>Scelta più ampia di opzioni disponibili<br/>Caricamento veloce quando la memorizzazione nella cache viene utilizzata correttamente<br/>Molte opzioni funzionano bene con la progettazione delle pagine reattive<br/>|
|Contro<br/><br/>Non si aggiorna automaticamente per riflettere la struttura del sito<br/>Impatto delle prestazioni se la limitazione di sicurezza è abilitata<br/>|Contro<br/><br/>**Non consigliato**<br/>**Impatto sulle prestazioni e sulla scalabilità**<br/>**Soggette a limitazione**<br/>|Contro<br/><br/>Non è possibile ordinare facilmente i siti<br/>Richiede la personalizzazione della pagina master (necessarie competenze tecniche)<br/>|Contro<br/><br/>Lo sviluppo personalizzato è obbligatorio<br/>L'origine dati esterna/cache memorizzata è necessaria ad esempio Azure<br/>|

L'opzione più appropriata per il sito dipende dai requisiti del sito e dalle proprie capacità tecniche. Se si desidera un provider di navigazione esterno scalabile, quindi l'esplorazione gestita con la limitazione della sicurezza disabilitata è un'ottima opzione.

L'opzione di spostamento gestito può essere mantenuta tramite la configurazione, non comporta file di personalizzazione del codice ed è significativamente più veloce rispetto alla struttura di spostamento strutturale. Se si richiede la riduzione della sicurezza e si ha dimestichezza con una pagina master personalizzata e si dispone di una certa funzionalità nell'organizzazione per gestire le modifiche che possono verificarsi nella pagina master predefinita per SharePoint Online, l'opzione basata sulla ricerca potrebbe produrre una migliore esperienza utente. Se si dispone di requisiti più complessi, è possibile che il provider di spostamento personalizzato sia la scelta giusta. La struttura di spostamento strutturale non è consigliata.

Infine, è importante tenere presente che SharePoint aggiunge ulteriori provider di spostamento e funzionalità per le moderne architetture di siti di SharePoint, sfruttando una gerarchia di siti più appiattita e un modello hub-and-spoke con i siti hub di SharePoint. In questo modo è possibile ottenere numerosi scenari che non richiedono l'utilizzo della caratteristica di pubblicazione di SharePoint e queste configurazioni di spostamento sono ottimizzate per la scalabilità e la latenza all'interno di SharePoint Online. Si noti che l'applicazione dello stesso principio: semplificare la struttura complessiva del sito di pubblicazione di SharePoint in una struttura più piatta, spesso contribuisce anche alle prestazioni generali e alla scalabilità. Ciò significa che, invece di disporre di una singola raccolta siti con centinaia di Site (Web secondari), un approccio migliore consiste nell'avere molte raccolte siti con pochissimi sottositi (Web secondari).


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>Utilizzo dell'esplorazione e dei metadati gestiti in SharePoint Online

L'esplorazione gestita è un'altra opzione che è possibile utilizzare per ricreare la maggior parte delle stesse funzionalità della struttura di spostamento strutturale. I metadati gestiti possono essere configurati in modo da abilitare o disabilitare la limitazione di sicurezza. Una volta configurata con la limitazione della sicurezza disabilitata, l'esplorazione gestita è piuttosto efficiente poiché carica tutti i collegamenti di spostamento con un numero costante di chiamate del server. L'abilitazione della limitazione della sicurezza, tuttavia, nega alcuni dei vantaggi dell'esplorazione gestita e i clienti possono scegliere di esplorare una delle soluzioni di spostamento personalizzate per ottimizzare le prestazioni e la scalabilità.

Molti siti non richiedono la limitazione della sicurezza, in quanto la struttura di spostamento è spesso coerente per tutti gli utenti del sito. Se la limitazione di sicurezza è disabilitata e viene aggiunto un collegamento alla struttura di spostamento a cui non è consentito l'accesso a tutti gli utenti, il collegamento verrà comunque visualizzato, ma comporterà un messaggio di accesso negato. Non vi è alcun rischio di accesso involontario al contenuto.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>Come implementare l'esplorazione gestita e i risultati

Sono disponibili numerosi articoli su Docs.Microsoft.com per informazioni dettagliate sull'esplorazione gestita, ad esempio, vedere [Overview of Managed Navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).

Per implementare l'esplorazione gestita, è necessario configurare i termini con gli URL corrispondenti alla struttura di spostamento del sito. L'esplorazione gestita può anche essere curata manualmente per sostituire la struttura di spostamento strutturale in molti casi. Ad esempio:

![Struttura del sito di SharePoint Online](media/SPONavOptionsListOfSites.png)

L'esempio seguente mostra le prestazioni della struttura di spostamento complessa utilizzando l'esplorazione gestita.

![Prestazioni dell'esplorazione complessa tramite l'esplorazione gestita](media/SPONavOptionsComplexNavPerf.png)

L'utilizzo dell'esplorazione gestita migliora costantemente le prestazioni rispetto all'approccio di spostamento strutturale.
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>Utilizzo dell'esplorazione strutturale in SharePoint Online

Questa è la struttura di spostamento fuori campo utilizzata per impostazione predefinita ed è la soluzione più semplice, ma come tale ha un costo elevato di prestazioni. Non richiede alcuna personalizzazione e un utente non tecnico può anche aggiungere facilmente elementi, nascondere gli elementi e gestire la struttura di spostamento dalla pagina impostazioni. Questo è tuttavia valido anche per l'esplorazione gestita, pertanto è consigliabile utilizzare l'esplorazione gestita in modo che possa essere anche facilmente gestita e controllata e con prestazioni migliorate.

![Struttura di spostamento strutturale con i siti secondari visualizzati selezionati](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>Attivazione dell'esplorazione strutturale in SharePoint Online

Per illustrare le prestazioni in una soluzione SharePoint Online con esplorazione strutturale e opzione per mostrare i siti secondari attivate. Di seguito è riportata una schermata delle impostazioni disponibili nella pagina di **spostamento** **delle impostazioni** \> del sito.
  
![Schermata che mostra i siti secondari](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>Analisi delle prestazioni dell'esplorazione strutturale in SharePoint Online

Per analizzare le prestazioni di una pagina di SharePoint, utilizzare la scheda **rete** degli strumenti di sviluppo F12 in Internet Explorer. 
  
![Schermata che mostra la scheda Rete degli strumenti di sviluppo F12](media/SPONavOptionsNetworks.png)
  
1. Nella scheda **Rete**, fare clic nella pagina aspx in caricamento, quindi fare clic sulla scheda **Dettagli**.<br/> ![Schermata che mostra la scheda dei dettagli](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)<br/>
2. Fare clic su **Intestazioni di risposta**. <br/>![Schermata scheda Dettagli](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)<br/>SharePoint restituisce alcune informazioni diagnostiche utili nelle intestazioni di risposta. 
3. Una delle informazioni più utili è **SPRequestDuration** , ovvero il valore, in millisecondi, della durata della richiesta di elaborazione sul server. Nella schermata seguente l'opzione **Mostra i siti secondari** non è selezionata per l'esplorazione strutturale. Questo significa che è presente solo il collegamento della raccolta di siti nel riquadro di esplorazione globale:<br/>![Schermata che mostra i tempi di caricamento come durata richiesta](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)<br/>
4. La chiave **SPRequestDuration** presenta un valore di 245 millisecondi. Questo valore rappresenta il tempo necessario per restituire la richiesta. Poiché esiste un solo elemento di spostamento nel sito, questo è un valido riferimento per il modo in cui si comporta SharePoint Online senza spostamento intenso. Nella schermata successiva viene mostrato il modo in cui l'aggiunta nei siti secondari influisce su questa chiave.<br/>![Schermata che illustra una durata richiesta di 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)<br/>
  
L'aggiunta dei siti secondari ha aumentato significativamente il tempo necessario per restituire la richiesta di pagina per questo sito di esempio relativamente semplice. Le gerarchie di siti complesse, incluse le pagine in navigazione e altre opzioni di configurazione e topologia, possono aumentare drasticamente ulteriormente questo impatto.

## <a name="using-search-driven-client-side-scripting"></a>Utilizzo di script sul lato client basato sulla ricerca

Utilizzando la ricerca è possibile utilizzare gli indici sviluppati in background tramite la ricerca per indicizzazione continua. I risultati della ricerca vengono recuperati dall'indice di ricerca e i risultati sono limitati per motivi di sicurezza. Questo è in genere più veloce rispetto ai provider di spostamento esterno alla casella quando è richiesta la limitazione della sicurezza. Utilizzando la ricerca per l'esplorazione strutturale, soprattutto se si dispone di una struttura di siti complessa, è possibile velocizzare notevolmente tempi di caricamento delle pagine. Il principale vantaggio di questa esplorazione gestita è che è possibile beneficiare della limitazione per motivi di sicurezza.

Questo approccio implica la creazione di una pagina master personalizzata e la sostituzione del codice di spostamento predefinito con codice HTML personalizzato. Seguire questa procedura illustrata nell'esempio seguente per sostituire il codice di spostamento nel file `seattle.html`. In questo esempio viene aperto il `seattle.html` file e sostituito l'intero elemento `id=”DeltaTopNavigation”` con codice HTML personalizzato.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>Esempio: sostituire il codice di spostamento fuori dalla casella in una pagina master

1.  Andare alla pagina Impostazioni sito.
2.  Aprire la raccolta di pagine master facendo clic su **Pagine master**.
3.  Da qui è possibile passare alla raccolta e scaricare il file `seattle.master`.
4.  Modificare il codice utilizzando un editor di testo ed eliminare il blocco di codice nella schermata seguente.<br/>![Eliminare il blocco di codice visualizzato](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. Rimuovere il codice tra i `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` tag `<\SharePoint:AjaxDelta>` e e sostituirlo con il seguente frammento:<br/>

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
6. Sostituire l'URL nel tag Anchor dell'immagine di caricamento all'inizio, con un collegamento a un'immagine di caricamento nella raccolta siti. Dopo aver apportato le modifiche, rinominare il file, quindi caricarlo nella raccolta di pagine master. Ciò genera un nuovo file con estensione master.<br/>
7. Questo codice HTML è il codice di base che verrà precompilato dai risultati della ricerca restituiti dal codice JavaScript. Sarà necessario modificare il codice per modificare il valore di var root = "URL della raccolta siti", come illustrato nel seguente frammento:<br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. I risultati vengono assegnati alla matrice self. Nodes e una gerarchia è costituita dagli oggetti tramite LINQ. js che assegnano l'output a una matrice self. Hierarchy. Questa matrice è l'oggetto in cui è associato il codice HTML. Questa operazione viene eseguita nella funzione toggleView() passando l'oggetto utente alla funzione ko.applyBinding().<br/>Quindi, in questo modo la matrice di gerarchia va associata al codice HTML seguente:<br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

I gestori eventi per `mouseenter` e `mouseexit` vengono aggiunti all'esplorazione di livello principale per gestire i menu a discesa dei siti secondari, che vengono eseguiti nella `addEventsToElements()` funzione.

Nell'esempio di esplorazione complessa, un caricamento di pagina aggiornato senza la memorizzazione nella cache locale indica che il tempo trascorso nel server è stato ridotto dall'esplorazione strutturale di benchmark per ottenere un risultato simile a quello dell'approccio di spostamento gestito.

### <a name="about-the-javascript-file"></a>Informazioni sul file JavaScript...

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

Per riepilogare il codice sopra riportato nella `jQuery $(document).ready` funzione viene `viewModel object` creata e quindi viene chiamata la `loadNavigationNodes()` funzione su quell'oggetto. Questa funzione carica la gerarchia di spostamento precedentemente creata memorizzata nell'archiviazione locale di HTML5 del browser client o chiama la funzione `queryRemoteInterface()`.

`QueryRemoteInterface()`Compila una richiesta utilizzando la `getRequest()` funzione con il parametro di query definito in precedenza nello script e quindi restituisce i dati dal server. Questi dati sono sostanzialmente una matrice di tutti i siti nella raccolta di siti rappresentati come oggetti di trasferimento dei dati con alcune proprietà. 

Questi dati vengono quindi analizzati negli oggetti definiti `SPO.Models.NavigationNode` in precedenza che utilizzano `Knockout.js` per creare proprietà osservabili per l'utilizzo da parte dei dati per l'associazione dei valori nel codice HTML definito in precedenza. 

Gli oggetti vengono quindi inseriti in una matrice di risultati. Questa matrice viene analizzata in JSON utilizzando Knockout e memorizzata nell'archivio locale del browser per migliorare le prestazioni su caricamenti di pagina futuri.

### <a name="benefits-of-this-approach"></a>Vantaggi di questo approccio

Uno dei principali vantaggi di [questo approccio](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) consiste nel fatto che tramite l'archiviazione locale di HTML5 la struttura di spostamento viene archiviata localmente per l'utente al successivo caricamento della pagina. Si ottengono miglioramenti delle prestazioni principali utilizzando l'API di ricerca per l'esplorazione strutturale; tuttavia, sono necessarie alcune capacità tecniche per eseguire e personalizzare questa funzionalità. 

Nell' [implementazione di esempio](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), i siti vengono ordinati in modo analogo a quello della struttura di spostamento strutturale fuori campo. ordine alfabetico. Se si desidera deviare da questo ordine, diventa più complesso lo sviluppo e la manutenzione. Inoltre, questo approccio richiede di deviare dalle pagine master supportate. Se non viene mantenuta la pagina master personalizzata, il sito verrà escluso dagli aggiornamenti e dai miglioramenti che Microsoft apporta alle pagine master.

Il [codice sopra](#about-the-javascript-file) riportato presenta le dipendenze seguenti:

- jQueryhttp://jquery.com/
- KnockoutJS -http://knockoutjs.com/
- LINQ. js- http://linqjs.codeplex.com/o github.com/neuecc/LINQ.js

La versione corrente di LinqJS non contiene il metodo ByHierarchy utilizzato nel codice precedente e interrompe il codice di spostamento. Per risolvere il cosa, aggiungere il metodo seguente al file LINQ. js prima della riga `Flatten: function ()`.

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

