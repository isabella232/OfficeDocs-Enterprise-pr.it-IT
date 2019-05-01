---
title: Diagramma accessibile-flusso eDiscovery locale
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: Questo articolo è una versione di testo accessibile del diagramma denominato flusso eDiscovery locale.
ms.openlocfilehash: e137a75fb80c9198a332144d82fe405c6884aa52
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487702"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a>Diagramma accessibile-flusso eDiscovery locale

**Riepilogo:** Questo articolo è una versione di testo accessibile del diagramma denominato flusso eDiscovery locale.
  
Questo poster fornisce informazioni dettagliate sull'architettura e sul flusso dei dati tra i prodotti server. 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a>Condivisioni di SharePoint, Exchange, Lync e file

Nel diagramma viene visualizzato un utente che invia una query che accede a due server farm, una farm di app SharePoint 2013 Enterprise e una farm di servizi di SharePoint 2013. La farm di SharePoint 2013 Services comunica con una farm di contenuto di SharePoint 2013, Exchange Server 2013 (che comunica con Lync 2013) e condivisioni file di Windows. 
  
L'elenco di flusso di eDiscovery descrive il flusso di dati e l'ordine in cui si verificano le azioni di query di eDisovery tra SharePoint, Exchange, Lync e le condivisioni di file. 
  
L'elenco di flusso di eDiscovery viene descritto in dettaglio per primo, seguito da una descrizione dettagliata delle caratteristiche descritte nel diagramma. 
  
### <a name="ediscovery-flow-list"></a>Elenco dei flussi di eDiscovery

I numeri per ogni procedura descritta in questo elenco sono relativi a un passaggio illustrato nel diagramma. Il diagramma è descritto in dettaglio più avanti in questo documento. 
  
1. i casi di eDiscovery vengono creati, gestiti e utilizzati in eDiscovery Center (EDC). EDC è una raccolta siti di SharePoint 2013. Di seguito vengono definiti i casi, vengono identificate le fonti da tenere presenti, vengono rilasciate le query, vengono esaminati i risultati delle query e il contenuto viene inserito o rimosso. 
    
2. La query o l'azione eDiscovery, ad esempio Place a Hold, ReleaseHold o GetStatus, viene inoltrata dall'EDC al proxy dell'applicazione del servizio di ricerca (SSA) nella farm di app Enterprise. Il proxy SSA inoltra quindi il traffico all'SSA nella farm di applicazioni dei servizi. In questo esempio, la richiesta è quella di inserire qualsiasi elemento nella farm del contenuto di SharePoint con "CONTOSO" nel nome del file in attesa. 
    
3. Se la richiesta è quella di eseguire una query su un caso, il SSA consulterà l'indice di ricerca. Successivamente, il set di risultati di query di eDiscovery torna all'utente tramite EDC. 
    
4. Se la richiesta è un'azione, ad esempio un blocco o un ReleaseHold, tale azione viene scritta in Actions_Table nel database amministrativo SSA. In questo esempio, una richiesta di archiviazione per qualsiasi elemento nella farm del contenuto di SharePoint con "CONTOSO" viene scritta in Actions_Table. 
    
5. A intervalli regolari la farm di contenuto eDiscovery il processo timer del blocco sul posto viene riattivato e genera una richiesta per le azioni in sospeso e invia gli aggiornamenti dello stato tramite il proxy SSA al SSA. 
    
6. La query per le azioni in sospeso viene inoltrata al SSA centrale, che consulta l'Action_Table per tutte le azioni in sospeso per la farm di contenuto. Il processo timer della farm di contenuto consente inoltre di inviare gli aggiornamenti di stato per gli oggetti e le azioni ricevuti, scritti in ActionsTable. 
    
7. La richiesta di archiviazione per qualsiasi contenuto con "CONTOSO" nel nome nella farm di contenuto di SharePoint 2013 viene inviata da SSA al processo timer di archiviazione sul posto di eDiscovery nella farm di contenuto. 
    
