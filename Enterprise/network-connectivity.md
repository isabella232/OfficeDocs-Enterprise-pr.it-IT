---
title: Connettività di rete con Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/01/2018
ms.audience: ITPro
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
description: Office 365 è progettato per consentire ai clienti in tutto il mondo per la connessione al servizio utilizzando una connessione internet. Con il servizio evoluzione, la sicurezza, prestazioni e affidabilità di Office 365 sono stati migliorati basata sui clienti che utilizzano internet per stabilire una connessione al servizio.
ms.openlocfilehash: da086aa3fcd23ccb4a82cde2a1f7d812c111071a
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "25911390"
---
# <a name="network-connectivity-to-office-365"></a>Connettività di rete con Office 365

Office 365 è progettato per consentire ai clienti in tutto il mondo per la connessione al servizio utilizzando una connessione internet. Con il servizio evoluzione, la sicurezza, prestazioni e affidabilità di Office 365 sono stati migliorati basata sui clienti che utilizzano internet per stabilire una connessione al servizio.
  
I clienti prevede di utilizzare Office 365 necessario valutare le esigenze di connettività internet previsti ed esistente come parte del progetto di distribuzione. Per le distribuzioni di classe enterprise affidabile e dimensione appropriata in connessione a internet è di utilizzo di funzionalità di Office 365 e gli scenari di fondamentale importanza.
  
Valutazioni di rete possono essere eseguite da molte diverse persone e organizzazioni in base alle dimensioni e preferenze dell'utente. L'ambito di rete della valutazione inoltre può variare a seconda di dove si è nel processo di distribuzione. Che consentono di ottenere una migliore comprensione delle necessario per eseguire una valutazione della rete, è stata generata una Guida alla valutazione di rete che consentono di acquisire familiarità con le opzioni disponibili per l'utente. Questa valutazione consente di determinare quali passaggi e le risorse devono essere aggiunti al progetto di distribuzione per consentire la corretta adottano Office 365.
  
Una valutazione completa di rete, come quelle indicate nella [Skype Operations Framework](https://www.skypeoperationsframework.com/) fornirà le possibili soluzioni a problemi di progettazione e i dettagli di implementazione di rete. La maggior parte delle valutazioni di rete indicherà la connettività di rete per Office 365 può essere sistemata in [configurazione secondarie o le modifiche di progettazione](https://aka.ms/manageo365endpoints) per l'infrastruttura dei servizi esterni internet e di rete esistenti.

Alcune valutazioni indicherà la connettività di rete per Office 365 richiederà ulteriori investimenti in componenti di rete. Ad esempio, a livello di larghezza di banda WAN o infrastruttura routing ottimizzata per supportare la connettività internet a Office 365. In alcuni casi una valutazione indicherà la connettività di rete per Office 365 è influenzata dalle disposizioni o le prestazioni requisiti per gli scenari, ad esempio [Skype per Business Online della qualità multimediale](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). Per gli investimenti in infrastruttura per la connettività internet, ottimizzazione routing e la connessione diretta specializzata possono causare questi requisiti aggiuntivi.
  
> [!NOTE]
> Autorizzazione di Microsoft è necessario utilizzare ExpressRoute per Office 365. Microsoft vengono esaminati ogni richiesta dei clienti e autorizza solo ExpressRoute per l'utilizzo di Office 365 quando i requisiti normativi del cliente impone la connessione diretta. Se si devono soddisfare questi requisiti, forniscono il collegamento testo estratto e web alla normativa che interpretare per indicare che è necessaria una connessione diretta in [ExpressRoute di modulo di richiesta di Office 365](https://aka.ms/O365ERReview) per iniziare una revisione di Microsoft. Sottoscrizioni non autorizzate tenta di creare filtri di route per Office 365 verranno visualizzato un [messaggio di errore](https://support.microsoft.com/kb/3181709).
  
I punti chiave da considerare quando si pianifica la valutazione della rete per Office 365:
  
- Office 365 è un servizio affidabile e high performance eseguito su internet. È continuano a investire per migliorare i seguenti aspetti del servizio. Tutti i servizi di Office 365 sono disponibili tramite la connessione a internet.

- Viene continuamente stiamo ottimizzazione core raggiungono gli aspetti di Office 365, ad esempio disponibilità, globale e la connettività di basato sulle prestazioni per internet. Molti servizi di Office 365, ad esempio, utilizzare un set di espansione dei nodi edge è connessa a internet. La rete perimetrale offre la massima prossimità e prestazioni per le connessioni in arrivo tramite internet.

- Quando si valutano la possibilità di utilizzare Office 365 per i servizi inclusi, ad esempio Skype per la funzionalità di Business Online vocali, video o riunione, i clienti devono eseguire una valutazione della rete end-to-end e soddisfare requisiti utilizzando il nostro Skype Operations Framework. Questi clienti avranno diverse opzioni per soddisfare requisiti specifici per la connettività cloud, tra cui ExpressRoute.

Dare uno sguardo sui case study di Microsoft [ottimizzazione delle prestazioni di rete per Microsoft Office 365](https://msdn.microsoft.com/en-us/library/mt450488.aspx). Se si sta valutando Office 365 e non sono assicurarsi che la posizione in cui iniziano con la valutazione della rete o hanno trovato struttura della rete richiede che per assistenza per superare il lavoro con il team di account Microsoft.
  
Inoltre, leggere l'argomento [Principi di connettività di rete di Office 365](https://aka.ms/o365networkingprinciples) per comprendere i principi di connettività per la gestione in modo sicuro il traffico di Office 365 e ottenere prestazioni ottimali. In questo articolo consentono di acquisire familiarità con le indicazioni più recenti per l'ottimizzazione in modo sicuro la connettività di rete di Office 365.
  
Questo è un collegamento breve è possibile utilizzare il ritorno: [ https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>Vedere anche

[Gestione degli endpoint di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Domande frequenti sugli endpoint di Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  
[Ottimizzazione delle prestazioni e della rete di Office 365](network-planning-and-performance.md)
  
[Azure ExpressRoute per Office 365](azure-expressroute.md)
  
[Routing con ExpressRoute per Office 365](routing-with-expressroute.md)
  
[Pianificazione della rete con ExpressRoute per Office 365](network-planning-with-expressroute.md)
  
[Uso delle community BGP in ExpressRoute per gli scenari di Office 365 (anteprima)](bgp-communities-in-expressroute.md)
  
[Qualità multimediale e prestazioni della connettività di rete in Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[URL e intervalli di indirizzi IP per Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Principi della connettività di rete di Office 365](https://aka.ms/o365networkingprinciples)
