---
title: Diagramma accessibile - opzioni della piattaforma Microsoft Lync 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: In questo articolo è una versione testo accessibile del diagramma denominato opzioni della piattaforma Microsoft Lync 2013, disponibile all'indirizzo Technical Diagrams.
ms.openlocfilehash: 4a660df4bfacad2a00f5d9fbb5e1b668840e3b9f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
ms.locfileid: "17504089"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a><span data-ttu-id="46ebf-103">Diagramma accessibile - opzioni della piattaforma Microsoft Lync 2013</span><span class="sxs-lookup"><span data-stu-id="46ebf-103">Accessible diagram - Microsoft Lync 2013 Platform Options</span></span>

<span data-ttu-id="46ebf-104">**Riepilogo:** In questo articolo è una versione testo accessibile del diagramma denominato opzioni della piattaforma Microsoft Lync 2013, disponibile all'indirizzo [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="46ebf-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Lync 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="46ebf-105">Questo poster viene descritto cosa decisori aziendali (hanno) e progettisti devono essere a conoscenza Lync Online (Office 365) e le distribuzioni di Lync Server e sono incluse:</span><span class="sxs-lookup"><span data-stu-id="46ebf-105">This poster describes what business decision makers (BDMs) and architects need to know about Lync Online (Office 365) and Lync Server deployments and includes:</span></span>
  
- <span data-ttu-id="46ebf-106">Un confronto tra quattro diverse opzioni di distribuzione: Lync Online (Office 365), Lync Online/Server ibrido, Lync Server e Provider-Hosted Lync Server.</span><span class="sxs-lookup"><span data-stu-id="46ebf-106">A comparison of four different deployment options: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server, and Provider-Hosted Lync Server.</span></span> 
    
- <span data-ttu-id="46ebf-107">Due scenari di esempio per la distribuzione di Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="46ebf-107">Two example scenarios for deploying Lync 2013.</span></span>
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a><span data-ttu-id="46ebf-108">Confronto tra quattro diverse distribuzioni per la piattaforma Lync 2013</span><span class="sxs-lookup"><span data-stu-id="46ebf-108">Comparison of four different deployments for the Lync 2013 platform</span></span>

<span data-ttu-id="46ebf-109">Il confronto vengono fornite informazioni su ogni opzione di distribuzione nelle aree seguenti:</span><span class="sxs-lookup"><span data-stu-id="46ebf-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="46ebf-110">Panoramica delle funzionalità di distribuzione diversi</span><span class="sxs-lookup"><span data-stu-id="46ebf-110">An overview of the different deployment features</span></span>
    
- <span data-ttu-id="46ebf-111">Vantaggi dell'implementazione di ogni opzione di distribuzione</span><span class="sxs-lookup"><span data-stu-id="46ebf-111">Benefits of implementing each deployment option</span></span>
    
- <span data-ttu-id="46ebf-112">Requisiti relativi alle licenze</span><span class="sxs-lookup"><span data-stu-id="46ebf-112">Licensing requirements</span></span>
    
- <span data-ttu-id="46ebf-113">Richiesta attività dell'architettura</span><span class="sxs-lookup"><span data-stu-id="46ebf-113">Required architectural tasks</span></span>
    
- <span data-ttu-id="46ebf-114">Responsabilità di professionisti IT per l'implementazione di ogni opzione di distribuzione</span><span class="sxs-lookup"><span data-stu-id="46ebf-114">IT Pro responsibilities for implementing each deployment option</span></span>
    
### <a name="overview"></a><span data-ttu-id="46ebf-115">Panoramica</span><span class="sxs-lookup"><span data-stu-id="46ebf-115">Overview</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="46ebf-116">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="46ebf-116">Lync Online (Office 365)</span></span>

<span data-ttu-id="46ebf-117">Maggiore efficienza e ottimizzare per costo con Office 365 plans multi-tenant.</span><span class="sxs-lookup"><span data-stu-id="46ebf-117">You gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span>
  
<span data-ttu-id="46ebf-118">Nella figura relativa Mostra Lync Online con un tenant di Azure Active Directory, che consente di sincronizzare i nomi degli account e password tra l'ambiente di servizi di dominio Active Directory (AD DS) locali e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="46ebf-118">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="46ebf-119">Descrizione delle funzionalità e caratteristiche:</span><span class="sxs-lookup"><span data-stu-id="46ebf-119">Description of features and functionality:</span></span>
  
- <span data-ttu-id="46ebf-120">Software come servizio (SaaS).</span><span class="sxs-lookup"><span data-stu-id="46ebf-120">Software as a Service (SaaS).</span></span>
    
