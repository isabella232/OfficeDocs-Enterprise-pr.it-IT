---
title: ExpressRoute per la connettività cloud Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/03/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: 'Riepilogo: Informazioni su come ExpressRoute grado di aiutarti con connessioni più veloci e affidabili a piattaforme e servizi cloud di Microsoft.'
ms.openlocfilehash: 1cd78372d37e40a53ba7725ff3653ef01daa48b0
ms.sourcegitcommit: 9da69a749ba557a4c4ae80070ce57e606148521f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "26525837"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a><span data-ttu-id="73e49-103">ExpressRoute per la connettività cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="73e49-103">ExpressRoute for Microsoft cloud connectivity</span></span>

 <span data-ttu-id="73e49-104">**Riepilogo:** Informazioni su come ExpressRoute grado di aiutarti con connessioni più veloci e affidabili a piattaforme e servizi cloud di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="73e49-104">**Summary:** Understand how ExpressRoute can help you with faster and more reliable connections to Microsoft's cloud services and platforms.</span></span>
  
<span data-ttu-id="73e49-105">ExpressRoute fornisce una connessione di rete a elevata velocità effettiva, dedicata e privata per il cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="73e49-105">ExpressRoute provides a private, dedicated, high-throughput network connection to Microsoft's cloud.</span></span>
  
## <a name="expressroute-to-the-microsoft-cloud"></a><span data-ttu-id="73e49-106">ExpressRoute nel cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="73e49-106">ExpressRoute to the Microsoft cloud</span></span>

<span data-ttu-id="73e49-107">Di seguito è il percorso di rete per il cloud Microsoft senza una connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="73e49-107">Here is the networking path to the Microsoft cloud without an ExpressRoute connection.</span></span>
  
<span data-ttu-id="73e49-108">**Figura 1: Il percorso di rete senza ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="73e49-108">**Figure 1: The networking path without ExpressRoute**</span></span>

![Figura 1: Il percorso di rete senza ExpressRoute](media/Network-Poster/ExpressRoute.png)
  
<span data-ttu-id="73e49-p101">Nella figura 1 viene visualizzato il percorso tipico tra una rete locali e cloud Microsoft. Perimetro della rete locale si connette a Internet tramite una rete WAN collegamento a un provider di servizi Internet. Il traffico passa quindi via Internet e il lato del cloud Microsoft. Offerte del cloud all'interno di Microsoft cloud includono Office 365, Microsoft Azure, Microsoft Intune e Dynamics 365. Gli utenti di un'organizzazione possono trovarsi nella rete locale o su Internet.</span><span class="sxs-lookup"><span data-stu-id="73e49-p101">Figure 1 shows the typical path between an on-premises network and the Microsoft cloud. The on-premises network edge connects to the Internet through a WAN link to an ISP. The traffic then travels across the Internet to the edge of the Microsoft cloud. Cloud offerings within the Microsoft cloud include Office 365, Microsoft Azure, Microsoft Intune, and Dynamics 365. Users of an organization can be located on the on-premises network or on the Internet.</span></span>
  
<span data-ttu-id="73e49-115">Senza una connessione ExpressRoute, l'unica parte del percorso del traffico da Microsoft cloud che consentono di controllare (e una relazione con il provider di servizi) è il collegamento tra il bordo di rete locale e provider di servizi Internet.</span><span class="sxs-lookup"><span data-stu-id="73e49-115">Without an ExpressRoute connection, the only part of the traffic path to the Microsoft cloud that you can control (and have a relationship with the service provider) is the link between your on-premises network edge and your ISP.</span></span> 
  
<span data-ttu-id="73e49-116">Il percorso tra provider di servizi Internet e il bordo di cloud Microsoft è un sistema di recapito sforzo su Internet soggetti a interruzioni, congestione del traffico e il monitoraggio da utenti malintenzionati.</span><span class="sxs-lookup"><span data-stu-id="73e49-116">The path between your ISP and the Microsoft cloud edge is a best-effort delivery system on the Internet subject to outages, traffic congestion, and monitoring by malicious users.</span></span>
  
<span data-ttu-id="73e49-117">Gli utenti su Internet, ad esempio gli utenti remoti o mobili, inviare traffico nel cloud Microsoft tramite Internet.</span><span class="sxs-lookup"><span data-stu-id="73e49-117">Users on the Internet, such as roaming or remote users, send their traffic to the Microsoft cloud over the Internet.</span></span>
  
<span data-ttu-id="73e49-118">Di seguito sono i percorsi di reti per il cloud Microsoft con una connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="73e49-118">Here are the networking paths to the Microsoft cloud with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="73e49-119">**Figura 2: I percorsi di rete senza ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="73e49-119">**Figure 2: The networking paths with ExpressRoute**</span></span>

![Figura 2: I percorsi di rete senza ExpressRoute](media/Network-Poster/ExpressRoute-post.png)
  
<span data-ttu-id="73e49-p102">Nella figura 2 sono riportati i due percorsi di reti. Il traffico a Microsoft Intune passa nello stesso percorso normale traffico Internet. Traffico a Office 365 e Azure Microsoft Dynamics 365 viaggia tra la connessione ExpressRoute, un percorso dedicato tra il bordo della rete locale e il bordo del cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="73e49-p102">Figure 2 shows two networking paths. Traffic to Microsoft Intune travels the same path as normal Internet traffic. Traffic to Office 365, Microsoft Azure, and Dynamics 365 travels across the ExpressRoute connection, a dedicated path between the edge of the on-premises network and the edge of the Microsoft cloud.</span></span>
  
