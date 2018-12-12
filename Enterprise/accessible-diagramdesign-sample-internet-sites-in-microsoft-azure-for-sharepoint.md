---
title: Accessibile diagramma - esempio di progettazione siti Internet in Microsoft Azure per SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: 'In questo articolo è una versione testo accessibile del diagramma denominata esempio di progettazione: siti Internet in Microsoft Azure per SharePoint 2013.'
ms.openlocfilehash: 0d42a96f80d47b360084557fea47c4155d106d30
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
ms.locfileid: "17502759"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="f2b38-103">Diagramma accessibile - esempio di progettazione: siti Internet in Microsoft Azure per SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="f2b38-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="f2b38-104">**Riepilogo:** In questo articolo è una versione testo accessibile del diagramma denominata esempio di progettazione: siti Internet in Microsoft Azure per SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="f2b38-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="f2b38-105">Utilizzare questo esempio di progettazione come punto di partenza per un sito Internet in Azure con SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="f2b38-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="f2b38-106">Questo poster viene illustrato un esempio di come progettare gli aspetti seguenti di SharePoint 2013:</span><span class="sxs-lookup"><span data-stu-id="f2b38-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="f2b38-107">Utenti</span><span class="sxs-lookup"><span data-stu-id="f2b38-107">Users</span></span>
    
- <span data-ttu-id="f2b38-108">Aree e autenticazione</span><span class="sxs-lookup"><span data-stu-id="f2b38-108">Zones and authentication</span></span>
    
- <span data-ttu-id="f2b38-109">Server farm</span><span class="sxs-lookup"><span data-stu-id="f2b38-109">Server farm</span></span>
    
- <span data-ttu-id="f2b38-110">Sito di amministrazione</span><span class="sxs-lookup"><span data-stu-id="f2b38-110">Administration site</span></span>
    
- <span data-ttu-id="f2b38-111">Servizi</span><span class="sxs-lookup"><span data-stu-id="f2b38-111">Services</span></span>
    
- <span data-ttu-id="f2b38-112">Pool di applicazioni e le applicazioni web</span><span class="sxs-lookup"><span data-stu-id="f2b38-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="f2b38-113">Raccolte siti</span><span class="sxs-lookup"><span data-stu-id="f2b38-113">Site collections</span></span>
    
- <span data-ttu-id="f2b38-114">Siti</span><span class="sxs-lookup"><span data-stu-id="f2b38-114">Sites</span></span>
    
- <span data-ttu-id="f2b38-115">Database del contenuto</span><span class="sxs-lookup"><span data-stu-id="f2b38-115">Content databases</span></span>
    
- <span data-ttu-id="f2b38-116">Aree e URL</span><span class="sxs-lookup"><span data-stu-id="f2b38-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="f2b38-117">Utenti, aree e autenticazione</span><span class="sxs-lookup"><span data-stu-id="f2b38-117">Users, zones and authentication</span></span>

<span data-ttu-id="f2b38-p101">Sono disponibili quattro tipi di account utente in questa struttura. Ogni tipo di account è associata a un sito per l'accesso e con un'area a cui viene utilizzato un tipo di autenticazione specifico.</span><span class="sxs-lookup"><span data-stu-id="f2b38-p101">There are four types of user accounts in this design. Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="f2b38-120">I clienti anonimi, ovvero i clienti anonimi hanno accesso a un sito, ad esempio http://www.contoso.com. È l'area che utilizzano il "area Internet / anonimi", che utilizza l'autenticazione anonima.</span><span class="sxs-lookup"><span data-stu-id="f2b38-120">Anonymous customers — Anonymous customers have access through a site such as http://www.contoso.com. The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="f2b38-121">Autenticati clienti, ovvero con i clienti hanno accesso a un sito, ad esempio https://secure.contoso.com. È l'area che utilizzano il "area Extranet / SAML", che utilizza Azure Active Directory con autenticazione SAML.</span><span class="sxs-lookup"><span data-stu-id="f2b38-121">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com. The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="f2b38-p102">Gli autori e agli sviluppatori di sito, ovvero gli autori di siti e gli sviluppatori hanno accesso a siti, ad esempio http://authoring.contoso.com:8000 o http://www.contoso.com:8000. È l'area che utilizzano il "area predefinita / integrata di Windows", che utilizza servizi di dominio Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="f2b38-p102">Site authors and developers — Site authors and developers have access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000. The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="f2b38-p103">Account di ricerca per indicizzazione di ricerca, ovvero L'account di ricerca per indicizzazione ricerca dispone dell'accesso a siti, ad esempio http://authoring.contoso.com:8000 o http://www.contoso.com:8000. È l'area viene utilizzato il metodo di "area predefinita / integrata di Windows", che utilizza Active Directory con l'autenticazione NTLM di Windows.</span><span class="sxs-lookup"><span data-stu-id="f2b38-p103">Search Crawl Account — The search crawl account has access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000. The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="f2b38-126">Server farm</span><span class="sxs-lookup"><span data-stu-id="f2b38-126">Server farm</span></span>

