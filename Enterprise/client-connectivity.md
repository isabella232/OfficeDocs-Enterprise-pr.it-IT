---
title: Connettività dei client
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: 'Riepilogo: Illustra la modalità di connessione dei computer client ai tenant di Office 365, in base al percorso del computer client e ai datacenter dei tenant di Office 365.'
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223038"
---
# <a name="client-connectivity"></a><span data-ttu-id="73fb7-103">Connettività dei client</span><span class="sxs-lookup"><span data-stu-id="73fb7-103">Client connectivity</span></span>

 <span data-ttu-id="73fb7-104">**Riepilogo:** Illustra la modalità di connessione dei computer client ai tenant di Office 365, in base al percorso del computer client e ai datacenter dei tenant di Office 365.</span><span class="sxs-lookup"><span data-stu-id="73fb7-104">**Summary:** Explains how client computers connect to Office 365 tenants, depending on the location of the client computer and Office 365 tenant datacenter.</span></span>
  
<span data-ttu-id="73fb7-p101">Office 365 si trova in datacenter Microsoft in tutto il mondo che assicurano il servizio di backup e in esecuzione anche quando si verifica un problema importante in un'area, ad esempio un terremoto o un'interruzione dell'alimentazione. Quando si connette al tenant di Office 365, la connessione client verrà indirizzata al datacenter appropriato ospitato tenant. Le regole che determinano dove possono essere ospitati tenant vengono definite dal contratto di licenza Microsoft. Le regole per determinare come il client acquisisce i dati da tale posizione datacenter dipendono l'architettura del servizio che si sta utilizzando.</span><span class="sxs-lookup"><span data-stu-id="73fb7-p101">Office 365 resides in Microsoft datacenters around the world which help keep the service up and running even when there's a major problem in one region, such as an earthquake or a power outage. When you connect to your Office 365 tenant, the client connection will be directed to the appropriate datacenter where your tenant is being hosted. The rules that determine where your tenant can be hosted are defined by your agreement with Microsoft. The rules that determine how your client acquires the data from that datacenter location depend on the architecture of the service you're using.</span></span>
  
<span data-ttu-id="73fb7-p102">Ad esempio, quando accede al portale di Office 365, in genere connessi al datacenter più vicino al client che quindi indirizzata a seconda del servizio che si utilizzano Avanti. Se si avvia posta elettronica, la connessione per visualizzare l'interfaccia utente può comunque provengono da datacenter più vicino, ma potrebbe essere aperta una connessione seconda tra datacenter più vicino e il centro dati dove si trova il tenant per mostrare a cosa si intende nei messaggi di posta elettronica è di lettura. Microsoft opera una delle dieci reti principali del mondo conseguenti estremamente fast datacenter per Data Center connessioni veloci.</span><span class="sxs-lookup"><span data-stu-id="73fb7-p102">For example, when you log on to the Office 365 portal, you're usually connected to the closest datacenter to the client and then directed depending on the service you use next. If you launch email, the initial connection to display the UI may still come from the nearest datacenter, but a second connection might be opened between the nearest datacenter and the datacenter where your tenant is located to show you what's in the emails you read. Microsoft operates one of the top ten networks in the world resulting in incredibly fast datacenter-to-datacenter connections fast.</span></span>
  
<span data-ttu-id="73fb7-112">Dopo aver letto l'articolo, è probabile che saranno comprendere perché Microsoft non fornisce [gli intervalli di indirizzi IP e gli URL di Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) per Data Center, semplicemente sono troppo interconnesse e basati su interagiscono per verificare che il realizzabile.</span><span class="sxs-lookup"><span data-stu-id="73fb7-112">After you read the article, you'll likely understand why we don't provide [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) per datacenter, they are simply too interconnected and reliant on each other to make that feasible.</span></span>
  
