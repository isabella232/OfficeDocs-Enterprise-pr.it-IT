---
title: Diagramma accessibile-opzioni della piattaforma Microsoft Lync 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: Questo articolo è una versione di testo accessibile del diagramma denominato opzioni della piattaforma Microsoft Lync 2013, disponibile nei diagrammi tecnici.
ms.openlocfilehash: 4a660df4bfacad2a00f5d9fbb5e1b668840e3b9f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487796"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a><span data-ttu-id="7107b-103">Diagramma accessibile-opzioni della piattaforma Microsoft Lync 2013</span><span class="sxs-lookup"><span data-stu-id="7107b-103">Accessible diagram - Microsoft Lync 2013 Platform Options</span></span>

<span data-ttu-id="7107b-104">**Riepilogo:** Questo articolo è una versione di testo accessibile del diagramma denominato opzioni della piattaforma Microsoft Lync 2013, disponibile nei [diagramMi tecnici](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="7107b-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Lync 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="7107b-105">In questo poster vengono descritti i responsabili decisionali aziendali (BDMs) e gli architetti che devono essere a conoscenza delle distribuzioni di Lync Online (Office 365) e di Lync Server e include:</span><span class="sxs-lookup"><span data-stu-id="7107b-105">This poster describes what business decision makers (BDMs) and architects need to know about Lync Online (Office 365) and Lync Server deployments and includes:</span></span>
  
- <span data-ttu-id="7107b-106">Confronto tra quattro opzioni di distribuzione diverse: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server e Lync Server ospitato dal provider.</span><span class="sxs-lookup"><span data-stu-id="7107b-106">A comparison of four different deployment options: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server, and Provider-Hosted Lync Server.</span></span> 
    
- <span data-ttu-id="7107b-107">Due scenari di esempio per la distribuzione di Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="7107b-107">Two example scenarios for deploying Lync 2013.</span></span>
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a><span data-ttu-id="7107b-108">Confronto tra quattro distribuzioni diverse per la piattaforma Lync 2013</span><span class="sxs-lookup"><span data-stu-id="7107b-108">Comparison of four different deployments for the Lync 2013 platform</span></span>

<span data-ttu-id="7107b-109">Il confronto fornisce informazioni su ogni opzione di distribuzione nelle aree seguenti:</span><span class="sxs-lookup"><span data-stu-id="7107b-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="7107b-110">Panoramica delle diverse funzionalità di distribuzione</span><span class="sxs-lookup"><span data-stu-id="7107b-110">An overview of the different deployment features</span></span>
    
- <span data-ttu-id="7107b-111">Vantaggi dell'implementazione di ogni opzione di distribuzione</span><span class="sxs-lookup"><span data-stu-id="7107b-111">Benefits of implementing each deployment option</span></span>
    
- <span data-ttu-id="7107b-112">Requisiti relativi alle licenze</span><span class="sxs-lookup"><span data-stu-id="7107b-112">Licensing requirements</span></span>
    
- <span data-ttu-id="7107b-113">Attività di architettura necessarie</span><span class="sxs-lookup"><span data-stu-id="7107b-113">Required architectural tasks</span></span>
    
- <span data-ttu-id="7107b-114">Responsabilità per i professionisti IT per l'implementazione di ogni opzione di distribuzione</span><span class="sxs-lookup"><span data-stu-id="7107b-114">IT Pro responsibilities for implementing each deployment option</span></span>
    
### <a name="overview"></a><span data-ttu-id="7107b-115">Panoramica</span><span class="sxs-lookup"><span data-stu-id="7107b-115">Overview</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="7107b-116">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="7107b-116">Lync Online (Office 365)</span></span>

<span data-ttu-id="7107b-117">È possibile ottenere efficienza e ottimizzare i costi con i piani multitenant di Office 365.</span><span class="sxs-lookup"><span data-stu-id="7107b-117">You gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span>
  
<span data-ttu-id="7107b-118">Nel diagramma di accompagnamento viene mostrato Lync Online con un tenant di Azure Active Directory, che sincronizza i nomi degli account e le password tra l'ambiente Servizi di dominio Active Directory locale e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7107b-118">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="7107b-119">Descrizione delle funzionalità e delle funzionalità:</span><span class="sxs-lookup"><span data-stu-id="7107b-119">Description of features and functionality:</span></span>
  
- <span data-ttu-id="7107b-120">Software come servizio (SaaS).</span><span class="sxs-lookup"><span data-stu-id="7107b-120">Software as a Service (SaaS).</span></span>
    
- <span data-ttu-id="7107b-121">Set di funzionalità RTF sempre aggiornato.</span><span class="sxs-lookup"><span data-stu-id="7107b-121">Rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="7107b-122">Include un tenant di Azure Active Directory per gli account online, che può essere utilizzato con altre applicazioni.</span><span class="sxs-lookup"><span data-stu-id="7107b-122">Includes an Azure Active Directory tenant for online accounts, which can be used with other applications.</span></span> 
    
- <span data-ttu-id="7107b-123">L'integrazione della directory include la sincronizzazione dei nomi degli account e delle password tra l'ambiente Servizi di dominio Active Directory locale e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7107b-123">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
    
- <span data-ttu-id="7107b-124">Se il servizio Single Sign-on (SSO) è un requisito, è necessario implementare Active Directory Federation Services (AD FS).</span><span class="sxs-lookup"><span data-stu-id="7107b-124">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) must be implemented.</span></span> 
    
