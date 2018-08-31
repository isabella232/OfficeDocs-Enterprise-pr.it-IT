---
title: Pianificazione della rete con ExpressRoute per Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
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
ms.assetid: 103208f1-e788-4601-aa45-504f896511cd
description: ExpressRoute per Office 365 fornisce la connettività di livello 3 tra la rete e Data Center di Microsoft. Parte del circuito utilizzare annunci route Border Gateway Protocol (BGP) del server front-end di Office 365. Dal punto di vista dei dispositivi in locale, quando è necessario selezionare il percorso corretto TCP/IP per Office 365, ExpressRoute Azure è visualizzato come alternativa a Internet.
ms.openlocfilehash: 79cad16a619f048d1ba98b6058127f901211344d
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541366"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Pianificazione della rete con ExpressRoute per Office 365

ExpressRoute per Office 365 fornisce la connettività di livello 3 tra la rete e Data Center di Microsoft. Parte del circuito utilizzare annunci route Border Gateway Protocol (BGP) del server front-end di Office 365. Dal punto di vista dei dispositivi in locale, quando è necessario selezionare il percorso corretto TCP/IP per Office 365, ExpressRoute Azure è visualizzato come alternativa a Internet.
  
Azure ExpressRoute aggiunge un percorso direttamente a un set specifico di funzionalità supportate e i servizi offerti dal server di Office 365 all'interno di Data Center di Microsoft. ExpressRoute Azure non sostituisce la connettività Internet Data Center Microsoft o di base servizi Internet, ad esempio la risoluzione dei nomi di dominio. ExpressRoute Azure e le circuiti Internet devono essere protetti e ridondanti.
  
Nella tabella seguente vengono evidenziate alcune differenze tra le connessioni di Azure ExpressRoute nel contesto di Office 365 e internet.

|**Differenze nella pianificazione della rete**|**Connessione a Internet**|**Connessione di rete ExpressRoute**|
|:-----|:-----|:-----|
| Accesso ai servizi internet necessari, incluse;  <br/>  Risoluzione dei nomi DNS  <br/>  Verifica della revoca dei certificati  <br/>  Reti per la distribuzione di contenuti  <br/> |Sì  <br/> |Le richieste a Microsoft di proprietà dell'infrastruttura DNS e/o CDN può utilizzare la rete ExpressRoute.  <br/> |
| Accesso ai servizi di Office 365, inclusi;  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype for Business Online  <br/>  Office Online  <br/>  L'autenticazione e portale di office 365  <br/> |Sì, tutte le applicazioni e caratteristiche  <br/> |Sì, [applicazioni e funzionalità specifiche](https://aka.ms/o365endpoints) <br/> |
|Sicurezza nel perimetro in locale.  <br/> |Sì  <br/> |Sì  <br/> |
|Pianificazione della disponibilità elevata.  <br/> |Failover su una connessione di rete internet alternativo  <br/> |Failover su una connessione ExpressRoute alternativo  <br/> |
|Connessione diretta con un profilo di rete prevedibile.  <br/> |No  <br/> |Sì  <br/> |
|Connettività IPv6.  <br/> |Sì  <br/> |Sì  <br/> |

