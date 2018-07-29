---
title: Guida sulla fine del supporto di SharePoint Server 2007
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
f1_keywords:
- vsemail
- MS_WSS_DirectoryManagement
- MS_WSS_ConfigEmail
- globalemailconfig
- configssc
- AppDefToBDC
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- OFU120
- SPS150
- OSU140
- WSU120
- OSR120
- SPO160
- PJW120
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: ba124775-d5c0-4d68-b88d-8458ad4c3717
description: In 10 ottobre 2017, supporto terminata per SharePoint Server 2007. In questo articolo per conoscere le opzioni di aggiornamento, risoluzione dei problemi, procedure consigliate, i requisiti di sistema, operazioni di aggiornamento e come ottenere assistenza da Microsoft Partners.
ms.openlocfilehash: b548e7623a72d57793c18409a80506bb832df858
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169798"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>Guida sulla fine del supporto di SharePoint Server 2007

In **10 ottobre 2017**, Microsoft Office SharePoint Server 2007 stata raggiunta la fine del supporto tecnico. Se si non iniziata la migrazione da SharePoint Server 2007 a Office 365 o una versione più recente di SharePoint Server locale, è ora per iniziare la pianificazione. In questo articolo vengono illustrati le risorse per facilitare la migrazione dei dati in SharePoint Online o un aggiornamento di SharePoint Server locale. 
  
## <a name="what-does-end-of-support-mean"></a>Quali fine consente di supporto Media?

SharePoint Server, come quasi tutti i prodotti Microsoft, dispone di un ciclo di vita del supporto durante il quale Microsoft sono disponibili nuove funzionalità, correzioni, correzioni rapide per la sicurezza e così via. Questo ciclo di vita dura in genere per 10 anni dalla data di rilascio iniziale del prodotto e fine di questo ciclo di vita è noto come fine del prodotto del supporto tecnico. Alla fine del supporto Microsoft non fornisce più:
  
- Supporto tecnico per i problemi che possono verificarsi;
    
- Correzioni degli errori per i problemi che vengono individuate e che possono influenzare la stabilità e l'usabilità di server.
    
- Le patch di protezione per le vulnerabilità che vengono individuate e che potrebbe essere vulnerabile ad attacchi di violazioni della protezione, il server e 
    
- Aggiornamenti di fuso orario.
    
Tuttavia la farm di SharePoint Server 2007 saranno ancora funzionante dopo ottobre 10, 2017, nessun ulteriori aggiornamenti, patch, o correzioni verranno inviate per il prodotto (incluse le patch correzioni) e supporto Microsoft verrà sono completamente spostate allo scopo di supporto di versioni più recenti del prodotto. Poiché l'installazione verrà non è più supportato o un'applicazione di patch, come fine del supporto approcci si deve eseguire l'aggiornamento del prodotto o la migrazione dei dati importanti.
  
> [!TIP]
> Se non sono già pianificato per l'aggiornamento o la migrazione, vedere: [Opzioni di migrazione di SharePoint 2007 da considerare](sharepoint-2007-migration-options.md)per alcuni esempi di cui iniziare. È inoltre possibile cercare [Partner Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) che possono essere utili per l'aggiornamento o la migrazione di Office 365 (o entrambe). 
  
