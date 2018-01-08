---
title: Progettazione della rete per IaaS di Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: concetpual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: 'Riepilogo: Informazioni su come progettare la rete ottimizzata per carichi di lavoro in Microsoft Azure IaaS.'
ms.openlocfilehash: e4861de51f386af6e142debdafc64f655f010880
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a><span data-ttu-id="d266c-103">Progettazione della rete per IaaS di Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="d266c-103">Designing networking for Microsoft Azure IaaS</span></span>

 <span data-ttu-id="d266c-104">**Riepilogo:** Informazioni su come progettare la rete ottimizzata per carichi di lavoro in Microsoft Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="d266c-104">**Summary:** Understand how to design optimized networking for workloads in Microsoft Azure IaaS.</span></span>
  
<span data-ttu-id="d266c-105">L'ottimizzazione della rete per i carichi di lavoro IT ospitati in IaaS di Azure richiede una certa familiarità con le reti virtuali di Azure, gli spazi di indirizzi, il routing, il sistema DNS e il bilanciamento del carico.</span><span class="sxs-lookup"><span data-stu-id="d266c-105">Optimizing networking for IT workloads hosted in Azure IaaS requires an understanding of Azure virtual networks (VNets), address spaces, routing, DNS, and load balancing.</span></span>
  
## <a name="planning-steps-for-any-vnet"></a><span data-ttu-id="d266c-106">Operazioni di pianificazione per qualsiasi rete virtuale</span><span class="sxs-lookup"><span data-stu-id="d266c-106">Planning steps for any VNet</span></span>

<span data-ttu-id="d266c-107">Seguire questa procedura per qualsiasi tipo di rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="d266c-107">Follow these steps for any type of VNet.</span></span>
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a><span data-ttu-id="d266c-108">Passaggio 1: Predisporre la rete Intranet per i servizi cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d266c-108">Step 1: Prepare your intranet for Microsoft cloud services.</span></span>

