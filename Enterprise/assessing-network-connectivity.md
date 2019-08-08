---
title: Valutazione della connettività di rete di Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/7/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Office 365 è stato creato per consentire ai clienti di tutto il mondo di connettersi al servizio tramite una connessione Internet. Man mano che il servizio si evolve, la sicurezza, le prestazioni e l'affidabilità di Office 365 sono migliorate in base ai clienti che utilizzano Internet per stabilire una connessione al servizio.
ms.openlocfilehash: 884c4c0d510de55da4125a3e3b80b4bd869ec697
ms.sourcegitcommit: c207aafc126a495e700552796ed89da3de254910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/07/2019
ms.locfileid: "36233426"
---
# <a name="assessing-office-365-network-connectivity"></a>Valutazione della connettività di rete di Office 365

Office 365 è stato creato per consentire ai clienti di tutto il mondo di connettersi al servizio tramite una connessione Internet. Man mano che il servizio si evolve, la sicurezza, le prestazioni e l'affidabilità di Office 365 sono migliorate in base ai clienti che utilizzano Internet per stabilire una connessione al servizio.
  
I clienti che pianificano l'utilizzo di Office 365 devono valutare le esigenze di connettività Internet esistenti e previste come parte del progetto di distribuzione. Per le distribuzioni di classi Enterprise la connettività Internet affidabile e di dimensioni appropriate è una parte importante dell'utilizzo delle funzionalità e degli scenari di Office 365.
  
Le valutazioni di rete possono essere eseguite da molte persone e organizzazioni diverse in base alle dimensioni e alle preferenze. L'ambito di rete della valutazione può anche variare a seconda della posizione del processo di distribuzione. Per ottenere maggiori informazioni sulle operazioni necessarie per eseguire una valutazione della rete, è stata creata una guida di valutazione della rete che consente di comprendere le opzioni disponibili per l'utente. Questa valutazione determinerà i passaggi e le risorse che devono essere aggiunti al progetto di distribuzione per consentire di adottare correttamente Office 365.
  
Una valutazione globale della rete fornirà le possibili soluzioni alle sfide di progettazione della rete insieme ai dettagli sull'implementazione. Alcune valutazioni di rete indicano che la connettività di rete ottimale a Office 365 può essere adattata con modifiche di configurazione o di progettazione secondarie all'infrastruttura di rete e di uscita Internet esistente.

Alcune valutazioni indicheranno che la connettività di rete a Office 365 richiederà ulteriori investimenti nei componenti di rete. Ad esempio, le reti aziendali che interessano succursali e più aree geografiche possono richiedere investimenti in soluzioni SD-WAN o infrastruttura di routing ottimizzata per supportare la connettività Internet a Office 365. Ogni tanto una valutazione indicherà che la connettività di rete a Office 365 è influenzata dai requisiti di regolamentazione o prestazioni per scenari come la [qualità multimediale di Skype for business online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). Questi requisiti aggiuntivi possono comportare investimenti in infrastruttura di connettività Internet, ottimizzazione del routing e connettività diretta specializzata.

Alcune risorse utili per valutare la rete:

