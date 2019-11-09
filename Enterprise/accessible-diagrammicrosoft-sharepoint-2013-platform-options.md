---
title: Diagramma accessibile-opzioni della piattaforma Microsoft SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- SPO_Content
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: Questo articolo è una versione di testo accessibile del diagramma denominato opzioni della piattaforma Microsoft SharePoint 2013.
ms.openlocfilehash: aeb17825efa26260422bd1407dfa71920838011d
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "38077549"
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a><span data-ttu-id="dcbda-103">Diagramma accessibile-opzioni della piattaforma Microsoft SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="dcbda-103">Accessible diagram - Microsoft SharePoint 2013 Platform Options</span></span>

<span data-ttu-id="dcbda-104">**Riepilogo:** Questo articolo è una versione di testo accessibile del diagramma denominato opzioni della piattaforma Microsoft SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="dcbda-104">**Summary:** This article is an accessible text version of the diagram named Microsoft SharePoint 2013 Platform Options.</span></span>
  
<span data-ttu-id="dcbda-105">Quali responsabili decisionali aziendali (BDMs) e gli architetti devono conoscere le distribuzioni di Office 365, Microsoft Azure e locali.</span><span class="sxs-lookup"><span data-stu-id="dcbda-105">What business decision makers (BDMs) and architects need to know about Office 365, Microsoft Azure, and on-premises deployments.</span></span> 
  
<span data-ttu-id="dcbda-106">Questo poster contiene due sezioni:</span><span class="sxs-lookup"><span data-stu-id="dcbda-106">This poster has two sections:</span></span> 
  
- <span data-ttu-id="dcbda-107">Confronto tra quattro distribuzioni diverse per SharePoint 2013: SharePoint in Office 365, un ibrido di Office 365 con una distribuzione locale di SharePoint 2013, Azure e una distribuzione locale di SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="dcbda-107">A comparison of four different deployments for SharePoint 2013: SharePoint in Office 365, a hybrid of Office 365 with an on-premises deployment of SharePoint 2013, Azure, and an on-premises deployment of SharePoint 2013.</span></span> 
    
- <span data-ttu-id="dcbda-108">Descrizione di tre carichi di lavoro tipici da spostare in Azure.</span><span class="sxs-lookup"><span data-stu-id="dcbda-108">A description of three typical workloads to move to Azure.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a><span data-ttu-id="dcbda-109">Confronto tra quattro distribuzioni diverse per la piattaforma SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="dcbda-109">Comparison of four different deployments for the SharePoint 2013 platform</span></span>

<span data-ttu-id="dcbda-110">Il confronto fornisce informazioni su ogni opzione di distribuzione relativa alle aree seguenti:</span><span class="sxs-lookup"><span data-stu-id="dcbda-110">The comparison provides information about each deployment option related to the following areas:</span></span> 
  
- <span data-ttu-id="dcbda-111">Panoramica delle diverse funzionalità di distribuzione</span><span class="sxs-lookup"><span data-stu-id="dcbda-111">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="dcbda-112">Cosa è meglio per ogni tipo di distribuzione</span><span class="sxs-lookup"><span data-stu-id="dcbda-112">What each type of deployment is best for</span></span> 
    
- <span data-ttu-id="dcbda-113">Requisiti di licenza</span><span class="sxs-lookup"><span data-stu-id="dcbda-113">License requirements</span></span> 
    
- <span data-ttu-id="dcbda-114">Attività dell'architettura necessarie per l'implementazione</span><span class="sxs-lookup"><span data-stu-id="dcbda-114">Architecture tasks required to implement</span></span> 
    
- <span data-ttu-id="dcbda-115">Responsabilità per i professionisti IT per l'implementazione</span><span class="sxs-lookup"><span data-stu-id="dcbda-115">IT pro responsibilities for implementation</span></span> 
    
### <a name="overview"></a><span data-ttu-id="dcbda-116">Panoramica</span><span class="sxs-lookup"><span data-stu-id="dcbda-116">Overview</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="dcbda-117">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="dcbda-117">SharePoint 2013 in Office 365</span></span>

<span data-ttu-id="dcbda-118">Aumentare l'efficienza e ottimizzare i costi con i piani multitenant di Office 365.</span><span class="sxs-lookup"><span data-stu-id="dcbda-118">Gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span> 
  
<span data-ttu-id="dcbda-119">Nel diagramma di accompagnamento viene mostrato SharePoint Online con un tenant di Azure Active Directory, che sincronizza i nomi degli account e le password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="dcbda-119">The accompanying diagram shows SharePoint Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="dcbda-120">Descrizione delle caratteristiche:</span><span class="sxs-lookup"><span data-stu-id="dcbda-120">Description of features:</span></span> 
  
- <span data-ttu-id="dcbda-121">Software come servizio (SaaS).</span><span class="sxs-lookup"><span data-stu-id="dcbda-121">Software as a Service (SaaS).</span></span> 
    
- <span data-ttu-id="dcbda-122">Il set di funzionalità RTF è sempre aggiornato.</span><span class="sxs-lookup"><span data-stu-id="dcbda-122">Rich feature set is always up to date.</span></span> 
    
- <span data-ttu-id="dcbda-123">Include un tenant di Azure Active Directory (può essere utilizzato con altre applicazioni).</span><span class="sxs-lookup"><span data-stu-id="dcbda-123">Includes an Azure Active Directory tenant (can be used with other applications).</span></span> 
    
- <span data-ttu-id="dcbda-124">L'integrazione della directory include la sincronizzazione dei nomi degli account e delle password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="dcbda-124">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
    
- <span data-ttu-id="dcbda-125">Se il servizio Single Sign-on (SSO) è un requisito, è possibile implementare Active Directory Federation Services (AD FS).</span><span class="sxs-lookup"><span data-stu-id="dcbda-125">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) can be implemented.</span></span> 
    
- <span data-ttu-id="dcbda-126">Comunicazione client tramite Internet tramite accesso crittografato e autenticato (porta 443).</span><span class="sxs-lookup"><span data-stu-id="dcbda-126">Client communication over the Internet through encrypted and authenticated access (port 443).</span></span> 
    
- <span data-ttu-id="dcbda-127">La migrazione dei dati è limitata a ciò che può essere caricato su Internet.</span><span class="sxs-lookup"><span data-stu-id="dcbda-127">Data migration is limited to what can be uploaded over the Internet.</span></span> 
    
- <span data-ttu-id="dcbda-128">Personalizzazioni: app per Office, SharePoint e SharePoint Designer 2013.</span><span class="sxs-lookup"><span data-stu-id="dcbda-128">Customizations: Apps for Office, SharePoint, and SharePoint Designer 2013.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="dcbda-129">Ibrido con Office 365</span><span class="sxs-lookup"><span data-stu-id="dcbda-129">Hybrid with Office 365</span></span>

