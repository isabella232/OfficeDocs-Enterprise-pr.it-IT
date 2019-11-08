---
title: Diagramma accessibile-progettare siti Internet di esempio in Microsoft Azure per SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: 'Questo articolo è una versione di testo accessibile del diagramma denominato esempio di progettazione: siti Internet in Microsoft Azure per SharePoint 2013.'
ms.openlocfilehash: 52ae615cbdc6a355155e54e36bc6a3d733d84869
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "38027630"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="108ac-103">Diagramma accessibile-esempio di progettazione: siti Internet in Microsoft Azure per SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="108ac-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="108ac-104">**Riepilogo:** Questo articolo è una versione di testo accessibile del diagramma denominato esempio di progettazione: siti Internet in Microsoft Azure per SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="108ac-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="108ac-105">Utilizzare questo esempio di progettazione come punto di partenza per un sito con connessione Internet in Azure con SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="108ac-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="108ac-106">In questo poster viene illustrato un esempio di come progettare i seguenti aspetti di SharePoint 2013:</span><span class="sxs-lookup"><span data-stu-id="108ac-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="108ac-107">Utenti</span><span class="sxs-lookup"><span data-stu-id="108ac-107">Users</span></span>
    
- <span data-ttu-id="108ac-108">Aree e autenticazione</span><span class="sxs-lookup"><span data-stu-id="108ac-108">Zones and authentication</span></span>
    
- <span data-ttu-id="108ac-109">Server farm</span><span class="sxs-lookup"><span data-stu-id="108ac-109">Server farm</span></span>
    
- <span data-ttu-id="108ac-110">Sito di amministrazione</span><span class="sxs-lookup"><span data-stu-id="108ac-110">Administration site</span></span>
    
- <span data-ttu-id="108ac-111">Servizi</span><span class="sxs-lookup"><span data-stu-id="108ac-111">Services</span></span>
    
- <span data-ttu-id="108ac-112">Pool di applicazioni e applicazioni Web</span><span class="sxs-lookup"><span data-stu-id="108ac-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="108ac-113">Raccolte siti</span><span class="sxs-lookup"><span data-stu-id="108ac-113">Site collections</span></span>
    
- <span data-ttu-id="108ac-114">Siti</span><span class="sxs-lookup"><span data-stu-id="108ac-114">Sites</span></span>
    
- <span data-ttu-id="108ac-115">Database del contenuto</span><span class="sxs-lookup"><span data-stu-id="108ac-115">Content databases</span></span>
    
- <span data-ttu-id="108ac-116">Aree e URL</span><span class="sxs-lookup"><span data-stu-id="108ac-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="108ac-117">Utenti, aree e autenticazione</span><span class="sxs-lookup"><span data-stu-id="108ac-117">Users, zones and authentication</span></span>

