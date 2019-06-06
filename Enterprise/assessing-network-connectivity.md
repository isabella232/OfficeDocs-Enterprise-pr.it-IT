---
title: Valutazione della connettività di rete di Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
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
ms.openlocfilehash: 3ea80ddccaf9fabbe158a10f0af1d35dbf3a9889
ms.sourcegitcommit: 0449c6f854c682719cac1bd0d086f2e3b20078b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "34724826"
---
# <a name="assessing-office-365-network-connectivity"></a>Valutazione della connettività di rete di Office 365

Office 365 è stato creato per consentire ai clienti di tutto il mondo di connettersi al servizio tramite una connessione Internet. Man mano che il servizio si evolve, la sicurezza, le prestazioni e l'affidabilità di Office 365 sono migliorate in base ai clienti che utilizzano Internet per stabilire una connessione al servizio.
  
I clienti che pianificano l'utilizzo di Office 365 devono valutare le esigenze di connettività Internet esistenti e previste come parte del progetto di distribuzione. Per le distribuzioni di classi Enterprise la connettività Internet affidabile e di dimensioni appropriate è una parte importante dell'utilizzo delle funzionalità e degli scenari di Office 365.
  
Le valutazioni di rete possono essere eseguite da molte persone e organizzazioni diverse in base alle dimensioni e alle preferenze. L'ambito di rete della valutazione può anche variare a seconda della posizione del processo di distribuzione. Per ottenere maggiori informazioni sulle operazioni necessarie per eseguire una valutazione della rete, è stata creata una guida di valutazione della rete che consente di comprendere le opzioni disponibili per l'utente. Questa valutazione determinerà i passaggi e le risorse che devono essere aggiunti al progetto di distribuzione per consentire di adottare correttamente Office 365.
  
Una valutazione globale della rete, come quelle prescritte in [Skype Operations Framework](https://www.skypeoperationsframework.com/) , fornirà le possibili soluzioni per le sfide di progettazione della rete insieme ai dettagli sull'implementazione. La maggior parte delle valutazioni di rete indicherà che la connettività di rete a Office 365 può essere adattata con [modifiche alla configurazione o alla progettazione secondarie](https://aka.ms/manageo365endpoints) all'infrastruttura di rete e di uscita Internet esistente.

Alcune valutazioni indicheranno che la connettività di rete a Office 365 richiederà ulteriori investimenti nei componenti di rete. Ad esempio, gli investimenti in larghezza di banda WAN o infrastruttura di routing ottimizzata per supportare la connettività Internet a Office 365. Ogni tanto una valutazione indicherà che la connettività di rete a Office 365 è influenzata dai requisiti di regolamentazione o prestazioni per scenari come la [qualità multimediale di Skype for business online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). Questi requisiti aggiuntivi possono comportare investimenti in infrastruttura di connettività Internet, ottimizzazione del routing e connettività diretta specializzata.
  
> [!NOTE]
> È necessaria l'autorizzazione Microsoft per l'utilizzo di ExpressRoute per Office 365. Microsoft esamina tutte le richieste dei clienti e autorizza ExpressRoute per l'utilizzo di Office 365 solo quando il requisito normativo del cliente delega la connettività diretta. Se si dispone di tali requisiti, fornire l'Estratto di testo e il collegamento Web al regolamento che si intende interpretare per indicare che la connettività diretta è necessaria nel [modulo di richiesta di ExpressRoute per Office 365](https://aka.ms/O365ERReview) per avviare una revisione Microsoft. Gli abbonamenti non autorizzati che tentano di creare filtri di route per Office 365 riceveranno un [messaggio di errore](https://support.microsoft.com/kb/3181709).
  
Punti chiave da prendere in considerazione durante la pianificazione della valutazione della rete per Office 365:
  
- Office 365 è un servizio sicuro, affidabile e ad alte prestazioni che viene eseguito su Internet pubblico. Continuiamo a investire per migliorare questi aspetti del servizio. Tutti i servizi di Office 365 sono disponibili tramite connettività Internet.

- Vengono continuamente ottimizzati gli aspetti principali di Office 365, ad esempio la disponibilità, la portata globale e le prestazioni per la connettività basata su Internet. Ad esempio, molti servizi di Office 365 sfruttano un insieme di nodi perimetrali Internet in espansione. Questa rete Edge offre le migliori caratteristiche di prossimità e prestazioni alle connessioni provenienti da Internet.

- Quando si considera l'utilizzo di Office 365 per uno qualsiasi dei servizi inclusi, come Skype for business online Voice, video o meeting capabilities, i clienti devono terminare la valutazione della rete finale e soddisfare i requisiti utilizzando Skype Operations Framework. Questi clienti avranno diverse opzioni per soddisfare requisiti specifici per la connettività cloud, tra cui ExpressRoute.

Esaminare il case study di Microsoft [per ottimizzare le prestazioni di rete per Microsoft Office 365](https://msdn.microsoft.com/en-us/library/mt450488.aspx). Se si sta valutando Office 365 e non si è certi di dove iniziare con la valutazione della rete o si sono verificati problemi di progettazione della rete per i quali è necessario un intervento di assistenza da superare, è possibile collaborare con il team dell'account Microsoft.
  
Leggere inoltre i [principi di connettività di rete di office 365](https://aka.ms/o365networkingprinciples) per comprendere i principi di connettività per la gestione sicura del traffico di Office 365 e ottenere le migliori prestazioni possibili. In questo articolo vengono fornite informazioni utili per comprendere le indicazioni più recenti per ottimizzare in modo sicuro la connettività di rete di Office 365.

## <a name="the-office-365-network-onboarding-tool"></a>Strumento di onboarding di rete di Office 365

È possibile utilizzare lo strumento di onboarding di [rete di Office 365](https://aka.ms/netonboard), un nuovo strumento di proof of Concept (POC), per eseguire test di connettività di base che forniscono indicazioni specifiche sui miglioramenti della connettività di rete che possono essere effettuati tra una determinata posizione utente e Office 365.

Lo strumento di onboarding di rete esegue le operazioni seguenti:

- Rileva la posizione oppure è possibile specificare una posizione in cui eseguire il test
- Verifica la posizione dell'uscita di rete
- Verifica il percorso di rete per il portello anteriore del servizio Office 365 più vicino

Lo strumento Visualizza le informazioni seguenti:

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

È possibile leggere informazioni sulla versione di Office 365 Network onboarding Tool e fornire commenti e suggerimenti in [office 365 Network Performance Tool poc Release](https://techcommunity.microsoft.com/t5/Office-365-Networking/Office-365-Network-Performance-tool-POC-release/m-p/319579#M102) post del Blog. Informazioni sugli aggiornamenti futuri di questo strumento e di altri aggiornamenti di rete di Office 365 verranno inviati al Blog di [rete di office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) .
  
Ecco un breve collegamento che è possibile utilizzare per tornare: [ https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>Vedere anche

[Panoramica della connettività di rete di Office 365](office-365-networking-overview.md)

[Principi della connettività di rete di Office 365](https://aka.ms/o365networkingprinciples)

[Gestione degli endpoint di Office 365](managing-office-365-endpoints.md)

[URL e intervalli di indirizzi IP per Office 365](urls-and-ip-address-ranges.md)

[Servizio Web per URL e indirizzi IP di Office 365](office-365-ip-web-service.md)

[Ottimizzazione delle prestazioni e della rete di Office 365](network-planning-and-performance.md)