<span data-ttu-id="dcbda-130">Combinare i vantaggi di Office 365 con una distribuzione locale di SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="dcbda-130">Combine the benefits of Office 365 with an on-premises deployment of SharePoint 2013.</span></span> 
  
<span data-ttu-id="dcbda-131">Nel diagramma di accompagnamento viene mostrato Office 365 con SharePoint Online con servizi di integrazione applicativa (BCS) per la connessione a una farm di SharePoint Server 2013 locale.</span><span class="sxs-lookup"><span data-stu-id="dcbda-131">The accompanying diagram shows Office 365 with SharePoint Online using Business Connectivity Services (BCS) to connect to an on-premises SharePoint Server 2013 farm.</span></span> 
  
<span data-ttu-id="dcbda-132">Scegliere le caratteristiche seguenti per l'integrazione:</span><span class="sxs-lookup"><span data-stu-id="dcbda-132">Choose which of the following features to integrate:</span></span> 
  
<span data-ttu-id="dcbda-133">Ricerca di SharePoint</span><span class="sxs-lookup"><span data-stu-id="dcbda-133">SharePoint Search</span></span> 
  
- <span data-ttu-id="dcbda-134">Gli utenti possono visualizzare i risultati della ricerca da entrambi gli ambienti.</span><span class="sxs-lookup"><span data-stu-id="dcbda-134">Users can see search results from both environments.</span></span> 
    
- <span data-ttu-id="dcbda-135">Gli utenti Extranet possono accedere in remoto con un account di Active Directory locale e utilizzare tutte le funzionalità ibride disponibili.</span><span class="sxs-lookup"><span data-stu-id="dcbda-135">Extranet users can remotely log on with an on-premises Active Directory account and use all available hybrid functionality.</span></span> 
    
<span data-ttu-id="dcbda-136">BCS</span><span class="sxs-lookup"><span data-stu-id="dcbda-136">BCS</span></span>
  
<span data-ttu-id="dcbda-137">Da SharePoint Online: gli utenti possono eseguire entrambe le operazioni di lettura e scrittura.</span><span class="sxs-lookup"><span data-stu-id="dcbda-137">From SharePoint Online: Users can perform both read and write operations.</span></span> <span data-ttu-id="dcbda-138">Il servizio BCS si connette a una farm di SharePoint Server 2013 locale.</span><span class="sxs-lookup"><span data-stu-id="dcbda-138">The BCS service connects to an on-premises SharePoint Server 2013 farm.</span></span> <span data-ttu-id="dcbda-139">Il servizio BCS configurato nei broker della farm locale la connessione agli endpoint del servizio OData locale.</span><span class="sxs-lookup"><span data-stu-id="dcbda-139">The BCS service configured on the on-premises farm brokers the connection to on-premises OData Service endpoints.</span></span> 
  
<span data-ttu-id="dcbda-140">Duet Enterprise Online</span><span class="sxs-lookup"><span data-stu-id="dcbda-140">Duet Enterprise Online</span></span> 
  
<span data-ttu-id="dcbda-141">Da SharePoint Online, gli utenti possono eseguire operazioni di lettura e scrittura su un sistema SAP locale.</span><span class="sxs-lookup"><span data-stu-id="dcbda-141">From SharePoint Online, users can perform read and write operations against an on-premises SAP system.</span></span> 
  
#### <a name="azure"></a><span data-ttu-id="dcbda-142">Azure</span><span class="sxs-lookup"><span data-stu-id="dcbda-142">Azure</span></span>

<span data-ttu-id="dcbda-143">Sfruttare il cloud mantenendo il controllo completo della piattaforma e delle funzionalità.</span><span class="sxs-lookup"><span data-stu-id="dcbda-143">Take advantage of the cloud while maintaining full control of the platform and features.</span></span> 
  
<span data-ttu-id="dcbda-144">Il diagramma di accompagnamento Visualizza Azure, che contiene due servizi cloud, una farm di SharePoint 2013 e Windows Server Active Directory con DNS che si connette agli utenti tramite Internet o che si connette a Active Directory locale tramite il tunnel VPN.</span><span class="sxs-lookup"><span data-stu-id="dcbda-144">The accompanying diagram shows Azure, which contains two cloud services, a SharePoint 2013 farm, and Windows Server Active Directory with DNS connecting to users over the Internet or connecting to on-premises Active Directory via VPN tunnel.</span></span> 
  
<span data-ttu-id="dcbda-145">Le caratteristiche includono:</span><span class="sxs-lookup"><span data-stu-id="dcbda-145">Features include:</span></span> 
  
-  <span data-ttu-id="dcbda-146">Azure è una piattaforma che fornisce l'infrastruttura e i servizi di app necessari per ospitare una farm di SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="dcbda-146">Azure is a platform that provides the infrastructure and app services needed to host a SharePoint 2013 farm.</span></span>
    
- <span data-ttu-id="dcbda-147">Servizi infrastrutturali.</span><span class="sxs-lookup"><span data-stu-id="dcbda-147">Infrastructure Services.</span></span> 
    
- <span data-ttu-id="dcbda-148">Migliore piattaforma cloud nativa per SQL Server e SharePoint.</span><span class="sxs-lookup"><span data-stu-id="dcbda-148">Best native cloud platform for SQL Server and SharePoint.</span></span> 
    
- <span data-ttu-id="dcbda-149">Le risorse di calcolo sono disponibili quasi immediatamente senza impegno.</span><span class="sxs-lookup"><span data-stu-id="dcbda-149">Computing resources are available almost immediately with no commitment.</span></span> 
    
- <span data-ttu-id="dcbda-150">Concentrarsi sulle applicazioni anziché sui data center e sull'infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="dcbda-150">Focus on applications, instead of datacenters and infrastructure.</span></span> 
    
- <span data-ttu-id="dcbda-151">Ambiente di test e sviluppo poco costoso.</span><span class="sxs-lookup"><span data-stu-id="dcbda-151">Inexpensive development and test environments.</span></span> 
    
- <span data-ttu-id="dcbda-152">Le soluzioni di SharePoint possono essere accessibili da Internet o accessibili solo da un ambiente aziendale tramite un tunnel VPN da sito a sito.</span><span class="sxs-lookup"><span data-stu-id="dcbda-152">SharePoint solutions can be accessible from the Internet or accessible only from a corporate environment through a site-to-site VPN tunnel.</span></span> 
    
- <span data-ttu-id="dcbda-153">Le personalizzazioni non sono limitate.</span><span class="sxs-lookup"><span data-stu-id="dcbda-153">Customizations are not limited.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="dcbda-154">Locali</span><span class="sxs-lookup"><span data-stu-id="dcbda-154">On premises</span></span>

<span data-ttu-id="dcbda-155">Si possiede tutto.</span><span class="sxs-lookup"><span data-stu-id="dcbda-155">You own everything.</span></span> 
  
