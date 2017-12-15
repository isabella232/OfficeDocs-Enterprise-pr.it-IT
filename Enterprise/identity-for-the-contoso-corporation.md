---
title: "Identità per Contoso Corporation"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 78a407e4-2d8b-4561-b308-b22c95f60eeb
description: "Sintesi: informazioni su come Contoso trae vantaggio da una soluzione di gestione delle identità e degli accessi distribuita come servizio (IDaaS) e fornisce un'autenticazione ridondante e distribuita a livello geografico per i suoi utenti."
ms.openlocfilehash: a0de29ac7e73216e04fe02c680f2557e9f402883
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="identity-for-the-contoso-corporation"></a><span data-ttu-id="d15fe-103">Identità per Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="d15fe-103">Identity for the Contoso Corporation</span></span>

 <span data-ttu-id="d15fe-104">**Sintesi:** informazioni su come Contoso trae vantaggio da una soluzione di gestione delle identità e degli accessi distribuita come servizio (IDaaS) e fornisce un'autenticazione ridondante e distribuita a livello geografico per i suoi utenti.</span><span class="sxs-lookup"><span data-stu-id="d15fe-104">**Summary:** Understand how Contoso takes advantage of IDaaS and provides geographically distributed and redundant authentication for its users.</span></span>
  
<span data-ttu-id="d15fe-p101">Microsoft fornisce una soluzione di gestione delle identità e degli accessi distribuita come servizio (IDaaS) nelle sue offerte cloud. Per adottare un'infrastruttura inclusiva di cloud, la soluzione IDaaS di Contoso deve sfruttare i provider di identità locali e includere l'autenticazione federata con i provider di identità di terze parti esistenti e attendibili.</span><span class="sxs-lookup"><span data-stu-id="d15fe-p101">Microsoft provides an Identity as a Service (IDaaS) across its cloud offerings. To adopt a cloud-inclusive infrastructure, Contoso's IDaaS solution must leverage their on-premises identity provider and include federated authentication with their existing trusted, third-party identity providers.</span></span>
  
## <a name="contosos-windows-server-ad-forest"></a><span data-ttu-id="d15fe-107">Foresta di Windows Server AD di Contoso</span><span class="sxs-lookup"><span data-stu-id="d15fe-107">Contoso's Windows Server AD forest</span></span>

<span data-ttu-id="d15fe-p102">Contoso usa una foresta di Windows Server Active Directory (AD) singola per contoso.com con sette domini, uno per ogni area geografica del mondo. La sede principale, le sedi centrali regionali e le filiali contengono controller di dominio per l'autorizzazione e l'autenticazione locali.</span><span class="sxs-lookup"><span data-stu-id="d15fe-p102">Contoso uses a single Windows Server Active Directory (AD) forest for contoso.com with seven domains, one for each region of the world. The headquarters, regional hub offices, and satellite offices contain domain controllers for local authentication and authorization.</span></span>
  
<span data-ttu-id="d15fe-110">**Figura 1: foresta di Contoso e domini a livello mondiale**</span><span class="sxs-lookup"><span data-stu-id="d15fe-110">**Figure 1: Contoso's forest and domains worldwide**</span></span>

![Domini e foresta di AD di Windows Server di Contoso nel mondo](images/Contoso_Poster/Contoso_WW_ID.png)
  
<span data-ttu-id="d15fe-112">Nella figura 1 viene mostrata la foresta di Contoso con domini regionali per le varie parti del mondo in cui sono presenti sedi centrali regionali.</span><span class="sxs-lookup"><span data-stu-id="d15fe-112">Figure 1 shows the Contoso forest with regional domains for the different parts of the world that contain regional hubs.</span></span>
  
<span data-ttu-id="d15fe-113">Contoso desidera utilizzare gli account e i gruppi della foresta contoso.com per l'autenticazione e l'autorizzazione per le app basate su cloud e per i carichi di lavoro.</span><span class="sxs-lookup"><span data-stu-id="d15fe-113">Contoso wants to use the accounts and groups in the contoso.com forest for authentication and authorization for its cloud-based apps and workloads.</span></span>
  
