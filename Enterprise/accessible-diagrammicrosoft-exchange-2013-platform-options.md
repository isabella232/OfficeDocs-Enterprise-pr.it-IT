---
title: Diagramma accessibile - opzioni della piattaforma di Microsoft Exchange 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: In questo articolo è una versione testo accessibile del diagramma denominato opzioni della piattaforma di Microsoft Exchange 2013, disponibile all'indirizzo Technical Diagrams.
ms.openlocfilehash: e1c4957c9152c5a23008c657d7e2d0d47b5cce0f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
ms.locfileid: "17503129"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a><span data-ttu-id="8ebd5-103">Diagramma accessibile - opzioni della piattaforma di Microsoft Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="8ebd5-103">Accessible diagram - Microsoft Exchange 2013 Platform Options</span></span>

<span data-ttu-id="8ebd5-104">**Riepilogo:** In questo articolo è una versione testo accessibile del diagramma denominato opzioni della piattaforma di Microsoft Exchange 2013, disponibile all'indirizzo [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="8ebd5-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Exchange 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="8ebd5-105">Questo poster viene descritto cosa decisori aziendali (hanno) e progettisti devono essere a conoscenza le distribuzioni di Exchange Online ed Exchange Server e sono incluse:</span><span class="sxs-lookup"><span data-stu-id="8ebd5-105">This poster describes what business decision makers (BDMs) and architects need to know about Exchange Online and Exchange Server deployments and includes:</span></span> 
  
- <span data-ttu-id="8ebd5-106">Confronto di quattro opzioni della piattaforma disponibili per Exchange 2013: Exchange Online (Office 365), Exchange Hybrid Server Exchange locale ed Exchange Provider-Hosted.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-106">A comparison of four available platform options for Exchange 2013: Exchange Online (Office 365), Exchange Hybrid, Exchange Server on-premises, and Provider-Hosted Exchange.</span></span> 
    
- <span data-ttu-id="8ebd5-107">Descrizioni di tre le caratteristiche nuove o aggiornate in Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-107">Descriptions of three new or updated features in Exchange 2013.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a><span data-ttu-id="8ebd5-108">Confronto tra quattro diverse distribuzioni per la piattaforma Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="8ebd5-108">Comparison of four different deployments for the Exchange 2013 platform</span></span>

<span data-ttu-id="8ebd5-109">Il confronto vengono fornite informazioni su ogni opzione di distribuzione nelle aree seguenti:</span><span class="sxs-lookup"><span data-stu-id="8ebd5-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="8ebd5-110">Panoramica delle funzionalità di distribuzione diversi</span><span class="sxs-lookup"><span data-stu-id="8ebd5-110">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="8ebd5-111">Vantaggi dell'implementazione di ogni opzione di distribuzione</span><span class="sxs-lookup"><span data-stu-id="8ebd5-111">Benefits of implementing each deployment option</span></span> 
    
- <span data-ttu-id="8ebd5-112">Requisiti relativi alle licenze</span><span class="sxs-lookup"><span data-stu-id="8ebd5-112">Licensing requirements</span></span> 
    
- <span data-ttu-id="8ebd5-113">Richiesta attività dell'architettura</span><span class="sxs-lookup"><span data-stu-id="8ebd5-113">Required architectural tasks</span></span> 
    
- <span data-ttu-id="8ebd5-114">Responsabilità di professionisti IT per l'implementazione di ogni opzione di distribuzione</span><span class="sxs-lookup"><span data-stu-id="8ebd5-114">IT Pro responsibilities for implementing each deployment option</span></span> 
    
### <a name="overview"></a><span data-ttu-id="8ebd5-115">Panoramica</span><span class="sxs-lookup"><span data-stu-id="8ebd5-115">Overview</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="8ebd5-116">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="8ebd5-116">Exchange Online (Office 365)</span></span>

<span data-ttu-id="8ebd5-117">Maggiore efficienza e ridurre i costi con Office 365.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-117">You gain efficiency and reduce costs with Office 365.</span></span>
  
<span data-ttu-id="8ebd5-p101">Nella figura relativa Mostra Exchange Online con un tenant di Azure Active Directory che consente di sincronizzare i nomi degli account e password tra l'ambiente di servizi di dominio Active Directory (AD DS) locali e il tenant di Azure Active Directory. Active Directory Federation Services (ADFS) è necessario per single sign-on.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-p101">The accompanying diagram shows Exchange Online with an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant. Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span> 
  
