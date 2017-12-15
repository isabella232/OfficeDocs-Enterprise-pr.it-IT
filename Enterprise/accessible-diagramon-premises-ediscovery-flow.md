---
title: Diagramma accessibile - eDiscovery locale flusso
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: "In questo articolo è una versione testo accessibile del diagramma denominato eDiscovery locale flusso."
ms.openlocfilehash: de94fc2af94df47a83f4a7847a84cd18131f637e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a><span data-ttu-id="48652-103">Diagramma accessibile - eDiscovery locale flusso</span><span class="sxs-lookup"><span data-stu-id="48652-103">Accessible diagram - On-premises eDiscovery Flow</span></span>

<span data-ttu-id="48652-104">**Riepilogo:** In questo articolo è una versione testo accessibile del diagramma denominato eDiscovery locale flusso.</span><span class="sxs-lookup"><span data-stu-id="48652-104">**Summary:** This article is an accessible text version of the diagram named On-premises eDiscovery Flow.</span></span>
  
<span data-ttu-id="48652-105">Questo poster fornisce informazioni dettagliate sull'architettura e flusso di dati tra i prodotti server.</span><span class="sxs-lookup"><span data-stu-id="48652-105">This poster provides details about the architecture and flow of data across server products.</span></span> 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a><span data-ttu-id="48652-106">In SharePoint, Exchange, Lync e condivisioni di file</span><span class="sxs-lookup"><span data-stu-id="48652-106">Across SharePoint, Exchange, Lync, and file shares</span></span>

<span data-ttu-id="48652-p101">Il diagramma mostra un utente che invia una query che accede a due server farm, una Farm di SharePoint 2013 Enterprise App e una Farm di servizi di SharePoint 2013. Farm di servizi di SharePoint 2013 comunica con una Farm di SharePoint 2013 il contenuto, Exchange Server 2013 (che comunica con Lync 2013) e le condivisioni di File di Windows.</span><span class="sxs-lookup"><span data-stu-id="48652-p101">The diagram shows a user sending a query that accesses two server farms, a SharePoint 2013 Enterprise App Farm, and a SharePoint 2013 Services Farm. The SharePoint 2013 Services Farm communicates with a SharePoint 2013 Content Farm, Exchange Server 2013 (which communicates with Lync 2013), and Windows File Shares.</span></span> 
  
<span data-ttu-id="48652-109">EDiscovery flusso elenco vengono descritti il flusso di dati e l'ordine in cui eDisovery azioni di query si verificano in SharePoint, Exchange, Lync e condivisioni di file.</span><span class="sxs-lookup"><span data-stu-id="48652-109">The eDiscovery Flow List describes the flow of data and the order in which eDisovery query actions occur across SharePoint, Exchange, Lync, and file shares.</span></span> 
  
<span data-ttu-id="48652-110">Nell'elenco di flusso di eDiscovery è descritto dettagliatamente in primo luogo, seguito da una descrizione dettagliata delle caratteristiche illustrato nel diagramma.</span><span class="sxs-lookup"><span data-stu-id="48652-110">The eDiscovery flow list is described in detail first, followed by a detailed description of the features depicted in the diagram.</span></span> 
  
### <a name="ediscovery-flow-list"></a><span data-ttu-id="48652-111">eDiscovery flusso elenco</span><span class="sxs-lookup"><span data-stu-id="48652-111">eDiscovery Flow List</span></span>

<span data-ttu-id="48652-p102">I numeri per ognuno dei passaggi descritti in questo elenco sono relativi a un passaggio illustrato nel diagramma. Nel diagramma è descritto in dettaglio più avanti in questo documento.</span><span class="sxs-lookup"><span data-stu-id="48652-p102">The numbers for each of the steps described in this list pertain to a step depicted in the diagram. The diagram is described in detail later in this document.</span></span> 
  
