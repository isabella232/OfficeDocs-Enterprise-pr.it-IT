---
title: Diagramma accessibile - opzioni della piattaforma Microsoft SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: "In questo articolo è una versione testo accessibile del diagramma denominato opzioni della piattaforma Microsoft SharePoint 2013."
ms.openlocfilehash: 9cd282cc723376f85fe2cbc5a439ee24fd2ab883
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a><span data-ttu-id="9e2c9-103">Diagramma accessibile - opzioni della piattaforma Microsoft SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="9e2c9-103">Accessible diagram - Microsoft SharePoint 2013 Platform Options</span></span>

<span data-ttu-id="9e2c9-104">**Riepilogo:** In questo articolo è una versione testo accessibile del diagramma denominato opzioni della piattaforma Microsoft SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-104">**Summary:** This article is an accessible text version of the diagram named Microsoft SharePoint 2013 Platform Options.</span></span>
  
<span data-ttu-id="9e2c9-105">Quali decisori aziendali (hanno) e i progettisti devono essere a conoscenza di Office 365, Microsoft Azure e le distribuzioni locali.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-105">What business decision makers (BDMs) and architects need to know about Office 365, Microsoft Azure, and on-premises deployments.</span></span> 
  
<span data-ttu-id="9e2c9-106">Questo poster composta da due sezioni:</span><span class="sxs-lookup"><span data-stu-id="9e2c9-106">This poster has two sections:</span></span> 
  
- <span data-ttu-id="9e2c9-107">Un confronto tra quattro diverse distribuzioni per SharePoint 2013: SharePoint in Office 365, un ambiente ibrido di Office 365 per una distribuzione locale di SharePoint 2013, Azure e una distribuzione locale di SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-107">A comparison of four different deployments for SharePoint 2013: SharePoint in Office 365, a hybrid of Office 365 with an on-premises deployment of SharePoint 2013, Azure, and an on-premises deployment of SharePoint 2013.</span></span> 
    
- <span data-ttu-id="9e2c9-108">Descrizione delle tre tipici carichi di lavoro per spostare in Azure.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-108">A description of three typical workloads to move to Azure.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a><span data-ttu-id="9e2c9-109">Confronto tra quattro diverse distribuzioni per la piattaforma di SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="9e2c9-109">Comparison of four different deployments for the SharePoint 2013 platform</span></span>

<span data-ttu-id="9e2c9-110">Il confronto vengono fornite informazioni su ogni opzione di distribuzione relative alle aree seguenti:</span><span class="sxs-lookup"><span data-stu-id="9e2c9-110">The comparison provides information about each deployment option related to the following areas:</span></span> 
  
- <span data-ttu-id="9e2c9-111">Panoramica delle funzionalità di distribuzione diversi</span><span class="sxs-lookup"><span data-stu-id="9e2c9-111">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="9e2c9-112">Che cos'è la soluzione migliore per ogni tipo di distribuzione</span><span class="sxs-lookup"><span data-stu-id="9e2c9-112">What each type of deployment is best for</span></span> 
    
- <span data-ttu-id="9e2c9-113">Requisiti relativi alle licenze</span><span class="sxs-lookup"><span data-stu-id="9e2c9-113">License requirements</span></span> 
    
- <span data-ttu-id="9e2c9-114">Attività di architettura necessarie per implementare</span><span class="sxs-lookup"><span data-stu-id="9e2c9-114">Architecture tasks required to implement</span></span> 
    
- <span data-ttu-id="9e2c9-115">IT pro responsabilità per l'implementazione</span><span class="sxs-lookup"><span data-stu-id="9e2c9-115">IT pro responsibilities for implementation</span></span> 
    
### <a name="overview"></a><span data-ttu-id="9e2c9-116">Panoramica</span><span class="sxs-lookup"><span data-stu-id="9e2c9-116">Overview</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="9e2c9-117">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="9e2c9-117">SharePoint 2013 in Office 365</span></span>

<span data-ttu-id="9e2c9-118">Maggiore efficienza e ottimizzare per costo con Office 365 plans multi-tenant.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-118">Gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span> 
  
<span data-ttu-id="9e2c9-119">Nella figura relativa Mostra SharePoint Online con un tenant di Azure Active Directory, che consente di sincronizzare i nomi degli account e password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-119">The accompanying diagram shows SharePoint Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="9e2c9-120">Descrizione delle funzionalità:</span><span class="sxs-lookup"><span data-stu-id="9e2c9-120">Description of features:</span></span> 
  
- <span data-ttu-id="9e2c9-121">Software come servizio (SaaS).</span><span class="sxs-lookup"><span data-stu-id="9e2c9-121">Software as a Service (SaaS).</span></span> 
    
- <span data-ttu-id="9e2c9-122">Set di funzionalità avanzate è sempre aggiornati.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-122">Rich feature set is always up to date.</span></span> 
    
- <span data-ttu-id="9e2c9-123">Include un tenant di Azure Active Directory (può essere utilizzato con altre applicazioni).</span><span class="sxs-lookup"><span data-stu-id="9e2c9-123">Includes an Azure Active Directory tenant (can be used with other applications).</span></span> 
    
- <span data-ttu-id="9e2c9-124">Integrazione di directory include la sincronizzazione dei nomi di account e password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-124">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
    
- <span data-ttu-id="9e2c9-125">Se il single sign-on (SSO) è un requisito, è possibile implementare Active Directory Federation Services (ADFS).</span><span class="sxs-lookup"><span data-stu-id="9e2c9-125">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) can be implemented.</span></span> 
    
- <span data-ttu-id="9e2c9-126">Comunicazione client tramite Internet tramite access autenticata e crittografata (porta 443).</span><span class="sxs-lookup"><span data-stu-id="9e2c9-126">Client communication over the Internet through encrypted and authenticated access (port 443).</span></span> 
    
