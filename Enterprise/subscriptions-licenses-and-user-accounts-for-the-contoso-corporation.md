---
title: Sottoscrizioni, licenze e account utente per Contoso Corporation
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
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: 'Riepilogo: Comprendere la struttura delle sottoscrizioni cloud di Contoso, le licenze, gli account utente e tenant.'
ms.openlocfilehash: 6e62fbbc0f52019e5d233fc73992b000952344f5
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a><span data-ttu-id="d2f00-103">Sottoscrizioni, licenze e account utente per Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="d2f00-103">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>

 <span data-ttu-id="d2f00-104">**Riepilogo:** Comprensione della struttura delle sottoscrizioni cloud di Contoso, le licenze, gli account utente e tenant.</span><span class="sxs-lookup"><span data-stu-id="d2f00-104">**Summary:** Understand the structure of Contoso's cloud subscriptions, licenses, user accounts, and tenants.</span></span>
  
<span data-ttu-id="d2f00-105">Per garantire un utilizzo coerente di identità e fatturazione per tutte le offerte cloud, Microsoft fornisce una gerarchia di organizzazioni/sottoscrizioni/licenze/account utente:</span><span class="sxs-lookup"><span data-stu-id="d2f00-105">To provide a consistent use of identities and billing for all cloud offerings, Microsoft provides an organization/subscriptions/licenses/user accounts hierarchy:</span></span>
  
- <span data-ttu-id="d2f00-106">Organizzazione</span><span class="sxs-lookup"><span data-stu-id="d2f00-106">Organization</span></span>
    
    <span data-ttu-id="d2f00-107">L'entità aziendale che utilizza offerte cloud Microsoft, in genere identificate tramite un nome di dominio DNS pubblico, ad esempio contoso.com.</span><span class="sxs-lookup"><span data-stu-id="d2f00-107">The business entity that is using Microsoft cloud offerings, typically identified by a public DNS domain name, such as contoso.com.</span></span>
    
- <span data-ttu-id="d2f00-108">Sottoscrizioni</span><span class="sxs-lookup"><span data-stu-id="d2f00-108">Subscriptions</span></span>
    
    <span data-ttu-id="d2f00-p101">Per SaaS Microsoft cloud offerte (Office 365, Intune/EMS e Dynamics 365), una sottoscrizione è un prodotto specifico e un set acquistato delle licenze utente. Per Azure, una sottoscrizione consente di fatturazione dei servizi cloud consumato nell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="d2f00-p101">For Microsoft SaaS cloud offerings (Office 365, Intune/EMS, and Dynamics 365), a subscription is a specific product and a purchased set of user licenses. For Azure, a subscription allows for billing of consumed cloud services to the organization.</span></span>
    
- <span data-ttu-id="d2f00-111">Licenze</span><span class="sxs-lookup"><span data-stu-id="d2f00-111">Licenses</span></span>
    
    <span data-ttu-id="d2f00-p102">Per le offerte cloud Microsoft SaaS, di una licenza consente a un account utente specifico utilizzare i servizi cloud. Per Azure, le licenze software sono incorporate nel servizio prezzi, ma in alcuni casi che è necessario acquistare licenze software aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="d2f00-p102">For Microsoft SaaS cloud offerings, a license allows a specific user account to use cloud services. For Azure, software licenses are built into service pricing, but in some cases you will need to purchase additional software licenses.</span></span>
    
- <span data-ttu-id="d2f00-114">Account utente</span><span class="sxs-lookup"><span data-stu-id="d2f00-114">User accounts</span></span>
    
    <span data-ttu-id="d2f00-115">Gli account utente vengono archiviati in un tenant di Azure AD e possono essere sincronizzati da un provider di identità locale, ad esempio Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="d2f00-115">User accounts are stored in an Azure AD tenant and can be synchronized from an on-premises identity provider such as Windows Server AD.</span></span>
    
## <a name="contosos-structure"></a><span data-ttu-id="d2f00-116">Struttura di Contoso</span><span class="sxs-lookup"><span data-stu-id="d2f00-116">Contoso's structure</span></span>

