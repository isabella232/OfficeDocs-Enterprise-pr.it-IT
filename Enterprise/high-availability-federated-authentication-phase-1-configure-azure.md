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
ms.openlocfilehash: 829bad1dadc3c3987e42d32f8afe8c1f76459ff0
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a><span data-ttu-id="cd692-103">Fase 1 dell'autenticazione federata a disponibilità elevata: Configurare Azure</span><span class="sxs-lookup"><span data-stu-id="cd692-103">High availability federated authentication Phase 1: Configure Azure</span></span>

 <span data-ttu-id="cd692-104">**Riepilogo:** Configurare l'infrastruttura Microsoft Azure per l'autenticazione di disponibilità elevata federate host per Office 365.</span><span class="sxs-lookup"><span data-stu-id="cd692-104">**Summary:** Configure the Microsoft Azure infrastructure to host high availability federated authentication for Office 365.</span></span>
  
<span data-ttu-id="cd692-p101">In questa fase, verrà creato i gruppi di risorse, gli account di archiviazione, set di rete (VNet) e la disponibilità virtuali di Azure che ospiterà le macchine virtuali in fasi 2, 3 e 4. È necessario completare prima di spostare in questa fase [la disponibilità elevata federati autenticazione fase 2: configurare i controller di dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Per tutte le fasi, vedere [Deploy la disponibilità elevata nell'autenticazione federata per Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) .</span><span class="sxs-lookup"><span data-stu-id="cd692-p101">In this phase, you create the resource groups, storage accounts, virtual network (VNet), and availability sets in Azure that will host the virtual machines in phases 2, 3, and 4. You must complete this phase before moving on to [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
<span data-ttu-id="cd692-108">Deve essere fornite da Azure con componenti di base seguenti:</span><span class="sxs-lookup"><span data-stu-id="cd692-108">Azure must be provisioned with these basic components:</span></span>
  
- <span data-ttu-id="cd692-109">Gruppi di risorse</span><span class="sxs-lookup"><span data-stu-id="cd692-109">Resource groups</span></span>
    
- <span data-ttu-id="cd692-110">Una rete virtuale (VNet) Azure cross-premise con subnet per ospitare le macchine virtuali di Azure</span><span class="sxs-lookup"><span data-stu-id="cd692-110">A cross-premises Azure virtual network (VNet) with subnets for hosting the Azure virtual machines</span></span>
    
- <span data-ttu-id="cd692-111">Gruppi di sicurezza di rete per l'esecuzione dell'isolamento delle subnet</span><span class="sxs-lookup"><span data-stu-id="cd692-111">Network security groups for performing subnet isolation</span></span>
    
- <span data-ttu-id="cd692-112">Set di disponibilità</span><span class="sxs-lookup"><span data-stu-id="cd692-112">Availability sets</span></span>
    
## <a name="configure-azure-components"></a><span data-ttu-id="cd692-113">Configurare i componenti di Azure</span><span class="sxs-lookup"><span data-stu-id="cd692-113">Configure Azure components</span></span>

<span data-ttu-id="cd692-p102">Prima di iniziare la configurazione dei componenti Azure, del riempimento nelle tabelle seguenti. Per facilitare le procedure per la configurazione di Azure, in questa sezione di stampa e prendere nota delle informazioni necessarie o copiare in questa sezione di un documento e completare. Per le impostazioni del VNet, compilare tabella V.</span><span class="sxs-lookup"><span data-stu-id="cd692-p102">Before you begin configuring Azure components, fill in the following tables. To assist you in the procedures for configuring Azure, print this section and write down the needed information or copy this section to a document and fill it in. For the settings of the VNet, fill in Table V.</span></span>
  
|<span data-ttu-id="cd692-117">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="cd692-117">**Item**</span></span>|<span data-ttu-id="cd692-118">**Impostazione di configurazione**</span><span class="sxs-lookup"><span data-stu-id="cd692-118">**Configuration setting**</span></span>|<span data-ttu-id="cd692-119">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="cd692-119">**Description**</span></span>|<span data-ttu-id="cd692-120">**Valore**</span><span class="sxs-lookup"><span data-stu-id="cd692-120">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="cd692-121">1.</span><span class="sxs-lookup"><span data-stu-id="cd692-121">1.</span></span>  <br/> |<span data-ttu-id="cd692-122">Nome VNet</span><span class="sxs-lookup"><span data-stu-id="cd692-122">VNet name</span></span>  <br/> |<span data-ttu-id="cd692-123">Un nome da assegnare alla VNet (ad esempio, FedAuthNet).</span><span class="sxs-lookup"><span data-stu-id="cd692-123">A name to assign to the VNet (example FedAuthNet).</span></span>  <br/> |<span data-ttu-id="cd692-124">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-124"></span></span>  <br/> |
|<span data-ttu-id="cd692-125">2.</span><span class="sxs-lookup"><span data-stu-id="cd692-125">2.</span></span>  <br/> |<span data-ttu-id="cd692-126">Percorso VNet</span><span class="sxs-lookup"><span data-stu-id="cd692-126">VNet location</span></span>  <br/> |<span data-ttu-id="cd692-127">Data center di Azure regionale che conterrà la rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="cd692-127">The regional Azure datacenter that will contain the virtual network.</span></span>  <br/> |<span data-ttu-id="cd692-128">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-128"></span></span>  <br/> |
|<span data-ttu-id="cd692-129">3.</span><span class="sxs-lookup"><span data-stu-id="cd692-129">3.</span></span>  <br/> |<span data-ttu-id="cd692-130">Indirizzo IP del dispositivo VPN</span><span class="sxs-lookup"><span data-stu-id="cd692-130">VPN device IP address</span></span>  <br/> |<span data-ttu-id="cd692-131">L'indirizzo IPv4 pubblico dell'interfaccia del dispositivo VPN su Internet. </span><span class="sxs-lookup"><span data-stu-id="cd692-131">The public IPv4 address of your VPN device's interface on the Internet.</span></span>  <br/> |<span data-ttu-id="cd692-132">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-132"></span></span>  <br/> |
|<span data-ttu-id="cd692-133">4.</span><span class="sxs-lookup"><span data-stu-id="cd692-133">4.</span></span>  <br/> |<span data-ttu-id="cd692-134">Spazio di indirizzi della VNet</span><span class="sxs-lookup"><span data-stu-id="cd692-134">VNet address space</span></span>  <br/> |<span data-ttu-id="cd692-p103">Lo spazio di indirizzi della rete virtuale. Consultare il proprio reparto IT per determinare tale spazio di indirizzi.</span><span class="sxs-lookup"><span data-stu-id="cd692-p103">The address space for the virtual network. Work with your IT department to determine this address space.</span></span>  <br/> |<span data-ttu-id="cd692-137">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-137"></span></span>  <br/> |
|<span data-ttu-id="cd692-138">5.</span><span class="sxs-lookup"><span data-stu-id="cd692-138">5.</span></span>  <br/> |<span data-ttu-id="cd692-139">Chiave condivisa IPsec</span><span class="sxs-lookup"><span data-stu-id="cd692-139">IPsec shared key</span></span>  <br/> |<span data-ttu-id="cd692-p104">32 caratteri alfanumerici casuale stringa che verrà utilizzata per autenticare entrambi i lati della connessione VPN da sito. Lavorare con le IT o un reparto di sicurezza per determinare il valore della chiave. In alternativa, vedere [creazione di una stringa casuale per una chiave già condivisa IPsec](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).</span><span class="sxs-lookup"><span data-stu-id="cd692-p104">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value. Alternately, see [Create a random string for an IPsec preshared key](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |<span data-ttu-id="cd692-143">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-143"></span></span>  <br/> |
   
 <span data-ttu-id="cd692-144">**Tabella V: configurazione di una rete virtuale cross-premise**</span><span class="sxs-lookup"><span data-stu-id="cd692-144">**Table V: Cross-premises virtual network configuration**</span></span>
  
<span data-ttu-id="cd692-p105">Successivamente, compilare la tabella S per le subnet della soluzione. Tutti gli spazi di indirizzi devono essere in formato CIDR (Classless Interdomain Routing), noto anche come formato del prefisso di rete. Ad esempio, 10.24.64.0/20.</span><span class="sxs-lookup"><span data-stu-id="cd692-p105">Next, fill in Table S for the subnets of this solution. All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>
  
<span data-ttu-id="cd692-p106">Per le prime tre subnet, specificare un nome e un singolo spazio di indirizzi IP in base allo spazio di indirizzi di rete virtuale. Per la prima subnet del gateway, determinare lo spazio di indirizzi a 27 bit (con una lunghezza del prefisso di /27) per la subnet del gateway di Azure con quanto segue:</span><span class="sxs-lookup"><span data-stu-id="cd692-p106">For the first three subnets, specify a name and a single IP address space based on the virtual network address space. For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span></span>
  
1. <span data-ttu-id="cd692-150">Impostare i bit variabili nello spazio di indirizzi della VNet su 1, fino ai bit utilizzati dalla subnet del gateway, quindi impostare i bit rimanenti su 0.</span><span class="sxs-lookup"><span data-stu-id="cd692-150">Set the variable bits in the address space of the VNet to 1, up to the bits being used by the gateway subnet, then set the remaining bits to 0.</span></span>
    
2. <span data-ttu-id="cd692-151">Convertire i bit risultanti in formato decimale ed esprimerli come spazio di indirizzi con la lunghezza del prefisso impostata sulle dimensioni della subnet del gateway.</span><span class="sxs-lookup"><span data-stu-id="cd692-151">Convert the resulting bits to decimal and express it as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="cd692-152">Per un blocco di comandi di PowerShell e applicazione console c# o Python utilizzato per eseguire tale calcolo automaticamente, vedere [la calcolatrice spazio indirizzo per le subnet gateway Azure](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) .</span><span class="sxs-lookup"><span data-stu-id="cd692-152">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for a PowerShell command block and C# or Python console application that performs this calculation for you.</span></span>
  
<span data-ttu-id="cd692-153">Consultare il reparto IT per determinare tali spazi di indirizzi in base allo spazio di indirizzi della rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="cd692-153">Work with your IT department to determine these address spaces from the virtual network address space.</span></span>
  
|<span data-ttu-id="cd692-154">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="cd692-154">**Item**</span></span>|<span data-ttu-id="cd692-155">**Nome della subnet**</span><span class="sxs-lookup"><span data-stu-id="cd692-155">**Subnet name**</span></span>|<span data-ttu-id="cd692-156">**Spazio di indirizzi della subnet**</span><span class="sxs-lookup"><span data-stu-id="cd692-156">**Subnet address space**</span></span>|<span data-ttu-id="cd692-157">**Scopo**</span><span class="sxs-lookup"><span data-stu-id="cd692-157">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="cd692-158">1.</span><span class="sxs-lookup"><span data-stu-id="cd692-158">1.</span></span>  <br/> |<span data-ttu-id="cd692-159">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-159"></span></span>  <br/> |<span data-ttu-id="cd692-160">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-160"></span></span>  <br/> |<span data-ttu-id="cd692-161">La subnet utilizzata dal controller di dominio Windows Server Active Directory (AD) e le macchine virtuali (VMs) del server DirSync.</span><span class="sxs-lookup"><span data-stu-id="cd692-161">The subnet used by the Windows Server Active Directory (AD) domain controller and DirSync server virtual machines (VMs).</span></span>  <br/> |
|<span data-ttu-id="cd692-162">2.</span><span class="sxs-lookup"><span data-stu-id="cd692-162">2.</span></span>  <br/> |<span data-ttu-id="cd692-163">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-163"></span></span>  <br/> |<span data-ttu-id="cd692-164">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-164"></span></span>  <br/> |<span data-ttu-id="cd692-165">La subnet utilizzata dalle macchine virtuali di AD FS.</span><span class="sxs-lookup"><span data-stu-id="cd692-165">The subnet used by the AD FS VMs.</span></span>  <br/> |
|<span data-ttu-id="cd692-166">3.</span><span class="sxs-lookup"><span data-stu-id="cd692-166">3.</span></span>  <br/> |<span data-ttu-id="cd692-167">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-167"></span></span>  <br/> |<span data-ttu-id="cd692-168">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-168"></span></span>  <br/> |<span data-ttu-id="cd692-169">La subnet utilizzata dalle macchine virtuali del proxy di applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="cd692-169">The subnet used by the web application proxy VMs.</span></span>  <br/> |
|<span data-ttu-id="cd692-170">4.</span><span class="sxs-lookup"><span data-stu-id="cd692-170">4.</span></span>  <br/> |<span data-ttu-id="cd692-171">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="cd692-171">GatewaySubnet</span></span>  <br/> |<span data-ttu-id="cd692-172">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-172"></span></span>  <br/> |<span data-ttu-id="cd692-173">La subnet utilizzata dalle macchine virtuali del gateway di Azure.</span><span class="sxs-lookup"><span data-stu-id="cd692-173">The subnet used by the Azure gateway VMs.</span></span>  <br/> |
   
 <span data-ttu-id="cd692-174">**Tabella S: subnet nella rete virtuale**</span><span class="sxs-lookup"><span data-stu-id="cd692-174">**Table S: Subnets in the virtual network**</span></span>
  
<span data-ttu-id="cd692-175">Successivamente, compilare la tabella I per gli indirizzi IP statici assegnati alle macchine virtuali e alle istanze del bilanciamento del carico.</span><span class="sxs-lookup"><span data-stu-id="cd692-175">Next, fill in Table I for the static IP addresses assigned to virtual machines and load balancer instances.</span></span>
  
|<span data-ttu-id="cd692-176">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="cd692-176">**Item**</span></span>|<span data-ttu-id="cd692-177">**Scopo**</span><span class="sxs-lookup"><span data-stu-id="cd692-177">**Purpose**</span></span>|<span data-ttu-id="cd692-178">**Indirizzo IP della subnet**</span><span class="sxs-lookup"><span data-stu-id="cd692-178">**IP address on the subnet**</span></span>|<span data-ttu-id="cd692-179">**Valore**</span><span class="sxs-lookup"><span data-stu-id="cd692-179">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="cd692-180">1.</span><span class="sxs-lookup"><span data-stu-id="cd692-180">1.</span></span>  <br/> |<span data-ttu-id="cd692-181">Indirizzo IP statico del primo controller di dominio</span><span class="sxs-lookup"><span data-stu-id="cd692-181">Static IP address of the first domain controller</span></span>  <br/> |<span data-ttu-id="cd692-182">Il quarto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 1 della tabella S.</span><span class="sxs-lookup"><span data-stu-id="cd692-182">The fourth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="cd692-183">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-183"></span></span>  <br/> |
|<span data-ttu-id="cd692-184">2.</span><span class="sxs-lookup"><span data-stu-id="cd692-184">2.</span></span>  <br/> |<span data-ttu-id="cd692-185">Indirizzo IP statico del secondo controller di dominio</span><span class="sxs-lookup"><span data-stu-id="cd692-185">Static IP address of the second domain controller</span></span>  <br/> |<span data-ttu-id="cd692-186">Il quinto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 1 della tabella S.</span><span class="sxs-lookup"><span data-stu-id="cd692-186">The fifth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="cd692-187">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-187"></span></span>  <br/> |
|<span data-ttu-id="cd692-188">3.</span><span class="sxs-lookup"><span data-stu-id="cd692-188">3.</span></span>  <br/> |<span data-ttu-id="cd692-189">Indirizzo IP statico del server DirSync</span><span class="sxs-lookup"><span data-stu-id="cd692-189">Static IP address of the DirSync server</span></span>  <br/> |<span data-ttu-id="cd692-190">Il sesto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 1 della tabella S. </span><span class="sxs-lookup"><span data-stu-id="cd692-190">The sixth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="cd692-191">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-191"></span></span>  <br/> |
|<span data-ttu-id="cd692-192">4.</span><span class="sxs-lookup"><span data-stu-id="cd692-192">4.</span></span>  <br/> |<span data-ttu-id="cd692-193">Indirizzo IP statico del bilanciamento del carico interno per i server AD FS</span><span class="sxs-lookup"><span data-stu-id="cd692-193">Static IP address of the internal load balancer for the AD FS servers</span></span>  <br/> |<span data-ttu-id="cd692-194">Il quarto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 2 della tabella S. </span><span class="sxs-lookup"><span data-stu-id="cd692-194">The fourth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="cd692-195">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-195"></span></span>  <br/> |
|<span data-ttu-id="cd692-196">5.</span><span class="sxs-lookup"><span data-stu-id="cd692-196">5.</span></span>  <br/> |<span data-ttu-id="cd692-197">Indirizzo IP statico del primo server AD FS</span><span class="sxs-lookup"><span data-stu-id="cd692-197">Static IP address of the first AD FS server</span></span>  <br/> |<span data-ttu-id="cd692-198">Il quinto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 2 della tabella S.</span><span class="sxs-lookup"><span data-stu-id="cd692-198">The fifth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="cd692-199">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-199"></span></span>  <br/> |
|<span data-ttu-id="cd692-200">6.</span><span class="sxs-lookup"><span data-stu-id="cd692-200">6.</span></span>  <br/> |<span data-ttu-id="cd692-201">Indirizzo IP statico del secondo server AD FS</span><span class="sxs-lookup"><span data-stu-id="cd692-201">Static IP address of the second AD FS server</span></span>  <br/> |<span data-ttu-id="cd692-202">Il sesto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 2 della tabella S.</span><span class="sxs-lookup"><span data-stu-id="cd692-202">The sixth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="cd692-203">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-203"></span></span>  <br/> |
|<span data-ttu-id="cd692-204">7.</span><span class="sxs-lookup"><span data-stu-id="cd692-204">7.</span></span>  <br/> |<span data-ttu-id="cd692-205">Indirizzo IP statico del primo server proxy dell'applicazione Web</span><span class="sxs-lookup"><span data-stu-id="cd692-205">Static IP address of the first web application proxy server</span></span>  <br/> |<span data-ttu-id="cd692-206">Il quarto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 3 della tabella S.</span><span class="sxs-lookup"><span data-stu-id="cd692-206">The fourth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |<span data-ttu-id="cd692-207">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-207"></span></span>  <br/> |
|<span data-ttu-id="cd692-208">8.</span><span class="sxs-lookup"><span data-stu-id="cd692-208">8.</span></span>  <br/> |<span data-ttu-id="cd692-209">Indirizzo IP statico del secondo server proxy dell'applicazione Web</span><span class="sxs-lookup"><span data-stu-id="cd692-209">Static IP address of the second web application proxy server</span></span>  <br/> |<span data-ttu-id="cd692-210">Il quinto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 3 della tabella S.</span><span class="sxs-lookup"><span data-stu-id="cd692-210">The fifth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |<span data-ttu-id="cd692-211">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-211"></span></span>  <br/> |
   
 <span data-ttu-id="cd692-212">**Indirizzi IP statici i: tabella nella rete virtuale**</span><span class="sxs-lookup"><span data-stu-id="cd692-212">**Table I: Static IP addresses in the virtual network**</span></span>
  
<span data-ttu-id="cd692-213">Per due server DNS (Domain Name System) nella rete locale che si desidera utilizzare durante la configurazione iniziale dei controller di dominio nella rete virtuale, compilare la tabella D. Consultare il reparto IT per determinare questo elenco.</span><span class="sxs-lookup"><span data-stu-id="cd692-213">For two Domain Name System (DNS) servers in your on-premises network that you want to use when initially setting up the domain controllers in your virtual network, fill in Table D. Work with your IT department to determine this list.</span></span>
  
|<span data-ttu-id="cd692-214">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="cd692-214">**Item**</span></span>|<span data-ttu-id="cd692-215">**Nome descrittivo del server DNS**</span><span class="sxs-lookup"><span data-stu-id="cd692-215">**DNS server friendly name**</span></span>|<span data-ttu-id="cd692-216">**Indirizzo IP del server DNS**</span><span class="sxs-lookup"><span data-stu-id="cd692-216">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="cd692-217">1.</span><span class="sxs-lookup"><span data-stu-id="cd692-217">1.</span></span>  <br/> |<span data-ttu-id="cd692-218">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-218"></span></span>  <br/> |<span data-ttu-id="cd692-219">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-219"></span></span>  <br/> |
|<span data-ttu-id="cd692-220">2.</span><span class="sxs-lookup"><span data-stu-id="cd692-220">2.</span></span>  <br/> |<span data-ttu-id="cd692-221">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-221"></span></span>  <br/> |<span data-ttu-id="cd692-222">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-222"></span></span>  <br/> |
   
 <span data-ttu-id="cd692-223">**Tabella D: server DNS locali**</span><span class="sxs-lookup"><span data-stu-id="cd692-223">**Table D: On-premises DNS servers**</span></span>
  
<span data-ttu-id="cd692-p107">Per instradare i pacchetti dalla rete cross-premise alla rete aziendale tramite la connessione VPN da sito a sito, è necessario configurare la rete virtuale con una rete locale contenente un elenco degli spazi di indirizzi (in notazione CIDR) per tutti i percorsi raggiungibili nella rete locale dell'organizzazione. L'elenco degli spazi di indirizzi che definiscono la rete locale deve essere univoco e non deve sovrapporsi con lo spazio di indirizzi utilizzato per altre reti virtuali o per altre reti locali.</span><span class="sxs-lookup"><span data-stu-id="cd692-p107">To route packets from the cross-premises network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network that contains a list of the address spaces (in CIDR notation) for all of the reachable locations on your organization's on-premises network. The list of address spaces that define your local network must be unique and must not overlap with the address space used for other virtual networks or other local networks.</span></span>
  
<span data-ttu-id="cd692-p108">Per l'insieme degli spazi di indirizzi della rete locale, compilare la tabella L. Sono elencate tre voci vuote, ma sarà necessario aggiungerne altre. Consultare il proprio reparto IT per determinare questo elenco di spazi di indirizzi.</span><span class="sxs-lookup"><span data-stu-id="cd692-p108">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list of address spaces.</span></span>
  
|<span data-ttu-id="cd692-228">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="cd692-228">**Item**</span></span>|<span data-ttu-id="cd692-229">**Spazio di indirizzi della rete locale**</span><span class="sxs-lookup"><span data-stu-id="cd692-229">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="cd692-230">1.</span><span class="sxs-lookup"><span data-stu-id="cd692-230">1.</span></span>  <br/> |<span data-ttu-id="cd692-231">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-231"></span></span>  <br/> |
|<span data-ttu-id="cd692-232">2.</span><span class="sxs-lookup"><span data-stu-id="cd692-232">2.</span></span>  <br/> |<span data-ttu-id="cd692-233">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-233"></span></span>  <br/> |
|<span data-ttu-id="cd692-234">3.</span><span class="sxs-lookup"><span data-stu-id="cd692-234">3.</span></span>  <br/> |<span data-ttu-id="cd692-235">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-235"></span></span>  <br/> |
   
 <span data-ttu-id="cd692-236">**Tabella L: prefissi degli indirizzi per la rete locale**</span><span class="sxs-lookup"><span data-stu-id="cd692-236">**Table L: Address prefixes for the local network**</span></span>
  
<span data-ttu-id="cd692-237">Iniziamo a creare l'infrastruttura di Azure per ospitare l'autenticazione federata di Office 365.</span><span class="sxs-lookup"><span data-stu-id="cd692-237">Now let's begin building the Azure infrastructure to host your federated authentication for Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="cd692-p109">Il seguente comando consente di utilizzare la versione più recente di Azure PowerShell. Vedere [iniziare a utilizzare i cmdlet PowerShell di Azure](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="cd692-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="cd692-240">Avviare un prompt dei comandi di Azure PowerShell e accedere al proprio account.</span><span class="sxs-lookup"><span data-stu-id="cd692-240">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="cd692-241">Per un file di testo che contiene tutti i comandi di PowerShell in questo articolo e una cartella di lavoro configurazione Microsoft Excel che genera pronto a portata di blocchi di comandi di PowerShell in base alle impostazioni personalizzate, vedere [autenticazione federata per Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="cd692-241">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
<span data-ttu-id="cd692-242">Ottenere il nome della sottoscrizione utilizzando il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="cd692-242">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="cd692-243">Per le versioni precedenti di Azure PowerShell, utilizzare questo comando.</span><span class="sxs-lookup"><span data-stu-id="cd692-243">For older versions of Azure PowerShell, use this command instead.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select SubscriptionName
```

<span data-ttu-id="cd692-p110">Impostare la sottoscrizione di Azure. Sostituire tutte le virgolette, incluse le \< e > caratteri, con il nome corretto.</span><span class="sxs-lookup"><span data-stu-id="cd692-p110">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="cd692-p111">Successivamente, creare i nuovi gruppi di risorse. Per determinare un set di nomi dei gruppi di risorse univoci, utilizzare questo comando per creare un elenco dei gruppi di risorse esistenti.</span><span class="sxs-lookup"><span data-stu-id="cd692-p111">Next, create the new resource groups. To determine a unique set of resource group names, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="cd692-248">Compilare la tabella seguente per il set di nomi dei gruppi di risorse univoci.</span><span class="sxs-lookup"><span data-stu-id="cd692-248">Fill in the following table for the set of unique resource group names.</span></span>
  
|<span data-ttu-id="cd692-249">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="cd692-249">**Item**</span></span>|<span data-ttu-id="cd692-250">**Nome del gruppo di risorse**</span><span class="sxs-lookup"><span data-stu-id="cd692-250">**Resource group name**</span></span>|<span data-ttu-id="cd692-251">**Scopo**</span><span class="sxs-lookup"><span data-stu-id="cd692-251">**Purpose**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="cd692-252">1.</span><span class="sxs-lookup"><span data-stu-id="cd692-252">1.</span></span>  <br/> |<span data-ttu-id="cd692-253">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-253"></span></span>  <br/> |<span data-ttu-id="cd692-254">Controller di dominio</span><span class="sxs-lookup"><span data-stu-id="cd692-254">Domain controllers</span></span>  <br/> |
|<span data-ttu-id="cd692-255">2.</span><span class="sxs-lookup"><span data-stu-id="cd692-255">2.</span></span>  <br/> |<span data-ttu-id="cd692-256">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-256"></span></span>  <br/> |<span data-ttu-id="cd692-257">Server AD FS</span><span class="sxs-lookup"><span data-stu-id="cd692-257">AD FS servers</span></span>  <br/> |
|<span data-ttu-id="cd692-258">3.</span><span class="sxs-lookup"><span data-stu-id="cd692-258">3.</span></span>  <br/> |<span data-ttu-id="cd692-259">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-259"></span></span>  <br/> |<span data-ttu-id="cd692-260">Server proxy di applicazione Web</span><span class="sxs-lookup"><span data-stu-id="cd692-260">Web application proxy servers</span></span>  <br/> |
|<span data-ttu-id="cd692-261">4.</span><span class="sxs-lookup"><span data-stu-id="cd692-261">4.</span></span>  <br/> |<span data-ttu-id="cd692-262">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-262"></span></span>  <br/> |<span data-ttu-id="cd692-263">Elementi dell'infrastruttura</span><span class="sxs-lookup"><span data-stu-id="cd692-263">Infrastructure elements</span></span>  <br/> |
   
 <span data-ttu-id="cd692-264">**Tabella r: gruppi di risorse**</span><span class="sxs-lookup"><span data-stu-id="cd692-264">**Table R: Resource groups**</span></span>
  
<span data-ttu-id="cd692-265">Creare i nuovi gruppi di risorse con questi comandi.</span><span class="sxs-lookup"><span data-stu-id="cd692-265">Create your new resource groups with these commands.</span></span>
  
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

<span data-ttu-id="cd692-266">Successivamente, creare la rete virtuale di Azure e le relative subnet.</span><span class="sxs-lookup"><span data-stu-id="cd692-266">Next, you create the Azure virtual network and its subnets.</span></span>
  
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

<span data-ttu-id="cd692-p112">È quindi creare rete gruppi di sicurezza per ogni subnet che contiene le macchine virtuali. Per eseguire isolamento subnet, è possibile aggiungere regole per specifici tipi di traffico concesse o negate al gruppo di protezione di rete di una subnet.</span><span class="sxs-lookup"><span data-stu-id="cd692-p112">Next, you create network security groups for each subnet that contains virtual machines. To perform subnet isolation, you can add rules for the specific types of traffic allowed or denied to the network security group of a subnet.</span></span>
  
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

<span data-ttu-id="cd692-269">Successivamente, utilizzare questi comandi per creare i gateway per la connessione VPN da sito a sito.</span><span class="sxs-lookup"><span data-stu-id="cd692-269">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
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
> <span data-ttu-id="cd692-p113">Le risorse locali non utilizzano l'autenticazione federata dei singoli utenti. Tuttavia, se la connessione VPN da sito risulta disponibile, i controller di dominio di VNet non riceverà aggiornamenti agli account utente e gruppi apportati in locale Windows Server Active Directory. Per garantire che non accade, è possibile configurare la disponibilità elevata per la connessione di rete VPN del sito per sito. Per ulteriori informazioni, vedere [altamente disponibili tra locali e la connettività VNet-VNet](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="cd692-p113">Federated authentication of individual users does not rely on any on-premises resources. However, if this site-to-site VPN connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your site-to-site VPN connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="cd692-274">Successivamente, registrare l'indirizzo IPv4 pubblico del gateway VPN di Azure per la rete virtuale visualizzato con questo comando:</span><span class="sxs-lookup"><span data-stu-id="cd692-274">Next, record the public IPv4 address of the Azure VPN gateway for your virtual network from the display of this command:</span></span>
  
```
Get-AzureRMPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

<span data-ttu-id="cd692-p114">Configurare quindi il dispositivo VPN in locale per la connessione al gateway VPN Azure. Per ulteriori informazioni, vedere [configurare il dispositivo VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="cd692-p114">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="cd692-277">Per configurare il dispositivo VPN locale, è necessario quanto segue:</span><span class="sxs-lookup"><span data-stu-id="cd692-277">To configure your on-premises VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="cd692-278">L'indirizzo IPv4 pubblico del gateway VPN di Azure.</span><span class="sxs-lookup"><span data-stu-id="cd692-278">The public IPv4 address of the Azure VPN gateway.</span></span>
    
- <span data-ttu-id="cd692-279">Il tasto già condiviso IPsec per la connessione VPN da sito (colonna di tabella V - elemento 5 - valore).</span><span class="sxs-lookup"><span data-stu-id="cd692-279">The IPsec pre-shared key for the site-to-site VPN connection (Table V - Item 5 - Value column).</span></span>
    
<span data-ttu-id="cd692-p115">Successivamente, assicurarsi che lo spazio di indirizzi della rete virtuale sia raggiungibile dalla rete locale. In genere è possibile aggiungere una route corrispondente allo spazio di indirizzi di rete virtuali al dispositivo VPN e quindi distribuire tale route al resto dell'infrastruttura di routing della rete dell'organizzazione. A tale scopo, consultare il proprio reparto IT.</span><span class="sxs-lookup"><span data-stu-id="cd692-p115">Next, ensure that the address space of the virtual network is reachable from your on-premises network. This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network. Work with your IT department to determine how to do this.</span></span>
  
<span data-ttu-id="cd692-p116">Successivamente, definire i nomi di tre set di disponibilità. Compilare la tabella A. </span><span class="sxs-lookup"><span data-stu-id="cd692-p116">Next, define the names of three availability sets. Fill out Table A.</span></span> 
  
|<span data-ttu-id="cd692-285">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="cd692-285">**Item**</span></span>|<span data-ttu-id="cd692-286">**Scopo**</span><span class="sxs-lookup"><span data-stu-id="cd692-286">**Purpose**</span></span>|<span data-ttu-id="cd692-287">**Nome del set di disponibilità**</span><span class="sxs-lookup"><span data-stu-id="cd692-287">**Availability set name**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="cd692-288">1.</span><span class="sxs-lookup"><span data-stu-id="cd692-288">1.</span></span>  <br/> |<span data-ttu-id="cd692-289">Controller di dominio</span><span class="sxs-lookup"><span data-stu-id="cd692-289">Domain controllers</span></span>  <br/> |<span data-ttu-id="cd692-290">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-290"></span></span>  <br/> |
|<span data-ttu-id="cd692-291">2.</span><span class="sxs-lookup"><span data-stu-id="cd692-291">2.</span></span>  <br/> |<span data-ttu-id="cd692-292">Server AD FS</span><span class="sxs-lookup"><span data-stu-id="cd692-292">AD FS servers</span></span>  <br/> |<span data-ttu-id="cd692-293">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-293"></span></span>  <br/> |
|<span data-ttu-id="cd692-294">3.</span><span class="sxs-lookup"><span data-stu-id="cd692-294">3.</span></span>  <br/> |<span data-ttu-id="cd692-295">Server proxy di applicazione Web</span><span class="sxs-lookup"><span data-stu-id="cd692-295">Web application proxy servers</span></span>  <br/> |<span data-ttu-id="cd692-296">_______________________________</span><span class="sxs-lookup"><span data-stu-id="cd692-296"></span></span>  <br/> |
   
 <span data-ttu-id="cd692-297">**Set di disponibilità a: tabella**</span><span class="sxs-lookup"><span data-stu-id="cd692-297">**Table A: Availability sets**</span></span>
  
<span data-ttu-id="cd692-298">Questi nomi sono necessari quando si creano le macchine virtuali nelle fasi 2, 3 e 4.</span><span class="sxs-lookup"><span data-stu-id="cd692-298">You will need these names when you create the virtual machines in phases 2, 3, and 4.</span></span>
  
<span data-ttu-id="cd692-299">Creare i nuovi set di disponibilità con questi comandi di Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cd692-299">Create the new availability sets with these Azure PowerShell commands.</span></span>
  
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

<span data-ttu-id="cd692-300">Questa è la configurazione risultante dal completamento corretto di questa fase.</span><span class="sxs-lookup"><span data-stu-id="cd692-300">This is the configuration resulting from the successful completion of this phase.</span></span>
  
<span data-ttu-id="cd692-301">**Fase 1: L'infrastruttura per l'autenticazione federata di disponibilità elevata per Office 365**</span><span class="sxs-lookup"><span data-stu-id="cd692-301">**Phase 1: The Azure infrastructure for high availability federated authentication for Office 365**</span></span>

![Fase 1 dell'autenticazione federata di Office 365 con disponibilità elevata in Azure con l'infrastruttura di Azure](images/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a><span data-ttu-id="cd692-303">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="cd692-303">Next step</span></span>

<span data-ttu-id="cd692-304">Utilizzare [la disponibilità elevata federati autenticazione fase 2: configurare i controller di dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) per continuare con la configurazione di questo carico di lavoro.</span><span class="sxs-lookup"><span data-stu-id="cd692-304">Use [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) to continue with the configuration of this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cd692-305">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cd692-305">See Also</span></span>

[<span data-ttu-id="cd692-306">Distribuire l'autenticazione federata ad alta visibilità per Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="cd692-306">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="cd692-307">Identità federata per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="cd692-307">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="cd692-308">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="cd692-308">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="cd692-309">Identità federata per Office 365</span><span class="sxs-lookup"><span data-stu-id="cd692-309">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