## <a name="contosos-federated-authentication-infrastructure"></a><span data-ttu-id="d15fe-114">Infrastruttura di autenticazione federata di Contoso</span><span class="sxs-lookup"><span data-stu-id="d15fe-114">Contoso's federated authentication infrastructure</span></span>

<span data-ttu-id="d15fe-115">Contoso consente:</span><span class="sxs-lookup"><span data-stu-id="d15fe-115">Contoso allows:</span></span>
  
- <span data-ttu-id="d15fe-116">Ai clienti di usare il proprio account Microsoft, Facebook o Google Mail per accedere al proprio sito Web pubblico.</span><span class="sxs-lookup"><span data-stu-id="d15fe-116">Customers to use their Microsoft, Facebook, or Google Mail accounts to sign in to their public web site.</span></span>
    
- <span data-ttu-id="d15fe-117">Ai fornitori e ai partner di usare il proprio account LinkedIn, Salesforce o Google Mail per accedere all'extranet dei partner.</span><span class="sxs-lookup"><span data-stu-id="d15fe-117">Vendors and partners to use their LinkedIn, Salesforce, or Google Mail accounts to sign in to the partner extranet.</span></span>
    
<span data-ttu-id="d15fe-118">**Figura 2: Supporto di Contoso per l'autenticazione federata di clienti e partner**</span><span class="sxs-lookup"><span data-stu-id="d15fe-118">**Figure 2: Contoso's support for federated authentication for customers and partners**</span></span>