Espandere i titoli di sotto di rete ulteriori istruzioni per la pianificazione. Sono state registrate anche una serie di [ExpressRoute Azure per la formazione su Office 365](https://channel9.msdn.com/series/aer) 10 parti che cade mirate.

## <a name="existing-azure-expressroute-customers"></a>Clienti esistenti ExpressRoute Azure

Se si utilizza un circuito ExpressRoute Azure esistente e si desidera aggiungere la connettività di Office 365 tramite questo circuito, è consigliabile prendere nota del numero di circuiti, le posizioni dei servizi esterni e le dimensioni del circuito a sarà soddisfino le esigenze dell'utilizzo di Office 365. Larghezza di banda aggiuntiva richiedono la maggior parte dei clienti e possono essere necessari ulteriori circuiti.
  
Per abilitare l'accesso a Office 365 tramite i circuiti ExpressRoute Azure esistenti, [configurare i filtri di route](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal) per verificare che i servizi di Office 365 sono accessibili.
  
La sottoscrizione ExpressRoute Azure è incentrato sui sottoscrizioni significato sono legate ai clienti di clienti. Come un cliente può avere più circuiti ExpressRoute Azure e possono accedere a molte risorse cloud Microsoft su tali circuiti. Ad esempio, è possibile scegliere di accedere a un Azure ospitata la macchina virtuale, un test di Office 365 tenant e un tenant di produzione di Office 365 tramite una coppia del circuito Azure ExpressRoute ridondanti.
  
In questa tabella indicano i due tipi di relazioni di peering che è possibile scegliere di implementare tramite i circuiti.

|**Relazione di peering**|**Azure privato**|**Microsoft**|
|:-----|:-----|:-----|
|**Servizi** <br/> |IaaS: Macchine virtuali Azure  <br/> |PaaS: Servizi pubblici Azure  <br/> SaaS: Office 365  <br/> SaaS: Dynamics 365  <br/> |
|Connessione initiation * * * <br/> |Clienti di Microsoft  <br/> Per clienti Microsoft  <br/> |Clienti di Microsoft  <br/> Per clienti Microsoft  <br/> |
|**Supporto di QoS** <br/> |Nessun QoS  <br/> |QoS<sup>1</sup> <br/> |

<sup>1</sup> QoS supporta Skype per le aziende solo in questa fase.
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Pianificazione di Azure ExpressRoute della larghezza di banda

Ogni cliente di Office 365 con esigenze di larghezza di banda univoco a seconda del numero di utenti in ogni punto come attivo sono con ogni applicazione di Office 365 e altri fattori, ad esempio l'utilizzo in locale o ibrida apparecchiature e configurazioni di protezione di rete.
  
Con larghezza di banda insufficiente genera una congestione ritrasmissioni di dati e ritardi imprevisti. Visto troppo della larghezza di banda genera costo non necessarie. In una rete esistente, la larghezza di banda viene spesso in termini di quantità di spazio disponibile nel circuito sotto forma di percentuale. Disporre di capacità aggiuntiva pari al 10% comporterà una congestione e con capacità aggiuntiva 80% in genere, costo non necessarie. Capacità aggiuntiva tipica destinazione allocazioni sono 20% e il 50%.
  
Per trovare il giusto livello di larghezza di banda, il migliore consiste nel testare il consumo di rete esistente. In alcuni modi univoci questo è l'unico modo per ottenere una vera misura di utilizzo ed è necessario come tutte le configurazioni di rete e le applicazioni. Quando la misurazione è consigliabile prestare particolare attenzione per la larghezza di banda totale, alla latenza e la congestione TCP per acquisire familiarità con la rete è necessario.
  
Dopo aver una previsione stimata che include tutte le applicazioni di rete, pilota di Office 365 con un piccolo gruppo che comprende i diversi profili utenti all'interno dell'organizzazione per determinare l'utilizzo effettivo, e utilizzare due misurazioni per stimare la quantità di larghezza di banda che necessarie per ogni sede. Se esistono eventuali problemi di congestione TCP trovati nell'esecuzione dei test o di latenza, potrebbe essere necessario spostare l'uscita più vicino alle persone con Office 365 o rimuovere rete elevata analisi, ad esempio la decrittografia/ispezione SSL.
  
Tutti i consigli sulla è consigliabile utilizzare il tipo di elaborazione di rete si applica a circuiti sia ExpressRoute e Internet. Lo stesso vale anche per il resto della Guida per il [sito di ottimizzazione delle prestazioni](https://aka.ms/tune).
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>L'applicazione di controlli di sicurezza per Azure ExpressRoute per gli scenari di Office 365

Protezione di integrazione applicativa Azure ExpressRoute inizia con gli stessi principi come proteggere la connessione a Internet. Molti clienti scelgono di distribuire i controlli di rete e perimetrale lungo il percorso ExpressRoute connessione la propria rete locale a Office 365 e altri cloud Microsoft. Questi controlli possono includere i firewall, proxy di applicazione, prevenzione della perdita di dati, intrusioni, sistemi per la prevenzione delle intrusioni e così via. In molti casi i clienti applicano diversi livelli di controlli al traffico avviato da locale continui a Microsoft, e il traffico avviato da Microsoft passando alla rete locale dei clienti, e il traffico avviato da locale verranno generale Destinazione Internet.
  
Ecco alcuni esempi dell'integrazione di sicurezza con il [modello di integrazione applicativa ExpressRoute](https://docs.microsoft.com/en-us/azure/expressroute/expressroute-connectivity-models) si sceglie di distribuire.

|**Opzione di integrazione ExpressRoute**|**Modello perimetrale protezione di rete**|
|:-----|:-----|
|Percorso condiviso in un exchange cloud  <br/> |Installare nuovi o utilizzare l'infrastruttura di protezione/perimetrale esistente in struttura posizione condivisa in cui viene stabilita la connessione ExpressRoute.  <br/> Struttura di posizione condivisa sfruttare esclusivamente per le connessioni di distanza back dalla funzionalità di posizione condivisa nell'infrastruttura di protezione/perimetrale locale e ai fini del routing interconnect.  <br/> |
|Scheda Ethernet punto-punto  <br/> |Terminare la connessione point-to-ExpressRoute nel percorso dell'infrastruttura di protezione/perimetrale locale esistente.  <br/> Installare nuova infrastruttura di protezione/perimetrale specifico al percorso ExpressRoute e terminare la connessione point-to-disponibili.  <br/> |
|Tutti a qualsiasi IPVPN  <br/> |Utilizzare un'infrastruttura di protezione/perimetrale locale esistente in tutti i percorsi dei servizi esterni in IPVPN utilizzata per ExpressRoute per la connettività di Office 365.  <br/> "Hairpin" IPVPN utilizzato per ExpressRoute per Office 365 per le posizioni locali specifiche designato come security/perimetrale.  <br/> |

Inoltre, alcuni provider di servizi offrono funzionalità di sicurezza/perimetrale gestito come parte delle proprie soluzioni di integrazione con Azure ExpressRoute.
  
Considerando il posizionamento della topologia delle opzioni/protezione della rete perimetrale utilizzata per ExpressRoute per le connessioni di Office 365 seguenti sono riportate ulteriori considerazioni
  
- I controlli di protezione della rete/profondità e tipo possono incidere sulle prestazioni e scalabilità dell'esperienza utente di Office 365.

- In uscita (su-locale -\>Microsoft) e in ingresso (Microsoft -\>locale) [se abilitata] flussi possono presentare requisiti differenti. Si tratta probabilmente diverso da quello in uscita a destinazioni Internet generale.

- Requisiti di Office 365 per le porte/protocolli e le subnet IP necessarie sono gli stessi se il traffico viene instradato tramite ExpressRoute per Office 365 oppure tramite Internet.

- Topologico posizionamento dei controlli di protezione di rete/cliente determina la rete end-to-end ultima tra l'utente e il servizio Office 365 e può avere un impatto considerevole sulla latenza di rete e congestione.

- Si consiglia di progettare la topologia loro sicurezza/perimetrale per l'utilizzo con ExpressRoute per Office 365 in conformità con procedure consigliate per la ridondanza, disponibilità elevata e ripristino di emergenza.

Di seguito è riportato un esempio di Woodgrove Bank che vengono messi a confronto le diverse opzioni di integrazione applicativa Azure ExpressRoute con i modelli di protezione perimetrale in precedenza.
  
### <a name="example-1-securing-azure-expressroute"></a>Nell'esempio 1: Protezione ExpressRoute Azure
  
Woodgrove Bank sta valutando l'implementazione di Azure ExpressRoute e dopo la pianificazione dell'architettura ottimale per [il Routing con ExpressRoute per Office 365](routing-with-expressroute.md) e dopo l'utilizzo di istruzioni precedenti per informazioni sui requisiti della larghezza di banda sta per determinare la metodo migliore per la protezione delle loro perimetrale.
  
Per Woodgrove, un'organizzazione multinazionale con posizioni in più continenti, sicurezza deve estendersi su perimetri tutti. L'opzione di integrazione applicativa ottimale per Woodgrove è una connessione multipunto con più posizioni peering in tutto il mondo per soddisfare le esigenze dei propri dipendenti in ogni continente. Ogni continente include circuiti Azure ExpressRoute ridondanti all'interno di continente e sicurezza deve estendersi su tutti i componenti.
  
Infrastruttura esistente della Woodgrove è affidabile e in grado di gestire le operazioni aggiuntive, di conseguenza, Woodgrove Bank è in grado di utilizzare l'infrastruttura di protezione perimetrale ExpressRoute Azure e internet. Se ciò non il caso, Woodgrove può scegliere di acquistare apparecchiature aggiuntive per integrare le apparecchiature esistente o per gestire un altro tipo di connessione.
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>Disponibilità elevata e failover con Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

È consigliabile eseguire il provisioning in almeno due circuiti attivi da ogni uscita con ExpressRoute al provider ExpressRoute. Si tratta del punto più comune per i clienti è, vedere gli errori ed è possibile evitare facilmente da una coppia del circuito ExpressRoute attivo/attivo di provisioning. È inoltre consigliabile almeno due circuiti di Internet attivo/attivo poiché molti servizi di Office 365 sono disponibili solo tramite Internet.
  
All'interno della rete il punto di uscita sono molti altri dispositivi e circuiti che riproducono un ruolo fondamentale nel modo persone percepire disponibilità. Le parti degli scenari di integrazione applicativa non sono coperte dai contratti di servizio di Office 365 o ExpressRoute, ma vengono riprodotti un ruolo fondamentale nella disponibilità del servizio end-to-end come percepita dagli utenti nell'organizzazione.
  
Importanza utenti che utilizzano e operativi Office 365, se un errore di un qualsiasi componente potrebbe influire sulle persone esperienza di utilizzo del servizio, cercare i modi per limitare la percentuale totale di utenti interessati. Se la modalità di failover è funzionalmente complessa, è consigliabile esperienza degli utenti del tempo di ripristino e individuare la modalità di failover automatico e semplice livello operativo.
  
Di fuori della rete, Office 365, ExpressRoute e il provider ExpressRoute tutti dispongono diversi livelli di disponibilità.
  
### <a name="service-availability"></a>Disponibilità del servizio
  
- Servizi di Office 365 rientrano ben definito [contratti di servizio](https://technet.microsoft.com/library/office-365-service-level-agreement.aspx), che includono le metriche di disponibilità e tempi di attività per singoli servizi. Uno dei motivi per che Office 365 può soddisfare questi livelli di disponibilità elevata del servizio è la possibilità per i singoli componenti eseguire facilmente il failover tra Data Center Microsoft molti, tramite la rete globale di Microsoft. Questo failover compreso tra i Data Center e di rete in più punti di uscita di Internet e consentire il failover facilmente dal punto di vista degli utenti tramite il servizio.

- ExpressRoute [fornisce un contratto di servizio di disponibilità del 99,9%](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) per i singoli circuiti dedicati tra il bordo di rete di Microsoft e l'infrastruttura ExpressRoute provider o partner. Questi livelli di servizio vengono applicati a livello di circuito ExpressRoute, costituito da [due indipendente interconnette](https://azure.microsoft.com/documentation/articles/expressroute-introduction/) tra i componenti di Microsoft ridondanti e le apparecchiature di provider di rete in ogni punto peering.

### <a name="provider-availability"></a>Disponibilità di provider
  
- Modalità di livello del servizio di Microsoft termina il provider di ExpressRoute o partner. Questo è il primo posto è possibile effettuare le scelte che influenzeranno il livello di disponibilità. È consigliabile valutare attentamente l'architettura, la disponibilità e le caratteristiche di resilienza provider ExpressRoute offre tra la rete perimetrale e la connessione al provider in ogni punto peering Microsoft. Prestare particolare attenzione agli aspetti logici e fisici di ridondanza, attrezzature peering, circuiti WAN gestore fornito e qualsiasi valore aggiuntivi aggiungere servizi, ad esempio servizi di NAT o firewall gestiti.

### <a name="designing-your-availability-plan"></a>La progettazione del piano di disponibilità
  
È consigliabile pianificare e progettare la disponibilità elevata e resilienza in scenari di connettività end-to-end di Office 365. Deve includere una progettazione;
  
- Nessun singoli punti di errore, tra cui circuiti Internet e di ExpressRoute.

- ridurre al minimo il numero di persone interessate e la durata di tale impatto per la gestione degli errori più previsti.

- ottimizzazione del processo di ripristino automatica, ripetibili e semplice da Gestione degli errori più previsti.

- supporto richieste complete del traffico di rete e funzionalità tramite percorsi ridondanti, senza notevole riduzione delle prestazioni.

Gli scenari di integrazione applicativa devono includere una topologia di rete è ottimizzata per più percorsi di rete indipendente e attiva a Office 365. Consente di ottenere una disponibilità meglio end-to-end di una topologia ottimizzato solo per la ridondanza a livello di singoli dispositivi o apparecchiature.
  
> [!TIP]
> Se gli utenti vengono distribuiti in più continenti o aree geografiche e ciascuno di questi percorsi si connette tramite circuiti WAN ridondanti in una posizione locale singolo in cui si trova un singolo circuito ExpressRoute, gli utenti osserveranno minore la disponibilità del servizio end-to-end di un progetto della topologia di rete che include indipendenti circuiti ExpressRoute che si connettono aree geografiche diverse a peering più vicino posizione.
  
È consigliabile eseguire il provisioning in almeno due circuiti ExpressRoute con ogni a commutazione di circuito connette con un percorso peering geografico diverso. È consigliabile eseguire il provisioning questa coppia attivo / attivo del circuito per ogni area di cui utenti utilizzeranno ExpressRoute connettività per servizi di Office 365. In questo modo ogni area rimanere connessi durante una situazione di emergenza che influisce su un percorso principale, ad esempio un Data Center o percorso peering. Configurarle come attivo/attivo consente traffico dell'utente finale deve essere distribuito tra più percorsi di rete. Consente di ridurre l'ambito delle persone interessate durante le interruzioni di apparecchiature di rete o dispositivo.
  
Non è consigliabile utilizzare un unico circuito ExpressRoute Internet come backup.
  
### <a name="example-2-failover-and-high-availability"></a>Nell'esempio 2: Il Failover e la disponibilità elevata
  
Progettazione più geografica Woodgrove Bank ha subito un'analisi di routing, la larghezza di banda, sicurezza e ora deve passare attraverso un'analisi di disponibilità elevata. Woodgrove pensa la disponibilità elevata in modo da coprire tre categorie. resilienza, l'affidabilità e la ridondanza.
  
Resilienza consente Woodgrove recuperare rapidamente gli errori. Affidabilità consente Woodgrove offrire un risultato coerente all'interno del sistema. Ridondanza consente Woodgrove per uno spostamento tra uno o più istanze di mirroring dell'infrastruttura.
  
All'interno di ogni configurazione di server perimetrali, Woodgrove è ridondanti firewall, i proxy e gli ID. Nord America Woodgrove ha una configurazione di edge nel Data Center Dallas e un'altra configurazione di edge nel data center Virginia. Le apparecchiature ridondanti in ogni punto offre la flessibilità per il percorso.
  
Configurazione di rete Woodgrove Bank si basa sulle alcuni principi:
  
- In ogni area geografica, sono disponibili più circuiti ExpressRoute Azure.

- Ogni circuito all'interno di un'area può supportare tutto il traffico di rete all'interno di tale area.

- Routing verrà chiaramente preferiscono una o altri percorsi a seconda della posizione, disponibilità e così via.

- Failover tra ExpressRoute Azure circuiti avviene automaticamente senza ulteriori operazioni di configurazione o azione richiesti da Woodgrove.

- Failover tra circuiti Internet avviene automaticamente senza ulteriori operazioni di configurazione o azione richiesti da Woodgrove.

In questa configurazione, con la ridondanza a livello di fisiche e virtuale Woodgrove Bank è in grado di offrire resilienza locale, resilienza regionale e resilienza globale in modo affidabile. Woodgrove scelto questa configurazione dopo la restituzione di un singolo Azure ExpressRoute a commutazione di circuito per ogni area, nonché la possibilità di eseguire il failover a internet.
  
Se Woodgrove è in grado di avere più circuiti ExpressRoute Azure per ogni area, il routing del traffico proveniente in Nord America al circuito ExpressRoute Azure in Asia Pacifico potrebbe aggiungere un livello accettabile di latenza e la procedura di configurazione del server di inoltro DNS maggiore complessità.
  
Sfruttamento internet come una configurazione di backup non è consigliato. In questo modo si interrompe principio di affidabilità della Woodgrove, risultante in un'esperienza coerente con la connessione. Configurazione manuale, inoltre, è necessaria per il failover prendendo in considerazione gli annunci BGP che sono stati configurati, la configurazione di NAT, configurazione DNS e la configurazione del proxy. Queste aggiunte failover complessità aumenta il tempo di ripristino e riduce la possibilità di diagnosticare e risolvere i passaggi necessari.
  
Ancora dubbi su come pianificare e implementare la gestione del traffico o ExpressRoute Azure? Leggere il resto di [Domande frequenti su ExpressRoute Azure](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)o le [indicazioni di rete e le prestazioni](https://aka.ms/tune) .
  
## <a name="working-with-azure-expressroute-providers"></a>Lavorare con i provider di Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

Scegliere le posizioni del circuito basato sulla larghezza di banda, latenza, sicurezza e pianificazione della disponibilità elevata. Quando si conoscono ottimali percorsi che si desidera inserire circuiti [esaminare l'elenco dei provider dall'area corrente](https://azure.microsoft.com/documentation/articles/expressroute-locations/).
  
Collaborare con il provider o a un provider per selezionare le opzioni di integrazione applicativa best, Point, multipunto o ospitata. Tenere presente che è possibile combinare e soddisfa i criteri del servizio di integrazione applicativa purché la larghezza di banda e altri componenti ridondanti supportano la progettazione di routing e l'elevata disponibilità.
  
Questo è un collegamento breve che è possibile utilizzare il ritorno:[https://aka.ms/planningexpressroute365](https://aka.ms/planningexpressroute365)
  
## <a name="related-topics"></a>Argomenti correlati
<a name="BKMK_high-availability"> </a>

[Connettività di rete con Office 365](network-connectivity.md)
  
[Azure ExpressRoute per Office 365](azure-expressroute.md)
  
[Gestione di ExpressRoute per la connettività di Office 365](managing-expressroute-for-connectivity.md)
  
[Routing con ExpressRoute per Office 365](routing-with-expressroute.md)
  
[Implementazione di ExpressRoute per Office 365](implementing-expressroute.md)
  
[Utilizzo della caratteristica community BGP in ExpressRoute per gli scenari di Office 365 (preview)](bgp-communities-in-expressroute.md)
  
[Qualità multimediale e le prestazioni di connettività di rete in Skype for Business in linea](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Ottimizzazione della rete per Skype Business online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute e QoS in Skype for Business in linea](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Flusso di chiamate tramite ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Ottimizzazione delle prestazioni di Office 365 mediante l'uso della cronologia delle prestazioni e delle previsioni](performance-tuning-using-baselines-and-history.md)
  
[Piano di risoluzione dei problemi di prestazioni per Office 365](performance-troubleshooting-plan.md)
  
[URL e intervalli di indirizzi IP per Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Ottimizzazione delle prestazioni e rete di Office 365](network-planning-and-performance.md)
  
[Domande frequenti sugli endpoint di Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