8. Il processo timer di archiviazione sul posto di eDiscovery inserisce in attesa il "sito CONTOSO" e il "contenuto CONTOSO". 
    
9. Il processo timer per il blocco sul posto di eDiscovery viene eseguito periodicamente nella farm dell'applicazione Enterprise per controllare lo stato delle azioni di individuazione e per aggiornare lo stato. 
    
10. La query di stato viene inoltrata tramite il proxy SSA farm dell'applicazione Enterprise all'SSA farm di SharePoint Services. 
    
11. Il SSA recupera lo stato dalla tabella Actions e lo restituisce al processo timer nella farm Enterprise app, che inserisce gli aggiornamenti dello stato in EDC. 
    
12. Quando l'utente di eDiscovery esegue la ricerca o l'esecuzione di un'azione per le origini di Exchange, ad esempio una cassetta postale o un contenuto Lync archiviato, la SSA centrale utilizza il proxy di servizi Web Exchange (EWS) per eseguire query sui servizi Web di Exchange. Exchange dispone di un'infrastruttura di ricerca e di eDiscovery e gestisce tutte le chiamate di eDiscovery internamente. 
    
13. Servizi Web Exchange risponde a SSA con i risultati della ricerca di eDiscovery o una risposta a una richiesta di stato per un blocco basato su query, che, a sua sua, viene inoltrato all'EDC. 
    
#### <a name="prerequisites"></a>Prerequisiti

- La ricerca di SharePoint Enterprise deve essere configurata, le ricerche per indicizzazione nelle origini di contenuto (condivisioni di file di SharePoint e di Windows) sono state eseguite correttamente e tutte le origini di contenuto sono nell'indice. 
    
- L'attendibilità da server a server e l'autenticazione devono essere configurate tra la farm di SharePoint Services e Exchange e anche tra Exchange e Lync. 
    
### <a name="description-of-components-in-the-diagram"></a>Descrizione dei componenti nel diagramma

Nel diagramma viene visualizzato un utente che invia una query, che accede a due server farm, una farm di SharePoint 2013 Enterprise app e una farm di servizi di SharePoint 2013. La farm di SharePoint Services si interfaccia con una farm di contenuto di SharePoint 2013, Exchange Server 2013 (che si interfaccia con Lync 2013) e condivisioni file di Windows. 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a>Farm delle app di SharePoint 2013 Enterprise

La farm delle app di SharePoint 2013 Enterprise contiene i componenti seguenti: 
  
- EDC
    
- Proxy SSA 
    
- Processo timer 
    
Una query o un'azione inviata dall'utente viene inviata all'EDC nella farm dell'applicazione Enterprise. Si verificano le seguenti azioni: 
  
- La query o l'azione passa al proxy SSA. 
    
- Il proxy SSA invia una query di stato o una risposta al processo timer nella farm di app Enterprise e invia anche una query di stato o una risposta al servizio SSA nella farm di SharePoint Services. Le azioni che derivano da questa operazione sono descritte nella sezione relativa alla farm di SharePoint Services. 
    
- Quando riceve una risposta, il processo timer Invia la risposta al proxy SSA e all'EDC. 
    
- Tutti i risultati della query o dell'azione vengono inviati all'utente dall'EDC. 
    
#### <a name="sharepoint-2013-services-farm"></a>Farm di SharePoint 2013 Services

La farm di SharePoint 2013 Services contiene i componenti seguenti: 
  
- Servizio SSA 
    
- Database degli indici di ricerca 
    
- Database SSA admin_db. La tabella Actions del database contiene: Hold Release Hold GetStatus 
    
- Proxy EWS 
    
Quando il proxy SSA nella farm di app di SharePoint Enterprise invia una query di stato al SSA nella farm di SharePoint Services, si verificano le seguenti azioni: 
  