<span data-ttu-id="8ebd5-120">Descrizione delle funzionalità e caratteristiche:</span><span class="sxs-lookup"><span data-stu-id="8ebd5-120">Description of features and functionality:</span></span>
  
- <span data-ttu-id="8ebd5-121">Il funzionamento del server e il software del server viene gestito da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-121">The operation of servers and server software is handled by Microsoft.</span></span>
    
- <span data-ttu-id="8ebd5-122">Set di caratteristiche complete di Exchange Server 2013 come un servizio basato su cloud.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-122">Rich feature set of Exchange Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="8ebd5-123">Sempre aggiornati con le funzionalità più recente.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-123">Always up-to-date with the newest features.</span></span>
    
- <span data-ttu-id="8ebd5-124">Exchange Online Protection (EOP) è incluso per la protezione da posta indesiderata/protezione anti malware.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-124">Exchange Online Protection (EOP) is included for anti-spam/anti-malware protection.</span></span>
    
- <span data-ttu-id="8ebd5-125">Disponibilità elevata incorporata con 99,9% Service Level Agreement (SLA).</span><span class="sxs-lookup"><span data-stu-id="8ebd5-125">Built-in high availability with a 99.9% Service Level Agreement (SLA).</span></span>
    
- <span data-ttu-id="8ebd5-p102">Sincronizzazione delle directory tra cui le password tra locali Active Directory Domain Services (AD DS) e il tenant di Azure Active Directory. Active Directory Federation Services (ADFS) è necessario per single sign-on.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-p102">Directory synchronization including passwords between the on-premises Active Directory Domain Services (AD DS) and the Azure Active Directory tenant. Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="8ebd5-128">Ibrida di Exchange</span><span class="sxs-lookup"><span data-stu-id="8ebd5-128">Exchange Hybrid</span></span>

<span data-ttu-id="8ebd5-129">È possibile sfruttare i vantaggi di Office 365 durante la gestione di Exchange Server locale.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-129">You can leverage the benefits of Office 365 while maintaining Exchange Server on-premises.</span></span>
  
<span data-ttu-id="8ebd5-p103">Il diagramma accompagnamento Mostra Office 365 con Exchange Online in cui alcuni utenti sono in locale e alcuni utenti ospitati in linea. Viene inoltre un tenant di Azure Active Directory che consente di sincronizzare i nomi degli account e password tra l'ambiente di servizi di dominio Active Directory (AD DS) locali e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-p103">The accompanying diagram shows Office 365 with Exchange Online where some users are homed on-premises and some users are homed online. It also shows an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
  
<span data-ttu-id="8ebd5-132">Descrizione delle funzionalità e caratteristiche:</span><span class="sxs-lookup"><span data-stu-id="8ebd5-132">Description of features and functionality:</span></span>
  
- <span data-ttu-id="8ebd5-133">Alcuni utenti sono ospitati in locale e alcuni utenti ospitati in linea e gli utenti hanno lo stesso spazio degli indirizzi di posta elettronica.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-133">Some users are homed on-premises and some users are homed online, and users share the same e-mail address space.</span></span>
    
- <span data-ttu-id="8ebd5-134">Sfrutta l'infrastruttura di Exchange Server esistente.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-134">Leverages your existing Exchange Server infrastructure.</span></span>
    
- <span data-ttu-id="8ebd5-135">Eseguire la migrazione di Exchange locale a Exchange Online nel tempo, al calendario.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-135">Migrate from Exchange on-premises to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="8ebd5-136">Integrazione con altre applicazioni di Office 365, tra cui Lync Online e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-136">Integrate with other Office 365 applications, including Lync Online and SharePoint Online.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="8ebd5-137">Server di Exchange in locale</span><span class="sxs-lookup"><span data-stu-id="8ebd5-137">Exchange Server on-premises</span></span>

<span data-ttu-id="8ebd5-138">È possibile progettare e gestire l'infrastruttura Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-138">You can design and manage your own Exchange Server 2013 infrastructure.</span></span>
  
<span data-ttu-id="8ebd5-139">Il diagramma accompagnamento Mostra un'infrastruttura di Exchange Server con un ambiente di servizi di dominio Active Directory (AD DS) locale in cui gli utenti sono in locale.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-139">The accompanying diagram shows an Exchange Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="8ebd5-140">Descrizione delle funzionalità e caratteristiche:</span><span class="sxs-lookup"><span data-stu-id="8ebd5-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="8ebd5-141">Massimo grado di controllo e la personalizzazione per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-141">Greatest degree of control and customization for your configuration.</span></span>
    
