---
title: Diagramma accessibile - eDiscovery locale flusso
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
description: In questo articolo è una versione testo accessibile del diagramma denominato eDiscovery locale flusso.
ms.openlocfilehash: e137a75fb80c9198a332144d82fe405c6884aa52
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
ms.locfileid: "17503059"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a>Diagramma accessibile - eDiscovery locale flusso

**Riepilogo:** In questo articolo è una versione testo accessibile del diagramma denominato eDiscovery locale flusso.
  
Questo poster fornisce informazioni dettagliate sull'architettura e flusso di dati tra i prodotti server. 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a>In SharePoint, Exchange, Lync e condivisioni di file

Il diagramma mostra un utente che invia una query che accede a due server farm, una Farm di SharePoint 2013 Enterprise App e una Farm di servizi di SharePoint 2013. Farm di servizi di SharePoint 2013 comunica con una Farm di SharePoint 2013 il contenuto, Exchange Server 2013 (che comunica con Lync 2013) e le condivisioni di File di Windows. 
  
EDiscovery flusso elenco vengono descritti il flusso di dati e l'ordine in cui eDisovery azioni di query si verificano in SharePoint, Exchange, Lync e condivisioni di file. 
  
Nell'elenco di flusso di eDiscovery è descritto dettagliatamente in primo luogo, seguito da una descrizione dettagliata delle caratteristiche illustrato nel diagramma. 
  
### <a name="ediscovery-flow-list"></a>eDiscovery flusso elenco

I numeri per ognuno dei passaggi descritti in questo elenco sono relativi a un passaggio illustrato nel diagramma. Nel diagramma è descritto in dettaglio più avanti in questo documento. 
  
1. casi di eDiscovery vengono creati, gestiti e utilizzati in eDiscovery center (EDC). Il EDC è una raccolta siti di SharePoint 2013. Si tratta di cui vengono definiti i casi, vengono identificate origini per tenere traccia, query vengono inviate, vengono esaminati i risultati delle query ed esenzioni contenuti vengono inseriti o rimossi. 
    
2. La query di eDiscovery o azione, ad esempio posto un'esenzione, ReleaseHold o GetStatus, viene inoltrata dal EDC al proxy di applicazione di servizio di ricerca (SSA) nella Farm di applicazione Enterprise. Il proxy SSA inoltra quindi il traffico per l'esecuzione dell'applicazione nella Farm di servizi di App. In questo esempio, la richiesta deve posizionerà nulla nella Farm di contenuto di SharePoint con "CONTOSO" nel nome del file in attesa. 
    
3. Se la richiesta di un caso di query, l'esecuzione dell'applicazione consulta l'indice di ricerca. Quindi, il set di risultati di query eDiscovery restituisce all'utente tramite il EDC. 
    
4. Se la richiesta di un'azione, ad esempio luogo una conservazione o ReleaseHold, tale azione viene scritta in Actions_Table nel database di amministrazione di esecuzione dell'applicazione. In questo esempio viene scritto il Actions_Table una richiesta di attesa per qualsiasi nella Farm di contenuto di SharePoint con "CONTOSO". 
    
5. A intervalli regolari il Farm di contenuto eDiscovery sul posto archiviazione processo timer riattiva e genera una richiesta di azioni in sospeso e invia gli aggiornamenti dello stato attraverso il proxy di esecuzione dell'applicazione per l'esecuzione dell'applicazione. 
    
6. La query per azioni in sospeso viene inoltrata per l'esecuzione dell'applicazione centrale, che consulta il Action_Table per le azioni per la Farm di contenuto in sospeso. Il processo timer di archiviazione sul posto di Farm di contenuto invia inoltre gli aggiornamenti di stato per gli oggetti e le azioni ha ricevuto, che vengono scritti i ActionsTable. 
    
7. La richiesta di attesa per qualsiasi contenuto con "CONTOSO" nel nome della Farm di SharePoint 2013 il contenuto viene inviata per l'esecuzione dell'applicazione per il processo timer di archiviazione sul posto di eDiscovery della farm di contenuto. 
    
8. Archiviazione la eDiscovery sul posto timer posizioni processo il "CONTOSO sito" e "CONTOSO contenuto" in attesa. 
    
