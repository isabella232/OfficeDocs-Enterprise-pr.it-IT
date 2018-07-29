---
title: Aggiornamento da SharePoint 2010
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 2/2/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
description: SharePoint 2010 e SharePoint Server 2010 sono quasi fine del supporto tecnico. Utilizzare questo articolo come guida per l'aggiornamento a SharePoint Online o una versione più recente di SharePoint Server locale.
ms.openlocfilehash: c88c6010aa398d8076fce59976bf6f5c0aa1a743
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169868"
---
# <a name="upgrading-from-sharepoint-2010"></a>Aggiornamento da SharePoint 2010

In 13 Oct 2020, Microsoft Office SharePoint Server 2010 raggiunge fine del supporto tecnico. In questo articolo vengono illustrati le risorse per facilitare la migrazione dei dati di SharePoint Server 2010 esistenti in SharePoint Online o un aggiornamento di SharePoint Server locale.
  
## <a name="what-is-end-of-support"></a>Che cos'è fine del supporto?

Quando il software di SharePoint Server 2010 e SharePoint Foundation 2010 raggiunta la fine del ciclo di vita di supporto (il tempo durante il quale Microsoft sono disponibili nuove funzionalità, correzioni, correzioni rapide per la sicurezza e così via) si tratta 'fine del software del supporto ", oppure In alcuni casi, il relativo 'pensionistico". Al termine di supporto o EOS di un prodotto, nothing effettivamente arresta o si in Microsoft Word. Tuttavia, alla fine del supporto del software, Microsoft non fornisce più:
  
- Supporto tecnico per i problemi che possono verificarsi;
    
- Correzioni degli errori per i problemi che vengono individuate e che possono influenzare la stabilità e l'usabilità di server.
    
- Le patch di protezione per le vulnerabilità che vengono individuate e che potrebbe essere vulnerabile ad attacchi di violazioni della protezione, il server
    
- Aggiornamenti di fuso orario.
    
Ciò significa, ci sarà senza ulteriori aggiornamenti, patch, o correzioni verranno inviate per il prodotto (incluse le patch correzioni) e supporto Microsoft verrà sono completamente spostati gli sforzi compiuti supporto per le versioni più recenti. Quando si avvicina la fine del supporto di SharePoint Server 2010, è consigliabile sfruttare opportunità per ridurre i dati che non sono più necessari prima di eseguire l'aggiornamento del prodotto e/o la migrazione dei dati importanti.
  
> [!NOTE]
> Un ciclo di vita del software è in genere dura per 10 anni dalla data di rilascio iniziale del prodotto. È possibile cercare [Partner Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) che possono aiutare con l'aggiornamento alla versione successiva del software o con la migrazione di Office 365 (o entrambi). Essere che essere a conoscenza della fine del periodo di supporto alle tecnologie sottostanti critiche, soprattutto della versione di SQL server che è utilizzato con SharePoint. 
  
## <a name="what-are-my-options"></a>Che cosa sono le opzioni disponibili.

Verificare innanzitutto la data in cui il supporto termina il [ciclo di vita del prodotto sito](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202010). Successivamente, è necessario pianificare del tempo di migrazione o l'aggiornamento a conoscenza di questa data. Tenere presente che il prodotto *non smettere di funzionare* in data elencati ed è possibile continuare il suo utilizzo, ma che, dopo l'installazione non è più essere corretto dopo tale data, è consigliabile una strategia che consentirà più fluide transizione alla versione successiva del prodotto. 
  
Questa matrice consente di tracciare un corso per la migrazione delle funzionalità del prodotto e i dati utente:
  
|**fine del supporto del prodotto**|**Buone**|**Elevate**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||Ambiente ibrido di SharePoint  <br/> |SharePoint Server 2016 (locale)  <br/> |
|||Ricerca ibrida Cloud di SharePoint  <br/> |
   
