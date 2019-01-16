---
title: Principi della connettività di rete di Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/14/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid: MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
description: Prima di iniziare la pianificazione della rete per la connettività di rete di Office 365, è importante comprendere i principi di connettività per la gestione in modo sicuro il traffico di Office 365 e ottenere prestazioni ottimali. In questo articolo consentono di acquisire familiarità con le indicazioni più recenti per l'ottimizzazione in modo sicuro la connettività di rete di Office 365.
ms.openlocfilehash: d319d99cdd413fe1df9e8f88d18742ad464bbb3b
ms.sourcegitcommit: f0ba0d8c62f802447bc9d07f5d877067156fbed5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "28021807"
---
# <a name="office-365-network-connectivity-principles"></a>Principi della connettività di rete di Office 365

Prima di iniziare la pianificazione della rete per la connettività di rete di Office 365, è importante comprendere i principi di connettività per la gestione in modo sicuro il traffico di Office 365 e ottenere prestazioni ottimali. In questo articolo consentono di acquisire familiarità con le indicazioni più recenti per l'ottimizzazione in modo sicuro la connettività di rete di Office 365.
  
Reti aziendali tradizionale create principalmente per fornire agli utenti l'accesso alle applicazioni e dati ospitati nella società utilizzate Datacenter con protezione avanzata perimetrale. Il modello tradizionale si presuppone che gli utenti potranno accedere le applicazioni e dati all'interno del perimetro della rete aziendale, attraverso collegamenti WAN dalle succursali o in remoto tramite connessioni VPN. 
  
L'adozione delle applicazioni SaaS quali Office 365 consente di spostare una combinazione di servizi e i dati all'esterno del perimetro della rete. Senza ottimizzazione, il traffico tra utenti e applicazioni SaaS è soggetta a latenza derivanti dalla controllo dei pacchetti, hairpins di rete, le connessioni involontarie agli endpoint geograficamente distanti e altri fattori. È possibile garantire le migliori prestazioni di Office 365 e l'affidabilità per comprendere e l'implementazione di informazioni sull'ottimizzazione chiave.
  
In questo articolo verranno fornite informazioni su:
  