- <span data-ttu-id="9e2c9-127">Migrazione dei dati è limitata ai quali possono essere caricate tramite Internet.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-127">Data migration is limited to what can be uploaded over the Internet.</span></span> 
    
- <span data-ttu-id="9e2c9-128">Le personalizzazioni: App per Office, SharePoint e SharePoint Designer 2013.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-128">Customizations: Apps for Office, SharePoint, and SharePoint Designer 2013.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="9e2c9-129">Ibrida con Office 365</span><span class="sxs-lookup"><span data-stu-id="9e2c9-129">Hybrid with Office 365</span></span>

<span data-ttu-id="9e2c9-130">Combinare i vantaggi di Office 365 con una distribuzione locale di SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-130">Combine the benefits of Office 365 with an on-premises deployment of SharePoint 2013.</span></span> 
  
<span data-ttu-id="9e2c9-131">Il diagramma accompagnamento Mostra Office 365 con SharePoint Online mediante servizi di integrazione applicativa (BCS) per la connessione a una farm di SharePoint Server 2013 locale.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-131">The accompanying diagram shows Office 365 with SharePoint Online using Business Connectivity Services (BCS) to connect to an on-premises SharePoint Server 2013 farm.</span></span> 
  
<span data-ttu-id="9e2c9-132">Scegliere quali delle seguenti funzionalità per l'integrazione:</span><span class="sxs-lookup"><span data-stu-id="9e2c9-132">Choose which of the following features to integrate:</span></span> 
  
<span data-ttu-id="9e2c9-133">Ricerca di SharePoint</span><span class="sxs-lookup"><span data-stu-id="9e2c9-133">SharePoint Search</span></span> 
  
- <span data-ttu-id="9e2c9-134">Gli utenti possono visualizzare risultati di ricerca di entrambi gli ambienti.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-134">Users can see search results from both environments.</span></span> 
    
- <span data-ttu-id="9e2c9-135">Gli utenti Extranet in remoto possono accedere con un account di Active Directory locale e utilizzare tutte le funzionalità ibrida disponibile.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-135">Extranet users can remotely log on with an on-premises Active Directory account and use all available hybrid functionality.</span></span> 
    
<span data-ttu-id="9e2c9-136">Servizi di integrazione applicativa</span><span class="sxs-lookup"><span data-stu-id="9e2c9-136">BCS</span></span>
  
<span data-ttu-id="9e2c9-p101">SharePoint Online: Gli utenti possono eseguire lettura e operazioni di scrittura. Il servizio servizi di integrazione Applicativa si connette a una farm di SharePoint Server 2013 locale. Il servizio servizi di integrazione Applicativa configurato sul Broker farm locale la connessione all'endpoint del servizio OData locale.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-p101">From SharePoint Online: Users can perform both read and write operations. The BCS service connects to an on-premises SharePoint Server 2013 farm. The BCS service configured on the on-premises farm brokers the connection to on-premises OData Service endpoints.</span></span> 
  
<span data-ttu-id="9e2c9-140">Duet Enterprise Online</span><span class="sxs-lookup"><span data-stu-id="9e2c9-140">Duet Enterprise Online</span></span> 
  
<span data-ttu-id="9e2c9-141">Da SharePoint Online, gli utenti possono eseguire lettura e scrittura operazioni su un sistema SAP locale.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-141">From SharePoint Online, users can perform read and write operations against an on-premises SAP system.</span></span> 
  
#### <a name="azure"></a><span data-ttu-id="9e2c9-142">Azure</span><span class="sxs-lookup"><span data-stu-id="9e2c9-142">Azure</span></span>

<span data-ttu-id="9e2c9-143">Trai vantaggio cloud mantenendo il controllo completo della piattaforma e funzionalità.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-143">Take advantage of the cloud while maintaining full control of the platform and features.</span></span> 
  
<span data-ttu-id="9e2c9-144">Il diagramma accompagnamento Mostra Azure contenente due servizi cloud, una farm di SharePoint 2013 e Windows Server Active Directory con DNS connessione agli utenti tramite Internet o per la connessione ad Active Directory locale tramite tunnel VPN.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-144">The accompanying diagram shows Azure, which contains two cloud services, a SharePoint 2013 farm, and Windows Server Active Directory with DNS connecting to users over the Internet or connecting to on-premises Active Directory via VPN tunnel.</span></span> 
  
<span data-ttu-id="9e2c9-145">Caratteristiche includono:</span><span class="sxs-lookup"><span data-stu-id="9e2c9-145">Features include:</span></span> 
  
-  <span data-ttu-id="9e2c9-146">Azure è una piattaforma che fornisce i servizi di app e l'infrastruttura necessari per ospitare una farm di SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-146">Azure is a platform that provides the infrastructure and app services needed to host a SharePoint 2013 farm.</span></span>
    
- <span data-ttu-id="9e2c9-147">Servizi di infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-147">Infrastructure Services.</span></span> 
    
- <span data-ttu-id="9e2c9-148">Piattaforma cloud nativa migliore per SQL Server e SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-148">Best native cloud platform for SQL Server and SharePoint.</span></span> 
    
- <span data-ttu-id="9e2c9-149">Risorse di elaborazione disponibili quasi immediatamente senza alcun obbligo.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-149">Computing resources are available almost immediately with no commitment.</span></span> 
    
- <span data-ttu-id="9e2c9-150">Concentrarsi sulle applicazioni, invece di infrastruttura e centri dati.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-150">Focus on applications, instead of datacenters and infrastructure.</span></span> 
    
- <span data-ttu-id="9e2c9-151">Ambienti di sviluppo e testing economici.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-151">Inexpensive development and test environments.</span></span> 
    
