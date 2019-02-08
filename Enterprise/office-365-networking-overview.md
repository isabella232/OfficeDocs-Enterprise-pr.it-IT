---
title: Panoramica di connettività di rete Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/12/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Viene descritta la perché è importante per i servizi SaaS, l'obiettivo della rete di Office 365, ottimizzazione della rete e modalità SaaS richiede una rete diversa da altri carichi di lavoro.
ms.openlocfilehash: 4acaee86136c88e5ac5b3c795f594fb056d15204
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897209"
---
# <a name="office-365-network-connectivity-overview"></a>Panoramica di connettività di rete Office 365

Office 365 è un cloud Software-as-a-Service (SaaS) distribuita che fornisce gli scenari di produttività e collaborazione mediante un insieme varie di micro servizi e applicazioni. Componenti client di Office 365, ad esempio Outlook, Word e PowerPoint eseguire nei computer degli utenti e la connessione ad altri componenti di Office 365 che vengono eseguite in Microsoft Data Center. Il fattore più importante che determina la qualità dell'esperienza utente finale Office 365 è affidabilità della rete e una bassa latenza tra i client di Office 365 e porte del servizio Office 365.

In questo articolo verranno illustrati gli obiettivi di Office 365 di rete e sui motivi per cui la rete di Office 365 richiede un approccio diverso per l'ottimizzazione di traffico Internet generico.

## <a name="office-365-networking-goals"></a>Obiettivi di rete di Office 365

L'obiettivo finale di una rete di Office 365 è per ottimizzare l'esperienza degli utenti finali tramite l'abilitazione all'accesso meno restrittivo tra client e i collaboratori più stretti endpoint di Office 365. La qualità percepita dagli utenti finali è direttamente correlata alle prestazioni e tempi di risposta dell'applicazione che utilizza l'utente. Ad esempio, Microsoft Teams si basa su bassa latenza in modo che le chiamate telefoniche utente, conferenze e collaborazione condivisa schermata sono senza problemi e Outlook utilizza la connettività di rete ideale per la funzionalità Ricerca immediata sul lato server di indicizzazione e AI funzionalità.

L'obiettivo principale nella progettazione di rete è per ridurre al minimo la latenza per la riduzione del tempo di round trip (RTT) dal computer client di rete globale Microsoft backbone di rete pubblica di Microsoft che interconnette tutti i data center Microsoft a bassa latenza , punti di ingresso cloud la disponibilità elevata distribuire tutto il mondo. Sono disponibili ulteriori su Microsoft Network globale in [modo Microsoft si basa la rete globale veloce e affidabile](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Ottimizzazione delle prestazioni di rete di Office 365 non devono essere complicata. È possibile ottenere prestazioni ottimali alcuni principi:

- Identificare il traffico di rete di Office 365
- Consenti uscita locale branch Office 365 del traffico di rete a internet da ogni località in cui gli utenti si connettono a Office 365
- Consentire il traffico di Office 365 ignorare i proxy e pacchetti ispezione dispositivi

Per ulteriori informazioni sui principi di connettività di rete Office 365, vedere [Principi di connettività di rete di Office 365](office-365-network-connectivity-principles.md).

## <a name="traditional-network-architectures-and-saas"></a>Architetture di rete tradizionali e SaaS

Principi di architettura di rete tradizionale per carichi di lavoro client/server sono progettati a partire dal presupposto che non si estende il traffico tra i client e gli endpoint esterno del perimetro della rete aziendale. Inoltre, in molte reti aziendali, tutte le connessioni in uscita Internet passare attraverso la rete aziendale e in uscita da una posizione centrale.

Architetture di rete tradizionale, latenza superiore per il traffico Internet generico è un buon compromesso necessario per gestire la protezione della rete perimetrale e ottimizzazione delle prestazioni per il traffico Internet in genere comporta l'aggiornamento o la scalabilità orizzontale di apparecchiature a punti di uscita alla rete. Tuttavia, questo approccio non soddisfare i requisiti per prestazioni ottimali della rete di servizi SaaS, ad esempio Office 365.

