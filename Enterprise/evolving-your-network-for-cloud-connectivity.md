---
title: Trasformazione della rete per la connettività cloud
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: "Riepilogo: Informazioni su come l'adozione cloud richiede un nuovo approccio agli investimenti nell'infrastruttura di rete."
ms.openlocfilehash: 16dbbafe46e903fa41163e12c1741a45b47c5f45
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915141"
---
# <a name="evolving-your-network-for-cloud-connectivity"></a><span data-ttu-id="39b5a-103">Trasformazione della rete per la connettività cloud</span><span class="sxs-lookup"><span data-stu-id="39b5a-103">Evolving your network for cloud connectivity</span></span>

 <span data-ttu-id="39b5a-104">**Riepilogo:** Informazioni su come l'adozione cloud richiede un nuovo approccio agli investimenti nell'infrastruttura di rete.</span><span class="sxs-lookup"><span data-stu-id="39b5a-104">**Summary:** Understand how cloud adoption requires a new approach to network infrastructure investments.</span></span>
  
<span data-ttu-id="39b5a-p101">La migrazione cloud cambia il volume e la natura dei flussi del traffico all'interno e all'esterno di una rete aziendale. Influisce, inoltre, sugli approcci finalizzati alla mitigazione dei rischi per la sicurezza.</span><span class="sxs-lookup"><span data-stu-id="39b5a-p101">Cloud migration changes the volume and nature of traffic flows within and outside a corporate network. It also affects approaches to mitigating security risk.</span></span>
  
- <span data-ttu-id="39b5a-107">Prima di nel cloud</span><span class="sxs-lookup"><span data-stu-id="39b5a-107">Before the cloud</span></span>
    
    <span data-ttu-id="39b5a-p102">La maggior parte degli investimenti nell'infrastruttura di rete sono state dedicate a garantire disponibili e affidabile e la connettività ad alte prestazioni a centri dati locali. Per molte organizzazioni, la connettività Internet non è stato critica per le operazioni aziendali interne. I confini della rete sono state principale difesa contro le violazioni della protezione.</span><span class="sxs-lookup"><span data-stu-id="39b5a-p102">Most networking infrastructure investments were spent on ensuring available, reliable, and performant connectivity to on-premises datacenters. For many organizations, Internet connectivity was not critical for internal business operations. Network boundaries were primary defenses against security breaches.</span></span>
    
- <span data-ttu-id="39b5a-111">Dopo aver nel cloud</span><span class="sxs-lookup"><span data-stu-id="39b5a-111">After the cloud</span></span>
    
    <span data-ttu-id="39b5a-p103">Con carichi di lavoro IT in esecuzione nel cloud e produttività nuove e sottoposti a migrazione, gli investimenti vengono spostate dall'infrastruttura locale centri dati per la connettività Internet, che ora è fondamentale per operazioni aziendali interne. Connettività federati Sposta strategia di protezione per proteggere le identità e dati quando circolano attraverso la rete e i punti di connettività ai servizi cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="39b5a-p103">With new and migrated productivity and IT workloads running in the cloud, infrastructure investments shift from on-premises datacenters to Internet connectivity, which is now critical for internal business operations. Federated connectivity shifts security strategy to protecting identities and data as they flow through the network and points of connectivity to Microsoft cloud services.</span></span>
    
<span data-ttu-id="39b5a-p104">Gli investimenti nell'infrastruttura di rete iniziano con la connettività. Ulteriori investimenti variano a seconda della categoria del servizio cloud.</span><span class="sxs-lookup"><span data-stu-id="39b5a-p104">Network infrastructure investments begin with connectivity. Additional investments depend on the category of cloud service.</span></span>
  
- <span data-ttu-id="39b5a-p105">**Software come servizio (SaaS)** Servizi Microsoft SaaS includono Office 365, Microsoft Intune e Microsoft Dynamics 365. Un'adozione dei servizi SaaS dagli utenti dipende dalla disponibilità elevata e la connettività ad alte prestazioni a Internet o direttamente a servizi cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="39b5a-p105">**Software as a Service (SaaS)** Microsoft SaaS services include Office 365, Microsoft Intune, and Microsoft Dynamics 365. Successful adoption of SaaS services by users depends on highly-available and performant connectivity to the Internet, or directly to Microsoft cloud services.</span></span>
    
    <span data-ttu-id="39b5a-p106">Architettura di rete è incentrata su connettività affidabile e ridondanti e la larghezza di banda ampio. Costante investimento include monitoraggio e ottimizzazione delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="39b5a-p106">Network architecture focuses on reliable, redundant connectivity and ample bandwidth. Ongoing investments include performance monitoring and tuning.</span></span>
    
