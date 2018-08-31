---
title: Scenari cloud ibridi per Azure PaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: 'Riepilogo: Informazioni su architettura ibrida e gli scenari per la piattaforma Microsoft come servizio (PaaS)-basato su cloud offerte in Azure.'
ms.openlocfilehash: e60bc92eed45e5d29fe0be80320dee65b8325028
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915011"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="fb2c2-103">Scenari cloud ibridi per Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="fb2c2-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="fb2c2-104">**Riepilogo:** Acquisire familiarità con l'architettura ibrida e gli scenari per la piattaforma Microsoft come servizio (PaaS)-basato su cloud offerte in Azure.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="fb2c2-105">Combinare dati locali o le risorse di elaborazione con nuove o convertire applicazioni in esecuzione in Azure PaaS, che possono trarre vantaggio cloud prestazioni, l'affidabilità e la scala e fornire supporto migliorato per gli utenti mobili.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="fb2c2-106">Architettura di uno scenario ibrido PaaS Azure</span><span class="sxs-lookup"><span data-stu-id="fb2c2-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="fb2c2-107">Nella figura 1 illustra l'architettura di scenari basati su PaaS ibridi Microsoft in Azure.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="fb2c2-108">**Nella figura 1: Scenari di ibrida basata su PaaS Microsoft in Azure**</span><span class="sxs-lookup"><span data-stu-id="fb2c2-108">**Figure 1: Microsoft PaaS-based hybrid scenarios in Azure**</span></span>