- <span data-ttu-id="7107b-125">La comunicazione client su Internet è crittografata e autenticata.</span><span class="sxs-lookup"><span data-stu-id="7107b-125">Client communication over the Internet is encrypted and authenticated.</span></span>
    
- <span data-ttu-id="7107b-126">Apparecchiature telefoniche legacy, rete PSTN (Public Switched Telephone Network), la connettività è disponibile tramite provider di terze parti.</span><span class="sxs-lookup"><span data-stu-id="7107b-126">Legacy phone equipment, public switched telephone network (PSTN), connectivity is available through third-party providers.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="7107b-127">Lync Online/server ibrido (dominio diviso)</span><span class="sxs-lookup"><span data-stu-id="7107b-127">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="7107b-128">È possibile combinare i vantaggi di Office 365 con una distribuzione locale di Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="7107b-128">You can combine the benefits of Office 365 with an on-premises deployment of Lync 2013.</span></span>
  
<span data-ttu-id="7107b-129">Nel diagramma di accompagnamento viene mostrato Office 365 con Lync online in cui alcuni utenti sono ospitati in locale e alcuni utenti sono alloggiati online.</span><span class="sxs-lookup"><span data-stu-id="7107b-129">The accompanying diagram shows Office 365 with Lync Online where some users are homed on-premises and some users are homed online.</span></span> <span data-ttu-id="7107b-130">Viene inoltre visualizzato un server perimetrale distribuito in locale.</span><span class="sxs-lookup"><span data-stu-id="7107b-130">An Edge Server that is deployed on-premises is also shown.</span></span>
  
<span data-ttu-id="7107b-131">Descrizione delle funzionalità e delle funzionalità:</span><span class="sxs-lookup"><span data-stu-id="7107b-131">Description of features and functionality:</span></span>
  
- <span data-ttu-id="7107b-132">Alcuni utenti sono ospitati in locale e alcuni utenti sono ospitati online, ma gli utenti condividono lo stesso dominio SIP, ad esempio contoso.com.</span><span class="sxs-lookup"><span data-stu-id="7107b-132">Some users are homed on premises and some users are homed online, but the users share the same SIP domain (such as contoso.com).</span></span>
    
- <span data-ttu-id="7107b-133">Sfruttare l'infrastruttura di Lync Server 2013 esistente, incluse le connessioni alla rete PSTN.</span><span class="sxs-lookup"><span data-stu-id="7107b-133">Leverage your existing Lync Server 2013 infrastructure, including the connections to the PSTN.</span></span>
    
- <span data-ttu-id="7107b-134">Aggiungere facilmente nuovi utenti di Lync Online quando non richiedono PSTN.</span><span class="sxs-lookup"><span data-stu-id="7107b-134">Add new Lync Online users easily when they do not require PSTN.</span></span>
    
- <span data-ttu-id="7107b-135">Eseguire la migrazione da Lync locale a Lync Online nel tempo, nella pianificazione.</span><span class="sxs-lookup"><span data-stu-id="7107b-135">Migrate from Lync on-premises to Lync Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="7107b-136">Integrazione con altre applicazioni di Office 365, tra cui Exchange Online e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7107b-136">Integrate with other Office 365 applications, including Exchange Online and SharePoint Online.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="7107b-137">Lync Server</span><span class="sxs-lookup"><span data-stu-id="7107b-137">Lync Server</span></span>

