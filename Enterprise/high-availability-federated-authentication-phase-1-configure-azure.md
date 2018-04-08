---
title: Fase 1 configurare Azure l'autenticazione federata la disponibilità elevata
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/06/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: "Riepilogo: Configurare l'infrastruttura Microsoft Azure per la disponibilità elevata host l'autenticazione federata per Office 365."
ms.openlocfilehash: aea4fb5b8645f18381b9b9391b91925ffed00aab
ms.sourcegitcommit: a337ac253054f571a8304e18e426f74bcd385857
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2018
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a><span data-ttu-id="d8890-103">Fase 1 dell'autenticazione federata a disponibilità elevata: Configurare Azure</span><span class="sxs-lookup"><span data-stu-id="d8890-103">High availability federated authentication Phase 1: Configure Azure</span></span>

 <span data-ttu-id="d8890-104">**Riepilogo:** Configurare l'infrastruttura Microsoft Azure per l'autenticazione di disponibilità elevata federate host per Office 365.</span><span class="sxs-lookup"><span data-stu-id="d8890-104">**Summary:** Configure the Microsoft Azure infrastructure to host high availability federated authentication for Office 365.</span></span>
  
<span data-ttu-id="d8890-p101">In questa fase, verrà creato i gruppi di risorse, set di rete (VNet) e la disponibilità virtuali di Azure che ospiterà le macchine virtuali in fasi 2, 3 e 4. È necessario completare prima di spostare in questa fase [la disponibilità elevata federati autenticazione fase 2: configurare i controller di dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Per tutte le fasi, vedere [Deploy la disponibilità elevata nell'autenticazione federata per Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) .</span><span class="sxs-lookup"><span data-stu-id="d8890-p101">In this phase, you create the resource groups, virtual network (VNet), and availability sets in Azure that will host the virtual machines in phases 2, 3, and 4. You must complete this phase before moving on to [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
<span data-ttu-id="d8890-108">Deve essere fornite da Azure con componenti di base seguenti:</span><span class="sxs-lookup"><span data-stu-id="d8890-108">Azure must be provisioned with these basic components:</span></span>
  
- <span data-ttu-id="d8890-109">Gruppi di risorse</span><span class="sxs-lookup"><span data-stu-id="d8890-109">Resource groups</span></span>
    
- <span data-ttu-id="d8890-110">Una rete virtuale (VNet) Azure cross-premise con subnet per ospitare le macchine virtuali di Azure</span><span class="sxs-lookup"><span data-stu-id="d8890-110">A cross-premises Azure virtual network (VNet) with subnets for hosting the Azure virtual machines</span></span>
    
- <span data-ttu-id="d8890-111">Gruppi di sicurezza di rete per l'esecuzione dell'isolamento delle subnet</span><span class="sxs-lookup"><span data-stu-id="d8890-111">Network security groups for performing subnet isolation</span></span>
    
- <span data-ttu-id="d8890-112">Set di disponibilità</span><span class="sxs-lookup"><span data-stu-id="d8890-112">Availability sets</span></span>
    
## <a name="configure-azure-components"></a><span data-ttu-id="d8890-113">Configurare i componenti di Azure</span><span class="sxs-lookup"><span data-stu-id="d8890-113">Configure Azure components</span></span>

<span data-ttu-id="d8890-p102">Prima di iniziare la configurazione dei componenti Azure, del riempimento nelle tabelle seguenti. Per facilitare le procedure per la configurazione di Azure, in questa sezione di stampa e prendere nota delle informazioni necessarie o copiare in questa sezione di un documento e completare. Per le impostazioni del VNet, compilare tabella V.</span><span class="sxs-lookup"><span data-stu-id="d8890-p102">Before you begin configuring Azure components, fill in the following tables. To assist you in the procedures for configuring Azure, print this section and write down the needed information or copy this section to a document and fill it in. For the settings of the VNet, fill in Table V.</span></span>
  
|<span data-ttu-id="d8890-117">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="d8890-117">**Item**</span></span>|<span data-ttu-id="d8890-118">**Impostazione di configurazione**</span><span class="sxs-lookup"><span data-stu-id="d8890-118">**Configuration setting**</span></span>|<span data-ttu-id="d8890-119">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="d8890-119">**Description**</span></span>|<span data-ttu-id="d8890-120">**Valore**</span><span class="sxs-lookup"><span data-stu-id="d8890-120">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="d8890-121">1.</span><span class="sxs-lookup"><span data-stu-id="d8890-121">1.</span></span>  <br/> |<span data-ttu-id="d8890-122">Nome VNet</span><span class="sxs-lookup"><span data-stu-id="d8890-122">VNet name</span></span>  <br/> |<span data-ttu-id="d8890-123">Un nome da assegnare alla VNet (ad esempio, FedAuthNet).</span><span class="sxs-lookup"><span data-stu-id="d8890-123">A name to assign to the VNet (example FedAuthNet).</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="d8890-124">2.</span><span class="sxs-lookup"><span data-stu-id="d8890-124">2.</span></span>  <br/> |<span data-ttu-id="d8890-125">Percorso VNet</span><span class="sxs-lookup"><span data-stu-id="d8890-125">VNet location</span></span>  <br/> |<span data-ttu-id="d8890-126">Data center di Azure regionale che conterrà la rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="d8890-126">The regional Azure datacenter that will contain the virtual network.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="d8890-127">3.</span><span class="sxs-lookup"><span data-stu-id="d8890-127">3.</span></span>  <br/> |<span data-ttu-id="d8890-128">Indirizzo IP del dispositivo VPN</span><span class="sxs-lookup"><span data-stu-id="d8890-128">VPN device IP address</span></span>  <br/> |<span data-ttu-id="d8890-129">L'indirizzo IPv4 pubblico dell'interfaccia del dispositivo VPN su Internet. </span><span class="sxs-lookup"><span data-stu-id="d8890-129">The public IPv4 address of your VPN device's interface on the Internet.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="d8890-130">4.</span><span class="sxs-lookup"><span data-stu-id="d8890-130">4.</span></span>  <br/> |<span data-ttu-id="d8890-131">Spazio di indirizzi della VNet</span><span class="sxs-lookup"><span data-stu-id="d8890-131">VNet address space</span></span>  <br/> |<span data-ttu-id="d8890-p103">Lo spazio di indirizzi della rete virtuale. Consultare il proprio reparto IT per determinare tale spazio di indirizzi.</span><span class="sxs-lookup"><span data-stu-id="d8890-p103">The address space for the virtual network. Work with your IT department to determine this address space.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="d8890-134">5.</span><span class="sxs-lookup"><span data-stu-id="d8890-134">5.</span></span>  <br/> |<span data-ttu-id="d8890-135">Chiave condivisa IPsec</span><span class="sxs-lookup"><span data-stu-id="d8890-135">IPsec shared key</span></span>  <br/> |<span data-ttu-id="d8890-p104">32 caratteri alfanumerici casuale stringa che verrà utilizzata per autenticare entrambi i lati della connessione VPN da sito. Lavorare con le IT o un reparto di sicurezza per determinare il valore della chiave. In alternativa, vedere [creazione di una stringa casuale per una chiave già condivisa IPsec](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).</span><span class="sxs-lookup"><span data-stu-id="d8890-p104">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value. Alternately, see [Create a random string for an IPsec preshared key](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |![](./images/Common_Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="d8890-139">**Tabella V: configurazione di una rete virtuale cross-premise**</span><span class="sxs-lookup"><span data-stu-id="d8890-139">**Table V: Cross-premises virtual network configuration**</span></span>
  
<span data-ttu-id="d8890-p105">Successivamente, compilare la tabella S per le subnet della soluzione. Tutti gli spazi di indirizzi devono essere in formato CIDR (Classless Interdomain Routing), noto anche come formato del prefisso di rete. Ad esempio, 10.24.64.0/20.</span><span class="sxs-lookup"><span data-stu-id="d8890-p105">Next, fill in Table S for the subnets of this solution. All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>
  
<span data-ttu-id="d8890-p106">Per le prime tre subnet, specificare un nome e un singolo spazio di indirizzi IP in base allo spazio di indirizzi di rete virtuale. Per la prima subnet del gateway, determinare lo spazio di indirizzi a 27 bit (con una lunghezza del prefisso di /27) per la subnet del gateway di Azure con quanto segue:</span><span class="sxs-lookup"><span data-stu-id="d8890-p106">For the first three subnets, specify a name and a single IP address space based on the virtual network address space. For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span></span>
  
1. <span data-ttu-id="d8890-145">Impostare i bit variabili nello spazio di indirizzi della VNet su 1, fino ai bit utilizzati dalla subnet del gateway, quindi impostare i bit rimanenti su 0.</span><span class="sxs-lookup"><span data-stu-id="d8890-145">Set the variable bits in the address space of the VNet to 1, up to the bits being used by the gateway subnet, then set the remaining bits to 0.</span></span>
    
2. <span data-ttu-id="d8890-146">Convertire i bit risultanti in formato decimale ed esprimerli come spazio di indirizzi con la lunghezza del prefisso impostata sulle dimensioni della subnet del gateway.</span><span class="sxs-lookup"><span data-stu-id="d8890-146">Convert the resulting bits to decimal and express it as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="d8890-147">Per un blocco di comandi di PowerShell e applicazione console c# o Python utilizzato per eseguire tale calcolo automaticamente, vedere [la calcolatrice spazio indirizzo per le subnet gateway Azure](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) .</span><span class="sxs-lookup"><span data-stu-id="d8890-147">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for a PowerShell command block and C# or Python console application that performs this calculation for you.</span></span>
  
<span data-ttu-id="d8890-148">Consultare il reparto IT per determinare tali spazi di indirizzi in base allo spazio di indirizzi della rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="d8890-148">Work with your IT department to determine these address spaces from the virtual network address space.</span></span>
  
|<span data-ttu-id="d8890-149">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="d8890-149">**Item**</span></span>|<span data-ttu-id="d8890-150">**Nome della subnet**</span><span class="sxs-lookup"><span data-stu-id="d8890-150">**Subnet name**</span></span>|<span data-ttu-id="d8890-151">**Spazio di indirizzi della subnet**</span><span class="sxs-lookup"><span data-stu-id="d8890-151">**Subnet address space**</span></span>|<span data-ttu-id="d8890-152">**Scopo**</span><span class="sxs-lookup"><span data-stu-id="d8890-152">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="d8890-153">1.</span><span class="sxs-lookup"><span data-stu-id="d8890-153">1.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |<span data-ttu-id="d8890-154">La subnet utilizzata dal controller di dominio Windows Server Active Directory (AD) e le macchine virtuali (VMs) del server DirSync.</span><span class="sxs-lookup"><span data-stu-id="d8890-154">The subnet used by the Windows Server Active Directory (AD) domain controller and DirSync server virtual machines (VMs).</span></span>  <br/> |
|<span data-ttu-id="d8890-155">2.</span><span class="sxs-lookup"><span data-stu-id="d8890-155">2.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |<span data-ttu-id="d8890-156">La subnet utilizzata dalle macchine virtuali di AD FS.</span><span class="sxs-lookup"><span data-stu-id="d8890-156">The subnet used by the AD FS VMs.</span></span>  <br/> |
|<span data-ttu-id="d8890-157">3.</span><span class="sxs-lookup"><span data-stu-id="d8890-157">3.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |<span data-ttu-id="d8890-158">La subnet utilizzata dalle macchine virtuali del proxy di applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="d8890-158">The subnet used by the web application proxy VMs.</span></span>  <br/> |
|<span data-ttu-id="d8890-159">4.</span><span class="sxs-lookup"><span data-stu-id="d8890-159">4.</span></span>  <br/> |<span data-ttu-id="d8890-160">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="d8890-160">GatewaySubnet</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |<span data-ttu-id="d8890-161">La subnet utilizzata dalle macchine virtuali del gateway di Azure.</span><span class="sxs-lookup"><span data-stu-id="d8890-161">The subnet used by the Azure gateway VMs.</span></span>  <br/> |
   
 <span data-ttu-id="d8890-162">**Tabella S: subnet nella rete virtuale**</span><span class="sxs-lookup"><span data-stu-id="d8890-162">**Table S: Subnets in the virtual network**</span></span>
  
<span data-ttu-id="d8890-163">Successivamente, compilare la tabella I per gli indirizzi IP statici assegnati alle macchine virtuali e alle istanze del bilanciamento del carico.</span><span class="sxs-lookup"><span data-stu-id="d8890-163">Next, fill in Table I for the static IP addresses assigned to virtual machines and load balancer instances.</span></span>
  
|<span data-ttu-id="d8890-164">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="d8890-164">**Item**</span></span>|<span data-ttu-id="d8890-165">**Scopo**</span><span class="sxs-lookup"><span data-stu-id="d8890-165">**Purpose**</span></span>|<span data-ttu-id="d8890-166">**Indirizzo IP della subnet**</span><span class="sxs-lookup"><span data-stu-id="d8890-166">**IP address on the subnet**</span></span>|<span data-ttu-id="d8890-167">**Valore**</span><span class="sxs-lookup"><span data-stu-id="d8890-167">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="d8890-168">1.</span><span class="sxs-lookup"><span data-stu-id="d8890-168">1.</span></span>  <br/> |<span data-ttu-id="d8890-169">Indirizzo IP statico del primo controller di dominio</span><span class="sxs-lookup"><span data-stu-id="d8890-169">Static IP address of the first domain controller</span></span>  <br/> |<span data-ttu-id="d8890-170">Il quarto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 1 della tabella S.</span><span class="sxs-lookup"><span data-stu-id="d8890-170">The fourth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="d8890-171">2.</span><span class="sxs-lookup"><span data-stu-id="d8890-171">2.</span></span>  <br/> |<span data-ttu-id="d8890-172">Indirizzo IP statico del secondo controller di dominio</span><span class="sxs-lookup"><span data-stu-id="d8890-172">Static IP address of the second domain controller</span></span>  <br/> |<span data-ttu-id="d8890-173">Il quinto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 1 della tabella S.</span><span class="sxs-lookup"><span data-stu-id="d8890-173">The fifth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="d8890-174">3.</span><span class="sxs-lookup"><span data-stu-id="d8890-174">3.</span></span>  <br/> |<span data-ttu-id="d8890-175">Indirizzo IP statico del server DirSync</span><span class="sxs-lookup"><span data-stu-id="d8890-175">Static IP address of the DirSync server</span></span>  <br/> |<span data-ttu-id="d8890-176">Il sesto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 1 della tabella S. </span><span class="sxs-lookup"><span data-stu-id="d8890-176">The sixth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="d8890-177">4.</span><span class="sxs-lookup"><span data-stu-id="d8890-177">4.</span></span>  <br/> |<span data-ttu-id="d8890-178">Indirizzo IP statico del bilanciamento del carico interno per i server AD FS</span><span class="sxs-lookup"><span data-stu-id="d8890-178">Static IP address of the internal load balancer for the AD FS servers</span></span>  <br/> |<span data-ttu-id="d8890-179">Il quarto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 2 della tabella S. </span><span class="sxs-lookup"><span data-stu-id="d8890-179">The fourth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="d8890-180">5.</span><span class="sxs-lookup"><span data-stu-id="d8890-180">5.</span></span>  <br/> |<span data-ttu-id="d8890-181">Indirizzo IP statico del primo server AD FS</span><span class="sxs-lookup"><span data-stu-id="d8890-181">Static IP address of the first AD FS server</span></span>  <br/> |<span data-ttu-id="d8890-182">Il quinto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 2 della tabella S.</span><span class="sxs-lookup"><span data-stu-id="d8890-182">The fifth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="d8890-183">6.</span><span class="sxs-lookup"><span data-stu-id="d8890-183">6.</span></span>  <br/> |<span data-ttu-id="d8890-184">Indirizzo IP statico del secondo server AD FS</span><span class="sxs-lookup"><span data-stu-id="d8890-184">Static IP address of the second AD FS server</span></span>  <br/> |<span data-ttu-id="d8890-185">Il sesto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 2 della tabella S.</span><span class="sxs-lookup"><span data-stu-id="d8890-185">The sixth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="d8890-186">7.</span><span class="sxs-lookup"><span data-stu-id="d8890-186">7.</span></span>  <br/> |<span data-ttu-id="d8890-187">Indirizzo IP statico del primo server proxy dell'applicazione Web</span><span class="sxs-lookup"><span data-stu-id="d8890-187">Static IP address of the first web application proxy server</span></span>  <br/> |<span data-ttu-id="d8890-188">Il quarto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 3 della tabella S.</span><span class="sxs-lookup"><span data-stu-id="d8890-188">The fourth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="d8890-189">8.</span><span class="sxs-lookup"><span data-stu-id="d8890-189">8.</span></span>  <br/> |<span data-ttu-id="d8890-190">Indirizzo IP statico del secondo server proxy dell'applicazione Web</span><span class="sxs-lookup"><span data-stu-id="d8890-190">Static IP address of the second web application proxy server</span></span>  <br/> |<span data-ttu-id="d8890-191">Il quinto indirizzo IP possibile per lo spazio di indirizzi della subnet definito alla voce 3 della tabella S.</span><span class="sxs-lookup"><span data-stu-id="d8890-191">The fifth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="d8890-192">**Indirizzi IP statici i: tabella nella rete virtuale**</span><span class="sxs-lookup"><span data-stu-id="d8890-192">**Table I: Static IP addresses in the virtual network**</span></span>
  
<span data-ttu-id="d8890-193">Per due server DNS (Domain Name System) nella rete locale che si desidera utilizzare durante la configurazione iniziale dei controller di dominio nella rete virtuale, compilare la tabella D. Consultare il reparto IT per determinare questo elenco.</span><span class="sxs-lookup"><span data-stu-id="d8890-193">For two Domain Name System (DNS) servers in your on-premises network that you want to use when initially setting up the domain controllers in your virtual network, fill in Table D. Work with your IT department to determine this list.</span></span>
  
|<span data-ttu-id="d8890-194">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="d8890-194">**Item**</span></span>|<span data-ttu-id="d8890-195">**Nome descrittivo del server DNS**</span><span class="sxs-lookup"><span data-stu-id="d8890-195">**DNS server friendly name**</span></span>|<span data-ttu-id="d8890-196">**Indirizzo IP del server DNS**</span><span class="sxs-lookup"><span data-stu-id="d8890-196">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="d8890-197">1.</span><span class="sxs-lookup"><span data-stu-id="d8890-197">1.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="d8890-198">2.</span><span class="sxs-lookup"><span data-stu-id="d8890-198">2.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="d8890-199">**Tabella D: server DNS locali**</span><span class="sxs-lookup"><span data-stu-id="d8890-199">**Table D: On-premises DNS servers**</span></span>
  
<span data-ttu-id="d8890-p107">Per instradare i pacchetti dalla rete cross-premise alla rete aziendale tramite la connessione VPN da sito a sito, è necessario configurare la rete virtuale con una rete locale contenente un elenco degli spazi di indirizzi (in notazione CIDR) per tutti i percorsi raggiungibili nella rete locale dell'organizzazione. L'elenco degli spazi di indirizzi che definiscono la rete locale deve essere univoco e non deve sovrapporsi con lo spazio di indirizzi utilizzato per altre reti virtuali o per altre reti locali.</span><span class="sxs-lookup"><span data-stu-id="d8890-p107">To route packets from the cross-premises network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network that contains a list of the address spaces (in CIDR notation) for all of the reachable locations on your organization's on-premises network. The list of address spaces that define your local network must be unique and must not overlap with the address space used for other virtual networks or other local networks.</span></span>
  
<span data-ttu-id="d8890-p108">Per l'insieme degli spazi di indirizzi della rete locale, compilare la tabella L. Sono elencate tre voci vuote, ma sarà necessario aggiungerne altre. Consultare il proprio reparto IT per determinare questo elenco di spazi di indirizzi.</span><span class="sxs-lookup"><span data-stu-id="d8890-p108">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list of address spaces.</span></span>
  
|<span data-ttu-id="d8890-204">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="d8890-204">**Item**</span></span>|<span data-ttu-id="d8890-205">**Spazio di indirizzi della rete locale**</span><span class="sxs-lookup"><span data-stu-id="d8890-205">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d8890-206">1.</span><span class="sxs-lookup"><span data-stu-id="d8890-206">1.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="d8890-207">2.</span><span class="sxs-lookup"><span data-stu-id="d8890-207">2.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="d8890-208">3.</span><span class="sxs-lookup"><span data-stu-id="d8890-208">3.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="d8890-209">**Tabella L: prefissi degli indirizzi per la rete locale**</span><span class="sxs-lookup"><span data-stu-id="d8890-209">**Table L: Address prefixes for the local network**</span></span>
  
<span data-ttu-id="d8890-210">Iniziamo a creare l'infrastruttura di Azure per ospitare l'autenticazione federata di Office 365.</span><span class="sxs-lookup"><span data-stu-id="d8890-210">Now let's begin building the Azure infrastructure to host your federated authentication for Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="d8890-p109">Il seguente comando consente di utilizzare la versione più recente di Azure PowerShell. Vedere [iniziare a utilizzare i cmdlet PowerShell di Azure](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="d8890-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="d8890-213">Avviare un prompt dei comandi di Azure PowerShell e accedere al proprio account.</span><span class="sxs-lookup"><span data-stu-id="d8890-213">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="d8890-214">Per un file di testo che contiene tutti i comandi di PowerShell in questo articolo e una cartella di lavoro configurazione Microsoft Excel che genera pronto a portata di blocchi di comandi di PowerShell in base alle impostazioni personalizzate, vedere [autenticazione federata per Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="d8890-214">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
<span data-ttu-id="d8890-215">Ottenere il nome della sottoscrizione utilizzando il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="d8890-215">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="d8890-216">Per le versioni precedenti di Azure PowerShell, utilizzare questo comando.</span><span class="sxs-lookup"><span data-stu-id="d8890-216">For older versions of Azure PowerShell, use this command instead.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select SubscriptionName
```

<span data-ttu-id="d8890-p110">Impostare la sottoscrizione di Azure. Sostituire tutte le virgolette, incluse le \< e > caratteri, con il nome corretto.</span><span class="sxs-lookup"><span data-stu-id="d8890-p110">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="d8890-p111">Successivamente, creare i nuovi gruppi di risorse. Per determinare un set di nomi dei gruppi di risorse univoci, utilizzare questo comando per creare un elenco dei gruppi di risorse esistenti.</span><span class="sxs-lookup"><span data-stu-id="d8890-p111">Next, create the new resource groups. To determine a unique set of resource group names, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="d8890-221">Compilare la tabella seguente per il set di nomi dei gruppi di risorse univoci.</span><span class="sxs-lookup"><span data-stu-id="d8890-221">Fill in the following table for the set of unique resource group names.</span></span>
  
|<span data-ttu-id="d8890-222">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="d8890-222">**Item**</span></span>|<span data-ttu-id="d8890-223">**Nome del gruppo di risorse**</span><span class="sxs-lookup"><span data-stu-id="d8890-223">**Resource group name**</span></span>|<span data-ttu-id="d8890-224">**Scopo**</span><span class="sxs-lookup"><span data-stu-id="d8890-224">**Purpose**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="d8890-225">1.</span><span class="sxs-lookup"><span data-stu-id="d8890-225">1.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |<span data-ttu-id="d8890-226">Controller di dominio</span><span class="sxs-lookup"><span data-stu-id="d8890-226">Domain controllers</span></span>  <br/> |
|<span data-ttu-id="d8890-227">2.</span><span class="sxs-lookup"><span data-stu-id="d8890-227">2.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |<span data-ttu-id="d8890-228">Server AD FS</span><span class="sxs-lookup"><span data-stu-id="d8890-228">AD FS servers</span></span>  <br/> |
|<span data-ttu-id="d8890-229">3.</span><span class="sxs-lookup"><span data-stu-id="d8890-229">3.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |<span data-ttu-id="d8890-230">Server proxy di applicazione Web</span><span class="sxs-lookup"><span data-stu-id="d8890-230">Web application proxy servers</span></span>  <br/> |
|<span data-ttu-id="d8890-231">4.</span><span class="sxs-lookup"><span data-stu-id="d8890-231">4.</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |<span data-ttu-id="d8890-232">Elementi dell'infrastruttura</span><span class="sxs-lookup"><span data-stu-id="d8890-232">Infrastructure elements</span></span>  <br/> |
   
 <span data-ttu-id="d8890-233">**Tabella r: gruppi di risorse**</span><span class="sxs-lookup"><span data-stu-id="d8890-233">**Table R: Resource groups**</span></span>
  
<span data-ttu-id="d8890-234">Creare i nuovi gruppi di risorse con questi comandi.</span><span class="sxs-lookup"><span data-stu-id="d8890-234">Create your new resource groups with these commands.</span></span>
  
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

<span data-ttu-id="d8890-235">Successivamente, creare la rete virtuale di Azure e le relative subnet.</span><span class="sxs-lookup"><span data-stu-id="d8890-235">Next, you create the Azure virtual network and its subnets.</span></span>
  
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

<span data-ttu-id="d8890-p112">È quindi creare rete gruppi di sicurezza per ogni subnet che contiene le macchine virtuali. Per eseguire isolamento subnet, è possibile aggiungere regole per specifici tipi di traffico concesse o negate al gruppo di protezione di rete di una subnet.</span><span class="sxs-lookup"><span data-stu-id="d8890-p112">Next, you create network security groups for each subnet that contains virtual machines. To perform subnet isolation, you can add rules for the specific types of traffic allowed or denied to the network security group of a subnet.</span></span>
  
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

<span data-ttu-id="d8890-238">Successivamente, utilizzare questi comandi per creare i gateway per la connessione VPN da sito a sito.</span><span class="sxs-lookup"><span data-stu-id="d8890-238">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
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
> <span data-ttu-id="d8890-p113">Le risorse locali non utilizzano l'autenticazione federata dei singoli utenti. Tuttavia, se la connessione VPN da sito risulta disponibile, i controller di dominio di VNet non riceverà aggiornamenti agli account utente e gruppi apportati in locale Windows Server Active Directory. Per garantire che non accade, è possibile configurare la disponibilità elevata per la connessione di rete VPN del sito per sito. Per ulteriori informazioni, vedere [altamente disponibili tra locali e la connettività VNet-VNet](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="d8890-p113">Federated authentication of individual users does not rely on any on-premises resources. However, if this site-to-site VPN connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your site-to-site VPN connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="d8890-243">Successivamente, registrare l'indirizzo IPv4 pubblico del gateway VPN di Azure per la rete virtuale visualizzato con questo comando:</span><span class="sxs-lookup"><span data-stu-id="d8890-243">Next, record the public IPv4 address of the Azure VPN gateway for your virtual network from the display of this command:</span></span>
  
```
Get-AzureRMPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

<span data-ttu-id="d8890-p114">Configurare quindi il dispositivo VPN in locale per la connessione al gateway VPN Azure. Per ulteriori informazioni, vedere [configurare il dispositivo VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="d8890-p114">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="d8890-246">Per configurare il dispositivo VPN locale, è necessario quanto segue:</span><span class="sxs-lookup"><span data-stu-id="d8890-246">To configure your on-premises VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="d8890-247">L'indirizzo IPv4 pubblico del gateway VPN di Azure.</span><span class="sxs-lookup"><span data-stu-id="d8890-247">The public IPv4 address of the Azure VPN gateway.</span></span>
    
- <span data-ttu-id="d8890-248">Il tasto già condiviso IPsec per la connessione VPN da sito (colonna di tabella V - elemento 5 - valore).</span><span class="sxs-lookup"><span data-stu-id="d8890-248">The IPsec pre-shared key for the site-to-site VPN connection (Table V - Item 5 - Value column).</span></span>
    
<span data-ttu-id="d8890-p115">Successivamente, assicurarsi che lo spazio di indirizzi della rete virtuale sia raggiungibile dalla rete locale. In genere è possibile aggiungere una route corrispondente allo spazio di indirizzi di rete virtuali al dispositivo VPN e quindi distribuire tale route al resto dell'infrastruttura di routing della rete dell'organizzazione. A tale scopo, consultare il proprio reparto IT.</span><span class="sxs-lookup"><span data-stu-id="d8890-p115">Next, ensure that the address space of the virtual network is reachable from your on-premises network. This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network. Work with your IT department to determine how to do this.</span></span>
  
<span data-ttu-id="d8890-p116">Successivamente, definire i nomi di tre set di disponibilità. Compilare la tabella A. </span><span class="sxs-lookup"><span data-stu-id="d8890-p116">Next, define the names of three availability sets. Fill out Table A.</span></span> 
  
|<span data-ttu-id="d8890-254">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="d8890-254">**Item**</span></span>|<span data-ttu-id="d8890-255">**Scopo**</span><span class="sxs-lookup"><span data-stu-id="d8890-255">**Purpose**</span></span>|<span data-ttu-id="d8890-256">**Nome del set di disponibilità**</span><span class="sxs-lookup"><span data-stu-id="d8890-256">**Availability set name**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="d8890-257">1.</span><span class="sxs-lookup"><span data-stu-id="d8890-257">1.</span></span>  <br/> |<span data-ttu-id="d8890-258">Controller di dominio</span><span class="sxs-lookup"><span data-stu-id="d8890-258">Domain controllers</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="d8890-259">2.</span><span class="sxs-lookup"><span data-stu-id="d8890-259">2.</span></span>  <br/> |<span data-ttu-id="d8890-260">Server AD FS</span><span class="sxs-lookup"><span data-stu-id="d8890-260">AD FS servers</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
|<span data-ttu-id="d8890-261">3.</span><span class="sxs-lookup"><span data-stu-id="d8890-261">3.</span></span>  <br/> |<span data-ttu-id="d8890-262">Server proxy di applicazione Web</span><span class="sxs-lookup"><span data-stu-id="d8890-262">Web application proxy servers</span></span>  <br/> |![](./images/Common_Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="d8890-263">**Set di disponibilità a: tabella**</span><span class="sxs-lookup"><span data-stu-id="d8890-263">**Table A: Availability sets**</span></span>
  
<span data-ttu-id="d8890-264">Questi nomi sono necessari quando si creano le macchine virtuali nelle fasi 2, 3 e 4.</span><span class="sxs-lookup"><span data-stu-id="d8890-264">You will need these names when you create the virtual machines in phases 2, 3, and 4.</span></span>
  
<span data-ttu-id="d8890-265">Creare i nuovi set di disponibilità con questi comandi di Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d8890-265">Create the new availability sets with these Azure PowerShell commands.</span></span>
  
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

<span data-ttu-id="d8890-266">Questa è la configurazione risultante dal completamento corretto di questa fase.</span><span class="sxs-lookup"><span data-stu-id="d8890-266">This is the configuration resulting from the successful completion of this phase.</span></span>
  
<span data-ttu-id="d8890-267">**Fase 1: L'infrastruttura per l'autenticazione federata di disponibilità elevata per Office 365**</span><span class="sxs-lookup"><span data-stu-id="d8890-267">**Phase 1: The Azure infrastructure for high availability federated authentication for Office 365**</span></span>

![Fase 1 dell'autenticazione federata di Office 365 con disponibilità elevata in Azure con l'infrastruttura di Azure](images/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a><span data-ttu-id="d8890-269">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="d8890-269">Next step</span></span>

<span data-ttu-id="d8890-270">Utilizzare [la disponibilità elevata federati autenticazione fase 2: configurare i controller di dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) per continuare con la configurazione di questo carico di lavoro.</span><span class="sxs-lookup"><span data-stu-id="d8890-270">Use [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) to continue with the configuration of this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d8890-271">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d8890-271">See Also</span></span>

[<span data-ttu-id="d8890-272">Distribuire l'autenticazione federata ad alta visibilità per Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="d8890-272">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="d8890-273">Identità federata per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="d8890-273">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="d8890-274">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="d8890-274">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="d8890-275">Identità federata per Office 365</span><span class="sxs-lookup"><span data-stu-id="d8890-275">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