- <span data-ttu-id="46ebf-121">RTF funzionalità set che siano sempre aggiornati.</span><span class="sxs-lookup"><span data-stu-id="46ebf-121">Rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="46ebf-122">Include un tenant di Azure Active Directory per gli account in linea, che può essere utilizzato con altre applicazioni.</span><span class="sxs-lookup"><span data-stu-id="46ebf-122">Includes an Azure Active Directory tenant for online accounts, which can be used with other applications.</span></span> 
    
- <span data-ttu-id="46ebf-123">Integrazione di directory include la sincronizzazione dei nomi di account e password tra l'ambiente di servizi di dominio Active Directory (AD DS) locali e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="46ebf-123">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
    
- <span data-ttu-id="46ebf-124">Se il single sign-on (SSO) è un requisito, è necessario implementare Active Directory Federation Services (ADFS).</span><span class="sxs-lookup"><span data-stu-id="46ebf-124">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) must be implemented.</span></span> 
    
- <span data-ttu-id="46ebf-125">La comunicazione client tramite Internet è crittografata e autenticata.</span><span class="sxs-lookup"><span data-stu-id="46ebf-125">Client communication over the Internet is encrypted and authenticated.</span></span>
    
- <span data-ttu-id="46ebf-126">Apparecchiatura, telefono legacy pubblica commutata (PSTN) telephone network, connettività è disponibile attraverso i provider di terze parti.</span><span class="sxs-lookup"><span data-stu-id="46ebf-126">Legacy phone equipment, public switched telephone network (PSTN), connectivity is available through third-party providers.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="46ebf-127">Lync Online/Server ibrido (dominio diviso)</span><span class="sxs-lookup"><span data-stu-id="46ebf-127">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="46ebf-128">È possibile combinare i vantaggi di Office 365 per una distribuzione locale di Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="46ebf-128">You can combine the benefits of Office 365 with an on-premises deployment of Lync 2013.</span></span>
  
<span data-ttu-id="46ebf-p101">Il diagramma accompagnamento Mostra Office 365 con Lync Online in cui alcuni utenti sono in locale e alcuni utenti ospitati in linea. Viene visualizzato anche un Edge Server distribuiti in locale.</span><span class="sxs-lookup"><span data-stu-id="46ebf-p101">The accompanying diagram shows Office 365 with Lync Online where some users are homed on-premises and some users are homed online. An Edge Server that is deployed on-premises is also shown.</span></span>
  
<span data-ttu-id="46ebf-131">Descrizione delle funzionalità e caratteristiche:</span><span class="sxs-lookup"><span data-stu-id="46ebf-131">Description of features and functionality:</span></span>
  
- <span data-ttu-id="46ebf-132">Alcuni utenti sono ospitati in locale e alcuni utenti ospitati in linea, ma gli utenti hanno lo stesso dominio SIP (ad esempio contoso.com).</span><span class="sxs-lookup"><span data-stu-id="46ebf-132">Some users are homed on premises and some users are homed online, but the users share the same SIP domain (such as contoso.com).</span></span>
    
- <span data-ttu-id="46ebf-133">Infrastruttura esistente Lync Server 2013, incluse le connessioni alla rete PSTN.</span><span class="sxs-lookup"><span data-stu-id="46ebf-133">Leverage your existing Lync Server 2013 infrastructure, including the connections to the PSTN.</span></span>
    
- <span data-ttu-id="46ebf-134">Aggiungere nuovi utenti di Lync Online con facilità quando non richiedono PSTN.</span><span class="sxs-lookup"><span data-stu-id="46ebf-134">Add new Lync Online users easily when they do not require PSTN.</span></span>
    
- <span data-ttu-id="46ebf-135">Eseguire la migrazione da Lync in locale con Lync Online nel tempo, al calendario.</span><span class="sxs-lookup"><span data-stu-id="46ebf-135">Migrate from Lync on-premises to Lync Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="46ebf-136">Integrazione con altre applicazioni di Office 365, inclusi Exchange Online e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="46ebf-136">Integrate with other Office 365 applications, including Exchange Online and SharePoint Online.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="46ebf-137">Lync Server</span><span class="sxs-lookup"><span data-stu-id="46ebf-137">Lync Server</span></span>

