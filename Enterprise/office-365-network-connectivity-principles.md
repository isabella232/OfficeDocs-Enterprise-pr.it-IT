---
title: Principi della connettività di rete di Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
search.appverid: MET150
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
f1.keywords:
- NOCSH
description: Prima di iniziare a pianificare la rete per la connettività di rete di Office 365, è importante comprendere i principi di connettività per la gestione sicura del traffico di Office 365 e ottenere le migliori prestazioni possibili. In questo articolo vengono fornite informazioni utili per comprendere le indicazioni più recenti per ottimizzare in modo sicuro la connettività di rete di Office 365.
ms.openlocfilehash: 29cfd5725d4c80f30146abcd921c37305c30b17d
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998665"
---
# <a name="microsoft-365-network-connectivity-principles"></a>Principi della connettività di rete di Microsoft 365

*Questo articolo si applica sia a Microsoft 365 Enterprise che a Office 365 Enterprise.*

Prima di iniziare a pianificare la rete per la connettività di rete Microsoft 365, è importante comprendere i principi di connettività per gestire in modo sicuro il traffico di Microsoft 365 e ottenere le migliori prestazioni possibili. In questo articolo vengono fornite informazioni sulle linee guida più recenti per ottimizzare in modo sicuro la connettività di rete di Microsoft 365.
  
Le reti aziendali tradizionali sono progettate principalmente per fornire agli utenti l'accesso alle applicazioni e ai dati ospitati nei datacenter aziendali gestiti con una sicurezza perimetrale elevata. Il modello tradizionale presuppone che gli utenti accedano a applicazioni e dati dall'interno del perimetro della rete aziendale, tramite collegamenti WAN da succursali o in remoto tramite connessioni VPN.
  
L'adozione di applicazioni SaaS come Microsoft 365 sposta una combinazione di servizi e dati all'esterno del perimetro della rete. Senza ottimizzazione, il traffico tra gli utenti e le applicazioni SaaS è soggetto a latenza introdotta da ispezione dei pacchetti, tornanti di rete, connessioni involontarie a endpoint geograficamente distanti e altri fattori. È possibile garantire le migliori prestazioni e affidabilità di Microsoft 365 mediante la comprensione e l'implementazione di linee guida per l'ottimizzazione delle chiavi.
  
In questo articolo verrà illustrato quanto segue:
  
