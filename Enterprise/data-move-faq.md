---
title: Domande frequenti sullo spostamento dati
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 9/14/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
description: Di seguito sono le risposte alle domande generali su spostamento dei dati di base in un nuovo geo datacenter.
ms.openlocfilehash: 40f83ee94aaa7c919f08d91d888ff131da02df67
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541284"
---
# <a name="data-move-general-faq"></a>Domande frequenti sullo spostamento dati

Di seguito sono le risposte alle domande generali su spostamento dei dati di base in un nuovo geo datacenter.
  
 **D. come è verificare che i dati dei clienti sono sicuro durante lo spostamento e che è possibile non verificarsi tempi di inattività?**
  
Spostamenti di dati r. sono un'operazione di servizio back-end con un impatto minimo per gli utenti finali. Sono elencate le funzionalità che possono essere influenzate in [durante e dopo la migrazione dei dati](during-and-after-your-data-move.md). È conforme a [Microsoft Online Services Service Level Agreement (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) per garantire la disponibilità in modo che i clienti necessari per preparare o per monitorare durante lo spostamento. 
  
Tutti i servizi di Office 365 eseguono le stesse versioni nei Data Center, in modo che è possibile essere certi di funzionalità coerente. Il servizio è completamente supportato nel corso del processo.
  
 **D: qual è l'impatto di avere diversi servizi che si trovano in diverse geos?**
  
R. per alcuni clienti esistenti e clienti nel corso del processo di spostamento, alcuni dei servizi di Office 365 può trovarsi in geos diversi. I servizi eseguiti dalle altre e sono disponibili Nessun impatto sugli utenti se questo fosse il caso.
  
 **D. nuovi clienti di Office 365 eseguire il provisioning automatico nel nuovo geos di datacenter?**
  
R. Sì. Una volta è disponibile un nuovo livello geografico datacenter, nuovo Office 365 per i clienti aziendali che selezionare un paese idoneo per il nuovo livello geografico come proprio paese durante l'abbonamento avranno i dati di base ospitati il nuovo livello geografico datacenter.
  
 **D. dove sono i dati si trova?**
  
