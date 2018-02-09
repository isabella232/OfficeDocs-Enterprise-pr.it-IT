---
title: Diagramma accessibile - rete integrazione di prodotti Microsoft Office Server
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
description: "In questo articolo è una versione testo accessibile del diagramma denominato rete integrazione di prodotti Microsoft Office Server."
ms.openlocfilehash: 3fa27b99bf0babf00c536057b9d21da784b6d94f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a><span data-ttu-id="8e15c-103">Diagramma accessibile - rete integrazione di prodotti Microsoft Office Server</span><span class="sxs-lookup"><span data-stu-id="8e15c-103">Accessible diagram - Network Integration of Microsoft Office Server Products</span></span>

<span data-ttu-id="8e15c-104">**Riepilogo:** In questo articolo è una versione testo accessibile del diagramma denominato rete integrazione di prodotti Microsoft Office Server.</span><span class="sxs-lookup"><span data-stu-id="8e15c-104">**Summary:** This article is an accessible text version of the diagram named Network Integration of Microsoft Office Server Products.</span></span>
  
<span data-ttu-id="8e15c-p101">Questo poster fornisce un'illustrazione generale di un ambiente di rete che include Lync Server 2013, SharePoint 2013 ed Exchange Server 2013. Viene inoltre i seguenti elementi di reti che sono comuni a questi prodotti: access interni e remoti, autenticazione, il traffico client e instradare il traffico dispositivi condivisi.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p101">This poster provides a general illustration of a network environment that includes Lync Server 2013, SharePoint 2013, and Exchange Server 2013. It also illustrates the following networking elements that are common across these products: remote and internal access, authentication, client traffic, and routing traffic through shared devices.</span></span> 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a><span data-ttu-id="8e15c-107">Concetti generali relativi a Lync, Exchange, SharePoint Server e Office Web Apps</span><span class="sxs-lookup"><span data-stu-id="8e15c-107">High-level concepts for Lync, Exchange, SharePoint Server, and Office Web Apps</span></span>

### <a name="about-the-design"></a><span data-ttu-id="8e15c-108">Sulla progettazione</span><span class="sxs-lookup"><span data-stu-id="8e15c-108">About the design</span></span>

#### <a name="streamlined-network-design"></a><span data-ttu-id="8e15c-109">Struttura della rete semplificate</span><span class="sxs-lookup"><span data-stu-id="8e15c-109">Streamlined network design</span></span>

<span data-ttu-id="8e15c-p102">Questa topologia viene illustrata una distribuzione di rete locale di SharePoint 2013, Exchange Server 2013 e Lync Server 2013. Viene inoltre illustrato l'utilizzo del servizio di basata sul cloud Microsoft, Exchange Online Protection, che offre una protezione da posta indesiderata e malware per il traffico in ingresso Simple Mail Transfer Protocol (SMTP) da Internet.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p102">This topology illustrates an on-premises network deployment of SharePoint 2013, Exchange Server 2013, and Lync Server 2013. It also shows the use of the Microsoft cloud-based service, Exchange Online Protection, which provides spam and malware protection for inbound Simple Mail Transfer Protocol (SMTP) traffic from the Internet.</span></span> 
  
<span data-ttu-id="8e15c-p103">Semplificata la progettazione di rete a un insieme minimo di funzionalità della rete. La progettazione non tiene conto protezione o infrastruttura funzionalità aggiuntive che potrebbero richiedere alcune organizzazioni.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p103">This network design is streamlined to a minimum set of network features. The design does not take into account additional security or infrastructure features that some organizations might require.</span></span> 
  
<span data-ttu-id="8e15c-114">Figura:</span><span class="sxs-lookup"><span data-stu-id="8e15c-114">This diagram:</span></span> 
  
- <span data-ttu-id="8e15c-115">Fornisce una topologia di rete di esempio che illustrano il traffico in ingresso e in uscita tramite un gateway router e il bilanciamento del carico di sessione il traffico client (interno ed esterno) per i livelli appropriati di SharePoint, Exchange e Lync server.</span><span class="sxs-lookup"><span data-stu-id="8e15c-115">Provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> 
    
- <span data-ttu-id="8e15c-116">Viene illustrato l'utilizzo dei server di accesso remoto facoltativo, ad esempio un gateway VPN di terze parti o un server DirectAccess, per la comunicazione protetta per i dipendenti remoti o mobili.</span><span class="sxs-lookup"><span data-stu-id="8e15c-116">Shows the use of optional remote access servers, such as a third-party VPN gateway or DirectAccess server, to provide secure communication for roaming or remote employees.</span></span> 
    
- <span data-ttu-id="8e15c-117">Vengono illustrati il SharePoint, Exchange e Lync flusso di traffico da client a ogni livello di piattaforma server.</span><span class="sxs-lookup"><span data-stu-id="8e15c-117">Details the SharePoint, Exchange, and Lync traffic flow from the client to each platform server tier.</span></span> 
    
- <span data-ttu-id="8e15c-118">Identifica il tipo di connessione di accesso remoto o interno basato su client (ad esempio partner o dipendenti) e il metodo di autenticazione utilizzato.</span><span class="sxs-lookup"><span data-stu-id="8e15c-118">Identifies the type of remote or internal access connection based on client (such as partner or employee), and the authentication method used.</span></span> 
    
- <span data-ttu-id="8e15c-119">Suddivide le piattaforme di SharePoint, Exchange e Lync per ruoli del server richiesti, che identifica il front-end, applicazione, database e altri livelli.</span><span class="sxs-lookup"><span data-stu-id="8e15c-119">Breaks down the SharePoint, Exchange, and Lync platforms by required server roles, identifying the front end, application, database, and other levels.</span></span> 
    
<span data-ttu-id="8e15c-p104">L'architettura utilizzato qui per SharePoint, Lync ed Exchange non suggerisce un modo migliore per l'implementazione di queste piattaforme. Fornisce un esempio come topologie variano in base alle esigenze di rete univoco e considerazioni sulla protezione.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p104">The architecture used here for SharePoint, Lync, and Exchange does not suggest a preferred way of implementing these platforms. It merely provides an example as topologies differ based on unique network requirements and security considerations.</span></span> 
  
#### <a name="gateway-router"></a><span data-ttu-id="8e15c-122">Router gateway</span><span class="sxs-lookup"><span data-stu-id="8e15c-122">Gateway router</span></span>

