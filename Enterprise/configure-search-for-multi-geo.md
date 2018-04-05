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
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a>Configurare la ricerca di OneDrive per Business Multi-Geo

In un ambiente Multi-Geo SharePoint Online (SPO), un'organizzazione può avere un tenant di Office 365, ma archiviare il contenuto di SharePoint in più posizioni geografiche - una posizione centrale e uno o più satellitare geo percorsi.

Ogni località geografica ha indice di ricerca e Centro ricerche. Quando un utente esegue la ricerca, la query viene disposta a tutti gli indici e i risultati restituiti vengono uniti.

Ad esempio, un utente in un'unica posizione geografica può eseguire ricerche per contenuto archiviato in un'altra posizione geografica o per il contenuto in un sito di SharePoint che è limitato a una posizione geografica diversi. Se l'utente ha accesso a tale contenuto, ricerca verrà visualizzato il risultato.

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a>Quale ricerca client funzioni correttamente in un ambiente Multi-Geo?

Questi client possono restituire risultati da tutti i percorsi geo:

-   OneDrive for Business

-   Delve

-   Home page di SharePoint

-   Centro ricerche

-   Applicazioni di ricerca personalizzate che utilizzano l'API di ricerca di SharePoint

### <a name="onedrive-for-business"></a>OneDrive for Business

Come configurare l'ambiente Multi-Geo, gli utenti che la ricerca in OneDrive ottenere i risultati da tutti i percorsi geo.

### <a name="delve"></a>Delve

Come configurare l'ambiente Multi-Geo, gli utenti che la ricerca in Delve ottenere i risultati da tutti i percorsi geo.

Il feed Delve e la scheda profilo vengono visualizzate solo le anteprime dei file vengono archiviati nella posizione **centrale** . Per i file archiviati in percorsi geo satellitari, l'icona per il tipo di file verrà visualizzato.

### <a name="the-sharepoint-home-page"></a>Home page di SharePoint

Come configurare l'ambiente Multi-Geo, gli utenti visualizzeranno news, siti di recenti e seguiti da più posizioni geo nella loro home page di SharePoint. Se si utilizza la casella di ricerca nella home page di SharePoint, si otterranno risultati uniti da più posizioni geo.

### <a name="the-search-center"></a>Centro ricerche