<span data-ttu-id="46ebf-p102">In questa distribuzione si è proprietari tutto il contenuto. Il diagramma accompagnamento Mostra un'infrastruttura di Lync Server con un ambiente di servizi di dominio Active Directory (AD DS) locale in cui gli utenti sono in locale.</span><span class="sxs-lookup"><span data-stu-id="46ebf-p102">In this deployment, you own everything. The accompanying diagram shows a Lync Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="46ebf-140">Descrizione delle funzionalità e caratteristiche:</span><span class="sxs-lookup"><span data-stu-id="46ebf-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="46ebf-141">Pianificazione della capacità e dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="46ebf-141">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="46ebf-142">Acquisizione di server e il programma di installazione.</span><span class="sxs-lookup"><span data-stu-id="46ebf-142">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="46ebf-143">Distribuzione.</span><span class="sxs-lookup"><span data-stu-id="46ebf-143">Deployment.</span></span>
    
- <span data-ttu-id="46ebf-144">Scalabilità orizzontale, applicazione di patch e operazioni.</span><span class="sxs-lookup"><span data-stu-id="46ebf-144">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="46ebf-145">Backup dei dati.</span><span class="sxs-lookup"><span data-stu-id="46ebf-145">Backing up data.</span></span>
    
- <span data-ttu-id="46ebf-146">Gestione di failover e ripristino di emergenza.</span><span class="sxs-lookup"><span data-stu-id="46ebf-146">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="46ebf-147">Connessione alla rete PSTN dell'infrastruttura di Lync Server 2013.</span><span class="sxs-lookup"><span data-stu-id="46ebf-147">Connecting your Lync Server 2013 infrastructure to the PSTN.</span></span>
    
- <span data-ttu-id="46ebf-148">Integrazione con l'apparecchio telefonico esistente, ad esempio lo scambio di centralino (PBX).</span><span class="sxs-lookup"><span data-stu-id="46ebf-148">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="46ebf-149">Ospitate da provider Lync Server</span><span class="sxs-lookup"><span data-stu-id="46ebf-149">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="46ebf-p103">In questa distribuzione, il provider è proprietario tutto il contenuto. Il diagramma accompagnamento Mostra rete del provider, inclusi i server e apparecchiature con una connessione a un ambiente locale.</span><span class="sxs-lookup"><span data-stu-id="46ebf-p103">In this deployment, your provider owns everything. The accompanying diagram shows a provider's network including their servers and equipment with a connection to an on-premises environment.</span></span>
  
<span data-ttu-id="46ebf-152">Descrizione delle funzionalità e caratteristiche:</span><span class="sxs-lookup"><span data-stu-id="46ebf-152">Description of features and functionality:</span></span>
  
- <span data-ttu-id="46ebf-153">Pianificazione della capacità e dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="46ebf-153">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="46ebf-154">Acquisizione di server e il programma di installazione.</span><span class="sxs-lookup"><span data-stu-id="46ebf-154">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="46ebf-155">Distribuzione.</span><span class="sxs-lookup"><span data-stu-id="46ebf-155">Deployment.</span></span>
    
- <span data-ttu-id="46ebf-156">Scalabilità orizzontale, applicazione di patch e operazioni.</span><span class="sxs-lookup"><span data-stu-id="46ebf-156">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="46ebf-157">Backup dei dati.</span><span class="sxs-lookup"><span data-stu-id="46ebf-157">Backing up data.</span></span>
    
- <span data-ttu-id="46ebf-158">Gestione di failover e ripristino di emergenza.</span><span class="sxs-lookup"><span data-stu-id="46ebf-158">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="46ebf-159">Integrazione con l'apparecchio telefonico esistente, ad esempio lo scambio di centralino (PBX).</span><span class="sxs-lookup"><span data-stu-id="46ebf-159">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
- <span data-ttu-id="46ebf-160">Inoltre, il provider può:</span><span class="sxs-lookup"><span data-stu-id="46ebf-160">In addition, the provider can:</span></span>
    
  - <span data-ttu-id="46ebf-161">Installare i server e apparecchiature la propria rete con una connessione ai propri locali (linea continua).</span><span class="sxs-lookup"><span data-stu-id="46ebf-161">Install their servers and equipment in their own network with a connection to your premises (solid line).</span></span>
    
  - <span data-ttu-id="46ebf-162">Installare i server il locale (linea tratteggiata).</span><span class="sxs-lookup"><span data-stu-id="46ebf-162">Install their servers on your premises (dotted line).</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="46ebf-163">Vantaggi dell'implementazione di ogni opzione di distribuzione</span><span class="sxs-lookup"><span data-stu-id="46ebf-163">Benefits of implementing each deployment option</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="46ebf-164">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="46ebf-164">Lync Online (Office 365)</span></span>

- <span data-ttu-id="46ebf-165">Nessun carico operativo del server locale o software del server.</span><span class="sxs-lookup"><span data-stu-id="46ebf-165">No operational burden of on-premises servers or server software.</span></span>
    
