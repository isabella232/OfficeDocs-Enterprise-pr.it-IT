---
title: Diagramma accessibile-ripristino di emergenza di SharePoint in Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: Questo articolo è una versione di testo accessibile del diagramma denominato ripristino di emergenza di SharePoint in Microsoft Azure.
ms.openlocfilehash: 545aaae05e3becbde60fe01c0e50e5610ee69f98
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487722"
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a><span data-ttu-id="3e2a2-103">Diagramma accessibile-ripristino di emergenza di SharePoint in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="3e2a2-103">Accessible diagram - SharePoint Disaster Recovery to Microsoft Azure</span></span>

<span data-ttu-id="3e2a2-104">**Riepilogo:** Questo articolo è una versione di testo accessibile del diagramma denominato ripristino di emergenza di SharePoint in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-104">**Summary:** This article is an accessible text version of the diagram named SharePoint Disaster Recovery to Microsoft Azure.</span></span>
  
<span data-ttu-id="3e2a2-105">Questo poster fornisce esempi di architetture per la creazione di un ambiente di ripristino in Azure.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-105">This poster provides examples of architectures for building a recovery environment in Azure.</span></span> 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a><span data-ttu-id="3e2a2-106">Ambiente locale con un ambiente di ripristino di Azure</span><span class="sxs-lookup"><span data-stu-id="3e2a2-106">On-premises environment with an Azure recovery environment</span></span>

<span data-ttu-id="3e2a2-107">Nel diagramma viene illustrato un esempio di architettura utilizzata per l'ambiente di produzione di un ambiente locale che utilizza Azure per il ripristino.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-107">The diagram shows an example of architecture used for the production environment of an on-premises environment that uses Azure for recovery.</span></span> 
  
### <a name="on-premises-production-environment"></a><span data-ttu-id="3e2a2-108">Ambiente di produzione locale</span><span class="sxs-lookup"><span data-stu-id="3e2a2-108">On-premises production environment</span></span>

<span data-ttu-id="3e2a2-109">Nel diagramma di accompagnamento viene mostrato un ambiente di produzione in tempo reale con quattro livelli di server in una server farm.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-109">The accompanying diagram shows a live production environment with four tiers of servers in a server farm.</span></span> 
  
#### <a name="tier-1"></a><span data-ttu-id="3e2a2-110">Livello 1</span><span class="sxs-lookup"><span data-stu-id="3e2a2-110">Tier 1</span></span>

<span data-ttu-id="3e2a2-111">Sono disponibili due server per i servizi front-end e per l'elaborazione delle query.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-111">There are two servers for front-end services and query processing.</span></span> <span data-ttu-id="3e2a2-112">È presente una partizione di indice che fornisce una replica di entrambi i server.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-112">There is an index partition that provides a replica of both servers.</span></span> 
  
#### <a name="tier-2"></a><span data-ttu-id="3e2a2-113">Livello 2</span><span class="sxs-lookup"><span data-stu-id="3e2a2-113">Tier 2</span></span>

<span data-ttu-id="3e2a2-114">In questo livello sono disponibili due server per la cache distribuita.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-114">There are two servers for distributed cache in this tier.</span></span> 
  
#### <a name="tier-3"></a><span data-ttu-id="3e2a2-115">Livello 3   </span><span class="sxs-lookup"><span data-stu-id="3e2a2-115">Tier 3</span></span>

<span data-ttu-id="3e2a2-116">Esistono tre server in questo livello.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-116">There are three servers in this tier.</span></span> <span data-ttu-id="3e2a2-117">Ogni server fornisce i servizi seguenti:</span><span class="sxs-lookup"><span data-stu-id="3e2a2-117">Each server provides the following services:</span></span> 
  
- <span data-ttu-id="3e2a2-118">Servizi back-end</span><span class="sxs-lookup"><span data-stu-id="3e2a2-118">Backend services</span></span> 
    
- <span data-ttu-id="3e2a2-119">Amministratore</span><span class="sxs-lookup"><span data-stu-id="3e2a2-119">Admin</span></span> 
    
- <span data-ttu-id="3e2a2-120">Gestione flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="3e2a2-120">Workflow manager</span></span> 
    
- <span data-ttu-id="3e2a2-121">Ricerca per indicizzazione</span><span class="sxs-lookup"><span data-stu-id="3e2a2-121">Crawl</span></span> 
    
- <span data-ttu-id="3e2a2-122">Elaborazione del contenuto</span><span class="sxs-lookup"><span data-stu-id="3e2a2-122">Content processing</span></span> 
    
