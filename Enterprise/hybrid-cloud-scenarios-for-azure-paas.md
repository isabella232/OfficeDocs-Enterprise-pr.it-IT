---
title: Scenari cloud ibridi per Azure PaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: "Riepilogo: comprendere l'architettura ibrida e gli scenari per le offerte cloud di Microsoft come servizio (PaaS) in Azure."
ms.openlocfilehash: fcc335d0e53463dea4e7ac73c3885b39734db38e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067532"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="6701a-103">Scenari cloud ibridi per Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="6701a-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="6701a-104">**Riepilogo:** Comprendere l'architettura ibrida e gli scenari per le offerte cloud basate su PaaS (Platform as a Service) di Microsoft in Azure.</span><span class="sxs-lookup"><span data-stu-id="6701a-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="6701a-105">Combinare dati locali o risorse di elaborazione con applicazioni nuove o convertite in esecuzione in PaaS di Azure, che possono sfruttare le prestazioni, l'affidabilità e la scalabilità del cloud e fornire un supporto migliore per gli utenti di dispositivi mobili.</span><span class="sxs-lookup"><span data-stu-id="6701a-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="6701a-106">Architettura di scenari ibridi di PaaS di Azure</span><span class="sxs-lookup"><span data-stu-id="6701a-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="6701a-107">Nella figura 1 viene illustrata l'architettura di scenari ibridi basati su Microsoft PaaS in Azure.</span><span class="sxs-lookup"><span data-stu-id="6701a-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="6701a-108">**Figura 1: scenari ibridi basati su Microsoft PaaS in Azure**</span><span class="sxs-lookup"><span data-stu-id="6701a-108">**Figure 1: Microsoft PaaS-based hybrid scenarios in Azure**</span></span>