- <span data-ttu-id="39b5a-p107">**Piattaforma Azure as a Service (PaaS)** Oltre che per i servizi Microsoft SaaS gli investimenti multisite o geograficamente distribuite applicazioni PaaS potrebbe essere necessario architettura Azure Traffic Managerhttp per distribuire il traffico client. Costante investimento include le prestazioni e monitoraggio del traffico di distribuzione e test di failover.</span><span class="sxs-lookup"><span data-stu-id="39b5a-p107">**Azure Platform as a Service (PaaS)** In addition to the investments for Microsoft SaaS services, multi-site or geographically distributed PaaS applications might require architecting Azure Traffic Manager to distribute client traffic. Ongoing investments include performance and traffic distribution monitoring and failover testing.</span></span>
    
- <span data-ttu-id="39b5a-p108">**Infrastruttura come servizio (IaaS)** Oltre a investimenti per i servizi Microsoft SaaS e PaaS, l'esecuzione di carichi di lavoro IT in IaaS richiede la progettazione e configurazione di Azure virtual reti di ospitare macchine virtuali, la connettività protetta per le applicazioni in esecuzione su di essi, routing, IP risoluzione DNS e bilanciamento del carico. Costante investimento include il monitoraggio e risoluzione dei problemi di protezione e le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="39b5a-p108">**Azure Infrastructure as a Service (IaaS)** In addition to the investments for Microsoft SaaS and PaaS services, running IT workloads in IaaS requires the design and configuration of Azure virtual networks that host virtual machines, secure connectivity to applications running on them, routing, IP addressing, DNS, and load balancing. Ongoing investments include performance and security monitoring and troubleshooting.</span></span>
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a><span data-ttu-id="39b5a-124">Aree di rete investimento per il successo nel cloud</span><span class="sxs-lookup"><span data-stu-id="39b5a-124">Areas of networking investment for success in the cloud</span></span>

<span data-ttu-id="39b5a-p109">Le organizzazioni aziendali può risultare vantaggiosa un approccio metodico per ottimizzare velocità effettiva della rete attraverso una rete intranet e Internet. È possibile traggono vantaggio da una connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="39b5a-p109">Enterprise organizations benefit from taking a methodical approach to optimizing network throughput across your intranet and to the Internet. You might also benefit from an ExpressRoute connection.</span></span>
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a><span data-ttu-id="39b5a-127">Ottimizzare la connettività di rete intranet alla rete perimetrale</span><span class="sxs-lookup"><span data-stu-id="39b5a-127">Optimize intranet connectivity to your edge network</span></span>

<span data-ttu-id="39b5a-p110">Nel corso degli anni, molte organizzazioni sono ottimizzate intranet connettività e le prestazioni per le applicazioni in esecuzione in locale datacenter. Con la produttività e IT carichi di lavoro in esecuzione nel cloud Microsoft, ulteriori investimenti devono garantire la disponibilità elevata connettività e che le prestazioni del traffico tra la rete perimetrale e gli utenti intranet sono ottimale.</span><span class="sxs-lookup"><span data-stu-id="39b5a-p110">Over the years, many organizations have optimized intranet connectivity and performance to applications running in on-premises datacenters. With productivity and IT workloads running in the Microsoft cloud, additional investment must ensure high connectivity availability and that traffic performance between your edge network and your intranet users is optimal.</span></span>
  
### <a name="optimize-throughput-at-your-edge-network"></a><span data-ttu-id="39b5a-130">Ottimizzazione della velocità effettiva alla rete perimetrale</span><span class="sxs-lookup"><span data-stu-id="39b5a-130">Optimize throughput at your edge network</span></span>

<span data-ttu-id="39b5a-131">Come più il traffico di produttività quotidiane viaggia nel cloud, è necessario esaminare l'insieme di sistemi strettamente nella rete perimetrale per verificare che siano corrente, garantire una disponibilità elevata e avere sufficiente capacità per soddisfare i carichi di picco.</span><span class="sxs-lookup"><span data-stu-id="39b5a-131">As more of your day-to-day productivity traffic travels to the cloud, you should closely examine the set of systems at your edge network to ensure that they are current, provide high availability, and have sufficient capacity to meet peak loads.</span></span>
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a><span data-ttu-id="39b5a-132">Per un contratto di servizio elevata Dynamics 365, Office 365 e Azure, utilizzare ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="39b5a-132">For a high SLA to Azure, Office 365, and Dynamics 365, use ExpressRoute</span></span>