<span data-ttu-id="7107b-138">In questa distribuzione, si è proprietari di tutto.</span><span class="sxs-lookup"><span data-stu-id="7107b-138">In this deployment, you own everything.</span></span> <span data-ttu-id="7107b-139">Il diagramma di accompagnamento Visualizza un'infrastruttura di Lync Server con un ambiente Servizi di dominio Active Directory (AD DS) locale in cui gli utenti sono ospitati in locale.</span><span class="sxs-lookup"><span data-stu-id="7107b-139">The accompanying diagram shows a Lync Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="7107b-140">Descrizione delle funzionalità e delle funzionalità:</span><span class="sxs-lookup"><span data-stu-id="7107b-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="7107b-141">Pianificazione della capacità e dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="7107b-141">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="7107b-142">Acquisizione e installazione del server.</span><span class="sxs-lookup"><span data-stu-id="7107b-142">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="7107b-143">Distribuzione.</span><span class="sxs-lookup"><span data-stu-id="7107b-143">Deployment.</span></span>
    
- <span data-ttu-id="7107b-144">Scalabilità orizzontale, applicazione di patch e operazioni.</span><span class="sxs-lookup"><span data-stu-id="7107b-144">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="7107b-145">Backup dei dati.</span><span class="sxs-lookup"><span data-stu-id="7107b-145">Backing up data.</span></span>
    
- <span data-ttu-id="7107b-146">Gestione del failover e del ripristino di emergenza.</span><span class="sxs-lookup"><span data-stu-id="7107b-146">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="7107b-147">Connessione dell'infrastruttura Lync Server 2013 alla rete PSTN.</span><span class="sxs-lookup"><span data-stu-id="7107b-147">Connecting your Lync Server 2013 infrastructure to the PSTN.</span></span>
    
- <span data-ttu-id="7107b-148">Integrazione con le apparecchiature telefoniche esistenti, ad esempio i sistemi PBX (Private Branch Exchange).</span><span class="sxs-lookup"><span data-stu-id="7107b-148">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="7107b-149">Lync Server ospitato dal provider</span><span class="sxs-lookup"><span data-stu-id="7107b-149">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="7107b-150">In questa distribuzione il provider possiede tutto.</span><span class="sxs-lookup"><span data-stu-id="7107b-150">In this deployment, your provider owns everything.</span></span> <span data-ttu-id="7107b-151">Il diagramma di accompagnamento Visualizza la rete di un provider, inclusi i server e le apparecchiature con una connessione a un ambiente locale.</span><span class="sxs-lookup"><span data-stu-id="7107b-151">The accompanying diagram shows a provider's network including their servers and equipment with a connection to an on-premises environment.</span></span>
  
<span data-ttu-id="7107b-152">Descrizione delle funzionalità e delle funzionalità:</span><span class="sxs-lookup"><span data-stu-id="7107b-152">Description of features and functionality:</span></span>
  
- <span data-ttu-id="7107b-153">Pianificazione della capacità e dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="7107b-153">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="7107b-154">Acquisizione e installazione del server.</span><span class="sxs-lookup"><span data-stu-id="7107b-154">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="7107b-155">Distribuzione.</span><span class="sxs-lookup"><span data-stu-id="7107b-155">Deployment.</span></span>
    
- <span data-ttu-id="7107b-156">Scalabilità orizzontale, applicazione di patch e operazioni.</span><span class="sxs-lookup"><span data-stu-id="7107b-156">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="7107b-157">Backup dei dati.</span><span class="sxs-lookup"><span data-stu-id="7107b-157">Backing up data.</span></span>
    
- <span data-ttu-id="7107b-158">Gestione del failover e del ripristino di emergenza.</span><span class="sxs-lookup"><span data-stu-id="7107b-158">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="7107b-159">Integrazione con le apparecchiature telefoniche esistenti, ad esempio i sistemi PBX (Private Branch Exchange).</span><span class="sxs-lookup"><span data-stu-id="7107b-159">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
- <span data-ttu-id="7107b-160">Inoltre, il provider può:</span><span class="sxs-lookup"><span data-stu-id="7107b-160">In addition, the provider can:</span></span>
    
  - <span data-ttu-id="7107b-161">Installare i propri server e le proprie apparecchiature nella propria rete con una connessione alla propria sede (linea continua).</span><span class="sxs-lookup"><span data-stu-id="7107b-161">Install their servers and equipment in their own network with a connection to your premises (solid line).</span></span>
    
  - <span data-ttu-id="7107b-162">Installare i propri server nella propria sede (linea tratteggiata).</span><span class="sxs-lookup"><span data-stu-id="7107b-162">Install their servers on your premises (dotted line).</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="7107b-163">Vantaggi dell'implementazione di ogni opzione di distribuzione</span><span class="sxs-lookup"><span data-stu-id="7107b-163">Benefits of implementing each deployment option</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="7107b-164">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="7107b-164">Lync Online (Office 365)</span></span>

