---
title: Opzioni di migrazione di SharePoint 2007 da prendere in considerazione
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- SPS150
- OSU140
- SPO160
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: 66325a43-5816-4f8e-81ba-c11b71345b7c
description: SharePoint Server 2007 è stata raggiunta la fine del supporto ed è necessario eseguire l'aggiornamento. Utilizzare questo articolo per semplificare la creazione del piano.
ms.openlocfilehash: 4395bc330efd97ae8865e0fb75f93f04fd162ecd
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169878"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>Opzioni di migrazione di SharePoint 2007 da prendere in considerazione

Microsoft SharePoint 2007 e SharePoint Server 2007 sono stata raggiunta la fine del supporto tecnico. È necessario eseguire l'aggiornamento! In questo articolo vengono fornite informazioni sulle opzioni di migrazione.
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>Comuni strategie di aggiornamento per SharePoint

Sono disponibili diversi metodi per l'aggiornamento di un ambiente SharePoint Server. Se si dispone di una farm di Microsoft Office SharePoint Server 2007, di seguito sono riportati alcuni esempi dei metodi di aggiornamento:
  
- Collegamento di database
    
- Aggiornamento side-by-side
    
- Aggiornamento sul posto
    
- Aggiornamento ibrido (sul posto con database scollegati / separato basato sul collegamento di database)
    
- Ibridi di SharePoint (connessione online di SharePoint locali)
    
- Spostare manualmente i dati tra le raccolte siti o raccolte
    
- Creazione guidata FastTrack l'aggiornamento a Office 365 ([advisor distribuzione SharePoint Online](https://aka.ms/spoguidance))
    
- API per la migrazione a SharePoint Online (SPO) in Office 365
    
Le soluzioni migliori automaticamente?
  
La conoscenza di elementi della farm e viene utilizzata per è una potenza strategico per quanto riguarda l'aggiornamento. Il modo in cui gli utenti utilizzano la Farm di SharePoint consentono di scegliere tra le opzioni.
  
> [!TIP]
> Microsoft Office SharePoint Server 2007 dispone di un aggiornamento graduale non descritto di seguito. Per visualizzare un elenco di aggiornamento specifiche del passaggio articoli, vedere [SharePoint Server 2007 fine di supportare Roadmap](sharepoint-2007-end-of-support.md). 
  
Ricordarsi di controllare il [Ciclo di vita del prodotto](https://support.microsoft.com/en-us/lifecycle/search) e i requisiti di sistema per qualsiasi versione di SharePoint sta eseguendo un aggiornamento a. Si tratta in modo sarà presente durante l'aggiornamento successivo sarà necessario (ad esempio, se sospesa in un prodotto legacy come SharePoint Server 2010 per pianificare gli aggiornamenti più, è necessario conoscere la fine del periodo supportato) e per essere certi di avere componenti hardware che supporta il piano. 
  
Se si prevede di eseguire la transizione alcuni o tutti i siti di SharePoint a Office 365 nel Cloud, si tratta di un'ora un segnalibro un collegamento alla [Descrizione del servizio Office 365](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx). Saranno necessarie le descrizioni dei servizi di informazioni sulle funzionalità di SharePoint Online e sulle differenze da SharePoint Server locale. Aggiornare le farm funzionale di Microsoft Office SharePoint Server 2007. Se l'installazione con i siti che non vengono mantenuti, risolverli prima dell'aggiornamento.
  
## <a name="a-note-about-managing-risk"></a>Nota sulla gestione dei rischi

Metodi come 'side-by-side' che sono rilevanti per la combinazione di logica di aggiornamento. Quando si esegue l'aggiornamento side-by-side, gestire la farm di Microsoft Office SharePoint Server 2007, ma creare una farm dalla prossima versione da esso (SharePoint Server 2010) in un nuovo hardware. In questo modo nei tre modi:
  
1. Si dispone di un'area in cui eseguire i backup dei database di Microsoft Office SharePoint Server 2007 per aggiornarli separatamente, utilizzando database basato sul collegamento.
    
2. Se si figura un piccolo numero di raccolte documenti critici e altre informazioni sono in uso nella farm di Microsoft Office SharePoint Server 2007, è possibile scegliere di spostare manualmente i dati da Microsoft Office SharePoint Server 2007 a SharePoint Server 2010 , oppure eseguire solo specifici siti e siti Web per la versione successiva (in cui è possibile semplificare il processo).
    
3. Minore è eseguire Microsoft Office SharePoint Server 2007 server farm, direttamente, il modo più sicura i dati della farm contengono come si effettua l'aggiornamento.
    
Metodi di aggiornamento sul posto fungerà direttamente nella farm di Microsoft Office SharePoint Server 2007, contenente le opzioni di facile meno abbandonare un percorso e iniziare nuovamente con l'ambiente assolutamente eccellente. Per quanto possibile, compilato in alcune misure di protezione (ad esempio, disconnessione e il testing di backup dell'ambiente originale). Ad esempio, se la farm di Microsoft Office SharePoint Server 2007 è virtuale e duplicata ai fini di backup e ripristino, quindi backup e ripristinare i database prima del tempo di attesa per l'aggiornamento più recenti. Conoscenza di avere l'opzione per ripristinare i database di backup non solo fornire alternativa, è possibile fornire massima sicurezza.
  