<span data-ttu-id="39b5a-p111">Anche se è possibile utilizzare la connessione a Internet corrente dalla rete perimetrale, il traffico da e verso servizi cloud Microsoft deve condividere pipe con altri del traffico intranet in Internet. Inoltre, il traffico ai servizi cloud Microsoft è soggetto a congestione traffico Internet.</span><span class="sxs-lookup"><span data-stu-id="39b5a-p111">Although you can utilize your current Internet connection from your edge network, traffic to and from Microsoft cloud services must share the pipe with other intranet traffic going to the Internet. Additionally, your traffic to Microsoft cloud services is subject to Internet traffic congestion.</span></span>
  
<span data-ttu-id="39b5a-135">Per ottenere prestazioni ottimali e un contratto di servizio elevata, utilizzare ExpressRoute, una singola connessione WAN tra la rete e Azure, Office 365, Dynamics 365 o tutti e tre.</span><span class="sxs-lookup"><span data-stu-id="39b5a-135">For a high SLA and the best performance, use ExpressRoute, a dedicated WAN connection between your network and Azure, Office 365, Dynamics 365, or all three.</span></span> 
  
<span data-ttu-id="39b5a-p112">ExpressRoute può utilizzare il provider di rete esistente per una connessione dedicata. Risorse connessione tramite ExpressRoute vengono visualizzate come se sono sulla WAN, anche per le organizzazioni geograficamente distribuita.</span><span class="sxs-lookup"><span data-stu-id="39b5a-p112">ExpressRoute can leverage your existing network provider for a dedicated connection. Resources connected by ExpressRoute appear as if they are on your WAN, even for geographically-distributed organizations.</span></span>
  
