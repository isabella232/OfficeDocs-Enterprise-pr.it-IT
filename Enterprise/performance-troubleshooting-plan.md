---
title: Piano di risoluzione dei problemi di prestazioni per Office 365
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 4/26/2017
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
ms.assetid: e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c
description: È necessario conoscere i passaggi da eseguire per identificare e correggere i ritardi, si blocca e un rallentamento delle prestazioni tra SharePoint Online, OneDrive for Business, Exchange Online o Skype Business online e i computer client? Prima di chiamare il supporto, in questo articolo consentono di risolvere i problemi relativi alle prestazioni di Office 365 e risolvere alcuni dei problemi più comuni.
ms.openlocfilehash: 0e588d35ff6caaa0796092bb2f964bced15f4e47
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975184"
---
# <a name="performance-troubleshooting-plan-for-office-365"></a>Piano di risoluzione dei problemi di prestazioni per Office 365

È necessario conoscere i passaggi da eseguire per identificare e correggere i ritardi, si blocca e un rallentamento delle prestazioni tra SharePoint Online, OneDrive for Business, Exchange Online o Skype Business online e i computer client? Prima di chiamare il supporto, in questo articolo consentono di risolvere i problemi relativi alle prestazioni di Office 365 e risolvere alcuni dei problemi più comuni.
  
In questo articolo viene effettivamente un piano di azione di esempio che è possibile utilizzare per acquisire dati utili relative al problema di prestazioni quando è in corso. Alcuni problemi principali sono inclusi anche in questo articolo.
    
Se ha familiarità con le prestazioni di rete e si desidera creare un piano a lungo termine per monitorare le prestazioni tra i computer client e Office 365, esaminare [le prestazioni di Office 365 ottimizzazione e risoluzione dei problemi - Admin e professionisti IT](performance-tuning-using-baselines-and-history.md).
  
## <a name="sample-performance-troubleshooting-action-plan"></a>Piano di azione sulla risoluzione dei problemi delle prestazioni di esempio

In questo piano di azione composta da due parti; fase di preparazione e una fase di registrazione. Se si dispone di un problema di prestazioni direttamente ed è necessario eseguire la raccolta dei dati, è possibile avviare immediatamente a utilizzare questo piano.
  
 **Preparare il computer client**
  
- Trovare un computer client che è possibile riprodurre il problema di prestazioni. In questo computer verrà utilizzato durante il corso di risoluzione dei problemi.
    
- Annotare i passaggi che causano il problema delle prestazioni avvenire in modo che si è pronti per quanto riguarda ora da testare.
    