> [!TIP]
> Migliori documenti consigliate per l'aggiornamento esistono per [Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/en-us/library/cc261992%28v=office.12%29.aspx), [SharePoint Server 2010](https://technet.microsoft.com/en-us/library/cc261992%28v=office.14%29.aspx), [SharePoint Server 2013](https://technet.microsoft.com/en-us/library/cc261992%28v=office.15%29.aspx)e [SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc261992%28v=office.16%29.aspx). È inoltre possibile cercare [Partner Microsoft](https://partnercenter.microsoft.com/en-us/pcv/search) che hanno familiarità con gli aggiornamenti o le migrazioni di Office 365. 
  
## <a name="make-your-plan"></a>Rendere il piano

Se è necessario eseguire l'aggiornamento, è necessario un piano e 1-non sono adatte tutti in questi casi. Il piano potrebbe essere semplice come 'Creazione di una sottoscrizione a Office 365 con SharePoint Online, registrare un dominio e reindirizzare persone per salvare i file non esiste'. E potrebbe non essere. Questa decisione è spetta all'utente ed è verso il basso per quali gli utenti possano effettivamente necessario.
  
> [!NOTE]
> È un rischio per l'esecuzione in software è terminata in cui ciclo di vita. Prodotti non più supportati non sono non è più corretti quando vengono rilevati problemi. Inoltre, ciò significa che se si verificano nuove minacce alla sicurezza, non ci sarà le patch di protezione o correzioni perché i prodotti di fine del ciclo di vita non sono più supportati. Evitare tale situazione! 
  
### <a name="first-know-your-farm"></a>Per prima cosa, verificare se la farm

Durante l'aggiornamento, prendere una decisione deve essere basata su scopo della farm per l'organizzazione. Le necessità questi soddisfano? Che cos'è il ruolo? Ogni farm nell'azienda potrebbe essere un ruolo diverso. Alcune delle farm SharePoint può essere *critico* , alcuni possono essere archivi file, quest'ultimo per la protezione. In alternativa, se la farm riempimenti molti ruoli contemporaneamente, quindi potrebbe essere necessario sapere quali raccolte siti, siti Web o anche le raccolte documenti non, eventuali personalizzazioni, e il livello di importanza sono. Analizzare i dati a questo livello possa sembrare molto lavoro ma viene salvato tempo e fatica a master del dominio prima di eseguire l'aggiornamento o la migrazione, è. Quando si conosce tutti gli elementi mobili e i bit più importanti, si verrà anche sapere cosa è stato superato le e possibile tralasciare. Che knowledge solo utile è poi. 
  
Quali sono gli utenti che indicano importanti sulla farm di SharePoint Server?
  
- Caratteristiche di SharePoint predefiniti
    
- Il corpo di dati di grandi dimensioni (ad esempio un archivio dei file)
    
- Disponibilità
    
- Applicazioni critici, web part o documenti nella farm (farm critici missione)
    
- Gli standard di conformità soddisfatti
    
- Personalizzazioni
    
Se si esegue un elemento essenziale per la propria azienda da farm di SharePoint, ad esempio funga da un grande catalogo dei dati critici sui requisiti del servizio client, è possibile inserire un segno di graduazione accanto a 'App critico', ma potrebbe essere 'Disponibilità' -, un'azienda interessato se non è possibile utilizzare SharePoint per un po' di tempo. Analogamente, è possibile estrarre 'Personalizzazioni' dal momento che la farm basate su codice personalizzato, definizioni di sito o un numero di personalizzazioni che è possibile utilizzare contemporaneamente le offerte di servizi critici.
  
