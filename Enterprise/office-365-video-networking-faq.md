---
title: Video di Office 365 domande frequenti di rete
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/13/2016
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
ms.assetid: 2bed67a1-4052-49ff-a4ce-b7e6530eb98e
description: Nell'archivio file Video di Office 365 e del flusso di servizi di semplificare l'archiviazione e del flusso video all'interno dell'organizzazione. È disponibile una quantità elevata di informazioni interessanti su Office 365 Video. questa sezione Domande frequenti rete è progettata per rispondere alle domande più comuni intorno a larghezza di banda e pianificazione, la crittografia, come il servizio si basa su reti di distribuzione del contenuto (CDN).
ms.openlocfilehash: bea9838277b5752e4c9905162c0e8525e8aded04
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541187"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a>Video di Office 365 domande frequenti di rete

Nell'archivio file Video di Office 365 e del flusso di servizi di semplificare l'archiviazione e del flusso video all'interno dell'organizzazione. È disponibile una quantità elevata di [informazioni su Office 365 Video](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)interessanti; questa sezione Domande frequenti rete è progettata per rispondere alle domande più comuni intorno a larghezza di banda e pianificazione, la crittografia, come il servizio si basa su [reti di distribuzione del contenuto (CDN)](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).
  
Se non già una conoscenza approfondita di cosa succede quando viene caricato un video o di riproduzione, dare uno sguardo in questo video abbiamo, [cosa succede a un file video quando vengono caricati in Office 365 Video](https://www.youtube.com/watch?v=HXSZ0jYBKlM).
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a>Che cosa sono i requisiti di larghezza di banda Video di Office 365?

Sono disponibili una numerosi [formati video supportati](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817) che possono essere caricati in Office 365. Ogni file video viene quindi codificato in un formato standard con diverse diverse qualità video per la riproduzione. Video di Office 365 utilizza velocità in bit adattivi di tipo di flusso per selezionare la migliore qualità la riproduzione del video in base alla larghezza di banda di rete disponibile e dimensioni del lettore video. Per ottenere questo risultato, il lettore richiede inizialmente la qualità di riproduzione più bassa. Il servizio inizia quindi inviando segmenti video 2 secondi il lettore video. Qualità superiore o inferiore riproduzione in base a sulla velocità viene recapitato ogni segmento di richiedere Windows Media player.
  
La velocità in bit adattivi flusso non eseguire queste operazioni in background durante la riproduzione del video con la quantità minima di interruzione del servizio o la memorizzazione nel buffer. Durante la riproduzione video, il lettore video consente di ignorare manualmente la qualità di riproduzione automatici, selezionare una qualità specifico per la riproduzione del video.
  
Di seguito è una tabella rapida che indicano i requisiti di rete per ciascuna delle qualità la riproduzione del video. La larghezza di banda minima per ogni persona necessario per riprodurre un video è 802Kbps.
  
|||
|:-----|:-----|
|**Qualità di riproduzione** <br/> |**Velocità di rete** <br/> |
|288p  <br/> |802kbps  <br/> |
|p 360  <br/> |1.2 Mbps  <br/> |
|576p  <br/> |2.5 Mbps  <br/> |
|720p  <br/> |3.8 Mbps  <br/> |

([Torna all'inizio](office-365-video-networking-faq.md))
  
## <a name="how-do-cdns-help-video-playback"></a>Come CDN facilitare la riproduzione video?

Se più persone dalla stessa organizzazione nella stessa posizione geografica sono streaming video(s) stesso, CDN memorizzerà una copia di questi video in una posizione più vicino a tale area geografica. Video archiviati o memorizzati nella cache nella posizione più vicina, ogni persona flussi video dalla posizione più vicina loro anziché una posizione ulteriormente non al computer. Video di Office 365 utilizza servizi di supporto Azure per gestire cosa viene memorizzato nella cache in CDN Azure e per quanto tempo. Servizi di Azure multimediale possibile utilizzare uno dei [percorsi CDN Azure](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/) per memorizzare nella cache frammenti video e i manifesti per alcuni giorni. Se gli utenti dell'organizzazione continuano a guardare i video memorizzati nella cache verranno rimanere nella cache. Se nessun accessi un video per diversi giorni, il video verrà alla fine eliminare essere eliminato dalla cache. Il successivo periodo di che un utente tenta di guardare il video che è ancora una volta memorizzata nella cache nel percorso di rete CDN più vicino.
  
Utenti che tentano di visualizzare il video mentre il contenuto viene memorizzato nella cache un vantaggi CDN circostanti dal video da più vicina e nella maggior parte dei casi meno hop, non al computer. In questo modo migliorano la velocità di riproduzione video; Tuttavia, non modifica la necessità di rete di riprodurre il video.
  
> [!NOTE]
> Vi sono alcuni casi, ad esempio è stato raggiunto il, dove il video può essere rimossi prima di tre giorni è stato raggiunto il limite di capacità.
  
([Torna all'inizio](office-365-video-networking-faq.md))
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a>È possibile memorizzare nella cache i video in locale per la riproduzione più veloce?

Sì. Office 365 non impedisce l'utilizzo di una rete CDN locale o un proxy di memorizzazione nella cache per inserire video o di altro contenuto di Office 365 nella rete locale per poter accedere più rapidamente. Esistono diversi modi per implementare una soluzione di memorizzazione nella cache locale nella rete, il metodo più comune consiste nell'utilizzare una soluzione proxy che memorizza nella cache contenuto in locale. Una volta un proxy o CDN private sono memorizzati i frammenti video e i manifesti, le richieste successive per i file che instradano tramite il proxy o privata CDN sono estratti dalla cache locale e non estratto da un percorso internet. Prendere in considerazione la larghezza di banda di rete, capacità e concorrenza la riproduzione del video durante la pianificazione di una soluzione simile al seguente.
  
([Torna all'inizio](office-365-video-networking-faq.md))
  
## <a name="how-videos-are-encrypted-and-secured"></a>Come video è crittografate e protette?

Video di Office 365 SA il livello di importanza è per proteggere i dati e privato. [Office 365 Trust Center](https://products.office.com/business/office-365-trust-center-cloud-computing-security) descrive la conferma dell'impegno per la privacy e sicurezza del contenuto. Con la riproduzione video, è importante per un'esperienza ottimale, la velocità è tuttavia, non compromettere relative alla protezione o sulla privacy per ricevere velocità. Ecco come è contenere velocità, sicurezza e privacy.
  
Quando un utente all'interno dell'organizzazione carica un nuovo video, che il video è codifica intermedia, crittografati con la crittografia AES-128 e archiviato in servizi di supporto di Azure. Ciò significa che i video vengono crittografati in transito e statici.
  
Quando qualcuno all'interno dell'organizzazione tentativo in un nuovo video, è procedere come segue:
  
1. Chiedere a SharePoint Online se dispongono dell'autorizzazione per visualizzare il video.

2. SharePoint Online utilizza le autorizzazioni per i file per determinare se la persona può guardare il video.

3. Se si sta consentiti, SharePoint Online consente di recuperare un token da Azure per fornire il lettore video.

4. Il lettore video utilizza quindi il token per richiedere la chiave di decrittografia di Azure.

5. Con la chiave di decrittografia a disposizione il lettore video è in grado di eseguire il flusso video.

![Office 365 La riproduzione del Video](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
([Torna all'inizio](office-365-video-networking-faq.md))
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a>Che cosa sono i requisiti per la riproduzione Video di Office 365?

Sistemi operativi supportati per Office 365 Video e web browser solo gli stessi requisiti SharePoint Online in [requisiti di sistema di Office 365](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45). In base al quale web e il sistema operativo è la configurazione del browser consente di determinare le esigenze specifiche del lettore video. Di seguito viene ulteriori informazioni sui [requisiti di riproduzione dei video](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6).
  
([Torna all'inizio](office-365-video-networking-faq.md))
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a>Impossibile ottenere Office 365 video funzioni correttamente, dove è consigliabile iniziare?

Risoluzione dei problemi di connettività a Office 365 Video comporta la risoluzione dei problemi di rete, le ISP(s) e la configurazione di Office 365. Il primo punto di partenza è il dashboard di integrità del servizio. Verranno indicate di Office 365 Video è stato rilevato un problema o non. Se tutto il contenuto accattivante non esiste, ecco alcune risorse aggiuntive che consentono di.
  
- Verificare che sia possibile connettersi all' [endpoint di rete necessario per il Video di Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

- Verificare la connettività di rete, utilizzare la [Guida alla risoluzione dei problemi di rete di Office 365](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).

- Vedere le [procedure consigliate per l'utilizzo di Office 365 con reti lente](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166).

- Visualizzare [la Guida sulla configurazione di Office 365 Video](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).

([Torna all'inizio](office-365-video-networking-faq.md))
  
## <a name="office-365-video-resources"></a>Risorse Video di Office 365

Valutare l'argomento e lasciare un commento per confermare se si risponde alle domande o se si sta cercando ancora risposte. Ecco alcuni dei nostri ad altre risorse che consentono di distribuire e utilizzare i Video di Office 365:
  
[Informazioni sulla configurazione di Office 365 Video](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).
  
[Soddisfare Video di Office 365](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)
  
[Creare e gestire un canale in Office 365 Video](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  
[Gestire il portale di Office 365 Video](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da)
  
[Formati video che lavorano in Office 365 Video](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
([Torna all'inizio](office-365-video-networking-faq.md))
  
Questo è un collegamento breve che è possibile utilizzare il ritorno:[https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)