- <span data-ttu-id="46ebf-166">Funzionalità di comunicazione di Lync Server 2013 come un servizio basato su cloud.</span><span class="sxs-lookup"><span data-stu-id="46ebf-166">Communication capabilities of Lync Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="46ebf-167">Presenza di Lync, messaggistica immediata, audio e video di chiamata avanzate riunioni in linea e funzionalità di conferenza web estesa.</span><span class="sxs-lookup"><span data-stu-id="46ebf-167">Lync presence, instant messaging, audio and video calling, rich online meetings, and extensive web conferencing capabilities.</span></span>
    
- <span data-ttu-id="46ebf-168">Utilizzato con le organizzazioni su più aree geografiche o dipendenti principalmente per dispositivi mobili.</span><span class="sxs-lookup"><span data-stu-id="46ebf-168">Used with geographically-dispersed organizations or with primarily mobile employees.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="46ebf-169">Lync Online/Server ibrido (dominio diviso)</span><span class="sxs-lookup"><span data-stu-id="46ebf-169">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="46ebf-170">Utilizzare Lync Online per utenti remoti e l'integrazione con i partner commerciali.</span><span class="sxs-lookup"><span data-stu-id="46ebf-170">Use Lync Online for remote users and integration with business partners.</span></span>
    
- <span data-ttu-id="46ebf-171">Effettuare una migrazione da Lync in locale con Lync Online.</span><span class="sxs-lookup"><span data-stu-id="46ebf-171">Facilitate a migration from Lync on-premises to Lync Online.</span></span>
    
- <span data-ttu-id="46ebf-172">Supportare siti remoti senza utilizzare un branch appliance di office.</span><span class="sxs-lookup"><span data-stu-id="46ebf-172">Support remote sites without using a branch office appliance.</span></span>
    
- <span data-ttu-id="46ebf-173">Facilità di aggiunta del supporto di Lync per nuove acquisizioni aziendali.</span><span class="sxs-lookup"><span data-stu-id="46ebf-173">Ease of adding Lync support for new business acquisitions.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="46ebf-174">Lync Server</span><span class="sxs-lookup"><span data-stu-id="46ebf-174">Lync Server</span></span>

- <span data-ttu-id="46ebf-175">Soluzioni basate su cloud privata.</span><span class="sxs-lookup"><span data-stu-id="46ebf-175">Private cloud solutions.</span></span>
    
- <span data-ttu-id="46ebf-176">Soluzioni fortemente personalizzate.</span><span class="sxs-lookup"><span data-stu-id="46ebf-176">Highly customized solutions.</span></span>
    
- <span data-ttu-id="46ebf-177">Soluzioni legacy con i componenti di terze parti che dipendono da hardware e software che non sono supportate da Lync Online.</span><span class="sxs-lookup"><span data-stu-id="46ebf-177">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="46ebf-178">Limitazioni relative alla privacy che impediscono la sincronizzazione degli account di dominio Active Directory con Office 365.</span><span class="sxs-lookup"><span data-stu-id="46ebf-178">Privacy restrictions that prevent synchronization of AD DS accounts with Office 365.</span></span>
    
- <span data-ttu-id="46ebf-179">Organizzazioni che desiderano controllo dell'intera piattaforma e soluzione.</span><span class="sxs-lookup"><span data-stu-id="46ebf-179">Organizations that desire control of the entire platform and solution.</span></span>
    
- <span data-ttu-id="46ebf-180">Sostituzione di PBX con VoIP aziendale di Lync.</span><span class="sxs-lookup"><span data-stu-id="46ebf-180">PBX replacement with Lync Enterprise Voice.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="46ebf-181">Ospitate da provider Lync Server</span><span class="sxs-lookup"><span data-stu-id="46ebf-181">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="46ebf-182">Organizzazioni che desiderano funzionalità di Lync Server ma si desidera affidare la distribuzione e manutenzione.</span><span class="sxs-lookup"><span data-stu-id="46ebf-182">Organizations that want Lync Server functionality but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="46ebf-183">Soluzioni basate su provider.</span><span class="sxs-lookup"><span data-stu-id="46ebf-183">Provider-based solutions.</span></span>
    
- <span data-ttu-id="46ebf-184">Soluzioni fortemente personalizzate.</span><span class="sxs-lookup"><span data-stu-id="46ebf-184">Highly customized solutions.</span></span>
    