<span data-ttu-id="f2b38-p104">Gli utenti di accedere alla server farm tramite Azure. La server farm include uno o più server Web.</span><span class="sxs-lookup"><span data-stu-id="f2b38-p104">The users access the server farm through Azure. The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="f2b38-129">Sito di amministrazione</span><span class="sxs-lookup"><span data-stu-id="f2b38-129">Administration site</span></span>

<span data-ttu-id="f2b38-p105">Il sito Amministrazione contiene più server applicazioni, che comunicano con un Pool di applicazioni (Application Pool 1 nell'esempio) che utilizza l'applicazione web del sito Amministrazione centrale. Il sito Amministrazione centrale consente di accedere alle raccolte siti all'interno dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="f2b38-p105">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site. The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="f2b38-132">Il sito Amministrazione contiene anche server Database di SQL Server di database con SQL Server installato e configurato per supportare SQL clustering, mirroring o AlwaysOn (AlwaysOn solo per SQL Server 2012).</span><span class="sxs-lookup"><span data-stu-id="f2b38-132">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="f2b38-133">Servizi</span><span class="sxs-lookup"><span data-stu-id="f2b38-133">Services</span></span>

<span data-ttu-id="f2b38-p106">Nell'esempio di progettazione viene illustrato un sito Web Internet Information Services (IIS), servizi Web di SharePoint. SharePoint Web Services contiene un pool di applicazioni (Application Pool 2) con tre servizi, i profili utente, ricerca e i metadati gestiti.</span><span class="sxs-lookup"><span data-stu-id="f2b38-p106">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services. SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="f2b38-136">Note sui servizi per i siti Internet:</span><span class="sxs-lookup"><span data-stu-id="f2b38-136">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="f2b38-137">Metadati gestiti, Assicurarsi di selezionare **l'applicazione di servizio è il percorso predefinito per il set di termini specifici di colonna**.</span><span class="sxs-lookup"><span data-stu-id="f2b38-137">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="f2b38-138">Gestione di applicazioni, Non è consigliabile utilizzando applicazioni in un sito Internet pubblico in Azure.</span><span class="sxs-lookup"><span data-stu-id="f2b38-138">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="f2b38-139">Pool di applicazioni e le applicazioni web</span><span class="sxs-lookup"><span data-stu-id="f2b38-139">Application pools and web applications</span></span>

<span data-ttu-id="f2b38-p107">Il gruppo predefinito in Azure Mostra 3 Pool di applicazioni, che include un'applicazione web denominata Contoso siti. Questa raccolta siti basata su percorso si trova in http://internal:8000.</span><span class="sxs-lookup"><span data-stu-id="f2b38-p107">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites. This path-based site collection is located at http://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="f2b38-142">Siti e raccolte siti</span><span class="sxs-lookup"><span data-stu-id="f2b38-142">Site collections and sites</span></span>

<span data-ttu-id="f2b38-143">Sono incluse le raccolte siti contenute nel pool di applicazioni:</span><span class="sxs-lookup"><span data-stu-id="f2b38-143">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="f2b38-144">Raccolta siti con nome host 1 per la ricerca per indicizzazione (esempio posizione http://authoring.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="f2b38-144">Host-named site collection 1 for crawling (example location http://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="f2b38-145">Raccolta siti con nome host 2 per le query (esempio percorsi http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="f2b38-145">Host-named site collection 2 for queries (sample locations http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="f2b38-146">Raccolta siti con nome host 3 per le query (esempio percorsi http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="f2b38-146">Host-named site collection 3 for queries (sample locations http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="f2b38-147">Database del contenuto</span><span class="sxs-lookup"><span data-stu-id="f2b38-147">Content databases</span></span>

<span data-ttu-id="f2b38-p108">L'esempio mostra due database del contenuto. Uno è per la raccolta siti 1 per la ricerca per indicizzazione (http://authoring.contoso.com:8000). È l'altro per le raccolte due siti 2 e 3 per le query (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000 o http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).</span><span class="sxs-lookup"><span data-stu-id="f2b38-p108">The example shows two content databases. One is for the site collection 1 used for crawling (http://authoring.contoso.com:8000). The other is for the two site collections 2 and 3 used for queries (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000, or http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="f2b38-151">Aree e URL</span><span class="sxs-lookup"><span data-stu-id="f2b38-151">Zones and URLs</span></span>

<span data-ttu-id="f2b38-152">L'esempio mostra tre aree con gli URL con bilanciamento del carico associati che vengono utilizzati per gli account utente diverso.</span><span class="sxs-lookup"><span data-stu-id="f2b38-152">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="f2b38-153">Primo elenco delle aree e URL è correlato alla raccolta siti 1 e vengono fornite le informazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f2b38-153">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="f2b38-154">Utenti - autori dei siti</span><span class="sxs-lookup"><span data-stu-id="f2b38-154">Users - Site authors</span></span>
    
- <span data-ttu-id="f2b38-155">Area - predefinito</span><span class="sxs-lookup"><span data-stu-id="f2b38-155">Zone - Default</span></span>
    
- <span data-ttu-id="f2b38-156">URL con bilanciamento del carico - http://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="f2b38-156">Load-balanced URL - http://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="f2b38-p109">Il secondo elenco delle aree e URL presenta tre diversi tipi di utenti in tre aree diverse. È correlata alla raccolta siti 2 e contiene le informazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f2b38-p109">The second list of zones and URLs has three different types of users in three different zones. It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="f2b38-159">Prima area:</span><span class="sxs-lookup"><span data-stu-id="f2b38-159">First zone:</span></span>
  
- <span data-ttu-id="f2b38-160">Utenti - autori dei siti</span><span class="sxs-lookup"><span data-stu-id="f2b38-160">Users - Site authors</span></span>
    
- <span data-ttu-id="f2b38-161">Area - predefinito</span><span class="sxs-lookup"><span data-stu-id="f2b38-161">Zone - Default</span></span>
    
- <span data-ttu-id="f2b38-162">URL con bilanciamento del carico - http://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="f2b38-162">Load-balanced URL - http://www.contoso.com:8000</span></span>
    
<span data-ttu-id="f2b38-163">Seconda area:</span><span class="sxs-lookup"><span data-stu-id="f2b38-163">Second zone:</span></span>
  
- <span data-ttu-id="f2b38-164">Utenti - clienti anonimi</span><span class="sxs-lookup"><span data-stu-id="f2b38-164">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="f2b38-165">Area - Internet</span><span class="sxs-lookup"><span data-stu-id="f2b38-165">Zone - Internet</span></span>
    
- <span data-ttu-id="f2b38-166">-URL con bilanciamento del carico http://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="f2b38-166">Load-balanced URL - http://www.contoso.com</span></span>
    
<span data-ttu-id="f2b38-167">Terzo area:</span><span class="sxs-lookup"><span data-stu-id="f2b38-167">Third zone:</span></span>
  
- <span data-ttu-id="f2b38-168">Utenti - clienti autenticati</span><span class="sxs-lookup"><span data-stu-id="f2b38-168">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="f2b38-169">Area - Extranet</span><span class="sxs-lookup"><span data-stu-id="f2b38-169">Zone - Extranet</span></span>
    
- <span data-ttu-id="f2b38-170">Bilanciamento del carico URL - https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="f2b38-170">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="f2b38-p110">Il terzo elenco delle aree e URL presenta tre diversi tipi di utenti in tre aree diverse. È correlata alla raccolta siti 3 e contiene le informazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f2b38-p110">The third list of zones and URLs has three different types of users in three different zones. It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="f2b38-173">Prima area:</span><span class="sxs-lookup"><span data-stu-id="f2b38-173">First zone:</span></span>
  
- <span data-ttu-id="f2b38-174">Utenti - autori dei siti</span><span class="sxs-lookup"><span data-stu-id="f2b38-174">Users - Site authors</span></span>
    
- <span data-ttu-id="f2b38-175">Area - Internet</span><span class="sxs-lookup"><span data-stu-id="f2b38-175">Zone - Internet</span></span>
    
- <span data-ttu-id="f2b38-176">URL con bilanciamento del carico - http://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="f2b38-176">Load-balanced URL - http://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="f2b38-177">Seconda area:</span><span class="sxs-lookup"><span data-stu-id="f2b38-177">Second zone:</span></span>
  
- <span data-ttu-id="f2b38-178">Utenti - clienti anonimi</span><span class="sxs-lookup"><span data-stu-id="f2b38-178">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="f2b38-179">Area - Internet</span><span class="sxs-lookup"><span data-stu-id="f2b38-179">Zone - Internet</span></span>
    
- <span data-ttu-id="f2b38-180">Bilanciamento del carico URL - http://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="f2b38-180">Load-balanced URL - http://assets.contoso.com</span></span>
    
<span data-ttu-id="f2b38-181">Terzo area:</span><span class="sxs-lookup"><span data-stu-id="f2b38-181">Third zone:</span></span>
  
- <span data-ttu-id="f2b38-182">Utenti - clienti autenticati</span><span class="sxs-lookup"><span data-stu-id="f2b38-182">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="f2b38-183">Area - Extranet</span><span class="sxs-lookup"><span data-stu-id="f2b38-183">Zone - Extranet</span></span>
    
- <span data-ttu-id="f2b38-184">Bilanciamento del carico URL - http://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="f2b38-184">Load-balanced URL - http://secureassets.contoso.com</span></span>
    

