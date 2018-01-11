---
title: Scenari cloud ibridi per IaaS di Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: 'Riepilogo: Informazioni su architettura ibrida e gli scenari per l''infrastruttura di Microsoft come servizio (IaaS)-basato su cloud offerte in Azure.'
ms.openlocfilehash: 5ec74058174724b6497a5cb41e67896818ef4d05
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a><span data-ttu-id="ade56-103">Scenari cloud ibridi per IaaS di Azure</span><span class="sxs-lookup"><span data-stu-id="ade56-103">Hybrid cloud scenarios for Azure IaaS</span></span>

 <span data-ttu-id="ade56-104">**Riepilogo:** Acquisire familiarità con l'architettura ibrida e gli scenari per l'infrastruttura di Microsoft come servizio (IaaS)-basato su cloud offerte in Azure.</span><span class="sxs-lookup"><span data-stu-id="ade56-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Infrastructure as a Service (IaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="ade56-105">Estendere l'infrastruttura di gestione delle identità e di calcolo locale nel cloud ospitando i carichi di lavoro IT in esecuzione su reti virtuali Azure cross-premise. </span><span class="sxs-lookup"><span data-stu-id="ade56-105">Extend your on-premises computing and identity infrastructure into the cloud by hosting IT workloads running in cross-premises Azure virtual networks (VNets).</span></span> 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a><span data-ttu-id="ade56-106">Architettura per scenario ibrido in IaaS di Azure</span><span class="sxs-lookup"><span data-stu-id="ade56-106">Azure IaaS hybrid scenario architecture</span></span>

<span data-ttu-id="ade56-107">La figura 1 mostra l'architettura di scenari ibridi Microsoft basati su IaaS in Azure.</span><span class="sxs-lookup"><span data-stu-id="ade56-107">Figure 1 shows the architecture of Microsoft IaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="ade56-108">**Nella figura 1: Scenari di ibrida basata su IaaS Microsoft in Azure**</span><span class="sxs-lookup"><span data-stu-id="ade56-108">**Figure 1: Microsoft IaaS-based hybrid scenarios in Azure**</span></span>

![Scenari ibridi Microsoft basati su IaaS in Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS.png)
  
<span data-ttu-id="ade56-110">Per ogni livello dell'architettura:</span><span class="sxs-lookup"><span data-stu-id="ade56-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="ade56-111">App e scenari</span><span class="sxs-lookup"><span data-stu-id="ade56-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="ade56-112">In genere, un carico di lavoro IT è un'applicazione a disponibilità elevata multilivello composta da macchine virtuali di Azure.</span><span class="sxs-lookup"><span data-stu-id="ade56-112">An IT workload is typically a multi-tier, highly-available application composed of Azure virtual machines (VMs).</span></span>
    
- <span data-ttu-id="ade56-113">Identità</span><span class="sxs-lookup"><span data-stu-id="ade56-113">Identity</span></span>
    
    <span data-ttu-id="ade56-114">Aggiunge server di identità, come i controller di dominio di AD di Windows Server, al set di server in esecuzione sulle reti virtuali di Azure per l'autenticazione locale.</span><span class="sxs-lookup"><span data-stu-id="ade56-114">Add identity servers, such as Windows Server AD domain controllers, to the set of servers running in Azure VNets for local authentication.</span></span>
    
- <span data-ttu-id="ade56-115">Rete</span><span class="sxs-lookup"><span data-stu-id="ade56-115">Network</span></span>
    
    <span data-ttu-id="ade56-116">Usa una connessione VPN da sito a sito su Internet o una connessione ExpressRoute con peer privato in IaaS di Azure.</span><span class="sxs-lookup"><span data-stu-id="ade56-116">Use either a site-to-site VPN connection over the Internet or an ExpressRoute connection with private peering to Azure IaaS.</span></span>
    
- <span data-ttu-id="ade56-117">Locale</span><span class="sxs-lookup"><span data-stu-id="ade56-117">On-premises</span></span>
    
    <span data-ttu-id="ade56-p101">Contiene identità server che vengono sincronizzate con il server di identità in Azure. Può inoltre contenere risorse cui possono accedere le macchine virtuali in esecuzione in Azure, ad esempio la risorsa di archiviazione e l’infrastruttura di gestione dei sistemi.</span><span class="sxs-lookup"><span data-stu-id="ade56-p101">Contains identity servers that are synchronized with the identity servers running in Azure. Can also contain resources that VMs running in Azure can access, such as storage and systems management infrastructure.</span></span>
    
