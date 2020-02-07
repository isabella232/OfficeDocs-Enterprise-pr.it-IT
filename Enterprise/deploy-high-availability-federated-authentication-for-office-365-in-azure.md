---
title: Distribuire l'autenticazione federata ad alta visibilità per Office 365 in Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: "Riepilogo: Configurare l'autenticazione federata a disponibilità elevata per l'abbonamento a Office 365 in Microsoft Azure."
ms.openlocfilehash: af73f75b7ac1e3151ddb5c55acdf49a48f784e95
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840523"
---
# <a name="deploy-high-availability-federated-authentication-for-office-365-in-azure"></a><span data-ttu-id="44661-103">Distribuire l'autenticazione federata a disponibilità elevata per Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="44661-103">Deploy high availability federated authentication for Office 365 in Azure</span></span>

<span data-ttu-id="44661-104">In questo articolo sono riportati i collegamenti a istruzioni dettagliate per la distribuzione dell'autenticazione federata a disponibilità elevata per Microsoft Office 365 in servizi infrastruttura di Azure con queste macchine virtuali:</span><span class="sxs-lookup"><span data-stu-id="44661-104">This article has links to the step-by-step instructions for deploying high availability federated authentication for Microsoft Office 365 in Azure infrastructure services with these virtual machines:</span></span>
  
- <span data-ttu-id="44661-105">Due server proxy di applicazione Web</span><span class="sxs-lookup"><span data-stu-id="44661-105">Two web application proxy servers</span></span>
    
- <span data-ttu-id="44661-106">Due server Active Directory Federation Services (AD FS)</span><span class="sxs-lookup"><span data-stu-id="44661-106">Two Active Directory Federation Services (AD FS) servers</span></span>
    
- <span data-ttu-id="44661-107">Due controller di dominio di replica</span><span class="sxs-lookup"><span data-stu-id="44661-107">Two replica domain controllers</span></span>
    
- <span data-ttu-id="44661-108">Un server di sincronizzazione della directory che esegue Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="44661-108">One directory synchronization server running Azure AD Connect</span></span>
    
<span data-ttu-id="44661-109">Di seguito viene riportata la configurazione, con i nomi segnaposto per ogni server.</span><span class="sxs-lookup"><span data-stu-id="44661-109">Here is the configuration, with placeholder names for each server.</span></span>
  
<span data-ttu-id="44661-110">**Un'autenticazione federata a disponibilità elevata per l'infrastruttura di Office 365 in Azure**</span><span class="sxs-lookup"><span data-stu-id="44661-110">**A high availability federated authentication for Office 365 infrastructure in Azure**</span></span>

