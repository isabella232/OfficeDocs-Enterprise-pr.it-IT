---
title: Servizio Web per URL e indirizzi IP di Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/1/2019
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
ms.openlocfilehash: af1ff6f222d4d9563116c4173ebeca9ca9f4470d
ms.sourcegitcommit: 3b5597cab55bc67890fd6c760102efce513be87b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/01/2019
ms.locfileid: "33512682"
---
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="1d2b8-104">Servizio Web per URL e indirizzi IP di Office 365</span><span class="sxs-lookup"><span data-stu-id="1d2b8-104">Office 365 IP Address and URL Web service</span></span>

<span data-ttu-id="1d2b8-p102">Per identificare e differenziare meglio il traffico di rete di Office 365, un nuovo servizio Web pubblica gli endpoint di Office 365, consentendo agli utenti di valutare, configurare e rimanere aggiornati con le ultime modifiche. Questo nuovo servizio Web sostituisce i file scaricabili XML attualmente disponibili. Il formato XML verrà ritirato il 2 ottobre 2018.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p102">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service replaces the XML downloadable files that are currently available. The XML format is planned to be phased out on October 2, 2018.</span></span>

<span data-ttu-id="1d2b8-p103">Un cliente o un fornitore di dispositivi di rete perimetrale può sfruttare il nuovo servizio Web basato su REST per voci FQDN e indirizzi IP di Office 365. È possibile accedere ai dati direttamente in un browser Web tramite questi URL.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p103">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries. You can access the data directly in a web browser using these URLs.</span></span>

