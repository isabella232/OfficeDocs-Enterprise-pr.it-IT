---
title: Diagramma accessibile - ripristino di emergenza di SharePoint in Microsoft Azure
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
description: "In questo articolo è una versione testo accessibile del diagramma denominata SharePoint il ripristino di emergenza in Microsoft Azure."
ms.openlocfilehash: 545aaae05e3becbde60fe01c0e50e5610ee69f98
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a><span data-ttu-id="2e514-103">Diagramma accessibile - ripristino di emergenza di SharePoint in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="2e514-103">Accessible diagram - SharePoint Disaster Recovery to Microsoft Azure</span></span>

<span data-ttu-id="2e514-104">**Riepilogo:** In questo articolo è una versione testo accessibile del diagramma denominata SharePoint il ripristino di emergenza in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="2e514-104">**Summary:** This article is an accessible text version of the diagram named SharePoint Disaster Recovery to Microsoft Azure.</span></span>
  
<span data-ttu-id="2e514-105">Questo poster vengono forniti esempi di architetture per la creazione di un ambiente di ripristino di Azure.</span><span class="sxs-lookup"><span data-stu-id="2e514-105">This poster provides examples of architectures for building a recovery environment in Azure.</span></span> 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a><span data-ttu-id="2e514-106">Ambiente locale con un ambiente di ripristino di Azure</span><span class="sxs-lookup"><span data-stu-id="2e514-106">On-premises environment with an Azure recovery environment</span></span>

<span data-ttu-id="2e514-107">Il diagramma mostra un esempio di architettura, utilizzata per l'ambiente di produzione di un ambiente locale che utilizza Azure per il ripristino.</span><span class="sxs-lookup"><span data-stu-id="2e514-107">The diagram shows an example of architecture used for the production environment of an on-premises environment that uses Azure for recovery.</span></span> 
  
### <a name="on-premises-production-environment"></a><span data-ttu-id="2e514-108">Ambiente di produzione in locale</span><span class="sxs-lookup"><span data-stu-id="2e514-108">On-premises production environment</span></span>

<span data-ttu-id="2e514-109">Nella figura relativa viene illustrato un ambiente di produzione con quattro livelli di server in una server farm.</span><span class="sxs-lookup"><span data-stu-id="2e514-109">The accompanying diagram shows a live production environment with four tiers of servers in a server farm.</span></span> 
  
#### <a name="tier-1"></a><span data-ttu-id="2e514-110">Livello 1</span><span class="sxs-lookup"><span data-stu-id="2e514-110">Tier 1</span></span>

<span data-ttu-id="2e514-p101">Esistono due server per i servizi front-end e di elaborazione delle query. Esiste una partizione di indice che fornisce una replica di entrambi i server.</span><span class="sxs-lookup"><span data-stu-id="2e514-p101">There are two servers for front-end services and query processing. There is an index partition that provides a replica of both servers.</span></span> 
  
#### <a name="tier-2"></a><span data-ttu-id="2e514-113">Livello 2</span><span class="sxs-lookup"><span data-stu-id="2e514-113">Tier 2</span></span>

<span data-ttu-id="2e514-114">Esistono due server per la cache distribuita in questo livello.</span><span class="sxs-lookup"><span data-stu-id="2e514-114">There are two servers for distributed cache in this tier.</span></span> 
  
#### <a name="tier-3"></a><span data-ttu-id="2e514-115">Livello 3</span><span class="sxs-lookup"><span data-stu-id="2e514-115">Tier 3</span></span>

<span data-ttu-id="2e514-p102">Esistono tre server in questo livello. Ogni server fornisce i servizi seguenti:</span><span class="sxs-lookup"><span data-stu-id="2e514-p102">There are three servers in this tier. Each server provides the following services:</span></span> 
  
- <span data-ttu-id="2e514-118">Servizi back-end</span><span class="sxs-lookup"><span data-stu-id="2e514-118">Backend services</span></span> 
    