<span data-ttu-id="dcbda-156">Il diagramma di accompagnamento Visualizza un ambiente locale con server Web, server applicazioni e Active Directory che comunica con tutti i database e i server applicazioni dedicati per la ricerca.</span><span class="sxs-lookup"><span data-stu-id="dcbda-156">The accompanying diagram shows an on-premises environment with web servers, application servers, and Active Directory communicating with all databases and dedicated application servers for search.</span></span> 
  
<span data-ttu-id="dcbda-157">Le caratteristiche includono:</span><span class="sxs-lookup"><span data-stu-id="dcbda-157">Features include:</span></span> 
  
- <span data-ttu-id="dcbda-158">Pianificazione della capacità e dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="dcbda-158">Capacity planning and sizing.</span></span> 
    
- <span data-ttu-id="dcbda-159">Acquisizione e installazione del server.</span><span class="sxs-lookup"><span data-stu-id="dcbda-159">Server acquisition and setup.</span></span> 
    
- <span data-ttu-id="dcbda-160">Distribuzione.</span><span class="sxs-lookup"><span data-stu-id="dcbda-160">Deployment.</span></span> 
    
- <span data-ttu-id="dcbda-161">Scalabilità orizzontale, applicazione di patch e operazioni.</span><span class="sxs-lookup"><span data-stu-id="dcbda-161">Scaling out, patching, and operations.</span></span> 
    
- <span data-ttu-id="dcbda-162">Backup dei dati.</span><span class="sxs-lookup"><span data-stu-id="dcbda-162">Backing up data.</span></span> 
    
- <span data-ttu-id="dcbda-163">Gestione di un ambiente di ripristino di emergenza.</span><span class="sxs-lookup"><span data-stu-id="dcbda-163">Maintaining a disaster recovery environment.</span></span> 
    
- <span data-ttu-id="dcbda-164">Le personalizzazioni non sono limitate.</span><span class="sxs-lookup"><span data-stu-id="dcbda-164">Customizations are not limited.</span></span> 
    
### <a name="deployment-type-is-best-for---"></a><span data-ttu-id="dcbda-165">Il tipo di distribuzione è consigliabile.</span><span class="sxs-lookup"><span data-stu-id="dcbda-165">Deployment type is best for .</span></span> <span data-ttu-id="dcbda-166">.</span><span class="sxs-lookup"><span data-stu-id="dcbda-166"></span></span> <span data-ttu-id="dcbda-167">.</span><span class="sxs-lookup"><span data-stu-id="dcbda-167"></span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="dcbda-168">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="dcbda-168">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="dcbda-169">Condivisione e collaborazione esterne sicure.</span><span class="sxs-lookup"><span data-stu-id="dcbda-169">Secure external sharing and collaboration.</span></span> <span data-ttu-id="dcbda-170">(Caratteristica univoca!)</span><span class="sxs-lookup"><span data-stu-id="dcbda-170">(Unique feature!)</span></span> 
    
- <span data-ttu-id="dcbda-171">Intranet: siti di Team, siti personali e collaborazione interna.</span><span class="sxs-lookup"><span data-stu-id="dcbda-171">Intranet — Team sites, My Sites, and internal collaboration.</span></span> 
    
- <span data-ttu-id="dcbda-172">Archiviazione e controllo delle versioni dei documenti nel cloud.</span><span class="sxs-lookup"><span data-stu-id="dcbda-172">Document storage and versioning in the cloud.</span></span> 
    
- <span data-ttu-id="dcbda-173">Sito Web di base pubblico.</span><span class="sxs-lookup"><span data-stu-id="dcbda-173">Basic public-facing website.</span></span> 
    
<span data-ttu-id="dcbda-174">Funzionalità aggiuntive con i piani di sottoscrizione dedicati a Office 365:</span><span class="sxs-lookup"><span data-stu-id="dcbda-174">Additional features with Office 365 Dedicated subscription plans:</span></span> 
  
- <span data-ttu-id="dcbda-175">Apparecchiature di Microsoft datacenter dedicate all'organizzazione e non condivise con nessun'altra organizzazione.</span><span class="sxs-lookup"><span data-stu-id="dcbda-175">Microsoft datacenter equipment that is dedicated to your organization and not shared with any other organization.</span></span> 
    
- <span data-ttu-id="dcbda-176">Ogni ambiente del cliente risiede in una rete fisicamente separata.</span><span class="sxs-lookup"><span data-stu-id="dcbda-176">Each customer environment resides in a physically separate network.</span></span> 
    
- <span data-ttu-id="dcbda-177">Comunicazione client su una connessione VPN protetta da IPSec o privata.</span><span class="sxs-lookup"><span data-stu-id="dcbda-177">Client communication across an IPSec-secured VPN or customer-owned private connection.</span></span> <span data-ttu-id="dcbda-178">L'autenticazione a due fattori è facoltativa.</span><span class="sxs-lookup"><span data-stu-id="dcbda-178">Two-factor authentication is optional.</span></span> 
    
- <span data-ttu-id="dcbda-179">ITAR-piani di supporto.</span><span class="sxs-lookup"><span data-stu-id="dcbda-179">ITAR-support plans.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="dcbda-180">Ibrido con Office 365</span><span class="sxs-lookup"><span data-stu-id="dcbda-180">Hybrid with Office 365</span></span>

- <span data-ttu-id="dcbda-181">Utilizzare Office 365 per la condivisione e la collaborazione esterne invece di configurare un ambiente Extranet.</span><span class="sxs-lookup"><span data-stu-id="dcbda-181">Use Office 365 for external sharing and collaboration instead of setting up an extranet environment.</span></span> 
    
- <span data-ttu-id="dcbda-182">Spostare i siti personali (OneDrive for business) nel cloud per semplificare l'accesso dei file da parte degli utenti in remoto.</span><span class="sxs-lookup"><span data-stu-id="dcbda-182">Move My Sites (OneDrive for Business) to the cloud to make it easier for users to access their files remotely.</span></span> 
    
- <span data-ttu-id="dcbda-183">Avviare nuovi siti del team in Office 365.</span><span class="sxs-lookup"><span data-stu-id="dcbda-183">Start new team sites in Office 365.</span></span> 
    
- <span data-ttu-id="dcbda-184">Integrazione di un sito di Office 365 con l'ambiente di SharePoint BCS locale.</span><span class="sxs-lookup"><span data-stu-id="dcbda-184">Integrate an Office 365 site with on-premises BCS SharePoint environment.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="dcbda-185">Azure</span><span class="sxs-lookup"><span data-stu-id="dcbda-185">Azure</span></span>

