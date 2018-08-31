---
title: Utilizzare lo strumento di diagnostica di pagina per SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/26/2018
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
ms.openlocfilehash: 6bfe26900426b30b9f0ad0746b0c1840e122dc82
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541358"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a>Utilizzare lo strumento di diagnostica di pagina per SharePoint Online

In questo articolo viene descritto come è possibile utilizzare lo strumento di diagnostica di pagina per analizzare le pagine di pubblicazione classiche e pagine nei siti di team classico, con un sottoinsieme delle procedure consigliate in **SharePoint Online**. 
  
Siti del team che non dispongono di pubblicazione abilitata non possono avvalersi dei CDN ma tutte le altre regole sono applicabili. Pubblicazione viene aggiunto un overhead aggiuntivo in modo che non è attiva la pubblicazione solo per ottenere la funzionalità di rete CDN come impatto negativo caricamenti delle pagine.
  
> [!IMPORTANT]
> Lo strumento di diagnostica di pagina non verrà eseguito su raccolte documenti o pagine di sistema, come lo strumento è progettato per controllare le pagine del sito di SharePoint. Una pagina *AllItems* è una pagina di sistema. Se si tenta di eseguire lo strumento in una pagina di sistema, verrà visualizzato un messaggio indicante, "questa applicazione deve essere eseguita solo in pagine di SharePoint." > ![deve essere eseguito su una pagina di SharePoint](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)
  