<span data-ttu-id="73e49-p103">Con una connessione ExpressRoute, è ora dispongono del controllo tramite una relazione con il provider di servizi, sul percorso intero traffico tra il bordo di Microsoft cloud edge. La connessione può offrire prestazioni prevedibile e un [SLA uptime 99,95%](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span><span class="sxs-lookup"><span data-stu-id="73e49-p103">With an ExpressRoute connection, you now have control, through a relationship with your service provider, over the entire traffic path from your edge to the Microsoft cloud edge. This connection can offer predictable performance and a [99.95% uptime SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span></span>
  
<span data-ttu-id="73e49-p104">È ora possibile usufruire della prevedibile velocità effettiva e latenza, basata su connessione del provider di servizi, ai servizi di Office 365 e Azure Dynamics 365. Connessioni ExpressRoute a Microsoft Intune non sono supportate in questa fase.</span><span class="sxs-lookup"><span data-stu-id="73e49-p104">You can now count on predictable throughput and latency, based on your service provider's connection, to Office 365, Azure, and Dynamics 365 services. ExpressRoute connections to Microsoft Intune are not supported at this time.</span></span>
  
<span data-ttu-id="73e49-128">Il traffico inviato tramite la connessione ExpressRoute non è più soggetti a Internet interruzioni, congestione del traffico e monitoraggio.</span><span class="sxs-lookup"><span data-stu-id="73e49-128">Traffic sent over the ExpressRoute connection is no longer subject to Internet outages, traffic congestion, and monitoring.</span></span>
  
<span data-ttu-id="73e49-p105">Gli utenti su Internet, ad esempio gli utenti remoti o mobili, continuare a inviare traffico nel cloud Microsoft tramite Internet. Fa eccezione il traffico a una rete intranet applicazione line-of business ospitate in Azure IaaS, inviati tramite la connessione ExpressRoute mediante una connessione di accesso remoto alla rete locale.</span><span class="sxs-lookup"><span data-stu-id="73e49-p105">Users on the Internet, such as roaming or remote users, still send their traffic to the Microsoft cloud over the Internet. One exception is traffic to an intranet line of business application hosted in Azure IaaS, which is sent over the ExpressRoute connection via a remote access connection to the on-premises network.</span></span>
  
<span data-ttu-id="73e49-131">Anche con una connessione ExpressRoute, alcuni invio del traffico ancora su Internet, ad esempio le query DNS, controllo, elenco di revoche di certificati e le richieste di rete per la distribuzione del contenuto (CDN).</span><span class="sxs-lookup"><span data-stu-id="73e49-131">Even with an ExpressRoute connection, some traffic is still sent over the Internet, such as DNS queries, certificate revocation list checking, and content delivery network (CDN) requests.</span></span>
  
<span data-ttu-id="73e49-132">Vedere le risorse aggiuntive per ulteriori informazioni:</span><span class="sxs-lookup"><span data-stu-id="73e49-132">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="73e49-133">ExpressRoute per Office 365</span><span class="sxs-lookup"><span data-stu-id="73e49-133">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="73e49-134">ExpressRoute per Azure</span><span class="sxs-lookup"><span data-stu-id="73e49-134">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a><span data-ttu-id="73e49-135">Vantaggi della ExpressRoute per Azure</span><span class="sxs-lookup"><span data-stu-id="73e49-135">Advantages of ExpressRoute for Azure</span></span>

<span data-ttu-id="73e49-136">Ecco alcuni vantaggi derivanti dall'utilizzo ExpressRoute per i servizi cloud basati su Azure:</span><span class="sxs-lookup"><span data-stu-id="73e49-136">Here are some advantages of using ExpressRoute for Azure-based cloud services:</span></span>
  
- <span data-ttu-id="73e49-p106">**Prestazioni prevedibile:** Con un percorso e il lato del cloud Microsoft dedicato le prestazioni non sono legate interruzioni provider Internet e picchi di traffico Internet. È possibile determinare e includono i provider responsabile per una velocità effettiva e latenza SLA nel cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="73e49-p106">**Predictable performance:** With a dedicated path to the edge of the Microsoft cloud, your performance is not subject to Internet provider outages and spikes in Internet traffic. You can determine and hold your providers accountable to a throughput and latency SLA to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="73e49-p107">**La riservatezza dei dati per il traffico:** Il traffico inviato tramite la connessione ExpressRoute dedicata non è soggetta a Internet di monitoraggio o pacchetti acquisizione e l'analisi da utenti malintenzionati. Si tratta di sicurezza basato su Multiprotocol etichetta commutazione MPLS collegamenti WAN.</span><span class="sxs-lookup"><span data-stu-id="73e49-p107">**Data privacy for your traffic:** Traffic sent over your dedicated ExpressRoute connection is not subject to Internet monitoring or packet capture and analysis by malicious users. It is as secure as using Multiprotocol Label Switching (MPLS)-based WAN links.</span></span>
    
- <span data-ttu-id="73e49-141">**Connessioni ad alta velocità effettiva:** Con supporto esteso per le connessioni ExpressRoute dai provider di exchange e provider di servizi di rete, è possibile ottenere fino a 10 GB/s collegamento a Microsoft cloud.</span><span class="sxs-lookup"><span data-stu-id="73e49-141">**High throughput connections:** With wide support for ExpressRoute connections by exchange providers and network service providers, you can obtain up to a 10 Gbps link to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="73e49-142">**Ridurre i costi per alcune configurazioni:** Sebbene le connessioni ExpressRoute un costo aggiuntivo, in alcuni casi una singola connessione ExpressRoute può costi minore di aumentare la capacità di Internet da più posizioni dell'organizzazione per garantire velocità effettiva adeguata per servizi cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="73e49-142">**Lower cost for some configurations:** Although ExpressRoute connections are an additional cost, in some cases a single ExpressRoute connection can cost less than increasing your Internet capacity at multiple locations of your organization to provide adequate throughput to Microsoft cloud services.</span></span>
    
<span data-ttu-id="73e49-p108">Una connessione ExpressRoute non è una garanzia di prestazioni più elevate in tutte le configurazioni. È possibile disporre di riduzione delle prestazioni tramite una connessione ExpressRoute larghezza di banda ridotta di una connessione Internet ampia larghezza di banda solo alcuni passaggi un Data Center Microsoft regionali.</span><span class="sxs-lookup"><span data-stu-id="73e49-p108">An ExpressRoute connection is not a guarantee of higher performance in every configuration. It is possible to have lower performance over a low-bandwidth ExpressRoute connection than a high-bandwidth Internet connection that is only a few hops away from a regional Microsoft datacenter.</span></span>
  
<span data-ttu-id="73e49-145">Per i suggerimenti più recenti per l'utilizzo di ExpressRoute con Office 365, vedere [ExpressRoute per Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span><span class="sxs-lookup"><span data-stu-id="73e49-145">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
## <a name="expressroute-connectivity-models"></a><span data-ttu-id="73e49-146">Modelli di connettività ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="73e49-146">ExpressRoute connectivity models</span></span>

<span data-ttu-id="73e49-147">Tabella 1 sono indicati i tre modelli di connettività principale per le connessioni ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="73e49-147">Table 1 shows the three primary connectivity models for ExpressRoute connections.</span></span>
  
|<span data-ttu-id="73e49-148">**Percorso condiviso in un exchange cloud**</span><span class="sxs-lookup"><span data-stu-id="73e49-148">**Co-located at a cloud exchange**</span></span>|<span data-ttu-id="73e49-149">**Scheda Ethernet punto-punto**</span><span class="sxs-lookup"><span data-stu-id="73e49-149">**Point-to-point Ethernet**</span></span>|<span data-ttu-id="73e49-150">**Tutti a qualsiasi IP connessione VPN)**</span><span class="sxs-lookup"><span data-stu-id="73e49-150">**Any-to-any (IP VPN) connection**</span></span>|
|:-----|:-----|:-----|
|![Modello di connettività ExpressRoute: Percorso condiviso in un exchange cloud](media/Network-Poster/ER-Conn1.png)|![Modello di connettività ExpressRoute: Ethernet punto a punto](media/Network-Poster/ER-Conn2.png)|![Modello di connettività ExpressRoute: Connessione punto a punto (VPN IP)](media/Network-Poster/ER-Conn3.png)|
|<span data-ttu-id="73e49-154">Se i datacenter situati in una struttura con uno scambio cloud, è possibile ordinare una connessione tra virtuale nel cloud Microsoft tramite exchange Ethernet del provider posizione condivisa.</span><span class="sxs-lookup"><span data-stu-id="73e49-154">If your datacenter is co-located in a facility with a cloud exchange, you can order a virtual cross-connection to the Microsoft cloud through the co-location provider's Ethernet exchange.</span></span>  <br/> |<span data-ttu-id="73e49-155">Se il centro dati si trova il locale, è possibile utilizzare un collegamento di una scheda Ethernet da punto a punto per la connessione a Microsoft cloud.</span><span class="sxs-lookup"><span data-stu-id="73e49-155">If your datacenter is located on your premises, you can use a point-to-point Ethernet link to connect to the Microsoft cloud.</span></span>  <br/> |<span data-ttu-id="73e49-156">Se si utilizza già un provider di servizi VPN IP (MPLS) per connettere i siti dell'organizzazione, una connessione ExpressRoute nel cloud Microsoft funge da un'altra posizione sulla WAN privata.</span><span class="sxs-lookup"><span data-stu-id="73e49-156">If you are already using an IP VPN (MPLS) provider to connect the sites of your organization, an ExpressRoute connection to the Microsoft cloud acts like another location on your private WAN.</span></span>  <br/> |
   
 <span data-ttu-id="73e49-157">**Tabella 1: Modelli di connettività ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="73e49-157">**Table 1: ExpressRoute connectivity models**</span></span>
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a><span data-ttu-id="73e49-158">Relazioni di peering ExpressRoute ai servizi cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="73e49-158">ExpressRoute peering relationships to Microsoft cloud services</span></span>

<span data-ttu-id="73e49-p109">Una singola connessione ExpressRoute supporta fino a tre diverse Border Gateway Protocol (BGP) peering relazioni in diverse parti del cloud Microsoft. BPG utilizza peering relazioni per stabilire una relazione di trust e scambiare informazioni di routing.</span><span class="sxs-lookup"><span data-stu-id="73e49-p109">A single ExpressRoute connection supports up to three different Border Gateway Protocol (BGP) peering relationships to different parts of the Microsoft cloud. BPG uses peering relationships to establish trust and exchange routing information.</span></span>
  
<span data-ttu-id="73e49-161">**Figura 3: Le tre diverse relazioni BGP in una sola connessione ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="73e49-161">**Figure 3: The three different BGP relationships in a single ExpressRoute connection**</span></span>

![Figura 3: Le tre diverse relazioni BGP in una sola connessione ExpressRoute](media/Network-Poster/ERPeering.png)
  
<span data-ttu-id="73e49-p110">Nella figura 3 viene mostrata una connessione ExpressRoute da una rete locale. La connessione ExpressRoute ha tre relazioni peering logiche. Una relazione di peering Microsoft passerà a servizi SaaS Microsoft, tra cui Office 365 e Dynamcs CRM Online. Una relazione di peering pubblica passerà a servizi di Azure PaaS. Una relazione di peering privata passa per Azure IaaS e un gateway di rete virtuale che ospita le macchine virtuali.</span><span class="sxs-lookup"><span data-stu-id="73e49-p110">Figure 3 shows an ExpressRoute connection from an on-premises network. The ExpressRoute connection has three logical peering relationships. A Microsoft peering relationship goes to Microsoft SaaS services, including Office 365 and Dynamcs CRM Online. A public peering relationship goes to Azure PaaS services. A private peering relationship goes to Azure IaaS and to a virtual network gateway that hosts virtual machines.</span></span>
  
<span data-ttu-id="73e49-168">La relazione BGP peering Microsoft:</span><span class="sxs-lookup"><span data-stu-id="73e49-168">The Microsoft peering BGP relationship:</span></span> 
  
- <span data-ttu-id="73e49-169">Ha origine dal router la DMZ gli indirizzi pubblici di servizi di Office 365 e Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="73e49-169">Is from a router in your DMZ to the public addresses of Office 365 and Dynamics 365 services.</span></span> 
    
- <span data-ttu-id="73e49-170">Supporta le comunicazioni avviate bidirezionale.</span><span class="sxs-lookup"><span data-stu-id="73e49-170">Supports bidirectional-initiated communication.</span></span>
    
<span data-ttu-id="73e49-171">La relazione BGP peering pubblica:</span><span class="sxs-lookup"><span data-stu-id="73e49-171">The public peering BGP relationship:</span></span>
  
- <span data-ttu-id="73e49-172">È compreso un router la DMZ e gli indirizzi IP pubblici di servizi di Azure.</span><span class="sxs-lookup"><span data-stu-id="73e49-172">Is from a router in your DMZ to the public IP addresses of Azure services.</span></span>
    
- <span data-ttu-id="73e49-p111">Supporta la comunicazione unidirezionale avviate da solo sistemi locali. La relazione peering non supporta le comunicazioni avviate da servizi di Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="73e49-p111">Supports unidirectional-initiated communication from on-premises systems only. The peering relationship does not support communication initiated from Azure PaaS services.</span></span>
    
<span data-ttu-id="73e49-175">La relazione BGP peering privata:</span><span class="sxs-lookup"><span data-stu-id="73e49-175">The private peering BGP relationship:</span></span>
  
- <span data-ttu-id="73e49-176">È compreso un router nel bordo della rete dell'organizzazione e gli indirizzi IP privati assegnati per il VNets Azure.</span><span class="sxs-lookup"><span data-stu-id="73e49-176">Is from a router on the edge of your organization network to the private IP addresses assigned to your Azure VNets.</span></span>
    
- <span data-ttu-id="73e49-177">Supporta le comunicazioni avviate bidirezionale.</span><span class="sxs-lookup"><span data-stu-id="73e49-177">Supports bidirectional-initiated communication.</span></span>
    
- <span data-ttu-id="73e49-178">È un'estensione della rete dell'organizzazione per il cloud Microsoft, utilizzando l'indirizzamento internamente coerente e il routing.</span><span class="sxs-lookup"><span data-stu-id="73e49-178">Is an extension of your organization network to the Microsoft cloud, complete with internally-consistent addressing and routing.</span></span>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a><span data-ttu-id="73e49-179">Esempio di flusso di distribuzione e il traffico di applicazione con ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="73e49-179">Example of application deployment and traffic flow with ExpressRoute</span></span>

<span data-ttu-id="73e49-p112">Come si sposti il traffico tra le connessioni ExpressRoute e all'interno di Microsoft cloud è una funzione di route all'hop del percorso tra l'origine e il comportamento di destinazione e l'applicazione. Di seguito è riportato un esempio di un'applicazione in esecuzione in una macchina virtuale Azure che accede a una farm di SharePoint locali tramite una connessione VPN da sito.</span><span class="sxs-lookup"><span data-stu-id="73e49-p112">How traffic travels across ExpressRoute connections and within the Microsoft cloud is a function of the routes at the hops of the path between the source and the destination and application behavior. Here is an example of an application running on an Azure virtual machine that accesses an on-premises SharePoint farm over a site-to-site VPN connection.</span></span>
  
<span data-ttu-id="73e49-182">**Figura 4: Un'applicazione in una macchina virtuale Azure che accede a una farm locale di SharePoint**</span><span class="sxs-lookup"><span data-stu-id="73e49-182">**Figure 4: An application on an Azure virtual machine accessing an on-premises SharePoint farm**</span></span>

![Figura 4: Un'applicazione in una macchina virtuale Azure che accede a una farm locale di SharePoint](media/Network-Poster/ER-App-Flow1.png)

  
<span data-ttu-id="73e49-184">Figura 4 viene illustrato il flusso di una farm di SharePoint locale, una connessione VPN da sito tra la rete locale e una rete virtuale in Azure IaaS, un server applicazioni in esecuzione come una macchina virtuale Azure IaaS e il traffico tra il server applicazioni e farm di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="73e49-184">Figure 4 shows an on-premises SharePoint farm, a site-to-site VPN connection between the on-premises network and a virtual network in Azure IaaS, an application server running as an Azure IaaS virtual machine, and the traffic flow between the application server and the SharePoint farm.</span></span>
  
<span data-ttu-id="73e49-185">L'applicazione individua l'indirizzo IP della farm di SharePoint tramite il sistema DNS locale e tutto il traffico viene inoltrata tramite una connessione VPN da sito.</span><span class="sxs-lookup"><span data-stu-id="73e49-185">The application locates the IP address of the SharePoint farm using the on-premises DNS and all traffic goes over the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="73e49-186">L'organizzazione migrati le farm di SharePoint locale in SharePoint Online in Office 365 e distribuzione di una connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="73e49-186">This organization migrated their on-premises SharePoint farm to SharePoint Online in Office 365 and deployed an ExpressRoute connection.</span></span>
  
<span data-ttu-id="73e49-187">**Figura 5: Spostamento dalla farm locale SharePoint a SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="73e49-187">**Figure 5: Moving the on-premises SharePoint farm to SharePoint Online**</span></span>

![Figura 5: Spostamento dalla farm locale SharePoint a SharePoint Online](media/Network-Poster/Hairpin1.png)
  
<span data-ttu-id="73e49-p113">Figura 5 viene illustrata l'aggiunta di una connessione ExpressRoute con relazioni di peering per Microsoft SaaS e Office 365 e Azure IaaS contenente il server applicazioni in una rete virtuale. Farm di SharePoint locale è stata eseguita la migrazione a Office 365.</span><span class="sxs-lookup"><span data-stu-id="73e49-p113">Figure 5 shows the addition of an ExpressRoute connection with peering relationships to Microsoft SaaS and Office 365 and to Azure IaaS containing the application server on a virtual network. The SharePoint on-premises farm has been migrated to Office 365.</span></span>
  
<span data-ttu-id="73e49-191">Con Microsoft e relazioni peering private:</span><span class="sxs-lookup"><span data-stu-id="73e49-191">With the Microsoft and private peering relationships:</span></span>
  
- <span data-ttu-id="73e49-192">Dal gateway rete virtuale Azure percorsi locali riguardano disponibili mediante la connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="73e49-192">From the Azure virtual network gateway, on-premises locations are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="73e49-193">Dalla sottoscrizione di Office 365, indirizzi IP pubblici di dispositivi edge, ad esempio server proxy, riguardano disponibili mediante la connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="73e49-193">From the Office 365 subscription, public IP addresses of edge devices, such as proxy servers, are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="73e49-194">Dalla rete locale edge, gli indirizzi IP privati del VNet Azure e indirizzi IP pubblici di Office 365 sono disponibili tramite la connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="73e49-194">From the on-premises network edge, the private IP addresses of the Azure VNet and the public IP addresses of Office 365 are available across the ExpressRoute connection.</span></span>
    
<span data-ttu-id="73e49-195">Quando l'applicazione accede l'URL di SharePoint Online, inoltra il traffico tra la connessione ExpressRoute a un server proxy del bordo.</span><span class="sxs-lookup"><span data-stu-id="73e49-195">When the application accesses the URLs of SharePoint Online, it forwards its traffic across the ExpressRoute connection to a proxy server in the edge.</span></span> 
  
<span data-ttu-id="73e49-p114">Quando il server proxy individua l'indirizzo IP di SharePoint Online, inoltra il traffico back tramite la connessione ExpressRoute. Il traffico di risposta passa il percorso inverso.</span><span class="sxs-lookup"><span data-stu-id="73e49-p114">When the proxy server locates the IP address of SharePoint Online, it forwards the traffic back over the ExpressRoute connection. Response traffic travels the reverse path.</span></span>
  
<span data-ttu-id="73e49-198">**Figura 6: Flusso del traffico quando la farm di SharePoint è stata migrata a SharePoint Online in Office 365**</span><span class="sxs-lookup"><span data-stu-id="73e49-198">**Figure 6: Traffic flow when the SharePoint farm has been migrated to SharePoint Online in Office 365**</span></span>

![Figura 6: Flusso del traffico quando la farm di SharePoint è stata migrata a SharePoint Online in Office 365](media/Network-Poster/Hairpin2.png)

  
<span data-ttu-id="73e49-200">Figura 6 mostra come il traffico tra il server applicazioni e SharePoint Online in Office 365 copre la relazione di peering privata dal server applicazioni e il margine di rete locale e quindi dal bordo tramite la relazione peering Microsoft per Office 365.</span><span class="sxs-lookup"><span data-stu-id="73e49-200">Figure 6 shows how the traffic between the application server and SharePoint Online in Office 365 flows over the private peering relationship from the application server to the on-premises network edge, and then from the edge over the Microsoft peering relationship to Office 365.</span></span>
  
<span data-ttu-id="73e49-201">Il risultato è fini del blocco, una conseguenza del comportamento di routing e dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="73e49-201">The result is hair pinning, a consequence of the routing and application behavior.</span></span>
  
## <a name="expressroute-and-microsofts-cloud-network"></a><span data-ttu-id="73e49-202">Rete cloud ExpressRoute e di Microsoft</span><span class="sxs-lookup"><span data-stu-id="73e49-202">ExpressRoute and Microsoft's cloud network</span></span>

<span data-ttu-id="73e49-203">Sono disponibili in due versioni diverse connessioni ExpressRoute: ExpressRoute ed ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="73e49-203">ExpressRoute connections are available in two different versions: ExpressRoute and ExpressRoute Premium.</span></span>
  
### <a name="expressroute"></a><span data-ttu-id="73e49-204">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="73e49-204">ExpressRoute</span></span>

<span data-ttu-id="73e49-205">Come si sposti il traffico tra la rete dell'organizzazione e un database di Microsoft Data Center è una combinazione di:</span><span class="sxs-lookup"><span data-stu-id="73e49-205">How traffic travels between your organization network and a Microsoft datacenter is a combination of:</span></span>
  
- <span data-ttu-id="73e49-206">I percorsi.</span><span class="sxs-lookup"><span data-stu-id="73e49-206">Your locations.</span></span>
    
- <span data-ttu-id="73e49-207">Microsoft cloud peering percorsi (posizioni fisiche per la connessione e il lato Microsoft).</span><span class="sxs-lookup"><span data-stu-id="73e49-207">Microsoft cloud peering locations (the physical locations to connect to the Microsoft edge).</span></span>
    
- <span data-ttu-id="73e49-208">Posizioni dei data center Microsoft.</span><span class="sxs-lookup"><span data-stu-id="73e49-208">Microsoft datacenter locations.</span></span>
    
<span data-ttu-id="73e49-209">Data Center Microsoft e cloud peering percorsi sono connessi alla rete Microsoft cloud.</span><span class="sxs-lookup"><span data-stu-id="73e49-209">Microsoft datacenter and cloud peering locations are all connected to the Microsoft cloud network.</span></span>
  
<span data-ttu-id="73e49-p115">Quando si crea una connessione ExpressRoute in un percorso peering cloud Microsoft, si è connessi alla rete Microsoft cloud e tutti i percorsi di datacenter Microsoft continente stesso. Il traffico tra il percorso peering cloud e i data center Microsoft di destinazione viene eseguito tramite la rete di Microsoft cloud.</span><span class="sxs-lookup"><span data-stu-id="73e49-p115">When you create an ExpressRoute connection to a Microsoft cloud peering location, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="73e49-212">Ciò potrebbe causare recapito non ottimale di datacenter Microsoft locale per il modello a tutti per qualsiasi servizio di integrazione applicativa.</span><span class="sxs-lookup"><span data-stu-id="73e49-212">This can result in non-optimal delivery to local Microsoft datacenters for the any-to-any connectivity model.</span></span>
  
<span data-ttu-id="73e49-213">**Figura 7: Esempio di un'organizzazione geograficamente distribuiti che utilizza una sola connessione ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="73e49-213">**Figure 7: Example of a geographically-distributed organization that uses a single ExpressRoute connection**</span></span>

![Figura 7: Esempio di un'organizzazione geograficamente distribuiti che utilizza una sola connessione ExpressRoute](media/Network-Poster/MSNet1.png)
  
<span data-ttu-id="73e49-p116">Figura 7 mostra un'organizzazione con due percorsi 1 località in Nord-Ovest degli Stati Uniti e 2 posizione del nord-est. Sono connessi da un qualsiasi per qualsiasi provider WAN. L'organizzazione ha inoltre una connessione ExpressRoute in un percorso peering Microsoft costa occidentale. Il traffico proveniente da posizioni 2 in Nord-Est destinate a un datacenter costa orientale deve recarsi completamente WAN dell'organizzazione in costa occidentale del percorso peering Microsoft e quindi nuovamente in tutto il paese sulla rete cloud Microsoft per la zona est Data Center.</span><span class="sxs-lookup"><span data-stu-id="73e49-p116">Figure 7 shows an organization with two locations, Location 1 in the northwest of the United States and Location 2 in the northeast. They are connected by an any-to-any WAN provider. This organization also has an ExpressRoute connection to a Microsoft peering location on the west coast. Traffic from Location 2 in the northeast destined for an east coast datacenter must travel all the way across the organization's WAN to the west coast, to the Microsoft peering location, and then back across the country over the Microsoft cloud network to the east coast datacenter.</span></span>
  
<span data-ttu-id="73e49-219">Per il recapito ottimale, utilizzare più connessioni ExpressRoute per regionali Microsoft cloud peering percorsi.</span><span class="sxs-lookup"><span data-stu-id="73e49-219">For optimal delivery, use multiple ExpressRoute connections to regional Microsoft cloud peering locations.</span></span> 
  
<span data-ttu-id="73e49-220">**Figura 8: L’uso di più connessioni ExpressRoute per una consegna ottimale ai datacenter dell’area**</span><span class="sxs-lookup"><span data-stu-id="73e49-220">**Figure 8: The use of multiple ExpressRoute connections for optimal delivery to regional datacenters**</span></span>

![Figura 8: L’uso di più connessioni ExpressRoute per una consegna ottimale ai datacenter dell’area](media/Network-Poster/MSNet2.png)
  
<span data-ttu-id="73e49-p117">Figura 8 Mostra alla stessa organizzazione con due connessioni ExpressRoute, uno per ogni località nella regione locale posizioni peering Microsoft. In questa configurazione, il traffico proveniente da posizioni 2 in Nord-Est destinate a un datacenter costa orientale passa direttamente in una posizione peering costa orientale, alla rete cloud Microsoft e quindi al datacenter costa orientale.</span><span class="sxs-lookup"><span data-stu-id="73e49-p117">Figure 8 shows the same organization with two ExpressRoute connections, one for each location, to regionally local Microsoft peering locations. In this configuration, traffic from Location 2 in the northeast destined for an east coast datacenter goes directly to an east coast peering location, to the Microsoft cloud network, and then to the east coast datacenter.</span></span>
  
<span data-ttu-id="73e49-224">Possono inviare più connessioni ExpressRoute:</span><span class="sxs-lookup"><span data-stu-id="73e49-224">Multiple ExpressRoute connections can provide:</span></span>
  
- <span data-ttu-id="73e49-225">Migliorare le prestazioni di posizioni dei data center Microsoft nella regione locale.</span><span class="sxs-lookup"><span data-stu-id="73e49-225">Better performance to regionally local Microsoft datacenter locations.</span></span>
    
- <span data-ttu-id="73e49-226">Maggiore disponibilità per il cloud Microsoft quando non è disponibile una connessione ExpressRoute locale.</span><span class="sxs-lookup"><span data-stu-id="73e49-226">Higher availability to the Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="73e49-p118">Ciò vale per organizzazioni di continente stesso. Tuttavia, il traffico di datacenter Microsoft esterno continente dell'organizzazione passa tramite Internet.</span><span class="sxs-lookup"><span data-stu-id="73e49-p118">This works well for organizations in the same continent. However, traffic to Microsoft datacenters outside the organization's continent travels over the Internet.</span></span>
  
<span data-ttu-id="73e49-229">Per il traffico intercontinental sulla rete Microsoft cloud, è necessario utilizzare connessioni ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="73e49-229">For intercontinental traffic over the Microsoft cloud network, you must use ExpressRoute Premium connections.</span></span>
  
### <a name="expressroute-premium"></a><span data-ttu-id="73e49-230">ExpressRoute Premium</span><span class="sxs-lookup"><span data-stu-id="73e49-230">ExpressRoute Premium</span></span>

<span data-ttu-id="73e49-231">Per le organizzazioni che a livello globale vengono distribuite in continenti diversi, è possibile utilizzare ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="73e49-231">For organizations that are globally distributed across continents, you can use ExpressRoute Premium.</span></span> 
  
<span data-ttu-id="73e49-p119">Con ExpressRoute Premium, puoi raggiungere qualsiasi datacenter Microsoft in qualsiasi continente da qualsiasi posizione di peering Microsoft. Il traffico tra i continenti viene trasportato sulla rete cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="73e49-p119">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="73e49-234">Con più connessioni ExpressRoute Premium, è possibile disporre di:</span><span class="sxs-lookup"><span data-stu-id="73e49-234">With multiple ExpressRoute Premium connections, you can have:</span></span>
  
- <span data-ttu-id="73e49-235">Migliorare le prestazioni di datacenter Microsoft continentally locale.</span><span class="sxs-lookup"><span data-stu-id="73e49-235">Better performance to continentally local Microsoft datacenters.</span></span>
    
- <span data-ttu-id="73e49-236">Maggiore disponibilità per il cloud Microsoft globale quando non è disponibile una connessione ExpressRoute locale.</span><span class="sxs-lookup"><span data-stu-id="73e49-236">Higher availability to the global Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="73e49-p120">È necessario per le connessioni basate su Office 365 ExpressRoute ExpressRoute Premium. Non esiste tuttavia costi aggiuntivi per le grandi aziende con più concessa in licenza o 500 utenti.</span><span class="sxs-lookup"><span data-stu-id="73e49-p120">ExpressRoute Premium is required for Office 365-based ExpressRoute connections. However, there is no additional cost for enterprises with 500 or more licensed users.</span></span>
  
<span data-ttu-id="73e49-239">**Figura 9: Livello mondiale Microsoft cloud network**</span><span class="sxs-lookup"><span data-stu-id="73e49-239">**Figure 9: The world-wide Microsoft cloud network**</span></span>

![Figura 9: Rete mondiale Microsoft Cloud](media/Network-Poster/MSNet3.png)
  
<span data-ttu-id="73e49-p121">Figura 9 mostra un diagramma logico della rete mondiale Microsoft cloud, con le reti che includono il continenti e le aree di tutto il mondo e i collegamenti. Con una parte della rete Microsoft cloud in ogni continente, un'azienda globale crea ExpressRoute Premium connessioni sedi internazionali hub ai percorsi di peering Microsoft locali.</span><span class="sxs-lookup"><span data-stu-id="73e49-p121">Figure 9 shows a logical diagram of the worldwide Microsoft cloud network, with networks that span the continents and regions of the world and their interconnections. With a portion of the Microsoft cloud network in each continent, a global enterprise creates ExpressRoute Premium connections from its regional hub offices to local Microsoft peering locations.</span></span>
  
<span data-ttu-id="73e49-243">Per un ufficio regionale appropriato per il traffico di Office 365:</span><span class="sxs-lookup"><span data-stu-id="73e49-243">For a regional office, appropriate Office 365 traffic to:</span></span>
  
- <span data-ttu-id="73e49-244">Continentale datacenter di Office 365 passa attraverso la rete di Microsoft cloud all'interno di continente.</span><span class="sxs-lookup"><span data-stu-id="73e49-244">Continental Office 365 datacenters travels over the Microsoft cloud network within the continent.</span></span>
    
- <span data-ttu-id="73e49-245">Centri dati di Office 365 in un altro continente passa attraverso la rete cloud Microsoft intercontinental.</span><span class="sxs-lookup"><span data-stu-id="73e49-245">Office 365 datacenters in another continent travels over the intercontinental Microsoft cloud network.</span></span>
    
<span data-ttu-id="73e49-246">Per altre informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="73e49-246">For more information, see:</span></span>
  
- [<span data-ttu-id="73e49-247">ExpressRoute Azure per la formazione su Office 365</span><span class="sxs-lookup"><span data-stu-id="73e49-247">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="73e49-248">Pianificazione della rete e ottimizzazione delle prestazioni per Office 365</span><span class="sxs-lookup"><span data-stu-id="73e49-248">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)
    
- [<span data-ttu-id="73e49-249">Gestione delle prestazioni di Office 365</span><span class="sxs-lookup"><span data-stu-id="73e49-249">Office 365 Performance Management</span></span>](https://mva.microsoft.com/en-US/training-courses/office-365-performance-management-8416)
    
## <a name="expressroute-options"></a><span data-ttu-id="73e49-250">Opzioni ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="73e49-250">ExpressRoute options</span></span>

<span data-ttu-id="73e49-251">La distribuzione ExpressRoute inoltre è possibile incorporare le opzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="73e49-251">You can also incorporate the following options into your ExpressRoute deployment:</span></span>
  
- <span data-ttu-id="73e49-252">**Protezione in corrispondenza del bordo:** Per garantire la sicurezza avanzata per il traffico inviato e ricevuto tramite la connessione ExpressRoute, ad esempio l'ispezione di traffico o il rilevamento delle intrusioni/malware, effettuare le apparecchiature di sicurezza nel percorso di traffico all'interno del DMZ o il bordo della rete intranet.</span><span class="sxs-lookup"><span data-stu-id="73e49-252">**Security at your edge:** To provide advanced security for the traffic sent and received over the ExpressRoute connection, such as traffic inspection or intrusion/malware detection, place your security appliances in the traffic path within your DMZ or at the border of your intranet.</span></span>
    
    <span data-ttu-id="73e49-p122">Il traffico Internet per le macchine virtuali per impedire che si avvia il traffico direttamente con i percorsi Internet e macchine virtuali di Azure annunciare la route predefinita a Microsoft. Il traffico verso Internet viene instradato attraverso la connessione ExpressRoute e tramite i server proxy in locale. Il traffico proveniente da macchine virtuali Azure per Office 365 o i servizi di Azure PaaS viene instradato nuovamente attraverso la connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="73e49-p122">Internet traffic for VMs To prevent Azure VMs from initiating traffic directly with Internet locations, advertise the default route to Microsoft. Traffic to the Internet is routed across the ExpressRoute connection and through your on-premises proxy servers. Traffic from Azure VMs to Azure PaaS services or Office 365 is routed back across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="73e49-p123">**Ottimizzatori WAN:** È possibile distribuire ottimizzatori WAN su entrambi i lati di una connessione peering privata per un Azure cross-premise reti virtuali (VNet). All'interno di VNet Azure, utilizzare un dispositivo di rete WAN optimizer Azure marketplace e routing definite dall'utente per instradare il traffico attraverso il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="73e49-p123">**WAN optimizers:** You can deploy WAN optimizers on both sides of a private peering connection for a cross-premises Azure virtual network (VNet). Inside the Azure VNet, use a WAN optimizer network appliance from the Azure marketplace and user-defined routing to route the traffic through the appliance.</span></span>
    
- <span data-ttu-id="73e49-p124">**Qualità del servizio:** Utilizzare i valori DSCP Differentiated Services Code Point () nell'intestazione IPv4 parte del traffico per contrassegnare per VoIP, video/interattiva o sforzo recapito. Ciò è particolarmente importante per la relazione di peering Microsoft e Skype per il traffico Business Online.</span><span class="sxs-lookup"><span data-stu-id="73e49-p124">**Quality of service:** Use Differentiated Services Code Point (DSCP) values in the IPv4 header of your traffic to mark it for voice, video/interactive, or best-effort delivery. This is especially important for the Microsoft peering relationship and Skype for Business Online traffic.</span></span>
    
<span data-ttu-id="73e49-260">Vedere le risorse aggiuntive per ulteriori informazioni:</span><span class="sxs-lookup"><span data-stu-id="73e49-260">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="73e49-261">ExpressRoute per Office 365</span><span class="sxs-lookup"><span data-stu-id="73e49-261">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="73e49-262">ExpressRoute Azure per la formazione su Office 365</span><span class="sxs-lookup"><span data-stu-id="73e49-262">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="73e49-263">ExpressRoute per Azure</span><span class="sxs-lookup"><span data-stu-id="73e49-263">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a><span data-ttu-id="73e49-264">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="73e49-264">Next step</span></span>

[<span data-ttu-id="73e49-265">Progettazione di rete per Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="73e49-265">Designing networking for Microsoft SaaS</span></span>](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a><span data-ttu-id="73e49-266">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="73e49-266">See also</span></span>

[<span data-ttu-id="73e49-267">Rete di Microsoft Cloud per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="73e49-267">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="73e49-268">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="73e49-268">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="73e49-269">Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT</span><span class="sxs-lookup"><span data-stu-id="73e49-269">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



