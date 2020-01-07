---
title: Office 365 degli endpoint del servizio governativo degli Stati Uniti
ms.author: laurawi
author: LauraWi
manager: laurawi
ms.date: 01/02/2020
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
description: 'Riepilogo: Office 365 richiede la connettività a Internet. Gli endpoint seguenti devono essere raggiungibili per i clienti che utilizzano solo i piani di Office 365.'
hideEdit: true
ms.openlocfilehash: 3f603ceb8211a46dec43d5b06677b6a316b4fefa
ms.sourcegitcommit: f9888d1c27e38d3c489a0cbed7684a2e67c3afbd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/07/2020
ms.locfileid: "40951517"
---
# <a name="office-365-us-government-dod-endpoints"></a>Office 365 degli endpoint del servizio governativo degli Stati Uniti

*Si applica a: Office 365 admin*

 **Riepilogo:** Office 365 richiede la connettività a Internet. Gli endpoint seguenti devono essere raggiungibili per i clienti che utilizzano solo i piani di Office 365.
  
> [!NOTE]
> Microsoft ha rilasciato un servizio Web basato su REST per le voci FQDN e gli indirizzi IP in questa pagina. Questo nuovo servizio consente di configurare e aggiornare i dispositivi di rete perimetrale come firewall e server proxy. È possibile scaricare l'elenco degli endpoint, la versione corrente dell'elenco o modifiche specifiche. Questo servizio sostituisce il documento XML collegato da questa pagina, la quale è stata deprecata il 2 ottobre 2018. Per provare questo nuovo servizio, passare a [Servizio Web](office-365-ip-web-service.md).
  
 **Endpoint di Office 365:** [Worldwide (compreso GCC)](urls-and-ip-address-ranges.md) | [Office 365 gestito da 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Germany](office-365-germany-endpoints.md) | *Office 365 U.S. Government DoD* | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**Ultimo aggiornamento:** 01/02/2020- ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Change log Subscription](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**Download:** l'elenco completo in [formato JSON](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |
   
 Iniziare con la [gestione degli endpoint di Office 365](managing-office-365-endpoints.md) per comprendere i suggerimenti per la gestione della connettività di rete tramite questi dati. I dati degli endpoint vengono aggiornati all'inizio di ogni mese con i nuovi indirizzi IP e gli URL pubblicati 30 giorni prima di essere attivi. In questo modo i clienti che non dispongono ancora di aggiornamenti automatici consentono di completare i processi prima che sia necessaria una nuova connettività. Gli endpoint possono anche essere aggiornati nel corso del mese, se necessario, per risolvere le escalation del supporto, gli incidenti di sicurezza o altri requisiti operativi immediati. I dati visualizzati in questa pagina sono tutti generati dai servizi Web basati su REST. Se si utilizza uno script o un dispositivo di rete per accedere a questi dati, è consigliabile andare direttamente al [servizio Web](office-365-ip-web-service.md) .

Dati dell'endpoint riportati di seguito sono elencati i requisiti per la connettività dal computer di un utente a Office 365. Non include connessioni di rete da Microsoft in una rete di clienti, a volte denominate connessioni di rete ibride o in ingresso. Per ulteriori informazioni, vedere [endpoint aggiuntivi non inclusi nel servizio Web](additional-office365-ip-addresses-and-urls.md). 

Gli endpoint sono raggruppati in quattro aree del servizio. Le prime tre aree del servizio possono essere selezionate in modo indipendente per la connessione. La quarta area del servizio è una dipendenza comune (denominata Microsoft 365 Common e Office) e deve avere sempre la connessione di rete.

Le colonne di dati visualizzate sono le seguenti:

- **ID**: il numero ID della riga, noto anche come set di endpoint. Questo ID è uguale a quello restituito dal servizio Web per il set di endpoint.

- **Categoria**: indica se il set di endpoint è categorizzato come "Optimize", "Allow" o "Default". Sono disponibili informazioni su queste categorie e linee guida per la loro gestione nell'articolo [https://aka.ms/pnc](https://aka.ms/pnc). Inoltre, in questa colonna sono elencati i set di endpoint necessari per la connessione di rete. Per i set di endpoint non necessari per la connessione di rete, in questo campo sono fornite delle note che indicano quale funzionalità non sarebbe disponibile se il set di endpoint fosse bloccato. Se si esclude un'intera area del servizio, i set di endpoint elencati come necessari non richiedono la connessione.

- **Er**: **Sì** , se il set di endpoint è supportato su Azure ExpressRoute con i prefissi di route di Office 365. La community BGP che include i prefissi del percorso visualizzati è allineata all'area di servizio elencata. Quando ER è **No**, significa che ExpressRoute non è supportato per questo set di endpoint. Tuttavia, non si deve presumere che nessuna route sia annunciata per un set di endpoint in cui ER è **No**. Se si prevede di utilizzare Azure AD Connect, leggere la [sezione Considerazioni speciali](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) per assicurarsi di avere la configurazione di Azure ad Connect appropriata.

- **Indirizzi**: sono elencati i nomi di dominio completo (FQDN) o con caratteri jolly e gli intervalli di indirizzi IP per il set di endpoint. Tenere presente che un intervallo di indirizzi IP è in formato CIDR e potrebbe includere più indirizzi IP nella rete specificata.
 
- **Porte**: sono elencate le porte TCP o UDP combinate con gli indirizzi per formare l'endpoint di rete. Si potrebbero notare dei duplicati negli intervalli di indirizzi IP in cui sono presenti diverse porte.
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
Note per questa tabella:

- Il Centro sicurezza e conformità (SCC) fornisce il supporto per Azure ExpressRoute per Office 365. Lo stesso vale per molte caratteristiche esposte tramite il SCC, ad esempio Reporting, controllo, Advanced eDiscovery, Unified DLP e data governance. Due caratteristiche specifiche, l'importazione PST e l'esportazione di eDiscovery, attualmente non supportano Azure ExpressRoute con solo filtri di route di Office 365 a causa della loro dipendenza dall'archiviazione BLOB di Azure. Per utilizzare tali funzionalità, è necessaria una connettività separata per l'archiviazione BLOB di Azure utilizzando tutte le opzioni di connettività di Azure supportate, tra cui la connettività Internet o Azure ExpressRoute con i filtri di route pubblica di Azure. È necessario valutare la creazione di tale connettività per entrambe le caratteristiche. Il team di protezione delle informazioni di Office 365 è a conoscenza di questa limitazione ed è attivamente impegnato per portare il supporto per Azure ExpressRoute per Office 365 come limitato ai filtri di route di Office 365 per entrambe le caratteristiche.

- Sono disponibili ulteriori endpoint facoltativi per Office 365 ProPlus che non sono presenti nell'elenco e che non sono necessari agli utenti per avviare le applicazioni di Office 365 ProPlus e modificare i documenti. Gli endpoint facoltativi sono ospitati nei Data Center Microsoft e non elaborano, trasmettono o archiviano i dati dei clienti. È consigliabile che le connessioni utente a tali endpoint vengano indirizzate al perimetro di uscita Internet predefinito.