Si pubblica il percorso di datacenter geos, centri dati e la posizione dei dati dei clienti nella [mappa datacenter interattiva di Office 365 ](https://o365datacentermap.azurewebsites.net). A partire da 1 agosto, sarà possibile verificare il percorso dei dati dei clienti statici tramite la sezione posizione dei dati del profilo dell'organizzazione nell'interfaccia di amministrazione di Office 365.
  
 **D. spostare i clienti esistenti di Office 365 per il nuovo geos datacenter?**
  
A. idonei Office 365 i clienti possono chiedere disporre i dati di base spostati geos nuovo. Gli utenti devono inviare una richiesta prima della scadenza per i geo per partecipare. 
  
 **D. quali sono quindi idonei per richiedere uno spostamento?**
  
Office 365 esistente A. commerciali ai clienti che ha selezionato un paese idoneo per il nuovo livello geografico datacenter saranno in grado di richiedere uno spostamento. 
  
 **D. quando sarà in grado di richiedere uno spostamento?**
  
R. il periodo di richiesta verrà annunciato nella pagina [come richiedere la migrazione dei dati](request-your-data-move.md) . 
  
 **D. come è possibile richiedere verrà spostato?**
  
R. clienti idonei verranno visualizzata una pagina nel proprio [Portale di amministrazione di Office 365](https://portal.office.com/). Per istruzioni su come richiedere uno spostamento, vedere [come richiedere la migrazione dei dati](request-your-data-move.md) . 
  
 **D. è possibile modificare la selezione dopo la richiesta di uno spostamento?**
  
R. It non è possibile per noi rimuovere il processo dopo avere inviato la richiesta.
  
 **D: cosa accade se non è possibile richiedere uno spostamento prima della scadenza.**
  
R. sono in grado di accettare le richieste verrà spostato dopo la scadenza di ogni livello geografico.
  
 **Q. se desidera spostare i dati per ottenere migliori prestazioni di rete?**
  
Per un datacenter di Office 365 non è una garanzia per migliorare le prestazioni di rete. Esistono molti componenti che influiscono sulle prestazioni della rete tra l'utente finale e il servizio Office 365 e fattori. Per ulteriori informazioni su questa e ottimizzazione delle prestazioni, vedere [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](network-planning-and-performance.md).
  
 **D tutti i servizi di spostare i dati nello stesso giorno?**
  
R. i servizi non spostano i dati alla stessa ora. Ogni servizio verrà spostato in modo indipendente e sarà probabilmente spostare i dati in momenti diversi.
  
 **D. è possibile scegliere se desidero che i dati da spostare?**
  
R. i clienti non sono possibile selezionare una data specifica, è possibile posticipare il passaggio ed è possibile condividere una data specifica o tempistica per gli spostamenti.
  
 **D. è possibile condividere quando i dati verranno essere spostate?**
  
Spostamenti di dati r. sono un'operazione di back-end con un impatto minimo per gli utenti finali. La complessità, precisione e scala in cui è necessario eseguire gli spostamenti di dati all'interno di un ambiente gestito a livello globale e automatizzato ci impediscono condivisione quando uno spostamento di dati è previsto per il completamento per il tenant o qualsiasi altro tenant singolo. Clienti riceveranno una conferma nell'interfaccia di messaggio per ogni servizio partecipano quando è completata la migrazione dei dati. 
  
 **D: cosa succede se gli utenti accedono servizi mentre si muove i dati?**
  
R. vedere [durante e dopo la migrazione dei dati](during-and-after-your-data-move.md) per un elenco completo delle funzionalità che potrebbe essere limitato durante parti dello spostamento dei dati per ogni servizio. 
  
 **D. come è possibile verificare se che lo spostamento è stato completo?**
  
R. guardare l'interfaccia di Office 365 messaggio di conferma che lo spostamento dei dati del servizio ogni è stato completo. Quando vengono spostati i dati di ogni servizio, verranno inviati un avviso di completamento in modo che si otterranno tre notifiche di completamento: 1 per Exchange Online, SharePoint Online e Skype Business online.
  
Se viene visualizzata eventuali problemi dopo lo spostamento, contattare il [Supporto per Office 365](https://go.microsoft.com/fwlink/p/?LinkID=522459) per ottenere assistenza. 
  
 **D. quali dati per Office 365 vengono archiviati nel nuovo geos di datacenter?**
  
R. Se disposizioni un cliente il tenant in una nuova geos di Data Center, Microsoft archivia i dati dei clienti seguenti statici all'interno di geo:
  
- Contenuto delle cassette postali Exchange Online (corpo del messaggio di posta elettronica, le voci di calendario e il contenuto degli allegati di posta elettronica)
    
- Contenuto del sito SharePoint Online e i file archiviati all'interno del sito, incluso il contenuto di Project Online e l'accesso in linea.
    
Inoltre, questi dati non vengono replicati di fuori di geo.
  
 **D: perché un cliente di Office 365 in uno dei nuovi geos di Data Center, ma quando è iscritti, è possibile selezionare un paese diverso. Come posso essere spostato nei nuovi geo di datacenter?**
  
R. non è purtroppo possibile modificare il paese associato il tenant. In realtà, è necessario creare un nuovo tenant di Office 365 con una nuova sottoscrizione e spostare manualmente gli utenti e i dati al nuovo tenant.
  
 **D. esserci le modifiche apportate in pagamento?**
  
R. nella maggior parte dei casi sono state apportate modifiche che i clienti verranno visualizzato sul proprio istruzione fatturazione.
  
Microsoft verrà addebitare tutti i clienti australiani di Office 365 un importo aggiuntivo uguale a GST australiano per servizi di Office 365 ed emetteranno fatture fiscali. Poiché GST australiano a soggetto di forniture e servizi forniti e offerte in Australia, si verificherà la modifica.
  
 **D: cosa succede se si è in corso la migrazione dei dati di posta elettronica durante lo spostamento di Exchange Online per Office 365?**
  
R. Se migrazione della posta elettronica sono in corso, verranno annullate qualsiasi delle singole cassette postali che attualmente vengono migrate durante lo spostamento tenant completa e la migrazione delle cassette postali si riavvierà automaticamente dopo aver aggiunto il tenant i datacenter di destinazione.
  
 **D. dopo i dati vengono spostati da geo di datacenter precedenti, questa viene rimossa da tali centri dati?**
  
R. Sì, i dati precedenti verranno eliminati dopo un periodo di tempo.
  
 **D. è pilota alcuni utenti?**
  
R. quando il tenant di Office 365 viene spostato in un nuovo livello geografico datacenter, tutti gli utenti vengono spostati in una sola volta. È possibile creare un tenant di prova separato per verificare la connettività, ma non è possibile combinare il tenant di prova in alcun modo con tenant esistente.
  
 **Verrà inviata una notifica Q. come utente viene avvisato sullo spostamento e gli utenti alla propria azienda?**
  
R. utilizzeremo il centro messaggi di Office 365, è visibile a tutti gli utenti con le autorizzazioni di amministratore in Office 365.
  
 **D: non desidero attendere Microsoft spostare i dati. È possibile solo crea un tenant nuovo e spostare personale?**
  
R. Sì, tuttavia il processo non saranno come semplice come se fosse Microsoft per eseguire lo spostamento dei dati.
  
Se si crea un tenant nuovo dopo il nuovo livello geografico datacenter è disponibile, il nuovo tenant verrà ospitato in geo nuovo. Questo nuovo tenant è completamente separato dalla precedente tenant e è responsabile per spostare tutte le cassette postali utente, il contenuto del sito, i nomi di dominio e altri dati. Si noti che non è possibile spostare il nome del tenant dal uno tenant a altro. È consigliabile attendere il programma di spostamento fornito da Microsoft come si verrà occuparsi di spostamento di tutte le impostazioni, dati e sottoscrizioni per gli utenti.
  
 **D: l'utente non è pronto per essere spostato, è possibile selezionare una data move specifici?**
  
R. It non è possibile per modificare quando verranno spostati i dati dei clienti di ciascun servizio. Spostamenti di dati sono un'operazione di back-end con un impatto minimo per gli utenti finali.
  
 **D. la mia dati relativi ai clienti già è stata spostata in un nuovo livello geografico datacenter. Spostarsi all'indietro?**
  
R. questo non è possibile. I clienti che siano stati spostati su nuovi centri dati geo non possono essere spostati. Come cliente in qualsiasi livello geografico, si verificherà la stessa qualità del servizio, prestazioni e controlli di sicurezza come descritto in precedenza.
  
 **D il nuovo geos datacenter utilizzare le stesse versioni di servizi di Office 365 come il geos datacenter corrente?**
  
R. Sì.
  
 **Tenant verrà Office 365 d: ospitate in datacenter nuovo essere disponibili per gli utenti di fuori del paese?**
  
R. Sì. Microsoft gestisce una rete globale di grandi dimensioni con connessioni Internet pubblica nelle posizioni più di 50 23 paesi in tutto il mondo con peering accordi con più di 1.500 provider di servizi Internet (ISP). Gli utenti saranno in grado di accedere i Data Center da ovunque si trovino in Internet.
  

