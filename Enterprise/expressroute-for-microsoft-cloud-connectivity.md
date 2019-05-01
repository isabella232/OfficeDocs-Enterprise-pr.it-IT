---
title: ExpressRoute per la connettività cloud Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/12/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: 'Riepilogo: informazioni su come ExpressRoute può essere di aiuto con connessioni più veloci e affidabili ai servizi cloud e alle piattaforme Microsoft.'
ms.openlocfilehash: a3b36e98c946bc3ae7281bd38cd4b98820ee8afb
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2019
ms.locfileid: "33488144"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a><span data-ttu-id="223b8-103">ExpressRoute per la connettività cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="223b8-103">ExpressRoute for Microsoft cloud connectivity</span></span>

 <span data-ttu-id="223b8-104">**Riepilogo:** Informazioni su come ExpressRoute può essere di aiuto con connessioni più veloci e affidabili ai servizi cloud e alle piattaforme Microsoft.</span><span class="sxs-lookup"><span data-stu-id="223b8-104">**Summary:** Understand how ExpressRoute can help you with faster and more reliable connections to Microsoft's cloud services and platforms.</span></span>
  
<span data-ttu-id="223b8-105">ExpressRoute fornisce una connessione di rete a elevata velocità effettiva, dedicata e privata per il cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="223b8-105">ExpressRoute provides a private, dedicated, high-throughput network connection to Microsoft's cloud.</span></span>
  
## <a name="expressroute-to-the-microsoft-cloud"></a><span data-ttu-id="223b8-106">ExpressRoute al cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="223b8-106">ExpressRoute to the Microsoft cloud</span></span>

<span data-ttu-id="223b8-107">Di seguito è indicato il percorso di rete del cloud Microsoft senza una connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="223b8-107">Here is the networking path to the Microsoft cloud without an ExpressRoute connection.</span></span>
  
<span data-ttu-id="223b8-108">**Figura 1: percorso di rete senza ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="223b8-108">**Figure 1: The networking path without ExpressRoute**</span></span>

![Figura 1: percorso di rete senza ExpressRoute](media/Network-Poster/ExpressRoute.png)
  
<span data-ttu-id="223b8-110">Nella figura 1 viene illustrato il percorso tipico tra una rete locale e il cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="223b8-110">Figure 1 shows the typical path between an on-premises network and the Microsoft cloud.</span></span> <span data-ttu-id="223b8-111">Il server perimetrale di rete locale si connette a Internet tramite un collegamento WAN a un ISP.</span><span class="sxs-lookup"><span data-stu-id="223b8-111">The on-premises network edge connects to the Internet through a WAN link to an ISP.</span></span> <span data-ttu-id="223b8-112">Il traffico si sposta su Internet verso il bordo del cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="223b8-112">The traffic then travels across the Internet to the edge of the Microsoft cloud.</span></span> <span data-ttu-id="223b8-113">Le offerte cloud all'interno del cloud Microsoft includono Office 365, Microsoft Azure, Microsoft Intune e Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="223b8-113">Cloud offerings within the Microsoft cloud include Office 365, Microsoft Azure, Microsoft Intune, and Dynamics 365.</span></span> <span data-ttu-id="223b8-114">Gli utenti di un'organizzazione possono trovarsi nella rete locale o su Internet.</span><span class="sxs-lookup"><span data-stu-id="223b8-114">Users of an organization can be located on the on-premises network or on the Internet.</span></span>
  
<span data-ttu-id="223b8-115">Senza una connessione ExpressRoute, l'unica parte del percorso di traffico del cloud Microsoft che è possibile controllare (e avere una relazione con il provider di servizi) è il collegamento tra il server perimetrale di rete locale e l'ISP.</span><span class="sxs-lookup"><span data-stu-id="223b8-115">Without an ExpressRoute connection, the only part of the traffic path to the Microsoft cloud that you can control (and have a relationship with the service provider) is the link between your on-premises network edge and your ISP.</span></span> 
  
<span data-ttu-id="223b8-116">Il percorso tra l'ISP e Microsoft Cloud Edge è un sistema di distribuzione di Best-Effort su Internet soggetto a interruzioni, congestione del traffico e monitoraggio da parte di utenti malintenzionati.</span><span class="sxs-lookup"><span data-stu-id="223b8-116">The path between your ISP and the Microsoft cloud edge is a best-effort delivery system on the Internet subject to outages, traffic congestion, and monitoring by malicious users.</span></span>
  
<span data-ttu-id="223b8-117">Gli utenti su Internet, ad esempio il roaming o gli utenti remoti, inviano il traffico al cloud Microsoft su Internet.</span><span class="sxs-lookup"><span data-stu-id="223b8-117">Users on the Internet, such as roaming or remote users, send their traffic to the Microsoft cloud over the Internet.</span></span>
  
<span data-ttu-id="223b8-118">Di seguito sono disponibili i percorsi di rete di Microsoft Cloud con una connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="223b8-118">Here are the networking paths to the Microsoft cloud with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="223b8-119">**Figura 2: i percorsi di rete con ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="223b8-119">**Figure 2: The networking paths with ExpressRoute**</span></span>

![Figura 2: i percorsi di rete con ExpressRoute](media/Network-Poster/ExpressRoute-post.png)
  