<span data-ttu-id="73fb7-p103">Se si utilizza ExpressRoute Azure per Office 365, nella maggior parte dei casi la connettività verrà inoltrate tramite una connessione privata a Office 365 anziché la connessione pubblica descritta di seguito. I principi sulla modalità di connessione client sono ancora precisi. Ulteriori informazioni sulle [ExpressRoute Azure per Office 365](azure-expressroute.md).</span><span class="sxs-lookup"><span data-stu-id="73fb7-p103">If you're using Azure ExpressRoute for Office 365, in most cases your connectivity will go over a private connection to Office 365 instead of the public connection described here. The principles about how clients connect are still accurate. Learn more about [Azure ExpressRoute for Office 365](azure-expressroute.md).</span></span>
  
<span data-ttu-id="73fb7-116">Per ulteriori profondità su Skype per le richieste di rete aziendale, leggere l'articolo [della qualità multimediale e le prestazioni di connettività di rete in Skype Business online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span><span class="sxs-lookup"><span data-stu-id="73fb7-116">For more depth on Skype for Business network requests, read the article [Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span>

||
|:-----|
| <span data-ttu-id="73fb7-117">In questo articolo fa parte della [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="73fb7-117">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

> [!NOTE]
> <span data-ttu-id="73fb7-p104">È necessario prestare attenzione ideale per gestire i dati dei clienti in modo da essere protette e private nei centri dati. Ulteriori informazioni sulla procedura da intraprendere per gestire la privacy vengono inclusi nel [Centro protezione](https://go.microsoft.com/fwlink/?LinkID=397383).</span><span class="sxs-lookup"><span data-stu-id="73fb7-p104">We take great care to manage customer data so it's secure and private in our datacenters. Details about the steps we take to manage privacy are included in the [Trust Center](https://go.microsoft.com/fwlink/?LinkID=397383).</span></span>
  
## <a name="connecting-to-the-nearest-datacenter"></a><span data-ttu-id="73fb7-120">Connessione al datacenter più vicino</span><span class="sxs-lookup"><span data-stu-id="73fb7-120">Connecting to the nearest datacenter</span></span>

<span data-ttu-id="73fb7-p105">Si tratta del tipo di connessione più comune e viene utilizzata per il portale di Office 365 ed Exchange Online. In questo caso, quando i client tentano di connettersi a Office 365, query DNS del proprio computer determina l'area del mondo che proviene il computer e Office 365 reindirizza la richiesta al datacenter più vicino.</span><span class="sxs-lookup"><span data-stu-id="73fb7-p105">This is the most common type of connection, and it's used by both the Office 365 portal and Exchange Online. In this situation, when clients attempt to connect to Office 365, their computer's DNS query determines the region of the world their computer is coming from, and Office 365 redirects the request to the nearest datacenter.</span></span>
  
<span data-ttu-id="73fb7-123">Connessioni al portale di arrestare in datacenter più vicino e il computer client è presentato con informazioni sul tenant del client da tale posizione.</span><span class="sxs-lookup"><span data-stu-id="73fb7-123">Connections to the portal stop at the nearest datacenter, and the client computer is presented with information about the client's tenant from that location.</span></span>
  
<span data-ttu-id="73fb7-p106">Exchange Online va un passaggio. Dopo che il computer client è connesso al datacenter più vicino, un server di Exchange in tale Data Center si connette al datacenter del tenant in cui effettivamente si trova come illustrato nel *in che modo il questo utilizzo sezione* sotto. Il server di Exchange Online nel più vicino datacenter quindi proxy le richieste dal computer client al server cassette postali. Ciò consente di velocizzare l'esperienza per il computer client spostando il pesante di recupero dei messaggi di posta elettronica e gli elementi del calendario di Microsoft network.</span><span class="sxs-lookup"><span data-stu-id="73fb7-p106">Exchange Online goes a step further. Once the client computer is connected to the nearest datacenter, an Exchange server in that datacenter connects to the datacenter where the tenant is actually located as illustrated in the  *How does this work section*  below. The Exchange Online servers in the nearest datacenter then proxy the requests from the client computer to the mailbox server. This speeds up the experience for the client computer by moving the heavy lifting of retrieving emails and calendar items to the Microsoft network.</span></span>
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a><span data-ttu-id="73fb7-128">Funzionamento di offerte standard cloud?</span><span class="sxs-lookup"><span data-stu-id="73fb7-128">How does this work for standard cloud offerings?</span></span>

<span data-ttu-id="73fb7-p107">Questo processo di connessione è standard per un traffico elevato, le applicazioni web di valore elevato come Office 365. In questa sezione è sono riportati e illustrati i passaggi del processo. Quando il computer client non è incluso nella stessa area tenant, la connessione ha un aspetto molto diversa a seconda del servizio a che client si connette.</span><span class="sxs-lookup"><span data-stu-id="73fb7-p107">This connection process is standard for high traffic, high value web applications like Office 365. In this section, we outline and illustrate the steps in the process. When the client computer is not in the same region as the tenant, the connection looks much different depending on the service the client is connecting to.</span></span>
  
 <span data-ttu-id="73fb7-p108">In questo diagramma illustra un cliente utilizzando una soluzione Office 365 standard con un tenant in Nord America. In questo scenario, la persona che effettua la richiesta è stato trasferito per Europa e utilizza Office 365 da tale posizione.</span><span class="sxs-lookup"><span data-stu-id="73fb7-p108">This diagram depicts a customer using a standard Office 365 offering with a tenant in North America. In this scenario, the person making the request has traveled to Europe and is using Office 365 from that location.</span></span>
  
1. <span data-ttu-id="73fb7-134">Il computer client chiede ai server DNS locali per l'indirizzo IP associato a Office 365.</span><span class="sxs-lookup"><span data-stu-id="73fb7-134">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="73fb7-135">Server DNS locali del computer client chiedono ai server DNS Microsoft l'indirizzo IP associato a Office 365.</span><span class="sxs-lookup"><span data-stu-id="73fb7-135">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="73fb7-136">Server DNS Microsoft restituire il nome del server regionali (in base alla posizione dei server DNS del client) e il computer client ripeterà i passaggi da 1 e 2 per ottenere l'indirizzo IP del datacenter internazionale di Office 365.</span><span class="sxs-lookup"><span data-stu-id="73fb7-136">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="73fb7-137">Il computer client si connette all'indirizzo IP del datacenter internazionale.</span><span class="sxs-lookup"><span data-stu-id="73fb7-137">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="73fb7-138">Il server di Exchange Online stabilire una connessione al datacenter attivo dove risiede il tenant del cliente.</span><span class="sxs-lookup"><span data-stu-id="73fb7-138">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![Data center regionale più vicino](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a><span data-ttu-id="73fb7-140">Come questo tipo di lavoro per statali cloud offerte?</span><span class="sxs-lookup"><span data-stu-id="73fb7-140">How does this work for sovereign cloud offerings?</span></span>

<span data-ttu-id="73fb7-p109">La connessione è leggermente diversa per le offerte sovrani cloud quali Office 365 gestito dal Vianet 21. Con il tenant in un'istanza sovrani di Office 365, i server di Office 365 più vicini che accettano connessioni del portale sono i server all'interno dell'area sovrani in cui risiede il tenant. Allo stesso modo, i clienti accesso a SharePoint Online nel nostro cloud sovrani o offerte standard verranno indirizzati ai server front-end in cui risiede il tenant. Vedere la connessione al datacenter attivo riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="73fb7-p109">This connection is slightly different for sovereign cloud offerings such as Office 365 operated by 21 Vianet. With the tenant in a sovereign instance of Office 365, the nearest Office 365 servers that will accept portal connections are the servers within the sovereign region where the tenant resides. Similarly, customers accessing SharePoint Online in our sovereign cloud or standard offerings will be directed to front end servers where the tenant resides. See connecting to the active datacenter below.</span></span>
  
1. <span data-ttu-id="73fb7-145">Il computer client chiede ai server DNS locali per l'indirizzo IP associato a Office 365.</span><span class="sxs-lookup"><span data-stu-id="73fb7-145">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="73fb7-146">Server DNS locali del computer client chiedono ai server DNS Microsoft l'indirizzo IP associato a Office 365.</span><span class="sxs-lookup"><span data-stu-id="73fb7-146">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="73fb7-147">Server DNS Microsoft restituire il nome del server regionali (in base alla posizione dei server DNS del client) e il computer client ripeterà i passaggi da 1 e 2 per ottenere l'indirizzo IP del datacenter internazionale di Office 365.</span><span class="sxs-lookup"><span data-stu-id="73fb7-147">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="73fb7-148">Il computer client si connette all'indirizzo IP del datacenter internazionale.</span><span class="sxs-lookup"><span data-stu-id="73fb7-148">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="73fb7-149">Il server di Exchange Online stabilire una connessione al datacenter attivo dove risiede il tenant del cliente.</span><span class="sxs-lookup"><span data-stu-id="73fb7-149">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![Data center statunitense regionale più vicino](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a><span data-ttu-id="73fb7-151">Connessione al datacenter attivo</span><span class="sxs-lookup"><span data-stu-id="73fb7-151">Connecting to the active datacenter</span></span>

<span data-ttu-id="73fb7-p110">Connessione al datacenter attivo è progettata per pesanti carichi di lavoro dati trasferimento e attualmente utilizzata da SharePoint Online. In questo caso, quando i client tentano di connettersi a Office 365, il browser viene reindirizzato al datacenter attivo per il tenant di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="73fb7-p110">Connecting to the active datacenter is designed for heavier data transfer workloads and is currently used by SharePoint Online. In this situation, when clients attempt to connect to Office 365, their browser is redirected to the active datacenter for their SharePoint Online tenant.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="73fb7-154">Funzionamento.</span><span class="sxs-lookup"><span data-stu-id="73fb7-154">How does this work?</span></span>

<span data-ttu-id="73fb7-p111">Quando il computer client si connette a SharePoint Online da un'area diversa, la connessione è reindirizzata al datacenter di SharePoint Online attivo. In questo scenario si sta utilizzando uno standard che offre, causando la connessioni portale rimanente locali e le connessioni di SharePoint Online viene reindirizzate al datacenter attivo.</span><span class="sxs-lookup"><span data-stu-id="73fb7-p111">When the client computer is connecting to SharePoint Online from a different region, the connection is redirected to the active SharePoint Online datacenter. In this scenario, the customer is using a standard offering, resulting in the portal connections remaining local and the SharePoint Online connections being directed to the active datacenter.</span></span>
  
1. <span data-ttu-id="73fb7-157">Il computer client chiede ai server DNS locali per l'indirizzo IP associato a Office 365.</span><span class="sxs-lookup"><span data-stu-id="73fb7-157">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="73fb7-158">Server DNS locali del computer client chiedono ai server DNS Microsoft l'indirizzo IP associato a Office 365.</span><span class="sxs-lookup"><span data-stu-id="73fb7-158">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="73fb7-159">Server DNS Microsoft restituire il nome del server di datacenter attivo SharePoint Online (in base alla posizione del tenant di Office 365 del client) e il computer client ripeterà i passaggi da 1 e 2 per ottenere l'indirizzo IP del datacenter attivo di Office 365.</span><span class="sxs-lookup"><span data-stu-id="73fb7-159">Microsoft's DNS servers return the server name of the active SharePoint Online datacenter (based on the location of the client's Office 365 tenant), and the client computer repeats steps 1 and 2 to obtain the IP address of the active Office 365 datacenter.</span></span>

4. <span data-ttu-id="73fb7-160">Il computer client si connette all'indirizzo IP del datacenter attivo.</span><span class="sxs-lookup"><span data-stu-id="73fb7-160">The client computer connects to the active datacenter IP address.</span></span>

![Data center statunitense attivo](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a><span data-ttu-id="73fb7-162">Connessione tramite reti virtuali private (VPN)</span><span class="sxs-lookup"><span data-stu-id="73fb7-162">Connecting over Virtual Private Networks (VPNs)</span></span>

<span data-ttu-id="73fb7-p112">Questo tipo di connessione si applica solo quando viene utilizzata una rete privata virtuale (VPN) dai computer client. In realtà, il comportamento di Office 365 non viene modificato semplicemente poiché viene utilizzata una rete VPN, ma le reti private virtuali comunemente utilizzate per controllare come computer client stabilire connessioni a Office 365 e, in genere, i risultati in un'esperienza di degradazione, pertanto, è importante specifichi.</span><span class="sxs-lookup"><span data-stu-id="73fb7-p112">This type of connection applies only when a virtual private network (VPN) is used by client computers. In reality, Office 365 behavior isn't changed simply because a VPN is used, but VPNs are commonly used to control how client computers establish connections to Office 365 and usually results in a degraded experience, so it's important to cover.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="73fb7-165">Funzionamento.</span><span class="sxs-lookup"><span data-stu-id="73fb7-165">How does this work?</span></span>

<span data-ttu-id="73fb7-p113">Quando il computer client stabilisce una connessione VPN alla sede in un'area diversa, vengono utilizzati i server DNS in tale office anziché ai server DNS nella posizione del computer client. Nella maggior parte dei casi, la connessione tramite VPN aggiuntiva comporta un peggioramento l'esperienza di Office 365. I servizi di Office 365 sono ottimizzati per connessioni del servizio clienti come raggiungere l'utente finale possibile. Molti servizi di sfruttano la rete perimetrale Azure, reti di distribuzione del contenuto e la capacità di rete affidabile Microsoft Network per offrire un'esperienza utente ottimale quando vengono effettuate le richieste di rete di servizi di Office 365 più vicino al computer client possibile.</span><span class="sxs-lookup"><span data-stu-id="73fb7-p113">When the client computer establishes a VPN connection to a corporate office in a different region, the DNS servers at that office are used instead of the DNS servers at the client computer's location. In most cases, this extra connection over the VPN will degrade the Office 365 experience. The Office 365 services are optimized to service customer connections as close to the end user as possible. Many services leverage the Azure edge network, Content Delivery Networks, and the reliable network capacity on the Microsoft network to deliver the best possible user experience when network requests for Office 365 services are made as close to the client computer as possible.</span></span>
  
1. <span data-ttu-id="73fb7-170">Il computer client chiede DNS VPN server per l'indirizzo IP associato a Office 365.</span><span class="sxs-lookup"><span data-stu-id="73fb7-170">The client computer asks the VPN DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="73fb7-171">Server DNS VPN del computer client chiedono ai server DNS Microsoft l'indirizzo IP associato a Office 365.</span><span class="sxs-lookup"><span data-stu-id="73fb7-171">The client computer's VPN DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="73fb7-172">Server DNS Microsoft restituire il nome del server regionali (in base alla posizione dei server DNS VPN) e il computer client ripeterà i passaggi da 1 e 2 per ottenere le informazioni sull'indirizzo IP del datacenter internazionale di Office 365.</span><span class="sxs-lookup"><span data-stu-id="73fb7-172">Microsoft's DNS servers return the regional server name (based on the location of the VPN DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address information of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="73fb7-173">Il computer client si connette al datacenter indirizzo IP che è più vicino all'ufficio aziendale con che cui ha stabilito una connessione.</span><span class="sxs-lookup"><span data-stu-id="73fb7-173">The client computer connects to the datacenter IP address that's closest to the corporate office they established a VPN connection with.</span></span>

![Connettività data center VPN](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
<span data-ttu-id="73fb7-175">Questo è un collegamento breve che è possibile utilizzare il ritorno:[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span><span class="sxs-lookup"><span data-stu-id="73fb7-175">Here's a short link you can use to come back: [https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="73fb7-176">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="73fb7-176">See also</span></span>

[<span data-ttu-id="73fb7-177">Gestione di endpoint di Office 365</span><span class="sxs-lookup"><span data-stu-id="73fb7-177">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="73fb7-178">Connettività di rete con Office 365</span><span class="sxs-lookup"><span data-stu-id="73fb7-178">Network connectivity to Office 365</span></span>](network-connectivity.md)
