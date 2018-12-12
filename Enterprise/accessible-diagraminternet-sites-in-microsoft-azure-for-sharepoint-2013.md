---
title: Diagramma accessibile - siti Internet in Microsoft Azure per SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
description: In questo articolo è una versione testo accessibile del diagramma denominato siti Internet in Microsoft Azure per SharePoint 2013.
ms.openlocfilehash: 59c84e34ab4d748a80ab0a597817ae4d3464a43c
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
ms.locfileid: "17503049"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="d1e24-103">Diagramma accessibile - siti Internet in Microsoft Azure per SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="d1e24-103">Accessible diagram - Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="d1e24-104">**Riepilogo:** In questo articolo è una versione testo accessibile del diagramma denominato siti Internet in Microsoft Azure per SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="d1e24-104">**Summary:** This article is an accessible text version of the diagram named Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="d1e24-p101">Questo poster descrive e illustra i benefici ai siti Internet pubblico come la flessibilità cloud e Azure Active Directory per gli account dei clienti. Esistono sei diversi scenari che illustrano come siti Internet traggono vantaggio da Azure:</span><span class="sxs-lookup"><span data-stu-id="d1e24-p101">This poster describes and illustrates how public-facing Internet sites benefit from cloud elasticity and Azure AD for customer accounts. There are six different scenarios that describe how Internet sites benefit from Azure:</span></span> 
  
- <span data-ttu-id="d1e24-107">Progettare e scegliere la topologia della farm.</span><span class="sxs-lookup"><span data-stu-id="d1e24-107">Design and size the farm topology.</span></span> 
    
- <span data-ttu-id="d1e24-108">Ottimizzare per Azure.</span><span class="sxs-lookup"><span data-stu-id="d1e24-108">Fine-tune for Azure.</span></span> 
    
- <span data-ttu-id="d1e24-109">Scegliere il modello di Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d1e24-109">Choose the Active Directory model.</span></span> 
    
- <span data-ttu-id="d1e24-110">Progettazione della gestione delle identità, aree e autenticazione.</span><span class="sxs-lookup"><span data-stu-id="d1e24-110">Design for identity management, zones, and authentication.</span></span> 
    
- <span data-ttu-id="d1e24-111">La progettazione di siti e gli URL per la pubblicazione intersito.</span><span class="sxs-lookup"><span data-stu-id="d1e24-111">Design sites and URLs for cross-site publishing.</span></span> 
    
- <span data-ttu-id="d1e24-112">Progettare l'ambiente Azure.</span><span class="sxs-lookup"><span data-stu-id="d1e24-112">Design the Azure environment.</span></span> 
    
## <a name="design-and-size-the-farm-topology"></a><span data-ttu-id="d1e24-113">Progettare e scegliere la topologia della farm</span><span class="sxs-lookup"><span data-stu-id="d1e24-113">Design and size the farm topology</span></span>

<span data-ttu-id="d1e24-114">Utilizzare le informazioni della topologia, capacità e prestazioni per SharePoint 2013 in TechNet per progettare la topologia della farm.</span><span class="sxs-lookup"><span data-stu-id="d1e24-114">Use the topology, capacity, and performance guidance for SharePoint 2013 on TechNet to design the farm topology.</span></span> 
  
<span data-ttu-id="d1e24-115">Verificare che la farm che è progettare soddisfi gli obiettivi di capacità e prestazioni.</span><span class="sxs-lookup"><span data-stu-id="d1e24-115">Ensure the farm you design meets the objectives for capacity and performance.</span></span> 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a><span data-ttu-id="d1e24-116">Esempio: Farm di medie dimensioni siti Internet (~ 85 visualizzazioni pagina al secondo)</span><span class="sxs-lookup"><span data-stu-id="d1e24-116">Example: Medium Internet Sites farm (~85 page views per second)</span></span>

<span data-ttu-id="d1e24-117">Questa farm renderà disponibili una tolleranza SharePoint 2013 farm topologia di ricerca è ottimizzata per un corpo che contiene 3,400,000 elementi.</span><span class="sxs-lookup"><span data-stu-id="d1e24-117">This farm provides a fault-tolerant SharePoint 2013 search farm topology that is optimized for a corpus that contains 3,400,000 items.</span></span> 
  
<span data-ttu-id="d1e24-118">La farm di esempio di elaborazione dei documenti di 100-200 al secondo, a seconda della lingua e tiene conto 85 visualizzazioni pagina al seconda e 100 query al secondo.</span><span class="sxs-lookup"><span data-stu-id="d1e24-118">The example farm processes 100-200 documents per second, depending on the language, and it accommodates 85 page views per second and 100 queries per second.</span></span> 
  
