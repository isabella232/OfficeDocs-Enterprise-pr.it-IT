---
title: Diagramma accessibile-opzioni della piattaforma Microsoft SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: Questo articolo è una versione di testo accessibile del diagramma denominato opzioni della piattaforma Microsoft SharePoint 2013.
ms.openlocfilehash: 4a0b068ffb8abbe11c2286f3daa70c5f62295425
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068602"
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a><span data-ttu-id="9d775-103">Diagramma accessibile-opzioni della piattaforma Microsoft SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="9d775-103">Accessible diagram - Microsoft SharePoint 2013 Platform Options</span></span>

<span data-ttu-id="9d775-104">**Riepilogo:** Questo articolo è una versione di testo accessibile del diagramma denominato opzioni della piattaforma Microsoft SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="9d775-104">**Summary:** This article is an accessible text version of the diagram named Microsoft SharePoint 2013 Platform Options.</span></span>
  
<span data-ttu-id="9d775-105">Quali responsabili decisionali aziendali (BDMs) e gli architetti devono conoscere le distribuzioni di Office 365, Microsoft Azure e locali.</span><span class="sxs-lookup"><span data-stu-id="9d775-105">What business decision makers (BDMs) and architects need to know about Office 365, Microsoft Azure, and on-premises deployments.</span></span> 
  
<span data-ttu-id="9d775-106">Questo poster contiene due sezioni:</span><span class="sxs-lookup"><span data-stu-id="9d775-106">This poster has two sections:</span></span> 
  
- <span data-ttu-id="9d775-107">Confronto tra quattro distribuzioni diverse per SharePoint 2013: SharePoint in Office 365, un ibrido di Office 365 con una distribuzione locale di SharePoint 2013, Azure e una distribuzione locale di SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="9d775-107">A comparison of four different deployments for SharePoint 2013: SharePoint in Office 365, a hybrid of Office 365 with an on-premises deployment of SharePoint 2013, Azure, and an on-premises deployment of SharePoint 2013.</span></span> 
    
- <span data-ttu-id="9d775-108">Descrizione di tre carichi di lavoro tipici da spostare in Azure.</span><span class="sxs-lookup"><span data-stu-id="9d775-108">A description of three typical workloads to move to Azure.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a><span data-ttu-id="9d775-109">Confronto tra quattro distribuzioni diverse per la piattaforma SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="9d775-109">Comparison of four different deployments for the SharePoint 2013 platform</span></span>

<span data-ttu-id="9d775-110">Il confronto fornisce informazioni su ogni opzione di distribuzione relativa alle aree seguenti:</span><span class="sxs-lookup"><span data-stu-id="9d775-110">The comparison provides information about each deployment option related to the following areas:</span></span> 
  
- <span data-ttu-id="9d775-111">Panoramica delle diverse funzionalità di distribuzione</span><span class="sxs-lookup"><span data-stu-id="9d775-111">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="9d775-112">Cosa è meglio per ogni tipo di distribuzione</span><span class="sxs-lookup"><span data-stu-id="9d775-112">What each type of deployment is best for</span></span> 
    
- <span data-ttu-id="9d775-113">Requisiti di licenza</span><span class="sxs-lookup"><span data-stu-id="9d775-113">License requirements</span></span> 
    
- <span data-ttu-id="9d775-114">Attività dell'architettura necessarie per l'implementazione</span><span class="sxs-lookup"><span data-stu-id="9d775-114">Architecture tasks required to implement</span></span> 
    
- <span data-ttu-id="9d775-115">Responsabilità per i professionisti IT per l'implementazione</span><span class="sxs-lookup"><span data-stu-id="9d775-115">IT pro responsibilities for implementation</span></span> 
    
### <a name="overview"></a><span data-ttu-id="9d775-116">Panoramica</span><span class="sxs-lookup"><span data-stu-id="9d775-116">Overview</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="9d775-117">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="9d775-117">SharePoint 2013 in Office 365</span></span>

<span data-ttu-id="9d775-118">Aumentare l'efficienza e ottimizzare i costi con i piani multitenant di Office 365.</span><span class="sxs-lookup"><span data-stu-id="9d775-118">Gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span> 
  
<span data-ttu-id="9d775-119">Nel diagramma di accompagnamento viene mostrato SharePoint Online con un tenant di Azure Active Directory, che sincronizza i nomi degli account e le password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9d775-119">The accompanying diagram shows SharePoint Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="9d775-120">Descrizione delle caratteristiche:</span><span class="sxs-lookup"><span data-stu-id="9d775-120">Description of features:</span></span> 
  
- <span data-ttu-id="9d775-121">Software come servizio (SaaS).</span><span class="sxs-lookup"><span data-stu-id="9d775-121">Software as a Service (SaaS).</span></span> 
    
- <span data-ttu-id="9d775-122">Il set di funzionalità RTF è sempre aggiornato.</span><span class="sxs-lookup"><span data-stu-id="9d775-122">Rich feature set is always up to date.</span></span> 
    
- <span data-ttu-id="9d775-123">Include un tenant di Azure Active Directory (può essere utilizzato con altre applicazioni).</span><span class="sxs-lookup"><span data-stu-id="9d775-123">Includes an Azure Active Directory tenant (can be used with other applications).</span></span> 
    
- <span data-ttu-id="9d775-124">L'integrazione della directory include la sincronizzazione dei nomi degli account e delle password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9d775-124">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
    
- <span data-ttu-id="9d775-125">Se il servizio Single Sign-on (SSO) è un requisito, è possibile implementare Active Directory Federation Services (AD FS).</span><span class="sxs-lookup"><span data-stu-id="9d775-125">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) can be implemented.</span></span> 
    
- <span data-ttu-id="9d775-126">Comunicazione client tramite Internet tramite accesso crittografato e autenticato (porta 443).</span><span class="sxs-lookup"><span data-stu-id="9d775-126">Client communication over the Internet through encrypted and authenticated access (port 443).</span></span> 
    
- <span data-ttu-id="9d775-127">La migrazione dei dati è limitata a ciò che può essere caricato su Internet.</span><span class="sxs-lookup"><span data-stu-id="9d775-127">Data migration is limited to what can be uploaded over the Internet.</span></span> 
    
- <span data-ttu-id="9d775-128">Personalizzazioni: app per Office, SharePoint e SharePoint Designer 2013.</span><span class="sxs-lookup"><span data-stu-id="9d775-128">Customizations: Apps for Office, SharePoint, and SharePoint Designer 2013.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="9d775-129">Ibrido con Office 365</span><span class="sxs-lookup"><span data-stu-id="9d775-129">Hybrid with Office 365</span></span>