- <span data-ttu-id="2e514-119">Admin</span><span class="sxs-lookup"><span data-stu-id="2e514-119">Admin</span></span> 
    
- <span data-ttu-id="2e514-120">Gestione flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="2e514-120">Workflow manager</span></span> 
    
- <span data-ttu-id="2e514-121">Ricerca per indicizzazione</span><span class="sxs-lookup"><span data-stu-id="2e514-121">Crawl</span></span> 
    
- <span data-ttu-id="2e514-122">Elaborazione del contenuto</span><span class="sxs-lookup"><span data-stu-id="2e514-122">Content processing</span></span> 
    
- <span data-ttu-id="2e514-123">Analisi</span><span class="sxs-lookup"><span data-stu-id="2e514-123">Analytics</span></span> 
    
#### <a name="tier-4"></a><span data-ttu-id="2e514-124">Livello 4</span><span class="sxs-lookup"><span data-stu-id="2e514-124">Tier 4</span></span>

<span data-ttu-id="2e514-p103">In questo livello sono disponibili due server. Entrambi i server presenti tre gruppi di disponibilità, come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="2e514-p103">There are two servers in this tier. Both servers have three availability groups, as follows:</span></span> 
  
- <span data-ttu-id="2e514-127">Gruppo di disponibilità #1 fornisce funzionalità di ricerca.</span><span class="sxs-lookup"><span data-stu-id="2e514-127">Availability group #1 provides search capabilities.</span></span> 
    
- <span data-ttu-id="2e514-128">Gruppo di disponibilità #2 fornisce contenuto, la configurazione e le applicazioni di servizio.</span><span class="sxs-lookup"><span data-stu-id="2e514-128">Availability group #2 provides content, configuration, and service applications.</span></span> 
    
- <span data-ttu-id="2e514-129">Gruppo di disponibilità #3 fornisce contenuto.</span><span class="sxs-lookup"><span data-stu-id="2e514-129">Availability group #3 provides content.</span></span> 
    
<span data-ttu-id="2e514-p104">È inoltre disponibile un file server in questo livello di condivisione. I server di livello 4 utilizzano la distribuzione dei log per comunicare con tale server. Il server, a sua volta, comunica su Distributed File System replica (che il servizio) a un server di condivisione di file nell'ambiente di Azure ripristino con warm standby, come descritto nella sezione seguente.</span><span class="sxs-lookup"><span data-stu-id="2e514-p104">There is also a file sharing server in this tier. The tier 4 servers use log shipping to communicate with this server. This server, in turn, communicates over Distributed File System Replication (DFSR) to a file share server in the Azure warm standby recovery environment, as described in the following section.</span></span> 
  
### <a name="azure-recovery-environment"></a><span data-ttu-id="2e514-133">Ambiente di ripristino di Azure</span><span class="sxs-lookup"><span data-stu-id="2e514-133">Azure recovery environment</span></span>

#### <a name="warm-standby-environment-running-virtual-machines"></a><span data-ttu-id="2e514-134">Con warm standby ambiente macchine virtuali in esecuzione</span><span class="sxs-lookup"><span data-stu-id="2e514-134">Warm standby environment running virtual machines</span></span>

<span data-ttu-id="2e514-p105">La relativa diagramma dell'ambiente locale replicato esattamente nell'ambiente di ripristino Azure. Il server di condivisione di file in questo ambiente è collegato l'ambiente locale e che il servizio. Che il servizio trasferisce registri dall'ambiente di produzione per l'ambiente di ripristino tramite il server di condivisione di file.</span><span class="sxs-lookup"><span data-stu-id="2e514-p105">The accompanying diagram shows the on-premises environment replicated exactly in the Azure recovery environment. The file share server in this environment is linked to the on-premises environment through DFSR. DFSR transfers logs from the production environment to the recovery environment through the file share server.</span></span> 
  