- <span data-ttu-id="8ebd5-142">Nessuna dipendenza da mantenere l'affinità di sessione a livello di bilanciamento del carico.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-142">No dependency on maintaining session affinity at the load balancing layer.</span></span>
    
- <span data-ttu-id="8ebd5-143">Semplice elevata disponibilità e resilienza del sito utilizzando gruppi di disponibilità del database (DAG).</span><span class="sxs-lookup"><span data-stu-id="8ebd5-143">Simple high availability and site resilience using database availability groups (DAGs).</span></span>
    
- <span data-ttu-id="8ebd5-144">Managed availability che consente di mantenere un ambiente ottimale.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-144">Managed availability that helps you maintain a great user experience.</span></span>
    
- <span data-ttu-id="8ebd5-145">Utilizzare hardware esistente e l'infrastruttura di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-145">Leverage existing hardware and storage infrastructure.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="8ebd5-146">Exchange ospitata dal provider</span><span class="sxs-lookup"><span data-stu-id="8ebd5-146">Provider-Hosted Exchange</span></span>

<span data-ttu-id="8ebd5-147">È possibile affidare il carico di lavoro di Exchange Server a un provider di soluzioni di Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-147">You can outsource your Exchange Server workload to an Exchange Server solutions provider.</span></span>
  
<span data-ttu-id="8ebd5-148">Nella figura relativa viene illustrato un ambiente di Exchange Server di gestione e manutenzione per un provider.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-148">The accompanying diagram shows an Exchange Server environment that is operated and maintained by a provider.</span></span>
  
<span data-ttu-id="8ebd5-149">Descrizione delle funzionalità e caratteristiche:</span><span class="sxs-lookup"><span data-stu-id="8ebd5-149">Description of features and functionality:</span></span>
  
- <span data-ttu-id="8ebd5-150">Il funzionamento del server e il software del server viene gestito dal provider.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-150">The operation of servers and server software is handled by your provider.</span></span>
    
- <span data-ttu-id="8ebd5-151">Pianificazione, dimensioni, scalabilità e la manutenzione dell'infrastruttura di Exchange Server vengono delegate al provider.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-151">Planning, sizing, scaling, and maintenance of the Exchange Server infrastructure are delegated to your provider.</span></span>
    
- <span data-ttu-id="8ebd5-152">Manutenzione del servizio viene gestita dal provider.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-152">Service maintenance is handled by your provider.</span></span>
    
- <span data-ttu-id="8ebd5-153">Il set di caratteristiche di Exchange è limitato alla versione software distribuita dal provider.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-153">The Exchange feature set is limited to the software version deployed by your provider.</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="8ebd5-154">Vantaggi dell'implementazione di ogni opzione di distribuzione</span><span class="sxs-lookup"><span data-stu-id="8ebd5-154">Benefits of implementing each deployment option</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="8ebd5-155">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="8ebd5-155">Exchange Online (Office 365)</span></span>

<span data-ttu-id="8ebd5-156">Questa opzione di distribuzione è la soluzione migliore per:</span><span class="sxs-lookup"><span data-stu-id="8ebd5-156">This deployment option is best for:</span></span>
  
- <span data-ttu-id="8ebd5-157">Le organizzazioni che desiderano ridurre i costi di operazioni locali di Exchange distribuzioni.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-157">Organizations looking to reduce operations costs for on-premises Exchange deployments.</span></span>
    
- <span data-ttu-id="8ebd5-158">Le organizzazioni che prevedono di utilizzare altre offerte di Office 365, ad esempio SharePoint Online e Lync Online.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-158">Organizations that plan to leverage other Office 365 offerings, such as SharePoint Online and Lync Online.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="8ebd5-159">Ibrida di Exchange</span><span class="sxs-lookup"><span data-stu-id="8ebd5-159">Exchange Hybrid</span></span>

<span data-ttu-id="8ebd5-160">Questa opzione di distribuzione è la soluzione migliore per:</span><span class="sxs-lookup"><span data-stu-id="8ebd5-160">This deployment option is best for:</span></span>
  
- <span data-ttu-id="8ebd5-161">Semplificazione di una migrazione di Exchange locale a Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-161">Facilitating a migration from Exchange on-premises to Exchange Online.</span></span>
    
