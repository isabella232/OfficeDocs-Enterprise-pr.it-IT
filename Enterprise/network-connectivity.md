---
title: Connettività di rete a Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/01/2018
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
ms.openlocfilehash: 4510cb073c0fde64abc4ee796a55d7ef32662f8c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069872"
---
# <a name="network-connectivity-to-office-365"></a>Connettività di rete a Office 365

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
  
Ecco un breve collegamento che è possibile utilizzare per tornare: [ https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>Vedere anche

[Gestione degli endpoint di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Domande frequenti sugli endpoint di Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  
[Ottimizzazione delle prestazioni e della rete di Office 365](network-planning-and-performance.md)
  
[Azure ExpressRoute per Office 365](azure-expressroute.md)
  
[Routing con ExpressRoute per Office 365](routing-with-expressroute.md)
  
[Pianificazione della rete con ExpressRoute per Office 365](network-planning-with-expressroute.md)
  
[Utilizzo delle community BGP in ExpressRoute per gli scenari di Office 365 (anteprima)](bgp-communities-in-expressroute.md)
  
[Qualità multimediale e prestazioni della connettività di rete in Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[URL e intervalli di indirizzi IP per Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Principi della connettività di rete di Office 365](https://aka.ms/o365networkingprinciples)
