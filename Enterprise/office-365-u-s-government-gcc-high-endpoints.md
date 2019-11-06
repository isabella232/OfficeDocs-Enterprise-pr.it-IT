---
title: Office 365 US Government High endpoint GCC
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/28/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: Se nell'organizzazione viene utilizzato Office 365 e i computer della rete vengono limitati dalla connessione a Internet, di seguito sono elencati gli endpoint (FQDN, porte, URL, IPv4 e gli intervalli di indirizzi IPv6) che devono essere inclusi negli elenchi in uscita consentiti per garantire la i computer possono utilizzare correttamente Office 365.
hideEdit: true
ms.openlocfilehash: 8ff4caf4c2fb3e067f3d0d23aed0be16fd099039
ms.sourcegitcommit: 8d1cc95b3641afe547c6d0e05f2dad5d013a0773
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2019
ms.locfileid: "37975858"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Office 365 US Government High endpoint GCC

 *Si applica a: Office 365 admin*

**Riepilogo:** Office 365 richiede la connettività a Internet. Gli endpoint seguenti devono essere raggiungibili per i clienti che usano solo i piani di Office 365 US Government High.
  
> [!NOTE]
> Microsoft ha rilasciato un servizio Web basato su REST per le voci FQDN e gli indirizzi IP in questa pagina. Questo nuovo servizio consente di configurare e aggiornare i dispositivi di rete perimetrale come firewall e server proxy. È possibile scaricare l'elenco degli endpoint, la versione corrente dell'elenco o modifiche specifiche. Questo servizio sostituisce il documento XML collegato da questa pagina, la quale è stata deprecata il 2 ottobre 2018. Per provare questo nuovo servizio, passare a [Servizio Web](office-365-ip-web-service.md).
  
 **Endpoint di Office 365:** [Worldwide (compreso GCC)](urls-and-ip-address-ranges.md) | [Office 365 gestito da 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Germany](office-365-germany-endpoints.md)  | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | *Office 365 U.S. Government GCC High* |
  
|||
|:-----|:-----|
|**Ultimo aggiornamento:** 28/10/2019 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Abbonamento al Log delle modifiche](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**Download:** l'elenco completo in [formato JSON](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |
   
 Iniziare con la [gestione degli endpoint di Office 365](managing-office-365-endpoints.md) per comprendere i suggerimenti per la gestione della connettività di rete tramite questi dati. I dati degli endpoint vengono aggiornati all'inizio di ogni mese con i nuovi indirizzi IP e gli URL pubblicati 30 giorni prima di essere attivi. In questo modo i clienti che non dispongono ancora di aggiornamenti automatici consentono di completare i processi prima che sia necessaria una nuova connettività. Gli endpoint possono anche essere aggiornati nel corso del mese, se necessario, per risolvere le escalation del supporto, gli incidenti di sicurezza o altri requisiti operativi immediati. I dati visualizzati in questa pagina sono tutti generati dai servizi Web basati su REST. Se si utilizza uno script o un dispositivo di rete per accedere a questi dati, è consigliabile andare direttamente al [servizio Web](office-365-ip-web-service.md) .

I dati degli endpoint riportati di seguito elencano i requisiti di connessione del computer di un utente a Office 365. Non sono incluse le connessioni di rete da Microsoft a una rete cliente, a volte chiamate connessioni di rete ibride o in ingresso.

Gli endpoint sono raggruppati in quattro aree del servizio. Le prime tre aree del servizio possono essere selezionate in modo indipendente per la connessione. La quarta area del servizio è una dipendenza comune (denominata Microsoft 365 Common e Office) e deve avere sempre la connessione di rete.

Le colonne di dati visualizzate sono le seguenti:

- **ID**: il numero ID della riga, noto anche come set di endpoint. Questo ID è uguale a quello restituito dal servizio Web per il set di endpoint.

- **Categoria**: indica se il set di endpoint è categorizzato come "Optimize", "Allow" o "Default". Sono disponibili informazioni su queste categorie e linee guida per la loro gestione nell'articolo [https://aka.ms/pnc](https://aka.ms/pnc). Inoltre, in questa colonna sono elencati i set di endpoint necessari per la connessione di rete. Per i set di endpoint non necessari per la connessione di rete, in questo campo sono fornite delle note che indicano quale funzionalità non sarebbe disponibile se il set di endpoint fosse bloccato. Se si esclude un'intera area del servizio, i set di endpoint elencati come necessari non richiedono la connessione.

- **Er**: **Sì** , se il set di endpoint è supportato su Azure ExpressRoute con i prefissi di route di Office 365. La community BGP che include i prefissi del percorso visualizzati è allineata all'area di servizio elencata. Quando ER è **No**, significa che ExpressRoute non è supportato per questo set di endpoint. Tuttavia, non si deve presumere che nessuna route sia annunciata per un set di endpoint in cui ER è **No**. Se si prevede di utilizzare Azure AD Connect, leggere la [sezione Considerazioni speciali](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud) per assicurarsi di avere la configurazione di Azure ad Connect appropriata.

- **Indirizzi**: sono elencati i nomi di dominio completo (FQDN) o con caratteri jolly e gli intervalli di indirizzi IP per il set di endpoint. Tenere presente che un intervallo di indirizzi IP è in formato CIDR e potrebbe includere più indirizzi IP nella rete specificata.
 
- **Porte**: sono elencate le porte TCP o UDP combinate con gli indirizzi per formare l'endpoint di rete. Si potrebbero notare dei duplicati negli intervalli di indirizzi IP in cui sono presenti diverse porte.
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

Note per questa tabella:

- Il Centro sicurezza e conformità (SCC) fornisce il supporto per Azure ExpressRoute per Office 365. Lo stesso vale per molte caratteristiche esposte tramite il SCC, ad esempio Reporting, controllo, Advanced eDiscovery, Unified DLP e data governance. Due caratteristiche specifiche, l'importazione PST e l'esportazione di eDiscovery, attualmente non supportano Azure ExpressRoute con solo filtri di route di Office 365 a causa della loro dipendenza dall'archiviazione BLOB di Azure. Per utilizzare tali funzionalità, è necessaria una connettività separata per l'archiviazione BLOB di Azure utilizzando tutte le opzioni di connettività di Azure supportate, tra cui la connettività Internet o Azure ExpressRoute con i filtri di route pubblica di Azure. È necessario valutare la creazione di tale connettività per entrambe le caratteristiche. Il team di protezione delle informazioni di Office 365 è a conoscenza di questa limitazione ed è attivamente impegnato per portare il supporto per Azure ExpressRoute per Office 365 come limitato ai filtri di route di Office 365 per entrambe le caratteristiche.

- Sono disponibili ulteriori endpoint facoltativi per Office 365 ProPlus che non sono presenti nell'elenco e che non sono necessari agli utenti per avviare le applicazioni di Office 365 ProPlus e modificare i documenti. Gli endpoint facoltativi sono ospitati nei Data Center Microsoft e non elaborano, trasmettono o archiviano i dati dei clienti. È consigliabile che le connessioni utente a tali endpoint vengano indirizzate al perimetro di uscita Internet predefinito.

