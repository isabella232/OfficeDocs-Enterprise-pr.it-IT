---
title: Ottimizzazione delle prestazioni di Office 365 mediante l'uso della cronologia delle prestazioni e delle previsioni
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/31/2017
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 1492cb94-bd62-43e6-b8d0-2a61ed88ebae
description: Sono disponibili alcuni modi semplici per controllare le prestazioni di connessione tra Office 365 e l'azienda che consente di stabilire una base approssimativa della connettività. Conoscenza dei collegamenti al computer la cronologia delle prestazioni del client consentono di individuare gli eventuali problemi emergenti all'inizio, identificare e prevedere problemi.
ms.openlocfilehash: 30a0903d95ccfcd2018d8971c74c7f80223c005d
ms.sourcegitcommit: e334616f1b357365b380990eda63f6e63d52ec5b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2018
ms.locfileid: "26024688"
---
# <a name="office-365-performance-tuning-using-baselines-and-performance-history"></a>Ottimizzazione delle prestazioni di Office 365 mediante l'uso della cronologia delle prestazioni e delle previsioni

Sono disponibili alcuni modi semplici per controllare le prestazioni di connessione tra Office 365 e l'azienda che consente di stabilire una base approssimativa della connettività. Conoscenza dei collegamenti al computer la cronologia delle prestazioni del client consentono di individuare gli eventuali problemi emergenti all'inizio, identificare e prevedere problemi.
  
Se sono abituati all'utilizzo di problemi di prestazioni, in questo articolo è progettato per essere utili per prendere in considerazione alcune domande comuni, come in modo da sapere il problema che sta visualizzando è un problema di prestazioni e non un evento imprevisto del servizio di Office 365? Come è possibile pianificare per prestazioni ottimali, a lungo termine? Come è possibile impedire un'occhiata in termini di prestazioni? Se il team o i client sono visualizzando un rallentamento delle prestazioni durante l'utilizzo di Office 365 e una descrizione di queste domande, continuare a leggere.
  
> [!IMPORTANT]
> **Presentano un problema di prestazioni tra i client e Office 365 direttamente?** Seguire le procedure descritte nel [piano di Office 365 risoluzione dei problemi di prestazioni](performance-troubleshooting-plan.md). 
    
## <a name="something-you-should-know-about-office-365-performance"></a>Un elemento è necessario tenere conto delle prestazioni di Office 365

Office 365 si trova all'interno di una rete di Microsoft dedicata, capacità elevata monitorati costantemente non solo di automazione, ma da persone reali. La parte del ruolo di gestione nel cloud di Office 365 è di creazione e ottimizzazione delle prestazioni semplificazione dove è possibile. Poiché i client di Office 365 cloud per la connessione tramite Internet, è disponibile uno sforzo continuo per ottimizzare le prestazioni in tutti i servizi di Office 365 troppo. Miglioramenti delle prestazioni arrestare mai nel cloud ed è disponibile una quantità elevata di esperienza accumulata con mantenendo cloud integro e veloce. Dovrebbero si verifichino problemi di prestazioni connessione dalla propria posizione a Office 365, è consigliabile iniziare con non e attendere in un caso del supporto tecnico. In realtà, è necessario iniziare analisi dei problemi 'in modo completo'. Vale a dire, avviare all'interno della rete e scoprire come a Office 365. Prima di aprire un caso con il supporto tecnico di Office 365, è possibile raccogliere dati ed eseguire azioni che verranno analizzate e possono risolvere il problema.
  