<span data-ttu-id="d2f00-117">Contoso ha determinato la struttura seguente per l'organizzazione e per le sottoscrizioni, licenze, account e tenant della stessa:</span><span class="sxs-lookup"><span data-stu-id="d2f00-117">Contoso determined the following structure for the organization and its subscriptions, licenses, accounts, and tenants:</span></span>
  
<span data-ttu-id="d2f00-118">**Nella figura 1: Del Contoso organizzazione, sottoscrizioni, licenze, gli account utente e tenant**</span><span class="sxs-lookup"><span data-stu-id="d2f00-118">**Figure 1: Contoso's organization, subscriptions, licenses, user accounts and tenants**</span></span>

![Organizzazione di Contoso, sottoscrizioni, licenze, account utente e tenant](images/Contoso_Poster/Subscriptions.png)
  
<span data-ttu-id="d2f00-120">Nella figura 1 viene mostrato in che modo l'organizzazione Contoso include più sottoscrizioni ed è legata a un tenant di Azure AD, il quale comprende gli account utente sincronizzati dalla foresta Windows Server AD di contoso.com.</span><span class="sxs-lookup"><span data-stu-id="d2f00-120">Figure 1 shows how the Contoso organization includes multiple subscriptions and is tied to a common Azure AD tenant that contains the user accounts synchronized from the contoso.com Windows Server AD forest.</span></span>
  
- <span data-ttu-id="d2f00-121">**Organizzazione** Contoso Corporation è identificata dal relativo nome di dominio pubblico contoso.com.</span><span class="sxs-lookup"><span data-stu-id="d2f00-121">**Organization** The Contoso Corporation is identified by its public domain name contoso.com.</span></span>
    
  - <span data-ttu-id="d2f00-122">**Licenze e sottoscrizioni** Contoso Corporation utilizza le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="d2f00-122">**Subscriptions and licenses** The Contoso Corporation is using the following:</span></span>
    
  - <span data-ttu-id="d2f00-123">Il prodotto Office 365 Enterprise E3 con 5.000 licenze</span><span class="sxs-lookup"><span data-stu-id="d2f00-123">The Office 365 Enterprise E3 product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="d2f00-124">Il prodotto Office 365 Enterprise E5 con 200 licenze</span><span class="sxs-lookup"><span data-stu-id="d2f00-124">The Office 365 Enterprise E5 product with 200 licenses</span></span>
    
  - <span data-ttu-id="d2f00-125">Il prodotto EMS con 5.000 licenze</span><span class="sxs-lookup"><span data-stu-id="d2f00-125">The EMS product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="d2f00-126">Prodotto Dynamics 365 con 100 licenze</span><span class="sxs-lookup"><span data-stu-id="d2f00-126">The Dynamics 365 product with 100 licenses</span></span>
    
  - <span data-ttu-id="d2f00-127">Più sottoscrizioni Azure basate sulle aree geografiche</span><span class="sxs-lookup"><span data-stu-id="d2f00-127">Multiple Azure subscriptions based on regions</span></span>
    
  - <span data-ttu-id="d2f00-128">**Account utente** Un comune tenant di Azure Active Directory contiene l'elenco degli account utente e i gruppi utilizzati da tutte le sottoscrizioni di Contoso, ad eccezione di sviluppo e di testing sottoscrizioni di Azure.</span><span class="sxs-lookup"><span data-stu-id="d2f00-128">**User accounts** A common Azure AD tenant contains the list of user accounts and groups used by all of Contoso's subscriptions, with the exception of dev/test Azure subscriptions.</span></span>
    
<span data-ttu-id="d2f00-129">Per i tenant Contoso:</span><span class="sxs-lookup"><span data-stu-id="d2f00-129">For Contoso's tenants:</span></span>
  
- <span data-ttu-id="d2f00-p103">Per le offerte cloud SaaS, tenant è il percorso internazionale in cui si trova il server che offrono servizi basati su cloud. Contoso ha scelto la regione Europa per ospitare il tenant Office 365, EMS e Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="d2f00-p103">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. Contoso chose the European region to host its Office 365, EMS, and Dynamics 365 tenants.</span></span> 
    