![Infrastruttura esistente di Contoso per supportare l'autenticazione federata di clienti e partner](images/Contoso_Poster/Federated_ID.png)
  
<span data-ttu-id="d15fe-p103">Nella figura 2 viene mostrata la rete perimetrale di Contoso contenente un sito Web pubblico, una rete extranet partner e un set di server AD FS. La rete perimetrale è connessa a Internet che contiene clienti, partner e servizi Internet.</span><span class="sxs-lookup"><span data-stu-id="d15fe-p103">Figure 2 shows the Contoso DMZ containing a public web site, a partner extranet, and a set of AD FS servers. The DMZ is connected to the Internet that contains customers and partners and Internet services.</span></span>
  
<span data-ttu-id="d15fe-122">I server di Active Directory Federation Services (AD FS) nella DMZ autenticano le credenziali dei clienti per l'accesso al sito Web pubblico e le credenziali dei partner per l'accesso all'extranet dei partner.</span><span class="sxs-lookup"><span data-stu-id="d15fe-122">Active Directory Federation Services (AD FS) servers in the DMZ authenticate customer credentials for access to the public web site and partner credentials for access to the partner extranet.</span></span>
  
<span data-ttu-id="d15fe-p104">Quando Contoso effettua la transizione dal proprio sito Web pubblico in Azure Web App e dall'extranet dei partner a Dynamics 365, desidera continuare a utilizzare i provider di identità di terze parti per clienti e partner. Questo sarà possibile configurando la federazione tra i tenant di Contoso Azure AD e i provider di identità di terze parti.</span><span class="sxs-lookup"><span data-stu-id="d15fe-p104">When Contoso transitions its public web site to an Azure Web App and partner extranet to Dynamics 365, they want to continue to use these third-party identity providers for their customers and partners. This will be accomplished by configuring federation between Contoso Azure AD tenants and these third-party identity providers.</span></span>
  
## <a name="directory-synchronization-for-contosos-windows-server-ad-forest"></a><span data-ttu-id="d15fe-125">Sincronizzazione di directory per la foresta Windows Server AD di Contoso</span><span class="sxs-lookup"><span data-stu-id="d15fe-125">Directory synchronization for Contoso's Windows Server AD forest</span></span>

<span data-ttu-id="d15fe-p105">Contoso ha distribuito lo strumento Azure AD Connect su un cluster di server nel suo centro dati di Parigi. Azure AD Connect sincronizza le modifiche alla foresta di Windows Server AD contoso.com con il tenant di Azure AD condiviso dalle sottoscrizioni a Office 365, EMS, Dynamics 365 e Azure di Contoso. Per ulteriori informazioni su sottoscrizioni, licenze, account utente e tenant, vedere [Sottoscrizioni, licenze e account utente per Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md).</span><span class="sxs-lookup"><span data-stu-id="d15fe-p105">Contoso has deployed the Azure AD Connect tool on a cluster of servers in its Paris datacenter. Azure AD Connect synchronizes changes to the contoso.com Windows Server AD forest with the Azure AD tenant shared by Contoso's Office 365, EMS, Dynamics 365, and Azure subscriptions. For more information about subscriptions, licenses, user accounts, and tenants, see [Subscriptions, licenses, and user accounts for the Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md).</span></span>
  
<span data-ttu-id="d15fe-129">**Figura 3: Infrastruttura di sincronizzazione della directory di Contoso**</span><span class="sxs-lookup"><span data-stu-id="d15fe-129">**Figure 3: Contoso's directory synchronization infrastructure**</span></span>

![Infrastruttura di sincronizzazione della directory di Contoso](images/Contoso_Poster/DirSync.png)
  
<span data-ttu-id="d15fe-131">Nella figura 3 viene mostrato un cluster di server che eseguono Azure AD Connect per la sincronizzazione della foresta di Windows Server AD di Contoso con il tenant di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="d15fe-131">Figure 3 shows a cluster of servers running Azure AD Connect synchronizing the Contoso Windows Server AD forest with the Azure AD tenant.</span></span>
  
<span data-ttu-id="d15fe-p106">Contoso ha configurato l'autenticazione federata, che permette ai dipendenti di Contoso di effettuare l'accesso Single Sign-On. Quando un utente che ha già effettuato l'accesso alla foresta Windows Server AD di contoso.com accede a una risorsa cloud SaaS o PaaS di Microsoft, non verrà richiesta la password.</span><span class="sxs-lookup"><span data-stu-id="d15fe-p106">Contoso has configured federated authentication, which provides single sign-on for Contoso's workers. When a user that has already signed in to the contoso.com Windows Server AD forest accesses a Microsoft SaaS or PaaS cloud resource, they will not be prompted for a password.</span></span>
  
## <a name="geographical-distribution-of-contoso-authentication-traffic"></a><span data-ttu-id="d15fe-134">Distribuzione geografica del traffico di autenticazione di Contoso</span><span class="sxs-lookup"><span data-stu-id="d15fe-134">Geographical distribution of Contoso authentication traffic</span></span>

<span data-ttu-id="d15fe-p107">Per supportare al meglio le proprie risorse mobili e remote, Contoso ha distribuito insiemi di server di autenticazione nelle proprie filiali. Questa infrastruttura distribuisce il carico e offre ridondanza, nonché prestazioni migliori durante l'autenticazione delle credenziali utente per l'accesso alle offerte cloud di Microsoft che utilizzano il tenant di Azure AD comune.</span><span class="sxs-lookup"><span data-stu-id="d15fe-p107">To better support its mobile and remote workforce, Contoso has deployed sets of authentication servers in its regional offices. This infrastructure distributes the load and provides redundancy and higher performance when authenticating user credentials for access to Microsoft cloud offerings that use the common Azure AD tenant.</span></span>
  
<span data-ttu-id="d15fe-137">Per distribuire il carico delle richieste di autenticazione, Contoso ha configurato Azure Traffic Manager con un profilo che utilizza il metodo di routing delle prestazioni, che consente di autenticare i client al set di server di autenticazione nell'area geografica più vicina.</span><span class="sxs-lookup"><span data-stu-id="d15fe-137">To distribute the load of authentication requests, Contoso has configured Azure Traffic Manager with a profile that uses the performance routing method, which refers authenticating clients to the regionally closest set of authentication servers.</span></span> 
  
<span data-ttu-id="d15fe-138">**Figura 4: Distribuzione geografica del traffico di autenticazione per le sedi regionali**</span><span class="sxs-lookup"><span data-stu-id="d15fe-138">**Figure 4: Geographical distribution of authentication traffic for regional offices**</span></span>

![Distribuzione geografica del traffico di autenticazione di Contoso per le sedi regionali](images/Contoso_Poster/Auth_GeoDist.png)
  
<span data-ttu-id="d15fe-p108">Nella figura 4 vengono mostrati i livelli dei computer client, Gestione traffico di Azure e i server di autenticazione nelle filiali regionali. Ogni filiale regionale usa proxy Web e server AD FS per autenticare le credenziali utente con i controller di dominio di Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="d15fe-p108">Figure 4 shows the layers of client computers, Azure Traffic Manager, and authentication servers in regional offices. Each regional office uses web proxies and AD FS servers to authenticate user credentials with Windows Server AD domain controllers.</span></span>
  
<span data-ttu-id="d15fe-142">Esempio di processo di autenticazione:</span><span class="sxs-lookup"><span data-stu-id="d15fe-142">Authentication process example:</span></span>
  
1. <span data-ttu-id="d15fe-143">Il computer client avvia la comunicazione con una pagina Web nella tenancy di Office 365 in Europa (ad esempio sharepoint.contoso.com).</span><span class="sxs-lookup"><span data-stu-id="d15fe-143">The client computer initiates communication with a web page in the Office 365 tenancy in Europe (such as sharepoint.contoso.com).</span></span>
    
2. <span data-ttu-id="d15fe-p109">Office 365 inoltra una richiesta di invio per la prova di autenticazione. La richiesta contiene l'URL da contattare per l'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="d15fe-p109">Office 365 sends back a request to send proof of authentication. The request contains the URL to contact for authentication.</span></span>
    
3. <span data-ttu-id="d15fe-146">Il computer client tenta di risolvere il nome DNS nell'URL a un indirizzo IP.</span><span class="sxs-lookup"><span data-stu-id="d15fe-146">The client computer attempts to resolve the DNS name in the URL to an IP address.</span></span>
    
4. <span data-ttu-id="d15fe-147">Azure Traffic Manager riceve la query DNS e risponde al computer client con l'indirizzo IP di un server proxy di applicazione Web nella filiale più vicina al computer client.</span><span class="sxs-lookup"><span data-stu-id="d15fe-147">Azure Traffic Manager receives the DNS query and responds to the client computer with the IP address of a web application proxy server in the regional office that is closest to the client computer.</span></span>
    
5.  <span data-ttu-id="d15fe-148">Il computer client invia una richiesta di autenticazione a un server proxy di applicazione Web, che inoltra la richiesta a un server AD FS.</span><span class="sxs-lookup"><span data-stu-id="d15fe-148">The client computer sends an authentication request to a web application proxy server, which forwards the request to an AD FS server.</span></span>
    
6. <span data-ttu-id="d15fe-149">Il server AD FS richiede le credenziali utente dal computer client.</span><span class="sxs-lookup"><span data-stu-id="d15fe-149">The AD FS server requests the user credentials from the client computer.</span></span>
    
7. <span data-ttu-id="d15fe-150">Il computer client invia le credenziali utente senza chiedere conferma all'utente.</span><span class="sxs-lookup"><span data-stu-id="d15fe-150">The client computer sends the user credentials without prompting the user.</span></span>
    
8. <span data-ttu-id="d15fe-151">Il server AD FS convalida le credenziali con un controller di dominio Windows Server AD nella filiale e restituisce un token di sicurezza al computer client.</span><span class="sxs-lookup"><span data-stu-id="d15fe-151">The AD FS server validates the credentials with a Windows Server AD domain controller in the regional office and returns a security token to the client computer.</span></span>
    
9. <span data-ttu-id="d15fe-152">Il computer client invia il token di sicurezza a Office 365.</span><span class="sxs-lookup"><span data-stu-id="d15fe-152">The client computer sends the security token to Office 365.</span></span>
    
10. <span data-ttu-id="d15fe-153">Dopo aver completato la convalida, Office 365 memorizza nella cache il token di sicurezza e invia la pagina Web richiesta nel passaggio 1 al computer client.</span><span class="sxs-lookup"><span data-stu-id="d15fe-153">After successful validation, Office 365 caches the security token and sends the web page requested in step 1 to the client computer.</span></span>
    
## <a name="redundancy-for-the-headquarters-authentication-infrastructure-in-azure-iaas"></a><span data-ttu-id="d15fe-154">Ridondanza per l'infrastruttura di autenticazione della sede centrale in IaaS di Azure</span><span class="sxs-lookup"><span data-stu-id="d15fe-154">Redundancy for the headquarters authentication infrastructure in Azure IaaS</span></span>

<span data-ttu-id="d15fe-155">Per garantire la ridondanza a dipendenti remoti e mobili della sede di Parigi con 15.000 dipendenti, Contoso ha distribuito un secondo set di proxy di applicazione e server AD FS in IaaS di Azure.</span><span class="sxs-lookup"><span data-stu-id="d15fe-155">To provide redundancy for the remote and mobile workers of the Paris headquarters that contains 15,000 workers, Contoso has deployed a second set of application proxies and AD FS servers in Azure IaaS.</span></span>
  
<span data-ttu-id="d15fe-156">**Figura 5: Infrastruttura di autenticazione ridondante in IaaS di Azure**</span><span class="sxs-lookup"><span data-stu-id="d15fe-156">**Figure 5: Redundant authentication infrastructure in Azure IaaS**</span></span>

![Infrastruttura di autenticazione ridondante in IaaS di Azure per la sede centrale di Parigi](images/Contoso_Poster/Paris_Auth_Redun.png)
  
<span data-ttu-id="d15fe-158">Nella figura 5 vengono mostrati i proxy Web e i server AD FS nella rete perimetrale e un set aggiuntivo di ognuno di questi in una rete virtuale di Azure cross-premise.</span><span class="sxs-lookup"><span data-stu-id="d15fe-158">Figure 5 shows web proxies and AD FS servers in the DMZ and an additional set of each in a cross-premises Azure virtual network.</span></span>
  
<span data-ttu-id="d15fe-p110">Quando i server di autenticazione principali nella rete perimetrale della sede centrale diventano non disponibili, il personale IT passa al set ridondante distribuito in IaaS di Azure. Le richieste di autenticazione successive provenienti dai computer della sede di Parigi usano il set in IaaS di Azure finché il problema di disponibilità non viene corretto.</span><span class="sxs-lookup"><span data-stu-id="d15fe-p110">When the primary authentication servers in the headquarters DMZ become unavailable, IT staff switch over to the redundant set deployed in Azure IaaS. Subsequent authentication requests from Paris office computers use the set in Azure IaaS until the availability problem is corrected.</span></span>
  
<span data-ttu-id="d15fe-161">Per effettuare questi passaggi, Contoso aggiorna il profilo Azure Traffic Manager affinché l'area di Parigi possa utilizzare un set di indirizzi IP diverso per i proxy di applicazioni Web:</span><span class="sxs-lookup"><span data-stu-id="d15fe-161">To switch over and switch back, Contoso updates the Azure Traffic Manager profile for the Paris region to use a different set of IP addresses for the web application proxies:</span></span>
  
- <span data-ttu-id="d15fe-162">Quando l'autenticazione ai server della rete perimetrale torna disponibile, usa gli indirizzi IP dei server nella rete perimetrale.</span><span class="sxs-lookup"><span data-stu-id="d15fe-162">When the DMZ authentication servers are available, use the IP addresses of the servers in the DMZ.</span></span>
    
- <span data-ttu-id="d15fe-163">Quando l'autenticazione ai server della rete perimetrale torna disponibile, usa gli indirizzi IP dei server in IaaS di Azure.</span><span class="sxs-lookup"><span data-stu-id="d15fe-163">When the DMZ authentication servers are not available, use the IP addresses of the servers in Azure IaaS.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="d15fe-164">See Also</span><span class="sxs-lookup"><span data-stu-id="d15fe-164">See Also</span></span>

[<span data-ttu-id="d15fe-165">Contoso nel Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="d15fe-165">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="d15fe-166">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="d15fe-166">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="d15fe-167">Identità di Microsoft Cloud per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="d15fe-167">Microsoft Cloud Identity for Enterprise Architects</span></span>](http://aka.ms/cloudarchidentity)
  
[<span data-ttu-id="d15fe-168">Protezione di dispositivi e identità per Office 365</span><span class="sxs-lookup"><span data-stu-id="d15fe-168">Identity and Device Protection for Office 365</span></span>](http://aka.ms/o365protect_device)
  
[<span data-ttu-id="d15fe-169">Guida di orientamento per Enterprise Cloud di Microsoft: risorse per i decision maker del settore IT</span><span class="sxs-lookup"><span data-stu-id="d15fe-169">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



