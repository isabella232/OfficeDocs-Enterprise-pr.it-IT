---
title: Progettazione di rete per Microsoft SaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: "Riepilogo: Informazioni su come ottimizzare la rete per l'accesso ai servizi SaaS di Microsoft, tra cui Office 365, Microsoft Intune e Dynamics 365."
ms.openlocfilehash: 4cfbeab3d90703e17c86e707988a8a62c937df9a
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="f8516-103">Progettazione di rete per Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="f8516-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="f8516-104">**Riepilogo:** Informazioni su come ottimizzare la rete per l'accesso ai servizi SaaS di Microsoft, tra cui Office 365, Microsoft Intune e Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="f8516-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="f8516-105">L'ottimizzazione della rete per i servizi SaaS di Microsoft richiede un'analisi approfondita della connessione Internet, dei dispositivi client e delle operazioni IT tipiche.</span><span class="sxs-lookup"><span data-stu-id="f8516-105">Optimizing your network for Microsoft SaaS services requires careful analysis of your Internet edge, your client devices, and typical IT operations.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="f8516-106">Passaggi di preparazione della rete per i servizi Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="f8516-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="f8516-107">Eseguire la procedura seguente per ottimizzare la rete per i servizi Microsoft SaaS:</span><span class="sxs-lookup"><span data-stu-id="f8516-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="f8516-108">Passare attraverso la sezione **operazioni per preparare la rete di servizi cloud Microsoft** in [elementi comuni di integrazione applicativa di Microsoft cloud](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="f8516-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="f8516-109">Ottimizzare l'uscita Internet per i servizi Microsoft SaaS utilizzando i consigli relativi al server proxy.</span><span class="sxs-lookup"><span data-stu-id="f8516-109">Optimize your Internet egress for Microsoft SaaS services using the proxy server recommendations.</span></span>
    
3. <span data-ttu-id="f8516-110">Ottimizzare la velocità effettiva Internet utilizzando i suggerimenti di prossimità e il percorso.</span><span class="sxs-lookup"><span data-stu-id="f8516-110">Optimize your Internet throughput using the proximity and location recommendations.</span></span>
    
4. <span data-ttu-id="f8516-111">Ottimizzare le prestazioni dei computer client e la rete intranet in cui si trovano utilizzando le considerazioni sull'utilizzo di client.</span><span class="sxs-lookup"><span data-stu-id="f8516-111">Optimize the performance of your client computers and the intranet on which they are located using the client usage considerations.</span></span>
    
5. <span data-ttu-id="f8516-112">In base alle esigenze, ottimizzare le prestazioni di sincronizzazione mediante le considerazioni di operazioni IT e le migrazioni dei dati.</span><span class="sxs-lookup"><span data-stu-id="f8516-112">As needed, optimize the performance of data migrations and synchronization using the IT operations considerations.</span></span>
    
## <a name="internet-edge-considerations"></a><span data-ttu-id="f8516-113">Considerazioni su edge Internet</span><span class="sxs-lookup"><span data-stu-id="f8516-113">Internet edge considerations</span></span>

<span data-ttu-id="f8516-114">Ecco alcuni aspetti da considerare ottimizzare il bordo di Internet e velocità effettiva ai servizi Microsoft SaaS.</span><span class="sxs-lookup"><span data-stu-id="f8516-114">Here are some things to consider optimize your Internet edge and throughput to Microsoft SaaS services.</span></span>
  
<span data-ttu-id="f8516-115">**Nella figura 1: Opzioni di connessione per i servizi Microsoft SaaS**</span><span class="sxs-lookup"><span data-stu-id="f8516-115">**Figure 1: Connection options for Microsoft SaaS services**</span></span>

![Figura 1: Opzioni di connessione per i servizi Microsoft SaaS](images/Network_Poster/SaaS1.png)
  
<span data-ttu-id="f8516-117">Una rete locale connettersi ai servizi Microsoft SaaS su una barra verticale Internet o ExpressRoute illustrato nella figura 1.</span><span class="sxs-lookup"><span data-stu-id="f8516-117">Figure 1 shows an on-premises network connecting to Microsoft SaaS services over an Internet pipe or ExpressRoute.</span></span>
  
<span data-ttu-id="f8516-118">Di seguito sono riportati alcuni consigli per ottimizzare il server proxy:</span><span class="sxs-lookup"><span data-stu-id="f8516-118">Here are some recommendations to optimize your proxy server:</span></span>
  
- <span data-ttu-id="f8516-119">Configurare i client web utilizzando WPAD, PAC o oggetto Criteri di gruppo</span><span class="sxs-lookup"><span data-stu-id="f8516-119">Configure web clients using WPAD, PAC, or GPO</span></span>
    
- <span data-ttu-id="f8516-120">Non utilizzare intercettazione SSL</span><span class="sxs-lookup"><span data-stu-id="f8516-120">Don't use SSL interception</span></span>
    
- <span data-ttu-id="f8516-121">Utilizzare un file PAC per ignorare il proxy per i nomi DNS servizio SaaS Microsoft</span><span class="sxs-lookup"><span data-stu-id="f8516-121">Use a PAC file to bypass the proxy for Microsoft SaaS service DNS names</span></span>
    
- <span data-ttu-id="f8516-122">Consentire il traffico per la verifica di revoche di certificati/OCSP</span><span class="sxs-lookup"><span data-stu-id="f8516-122">Allow traffic for CRL/OCSP verification</span></span>
    
<span data-ttu-id="f8516-123">Ecco alcuni colli di bottiglia server proxy per controllare:</span><span class="sxs-lookup"><span data-stu-id="f8516-123">Here are some proxy server bottlenecks to check:</span></span>
  
- <span data-ttu-id="f8516-124">Connessioni permanenti insufficienti (Outlook)</span><span class="sxs-lookup"><span data-stu-id="f8516-124">Insufficient persistent connections (Outlook)</span></span>
    
- <span data-ttu-id="f8516-125">Capacità insufficiente</span><span class="sxs-lookup"><span data-stu-id="f8516-125">Insufficient capacity</span></span>
    
- <span data-ttu-id="f8516-126">Valutazione off rete pur</span><span class="sxs-lookup"><span data-stu-id="f8516-126">Doing off-network evaluation</span></span>
    
- <span data-ttu-id="f8516-127">La richiesta di autenticazione</span><span class="sxs-lookup"><span data-stu-id="f8516-127">Requiring authentication</span></span>
    
- <span data-ttu-id="f8516-128">Nessun supporto per il traffico UDP (Skype per le aziende)</span><span class="sxs-lookup"><span data-stu-id="f8516-128">No support for UDP traffic (Skype for Business)</span></span>
    
<span data-ttu-id="f8516-129">Di seguito sono riportati alcuni consigli prossimità e il percorso:</span><span class="sxs-lookup"><span data-stu-id="f8516-129">Here are some proximity and location recommendations:</span></span>
  
- <span data-ttu-id="f8516-130">Non eseguire il routing del traffico Internet nella rete WAN privata</span><span class="sxs-lookup"><span data-stu-id="f8516-130">Don't route your Internet traffic over the private WAN</span></span>
    
- <span data-ttu-id="f8516-131">Utilizzare il flusso di traffico DNS e Internet nell'area per gli utenti di fuori dell'area</span><span class="sxs-lookup"><span data-stu-id="f8516-131">Use in-region DNS and Internet traffic flow for out-of-region users</span></span>
    
- <span data-ttu-id="f8516-132">Utilizzare ExpressRoute per connessioni a banda larga per Office 365 e la connettività simultanea con servizi di Azure</span><span class="sxs-lookup"><span data-stu-id="f8516-132">Use ExpressRoute for high bandwidth to Office 365 and concurrent connectivity with Azure services</span></span>
    
<span data-ttu-id="f8516-133">Di seguito sono le porte in uscita necessarie per il traffico di Office 365:</span><span class="sxs-lookup"><span data-stu-id="f8516-133">Here are the outbound ports needed for Office 365 traffic:</span></span>
  
- <span data-ttu-id="f8516-134">TCP 80 (per i controlli di revoche di certificati/OCSP)</span><span class="sxs-lookup"><span data-stu-id="f8516-134">TCP 80 (for CRL/OCSP checks)</span></span>
    
- <span data-ttu-id="f8516-135">TCP 443</span><span class="sxs-lookup"><span data-stu-id="f8516-135">TCP 443</span></span>
    
- <span data-ttu-id="f8516-136">UDP 3478</span><span class="sxs-lookup"><span data-stu-id="f8516-136">UDP 3478</span></span>
    
- <span data-ttu-id="f8516-137">TCP 5223</span><span class="sxs-lookup"><span data-stu-id="f8516-137">TCP 5223</span></span>
    
- <span data-ttu-id="f8516-138">TCP 50000 A 59999</span><span class="sxs-lookup"><span data-stu-id="f8516-138">TCP 50000-59999</span></span>
    
- <span data-ttu-id="f8516-139">UDP 50000 A 59999</span><span class="sxs-lookup"><span data-stu-id="f8516-139">UDP 50000-59999</span></span>
    
## <a name="client-usage-considerations"></a><span data-ttu-id="f8516-140">Considerazioni sull'utilizzo di client</span><span class="sxs-lookup"><span data-stu-id="f8516-140">Client usage considerations</span></span>

<span data-ttu-id="f8516-141">Innanzitutto configurare il gruppo di servizi che i client utilizzeranno, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f8516-141">First, configure the set of services that your clients will be using, such as:</span></span>
  
- <span data-ttu-id="f8516-142">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="f8516-142">Azure Active Directory</span></span>
    
- <span data-ttu-id="f8516-143">Office 365</span><span class="sxs-lookup"><span data-stu-id="f8516-143">Office 365</span></span>
    
  - <span data-ttu-id="f8516-144">Applicazioni client di Office</span><span class="sxs-lookup"><span data-stu-id="f8516-144">Office client apps</span></span>
    
  - <span data-ttu-id="f8516-145">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="f8516-145">SharePoint Online</span></span>
    
  - <span data-ttu-id="f8516-146">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="f8516-146">Exchange Online</span></span>
    
  - <span data-ttu-id="f8516-147">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="f8516-147">Skype for Business</span></span>
    
- <span data-ttu-id="f8516-148">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="f8516-148">Microsoft Intune</span></span>
    
- <span data-ttu-id="f8516-149">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="f8516-149">Dynamics 365</span></span>
    
<span data-ttu-id="f8516-150">Per i computer client, determinare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="f8516-150">For your client computers, determine the following:</span></span>
  
- <span data-ttu-id="f8516-151">Numero massimo in qualsiasi momento (ora del giorni, stagionali, picchi e gestirle in uso)</span><span class="sxs-lookup"><span data-stu-id="f8516-151">Maximum number at any one time (time of day, seasonal, peaks and troughs in usage)</span></span>
    
- <span data-ttu-id="f8516-152">Totale della larghezza di banda necessaria per picchi</span><span class="sxs-lookup"><span data-stu-id="f8516-152">Total bandwidth needed for peaks</span></span>
    
- <span data-ttu-id="f8516-153">Latenza per il dispositivo di uscita Internet</span><span class="sxs-lookup"><span data-stu-id="f8516-153">Latency to the Internet egress device</span></span>
    
- <span data-ttu-id="f8516-154">Paese di origine e paese di posizione condivisa datacenter</span><span class="sxs-lookup"><span data-stu-id="f8516-154">Country of origin vs. country of datacenter co-location</span></span>
    
<span data-ttu-id="f8516-155">Per ogni tipo di client (PC, smartphone o tablet), verificare che l'oggetto corrente:</span><span class="sxs-lookup"><span data-stu-id="f8516-155">For each type of client (PC, smartphone, tablet), ensure the current:</span></span>
  
- <span data-ttu-id="f8516-156">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="f8516-156">Operating system</span></span>
    
- <span data-ttu-id="f8516-157">Browser Internet</span><span class="sxs-lookup"><span data-stu-id="f8516-157">Internet browser</span></span>
    
- <span data-ttu-id="f8516-158">Stack TCP/IP</span><span class="sxs-lookup"><span data-stu-id="f8516-158">TCP/IP stack</span></span>
    
- <span data-ttu-id="f8516-159">Hardware di rete</span><span class="sxs-lookup"><span data-stu-id="f8516-159">Network hardware</span></span>
    
- <span data-ttu-id="f8516-160">Driver del sistema operativo per l'hardware di rete</span><span class="sxs-lookup"><span data-stu-id="f8516-160">OS drivers for network hardware</span></span>
    
- <span data-ttu-id="f8516-161">Sono installate gli aggiornamenti e patch</span><span class="sxs-lookup"><span data-stu-id="f8516-161">Updates and patches are installed</span></span>
    
<span data-ttu-id="f8516-162">Inoltre, ottimizzare la velocità effettiva connessione intranet (cablata, senza fili o VPN).</span><span class="sxs-lookup"><span data-stu-id="f8516-162">Additionally, optimize intranet connection throughput (wired, wireless, or VPN).</span></span>
  
<span data-ttu-id="f8516-163">Per ulteriori informazioni, vedere [supporto di NAT con Office 365](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9).</span><span class="sxs-lookup"><span data-stu-id="f8516-163">For more information, see [NAT support with Office 365](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9).</span></span>
  
<span data-ttu-id="f8516-164">Per i suggerimenti più recenti per l'utilizzo di ExpressRoute con Office 365, vedere [ExpressRoute per Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span><span class="sxs-lookup"><span data-stu-id="f8516-164">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
<span data-ttu-id="f8516-165">Per ottimizzare le prestazioni di rete intranet, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f8516-165">To optimize your intranet performance, do the following:</span></span>
  
- <span data-ttu-id="f8516-166">Utilizzare gli strumenti per misurare andata tempi (RTTs) per i dispositivi edge Internet (PsPing, il comando Ping, Tracert, TraceTCP, Network Monitor)</span><span class="sxs-lookup"><span data-stu-id="f8516-166">Use tools to gauge round trip times (RTTs) to your Internet edge devices (PsPing, Ping, Tracert, TraceTCP, Network Monitor)</span></span>
    
- <span data-ttu-id="f8516-167">Eseguire l'analisi del percorso di uscita utilizzando i protocolli di flusso</span><span class="sxs-lookup"><span data-stu-id="f8516-167">Perform egress path analysis using flow protocols</span></span>
    
- <span data-ttu-id="f8516-168">Eseguire l'analisi dei dispositivi intermedi (età, integrità e così via)</span><span class="sxs-lookup"><span data-stu-id="f8516-168">Perform analysis of intermediate devices (age, health, etc.)</span></span>
    
<span data-ttu-id="f8516-169">Per ulteriori informazioni, vedere [strumento PsPing](https://technet.microsoft.com/sysinternals/jj729731.aspx).</span><span class="sxs-lookup"><span data-stu-id="f8516-169">For more information, see the [PsPing tool](https://technet.microsoft.com/sysinternals/jj729731.aspx).</span></span>
  
## <a name="it-operations-considerations"></a><span data-ttu-id="f8516-170">Considerazioni sulle operazioni IT</span><span class="sxs-lookup"><span data-stu-id="f8516-170">IT operations considerations</span></span>

<span data-ttu-id="f8516-171">Ecco alcuni aspetti da considerare durante il funzionamento di un carico di lavoro in un servizio SaaS Microsoft IT.</span><span class="sxs-lookup"><span data-stu-id="f8516-171">Here are some things to consider when operating an IT workload in a Microsoft SaaS service.</span></span>
  
### <a name="one-time-migrations"></a><span data-ttu-id="f8516-172">Migrazioni occasionale</span><span class="sxs-lookup"><span data-stu-id="f8516-172">One-time migrations</span></span>

<span data-ttu-id="f8516-173">Esempi di migrazioni occasionale sono trasferimento di dati di blocco per le applicazioni basate su cloud o l'archiviazione di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="f8516-173">Examples of one-time migrations are bulk data transfer for cloud-based applications or archival storage.</span></span>
  
<span data-ttu-id="f8516-174">Per ottimizzare la rete per le migrazioni nel tempo:</span><span class="sxs-lookup"><span data-stu-id="f8516-174">To optimize your network for on-time migrations:</span></span>
  
- <span data-ttu-id="f8516-175">Evitare l'utilizzo massimo della rete e dei computer applicate patch per orari</span><span class="sxs-lookup"><span data-stu-id="f8516-175">Avoid peak network usage and computer patching times</span></span>
    
- <span data-ttu-id="f8516-176">Deve essere inseriti nella previsione e un progetto pilota, valutare l'integrità della rete e risolvere i problemi prima di tentare di migrazione effettiva</span><span class="sxs-lookup"><span data-stu-id="f8516-176">Should be baselined and piloted, assess network health and resolve issues before attempting actual migration</span></span>
    
- <span data-ttu-id="f8516-177">Eseguire finale per le migrazioni future</span><span class="sxs-lookup"><span data-stu-id="f8516-177">Perform post-mortem for future migrations</span></span>
    
### <a name="ongoing-synchronizations"></a><span data-ttu-id="f8516-178">Sincronizzazione in corso</span><span class="sxs-lookup"><span data-stu-id="f8516-178">Ongoing synchronizations</span></span>

<span data-ttu-id="f8516-179">Esempi di sincronizzazione in corso sono le informazioni di directory, le impostazioni o i file.</span><span class="sxs-lookup"><span data-stu-id="f8516-179">Examples of ongoing synchronizations are directory information, settings, or files.</span></span>
  
<span data-ttu-id="f8516-180">Per ottimizzare la rete per la sincronizzazione in corso:</span><span class="sxs-lookup"><span data-stu-id="f8516-180">To optimize your network for ongoing synchronizations:</span></span>
  
- <span data-ttu-id="f8516-181">Verificare che una larghezza di banda del sistema di monitoraggio sul posto, risolvere o ignorare errori raccolti</span><span class="sxs-lookup"><span data-stu-id="f8516-181">Ensure that a network bandwidth monitoring system is in place, resolve or dismiss collected errors</span></span>
    
- <span data-ttu-id="f8516-182">Utilizzare i risultati del monitoraggio della larghezza di banda per determinare la necessità di modifiche alla rete (su scalabilità, nuovi circuiti o dispositivi aggiunta)</span><span class="sxs-lookup"><span data-stu-id="f8516-182">Use bandwidth monitoring results to determine need for network changes (scale-up/out, new circuits, or adding devices)</span></span>
    
<span data-ttu-id="f8516-183">Per ulteriori informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="f8516-183">For more information, see:</span></span>
  
- [<span data-ttu-id="f8516-184">Pianificazione per Office 365 e rete</span><span class="sxs-lookup"><span data-stu-id="f8516-184">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
- [<span data-ttu-id="f8516-185">ExpressRoute per Office 365</span><span class="sxs-lookup"><span data-stu-id="f8516-185">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)

## <a name="next-step"></a><span data-ttu-id="f8516-186">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="f8516-186">Next step</span></span>

[<span data-ttu-id="f8516-187">Progettazione di rete per Microsoft Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="f8516-187">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="f8516-188">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f8516-188">See also</span></span>

[<span data-ttu-id="f8516-189">Rete cloud Microsoft per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="f8516-189">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="f8516-190">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="f8516-190">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="f8516-191">Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT</span><span class="sxs-lookup"><span data-stu-id="f8516-191">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