<span data-ttu-id="d1e24-119">Nella figura relativa viene illustrata una farm di siti internet medie dimensioni con tre tipi di server:</span><span class="sxs-lookup"><span data-stu-id="d1e24-119">The accompanying diagram shows a medium internet sites farm with three types of servers:</span></span> 
  
- <span data-ttu-id="d1e24-120">Server Web</span><span class="sxs-lookup"><span data-stu-id="d1e24-120">Web servers</span></span> 
    
- <span data-ttu-id="d1e24-121">Server applicazioni</span><span class="sxs-lookup"><span data-stu-id="d1e24-121">Application servers</span></span> 
    
- <span data-ttu-id="d1e24-122">Server di database</span><span class="sxs-lookup"><span data-stu-id="d1e24-122">Database servers</span></span> 
    
#### <a name="web-servers"></a><span data-ttu-id="d1e24-123">Server Web</span><span class="sxs-lookup"><span data-stu-id="d1e24-123">Web servers</span></span>

<span data-ttu-id="d1e24-p102">Nella sezione server web, esistono tre server web, Host A, Host B e c Host. Ogni server web contiene una cache distribuita, profili utente, metadati gestiti e le funzionalità di elaborazione delle query. Contengono anche una replica della partizione di indice in ogni server.</span><span class="sxs-lookup"><span data-stu-id="d1e24-p102">In the web servers section, there are three web servers, Host A, Host B, and Host C. Each web server contains a distributed cache, user profiles, managed metadata, and query processing capabilities. They also contain an index partition replica that is in each server.</span></span> 
  
<span data-ttu-id="d1e24-126">Per implementare la scalabilità, aggiungere un server web aggiuntivi con le stesse funzionalità, permettendo un 28 aggiuntive visualizzazioni di pagine al secondo.</span><span class="sxs-lookup"><span data-stu-id="d1e24-126">To scale out, add an additional web server with the same capabilities, which allows for an additional 28 page views per second.</span></span> 
  
#### <a name="application-servers"></a><span data-ttu-id="d1e24-127">Server applicazioni</span><span class="sxs-lookup"><span data-stu-id="d1e24-127">Application servers</span></span>

<span data-ttu-id="d1e24-p103">Nella sezione Server applicazioni, sono disponibili tre server applicazioni, D Host, Host E e Host F. Host G include i componenti di elaborazione della ricerca per indicizzazione, amministrazione, Analitica e contenuto. Host E include i componenti di elaborazione della ricerca per indicizzazione, amministrazione e il contenuto. Host F include i componenti di elaborazione del contenuto e ricerca per indicizzazione.</span><span class="sxs-lookup"><span data-stu-id="d1e24-p103">In the application servers section, there are three application servers, Host D, Host E, and Host F. Host D contains Crawl, Admin, Analytics, and Content processing components. Host E contains Crawl, Admin, and Content processing components. Host F contains Crawl and Content processing components.</span></span> 
  
<span data-ttu-id="d1e24-131">Per la scalabilità, aggiungere un server applicazioni con un componente di ricerca per indicizzazione e un componente per elaborare un ulteriori documenti 40 al secondo di elaborazione del contenuto.</span><span class="sxs-lookup"><span data-stu-id="d1e24-131">To scale out, add one application server with a crawl component and a content processing component to process an additional 40 documents per second.</span></span> 
  
#### <a name="database-servers"></a><span data-ttu-id="d1e24-132">Server di database</span><span class="sxs-lookup"><span data-stu-id="d1e24-132">Database servers</span></span>

<span data-ttu-id="d1e24-133">Nella sezione server di database, sono disponibili due server, G Host e Host H. I server di database sono negli host accoppiati della tolleranza di errore.</span><span class="sxs-lookup"><span data-stu-id="d1e24-133">In the database servers section, there are two servers, Host G and Host H. The database servers are in paired hosts for fault tolerance.</span></span> 
  
<span data-ttu-id="d1e24-p104">Host G contiene tutti i database di SharePoint, inclusi il database di amministrazione della ricerca, database dei collegamenti, due database di ricerca per indicizzazione, un database Analitica e tutti gli altri database di SharePoint. Host H contiene tutti i database di SharePoint, tra cui le copie ridondanti di tutti i database tramite SQL clustering, mirroring o SQL Server 2012 AlwaysOn.</span><span class="sxs-lookup"><span data-stu-id="d1e24-p104">Host G contains all SharePoint database, including Search admin database, Link database, two Crawl databases, an Analytics database, and all other SharePoint databases. Host H contains all SharePoint databases, including redundant copies of all databases using SQL clustering, mirroring, or SQL Server 2012 AlwaysOn.</span></span> 
  
