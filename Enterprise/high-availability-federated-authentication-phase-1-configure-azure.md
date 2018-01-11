---
title: "Fase 1 configurare Azure l'autenticazione federata la disponibilità elevata"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: "Riepilogo: Configurare l'infrastruttura Microsoft Azure per la disponibilità elevata host l'autenticazione federata per Office 365."
ms.openlocfilehash: f74e91930f5aef8f10986dcf51db6066c953014d
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a><span data-ttu-id="4fc62-103">Fase 1 dell'autenticazione federata a disponibilità elevata: Configurare Azure</span><span class="sxs-lookup"><span data-stu-id="4fc62-103">High availability federated authentication Phase 1: Configure Azure</span></span>

 <span data-ttu-id="4fc62-104">**Riepilogo:** Configurare l'infrastruttura Microsoft Azure per l'autenticazione di disponibilità elevata federate host per Office 365.</span><span class="sxs-lookup"><span data-stu-id="4fc62-104">**Summary:** Configure the Microsoft Azure infrastructure to host high availability federated authentication for Office 365.</span></span>
  
<span data-ttu-id="4fc62-p101">In questa fase, verrà creato i gruppi di risorse, gli account di archiviazione, set di rete (VNet) e la disponibilità virtuali di Azure che ospiterà le macchine virtuali in fasi 2, 3 e 4. È necessario completare prima di spostare in questa fase [la disponibilità elevata federati autenticazione fase 2: configurare i controller di dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Per tutte le fasi, vedere [Deploy la disponibilità elevata nell'autenticazione federata per Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) .</span><span class="sxs-lookup"><span data-stu-id="4fc62-p101">In this phase, you create the resource groups, storage accounts, virtual network (VNet), and availability sets in Azure that will host the virtual machines in phases 2, 3, and 4. You must complete this phase before moving on to [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
<span data-ttu-id="4fc62-108">Deve essere fornite da Azure con componenti di base seguenti:</span><span class="sxs-lookup"><span data-stu-id="4fc62-108">Azure must be provisioned with these basic components:</span></span>
  
- <span data-ttu-id="4fc62-109">Gruppi di risorse</span><span class="sxs-lookup"><span data-stu-id="4fc62-109">Resource groups</span></span>
    
- <span data-ttu-id="4fc62-110">Una rete virtuale (VNet) Azure cross-premise con subnet per ospitare le macchine virtuali di Azure</span><span class="sxs-lookup"><span data-stu-id="4fc62-110">A cross-premises Azure virtual network (VNet) with subnets for hosting the Azure virtual machines</span></span>
    
- <span data-ttu-id="4fc62-111">Gruppi di sicurezza di rete per l'esecuzione dell'isolamento delle subnet</span><span class="sxs-lookup"><span data-stu-id="4fc62-111">Network security groups for performing subnet isolation</span></span>
    
- <span data-ttu-id="4fc62-112">Set di disponibilità</span><span class="sxs-lookup"><span data-stu-id="4fc62-112">Availability sets</span></span>
    
## <a name="configure-azure-components"></a><span data-ttu-id="4fc62-113">Configurare i componenti di Azure</span><span class="sxs-lookup"><span data-stu-id="4fc62-113">Configure Azure components</span></span>

<span data-ttu-id="4fc62-p102">Prima di iniziare la configurazione dei componenti Azure, del riempimento nelle tabelle seguenti. Per facilitare le procedure per la configurazione di Azure, in questa sezione di stampa e prendere nota delle informazioni necessarie o copiare in questa sezione di un documento e completare. Per le impostazioni del VNet, compilare tabella V.</span><span class="sxs-lookup"><span data-stu-id="4fc62-p102">Before you begin configuring Azure components, fill in the following tables. To assist you in the procedures for configuring Azure, print this section and write down the needed information or copy this section to a document and fill it in. For the settings of the VNet, fill in Table V.</span></span>
  
|<span data-ttu-id="4fc62-117">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="4fc62-117">**Item**</span></span>|<span data-ttu-id="4fc62-118">**Impostazione di configurazione**</span><span class="sxs-lookup"><span data-stu-id="4fc62-118">**Configuration setting**</span></span>|<span data-ttu-id="4fc62-119">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="4fc62-119">**Description**</span></span>|<span data-ttu-id="4fc62-120">**Valore**</span><span class="sxs-lookup"><span data-stu-id="4fc62-120">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="4fc62-121">1.</span><span class="sxs-lookup"><span data-stu-id="4fc62-121">1.</span></span>  <br/> |<span data-ttu-id="4fc62-122">Nome VNet</span><span class="sxs-lookup"><span data-stu-id="4fc62-122">VNet name</span></span>  <br/> |<span data-ttu-id="4fc62-123">Un nome da assegnare alla VNet (ad esempio, FedAuthNet).</span><span class="sxs-lookup"><span data-stu-id="4fc62-123">A name to assign to the VNet (example FedAuthNet).</span></span>  <br/> |<span data-ttu-id="4fc62-124">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-124"></span></span>  <br/> |
|<span data-ttu-id="4fc62-125">2.</span><span class="sxs-lookup"><span data-stu-id="4fc62-125">2.</span></span>  <br/> |<span data-ttu-id="4fc62-126">Percorso VNet</span><span class="sxs-lookup"><span data-stu-id="4fc62-126">VNet location</span></span>  <br/> |<span data-ttu-id="4fc62-127">Data center di Azure regionale che conterrà la rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="4fc62-127">The regional Azure datacenter that will contain the virtual network.</span></span>  <br/> |<span data-ttu-id="4fc62-128">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-128"></span></span>  <br/> |
|<span data-ttu-id="4fc62-129">3.</span><span class="sxs-lookup"><span data-stu-id="4fc62-129">3.</span></span>  <br/> |<span data-ttu-id="4fc62-130">Indirizzo IP del dispositivo VPN</span><span class="sxs-lookup"><span data-stu-id="4fc62-130">VPN device IP address</span></span>  <br/> |<span data-ttu-id="4fc62-131">L'indirizzo IPv4 pubblico dell'interfaccia del dispositivo VPN su Internet. </span><span class="sxs-lookup"><span data-stu-id="4fc62-131">The public IPv4 address of your VPN device's interface on the Internet.</span></span>  <br/> |<span data-ttu-id="4fc62-132">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-132"></span></span>  <br/> |
|<span data-ttu-id="4fc62-133">4.</span><span class="sxs-lookup"><span data-stu-id="4fc62-133">4.</span></span>  <br/> |<span data-ttu-id="4fc62-134">Spazio di indirizzi della VNet</span><span class="sxs-lookup"><span data-stu-id="4fc62-134">VNet address space</span></span>  <br/> |<span data-ttu-id="4fc62-p103">Lo spazio di indirizzi della rete virtuale. Consultare il proprio reparto IT per determinare tale spazio di indirizzi.</span><span class="sxs-lookup"><span data-stu-id="4fc62-p103">The address space for the virtual network. Work with your IT department to determine this address space.</span></span>  <br/> |<span data-ttu-id="4fc62-137">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-137"></span></span>  <br/> |
|<span data-ttu-id="4fc62-138">5.</span><span class="sxs-lookup"><span data-stu-id="4fc62-138">5.</span></span>  <br/> |<span data-ttu-id="4fc62-139">Chiave condivisa IPsec</span><span class="sxs-lookup"><span data-stu-id="4fc62-139">IPsec shared key</span></span>  <br/> |<span data-ttu-id="4fc62-p104">32 caratteri alfanumerici casuale stringa che verrà utilizzata per autenticare entrambi i lati della connessione VPN da sito. Lavorare con le IT o un reparto di sicurezza per determinare il valore della chiave. In alternativa, vedere [creazione di una stringa casuale per una chiave già condivisa IPsec](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).</span><span class="sxs-lookup"><span data-stu-id="4fc62-p104">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value. Alternately, see [Create a random string for an IPsec preshared key](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |<span data-ttu-id="4fc62-143">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-143"></span></span>  <br/> |
   
 <span data-ttu-id="4fc62-144">**Tabella V: configurazione di una rete virtuale cross-premise**</span><span class="sxs-lookup"><span data-stu-id="4fc62-144">**Table V: Cross-premises virtual network configuration**</span></span>
  
<span data-ttu-id="4fc62-p105">Successivamente, compilare la tabella S per le subnet della soluzione. Tutti gli spazi di indirizzi devono essere in formato CIDR (Classless Interdomain Routing), noto anche come formato del prefisso di rete. Ad esempio, 10.24.64.0/20.</span><span class="sxs-lookup"><span data-stu-id="4fc62-p105">Next, fill in Table S for the subnets of this solution. All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>
  
<span data-ttu-id="4fc62-p106">Per le prime tre subnet, specificare un nome e un singolo spazio di indirizzi IP in base allo spazio di indirizzi di rete virtuale. Per la prima subnet del gateway, determinare lo spazio di indirizzi a 27 bit (con una lunghezza del prefisso di /27) per la subnet del gateway di Azure con quanto segue:</span><span class="sxs-lookup"><span data-stu-id="4fc62-p106">For the first three subnets, specify a name and a single IP address space based on the virtual network address space. For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span></span>
  
1. <span data-ttu-id="4fc62-150">Impostare i bit variabili nello spazio di indirizzi della VNet su 1, fino ai bit utilizzati dalla subnet del gateway, quindi impostare i bit rimanenti su 0.</span><span class="sxs-lookup"><span data-stu-id="4fc62-150">Set the variable bits in the address space of the VNet to 1, up to the bits being used by the gateway subnet, then set the remaining bits to 0.</span></span>
    
2. <span data-ttu-id="4fc62-151">Convertire i bit risultanti in formato decimale ed esprimerli come spazio di indirizzi con la lunghezza del prefisso impostata sulle dimensioni della subnet del gateway.</span><span class="sxs-lookup"><span data-stu-id="4fc62-151">Convert the resulting bits to decimal and express it as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="4fc62-152">Per un blocco di comandi di PowerShell e applicazione console c# o Python utilizzato per eseguire tale calcolo automaticamente, vedere [la calcolatrice spazio indirizzo per le subnet gateway Azure](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) .</span><span class="sxs-lookup"><span data-stu-id="4fc62-152">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for a PowerShell command block and C# or Python console application that performs this calculation for you.</span></span>
  
<span data-ttu-id="4fc62-153">Consultare il reparto IT per determinare tali spazi di indirizzi in base allo spazio di indirizzi della rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="4fc62-153">Work with your IT department to determine these address spaces from the virtual network address space.</span></span>
  
|<span data-ttu-id="4fc62-154">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="4fc62-154">**Item**</span></span>|<span data-ttu-id="4fc62-155">**Nome della subnet**</span><span class="sxs-lookup"><span data-stu-id="4fc62-155">**Subnet name**</span></span>|<span data-ttu-id="4fc62-156">**Spazio di indirizzi della subnet**</span><span class="sxs-lookup"><span data-stu-id="4fc62-156">**Subnet address space**</span></span>|<span data-ttu-id="4fc62-157">**Scopo**</span><span class="sxs-lookup"><span data-stu-id="4fc62-157">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="4fc62-158">1.</span><span class="sxs-lookup"><span data-stu-id="4fc62-158">1.</span></span>  <br/> |<span data-ttu-id="4fc62-159">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-159"></span></span>  <br/> |<span data-ttu-id="4fc62-160">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-160"></span></span>  <br/> |<span data-ttu-id="4fc62-161">La subnet utilizzata dal controller di dominio Windows Server Active Directory (AD) e le macchine virtuali (VMs) del server DirSync.</span><span class="sxs-lookup"><span data-stu-id="4fc62-161">The subnet used by the Windows Server Active Directory (AD) domain controller and DirSync server virtual machines (VMs).</span></span>  <br/> |
|<span data-ttu-id="4fc62-162">2.</span><span class="sxs-lookup"><span data-stu-id="4fc62-162">2.</span></span>  <br/> |<span data-ttu-id="4fc62-163">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-163"></span></span>  <br/> |<span data-ttu-id="4fc62-164">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-164"></span></span>  <br/> |<span data-ttu-id="4fc62-165">La subnet utilizzata dalle macchine virtuali di AD FS.</span><span class="sxs-lookup"><span data-stu-id="4fc62-165">The subnet used by the AD FS VMs.</span></span>  <br/> |
|<span data-ttu-id="4fc62-166">3.</span><span class="sxs-lookup"><span data-stu-id="4fc62-166">3.</span></span>  <br/> |<span data-ttu-id="4fc62-167">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-167"></span></span>  <br/> |<span data-ttu-id="4fc62-168">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-168"></span></span>  <br/> |<span data-ttu-id="4fc62-169">La subnet utilizzata dalle macchine virtuali del proxy di applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="4fc62-169">The subnet used by the web application proxy VMs.</span></span>  <br/> |
|<span data-ttu-id="4fc62-170">4.</span><span class="sxs-lookup"><span data-stu-id="4fc62-170">4.</span></span>  <br/> |<span data-ttu-id="4fc62-171">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="4fc62-171">GatewaySubnet</span></span>  <br/> |<span data-ttu-id="4fc62-172">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-172"></span></span>  <br/> |<span data-ttu-id="4fc62-173">La subnet utilizzata dalle macchine virtuali del gateway di Azure.</span><span class="sxs-lookup"><span data-stu-id="4fc62-173">The subnet used by the Azure gateway VMs.</span></span>  <br/> |
   
 <span data-ttu-id="4fc62-174">**Tabella S: subnet nella rete virtuale**</span><span class="sxs-lookup"><span data-stu-id="4fc62-174">**Table S: Subnets in the virtual network**</span></span>
  
<span data-ttu-id="4fc62-175">Successivamente, compilare la tabella I per gli indirizzi IP statici assegnati alle macchine virtuali e alle istanze del bilanciamento del carico.</span><span class="sxs-lookup"><span data-stu-id="4fc62-175">Next, fill in Table I for the static IP addresses assigned to virtual machines and load balancer instances.</span></span>
  
|<span data-ttu-id="4fc62-176">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="4fc62-176">**Item**</span></span>|<span data-ttu-id="4fc62-177">**Scopo**</span><span class="sxs-lookup"><span data-stu-id="4fc62-177">**Purpose**</span></span>|<span data-ttu-id="4fc62-178">**Indirizzo IP della subnet**</span><span class="sxs-lookup"><span data-stu-id="4fc62-178">**IP address on the subnet**</span></span>|<span data-ttu-id="4fc62-179">**Valore**</span><span class="sxs-lookup"><span data-stu-id="4fc62-179">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="4fc62-180">1.</span><span class="sxs-lookup"><span data-stu-id="4fc62-180">1.</span></span>  <br/> |<span data-ttu-id="4fc62-181">Indirizzo IP statico del primo controller di dominio</span><span class="sxs-lookup"><span data-stu-id="4fc62-181">Static IP address of the first domain controller</span></span>  <br/> |<span data-ttu-id="4fc62-182">Il quarto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 1 della tabella S.</span><span class="sxs-lookup"><span data-stu-id="4fc62-182">The fourth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="4fc62-183">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-183"></span></span>  <br/> |
|<span data-ttu-id="4fc62-184">2.</span><span class="sxs-lookup"><span data-stu-id="4fc62-184">2.</span></span>  <br/> |<span data-ttu-id="4fc62-185">Indirizzo IP statico del secondo controller di dominio</span><span class="sxs-lookup"><span data-stu-id="4fc62-185">Static IP address of the second domain controller</span></span>  <br/> |<span data-ttu-id="4fc62-186">Il quinto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 1 della tabella S.</span><span class="sxs-lookup"><span data-stu-id="4fc62-186">The fifth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="4fc62-187">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-187"></span></span>  <br/> |
|<span data-ttu-id="4fc62-188">3.</span><span class="sxs-lookup"><span data-stu-id="4fc62-188">3.</span></span>  <br/> |<span data-ttu-id="4fc62-189">Indirizzo IP statico del server DirSync</span><span class="sxs-lookup"><span data-stu-id="4fc62-189">Static IP address of the DirSync server</span></span>  <br/> |<span data-ttu-id="4fc62-190">Il sesto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 1 della tabella S. </span><span class="sxs-lookup"><span data-stu-id="4fc62-190">The sixth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="4fc62-191">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-191"></span></span>  <br/> |
|<span data-ttu-id="4fc62-192">4.</span><span class="sxs-lookup"><span data-stu-id="4fc62-192">4.</span></span>  <br/> |<span data-ttu-id="4fc62-193">Indirizzo IP statico del bilanciamento del carico interno per i server AD FS</span><span class="sxs-lookup"><span data-stu-id="4fc62-193">Static IP address of the internal load balancer for the AD FS servers</span></span>  <br/> |<span data-ttu-id="4fc62-194">Il quarto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 2 della tabella S. </span><span class="sxs-lookup"><span data-stu-id="4fc62-194">The fourth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="4fc62-195">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-195"></span></span>  <br/> |
|<span data-ttu-id="4fc62-196">5.</span><span class="sxs-lookup"><span data-stu-id="4fc62-196">5.</span></span>  <br/> |<span data-ttu-id="4fc62-197">Indirizzo IP statico del primo server AD FS</span><span class="sxs-lookup"><span data-stu-id="4fc62-197">Static IP address of the first AD FS server</span></span>  <br/> |<span data-ttu-id="4fc62-198">Il quinto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 2 della tabella S.</span><span class="sxs-lookup"><span data-stu-id="4fc62-198">The fifth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="4fc62-199">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-199"></span></span>  <br/> |
|<span data-ttu-id="4fc62-200">6.</span><span class="sxs-lookup"><span data-stu-id="4fc62-200">6.</span></span>  <br/> |<span data-ttu-id="4fc62-201">Indirizzo IP statico del secondo server AD FS</span><span class="sxs-lookup"><span data-stu-id="4fc62-201">Static IP address of the second AD FS server</span></span>  <br/> |<span data-ttu-id="4fc62-202">Il sesto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 2 della tabella S.</span><span class="sxs-lookup"><span data-stu-id="4fc62-202">The sixth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="4fc62-203">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-203"></span></span>  <br/> |
|<span data-ttu-id="4fc62-204">7.</span><span class="sxs-lookup"><span data-stu-id="4fc62-204">7.</span></span>  <br/> |<span data-ttu-id="4fc62-205">Indirizzo IP statico del primo server proxy dell'applicazione Web</span><span class="sxs-lookup"><span data-stu-id="4fc62-205">Static IP address of the first web application proxy server</span></span>  <br/> |<span data-ttu-id="4fc62-206">Il quarto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 3 della tabella S.</span><span class="sxs-lookup"><span data-stu-id="4fc62-206">The fourth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |<span data-ttu-id="4fc62-207">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-207"></span></span>  <br/> |
|<span data-ttu-id="4fc62-208">8.</span><span class="sxs-lookup"><span data-stu-id="4fc62-208">8.</span></span>  <br/> |<span data-ttu-id="4fc62-209">Indirizzo IP statico del secondo server proxy dell'applicazione Web</span><span class="sxs-lookup"><span data-stu-id="4fc62-209">Static IP address of the second web application proxy server</span></span>  <br/> |<span data-ttu-id="4fc62-210">Il quinto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 3 della tabella S.</span><span class="sxs-lookup"><span data-stu-id="4fc62-210">The fifth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |<span data-ttu-id="4fc62-211">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-211"></span></span>  <br/> |
   
 <span data-ttu-id="4fc62-212">**Indirizzi IP statici i: tabella nella rete virtuale**</span><span class="sxs-lookup"><span data-stu-id="4fc62-212">**Table I: Static IP addresses in the virtual network**</span></span>
  
<span data-ttu-id="4fc62-213">Per due server DNS (Domain Name System) nella rete locale che si desidera utilizzare durante la configurazione iniziale dei controller di dominio nella rete virtuale, compilare la tabella D. Consultare il reparto IT per determinare questo elenco.</span><span class="sxs-lookup"><span data-stu-id="4fc62-213">For two Domain Name System (DNS) servers in your on-premises network that you want to use when initially setting up the domain controllers in your virtual network, fill in Table D. Work with your IT department to determine this list.</span></span>
  
|<span data-ttu-id="4fc62-214">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="4fc62-214">**Item**</span></span>|<span data-ttu-id="4fc62-215">**Nome descrittivo del server DNS**</span><span class="sxs-lookup"><span data-stu-id="4fc62-215">**DNS server friendly name**</span></span>|<span data-ttu-id="4fc62-216">**Indirizzo IP del server DNS**</span><span class="sxs-lookup"><span data-stu-id="4fc62-216">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="4fc62-217">1.</span><span class="sxs-lookup"><span data-stu-id="4fc62-217">1.</span></span>  <br/> |<span data-ttu-id="4fc62-218">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-218"></span></span>  <br/> |<span data-ttu-id="4fc62-219">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-219"></span></span>  <br/> |
|<span data-ttu-id="4fc62-220">2.</span><span class="sxs-lookup"><span data-stu-id="4fc62-220">2.</span></span>  <br/> |<span data-ttu-id="4fc62-221">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-221"></span></span>  <br/> |<span data-ttu-id="4fc62-222">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-222"></span></span>  <br/> |
   
 <span data-ttu-id="4fc62-223">**Tabella D: server DNS locali**</span><span class="sxs-lookup"><span data-stu-id="4fc62-223">**Table D: On-premises DNS servers**</span></span>
  
<span data-ttu-id="4fc62-p107">Per instradare i pacchetti dalla rete cross-premise alla rete aziendale tramite la connessione VPN da sito a sito, è necessario configurare la rete virtuale con una rete locale contenente un elenco degli spazi di indirizzi (in notazione CIDR) per tutti i percorsi raggiungibili nella rete locale dell'organizzazione. L'elenco degli spazi di indirizzi che definiscono la rete locale deve essere univoco e non deve sovrapporsi con lo spazio di indirizzi utilizzato per altre reti virtuali o per altre reti locali.</span><span class="sxs-lookup"><span data-stu-id="4fc62-p107">To route packets from the cross-premises network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network that contains a list of the address spaces (in CIDR notation) for all of the reachable locations on your organization's on-premises network. The list of address spaces that define your local network must be unique and must not overlap with the address space used for other virtual networks or other local networks.</span></span>
  
<span data-ttu-id="4fc62-p108">Per l'insieme degli spazi di indirizzi della rete locale, compilare la tabella L. Sono elencate tre voci vuote, ma sarà necessario aggiungerne altre. Consultare il proprio reparto IT per determinare questo elenco di spazi di indirizzi.</span><span class="sxs-lookup"><span data-stu-id="4fc62-p108">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list of address spaces.</span></span>
  
|<span data-ttu-id="4fc62-228">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="4fc62-228">**Item**</span></span>|<span data-ttu-id="4fc62-229">**Spazio di indirizzi della rete locale**</span><span class="sxs-lookup"><span data-stu-id="4fc62-229">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="4fc62-230">1.</span><span class="sxs-lookup"><span data-stu-id="4fc62-230">1.</span></span>  <br/> |<span data-ttu-id="4fc62-231">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-231"></span></span>  <br/> |
|<span data-ttu-id="4fc62-232">2.</span><span class="sxs-lookup"><span data-stu-id="4fc62-232">2.</span></span>  <br/> |<span data-ttu-id="4fc62-233">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-233"></span></span>  <br/> |
|<span data-ttu-id="4fc62-234">3.</span><span class="sxs-lookup"><span data-stu-id="4fc62-234">3.</span></span>  <br/> |<span data-ttu-id="4fc62-235">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-235"></span></span>  <br/> |
   
 <span data-ttu-id="4fc62-236">**Tabella L: prefissi degli indirizzi per la rete locale**</span><span class="sxs-lookup"><span data-stu-id="4fc62-236">**Table L: Address prefixes for the local network**</span></span>
  
<span data-ttu-id="4fc62-237">Iniziamo a creare l'infrastruttura di Azure per ospitare l'autenticazione federata di Office 365.</span><span class="sxs-lookup"><span data-stu-id="4fc62-237">Now let's begin building the Azure infrastructure to host your federated authentication for Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="4fc62-p109">Il seguente comando consente di utilizzare la versione più recente di Azure PowerShell. Vedere [iniziare a utilizzare i cmdlet PowerShell di Azure](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="4fc62-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="4fc62-240">Avviare un prompt dei comandi di Azure PowerShell e accedere al proprio account.</span><span class="sxs-lookup"><span data-stu-id="4fc62-240">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="4fc62-241">Per un file di testo che contiene tutti i comandi di PowerShell in questo articolo e una cartella di lavoro configurazione Microsoft Excel che genera pronto a portata di blocchi di comandi di PowerShell in base alle impostazioni personalizzate, vedere [autenticazione federata per Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="4fc62-241">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
<span data-ttu-id="4fc62-242">Ottenere il nome della sottoscrizione utilizzando il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="4fc62-242">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="4fc62-243">Per le versioni precedenti di Azure PowerShell, utilizzare questo comando.</span><span class="sxs-lookup"><span data-stu-id="4fc62-243">For older versions of Azure PowerShell, use this command instead.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select SubscriptionName
```

<span data-ttu-id="4fc62-p110">Impostare la sottoscrizione di Azure. Sostituire tutte le virgolette, incluse le \< e > caratteri, con il nome corretto.</span><span class="sxs-lookup"><span data-stu-id="4fc62-p110">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="4fc62-p111">Successivamente, creare i nuovi gruppi di risorse. Per determinare un set di nomi dei gruppi di risorse univoci, utilizzare questo comando per creare un elenco dei gruppi di risorse esistenti.</span><span class="sxs-lookup"><span data-stu-id="4fc62-p111">Next, create the new resource groups. To determine a unique set of resource group names, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="4fc62-248">Compilare la tabella seguente per il set di nomi dei gruppi di risorse univoci.</span><span class="sxs-lookup"><span data-stu-id="4fc62-248">Fill in the following table for the set of unique resource group names.</span></span>
  
|<span data-ttu-id="4fc62-249">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="4fc62-249">**Item**</span></span>|<span data-ttu-id="4fc62-250">**Nome del gruppo di risorse**</span><span class="sxs-lookup"><span data-stu-id="4fc62-250">**Resource group name**</span></span>|<span data-ttu-id="4fc62-251">**Scopo**</span><span class="sxs-lookup"><span data-stu-id="4fc62-251">**Purpose**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="4fc62-252">1.</span><span class="sxs-lookup"><span data-stu-id="4fc62-252">1.</span></span>  <br/> |<span data-ttu-id="4fc62-253">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-253"></span></span>  <br/> |<span data-ttu-id="4fc62-254">Controller di dominio</span><span class="sxs-lookup"><span data-stu-id="4fc62-254">Domain controllers</span></span>  <br/> |
|<span data-ttu-id="4fc62-255">2.</span><span class="sxs-lookup"><span data-stu-id="4fc62-255">2.</span></span>  <br/> |<span data-ttu-id="4fc62-256">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-256"></span></span>  <br/> |<span data-ttu-id="4fc62-257">Server AD FS</span><span class="sxs-lookup"><span data-stu-id="4fc62-257">AD FS servers</span></span>  <br/> |
|<span data-ttu-id="4fc62-258">3.</span><span class="sxs-lookup"><span data-stu-id="4fc62-258">3.</span></span>  <br/> |<span data-ttu-id="4fc62-259">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-259"></span></span>  <br/> |<span data-ttu-id="4fc62-260">Server proxy di applicazione Web</span><span class="sxs-lookup"><span data-stu-id="4fc62-260">Web application proxy servers</span></span>  <br/> |
|<span data-ttu-id="4fc62-261">4.</span><span class="sxs-lookup"><span data-stu-id="4fc62-261">4.</span></span>  <br/> |<span data-ttu-id="4fc62-262">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-262"></span></span>  <br/> |<span data-ttu-id="4fc62-263">Elementi dell'infrastruttura</span><span class="sxs-lookup"><span data-stu-id="4fc62-263">Infrastructure elements</span></span>  <br/> |
   
 <span data-ttu-id="4fc62-264">**Tabella r: gruppi di risorse**</span><span class="sxs-lookup"><span data-stu-id="4fc62-264">**Table R: Resource groups**</span></span>
  
<span data-ttu-id="4fc62-265">Creare i nuovi gruppi di risorse con questi comandi.</span><span class="sxs-lookup"><span data-stu-id="4fc62-265">Create your new resource groups with these commands.</span></span>
  
```
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="4fc62-266">Successivamente, creare la rete virtuale di Azure e le relative subnet.</span><span class="sxs-lookup"><span data-stu-id="4fc62-266">Next, you create the Azure virtual network and its subnets.</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzureRmResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

<span data-ttu-id="4fc62-p112">È quindi creare rete gruppi di sicurezza per ogni subnet che contiene le macchine virtuali. Per eseguire isolamento subnet, è possibile aggiungere regole per specifici tipi di traffico concesse o negate al gruppo di protezione di rete di una subnet.</span><span class="sxs-lookup"><span data-stu-id="4fc62-p112">Next, you create network security groups for each subnet that contains virtual machines. To perform subnet isolation, you can add rules for the specific types of traffic allowed or denied to the network security group of a subnet.</span></span>
  
```
# Create network security groups
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
```

<span data-ttu-id="4fc62-269">Successivamente, utilizzare questi comandi per creare i gateway per la connessione VPN da sito a sito.</span><span class="sxs-lookup"><span data-stu-id="4fc62-269">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzureRMVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzureRMVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzureRMLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzureRMVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> <span data-ttu-id="4fc62-p113">Le risorse locali non utilizzano l'autenticazione federata dei singoli utenti. Tuttavia, se la connessione VPN da sito risulta disponibile, i controller di dominio di VNet non riceverà aggiornamenti agli account utente e gruppi apportati in locale Windows Server Active Directory. Per garantire che non accade, è possibile configurare la disponibilità elevata per la connessione di rete VPN del sito per sito. Per ulteriori informazioni, vedere [altamente disponibili tra locali e la connettività VNet-VNet](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="4fc62-p113">Federated authentication of individual users does not rely on any on-premises resources. However, if this site-to-site VPN connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your site-to-site VPN connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="4fc62-274">Successivamente, registrare l'indirizzo IPv4 pubblico del gateway VPN di Azure per la rete virtuale visualizzato con questo comando:</span><span class="sxs-lookup"><span data-stu-id="4fc62-274">Next, record the public IPv4 address of the Azure VPN gateway for your virtual network from the display of this command:</span></span>
  
```
Get-AzureRMPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

<span data-ttu-id="4fc62-p114">Configurare quindi il dispositivo VPN in locale per la connessione al gateway VPN Azure. Per ulteriori informazioni, vedere [configurare il dispositivo VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="4fc62-p114">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="4fc62-277">Per configurare il dispositivo VPN locale, è necessario quanto segue:</span><span class="sxs-lookup"><span data-stu-id="4fc62-277">To configure your on-premises VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="4fc62-278">L'indirizzo IPv4 pubblico del gateway VPN di Azure.</span><span class="sxs-lookup"><span data-stu-id="4fc62-278">The public IPv4 address of the Azure VPN gateway.</span></span>
    
- <span data-ttu-id="4fc62-279">Il tasto già condiviso IPsec per la connessione VPN da sito (colonna di tabella V - elemento 5 - valore).</span><span class="sxs-lookup"><span data-stu-id="4fc62-279">The IPsec pre-shared key for the site-to-site VPN connection (Table V - Item 5 - Value column).</span></span>
    
<span data-ttu-id="4fc62-p115">Successivamente, assicurarsi che lo spazio di indirizzi della rete virtuale sia raggiungibile dalla rete locale. In genere è possibile aggiungere una route corrispondente allo spazio di indirizzi di rete virtuali al dispositivo VPN e quindi distribuire tale route al resto dell'infrastruttura di routing della rete dell'organizzazione. A tale scopo, consultare il proprio reparto IT.</span><span class="sxs-lookup"><span data-stu-id="4fc62-p115">Next, ensure that the address space of the virtual network is reachable from your on-premises network. This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network. Work with your IT department to determine how to do this.</span></span>
  
<span data-ttu-id="4fc62-p116">Successivamente, definire i nomi di tre set di disponibilità. Compilare la tabella A. </span><span class="sxs-lookup"><span data-stu-id="4fc62-p116">Next, define the names of three availability sets. Fill out Table A.</span></span> 
  
|<span data-ttu-id="4fc62-285">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="4fc62-285">**Item**</span></span>|<span data-ttu-id="4fc62-286">**Scopo**</span><span class="sxs-lookup"><span data-stu-id="4fc62-286">**Purpose**</span></span>|<span data-ttu-id="4fc62-287">**Nome del set di disponibilità**</span><span class="sxs-lookup"><span data-stu-id="4fc62-287">**Availability set name**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="4fc62-288">1.</span><span class="sxs-lookup"><span data-stu-id="4fc62-288">1.</span></span>  <br/> |<span data-ttu-id="4fc62-289">Controller di dominio</span><span class="sxs-lookup"><span data-stu-id="4fc62-289">Domain controllers</span></span>  <br/> |<span data-ttu-id="4fc62-290">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-290"></span></span>  <br/> |
|<span data-ttu-id="4fc62-291">2.</span><span class="sxs-lookup"><span data-stu-id="4fc62-291">2.</span></span>  <br/> |<span data-ttu-id="4fc62-292">Server AD FS</span><span class="sxs-lookup"><span data-stu-id="4fc62-292">AD FS servers</span></span>  <br/> |<span data-ttu-id="4fc62-293">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-293"></span></span>  <br/> |
|<span data-ttu-id="4fc62-294">3.</span><span class="sxs-lookup"><span data-stu-id="4fc62-294">3.</span></span>  <br/> |<span data-ttu-id="4fc62-295">Server proxy di applicazione Web</span><span class="sxs-lookup"><span data-stu-id="4fc62-295">Web application proxy servers</span></span>  <br/> |<span data-ttu-id="4fc62-296">_______________________________</span><span class="sxs-lookup"><span data-stu-id="4fc62-296"></span></span>  <br/> |
   
 <span data-ttu-id="4fc62-297">**Set di disponibilità a: tabella**</span><span class="sxs-lookup"><span data-stu-id="4fc62-297">**Table A: Availability sets**</span></span>
  
<span data-ttu-id="4fc62-298">Questi nomi sono necessari quando si creano le macchine virtuali nelle fasi 2, 3 e 4.</span><span class="sxs-lookup"><span data-stu-id="4fc62-298">You will need these names when you create the virtual machines in phases 2, 3, and 4.</span></span>
  
<span data-ttu-id="4fc62-299">Creare i nuovi set di disponibilità con questi comandi di Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4fc62-299">Create the new availability sets with these Azure PowerShell commands.</span></span>
  
```
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
```

<span data-ttu-id="4fc62-300">Questa è la configurazione risultante dal completamento corretto di questa fase.</span><span class="sxs-lookup"><span data-stu-id="4fc62-300">This is the configuration resulting from the successful completion of this phase.</span></span>
  
<span data-ttu-id="4fc62-301">**Fase 1: L'infrastruttura per l'autenticazione federata di disponibilità elevata per Office 365**</span><span class="sxs-lookup"><span data-stu-id="4fc62-301">**Phase 1: The Azure infrastructure for high availability federated authentication for Office 365**</span></span>

![Fase 1 dell'autenticazione federata di Office 365 con disponibilità elevata in Azure con l'infrastruttura di Azure](images/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a><span data-ttu-id="4fc62-303">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="4fc62-303">Next step</span></span>

<span data-ttu-id="4fc62-304">Utilizzare [la disponibilità elevata federati autenticazione fase 2: configurare i controller di dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) per continuare con la configurazione di questo carico di lavoro.</span><span class="sxs-lookup"><span data-stu-id="4fc62-304">Use [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) to continue with the configuration of this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4fc62-305">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4fc62-305">See Also</span></span>

[<span data-ttu-id="4fc62-306">Distribuire l'autenticazione federata ad alta visibilità per Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="4fc62-306">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="4fc62-307">Identità federata per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="4fc62-307">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="4fc62-308">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="4fc62-308">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="4fc62-309">Identità federata per Office 365</span><span class="sxs-lookup"><span data-stu-id="4fc62-309">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