- <span data-ttu-id="dcbda-186">SharePoint per siti Internet: siti di riorientamento pubblico.</span><span class="sxs-lookup"><span data-stu-id="dcbda-186">SharePoint for Internet Sites — Public facing sites.</span></span> <span data-ttu-id="dcbda-187">Trarre vantaggio da Azure AD per gli account dei clienti e l'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="dcbda-187">Take advantage of Azure AD for customer accounts and authentication.</span></span> 
    
- <span data-ttu-id="dcbda-188">Ambienti di sviluppo, testing e gestione temporanea: provisioning e deprovisioning rapido di interi ambienti.</span><span class="sxs-lookup"><span data-stu-id="dcbda-188">Developer, test, and staging environments — Quickly provision and deprovision entire environments.</span></span> 
    
- <span data-ttu-id="dcbda-189">Applicazioni ibride: applicazioni che si estendono al Data Center e al cloud.</span><span class="sxs-lookup"><span data-stu-id="dcbda-189">Hybrid applications — Applications that span your datacenter and the cloud.</span></span> 
    
- <span data-ttu-id="dcbda-190">Ambiente di ripristino di emergenza: ripristino rapido da una situazione di emergenza.</span><span class="sxs-lookup"><span data-stu-id="dcbda-190">Disaster recovery environment — Quickly recover from a disaster.</span></span> <span data-ttu-id="dcbda-191">Paghi solo per l'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="dcbda-191">Pay only for use.</span></span> 
    
- <span data-ttu-id="dcbda-192">Farm che richiedono rapporti profondi o di controllo.</span><span class="sxs-lookup"><span data-stu-id="dcbda-192">Farms that require deep reporting or auditing.</span></span> 
    
- <span data-ttu-id="dcbda-193">Web Analytics.</span><span class="sxs-lookup"><span data-stu-id="dcbda-193">Web analytics.</span></span> 
    
- <span data-ttu-id="dcbda-194">Crittografia dei dati a Rest (i dati vengono crittografati nei database SQL).</span><span class="sxs-lookup"><span data-stu-id="dcbda-194">Data encryption at rest (data is encrypted in the SQL databases).</span></span> 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a><span data-ttu-id="dcbda-195">Crittografia dei dati a Rest (i dati vengono crittografati nei database SQL)</span><span class="sxs-lookup"><span data-stu-id="dcbda-195">Data encryption at rest (data is encrypted in the SQL databases)</span></span>