<span data-ttu-id="108ac-118">In questa struttura sono disponibili quattro tipi di account utente.</span><span class="sxs-lookup"><span data-stu-id="108ac-118">There are four types of user accounts in this design.</span></span> <span data-ttu-id="108ac-119">Ogni tipo di account è associato a un sito per l'accesso e a un'area in cui viene utilizzato un tipo di autenticazione specifico.</span><span class="sxs-lookup"><span data-stu-id="108ac-119">Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="108ac-120">Clienti anonimi: i clienti anonimi dispongono dell'accesso tramite https://www.contoso.comun sito, ad esempio.</span><span class="sxs-lookup"><span data-stu-id="108ac-120">Anonymous customers — Anonymous customers have access through a site such as https://www.contoso.com.</span></span> <span data-ttu-id="108ac-121">L'area utilizzata è "Internet zone/Anonymous", che utilizza l'autenticazione anonima.</span><span class="sxs-lookup"><span data-stu-id="108ac-121">The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="108ac-122">Clienti autenticati: i clienti autenticati dispongono dell'accesso tramite un sito https://secure.contoso.com, ad esempio.</span><span class="sxs-lookup"><span data-stu-id="108ac-122">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com.</span></span> <span data-ttu-id="108ac-123">L'area utilizzata è "area Extranet/SAML", che utilizza Azure Active Directory con l'autenticazione SAML.</span><span class="sxs-lookup"><span data-stu-id="108ac-123">The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="108ac-124">Autori e sviluppatori di siti: gli autori e gli sviluppatori di siti possono accedere https://authoring.contoso.com:8000 tramite https://www.contoso.com:8000siti quali o.</span><span class="sxs-lookup"><span data-stu-id="108ac-124">Site authors and developers — Site authors and developers have access through sites such as https://authoring.contoso.com:8000 or https://www.contoso.com:8000.</span></span> <span data-ttu-id="108ac-125">L'area utilizzata è la "zona predefinita/integrata di Windows", che utilizza servizi di dominio Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="108ac-125">The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="108ac-126">Account di ricerca per indicizzazione-l'account di https://authoring.contoso.com:8000 ricerca per indicizzazione ha accesso tramite siti quali o. https://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="108ac-126">Search Crawl Account — The search crawl account has access through sites such as https://authoring.contoso.com:8000 or https://www.contoso.com:8000.</span></span> <span data-ttu-id="108ac-127">L'area utilizzata è l'"area predefinita/integrata di Windows", che utilizza servizi di dominio Active Directory con l'autenticazione NTLM di Windows.</span><span class="sxs-lookup"><span data-stu-id="108ac-127">The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="108ac-128">Server farm</span><span class="sxs-lookup"><span data-stu-id="108ac-128">Server farm</span></span>

<span data-ttu-id="108ac-129">Gli utenti accedono alla server farm tramite Azure.</span><span class="sxs-lookup"><span data-stu-id="108ac-129">The users access the server farm through Azure.</span></span> <span data-ttu-id="108ac-130">La server farm contiene uno o più server Web.</span><span class="sxs-lookup"><span data-stu-id="108ac-130">The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="108ac-131">Sito di amministrazione</span><span class="sxs-lookup"><span data-stu-id="108ac-131">Administration site</span></span>