Dopo la Multi-Geo environment è stata impostata, ogni Centro ricerche continua a Mostra solo i risultati dalla posizione geografica. Gli amministratori devono [modificare le impostazioni di ogni Centro ricerche](#_Set_up_a_1) per ottenere i risultati da tutti i percorsi geo. Gli utenti che la ricerca nel sito Centro ricerche in un secondo momento, ottenere i risultati da tutti i percorsi geo.

### <a name="custom-search-applications"></a>Applicazioni di ricerca personalizzate

Come di consueto, applicazioni di ricerca personalizzate interagiscono con gli indici di ricerca tramite l'API REST di ricerca di SharePoint esistente. Per ottenere i risultati da alcuni o tutti i percorsi di livello geografico, l'applicazione deve essere [chiamata l'API e includere i nuovi parametri di query Multi-Geo](#_Get_custom_search) nella richiesta. In questo modo viene attivata una ventola fuori la query per tutti i percorsi geo.

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a>Che cos'è diverse informazioni sulla ricerca in un ambiente Multi-Geo?

Alcune funzionalità di ricerca è possibile acquisire familiarità con, funziona in modo diverso in un ambiente Multi-Geo.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Caratteristica</strong></th>
<th align="left"><strong>Come funziona</strong></th>
<th align="left"><strong>Soluzione</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Risultati alzati di livello</td>
<td align="left">È possibile creare le regole di query con risultati alzati di livello a diversi livelli: per l'intero tenant, per una raccolta siti o per un sito. In un ambiente Multi-Geo, definire i risultati alzati di livello a livello di <strong>tenant</strong> per alzare di livello i risultati ai siti Centro ricerche in <strong>tutte le</strong> posizioni geo. Se è <strong>solo</strong> scopo di ottenere risultati nel Centro ricerche nella posizione geografica della raccolta siti o del sito, definire i risultati a livello di <strong>raccolta siti</strong> o del <strong>sito</strong> .</td>
<td align="left">Se non è necessario risultati alzati di livello diversi per ogni località geografica, ad esempio regole per i viaggi, è consigliabile definire alzati di livello i risultati a livello di tenant.</td>
</tr>
<tr class="even">
<td align="left">Criteri di affinamento ricerca</td>
<td align="left">Ricerca restituisce i criteri di affinamento ricerca da tutti i percorsi geografica di un tenant e aggrega loro. L'aggregazione è tenterà, il che significa che il numero di criteri di affinamento ricerca potrebbe non essere precisi al 100%. Per la maggior parte degli scenari basate sulla ricerca, questa accuratezza è sufficiente.</td>
<td align="left">Per le applicazioni basate sulla ricerca che dipendono dal livello di completezza criteri di affinamento ricerca, eseguire una query ogni località geografica in modo indipendente senza utilizzare Multi-Geo fanout.</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left">Ricerca multi-Geo non supporta il bucket dinamico per criteri di affinamento ricerca numerici.</td>
<td align="left">Utilizzare il <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">parametro "Discretize"</a> di criteri di affinamento ricerca numerici.</td>
</tr>
<tr class="even">
<td align="left">ID documento</td>
<td align="left">Se si sta sviluppando un'applicazione basata sulla ricerca dipende dal documento ID, si noti che gli ID documento in un ambiente Multi-Geo non sono univoci tra diverse ubicazioni geo, sono univoci per ogni località geografica.</td>
<td align="left">È stata aggiunta una colonna che identifica la posizione geografica. Utilizzare questa colonna per garantire l'univocità. Questa colonna è denominata "GeoLocationSource".</td>
</tr>
<tr class="odd">
<td align="left">Numero di risultati</td>
<td align="left">Pagina dei risultati della ricerca vengono mostrati i risultati combinati dalle posizioni geo, ma non è possibile pagina oltre 500 risultati.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a>Cosa non è supportata per la ricerca in un ambiente Multi-Geo?

Alcune delle funzionalità di ricerca è possibile acquisire familiarità con, non sono supportate in un ambiente Multi-Geo.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Funzionalità di ricerca</strong></th>
<th align="left"><strong>Nota</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Autenticazione di App</td>
<td align="left">App sola autenticazione (accesso privilegiato da servizi) non è supportata in ricerca Multi-Geo.</td>
</tr>
<tr class="even">
<td align="left">Utenti guest</td>
<td align="left">Gli utenti guest risultati solo dalla posizione geografica esegue la ricerca da.</td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a>Funzionamento consente ricerche in un ambiente Multi-Geo?

**Tutti** i client di ricerca utilizzano l'API REST di ricerca di SharePoint esistente per interagire con gli indici di ricerca.
<img src="media/configure-search-for-multi-geo_image1-1.png" />

1. Un client di ricerca chiama l'endpoint REST di ricerca con la proprietà query EnableMultiGeoSearch = true.
2. La query viene inviata a tutti i percorsi geo nel tenant.
3. Risultati di ricerca ogni località geografica vengono uniti e classificati.
4. Il client ottiene risultati di ricerca unificata.



<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Si noti che è non unire i risultati della ricerca fino a quando non risultati abbiamo ricevuto da tutti i percorsi di livello geografico. Ciò significa che le ricerche Multi-Geo latenza aggiuntiva rispetto alle ricerche in un ambiente con una sola geo posizione.

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a>Ottenere un centro ricerche per visualizzare i risultati da tutti i percorsi geo

È necessario impostare ogni verticale singolarmente ogni Centro ricerche ha diversi verticali.

1.  Assicurarsi di eseguire la procedura seguente con un account che dispone dell'autorizzazione per modificare la pagina dei risultati di ricerca e la Web Part risultati di ricerca.

2.  Passare alla pagina dei risultati della ricerca (vedere l' [elenco](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) di ricerca pagine dei risultati)

3.  Selezionare il verticale di configurare, fare clic sull'icona ingranaggio **Impostazioni** nell'angolo in alto a destra e quindi fare clic su **Modifica pagina**. Verrà visualizzata la pagina dei risultati della ricerca in modalità di modifica.

     ![](media/configure-search-for-multi-geo_image2.png)
1.  Nella Web Part risultati di ricerca spostare il puntatore verso l'alto a destra della Web Part fare clic sulla freccia e quindi fare clic su **Modifica Web Part** dal menu. Riquadro degli strumenti della Web Part risultati ricerca verrà visualizzata sotto la barra multifunzione nella parte superiore destra della pagina.![](media/configure-search-for-multi-geo_image3.png)

1.  Nel riquadro strumenti Web Part, nella sezione **Impostazioni** in **risultati controllano le impostazioni**, selezionare **Mostra Multi-Geo risultati** per ottenere la Web Part risultati di ricerca per visualizzare i risultati da tutti i percorsi geo.

2.  Fare clic su **OK** per salvare le modifiche e chiudere il riquadro strumenti della Web Part.

3.  Verificare le modifiche apportate a Web Part risultati di ricerca fare clic su **Archiviazione** nella scheda pagina del menu principale.

4.  Pubblicare le modifiche utilizzando il collegamento contenuto nella nota nella parte superiore della pagina.

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a>Ottenere le applicazioni di ricerca personalizzate da visualizzare i risultati di alcuni o tutti i percorsi geo

Applicazioni di ricerca personalizzate ottenere i risultati da posizioni geo tutte o alcune, specificando i parametri di query con la richiesta per l'API REST di ricerca di SharePoint. In base ai parametri di query, la query viene disposta in tutti i percorsi geo o in alcuni percorsi geo. Ad esempio, se è necessario solo per un sottoinsieme delle posizioni geo per trovare le informazioni rilevanti di query, è possibile controllare la ventola fuori solo a queste. Se la richiesta ha esito positivo, l'API REST di ricerca di SharePoint restituisce i dati di risposta.

### <a name="query-parameters"></a>Parametri di query

EnableMultiGeoSearch - questo è un valore Boolean che specifica se la query deve disposta per gli indici delle altre posizioni geo del tenant Multi-Geo. Impostare su **true** per estendere le query. **false** per non ventaglio la query. Il valore predefinito è **false**. Se non si include questo parametro, la query viene disposta **non** in altre posizioni geo. Se si utilizza il parametro in un ambiente che non è più Geo, il parametro viene ignorato.

TipoClient - questa è una stringa. Immettere un nome di client univoci per ogni applicazione di ricerca. Se non si include questo parametro, la query viene disposta **non** in altre posizioni geo.

MultiGeoSearchConfiguration - si tratta di un elenco facoltativo di quali geo percorsi Multi-Geo tenant per ventaglio la query su quando **EnableMultiGeoSearch** è **true**. Se si non include questo parametro o lasciare vuoto, la query viene disposta in tutti i percorsi geo. Per ogni località geografica, immettere gli elementi seguenti nel formato JSON:

<table>
<thead>
<tr class="header">
<th align="left">Elemento</th>
<th align="left">Descrizione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">PercorsoDati</td>
<td align="left">Posizione geografica, ad esempio nomi.</td>
</tr>
<tr class="even">
<td align="left">EndPoint</td>
<td align="left">L'endpoint a cui connettersi, ad esempiohttps://contoso.sharepoint.com</td>
</tr>
<tr class="odd">
<td align="left">SourceId</td>
<td align="left">GUID dell'origine dei risultati, ad esempio B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</td>
</tr>
</tbody>
</table>

Se si omette PercorsoDati o EndPoint oppure un PercorsoDati viene duplicato, la richiesta ha esito negativo. [È possibile ottenere informazioni sul punto finale della località geografica del tenant utilizzando Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).

### <a name="response-data"></a>Dati di risposta

MultiGeoSearchStatus – questa è una proprietà che restituisce l'API di ricerca di SharePoint in risposta alla richiesta. Il valore della proprietà corrisponde a una stringa e vengono fornite le informazioni seguenti relative ai risultati che restituisce l'API di ricerca di SharePoint:

<table>
<thead>
<tr class="header">
<th align="left">Valore</th>
<th align="left">Descrizione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Completo</td>
<td align="left">Completo dei risultati di <strong>tutti</strong> i percorsi geo.</td>
</tr>
<tr class="even">
<td align="left">Parziale</td>
<td align="left">Risultati parziali da uno o più percorsi geo. I risultati sono incompleti a causa di un errore temporaneo.</td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a>Utilizzo del servizio REST di query

Con una richiesta GET, specificare i parametri di query nell'URL. Con una richiesta POST è passare i parametri di query nel corpo in formato JavaScript Object Notation (JSON).

#### <a name="request-headers"></a>Intestazioni delle richieste

<table>
<thead>
<tr class="header">
<th align="left">Nome</th>
<th align="left">Valore</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Content-Type</td>
<td align="left">applicazione/json; odata = verbose</td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a>Esempio di convocazione GET che viene disposta in **tutti i** percorsi geo

https:// \<tenant\>/\_api/ricerca/query?querytext = proprietà & "sharepoint" = 'EnableMultiGeoSearch:true' & TipoClient =' personale\_client\_id'

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a>Esempio di convocazione GET a ventaglio **alcune** posizioni geo

https:// <tenant>/_api/search/query?querytext = 'sito' & TipoClient = 'my_client_id' & proprietà ='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration: [{PercorsoDati\:"Nome"\,Endpoint\:"https\: contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{PercorsoDati\:"Può"\,Endpoint\:" https\://contosoCAN.sharepoint-df.com "}]'

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a>Esempio di convocazione di POST che viene disposta in **tutti i** percorsi geo

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


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a>Esempio di convocazione di POST che viene disposta in **alcuni** percorsi geo


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

### <a name="query-using-csom"></a>Query utilizza CSOM

Ecco una query di esempio CSOM che viene disposta in **tutti i** percorsi geo:

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

