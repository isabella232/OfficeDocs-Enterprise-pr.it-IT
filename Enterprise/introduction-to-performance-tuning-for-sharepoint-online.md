---
title: Introduzione all'ottimizzazione delle prestazioni per SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: In questo articolo viene illustrato quali aspetti specifici, è necessario prendere in considerazione durante la progettazione di pagine per ottimizzare le prestazioni di SharePoint Online.
ms.openlocfilehash: 07938770d711477126f78fc583e8d2533ba5c1d1
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219876"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>Introduzione all'ottimizzazione delle prestazioni per SharePoint Online

In questo articolo viene illustrato quali aspetti specifici, è necessario prendere in considerazione durante la progettazione di pagine per ottimizzare le prestazioni di SharePoint Online.
     
## <a name="sharepoint-online-metrics"></a>Metriche di SharePoint Online

Le seguenti metriche generali per SharePoint Online forniscono dati reali sulle prestazioni:
  
- Velocità di caricamento delle pagine
    
- Numero di round trip necessari per ogni pagina
    
- Problemi con il servizio
    
- Altri aspetti che causano la riduzione delle prestazioni
    
### <a name="conclusions-reached-because-of-the-data"></a>Conclusioni in base ai dati

I dati dicono:
  
- La maggior parte delle pagine garantisce buone prestazioni con SharePoint Online.
    
- Le pagine non personalizzate si caricano molto rapidamente.
    
- OneDrive for Business, i siti del team e le pagine di sistema, ad esempio _layouts e così via, si caricano tutti rapidamente.
    
- La pagina più lenta di 1% di SharePoint Online impiega più di 5.000 millisecondi per caricarsi.
    
È possibile utilizzare un semplice test di benchmark per misurare le prestazioni confrontando il tempo di caricamento del proprio portale con il tempo di caricamento della home page di OneDrive for Business, perché utilizza alcune funzionalità personalizzate. Questo spesso sarà il primo passaggio che il supporto chiederà di completare durante la risoluzione dei problemi relativi alle prestazioni di rete.
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>Utilizzare un account utente standard per il controllo delle prestazioni

Un amministratore della raccolta siti, proprietario del sito, Editor o collaboratore appartengono a gruppi di sicurezza aggiuntive, disporre di autorizzazioni aggiuntive e pertanto sono elementi aggiuntivi che SharePoint viene caricato in una pagina.
  
Questa opzione è disponibile per SharePoint Online e SharePoint locale, ma in uno scenario in locale differenze saranno la stessa facilità inosservate come SharePoint Online.
  
Per valutare correttamente come una pagina verrà eseguite per gli utenti, è consigliabile utilizzare un account utente standard per evitare di caricare la creazione di controlli e un aumento del traffico relative ai gruppi di sicurezza.
  
## <a name="connection-categories-for-performance-tuning"></a>Categorie di connessione per l'ottimizzazione delle prestazioni

È possibile classificare le connessioni tra il server e l'utente in tre componenti principali. Prendere in considerazione tali componenti durante la progettazione delle pagine di SharePoint Online per comprendere i tempi di caricamento.
  
- **Server** I server che ospita Microsoft nei Data Center.
    
- **Rete** Microsoft network, Internet e la rete locale tra i Data Center e gli utenti.
    
- **Browser** Dove viene caricata la pagina.
    
All'interno di queste tre connessioni in genere esistono cinque motivi che causano il 95% delle pagine lente. Ciascuna di queste situazioni è illustrata in questo articolo:
  
- Problemi di navigazione
    
- Rollup contenuto
    
- File di grandi dimensioni
    
- Numero elevato di richieste al server
    
- Elaborazione di Web Part
    
### <a name="server-connection"></a>Connessione al server

Molti dei problemi che influiscono sulle prestazioni di SharePoint locale valgono anche per SharePoint Online.
  
Come previsto, è necessario prestare maggiore controllo sul funzionamento dei server con SharePoint locale. Con SharePoint Online le cose sono leggermente diverse. Più lavoro si fa fare al server, maggiore sarà il tempo necessario per il rendering di una pagina. Con SharePoint, la causa principale a questo proposito sono le pagine complesse con più web part.
  