## <a name="fine-tune-for-azure"></a><span data-ttu-id="d1e24-136">Ottimizzare per Azure</span><span class="sxs-lookup"><span data-stu-id="d1e24-136">Fine-tune for Azure</span></span>

<span data-ttu-id="d1e24-p105">Farm di SharePoint potrebbe essere necessario ottimizzato per set di disponibilità nella piattaforma Azure. Per garantire la disponibilità elevata di tutti i componenti, verificare che i ruoli del server siano configurati tutti in modo identico.</span><span class="sxs-lookup"><span data-stu-id="d1e24-p105">The SharePoint farm might need to be fine-tuned for availability sets in the Azure platform. To ensure high availability of all components, ensure that the server roles are all identically configured.</span></span> 
  
<span data-ttu-id="d1e24-139">Nella topologia di esempio nel diagramma:</span><span class="sxs-lookup"><span data-stu-id="d1e24-139">In the example topology in the diagram:</span></span> 
  
- <span data-ttu-id="d1e24-140">I server web e i server di database vengono configurati in modo identico.</span><span class="sxs-lookup"><span data-stu-id="d1e24-140">The web servers and the database servers are identically configured.</span></span> 
    
- <span data-ttu-id="d1e24-p106">I server tre applicazioni non sono configurati in modo identico. Questi ruoli del server richiedono ottimizzazione per la disponibilità viene impostata in Azure.</span><span class="sxs-lookup"><span data-stu-id="d1e24-p106">The three application servers are not identically configured. These server roles require fine tuning for availability sets in Azure.</span></span> 
    
### <a name="before"></a><span data-ttu-id="d1e24-143">Before</span><span class="sxs-lookup"><span data-stu-id="d1e24-143">Before</span></span>

<span data-ttu-id="d1e24-p107">Nella parte superiore del diagramma mostra la farm di SharePoint prima che è stato ottimizzato per la disponibilità viene impostata in Azure. Nel diagramma, i server applicazioni tre host non sono configurati in modo identico. Il numero di componenti dipende dagli obiettivi di prestazioni e capacità per la farm. I tre server sono configurati come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="d1e24-p107">The top portion of the diagram shows the SharePoint farm before it has been fine-tuned for availability sets in Azure. In the diagram, the three host application servers are not identically configured. The number of components is determined by the performance and capacity targets for the farm. The three servers are configured as follows:</span></span> 
  
- <span data-ttu-id="d1e24-148">Server applicazioni host D è configurato con i ruoli di elaborazione della ricerca per indicizzazione, amministrazione, Analitica e contenuto.</span><span class="sxs-lookup"><span data-stu-id="d1e24-148">Host D application server is configured with Crawl, Admin, Analytics, and Content processing roles.</span></span> 
    
- <span data-ttu-id="d1e24-149">Host E applicazione server viene configurato con i ruoli di elaborazione della ricerca per indicizzazione, amministrazione e il contenuto.</span><span class="sxs-lookup"><span data-stu-id="d1e24-149">Host E application server is configured with Crawl, Admin, and Content processing roles.</span></span> 
    
- <span data-ttu-id="d1e24-150">Server applicazioni host F è configurato con i ruoli di elaborazione del contenuto e ricerca per indicizzazione.</span><span class="sxs-lookup"><span data-stu-id="d1e24-150">Host F application server is configured with Crawl and Content processing roles.</span></span> 
    
### <a name="after"></a><span data-ttu-id="d1e24-151">After</span><span class="sxs-lookup"><span data-stu-id="d1e24-151">After</span></span>

<span data-ttu-id="d1e24-p108">In questa sezione del diagramma è illustrata la farm di SharePoint dopo che è stato ottimizzato per la disponibilità viene impostata in Azure. Per adattare questa architettura per Azure, si verranno replicare i quattro componenti in tutti i tre server. In questo modo aumenta il numero di componenti oltre quanto necessario per le prestazioni e capacità. Lo svantaggio è che questa struttura garantisce la disponibilità elevata di tutti i quattro componenti della piattaforma Azure quando questi tre macchine virtuali vengono assegnate a un set di disponibilità.</span><span class="sxs-lookup"><span data-stu-id="d1e24-p108">This part of the diagram shows the SharePoint farm after it has been fine-tuned for availability sets in Azure. To adapt this architecture for Azure, we'll replicate the four components across all three servers. This increases the number of components beyond what is necessary for performance and capacity. The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span> 
  