- <span data-ttu-id="8ebd5-162">Supporto siti remoti senza investimenti nell'infrastruttura office succursale.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-162">Supporting remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="8ebd5-163">Multinazionali con le filiali che richiedono dati si trovano in locale.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-163">Multinational corporations with subsidiaries that require data to reside on-premises.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="8ebd5-164">Server di Exchange in locale</span><span class="sxs-lookup"><span data-stu-id="8ebd5-164">Exchange Server on-premises</span></span>

<span data-ttu-id="8ebd5-165">Questa opzione di distribuzione è la soluzione migliore per:</span><span class="sxs-lookup"><span data-stu-id="8ebd5-165">This deployment option is best for:</span></span>
  
- <span data-ttu-id="8ebd5-166">Soluzioni fortemente personalizzate.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-166">Highly customized solutions.</span></span>
    
- <span data-ttu-id="8ebd5-167">Soluzioni legacy con i componenti di terze parti che dipendono da hardware e software che non sono supportate da Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-167">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
- <span data-ttu-id="8ebd5-168">Le organizzazioni oggetto la normativa governance dati che richiedono dati si trovano in locale.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-168">Organizations subject to data governance regulations that require data to reside on-premises.</span></span>
    
- <span data-ttu-id="8ebd5-169">Le organizzazioni che si desiderano mantengono il controllo dell'intera piattaforma e soluzione.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-169">Organizations that wish to retain control of the entire platform and solution.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="8ebd5-170">Exchange ospitata dal provider</span><span class="sxs-lookup"><span data-stu-id="8ebd5-170">Provider-Hosted Exchange</span></span>

<span data-ttu-id="8ebd5-171">Questa opzione di distribuzione è la soluzione migliore per:</span><span class="sxs-lookup"><span data-stu-id="8ebd5-171">This deployment option is best for:</span></span>
  
- <span data-ttu-id="8ebd5-172">Organizzazioni che richiedono funzionalità di Exchange Server, ma si desidera affidare la distribuzione e manutenzione.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-172">Organizations that need Exchange Server functionality, but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="8ebd5-173">Organizzazioni che richiedono opzioni di supporto personalizzate.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-173">Organizations that need personalized support options.</span></span>
    
- <span data-ttu-id="8ebd5-174">Le soluzioni personalizzate e l'integrazione con le applicazioni personalizzate fornito dal provider.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-174">Customized solutions and integration with custom applications offered by the provider.</span></span>
    
- <span data-ttu-id="8ebd5-175">Soluzioni legacy con i componenti di terze parti che dipendono da hardware e software che non sono supportate da Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-175">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="8ebd5-176">Requisiti relativi alle licenze</span><span class="sxs-lookup"><span data-stu-id="8ebd5-176">License requirements</span></span>

<span data-ttu-id="8ebd5-177">Nella tabella seguente vengono illustrati i requisiti di licenza per ogni opzione di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-177">The following table details the license requirements for each deployment option.</span></span>
  
|<span data-ttu-id="8ebd5-178">**Opzione di distribuzione**</span><span class="sxs-lookup"><span data-stu-id="8ebd5-178">**Deployment option**</span></span>|<span data-ttu-id="8ebd5-179">**Requisiti relativi alle licenze**</span><span class="sxs-lookup"><span data-stu-id="8ebd5-179">**License requirements**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8ebd5-180">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="8ebd5-180">Exchange Online (Office 365)</span></span>  <br/> |<span data-ttu-id="8ebd5-181">Modello di sottoscrizione</span><span class="sxs-lookup"><span data-stu-id="8ebd5-181">Subscription model</span></span>  <br/> |
|<span data-ttu-id="8ebd5-182">Ibrida di Exchange</span><span class="sxs-lookup"><span data-stu-id="8ebd5-182">Exchange Hybrid</span></span>  <br/> | <span data-ttu-id="8ebd5-183">Office 365 - modello di sottoscrizione</span><span class="sxs-lookup"><span data-stu-id="8ebd5-183">Office 365 - Subscription model</span></span> <br/>  <span data-ttu-id="8ebd5-184">Locale - tutte le licenze locali applicano (esaminare le licenze per gli scambi Server in locale)</span><span class="sxs-lookup"><span data-stu-id="8ebd5-184">On-premises - All on-premises licenses apply (review licenses for Exchanges Server on-premises)</span></span> <br/>  <span data-ttu-id="8ebd5-185">Licenza server ibrido \*</span><span class="sxs-lookup"><span data-stu-id="8ebd5-185">Hybrid server license\*</span></span> <br/> |
|<span data-ttu-id="8ebd5-186">Server di Exchange in locale</span><span class="sxs-lookup"><span data-stu-id="8ebd5-186">Exchange Server on-premises</span></span>  <br/> | <span data-ttu-id="8ebd5-187">Sistema operativo del server</span><span class="sxs-lookup"><span data-stu-id="8ebd5-187">Server Operating System</span></span> <br/>  <span data-ttu-id="8ebd5-188">Licenza Server di Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="8ebd5-188">Exchange 2013 Server License</span></span> <br/>  <span data-ttu-id="8ebd5-189">Licenza di accesso Client di Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="8ebd5-189">Exchange 2013 Client Access License</span></span> <br/> |
|<span data-ttu-id="8ebd5-190">Exchange ospitata dal provider</span><span class="sxs-lookup"><span data-stu-id="8ebd5-190">Provider-Hosted Exchange</span></span>  <br/> |<span data-ttu-id="8ebd5-191">I costi basati sul contratto con il provider</span><span class="sxs-lookup"><span data-stu-id="8ebd5-191">Costs are based on the agreement with the provider</span></span>  <br/> |
   
