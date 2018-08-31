---
title: Implementazione di ExpressRoute per Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/5/2017
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
ms.assetid: 77735c9d-8b80-4d2f-890e-a8598547dea6
description: ExpressRoute per Office 365 fornisce un percorso alternativo routing molti internet con connessione a servizi di Office 365. L'architettura di ExpressRoute per Office 365 si basa su annunciare prefissi IP pubblici di servizi di Office 365 che sono già accessibili tramite Internet nei provisioning circuiti ExpressRoute per le successive ridistribuzione di questi prefissi IP in la rete. Con ExpressRoute si attiva in modo efficace diverse diversi percorsi di routing, tramite internet ed ExpressRoute, per molti servizi di Office 365. Questo stato del routing nella rete può rappresentare un cambiamento di come è stata progettata la topologia di rete interna.
ms.openlocfilehash: c4479a236d1419293dbd433e8d3c10a11ea5fb45
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541472"
---
# <a name="implementing-expressroute-for-office-365"></a>Implementazione di ExpressRoute per Office 365

ExpressRoute per Office 365 fornisce un percorso alternativo routing molti internet con connessione a servizi di Office 365. L'architettura di ExpressRoute per Office 365 si basa su annunciare prefissi IP pubblici di servizi di Office 365 che sono già accessibili tramite Internet nei provisioning circuiti ExpressRoute per le successive ridistribuzione di questi prefissi IP in la rete. Con ExpressRoute si attiva in modo efficace diverse diversi percorsi di routing, tramite internet ed ExpressRoute, per molti servizi di Office 365. Questo stato del routing nella rete può rappresentare un cambiamento di come è stata progettata la topologia di rete interna.
  
 **Stato:** Guida completa v2
  
È necessario pianificare attentamente la ExpressRoute per l'implementazione di Office 365 per gestire la complessità della rete di disporre di routing disponibili tramite sia una dedicata a commutazione di circuito con le route inserite in rete core e internet. Se l'utente e al team di non eseguire i dettagli della pianificazione e test in questa Guida, non esiste un rischio elevato che potrai intermittente o la perdita della connettività a Office 365 totale servizi quando è abilitata a commutazione di circuito ExpressRoute.
  
Per una corretta implementazione, è necessario analizzare i requisiti dell'infrastruttura, attraversano assessment informazioni dettagliate sulla rete e progettare, pianificare l'implementazione in modo graduale e controllato attentamente e creare un piano test e convalida dettagliata. Per un ambiente di grandi dimensioni, distribuito non è potrebbe venire eseguito implementazioni estendersi su alcuni mesi. In questa guida è progettata per utili per pianificare in anticipo.
  
Distribuzioni corretta di grandi dimensioni potrebbero richiedere sei mesi nella pianificazione e spesso includono i membri del team da molte aree nell'organizzazione inclusi rete, gli amministratori del server Proxy e Firewall, gli amministratori di Office 365, sicurezza, il supporto degli utenti finali, project gestione e l'approvazione. Investimenti nel processo di pianificazione consente di ridurre la probabilità che saranno verificarsi gli errori di distribuzione conseguenti tempi di inattività o la risoluzione dei problemi di complessa e costosa.
  
Si prevede che i prerequisiti seguenti per essere completata prima che venga avviata la Guida all'implementazione.
  
1. È stata completata una valutazione della rete per determinare se ExpressRoute è consigliato e approvati.

2. È stato selezionato un provider di servizi di rete ExpressRoute. Per ulteriori informazioni sull' [ExpressRoute partner e percorsi peering](https://azure.microsoft.com/documentation/articles/expressroute-locations/).