## <a name="identifying-office-365-network-traffic"></a>Che identifica il traffico di rete di Office 365

È stiamo facilitando identificare il traffico di rete di Office 365 e renderla più semplice gestire l'identificazione di rete.

- Nuove categorie endpoint di rete per distinguere essenziale del traffico di rete di traffico di rete che non è interessato dalla latenza di Internet. Sono disponibili solo un numero limitato di URL e supporto indirizzi IP appartenenti alla categoria "Ottimizza" più importante.
- Identificazione di rete di servizi Web per l'utilizzo di script o dispositivo direct configurazione e gestione delle modifiche di Office 365. Le modifiche sono disponibili dal servizio web o in formato RSS o nel messaggio di posta elettronica utilizzando un modello di Microsoft Flow.
- [Programma per i partner di rete di office 365](http://aka.ms/Office365NPP) con i partner Microsoft che forniscono i dispositivi o i servizi che seguono principi di connettività di rete Office 365 e sono configurazione semplice.

## <a name="securing-office-365-connections"></a>Protezione delle connessioni di Office 365

L'obiettivo di protezione di rete tradizionale è per la protezione avanzata del perimetro della rete aziendale da intrusioni e gli attacchi dannosi. La maggior parte delle reti aziendali applicare la protezione di rete per il traffico Internet utilizzando le tecnologie, come i server proxy, firewall, interruzione SSL e controllare controllo dei pacchetti complete e sistemi di prevenzione della perdita di dati. Tali tecnologie offrono riduzione dei rischi importanti per le richieste Internet generiche ma che possono ridurre drasticamente le prestazioni, scalabilità e la qualità dell'esperienza utente finale se applicata a endpoint di Office 365.

Office 365 consente di soddisfare le esigenze dell'organizzazione per la protezione e dati di utilizzo conformità del contenuto con funzionalità di sicurezza e la governance incorporate progettato appositamente per carichi di lavoro e funzionalità di Office 365. Per ulteriori informazioni sulla sicurezza di Office 365 e la conformità, vedere [roadmap di protezione di Office 365](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap). Per ulteriori informazioni sulle indicazioni e la posizione di supporto Microsoft sulle soluzioni di rete avanzate che eseguono l'elaborazione di livello avanzato sul traffico di Office 365, vedere [utilizzo dei dispositivi di rete di terze parti o le soluzioni sul traffico di Office 365](https://support.microsoft.com/en-us/help/2690045).

## <a name="why-is-office-365-networking-different"></a>Perché Office 365 delle reti diverse?

Office 365 è progettato per garantire prestazioni ottimali con protezione endpoint e le connessioni di rete crittografate, la riduzione della necessità per l'applicazione della protezione perimetrale. Office 365 centri dati si trovano in tutto il mondo e il servizio è progettato per l'utilizzo dei vari metodi per la connessione client indicato endpoint del servizio disponibili. Dopo l'elaborazione e i dati utente viene distribuito tra molti Data Center Microsoft, non esiste alcun endpoint di rete singola per i client possono connettersi macchine. In realtà, dati e dei servizi in Office 365 tenant in modo dinamico ottimizzati per Microsoft Network globale per adattarsi a posizioni geografiche da cui si accede dagli utenti finali.

Alcuni comuni problemi di prestazioni vengono creati quando il traffico di Office 365 è soggetta a controllo dei pacchetti e in uscita centralizzato:

- Latenza elevata può causare prestazioni molto scarse di flussi audio e video e tempi di risposta di recupero dei dati, ricerche, collaborazione in tempo reale, le informazioni di disponibilità del calendario, contenuto in prodotti e altri servizi
- Egressing connessioni da una posizione centralizzata vanifica le funzionalità di routing dinamiche della rete globale di Office 365, l'aggiunta di latenza e tempo di round trip
- Decrittografia SSL protetta del traffico di rete di Office 365 e ricrittografare possono causare errori di protocollo e presenta rischi di protezione

Riduzione il percorso di rete di Office 365 i punti di ingresso per consentire il traffico client di uscita più vicino possibile al loro posizione geografica può migliorare la connettività verifica delle prestazioni e l'utente finale in Office 365. Inoltre contribuire a ridurre l'impatto delle modifiche future per l'architettura di rete in Office 365 prestazioni e affidabilità. Il modello di integrazione applicativa ottimale è sempre offrire servizi esterni di rete nel percorso dell'utente, indipendentemente dal fatto che questo nella rete aziendale o sedi remote, ad esempio home, hotel, café e aeroporti. Generico traffico Internet e WAN basati su aziendale del traffico di rete potrebbe essere instradate separatamente e non utilizzano il modello di uscita diretta locale. In questo modello di uscita diretta locale è rappresentato nella figura riportata di seguito.

![Architettura di rete in uscita locale](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

L'architettura di uscita locale presenta i vantaggi seguenti per il traffico di rete di Office 365 tramite il modello tradizionale:
  
- Garantisce prestazioni ottimali di Office 365 all'ottimizzazione delle route lunghezza. Utenti finali sono in modo dinamico il routing delle connessioni al punto di ingresso di Office 365 più vicino dall'infrastruttura _distribuita porta anteriore del servizio_ di rete globale Microsoft e il traffico verrà instradato internamente agli endpoint servizio e dei dati tramite Microsoft fibra scuro la disponibilità elevata latenza ridotta.
- Riduce il carico dell'infrastruttura di rete aziendale consentendo locale in uscita per il traffico di Office 365, ignorando i proxy e i dispositivi di controllo del traffico.
- Consente di proteggere le connessioni a entrambe le estremità utilizzando client endpoint cloud e protezione funzionalità di sicurezza, evitare di applicazione delle tecnologie di protezione di rete ridondanti.

> [!NOTE]
> L'infrastruttura di _ingresso servizio distribuita_ è edge rete elevata disponibilità e scalabilità di rete globale Microsoft con posizioni geografiche. Che supporta le connessioni utente finale e instrada in modo efficiente all'interno della rete globale di Microsoft. Sono disponibili ulteriori su Microsoft Network globale in [modo Microsoft si basa la rete globale veloce e affidabile](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Per ulteriori informazioni sulle indicazioni e applicare i principi di connettività di rete Office 365, vedere [Principi di connettività di rete di Office 365](office-365-network-connectivity-principles.md).

## <a name="conclusion"></a>Conclusione

Ottimizzazione delle prestazioni di rete di Office 365 veramente un' verso il basso rimozione ostacoli non necessari. Gestendo le connessioni di Office 365 come traffico attendibile, è possibile impedire latenza introdotto dal controllo dei pacchetti e alla concorrenza di larghezza di banda proxy. Consentire le connessioni locali tra computer client e gli endpoint di Office 365 consente il traffico in modo dinamico essere instradato attraverso la rete globale Microsoft.

## <a name="related-topics"></a>Argomenti correlati

[Principi della connettività di rete di Office 365](office-365-network-connectivity-principles.md)

[Servizio Web per URL e indirizzi IP di Office 365](office-365-ip-web-service.md)

[Gestione degli endpoint di Office 365](managing-office-365-endpoints.md)

[Servizio Web per URL e indirizzi IP di Office 365](office-365-ip-web-service.md)

[Connettività di rete con Office 365](network-connectivity.md)

[Ottimizzazione delle prestazioni e della rete di Office 365](network-planning-and-performance.md)

[Ottimizzazione delle prestazioni di Office 365 mediante l'uso della cronologia delle prestazioni e delle previsioni](performance-tuning-using-baselines-and-history.md)

[Piano di risoluzione dei problemi di prestazioni per Office 365](performance-troubleshooting-plan.md)

[Come Microsoft si basa la rete globale veloce e affidabile](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)