### <a name="architecture-tasks"></a><span data-ttu-id="8ebd5-192">Attività di architettura</span><span class="sxs-lookup"><span data-stu-id="8ebd5-192">Architecture tasks</span></span>

<span data-ttu-id="8ebd5-193">In questa sezione sono elencate le attività dell'architettura per ogni opzione di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-193">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="8ebd5-194">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="8ebd5-194">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="8ebd5-195">Pianificare e progettare la sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-195">Plan and design the directory synchronization.</span></span>
    
- <span data-ttu-id="8ebd5-196">Verificare che la capacità di rete e la connettività attraverso i firewall, server proxy, gateway e sui collegamenti WAN.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-196">Ensure network capacity and connectivity through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="8ebd5-197">Ibrida di Exchange</span><span class="sxs-lookup"><span data-stu-id="8ebd5-197">Exchange Hybrid</span></span>

<span data-ttu-id="8ebd5-198">Oltre alle attività di architettura per gli ambienti di Office 365 e locali:</span><span class="sxs-lookup"><span data-stu-id="8ebd5-198">In addition to the architecture tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="8ebd5-199">Decidere se fornire un single sign-sull'esperienza.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-199">Decide whether to provide a single-sign on experience.</span></span>
    
- <span data-ttu-id="8ebd5-200">Decidere se instradare la posta Internet in ingresso tramite un'organizzazione locale oppure tramite Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-200">Decide whether to route inbound Internet mail through an on-premises organization or through Exchange Online Protection.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="8ebd5-201">Server di Exchange in locale</span><span class="sxs-lookup"><span data-stu-id="8ebd5-201">Exchange Server on-premises</span></span>

- <span data-ttu-id="8ebd5-202">Progettare la topologia di Exchange.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-202">Design the Exchange topology.</span></span>
    
- <span data-ttu-id="8ebd5-203">Pianificazione della capacità per l'hardware server.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-203">Plan the capacity for server hardware.</span></span>
    
- <span data-ttu-id="8ebd5-204">Progettare la topologia di routing dei messaggi.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-204">Design the message routing topology.</span></span>
    
- <span data-ttu-id="8ebd5-205">Progettare il bilanciamento del carico per il server Accesso Client.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-205">Design load balancing for Client Access servers.</span></span>
    
- <span data-ttu-id="8ebd5-206">Pianificare la disponibilità elevata utilizzando gruppi di disponibilità del database.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-206">Plan for high availability using database availability groups.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="8ebd5-207">Exchange ospitata dal provider</span><span class="sxs-lookup"><span data-stu-id="8ebd5-207">Provider-Hosted Exchange</span></span>

<span data-ttu-id="8ebd5-208">Verificare che la capacità di rete e la disponibilità attraverso i firewall, server proxy, gateway e sui collegamenti WAN sono disponibili per il provider.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-208">Ensure that the network capacity and availability through firewalls, proxy servers, gateways, and across WAN links are available to your provider.</span></span>
  
### <a name="it-pro-responsibilities"></a><span data-ttu-id="8ebd5-209">Responsabilità di professionisti IT</span><span class="sxs-lookup"><span data-stu-id="8ebd5-209">IT Pro responsibilities</span></span>

