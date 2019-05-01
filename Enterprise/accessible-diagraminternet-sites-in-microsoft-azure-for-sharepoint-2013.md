---
title: Diagramma accessibile-siti Internet in Microsoft Azure per SharePoint 2013
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
description: Questo articolo è una versione di testo accessibile del diagramma denominato siti Internet in Microsoft Azure per SharePoint 2013.
ms.openlocfilehash: 59c84e34ab4d748a80ab0a597817ae4d3464a43c
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487693"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="54862-103">Diagramma accessibile-siti Internet in Microsoft Azure per SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="54862-103">Accessible diagram - Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="54862-104">**Riepilogo:** Questo articolo è una versione di testo accessibile del diagramma denominato siti Internet in Microsoft Azure per SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="54862-104">**Summary:** This article is an accessible text version of the diagram named Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="54862-105">Questo poster descrive e illustra come i siti Internet con accesso pubblico traggono vantaggio dall'elasticità cloud e da Azure AD per gli account dei clienti.</span><span class="sxs-lookup"><span data-stu-id="54862-105">This poster describes and illustrates how public-facing Internet sites benefit from cloud elasticity and Azure AD for customer accounts.</span></span> <span data-ttu-id="54862-106">Esistono sei diversi scenari che descrivono come i siti Internet traggono vantaggio da Azure:</span><span class="sxs-lookup"><span data-stu-id="54862-106">There are six different scenarios that describe how Internet sites benefit from Azure:</span></span> 
  
- <span data-ttu-id="54862-107">Progettare e ridimensionare la topologia della farm.</span><span class="sxs-lookup"><span data-stu-id="54862-107">Design and size the farm topology.</span></span> 
    
- <span data-ttu-id="54862-108">Ottimizzare la precisione per Azure.</span><span class="sxs-lookup"><span data-stu-id="54862-108">Fine-tune for Azure.</span></span> 
    
- <span data-ttu-id="54862-109">Scegliere il modello di Active Directory.</span><span class="sxs-lookup"><span data-stu-id="54862-109">Choose the Active Directory model.</span></span> 
    
- <span data-ttu-id="54862-110">Progettazione per la gestione delle identità, le aree e l'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="54862-110">Design for identity management, zones, and authentication.</span></span> 
    
- <span data-ttu-id="54862-111">Progettare siti e URL per la pubblicazione intersito.</span><span class="sxs-lookup"><span data-stu-id="54862-111">Design sites and URLs for cross-site publishing.</span></span> 
    
- <span data-ttu-id="54862-112">Progettare l'ambiente di Azure.</span><span class="sxs-lookup"><span data-stu-id="54862-112">Design the Azure environment.</span></span> 
    
## <a name="design-and-size-the-farm-topology"></a><span data-ttu-id="54862-113">Progettare e ridimensionare la topologia della farm</span><span class="sxs-lookup"><span data-stu-id="54862-113">Design and size the farm topology</span></span>

<span data-ttu-id="54862-114">Utilizzare le linee guida per la topologia, la capacità e le prestazioni per SharePoint 2013 su TechNet per progettare la topologia della farm.</span><span class="sxs-lookup"><span data-stu-id="54862-114">Use the topology, capacity, and performance guidance for SharePoint 2013 on TechNet to design the farm topology.</span></span> 
  
<span data-ttu-id="54862-115">Verificare che la farm che si progetta soddisfi gli obiettivi di capacità e prestazioni.</span><span class="sxs-lookup"><span data-stu-id="54862-115">Ensure the farm you design meets the objectives for capacity and performance.</span></span> 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a><span data-ttu-id="54862-116">Esempio: farm di siti Internet di medie dimensioni (~ 85 visualizzazioni di pagina al secondo)</span><span class="sxs-lookup"><span data-stu-id="54862-116">Example: Medium Internet Sites farm (~85 page views per second)</span></span>

<span data-ttu-id="54862-117">Questa farm fornisce una topologia della farm di ricerca di SharePoint 2013 con tolleranza di errore che è ottimizzata per un corpo contenente 3,4 milioni elementi.</span><span class="sxs-lookup"><span data-stu-id="54862-117">This farm provides a fault-tolerant SharePoint 2013 search farm topology that is optimized for a corpus that contains 3,400,000 items.</span></span> 
  
<span data-ttu-id="54862-118">La farm di esempio elabora 100-200 documenti al secondo, a seconda della lingua, e ospita 85 visualizzazioni di pagina al secondo e 100 query al secondo.</span><span class="sxs-lookup"><span data-stu-id="54862-118">The example farm processes 100-200 documents per second, depending on the language, and it accommodates 85 page views per second and 100 queries per second.</span></span> 
  
