---
title: Scenari cloud ibridi per IaaS di Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: "Riepilogo: informazioni sull'architettura ibrida e sugli scenari per le offerte cloud di Microsoft Infrastructure as a Service (IaaS) in Azure."
ms.openlocfilehash: d3f4b4ccbc9dbfa54e6f1d0988624aeb71f27106
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741362"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a><span data-ttu-id="d5d18-103">Scenari cloud ibridi per Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="d5d18-103">Hybrid cloud scenarios for Azure IaaS</span></span>

 <span data-ttu-id="d5d18-104">**Riepilogo:** Comprendere l'architettura ibrida e gli scenari per le offerte cloud basate su servizi infrastruttura di Microsoft come servizio (IaaS) in Azure.</span><span class="sxs-lookup"><span data-stu-id="d5d18-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Infrastructure as a Service (IaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="d5d18-105">Estendere l'infrastruttura di gestione delle identità e di calcolo locale nel cloud ospitando i carichi di lavoro IT in esecuzione su reti virtuali Azure cross-premise. </span><span class="sxs-lookup"><span data-stu-id="d5d18-105">Extend your on-premises computing and identity infrastructure into the cloud by hosting IT workloads running in cross-premises Azure virtual networks (VNets).</span></span> 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a><span data-ttu-id="d5d18-106">Architettura per scenario ibrido in IaaS di Azure</span><span class="sxs-lookup"><span data-stu-id="d5d18-106">Azure IaaS hybrid scenario architecture</span></span>

<span data-ttu-id="d5d18-107">La figura 1 mostra l'architettura di scenari ibridi Microsoft basati su IaaS in Azure.</span><span class="sxs-lookup"><span data-stu-id="d5d18-107">Figure 1 shows the architecture of Microsoft IaaS-based hybrid scenarios in Azure.</span></span>
  
**<span data-ttu-id="d5d18-108">Figura 1: Scenari ibridi Microsoft basati su IaaS in Azure</span><span class="sxs-lookup"><span data-stu-id="d5d18-108">Figure 1: Microsoft IaaS-based hybrid scenarios in Azure</span></span>**

