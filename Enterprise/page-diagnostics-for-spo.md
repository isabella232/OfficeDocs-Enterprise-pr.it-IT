---
title: Utilizzare lo strumento di diagnostica delle pagine per SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- SPO160
- MOE150
- BSA160
ms.assetid: dbab2593-dc6a-40f7-adfe-031b9baa620f
description: Utilizzare lo strumento page Diagnostics for SharePoint per analizzare le pagine classiche rispetto alle procedure consigliate per SharePoint Online.
ms.openlocfilehash: a188b5dbe52a92cd536ef7145534288345b74c22
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069512"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a>Utilizzare lo strumento di diagnostica delle pagine per SharePoint Online

In questo articolo viene descritto come utilizzare lo strumento di diagnostica della pagina per analizzare le pagine e le pagine di pubblicazione classiche nei siti del team classico, in base a un sottoinsieme di procedure consigliate in **SharePoint Online**. 
  
Non è possibile utilizzare reti CDN per i siti del team che non dispongono della pubblicazione abilitata, ma sono applicabili tutte le regole restanti. La pubblicazione aggiunge un sovraccarico aggiuntivo in modo che non venga attivata la pubblicazione solo per ottenere la funzionalità della rete CDN, in quanto inciderà negativamente sui tempi di caricamento delle pagine.

Tieni **presente che è stata rilasciata la versione v 1.05 quindi aggiorna l'estensione se l'hai già installato**. Se non si è sicuri di quale versione fare, fare clic sul collegamento "informazioni" per verificarla.
  