<span data-ttu-id="54862-119">Nel diagramma di accompagnamento viene illustrata una farm di siti Internet di medie dimensioni con tre tipi di server:</span><span class="sxs-lookup"><span data-stu-id="54862-119">The accompanying diagram shows a medium internet sites farm with three types of servers:</span></span> 
  
- <span data-ttu-id="54862-120">Server Web</span><span class="sxs-lookup"><span data-stu-id="54862-120">Web servers</span></span> 
    
- <span data-ttu-id="54862-121">Server applicazioni</span><span class="sxs-lookup"><span data-stu-id="54862-121">Application servers</span></span> 
    
- <span data-ttu-id="54862-122">Server di database</span><span class="sxs-lookup"><span data-stu-id="54862-122">Database servers</span></span> 
    
#### <a name="web-servers"></a><span data-ttu-id="54862-123">Server Web</span><span class="sxs-lookup"><span data-stu-id="54862-123">Web servers</span></span>

<span data-ttu-id="54862-124">Nella sezione server Web sono disponibili tre server Web, host A, host B e host C. Ogni server Web contiene una cache distribuita, profili utente, metadati gestiti e funzionalità di elaborazione delle query.</span><span class="sxs-lookup"><span data-stu-id="54862-124">In the web servers section, there are three web servers, Host A, Host B, and Host C. Each web server contains a distributed cache, user profiles, managed metadata, and query processing capabilities.</span></span> <span data-ttu-id="54862-125">Contengono anche una replica di partizione di indice presente in ogni server.</span><span class="sxs-lookup"><span data-stu-id="54862-125">They also contain an index partition replica that is in each server.</span></span> 
  
<span data-ttu-id="54862-126">Per eseguire la scalabilità orizzontale, aggiungere un ulteriore server Web con le stesse funzionalità, che consente di ottenere altre 28 visualizzazioni di pagina al secondo.</span><span class="sxs-lookup"><span data-stu-id="54862-126">To scale out, add an additional web server with the same capabilities, which allows for an additional 28 page views per second.</span></span> 
  
#### <a name="application-servers"></a><span data-ttu-id="54862-127">Server applicazioni</span><span class="sxs-lookup"><span data-stu-id="54862-127">Application servers</span></span>

<span data-ttu-id="54862-128">Nella sezione Server applicazioni esistono tre server applicazioni, host D, host E e host F. host D contenente i componenti di ricerca per inDicizzazione, amministrazione, analisi e elaborazione del contenuto.</span><span class="sxs-lookup"><span data-stu-id="54862-128">In the application servers section, there are three application servers, Host D, Host E, and Host F. Host D contains Crawl, Admin, Analytics, and Content processing components.</span></span> <span data-ttu-id="54862-129">Host E contiene componenti di ricerca per inDicizzazione, amministrazione e elaborazione del contenuto.</span><span class="sxs-lookup"><span data-stu-id="54862-129">Host E contains Crawl, Admin, and Content processing components.</span></span> <span data-ttu-id="54862-130">Host F contiene i componenti di ricerca per inDicizzazione e elaborazione del contenuto.</span><span class="sxs-lookup"><span data-stu-id="54862-130">Host F contains Crawl and Content processing components.</span></span> 
  
<span data-ttu-id="54862-131">Per eseguire la scalabilità orizzontale, aggiungere un server applicazioni con un componente di ricerca per indicizzazione e un componente di elaborazione del contenuto per elaborare un ulteriore 40 documenti al secondo.</span><span class="sxs-lookup"><span data-stu-id="54862-131">To scale out, add one application server with a crawl component and a content processing component to process an additional 40 documents per second.</span></span> 
  
#### <a name="database-servers"></a><span data-ttu-id="54862-132">Server di database</span><span class="sxs-lookup"><span data-stu-id="54862-132">Database servers</span></span>

<span data-ttu-id="54862-133">Nella sezione Server database sono disponibili due server, ovvero host G e host H. I server di database sono inclusi in host associati per la tolleranza di errore.</span><span class="sxs-lookup"><span data-stu-id="54862-133">In the database servers section, there are two servers, Host G and Host H. The database servers are in paired hosts for fault tolerance.</span></span> 
  
<span data-ttu-id="54862-134">L'host G contiene tutti i database di SharePoint, inclusi il database di amministrazione della ricerca, il database dei collegamenti, due database per inDicizzazione, un database di analisi e tutti i database di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="54862-134">Host G contains all SharePoint database, including Search admin database, Link database, two Crawl databases, an Analytics database, and all other SharePoint databases.</span></span> <span data-ttu-id="54862-135">Host H contiene tutti i database di SharePoint, incluse le copie ridondanti di tutti i database che utilizzano il clustering SQL, il mirroring o SQL Server 2012 AlwaysOn.</span><span class="sxs-lookup"><span data-stu-id="54862-135">Host H contains all SharePoint databases, including redundant copies of all databases using SQL clustering, mirroring, or SQL Server 2012 AlwaysOn.</span></span> 
  
