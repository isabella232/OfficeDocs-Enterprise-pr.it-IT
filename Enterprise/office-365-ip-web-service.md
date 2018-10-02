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
ms.openlocfilehash: 2b5763b9f8f08f2cc619331dac70743474a8515b
ms.sourcegitcommit: d67e73f6cdc1e8d220d90a239e23e218f24528d2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/21/2018
ms.locfileid: "24961825"
---
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="0b5a2-104">**Servizio Web per URL e indirizzi IP di Office 365**</span><span class="sxs-lookup"><span data-stu-id="0b5a2-104">**Office 365 IP Address and URL Web service**</span></span>

<span data-ttu-id="0b5a2-p102">Per identificare e differenziare meglio il traffico di rete di Office 365, un nuovo servizio Web pubblica gli endpoint di Office 365, consentendo agli utenti di valutare, configurare e rimanere aggiornati con le ultime modifiche. Questo nuovo servizio Web sostituisce i file scaricabili XML attualmente disponibili. Il formato XML verrà ritirato il 2 ottobre 2018.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p102">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service replaces the XML downloadable files that are currently available. The XML format is planned to be phased out on October 2, 2018.</span></span>

<span data-ttu-id="0b5a2-p103">Un cliente o un fornitore di dispositivi di rete perimetrale può sfruttare il nuovo servizio Web basato su REST per voci FQDN e indirizzi IP di Office 365. È possibile accedere ai dati direttamente in un browser Web tramite questi URL.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p103">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries. You can access the data directly in a web browser using these URLs.</span></span>