- <span data-ttu-id="7107b-165">Nessun onere operativo dei server locali o del software del server.</span><span class="sxs-lookup"><span data-stu-id="7107b-165">No operational burden of on-premises servers or server software.</span></span>
    
- <span data-ttu-id="7107b-166">Funzionalità di comunicazione di Lync Server 2013 come servizio basato su cloud.</span><span class="sxs-lookup"><span data-stu-id="7107b-166">Communication capabilities of Lync Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="7107b-167">Presenza di Lync, messaggistica istantanea, chiamata audio e video, riunioni online ricche e funzionalità di Web Conferencing estese.</span><span class="sxs-lookup"><span data-stu-id="7107b-167">Lync presence, instant messaging, audio and video calling, rich online meetings, and extensive web conferencing capabilities.</span></span>
    
- <span data-ttu-id="7107b-168">Utilizzato con organizzazioni geograficamente disperse o con dipendenti principalmente mobili.</span><span class="sxs-lookup"><span data-stu-id="7107b-168">Used with geographically-dispersed organizations or with primarily mobile employees.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="7107b-169">Lync Online/server ibrido (dominio diviso)</span><span class="sxs-lookup"><span data-stu-id="7107b-169">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="7107b-170">Utilizzare Lync Online per gli utenti remoti e l'integrazione con i partner commerciali.</span><span class="sxs-lookup"><span data-stu-id="7107b-170">Use Lync Online for remote users and integration with business partners.</span></span>
    
- <span data-ttu-id="7107b-171">Semplificare la migrazione da Lync locale a Lync Online.</span><span class="sxs-lookup"><span data-stu-id="7107b-171">Facilitate a migration from Lync on-premises to Lync Online.</span></span>
    
- <span data-ttu-id="7107b-172">Supporto di siti remoti senza l'utilizzo di un dispositivo di succursale.</span><span class="sxs-lookup"><span data-stu-id="7107b-172">Support remote sites without using a branch office appliance.</span></span>
    
- <span data-ttu-id="7107b-173">Semplificazione dell'aggiunta del supporto di Lync per nuove acquisizioni aziendali.</span><span class="sxs-lookup"><span data-stu-id="7107b-173">Ease of adding Lync support for new business acquisitions.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="7107b-174">Lync Server</span><span class="sxs-lookup"><span data-stu-id="7107b-174">Lync Server</span></span>

- <span data-ttu-id="7107b-175">Soluzioni cloud private.</span><span class="sxs-lookup"><span data-stu-id="7107b-175">Private cloud solutions.</span></span>
    
- <span data-ttu-id="7107b-176">Soluzioni altamente personalizzate.</span><span class="sxs-lookup"><span data-stu-id="7107b-176">Highly customized solutions.</span></span>
    
- <span data-ttu-id="7107b-177">Soluzioni legacy con componenti di terze parti che dipendono da hardware e software che non sono supportati da Lync Online.</span><span class="sxs-lookup"><span data-stu-id="7107b-177">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="7107b-178">Restrizioni sulla privacy che impediscono la sincronizzazione degli account di servizi di dominio Active Directory con Office 365.</span><span class="sxs-lookup"><span data-stu-id="7107b-178">Privacy restrictions that prevent synchronization of AD DS accounts with Office 365.</span></span>
    
- <span data-ttu-id="7107b-179">Organizzazioni che desiderano controllare l'intera piattaforma e la soluzione.</span><span class="sxs-lookup"><span data-stu-id="7107b-179">Organizations that desire control of the entire platform and solution.</span></span>
    
- <span data-ttu-id="7107b-180">Sostituzione del PBX con Lync Enterprise Voice.</span><span class="sxs-lookup"><span data-stu-id="7107b-180">PBX replacement with Lync Enterprise Voice.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="7107b-181">Lync Server ospitato dal provider</span><span class="sxs-lookup"><span data-stu-id="7107b-181">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="7107b-182">Organizzazioni che desiderano funzionalità di Lync Server, ma che desiderano esternalizzare la distribuzione e la manutenzione.</span><span class="sxs-lookup"><span data-stu-id="7107b-182">Organizations that want Lync Server functionality but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="7107b-183">Soluzioni basate sul provider.</span><span class="sxs-lookup"><span data-stu-id="7107b-183">Provider-based solutions.</span></span>
    
- <span data-ttu-id="7107b-184">Soluzioni altamente personalizzate.</span><span class="sxs-lookup"><span data-stu-id="7107b-184">Highly customized solutions.</span></span>
    