<span data-ttu-id="9d775-130">Combinare i vantaggi di Office 365 con una distribuzione locale di SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="9d775-130">Combine the benefits of Office 365 with an on-premises deployment of SharePoint 2013.</span></span> 
  
<span data-ttu-id="9d775-131">Nel diagramma di accompagnamento viene mostrato Office 365 con SharePoint Online con servizi di integrazione applicativa (BCS) per la connessione a una farm di SharePoint Server 2013 locale.</span><span class="sxs-lookup"><span data-stu-id="9d775-131">The accompanying diagram shows Office 365 with SharePoint Online using Business Connectivity Services (BCS) to connect to an on-premises SharePoint Server 2013 farm.</span></span> 
  
<span data-ttu-id="9d775-132">Scegliere le caratteristiche seguenti per l'integrazione:</span><span class="sxs-lookup"><span data-stu-id="9d775-132">Choose which of the following features to integrate:</span></span> 
  
<span data-ttu-id="9d775-133">Ricerca di SharePoint</span><span class="sxs-lookup"><span data-stu-id="9d775-133">SharePoint Search</span></span> 
  
- <span data-ttu-id="9d775-134">Gli utenti possono visualizzare i risultati della ricerca da entrambi gli ambienti.</span><span class="sxs-lookup"><span data-stu-id="9d775-134">Users can see search results from both environments.</span></span> 
    
- <span data-ttu-id="9d775-135">Gli utenti Extranet possono accedere in remoto con un account di Active Directory locale e utilizzare tutte le funzionalità ibride disponibili.</span><span class="sxs-lookup"><span data-stu-id="9d775-135">Extranet users can remotely log on with an on-premises Active Directory account and use all available hybrid functionality.</span></span> 
    
<span data-ttu-id="9d775-136">BCS</span><span class="sxs-lookup"><span data-stu-id="9d775-136">BCS</span></span>
  
<span data-ttu-id="9d775-137">Da SharePoint Online: gli utenti possono eseguire entrambe le operazioni di lettura e scrittura.</span><span class="sxs-lookup"><span data-stu-id="9d775-137">From SharePoint Online: Users can perform both read and write operations.</span></span> <span data-ttu-id="9d775-138">Il servizio BCS si connette a una farm di SharePoint Server 2013 locale.</span><span class="sxs-lookup"><span data-stu-id="9d775-138">The BCS service connects to an on-premises SharePoint Server 2013 farm.</span></span> <span data-ttu-id="9d775-139">Il servizio BCS configurato nei broker della farm locale la connessione agli endpoint del servizio OData locale.</span><span class="sxs-lookup"><span data-stu-id="9d775-139">The BCS service configured on the on-premises farm brokers the connection to on-premises OData Service endpoints.</span></span> 
  
<span data-ttu-id="9d775-140">Duet Enterprise Online</span><span class="sxs-lookup"><span data-stu-id="9d775-140">Duet Enterprise Online</span></span> 
  
<span data-ttu-id="9d775-141">Da SharePoint Online, gli utenti possono eseguire operazioni di lettura e scrittura su un sistema SAP locale.</span><span class="sxs-lookup"><span data-stu-id="9d775-141">From SharePoint Online, users can perform read and write operations against an on-premises SAP system.</span></span> 
  
#### <a name="azure"></a><span data-ttu-id="9d775-142">Azure</span><span class="sxs-lookup"><span data-stu-id="9d775-142">Azure</span></span>

<span data-ttu-id="9d775-143">Sfruttare il cloud mantenendo il controllo completo della piattaforma e delle funzionalità.</span><span class="sxs-lookup"><span data-stu-id="9d775-143">Take advantage of the cloud while maintaining full control of the platform and features.</span></span> 
  
<span data-ttu-id="9d775-144">Il diagramma di accompagnamento Visualizza Azure, che contiene due servizi cloud, una farm di SharePoint 2013 e Windows Server Active Directory con DNS che si connette agli utenti tramite Internet o che si connette a Active Directory locale tramite il tunnel VPN.</span><span class="sxs-lookup"><span data-stu-id="9d775-144">The accompanying diagram shows Azure, which contains two cloud services, a SharePoint 2013 farm, and Windows Server Active Directory with DNS connecting to users over the Internet or connecting to on-premises Active Directory via VPN tunnel.</span></span> 
  
<span data-ttu-id="9d775-145">Le caratteristiche includono:</span><span class="sxs-lookup"><span data-stu-id="9d775-145">Features include:</span></span> 
  
-  <span data-ttu-id="9d775-146">Azure è una piattaforma che fornisce l'infrastruttura e i servizi di app necessari per ospitare una farm di SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="9d775-146">Azure is a platform that provides the infrastructure and app services needed to host a SharePoint 2013 farm.</span></span>
    
- <span data-ttu-id="9d775-147">Servizi infrastrutturali.</span><span class="sxs-lookup"><span data-stu-id="9d775-147">Infrastructure Services.</span></span> 
    
- <span data-ttu-id="9d775-148">Migliore piattaforma cloud nativa per SQL Server e SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9d775-148">Best native cloud platform for SQL Server and SharePoint.</span></span> 
    
- <span data-ttu-id="9d775-149">Le risorse di calcolo sono disponibili quasi immediatamente senza impegno.</span><span class="sxs-lookup"><span data-stu-id="9d775-149">Computing resources are available almost immediately with no commitment.</span></span> 
    
- <span data-ttu-id="9d775-150">Concentrarsi sulle applicazioni anziché sui data center e sull'infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="9d775-150">Focus on applications, instead of datacenters and infrastructure.</span></span> 
    
- <span data-ttu-id="9d775-151">Ambiente di test e sviluppo poco costoso.</span><span class="sxs-lookup"><span data-stu-id="9d775-151">Inexpensive development and test environments.</span></span> 
    
- <span data-ttu-id="9d775-152">Le soluzioni di SharePoint possono essere accessibili da Internet o accessibili solo da un ambiente aziendale tramite un tunnel VPN da sito a sito.</span><span class="sxs-lookup"><span data-stu-id="9d775-152">SharePoint solutions can be accessible from the Internet or accessible only from a corporate environment through a site-to-site VPN tunnel.</span></span> 
    
- <span data-ttu-id="9d775-153">Le personalizzazioni non sono limitate.</span><span class="sxs-lookup"><span data-stu-id="9d775-153">Customizations are not limited.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="9d775-154">Locali</span><span class="sxs-lookup"><span data-stu-id="9d775-154">On premises</span></span>

<span data-ttu-id="9d775-155">Si possiede tutto.</span><span class="sxs-lookup"><span data-stu-id="9d775-155">You own everything.</span></span> 
  