<span data-ttu-id="d1e24-156">Tre server sono configurati per tutti avere i ruoli di elaborazione della ricerca per indicizzazione, amministrazione, Analitica e contenuto.</span><span class="sxs-lookup"><span data-stu-id="d1e24-156">The three servers are configured to all have the Crawl, Admin, Analytics, and Content processing roles.</span></span> 
  
## <a name="choose-the-active-directory-model"></a><span data-ttu-id="d1e24-157">Scegliere il modello di Active Directory</span><span class="sxs-lookup"><span data-stu-id="d1e24-157">Choose the Active Directory model</span></span>

<span data-ttu-id="d1e24-p109">Tutte le soluzioni di SharePoint richiedono servizi di dominio Active Directory Windows (AD DS). In questa fase sono disponibili due opzioni per le soluzioni SharePoint in Azure.</span><span class="sxs-lookup"><span data-stu-id="d1e24-p109">All SharePoint solutions require Windows Active Directory Domain Services (AD DS). At this time, there are two options for SharePoint solutions in Azure.</span></span> 
  
- <span data-ttu-id="d1e24-p110">Opzione 1: Dominio dedicato, è possibile distribuire un dominio dedicato e isolato in Azure per supportare una farm di SharePoint. Si tratta di una buona scelta per siti Internet pubblico.</span><span class="sxs-lookup"><span data-stu-id="d1e24-p110">Option 1: Dedicated domain — You can deploy a dedicated and isolated domain to Azure to support a SharePoint farm. This is a good choice for public-facing Internet sites.</span></span> 
    
- <span data-ttu-id="d1e24-p111">Opzione 2: Estendere il dominio locale tramite una connessione VPN da sito. Quando si estende il dominio locale tramite una connessione VPN a siti, gli utenti accedere alla farm di SharePoint come se fosse ospitati in locale. È possibile sfruttare le implementazioni di Active Directory e DNS esistenti.</span><span class="sxs-lookup"><span data-stu-id="d1e24-p111">Option 2: Extend the on-premises domain through a site-to-site VPN connection. When you extend the on-premises domain through a site-to-site VPN connection, users access the SharePoint farm as if it were hosted on-premises. You can take advantage of your existing Active Directory and DNS implementations.</span></span> 
    
## <a name="design-for-identity-management-zones-and-authentication"></a><span data-ttu-id="d1e24-165">Progettazione della gestione delle identità, aree e autenticazione</span><span class="sxs-lookup"><span data-stu-id="d1e24-165">Design for identity management, zones, and authentication</span></span>

### <a name="design-for-accounts-and-authentication"></a><span data-ttu-id="d1e24-166">Progettazione per gli account e autenticazione</span><span class="sxs-lookup"><span data-stu-id="d1e24-166">Design for accounts and authentication</span></span>

<span data-ttu-id="d1e24-167">Determinare la modalità di gestione di account e il tipo di autenticazione utilizzato.</span><span class="sxs-lookup"><span data-stu-id="d1e24-167">Determine how accounts will be managed and which type of authentication will be used.</span></span> 
  
#### <a name="accounts-for-site-developers-and-authors"></a><span data-ttu-id="d1e24-168">Account per gli sviluppatori di siti e gli autori</span><span class="sxs-lookup"><span data-stu-id="d1e24-168">Accounts for site developers and authors</span></span>

- <span data-ttu-id="d1e24-169">Aggiungere account al dominio in Azure.</span><span class="sxs-lookup"><span data-stu-id="d1e24-169">Add accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="d1e24-170">Utilizzare Active Directory Federation Services (ADFS) locale per attuare la federazione gli account interni al dominio in Azure.</span><span class="sxs-lookup"><span data-stu-id="d1e24-170">Use Active Directory Federation Services (AD FS) on premises to federate the internal accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="d1e24-171">Se la progettazione include una connessione VPN da sito, utilizzare gli account interni.</span><span class="sxs-lookup"><span data-stu-id="d1e24-171">If the design includes a site-to-site VPN connection, use the internal accounts.</span></span> 
    
#### <a name="accounts-for-customers"></a><span data-ttu-id="d1e24-172">Account per i clienti</span><span class="sxs-lookup"><span data-stu-id="d1e24-172">Accounts for customers</span></span>