- <span data-ttu-id="3e2a2-123">Analisi</span><span class="sxs-lookup"><span data-stu-id="3e2a2-123">Analytics</span></span> 
    
#### <a name="tier-4"></a><span data-ttu-id="3e2a2-124">Tier 4</span><span class="sxs-lookup"><span data-stu-id="3e2a2-124">Tier 4</span></span>

<span data-ttu-id="3e2a2-125">Esistono due server in questo livello.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-125">There are two servers in this tier.</span></span> <span data-ttu-id="3e2a2-126">In entrambi i server sono disponibili tre gruppi di disponibilità, come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="3e2a2-126">Both servers have three availability groups, as follows:</span></span> 
  
- <span data-ttu-id="3e2a2-127">Il gruppo di disponibilità #1 fornisce le funzionalità di ricerca.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-127">Availability group #1 provides search capabilities.</span></span> 
    
- <span data-ttu-id="3e2a2-128">Il gruppo di disponibilità #2 fornisce le applicazioni di contenuto, configurazione e di servizio.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-128">Availability group #2 provides content, configuration, and service applications.</span></span> 
    
- <span data-ttu-id="3e2a2-129">Il gruppo di disponibilità #3 fornisce contenuto.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-129">Availability group #3 provides content.</span></span> 
    
<span data-ttu-id="3e2a2-130">Esiste anche un server di condivisione file in questo livello.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-130">There is also a file sharing server in this tier.</span></span> <span data-ttu-id="3e2a2-131">I server Tier 4 utilizzano log shipping per comunicare con il server.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-131">The tier 4 servers use log shipping to communicate with this server.</span></span> <span data-ttu-id="3e2a2-132">Questo server, a sua incirca, comunica tramite la replica del file System distribuito (DFSR) a un server di condivisione file nell'ambiente di ripristino di emergenza con warm standby di Azure, come descritto nella sezione seguente.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-132">This server, in turn, communicates over Distributed File System Replication (DFSR) to a file share server in the Azure warm standby recovery environment, as described in the following section.</span></span> 
  
### <a name="azure-recovery-environment"></a><span data-ttu-id="3e2a2-133">Ambiente di ripristino di Azure</span><span class="sxs-lookup"><span data-stu-id="3e2a2-133">Azure recovery environment</span></span>

#### <a name="warm-standby-environment-running-virtual-machines"></a><span data-ttu-id="3e2a2-134">Ambiente caldo di standby in esecuzione macchine virtuali</span><span class="sxs-lookup"><span data-stu-id="3e2a2-134">Warm standby environment running virtual machines</span></span>

<span data-ttu-id="3e2a2-135">Nel diagramma di accompagnamento viene illustrato l'ambiente locale replicato esattamente nell'ambiente di ripristino di Azure.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-135">The accompanying diagram shows the on-premises environment replicated exactly in the Azure recovery environment.</span></span> <span data-ttu-id="3e2a2-136">Il server di condivisione file in questo ambiente è collegato all'ambiente locale tramite DFSR.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-136">The file share server in this environment is linked to the on-premises environment through DFSR.</span></span> <span data-ttu-id="3e2a2-137">DFSR trasferisce i registri dall'ambiente di produzione all'ambiente di ripristino tramite il server di condivisione file.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-137">DFSR transfers logs from the production environment to the recovery environment through the file share server.</span></span> 
  
### <a name="overview"></a><span data-ttu-id="3e2a2-138">Panoramica</span><span class="sxs-lookup"><span data-stu-id="3e2a2-138">Overview</span></span>

<span data-ttu-id="3e2a2-139">L'ambiente di ripristino di emergenza per una farm di SharePoint 2013 locale può essere ospitato in Azure.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-139">The disaster recovery environment for an on-premises SharePoint 2013 farm can be hosted in Azure.</span></span> 
  
-  <span data-ttu-id="3e2a2-140">Servizi di infrastruttura di Azure fornisce un datacenter secondario.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-140">Azure Infrastructure Services provides a secondary datacenter.</span></span>
    
- <span data-ttu-id="3e2a2-141">Paghi solo per le risorse che utilizzi.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-141">Pay only for the resources you use.</span></span> 
    
- <span data-ttu-id="3e2a2-142">È possibile eseguire la scalabilità delle farm di ripristino di piccole dimensioni dopo una catastrofe per raggiungere gli obiettivi di scalabilità e capacità.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-142">Small recovery farms can be scaled out after a disaster to meet scale and capacity targets.</span></span> 
    
