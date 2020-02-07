---
title: Diagramma accessibile-flusso eDiscovery locale
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
f1.keywords:
- NOCSH
description: Questo articolo è una versione di testo accessibile del diagramma denominato flusso eDiscovery locale.
ms.openlocfilehash: ec9ecf7d3663503f2da412364d919a6c70032e23
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843857"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a><span data-ttu-id="8acc5-103">Diagramma accessibile-flusso eDiscovery locale</span><span class="sxs-lookup"><span data-stu-id="8acc5-103">Accessible diagram - On-premises eDiscovery Flow</span></span>

<span data-ttu-id="8acc5-104">**Riepilogo:** Questo articolo è una versione di testo accessibile del diagramma denominato flusso eDiscovery locale.</span><span class="sxs-lookup"><span data-stu-id="8acc5-104">**Summary:** This article is an accessible text version of the diagram named On-premises eDiscovery Flow.</span></span>
  
<span data-ttu-id="8acc5-105">Questo poster fornisce informazioni dettagliate sull'architettura e sul flusso dei dati tra i prodotti server.</span><span class="sxs-lookup"><span data-stu-id="8acc5-105">This poster provides details about the architecture and flow of data across server products.</span></span> 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a><span data-ttu-id="8acc5-106">Condivisioni di SharePoint, Exchange, Lync e file</span><span class="sxs-lookup"><span data-stu-id="8acc5-106">Across SharePoint, Exchange, Lync, and file shares</span></span>

<span data-ttu-id="8acc5-107">Nel diagramma viene visualizzato un utente che invia una query che accede a due server farm, una farm di app SharePoint 2013 Enterprise e una farm di servizi di SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="8acc5-107">The diagram shows a user sending a query that accesses two server farms, a SharePoint 2013 Enterprise App Farm, and a SharePoint 2013 Services Farm.</span></span> <span data-ttu-id="8acc5-108">La farm di SharePoint 2013 Services comunica con una farm di contenuto di SharePoint 2013, Exchange Server 2013 (che comunica con Lync 2013) e condivisioni file di Windows.</span><span class="sxs-lookup"><span data-stu-id="8acc5-108">The SharePoint 2013 Services Farm communicates with a SharePoint 2013 Content Farm, Exchange Server 2013 (which communicates with Lync 2013), and Windows File Shares.</span></span> 
  
<span data-ttu-id="8acc5-109">L'elenco di flusso di eDiscovery descrive il flusso di dati e l'ordine in cui si verificano le azioni di query di eDisovery tra SharePoint, Exchange, Lync e le condivisioni di file.</span><span class="sxs-lookup"><span data-stu-id="8acc5-109">The eDiscovery Flow List describes the flow of data and the order in which eDisovery query actions occur across SharePoint, Exchange, Lync, and file shares.</span></span> 
  
<span data-ttu-id="8acc5-110">L'elenco di flusso di eDiscovery viene descritto in dettaglio per primo, seguito da una descrizione dettagliata delle caratteristiche descritte nel diagramma.</span><span class="sxs-lookup"><span data-stu-id="8acc5-110">The eDiscovery flow list is described in detail first, followed by a detailed description of the features depicted in the diagram.</span></span> 
  
### <a name="ediscovery-flow-list"></a><span data-ttu-id="8acc5-111">Elenco dei flussi di eDiscovery</span><span class="sxs-lookup"><span data-stu-id="8acc5-111">eDiscovery Flow List</span></span>

<span data-ttu-id="8acc5-112">I numeri per ogni procedura descritta in questo elenco sono relativi a un passaggio illustrato nel diagramma.</span><span class="sxs-lookup"><span data-stu-id="8acc5-112">The numbers for each of the steps described in this list pertain to a step depicted in the diagram.</span></span> <span data-ttu-id="8acc5-113">Il diagramma è descritto in dettaglio più avanti in questo documento.</span><span class="sxs-lookup"><span data-stu-id="8acc5-113">The diagram is described in detail later in this document.</span></span> 
  