<span data-ttu-id="108ac-132">Il sito di amministrazione contiene diversi server applicazioni, che comunicano con un pool di applicazioni (pool di applicazioni 1 nell'esempio) che utilizza il sito Amministrazione centrale dell'applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="108ac-132">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site.</span></span> <span data-ttu-id="108ac-133">Il sito Amministrazione centrale consente di accedere alle raccolte siti all'interno dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="108ac-133">The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="108ac-134">Il sito di amministrazione contiene anche server di database SQL, che sono server di database con SQL Server installato e configurato per supportare il clustering SQL, il mirroring o AlwaysOn (AlwaysOn si applica solo a SQL Server 2012).</span><span class="sxs-lookup"><span data-stu-id="108ac-134">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="108ac-135">Servizi</span><span class="sxs-lookup"><span data-stu-id="108ac-135">Services</span></span>

<span data-ttu-id="108ac-136">Nell'esempio di progettazione viene visualizzato un sito Web di Internet Information Services (IIS), servizi Web di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="108ac-136">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services.</span></span> <span data-ttu-id="108ac-137">Servizi Web di SharePoint include un pool di applicazioni (pool di applicazioni 2) con tre servizi, profili utente, ricerca e metadati gestiti.</span><span class="sxs-lookup"><span data-stu-id="108ac-137">SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="108ac-138">Note sui servizi per i siti Internet:</span><span class="sxs-lookup"><span data-stu-id="108ac-138">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="108ac-139">Metadati gestiti-assicurarsi di selezionare **questa applicazione di servizio è il percorso di archiviazione predefinito per i set di termini specifici della colonna**.</span><span class="sxs-lookup"><span data-stu-id="108ac-139">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="108ac-140">Gestione app: non è consigliabile utilizzare le app in un sito Internet pubblico in Azure.</span><span class="sxs-lookup"><span data-stu-id="108ac-140">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="108ac-141">Pool di applicazioni e applicazioni Web</span><span class="sxs-lookup"><span data-stu-id="108ac-141">Application pools and web applications</span></span>

<span data-ttu-id="108ac-142">Il gruppo predefinito in Azure Visualizza il pool di applicazioni 3, che contiene un'applicazione Web denominata contoso sites.</span><span class="sxs-lookup"><span data-stu-id="108ac-142">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites.</span></span> <span data-ttu-id="108ac-143">Questa raccolta siti basata su percorso si trova in https://internal:8000.</span><span class="sxs-lookup"><span data-stu-id="108ac-143">This path-based site collection is located at https://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="108ac-144">Raccolte e siti del sito</span><span class="sxs-lookup"><span data-stu-id="108ac-144">Site collections and sites</span></span>

<span data-ttu-id="108ac-145">Le raccolte siti incluse nel pool di applicazioni includono:</span><span class="sxs-lookup"><span data-stu-id="108ac-145">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="108ac-146">Raccolta siti con nome host 1 per la ricerca per indicizzazione (percorso di esempiohttps://authoring.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="108ac-146">Host-named site collection 1 for crawling (example location https://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="108ac-147">Raccolta siti con nome host 2 per le query (percorsi https://www.contoso.comdi https://secure.contoso.comesempio,https://www.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="108ac-147">Host-named site collection 2 for queries (sample locations https://www.contoso.com, https://secure.contoso.com, https://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="108ac-148">Raccolta siti con nome host 3 per le query (percorsi https://assets.contoso.comdi https://secureassets.contoso.comesempio,https://assets.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="108ac-148">Host-named site collection 3 for queries (sample locations https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="108ac-149">Database del contenuto</span><span class="sxs-lookup"><span data-stu-id="108ac-149">Content databases</span></span>

<span data-ttu-id="108ac-150">Nell'esempio vengono illustrati due database del contenuto.</span><span class="sxs-lookup"><span data-stu-id="108ac-150">The example shows two content databases.</span></span> <span data-ttu-id="108ac-151">Uno è per la raccolta siti 1 utilizzata per la ricerca perhttps://authoring.contoso.com:8000)indicizzazione (.</span><span class="sxs-lookup"><span data-stu-id="108ac-151">One is for the site collection 1 used for crawling (https://authoring.contoso.com:8000).</span></span> <span data-ttu-id="108ac-152">L'altro è per le due raccolte siti 2 e 3 utilizzate per le queryhttps://www.contoso.com( https://secure.contoso.com, https://www.contoso.com:8000, o https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000).</span><span class="sxs-lookup"><span data-stu-id="108ac-152">The other is for the two site collections 2 and 3 used for queries (https://www.contoso.com, https://secure.contoso.com, https://www.contoso.com:8000, or https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="108ac-153">Aree e URL</span><span class="sxs-lookup"><span data-stu-id="108ac-153">Zones and URLs</span></span>

<span data-ttu-id="108ac-154">Nell'esempio vengono visualizzate tre aree con gli URL con bilanciamento del carico associati che vengono utilizzati da diversi account utente.</span><span class="sxs-lookup"><span data-stu-id="108ac-154">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="108ac-155">Il primo elenco di aree e URL è correlato alla raccolta siti 1 e contiene le informazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="108ac-155">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="108ac-156">Utenti-autori del sito</span><span class="sxs-lookup"><span data-stu-id="108ac-156">Users - Site authors</span></span>
    
- <span data-ttu-id="108ac-157">Area-impostazione predefinita</span><span class="sxs-lookup"><span data-stu-id="108ac-157">Zone - Default</span></span>
    
- <span data-ttu-id="108ac-158">URL con bilanciamento del caricohttps://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="108ac-158">Load-balanced URL - https://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="108ac-159">Il secondo elenco di aree e URL ha tre diversi tipi di utenti in tre aree diverse.</span><span class="sxs-lookup"><span data-stu-id="108ac-159">The second list of zones and URLs has three different types of users in three different zones.</span></span> <span data-ttu-id="108ac-160">È correlata alla raccolta siti 2 e contiene le informazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="108ac-160">It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="108ac-161">Prima area:</span><span class="sxs-lookup"><span data-stu-id="108ac-161">First zone:</span></span>
  
- <span data-ttu-id="108ac-162">Utenti-autori del sito</span><span class="sxs-lookup"><span data-stu-id="108ac-162">Users - Site authors</span></span>
    
- <span data-ttu-id="108ac-163">Area-impostazione predefinita</span><span class="sxs-lookup"><span data-stu-id="108ac-163">Zone - Default</span></span>
    
- <span data-ttu-id="108ac-164">URL con bilanciamento del caricohttps://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="108ac-164">Load-balanced URL - https://www.contoso.com:8000</span></span>
    
<span data-ttu-id="108ac-165">Seconda area:</span><span class="sxs-lookup"><span data-stu-id="108ac-165">Second zone:</span></span>
  
- <span data-ttu-id="108ac-166">Utenti-clienti anonimi</span><span class="sxs-lookup"><span data-stu-id="108ac-166">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="108ac-167">Area-Internet</span><span class="sxs-lookup"><span data-stu-id="108ac-167">Zone - Internet</span></span>
    
- <span data-ttu-id="108ac-168">URL con bilanciamento del caricohttps://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="108ac-168">Load-balanced URL - https://www.contoso.com</span></span>
    
<span data-ttu-id="108ac-169">Terza area:</span><span class="sxs-lookup"><span data-stu-id="108ac-169">Third zone:</span></span>
  
- <span data-ttu-id="108ac-170">Clienti autenticati dagli utenti</span><span class="sxs-lookup"><span data-stu-id="108ac-170">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="108ac-171">Area-Extranet</span><span class="sxs-lookup"><span data-stu-id="108ac-171">Zone - Extranet</span></span>
    
- <span data-ttu-id="108ac-172">URL con bilanciamento del caricohttps://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="108ac-172">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="108ac-173">Il terzo elenco di aree e URL ha tre diversi tipi di utenti in tre aree diverse.</span><span class="sxs-lookup"><span data-stu-id="108ac-173">The third list of zones and URLs has three different types of users in three different zones.</span></span> <span data-ttu-id="108ac-174">È correlata alla raccolta siti 3 e contiene le informazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="108ac-174">It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="108ac-175">Prima area:</span><span class="sxs-lookup"><span data-stu-id="108ac-175">First zone:</span></span>
  
- <span data-ttu-id="108ac-176">Utenti-autori del sito</span><span class="sxs-lookup"><span data-stu-id="108ac-176">Users - Site authors</span></span>
    
- <span data-ttu-id="108ac-177">Area-Internet</span><span class="sxs-lookup"><span data-stu-id="108ac-177">Zone - Internet</span></span>
    
- <span data-ttu-id="108ac-178">URL con bilanciamento del caricohttps://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="108ac-178">Load-balanced URL - https://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="108ac-179">Seconda area:</span><span class="sxs-lookup"><span data-stu-id="108ac-179">Second zone:</span></span>
  
- <span data-ttu-id="108ac-180">Utenti-clienti anonimi</span><span class="sxs-lookup"><span data-stu-id="108ac-180">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="108ac-181">Area-Internet</span><span class="sxs-lookup"><span data-stu-id="108ac-181">Zone - Internet</span></span>
    
- <span data-ttu-id="108ac-182">URL con bilanciamento del caricohttps://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="108ac-182">Load-balanced URL - https://assets.contoso.com</span></span>
    
<span data-ttu-id="108ac-183">Terza area:</span><span class="sxs-lookup"><span data-stu-id="108ac-183">Third zone:</span></span>
  
- <span data-ttu-id="108ac-184">Clienti autenticati dagli utenti</span><span class="sxs-lookup"><span data-stu-id="108ac-184">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="108ac-185">Area-Extranet</span><span class="sxs-lookup"><span data-stu-id="108ac-185">Zone - Extranet</span></span>
    
- <span data-ttu-id="108ac-186">URL con bilanciamento del caricohttps://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="108ac-186">Load-balanced URL - https://secureassets.contoso.com</span></span>
    