<span data-ttu-id="9d775-156">Il diagramma di accompagnamento Visualizza un ambiente locale con server Web, server applicazioni e Active Directory che comunica con tutti i database e i server applicazioni dedicati per la ricerca.</span><span class="sxs-lookup"><span data-stu-id="9d775-156">The accompanying diagram shows an on-premises environment with web servers, application servers, and Active Directory communicating with all databases and dedicated application servers for search.</span></span> 
  
<span data-ttu-id="9d775-157">Le caratteristiche includono:</span><span class="sxs-lookup"><span data-stu-id="9d775-157">Features include:</span></span> 
  
- <span data-ttu-id="9d775-158">Pianificazione della capacità e dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="9d775-158">Capacity planning and sizing.</span></span> 
    
- <span data-ttu-id="9d775-159">Acquisizione e installazione del server.</span><span class="sxs-lookup"><span data-stu-id="9d775-159">Server acquisition and setup.</span></span> 
    
- <span data-ttu-id="9d775-160">Distribuzione.</span><span class="sxs-lookup"><span data-stu-id="9d775-160">Deployment.</span></span> 
    
- <span data-ttu-id="9d775-161">Scalabilità orizzontale, applicazione di patch e operazioni.</span><span class="sxs-lookup"><span data-stu-id="9d775-161">Scaling out, patching, and operations.</span></span> 
    
- <span data-ttu-id="9d775-162">Backup dei dati.</span><span class="sxs-lookup"><span data-stu-id="9d775-162">Backing up data.</span></span> 
    
- <span data-ttu-id="9d775-163">Gestione di un ambiente di ripristino di emergenza.</span><span class="sxs-lookup"><span data-stu-id="9d775-163">Maintaining a disaster recovery environment.</span></span> 
    
- <span data-ttu-id="9d775-164">Le personalizzazioni non sono limitate.</span><span class="sxs-lookup"><span data-stu-id="9d775-164">Customizations are not limited.</span></span> 
    
### <a name="deployment-type-is-best-for---"></a><span data-ttu-id="9d775-165">Il tipo di distribuzione è consigliabile.</span><span class="sxs-lookup"><span data-stu-id="9d775-165">Deployment type is best for .</span></span> <span data-ttu-id="9d775-166">.</span><span class="sxs-lookup"><span data-stu-id="9d775-166"></span></span> <span data-ttu-id="9d775-167">.</span><span class="sxs-lookup"><span data-stu-id="9d775-167"></span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="9d775-168">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="9d775-168">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="9d775-169">Condivisione e collaborazione esterne sicure.</span><span class="sxs-lookup"><span data-stu-id="9d775-169">Secure external sharing and collaboration.</span></span> <span data-ttu-id="9d775-170">(Caratteristica univoca!)</span><span class="sxs-lookup"><span data-stu-id="9d775-170">(Unique feature!)</span></span> 
    
- <span data-ttu-id="9d775-171">Intranet: siti di Team, siti personali e collaborazione interna.</span><span class="sxs-lookup"><span data-stu-id="9d775-171">Intranet — Team sites, My Sites, and internal collaboration.</span></span> 
    
- <span data-ttu-id="9d775-172">Archiviazione e controllo delle versioni dei documenti nel cloud.</span><span class="sxs-lookup"><span data-stu-id="9d775-172">Document storage and versioning in the cloud.</span></span> 
    
- <span data-ttu-id="9d775-173">Sito Web di base pubblico.</span><span class="sxs-lookup"><span data-stu-id="9d775-173">Basic public-facing website.</span></span> 
    
<span data-ttu-id="9d775-174">Funzionalità aggiuntive con i piani di sottoscrizione dedicati a Office 365:</span><span class="sxs-lookup"><span data-stu-id="9d775-174">Additional features with Office 365 Dedicated subscription plans:</span></span> 
  
- <span data-ttu-id="9d775-175">Apparecchiature di Microsoft datacenter dedicate all'organizzazione e non condivise con nessun'altra organizzazione.</span><span class="sxs-lookup"><span data-stu-id="9d775-175">Microsoft datacenter equipment that is dedicated to your organization and not shared with any other organization.</span></span> 
    
- <span data-ttu-id="9d775-176">Ogni ambiente del cliente risiede in una rete fisicamente separata.</span><span class="sxs-lookup"><span data-stu-id="9d775-176">Each customer environment resides in a physically separate network.</span></span> 
    
- <span data-ttu-id="9d775-177">Comunicazione client su una connessione VPN protetta da IPSec o privata.</span><span class="sxs-lookup"><span data-stu-id="9d775-177">Client communication across an IPSec-secured VPN or customer-owned private connection.</span></span> <span data-ttu-id="9d775-178">L'autenticazione a due fattori è facoltativa.</span><span class="sxs-lookup"><span data-stu-id="9d775-178">Two-factor authentication is optional.</span></span> 
    
- <span data-ttu-id="9d775-179">ITAR-piani di supporto.</span><span class="sxs-lookup"><span data-stu-id="9d775-179">ITAR-support plans.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="9d775-180">Ibrido con Office 365</span><span class="sxs-lookup"><span data-stu-id="9d775-180">Hybrid with Office 365</span></span>

- <span data-ttu-id="9d775-181">Utilizzare Office 365 per la condivisione e la collaborazione esterne invece di configurare un ambiente Extranet.</span><span class="sxs-lookup"><span data-stu-id="9d775-181">Use Office 365 for external sharing and collaboration instead of setting up an extranet environment.</span></span> 
    
- <span data-ttu-id="9d775-182">Spostare i siti personali (OneDrive for business) nel cloud per semplificare l'accesso dei file da parte degli utenti in remoto.</span><span class="sxs-lookup"><span data-stu-id="9d775-182">Move My Sites (OneDrive for Business) to the cloud to make it easier for users to access their files remotely.</span></span> 
    
- <span data-ttu-id="9d775-183">Avviare nuovi siti del team in Office 365.</span><span class="sxs-lookup"><span data-stu-id="9d775-183">Start new team sites in Office 365.</span></span> 
    
- <span data-ttu-id="9d775-184">Integrazione di un sito di Office 365 con l'ambiente di SharePoint BCS locale.</span><span class="sxs-lookup"><span data-stu-id="9d775-184">Integrate an Office 365 site with on-premises BCS SharePoint environment.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="9d775-185">Azure</span><span class="sxs-lookup"><span data-stu-id="9d775-185">Azure</span></span>