1. <span data-ttu-id="8acc5-114">i casi di eDiscovery vengono creati, gestiti e utilizzati in eDiscovery Center (EDC).</span><span class="sxs-lookup"><span data-stu-id="8acc5-114">eDiscovery cases are created, managed, and used in the eDiscovery center (EDC).</span></span> <span data-ttu-id="8acc5-115">EDC è una raccolta siti di SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="8acc5-115">The EDC is a SharePoint 2013 site collection.</span></span> <span data-ttu-id="8acc5-116">Di seguito vengono definiti i casi, vengono identificate le fonti da tenere presenti, vengono rilasciate le query, vengono esaminati i risultati delle query e il contenuto viene inserito o rimosso.</span><span class="sxs-lookup"><span data-stu-id="8acc5-116">This is where cases are defined, sources to be tracked are identified, queries are issued, query results are reviewed, and holds on content are placed or removed.</span></span> 
    
2. <span data-ttu-id="8acc5-117">La query o l'azione eDiscovery, ad esempio Place a Hold, ReleaseHold o GetStatus, viene inoltrata dall'EDC al proxy dell'applicazione del servizio di ricerca (SSA) nella farm di app Enterprise.</span><span class="sxs-lookup"><span data-stu-id="8acc5-117">The eDiscovery query or action, such as place a Hold, ReleaseHold, or GetStatus, is relayed from the EDC to the Search Service Application (SSA) proxy in the Enterprise App Farm.</span></span> <span data-ttu-id="8acc5-118">Il proxy SSA inoltra quindi il traffico all'SSA nella farm di applicazioni dei servizi.</span><span class="sxs-lookup"><span data-stu-id="8acc5-118">The SSA proxy then relays the traffic to the SSA in the Services App Farm.</span></span> <span data-ttu-id="8acc5-119">In questo esempio, la richiesta è quella di inserire qualsiasi elemento nella farm del contenuto di SharePoint con "CONTOSO" nel nome del file in attesa.</span><span class="sxs-lookup"><span data-stu-id="8acc5-119">In this example, the request is to place anything in the SharePoint Content Farm with "CONTOSO" in the file name on hold.</span></span> 
    
3. <span data-ttu-id="8acc5-120">Se la richiesta è quella di eseguire una query su un caso, il SSA consulterà l'indice di ricerca.</span><span class="sxs-lookup"><span data-stu-id="8acc5-120">If the request is to query a case, the SSA consults the search index.</span></span> <span data-ttu-id="8acc5-121">Successivamente, il set di risultati di query di eDiscovery torna all'utente tramite EDC.</span><span class="sxs-lookup"><span data-stu-id="8acc5-121">Then, the eDiscovery query result set returns to the user through the EDC.</span></span> 
    
4. <span data-ttu-id="8acc5-122">Se la richiesta è un'azione, ad esempio un blocco o un ReleaseHold, tale azione viene scritta nel Actions_Table nel database amministrativo SSA.</span><span class="sxs-lookup"><span data-stu-id="8acc5-122">If the request is an action, such as place a Hold or ReleaseHold, that action is written to the Actions_Table in the SSA Administrative database.</span></span> <span data-ttu-id="8acc5-123">In questo esempio, una richiesta di archiviazione per qualsiasi elemento nella farm del contenuto di SharePoint con "CONTOSO" viene scritta nel Actions_Table.</span><span class="sxs-lookup"><span data-stu-id="8acc5-123">In this example, a hold request for anything in the SharePoint Content Farm with "CONTOSO" is written to the Actions_Table.</span></span> 
    
5. <span data-ttu-id="8acc5-124">A intervalli regolari la farm di contenuto eDiscovery il processo timer del blocco sul posto viene riattivato e genera una richiesta per le azioni in sospeso e invia gli aggiornamenti dello stato tramite il proxy SSA al SSA.</span><span class="sxs-lookup"><span data-stu-id="8acc5-124">At regular intervals the Content Farm eDiscovery in-place hold timer job wakes up and generates a request for pending actions and sends status updates through the SSA proxy to the SSA.</span></span> 
    