Per ulteriori informazioni sui server di Office 2007 sta per raggiungere la fine del supporto tecnico, vedere [pianificare l'aggiornamento per i server di Office 2007](https://support.office.com/article/4e5eab5f-05db-4627-9e17-421a6bf89606.aspx).
  
## <a name="what-are-my-options"></a>Che cosa sono le opzioni disponibili.

Il primo punto deve essere il [sito del ciclo di vita del prodotto](https://go.microsoft.com/fwlink/?linkid=843148). Se si dispone di un prodotto Microsoft locale che sia la durata, è necessario controllare per la fine del periodo supportato in modo che un anno o un modo out - o purché le migrazioni richiedono in genere - è possibile pianificare l'aggiornamento o le migrazioni. Quando si sceglie il passaggio successivo, può essere utile per pensare in termini di cosa potrebbe è sufficiente, integrazione e procedure per quanto riguarda la funzionalità del prodotto. Di seguito è riportato un esempio:
  
|**Buone**|**Migliore**|**Elevate**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||Ambiente ibrido di SharePoint  <br/> |SharePoint Server 2016  <br/> |
|||Ambiente ibrido di SharePoint  <br/> |
   
Se si sceglie ricordare opzioni sul valore minimo della scala (adeguata), è necessario iniziare a pianificare l'aggiornamento molto subito dopo la migrazione da SharePoint Server 2007 è state complete. (fine del supporto per SharePoint Server 2007 è 10 ottobre 2017. Si suggerisce che queste date sono soggetti a modifiche e controllare il [ciclo di vita del prodotto sito](https://support.microsoft.com/en-us/lifecycle)).
  
## <a name="where-can-i-go-next"></a>Dove posso passare successivo?

SharePoint Server può essere installato in locale nel server oppure è possibile utilizzare SharePoint Online, che è un servizio in linea che fa parte di Microsoft Office 365. È possibile scegliere di:
  
- Eseguire la migrazione a SharePoint Online
    
- Aggiornamento di SharePoint Server in locale
    
- Eseguire entrambe le precedenti
    
- Implementare una soluzione [ibrida di SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) 
    
Tenere presente nascosti costi associati alla gestione di una server farm in futuro, gestione o la migrazione delle personalizzazioni e aggiornare l'hardware da cui dipende il Server di SharePoint. Disporre di una farm di SharePoint Server locale è gratificante in caso di necessità; in caso contrario, se si esegue la farm in SharePoint Server legacy, senza personalizzazione elevata, possono utilizzare una migrazione pianificata con SharePoint Online.
  
> [!IMPORTANT]
> Non esiste un'altra opzione se il contenuto di SharePoint 2007 viene utilizzato raramente. Alcuni amministratori SharePoint possibile [creare una sottoscrizione a Office 365](https://go.microsoft.com/fwlink/?linkid=843152), impostare un nuovo sito di SharePoint Online e poi rimuovere dalla SharePoint 2007, in modo corretto, accettando solo i documenti più importanti per i siti di SharePoint Online aggiornati. Da quest'ultimo, dati possono essere scaricati dal sito di SharePoint 2007 in archivi. Fornire pensato per gli utenti che utilizzano dati di installazione di SharePoint 2007. È possibile soluzioni per risolvere questo problema! 
  
|**SharePoint Online (SPO)**|**SharePoint Server in locale**|
|:-----|:-----|
|Costi elevati in tempo (piano / esecuzione / verifica)  <br/> |Costi elevati in tempo (piano / esecuzione / verifica)  <br/> |
|Ridurre il costo dei fondi (nessun acquisti hardware)  <br/> |Costo maggiore fondi (hardware + sviluppatori / admins)  <br/> |
|Costo occasionale nella migrazione  <br/> |Costo occasionale ripetuto per la migrazione futura  <br/> |
|Basso costo totale di proprietà / manutenzione  <br/> |Elevata costo totale di proprietà / manutenzione  <br/> |
   
Quando esegue la migrazione a Office 365, lo spostamento occasionale avrà un costo pesante all'inizio, mentre si sta organizzazione dei dati e stabilire gli elementi da eseguire nel cloud e gli elementi da tralasciare. Tuttavia, gli aggiornamenti sarà automatici da quel momento, non è più necessario gestire gli aggiornamenti software e hardware e il tempo della farm deve essere eseguito da Microsoft Service Level Agreement ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)).
  
### <a name="migrate-to-sharepoint-online"></a>Eseguire la migrazione a SharePoint Online

Assicurarsi che SharePoint Online include tutte le funzionalità che è necessario esaminare la descrizione del servizio associato. Ecco il collegamento a tutte le descrizioni dei servizi di Office 365:
  
[Descrizioni dei servizi di Office 365](https://go.microsoft.com/fwlink/?linkid=272060)
  
Non è possibile eseguire la migrazione da SharePoint 2007 a SharePoint Online, diretto la migrazione a SharePoint Online potrebbe essere eseguita manualmente. Se esegue l'aggiornamento a SharePoint Server 2013 o SharePoint Server 2016, la migrazione può inoltre comportare utilizzando l'API di migrazione di SharePoint (per trasferire le informazioni in OneDrive for Business, ad esempio).
  
|**Pro online**|**Ezio online**|
|:-----|:-----|
|Microsoft fornisce hardware SharePoint Online e amministrazione di tutti i componenti hardware.  <br/> |Funzionalità disponibili possono essere diverse tra SharePoint Server locali e SharePoint Online.  <br/> |
|L'amministratore globale dell'abbonamento e possono assegnare amministratori a siti di SharePoint Online.  <br/> |Alcune azioni disponibili per un amministratore della Farm in SharePoint Server locale non esistono (o non sono necessarie) incluso il ruolo di amministratore di SharePoint in Office 365.  <br/> |
|Microsoft applica patch, consente di risolvere e gli aggiornamenti software e hardware sottostante.  <br/> |Perché non è possibile accedere al file system sottostante nel servizio, alcune personalizzazioni sono limitate.  <br/> |
|Microsoft pubblica i [Contratti di servizio](https://go.microsoft.com/fwlink/?linkid=843153) e lo sposta rapidamente di risolvere i problemi di livello di servizio.  <br/> |Backup e ripristino e altre opzioni di ripristino saranno eseguiti automaticamente dal servizio in SharePoint Online - backup vengono sovrascritti se non viene utilizzati.  <br/> |
|Testing della protezione e ottimizzazione delle prestazioni del server vengono eseguite in modo continuativo nel servizio da Microsoft.  <br/> |Modifica dell'interfaccia utente e altre funzionalità vengono installate per il servizio e potrebbe essere necessario essere attivati o disattivati SharePoint.  <br/> |
|Office 365 soddisfi numerosi standard di settore: [Office 365 conformità](https://go.microsoft.com/fwlink/?linkid=843165).  <br/> |[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) assistenza per la migrazione è limitata.  <br/> Gran parte dell'aggiornamento sarà manuale o mediante l'API di migrazione di SharePoint Online descritto in [SharePoint Online e Roadmap dei contenuti migrazione OneDrive](https://go.microsoft.com/fwlink/?linkid=843184).  <br/> |
|Tecnici del supporto Microsoft né dipendenti nel centro dati admin accesso illimitato alla sottoscrizione.  <br/> |Può esistere costi aggiuntivi se infrastruttura hardware deve essere aggiornato per supportare la versione più recente di SharePoint o se è necessaria per l'aggiornamento di una farm secondaria.  <br/> |
|Partner possono essere utili a singola occorrenza di migrazione dei dati in SharePoint Online.  <br/> ||
|Prodotti online vengono aggiornati automaticamente tra il servizio non significa che anche se potrebbe rendere obsoleti i funzionalità, non esiste alcun true fine del supporto tecnico.  <br/> ||
   
Se si è deciso di creare un nuovo sito di Office 365 e verranno manualmente migrare dati è sufficiente, è possibile esaminare il diritto di opzioni di Office 365:
  
[Opzioni di piani di Office 365](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Aggiornamento di SharePoint Server in locale

Non è possibile in passato per ignorare le versioni in SharePoint gli aggiornamenti, almeno non alla data di rilascio di SharePoint Server 2016. Di conseguenza, gli aggiornamenti di passare in serie:
  
|||
|:-----|:-----|
||SharePoint 2007 | SharePoint Server 2010 | SharePoint Server 2013 | SharePoint Server 2016 |
   
Per rendere l'intero percorso da SharePoint 2007 a SharePoint Server 2016 comporta un investimento significativo di tempo e implica un costo in termini di hardware aggiornata (tenere presente che è necessario aggiornare anche SQL Server), software e l'amministrazione. Le personalizzazioni saranno necessario aggiornata o abbandonati, in base all'importanza della caratteristica.
  
> [!NOTE]
> È possibile gestire la farm di SharePoint 2007 fine del ciclo di vita, installazione di una farm di SharePoint Server 2016 nel nuovo hardware (in modo che la farm distinte eseguire side-by-side) e quindi pianificare ed eseguire una migrazione manuale del contenuto (per il download e nuovamente il caricamento del contenuto, per esempio). Tenere conto di alcuni dei problemi individuati di spostamento manuale (ad esempio, si sposta di documenti, sostituendo l'ultimo account modificato con l'alias dell'account di cui eseguire lo spostamento manuale) e il lavoro che deve essere eseguito anticipo (ad esempio ricreare i siti, siti secondari, autorizzazioni ed elenco strutture). Anche questa è necessario prendere in considerazione i dati che è possibile spostare in archiviazione, o non è più necessario, un'azione che può ridurre l'impatto della migrazione.
  
In entrambi i casi, eliminare il prima dell'ambiente di aggiornamento. Essere farm esistente è funzionante prima dell'aggiornamento e (con certezza) prima rimuovere le autorizzazioni! 
  
Ricordarsi di esaminare i **percorsi di aggiornamento supportati e non supportati**: 
  
- 
  [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
Se si dispone **delle personalizzazioni**, è essenziale che avere un piano dell'aggiornamento per ogni passaggio nel percorso di migrazione: 
  
- [SharePoint 2007](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**Pro locale**|**Ezio locale**|
|:-----|:-----|
|Controllo completo di tutti gli aspetti della Farm di SharePoint, da hardware del server backup.  <br/> |Tutte le correzioni e le interruzioni sono assume la responsabilità dell'organizzazione (possano utilizzare Microsoft Support pagamento se il prodotto non è alla fine del supporto):  <br/> |
|Il set completo di funzionalità del SharePoint Server locale con l'opzione per la connessione della farm locale in una sottoscrizione a SharePoint Online tramite ibrida.  <br/> |L'aggiornamento, patch, correzioni rapide per la protezione e tutti i manutenzione di SharePoint Server gestiti locale.  <br/> |
|Accesso completo per la personalizzazione maggiore.  <br/> |[Standard di conformità supportati da Office 365](https://go.microsoft.com/fwlink/?linkid=843165) deve essere configurati manualmente in locale.  <br/> |
|Test di sicurezza e ottimizzazione delle prestazioni del server, eseguite le locale (è sotto il controllo).  <br/> |Office 365 può rendere disponibili funzionalità di SharePoint Online che non interagiscono con SharePoint Server in locale  <br/> |
|Partner possono essere utili per la migrazione dei dati alla versione successiva di SharePoint Server (e anche oltre).  <br/> |I siti di SharePoint Server non utilizzeranno automaticamente i certificati [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) come indicato in SharePoint Online.  <br/> |
|Controllo completo di convenzioni di denominazione, il backup e ripristino e altre opzioni di ripristino in SharePoint Server locale.  <br/> |SharePoint Server in locale è sensibile cicli di vita del prodotto.  <br/> |
   
### <a name="upgrade-resources"></a>Risorse di aggiornamento

Per iniziare è necessario sapere che siano soddisfatti i requisiti hardware e software, quindi seguire metodi di aggiornamento supportati.
  
- **Requisiti hardware e software per**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [2016 di SharePoint Server](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **Limiti software statici e configurabili per**: 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [2016 di SharePoint Server](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **Panoramica del processo di aggiornamento per**: 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [2016 di SharePoint Server](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Creare una soluzione ibrida di SharePoint tra SharePoint Online e locale

Se la risposta alle proprie esigenze di migrazione è un punto qualsiasi tra self-control offerte da locali e il costo inferiore di proprietà offerte da SharePoint Online, è possibile connettere SharePoint Server 2013 o 2016 farms in SharePoint Online tramite ibridi. [Informazioni sulle soluzioni ibride di SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
Se si decide di un farm di SharePoint Server ibrido utilizzeranno l'azienda, acquisire familiarità con i tipi di ibride e su come configurare la connessione tra la farm di SharePoint locale e la sottoscrizione a Office 365 esistenti.
  
Un modo efficace per verificare il funzionamento è mediante la creazione di un [ambiente di sviluppo e di testing di Office 365](https://go.microsoft.com/fwlink/?linkid=843152). Una volta che si dispone di una versione di valutazione o acquistato una sottoscrizione a Office 365, sarà in come per la creazione le raccolte siti, siti Web e raccolte documenti in SharePoint Online in cui è possibile eseguire la migrazione dei dati (uno manualmente, dall'uso dell'API di migrazione, oppure - se si desidera eseguire la migrazione di personale Contenuto del sito a OneDrive for Business - tramite la procedura guidata ibrida).
  
> [!NOTE]
> Ricordare che la farm di SharePoint 2007 dovrà essere aggiornato, locali, a SharePoint Server 2013 o SharePoint Server 2016 per utilizzare l'opzione ibrida 
  
## <a name="related-topics"></a>Argomenti correlati

[Risolvere i problemi e riprendere l'aggiornamento (Office SharePoint Server 2007)](https://go.microsoft.com/fwlink/?linkid=843192)
  
[Risoluzione dei problemi di aggiornamento (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=843194)
  
[Risolvere i problemi relativi all'aggiornamento dei database in SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=843195)
  
[Ricerca per Microsoft Partners al fine di facilitare l'aggiornamento](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Risorse che consentono di eseguire l'aggiornamento da Office 2007 ai server e client](upgrade-from-office-2007-servers-and-products.md)
  