<span data-ttu-id="223b8-121">Nella figura 2 sono illustrati due percorsi di rete.</span><span class="sxs-lookup"><span data-stu-id="223b8-121">Figure 2 shows two networking paths.</span></span> <span data-ttu-id="223b8-122">Il traffico verso Microsoft Intune percorre lo stesso percorso del normale traffico Internet.</span><span class="sxs-lookup"><span data-stu-id="223b8-122">Traffic to Microsoft Intune travels the same path as normal Internet traffic.</span></span> <span data-ttu-id="223b8-123">Il traffico verso Office 365, Microsoft Azure e Dynamics 365 attraversa la connessione ExpressRoute, un percorso dedicato tra il perimetro della rete locale e il perimetro del cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="223b8-123">Traffic to Office 365, Microsoft Azure, and Dynamics 365 travels across the ExpressRoute connection, a dedicated path between the edge of the on-premises network and the edge of the Microsoft cloud.</span></span>
  
<span data-ttu-id="223b8-124">Con una connessione ExpressRoute, è ora possibile controllare, tramite una relazione con il provider di servizi, l'intero percorso del traffico dal server perimetrale al bordo cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="223b8-124">With an ExpressRoute connection, you now have control, through a relationship with your service provider, over the entire traffic path from your edge to the Microsoft cloud edge.</span></span> <span data-ttu-id="223b8-125">Questa connessione può offrire prestazioni prevedibili e un [SLA di uptime del 99,95%](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span><span class="sxs-lookup"><span data-stu-id="223b8-125">This connection can offer predictable performance and a [99.95% uptime SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span></span>
  
<span data-ttu-id="223b8-126">È ora possibile contare sulla velocità effettiva e sulla latenza prevedibile, in base alla connessione del provider di servizi, ai servizi di Office 365, Azure e Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="223b8-126">You can now count on predictable throughput and latency, based on your service provider's connection, to Office 365, Azure, and Dynamics 365 services.</span></span> <span data-ttu-id="223b8-127">Le connessioni di ExpressRoute a Microsoft Intune non sono supportate in questo momento.</span><span class="sxs-lookup"><span data-stu-id="223b8-127">ExpressRoute connections to Microsoft Intune are not supported at this time.</span></span>
  
<span data-ttu-id="223b8-128">Il traffico inviato tramite la connessione ExpressRoute non è più soggetto a interruzioni Internet, alla congestione del traffico e al monitoraggio.</span><span class="sxs-lookup"><span data-stu-id="223b8-128">Traffic sent over the ExpressRoute connection is no longer subject to Internet outages, traffic congestion, and monitoring.</span></span>
  
<span data-ttu-id="223b8-129">Gli utenti su Internet, ad esempio il roaming o gli utenti remoti, continuano a inviare il traffico al cloud Microsoft su Internet.</span><span class="sxs-lookup"><span data-stu-id="223b8-129">Users on the Internet, such as roaming or remote users, still send their traffic to the Microsoft cloud over the Internet.</span></span> <span data-ttu-id="223b8-130">Un'eccezione è il traffico verso un'applicazione di linea Intranet di business ospitata in Azure IaaS, che viene inviata tramite la connessione ExpressRoute tramite una connessione di accesso remoto alla rete locale.</span><span class="sxs-lookup"><span data-stu-id="223b8-130">One exception is traffic to an intranet line of business application hosted in Azure IaaS, which is sent over the ExpressRoute connection via a remote access connection to the on-premises network.</span></span>
  
<span data-ttu-id="223b8-131">Anche se si dispone di una connessione ExpressRoute, viene comunque inviato tramite Internet, ad esempio query DNS, controllo dell'elenco di revoche di certificati e richieste della rete di distribuzione del contenuto (CDN, content deliverment Network).</span><span class="sxs-lookup"><span data-stu-id="223b8-131">Even with an ExpressRoute connection, some traffic is still sent over the Internet, such as DNS queries, certificate revocation list checking, and content delivery network (CDN) requests.</span></span>
  
<span data-ttu-id="223b8-132">Per ulteriori informazioni, vedere queste risorse aggiuntive:</span><span class="sxs-lookup"><span data-stu-id="223b8-132">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="223b8-133">ExpressRoute per Office 365</span><span class="sxs-lookup"><span data-stu-id="223b8-133">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="223b8-134">ExpressRoute per Azure</span><span class="sxs-lookup"><span data-stu-id="223b8-134">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a><span data-ttu-id="223b8-135">Vantaggi di ExpressRoute per Azure</span><span class="sxs-lookup"><span data-stu-id="223b8-135">Advantages of ExpressRoute for Azure</span></span>

<span data-ttu-id="223b8-136">Di seguito sono offerti alcuni vantaggi dell'utilizzo di ExpressRoute per i servizi cloud basati su Azure:</span><span class="sxs-lookup"><span data-stu-id="223b8-136">Here are some advantages of using ExpressRoute for Azure-based cloud services:</span></span>
  
- <span data-ttu-id="223b8-137">**Prestazioni prevedibili:** Con un percorso dedicato al server perimetrale di Microsoft Cloud, le prestazioni non sono soggette a interruzioni dei provider Internet e ai picchi del traffico Internet.</span><span class="sxs-lookup"><span data-stu-id="223b8-137">**Predictable performance:** With a dedicated path to the edge of the Microsoft cloud, your performance is not subject to Internet provider outages and spikes in Internet traffic.</span></span> <span data-ttu-id="223b8-138">È possibile determinare e mantenere i provider responsabili di una velocità effettiva e una latenza SLA nel cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="223b8-138">You can determine and hold your providers accountable to a throughput and latency SLA to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="223b8-139">**Privacy dei dati per il traffico:** Il traffico inviato tramite la connessione ExpressRoute dedicata non è soggetto a monitoraggio Internet o all'acquisizione e all'analisi di pacchetti da parte di utenti malintenzionati.</span><span class="sxs-lookup"><span data-stu-id="223b8-139">**Data privacy for your traffic:** Traffic sent over your dedicated ExpressRoute connection is not subject to Internet monitoring or packet capture and analysis by malicious users.</span></span> <span data-ttu-id="223b8-140">È sicura come l'utilizzo dei collegamenti WAN basati su Multiprotocol Label Switching (MPLS).</span><span class="sxs-lookup"><span data-stu-id="223b8-140">It is as secure as using Multiprotocol Label Switching (MPLS)-based WAN links.</span></span>
    
