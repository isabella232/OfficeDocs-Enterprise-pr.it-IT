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
# <a name="navigation-options-for-sharepoint-online"></a>Opzioni di spostamento per SharePoint Online

In questo articolo viene descritto come migliorare i tempi di caricamento delle pagine per SharePoint Online mediante l'utilizzo di esplorazione gestita o lo spostamento basato sulla ricerca nella pubblicazione classica.
  
SharePoint Online con pubblicazione classica abilitata sono presenti due aree di spostamento; Struttura di spostamento globale e struttura di spostamento corrente.
  
Struttura di spostamento globale è il menu di spostamento superiore durante la struttura di spostamento corrente rappresenta la parte o una struttura di spostamento sinistra o verso destra nel contesto varia a seconda di configurazione di lingua e pagina master utilizzata.
  
Struttura di spostamento può impatto negativo sulle prestazioni per l'intero portale come spesso è configurato per l'utilizzo a livello di portale e pertanto è un importante elemento di un sito di SharePoint.
  
Struttura di spostamento non è l'opzione di esplorazione consigliato in SharePoint Online è stata progettata per una topologia locale con limitazione per motivi di sicurezza e questa struttura fa sì che le chiamate di un sovraccarico del server e influisce sulle prestazioni quando viene utilizzata.
  
Di progettazione è stato modificato con l'introduzione di siti di SharePoint moderno dove moderno dispone di una gerarchia di siti bidimensionale semplificata. Ciò è semplificato esplorazione con una gerarchia semplificata che ha eliminato problemi di prestazioni relative alla struttura di spostamento.
  
Sono disponibili due opzioni di spostamento della finestra principale di SharePoint, nonché un terzo, l'approccio personalizzato, basate sulla ricerca. In alternativa, opzione relativamente più comuni e una quarta consiste nel creare un Provider di spostamento personalizzato. Esaminare [le soluzioni di spostamento per i portali di SharePoint Online](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) per informazioni su un provider di spostamento personalizzato. 
  
Ogni opzione presenta vantaggi e gli svantaggi, come descritto nella tabella seguente.
  
|**Esplorazione strutturale**|**Esplorazione gestita**|**Esplorazione basata sulla ricerca**||**Provider di spostamento personalizzato**|
|:-----|:-----|:-----|:-----|:-----|
| Pro:  <br/>  Semplice da configurare  <br/>  Limitato per motivi di sicurezza  <br/>  Si aggiorna automaticamente man mano che i siti vengono aggiunti  <br/> | Pro:  <br/>  Facile da gestire  <br/>  Opzione consigliata  <br/> | Pro:  <br/>  Limitato per motivi di sicurezza  <br/>  Si aggiorna automaticamente man mano che i siti vengono aggiunti  <br/>  Tempo di caricamento rapido e struttura dell'esplorazione memorizzata nella cache  <br/> || Vantaggi:  <br/>    <br/>  Scelta più ampia / opzioni disponibili  <br/>  Caricamento rapido quando la memorizzazione nella cache viene utilizzato in modo corretto  <br/> |
| Contro:  <br/> **Scelta non consigliata** <br/> **Influisce sulle prestazioni** <br/> | Contro:  <br/>  Non si aggiorna automaticamente per riflettere la struttura del sito  <br/>  Influisce sulle prestazioni se è abilitata la rimozione di sicurezza  <br/> | Contro:  <br/>  Non è possibile ordinare facilmente i siti  <br/>  Richiede la personalizzazione della pagina master (necessarie competenze tecniche)  <br/> || Contro:  <br/>  Sviluppo personalizzato è obbligatorio  <br/>  Origine dati esterna / cache memorizzati è necessario ad esempio Azure  <br/> |
   
L'opzione più appropriata per il sito dipenderà alle specifiche esigenze di siti e le funzionalità tecniche. Se si ha familiarità con una pagina master personalizzata e alcune funzionalità nell'organizzazione per gestire le modifiche che possono verificarsi nella pagina master predefinita per SharePoint Online, l'opzione basate sulla ricerca genereranno un'esperienza utente ottimale. Se si desidera semplice metà strada tra la struttura di spostamento della casella e la ricerca, l'esplorazione gestita è un'opzione ottima. È possibile mantenere l'opzione di esplorazione gestita tramite la configurazione, non comporta i file di personalizzazione di codice e è significativamente più veloce rispetto della casella struttura di spostamento.
  