6. <span data-ttu-id="8acc5-125">La query per le azioni in sospeso viene inoltrata al SSA centrale, che consulta la Action_Table per tutte le azioni in sospeso per la farm di contenuto.</span><span class="sxs-lookup"><span data-stu-id="8acc5-125">The query for pending actions is relayed to the central SSA, which consults the Action_Table for any pending actions for the Content Farm.</span></span> <span data-ttu-id="8acc5-126">Il processo timer della farm di contenuto consente inoltre di inviare gli aggiornamenti di stato per gli oggetti e le azioni ricevuti, scritti in ActionsTable.</span><span class="sxs-lookup"><span data-stu-id="8acc5-126">The Content Farm in-place hold timer job also sends status updates for objects and actions it has received, which are written to the ActionsTable.</span></span> 
    
7. <span data-ttu-id="8acc5-127">La richiesta di archiviazione per qualsiasi contenuto con "CONTOSO" nel nome nella farm di contenuto di SharePoint 2013 viene inviata da SSA al processo timer di archiviazione sul posto di eDiscovery nella farm di contenuto.</span><span class="sxs-lookup"><span data-stu-id="8acc5-127">The hold request for any content with "CONTOSO" in the name in the SharePoint 2013 Content Farm is sent by the SSA to the eDiscovery in-place hold timer job in the Content Farm.</span></span> 
    
8. <span data-ttu-id="8acc5-128">Il processo timer di archiviazione sul posto di eDiscovery inserisce in attesa il "sito CONTOSO" e il "contenuto CONTOSO".</span><span class="sxs-lookup"><span data-stu-id="8acc5-128">The eDiscovery in-place hold timer job places the "CONTOSO Site" and "CONTOSO content" on hold.</span></span> 
    
9. <span data-ttu-id="8acc5-129">Il processo timer per il blocco sul posto di eDiscovery viene eseguito periodicamente nella farm dell'applicazione Enterprise per controllare lo stato delle azioni di individuazione e per aggiornare lo stato.</span><span class="sxs-lookup"><span data-stu-id="8acc5-129">The eDiscovery in-place hold timer job periodically runs in the Enterprise App Farm to check the status of discovery actions and to update the status.</span></span> 
    
10. <span data-ttu-id="8acc5-130">La query di stato viene inoltrata tramite il proxy SSA farm dell'applicazione Enterprise all'SSA farm di SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="8acc5-130">The status query is relayed through the Enterprise App Farm SSA proxy to the SharePoint Services Farm SSA.</span></span> 
    
11. <span data-ttu-id="8acc5-131">Il SSA recupera lo stato dalla tabella Actions e lo restituisce al processo timer nella farm Enterprise app, che inserisce gli aggiornamenti dello stato in EDC.</span><span class="sxs-lookup"><span data-stu-id="8acc5-131">The SSA retrieves the status from the Actions table and returns it to the timer job in the Enterprise App Farm, which pushes the status updates to the EDC.</span></span> 
    
12. <span data-ttu-id="8acc5-132">Quando l'utente di eDiscovery esegue la ricerca o l'esecuzione di un'azione per le origini di Exchange, ad esempio una cassetta postale o un contenuto Lync archiviato, la SSA centrale utilizza il proxy di servizi Web Exchange (EWS) per eseguire query sui servizi Web di Exchange.</span><span class="sxs-lookup"><span data-stu-id="8acc5-132">When the eDiscovery user is searching (or performing an action) for Exchange sources, such as a mailbox or archived Lync content, the central SSA uses Exchange Web Services (EWS) proxy to query Exchange Web Services.</span></span> <span data-ttu-id="8acc5-133">Exchange dispone di un'infrastruttura di ricerca e di eDiscovery e gestisce tutte le chiamate di eDiscovery internamente.</span><span class="sxs-lookup"><span data-stu-id="8acc5-133">Exchange has its own search and eDiscovery infrastructure and manages all eDiscovery calls internally.</span></span> 
    
13. <span data-ttu-id="8acc5-134">Servizi Web Exchange risponde a SSA con i risultati della ricerca di eDiscovery o una risposta a una richiesta di stato per un blocco basato su query, che, a sua sua, viene inoltrato all'EDC.</span><span class="sxs-lookup"><span data-stu-id="8acc5-134">Exchange Web Services responds to SSA with eDiscovery search results or a response to a status request for a query-based hold, which, in turn, gets relayed to the EDC.</span></span> 
    