- <span data-ttu-id="9e2c9-152">Soluzioni di SharePoint possono essere accessibile solo da un ambiente aziendale tramite un tunnel VPN per siti o accessibile da Internet.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-152">SharePoint solutions can be accessible from the Internet or accessible only from a corporate environment through a site-to-site VPN tunnel.</span></span> 
    
- <span data-ttu-id="9e2c9-153">Personalizzazioni non sono limitate.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-153">Customizations are not limited.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="9e2c9-154">In locale</span><span class="sxs-lookup"><span data-stu-id="9e2c9-154">On premises</span></span>

<span data-ttu-id="9e2c9-155">Si è proprietari tutto il contenuto.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-155">You own everything.</span></span> 
  
<span data-ttu-id="9e2c9-156">Nella figura relativa viene illustrato un ambiente locale con server web, server applicazioni e Active Directory la comunicazione con tutti i database e server applicazioni dedicato per la ricerca.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-156">The accompanying diagram shows an on-premises environment with web servers, application servers, and Active Directory communicating with all databases and dedicated application servers for search.</span></span> 
  
<span data-ttu-id="9e2c9-157">Caratteristiche includono:</span><span class="sxs-lookup"><span data-stu-id="9e2c9-157">Features include:</span></span> 
  
- <span data-ttu-id="9e2c9-158">Pianificazione della capacità e dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-158">Capacity planning and sizing.</span></span> 
    
- <span data-ttu-id="9e2c9-159">Acquisizione di server e il programma di installazione.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-159">Server acquisition and setup.</span></span> 
    
- <span data-ttu-id="9e2c9-160">Distribuzione.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-160">Deployment.</span></span> 
    
- <span data-ttu-id="9e2c9-161">Scalabilità orizzontale, applicazione di patch e operazioni.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-161">Scaling out, patching, and operations.</span></span> 
    
- <span data-ttu-id="9e2c9-162">Backup dei dati.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-162">Backing up data.</span></span> 
    
- <span data-ttu-id="9e2c9-163">Gestione di un ambiente di ripristino di emergenza.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-163">Maintaining a disaster recovery environment.</span></span> 
    
- <span data-ttu-id="9e2c9-164">Personalizzazioni non sono limitate.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-164">Customizations are not limited.</span></span> 
    
### <a name="deployment-type-is-best-for---"></a><span data-ttu-id="9e2c9-p102">Tipo di distribuzione è la soluzione migliore per...</span><span class="sxs-lookup"><span data-stu-id="9e2c9-p102">Deployment type is best for . . .</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="9e2c9-168">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="9e2c9-168">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="9e2c9-p103">Proteggere la collaborazione e condivisione esterna. (Caratteristica univoco!)</span><span class="sxs-lookup"><span data-stu-id="9e2c9-p103">Secure external sharing and collaboration. (Unique feature!)</span></span> 
    
- <span data-ttu-id="9e2c9-171">Intranet, ovvero Siti del Team, siti personali e collaborazione interni.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-171">Intranet — Team sites, My Sites, and internal collaboration.</span></span> 
    
- <span data-ttu-id="9e2c9-172">Memorizzazione dei documenti e il controllo delle versioni nel cloud.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-172">Document storage and versioning in the cloud.</span></span> 
    
- <span data-ttu-id="9e2c9-173">Sito Web pubblico Basic.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-173">Basic public-facing website.</span></span> 
    
<span data-ttu-id="9e2c9-174">Funzionalità aggiuntive con piani di sottoscrizione dedicati di Office 365:</span><span class="sxs-lookup"><span data-stu-id="9e2c9-174">Additional features with Office 365 Dedicated subscription plans:</span></span> 
  
- <span data-ttu-id="9e2c9-175">Apparecchiature datacenter Microsoft dedicata all'organizzazione e non condivisa con altre organizzazioni.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-175">Microsoft datacenter equipment that is dedicated to your organization and not shared with any other organization.</span></span> 
    
- <span data-ttu-id="9e2c9-176">Ogni ambiente dei clienti si trova in una rete fisicamente distinta.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-176">Each customer environment resides in a physically separate network.</span></span> 
    
- <span data-ttu-id="9e2c9-p104">Comunicazione client tra un cliente di proprietà privata connessione o protetto con IPSec VPN. Autenticazione a due fattori è facoltativa.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-p104">Client communication across an IPSec-secured VPN or customer-owned private connection. Two-factor authentication is optional.</span></span> 
    
- <span data-ttu-id="9e2c9-179">Piani di supporto ITAR che offre.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-179">ITAR-support plans.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="9e2c9-180">Ibrida con Office 365</span><span class="sxs-lookup"><span data-stu-id="9e2c9-180">Hybrid with Office 365</span></span>

- <span data-ttu-id="9e2c9-181">Utilizzo di Office 365 per la condivisione e collaborazione anziché configurare un ambiente extranet esterno.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-181">Use Office 365 for external sharing and collaboration instead of setting up an extranet environment.</span></span> 
    
- <span data-ttu-id="9e2c9-182">Spostare i siti personali (OneDrive for Business) nel cloud per rendere più semplice per gli utenti di accedere in remoto i relativi file.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-182">Move My Sites (OneDrive for Business) to the cloud to make it easier for users to access their files remotely.</span></span> 
    
- <span data-ttu-id="9e2c9-183">Avvio di nuovi siti del team in Office 365.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-183">Start new team sites in Office 365.</span></span> 
    
- <span data-ttu-id="9e2c9-184">Integrare un sito di Office 365 con l'ambiente SharePoint servizi di integrazione Applicativa locale.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-184">Integrate an Office 365 site with on-premises BCS SharePoint environment.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="9e2c9-185">Azure</span><span class="sxs-lookup"><span data-stu-id="9e2c9-185">Azure</span></span>