## <a name="dirsync-server-for-office-365"></a><span data-ttu-id="ade56-120">Server DirSync per Office 365</span><span class="sxs-lookup"><span data-stu-id="ade56-120">DirSync server for Office 365</span></span>

<span data-ttu-id="ade56-121">L’esecuzione del server di sincronizzazione della directory (DirSync) da una rete virtuale di Azure, come illustrato nella figura 2, è un esempio di come estendere l'infrastruttura di identità e calcolo al cloud.</span><span class="sxs-lookup"><span data-stu-id="ade56-121">Running your directory synchronization (DirSync) server from an Azure VNet, as shown in Figure 2, is an example of extending your computing and identity infrastructure to the cloud.</span></span>
  
<span data-ttu-id="ade56-122">**Figura 2: Server DirSync per Office 365 in Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="ade56-122">**Figure 2: DirSync server for Office 365 in Azure IaaS**</span></span>

![Server DirSync per Office 365 in IaaS di Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_DirSync.png)
  
<span data-ttu-id="ade56-p102">Nella figura 2, una rete locale ospita un'infrastruttura di Windows Server Active Directory, con un server proxy e un router in corrispondenza del bordo. Il router si connette a un gateway Azure in corrispondenza del bordo di un VNet Azure con una connessione VPN o ExpressRoute sito per sito. All'interno di VNet, un server di DirSync esegue Connetti Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="ade56-p102">In Figure 2, an on-premises network hosts a Windows Server AD infrastructure, with a proxy server and a router at its edge. The router connects to an Azure gateway at the edge of an Azure VNet with a site-to-site VPN or ExpressRoute connection. Inside the VNet, a DirSync server runs Azure AD Connect.</span></span>
  
<span data-ttu-id="ade56-127">Un server DirSync per Office 365 sincronizza l'elenco degli account in Windows Server AD con il tenant di Azure AD di un abbonamento a Office 365.</span><span class="sxs-lookup"><span data-stu-id="ade56-127">A DirSync server for Office 365 synchronizes the list of accounts in Windows Server AD with the Azure AD tenant of an Office 365 subscription.</span></span>
  
<span data-ttu-id="ade56-p103">Un server DirSync è un server basato su Windows che esegue Azure AD Connect. Per un provisioning più veloce o per ridurre il numero di server in locale nell'organizzazione, distribuire il server DirSync in una rete virtuale (VNet) in Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="ade56-p103">A DirSync server is a Windows-based server that runs Azure AD Connect. For faster provisioning or to reduce the number of on-premises servers in your organization, deploy your DirSync server in a virtual network (VNet) in Azure IaaS.</span></span>
  
<span data-ttu-id="ade56-130">Il server DirSync sonda Windows Server AD per le modifiche, quindi le sincronizza con l’abbonamento a Office 365.</span><span class="sxs-lookup"><span data-stu-id="ade56-130">The DirSync server polls Windows Server AD for changes and then synchronizes them with the Office 365 subscription.</span></span>
  