<span data-ttu-id="3e2a2-143">La farm di ripristino in Azure è configurata nel modo più identico possibile alla farm di produzione locale.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-143">The recovery farm in Azure is configured as identically as possible to the production on-premises farm.</span></span> 
  
- <span data-ttu-id="3e2a2-144">Stessa rappresentazione dei ruoli del server.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-144">Same representation of server roles.</span></span> 
    
- <span data-ttu-id="3e2a2-145">Stessa configurazione delle personalizzazioni.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-145">Same configuration of customizations.</span></span> 
    
- <span data-ttu-id="3e2a2-146">Stessa configurazione delle funzionalità di ricerca (possono trovarsi in una versione ridotta della farm di produzione).</span><span class="sxs-lookup"><span data-stu-id="3e2a2-146">Same configuration of search features (these can be on a smaller version of the production farm).</span></span> 
    
<span data-ttu-id="3e2a2-147">I log shipping e DFSR vengono utilizzati per copiare i backup di database e i registri delle transazioni nella farm di Azure.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-147">Log shipping and DFSR are used to copy database backups and transaction logs to the Azure farm.</span></span> 
  
- <span data-ttu-id="3e2a2-148">DFSR viene utilizzato per trasferire i log dall'ambiente di produzione all'ambiente di ripristino.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-148">DFSR is used to transfer logs from the production environment to the recovery environment.</span></span> <span data-ttu-id="3e2a2-149">In uno scenario WAN, Replica DFS è più efficiente della spedizione diretta dei registri al server secondario in Azure.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-149">In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.</span></span> 
    
- <span data-ttu-id="3e2a2-150">I registri vengono riprodotti nei computer SQL Server basati su Azure.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-150">Logs are replayed to the Azure-based SQL Server computers.</span></span> 
    
- <span data-ttu-id="3e2a2-151">I database di log shipping non vengono associati alla farm fino a quando non viene eseguito un esercizio di ripristino.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-151">Log-shipped databases are not attached to the farm until a recovery exercise is performed.</span></span> 
    
<span data-ttu-id="3e2a2-152">Procedure di failover:</span><span class="sxs-lookup"><span data-stu-id="3e2a2-152">Failover procedures:</span></span> 
  
1. <span data-ttu-id="3e2a2-153">Arrestare il log shipping</span><span class="sxs-lookup"><span data-stu-id="3e2a2-153">Stop log shipping.</span></span> 
    
2. <span data-ttu-id="3e2a2-154">Smettere di accettare il traffico alla farm primaria.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-154">Stop accepting traffic to the primary farm.</span></span> 
    
3. <span data-ttu-id="3e2a2-155">Riprodurre i registri di transazioni finali.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-155">Replay the final transaction logs.</span></span> 
    
4. <span data-ttu-id="3e2a2-156">Collegare i database di contenuto alla farm.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-156">Attach the content databases to the farm.</span></span> 
    
5. <span data-ttu-id="3e2a2-157">Avviare una ricerca per indicizzazione completa.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-157">Start a full crawl.</span></span> 
    
6. <span data-ttu-id="3e2a2-158">Ripristinare le applicazioni di servizio dai database di servizi replicati.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-158">Restore service applications from the replicated services databases.</span></span> 
    
<span data-ttu-id="3e2a2-159">Gli obiettivi di ripristino forniti da questa soluzione includono:</span><span class="sxs-lookup"><span data-stu-id="3e2a2-159">Recovery objectives provided by this solution include:</span></span> 
  
- <span data-ttu-id="3e2a2-160">Siti e contenuto</span><span class="sxs-lookup"><span data-stu-id="3e2a2-160">Sites and content</span></span> 
    
- <span data-ttu-id="3e2a2-161">Ricerca (sottoposto a ricerca per indicizzazione, nessuna cronologia ricerche)</span><span class="sxs-lookup"><span data-stu-id="3e2a2-161">Search (re-crawled, no search history)</span></span> 
    
- <span data-ttu-id="3e2a2-162">Servizi</span><span class="sxs-lookup"><span data-stu-id="3e2a2-162">Services</span></span>
    
<span data-ttu-id="3e2a2-163">Elementi aggiuntivi che possono essere indirizzati da Microsoft Consulting Services o da un partner:</span><span class="sxs-lookup"><span data-stu-id="3e2a2-163">Additional items that can be addressed by Microsoft Consulting Services or a partner:</span></span> 
  
