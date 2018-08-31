---
title: Durante e dopo lo spostamento dati
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 3/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
description: Spostamenti di dati sono un'operazione di back-end con un impatto minimo per gli utenti finali. Mentre Microsoft Sposta ogni servizio e dei dati associati per il tenant di un nuovo livello geografico datacenter, è necessaria alcuna azione. Il trasferimento dei dati e la convalida eseguita in background in anticipo con un impatto minimo per gli utenti.
ms.openlocfilehash: 8813e73dcbce7b6ea24e497929ca6b8e0928e4e7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541273"
---
# <a name="during-and-after-your-data-move"></a>Durante e dopo lo spostamento dati

Spostamenti di dati sono un'operazione di back-end con un impatto minimo per gli utenti finali. Mentre Microsoft Sposta ogni servizio e dei dati associati per il tenant di un nuovo livello geografico datacenter, è necessaria alcuna azione. Il trasferimento dei dati e la convalida eseguita in background in anticipo con un impatto minimo per gli utenti.
  
> [!NOTE]
> Spostamenti si verificano in momenti diversi per ogni servizio. Di conseguenza, vedrai descritte alcune funzionalità per ogni servizio in momenti diversi. 
  
Guardare interfaccia di Office 365 messaggio di conferma quando si sposta per ognuno di Exchange Online, SharePoint Online e Skype per le aziende sono state completate. Come illustrato nella tabella riportata di seguito, è possibile richiedere fino a 24 mesi, dopo la fine del periodo di registrazione, per completare tutti i dati richiesti sposta per tutti i clienti di un livello geografico specifico. Se viene visualizzata eventuali problemi con il tenant dopo lo spostamento, contattare il [Supporto per Office 365](https://go.microsoft.com/fwlink/p/?LinkID=522459) per ottenere assistenza. 
  

|**Clienti con indirizzo di fatturazione**|**Tutti gli spostamenti completati manualmente**|
|:-----|:-----|
|Australia, Nuova Zelanda Figi  <br/> |31 ottobre 2017  <br/> |
|Giappone  <br/> |31 ottobre 2018  <br/> |
|India  <br/> |31 ottobre 2018  <br/> |
|Canada  <br/> |31 ottobre 2018  <br/> |
|Sud Corea  <br/> |31 ottobre 2018  <br/> |
|Regno Unito  <br/> |15 settembre 2019  <br/> |
|Francia  <br/> |15 settembre 2020  <br/> |
   
## <a name="moves-that-involve-a-third-party-audio-conferencing-provider"></a>Spostamenti che implicano l'utilizzo di un Provider di servizi di conferenza Audio di terze parti

- Servizi di componente aggiuntivo Provider di servizi di conferenza Audio di terze parti per Skype per le aziende non sono disponibili per gli utenti ospitati in nuovi centri dati geo specifici. 
    
- I clienti esistenti utilizzando il servizio Provider di servizi di conferenza Audio di terze parti non devono richiedere uno spostamento di un nuovo centro dati specifici a livello geografico. 
    
- Nuovi clienti distribuiti in nuovi centri di dati specifici a livello geografico saranno necessario richiedere uno spostamento di un centro dati locale per utilizzare un Provider di servizi di conferenza Audio di terze parti. 
    
## <a name="exchange-online"></a>Exchange Online

Poiché il tempo per spostare ogni utente per il nuovo livello geografico datacenter per un singolo tenant, alcuni utenti saranno ancora presente nel precedente geo di datacenter durante lo spostamento, mentre altri utenti saranno nella nuova geo di datacenter. Ciò significa che alcune caratteristiche che implicano l'utilizzo di accesso a più cassette postali non completamente lavorare durante un periodo del processo di spostamento, che può ultime settimane. Queste funzionalità sono descritte nelle sezioni seguenti.
  
### <a name="mailbox-move"></a>Spostamento delle cassette postali

Quando una singola cassetta postale spostamenti crosses datacenter geos, il contenuto delle cassette postali viene innanzitutto pre-in fasi in modo che i dati esistenti viene copiati geo destinazione senza modificare la cassetta postale. Al momento della completa geo destinazione della cassetta postale in geo origine è bloccata per alcuni minuti. Nel frattempo il client di posta elettronica non possono connettersi temporaneamente. Modifiche aggiuntive vengono copiate geo destinazione e quindi la cassetta postale completa lo spostamento in geo destinazione. Non esiste alcuna interruzione del servizio di flusso di posta durante lo spostamento.
  
Alcuni utenti potrebbero essere necessario riavviare Outlook Desktop dopo lo spostamento della cassetta postale come descritto [nell'articolo della Knowledge Base 2591913](https://support.microsoft.com/kb/2591913).
  
### <a name="shared-mailbox"></a>Cassetta postale condivisa

Un utente con l'autorizzazione "Accesso completo" per le cassette postali condivise non è influenzato durante lo spostamento.
  
### <a name="resource-mailbox"></a>Cassetta postale delle risorse

Un utente che ha necessità di gestire le configurazioni delle cassette postali delle risorse mediante la pagina Opzioni di Outlook Web Access è possibile continuare a eseguire questa operazione durante lo spostamento.
  
Se le cassette postali delle risorse vengono gestite direttamente tramite i cmdlet di Exchange, il cmdlet Set-MailboxRegionalConfiguration e Set-MailboxCalendarConfiguration non funziona se l'utente in esecuzione e la cassetta postale delle risorse geos diversi.
  
### <a name="calendar-delegation"></a>Delega di calendario

Disponibilità e condivisione del calendario non sono interessati durante lo spostamento tenant. L'utente con autorizzazioni di scrittura per la cartella di calendario della cassetta postale B può gestire ancora cartella Calendario della cassetta postale B utilizza Outlook Desktop. Tuttavia, durante lo spostamento, se l'utente a e B delle cassette postali non sono presenti nelle geo stesso, l'utente non può modificare calendario della cassetta postale B in Outlook Web Access fino a quando non entrambi vengono spostate geo destinazione.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Aprire "Cartella condivisa" in Outlook Web Access

Alcuni utenti di aprire una cartella di posta condivise da un'altra cassetta postale (che l'utente dispone di lettura o scrittura delle autorizzazioni per) in Outlook Web Access tramite la funzionalità "Cartella condivisa". Nella tabella seguente viene descritto come spostare l'accesso a cartelle condivise works durante una cassetta postale. Si noti che gli utenti con autorizzazioni complete per una cassetta postale condivisa possono aprire la cassetta postale tramite Outlook Web Access durante lo spostamento. 
  
|**Configurazione**|**Descrizione**|
|:-----|:-----|
|Utente disponga dell'autorizzazione di cartella delle cassette postali a un'altra cassetta postale  <br/> |Potenzialmente limitato.  <br/> Se l'utente a e B delle cassette postali non nella stessa geo durante lo spostamento tenant, l'utente non può aprire la cartella delle cassette postali B in Outlook Web Access se l'utente dispone solo dell'autorizzazione in una determinata cartella delle cassette postali B.  <br/> Per aggiungere una cartella condivisa, destro del mouse sul nome utente nel riquadro di spostamento a sinistra e selezionare **Aggiungi cartella condivisa**.  <br/> |
|Utente con l'autorizzazione completa delle cassette postali a un'altra cassetta postale  <br/> |Supporto completo.  <br/> Se l'utente dispone dell'autorizzazione "Accesso completo" per cassetta postale B, l'utente può fare clic sulla cartella condivisa nel riquadro di spostamento a sinistra in Outlook Web Access per aprire una finestra di visualizzazione delle cassette postali B.  <br/> > [!NOTE]> Un utente può aprire una cassetta postale condivisa tramite Outlook Web Access durante lo spostamento senza alcun impatto negativo. La limitazione si applica solo a livello di cartella condivisione in una cassetta postale.           |
   
### <a name="public-folders"></a>Cartelle pubbliche

Se la cassetta postale di cartelle pubbliche è temporaneamente in un Data Center diverse geo dall'utente che tenta di accedervi, l'utente non possono accedervi. 
  
### <a name="online-archives"></a>Archivi online

Utenti che si connettono tramite Outlook Web Access non sarà in grado di connettersi alla cassetta postale di archivio online durante lo spostamento. È supportato l'accesso alla cassetta postale di archiviazione per utenti che si connettono con Outlook.
  
### <a name="ediscovery-amp-auditing"></a>eDiscovery &amp; controllo

EDiscovery e il controllo delle caratteristiche di Office 365 Security &amp; Sposta tenant geo tra il supporto di centro conformità. a differenza di interfaccia di amministrazione di Exchange (EAC), che non supporta gli utenti che non sono ancora spostati dopo il tenant spostare l'esecuzione di query è stato avviato. Per ulteriori informazioni sulla sicurezza &amp; centro conformità, vedere [protezione di Office 365 &amp; centro conformità](https://go.microsoft.com/fwlink/p/?linkid=841313). 
  
Nella tabella seguente viene illustrato come accedere a eDiscovery e controllo tramite l'interfaccia di amministrazione di Exchange e la sicurezza &amp; centro conformità.
  
||**Interfaccia di amministrazione di Exchange**|**Protezione &amp; centro conformità**|
|:-----|:-----|:-----|
|eDiscovery  <br/> | Accedere a https://portal.office.come quindi fare clic su tessera di **amministrazione** . </br> Fare clic su **Admin Center** \> **Exchange**. </br> Selezionare **gestione della conformità** \> **eDiscovery in locale &amp; attesa**. | Accedere a https://portal.office.come quindi fare clic su tessera di amministrazione. </br> Fare clic su **Admin Center** \> **protezione &amp; conformità**. </br> Selezionare **ricerca &amp; indagini** \> **eDiscovery**.|
|Controllo  <br/> | Accedere a https://portal.office.come quindi fare clic su tessera di **amministrazione** . </br> Fare clic su **Admin Center** \> **Exchange**. Selezionare **gestione della conformità** \> **il controllo**. | Accedere a https://portal.office.come quindi fare clic su tessera di amministrazione. </br> Fare clic su **Admin Center** \> **protezione &amp; conformità**. </br> Selezionare **ricerca &amp; indagini** \> **ricerca dei registri di controllo**. |
   
### <a name="mailbox-migration"></a>Migrazione delle cassette postali

Durante lo spostamento di un tenant tra geos, un batch di migrazione potrebbe segnalare errori su alcuni utenti nel batch di migrazione che restano nel geo origine. In questo caso, rimuovere il batch di migrazione esistenti per rimuovere la richiesta di sincronizzazione sottostante. Dopo il batch completamente pulito, creare il batch, quale inizierà a creare richieste di sincronizzazione in geo destinazione.
  
## <a name="sharepoint-online"></a>SharePoint Online

Quando viene spostato SharePoint Online, vengono spostati anche dati per i servizi seguenti:
  
- One Drive for Business
    
- Project Online
    
- Project per Office 365
    
- Servizi di Video di Office 365
    
- Office Online
    
- Office 365 ProPlus
    
- Visio Pro per Office 365
    
Dopo aver completato il passaggio di dati di SharePoint Online, è possibile visualizzare alcuni degli effetti seguenti.
  
### <a name="office-365-video-services"></a>Servizi Video di Office 365

- Spostare i dati degli video è più lungo del spostamenti per il resto del contenuto in SharePoint Online.
    
- Dopo aver SharePoint Online viene spostato il contenuto, ci sarà un intervallo di tempo quando non è in grado di riprodurre video.
    
- Si sta rimuovendo codificato transazioni dal centro dati precedenti e transcodifica li copia nuovamente nel nuovo centro dati.
    
### <a name="search"></a>Ricerca

Durante lo spostamento di dati di SharePoint Online, è eseguire la migrazione delle impostazioni di ricerca e di indice di ricerca in una nuova posizione. Fino a quando non è stato **completato** lo spostamento dei dati di SharePoint Online, è continua gestire gli utenti dall'indice nella posizione originale. Nel nuovo percorso ricerca avvia automaticamente la ricerca per indicizzazione del contenuto dopo aver completato il passaggio di dati di SharePoint Online. Da questo punto e in avanti è gestire gli utenti dall'indice di migrati. Modifiche al contenuto che si sono verificati dopo la migrazione non vengono inclusi nell'indice migrato fino a quando la ricerca per indicizzazione Seleziona. La maggior parte dei clienti non si noti che i risultati sono meno destra aggiornato dopo aver completato lo spostamento dei dati di SharePoint Online, ma alcuni clienti potrebbero verificarsi aggiornamento ridotta prima 48 24 ore 
  
Le seguenti funzionalità di ricerca sono interessate:
  
- Web part di ricerca e i risultati di ricerca: i risultati non includono le modifiche apportate dopo la migrazione fino a quando la ricerca per indicizzazione Seleziona. 
    
- Approfondire: Approfondire non include le modifiche apportate dopo la migrazione fino a quando la ricerca per indicizzazione Seleziona.
    
- Popolarità e report della ricerca per il sito: il numero per i rapporti di Excel in una nuova posizione include solo conteggi sottoposti a migrazione e numero di report di utilizzo che sono state eseguite al termine è lo spostamento di dati di SharePoint Online. Qualsiasi numero da periodo provvisorio viene interrotte e non può essere ripristinato. In questo periodo è in genere un paio di giorni. Alcuni clienti potrebbero verificarsi perdite breve o più.
    
- Video Portal: Visualizza il numero e le statistiche per il portale Video dipendono dalle statistiche per i report di Excel, in modo visualizzare i conteggi relativi ai e le statistiche per il portale di Video vengono perse per lo stesso periodo di tempo per i report di Excel.
    
- eDiscovery: elementi modificati durante la migrazione non vengono visualizzati solo la ricerca per indicizzazione seleziona automaticamente le modifiche.
    
- Prevenzione della perdita dei dati (DLP): Criteri non vengono applicati gli elementi che modificano finché la ricerca per indicizzazione seleziona automaticamente le modifiche.
    
## <a name="skype-for-business"></a>Skype for Business

Tutti gli utenti la disconnessione da Skype per il software client aziendale durante cutover. Automatico sign-in eseguiranno la riconnessione gli utenti all'interno di due minuti.
  
|**Funzionalità disponibili durante l'intero trasloco**|**Caratteristiche che possono essere limitati durante una parte dello spostamento**|
|:-----|:-----|
| Chiamate VoIP e messaggistica immediate  <br/>  Gli utenti possono aggiungere contatti, aggiungere gruppi di contatti, aggiungere le riunioni, impostare il percorso e modificare "Appuntamenti giornalieri".  <br/>  Impostazioni audio Conferencing Provider (ACP) vengono copiate i geo datacenter di destinazione. Se il provider di servizi di Audioconferenza è presente nel centro dati di destinazione, possa essere utilizzata. In caso contrario, verrà non.  <br/> | Non sarà disponibile per gli amministratori di creare sessioni tenant Admin TRPS (Tenant Remote PowerShell).  <br/>  Amministratore tenant interfaccia non sarà disponibile per gli amministratori di accedere e modificare le impostazioni utente.  <br/> |
   
|**Dopo lo spostamento**|
|:-----|
| Dati delle riunioni (presentazioni caricate e così via) non verranno spostate e saranno necessario rieseguire caricati.  <br/>  Client Lync meno recenti, ad esempio il client Lync 2010 e Lync per Mac 2011 client, sono noti da memorizzare nella cache le informazioni di DNS per il servizio causa problemi di accesso. Cancellazione della cache DNS può essere necessaria se l'utente non è disponibile nella Skype più recente per il client Windows aziendali. Chiedere agli utenti di eseguire la [procedura guidata di risoluzione dei problemi](https://support.microsoft.com/en-us/kb/2541980) e attenersi alle istruzioni su come cancellare la cache del client. Lync per Mac client devono seguire [queste istruzioni](https://support.microsoft.com/en-us/kb/2629861).<br/> |
   
## <a name="data-for-other-services-including-yammer-and-power-bi"></a>Dati di altri servizi, tra cui Yammer e Power BI

È spostare solo i dati dei clienti per Exchange Online, SharePoint Online e Skype per le aziende. Non è spostare i dati per altri servizi. Nessuna modifica o impatto è come un cliente o un utente di questi altri servizi. Il processo di spostamento non influenza la loro e il percorso dei propri dati personali rimane invariato.
  