### <a name="overview"></a><span data-ttu-id="2e514-138">Panoramica</span><span class="sxs-lookup"><span data-stu-id="2e514-138">Overview</span></span>

<span data-ttu-id="2e514-139">L'ambiente di ripristino di emergenza per una farm di SharePoint 2013 locali può essere ospitata in Azure.</span><span class="sxs-lookup"><span data-stu-id="2e514-139">The disaster recovery environment for an on-premises SharePoint 2013 farm can be hosted in Azure.</span></span> 
  
-  <span data-ttu-id="2e514-140">Servizi di infrastruttura Azure offre un centro dati secondario.</span><span class="sxs-lookup"><span data-stu-id="2e514-140">Azure Infrastructure Services provides a secondary datacenter.</span></span>
    
- <span data-ttu-id="2e514-141">Prestare solo per le risorse utilizzate.</span><span class="sxs-lookup"><span data-stu-id="2e514-141">Pay only for the resources you use.</span></span> 
    
- <span data-ttu-id="2e514-142">Farm di piccole dimensioni ripristino può essere scalata dopo una situazione di emergenza per soddisfare gli obiettivi di capacità e scalabilità.</span><span class="sxs-lookup"><span data-stu-id="2e514-142">Small recovery farms can be scaled out after a disaster to meet scale and capacity targets.</span></span> 
    
<span data-ttu-id="2e514-143">La farm di ripristino in Azure è configurata come in modo identico possibile nella farm di produzione in locale.</span><span class="sxs-lookup"><span data-stu-id="2e514-143">The recovery farm in Azure is configured as identically as possible to the production on-premises farm.</span></span> 
  
- <span data-ttu-id="2e514-144">Stessa rappresentazione dei ruoli del server.</span><span class="sxs-lookup"><span data-stu-id="2e514-144">Same representation of server roles.</span></span> 
    
- <span data-ttu-id="2e514-145">Stessa configurazione di personalizzazioni.</span><span class="sxs-lookup"><span data-stu-id="2e514-145">Same configuration of customizations.</span></span> 
    
- <span data-ttu-id="2e514-146">Stessa configurazione delle funzionalità di ricerca (possibile in una versione ridotta di farm di produzione).</span><span class="sxs-lookup"><span data-stu-id="2e514-146">Same configuration of search features (these can be on a smaller version of the production farm).</span></span> 
    
<span data-ttu-id="2e514-147">La distribuzione dei log e che il servizio vengono utilizzati per copiare i log delle transazioni e dei backup di database alla farm di Azure.</span><span class="sxs-lookup"><span data-stu-id="2e514-147">Log shipping and DFSR are used to copy database backups and transaction logs to the Azure farm.</span></span> 
  
- <span data-ttu-id="2e514-p106">Che il servizio viene utilizzato per trasferire i registri dall'ambiente di produzione per l'ambiente di ripristino. In uno scenario WAN, che il servizio è più efficiente log direttamente al server secondario in Azure.</span><span class="sxs-lookup"><span data-stu-id="2e514-p106">DFSR is used to transfer logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.</span></span> 
    
- <span data-ttu-id="2e514-150">I registri vengono riprodotti nei computer basato su Azure SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2e514-150">Logs are replayed to the Azure-based SQL Server computers.</span></span> 
    
- <span data-ttu-id="2e514-151">Database con log Shipping vengono collegati alla farm finché non viene eseguito un esercizio di ripristino.</span><span class="sxs-lookup"><span data-stu-id="2e514-151">Log-shipped databases are not attached to the farm until a recovery exercise is performed.</span></span> 
    
<span data-ttu-id="2e514-152">Procedure di failover:</span><span class="sxs-lookup"><span data-stu-id="2e514-152">Failover procedures:</span></span> 
  
1. <span data-ttu-id="2e514-153">Arrestare il log shipping</span><span class="sxs-lookup"><span data-stu-id="2e514-153">Stop log shipping.</span></span> 
    