- <span data-ttu-id="d2f00-p104">Azure PaaS servizi e applicazioni e carichi di lavoro IaaS IT possono avere tenancy in un Data Center Azure in tutto il mondo. Un tenant di Azure Active Directory è un'istanza specifica di Azure Active Directory contenente gli account e gruppi.</span><span class="sxs-lookup"><span data-stu-id="d2f00-p104">Azure PaaS services and apps and IaaS IT workloads can have tenancy in any Azure datacenter across the world. An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span></span>
    
- <span data-ttu-id="d2f00-134">Il comune tenant di Azure Active Directory contenente gli account di sincronizzazione per la foresta Contoso Windows Server Active Directory fornisce IDaaS nelle offerte cloud di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d2f00-134">The common Azure AD tenant that contains the synchronized accounts for the Contoso Windows Server AD forest provides IDaaS across Microsoft's cloud offerings.</span></span>
    
<span data-ttu-id="d2f00-135">Per ulteriori informazioni, vedere [sottoscrizioni, le licenze, gli account utilizzati e tenant per le offerte cloud di Microsoft](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span><span class="sxs-lookup"><span data-stu-id="d2f00-135">For more information, see [Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span></span>
  
## <a name="contosos-azure-subscriptions"></a><span data-ttu-id="d2f00-136">Sottoscrizioni Azure contoso</span><span class="sxs-lookup"><span data-stu-id="d2f00-136">Contoso's Azure subscriptions</span></span>

<span data-ttu-id="d2f00-137">Nella figura 2 viene illustrata la struttura gerarchica delle sottoscrizioni Azure Contoso:</span><span class="sxs-lookup"><span data-stu-id="d2f00-137">Figure 2 shows the hierarchical design of Contoso's Azure subscriptions:</span></span>
  
<span data-ttu-id="d2f00-138">**Figura 2: Struttura di Contoso per le sottoscrizioni di Azure**</span><span class="sxs-lookup"><span data-stu-id="d2f00-138">**Figure 2: Contoso's structure for Azure subscriptions**</span></span>

![Struttura di Contoso per sottoscrizioni di Azure](images/Contoso_Poster/Subscriptions_Nested.png)
  
- <span data-ttu-id="d2f00-140">Contoso è nella parte superiore, in base agli accordi aziendali con Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d2f00-140">Contoso is at the top, based on its Enterprise Agreement with Microsoft.</span></span>
    
- <span data-ttu-id="d2f00-141">Sono disponibili un set di account corrispondente per aree geografiche diverse di Contoso Corporation tutto il mondo, basato sui domini della foresta di Windows Server Active Directory Contoso.</span><span class="sxs-lookup"><span data-stu-id="d2f00-141">There are a set of accounts corresponding to the different regions of the Contoso Corporation around the world, based on the domains of Contoso's Windows Server AD forest.</span></span>
    
- <span data-ttu-id="d2f00-142">In ogni area, esistono uno o più sottoscrizioni in base alle esigenze di distribuzione di sviluppo, test e produzione dell'area.</span><span class="sxs-lookup"><span data-stu-id="d2f00-142">Within each region, there are one or more subscriptions based on the region's development, testing, and production deployment needs.</span></span>
    
<span data-ttu-id="d2f00-p105">Ogni sottoscrizione ad Azure può essere associata a un singolo tenant Azure AD contenente account utente e gruppi per l'autenticazione e l'autorizzazione dei servizi Azure. Le sottoscrizioni di produzione utilizzano il tenant di Contoso Azure AD comune.</span><span class="sxs-lookup"><span data-stu-id="d2f00-p105">Each Azure subscription can be associated with a single Azure AD tenant that contains user accounts and groups for authentication and authorization to Azure services. Production subscriptions use the common Contoso Azure AD tenant.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d2f00-145">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d2f00-145">See Also</span></span>

[<span data-ttu-id="d2f00-146">Contoso nel Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="d2f00-146">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="d2f00-147">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="d2f00-147">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="d2f00-148">Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT</span><span class="sxs-lookup"><span data-stu-id="d2f00-148">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