1. <span data-ttu-id="48652-p103">casi di eDiscovery vengono creati, gestiti e utilizzati in eDiscovery center (EDC). Il EDC è una raccolta siti di SharePoint 2013. Si tratta di cui vengono definiti i casi, vengono identificate origini per tenere traccia, query vengono inviate, vengono esaminati i risultati delle query ed esenzioni contenuti vengono inseriti o rimossi.</span><span class="sxs-lookup"><span data-stu-id="48652-p103">eDiscovery cases are created, managed, and used in the eDiscovery center (EDC). The EDC is a SharePoint 2013 site collection. This is where cases are defined, sources to be tracked are identified, queries are issued, query results are reviewed, and holds on content are placed or removed.</span></span> 
    
2. <span data-ttu-id="48652-p104">La query di eDiscovery o azione, ad esempio posto un'esenzione, ReleaseHold o GetStatus, viene inoltrata dal EDC al proxy di applicazione di servizio di ricerca (SSA) nella Farm di applicazione Enterprise. Il proxy SSA inoltra quindi il traffico per l'esecuzione dell'applicazione nella Farm di servizi di App. In questo esempio, la richiesta deve posizionerà nulla nella Farm di contenuto di SharePoint con "CONTOSO" nel nome del file in attesa.</span><span class="sxs-lookup"><span data-stu-id="48652-p104">The eDiscovery query or action, such as place a Hold, ReleaseHold, or GetStatus, is relayed from the EDC to the Search Service Application (SSA) proxy in the Enterprise App Farm. The SSA proxy then relays the traffic to the SSA in the Services App Farm. In this example, the request is to place anything in the SharePoint Content Farm with "CONTOSO" in the file name on hold.</span></span> 
    
3. <span data-ttu-id="48652-p105">Se la richiesta di un caso di query, l'esecuzione dell'applicazione consulta l'indice di ricerca. Quindi, il set di risultati di query eDiscovery restituisce all'utente tramite il EDC.</span><span class="sxs-lookup"><span data-stu-id="48652-p105">If the request is to query a case, the SSA consults the search index. Then, the eDiscovery query result set returns to the user through the EDC.</span></span> 
    
4. <span data-ttu-id="48652-p106">Se la richiesta di un'azione, ad esempio luogo una conservazione o ReleaseHold, tale azione viene scritta in Actions_Table nel database di amministrazione di esecuzione dell'applicazione. In questo esempio viene scritto il Actions_Table una richiesta di attesa per qualsiasi nella Farm di contenuto di SharePoint con "CONTOSO".</span><span class="sxs-lookup"><span data-stu-id="48652-p106">If the request is an action, such as place a Hold or ReleaseHold, that action is written to the Actions_Table in the SSA Administrative database. In this example, a hold request for anything in the SharePoint Content Farm with "CONTOSO" is written to the Actions_Table.</span></span> 
    
5. <span data-ttu-id="48652-124">A intervalli regolari il Farm di contenuto eDiscovery sul posto archiviazione processo timer riattiva e genera una richiesta di azioni in sospeso e invia gli aggiornamenti dello stato attraverso il proxy di esecuzione dell'applicazione per l'esecuzione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="48652-124">At regular intervals the Content Farm eDiscovery in-place hold timer job wakes up and generates a request for pending actions and sends status updates through the SSA proxy to the SSA.</span></span> 
    
6. <span data-ttu-id="48652-p107">La query per azioni in sospeso viene inoltrata per l'esecuzione dell'applicazione centrale, che consulta il Action_Table per le azioni per la Farm di contenuto in sospeso. Il processo timer di archiviazione sul posto di Farm di contenuto invia inoltre gli aggiornamenti di stato per gli oggetti e le azioni ha ricevuto, che vengono scritti i ActionsTable.</span><span class="sxs-lookup"><span data-stu-id="48652-p107">The query for pending actions is relayed to the central SSA, which consults the Action_Table for any pending actions for the Content Farm. The Content Farm in-place hold timer job also sends status updates for objects and actions it has received, which are written to the ActionsTable.</span></span> 
    