> [!IMPORTANT]
> Tenere conto dei limiti in Office 365 e la pianificazione della capacità. Tali informazioni verranno posizionare il passo avanti quando si tenta di risolvere un problema di prestazioni. Di seguito è un collegamento a [Office 365 Platform Service Description](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx). Si tratta di un hub centrale e tutti i servizi offerti da Office 365 dispongano di un collegamento che consente di accedere al proprio descrizioni dei servizi da qui. Ciò significa, dovrebbe necessario per SharePoint Online, vedere limiti standard, ad esempio, scegliere [Descrizione del servizio SharePoint Online](https://technet.microsoft.com/en-us/library/sharepoint-online-service-description.aspx) e individuare la [sezione limiti di SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkID=856113). 
  
Verificare che influiscono sulla risoluzione dei problemi con la consapevolezza di prestazioni sono una scala di scorrimento, non viene incluso per ottenere un valore di simulazione e la gestione in modo permanente (se si ritiene che si tratta di questa operazione, quindi occasionale ampia larghezza di banda attività quali audiovisivi un numero elevato di utenti, o eseguire le migrazioni dei dati di grandi dimensioni è molto stressante, quindi pianificare impatto sulle prestazioni quindi). È possibile e, è necessario una semplice indicazione gli obiettivi di prestazioni, ma varia una quantità elevata di riproduzione variabili nelle prestazioni, di conseguenza, le prestazioni. È la natura delle prestazioni. 
  
Risoluzione dei problemi di prestazioni non su conseguimento degli obiettivi specifici e gestione di tali numeri per un tempo indefinito, è sul miglioramento delle attività esistente, assegnate tutte le variabili. 
  
## <a name="okay-what-does-a-performance-problem-look-like"></a>Passare alla procedura guidata che problemi di prestazioni aspetto?

Per prima cosa, è necessario assicurarsi che si verificano è effettivamente un problema di prestazioni e non un problema di servizio. Problemi di prestazioni sono diverso da un problema di servizio in Office 365. Di seguito è illustrato per informarli distinto.
  
Se il servizio Office 365 si verificano problemi, che corrisponde a un evento imprevisto del servizio. Verrà visualizzato rosse o gialle icone all' **integrità corrente** nell'interfaccia di amministrazione di Office 365, è possibile inoltre un rallentamento delle prestazioni nei computer client la connessione a Office 365. Ad esempio, se un'icona rossa rapporti di integrità corrente e viene visualizzato **Investigating** accanto a Exchange, è possibile quindi inoltre ricevere una serie di chiamate da persone all'interno dell'organizzazione che si lamentano perché che esegue le cassette postali client che utilizzano Exchange Online. In tal caso, è ragionevole si supponga che le prestazioni di Exchange Online è appena stato vittime di problemi all'interno del servizio. 
  
![Il dashboard di Office 365 integrità con tutti i carichi di lavoro che mostra verde, ad eccezione di Exchange, che visualizza servizio ripristinato.](media/ec7f0325-9e61-4e1a-bec0-64b87f4469be.PNG)
  
A questo punto, l'amministratore di Office 365, controllare **integrità corrente** e quindi **la cronologia e visualizzare i dettagli**, spesso, per mantenere aggiornati su manutenzione è eseguire nel sistema. Il dashboard **sull'integrità corrente** è stato effettuato da aggiornare è sulle modifiche apportate alle e problemi nel servizio. Le note e spiegazioni scritte nella cronologia di integrità, admin su admin, esistono che consentono di valutare l'impatto e mantenere è registrato sull'ufficio in corso. 
  
![Un'immagine di Office 365 integrità dashboard che spiega che è stato ripristinato il servizio Exchange Online e il motivo.](media/66609554-426a-4448-8be6-ea09817f41ba.PNG)
  
Problemi di prestazioni non sono un problema di servizio, anche se risolte possono causare un rallentamento delle prestazioni. Problemi di prestazioni è simile al seguente:
  
- Si verifica un problema di prestazioni indipendentemente dalle quali l'interfaccia di amministrazione di Office 365 **integrità corrente** viene segnalato per il servizio. 
    
-  Un comportamento che era relativamente semplice richiede molto tempo per il completamento o non viene mai completata. 
    
- È possibile replicare il problema troppo o, almeno, si conosce che tale operazione verrà eseguita in caso contrario la serie di operazioni destra.
    
-  Se il problema è intermittente, vi è ancora un modello, ad esempio, si è certi che da 10:00 AM si avrà le chiamate provenienti da utenti che non sono affidabile accedono a Office 365 e che le chiamate verranno annullamento verso il basso intorno a mezzogiorno. 
    
Tutto ciò probabilmente suona familiare; forse troppo familiarità. Quando si conosce è un problema di prestazioni, la domanda diventa, "In che modo? Avanti" Il resto di questo articolo consente di determinare esattamente che.
  
## <a name="how-to-define-and-test-the-performance-problem"></a>Come definire e testare il problema di prestazioni

Problemi di prestazioni emergono spesso nel tempo, in modo che può diventare problematico per definire il problema effettivo. È necessario creare un'istruzione problemi ben e una buona idea del contesto problema e, sarà necessario alle fasi di testing ripetibili win giorno. In caso contrario, tramite alcun errore personalizzato, è possibile persi. Perché? Di seguito sono riportati alcuni esempi delle istruzioni di problemi che non forniscono informazioni sufficienti:
  
- Passaggio dalla posta in arrivo per il calendario utilizzato per un elemento che è possibile non osservare e a questo punto è una pausa. Possono essere apportate funzionano come viene utilizzato per?
    
- Caricamento dei file in SharePoint Online è un'operazione molto lunga. Perché è lenta pomeriggio, ma qualsiasi altro momento, è fast? Non può solo essere fast?
    
Sono disponibili diverse sfide grande insite istruzioni problema elencate in precedenza. In particolare, sono presenti molte delle ambiguità per affrontare. Per esempio:
  
- Non è chiaro come passare dal calendario e posta in arrivo consente di agire sul portatile.
    
- Quando si indica che l'utente, "non è semplicemente esserlo fast", che cos'è "fast"?
    
- Quanto tempo è "infinita"? Consiste nel fatto che alcuni secondi o minuti, o è l'utente passare a pranzo e sarebbe fine backup dieci minuti dopo aver ricevuto l'utente?
    
Tutte queste operazioni senza considerare che l'amministrazione e risoluzione dei problemi non può essere consapevoli dei dettagli da tali alcuni dei problemi. Ad esempio, quando il problema avviata appuntamenti; Lavora da casa e sempre solo l'utente visualizza commutazione lente in una rete domestica; Che l'utente deve eseguire numerose altre applicazioni che richiede molte risorse di RAM sul client locale o l'utente è un sistema operativo precedente non ha eseguito o aggiornamenti recenti.
  
Quando gli utenti segnalano problemi di prestazioni, non esiste una quantità elevata di informazioni da raccogliere. La raccolta di queste informazioni fa parte di un processo noto come ambito il problema o ulteriori ricerche. Di seguito è un elenco all'ambito base che è possibile utilizzare per raccogliere le informazioni relative al problema delle prestazioni. In questo elenco non è completo, ma è un punto di partenza uno personalizzato: 
  
- Quali data ha il problema si verificano e intorno a che ora del giorno o della notte?
    
- Quale tipo di computer client si stava utilizzando e come si connette alla rete aziendale (VPN, rete cablata, Wireless)?
    
- Sono stati lavora in remoto o sono state in ufficio.
    
- Ha le stesse operazioni su un altro computer di prova e lo stesso comportamento?
    
- Eseguire i passaggi che offrono i problemi in modo che sia possibile scrivere azioni effettuate verso il basso.
    
- Le prestazioni sono i come lente in pochi secondi o minuti?
    
- Dove nel mondo trovano?
    
Alcune di queste domande sono più ovvie rispetto ad altri. La maggior parte dei tutti gli utenti di comprendere che una risoluzione dei problemi deve dettaglio la procedura per riprodurre il problema. Dopo tutto, come altre posizioni possono registrare qual è il e altre posizioni come è possibile verificare se il problema è stato risolto? Meno ovvie essere, ad esempio "cosa data e ora hai acquistato vedere il problema?" e "Dove del mondo si trova?", le informazioni che possono essere utilizzate in coppia. A seconda se quest ' ultimo è stato in, alcune ore di differenza di tempo possono indicare manutenzione è già in corso nella Web part di rete della società. Se, ad esempio, la società dispone di un'implementazione ibrida, ad esempio una ricerca di SharePoint, eseguire una query ibrida indici di ricerca in SharePoint Online e un Server di SharePoint locale 2013 istanza, gli aggiornamenti in corso nella farm locale. Se la società è tutto nel cloud, la manutenzione del sistema può riguardare aggiunta o rimozione di componenti hardware di rete, distribuzione degli aggiornamenti presenti a livello aziendale o le modifiche al DNS o altre infrastruttura di base.
  
Quando si sta risolvendo un problema di prestazioni, è un po' come una scena crime, è necessario essere precisi ed esperto disegnare le conclusioni di prova. Per eseguire questa operazione, è necessario ottenere un'istruzione buona problema con la raccolta di prova. Da includere il computer utilizzato dall'utente, al contesto dell'utente, se il problema si è verificato e i passaggi esatti esposte problema delle prestazioni. Questa istruzione problema deve essere e rimanere, pagina delle note. Esaminando l'istruzione problema nuovamente dopo che si sta lavorando la risoluzione, per cui vengono eseguite le operazioni di testing e la dimostrazione se l'azione di aver risolto il problema. Ciò è importante per sapere quando il lavoro, non esiste, viene eseguito.
  
## <a name="do-you-know-how-performance-used-to-look-when-it-was-good"></a>Utilizzo delle prestazioni da considerare quando si tratta di una buona sanno

Se si è sfortunato, nessuno è a conoscenza. Nessuno con numeri. Ciò significa che nessuno può rispondere alla domanda semplice "informazioni su come numero di secondi è stato viene in genere necessari per attivare la posta in arrivo in Office 365?" o "quanto tempo è stato utilizzato da eseguire quando i dirigenti hanno una Lync Online meeting?", ovvero un tipico scenario per molte aziende.
  
Che cos'è mancante Ecco una previsione delle prestazioni.
  
Previsioni offrono un contesto per le prestazioni. È necessario prendere una linea di base occasionalmente a frequentemente, a seconda delle esigenze dell'azienda. Se si è una società di grandi dimensioni, il team addetto alle operazioni potrebbe richiedere già previsioni per l'ambiente locale. Ad esempio, se si patch per tutti i server Exchange il primo lunedì del mese e tutti i server di SharePoint nel terzo lunedì, il team addetto alle operazioni probabilmente è presente un elenco delle attività e scenari viene eseguito dopo l'aggiornamento, per dimostrare che funzioni critiche sono operativa. Ad esempio, aprire la cartella Posta in arrivo, facendo clic su Invia/Ricevi e assicurandosi aggiornare le cartelle o, in SharePoint, visualizzando la pagina principale del sito di entrare in una pagina di ricerca dell'organizzazione e si esegue una ricerca restituisce risultati.
  
Se le proprie applicazioni in Office 365, alcune delle linee di base più importante, che è possibile eseguire misura il tempo (in millisecondi) da un computer client all'interno della rete a un punto di uscita o il punto in cui si lascia la rete e visita da Office 365. Ecco alcuni utili previsioni che è possibile ricercare e record:
  
- Identificare i dispositivi tra computer client e il punto di uscita, ad esempio, il server proxy.
    
  - È necessario conoscere i dispositivi in modo da avere contesto (indirizzi IP, tipo di dispositivo, et cetera) per problemi di prestazioni che si verificano.
    
  - Server proxy sono comuni punti di uscita e in modo che è possibile controllare il web browser per visualizzare i server proxy viene impostata da utilizzare, se disponibili.
    
  - Sono disponibili strumenti di terze parti che consente di rilevare e il mapping della rete, ma è il modo più sicuro per conoscere i dispositivi per chiedere a un membro del team di rete.
    
- Identificare i provider di servizi Internet (ISP), annotare le informazioni di contatto e chiedere quanti circuiti quanta larghezza di banda si dispone.
    
- All'interno della società, identificare le risorse per i dispositivi tra client e il punto di uscita oppure individuare un contatto di emergenza per parlare con sui problemi di rete.
    
Ecco alcune linee di base che semplice test con gli strumenti possono calcola automaticamente:
  
- Tempo tra computer client e il punto di uscita in millisecondi
    
- Tempo dal punto di uscita a Office 365 in millisecondi
    
- Posizione nel mondo del server che consente di risolvere l'URL per Office 365 durante l'esplorazione
    
- La velocità della risoluzione DNS del proprio ISP in millisecondi, incoerenze in arrivo di pacchetti (instabilità di rete), caricamento e download di volte in millisecondi
    
Se si ha familiarità con come effettuare queste operazioni, ci sarà illustrare più dettagliatamente in questo articolo. 
  
## <a name="what-is-a-baseline"></a>Che cos'è una linea di base?

Significa l'impatto quando viene inoltrata non valido, ma se non si conoscono i dati cronologici relativi alle prestazioni, non è possibile disporre di un contesto per come non validi può essere diventate e quando. In modo persi senza una linea di base, indicazione chiave per il puzzle: l'immagine nella casella puzzle. La risoluzione dei problemi di prestazioni, è necessario un punto di *confronto* . Previsioni di prestazioni semplice non sono difficili da eseguire. Il team addetto alle operazioni può essere assegnato il compito di esecuzione di queste in base alla pianificazione. Si supponga, ad esempio, che la connessione è simile al seguente: 
  
![Una rete di base grafica client, proxy e cloud di Office 365.](media/c6ca7140-09f9-4c2d-a775-dbf2820eaa0c.PNG)
  
Ciò significa è stato archiviato con il team di rete e hanno riscontrato che si lascia l'azienda per Internet tramite un server proxy e proxy gestisce tutte le richieste di che computer client invia nel cloud. In questo caso, è consigliabile disegnare una versione semplificata della connessione in cui sono elencati tutti i dispositivi intermedi. A questo punto, inserire gli strumenti che è possibile utilizzare per testare le prestazioni tra i client, il punto di uscita (dove si lascia la rete per Internet) e Office 365 cloud.
  
![Rete di base con client, proxy e cloud e i suggerimenti di strumenti PSPing, TraceTCP e le tracce di rete.](media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
Come **semplice** e **Avanzate** sono elencate le opzioni per la quantità di conoscenze che necessarie per trovare i dati sulle prestazioni. Traccia di rete può richiedere molto tempo, rispetto all'esecuzione strumenti da riga di comando come PsPing e TraceTCP. Questi due strumenti da riga di comando fosse stata scelta in quanto non utilizzano i pacchetti ICMP, verranno bloccati da Office 365, e il fatto che permettono il tempo in millisecondi necessario lasciare il computer client o server proxy (se si dispone dell'accesso) e arrivano in Office 365. Ogni hop singolo da un computer a un altro terminerà con un valore ora e che è ottimo per linee di base! Così come importante, questi strumenti da riga di comando consentono di aggiungere un numero di porta il comando, questa è utile perché Office 365 comunica tramite la porta 443, ovvero la porta utilizzata dal Transport Layer Security (SSL e TLS) e SSL (Secure Sockets Layer). Altri strumenti di terze parti, tuttavia, potrebbero essere migliori soluzioni per la situazione. Microsoft non supporta tutti questi strumenti, pertanto se per qualche motivo, non è possibile ottenere PsPing e TraceTCP funziona, passare alla traccia di rete con uno strumento simile Netmon. 
  
Prima dell'orario di ufficio nuovamente durante l'utilizzo elevato, è possibile eseguire una linea di base e quindi nuovamente dopo ore. Ciò significa che potrebbe essere una struttura di cartelle che si presenta più simile al seguente alla fine:
  
![Grafica che propone una soluzione per organizzare i dati delle prestazioni in cartelle.](media/13e01ffa-f0f2-4d10-b89d-d5980ec89fae.png)
  
È inoltre opportuno scegliere una convenzione di denominazione dei file. Di seguito sono riportati alcuni esempi:
  
- Feb_09_2015_9amPST_PerfBaseline_Netmon_ClientToEgress_Normal
    
- Jan_10_2015_3pmCST_PerfBaseline_PsPing_ClientToO365_bypassProxy_SLOW
    
- Feb_08_2015_2pmEST_PerfBaseline_BADPerf
    
- Feb_08_2015_8 30amEST_PerfBaseline_GoodPerf
    
Sono numerosi i diversi modi per eseguire questa operazione, ma utilizza il formato ** \<dateTime\>\<quanto avviene nel test\> ** è un ottimo punto di partenza. Corso attente su questa viene illustrato come maggiormente quando si sta tentando di risolvere i problemi più avanti. In seguito, sarà possibile affermare "ha eseguito le due tracce su 8 febbraio uno hanno dimostrato buone prestazioni e uno stato non valido, in modo che è possibile eseguire un confronto". Si tratta estremamente utile per la risoluzione dei problemi. 
  
È necessario che risulta utile per mantenere le previsioni storica. In questo esempio, i metodi semplici prodotta tre output della riga di comando e i risultati sono stati raccolti come catture di schermata, ma potrebbe essere invece i file di acquisizione di rete. Utilizzare il metodo più adatta automaticamente. Archiviare le previsioni cronologiche e fare riferimento a punti di cui si noterà modificano il comportamento dei servizi online. 
  
## <a name="why-collect-performance-data-during-a-pilot"></a>Perché raccogliere dati sulle prestazioni durante un test pilota?

Non esiste alcun momento migliore per iniziare ad apportare previsioni di durante un test pilota del servizio Office 365. L'ufficio di migliaia di utenti, potrebbe essere centinaia di migliaia o 5, ma anche con un numero limitato di utenti, è possibile eseguire alcuni test per misurare fluttuazioni delle prestazioni. Nel caso di una società di grandi dimensioni rappresentative alcuni degli diverse centinaia di utenti distribuzione pilota di Office 365 possono proiettare verso l'esterno a diverse migliaia per sapere dove potrebbero verificarsi i problemi prima che si verifichino.
  
Nel caso di una piccola società, dove audiovisivi significa che tutti gli utenti di accedere al servizio contemporaneamente e non esiste alcun pilota, tenere misure delle prestazioni in modo da avere i dati per mostrare a tutti coloro che potrebbe essere necessario risolvere i problemi di un'operazione di prestazioni in modo errato. Ad esempio, se si nota che all'improvviso è possibile scorrere attorno dell'edificio nel tempo che necessario per caricare un'immagine di medie dimensioni in cui utilizzato per eseguire rapidamente.
  
## <a name="how-to-collect-baselines"></a>Come per la raccolta di previsioni

Per tutti i piani di risoluzione dei problemi è necessario identificare tali aspetti come minimo:
  
- Il computer client si utilizza (il tipo di computer o dispositivi, un indirizzo IP e le azioni che hanno causato il problema)
    
- Dove si trova il computer client nel mondo (ad esempio, se l'utente in una rete VPN per rete, si lavora in remoto, o in rete intranet aziendale)
    
- Il punto di uscita del computer client viene utilizzato dalla rete (il punto in cui il traffico lascia l'organizzazione per un provider di servizi Internet o Internet)
    
 Identificare il layout della rete dell'amministratore di rete. Se si è in una rete di dimensioni ridotte, esaminare i dispositivi di connessione a Internet e chiamare l'ISP se quesiti relativi al layout. Creare un'immagine del layout finale per riferimento. 
  
In questa sezione viene suddiviso in metodi e gli strumenti da riga di comando semplici e più avanzate opzioni del menu Strumenti. Metodi semplici verranno trattati prima. Ma se hai direttamente problemi di prestazioni, è necessario passare ai metodi avanzati e provare a utilizzare il piano di azione risoluzione dei problemi relativi alle prestazioni di esempio.
  
### <a name="simple-methods"></a>Metodi semplici

L'obiettivo di questi metodi semplici consiste nel richiedere, comprendere ed archiviare correttamente previsioni semplice prestazioni nel tempo in modo che l'utente viene informato sulle prestazioni di Office 365. Ecco il diagramma molto semplice per semplice, come visto prima in:
  
![Rete di base con client, proxy e cloud e i suggerimenti di strumenti PSPing, TraceTCP e le tracce di rete.](media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
> [!NOTE]
> TraceTCP è incluso in questa schermata perché è uno strumento utile per la visualizzazione delle, in millisecondi, una richiesta di tempo per processo e quante hop di rete o connessioni da un solo computer alla successiva, che accetta la richiesta di raggiungere una destinazione. TraceTCP possono anche assegnare i nomi dei server utilizzati durante l'hop, che può essere utile per una risoluzione dei problemi di Microsoft Office 365 in supporto. > Comandi TraceTCP possono essere molto semplici, ad esempio: > `tracetcp.exe outlook.office365.com:443`> ricordarsi di includere il numero di porta nel comando! > [TraceTCP](http://simulatedsimian.github.io/tracetcp_download.html) è disponibile come download gratuito, ma si basa su Wincap. Wincap è uno strumento che viene inoltre utilizzato e installato in Netmon. È inoltre possibile utilizzare Netmon nella sezione metodi avanzati. 
  
 Se si dispone di più uffici, è necessario mantenere un blocco di dati da un client di ciascuno di questi percorsi anche. Questo test misure di latenza, che, in questo caso, è un valore numerico che descrive la quantità di tempo tra un client invia una richiesta a Office 365 e Office 365 risponde alla richiesta. Il test viene creato il dominio in un computer client e Cerca per misurare un round trip dall'interno della rete tramite un punto di uscita via Internet a Office 365 ed eseguire il. 
  
Sono disponibili alcuni modi per gestire il punto di uscita del, in questo caso, il server proxy. È possibile tracciare da 1 a 2 e quindi 2 e 3 e quindi aggiungere i numeri in millisecondi per ottenere un totale complessivo e il lato della rete. In alternativa, è possibile configurare la connessione per ignorare il proxy per indirizzi di Office 365. In una rete di dimensioni superiore con un firewall, proxy inverso o una combinazione delle due configurazioni, è necessario creare eccezioni nel server proxy per consentire il traffico da passare per una quantità elevata di URL. Per l'elenco degli endpoint utilizzato da Office 365, vedere [Office 365 URL e intervalli di indirizzi IP](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2). Se si dispone di un proxy di autenticazione, iniziare eseguendo il test eccezioni per le operazioni seguenti:
  
- Porte 80 e 443
    
- TCP e HTTPs
    
- Connessioni in uscita verso uno di questi URL:
    
- \*. microsoftonline.com
    
- \*.microsoftonline p.com
    
- \*. sharepoint.com
    
- \*. outlook.com
    
- \*. lync.com
    
- osub.microsoft.com
    
Tutti gli utenti hanno l'esigenza per ottenere tali indirizzi senza interferenza con proxy o l'autenticazione. In una rete di dimensioni ridotte, è consigliabile aggiungere che tali per il proxy di bypass elenco nel web browser. 
  
Per aggiungerli all'elenco di bypass proxy in Internet Explorer, andare a **Strumenti** \> **Opzioni Internet** \> **connessioni** \> **Impostazioni LAN** \> **Avanzate**. Scheda Avanzate è anche dove si trova il server proxy e porta del server proxy. Potrebbe essere necessario selezionare la casella di controllo **utilizza un server proxy per le connessioni LAN**per accedere al pulsante **Avanzate** . È consigliabile verificare che sia selezionata **Ignora server proxy per indirizzi locali** . Una volta che si fa clic su **Avanzate**, vedrai una casella di testo in cui è possibile immettere le eccezioni. Separare gli URL con caratteri jolly sopra elencati con punti e virgola, ad esempio:
  
\*. microsoftonline.com; \*. sharepoint.com
  
Una volta che si ignora il proxy, sarà possibile utilizzare il comando ping o PsPing direttamente in un URL di Office 365. Per testare il comando ping **outlook.office365.com**è il passaggio successivo. In alternativa, se si utilizza PsPing o un altro strumento che sia possibile fornire un numero di porta per il comando PsPing contro **portal.microsoftonline.com:443** per verificare il tempo di round trip Media in millisecondi. 
  
Il tempo di round trip o RTT, è un valore numerico che misura il tempo impiegato per inviare una richiesta HTTP a un server come outlook.office365.com e ottenere nuovamente una risposta che riconosce che server SA stata eseguita. In alcuni casi vedremo questo abbreviato in RTT. Deve trattarsi di un periodo di tempo relativamente breve.
  
È necessario utilizzare [PSPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx) o un altro strumento che non utilizza i pacchetti di ICMP bloccati da Office 365 per poter effettuare questo test. 
  
 **Come utilizzare PsPing per ottenere un' generale andata tempo in millisecondi direttamente da un URL di Office 365**
  
1. Eseguire un prompt dei comandi con privilegi elevati completando la procedura seguente:
    
1. Fare clic sul pulsante **Start**.
    
2. Nella casella **Inizia la ricerca** , digitare cmd e quindi premere CTRL + MAIUSC + INVIO.
    
3. Se viene visualizzata la finestra di dialogo **Controllo account utente**, confermare che l'azione visualizzata è quella desiderata e scegliere **Continua**.
    
2. Passare alla cartella in cui è installato lo strumento (in questo caso PsPing) e verificare gli URL di Office 365:
    
  - psping portal.office.com:443
    
  - microsoft psping-my.sharepoint.com:443
    
  - psping outlook.office365.com:443
    
  - psping www.yammer.com:443
    
    ![Il comando PSPing microsoft my.sharepoint.com porta 443.](media/3258f620-4513-4e82-95c9-06b387fc3a82.PNG)
  
È necessario includere il numero di porta 443. Tenere presente che Office 365 funzioni in un canale crittografato. Se si PsPing senza il numero di porta, l'invio della richiesta avrà esito negativo. Dopo aver eseguito il ping di elenco short, cercare il tempo medio in millisecondi (ms). È che si desidera registrare!
  
![Grafico che mostra un'illustrazione dei client al proxy PSPing con un tempo di round trip di 2,8 millisecondi.](media/96901aea-1093-4f1b-b5a3-6078e9035e6c.png)
  
Se si si ha familiarità con bypass proxy e si preferisce per richiedere informazioni dettagliate, è necessario innanzitutto individuare il nome del server proxy. In Internet Explorer passare a **Strumenti** \> **Opzioni Internet** \> **connessioni** \> **Impostazioni LAN** \> **Avanzate**. Scheda **Avanzate** è dove verrà visualizzato il server proxy elencato. Eseguire il ping di tale server proxy un prompt dei comandi eseguendo questa attività: 
  
 **Per effettuare il ping del server proxy e ottenere un valore di round trip in millisecondi per la fase 1-2**
  
1. Eseguire un prompt dei comandi con privilegi elevati completando la procedura seguente:
    
1. Fare clic sul pulsante **Start**.
    
2. Nella casella **Inizia la ricerca** , digitare cmd e quindi premere CTRL + MAIUSC + INVIO.
    
3. Se viene visualizzata la finestra di dialogo **Controllo account utente**, confermare che l'azione visualizzata è quella desiderata e scegliere **Continua**.
    
2. Digitare ping \<il nome del server proxy utilizzato dal browser o l'indirizzo IP del server proxy\> e quindi premere INVIO. Se si dispone di PsPing o un altro strumento, installazione, è possibile scegliere da utilizzare per tale strumento. 
    
    Il comando sia simile a uno di questi esempi: 
    
  - eseguire il ping ourproxy.ourdomain.industry.business.com
    
  - eseguire il ping 155.55.121.55
    
  - eseguire il ping ourproxy
    
  - psping ourproxy.ourdomain.industry.business.com:80
    
  - psping 155.55.121.55:80
    
  - psping ourproxy:80
    
3. Quando la traccia interrompe l'invio di pacchetti di test, verrà visualizzato un riepilogo piccolo una media, in millisecondi, con l'elenco e che è il valore che è dopo. Richiedere una schermata del prompt dei comandi e salvarlo utilizzando la convenzione di denominazione. A questo punto può essere utile per l'inserimento di diagramma con il valore.
    
Forse, è consigliabile una traccia del mattino anticipati e i client possano accedere rapidamente al proxy (o esce da qualsiasi server in uscita a Internet). In questo caso, i numeri potrebbero essere simile al seguente:
  
![Grafico che mostra il tempo di round trip da un client a un proxy di 2,8 millisecondi.](media/1bd03544-23fc-47d4-bbae-c1feb466a5d8.PNG)
  
Se il computer client è una delle poche select con l'accesso al server proxy (o in uscita), è possibile eseguire il tratto successivo del test tramite la connessione in remoto a tale computer che esegue il prompt dei comandi per PsPing a un URL di Office 365 da quest'ultimo. Se non disponi di accedere al computer, è possibile contattare le risorse di rete per la Guida in linea con il successivo tratto e get esatta numeri in questo modo. Se non è possibile, utilizzare una PsPing con l'URL di Office 365 in questione e confrontare con l'ora PsPing o Ping per il server proxy. 
  
Ad esempio, se si dispone 51.84 millisecondi dal client all'URL di Office 365 e aver 2,8 millisecondi dal client al proxy (o punto di uscita), è necessario 49.04 millisecondi dall'uscita a Office 365. Analogamente, se si dispone PsPing di 12.25 millisecondi dal client al proxy durante l'altezza del giorno e 62.01 millisecondi dal client di Office 365 URL, il valore medio di uscita proxy per l'URL di Office 365 è 49.76 millisecondi.
  
![Ulteriore immagine grafica che mostra il ping in millisecondi dal client al proxy accanto a client a Office 365 in modo che i valori possono essere sottratto.](media/cd764e77-5154-44ba-a5cd-443a628eb2d9.PNG)
  
In termini di risoluzione dei problemi, è possibile qualcosa di interessante solo da mantenere queste linee di base. Ad esempio, se si rileva che in genere su 40 e 59 millisecondi della latenza dal proxy o uscita punti all'URL di Office 365 ed è un client di latenza punto proxy o uscita di millisecondi di circa 3 a 7 (a seconda della rete quantità traffico si sta seein g durante tale ora del giorno), quindi sicuramente saprai che un elemento è un problema se visualizzare le ultime tre client di previsioni proxy o uscita da una latenza di 45 millisecondi.
  
### <a name="advanced-methods"></a>Metodi avanzati

Se si desidera realmente conoscere quanto avviene con le richieste Internet a Office 365, è necessario acquisire familiarità con le tracce di rete. Non è importante degli strumenti si preferisce per le tracce, HTTPWatch, Netmon, messaggio Analyzer, Wireshark, Fiddler, strumento di Dashboard di sviluppo o qualsiasi altra eseguite, purché tale strumento può acquisire e filtrare il traffico di rete. Verrà visualizzato in questa sezione è utile eseguire più di uno di questi strumenti per ottenere una panoramica dettagliata del problema. Quando si verifica, alcuni di questi strumenti fungere anche proxy propri. Gli strumenti utilizzati nell'articolo complementare, [risoluzione dei problemi di prestazioni piano per Office 365](performance-troubleshooting-plan.md), includono [Netmon 3.4](https://www.microsoft.com/en-us/download/details.aspx?id=4865), [HTTPWatch](https://www.httpwatch.com/download/)o [WireShark](https://www.wireshark.org/).
  
Ottenere un riferimento per le prestazioni è semplice parte di questo metodo e molti dei passaggi solo gli stessi per la risoluzione dei problemi di prestazioni. I metodi più avanzati di creazione di previsioni per le prestazioni è necessario prendere e archiviare le tracce di rete. La maggior parte degli esempi in questo articolo utilizza SharePoint Online, ma è necessario sviluppare un elenco delle azioni comuni tra i servizi di Office 365 che si desidera sottoscrivere per testare e registrare. Ecco un esempio di base:
  
- Elenco di base per SharePoint Online - * * passaggio 1: * * Sfoglia la home page del sito Web di SharePoint Online ed eseguire una traccia di rete. Salvare la registrazione. 
    
- Elenco di base per SharePoint Online - **passaggio 2:** ricercare un termine (ad esempio il nome della società) tramite ricerca contenuti organizzazione, quindi effettuare una traccia di rete. Salvare la registrazione. 
    
- Elenco di base per SharePoint Online - **passaggio 3:** carica un file di grandi dimensioni a una raccolta documenti di SharePoint Online, quindi effettuare una traccia di rete. Salvare la registrazione. 
    
- Elenco di base per SharePoint Online - **passaggio 4:** Sfoglia la home page del sito Web di OneDrive ed eseguire una traccia di rete. Salvare la registrazione. 
    
In questo elenco deve includere le azioni comuni più importanti che gli utenti di effettuare con SharePoint Online. Si noti che l'ultimo passaggio di traccia continui a OneDrive for Business, build di un confronto tra il caricamento della home page SharePoint Online (che spesso personalizzato per le aziende) e OneDrive per Business home page, ovvero raramente. Questa è una prova di base quando si tratta di un sito di SharePoint Online caricano lentamente. È possibile creare un record di questa differenza in per i test.
  
Se si è all'interno di un problema di prestazioni, molti dei passaggi solo gli stessi quando si effettuano una linea di base. Le tracce di rete importanza fondamentale, in modo che si sarà gestire *come* per sfruttare le tracce importanti successivo. 
  
Per affrontare i problemi di prestazioni, *direttamente* , è necessario avere una traccia al momento riscontrato il problema di prestazioni. È necessario che gli strumenti appropriati disponibili per raccogliere i registri ed è necessario un piano di azione, vale a dire un elenco delle azioni da intraprendere per raccogliere le informazioni di procedure che è possibile eseguire la risoluzione dei problemi. Il primo consiste nella registrare la data e l'ora del test in modo che sia possono salvare i file in una cartella che riflettono l'intervallo di tempo. Successivamente, restringere ai passaggi problema se stessi. Questi sono i passaggi esatti che verrà utilizzato per il testing. Non bisogna dimenticare i concetti di base: se il problema è solo con Outlook, assicurarsi di record che il comportamento di problema si verifica in un solo servizio di Office 365. In quanto l'ambito di questo problema aiuteranno per evidenziare un elemento che è possibile risolvere. 
  
## <a name="see-also"></a>Vedere anche

[Gestione degli endpoint di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