## <a name="fine-tune-for-azure"></a><span data-ttu-id="54862-136">Ottimizzazione per Azure</span><span class="sxs-lookup"><span data-stu-id="54862-136">Fine-tune for Azure</span></span>

<span data-ttu-id="54862-137">Potrebbe essere necessario ottimizzare la farm di SharePoint per i set di disponibilità nella piattaforma di Azure.</span><span class="sxs-lookup"><span data-stu-id="54862-137">The SharePoint farm might need to be fine-tuned for availability sets in the Azure platform.</span></span> <span data-ttu-id="54862-138">Per garantire la disponibilità elevata di tutti i componenti, verificare che i ruoli del server siano tutti configurati in modo identico.</span><span class="sxs-lookup"><span data-stu-id="54862-138">To ensure high availability of all components, ensure that the server roles are all identically configured.</span></span> 
  
<span data-ttu-id="54862-139">Nella topologia di esempio nel diagramma:</span><span class="sxs-lookup"><span data-stu-id="54862-139">In the example topology in the diagram:</span></span> 
  
- <span data-ttu-id="54862-140">I server Web e i server di database sono configurati in modo identico.</span><span class="sxs-lookup"><span data-stu-id="54862-140">The web servers and the database servers are identically configured.</span></span> 
    
- <span data-ttu-id="54862-141">I tre server applicazioni non sono configurati in modo identico.</span><span class="sxs-lookup"><span data-stu-id="54862-141">The three application servers are not identically configured.</span></span> <span data-ttu-id="54862-142">Questi ruoli del server richiedono l'ottimizzazione per i set di disponibilità in Azure.</span><span class="sxs-lookup"><span data-stu-id="54862-142">These server roles require fine tuning for availability sets in Azure.</span></span> 
    
### <a name="before"></a><span data-ttu-id="54862-143">Prima</span><span class="sxs-lookup"><span data-stu-id="54862-143">Before</span></span>

<span data-ttu-id="54862-144">La parte superiore del diagramma Visualizza la farm di SharePoint prima che sia stata ottimizzata per i set di disponibilità in Azure.</span><span class="sxs-lookup"><span data-stu-id="54862-144">The top portion of the diagram shows the SharePoint farm before it has been fine-tuned for availability sets in Azure.</span></span> <span data-ttu-id="54862-145">Nel diagramma, i tre server applicazioni host non sono configurati in modo identico.</span><span class="sxs-lookup"><span data-stu-id="54862-145">In the diagram, the three host application servers are not identically configured.</span></span> <span data-ttu-id="54862-146">Il numero di componenti è determinato dagli obiettivi di prestazioni e capacità per la farm.</span><span class="sxs-lookup"><span data-stu-id="54862-146">The number of components is determined by the performance and capacity targets for the farm.</span></span> <span data-ttu-id="54862-147">I tre server sono configurati come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="54862-147">The three servers are configured as follows:</span></span> 
  
- <span data-ttu-id="54862-148">Host D Application Server è configurato con ruoli di ricerca per inDicizzazione, amministrazione, analisi e elaborazione del contenuto.</span><span class="sxs-lookup"><span data-stu-id="54862-148">Host D application server is configured with Crawl, Admin, Analytics, and Content processing roles.</span></span> 
    
- <span data-ttu-id="54862-149">Host E Application Server è configurato con i ruoli di elaborazione di ricerca per inDicizzazione, amministrazione e contenuto.</span><span class="sxs-lookup"><span data-stu-id="54862-149">Host E application server is configured with Crawl, Admin, and Content processing roles.</span></span> 
    
- <span data-ttu-id="54862-150">Il server applicazioni F host è configurato con i ruoli di ricerca per inDicizzazione e elaborazione del contenuto.</span><span class="sxs-lookup"><span data-stu-id="54862-150">Host F application server is configured with Crawl and Content processing roles.</span></span> 
    
### <a name="after"></a><span data-ttu-id="54862-151">Dopo</span><span class="sxs-lookup"><span data-stu-id="54862-151">After</span></span>