7. <span data-ttu-id="48652-127">La richiesta di attesa per qualsiasi contenuto con "CONTOSO" nel nome della Farm di SharePoint 2013 il contenuto viene inviata per l'esecuzione dell'applicazione per il processo timer di archiviazione sul posto di eDiscovery della farm di contenuto.</span><span class="sxs-lookup"><span data-stu-id="48652-127">The hold request for any content with "CONTOSO" in the name in the SharePoint 2013 Content Farm is sent by the SSA to the eDiscovery in-place hold timer job in the Content Farm.</span></span> 
    
8. <span data-ttu-id="48652-128">Archiviazione la eDiscovery sul posto timer posizioni processo il "CONTOSO sito" e "CONTOSO contenuto" in attesa.</span><span class="sxs-lookup"><span data-stu-id="48652-128">The eDiscovery in-place hold timer job places the "CONTOSO Site" and "CONTOSO content" on hold.</span></span> 
    
9. <span data-ttu-id="48652-129">Il processo timer di archiviazione sul posto di eDiscovery viene eseguito periodicamente nella Farm di applicazione Enterprise per verificare lo stato delle azioni di individuazione e per aggiornare lo stato.</span><span class="sxs-lookup"><span data-stu-id="48652-129">The eDiscovery in-place hold timer job periodically runs in the Enterprise App Farm to check the status of discovery actions and to update the status.</span></span> 
    
10. <span data-ttu-id="48652-130">La query di stato viene inoltrata attraverso il proxy di esecuzione dell'applicazione Enterprise App Farm per l'esecuzione dell'applicazione Farm di servizi di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="48652-130">The status query is relayed through the Enterprise App Farm SSA proxy to the SharePoint Services Farm SSA.</span></span> 
    
11. <span data-ttu-id="48652-131">L'esecuzione dell'applicazione viene recuperato lo stato dalla tabella azioni e restituisce il processo timer nella Farm di applicazione Enterprise, che inserisce gli aggiornamenti di stato per il EDC.</span><span class="sxs-lookup"><span data-stu-id="48652-131">The SSA retrieves the status from the Actions table and returns it to the timer job in the Enterprise App Farm, which pushes the status updates to the EDC.</span></span> 
    
12. <span data-ttu-id="48652-p108">Quando l'utente di eDiscovery è la ricerca (o eseguendo un'azione) per le origini di Exchange, ad esempio una cassetta postale o contenuto archiviato Lync, l'esecuzione dell'applicazione centrale viene utilizzato il proxy di servizi Web Exchange (EWS) per eseguire una query servizi Web Exchange. Exchange è disponibile il proprio infrastruttura di ricerca ed eDiscovery e gestisce tutte le chiamate di eDiscovery internamente.</span><span class="sxs-lookup"><span data-stu-id="48652-p108">When the eDiscovery user is searching (or performing an action) for Exchange sources, such as a mailbox or archived Lync content, the central SSA uses Exchange Web Services (EWS) proxy to query Exchange Web Services. Exchange has its own search and eDiscovery infrastructure and manages all eDiscovery calls internally.</span></span> 
    
13. <span data-ttu-id="48652-134">Servizi Web Exchange risponde a esecuzione dell'applicazione con i risultati della ricerca eDiscovery o una risposta a una richiesta di stato per un'esenzione basata su query, che a sua volta, ottiene inoltrata al EDC.</span><span class="sxs-lookup"><span data-stu-id="48652-134">Exchange Web Services responds to SSA with eDiscovery search results or a response to a status request for a query-based hold, which, in turn, gets relayed to the EDC.</span></span> 
    
#### <a name="prerequisites"></a><span data-ttu-id="48652-135">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="48652-135">Prerequisites</span></span>