- <span data-ttu-id="d1e24-173">Utilizzo di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d1e24-173">Use Azure Active Directory.</span></span> 
    
- <span data-ttu-id="d1e24-174">Utilizzare un altro provider basata su SAML.</span><span class="sxs-lookup"><span data-stu-id="d1e24-174">Use a different SAML-based provider.</span></span> 
    
### <a name="design-for-zones"></a><span data-ttu-id="d1e24-175">Progettazione delle aree</span><span class="sxs-lookup"><span data-stu-id="d1e24-175">Design for zones</span></span>

<span data-ttu-id="d1e24-176">In SharePoint 2013, la gestione delle identità è inserita nella configurazione delle aree e autenticazione.</span><span class="sxs-lookup"><span data-stu-id="d1e24-176">In SharePoint 2013, identity management is factored into the configuration of zones and authentication.</span></span> 
  
<span data-ttu-id="d1e24-177">Questo tipo di progetto vengono sempre nettamente separato di account cliente da tutti gli altri account.</span><span class="sxs-lookup"><span data-stu-id="d1e24-177">This design provides clear separation of customer accounts from all other accounts.</span></span> 
  
- <span data-ttu-id="d1e24-178">Se si desidera che gli account cliente deve essere considerata completamente diverso dall'account interno per gli autori e agli sviluppatori del sito, utilizzare questo tipo di progetto.</span><span class="sxs-lookup"><span data-stu-id="d1e24-178">Use this design if you want customer accounts to be treated entirely different from the internal accounts for authors and site developers.</span></span> 
    
- <span data-ttu-id="d1e24-179">Se si utilizza questo tipo di progetto, è possibile utilizzare i criteri per le aree per limitare le azioni dei clienti in un'applicazione web.</span><span class="sxs-lookup"><span data-stu-id="d1e24-179">By using this design, you can use zone policies to limit customer actions within a web application.</span></span> 
    
- <span data-ttu-id="d1e24-180">Questo tipo di progetto di conseguenza URL diversi per conti cliente e interni.</span><span class="sxs-lookup"><span data-stu-id="d1e24-180">This design results in different URLs for customer accounts and internal accounts.</span></span> 
    
<span data-ttu-id="d1e24-181">In questo esempio:</span><span class="sxs-lookup"><span data-stu-id="d1e24-181">In this example:</span></span> 
  
- <span data-ttu-id="d1e24-182">Configurare l'area predefinita per gli account interni.</span><span class="sxs-lookup"><span data-stu-id="d1e24-182">Configure the default zone for internal accounts.</span></span> 
    
- <span data-ttu-id="d1e24-p112">Configurare l'area extranet per l'accesso autenticato cliente. Utilizzare Azure Active Directory (AD) per gli account dei clienti, oppure un altro provider basata su SAML.</span><span class="sxs-lookup"><span data-stu-id="d1e24-p112">Configure the extranet zone for customer authenticated access. Use Azure Active Directory (AD) for customer accounts, or use a different SAML-based provider.</span></span> 
    
- <span data-ttu-id="d1e24-185">Configurare l'area Internet per l'accesso anonimo.</span><span class="sxs-lookup"><span data-stu-id="d1e24-185">Configure the Internet zone for anonymous access.</span></span> 
    
<span data-ttu-id="d1e24-186">Non utilizzare un progetto di due area in cui tutti gli utenti autenticati sono configurati per utilizzare l'area predefinita.</span><span class="sxs-lookup"><span data-stu-id="d1e24-186">Don't use a two-zone design in which all authenticated users are configured to use the default zone.</span></span> 
  
<span data-ttu-id="d1e24-187">Il diagramma accompagnamento Mostra una progettazione area tre separazione di interni e gli account dei clienti.</span><span class="sxs-lookup"><span data-stu-id="d1e24-187">The accompanying diagram shows a three-zone design with separation of internal and customer accounts.</span></span> 
  
<span data-ttu-id="d1e24-p113">Visitatori e clienti accesso Tenant Azure Active Directory nella farm di SharePoint 2013 attraverso le applicazioni web in una delle due aree. Le due aree includono:</span><span class="sxs-lookup"><span data-stu-id="d1e24-p113">Visitors and customers access the Azure AD Tenant in the SharePoint 2013 farm through web applications in one of two zones. The two zones include:</span></span> 
  
- <span data-ttu-id="d1e24-190">Area: Internet per utenti anonimi</span><span class="sxs-lookup"><span data-stu-id="d1e24-190">Zone: Internet for anonymous users</span></span> 
    