- <span data-ttu-id="0b5a2-110">Per la versione più recente degli URL e degli intervalli di indirizzi IP di Office 365, usare [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="0b5a2-110">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="0b5a2-111">Per i dati sulla pagina degli URL e degli intervalli di indirizzi IP di Office 365 per firewall e server proxy, usare [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="0b5a2-111">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="0b5a2-112">Per ottenere tutte le ultime modifiche apportate dalla fine di luglio 2018, quando il servizio Web ha iniziato a essere disponibile, usare [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="0b5a2-112">To get all the latest changes since the end of July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="0b5a2-113">Un cliente può utilizzare questo servizio Web per le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-113">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="0b5a2-114">Aggiornare gli script di PowerShell per ottenere i dati degli endpoint di Office 365 e modificare la formattazione dei dispositivi di rete in uso.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-114">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="0b5a2-115">Usare queste informazioni per aggiornare i file PAC distribuiti ai computer client.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-115">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="0b5a2-116">Un fornitore di dispositivi di rete perimetrale può utilizzare questo servizio Web per le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-116">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="0b5a2-117">Creare e testare il software dei dispositivi per scaricare l'elenco per la configurazione automatizzata.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-117">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="0b5a2-118">Verificare la versione corrente.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-118">Check for the current version.</span></span>
- <span data-ttu-id="0b5a2-119">Conoscere le modifiche apportate.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-119">Get the current changes.</span></span>

<span data-ttu-id="0b5a2-120">Per ulteriori informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-120">For additional information, see:</span></span>

- [<span data-ttu-id="0b5a2-121">Post di blog dell'annuncio nel forum della community IT di Office 365</span><span class="sxs-lookup"><span data-stu-id="0b5a2-121">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [<span data-ttu-id="0b5a2-122">Forum della community IT di Office 365 per domande sull'uso dei servizi Web</span><span class="sxs-lookup"><span data-stu-id="0b5a2-122">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a><span data-ttu-id="0b5a2-123">**Parametri comuni**</span><span class="sxs-lookup"><span data-stu-id="0b5a2-123">**Common parameters**</span></span>

<span data-ttu-id="0b5a2-124">Questi parametri sono comuni a tutti i metodi di servizio Web:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-124">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="0b5a2-p104">**format=CSV | JSON**: parametro stringa di query. Per impostazione predefinita, i dati vengono restituiti in formato JSON. Includere questo parametro opzionale per ottenere i dati in formato CSV (valori separati da virgola).</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p104">**format=CSV | JSON** - Query string parameter. By default, the returned data format is JSON. Include this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="0b5a2-p105">**ClientRequestId**: parametro stringa di query. Un GUID obbligatorio generato dall'utente per l'associazione del client. È necessario generare un GUID per ogni computer che chiama il servizio Web. Non usare i GUID mostrati negli esempi seguenti perché potrebbero essere bloccati dal servizio Web in futuro. Il formato del GUID è _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, dove x rappresenta un numero esadecimale. Per generare un GUID, usare il comando [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p105">**ClientRequestId** - Query string parameter. A required GUID that you generate for client association. You should generate a GUID for each machine that calls the web service. Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future. GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number. To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span>

## <a name="version-web-method"></a><span data-ttu-id="0b5a2-134">**Metodo Web per la versione**</span><span class="sxs-lookup"><span data-stu-id="0b5a2-134">**Version web method**</span></span>

<span data-ttu-id="0b5a2-p106">Microsoft aggiorna le voci FQDN e gli indirizzi IP di Office 365 alla fine di ogni mese e occasionalmente per requisiti operativi o relativi al supporto. Ai dati di ciascuna istanza pubblicata viene assegnato un numero di versione. Il metodo Web per la versione consente di verificare l'ultima versione per ogni istanza del servizio di Office 365. È consigliabile controllare la versione ogni giorno o, al massimo, ogni ora. Le nuove versioni sono previste all'inizio di ogni mese. A volte, a causa di richieste di assistenza, aspetti legati alla sicurezza o altri requisiti operativi, sono disponibili nuove versioni durante il mese.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p106">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly. New versions should be expected at the start of each month. Sometimes due to support incident, security, or other operational requirements there will be new versions during the month.</span></span>

<span data-ttu-id="0b5a2-141">È presente un parametro per il metodo Web per la versione:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-141">There is one parameter for the version web method:</span></span>

- <span data-ttu-id="0b5a2-p107">**AllVersions=true**: parametro stringa di query. Per impostazione predefinita, la versione restituita è la più recente. Includere questo parametro opzionale per richiedere tutte le versioni pubblicate.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p107">**AllVersions=true** - Query string parameter. By default, the version returned is the latest. Include this optional parameter to request all published versions.</span></span>
- <span data-ttu-id="0b5a2-p108">**Format=JSON** | **CSV** | **RSS**: oltre ai formati JSON e CSV, il metodo Web per la versione supporta anche RSS. È possibile utilizzarlo insieme con il parametro allVersions=true per richiedere un feed RSS da utilizzare con Outlook o altri lettori RSS.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p108">**Format=JSON** | **CSV** | **RSS** – In addition to the JSON and CSV formats, the version web method also supports RSS. You can use this along with the allVersions=true parameter to request an RSS feed which can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="0b5a2-p109">**Instance**: parametro di route. Questo parametro opzionale specifica l'istanza per cui restituire la versione. Se si omette, vengono restituite tutte le istanze. Le istanze valide sono: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p109">**Instance** - Route parameter. This optional parameter specifies the instance to return the version for. If omitted, all instances are returned. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="0b5a2-p110">Il risultato ottenuto dal metodo Web per la versione potrebbe essere un singolo record o una matrice di record. Gli elementi di ogni record sono:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p110">The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>

- <span data-ttu-id="0b5a2-153">instance: il nome breve dell'istanza del servizio di Office 365.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-153">instance - The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="0b5a2-154">latest: l'ultima versione degli endpoint dell'istanza specificata.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-154">latest - The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="0b5a2-p111">versions: un elenco di tutte le versioni precedenti dell'istanza specificata. Questo elemento è incluso solo se il parametro AllVersions è true.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p111">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>

<span data-ttu-id="0b5a2-p112">È possibile utilizzare Microsoft Flow per ricevere notifiche di posta elettronica delle modifiche agli URL e agli indirizzi IP. Vedere l'articolo sull'[uso di Microsoft Flow per ricevere un'e-mail per le modifiche agli URL e agli indirizzi IP di Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p112">You can use Microsoft Flow to get email notifications of changes to the IP Addresses and URLs. See [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span></span>

### <a name="examples"></a><span data-ttu-id="0b5a2-159">**Esempi:**</span><span class="sxs-lookup"><span data-stu-id="0b5a2-159">**Examples:**</span></span>

<span data-ttu-id="0b5a2-160">URI della richiesta di esempio 1: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="0b5a2-160">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="0b5a2-p113">Questo URI restituisce l'ultima versione di ogni istanza del servizio di Office 365. Risultato dell'esempio:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p113">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

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
<span data-ttu-id="0b5a2-p114">Il GUID del parametro ClientRequestID in questi URI è solo un esempio. Per provare gli URI del servizio Web, generare il proprio GUID. I GUID mostrati in questi esempi potrebbero essere bloccati dal servizio Web in futuro.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p114">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="0b5a2-166">URI della richiesta di esempio 2: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="0b5a2-166">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="0b5a2-p115">Questo URI restituisce l'ultima versione dell'istanza del servizio di Office 365 specificata. Risultato dell'esempio:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p115">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}

```

<span data-ttu-id="0b5a2-169">URI della richiesta di esempio 3: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="0b5a2-169">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="0b5a2-p116">Questo URI mostra l'output in formato CSV. Risultato dell'esempio:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p116">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="0b5a2-172">URI della richiesta di esempio 4: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="0b5a2-172">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="0b5a2-p117">Questo URI mostra tutte le versioni precedenti che sono state pubblicate per l'istanza Worldwide del servizio di Office 365. Risultato dell'esempio:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p117">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="0b5a2-175">URI del feed RSS di esempio 5: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="0b5a2-175">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="0b5a2-p118">Questo URI mostra un feed RSS delle versioni pubblicate che includono collegamenti all'elenco di modifiche di ogni versione. Risultato dell'esempio:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p118">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

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

## <a name="endpoints-web-method"></a><span data-ttu-id="0b5a2-178">**Metodo Web per gli endpoint**</span><span class="sxs-lookup"><span data-stu-id="0b5a2-178">**Endpoints web method**</span></span>

<span data-ttu-id="0b5a2-p119">Il metodo Web per gli endpoint restituisce tutti i record per gli URL e gli intervalli di indirizzi IP che formano il servizio di Office 365. Gli ultimi dati ottenuti dal metodo Web per gli endpoint devono essere usati per la configurazione dei dispositivi di rete, ma i dati possono essere raccolti per un massimo di 30 giorni dopo la loro pubblicazione a causa del preavviso fornito per le aggiunte. I parametri del metodo Web per gli endpoint sono:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p119">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service. While the latest data from the endpoints web method should be used for network device configuration, the data can be cached for up to 30 days after it is published due to the advance notice provided for additions. Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="0b5a2-p120">**ServiceAreas**: parametro stringa di query. Un elenco di aree del servizio con valori separati da virgole. Gli elementi validi sono Common, Exchange, SharePoint, Skype. Poiché gli elementi dell'area del servizio Common sono un prerequisito per tutte le altre aree del servizio, tali elementi devono essere sempre inclusi nel servizio Web. In caso contrario, vengono restituite tutte le aree del servizio.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p120">**ServiceAreas** - Query string parameter. A comma-separated list of service areas. Valid items are Common,Exchange,SharePoint,Skype. Because Common service area items are a prerequisite for all other service areas, the web service will always include them. If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="0b5a2-p121">**TenantName**: parametro stringa di query. Il nome del tenant di Office 365 dell'utente. Il servizio Web prende il nome fornito dall'utente e lo inserisce nelle parti degli URL che includono il nome del tenant. Se non si fornisce il nome del tenant, quelle parti degli URL hanno il carattere jolly (\*).</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p121">**TenantName** - Query string parameter. Your Office 365 tenant name. The web service takes your provided name and inserts it in parts of URLs that include the tenant name. If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="0b5a2-p122">**NoIPv6**: parametro stringa di query. Impostare questo parametro su true per escludere gli indirizzi IPv6 dall'output, ad esempio, se non si usa il protocollo IPv6 nella propria rete.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p122">**NoIPv6** - Query string parameter. Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="0b5a2-p123">**Instance**: parametro di route. Questo parametro obbligatorio specifica l'istanza per cui restituire gli endpoint. Le istanze valide sono: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p123">**Instance** - Route parameter. This required parameter specifies the instance to return the endpoints for. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="0b5a2-p124">Il risultato ottenuto dal metodo Web per gli endpoint è una matrice di record in cui ogni record rappresenta un set di endpoint. Gli elementi per ogni record sono:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p124">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>

- <span data-ttu-id="0b5a2-198">id: il numero ID non modificabile del set di endpoint.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-198">id - The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="0b5a2-199">serviceArea: l'area del servizio di cui fa parte: Common, Exchange, SharePoint o Skype.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-199">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
- <span data-ttu-id="0b5a2-p125">urls: gli URL per il set di endpoint. Una matrice JSON di record DNS. Questo elemento viene omesso se non specificato.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p125">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
- <span data-ttu-id="0b5a2-p126">tcpPorts: le porte TCP per il set di endpoint. Tutti gli elementi delle porte sono formattati come elenco con valori separati da virgole di porte o intervalli di porte separati da un trattino (-). Le porte si applicano a tutti gli URL e indirizzi IP nel set di endpoint per quella categoria. Questo elemento viene omesso se non specificato.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p126">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
- <span data-ttu-id="0b5a2-p127">udpPorts: le porte UDP degli intervalli di indirizzi IP nel set di endpoint. Questo elemento viene omesso se non specificato.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p127">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
- <span data-ttu-id="0b5a2-p128">ips: gli intervalli di indirizzi IP associati al set di endpoint come associati alle porte UDP o TCP elencate. Una matrice JSON di intervalli di indirizzi IP. Questo elemento viene omesso se non specificato.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p128">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. A JSON array of IP Address ranges. Omitted if blank.</span></span>
- <span data-ttu-id="0b5a2-p129">categoria: la categoria di connettività per il set di endpoint. I valori validi sono Optimize, Allow e Default. Se si usano i dati di endpoint per cercare la categoria di un indirizzo IP o un URL, è possibile che la query restituisca più categorie. Esistono alcuni motivi per cui potrebbe verificarsi. In questi casi è necessario seguire i suggerimenti per la categoria con priorità più alta. Ad esempio, se viene visualizzato un endpoint sia su Optimize sia su Allow, seguire i requisiti per Optimize. Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p129">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. If using the endpoint data to search for the category of an IP Address or URL, it is possible that your query may return multiple categories. There are a few reasons why that may happen. In these cases you should follow the recommendations for the highest priority category. For example, if the endpoint appears in both Optimize and Allow, you should follow the requirements for Optimize. Required.</span></span> 
- <span data-ttu-id="0b5a2-219">expressRoute: True o False se il set di endpoint sfrutta la connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-219">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
- <span data-ttu-id="0b5a2-p130">required: True se il set di endpoint deve avere una connettività per Office 365 che sia supportata. False se il set di endpoint è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p130">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. False if this endpoint set is optional.</span></span>
- <span data-ttu-id="0b5a2-p131">notes: per gli endpoint facoltativi, questo testo descrive la funzionalità di Office 365 che non sarà presente se gli URL o gli indirizzi IP nel set di endpoint non sono accessibili al livello della rete. Questo elemento viene omesso se non specificato.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p131">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="0b5a2-224">Esempi:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-224">Examples:</span></span>

<span data-ttu-id="0b5a2-225">URI della richiesta di esempio 1: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="0b5a2-225">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="0b5a2-p132">Questo URI ottiene tutti gli endpoint per l'istanza Worldwide di Office 365 per tutti i carichi di lavoro. Risultato dell'esempio che mostra un estratto dell'output:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p132">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>

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

<span data-ttu-id="0b5a2-228">In questo esempio non sono inclusi altri set di endpoint.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-228">Additional endpoint sets are not included in this example.</span></span>

<span data-ttu-id="0b5a2-229">URI della richiesta di esempio 2: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="0b5a2-229">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="0b5a2-230">In questo esempio si ottengono gli endpoint per l'istanza Worldwide di Office 365 solo per Exchange Online e le dipendenze.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-230">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="0b5a2-231">L'output dell'esempio 2 è simile a quello dell'esempio 1, ad eccezione del fatto che i risultati non includono endpoint per SharePoint Online o Skype for Business Online.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-231">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="0b5a2-232">Metodo Web per le modifiche</span><span class="sxs-lookup"><span data-stu-id="0b5a2-232">Changes web method</span></span>

<span data-ttu-id="0b5a2-p133">Il metodo Web per le modifiche restituisce gli aggiornamenti più recenti che sono stati pubblicati. In genere, si tratta delle modifiche del mese precedente apportate agli URL e agli intervalli di indirizzi IP. Le modifiche più importanti da elaborare riguardano l'aggiunta di nuovi URL o indirizzi IP: infatti, se non è stato possibile aggiungere un indirizzo IP a un elenco di controllo di accesso al firewall o un URL a un elenco di server proxy da ignorare, può verificarsi un'interruzione del servizio per gli utenti di Office 365 che usano il relativo dispositivo di rete. Nonostante i requisiti operativi, le operazioni _Add_ vengono aggiunte con un preavviso di 30 giorni prima che si verifichi tale interruzione del servizio.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p133">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs. The most critical changes to be processed are when new URLs or IP Addresses are added since failing to add an IP Address to a firewall access control list, or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device. Notwithstanding operational requirements, _Add_ operations are added with 30 days' notice before such an outage would occur.</span></span>

<span data-ttu-id="0b5a2-237">Il parametro del metodo Web per le modifiche è il seguente:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-237">The parameter for the changes web method is:</span></span>

- <span data-ttu-id="0b5a2-p134">**Version**: parametro di route dell'URL obbligatorio. Indica la versione attualmente implementata dall'utente, che desidera verificare le modifiche apportate a partire da quella versione. Il formato è _YYYYMMDDNN_.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p134">**Version** - Required URL route parameter. The version that you have currently implemented, and you want to see the changes since that version. The format is _YYYYMMDDNN_.</span></span>

<span data-ttu-id="0b5a2-p135">Il risultato ottenuto dal metodo Web per le modifiche è una matrice di record in cui ogni record rappresenta una modifica in una versione specifica degli endpoint. Gli elementi per ogni record sono:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p135">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>

- <span data-ttu-id="0b5a2-243">id: l'ID non modificabile del record della modifica.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-243">id - The immutable id of the change record.</span></span>
- <span data-ttu-id="0b5a2-p136">endpointSetId: l'ID del record del set di endpoint cui è stata apportata la modifica. Questo elemento è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p136">endpointSetId - The ID of the endpoint set record that is changed. Required.</span></span>
- <span data-ttu-id="0b5a2-p137">disposition: può trattarsi di una modifica, un'aggiunta o una rimozione e descrive l'effetto della modifica apportata sul record del set di endpoint. Questo elemento è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p137">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record. Required.</span></span>
- <span data-ttu-id="0b5a2-p138">version: la versione del set di endpoint pubblicato in cui è stata introdotta la modifica. I numeri di versione hanno il formato _YYYYMMDDNN_, dove NN è un numero naturale incrementato se sono presenti più versioni da pubblicare in un unico giorno.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p138">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format _YYYYMMDDNN_, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="0b5a2-p139">previous: una sottostruttura che descrive nel dettaglio i valori precedenti degli elementi modificati sul set di endpoint. Questo elemento non è incluso per i set di endpoint aggiunti di recente. Include tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p139">previous - A substructure detailing previous values of changed elements on the endpoint set. This will not be included for newly added endpoint sets. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
- <span data-ttu-id="0b5a2-p140">current: una sottostruttura che descrive nel dettaglio i valori aggiornati degli elementi modificati sul set di endpoint. Include tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p140">current - A substructure detailing updated values of changes elements on the endpoint set. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
- <span data-ttu-id="0b5a2-p141">add: una sottostruttura che descrive nel dettaglio gli elementi da aggiungere alle raccolte dei set di endpoint. Questo elemento viene omesso se non ci sono aggiunte.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p141">add - A substructure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
  - <span data-ttu-id="0b5a2-257">effectiveDate: definisce la data in cui le aggiunte saranno effettive nel servizio.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-257">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
  - <span data-ttu-id="0b5a2-258">ips: gli elementi da aggiungere alla matrice di indirizzi IP.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-258">ips - Items to be added to the ips array.</span></span>
  - <span data-ttu-id="0b5a2-259">urls: gli elementi da aggiungere alla matrice di URL.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-259">urls- Items to be added to the urls array.</span></span>
- <span data-ttu-id="0b5a2-p142">remove: una sottostruttura che descrive nel dettaglio gli elementi da rimuovere dal set di endpoint. Questo elemento viene omesso se non ci sono rimozioni.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p142">remove - A substructure detailing items to be removed from the endpoint set. Omitted if there are no removals.</span></span>
  - <span data-ttu-id="0b5a2-262">ips: gli elementi da rimuovere dalla matrice di indirizzi IP.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-262">ips - Items to be removed from the ips array.</span></span>
  - <span data-ttu-id="0b5a2-263">urls: gli elementi da rimuovere dalla matrice di URL.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-263">urls- Items to be removed from the urls array.</span></span>

### <a name="examples"></a><span data-ttu-id="0b5a2-264">**Esempi:**</span><span class="sxs-lookup"><span data-stu-id="0b5a2-264">**Examples:**</span></span>

<span data-ttu-id="0b5a2-265">URI della richiesta di esempio 1: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="0b5a2-265">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="0b5a2-p143">Richiede tutte le modifiche precedenti apportate all'istanza Worldwide del servizio di Office 365. Risultato dell'esempio:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p143">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="0b5a2-268">URI della richiesta di esempio 2: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="0b5a2-268">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="0b5a2-p144">Richiede le modifiche apportate all'istanza Worldwide di Office 365 a partire dalla versione specificata. In questo caso, la versione specificata è la più recente. Risultato dell'esempio:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p144">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

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

## <a name="example-powershell-script"></a><span data-ttu-id="0b5a2-272">**Script di PowerShell di esempio**</span><span class="sxs-lookup"><span data-stu-id="0b5a2-272">**Example PowerShell Script**</span></span>

<span data-ttu-id="0b5a2-p145">Di seguito è riportato uno script di PowerShell che è possibile eseguire per verificare se sono presenti azioni che è necessario effettuare per i dati aggiornati. Questo script controlla il numero di versione degli endpoint dell'istanza Worldwide di Office 365. Quando è presente una modifica, lo script scarica gli endpoint e li filtra per quelli di categoria &quot;Allow&quot; e &quot;Optimize&quot;. Inoltre, usa un ClientRequestId unico tra più chiamate e salva l'ultima versione trovata in un file temporaneo. È necessario chiamare questo script ogni ora per verificare la disponibilità di un aggiornamento della versione.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p145">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the &quot;Allow&quot; and &quot;Optimize&quot; category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="example-python-script"></a><span data-ttu-id="0b5a2-278">**Script di Python di esempio**</span><span class="sxs-lookup"><span data-stu-id="0b5a2-278">**Example Python Script**</span></span>

<span data-ttu-id="0b5a2-p146">Di seguito è riportato uno script di Python, testato con Python 3.6.3 su Windows 10, che è possibile eseguire per verificare se sono presenti azioni che è necessario effettuare per i dati aggiornati. Questo script controlla il numero di versione degli endpoint dell'istanza Worldwide di Office 365. Quando è presente una modifica, scarica gli endpoint e li filtra per quelli di categoria _Allow_ e _Optimize_. Inoltre, usa un ClientRequestId unico tra più chiamate e salva l'ultima versione trovata in un file temporaneo. È necessario chiamare questo script ogni ora per verificare la disponibilità di un aggiornamento della versione.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p146">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="web-service-interface-versioning"></a><span data-ttu-id="0b5a2-284">**Controllo delle versioni dell'interfaccia del servizio Web**</span><span class="sxs-lookup"><span data-stu-id="0b5a2-284">**Web Service interface versioning**</span></span>

<span data-ttu-id="0b5a2-p147">In futuro potrebbero essere richiesti aggiornamenti ai parametri o ai risultati di questi metodi del servizio Web. Dopo il rilascio della versione di disponibilità generale di questi servizi Web, Microsoft si impegnerà nel fornire avvisi preventivi in merito alla disponibilità di aggiornamenti dei materiali per il servizio Web. Quando Microsoft ritiene che un aggiornamento potrebbe richiedere modifiche per i client che usano il servizio Web, Microsoft mantiene la versione precedente del servizio Web disponibile per almeno dodici (12) mesi dopo il rilascio della nuova versione. I clienti che non eseguono l'aggiornamento durante questo periodo potrebbero non essere in grado di accedere al servizio Web e ai suoi metodi. I clienti devono assicurarsi che i client del servizio Web continuino a funzionare correttamente se le modifiche riportate di seguito vengono apportate alla firma per l'interfaccia del servizio Web:</span><span class="sxs-lookup"><span data-stu-id="0b5a2-p147">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="0b5a2-290">L'aggiunta di un nuovo parametro opzionale a un metodo Web esistente che non deve essere fornito dai client precedenti e che non influisce sul risultato ottenuto da un client precedente.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-290">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="0b5a2-291">L'aggiunta di un nuovo attributo denominato in una delle colonne aggiuntive o in uno degli elementi REST della risposta nel CSV di risposta.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-291">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="0b5a2-292">L'aggiunta di un nuovo metodo Web con un nuovo nome che non è chiamato dai client precedenti.</span><span class="sxs-lookup"><span data-stu-id="0b5a2-292">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="related-topics"></a><span data-ttu-id="0b5a2-293">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="0b5a2-293">Related Topics</span></span>
  
[<span data-ttu-id="0b5a2-294">URL e intervalli di indirizzi IP per Office 365</span><span class="sxs-lookup"><span data-stu-id="0b5a2-294">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="0b5a2-295">Domande frequenti sugli endpoint di Office 365</span><span class="sxs-lookup"><span data-stu-id="0b5a2-295">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[<span data-ttu-id="0b5a2-296">Principi della connettività di rete di Office 365</span><span class="sxs-lookup"><span data-stu-id="0b5a2-296">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="0b5a2-297">Ottimizzazione delle prestazioni e della rete di Office 365</span><span class="sxs-lookup"><span data-stu-id="0b5a2-297">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="0b5a2-298">Connettività di rete con Office 365</span><span class="sxs-lookup"><span data-stu-id="0b5a2-298">Network connectivity to Office 365</span></span>](network-connectivity.md)
  
[<span data-ttu-id="0b5a2-299">Qualità multimediale e prestazioni della connettività di rete in Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="0b5a2-299">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="0b5a2-300">Ottimizzazione della rete per Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="0b5a2-300">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[<span data-ttu-id="0b5a2-301">Ottimizzazione delle prestazioni di Office 365 mediante l'uso della cronologia delle prestazioni e delle previsioni</span><span class="sxs-lookup"><span data-stu-id="0b5a2-301">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="0b5a2-302">Piano di risoluzione dei problemi di prestazioni per Office 365</span><span class="sxs-lookup"><span data-stu-id="0b5a2-302">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