- [Architettura di office 365](office-365-network-connectivity-principles.md#BKMK_Architecture) come si applica a connettività cliente nel cloud
- Aggiornati [principi di connettività di Office 365](office-365-network-connectivity-principles.md#BKMK_Principles) e sulle strategie per ottimizzare il traffico di rete e l'esperienza degli utenti finali
- Il [servizio web di Office 365 endpoint](office-365-network-connectivity-principles.md#BKMK_WebSvc), che consente agli amministratori di rete all'utilizzo di un elenco strutturato di endpoint per l'utilizzo di ottimizzazione della rete
- Indicazioni e ottimizzazione di [categorie di endpoint nuovo Office 365](office-365-network-connectivity-principles.md#BKMK_Categories)
- [Confronto di protezione della rete perimetrale con protezione endpoint](office-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- Opzioni di [ottimizzazione incrementale](office-365-network-connectivity-principles.md#BKMK_IncOpt) per il traffico di Office 365

## <a name="office-365-architecture"></a>Architettura di Office 365
<a name="BKMK_Architecture"> </a>

Office 365 è un cloud Software-as-a-Service (SaaS) distribuito che fornisce gli scenari di produttività e collaborazione mediante un insieme varie di micro servizi e applicazioni, ad esempio Skype Online Exchange, SharePoint Online per Online aziendale Microsoft I team, Exchange Online Protection, Office Online e molti altri. Mentre specifiche applicazioni di Office 365 potrebbero essere sulle relative funzionalità univoco applicato alla rete cliente e la connettività al cloud, condividono alcune entità chiave, obiettivi e modelli di architettura. Queste entità e modelli di architettura per la connettività sono tipiche per molte altre aree SaaS e contemporaneamente viene piuttosto diversa dai modelli di distribuzione più comuni della piattaforma come servizio e cloud dell'infrastruttura come servizio, ad esempio Microsoft Azure.
  
Una delle principali funzionalità dell'architettura di Office 365 (che è spesso perse non interpreta correttamente per i progettisti della rete) è che è un servizio distribuito realmente globale, nell'ambito di come utenti connetteranno ad essa. La posizione del tenant Office 365 di destinazione è importante comprendere la località di memorizzazione dei dati dei clienti in cloud, ma non implicano l'utilizzo dell'esperienza utente con Office 365 connessione direttamente a dischi contenente i dati. L'esperienza utente con Office 365 (incluse le prestazioni, l'affidabilità e altre caratteristiche di qualità importanti) comporta la connettività tramite un porte servizio altamente distribuiti che vengono scalati orizzontalmente in centinaia di Microsoft percorsi in tutto il mondo. Nella maggior parte dei casi, viene eseguita un'esperienza utente ottimale per consentire la rete del cliente per instradare le richieste utente al punto di ingresso del servizio Office 365 più vicino, anziché la connessione a Office 365 tramite un punto di uscita in una posizione centrale o l'area geografica.
  
Per la maggior parte dei clienti, gli utenti di Office 365 vengono distribuiti in più posizioni. Per ottenere risultati ottimali, devono essere esaminati i principi illustrati in questo documento dal con scalabilità orizzontale (non implementare la scalabilità verticale) punto di vista, concentrandosi sulle ottimizzare la connettività al punto più vicino di presenza nella rete globale Microsoft, non per il geografica posizione del tenant Office 365. In pratica, ciò significa che, anche se Office 365 tenant possono essere archiviati in una determinata posizione geografica, esperienze con Office 365 per tale tenant rimangono distribuita e possono essere presenti in molto Chiudi prossimità (rete) in ogni posizione degli utenti finali con tenant .
  
## <a name="office-365-connectivity-principles"></a>Principi di connettività di Office 365
<a name="BKMK_Principles"> </a>

È consigliabile i principi seguenti per ottenere prestazioni e la connettività di Office 365 ottimale. Utilizzare questi principi di connettività di Office 365 per gestire il traffico e ottenere prestazioni ottimali durante la connessione a Office 365.
  
L'obiettivo principale nella progettazione di rete è per ridurre al minimo la latenza per la riduzione del tempo di round trip (RTT) dalla rete in rete globale Microsoft backbone di rete pubblica di Microsoft che interconnette tutti i data center Microsoft a bassa latenza e cloud punti di ingresso distribuire tutto il mondo. Sono disponibili ulteriori su Microsoft Network globale in [modo Microsoft si basa la rete globale veloce e affidabile](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).
  
<a name="BKMK_P1"> </a>
### <a name="identify-and-differentiate-office-365-traffic"></a>Identificare e distinguere il traffico di Office 365

![Identificare il traffico di Office 365](media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
Che identifica il traffico di rete di Office 365 è il primo passaggio nella possibilità di distinguere questo tipo di traffico da generico del traffico di rete diretti a Internet. È possibile ottimizzare la connettività di Office 365 mediante l'implementazione di una combinazione di approcci come ottimizzazione route di rete, le regole del firewall, le impostazioni del proxy del browser e ignora l'ispezione dei dispositivi di rete per determinati endpoint.
  
Indicazioni di ottimizzazione di Office 365 precedente divisi endpoint di Office 365 in due categorie, **necessari** e **facoltativi**. Come sono stati aggiunti gli endpoint per il supporto di nuovi servizi di Office 365 e funzionalità, è stato riorganizzato endpoint di Office 365 in tre categorie: **Optimize**, **Consenti** e **predefinito**. Linee guida per ogni categoria si applica a tutti gli endpoint appartenenti alla categoria, semplificando comprendere e implementare le ottimizzazioni. 
  
Per ulteriori informazioni sulle categorie di endpoint di Office 365 e i metodi di ottimizzazione, vedere la sezione [categorie di endpoint nuovo Office 365](office-365-network-connectivity-principles.md#BKMK_Categories) .
  
Microsoft ora pubblica tutti gli endpoint di Office 365 come un servizio web e vengono fornite indicazioni sulla migliore per utilizzare questi dati. Per ulteriori informazioni su come il recupero e l'utilizzo degli endpoint di Office 365, vedere l'articolo [Office 365 URL e intervalli di indirizzi IP](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
<a name="BKMK_P2"> </a>
### <a name="egress-network-connections-locally"></a>Uscire dalle connessione di rete a livello locale

![Uscire dalle connessione di rete a livello locale](media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
In uscita locale DNS e Internet è di importanza critica per ridurre la latenza della connessione e assicurarsi che le connessioni utente vengano effettuate fino al punto di ingresso a servizi di Office 365 più vicino. In una topologia di rete complessa, è importante per l'implementazione DNS locale sia servizi esterni Internet locali contemporaneamente. Per ulteriori informazioni su come Office 365 consente di indirizzare le connessioni client più vicino punto di ingresso, vedere l'articolo [Connettività dei Client](https://support.office.com/en-us/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b).
  
Prima dell'introduzione di servizi cloud quali Office 365, utenti finali la connettività Internet come un fattore di progettazione all'architettura di rete è stata relativamente semplici. Quando i siti web e servizi Internet sono distribuiti in tutto il mondo, latenza tra i punti di uscita aziendale e qualsiasi endpoint di destinazione specificato dipende in gran parte della distanza geografica.
  
In un'architettura di rete tradizionale, tutte le connessioni in uscita Internet passare attraverso la rete aziendale e in uscita da una posizione centrale. Come migliorare offerte cloud di Microsoft, un'architettura distribuita di rete con connessione Internet è diventato critica per il supporto dei servizi cloud sensibili alla latenza. La rete globale Microsoft sono stata progettata per soddisfare i requisiti di latenza con l'infrastruttura distribuita porta anteriore Service, un'infrastruttura dinamica dei punti di ingresso globale che esegue il routing in ingresso connessioni ai servizi cloud al punto di ingresso più vicino. Si tratta di ridurre la lunghezza di "Ultimo miglio" per i clienti Microsoft cloud mediante l'abbreviazione efficacemente la route tra il cliente e nel cloud.
  
Enterprise WAN spesso sono progettati per il traffico di rete backhaul per sede centrale società per l'ispezione prima uscita a Internet, in genere tramite uno o più server proxy. Nel diagramma seguente viene illustrata una topologia di rete.
  
![Modello di rete aziendale tradizionale](media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
Poiché viene eseguito Office 365 sulla rete globale Microsoft, che include server front-end in tutto il mondo, è spesso che un server front-end corrispondenza della posizione dell'utente. Fornendo uscita Internet locale e la configurazione server DNS interni per fornire la risoluzione dei nomi locali per gli endpoint di Office 365, il traffico di rete destinato a Office 365 può connettersi ai server front-end di Office 365 più vicino possibile all'utente. Nel diagramma seguente è illustrato un esempio di una topologia di rete che consente agli utenti che si connettono da office principale, succursale e sedi remote di seguire il percorso più breve al punto di ingresso di Office 365 più vicino.
  
![Modello di rete WAN con punti di uscita regionali](media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
Abbreviare il percorso di rete per Office 365 punti di ingresso in questo modo possono migliorare le prestazioni di connettività e l'utente finale esperienza in Office 365 e può inoltre richiedere la riduzione dell'impatto delle future modifiche all'architettura di rete in termini di prestazioni di Office 365 e affidabilità.
  
Inoltre, le richieste DNS possono provocare latenza se il server DNS di risposta è distante relativi alla disponibilità. È possibile ridurre la latenza di nome soluzione provisioning server DNS locali nelle succursali e verificando che sono configurati in modo appropriato ai record DNS di cache.
  
Durante l'uscita internazionale è possono utilizzare anche per Office 365, il modello di integrazione applicativa ottimali, è possibile fornire sempre uscita di rete nel percorso dell'utente, indipendentemente dal fatto che questo nella rete aziendale o sedi remote, ad esempio home, in hotel o café e aeroporti. In questo modello di uscita diretta locale è rappresentato nella figura riportata di seguito.
  
![Architettura di rete in uscita locale](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
Le aziende che hanno adottato Office 365 possono avvalersi dell'architettura distribuita porta anteriore del servizio di rete globale Microsoft, assicurando connessioni utente a Office 365 route possibile più breve della voce di rete globale Microsoft più vicino punto. A tale scopo, l'architettura di rete in uscita locale che consente il traffico di Office 365 eseguire il routing in uscita più vicino, indipendentemente dalla posizione utente.
  
Tramite il modello tradizionale, l'architettura di uscita locale offre i vantaggi seguenti:
  
- Garantisce prestazioni ottimali di Office 365 all'ottimizzazione delle route lunghezza. Le connessioni utente finale in modo dinamico vengono instradate al punto di ingresso di Office 365 più vicino dall'infrastruttura distribuita porta anteriore di servizio.
- Riduce il carico dell'infrastruttura di rete aziendale consentendo uscita locale.
- Consente di proteggere le connessioni a entrambe le estremità per sfruttare la sicurezza dell'endpoint dei client e funzionalità di protezione cloud.

<a name="BKMK_P3"> </a>
### <a name="avoid-network-hairpins"></a>Evitare fenomeni di "hairpinning" di rete

![Evitare hairpins](media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
Come un generale, la route più breve, più diretta tra più endpoint di Office 365 e utente offrirà prestazioni ottimali. Effetti "hairpin" una rete WAN o VPN il traffico diretto per una destinazione specifica innanzitutto viene indirizzata a un'altra posizione intermedia (ad esempio sicurezza stack, broker di accesso cloud, del gateway web basato su cloud), Introduzione alla latenza e potenziale reindirizzamento a un endpoint geograficamente distanti. Rete hairpins può anche essere causato da routing peering aree non efficienti o non ottimali ricerche DNS (remote).
  
Per assicurarsi che la connettività di Office 365 non è legate hairpins rete anche nel caso di uscita locale, verificare se il provider di servizi Internet che consente di fornire servizi esterni Internet per la posizione dell'utente ha una relazione peering diretta Microsoft Network globale in chiudere vicino al percorso. È possibile anche configurare per inviare traffico attendibile di Office 365 direttamente il routing in uscita, anziché l'inoltro o tunnel attraverso un cloud di terze parti o un fornitore di protezione di rete basato su cloud che i processi del traffico diretti a Internet. Risoluzione dei nomi DNS locale di Office 365 endpoint consente di garantire che oltre il routing diretto, i punti di ingresso collaboratori più stretti di Office 365 sono utilizzati per le connessioni utente.
  
Se si utilizza servizi di sicurezza per il traffico di Office 365 o reti basate su cloud, verificare che l'effetto hairpinning viene valutata e viene considerato l'impatto sulle prestazioni di Office 365. Questa operazione può essere eseguita esaminando il numero e le posizioni dei percorsi di provider del servizio tramite cui il traffico viene inoltrato in relazione al numero di succursali e Microsoft Network globale peering punti qualità della relazione peering rete di provider di servizi di provider di servizi Internet, Microsoft e l'impatto sulle prestazioni di backhauling nell'infrastruttura del provider del servizio.
  
A causa dell'elevato numero di posizioni distribuite con punti di ingresso di Office 365 e della loro prossimità agli utenti finali, il routing del traffico Office 365 per qualsiasi provider di rete o di sicurezza di terze parti possono avere un impatto negativo sulle connessioni di Office 365 se non è rete del provider configurato per Office 365 ottimale peering.
  
<a name="BKMK_P4"> </a>
### <a name="bypass-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>Ignorare i proxy, dispositivi di controllo del traffico e le tecnologie di protezione duplicati

![Ignorare i proxy, dispositivi di controllo del traffico e le tecnologie di protezione duplicati](media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
I clienti aziendali consigliabile consultare la protezione di rete e i metodi di riduzione dei rischi specifici per Office 365 associata traffico e utilizzano le funzionalità di protezione di Office 365 per ridurre gli affidarsi a discreto, alcun impatto sulle prestazioni e la protezione della rete costosa tecnologie per il traffico di rete di Office 365.
  
La maggior parte delle reti aziendali applicare la protezione di rete per il traffico Internet utilizzando le tecnologie come proxy, ispezione SSL, controllo dei pacchetti e sistemi di prevenzione della perdita di dati. Tali tecnologie offrono riduzione dei rischi importanti per le richieste Internet generiche ma che possono ridurre drasticamente le prestazioni, scalabilità e la qualità dell'esperienza utente finale se applicata a endpoint di Office 365.
  
<a name="BKMK_WebSvc"> </a>
#### <a name="office-365-endpoints-web-service"></a>Servizio web di Office 365 endpoint

Gli amministratori di Office 365 possono utilizzare uno script o chiamate REST all'utilizzo di un elenco degli endpoint dagli endpoint Office 365 strutturato servizio web e aggiornare le configurazioni del firewall perimetrale e altri dispositivi di rete. In tal modo che il traffico associato per Office 365 è identificato, trattato in modo appropriato e gestito in modo diverso dal traffico di rete associato per i siti web Internet generico e spesso sconosciuto. Per ulteriori informazioni su come utilizzare gli endpoint di Office 365 al servizio web, vedere l'articolo [Office 365 URL e intervalli di indirizzi IP](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>Script PAC (Proxy la configurazione automatica)
<a name="BKMK_WebSvc"> </a>

Gli amministratori di Office 365 possono creare script PAC (Proxy la configurazione automatica) che possono essere inviati nei computer degli utenti tramite WPAD o oggetto Criteri di gruppo. Script PAC possono essere utilizzati per ignorare i proxy per le richieste di Office 365 degli utenti WAN o VPN, consentire il traffico di Office 365 da utilizzare connessioni Internet dirette anziché attraversare della rete aziendale.
  
#### <a name="office-365-security-features"></a>Caratteristiche di protezione di Office 365
<a name="BKMK_WebSvc"> </a>

Microsoft è trasparente sulla sicurezza datacenter, sicurezza operativa e la riduzione del rischio intorno a server di Office 365 e gli endpoint di rete che essi rappresentano. Caratteristiche di Office 365 protezione incorporata sono disponibili per la riduzione dei rischi di protezione di rete, quali prevenzione della perdita di dati, antivirus, autenticazione a più fattori, casella di blocco dei clienti, avanzate Threat Protection, Business Intelligence di Office 365 rischio, sicura di Office 365 Punteggio, Exchange Online Protection e la protezione della rete DDOS.
  
Per ulteriori informazioni sulla protezione di rete globale e Data Center Microsoft, vedere il [Centro protezione di Microsoft](https://www.microsoft.com/en-us/trustcenter/security).
  
## <a name="new-office-365-endpoint-categories"></a>Nuove categorie di endpoint di Office 365
<a name="BKMK_Categories"> </a>

Gli endpoint di Office 365 rappresentano un set di variabile di indirizzi di rete e subnet. Endpoint potrebbero essere URL, indirizzi IP o IP compreso e alcuni endpoint sono elencate le porte TCP/UDP specifiche. Gli URL possono essere costituiti da un FQDN come *account.office.net* o un URL con caratteri jolly like * \*. office365.com*.
  
> [!NOTE]
> I percorsi di endpoint di Office 365 all'interno della rete non sono direttamente correlati al percorso dei dati relativi al tenant di Office 365. Per questo motivo, i clienti risulterà in Office 365 come servizio distribuito e globale e non devono tentare di bloccare le connessioni di rete agli endpoint di Office 365 in base ai criteri geografici.
  
Nel nostro precedenti indicazioni per la gestione del traffico di Office 365, gli endpoint erano organizzati in due categorie, **necessari** e **facoltativi**. Endpoint all'interno di ogni categoria necessari ottimizzazioni diverse in base all'importanza del servizio e molti clienti dovuto affrontare i problemi nel che giustifichi l'applicazione della stessa ottimizzazione di rete per un elenco completo di Office 365 URL e gli indirizzi IP. 
  
Nel nuovo modello, gli endpoint sono suddivisi in tre categorie, **Optimize**, **Consenti** e **predefinito**, fornire un pivot basata sulla priorità nella posizione in cui concentrare gli sforzi di ottimizzazione della rete per il miglioramento delle prestazioni ottimali e restituire investimento. I punti finali vengono consolidati nelle categorie sopra la riservatezza dell'esperienza utente effettivi busta qualità, volume e prestazioni di rete di scenari e facilità di implementazione di base. Ottimizzazioni consigliate è possibile applicare allo stesso modo a tutti gli endpoint di una determinata categoria.
  
- **Ottimizza** endpoint necessari per la connettività a ogni servizio Office 365 e rappresentano oltre il 75% di Office 365 della larghezza di banda, le connessioni e dei dati. Questi due estremi rappresentano gli scenari di Office 365 più sensibili alle prestazioni, la latenza e disponibilità in rete. Tutti gli endpoint sono ospitati in datacenter Microsoft. La frequenza di modifica per gli endpoint di questa categoria dovrebbe essere molto inferiore rispetto a quello per l'endpoint in due categorie. Questa categoria include un set di dimensioni molto piccolo (dovrebbe essere ~ 10) della chiave gli URL e un insieme definito di subnet IP dedicate a carichi di lavoro di base di Office 365, ad esempio Exchange Online, SharePoint Online, Skype per Business Online e Microsoft Teams.

    Un elenco degli endpoint critici ben definito ridotto essere utili per pianificare e implementare le ottimizzazioni rete valore elevato per queste destinazioni più semplice e rapido.

    Esempi di endpoint *Optimize* *https://outlook.office365.com* , *https://\<tenant\>. sharepoint.com* e *https://\<tenant\>-my.sharepoint.com* .

    Metodi di ottimizzazione includono:

  - Bypass o proprietà consentite endpoint *Optimize* sui dispositivi di rete e sui servizi che eseguono intercettazione traffico, SSL e la decrittografia, controllo dei complete pacchetti filtro contenuto.
  - Ignorare i dispositivi proxy locali e servizi basati su cloud proxy comunemente utilizzati per l'esplorazione di Internet generico.
  - Definire la priorità la valutazione degli endpoint come completamente attendibile per i sistemi perimetrale e l'infrastruttura di rete.
  - Impostare la priorità di riduzione o eliminazione di backhauling WAN e facilitare diretto distribuita uscita basati su Internet per questi endpoint più vicino utenti/succursali possibile.
  - Facilitare la connessione diretta con gli endpoint cloud per gli utenti VPN implementando tunnel diviso.
  - Assicurarsi che gli indirizzi IP restituiti dalla risoluzione dei nomi DNS corrispondano il percorso di routing in uscita per gli endpoint.
  - Definire la priorità questi endpoint per l'integrazione della WAN SD per il routing diretta, minima la latenza nel punto più vicino peering Internet della rete globale Microsoft.

- **Consenti** endpoint necessari per la connettività a funzionalità e servizi specifici di Office 365, ma non sono i cursori sensibili alle prestazioni di rete e latenza a quelli della categoria *Ottimizza* . Footprint di rete globale di queste endpoint dal punto di vista della proprietà count della larghezza di banda e la connessione è molto più piccole. Questi due estremi dedicati a Office 365 e ospitati nei data center Microsoft. Rappresentano un'ampia gamma di servizi di Office 365 micro e le dipendenze tra (sull'ordine degli URL di circa 100) e si prevede verranno modificati una velocità superiore rispetto a quelli della categoria *Optimize* . Non tutti gli endpoint di questa categoria sono associati definita subnet IP dedicata.

    Le ottimizzazioni di rete per gli endpoint *Consenti* possono migliorare l'esperienza utente di Office 365, ma alcuni clienti possono scegliere come ambito le ottimizzazioni più ristretto per ridurre al minimo le modifiche apportate alla rete.

    Esempi di endpoint *Consenti* *https://\*. protection.outlook.com* e *https://accounts.accesscontrol.windows.net*.

    Metodi di ottimizzazione includono:

  - Bypass o proprietà consentite endpoint *Consenti* sui dispositivi di rete e sui servizi che eseguono intercettazione traffico, SSL e la decrittografia, controllo dei complete pacchetti filtro contenuto.
  - Definire la priorità la valutazione degli endpoint come completamente attendibile per i sistemi perimetrale e l'infrastruttura di rete.
  - Impostare la priorità di riduzione o eliminazione di backhauling WAN e facilitare diretto distribuita uscita basati su Internet per questi endpoint più vicino utenti/succursali possibile.
  - Assicurarsi che gli indirizzi IP restituiti dalla risoluzione dei nomi DNS corrispondano il percorso di routing in uscita per gli endpoint.
  - Definire la priorità questi endpoint per l'integrazione della WAN SD per il routing diretta, minima la latenza nel punto più vicino peering Internet della rete globale Microsoft.

- Gli endpoint **predefinito** rappresentano servizi di Office 365 e le dipendenze esistenti che non richiedono alcun ottimizzazione e possono essere gestite da reti dei clienti come Internet normale associato il traffico. Si noti che alcune endpoint nella categoria potrebbe non essere disponibile nei data center Microsoft. Ad esempio *https://odc.officeapps.live.com* e *https://appexsin.stb.s-msn.com*.

Per ulteriori informazioni sulle tecniche di ottimizzazione della rete di Office 365, vedere l'articolo [endpoint di gestione di Office 365](https://support.office.com/en-us/article/managing-office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a#ID0EAEAAA=0._Overview).
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>Confronto di protezione della rete perimetrale con protezione endpoint
<a name="BKMK_SecurityComparison"> </a>

L'obiettivo di protezione di rete tradizionale è per la protezione avanzata del perimetro della rete aziendale da intrusioni e gli attacchi dannosi. Come le organizzazioni adottano Office 365, alcuni servizi di rete e i dati sono parzialmente o completamente la migrazione nel cloud. Come avviene alcun cambiamento fondamentale all'architettura di rete, questo processo richiede una nuova valutazione della protezione di rete che tiene conto emergenti fattori:
  
- Adottato servizi cloud, dati e servizi di rete vengono distribuiti tra centri dati locali e cloud e protezione perimetrale non è più adeguata in modo autonomo.
- Utenti remoti connettersi alle risorse aziendali in centri dati locali e cloud da posizioni includerlo nel controllo, ad esempio include, hotel e Internet café.
- Funzionalità di sicurezza progettato appositamente per sempre più incorporate in servizi cloud potenzialmente integrare o sostituire i sistemi di protezione esistente.

Microsoft offre un'ampia di Office 365 funzionalità di protezione e vengono fornite indicazioni per utilizzare le procedure consigliate utili per garantire la protezione dei dati e di rete per Office 365. Procedure consigliate includono quanto segue:
  
- **Usa autenticazione a più fattori (MFA)** MFA consente di aggiungere un ulteriore livello di protezione di una strategia di password complesse da richiedere agli utenti di confermare una telefonata, messaggio di testo o una notifica di app nel telefono smart dopo aver immesso correttamente le password.

- **Utilizzare Office 365 Cloud App protezione** Impostare i criteri per agire su di esso e tenere traccia di attività anomala. Impostare gli avvisi con Office 365 Cloud App protezione in modo che gli amministratori possono esaminare l'attività dell'utente non comune o rischioso, ad esempio il download di grandi quantità di dati, più tentativi di accesso non riuscito o connessioni da un indirizzo IP sconosciuto o pericoloso indirizzi.

- **Configurare la prevenzione della perdita di dati (DLP)** DLP consente di identificare i dati riservati e creare i criteri che consentono di impedire agli utenti di intenzionalmente o accidentalmente i dati di condivisione. DLP può essere utilizzato in Office 365, inclusi Exchange Online, SharePoint Online e OneDrive in modo che gli utenti possono garantire la conformi senza interrompere il flusso di lavoro.

- **Archivio protetto analisi di utilizzo** Come un amministratore di Office 365, è possibile utilizzare archivio protetto cliente per controllare la modalità del supporto tecnico accede dei dati durante una sessione di supporto. In casi in cui il tecnico richiede l'accesso ai dati per risolvere un problema, archivio protetto cliente consente di approvare o rifiutare le richieste di accesso.

- **Utilizzare punteggio protetta di Office 365** Punteggio sicura è uno strumento di analitica protezione consigliate da eseguire per ridurre ulteriormente il rischio da. Punteggio sicura legge le impostazioni di Office 365 e le attività e li confronta con una linea di base stabilita da Microsoft. Verrà visualizzato un punteggio basato sulla modalità allineato con le procedure consigliate di sicurezza.

Un approccio globale per aumentare la protezione deve basarsi sulle operazioni seguenti:
  
- Sicurezza perimetrale per raggiungere l'endpoint protezione tramite l'applicazione basata su cloud e caratteristiche di protezione di Office client vengono spostate enfasi.
  - Ridurre le dimensioni del perimetro di protezione al datacenter
  - Impostare come attendibili equivalenti per i dispositivi utente all'interno dell'ufficio o presso sedi remote
  - Concentrarsi sulla protezione di posizione dell'utente e il percorso dei dati
  - Computer utente gestito dispongono di attendibilità più elevato con protezione endpoint
- Gestire la sicurezza di tutte le informazioni modo globale, non concentrare l'attenzione sui perimetro
  - Consente di ridefinire WAN e creazione di protezione della rete perimetrale per consentire il traffico attendibile di ignorare i dispositivi di sicurezza e la separazione dispositivi non gestiti a rete Wi-Fi guest.
  - Riduce i requisiti di protezione di rete del bordo WAN aziendale
  - Alcuni dispositivi di protezione di rete perimetrale come firewall, sono tuttavia obbligatori, ma caricare viene ridotta
  - Assicura locale in uscita per il traffico di Office 365
- Miglioramenti possono essere gestiti in modo incrementale, come descritto nella sezione [ottimizzazione incrementale](office-365-network-connectivity-principles.md#BKMK_IncOpt) . Alcune tecniche di ottimizzazione possono offrire migliori rapporti tra costi/benefici a seconda dell'architettura di rete e si consiglia di scegliere le ottimizzazioni che più indicate per l'organizzazione.

Per ulteriori informazioni sulla protezione di Office 365 e la conformità, vedere l'articolo [Panoramica della sicurezza e conformità in Office 365](https://support.office.com/en-us/article/overview-of-security-and-compliance-in-office-365-dcb83b2c-ac66-4ced-925d-50eb9698a0b2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
## <a name="incremental-optimization"></a>Ottimizzazione incrementale
<a name="BKMK_IncOpt"> </a>

È stata rappresentata il modello di connettività di rete ideale per SaaS più indietro in questo articolo, ma per molte organizzazioni di grandi dimensioni con architetture di rete in passato complesse, non sarà una soluzione pratica direttamente effettuare tutte le modifiche. In questa sezione viene illustrato un numero di modifiche incrementali che consentono di migliorare l'affidabilità e prestazioni di Office 365.
  
I metodi che verrà utilizzato per ottimizzare il traffico di Office 365 varia a seconda della topologia di rete e i dispositivi di rete che è stato implementato. Per le grandi aziende con molti percorsi e procedure di protezione di rete complessa, saranno necessario sviluppare una strategia che include più o tutti i principi elencati nella sezione [principi di connettività di Office 365](office-365-network-connectivity-principles.md#BKMK_Principles) , mentre organizzazioni di piccole dimensioni possono solo è necessario prendere in considerazione uno o due.
  
È possibile eseguire l'ottimizzazione come un processo incrementale, l'applicazione di ogni metodo successivamente. Nella tabella seguente vengono elencati i metodi di ottimizzazione della chiave in ordine dell'impatto sulla latenza e l'affidabilità per il numero massimo di utenti.
  
|**Metodo di ottimizzazione**|**Descrizione**|**Impatto**|
|:-----|:-----|:-----|
|Risoluzione DNS locale e in uscita Internet  <br/> |Effettuare il provisioning di server DNS locali in ogni sede e verificare che in uscita connessioni di Office 365 a Internet più vicino possibile, per la posizione dell'utente.  <br/> | Ridurre al minimo la latenza  <br/>  Migliorare la connettività affidabile al punto di ingresso collaboratori più stretti di Office 365  <br/> |
|Aggiungere punti di uscita regionali  <br/> |Se la rete aziendale dispone di più posizioni ma punto di una sola uscita, aggiungere punti di uscita regionale per consentire agli utenti di connettersi al punto di ingresso di Office 365 più vicino.  <br/> | Ridurre al minimo la latenza  <br/>  Migliorare la connettività affidabile al punto di ingresso collaboratori più stretti di Office 365  <br/> |
|I proxy di bypass e gli strumenti di controllo  <br/> |Configurare browser con i file PAC inviare richieste di Office 365 direttamente ai punti di uscita.  <br/> Configurare edge router e nei firewall per consentire il traffico di Office 365 senza ispezione.  <br/> | Ridurre al minimo la latenza  <br/>  Ridurre il carico sui dispositivi di rete  <br/> |
|Abilita connessione diretta per gli utenti VPN  <br/> |Per gli utenti VPN, abilitare le connessioni di Office 365 per la connessione direttamente dalla rete dell'utente anziché sul tunnel VPN implementando tunnel diviso.  <br/> | Ridurre al minimo la latenza  <br/>  Migliorare la connettività affidabile al punto di ingresso collaboratori più stretti di Office 365  <br/> |
|Eseguire la migrazione da WAN tradizionale a SD WAN  <br/> |SD-WAN (Software definito Wide Area Network) semplificare la gestione WAN e migliorare le prestazioni, sostituendo tradizionale router WAN con dispositivi di rete, simile alla virtualizzazione delle risorse di elaborazione utilizzando macchine virtuali (VM).  <br/> | Migliorare le prestazioni e gestibilità del traffico WAN  <br/>  Ridurre il carico sui dispositivi di rete  <br/> |