- <span data-ttu-id="d1e24-191">Area: Extranet per gli utenti autenticati</span><span class="sxs-lookup"><span data-stu-id="d1e24-191">Zone: Extranet for authenticated users</span></span> 
    
<span data-ttu-id="d1e24-p114">Gli utenti con account interno accedere Tenant di Azure Active Directory da servizi di dominio Active Directory e di ADFS nell'ambiente locale tramite il tunnel VPN per Azure Active Directory. L'area predefinita fornisce l'autenticazione di Windows (NTLM).</span><span class="sxs-lookup"><span data-stu-id="d1e24-p114">Users with internal accounts access the Azure Active Directory Tenant from AD DS and AD FS in the on-premises environment through the VPN tunnel to Azure AD. The Default zone provides Windows Authentication (NTLM).</span></span> 
  
### <a name="design-for-connecting-to-azure-ad"></a><span data-ttu-id="d1e24-194">Progettazione per la connessione a Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="d1e24-194">Design for connecting to Azure AD</span></span>

 <span data-ttu-id="d1e24-p115">Azure Active Directory fornisce funzionalità di controllo di accesso e gestione identità per servizi basati su cloud. Funzionalità di includere un archivio basato su cloud per dati di directory e un set di componenti di base dei servizi di identità, tra cui i processi di accesso, servizi di autenticazione e di ADFS. L'identità integrazione dei servizi che sono inclusi con Azure Active Directory con facilità con locale distribuzioni di dominio Active Directory e nome provider di identità di terze parti di supporto.</span><span class="sxs-lookup"><span data-stu-id="d1e24-p115">Azure AD provides identity management and access control capabilities for cloud services. Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS. The identity services that are included with Azure AD easily integrate with your on-premises AD DS deployments and fully support third-party identity providers.</span></span>
  
<span data-ttu-id="d1e24-198">Nella figura relativa viene visualizzato lo scenario seguente:</span><span class="sxs-lookup"><span data-stu-id="d1e24-198">The accompanying diagram shows the following scenario:</span></span> 
  
<span data-ttu-id="d1e24-199">Per integrare SharePoint 2013 con Azure Active Directory, un servizio di controllo accesso Azure (ACS) duplice:</span><span class="sxs-lookup"><span data-stu-id="d1e24-199">When integrating SharePoint 2013 with Azure Active Directory, an Azure Access Control Service (ACS) serves two purposes:</span></span> 
  
-  <span data-ttu-id="d1e24-p116">Azure Active Directory utilizza SAML 2.0 e SharePoint funziona solo con SAML 1.1. ACS conosce entrambi i formati e funge da intermediario per trasformare i token formati tra SharePoint e Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d1e24-p116">Azure AD uses SAML 2.0, and SharePoint only works with SAML 1.1. ACS understands both formats and serves as the intermediary to transform the token formats between SharePoint and Azure AD.</span></span>
    
- <span data-ttu-id="d1e24-202">ACS sostituisce la necessità di identity provider servizio token di sicurezza (STS IP) per questo scenario SAML.</span><span class="sxs-lookup"><span data-stu-id="d1e24-202">ACS replaces the need for the identity provider security token service (IP-STS) for this SAML scenario.</span></span> 
    
<span data-ttu-id="d1e24-203">Per ulteriori informazioni, vedere Configure Azure Active Directory con SharePoint 2013 nella libreria TechNet.</span><span class="sxs-lookup"><span data-stu-id="d1e24-203">For more information, see Configure Azure AD with SharePoint 2013 in the TechNet library.</span></span> 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a><span data-ttu-id="d1e24-204">La progettazione di siti e gli URL per la pubblicazione intersito</span><span class="sxs-lookup"><span data-stu-id="d1e24-204">Design sites and URLs for cross-site publishing</span></span>

<span data-ttu-id="d1e24-205">Un'una progettazione dell'applicazione web è consigliata per gli scenari di pubblicazione.</span><span class="sxs-lookup"><span data-stu-id="d1e24-205">A one web-application design is recommended for publishing scenarios.</span></span> 
  
- <span data-ttu-id="d1e24-206">Modifica di e i siti di pubblicazione sono della stessa applicazione web.</span><span class="sxs-lookup"><span data-stu-id="d1e24-206">Both authoring and publishing sites are in the same web application.</span></span> 
    
- <span data-ttu-id="d1e24-207">Pubblicazione intersito viene utilizzata per pubblicare risorse.</span><span class="sxs-lookup"><span data-stu-id="d1e24-207">Cross-site publishing is used to publish assets.</span></span> 
    