Semplificando la struttura globale del portale classica in modo analogo moderno, aiuta a con le prestazioni e scalabilità anche globali. Ciò significa che invece una singola raccolta siti con centinaia o migliaia di sedi (Web secondari), una soluzione migliore deve disporre di molte raccolte siti con poche siti secondari (Web secondari).
  
Questo sono disponibili ulteriori opzioni di implementazione della scalabilità per il servizio, consente di evitare la messa tutto il contenuto in un database di grande e infine maggiore flessibilità per lo spostamento e soprattutto sicurezza.
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>Utilizzo dell'esplorazione strutturale in SharePoint Online

Questa è la struttura di spostamento della casella utilizzato per impostazione predefinita ed è la soluzione più semplice ma è pertanto un compromesso prestazioni costosa. Non richiede alcuna personalizzazione e utente tecnico può inoltre possibile aggiungere elementi, nascondere gli elementi e gestire la struttura di spostamento dalla pagina delle impostazioni. Si tratta tuttavia true per l'esplorazione gestita in modo, si consiglia di utilizzare l'esplorazione gestita come che può anche essere facilmente gestiti e controllati anche.
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>Attivazione dell'esplorazione strutturale in SharePoint Online

Per illustrare come le prestazioni in una soluzione di SharePoint Online standard con struttura di spostamento e Mostra i siti secondari opzione attivato. Di seguito è una cattura di schermata impostazioni presenti nella pagina **Impostazioni sito** \> **struttura di spostamento**.
  
![Schermata che mostra i siti secondari](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>Analisi delle prestazioni dell'esplorazione strutturale in SharePoint Online

Per analizzare le prestazioni di una pagina di SharePoint utilizzare la scheda **Rete** degli strumenti di sviluppo F12 in Internet Explorer. 
  
![Schermata che mostra la scheda Rete degli strumenti di sviluppo F12](media/e2aed8af-0843-487a-8b68-4f5260a2685e.png)
  
Nella scheda **Rete**, fare clic nella pagina aspx in caricamento, quindi fare clic sulla scheda **Dettagli**. 
  
![Schermata che mostra la scheda dei dettagli](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)
  
Fare clic su **Intestazioni di risposta**.
  
![Schermata scheda Dettagli](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)
  
SharePoint restituisce alcune informazioni diagnostiche utili nelle intestazioni di risposta. Una delle più utili è **SPRequestDuration** che è il valore in millisecondi, del tempo che impiega una richiesta per essere elaborata sul server. 
  
Nella schermata seguente **Mostra i siti secondari** non è selezionata per la struttura di spostamento. Ciò significa che non vi è solo il collegamento di raccolta siti nel riquadro di spostamento globale: 
  
![Schermata che mostra i tempi di caricamento come durata richiesta](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)
  
Il tasto **SPRequestDuration** ha un valore di 245 millisecondi. Rappresenta il tempo impiegato per restituire la richiesta. Poiché esiste un solo elemento di spostamento nel sito, questo è un riscontro valido per modalità SharePoint Online esegue senza spostamento spessi. Nella schermata successiva viene illustrato l'aggiunta nei siti secondari su questa chiave. 
  
![Schermata che illustra una durata richiesta di 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)
  
L'aggiunta di siti secondari ha aumentato sensibilmente il tempo necessario per restituire la richiesta della pagina.
  
I vantaggi derivanti dall'utilizzo di esplorazione strutturata regolare è che si possono facilmente organizzare l'ordine, nascondere i siti, aggiungere pagine, i risultati vengono tagliati sicurezza e non è differiscono dalle pagine master supportate utilizzate in SharePoint Online.
  
## <a name="using-managed-navigation-and-managed-metadata-in-sharepoint-online"></a>Usare l'esplorazione gestita e i metadati gestiti di SharePoint Online

L'esplorazione gestita è un'altra opzione predefinita che è possibile utilizzare per ricreare lo stesso tipo di funzionalità dell'esplorazione strutturale.
  
Il vantaggio di utilizzo dei metadati gestiti è è molto più veloce per recuperare i dati rispetto all'utilizzo di contenuto da query per creare la struttura del sito. Anche se è che molto più rapidamente non è possibile alla protezione di limitare i risultati in modo se un utente non dispone dell'accesso a un determinato sito, il collegamento ancora mostrerà ma porterà a un messaggio di errore.
  
 **Come implementare l'esplorazione gestita e i risultati**
  
Esistono diversi articoli di TechNet sui dettagli dell'esplorazione gestita, ad esempio, vedere [Panoramica dell'esplorazione gestita in SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).
  
