---
title: Pianificazione della capacità e test di carico di SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/18/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: In questo articolo viene descritto come distribuire SharePoint Online senza eseguire il test di carico tradizionale, poiché non è consentito.
ms.openlocfilehash: ef5d6c043b4be2e8c5358a9c060459b4c6a92156
ms.sourcegitcommit: 468c8e8d2f951e08cf50301445ad650ef17328aa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/09/2019
ms.locfileid: "30512721"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>Pianificazione della capacità e test di carico di SharePoint Online.

In questo articolo viene descritto come eseguire la distribuzione in SharePoint Online senza il test di carico tradizionale, in quanto i test di carico non sono consentiti in SharePoint Online. SharePoint Online è un servizio cloud le funzionalità di carico, integrità e bilanciamento del carico generale del servizio sono gestite da Microsoft.
  
L'approccio migliore per garantire il successo del lancio del sito consiste nel seguire i principi, le procedure e i suggerimenti di base riportati di seguito.
  
Con gli ambienti locali, il test di carico viene utilizzato per convalidare il presupposto della scala e infine individuare il punto di interruzione di una farm. saturando il carico. Con SharePoint Online, è necessario eseguire le operazioni in modo diverso. Poiché si tratta di un ambiente multi-tenant, è necessario proteggere tutti i tenant della stessa farm, in modo da limitare automaticamente eventuali test di carico. Questo significa che si riceveranno risultati deludenti e potenzialmente detestabili se si tenta di caricare il test dell'ambiente.
  
Uno dei principali vantaggi di SharePoint online in una distribuzione locale è l'elasticità del cloud. L'ambiente su larga scala è configurato per il servizio di milioni di utenti su base giornaliera, pertanto è importante gestire efficacemente la capacità mediante l'equilibratura e l'espansione delle farm. L'articolo include anche gli approcci per l'utilizzo che non coinvolgono i test di carico, ma implicano le linee guida seguenti che consentiranno di eseguire correttamente il lancio. 
  
Anche se la crescita è imprevedibile per qualsiasi tenant in una farm, la somma aggregata delle richieste è prevedibile nel tempo. Identificando le tendenze di sviluppo in SharePoint Online, è possibile pianificare la futura espansione.
  
Al fine di utilizzare in modo efficiente la capacità e gestire la crescita imprevista, in qualsiasi farm, è presente un'automazione che consente di tenere traccia del carico front-end e di eseguire la scalabilità verticale, se necessario. Sono disponibili più metriche con uno dei principali carichi di CPU che vengono utilizzati come segnale per la scalabilità verticale dei Front End Server. In aggiunta a questo e come si noterà ulteriormente nell'articolo, è consigliabile un approccio graduale/Wave come gli ambienti SQL verranno scalati in base al carico e alla domanda e seguendo le fasi e le onde consentono la corretta distribuzione del carico e della crescita. 
  
## <a name="how-do-i-plan-for-a-site-launch"></a>Come si pianifica un avvio del sito?

### <a name="optimize-pages-by-following-recommended-guidelines"></a>Ottimizzare le pagine seguendo le linee guida consigliate
Le pagine di una distribuzione locale non devono essere semplicemente eseguite come sono su SharePoint Online senza verificarle in base alle linee guida consigliate per SharePoint Online.

Alcuni fattori chiave devono essere considerati:
- Le distribuzioni in locale possono sfruttare le tradizionali cache sul fianco del server, come la cache degli oggetti, ma con le differenze di topologia nel cloud, queste opzioni non sono disponibili.
- Tutte le pagine/caratteristiche/personalizzazioni utilizzate per il consumo di cloud devono essere ottimizzate per più posizioni in modo che gli utenti in aree geografiche diverse abbiano un'esperienza coerente. Cloud offre ottimizzazioni come la rete per la distribuzione dei contenuti (CDN) per ottimizzare la base di utenti distribuiti.

Per le pagine di pubblicazione classiche di SharePoint Online, è possibile utilizzare l'estensione Chrome dello [strumento di diagnostica di pagina](https://aka.ms/perftool) , che consentirà di analizzare le pagine di destinazione principali utilizzate dagli utenti.
Gli strumenti di sviluppo F12 nel browser o [Fiddler](https://www.telerik.com/download/fiddler) possono essere utilizzati per esaminare il peso della pagina e il numero di chiamate e gli elementi che influiscono sul caricamento generale della pagina devono essere esaminati e ottimizzati. Un elenco di suggerimenti, tra cui l'utilizzo di reti di distribuzione del contenuto e altre ottimizzazioni, può essere esaminato nell'articolo [Tune SharePoint Online performance](https://aka.ms/spoperformance) .

### <a name="wave--phase-approach"></a>Approccio Wave/Phase
L'approccio tradizionale del Big Bang per i lanci dei siti non consente in modo efficace la verifica che le personalizzazioni, le origini esterne, i servizi o i processi siano stati testati sulla scala giusta. SharePoint come servizio bilancia anche la capacità in base all'utilizzo e all'utilizzo previsto e sebbene non sia necessario inviare una notifica del lancio del sito, è consigliabile seguire le linee guida riportate di seguito per garantire il successo.
  
Come illustrato nella figura seguente, spesso il numero di utenti invitati è significativamente più elevato rispetto a quelli che utilizzano effettivamente il sito. In questa immagine viene illustrata una strategia su come eseguire il rollback di una versione. Questo metodo consente di identificare i modi per migliorare il sito di SharePoint prima che la maggior parte degli utenti lo veda. Inoltre, consente di sospendere l'implementazione se si riscontrano problemi in una delle fasi/onde che limitano il potenziale numero di utenti interessati.
  
![Grafico degli utenti invitati e attivi](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
Nella fase pilota, è opportuno ottenere commenti e suggerimenti da parte degli utenti che l'organizzazione ha fiducia e sa che verranno coinvolti. In questo modo è possibile valutare la modalità di utilizzo del sistema, nonché la modalità di esecuzione.
  
Durante ciascuna delle onde, raccogliere i commenti degli utenti in merito alle caratteristiche e le prestazioni durante ogni ondata di distribuzione. Questo ha il vantaggio di introdurre lentamente il sistema e apportare miglioramenti man mano che il sistema viene utilizzato. In questo modo, è possibile reagire anche all'aumento del carico quando il sito viene implementato per un numero sempre maggiore di utenti.