- <span data-ttu-id="48652-136">Nell'indice di ricerca contenuti organizzazione SharePoint deve essere configurato correttamente si verificano ricerche per indicizzazione su origini di contenuto (SharePoint e Windows condivisioni di file), e tutte le origini di contenuto.</span><span class="sxs-lookup"><span data-stu-id="48652-136">SharePoint Enterprise Search must be configured, search crawls on content sources (SharePoint and Windows file shares) are successfully occurring, and all content sources are in the index.</span></span> 
    
- <span data-ttu-id="48652-137">Necessario configurare l'autenticazione e la relazione di trust da server a server tra Farm di SharePoint Services ed Exchange e anche tra Exchange e Lync.</span><span class="sxs-lookup"><span data-stu-id="48652-137">Server-to-server trust and authentication must be configured between the SharePoint Services Farm and Exchange and also between Exchange and Lync.</span></span> 
    
### <a name="description-of-components-in-the-diagram"></a><span data-ttu-id="48652-138">Descrizione dei componenti del diagramma</span><span class="sxs-lookup"><span data-stu-id="48652-138">Description of components in the diagram</span></span>

<span data-ttu-id="48652-p109">Il diagramma mostra un utente che invia una query, che accede a due server farm, una Farm di SharePoint 2013 Enterprise App e una Farm di servizi di SharePoint 2013. Interfacce di Farm di servizi di SharePoint con una Farm di SharePoint 2013 il contenuto, Exchange Server 2013 (in cui si interfaccia con Lync 2013) e le condivisioni di File di Windows.</span><span class="sxs-lookup"><span data-stu-id="48652-p109">The diagram shows a user sending a query, which accesses two server farms, a SharePoint 2013 Enterprise App Farm and a SharePoint 2013 Services Farm. The SharePoint Services Farm interfaces with a SharePoint 2013 Content Farm, Exchange Server 2013 (which interfaces with Lync 2013), and Windows File Shares.</span></span> 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a><span data-ttu-id="48652-141">Farm di SharePoint 2013 Enterprise App</span><span class="sxs-lookup"><span data-stu-id="48652-141">SharePoint 2013 Enterprise App Farm</span></span>

<span data-ttu-id="48652-142">Farm di SharePoint 2013 Enterprise App include i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="48652-142">The SharePoint 2013 Enterprise App Farm contains the following components:</span></span> 
  
- <span data-ttu-id="48652-143">EDC</span><span class="sxs-lookup"><span data-stu-id="48652-143">EDC</span></span>
    
- <span data-ttu-id="48652-144">Proxy di esecuzione dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="48652-144">SSA proxy</span></span> 
    
- <span data-ttu-id="48652-145">Processo timer</span><span class="sxs-lookup"><span data-stu-id="48652-145">Timer job</span></span> 
    
<span data-ttu-id="48652-p110">Una query o azione inviati dall'utente viene inviato a EDC nella Farm di applicazione Enterprise. Si verifica quanto segue:</span><span class="sxs-lookup"><span data-stu-id="48652-p110">A query or action sent by the user is sent to the EDC in the Enterprise App Farm. The following actions occur:</span></span> 
  
- <span data-ttu-id="48652-148">La query o l'azione viene inoltrata al proxy di esecuzione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="48652-148">The query or action goes to the SSA proxy.</span></span> 
    
- <span data-ttu-id="48652-p111">Il proxy dell'esecuzione dell'applicazione invia una query sullo stato o una risposta per il processo Timer della farm di applicazioni Enterprise e consente inoltre di inviare una query sullo stato o una risposta al servizio di esecuzione dell'applicazione nella Farm di servizi di SharePoint. Azioni risultanti da ciò sono descritte nella sezione sulla Farm di servizi di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="48652-p111">The SSA proxy sends a status query or response to the Timer job in the Enterprise App Farm, and it also sends a status query or response to the SSA service in the SharePoint Services Farm. The actions that result from this are described in the section about the SharePoint Services Farm.</span></span> 
    