![Scenari ibridi basati su Microsoft IaaS in Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
<span data-ttu-id="d5d18-110">Per ogni livello dell'architettura:</span><span class="sxs-lookup"><span data-stu-id="d5d18-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="d5d18-111">App e scenari</span><span class="sxs-lookup"><span data-stu-id="d5d18-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="d5d18-112">In genere, un carico di lavoro IT è un'applicazione a disponibilità elevata multilivello composta da macchine virtuali di Azure.</span><span class="sxs-lookup"><span data-stu-id="d5d18-112">An IT workload is typically a multi-tier, highly-available application composed of Azure virtual machines (VMs).</span></span>
    
- <span data-ttu-id="d5d18-113">Identità</span><span class="sxs-lookup"><span data-stu-id="d5d18-113">Identity</span></span>
    
    <span data-ttu-id="d5d18-114">Aggiungere server di identità, ad esempio controller di dominio di servizi di dominio Active Directory, al set di server in esecuzione in Azure reti virtuali per l'autenticazione locale.</span><span class="sxs-lookup"><span data-stu-id="d5d18-114">Add identity servers, such as Active Directory Domain Services (AD DS) domain controllers, to the set of servers running in Azure VNets for local authentication.</span></span>
    
- <span data-ttu-id="d5d18-115">Rete</span><span class="sxs-lookup"><span data-stu-id="d5d18-115">Network</span></span>
    
    <span data-ttu-id="d5d18-116">Usa una connessione VPN da sito a sito su Internet o una connessione ExpressRoute con peer privato in IaaS di Azure.</span><span class="sxs-lookup"><span data-stu-id="d5d18-116">Use either a site-to-site VPN connection over the Internet or an ExpressRoute connection with private peering to Azure IaaS.</span></span>
    
- <span data-ttu-id="d5d18-117">Locale</span><span class="sxs-lookup"><span data-stu-id="d5d18-117">On-premises</span></span>
    
    <span data-ttu-id="d5d18-p101">Contiene identità server che vengono sincronizzate con il server di identità in Azure. Può inoltre contenere risorse cui possono accedere le macchine virtuali in esecuzione in Azure, ad esempio la risorsa di archiviazione e l’infrastruttura di gestione dei sistemi.</span><span class="sxs-lookup"><span data-stu-id="d5d18-p101">Contains identity servers that are synchronized with the identity servers running in Azure. Can also contain resources that VMs running in Azure can access, such as storage and systems management infrastructure.</span></span>
    
## <a name="directory-synchronization-server-for-office-365"></a><span data-ttu-id="d5d18-120">Server di sincronizzazione della directory per Office 365</span><span class="sxs-lookup"><span data-stu-id="d5d18-120">Directory synchronization server for Office 365</span></span>

<span data-ttu-id="d5d18-121">L'esecuzione del server di sincronizzazione della directory da una rete virtuale di Azure, come illustrato nella figura 2, è un esempio di estensione dell'infrastruttura di elaborazione e identità al cloud.</span><span class="sxs-lookup"><span data-stu-id="d5d18-121">Running your directory synchronization server from an Azure VNet, as shown in Figure 2, is an example of extending your computing and identity infrastructure to the cloud.</span></span>
  
**<span data-ttu-id="d5d18-122">Figura 2: server di sincronizzazione della directory per Office 365 in Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="d5d18-122">Figure 2: Directory synchronization server for Office 365 in Azure IaaS</span></span>**

![Server di sincronizzazione della directory per Office 365 in IaaS di Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
<span data-ttu-id="d5d18-124">Nella figura 2, una rete locale ospita un'infrastruttura di servizi di dominio Active Directory, con un server proxy e un router ai suoi margini.</span><span class="sxs-lookup"><span data-stu-id="d5d18-124">In Figure 2, an on-premises network hosts a AD DS infrastructure, with a proxy server and a router at its edge.</span></span> <span data-ttu-id="d5d18-125">Il router si connette a un gateway di Azure sul bordo di una rete virtuale di Azure con una connessione VPN da sito a sito o ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="d5d18-125">The router connects to an Azure gateway at the edge of an Azure VNet with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="d5d18-126">All'interno di rete virtuale, un server di sincronizzazione della directory esegue Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="d5d18-126">Inside the VNet, a directory synchronization server runs Azure AD Connect.</span></span>
  
<span data-ttu-id="d5d18-127">Un server di sincronizzazione della directory per Office 365 sincronizza l'elenco degli account in AD DS con il tenant di Azure AD di una sottoscrizione a Office 365.</span><span class="sxs-lookup"><span data-stu-id="d5d18-127">A directory synchronization server for Office 365 synchronizes the list of accounts in AD DS with the Azure AD tenant of an Office 365 subscription.</span></span>
  
<span data-ttu-id="d5d18-128">Un server di sincronizzazione della directory è un server basato su Windows che esegue Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="d5d18-128">A directory synchronization server is a Windows-based server that runs Azure AD Connect.</span></span> <span data-ttu-id="d5d18-129">Per il provisioning più rapido o per ridurre il numero di server locali nell'organizzazione, distribuire il server di sincronizzazione della directory in una rete virtuale (rete virtuale) in IaaS di Azure.</span><span class="sxs-lookup"><span data-stu-id="d5d18-129">For faster provisioning or to reduce the number of on-premises servers in your organization, deploy your directory synchronization server in a virtual network (VNet) in Azure IaaS.</span></span>
  
<span data-ttu-id="d5d18-130">Il server di sincronizzazione della directory esegue il polling di AD DS per le modifiche e quindi li sincronizza con la sottoscrizione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="d5d18-130">The directory synchronization server polls AD DS for changes and then synchronizes them with the Office 365 subscription.</span></span>
  
<span data-ttu-id="d5d18-131">Per ulteriori informazioni, vedere [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="d5d18-131">For more information, see [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>
  
## <a name="line-of-business-lob-application"></a><span data-ttu-id="d5d18-132">Applicazione LOB (line-of-business)</span><span class="sxs-lookup"><span data-stu-id="d5d18-132">Line of business (LOB) application</span></span>

<span data-ttu-id="d5d18-133">La figura 3 mostra la configurazione di un'applicazione LOB basata su server in esecuzione su IaaS di Azure.</span><span class="sxs-lookup"><span data-stu-id="d5d18-133">Figure 3 shows the configuration of a server-based LOB application running in Azure IaaS.</span></span>
  
**<span data-ttu-id="d5d18-134">Figura 3: Applicazione LOB in IaaS di Azure</span><span class="sxs-lookup"><span data-stu-id="d5d18-134">Figure 3: LOB application in Azure IaaS</span></span>**

![Applicazione line-of-business basata su server in Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
<span data-ttu-id="d5d18-p104">Nella figura 3, una rete locale ospita un'infrastruttura di identità e utenti. È collegato a un gateway IaaS di Azure con una connessione VPN da sito a sito o ExpressRoute. IaaS di Azure ospita una rete virtuale contenente i server dell'applicazione LOB.</span><span class="sxs-lookup"><span data-stu-id="d5d18-p104">In Figure 3, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. Azure IaaS hosts a virtual network containing the servers of the LOB application.</span></span>
  
<span data-ttu-id="d5d18-139">È possibile creare applicazioni LOB in esecuzione su macchine virtuali di Azure, che risiedono nelle subnet di una rete virtuale di Azure all'interno di un datacenter di Azure (noto anche come posizione).</span><span class="sxs-lookup"><span data-stu-id="d5d18-139">You can create LOB applications running on Azure VMs, which reside on subnets of an Azure VNet in an Azure datacenter (also known as a location).</span></span>
  
<span data-ttu-id="d5d18-140">Dato che essenzialmente si sta estendendo l'infrastruttura locale ad Azure, è necessario assegnare uno spazio di indirizzi privato unico alle reti virtuali e aggiornare le tabelle di routing locali per garantire l'accessibilità a ogni rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="d5d18-140">Because you are essentially extending your on-premises infrastructure to Azure, you must assign unique private address space to your VNets and update your on-premises routing tables to ensure reachability to each VNet.</span></span>
  
<span data-ttu-id="d5d18-141">Una volta stabilita la connessione, queste macchine virtuali possono essere gestite con connessioni desktop remoto o con un software di gestione dei sistemi, proprio come i server locali.</span><span class="sxs-lookup"><span data-stu-id="d5d18-141">Once connected, these VMs can be managed with remote desktop connections or with your systems management software, just like your on-premises servers.</span></span>
  
<span data-ttu-id="d5d18-142">Configurando le porte pubbliche, queste macchine virtuali sono accessibili anche da Internet per utenti remoti o mobili.</span><span class="sxs-lookup"><span data-stu-id="d5d18-142">By configuring publically-exposed ports, these VMs can also be accessed from the Internet by mobile or remote users.</span></span>
  
<span data-ttu-id="d5d18-143">Per una configurazione di prova, vedere [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="d5d18-143">For a proof-of-concept configuration, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span>
  
<span data-ttu-id="d5d18-144">Attributi di applicazioni LOB ospitate su macchine virtuali di Azure:</span><span class="sxs-lookup"><span data-stu-id="d5d18-144">Attributes of LOB applications hosted on Azure VMs are the following:</span></span>
  
- <span data-ttu-id="d5d18-145">Più livelli</span><span class="sxs-lookup"><span data-stu-id="d5d18-145">Multiple tiers</span></span>
    
    <span data-ttu-id="d5d18-p105">Applicazioni LOB tipiche utilizzano un approccio graduale. I set di server forniscono identità, elaborazione di database, elaborazione logica e applicazioni, server Web front-end per l'accesso di dipendenti o clienti. </span><span class="sxs-lookup"><span data-stu-id="d5d18-p105">Typical LOB applications use a tiered approach. Sets of servers provide identity, database processing, application and logic processing, and front-end web servers for employee or customer access.</span></span> 
    
- <span data-ttu-id="d5d18-148">Disponibilità elevata</span><span class="sxs-lookup"><span data-stu-id="d5d18-148">High availability</span></span>
    
    <span data-ttu-id="d5d18-p106">Applicazioni LOB tipiche forniscono disponibilità elevata utilizzando più server in ogni livello. IaaS di Azure fornisce un contratto di servizio di operatività del 99,9% per i server in set di disponibilità di Azure. </span><span class="sxs-lookup"><span data-stu-id="d5d18-p106">Typical LOB applications provide high availability by using multiple servers in each tier. Azure IaaS provides a 99.9% uptime SLA for servers in Azure availability sets.</span></span> 
    
- <span data-ttu-id="d5d18-151">Distribuzione del carico</span><span class="sxs-lookup"><span data-stu-id="d5d18-151">Load distribution</span></span>
    
    <span data-ttu-id="d5d18-p107">Per distribuire il carico del traffico di rete tra i server di un livello, è possibile usare un bilanciamento del carico di Azure interno o con connessione Internet. In alternativa, usare un'applicazione di bilanciamento del carico dedicata disponibile in Azure Marketplace.</span><span class="sxs-lookup"><span data-stu-id="d5d18-p107">To distribute the load of network traffic among multiple servers in a tier, you can use an Internet-facing or internal Azure load balancer. Or, you can use a dedicated load balancer appliance available from the Azure marketplace.</span></span>
    
- <span data-ttu-id="d5d18-154">Sicurezza</span><span class="sxs-lookup"><span data-stu-id="d5d18-154">Security</span></span>
    
    <span data-ttu-id="d5d18-p108">Per proteggere i server dal traffico in ingresso provenienti da Internet, è possibile utilizzare gruppi di sicurezza di rete Azure. Puoi definire di concedere o negare il traffico verso una subnet o l'interfaccia di rete di una singola macchina virtuale.</span><span class="sxs-lookup"><span data-stu-id="d5d18-p108">To protect servers from unsolicited incoming traffic from the Internet, you can use Azure network security groups. You can define allowed or denied traffic for a subnet or the network interface of an individual virtual machine.</span></span>
    
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="d5d18-157">Farm di SharePoint Server 2016 in Azure</span><span class="sxs-lookup"><span data-stu-id="d5d18-157">SharePoint Server 2016 farm in Azure</span></span>

<span data-ttu-id="d5d18-158">Un esempio di applicazione LOB altamente disponibile di più livelli in Azure è una farm di SharePoint Server 2016, come illustrato nella figura 4.</span><span class="sxs-lookup"><span data-stu-id="d5d18-158">An example of a multi-tier, highly-available LOB application in Azure is a SharePoint Server 2016 farm, as shown in Figure 4.</span></span>
  
**<span data-ttu-id="d5d18-159">Figura 4: Una farm di SharePoint Server 2016 a disponibilità elevata in IaaS di Azure</span><span class="sxs-lookup"><span data-stu-id="d5d18-159">Figure 4: A high-availability SharePoint Server 2016 farm in Azure IaaS</span></span>**

![Una farm di SharePoint Server 2016 a disponibilità elevata in IaaS di Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
<span data-ttu-id="d5d18-p109">Nella figura 4, una rete locale ospita un'infrastruttura di identità e utenti. È collegato a un gateway IaaS di Azure con una connessione VPN da sito a sito o ExpressRoute. La rete virtuale di Azure contiene i server della farm di SharePoint Server 2016, che include livelli separati per server front-end, server di applicazioni, cluster di SQL Server e controller di dominio.</span><span class="sxs-lookup"><span data-stu-id="d5d18-p109">In Figure 4, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains the servers of the SharePoint Server 2016 farm, which includes separate tiers for the front-end servers, the application servers, the SQL Server cluster, and the domain controllers.</span></span>
  
<span data-ttu-id="d5d18-164">Questa configurazione offre i seguenti attributi delle applicazioni LOB in Azure: </span><span class="sxs-lookup"><span data-stu-id="d5d18-164">This configuration has the following attributes of LOB applications in Azure:</span></span> 
  
- <span data-ttu-id="d5d18-165">Livelli</span><span class="sxs-lookup"><span data-stu-id="d5d18-165">Tiers</span></span>
    
    <span data-ttu-id="d5d18-166">Server che eseguono ruoli diversi all'interno della farm creano i livelli e ogni livello ha una propria subnet.</span><span class="sxs-lookup"><span data-stu-id="d5d18-166">Servers running different roles within the farm create the tiers and each tier has its own subnet.</span></span>
    
- <span data-ttu-id="d5d18-167">Disponibilità elevata</span><span class="sxs-lookup"><span data-stu-id="d5d18-167">High-availability</span></span>
    
    <span data-ttu-id="d5d18-168">È ottenuta utilizzando più di un server in ogni livello e tutti i server di un livello di immissione nello stesso set di disponibilità.</span><span class="sxs-lookup"><span data-stu-id="d5d18-168">Achieved by using more than one server in each tier and placing all the servers of a tier in the same availability set.</span></span>
    
- <span data-ttu-id="d5d18-169">Distribuzione del carico</span><span class="sxs-lookup"><span data-stu-id="d5d18-169">Load distribution</span></span>
    
    <span data-ttu-id="d5d18-170">Servizi di bilanciamento del carico Azure interno distribuiscono il traffico web client in arrivo ai server front-end (WEB1 e WEB2) e all'indirizzo IP del listener del cluster SQL Server (SQL1, SQL2 e MN1).</span><span class="sxs-lookup"><span data-stu-id="d5d18-170">Internal Azure load balancers distribute the incoming client web traffic to the front-end servers (WEB1 and WEB2) and to the listener IP address of the SQL Server cluster (SQL1, SQL2, and MN1).</span></span>
    
- <span data-ttu-id="d5d18-171">Sicurezza</span><span class="sxs-lookup"><span data-stu-id="d5d18-171">Security</span></span>
    
    <span data-ttu-id="d5d18-172">Gruppi di sicurezza di rete per ogni subnet consentono di configurare il traffico in ingresso e in uscita consentito.</span><span class="sxs-lookup"><span data-stu-id="d5d18-172">Network security groups for each subnet let you to configure allowed inbound and outbound traffic.</span></span>
    
<span data-ttu-id="d5d18-173">Seguire questo percorso per l’adozione:</span><span class="sxs-lookup"><span data-stu-id="d5d18-173">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="d5d18-174">Valutare e sperimentare</span><span class="sxs-lookup"><span data-stu-id="d5d18-174">Evaluate and experiment</span></span>
    
    <span data-ttu-id="d5d18-175">Per informazioni sui vantaggi derivanti dall'esecuzione di SharePoint Server 2016 in Azure, vedere [SharePoint server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) .</span><span class="sxs-lookup"><span data-stu-id="d5d18-175">See [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) to understand the benefits of running SharePoint Server 2016 in Azure.</span></span>
    
    <span data-ttu-id="d5d18-176">Vedere [Intranet SharePoint Server 2016 in Azure Dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) per creare un ambiente di sviluppo/test simulato</span><span class="sxs-lookup"><span data-stu-id="d5d18-176">See [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) to build a simulated dev/test environment</span></span>
    
2. <span data-ttu-id="d5d18-177">Struttura</span><span class="sxs-lookup"><span data-stu-id="d5d18-177">Design</span></span>
    
    <span data-ttu-id="d5d18-178">Vedere [progettazione di una farm di SharePoint Server 2016 in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) per eseguire un processo per determinare il set di elementi di rete, di computo e di archiviazione di IaaS di Azure per ospitare la farm e le relative impostazioni.</span><span class="sxs-lookup"><span data-stu-id="d5d18-178">See [Designing a SharePoint Server 2016 farm in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) to step through a process to determine the set of Azure IaaS networking, compute, and storage elements to host your farm and their settings.</span></span>
    
3. <span data-ttu-id="d5d18-179">Distribuzione</span><span class="sxs-lookup"><span data-stu-id="d5d18-179">Deploy</span></span>
    
    <span data-ttu-id="d5d18-180">Vedere [deployIng SharePoint server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) to step through the end-to-end Configuration della farm a disponibilità elevata in cinque fasi.</span><span class="sxs-lookup"><span data-stu-id="d5d18-180">See [Deploying SharePoint Server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) to step through the end-to-end configuration of the high-availability farm in five phases.</span></span>
    
## <a name="federated-identity-for-office-365-in-azure"></a><span data-ttu-id="d5d18-181">Identità federata per Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="d5d18-181">Federated identity for Office 365 in Azure</span></span>

<span data-ttu-id="d5d18-182">Un altro esempio di un'applicazione LOB a più livelli e a disponibilità elevata in Azure è l'identità federata per Office 365.</span><span class="sxs-lookup"><span data-stu-id="d5d18-182">Another example of a multi-tier, highly-available LOB application in Azure is federated identity for Office 365.</span></span>
  
**<span data-ttu-id="d5d18-183">Figura 5: infrastruttura di identità federata a disponibilità elevata per Office 365 in Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="d5d18-183">Figure 5: A high-availability federated identity infrastructure for Office 365 in Azure IaaS</span></span>**

![Un'infrastruttura di autenticazione federata a disponibilità elevata di Office 365 in Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
<span data-ttu-id="d5d18-185">Nella figura 5, una rete locale ospita un'infrastruttura di identità e gli utenti.</span><span class="sxs-lookup"><span data-stu-id="d5d18-185">In Figure 5, an on-premises network hosts an identity infrastructure and users.</span></span> <span data-ttu-id="d5d18-186">È collegato a un gateway IaaS di Azure con una connessione VPN da sito a sito o ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="d5d18-186">It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="d5d18-187">Rete virtuale di Azure contiene server proxy Web, server Active Directory Federation Services (AD FS) e controller di dominio Active Directory Domain Services (AD DS).</span><span class="sxs-lookup"><span data-stu-id="d5d18-187">The Azure VNet contains web proxy servers, Active Directory Federation Services (AD FS) servers, and Active Directory Domain Services (AD DS) domain controllers.</span></span>
  
<span data-ttu-id="d5d18-188">Questa configurazione offre i seguenti attributi delle applicazioni LOB in Azure: </span><span class="sxs-lookup"><span data-stu-id="d5d18-188">This configuration has the following attributes of LOB applications in Azure:</span></span>
  
- <span data-ttu-id="d5d18-189">**Livelli:** Esistono livelli per i server proxy Web, per i server AD FS e per i controller di dominio AD DS.</span><span class="sxs-lookup"><span data-stu-id="d5d18-189">**Tiers:** There are tiers for web proxy servers, AD FS servers, and AD DS domain controllers.</span></span>
    
- <span data-ttu-id="d5d18-190">**Distribuzione del carico:** Un bilanciamento del carico di Azure esterno distribuisce le richieste di autenticazione del client in arrivo ai proxy Web e un bilanciamento del carico di Azure interno distribuisce le richieste di autenticazione ai server ADFS.</span><span class="sxs-lookup"><span data-stu-id="d5d18-190">**Load distribution:** An external Azure load balancer distributes the incoming client authentication requests to the web proxies and an internal Azure load balancer distributes authentication requests to the AD FS servers.</span></span>
    
<span data-ttu-id="d5d18-191">Seguire questo percorso per l’adozione:</span><span class="sxs-lookup"><span data-stu-id="d5d18-191">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="d5d18-192">Valutare e sperimentare</span><span class="sxs-lookup"><span data-stu-id="d5d18-192">Evaluate and experiment</span></span>
    
    <span data-ttu-id="d5d18-193">Vedere [l'identità federata per l'ambiente di sviluppo/test di office 365](federated-identity-for-your-office-365-dev-test-environment.md) per creare un ambiente di sviluppo/test simulato per l'autenticazione federata con Office 365.</span><span class="sxs-lookup"><span data-stu-id="d5d18-193">See [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md) to build a simulated dev/test environment for federated authentication with Office 365.</span></span>
    
2. <span data-ttu-id="d5d18-194">Distribuzione</span><span class="sxs-lookup"><span data-stu-id="d5d18-194">Deploy</span></span>
    
    <span data-ttu-id="d5d18-195">Vedere [deploy High Availability Federated Authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) per passare alla configurazione end-to-end dell'infrastruttura ad FS a disponibilità elevata in cinque fasi.</span><span class="sxs-lookup"><span data-stu-id="d5d18-195">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) to step through the end-to-end configuration of the high availability AD FS infrastructure in five phases.</span></span>
    
    
## <a name="see-also"></a><span data-ttu-id="d5d18-196">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d5d18-196">See Also</span></span>

[<span data-ttu-id="d5d18-197">Cloud ibrido Microsoft per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="d5d18-197">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="d5d18-198">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="d5d18-198">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