<span data-ttu-id="d1e24-208">Utilizzare raccolte siti basate su percorso e nome host.</span><span class="sxs-lookup"><span data-stu-id="d1e24-208">Use path-based and host-named site collections.</span></span> 
  
- <span data-ttu-id="d1e24-p117">Una raccolta siti radice è un requisito. Creare il sito come siti basati sul percorso.</span><span class="sxs-lookup"><span data-stu-id="d1e24-p117">A root site collection is a requirement. Create this site as a path-based site.</span></span> 
    
- <span data-ttu-id="d1e24-211">Creare tutte le altre raccolte siti come raccolte siti con nome host.</span><span class="sxs-lookup"><span data-stu-id="d1e24-211">Create all other site collections as host-named site collections.</span></span> 
    
<span data-ttu-id="d1e24-212">URL del sito radice e applicazione Web</span><span class="sxs-lookup"><span data-stu-id="d1e24-212">Web application and root site URLs</span></span> 
  
- <span data-ttu-id="d1e24-p118">Utilizzare un nome interno per l'URL dell'applicazione web. SharePoint utilizza il nome del computer locale come nome predefinito se non viene specificato un nome diverso. È possibile utilizzare un nome di dominio è riservato per l'ambiente di rete interna.</span><span class="sxs-lookup"><span data-stu-id="d1e24-p118">Use an internal name for the web application URL. SharePoint uses the local machine name as the default name unless a different name is specified. You can use a domain name that is reserved for the internal network environment.</span></span> 
    
- <span data-ttu-id="d1e24-p119">Quando si crea l'applicazione web, SharePoint assegnato un numero di porta non standard. Utilizzare questo numero di porta anziché la porta 80 o 443. Oppure utilizzare un numero di porta diverso, ma non standard.</span><span class="sxs-lookup"><span data-stu-id="d1e24-p119">SharePoint assigns a nonstandard port number when the web application is created. Use this port number instead of port 80 or port 443. Or use a different but nonstandard port number.</span></span> 
    
- <span data-ttu-id="d1e24-219">Utilizzare lo stesso nome e il numero di porta per la raccolta siti radice, che corrisponde a una raccolta siti basata sul percorso.</span><span class="sxs-lookup"><span data-stu-id="d1e24-219">Use the same name and port number for the root site collection, which is a path-based site collection.</span></span> 
    
<span data-ttu-id="d1e24-p120">Il diagramma accompagnamento Mostra servizi dei pool di applicazioni, ad esempio ricerca interagire con le raccolte siti con le applicazioni web. Le raccolte siti riportate includono:</span><span class="sxs-lookup"><span data-stu-id="d1e24-p120">The accompanying diagram shows application pool services such as Search interacting with site collections using web applications. The site collections shown include:</span></span> 
  
- <span data-ttu-id="d1e24-222">Raccolta siti basata su percorso all'http://internal:8000 (sito radice).</span><span class="sxs-lookup"><span data-stu-id="d1e24-222">Path-based site collection located at http://internal:8000 (root site).</span></span> 
    
- <span data-ttu-id="d1e24-223">Ricerca per indicizzazione: Raccolte siti con nome Host disponibile all'indirizzo, ad esempio https://authoring.contoso.com:8000.</span><span class="sxs-lookup"><span data-stu-id="d1e24-223">Crawl: Host-named site collections located at an address such as https://authoring.contoso.com:8000.</span></span> 
    
- <span data-ttu-id="d1e24-224">Query: 2 raccolte siti con nome basato sull'Host separati si trovano in indirizzi come:</span><span class="sxs-lookup"><span data-stu-id="d1e24-224">Queries: 2 separate Host-named site collections located at addresses such as:</span></span> 
    
  - <span data-ttu-id="d1e24-225">http://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="d1e24-225">http://www.contoso.com</span></span> 
    
  - <span data-ttu-id="d1e24-226">https://Secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="d1e24-226">https://secure.contoso.com</span></span> 
    
  - <span data-ttu-id="d1e24-227">http://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="d1e24-227">http://www.contoso.com:8000</span></span> 
    
  - <span data-ttu-id="d1e24-228">http://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="d1e24-228">http://assets.contoso.com</span></span> 
    
  - <span data-ttu-id="d1e24-229">https://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="d1e24-229">https://secureassets.contoso.com</span></span> 
    
  - <span data-ttu-id="d1e24-230">http://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="d1e24-230">http://assets.contoso.com:8000</span></span> 
    