<span data-ttu-id="8e15c-p105">Per questa topologia router gateway si trova in corrispondenza del bordo della rete e il routing di tutto il traffico in ingresso e in uscita da e verso la rete intranet. In alternativa, si potrebbe essere anche altri componenti di collegano la distanza tra il router gateway e il servizio di bilanciamento del carico indicato, ad esempio più livelli di firewall. Questa topologia rappresenta semplicemente un modo per distribuire la rete tra molti. In questa configurazione, il gateway è configurato con elenchi di controllo di accesso (ACL) per consentire molto specifico traffico in ingresso e in uscita basati su IP nelle interfacce router. ACL, ispezione avanzata o Network Address Translation (NAT) può anche essere eseguito su altri dispositivi, ad esempio firewall attraverso la rete.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p105">For this topology, the gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet. Alternatively, there could also be other components that bridge the gap between the gateway router and the load balancer shown, such as multiple layers of firewalls. This topology represents just one way to deploy your network out of many. In this configuration, the gateway is configured with access control lists (ACLs) to permit very specific incoming and outgoing IP-based traffic on the router interfaces. ACLs, advanced inspection, or Network Address Translation (NAT) can also be performed on other devices, such as firewalls, throughout your network.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a><span data-ttu-id="8e15c-128">Carico bilanciamento e dispositivi proxy inverso</span><span class="sxs-lookup"><span data-stu-id="8e15c-128">Load balancer and reverse proxy devices</span></span>

<span data-ttu-id="8e15c-p106">È possibile utilizzare soluzioni di bilanciamento del carico di hardware o software per reindirizzare il traffico per i segmenti inclusi i server web front-end SharePoint e server Accesso Client di Exchange (classi). In alcuni casi è preferibile utilizzare il bilanciamento del carico basata su hardware livello 7 per i requisiti di persistenza come è possibile eseguire meglio utilizzando informazioni nella richiesta, ad esempio i cookie o intestazioni. Tuttavia, quali fattori di costo e l'aumento dell'utilizzo e carico di lavoro da questa soluzione non può essere preferibile per specifiche esigenze. Tenere presente quanto segue per il bilanciamento del carico in SharePoint, Exchange e Lync:</span><span class="sxs-lookup"><span data-stu-id="8e15c-p106">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). In some cases it's optimal to use a layer 7 hardware-based load balancer for persistence requirements as it can perform better by using information in the request, such as cookies or headers. However, factors like cost and increased utilization and workload from such a solution might not be desirable for your specific needs. Consider the following points for load balancing across SharePoint, Exchange, and Lync:</span></span> 
  
- <span data-ttu-id="8e15c-p107">SharePoint - per SharePoint 2013, è necessario abilitare l'affinità per i server web front-end. In genere, questo verrà utilizzato per la creazione di sessioni permanenti ed evitando più richieste di autenticazione da client a ogni server web front-end. Il nuovo servizio Cache distribuita in SharePoint 2013 archivia e distribuisce i token di accesso tra i server web nella farm di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p107">SharePoint - For SharePoint 2013, you do not need to enable affinity for your front-end web servers. Normally, this would be used for creating sticky sessions and avoiding multiple authentication requests from clients to each front-end web server. The new Distributed Cache service in SharePoint 2013 stores and distributes logon tokens across the web servers of the SharePoint farm.</span></span> 
    
- <span data-ttu-id="8e15c-p108">Exchange - In Exchange 2013, il ruolo del server accesso client è progettato per utilizzare il bilanciamento del carico di livello 4, la distribuzione richieste il livello di trasporto. Utilizzo del servizio di bilanciamento del carico e il carico di lavoro può ridurre notevolmente.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p108">Exchange - In Exchange 2013, the CAS role is designed to use layer 4 load balancing, distributing requests at the transport layer. This can significantly decrease load balancer utilization and workload.</span></span> 
    