- <span data-ttu-id="46ebf-185">Soluzioni legacy con i componenti di terze parti che dipendono da hardware e software che non sono supportate da Lync Online.</span><span class="sxs-lookup"><span data-stu-id="46ebf-185">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="46ebf-186">Sostituzione di PBX con VoIP aziendale di Lync.</span><span class="sxs-lookup"><span data-stu-id="46ebf-186">PBX replacement with Lync Enterprise Voice.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="46ebf-187">Requisiti relativi alle licenze</span><span class="sxs-lookup"><span data-stu-id="46ebf-187">License requirements</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="46ebf-188">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="46ebf-188">Lync Online (Office 365)</span></span>

<span data-ttu-id="46ebf-189">Modello di sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="46ebf-189">Subscription model.</span></span>
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="46ebf-190">Lync Online/Server ibrido (dominio diviso)</span><span class="sxs-lookup"><span data-stu-id="46ebf-190">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="46ebf-p104">Office 365, ovvero Modello di sottoscrizione. Nessuna licenza aggiuntiva necessaria.</span><span class="sxs-lookup"><span data-stu-id="46ebf-p104">Office 365 — Subscription model. No additional licenses needed.</span></span> 
    
- <span data-ttu-id="46ebf-193">Locale, Si applicano tutte le licenze locali.</span><span class="sxs-lookup"><span data-stu-id="46ebf-193">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="lync-server"></a><span data-ttu-id="46ebf-194">Lync Server</span><span class="sxs-lookup"><span data-stu-id="46ebf-194">Lync Server</span></span>

- <span data-ttu-id="46ebf-195">Sistema operativo del server</span><span class="sxs-lookup"><span data-stu-id="46ebf-195">Server Operating System</span></span>
    
- <span data-ttu-id="46ebf-196">SQL Server</span><span class="sxs-lookup"><span data-stu-id="46ebf-196">SQL Server</span></span>
    
- <span data-ttu-id="46ebf-197">Licenza Server di Lync 2013</span><span class="sxs-lookup"><span data-stu-id="46ebf-197">Lync 2013 Server License</span></span>
    
- <span data-ttu-id="46ebf-198">Licenza di accesso Client di Lync 2013</span><span class="sxs-lookup"><span data-stu-id="46ebf-198">Lync 2013 Client Access License</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="46ebf-199">Ospitate da provider Lync Server</span><span class="sxs-lookup"><span data-stu-id="46ebf-199">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="46ebf-200">Costi sono basati sul contratto con provider di soluzioni Lync.</span><span class="sxs-lookup"><span data-stu-id="46ebf-200">Costs are based on the agreement with your Lync solution provider.</span></span>
  
### <a name="architecture-tasks"></a><span data-ttu-id="46ebf-201">Attività di architettura</span><span class="sxs-lookup"><span data-stu-id="46ebf-201">Architecture tasks</span></span>

<span data-ttu-id="46ebf-202">In questa sezione sono elencate le attività dell'architettura per ogni opzione di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="46ebf-202">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="46ebf-203">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="46ebf-203">Lync Online (Office 365)</span></span>

- <span data-ttu-id="46ebf-204">Pianificare e progettare sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="46ebf-204">Plan and design directory synchronization.</span></span>
    
- <span data-ttu-id="46ebf-205">Verificare la capacità di rete e la disponibilità attraverso i firewall, server proxy, gateway e sui collegamenti WAN.</span><span class="sxs-lookup"><span data-stu-id="46ebf-205">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
- <span data-ttu-id="46ebf-206">Ottenere i certificati SSL di terze parti per garantire la sicurezza aziendale per le offerte di servizi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="46ebf-206">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span>
    
- <span data-ttu-id="46ebf-207">Decidere se si desidera connettersi a Office 365 con Internet Protocol versione 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="46ebf-207">Decide if you want to connect to Office 365 with Internet Protocol version 6 (IPv6).</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="46ebf-208">Lync Online/Server ibrido (dominio diviso)</span><span class="sxs-lookup"><span data-stu-id="46ebf-208">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="46ebf-209">Oltre alle attività per gli ambienti di Office 365 e locali:</span><span class="sxs-lookup"><span data-stu-id="46ebf-209">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="46ebf-210">Determinare la quantità integrazione delle funzionalità che si desidera utilizzare con organizzazioni locali e le versioni di Exchange Server e SharePoint online.</span><span class="sxs-lookup"><span data-stu-id="46ebf-210">Determine how much feature integration you want to use with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
- <span data-ttu-id="46ebf-211">Se necessario, determinare quali dispositivi server proxy da utilizzare per le richieste da Office 365.</span><span class="sxs-lookup"><span data-stu-id="46ebf-211">If required, determine which proxy server device will be used for requests from Office 365.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="46ebf-212">Lync Server</span><span class="sxs-lookup"><span data-stu-id="46ebf-212">Lync Server</span></span>