<span data-ttu-id="8ebd5-210">In questa sezione sono elencate le responsabilità per professionisti IT per ogni opzione di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-210">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="8ebd5-211">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="8ebd5-211">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="8ebd5-212">Implementare il piano di sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-212">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="8ebd5-213">Pianificare e implementare i record DNS interni ed esterni e il routing.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-213">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="8ebd5-214">Configurare il server proxy o del firewall per l'indirizzo IP di Office 365 e requisiti per gli URL.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-214">Configure the proxy server or firewall for the Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="8ebd5-215">Amministrare gli account utente e le impostazioni di Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-215">Administer the user accounts and the Exchange Online settings.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="8ebd5-216">Ibrida di Exchange</span><span class="sxs-lookup"><span data-stu-id="8ebd5-216">Exchange Hybrid</span></span>

<span data-ttu-id="8ebd5-217">Oltre alle responsabilità per professionisti IT per gli ambienti di Office 365 e locali:</span><span class="sxs-lookup"><span data-stu-id="8ebd5-217">In addition to the IT Pro responsibilities for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="8ebd5-218">Configurare Active Directory Federation Services (ADFS) per single sign-in (se necessario).</span><span class="sxs-lookup"><span data-stu-id="8ebd5-218">Configure Active Directory Federation Services (AD FS) for single-sign on (if desired).</span></span>
    
- <span data-ttu-id="8ebd5-219">Configurare i certificati di Exchange per le comunicazioni protette tra i server Exchange 2013 e Office 365.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-219">Configure Exchange certificates for secure communications between Exchange 2013 servers and Office 365.</span></span>
    
- <span data-ttu-id="8ebd5-220">Configurare i record DNS per il percorso della posta Internet in ingresso.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-220">Configure DNS records for the desired inbound Internet mail path.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="8ebd5-221">Server di Exchange in locale</span><span class="sxs-lookup"><span data-stu-id="8ebd5-221">Exchange Server on-premises</span></span>

- <span data-ttu-id="8ebd5-222">Configurare i certificati necessari per i servizi Exchange.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-222">Configure the necessary certificates for Exchange services.</span></span>
    
- <span data-ttu-id="8ebd5-223">I server di provisioning.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-223">Provision the servers.</span></span>
    
- <span data-ttu-id="8ebd5-224">Implementare la topologia di routing dei messaggi di Exchange.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-224">Implement the Exchange message routing topology.</span></span>
    
- <span data-ttu-id="8ebd5-225">Implementazione di gruppi di disponibilità del database.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-225">Implement database availability groups.</span></span>
    
- <span data-ttu-id="8ebd5-226">Aggiornamento e la gestione di server di Exchange.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-226">Update and maintain Exchange servers.</span></span>
    
- <span data-ttu-id="8ebd5-227">A seconda dell'utilizzo, aggiungere o rimuovere i server in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-227">Depending on utilization, add or remove servers as needed.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="8ebd5-228">Exchange ospitata dal provider</span><span class="sxs-lookup"><span data-stu-id="8ebd5-228">Provider-Hosted Exchange</span></span>

<span data-ttu-id="8ebd5-229">Responsabilità del provider includono:</span><span class="sxs-lookup"><span data-stu-id="8ebd5-229">The provider's responsibilities include:</span></span>
  
- <span data-ttu-id="8ebd5-230">Manutenzione del sistema e il servizio.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-230">System and service maintenance.</span></span>
    
- <span data-ttu-id="8ebd5-231">Caratteristica implementazioni.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-231">Feature rollouts.</span></span>
    
- <span data-ttu-id="8ebd5-232">Ripristino di emergenza e la protezione dei dati.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-232">Data protection and disaster recovery.</span></span>
    
<span data-ttu-id="8ebd5-233">Responsabilità del personale IT dell'organizzazione include la creazione e gestione degli account utente.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-233">The IT staff's responsibilities in your organization include creating and managing user accounts.</span></span>
  
#### <a name="more-information"></a><span data-ttu-id="8ebd5-234">Ulteriori informazioni</span><span class="sxs-lookup"><span data-stu-id="8ebd5-234">More information</span></span>

<span data-ttu-id="8ebd5-235">Per ulteriori informazioni su Exchange Online (Office 365), vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="8ebd5-235">To learn more about Exchange Online (Office 365), see the following:</span></span>
  
