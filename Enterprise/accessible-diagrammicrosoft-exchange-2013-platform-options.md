---
title: Diagramma accessibile-opzioni della piattaforma Microsoft Exchange 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: Questo articolo è una versione di testo accessibile del diagramma denominato opzioni della piattaforma Microsoft Exchange 2013, disponibile nei diagrammi tecnici.
ms.openlocfilehash: ce1fe525b6a339c64d757b82a6f1c9ea4b82d23e
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "38027570"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a><span data-ttu-id="118a5-103">Diagramma accessibile-opzioni della piattaforma Microsoft Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="118a5-103">Accessible diagram - Microsoft Exchange 2013 Platform Options</span></span>

<span data-ttu-id="118a5-104">**Riepilogo:** Questo articolo è una versione di testo accessibile del diagramma denominato opzioni della piattaforma Microsoft Exchange 2013, disponibile nei [diagrammi tecnici](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="118a5-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Exchange 2013 Platform Options, which is available at [Technical Diagrams](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="118a5-105">In questo poster vengono descritti i responsabili decisionali aziendali (BDMs) e gli architetti che devono essere a conoscenza delle distribuzioni di Exchange Online e Exchange Server e include:</span><span class="sxs-lookup"><span data-stu-id="118a5-105">This poster describes what business decision makers (BDMs) and architects need to know about Exchange Online and Exchange Server deployments and includes:</span></span> 
  
- <span data-ttu-id="118a5-106">Confronto tra quattro opzioni della piattaforma disponibili per Exchange 2013: Exchange Online (Office 365), Exchange ibrido, Exchange Server locale e Exchange ospitato dal provider.</span><span class="sxs-lookup"><span data-stu-id="118a5-106">A comparison of four available platform options for Exchange 2013: Exchange Online (Office 365), Exchange Hybrid, Exchange Server on-premises, and Provider-Hosted Exchange.</span></span> 
    
- <span data-ttu-id="118a5-107">Descrizioni di tre funzionalità nuove o aggiornate in Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="118a5-107">Descriptions of three new or updated features in Exchange 2013.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a><span data-ttu-id="118a5-108">Confronto tra quattro distribuzioni diverse per la piattaforma Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="118a5-108">Comparison of four different deployments for the Exchange 2013 platform</span></span>

<span data-ttu-id="118a5-109">Il confronto fornisce informazioni su ogni opzione di distribuzione nelle aree seguenti:</span><span class="sxs-lookup"><span data-stu-id="118a5-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="118a5-110">Panoramica delle diverse funzionalità di distribuzione</span><span class="sxs-lookup"><span data-stu-id="118a5-110">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="118a5-111">Vantaggi dell'implementazione di ogni opzione di distribuzione</span><span class="sxs-lookup"><span data-stu-id="118a5-111">Benefits of implementing each deployment option</span></span> 
    
- <span data-ttu-id="118a5-112">Requisiti relativi alle licenze</span><span class="sxs-lookup"><span data-stu-id="118a5-112">Licensing requirements</span></span> 
    
- <span data-ttu-id="118a5-113">Attività di architettura necessarie</span><span class="sxs-lookup"><span data-stu-id="118a5-113">Required architectural tasks</span></span> 
    
- <span data-ttu-id="118a5-114">Responsabilità per i professionisti IT per l'implementazione di ogni opzione di distribuzione</span><span class="sxs-lookup"><span data-stu-id="118a5-114">IT Pro responsibilities for implementing each deployment option</span></span> 
    
### <a name="overview"></a><span data-ttu-id="118a5-115">Panoramica</span><span class="sxs-lookup"><span data-stu-id="118a5-115">Overview</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="118a5-116">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="118a5-116">Exchange Online (Office 365)</span></span>

<span data-ttu-id="118a5-117">Aumentare l'efficienza e ridurre i costi con Office 365.</span><span class="sxs-lookup"><span data-stu-id="118a5-117">You gain efficiency and reduce costs with Office 365.</span></span>
  
<span data-ttu-id="118a5-118">Nel diagramma di accompagnamento viene mostrato Exchange Online con un tenant di Azure Active Directory che sincronizza i nomi e le password degli account tra l'ambiente Servizi di dominio Active Directory locale e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="118a5-118">The accompanying diagram shows Exchange Online with an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> <span data-ttu-id="118a5-119">Active Directory Federation Services (ADFS) è necessario per l'accesso Single Sign-on.</span><span class="sxs-lookup"><span data-stu-id="118a5-119">Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span> 
  
<span data-ttu-id="118a5-120">Descrizione delle funzionalità e delle funzionalità:</span><span class="sxs-lookup"><span data-stu-id="118a5-120">Description of features and functionality:</span></span>
  
- <span data-ttu-id="118a5-121">Il funzionamento dei server e del software server è gestito da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="118a5-121">The operation of servers and server software is handled by Microsoft.</span></span>
    
- <span data-ttu-id="118a5-122">Set di funzionalità RTF di Exchange Server 2013 come servizio basato su cloud.</span><span class="sxs-lookup"><span data-stu-id="118a5-122">Rich feature set of Exchange Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="118a5-123">Sempre aggiornate con le funzionalità più recenti.</span><span class="sxs-lookup"><span data-stu-id="118a5-123">Always up-to-date with the newest features.</span></span>
    
- <span data-ttu-id="118a5-124">Exchange Online Protection (EOP) è incluso per la protezione da posta indesiderata e anti-malware.</span><span class="sxs-lookup"><span data-stu-id="118a5-124">Exchange Online Protection (EOP) is included for anti-spam/anti-malware protection.</span></span>
    
- <span data-ttu-id="118a5-125">Disponibilità elevata integrata con contratto di servizio (SLA, Service Level Agreement) 99,9%.</span><span class="sxs-lookup"><span data-stu-id="118a5-125">Built-in high availability with a 99.9% Service Level Agreement (SLA).</span></span>
    
- <span data-ttu-id="118a5-126">Sincronizzazione della directory, tra cui le password tra i servizi di dominio Active Directory locale e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="118a5-126">Directory synchronization including passwords between the on-premises Active Directory Domain Services (AD DS) and the Azure Active Directory tenant.</span></span> <span data-ttu-id="118a5-127">Active Directory Federation Services (ADFS) è necessario per l'accesso Single Sign-on.</span><span class="sxs-lookup"><span data-stu-id="118a5-127">Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="118a5-128">Ambiente Exchange ibrido</span><span class="sxs-lookup"><span data-stu-id="118a5-128">Exchange Hybrid</span></span>

<span data-ttu-id="118a5-129">È possibile sfruttare i vantaggi di Office 365 durante la gestione di Exchange Server locale.</span><span class="sxs-lookup"><span data-stu-id="118a5-129">You can leverage the benefits of Office 365 while maintaining Exchange Server on-premises.</span></span>
  
<span data-ttu-id="118a5-130">Nel diagramma di accompagnamento viene mostrato Office 365 con Exchange online in cui alcuni utenti sono ospitati in locale e alcuni utenti sono alloggiati online.</span><span class="sxs-lookup"><span data-stu-id="118a5-130">The accompanying diagram shows Office 365 with Exchange Online where some users are homed on-premises and some users are homed online.</span></span> <span data-ttu-id="118a5-131">Viene inoltre visualizzato un tenant di Azure Active Directory che sincronizza i nomi e le password degli account tra l'ambiente Servizi di dominio Active Directory locale e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="118a5-131">It also shows an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
  
<span data-ttu-id="118a5-132">Descrizione delle funzionalità e delle funzionalità:</span><span class="sxs-lookup"><span data-stu-id="118a5-132">Description of features and functionality:</span></span>
  
- <span data-ttu-id="118a5-133">Alcuni utenti sono ospitati in locale e alcuni utenti sono ospitati online e gli utenti condividono lo stesso spazio di indirizzi di posta elettronica.</span><span class="sxs-lookup"><span data-stu-id="118a5-133">Some users are homed on-premises and some users are homed online, and users share the same e-mail address space.</span></span>
    
- <span data-ttu-id="118a5-134">Sfrutta l'infrastruttura di Exchange Server esistente.</span><span class="sxs-lookup"><span data-stu-id="118a5-134">Leverages your existing Exchange Server infrastructure.</span></span>
    
- <span data-ttu-id="118a5-135">Eseguire la migrazione da Exchange locale a Exchange Online nel corso del tempo, nella pianificazione.</span><span class="sxs-lookup"><span data-stu-id="118a5-135">Migrate from Exchange on-premises to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="118a5-136">Integrazione con altre applicazioni di Office 365, tra cui Lync Online e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="118a5-136">Integrate with other Office 365 applications, including Lync Online and SharePoint Online.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="118a5-137">Exchange Server locale</span><span class="sxs-lookup"><span data-stu-id="118a5-137">Exchange Server on-premises</span></span>

<span data-ttu-id="118a5-138">È possibile progettare e gestire un'infrastruttura di Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="118a5-138">You can design and manage your own Exchange Server 2013 infrastructure.</span></span>
  
<span data-ttu-id="118a5-139">Il diagramma di accompagnamento Visualizza un'infrastruttura di Exchange Server con un ambiente Servizi di dominio Active Directory (AD DS) locale in cui gli utenti sono ospitati in locale.</span><span class="sxs-lookup"><span data-stu-id="118a5-139">The accompanying diagram shows an Exchange Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="118a5-140">Descrizione delle funzionalità e delle funzionalità:</span><span class="sxs-lookup"><span data-stu-id="118a5-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="118a5-141">Maggiore grado di controllo e personalizzazione per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="118a5-141">Greatest degree of control and customization for your configuration.</span></span>
    
- <span data-ttu-id="118a5-142">Nessuna dipendenza dalla gestione dell'affinità di sessione al livello di bilanciamento del carico.</span><span class="sxs-lookup"><span data-stu-id="118a5-142">No dependency on maintaining session affinity at the load balancing layer.</span></span>
    
- <span data-ttu-id="118a5-143">Disponibilità elevata semplice e resilienza del sito mediante i gruppi di disponibilità del database (DAG).</span><span class="sxs-lookup"><span data-stu-id="118a5-143">Simple high availability and site resilience using database availability groups (DAGs).</span></span>
    
- <span data-ttu-id="118a5-144">Disponibilità gestita che consente di mantenere un'esperienza utente ottimale.</span><span class="sxs-lookup"><span data-stu-id="118a5-144">Managed availability that helps you maintain a great user experience.</span></span>
    
- <span data-ttu-id="118a5-145">Sfruttare l'infrastruttura hardware e di archiviazione esistente.</span><span class="sxs-lookup"><span data-stu-id="118a5-145">Leverage existing hardware and storage infrastructure.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="118a5-146">Exchange ospitato dal provider</span><span class="sxs-lookup"><span data-stu-id="118a5-146">Provider-Hosted Exchange</span></span>

<span data-ttu-id="118a5-147">È possibile esternalizzare il carico di lavoro del server Exchange a un provider di soluzioni di Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="118a5-147">You can outsource your Exchange Server workload to an Exchange Server solutions provider.</span></span>
  
<span data-ttu-id="118a5-148">Il diagramma di accompagnamento Visualizza un ambiente di Exchange Server gestito e gestito da un provider.</span><span class="sxs-lookup"><span data-stu-id="118a5-148">The accompanying diagram shows an Exchange Server environment that is operated and maintained by a provider.</span></span>
  
<span data-ttu-id="118a5-149">Descrizione delle funzionalità e delle funzionalità:</span><span class="sxs-lookup"><span data-stu-id="118a5-149">Description of features and functionality:</span></span>
  
- <span data-ttu-id="118a5-150">Il funzionamento dei server e del software server viene gestito dal provider.</span><span class="sxs-lookup"><span data-stu-id="118a5-150">The operation of servers and server software is handled by your provider.</span></span>
    
- <span data-ttu-id="118a5-151">La pianificazione, il ridimensionamento, la scalabilità e la manutenzione dell'infrastruttura di Exchange Server sono delegati al provider.</span><span class="sxs-lookup"><span data-stu-id="118a5-151">Planning, sizing, scaling, and maintenance of the Exchange Server infrastructure are delegated to your provider.</span></span>
    
- <span data-ttu-id="118a5-152">La manutenzione del servizio è gestita dal provider.</span><span class="sxs-lookup"><span data-stu-id="118a5-152">Service maintenance is handled by your provider.</span></span>
    
- <span data-ttu-id="118a5-153">Il set di funzionalità di Exchange è limitato alla versione software distribuita dal provider.</span><span class="sxs-lookup"><span data-stu-id="118a5-153">The Exchange feature set is limited to the software version deployed by your provider.</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="118a5-154">Vantaggi dell'implementazione di ogni opzione di distribuzione</span><span class="sxs-lookup"><span data-stu-id="118a5-154">Benefits of implementing each deployment option</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="118a5-155">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="118a5-155">Exchange Online (Office 365)</span></span>

<span data-ttu-id="118a5-156">Questa opzione di distribuzione è la soluzione ideale per:</span><span class="sxs-lookup"><span data-stu-id="118a5-156">This deployment option is best for:</span></span>
  
- <span data-ttu-id="118a5-157">Organizzazioni che desiderano ridurre i costi delle operazioni per le distribuzioni di Exchange locali.</span><span class="sxs-lookup"><span data-stu-id="118a5-157">Organizations looking to reduce operations costs for on-premises Exchange deployments.</span></span>
    
- <span data-ttu-id="118a5-158">Organizzazioni che intendono sfruttare altre offerte di Office 365, ad esempio SharePoint Online e Lync Online.</span><span class="sxs-lookup"><span data-stu-id="118a5-158">Organizations that plan to leverage other Office 365 offerings, such as SharePoint Online and Lync Online.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="118a5-159">Ambiente Exchange ibrido</span><span class="sxs-lookup"><span data-stu-id="118a5-159">Exchange Hybrid</span></span>

<span data-ttu-id="118a5-160">Questa opzione di distribuzione è la soluzione ideale per:</span><span class="sxs-lookup"><span data-stu-id="118a5-160">This deployment option is best for:</span></span>
  
- <span data-ttu-id="118a5-161">Facilitare la migrazione da Exchange locale a Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="118a5-161">Facilitating a migration from Exchange on-premises to Exchange Online.</span></span>
    
- <span data-ttu-id="118a5-162">Supporto di siti remoti senza investire nell'infrastruttura di succursale.</span><span class="sxs-lookup"><span data-stu-id="118a5-162">Supporting remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="118a5-163">Società multinazionali con filiali che richiedono l'installazione di dati in locale.</span><span class="sxs-lookup"><span data-stu-id="118a5-163">Multinational corporations with subsidiaries that require data to reside on-premises.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="118a5-164">Exchange Server locale</span><span class="sxs-lookup"><span data-stu-id="118a5-164">Exchange Server on-premises</span></span>

<span data-ttu-id="118a5-165">Questa opzione di distribuzione è la soluzione ideale per:</span><span class="sxs-lookup"><span data-stu-id="118a5-165">This deployment option is best for:</span></span>
  
- <span data-ttu-id="118a5-166">Soluzioni altamente personalizzate.</span><span class="sxs-lookup"><span data-stu-id="118a5-166">Highly customized solutions.</span></span>
    
- <span data-ttu-id="118a5-167">Soluzioni legacy con componenti di terze parti che dipendono da hardware e software che non sono supportati da Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="118a5-167">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
- <span data-ttu-id="118a5-168">Organizzazioni soggette a normative sulla governance dei dati che richiedono l'installazione di dati in locale.</span><span class="sxs-lookup"><span data-stu-id="118a5-168">Organizations subject to data governance regulations that require data to reside on-premises.</span></span>
    
- <span data-ttu-id="118a5-169">Organizzazioni che desiderano mantenere il controllo dell'intera piattaforma e della soluzione.</span><span class="sxs-lookup"><span data-stu-id="118a5-169">Organizations that wish to retain control of the entire platform and solution.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="118a5-170">Exchange ospitato dal provider</span><span class="sxs-lookup"><span data-stu-id="118a5-170">Provider-Hosted Exchange</span></span>

<span data-ttu-id="118a5-171">Questa opzione di distribuzione è la soluzione ideale per:</span><span class="sxs-lookup"><span data-stu-id="118a5-171">This deployment option is best for:</span></span>
  
- <span data-ttu-id="118a5-172">Organizzazioni che necessitano di funzionalità di Exchange Server, ma che desiderano esternalizzare la distribuzione e la manutenzione.</span><span class="sxs-lookup"><span data-stu-id="118a5-172">Organizations that need Exchange Server functionality, but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="118a5-173">Organizzazioni che richiedono opzioni di supporto personalizzate.</span><span class="sxs-lookup"><span data-stu-id="118a5-173">Organizations that need personalized support options.</span></span>
    
- <span data-ttu-id="118a5-174">Soluzioni personalizzate e integrazione con le applicazioni personalizzate offerte dal provider.</span><span class="sxs-lookup"><span data-stu-id="118a5-174">Customized solutions and integration with custom applications offered by the provider.</span></span>
    
- <span data-ttu-id="118a5-175">Soluzioni legacy con componenti di terze parti che dipendono da hardware e software che non sono supportati da Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="118a5-175">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="118a5-176">Requisiti di licenza</span><span class="sxs-lookup"><span data-stu-id="118a5-176">License requirements</span></span>

<span data-ttu-id="118a5-177">Nella tabella seguente vengono illustrati i requisiti di licenza per ogni opzione di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="118a5-177">The following table details the license requirements for each deployment option.</span></span>
  
|<span data-ttu-id="118a5-178">**Opzione di distribuzione**</span><span class="sxs-lookup"><span data-stu-id="118a5-178">**Deployment option**</span></span>|<span data-ttu-id="118a5-179">**Requisiti di licenza**</span><span class="sxs-lookup"><span data-stu-id="118a5-179">**License requirements**</span></span>|
|:-----|:-----|
|<span data-ttu-id="118a5-180">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="118a5-180">Exchange Online (Office 365)</span></span>  <br/> |<span data-ttu-id="118a5-181">Modello di sottoscrizione</span><span class="sxs-lookup"><span data-stu-id="118a5-181">Subscription model</span></span>  <br/> |
|<span data-ttu-id="118a5-182">Ambiente Exchange ibrido</span><span class="sxs-lookup"><span data-stu-id="118a5-182">Exchange Hybrid</span></span>  <br/> | <span data-ttu-id="118a5-183">Office 365-modello di sottoscrizione</span><span class="sxs-lookup"><span data-stu-id="118a5-183">Office 365 - Subscription model</span></span> <br/>  <span data-ttu-id="118a5-184">On-premises-tutte le licenze locali si applicano (verifica licenze per Exchange Server locale)</span><span class="sxs-lookup"><span data-stu-id="118a5-184">On-premises - All on-premises licenses apply (review licenses for Exchanges Server on-premises)</span></span> <br/>  <span data-ttu-id="118a5-185">Licenza del server ibrido \*</span><span class="sxs-lookup"><span data-stu-id="118a5-185">Hybrid server license\*</span></span> <br/> |
|<span data-ttu-id="118a5-186">Exchange Server locale</span><span class="sxs-lookup"><span data-stu-id="118a5-186">Exchange Server on-premises</span></span>  <br/> | <span data-ttu-id="118a5-187">Sistema operativo del server</span><span class="sxs-lookup"><span data-stu-id="118a5-187">Server Operating System</span></span> <br/>  <span data-ttu-id="118a5-188">Licenza del server di Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="118a5-188">Exchange 2013 Server License</span></span> <br/>  <span data-ttu-id="118a5-189">Licenza di accesso client di Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="118a5-189">Exchange 2013 Client Access License</span></span> <br/> |
|<span data-ttu-id="118a5-190">Exchange ospitato dal provider</span><span class="sxs-lookup"><span data-stu-id="118a5-190">Provider-Hosted Exchange</span></span>  <br/> |<span data-ttu-id="118a5-191">I costi sono basati sull'accordo con il provider</span><span class="sxs-lookup"><span data-stu-id="118a5-191">Costs are based on the agreement with the provider</span></span>  <br/> |
   
### <a name="architecture-tasks"></a><span data-ttu-id="118a5-192">Attività dell'architettura</span><span class="sxs-lookup"><span data-stu-id="118a5-192">Architecture tasks</span></span>

<span data-ttu-id="118a5-193">In questa sezione sono elencate le attività di architettura per ogni opzione di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="118a5-193">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="118a5-194">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="118a5-194">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="118a5-195">Pianificare e progettare la sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="118a5-195">Plan and design the directory synchronization.</span></span>
    
- <span data-ttu-id="118a5-196">Garantire la connettività e la capacità di rete tramite firewall, server proxy, gateway e tra i collegamenti WAN.</span><span class="sxs-lookup"><span data-stu-id="118a5-196">Ensure network capacity and connectivity through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="118a5-197">Ambiente Exchange ibrido</span><span class="sxs-lookup"><span data-stu-id="118a5-197">Exchange Hybrid</span></span>

<span data-ttu-id="118a5-198">Oltre alle attività dell'architettura sia per gli ambienti Office 365 che per quelli locali:</span><span class="sxs-lookup"><span data-stu-id="118a5-198">In addition to the architecture tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="118a5-199">Decidere se fornire un'esperienza Single Sign-on.</span><span class="sxs-lookup"><span data-stu-id="118a5-199">Decide whether to provide a single-sign on experience.</span></span>
    
- <span data-ttu-id="118a5-200">Decidere se instradare la posta Internet in ingresso tramite un'organizzazione locale o tramite Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="118a5-200">Decide whether to route inbound Internet mail through an on-premises organization or through Exchange Online Protection.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="118a5-201">Exchange Server locale</span><span class="sxs-lookup"><span data-stu-id="118a5-201">Exchange Server on-premises</span></span>

- <span data-ttu-id="118a5-202">Progettare la topologia di Exchange.</span><span class="sxs-lookup"><span data-stu-id="118a5-202">Design the Exchange topology.</span></span>
    
- <span data-ttu-id="118a5-203">Pianificare la capacità per l'hardware del server.</span><span class="sxs-lookup"><span data-stu-id="118a5-203">Plan the capacity for server hardware.</span></span>
    
- <span data-ttu-id="118a5-204">Progettare la topologia di routing dei messaggi.</span><span class="sxs-lookup"><span data-stu-id="118a5-204">Design the message routing topology.</span></span>
    
- <span data-ttu-id="118a5-205">Progettare il bilanciamento del carico per i server Accesso client.</span><span class="sxs-lookup"><span data-stu-id="118a5-205">Design load balancing for Client Access servers.</span></span>
    
- <span data-ttu-id="118a5-206">Pianificare la disponibilità elevata utilizzando i gruppi di disponibilità del database.</span><span class="sxs-lookup"><span data-stu-id="118a5-206">Plan for high availability using database availability groups.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="118a5-207">Exchange ospitato dal provider</span><span class="sxs-lookup"><span data-stu-id="118a5-207">Provider-Hosted Exchange</span></span>

<span data-ttu-id="118a5-208">Garantire che la capacità e la disponibilità della rete tramite i firewall, i server proxy, i gateway e i collegamenti WAN siano disponibili per il provider.</span><span class="sxs-lookup"><span data-stu-id="118a5-208">Ensure that the network capacity and availability through firewalls, proxy servers, gateways, and across WAN links are available to your provider.</span></span>
  
### <a name="it-pro-responsibilities"></a><span data-ttu-id="118a5-209">Responsabilità per i professionisti IT</span><span class="sxs-lookup"><span data-stu-id="118a5-209">IT Pro responsibilities</span></span>

<span data-ttu-id="118a5-210">In questa sezione sono elencate le responsabilità per i professionisti IT per ogni opzione di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="118a5-210">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="118a5-211">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="118a5-211">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="118a5-212">Implementare il piano di sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="118a5-212">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="118a5-213">Pianificare e implementare i record DNS interni ed esterni e il routing.</span><span class="sxs-lookup"><span data-stu-id="118a5-213">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="118a5-214">Configurare il server proxy o il firewall per i requisiti di URL e indirizzi IP di Office 365.</span><span class="sxs-lookup"><span data-stu-id="118a5-214">Configure the proxy server or firewall for the Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="118a5-215">Amministrare gli account utente e le impostazioni di Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="118a5-215">Administer the user accounts and the Exchange Online settings.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="118a5-216">Ambiente Exchange ibrido</span><span class="sxs-lookup"><span data-stu-id="118a5-216">Exchange Hybrid</span></span>

<span data-ttu-id="118a5-217">Oltre alle responsabilità Pro IT sia per gli ambienti Office 365 che per quelli locali:</span><span class="sxs-lookup"><span data-stu-id="118a5-217">In addition to the IT Pro responsibilities for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="118a5-218">Configurare Active Directory Federation Services (AD FS) per Single Sign-on (se lo si desidera).</span><span class="sxs-lookup"><span data-stu-id="118a5-218">Configure Active Directory Federation Services (AD FS) for single-sign on (if desired).</span></span>
    
- <span data-ttu-id="118a5-219">Configurare i certificati di Exchange per le comunicazioni sicure tra Exchange 2013 Servers e Office 365.</span><span class="sxs-lookup"><span data-stu-id="118a5-219">Configure Exchange certificates for secure communications between Exchange 2013 servers and Office 365.</span></span>
    
- <span data-ttu-id="118a5-220">Configurare i record DNS per il percorso di posta Internet in ingresso desiderato.</span><span class="sxs-lookup"><span data-stu-id="118a5-220">Configure DNS records for the desired inbound Internet mail path.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="118a5-221">Exchange Server locale</span><span class="sxs-lookup"><span data-stu-id="118a5-221">Exchange Server on-premises</span></span>

- <span data-ttu-id="118a5-222">Configurare i certificati necessari per i servizi di Exchange.</span><span class="sxs-lookup"><span data-stu-id="118a5-222">Configure the necessary certificates for Exchange services.</span></span>
    
- <span data-ttu-id="118a5-223">Eseguire il provisioning dei server.</span><span class="sxs-lookup"><span data-stu-id="118a5-223">Provision the servers.</span></span>
    
- <span data-ttu-id="118a5-224">Implementare la topologia di routing dei messaggi di Exchange.</span><span class="sxs-lookup"><span data-stu-id="118a5-224">Implement the Exchange message routing topology.</span></span>
    
- <span data-ttu-id="118a5-225">Implementare i gruppi di disponibilità del database.</span><span class="sxs-lookup"><span data-stu-id="118a5-225">Implement database availability groups.</span></span>
    
- <span data-ttu-id="118a5-226">Aggiornare e gestire i server di Exchange.</span><span class="sxs-lookup"><span data-stu-id="118a5-226">Update and maintain Exchange servers.</span></span>
    
- <span data-ttu-id="118a5-227">A seconda dell'utilizzo, aggiungere o rimuovere server in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="118a5-227">Depending on utilization, add or remove servers as needed.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="118a5-228">Exchange ospitato dal provider</span><span class="sxs-lookup"><span data-stu-id="118a5-228">Provider-Hosted Exchange</span></span>

<span data-ttu-id="118a5-229">Le responsabilità del provider sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="118a5-229">The provider's responsibilities include:</span></span>
  
- <span data-ttu-id="118a5-230">Manutenzione del sistema e del servizio.</span><span class="sxs-lookup"><span data-stu-id="118a5-230">System and service maintenance.</span></span>
    
- <span data-ttu-id="118a5-231">Feature graduali.</span><span class="sxs-lookup"><span data-stu-id="118a5-231">Feature rollouts.</span></span>
    
- <span data-ttu-id="118a5-232">Protezione dei dati e ripristino di emergenza.</span><span class="sxs-lookup"><span data-stu-id="118a5-232">Data protection and disaster recovery.</span></span>
    
<span data-ttu-id="118a5-233">Le responsabilità del personale IT nell'organizzazione includono la creazione e la gestione degli account utente.</span><span class="sxs-lookup"><span data-stu-id="118a5-233">The IT staff's responsibilities in your organization include creating and managing user accounts.</span></span>
  
#### <a name="more-information"></a><span data-ttu-id="118a5-234">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="118a5-234">More information</span></span>

<span data-ttu-id="118a5-235">Per ulteriori informazioni su Exchange Online (Office 365), vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="118a5-235">To learn more about Exchange Online (Office 365), see the following:</span></span>
  
- [<span data-ttu-id="118a5-236">Descrizione del servizio Exchange Online</span><span class="sxs-lookup"><span data-stu-id="118a5-236">Exchange Online service description</span></span>](https://aka.ms/EXOSD)
    
- [<span data-ttu-id="118a5-237">Libreria di Exchange Online su TechNet</span><span class="sxs-lookup"><span data-stu-id="118a5-237">Exchange Online library on TechNet</span></span>](https://aka.ms/EXOTN)
    
- [<span data-ttu-id="118a5-238">Portale di Exchange Online</span><span class="sxs-lookup"><span data-stu-id="118a5-238">Exchange Online portal</span></span>](https://aka.ms/EXO)
    
<span data-ttu-id="118a5-239">Per ulteriori informazioni su Exchange Hybrid, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="118a5-239">To learn more about Exchange Hybrid, see the following:</span></span>
  
- <span data-ttu-id="118a5-240">[Distribuzioni ibride di Exchange 2013](https://aka.ms/ExchangeHybrid).</span><span class="sxs-lookup"><span data-stu-id="118a5-240">[Exchange 2013 hybrid deployments](https://aka.ms/ExchangeHybrid).</span></span> <span data-ttu-id="118a5-241">È necessario tenere presente che la licenza del server ibrido è necessaria solo per gli scenari seguenti: organizzazione di Exchange 2010 con Exchange 2013 Hybrid server ed Exchange 2007 Organization con Exchange 2013 o Exchange 2010 Hybrid server.</span><span class="sxs-lookup"><span data-stu-id="118a5-241">You should note that the Hybrid server license is only required for the following scenarios: Exchange 2010 organization with Exchange 2013 hybrid server and Exchange 2007 organization with Exchange 2013 or Exchange 2010 hybrid server.</span></span>
    
- [<span data-ttu-id="118a5-242">Accesso a Office 365</span><span class="sxs-lookup"><span data-stu-id="118a5-242">Office 365 Sign in</span></span>](https://aka.ms/HybridKey)
    
<span data-ttu-id="118a5-243">Per ulteriori informazioni su Exchange Server locale, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="118a5-243">To learn more about Exchange Server on-premises, see the following:</span></span>
  
- [<span data-ttu-id="118a5-244">Libreria di Exchange Server 2013 su TechNet</span><span class="sxs-lookup"><span data-stu-id="118a5-244">Exchange Server 2013 library on TechNet</span></span>](https://aka.ms/Ex2013TN)
    
- [<span data-ttu-id="118a5-245">Portale di Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="118a5-245">Exchange Server 2013 portal</span></span>](https://aka.ms/Exchange2013)
    
- [<span data-ttu-id="118a5-246">Architettura di Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="118a5-246">Exchange Server 2013 architecture</span></span>](https://aka.ms/Ex2013SP1ArchPoster)
    
<span data-ttu-id="118a5-247">Per ulteriori informazioni su Exchange ospitato dal provider, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="118a5-247">To learn more about Provider-Hosted Exchange, see the following:</span></span>
  
[<span data-ttu-id="118a5-248">Exchange Server 2013 hosting e soluzioni e linee guida per la multi-locazione</span><span class="sxs-lookup"><span data-stu-id="118a5-248">Exchange Server 2013 hosting and multi-tenancy solutions and guidance</span></span>](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a><span data-ttu-id="118a5-249">Descrizioni di tre funzionalità nuove o aggiornate in Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="118a5-249">Descriptions of three new or updated features in Exchange 2013</span></span>

### <a name="exchange-online-protection"></a><span data-ttu-id="118a5-250">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="118a5-250">Exchange Online Protection</span></span>

<span data-ttu-id="118a5-251">Exchange Online Protection (EOP) fornisce protezione da posta indesiderata e antimalware per qualsiasi distribuzione fornendo un livello di funzionalità di protezione distribuite su una rete globale di Data Center.</span><span class="sxs-lookup"><span data-stu-id="118a5-251">Exchange Online Protection (EOP) provides anti-spam and anti-malware protection for any deployment by providing a layer of protection features that are deployed across a global network of data centers.</span></span> <span data-ttu-id="118a5-252">In questo modo è possibile semplificare la gestione degli ambienti di messaggistica.</span><span class="sxs-lookup"><span data-stu-id="118a5-252">This helps you to simplify the management of your messaging environments.</span></span> <span data-ttu-id="118a5-253">EOP è incluso nelle sottoscrizioni di Exchange Online, ma è possibile utilizzarlo anche per le distribuzioni ibride e locali.</span><span class="sxs-lookup"><span data-stu-id="118a5-253">EOP is included in Exchange Online subscriptions, but you can also leverage it for hybrid and on-premises deployments.</span></span>
  
<span data-ttu-id="118a5-254">Nei diagrammi di accompagnamento vengono illustrate le distribuzioni per Exchange Online, Exchange Hybrid ed Exchange locale che includono il livello EOP nella rete globale.</span><span class="sxs-lookup"><span data-stu-id="118a5-254">The accompanying diagrams show deployments for Exchange Online, Exchange Hybrid, and Exchange on-premises that include the EOP layer in the global network.</span></span>
  
### <a name="exchange-server-deployment-assistant"></a><span data-ttu-id="118a5-255">Assistente per la distribuzione di Exchange Server</span><span class="sxs-lookup"><span data-stu-id="118a5-255">Exchange Server Deployment Assistant</span></span>

<span data-ttu-id="118a5-256">L'assistente per la distribuzione di Exchange Server è uno strumento basato sul Web che richiede alcune domande sull'ambiente corrente e quindi genera un elenco di controllo dettagliato personalizzato per facilitare la distribuzione di Exchange Server per diversi tipi di scenari.</span><span class="sxs-lookup"><span data-stu-id="118a5-256">The Exchange Server Deployment Assistant is a web-based tool that asks you a few questions about your current environment, and then generates a custom step-by-step checklist to help you deploy Exchange Server for different types of scenarios.</span></span> <span data-ttu-id="118a5-257">Se si esegue la migrazione da una versione precedente di Exchange a Exchange 2013, la migrazione a Exchange Online o la pianificazione di un'infrastruttura ibrida, l'assistente per la distribuzione di Exchange Server crea un elenco di controllo di distribuzione personalizzato per lo scenario.</span><span class="sxs-lookup"><span data-stu-id="118a5-257">Whether you are migrating from a previous version of Exchange to Exchange 2013, migrating to Exchange Online, or planning a hybrid infrastructure, the Exchange Server Deployment Assistant creates a customized deployment checklist for your scenario.</span></span>
  
<span data-ttu-id="118a5-258">Nella schermata di accompagnamento viene visualizzato un elenco di controllo di esempio creato utilizzando l'assistente per la distribuzione di Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="118a5-258">The accompanying screenshot shows an example checklist that was created using the Exchange Server Deployment Assistant.</span></span>
  
### <a name="integration-with-lync-and-sharepoint"></a><span data-ttu-id="118a5-259">Integrazione con Lync e SharePoint</span><span class="sxs-lookup"><span data-stu-id="118a5-259">Integration with Lync and SharePoint</span></span>

<span data-ttu-id="118a5-260">Exchange Server 2013 include numerose funzionalità che si integrano con Lync Server 2013 e SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="118a5-260">Exchange Server 2013 includes many features that integrate with Lync Server 2013 and SharePoint Server 2013.</span></span> <span data-ttu-id="118a5-261">Insieme, questi prodotti offrono una ricca gamma di funzionalità e migliorano la collaborazione all'interno dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="118a5-261">Together, these products offer a rich suite of features and improve collaboration across your organization.</span></span> 
  
<span data-ttu-id="118a5-262">Un diagramma di accompagnamento Visualizza il poster di autenticazione da server a server e include un collegamento al poster.</span><span class="sxs-lookup"><span data-stu-id="118a5-262">An accompanying diagram shows the Server-to-Server Authentication poster and includes a link to the poster.</span></span> 
  
- <span data-ttu-id="118a5-263">Archiviazione, blocco e eDiscovery</span><span class="sxs-lookup"><span data-stu-id="118a5-263">Archiving, hold and eDiscovery</span></span>
    
- <span data-ttu-id="118a5-264">Cassette postali del sito</span><span class="sxs-lookup"><span data-stu-id="118a5-264">Site mailboxes</span></span>
    
- <span data-ttu-id="118a5-265">Archivio contatti unificato</span><span class="sxs-lookup"><span data-stu-id="118a5-265">Unified contact store</span></span>
    
- <span data-ttu-id="118a5-266">Foto degli utenti ad alta risoluzione</span><span class="sxs-lookup"><span data-stu-id="118a5-266">High-resolution user photos</span></span>
    
- <span data-ttu-id="118a5-267">Presenza di Lync in Outlook e Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="118a5-267">Lync presence in Outlook and Outlook Web App</span></span>
    
- <span data-ttu-id="118a5-268">Autenticazione da server a server</span><span class="sxs-lookup"><span data-stu-id="118a5-268">Server-to-server authentication</span></span>
    
- <span data-ttu-id="118a5-269">Segreteria telefonica</span><span class="sxs-lookup"><span data-stu-id="118a5-269">Voicemail</span></span>
    
- <span data-ttu-id="118a5-270">Registrazioni di riunioni</span><span class="sxs-lookup"><span data-stu-id="118a5-270">Meeting recordings</span></span>
    
- <span data-ttu-id="118a5-271">Sincronizzazione delle attività di Exchange</span><span class="sxs-lookup"><span data-stu-id="118a5-271">Exchange task synchronization</span></span>
    
<span data-ttu-id="118a5-272">Un diagramma di accompagnamento Visualizza il poster dell'architettura di Exchange Server 2013 SP1 e include un collegamento al poster.</span><span class="sxs-lookup"><span data-stu-id="118a5-272">An accompanying diagram shows the Exchange Server 2013 SP1 Architecture poster and includes a link to the poster.</span></span>
  