#### <a name="prerequisites"></a><span data-ttu-id="8acc5-135">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="8acc5-135">Prerequisites</span></span>

- <span data-ttu-id="8acc5-136">La ricerca di SharePoint Enterprise deve essere configurata, le ricerche per indicizzazione nelle origini di contenuto (condivisioni di file di SharePoint e di Windows) sono state eseguite correttamente e tutte le origini di contenuto sono nell'indice.</span><span class="sxs-lookup"><span data-stu-id="8acc5-136">SharePoint Enterprise Search must be configured, search crawls on content sources (SharePoint and Windows file shares) are successfully occurring, and all content sources are in the index.</span></span> 
    
- <span data-ttu-id="8acc5-137">L'attendibilità da server a server e l'autenticazione devono essere configurate tra la farm di SharePoint Services e Exchange e anche tra Exchange e Lync.</span><span class="sxs-lookup"><span data-stu-id="8acc5-137">Server-to-server trust and authentication must be configured between the SharePoint Services Farm and Exchange and also between Exchange and Lync.</span></span> 
    
### <a name="description-of-components-in-the-diagram"></a><span data-ttu-id="8acc5-138">Descrizione dei componenti nel diagramma</span><span class="sxs-lookup"><span data-stu-id="8acc5-138">Description of components in the diagram</span></span>

<span data-ttu-id="8acc5-139">Nel diagramma viene visualizzato un utente che invia una query, che accede a due server farm, una farm di SharePoint 2013 Enterprise app e una farm di servizi di SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="8acc5-139">The diagram shows a user sending a query, which accesses two server farms, a SharePoint 2013 Enterprise App Farm and a SharePoint 2013 Services Farm.</span></span> <span data-ttu-id="8acc5-140">La farm di SharePoint Services si interfaccia con una farm di contenuto di SharePoint 2013, Exchange Server 2013 (che si interfaccia con Lync 2013) e condivisioni file di Windows.</span><span class="sxs-lookup"><span data-stu-id="8acc5-140">The SharePoint Services Farm interfaces with a SharePoint 2013 Content Farm, Exchange Server 2013 (which interfaces with Lync 2013), and Windows File Shares.</span></span> 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a><span data-ttu-id="8acc5-141">Farm delle app di SharePoint 2013 Enterprise</span><span class="sxs-lookup"><span data-stu-id="8acc5-141">SharePoint 2013 Enterprise App Farm</span></span>

<span data-ttu-id="8acc5-142">La farm delle app di SharePoint 2013 Enterprise contiene i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="8acc5-142">The SharePoint 2013 Enterprise App Farm contains the following components:</span></span> 
  
- <span data-ttu-id="8acc5-143">EDC</span><span class="sxs-lookup"><span data-stu-id="8acc5-143">EDC</span></span>
    
- <span data-ttu-id="8acc5-144">Proxy SSA</span><span class="sxs-lookup"><span data-stu-id="8acc5-144">SSA proxy</span></span> 
    
- <span data-ttu-id="8acc5-145">Processo timer</span><span class="sxs-lookup"><span data-stu-id="8acc5-145">Timer job</span></span> 
    
<span data-ttu-id="8acc5-146">Una query o un'azione inviata dall'utente viene inviata all'EDC nella farm dell'applicazione Enterprise.</span><span class="sxs-lookup"><span data-stu-id="8acc5-146">A query or action sent by the user is sent to the EDC in the Enterprise App Farm.</span></span> <span data-ttu-id="8acc5-147">Si verificano le seguenti azioni:</span><span class="sxs-lookup"><span data-stu-id="8acc5-147">The following actions occur:</span></span> 
  
- <span data-ttu-id="8acc5-148">La query o l'azione passa al proxy SSA.</span><span class="sxs-lookup"><span data-stu-id="8acc5-148">The query or action goes to the SSA proxy.</span></span> 
    