- <span data-ttu-id="8e15c-p109">Lync - bilanciamento del carico del sistema DNS (Domain Name) è consigliata per il traffico di Strumentazione gestione Windows (SIP, Session Initiation Protocol) per i pool di Lync. (Bilanciamento del carico hardware) di bilanciamento del carico hardware è necessaria per il traffico di Lync Web (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="8e15c-p109">Lync - Domain Name System (DNS) load balancing is recommended for Session Initiation Protocol (SIP) traffic for Lync pools. Hardware load balancing (HLB) is required for Lync Web (HTTPS) traffic.</span></span> 
    
### <a name="remote-access-options"></a><span data-ttu-id="8e15c-140">Opzioni di accesso remoto</span><span class="sxs-lookup"><span data-stu-id="8e15c-140">Remote access options</span></span>

<span data-ttu-id="8e15c-p110">Sono disponibili diverse opzioni che è possono pubblicare risorse della rete intranet per i partner su Internet o fornire l'accesso remoto protetto per i dipendenti remoti o mobili. Quali ad esempio i proxy inversi, DirectAccess e gateway VPN di terze parti. Le soluzioni di accesso remoto descritte più avanti in questa sezione sono le possibilità di SharePoint, Lync ed Exchange o una combinazione di questi server in una distribuzione locale. Tuttavia, alcune opzioni remote potrebbero non funzionare con una particolare soluzione.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p110">There are several options that can publish intranet resources for partners on the Internet or provide secure remote access for remote or roaming employees. Such examples include reverse proxies, DirectAccess, and third-party VPN gateways. The remote access solutions discussed later in this section are possibilities for SharePoint, Lync, and Exchange, or any combination of these servers in an on-premises deployment. However, some remote options might not work with a particular solution.</span></span> 
  
<span data-ttu-id="8e15c-p111">Proxy inverso - proxy inverso supporta la crittografia del traffico, ad esempio Secure Sockets Layer (SSL) e con che è possibile pubblicare le applicazioni intranet e risorse web per l'autenticazione utenti e partner in Internet. Un esempio è Microsoft Forefront Unified Access Gateway (UAG). Molti bilanciamento del carico hardware supporta anche la funzionalità di proxy inverso. Esistono, tuttavia, gli scenari ancora validi per l'utilizzo di una soluzione autonoma in base alle esigenze e i requisiti, ad esempio l'ottimizzazione delle prestazioni, il contesto di sicurezza e isolamento di traffico.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p111">Reverse Proxy - A reverse proxy supports traffic encryption, such as Secure Sockets Layer (SSL), and with it you can publish intranet applications and web resources to authenticated users and partners on the Internet. An example is Microsoft Forefront Unified Access Gateway (UAG). Many hardware load balancers also support reverse proxy functionality. However, there are still valid scenarios for using a standalone solution based on your needs and requirements, such as traffic isolation, security compartmentalization, and performance optimization.</span></span> 
  
<span data-ttu-id="8e15c-149">Considerazioni e vantaggi relativi proxy inverso:</span><span class="sxs-lookup"><span data-stu-id="8e15c-149">Reverse-proxy benefits and considerations:</span></span> 
  
- <span data-ttu-id="8e15c-150">Consente l'accesso autenticato e protetta per i partner o utenti che accedono a risorse della rete intranet (utilizza SSL (TCP 443) tra il client e server proxy inverso).</span><span class="sxs-lookup"><span data-stu-id="8e15c-150">Provides authenticated and secured access for partners or users accessing intranet resources (uses SSL (TCP 443) between the client and reverse proxy server).</span></span> 
    
- <span data-ttu-id="8e15c-p112">Per Exchange, un vantaggio dell'utilizzo di un proxy inverso, ad esempio Forefront UAG è preautenticazione prima di accedere al server Accesso Client di Exchange. Gli utenti remoti mediante pubblicati applicazioni come Outlook Web Access (OWA) possono eseguire l'autenticazione di base, NTLM o Kerberos metodi prima che raggiungano la rete interna.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p112">For Exchange, a benefit of using a reverse proxy such as Forefront UAG is pre-authentication before accessing the Exchange Client access server. Remote access users using published applications such as Outlook Web Access (OWA) can authenticate with the basic, NTLM, or Kerberos methods before they reach the internal network.</span></span> 
    
- <span data-ttu-id="8e15c-153">Per Exchange e SharePoint soluzioni come Forefront UAG possono terminare le connessioni SSL e ridurre il carico del server di risorse intranet fornendo un singolo punto di gestione per i certificati.</span><span class="sxs-lookup"><span data-stu-id="8e15c-153">For Exchange and SharePoint, solutions like Forefront UAG can terminate SSL connections and decrease the load of the intranet resources server while providing a single point of management for certificates.</span></span> 
    
- <span data-ttu-id="8e15c-p113">Per Lync, il traffico Web (HTTPS) passa attraverso il proxy inverso (TCP 443) per la comunicazione client. I proxy di proxy inverso il protocollo HTTPS connessione a servizi Web di Lync, accesso client di Exchange e Office Web Apps. Lync Server 2013 non supporta UAG.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p113">For Lync, Web (HTTPS) traffic goes through the reverse proxy (TCP 443) for client communication. The reverse proxy proxies the HTTPS connection to Lync Web Services, Exchange CAS, and Office Web Apps. Lync Server 2013 does not support UAG.</span></span> 
    
<span data-ttu-id="8e15c-p114">DirectAccess - una tecnologia di accesso remoto che si basa su Internet Protocol security (IPsec) per l'autenticazione e per crittografare il traffico tra l'integrità e il server. DirectAccess consente di accedere contemporaneamente a Internet e intranet risorse per i dipendenti mobili e remoti senza dover avviare una connessione.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p114">DirectAccess - A remote access technology that relies on Internet Protocol security (IPsec) for authentication and for encrypting traffic between the DirectAccess client and server. DirectAccess provides simultaneous access to both Internet and intranet resources for roaming and remote employees without having to initiate a connection.</span></span> 
  
<span data-ttu-id="8e15c-159">DirectAccess aspetti da considerare:</span><span class="sxs-lookup"><span data-stu-id="8e15c-159">DirectAccess points to consider:</span></span> 
  
- <span data-ttu-id="8e15c-160">DirectAccess utilizza il traffico IPsec protetta (protocollo 50 e 51 e UDP 500) tra l'integrità e il server.</span><span class="sxs-lookup"><span data-stu-id="8e15c-160">DirectAccess uses IPsec protected traffic (protocol 50 and 51 and UDP 500) between the DirectAccess client and server.</span></span> 
    
- <span data-ttu-id="8e15c-161">DirectAccess per Windows Server 2012 e Windows 8 non è necessaria una distribuzione di infrastruttura a chiave pubblica (PKI) per l'autenticazione di client e server.</span><span class="sxs-lookup"><span data-stu-id="8e15c-161">DirectAccess for Windows Server 2012 and Windows 8 does not need a public key infrastructure (PKI) deployment for server and client authentication.</span></span> 
    
- <span data-ttu-id="8e15c-162">Si consiglia di base utilizzando DirectAccess con Lync Server 2013 a causa di problemi di latenza audio e video associati a crittografia e decrittografia IPsec.</span><span class="sxs-lookup"><span data-stu-id="8e15c-162">We recommend against using DirectAccess with Lync Server 2013 because of audio and video latency issues associated with IPsec encryption and decryption.</span></span> 
    
    <span data-ttu-id="8e15c-p115">Gateway VPN - gateway VPN tipica fornire una connessione di accesso remoto in cui un client di accesso remoto è previsto logicamente nella rete intranet attraverso una connessione tunnel e dall'utente. È possibile utilizzare unificata l'accesso remoto in Windows Server 2012 o diverse soluzioni di terze parti per fornire l'accesso protetto alla rete intranet per dipendenti remoti o mobili. VPN non è consigliata per Lync. Il traffico remoto Lync deve utilizzare i server perimetrali e dividere tunnel.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p115">VPN Gateway - Typical VPN gateways provide a remote access connection in which a remote access client computer is logically projected onto the intranet through a tunneled and user-initiated connection. You can use Unified Remote Access in Windows Server 2012 or several third-party solutions to provide secured access to the intranet for roaming or remote employees. VPN is not recommended for Lync. Remote Lync traffic should use the Edge Servers and split tunneling.</span></span> 
    
### <a name="domain-name-system-dns-considerations"></a><span data-ttu-id="8e15c-167">Considerazioni per Domain Name System (DNS)</span><span class="sxs-lookup"><span data-stu-id="8e15c-167">Domain Name System (DNS) considerations</span></span>

<span data-ttu-id="8e15c-168">È necessario pianificare per il set di record DNS che consentono agli utenti di Internet e intranet risolvere i nomi DNS per gli indirizzi IP appropriati.</span><span class="sxs-lookup"><span data-stu-id="8e15c-168">You need to plan for the set of DNS records that allow both Internet and intranet users to resolve DNS names to the appropriate IP addresses.</span></span> 
  
- <span data-ttu-id="8e15c-169">Per basato su Internet partner e dipendenti remoti o mobili, i record DNS registrati con i server DNS Internet forniscono risoluzione per l'insieme di indirizzi IP pubblici corrispondente al router gateway, il Server perimetrale di Lync, l'insieme di indirizzi IP virtuali (VIP) servizio di bilanciamento del carico e il gateway DirectAccess o una rete VPN in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="8e15c-169">For Internet-based partners and roaming or remote employees, DNS records registered with Internet DNS servers provide resolution to the set of public IP addresses corresponding to the gateway router, the Lync Edge Server, the set of virtual IP addresses (VIPs) on the load balancer, and the DirectAccess or VPN gateway as needed.</span></span> 
    
- <span data-ttu-id="8e15c-170">Per gli utenti basate su intranet, i record DNS registrati con server DNS della rete intranet forniscono risoluzione per l'insieme di indirizzi IP virtuali (VIP) del servizio di bilanciamento del carico per l'accesso alle risorse di SharePoint, Lync ed Exchange.</span><span class="sxs-lookup"><span data-stu-id="8e15c-170">For intranet-based users, DNS records registered with intranet DNS servers provide resolution to the set of virtual IP addresses (VIPs) on the load balancer for access to SharePoint, Lync, and Exchange resources.</span></span> 
    
- <span data-ttu-id="8e15c-p116">Client DirectAccess utilizzano server DNS della rete intranet di nomi che corrispondono ai server DNS Internet per i nomi che non e spazio dei nomi DNS intranet. Per semplificare l'operazione di DirectAccess, prendere in considerazione l'utilizzo di un'implementazione di DNS split che utilizza spazi dei nomi DNS diversi per i nomi basato su Internet e intranet. Utilizzare ad esempio, contoso.com per Internet dello spazio dei nomi e corp.contoso.com per lo spazio dei nomi intranet.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p116">DirectAccess clients use intranet DNS servers for names corresponding to the intranet DNS name space and Internet DNS servers for names that do not. To simplify the operation of DirectAccess, consider the use of a split DNS implementation that uses different DNS namespaces for intranet and Internet-based names. For example, use contoso.com for Internet namespace and corp.contoso.com for the intranet namespace.</span></span> 
    
- <span data-ttu-id="8e15c-p117">Exchange utilizza un modello DNS diviso in host per la risoluzione IP diverso sul traffico pubblicamente indirizzato rispetto a quello della rete aziendale. Come minimo, è necessario disporre dei record DNS per OWA, individuazione automatica, ActiveSync URL per il traffico client e un record MX per la posta in ingresso.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p117">Exchange uses a split DNS model where host to IP resolution differs on publicly routed traffic from that on the corporate network. At a minimum, you need to have DNS records for OWA, Autodiscover, ActiveSync URLs for client traffic, and an MX record for inbound mail.</span></span> 
    
- <span data-ttu-id="8e15c-176">Se si utilizza Exchange Online Protection (EOP), il record MX punta a tale servizio anziché la farm di Exchange.</span><span class="sxs-lookup"><span data-stu-id="8e15c-176">If you are using Exchange Online Protection (EOP), your MX record points to that service instead of your Exchange farm.</span></span> 
    
- <span data-ttu-id="8e15c-177">Per Exchange, è necessario un modello di prova di proprietà record TXT nel sistema DNS pubblico e un ID di organizzazione federativa impostare condivisione federata.</span><span class="sxs-lookup"><span data-stu-id="8e15c-177">For Exchange, you need a proof of ownership TXT record in your public DNS, and a Federation Org ID to set up federated sharing.</span></span> 
    
- <span data-ttu-id="8e15c-178">Accesso remoto VPN client possono essere configurati per utilizzare solo i server DNS della rete intranet quando è attiva la connessione VPN di accesso remoto.</span><span class="sxs-lookup"><span data-stu-id="8e15c-178">Remote access VPN clients can be configured to use only intranet DNS servers when the remote access VPN connection is active.</span></span> 
    
### <a name="diagram-description"></a><span data-ttu-id="8e15c-179">Descrizione diagramma</span><span class="sxs-lookup"><span data-stu-id="8e15c-179">Diagram Description</span></span>

<span data-ttu-id="8e15c-p118">In questo diagramma viene fornita una topologia di rete di esempio che illustrano il traffico in ingresso e in uscita tramite un gateway router e il bilanciamento del carico di sessione il traffico client (interno ed esterno) per i livelli appropriati di SharePoint, Exchange e Lync server. La descrizione di questo diagramma viene suddiviso in due parti:</span><span class="sxs-lookup"><span data-stu-id="8e15c-p118">This diagram provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers. The description of this diagram is divided into two parts:</span></span> 
  
- <span data-ttu-id="8e15c-182">Descrizione dei componenti mostrato nella figura</span><span class="sxs-lookup"><span data-stu-id="8e15c-182">Description of components shown in the diagram</span></span> 
    
- <span data-ttu-id="8e15c-183">Descrizione di come traffico si sposta tra i componenti per i livelli di SharePoint, Exchange, Lync e Office Web Apps server.</span><span class="sxs-lookup"><span data-stu-id="8e15c-183">Description of how traffic moves through the components to the SharePoint, Exchange, Lync, and Office Web Apps server tiers.</span></span> 
    
#### <a name="description-of-components-shown-in-the-diagram"></a><span data-ttu-id="8e15c-184">Descrizione dei componenti mostrato nella figura</span><span class="sxs-lookup"><span data-stu-id="8e15c-184">Description of components shown in the diagram</span></span>

#### <a name="user-types"></a><span data-ttu-id="8e15c-185">Tipi di utente</span><span class="sxs-lookup"><span data-stu-id="8e15c-185">User types</span></span>

<span data-ttu-id="8e15c-186">Sono disponibili quattro tipi di utenti diversi, tre all'esterno dei servizi cloud e di rete e uno interno, che comprendono:</span><span class="sxs-lookup"><span data-stu-id="8e15c-186">There are four different types of users, three outside the network and cloud services and one internal, which include:</span></span> 
  
- <span data-ttu-id="8e15c-187">Società (business to business) partner-esterno</span><span class="sxs-lookup"><span data-stu-id="8e15c-187">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="8e15c-188">Singoli partner (SharePoint e anonimi (Lync))-esterno</span><span class="sxs-lookup"><span data-stu-id="8e15c-188">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="8e15c-189">Esterni dipendenti remoti e mobili</span><span class="sxs-lookup"><span data-stu-id="8e15c-189">Roaming and remote employees-external</span></span> 
    
- <span data-ttu-id="8e15c-190">Dipendenti interni</span><span class="sxs-lookup"><span data-stu-id="8e15c-190">Internal employees</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="8e15c-191">Traffico di posta elettronica basata sul cloud</span><span class="sxs-lookup"><span data-stu-id="8e15c-191">Cloud-based email traffic</span></span>

<span data-ttu-id="8e15c-192">Non vi è un componente basato su cloud per il traffico di posta elettronica basata su SMTP, ospitate su Internet Mail o Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="8e15c-192">There is a cloud-based component for SMTP-based email traffic, either Internet Mail Hosts or Exchange Online Protection.</span></span> 
  
#### <a name="authentication-for-external-access"></a><span data-ttu-id="8e15c-193">Autenticazione per l'accesso esterno</span><span class="sxs-lookup"><span data-stu-id="8e15c-193">Authentication for external access</span></span>

<span data-ttu-id="8e15c-p119">Non esiste un set specifico di procedure di autenticazione per Lync, SharePoint ed Exchange per ognuno dei tipi di utente. Vengono descritte in dettaglio più avanti in questo documento.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p119">There is a specific set of authentication procedures for Lync, SharePoint, and Exchange for each of the user types. They are described in more detail later in this document.</span></span> 
  
#### <a name="gateway-router-with-acls"></a><span data-ttu-id="8e15c-196">Router gateway con ACL</span><span class="sxs-lookup"><span data-stu-id="8e15c-196">Gateway router with ACLs</span></span>

<span data-ttu-id="8e15c-197">Router gateway si trova in corrispondenza del bordo della rete e il routing di tutto il traffico in ingresso e in uscita da e verso la rete intranet.</span><span class="sxs-lookup"><span data-stu-id="8e15c-197">The gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a><span data-ttu-id="8e15c-198">Server di accesso remoto di Lync e SharePoint</span><span class="sxs-lookup"><span data-stu-id="8e15c-198">Remote access servers for Lync and SharePoint</span></span>

<span data-ttu-id="8e15c-199">Questa topologia include un server perimetrale di Lync e un gateway VPN SharePoint o server DirectAccess.</span><span class="sxs-lookup"><span data-stu-id="8e15c-199">This topology includes a Lync Edge server, and a SharePoint VPN gateway or DirectAccess server.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a><span data-ttu-id="8e15c-200">Servizio di bilanciamento del carico e il dispositivo proxy inverso</span><span class="sxs-lookup"><span data-stu-id="8e15c-200">Load balancer and reverse proxy device</span></span>

<span data-ttu-id="8e15c-p120">È possibile utilizzare soluzioni di bilanciamento del carico di hardware o software per reindirizzare il traffico per i segmenti inclusi i server web front-end SharePoint e server Accesso Client di Exchange (classi). Questa topologia vengono illustrati i componenti di Lync VIP, SharePoint VIP e indirizzo IP virtuale di Exchange nel servizio di bilanciamento del carico.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p120">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). This topology shows Lync VIP, SharePoint VIP, and Exchange VIP components in the load balancer.</span></span> 
  
#### <a name="servers"></a><span data-ttu-id="8e15c-203">Server</span><span class="sxs-lookup"><span data-stu-id="8e15c-203">Servers</span></span>

<span data-ttu-id="8e15c-p121">Esistono quattro server: Lync, SharePoint, Exchange e Office Web Apps Server. Ogni server può essere associato a tre livelli: front-end, a livelli di accesso client, un livello di applicazione e un livello di database e archivi.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p121">There are four servers: Lync, SharePoint, Exchange, and Office Web Apps Server. Each server can have three tiers: a front-end, client-access tier, an application tier, and a database/storage tier.</span></span>
  
#### <a name="front-end-client-access-tier"></a><span data-ttu-id="8e15c-206">Front-end, a livelli di accesso client</span><span class="sxs-lookup"><span data-stu-id="8e15c-206">Front-end, client-access tier</span></span>

<span data-ttu-id="8e15c-207">Questo livello è componenti in tutti i quattro server seguenti:</span><span class="sxs-lookup"><span data-stu-id="8e15c-207">This tier has components on all four servers:</span></span> 
  
- <span data-ttu-id="8e15c-p122">Pool di Lync (front-end). Nel diagramma vengono illustrati due database Lync.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p122">Lync pool (front end). The diagram shows two Lync databases.</span></span> 
    
- <span data-ttu-id="8e15c-p123">Front-end di SharePoint e cache distribuita. Nel diagramma vengono illustrati tre database di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p123">SharePoint front end and distributed cache. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="8e15c-p124">Exchange Server accesso client. Nel diagramma vengono illustrati due database di Exchange.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p124">Exchange CAS. The diagram shows two Exchange databases.</span></span> 
    
- <span data-ttu-id="8e15c-p125">Office Web Apps Server. Nel diagramma vengono illustrati due database di Office Web Apps.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p125">Office Web Apps Server. The diagram shows two Office Web Apps databases.</span></span> 
    
#### <a name="application-tier"></a><span data-ttu-id="8e15c-216">Livello applicazione</span><span class="sxs-lookup"><span data-stu-id="8e15c-216">Application tier</span></span>

<span data-ttu-id="8e15c-217">Questo livello è componenti solo nel server di SharePoint seguenti:</span><span class="sxs-lookup"><span data-stu-id="8e15c-217">This tier has components only on the SharePoint server:</span></span> 
  
- <span data-ttu-id="8e15c-p126">Ricerca (query, indicizzazione, amministrazione). Nel diagramma vengono illustrati tre database di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p126">Search (query, index, admin). The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="8e15c-p127">Elaborazione batch. Nel diagramma vengono illustrati tre database di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p127">Batch processing. The diagram shows three SharePoint databases.</span></span> 
    
#### <a name="databasestorage-tier"></a><span data-ttu-id="8e15c-222">Livello di database e archivi</span><span class="sxs-lookup"><span data-stu-id="8e15c-222">Database/storage tier</span></span>

<span data-ttu-id="8e15c-223">Questo livello con componenti sui server Exchange, Lync e SharePoint:</span><span class="sxs-lookup"><span data-stu-id="8e15c-223">This tier has components on the Lync, SharePoint, and Exchange servers:</span></span> 
  
- <span data-ttu-id="8e15c-p128">Database di Lync (back-end). Nel diagramma vengono illustrati tre database Lync.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p128">Lync Database (backend). The diagram shows three Lync databases.</span></span> 
    
- <span data-ttu-id="8e15c-p129">Database di SharePoint. Nel diagramma vengono illustrati tre database di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p129">SharePoint Database. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="8e15c-p130">Server cassette postali di Exchange. Nel diagramma vengono illustrati due server di cassette postali di Exchange.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p130">Exchange Mailbox server. The diagram shows two Exchange Mailbox servers.</span></span> 
    
<span data-ttu-id="8e15c-230">Per ulteriori informazioni sui componenti installati in ognuno dei ruoli del server SharePoint, vedere [Topologie semplificate per SharePoint 2013](https://aka.ms/Ma5cgk).</span><span class="sxs-lookup"><span data-stu-id="8e15c-230">For more information about components installed on each of the SharePoint server roles, see [Streamlined Topologies for SharePoint 2013](https://aka.ms/Ma5cgk).</span></span> 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a><span data-ttu-id="8e15c-231">Descrizione di come traffico si sposta tra i componenti a livelli diversi server</span><span class="sxs-lookup"><span data-stu-id="8e15c-231">Description of how traffic moves through the components to the different server tiers</span></span>

<span data-ttu-id="8e15c-232">In questa sezione viene descritto come spostare le richieste degli utenti tramite la topologia di rete.</span><span class="sxs-lookup"><span data-stu-id="8e15c-232">This section describes how user requests move through the network topology.</span></span> 
  
#### <a name="authentication-and-routing-for-external-access"></a><span data-ttu-id="8e15c-233">Autenticazione e il routing per l'accesso esterno</span><span class="sxs-lookup"><span data-stu-id="8e15c-233">Authentication and routing for external access</span></span>

<span data-ttu-id="8e15c-234">Esistono tre diversi tipi di client esterni servizi cloud e di rete, che comprendono:</span><span class="sxs-lookup"><span data-stu-id="8e15c-234">There are three different types of clients outside the network and cloud services, which include:</span></span> 
  
- <span data-ttu-id="8e15c-235">Società (business to business) partner-esterno</span><span class="sxs-lookup"><span data-stu-id="8e15c-235">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="8e15c-236">Singoli partner (SharePoint e anonimi (Lync))-esterno</span><span class="sxs-lookup"><span data-stu-id="8e15c-236">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="8e15c-237">Esterni dipendenti remoti e mobili</span><span class="sxs-lookup"><span data-stu-id="8e15c-237">Roaming and remote employees-external</span></span> 
    
<span data-ttu-id="8e15c-238">L'autenticazione e il processo di distribuzione per ogni tipo di utente esterno è descritto singolarmente.</span><span class="sxs-lookup"><span data-stu-id="8e15c-238">The authentication and routing process for each external user type is described individually.</span></span> 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a><span data-ttu-id="8e15c-239">Società partner (business-to-business) (https://partnerweb.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="8e15c-239">Partner companies (business-to-business) (https://partnerweb.contoso.com)</span></span>

- <span data-ttu-id="8e15c-p131">Lync: trust federativo con altre organizzazioni, Skype e la connettività di messaggistica immediata pubblica (PIC) con AOL. Il traffico della federazione Lync passa attraverso il router gateway per il Server perimetrale di Lync, all'indirizzo VIP Lync (server di proxy inverso/del servizio di bilanciamento del carico) e quindi a Lync Server.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p131">Lync: federation trust with other organizations, Skype and Public IM Connectivity (PIC) with AOL. The Lync federation traffic goes through the gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="8e15c-p132">SharePoint: Attendibili provider di identità di partner con autenticazione SAML. Il traffico client SharePoint passa attraverso il router Gateway nell'indirizzo IP virtuale di SharePoint (server di proxy inverso/del servizio di bilanciamento del carico) e quindi al Server di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p132">SharePoint: Trusted partner identity provider with SAML authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="8e15c-p133">Exchange: Mutual Auth TLS per il traffico di posta elettronica, l'autenticazione SAML per la condivisione federata. Il traffico client di Exchange passa attraverso il router Gateway nell'indirizzo IP virtuale di Exchange (server di proxy inverso/del servizio di bilanciamento del carico) e quindi al Server di Exchange.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p133">Exchange: Mutual Auth TLS for mail traffic, SAML authentication for Federated Sharing. The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="8e15c-246">Il traffico SMTP passa attraverso il router Gateway e l'indirizzo IP virtuale di Exchange (server di proxy inverso/del servizio di bilanciamento del carico) al server di Exchange.</span><span class="sxs-lookup"><span data-stu-id="8e15c-246">SMTP traffic goes through the Gateway router and through the Exchange VIP (load balancer/reverse proxy server) to the Exchange server.</span></span> 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a><span data-ttu-id="8e15c-247">Singoli partner (SharePoint) e anonimi (Lync) (https://partnerweb.contoso.com e https://meet.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="8e15c-247">Individual partners (SharePoint) and anonymous (Lync) (https://partnerweb.contoso.com and https://meet.contoso.com)</span></span>

- <span data-ttu-id="8e15c-p134">Lync: gli utenti anonimi possono partecipare solo alle riunioni di Lync organizzate in base ai dipendenti. Il traffico della federazione Lync passa attraverso il router Gateway per il Server perimetrale di Lync, all'indirizzo VIP Lync (server di proxy inverso/del servizio di bilanciamento del carico) e quindi a Lync Server.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p134">Lync: anonymous users can only join Lync meetings organized by employees. The Lync federation traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="8e15c-p135">SharePoint: Il provider di identità di partner attendibile con autenticazione basata su moduli o autenticazione SAML. Il traffico client SharePoint passa attraverso il router Gateway nell'indirizzo IP virtuale di SharePoint (server di proxy inverso/del servizio di bilanciamento del carico) e quindi al Server di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p135">SharePoint: Trusted partner identity provider with SAML authentication or forms-based authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="8e15c-252">Exchange: Non applicabile.</span><span class="sxs-lookup"><span data-stu-id="8e15c-252">Exchange: Does not apply.</span></span> 
    
- <span data-ttu-id="8e15c-253">Lync Web traffico attraversa il router Gateway per il Server perimetrale di Lync, all'indirizzo VIP Lync (server proxy inverso/del servizio di bilanciamento del carico,) al bilanciamento del carico hardware, che è necessaria per il traffico HTTPS, e quindi a Lync Server.</span><span class="sxs-lookup"><span data-stu-id="8e15c-253">Lync Web traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="roaming-and-remote-employees"></a><span data-ttu-id="8e15c-254">Dipendenti remoti e mobili</span><span class="sxs-lookup"><span data-stu-id="8e15c-254">Roaming and remote employees</span></span>

1. <span data-ttu-id="8e15c-255">https://Intranet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8e15c-255">https://intranet.contoso.com</span></span> 
    
2. <span data-ttu-id="8e15c-256">https://Teams.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8e15c-256">https://teams.contoso.com</span></span> 
    
3. <span data-ttu-id="8e15c-257">https://My.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8e15c-257">https://my.contoso.com</span></span>
    
4. <span data-ttu-id="8e15c-258">https://partnerweb.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8e15c-258">https://partnerweb.contoso.com</span></span> 
    
5. <span data-ttu-id="8e15c-259">https://Mail.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="8e15c-259">https://mail.contoso.com\*</span></span> 
    
6. <span data-ttu-id="8e15c-260">https://dial.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="8e15c-260">https://dial.contoso.com\*</span></span>
    
7. <span data-ttu-id="8e15c-261">https://Meet.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="8e15c-261">https://meet.contoso.com\*</span></span>
    
* <span data-ttu-id="8e15c-262">L'URL di Exchange sono le seguenti directory virtuali: servizio di individuazione automatica, ecp, servizi Web Exchange, Microsoft-Server-ActiveSync, della Rubrica offline, owa, PowerShell</span><span class="sxs-lookup"><span data-stu-id="8e15c-262">The Exchange URL has the following virtual directories: Autodiscover, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell</span></span> 
  
- <span data-ttu-id="8e15c-p136">Lync: L'autenticazione TLS DSK o NTLM. Il traffico client Lync passa attraverso il router Gateway per il Server perimetrale di Lync, all'indirizzo VIP Lync (server di proxy inverso/del servizio di bilanciamento del carico) e quindi a Lync Server.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p136">Lync: TLS-DSK or NTLM authentication. The Lync client traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="8e15c-p137">SharePoint: Servizi di dominio Active Directory (AD DS), l'autenticazione basata su moduli o autenticazione SAML. Il traffico client SharePoint passa attraverso il gateway VPN o il server DirectAccess nell'indirizzo IP virtuale di SharePoint (server di proxy inverso/del servizio di bilanciamento del carico) e quindi al server di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p137">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes through the VPN gateway or the DirectAccess server to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint server.</span></span> 
    
- <span data-ttu-id="8e15c-p138">Exchange: L'autenticazione di base su SSL (ActiveSync, individuazione automatica), l'autenticazione basata su moduli (OWA). Il traffico client di Exchange passa attraverso il router Gateway nell'indirizzo IP virtuale di Exchange (server di proxy inverso/del servizio di bilanciamento del carico) e quindi al Server di Exchange.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p138">Exchange: Basic authentication over SSL (ActiveSync, Autodiscover), forms-based authentication (OWA). The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="8e15c-269">Il traffico client Lync passa attraverso il router Gateway per Lync indirizzo IP virtuale (server di proxy inverso/del servizio di bilanciamento del carico) al bilanciamento del carico hardware, che è necessaria per il traffico HTTPS, e quindi a Lync Server.</span><span class="sxs-lookup"><span data-stu-id="8e15c-269">Lync client traffic goes through the Gateway router to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="authentication-for-internal-access"></a><span data-ttu-id="8e15c-270">Autenticazione per l'accesso interno</span><span class="sxs-lookup"><span data-stu-id="8e15c-270">Authentication for internal access</span></span>

#### <a name="internal-employees"></a><span data-ttu-id="8e15c-271">Dipendenti interni</span><span class="sxs-lookup"><span data-stu-id="8e15c-271">Internal employees</span></span>

> <span data-ttu-id="8e15c-272">https://Intranet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8e15c-272">https://intranet.contoso.com</span></span> 
    
> <span data-ttu-id="8e15c-273">https://Teams.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8e15c-273">https://teams.contoso.com</span></span> 
    
> <span data-ttu-id="8e15c-274">https://My.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8e15c-274">https://my.contoso.com</span></span>
    
> <span data-ttu-id="8e15c-275">https://partnerweb.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8e15c-275">https://partnerweb.contoso.com</span></span>
    
> <span data-ttu-id="8e15c-276">https://Mail.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="8e15c-276">https://mail.contoso.com\*</span></span> 
    
> <span data-ttu-id="8e15c-277">https://dial.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8e15c-277">https://dial.contoso.com</span></span> 
    
> <span data-ttu-id="8e15c-278">https://Meet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8e15c-278">https://meet.contoso.com</span></span>
    
> <span data-ttu-id="8e15c-279">https://Admin.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8e15c-279">https://admin.contoso.com</span></span>
    
- <span data-ttu-id="8e15c-p139">Lync: Autenticazione Kerberos, TLS DSK o NTLM. Il traffico client Lync passa all'indirizzo VIP Lync (server di proxy inverso/del servizio di bilanciamento del carico) e quindi a Lync Server.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p139">Lync: Kerberos, TLS-DSK, or NTLM authentication. The Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="8e15c-p140">SharePoint: Servizi di dominio Active Directory (AD DS), l'autenticazione basata su moduli o autenticazione SAML. Il traffico client di SharePoint viene inoltrata all'indirizzo VIP SharePoint (server di proxy inverso/del servizio di bilanciamento del carico) e quindi al Server di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p140">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="8e15c-p141">Exchange: Di dominio Active Directory, l'autenticazione basata su form. Il traffico client di Exchange viene inoltrata nell'indirizzo IP virtuale di Exchange (server di proxy inverso/del servizio di bilanciamento del carico) e quindi al Server di Exchange.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p141">Exchange: AD DS, forms-based authentication. The Exchange client traffic goes to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="8e15c-286">Il traffico client Lync passerà a Lync indirizzo IP virtuale (server di proxy inverso/del servizio di bilanciamento del carico) al bilanciamento del carico hardware, che è necessaria per il traffico HTTPS, e quindi a Lync Server.</span><span class="sxs-lookup"><span data-stu-id="8e15c-286">Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="8e15c-287">Traffico di posta elettronica basata sul cloud</span><span class="sxs-lookup"><span data-stu-id="8e15c-287">Cloud-based email traffic</span></span>

<span data-ttu-id="8e15c-288">Il componente basata su cloud per il traffico di posta elettronica basata su SMTP è costituita da host della posta Internet o Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="8e15c-288">The cloud-based component for SMTP-based email traffic consists of either Internet Mail Hosts or Exchange Online Protection.</span></span>
  
<span data-ttu-id="8e15c-p142">Questi componenti spostare il traffico di posta elettronica tramite la rete tramite SMTP. Il traffico attraversa il router Gateway nell'indirizzo IP virtuale di Exchange (server di proxy inverso/del servizio di bilanciamento del carico) e quindi al Server di Exchange.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p142">These components move email traffic over the network using SMTP. The traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
  
### <a name="network-traffic-legend"></a><span data-ttu-id="8e15c-291">Legenda del traffico di rete</span><span class="sxs-lookup"><span data-stu-id="8e15c-291">Network traffic legend</span></span>

<span data-ttu-id="8e15c-292">La casella legenda Mostra graficamente i diversi tipi di traffico illustrato nel grafico nelle diverse righe colorate come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="8e15c-292">The legend box graphically shows the different types of traffic depicted on the graph in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="8e15c-293">Verde riga: Lync SIP traffico</span><span class="sxs-lookup"><span data-stu-id="8e15c-293">Green line: Lync SIP traffic</span></span> 
    
- <span data-ttu-id="8e15c-294">Blu riga: il traffico Web di Lync</span><span class="sxs-lookup"><span data-stu-id="8e15c-294">Blue line: Lync Web traffic</span></span> 
    
- <span data-ttu-id="8e15c-295">Viola riga: il traffico client di SharePoint</span><span class="sxs-lookup"><span data-stu-id="8e15c-295">Purple line: SharePoint client traffic</span></span> 
    
- <span data-ttu-id="8e15c-296">Linea arancione: il traffico client di Exchange</span><span class="sxs-lookup"><span data-stu-id="8e15c-296">Orange line: Exchange client traffic</span></span> 
    
- <span data-ttu-id="8e15c-297">Grigio riga: il traffico di Exchange Server di posta elettronica tra Exchange in locale ed Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="8e15c-297">Gray line: Exchange Mail Server traffic between Exchange on-premises and Exchange Online Protection.</span></span> 
    
<span data-ttu-id="8e15c-298">Nella casella legenda inoltre descritti i diversi tipi di traffico e le porte che utilizzano.</span><span class="sxs-lookup"><span data-stu-id="8e15c-298">The different types of traffic and the ports that they use are also described in the legend box.</span></span> 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a><span data-ttu-id="8e15c-299">Traffico SIP Lync e Lync web</span><span class="sxs-lookup"><span data-stu-id="8e15c-299">Lync SIP traffic and Lync web traffic</span></span>

<span data-ttu-id="8e15c-300">Server perimetrale Lync utilizza le porte seguenti per le comunicazioni degli utenti esterni:</span><span class="sxs-lookup"><span data-stu-id="8e15c-300">The Lync Edge Server uses the following ports for external user communication:</span></span> 
  
- <span data-ttu-id="8e15c-301">Il traffico di segnalazione/messaggistica immediata (SIP/semplice): porta TCP 443 (open per il traffico in ingresso)</span><span class="sxs-lookup"><span data-stu-id="8e15c-301">Signaling/IM traffic (SIP/SIMPLE): TCP port 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="8e15c-302">Web (PSOM) traffico delle conferenze: TCP 443 (aperto per il traffico in ingresso)</span><span class="sxs-lookup"><span data-stu-id="8e15c-302">Web conferencing traffic (PSOM): TCP 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="8e15c-303">Un traffico audio / video (SRTP): 443 TCP, UDP 3478 e TCP 50000 a 59999 (facoltativo) (aperto per il traffico in ingresso e in uscita)</span><span class="sxs-lookup"><span data-stu-id="8e15c-303">A/V traffic (SRTP): TCP 443, UDP 3478 and TCP 50000-59999 (optional) (open for inbound and outbound traffic)</span></span> 
    
<span data-ttu-id="8e15c-304">Server perimetrale Lync utilizza le porte seguenti per le comunicazioni federate:</span><span class="sxs-lookup"><span data-stu-id="8e15c-304">Lync Edge Server uses the following ports for federation communication:</span></span> 
  
- <span data-ttu-id="8e15c-305">Porte TCP 5061 (SIP) 5269 (XMPP) 443 e UDP 3478 (SRTP) (aperto per il traffico in ingresso e in uscita)</span><span class="sxs-lookup"><span data-stu-id="8e15c-305">TCP ports 5061 (SIP), 5269 (XMPP), 443 and UDP 3478 (SRTP) (open for inbound and outbound traffic)</span></span> 
    
#### <a name="sharepoint-client-traffic"></a><span data-ttu-id="8e15c-306">Traffico client di SharePoint</span><span class="sxs-lookup"><span data-stu-id="8e15c-306">SharePoint client traffic</span></span>

<span data-ttu-id="8e15c-p143">SharePoint è possibile utilizzare la porta TCP 443 (SSL) per la comunicazione crittografata tra il client e il servizio di bilanciamento del carico. Per l'accesso esterno da Internet, è necessario che la porta aperto per il traffico in ingresso e in uscita sul router gateway (o firewall esterno).</span><span class="sxs-lookup"><span data-stu-id="8e15c-p143">SharePoint can use TCP port 443 (SSL) for encrypted communication between the client and the load balancer. For external access from the Internet, this port needs to be opened for inbound and outbound traffic on the gateway router (or external firewall).</span></span> 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a><span data-ttu-id="8e15c-309">Il traffico client di Exchange e il traffico di server di posta elettronica di Exchange</span><span class="sxs-lookup"><span data-stu-id="8e15c-309">Exchange client traffic and Exchange mail server traffic</span></span>

<span data-ttu-id="8e15c-p144">Exchange utilizza la porta TCP 25 (SMTP) per le comunicazioni server-to-server. La maggior parte del traffico dei client (OWA, ActiveSync, individuazione automatica, Outlook via Internet) viene gestito tramite la porta 443 (HTTPS). Se sono presenti client POP o IMAP, le porte 110 (POP3), 995 (POP3 crittografato), 143 (IMAP4), 993 crittografate IMAP4 () e 587 (SMTP) vengono utilizzate anche per supportare tali client.</span><span class="sxs-lookup"><span data-stu-id="8e15c-p144">Exchange uses TCP port 25 (SMTP) for server-to-server communications. Most client traffic (OWA, ActiveSync, Autodiscover, Outlook Anywhere) is handled over port 443 (HTTPS). If you have POP or IMAP clients, ports 110 (POP3), 995 (encrypted POP3), 143 (IMAP4), 993 (encrypted IMAP4), and 587 (SMTP) are also used to support these clients.</span></span> 
  
#### <a name="more-on-lync-network-traffic"></a><span data-ttu-id="8e15c-313">Ulteriori in Lync il traffico di rete?</span><span class="sxs-lookup"><span data-stu-id="8e15c-313">More on Lync network traffic?</span></span>

<span data-ttu-id="8e15c-p145">Informazioni su come Lync Server consentono alle organizzazioni forniscono messaggistica immediata, servizi di conferenza web, la condivisione delle applicazioni e le comunicazioni vocali. Per ulteriori informazioni, vedere [Poster dei carichi di lavoro di protocollo di Microsoft Lync Server 2013](https://aka.ms/G5jzjo).</span><span class="sxs-lookup"><span data-stu-id="8e15c-p145">Learn how Lync Server can help your organization provide instant messaging, web conferencing, application sharing, and voice communication. For more information, see [Microsoft Lync Server 2013 Protocol Workloads Poster](https://aka.ms/G5jzjo).</span></span> 
  
<span data-ttu-id="8e15c-316">Il poster include inoltre un codice QR per accedere a queste informazioni.</span><span class="sxs-lookup"><span data-stu-id="8e15c-316">The poster also includes a QR code to access this information.</span></span> 
  