<span data-ttu-id="46ebf-213">Progettare l'ambiente Lync in un ambiente locale esistente:</span><span class="sxs-lookup"><span data-stu-id="46ebf-213">Design the Lync environment in an existing on-premises environment:</span></span>
  
- <span data-ttu-id="46ebf-214">Topologie di Lync per centrali e nelle succursali.</span><span class="sxs-lookup"><span data-stu-id="46ebf-214">Lync topology for central and branch offices.</span></span>
    
- <span data-ttu-id="46ebf-215">Hardware del server, tra cui la virtualizzazione.</span><span class="sxs-lookup"><span data-stu-id="46ebf-215">Server hardware, including virtualization.</span></span>
    
- <span data-ttu-id="46ebf-216">Integrazione con servizi di dominio Active Directory (AD DS) e DNS.</span><span class="sxs-lookup"><span data-stu-id="46ebf-216">Integration with Active Directory Domain Services (AD DS) and DNS.</span></span>
    
- <span data-ttu-id="46ebf-217">Bilanciamento del carico per pool di Lync server.</span><span class="sxs-lookup"><span data-stu-id="46ebf-217">Load balancing for Lync server pools.</span></span>
    
- <span data-ttu-id="46ebf-218">Failover e ripristino di emergenza.</span><span class="sxs-lookup"><span data-stu-id="46ebf-218">Failover and disaster recovery.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="46ebf-219">Ospitate da provider Lync Server</span><span class="sxs-lookup"><span data-stu-id="46ebf-219">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="46ebf-220">Determinare la connessione alla rete del provider di servizi per un'installazione basata su cloud.</span><span class="sxs-lookup"><span data-stu-id="46ebf-220">For a cloud-based installation, determine the connection to the service provider's network.</span></span>
    
- <span data-ttu-id="46ebf-221">Per un'installazione locale, determinare la posizione dei server di Lync Server del provider nella rete.</span><span class="sxs-lookup"><span data-stu-id="46ebf-221">For an on-premises installation, determine the placement of the provider's Lync servers on your network.</span></span>
    
- <span data-ttu-id="46ebf-222">Per entrambi i tipi, determinare l'integrazione con Active Directory e il dispositivo il PBX.</span><span class="sxs-lookup"><span data-stu-id="46ebf-222">For both types, determine the integration with AD DS and your PBX equipment.</span></span>
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="46ebf-223">Responsabilità di professionisti IT</span><span class="sxs-lookup"><span data-stu-id="46ebf-223">IT Pro responsibilities</span></span>

<span data-ttu-id="46ebf-224">In questa sezione sono elencate le responsabilità per professionisti IT per ogni opzione di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="46ebf-224">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="46ebf-225">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="46ebf-225">Lync Online (Office 365)</span></span>

<span data-ttu-id="46ebf-226">Distribuire e gestire Lync Online (Office 365):</span><span class="sxs-lookup"><span data-stu-id="46ebf-226">Deploy and manage Lync Online (Office 365):</span></span>
  
- <span data-ttu-id="46ebf-227">Implementare il piano di sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="46ebf-227">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="46ebf-228">Pianificare e implementare i record DNS interni ed esterni e il routing.</span><span class="sxs-lookup"><span data-stu-id="46ebf-228">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="46ebf-229">Configurare il proxy o del firewall per l'indirizzo IP di Office 365 e requisiti per gli URL.</span><span class="sxs-lookup"><span data-stu-id="46ebf-229">Configure your proxy or firewall for Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="46ebf-230">Gestire gli account utente e le impostazioni di Lync Online.</span><span class="sxs-lookup"><span data-stu-id="46ebf-230">Administer user accounts and Lync Online settings.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="46ebf-231">Lync Online/Server ibrido (dominio diviso)</span><span class="sxs-lookup"><span data-stu-id="46ebf-231">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="46ebf-232">Oltre alle attività per gli ambienti di Office 365 e locali:</span><span class="sxs-lookup"><span data-stu-id="46ebf-232">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="46ebf-233">Configurare il dispositivo di server proxy, se necessario.</span><span class="sxs-lookup"><span data-stu-id="46ebf-233">Configure the proxy server device, if required.</span></span>
    
- <span data-ttu-id="46ebf-234">Configurare l'integrazione delle funzionalità con le versioni di Exchange Server e SharePoint online e locale.</span><span class="sxs-lookup"><span data-stu-id="46ebf-234">Configure the integration of features with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="46ebf-235">Lync Server</span><span class="sxs-lookup"><span data-stu-id="46ebf-235">Lync Server</span></span>