Se SharePoint soddisfare le esigenze senza che sia necessario eseguire alcuna operazione all'esterno di utilizzo che cos'è incorporata per i componenti software ed in genere aggiornarlo ed eseguire le normali amministrazione e manutenzione, è stato scelto "Predefiniti di SharePoint", è anche possibile la motivo della seduta in una versione precedente di SharePoint. In altre parole, è già cosa è necessario per e non sono necessari per l'aggiornamento fino a questo punto, alla fine di Microsoft Office SharePoint Server 2007 di supporto.
  
Quando si elenco puntato queste operazioni, si creano i criteri per l'aggiornamento. In altre parole, un aggiornamento avrebbe soddisfare questo barra per prendere in considerazione. In questo modo consente di escludere i metodi che attualmente non adattano alle proprie esigenze.
  
### <a name="a-simple-sample-plan"></a>Un piano di esempio semplice

Si potrebbe essere necessario essere più ampio consenso con leader e gli altri amministratori sul percorso che necessario per completare l'aggiornamento di SharePoint. Amministratori di SharePoint Server spesso collaborare con gli amministratori di Microsoft SQL Server, utilizzare i team di rete e la protezione e altro ancora. In cui sono presenti molte delle parti interessate, potrebbe essere necessario contratto per creare o modificare, il piano di aggiornamento e migrazione. Ad esempio, se si esegue la migrazione dei dati in modo da parte dell'azienda utilizza SharePoint Online in Office 365, vi sarà probabilmente necessario essere ottimizzazione delle prestazioni e la verifica all'interno della rete. I team interessati devono essere informati anticipo.
  
Nell'esempio semplice, è possibile visualizzare proposta dell'amministratore di SharePoint ed elencare il piano concordate tutte le parti interessate. Per chiarezza, documentare i contratti e decisioni.
  
Il piano inizia dopo un'analisi approfondita di una farm e tenta di identificare il ruolo di farm, criticità e altre informazioni importanti che potrebbero causare di limitazione verso il basso alcune opzioni di aggiornamento. Successivamente, una proposta di aggiornamento viene effettuata dall'amministratore di SharePoint e le parti interessate l'utente accetta di un piano di azione.
  
Elenco puntato con personale "importante":
  
- Disponibilità, incorporati in SharePoint, sulle funzionalità standard di conformità.
    
- La maggior parte dei dati è in tre raccolte siti, con un'area di lavoro riunioni da un team di sviluppatori particolarmente importante e utilizzati in un utilizzo intenso in più i fusi orari tutto il mondo.
    
- Esistono diciassette altri siti che sono ampiamente utilizzate.
    
- Due raccolte documenti (area di lavoro riunioni e documenti nella raccolta siti radice) sono più grandi (oltre 8000 documenti ogni). È disponibile un numero elevato di documenti archiviati e dell'elenco con allegati di fogli di calcolo.
    
- Sono disponibili quattordici elenchi delle raccolte con i dati riservati devono rimanere in conformità.
    
- È necessario hanno la possibilità di eseguire esenzioni ed e-discovery è ovunque.
    
- Alcuni di questi dati devono essere informati locali, a causa di regole InfoSec.
    
 **Scelte aggiornamento e migrazione:**
  
|||
|:-----|:-----|
|**Sì** <br/> |**No** <br/> |
|Aggiornamento di database con database basato sul collegamento  <br/> |Aggiornamento sul posto  <br/> |
|Aggiornamento con farm side-by-side  <br/> |Aggiornamento ibrido  <br/> |
|API per la migrazione a SharePoint Online in Office 365 (per i dati del sito personale)  <br/> |Ambiente ibrido di SharePoint (non è necessario ancora)  <br/> |
|Migrazioni alcuni manuale dei dati in SharePoint Online per i dati critici  <br/> |Aggiornamento guidata FastTrack a Office 365  <br/> |
   
 **Il piano proposto:**
  