9. Il processo timer di archiviazione sul posto di eDiscovery viene eseguito periodicamente nella Farm di applicazione Enterprise per verificare lo stato delle azioni di individuazione e per aggiornare lo stato. 
    
10. La query di stato viene inoltrata attraverso il proxy di esecuzione dell'applicazione Enterprise App Farm per l'esecuzione dell'applicazione Farm di servizi di SharePoint. 
    
11. L'esecuzione dell'applicazione viene recuperato lo stato dalla tabella azioni e restituisce il processo timer nella Farm di applicazione Enterprise, che inserisce gli aggiornamenti di stato per il EDC. 
    
12. Quando l'utente di eDiscovery è la ricerca (o eseguendo un'azione) per le origini di Exchange, ad esempio una cassetta postale o contenuto archiviato Lync, l'esecuzione dell'applicazione centrale viene utilizzato il proxy di servizi Web Exchange (EWS) per eseguire una query servizi Web Exchange. Exchange è disponibile il proprio infrastruttura di ricerca ed eDiscovery e gestisce tutte le chiamate di eDiscovery internamente. 
    
13. Servizi Web Exchange risponde a esecuzione dell'applicazione con i risultati della ricerca eDiscovery o una risposta a una richiesta di stato per un'esenzione basata su query, che a sua volta, ottiene inoltrata al EDC. 
    
#### <a name="prerequisites"></a>Prerequisiti

- Nell'indice di ricerca contenuti organizzazione SharePoint deve essere configurato correttamente si verificano ricerche per indicizzazione su origini di contenuto (SharePoint e Windows condivisioni di file), e tutte le origini di contenuto. 
    
- Necessario configurare l'autenticazione e la relazione di trust da server a server tra Farm di SharePoint Services ed Exchange e anche tra Exchange e Lync. 
    
### <a name="description-of-components-in-the-diagram"></a>Descrizione dei componenti del diagramma

Il diagramma mostra un utente che invia una query, che accede a due server farm, una Farm di SharePoint 2013 Enterprise App e una Farm di servizi di SharePoint 2013. Interfacce di Farm di servizi di SharePoint con una Farm di SharePoint 2013 il contenuto, Exchange Server 2013 (in cui si interfaccia con Lync 2013) e le condivisioni di File di Windows. 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a>Farm di SharePoint 2013 Enterprise App

Farm di SharePoint 2013 Enterprise App include i componenti seguenti: 
  
- EDC
    
- Proxy di esecuzione dell'applicazione 
    
- Processo timer 
    
Una query o azione inviati dall'utente viene inviato a EDC nella Farm di applicazione Enterprise. Si verifica quanto segue: 
  
- La query o l'azione viene inoltrata al proxy di esecuzione dell'applicazione. 
    
- Il proxy dell'esecuzione dell'applicazione invia una query sullo stato o una risposta per il processo Timer della farm di applicazioni Enterprise e consente inoltre di inviare una query sullo stato o una risposta al servizio di esecuzione dell'applicazione nella Farm di servizi di SharePoint. Azioni risultanti da ciò sono descritte nella sezione sulla Farm di servizi di SharePoint. 
    
- Quando riceve una risposta, il processo Timer invia la risposta per il proxy dell'esecuzione dell'applicazione e il EDC. 
    
- Risultati di query o azione vengono inviati all'utente dal EDC. 
    
#### <a name="sharepoint-2013-services-farm"></a>Farm di servizi di SharePoint 2013

Farm di servizi di SharePoint 2013 include i componenti seguenti: 
  
- Esecuzione dell'applicazione servizio 
    
- Database di indice di ricerca 
    
- Database admin_db esecuzione dell'applicazione. Contiene la tabella azioni nel database: archiviazione versione attesa GetStatus 
    
- Proxy di servizi Web Exchange 
    
Quando il proxy dell'esecuzione dell'applicazione nella Farm di SharePoint Enterprise App invia una query di stato per l'esecuzione dell'applicazione nella Farm di servizi di SharePoint, si verificano le seguenti operazioni: 
  
- Se la richiesta di una query, l'esecuzione dell'applicazione consulta l'indice di ricerca. La risposta di individuazione verrà restituita per l'esecuzione dell'applicazione e quindi all'utente tramite il EDC. 
    
- Se la richiesta è un'operazione di scrittura, il servizio SSA invia l'azione di scrittura per l'esecuzione dell'applicazione admin_db. 
    