- [<span data-ttu-id="8ebd5-236">Descrizione servizio Exchange Online</span><span class="sxs-lookup"><span data-stu-id="8ebd5-236">Exchange Online service description</span></span>](https://aka.ms/EXOSD)
    
- [<span data-ttu-id="8ebd5-237">Documentazione di Exchange Online su TechNet</span><span class="sxs-lookup"><span data-stu-id="8ebd5-237">Exchange Online library on TechNet</span></span>](https://aka.ms/EXOTN)
    
- [<span data-ttu-id="8ebd5-238">Portale di Exchange Online</span><span class="sxs-lookup"><span data-stu-id="8ebd5-238">Exchange Online portal</span></span>](https://aka.ms/EXO)
    
<span data-ttu-id="8ebd5-239">Per ulteriori informazioni sull'ambiente ibrido di Exchange, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="8ebd5-239">To learn more about Exchange Hybrid, see the following:</span></span>
  
- <span data-ttu-id="8ebd5-p104">[Distribuzioni ibride di Exchange 2013](https://aka.ms/ExchangeHybrid). Si noti che la licenza server ibrido è solo necessario per i seguenti scenari: organizzazione di Exchange 2010 con server ibrido Exchange 2013 e l'organizzazione di Exchange 2007 con server ibridi Exchange 2010 o Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-p104">[Exchange 2013 hybrid deployments](https://aka.ms/ExchangeHybrid). You should note that the Hybrid server license is only required for the following scenarios: Exchange 2010 organization with Exchange 2013 hybrid server and Exchange 2007 organization with Exchange 2013 or Exchange 2010 hybrid server.</span></span>
    
- [<span data-ttu-id="8ebd5-242">Accedi a Office 365</span><span class="sxs-lookup"><span data-stu-id="8ebd5-242">Office 365 Sign in</span></span>](https://aka.ms/HybridKey)
    
<span data-ttu-id="8ebd5-243">Per ulteriori informazioni sui Server Exchange locale, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="8ebd5-243">To learn more about Exchange Server on-premises, see the following:</span></span>
  
- [<span data-ttu-id="8ebd5-244">Documentazione di Exchange Server 2013 in TechNet</span><span class="sxs-lookup"><span data-stu-id="8ebd5-244">Exchange Server 2013 library on TechNet</span></span>](https://aka.ms/Ex2013TN)
    
- [<span data-ttu-id="8ebd5-245">Portale di Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="8ebd5-245">Exchange Server 2013 portal</span></span>](https://aka.ms/Exchange2013)
    
- [<span data-ttu-id="8ebd5-246">Architettura di Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="8ebd5-246">Exchange Server 2013 architecture</span></span>](https://aka.ms/Ex2013SP1ArchPoster)
    
<span data-ttu-id="8ebd5-247">Per ulteriori informazioni su Exchange Provider-Hosted, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="8ebd5-247">To learn more about Provider-Hosted Exchange, see the following:</span></span>
  
[<span data-ttu-id="8ebd5-248">Linee guida e le soluzioni di hosting e multi-tenancy di Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="8ebd5-248">Exchange Server 2013 hosting and multi-tenancy solutions and guidance</span></span>](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a><span data-ttu-id="8ebd5-249">Descrizioni di tre le caratteristiche nuove o aggiornate in Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="8ebd5-249">Descriptions of three new or updated features in Exchange 2013</span></span>

### <a name="exchange-online-protection"></a><span data-ttu-id="8ebd5-250">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="8ebd5-250">Exchange Online Protection</span></span>

<span data-ttu-id="8ebd5-p105">Exchange Online Protection (EOP) è assicurata la protezione da posta indesiderata e antimalware per qualsiasi distribuzione fornendo un livello di funzionalità di protezione che vengono distribuiti in una rete globale di data center. In questo modo è possibile semplificare la gestione dell'ambiente di messaggistica. EOP è incluso in sottoscrizioni a Exchange Online, ma è possibile utilizzare anche per le distribuzioni ibride e locali.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-p105">Exchange Online Protection (EOP) provides anti-spam and anti-malware protection for any deployment by providing a layer of protection features that are deployed across a global network of data centers. This helps you to simplify the management of your messaging environments. EOP is included in Exchange Online subscriptions, but you can also leverage it for hybrid and on-premises deployments.</span></span>
  
<span data-ttu-id="8ebd5-254">I diagrammi di accompagnamento mostrano le distribuzioni di Exchange Online, Exchange Hybrid e di Exchange in locale che include il livello di EOP in rete globale.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-254">The accompanying diagrams show deployments for Exchange Online, Exchange Hybrid, and Exchange on-premises that include the EOP layer in the global network.</span></span>
  
### <a name="exchange-server-deployment-assistant"></a><span data-ttu-id="8ebd5-255">Assistente per la distribuzione di Exchange Server</span><span class="sxs-lookup"><span data-stu-id="8ebd5-255">Exchange Server Deployment Assistant</span></span>

<span data-ttu-id="8ebd5-p106">Exchange Server Deployment Assistant è uno strumento basato su web che richiede alcune domande sull'ambiente corrente e quindi genera un elenco di controllo dettagliata personalizzato per facilitare la distribuzione di Exchange Server per diversi tipi di scenario. Se esegue la migrazione da una versione precedente di Exchange a Exchange 2013, eseguire la migrazione a Exchange Online o pianificando l'infrastruttura ibrida, Exchange Server Deployment Assistant consente di creare un elenco di controllo di distribuzione personalizzata per lo scenario.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-p106">The Exchange Server Deployment Assistant is a web-based tool that asks you a few questions about your current environment, and then generates a custom step-by-step checklist to help you deploy Exchange Server for different types of scenarios. Whether you are migrating from a previous version of Exchange to Exchange 2013, migrating to Exchange Online, or planning a hybrid infrastructure, the Exchange Server Deployment Assistant creates a customized deployment checklist for your scenario.</span></span>
  
<span data-ttu-id="8ebd5-258">Schermata relativa che mostra un elenco di controllo di esempio creato con Exchange Server Deployment Assistant.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-258">The accompanying screenshot shows an example checklist that was created using the Exchange Server Deployment Assistant.</span></span>
  
### <a name="integration-with-lync-and-sharepoint"></a><span data-ttu-id="8ebd5-259">Integrazione con Lync e SharePoint</span><span class="sxs-lookup"><span data-stu-id="8ebd5-259">Integration with Lync and SharePoint</span></span>

<span data-ttu-id="8ebd5-p107">Exchange Server 2013 sono incluse numerose caratteristiche che si integrano con Lync Server 2013 e SharePoint Server 2013. Insieme, questi prodotti offrono una vasta gamma di funzionalità e migliorare la collaborazione all'interno dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-p107">Exchange Server 2013 includes many features that integrate with Lync Server 2013 and SharePoint Server 2013. Together, these products offer a rich suite of features and improve collaboration across your organization.</span></span> 
  
<span data-ttu-id="8ebd5-262">Un diagramma di accompagnamento vengono visualizzati il poster di autenticazione da Server a Server e include un collegamento al poster.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-262">An accompanying diagram shows the Server-to-Server Authentication poster and includes a link to the poster.</span></span> 
  
- <span data-ttu-id="8ebd5-263">L'archiviazione, conservazione ed eDiscovery</span><span class="sxs-lookup"><span data-stu-id="8ebd5-263">Archiving, hold and eDiscovery</span></span>
    
- <span data-ttu-id="8ebd5-264">Cassette postali del sito</span><span class="sxs-lookup"><span data-stu-id="8ebd5-264">Site mailboxes</span></span>
    
- <span data-ttu-id="8ebd5-265">Archivio unico dei contatti</span><span class="sxs-lookup"><span data-stu-id="8ebd5-265">Unified contact store</span></span>
    
- <span data-ttu-id="8ebd5-266">Foto dell'utente ad alta risoluzione</span><span class="sxs-lookup"><span data-stu-id="8ebd5-266">High-resolution user photos</span></span>
    
- <span data-ttu-id="8ebd5-267">Presenza di Lync in Outlook e Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="8ebd5-267">Lync presence in Outlook and Outlook Web App</span></span>
    
- <span data-ttu-id="8ebd5-268">Autenticazione tra server</span><span class="sxs-lookup"><span data-stu-id="8ebd5-268">Server-to-server authentication</span></span>
    
- <span data-ttu-id="8ebd5-269">Segreteria telefonica</span><span class="sxs-lookup"><span data-stu-id="8ebd5-269">Voicemail</span></span>
    
- <span data-ttu-id="8ebd5-270">Registrazioni delle riunioni</span><span class="sxs-lookup"><span data-stu-id="8ebd5-270">Meeting recordings</span></span>
    
- <span data-ttu-id="8ebd5-271">Sincronizzazione delle attività di Exchange</span><span class="sxs-lookup"><span data-stu-id="8ebd5-271">Exchange task synchronization</span></span>
    
<span data-ttu-id="8ebd5-272">Un diagramma di accompagnamento vengono visualizzati il poster dell'architettura di Exchange Server 2013 SP1 e include un collegamento al poster.</span><span class="sxs-lookup"><span data-stu-id="8ebd5-272">An accompanying diagram shows the Exchange Server 2013 SP1 Architecture poster and includes a link to the poster.</span></span>
  