Per implementare l'esplorazione gestita, è necessario disporre di autorizzazioni di amministratore per l'archivio dei termini. Impostando termini con URL che corrispondono alla struttura di una raccolta di siti, è possibile utilizzare l'esplorazione gestita per sostituire l'esplorazione strutturale. Ad esempio:
  
![Schermata di esempio Subsite1](media/4155b4da-ccff-4e2a-92de-7803ac62982b.png)
  
L'esempio seguente mostra le prestazioni della struttura di spostamento complessa utilizzando l'esplorazione gestita.
  
![Schermata di esempio SPRequestDuration](media/72257528-0ec6-48b0-85a5-efeb7432db5b.png)
  
L'utilizzo dell'esplorazione gestita in modo coerente migliora le prestazioni rispetto all'approccio dell'esplorazione strutturale della Query contenuto.
  
## <a name="using-search-driven-client-side-scripting"></a>Utilizzo di script sul lato client basato sulla ricerca

Utilizzando la ricerca è possibile utilizzare gli indici sviluppati in background tramite la ricerca per indicizzazione continua. Ciò significa che non sono presenti query di contenuto pesante. I risultati della ricerca vengono recuperati dall'indice di ricerca e i risultati sono limitati per motivi di sicurezza. Ciò è più veloce rispetto all'utilizzo di query contenuto. Utilizzando la ricerca per l'esplorazione strutturale, soprattutto se si dispone di una struttura di siti complessa, è possibile velocizzare notevolmente tempi di caricamento delle pagine. Il principale vantaggio di questa esplorazione gestita è che è possibile beneficiare della limitazione per motivi di sicurezza.
  
Questo approccio implica la creazione di una pagina master personalizzata e la sostituzione del codice di spostamento predefinito con codice HTML personalizzato. Seguire questa procedura per sostituire il codice della struttura di spostamento nel file seattle.html.
  
In questo esempio, si verrà aprire il file seattle.html e sostituire l'intero elemento **id = "DeltaTopNavigation"** con il codice HTML personalizzato. 
  
 **Esempio: per sostituire il codice della struttura di spostamento predefinito in una pagina master**
  
1. Andare alla pagina **Impostazioni sito**. 
    
2. Aprire la raccolta di pagine master facendo clic su **Pagine master**.
    
3. Da qui è possibile spostarsi all'interno della raccolta e scaricare il file **seattle.master**.
    
4. Modificare il codice utilizzando un editor di testo ed eliminare il blocco di codice nella schermata seguente.
    
    ![Schermata del codice DeltaTopNavigation da eliminare](media/70db2cd2-660d-4e0d-9d5c-a5df331c73b4.png)
  
5. Rimuovere il codice tra il \<SharePoint:AjaxDelta id = "DeltaTopNavigation"\> e \<\SharePoint:AjaxDelta\> tags e sostituirlo con il frammento di codice seguente:
    
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

6. Sostituire l'URL nel caricamento dell'immagine tag di ancoraggio all'inizio, con un collegamento a un'immagine nella raccolta siti. Dopo aver apportato le modifiche, rinominare il file e quindi caricare nella raccolta pagine master. Verrà generato un nuovo file con estensione master.
    