2. <span data-ttu-id="2e514-154">Smettere di accettare il traffico alla farm primaria.</span><span class="sxs-lookup"><span data-stu-id="2e514-154">Stop accepting traffic to the primary farm.</span></span> 
    
3. <span data-ttu-id="2e514-155">Riprodurre i registri di transazioni finali.</span><span class="sxs-lookup"><span data-stu-id="2e514-155">Replay the final transaction logs.</span></span> 
    
4. <span data-ttu-id="2e514-156">Collegare i database di contenuto alla farm.</span><span class="sxs-lookup"><span data-stu-id="2e514-156">Attach the content databases to the farm.</span></span> 
    
5. <span data-ttu-id="2e514-157">Avviare una ricerca per indicizzazione completa.</span><span class="sxs-lookup"><span data-stu-id="2e514-157">Start a full crawl.</span></span> 
    
6. <span data-ttu-id="2e514-158">Ripristinare le applicazioni di servizio dai database di servizi replicati.</span><span class="sxs-lookup"><span data-stu-id="2e514-158">Restore service applications from the replicated services databases.</span></span> 
    
<span data-ttu-id="2e514-159">Obiettivi del recupero forniti da questa soluzione includono:</span><span class="sxs-lookup"><span data-stu-id="2e514-159">Recovery objectives provided by this solution include:</span></span> 
  
- <span data-ttu-id="2e514-160">Siti e contenuto</span><span class="sxs-lookup"><span data-stu-id="2e514-160">Sites and content</span></span> 
    
- <span data-ttu-id="2e514-161">Ricerca (nuovamente a ricerca per indicizzazione, nessuna cronologia ricerca)</span><span class="sxs-lookup"><span data-stu-id="2e514-161">Search (re-crawled, no search history)</span></span> 
    
- <span data-ttu-id="2e514-162">Servizi</span><span class="sxs-lookup"><span data-stu-id="2e514-162">Services</span></span>
    
<span data-ttu-id="2e514-163">Ulteriori elementi che possono essere risolti da Microsoft Consulting Services o un partner:</span><span class="sxs-lookup"><span data-stu-id="2e514-163">Additional items that can be addressed by Microsoft Consulting Services or a partner:</span></span> 
  
- <span data-ttu-id="2e514-164">Sincronizzazione di soluzioni farm personalizzate</span><span class="sxs-lookup"><span data-stu-id="2e514-164">Synchronizing custom farm solutions</span></span> 
    
- <span data-ttu-id="2e514-165">Connessioni a origini dati in locale (origine contenuti di integrazione applicativa dei dati (BDC) e ricerca)</span><span class="sxs-lookup"><span data-stu-id="2e514-165">Connections to data sources on premises (Business Data Connectivity (BDC) and search content sources)</span></span> 
    
- <span data-ttu-id="2e514-166">Scenari di ripristino di ricerca</span><span class="sxs-lookup"><span data-stu-id="2e514-166">Search restore scenarios</span></span> 
    
- <span data-ttu-id="2e514-167">Gli obiettivi di tempo di ripristino (RTO) e obiettivi del punto di ripristino (RPO)</span><span class="sxs-lookup"><span data-stu-id="2e514-167">Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO)</span></span> 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a><span data-ttu-id="2e514-168">Ambiente di standby fredda macchine virtuali in esecuzione</span><span class="sxs-lookup"><span data-stu-id="2e514-168">Cold standby environment running virtual machines</span></span>

<span data-ttu-id="2e514-169">Cold standby ambienti richiedono più tempo per avviare ma sono meno costosi.</span><span class="sxs-lookup"><span data-stu-id="2e514-169">Cold standby environments take longer to start but are less expensive.</span></span> 
  