- <span data-ttu-id="223b8-141">**Connessioni a velocità elevata:** Con un ampio supporto per le connessioni di ExpressRoute da parte di provider di Exchange e provider di servizi di rete, è possibile ottenere fino a un collegamento a 10 Gbps per il cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="223b8-141">**High throughput connections:** With wide support for ExpressRoute connections by exchange providers and network service providers, you can obtain up to a 10 Gbps link to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="223b8-142">**Riduzione dei costi per alcune configurazioni:** Anche se le connessioni di ExpressRoute sono un costo aggiuntivo, in alcuni casi una singola connessione ExpressRoute può costare meno che aumentare la capacità Internet in più posizioni dell'organizzazione per fornire una velocità effettiva ai servizi cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="223b8-142">**Lower cost for some configurations:** Although ExpressRoute connections are an additional cost, in some cases a single ExpressRoute connection can cost less than increasing your Internet capacity at multiple locations of your organization to provide adequate throughput to Microsoft cloud services.</span></span>
    
<span data-ttu-id="223b8-143">Una connessione di ExpressRoute non garantisce prestazioni superiori in ogni configurazione.</span><span class="sxs-lookup"><span data-stu-id="223b8-143">An ExpressRoute connection is not a guarantee of higher performance in every configuration.</span></span> <span data-ttu-id="223b8-144">È possibile avere prestazioni più basse rispetto a una connessione ExpressRoute con larghezza di banda ridotta rispetto a una connessione Internet a larghezza di banda elevata che dista solo pochi passaggi da un datacenter Microsoft regionale.</span><span class="sxs-lookup"><span data-stu-id="223b8-144">It is possible to have lower performance over a low-bandwidth ExpressRoute connection than a high-bandwidth Internet connection that is only a few hops away from a regional Microsoft datacenter.</span></span>
  
<span data-ttu-id="223b8-145">Per i suggerimenti più recenti per l'utilizzo di ExpressRoute con Office 365, vedere [ExpressRoute per office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span><span class="sxs-lookup"><span data-stu-id="223b8-145">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
## <a name="expressroute-connectivity-models"></a><span data-ttu-id="223b8-146">Modelli di connettività di ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="223b8-146">ExpressRoute connectivity models</span></span>

<span data-ttu-id="223b8-147">Nella tabella 1 sono riportati i tre modelli di connettività principali per le connessioni di ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="223b8-147">Table 1 shows the three primary connectivity models for ExpressRoute connections.</span></span>
  
|<span data-ttu-id="223b8-148">**Percorso condiviso in un exchange cloud**</span><span class="sxs-lookup"><span data-stu-id="223b8-148">**Co-located at a cloud exchange**</span></span>|<span data-ttu-id="223b8-149">**Ethernet Point-to-Point**</span><span class="sxs-lookup"><span data-stu-id="223b8-149">**Point-to-point Ethernet**</span></span>|<span data-ttu-id="223b8-150">**Connessione any-to-any (VPN IP)**</span><span class="sxs-lookup"><span data-stu-id="223b8-150">**Any-to-any (IP VPN) connection**</span></span>|
|:-----|:-----|:-----|
|![Modello di connettività ExpressRoute: si trova in un Exchange cloud](media/Network-Poster/ER-Conn1.png)|![Modello di connettività ExpressRoute: Ethernet Point-to-Point](media/Network-Poster/ER-Conn2.png)|![Modello di connettività ExpressRoute: connessione any-to-any (VPN IP)](media/Network-Poster/ER-Conn3.png)|
|<span data-ttu-id="223b8-154">Se il Data Center è posizionato in una struttura con un cloud Exchange, è possibile ordinare una connessione incrociata virtuale a Microsoft Cloud tramite lo scambio Ethernet del provider di co-location.</span><span class="sxs-lookup"><span data-stu-id="223b8-154">If your datacenter is co-located in a facility with a cloud exchange, you can order a virtual cross-connection to the Microsoft cloud through the co-location provider's Ethernet exchange.</span></span>  <br/> |<span data-ttu-id="223b8-155">Se il Data Center si trova nella propria sede, è possibile utilizzare un collegamento Ethernet Point-to-Point per la connessione al cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="223b8-155">If your datacenter is located on your premises, you can use a point-to-point Ethernet link to connect to the Microsoft cloud.</span></span>  <br/> |<span data-ttu-id="223b8-156">Se si sta già utilizzando un provider IP VPN (MPLS) per connettere i siti dell'organizzazione, una connessione ExpressRoute al cloud Microsoft agisce come un'altra posizione sulla WAN privata.</span><span class="sxs-lookup"><span data-stu-id="223b8-156">If you are already using an IP VPN (MPLS) provider to connect the sites of your organization, an ExpressRoute connection to the Microsoft cloud acts like another location on your private WAN.</span></span>  <br/> |
   
 <span data-ttu-id="223b8-157">**Tabella 1: modelli di connettività di ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="223b8-157">**Table 1: ExpressRoute connectivity models**</span></span>
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a><span data-ttu-id="223b8-158">Relazioni di peering di ExpressRoute con i servizi cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="223b8-158">ExpressRoute peering relationships to Microsoft cloud services</span></span>