7. In questo codice HTML è il markup di base che verrà popolato per i risultati della ricerca restituiti dal codice JavaScript. È necessario modificare il codice seguente per modificare il valore per il `var root = "site collection URL"` come illustrato nel frammento di seguito: 
    
  ```
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  ```

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

     $("li.level1").mouseover (funzione () { 
  
posizione var = $(this).position();
  
$(this).find("ul.level2").css ({larghezza: 100, sinistra: position.left + 10, dall'alto: 50});
    
     }) 
  
.MOUSEOUT (funzione () {
  
$(this).find("ul.level2").css ({sinistra:-99999 principali: 0});
  
});
  
$("li.level2").mouseover (funzione () {
  
posizione var = $(this).position();
  
console.log(JSON.stringify(Position));
  
$(this).find("ul.level3").css ({larghezza: 100, sinistra: position.left + 95, dall'alto: position.top});
    
     }) 
  
.MOUSEOUT (funzione () {
  
$(this).find("ul.level3").css ({sinistra:-99999 principali: 0});
  
});
    
    } _spBodyOnLoadFunctionNames.push("InitCustomNav");
    
    To summarize the code shown above in the jQuery **[$(document).ready]** function there is a **[viewModel]** object created and then the **[loadNavigationNodes()]** function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function **[queryRemoteInterface()]**. 
    
    **[QueryRemoteInterface()]** builds a request using the **[getRequest()]** function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties. This data is then parsed into the previously defined **[SPO.Models.NavigationNode]** objects which use Knockout.js to create observable properties for use by data binding the values into the HTML that we defined earlier. The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads. 
    
8. Successivamente, i risultati vengono assegnati alla matrice **[self.nodes]** e viene creata una gerarchia dagli oggetti utilizzando linq.js assegnazione l'output a una matrice **[self.heirarchy]**. Questa matrice è l'oggetto che viene associato al codice HTML. Questa operazione viene eseguita nella funzione **[toggleView()]** passando l'oggetto self-alla funzione **[ko.applyBinding()]** . In questo modo quindi la matrice di gerarchia per l'associazione ai HTML seguenti: 
    
  ```
  <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
  ```

    Infine, vengono aggiunti i gestori eventi per **[mouseenter]** e **[mouseexit]** per lo spostamento principale per gestire i menu a discesa sito secondario che viene eseguito nella funzione **[addEventsToElements()]** . 
    
    I risultati del riquadro di spostamento possono essere visualizzati nella schermata di seguito:
    
    ![Schermata dei risultati della struttura di spostamento](media/020d34d2-942a-431b-9b26-6d2c8a6fde30.png)
  
    Questo esempio di navigazione complessa in cui una nuova pagina si carica senza memorizzazione nella cache locale mostra che il tempo impiegato sul server è stato ridotto rispetto all'esplorazione strutturale predefinita per ottenere un risultato simile a quello dell'esplorazione gestita.
    
    ![Schermata di SPRequestDuration 301](media/307d7caf-e83a-40d9-a551-91d842521d03.png)
  
    Uno dei principali vantaggi di questo approccio è che con l'archiviazione locale HTML5, la struttura di spostamento è archiviata in locale per l'utente la volta successiva che carica la pagina.
    
Si ottengono miglioramenti delle prestazioni principali utilizzando l'API di ricerca per l'esplorazione strutturale; tuttavia, sono necessarie alcune capacità tecniche per eseguire e personalizzare questa funzionalità. Nell'esempio di implementazione, i siti vengono ordinati in base alla stessa stregua dell'esplorazione strutturale predefinita; in ordine alfabetico. Se si desidera deviare da questo ordine, diventa più complesso lo sviluppo e la manutenzione. Inoltre, questo approccio richiede di deviare dalle pagine master supportate. Se non viene mantenuta la pagina master personalizzata, il sito verrà escluso dagli aggiornamenti e dai miglioramenti che Microsoft apporta alle pagine master.
  
Nel codice precedente ha le dipendenze seguenti:
  
- jQuery-[http://jquery.com/](http://jquery.com/)
    
- KnockoutJS-[http://knockoutjs.com/](http://knockoutjs.com/)
    
- LINQ.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), o [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)
    
La versione corrente di LinqJS non contiene il metodo ByHierarchy utilizzato nel codice precedente e interromperà il codice di struttura di spostamento. Per risolvere questo problema, aggiungere il metodo seguente al file Linq.js prima della riga "Flatten: funzione ()".
  
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