<span data-ttu-id="ade56-131">Per ulteriori informazioni, vedere [Distribuzione di Office 365 DirSync in Azure](https://technet.microsoft.com/library/dn635310.aspx).</span><span class="sxs-lookup"><span data-stu-id="ade56-131">For more information, see [Deploy Office 365 DirSync in Azure](https://technet.microsoft.com/library/dn635310.aspx).</span></span>
  
## <a name="line-of-business-lob-application"></a><span data-ttu-id="ade56-132">Applicazione LOB (line-of-business)</span><span class="sxs-lookup"><span data-stu-id="ade56-132">Line of business (LOB) application</span></span>

<span data-ttu-id="ade56-133">La figura 3 mostra la configurazione di un'applicazione LOB basata su server in esecuzione su IaaS di Azure.</span><span class="sxs-lookup"><span data-stu-id="ade56-133">Figure 3 shows the configuration of a server-based LOB application running in Azure IaaS.</span></span>
  
<span data-ttu-id="ade56-134">**Figura 3: Applicazione LOB in Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="ade56-134">**Figure 3: LOB application in Azure IaaS**</span></span>

![Applicazione line-of-business basata su server in Azure IaaS](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_Ex.png)
  
<span data-ttu-id="ade56-p104">Nella figura 3, una rete locale ospita un'infrastruttura di identità e utenti. È collegato a un gateway IaaS di Azure con una connessione VPN da sito a sito o ExpressRoute. IaaS di Azure ospita una rete virtuale contenente i server dell'applicazione LOB.</span><span class="sxs-lookup"><span data-stu-id="ade56-p104">In Figure 3, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. Azure IaaS hosts a virtual network containing the servers of the LOB application.</span></span>
  
<span data-ttu-id="ade56-139">È possibile creare le applicazioni LOB in esecuzione su macchine virtuali di Azure, che si trovano in subnet di un VNet Azure in un Data Center Azure (noto anche come posizione).</span><span class="sxs-lookup"><span data-stu-id="ade56-139">You can create LOB applications running on Azure VMs, which reside on subnets of an Azure VNet in an Azure datacenter (also known as a location).</span></span>
  
<span data-ttu-id="ade56-140">Dato che essenzialmente si sta estendendo l'infrastruttura locale ad Azure, è necessario assegnare uno spazio di indirizzi privato unico alle reti virtuali e aggiornare le tabelle di routing locali per garantire l'accessibilità a ogni rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="ade56-140">Because you are essentially extending your on-premises infrastructure to Azure, you must assign unique private address space to your VNets and update your on-premises routing tables to ensure reachability to each VNet.</span></span>
  
<span data-ttu-id="ade56-141">Una volta stabilita la connessione, queste macchine virtuali possono essere gestite con connessioni desktop remoto o con un software di gestione dei sistemi, proprio come i server locali.</span><span class="sxs-lookup"><span data-stu-id="ade56-141">Once connected, these VMs can be managed with remote desktop connections or with your systems management software, just like your on-premises servers.</span></span>
  
<span data-ttu-id="ade56-142">Configurando le porte pubbliche, queste macchine virtuali sono accessibili anche da Internet per utenti remoti o mobili.</span><span class="sxs-lookup"><span data-stu-id="ade56-142">By configuring publically-exposed ports, these VMs can also be accessed from the Internet by mobile or remote users.</span></span>
  
<span data-ttu-id="ade56-143">Per una configurazione di prova, vedere [simulato tra locali reti virtuali di Azure](simulated-cross-premises-virtual-network-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="ade56-143">For a proof-of-concept configuration, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span>
  
<span data-ttu-id="ade56-144">Attributi di applicazioni LOB ospitate su macchine virtuali di Azure:</span><span class="sxs-lookup"><span data-stu-id="ade56-144">Attributes of LOB applications hosted on Azure VMs are the following:</span></span>
  
- <span data-ttu-id="ade56-145">Più livelli</span><span class="sxs-lookup"><span data-stu-id="ade56-145">Multiple tiers</span></span>
    
    <span data-ttu-id="ade56-p105">Applicazioni LOB tipiche utilizzano un approccio graduale. I set di server forniscono identità, elaborazione di database, elaborazione logica e applicazioni, server Web front-end per l'accesso di dipendenti o clienti. </span><span class="sxs-lookup"><span data-stu-id="ade56-p105">Typical LOB applications use a tiered approach. Sets of servers provide identity, database processing, application and logic processing, and front-end web servers for employee or customer access.</span></span> 
    
- <span data-ttu-id="ade56-148">Disponibilità elevata</span><span class="sxs-lookup"><span data-stu-id="ade56-148">High availability</span></span>
    
    <span data-ttu-id="ade56-p106">Applicazioni LOB tipiche forniscono disponibilità elevata utilizzando più server in ogni livello. IaaS di Azure fornisce un contratto di servizio di operatività del 99,9% per i server in set di disponibilità di Azure. </span><span class="sxs-lookup"><span data-stu-id="ade56-p106">Typical LOB applications provide high availability by using multiple servers in each tier. Azure IaaS provides a 99.9% uptime SLA for servers in Azure availability sets.</span></span> 
    
- <span data-ttu-id="ade56-151">Distribuzione del carico</span><span class="sxs-lookup"><span data-stu-id="ade56-151">Load distribution</span></span>
    
    <span data-ttu-id="ade56-p107">Per distribuire il carico del traffico di rete tra i server di un livello, è possibile usare un bilanciamento del carico di Azure interno o con connessione Internet. In alternativa, usare un'applicazione di bilanciamento del carico dedicata disponibile in Azure Marketplace.</span><span class="sxs-lookup"><span data-stu-id="ade56-p107">To distribute the load of network traffic among multiple servers in a tier, you can use an Internet-facing or internal Azure load balancer. Or, you can use a dedicated load balancer appliance available from the Azure marketplace.</span></span>
    
- <span data-ttu-id="ade56-154">Sicurezza</span><span class="sxs-lookup"><span data-stu-id="ade56-154">Security</span></span>
    
    <span data-ttu-id="ade56-p108">Per proteggere i server dal traffico in ingresso provenienti da Internet, è possibile utilizzare gruppi di sicurezza di rete Azure. Puoi definire di concedere o negare il traffico verso una subnet o l'interfaccia di rete di una singola macchina virtuale.</span><span class="sxs-lookup"><span data-stu-id="ade56-p108">To protect servers from unsolicited incoming traffic from the Internet, you can use Azure network security groups. You can define allowed or denied traffic for a subnet or the network interface of an individual virtual machine.</span></span>
    
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="ade56-157">Farm di SharePoint Server 2016 in Azure</span><span class="sxs-lookup"><span data-stu-id="ade56-157">SharePoint Server 2016 farm in Azure</span></span>

<span data-ttu-id="ade56-158">Un esempio di applicazione LOB altamente disponibile di più livelli in Azure è una farm di SharePoint Server 2016, come illustrato nella figura 4.</span><span class="sxs-lookup"><span data-stu-id="ade56-158">An example of a multi-tier, highly-available LOB application in Azure is a SharePoint Server 2016 farm, as shown in Figure 4.</span></span>
  
<span data-ttu-id="ade56-159">**Figura 4: Una disponibilità elevata 2016 di SharePoint Server farm in Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="ade56-159">**Figure 4: A high-availability SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Una farm di SharePoint Server 2016 a disponibilità elevata in IaaS di Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_SP2016.png)
  
<span data-ttu-id="ade56-p109">Nella figura 4, una rete locale ospita un'infrastruttura di identità e utenti. È collegato a un gateway IaaS di Azure con una connessione VPN da sito a sito o ExpressRoute. La rete virtuale di Azure contiene i server della farm di SharePoint Server 2016, che include livelli separati per server front-end, server di applicazioni, cluster di SQL Server e controller di dominio.</span><span class="sxs-lookup"><span data-stu-id="ade56-p109">In Figure 4, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains the servers of the SharePoint Server 2016 farm, which includes separate tiers for the front-end servers, the application servers, the SQL Server cluster, and the domain controllers.</span></span>
  
<span data-ttu-id="ade56-164">Questa configurazione offre i seguenti attributi delle applicazioni LOB in Azure: </span><span class="sxs-lookup"><span data-stu-id="ade56-164">This configuration has the following attributes of LOB applications in Azure:</span></span> 
  
- <span data-ttu-id="ade56-165">Livelli</span><span class="sxs-lookup"><span data-stu-id="ade56-165">Tiers</span></span>
    
    <span data-ttu-id="ade56-166">Server che eseguono diversi ruoli all'interno della farm crea i livelli e ogni livello ha una propria subnet.</span><span class="sxs-lookup"><span data-stu-id="ade56-166">Servers running different roles within the farm create the tiers and each tier has its own subnet.</span></span>
    
- <span data-ttu-id="ade56-167">Disponibilità elevata</span><span class="sxs-lookup"><span data-stu-id="ade56-167">High-availability</span></span>
    
    <span data-ttu-id="ade56-168">È ottenuta utilizzando più di un server in ogni livello e tutti i server di un livello di immissione nello stesso set di disponibilità.</span><span class="sxs-lookup"><span data-stu-id="ade56-168">Achieved by using more than one server in each tier and placing all the servers of a tier in the same availability set.</span></span>
    
- <span data-ttu-id="ade56-169">Distribuzione del carico</span><span class="sxs-lookup"><span data-stu-id="ade56-169">Load distribution</span></span>
    
    <span data-ttu-id="ade56-170">Servizi di bilanciamento del carico Azure interno distribuiscono il traffico web client in arrivo ai server front-end (WEB1 e WEB2) e all'indirizzo IP del listener del cluster SQL Server (SQL1, SQL2 e MN1).</span><span class="sxs-lookup"><span data-stu-id="ade56-170">Internal Azure load balancers distribute the incoming client web traffic to the front-end servers (WEB1 and WEB2) and to the listener IP address of the SQL Server cluster (SQL1, SQL2, and MN1).</span></span>
    
- <span data-ttu-id="ade56-171">Sicurezza</span><span class="sxs-lookup"><span data-stu-id="ade56-171">Security</span></span>
    
    <span data-ttu-id="ade56-172">Gruppi di sicurezza di rete per ogni subnet consentono di configurare il traffico in ingresso e in uscita consentito.</span><span class="sxs-lookup"><span data-stu-id="ade56-172">Network security groups for each subnet let you to configure allowed inbound and outbound traffic.</span></span>
    
<span data-ttu-id="ade56-173">Seguire questo percorso per l’adozione:</span><span class="sxs-lookup"><span data-stu-id="ade56-173">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="ade56-174">Valutare e sperimentare</span><span class="sxs-lookup"><span data-stu-id="ade56-174">Evaluate and experiment</span></span>
    
    <span data-ttu-id="ade56-175">Vedere [2016 di SharePoint Server in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx) per acquisire familiarità con i vantaggi dell'esecuzione di SharePoint Server 2016 in Azure.</span><span class="sxs-lookup"><span data-stu-id="ade56-175">See [SharePoint Server 2016 in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx) to understand the benefits of running SharePoint Server 2016 in Azure.</span></span>
    
    <span data-ttu-id="ade56-176">Vedere [Intranet SharePoint Server 2016 nell'ambiente di sviluppo e di testing Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx) per creare un ambiente di sviluppo e di testing simulate</span><span class="sxs-lookup"><span data-stu-id="ade56-176">See [Intranet SharePoint Server 2016 in Azure dev/test environment](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx) to build a simulated dev/test environment</span></span>
    
2. <span data-ttu-id="ade56-177">Struttura</span><span class="sxs-lookup"><span data-stu-id="ade56-177">Design</span></span>
    
    <span data-ttu-id="ade56-178">Vedere [Progettazione di una farm di SharePoint Server 2016 in Azure](https://technet.microsoft.com/library/mt779108%28v=office.16%29.aspx) per eseguire un processo per determinare il set di rete Azure IaaS, compute ed elementi di archiviazione per ospitare la farm e le relative impostazioni.</span><span class="sxs-lookup"><span data-stu-id="ade56-178">See [Designing a SharePoint Server 2016 farm in Azure](https://technet.microsoft.com/library/mt779108%28v=office.16%29.aspx) to step through a process to determine the set of Azure IaaS networking, compute, and storage elements to host your farm and their settings.</span></span>
    
3. <span data-ttu-id="ade56-179">Distribuzione</span><span class="sxs-lookup"><span data-stu-id="ade56-179">Deploy</span></span>
    
    <span data-ttu-id="ade56-180">Vedere [distribuzione di SharePoint Server 2016 con SQL Server AlwaysOn Availability Groups in Azure](https://technet.microsoft.com/library/mt793552%28v=office.16%29.aspx) per eseguire la configurazione end-to-end della farm di disponibilità elevata in cinque fasi.</span><span class="sxs-lookup"><span data-stu-id="ade56-180">See [Deploying SharePoint Server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://technet.microsoft.com/library/mt793552%28v=office.16%29.aspx) to step through the end-to-end configuration of the high-availability farm in five phases.</span></span>
    
## <a name="federated-identity-for-office-365-in-azure"></a><span data-ttu-id="ade56-181">Identità federata per Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="ade56-181">Federated identity for Office 365 in Azure</span></span>

<span data-ttu-id="ade56-182">Un altro esempio di un'applicazione LOB a più livelli e altamente disponibile in Azure è identità federata per Office 365.</span><span class="sxs-lookup"><span data-stu-id="ade56-182">Another example of a multi-tier, highly-available LOB application in Azure is federated identity for Office 365.</span></span>
  
<span data-ttu-id="ade56-183">**Figura 5: Un'infrastruttura di identità federata di disponibilità elevata per Office 365 in Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="ade56-183">**Figure 5: A high-availability federated identity infrastructure for Office 365 in Azure IaaS**</span></span>

![La configurazione finale dell'infrastruttura di autenticazione federata di Office 365 con disponibilità elevata](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_ADFS.png)
  
<span data-ttu-id="ade56-p110">Nella figura 5, una rete locale ospita un'infrastruttura di identità e degli utenti. Si connette a un gateway Azure IaaS con una connessione VPN o ExpressRoute sito per sito. VNet Azure contiene il server proxy web, server di Active Directory Federation Services (ADFS) e i controller di dominio Windows Server Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="ade56-p110">In Figure 5, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains web proxy servers, Active Directory Federation Services (AD FS) servers, and Windows Server Active Directory (AD) domain controllers.</span></span>
  
<span data-ttu-id="ade56-188">Questa configurazione offre i seguenti attributi delle applicazioni LOB in Azure: </span><span class="sxs-lookup"><span data-stu-id="ade56-188">This configuration has the following attributes of LOB applications in Azure:</span></span>
  
- <span data-ttu-id="ade56-189">**Livelli:** Sono disponibili i livelli per server proxy web, server AD FS e controller di dominio di Windows Server Active Directory.</span><span class="sxs-lookup"><span data-stu-id="ade56-189">**Tiers:** There are tiers for web proxy servers, AD FS servers, and Windows Server AD domain controllers.</span></span>
    
- <span data-ttu-id="ade56-190">**Distribuzione del carico:** Un servizio di bilanciamento del carico esterno Azure distribuisce le richieste di autenticazione client in ingresso per il proxy web e un servizio di bilanciamento del carico interno Azure distribuisce le richieste di autenticazione per i server ADFS.</span><span class="sxs-lookup"><span data-stu-id="ade56-190">**Load distribution:** An external Azure load balancer distributes the incoming client authentication requests to the web proxies and an internal Azure load balancer distributes authentication requests to the AD FS servers.</span></span>
    
<span data-ttu-id="ade56-191">Seguire questo percorso per l’adozione:</span><span class="sxs-lookup"><span data-stu-id="ade56-191">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="ade56-192">Valutare e sperimentare</span><span class="sxs-lookup"><span data-stu-id="ade56-192">Evaluate and experiment</span></span>
    
    <span data-ttu-id="ade56-193">[Identità federata per l'ambiente di sviluppo e di testing di Office 365](federated-identity-for-your-office-365-dev-test-environment.md) per creare un ambiente di sviluppo e di testing simulato per l'autenticazione federata con Office 365, vedere.</span><span class="sxs-lookup"><span data-stu-id="ade56-193">See [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md) to build a simulated dev/test environment for federated authentication with Office 365.</span></span>
    
2. <span data-ttu-id="ade56-194">Distribuzione</span><span class="sxs-lookup"><span data-stu-id="ade56-194">Deploy</span></span>
    
    <span data-ttu-id="ade56-195">Vedere [l'autenticazione federata distribuire la disponibilità elevata per Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) per eseguire la configurazione end-to-end della disponibilità elevata dell'infrastruttura ADFS in cinque fasi.</span><span class="sxs-lookup"><span data-stu-id="ade56-195">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) to step through the end-to-end configuration of the high availability AD FS infrastructure in five phases.</span></span>
    
<span data-ttu-id="ade56-196">Consultare queste risorse aggiuntive:</span><span class="sxs-lookup"><span data-stu-id="ade56-196">See these additional resources:</span></span>
  
- [<span data-ttu-id="ade56-197">Architettura degli ambienti ibridi di Cloud</span><span class="sxs-lookup"><span data-stu-id="ade56-197">Architecting Hybrid Cloud Environments</span></span>](https://gallery.technet.microsoft.com/Architecting-Hybrid-Cloud-a7dc9f24/file/147475/1/Architecting%20Hybrid%20Cloud%20Environments%20V1.docx)
    
- [<span data-ttu-id="ade56-198">Estensione del centro dati per il corso Cloud Microsoft Virtual Academy</span><span class="sxs-lookup"><span data-stu-id="ade56-198">Extend Your Datacenter to the Cloud Microsoft Virtual Academy course</span></span>](https://mva.microsoft.com/en-US/training-courses/extend-your-datacenter-to-the-cloud-13908?l=7fG3tAouB_7100115881)
    
- [<span data-ttu-id="ade56-199">Progettare e creare un'applicazione LOB in Azure</span><span class="sxs-lookup"><span data-stu-id="ade56-199">Design and Build an LOB application in Azure </span></span>](https://techcommunity.microsoft.com/t5/CAAB-Cloud-Adoption-Advisory/EXTRA-November-2016-Webinar/m-p/30058#M41)
    
## <a name="see-also"></a><span data-ttu-id="ade56-200">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ade56-200">See Also</span></span>

[<span data-ttu-id="ade56-201">Cloud ibrido Microsoft per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="ade56-201">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="ade56-202">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="ade56-202">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="ade56-203">Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT</span><span class="sxs-lookup"><span data-stu-id="ade56-203">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