- <span data-ttu-id="3e2a2-164">Sincronizzazione di soluzioni farm personalizzate</span><span class="sxs-lookup"><span data-stu-id="3e2a2-164">Synchronizing custom farm solutions</span></span> 
    
- <span data-ttu-id="3e2a2-165">Connessioni a origini dati in locale (integrazione applicativa dei dati (BDC) e fonti di contenuto di ricerca)</span><span class="sxs-lookup"><span data-stu-id="3e2a2-165">Connections to data sources on premises (Business Data Connectivity (BDC) and search content sources)</span></span> 
    
- <span data-ttu-id="3e2a2-166">Scenari di ripristino di ricerca</span><span class="sxs-lookup"><span data-stu-id="3e2a2-166">Search restore scenarios</span></span> 
    
- <span data-ttu-id="3e2a2-167">Obiettivi per il tempo di ripristino (RTO) e gli obiettivi del punto di ripristino (RPO)</span><span class="sxs-lookup"><span data-stu-id="3e2a2-167">Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO)</span></span> 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a><span data-ttu-id="3e2a2-168">Ambiente di standby freddo in esecuzione macchine virtuali</span><span class="sxs-lookup"><span data-stu-id="3e2a2-168">Cold standby environment running virtual machines</span></span>

<span data-ttu-id="3e2a2-169">Gli ambienti Cold standby richiedono più tempo per iniziare ma sono meno costosi.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-169">Cold standby environments take longer to start but are less expensive.</span></span> 
  
- <span data-ttu-id="3e2a2-170">La farm è completamente compilata, ma le macchine virtuali vengono arrestate dopo la creazione della farm.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-170">The farm is fully built, but the virtual machines are stopped after the farm is created.</span></span> <span data-ttu-id="3e2a2-171">Si pagano solo i costi di elaborazione quando le macchine virtuali sono in esecuzione, ma vengono applicati i costi di archiviazione e trasferimento dei dati di rete.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-171">You pay only processing costs when the virtual machines are running, but storage and network data transfer costs apply.</span></span> 
    
- <span data-ttu-id="3e2a2-172">In caso di emergenza, tutte le macchine virtuali della farm vengono avviate e patchate.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-172">In the event of a disaster, all the virtual machines in the farm are started and patched.</span></span> 
    
- <span data-ttu-id="3e2a2-173">I backup e i registri delle transazioni vengono applicati ai database della farm.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-173">Backups and transaction logs are applied to the farm databases.</span></span> 
    
<span data-ttu-id="3e2a2-174">Nell'elenco seguente vengono descritte le procedure aggiuntive per gli ambienti Cold standby:</span><span class="sxs-lookup"><span data-stu-id="3e2a2-174">The following list describes additional procedures for cold standby environments:</span></span> 
  
- <span data-ttu-id="3e2a2-175">Abilitare regolarmente le macchine virtuali per la patch, l'aggiornamento e la verifica dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-175">Turn on virtual machines regularly to patch, update, and verify the environment.</span></span> 
    
- <span data-ttu-id="3e2a2-176">Eseguire le procedure per aggiornare DNS e gli indirizzi IP.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-176">Run procedures to refresh DNS and IP addresses.</span></span> 
    
- <span data-ttu-id="3e2a2-177">Configurare SQL AlwaysOn dopo un failover.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-177">Set up SQL AlwaysOn after a failover.</span></span> 
    
<span data-ttu-id="3e2a2-178">Il diagramma di accompagnamento Visualizza un ambiente di ripristino replicato nelle macchine virtuali.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-178">The accompanying diagram shows a replicated recovery environment on virtual machines.</span></span> <span data-ttu-id="3e2a2-179">Dopo il failover in un ambiente di standby freddo, vengono avviate tutte le macchine virtuali e i gruppi di disponibilità vengono configurati utilizzando i registri di riesecuzione per rendere disponibili i server di database.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-179">After failover to a cold standby environment, all virtual machines are started, and the availability groups are configured using replay logs to make the database servers available.</span></span> 
  
## <a name="sharepoint-recovery-environment-in-azure"></a><span data-ttu-id="3e2a2-180">Ambiente di ripristino di SharePoint in Azure</span><span class="sxs-lookup"><span data-stu-id="3e2a2-180">SharePoint recovery environment in Azure</span></span>

<span data-ttu-id="3e2a2-181">Progettare e creare l'ambiente di failover in Azure.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-181">Design and build the failover environment in Azure.</span></span> 
  