![La configurazione finale dell'infrastruttura di autenticazione federata di Office 365 con disponibilità elevata](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="44661-112">Tutte le macchine virtuali si trovano in una singola rete virtuale di Azure (VNet) cross-premise.</span><span class="sxs-lookup"><span data-stu-id="44661-112">All of the virtual machines are in a single cross-premises Azure virtual network (VNet).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="44661-p101">L'autenticazione federata di singoli utenti non fa affidamento ad alcuna risorsa locale. Tuttavia, se la connessione cross-premise non è più disponibile, i controller di dominio della VNet non riceveranno aggiornamenti sugli account utente e sui gruppi creati nell'ambiente Active Directory Domain Services (AD DS). Affinché ciò non si verifichi, è possibile configurare la disponibilità elevata per la connessione cross-premise. Per maggiori informazioni, vedere [Connettività cross-premise e da rete virtuale a rete virtuale a disponibilità elevata](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="44661-p101">Federated authentication of individual users does not rely on any on-premises resources. However, if the cross-premises connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Active Directory Domain Services (AD DS). To ensure this does not happen, you can configure high availability for your cross-premises connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="44661-117">Ogni coppia di macchine virtuali per un ruolo specifico si trova nella propria subnet e nel set di disponibilità.</span><span class="sxs-lookup"><span data-stu-id="44661-117">Each pair of virtual machines for a specific role is in its own subnet and availability set.</span></span>
  
> [!NOTE]
> <span data-ttu-id="44661-p102">Poiché tale VNet è connessa alla rete locale, questa configurazione non include jumpbox o macchine virtuali di monitoraggio in una subnet di gestione. Per ulteriori informazioni, vedere [Esecuzione di macchine virtuali Windows per un'architettura a N livelli](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span><span class="sxs-lookup"><span data-stu-id="44661-p102">Because this VNet is connected to the on-premises network, this configuration does not include jumpbox or monitoring virtual machines on a management subnet. For more information, see [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span></span> 
  
<span data-ttu-id="44661-120">A seguito di questa configurazione, tutti gli utenti di Office 365 avranno a disposizione l'autenticazione federata e potranno accedere usando le credenziali di Active Directory Domain Services anziché l'account di Office 365.</span><span class="sxs-lookup"><span data-stu-id="44661-120">The result of this configuration is that you will have federated authentication for all of your Office 365 users, in which they can use their AD DS credentials to sign in rather than their Office 365 account.</span></span> <span data-ttu-id="44661-121">L'infrastruttura di autenticazione federata utilizza un set ridondante di server che vengono distribuiti nei servizi dell'infrastruttura di Azure invece che nella rete perimetrale locale.</span><span class="sxs-lookup"><span data-stu-id="44661-121">The federated authentication infrastructure uses a redundant set of servers that are more easily deployed in Azure infrastructure services, rather than in your on-premises edge network.</span></span>
  
## <a name="bill-of-materials"></a><span data-ttu-id="44661-122">Distinta base</span><span class="sxs-lookup"><span data-stu-id="44661-122">Bill of materials</span></span>

<span data-ttu-id="44661-123">Questa configurazione di base richiede l'insieme di componenti e servizi di Azure seguente:</span><span class="sxs-lookup"><span data-stu-id="44661-123">This baseline configuration requires the following set of Azure services and components:</span></span>
  
- <span data-ttu-id="44661-124">Sette macchine virtuali</span><span class="sxs-lookup"><span data-stu-id="44661-124">Seven virtual machines</span></span>
    
- <span data-ttu-id="44661-125">Una rete virtuale cross-premise con quattro subnet</span><span class="sxs-lookup"><span data-stu-id="44661-125">One cross-premises virtual network with four subnets</span></span>
    
- <span data-ttu-id="44661-126">Quattro gruppi di risorse</span><span class="sxs-lookup"><span data-stu-id="44661-126">Four resource groups</span></span>
    
- <span data-ttu-id="44661-127">Tre set di disponibilità</span><span class="sxs-lookup"><span data-stu-id="44661-127">Three availability sets</span></span>
    
- <span data-ttu-id="44661-128">Un abbonamento di Azure</span><span class="sxs-lookup"><span data-stu-id="44661-128">One Azure subscription</span></span>
    
<span data-ttu-id="44661-129">Di seguito sono riportate le macchine virtuali e le rispettive dimensioni predefinite per questa configurazione.</span><span class="sxs-lookup"><span data-stu-id="44661-129">Here are the virtual machines and their default sizes for this configuration.</span></span>
  
|<span data-ttu-id="44661-130">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="44661-130">**Item**</span></span>|<span data-ttu-id="44661-131">**Descrizione macchina virtuale**</span><span class="sxs-lookup"><span data-stu-id="44661-131">**Virtual machine description**</span></span>|<span data-ttu-id="44661-132">**Immagine della raccolta Azure**</span><span class="sxs-lookup"><span data-stu-id="44661-132">**Azure gallery image**</span></span>|<span data-ttu-id="44661-133">**Dimensione predefinita**</span><span class="sxs-lookup"><span data-stu-id="44661-133">**Default size**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="44661-134">1.</span><span class="sxs-lookup"><span data-stu-id="44661-134">1.</span></span>  <br/> |<span data-ttu-id="44661-135">Primo controller di dominio</span><span class="sxs-lookup"><span data-stu-id="44661-135">First domain controller</span></span>  <br/> |<span data-ttu-id="44661-136">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="44661-136">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="44661-137">D2</span><span class="sxs-lookup"><span data-stu-id="44661-137">D2</span></span>  <br/> |
|<span data-ttu-id="44661-138">2.</span><span class="sxs-lookup"><span data-stu-id="44661-138">2.</span></span>  <br/> |<span data-ttu-id="44661-139">Secondo controller di dominio</span><span class="sxs-lookup"><span data-stu-id="44661-139">Second domain controller</span></span>  <br/> |<span data-ttu-id="44661-140">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="44661-140">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="44661-141">D2</span><span class="sxs-lookup"><span data-stu-id="44661-141">D2</span></span>  <br/> |
|<span data-ttu-id="44661-142">3.</span><span class="sxs-lookup"><span data-stu-id="44661-142">3.</span></span>  <br/> |<span data-ttu-id="44661-143">Server di Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="44661-143">Azure AD Connect server</span></span>  <br/> |<span data-ttu-id="44661-144">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="44661-144">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="44661-145">D2</span><span class="sxs-lookup"><span data-stu-id="44661-145">D2</span></span>  <br/> |
|<span data-ttu-id="44661-146">4.</span><span class="sxs-lookup"><span data-stu-id="44661-146">4.</span></span>  <br/> |<span data-ttu-id="44661-147">primo server AD FS</span><span class="sxs-lookup"><span data-stu-id="44661-147">First AD FS server</span></span>  <br/> |<span data-ttu-id="44661-148">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="44661-148">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="44661-149">D2</span><span class="sxs-lookup"><span data-stu-id="44661-149">D2</span></span>  <br/> |
|<span data-ttu-id="44661-150">5.</span><span class="sxs-lookup"><span data-stu-id="44661-150">5.</span></span>  <br/> |<span data-ttu-id="44661-151">Secondo server AD FS</span><span class="sxs-lookup"><span data-stu-id="44661-151">Second AD FS server</span></span>  <br/> |<span data-ttu-id="44661-152">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="44661-152">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="44661-153">D2</span><span class="sxs-lookup"><span data-stu-id="44661-153">D2</span></span>  <br/> |
|<span data-ttu-id="44661-154">6.</span><span class="sxs-lookup"><span data-stu-id="44661-154">6.</span></span>  <br/> |<span data-ttu-id="44661-155">Primo server proxy di applicazione Web</span><span class="sxs-lookup"><span data-stu-id="44661-155">First web application proxy server</span></span>  <br/> |<span data-ttu-id="44661-156">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="44661-156">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="44661-157">D2</span><span class="sxs-lookup"><span data-stu-id="44661-157">D2</span></span>  <br/> |
|<span data-ttu-id="44661-158">7.</span><span class="sxs-lookup"><span data-stu-id="44661-158">7.</span></span>  <br/> |<span data-ttu-id="44661-159">Secondo server proxy di applicazione Web</span><span class="sxs-lookup"><span data-stu-id="44661-159">Second web application proxy server</span></span>  <br/> |<span data-ttu-id="44661-160">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="44661-160">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="44661-161">D2</span><span class="sxs-lookup"><span data-stu-id="44661-161">D2</span></span>  <br/> |
   
<span data-ttu-id="44661-162">Per fare una stima dei costi per questa configurazione, vedere il [calcolatore dei prezzi Azure](https://azure.microsoft.com/pricing/calculator/)</span><span class="sxs-lookup"><span data-stu-id="44661-162">To compute the estimated costs for this configuration, see the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/)</span></span>
  
## <a name="phases-of-deployment"></a><span data-ttu-id="44661-163">Fasi di distribuzione</span><span class="sxs-lookup"><span data-stu-id="44661-163">Phases of deployment</span></span>

<span data-ttu-id="44661-164">Distribuire il carico di lavoro nelle fasi seguenti:</span><span class="sxs-lookup"><span data-stu-id="44661-164">You deploy this workload in the following phases:</span></span>
  
- <span data-ttu-id="44661-p104">[Fase 1: configurare Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Creare gruppi di risorse, account di archiviazione, set di disponibilità e una rete virtuale cross-premise.</span><span class="sxs-lookup"><span data-stu-id="44661-p104">[Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="44661-167">[Fase 2: configurare i controller di dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="44661-167">[Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md).</span></span> <span data-ttu-id="44661-168">Creare e configurare i controller di dominio di Active Directory Domain Services di replica e il server di sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="44661-168">Create and configure replica AD DS domain controllers and the directory synchronization server.</span></span>
    
- <span data-ttu-id="44661-p106">[Fase 3: configurare i server AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Creare e configurare i due server AD FS.</span><span class="sxs-lookup"><span data-stu-id="44661-p106">[Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="44661-p107">[Fase 4: configurare i proxy dell'applicazione Web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Creare e configurare i due server proxy dell'applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="44661-p107">[Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="44661-p108">[Fase 5: configurare l'autenticazione federata per Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configurare l'autenticazione federata per l'abbonamento di Office 365.</span><span class="sxs-lookup"><span data-stu-id="44661-p108">[Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configure federated authentication for your Office 365 subscription.</span></span>
    
<span data-ttu-id="44661-p109">Questi articoli forniscono una guida dettagliata per un'architettura predefinita al fine di creare un'autenticazione federata a elevata funzionale per Office 365 nei servizi infrastruttura di Azure. Tenere presente quanto segue:</span><span class="sxs-lookup"><span data-stu-id="44661-p109">These articles provide a prescriptive, phase-by-phase guide for a predefined architecture to create a functional, high availability federated authentication for Office 365 in Azure infrastructure services. Keep the following in mind:</span></span>
  
- <span data-ttu-id="44661-177">Se si è un responsabile dell'implementazione AD FS esperto, adattare le istruzione fornite nelle fasi 3 e 4 e compilare il set di server più opportuno per le proprie esigenze.</span><span class="sxs-lookup"><span data-stu-id="44661-177">If you are an experienced AD FS implementer, feel free to adapt the instructions in phases 3 and 4 and build the set of servers that best suits your needs.</span></span>
    
- <span data-ttu-id="44661-178">Se si dispone già di una distribuzione cloud ibrida Azure con una rete virtuale cross-premise esistente, è possibile adattare o ignorare le istruzioni riportate nelle fasi 1 e 2 e posizionare i server proxy dell'applicazione Web e AD FS sulle subnet appropriate.</span><span class="sxs-lookup"><span data-stu-id="44661-178">If you already have an existing Azure hybrid cloud deployment with an existing cross-premises virtual network, feel free to adapt or skip the instructions in phases 1 and 2 and place the AD FS and web application proxy servers on the appropriate subnets.</span></span>
    
<span data-ttu-id="44661-179">Per creare un ambiente di sviluppo e di testing o modello di verifica di questa configurazione, vedere [Identità federata per l'ambiente di sviluppo/test di Office 365](federated-identity-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="44661-179">To build a dev/test environment or a proof-of-concept of this configuration, see [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md).</span></span>
  
## <a name="next-step"></a><span data-ttu-id="44661-180">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="44661-180">Next step</span></span>

<span data-ttu-id="44661-181">Iniziare la configurazione di questo carico di lavoro con la [Fase 1: configurare Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="44661-181">Start the configuration of this workload with [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span> 
  