- <span data-ttu-id="dcbda-196">Farm nazionali (quando i dati devono risiedere all'interno di una giurisdizione).</span><span class="sxs-lookup"><span data-stu-id="dcbda-196">In-country farms (when data is required to reside within a jurisdiction).</span></span> 
    
- <span data-ttu-id="dcbda-197">Soluzioni di BI complesse che devono risiedere vicino ai dati di BI.</span><span class="sxs-lookup"><span data-stu-id="dcbda-197">Complex BI solutions that must reside close to BI data.</span></span> 
    
- <span data-ttu-id="dcbda-198">Soluzioni cloud private.</span><span class="sxs-lookup"><span data-stu-id="dcbda-198">Private cloud solutions.</span></span> 
    
- <span data-ttu-id="dcbda-199">Soluzioni altamente personalizzate.</span><span class="sxs-lookup"><span data-stu-id="dcbda-199">Highly customized solutions.</span></span> 
    
- <span data-ttu-id="dcbda-200">Soluzioni legacy con componenti di terze parti che dipendono da hardware e software che non sono supportati nei servizi di infrastruttura di Azure.</span><span class="sxs-lookup"><span data-stu-id="dcbda-200">Legacy solutions with third-party components that depend on hardware and software that are not supported on Azure Infrastructure Services.</span></span> 
    
- <span data-ttu-id="dcbda-201">Restrizioni sulla privacy che impediscono la sincronizzazione degli account di Active Directory con Azure Active Directory (un requisito per Office 365).</span><span class="sxs-lookup"><span data-stu-id="dcbda-201">Privacy restrictions that prevent synchronization of Active Directory accounts with Azure Active Directory (a requirement for Office 365).</span></span> 
    
- <span data-ttu-id="dcbda-202">Organizzazioni che preferiscono il controllo dell'intera piattaforma e della soluzione.</span><span class="sxs-lookup"><span data-stu-id="dcbda-202">Organizations that prefer control of the entire platform and solution.</span></span> 
    
### <a name="license-requirements"></a><span data-ttu-id="dcbda-203">Requisiti di licenza</span><span class="sxs-lookup"><span data-stu-id="dcbda-203">License requirements</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="dcbda-204">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="dcbda-204">SharePoint 2013 in Office 365</span></span>

<span data-ttu-id="dcbda-205">Modello di sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="dcbda-205">Subscription model.</span></span> <span data-ttu-id="dcbda-206">Non sono necessarie licenze aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="dcbda-206">No additional licenses needed.</span></span> 
  
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="dcbda-207">Ibrido con Office 365</span><span class="sxs-lookup"><span data-stu-id="dcbda-207">Hybrid with Office 365</span></span>

- <span data-ttu-id="dcbda-208">Office 365: modello di sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="dcbda-208">Office 365 — Subscription model.</span></span> <span data-ttu-id="dcbda-209">Non sono necessarie licenze aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="dcbda-209">No additional licenses needed.</span></span> 
    
- <span data-ttu-id="dcbda-210">Locale: vengono applicate tutte le licenze locali.</span><span class="sxs-lookup"><span data-stu-id="dcbda-210">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="dcbda-211">Azure</span><span class="sxs-lookup"><span data-stu-id="dcbda-211">Azure</span></span>

-  <span data-ttu-id="dcbda-212">Sottoscrizione di Azure (include il sistema operativo del server)</span><span class="sxs-lookup"><span data-stu-id="dcbda-212">Azure subscription (includes the server operating system)</span></span>
    
- <span data-ttu-id="dcbda-213">SQL Server</span><span class="sxs-lookup"><span data-stu-id="dcbda-213">SQL Server</span></span> 
    
- <span data-ttu-id="dcbda-214">Licenza del server di SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="dcbda-214">SharePoint 2013 Server License</span></span> 
    
- <span data-ttu-id="dcbda-215">Licenza di accesso client di SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="dcbda-215">SharePoint 2013 Client Access License</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="dcbda-216">Locali</span><span class="sxs-lookup"><span data-stu-id="dcbda-216">On premises</span></span>

- <span data-ttu-id="dcbda-217">Sistema operativo del server</span><span class="sxs-lookup"><span data-stu-id="dcbda-217">Server operating system</span></span> 
    
- <span data-ttu-id="dcbda-218">SQL Server</span><span class="sxs-lookup"><span data-stu-id="dcbda-218">SQL Server</span></span> 
    
- <span data-ttu-id="dcbda-219">Licenza del server di SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="dcbda-219">SharePoint 2013 Server License</span></span> 
    
- <span data-ttu-id="dcbda-220">Licenza di accesso client di SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="dcbda-220">SharePoint 2013 Client Access License</span></span> 
    
### <a name="architecture-tasks"></a><span data-ttu-id="dcbda-221">Attività dell'architettura</span><span class="sxs-lookup"><span data-stu-id="dcbda-221">Architecture tasks</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="dcbda-222">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="dcbda-222">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="dcbda-223">Pianificare e progettare l'integrazione di directory.</span><span class="sxs-lookup"><span data-stu-id="dcbda-223">Plan and design directory integration.</span></span> <span data-ttu-id="dcbda-224">Due opzioni.</span><span class="sxs-lookup"><span data-stu-id="dcbda-224">Two options.</span></span> <span data-ttu-id="dcbda-225">Entrambe le opzioni possono essere distribuite in locale o in Azure: sincronizzazione password (richiede un server a 1 64 bit).</span><span class="sxs-lookup"><span data-stu-id="dcbda-225">Either option can be deployed on premises or in Azure: Password sync (requires one 64-bit server).</span></span> <span data-ttu-id="dcbda-226">SSO (richiede ADFS e più server).</span><span class="sxs-lookup"><span data-stu-id="dcbda-226">SSO (requires AD FS and multiple servers).</span></span> 
    
- <span data-ttu-id="dcbda-227">Garantire la disponibilità e la capacità della rete attraverso i firewall, i server proxy, i gateway e i collegamenti WAN.</span><span class="sxs-lookup"><span data-stu-id="dcbda-227">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span> 
    
- <span data-ttu-id="dcbda-228">Acquisizione dei certificati SSL di terze parti per fornire la sicurezza aziendale per le offerte di servizi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="dcbda-228">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span> 
    
- <span data-ttu-id="dcbda-229">Pianificare il nome del tenant e progettare l'architettura e la governance della raccolta siti.</span><span class="sxs-lookup"><span data-stu-id="dcbda-229">Plan the tenant name, and design the site collection architecture and governance.</span></span> 
    
- <span data-ttu-id="dcbda-230">Pianificare le personalizzazioni, le soluzioni e le app per SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="dcbda-230">Plan customizations, solutions, and apps for SharePoint Online.</span></span> 
    
- <span data-ttu-id="dcbda-231">Decidere se si desidera connettersi a Office 365 utilizzando il protocollo IPv6 (Internet Protocol 6).</span><span class="sxs-lookup"><span data-stu-id="dcbda-231">Decide if you want to connect to Office 365 by using the Internet Protocol 6 (IPv6).</span></span> <span data-ttu-id="dcbda-232">Non si tratta di una cosa comune.</span><span class="sxs-lookup"><span data-stu-id="dcbda-232">This is not common.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="dcbda-233">Ibrido con Office 365</span><span class="sxs-lookup"><span data-stu-id="dcbda-233">Hybrid with Office 365</span></span>

<span data-ttu-id="dcbda-234">Oltre alle attività sia per gli ambienti Office 365 che per quelli locali:</span><span class="sxs-lookup"><span data-stu-id="dcbda-234">In addition to tasks for both the Office 365 and on-premises environments:</span></span> 
  
- <span data-ttu-id="dcbda-235">Determinare la quantità di integrazione delle caratteristiche desiderata e scegliere la topologia ibrida.</span><span class="sxs-lookup"><span data-stu-id="dcbda-235">Determine how much feature integration you want and choose the hybrid topology.</span></span> <span data-ttu-id="dcbda-236">Vedere questo poster del modello: quale topologia ibrida utilizzare?</span><span class="sxs-lookup"><span data-stu-id="dcbda-236">See this model poster: Which hybrid topology should I use?</span></span> 
    
- <span data-ttu-id="dcbda-237">Se necessario, determinare quale dispositivo server proxy verrà utilizzato.</span><span class="sxs-lookup"><span data-stu-id="dcbda-237">If required, determine which proxy server device will be used.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="dcbda-238">Azure</span><span class="sxs-lookup"><span data-stu-id="dcbda-238">Azure</span></span>

<span data-ttu-id="dcbda-239">Progettare l'ambiente di rete di Azure:</span><span class="sxs-lookup"><span data-stu-id="dcbda-239">Design the Azure network environment:</span></span> 
  
- <span data-ttu-id="dcbda-240">Rete virtuale all'interno di Azure, incluse le subnet.</span><span class="sxs-lookup"><span data-stu-id="dcbda-240">Virtual network within Azure, including subnets.</span></span> 
    
- <span data-ttu-id="dcbda-241">Ambiente di dominio e integrazione con i server locali.</span><span class="sxs-lookup"><span data-stu-id="dcbda-241">Domain environment and integration with on-premises servers.</span></span> 
    
- <span data-ttu-id="dcbda-242">Indirizzi IP e DNS.</span><span class="sxs-lookup"><span data-stu-id="dcbda-242">IP addresses and DNS.</span></span> 
    
- <span data-ttu-id="dcbda-243">Gruppi di affinità e account di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="dcbda-243">Affinity groups and storage accounts.</span></span> 
    
<span data-ttu-id="dcbda-244">Progettare l'ambiente di SharePoint in Azure:</span><span class="sxs-lookup"><span data-stu-id="dcbda-244">Design the SharePoint environment in Azure:</span></span> 
  
- <span data-ttu-id="dcbda-245">Topologia della farm di SharePoint e architettura logica.</span><span class="sxs-lookup"><span data-stu-id="dcbda-245">SharePoint farm topology and logical architecture.</span></span> 
    
-  <span data-ttu-id="dcbda-246">I set di disponibilità di Azure e i domini di aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="dcbda-246">Azure availability sets and update domains.</span></span>
    
- <span data-ttu-id="dcbda-247">Dimensioni delle macchine virtuali.</span><span class="sxs-lookup"><span data-stu-id="dcbda-247">Virtual machines sizes.</span></span> 
    
- <span data-ttu-id="dcbda-248">Endpoint con bilanciamento del carico.</span><span class="sxs-lookup"><span data-stu-id="dcbda-248">Load balanced endpoint.</span></span> 
    
- <span data-ttu-id="dcbda-249">Endpoint esterni per l'accesso pubblico, se questo è preferibile.</span><span class="sxs-lookup"><span data-stu-id="dcbda-249">External endpoints for public access, if that is preferable.</span></span> 
    
- <span data-ttu-id="dcbda-250">Ambiente di ripristino di emergenza.</span><span class="sxs-lookup"><span data-stu-id="dcbda-250">Disaster recovery environment.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="dcbda-251">Locali</span><span class="sxs-lookup"><span data-stu-id="dcbda-251">On premises</span></span>

<span data-ttu-id="dcbda-252">Progettare l'ambiente di SharePoint in un ambiente locale esistente:</span><span class="sxs-lookup"><span data-stu-id="dcbda-252">Design the SharePoint environment in an existing on-premises environment:</span></span> 
  
- <span data-ttu-id="dcbda-253">Topologia della farm di SharePoint e architettura logica.</span><span class="sxs-lookup"><span data-stu-id="dcbda-253">SharePoint farm topology and logical architecture.</span></span> 
    
- <span data-ttu-id="dcbda-254">Hardware del server.</span><span class="sxs-lookup"><span data-stu-id="dcbda-254">Server hardware.</span></span> 
    
- <span data-ttu-id="dcbda-255">Ambiente virtuale, se utilizzato.</span><span class="sxs-lookup"><span data-stu-id="dcbda-255">Virtual environment, if used.</span></span> 
    
- <span data-ttu-id="dcbda-256">Bilanciamento del carico.</span><span class="sxs-lookup"><span data-stu-id="dcbda-256">Load balancing.</span></span> 
    
- <span data-ttu-id="dcbda-257">Integrazione con servizi di dominio Active Directory e DNS.</span><span class="sxs-lookup"><span data-stu-id="dcbda-257">Integration with AD DS and DNS.</span></span> 
    
- <span data-ttu-id="dcbda-258">Ambiente di ripristino di emergenza.</span><span class="sxs-lookup"><span data-stu-id="dcbda-258">Disaster recovery environment.</span></span> 
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="dcbda-259">Responsabilità per i professionisti IT</span><span class="sxs-lookup"><span data-stu-id="dcbda-259">IT pro responsibilities</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="dcbda-260">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="dcbda-260">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="dcbda-261">Garantire che le workstation degli utenti soddisfino i prerequisiti client di Office 365.</span><span class="sxs-lookup"><span data-stu-id="dcbda-261">Ensure user workstations meet Office 365 client prerequisites.</span></span> 
    
- <span data-ttu-id="dcbda-262">Implementare il piano di integrazione della directory.</span><span class="sxs-lookup"><span data-stu-id="dcbda-262">Implement the directory integration plan.</span></span> 
    
- <span data-ttu-id="dcbda-263">Pianificare e implementare i record DNS interni ed esterni e il routing.</span><span class="sxs-lookup"><span data-stu-id="dcbda-263">Plan and implement internal and external DNS records and routing.</span></span> 
    
- <span data-ttu-id="dcbda-264">Configurare il proxy o il firewall per i requisiti di indirizzo IP e URL di Office 365.</span><span class="sxs-lookup"><span data-stu-id="dcbda-264">Configure the proxy or firewall for Office 365 IP address and URL requirements.</span></span> 
    
- <span data-ttu-id="dcbda-265">Creare e assegnare autorizzazioni per le raccolte siti.</span><span class="sxs-lookup"><span data-stu-id="dcbda-265">Create and assign permissions to site collections.</span></span> 
    
- <span data-ttu-id="dcbda-266">Implementare le personalizzazioni, le soluzioni e le app per SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="dcbda-266">Implement customizations, solutions, and apps for SharePoint Online.</span></span> 
    
- <span data-ttu-id="dcbda-267">Monitorare la disponibilità della rete e identificare i colli di bottiglia possibili.</span><span class="sxs-lookup"><span data-stu-id="dcbda-267">Monitor network availability and identify possible bottlenecks.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="dcbda-268">Ibrido con Office 365</span><span class="sxs-lookup"><span data-stu-id="dcbda-268">Hybrid with Office 365</span></span>

<span data-ttu-id="dcbda-269">Oltre alle attività sia per gli ambienti Office 365 che per quelli locali:</span><span class="sxs-lookup"><span data-stu-id="dcbda-269">In addition to tasks for both the Office 365 and on-premises environments:</span></span> 
  
- <span data-ttu-id="dcbda-270">Configurare il dispositivo server proxy, se necessario.</span><span class="sxs-lookup"><span data-stu-id="dcbda-270">Configure the proxy server device, if required.</span></span> 
    
- <span data-ttu-id="dcbda-271">Configurare l'infrastruttura di gestione delle identità ibride: SSO e l'autenticazione da server a server tra i due ambienti.</span><span class="sxs-lookup"><span data-stu-id="dcbda-271">Configure the hybrid identity management infrastructure: SSO and server-to-server authentication between the two environments.</span></span> 
    
- <span data-ttu-id="dcbda-272">Configurare l'integrazione delle funzionalità scelte: Search, BCS, Duet Enterprise online.</span><span class="sxs-lookup"><span data-stu-id="dcbda-272">Configure the integration of chosen features: Search, BCS, Duet Enterprise Online.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="dcbda-273">Azure</span><span class="sxs-lookup"><span data-stu-id="dcbda-273">Azure</span></span>

<span data-ttu-id="dcbda-274">Distribuire e gestire l'ambiente di Azure e SharePoint:</span><span class="sxs-lookup"><span data-stu-id="dcbda-274">Deploy and manage the Azure and SharePoint environment:</span></span> 
  
- <span data-ttu-id="dcbda-275">Implementare e gestire l'ambiente di rete di Azure.</span><span class="sxs-lookup"><span data-stu-id="dcbda-275">Implement and manage the Azure network environment.</span></span> 
    
- <span data-ttu-id="dcbda-276">Distribuire l'ambiente di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="dcbda-276">Deploy the SharePoint environment.</span></span> 
    
- <span data-ttu-id="dcbda-277">Aggiornare i server della farm di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="dcbda-277">Update SharePoint farm servers.</span></span> 
    
- <span data-ttu-id="dcbda-278">Aggiungere o arrestare macchine virtuali secondo necessità in base all'utilizzo della farm.</span><span class="sxs-lookup"><span data-stu-id="dcbda-278">Add or shut down virtual machines as needed based on farm utilization.</span></span> 
    
- <span data-ttu-id="dcbda-279">Aumentare o diminuire le dimensioni delle macchine virtuali, se necessario.</span><span class="sxs-lookup"><span data-stu-id="dcbda-279">Increase or decrease virtual machine sizes, as needed.</span></span> 
    
- <span data-ttu-id="dcbda-280">Eseguire il backup dell'ambiente di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="dcbda-280">Back up the SharePoint environment.</span></span> 
    
- <span data-ttu-id="dcbda-281">Implementare l'ambiente di ripristino di emergenza e il protocollo.</span><span class="sxs-lookup"><span data-stu-id="dcbda-281">Implement the disaster recovery environment and protocol.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="dcbda-282">Locali</span><span class="sxs-lookup"><span data-stu-id="dcbda-282">On premises</span></span>

<span data-ttu-id="dcbda-283">Distribuire e gestire l'ambiente SharePoint in locale:</span><span class="sxs-lookup"><span data-stu-id="dcbda-283">Deploy and manage the SharePoint on premises environment:</span></span> 
  
- <span data-ttu-id="dcbda-284">Server di provisioning.</span><span class="sxs-lookup"><span data-stu-id="dcbda-284">Provision servers.</span></span> 
    
- <span data-ttu-id="dcbda-285">Distribuire l'ambiente di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="dcbda-285">Deploy the SharePoint environment.</span></span> 
    
- <span data-ttu-id="dcbda-286">Aggiornare i server della farm di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="dcbda-286">Update SharePoint farm servers.</span></span> 
    
- <span data-ttu-id="dcbda-287">Aggiungere o rimuovere i server della farm in base all'utilizzo della farm.</span><span class="sxs-lookup"><span data-stu-id="dcbda-287">Add or remove farm servers as needed based on farm utilization.</span></span> 
    
- <span data-ttu-id="dcbda-288">Eseguire il backup dell'ambiente di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="dcbda-288">Back up the SharePoint environment.</span></span> 
    
- <span data-ttu-id="dcbda-289">Implementare l'ambiente di ripristino di emergenza e il protocollo.</span><span class="sxs-lookup"><span data-stu-id="dcbda-289">Implement the disaster recovery environment and protocol.</span></span> 
    
## <a name="three-typical-workloads-to-move-to-azure"></a><span data-ttu-id="dcbda-290">Tre carichi di lavoro tipici da spostare in Azure</span><span class="sxs-lookup"><span data-stu-id="dcbda-290">Three typical workloads to move to Azure</span></span>

### <a name="office-365-plus-directory-components-in-azure"></a><span data-ttu-id="dcbda-291">Componenti di directory di Office 365 Plus in Azure</span><span class="sxs-lookup"><span data-stu-id="dcbda-291">Office 365 plus Directory Components in Azure</span></span>

<span data-ttu-id="dcbda-292">La distribuzione di componenti di integrazione della directory di Office 365 in Azure è più veloce perché è in grado di distribuire macchine virtuali su richiesta.</span><span class="sxs-lookup"><span data-stu-id="dcbda-292">Deploying Office 365 directory integration components in Azure is faster because it can deploy virtual machines on-demand.</span></span> 
  
#### <a name="directory-synchronization-server-only"></a><span data-ttu-id="dcbda-293">Solo server di sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="dcbda-293">Directory synchronization server only</span></span>

<span data-ttu-id="dcbda-294">Invece di distribuire il server di sincronizzazione della directory a 64 bit nell'ambiente locale, eseguire il provisioning di una macchina virtuale in Azure.</span><span class="sxs-lookup"><span data-stu-id="dcbda-294">Instead of deploying the 64-bit directory synchronization server in your on-premises environment, provision a virtual machine in Azure instead.</span></span> 
  
<span data-ttu-id="dcbda-295">Nel diagramma di accompagnamento viene mostrato SharePoint Online con un tenant di Azure Active Directory, che sincronizza i nomi degli account e le password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="dcbda-295">The accompanying diagram shows SharePoint Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
  
#### <a name="directory-synchronization-plus-ad-fs"></a><span data-ttu-id="dcbda-296">Sincronizzazione della directory e AD FS</span><span class="sxs-lookup"><span data-stu-id="dcbda-296">Directory synchronization plus AD FS</span></span>

<span data-ttu-id="dcbda-297">Questa opzione consente di supportare le identità federative di Office 365 senza aggiungere hardware all'infrastruttura locale.</span><span class="sxs-lookup"><span data-stu-id="dcbda-297">This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure.</span></span> <span data-ttu-id="dcbda-298">Inoltre, fornisce resilienza se l'ambiente Active Directory locale non è disponibile.</span><span class="sxs-lookup"><span data-stu-id="dcbda-298">It also provides resiliency if the on-premises Active Directory environment is unavailable.</span></span> 
  
- <span data-ttu-id="dcbda-299">I componenti di integrazione della directory risiedono in Azure.</span><span class="sxs-lookup"><span data-stu-id="dcbda-299">Directory integration components reside in Azure.</span></span> 
    
- <span data-ttu-id="dcbda-300">AD FS viene pubblicato su Internet tramite proxy ADFS in Azure.</span><span class="sxs-lookup"><span data-stu-id="dcbda-300">AD FS is published to the Internet through AD FS proxies in Azure.</span></span> 
    
- <span data-ttu-id="dcbda-301">Il traffico di autenticazione del client, per gli utenti che si connettono da qualsiasi percorso, è gestito da server ADFS e da proxy distribuiti in Azure.</span><span class="sxs-lookup"><span data-stu-id="dcbda-301">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed on Azure.</span></span> 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a><span data-ttu-id="dcbda-302">Sito Internet pubblico e Azure AD per l'autenticazione dei clienti</span><span class="sxs-lookup"><span data-stu-id="dcbda-302">Public-facing Internet site and Azure AD for customer authentication</span></span>

<span data-ttu-id="dcbda-303">Approfitta della possibilità di scalare facilmente la domanda inserendo il sito Internet in Azure.</span><span class="sxs-lookup"><span data-stu-id="dcbda-303">Take advantage of the ability to easily scale to demand by placing your Internet site in Azure.</span></span> <span data-ttu-id="dcbda-304">Usare Azure AD per archiviare gli account dei clienti.</span><span class="sxs-lookup"><span data-stu-id="dcbda-304">Use Azure AD to store customer accounts.</span></span> 
  
#### <a name="azure-advantages-for-internet-sites"></a><span data-ttu-id="dcbda-305">Vantaggi di Azure per i siti Internet</span><span class="sxs-lookup"><span data-stu-id="dcbda-305">Azure advantages for Internet sites</span></span>

- <span data-ttu-id="dcbda-306">Pagare solo le risorse necessarie per la scalabilità del numero di macchine virtuali in base all'utilizzo della farm.</span><span class="sxs-lookup"><span data-stu-id="dcbda-306">Pay only for the resources you need by scaling the number of virtual machines based on farm utilization.</span></span> 
    
- <span data-ttu-id="dcbda-307">Aggiungere rapporti profondi e analisi Web.</span><span class="sxs-lookup"><span data-stu-id="dcbda-307">Add deep reporting and web analytics.</span></span> 
    
- <span data-ttu-id="dcbda-308">Concentrarsi sullo sviluppo di un sito importante anziché sull'infrastruttura di costruzione.</span><span class="sxs-lookup"><span data-stu-id="dcbda-308">Focus on developing a great site rather than building infrastructure.</span></span> 
    
#### <a name="azure-ad"></a><span data-ttu-id="dcbda-309">Azure AD</span><span class="sxs-lookup"><span data-stu-id="dcbda-309">Azure AD</span></span>

<span data-ttu-id="dcbda-310">Azure AD offre funzionalità di gestione delle identità e controllo di accesso per i servizi cloud.</span><span class="sxs-lookup"><span data-stu-id="dcbda-310">Azure AD provides identity management and access control capabilities for cloud services.</span></span> <span data-ttu-id="dcbda-311">Le funzionalità includono un archivio basato sul cloud per i dati di directory e un set di base di servizi di identità, tra cui processi di accesso degli utenti, servizi di autenticazione e AD FS.</span><span class="sxs-lookup"><span data-stu-id="dcbda-311">Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS.</span></span> <span data-ttu-id="dcbda-312">I servizi Identity inclusi in Azure AD si integrano facilmente con le distribuzioni di Active Directory locali e supportano completamente i provider di identità di terze parti.</span><span class="sxs-lookup"><span data-stu-id="dcbda-312">The identity services that are included with Azure AD easily integrate with your on-premises Active Directory deployments and fully support third-party identity providers.</span></span> 
  
<span data-ttu-id="dcbda-313">Nel diagramma di accompagnamento viene illustrata la configurazione delle aree e dell'autenticazione importanti per i siti con accesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="dcbda-313">The accompanying diagram shows the configuration of zones and authentication that is important for Internet-facing sites.</span></span> <span data-ttu-id="dcbda-314">Nel diagramma viene visualizzato il tenant di Azure Active Directory, che contiene una farm di SharePoint in Azure con due aree:</span><span class="sxs-lookup"><span data-stu-id="dcbda-314">The diagram shows the Azure Active Directory Tenant, which contains a SharePoint Farm on Azure with two zones:</span></span> 
  
- <span data-ttu-id="dcbda-315">Un'area Internet che interagisce con utenti e visitatori anonimi e autenticati all'esterno della rete</span><span class="sxs-lookup"><span data-stu-id="dcbda-315">An Internet zone that interacts with Anonymous and Authenticated visitors and customers outside the network</span></span> 
    
- <span data-ttu-id="dcbda-316">Un'area predefinita che contiene NTLM per la ricerca per indicizzazione e l'autenticazione di Windows che interagiscono con la distribuzione di Active Directory locale su un tunnel VPN.</span><span class="sxs-lookup"><span data-stu-id="dcbda-316">A default zone that contains NTLM for Crawl and Windows Authentication that interacts with your on-premises Active Directory deployment over a VPN tunnel.</span></span> 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a><span data-ttu-id="dcbda-317">Farm locale e ripristino di emergenza in Azure</span><span class="sxs-lookup"><span data-stu-id="dcbda-317">On-premises Farm plus Disaster Recovery in Azure</span></span>

<span data-ttu-id="dcbda-318">Scegliere un'opzione di ripristino di emergenza che corrisponda ai requisiti aziendali.</span><span class="sxs-lookup"><span data-stu-id="dcbda-318">Choose a disaster recovery option that matches your business requirements.</span></span> <span data-ttu-id="dcbda-319">In Azure sono disponibili opzioni di ingresso per le aziende per iniziare a usare il ripristino di emergenza e le opzioni avanzate per aziende con requisiti di resilienza elevati.</span><span class="sxs-lookup"><span data-stu-id="dcbda-319">Azure provides entry-level options for companies getting started with disaster recovery and advanced options for enterprises with high resiliency requirements.</span></span> 
  
#### <a name="cold-standby"></a><span data-ttu-id="dcbda-320">Standby freddo</span><span class="sxs-lookup"><span data-stu-id="dcbda-320">Cold standby</span></span>

- <span data-ttu-id="dcbda-321">La farm viene creata completamente, ma le macchine virtuali sono arrestate.</span><span class="sxs-lookup"><span data-stu-id="dcbda-321">The farm is fully built, but the virtual machines are stopped.</span></span> <span data-ttu-id="dcbda-322">(Paghi solo quando è in esecuzione!)</span><span class="sxs-lookup"><span data-stu-id="dcbda-322">(You're paying only when they're running!)</span></span> 
    
- <span data-ttu-id="dcbda-323">La gestione dell'ambiente include l'avvio delle macchine virtuali di tanto in tanto, l'applicazione di patch, l'aggiornamento e la verifica dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="dcbda-323">Maintaining the environment includes starting the virtual machines from time-to-time, patching, updating, and verifying the environment.</span></span> 
    
- <span data-ttu-id="dcbda-324">Avviare l'ambiente completo in caso di calamità.</span><span class="sxs-lookup"><span data-stu-id="dcbda-324">Start the full environment in the event of a disaster.</span></span> 
    
#### <a name="warm-standby"></a><span data-ttu-id="dcbda-325">Standby caldo</span><span class="sxs-lookup"><span data-stu-id="dcbda-325">Warm standby</span></span>

- <span data-ttu-id="dcbda-326">Include una farm di piccole dimensioni di cui è stato eseguito il provisioning e l'esecuzione.</span><span class="sxs-lookup"><span data-stu-id="dcbda-326">This includes a small farm that is provisioned and running.</span></span> 
    
- <span data-ttu-id="dcbda-327">La farm può servire immediatamente gli utenti in caso di failover.</span><span class="sxs-lookup"><span data-stu-id="dcbda-327">The farm can immediately serve users in the event of a failover.</span></span> 
    
- <span data-ttu-id="dcbda-328">Scalare rapidamente la farm per servire la base di utenti completa.</span><span class="sxs-lookup"><span data-stu-id="dcbda-328">Scale out the farm quickly to serve the full user base.</span></span> 
    
#### <a name="hot-standby"></a><span data-ttu-id="dcbda-329">Standby caldo</span><span class="sxs-lookup"><span data-stu-id="dcbda-329">Hot standby</span></span>

<span data-ttu-id="dcbda-330">Viene effettuato il provisioning e l'esecuzione di una farm di dimensioni complete in modalità standby.</span><span class="sxs-lookup"><span data-stu-id="dcbda-330">A fully-sized farm is provisioned and running on standby.</span></span> 
  
<span data-ttu-id="dcbda-331">Nel diagramma di accompagnamento viene illustrata una farm locale che interagisce con l'ambiente di ripristino di emergenza di SharePoint in Azure.</span><span class="sxs-lookup"><span data-stu-id="dcbda-331">The accompanying diagram shows an on-premises farm interacting with the SharePoint Disaster Recovery Environment on Azure.</span></span> <span data-ttu-id="dcbda-332">Nei database locali viene utilizzato il log shipping di SQL Server tramite il tunnel VPN per accedere all'ambiente di ripristino di emergenza di SharePoint, che include due server di database SQL che contengono i database di SharePoint, due server front-end Web e due SharePoint Server applicazioni.</span><span class="sxs-lookup"><span data-stu-id="dcbda-332">The on-premises databases use SQL Server Log Shipping over the VPN tunnel to access the SharePoint Disaster Recovery environment, which includes two SQL database servers that contain the SharePoint databases, two Web Front End servers, and two SharePoint Application servers.</span></span> 
  