Aggiornamento locale, con le versioni di SharePoint side-by-side, alcune virtualizzato, in modo che è possibile aggiornare i database prima. Passare da SharePoint 2007 a SharePoint 2010. Gli amministratori e sviluppatori di testing della farm risultante. Gli utenti di test della farm risultante. Risolvere eventuali problemi di arresto Mostra durante questa fase. Nuovamente, side-by-side, effettuare l'aggiornamento database di SharePoint 2010 a SharePoint 2013. Utente di test. test/pilota. Risolvere eventuali problemi di arresto Mostra durante questa fase.
  
- Valutare se una ricerca federata ibrida con SharePoint Online soddisfi le proprie esigenze.
    
- Se si desidera eseguire l'aggiornamento a SharePoint Online da qui, prendere in considerazione [FastTrack assistenza](https://fasttrack.microsoft.com) . 
    
- Determinare se è possono scaricare le raccolte siti in una sottoscrizione a Office 365. (Office 365 soddisfi molti [standard di conformità](https://technet.microsoft.com/library/office-365-compliance.aspx). Office 365 è [eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) e può eseguire [contiene](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) per il centro conformità.) 
    
In caso contrario, continuare con un aggiornamento side-by-side per SharePoint Server 2016.
  
> [!NOTE]
> Tra le raccomandazioni per gli amministratori che pianificano l'aggiornamento e l'effettivo processo sono le conversazioni eseguite con altre parti interessate in cui si basa l'aggiornamento. Ad esempio, in alcuni casi economici imporre agli amministratori di modificare i piani. Qualsiasi la decisione finale è, è consigliabile documentare che cos'è la pianificazione concordata in futuro. Potrebbe essere simile al seguente: 
  
 **Il piano di azione:**
  
Locale, viene utilizzato un ambiente virtuale per creare predefinito SharePoint Server 2010 e 2013. SharePoint Server 2016 verrà generata in un nuovo hardware che soddisfi i requisiti di sistema per 2016. Questa operazione verrà eseguita associa per aggiornare i database da SharePoint 2007 a tutte le versioni tra di esso e SharePoint Server 2016 del database. Le personalizzazioni di base viene ricreate per e test rigorosi in SharePoint Server 2016 ambiente il momento, se la funzionalità nativa già non soddisfa le esigenze. Se si ha esito positivo, si avrà una farm locale in un nuovo hardware con database aggiornati e le personalizzazioni meno. Si verranno collegare i database del contenuto aggiornati nuove raccolte siti in SharePoint Server 2013, prova, pilota/utente test, e quindi eseguire una DNS cutover nel nuovo ambiente SharePoint Server 2016 per l'utilizzo di live.
  
- Non è saranno considerati direttamente federati ibrido di SharePoint Server 2016 e SharePoint Online.
    
- Un stimata 35% dei siti possono essere trasformato in nuovi siti di SharePoint Online con i domini di reindirizzamento a microsito o, in ultima analisi, diventano OneDrive per l'archiviazione Business. Cerchi altre opportunità convertire i siti o distribuire nuovi siti a SharePoint Online.
    
- Alcuni di questa parte della migrazione è manuale e trascinamento per OneDrive per i siti personali e altri dall'API per la migrazione.
    
Ulteriori passaggi o un numero di collegamenti a istruzioni di aggiornamento specifici consigliabile eseguire un piano. Il computer MOSS 2007 non deve essere disattivato e ambienti virtuali devono essere gestiti per ragioni di confronto; Tuttavia, l'aggiornamento sarà completato quando gli utenti vengono reindirizzati a SharePoint Server 2016.
  
Fattori principali spesso nella scelta di un metodo sono il costo totale dell'aggiornamento e il costo nel tempo (verrà visualizzato ulteriori informazioni su questo nell'articolo Roadmap di migrazione di SharePoint). Tuttavia, pianificazione anticipo utilizzeranno è notevolmente in aspettative scelta in modo appropriato, e il successo di frame sarà simile al seguente.
  
## <a name="related-links"></a>Collegamenti correlati

[Risorse che consentono di eseguire l'aggiornamento da Office 2007 ai server e client](upgrade-from-office-2007-servers-and-products.md)
  
[Ricerca di Microsoft Lifecycle Policy e del ciclo di vita](https://support.microsoft.com/en-us/lifecycle)
  
[Ricerca per Microsoft Partners che possono essere utili per l'aggiornamento o la migrazione](https://partnercenter.microsoft.com/en-us/pcv/search)
  