- Vedere [office 365 Network Connectivity Overview](office-365-networking-overview.md) per informazioni concettuali sulla rete di Office 365.
- Vedere i [principi di connettività di rete di office 365](https://aka.ms/o365networkingprinciples) per comprendere i principi di connettività per la gestione sicura del traffico di Office 365 e ottenere le migliori prestazioni possibili.
- Iscriversi a [Microsoft FastTrack](https://www.microsoft.com/en-us/fasttrack) per assistenza guidata per la pianificazione, la progettazione e la distribuzione di Office 365. 
- Vedere la sezione [office 365 Network onboarding Tool](assessing-network-connectivity.md#the-office-365-network-onboarding-tool) seguente per eseguire test di connettività di base che forniscono indicazioni specifiche sui miglioramenti della connettività di rete che possono essere effettuati tra una determinata posizione utente e Office 365.

> [!NOTE]
> È necessaria l'autorizzazione Microsoft per l'utilizzo di ExpressRoute per Office 365. Microsoft esamina tutte le richieste dei clienti e autorizza ExpressRoute per l'utilizzo di Office 365 solo quando il requisito normativo del cliente delega la connettività diretta. Se si dispone di tali requisiti, fornire l'Estratto di testo e il collegamento Web al regolamento che si intende interpretare per indicare che la connettività diretta è necessaria nel [modulo di richiesta di ExpressRoute per Office 365](https://aka.ms/O365ERReview) per avviare una revisione Microsoft. Gli abbonamenti non autorizzati che tentano di creare filtri di route per Office 365 riceveranno un [messaggio di errore](https://support.microsoft.com/kb/3181709).
  
Punti chiave da prendere in considerazione durante la pianificazione della valutazione della rete per Office 365:
  
- Office 365 è un servizio sicuro, affidabile e ad alte prestazioni che viene eseguito su Internet pubblico. Continuiamo a investire per migliorare questi aspetti del servizio. Tutti i servizi di Office 365 sono disponibili tramite connettività Internet.

- Vengono continuamente ottimizzati gli aspetti principali di Office 365, ad esempio la disponibilità, la portata globale e le prestazioni per la connettività basata su Internet. Ad esempio, molti servizi di Office 365 sfruttano un insieme di nodi perimetrali Internet in espansione. Questa rete Edge offre le migliori caratteristiche di prossimità e prestazioni alle connessioni provenienti da Internet.

- Quando si considera l'utilizzo di Office 365 per uno qualsiasi dei servizi inclusi, ad esempio teams o funzionalità di riunione, video o riunioni di Skype for business online, i clienti devono terminare la valutazione della rete finale e soddisfare i requisiti di connettività tramite [Microsoft FastTrack](https://www.microsoft.com/en-us/fasttrack).

Se si sta valutando Office 365 e non si è certi di dove iniziare con la valutazione della rete o si sono verificati problemi di progettazione della rete per i quali è necessario un intervento di assistenza da superare, è possibile collaborare con il team dell'account Microsoft.

## <a name="the-office-365-network-onboarding-tool"></a>Strumento di onboarding di rete di Office 365

[Office 365 Network onboarding Tool](https://aka.ms/netonboard) è uno strumento di valutazione della rete di proof of Concept (POC) che esegue i test di connettività di base sul tenant di Office 365 e rende specifiche indicazioni sulla progettazione della rete per ottimizzare le prestazioni di Office 365. Lo strumento evidenzia le scelte di progettazione del perimetro della rete aziendale di grandi dimensioni utili per la Web Browsing Internet, ma ha un impatto sulle prestazioni di applicazioni SaaS di grandi dimensioni, ad esempio Office 365.

Lo strumento di onboarding di rete esegue le operazioni seguenti:

- Rileva la posizione oppure è possibile specificare una posizione in cui eseguire il test
- Verifica la posizione dell'uscita di rete
- Verifica il percorso di rete per il portello anteriore del servizio Office 365 più vicino
- Fornisce test avanzati tramite un'applicazione scaricabile di Windows 10 che rende le indicazioni relative alla progettazione della rete perimetrale correlate ai server proxy, ai firewall e al DNS. Lo strumento esegue anche test delle prestazioni per Skype for business online, Microsoft teams, SharePoint Online e Exchange Online.

Lo strumento dispone di due componenti: un'interfaccia utente basata su browser che raccoglie informazioni di connettività di base e un'applicazione di Windows 10 scaricabile che esegue test avanzati e restituisce ulteriori dati di valutazione.

Lo strumento basato su browser Visualizza le informazioni seguenti:

- Scheda risultati e impatto
  - La posizione in una mappa della porta di ingresso del servizio in uso
  - La posizione in una mappa di altre porte anteriori del servizio che forniscono una connettività ottimale
  - Prestazioni relative rispetto ad altri clienti di Office 365 vicino a te
- Scheda dettagli e soluzioni
  - Posizione dell'utente in base alla città e al paese
  - Posizione di uscita di rete per città, stato e paese
  - Utente per la distanza di uscita dalla rete
  - Posizione della porta principale del servizio Exchange Online di Office 365
  - Optimal Office 365 Exchange Online Service porta anteriore (s) per la posizione dell'utente
  - Clienti nell'area metropolitana con prestazioni migliori

L'applicazione scaricabile test avanzati fornisce le seguenti informazioni aggiuntive:

- Scheda dettagli e soluzioni (aggiunta)
  - Gateway predefinito dell'utente
  - Server DNS client
  - Resolver ricorsivo DNS client
  - Server DNS Exchange Online
  - Server DNS di SharePoint Online
  - Identificazione del server proxy
  - Verifica della connettività multimediale
  - Perdita di pacchetti di qualità multimediale
  - Latenza qualità multimediale
  - Instabilità della qualità multimediale
  - Riordino dei pacchetti di qualità multimediale
- Test di connettività a più endpoint specifici delle funzionalità
- Diagnostica percorso di rete che include i dati di tracert e latenza per i servizi di Exchange Online, SharePoint Online e teams

È possibile leggere informazioni sullo strumento di onboarding di rete di Office 365 e fornire commenti e suggerimenti per l' [aggiornamento di office 365 Network onboarding Tool poc con New Network Design raccomandazioni](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130) post di Blog. Informazioni sugli aggiornamenti futuri di questo strumento e di altri aggiornamenti di rete di Office 365 verranno inviati al Blog di [rete di office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) .
  
Ecco un breve collegamento che è possibile utilizzare per tornare: [ https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>Vedere anche

[Panoramica della connettività di rete di Office 365](office-365-networking-overview.md)

[Principi della connettività di rete di Office 365](https://aka.ms/o365networkingprinciples)

[Gestione degli endpoint di Office 365](managing-office-365-endpoints.md)

[URL e intervalli di indirizzi IP per Office 365](urls-and-ip-address-ranges.md)

[Servizio Web per URL e indirizzi IP di Office 365](office-365-ip-web-service.md)

[Ottimizzazione delle prestazioni e della rete di Office 365](network-planning-and-performance.md)