- <span data-ttu-id="2e514-p107">Viene creata completamente la farm, ma le macchine virtuali vengono arrestate dopo la creazione della farm. Corrisposto solo i costi di elaborazione per le macchine virtuali sono in esecuzione, ma si applicano i costi di archiviazione e di rete trasferimento di dati.</span><span class="sxs-lookup"><span data-stu-id="2e514-p107">The farm is fully built, but the virtual machines are stopped after the farm is created. You pay only processing costs when the virtual machines are running, but storage and network data transfer costs apply.</span></span> 
    
- <span data-ttu-id="2e514-172">In caso di emergenza, tutte le macchine virtuali della farm vengono avviate e un'applicazione di patch.</span><span class="sxs-lookup"><span data-stu-id="2e514-172">In the event of a disaster, all the virtual machines in the farm are started and patched.</span></span> 
    
- <span data-ttu-id="2e514-173">Backup e i registri delle transazioni vengono applicati ai database della farm.</span><span class="sxs-lookup"><span data-stu-id="2e514-173">Backups and transaction logs are applied to the farm databases.</span></span> 
    
<span data-ttu-id="2e514-174">Nell'elenco seguente vengono descritte le procedure aggiuntive per con cold standby ambienti:</span><span class="sxs-lookup"><span data-stu-id="2e514-174">The following list describes additional procedures for cold standby environments:</span></span> 
  
- <span data-ttu-id="2e514-175">Attivare le macchine virtuali regolarmente di patch, aggiornare e verifica dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="2e514-175">Turn on virtual machines regularly to patch, update, and verify the environment.</span></span> 
    
- <span data-ttu-id="2e514-176">Eseguire le procedure per aggiornare DNS e gli indirizzi IP.</span><span class="sxs-lookup"><span data-stu-id="2e514-176">Run procedures to refresh DNS and IP addresses.</span></span> 
    
- <span data-ttu-id="2e514-177">Configurare SQL AlwaysOn dopo il failover.</span><span class="sxs-lookup"><span data-stu-id="2e514-177">Set up SQL AlwaysOn after a failover.</span></span> 
    
<span data-ttu-id="2e514-p108">Nella figura relativa viene illustrato un ambiente di ripristino replicato nelle macchine virtuali. Dopo il failover in un ambiente con cold standby, tutte le macchine virtuali siano state avviate e configurati i gruppi di disponibilità utilizzando i registri di riesecuzione per rendere disponibili i server di database.</span><span class="sxs-lookup"><span data-stu-id="2e514-p108">The accompanying diagram shows a replicated recovery environment on virtual machines. After failover to a cold standby environment, all virtual machines are started, and the availability groups are configured using replay logs to make the database servers available.</span></span> 
  
## <a name="sharepoint-recovery-environment-in-azure"></a><span data-ttu-id="2e514-180">Ambiente di ripristino di SharePoint in Azure</span><span class="sxs-lookup"><span data-stu-id="2e514-180">SharePoint recovery environment in Azure</span></span>

<span data-ttu-id="2e514-181">Progettare e creare l'ambiente di failover in Azure.</span><span class="sxs-lookup"><span data-stu-id="2e514-181">Design and build the failover environment in Azure.</span></span> 
  
- <span data-ttu-id="2e514-182">Creare una rete virtuale in Azure.</span><span class="sxs-lookup"><span data-stu-id="2e514-182">Create a virtual network in Azure.</span></span> 
    
- <span data-ttu-id="2e514-p109">Connettersi alla rete locale con la rete virtuale in Azure con una connessione VPN del sito per sito. La connessione utilizza un gateway dinamico in Azure.</span><span class="sxs-lookup"><span data-stu-id="2e514-p109">Connect the on-premises network with the virtual network in Azure with a site-to-site VPN connection. This connection uses a dynamic gateway in Azure.</span></span> 
    
- <span data-ttu-id="2e514-p110">Distribuire uno o più controller di dominio per la rete virtuale Azure e configurare questi per l'utilizzo con il dominio locale. I controller di dominio sono i server di catalogo.</span><span class="sxs-lookup"><span data-stu-id="2e514-p110">Deploy one or more domain controllers to the Azure virtual network, and configure these to work with your on-premises domain. These domain controllers are catalog servers.</span></span> 
    