<span data-ttu-id="54862-152">Questa parte del diagramma Visualizza la farm di SharePoint dopo che è stata ottimizzata per i set di disponibilità in Azure.</span><span class="sxs-lookup"><span data-stu-id="54862-152">This part of the diagram shows the SharePoint farm after it has been fine-tuned for availability sets in Azure.</span></span> <span data-ttu-id="54862-153">Per adattare questa architettura per Azure, è possibile replicare i quattro componenti in tutti e tre i server.</span><span class="sxs-lookup"><span data-stu-id="54862-153">To adapt this architecture for Azure, we'll replicate the four components across all three servers.</span></span> <span data-ttu-id="54862-154">Questo aumenta il numero di componenti oltre ciò che è necessario per le prestazioni e la capacità.</span><span class="sxs-lookup"><span data-stu-id="54862-154">This increases the number of components beyond what is necessary for performance and capacity.</span></span> <span data-ttu-id="54862-155">Il compromesso è che questa struttura garantisce una disponibilità elevata di tutti e quattro i componenti della piattaforma di Azure quando queste tre macchine virtuali vengono assegnate a un set di disponibilità.</span><span class="sxs-lookup"><span data-stu-id="54862-155">The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span> 
  
<span data-ttu-id="54862-156">I tre server sono configurati per tutti i ruoli di ricerca per inDicizzazione, amministrazione, analisi e elaborazione del contenuto.</span><span class="sxs-lookup"><span data-stu-id="54862-156">The three servers are configured to all have the Crawl, Admin, Analytics, and Content processing roles.</span></span> 
  
## <a name="choose-the-active-directory-model"></a><span data-ttu-id="54862-157">Scegliere il modello di Active Directory</span><span class="sxs-lookup"><span data-stu-id="54862-157">Choose the Active Directory model</span></span>

<span data-ttu-id="54862-158">Tutte le soluzioni di SharePoint richiedono Windows Active Directory Domain Services (AD DS).</span><span class="sxs-lookup"><span data-stu-id="54862-158">All SharePoint solutions require Windows Active Directory Domain Services (AD DS).</span></span> <span data-ttu-id="54862-159">In questo momento, sono disponibili due opzioni per le soluzioni SharePoint in Azure.</span><span class="sxs-lookup"><span data-stu-id="54862-159">At this time, there are two options for SharePoint solutions in Azure.</span></span> 
  
- <span data-ttu-id="54862-160">Opzione 1: dominio dedicato-è possibile distribuire un dominio dedicato e isolato in Azure per supportare una farm di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="54862-160">Option 1: Dedicated domain — You can deploy a dedicated and isolated domain to Azure to support a SharePoint farm.</span></span> <span data-ttu-id="54862-161">Questa è una buona scelta per i siti Internet di pubblico dominio.</span><span class="sxs-lookup"><span data-stu-id="54862-161">This is a good choice for public-facing Internet sites.</span></span> 
    
- <span data-ttu-id="54862-162">Opzione 2: estendere il dominio locale tramite una connessione VPN da sito a sito.</span><span class="sxs-lookup"><span data-stu-id="54862-162">Option 2: Extend the on-premises domain through a site-to-site VPN connection.</span></span> <span data-ttu-id="54862-163">Quando si estende il dominio locale tramite una connessione VPN da sito a sito, gli utenti accedono alla farm di SharePoint come se fossero ospitati in locale.</span><span class="sxs-lookup"><span data-stu-id="54862-163">When you extend the on-premises domain through a site-to-site VPN connection, users access the SharePoint farm as if it were hosted on-premises.</span></span> <span data-ttu-id="54862-164">È possibile usufruire delle implementazioni di Active Directory e DNS esistenti.</span><span class="sxs-lookup"><span data-stu-id="54862-164">You can take advantage of your existing Active Directory and DNS implementations.</span></span> 
    
## <a name="design-for-identity-management-zones-and-authentication"></a><span data-ttu-id="54862-165">Progettazione per la gestione delle identità, le aree e l'autenticazione</span><span class="sxs-lookup"><span data-stu-id="54862-165">Design for identity management, zones, and authentication</span></span>

### <a name="design-for-accounts-and-authentication"></a><span data-ttu-id="54862-166">Progettazione per account e autenticazione</span><span class="sxs-lookup"><span data-stu-id="54862-166">Design for accounts and authentication</span></span>

<span data-ttu-id="54862-167">Determinare la modalità di gestione degli account e il tipo di autenticazione da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="54862-167">Determine how accounts will be managed and which type of authentication will be used.</span></span> 
  
#### <a name="accounts-for-site-developers-and-authors"></a><span data-ttu-id="54862-168">Account per sviluppatori e autori di siti</span><span class="sxs-lookup"><span data-stu-id="54862-168">Accounts for site developers and authors</span></span>