- <span data-ttu-id="3e2a2-182">Creare una rete virtuale in Azure.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-182">Create a virtual network in Azure.</span></span> 
    
- <span data-ttu-id="3e2a2-183">Connettere la rete locale alla rete virtuale in Azure con una connessione VPN da sito a sito.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-183">Connect the on-premises network with the virtual network in Azure with a site-to-site VPN connection.</span></span> <span data-ttu-id="3e2a2-184">Questa connessione utilizza un gateway dinamico in Azure.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-184">This connection uses a dynamic gateway in Azure.</span></span> 
    
- <span data-ttu-id="3e2a2-185">Distribuire uno o più controller di dominio nella rete virtuale di Azure e configurarli in modo che funzionino con il dominio locale.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-185">Deploy one or more domain controllers to the Azure virtual network, and configure these to work with your on-premises domain.</span></span> <span data-ttu-id="3e2a2-186">Questi controller di dominio sono server di catalogo.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-186">These domain controllers are catalog servers.</span></span> 
    
- <span data-ttu-id="3e2a2-187">Adattare la farm di SharePoint per i set di disponibilità e servizi cloud.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-187">Adapt the SharePoint farm for cloud services and availability sets.</span></span> 
    
- <span data-ttu-id="3e2a2-188">Distribuire la farm di SharePoint e un file server per ospitare le condivisioni di file.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-188">Deploy the SharePoint farm plus a file server to host file shares.</span></span> 
    
- <span data-ttu-id="3e2a2-189">Configurare il log shipping e DFSR tra l'ambiente locale e l'ambiente di ripristino basato su Azure.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-189">Set up log shipping and DFSR between the on-premises environment and the Azure-based recovery environment.</span></span> 
    
<span data-ttu-id="3e2a2-190">Nel diagramma di accompagnamento viene illustrato l'ambiente locale e la rete virtuale di Azure con le caratteristiche seguenti:</span><span class="sxs-lookup"><span data-stu-id="3e2a2-190">The accompanying diagram shows the on-premises environment and the Azure virtual network with the following features:</span></span> 
  
### <a name="on-premises-environment"></a><span data-ttu-id="3e2a2-191">Ambiente locale</span><span class="sxs-lookup"><span data-stu-id="3e2a2-191">On-premises environment</span></span>

- <span data-ttu-id="3e2a2-192">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="3e2a2-192">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="3e2a2-193">Server Active Directory</span><span class="sxs-lookup"><span data-stu-id="3e2a2-193">Active Directory server</span></span> 
    
<span data-ttu-id="3e2a2-194">Le interfacce di rete locali con la rete virtuale di Azure su un gateway VPN (Virtual Private Network).</span><span class="sxs-lookup"><span data-stu-id="3e2a2-194">The on-premises network interfaces with the Azure virtual network over a virtual private network (VPN) gateway.</span></span> 
  
### <a name="azure-virtual-network"></a><span data-ttu-id="3e2a2-195">Rete virtuale di Azure</span><span class="sxs-lookup"><span data-stu-id="3e2a2-195">Azure virtual network</span></span>

<span data-ttu-id="3e2a2-196">Il gateway VPN si interfaccia con una subnet del gateway VPN attiva.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-196">The VPN gateway interfaces with an active VPN gateway subnet.</span></span> 
  
<span data-ttu-id="3e2a2-197">Nella rete virtuale di Azure sono disponibili tre servizi cloud:</span><span class="sxs-lookup"><span data-stu-id="3e2a2-197">There are three cloud services in the Azure virtual network:</span></span> 
  
- <span data-ttu-id="3e2a2-198">Il primo servizio cloud dispone di due server Active Directory e DNS con un set di disponibilità.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-198">The first cloud service has two Active Directory and DNS servers with an availability set.</span></span> 
    
- <span data-ttu-id="3e2a2-199">Nel secondo servizio cloud sono disponibili tre gruppi di server: due server di cache distribuita con un set di disponibilità.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-199">The second cloud service has three sets of servers: Two distributed cache servers with an availability set.</span></span> <span data-ttu-id="3e2a2-200">Due server front-end con un set di disponibilità.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-200">Two front-end servers with an availability set.</span></span> <span data-ttu-id="3e2a2-201">Tre server back-end con un set di disponibilità.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-201">Three backend servers with an availability set.</span></span>
    