- <span data-ttu-id="1d2b8-110">Per la versione più recente degli URL e degli intervalli di indirizzi IP di Office 365, usare [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="1d2b8-110">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="1d2b8-111">Per i dati sulla pagina degli URL e degli intervalli di indirizzi IP di Office 365 per firewall e server proxy, usare [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="1d2b8-111">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="1d2b8-112">Per ottenere tutte le ultime modifiche apportate dalla fine di luglio 2018, quando il servizio Web ha iniziato a essere disponibile, usare [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="1d2b8-112">To get all the latest changes since the end of July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="1d2b8-113">Un cliente può utilizzare questo servizio Web per le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-113">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="1d2b8-114">Aggiornare gli script di PowerShell per ottenere i dati degli endpoint di Office 365 e modificare la formattazione dei dispositivi di rete in uso.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-114">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="1d2b8-115">Usare queste informazioni per aggiornare i file PAC distribuiti ai computer client.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-115">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="1d2b8-116">Un fornitore di dispositivi di rete perimetrale può utilizzare questo servizio Web per le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-116">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="1d2b8-117">Creare e testare il software dei dispositivi per scaricare l'elenco per la configurazione automatizzata.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-117">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="1d2b8-118">Verificare la versione corrente.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-118">Check for the current version.</span></span>
- <span data-ttu-id="1d2b8-119">Conoscere le modifiche apportate.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-119">Get the current changes.</span></span>

> [!NOTE]
> <span data-ttu-id="1d2b8-120">Se si usa Azure ExpressRoute per connettersi a Office 365, vedere [Azure ExpressRoute per Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute) per acquisire familiarità con i servizi di Office 365 supportati su Azure ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-120">If you are using Azure ExpressRoute to connect to Office 365, please review [Azure ExpressRoute for Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute) to familiarize yourself with the Office 365 services supported over Azure ExpressRoute.</span></span> <span data-ttu-id="1d2b8-121">Per comprendere quali richieste di rete per le applicazioni di Office 365 richiedono la connettività Internet, vedere l'articolo [URL e intervalli di indirizzi IP di Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).</span><span class="sxs-lookup"><span data-stu-id="1d2b8-121">Also review the article [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) to understand which network requests for Office 365 applications require Internet connectivity.</span></span> <span data-ttu-id="1d2b8-122">Queste precauzioni consentiranno di migliorare la configurazione dei dispositivi di protezione perimetrale.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-122">This will help to better configure your perimeter security devices.</span></span>

<span data-ttu-id="1d2b8-123">Per ulteriori informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-123">For additional information, see:</span></span>

- [<span data-ttu-id="1d2b8-124">Post di blog dell'annuncio nel forum della community IT di Office 365</span><span class="sxs-lookup"><span data-stu-id="1d2b8-124">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [<span data-ttu-id="1d2b8-125">Forum della community IT di Office 365 per domande sull'uso dei servizi Web</span><span class="sxs-lookup"><span data-stu-id="1d2b8-125">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a><span data-ttu-id="1d2b8-126">Parametri comuni</span><span class="sxs-lookup"><span data-stu-id="1d2b8-126">Common parameters</span></span>

<span data-ttu-id="1d2b8-127">Questi parametri sono comuni a tutti i metodi di servizio Web:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-127">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="1d2b8-128">**formato = < JSON | CSV >** - Per impostazione predefinita il formato dei dati restituiti è JSON.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-128">**format=<JSON | CSV>** - By default, the returned data format is JSON.</span></span> <span data-ttu-id="1d2b8-129">Questo parametro facoltativo consente di restituire i dati con valori delimitati da virgole (CSV).</span><span class="sxs-lookup"><span data-stu-id="1d2b8-129">Use this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="1d2b8-130">**ClientRequestId =\<guid >** - GUID necessario creato per l'associazione di client.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-130">**ClientRequestId=\<guid>** - A required GUID that you generate for client association.</span></span> <span data-ttu-id="1d2b8-131">È necessario generare un GUID per ogni macchina collegata al servizio web.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-131">You should generate a GUID for each machine that calls the web service.</span></span> <span data-ttu-id="1d2b8-132">Non usare i GUID illustrati negli esempi seguenti perché si potrebbe essere bloccati dal servizio web in futuro.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-132">Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future.</span></span> <span data-ttu-id="1d2b8-133">Il formato GUID è _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, dove x rappresenta un numero esadecimale.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-133">GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number.</span></span> <span data-ttu-id="1d2b8-134">Per generare un GUID, usare il comando [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-134">To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span>

## <a name="version-web-method"></a><span data-ttu-id="1d2b8-135">Metodo per la versione web</span><span class="sxs-lookup"><span data-stu-id="1d2b8-135">Version web method</span></span>

<span data-ttu-id="1d2b8-p107">Microsoft aggiorna le voci FQDN e gli indirizzi IP di Office 365 alla fine di ogni mese e occasionalmente per requisiti operativi o relativi al supporto. Ai dati di ciascuna istanza pubblicata viene assegnato un numero di versione. Il metodo Web per la versione consente di verificare l'ultima versione per ogni istanza del servizio di Office 365. È consigliabile controllare la versione ogni giorno o, al massimo, ogni ora. Le nuove versioni sono previste all'inizio di ogni mese. A volte, a causa di richieste di assistenza, aspetti legati alla sicurezza o altri requisiti operativi, sono disponibili nuove versioni durante il mese.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p107">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly. New versions should be expected at the start of each month. Sometimes due to support incident, security, or other operational requirements there will be new versions during the month.</span></span>

<span data-ttu-id="1d2b8-142">I parametri per il metodo per la versione web sono:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-142">Parameters for the version web method are:</span></span>

- <span data-ttu-id="1d2b8-143">**Completaversioni = < true | False >** - Per impostazione predefinita la versione restituita è la più recente.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-143">**AllVersions=<true | false>** - By default, the version returned is the latest.</span></span> <span data-ttu-id="1d2b8-144">Includere questo parametro facoltativo per richiedere tutte le versioni pubblicate dopo il primo rilascio del servizio web.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-144">Include this optional parameter to request all published versions since the web service was first released.</span></span>
- <span data-ttu-id="1d2b8-145">**Format=< JSON | CSV | RSS >**, oltre ai formati JSON e CSV, la versione metodo web supporta inoltre RSS.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-145">**Format=<JSON | CSV | RSS>** – In addition to the JSON and CSV formats, the version web method also supports RSS.</span></span> <span data-ttu-id="1d2b8-146">È possibile usare questo parametro facoltativo con _AllVersions=true_ per richiedere un feed RSS che può essere usato con Outlook o altri lettori RSS.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-146">Format=JSON  CSV  RSS – In addition to the JSON and CSV formats, the version web method also supports RSS. You can use this along with the allVersions=true parameter to request an RSS feed which can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="1d2b8-147">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>**: questo parametro facoltativo specifica l'istanza per ripristinare la versione.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-147">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - This optional parameter specifies the instance to return the version for.</span></span> <span data-ttu-id="1d2b8-148">Se omesso, vengono restituite tutte le istanze.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-148">If MaxColumns is omitted, all the results are returned.</span></span> <span data-ttu-id="1d2b8-149">Le istanze valide sono: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-149">Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="1d2b8-p111">Il metodo Web per la versione non ha limiti di frequenza e non restituisce mai codici di risposta HTTP 429. La risposta al metodo Web per la versione include un’intestazione di controllo cache che consiglia la memorizzazione dei dati nella cache per un'ora. Il risultato del metodo Web per la versione può essere un singolo record o una matrice di record. Gli elementi di ogni record sono:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p111">The version web method is not rate limited and does not ever return 429 HTTP Response Codes. The response to the version web method does include a cache-control header recommending caching of the data for 1 hour. The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>

- <span data-ttu-id="1d2b8-154">instance: il nome breve dell'istanza del servizio di Office 365.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-154">instance - The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="1d2b8-155">latest: l'ultima versione degli endpoint dell'istanza specificata.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-155">latest - The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="1d2b8-p112">versions: un elenco di tutte le versioni precedenti dell'istanza specificata. Questo elemento è incluso solo se il parametro AllVersions è true.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p112">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>

<span data-ttu-id="1d2b8-p113">È possibile utilizzare Microsoft Flow per ricevere notifiche di posta elettronica delle modifiche agli URL e agli indirizzi IP. Vedere l'articolo sull'[uso di Microsoft Flow per ricevere un'e-mail per le modifiche agli URL e agli indirizzi IP di Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p113">You can use Microsoft Flow to get email notifications of changes to the IP Addresses and URLs. See [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span></span>

### <a name="examples"></a><span data-ttu-id="1d2b8-160">Esempi:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-160">Examples:</span></span>

<span data-ttu-id="1d2b8-161">URI della richiesta di esempio 1: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="1d2b8-161">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="1d2b8-p114">Questo URI restituisce l'ultima versione di ogni istanza del servizio di Office 365. Risultato dell'esempio:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p114">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

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

> [!IMPORTANT]
> <span data-ttu-id="1d2b8-p115">Il GUID del parametro ClientRequestID in questi URI è solo un esempio. Per provare gli URI del servizio Web, generare il proprio GUID. I GUID mostrati in questi esempi potrebbero essere bloccati dal servizio Web in futuro.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p115">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="1d2b8-167">URI della richiesta di esempio 2: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="1d2b8-167">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="1d2b8-p116">Questo URI restituisce l'ultima versione dell'istanza del servizio di Office 365 specificata. Risultato dell'esempio:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p116">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}

```

<span data-ttu-id="1d2b8-170">URI della richiesta di esempio 3: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="1d2b8-170">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="1d2b8-p117">Questo URI mostra l'output in formato CSV. Risultato dell'esempio:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p117">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="1d2b8-173">URI della richiesta di esempio 4: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="1d2b8-173">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="1d2b8-p118">Questo URI mostra tutte le versioni precedenti che sono state pubblicate per l'istanza Worldwide del servizio di Office 365. Risultato dell'esempio:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p118">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="1d2b8-176">URI del feed RSS di esempio 5: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="1d2b8-176">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="1d2b8-p119">Questo URI mostra un feed RSS delle versioni pubblicate che includono collegamenti all'elenco di modifiche di ogni versione. Risultato dell'esempio:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p119">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

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

## <a name="endpoints-web-method"></a><span data-ttu-id="1d2b8-179">Metodo Web per gli endpoint</span><span class="sxs-lookup"><span data-stu-id="1d2b8-179">Endpoints web method</span></span>

<span data-ttu-id="1d2b8-180">Il metodo web per gli endpoint restituisce tutti i record per intervalli di indirizzi IP e URL del servizio Office 365.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-180">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service.</span></span> <span data-ttu-id="1d2b8-181">Anche se i dati più recenti dal metodo web per gli endpoint dovrebbe essere utilizzato per la configurazione di dispositivi di rete, i dati possono essere memorizzati fino a 30 giorni dopo la sua pubblicazione grazie alla notifica di preavviso disponibile per le aggiunte.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-181">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service. While the latest data from the endpoints web method should be used for network device configuration, the data can be cached for up to 30 days after it is published due to the advance notice provided for additions. We recommend you only call the endpoints web method again when the version web method indicates a new version of the data is available. Parameters for the endpoints web method are:</span></span> <span data-ttu-id="1d2b8-182">È consigliabile chiamare il metodo web per gli endpoint solo quando la versione metodo web indica che è disponibile una nuova versione dei dati.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-182">We recommend you only call the endpoints web method again when the version web method indicates a new version of the data is available.</span></span>

<span data-ttu-id="1d2b8-183">I parametri per il metodo web per gli endpoint sono:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-183">Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="1d2b8-184">**ServiceAreas = < comuni | Exchange | SharePoint | Skype >**, un elenco delle aree di servizio separato da virgole.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-184">**ServiceAreas=<Common | Exchange | SharePoint | Skype>** - A comma-separated list of service areas.</span></span> <span data-ttu-id="1d2b8-185">Sono validi _Common_, _Exchange_, _SharePoint_ e _Skype_.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-185">Valid items are _Common_, _Exchange_, _SharePoint_, and _Skype_.</span></span> <span data-ttu-id="1d2b8-186">Poiché gli elementi dell’area di servizio di Common sono un prerequisito per tutte le altre aree di servizio, il servizio web li includerà sempre.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-186">Because Common service area items are a prerequisite for all other service areas, the web service will always include them.</span></span> <span data-ttu-id="1d2b8-187">Se non si include questo parametro, tutte le aree del servizio vengono restituite.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-187">If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="1d2b8-188">**TenantName=< tenant_name >** - Nome tenant di Office 365.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-188">**TenantName=<tenant_name>** - Your Office 365 tenant name.</span></span> <span data-ttu-id="1d2b8-189">Il servizio web prende il nome specificato e lo inserisce in parti dell'URL che includono il nome del tenant.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-189">TenantName - Query string parameter. Your Office 365 tenant name. The web service takes your provided name and inserts it in parts of URLs that include the tenant name. If you don't provide a tenant name, those parts of URLs have the wildcard character ().</span></span> <span data-ttu-id="1d2b8-190">Se non si specifica alcun nome tenant, tali parti dell'URL avranno il carattere jolly (\*).</span><span class="sxs-lookup"><span data-stu-id="1d2b8-190">If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="1d2b8-191">**NoIPv6=<true | false>**: Impostare questo parametro su true per escludere gli indirizzi IPv6 dall'output, ad esempio, se non si usa il protocollo IPv6 nella propria rete.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-191">**NoIPv6** - Query string parameter. Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="1d2b8-192">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>**. Questo parametro obbligatorio specifica l'istanza per cui restituire gli endpoint.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-192">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - This required parameter specifies the instance to return the endpoints for.</span></span> <span data-ttu-id="1d2b8-193">Le istanze valide sono: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-193">Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="1d2b8-194">Se si chiama il metodo Web per gli endpoint molte volte dallo stesso indirizzo IP client, si potrebbe ricevere il codice di risposta HTTP 429 (Troppe richieste).</span><span class="sxs-lookup"><span data-stu-id="1d2b8-194">If you call the endpoints web method a large number of times from the same client IP address, you may receive HTTP response code 429 (Too Many Requests).</span></span> <span data-ttu-id="1d2b8-195">La maggior parte degli utenti non lo vedranno.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-195">Most people will never see this.</span></span> <span data-ttu-id="1d2b8-196">Se viene visualizzato questo codice di risposta, attendere un'ora prima di ripetere la richiesta.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-196">If you get this response code, wait 1 hour before repeating your request.</span></span> <span data-ttu-id="1d2b8-197">Pianificare la chiamata del metodo Web per gli endpoint solo quando la versione metodo Web indica che è disponibile una nuova versione dei dati.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-197">Plan to only call the endpoints web method when the version web method indicates there is a new version available.</span></span>

<span data-ttu-id="1d2b8-p125">Il risultato ottenuto dal metodo Web per gli endpoint è una matrice di record in cui ogni record rappresenta un set di endpoint. Gli elementi per ogni record sono:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p125">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>

- <span data-ttu-id="1d2b8-200">id: il numero ID non modificabile del set di endpoint.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-200">id - The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="1d2b8-201">serviceArea: l'area del servizio di cui fa parte: Common, Exchange, SharePoint o Skype.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-201">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
- <span data-ttu-id="1d2b8-p126">urls: gli URL per il set di endpoint. Una matrice JSON di record DNS. Questo elemento viene omesso se non specificato.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p126">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
- <span data-ttu-id="1d2b8-p127">tcpPorts: le porte TCP per il set di endpoint. Tutti gli elementi delle porte sono formattati come elenco con valori separati da virgole di porte o intervalli di porte separati da un trattino (-). Le porte si applicano a tutti gli URL e indirizzi IP nel set di endpoint per quella categoria. Questo elemento viene omesso se non specificato.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p127">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
- <span data-ttu-id="1d2b8-p128">udpPorts: le porte UDP degli intervalli di indirizzi IP nel set di endpoint. Questo elemento viene omesso se non specificato.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p128">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
- <span data-ttu-id="1d2b8-p129">ips: gli intervalli di indirizzi IP associati al set di endpoint come associati alle porte UDP o TCP elencate. Una matrice JSON di intervalli di indirizzi IP. Questo elemento viene omesso se non specificato.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p129">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. A JSON array of IP Address ranges. Omitted if blank.</span></span>
- <span data-ttu-id="1d2b8-p130">categoria: la categoria di connettività per il set di endpoint. I valori validi sono Optimize, Allow e Default. Se si usano i dati di endpoint per cercare la categoria di un indirizzo IP o un URL, è possibile che la query restituisca più categorie. Esistono alcuni motivi per cui potrebbe verificarsi. In questi casi è necessario seguire i suggerimenti per la categoria con priorità più alta. Ad esempio, se viene visualizzato un endpoint sia su Optimize sia su Allow, seguire i requisiti per Optimize. Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p130">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. If using the endpoint data to search for the category of an IP Address or URL, it is possible that your query may return multiple categories. There are a few reasons why that may happen. In these cases you should follow the recommendations for the highest priority category. For example, if the endpoint appears in both Optimize and Allow, you should follow the requirements for Optimize. Required.</span></span>
- <span data-ttu-id="1d2b8-221">expressRoute: True o False se il set di endpoint sfrutta la connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-221">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
- <span data-ttu-id="1d2b8-p131">required: True se il set di endpoint deve avere una connettività per Office 365 che sia supportata. False se il set di endpoint è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p131">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. False if this endpoint set is optional.</span></span>
- <span data-ttu-id="1d2b8-p132">notes: per gli endpoint facoltativi, questo testo descrive la funzionalità di Office 365 che non sarà presente se gli URL o gli indirizzi IP nel set di endpoint non sono accessibili al livello della rete. Questo elemento viene omesso se non specificato.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p132">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="1d2b8-226">Esempi:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-226">Examples:</span></span>

<span data-ttu-id="1d2b8-227">URI della richiesta di esempio 1: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="1d2b8-227">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="1d2b8-p133">Questo URI ottiene tutti gli endpoint per l'istanza Worldwide di Office 365 per tutti i carichi di lavoro. Risultato dell'esempio che mostra un estratto dell'output:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p133">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>

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
```

<span data-ttu-id="1d2b8-230">In questo esempio non sono inclusi altri set di endpoint.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-230">Additional endpoint sets are not included in this example.</span></span>

<span data-ttu-id="1d2b8-231">URI della richiesta di esempio 2: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="1d2b8-231">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="1d2b8-232">In questo esempio si ottengono gli endpoint per l'istanza Worldwide di Office 365 solo per Exchange Online e le dipendenze.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-232">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="1d2b8-233">L'output dell'esempio 2 è simile a quello dell'esempio 1, ad eccezione del fatto che i risultati non includono endpoint per SharePoint Online o Skype for Business Online.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-233">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="1d2b8-234">Metodo Web per le modifiche</span><span class="sxs-lookup"><span data-stu-id="1d2b8-234">Changes web method</span></span>

<span data-ttu-id="1d2b8-p134">Il metodo Web per le modifiche restituisce gli aggiornamenti più recenti che sono stati pubblicati. In genere, si tratta delle modifiche del mese precedente apportate agli URL e agli intervalli di indirizzi IP. Le modifiche più importanti da elaborare riguardano l'aggiunta di nuovi URL o indirizzi IP: infatti, se non è stato possibile aggiungere un indirizzo IP a un elenco di controllo di accesso al firewall o un URL a un elenco di server proxy da ignorare, può verificarsi un'interruzione del servizio per gli utenti di Office 365 che usano il relativo dispositivo di rete. Nonostante i requisiti operativi, le operazioni _Add_ vengono aggiunte con un preavviso di 30 giorni prima che si verifichi tale interruzione del servizio.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p134">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs. The most critical changes to be processed are when new URLs or IP Addresses are added since failing to add an IP Address to a firewall access control list, or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device. Notwithstanding operational requirements, _Add_ operations are added with 30 days' notice before such an outage would occur.</span></span>

<span data-ttu-id="1d2b8-239">Il parametro obbligatorio del metodo Web per le modifiche è il seguente:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-239">The parameter for the changes web method is:</span></span>

- <span data-ttu-id="1d2b8-240">**Versione =\<AAAAMMGGNN>** - Parametro di route URL obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-240">**Version=\<YYYYMMDDNN>** - Required URL route parameter.</span></span> <span data-ttu-id="1d2b8-241">Questo valore deve corrispondere alla versione attualmente implementata.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-241">This value should be the version that you have currently implemented.</span></span> <span data-ttu-id="1d2b8-242">Il servizio Web restituisce le modifiche apportate dopo tale versione.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-242">The web service will return the changes since that version.</span></span> <span data-ttu-id="1d2b8-243">Il formato è _AAAAMMGGNN_, dove _NN_ sono zeri.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-243">The format is _YYYYMMDDNN_, where _NN_ are zeros.</span></span> <span data-ttu-id="1d2b8-244">Il servizio Web richiede che questo parametro contenga esattamente 10 cifre.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-244">The web service requires this parameter to contain exactly 10 digits.</span></span>

<span data-ttu-id="1d2b8-245">Il metodo Web per le modifiche ha frequenza limitata, allo stesso modo del metodo Web per gli endpoint.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-245">The changes web method is rate limited in the same way as the endpoints web method. If you receive a 429 HTTP Response Code then you should wait 1 hour before calling again.</span></span> <span data-ttu-id="1d2b8-246">Se viene visualizzato il codice di risposta 429 HTTP, attendere un'ora prima di ripetere la richiesta.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-246">If you receive a 429 HTTP response code, wait 1 hour before repeating your request.</span></span>

<span data-ttu-id="1d2b8-p137">Il risultato ottenuto dal metodo Web per le modifiche è una matrice di record in cui ogni record rappresenta una modifica in una versione specifica degli endpoint. Gli elementi per ogni record sono:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p137">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>

- <span data-ttu-id="1d2b8-249">id: l'ID non modificabile del record della modifica.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-249">id - The immutable id of the change record.</span></span>
- <span data-ttu-id="1d2b8-250">endpointSetId: l'ID del record del set di endpoint cui è stata apportata la modifica.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-250">endpointSetId - The ID of the endpoint set record that is changed. Required.</span></span>
- <span data-ttu-id="1d2b8-251">disposition: può trattarsi di una modifica, un'aggiunta o una rimozione e descrive l'effetto della modifica apportata sul record del set di endpoint.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-251">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record. Required.</span></span>
- <span data-ttu-id="1d2b8-p138">impact: non tutte le modifiche avranno la stessa importanza per ogni ambiente. Descrive l'impatto previsto per un ambiente di rete perimetrale dell’organizzazione in seguito a questa modifica. Questo attributo è incluso solo nei record di modifica della versione 2018112800 e versioni successive. Le opzioni di impact sono:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p138">impact - Not all changes will be equally important to every environment. This describes the expected impact to an enterprise network perimeter environment as a result of this change. This attribute is included only in change records of version 2018112800 and later. Options for the impact are:</span></span>
  - <span data-ttu-id="1d2b8-p139">AddedIp: un indirizzo IP è stato aggiunto a Office 365 e sarà presto live nel servizio. Rappresenta una modifica che è necessario impostare in un firewall o un altro dispositivo di rete perimetrale di livello 3. Se non si aggiunge prima che iniziamo a usarlo, potrebbe verificarsi un'interruzione del servizio.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p139">AddedIp – An IP Address was added to Office 365 and will be live on the service soon. This represents a change you need to take on a firewall or other layer 3 network perimeter device. If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="1d2b8-259">AddedUrl: un URL è stato aggiunto a Office 365 e sarà presto live nel servizio.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-259">AddedUrl – A URL was added to Office 365 and will be live on the service soon.</span></span> <span data-ttu-id="1d2b8-260">Rappresenta una modifica da eseguire in un server proxy o in un dispositivo di rete perimetrale per analisi URL.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-260">This represents a change you need to take on a proxy server or URL parsing network perimeter device.</span></span> <span data-ttu-id="1d2b8-261">Se non si aggiunge prima che iniziamo a usarlo, può verificarsi un'interruzione del servizio.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-261">If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="1d2b8-p141">AddedIpAndUrl: sono stati aggiunti sia un indirizzo IP sia un URL. Rappresenta una modifica da eseguire su un dispositivo firewall di livello 3, un server proxy o un dispositivo di analisi di URL. Se non si aggiunge prima che iniziamo a usarlo, potrebbe verificarsi un'interruzione del servizio.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p141">AddedIpAndUrl - Both an IP Address and a URL were added. This represents a change you need to take on either a firewall layer 3 device or a proxy server or URL parsing device. If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="1d2b8-p142">RemovedIpOrUrl: da Office 365 è stato rimosso almeno un indirizzo IP o un URL. È consigliabile rimuovere gli endpoint di rete dai dispositivi perimetrali, ma non c'è nessuna scadenza per eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p142">RemovedIpOrUrl – At least one IP Address or URL was removed from Office 365. You should remove the network endpoints from your perimeter devices, but there’s no deadline for you to do this.</span></span>
  - <span data-ttu-id="1d2b8-p143">ChangedIsExpressRoute: l'attributo di supporto ExpressRoute è stato modificato. Se si utilizza ExpressRoute potrebbe essere necessario intervenire in base alla configurazione.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p143">ChangedIsExpressRoute – The ExpressRoute support attribute was changed. If you use ExpressRoute then you may need to take action depending on your configuration.</span></span>
  - <span data-ttu-id="1d2b8-p144">MovedIpOrUrl: abbiamo spostato un indirizzo IP o un Url da questo set di endpoint a un altro. In genere, non è necessario alcun intervento.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p144">MovedIpOrUrl – We moved an IP Address or Url between this endpoint set and another one. Generally no action is required.</span></span>
  - <span data-ttu-id="1d2b8-p145">RemovedDuplicateIpOrUrl: abbiamo rimosso un indirizzo IP o URL duplicato ma questo è ancora pubblicato per Office 365. In genere, non è necessario alcun intervento.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p145">RemovedDuplicateIpOrUrl – We removed a duplicate IP Address or Url but it’s still published for Office 365. Generally no action is required.</span></span>
  - <span data-ttu-id="1d2b8-273">OtherNonPriorityChanges: abbiamo modificato qualcosa di meno critico rispetto a tutte le altre opzioni, ad esempio un campo della nota</span><span class="sxs-lookup"><span data-stu-id="1d2b8-273">OtherNonPriorityChanges – We changed something less critical than all of the other options like a note field</span></span>
- <span data-ttu-id="1d2b8-p146">version: la versione del set di endpoint pubblicato in cui è stata introdotta la modifica. I numeri di versione hanno il formato _YYYYMMDDNN_, dove NN è un numero naturale incrementato se sono presenti più versioni da pubblicare in un unico giorno.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p146">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format _YYYYMMDDNN_, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="1d2b8-276">previous: una sottostruttura che descrive dettagliatamente i valori precedenti degli elementi modificati nel set di endpoint.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-276">previous - A substructure detailing previous values of changed elements on the endpoint set. This will not be included for newly added endpoint sets. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span> <span data-ttu-id="1d2b8-277">Non sarà inclusa per i set di endpoint appena aggiunti.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-277">This will not be included for newly added endpoint sets.</span></span> <span data-ttu-id="1d2b8-278">Include _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ e _notes_.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-278">Includes  _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="1d2b8-279">current: una sottostruttura che descrive dettagliatamente i valori aggiornati degli elementi di modifica nel set di endpoint.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-279">current - A substructure detailing updated values of changes elements on the endpoint set. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span> <span data-ttu-id="1d2b8-280">Include _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ e _notes_.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-280">Includes _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="1d2b8-p149">add: una sottostruttura che descrive nel dettaglio gli elementi da aggiungere alle raccolte dei set di endpoint. Questo elemento viene omesso se non ci sono aggiunte.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p149">add - A substructure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
  - <span data-ttu-id="1d2b8-283">effectiveDate: definisce la data in cui le aggiunte saranno effettive nel servizio.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-283">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
  - <span data-ttu-id="1d2b8-284">ips: gli elementi da aggiungere alla matrice di _indirizzi IP_.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-284">ips - Items to be added to the ips array.</span></span>
  - <span data-ttu-id="1d2b8-285">urls: gli elementi da aggiungere alla matrice di _urls_.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-285">urls- Items to be added to the urls array.</span></span>
- <span data-ttu-id="1d2b8-286">remove: una sottostruttura che descrive nel dettaglio gli elementi da rimuovere dal set di endpoint.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-286">remove - A substructure detailing items to be removed from the endpoint set. Omitted if there are no removals.</span></span> <span data-ttu-id="1d2b8-287">Questo elemento viene omesso se non ci sono rimozioni.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-287">Omitted if there are no removals.</span></span>
  - <span data-ttu-id="1d2b8-288">ips: gli elementi da rimuovere dalla matrice di _indirizzi IP_.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-288">ips - Items to be removed from the ips array.</span></span>
  - <span data-ttu-id="1d2b8-289">urls: gli elementi da rimuovere dalla matrice di _URL_.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-289">urls- Items to be removed from the urls array.</span></span>

### <a name="examples"></a><span data-ttu-id="1d2b8-290">Esempi:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-290">Examples:</span></span>

<span data-ttu-id="1d2b8-291">URI della richiesta di esempio 1: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="1d2b8-291">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="1d2b8-p151">Richiede tutte le modifiche precedenti apportate all'istanza Worldwide del servizio di Office 365. Risultato dell'esempio:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p151">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

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
```

<span data-ttu-id="1d2b8-294">URI della richiesta di esempio 2: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="1d2b8-294">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="1d2b8-p152">Richiede le modifiche apportate all'istanza Worldwide di Office 365 a partire dalla versione specificata. In questo caso, la versione specificata è la più recente. Risultato dell'esempio:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p152">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

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

## <a name="example-powershell-script"></a><span data-ttu-id="1d2b8-298">Script di PowerShell di esempio</span><span class="sxs-lookup"><span data-stu-id="1d2b8-298">Example PowerShell Script</span></span>

<span data-ttu-id="1d2b8-299">Ecco uno script di PowerShell da eseguire per verificare se esistono attività da eseguire per ottenere dati aggiornati.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-299">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data.</span></span> <span data-ttu-id="1d2b8-300">Questo script controlla il numero di versione degli endpoint dell’istanza di Office 365 Worldwidex.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-300">This script checks the version number for the Office 365 Worldwide instance endpoints.</span></span> <span data-ttu-id="1d2b8-301">Quando viene apportata una modifica, verranno scaricati gli endpoint e i filtri per gli endpoint di categoria "Consenti" e "Ottimizza".</span><span class="sxs-lookup"><span data-stu-id="1d2b8-301">When there is a change, it downloads the endpoints and filters for the "Allow" and "Optimize" category endpoints.</span></span> <span data-ttu-id="1d2b8-302">Si utilizza anche un unico_ClientRequestId_ per più chiamate e consente di salvare la versione più recente disponibile in un file temporaneo.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-302">It also uses a unique _ClientRequestId_ across multiple calls and saves the latest version found in a temporary file.</span></span> <span data-ttu-id="1d2b8-303">Per eseguire un aggiornamento della versione, è necessario chiamare lo script una volta all'ora.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-303">You should call this script once an hour to check for a version update.</span></span>

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

## <a name="example-python-script"></a><span data-ttu-id="1d2b8-304">Script di Python di esempio</span><span class="sxs-lookup"><span data-stu-id="1d2b8-304">Example Python Script</span></span>

<span data-ttu-id="1d2b8-p154">Di seguito è riportato uno script di Python, testato con Python 3.6.3 su Windows 10, che è possibile eseguire per verificare se sono presenti azioni che è necessario effettuare per i dati aggiornati. Questo script controlla il numero di versione degli endpoint dell'istanza Worldwide di Office 365. Quando è presente una modifica, scarica gli endpoint e li filtra per quelli di categoria _Allow_ e _Optimize_. Inoltre, usa un ClientRequestId unico tra più chiamate e salva l'ultima versione trovata in un file temporaneo. È necessario chiamare questo script ogni ora per verificare la disponibilità di un aggiornamento della versione.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p154">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="web-service-interface-versioning"></a><span data-ttu-id="1d2b8-310">Controllo delle versioni dell'interfaccia del servizio Web</span><span class="sxs-lookup"><span data-stu-id="1d2b8-310">Web Service interface versioning</span></span>

<span data-ttu-id="1d2b8-p155">In futuro potrebbero essere richiesti aggiornamenti ai parametri o ai risultati di questi metodi del servizio Web. Dopo il rilascio della versione di disponibilità generale di questi servizi Web, Microsoft si impegnerà nel fornire avvisi preventivi in merito alla disponibilità di aggiornamenti dei materiali per il servizio Web. Quando Microsoft ritiene che un aggiornamento potrebbe richiedere modifiche per i client che usano il servizio Web, Microsoft mantiene la versione precedente del servizio Web disponibile per almeno dodici (12) mesi dopo il rilascio della nuova versione. I clienti che non eseguono l'aggiornamento durante questo periodo potrebbero non essere in grado di accedere al servizio Web e ai suoi metodi. I clienti devono assicurarsi che i client del servizio Web continuino a funzionare correttamente se le modifiche riportate di seguito vengono apportate alla firma per l'interfaccia del servizio Web:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-p155">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="1d2b8-316">L'aggiunta di un nuovo parametro opzionale a un metodo Web esistente che non deve essere fornito dai client precedenti e che non influisce sul risultato ottenuto da un client precedente.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-316">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="1d2b8-317">L'aggiunta di un nuovo attributo denominato in una delle colonne aggiuntive o in uno degli elementi REST della risposta nel CSV di risposta.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-317">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="1d2b8-318">L'aggiunta di un nuovo metodo Web con un nuovo nome che non è chiamato dai client precedenti.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-318">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="office-365-endpoint-functions-module"></a><span data-ttu-id="1d2b8-319">Modulo di funzioni di Endpoint di Office 365</span><span class="sxs-lookup"><span data-stu-id="1d2b8-319">Office 365 Endpoint Functions Module</span></span>

<span data-ttu-id="1d2b8-320">Microsoft ospita un servizio REST per ottenere l'URI più nuovo e recente per i servizi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-320">Microsoft is hosting a REST Service to get the newest and latest URI for the Office 365 services.</span></span>  <span data-ttu-id="1d2b8-321">Per poter usare l'URI come raccolta, è possibile utilizzare questo modulo con alcuni cmdlet utili.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-321">To be able to use the URI as a collection, you can use this module with a few helpful cmdlets.</span></span>

### <a name="calling-the-rest-service"></a><span data-ttu-id="1d2b8-322">Chiamare il servizio REST</span><span class="sxs-lookup"><span data-stu-id="1d2b8-322">Calling the REST service</span></span>

<span data-ttu-id="1d2b8-323">Per usare questo modulo, è sufficiente copiare il file del modulo [O365EndpointFunctions.psm1](https://github.com/samurai-ka/PS-Module-O365EndpointService/blob/master/O365EndpointFunctions.psm1) in un punto qualsiasi del disco rigido e importarlo direttamente con questo comando:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-323">To use this module, simply copy the module file [O365EndpointFunctions.psm1](https://github.com/samurai-ka/PS-Module-O365EndpointService/blob/master/O365EndpointFunctions.psm1) somewhere on your hard disk and import it directly with this command:</span></span>

```powershell
    Import-Module O365EndpointFunctions.psm1
```

<span data-ttu-id="1d2b8-324">Dopo avere importato il modulo, sarà possibile chiamare il servizio REST.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-324">After you have imported the module, you will be able to call the REST service.</span></span> <span data-ttu-id="1d2b8-325">L'URI sarà restituito come una raccolta che può essere elaborata direttamente in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-325">This will return the URI as a collection that you can now process in PowerShell directly.</span></span> <span data-ttu-id="1d2b8-326">È necessario immettere il nome del tenant di Office 365, come descritto in questo comando:</span><span class="sxs-lookup"><span data-stu-id="1d2b8-326">You must enter the name of your Office 365 tenant, as described in the following command:</span></span>

```powershell
    Invoke-O365EnpointService -tenantName [Name of your tenant]
```

> [!NOTE]
> <span data-ttu-id="1d2b8-327">Il cmdlet va digitato in questo modo **Invoke-O365EnpointService**, senza lettera _d_.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-327">The cmdlet is spelled **Invoke-O365EnpointService**, with no letter _d_.</span></span> <span data-ttu-id="1d2b8-328">Non è un errore di digitazione.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-328">This is not a typographical error.</span></span>

#### <a name="parameters"></a><span data-ttu-id="1d2b8-329">Parametri</span><span class="sxs-lookup"><span data-stu-id="1d2b8-329">Parameters</span></span>

- <span data-ttu-id="1d2b8-330">**tenantName** - il nome del tenant di Office 365.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-330">**tenantName** - The name of your Office 365 tenant.</span></span> <span data-ttu-id="1d2b8-331">Questo parametro è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-331">This parameter is mandatory.</span></span>
- <span data-ttu-id="1d2b8-332">**ForceLatest** - questa opzione obbligherà le API REST a restituire l'intero elenco di URI più recente.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-332">**ForceLatest** -This switch will force the REST API to always return the entire list of the latest URI.</span></span>
- <span data-ttu-id="1d2b8-333">**IPv6** - restituisce il parametro e gli indirizzi IPv6.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-333">**IPv6** -This switch will return the IPv6 addresses as well.</span></span> <span data-ttu-id="1d2b8-334">Verrà restituito solo IPv4 come predefinito.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-334">As default only IPv4 will be returned.</span></span>

### <a name="examples"></a><span data-ttu-id="1d2b8-335">Esempi</span><span class="sxs-lookup"><span data-stu-id="1d2b8-335">Examples</span></span>

<span data-ttu-id="1d2b8-336">Restituire l'elenco completo di tutti gli URI, inclusi gli indirizzi IPv6</span><span class="sxs-lookup"><span data-stu-id="1d2b8-336">Return the complete list of all URIs including the IPv6 addresses</span></span>

```powershell
    Invoke-O365EnpointService -tenantName [Name of your tenant] -ForceLatest -IPv6 | Format-Table -AutoSize
```

<span data-ttu-id="1d2b8-337">Restituire solo gli indirizzi IP per il servizio Exchange Online</span><span class="sxs-lookup"><span data-stu-id="1d2b8-337">Return only the IP addresses for Exchange Online Service</span></span>

```powershell
    Invoke-O365EnpointService -tenantName [Name of your tenant] -ForceLatest | where{($_.serviceArea -eq "Exchange") -and ($_.protocol -eq "ip")}| Format-Table -AutoSize
```

### <a name="exporting-a-proxy-pac-file"></a><span data-ttu-id="1d2b8-338">Esportare un file PAC Proxy</span><span class="sxs-lookup"><span data-stu-id="1d2b8-338">Exporting a Proxy PAC file</span></span>

<span data-ttu-id="1d2b8-339">È possibile utilizzare questo modulo per creare un file PAC Proxy.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-339">You can use this module to create a Proxy PAC file.</span></span> <span data-ttu-id="1d2b8-340">In questo esempio si ottengono in primo luogo gli endpoint, quindi si filtrano i risultati per selezionare gli URL.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-340">In this example you first get the endpoints and filter the result to select the URLs.</span></span> <span data-ttu-id="1d2b8-341">Tali URL vengono reindirizzati per l’esportazione.</span><span class="sxs-lookup"><span data-stu-id="1d2b8-341">These URLs are piped to be exported.</span></span>  

```powershell
 Invoke-O365EnpointService -tenantName [Name of your tenant] -ForceLatest | where{($_.Protocol -eq "Url") -and (($_.Category -eq "Optimize") -or ($_.category -eq "Allow"))} | select uri -Unique | Export-O365ProxyPacFile
```

## <a name="related-topics"></a><span data-ttu-id="1d2b8-342">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="1d2b8-342">Related Topics</span></span>
  
[<span data-ttu-id="1d2b8-343">URL e intervalli di indirizzi IP per Office 365</span><span class="sxs-lookup"><span data-stu-id="1d2b8-343">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="1d2b8-344">Domande frequenti sugli endpoint di Office 365</span><span class="sxs-lookup"><span data-stu-id="1d2b8-344">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[<span data-ttu-id="1d2b8-345">Principi della connettività di rete di Office 365</span><span class="sxs-lookup"><span data-stu-id="1d2b8-345">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="1d2b8-346">Ottimizzazione delle prestazioni e della rete di Office 365</span><span class="sxs-lookup"><span data-stu-id="1d2b8-346">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="1d2b8-347">Connettività di rete con Office 365</span><span class="sxs-lookup"><span data-stu-id="1d2b8-347">Network connectivity to Office 365</span></span>](network-connectivity.md)
  
[<span data-ttu-id="1d2b8-348">Qualità multimediale e prestazioni della connettività di rete in Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="1d2b8-348">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="1d2b8-349">Ottimizzazione della rete per Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="1d2b8-349">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[<span data-ttu-id="1d2b8-350">Ottimizzazione delle prestazioni di Office 365 mediante l'uso della cronologia delle prestazioni e delle previsioni</span><span class="sxs-lookup"><span data-stu-id="1d2b8-350">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="1d2b8-351">Piano di risoluzione dei problemi di prestazioni per Office 365</span><span class="sxs-lookup"><span data-stu-id="1d2b8-351">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