Se si sceglie opzioni sul valore minimo della scala (opzioni), è necessario iniziare la pianificazione per l'aggiornamento di un'altra subito dopo il completamento della migrazione da SharePoint Server 2010. (fine del supporto per SharePoint Server 2010 e SharePoint Foundation 2010 sia stata pianificata 13 Oct 2020, ma *tenere* sempre necessario controllare il [ciclo di vita del prodotto sito](https://support.microsoft.com/en-us/lifecycle) per le date più precisione!) 
  
## <a name="where-should-i-go-next"></a>Dove devono accedere successivo?

SharePoint Server 2013 e SharePoint Foundation 2013 può essere installato in locale nel server. In caso contrario, è possibile utilizzare SharePoint Online, che è un servizio in linea che fa parte di Microsoft Office 365. È possibile scegliere di:
  
- Eseguire la migrazione a SharePoint Online
    
- Eseguire l'aggiornamento a SharePoint Server o SharePoint Foundation in locale
    
- Eseguire entrambe le precedenti
    
- Implementare una soluzione [ibrida di SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) 
    
Tenere presente nascosti costi associati alla gestione di una server farm in futuro, gestione o la migrazione delle personalizzazioni e aggiornare l'hardware da cui dipende il Server di SharePoint. Tenere presente che preso in considerazione tutti questi, sarà più semplice continuare con l'aggiornamento sul posto. In caso contrario, se si esegue la farm in SharePoint Server legacy senza personalizzazione elevata, potrebbe essere utile una migrazione pianificata con SharePoint Online. È inoltre possibile che in locale decidere gli ambienti SharePoint Server per inserire i dati in SharePoint Online per ridurre il tempo di mantenimento tutti i dati locali prevede la gestione dell'hardware. Potrebbe risultare più economico spostare alcuni dei dati in SharePoint Online.
  
> [!NOTE]
> Gli amministratori di SharePoint può [creare una sottoscrizione a Office 365](https://go.microsoft.com/fwlink/?linkid=843152), impostare un nuovo sito di SharePoint Online e poi rimuovere dalla SharePoint Server 2010, in modo corretto, accettando solo i documenti più importanti per i siti di SharePoint Online aggiornati. Da quest'ultimo, i dati restanti possono essere scaricati dal sito di SharePoint Server 2010 in archivi locali. 
  
|**SharePoint Online (SPO)**|**SharePoint Server in locale**|
|:-----|:-----|
|Costi elevati in tempo (piano / esecuzione / verifica)  <br/> |Costi elevati in tempo (piano / esecuzione / verifica)  <br/> |
|Ridurre il costo dei fondi (nessun acquisti hardware)  <br/> |Costo maggiore fondi (acquisti hardware)  <br/> |
|Costo occasionale nella migrazione  <br/> |Costo occasionale ripetuto per la migrazione futura  <br/> |
|Basso costo totale di proprietà / manutenzione  <br/> |Elevata costo totale di proprietà / manutenzione  <br/> |
   
Quando esegue la migrazione a Office 365, l'unica Sposta sarà un costo pesante nel tempo dedicato di pianificazione, all'inizio (se si sta organizzazione dei dati e stabilire gli elementi da eseguire nel cloud e gli elementi da tralasciare). Tuttavia, dopo la migrazione dei dati, gli aggiornamenti sarà automatici da quel momento, non è più necessario gestire gli aggiornamenti software e hardware e il tempo della farm deve essere eseguito da Microsoft Service Level Agreement ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)).
  
### <a name="migrate-to-sharepoint-online"></a>Eseguire la migrazione a SharePoint Online

Assicurarsi che SharePoint Online offre tutte queste funzionalità che è necessario esaminare la descrizione del servizio associato. Ecco il collegamento a tutte le descrizioni dei servizi di Office 365:
  
[Descrizioni dei servizi di Office 365](https://go.microsoft.com/fwlink/?linkid=272060)
  
Non esiste alcun attualmente un mezzo per cui è possibile direttamente migrare da SharePoint Server 2010 (o SharePoint Foundation 2010) in SharePoint Online, in modo quantità di lavoro è manuale. In questo sarà la possibilità di dati di archiviazione e Comprimi e i siti che non sono più necessari, prima dello spostamento. È possibile archiviare altri dati nell'archivio. È importante ricordare che SharePoint Server 2010 e SharePoint Foundation 2010 non smette di funzionare alla fine del supporto, in modo che gli amministratori possono avere un periodo durante il quale SharePoint è ancora in esecuzione se i clienti dimenticano spostare alcuni dei propri dati.
  
Se si esegue l'aggiornamento a SharePoint Server 2013 o SharePoint Server 2016 e decidere di inserire i dati in SharePoint Online, la migrazione può inoltre comportare utilizzando l' [API di migrazione di SharePoint](https://support.office.com/en-us/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) (per eseguire la migrazione di informazioni a OneDrive for Business). 
  
|**Pro online**|**Ezio online**|
|:-----|:-----|
|Microsoft fornisce hardware SharePoint Online e amministrazione di tutti i componenti hardware.  <br/> |Funzionalità disponibili possono essere diverse tra SharePoint Server locali e SharePoint Online.  <br/> |
|L'amministratore globale dell'abbonamento e possono assegnare amministratori a siti di SharePoint Online.  <br/> |Alcune azioni disponibili per un amministratore della Farm in SharePoint Server locale non esistono (o non sono necessarie) al ruolo di amministratore di SharePoint in Office 365, ma l'amministrazione di SharePoint, sono locali per Amministrazione raccolta siti e la proprietà del sito l'org.  <br/> |
|Microsoft si applica patch, consente di risolvere e gli aggiornamenti hardware e software (inclusi i server SQL in cui SharePoint Online è in esecuzione) sottostanti.  <br/> |Perché non è possibile accedere al file system sottostante nel servizio, alcune personalizzazioni sono limitate.  <br/> |
|Microsoft pubblica i [Contratti di servizio](https://go.microsoft.com/fwlink/?linkid=843153) e lo sposta rapidamente di risolvere i problemi di livello di servizio.  <br/> |Backup e ripristino e altre opzioni di ripristino saranno eseguiti automaticamente dal servizio in SharePoint Online - backup vengono sovrascritti se non viene utilizzati.  <br/> |
|Testing della protezione e ottimizzazione delle prestazioni del server vengono eseguite in modo continuativo nel servizio da Microsoft.  <br/> |Modifica dell'interfaccia utente e altre funzionalità vengono installate per il servizio e potrebbe essere necessario essere attivati o disattivati SharePoint.  <br/> |
|Office 365 soddisfi numerosi standard di settore: [Office 365 conformità](https://go.microsoft.com/fwlink/?linkid=843165).  <br/> |[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) assistenza per la migrazione è limitata.  <br/> Gran parte dell'aggiornamento sarà manuale o mediante l'API di migrazione di SharePoint Online descritto in [SharePoint Online e Roadmap dei contenuti migrazione OneDrive](https://go.microsoft.com/fwlink/?linkid=843184).  <br/> |
|Tecnici del supporto Microsoft né dipendenti nel centro dati admin accesso illimitato alla sottoscrizione.  <br/> |Può esistere costi aggiuntivi se infrastruttura hardware deve essere aggiornato per supportare la versione più recente di SharePoint o se è necessaria per l'aggiornamento di una farm secondaria.  <br/> |
|Partner possono essere utili a singola occorrenza di migrazione dei dati in SharePoint Online.  <br/> |Non tutte le modifiche in SharePoint Online si trovano all'interno del controllo. Dopo la migrazione, le differenze di progettazione nei menu, raccolte e altre caratteristiche temporaneamente possono influire sull'usabilità.  <br/> |
|Prodotti online vengono aggiornati automaticamente tra il servizio non significa che anche se potrebbe rendere obsoleti i funzionalità, non esiste alcun true fine del supporto del ciclo di vita.  <br/> |Non esiste una fine del ciclo di vita del supporto per SharePoint Server (o SharePoint Foundation) e SQL Server sottostante.  <br/> |
   
Se si è deciso di creare un nuovo sito di Office 365 e verranno manualmente migrare dati è sufficiente, è possibile esaminare il diritto di opzioni di Office 365:
  
[Opzioni di piani di Office 365](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Aggiornamento di SharePoint Server in locale

Come dell'ultima versione del prodotto locale SharePoint (SharePoint Server 2016), gli aggiornamenti di SharePoint Server devono passare *in successione* , che indica che non è possibile eseguire l'aggiornamento da SharePoint Server 2010 a SharePoint Server 2016, direttamente. 
  
|||
|:-----|:-----|
||Percorso di aggiornamento seriale *: SharePoint Server 2010 **\>** SharePoint Server 2013 **\>** 2016 di SharePoint Server |
   
Se si sceglie di eseguire l'intero percorso da SharePoint 2010 per SharePoint Server 2016, si avrà ora e la pianificazione. Gli aggiornamenti comportano un costo in termini di hardware aggiornata (tenere presente che è necessario aggiornare anche SQL Server), software e amministrazione. Inoltre, le personalizzazioni potrebbe essere necessario essere aggiornato o persino abbandonati. Assicurarsi di raccogliere note in tutte le personalizzazioni critiche prima di aggiornare la farm di SharePoint Server.
  
> [!NOTE]
> È possibile mantenere la fine del supporto per SharePoint 2010 farm, installazione di una farm di SharePoint Server 2016 nel nuovo hardware (in modo che la farm distinte eseguire side-by-side) e quindi pianificare ed eseguire una migrazione manuale del contenuto (per il download e nuovamente il caricamento del contenuto, per esempio). Non esistono potenziali problemi per questi spostamento manuale (ad esempio documenti provenienti da 2010 con un account modificato ultimo corrente con l'alias dell'account di cui eseguire lo spostamento manuale), e necessario eseguire alcune operazioni anticipo (ricreare i siti, siti secondari, autorizzazioni e strutture di elenco). È consigliabile considerare quali dati per spostarsi all'interno di archiviazione o non è più necessario. Ciò può ridurre l'impatto della migrazione. In entrambi i casi, eliminare il prima dell'ambiente di aggiornamento. Essere farm esistente è funzionante prima dell'aggiornamento e (con certezza) prima rimuovere le autorizzazioni! 
  
Ricordarsi di esaminare i **percorsi di aggiornamento supportati e non supportati**: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
Se si dispone **delle personalizzazioni**, è essenziale che avere un piano dell'aggiornamento per ogni passaggio nel percorso di migrazione: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**Pro locale**|**Ezio locale**|
|:-----|:-----|
|Del controllo completo di tutti gli aspetti della Farm di SharePoint e SQL è, dall'hardware del server backup.  <br/> |Tutte le correzioni e le interruzioni sono assume la responsabilità dell'organizzazione (ma si può condurre pagamento supporto Microsoft se il prodotto non è alla fine del supporto):  <br/> |
|Il set completo di funzionalità del SharePoint Server locale con l'opzione per la connessione della farm locale in una sottoscrizione a SharePoint Online tramite ibrida.  <br/> |L'aggiornamento, le patch, correzioni della protezione, aggiornamenti hardware e tutti manutenzione della farm SQL Server di SharePoint e le relative sono gestiti in locale.  <br/> |
|Accesso completo per le opzioni di personalizzazione maggiore rispetto a SharePoint Online.  <br/> |[Standard di conformità supportati da Office 365](https://go.microsoft.com/fwlink/?linkid=843165) deve essere configurati manualmente in locale.  <br/> |
|Test di sicurezza e ottimizzazione delle prestazioni del server, eseguite le locale (sotto il controllo).  <br/> |Office 365 può rendere disponibili funzionalità di SharePoint Online che non interagiscono con SharePoint Server in locale  <br/> |
|Partner possono essere utili per la migrazione dei dati alla versione successiva di SharePoint Server (e anche oltre).  <br/> |I siti di SharePoint Server non utilizzeranno automaticamente i certificati [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) come indicato in SharePoint Online.  <br/> |
|Controllo completo di convenzioni di denominazione, il backup e ripristino e altre opzioni di ripristino in SharePoint Server locale.  <br/> |SharePoint Server in locale è sensibile cicli di vita del prodotto.  <br/> |
   
### <a name="upgrade-resources"></a>Risorse di aggiornamento

Iniziare confrontando i requisiti hardware e software. Se si non soddisfano i requisiti di base per l'aggiornamento dall'hardware corrente, che possono significare è necessario aggiornare prima i componenti hardware di SQL Server o farm oppure che è possibile decidere di spostare alcuni percentuale dei siti per l'hardware 'sempreverde' di SharePoint Online. Dopo aver effettuato la valutazione, seguire i percorsi di aggiornamento supportati e i metodi.
  
- **Requisiti hardware e software per**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [2016 di SharePoint Server](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **Limiti software statici e configurabili per**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [2016 di SharePoint Server](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **Panoramica del processo di aggiornamento per**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [2016 di SharePoint Server](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-sharepoint-server-on-premises"></a>Creare una soluzione ibrida di SharePoint tra SharePoint Online e SharePoint Server in locale

Un'altra opzione (che potrebbe essere la migliore sia in locale che online ufficio per la migrazione di alcune deve) è un ambiente ibrido, è possibile connettere SharePoint Server 2013 o 2016 farms in SharePoint Online per creare un ambiente ibrido di SharePoint: [informazioni sulle soluzioni ibride di SharePoint ](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
Se si decide di che un farm di SharePoint Server ibrido è l'obiettivo di migrazione, è necessario pianificare i siti e gli utenti si consiglia di spostare in linea e che devono restare in locale. Una revisione e classificazione del contenuto della farm di SharePoint Server (come determinare quali dati sono elevato, medio o basso impatto per l'azienda) possono essere utili per prendere questa decisione. Potrebbe essere che l'unica operazione che si desidera condividere con SharePoint Online sia gli account utente (a) per l'account di accesso e (b) l'indice di ricerca di SharePoint Server - ciò potrebbe non essere chiaro fino a quando non si esamina come vengono utilizzati i siti. Se l'azienda decide in seguito eseguire la migrazione di tutto il contenuto in SharePoint Online, è possibile spostare tutti gli altri account e i dati in linea e rimuovere la farm locale e gestione/amministrazione nella farm di SharePoint viene eseguita tramite Office 365 console da questo punto in poi.
  
Assicurarsi di acquisire familiarità con i tipi di ibride e su come configurare la connessione tra la farm di SharePoint locale e la sottoscrizione a Office 365 esistenti.
  
Un modo efficace per verificare il funzionamento di una farm di SharePoint ibrido è mediante la creazione di un [ambiente di sviluppo e di testing di Office 365](https://go.microsoft.com/fwlink/?linkid=843152). Una volta che si dispone di una versione di valutazione o acquistato una sottoscrizione a Office 365, sarà in come per la creazione le raccolte siti, siti Web e raccolte documenti in SharePoint Online in cui è possibile eseguire la migrazione dei dati (uno manualmente, dall'uso dell'API di migrazione, oppure - se si desidera eseguire la migrazione di personale Contenuto del sito a OneDrive for Business - tramite la procedura guidata ibrida).
  
> [!NOTE]
> Ricordare che la farm di SharePoint Server 2010 necessario aggiornato, locali, a SharePoint Server 2013 o SharePoint Server 2016 per utilizzare l'opzione ibrida. SharePoint Foundation 2010 e SharePoint Foundation 2013 non puoi creare connessioni ibrida con SharePoint Online. 
  
## <a name="related-topics"></a>Argomenti correlati

[Risorse per facilitare l'aggiornamento da Office 2007 o 2010 server e client](upgrade-from-office-2010-servers-and-products.md)
  
[Overview of the upgrade process from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493301%28v=office.16%29.aspx)
  
[Procedure consigliate per l'aggiornamento da SharePoint 2010 a SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493305%28v=office.16%29.aspx)
  
[Risolvere i problemi relativi all'aggiornamento dei database in SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=843195)
  
[Ricerca per Microsoft Partners al fine di facilitare l'aggiornamento](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Criterio di manutenzione del prodotto aggiornato per SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493253%28v=office.16%29.aspx)
  
[Criterio di manutenzione del prodotto aggiornato per SharePoint Server 2016](https://technet.microsoft.com/en-us/library/mt782882%28v=office.16%29.aspx)
  

