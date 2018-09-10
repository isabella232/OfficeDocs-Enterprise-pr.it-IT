---
title: Servizio Web per URL e indirizzi IP di Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/4/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: Per identificare e differenziare meglio il traffico di rete di Office 365, un nuovo servizio Web pubblica gli endpoint di Office 365, consentendo agli utenti di valutare, configurare e rimanere aggiornati con le ultime modifiche. Questo nuovo servizio Web sostituisce i file scaricabili XML attualmente disponibili.
ms.openlocfilehash: 3abd6a0692ae4d66c76f8c0d65653b83646c6e23
ms.sourcegitcommit: d07feeba2e886febc6a57a5c33b0df02b3db5631
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2018
ms.locfileid: "23830890"
---
# <a name="office-365-ip-address-and-url-web-service"></a>**Servizio Web per URL e indirizzi IP di Office 365**

Per identificare e differenziare meglio il traffico di rete di Office 365, un nuovo servizio Web pubblica gli endpoint di Office 365, consentendo agli utenti di valutare, configurare e rimanere aggiornati con le ultime modifiche. Questo nuovo servizio Web sostituisce i file scaricabili XML attualmente disponibili. Il formato XML verrà ritirato il 2 ottobre 2018.

Un cliente o un fornitore di dispositivi di rete perimetrale può sfruttare il nuovo servizio Web basato su REST per voci FQDN e indirizzi IP di Office 365. È possibile accedere ai dati direttamente in un browser Web tramite questi URL.

