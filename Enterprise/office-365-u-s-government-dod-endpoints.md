---
title: Endpoint di Office 365 DoD gli Stati Uniti
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/11/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: 5d7dce60-4892-4b58-b45e-ee42fe8a907f
description: 'Riepilogo: Office 365 richiede la connettività a Internet. Endpoint riportata di seguito devono essere raggiungibili per i clienti che utilizzano solo i piani di Office 365 US Government DoD.'
hideEdit: true
ms.openlocfilehash: 3809298c012d41126271c3eec0981b5a6b7415c9
ms.sourcegitcommit: 79ffc3bfded032ee510b800426a0619e19e46915
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2019
ms.locfileid: "27896376"
---
# <a name="office-365-us-government-dod-endpoints"></a>Endpoint di Office 365 DoD gli Stati Uniti

*Si applica a: Amministrazione di Office 365*

 **Riepilogo:** Office 365 richiede la connettività a Internet. Endpoint riportata di seguito devono essere raggiungibili per i clienti che utilizzano solo i piani di Office 365 US Government DoD.
  
> [!NOTE]
> Microsoft ha rilasciato un servizio Web basato su REST per le voci FQDN e gli indirizzi IP in questa pagina. Questo nuovo servizio consente di configurare e aggiornare i dispositivi di rete perimetrale come firewall e server proxy. È possibile scaricare l'elenco degli endpoint, la versione corrente dell'elenco o modifiche specifiche. Questo servizio sostituisce il documento XML collegato da questa pagina, la quale è stata deprecata il 2 ottobre 2018. Per provare questo nuovo servizio, passare a [Servizio Web](office-365-ip-web-service.md).
  
 **Endpoint di Office 365:** [Worldwide (compreso GCC)](urls-and-ip-address-ranges.md) | [Office 365 gestito da 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Germany](office-365-germany-endpoints.md) | *Office 365 U.S. Government DoD* | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**Ultimo aggiornamento:** 01/11/2019 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [sottoscrizione registro modifiche](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**Download:** per un elenco completo nel [formato JSON](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |
   
 Iniziare con [gli endpoint di gestione di Office 365](managing-office-365-endpoints.md) acquisire familiarità con i suggerimenti per la gestione di connettività di rete con questi dati. Aggiornamento dei dati di endpoint all'inizio di ogni mese, nuovi indirizzi IP e gli URL pubblicati 30 giorni prima fase attiva. In tal modo gli utenti che hanno ancora non si dispongono automatica degli aggiornamenti per eseguire i processi prima è necessaria una nuova connessione. È anche possibile aggiornare gli endpoint nel corso del mese se necessari per la risoluzione di supporto, problemi di protezione o altri requisiti operativi immediati. I dati riportati in questa pagina riportata di seguito viene generati dai servizi web basato su REST. Se si utilizza un dispositivo di rete o di uno script di accedere a tali dati, deve accedere direttamente al [servizio Web](office-365-ip-web-service.md) .

I dati degli endpoint riportati di seguito elencano i requisiti di connessione del computer di un utente a Office 365. Non sono incluse le connessioni di rete da Microsoft a una rete cliente, a volte chiamate connessioni di rete ibride o in ingresso.

Gli endpoint sono raggruppati in quattro aree del servizio. Le prime tre aree del servizio possono essere selezionate in modo indipendente per la connessione. La quarta area del servizio è una dipendenza comune (denominata Microsoft 365 Common e Office Online) e deve avere sempre la connessione di rete.

Le colonne di dati visualizzate sono le seguenti:

- **ID**: il numero ID della riga, noto anche come set di endpoint. Questo ID è uguale a quello restituito dal servizio Web per il set di endpoint.

- **Categoria**: indica se il set di endpoint è categorizzato come "Optimize", "Allow" o "Default". Sono disponibili informazioni su queste categorie e linee guida per la loro gestione nell'articolo [http://aka.ms/pnc](http://aka.ms/pnc). Inoltre, in questa colonna sono elencati i set di endpoint necessari per la connessione di rete. Per i set di endpoint non necessari per la connessione di rete, in questo campo sono fornite delle note che indicano quale funzionalità non sarebbe disponibile se il set di endpoint fosse bloccato. Se si esclude un'intera area del servizio, i set di endpoint elencati come necessari non richiedono la connessione.

- **ER**: questo è **Sì** se il set di endpoint è supportato su Azure ExpressRoute con Office 365 route prefissi. Community BGP che include i prefissi route riportati risulti allineato con l'area servizio elencato. Una volta ER **No**, ciò significa che ExpressRoute non è supportato per questo set di endpoint. Tuttavia, è necessario non considerare che le route non sono annunciate per un set di endpoint dove ER è **No**. Se si prevede di utilizzare la connessione di Azure Active Directory, consultare la [sezione Considerazioni speciali](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud) per verificare di disporre di appropriata configurazione Connetti Azure Active Directory.

- **Indirizzi**: sono elencati i nomi di dominio completo (FQDN) o con caratteri jolly e gli intervalli di indirizzi IP per il set di endpoint. Tenere presente che un intervallo di indirizzi IP è in formato CIDR e potrebbe includere più indirizzi IP nella rete specificata.
 
- **Porte**: sono elencate le porte TCP o UDP combinate con gli indirizzi per formare l'endpoint di rete. Si potrebbero notare dei duplicati negli intervalli di indirizzi IP in cui sono presenti diverse porte.
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
Note per questa tabella:

- La sicurezza e conformità centro (SCC) fornisce supporto per ExpressRoute Azure per Office 365. Ciò vale anche per numerose funzionalità esposte tramite il controllo del codice sorgente, ad esempio report, controllo, eDiscovery avanzate, Unified DLP e Governance di dati. Le due funzionalità specifiche PST importazione ed esportazione, di eDiscovery attualmente non supportano ExpressRoute Azure con Office 365 solo i filtri route a causa del tipo di relazione in archiviazione Blob di Azure. Per l'utilizzo di tali funzionalità, è necessaria la connettività separata per archiviazione Blob Azure utilizzando le opzioni di connettività Azure supportato, che includono la connessione a Internet o ExpressRoute Azure Azure pubblica filtri di route. È necessario valutare stabilire quali la connettività per tali funzionalità. Il team di protezione di Office 365 informazioni è a conoscenza di questa limitazione e opera attivamente per inserire il supporto per ExpressRoute Azure per Office 365 come limitato ai filtri di route di Office 365 per tali funzionalità.

- Esistono altri endpoint facoltativo per Office 365 ProPlus che non sono elencati e non sono necessarie agli utenti di avviare le applicazioni di Office 365 ProPlus e modificare i documenti. Endpoint facoltativo ospitate nei data center Microsoft e non del processo di trasmettere o archiviare i dati dei clienti. È consigliabile che le connessioni utente a questi endpoint indirizzati al perimetro uscita Internet predefinito.