- Installare gli strumenti per la raccolta e la registrazione delle informazioni:
    
  - Installare [Netmon 3.4](https://www.microsoft.com/en-us/download/details.aspx?id=4865) (oppure utilizzare uno strumento di traccia di rete equivalente). 
    
  - Installare l'edizione di base gratuita di [HTTPWatch](https://www.httpwatch.com/download/) (oppure utilizzare uno strumento di traccia di rete equivalente). 
    
  - Utilizzare il registratore di una schermata o eseguire il registratore delle operazioni (PSR.exe) provenienti da Windows Vista e versioni successive, per tenere traccia della procedura da seguire durante il test.
    
 **Registro problema delle prestazioni**
  
- Chiudere tutti i browser Internet estranei.
    
- Avviare il registratore passaggi o un altro registratore dello schermo.
    
- Avviare l'acquisizione Netmon (o lo strumento di traccia di rete).
    
- Cancellare la cache DNS nel computer client dalla riga di comando digitando ipconfig /flushdns.
    
- Avviare una nuova sessione di browser e attivare HTTPWatch.
    
- Facoltativo: Se si esegue il test Exchange Online, eseguire lo strumento Analizzatore prestazioni Client di Exchange dalla console di amministrazione di Office 365.
    
- Riprodurre i passaggi esatti che causano problemi di prestazioni.
    
- Arrestare il Netmon o traccia di altre dello strumento.
    
- Nella riga di comando eseguire una route di traccia per la sottoscrizione a Office 365 digitando il comando seguente e quindi premere INVIO:
    
    `tracert \< *subscriptionname*  \>.onmicrosoft.com` 
    
- Interrompere la registrazione di passaggi e salvare il video. Assicurarsi di includere la data e ora di acquisizione e se viene dimostrata positivo o negativo sulle prestazioni.
    
- Salvare i file di traccia. Nuovamente, è necessario includere la data e ora di acquisizione e se viene dimostrata positivo o negativo sulle prestazioni.
    
Se non si ha familiarità con l'esecuzione di strumenti illustrati in questo articolo, tenere presente che poiché Microsoft fornisce i passaggi successivo. Per gli utenti di effettuare questo tipo di acquisizione di rete, è possibile ignorare su [come raccogliere le linee di base](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines), che descrive il filtro e leggere i registri. 
  
## <a name="flush-the-dns-cache-first"></a>Svuotare la Cache DNS prima

Perché? Rimuovendo il timeout della cache DNS si sta iniziando test una situazione pulita. Deselezionando la cache si sta reimpostare il contenuto di sistema di risoluzione DNS per le voci più aggiornate. Tenere presente che uno svuotamento non rimuove le voci del file HOSTs. Se si utilizza le voci del file HOST in modo esteso, è consigliabile copiare tali voci in un file in un'altra directory e quindi svuotare il file HOST.
  
 **Svuotare la cache di sistema di risoluzione DNS**
  
1. Aprire il prompt dei comandi (entrambi **avviare** \> **eseguire** \> **cmd** o la **chiave di Windows** \> **cmd**).
    
2. Digitare il comando seguente e premere INVIO:`ipconfig /flushdns`
    
## <a name="netmon"></a>Netmon

Strumento Microsoft per il monitoraggio della rete ([Netmon](https://www.microsoft.com/download/details.aspx?id=4865)) analizza i pacchetti, ovvero traffico, che passa tra i computer nelle reti. Utilizzando Netmon con Office 365 è possibile acquisire, visualizzazione, il traffico di traccia e leggere le intestazioni dei pacchetti, identificare i dispositivi intermedi, controllare le impostazioni importanti su hardware di rete, cercare pacchetti ignorati e seguire il flusso del traffico tra i computer aziendali rete e Office 365. Poiché il corpo del traffico effettivo viene crittografato, vale a dire che (viaggia sulla porta 443 tramite TLS/SSL, è possibile leggere i file da inviare. In realtà, viene visualizzato una non filtrata traccia del percorso che accetta i pacchetti che consentono di individuare il comportamento di problema.
  
Assicurarsi che non applicare un filtro in questa fase. In realtà, eseguire i passaggi e viene illustrato il problema prima dell'interruzione di traccia e il salvataggio.
  
Dopo aver installato Netmon 3.4, aprire lo strumento ed eseguire la procedura seguente:
  
 **Eseguire una traccia Netmon e riprodurre il problema**
  
1. Sulla barra di avvio Netmon 3.4.
    
    Esistono tre riquadri nella pagina **iniziale** : **Acquisisce recenti**, **Selezionare reti**e la Guida introduttiva a Microsoft Network Monitor 3.4 **. Avviso**. Riquadro Seleziona reti inoltre si otterrà un elenco delle reti predefinito da cui è possibile acquisire. Assicurarsi che le schede di rete siano selezionate di seguito.
    
2. Fare clic su **Nuovo ritaglio** nella parte superiore della pagina **iniziale** . Aggiunge una nuova scheda accanto **avviare** scheda pagina denominata **Capture 1**.
    
    ![Interfaccia con il nuovo ritaglio, Start, utente del Nemon e arrestare i pulsanti evidenziati.](media/d4527d84-62ec-4301-82d5-e0166ff71f20.PNG)
  
3. Per acquisire un' semplice, fare clic su **Start** sulla barra degli strumenti. 
    
4. Riprodurre i passaggi che presentano un problema di prestazioni.
    
5. Fare clic su **Interrompi** \> **File** \> **Salva con nome**. Ricordarsi di fornire la data e ora al fuso orario e di segnalare se viene illustrato come non valida o buone prestazioni.
    
## <a name="httpwatch"></a>HTTPWatch

[HTTPWatch](https://www.httpwatch.com/download/) è disponibile in tariffe e un'edizione gratuita. Versione di base gratuito sono descritte tutte le informazioni che necessarie per questo test. Monitor HTTPWatch momento del caricamento di pagina e il traffico di rete direttamente dalla finestra del browser. HTTPWatch è un plug-in Internet Explorer in forma grafica descrive le prestazioni. L'analisi possono essere salvato e visualizzarli in HTTPWatch Studio. 
  
> [!NOTE]
> Se si utilizza un altro browser, ad esempio Firefox, Google Chrome, o se non è possibile installare HTTPWatch in Internet Explorer, aprire una nuova finestra del browser e premere F12 sulla tastiera. Verrà visualizzato lo strumento per gli sviluppatori popup nella parte inferiore del browser. Se si utilizza Opera, premere CTRL + MAIUSC + I per il controllo Web, fare clic sulla scheda di **rete** e il completamento della verifica indicate di seguito. Le informazioni possono essere leggermente diverse, ma vengono caricate ancora da visualizzare in millisecondi. > HTTPWatch anche è molto utile per problemi relativi ai tempi di caricamento delle pagine SharePoint Online. 
  
 **Eseguire HTTPWatch e riprodurre il problema**
  
1. HTTPWatch è un browser plug-in, in modo che lo strumento nel browser l'esposizione è leggermente diverso per ogni versione di Internet Explorer. In genere, è possibile trovare HTTPWatch sotto la barra dei comandi nel browser Internet Explorer.<br/>Se il plug-in HTTPWatch non viene visualizzata nella finestra del browser, controllo della versione del browser con fare clic su Guida \> su, o versioni successive di Internet Explorer, fare clic sul simbolo di ingranaggio e informazioni su Internet Explorer. Per avviare la barra dei **comandi** , fare clic sulla barra dei menu in Internet Explorer e fare clic su **barra dei comandi**. In passato, HTTPWatch è stati associati con i comandi e le barre di Explorer, pertanto una volta si installa, se non è immediatamente visualizzata l'icona (anche dopo il riavvio) controllare **gli strumenti**e le barre degli strumenti per l'icona. Tenere presente che è possibile personalizzare le barre degli strumenti e le opzioni possono essere aggiunte loro.<br/>
    ![Comando della barra degli strumenti Internet Explorer con l'icona HTTPWatch visualizzata.](media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)
  
2. Sulla barra di avvio HTTPWatch in una finestra del browser Internet Explorer. Verrà visualizzato ancorato alla parte inferiore della finestra del browser. Fare clic su **Record**.
    
3. Riprodurre la procedura esatta per il problema di prestazioni. Fare clic sul pulsante **Interrompi** HTTPWatch. 
    
4. **Salvare** il HTTPWatch o **inviare tramite posta elettronica**. Ricordarsi di nome del file in modo che includa informazioni su data e ora e l'indicazione del fatto l'orologio contiene una dimostrazione delle prestazioni positivo o negativo.<br/>![HTTPWatch che mostra la scheda Rete per il caricamento pagina della homepage di Office 365.](media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)<br/>
    Questa schermata è dalla versione di HTTPWatch Professional. È possibile aprire le tracce attenzione la versione di base in un computer con una versione Professional e leggere disponibili. Informazioni aggiuntive potrebbero essere disponibile dalla traccia tramite il metodo.
    
## <a name="problem-steps-recorder"></a>Registrazione azioni

Passaggi registratore o PSR.exe, consente di registrare problemi in tempo reale. È uno strumento molto utile e molto semplice da eseguire.
  
 **Eseguire passaggi di registrazione (PSR.exe) per registrare il proprio lavoro**
  
1. Utilizzare **Avvia** \> **eseguire** \> digitare **PSR.exe** \> **OK**, oppure fare clic su **Chiave Windows** \> digitare **PSR.exe** \> e quindi premere INVIO. 
    
2. Quando viene visualizzata la finestra PSR.exe piccola, fare clic su **Avvia Record** e riprodurre i passaggi riprodurre il problema di prestazioni. È possibile aggiungere commenti in base alle esigenze, fare clic su **Aggiungere commenti**.
    
3. Fare clic su **Interrompi Record** dopo avere completato i passaggi. Se il problema delle prestazioni è un pagina di rendering, attendere il rendering prima di interrompere la registrazione della pagina. 
    
4. Fare clic su **Salva**.
    
![Cattura di schermata del registratore passaggi o PSR.exe.](media/8542b0aa-a3ff-4718-8dc4-43f5521c6c34.PNG)
  
Data e ora viene registrato automaticamente. Collega il determinate di traccia Netmon e HTTPWatch nel tempo e consente la precisione di risoluzione dei problemi. Data e ora del record determinate possono mostrare che un minuto passato tra l'account di accesso e l'esplorazione, ad esempio gli URL e il rendering parziale del sito di amministrazione.
  
## <a name="read-your-traces"></a>Leggere le tracce

Non è possibile fornire agli tutto il contenuto sulla rete e la risoluzione dei problemi di prestazioni che si desidera ottenere tramite un articolo. Guida buone prestazioni ha esperienza e conoscere il funzionamento della rete ed esegue in genere. Ma è possibile eseguire l'arrotondamento l'elenco dei problemi principali e Mostra come strumenti può facilitare consente di eliminare i problemi più comuni.
  
Se si desidera rispondere competenze leggere le tracce di rete per i siti di Office 365, non esiste alcun docente migliori rispetto a creare regolarmente le tracce dei carichi di pagina e acquisire esperienza eseguirne la lettura. Ad esempio, quando possibile, caricare un servizio di Office 365 e il processo di analisi. Filtrare la traccia per il traffico DNS o FrameData per il nome del servizio che si è passati di ricerca. Analizzare la traccia per avere un'idea delle operazioni che si verificano quando viene caricato il servizio. Ciò consentirà di informazioni su quali normale caricamento della pagina dovrebbe essere simile e nel caso di risoluzione dei problemi, in particolare per quanto riguarda le prestazioni, confronto tra le tracce buone a non valida può spiegano che una quantità elevata.
  
Netmon utilizza Microsoft Intellisense nel campo filtro visualizzazione. IntelliSense o il completamento del codice intelligente, è che invece di cui si digita un periodo e vengono visualizzate tutte le opzioni disponibili in una casella di riepilogo a discesa selezione. Se, ad esempio, si è preoccupazione di adattamento della finestra TCP, è possibile trovare il modo in cui a un filtro (ad esempio `.protocol.tcp.window < 100`) in questo modo.
  
![Cattura di schermata di Netmon che indicano che il campo filtro visualizzazione utilizza intellisense.](media/75a56c11-9a60-47ee-a100-aabdfb1ba10f.PNG)
  
Netmon tracce possono contenere una grande quantità di traffico. Se non si è pratici di eseguirne la lettura, è probabile che l'utente sarà sovraccarico aprendo la traccia per la prima volta. Il primo consiste nella separare il segnale dal rumore di fondo nella traccia. Test con Office 365 e che sia il traffico che si desidera visualizzare. Se consentono di esplorare le tracce, potrebbe non essere questo elenco.
  
Il traffico tra il client e Office 365 passa tramite TLS, il che significa che il corpo del traffico verrà crittografato e non leggibili in una traccia Netmon generica. Analisi delle prestazioni non ha necessità di conoscere le specifiche per le informazioni nel pacchetto. È tuttavia molto interessati le intestazioni dei pacchetti e le informazioni in essi contenute.
  
 **Suggerimenti per ottenere una buona traccia**
  
- Verificare se il valore dell'indirizzo IPv4 o IPv6 del computer client. È possibile ottenere al prompt dei comandi digitando **IPConfig** e quindi premere INVIO. Conoscenza di questo indirizzo consentirà di identificare immediatamente se il traffico nella traccia comporta direttamente il computer client. Se non esiste un proxy noto, effettuare il ping e ottenere anche al relativo indirizzo IP. 
    
- Svuotare la cache di sistema di risoluzione DNS e, se possibile, chiudere tutti i browser ad eccezione di quello in cui si esegue il test. Se non si è in grado di eseguire questa operazione, ad esempio, se il supporto utilizza uno strumento basato su browser per visualizzare il desktop del computer client, essere pronti filtrare la traccia.
    
- In una traccia occupata, individuare il servizio Office 365 che si sta utilizzando. Se si è mai o raramente visto il traffico prima, questo è un passaggio utile per la separazione problema delle prestazioni da altri rumore di rete. Esistono alcuni modi per eseguire questa operazione. Direttamente prima di effettuare i test, è possibile utilizzare ping o PsPing all'URL del servizio specifico ( `ping outlook.office365.com` e/o `psping -4 microsoft-my.sharepoint.com:443`, per alcuni esempi). È possibile trovare anche facilmente tale PsPing in una traccia Netmon (in base al nome di processo). In questo modo si un punto di partenza alla ricerca.
    
    Se si utilizza solo traccia Netmon al momento del problema, che è necessario è troppo. Per orientare familiarità, utilizzare un filtro come `ContainsBin(FrameData, ASCII, "office")` o `ContainsBin(FrameData, ASCII, "outlook")`. È possibile registrare il numero di fotogrammi dal file di traccia. È inoltre possibile scorrere il riquadro Riepilogo cornice verso destra e cercare nella colonna ID di conversazione. Non vi è un numero indicato disponibili per l'ID di questa conversazione specifica che possono registrare e visualizzare in isolamento più avanti. Ricordarsi di rimuovere il filtro prima di applicare un altro filtro.
    
> [!TIP]
> Netmon è molto utili filtri predefiniti. Provare il pulsante "Load Filter" nella parte superiore del riquadro del filtro di **visualizzazione** . 
  
![Individuare l'IP con PSPing alla riga di comando nel computer client.](media/4c43ac67-e28e-4536-842d-7add7aa28847.PNG)
  
![Traccia Netmon dal client con lo stesso comando PSPing attraverso il filtro TCP. Flags.Syn = = 1.](media/0ae7ef7d-e003-4d01-a006-dc49bd1fcef2.PNG)
  
Acquisisci familiarità con il traffico e informazioni su come individuare le informazioni che necessarie. Ad esempio, viene illustrato come determinare i pacchetti la traccia sono il primo riferimento al servizio Office 365 in uso (ad esempio, "Outlook").
    
Tenendo in linea di Outlook Office 365 come esempio, il traffico inizia simile al seguente:
  
- Query Standard DNS e risposta DNS per outlook.office365.com con corrispondenza QueryIDs. È importante notare l'Offset tempo per questo risolvere, nonché where nel mondo del DNS globali di Office 365 invia la richiesta per la risoluzione dei nomi. In teoria, nel sistema locale come possibile, anziché a metà in tutto il mondo. (Tale operazione può essere seguita da alcuni account di accesso online il traffico DNS.)
    
- Un HTTP GET-richiesta il cui stato spostato in modo permanente (301) di report
    
- Traffico RW inclusi RW connettere le richieste e risposte di connessione. (Si tratta di Remote Winsock viene stabilita una connessione automaticamente).
    
- Conversazione SYN TCP e TCP SYN/riconoscimento. Una quantità elevata di impostazioni in questa conversazione influire sulle prestazioni del.
    
- Quindi una serie di traffico TLS:TLS che corrisponde a cui l'handshake TLS e le conversazioni certificato TLS effettuati. (Memorizza che i dati vengono crittografati tramite TLS/SSL).
    
Tutte le parti del traffico sono importanti e connessa, ma piccole parti dell'analisi contengono informazioni particolarmente importanti per quanto riguarda la risoluzione dei problemi di prestazioni, pertanto verrà posta attenzione su tali aree. Inoltre, poiché è stata effettuata sufficienti prestazioni di Office 365 risoluzione dei problemi in Microsoft per compilare un elenco di problemi comuni dieci principali, verrà posta attenzione su tali problemi e su come utilizzare gli strumenti che siamo obbligati a essi radice fuori Avanti.
  
Se non sono stati installati ed è possibile procedere, la matrice di seguito consente di utilizzare gli strumenti diverse di. Quando possibile. Vengono forniti collegamenti ai punti di installazione. L'elenco include comuni strumenti di traccia di rete come [Netmon](https://www.microsoft.com/en-us/download/details.aspx?id=4865) e [Wireshark](https://www.wireshark.org/), ma utilizzare qualsiasi strumento di traccia che si ha familiarità con, in cui sta abituati per filtrare il traffico di rete. Quando si sta eseguendo il test, tenere presenti:
  
-  *Chiudere il browser e con un solo browser in esecuzione di test* - questo consente di ridurre il traffico complessivo di acquisire. Tale scelta risulta per una traccia meno occupata. 
    
-  *Svuotare la cache di sistema di risoluzione DNS nel computer client* , che consente di una situazione pulita quando si inizia a richiedere l'acquisizione di un'analisi più lineare. 
    
## <a name="some-top-issues"></a>Alcuni problemi principali

Alcuni problemi comuni che potrebbero verificarsi e su come trovare la traccia di rete.

### <a name="tcp-windows-scaling"></a>Windows TCP scalabilità

Trovato SYN - permanenza hardware o SYN/ACK. Legacy potrebbe non essere basate su windows TCP scalabilità.  Senza windows TCP corretta delle impostazioni di ridimensionamento, il buffer di 16 bit predefinita nelle intestazioni TCP viene riempito in millisecondi.  Il traffico non può continuare a inviare fino a quando il client riceve un messaggio di conferma che i dati originali viene ricevuti, causando ritardi.

#### <a name="tools"></a>Strumenti di:

- Netmon
- Wireshark 

#### <a name="what-youre-looking-for"></a>Che cosa si sta cercando:

Cercare SYN - SYN/riconoscimento il traffico nella traccia di rete.  Utilizzare un filtro come in Netmon, `tcp.flags.syn == 1`. Questo filtro è la stessa in Wireshark.  

![Filtro Netmon o Wireshark per pacchetti Syn per entrambi gli strumenti: TCP. Flags.Syn = = 1.](media/4b9a12a1-c915-43c8-ac2f-a679d0435a29.PNG)         
Si noti che per ogni SYN esiste un numero di porta (SrcPort) origine corrispondenti in porta di destinazione (DstPort) di riconoscimento correlata (SYN/riconoscimento). 

Per visualizzare il valore di ridimensionamento di Windows che viene utilizzato per la connessione di rete, espandere innanzitutto il SYN, quindi correlate SYN/ACK.  

![Immagine che illustra come per la corrispondenza SrcPort a DstPort una traccia per ottenere l'intervallo di tempo.](media/6a4ca573-0253-4fbd-93e8-92821ee1c351.png)  

### <a name="tcp-idle-time-settings"></a>Impostazioni di tempo di inattività TCP

In passato, la maggior parte delle reti perimetrali sono configurate per le connessioni temporanee, ovvero le connessioni inattive vengono in genere terminate. Termina sessioni inattive TCP per i proxy e firewall a maggiore di 100-300 secondi. Si tratta problematico per Outlook in linea in quanto consente di creare e vengono utilizzate connessioni a lungo termine, se sono inattivi o non.  

Quando le connessioni vengono terminate dal proxy o dispositivi firewall, il client non viene informato e un tentativo di utilizzare Outlook Online comporta un client tenta, più volte, lussuosi la connessione prima di crearne uno nuovo. Blocchi di prodotto, istruzioni o un rallentamento delle prestazioni venga visualizzato nel caricamento della pagina.

#### <a name="tools"></a>Strumenti di:

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Sugli aspetti da considerare:

In Netmon, esaminare il campo Scostamento tempo per un round trip. Un round trip è il tempo tra client invia una richiesta al server e la ricezione nuovamente una risposta. Controllare tra il Client e il punto di uscita (ad esempio Client -\> Proxy), o del Client a Office 365 (Client -\> Office 365). È possibile visualizzare questo in molti altri tipi di pacchetti. 

Ad esempio, il filtro nella Netmon sia simile `.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12`, o Wireshark, `ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12`.  

> [!TIP]
> Non è possibile sapere se l'indirizzo IP nella traccia appartiene al server DNS? Provare a cercare nella riga di comando. Fare clic su **Start** \> **eseguire** \> e digitare **cmd**oppure premere **Il tasto Windows** \> e digitare **cmd**. Al prompt dei comandi, digitare `nslookup <the IP address from the network trace>`. Per eseguire il test, utilizzare nslookup indirizzo IP del computer. > Per visualizzare un elenco di intervalli IP di Microsoft, vedere [Office 365 URL e intervalli di indirizzi IP](https://technet.microsoft.com/en-us/library/hh373144.aspx). 

Se si verifica un problema, si aspettano lungo tempo Scosta venga visualizzato, in questo caso (Outlook in linea), in particolare nei pacchetti TLS:TLS che mostra il passaggio dei dati delle applicazioni (ad esempio Netmon è possibile trovare i pacchetti di dati dell'applicazione tramite `.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"`). Verrà visualizzato un avanzamento uniforme nel tempo tra la sessione. Se viene visualizzata lunghi ritardi quando viene aggiornata la linea di Outlook, ciò potrebbe essere causato da un elevato grado di ripristino in corso di invio. 

### <a name="latencyround-trip-time"></a>Latenza/Round attivarsi ora 

Latenza è una misura che può cambiare maggiormente in base al numero di variabili, tale aggiornamento dispositivi di permanenza, aggiunta di un numero elevato di utenti a una rete e la percentuale della larghezza di banda complessiva utilizzata dalle altre attività di una connessione di rete. 

Calcolatori di larghezza di banda per Office 365 sono disponibili in questa pagina [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](network-planning-and-performance.md) .  

Necessario per calcolare la velocità di connessione o della larghezza di banda della connessione ISP? Provare a eseguire questo sito (o siti come viene): [Sito ufficiale Speedtest](https://www.speedtest.net/)ed [esecuzione Pingtest](http://www.pingtest.net/).

#### <a name="tools"></a>Strumenti di:

- Ping
- PsPing
- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Sugli aspetti da considerare:

Per tenere traccia latenza in una traccia, saranno utili di dover registrato l'indirizzo IP del computer client e l'indirizzo IP del server DNS in Office 365. Si tratta allo scopo di filtro di traccia più semplice. Se ci si connette tramite un proxy, è necessario l'indirizzo IP del computer client, l'indirizzo IP proxy/in uscita e l'indirizzo IP di Office 365 DNS, che semplificano il lavoro.  

Una richiesta ping al outlook.office365.com indicherà il nome del centro dati che riceve la richiesta, anche se il comando ping *potrebbe* non essere in grado di connettersi per inviare il marchio consecutivi pacchetti ICMP. Se si utilizza PsPing (uno strumento gratuito per il download) e specifica la porta (443) e magari per l'utilizzo di IPv4 (-4) si otterrà un round-trip-tempo medio di pacchetti inviati. Questo metodo funziona questa per altro URL in servizi di Office 365, come `psping -4 yourSite.sharepoint.com:443`. In realtà, è possibile specificare un numero di ping per ottenere un campione di dimensioni maggiore di tentare la media, simile: `psping -4 -n 20 yourSite-my.sharepoint.com:443`.  

> [!NOTE]
> PsPing non invia pacchetti ICMP. Esegue il ping con pacchetti TCP su una porta specifica, in modo che è possibile utilizzare uno che dovrebbe per essere aperto. In Office 365, che utilizza TLS/SSL, provare ad associare porta: 443 per le PsPing.

![Schermata che mostra un comando ping risoluzione outlook.office365.com e un PSPing con 443 eseguono la stessa, ma anche reporting un RTT Media 6.5ms.](media/c64339f2-2c96-45b8-b168-c2a060430266.PNG)        

Se è stato caricato la pagina di Office 365 con prestazioni lenta durante l'esecuzione di una traccia di rete, è consigliabile filtrare una traccia Netmon o Wireshark per `DNS`. Questa è una gli indirizzi IP che stiamo cercando.  

Di seguito sono i passaggi da eseguire per filtrare i Netmon per acquisire l'indirizzo IP (e dare uno sguardo al DNS latenza). In questo esempio utilizza outlook.office365.com, ma è inoltre possibile utilizzare l'URL di un tenant di SharePoint Online (hithere.sharepoint.com, ad esempio).  

1. Eseguire il ping URL `ping outlook.office365.com` e nei risultati di registrare il nome e indirizzo IP del server DNS, il comando ping è stato inviato a. 
2. Rete individuare apertura della pagina o eseguire l'azione che permette di utilizzare i problemi di prestazioni, oppure, se è visualizzata un'elevata latenza ping, rete. 
3. Aprire la traccia in Netmon e filtro per il servizio DNS (questo filtro anche Wireshark viene utilizzato, ma è riservato a caso `-- dns`). Poiché si conosce il nome del server DNS dal ping è possibile inoltre filtrare più velocemente in Netmon simile alla seguente: `DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")` , quali simile a quello che nel sistema dns Wireshark e cornice contiene "namnorthwest".<br/>Aprire il pacchetto di risposta e, nella finestra Dettagli dei Frame di Netmon, fare clic su DNS espandere per ulteriori informazioni. Le informazioni DNS che consente di individuare l'indirizzo IP del server DNS che della richiesta non appena si in Office 365, è necessario l'indirizzo IP per il passaggio successivo (strumento PsPing). Rimuovere il filtro pulsante destro del mouse risposta DNS riepilogando cornice del Netmon \> trova conversazioni \> DNS per visualizzare le Query DNS e risposta side-by-side. 
4. Netmon, anche noti nella colonna Scostamento tempo tra le richieste DNS e le risposte. Il passaggio successivo per installare e utilizzare [PsPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx) strumento è disponibile in molto utile, poiché ICMP spesso è bloccata nel firewall e poiché PsPing edito tiene traccia della latenza in millisecondi. PsPing viene completata una connessione TCP alla porta (nel nostro maiuscole aprire la porta 443) e indirizzo. 
5. Installare PsPing. 
6. Aprire un prompt dei comandi (avviare \> eseguire \> digitare cmd o il tasto Windows \> digitare cmd) e passare alla directory in cui è installato PsPing per eseguire il comando PsPing directory. Negli esempi è possibile visualizzare che dopo aver apportato una 'Perf' della cartella principale del C. È possibile eseguire la stessa per l'accesso rapido. 
7. Digitare il comando in modo che si sta effettuando la PsPing sull'indirizzo IP del server di Office 365 DNS dalla traccia Netmon precedente, ricordarsi di aggiungere il numero di porta. <br/>In altre parole, `psping -n 20 132.245.24.82:445`. Per fornire un campionamento di 20 ping e la latenza media al termine del PsPing. 

Se prevede di Office 365 tramite un server proxy, la procedura è leggermente diversa. È necessario prima PsPing al server proxy per ottenere un valore di latenza media in millisecondi a proxy/in uscita e viceversa, e quindi uno eseguire PsPing nel proxy o in un computer con una connessione diretta a Internet per ottenere il valore mancano (quello a Office 365 e viceversa).  

Se si sceglie di eseguire PsPing dal proxy, sarà necessario due valori millisecondo: computer Client al server proxy o punto di uscita e server proxy per Office 365. E termine. Registrazione, i valori, comunque.  

Se si esegue PsPing in un altro computer client con una connessione diretta a Internet, vale a dire, senza un proxy, sarà necessario due valori millisecondo: computer Client al server proxy o punto di uscita e i computer client a Office 365. In questo caso, sottrarre il valore del computer client al proxy server o in uscita al punto da quello del computer client a Office 365 e sarà necessario numeri RTT dal computer client e il punto di uscita o server proxy e dal proxy server o in uscita scegliere distaccate CE 365. 

Tuttavia, se è possibile trovare un computer client nel percorso sono connessi direttamente o ignora il proxy, potrebbe scegliere di verificare se il problema viene riprodotto vi innanzitutto e testare utilizzarlo, in seguito. 

Latenza, come indicato in una traccia Netmon tali millisecondi aggiuntivi possono aggiungere verso l'alto, se sono presenti un numero sufficiente di essi in una sessione specifica.  

![Latenza generale in Network Monitor, con la colonna dell'intervallo di tempo predefinita di Network Monitor aggiunta al riepilogo dei frame.](media/7ad17380-8527-4bc2-9b9b-6310cf19ba6b.PNG)

> [!NOTE]
> L'indirizzo IP può essere diverso da quello gli indirizzi IP illustrato di seguito, ad esempio, che il ping può restituire simile ulteriori 157.56.0.0/16 o un intervallo simile. Per un elenco di intervalli utilizzati da Office 365, vedere [Office 365 URL e intervalli di indirizzi IP](https://technet.microsoft.com/en-us/library/hh373144.aspx). 

Se si desidera eseguire la ricerca, ad esempio, 132.245, ricordarsi di espandere tutti i nodi (viene visualizzato un pulsante nella parte superiore per l'oggetto).

### <a name="proxy-authentication"></a>Autenticazione proxy

Si applica solo a un utente se si prevede un server proxy. In caso contrario, è possibile ignorare la procedura seguente. Quando si utilizza in modo corretto, autenticazione proxy dovrebbe avvenire in millisecondi, in modo coerente. Si non devono vedere prestazioni errato intermittente durante i periodi di utilizzo (ad esempio).  

Se l'autenticazione Proxy, ogni volta che si crea una nuova connessione TCP a Office 365 per ottenere informazioni, è necessario passare attraverso un processo di autenticazione in background. Pertanto, ad esempio, quando si passa dal calendario di posta elettronica in Outlook Online, è verranno autenticati. E in SharePoint Online, se viene visualizzata una pagina multimediale o i dati di più siti o le sedi, verrà l'autenticazione per ogni connessione TCP diversi che è necessaria per il rendering dei dati.  

In Outlook Online, possono verificarsi tempi di caricamento lenta ogni volta che si passa dal calendario e delle cassette postali o lenta pagina viene caricata in SharePoint Online. Tuttavia, esistono altri sintomi non elencate di seguito. 

Autenticazione proxy è un'impostazione sul server proxy in uscita. Se causa problemi di prestazioni con Office 365, è necessario consultare il team di rete.  

#### <a name="tool"></a>Strumento: 

- Netmon
- Wireshark 

#### <a name="what-to-look-for"></a>Sugli aspetti da considerare:

Proxy autenticazione viene eseguita ogni volta che una nuova sessione TCP deve caricare un, in genere per richiedere il file o informazioni dal server o per fornire informazioni. Ad esempio, si può vedere authentication proxy intorno a richieste HTTP POST o HTTP GET. Se si desidera visualizzare le cornici di cui si eseguono l'autenticazione richieste nella traccia, aggiungere la colonna 'NTLMSSP riepilogo' Netmon e filtra `.property.NTLMSSPSummary`. Per verificare il tempo in corso l'autenticazione, aggiungere la colonna dell'intervallo di tempo. 

Per aggiungere una colonna a Netmon: 
1. Pulsante destro del mouse su una colonna, ad esempio descrizione. 
2. Fare clic su Scegli colonne. 
3. Individuare NTLMSSP riepilogo e intervallo di tempo nell'elenco e fare clic su Aggiungi. 
4. Spostare le nuove colonne nella posizione corretta prima o dietro nella colonna Descrizione in modo che è possibile leggerli side-by-side.
5. Fare clic su OK. 

Anche se non si aggiunge la colonna, il filtro Netmon funzionerà. Ma la risoluzione dei problemi è molto più semplice è possibile visualizzare la fase di autenticazione è attiva. 

Quando è presente la ricerca per le istanze dell'autenticazione Proxy, assicurarsi di esaminare tutti i frame in caso di una richiesta NTLM oppure un messaggio di eseguire l'autenticazione. Se necessario, fare parte specifica del traffico e trova conversazioni \> TCP. Tenere presente i valori di ora Delta le conversazioni. 

![Netmon traccia che illustra autenticazione proxy, filtrato in base alla conversazione.](media/b640f176-0a52-4bbb-972e-60fb3d6aece2.PNG)        

Un secondo quattro un ritardo nell'autenticazione proxy come indicato in Wireshark. Nella colonna **delta ora dal frame visualizzato precedente** è stata effettuata tramite il pulsante destro del campo lo stesso nome nei dettagli del frame e selezionando Aggiungi come colonna.<br/> ![In Wireshark, nella colonna 'Delta ora dalla precedente frame visualizzato' può essere apportata tramite il pulsante destro del campo lo stesso nome nei dettagli del frame e selezionando Aggiungi come colonna.](media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)        

### <a name="dns-performance"></a>Prestazioni del DNS

Nome soluzione è più adatta e più rapidamente quando ha luogo più vicino paese del client possibile. 

Se la risoluzione dei nomi DNS è in corso d'oltremare, è possibile aggiungere secondi per i carichi di pagina. In teoria, la risoluzione dei nomi effetti in 100 ms. Se non, è necessario effettuare ulteriori indagini. 

> [!TIP]
> In caso di dubbi come funziona la connettività dei Client in Office 365 Esaminare il documento di riferimento di connettività Client [di seguito](https://technet.microsoft.com/en-us/library/dn741250.aspx).           

#### <a name="tools"></a>Strumenti di: 

- Netmon
- Wireshark
- PsPing

#### <a name="what-to-look-for"></a>Sugli aspetti da considerare:
Analisi delle prestazioni DNS è in genere un altro processo per l'analisi della rete. Tuttavia, è anche utile in stranieri, o l'uscita, causando PsPing. 

Il traffico DNS si basa su TCP e UDP richieste e risposte chiaramente contrassegnate con un ID utili per identificare una richiesta specifica con le specifiche di response. Verrà visualizzato DNS traffico quando, ad esempio, SharePoint Online utilizza un nome di rete o un URL in una pagina web. Come regola, la maggior parte di tale traffico, ad eccezione durante il trasferimento delle aree, viene eseguito su UDP. 

In Netmon e Wireshark, il filtro più semplice che consente di esaminare il traffico DNS è semplicemente `dns`. Assicurarsi di utilizzare lettere minuscole quando si specifica il filtro. Ricordarsi di scaricare la cache di sistema di risoluzione DNS prima di iniziare a riprodurre il problema nei computer client. Ad esempio, se si dispone di un caricamento della pagina lenta SharePoint Online per la Home page, deve chiudere tutti i browser, aprire un nuovo browser, avviare l'analisi, svuotare la cache di sistema di risoluzione DNS e passare al sito di SharePoint Online. Una volta che viene risolto l'intera pagina, è necessario arrestare e salvare la traccia.

![Un filtro di base per DNS in Netmon è DNS.](media/1bebc118-ca13-45f3-803f-ab73e7af401d.png)

Si desidera esaminare il tempo di scostamento in seguito. E può essere utile aggiungere la colonna **dell'Intervallo di tempo** per Netmon che è possibile effettuare completando la procedura seguente: 
1. Pulsante destro del mouse su una colonna, ad esempio descrizione. 
2. Fare clic su Scegli colonne. 
3. Individuare l'intervallo di tempo nell'elenco e fare clic su Aggiungi. 
4. Spostare la nuova colonna nella posizione corretta prima o dietro nella colonna Descrizione in modo che è possibile leggerli side-by-side.
5. Fare clic su OK. 

Se una query di interesse, prendere in considerazione isolamento facendo clic su query nel riquadro dei dettagli frame, scegliere **Trova conversazioni** \> **DNS**. Si noti che il pannello di rete conversazioni rimanda diritto a partecipare alla conversazione specifico nel Registro di traffico UDP. 

![Una traccia Netmon di carico Outlook Online filtrato in base a DNS e l'utilizzo di trovare le conversazioni, quindi DNS restringere i risultati.](media/763cf20e-7b48-4a37-9449-c9978cfe118b.PNG)        

In Wireshark è possibile rendere una colonna per volta DNS. Eseguire la traccia (o si apre una traccia) in Wireshark e filter by `dns`, o più ha `dns.time`. Fare clic su tutte le query DNS e, nel riquadro di visualizzazione dei dettagli espandere il `Domain Name System (response)` dettagli. Verrà visualizzato un campo per volta (ad esempio ` [Time: 0.001111100 seconds] `. Questa volta pulsante destro del mouse e selezionare **Applica come colonna**. Si avrà così una colonna di **tempo** per l'ordinamento più velocemente di traccia. Fare clic su nuova colonna per l'ordinamento decrescente i valori per verificare che DNS chiamata hanno impiegato più a lungo per risolvere. 

[Una ricerca di SharePoint Online filtrata in Wireshark da (tutto minuscolo) dns.time, con il tempo dei dettagli realizzato in una colonna e classificato in ordine crescente.](media/1439dcc2-12ff-4ee2-9ef3-1484cf79c384.PNG)

Se si desidera eseguire un'ulteriore analisi del tempo di risoluzione DNS, provare a PsPing contro la porta DNS utilizzata da TCP (ad esempio `psping <IP address of DNS server>:53`). È visualizzato un problema di prestazioni? In tal caso, il problema è più probabilmente una più ampia rete emettere rispetto a un problema di specifiche dell'applicazione DNS sta lavorare a tale soluzione. È inoltre pena, ricordare, che un comando ping per outlook.office365.com segnala la cui risoluzione dei nomi DNS per Outlook Online è in corso (ad esempio outlook namnorthwest.office365.com).<br/> Se il problema sembra da DNS specifici, potrebbe essere necessario contattare il reparto IT per osservare le configurazioni DNS e inoltro DNS per ulteriori informazioni su questo argomento. 

### <a name="proxy-scalability"></a>Scalabilità proxy

Servizi, ad esempio Outlook Online in Office 365 concedono client più connessioni a lungo termine. Pertanto, ogni utente può utilizzare più connessioni che richiedono una maggiore durata.  

> [!TIP]
> È necessario pianificare per l'utilizzo della larghezza di banda dal momento che si sta per aggiungere molti utenti a Office 365? Provare a [pianificare l'utilizzo di Internet della larghezza di banda per Office 365](https://technet.microsoft.com/en-us/library/hh852542.aspx). Calcolatori di larghezza di banda disponibili sono disponibili.

#### <a name="tool"></a>Strumento:
 
Matematiche  

#### <a name="what-to-look-for"></a>Sugli aspetti da considerare: 

Non è disponibile l'analisi della rete o strumento di risoluzione dei problemi specifici al seguente. In realtà, questo si basa i calcoli di larghezza di banda assegnato limitazioni e ad altre variabili.  

### <a name="tcp-max-segment-size"></a>Dimensione massima segmento TCP

Trovato SYN - SYN/ACK.  Eseguire questo controllo in qualsiasi traccia di rete di prestazioni, è consigliabile per garantire che i pacchetti TCP siano configurati per eseguire la quantità massima di dati possibili. 

L'obiettivo è visualizzare MSS di 1460 byte per la trasmissione di dati. Se si è controllato da un proxy o se si utilizza un NAT, ricordarsi di eseguire questo test dal client al proxy/uscita/NAT e dal proxy/uscita/NAT a Office 365 per ottenere risultati ottimali! Si tratta di diverse sessioni TCP.

#### <a name="tool"></a>Strumento: 

Netmon

#### <a name="what-to-look-for"></a>Sugli aspetti da considerare:

TCP Max segmento dimensione MSS () è un altro parametro dell'handshake tre elementi nella traccia di rete, che indica che sono disponibili i dati che necessari in SYN - pacchetto di SYN/riconoscimento. MSS è piuttosto semplice visualizzare. 

Aprire qualsiasi traccia di rete prestazioni avere e trovare la connessione che si desidera conoscere o che illustra i problemi di prestazioni. 

> [!NOTE]
> Se si sta visualizzando una traccia e sai dove trovare il traffico pertinenti alla conversazione, filtrare per l'IP del Client o l'IP del server proxy e/o punto di uscita. Passare direttamente, è necessario eseguire il ping l'URL che si sta testando per l'indirizzo IP di Office 365 nella traccia e filtro da essa. 

Osservando la traccia usata? Provare a utilizzare i filtri per orientare personalmente. In Netmon, eseguire una ricerca in base all'URL, ad esempio `Containsbin(framedata, ascii, "sphybridExample")`, prendere nota del numero di frame. 

In Wireshark utilizzare simile `frame contains "sphybridExample"`. Se si nota che aver trovato il traffico remoto Winsock (RW) (può essere visualizzato come [PSH, riconoscimento] Wireshark), tenere presente che si connetta RW può essere visualizzato a breve prima pertinenti SYN - SYN/ACK, come illustrato in precedenza. 

A questo punto è possibile registrare il numero di fotogrammi, eliminare il filtro, fare clic su tutto il traffico nella finestra della rete conversazioni nel Netmon paragonare la SYN più vicino. 

È importante se non si riceve una qualsiasi delle informazioni di indirizzo IP al momento dell'analisi, individuare l'URL nella traccia (parte di `sphybridExample-my.sharepoint.com`, ad esempio), per ottenere gli indirizzi IP da filtrare. 

Individuare la connessione di traccia che si desidera visualizzare. È possibile eseguire questa analizzando una traccia, filtrando in base agli indirizzi IP oppure selezionando specifica gli ID di conversazione utilizzando la finestra di rete conversazioni in Netmon. Dopo aver individuato il pacchetto SYN, espandere TCP (in Netmon) o Transmission Control Protocol (in Wireshark) nel riquadro dei dettagli dei Frame. Espandere MaxSegementSize e le opzioni di TCP. Individuare la cornice SYN riconoscimento correlate ed espandere opzioni TCP e MaxSegmentSize. Il minore dei due valori è la dimensione massima di segmento. In questa figura, è possibile avvalersi della colonna incorporata Netmon chiamato TCP risolvere i problemi.  

![Traccia di rete filtrata Netmon con le colonne predefinite.](media/e073df13-71f8-497a-83b4-bb9f70bd9833.PNG)

La colonna predefinita è nella parte superiore del riquadro **Dei dettagli dei Frame** . (Per tornare alla visualizzazione normale, fare nuovamente clic su colonne e quindi scegliere fuso orario.) 

![Dove trovare l'elenco a discesa delle colonne per l'opzione di risoluzione dei problemi di TCP (nella parte superiore del riepilogo dei frame).](media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)           
Ecco una traccia filtrata in Wireshark. Non esiste un filtro specifico del valore MSS ( `tcp.options.mss`). Le cornici di SYN, SYN/riconoscimento, handshake riconoscimento collegate nella parte inferiore della Wireshark equivale a dettagli dei Frame (cornice così riconoscimento 47, collegamenti a 46 SYN/riconoscimento, collegamenti a SYN 43) per facilitare questo tipo di lavoro. 

![Traccia filtrata in Wireshark da tcp.options.mss per Max segmento dimensione MSS ().](media/51e278db-801b-48bc-9b68-87cf92f03fd6.PNG)         
Se si desidera controllare riconoscimento selettivo (argomento successivo di questa matrice), non chiudere la traccia!

### <a name="selective-acknowledgment"></a>Riconoscimento selettivo

Trovato SYN - SYN/ACK. devono essere presentate come consentiti in SYN e SYN/ACK. selettiva acknowledgement (SACK) consentano più fluide invii dei dati quando un pacchetto o pacchetti smarriti. Dispositivi è possono disattivare questa funzionalità, può influire negativamente sulle prestazioni. 

Se si è controllato da un proxy o se si utilizza un NAT, ricordarsi di eseguire questo test dal client al proxy/uscita/NAT e dal proxy/uscita/NAT a Office 365 per ottenere risultati ottimali! Si tratta di diverse sessioni TCP.

#### <a name="tool"></a>Strumento: 

Netmon 

#### <a name="what-to-look-for"></a>Sugli aspetti da considerare:

Messaggio di conferma selettiva (SACK) è un altro parametro nell'handshake SYN SYN/riconoscimento. È possibile filtrare la traccia per SYN - SYN/riconoscimento molti modi. 

Individuare la connessione di traccia che si è interessati visualizzando sia grazie alla scansione traccia, in base agli indirizzi IP o facendo clic su un ID di conversazione utilizzando la finestra di rete conversazioni in Netmon il filtro. Dopo aver individuato il pacchetto SYN, espandere TCP in Netmon o Transmission Control Protocol in Wireshark nella sezione dettagli dei Frame. Espandere opzioni TCP e quindi SACK. Individuare la cornice SYN riconoscimento correlata ed espandere opzioni TCP e il relativo campo SACK. Rendere che SACK è autorizzato SYN sia SYN/ACK. Di seguito sono valori SACK come indicato in Netmon e Wireshark.

![Selettiva acknowledgement (SACK) in Netmon come risultato di tcp.flags.syn = = 1.](media/216f556f-5031-4ed2-b066-a0d9b3251fa2.PNG)           <br/> ![SACK come visualizzato in Wireshark con il filtro tcp.flags.syn == 1.](media/0a6e26e5-43dc-403b-adc9-3349a55f4e4b.PNG)        

### <a name="dns-geolocation"></a>Georilevazione DNS 

Qualora in tutto il mondo di Office 365 tentare di risolvere il DNS avvalersi gli effetti della velocità di connessione. 

In Outlook Online, una volta completata la prima ricerca DNS, la posizione di tale DNS verrà utilizzata per la connessione al datacenter più vicino. L'utente verrà connesso a un server accesso client in linea di Outlook, che utilizzerà la rete backbone per la connessione al datacenter (dC) cui sono archiviati i dati. Si tratta più veloce.

Se l'accesso a SharePoint Online, un utente in viaggio estero verrà indirizzato ai loro datacenter attivo, ovvero il controller di dominio la cui posizione si basa sul proprio tenant di SharePoint Online della home page di base (questa operazione, un controller di dominio negli Stati Uniti se l'utente se basate su USA).  <br/>  Lync online include nodi attivi in più di un controller di dominio alla volta. Quando sono richieste inviate per Lync online le istanze, Microsoft DNS verrà determinare dove nel mondo la richiesta proviene da e restituire gli indirizzi IP del controller di dominio regionale più vicino in Lync online è attivo. 

> [!TIP]
> Necessario ottenere maggiori informazioni su come i client si connettono a Office 365? Esaminare l'articolo di riferimento di [Connettività dei Client](https://technet.microsoft.com/en-us/library/dn741250.aspx) (e il relativo grafica utile).           
#### <a name="tools"></a>Strumenti di:

- Ping
- PsPing

#### <a name="what-to-look-for"></a>Sugli aspetti da considerare:

Le richieste per la risoluzione dei nomi di server DNS del client ai server DNS Microsoft devono nella maggior parte dei risultati casi nel sistema DNS Microsoft restituendo l'indirizzo IP di un datacenter internazionale (dC). Cosa significa questo automaticamente? Se la sede centrale sono Bangalore, India, ma si è in viaggio negli Stati Uniti, quando il browser in uso esegue una richiesta per Outlook in linea, i server DNS Microsoft devono trasferito è indirizzi IP datacenter negli Stati Uniti - un datacenter internazionale. Se è necessario posta da Outlook, che i dati verranno attraversare rete backbone rapido di Microsoft tra i Data Center.

DNS funziona più rapida quando la risoluzione dei nomi viene eseguita il più vicino possibile percorso dell'utente possibile. Se si è in Europa, si desidera accedere al DNS Microsoft in Europa e (dovrebbe) in relazione ai datacenter in Europa. Prestazioni da un client in Europa passando a un datacenter in America e DNS sarà più lenta.

Eseguire lo strumento Ping per outlook.office365.com per determinare dove nel mondo richiesta DNS viene instradata. Se si è in Europa, è necessario visualizzare una risposta da un'operazione di outlook emeawest.office365.com. America, probabilmente simile namnorthwest.office365.com di outlook. 

Aprire il prompt dei comandi nel computer client (tramite Start \> eseguire \> cmd o la chiave di Windows \> digitare cmd). Digitare ping outlook.office365.com e premere INVIO. Ricordarsi di specificare -4 Se si desidera specificare per eseguire il ping mediante IPv4. Si potrebbe non riuscire ottenere una risposta da pacchetti ICMP, ma è consigliabile visualizzare il nome del DNS a cui è stata instradata la richiesta. Se si desidera visualizzare i numeri di latenza per la connessione di prova PsPing all'indirizzo IP del server in cui viene restituito dalla ping.  

![Ping di outlook.office365.com che mostra la risoluzione in outlook-namnorthwest.](media/06c944d5-6159-43ec-aa31-757770695e8b.PNG)           
![PSPing all'indirizzo IP restituito dal ping a outlook.office365.com che mostra la latenza media di 28 millisecondo.](media/f2b25a75-1a87-4479-b8a7-fa4375683507.PNG)           
### <a name="office-365-application-troubleshooting"></a>Risoluzione dei problemi dell'applicazione di Office 365

#### <a name="tools"></a>Strumenti di: 

- Netmon
- HTTPWatch
- Console F12 nel browser

È non vengono trattati gli strumenti utilizzati nella risoluzione dei problemi specifici dell'applicazione in questo articolo specifiche della rete. Consente di individuare risorse, ma è *possibile* utilizzare [questa pagina](https://support.office.com/en-us/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848).
   
## <a name="related-topics"></a>Argomenti correlati

[Gestione degli endpoint di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Domande frequenti sugli endpoint di Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  