- <span data-ttu-id="7107b-185">Soluzioni legacy con componenti di terze parti che dipendono da hardware e software che non sono supportati da Lync Online.</span><span class="sxs-lookup"><span data-stu-id="7107b-185">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="7107b-186">Sostituzione del PBX con Lync Enterprise Voice.</span><span class="sxs-lookup"><span data-stu-id="7107b-186">PBX replacement with Lync Enterprise Voice.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="7107b-187">Requisiti di licenza</span><span class="sxs-lookup"><span data-stu-id="7107b-187">License requirements</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="7107b-188">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="7107b-188">Lync Online (Office 365)</span></span>

<span data-ttu-id="7107b-189">Modello di sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="7107b-189">Subscription model.</span></span>
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="7107b-190">Lync Online/server ibrido (dominio diviso)</span><span class="sxs-lookup"><span data-stu-id="7107b-190">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="7107b-191">Office 365: modello di sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="7107b-191">Office 365 — Subscription model.</span></span> <span data-ttu-id="7107b-192">Non sono necessarie licenze aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="7107b-192">No additional licenses needed.</span></span> 
    
- <span data-ttu-id="7107b-193">Locale: vengono applicate tutte le licenze locali.</span><span class="sxs-lookup"><span data-stu-id="7107b-193">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="lync-server"></a><span data-ttu-id="7107b-194">Lync Server</span><span class="sxs-lookup"><span data-stu-id="7107b-194">Lync Server</span></span>

- <span data-ttu-id="7107b-195">Sistema operativo del server</span><span class="sxs-lookup"><span data-stu-id="7107b-195">Server Operating System</span></span>
    
- <span data-ttu-id="7107b-196">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7107b-196">SQL Server</span></span>
    
- <span data-ttu-id="7107b-197">Licenza del server Lync 2013</span><span class="sxs-lookup"><span data-stu-id="7107b-197">Lync 2013 Server License</span></span>
    
- <span data-ttu-id="7107b-198">Licenza di accesso client Lync 2013</span><span class="sxs-lookup"><span data-stu-id="7107b-198">Lync 2013 Client Access License</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="7107b-199">Lync Server ospitato dal provider</span><span class="sxs-lookup"><span data-stu-id="7107b-199">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="7107b-200">I costi sono basati sull'accordo con il provider di soluzioni Lync.</span><span class="sxs-lookup"><span data-stu-id="7107b-200">Costs are based on the agreement with your Lync solution provider.</span></span>
  
### <a name="architecture-tasks"></a><span data-ttu-id="7107b-201">Attività dell'architettura</span><span class="sxs-lookup"><span data-stu-id="7107b-201">Architecture tasks</span></span>

<span data-ttu-id="7107b-202">In questa sezione sono elencate le attività di architettura per ogni opzione di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="7107b-202">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="7107b-203">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="7107b-203">Lync Online (Office 365)</span></span>

- <span data-ttu-id="7107b-204">Pianificare e progettare la sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="7107b-204">Plan and design directory synchronization.</span></span>
    
- <span data-ttu-id="7107b-205">Garantire la disponibilità e la capacità della rete attraverso i firewall, i server proxy, i gateway e i collegamenti WAN.</span><span class="sxs-lookup"><span data-stu-id="7107b-205">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
- <span data-ttu-id="7107b-206">Acquisizione dei certificati SSL di terze parti per fornire la sicurezza aziendale per le offerte di servizi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="7107b-206">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span>
    
- <span data-ttu-id="7107b-207">Decidere se si desidera connettersi a Office 365 con Internet Protocol versione 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="7107b-207">Decide if you want to connect to Office 365 with Internet Protocol version 6 (IPv6).</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="7107b-208">Lync Online/server ibrido (dominio diviso)</span><span class="sxs-lookup"><span data-stu-id="7107b-208">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="7107b-209">Oltre alle attività sia per gli ambienti Office 365 che per quelli locali:</span><span class="sxs-lookup"><span data-stu-id="7107b-209">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="7107b-210">Determinare la quantità di integrazione delle funzionalità che si desidera utilizzare con le versioni locali e online di Exchange Server e SharePoint.</span><span class="sxs-lookup"><span data-stu-id="7107b-210">Determine how much feature integration you want to use with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
- <span data-ttu-id="7107b-211">Se necessario, determinare quale dispositivo server proxy verrà utilizzato per le richieste provenienti da Office 365.</span><span class="sxs-lookup"><span data-stu-id="7107b-211">If required, determine which proxy server device will be used for requests from Office 365.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="7107b-212">Lync Server</span><span class="sxs-lookup"><span data-stu-id="7107b-212">Lync Server</span></span>

<span data-ttu-id="7107b-213">Progettare l'ambiente Lync in un ambiente locale esistente:</span><span class="sxs-lookup"><span data-stu-id="7107b-213">Design the Lync environment in an existing on-premises environment:</span></span>
  