- <span data-ttu-id="2e514-187">Adattare la farm di SharePoint per i set di disponibilità e servizi cloud.</span><span class="sxs-lookup"><span data-stu-id="2e514-187">Adapt the SharePoint farm for cloud services and availability sets.</span></span> 
    
- <span data-ttu-id="2e514-188">Distribuire la farm di SharePoint e un file server a condivisioni file host.</span><span class="sxs-lookup"><span data-stu-id="2e514-188">Deploy the SharePoint farm plus a file server to host file shares.</span></span> 
    
- <span data-ttu-id="2e514-189">Configurare la distribuzione dei log e che il servizio tra l'ambiente locale e l'ambiente di ripristino basato su Azure.</span><span class="sxs-lookup"><span data-stu-id="2e514-189">Set up log shipping and DFSR between the on-premises environment and the Azure-based recovery environment.</span></span> 
    
<span data-ttu-id="2e514-190">Figura relativa che mostra l'ambiente locale e la rete virtuale Azure con le caratteristiche seguenti:</span><span class="sxs-lookup"><span data-stu-id="2e514-190">The accompanying diagram shows the on-premises environment and the Azure virtual network with the following features:</span></span> 
  
### <a name="on-premises-environment"></a><span data-ttu-id="2e514-191">Ambiente locale</span><span class="sxs-lookup"><span data-stu-id="2e514-191">On-premises environment</span></span>

- <span data-ttu-id="2e514-192">Configurazione di Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="2e514-192">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="2e514-193">Server Active Directory</span><span class="sxs-lookup"><span data-stu-id="2e514-193">Active Directory server</span></span> 
    
<span data-ttu-id="2e514-194">Le interfacce di rete locale con la rete virtuale Azure tramite un gateway di rete privata virtuale (VPN).</span><span class="sxs-lookup"><span data-stu-id="2e514-194">The on-premises network interfaces with the Azure virtual network over a virtual private network (VPN) gateway.</span></span> 
  
### <a name="azure-virtual-network"></a><span data-ttu-id="2e514-195">Rete virtuale Azure</span><span class="sxs-lookup"><span data-stu-id="2e514-195">Azure virtual network</span></span>

<span data-ttu-id="2e514-196">Le interfacce di gateway VPN con una subnet di gateway VPN attiva.</span><span class="sxs-lookup"><span data-stu-id="2e514-196">The VPN gateway interfaces with an active VPN gateway subnet.</span></span> 
  
<span data-ttu-id="2e514-197">Esistono tre servizi cloud nella rete virtuale Azure:</span><span class="sxs-lookup"><span data-stu-id="2e514-197">There are three cloud services in the Azure virtual network:</span></span> 
  
- <span data-ttu-id="2e514-198">Il primo servizio cloud dispone di due Active Directory e dei server DNS con una disponibilità impostato.</span><span class="sxs-lookup"><span data-stu-id="2e514-198">The first cloud service has two Active Directory and DNS servers with an availability set.</span></span> 
    
- <span data-ttu-id="2e514-p111">Il servizio cloud secondo presenta tre gruppi di server: due distribuiti i server della cache con un gruppo di disponibilità. Due server front-end con un gruppo di disponibilità. Tre server back-end con un gruppo di disponibilità.</span><span class="sxs-lookup"><span data-stu-id="2e514-p111">The second cloud service has three sets of servers: Two distributed cache servers with an availability set. Two front-end servers with an availability set. Three backend servers with an availability set.</span></span>
    
- <span data-ttu-id="2e514-p112">Il terzo servizio cloud con tre server di database con un gruppo di disponibilità. Uno di questi server di database è una condivisione file per nodo log shipping e un terzo di una maggioranza dei nodi per SQL Server AlwaysOn.</span><span class="sxs-lookup"><span data-stu-id="2e514-p112">The third cloud service has three database servers with an availability set. One of these database servers is a file share for log shipping and a third node of a node majority for SQL Server AlwaysOn.</span></span> 
    