- [Architettura di Microsoft 365](office-365-network-connectivity-principles.md#BKMK_Architecture) applicata alla connettività dei clienti al cloud
- Sono stati aggiornati i principi e le strategie di [connettività di Microsoft 365](office-365-network-connectivity-principles.md#BKMK_Principles) per ottimizzare il traffico di rete e l'esperienza dell'utente finale
- Il [servizio Web di Office 365 Endpoints](office-365-network-connectivity-principles.md#BKMK_WebSvc), che consente agli amministratori di rete di utilizzare un elenco strutturato di endpoint per l'utilizzo in ottimizzazione della rete
- [Nuove categorie di endpoint di Office 365](office-365-network-connectivity-principles.md#BKMK_Categories) e linee guida per l'ottimizzazione
- [Confronto tra sicurezza perimetrale di rete e sicurezza degli endpoint](office-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- Opzioni di [ottimizzazione incrementale](office-365-network-connectivity-principles.md#BKMK_IncOpt) per il traffico di Microsoft 365
- [Test di connettività microsoft 365](https://aka.ms/netonboard), un nuovo strumento per testare la connettività di base a Microsoft 365

## <a name="microsoft-365-architecture"></a>Architettura di Microsoft 365
<a name="BKMK_Architecture"> </a>

Microsoft 365 è un cloud SaaS (software-as-a-Service) distribuito che offre scenari di produttività e collaborazione tramite una serie diversificata di micro-servizi e applicazioni, ad esempio Exchange Online, SharePoint Online, Skype for business online, Microsoft teams, Exchange Online Protection, Office in un browser e molti altri. Sebbene le applicazioni Microsoft 365 specifiche possano avere caratteristiche univoche applicate alla rete e alla connettività dei clienti al cloud, condividono tutti alcuni principi chiave, obiettivi e modelli di architettura. Questi modelli di entità e architettura per la connettività sono tipici di molte altre nubi SaaS e allo stesso tempo sono molto diversi dai modelli di distribuzione tipici di cloud di tipo piattaforma-come-a-Service e infrastruttura-come-a-Service, ad esempio Microsoft Azure.
  
Uno dei più significativi elementi architettonici di Microsoft 365 (spesso mancati o erroneamente interpretati dai pianificatori di rete) è che si tratta di un servizio distribuito davvero globale, nel contesto del modo in cui gli utenti si connettono. La posizione del tenant di destinazione Microsoft 365 è importante per comprendere la località in cui vengono archiviati i dati dei clienti all'interno del cloud, ma l'esperienza utente con Microsoft 365 non comporta la connessione diretta ai dischi contenenti i dati. L'esperienza dell'utente con Microsoft 365 (comprese le prestazioni, l'affidabilità e altre importanti caratteristiche di qualità) implica la connettività tramite porte frontali di servizi altamente distribuiti che sono state distribuite in centinaia di percorsi Microsoft in tutto il mondo. Nella maggior parte dei casi, la migliore esperienza utente viene ottenuta consentendo alla rete del cliente di instradare le richieste degli utenti al punto di ingresso del servizio Microsoft 365 più vicino, anziché connettersi a Microsoft 365 tramite un punto di uscita in una posizione centrale o in un'area geografica.
  
Per la maggior parte dei clienti, gli utenti di Microsoft 365 sono distribuiti in numerosi percorsi. Per ottenere risultati ottimali, i principi descritti in questo documento devono essere esaminati dal punto di vista della scalabilità orizzontale (non di scalabilità verticale), concentrandosi sull'ottimizzazione della connettività al punto di presenza più vicino nella rete globale Microsoft, non sulla posizione geografica del tenant Microsoft 365. In sostanza, ciò significa che, anche se i dati del tenant di Microsoft 365 possono essere archiviati in una specifica posizione geografica, l'esperienza di Microsoft 365 per tale tenant rimane distribuita e può essere presente in prossimità (rete) a tutte le posizioni degli utenti finali del tenant.
  
## <a name="microsoft-365-connectivity-principles"></a>Principi di connettività di Microsoft 365
<a name="BKMK_Principles"> </a>

Microsoft consiglia i seguenti principi per ottenere la connettività e le prestazioni ottimali di Microsoft 365. Utilizzare questi principi di connettività di Microsoft 365 per gestire il traffico e ottenere prestazioni ottimali per la connessione a Microsoft 365.
  
L'obiettivo principale della progettazione della rete dovrebbe essere quello di ridurre al minimo la latenza riducendo la RTT (Round Trip Time) dalla rete nella rete globale Microsoft, la backbone di rete pubblica di Microsoft che interconnette tutti i datacenter di Microsoft con una bassa latenza e punti di ingresso dell'applicazione cloud sparsi in tutto il mondo. Per ulteriori informazioni sulla rete globale Microsoft [, vedere come Microsoft crea la propria rete globale veloce e affidabile](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).
  
<a name="BKMK_P1"> </a>
### <a name="identify-and-differentiate-microsoft-365-traffic"></a>Identificare e differenziare il traffico di Microsoft 365

![Identificare il traffico di Microsoft 365](media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
Identificare il traffico di rete di Microsoft 365 è il primo passaggio per la possibilità di differenziare il traffico dal traffico di rete generico associato a Internet. La connettività Microsoft 365 può essere ottimizzata mediante l'implementazione di una combinazione di approcci quali l'ottimizzazione del percorso di rete, le regole del firewall, le impostazioni del proxy del browser e la bypass dei dispositivi di ispezione di rete per alcuni endpoint.
  
Le precedenti linee guida per l'ottimizzazione di Microsoft 365 hanno suddiviso gli endpoint Microsoft 365 in due categorie, **obbligatorie** e **facoltative**. Poiché sono stati aggiunti endpoint per supportare nuovi servizi e funzionalità di Microsoft 365, sono stati riorganizzati endpoint di Microsoft 365 in tre categorie: **optimize**, **Allow** e **default**. Le linee guida di ogni categoria si applicano a tutti gli endpoint della categoria, semplificando le ottimizzazioni per la comprensione e l'implementazione.
  
Per ulteriori informazioni sulle categorie di endpoint e sui metodi di ottimizzazione di Microsoft 365, vedere la sezione [New Office 365 endpoint Categories](office-365-network-connectivity-principles.md#BKMK_Categories) .
  
Microsoft ora pubblica tutti gli endpoint Microsoft 365 come servizio Web e fornisce indicazioni su come utilizzare al meglio questi dati. Per ulteriori informazioni su come recuperare e utilizzare gli endpoint di Microsoft 365, vedere l'articolo [Office 365 URLs and IP address ranges](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
<a name="BKMK_P2"> </a>
### <a name="egress-network-connections-locally"></a>Uscire dalle connessione di rete a livello locale

![Uscire dalle connessione di rete a livello locale](media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
L'uscita DNS locale e Internet è di importanza cruciale per la riduzione della latenza delle connessioni e per garantire che le connessioni utente vengano apportate al punto più vicino di accesso ai servizi di Microsoft 365. In una topologia di rete complessa, è importante implementare contemporaneamente sia il DNS locale che l'uscita Internet locale. Per ulteriori informazioni sul modo in cui Microsoft 365 instrada le connessioni client al punto di ingresso più vicino, vedere l'articolo [connettività client](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b).
  
Prima dell'avvento dei servizi cloud, ad esempio Microsoft 365, la connettività Internet degli utenti finali come fattore di progettazione nell'architettura di rete era relativamente semplice. Quando i servizi Internet e i siti Web vengono distribuiti in tutto il mondo, la latenza tra i punti di uscita delle aziende e qualsiasi endpoint di destinazione specificato è in gran parte una funzione di distanza geografica.
  
In un'architettura di rete tradizionale, tutte le connessioni Internet in uscita attraversano la rete aziendale e l'uscita da una posizione centrale. Le offerte cloud di Microsoft sono state maturate, un'architettura di rete distribuita con connessione Internet è diventata critica per il supporto dei servizi cloud sensibili alla latenza. La rete globale Microsoft è stata progettata per soddisfare i requisiti di latenza con l'infrastruttura del servizio Distributed front door, un tessuto dinamico di punti di ingresso globali che instradano le connessioni del servizio cloud in ingresso al punto di ingresso più vicino. Questo ha lo scopo di ridurre la lunghezza dell'"ultimo chilometro" per i clienti di Microsoft cloud riducendo in modo efficace la route tra il cliente e il cloud.
  
Le reti WAN Enterprise sono spesso progettate per eseguire un backhaul del traffico di rete verso una sede centrale aziendale per l'ispezione prima dell'uscita su Internet, in genere tramite uno o più server proxy. Nel diagramma seguente viene illustrata una topologia di rete.
  
![Modello di rete aziendale tradizionale](media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
Poiché Microsoft 365 viene eseguito sulla rete globale Microsoft, che include server front-end di tutto il mondo, spesso vi sarà un server front-end vicino alla posizione dell'utente. Fornendo l'uscita Internet locale e configurando i server DNS interni per fornire la risoluzione dei nomi locali per gli endpoint di Microsoft 365, il traffico di rete destinato a Microsoft 365 può connettersi a Microsoft 365 front end server il più vicino possibile all'utente. Nel diagramma seguente viene illustrato un esempio di topologia di rete che consente agli utenti di connettersi dalle sedi principali, succursali e remote per seguire la route più breve verso il punto di ingresso Microsoft 365 più vicino.
  
![Modello di rete WAN con punti di uscita regionali](media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
La riduzione del percorso di rete per i punti di ingresso di Microsoft 365 in questo modo può migliorare le prestazioni di connettività e l'esperienza degli utenti finali in Microsoft 365 e può anche contribuire a ridurre l'impatto delle modifiche future nell'architettura di rete in termini di prestazioni e affidabilità di Microsoft 365.
  
Inoltre, le richieste DNS possono introdurre latenza se il server DNS rispondente è distante o occupato. È possibile ridurre al minimo la latenza della risoluzione dei nomi provisioning di server DNS locali in posizioni di succursale e verificare che siano configurati in modo appropriato per memorizzare nella cache i record DNS.
  
Anche se l'uscita Regional può funzionare bene per Microsoft 365, il modello di connettività ottimale potrebbe essere quello di fornire sempre l'uscita di rete nella posizione dell'utente, indipendentemente dal fatto che si trovi sulla rete aziendale o su postazioni remote quali Home, Hotels, coffee shops e airports. Questo modello di uscita diretta locale è rappresentato nel diagramma seguente.
  
![Architettura di rete in uscita locale](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
Le aziende che hanno adottato Microsoft 365 possono usufruire dell'architettura del servizio distribuito di Microsoft Global Network, garantendo che le connessioni utente a Microsoft 365 portino il percorso più breve possibile verso il punto di ingresso di rete globale Microsoft più vicino. L'architettura di rete in uscita locale consente di instradare il traffico di Microsoft 365 sull'uscita più vicina, indipendentemente dalla posizione dell'utente.
  
L'architettura di uscita locale presenta i seguenti vantaggi rispetto al modello tradizionale:
  
- Offre prestazioni ottimali di Microsoft 365 ottimizzando la lunghezza del percorso. Le connessioni degli utenti finali vengono instradate dinamicamente al punto di ingresso Microsoft 365 più vicino dall'infrastruttura del servizio Distributed front door.
- Riduce il carico dell'infrastruttura di rete aziendale consentendo l'uscita locale.
- Consente di proteggere le connessioni su entrambe le estremità sfruttando le funzionalità di sicurezza e sicurezza del cloud di endpoint client.

<a name="BKMK_P3"> </a>
### <a name="avoid-network-hairpins"></a>Evitare fenomeni di "hairpinning" di rete

![Evitare i tornanti](media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
Come regola generale, il percorso più breve e diretto tra l'utente e l'endpoint Microsoft 365 più vicino offrirà le migliori prestazioni. Un tornante di rete si verifica quando il traffico WAN o VPN associato a una determinata destinazione viene prima indirizzato a un altro percorso intermedio, ad esempio stack di sicurezza, broker di accesso cloud, del gateway Web basato sul cloud, introducendo la latenza e il reindirizzamento potenziale a un endpoint geograficamente distante. I tornanti di rete possono essere causati anche da inefficienze di routing e peering o ricerche DNS subottimali (Remote).
  
Per assicurarsi che la connettività di Microsoft 365 non sia soggetta ai tornanti di rete anche nel caso di uscita locale, verificare se l'ISP utilizzato per fornire l'uscita Internet per la posizione dell'utente ha una relazione di peering diretta con la rete globale Microsoft nelle immediate vicinanze di tale posizione. È inoltre possibile configurare il routing di uscita per inviare direttamente il traffico Microsoft 365 attendibile, anziché inoltrare o eseguire il tunneling attraverso un fornitore di sicurezza di rete cloud o cloud di terze parti che elabora il traffico associato a Internet. La risoluzione dei nomi DNS locali degli endpoint di Microsoft 365 contribuisce a garantire che, oltre al routing diretto, i punti di ingresso Microsoft 365 più vicini vengano utilizzati per le connessioni utente.
  
Se si utilizzano i servizi di sicurezza e di rete basati sul cloud per il traffico Microsoft 365, assicurarsi che l'effetto Hairpin venga valutato e che il relativo impatto sulle prestazioni di Microsoft 365 sia compreso. A tale scopo, è possibile esaminare il numero e le posizioni delle posizioni dei provider di servizi tramite cui viene inoltrato il traffico in relazione al numero delle succursali e dei punti di peering della rete globale di Microsoft, la qualità della relazione di peering di rete del provider di servizi con l'ISP e Microsoft e l'impatto sulle prestazioni del backhauling nell'infrastruttura del provider di servizi.
  
A causa del numero elevato di posizioni distribuite con i punti di ingresso di Microsoft 365 e della prossimità degli utenti finali, il routing del traffico Microsoft 365 a qualsiasi rete o provider di sicurezza di terze parti può avere un impatto negativo sulle connessioni Microsoft 365 se la rete del provider non è configurata per l'peering Microsoft 365 ottimale.
  
<a name="BKMK_P4"> </a>
### <a name="assess-bypassing-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>Valutare l'esclusione di proxy, dispositivi di ispezione del traffico e tecnologie di sicurezza duplicate

![Bypassare proxy, dispositivi di ispezione del traffico e tecnologie di sicurezza duplicate](media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
I clienti aziendali devono esaminare i propri metodi di protezione e riduzione dei rischi di rete in modo specifico per il traffico associato a Microsoft 365 e utilizzare le funzionalità di sicurezza di Microsoft 365 per ridurre la dipendenza dall'intrusione, dall'impatto sulle prestazioni e dalla costosa tecnologia di rete per il traffico di rete Microsoft 365.
  
La maggior parte delle reti aziendali impone la sicurezza della rete per il traffico Internet utilizzando tecnologie come proxy, ispezione SSL, ispezione dei pacchetti e sistemi di prevenzione della perdita di dati. Queste tecnologie offrono una significativa attenuazione dei rischi per le richieste generiche su Internet, ma possono ridurre drasticamente le prestazioni, la scalabilità e la qualità dell'esperienza degli utenti finali quando vengono applicate agli endpoint di Microsoft 365.
  
<a name="BKMK_WebSvc"> </a>
#### <a name="office-365-endpoints-web-service"></a>Servizio Web di endpoint di Office 365

Gli amministratori di Microsoft 365 possono utilizzare uno script o una chiamata REST per consumare un elenco strutturato di endpoint dal servizio Web di Office 365 endpoint e aggiornare le configurazioni dei firewall perimetrali e di altri dispositivi di rete. Questo assicurerà che il traffico associato a Microsoft 365 venga identificato, trattato adeguatamente e gestito in modo diverso dal traffico di rete associato a siti web generici e spesso sconosciuti. Per ulteriori informazioni su come utilizzare il servizio Web di Office 365 endpoint, vedere l'articolo [office 365 URLs and IP address ranges](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>Script per la configurazione automatica del proxy (PAC)
<a name="BKMK_WebSvc"> </a>

Gli amministratori di Microsoft 365 possono creare script PAC (Proxy Automatic Configuration) che possono essere recapitati ai computer degli utenti tramite WPAD o GPO. Gli script PAC possono essere utilizzati per ignorare i proxy per le richieste di Microsoft 365 da parte di utenti WAN o VPN, consentendo al traffico di Microsoft 365 di utilizzare connessioni Internet dirette anziché attraversare la rete aziendale.
  
#### <a name="microsoft-365-security-features"></a>Funzionalità di sicurezza di Microsoft 365
<a name="BKMK_WebSvc"> </a>

Microsoft è trasparente sulla sicurezza del centro dati, la sicurezza operativa e la riduzione dei rischi nei server Microsoft 365 e negli endpoint di rete che rappresentano. Le funzionalità di sicurezza predefinite di Microsoft 365 sono disponibili per ridurre il rischio di protezione della rete, ad esempio la prevenzione della perdita di dati, l'antivirus, l'autenticazione a più fattori, la casella di blocco dei clienti, la protezione avanzata dalle minacce, Microsoft 365 Threat Intelligence, Microsoft 365 Secure score, Exchange Online Protection e la sicurezza DDOS di rete.
  
Per ulteriori informazioni su Microsoft datacenter e sulla sicurezza della rete globale, vedere [Microsoft Trust Center](https://www.microsoft.com/trustcenter/security).
  
## <a name="new-office-365-endpoint-categories"></a>Nuove categorie di endpoint di Office 365
<a name="BKMK_Categories"> </a>

Gli endpoint di Office 365 rappresentano un insieme variegato di indirizzi di rete e subnet. Gli endpoint possono essere URL, indirizzi IP o intervalli IP e alcuni endpoint sono elencati con porte TCP/UDP specifiche. Gli URL possono essere un FQDN come *account.Office.NET* , o un URL con caratteri jolly come * \* . office365.com*.
  
> [!NOTE]
> Le posizioni degli endpoint di Office 365 all'interno della rete non sono direttamente correlate al percorso dei dati del tenant di Microsoft 365. Per questo motivo, i clienti devono esaminare Microsoft 365 come servizio distribuito e globale e non devono tentare di bloccare le connessioni di rete agli endpoint di Office 365 in base a criteri geografici.
  
Nelle linee guida precedenti per la gestione del traffico Microsoft 365, gli endpoint sono stati organizzati in due categorie, **obbligatorio** e **facoltativo**. Gli endpoint all'interno di ogni categoria richiedevano diverse ottimizzazioni a seconda della criticità del servizio e molti clienti affrontavano le sfide per giustificare l'applicazione delle stesse ottimizzazioni di rete all'elenco completo di URL e indirizzi IP di Office 365.
  
Nel nuovo modello gli endpoint sono suddivisi in tre categorie, **optimize**, **Allow** e **default**, fornendo un pivot basato sulla priorità in cui si concentrano gli sforzi di ottimizzazione della rete per ottenere i migliori miglioramenti delle prestazioni e il ritorno sull'investimento. Gli endpoint sono consolidati nelle categorie sopra riportate in base alla sensibilità dell'esperienza utente effettiva alla qualità della rete, all'inviluppo di volume e prestazioni degli scenari e alla facilità di implementazione. Le ottimizzazioni consigliate possono essere applicate allo stesso modo per tutti gli endpoint di una determinata categoria.
  
- **Ottimizzazione** degli endpoint sono necessari per la connettività a tutti i servizi di Office 365 e rappresentano oltre il 75% della larghezza di banda, delle connessioni e del volume di dati di Office 365. Tali endpoint rappresentano gli scenari di Office 365 che sono più sensibili alle prestazioni, alla latenza e alla disponibilità della rete. Tutti gli endpoint sono ospitati nei datacenter Microsoft. La percentuale di modifiche apportate agli endpoint in questa categoria dovrebbe essere molto più bassa rispetto a quella degli endpoint nelle altre due categorie. Questa categoria include un insieme di URL di chiave molto piccolo (nell'ordine di ~ 10) e un set definito di subnet IP dedicate ai carichi di lavoro di core Office 365, ad esempio Exchange Online, SharePoint Online, Skype for business online e Microsoft teams.

    Un elenco condensato di endpoint critici ben definiti dovrebbe essere utile per pianificare e implementare le ottimizzazioni di rete di alto valore per queste destinazioni in modo più semplice e veloce.

    Di seguito sono riportati alcuni esempi di endpoint di *ottimizzazione* *https://outlook.office365.com* : *https:// \<tenant\> . SharePoint.com* e *https:// \<tenant\> -My.SharePoint.com* .

    I metodi di ottimizzazione includono:

  - Bypass o whitelist *ottimizzare* gli endpoint sui dispositivi di rete e sui servizi che eseguono l'intercettazione del traffico, la decrittografia SSL, l'ispezione profonda dei pacchetti e il filtro contenuto.
  - Bypassare i dispositivi proxy locali e i servizi proxy basati su cloud comunemente utilizzati per l'esplorazione Internet generica.
  - Assegnare la priorità alla valutazione di tali endpoint come completamente attendibile dall'infrastruttura di rete e dai sistemi perimetrali.
  - Assegnare la priorità alla riduzione o all'eliminazione del backhauling WAN e facilitare l'uscita basata su Internet distribuita direttamente per questi endpoint il più vicino possibile alle posizioni degli utenti/succursali.
  - Semplificare la connettività diretta a questi endpoint cloud per gli utenti VPN mediante l'implementazione del tunneling suddiviso.
  - Verificare che gli indirizzi IP restituiti dalla risoluzione dei nomi DNS corrispondano al percorso di uscita del routing per questi endpoint.
  - Assegnare la priorità a questi endpoint per l'integrazione di SD-WAN per il routing diretto e minimo di latenza al punto di peering Internet più vicino della rete globale di Microsoft.

- **Consenti** gli endpoint sono necessari per la connettività a servizi e funzionalità di Office 365 specifici, ma non sono sensibili alle prestazioni e alla latenza di rete come quelli della categoria *optimize* . L'ingombro globale di rete di questi endpoint dal punto di vista della larghezza di banda e del numero di connessioni è significativamente più piccolo. Questi endpoint sono dedicati a Office 365 e sono ospitati nei Data Center Microsoft. Essi rappresentano un ampio set di micro-servizi di Office 365 e le relative dipendenze (nell'ordine di ~ 100 URL) e dovrebbero variare a una velocità superiore rispetto a quelle della categoria *optimize* . Non tutti gli endpoint di questa categoria sono associati a subnet IP dedicate definite.

    Le ottimizzazioni di rete per gli endpoint *consentono* di migliorare l'esperienza utente di Office 365, ma alcuni clienti possono scegliere di applicare queste ottimizzazioni in modo più restrittivo per ridurre al minimo le modifiche apportate alla rete.

    Di seguito sono riportati alcuni esempi di endpoint che *consentono* di includere *https:// \* . Protection.Outlook.com* e *https://accounts.accesscontrol.windows.net* .

    I metodi di ottimizzazione includono:

  - Bypass o whitelist *consentono* gli endpoint sui dispositivi di rete e sui servizi che eseguono l'intercettazione del traffico, la decrittografia SSL, l'ispezione profonda dei pacchetti e il filtro contenuto.
  - Assegnare la priorità alla valutazione di tali endpoint come completamente attendibile dall'infrastruttura di rete e dai sistemi perimetrali.
  - Assegnare la priorità alla riduzione o all'eliminazione del backhauling WAN e facilitare l'uscita basata su Internet distribuita direttamente per questi endpoint il più vicino possibile alle posizioni degli utenti/succursali.
  - Verificare che gli indirizzi IP restituiti dalla risoluzione dei nomi DNS corrispondano al percorso di uscita del routing per questi endpoint.
  - Assegnare la priorità a questi endpoint per l'integrazione di SD-WAN per il routing diretto e minimo di latenza al punto di peering Internet più vicino della rete globale di Microsoft.

- Gli endpoint **predefiniti** rappresentano i servizi e le dipendenze di Office 365 che non richiedono alcuna ottimizzazione e possono essere trattati dalle reti dei clienti come normale traffico associato a Internet. Tenere presente che alcuni endpoint di questa categoria potrebbero non essere ospitati nei Data Center Microsoft. Tra gli esempi sono inclusi *https://odc.officeapps.live.com* e *https://appexsin.stb.s-msn.com* .

Per ulteriori informazioni sulle tecniche di ottimizzazione della rete di Office 365, vedere l'articolo [Managing office 365 Endpoints](https://support.office.com/article/managing-office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a#ID0EAEAAA=0._Overview).
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>Confronto tra sicurezza perimetrale di rete e sicurezza degli endpoint
<a name="BKMK_SecurityComparison"> </a>

L'obiettivo della sicurezza della rete tradizionale è quello di indurire il perimetro della rete aziendale contro intrusioni e exploit dolosi. Poiché le organizzazioni adottano Microsoft 365, alcuni servizi di rete e dati vengono parzialmente o completamente migrati nel cloud. Analogamente a qualsiasi modifica sostanziale dell'architettura di rete, questo processo richiede una rivalutazione della sicurezza della rete che tiene conto dei fattori emergenti:
  
- Come vengono adottati i servizi cloud, i servizi e i dati di rete vengono distribuiti tra i datacenter locali e il cloud e la sicurezza perimetrale non è più adeguata.
- Gli utenti remoti si connettono alle risorse aziendali sia nei centri dati locali sia nel cloud da posizioni incontrollate come case, Alberghi e coffee shop.
- Le funzionalità di sicurezza create appositamente sono integrate in servizi cloud e possono potenzialmente integrare o sostituire i sistemi di sicurezza esistenti.

Microsoft offre una vasta gamma di funzionalità di sicurezza di Microsoft 365 e fornisce indicazioni prescrittivi per l'utilizzo di procedure consigliate per la sicurezza che consentono di garantire la sicurezza dei dati e della rete per Microsoft 365. Le procedure consigliate suggerite sono le seguenti:
  
- **Utilizzo dell'autenticazione a più fattori (AMF)** L'AMF aggiunge un ulteriore livello di protezione a una strategia di password complessa richiedendo agli utenti di riconoscere una telefonata, un messaggio di testo o una notifica di app sul proprio smartphone dopo aver inserito correttamente la propria password.

- **Utilizzare Microsoft cloud app Security** Impostare i criteri per monitorare le attività anomale e agire su di esso. Configurare gli avvisi con Microsoft cloud app Security in modo che gli amministratori possano esaminare attività utente inusuali o rischiose, ad esempio il download di grandi quantità di dati, più tentativi di accesso non riusciti o connessioni provenienti da indirizzi IP sconosciuti o pericolosi.

- **Configurare la prevenzione della perdita di dati (DLP)** DLP consente di identificare i dati sensibili e creare criteri che consentono di impedire agli utenti di condividere accidentalmente o intenzionalmente i dati. DLP è compatibile con Microsoft 365 incluso Exchange Online, SharePoint Online e OneDrive in modo che gli utenti possano rimanere conformi senza interrompere il flusso di lavoro.

- **Utilizzo dell'archivio protetto dei clienti** In qualità di amministratore Microsoft 365, è possibile utilizzare l'archivio protetto dei clienti per controllare il modo in cui un tecnico del supporto Microsoft accede ai dati durante una sessione della guida. Nei casi in cui il tecnico richiede l'accesso ai dati dell'utente per risolvere e correggere un problema, Customer Lockbox consente di approvare o rifiutare la richiesta di accesso.

- **Utilizzare Office 365 Secure Score** Secure Score è uno strumento di analisi della sicurezza che consiglia le operazioni che è possibile eseguire per ridurre ulteriormente i rischi. Secure Score analizza le impostazioni e le attività di Microsoft 365 e le confronta con una linea di base stabilita da Microsoft. Si otterrà un punteggio in base al modo in cui si è allineati con le migliori procedure di sicurezza.

Un approccio olistico alla sicurezza avanzata deve includere la considerazione di quanto segue:
  
- Spostare l'accento sulla sicurezza perimetrale verso endpoint Security applicando le funzionalità di sicurezza e di Office client basate su cloud.
  - Compattazione del perimetro di sicurezza per il datacenter
  - Abilitazione dell'attendibilità equivalente per i dispositivi utente all'interno di Office o in posizioni remote
  - Concentrarsi sulla protezione del percorso dei dati e della posizione dell'utente
  - I computer degli utenti gestiti hanno maggiore attendibilità con endpoint Security
- Gestire tutta la sicurezza delle informazioni in maniera olistica, non concentrandosi unicamente sul perimetro
  - Ridefinire WAN e creare la sicurezza della rete perimetrale consentendo al traffico attendibile di ignorare i dispositivi di sicurezza e di separare i dispositivi non gestiti nelle reti Wi-Fi Guest.
  - Riduzione dei requisiti di sicurezza della rete del server WAN aziendale
  - Alcuni dispositivi di sicurezza perimetrali di rete, ad esempio i firewall, sono ancora necessari, ma il carico è diminuito
  - Assicura l'uscita locale per il traffico Microsoft 365
- I miglioramenti possono essere risolti in modo incrementale come descritto nella sezione [ottimizzazione incrementale](office-365-network-connectivity-principles.md#BKMK_IncOpt) . Alcune tecniche di ottimizzazione possono offrire migliori rapporti costi/benefici a seconda dell'architettura di rete e scegliere le ottimizzazioni più sensate per l'organizzazione.

Per ulteriori informazioni su Microsoft 365 sicurezza e conformità, vedere l'articolo [panoramica sulla sicurezza e la conformità in Office 365](https://support.office.com/article/overview-of-security-and-compliance-in-office-365-dcb83b2c-ac66-4ced-925d-50eb9698a0b2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
## <a name="incremental-optimization"></a>Ottimizzazione incrementale
<a name="BKMK_IncOpt"> </a>

Il modello di connettività di rete ideale per SaaS è stato rappresentato in precedenza in questo articolo, ma per molte organizzazioni di grandi dimensioni con architetture di rete complesse storicamente, non sarà pratico apportare direttamente tutte queste modifiche. In questa sezione vengono illustrate numerose modifiche incrementali che consentono di migliorare le prestazioni e l'affidabilità di Microsoft 365.
  
I metodi che verranno utilizzati per ottimizzare il traffico di Microsoft 365 variano a seconda della topologia di rete e dei dispositivi di rete implementati. Le grandi aziende con numerosi percorsi e procedure di sicurezza di rete complesse dovranno sviluppare una strategia che includa la maggior parte o tutti i principi elencati nella sezione [principi di connettività di Microsoft 365](office-365-network-connectivity-principles.md#BKMK_Principles) , mentre le organizzazioni più piccole potrebbero essere tenute a prendere in considerazione solo uno o due.
  
È possibile approcciare l'ottimizzazione come processo incrementale, applicando ogni metodo in successione. Nella tabella seguente sono elencati i metodi di ottimizzazione principali per il loro impatto sulla latenza e l'affidabilità per il numero massimo di utenti.
  
|**Metodo di ottimizzazione**|**Descrizione**|**Impatto**|
|:-----|:-----|:-----|
|Risoluzione DNS locale e uscita Internet  <br/> |Eseguire il provisioning dei server DNS locali in ogni posizione e verificare che Microsoft 365 connessioni in uscita su Internet sia il più vicino possibile alla posizione dell'utente.  <br/> | Ridurre al minimo la latenza  <br/>  Migliorare la connettività affidabile con il punto di ingresso Microsoft 365 più vicino  <br/> |
|Aggiungere punti di uscita regionali  <br/> |Se la rete aziendale dispone di più posizioni, ma solo di un punto di uscita, aggiungere punti di uscita regionali per consentire agli utenti di connettersi al punto di ingresso Microsoft 365 più vicino.  <br/> | Ridurre al minimo la latenza  <br/>  Migliorare la connettività affidabile con il punto di ingresso Microsoft 365 più vicino  <br/> |
|Bypassare proxy e dispositivi di ispezione  <br/> |Configurare i browser con i file PAC che inviano le richieste di Microsoft 365 direttamente ai punti di uscita.  <br/> Configurare i router perimetrali e i firewall per consentire il traffico di Microsoft 365 senza ispezione.  <br/> | Ridurre al minimo la latenza  <br/>  Riduzione del carico sui dispositivi di rete  <br/> |
|Abilitare la connessione diretta per gli utenti VPN  <br/> |Per gli utenti VPN, abilitare le connessioni Microsoft 365 per la connessione direttamente dalla rete dell'utente anziché tramite il tunnel VPN mediante l'implementazione del tunneling suddiviso.  <br/> | Ridurre al minimo la latenza  <br/>  Migliorare la connettività affidabile con il punto di ingresso Microsoft 365 più vicino  <br/> |
|Eseguire la migrazione dalla WAN tradizionale alla SD-WAN  <br/> |SD-WAN (software defined Wide Area Networks) semplificare la gestione della rete WAN e migliorare le prestazioni sostituendo i router WAN tradizionali con gli strumenti virtuali, analogamente alla virtualizzazione delle risorse di calcolo tramite macchine virtuali (VM).  <br/> | Migliorare le prestazioni e la gestibilità del traffico WAN  <br/>  Riduzione del carico sui dispositivi di rete  <br/> |

## <a name="related-topics"></a>Argomenti correlati

[Panoramica della connettività di rete Microsoft 365](office-365-networking-overview.md)

[Gestione degli endpoint di Office 365](managing-office-365-endpoints.md)

[URL e intervalli di indirizzi IP per Office 365](urls-and-ip-address-ranges.md)

[Servizio Web per URL e indirizzi IP di Office 365](office-365-ip-web-service.md)

[Valutazione della connettività di rete di Microsoft 365](assessing-network-connectivity.md)

[Pianificazione della rete e ottimizzazione delle prestazioni per Microsoft 365](network-planning-and-performance.md)

[Ottimizzazione delle prestazioni di Office 365 mediante l'uso della cronologia delle prestazioni e delle previsioni](performance-tuning-using-baselines-and-history.md)

[Piano di risoluzione dei problemi di prestazioni per Office 365](performance-troubleshooting-plan.md)

[Reti per la distribuzione di contenuti](content-delivery-networks.md)

[Test di connettività di Microsoft 365](https://aka.ms/netonboard)

[In che modo Microsoft crea la propria rete globale veloce e affidabile](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Blog di rete di Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