<span data-ttu-id="223b8-159">Una singola connessione di ExpressRoute supporta fino a due diverse relazioni di peering del protocollo del gateway di Border (BGP) a diverse parti del cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="223b8-159">A single ExpressRoute connection supports up to two different Border Gateway Protocol (BGP) peering relationships to different parts of the Microsoft cloud.</span></span> <span data-ttu-id="223b8-160">BPG utilizza relazioni di peering per stabilire informazioni di routing di attendibilità e di Exchange.</span><span class="sxs-lookup"><span data-stu-id="223b8-160">BPG uses peering relationships to establish trust and exchange routing information.</span></span>
  
<span data-ttu-id="223b8-161">**Figura 3: le due diverse relazioni BGP in una singola connessione di ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="223b8-161">**Figure 3: The two different BGP relationships in a single ExpressRoute connection**</span></span>

![Figura 3: le due diverse relazioni BGP in una singola connessione di ExpressRoute](media/Network-Poster/ERPeering.png)
  
<span data-ttu-id="223b8-163">Nella figura 3 viene illustrata una connessione ExpressRoute da una rete locale.</span><span class="sxs-lookup"><span data-stu-id="223b8-163">Figure 3 shows an ExpressRoute connection from an on-premises network.</span></span> <span data-ttu-id="223b8-164">La connessione ExpressRoute dispone di due relazioni di peering logiche.</span><span class="sxs-lookup"><span data-stu-id="223b8-164">The ExpressRoute connection has two logical peering relationships.</span></span> <span data-ttu-id="223b8-165">Una relazione di peering Microsoft si collega ai servizi SaaS di Microsoft, tra cui Office 365, DYNAMCS 365 e Azure PaaS Services.</span><span class="sxs-lookup"><span data-stu-id="223b8-165">A Microsoft peering relationship goes to Microsoft SaaS services, including Office 365, Dynamcs 365, and Azure PaaS services.</span></span> <span data-ttu-id="223b8-166">Una relazione di peering privata passa a Azure IaaS e a un gateway di rete virtuale che ospita macchine virtuali.</span><span class="sxs-lookup"><span data-stu-id="223b8-166">A private peering relationship goes to Azure IaaS and to a virtual network gateway that hosts virtual machines.</span></span>
  
<span data-ttu-id="223b8-167">La relazione Microsoft peering BGP:</span><span class="sxs-lookup"><span data-stu-id="223b8-167">The Microsoft peering BGP relationship:</span></span> 
  
- <span data-ttu-id="223b8-168">È da un router della DMZ agli indirizzi pubblici di Office 365, Dynamics 365 e Azure Services.</span><span class="sxs-lookup"><span data-stu-id="223b8-168">Is from a router in your DMZ to the public addresses of Office 365, Dynamics 365, and Azure services.</span></span> 
    
- <span data-ttu-id="223b8-169">Supporta la comunicazione con avvio bidirezionale.</span><span class="sxs-lookup"><span data-stu-id="223b8-169">Supports bidirectional-initiated communication.</span></span>
    
<span data-ttu-id="223b8-170">La relazione privata di peering BGP:</span><span class="sxs-lookup"><span data-stu-id="223b8-170">The private peering BGP relationship:</span></span>
  
- <span data-ttu-id="223b8-171">È da un router sul bordo della rete dell'organizzazione agli indirizzi IP privati assegnati alla reti virtuali di Azure.</span><span class="sxs-lookup"><span data-stu-id="223b8-171">Is from a router on the edge of your organization network to the private IP addresses assigned to your Azure VNets.</span></span>
    
- <span data-ttu-id="223b8-172">Supporta la comunicazione con avvio bidirezionale.</span><span class="sxs-lookup"><span data-stu-id="223b8-172">Supports bidirectional-initiated communication.</span></span>
    
- <span data-ttu-id="223b8-173">È un'estensione della rete dell'organizzazione al cloud Microsoft, con indirizzamento e routing coerenti internamente.</span><span class="sxs-lookup"><span data-stu-id="223b8-173">Is an extension of your organization network to the Microsoft cloud, complete with internally-consistent addressing and routing.</span></span>

>[!Note]
><span data-ttu-id="223b8-174">La relazione pubblica di peering BGP descritta nelle versioni precedenti di questo articolo è obsoleta.</span><span class="sxs-lookup"><span data-stu-id="223b8-174">The public peering BGP relationship described in previous versions of this article has been deprecated.</span></span>
>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a><span data-ttu-id="223b8-175">Esempio di distribuzione di applicazioni e flusso di traffico con ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="223b8-175">Example of application deployment and traffic flow with ExpressRoute</span></span>

<span data-ttu-id="223b8-176">La modalità di spostamento del traffico tra le connessioni di ExpressRoute e all'interno del cloud Microsoft è una funzione delle route in corrispondenza del luppolo del percorso tra il comportamento di origine e di destinazione e l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="223b8-176">How traffic travels across ExpressRoute connections and within the Microsoft cloud is a function of the routes at the hops of the path between the source and the destination and application behavior.</span></span> <span data-ttu-id="223b8-177">Di seguito è riportato un esempio di un'applicazione in esecuzione su una macchina virtuale di Azure che accede a una farm di SharePoint locale tramite una connessione VPN da sito a sito.</span><span class="sxs-lookup"><span data-stu-id="223b8-177">Here is an example of an application running on an Azure virtual machine that accesses an on-premises SharePoint farm over a site-to-site VPN connection.</span></span>
  
<span data-ttu-id="223b8-178">**Figura 4: un'applicazione in una macchina virtuale di Azure che accede a una farm di SharePoint locale**</span><span class="sxs-lookup"><span data-stu-id="223b8-178">**Figure 4: An application on an Azure virtual machine accessing an on-premises SharePoint farm**</span></span>