- <span data-ttu-id="8acc5-149">Il proxy SSA invia una query di stato o una risposta al processo timer nella farm di app Enterprise e invia anche una query di stato o una risposta al servizio SSA nella farm di SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="8acc5-149">The SSA proxy sends a status query or response to the Timer job in the Enterprise App Farm, and it also sends a status query or response to the SSA service in the SharePoint Services Farm.</span></span> <span data-ttu-id="8acc5-150">Le azioni che derivano da questa operazione sono descritte nella sezione relativa alla farm di SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="8acc5-150">The actions that result from this are described in the section about the SharePoint Services Farm.</span></span> 
    
- <span data-ttu-id="8acc5-151">Quando riceve una risposta, il processo timer Invia la risposta al proxy SSA e all'EDC.</span><span class="sxs-lookup"><span data-stu-id="8acc5-151">When it receives a response, the Timer job sends the response to the SSA proxy and to the EDC.</span></span> 
    
- <span data-ttu-id="8acc5-152">Tutti i risultati della query o dell'azione vengono inviati all'utente dall'EDC.</span><span class="sxs-lookup"><span data-stu-id="8acc5-152">Any results from the query or action are sent to the user from the EDC.</span></span> 
    
#### <a name="sharepoint-2013-services-farm"></a><span data-ttu-id="8acc5-153">Farm di SharePoint 2013 Services</span><span class="sxs-lookup"><span data-stu-id="8acc5-153">SharePoint 2013 Services Farm</span></span>

<span data-ttu-id="8acc5-154">La farm di SharePoint 2013 Services contiene i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="8acc5-154">The SharePoint 2013 Services Farm contains the following components:</span></span> 
  
- <span data-ttu-id="8acc5-155">Servizio SSA</span><span class="sxs-lookup"><span data-stu-id="8acc5-155">SSA Service</span></span> 
    
- <span data-ttu-id="8acc5-156">Database degli indici di ricerca</span><span class="sxs-lookup"><span data-stu-id="8acc5-156">Search index database</span></span> 
    
- <span data-ttu-id="8acc5-157">Database admin_db SSA.</span><span class="sxs-lookup"><span data-stu-id="8acc5-157">SSA admin_db database.</span></span> <span data-ttu-id="8acc5-158">La tabella Actions del database contiene: Hold Release Hold GetStatus</span><span class="sxs-lookup"><span data-stu-id="8acc5-158">The Actions Table in this database contains: Hold Release Hold GetStatus</span></span> 
    
- <span data-ttu-id="8acc5-159">Proxy EWS</span><span class="sxs-lookup"><span data-stu-id="8acc5-159">EWS proxy</span></span> 
    
<span data-ttu-id="8acc5-160">Quando il proxy SSA nella farm di app di SharePoint Enterprise invia una query di stato al SSA nella farm di SharePoint Services, si verificano le seguenti azioni:</span><span class="sxs-lookup"><span data-stu-id="8acc5-160">When the SSA proxy in the SharePoint Enterprise App Farm sends a status query to the SSA in the SharePoint Services Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="8acc5-161">Se la richiesta è una query, la SSA consulterà l'indice di ricerca.</span><span class="sxs-lookup"><span data-stu-id="8acc5-161">If the request is a query, the SSA consults the search index.</span></span> <span data-ttu-id="8acc5-162">La risposta di individuazione viene restituita al SSA e quindi all'utente tramite EDC.</span><span class="sxs-lookup"><span data-stu-id="8acc5-162">The discovery response is returned to the SSA and then to the user through the EDC.</span></span> 
    
- <span data-ttu-id="8acc5-163">Se la richiesta è un'azione di scrittura, il servizio SSA invierà l'azione di scrittura sul admin_db SSA.</span><span class="sxs-lookup"><span data-stu-id="8acc5-163">If the request is a write action, the SSA service sends the write action to the SSA admin_db.</span></span> 
    