- Una ricerca per indicizzazione e risponde risultati richiesta viene inviata dall'esecuzione dell'applicazione per la Farm di contenuto di SharePoint 2013 e viene restituita una risposta per l'esecuzione dell'applicazione. 
    
- Una ricerca per indicizzazione e risponde risultati richiesta viene inviata dall'esecuzione dell'applicazione per le condivisioni di File di Windows e viene restituita una risposta per l'esecuzione dell'applicazione. 
    
- Invio di una query per le azioni, le risposte o gli aggiornamenti dello stato in sospeso dall'esecuzione dell'applicazione per il proxy dell'esecuzione dell'applicazione nella Farm di contenuto di SharePoint e viene restituita una risposta per l'esecuzione dell'applicazione. 
    
- Viene inviata una richiesta di stato dell'azione/Exchange dall'esecuzione dell'applicazione per il proxy di servizi Web Exchange, che invia una richiesta di stato dell'azione/Exchange Query al servizio Web di Exchange sul server Exchange 2013. 
    
- Una query/risposta sullo stato viene inviata dall'esecuzione dell'applicazione a admin_db esecuzione dell'applicazione e vengono restituita per l'esecuzione dell'applicazione. 
    
- Un'operazione in sospeso query/risposta inviata dall'esecuzione dell'applicazione per l'esecuzione dell'applicazione admin_db e viene restituita per l'esecuzione dell'applicazione. 
    
#### <a name="sharepoint-2013-content-farm"></a>Farm di contenuto di SharePoint 2013

Farm di contenuto di SharePoint 2013 include i componenti seguenti: 
  
- Proxy di esecuzione dell'applicazione 
    
- Processo timer 
    
- Sito di contoso SharePoint 
    
- Contenuto di contoso SharePoint 
    
Durante l'esecuzione dell'applicazione nella Farm di SharePoint Services invia una query di stato per il Proxy dell'esecuzione dell'applicazione nella Farm di contenuto di SharePoint, si verificano le seguenti operazioni: 
  
- Il proxy dell'esecuzione dell'applicazione nella Farm di contenuto di SharePoint invia una query in attesa di risposta di azioni/stato processo Timer. 
    
- Il processo Timer invia una richiesta al sito di SharePoint di Contoso, che viene esaminato il contenuto di SharePoint di Contoso. 
    
- Viene inviata la risposta alla query azioni/dello stato in sospeso provenienti dal processo Timer per il proxy dell'esecuzione dell'applicazione nella Farm di contenuto di SharePoint e quindi viene inviato al servizio di esecuzione dell'applicazione nella Farm di servizi di SharePoint 
    
#### <a name="exchange-2013"></a>Exchange 2013

Il componente server Exchange 2013 contiene il servizio Web di Exchange e fornisce le operazioni seguenti: 
  
- Relazione di Trust da server a server/OAuth viene gestita tra la Farm di contenuto di SharePoint 2013 ed Exchange 2013. 
    
- Relazione di Trust da server a server/OAuth viene gestita tra Exchange 2013 e Lync 2013. 
    
#### <a name="lync-2013"></a>Lync 2013

Il componente di Lync 2013 archivia Lync contenuto di Exchange 2013. 
  
#### <a name="windows-file-shares"></a>Condivisioni di File di Windows

Il componente di condivisioni di File Windows fornisce i risultati di ricerca per indicizzazione per l'esecuzione dell'applicazione nella Farm di servizi di SharePoint. 
  
### <a name="legend"></a>Legenda

La legenda figura mostra graficamente i diversi tipi di traffico riportato tra i componenti nelle diverse righe colorate come indicato di seguito: 
  
- Linea di colore blu chiaro: Query/azione: dati di query o l'azione di eDiscovery 
    
- Linea arancione: risposta eDisovery - dati risposta delle query di eDiscovery 
    
- Verde linea: stato query/risposta - dati di query/risposta lo stato di eDiscovery 
    
- Viola riga: Exchange/stato dell'azione richiesta - eDiscovery per stato dell'azione per il traffico di Exchange. 
    
- Linea rossa: Exchange risposta/lo stato dei dati - risposta lo stato o query di eDiscovery da Exchange. 
    
- Riga nero con punti: Trust da Server a Server/Oauth 
    
- Linea continua nero: risultati di ricerca per indicizzazione / 
    