- <span data-ttu-id="54862-169">Aggiungere account al dominio in Azure.</span><span class="sxs-lookup"><span data-stu-id="54862-169">Add accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="54862-170">Utilizzare Active Directory Federation Services (ADFS) in locale per la Federazione degli account interni per il dominio in Azure.</span><span class="sxs-lookup"><span data-stu-id="54862-170">Use Active Directory Federation Services (AD FS) on premises to federate the internal accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="54862-171">Se nella struttura è inclusa una connessione VPN da sito a sito, utilizzare gli account interni.</span><span class="sxs-lookup"><span data-stu-id="54862-171">If the design includes a site-to-site VPN connection, use the internal accounts.</span></span> 
    
#### <a name="accounts-for-customers"></a><span data-ttu-id="54862-172">Account per i clienti</span><span class="sxs-lookup"><span data-stu-id="54862-172">Accounts for customers</span></span>

- <span data-ttu-id="54862-173">Utilizzare Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="54862-173">Use Azure Active Directory.</span></span> 
    
- <span data-ttu-id="54862-174">Utilizzare un altro provider basato su SAML.</span><span class="sxs-lookup"><span data-stu-id="54862-174">Use a different SAML-based provider.</span></span> 
    
### <a name="design-for-zones"></a><span data-ttu-id="54862-175">Progettazione per le aree</span><span class="sxs-lookup"><span data-stu-id="54862-175">Design for zones</span></span>

<span data-ttu-id="54862-176">In SharePoint 2013, la gestione delle identità viene fattorizzata nella configurazione delle aree e dell'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="54862-176">In SharePoint 2013, identity management is factored into the configuration of zones and authentication.</span></span> 
  
<span data-ttu-id="54862-177">Questa struttura fornisce una chiara separazione degli account dei clienti da tutti gli altri account.</span><span class="sxs-lookup"><span data-stu-id="54862-177">This design provides clear separation of customer accounts from all other accounts.</span></span> 
  
- <span data-ttu-id="54862-178">Utilizzare questa struttura se si desidera che gli account dei clienti vengano trattati completamente diversi dagli account interni per autori e sviluppatori di siti.</span><span class="sxs-lookup"><span data-stu-id="54862-178">Use this design if you want customer accounts to be treated entirely different from the internal accounts for authors and site developers.</span></span> 
    
- <span data-ttu-id="54862-179">Se si utilizza questa struttura, è possibile utilizzare i criteri di area per limitare le azioni dei clienti all'interno di un'applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="54862-179">By using this design, you can use zone policies to limit customer actions within a web application.</span></span> 
    
- <span data-ttu-id="54862-180">Questa struttura genera URL diversi per gli account dei clienti e gli account interni.</span><span class="sxs-lookup"><span data-stu-id="54862-180">This design results in different URLs for customer accounts and internal accounts.</span></span> 
    
<span data-ttu-id="54862-181">In questo esempio:</span><span class="sxs-lookup"><span data-stu-id="54862-181">In this example:</span></span> 
  
- <span data-ttu-id="54862-182">Configurare l'area predefinita per gli account interni.</span><span class="sxs-lookup"><span data-stu-id="54862-182">Configure the default zone for internal accounts.</span></span> 
    
- <span data-ttu-id="54862-183">Configurare l'area Extranet per l'accesso con autenticazione dei clienti.</span><span class="sxs-lookup"><span data-stu-id="54862-183">Configure the extranet zone for customer authenticated access.</span></span> <span data-ttu-id="54862-184">Utilizzare Azure Active Directory (AD) per gli account dei clienti oppure utilizzare un altro provider basato su SAML.</span><span class="sxs-lookup"><span data-stu-id="54862-184">Use Azure Active Directory (AD) for customer accounts, or use a different SAML-based provider.</span></span> 
    
- <span data-ttu-id="54862-185">Configurare l'area Internet per l'accesso anonimo.</span><span class="sxs-lookup"><span data-stu-id="54862-185">Configure the Internet zone for anonymous access.</span></span> 
    
<span data-ttu-id="54862-186">Non utilizzare una struttura a due aree in cui tutti gli utenti autenticati sono configurati per l'utilizzo dell'area predefinita.</span><span class="sxs-lookup"><span data-stu-id="54862-186">Don't use a two-zone design in which all authenticated users are configured to use the default zone.</span></span> 
  
<span data-ttu-id="54862-187">Il diagramma di accompagnamento Visualizza una struttura a tre aree con la separazione degli account interni e dei clienti.</span><span class="sxs-lookup"><span data-stu-id="54862-187">The accompanying diagram shows a three-zone design with separation of internal and customer accounts.</span></span> 
  