- <span data-ttu-id="9d775-186">SharePoint per siti Internet: siti di riorientamento pubblico.</span><span class="sxs-lookup"><span data-stu-id="9d775-186">SharePoint for Internet Sites — Public facing sites.</span></span> <span data-ttu-id="9d775-187">Trarre vantaggio da Azure AD per gli account dei clienti e l'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="9d775-187">Take advantage of Azure AD for customer accounts and authentication.</span></span> 
    
- <span data-ttu-id="9d775-188">Ambienti di sviluppo, testing e gestione temporanea: provisioning e deprovisioning rapido di interi ambienti.</span><span class="sxs-lookup"><span data-stu-id="9d775-188">Developer, test, and staging environments — Quickly provision and deprovision entire environments.</span></span> 
    
- <span data-ttu-id="9d775-189">Applicazioni ibride: applicazioni che si estendono al Data Center e al cloud.</span><span class="sxs-lookup"><span data-stu-id="9d775-189">Hybrid applications — Applications that span your datacenter and the cloud.</span></span> 
    
- <span data-ttu-id="9d775-190">Ambiente di ripristino di emergenza: ripristino rapido da una situazione di emergenza.</span><span class="sxs-lookup"><span data-stu-id="9d775-190">Disaster recovery environment — Quickly recover from a disaster.</span></span> <span data-ttu-id="9d775-191">Paghi solo per l'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="9d775-191">Pay only for use.</span></span> 
    
- <span data-ttu-id="9d775-192">Farm che richiedono rapporti profondi o di controllo.</span><span class="sxs-lookup"><span data-stu-id="9d775-192">Farms that require deep reporting or auditing.</span></span> 
    
- <span data-ttu-id="9d775-193">Web Analytics.</span><span class="sxs-lookup"><span data-stu-id="9d775-193">Web analytics.</span></span> 
    
- <span data-ttu-id="9d775-194">Crittografia dei dati a Rest (i dati vengono crittografati nei database SQL).</span><span class="sxs-lookup"><span data-stu-id="9d775-194">Data encryption at rest (data is encrypted in the SQL databases).</span></span> 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a><span data-ttu-id="9d775-195">Crittografia dei dati a Rest (i dati vengono crittografati nei database SQL)</span><span class="sxs-lookup"><span data-stu-id="9d775-195">Data encryption at rest (data is encrypted in the SQL databases)</span></span>