- <span data-ttu-id="7107b-214">Topologia di Lync per centrali e succursali.</span><span class="sxs-lookup"><span data-stu-id="7107b-214">Lync topology for central and branch offices.</span></span>
    
- <span data-ttu-id="7107b-215">Hardware del server, inclusa la virtualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7107b-215">Server hardware, including virtualization.</span></span>
    
- <span data-ttu-id="7107b-216">Integrazione con servizi di dominio Active Directory (AD DS) e DNS.</span><span class="sxs-lookup"><span data-stu-id="7107b-216">Integration with Active Directory Domain Services (AD DS) and DNS.</span></span>
    
- <span data-ttu-id="7107b-217">Bilanciamento del carico per i pool di Lync Server.</span><span class="sxs-lookup"><span data-stu-id="7107b-217">Load balancing for Lync server pools.</span></span>
    
- <span data-ttu-id="7107b-218">Failover e ripristino di emergenza.</span><span class="sxs-lookup"><span data-stu-id="7107b-218">Failover and disaster recovery.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="7107b-219">Lync Server ospitato dal provider</span><span class="sxs-lookup"><span data-stu-id="7107b-219">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="7107b-220">Per un'installazione basata sul cloud, determinare la connessione alla rete del provider di servizi.</span><span class="sxs-lookup"><span data-stu-id="7107b-220">For a cloud-based installation, determine the connection to the service provider's network.</span></span>
    
- <span data-ttu-id="7107b-221">Per un'installazione locale, determinare la posizione dei server Lync del provider sulla rete.</span><span class="sxs-lookup"><span data-stu-id="7107b-221">For an on-premises installation, determine the placement of the provider's Lync servers on your network.</span></span>
    
- <span data-ttu-id="7107b-222">Per entrambi i tipi, determinare l'integrazione con servizi di dominio Active Directory e le apparecchiature PBX.</span><span class="sxs-lookup"><span data-stu-id="7107b-222">For both types, determine the integration with AD DS and your PBX equipment.</span></span>
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="7107b-223">Responsabilità per i professionisti IT</span><span class="sxs-lookup"><span data-stu-id="7107b-223">IT Pro responsibilities</span></span>

<span data-ttu-id="7107b-224">In questa sezione sono elencate le responsabilità per i professionisti IT per ogni opzione di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="7107b-224">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="7107b-225">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="7107b-225">Lync Online (Office 365)</span></span>

<span data-ttu-id="7107b-226">Distribuire e gestire Lync Online (Office 365):</span><span class="sxs-lookup"><span data-stu-id="7107b-226">Deploy and manage Lync Online (Office 365):</span></span>
  
- <span data-ttu-id="7107b-227">Implementare il piano di sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="7107b-227">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="7107b-228">Pianificare e implementare i record DNS interni ed esterni e il routing.</span><span class="sxs-lookup"><span data-stu-id="7107b-228">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="7107b-229">Configurare il proxy o il firewall per i requisiti di indirizzo IP e URL di Office 365.</span><span class="sxs-lookup"><span data-stu-id="7107b-229">Configure your proxy or firewall for Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="7107b-230">Amministrare gli account utente e le impostazioni di Lync Online.</span><span class="sxs-lookup"><span data-stu-id="7107b-230">Administer user accounts and Lync Online settings.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="7107b-231">Lync Online/server ibrido (dominio diviso)</span><span class="sxs-lookup"><span data-stu-id="7107b-231">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="7107b-232">Oltre alle attività sia per gli ambienti Office 365 che per quelli locali:</span><span class="sxs-lookup"><span data-stu-id="7107b-232">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="7107b-233">Configurare il dispositivo server proxy, se necessario.</span><span class="sxs-lookup"><span data-stu-id="7107b-233">Configure the proxy server device, if required.</span></span>
    
- <span data-ttu-id="7107b-234">Configurare l'integrazione delle funzionalità con le versioni locali e online di Exchange Server e SharePoint.</span><span class="sxs-lookup"><span data-stu-id="7107b-234">Configure the integration of features with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="7107b-235">Lync Server</span><span class="sxs-lookup"><span data-stu-id="7107b-235">Lync Server</span></span>

<span data-ttu-id="7107b-236">Distribuire e gestire Lync Server in un ambiente locale:</span><span class="sxs-lookup"><span data-stu-id="7107b-236">Deploy and manage Lync Server in an on-premises environment:</span></span>
  
- <span data-ttu-id="7107b-237">Eseguire il proVisioning dei server.</span><span class="sxs-lookup"><span data-stu-id="7107b-237">Provision the servers.</span></span>
    