<span data-ttu-id="d266c-109">Passare attraverso la sezione **operazioni per preparare la rete di servizi cloud Microsoft** in [elementi comuni di integrazione applicativa di Microsoft cloud](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="d266c-109">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-2-optimize-your-internet-bandwidth"></a><span data-ttu-id="d266c-110">Passaggio 2: Ottimizzare la larghezza di banda Internet.</span><span class="sxs-lookup"><span data-stu-id="d266c-110">Step 2: Optimize your Internet bandwidth.</span></span>

<span data-ttu-id="d266c-111">Ottimizzare la larghezza di banda Internet utilizzando i passaggi da 2 a 4 della sezione **passaggi per la preparazione della rete per i servizi Microsoft SaaS** nella [Progettazione di rete per Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span><span class="sxs-lookup"><span data-stu-id="d266c-111">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a><span data-ttu-id="d266c-112">Passaggio 3: Determinare il tipo di rete virtuale (solo cloud o cross-premise).</span><span class="sxs-lookup"><span data-stu-id="d266c-112">Step 3: Determine the type of VNet (cloud-only or cross-premises).</span></span>

<span data-ttu-id="d266c-p101">Una rete virtuale solo cloud non dispone di connessione a una rete locale. Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="d266c-p101">A cloud-only VNet has no connection to an on-premises network. Here is an example.</span></span>
  
<span data-ttu-id="d266c-115">**Nella figura 1: Un VNet di solo cloud**</span><span class="sxs-lookup"><span data-stu-id="d266c-115">**Figure 1: A cloud-only VNet**</span></span>

![Figura 1: Una rete virtuale basata solo su cloud in Azure](images/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
<span data-ttu-id="d266c-117">La figura 1 mostra un insieme di macchine virtuali all'interno di una rete virtuale solo cloud.</span><span class="sxs-lookup"><span data-stu-id="d266c-117">Figure 1 shows a set of virtual machines in a cloud-only VNet.</span></span>
  
<span data-ttu-id="d266c-p102">Una rete virtuale locale dispone di una connessione S2S VPN o ExpressRoute da sito a sito a una rete locale mediante il gateway Azure. Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="d266c-p102">A cross-premises VNet has a site-to-site (S2S) VPN or ExpressRoute connection to an on-premises network through an Azure gateway. Here is an example.</span></span>
  
<span data-ttu-id="d266c-120">**Figura 2: VNet tra locali**</span><span class="sxs-lookup"><span data-stu-id="d266c-120">**Figure 2: A cross-premises VNet**</span></span>

![Figura 2: Una rete virtuale di Azure tra più sedi](images/caacf007-e0dc-45d3-9531-441109776d25.png)
  
<span data-ttu-id="d266c-122">La figura 2 mostra un insieme di macchine virtuali all'interno di una rete virtuale locale, connessa a una rete locale.</span><span class="sxs-lookup"><span data-stu-id="d266c-122">Figure 2 shows a set of virtual machines in a cross-premises VNet, which is connected to an on-premises network.</span></span>
  
<span data-ttu-id="d266c-123">Vedere le ulteriori [operazioni di pianificazione per un VNet cross-premise](designing-networking-for-microsoft-azure-iaas.md#cross_prem) sezione in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="d266c-123">See the additional [Planning steps for a cross-premises VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) section in this article.</span></span>
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a><span data-ttu-id="d266c-124">Passaggio 4: Determinare lo spazio indirizzi della rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="d266c-124">Step 4: Determine the address space of the VNet.</span></span>

<span data-ttu-id="d266c-125">La tabella 1 mostra gli spazi indirizzi per i vari tipi di rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="d266c-125">Table 1 shows the address spaces for the different types of VNets.</span></span>
  
|<span data-ttu-id="d266c-126">**Tipo di VNet**</span><span class="sxs-lookup"><span data-stu-id="d266c-126">**Type of VNet**</span></span>|<span data-ttu-id="d266c-127">**Spazio degli indirizzi di rete virtuale**</span><span class="sxs-lookup"><span data-stu-id="d266c-127">**Virtual network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d266c-128">Solo cloud</span><span class="sxs-lookup"><span data-stu-id="d266c-128">Cloud-only</span></span>  <br/> |<span data-ttu-id="d266c-129">Spazio di indirizzi privato arbitrario</span><span class="sxs-lookup"><span data-stu-id="d266c-129">Arbitrary private address space</span></span>  <br/> |
|<span data-ttu-id="d266c-130">Solo cloud interconnesso</span><span class="sxs-lookup"><span data-stu-id="d266c-130">Interconnected cloud-only</span></span>  <br/> |<span data-ttu-id="d266c-131">Private arbitrarie, ma non la sovrapposizione con altre connessi VNets</span><span class="sxs-lookup"><span data-stu-id="d266c-131">Arbitrary private, but not overlapping with other connected VNets</span></span>  <br/> |
|<span data-ttu-id="d266c-132">Cross-premise</span><span class="sxs-lookup"><span data-stu-id="d266c-132">Cross-premises</span></span>  <br/> |<span data-ttu-id="d266c-133">Privato, ma non in sovrapposizione alle reti virtuali locali</span><span class="sxs-lookup"><span data-stu-id="d266c-133">Private, but not overlapping with on-premises</span></span>  <br/> |
|<span data-ttu-id="d266c-134">Cross-premise interconnesso</span><span class="sxs-lookup"><span data-stu-id="d266c-134">Interconnected cross-premises</span></span>  <br/> |<span data-ttu-id="d266c-135">Privato, ma non in sovrapposizione ad altre reti virtuali locali e connesse</span><span class="sxs-lookup"><span data-stu-id="d266c-135">Private, but not overlapping with on-premises and other connected VNets</span></span>  <br/> |
   
 <span data-ttu-id="d266c-136">**Tabella 1: Tipi di VNets e sul relativo spazio indirizzo**</span><span class="sxs-lookup"><span data-stu-id="d266c-136">**Table 1: Types of VNets and their corresponding address space**</span></span>
  
<span data-ttu-id="d266c-137">Le macchine virtuali sono assegnate a una configurazione di indirizzi dallo spazio di indirizzi della subnet da parte di DHCP:</span><span class="sxs-lookup"><span data-stu-id="d266c-137">Virtual machines are assigned an address configuration from the address space of the subnet by DHCP:</span></span>
  
- <span data-ttu-id="d266c-138">indirizzo/subnet mask</span><span class="sxs-lookup"><span data-stu-id="d266c-138">Address/subnet mask</span></span>
    
- <span data-ttu-id="d266c-139">Gateway predefinito</span><span class="sxs-lookup"><span data-stu-id="d266c-139">Default gateway</span></span>
    
- <span data-ttu-id="d266c-140">Indirizzi IP dei server DNS</span><span class="sxs-lookup"><span data-stu-id="d266c-140">DNS server IP addresses</span></span>
    
<span data-ttu-id="d266c-141">È anche possibile riservare un indirizzo IP statico.</span><span class="sxs-lookup"><span data-stu-id="d266c-141">You can also reserve a static IP address.</span></span>
  
<span data-ttu-id="d266c-142">Le macchine virtuali possono anche essere assegnate a un indirizzo IP pubblico, singolarmente o dal servizio cloud contenitore (solo per computer di distribuzione classici).</span><span class="sxs-lookup"><span data-stu-id="d266c-142">Virtual machines can also be assigned a public IP address, either individually or from the containing cloud service (for classic deployment machines only).</span></span>
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a><span data-ttu-id="d266c-143">Passaggio 5: Determinare le subnet all'interno della rete virtuale e gli spazi di indirizzi assegnati a ognuna di esse.</span><span class="sxs-lookup"><span data-stu-id="d266c-143">Step 5: Determine the subnets within the VNet and the address spaces assigned to each.</span></span>

<span data-ttu-id="d266c-144">Esistono due tipi di subnet in una rete virtuale, una subnet gateway e una subnet che ospita la macchina virtuale.</span><span class="sxs-lookup"><span data-stu-id="d266c-144">There are two types of subnets in a VNet, a gateway subnet and a virtual machine-hosting subnet.</span></span>
  
<span data-ttu-id="d266c-145">**Figura 3: I due tipi di subnet in Azure**</span><span class="sxs-lookup"><span data-stu-id="d266c-145">**Figure 3: The two types of subnets in Azure**</span></span>

![Figura 3: Due tipi di sottoreti in Azure](images/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
<span data-ttu-id="d266c-147">La figura 3 mostra un rete virtuale contenente una subnet gateway che include un gateway Azure e un set di subnet che ospitano macchine virtuali.</span><span class="sxs-lookup"><span data-stu-id="d266c-147">Figure 3 shows a VNet containing a gateway subnet that contains an Azure gateway and a set of virtual machine-hosting subnets containing virtual machines.</span></span>
  
<span data-ttu-id="d266c-p103">La subnet gateway di Azure è necessaria per ospitare le due macchine virtuali del gateway di Azure. Specificare uno spazio indirizzi con una lunghezza del prefisso di almeno 29 bit (ad esempio: 192.168.15.248/29). Si consiglia di usare una lunghezza prefisso di massimo 28 bit, soprattutto se si prevede di utilizzare ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="d266c-p103">The Azure gateway subnet is needed by Azure to host the two virtual machines of your Azure gateway. Specify an address space with at least a 29-bit prefix length (example: 192.168.15.248/29). A 28-bit or smaller prefix length is recommended, especially if you are planning to use ExpressRoute.</span></span>
  
<span data-ttu-id="d266c-151">Di seguito è riportata una procedura consigliata per determinare lo spazio indirizzi della subnet gateway di Azure:</span><span class="sxs-lookup"><span data-stu-id="d266c-151">A best practice for determining the address space of the Azure gateway subnet is the following:</span></span>
  
1. <span data-ttu-id="d266c-152">Decidere la dimensione della subnet del gateway.</span><span class="sxs-lookup"><span data-stu-id="d266c-152">Decide on the size of the gateway subnet.</span></span>
    
2. <span data-ttu-id="d266c-153">Nei bit variabili nello spazio indirizzi della rete virtuale, impostare i bit usati per la subnet gateway su 0 e impostare i bit rimanenti su 1.</span><span class="sxs-lookup"><span data-stu-id="d266c-153">In the variable bits in the address space of the VNet, set the bits used for the gateway subnet to 0 and set the remaining bits to 1.</span></span>
    
3. <span data-ttu-id="d266c-154">Convertire in formato decimale ed esprimerli come spazio di indirizzi con la lunghezza del prefisso impostata sulle dimensioni della subnet del gateway.</span><span class="sxs-lookup"><span data-stu-id="d266c-154">Convert to decimal and express as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="d266c-155">Con questo metodo, lo spazio di indirizzi per la subnet del gateway è sempre all'estremità più lontana dello spazio di indirizzi della rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="d266c-155">With this method, the address space for the gateway subnet is always at the farthest end of the VNet address space.</span></span>
  
<span data-ttu-id="d266c-p104">Di seguito, è riportato un esempio di definizione del prefisso dell'indirizzo per la subnet del gateway Lo spazio indirizzi della rete virtuale è 10.119.0.0/16. Inizialmente l'organizzazione userà una connessione VPN da sito a sito, ma probabilmente passerà a ExpressRoute. La tabella 2 mostra i passaggi e i risultati relativi alla definizione del prefisso di indirizzo della subnet gateway nella notazione per i prefissi di rete (detta anche CIDR).</span><span class="sxs-lookup"><span data-stu-id="d266c-p104">Here is an example of defining the address prefix for the gateway subnet: The address space of the VNet is 10.119.0.0/16. The organization will initially use a site-to-site VPN connection, but will eventually get ExpressRoute. Table 2 shows the steps and results of determining the gateway subnet address prefix in network prefix notation (also known as CIDR).</span></span>

<span data-ttu-id="d266c-159">Di seguito sono i passaggi e l'esempio che consente di determinare il prefisso dell'indirizzo gateway subnet:</span><span class="sxs-lookup"><span data-stu-id="d266c-159">Here are the steps and example of determining the gateway subnet address prefix:</span></span>

1. <span data-ttu-id="d266c-p105">Decidere le dimensioni della subnet gateway. In questo esempio, si è scelto /28.</span><span class="sxs-lookup"><span data-stu-id="d266c-p105">Decide on the size of the gateway subnet. For our example, we chose /28.</span></span>
2. <span data-ttu-id="d266c-p106">Impostare i bit nella variabile parte dello spazio di indirizzi VNet (b) su 0 per il gateway subnet bit (G), 1 indica il contrario (V). Per questo esempio viene utilizzato lo spazio degli indirizzi 10.119.0.0/16 per il VNet.</span><span class="sxs-lookup"><span data-stu-id="d266c-p106">Set the bits in the variable portion of the VNet address space (b) to 0 for the gateway subnet bits (G), otherwise 1 (V). For our example, we are using the 10.119.0.0/16 address space for the VNet. </span></span><br/>
<br/><span data-ttu-id="d266c-p107">10.119. bbbbbbbb. bbbbbbbb</span><span class="sxs-lookup"><span data-stu-id="d266c-p107">10.119. bbbbbbbb . bbbbbbbb </span></span><br/><span data-ttu-id="d266c-p108">10.119. VVVVVVVV. VVVVGGGG</span><span class="sxs-lookup"><span data-stu-id="d266c-p108">10.119. VVVVVVVV . VVVVGGGG </span></span><br/><span data-ttu-id="d266c-p109">10.119. 11111111. 11110000</span><span class="sxs-lookup"><span data-stu-id="d266c-p109">10.119. 11111111 . 11110000 </span></span><br/><br/>
3. <span data-ttu-id="d266c-p110">Convertire il risultato del passaggio 2 in decimale ed express come uno spazio degli indirizzi. In questo esempio, 10.119. 11111111. 11110000 è 10.119.255.240 e con la lunghezza del prefisso nel passaggio 1, (28 in questo esempio), il prefisso subnet gateway risultante è 10.119.255.240/28.</span><span class="sxs-lookup"><span data-stu-id="d266c-p110">Convert the result from step 2 to decimal and express as an address space. For our example, 10.119. 11111111 . 11110000 is 10.119.255.240, and with the prefix length from step 1, (28 in our example), the resulting gateway subnet address prefix is 10.119.255.240/28.</span></span>
  
<span data-ttu-id="d266c-177">Per ulteriori informazioni, vedere [la calcolatrice spazio indirizzo per le subnet gateway Azure](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) .</span><span class="sxs-lookup"><span data-stu-id="d266c-177">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for more information.</span></span>
  
<span data-ttu-id="d266c-178">Nelle subnet che ospitano le macchine virtuali si inseriscono le macchine virtuali di Azure. È possibile effettuare questa operazione in base alle tipiche linee guide in locale, come un livello o ruolo comune di un'applicazione o per l'isolamento della subnet.</span><span class="sxs-lookup"><span data-stu-id="d266c-178">Virtual machine-hosting subnets are where you place Azure virtual machines, which you can do according to typical on-premises guidelines, such as a common role or tier of an application or for subnet isolation.</span></span>
  
<span data-ttu-id="d266c-p111">Azure utilizza gli indirizzi prime 3 in ogni subnet. Di conseguenza, il numero di indirizzi possibili in una subnet Azure è 2<sup>n</sup> -5, dove n è il numero di bit host. Nella tabella 3 viene illustrato l'intervallo delle macchine virtuali necessarie, il numero di ospita bit necessari e le dimensioni di subnet corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="d266c-p111">Azure uses the first 3 addresses on each subnet. Therefore, the number of possible addresses on an Azure subnet is 2<sup>n</sup> - 5, where n is the number of host bits. Table 3 shows the range of virtual machines required, the number of hosts bits needed, and the corresponding subnet size.</span></span>
  
|<span data-ttu-id="d266c-182">**Macchine virtuali necessarie**</span><span class="sxs-lookup"><span data-stu-id="d266c-182">**Virtual machines required**</span></span>|<span data-ttu-id="d266c-183">**Bit host**</span><span class="sxs-lookup"><span data-stu-id="d266c-183">**Host bits**</span></span>|<span data-ttu-id="d266c-184">**Dimensioni subnet**</span><span class="sxs-lookup"><span data-stu-id="d266c-184">**Subnet size**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="d266c-185">1-3</span><span class="sxs-lookup"><span data-stu-id="d266c-185">1-3</span></span>  <br/> |<span data-ttu-id="d266c-186">3</span><span class="sxs-lookup"><span data-stu-id="d266c-186">3</span></span>  <br/> |<span data-ttu-id="d266c-187">/29</span><span class="sxs-lookup"><span data-stu-id="d266c-187">/29</span></span>  <br/> |
|<span data-ttu-id="d266c-188">4-11</span><span class="sxs-lookup"><span data-stu-id="d266c-188">4-11</span></span>  <br/> |<span data-ttu-id="d266c-189">4</span><span class="sxs-lookup"><span data-stu-id="d266c-189">4</span></span>  <br/> |<span data-ttu-id="d266c-190">/28</span><span class="sxs-lookup"><span data-stu-id="d266c-190">/28</span></span>  <br/> |
|<span data-ttu-id="d266c-191">12-27</span><span class="sxs-lookup"><span data-stu-id="d266c-191">12-27</span></span>  <br/> |<span data-ttu-id="d266c-192">5</span><span class="sxs-lookup"><span data-stu-id="d266c-192">5</span></span>  <br/> |<span data-ttu-id="d266c-193">/27</span><span class="sxs-lookup"><span data-stu-id="d266c-193">/27</span></span>  <br/> |
|<span data-ttu-id="d266c-194">28-59</span><span class="sxs-lookup"><span data-stu-id="d266c-194">28-59</span></span>  <br/> |<span data-ttu-id="d266c-195">6</span><span class="sxs-lookup"><span data-stu-id="d266c-195">6</span></span>  <br/> |<span data-ttu-id="d266c-196">/26</span><span class="sxs-lookup"><span data-stu-id="d266c-196">/26</span></span>  <br/> |
|<span data-ttu-id="d266c-197">60-123</span><span class="sxs-lookup"><span data-stu-id="d266c-197">60-123</span></span>  <br/> |<span data-ttu-id="d266c-198">7</span><span class="sxs-lookup"><span data-stu-id="d266c-198">7</span></span>  <br/> |<span data-ttu-id="d266c-199">/25</span><span class="sxs-lookup"><span data-stu-id="d266c-199">/25</span></span>  <br/> |
   
 <span data-ttu-id="d266c-200">**Tabella 3: requisiti delle macchine virtuali e alle dimensioni di subnet**</span><span class="sxs-lookup"><span data-stu-id="d266c-200">**Table 3: Virtual machine requirements and their subnet sizes**</span></span>
  
<span data-ttu-id="d266c-201">Per ulteriori informazioni sulla quantità massima di macchine virtuali in una subnet o VNet, vedere [Limiti di rete](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span><span class="sxs-lookup"><span data-stu-id="d266c-201">For more information about the maximum amount of virtual machines on a subnet or VNet, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="d266c-202">Per ulteriori informazioni, vedere [pianificare e progettare reti virtuali di Azure](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span><span class="sxs-lookup"><span data-stu-id="d266c-202">For more information, see [Plan and design Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span></span>
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a><span data-ttu-id="d266c-203">Passaggio 6: Determinare la configurazione del server DNS e gli indirizzi dei server DNS da assegnare alle macchine virtuali della rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="d266c-203">Step 6: Determine the DNS server configuration and the addresses of the DNS servers to assign to VMs in the VNet.</span></span>

<span data-ttu-id="d266c-p112">Azure assegna alle macchine virtuali gli indirizzi dei server DNS da parte di DHCP. I server DNS possono essere:</span><span class="sxs-lookup"><span data-stu-id="d266c-p112">Azure assigns virtual machines the addresses of DNS servers by DHCP. DNS servers can be:</span></span>
  
- <span data-ttu-id="d266c-206">Forniti da Azure: con registrazione del nome locale e risoluzione del nome Internet</span><span class="sxs-lookup"><span data-stu-id="d266c-206">Supplied by Azure: Provides local name registration and local and Internet name resolution</span></span>
    
- <span data-ttu-id="d266c-207">Forniti dall'utente: con registrazione del nome Intranet o locale e risoluzione del nome Intranet o Internet</span><span class="sxs-lookup"><span data-stu-id="d266c-207">Provided by you: Provides local or intranet name registration and either intranet or Internet name resolution</span></span>
    
<span data-ttu-id="d266c-208">La tabella 4 mostra le diverse configurazioni dei server DNS per ogni tipo di rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="d266c-208">Table 4 shows the different configurations of DNS servers for each type of VNet.</span></span>
    
|<span data-ttu-id="d266c-209">**Tipo di VNet**</span><span class="sxs-lookup"><span data-stu-id="d266c-209">**Type of VNet**</span></span>|<span data-ttu-id="d266c-210">**Server DNS**</span><span class="sxs-lookup"><span data-stu-id="d266c-210">**DNS server**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d266c-211">Solo cloud</span><span class="sxs-lookup"><span data-stu-id="d266c-211">Cloud-only</span></span>  <br/> |<span data-ttu-id="d266c-212">Fornito da Azure per la risoluzione dei nomi locali e Internet</span><span class="sxs-lookup"><span data-stu-id="d266c-212">Azure-supplied for local and Internet name resolution</span></span>  <br/> <span data-ttu-id="d266c-213">Macchina virtuale di Azure per la risoluzione dei nomi locali e Internet (inoltro DNS)</span><span class="sxs-lookup"><span data-stu-id="d266c-213">Azure virtual machine for local and Internet name resolution (DNS forwarding)</span></span>  <br/> |
|<span data-ttu-id="d266c-214">Cross-premise</span><span class="sxs-lookup"><span data-stu-id="d266c-214">Cross-premises</span></span>  <br/> |<span data-ttu-id="d266c-215">Locale per le risoluzione dei nomi locali e Intranet</span><span class="sxs-lookup"><span data-stu-id="d266c-215">On-premises for local and intranet name resolution</span></span>  <br/> <span data-ttu-id="d266c-216">Macchina virtuale di Azure per la risoluzione dei nomi locali e Intranet (replica e inoltro DNS)</span><span class="sxs-lookup"><span data-stu-id="d266c-216">Azure virtual machine for local and intranet name resolution (DNS replication and forwarding)</span></span>  <br/> |
   
 <span data-ttu-id="d266c-217">**Tabella 4: Opzioni del server DNS per i due tipi diversi di VNets**</span><span class="sxs-lookup"><span data-stu-id="d266c-217">**Table 4: DNS server options for the two different types of VNets**</span></span>
  
<span data-ttu-id="d266c-218">Per ulteriori informazioni, vedere [Risoluzione dei nomi per le macchine virtuali e istanze del ruolo](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span><span class="sxs-lookup"><span data-stu-id="d266c-218">For more information, see [Name Resolution for VMs and Role Instances](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span></span>
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a><span data-ttu-id="d266c-219">Passaggio 7: Determinare la configurazione del bilanciamento del carico (Internet o interno).</span><span class="sxs-lookup"><span data-stu-id="d266c-219">Step 7: Determine the load balancing configuration (Internet-facing or internal).</span></span>

<span data-ttu-id="d266c-p113">In alcuni casi, potrebbe essere necessario distribuire il traffico in arrivo in un insieme di server che hanno lo stesso ruolo. IaaS di Azure dispone di una funzione integrata per eseguire questa operazione per i carichi di traffico interno e verso Internet.</span><span class="sxs-lookup"><span data-stu-id="d266c-p113">In some cases, you want to distribute incoming traffic to a set of servers that have the same role. Azure IaaS has a built-in facility to do this for Internet-facing and internal traffic loads.</span></span>
  
<span data-ttu-id="d266c-222">Il bilanciamento del carico verso Internet di Azure distribuisce in ordine casuale il traffico in ingresso non richiesto da Internet ai membri di un set con carico bilanciato.</span><span class="sxs-lookup"><span data-stu-id="d266c-222">Azure Internet-facing load balancing randomly distributes unsolicited incoming traffic from the Internet to the members of a load-balanced set.</span></span>
  
<span data-ttu-id="d266c-223">**Figura 4: Un esterno bilanciamento del carico in Azure**</span><span class="sxs-lookup"><span data-stu-id="d266c-223">**Figure 4: An external load balancer in Azure**</span></span>

![Figura 4: Un bilanciamento del carico esterno in Azure](images/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
<span data-ttu-id="d266c-225">Figura 4 viene illustrato un servizio di bilanciamento del carico esterno in Azure che distribuisce il traffico in ingresso in una regola NAT in entrata o endpoint per una serie di macchine virtuali in un set di bilanciamento del carico.</span><span class="sxs-lookup"><span data-stu-id="d266c-225">Figure 4 shows an external load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="d266c-226">Il bilanciamento del carico interno di Azure distribuisce in modo casuale il traffico in ingresso da altre macchine virtuali di Azure o da computer Intranet ai membri di un set con carico bilanciato. </span><span class="sxs-lookup"><span data-stu-id="d266c-226">Azure internal load balancing randomly distributes unsolicited incoming traffic from other Azure VMs or from intranet computers to the members of a load-balanced set.</span></span> 
  
<span data-ttu-id="d266c-227">**Figura 5: Un interno bilanciamento del carico in Azure**</span><span class="sxs-lookup"><span data-stu-id="d266c-227">**Figure 5: An internal load balancer in Azure**</span></span>

![Figura 5: Un bilanciamento del carico interno in Azure](images/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
<span data-ttu-id="d266c-229">Figura 5 viene illustrato un servizio di bilanciamento del carico interno in Azure che distribuisce il traffico in ingresso in una regola NAT in entrata o endpoint per una serie di macchine virtuali in un set di bilanciamento del carico.</span><span class="sxs-lookup"><span data-stu-id="d266c-229">Figure 5 shows an internal load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="d266c-230">Per ulteriori informazioni, vedere [Bilanciamento del carico di Azure](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span><span class="sxs-lookup"><span data-stu-id="d266c-230">For more information, see [Azure Load Balancer](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span></span>
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a><span data-ttu-id="d266c-231">Passaggio 8: Determinare l'uso delle applicazioni virtuali e delle route definite dall'utente.</span><span class="sxs-lookup"><span data-stu-id="d266c-231">Step 8: Determine the use of virtual appliances and user-defined routes.</span></span>

<span data-ttu-id="d266c-232">Nel caso in cui fosse necessario inoltrare il traffico alle applicazioni virtuali della rete virtuale, è necessario aggiungere una o più route definite dall'utente a una subnet.</span><span class="sxs-lookup"><span data-stu-id="d266c-232">If you need to forward traffic to virtual appliances in your VNet, you may need to add one or more user-defined routes to a subnet.</span></span>
  
<span data-ttu-id="d266c-233">**Nella figura 6: Dispositivi di rete e le route definite dall'utente in Azure**</span><span class="sxs-lookup"><span data-stu-id="d266c-233">**Figure 6: Virtual appliances and user-defined routes in Azure**</span></span>

![Figura 6: Route definite dall’utente e dispositivi virtuali in Azure](images/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
<span data-ttu-id="d266c-235">La figura 6 mostra una rete virtuale cross-premise e una route definita dall'utente assegnate a una subnet che ospita una macchina virtuale che punta a un'applicazione virtuale.</span><span class="sxs-lookup"><span data-stu-id="d266c-235">Figure 6 shows a cross-premises VNet and a user-defined route assigned to a virtual machine-hosting subnet that points to a virtual appliance.</span></span>
  
<span data-ttu-id="d266c-236">Per ulteriori informazioni, vedere [le route definite dall'utente e inoltro IP](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span><span class="sxs-lookup"><span data-stu-id="d266c-236">For more information, see [User Defined Routes and IP Forwarding](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span></span>
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a><span data-ttu-id="d266c-237">Passaggio 9: Determinare la modalità di connessione di computer da Internet alle macchine virtuali.</span><span class="sxs-lookup"><span data-stu-id="d266c-237">Step 9: Determine how computers from the Internet will connect to virtual machines.</span></span>

<span data-ttu-id="d266c-238">Sono disponibili vari modi per fornire accesso a Internet alle macchine virtuali presenti in una rete virtuale, ad esempio, accesso dalla rete aziendale tramite server proxy oppure altri dispositivi periferici.</span><span class="sxs-lookup"><span data-stu-id="d266c-238">There are multiple ways to provide Internet access to the virtual machines on a VNet, which includes access from your organization network through your proxy server or other edge device.</span></span>
  
<span data-ttu-id="d266c-239">Nella tabella 5 sono riportati i metodi per filtrare o esaminare il traffico in ingresso non richiesto.</span><span class="sxs-lookup"><span data-stu-id="d266c-239">Table 5 lists the methods for filtering or inspecting unsolicited incoming traffic.</span></span>
  
|<span data-ttu-id="d266c-240">**Metodo**</span><span class="sxs-lookup"><span data-stu-id="d266c-240">**Method**</span></span>|<span data-ttu-id="d266c-241">**Modello di distribuzione**</span><span class="sxs-lookup"><span data-stu-id="d266c-241">**Deployment model**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d266c-242">1. Endpoint e ACL configurati sui servizi cloud</span><span class="sxs-lookup"><span data-stu-id="d266c-242">1. Endpoints and ACLs configured on cloud services</span></span>  <br/> |<span data-ttu-id="d266c-243">Classico</span><span class="sxs-lookup"><span data-stu-id="d266c-243">Classic</span></span>  <br/> |
|<span data-ttu-id="d266c-244">2. Gruppi di sicurezza di rete</span><span class="sxs-lookup"><span data-stu-id="d266c-244">2. Network security groups</span></span>  <br/> |<span data-ttu-id="d266c-245">Gestione risorse e classico</span><span class="sxs-lookup"><span data-stu-id="d266c-245">Resource Manager and classic</span></span>  <br/> |
|<span data-ttu-id="d266c-246">3. Bilanciamento del carico con accesso a Internet con regole NAT in ingresso</span><span class="sxs-lookup"><span data-stu-id="d266c-246">3. Internet-facing load balancer with inbound NAT rules</span></span>  <br/> |<span data-ttu-id="d266c-247">Manager delle risorse</span><span class="sxs-lookup"><span data-stu-id="d266c-247">Resource Manager</span></span>  <br/> |
|<span data-ttu-id="d266c-248">4. dispositivi di rete della protezione in di Azure</span><span class="sxs-lookup"><span data-stu-id="d266c-248">4. Network security appliances in the Azure</span></span> 
 <span data-ttu-id="d266c-249">Marketplace (non visualizzata)</span><span class="sxs-lookup"><span data-stu-id="d266c-249">Marketplace (not shown)</span></span>  <br/> |<span data-ttu-id="d266c-250">Gestione risorse e classico</span><span class="sxs-lookup"><span data-stu-id="d266c-250">Resource Manager and classic</span></span>  <br/> |
   
 <span data-ttu-id="d266c-251">**Tabella 5: Metodi di connessione per le macchine virtuali e dai modelli di distribuzione Azure corrispondenti**</span><span class="sxs-lookup"><span data-stu-id="d266c-251">**Table 5: Methods of connecting to virtual machines and their corresponding Azure deployment models**</span></span>
  
<span data-ttu-id="d266c-252">**Figura 7: La connessione alle macchine virtuali di Azure su Internet**</span><span class="sxs-lookup"><span data-stu-id="d266c-252">**Figure 7: Connecting to Azure virtual machines over the Internet**</span></span>

![Figura 7: Connessione a macchine virtuali di Azure tramite Internet](images/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
<span data-ttu-id="d266c-254">La figura 7 mostra un computer connesso a Internet che stabilisce una connessione con una macchina virtuale in un servizio cloud tramite un endpoint, una macchina virtuale su una subnet utilizzando un gruppo di sicurezza di rete e una macchina virtuale su una subnet utilizzando un bilanciamento del carico esterno e le regole NAT in ingresso.</span><span class="sxs-lookup"><span data-stu-id="d266c-254">Figure 7 shows an Internet-connected computer connecting to a virtual machine in a cloud service using an endpoint, a virtual machine on a subnet using a network security group, and a virtual machine on a subnet using an external load balancer and inbound NAT rules.</span></span>
  
<span data-ttu-id="d266c-255">Ulteriore sicurezza è offerta da:</span><span class="sxs-lookup"><span data-stu-id="d266c-255">Additional security is provided by:</span></span>
  
- <span data-ttu-id="d266c-256">Il desktop remoto e le connessioni SSH che sono autenticati e crittografati.</span><span class="sxs-lookup"><span data-stu-id="d266c-256">Remote Desktop and SSH connections, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="d266c-257">Le sessioni remote di PowerShell che sono autenticate e crittografate.</span><span class="sxs-lookup"><span data-stu-id="d266c-257">Remote PowerShell sessions, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="d266c-258">La modalità di trasporto IPsec, da usare per la crittografia end-to-end.</span><span class="sxs-lookup"><span data-stu-id="d266c-258">IPsec transport mode, which you can use for end-to-end encryption.</span></span>
    
- <span data-ttu-id="d266c-259">La protezione DDoS di Azure che blocca gli attacchi interni ed esterni.</span><span class="sxs-lookup"><span data-stu-id="d266c-259">Azure DDOS protection, which helps prevent external and internal attacks</span></span>
    
<span data-ttu-id="d266c-260">Per ulteriori informazioni, vedere [Microsoft Security Cloud per architetti](https://aka.ms/cloudarchsecurity) e [La protezione della rete Azure](https://azure.microsoft.com/blog/azure-network-security/).</span><span class="sxs-lookup"><span data-stu-id="d266c-260">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a><span data-ttu-id="d266c-261">Passaggio 10: Per più reti virtuali, determina la topologia di connessione da rete virtuale a rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="d266c-261">Step 10: For multiple VNets, determine the VNet-to-VNet connection topology.</span></span>

<span data-ttu-id="d266c-262">Le reti virtuali possono essere connesse tra loro mediante topologie simili a quelle utilizzate per la connessione dei siti di un'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="d266c-262">VNets can be connected to each other using topologies similar to those used for connecting the sites of an organization.</span></span>
  
<span data-ttu-id="d266c-263">Una configurazione di collegamento in cascata connette le reti virtuali in serie.</span><span class="sxs-lookup"><span data-stu-id="d266c-263">A daisy chain configuration connects the VNets in a series.</span></span>
  
<span data-ttu-id="d266c-264">**Figura 8: Una concatenati daisy configurazione per VNets**</span><span class="sxs-lookup"><span data-stu-id="d266c-264">**Figure 8: A daisy-chained configuration for VNets**</span></span>

![Figura 8: Una configurazione di collegamento in cascata per le reti virtuali Azure](images/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
<span data-ttu-id="d266c-266">Figura 8 mostra cinque VNets connessi nella serie utilizzando una configurazione daisy concatenati.</span><span class="sxs-lookup"><span data-stu-id="d266c-266">Figure 8 shows five VNets connected in series using a daisy-chained configuration.</span></span>
  
<span data-ttu-id="d266c-267">Una configurazione spoke e hub connette più reti virtuali a un set di reti virtuali centrali, che sono a loro connesse tra di loro.</span><span class="sxs-lookup"><span data-stu-id="d266c-267">A spoke and hub configuration connects multiple VNets to a set of central VNets, which are themselves connected to each other.</span></span>
  
<span data-ttu-id="d266c-268">**Figura 9: Un hub e spoke configurazione per VNets**</span><span class="sxs-lookup"><span data-stu-id="d266c-268">**Figure 9: A spoke and hub configuration for VNets**</span></span>

![Figura 9: Una configurazione hub-spoke per le reti virtuali di Azure](images/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
<span data-ttu-id="d266c-270">La figura 9 mostra 6 reti virtuali, 2 reti virtuali sono hub connessi a loro volta e anche 2 reti virtuali spoke.</span><span class="sxs-lookup"><span data-stu-id="d266c-270">Figure 9 shows six VNets, two VNets are hubs that are connected to each other and also two other spoke VNets.</span></span>
  
<span data-ttu-id="d266c-271">Una configurazione a maglia completa connette le reti virtuali tra di loro.</span><span class="sxs-lookup"><span data-stu-id="d266c-271">A full mesh configuration connects every VNet to each other.</span></span>
  
<span data-ttu-id="d266c-272">**Figura 10: Un intero trama configurazione per VNets**</span><span class="sxs-lookup"><span data-stu-id="d266c-272">**Figure 10: A full mesh configuration for VNets**</span></span>

![Figura 10: Una configurazione mesh per le reti virtuali di Azure](images/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
<span data-ttu-id="d266c-274">La figura 10 mostra 4 reti virtuali che sono connesse a vicenda utilizzando 6 collegamenti da rete virtuale a rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="d266c-274">Figure 10 shows four VNets that are all connected to each other, using a total of six VNet-to-VNet connections.</span></span>
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a><span data-ttu-id="d266c-275">Operazioni di pianificazione per una rete virtuale cross-premise</span><span class="sxs-lookup"><span data-stu-id="d266c-275">Planning steps for a cross-premises VNet</span></span>
<span data-ttu-id="d266c-276"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="d266c-276"></span></span>

<span data-ttu-id="d266c-277">Seguire questa procedura per una rete virtuale cross-premise.</span><span class="sxs-lookup"><span data-stu-id="d266c-277">Follow these steps for a cross-premises VNet.</span></span>
  
> [!TIP]
> <span data-ttu-id="d266c-278">Per creare un ambiente di sviluppo e di testing simulato tra locali, vedere [simulato tra locali reti virtuali di Azure](simulated-cross-premises-virtual-network-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="d266c-278">To create a simulated cross-premises dev/test environment, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span> 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a><span data-ttu-id="d266c-279">Passaggio 1: Determinare la connessione cross-premise alla rete virtuale (S2S VPN o ExpressRoute).</span><span class="sxs-lookup"><span data-stu-id="d266c-279">Step 1: Determine the cross-premises connection to the VNet (S2S VPN or ExpressRoute).</span></span>

<span data-ttu-id="d266c-280">Nella tabella 6 sono elencati i vari di tipi di connessioni.</span><span class="sxs-lookup"><span data-stu-id="d266c-280">Table 6 lists the different types of connections.</span></span>
  
|<span data-ttu-id="d266c-281">**Tipo di connessione**</span><span class="sxs-lookup"><span data-stu-id="d266c-281">**Type of connection**</span></span>|<span data-ttu-id="d266c-282">**Scopo**</span><span class="sxs-lookup"><span data-stu-id="d266c-282">**Purpose**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d266c-283">VPN da sito a sito (S2S)</span><span class="sxs-lookup"><span data-stu-id="d266c-283">Site-to-Site (S2S) VPN</span></span>  <br/> |<span data-ttu-id="d266c-284">Connettere i siti 1 a 10 (inclusi altri VNets) a un singolo VNet.</span><span class="sxs-lookup"><span data-stu-id="d266c-284">Connect 1-10 sites (including other VNets) to a single VNet.</span></span>  <br/> |
|<span data-ttu-id="d266c-285">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="d266c-285">ExpressRoute</span></span>  <br/> |<span data-ttu-id="d266c-286">Un collegamento sicuro e privato ad Azure tramite un IXP (Internet Exchange Provider) o un NSP (Network Service Provider).</span><span class="sxs-lookup"><span data-stu-id="d266c-286">A private, secure link to Azure via an Internet Exchange Provider (IXP) or a Network Service Provider (NSP).</span></span>  <br/> |
|<span data-ttu-id="d266c-287">VPN da punto a punto (P2S)</span><span class="sxs-lookup"><span data-stu-id="d266c-287">Point-to-Site (P2S) VPN</span></span>  <br/> |<span data-ttu-id="d266c-288">Connette un singolo computer alla rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="d266c-288">Connects a single computer to a VNet.</span></span>  <br/> |
|<span data-ttu-id="d266c-289">Peering della rete virtuale o VPN da rete virtuale a rete virtuale (V2V) </span><span class="sxs-lookup"><span data-stu-id="d266c-289">VNet peering or VNet-to-VNet (V2V) VPN</span></span>  <br/> |<span data-ttu-id="d266c-290">Connette una rete virtuale a un'altra rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="d266c-290">Connects a VNet to another VNet.</span></span>  <br/> |
   
 <span data-ttu-id="d266c-291">**Tabella 6: I tipi di connessioni per VNets tra locali**</span><span class="sxs-lookup"><span data-stu-id="d266c-291">**Table 6: The types of connections for cross-premises VNets**</span></span>
  
<span data-ttu-id="d266c-292">Per ulteriori informazioni sul numero massimo di connessioni, vedere [Limiti della rete](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span><span class="sxs-lookup"><span data-stu-id="d266c-292">For more information on the maximum number of connections, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="d266c-293">Per ulteriori informazioni sui dispositivi VPN, vedere [dispositivi VPN per le connessioni di rete virtuale di sito per sito](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="d266c-293">For more information about VPN devices, see [VPN devices for site-to-site virtual network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="d266c-294">Per ulteriori informazioni su VNet peering, vedere [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span><span class="sxs-lookup"><span data-stu-id="d266c-294">For more information about VNet peering, see [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span></span>
  
<span data-ttu-id="d266c-295">**Figura 11: Le quattro modalità per connettersi a un VNet tra locali**</span><span class="sxs-lookup"><span data-stu-id="d266c-295">**Figure 11: The four ways to connect to a cross-premises VNet**</span></span>

![Figura 11: I tre modi per connettersi a una rete virtuale di Azure tra più sedi](images/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
<span data-ttu-id="d266c-297">Nella figura 11 viene VNet con quattro tipi di connessioni: connessione a un P2S da un computer, una connessione VPN S2S da una rete locale, una connessione ExpressRoute da una rete locale e una connessione VNet-VNet da un altro VNet.</span><span class="sxs-lookup"><span data-stu-id="d266c-297">Figure 11 shows a VNet with the four types of connections: a P2S connection from a computer, an S2S VPN connection from an on-premises network, an ExpressRoute connection from an on-premises network, and a VNet-to-VNet connection from another VNet.</span></span> 
  
<span data-ttu-id="d266c-298">È possibile connettersi alle macchine virtuali di una rete virtuale nei modi seguenti:</span><span class="sxs-lookup"><span data-stu-id="d266c-298">You can connect to VMs in a VNet in the following ways:</span></span>
  
- <span data-ttu-id="d266c-299">Amministrazione delle macchine virtuali della rete virtuale dalla rete locale o da Internet</span><span class="sxs-lookup"><span data-stu-id="d266c-299">Administration of VNet VMs from your on-premises network or the Internet</span></span>
    
- <span data-ttu-id="d266c-300">Accesso al carico IT dalla rete locale</span><span class="sxs-lookup"><span data-stu-id="d266c-300">IT workload access from your on-premises network</span></span>
    
- <span data-ttu-id="d266c-301">Estensione della rete mediante reti virtuali aggiuntive</span><span class="sxs-lookup"><span data-stu-id="d266c-301">Extension of your network through additional VNets</span></span>
    
<span data-ttu-id="d266c-302">La sicurezza per le connessioni è offerta dai seguenti elementi:</span><span class="sxs-lookup"><span data-stu-id="d266c-302">Security for connections is provided by the following:</span></span>
  
- <span data-ttu-id="d266c-303">La connessione P2S usa il protocollo SSTP (Secure Socket Tunneling Protocol)  </span><span class="sxs-lookup"><span data-stu-id="d266c-303">P2S uses the Secure Socket Tunneling Protocol (SSTP)</span></span> 
    
- <span data-ttu-id="d266c-304">Le connessioni VPN S2S e da rete virtuale a rete virtuale usano la modalità tunnel IPsec con AES256</span><span class="sxs-lookup"><span data-stu-id="d266c-304">S2S and VNet-to-VNet VPN connections use IPsec tunnel mode with AES256</span></span>
    
- <span data-ttu-id="d266c-305">ExpressRoute è una connessione WAN privata</span><span class="sxs-lookup"><span data-stu-id="d266c-305">ExpressRoute is a private WAN connection</span></span>
    
<span data-ttu-id="d266c-306">Per ulteriori informazioni, vedere [Microsoft Security Cloud per architetti](https://aka.ms/cloudarchsecurity) e [La protezione della rete Azure](https://azure.microsoft.com/blog/azure-network-security/).</span><span class="sxs-lookup"><span data-stu-id="d266c-306">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a><span data-ttu-id="d266c-307">Passaggio 2: Determinare il router o dispositivo VPN locale.</span><span class="sxs-lookup"><span data-stu-id="d266c-307">Step 2: Determine the on-premises VPN device or router.</span></span>

<span data-ttu-id="d266c-308">Il router o dispositivo VPN locale si comporta come:</span><span class="sxs-lookup"><span data-stu-id="d266c-308">Your on-premises VPN device or router acts as:</span></span>
  
- <span data-ttu-id="d266c-309">Peer IPsec, terminando la connessione S2S VPN dal gateway di Azure.</span><span class="sxs-lookup"><span data-stu-id="d266c-309">An IPsec peer, terminating the S2S VPN connection from the Azure gateway.</span></span>
    
- <span data-ttu-id="d266c-310">Peer BPG e punto di terminazione per la connessione ExpressRoute con peer privato.</span><span class="sxs-lookup"><span data-stu-id="d266c-310">The BPG peer and termination point for the private peering ExpressRoute connection.</span></span>
    
<span data-ttu-id="d266c-311">**Figura 12: Router VPN locale o dispositivo**</span><span class="sxs-lookup"><span data-stu-id="d266c-311">**Figure 12: The on-premises VPN router or device**</span></span>

![Figura 12: Il router VPN locale o il dispositivo](images/bd221468-a660-4730-aa55-0426986480b9.png)
  
<span data-ttu-id="d266c-313">La figura 12 mostra una rete virtuale cross-premise connessa a un router o a un dispositivo VPN locale.</span><span class="sxs-lookup"><span data-stu-id="d266c-313">Figure 12 shows a cross-premises VNet connected to an on-premises VPN router or device.</span></span>
  
<span data-ttu-id="d266c-314">Per ulteriori informazioni, vedere [gateway su VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span><span class="sxs-lookup"><span data-stu-id="d266c-314">For more information, see [About VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span></span>
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a><span data-ttu-id="d266c-315">Passaggio 3: Aggiungere route alla rete intranet per rendere lo spazio degli indirizzi del VNet raggiungibili.</span><span class="sxs-lookup"><span data-stu-id="d266c-315">Step 3: Add routes to your intranet to make the address space of the VNet reachable.</span></span>

<span data-ttu-id="d266c-316">Il routing verso le reti virtuali da ambiente locale comprende i seguenti elementi:</span><span class="sxs-lookup"><span data-stu-id="d266c-316">Routing to VNets from on-premises consists of the following:</span></span>
  
1. <span data-ttu-id="d266c-317">Una route per lo spazio indirizzi della rete virtuale che punta verso il dispositivo VPN.</span><span class="sxs-lookup"><span data-stu-id="d266c-317">A route for the VNet address space that points toward your VPN device.</span></span>
    
2. <span data-ttu-id="d266c-318">Una route per lo spazio indirizzo della rete virtuale sul dispositivo VPN che punta tra la connessione VPN S2S o ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="d266c-318">A route for the VNet address space on your VPN device that points across the S2S VPN or ExpressRoute connection</span></span>
    
<span data-ttu-id="d266c-319">**Figura 13: Route locale necessari per rendere un VNet raggiungibile**</span><span class="sxs-lookup"><span data-stu-id="d266c-319">**Figure 13: The on-premises routes needed to make a VNet reachable**</span></span>

![Figura 13: Le route locali hanno dovuto rendere la rete virtuale di Azure raggiungibile](images/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
<span data-ttu-id="d266c-321">La figura 13 mostra le informazioni di routing richieste dai router locali, da quelli VPN o dal dispositivo che rappresenta lo spazio indirizzi della rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="d266c-321">Figure 13 shows the routing information needed by the on-premises routers and the VPN router or device that represents the address space of the VNet.</span></span>
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a><span data-ttu-id="d266c-322">Passaggio 4: Per ExpressRoute, pianifica la nuova connessione con il provider.</span><span class="sxs-lookup"><span data-stu-id="d266c-322">Step 4: For ExpressRoute, plan for the new connection with your provider.</span></span>

<span data-ttu-id="d266c-323">È possibile creare una connessione ExpressRoute con peering privato tra la rete locale e il cloud Microsoft in tre modi diversi:</span><span class="sxs-lookup"><span data-stu-id="d266c-323">You can create an ExpressRoute connection with private peering between your on-premises network and the Microsoft cloud in three different ways:</span></span>
  
- <span data-ttu-id="d266c-324">Percorso condiviso in un exchange cloud</span><span class="sxs-lookup"><span data-stu-id="d266c-324">Co-located at a cloud exchange</span></span>
    
- <span data-ttu-id="d266c-325">Connessioni Ethernet da punto a punto</span><span class="sxs-lookup"><span data-stu-id="d266c-325">Point-to-point Ethernet connections</span></span>
    
- <span data-ttu-id="d266c-326">Reti any-to-any (VPN IP)</span><span class="sxs-lookup"><span data-stu-id="d266c-326">Any-to-any (IP VPN) networks</span></span>
    
<span data-ttu-id="d266c-327">**Figura 14: Utilizzo ExpressRoute per connettersi a un VNet tra locali**</span><span class="sxs-lookup"><span data-stu-id="d266c-327">**Figure 14: Using ExpressRoute to connect to a cross-premises VNet**</span></span>

![Figura 14: Uso di ExpressRoute per connettersi a una rete virtuale Azure tra più sedi](images/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
<span data-ttu-id="d266c-329">La figura 14 mostra una rete virtuale cross-premise e una connessione ExpressRoute da un router locale a Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="d266c-329">Figure 14 shows a cross-premises VNet and an ExpressRoute connection from an on-premises router to Microsoft Azure.</span></span>
  
<span data-ttu-id="d266c-330">Per ulteriori informazioni, vedere [ExpressRoute per la connettività cloud Microsoft](expressroute-for-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="d266c-330">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a><span data-ttu-id="d266c-331">Passaggio 5: Determinare lo spazio di indirizzi della rete locale per il gateway di Azure.</span><span class="sxs-lookup"><span data-stu-id="d266c-331">Step 5: Determine the Local Network address space for the Azure gateway.</span></span>

<span data-ttu-id="d266c-332">Per il routing verso reti virtuali locali o di altro tipo, Azure inoltra il traffico mediante un gateway che corrisponde allo spazio di indirizzi della rete locale ad esso assegnato.</span><span class="sxs-lookup"><span data-stu-id="d266c-332">For the routing to on-premises or other VNets from a VNet, Azure forwards traffic across an Azure gateway that matches the Local Network address space assigned to the gateway.</span></span>
  
<span data-ttu-id="d266c-333">**Figura 15: La rete locale spazio degli indirizzi per un VNet tra locali**</span><span class="sxs-lookup"><span data-stu-id="d266c-333">**Figure 15: The Local Network address space for a cross-premises VNet**</span></span>

![Figura 15: Lo spazio degli indirizzi di rete locale per una rete virtuale di Azure tra più sedi](images/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
<span data-ttu-id="d266c-335">La figura 15 mostra una rete virtuale cross-premise e lo spazio indirizzi della rete locale sul gateway di Azure, che rappresenta lo spazio indirizzi raggiungibile sulla rete locale. </span><span class="sxs-lookup"><span data-stu-id="d266c-335">Figure 15 shows a cross-premises VNet and the Local Network address space on the Azure gateway, which represents the reachable address space on the on-premises network.</span></span> 
  
<span data-ttu-id="d266c-336">È possibile definire lo spazio indirizzi della rete locale nei modi seguenti:</span><span class="sxs-lookup"><span data-stu-id="d266c-336">You can define the Local Network address space in the following ways:</span></span>
  
- <span data-ttu-id="d266c-337">Opzione 1: L'elenco dei prefissi per lo spazio indirizzi corrente necessario o in uso (potrebbero essere necessari degli aggiornamenti quando si aggiungono subnet).</span><span class="sxs-lookup"><span data-stu-id="d266c-337">Option 1: The list of prefixes for the address space currently needed or in use (updates might be needed when you add new subnets).</span></span>
    
- <span data-ttu-id="d266c-338">Opzione 2: L'intero spazio di indirizzi locale (gli aggiornamenti sono necessari solo quando si aggiunge un nuovo spazio di indirizzi).</span><span class="sxs-lookup"><span data-stu-id="d266c-338">Option 2: Your entire on-premises address space (updates only needed when you add new address space).</span></span>
    
<span data-ttu-id="d266c-339">Poiché il gateway di Azure non consente route riepilogate, devi definire lo spazio di indirizzi della rete locale per l'opzione 2 affinché non includa lo spazio di indirizzi della rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="d266c-339">Because the Azure gateway does not allow summarized routes, you must define the Local Network address space for option 2 so that it does not include the VNet address space.</span></span>
  
<span data-ttu-id="d266c-340">**Figura 16: L'indirizzo spazio foro creato per lo spazio degli indirizzi VNet**</span><span class="sxs-lookup"><span data-stu-id="d266c-340">**Figure 16: The address space hole created by the VNet address space**</span></span>

![Figura 16: Hole dello spazio di indirizzi creato dallo spazio di indirizzi della rete virtuale](images/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
<span data-ttu-id="d266c-342">La figura 16 mostra una rappresentazione di uno spazio indirizzi, con lo spazio radice e lo spazio indirizzi della rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="d266c-342">Figure 16 shows a representation of an address space, with the root space and the VNet address space.</span></span>
  
<span data-ttu-id="d266c-343">Di seguito è riportato un esempio di definizione dei prefissi per lo spazio degli indirizzi di rete locale attorno lo spazio degli indirizzi "foro" creato dal VNet:</span><span class="sxs-lookup"><span data-stu-id="d266c-343">Here is an example of defining the prefixes for the Local Network address space around the address space "hole" created by the VNet:</span></span>
  
- <span data-ttu-id="d266c-p114">Un'organizzazione usa porzioni dello spazio di indirizzi privato (10.0.0.0/8, 172.16.0.0/12 e 192.168.0.0/16) nella propria rete locale. Si sceglie l'opzione 2 e 10.100.100.0/24 come spazio indirizzi della rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="d266c-p114">An organization uses portions of the private address space (10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16) across their on-premises network. They chose option 2 and 10.100.100.0/24 as their VNet address space.</span></span>
    
<span data-ttu-id="d266c-346">La tabella 7 mostra i passaggi e i prefissi risultanti che definiscono lo spazio indirizzi della rete locale per questo esempio.</span><span class="sxs-lookup"><span data-stu-id="d266c-346">Table 7 shows the steps and resulting prefixes that define the Local Network address space for this example.</span></span>
  
|<span data-ttu-id="d266c-347">**Passaggio**</span><span class="sxs-lookup"><span data-stu-id="d266c-347">**Step**</span></span>|<span data-ttu-id="d266c-348">**Risultati**</span><span class="sxs-lookup"><span data-stu-id="d266c-348">**Results**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d266c-349">1. Elencare i prefissi che non sono lo spazio radice per lo spazio indirizzi della rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="d266c-349">1. List the prefixes that are not the root space for the VNet address space.</span></span>  <br/> |<span data-ttu-id="d266c-350">172.16.0.0/12 e 192.168.0.0/16</span><span class="sxs-lookup"><span data-stu-id="d266c-350">172.16.0.0/12 and 192.168.0.0/16</span></span>  <br/> |
|<span data-ttu-id="d266c-351">2. elencare i prefissi senza sovrapposizioni per ottetti variabile fino a ma non inclusa l'ultima utilizzato</span><span class="sxs-lookup"><span data-stu-id="d266c-351">2. List the non-overlapping prefixes for variable octets up to but not including the last used</span></span> 
 <span data-ttu-id="d266c-352">ottetti nello spazio di indirizzi VNet.</span><span class="sxs-lookup"><span data-stu-id="d266c-352">octet in the VNet address space.</span></span>  <br/> |<span data-ttu-id="d266c-353">10.0.0.0/16, 10.1.0.0/16... 10.99.0.0/16, 10.101.0.0/16... 10.254.0.0/16, 10.255.0.0/16 (255 prefissi, ignorando 10.100.0.0/16)</span><span class="sxs-lookup"><span data-stu-id="d266c-353">10.0.0.0/16, 10.1.0.0/16…10.99.0.0/16, 10.101.0.0/16…10.254.0.0/16, 10.255.0.0/16 (255 prefixes, skipping 10.100.0.0/16)</span></span>  <br/> |
|<span data-ttu-id="d266c-354">3. elenco senza sovrapposizioni prefissi all'interno di</span><span class="sxs-lookup"><span data-stu-id="d266c-354">3. List the non-overlapping prefixes within the</span></span> 
 <span data-ttu-id="d266c-355">utilizzato per ultimo ottetti VNet spazio degli indirizzi.</span><span class="sxs-lookup"><span data-stu-id="d266c-355">last used octet of the VNet address space.</span></span>  <br/> <span data-ttu-id="d266c-356">| 10.100.0.0/24, 10.100.1.0/24... 10.100.99.0/24, 10.100.101.0/24... 10.100.254.0/24, 10.100.0.255.0/24 (255 prefissi, ignorando 10.100.100.0/24)</span><span class="sxs-lookup"><span data-stu-id="d266c-356">|10.100.0.0/24, 10.100.1.0/24…10.100.99.0/24, 10.100.101.0/24…10.100.254.0/24, 10.100.0.255.0/24 (255 prefixes, skipping 10.100.100.0/24)</span></span>  <br/> |
   
 <span data-ttu-id="d266c-357">**Tabella 7: Spazio di rete esempio indirizzi locali**</span><span class="sxs-lookup"><span data-stu-id="d266c-357">**Table 7: Example Local Address network space**</span></span>
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a><span data-ttu-id="d266c-358">Passaggio 6: Configurare i server DNS locali per la replica DNS con i server DNS ospitati in Azure.</span><span class="sxs-lookup"><span data-stu-id="d266c-358">Step 6: Configure on-premises DNS servers for DNS replication with DNS servers hosted in Azure.</span></span>

<span data-ttu-id="d266c-359">Per assicurarsi che i computer locali possano risolvere i nomi dei server basati su Azure e che i server basati su Azure possano risolvere i nomi dei computer locali, configurare:</span><span class="sxs-lookup"><span data-stu-id="d266c-359">To ensure that on-premises computers can resolve the names of Azure-based servers and Azure-based servers can resolve the names of on-premises computers, configure:</span></span>
  
- <span data-ttu-id="d266c-360">I server DNS nella rete virtuale per l'inoltro ai server DNS locali</span><span class="sxs-lookup"><span data-stu-id="d266c-360">The DNS servers in your VNet to forward to on-premises DNS servers</span></span>
    
- <span data-ttu-id="d266c-361">La replica DNS delle zone appropriate tra i server DNS in locale e nella rete virtuale</span><span class="sxs-lookup"><span data-stu-id="d266c-361">DNS replication of the appropriate zones between DNS servers on-premises and in the VNet</span></span>
    
<span data-ttu-id="d266c-362">**Figura 17: La replica DNS e inoltro per un server DNS in una VNet tra locali**</span><span class="sxs-lookup"><span data-stu-id="d266c-362">**Figure 17: DNS replication and forwarding for a DNS server in a cross-premises VNet**</span></span>

![Figura 17: Replica DNS e inoltro per un server DNS in una rete virtuale di Azure tra più sedi](images/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
<span data-ttu-id="d266c-p115">La figura 17 mostra una rete virtuale cross-premise con server DNS nella rete locale e su una subnet della rete virtuale. La replica e l'inoltro DNS sono stati configurati tra due server DNS.</span><span class="sxs-lookup"><span data-stu-id="d266c-p115">Figure 17 shows a cross-premises VNet with DNS servers in the on-premises network and on a subnet in the VNet. DNS replication and forwarding has been configured between the two DNS servers.</span></span>
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a><span data-ttu-id="d266c-366">Passaggio 7: Determinare l'utilizzo del tunneling forzato.</span><span class="sxs-lookup"><span data-stu-id="d266c-366">Step 7: Determine the use of forced tunneling.</span></span>

<span data-ttu-id="d266c-p116">La route di sistema predefinito per le subnet Azure punta a Internet. Per garantire che tutto il traffico da macchine virtuali passa attraverso la connessione tra locali, creare una tabella di routing con la route predefinita che utilizza il gateway Azure come relativo indirizzo hop successivo. È quindi possibile associare la tabella di route con la subnet. Questo è noto come forzato tunnel. Per ulteriori informazioni, vedere [Configure forzato tunnel](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span><span class="sxs-lookup"><span data-stu-id="d266c-p116">The default system route for Azure subnets points to the Internet. To ensure that all traffic from virtual machines travels across the cross-premises connection, create a routing table with the default route that uses the Azure gateway as its next-hop address. You then associate the route table with the subnet. This is known as forced tunneling. For more information, see [Configure forced tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span></span>
  
<span data-ttu-id="d266c-372">**Figura 18: Route definite dall'utente e tunnel forzato per un VNet tra locali**</span><span class="sxs-lookup"><span data-stu-id="d266c-372">**Figure 18: User-defined routes and forced tunneling for a cross-premises VNet**</span></span>

![Figura 18: Route definite dall'utente e tunnel forzata nella rete virtuale Azure tra più sedi](images/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
<span data-ttu-id="d266c-374">Figura 18 viene illustrata una VNet cross-premise a una route definita dall'utente per una subnet che punta al gateway di Azure.</span><span class="sxs-lookup"><span data-stu-id="d266c-374">Figure 18 shows a cross-premises VNet with a user-defined route for a subnet pointing to the Azure gateway.</span></span>
  
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="d266c-375">Farm di SharePoint Server 2016 in Azure</span><span class="sxs-lookup"><span data-stu-id="d266c-375">SharePoint Server 2016 farm in Azure</span></span>
<span data-ttu-id="d266c-376"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="d266c-376"></span></span>

<span data-ttu-id="d266c-377">Un esempio del carico di lavoro di una Intranet IT ospitata in IaaS di Azure è una farm a più livelli e a disponibilità elevata di SharePoint Server 2016, come mostrato nella figura 19.</span><span class="sxs-lookup"><span data-stu-id="d266c-377">An example of an intranet IT workload hosted in Azure IaaS is a highly-available, multi-tier SharePoint Server 2016 farm, as shown in Figure 19.</span></span>
  
<span data-ttu-id="d266c-378">**Figura 19: Una farm di SharePoint Server 2016 intranet a disponibilità elevata in Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="d266c-378">**Figure 19: A highly-available intranet SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Una farm di SharePoint Server 2016 a disponibilità elevata in IaaS di Azure](images/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
<span data-ttu-id="d266c-p117">Figura 19 mostra i nove server di una farm di SharePoint Server 2016 distribuiti in un VNet cross-premise utilizzato da servizi di bilanciamento del carico interno per i livelli front-end e i dati. Per ulteriori informazioni, tra cui progettazione dettagliate e istruzioni di distribuzione, vedere [SharePoint Server 2016 in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="d266c-p117">Figure 19 shows the nine servers of a SharePoint Server 2016 farm deployed in a cross-premises VNet that uses internal load balancers for the front-end and data tiers. For more information, including step-by-step design and deployment instructions, see [SharePoint Server 2016 in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx).</span></span>
  
> [!TIP]
> <span data-ttu-id="d266c-382">Per creare una farm di SharePoint Server 2016 a server singolo in un VNet simulato tra locali, vedere [Intranet SharePoint Server 2016 nell'ambiente di sviluppo e di testing Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="d266c-382">To create a single-server SharePoint Server 2016 farm in a simulated cross-premises VNet, see [Intranet SharePoint Server 2016 in Azure dev/test environment](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span></span> 
  
<span data-ttu-id="d266c-383">Per ulteriori esempi di carichi di lavoro IT distribuiti nelle macchine virtuali in un virtuali di Azure cross-premise di rete, vedere [scenari basati su cloud ibrida per Azure IaaS](https://technet.microsoft.com/library/mt750502.aspx).</span><span class="sxs-lookup"><span data-stu-id="d266c-383">For additional examples of IT workloads deployed on virtual machines in a cross-premises Azure virtual network, see [Hybrid cloud scenarios for Azure IaaS](https://technet.microsoft.com/library/mt750502.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d266c-384">See Also</span><span class="sxs-lookup"><span data-stu-id="d266c-384">See Also</span></span>

<span data-ttu-id="d266c-385"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="d266c-385"></span></span>

[<span data-ttu-id="d266c-386">Microsoft Cloud per architetti di rete</span><span class="sxs-lookup"><span data-stu-id="d266c-386">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="d266c-387">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="d266c-387">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="d266c-388">Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT</span><span class="sxs-lookup"><span data-stu-id="d266c-388">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