- <span data-ttu-id="9d775-196">Farm nazionali (quando i dati devono risiedere all'interno di una giurisdizione).</span><span class="sxs-lookup"><span data-stu-id="9d775-196">In-country farms (when data is required to reside within a jurisdiction).</span></span> 
    
- <span data-ttu-id="9d775-197">Soluzioni di BI complesse che devono risiedere vicino ai dati di BI.</span><span class="sxs-lookup"><span data-stu-id="9d775-197">Complex BI solutions that must reside close to BI data.</span></span> 
    
- <span data-ttu-id="9d775-198">Soluzioni cloud private.</span><span class="sxs-lookup"><span data-stu-id="9d775-198">Private cloud solutions.</span></span> 
    
- <span data-ttu-id="9d775-199">Soluzioni altamente personalizzate.</span><span class="sxs-lookup"><span data-stu-id="9d775-199">Highly customized solutions.</span></span> 
    
- <span data-ttu-id="9d775-200">Soluzioni legacy con componenti di terze parti che dipendono da hardware e software che non sono supportati nei servizi di infrastruttura di Azure.</span><span class="sxs-lookup"><span data-stu-id="9d775-200">Legacy solutions with third-party components that depend on hardware and software that are not supported on Azure Infrastructure Services.</span></span> 
    
- <span data-ttu-id="9d775-201">Restrizioni sulla privacy che impediscono la sincronizzazione degli account di Active Directory con Azure Active Directory (un requisito per Office 365).</span><span class="sxs-lookup"><span data-stu-id="9d775-201">Privacy restrictions that prevent synchronization of Active Directory accounts with Azure Active Directory (a requirement for Office 365).</span></span> 
    
- <span data-ttu-id="9d775-202">Organizzazioni che preferiscono il controllo dell'intera piattaforma e della soluzione.</span><span class="sxs-lookup"><span data-stu-id="9d775-202">Organizations that prefer control of the entire platform and solution.</span></span> 
    
### <a name="license-requirements"></a><span data-ttu-id="9d775-203">Requisiti di licenza</span><span class="sxs-lookup"><span data-stu-id="9d775-203">License requirements</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="9d775-204">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="9d775-204">SharePoint 2013 in Office 365</span></span>

<span data-ttu-id="9d775-205">Modello di sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="9d775-205">Subscription model.</span></span> <span data-ttu-id="9d775-206">Non sono necessarie licenze aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="9d775-206">No additional licenses needed.</span></span> 
  
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="9d775-207">Ibrido con Office 365</span><span class="sxs-lookup"><span data-stu-id="9d775-207">Hybrid with Office 365</span></span>

- <span data-ttu-id="9d775-208">Office 365: modello di sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="9d775-208">Office 365 — Subscription model.</span></span> <span data-ttu-id="9d775-209">Non sono necessarie licenze aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="9d775-209">No additional licenses needed.</span></span> 
    
- <span data-ttu-id="9d775-210">Locale: vengono applicate tutte le licenze locali.</span><span class="sxs-lookup"><span data-stu-id="9d775-210">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="9d775-211">Azure</span><span class="sxs-lookup"><span data-stu-id="9d775-211">Azure</span></span>

-  <span data-ttu-id="9d775-212">Sottoscrizione di Azure (include il sistema operativo del server)</span><span class="sxs-lookup"><span data-stu-id="9d775-212">Azure subscription (includes the server operating system)</span></span>
    
- <span data-ttu-id="9d775-213">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9d775-213">SQL Server</span></span> 
    
- <span data-ttu-id="9d775-214">Licenza del server di SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="9d775-214">SharePoint 2013 Server License</span></span> 
    
- <span data-ttu-id="9d775-215">Licenza di accesso client di SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="9d775-215">SharePoint 2013 Client Access License</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="9d775-216">Locali</span><span class="sxs-lookup"><span data-stu-id="9d775-216">On premises</span></span>

- <span data-ttu-id="9d775-217">Sistema operativo del server</span><span class="sxs-lookup"><span data-stu-id="9d775-217">Server operating system</span></span> 
    
- <span data-ttu-id="9d775-218">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9d775-218">SQL Server</span></span> 
    
- <span data-ttu-id="9d775-219">Licenza del server di SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="9d775-219">SharePoint 2013 Server License</span></span> 
    
- <span data-ttu-id="9d775-220">Licenza di accesso client di SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="9d775-220">SharePoint 2013 Client Access License</span></span> 
    
### <a name="architecture-tasks"></a><span data-ttu-id="9d775-221">Attività dell'architettura</span><span class="sxs-lookup"><span data-stu-id="9d775-221">Architecture tasks</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="9d775-222">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="9d775-222">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="9d775-223">Pianificare e progettare l'integrazione di directory.</span><span class="sxs-lookup"><span data-stu-id="9d775-223">Plan and design directory integration.</span></span> <span data-ttu-id="9d775-224">Due opzioni.</span><span class="sxs-lookup"><span data-stu-id="9d775-224">Two options.</span></span> <span data-ttu-id="9d775-225">Entrambe le opzioni possono essere distribuite in locale o in Azure: sincronizzazione password (richiede un server a 1 64 bit).</span><span class="sxs-lookup"><span data-stu-id="9d775-225">Either option can be deployed on premises or in Azure: Password sync (requires one 64-bit server).</span></span> <span data-ttu-id="9d775-226">SSO (richiede ADFS e più server).</span><span class="sxs-lookup"><span data-stu-id="9d775-226">SSO (requires AD FS and multiple servers).</span></span> 
    
- <span data-ttu-id="9d775-227">Garantire la disponibilità e la capacità della rete attraverso i firewall, i server proxy, i gateway e i collegamenti WAN.</span><span class="sxs-lookup"><span data-stu-id="9d775-227">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span> 
    
- <span data-ttu-id="9d775-228">Acquisizione dei certificati SSL di terze parti per fornire la sicurezza aziendale per le offerte di servizi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="9d775-228">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span> 
    
- <span data-ttu-id="9d775-229">Pianificare il nome del tenant e progettare l'architettura e la governance della raccolta siti.</span><span class="sxs-lookup"><span data-stu-id="9d775-229">Plan the tenant name, and design the site collection architecture and governance.</span></span> 
    
- <span data-ttu-id="9d775-230">Pianificare le personalizzazioni, le soluzioni e le app per SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9d775-230">Plan customizations, solutions, and apps for SharePoint Online.</span></span> 
    
- <span data-ttu-id="9d775-231">Decidere se si desidera connettersi a Office 365 utilizzando il protocollo IPv6 (Internet Protocol 6).</span><span class="sxs-lookup"><span data-stu-id="9d775-231">Decide if you want to connect to Office 365 by using the Internet Protocol 6 (IPv6).</span></span> <span data-ttu-id="9d775-232">Non si tratta di una cosa comune.</span><span class="sxs-lookup"><span data-stu-id="9d775-232">This is not common.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="9d775-233">Ibrido con Office 365</span><span class="sxs-lookup"><span data-stu-id="9d775-233">Hybrid with Office 365</span></span>

<span data-ttu-id="9d775-234">Oltre alle attività sia per gli ambienti Office 365 che per quelli locali:</span><span class="sxs-lookup"><span data-stu-id="9d775-234">In addition to tasks for both the Office 365 and on-premises environments:</span></span> 
  
- <span data-ttu-id="9d775-235">Determinare la quantità di integrazione delle caratteristiche desiderata e scegliere la topologia ibrida.</span><span class="sxs-lookup"><span data-stu-id="9d775-235">Determine how much feature integration you want and choose the hybrid topology.</span></span> <span data-ttu-id="9d775-236">Vedere questo poster del modello: quale topologia ibrida utilizzare?</span><span class="sxs-lookup"><span data-stu-id="9d775-236">See this model poster: Which hybrid topology should I use?</span></span> 
    
- <span data-ttu-id="9d775-237">Se necessario, determinare quale dispositivo server proxy verrà utilizzato.</span><span class="sxs-lookup"><span data-stu-id="9d775-237">If required, determine which proxy server device will be used.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="9d775-238">Azure</span><span class="sxs-lookup"><span data-stu-id="9d775-238">Azure</span></span>

<span data-ttu-id="9d775-239">Progettare l'ambiente di rete di Azure:</span><span class="sxs-lookup"><span data-stu-id="9d775-239">Design the Azure network environment:</span></span> 
  
- <span data-ttu-id="9d775-240">Rete virtuale all'interno di Azure, incluse le subnet.</span><span class="sxs-lookup"><span data-stu-id="9d775-240">Virtual network within Azure, including subnets.</span></span> 
    
- <span data-ttu-id="9d775-241">Ambiente di dominio e integrazione con i server locali.</span><span class="sxs-lookup"><span data-stu-id="9d775-241">Domain environment and integration with on-premises servers.</span></span> 
    
- <span data-ttu-id="9d775-242">Indirizzi IP e DNS.</span><span class="sxs-lookup"><span data-stu-id="9d775-242">IP addresses and DNS.</span></span> 
    
- <span data-ttu-id="9d775-243">Gruppi di affinità e account di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="9d775-243">Affinity groups and storage accounts.</span></span> 
    
<span data-ttu-id="9d775-244">Progettare l'ambiente di SharePoint in Azure:</span><span class="sxs-lookup"><span data-stu-id="9d775-244">Design the SharePoint environment in Azure:</span></span> 
  
- <span data-ttu-id="9d775-245">Topologia della farm di SharePoint e architettura logica.</span><span class="sxs-lookup"><span data-stu-id="9d775-245">SharePoint farm topology and logical architecture.</span></span> 
    
-  <span data-ttu-id="9d775-246">I set di disponibilità di Azure e i domini di aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="9d775-246">Azure availability sets and update domains.</span></span>
    
- <span data-ttu-id="9d775-247">Dimensioni delle macchine virtuali.</span><span class="sxs-lookup"><span data-stu-id="9d775-247">Virtual machines sizes.</span></span> 
    
- <span data-ttu-id="9d775-248">Endpoint con bilanciamento del carico.</span><span class="sxs-lookup"><span data-stu-id="9d775-248">Load balanced endpoint.</span></span> 
    
- <span data-ttu-id="9d775-249">Endpoint esterni per l'accesso pubblico, se questo è preferibile.</span><span class="sxs-lookup"><span data-stu-id="9d775-249">External endpoints for public access, if that is preferable.</span></span> 
    
- <span data-ttu-id="9d775-250">Ambiente di ripristino di emergenza.</span><span class="sxs-lookup"><span data-stu-id="9d775-250">Disaster recovery environment.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="9d775-251">Locali</span><span class="sxs-lookup"><span data-stu-id="9d775-251">On premises</span></span>

<span data-ttu-id="9d775-252">Progettare l'ambiente di SharePoint in un ambiente locale esistente:</span><span class="sxs-lookup"><span data-stu-id="9d775-252">Design the SharePoint environment in an existing on-premises environment:</span></span> 
  
- <span data-ttu-id="9d775-253">Topologia della farm di SharePoint e architettura logica.</span><span class="sxs-lookup"><span data-stu-id="9d775-253">SharePoint farm topology and logical architecture.</span></span> 
    
- <span data-ttu-id="9d775-254">Hardware del server.</span><span class="sxs-lookup"><span data-stu-id="9d775-254">Server hardware.</span></span> 
    
- <span data-ttu-id="9d775-255">Ambiente virtuale, se utilizzato.</span><span class="sxs-lookup"><span data-stu-id="9d775-255">Virtual environment, if used.</span></span> 
    
- <span data-ttu-id="9d775-256">Bilanciamento del carico.</span><span class="sxs-lookup"><span data-stu-id="9d775-256">Load balancing.</span></span> 
    
- <span data-ttu-id="9d775-257">Integrazione con servizi di dominio Active Directory e DNS.</span><span class="sxs-lookup"><span data-stu-id="9d775-257">Integration with AD DS and DNS.</span></span> 
    
- <span data-ttu-id="9d775-258">Ambiente di ripristino di emergenza.</span><span class="sxs-lookup"><span data-stu-id="9d775-258">Disaster recovery environment.</span></span> 
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="9d775-259">Responsabilità per i professionisti IT</span><span class="sxs-lookup"><span data-stu-id="9d775-259">IT pro responsibilities</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="9d775-260">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="9d775-260">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="9d775-261">Garantire che le workstation degli utenti soddisfino i prerequisiti client di Office 365.</span><span class="sxs-lookup"><span data-stu-id="9d775-261">Ensure user workstations meet Office 365 client prerequisites.</span></span> 
    
- <span data-ttu-id="9d775-262">Implementare il piano di integrazione della directory.</span><span class="sxs-lookup"><span data-stu-id="9d775-262">Implement the directory integration plan.</span></span> 
    
- <span data-ttu-id="9d775-263">Pianificare e implementare i record DNS interni ed esterni e il routing.</span><span class="sxs-lookup"><span data-stu-id="9d775-263">Plan and implement internal and external DNS records and routing.</span></span> 
    
- <span data-ttu-id="9d775-264">Configurare il proxy o il firewall per i requisiti di indirizzo IP e URL di Office 365.</span><span class="sxs-lookup"><span data-stu-id="9d775-264">Configure the proxy or firewall for Office 365 IP address and URL requirements.</span></span> 
    
- <span data-ttu-id="9d775-265">Creare e assegnare autorizzazioni per le raccolte siti.</span><span class="sxs-lookup"><span data-stu-id="9d775-265">Create and assign permissions to site collections.</span></span> 
    
- <span data-ttu-id="9d775-266">Implementare le personalizzazioni, le soluzioni e le app per SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9d775-266">Implement customizations, solutions, and apps for SharePoint Online.</span></span> 
    
- <span data-ttu-id="9d775-267">Monitorare la disponibilità della rete e identificare i colli di bottiglia possibili.</span><span class="sxs-lookup"><span data-stu-id="9d775-267">Monitor network availability and identify possible bottlenecks.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="9d775-268">Ibrido con Office 365</span><span class="sxs-lookup"><span data-stu-id="9d775-268">Hybrid with Office 365</span></span>

<span data-ttu-id="9d775-269">Oltre alle attività sia per gli ambienti Office 365 che per quelli locali:</span><span class="sxs-lookup"><span data-stu-id="9d775-269">In addition to tasks for both the Office 365 and on-premises environments:</span></span> 
  
- <span data-ttu-id="9d775-270">Configurare il dispositivo server proxy, se necessario.</span><span class="sxs-lookup"><span data-stu-id="9d775-270">Configure the proxy server device, if required.</span></span> 
    
- <span data-ttu-id="9d775-271">Configurare l'infrastruttura di gestione delle identità ibride: SSO e l'autenticazione da server a server tra i due ambienti.</span><span class="sxs-lookup"><span data-stu-id="9d775-271">Configure the hybrid identity management infrastructure: SSO and server-to-server authentication between the two environments.</span></span> 
    
- <span data-ttu-id="9d775-272">Configurare l'integrazione delle funzionalità scelte: Search, BCS, Duet Enterprise online.</span><span class="sxs-lookup"><span data-stu-id="9d775-272">Configure the integration of chosen features: Search, BCS, Duet Enterprise Online.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="9d775-273">Azure</span><span class="sxs-lookup"><span data-stu-id="9d775-273">Azure</span></span>

<span data-ttu-id="9d775-274">Distribuire e gestire l'ambiente di Azure e SharePoint:</span><span class="sxs-lookup"><span data-stu-id="9d775-274">Deploy and manage the Azure and SharePoint environment:</span></span> 
  
- <span data-ttu-id="9d775-275">Implementare e gestire l'ambiente di rete di Azure.</span><span class="sxs-lookup"><span data-stu-id="9d775-275">Implement and manage the Azure network environment.</span></span> 
    
- <span data-ttu-id="9d775-276">Distribuire l'ambiente di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9d775-276">Deploy the SharePoint environment.</span></span> 
    
- <span data-ttu-id="9d775-277">Aggiornare i server della farm di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9d775-277">Update SharePoint farm servers.</span></span> 
    
- <span data-ttu-id="9d775-278">Aggiungere o arrestare macchine virtuali secondo necessità in base all'utilizzo della farm.</span><span class="sxs-lookup"><span data-stu-id="9d775-278">Add or shut down virtual machines as needed based on farm utilization.</span></span> 
    
- <span data-ttu-id="9d775-279">Aumentare o diminuire le dimensioni delle macchine virtuali, se necessario.</span><span class="sxs-lookup"><span data-stu-id="9d775-279">Increase or decrease virtual machine sizes, as needed.</span></span> 
    
- <span data-ttu-id="9d775-280">Eseguire il backup dell'ambiente di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9d775-280">Back up the SharePoint environment.</span></span> 
    
- <span data-ttu-id="9d775-281">Implementare l'ambiente di ripristino di emergenza e il protocollo.</span><span class="sxs-lookup"><span data-stu-id="9d775-281">Implement the disaster recovery environment and protocol.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="9d775-282">Locali</span><span class="sxs-lookup"><span data-stu-id="9d775-282">On premises</span></span>

<span data-ttu-id="9d775-283">Distribuire e gestire l'ambiente SharePoint in locale:</span><span class="sxs-lookup"><span data-stu-id="9d775-283">Deploy and manage the SharePoint on premises environment:</span></span> 
  
- <span data-ttu-id="9d775-284">Server di provisioning.</span><span class="sxs-lookup"><span data-stu-id="9d775-284">Provision servers.</span></span> 
    
- <span data-ttu-id="9d775-285">Distribuire l'ambiente di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9d775-285">Deploy the SharePoint environment.</span></span> 
    
- <span data-ttu-id="9d775-286">Aggiornare i server della farm di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9d775-286">Update SharePoint farm servers.</span></span> 
    
- <span data-ttu-id="9d775-287">Aggiungere o rimuovere i server della farm in base all'utilizzo della farm.</span><span class="sxs-lookup"><span data-stu-id="9d775-287">Add or remove farm servers as needed based on farm utilization.</span></span> 
    
- <span data-ttu-id="9d775-288">Eseguire il backup dell'ambiente di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9d775-288">Back up the SharePoint environment.</span></span> 
    
- <span data-ttu-id="9d775-289">Implementare l'ambiente di ripristino di emergenza e il protocollo.</span><span class="sxs-lookup"><span data-stu-id="9d775-289">Implement the disaster recovery environment and protocol.</span></span> 
    
## <a name="three-typical-workloads-to-move-to-azure"></a><span data-ttu-id="9d775-290">Tre carichi di lavoro tipici da spostare in Azure</span><span class="sxs-lookup"><span data-stu-id="9d775-290">Three typical workloads to move to Azure</span></span>

### <a name="office-365-plus-directory-components-in-azure"></a><span data-ttu-id="9d775-291">Componenti di directory di Office 365 Plus in Azure</span><span class="sxs-lookup"><span data-stu-id="9d775-291">Office 365 plus Directory Components in Azure</span></span>

<span data-ttu-id="9d775-292">La distribuzione di componenti di integrazione della directory di Office 365 in Azure è più veloce perché è in grado di distribuire macchine virtuali su richiesta.</span><span class="sxs-lookup"><span data-stu-id="9d775-292">Deploying Office 365 directory integration components in Azure is faster because it can deploy virtual machines on-demand.</span></span> 
  
#### <a name="directory-synchronization-server-only"></a><span data-ttu-id="9d775-293">Solo server di sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="9d775-293">Directory synchronization server only</span></span>

<span data-ttu-id="9d775-294">Invece di distribuire il server di sincronizzazione della directory a 64 bit nell'ambiente locale, eseguire il provisioning di una macchina virtuale in Azure.</span><span class="sxs-lookup"><span data-stu-id="9d775-294">Instead of deploying the 64-bit directory synchronization server in your on-premises environment, provision a virtual machine in Azure instead.</span></span> 
  
<span data-ttu-id="9d775-295">Nel diagramma di accompagnamento viene mostrato SharePoint Online con un tenant di Azure Active Directory, che sincronizza i nomi degli account e le password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9d775-295">The accompanying diagram shows SharePoint Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
  
#### <a name="directory-synchronization-plus-ad-fs"></a><span data-ttu-id="9d775-296">Sincronizzazione della directory e AD FS</span><span class="sxs-lookup"><span data-stu-id="9d775-296">Directory synchronization plus AD FS</span></span>

<span data-ttu-id="9d775-297">Questa opzione consente di supportare le identità federative di Office 365 senza aggiungere hardware all'infrastruttura locale.</span><span class="sxs-lookup"><span data-stu-id="9d775-297">This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure.</span></span> <span data-ttu-id="9d775-298">Inoltre, fornisce resilienza se l'ambiente Active Directory locale non è disponibile.</span><span class="sxs-lookup"><span data-stu-id="9d775-298">It also provides resiliency if the on-premises Active Directory environment is unavailable.</span></span> 
  
- <span data-ttu-id="9d775-299">I componenti di integrazione della directory risiedono in Azure.</span><span class="sxs-lookup"><span data-stu-id="9d775-299">Directory integration components reside in Azure.</span></span> 
    
- <span data-ttu-id="9d775-300">AD FS viene pubblicato su Internet tramite proxy ADFS in Azure.</span><span class="sxs-lookup"><span data-stu-id="9d775-300">AD FS is published to the Internet through AD FS proxies in Azure.</span></span> 
    
- <span data-ttu-id="9d775-301">Il traffico di autenticazione del client, per gli utenti che si connettono da qualsiasi percorso, è gestito da server ADFS e da proxy distribuiti in Azure.</span><span class="sxs-lookup"><span data-stu-id="9d775-301">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed on Azure.</span></span> 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a><span data-ttu-id="9d775-302">Sito Internet pubblico e Azure AD per l'autenticazione dei clienti</span><span class="sxs-lookup"><span data-stu-id="9d775-302">Public-facing Internet site and Azure AD for customer authentication</span></span>

<span data-ttu-id="9d775-303">Approfitta della possibilità di scalare facilmente la domanda inserendo il sito Internet in Azure.</span><span class="sxs-lookup"><span data-stu-id="9d775-303">Take advantage of the ability to easily scale to demand by placing your Internet site in Azure.</span></span> <span data-ttu-id="9d775-304">Usare Azure AD per archiviare gli account dei clienti.</span><span class="sxs-lookup"><span data-stu-id="9d775-304">Use Azure AD to store customer accounts.</span></span> 
  
#### <a name="azure-advantages-for-internet-sites"></a><span data-ttu-id="9d775-305">Vantaggi di Azure per i siti Internet</span><span class="sxs-lookup"><span data-stu-id="9d775-305">Azure advantages for Internet sites</span></span>

- <span data-ttu-id="9d775-306">Pagare solo le risorse necessarie per la scalabilità del numero di macchine virtuali in base all'utilizzo della farm.</span><span class="sxs-lookup"><span data-stu-id="9d775-306">Pay only for the resources you need by scaling the number of virtual machines based on farm utilization.</span></span> 
    
- <span data-ttu-id="9d775-307">Aggiungere rapporti profondi e analisi Web.</span><span class="sxs-lookup"><span data-stu-id="9d775-307">Add deep reporting and web analytics.</span></span> 
    
- <span data-ttu-id="9d775-308">Concentrarsi sullo sviluppo di un sito importante anziché sull'infrastruttura di costruzione.</span><span class="sxs-lookup"><span data-stu-id="9d775-308">Focus on developing a great site rather than building infrastructure.</span></span> 
    
#### <a name="azure-ad"></a><span data-ttu-id="9d775-309">Azure AD</span><span class="sxs-lookup"><span data-stu-id="9d775-309">Azure AD</span></span>

<span data-ttu-id="9d775-310">Azure AD offre funzionalità di gestione delle identità e controllo di accesso per i servizi cloud.</span><span class="sxs-lookup"><span data-stu-id="9d775-310">Azure AD provides identity management and access control capabilities for cloud services.</span></span> <span data-ttu-id="9d775-311">Le funzionalità includono un archivio basato sul cloud per i dati di directory e un set di base di servizi di identità, tra cui processi di accesso degli utenti, servizi di autenticazione e AD FS.</span><span class="sxs-lookup"><span data-stu-id="9d775-311">Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS.</span></span> <span data-ttu-id="9d775-312">I servizi Identity inclusi in Azure AD si integrano facilmente con le distribuzioni di Active Directory locali e supportano completamente i provider di identità di terze parti.</span><span class="sxs-lookup"><span data-stu-id="9d775-312">The identity services that are included with Azure AD easily integrate with your on-premises Active Directory deployments and fully support third-party identity providers.</span></span> 
  
<span data-ttu-id="9d775-313">Nel diagramma di accompagnamento viene illustrata la configurazione delle aree e dell'autenticazione importanti per i siti con accesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="9d775-313">The accompanying diagram shows the configuration of zones and authentication that is important for Internet-facing sites.</span></span> <span data-ttu-id="9d775-314">Nel diagramma viene visualizzato il tenant di Azure Active Directory, che contiene una farm di SharePoint in Azure con due aree:</span><span class="sxs-lookup"><span data-stu-id="9d775-314">The diagram shows the Azure Active Directory Tenant, which contains a SharePoint Farm on Azure with two zones:</span></span> 
  
- <span data-ttu-id="9d775-315">Un'area Internet che interagisce con utenti e visitatori anonimi e autenticati all'esterno della rete</span><span class="sxs-lookup"><span data-stu-id="9d775-315">An Internet zone that interacts with Anonymous and Authenticated visitors and customers outside the network</span></span> 
    
- <span data-ttu-id="9d775-316">Un'area predefinita che contiene NTLM per la ricerca per indicizzazione e l'autenticazione di Windows che interagiscono con la distribuzione di Active Directory locale su un tunnel VPN.</span><span class="sxs-lookup"><span data-stu-id="9d775-316">A default zone that contains NTLM for Crawl and Windows Authentication that interacts with your on-premises Active Directory deployment over a VPN tunnel.</span></span> 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a><span data-ttu-id="9d775-317">Farm locale e ripristino di emergenza in Azure</span><span class="sxs-lookup"><span data-stu-id="9d775-317">On-premises Farm plus Disaster Recovery in Azure</span></span>

<span data-ttu-id="9d775-318">Scegliere un'opzione di ripristino di emergenza che corrisponda ai requisiti aziendali.</span><span class="sxs-lookup"><span data-stu-id="9d775-318">Choose a disaster recovery option that matches your business requirements.</span></span> <span data-ttu-id="9d775-319">In Azure sono disponibili opzioni di ingresso per le aziende per iniziare a usare il ripristino di emergenza e le opzioni avanzate per aziende con requisiti di resilienza elevati.</span><span class="sxs-lookup"><span data-stu-id="9d775-319">Azure provides entry-level options for companies getting started with disaster recovery and advanced options for enterprises with high resiliency requirements.</span></span> 
  
#### <a name="cold-standby"></a><span data-ttu-id="9d775-320">Standby freddo</span><span class="sxs-lookup"><span data-stu-id="9d775-320">Cold standby</span></span>

- <span data-ttu-id="9d775-321">La farm viene creata completamente, ma le macchine virtuali sono arrestate.</span><span class="sxs-lookup"><span data-stu-id="9d775-321">The farm is fully built, but the virtual machines are stopped.</span></span> <span data-ttu-id="9d775-322">(Paghi solo quando è in esecuzione!)</span><span class="sxs-lookup"><span data-stu-id="9d775-322">(You're paying only when they're running!)</span></span> 
    
- <span data-ttu-id="9d775-323">La gestione dell'ambiente include l'avvio delle macchine virtuali di tanto in tanto, l'applicazione di patch, l'aggiornamento e la verifica dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="9d775-323">Maintaining the environment includes starting the virtual machines from time-to-time, patching, updating, and verifying the environment.</span></span> 
    
- <span data-ttu-id="9d775-324">Avviare l'ambiente completo in caso di calamità.</span><span class="sxs-lookup"><span data-stu-id="9d775-324">Start the full environment in the event of a disaster.</span></span> 
    
#### <a name="warm-standby"></a><span data-ttu-id="9d775-325">Standby caldo</span><span class="sxs-lookup"><span data-stu-id="9d775-325">Warm standby</span></span>

- <span data-ttu-id="9d775-326">Include una farm di piccole dimensioni di cui è stato eseguito il provisioning e l'esecuzione.</span><span class="sxs-lookup"><span data-stu-id="9d775-326">This includes a small farm that is provisioned and running.</span></span> 
    
- <span data-ttu-id="9d775-327">La farm può servire immediatamente gli utenti in caso di failover.</span><span class="sxs-lookup"><span data-stu-id="9d775-327">The farm can immediately serve users in the event of a failover.</span></span> 
    
- <span data-ttu-id="9d775-328">Scalare rapidamente la farm per servire la base di utenti completa.</span><span class="sxs-lookup"><span data-stu-id="9d775-328">Scale out the farm quickly to serve the full user base.</span></span> 
    
#### <a name="hot-standby"></a><span data-ttu-id="9d775-329">Standby caldo</span><span class="sxs-lookup"><span data-stu-id="9d775-329">Hot standby</span></span>

<span data-ttu-id="9d775-330">Viene effettuato il provisioning e l'esecuzione di una farm di dimensioni complete in modalità standby.</span><span class="sxs-lookup"><span data-stu-id="9d775-330">A fully-sized farm is provisioned and running on standby.</span></span> 
  
<span data-ttu-id="9d775-331">Nel diagramma di accompagnamento viene illustrata una farm locale che interagisce con l'ambiente di ripristino di emergenza di SharePoint in Azure.</span><span class="sxs-lookup"><span data-stu-id="9d775-331">The accompanying diagram shows an on-premises farm interacting with the SharePoint Disaster Recovery Environment on Azure.</span></span> <span data-ttu-id="9d775-332">Nei database locali viene utilizzato il log shipping di SQL Server tramite il tunnel VPN per accedere all'ambiente di ripristino di emergenza di SharePoint, che include due server di database SQL che contengono i database di SharePoint, due server front-end Web e due SharePoint Server applicazioni.</span><span class="sxs-lookup"><span data-stu-id="9d775-332">The on-premises databases use SQL Server Log Shipping over the VPN tunnel to access the SharePoint Disaster Recovery environment, which includes two SQL database servers that contain the SharePoint databases, two Web Front End servers, and two SharePoint Application servers.</span></span> 
  