- <span data-ttu-id="7107b-238">Distribuire la topologia di Lync.</span><span class="sxs-lookup"><span data-stu-id="7107b-238">Deploy the Lync topology.</span></span>
    
- <span data-ttu-id="7107b-239">Aggiornare i server Lync.</span><span class="sxs-lookup"><span data-stu-id="7107b-239">Update Lync servers.</span></span>
    
- <span data-ttu-id="7107b-240">Aggiungere o rimuovere i server di topologia in base all'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="7107b-240">Add or remove topology servers as needed based on utilization.</span></span>
    
- <span data-ttu-id="7107b-241">Implementare l'ambiente di failover e ripristino di emergenza.</span><span class="sxs-lookup"><span data-stu-id="7107b-241">Implement the failover and disaster recovery environment.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="7107b-242">Lync Server ospitato dal provider</span><span class="sxs-lookup"><span data-stu-id="7107b-242">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="7107b-243">Collaborare con il provider per:</span><span class="sxs-lookup"><span data-stu-id="7107b-243">Work with the provider to:</span></span>
  
- <span data-ttu-id="7107b-244">Integrazione di Lync Server nella rete.</span><span class="sxs-lookup"><span data-stu-id="7107b-244">Integrate Lync Server into your network.</span></span>
    
- <span data-ttu-id="7107b-245">Integrazione di Lync Server con altri prodotti Microsoft o soluzioni personalizzate.</span><span class="sxs-lookup"><span data-stu-id="7107b-245">Integrate Lync Server with other Microsoft products or custom solutions.</span></span>
    
- <span data-ttu-id="7107b-246">Monitorare l'aderenza con il contratto di servizio provider (SLA, Service Level Agreement).</span><span class="sxs-lookup"><span data-stu-id="7107b-246">Monitor adherence with provider service level agreement (SLA).</span></span>
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a><span data-ttu-id="7107b-247">Due scenari di esempio per la distribuzione di Lync 2013</span><span class="sxs-lookup"><span data-stu-id="7107b-247">Two example scenarios for deploying Lync 2013</span></span>

### <a name="directory-synchronization-components-in-microsoft-azure"></a><span data-ttu-id="7107b-248">Componenti di sincronizzazione della directory in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="7107b-248">Directory Synchronization components in Microsoft Azure</span></span>

<span data-ttu-id="7107b-249">La distribuzione dei componenti di sincronizzazione della directory di Office 365 in Azure è più veloce grazie alla possibilità di distribuire macchine virtuali su richiesta.</span><span class="sxs-lookup"><span data-stu-id="7107b-249">Deploying Office 365 directory synchronization components in Azure is faster due to the ability to deploy virtual machines on-demand.</span></span>
  
<span data-ttu-id="7107b-250">Nel diagramma di accompagnamento viene mostrato Lync Online con un tenant di Azure Active Directory, che sincronizza i nomi degli account e le password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7107b-250">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span>
  
 <span data-ttu-id="7107b-251">**Solo server di sincronizzazione della directory**.</span><span class="sxs-lookup"><span data-stu-id="7107b-251">**Directory synchronization server only**.</span></span> <span data-ttu-id="7107b-252">Invece di distribuire il server di sincronizzazione della directory a 64 bit nell'ambiente locale, è possibile eseguire il provisioning di una macchina virtuale in Azure su Internet.</span><span class="sxs-lookup"><span data-stu-id="7107b-252">Instead of deploying the 64-bit directory synchronization server in your on-premises environment, you provision a virtual machine in Azure over the Internet.</span></span>
  
 <span data-ttu-id="7107b-253">**Sincronizzazione della directory +** ADFS.</span><span class="sxs-lookup"><span data-stu-id="7107b-253">**Directory synchronization + AD FS**.</span></span> <span data-ttu-id="7107b-254">Questa opzione consente di supportare le identità federative di Office 365 senza aggiungere hardware all'infrastruttura locale.</span><span class="sxs-lookup"><span data-stu-id="7107b-254">This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure.</span></span> <span data-ttu-id="7107b-255">Inoltre, fornisce resilienza se l'ambiente Active Directory locale non è disponibile.</span><span class="sxs-lookup"><span data-stu-id="7107b-255">It also provides resiliency if the on-premises Active Directory environment is unavailable.</span></span> <span data-ttu-id="7107b-256">Le caratteristiche di questa opzione includono:</span><span class="sxs-lookup"><span data-stu-id="7107b-256">The features of this option include:</span></span>
  