- <span data-ttu-id="9e2c9-p105">SharePoint per siti Internet, ovvero pubblica facing siti. Trai vantaggio di Azure Active Directory per gli account dei clienti e l'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-p105">SharePoint for Internet Sites — Public facing sites. Take advantage of Azure AD for customer accounts and authentication.</span></span> 
    
- <span data-ttu-id="9e2c9-188">Sviluppo, test e ambienti di gestione temporanea, ovvero rapidamente il provisioning e il deprovisioning degli ambienti intero.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-188">Developer, test, and staging environments — Quickly provision and deprovision entire environments.</span></span> 
    
- <span data-ttu-id="9e2c9-189">Applicazioni ibride, ovvero le applicazioni che si estendono su cloud e i Data Center.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-189">Hybrid applications — Applications that span your datacenter and the cloud.</span></span> 
    
- <span data-ttu-id="9e2c9-p106">Ambiente di ripristino di emergenza, ripristinare rapidamente da una situazione di emergenza. Prestare solo per l'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-p106">Disaster recovery environment — Quickly recover from a disaster. Pay only for use.</span></span> 
    
- <span data-ttu-id="9e2c9-192">Farm che richiedono sulla creazione di report o controllo.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-192">Farms that require deep reporting or auditing.</span></span> 
    
- <span data-ttu-id="9e2c9-193">Analitica Web.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-193">Web analytics.</span></span> 
    
- <span data-ttu-id="9e2c9-194">Crittografia dei dati statici (dati vengono crittografati nei database di SQL).</span><span class="sxs-lookup"><span data-stu-id="9e2c9-194">Data encryption at rest (data is encrypted in the SQL databases).</span></span> 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a><span data-ttu-id="9e2c9-195">Crittografia dei dati statici (dati vengono crittografati nei database di SQL)</span><span class="sxs-lookup"><span data-stu-id="9e2c9-195">Data encryption at rest (data is encrypted in the SQL databases)</span></span>