### <a name="build-the-ad-ds-hybrid-environment"></a><span data-ttu-id="2e514-204">Creare l'ambiente ibrido di servizi di dominio Active Directory</span><span class="sxs-lookup"><span data-stu-id="2e514-204">Build the AD DS hybrid environment</span></span>

<span data-ttu-id="2e514-205">La configurazione di AD DS per questa soluzione costituisce uno scenario di distribuzione ibrida, in cui è parzialmente distribuiti in locale di dominio Active Directory e parzialmente distribuiti nelle macchine virtuali Azure.</span><span class="sxs-lookup"><span data-stu-id="2e514-205">The configuration of AD DS for this solution constitutes a hybrid deployment scenario in which AD DS is partly deployed on-premises and partly deployed on Azure virtual machines.</span></span> 
  
<span data-ttu-id="2e514-206">Importante: Prima di distribuire Active Directory in Azure, leggere le linee guida per la distribuzione di Windows Server Active Directory in Microsoft macchine virtuali di Azure (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx).</span><span class="sxs-lookup"><span data-stu-id="2e514-206">Important — Before you deploy AD DS in Azure, read Guidelines for Deploying Windows Server Active Directory on Microsoft Azure Virtual Machines (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx).</span></span> 
  
<span data-ttu-id="2e514-207">Per indicazioni dettagliate sulla progettazione e distribuzione di ambienti Active Directory, vedere http://TechNet.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="2e514-207">For complete guidance on designing and deploying Active Directory environments, see http://TechNet.microsoft.com.</span></span> 
  
<span data-ttu-id="2e514-p113">Questa architettura di riferimento include due macchine virtuali configurate come controller di dominio. È stata configurata come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="2e514-p113">This reference architecture includes two virtual machines configured as domain controllers. Each is configured as follows:</span></span> 
  
- <span data-ttu-id="2e514-210">Dimensioni, ovvero piccola.</span><span class="sxs-lookup"><span data-stu-id="2e514-210">Size — Small.</span></span> 
    
- <span data-ttu-id="2e514-211">Sistema operativo: Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="2e514-211">Operating system — Windows Server 2012.</span></span> 
    
- <span data-ttu-id="2e514-p114">Ruolo, ovvero i controller di dominio Active Directory designato come server di catalogo globale. Questa configurazione consente di ridurre il traffico in uscita attraverso la connessione VPN. In un ambiente con più domini con modifiche molto frequenti, configurare domain controller locale non sincronizzare con il server di catalogo globale in Azure.</span><span class="sxs-lookup"><span data-stu-id="2e514-p114">Role — AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the VPN connection. In a multi-domain environment with high rates of change, configure domain controllers on-premises to not sync with the global catalog servers in Azure.</span></span> 
    
- <span data-ttu-id="2e514-p115">Dischi dati, posizionare il database di dominio Active Directory, log e SYSVOL su dischi dati Azure. Non collocare questi del disco di sistema operativo o i dischi temporanei forniti da Azure. Questo è importante.</span><span class="sxs-lookup"><span data-stu-id="2e514-p115">Data disks — Place the AD DS database, logs, and SYSVOL on Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure. This is important.</span></span> 
    
- <span data-ttu-id="2e514-218">Ruolo, Installare e configurare Windows DNS nei controller di dominio.</span><span class="sxs-lookup"><span data-stu-id="2e514-218">Role — Install and configure Windows DNS on the domain controllers.</span></span> 
    
- <span data-ttu-id="2e514-p116">Indirizzi IP, utilizzare gli indirizzi IP dinamici. È necessario creare una rete virtuale Azure.</span><span class="sxs-lookup"><span data-stu-id="2e514-p116">IP addresses — Use dynamic IP addresses. This requires you to create an Azure Virtual Network.</span></span> 
    