![Scenari ibridi basati su Microsoft PaaS in Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
<span data-ttu-id="6701a-110">Per ogni livello dell'architettura:</span><span class="sxs-lookup"><span data-stu-id="6701a-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="6701a-111">App e scenari</span><span class="sxs-lookup"><span data-stu-id="6701a-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="6701a-112">Un'applicazione PaaS ibrida viene eseguita in Azure e utilizza risorse di calcolo o di archiviazione locali.</span><span class="sxs-lookup"><span data-stu-id="6701a-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="6701a-113">Identità</span><span class="sxs-lookup"><span data-stu-id="6701a-113">Identity</span></span>
    
    <span data-ttu-id="6701a-114">È costituito dalla sincronizzazione della directory o dalla Federazione con un provider di identità di terze parti.</span><span class="sxs-lookup"><span data-stu-id="6701a-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="6701a-115">Rete</span><span class="sxs-lookup"><span data-stu-id="6701a-115">Network</span></span>
    
    <span data-ttu-id="6701a-116">È costituito dalla pipe Internet esistente o da una connessione ExpressRoute con peering pubblico a Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="6701a-116">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS.</span></span> <span data-ttu-id="6701a-117">È necessario includere un metodo per l'applicazione di Azure PaaS per accedere alla risorsa di archiviazione o computo locale.</span><span class="sxs-lookup"><span data-stu-id="6701a-117">You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="6701a-118">Locale</span><span class="sxs-lookup"><span data-stu-id="6701a-118">On-premises</span></span>
    
    <span data-ttu-id="6701a-119">È costituito da un'infrastruttura di identità e sicurezza e da applicazioni line-of-business (LOB) esistenti o da server di database, che un'applicazione di PaaS di Azure può accedere in modo sicuro.</span><span class="sxs-lookup"><span data-stu-id="6701a-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="6701a-120">Applicazione ibrida di PaaS di Azure</span><span class="sxs-lookup"><span data-stu-id="6701a-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="6701a-121">Nella figura 2 viene illustrata la configurazione di un'applicazione ibrida in esecuzione in Azure.</span><span class="sxs-lookup"><span data-stu-id="6701a-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
<span data-ttu-id="6701a-122">**Figura 2: applicazione ibrida basata su PaaS di Azure**</span><span class="sxs-lookup"><span data-stu-id="6701a-122">**Figure 2: Azure PaaS-based hybrid application**</span></span>

![Applicazione ibrida basata su PaaS di Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
<span data-ttu-id="6701a-124">Nella figura 2, una rete locale ospita l'archiviazione o le app nei server e una DMZ contenente un server proxy.</span><span class="sxs-lookup"><span data-stu-id="6701a-124">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server.</span></span> <span data-ttu-id="6701a-125">È collegato ai servizi di PaaS di Azure su Internet o con una connessione ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="6701a-125">It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="6701a-126">Un'organizzazione può rendere disponibili le proprie risorse di calcolo o di archiviazione per l'applicazione ibrida di Azure PaaS per:</span><span class="sxs-lookup"><span data-stu-id="6701a-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="6701a-127">Hosting della risorsa nei server della DMZ.</span><span class="sxs-lookup"><span data-stu-id="6701a-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="6701a-128">Hosting di un server proxy inverso nella DMZ, che consente le richieste autenticate, in ingresso e basate su HTTPS alla risorsa che si trova in locale.</span><span class="sxs-lookup"><span data-stu-id="6701a-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="6701a-129">L'app di Azure può utilizzare le credenziali da:</span><span class="sxs-lookup"><span data-stu-id="6701a-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="6701a-130">Azure AD, che può essere sincronizzato con il provider di identità locale, ad esempio servizi di dominio Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="6701a-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="6701a-131">Un provider di identità di terze parti.</span><span class="sxs-lookup"><span data-stu-id="6701a-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="6701a-132">Esempio di applicazione ibrida di Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="6701a-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="6701a-133">Nella figura 3 viene mostrato un esempio di applicazione ibrida in esecuzione in Azure.</span><span class="sxs-lookup"><span data-stu-id="6701a-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
<span data-ttu-id="6701a-134">**Figura 3: un'applicazione ibrida basata su Azure PaaS di esempio**</span><span class="sxs-lookup"><span data-stu-id="6701a-134">**Figure 3: An example Azure PaaS-based hybrid application**</span></span>

![Esempio di un doma ibrido basato su Azure PaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
<span data-ttu-id="6701a-136">Nella figura 3, una rete locale ospita un'app LOB.</span><span class="sxs-lookup"><span data-stu-id="6701a-136">In Figure 3, an on-premises network hosts an LOB app.</span></span> <span data-ttu-id="6701a-137">Azure PaaS ospita un'app per dispositivi mobili personalizzata.</span><span class="sxs-lookup"><span data-stu-id="6701a-137">Azure PaaS hosts a custom mobile app.</span></span> <span data-ttu-id="6701a-138">Uno smartphone su Internet accede all'app per dispositivi mobili personalizzata in Azure, che invia le richieste di dati all'app LOB locale.</span><span class="sxs-lookup"><span data-stu-id="6701a-138">A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="6701a-139">In questo esempio, l'applicazione ibrida di Azure PaaS è un'app per dispositivi mobili personalizzata che fornisce informazioni di contatto aggiornate sui dipendenti.</span><span class="sxs-lookup"><span data-stu-id="6701a-139">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees.</span></span> <span data-ttu-id="6701a-140">Lo scenario ibrido end-to-end è costituito da:</span><span class="sxs-lookup"><span data-stu-id="6701a-140">The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="6701a-141">App per smartphone che richiede l'esecuzione di credenziali convalidate e locali.</span><span class="sxs-lookup"><span data-stu-id="6701a-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="6701a-142">Un'app per dispositivi mobili personalizzata in esecuzione in Azure PaaS, che richiede informazioni su specifici dipendenti in base alle query provenienti dall'app smartphone di un utente.</span><span class="sxs-lookup"><span data-stu-id="6701a-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="6701a-143">Un server proxy inverso nella DMZ che convalida l'app per dispositivi mobili personalizzata e inoltra la richiesta.</span><span class="sxs-lookup"><span data-stu-id="6701a-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="6701a-144">Una farm di server applicazioni LOB che assiste la richiesta di contatto, in base alle autorizzazioni dell'account dell'utente.</span><span class="sxs-lookup"><span data-stu-id="6701a-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="6701a-145">Poiché il provider di identità locale è stato sincronizzato con Azure AD, sia l'app per dispositivi mobili personalizzata che l'app LOB possono convalidare il nome dell'account dell'utente che richiede la richiesta.</span><span class="sxs-lookup"><span data-stu-id="6701a-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6701a-146">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6701a-146">See Also</span></span>

[<span data-ttu-id="6701a-147">Cloud ibrido Microsoft per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="6701a-147">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="6701a-148">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="6701a-148">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