SharePoint Server in locale
  
![Schermata del server in locale](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![Schermata del server online](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
Con SharePoint Online, alcune richieste di pagine potrebbero effettivamente finire per chiamare più server. Si potrebbe finire con una matrice di richieste tra i server per una singola richiesta. Tali interazioni sono costose da una prospettiva di caricamento della pagina e rendono le operazioni lente.
  
Esempi di tali interazioni da server a server sono:
  
- Da Web a SQL Server
    
- Da Web ai server applicazioni
    
L'altra operazione che può rallentare le interazioni del server è la mancanza della cache. A differenza di SharePoint locale, esiste una possibilità molto piccola di raggiungere lo stesso server di una pagina visitata in precedenza. Ciò rende la memorizzazione degli oggetti nella cache obsoleta.
  
### <a name="network-connection"></a>Connessione di rete

Con SharePoint locale che non utilizzano una rete WAN, è possibile utilizzare una connessione ad alta velocità tra Data Center e gli utenti finali. In generale, aspetti sono facile da gestire da un punto di vista di rete.
  
Con SharePoint Online, esistono alcuni ulteriori fattori da considerare; ad esempio:
  
- La rete Microsoft
    
- Internet
    
- Il provider di servizi Internet
    
Indipendentemente dalla versione di SharePoint (e di rete) utilizzata, le operazioni che in genere rendono la rete occupata sono:
  
- Payload di grandi dimensioni
    
- Numero elevato di file
    
- Grande distanza fisica con il server
    
Una funzionalità che è possibile utilizzare in SharePoint Online è Microsoft CDN (rete CDN). Una rete CDN è fondamentalmente una raccolta distribuita dei server distribuiti tra più centri dati. Con una rete CDN, il contenuto delle pagine può essere ospitato in un server all'incirca il client anche se il client è lontana dal Server di origine SharePoint. Microsoft utilizzerà questo più in futuro per archiviare le istanze locali di pagine che non possono essere personalizzate, ad esempio SharePoint Online admin home page. Per ulteriori informazioni su CDN, vedere [reti di distribuzione del contenuto](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).
  
Un elemento che è necessario tenere presente ma sul quale potrebbe non essere possibile agire, è la velocità della connessione del provider di servizi Internet. Uno strumento di test di velocità semplice indica la velocità della connessione.
  
### <a name="browser-connection"></a>Connessione del browser

Esistono alcuni fattori da considerare con il browser Web dal punto di vista delle prestazioni.
  
Visitare pagine complesse inciderà sulle prestazioni. La maggior parte dei browser hanno a disposizione una cache di piccole dimensioni (circa 90MB), mentre la media pagina web viene in genere circa 1.6 MB. Non richiedere tempo che deve ottenere esaurite.
  
Larghezza di banda può essere anche un problema. Ad esempio, se un utente è la riproduzione di video in un'altra sessione, si inciderà sulle prestazioni della pagina di SharePoint. Quando si non possono impedire agli utenti di flussi multimediali, è possibile controllare il modo in cui che carica una pagina per gli utenti.
  
Vedere gli articoli seguenti per diverse tecniche di personalizzazione di pagina SharePoint Online e altre procedure consigliate per ottenere prestazioni ottimali.
  
- [Opzioni di spostamento per SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Utilizzare lo strumento di diagnostica di pagina per SharePoint Online](page-diagnostics-for-spo.md)
    
- [Ottimizzazione delle immagini per SharePoint Online](image-optimization-for-sharepoint-online.md)
    
- [Ritardo caricamento immagini e JavaScript in SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [Minimizzazione e creazione di bundle in SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Utilizzo delle reti di distribuzione del contenuto](using-content-delivery-networks-with-sharepoint-online.md)
    
- [Utilizzo di Web Part ricerca contenuto invece di Web Part Query contenuto per migliorare le prestazioni di SharePoint Online](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [Capacità di pianificazione test di carico e SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [Diagnosi dei problemi delle prestazioni con SharePoint Online](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [Utilizzo della cache oggetti con SharePoint Online](using-the-object-cache-with-sharepoint-online.md)
    
- [Procedura: Evitare la limitazione o il blocco in SharePoint Online](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