<span data-ttu-id="46ebf-236">Distribuzione e la gestione di Lync Server in un ambiente locale:</span><span class="sxs-lookup"><span data-stu-id="46ebf-236">Deploy and manage Lync Server in an on-premises environment:</span></span>
  
- <span data-ttu-id="46ebf-237">I server di provisioning.</span><span class="sxs-lookup"><span data-stu-id="46ebf-237">Provision the servers.</span></span>
    
- <span data-ttu-id="46ebf-238">Distribuire la topologia di Lync.</span><span class="sxs-lookup"><span data-stu-id="46ebf-238">Deploy the Lync topology.</span></span>
    
- <span data-ttu-id="46ebf-239">Aggiornare i server Lync.</span><span class="sxs-lookup"><span data-stu-id="46ebf-239">Update Lync servers.</span></span>
    
- <span data-ttu-id="46ebf-240">Aggiungere o rimuovere i server della topologia in base alle esigenze basato sull'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="46ebf-240">Add or remove topology servers as needed based on utilization.</span></span>
    
- <span data-ttu-id="46ebf-241">Implementare l'ambiente di ripristino di emergenza e failover.</span><span class="sxs-lookup"><span data-stu-id="46ebf-241">Implement the failover and disaster recovery environment.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="46ebf-242">Ospitate da provider Lync Server</span><span class="sxs-lookup"><span data-stu-id="46ebf-242">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="46ebf-243">È possibile utilizzare con il provider di:</span><span class="sxs-lookup"><span data-stu-id="46ebf-243">Work with the provider to:</span></span>
  
- <span data-ttu-id="46ebf-244">Integrazione di Lync Server nella rete.</span><span class="sxs-lookup"><span data-stu-id="46ebf-244">Integrate Lync Server into your network.</span></span>
    
- <span data-ttu-id="46ebf-245">Integrazione di Lync Server con altri prodotti Microsoft o soluzioni personalizzate.</span><span class="sxs-lookup"><span data-stu-id="46ebf-245">Integrate Lync Server with other Microsoft products or custom solutions.</span></span>
    
- <span data-ttu-id="46ebf-246">Monitoraggio della conformità con provider contratto di servizio (SLA).</span><span class="sxs-lookup"><span data-stu-id="46ebf-246">Monitor adherence with provider service level agreement (SLA).</span></span>
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a><span data-ttu-id="46ebf-247">Due scenari di esempio per la distribuzione di Lync 2013</span><span class="sxs-lookup"><span data-stu-id="46ebf-247">Two example scenarios for deploying Lync 2013</span></span>

### <a name="directory-synchronization-components-in-microsoft-azure"></a><span data-ttu-id="46ebf-248">Componenti della sincronizzazione della directory in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="46ebf-248">Directory Synchronization components in Microsoft Azure</span></span>

<span data-ttu-id="46ebf-249">Distribuzione di Office 365 componenti di sincronizzazione della directory in Azure è superiore a causa la possibilità di distribuire le macchine virtuali su richiesta.</span><span class="sxs-lookup"><span data-stu-id="46ebf-249">Deploying Office 365 directory synchronization components in Azure is faster due to the ability to deploy virtual machines on-demand.</span></span>
  
<span data-ttu-id="46ebf-250">Nella figura relativa Mostra Lync Online con un tenant di Azure Active Directory, che consente di sincronizzare i nomi degli account e password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="46ebf-250">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span>
  
 <span data-ttu-id="46ebf-p105">**Solo i server di sincronizzazione della directory**. Invece di distribuire il server di sincronizzazione directory a 64 bit nell'ambiente locale, eseguire il provisioning una macchina virtuale in Azure tramite Internet.</span><span class="sxs-lookup"><span data-stu-id="46ebf-p105">**Directory synchronization server only**. Instead of deploying the 64-bit directory synchronization server in your on-premises environment, you provision a virtual machine in Azure over the Internet.</span></span>
  
 <span data-ttu-id="46ebf-p106">**La sincronizzazione delle directory + ADFS**. Questa opzione consente di supportare le identità federata di Office 365 (SSO) senza aggiungere componenti hardware per l'infrastruttura locale. Fornisce inoltre resilienza se non è disponibile nell'ambiente Active Directory locale. Le funzionalità di questa opzione includono:</span><span class="sxs-lookup"><span data-stu-id="46ebf-p106">**Directory synchronization + AD FS**. This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure. It also provides resiliency if the on-premises Active Directory environment is unavailable. The features of this option include:</span></span>
  
- <span data-ttu-id="46ebf-257">Componenti di integrazione directory eseguire con macchine virtuali di Azure.</span><span class="sxs-lookup"><span data-stu-id="46ebf-257">Directory integration components run as Azure virtual machines.</span></span>
    