- Se la richiesta è una query, la SSA consulterà l'indice di ricerca. La risposta di individuazione viene restituita al SSA e quindi all'utente tramite EDC. 
    
- Se la richiesta è un'azione di scrittura, il servizio SSA invia l'azione di scrittura al admin_db SSA. 
    
- Una richiesta di ricerca per indicizzazione e risposta viene inviata da SSA alla farm di contenuto di SharePoint 2013 e viene restituita una risposta al SSA. 
    
- Una richiesta di ricerca per indicizzazione e risposta viene inviata dal SSA alle condivisioni file di Windows e una risposta viene restituita al SSA. 
    
- Una query per le azioni, le risposte o gli aggiornamenti di stato in sospeso viene inviata dal SSA al proxy SSA nella farm del contenuto di SharePoint e viene restituita una risposta al SSA. 
    
- Una richiesta di azione/stato di Exchange viene inviata dal SSA al proxy EWS, che invia una richiesta di azione/stato di query di Exchange al servizio Web di Exchange sul server Exchange 2013. 
    
- Una query di stato/risposta viene inviata dal SSA al ssa admin_db e viene restituita al SSA. 
    
- Una query o una risposta di azione in sospeso viene inviata dal SSA al ssa admin_db e viene restituita al SSA. 
    
#### <a name="sharepoint-2013-content-farm"></a>Farm di contenuto di SharePoint 2013

La farm di contenuto di SharePoint 2013 contiene i componenti seguenti: 
  
- Proxy SSA 
    
- Processo timer 
    
- Sito di SharePoint di contoso 
    
- Contenuto di SharePoint di contoso 
    
Quando la farm di SharePoint Services viene inviata una query di stato al proxy SSA nella farm di contenuto di SharePoint, si verificano le seguenti azioni: 
  
- Il proxy SSA nella farm del contenuto di SharePoint invia una query per le azioni in sospeso/la risposta dello stato al processo timer. 
    
- Il processo timer invia una richiesta al sito di SharePoint contoso, che esamina il contenuto di SharePoint contoso. 
    
- La risposta alla query relativa alle azioni o allo stato in sospeso viene inviata dal processo timer al proxy SSA nella farm del contenuto di SharePoint e quindi viene inviata al servizio SSA nella farm di SharePoint Services. 
    
#### <a name="exchange-2013"></a>Exchange 2013

Il componente server di Exchange 2013 contiene il servizio Web di Exchange e fornisce quanto segue: 
  
- La relazione di trust tra server/OAuth viene gestita tra la farm di contenuto di SharePoint 2013 e Exchange 2013. 
    
- La relazione di trust tra server/OAuth viene gestita tra Exchange 2013 e Lync 2013. 
    
#### <a name="lync-2013"></a>Lync 2013

Il componente Lync 2013 archivia il contenuto di Lync in Exchange 2013. 
  
#### <a name="windows-file-shares"></a>Condivisioni file di Windows

Il componente Condivisione file di Windows fornisce i risultati della ricerca per indicizzazione all'SSA nella farm di SharePoint Services. 
  
### <a name="legend"></a>Legenda

La legenda per questo diagramma Visualizza graficamente i diversi tipi di traffico rappresentati tra i componenti in linee colorate diverse, come indicato di seguito: 
  
- Riga blu chiaro: query/azione-eDiscovery di query o dati di azione 
    
- Linea arancione: eDisovery Response-eDiscovery query Response data 
    
- Linea verde: Status query/Response-eDiscovery Status query/dati di risposta 
    
- Linea viola: Exchange Action/Status Request-eDiscovery Request for Action Status per il traffico di Exchange. 
    
- Linea rossa: Exchange Data/status Response-eDiscovery query o la risposta dello stato da Exchange. 
    
- Riga nera punteggiata: attendibilità da server a server/OAuth 
    
- Linea nera massiccia: ricerca per inDicizzazione/risultati 
    