## <a name="design-the-azure-environment"></a><span data-ttu-id="d1e24-231">Progettare l'ambiente Azure</span><span class="sxs-lookup"><span data-stu-id="d1e24-231">Design the Azure environment</span></span>

<span data-ttu-id="d1e24-232">Questa architettura di esempio include gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="d1e24-232">This example architecture includes the following elements:</span></span> 
  
- <span data-ttu-id="d1e24-233">Una connessione VPN da sito è facoltativa ed estende di Windows locale di dominio Active Directory e dell'ambiente DNS per la rete virtuale in Azure.</span><span class="sxs-lookup"><span data-stu-id="d1e24-233">A site-to-site VPN connection is optional and extends the on-premises Windows AD DS and DNS environment to the virtual network in Azure.</span></span> 
    
- <span data-ttu-id="d1e24-234">Facoltativamente, utilizzare un dominio dedicato in Azure per supportare la farm di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d1e24-234">Optionally, use a dedicated domain in Azure to support the SharePoint farm.</span></span> 
    
- <span data-ttu-id="d1e24-235">I server sono suddivisi in tutti i servizi cloud Azure in base al ruolo.</span><span class="sxs-lookup"><span data-stu-id="d1e24-235">Servers are split across Azure cloud services based on role.</span></span> 
    
- <span data-ttu-id="d1e24-236">Set di disponibilità assicurare una disponibilità elevata dei ruoli del server configurati in modo identico.</span><span class="sxs-lookup"><span data-stu-id="d1e24-236">Availability sets ensure high availability of identically configured server roles.</span></span> 
    
<span data-ttu-id="d1e24-237">Per ulteriori informazioni, vedere l'articolo seguente nel sito TechNet: Azure Architectures for SharePoint Solutions.</span><span class="sxs-lookup"><span data-stu-id="d1e24-237">For more information, see the following article on TechNet: Azure Architectures for SharePoint Solutions.</span></span> 
  
<span data-ttu-id="d1e24-238">Nella figura relativa illustrato un esempio di un ambiente locale connessione con una rete virtuale Azure.</span><span class="sxs-lookup"><span data-stu-id="d1e24-238">The accompanying diagram shows an example of an on-premises environment connecting with an Azure virtual network.</span></span> 
  
<span data-ttu-id="d1e24-239">Sono inclusi nell'ambiente locale, ovvero un elemento facoltativo dell'ambiente di Azure, i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="d1e24-239">Included in the on-premises environment, which is an optional element of the Azure environment, are the following components:</span></span> 
  
- <span data-ttu-id="d1e24-240">Configurazione di Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="d1e24-240">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="d1e24-241">Servizi di dominio Active Directory</span><span class="sxs-lookup"><span data-stu-id="d1e24-241">AD DS</span></span> 
    
- <span data-ttu-id="d1e24-242">Un gateway VPN da Windows Server e di dominio Active Directory per la subnet attiva Gateway VPN</span><span class="sxs-lookup"><span data-stu-id="d1e24-242">A VPN gateway from Windows Server and AD DS to the Active VPN Gateway subnet</span></span> 
    
<span data-ttu-id="d1e24-243">L'ambiente di rete virtuale Azure include i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="d1e24-243">The Azure virtual network environment includes the following components:</span></span> 
  
- <span data-ttu-id="d1e24-244">Subnet Gateway VPN attivo (la sovrapposizione con l'ambiente locale, se applicabile)</span><span class="sxs-lookup"><span data-stu-id="d1e24-244">The Active VPN Gateway subnet (overlapping with the on-premises environment, if applicable)</span></span> 
    
- <span data-ttu-id="d1e24-245">Servizio cloud che include la disponibilità di dominio Active Directory e DNS impostato (due server)</span><span class="sxs-lookup"><span data-stu-id="d1e24-245">Cloud service that includes AD DS and DNS availability set (two servers)</span></span> 
    
- <span data-ttu-id="d1e24-246">Servizio cloud che includono la disponibilità di server front-end impostato (tre SharePoint Server) e la disponibilità del server applicazioni (tre SharePoint Server)</span><span class="sxs-lookup"><span data-stu-id="d1e24-246">Cloud service that include the front-end server availability set (three SharePoint servers) and the App server availability set (three SharePoint servers)</span></span> 
    
- <span data-ttu-id="d1e24-247">Imposta cloud Services contenente due la disponibilità del database</span><span class="sxs-lookup"><span data-stu-id="d1e24-247">Cloud service that contains two database availability sets</span></span> 
    

