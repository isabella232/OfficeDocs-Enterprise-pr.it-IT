---
title: "Distribuire l'autenticazione federata ad alta visibilità per Office 365 in Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: "Riepilogo: Configurare l'autenticazione federata a disponibilità elevata per l'abbonamento a Office 365 in Microsoft Azure."
ms.openlocfilehash: 111e52531e45e54b8ce53c3f530e9c9d273f24fc
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="deploy-high-availability-federated-authentication-for-office-365-in-azure"></a><span data-ttu-id="3babf-103">Distribuire l'autenticazione federata ad alta visibilità per Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="3babf-103">Deploy high availability federated authentication for Office 365 in Azure</span></span>

 <span data-ttu-id="3babf-104">**Riepilogo:** Configurare l'autenticazione federata a disponibilità elevata per l'abbonamento a Office 365 in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="3babf-104">**Summary:** Configure high availability federated authentication for your Office 365 subscription in Microsoft Azure.</span></span>
  
<span data-ttu-id="3babf-105">In questo articolo sono riportati i collegamenti a istruzioni dettagliate per la distribuzione dell'autenticazione federata a disponibilità elevata per Microsoft Office 365 in servizi infrastruttura di Azure con queste macchine virtuali:</span><span class="sxs-lookup"><span data-stu-id="3babf-105">This article contains links to the step-by-step instructions for deploying high availability federated authentication for Microsoft Office 365 in Azure infrastructure services with these virtual machines:</span></span>
  
- <span data-ttu-id="3babf-106">Due server proxy di applicazione Web</span><span class="sxs-lookup"><span data-stu-id="3babf-106">Two web application proxy servers</span></span>
    
- <span data-ttu-id="3babf-107">Due server Active Directory Federation Services (AD FS)</span><span class="sxs-lookup"><span data-stu-id="3babf-107">Two Active Directory Federation Services (AD FS) servers</span></span>
    
- <span data-ttu-id="3babf-108">Due controller di dominio di replica</span><span class="sxs-lookup"><span data-stu-id="3babf-108">Two replica domain controllers</span></span>
    
- <span data-ttu-id="3babf-109">Un server di sincronizzazione della directory (DirSync) che esegue Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="3babf-109">One directory synchronization (DirSync) server running Azure AD Connect</span></span>
    
<span data-ttu-id="3babf-110">Di seguito viene riportata la configurazione, con i nomi segnaposto per ogni server.</span><span class="sxs-lookup"><span data-stu-id="3babf-110">Here is the configuration, with placeholder names for each server.</span></span>
  
<span data-ttu-id="3babf-111">**Un'autenticazione federata a disponibilità elevata per l'infrastruttura di Office 365 in Azure**</span><span class="sxs-lookup"><span data-stu-id="3babf-111">**A high availability federated authentication for Office 365 infrastructure in Azure**</span></span>