<span data-ttu-id="39b5a-138">Per ulteriori informazioni, vedere [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="39b5a-138">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
## <a name="scope-of-network-investments"></a><span data-ttu-id="39b5a-139">Ambito degli investimenti di rete</span><span class="sxs-lookup"><span data-stu-id="39b5a-139">Scope of network investments</span></span>

<span data-ttu-id="39b5a-p113">L'ambito degli investimenti rete variano a seconda della categoria del servizio cloud. Investire in cloud Microsoft ingrandita gli investimenti del team di rete. Gli investimenti per i servizi IaaS, ad esempio, si applicano a tutte le aree di investimento.</span><span class="sxs-lookup"><span data-stu-id="39b5a-p113">The scope of network investments depend on the category of cloud service. Investing across Microsoft's cloud maximizes the investments of networking teams. For example, investments for IaaS services apply to all investment areas.</span></span>
  
|||||
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="39b5a-143">Aree di investimento</span><span class="sxs-lookup"><span data-stu-id="39b5a-143">Investment area</span></span>  <br/> |<span data-ttu-id="39b5a-144">SaaS</span><span class="sxs-lookup"><span data-stu-id="39b5a-144">SaaS</span></span>  <br/> |<span data-ttu-id="39b5a-145">PaaS</span><span class="sxs-lookup"><span data-stu-id="39b5a-145">PaaS</span></span>  <br/> |<span data-ttu-id="39b5a-146">IaaS</span><span class="sxs-lookup"><span data-stu-id="39b5a-146">IaaS</span></span>  <br/> |
|<span data-ttu-id="39b5a-147">Progettare la connettività Internet affidabile e ridondante con larghezza di banda ampio</span><span class="sxs-lookup"><span data-stu-id="39b5a-147">Architect reliable, redundant Internet connectivity with ample bandwidth</span></span>  <br/> |<span data-ttu-id="39b5a-148">Si applica</span><span class="sxs-lookup"><span data-stu-id="39b5a-148">Applies</span></span>  <br/> |<span data-ttu-id="39b5a-149">Si applica</span><span class="sxs-lookup"><span data-stu-id="39b5a-149">Applies</span></span>  <br/> |<span data-ttu-id="39b5a-150">Si applica</span><span class="sxs-lookup"><span data-stu-id="39b5a-150">Applies</span></span>  <br/> |
|<span data-ttu-id="39b5a-151">Monitorare e ottimizzare la velocità effettiva Internet per le prestazioni</span><span class="sxs-lookup"><span data-stu-id="39b5a-151">Monitor and tune Internet throughput for performance</span></span>  <br/> |<span data-ttu-id="39b5a-152">Si applica</span><span class="sxs-lookup"><span data-stu-id="39b5a-152">Applies</span></span>  <br/> |<span data-ttu-id="39b5a-153">Si applica</span><span class="sxs-lookup"><span data-stu-id="39b5a-153">Applies</span></span>  <br/> |<span data-ttu-id="39b5a-154">Si applica</span><span class="sxs-lookup"><span data-stu-id="39b5a-154">Applies</span></span>  <br/> |
|<span data-ttu-id="39b5a-155">Risoluzione dei problemi di connettività e la velocità effettiva Internet</span><span class="sxs-lookup"><span data-stu-id="39b5a-155">Troubleshoot Internet connectivity and throughput issues</span></span>  <br/> |<span data-ttu-id="39b5a-156">Si applica</span><span class="sxs-lookup"><span data-stu-id="39b5a-156">Applies</span></span>  <br/> |<span data-ttu-id="39b5a-157">Si applica</span><span class="sxs-lookup"><span data-stu-id="39b5a-157">Applies</span></span>  <br/> |<span data-ttu-id="39b5a-158">Si applica</span><span class="sxs-lookup"><span data-stu-id="39b5a-158">Applies</span></span>  <br/> |
|<span data-ttu-id="39b5a-159">Gestione del traffico Azure progettazione per il carico del traffico bilanciare agli endpoint diversi</span><span class="sxs-lookup"><span data-stu-id="39b5a-159">Design Azure Traffic Manager to load balance traffic to different endpoints</span></span>  <br/> ||<span data-ttu-id="39b5a-160">Si applica</span><span class="sxs-lookup"><span data-stu-id="39b5a-160">Applies</span></span>  <br/> |<span data-ttu-id="39b5a-161">Si applica</span><span class="sxs-lookup"><span data-stu-id="39b5a-161">Applies</span></span>  <br/> |
|<span data-ttu-id="39b5a-162">Connettività architetto affidabile e ridondante e ad alte prestazioni a Azure virtual Network</span><span class="sxs-lookup"><span data-stu-id="39b5a-162">Architect reliable, redundant, and performant connectivity to Azure virtual networks</span></span>  <br/> |||<span data-ttu-id="39b5a-163">Si applica</span><span class="sxs-lookup"><span data-stu-id="39b5a-163">Applies</span></span>  <br/> |
|<span data-ttu-id="39b5a-164">Progettare la connettività protetta per macchine virtuali di Azure</span><span class="sxs-lookup"><span data-stu-id="39b5a-164">Design secure connectivity to Azure virtual machines</span></span>  <br/> |||<span data-ttu-id="39b5a-165">Si applica</span><span class="sxs-lookup"><span data-stu-id="39b5a-165">Applies</span></span>  <br/> |
|<span data-ttu-id="39b5a-166">Progettare e implementare il routing tra le posizioni in locale e reti virtuali</span><span class="sxs-lookup"><span data-stu-id="39b5a-166">Design and implement routing between on-premises locations and virtual networks</span></span>  <br/> |||<span data-ttu-id="39b5a-167">Si applica</span><span class="sxs-lookup"><span data-stu-id="39b5a-167">Applies</span></span>  <br/> |
|<span data-ttu-id="39b5a-168">Progettare e implementare il bilanciamento del carico per carichi di lavoro IT interni e con connessione Internet</span><span class="sxs-lookup"><span data-stu-id="39b5a-168">Architect and implement load balancing for internal and Internet-facing IT workloads</span></span>  <br/> |||<span data-ttu-id="39b5a-169">Si applica</span><span class="sxs-lookup"><span data-stu-id="39b5a-169">Applies</span></span>  <br/> |
|<span data-ttu-id="39b5a-170">Risoluzione dei problemi di connettività e velocità effettiva delle macchine virtuali</span><span class="sxs-lookup"><span data-stu-id="39b5a-170">Troubleshoot virtual machine connectivity and throughput issues</span></span>  <br/> |||<span data-ttu-id="39b5a-171">Si applica</span><span class="sxs-lookup"><span data-stu-id="39b5a-171">Applies</span></span>  <br/> |
   
## <a name="next-step"></a><span data-ttu-id="39b5a-172">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="39b5a-172">Next step</span></span>

[<span data-ttu-id="39b5a-173">Elementi comuni della connettività cloud di Microsoft</span><span class="sxs-lookup"><span data-stu-id="39b5a-173">Common elements of Microsoft cloud connectivity</span></span>](common-elements-of-microsoft-cloud-connectivity.md)

## <a name="see-also"></a><span data-ttu-id="39b5a-174">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="39b5a-174">See also</span></span>

[<span data-ttu-id="39b5a-175">Rete di Microsoft Cloud per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="39b5a-175">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="39b5a-176">Risorse sull'architettura IT di Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="39b5a-176">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