- <span data-ttu-id="9e2c9-196">Farm nazionale (quando sono necessario dati che si trovano all'interno di un ufficio).</span><span class="sxs-lookup"><span data-stu-id="9e2c9-196">In-country farms (when data is required to reside within a jurisdiction).</span></span> 
    
- <span data-ttu-id="9e2c9-197">Soluzioni di Business Intelligence complesse che devono risiedere chiudere ai dati di Business Intelligence.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-197">Complex BI solutions that must reside close to BI data.</span></span> 
    
- <span data-ttu-id="9e2c9-198">Soluzioni basate su cloud privata.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-198">Private cloud solutions.</span></span> 
    
- <span data-ttu-id="9e2c9-199">Soluzioni fortemente personalizzate.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-199">Highly customized solutions.</span></span> 
    
- <span data-ttu-id="9e2c9-200">Soluzioni legacy con i componenti di terze parti che dipendono da hardware e software che non sono supportati nei servizi infrastruttura di Azure.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-200">Legacy solutions with third-party components that depend on hardware and software that are not supported on Azure Infrastructure Services.</span></span> 
    
- <span data-ttu-id="9e2c9-201">Limitazioni relative alla privacy che impediscono la sincronizzazione degli account di Active Directory con Azure Active Directory (un requisito per Office 365).</span><span class="sxs-lookup"><span data-stu-id="9e2c9-201">Privacy restrictions that prevent synchronization of Active Directory accounts with Azure Active Directory (a requirement for Office 365).</span></span> 
    
- <span data-ttu-id="9e2c9-202">Organizzazioni che preferiscono controllo dell'intera piattaforma e soluzione.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-202">Organizations that prefer control of the entire platform and solution.</span></span> 
    
### <a name="license-requirements"></a><span data-ttu-id="9e2c9-203">Requisiti relativi alle licenze</span><span class="sxs-lookup"><span data-stu-id="9e2c9-203">License requirements</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="9e2c9-204">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="9e2c9-204">SharePoint 2013 in Office 365</span></span>

<span data-ttu-id="9e2c9-p107">Modello di sottoscrizione. Nessuna licenza aggiuntiva necessaria.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-p107">Subscription model. No additional licenses needed.</span></span> 
  
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="9e2c9-207">Ibrida con Office 365</span><span class="sxs-lookup"><span data-stu-id="9e2c9-207">Hybrid with Office 365</span></span>

- <span data-ttu-id="9e2c9-p108">Office 365, ovvero Modello di sottoscrizione. Nessuna licenza aggiuntiva necessaria.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-p108">Office 365 — Subscription model. No additional licenses needed.</span></span> 
    
- <span data-ttu-id="9e2c9-210">Locale, Si applicano tutte le licenze locali.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-210">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="9e2c9-211">Azure</span><span class="sxs-lookup"><span data-stu-id="9e2c9-211">Azure</span></span>

-  <span data-ttu-id="9e2c9-212">Sottoscrizione Azure (include il sistema operativo server)</span><span class="sxs-lookup"><span data-stu-id="9e2c9-212">Azure subscription (includes the server operating system)</span></span>
    
- <span data-ttu-id="9e2c9-213">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9e2c9-213">SQL Server</span></span> 
    
- <span data-ttu-id="9e2c9-214">Licenza di SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="9e2c9-214">SharePoint 2013 Server License</span></span> 
    
- <span data-ttu-id="9e2c9-215">Licenza di accesso Client di SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="9e2c9-215">SharePoint 2013 Client Access License</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="9e2c9-216">In locale</span><span class="sxs-lookup"><span data-stu-id="9e2c9-216">On premises</span></span>

- <span data-ttu-id="9e2c9-217">Sistema operativo del server</span><span class="sxs-lookup"><span data-stu-id="9e2c9-217">Server operating system</span></span> 
    
- <span data-ttu-id="9e2c9-218">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9e2c9-218">SQL Server</span></span> 
    
- <span data-ttu-id="9e2c9-219">Licenza di SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="9e2c9-219">SharePoint 2013 Server License</span></span> 
    
- <span data-ttu-id="9e2c9-220">Licenza di accesso Client di SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="9e2c9-220">SharePoint 2013 Client Access License</span></span> 
    
### <a name="architecture-tasks"></a><span data-ttu-id="9e2c9-221">Attività di architettura</span><span class="sxs-lookup"><span data-stu-id="9e2c9-221">Architecture tasks</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="9e2c9-222">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="9e2c9-222">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="9e2c9-p109">Pianificare e progettare integrazione di directory. Due opzioni. Entrambe le opzioni possono essere distribuite in locale o in Azure: sincronizzazione delle Password (è richiesto un server a 64 bit). SSO (richiede AD FS e più server).</span><span class="sxs-lookup"><span data-stu-id="9e2c9-p109">Plan and design directory integration. Two options. Either option can be deployed on premises or in Azure: Password sync (requires one 64-bit server). SSO (requires AD FS and multiple servers).</span></span> 
    
- <span data-ttu-id="9e2c9-227">Verificare la capacità di rete e la disponibilità attraverso i firewall, server proxy, gateway e sui collegamenti WAN.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-227">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span> 
    
- <span data-ttu-id="9e2c9-228">Ottenere i certificati SSL di terze parti per garantire la sicurezza aziendale per le offerte di servizi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-228">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span> 
    
- <span data-ttu-id="9e2c9-229">Il nome del tenant di pianificare e progettare l'architettura della raccolta siti e la governance.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-229">Plan the tenant name, and design the site collection architecture and governance.</span></span> 
    
- <span data-ttu-id="9e2c9-230">Pianificare le personalizzazioni, soluzioni e App per SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-230">Plan customizations, solutions, and apps for SharePoint Online.</span></span> 
    
- <span data-ttu-id="9e2c9-p110">Decidere se si desidera connettersi a Office 365 utilizzando il protocollo Internet 6 (IPv6). Questa non operazione comune.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-p110">Decide if you want to connect to Office 365 by using the Internet Protocol 6 (IPv6). This is not common.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="9e2c9-233">Ibrida con Office 365</span><span class="sxs-lookup"><span data-stu-id="9e2c9-233">Hybrid with Office 365</span></span>

<span data-ttu-id="9e2c9-234">Oltre alle attività per gli ambienti di Office 365 e locali:</span><span class="sxs-lookup"><span data-stu-id="9e2c9-234">In addition to tasks for both the Office 365 and on-premises environments:</span></span> 
  
- <span data-ttu-id="9e2c9-p111">Determinare la quantità integrazione delle funzionalità desiderata e scegliere la topologia ibrida. Vedere il poster di modello: quale topologia ibrida utilizzare?</span><span class="sxs-lookup"><span data-stu-id="9e2c9-p111">Determine how much feature integration you want and choose the hybrid topology. See this model poster: Which hybrid topology should I use?</span></span> 
    
- <span data-ttu-id="9e2c9-237">Se necessario, determinare quali dispositivi server proxy da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-237">If required, determine which proxy server device will be used.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="9e2c9-238">Azure</span><span class="sxs-lookup"><span data-stu-id="9e2c9-238">Azure</span></span>

<span data-ttu-id="9e2c9-239">Progettare l'ambiente di rete Azure:</span><span class="sxs-lookup"><span data-stu-id="9e2c9-239">Design the Azure network environment:</span></span> 
  
- <span data-ttu-id="9e2c9-240">Rete virtuale interna Azure, comprese le subnet.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-240">Virtual network within Azure, including subnets.</span></span> 
    
- <span data-ttu-id="9e2c9-241">Ambiente di dominio e l'integrazione con i server locali.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-241">Domain environment and integration with on-premises servers.</span></span> 
    
- <span data-ttu-id="9e2c9-242">DNS e indirizzi IP.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-242">IP addresses and DNS.</span></span> 
    
- <span data-ttu-id="9e2c9-243">Affinità gruppi e gli account di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-243">Affinity groups and storage accounts.</span></span> 
    
<span data-ttu-id="9e2c9-244">Progettare l'ambiente di SharePoint in Azure:</span><span class="sxs-lookup"><span data-stu-id="9e2c9-244">Design the SharePoint environment in Azure:</span></span> 
  
- <span data-ttu-id="9e2c9-245">Topologia farm di SharePoint e l'architettura logica.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-245">SharePoint farm topology and logical architecture.</span></span> 
    
-  <span data-ttu-id="9e2c9-246">Set di disponibilità Azure e i domini di aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-246">Azure availability sets and update domains.</span></span>
    
- <span data-ttu-id="9e2c9-247">Dimensioni delle macchine virtuali.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-247">Virtual machines sizes.</span></span> 
    
- <span data-ttu-id="9e2c9-248">Carico bilanciato endpoint.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-248">Load balanced endpoint.</span></span> 
    
- <span data-ttu-id="9e2c9-249">Endpoint esterni di accesso pubblico, se è preferibile.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-249">External endpoints for public access, if that is preferable.</span></span> 
    
- <span data-ttu-id="9e2c9-250">Ambiente di ripristino di emergenza.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-250">Disaster recovery environment.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="9e2c9-251">In locale</span><span class="sxs-lookup"><span data-stu-id="9e2c9-251">On premises</span></span>

<span data-ttu-id="9e2c9-252">Progettare l'ambiente di SharePoint in un ambiente locale esistente:</span><span class="sxs-lookup"><span data-stu-id="9e2c9-252">Design the SharePoint environment in an existing on-premises environment:</span></span> 
  
- <span data-ttu-id="9e2c9-253">Topologia farm di SharePoint e l'architettura logica.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-253">SharePoint farm topology and logical architecture.</span></span> 
    
- <span data-ttu-id="9e2c9-254">Hardware del server.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-254">Server hardware.</span></span> 
    
- <span data-ttu-id="9e2c9-255">Ambiente virtuale, se utilizzato.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-255">Virtual environment, if used.</span></span> 
    
- <span data-ttu-id="9e2c9-256">Il bilanciamento del carico.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-256">Load balancing.</span></span> 
    
- <span data-ttu-id="9e2c9-257">Integrazione con Active Directory e DNS.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-257">Integration with AD DS and DNS.</span></span> 
    
- <span data-ttu-id="9e2c9-258">Ambiente di ripristino di emergenza.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-258">Disaster recovery environment.</span></span> 
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="9e2c9-259">IT pro responsabilità</span><span class="sxs-lookup"><span data-stu-id="9e2c9-259">IT pro responsibilities</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="9e2c9-260">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="9e2c9-260">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="9e2c9-261">Verificare le workstation degli utenti soddisfino i prerequisiti del client Office 365.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-261">Ensure user workstations meet Office 365 client prerequisites.</span></span> 
    
- <span data-ttu-id="9e2c9-262">Implementare il piano di integrazione di directory.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-262">Implement the directory integration plan.</span></span> 
    
- <span data-ttu-id="9e2c9-263">Pianificare e implementare i record DNS interni ed esterni e il routing.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-263">Plan and implement internal and external DNS records and routing.</span></span> 
    
- <span data-ttu-id="9e2c9-264">Configurare il firewall per l'indirizzo IP di Office 365 e requisiti per gli URL o il proxy.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-264">Configure the proxy or firewall for Office 365 IP address and URL requirements.</span></span> 
    
- <span data-ttu-id="9e2c9-265">Creare e assegnare le autorizzazioni per le raccolte siti.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-265">Create and assign permissions to site collections.</span></span> 
    
- <span data-ttu-id="9e2c9-266">Implementazione di applicazioni, le personalizzazioni e soluzioni per SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-266">Implement customizations, solutions, and apps for SharePoint Online.</span></span> 
    
- <span data-ttu-id="9e2c9-267">Monitorare la disponibilità della rete e identificare possibili colli di bottiglia.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-267">Monitor network availability and identify possible bottlenecks.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="9e2c9-268">Ibrida con Office 365</span><span class="sxs-lookup"><span data-stu-id="9e2c9-268">Hybrid with Office 365</span></span>

<span data-ttu-id="9e2c9-269">Oltre alle attività per gli ambienti di Office 365 e locali:</span><span class="sxs-lookup"><span data-stu-id="9e2c9-269">In addition to tasks for both the Office 365 and on-premises environments:</span></span> 
  
- <span data-ttu-id="9e2c9-270">Configurare il dispositivo di server proxy, se necessario.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-270">Configure the proxy server device, if required.</span></span> 
    
- <span data-ttu-id="9e2c9-271">Configurare l'infrastruttura di gestione delle identità ibrida: SSO e l'autenticazione da server a server tra due ambienti.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-271">Configure the hybrid identity management infrastructure: SSO and server-to-server authentication between the two environments.</span></span> 
    
- <span data-ttu-id="9e2c9-272">Configurare l'integrazione delle funzionalità scelte: ricerca, servizi di integrazione Applicativa, Duet Enterprise Online.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-272">Configure the integration of chosen features: Search, BCS, Duet Enterprise Online.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="9e2c9-273">Azure</span><span class="sxs-lookup"><span data-stu-id="9e2c9-273">Azure</span></span>

<span data-ttu-id="9e2c9-274">Distribuire e gestire l'ambiente Azure e SharePoint:</span><span class="sxs-lookup"><span data-stu-id="9e2c9-274">Deploy and manage the Azure and SharePoint environment:</span></span> 
  
- <span data-ttu-id="9e2c9-275">Implementare e gestire l'ambiente di rete di Azure.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-275">Implement and manage the Azure network environment.</span></span> 
    
- <span data-ttu-id="9e2c9-276">Distribuire l'ambiente SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-276">Deploy the SharePoint environment.</span></span> 
    
- <span data-ttu-id="9e2c9-277">Aggiornare i server della farm di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-277">Update SharePoint farm servers.</span></span> 
    
- <span data-ttu-id="9e2c9-278">Aggiungere o arrestare macchine virtuali in base alle esigenze basato sull'utilizzo di farm.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-278">Add or shut down virtual machines as needed based on farm utilization.</span></span> 
    
- <span data-ttu-id="9e2c9-279">Aumentare o ridurre le dimensioni delle macchine virtuali, in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-279">Increase or decrease virtual machine sizes, as needed.</span></span> 
    
- <span data-ttu-id="9e2c9-280">Eseguire il backup dell'ambiente di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-280">Back up the SharePoint environment.</span></span> 
    
- <span data-ttu-id="9e2c9-281">Implementazione di un ambiente di ripristino di emergenza e il protocollo.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-281">Implement the disaster recovery environment and protocol.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="9e2c9-282">In locale</span><span class="sxs-lookup"><span data-stu-id="9e2c9-282">On premises</span></span>

<span data-ttu-id="9e2c9-283">Distribuire e gestire SharePoint dall'ambiente locale:</span><span class="sxs-lookup"><span data-stu-id="9e2c9-283">Deploy and manage the SharePoint on premises environment:</span></span> 
  
- <span data-ttu-id="9e2c9-284">Server di provisioning.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-284">Provision servers.</span></span> 
    
- <span data-ttu-id="9e2c9-285">Distribuire l'ambiente SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-285">Deploy the SharePoint environment.</span></span> 
    
- <span data-ttu-id="9e2c9-286">Aggiornare i server della farm di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-286">Update SharePoint farm servers.</span></span> 
    
- <span data-ttu-id="9e2c9-287">Aggiungere o rimuovere server della farm in base alle esigenze basato sull'utilizzo di farm.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-287">Add or remove farm servers as needed based on farm utilization.</span></span> 
    
- <span data-ttu-id="9e2c9-288">Eseguire il backup dell'ambiente di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-288">Back up the SharePoint environment.</span></span> 
    
- <span data-ttu-id="9e2c9-289">Implementazione di un ambiente di ripristino di emergenza e il protocollo.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-289">Implement the disaster recovery environment and protocol.</span></span> 
    
## <a name="three-typical-workloads-to-move-to-azure"></a><span data-ttu-id="9e2c9-290">Tre tipici carichi di lavoro per spostare in Azure</span><span class="sxs-lookup"><span data-stu-id="9e2c9-290">Three typical workloads to move to Azure</span></span>

### <a name="office-365-plus-directory-components-in-azure"></a><span data-ttu-id="9e2c9-291">Office 365 e componenti della Directory in Azure</span><span class="sxs-lookup"><span data-stu-id="9e2c9-291">Office 365 plus Directory Components in Azure</span></span>

<span data-ttu-id="9e2c9-292">Distribuzione di Office 365 componenti di integrazione directory in Azure è più veloce perché è possibile distribuire le macchine virtuali su richiesta.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-292">Deploying Office 365 directory integration components in Azure is faster because it can deploy virtual machines on-demand.</span></span> 
  
#### <a name="directory-synchronization-server-only"></a><span data-ttu-id="9e2c9-293">Solo server di sincronizzazione directory</span><span class="sxs-lookup"><span data-stu-id="9e2c9-293">Directory synchronization server only</span></span>

<span data-ttu-id="9e2c9-294">Invece di distribuire il server di sincronizzazione directory a 64 bit nell'ambiente locale, effettuare il provisioning una macchina virtuale in Azure.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-294">Instead of deploying the 64-bit directory synchronization server in your on-premises environment, provision a virtual machine in Azure instead.</span></span> 
  
<span data-ttu-id="9e2c9-295">Nella figura relativa Mostra SharePoint Online con un tenant di Azure Active Directory, che consente di sincronizzare i nomi degli account e password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-295">The accompanying diagram shows SharePoint Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
  
#### <a name="directory-synchronization-plus-ad-fs"></a><span data-ttu-id="9e2c9-296">La sincronizzazione delle directory oltre AD FS</span><span class="sxs-lookup"><span data-stu-id="9e2c9-296">Directory synchronization plus AD FS</span></span>

<span data-ttu-id="9e2c9-p112">Questa opzione consente di supportare le identità federata di Office 365 (SSO) senza aggiungere componenti hardware per l'infrastruttura locale. Fornisce inoltre resilienza se non è disponibile nell'ambiente Active Directory locale.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-p112">This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure. It also provides resiliency if the on-premises Active Directory environment is unavailable.</span></span> 
  
- <span data-ttu-id="9e2c9-299">Componenti di integrazione Directory risiedono in Azure.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-299">Directory integration components reside in Azure.</span></span> 
    
- <span data-ttu-id="9e2c9-300">ADFS viene pubblicato su Internet tramite proxy AD FS in Azure.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-300">AD FS is published to the Internet through AD FS proxies in Azure.</span></span> 
    
- <span data-ttu-id="9e2c9-301">Il traffico di autenticazione client, per gli utenti che si connettono da qualsiasi posizione, viene gestito dal server ADFS e i proxy che vengono distribuiti in Azure.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-301">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed on Azure.</span></span> 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a><span data-ttu-id="9e2c9-302">Sito Internet pubblico e Azure Active Directory per l'autenticazione dei clienti</span><span class="sxs-lookup"><span data-stu-id="9e2c9-302">Public-facing Internet site and Azure AD for customer authentication</span></span>

<span data-ttu-id="9e2c9-p113">Possibilità di sfruttare la possibilità di scalabilità per richiesta inserendo il sito Internet in Azure. Utilizzare Azure Active Directory per archiviare gli account dei clienti.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-p113">Take advantage of the ability to easily scale to demand by placing your Internet site in Azure. Use Azure AD to store customer accounts.</span></span> 
  
#### <a name="azure-advantages-for-internet-sites"></a><span data-ttu-id="9e2c9-305">Vantaggi Azure per siti Internet</span><span class="sxs-lookup"><span data-stu-id="9e2c9-305">Azure advantages for Internet sites</span></span>

- <span data-ttu-id="9e2c9-306">Prestare solo per le risorse che necessarie quando si aumenta il numero di macchine virtuali in base sull'utilizzo di farm.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-306">Pay only for the resources you need by scaling the number of virtual machines based on farm utilization.</span></span> 
    
- <span data-ttu-id="9e2c9-307">Aggiungere informazioni sui report e analitica web.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-307">Add deep reporting and web analytics.</span></span> 
    
- <span data-ttu-id="9e2c9-308">Importanza lo sviluppo di un ottimo sito anziché la creazione di infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-308">Focus on developing a great site rather than building infrastructure.</span></span> 
    
#### <a name="azure-ad"></a><span data-ttu-id="9e2c9-309">Azure AD</span><span class="sxs-lookup"><span data-stu-id="9e2c9-309">Azure AD</span></span>

<span data-ttu-id="9e2c9-p114">Azure Active Directory fornisce funzionalità di controllo di accesso e gestione identità per servizi basati su cloud. Funzionalità di includere un archivio basato su cloud per dati di directory e un set di componenti di base dei servizi di identità, tra cui i processi di accesso, servizi di autenticazione e di ADFS. I servizi di identità inclusi con Azure Active Directory si integrano facilmente con distribuzioni di Active Directory locale e supportano i provider di identità di terze parti.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-p114">Azure AD provides identity management and access control capabilities for cloud services. Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS. The identity services that are included with Azure AD easily integrate with your on-premises Active Directory deployments and fully support third-party identity providers.</span></span> 
  
<span data-ttu-id="9e2c9-p115">Figura relativa che mostra la configurazione delle aree e autenticazione è importante per siti Internet. Il diagramma mostra Azure Active Directory Tenant, che contiene una Farm di SharePoint su Azure con due aree:</span><span class="sxs-lookup"><span data-stu-id="9e2c9-p115">The accompanying diagram shows the configuration of zones and authentication that is important for Internet-facing sites. The diagram shows the Azure Active Directory Tenant, which contains a SharePoint Farm on Azure with two zones:</span></span> 
  
- <span data-ttu-id="9e2c9-315">Un'area Internet che interagisce con i clienti esterni alla rete e visitatori autenticato e anonimi</span><span class="sxs-lookup"><span data-stu-id="9e2c9-315">An Internet zone that interacts with Anonymous and Authenticated visitors and customers outside the network</span></span> 
    
- <span data-ttu-id="9e2c9-316">Area predefinita che contiene NTLM per la ricerca per indicizzazione e l'autenticazione di Windows che interagisce con la distribuzione di Active Directory locale su un tunnel VPN.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-316">A default zone that contains NTLM for Crawl and Windows Authentication that interacts with your on-premises Active Directory deployment over a VPN tunnel.</span></span> 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a><span data-ttu-id="9e2c9-317">Farm locale e il ripristino di emergenza in Azure</span><span class="sxs-lookup"><span data-stu-id="9e2c9-317">On-premises Farm plus Disaster Recovery in Azure</span></span>

<span data-ttu-id="9e2c9-p116">Scegliere un'opzione di ripristino di emergenza che genera una corrispondenza per i requisiti aziendali. Azure sono disponibili opzioni semplice per le società Guida introduttiva a ripristino di emergenza e opzioni avanzate per le grandi aziende con i requisiti di resilienza elevata.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-p116">Choose a disaster recovery option that matches your business requirements. Azure provides entry-level options for companies getting started with disaster recovery and advanced options for enterprises with high resiliency requirements.</span></span> 
  
#### <a name="cold-standby"></a><span data-ttu-id="9e2c9-320">Data Center con cold standby</span><span class="sxs-lookup"><span data-stu-id="9e2c9-320">Cold standby</span></span>

- <span data-ttu-id="9e2c9-p117">Viene creata completamente la farm, ma le macchine virtuali vengono arrestate. (Estinguere solo quando viene eseguito!)</span><span class="sxs-lookup"><span data-stu-id="9e2c9-p117">The farm is fully built, but the virtual machines are stopped. (You're paying only when they're running!)</span></span> 
    
- <span data-ttu-id="9e2c9-323">Gestione dell'ambiente include le macchine virtuali a partire dal momento in tanto, applicazione di patch, l'aggiornamento e la verifica dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-323">Maintaining the environment includes starting the virtual machines from time-to-time, patching, updating, and verifying the environment.</span></span> 
    
- <span data-ttu-id="9e2c9-324">Avviare l'ambiente completo in caso di calamità.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-324">Start the full environment in the event of a disaster.</span></span> 
    
#### <a name="warm-standby"></a><span data-ttu-id="9e2c9-325">Data Center con warm standby</span><span class="sxs-lookup"><span data-stu-id="9e2c9-325">Warm standby</span></span>

- <span data-ttu-id="9e2c9-326">Sono incluse le farm di piccole dimensioni che è stato eseguito il provisioning e in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-326">This includes a small farm that is provisioned and running.</span></span> 
    
- <span data-ttu-id="9e2c9-327">La farm immediatamente può supportare utenti in caso di failover.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-327">The farm can immediately serve users in the event of a failover.</span></span> 
    
- <span data-ttu-id="9e2c9-328">Scalabilità orizzontale della farm rapidamente per servire base utente completa.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-328">Scale out the farm quickly to serve the full user base.</span></span> 
    
#### <a name="hot-standby"></a><span data-ttu-id="9e2c9-329">Data Center con hot standby</span><span class="sxs-lookup"><span data-stu-id="9e2c9-329">Hot standby</span></span>

<span data-ttu-id="9e2c9-330">Una farm di dimensioni completamente è stato eseguito il provisioning e in esecuzione in modalità standby.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-330">A fully-sized farm is provisioned and running on standby.</span></span> 
  
<span data-ttu-id="9e2c9-p118">Di accompagnamento è illustrata una farm locale interazione con l'ambiente di ripristino di emergenza di SharePoint su Azure. Utilizzano i database locale SQL Server Log Shipping sul tunnel VPN per accedere all'ambiente di ripristino di emergenza di SharePoint, che include due server di database SQL che contengono i database di SharePoint, due server Web front-End e due SharePoint Server applicazioni.</span><span class="sxs-lookup"><span data-stu-id="9e2c9-p118">The accompanying diagram shows an on-premises farm interacting with the SharePoint Disaster Recovery Environment on Azure. The on-premises databases use SQL Server Log Shipping over the VPN tunnel to access the SharePoint Disaster Recovery environment, which includes two SQL database servers that contain the SharePoint databases, two Web Front End servers, and two SharePoint Application servers.</span></span> 
  