- <span data-ttu-id="8acc5-164">Una richiesta di ricerca per indicizzazione e risposta viene inviata da SSA alla farm di contenuto di SharePoint 2013 e viene restituita una risposta al SSA.</span><span class="sxs-lookup"><span data-stu-id="8acc5-164">A crawl and responding results request is sent from the SSA to the SharePoint 2013 Content Farm and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="8acc5-165">Una richiesta di ricerca per indicizzazione e risposta viene inviata dal SSA alle condivisioni file di Windows e una risposta viene restituita al SSA.</span><span class="sxs-lookup"><span data-stu-id="8acc5-165">A crawl and responding results request is sent from the SSA to the Windows File Shares, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="8acc5-166">Una query per le azioni, le risposte o gli aggiornamenti di stato in sospeso viene inviata dal SSA al proxy SSA nella farm del contenuto di SharePoint e viene restituita una risposta al SSA.</span><span class="sxs-lookup"><span data-stu-id="8acc5-166">A query for pending action(s), responses, or status updates is sent from the SSA to the SSA proxy in the SharePoint Content Farm, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="8acc5-167">Una richiesta di azione/stato di Exchange viene inviata dal SSA al proxy EWS, che invia una richiesta di azione/stato di query di Exchange al servizio Web di Exchange sul server Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="8acc5-167">An Exchange action/status request is sent from the SSA to the EWS proxy, which sends an Exchange Query action/status request to the Exchange Web Service on the Exchange 2013 server.</span></span> 
    
- <span data-ttu-id="8acc5-168">Una query di stato/risposta viene inviata dal SSA al admin_db SSA e viene restituita al SSA.</span><span class="sxs-lookup"><span data-stu-id="8acc5-168">A status query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
- <span data-ttu-id="8acc5-169">Una query o una risposta di azione in sospeso viene inviata dal SSA alla admin_db SSA e viene restituita al SSA.</span><span class="sxs-lookup"><span data-stu-id="8acc5-169">A pending action query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
#### <a name="sharepoint-2013-content-farm"></a><span data-ttu-id="8acc5-170">Farm di contenuto di SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="8acc5-170">SharePoint 2013 Content Farm</span></span>

<span data-ttu-id="8acc5-171">La farm di contenuto di SharePoint 2013 contiene i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="8acc5-171">The SharePoint 2013 Content Farm contains the following components:</span></span> 
  
- <span data-ttu-id="8acc5-172">Proxy SSA</span><span class="sxs-lookup"><span data-stu-id="8acc5-172">SSA proxy</span></span> 
    
- <span data-ttu-id="8acc5-173">Processo timer</span><span class="sxs-lookup"><span data-stu-id="8acc5-173">Timer job</span></span> 
    
- <span data-ttu-id="8acc5-174">Sito di SharePoint di contoso</span><span class="sxs-lookup"><span data-stu-id="8acc5-174">Contoso SharePoint site</span></span> 
    
- <span data-ttu-id="8acc5-175">Contenuto di SharePoint di contoso</span><span class="sxs-lookup"><span data-stu-id="8acc5-175">Contoso SharePoint content</span></span> 
    
<span data-ttu-id="8acc5-176">Quando la farm di SharePoint Services viene inviata una query di stato al proxy SSA nella farm di contenuto di SharePoint, si verificano le seguenti azioni:</span><span class="sxs-lookup"><span data-stu-id="8acc5-176">When the SSA in the SharePoint Services Farm sends a status query to the SSA Proxy in the SharePoint Content Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="8acc5-177">Il proxy SSA nella farm del contenuto di SharePoint invia una query per le azioni in sospeso/la risposta dello stato al processo timer.</span><span class="sxs-lookup"><span data-stu-id="8acc5-177">The SSA proxy in the SharePoint Content Farm sends a query for pending actions/status response to the Timer job.</span></span> 
    
- <span data-ttu-id="8acc5-178">Il processo timer invia una richiesta al sito di SharePoint contoso, che esamina il contenuto di SharePoint contoso.</span><span class="sxs-lookup"><span data-stu-id="8acc5-178">The Timer job sends a request to the Contoso SharePoint site, which reviews the Contoso SharePoint content.</span></span> 
    
- <span data-ttu-id="8acc5-179">La risposta alla query relativa alle azioni o allo stato in sospeso viene inviata dal processo timer al proxy SSA nella farm del contenuto di SharePoint e quindi viene inviata al servizio SSA nella farm di SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="8acc5-179">The response to the pending actions/status query is sent from the Timer job to the SSA proxy in the SharePoint Content Farm, and then it is sent to the SSA service in the SharePoint Services Farm</span></span> 
    
#### <a name="exchange-2013"></a><span data-ttu-id="8acc5-180">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="8acc5-180">Exchange 2013</span></span>