<span data-ttu-id="54862-188">I visitatori e i clienti accedono al tenant di Azure AD nella farm di SharePoint 2013 tramite le applicazioni Web in una delle due aree.</span><span class="sxs-lookup"><span data-stu-id="54862-188">Visitors and customers access the Azure AD Tenant in the SharePoint 2013 farm through web applications in one of two zones.</span></span> <span data-ttu-id="54862-189">Tra le due aree sono incluse le seguenti:</span><span class="sxs-lookup"><span data-stu-id="54862-189">The two zones include:</span></span> 
  
- <span data-ttu-id="54862-190">Area: Internet per gli utenti anonimi</span><span class="sxs-lookup"><span data-stu-id="54862-190">Zone: Internet for anonymous users</span></span> 
    
- <span data-ttu-id="54862-191">Area: Extranet per gli utenti autenticati</span><span class="sxs-lookup"><span data-stu-id="54862-191">Zone: Extranet for authenticated users</span></span> 
    
<span data-ttu-id="54862-192">Gli utenti con account interni accedono al tenant di Azure Active Directory da AD DS e AD FS nell'ambiente locale tramite il tunnel VPN ad Azure AD.</span><span class="sxs-lookup"><span data-stu-id="54862-192">Users with internal accounts access the Azure Active Directory Tenant from AD DS and AD FS in the on-premises environment through the VPN tunnel to Azure AD.</span></span> <span data-ttu-id="54862-193">L'area predefinita fornisce l'autenticazione di Windows (NTLM).</span><span class="sxs-lookup"><span data-stu-id="54862-193">The Default zone provides Windows Authentication (NTLM).</span></span> 
  
### <a name="design-for-connecting-to-azure-ad"></a><span data-ttu-id="54862-194">Progettazione per la connessione ad Azure AD</span><span class="sxs-lookup"><span data-stu-id="54862-194">Design for connecting to Azure AD</span></span>

 <span data-ttu-id="54862-195">Azure AD offre funzionalità di gestione delle identità e controllo di accesso per i servizi cloud.</span><span class="sxs-lookup"><span data-stu-id="54862-195">Azure AD provides identity management and access control capabilities for cloud services.</span></span> <span data-ttu-id="54862-196">Le funzionalità includono un archivio basato sul cloud per i dati di directory e un set di base di servizi di identità, tra cui processi di accesso degli utenti, servizi di autenticazione e AD FS.</span><span class="sxs-lookup"><span data-stu-id="54862-196">Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS.</span></span> <span data-ttu-id="54862-197">I servizi Identity inclusi in Azure AD si integrano facilmente con le distribuzioni di servizi di dominio Active Directory locali e supportano completamente i provider di identità di terze parti.</span><span class="sxs-lookup"><span data-stu-id="54862-197">The identity services that are included with Azure AD easily integrate with your on-premises AD DS deployments and fully support third-party identity providers.</span></span>
  
<span data-ttu-id="54862-198">Nel diagramma che segue è illustrato lo scenario seguente:</span><span class="sxs-lookup"><span data-stu-id="54862-198">The accompanying diagram shows the following scenario:</span></span> 
  
<span data-ttu-id="54862-199">Quando si integra SharePoint 2013 con Azure Active Directory, un servizio di controllo di accesso di Azure serve due scopi:</span><span class="sxs-lookup"><span data-stu-id="54862-199">When integrating SharePoint 2013 with Azure Active Directory, an Azure Access Control Service (ACS) serves two purposes:</span></span> 
  
-  <span data-ttu-id="54862-200">Azure AD utilizza SAML 2,0 e SharePoint funziona solo con SAML 1,1.</span><span class="sxs-lookup"><span data-stu-id="54862-200">Azure AD uses SAML 2.0, and SharePoint only works with SAML 1.1.</span></span> <span data-ttu-id="54862-201">ACS riconosce entrambi i formati e funge da intermediario per la trasformazione dei formati di token tra SharePoint e Azure AD.</span><span class="sxs-lookup"><span data-stu-id="54862-201">ACS understands both formats and serves as the intermediary to transform the token formats between SharePoint and Azure AD.</span></span>
    
- <span data-ttu-id="54862-202">ACS sostituisce la necessità del servizio token di sicurezza del provider di identità per questo scenario SAML.</span><span class="sxs-lookup"><span data-stu-id="54862-202">ACS replaces the need for the identity provider security token service (IP-STS) for this SAML scenario.</span></span> 
    
<span data-ttu-id="54862-203">Per ulteriori informazioni, vedere Configurare Azure AD con SharePoint 2013 nella libreria TechNet.</span><span class="sxs-lookup"><span data-stu-id="54862-203">For more information, see Configure Azure AD with SharePoint 2013 in the TechNet library.</span></span> 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a><span data-ttu-id="54862-204">Progettare siti e URL per la pubblicazione intersito</span><span class="sxs-lookup"><span data-stu-id="54862-204">Design sites and URLs for cross-site publishing</span></span>