![Scenari ibridi Microsoft basati su PaaS in Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
<span data-ttu-id="fb2c2-110">Per ogni livello dell'architettura:</span><span class="sxs-lookup"><span data-stu-id="fb2c2-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="fb2c2-111">App e scenari</span><span class="sxs-lookup"><span data-stu-id="fb2c2-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="fb2c2-112">Un ambiente ibrido applicazione PaaS viene eseguito in Azure e utilizza risorse compute o l'archiviazione in locale.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="fb2c2-113">Identità</span><span class="sxs-lookup"><span data-stu-id="fb2c2-113">Identity</span></span>
    
    <span data-ttu-id="fb2c2-114">È costituita dalla sincronizzazione delle directory o la federazione con un provider di identità di terze parti.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="fb2c2-115">Rete</span><span class="sxs-lookup"><span data-stu-id="fb2c2-115">Network</span></span>
    
    <span data-ttu-id="fb2c2-p101">È costituita dal canale Internet esistente o una connessione ExpressRoute con peering pubblica per Azure PaaS. È necessario includere un modo per l'applicazione PaaS Azure accedere alla risorsa compute o l'archiviazione in locale.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-p101">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS. You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="fb2c2-118">Locale</span><span class="sxs-lookup"><span data-stu-id="fb2c2-118">On-premises</span></span>
    
    <span data-ttu-id="fb2c2-119">È costituita da identità e la protezione dell'infrastruttura e line-of business (LOB) applicazioni o server di database, un'applicazione di Azure PaaS può accedere in modo sicuro esistenti.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="fb2c2-120">Applicazione di ibrida PaaS Azure</span><span class="sxs-lookup"><span data-stu-id="fb2c2-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="fb2c2-121">Nella figura 2 viene illustrata la configurazione di un'applicazione ibrida in esecuzione in Azure.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
<span data-ttu-id="fb2c2-122">**Nella figura 2: Applicazione ibrida basata su PaaS Azure**</span><span class="sxs-lookup"><span data-stu-id="fb2c2-122">**Figure 2: Azure PaaS-based hybrid application**</span></span>

![Applicazione ibrida basta su PaaS di Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
<span data-ttu-id="fb2c2-p102">Nella figura 2, una rete locale ospita archiviazione o applicazioni server e una DMZ contenente un server proxy. Si connette ai servizi di Azure PaaS tramite Internet o con una connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-p102">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server. It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="fb2c2-126">Un'organizzazione, è possibile effettuare le relative risorse compute o l'archiviazione disponibili per l'applicazione ibrida PaaS Azure per:</span><span class="sxs-lookup"><span data-stu-id="fb2c2-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="fb2c2-127">Hosting delle risorse nei server DMZ.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="fb2c2-128">Hosting di un server proxy inverso nella DMZ, che consente le richieste di utenti autenticate, in ingresso, basato su HTTPS per la risorsa che si trova in locale.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="fb2c2-129">L'app Azure è possibile utilizzare le credenziali da:</span><span class="sxs-lookup"><span data-stu-id="fb2c2-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="fb2c2-130">Azure Active Directory, che possono essere sincronizzati con il provider di identità in locale, ad esempio Windows Server Active Directory.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Windows Server AD.</span></span>
    
- <span data-ttu-id="fb2c2-131">Un provider di identità di terze parti.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="fb2c2-132">Applicazione di esempio Azure PaaS ibrida</span><span class="sxs-lookup"><span data-stu-id="fb2c2-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="fb2c2-133">Nella figura 3 viene mostrata un'applicazione di ibrida di esempio in esecuzione in Azure.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
<span data-ttu-id="fb2c2-134">**Figura 3: Un esempio di un'applicazione basata su Azure PaaS ibrida**</span><span class="sxs-lookup"><span data-stu-id="fb2c2-134">**Figure 3: An example Azure PaaS-based hybrid application**</span></span>

![Un esempio di applicazione ibrida di Azure basata su PaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
<span data-ttu-id="fb2c2-p103">Nella figura 3, un host di rete locale un LOB App Azure PaaS ospita un'applicazione personalizzata per dispositivi mobili. Un dispositivo smartphone su Internet accede l'app personalizzata per dispositivi mobili in Azure, che invia le richieste di dati per l'applicazione LOB locale.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-p103">In Figure 3, an on-premises network hosts an LOB app. Azure PaaS hosts a custom mobile app. A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="fb2c2-p104">In questo esempio Azure PaaS ibrida applicazione sia un'app per dispositivi mobili personalizzata che fornisce informazioni aggiornate sui contatti sui dipendenti. Lo scenario ibrido end-to-end è costituito da:</span><span class="sxs-lookup"><span data-stu-id="fb2c2-p104">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees. The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="fb2c2-141">Una smartphone app che richiede la convalida, le credenziali locali per l'esecuzione.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="fb2c2-142">Un'applicazione personalizzata per dispositivi mobili in esecuzione in Azure PaaS, che richiede informazioni sui dipendenti specifici in base alle query da app smartphone dell'utente.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="fb2c2-143">Un server proxy inverso nella DMZ che convalida l'app per dispositivi mobili personalizzato e inoltra la richiesta.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="fb2c2-144">Una farm di server applicazioni LOB che gestisce la richiesta di contatto, soggette alle autorizzazioni dell'account dell'utente.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="fb2c2-145">Dal momento che il provider di identità locale è stato sincronizzato con Azure Active Directory, l'app per dispositivi mobili personalizzato e le applicazioni LOB possano convalidare il richiedente nome dell'account utente.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="stretch-database-with-sql-server-2016"></a><span data-ttu-id="fb2c2-146">Estensione database con SQL Server 2016</span><span class="sxs-lookup"><span data-stu-id="fb2c2-146">Stretch Database with SQL Server 2016</span></span>

<span data-ttu-id="fb2c2-147">Estensione database è una funzionalità di SQL Server 2016 che consente di spostare in modo sicuro e in modo trasparente freddi dati, ad esempio dati business chiuso in una tabella di grandi dimensioni che contiene informazioni sugli ordini, a un database SQL adatta in Azure.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-147">Stretch database is a feature of SQL Server 2016 that allows you to transparently and securely move cold data, such as closed business data in a large table that contains customer order information, to a SQL Stretch database in Azure.</span></span>
  
<span data-ttu-id="fb2c2-p105">Quando estesa, il contenuto di un'istanza di SQL Server, un database o anche una singola tabella è la combinazione di dati locali nel server SQL Server 2016 e dati remoti in Azure. Dati diventa idonei per Ridimensiona vengono automaticamente spostati Azure da SQL Server 2016.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-p105">When stretched, the contents of a SQL Server instance, a database, or even a single table is the combination of local data in SQL Server 2016 server and remote data in Azure. Data that becomes eligible for stretch is automatically moved to Azure by SQL Server 2016.</span></span>
  
<span data-ttu-id="fb2c2-150">Database Ridimensiona con SQL Server 2016 illustrato nella figura 4.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-150">Figure 4 shows Stretch Database with SQL Server 2016.</span></span>
  
<span data-ttu-id="fb2c2-151">**Figura 4: Database esteso con SQL Server 2016**</span><span class="sxs-lookup"><span data-stu-id="fb2c2-151">**Figure 4: Stretch Database with SQL Server 2016**</span></span>

![Estensione database con SQL Server 2016](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-SQL.png)
  
<span data-ttu-id="fb2c2-p106">Nella figura 4, una rete locale ospita un server che esegue SQL Server 2016 con un database locale di piccole dimensioni. Azure PaaS ospita un'istanza di Database Ridimensiona Azure SQL Server con la parte estesa del database. Query T-SQL da un utente locale inviati a SQL server in locale in modo sicuro vengono inoltrate al Database Ridimensiona SQL Azure, che restituisce i risultati all'utente richiedente.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-p106">In Figure 4, an on-premises network hosts a server running SQL Server 2016 with a small local database. Azure PaaS hosts an instance of Azure SQL Server Stretch Database with the stretched portion of the database. T-SQL queries from an on-premises user sent to the on-premises SQL server are securely forwarded to the Azure SQL Stretch Database, which returns the results to the requesting user.</span></span>
  
 <span data-ttu-id="fb2c2-p107">Le query degli utenti che includono i dati cronologici vengono inoltrate in modo trasparente all'estensione database Azure SQL. Le query non devono essere riscritte, anche se la tabella viene estesa.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-p107">User queries that include the historical data are transparently forwarded to Azure SQL Stretch database. The queries do not need to be re-written, even though the table is stretched.</span></span>
  
<span data-ttu-id="fb2c2-p108">Il database esteso fornisce un'opzione conveniente per l'archiviazione a lungo termine e l'accesso trasparente ai dati cronologici. Consente inoltre di risolvere problemi relativi a prestazioni e disponibilità che si verificano quando le tabelle diventano molto grandi.</span><span class="sxs-lookup"><span data-stu-id="fb2c2-p108">Stretch database provides a cost-effective option for long-term storage and transparent access to historical data. It also solves performance and availability problems that arise when tables become very large.</span></span>
  
<span data-ttu-id="fb2c2-160">Per ulteriori informazioni, vedere [Database adatta](https://msdn.microsoft.com/library/dn935011.aspx).</span><span class="sxs-lookup"><span data-stu-id="fb2c2-160">For more information, see [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fb2c2-161">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fb2c2-161">See Also</span></span>

[<span data-ttu-id="fb2c2-162">Cloud ibrido Microsoft per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="fb2c2-162">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="fb2c2-163">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="fb2c2-163">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="fb2c2-164">Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT</span><span class="sxs-lookup"><span data-stu-id="fb2c2-164">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