- <span data-ttu-id="48652-151">Quando riceve una risposta, il processo Timer invia la risposta per il proxy dell'esecuzione dell'applicazione e il EDC.</span><span class="sxs-lookup"><span data-stu-id="48652-151">When it receives a response, the Timer job sends the response to the SSA proxy and to the EDC.</span></span> 
    
- <span data-ttu-id="48652-152">Risultati di query o azione vengono inviati all'utente dal EDC.</span><span class="sxs-lookup"><span data-stu-id="48652-152">Any results from the query or action are sent to the user from the EDC.</span></span> 
    
#### <a name="sharepoint-2013-services-farm"></a><span data-ttu-id="48652-153">Farm di servizi di SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="48652-153">SharePoint 2013 Services Farm</span></span>

<span data-ttu-id="48652-154">Farm di servizi di SharePoint 2013 include i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="48652-154">The SharePoint 2013 Services Farm contains the following components:</span></span> 
  
- <span data-ttu-id="48652-155">Esecuzione dell'applicazione servizio</span><span class="sxs-lookup"><span data-stu-id="48652-155">SSA Service</span></span> 
    
- <span data-ttu-id="48652-156">Database di indice di ricerca</span><span class="sxs-lookup"><span data-stu-id="48652-156">Search index database</span></span> 
    
- <span data-ttu-id="48652-p112">Database admin_db esecuzione dell'applicazione. Contiene la tabella azioni nel database: archiviazione versione attesa GetStatus</span><span class="sxs-lookup"><span data-stu-id="48652-p112">SSA admin_db database. The Actions Table in this database contains: Hold Release Hold GetStatus</span></span> 
    
- <span data-ttu-id="48652-159">Proxy di servizi Web Exchange</span><span class="sxs-lookup"><span data-stu-id="48652-159">EWS proxy</span></span> 
    
<span data-ttu-id="48652-160">Quando il proxy dell'esecuzione dell'applicazione nella Farm di SharePoint Enterprise App invia una query di stato per l'esecuzione dell'applicazione nella Farm di servizi di SharePoint, si verificano le seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="48652-160">When the SSA proxy in the SharePoint Enterprise App Farm sends a status query to the SSA in the SharePoint Services Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="48652-p113">Se la richiesta di una query, l'esecuzione dell'applicazione consulta l'indice di ricerca. La risposta di individuazione verrà restituita per l'esecuzione dell'applicazione e quindi all'utente tramite il EDC.</span><span class="sxs-lookup"><span data-stu-id="48652-p113">If the request is a query, the SSA consults the search index. The discovery response is returned to the SSA and then to the user through the EDC.</span></span> 
    
- <span data-ttu-id="48652-163">Se la richiesta è un'operazione di scrittura, il servizio SSA invia l'azione di scrittura per l'esecuzione dell'applicazione admin_db.</span><span class="sxs-lookup"><span data-stu-id="48652-163">If the request is a write action, the SSA service sends the write action to the SSA admin_db.</span></span> 
    
- <span data-ttu-id="48652-164">Una ricerca per indicizzazione e risponde risultati richiesta viene inviata dall'esecuzione dell'applicazione per la Farm di contenuto di SharePoint 2013 e viene restituita una risposta per l'esecuzione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="48652-164">A crawl and responding results request is sent from the SSA to the SharePoint 2013 Content Farm and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="48652-165">Una ricerca per indicizzazione e risponde risultati richiesta viene inviata dall'esecuzione dell'applicazione per le condivisioni di File di Windows e viene restituita una risposta per l'esecuzione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="48652-165">A crawl and responding results request is sent from the SSA to the Windows File Shares, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="48652-166">Invio di una query per le azioni, le risposte o gli aggiornamenti dello stato in sospeso dall'esecuzione dell'applicazione per il proxy dell'esecuzione dell'applicazione nella Farm di contenuto di SharePoint e viene restituita una risposta per l'esecuzione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="48652-166">A query for pending action(s), responses, or status updates is sent from the SSA to the SSA proxy in the SharePoint Content Farm, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="48652-167">Viene inviata una richiesta di stato dell'azione/Exchange dall'esecuzione dell'applicazione per il proxy di servizi Web Exchange, che invia una richiesta di stato dell'azione/Exchange Query al servizio Web di Exchange sul server Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="48652-167">An Exchange action/status request is sent from the SSA to the EWS proxy, which sends an Exchange Query action/status request to the Exchange Web Service on the Exchange 2013 server.</span></span> 
    
