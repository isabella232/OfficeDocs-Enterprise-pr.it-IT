---
title: Utilizzare lo strumento di diagnostica di pagina per SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.audience: Admin
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
description: Utilizzare la diagnostica di pagina per lo strumento di SharePoint per analizzare le pagine classiche con le procedure consigliate per SharePoint Online.
ms.openlocfilehash: 0fc2e16867b54e644d00c57fbfc41d4f7d042f88
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975164"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a>Utilizzare lo strumento di diagnostica di pagina per SharePoint Online

In questo articolo viene descritto come è possibile utilizzare lo strumento di diagnostica di pagina per analizzare le pagine di pubblicazione classiche e pagine nei siti di team classico, con un sottoinsieme delle procedure consigliate in **SharePoint Online**. 
  
Siti del team che non dispongono di pubblicazione abilitata non possono avvalersi dei CDN ma tutte le altre regole sono applicabili. Pubblicazione viene aggiunto un overhead aggiuntivo in modo che non è attiva la pubblicazione solo per ottenere la funzionalità di rete CDN come impatto negativo caricamenti delle pagine.
  
> [!IMPORTANT]
> Lo strumento di diagnostica di pagina non verrà eseguito su raccolte documenti o pagine di sistema, come lo strumento è progettato per controllare le pagine del sito di SharePoint. Una pagina *AllItems* è una pagina di sistema. Se si tenta di eseguire lo strumento in una pagina di sistema, si riceverà un messaggio indicante, "questa applicazione deve essere eseguita solo in pagine di SharePoint."<br/> ![Deve essere eseguito su una pagina di SharePoint](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)<br/>Non si tratta di un errore nello strumento di quando è presente alcun valore per la valutazione raccolte o le pagine di sistema. Passare a una pagina di SharePoint non di sistema per utilizzare lo strumento. Se lo si desidera fornire commenti e suggerimenti sullo strumento, fare clic sulla scheda dettagli e seguire [fornire il collegamento commenti e suggerimenti](https://go.microsoft.com/fwlink/?linkid=874109). 
  
## <a name="install-the-page-diagnostic-tool"></a>Installare lo strumento di diagnostica di pagina

> [!IMPORTANT]
> Microsoft non letti i dati o siti Web visitati e non è acquisire le informazioni personali, le informazioni di sito Web o download con questo strumento. L'unica informazione connessi tramite lo strumento è il nome del Tenant, count e indica se l'opzione di registrazione di supporto ha utilizzato quando viene eseguito lo strumento della regola. Queste informazioni sono per Microsoft per analizzare i problemi affrontati dalle sono incontrato dai nostri clienti e per garantire che la funzionalità di registrazione di supporto non è viene utilizzato in modo improprio.

1. Utilizzando un browser Chrome, aprire il [collegamento allo strumento](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) direttamente o aprire la ricerca in [WebStore Browser Chrome](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) e installare l'estensione del browser. Leggere l'informativa sulla privacy utente disponibili nella pagina Descrizione dell'archivio. Quando si aggiungono lo strumento nel browser in uso, verrà visualizzato quanto segue osservare le autorizzazioni.<br/>![Autorizzazioni per l'archivio Chrome](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)<br/>   Questo avviso è sul posto, in quanto una pagina può includere contenuto da posizioni all'esterno di SharePoint a seconda del WebPart e le personalizzazioni nella pagina. Ciò significa che lo strumento leggerà le richieste e risposte quando si fa clic sul pulsante start e solo per la scheda attiva di SharePoint in cui è in esecuzione dello strumento. Tali informazioni vengono acquisite in locale per il web browser ed sono disponibile tramite l'esportazione di collegamento JSON nello strumento. **Le informazioni non viene inviate o acquisite da Microsoft.** (Lo strumento rispetta la Privacy Microsoft criteri accessibile [qui](https://go.microsoft.com/fwlink/p/?linkid=857875).)<br/><br/>La funzionalità "Esportare per JSON" nello strumento è anche il motivo per cui è necessaria l'autorizzazione "Gestire i download disponibili". Attenersi alle linee guida relative alla Privacy dell'azienda prima che la condivisione file JSON esterni all'organizzazione, come i risultati includono gli URL e che possono essere classificata come PII (informazioni personali).
    
2. (È facoltativo) Se si desidera utilizzare lo strumento in modalità incognito Chrome, passare all'estensione e fare clic su **Consenti incognito**.
    
3. Passare alla pagina di pubblicazione classica di SharePoint in SharePoint Online che si desidera controllare. È stata consentita per "caricamento ritardato" di elementi nelle pagine; di conseguenza, lo **strumento non verrà interrotta automaticamente**. Se lo si desidera interrompere la raccolta, è possibile fare clic su **Interrompi**. (È per impostazione predefinita appropriate per tutti gli scenari di carico pagina). Prima di scegliere di **interrompere**, assicurarsi che i dati di traccia di rete sono stati completati. In caso contrario, sarà necessario una traccia parziale. Inoltre, lo strumento è un'estensione del Browser e l'apertura di più schede o windows che consente solo un'istanza attiva dello strumento da eseguire contemporaneamente. Si tratta di una limitazione delle estensioni nel browser. 
  
4. Fare clic su logo estensione ![Diagnostica di pagina per logo di SharePoint](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) per caricare lo strumento e si viene visualizzata con la finestra popup estensione seguenti:<br/> ![Strumento di diagnostica pagina Popup](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)<br/>Avviare e arrestare eseguire le operazioni inizieranno le nozioni fondamentali relative quando si fa clic su raccolta e avvia che la pagina verrà aggiornata.

Leggere le sezioni seguenti per ulteriori informazioni sulle informazioni disponibili nello strumento.

## <a name="what-youll-see-in-the-page-diagnostics-tool"></a>Nello strumento di diagnostica pagina verrà visualizzato
    
1. Il collegamento **su** verrà fornite indicazioni generali e informazioni dettagliate su strumento incluso un collegamento nuovamente a questo articolo. Include inoltre un collegamento diretto consigli relativi alle prestazioni di SharePoint, un avviso di terze parti e un'opzione per inviare commenti e suggerimenti sullo strumento. 
    
2. I dettagli **dell'ID correlazione, SPRequestDuration, SPIISLatency**, **il tempo di caricamento di pagina**e **URL** sono informativi e possono essere utilizzati per alcuni motivi. 
    
  - **CorrelationID** è un elemento importante quando si lavora con il team di supporto Microsoft poiché consente di ottenere ulteriori dati di diagnostica. 
    
  - **SPRequestDuration** è l'ora del server per elaborare la pagina. Se questo momento è lungo, non necessariamente significa che il server eseguite in modo errato, ma può anche riflette il numero di chiamate e caricare spinti dalla pagina al server, ad esempio struttura di spostamento, immagini di grandi dimensioni, una quantità elevata di chiamate all'API potrebbe contribuire a più tempo del server . 
    
  - **SPIISLatency** è il tempo in millisecondi portato nel Server Web front-End quando riceve la richiesta per il caricamento della pagina. Si tratta di un indicatore della latenza per avviare l'elaborazione della pagina e non include il tempo necessario per l'applicazione web di rispondere. 
    
  - **Tempo di caricamento di pagina** è ora registrato dalla pagina da ora della richiesta al momento della risposta è stata ricevuta e leggere dal browser. Qualsiasi altro tempo viene influenzato dalle prestazioni dei computer e il tempo che necessario per il browser per il caricamento. 
    
  - L' **URL** (Uniform Resource Locator) è l'indirizzo web della pagina corrente. 
    
3. La [scheda **diagnostica** ](#how-to-use-the-diagnostic-tab) verranno visualizzate le regole e se una qualsiasi delle loro sono contrassegnati con un rosso ![tra](media/9859ac84-be43-4eae-984c-e0e827f5a228.png), quindi non vi siano problemi identificati nella pagina.<br/>Ogni regola presenta il proprio collegamento "ulteriori informazioni" che si fa clic su se un elemento è rosso. Che si accederà in dettaglio i concetti tale regola e su come correggere il problema.<br/>![Diagnostica rosso - regola open](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)

4. Una [scheda di **traccia di rete** ](#how-to-use-the-network-trace-tab) vengono fornite informazioni dettagliate sulla pagina creare richieste e risposte.

## <a name="how-to-use-the-diagnostic-tab"></a>Come utilizzare la scheda diagnostica

1. **Controllo eseguito come utente Standard**  Controllare le prestazioni delle pagine non devono essere eseguite quando si accede a un Account di servizio, amministratore o amministratore della raccolta siti o un account con privilegi elevati. Funzionalità e script aggiuntivi vengono caricati in modo specifico per questi tipi di account, in modo che i risultati non sarà una rappresentazione reale delle prestazioni delle pagine.
    
2. **Controllare le richieste in SharePoint**  La quantità di dati e richieste inviate al server deve essere limitata come una pagina di overload osserveranno riduzione delle prestazioni. Questo controllo consente di verificare il numero di richieste in SharePoint e per avvisare quando le richieste di superano i 6 richieste. La maggior parte delle richieste devono essere memorizzati nella cache e pertanto non viene chiamate per ogni pagina caricata. Cache deve essere il programma di installazione e utilizzata per almeno 15 minuti per ridurre la quantità di chiamate a una pagina di ogni utente. Si tratta di un problema comune e nella maggior parte dei casi modifica dei dati solo ogni giorno, ma la pagina verifica e recupera i dati ogni volta che per ogni pagina per ogni utente che è spesso non necessari.
    
3. **Controllare CDN in uso**  Reti di distribuzione del contenuto (CDN) sono state fornite da Microsoft e quelli indicati di seguito sono reti di distribuzione del contenuto in linea di SharePoint. Sono disponibili più tipi di oltre a diversi servizi di rete CDN come CDN SharePoint e quindi CDN in Azure. [Utilizzare le linee guida seguenti](https://go.microsoft.com/fwlink/?linkid=873250).
    
4. **Controllare le dimensioni delle immagini di grandi dimensioni**  Immagini devono essere ottimizzate per web utilizzando le migliori tipi web come file PNG. Rendering di immagini deve inoltre essere utilizzate ed è disponibile in SharePoint direttamente. Immagini / rendering di immagini superiori a 100kb verranno evidenziate come non è ottimizzato per web. [Utilizzare le linee guida seguenti per le immagini di ottimizzazione](https://go.microsoft.com/fwlink/?linkid=873251).
    
5. **Verificare la struttura di spostamento**  Struttura di spostamento è stato originariamente progettato per l'utilizzo di SharePoint locale dove cache degli oggetti può essere utilizzata. Struttura di spostamento non è consigliato per l'utilizzo in SharePoint Online e deve essere modificato per l'esplorazione gestita o un Provider personalizzato. [Utilizzare le linee guida seguenti per l'ottimizzazione di navigazione.](https://go.microsoft.com/fwlink/?linkid=873247)
    
6. **Verificare la Web part CBQ** (CBQ - per Web part Query contenuto)  Per Web part Query contenuto genera un carico elevato SQL durante l'attraversamento tutti gli elementi nella query per ogni pagina caricata per ogni utente. A differenza di un'installazione locale, non esiste alcuna cache disponibile per limitare il numero di query necessari per popolare questa Web part. In quanto tale CBQ lento e incide sulle prestazioni generali pagina motivo per cui consigliabile non utilizzata. Utilizzare la Web part ricerca contenuto (CSWP) in sostituzione della Web part Query contenuto. [Utilizzare le informazioni seguenti relative alla Web part di ricerca del contenuto](https://go.microsoft.com/fwlink/?linkid=873245).

## <a name="how-to-use-the-network-trace-tab"></a>Come utilizzare la scheda di traccia di rete
    
Scheda di **Traccia di rete** vengono fornite informazioni dettagliate sulle richieste per creare la pagina, nonché le risposte ricevute. 

1. **Cercare i tempi di caricamento elemento contrassegnati come rosso**. Le prestazioni di ogni richiesta e risposta sono colori diversi, basato sull'impatto sulle prestazioni complessive di pagina nel modo seguente:
- Verde: \< 500 ms
- Colore giallo: 500-1000 MS
- Rosso: \> 1000 MS
<br/>![Traccia di rete](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)<br/>Nell'immagine sopra riportato, l'elemento di colore rosso è relativa alla pagina predefinita. Sarà sempre visualizzato rosso a meno che la pagina viene caricata \< 1000 ms (1 secondo).

2. **Tempi di caricamento elemento di test**. In alcuni casi non vi sarà alcun indicatore ora o il colore in quanto gli elementi sono già stati memorizzati nella cache dal browser. Per testare questo in modo corretto, aprire la pagina, deselezionare cache del browser e quindi fare clic su **Start** come che impone un caricamento della pagina "fredda" ed essere un valore true riflesso il caricamento della pagina iniziale. Questo deve essere confrontato con il caricamento della pagina "warm" come che verrà inoltre consentono di determinare quali elementi nella cache nella pagina. 
    
3. **Dettagli relativi a Condividi con altri utenti che consentono di analizzare i problemi**. Per condividere le informazioni o le informazioni disponibili nello strumento con una persona supporto tecnico o agli sviluppatori, fare clic su **Esporta in JSON** (come illustrato nell'immagine precedente). Che consentirà di scaricare i risultati visualizzabili con un visualizzatore di file JSON.

> [!IMPORTANT]
> Questi risultati sono gli URL e che possono essere classificate come PII (informazioni personali). Assicurarsi di seguire le linee guida dell'organizzazione prima di distribuire tali informazioni. 

## <a name="engaging-with-microsoft-support"></a>Partecipazione a con il supporto tecnico Microsoft
   
È stata inclusa una **caratteristica a livello di supporto Microsoft** che devono essere sfruttato solo quando si lavora direttamente in un caso del supporto tecnico per le prestazioni. Utilizzando questa caratteristica non fornirà alcun vantaggio all'utente quando viene utilizzata senza il nostro team di supporto. Infatti effettua la pagina significativamente più lente e continuazione dell'utilizzo della caratteristica può essere considerata "utilizzate in modo improprio" del servizio. Non sono disponibili informazioni aggiuntive quando si utilizza questa funzionalità dello strumento con l'aggiunta di informazioni aggiuntive per la registrazione nel servizio. 

Nessuna modifica è visibile la differenza che si riceverà una notifica che è stata abilitata e le prestazioni delle pagine risulterà notevolmente inferiore per 2 - 3 volte un rallentamento delle prestazioni, che è abilitata. Solo sarà pertinente per una determinata pagina e tale sessione attiva. Per questo motivo, si consiglia di utilizzarla e solo se attivamente impegnati con il Team di supporto.

### <a name="to-enable-the-microsoft-support-level-feature"></a>Per attivare la caratteristica di livello di supporto Microsoft

1. Aprire lo strumento di diagnostica di pagina.
2. Sulla tastiera, premere ALT-MAIUSC-L. Verrà visualizzata **abilitare la registrazione di livello di supporto**. 
3. Selezionare la casella di controllo e quindi fare clic su **start** per ricaricare la pagina e genera la registrazione dettagliata per il supporto per l'analisi.<br/>![Opzione supporto abilitato](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
Un importante elemento per questo è il parametro CorrelationID come il team di supporto utilizzerà quindi tale numero per estrarre le informazioni necessarie. Copiare il parametro CorrelationID (nella parte superiore dello strumento di diagnostica pagina) e che offrono supporto come non possono eseguire le operazioni necessarie senza l'ID completo.
    
## <a name="related-topics"></a>Argomenti correlati

[Ottimizzare le prestazioni di SharePoint Online](tune-sharepoint-online-performance.md)

[Ottimizzare le prestazioni di Office 365](tune-office-365-performance.md)

[Reti per la distribuzione di contenuti](content-delivery-networks.md)