<span data-ttu-id="54862-205">Per gli scenari di pubblicazione è consigliata una progettazione di un'applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="54862-205">A one web-application design is recommended for publishing scenarios.</span></span> 
  
- <span data-ttu-id="54862-206">Entrambi i siti di creazione e modifica sono presenti nella stessa applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="54862-206">Both authoring and publishing sites are in the same web application.</span></span> 
    
- <span data-ttu-id="54862-207">La pubblicazione intersito viene utilizzata per pubblicare le risorse.</span><span class="sxs-lookup"><span data-stu-id="54862-207">Cross-site publishing is used to publish assets.</span></span> 
    
<span data-ttu-id="54862-208">Utilizzare le raccolte siti basate su percorso e con nome host.</span><span class="sxs-lookup"><span data-stu-id="54862-208">Use path-based and host-named site collections.</span></span> 
  
- <span data-ttu-id="54862-209">Una raccolta siti radice è un requisito.</span><span class="sxs-lookup"><span data-stu-id="54862-209">A root site collection is a requirement.</span></span> <span data-ttu-id="54862-210">Creare questo sito come sito basato su percorso.</span><span class="sxs-lookup"><span data-stu-id="54862-210">Create this site as a path-based site.</span></span> 
    
- <span data-ttu-id="54862-211">Creare tutte le altre raccolte siti come raccolte siti con nome host.</span><span class="sxs-lookup"><span data-stu-id="54862-211">Create all other site collections as host-named site collections.</span></span> 
    
<span data-ttu-id="54862-212">URL del sito radice e dell'applicazione Web</span><span class="sxs-lookup"><span data-stu-id="54862-212">Web application and root site URLs</span></span> 
  
- <span data-ttu-id="54862-213">Utilizzare un nome interno per l'URL dell'applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="54862-213">Use an internal name for the web application URL.</span></span> <span data-ttu-id="54862-214">SharePoint utilizza il nome del computer locale come nome predefinito, a meno che non venga specificato un nome diverso.</span><span class="sxs-lookup"><span data-stu-id="54862-214">SharePoint uses the local machine name as the default name unless a different name is specified.</span></span> <span data-ttu-id="54862-215">È possibile utilizzare un nome di dominio riservato per l'ambiente di rete interno.</span><span class="sxs-lookup"><span data-stu-id="54862-215">You can use a domain name that is reserved for the internal network environment.</span></span> 
    
- <span data-ttu-id="54862-216">SharePoint assegna un numero di porta non standard quando si crea l'applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="54862-216">SharePoint assigns a nonstandard port number when the web application is created.</span></span> <span data-ttu-id="54862-217">Utilizzare questo numero di porta anziché la porta 80 o la porta 443.</span><span class="sxs-lookup"><span data-stu-id="54862-217">Use this port number instead of port 80 or port 443.</span></span> <span data-ttu-id="54862-218">Oppure utilizzare un numero di porta diverso ma non standard.</span><span class="sxs-lookup"><span data-stu-id="54862-218">Or use a different but nonstandard port number.</span></span> 
    
- <span data-ttu-id="54862-219">Utilizzare lo stesso nome e il numero di porta per la raccolta siti radice, che è una raccolta siti basata su percorso.</span><span class="sxs-lookup"><span data-stu-id="54862-219">Use the same name and port number for the root site collection, which is a path-based site collection.</span></span> 
    
<span data-ttu-id="54862-220">Nel diagramma di accompagnamento vengono illustrati i servizi del pool di applicazioni, ad esempio la ricerca che interagisce con le raccolte siti tramite applicazioni Web.</span><span class="sxs-lookup"><span data-stu-id="54862-220">The accompanying diagram shows application pool services such as Search interacting with site collections using web applications.</span></span> <span data-ttu-id="54862-221">Le raccolte siti mostrate includono:</span><span class="sxs-lookup"><span data-stu-id="54862-221">The site collections shown include:</span></span> 
  
- <span data-ttu-id="54862-222">Raccolta siti basata su percorso disponibile in http://internal:8000 (sito radice).</span><span class="sxs-lookup"><span data-stu-id="54862-222">Path-based site collection located at http://internal:8000 (root site).</span></span> 
    
- <span data-ttu-id="54862-223">Ricerca per inDicizzazione: raccolte siti con nome basato sull'host https://authoring.contoso.com:8000situate in un indirizzo, ad esempio.</span><span class="sxs-lookup"><span data-stu-id="54862-223">Crawl: Host-named site collections located at an address such as https://authoring.contoso.com:8000.</span></span> 
    