- <span data-ttu-id="48652-168">Una query/risposta sullo stato viene inviata dall'esecuzione dell'applicazione a admin_db esecuzione dell'applicazione e vengono restituita per l'esecuzione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="48652-168">A status query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
- <span data-ttu-id="48652-169">Un'operazione in sospeso query/risposta inviata dall'esecuzione dell'applicazione per l'esecuzione dell'applicazione admin_db e viene restituita per l'esecuzione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="48652-169">A pending action query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
#### <a name="sharepoint-2013-content-farm"></a><span data-ttu-id="48652-170">Farm di contenuto di SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="48652-170">SharePoint 2013 Content Farm</span></span>

<span data-ttu-id="48652-171">Farm di contenuto di SharePoint 2013 include i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="48652-171">The SharePoint 2013 Content Farm contains the following components:</span></span> 
  
- <span data-ttu-id="48652-172">Proxy di esecuzione dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="48652-172">SSA proxy</span></span> 
    
- <span data-ttu-id="48652-173">Processo timer</span><span class="sxs-lookup"><span data-stu-id="48652-173">Timer job</span></span> 
    
- <span data-ttu-id="48652-174">Sito di contoso SharePoint</span><span class="sxs-lookup"><span data-stu-id="48652-174">Contoso SharePoint site</span></span> 
    
- <span data-ttu-id="48652-175">Contenuto di contoso SharePoint</span><span class="sxs-lookup"><span data-stu-id="48652-175">Contoso SharePoint content</span></span> 
    
<span data-ttu-id="48652-176">Durante l'esecuzione dell'applicazione nella Farm di SharePoint Services invia una query di stato per il Proxy dell'esecuzione dell'applicazione nella Farm di contenuto di SharePoint, si verificano le seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="48652-176">When the SSA in the SharePoint Services Farm sends a status query to the SSA Proxy in the SharePoint Content Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="48652-177">Il proxy dell'esecuzione dell'applicazione nella Farm di contenuto di SharePoint invia una query in attesa di risposta di azioni/stato processo Timer.</span><span class="sxs-lookup"><span data-stu-id="48652-177">The SSA proxy in the SharePoint Content Farm sends a query for pending actions/status response to the Timer job.</span></span> 
    
- <span data-ttu-id="48652-178">Il processo Timer invia una richiesta al sito di SharePoint di Contoso, che viene esaminato il contenuto di SharePoint di Contoso.</span><span class="sxs-lookup"><span data-stu-id="48652-178">The Timer job sends a request to the Contoso SharePoint site, which reviews the Contoso SharePoint content.</span></span> 
    
- <span data-ttu-id="48652-179">Viene inviata la risposta alla query azioni/dello stato in sospeso provenienti dal processo Timer per il proxy dell'esecuzione dell'applicazione nella Farm di contenuto di SharePoint e quindi viene inviato al servizio di esecuzione dell'applicazione nella Farm di servizi di SharePoint</span><span class="sxs-lookup"><span data-stu-id="48652-179">The response to the pending actions/status query is sent from the Timer job to the SSA proxy in the SharePoint Content Farm, and then it is sent to the SSA service in the SharePoint Services Farm</span></span> 
    
#### <a name="exchange-2013"></a><span data-ttu-id="48652-180">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="48652-180">Exchange 2013</span></span>