> [!IMPORTANT]
> Lo strumento di diagnostica della pagina non verrà eseguito su raccolte documenti o pagine di sistema, in quanto lo strumento è stato creato per esaminare le pagine del sito di SharePoint. Una pagina di *AllItems. aspx* è una pagina di sistema. Se si tenta di eseguire lo strumento in una pagina di sistema, verrà visualizzato un messaggio che indica che "questa applicazione deve essere eseguita solo nelle pagine di SharePoint". <br/> ![Deve essere eseguito in una pagina di SharePoint](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)<br/>Non si tratta di un errore nello strumento poiché non è presente alcun valore per la valutazione di raccolte o pagine di sistema. Passare a una pagina di SharePoint non di sistema per utilizzare lo strumento. Se si verifica questa situazione in una pagina di SharePoint, verificare che il MasterPage, come abbiamo visto i clienti, rimuovere i metatag di SharePoint e quindi la pagina non è più una pagina di SharePoint. Se si desidera inviare commenti e suggerimenti sullo strumento, fare clic sulla scheda informazioni e seguire il [collegamento Invia commenti e suggerimenti](https://go.microsoft.com/fwlink/?linkid=874109). 
  
## <a name="install-the-page-diagnostic-tool"></a>Installare lo strumento di diagnostica della pagina

> [!IMPORTANT]
> Microsoft non legge i dati o i siti Web visitati e non acquisisce informazioni personali, il sito Web o le informazioni di download con questo strumento. Le uniche informazioni registrate dallo strumento sono il nome del tenant, il conteggio delle regole e se l'opzione di registrazione del supporto è stata utilizzata al momento dell'esecuzione dello strumento. Queste informazioni consentono a Microsoft di analizzare quali sfide sono state sperimentate dai clienti e di garantire che la funzionalità di registrazione del supporto non venga utilizzata in modo improprio.

1. Utilizzando un browser Chrome, aprire il [collegamento](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) direttamente allo strumento oppure aprire la ricerca nel webstore del [browser Chrome](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) e installare l'estensione del browser. Leggere i criteri di privacy degli utenti disponibili nella pagina di descrizione dell'archivio. Quando si aggiunge lo strumento al browser, verrà visualizzato il seguente avviso di autorizzazione.<br/>![Autorizzazioni per l'Archivio Chrome](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)<br/>   Questo avviso è sul posto perché una pagina può contenere contenuto proveniente da percorsi esterni a SharePoint a seconda delle web part e delle personalizzazioni presenti nella pagina. Questo significa che nello strumento verranno lette le richieste e le risposte quando si fa clic sul pulsante Start e solo per la scheda attiva di SharePoint in cui è in esecuzione lo strumento. Tali informazioni vengono acquisite localmente dal Web browser ed è possibile accedervi tramite il collegamento Esporta in JSON nello strumento. **Le informazioni non vengono inviate o acquisite da Microsoft.** (Lo strumento rispetta l'informativa sulla privacy di Microsoft accessibile [qui](https://go.microsoft.com/fwlink/p/?linkid=857875)).<br/><br/>La funzionalità "Esporta in JSON" nello strumento è anche il motivo per cui è necessaria l'autorizzazione "Gestisci i download". Seguire le linee guida sulla privacy della propria azienda prima di condividere il file JSON all'esterno dell'organizzazione, in quanto i risultati contengono URL e possono essere classificati come PII (informazioni di identificazione personale).
    
2. (Facoltativo) Se si desidera utilizzare lo strumento in modalità Chrome incognito, passare all'interno e fare clic su **Consenti in incognito**.
    
3. Passare alla pagina di pubblicazione classica di SharePoint in SharePoint Online che si desidera esaminare. È stato consentito il "caricamento ritardato" degli elementi nelle pagine; di conseguenza, lo **strumento non si arresterà automaticamente**. Se si desidera interrompere la raccolta, è possibile fare **** clic su Interrompi. In base alla progettazione, è possibile soddisfare tutti gli scenari di caricamento delle pagine. Prima di fare **** clic su Interrompi, verificare che i dati di traccia di rete siano stati completati. In caso contrario, si avrà una traccia parziale. Inoltre, lo strumento è un'estensione del browser e l'apertura di più schede o finestre consentirà l'esecuzione di una sola istanza attiva dello strumento contemporaneamente. Si tratta di una limitazione delle estensioni nel browser. 
  
4. Fare clic sul logo dell'estensione ![Diagnostica pagina per il logo di SharePoint](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) per caricare lo strumento e viene visualizzata la finestra popup di estensione seguente:<br/> ![Popup dello strumento di diagnostica delle pagine](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)<br/>Operazioni di avvio e arresto seguire il concetto di base di quando si fa clic su Avvia la pagina verrà ricaricata e inizierà la raccolta.

Leggere le sezioni seguenti per ulteriori informazioni sui dati forniti nello strumento.

## <a name="what-youll-see-in-the-page-diagnostics-tool"></a>Cosa verrà visualizzato nello strumento di diagnostica delle pagine
    
1. Il collegamento **About** fornirà indicazioni generali e dettagli relativi allo strumento, incluso un collegamento a questo articolo. Include inoltre un collegamento diretto ai consigli sulle prestazioni di SharePoint, un avviso di terze parti e un'opzione per fornire commenti e suggerimenti sullo strumento. 
    
2. L' **ID correlazione, SPRequestDuration, SPIISLatency**, il **tempo di caricamento delle pagine**e i dettagli **URL** sono informativi e possono essere utilizzati per alcuni scopi. 
    
  - **CorrelationId** è un elemento importante quando si lavora con i team di supporto Microsoft in quanto consente di estrarre dati diagnostici aggiuntivi. 
    
  - **SPRequestDuration** è il tempo del server necessario per elaborare la pagina. Se questo tempo è lungo, non significa necessariamente che il server è stato eseguito male, ma può anche riflettere il numero di chiamate e carico spinto dalla pagina al server, ad esempio, la struttura di spostamento strutturale, le immagini di grandi dimensioni, un sacco di chiamate API potrebbero contribuire a un tempo più lungo del server . 
    
  - **SPIISLatency** è il tempo in millisecondi ricavato dal front end server Web quando riceve la richiesta di caricamento della pagina. Si tratta di un indicatore della latenza per avviare l'elaborazione della pagina e non include il tempo necessario per l'applicazione Web per rispondere. 
    
  - Il tempo di **caricamento della pagina** è l'ora registrata dalla pagina dal momento della richiesta al momento in cui la risposta è stata ricevuta e letta dal browser. Qualsiasi tempo aggiuntivo dipende dalle prestazioni del computer e dal tempo necessario per il caricamento del browser. 
    
  - L' **URL** (Uniform Resource Locator) è l'indirizzo Web della pagina corrente. 
    
3. La [scheda **diagnostica** ](#how-to-use-the-diagnostic-tab) elenca le regole e, se una di esse è contrassegnata con una ![Croce](media/9859ac84-be43-4eae-984c-e0e827f5a228.png)rossa, sono presenti problemi identificati nella pagina.<br/>Ogni regola ha il proprio collegamento "altre informazioni" che si fa clic se un elemento è rosso. Che conterrà i dettagli alla base di quella regola e come risolvere il problema.<br/>![Diagnostica rossa-regola aperta](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)

4. Una [scheda di **traccia di rete** ](#how-to-use-the-network-trace-tab) fornisce informazioni dettagliate sulle richieste e le risposte di compilazione della pagina.

## <a name="how-to-use-the-diagnostic-tab"></a>Come usare la scheda diagnostica

1. **Controllare l'esecuzione come utente standard**  Se si esegue l'accesso come account di servizio, amministratore o amministratore della raccolta siti o qualsiasi account con privilegi elevati, non è possibile eseguire il controllo delle prestazioni delle pagine. Gli script e le funzionalità aggiuntivi vengono caricati in modo specifico per questi tipi di account, quindi i risultati non saranno una vera rappresentazione delle prestazioni delle pagine.
    
2. **Controllare le richieste a SharePoint**  La quantità di dati e le richieste apportate al server devono essere limitate poiché una pagina di overload subirà scarse prestazioni. Questo controllo consente di verificare il numero di richieste eseguite a SharePoint e di consigliare quando le richieste superano le 6 richieste. La maggior parte delle richieste deve essere memorizzata nella cache e pertanto non viene chiamata per ogni caricamento della pagina. La cache deve essere impostata e utilizzata per almeno 15 minuti per ridurre il numero di chiamate a una pagina per ogni utente. Si tratta di un problema comune e, nella maggior parte dei casi, i dati cambiano solo ogni giorno, ma la pagina consente di controllare e recuperare i dati ogni volta per ogni pagina di ogni utente che spesso non è necessario.
    
3. **Controllare l'utilizzo di reti CDN**  Le reti di distribuzione del contenuto (reti CDN) sono state fornite da Microsoft e quelle riportate di seguito sono le reti di distribuzione del contenuto di SharePoint Online. Sono disponibili più tipi di servizi CDN diversi, come SharePoint reti CDN e quindi reti CDN in Azure. [Utilizzare le linee guida seguenti](https://go.microsoft.com/fwlink/?linkid=873250).
    
4. **Controllare la dimensione delle immagini di grandi dimensioni**  Le immagini devono essere ottimizzate per il Web utilizzando tipi Web migliori come PNG. È inoltre possibile utilizzare le copie trasformate di immagini ed è disponibile in SharePoint direttamente. Le immagini/copie trasformate di immagini più grandi di 100KB verranno evidenziate come non ottimizzate per il Web. [Utilizzare le linee guida seguenti per l'ottimizzazione delle immagini](https://go.microsoft.com/fwlink/?linkid=873251).
    
5. **Controllare la struttura di spostamento strutturale**  La struttura di spostamento strutturale è stata originariamente progettata per l'utilizzo in SharePoint locale in cui è possibile utilizzare la cache degli oggetti. L'esplorazione strutturale non è consigliata per l'utilizzo in SharePoint Online e deve essere modificata per l'esplorazione gestita o per un provider personalizzato. [Per ottimizzare la struttura di spostamento, utilizzare le linee guida seguenti.](https://go.microsoft.com/fwlink/?linkid=873247)
    
6. **Controllare la cbq WebPart** (CBQ-content by query WebPart)  Il contenuto in base alla query WebPart genera un carico SQL elevato poiché attraversa tutti gli elementi della query per ogni caricamento di ogni pagina, per ogni utente. A differenza di un'installazione locale, non è disponibile alcuna cache per limitare il numero di query necessarie per popolare questa WebPart. Poiché tale CBQ si comporta lentamente e ha un impatto complessivo sulle prestazioni delle pagine, il che è il motivo per cui non deve essere utilizzato. Utilizzare il controllo WebPart per la ricerca del contenuto (CSWP) come sostituto del controllo WebPart della query di contenuto. [Utilizzare le seguenti linee guida relative al controllo WebPart di ricerca contenuto](https://go.microsoft.com/fwlink/?linkid=873245).

## <a name="how-to-use-the-network-trace-tab"></a>Come usare la scheda traccia di rete
    
La scheda **traccia di rete** fornisce informazioni dettagliate sulle richieste di creazione della pagina e sulle risposte ricevute. 

1. **Cercare i tempi di caricamento degli elementi contrassegnati come rossi**. Le prestazioni di ogni richiesta e risposta sono codificate a colori, in base al loro impatto sulle prestazioni complessive della pagina, come indicato di seguito:
- Verde: \< 500ms
- Giallo: 500-1000ms
- Rosso: \> 1000ms
<br/>![Traccia di rete](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)<br/> Nell'immagine sopra riportata, l'elemento rosso appartiene alla pagina predefinita. La visualizzazione sarà sempre rossa, a meno che la pagina \< non venga caricata in 1000ms (meno di 1 secondo).

2. **Tempi di caricamento degli elementi di prova**. In alcuni casi non vi sarà alcun indicatore di tempo o colore perché gli elementi sono già stati memorizzati nella cache dal browser. Per eseguire il testing in modo corretto, aprire la pagina, cancellare la cache del browser e quindi fare clic su **Avvia** come che forza il caricamento di una pagina "fredda" ed essere una vera riflessione del caricamento della pagina iniziale. Questo dovrebbe essere quindi confrontato con il caricamento della pagina "calda", che consentirà anche di determinare quali elementi vengono memorizzati nella cache della pagina. 
    
3. **Condividere i dettagli rilevanti con altri utenti che possono contribuire all'analisi dei problemi**. Per condividere i dettagli o le informazioni fornite nello strumento con gli sviluppatori o con una persona del supporto tecnico, fare clic su **Esporta in JSON** (come mostrato nell'immagine precedente). Che consentirà di scaricare i risultati, visualizzabili con un visualizzatore di file JSON.

> [!IMPORTANT]
> Questi risultati contengono URL e possono essere classificati come PII (informazioni di identificazione personale). Assicurarsi di seguire le linee guida dell'organizzazione prima di distribuire tali informazioni. 

## <a name="engaging-with-microsoft-support"></a>Interazione con il supporto tecnico Microsoft
   
È stata inclusa una **funzionalità di supporto tecnico Microsoft** che dovrebbe essere utilizzata solo quando si lavora direttamente su un caso di supporto per le prestazioni. L'utilizzo di questa funzionalità non offrirà alcun vantaggio quando viene utilizzato senza il team di supporto. In effetti, la pagina verrà ridotta significativamente più lenta e l'utilizzo della funzionalità può essere considerato "errato" del servizio. Quando si utilizza questa funzionalità nello strumento non sono disponibili ulteriori informazioni, in quanto le informazioni aggiuntive vengono aggiunte alla registrazione nel servizio. 

Nessuna modifica è visibile, tranne per il fatto che si riceverà una notifica che è stata abilitata e che le prestazioni della pagina saranno significativamente diminuite di 2-3 volte più lente quando questo è abilitato. Sarà pertinente solo per la pagina specifica e per la sessione attiva. Per questo motivo, questo dovrebbe essere usato con parsimonia e solo quando attivamente impegnato con il nostro team di supporto.

### <a name="to-enable-the-microsoft-support-level-feature"></a>Per abilitare la caratteristica livello di supporto Microsoft

1. Aprire lo strumento page Diagnostics.
2. Sulla tastiera, premere ALT-MAIUSC-L. Verrà visualizzata la **registrazione attiva livello di supporto**. 
3. Selezionare la casella di controllo e quindi fare clic su **Avvia** per ricaricare la pagina e generare la registrazione dettagliata per il supporto da analizzare.<br/>![Opzione di supporto attivata](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
Un elemento importante per questo è CorrelationID poiché il team di supporto utilizzerà tale numero per estrarre le informazioni necessarie. Copiare il parametro CorrelationID (nella parte superiore dello strumento di diagnostica della pagina) e fornire tale supporto poiché non è possibile eseguire l'operazione necessaria senza l'ID completo.
    
## <a name="related-topics"></a>Argomenti correlati

[Ottimizzare le prestazioni di SharePoint Online](tune-sharepoint-online-performance.md)

[Ottimizzare le prestazioni di Office 365](tune-office-365-performance.md)

[Reti per la distribuzione di contenuti](content-delivery-networks.md)