- <span data-ttu-id="3e2a2-202">Il terzo servizio cloud dispone di tre server di database con un set di disponibilità.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-202">The third cloud service has three database servers with an availability set.</span></span> <span data-ttu-id="3e2a2-203">Uno di questi server di database è una condivisione file per il log shipping e un terzo nodo di una maggioranza dei nodi per SQL Server AlwaysOn.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-203">One of these database servers is a file share for log shipping and a third node of a node majority for SQL Server AlwaysOn.</span></span> 
    
### <a name="build-the-ad-ds-hybrid-environment"></a><span data-ttu-id="3e2a2-204">Creare l'ambiente ibrido di servizi di dominio Active Directory</span><span class="sxs-lookup"><span data-stu-id="3e2a2-204">Build the AD DS hybrid environment</span></span>

<span data-ttu-id="3e2a2-205">La configurazione di servizi di dominio Active Directory per questa soluzione costituisce uno scenario di distribuzione ibrida in cui AD DS è in parte distribuito in locale e in parte distribuito in macchine virtuali di Azure.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-205">The configuration of AD DS for this solution constitutes a hybrid deployment scenario in which AD DS is partly deployed on-premises and partly deployed on Azure virtual machines.</span></span> 
  
<span data-ttu-id="3e2a2-206">Importante: prima di distribuire servizi di dominio Active Directory in Azure, vedere linee guida per la distribuzione di Windows Server attivo nellehttp://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx)macchine virtuali di Microsoft Azure (.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-206">Important — Before you deploy AD DS in Azure, read Guidelines for Deploying Windows Server Active Directory on Microsoft Azure Virtual Machines (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx).</span></span> 
  
<span data-ttu-id="3e2a2-207">Per istruzioni complete sulla progettazione e la distribuzione di ambienti Active Directory http://TechNet.microsoft.com, vedere.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-207">For complete guidance on designing and deploying Active Directory environments, see http://TechNet.microsoft.com.</span></span> 
  
<span data-ttu-id="3e2a2-208">Questa architettura di riferimento include due macchine virtuali configurate come controller di dominio.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-208">This reference architecture includes two virtual machines configured as domain controllers.</span></span> <span data-ttu-id="3e2a2-209">Ognuna è configurata come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="3e2a2-209">Each is configured as follows:</span></span> 
  
- <span data-ttu-id="3e2a2-210">Dimensioni: piccolo.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-210">Size — Small.</span></span> 
    
- <span data-ttu-id="3e2a2-211">Sistema operativo-Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-211">Operating system — Windows Server 2012.</span></span> 
    
- <span data-ttu-id="3e2a2-212">Role-controller di dominio AD DS designato come server di catalogo globale.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-212">Role — AD DS domain controller designated as a global catalog server.</span></span> <span data-ttu-id="3e2a2-213">Questa configurazione riduce il traffico in uscita attraverso la connessione VPN.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-213">This configuration reduces egress traffic across the VPN connection.</span></span> <span data-ttu-id="3e2a2-214">In un ambiente con più domini con alti tassi di modifica, configurare i controller di dominio locali in modo che non vengano sincronizzati con i server di catalogo globale in Azure.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-214">In a multi-domain environment with high rates of change, configure domain controllers on-premises to not sync with the global catalog servers in Azure.</span></span> 
    
- <span data-ttu-id="3e2a2-215">Dischi di dati: posizionare il database di servizi di dominio Active Directory, i registri e SYSVOL nei dischi di dati di Azure.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-215">Data disks — Place the AD DS database, logs, and SYSVOL on Azure data disks.</span></span> <span data-ttu-id="3e2a2-216">Non posizionarli sul disco del sistema operativo o sui dischi temporanei forniti da Azure.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-216">Do not place these on the operating system disk or the temporary disks provided by Azure.</span></span> <span data-ttu-id="3e2a2-217">Questo è importante.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-217">This is important.</span></span> 
    
- <span data-ttu-id="3e2a2-218">Ruolo: installazione e configurazione di Windows DNS sui controller di dominio.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-218">Role — Install and configure Windows DNS on the domain controllers.</span></span> 
    
- <span data-ttu-id="3e2a2-219">Indirizzi IP: utilizzare indirizzi IP dinamici.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-219">IP addresses — Use dynamic IP addresses.</span></span> <span data-ttu-id="3e2a2-220">In questo modo è necessario creare una rete virtuale di Azure.</span><span class="sxs-lookup"><span data-stu-id="3e2a2-220">This requires you to create an Azure Virtual Network.</span></span> 
    