![Figura 4: un'applicazione in una macchina virtuale di Azure che accede a una farm di SharePoint locale](media/Network-Poster/ER-App-Flow1.png)

  
<span data-ttu-id="223b8-180">Nella figura 4 viene illustrata una farm di SharePoint locale, una connessione VPN da sito a sito tra la rete locale e una rete virtuale in Azure IaaS, un server applicazioni in esecuzione come una macchina virtuale IaaS di Azure e il flusso di traffico tra il server applicazioni e farm di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="223b8-180">Figure 4 shows an on-premises SharePoint farm, a site-to-site VPN connection between the on-premises network and a virtual network in Azure IaaS, an application server running as an Azure IaaS virtual machine, and the traffic flow between the application server and the SharePoint farm.</span></span>
  
<span data-ttu-id="223b8-181">L'applicazione individua l'indirizzo IP della farm di SharePoint utilizzando il DNS locale e tutto il traffico supera la connessione VPN da sito a sito.</span><span class="sxs-lookup"><span data-stu-id="223b8-181">The application locates the IP address of the SharePoint farm using the on-premises DNS and all traffic goes over the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="223b8-182">Questa organizzazione ha eseguito la migrazione della farm di SharePoint locale a SharePoint online in Office 365 e ha distribuito una connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="223b8-182">This organization migrated their on-premises SharePoint farm to SharePoint Online in Office 365 and deployed an ExpressRoute connection.</span></span>
  
<span data-ttu-id="223b8-183">**Figura 5: spostamento della farm di SharePoint locale in SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="223b8-183">**Figure 5: Moving the on-premises SharePoint farm to SharePoint Online**</span></span>

![Figura 5: spostamento della farm di SharePoint locale in SharePoint Online](media/Network-Poster/Hairpin1.png)
  
<span data-ttu-id="223b8-185">Nella figura 5 è illustrata l'aggiunta di una connessione ExpressRoute con relazioni di peering a Microsoft SaaS e Office 365 e a Azure IaaS contenente il server applicazioni in una rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="223b8-185">Figure 5 shows the addition of an ExpressRoute connection with peering relationships to Microsoft SaaS and Office 365 and to Azure IaaS containing the application server on a virtual network.</span></span> <span data-ttu-id="223b8-186">La farm di SharePoint locale è stata migrata a Office 365.</span><span class="sxs-lookup"><span data-stu-id="223b8-186">The SharePoint on-premises farm has been migrated to Office 365.</span></span>
  
<span data-ttu-id="223b8-187">Con le relazioni di peering Microsoft e private:</span><span class="sxs-lookup"><span data-stu-id="223b8-187">With the Microsoft and private peering relationships:</span></span>
  
- <span data-ttu-id="223b8-188">Dal gateway di rete virtuale di Azure, le posizioni locali sono disponibili in tutta la connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="223b8-188">From the Azure virtual network gateway, on-premises locations are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="223b8-189">Dall'abbonamento a Office 365, gli indirizzi IP pubblici dei dispositivi perimetrali, ad esempio i server proxy, sono disponibili nella connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="223b8-189">From the Office 365 subscription, public IP addresses of edge devices, such as proxy servers, are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="223b8-190">Dal server perimetrale di rete locale, gli indirizzi IP privati dei rete virtuale di Azure e gli indirizzi IP pubblici di Office 365 sono disponibili nella connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="223b8-190">From the on-premises network edge, the private IP addresses of the Azure VNet and the public IP addresses of Office 365 are available across the ExpressRoute connection.</span></span>
    
<span data-ttu-id="223b8-191">Quando l'applicazione accede agli URL di SharePoint Online, inoltra il traffico attraverso la connessione ExpressRoute a un server proxy nel perimetro.</span><span class="sxs-lookup"><span data-stu-id="223b8-191">When the application accesses the URLs of SharePoint Online, it forwards its traffic across the ExpressRoute connection to a proxy server in the edge.</span></span> 
  
<span data-ttu-id="223b8-192">Quando il server proxy individua l'indirizzo IP di SharePoint Online, inoltra il traffico sulla connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="223b8-192">When the proxy server locates the IP address of SharePoint Online, it forwards the traffic back over the ExpressRoute connection.</span></span> <span data-ttu-id="223b8-193">Il traffico di risposta percorre il percorso inverso.</span><span class="sxs-lookup"><span data-stu-id="223b8-193">Response traffic travels the reverse path.</span></span>
  
<span data-ttu-id="223b8-194">**Figura 6: flusso di traffico quando la farm di SharePoint è stata migrata a SharePoint online in Office 365**</span><span class="sxs-lookup"><span data-stu-id="223b8-194">**Figure 6: Traffic flow when the SharePoint farm has been migrated to SharePoint Online in Office 365**</span></span>

![Figura 6: flusso di traffico quando la farm di SharePoint è stata migrata a SharePoint online in Office 365](media/Network-Poster/Hairpin2.png)

  
<span data-ttu-id="223b8-196">Nella figura 6 viene illustrato il flusso del traffico tra il server applicazioni e SharePoint online in Office 365 sulla relazione privata di peering tra il server applicazioni e il perimetro di rete locale e quindi dal bordo della relazione di peering Microsoft a Office 365.</span><span class="sxs-lookup"><span data-stu-id="223b8-196">Figure 6 shows how the traffic between the application server and SharePoint Online in Office 365 flows over the private peering relationship from the application server to the on-premises network edge, and then from the edge over the Microsoft peering relationship to Office 365.</span></span>
  
<span data-ttu-id="223b8-197">Il risultato è il pinning dei capelli, una conseguenza del comportamento dell'applicazione e del routing.</span><span class="sxs-lookup"><span data-stu-id="223b8-197">The result is hair pinning, a consequence of the routing and application behavior.</span></span>
  
## <a name="expressroute-and-microsofts-cloud-network"></a><span data-ttu-id="223b8-198">ExpressRoute e la rete cloud di Microsoft</span><span class="sxs-lookup"><span data-stu-id="223b8-198">ExpressRoute and Microsoft's cloud network</span></span>

<span data-ttu-id="223b8-199">Le connessioni di ExpressRoute sono disponibili in due versioni diverse: ExpressRoute e ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="223b8-199">ExpressRoute connections are available in two different versions: ExpressRoute and ExpressRoute Premium.</span></span>
  
### <a name="expressroute"></a><span data-ttu-id="223b8-200">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="223b8-200">ExpressRoute</span></span>

<span data-ttu-id="223b8-201">La modalità di spostamento del traffico tra la rete dell'organizzazione e un datacenter Microsoft è una combinazione di:</span><span class="sxs-lookup"><span data-stu-id="223b8-201">How traffic travels between your organization network and a Microsoft datacenter is a combination of:</span></span>
  
- <span data-ttu-id="223b8-202">Posizioni.</span><span class="sxs-lookup"><span data-stu-id="223b8-202">Your locations.</span></span>
    
- <span data-ttu-id="223b8-203">Microsoft Cloud peering locations (le posizioni fisiche per la connessione a Microsoft Edge).</span><span class="sxs-lookup"><span data-stu-id="223b8-203">Microsoft cloud peering locations (the physical locations to connect to the Microsoft edge).</span></span>
    
- <span data-ttu-id="223b8-204">Posizioni del datacenter Microsoft.</span><span class="sxs-lookup"><span data-stu-id="223b8-204">Microsoft datacenter locations.</span></span>
    
<span data-ttu-id="223b8-205">Microsoft datacenter e cloud peering locations sono tutti connessi alla rete cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="223b8-205">Microsoft datacenter and cloud peering locations are all connected to the Microsoft cloud network.</span></span>
  
<span data-ttu-id="223b8-206">Quando si crea una connessione ExpressRoute a un percorso peering di Microsoft Cloud, si è connessi alla rete cloud Microsoft e a tutte le posizioni del datacenter Microsoft nello stesso continente.</span><span class="sxs-lookup"><span data-stu-id="223b8-206">When you create an ExpressRoute connection to a Microsoft cloud peering location, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent.</span></span> <span data-ttu-id="223b8-207">Il traffico tra il percorso di peering cloud e il datacenter di destinazione Microsoft viene eseguito tramite la rete cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="223b8-207">The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="223b8-208">Questo può comportare un recapito non ottimale ai datacenter locali Microsoft per il modello di connettività any-to-any.</span><span class="sxs-lookup"><span data-stu-id="223b8-208">This can result in non-optimal delivery to local Microsoft datacenters for the any-to-any connectivity model.</span></span>
  
<span data-ttu-id="223b8-209">**Figura 7: esempio di un'organizzazione geograficamente distribuita che utilizza una singola connessione di ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="223b8-209">**Figure 7: Example of a geographically-distributed organization that uses a single ExpressRoute connection**</span></span>

![Figura 7: esempio di un'organizzazione geograficamente distribuita che utilizza una singola connessione di ExpressRoute](media/Network-Poster/MSNet1.png)
  
<span data-ttu-id="223b8-211">Nella figura 7 è illustrata un'organizzazione con due posizioni, la posizione 1 nel nord-ovest degli Stati Uniti e la posizione 2 nel nordest.</span><span class="sxs-lookup"><span data-stu-id="223b8-211">Figure 7 shows an organization with two locations, Location 1 in the northwest of the United States and Location 2 in the northeast.</span></span> <span data-ttu-id="223b8-212">Sono connessi da un provider WAN any-to-any.</span><span class="sxs-lookup"><span data-stu-id="223b8-212">They are connected by an any-to-any WAN provider.</span></span> <span data-ttu-id="223b8-213">Questa organizzazione dispone anche di una connessione ExpressRoute a una posizione peering Microsoft sulla West Coast.</span><span class="sxs-lookup"><span data-stu-id="223b8-213">This organization also has an ExpressRoute connection to a Microsoft peering location on the west coast.</span></span> <span data-ttu-id="223b8-214">Il traffico proveniente dalla posizione 2 nel nordest destinato a un centro dati della costa est deve attraversare la WAN dell'organizzazione fino alla costa occidentale, alla posizione di peering Microsoft e quindi di nuovo in tutto il paese tramite la rete cloud Microsoft fino alla costa orientale Datacenter.</span><span class="sxs-lookup"><span data-stu-id="223b8-214">Traffic from Location 2 in the northeast destined for an east coast datacenter must travel all the way across the organization's WAN to the west coast, to the Microsoft peering location, and then back across the country over the Microsoft cloud network to the east coast datacenter.</span></span>
  
<span data-ttu-id="223b8-215">Per il recapito ottimale, utilizzare più connessioni di ExpressRoute a posizioni peering di Microsoft Cloud regionali.</span><span class="sxs-lookup"><span data-stu-id="223b8-215">For optimal delivery, use multiple ExpressRoute connections to regional Microsoft cloud peering locations.</span></span> 
  
<span data-ttu-id="223b8-216">**Figura 8: l'utilizzo di più connessioni ExpressRoute per il recapito ottimale ai datacenter regionali**</span><span class="sxs-lookup"><span data-stu-id="223b8-216">**Figure 8: The use of multiple ExpressRoute connections for optimal delivery to regional datacenters**</span></span>

![Figura 8: l'utilizzo di più connessioni ExpressRoute per il recapito ottimale ai datacenter regionali](media/Network-Poster/MSNet2.png)
  
<span data-ttu-id="223b8-218">Nella figura 8 viene illustrata la stessa organizzazione con due connessioni ExpressRoute, una per ogni posizione, per le posizioni peering locali di Microsoft regionalmente.</span><span class="sxs-lookup"><span data-stu-id="223b8-218">Figure 8 shows the same organization with two ExpressRoute connections, one for each location, to regionally local Microsoft peering locations.</span></span> <span data-ttu-id="223b8-219">In questa configurazione, il traffico proveniente dalla posizione 2 nel nordest destinato a un datacenter della costa est passa direttamente a una posizione peering della costa orientale, alla rete cloud Microsoft e quindi al datacenter della East Coast.</span><span class="sxs-lookup"><span data-stu-id="223b8-219">In this configuration, traffic from Location 2 in the northeast destined for an east coast datacenter goes directly to an east coast peering location, to the Microsoft cloud network, and then to the east coast datacenter.</span></span>
  
<span data-ttu-id="223b8-220">Per le connessioni a più ExpressRoute è possibile specificare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="223b8-220">Multiple ExpressRoute connections can provide:</span></span>
  
- <span data-ttu-id="223b8-221">Migliorare le prestazioni per le posizioni locali del datacenter Microsoft.</span><span class="sxs-lookup"><span data-stu-id="223b8-221">Better performance to regionally local Microsoft datacenter locations.</span></span>
    
- <span data-ttu-id="223b8-222">Maggiore disponibilità al cloud Microsoft quando una connessione ExpressRoute locale non è disponibile.</span><span class="sxs-lookup"><span data-stu-id="223b8-222">Higher availability to the Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="223b8-223">Questo funziona bene per le organizzazioni dello stesso continente.</span><span class="sxs-lookup"><span data-stu-id="223b8-223">This works well for organizations in the same continent.</span></span> <span data-ttu-id="223b8-224">Tuttavia, il traffico verso i centri dati Microsoft al di fuori del continente dell'organizzazione viaggia su Internet.</span><span class="sxs-lookup"><span data-stu-id="223b8-224">However, traffic to Microsoft datacenters outside the organization's continent travels over the Internet.</span></span>
  
<span data-ttu-id="223b8-225">Per il traffico intercontinentale sulla rete cloud Microsoft, è necessario utilizzare le connessioni Premium di ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="223b8-225">For intercontinental traffic over the Microsoft cloud network, you must use ExpressRoute Premium connections.</span></span>
  
### <a name="expressroute-premium"></a><span data-ttu-id="223b8-226">ExpressRoute Premium</span><span class="sxs-lookup"><span data-stu-id="223b8-226">ExpressRoute Premium</span></span>

<span data-ttu-id="223b8-227">Per le organizzazioni distribuite a livello globale in tutti i continenti, è possibile utilizzare ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="223b8-227">For organizations that are globally distributed across continents, you can use ExpressRoute Premium.</span></span> 
  
<span data-ttu-id="223b8-p118">Con ExpressRoute Premium, puoi raggiungere qualsiasi datacenter Microsoft in qualsiasi continente da qualsiasi posizione di peering Microsoft. Il traffico tra i continenti viene trasportato sulla rete cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="223b8-p118">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="223b8-230">Con più connessioni Premium di ExpressRoute, è possibile disporre di:</span><span class="sxs-lookup"><span data-stu-id="223b8-230">With multiple ExpressRoute Premium connections, you can have:</span></span>
  
- <span data-ttu-id="223b8-231">Prestazioni migliori per i datacenter Microsoft locali.</span><span class="sxs-lookup"><span data-stu-id="223b8-231">Better performance to continentally local Microsoft datacenters.</span></span>
    
- <span data-ttu-id="223b8-232">Maggiore disponibilità al cloud globale di Microsoft quando una connessione ExpressRoute locale non è disponibile.</span><span class="sxs-lookup"><span data-stu-id="223b8-232">Higher availability to the global Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="223b8-233">ExpressRoute Premium è necessario per le connessioni ExpressRoute basate su Office 365.</span><span class="sxs-lookup"><span data-stu-id="223b8-233">ExpressRoute Premium is required for Office 365-based ExpressRoute connections.</span></span>
  
<span data-ttu-id="223b8-234">**Figura 9: la rete cloud Microsoft in tutto il mondo**</span><span class="sxs-lookup"><span data-stu-id="223b8-234">**Figure 9: The world-wide Microsoft cloud network**</span></span>

![Figura 9: la rete cloud Microsoft in tutto il mondo](media/Network-Poster/MSNet3.png)
  
<span data-ttu-id="223b8-236">Nella figura 9 è illustrato un diagramma logico della rete cloud Microsoft in tutto il mondo, con reti che si estendono nei continenti e nelle aree geografiche del mondo e nelle loro interconnessioni.</span><span class="sxs-lookup"><span data-stu-id="223b8-236">Figure 9 shows a logical diagram of the worldwide Microsoft cloud network, with networks that span the continents and regions of the world and their interconnections.</span></span> <span data-ttu-id="223b8-237">Con una parte della rete cloud Microsoft in ogni continente, un'organizzazione globale crea connessioni ExpressRoute Premium dalle sedi degli hub regionali alle posizioni di peering di Microsoft locali.</span><span class="sxs-lookup"><span data-stu-id="223b8-237">With a portion of the Microsoft cloud network in each continent, a global enterprise creates ExpressRoute Premium connections from its regional hub offices to local Microsoft peering locations.</span></span>
  
<span data-ttu-id="223b8-238">Per un ufficio regionale, il traffico di Office 365 appropriato per:</span><span class="sxs-lookup"><span data-stu-id="223b8-238">For a regional office, appropriate Office 365 traffic to:</span></span>
  
- <span data-ttu-id="223b8-239">I datacenter di Office 365 continentale viaggiano sulla rete cloud Microsoft all'interno del continente.</span><span class="sxs-lookup"><span data-stu-id="223b8-239">Continental Office 365 datacenters travels over the Microsoft cloud network within the continent.</span></span>
    
- <span data-ttu-id="223b8-240">I datacenter di Office 365 in un altro continente viaggiano sulla rete intercontinentale Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="223b8-240">Office 365 datacenters in another continent travels over the intercontinental Microsoft cloud network.</span></span>
    
<span data-ttu-id="223b8-241">Per ulteriori informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="223b8-241">For more information, see:</span></span>
  
- [<span data-ttu-id="223b8-242">Formazione di Azure ExpressRoute per Office 365</span><span class="sxs-lookup"><span data-stu-id="223b8-242">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="223b8-243">Pianificazione della rete e ottimizzazione delle prestazioni per Office 365</span><span class="sxs-lookup"><span data-stu-id="223b8-243">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="expressroute-options"></a><span data-ttu-id="223b8-244">Opzioni di ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="223b8-244">ExpressRoute options</span></span>

<span data-ttu-id="223b8-245">È inoltre possibile incorporare le opzioni seguenti nella distribuzione di ExpressRoute:</span><span class="sxs-lookup"><span data-stu-id="223b8-245">You can also incorporate the following options into your ExpressRoute deployment:</span></span>
  
- <span data-ttu-id="223b8-246">**Sicurezza al tuo margine:** Per garantire una sicurezza avanzata per il traffico inviato e ricevuto tramite la connessione ExpressRoute, ad esempio il controllo del traffico o il rilevamento di intrusioni/malware, inserire gli strumenti di sicurezza nel percorso di traffico all'interno della DMZ o al bordo della rete Intranet.</span><span class="sxs-lookup"><span data-stu-id="223b8-246">**Security at your edge:** To provide advanced security for the traffic sent and received over the ExpressRoute connection, such as traffic inspection or intrusion/malware detection, place your security appliances in the traffic path within your DMZ or at the border of your intranet.</span></span>
    
- <span data-ttu-id="223b8-247">**Traffico Internet per le macchine virtuali:** Per impedire che le macchine virtuali di Azure inizino il traffico direttamente con le posizioni Internet, annunciare la route predefinita a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="223b8-247">**Internet traffic for VMs:** To prevent Azure VMs from initiating traffic directly with Internet locations, advertise the default route to Microsoft.</span></span> <span data-ttu-id="223b8-248">Il traffico su Internet viene instradato attraverso la connessione ExpressRoute e attraverso i server proxy locali.</span><span class="sxs-lookup"><span data-stu-id="223b8-248">Traffic to the Internet is routed across the ExpressRoute connection and through your on-premises proxy servers.</span></span> <span data-ttu-id="223b8-249">Il traffico dalle macchine virtuali di Azure ai servizi di PaaS di Azure o Office 365 viene instradato all'interno della connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="223b8-249">Traffic from Azure VMs to Azure PaaS services or Office 365 is routed back across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="223b8-250">**OttimizzaTori WAN:** È possibile distribuire ottimizzatori WAN su entrambi i lati di una connessione peer privata per una rete virtuale di Azure cross-premise (rete virtuale).</span><span class="sxs-lookup"><span data-stu-id="223b8-250">**WAN optimizers:** You can deploy WAN optimizers on both sides of a private peering connection for a cross-premises Azure virtual network (VNet).</span></span> <span data-ttu-id="223b8-251">All'interno di rete virtuale di Azure, utilizzare un dispositivo di rete WAN Optimizer da Azure Marketplace e routing definito dall'utente per instradare il traffico tramite l'accessorio.</span><span class="sxs-lookup"><span data-stu-id="223b8-251">Inside the Azure VNet, use a WAN optimizer network appliance from the Azure marketplace and user-defined routing to route the traffic through the appliance.</span></span>
    
- <span data-ttu-id="223b8-252">**Qualità del servizio:** Utilizzare i valori di codice Point (DSCP) di servizi differenziati nell'intestazione IPv4 del traffico per contrassegnarla per il recapito vocale, video/Interactive o Best-Effort.</span><span class="sxs-lookup"><span data-stu-id="223b8-252">**Quality of service:** Use Differentiated Services Code Point (DSCP) values in the IPv4 header of your traffic to mark it for voice, video/interactive, or best-effort delivery.</span></span> <span data-ttu-id="223b8-253">Questo è particolarmente importante per la relazione di peering Microsoft e per il traffico di Skype for business online.</span><span class="sxs-lookup"><span data-stu-id="223b8-253">This is especially important for the Microsoft peering relationship and Skype for Business Online traffic.</span></span>
    
<span data-ttu-id="223b8-254">Per ulteriori informazioni, vedere queste risorse aggiuntive:</span><span class="sxs-lookup"><span data-stu-id="223b8-254">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="223b8-255">ExpressRoute per Office 365</span><span class="sxs-lookup"><span data-stu-id="223b8-255">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="223b8-256">Formazione di Azure ExpressRoute per Office 365</span><span class="sxs-lookup"><span data-stu-id="223b8-256">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="223b8-257">ExpressRoute per Azure</span><span class="sxs-lookup"><span data-stu-id="223b8-257">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a><span data-ttu-id="223b8-258">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="223b8-258">Next step</span></span>

[<span data-ttu-id="223b8-259">Progettazione di rete per Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="223b8-259">Designing networking for Microsoft SaaS</span></span>](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a><span data-ttu-id="223b8-260">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="223b8-260">See also</span></span>

[<span data-ttu-id="223b8-261">Rete di Microsoft Cloud per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="223b8-261">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="223b8-262">Risorse sull'architettura IT di Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="223b8-262">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