- <span data-ttu-id="54862-224">Query: 2 raccolte siti con nome host distinte situate in indirizzi quali:</span><span class="sxs-lookup"><span data-stu-id="54862-224">Queries: 2 separate Host-named site collections located at addresses such as:</span></span> 
    
  - http://www.contoso.com 
    
  - https://secure.contoso.com 
    
  - http://www.contoso.com:8000 
    
  - http://assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - http://assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a><span data-ttu-id="54862-225">Progettare l'ambiente di Azure</span><span class="sxs-lookup"><span data-stu-id="54862-225">Design the Azure environment</span></span>

<span data-ttu-id="54862-226">In questo esempio di architettura sono inclusi gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="54862-226">This example architecture includes the following elements:</span></span> 
  
- <span data-ttu-id="54862-227">Una connessione VPN da sito a sito è facoltativa e estende l'ambiente Windows AD DS e DNS locale alla rete virtuale in Azure.</span><span class="sxs-lookup"><span data-stu-id="54862-227">A site-to-site VPN connection is optional and extends the on-premises Windows AD DS and DNS environment to the virtual network in Azure.</span></span> 
    
- <span data-ttu-id="54862-228">Facoltativamente, utilizzare un dominio dedicato in Azure per supportare la farm di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="54862-228">Optionally, use a dedicated domain in Azure to support the SharePoint farm.</span></span> 
    
- <span data-ttu-id="54862-229">I server sono suddivisi tra i servizi cloud di Azure in base al ruolo.</span><span class="sxs-lookup"><span data-stu-id="54862-229">Servers are split across Azure cloud services based on role.</span></span> 
    
- <span data-ttu-id="54862-230">I set di disponibilità garantiscono un'elevata disponibilità dei ruoli server configurati in modo identico.</span><span class="sxs-lookup"><span data-stu-id="54862-230">Availability sets ensure high availability of identically configured server roles.</span></span> 
    
<span data-ttu-id="54862-231">Per ulteriori informazioni, vedere il seguente articolo su TechNet: architetture di Azure per le soluzioni di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="54862-231">For more information, see the following article on TechNet: Azure Architectures for SharePoint Solutions.</span></span> 
  
<span data-ttu-id="54862-232">Nel diagramma di accompagnamento viene illustrato un esempio di un ambiente locale che si connette a una rete virtuale di Azure.</span><span class="sxs-lookup"><span data-stu-id="54862-232">The accompanying diagram shows an example of an on-premises environment connecting with an Azure virtual network.</span></span> 
  
<span data-ttu-id="54862-233">Sono inclusi nell'ambiente locale, che è un elemento facoltativo dell'ambiente di Azure, i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="54862-233">Included in the on-premises environment, which is an optional element of the Azure environment, are the following components:</span></span> 
  
- <span data-ttu-id="54862-234">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="54862-234">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="54862-235">Servizi di dominio Active Directory</span><span class="sxs-lookup"><span data-stu-id="54862-235">AD DS</span></span> 
    
- <span data-ttu-id="54862-236">Un gateway VPN da Windows Server e servizi di dominio Active Directory alla subnet del gateway VPN attivo</span><span class="sxs-lookup"><span data-stu-id="54862-236">A VPN gateway from Windows Server and AD DS to the Active VPN Gateway subnet</span></span> 
    
<span data-ttu-id="54862-237">L'ambiente di rete virtuale di Azure include i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="54862-237">The Azure virtual network environment includes the following components:</span></span> 
  
- <span data-ttu-id="54862-238">Subnet del gateway VPN attivo (sovrapposto all'ambiente locale, se applicabile)</span><span class="sxs-lookup"><span data-stu-id="54862-238">The Active VPN Gateway subnet (overlapping with the on-premises environment, if applicable)</span></span> 
    
- <span data-ttu-id="54862-239">Servizio cloud che include servizi di dominio Active Directory e set di disponibilità DNS (due server)</span><span class="sxs-lookup"><span data-stu-id="54862-239">Cloud service that includes AD DS and DNS availability set (two servers)</span></span> 
    
- <span data-ttu-id="54862-240">Servizio cloud che include il set di disponibilità del server front-end (tre SharePoint Server) e il set di disponibilità del server app (tre server di SharePoint)</span><span class="sxs-lookup"><span data-stu-id="54862-240">Cloud service that include the front-end server availability set (three SharePoint servers) and the App server availability set (three SharePoint servers)</span></span> 
    
- <span data-ttu-id="54862-241">Servizio cloud che contiene due set di disponibilità del database</span><span class="sxs-lookup"><span data-stu-id="54862-241">Cloud service that contains two database availability sets</span></span> 
    