- <span data-ttu-id="46ebf-258">ADFS viene pubblicato su Internet tramite proxy AD FS in esecuzione come macchine virtuali di Azure.</span><span class="sxs-lookup"><span data-stu-id="46ebf-258">AD FS is published to the Internet through AD FS proxies running as Azure virtual machines.</span></span>
    
- <span data-ttu-id="46ebf-259">Il traffico di autenticazione client, per gli utenti che si connettono da qualsiasi posizione, viene gestito dal server ADFS e i proxy che vengono distribuiti come macchine virtuali di Azure.</span><span class="sxs-lookup"><span data-stu-id="46ebf-259">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed as Azure virtual machines.</span></span>
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a><span data-ttu-id="46ebf-260">Integrazione di Lync con Exchange e SharePoint in Office 365</span><span class="sxs-lookup"><span data-stu-id="46ebf-260">Lync integration with Exchange and SharePoint in Office 365</span></span>

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a><span data-ttu-id="46ebf-261">Lync Server con Exchange Online e SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="46ebf-261">Lync Server with Exchange Online and SharePoint Online</span></span>

<span data-ttu-id="46ebf-262">Il diagramma accompagnamento mostra che Office 365 con Exchange Online e SharePoint Online connessa a una farm di Lync Server 2013 locale.</span><span class="sxs-lookup"><span data-stu-id="46ebf-262">The accompanying diagram shows Office 365 with Exchange Online and SharePoint Online connected to an on-premises Lync Server 2013 farm.</span></span>
  
<span data-ttu-id="46ebf-263">I vantaggi della distribuzione consentono di:</span><span class="sxs-lookup"><span data-stu-id="46ebf-263">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="46ebf-264">Utilizzare il set completo di funzionalità di Lync Server 2013.</span><span class="sxs-lookup"><span data-stu-id="46ebf-264">Use the full feature set of Lync Server 2013.</span></span>
    
- <span data-ttu-id="46ebf-265">Utilizzare l'apparecchio telefonico locale esistente, ad esempio PBX.</span><span class="sxs-lookup"><span data-stu-id="46ebf-265">Leverage your existing on-premises phone equipment, such as PBXs.</span></span>
    
- <span data-ttu-id="46ebf-266">Utilizzare Exchange Online per la posta elettronica, gestione il carico dei server di posta elettronica locale e l'archiviazione.</span><span class="sxs-lookup"><span data-stu-id="46ebf-266">Use Exchange Online for email, off-loading the burden of on-premises email servers and storage.</span></span>
    
- <span data-ttu-id="46ebf-267">Utilizzare SharePoint Online per la collaborazione, gestione il carico di lavoro di gestione di server di SharePoint locali.</span><span class="sxs-lookup"><span data-stu-id="46ebf-267">Use SharePoint Online for collaboration, off-loading the burden of maintaining on-premises SharePoint servers.</span></span>
    
- <span data-ttu-id="46ebf-268">Utilizzare Lync, Exchange e SharePoint integrato funzionalità, inclusi messaggistica unificata (UM) in Office 365.</span><span class="sxs-lookup"><span data-stu-id="46ebf-268">Use Lync, Exchange, and SharePoint integrated features, including Unified Messaging (UM) in Office 365.</span></span>
    
#### <a name="exchange-server-with-lync-online"></a><span data-ttu-id="46ebf-269">Server di Exchange con Lync Online</span><span class="sxs-lookup"><span data-stu-id="46ebf-269">Exchange Server with Lync Online</span></span>

<span data-ttu-id="46ebf-270">Il diagramma accompagnamento mostra che Office 365 con Lync Online connessa a una farm di Server di Exchange locale.</span><span class="sxs-lookup"><span data-stu-id="46ebf-270">The accompanying diagram shows Office 365 with Lync Online connected to an on-premises Exchange Server farm.</span></span>
  
<span data-ttu-id="46ebf-271">I vantaggi della distribuzione consentono di:</span><span class="sxs-lookup"><span data-stu-id="46ebf-271">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="46ebf-272">Infrastruttura esistente Exchange.</span><span class="sxs-lookup"><span data-stu-id="46ebf-272">Leverage your existing Exchange infrastructure.</span></span>
    
- <span data-ttu-id="46ebf-273">Utilizzare Lync Online per la presenza, messaggistica immediata e le funzionalità di conferenza.</span><span class="sxs-lookup"><span data-stu-id="46ebf-273">Use Lync Online for presence, instant messaging, and conferencing capabilities.</span></span>
    