> Non si tratta di un errore nello strumento di quando è presente alcun valore per la valutazione raccolte o le pagine di sistema. Passare a una pagina di SharePoint non di sistema per utilizzare lo strumento. Se lo si desidera fornire commenti e suggerimenti sullo strumento, fare clic sulla scheda dettagli e seguire [fornire il collegamento commenti e suggerimenti](https://go.microsoft.com/fwlink/?linkid=874109). 
  
## <a name="how-to-use-the-page-diagnostic-tool"></a>Come utilizzare lo strumento di diagnostica di pagina
<a name="useit"> </a>

1. Utilizzando un browser Chrome, aprire il [collegamento allo strumento](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) direttamente o aprire la ricerca in [WebStore Browser Chrome](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) e installare l'estensione del browser. 
    
    Leggere l'informativa sulla privacy utente disponibili nella pagina Descrizione dell'archivio.
    
    Quando si aggiungono lo strumento nel browser in uso, verrà visualizzato quanto segue osservare le autorizzazioni.
    
    ![Autorizzazioni per l'archivio Chrome](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)
  
    Questo avviso è sul posto, in quanto una pagina può includere contenuto da posizioni all'esterno di SharePoint a seconda del WebPart e le personalizzazioni nella pagina. Ciò significa che lo strumento leggerà le richieste e risposte quando si fa clic sul pulsante start e solo per la scheda attiva di SharePoint in cui è in esecuzione dello strumento. Tali informazioni vengono acquisite in locale per il web browser ed sono disponibile tramite l'esportazione di collegamento JSON nello strumento. **Le informazioni non viene inviate o acquisite da Microsoft.**
    
    > [!IMPORTANT]
    > Microsoft non letti i dati o siti Web visitati e non è acquisire le informazioni personali, le informazioni di sito Web o download con questo strumento. L'unica informazione connessi tramite lo strumento è il nome del Tenant, count e indica se l'opzione di registrazione di supporto ha utilizzato quando viene eseguito lo strumento della regola. Queste informazioni sono per Microsoft per analizzare i problemi affrontati dalle sono incontrato dai nostri clienti e per garantire che la funzionalità di registrazione di supporto non è viene utilizzato in modo improprio.
  
Lo strumento rispetta la Privacy Microsoft criteri accessibile [qui](https://go.microsoft.com/fwlink/p/?linkid=857875). 
  
    The "Export to JSON" functionality in the tool is also why the "Manage your downloads" permission is needed. Please follow your Company's own Privacy guidelines before sharing the JSON file outside of your Company as it contains the URL's and they fall within PII (Personally Identifiable Information).
    
2. (Facoltativo) Se si desidera utilizzare lo strumento in modalità incognito Chrome, passare all'estensione e fare clic su "Consenti in incognito".
    
3. Passare alla pagina di pubblicazione classica di SharePoint in SharePoint Online che si desidera controllare.
    
    > [!IMPORTANT]
    > È stata consentita per "caricamento ritardato" di elementi nelle pagine; di conseguenza, lo **strumento non verrà interrotta automaticamente**. Se lo si desidera interrompere la raccolta, è possibile fare clic su **Interrompi**. (È per impostazione predefinita appropriate per tutti gli scenari di carico pagina) 
  
Prima di scegliere di **interrompere**, assicurarsi che i dati di traccia di rete sono stati completati. In caso contrario, sarà necessario una traccia parziale. 
  
Inoltre, lo strumento è un'estensione del Browser e l'apertura di più schede o windows che consente solo un'istanza attiva dello strumento da eseguire contemporaneamente. Si tratta di una limitazione delle estensioni nel browser. 
  
4. Fare clic su logo estensione ![Diagnostica di pagina per logo di SharePoint](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) per caricare lo strumento e si viene visualizzata con la finestra popup estensione seguenti: 
    
    ![Strumento di diagnostica pagina Popup](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)
  
    Avviare e arrestare eseguire le operazioni inizieranno le nozioni fondamentali relative quando si fa clic su raccolta e avvia che la pagina verrà aggiornata.
    
5. Il primo collegamento corrisponde al collegamento **su** e verrà fornite indicazioni generali e informazioni dettagliate su strumento incluso un collegamento all'articolo. Include inoltre un collegamento diretto consigli relativi alle prestazioni di SharePoint, un avviso di terze parti e un'opzione per inviare commenti e suggerimenti sullo strumento. 
    
6. Esaminare le informazioni **ID correlazione, SPRequestDuration, SPIISLatency** **, caricare la pagina ora e l'URL** . (In questa sezione è puramente informativa e può essere utilizzata per scopi alcuni). 
    
  - **CorrelationID** è un elemento importante quando si lavora con il team di supporto Microsoft poiché consente di ottenere ulteriori dati di diagnostica. 
    
  - **SPRequestDuration** è l'ora del server per elaborare la pagina. Se questo momento è lungo, non necessariamente significa che il server eseguite in modo errato, ma può anche riflette il numero di chiamate e caricare spinti dalla pagina al server, ad esempio struttura di spostamento, immagini di grandi dimensioni, una quantità elevata di chiamate all'API potrebbe contribuire a più tempo del server . 
    
  - **SPIISLatency** è il tempo in millisecondi portato nel Server Web front-End quando riceve la richiesta per il caricamento della pagina. Si tratta di un indicatore della latenza per avviare l'elaborazione della pagina e non include il tempo necessario per l'applicazione web di rispondere. 
    
  - **Tempo di caricamento di pagina** è ora registrato dalla pagina da ora della richiesta al momento della risposta è stata ricevuta e leggere dal browser. Qualsiasi altro tempo viene influenzato dalle prestazioni dei computer e il tempo che necessario per il browser per il caricamento. 
    
  - L' **URL** (Uniform Resource Locator) è l'indirizzo web della pagina corrente. 
    
7. La **scheda diagnostica** verranno visualizzate le regole e se una qualsiasi delle loro sono contrassegnati con un rosso ![tra](media/9859ac84-be43-4eae-984c-e0e827f5a228.png), quindi non vi siano problemi identificati nella pagina.
    
    Ogni regola ha il proprio collegamento "ulteriori informazioni" Se si fa clic su di esso quando è rosso. Che si accederà in dettaglio i concetti tale regola e su come correggere il problema.
    
    ![Diagnostica rosso - regola open](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)
  
1. Verificare l'utente che esegue come Standard
  
Controllare le prestazioni delle pagine non devono essere eseguite durante l'accesso con un Account di servizio, un amministratore o un amministratore della raccolta siti vale a dire un account con privilegi elevati. Funzionalità e script aggiuntivi viene caricati in modo specifico per i tipi di account e non fornirà una rappresentazione reale delle prestazioni delle pagine.
    
2. Richieste di controllo per SharePoint
  
La quantità di dati e richieste inviate al server deve essere limitata come una pagina di overload osserveranno riduzione delle prestazioni. Questo controllo consente di verificare il numero di richieste in SharePoint e per avvisare quando le richieste di superano i 6 richieste. La maggior parte delle richieste devono essere memorizzati nella cache e pertanto non viene chiamate per ogni pagina caricata. Cache deve essere il programma di installazione e utilizzata per almeno 15 minuti per ridurre la quantità di chiamate a una pagina di ogni utente. Si tratta di un problema comune e nella maggior parte dei casi modifica dei dati solo ogni giorno, ma la pagina verifica e recupera i dati ogni volta che per ogni pagina per ogni utente che è spesso non necessari.
    
3. Controllare CDN in uso
  
Reti di distribuzione del contenuto sono state fornite da Microsoft e quelli indicati di seguito sono reti di distribuzione del contenuto in linea di SharePoint. Sono disponibili più tipi di oltre a diversi servizi di rete CDN come CDN SharePoint e quindi CDN in Azure. [Utilizzare le linee guida seguenti](https://go.microsoft.com/fwlink/?linkid=873250).
    
4. Controllo per immagine di grandi dimensioni
  
Immagini devono essere ottimizzate per web utilizzando le migliori tipi web come file PNG. Rendering di immagini deve inoltre essere utilizzate ed è disponibile in SharePoint direttamente. Immagini / rendering di immagini superiori a 100kb verranno evidenziate come non è ottimizzato per web. [Utilizzare le linee guida seguenti per le immagini di ottimizzazione](https://go.microsoft.com/fwlink/?linkid=873251).
    
5. Controllo per la struttura di spostamento
  
Struttura di spostamento è stato originariamente progettato per l'utilizzo di SharePoint locale dove cache degli oggetti può essere utilizzata. Struttura di spostamento non è consigliato per l'utilizzo in SharePoint Online e deve essere modificato per l'esplorazione gestita o un Provider personalizzato. [Utilizzare le linee guida seguenti per l'ottimizzazione di navigazione.](https://go.microsoft.com/fwlink/?linkid=873247)
    
6. Verificare la Web part CBQ (CBQ - per Web part Query contenuto)
  
Per Web part Query contenuto genera un carico elevato SQL durante l'attraversamento tutti gli elementi nella query per ogni pagina caricata per ogni utente. A differenza di un'installazione locale, non esiste alcuna cache disponibile per limitare il numero di query necessari per popolare questa Web part. In quanto tale CBQ lento e incide sulle prestazioni generali pagina motivo per cui consigliabile non utilizzata. Utilizzare la Web part ricerca contenuto (CSWP) in sostituzione della Web part Query contenuto. [Utilizzare le informazioni seguenti relative alla Web part di ricerca del contenuto](https://go.microsoft.com/fwlink/?linkid=873245).
    
8. La **scheda di rete traccia** fornisce * * * informazioni dettagliate sulle richieste per creare la pagina, nonché le risposte ricevute. Le prestazioni di ogni richiesta e risposta vengono codificati a colori basato sull'impatto sulle prestazioni complessive di pagina vale a dire verde \< 500 ms, giallo 1000 MS 500 e rossa \> 1000 ms. 
    
    In questa scheda non esiste un'esportazione all'opzione JSON se lo si desidera scaricare e condividere i dettagli della richiesta e la risposta.
    
    > [!IMPORTANT]
    > Posizionare il puntatore sugli URL abbreviato per visualizzare l'URL completo. 
  
    ![Traccia di rete](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)
  
    In questa immagine il colore rosso è la pagina stessa e che è sempre di colore rosso a meno che la pagina viene caricata \< 1000 ms (vale a dire 1 secondo).
    
    In alcuni casi, *non ci sarà alcun indicatore ora o il colore in quanto gli elementi sono già stati memorizzati nella cache dal browser* . Per testare questo in modo corretto, aprire la pagina, deselezionare cache del browser e quindi fare clic su **Start** come che impone un caricamento della pagina "fredda" ed essere un valore true riflesso il caricamento della pagina iniziale. Questo deve essere confrontato con il caricamento della pagina "warm" come che verrà inoltre consentono di determinare quali elementi nella cache nella pagina. 
    
9. Se si desidera condividere le informazioni o le informazioni con gli sviluppatori o un addetto del supporto è possibile fare clic su "Esportare per JSON" come immagine precedente e che eseguirà il download i risultati. Si noti che il file può quindi essere aperta utilizzando un visualizzatore di file JSON.
    
    > [!IMPORTANT]
    > Questi risultati contengono l'URL e pertanto contiene PII (informazioni personali) è necessario attenersi alle linee guida società prima di distribuire tali informazioni. 
  
10. È stata inclusa una **caratteristica a livello di supporto Microsoft** che devono essere sfruttato solo quando si lavora direttamente in un caso del supporto tecnico per le prestazioni. Utilizzando questa caratteristica non fornirà alcun vantaggio all'utente quando viene utilizzata senza il nostro team di supporto. Infatti effettua la pagina significativamente più lente e continuazione dell'utilizzo della caratteristica può essere considerata "utilizzate in modo improprio" del servizio. Non sono disponibili informazioni aggiuntive quando si utilizza questa funzionalità dello strumento con l'aggiunta di informazioni aggiuntive per la registrazione nel servizio. 
    
    Nessuna modifica è visibile la differenza che si riceverà una notifica che è stata abilitata e le prestazioni delle pagine risulterà notevolmente inferiore per 2 - 3 volte un rallentamento delle prestazioni, che è abilitata. Solo sarà pertinente per una determinata pagina e tale sessione attiva. Per questo motivo, si consiglia di utilizzarla e solo se attivamente impegnati con il Team di supporto.
    
    Per attivare la caratteristica, aprire lo strumento e utilizzare ALT-MAIUSC-L che verrà quindi visualizzata "abilitare la registrazione a livello di supporto". Fare clic sulla che casella di controllo e quindi fare clic su start per ricaricare la pagina e generare la registrazione dettagliata per il supporto per l'analisi.
    
    ![Opzione supporto abilitato](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
    Un importante elemento per questo è il parametro CorrelationID come il team di supporto utilizzerà quindi tale numero per estrarre le informazioni necessarie. Copiare il parametro CorrelationID e che offrono supporto come non possono eseguire le operazioni necessarie senza l'ID completo.
    