- Per la versione più recente degli URL e degli intervalli di indirizzi IP di Office 365, usare [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Per i dati sulla pagina degli URL e degli intervalli di indirizzi IP di Office 365 per firewall e server proxy, usare [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Per ottenere tutte le ultime modifiche apportate dalla fine di luglio 2018, quando il servizio Web ha iniziato a essere disponibile, usare [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

Un cliente può utilizzare questo servizio Web per le operazioni seguenti:

- Aggiornare gli script di PowerShell per ottenere i dati degli endpoint di Office 365 e modificare la formattazione dei dispositivi di rete in uso.
- Usare queste informazioni per aggiornare i file PAC distribuiti ai computer client.

Un fornitore di dispositivi di rete perimetrale può utilizzare questo servizio Web per le operazioni seguenti:

- Creare e testare il software dei dispositivi per scaricare l'elenco per la configurazione automatizzata.
- Verificare la versione corrente.
- Conoscere le modifiche apportate.

Per ulteriori informazioni, vedere:

- [Post di blog dell'annuncio nel forum della community IT di Office 365](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [Forum della community IT di Office 365 per domande sull'uso dei servizi Web](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>**Parametri comuni**

Questi parametri sono comuni a tutti i metodi di servizio Web:

- **format=CSV | JSON**: parametro stringa di query. Per impostazione predefinita, i dati vengono restituiti in formato JSON. Includere questo parametro opzionale per ottenere i dati in formato CSV (valori separati da virgola).
- **ClientRequestId**: parametro stringa di query. Un GUID obbligatorio generato dall'utente per l'associazione del client. È necessario generare un GUID per ogni computer che chiama il servizio Web. Non usare i GUID mostrati negli esempi seguenti perché potrebbero essere bloccati dal servizio Web in futuro. Il formato del GUID è _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, dove x rappresenta un numero esadecimale. Per generare un GUID, usare il comando [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) di PowerShell.

## <a name="version-web-method"></a>**Metodo Web per la versione**

Microsoft aggiorna le voci FQDN e gli indirizzi IP di Office 365 alla fine di ogni mese e occasionalmente per requisiti operativi o relativi al supporto. Ai dati di ciascuna istanza pubblicata viene assegnato un numero di versione. Il metodo Web per la versione consente di verificare l'ultima versione per ogni istanza del servizio di Office 365. È consigliabile controllare la versione ogni giorno o, al massimo, ogni ora. Le nuove versioni sono previste all'inizio di ogni mese. A volte, a causa di richieste di assistenza, aspetti legati alla sicurezza o altri requisiti operativi, sono disponibili nuove versioni durante il mese.

È presente un parametro per il metodo Web per la versione:

- **AllVersions=true**: parametro stringa di query. Per impostazione predefinita, la versione restituita è la più recente. Includere questo parametro opzionale per richiedere tutte le versioni pubblicate.
- **Format=JSON** | **CSV** | **RSS**: oltre ai formati JSON e CSV, il metodo Web per la versione supporta anche RSS. È possibile utilizzarlo insieme con il parametro allVersions=true per richiedere un feed RSS da utilizzare con Outlook o altri lettori RSS.
- **Instance**: parametro di route. Questo parametro opzionale specifica l'istanza per cui restituire la versione. Se si omette, vengono restituite tutte le istanze. Le istanze valide sono: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.

Il risultato ottenuto dal metodo Web per la versione potrebbe essere un singolo record o una matrice di record. Gli elementi di ogni record sono:

- instance: il nome breve dell'istanza del servizio di Office 365.
- latest: l'ultima versione degli endpoint dell'istanza specificata.
- versions: un elenco di tutte le versioni precedenti dell'istanza specificata. Questo elemento è incluso solo se il parametro AllVersions è true.

### <a name="examples"></a>**Esempi:**

URI della richiesta di esempio 1: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Questo URI restituisce l'ultima versione di ogni istanza del servizio di Office 365. Risultato dell'esempio:

```json
[
 {
  "instance": "Worldwide",
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD",
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 },
 {
  "instance": "Germany",
  "latest": "2018063000"
 }
]
```

[!IMPORTANT]
Il GUID del parametro ClientRequestID in questi URI è solo un esempio. Per provare gli URI del servizio Web, generare il proprio GUID. I GUID mostrati in questi esempi potrebbero essere bloccati dal servizio Web in futuro.

URI della richiesta di esempio 2: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Questo URI restituisce l'ultima versione dell'istanza del servizio di Office 365 specificata. Risultato dell'esempio:

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}

```

URI della richiesta di esempio 3: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Questo URI mostra l'output in formato CSV. Risultato dell'esempio:

```csv
instance,latest
Worldwide,2018063000
```

URI della richiesta di esempio 4: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Questo URI mostra tutte le versioni precedenti che sono state pubblicate per l'istanza Worldwide del servizio di Office 365. Risultato dell'esempio:

```json
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

URI del feed RSS di esempio 5: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)

Questo URI mostra un feed RSS delle versioni pubblicate che includono collegamenti all'elenco di modifiche di ogni versione. Risultato dell'esempio:

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<rss version="2.0" xmlns:a10="http://www.w3.org/2005/Atom">
<channel>
<link>http://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
...
```

## <a name="endpoints-web-method"></a>**Metodo Web per gli endpoint**

Il metodo Web per gli endpoint restituisce tutti i record per gli URL e gli intervalli di indirizzi IP che formano il servizio di Office 365. Gli ultimi dati ottenuti dal metodo Web per gli endpoint devono essere usati per la configurazione dei dispositivi di rete, ma i dati possono essere raccolti per un massimo di 30 giorni dopo la loro pubblicazione a causa del preavviso fornito per le aggiunte. I parametri del metodo Web per gli endpoint sono:

- **ServiceAreas**: parametro stringa di query. Un elenco di aree del servizio con valori separati da virgole. Gli elementi validi sono Common, Exchange, SharePoint, Skype. Poiché gli elementi dell'area del servizio Common sono un prerequisito per tutte le altre aree del servizio, tali elementi devono essere sempre inclusi nel servizio Web. In caso contrario, vengono restituite tutte le aree del servizio.
- **TenantName**: parametro stringa di query. Il nome del tenant di Office 365 dell'utente. Il servizio Web prende il nome fornito dall'utente e lo inserisce nelle parti degli URL che includono il nome del tenant. Se non si fornisce il nome del tenant, quelle parti degli URL hanno il carattere jolly (\*).
- **NoIPv6**: parametro stringa di query. Impostare questo parametro su true per escludere gli indirizzi IPv6 dall'output, ad esempio, se non si usa il protocollo IPv6 nella propria rete.
- **Instance**: parametro di route. Questo parametro obbligatorio specifica l'istanza per cui restituire gli endpoint. Le istanze valide sono: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.

Il risultato ottenuto dal metodo Web per gli endpoint è una matrice di record in cui ogni record rappresenta un set di endpoint. Gli elementi per ogni record sono:

- id: il numero ID non modificabile del set di endpoint.
- serviceArea: l'area del servizio di cui fa parte: Common, Exchange, SharePoint o Skype.
- urls: gli URL per il set di endpoint. Una matrice JSON di record DNS. Questo elemento viene omesso se non specificato.
- tcpPorts: le porte TCP per il set di endpoint. Tutti gli elementi delle porte sono formattati come elenco con valori separati da virgole di porte o intervalli di porte separati da un trattino (-). Le porte si applicano a tutti gli URL e indirizzi IP nel set di endpoint per quella categoria. Questo elemento viene omesso se non specificato.
- udpPorts: le porte UDP degli intervalli di indirizzi IP nel set di endpoint. Questo elemento viene omesso se non specificato.
- ips: gli intervalli di indirizzi IP associati al set di endpoint come associati alle porte UDP o TCP elencate. Una matrice JSON di intervalli di indirizzi IP. Questo elemento viene omesso se non specificato.
- category: la categoria di connettività per il set di endpoint. I valori validi sono Optimize, Allow e Default. Questo elemento è obbligatorio.
- expressRoute: True o False se il set di endpoint sfrutta la connessione ExpressRoute.
- required: True se il set di endpoint deve avere una connettività per Office 365 che sia supportata. False se il set di endpoint è facoltativo.
- notes: per gli endpoint facoltativi, questo testo descrive la funzionalità di Office 365 che non sarà presente se gli URL o gli indirizzi IP nel set di endpoint non sono accessibili al livello della rete. Questo elemento viene omesso se non specificato.

### <a name="examples"></a>Esempi:

URI della richiesta di esempio 1: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Questo URI ottiene tutti gli endpoint per l'istanza Worldwide di Office 365 per tutti i carichi di lavoro. Risultato dell'esempio che mostra un estratto dell'output:

```json
[
 {
  "id": 1,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.protection.outlook.com"
   ],
  "ips":
   [
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32"
   ],
  "tcpPorts": "443",
  "expressRoute": true,
  "category": "Allow"
 },
 {
  "id": 2,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.mail.protection.outlook.com"
   ],
...
```

In questo esempio non sono inclusi altri set di endpoint.

URI della richiesta di esempio 2: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

In questo esempio si ottengono gli endpoint per l'istanza Worldwide di Office 365 solo per Exchange Online e le dipendenze.

L'output dell'esempio 2 è simile a quello dell'esempio 1, ad eccezione del fatto che i risultati non includono endpoint per SharePoint Online o Skype for Business Online.

## <a name="changes-web-method"></a>Metodo Web per le modifiche

Il metodo Web per le modifiche restituisce gli aggiornamenti più recenti che sono stati pubblicati. In genere, si tratta delle modifiche del mese precedente apportate agli URL e agli intervalli di indirizzi IP. Le modifiche più importanti da elaborare riguardano l'aggiunta di nuovi URL o indirizzi IP: infatti, se non è stato possibile aggiungere un indirizzo IP a un elenco di controllo di accesso al firewall o un URL a un elenco di server proxy da ignorare, può verificarsi un'interruzione del servizio per gli utenti di Office 365 che usano il relativo dispositivo di rete. Nonostante i requisiti operativi, le operazioni _Add_ vengono aggiunte con un preavviso di 30 giorni prima che si verifichi tale interruzione del servizio.

Il parametro del metodo Web per le modifiche è il seguente:

- **Version**: parametro di route dell'URL obbligatorio. Indica la versione attualmente implementata dall'utente, che desidera verificare le modifiche apportate a partire da quella versione. Il formato è _YYYYMMDDNN_.

Il risultato ottenuto dal metodo Web per le modifiche è una matrice di record in cui ogni record rappresenta una modifica in una versione specifica degli endpoint. Gli elementi per ogni record sono:

- id: l'ID non modificabile del record della modifica.
- endpointSetId: l'ID del record del set di endpoint cui è stata apportata la modifica. Questo elemento è obbligatorio.
- disposition: può trattarsi di una modifica, un'aggiunta o una rimozione e descrive l'effetto della modifica apportata sul record del set di endpoint. Questo elemento è obbligatorio.
- version: la versione del set di endpoint pubblicato in cui è stata introdotta la modifica. I numeri di versione hanno il formato _YYYYMMDDNN_, dove NN è un numero naturale incrementato se sono presenti più versioni da pubblicare in un unico giorno.
- previous: una sottostruttura che descrive nel dettaglio i valori precedenti degli elementi modificati sul set di endpoint. Questo elemento non è incluso per i set di endpoint aggiunti di recente. Include tcpPorts, udpPorts, ExpressRoute, category, required, notes.
- current: una sottostruttura che descrive nel dettaglio i valori aggiornati degli elementi modificati sul set di endpoint. Include tcpPorts, udpPorts, ExpressRoute, category, required, notes.
- add: una sottostruttura che descrive nel dettaglio gli elementi da aggiungere alle raccolte dei set di endpoint. Questo elemento viene omesso se non ci sono aggiunte.
  - effectiveDate: definisce la data in cui le aggiunte saranno effettive nel servizio.
  - ips: gli elementi da aggiungere alla matrice di indirizzi IP.
  - urls: gli elementi da aggiungere alla matrice di URL.
- remove: una sottostruttura che descrive nel dettaglio gli elementi da rimuovere dal set di endpoint. Questo elemento viene omesso se non ci sono rimozioni.
  - ips: gli elementi da rimuovere dalla matrice di indirizzi IP.
  - urls: gli elementi da rimuovere dalla matrice di URL.

### <a name="examples"></a>**Esempi:**

URI della richiesta di esempio 1: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Richiede tutte le modifiche precedenti apportate all'istanza Worldwide del servizio di Office 365. Risultato dell'esempio:

```json
[
 {
  "id": 424,
  "endpointSetId": 32,
  "disposition": "Change",
  "version": "2018062700",
  "remove":
   {
    "urls":
     [
      "*.api.skype.com", "skypegraph.skype.com"
     ]
   }
 },
 {
  "id": 426,
  "endpointSetId": 31,
  "disposition": "Change",
  "version": "2018062700",
  "add":
   {
    "effectiveDate": "20180609",
    "ips":
     [
      "51.140.203.190/32"
     ]
   },
  "remove":
   {
    "ips":
     [
...
```

URI della richiesta di esempio 2: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Richiede le modifiche apportate all'istanza Worldwide di Office 365 a partire dalla versione specificata. In questo caso, la versione specificata è la più recente. Risultato dell'esempio:

```json
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]
```

## <a name="example-powershell-script"></a>**Script di PowerShell di esempio**

Di seguito è riportato uno script di PowerShell che è possibile eseguire per verificare se sono presenti azioni che è necessario effettuare per i dati aggiornati. Questo script controlla il numero di versione degli endpoint dell'istanza Worldwide di Office 365. Quando è presente una modifica, lo script scarica gli endpoint e li filtra per quelli di categoria &quot;Allow&quot; e &quot;Optimize&quot;. Inoltre, usa un ClientRequestId unico tra più chiamate e salva l'ultima versione trovata in un file temporaneo. È necessario chiamare questo script ogni ora per verificare la disponibilità di un aggiornamento della versione.

```powershell
# webservice root URL
$ws = "https://endpoints.office.com"
# path where client ID and latest version number will be stored
$datapath = $Env:TEMP + "\endpoints_clientid_latestversion.txt"
# fetch client ID and version if data file exists; otherwise create new file
if (Test-Path $datapath) {
    $content = Get-Content $datapath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
}
else {
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $datapath
}
# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"

    # write the new version number to the data file
    @($clientRequestId, $version.latest) | Out-File $datapath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    $flatIps = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings have dots while IPv6 strings have colons
        $ip4s = $ips | Where-Object { $_ -like '*.*' }

        $ipCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ipCustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ipCustomObjects
    }
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIps.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    # TODO Call Send-MailMessage with new endpoints data
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date"
}
```

## <a name="example-python-script"></a>**Script di Python di esempio**

Di seguito è riportato uno script di Python, testato con Python 3.6.3 su Windows 10, che è possibile eseguire per verificare se sono presenti azioni che è necessario effettuare per i dati aggiornati. Questo script controlla il numero di versione degli endpoint dell'istanza Worldwide di Office 365. Quando è presente una modifica, scarica gli endpoint e li filtra per quelli di categoria _Allow_ e _Optimize_. Inoltre, usa un ClientRequestId unico tra più chiamate e salva l'ultima versione trovata in un file temporaneo. È necessario chiamare questo script ogni ora per verificare la disponibilità di un aggiornamento della versione.

```python
import json
import os
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = os.environ['TEMP'] + '\endpoints_clientid_latestversion.txt'
# fetch client ID and version if data exists; otherwise create new file
if os.path.exists(datapath):
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))

    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

## <a name="web-service-interface-versioning"></a>**Controllo delle versioni dell'interfaccia del servizio Web**

In futuro potrebbero essere richiesti aggiornamenti ai parametri o ai risultati di questi metodi del servizio Web. Dopo il rilascio della versione di disponibilità generale di questi servizi Web, Microsoft si impegnerà nel fornire avvisi preventivi in merito alla disponibilità di aggiornamenti dei materiali per il servizio Web. Quando Microsoft ritiene che un aggiornamento potrebbe richiedere modifiche per i client che usano il servizio Web, Microsoft mantiene la versione precedente del servizio Web disponibile per almeno dodici (12) mesi dopo il rilascio della nuova versione. I clienti che non eseguono l'aggiornamento durante questo periodo potrebbero non essere in grado di accedere al servizio Web e ai suoi metodi. I clienti devono assicurarsi che i client del servizio Web continuino a funzionare correttamente se le modifiche riportate di seguito vengono apportate alla firma per l'interfaccia del servizio Web:

- L'aggiunta di un nuovo parametro opzionale a un metodo Web esistente che non deve essere fornito dai client precedenti e che non influisce sul risultato ottenuto da un client precedente.
- L'aggiunta di un nuovo attributo denominato in una delle colonne aggiuntive o in uno degli elementi REST della risposta nel CSV di risposta.
- L'aggiunta di un nuovo metodo Web con un nuovo nome che non è chiamato dai client precedenti.

## <a name="related-topics"></a>Argomenti correlati
  
[URL e intervalli di indirizzi IP per Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Domande frequenti sugli endpoint di Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[Principi della connettività di rete di Office 365](office-365-network-connectivity-principles.md)

[Ottimizzazione delle prestazioni e della rete di Office 365](network-planning-and-performance.md)

[Connettività di rete con Office 365](network-connectivity.md)
  
[Azure ExpressRoute per Office 365](azure-expressroute.md)
  
[Gestione di ExpressRoute per la connettività di Office 365](managing-expressroute-for-connectivity.md)
  
[Routing con ExpressRoute per Office 365](routing-with-expressroute.md)
  
[Implementazione di ExpressRoute per Office 365](implementing-expressroute.md)
  
[Uso delle community BGP in ExpressRoute per gli scenari di Office 365 (anteprima)](bgp-communities-in-expressroute.md)
  
[Qualità multimediale e prestazioni della connettività di rete in Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Ottimizzazione della rete per Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute e QoS in Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Flusso di chiamata con ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Ottimizzazione delle prestazioni di Office 365 mediante l'uso della cronologia delle prestazioni e delle previsioni](performance-tuning-using-baselines-and-history.md)
  
[Piano di risoluzione dei problemi di prestazioni per Office 365](performance-troubleshooting-plan.md)