![La configurazione finale dell'infrastruttura di autenticazione federata di Office 365 con disponibilità elevata](images/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="3babf-113">Tutte le macchine virtuali si trovano in una singola rete virtuale di Azure (VNet) cross-premise.</span><span class="sxs-lookup"><span data-stu-id="3babf-113">All of the virtual machines are in a single cross-premises Azure virtual network (VNet).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="3babf-p101">L'autenticazione federata di singoli utenti non fa affidamento ad alcuna risorsa locale. Tuttavia, se la connessione cross-premise non è più disponibile, i controller di dominio della VNet non riceveranno aggiornamenti sugli account utente e sui gruppi creati nell'AD di Windows Server locale. Affinché ciò non si verifichi, è possibile configurare la disponibilità elevata per la connessione cross-premise. Per maggiori informazioni, vedere [Connettività cross-premise e da rete virtuale a rete virtuale a disponibilità elevata](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="3babf-p101">Federated authentication of individual users does not rely on any on-premises resources. However, if the cross-premises connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your cross-premises connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="3babf-118">Ogni coppia di macchine virtuali per un ruolo specifico si trova nella propria subnet e nel set di disponibilità.</span><span class="sxs-lookup"><span data-stu-id="3babf-118">Each pair of virtual machines for a specific role is in its own subnet and availability set.</span></span>
  
> [!NOTE]
> <span data-ttu-id="3babf-p102">Poiché tale VNet è connessa alla rete locale, questa configurazione non include jumpbox o macchine virtuali di monitoraggio in una subnet di gestione. Per ulteriori informazioni, vedere [Esecuzione di macchine virtuali Windows per un'architettura a N livelli](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span><span class="sxs-lookup"><span data-stu-id="3babf-p102">Because this VNet is connected to the on-premises network, this configuration does not include jumpbox or monitoring virtual machines on a management subnet. For more information, see [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span></span> 
  
<span data-ttu-id="3babf-p103">A seguito di questa configurazione, tutti gli utenti di Office 365 avranno a disposizione l'autenticazione federata e potranno accedere usando le credenziali di Windows Server Active Directory anziché l'account di Office 365. L'infrastruttura di autenticazione federata utilizza un set ridondante di server che vengono distribuiti nei servizi dell'infrastruttura di Azure invece che nella rete perimetrale locale.</span><span class="sxs-lookup"><span data-stu-id="3babf-p103">The result of this configuration is that you will have federated authentication for all of your Office 365 users, in which they can use their Windows Server Active Directory credentials to sign in rather than their Office 365 account. The federated authentication infrastructure uses a redundant set of servers that are more easily deployed in Azure infrastructure services, rather than in your on-premises edge network.</span></span>
  
## <a name="bill-of-materials"></a><span data-ttu-id="3babf-123">Distinta base</span><span class="sxs-lookup"><span data-stu-id="3babf-123">Bill of materials</span></span>

<span data-ttu-id="3babf-124">Questa configurazione di base richiede l'insieme di componenti e servizi di Azure seguente:</span><span class="sxs-lookup"><span data-stu-id="3babf-124">This baseline configuration requires the following set of Azure services and components:</span></span>
  
- <span data-ttu-id="3babf-125">Sette macchine virtuali</span><span class="sxs-lookup"><span data-stu-id="3babf-125">Seven virtual machines</span></span>
    
- <span data-ttu-id="3babf-126">Una rete virtuale cross-premise con quattro subnet</span><span class="sxs-lookup"><span data-stu-id="3babf-126">One cross-premises virtual network with four subnets</span></span>
    
- <span data-ttu-id="3babf-127">Quattro gruppi di risorse</span><span class="sxs-lookup"><span data-stu-id="3babf-127">Four resource groups</span></span>
    
- <span data-ttu-id="3babf-128">Tre set di disponibilità</span><span class="sxs-lookup"><span data-stu-id="3babf-128">Three availability sets</span></span>
    
- <span data-ttu-id="3babf-129">Un abbonamento di Azure</span><span class="sxs-lookup"><span data-stu-id="3babf-129">One Azure subscription</span></span>
    
<span data-ttu-id="3babf-130">Di seguito sono riportate le macchine virtuali e le rispettive dimensioni predefinite per questa configurazione.</span><span class="sxs-lookup"><span data-stu-id="3babf-130">Here are the virtual machines and their default sizes for this configuration.</span></span>
  
|<span data-ttu-id="3babf-131">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="3babf-131">**Item**</span></span>|<span data-ttu-id="3babf-132">**Descrizione macchina virtuale**</span><span class="sxs-lookup"><span data-stu-id="3babf-132">**Virtual machine description**</span></span>|<span data-ttu-id="3babf-133">**Immagine della raccolta Azure**</span><span class="sxs-lookup"><span data-stu-id="3babf-133">**Azure gallery image**</span></span>|<span data-ttu-id="3babf-134">**Dimensione predefinita**</span><span class="sxs-lookup"><span data-stu-id="3babf-134">**Default size**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="3babf-135">1.</span><span class="sxs-lookup"><span data-stu-id="3babf-135">1.</span></span>  <br/> |<span data-ttu-id="3babf-136">Primo controller di dominio</span><span class="sxs-lookup"><span data-stu-id="3babf-136">First domain controller</span></span>  <br/> |<span data-ttu-id="3babf-137">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="3babf-137">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="3babf-138">D2</span><span class="sxs-lookup"><span data-stu-id="3babf-138">D2</span></span>  <br/> |
|<span data-ttu-id="3babf-139">2.</span><span class="sxs-lookup"><span data-stu-id="3babf-139">2.</span></span>  <br/> |<span data-ttu-id="3babf-140">Secondo controller di dominio</span><span class="sxs-lookup"><span data-stu-id="3babf-140">Second domain controller</span></span>  <br/> |<span data-ttu-id="3babf-141">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="3babf-141">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="3babf-142">D2</span><span class="sxs-lookup"><span data-stu-id="3babf-142">D2</span></span>  <br/> |
|<span data-ttu-id="3babf-143">3.</span><span class="sxs-lookup"><span data-stu-id="3babf-143">3.</span></span>  <br/> |<span data-ttu-id="3babf-144">Server di Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="3babf-144">Azure AD Connect server</span></span>  <br/> |<span data-ttu-id="3babf-145">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="3babf-145">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="3babf-146">D2</span><span class="sxs-lookup"><span data-stu-id="3babf-146">D2</span></span>  <br/> |
|<span data-ttu-id="3babf-147">4.</span><span class="sxs-lookup"><span data-stu-id="3babf-147">4.</span></span>  <br/> |<span data-ttu-id="3babf-148">primo server AD FS</span><span class="sxs-lookup"><span data-stu-id="3babf-148">First AD FS server</span></span>  <br/> |<span data-ttu-id="3babf-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="3babf-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="3babf-150">D2</span><span class="sxs-lookup"><span data-stu-id="3babf-150">D2</span></span>  <br/> |
|<span data-ttu-id="3babf-151">5.</span><span class="sxs-lookup"><span data-stu-id="3babf-151">5.</span></span>  <br/> |<span data-ttu-id="3babf-152">Secondo server AD FS</span><span class="sxs-lookup"><span data-stu-id="3babf-152">Second AD FS server</span></span>  <br/> |<span data-ttu-id="3babf-153">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="3babf-153">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="3babf-154">D2</span><span class="sxs-lookup"><span data-stu-id="3babf-154">D2</span></span>  <br/> |
|<span data-ttu-id="3babf-155">6.</span><span class="sxs-lookup"><span data-stu-id="3babf-155">6.</span></span>  <br/> |<span data-ttu-id="3babf-156">Primo server proxy di applicazione Web</span><span class="sxs-lookup"><span data-stu-id="3babf-156">First web application proxy server</span></span>  <br/> |<span data-ttu-id="3babf-157">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="3babf-157">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="3babf-158">D2</span><span class="sxs-lookup"><span data-stu-id="3babf-158">D2</span></span>  <br/> |
|<span data-ttu-id="3babf-159">7.</span><span class="sxs-lookup"><span data-stu-id="3babf-159">7.</span></span>  <br/> |<span data-ttu-id="3babf-160">Secondo server proxy di applicazione Web</span><span class="sxs-lookup"><span data-stu-id="3babf-160">Second web application proxy server</span></span>  <br/> |<span data-ttu-id="3babf-161">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="3babf-161">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="3babf-162">D2</span><span class="sxs-lookup"><span data-stu-id="3babf-162">D2</span></span>  <br/> |
   
<span data-ttu-id="3babf-163">Per fare una stima dei costi per questa configurazione, vedere il [calcolatore dei prezzi Azure](https://azure.microsoft.com/pricing/calculator/)</span><span class="sxs-lookup"><span data-stu-id="3babf-163">To compute the estimated costs for this configuration, see the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/)</span></span>
  
## <a name="phases-of-deployment"></a><span data-ttu-id="3babf-164">Fasi di distribuzione</span><span class="sxs-lookup"><span data-stu-id="3babf-164">Phases of deployment</span></span>

<span data-ttu-id="3babf-165">Distribuire il carico di lavoro nelle fasi seguenti:</span><span class="sxs-lookup"><span data-stu-id="3babf-165">You deploy this workload in the following phases:</span></span>
  
<span data-ttu-id="3babf-166"><<<<<<< HEAD</span><span class="sxs-lookup"><span data-stu-id="3babf-166"><<<<<<< HEAD</span></span>
- <span data-ttu-id="3babf-p104">[Fase 1 dell'autenticazione federata a disponibilità elevata: Configurare Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Creare gruppi di risorse, account di archiviazione, set di disponibilità e una rete virtuale cross-premise.</span><span class="sxs-lookup"><span data-stu-id="3babf-p104">[High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="3babf-p105">[High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Creare e configurare i controller di dominio di Windows Server Active Directory (AD) di replica e il server DirSync.</span><span class="sxs-lookup"><span data-stu-id="3babf-p105">[High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Create and configure replica Windows Server Active Directory (AD) domain controllers and the DirSync server.</span></span>
    
- <span data-ttu-id="3babf-p106">[Fase 3 dell'autenticazione federata a disponibilità elevata: Configurare i server AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Creare e configurare i due server AD FS.</span><span class="sxs-lookup"><span data-stu-id="3babf-p106">[High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="3babf-p107">[Fase 4 dell'autenticazione federata a disponibilità elevata: Configurare i proxy dell'applicazione Web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Creare e configurare i due server proxy dell'applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="3babf-p107">[High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="3babf-p108">[Fase 5 dell'autenticazione federata a disponibilità elevata: Configurare l'autenticazione federata per Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configurare l'autenticazione federata per l'abbonamento di Office 365. =======</span><span class="sxs-lookup"><span data-stu-id="3babf-p108">[High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configure federated authentication for your Office 365 subscription. =======</span></span>
- <span data-ttu-id="3babf-177">[Fase 1 dell'autenticazione federata a disponibilità elevata: Configurare Azure](high-availability-federated-authentication-phase-1-configure-azure.md) - Creare gruppi di risorse, account di archiviazione, set di disponibilità e una rete virtuale cross-premise.</span><span class="sxs-lookup"><span data-stu-id="3babf-177">[High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md) - Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="3babf-178">[Fase 2 dell'autenticazione federata a disponibilità elevata: configurare i controller di dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Creare e configurare i controller di dominio di Windows Server Active Directory (AD) di replica e il server DirSync.</span><span class="sxs-lookup"><span data-stu-id="3babf-178">[High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) - Create and configure replica Windows Server Active Directory (AD) domain controllers and the DirSync server.</span></span>
    
- <span data-ttu-id="3babf-179">[Fase 3 dell'autenticazione federata a disponibilità elevata: Configurare i server AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) - Creare e configurare i due server AD FS.</span><span class="sxs-lookup"><span data-stu-id="3babf-179">[High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) - Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="3babf-180">[Fase 4 dell'autenticazione federata a disponibilità elevata: Configurare i proxy dell'applicazione Web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) - Creare e configurare i due server proxy dell'applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="3babf-180">[High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) - Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="3babf-181">[Fase 5 dell'autenticazione federata a disponibilità elevata: Configurare l'autenticazione federata per Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configurare l'autenticazione federata per l'abbonamento di Office 365.</span><span class="sxs-lookup"><span data-stu-id="3babf-181">[High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) - Configure federated authentication for your Office 365 subscription.</span></span>
>>>>>>> <span data-ttu-id="3babf-182">master</span><span class="sxs-lookup"><span data-stu-id="3babf-182">master</span></span>
    
<span data-ttu-id="3babf-p109">Questi articoli forniscono una guida dettagliata per un'architettura predefinita al fine di creare un'autenticazione federata a elevata funzionale per Office 365 nei servizi infrastruttura di Azure. Tenere presente quanto segue:</span><span class="sxs-lookup"><span data-stu-id="3babf-p109">These articles provide a prescriptive, phase-by-phase guide for a predefined architecture to create a functional, high availability federated authentication for Office 365 in Azure infrastructure services. Keep the following in mind:</span></span>
  
- <span data-ttu-id="3babf-185">Se si è un responsabile dell'implementazione AD FS esperto, adattare le istruzione fornite nelle fasi 3 e 4 e compilare il set di server più opportuno per le proprie esigenze.</span><span class="sxs-lookup"><span data-stu-id="3babf-185">If you are an experienced AD FS implementer, feel free to adapt the instructions in phases 3 and 4 and build the set of servers that best suits your needs.</span></span>
    
- <span data-ttu-id="3babf-186">Se si dispone già di una distribuzione cloud ibrida Azure con una rete virtuale cross-premise esistente, è possibile adattare o ignorare le istruzioni riportate nelle fasi 1 e 2 e posizionare i server proxy dell'applicazione Web e AD FS sulle subnet appropriate.</span><span class="sxs-lookup"><span data-stu-id="3babf-186">If you already have an existing Azure hybrid cloud deployment with an existing cross-premises virtual network, feel free to adapt or skip the instructions in phases 1 and 2 and place the AD FS and web application proxy servers on the appropriate subnets.</span></span>
    
<span data-ttu-id="3babf-187">Per creare un ambiente di sviluppo e di testing o modello di verifica di questa configurazione, vedere [Identità federata per l'ambiente di sviluppo/test di Office 365](federated-identity-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="3babf-187">To build a dev/test environment or a proof-of-concept of this configuration, see [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md).</span></span>
  
## <a name="next-step"></a><span data-ttu-id="3babf-188">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="3babf-188">Next step</span></span>

<span data-ttu-id="3babf-189">Iniziare la configurazione di questo carico di lavoro con [Fase 1 dell'autenticazione federata a disponibilità elevata: Configurare Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="3babf-189">Start the configuration of this workload with [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span> 
  
> [!TIP]
> <span data-ttu-id="3babf-190">Affinché un set di file distribuisca più velocemente l'autenticazione federata a elevata disponibilità per Office 365 in Azure, vedere [Autenticazione federata per Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="3babf-190">For a set of files to more quickly deploy your high availability federated authentication for Office 365 in Azure, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="3babf-191">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3babf-191">See Also</span></span>

[<span data-ttu-id="3babf-192">Identità federata per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="3babf-192">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="3babf-193">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="3babf-193">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="3babf-194">Identità federata per Office 365</span><span class="sxs-lookup"><span data-stu-id="3babf-194">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