<span data-ttu-id="48652-181">Il componente server Exchange 2013 contiene il servizio Web di Exchange e fornisce le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="48652-181">The Exchange 2013 server component contains the Exchange Web Service and provides the following:</span></span> 
  
- <span data-ttu-id="48652-182">Relazione di Trust da server a server/OAuth viene gestita tra la Farm di contenuto di SharePoint 2013 ed Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="48652-182">Server-to-server Trust/OAuth is handled between the SharePoint 2013 Content Farm and Exchange 2013.</span></span> 
    
- <span data-ttu-id="48652-183">Relazione di Trust da server a server/OAuth viene gestita tra Exchange 2013 e Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="48652-183">Server-to-server Trust/OAuth is handled between Exchange 2013 and Lync 2013.</span></span> 
    
#### <a name="lync-2013"></a><span data-ttu-id="48652-184">Lync 2013</span><span class="sxs-lookup"><span data-stu-id="48652-184">Lync 2013</span></span>

<span data-ttu-id="48652-185">Il componente di Lync 2013 archivia Lync contenuto di Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="48652-185">The Lync 2013 component archives Lync content in Exchange 2013.</span></span> 
  
#### <a name="windows-file-shares"></a><span data-ttu-id="48652-186">Condivisioni di File di Windows</span><span class="sxs-lookup"><span data-stu-id="48652-186">Windows File Shares</span></span>

<span data-ttu-id="48652-187">Il componente di condivisioni di File Windows fornisce i risultati di ricerca per indicizzazione per l'esecuzione dell'applicazione nella Farm di servizi di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="48652-187">The Windows File Shares component provides crawl results to the SSA in the SharePoint Services Farm.</span></span> 
  
### <a name="legend"></a><span data-ttu-id="48652-188">Legenda</span><span class="sxs-lookup"><span data-stu-id="48652-188">Legend</span></span>

<span data-ttu-id="48652-189">La legenda figura mostra graficamente i diversi tipi di traffico riportato tra i componenti nelle diverse righe colorate come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="48652-189">The legend for this diagram graphically shows the different types of traffic depicted among the components in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="48652-190">Linea di colore blu chiaro: Query/azione: dati di query o l'azione di eDiscovery</span><span class="sxs-lookup"><span data-stu-id="48652-190">Light blue line: Query/action - eDiscovery query or action data</span></span> 
    
- <span data-ttu-id="48652-191">Linea arancione: risposta eDisovery - dati risposta delle query di eDiscovery</span><span class="sxs-lookup"><span data-stu-id="48652-191">Orange line: eDisovery response - eDiscovery query response data</span></span> 
    
- <span data-ttu-id="48652-192">Verde linea: stato query/risposta - dati di query/risposta lo stato di eDiscovery</span><span class="sxs-lookup"><span data-stu-id="48652-192">Green line: Status query/response - eDiscovery status query/response data</span></span> 
    
- <span data-ttu-id="48652-193">Viola riga: Exchange/stato dell'azione richiesta - eDiscovery per stato dell'azione per il traffico di Exchange.</span><span class="sxs-lookup"><span data-stu-id="48652-193">Purple line: Exchange action/status request - eDiscovery request for action status for Exchange traffic.</span></span> 
    
- <span data-ttu-id="48652-194">Linea rossa: Exchange risposta/lo stato dei dati - risposta lo stato o query di eDiscovery da Exchange.</span><span class="sxs-lookup"><span data-stu-id="48652-194">Red line: Exchange data/status response - eDiscovery query or status response from Exchange.</span></span> 
    
- <span data-ttu-id="48652-195">Riga nero con punti: Trust da Server a Server/Oauth</span><span class="sxs-lookup"><span data-stu-id="48652-195">Dotted black line: Server-to-Server Trust/Oauth</span></span> 
    
- <span data-ttu-id="48652-196">Linea continua nero: risultati di ricerca per indicizzazione /</span><span class="sxs-lookup"><span data-stu-id="48652-196">Solid black line: Crawl/results</span></span> 
    