<span data-ttu-id="8acc5-181">Il componente server di Exchange 2013 contiene il servizio Web di Exchange e fornisce quanto segue:</span><span class="sxs-lookup"><span data-stu-id="8acc5-181">The Exchange 2013 server component contains the Exchange Web Service and provides the following:</span></span> 
  
- <span data-ttu-id="8acc5-182">La relazione di trust tra server/OAuth viene gestita tra la farm di contenuto di SharePoint 2013 e Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="8acc5-182">Server-to-server Trust/OAuth is handled between the SharePoint 2013 Content Farm and Exchange 2013.</span></span> 
    
- <span data-ttu-id="8acc5-183">La relazione di trust tra server/OAuth viene gestita tra Exchange 2013 e Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="8acc5-183">Server-to-server Trust/OAuth is handled between Exchange 2013 and Lync 2013.</span></span> 
    
#### <a name="lync-2013"></a><span data-ttu-id="8acc5-184">Lync 2013</span><span class="sxs-lookup"><span data-stu-id="8acc5-184">Lync 2013</span></span>

<span data-ttu-id="8acc5-185">Il componente Lync 2013 archivia il contenuto di Lync in Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="8acc5-185">The Lync 2013 component archives Lync content in Exchange 2013.</span></span> 
  
#### <a name="windows-file-shares"></a><span data-ttu-id="8acc5-186">Condivisioni file di Windows</span><span class="sxs-lookup"><span data-stu-id="8acc5-186">Windows File Shares</span></span>

<span data-ttu-id="8acc5-187">Il componente Condivisione file di Windows fornisce i risultati della ricerca per indicizzazione all'SSA nella farm di SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="8acc5-187">The Windows File Shares component provides crawl results to the SSA in the SharePoint Services Farm.</span></span> 
  
### <a name="legend"></a><span data-ttu-id="8acc5-188">Legenda</span><span class="sxs-lookup"><span data-stu-id="8acc5-188">Legend</span></span>

<span data-ttu-id="8acc5-189">La legenda per questo diagramma Visualizza graficamente i diversi tipi di traffico rappresentati tra i componenti in linee colorate diverse, come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="8acc5-189">The legend for this diagram graphically shows the different types of traffic depicted among the components in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="8acc5-190">Riga blu chiaro: query/azione-eDiscovery di query o dati di azione</span><span class="sxs-lookup"><span data-stu-id="8acc5-190">Light blue line: Query/action - eDiscovery query or action data</span></span> 
    
- <span data-ttu-id="8acc5-191">Linea arancione: eDisovery Response-eDiscovery query Response data</span><span class="sxs-lookup"><span data-stu-id="8acc5-191">Orange line: eDisovery response - eDiscovery query response data</span></span> 
    
- <span data-ttu-id="8acc5-192">Linea verde: Status query/Response-eDiscovery Status query/dati di risposta</span><span class="sxs-lookup"><span data-stu-id="8acc5-192">Green line: Status query/response - eDiscovery status query/response data</span></span> 
    
- <span data-ttu-id="8acc5-193">Linea viola: Exchange Action/Status Request-eDiscovery Request for Action Status per il traffico di Exchange.</span><span class="sxs-lookup"><span data-stu-id="8acc5-193">Purple line: Exchange action/status request - eDiscovery request for action status for Exchange traffic.</span></span> 
    
- <span data-ttu-id="8acc5-194">Linea rossa: Exchange Data/status Response-eDiscovery query o la risposta dello stato da Exchange.</span><span class="sxs-lookup"><span data-stu-id="8acc5-194">Red line: Exchange data/status response - eDiscovery query or status response from Exchange.</span></span> 
    
- <span data-ttu-id="8acc5-195">Riga nera punteggiata: attendibilità da server a server/OAuth</span><span class="sxs-lookup"><span data-stu-id="8acc5-195">Dotted black line: Server-to-Server Trust/Oauth</span></span> 
    
- <span data-ttu-id="8acc5-196">Linea nera massiccia: ricerca per indicizzazione/risultati</span><span class="sxs-lookup"><span data-stu-id="8acc5-196">Solid black line: Crawl/results</span></span> 
    