- <span data-ttu-id="7107b-257">I componenti di integrazione della directory vengono eseguiti come macchine virtuali di Azure.</span><span class="sxs-lookup"><span data-stu-id="7107b-257">Directory integration components run as Azure virtual machines.</span></span>
    
- <span data-ttu-id="7107b-258">Ad FS viene pubblicato su Internet tramite proxy ADFS in esecuzione come macchine virtuali di Azure.</span><span class="sxs-lookup"><span data-stu-id="7107b-258">AD FS is published to the Internet through AD FS proxies running as Azure virtual machines.</span></span>
    
- <span data-ttu-id="7107b-259">Il traffico di autenticazione del client, per gli utenti che si connettono da qualsiasi percorso, è gestito da server ADFS e da proxy distribuiti come macchine virtuali di Azure.</span><span class="sxs-lookup"><span data-stu-id="7107b-259">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed as Azure virtual machines.</span></span>
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a><span data-ttu-id="7107b-260">Integrazione di Lync con Exchange e SharePoint in Office 365</span><span class="sxs-lookup"><span data-stu-id="7107b-260">Lync integration with Exchange and SharePoint in Office 365</span></span>

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a><span data-ttu-id="7107b-261">Lync Server con Exchange Online e SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7107b-261">Lync Server with Exchange Online and SharePoint Online</span></span>

<span data-ttu-id="7107b-262">Nel diagramma di accompagnamento viene mostrato Office 365 con Exchange Online e SharePoint Online connesso a una farm Lync Server 2013 locale.</span><span class="sxs-lookup"><span data-stu-id="7107b-262">The accompanying diagram shows Office 365 with Exchange Online and SharePoint Online connected to an on-premises Lync Server 2013 farm.</span></span>
  
<span data-ttu-id="7107b-263">I vantaggi di questa distribuzione consentono di:</span><span class="sxs-lookup"><span data-stu-id="7107b-263">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="7107b-264">Utilizzare il set di funzionalità completo di Lync Server 2013.</span><span class="sxs-lookup"><span data-stu-id="7107b-264">Use the full feature set of Lync Server 2013.</span></span>
    
- <span data-ttu-id="7107b-265">Sfruttare le apparecchiature telefoniche locali esistenti, ad esempio i sistemi PBX.</span><span class="sxs-lookup"><span data-stu-id="7107b-265">Leverage your existing on-premises phone equipment, such as PBXs.</span></span>
    
- <span data-ttu-id="7107b-266">Utilizzo di Exchange Online per la posta elettronica, disattivazione del carico dei server di posta elettronica locali e dell'archiviazione.</span><span class="sxs-lookup"><span data-stu-id="7107b-266">Use Exchange Online for email, off-loading the burden of on-premises email servers and storage.</span></span>
    
- <span data-ttu-id="7107b-267">Utilizzo di SharePoint Online per la collaborazione, disattivazione del carico di manutenzione dei server di SharePoint locali.</span><span class="sxs-lookup"><span data-stu-id="7107b-267">Use SharePoint Online for collaboration, off-loading the burden of maintaining on-premises SharePoint servers.</span></span>
    
- <span data-ttu-id="7107b-268">Utilizzare le funzionalità integrate di Lync, Exchange e SharePoint, inclusa la messaggistica unificata (UM) in Office 365.</span><span class="sxs-lookup"><span data-stu-id="7107b-268">Use Lync, Exchange, and SharePoint integrated features, including Unified Messaging (UM) in Office 365.</span></span>
    
#### <a name="exchange-server-with-lync-online"></a><span data-ttu-id="7107b-269">Server Exchange con Lync Online</span><span class="sxs-lookup"><span data-stu-id="7107b-269">Exchange Server with Lync Online</span></span>

<span data-ttu-id="7107b-270">Il diagramma di accompagnamento Visualizza Office 365 con Lync Online connesso a una farm di Exchange Server locale.</span><span class="sxs-lookup"><span data-stu-id="7107b-270">The accompanying diagram shows Office 365 with Lync Online connected to an on-premises Exchange Server farm.</span></span>
  
<span data-ttu-id="7107b-271">I vantaggi di questa distribuzione consentono di:</span><span class="sxs-lookup"><span data-stu-id="7107b-271">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="7107b-272">Sfruttare l'infrastruttura di Exchange esistente.</span><span class="sxs-lookup"><span data-stu-id="7107b-272">Leverage your existing Exchange infrastructure.</span></span>
    
- <span data-ttu-id="7107b-273">Utilizzare Lync Online per le funzionalità di presenza, messaggistica istantanea e conferenza.</span><span class="sxs-lookup"><span data-stu-id="7107b-273">Use Lync Online for presence, instant messaging, and conferencing capabilities.</span></span>
    

