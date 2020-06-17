---
title: Office 365 degli endpoint del servizio governativo degli Stati Uniti
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/16/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: 5d7dce60-4892-4b58-b45e-ee42fe8a907f
f1.keywords:
- NOCSH
description: 'Riepilogo: Office 365 richiede la connettività a Internet. Gli endpoint seguenti devono essere raggiungibili per i clienti che utilizzano solo i piani di Office 365.'
hideEdit: true
ms.openlocfilehash: 7fc3f0919022903cc2b024b11e9ec17e84431bf0
ms.sourcegitcommit: f2a4b77c8c3932beb1a78bf2f5bf793fefb3fa49
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/16/2020
ms.locfileid: "44747402"
---
# <a name="office-365-us-government-dod-endpoints"></a>Office 365 degli endpoint del servizio governativo degli Stati Uniti

*Si applica a: Office 365 admin*

 **Riepilogo:** Office 365 richiede la connettività a Internet. Gli endpoint seguenti devono essere raggiungibili per i clienti che utilizzano solo i piani di Office 365.
  
> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
  
 **Endpoint di Office 365:** [Worldwide (compreso GCC)](urls-and-ip-address-ranges.md) | [Office 365 gestito da 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Germany](office-365-germany-endpoints.md) | *Office 365 U.S. Government DoD* | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**Ultimo aggiornamento:** 06/16/2020- ![ RSS ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Change log Subscription](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**Download:** l'elenco completo in [formato JSON](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |

 Iniziare con la [gestione degli endpoint di Office 365](managing-office-365-endpoints.md) per comprendere i suggerimenti per la gestione della connettività di rete tramite questi dati. I dati degli endpoint vengono aggiornati all'inizio di ogni mese con i nuovi indirizzi IP e gli URL pubblicati 30 giorni prima di essere attivi. In questo modo i clienti che non dispongono ancora di aggiornamenti automatici consentono di completare i processi prima che sia necessaria una nuova connettività. Gli endpoint possono anche essere aggiornati nel corso del mese, se necessario, per risolvere le escalation del supporto, gli incidenti di sicurezza o altri requisiti operativi immediati. I dati visualizzati in questa pagina sono tutti generati dai servizi Web basati su REST. Se si utilizza uno script o un dispositivo di rete per accedere a questi dati, è consigliabile andare direttamente al [servizio Web](office-365-ip-web-service.md) .

Dati dell'endpoint riportati di seguito sono elencati i requisiti per la connettività dal computer di un utente a Office 365. Non include connessioni di rete da Microsoft in una rete di clienti, a volte denominate connessioni di rete ibride o in ingresso. Per ulteriori informazioni, vedere [endpoint aggiuntivi non inclusi nel servizio Web](additional-office365-ip-addresses-and-urls.md). 

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

Le colonne di dati visualizzate sono le seguenti:

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **Er**: **Sì** , se il set di endpoint è supportato su Azure ExpressRoute con i prefissi di route di Office 365. La community BGP che include i prefissi del percorso visualizzati è allineata all'area di servizio elencata. Quando ER è **No**, significa che ExpressRoute non è supportato per questo set di endpoint. Tuttavia, non si deve presumere che nessuna route sia annunciata per un set di endpoint in cui ER è **No**. Se si prevede di utilizzare Azure AD Connect, leggere la [sezione Considerazioni speciali](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) per assicurarsi di avere la configurazione di Azure ad Connect appropriata.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
Note per questa tabella:

- Il Centro sicurezza e conformità (SCC) fornisce il supporto per Azure ExpressRoute per Office 365. Lo stesso vale per molte caratteristiche esposte tramite il SCC, ad esempio Reporting, controllo, Advanced eDiscovery, Unified DLP e data governance. Due caratteristiche specifiche, l'importazione PST e l'esportazione di eDiscovery, attualmente non supportano Azure ExpressRoute con solo filtri di route di Office 365 a causa della loro dipendenza dall'archiviazione BLOB di Azure. Per utilizzare tali funzionalità, è necessaria una connettività separata per l'archiviazione BLOB di Azure utilizzando tutte le opzioni di connettività di Azure supportate, tra cui la connettività Internet o Azure ExpressRoute con i filtri di route pubblica di Azure. È necessario valutare la creazione di tale connettività per entrambe le caratteristiche. Il team di protezione delle informazioni di Office 365 è a conoscenza di questa limitazione ed è attivamente impegnato per portare il supporto per Azure ExpressRoute per Office 365 come limitato ai filtri di route di Office 365 per entrambe le caratteristiche.

- Sono disponibili ulteriori endpoint facoltativi per le app Microsoft 365 per le aziende che non sono elencate e non sono necessarie per l'avvio delle app di Microsoft 365 per le applicazioni Enterprise e la modifica dei documenti. Gli endpoint facoltativi sono ospitati nei Data Center Microsoft e non elaborano, trasmettono o archiviano i dati dei clienti. È consigliabile che le connessioni utente a tali endpoint vengano indirizzate al perimetro di uscita Internet predefinito.