3. Si è già letto e comprendere la [documentazione ExpressRoute](https://azure.microsoft.com/documentation/services/expressroute/) e la rete interna è in grado di soddisfare i prerequisiti ExpressRoute end-to-end.

4. Il team ha leggere tutte le indicazioni pubblici e documentazione al [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365), [https://aka.ms/ert](https://aka.ms/ert)e controllare la serie [ExpressRoute Azure per Office 365 formazione](https://channel9.msdn.com/series/aer) su Channel 9 per acquisire una conoscenza dei dettagli tecnici critici inclusi:

      - Dipendenze internet dei servizi SaaS.

      - Come evitare route asimmetriche e gestiscono il routing complessi.

      - Come incorporare la protezione del perimetro, disponibilità e controlli del livello di applicazione.

## <a name="begin-by-gathering-requirements"></a>Iniziare con la raccolta di requisiti
<a name="requirements"> </a>

Avviare per determinare quali funzionalità e servizi che si prevede di utilizzare all'interno dell'organizzazione. È necessario determinare verranno utilizzate le funzionalità dei diversi servizi di Office 365 e i percorsi di rete ospiterà gli utenti che utilizzano le caratteristiche. Con il catalogo di scenari, è necessario aggiungere gli attributi di rete per ognuno di questi scenari richiedono; ad esempio se l'endpoint di Office 365 sono disponibili su ExpressRoute o non e flussi di traffico di rete in ingresso e in uscita.
  
Per raccogliere i requisiti dell'organizzazione:
  
- Catalogo il traffico di rete in ingresso e in uscita per l'organizzazione utilizza i servizi di Office 365. Consultare pagina gli intervalli di indirizzi IP e gli URL di Office 365 per una descrizione dei flussi di richiedono diversi scenari di Office 365.

- Raccogliere documentazione della topologia di rete esistente che mostra i dettagli dei interno backbone WAN e topologia, la connettività dei siti satellitari, la connettività utente miglio ultimo, il routing a punti di uscita alla rete perimetrale e proxy servizi.

  - Identificare gli endpoint del servizio in ingresso nei diagrammi di rete che Office 365 e altri servizi Microsoft eseguirà la connessione, che mostra i percorsi internet e proposti ExpressRoute connessione.

  - Identificare tutte le posizioni geografiche utente e la connettività WAN tra le posizioni insieme a quelli che attualmente dispongono di un uscita a internet e quelli che sono proposto per avere un'uscita in una posizione peering ExpressRoute.

  - Identificare tutti i dispositivi di server perimetrali, ad esempio proxy, firewall e così via e delle relazioni flussi continui via Internet ed ExpressRoute del catalogo.

  - Se gli utenti finali avranno accesso ai servizi di Office 365 tramite il routing diretto o il proxy di applicazione indiretti per i flussi di Internet e di ExpressRoute del documento.

- Aggiungere il percorso del tenant e soddisfare-me percorsi al diagramma di rete.

- Valutare le osservati e previsti delle prestazioni e della latenza delle caratteristiche di rete da posizioni utente principali per Office 365. Tenere presente che Office 365 è un insieme globale e distribuito dei servizi e gli utenti si connetteranno a percorsi che possono essere diversi dal percorso di loro tenant. Per questo motivo, è consigliabile misurare e ottimizzazione per la latenza tra l'utente e il bordo più vicino di rete globale Microsoft su connessioni ExpressRoute e Internet. Per facilitare l'esecuzione di questa attività, è possibile utilizzare i risultati di valutazione della rete.

- Protezione della rete aziendale e i requisiti di disponibilità elevata che devono essere soddisfatti con la nuova connessione ExpressRoute. Ad esempio, come gli utenti continuano a ottenere l'accesso a Office 365 in caso di uscita Internet o errore a commutazione di circuito ExpressRoute.

- Documento di rete che Office 365 in ingresso e in uscita scorre verrà utilizzato il percorso Internet e che verrà utilizzato ExpressRoute. Le specifiche aree geografiche degli utenti e i dettagli della topologia di rete locale potrebbe essere necessario pianificare può essere diverso dal percorso di un utente a un altro.

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a>Il traffico di rete in ingresso e in uscita del catalogo
<a name="trafficCatalog"> </a>

Per ridurre al minimo la complessità di rete di routing e di altro, si consiglia di utilizzare solo ExpressRoute per Office 365 per i flussi di traffico di rete necessari per accedere tramite una connessione dedicata a causa di requisiti normativi o come risultato di valutazione della rete. È inoltre consigliabile distribuire gradualmente l'ambito della ExpressRoute routing e l'approccio di rete in ingresso e in uscita flussi di traffico come diversi passaggi del progetto di implementazione. Distribuire ExpressRoute per Office 365 per avviata dall'utente solo flussi di traffico di rete in uscita e di abbandono flussi di traffico di rete in ingresso tramite Internet consentono di controllare l'aumento rischi di introduzione aggiuntivi e la complessità topologiche asimmetrica possibilità di routing.
  
Catalogo del traffico di rete deve includere voci di tutte le connessioni di rete in ingresso e in uscita tra la rete locale e Microsoft, è necessario.
  
- Flussi di traffico di rete in uscita sono tutti gli scenari di cui viene attivata una connessione dall'ambiente locale, ad esempio da client interni o più server, con una destinazione dei servizi Microsoft. Tali connessioni possono essere direttamente a Office 365 o indiretti, ad esempio quando la connessione viene inoltrata tramite i server proxy, firewall o altri dispositivi di rete nel percorso a Office 365.

- Flussi di traffico di rete in ingresso sono tutti gli scenari di cui una connessione viene avviata dal cloud Microsoft a un host locale. Le connessioni in genere necessario passare attraverso firewall e altre infrastruttura di protezione che richiede di criteri di protezione dei clienti per i flussi originati esternamente.

Leggere la sezione **simmetria route garanzia** dell'articolo [Routing con ExpressRoute per Office 365](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) per determinare quali servizi verranno inviare traffico in ingresso e cercare nella colonna contrassegnata **ExpressRoute per Office 365** in [Office 365 endpoint](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) articolo di riferimento per determinare il resto delle informazioni di connettività.
  
Per ogni servizio che richiede una connessione in uscita, è opportuno descrivere la connettività pianificata per il servizio, inclusi il routing di rete, la configurazione del proxy, controllo dei pacchetti e della larghezza di banda è necessario.
  
Per ogni servizio che richiede una connessione in ingresso, sarà necessario alcune informazioni aggiuntive. Server di Microsoft cloud stabilirà connessioni alla rete locale. Per verificare che le connessioni vengono eseguite correttamente, è opportuno descrivere tutti gli aspetti della connettività, inclusi; le voci DNS pubbliche per i servizi che accettano le connessioni in ingresso, il CIDR formattato come in ingresso NAT e indirizzi IP IPv4, quali dispositivi ISP sono presente, o NAT di origine viene gestito per le connessioni.
  
È consigliabile leggere le connessioni in ingresso indipendentemente dal fatto connette tramite internet o non è stato introdotto ExpressRoute per garantire il routing asimmetrica. In alcuni casi, locale gli endpoint di servizi di Office 365 avviare le connessioni in ingresso al maggio inoltre necessario accedere da altri Microsoft e i servizi non Microsoft. È fondamentale che l'abilitazione di questi servizi Office 365 ai fini del routing ExpressRoute non provoca problemi di altri scenari. In molti casi, i clienti potrebbe essere necessario implementare le modifiche specifiche per la rete interna, ad esempio origine base NAT per garantire che viene disposto in ingresso da Microsoft rimanga simmetrico dopo aver abilitato ExpressRoute.
  
Di seguito è riportato un esempio del livello di dettaglio necessario. In questo caso Exchange Hybrid indirizza al sistema locale su ExpressRoute.

|**Proprietà di connessione**|**Valore**|
|:-----|:-----|
|**Direzione del traffico di rete** <br/> |In ingresso  <br/> |
|**Servizio** <br/> |Ambiente Exchange ibrido  <br/> |
|**Pubblico endpoint di Office 365 (origine)** <br/> |Exchange Online (indirizzi IP)  <br/> |
|**Endpoint locale pubblico (destinazione)** <br/> |5.5.5.5  <br/> |
|**Voce (Internet) DNS pubblica** <br/> |Autodiscover.contoso.com  <br/> |
|**Endpoint locale da utilizzare per altri servizi di Microsoft (non Office 365)** <br/> |No  <br/> |
|**Endpoint locale verrà utilizzato da utenti/sistemi su Internet** <br/> |Sì  <br/> |
|**Sistemi interni pubblicato tramite endpoint pubblico** <br/> |Ruolo accesso client di Exchange Server (locale) 192.168.101, 192.168.102, 192.168.103  <br/> |
|**Annuncio pubblicitario IP dell'endpoint pubblico** <br/> |**A Internet**: 5.5.0.0/16  <br/> **Per ExpressRoute**: 5.5.5.0/24  <br/> |
|**Controlli di sicurezza/perimetrale** <br/> |**Percorso Internet**: DeviceID_002  <br/> **Percorso ExpressRoute**: DeviceID_003  <br/> |
|**Disponibilità elevata** <br/> |Attivo/attivo tra 2 geo ridondanti  <br/> ExpressRoute circuiti - Chicago e Dallas  <br/> |
|**Controllo simmetria percorso** <br/> |**Metodo**: NAT di origine  <br/> **Percorso Internet**: connessioni a 192.168.5.5 in ingresso origine NAT  <br/> |**Percorso ExpressRoute**: connessioni NAT origine 192.168.1.0 (Chicago) e 192.168.2.0 (Dallas)  <br/> |

Di seguito è riportato un esempio di un servizio è solo in uscita:
|**Proprietà di connessione**|**Valore**|
|:-----|:-----|
|**Direzione del traffico di rete** <br/> |In uscita  <br/> |
|**Servizio** <br/> |SharePoint Online  <br/> |
|**Endpoint locale (origine)** <br/> |Workstation degli utenti  <br/> |
|**Pubblico endpoint di Office 365 (destinazione)** <br/> |SharePoint Online (indirizzi IP)  <br/> |
|**Voce (Internet) DNS pubblica** <br/> |\*. sharepoint.com (e altri nomi di dominio completo)  <br/> |
|**Riferimenti alle CDN** <br/> |CDN.sharepointonline.com (e altri nomi di dominio completi) - indirizzi IP gestiti dal provider CDN)  <br/> |
|**Annuncio pubblicitario IP e NAT in uso** <br/> |**Percorso di Internet/NAT di origine**: 1.1.1.0/24  <br/> **Percorso di ExpressRoute/NAT di origine**: 1.1.2.0/24 (Chicago) e 1.1.3.0/24 (Dallas)  <br/> |
|**Metodo di integrazione applicativa** <br/> |**Internet**: attraverso il proxy di livello 7 (file con estensione PAC)  <br/> **ExpressRoute**: diretto routing (Nessun proxy)  <br/> |
|**Controlli di sicurezza/perimetrale** <br/> |**Percorso Internet**: DeviceID_002  <br/> **Percorso ExpressRoute**: DeviceID_003  <br/> |
|**Disponibilità elevata** <br/> |**Percorso Internet**: uscita internet ridondanti  <br/> **Percorso ExpressRoute**: attivo/attivo 'hot la' routing tra 2 circuiti ExpressRoute geo ridondanti - Chicago e Dallas  <br/> |
|**Controllo simmetria percorso** <br/> |**Metodo**: NAT per tutte le connessioni di origine  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a>La progettazione della topologia di rete con connettività regionali
<a name="topology"> </a>

Dopo avere compreso i servizi e i flussi di traffico di rete associato, è possibile creare un diagramma di rete che include i nuovi requisiti di integrazione applicativa e vengono illustrate le modifiche apportate da utilizzare ExpressRoute per Office 365. Il diagramma deve includere:
  
1. In Office 365 e altri servizi si accederà da tutti i percorsi utente.

2. Tutto internet e punti di uscita ExpressRoute.

3. Tutti in ingresso e in uscita i dispositivi che gestiscono la connettività e la disconnessione da rete, inclusi i router, firewall, server proxy di applicazione e il rilevamento delle intrusioni/prevenzione.

4. Destinazioni interne per tutto il traffico in ingresso, ad esempio server ADFS interni accettare connessioni dai server proxy applicazione web ADFS.

5. Catalogo di tutte le subnet IP che verrà annunciato

6. Identificare ogni località in cui verranno accedere a Office 365 da ed elencare le riunioni persone-me posizioni che verranno utilizzate per ExpressRoute.

7. Percorsi e parti della topologia di rete interna, dove verranno accettati prefissi IP Microsoft maturati dal ExpressRoute, filtrati e propagazione.

8. La topologia di rete deve illustrano la posizione geografica di ogni segmento di rete e come si connette alla rete Microsoft su ExpressRoute e/o Internet.

Nel diagramma seguente viene illustrato ogni località in cui utenti verranno con Office 365 dall'insieme gli annunci di routing in ingresso e in uscita a Office 365.
  
![Meet geografica regionale ExpressRoute-me](media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
Per il traffico in uscita, le persone accedere a Office 365 in uno dei tre modi:
  
1. A una riunione-me posizione in Nord America per gli utenti in California.

2. A una riunione-me percorso Hong Kong per gli utenti di Hong Kong.

3. Tramite internet in Bangladesh dove sono disponibili un massimo di persone e non a commutazione di circuito ExpressRoute il provisioning.

![Connessioni in uscita per diagramma regionale](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
Analogamente, il traffico di rete in ingresso da Office 365 restituisce in uno dei tre modi:
  
1. A una riunione-me posizione in Nord America per gli utenti in California.

2. A una riunione-me percorso Hong Kong per gli utenti di Hong Kong.

3. Tramite internet in Bangladesh dove sono disponibili un massimo di persone e non a commutazione di circuito ExpressRoute il provisioning.

![Connessioni in ingresso per diagramma regionale](media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a>Determinare la riunione appropriato-me posizione

La selezione di riunione-me posizioni, ovvero la località dove il circuito ExpressRoute si connette alla rete a Microsoft network, è influenzato da percorsi di cui gli utenti accederanno Office 365 da. Come SaaS che offre, Office 365 non funziona in base al modello regionale IaaS o PaaS allo stesso modo Azure. In realtà, Office 365 è un insieme di servizi di collaborazione, distribuiti cui potrebbe essere necessario agli utenti di connettersi agli endpoint in più centri dati e le aree, potrebbero non essere necessariamente nella stessa posizione o area di cui è ospitato tenant dell'utente.
  
Ciò significa molto importante è necessario prendere quando si seleziona meet-me percorsi per ExpressRoute per Office 365 è dove si connetteranno le persone all'interno dell'organizzazione da. Suggerimenti generali per la connettività di Office 365 ottimale è implementare il routing, in modo che le richieste degli utenti ai servizi di Office 365 sono trasferite in Microsoft network tramite il percorso più breve di rete, questo viene inoltre spesso viene denominato 'hot la' routing. Ad esempio, se la maggior parte degli utenti di Office 365 in uno o due posizioni, selezionando meet-me percorsi presenti vicino al percorso di tali utenti creata la progettazione ottimale. Se la società dispone di gruppi di utenti numerosi in numerose aree geografiche diverse, è possibile disporre di più circuiti ExpressRoute e soddisfare-me percorsi. Per alcuni percorsi utente, il percorso più breve/ottimale in Office 365 e Microsoft network potrebbero non essere attraverso l'interno meet WAN ed ExpressRoute-me coordinate, ma tramite Internet.
  
Spesso esistono più meet-me alle ubicazioni selezionati all'interno di un'area con prossimità relativa agli utenti. Compilare la tabella seguente per informazioni utili per le decisioni.

|**Riunioni pianificate ExpressRoute-me posizioni in California e New York**||
|:-----|:-----|
|Percorso  <br/> |Numero di persone  <br/> |Previsto latenza di rete di Microsoft in uscita Internet  <br/> |Prevista latenza di rete di Microsoft su ExpressRoute  <br/> |
|Roma  <br/> |10,000  <br/> |~ 15 ms  <br/> |~ 10 ms (tramite valle silicio)  <br/> |
|Controller di dominio di Washington  <br/> |15.000  <br/> |~ 20 ms  <br/> |~ 10 ms (tramite New York)  <br/> |
|Dallas  <br/> |5,000  <br/> |~ 15 ms  <br/> |~ 40ms (tramite New York)  <br/> |

Dopo che l'architettura di rete globale che mostra l'area di Office 365, provider di servizi di rete ExpressRoute soddisfare-me percorsi e la quantità di utenti in base al percorso è stata sviluppata, è possibile utilizzare per identificare se è possibile effettuare le ottimizzazioni. Potrebbe essere inoltre visualizzato "hairpin" globale connessioni di rete in cui il traffico indirizza in un percorso distante per ottenere la riunione-me posizione. Se viene rilevato un "hairpin" sulla rete globale che deve essere risolte prima di continuare. Uno trovare un'altra meet-me percorso o utilizzare selettivi punti di uscita Internet private per evitare il "hairpin".
  
Il primo diagramma mostra un esempio di un cliente con due posizioni fisiche in Nord America. È possibile visualizzare le informazioni sui percorsi di office, le posizioni tenant Office 365, e soddisfano diverse opzioni per ExpressRoute-me percorsi. In questo esempio, il cliente è selezionato il meet-me posizione basato su due principi, nell'ordine indicato:
  
1. Vicino alle persone all'interno dell'organizzazione.

2. Più vicino in prossimità di un Data Center Microsoft a cui è ospitato Office 365.

![Meet geografica ExpressRoute US-me](media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
L'espansione di questo concetto leggermente ulteriormente, mostrato nella figura secondo un cliente multinazionale esempio affrontare processi decisionali e informazioni simili. Il cliente ha un piccolo ufficio in Bangladesh con un piccolo team di dieci persone dedicata a diventando loro footprint nell'area. Esiste una riunione-me posizione in un Data Center Microsoft a Office 365 e Chennai ospitate in Chennai così una riunione-me percorso potrebbe essere preferibile; Tuttavia, per dieci persone, i costi legati a commutazione di circuito aggiuntive sono difficile. Durante l'analisi della rete, è necessario determinare se la latenza per l'invio del traffico di rete tra la rete è più efficace spese di investimento per l'acquisizione di un'altra a commutazione di circuito ExpressRoute.
  
In alternativa, dieci persone appartenenti Bangladesh delle prestazioni migliori con il traffico di rete inviato via internet alla rete Microsoft che verrebbero il routing all'interno della rete interna è emerso nei diagrammi introduttivi e riprodotta di seguito.
  
![Connessioni in uscita per diagramma regionale](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a>Creare il ExpressRoute per il piano di implementazione di Office 365
<a name="implementation"> </a>

Il piano di implementazione dovrebbe includere entrambi i dettagli tecnici delle configurazione ExpressRoute, nonché i dettagli di configurazione di tutte le altre infrastruttura della rete, ad esempio.
  
- Pianificare servizi suddivisi tra ExpressRoute e Internet.

- Pianificare la larghezza di banda, sicurezza, la disponibilità elevata e failover.

- Progettare in ingresso e in uscita routing, inclusi corretto routing ottimizzazioni del percorso per località diverse

- Decidere quanto ExpressRoute route verranno annunciate alla rete e qual è il meccanismo per i client selezionare percorso Internet o ExpressRoute; ad esempio diretto proxy routing o dell'applicazione.

- Pianificare modifiche a record DNS, incluse le voci [Sender Policy Framework](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx) .

- Pianificare la strategia NAT inclusa in ingresso e in uscita origine NAT.

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a>Pianificare la distribuzione con internet e percorsi di rete ExpressRoute
<a name="paths"> </a>

- Per la distribuzione iniziale, tutti i servizi in ingresso, ad esempio posta elettronica in ingresso o la connettività ibrida, si consiglia di utilizzare internet.

- Pianificare l'utente finale client LAN routing, ad esempio [la configurazione di un file PAC/WPAD](https://aka.ms/manageo365endpoints), route predefinita, i server proxy e annunci route BGP.

- Pianificare la distribuzione perimetrale, inclusi i server proxy, firewall e i proxy cloud.

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a>Pianificare la larghezza di banda, sicurezza, la disponibilità elevata e failover
<a name="availability"> </a>

Creare un piano per la larghezza di banda necessaria per ogni carico di lavoro principale di Office 365. Stimare separatamente Exchange Online, SharePoint Online e Skype per i requisiti di larghezza di banda Business Online. È possibile utilizzare calcolatori stima fornita in Exchange Online e Skype per le aziende come punto di partenza; un test pilota con un rappresentante alcuni dei profili utente e le posizioni, tuttavia, è necessario valutare le esigenze di larghezza di banda dell'organizzazione.
  
Aggiungere la modalità di gestione della protezione in ogni internet ed ExpressRoute della posizione in uscita per il piano, ricordarsi di tutte le connessioni ExpressRoute a Office 365 utilizzano peering pubblici e devono essere protette ancora in base alle politiche aziendali protezione della connessione a esterno reti.
  
Aggiungere i dettagli per il piano sui utenti interessati dal tipo di interruzione dei servizi e come tali utenti saranno in grado di eseguire le operazioni a piena capacità nel modo più semplice.
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a>Pianificare i requisiti di larghezza di banda tra Skype per i requisiti aziendali di instabilità, la latenza, congestione e capacità aggiuntiva
  
Skype per Business Online dispone inoltre di requisiti di rete aggiuntive specifiche che sono descritte in dettaglio nell'articolo [della qualità multimediale e le prestazioni di connettività di rete in Skype Business online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).
  
Leggere la sezione **pianificazione della larghezza di banda per Azure ExpressRoute** nella [pianificazione della rete con ExpressRoute per Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
Quando si esegue una valutazione della larghezza di banda con gli utenti pilota, è possibile utilizzare la Guida. [Ottimizzazione delle prestazioni di office 365 utilizzando le linee di base e la cronologia delle prestazioni](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).
  
#### <a name="plan-for-high-availability-requirements"></a>Pianificare i requisiti di disponibilità elevata
  
Creare un piano per la disponibilità elevata soddisfare le esigenze e incorporare questo diagramma di topologia di rete aggiornato. Leggere la sezione **la disponibilità elevata e failover con Azure ExpressRoute** , [pianificazione della rete con ExpressRoute per Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
#### <a name="plan-for-network-security-requirements"></a>Pianificare i requisiti di protezione di rete
  
Creare un piano per soddisfare i requisiti di protezione di rete e incorporare questo diagramma di topologia di rete aggiornato. Leggere la sezione **controlli di sicurezza applicazione a ExpressRoute Azure per Office 365 scenari** di [pianificazione della rete con ExpressRoute per Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
### <a name="design-outbound-service-connectivity"></a>Progettare la connettività al servizio in uscita
<a name="outbound"> </a>

*In uscita* i requisiti di rete che possono essere familiarità è ExpressRoute per Office 365. In particolare, gli indirizzi IP che rappresentano gli utenti e reti a Office 365 e agiscono come gli endpoint di origine per le connessioni in uscita a Microsoft devono seguire requisiti specifici indicati di seguito.
  
1. L'endpoint deve essere indirizzi IP pubblici, che vengono registrati per l'azienda o per portante fornire connettività ExpressRoute all'utente.

2. L'endpoint deve essere richiesti a Microsoft e convalidate accettata da ExpressRoute.

3. L'endpoint deve non verrà annunciato a Internet con la metrica di routing uguale o maggiore preferita.

4. I punti finali non devono essere utilizzati per la connettività ai servizi Microsoft che non sono configurate su ExpressRoute.

Se la progettazione di rete non soddisfa questi requisiti, non esiste un rischio elevato che gli utenti osserveranno gli errori di connettività a Office 365 e altri servizi Microsoft a causa di route nero holing o routing asimmetrica. Si verifica quando le richieste ai servizi Microsoft vengono instradate tramite ExpressRoute, ma le risposte vengono instradate via internet e viceversa e le risposte vengono rilasciate dai dispositivi di rete informazioni sullo stato, ad esempio i firewall.
  
Il metodo più comune che è possibile utilizzare per soddisfare i requisiti indicati consiste nell'utilizzare NAT implementato come parte della rete o disponibili per il gestore ExpressRoute di origine. Origine NAT consente di estrarre i dettagli e private gli indirizzi IP della rete internet da ExpressRoute e; Oltre a annunci di route IP corretto, offrono un semplice meccanismo per garantire la simmetria percorso. Se si utilizzano dispositivi di rete informazioni sullo stato specifiche per i percorsi peering ExpressRoute, è necessario implementare pool NAT separato per ogni ExpressRoute peering per garantire la simmetria percorso.
  
Per ulteriori informazioni sui [requisiti NAT ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-nat/).
  
Aggiungere le modifiche per la connettività in uscita al diagramma di topologia di rete.
  
### <a name="design-inbound-service-connectivity"></a>Progettare la connettività al servizio in ingresso
<a name="inbound"> </a>

La maggior parte delle distribuzioni di Office 365 enterprise si presuppone una forma di connettività in ingresso da Office 365 a servizi locali, ad esempio per Exchange, SharePoint e Skype per gli scenari ibridi Business, migrazioni delle cassette postali e l'autenticazione tramite ADFS infrastruttura. Quando si ExpressRoute si attiva un percorso di routing aggiuntivo per la connettività in uscita tra la rete locale e Microsoft, le connessioni in ingresso inavvertitamente possono essere influenzate dal routing asimmetrica, anche se si prevede di disporre i flussi di continuano a tramite Internet. Alcune precauzioni descritte di seguito si consiglia di verificare che non vi è alcun impatto a Internet basato su flussi in ingresso da Office 365 per sistemi locali.
  
Per ridurre al minimo i rischi di routing asimmetrica per i flussi di traffico di rete in ingresso, tutte le connessioni in ingresso deve utilizzare NAT di origine prima che si è distribuiti in segmenti di rete con routing della visibilità ExpressRoute. Se le connessioni in ingresso sono consentite in un segmento di rete con routing della visibilità ExpressRoute senza NAT di origine, le richieste provenienti da Office 365 verranno immesso da internet, ma la risposta tornando a Office 365 verrà preferisce il ExpressRoute percorso di rete al Microsoft network, causando routing asimmetrica.
  
Provare a uno dei seguenti formati di implementazione per soddisfare questo requisito:
  
1. Eseguire NAT di origine prima che le richieste vengono indirizzate verso la rete interna utilizzando le apparecchiature di rete, ad esempio firewall o carico bilanciamento del carico sul percorso da Internet ai sistemi locali.

2. Verificare che le route ExpressRoute non verranno propagate per i segmenti di rete in servizi in ingresso, ad esempio front end server o invertire i sistemi proxy, che si trovano le connessioni Internet.

In modo esplicito contabili per questi scenari nella rete e mantenere tutto il traffico di rete in ingresso passa su consente Internet per ridurre al minimo i rischi operativi di routing asimmetrica e distribuzione.
  
È possibile casi dove è possibile indirizzare alcuni flussi in ingresso su connessioni ExpressRoute. Per questi scenari, eseguire le seguenti considerazioni aggiuntive all'account.
  
1. Office 365 può solo gli endpoint locale di destinazione che utilizzano IP pubblico. Ciò significa che anche se locale endpoint in ingresso viene esposta solo a Office 365 su ExpressRoute, comunque deve disporre di IP pubblico associato.

2. Risoluzione dei nomi DNS tutti che servizi di Office 365 eseguono per risolvere gli endpoint locale avvenire utilizza DNS pubblico. Ciò significa che è necessario registrare FQDN gli endpoint del servizio in ingresso di mapping IP su Internet.

3. Per ricevere connessioni di rete in ingresso su ExpressRoute, è necessario che le subnet IP pubbliche per gli endpoint annunciato alla Microsoft su ExpressRoute.

4. Valutare attentamente questi flussi di traffico di rete in ingresso per garantire la protezione appropriata e controlli di rete vengono applicati a tali in conformità con le società criteri di protezione e rete.

5. Una volta locale in ingresso endpoint né annunciato a Microsoft tramite ExpressRoute, ExpressRoute in modo efficace diventerà il percorso di routing preferito per gli endpoint di tutti i servizi di Microsoft, tra cui Office 365. Ciò significa che le subnet endpoint deve essere utilizzata solo per le comunicazioni con servizi di Office 365 e nessun altro servizio Microsoft Network. In caso contrario, la progettazione consentono di routing asimmetrica in connessioni in ingresso da altri Microsoft services preferisce per il routing in ingresso su ExpressRoute, mentre il percorso di ritorno utilizzerà Internet.

6. Nell'evento un ExpressRoute circuito o soddisfare-me posizione non è attiva, è necessario verificare locale endpoint in ingresso sono ancora disponibili per accettare richieste su un percorso di rete distinta. Ciò significa subnet pubblicità per tali endpoint tramite più circuiti ExpressRoute.

7. È consigliabile l'applicazione di origine NAT per tutti i flussi di traffico di rete in ingresso l'accesso alla rete tramite ExpressRoute, soprattutto quando questi flussi tra dispositivi di rete informazioni sullo stato, ad esempio i firewall.

8. Alcuni servizi locali, ad esempio individuazione automatica di Exchange o proxy ADFS possono ricevere le richieste in ingresso da servizi di Office 365 sia gli utenti da Internet. Per le richieste di Office 365 sarà destinato lo stesso FQDN le richieste degli utenti tramite Internet. Che consente di connessioni utente in ingresso da internet a tali endpoint locale, mentre forzato connessioni di Office 365 utilizzino ExpressRoute, rappresenta complessità routing significativa. Per la maggior parte dei clienti non è consigliato l'implementazione di questi scenari complessi su ExpressRoute a causa di considerazioni operative. Il sovraccarico aggiuntivo include, la gestione dei rischi di routing asimmetrica e verrà richiesto di gestire con attenzione routing annunci pubblicitari e i criteri tra più dimensioni.

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a>Aggiornare il piano di topologia di rete per mostrare come è necessario evitare asimmetriche route
<a name="asymmetric"> </a>

Si desidera evitare di routing asimmetrica affinché gli utenti dell'organizzazione possono facilmente utilizzare Office 365, nonché altri importanti servizi su internet. Esistono due configurazioni i clienti possono causare routing asimmetrica. Questo punto, è buona per verificare la configurazione di rete si prevede di utilizzare e controllare se uno di questi scenari di distribuzione asimmetrici esista.
  
Per iniziare, verranno approfondite alcune situazioni diverse associate nel seguente diagramma di rete. In questo diagramma, tutti i server che riceve le richieste in ingresso, ad esempio ibrida ADFS o locale server nel centro dati di New Jersey e annunciato a internet.
  
1. Mentre la rete perimetrale è protetta, non esiste alcun NAT origine disponibili per le richieste in arrivo.

2. I server del centro dati New Jersey sono in grado di vedere internet e ExpressRoute route.

![Panoramica del servizio di integrazione applicativa ExpressRoute](media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
È inoltre disponibile suggerimenti su come risolverli.
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a>Problema 1: Cloud alla connessione locale tramite Internet
  
Nel diagramma seguente illustra il percorso di rete asimmetrica al momento della configurazione di rete non propone NAT per le richieste in ingresso dal cloud Microsoft tramite internet.
  
1. Le richieste in ingresso da Office 365 consente di recuperare l'indirizzo IP dell'endpoint locale dal DNS pubblico e invia la richiesta alla rete perimetrale.

2. In questa configurazione presenta il problema, non esiste alcun NAT origine configurato o disponibile nella rete perimetrale in cui è il traffico inviato causando l'indirizzo IP di origine effettivo di indirizzi utilizzata come destinazione restituita.

  - Il server nella rete instrada il traffico di ritorno a Office 365 tramite qualsiasi connessione di rete ExpressRoute disponibili.

  - Il risultato è un percorso asimmetrico per quel flusso a Office 365, risultando in una connessione interrotta.

![Problema di routing ExpressRoute Asymetric 1](media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a>Soluzione 1a: NAT di origine
  
Semplicemente aggiungendo un'origine di NAT per le richieste in ingresso risolve questa rete non correttamente configurata. In questo diagramma:
  
1. Le richieste in arrivo continuano a immettere tramite rete perimetrale del data center New Jersey. Questa volta NAT di origine è disponibile.

2. Risposta da route server nuovamente verso l'indirizzo IP associato NAT origine anziché l'indirizzo IP originale, causando la risposta restituzione sullo stesso percorso di rete.

![Soluzione di routing ExpressRoute Asymetric 1](media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a>Soluzione 1b: Route di ambito
  
In alternativa, è possibile scegliere di non consentire BGP ExpressRoute prefissi da annunciare, rimuovere il percorso di rete alternativo per i computer. In questo diagramma:
  
1. Le richieste in arrivo continuano a immettere tramite rete perimetrale del data center New Jersey. Attualmente non sono disponibili nel centro dati New Jersey i prefissi annunciati Microsoft nel circuito ExpressRoute.

2. Risposta da route server nuovamente verso l'indirizzo IP associato all'indirizzo IP originale tramite l'unica route disponibile, causando la risposta restituzione sullo stesso percorso di rete.

![Soluzione di routing ExpressRoute Asymetric 2](media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a>Problema 2: Cloud alla connessione locale su ExpressRoute
  
Nel diagramma seguente illustra il percorso di rete asimmetrica al momento della configurazione di rete non propone NAT per le richieste in ingresso dal cloud Microsoft su ExpressRoute.
  
1. Le richieste in ingresso da Office 365 consente di recuperare l'indirizzo IP da DNS e invia la richiesta alla rete perimetrale.

2. In questa configurazione presenta il problema, non esiste alcun NAT origine configurato o disponibile nella rete perimetrale in cui è il traffico inviato causando l'indirizzo IP di origine effettivo di indirizzi utilizzata come destinazione restituita.

  - I computer della rete indirizza il traffico di ritorno a Office 365 tramite qualsiasi connessione di rete ExpressRoute disponibili.

  - Il risultato è una connessione a Office 365 asimmetrica.

![Problema di routing ExpressRoute Asymetric 2](media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a>Soluzione 2: Origine NAT
  
Semplicemente aggiungendo un'origine di NAT per le richieste in ingresso risolve questa rete non correttamente configurata. In questo diagramma:
  
1. Le richieste in arrivo continuano a immettere tramite rete perimetrale del data center New York. Questa volta NAT di origine è disponibile.

2. Risposta da route server nuovamente verso l'indirizzo IP associato NAT origine anziché l'indirizzo IP originale, causando la risposta restituzione sullo stesso percorso di rete.

![Soluzione di routing ExpressRoute Asymetric 3](media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a>Carta verificare che la struttura della rete disponga simmetria percorso

A questo punto, è necessario verificare nel documento che il piano di implementazione offre simmetria route per i diversi scenari in cui verrà con Office 365. È possibile identificare la route di rete specifico che si prevede che da eseguire quando una persona utilizza diverse caratteristiche del servizio. Dalla rete locale e il routing WAN, nei dispositivi perimetrale, al percorso di connettività; ExpressRoute o internet e alla connessione all'endpoint in linea.
  
È necessario eseguire questa operazione per tutti i servizi di rete di Office 365 che sono stati identificati in precedenza come servizi che verrà adottate nell'organizzazione.
  
È possibile per effettuare questo paper indicazioni di route con un secondo utente. Viene spiegato al loro posto ogni hop di rete per ottenere il successivo route dalla e verificare che si ha familiarità con i percorsi di routing. Tenere presente che ExpressRoute sempre fornirà una route più con ambita a indirizzi IP dei server Microsoft assegnandogli costi inferiori route che una route predefinita di Internet.
  
### <a name="design-client-connectivity-configuration"></a>Configurazione di connettività Client di progettazione
<a name="asymmetric"> </a>

![Utilizzo dei file PAC con ExpressRoute](media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
Se si utilizza un server proxy per internet associato traffico quindi è necessario modificare qualsiasi PAC o i file di configurazione client per verificare che il computer client nella rete siano configurati correttamente per l'invio del traffico ExpressRoute che costantemente a Office 365 senza in transito il server proxy e del traffico, inclusi alcuni traffico di Office 365, viene inviata al proxy pertinenti. Leggere la Guida sulla [gestione di endpoint di Office 365](https://aka.ms/manageo365endpoints) , ad esempio file PAC.
  
> [!NOTE]
> I punti finali modificare spesso, con una frequenza massima settimanale. È solo necessario apportare modifiche in base ai servizi e funzionalità che dell'organizzazione ha adottato per ridurre il numero di modifiche è necessario effettuare essere sempre aggiornati. Prestare attenzione close alla **Data di validità** del feed RSS in cui vengono inserite le modifiche e viene generato un record di tutte le precedenti modifiche, IP indirizzi che sono annunciati potrebbe non annunciato, o rimosso da annuncio, fino a raggiunta la data di validità.
  
## <a name="build-your-deployment-and-testing-procedures"></a>Creare la distribuzione e le procedure di testing
<a name="testing"> </a>

Il piano di implementazione deve includere sia test e rollback di pianificazione. Se l'implementazione non funziona come previsto, il piano progettato effetto il minor numero di utenti prima vengono rilevati problemi. Di seguito sono alcuni principi di alto livelli che deve prendere in considerazione il piano.
  
1. Fase il onboarding di servizio utente e segmento di rete per ridurre a icona interruzione del servizio.

2. Pianificazione del test della route con traceroute e TCP connettersi da un host connessi a internet separato.

3. Preferibilmente, test dei servizi in ingresso e in uscita deve essere eseguito su una rete di testing isolato con un tenant di prova Office 365.

      - In alternativa, il test può essere eseguito in una rete di produzione se ancora non utilizza Office 365 cliente o nel progetto pilota.

      - In alternativa, il test può essere eseguite durante un'interruzione di produzione che è riservata per test e monitoraggio solo.

      - In alternativa, il test può essere eseguito controllando le route per ogni servizio in ogni nodo del router livello 3. Questo autunno back deve essere utilizzato solo nessun altro test è possibile poiché mancanza di testing fisico presenta rischi.

### <a name="build-your-deployment-procedures"></a>Creare le procedure di distribuzione

Le procedure di distribuzione necessario distribuire per piccoli gruppi di utenti in più fasi per consentire di test prima di distribuire a più gruppi di utenti. Di seguito sono diversi modi per eseguire la distribuzione di ExpressRoute.
  
1. Impostare ExpressRoute con Microsoft peering e sono in fasi annunci route inoltrati a un singolo host solo per scopi di test.

2. Advertise route alla rete ExpressRoute per un singolo segmento di rete inizialmente ed espandere annunci route da segmento di rete o l'area geografica.

3. Se la distribuzione di Office 365 per la prima volta, utilizzare la distribuzione di rete ExpressRoute come un progetto pilota per un numero limitato di utenti.

4. Se si utilizza il server proxy, in alternativa è possibile configurare un file PAC test per indicare un numero limitato di utenti a ExpressRoute con test e suggerimenti prima di aggiungere ulteriori.

Il piano di implementazione deve includere ognuna delle procedure di distribuzione che devono essere prese o comandi che devono essere utilizzati per distribuire la configurazione di rete. Quando si riceve l'ora di interruzione del funzionamento della rete tutte le modifiche apportate devono essere dal peer e piano di distribuzione scritta di cui è stato scritto in anticipo revisione. Vedere la Guida alla configurazione di documentazione tecnica di ExpressRoute.
  
- Aggiornare i record SPF TXT se sono stati modificati gli indirizzi IP per tutti i server locali che continueranno a inviare la posta elettronica.

- Aggiornare le voci DNS per i server locale se sono stati modificati gli indirizzi IP per l'utilizzo di una nuova configurazione di NAT.

- Verificare che è stato sottoscritto il feed RSS per le notifiche di endpoint di Office 365 gestire tutte le configurazioni di routing o il proxy.

Dopo aver completata la distribuzione ExpressRoute devono essere eseguite le procedure descritte nel piano di test. I risultati per ogni procedura devono essere registrati. È necessario includere le procedure per eseguire il rollback all'ambiente di produzione originale nel caso in cui i risultati del test plan indicano che l'implementazione ha avuto esito negativo.
  
### <a name="build-your-test-procedures"></a>Creare le procedure di test

Le procedure di testing devono includere i test per ogni servizio di rete in ingresso e in uscita per Office 365 entrambi che verrà utilizzata ExpressRoute e quelle in cui non lo eseguiranno. Devono includere le procedure di test da ogni percorso di rete univoco inclusi gli utenti che non sono in locale nella rete LAN aziendale.
  
Riportati di seguito alcuni esempi delle attività di test.
  
1. Eseguire il ping dal router locale al router operatore di rete.

2. Convalidare i 500 + Office 365 e CRM Online l'indirizzo IP gli annunci vengono ricevuti dal router locale.

3. Convalidare l'entrata e in uscita NAT funziona tra ExpressRoute e la rete interna.

4. Verificare che le route per il dispositivo NAT sono viene annunciate dal router.

5. Verificare che ExpressRoute ha accettato i prefissi richiesti.

      - Utilizzare il cmdlet seguente per verificare gli annunci peering:

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. Convalidare l'IP pubblico NAT intervallo non è stato annunciato attraverso tutti gli altri ExpressRoute o pubblica a commutazione di circuito rete Internet di Microsoft a meno che non è un sottoinsieme specifico di un intervallo di dimensioni maggiore come nell'esempio precedente.

7. Sono abbinati circuiti ExpressRoute, verificare che le sessioni BGP siano in esecuzione.

8. Impostare un singolo host all'interno delle NAT e utilizzare il comando ping, tracert e tcpping per testare la connettività tra il nuovo circuito a outlook.office365.com host. In alternativa, è possibile utilizzare uno strumento quale Wireshark o Microsoft Network Monitor 3.4 su una porta con mirroring per MSEE per convalidare l'utente è in grado di connettersi all'indirizzo IP associato outlook.office365.com.

9. Verificare la funzionalità di livello di applicazione per Exchange Online.

  - Test Outlook è in grado di connettersi a Exchange Online e di invio/ricezione della posta elettronica.

  - Test Outlook è in grado di utilizzare la modalità online.

  - Test delle funzionalità di integrazione applicativa e di invio/ricezione smartphone.

10. Testare la funzionalità di livello di applicazione per SharePoint Online

  - Test OneDrive for Business client di sincronizzazione.

  - Verificare l'accesso web SharePoint Online.

11. Il test funzionalità a livello dell'applicazione per Skype per gli scenari di chiamata Business:

  - Partecipare alla conferenza telefonica come utente autenticato [invita avviato dall'utente finale].

  - Invitare utente alla conferenza telefonica [invito inviato da MCU].

  - Partecipare a conferenze come utente anonimo utilizzando i Skype per applicazione web di Business.

  - Partecipare alle chiamate dalla connessione cablata PC, telefono IP e dispositivi mobili.

  - Chiamata a utenti federati o chiamata PSTN convalida: completamento della chiamata, la qualità delle chiamate è accettabile, la durata della connessione è accettabile.

  - Verificare lo stato presenza dei contatti è stato aggiornato per entrambi i membri del tenant e gli utenti federati.

### <a name="common-problems"></a>Problemi comuni

Distribuzione asimmetrica è più comuni problemi di implementazione. Ecco alcune origini comuni da considerare:
  
- Utilizzo di una topologia di routing di rete aperti o flat senza NAT sul posto di origine.

- Non si utilizza SNAT per eseguire il routing in ingresso a internet ed ExpressRoute le connessioni di servizi.

- Non testare servizi in ingresso nel ExpressRoute in una rete di testing prima della distribuzione in generale.

## <a name="deploying-expressroute-connectivity-through-your-network"></a>Distribuzione di connettività ExpressRoute tramite la rete
<a name="testing"> </a>

Fase della distribuzione di un segmento di rete per volta, distribuzione progressivamente la connettività a diverse parti della rete con un piano per eseguire il rollback per ogni nuovo segmento di rete. Se la distribuzione è allineata con una distribuzione di Office 365, la prima distribuzione per gli utenti pilota di Office 365 ed estendere da quest'ultimo.
  
Funzionalità per il test e quindi per la produzione:
  
- Eseguire la procedura di distribuzione per consentire ExpressRoute.

- Testare le visualizzando che le route di rete sono quelli previsti.

- Eseguire test di ogni servizio in ingresso e in uscita.

- Rollback se eventuali problemi rilevati.

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a>Configurare una connessione di prova a ExpressRoute con un segmento di rete di testing

Dopo aver creato il piano completato su carta è necessario testare su piccola scala. In questo test è verrà stabilire una connessione ExpressRoute singola con Microsoft Peering a una subnet di test nella rete locale. È possibile configurare una [prova Office 365 tenant](https://go.microsoft.com/fwlink/p/?LinkID=403802) con connettività da e verso la subnet di test e includere tutti i servizi in ingresso e in uscita che verrà utilizzata nell'ambiente di produzione di subnet di test. Configurare il DNS per il segmento di rete di testing e definire tutti i servizi in ingresso e in uscita. Eseguire il piano di test e verificare che abbia familiarità con il routing per ogni servizio e la propagazione di route.
  
### <a name="execute-the-deployment-and-test-plans"></a>Esecuzione di piani di distribuzione e test

Dopo avere completato gli elementi descritti in precedenza, spuntare le aree una volta completata e verificare che si e aver esaminato il team di loro prima di eseguire la distribuzione e piani di test.
  
- Elenco dei servizi in ingresso e in uscita che partecipano alla modifica di rete.

- Diagramma dell'architettura di rete globale che mostra uscita internet sia meet ExpressRoute-me percorsi.

- Routing diagramma che illustra i diversi percorsi di rete utilizzati per ogni servizio distribuito.

- Un piano di distribuzione con i passaggi per implementare le modifiche e rollback, se necessario.

- Un piano di test per ogni servizio Office 365 e la rete di testing.

- Completare la convalida di carta di route di produzione per i servizi in ingresso e in uscita.

- Test completato tra un segmento di rete di testing inclusi il test della disponibilità.

Scegliere una finestra di interruzione dei servizi che è sufficiente eseguire tramite il piano di distribuzione intera e il piano di test, ha alcune ora disponibile per la risoluzione dei problemi e per distribuzione nuovamente se necessario.
  
> [!CAUTION]
> A causa della natura complessa di routing via internet ed ExpressRoute, è consigliabile che ora buffer aggiuntive viene aggiunto a questa finestra di gestione di risoluzione dei problemi di routing complesso.
  
### <a name="configure-qos-for-skype-for-business-online"></a>Configurare QoS per Skype Online per le aziende

QoS è necessario ottenere vantaggi audio e riunione Skype Business online. Dopo aver verificato che la connessione di rete ExpressRoute non si blocchi qualsiasi altro accesso di servizio di Office 365, è possibile configurare QoS. Configurazione di QoS è descritto nell'articolo [ExpressRoute e QoS in Skype Business online](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) .
  
## <a name="troubleshooting-your-implementation"></a>Risoluzione dei problemi dell'implementazione
<a name="troubleshooting"> </a>

Individuare il primo posto si trova la procedura descritta in questa Guida di implementazione, eventuali perse nel piano di implementazione? Tornare indietro ed eseguire un'ulteriore verifica se possibile replicare l'errore e di eseguire il debug reti di piccole dimensioni.
  
Identificare i cui, in ingresso e in uscita, i servizi non durante il test. Acquisire in particolare gli indirizzi IP e subnet per ognuno dei servizi che non è riuscita. Proseguire e scorrere il diagramma di topologia di rete su carta e convalidare il routing. Convalidare in modo specifico dove il routing ExpressRoute annuncia per, verificare che il routing durante l'interruzione se possibile con le tracce.
  
Eseguire PSPing con una traccia di rete per ogni endpoint cliente e valutare gli indirizzi IP di origine e di destinazione per verificare che siano come previsto. Eseguire telnet a qualsiasi host posta esporre sulla porta 25 e verificare che SNAT è nascondere l'indirizzo IP di origine originale se è previsto.
  
Tenere presente che durante la distribuzione di Office 365 con una connessione ExpressRoute che è necessario verificare che sia la configurazione di rete per ExpressRoute è progettato in modo ottimale ed è stato ottimizzato anche gli altri componenti nella rete, ad esempio i computer client. Oltre a utilizzare questa Guida alla pianificazione per la risoluzione dei passaggi che non ricevuti, è stato scritto anche un [piano per Office 365 risoluzione dei problemi di prestazioni](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) .
  
Questo è un collegamento breve che è possibile utilizzare il ritorno:[https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)
  
## <a name="related-topics"></a>Argomenti correlati

[Connettività di rete con Office 365](network-connectivity.md)
  
[Azure ExpressRoute per Office 365](azure-expressroute.md)
  
[Gestione di ExpressRoute per la connettività di Office 365](managing-expressroute-for-connectivity.md)
  
[Routing con ExpressRoute per Office 365](routing-with-expressroute.md)
  
[Pianificazione della rete con ExpressRoute per Office 365](network-planning-with-expressroute.md)
  
[Utilizzo della caratteristica community BGP in ExpressRoute per gli scenari di Office 365 (preview)](bgp-communities-in-expressroute.md)
  
[Qualità multimediale e le prestazioni di connettività di rete in Skype for Business in linea](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Ottimizzazione della rete per Skype Business online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute e QoS in Skype for Business in linea](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Flusso di chiamate tramite ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Ottimizzazione delle prestazioni di Office 365 mediante l'uso della cronologia delle prestazioni e delle previsioni](performance-tuning-using-baselines-and-history.md)
  
[Piano di risoluzione dei problemi di prestazioni per Office 365](performance-troubleshooting-plan.md)
  
[URL e intervalli di indirizzi IP per Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Ottimizzazione delle prestazioni e rete di Office 365](network-planning-and-performance.md)
