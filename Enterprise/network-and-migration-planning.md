---
title: Pianificazione della rete e della migrazione per Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Contiene collegamenti a informazioni sulla pianificazione della rete e il testing e la migrazione a Office 365.
ms.openlocfilehash: e2434a65b48c12f38d7371a569ba8e0bc282ae06
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223058"
---
# <a name="network-and-migration-planning-for-office-365"></a><span data-ttu-id="fc79a-103">Pianificazione della rete e della migrazione per Office 365</span><span class="sxs-lookup"><span data-stu-id="fc79a-103">Network and migration planning for Office 365</span></span>

<span data-ttu-id="fc79a-104">In questo articolo contiene collegamenti a informazioni sulla pianificazione e test di rete e la migrazione a Office 365.</span><span class="sxs-lookup"><span data-stu-id="fc79a-104">This article contains links to information about network planning and testing, and migration to Office 365.</span></span>
  
<span data-ttu-id="fc79a-105">Prima di eseguire la distribuzione o la migrazione per la prima volta in Office 365, è possibile utilizzare le informazioni in questi argomenti per stimare la larghezza di banda necessaria, per poi testare e verificare di disporre di larghezza di banda sufficiente per distribuire o migrare in Office 365.</span><span class="sxs-lookup"><span data-stu-id="fc79a-105">Before you deploy for the first time or migrate to Office 365, you can use the information in these topics to estimate the bandwidth you need and then to test and verify that you have enough bandwidth to deploy or migrate to Office 365.</span></span>

||
|:-----|
| <span data-ttu-id="fc79a-106">In questo articolo fa parte della [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="fc79a-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

|||
|:-----|:-----|
|![Vedere Cloud Microsoft Networking per poster architetti Enterprise](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|<span data-ttu-id="fc79a-108">Per le procedure ottimizzare la rete per Office 365 e altre piattaforme Microsoft cloud e servizi, vedere il poster [Microsoft Cloud di rete per architetti Enterprise](https://aka.ms/cloudarchnetworking) .</span><span class="sxs-lookup"><span data-stu-id="fc79a-108">For the steps to optimize your network for Office 365 and other Microsoft cloud platforms and services, see the [Microsoft Cloud Networking for Enterprise Architects](https://aka.ms/cloudarchnetworking) poster.</span></span> |
   
## <a name="estimate-network-bandwidth-requirements"></a><span data-ttu-id="fc79a-109">Stimare i requisiti di larghezza di banda di rete</span><span class="sxs-lookup"><span data-stu-id="fc79a-109">Estimate network bandwidth requirements</span></span>
<span data-ttu-id="fc79a-110"><a name="EstimateBandwidthRequirements"> </a></span><span class="sxs-lookup"><span data-stu-id="fc79a-110"></span></span>

<span data-ttu-id="fc79a-p101">Utilizzo di Office 365 può aumentare l'utilizzo di circuito internet dell'organizzazione. È importante determinare se la quantità di larghezza di banda disponibile attualmente è sufficiente per gestire l'aumento stimato dopo aver distribuito Office 365 lasciando almeno 20% della capacità di gestire più occupata dei giorni.</span><span class="sxs-lookup"><span data-stu-id="fc79a-p101">Using Office 365 may increase the utilization of your organization's internet circuit. It's important to determine if the amount of bandwidth currently available is enough to handle the estimated increase once Office 365 is fully deployed while leaving at least 20% capacity to handle the busiest of days.</span></span>
  
<span data-ttu-id="fc79a-113">Per calcolare la larghezza di banda, utilizzare la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="fc79a-113">To estimate the bandwidth, use the following steps:</span></span>
  
1. <span data-ttu-id="fc79a-p102">Valutare il numero di client che verrà utilizzata ogni uscita Internet. Consentono di gestire le informazioni sulla connessione possibile la nostra rete terabit al multi.</span><span class="sxs-lookup"><span data-stu-id="fc79a-p102">Assess the number of clients that will use each Internet egress. Let our multi-terabit network handle as much of the connection as possible.</span></span> 
    
2. <span data-ttu-id="fc79a-p103">Determinare i servizi di Office 365 e le funzionalità saranno disponibili per i client da utilizzare. Sarà probabilmente necessario gruppi di utenti con diversi servizi o i profili di utilizzo.</span><span class="sxs-lookup"><span data-stu-id="fc79a-p103">Determine which Office 365 services and features will be available for clients to use. You will likely have groups of people with different services or usage profiles.</span></span>
    
3. <span data-ttu-id="fc79a-p104">Misurare l'utilizzo di rete per un gruppo pilota dei client. Verificare i client pilota rappresentante dei profili diversi di utenti nell'organizzazione, nonché le posizioni geografiche diverse. È possibile cross-controllo i risultati con i vecchi calcolatori per [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)e [Skype per le aziende](https://go.microsoft.com/fwlink/p/?LinkId=321551) o [case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) che viene eseguite la propria rete.</span><span class="sxs-lookup"><span data-stu-id="fc79a-p104">Measure the network use for a pilot group of clients. Ensure the pilot clients are representative of the different profiles of people in the organization as well as the different geographic locations. You can cross-check your results against our old calculators for [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)and [Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=321551) or the [case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) we performed on our own network.</span></span> 
    
4. <span data-ttu-id="fc79a-121">Utilizzare le misure dal gruppo pilota estrapolare alle esigenze dell'intera organizzazione e nuovamente test per convalidare le stime prima di apportare modifiche alla rete.</span><span class="sxs-lookup"><span data-stu-id="fc79a-121">Use the measurements from the pilot group to extrapolate the entire organization's needs and re-test to validate the estimations before making any changes to your network.</span></span>
    
## <a name="test-your-existing-network"></a><span data-ttu-id="fc79a-122">Test della rete esistente</span><span class="sxs-lookup"><span data-stu-id="fc79a-122">Test your existing network</span></span>
<span data-ttu-id="fc79a-123"><a name="calculators"> </a></span><span class="sxs-lookup"><span data-stu-id="fc79a-123"></span></span>

 <span data-ttu-id="fc79a-p105">**Strumenti di rete.** Testare e convalidare la larghezza di banda Internet per determinare il download, caricamento e latenza dei vincoli. Questi strumenti consentono di determinare le funzionalità della rete per la migrazione e dopo che ha completato la distribuzione.</span><span class="sxs-lookup"><span data-stu-id="fc79a-p105">**Network tools.** Test and validate your Internet bandwidth to determine download, upload, and latency constraints. These tools will help you determine the capabilities of your network for migration as well as after you're fully deployed.</span></span> 
  
- <span data-ttu-id="fc79a-p106">[Microsoft messaggio Analyzer](https://technet.microsoft.com/library/jj649776.aspx): messaggio Analyzer è uno strumento efficace per la risoluzione dei problemi di rete. Messaggio Analyzer acquisisce, viene visualizzato e consente di analizzare il traffico di messaggistica basato su protocollo e messaggi di sistema. Messaggio Analyzer consente inoltre di importare, aggregare e analizzare i dati dai file di registro e di traccia.</span><span class="sxs-lookup"><span data-stu-id="fc79a-p106">[Microsoft Message Analyzer](https://technet.microsoft.com/library/jj649776.aspx): Message Analyzer is an effective tool for troubleshooting network issues. Message Analyzer captures, displays, and analyzes protocol-based messaging traffic and system messages. Message Analyzer also lets you import, aggregate, and analyze data from log and trace files.</span></span>
    
- <span data-ttu-id="fc79a-130">[Analizzatore connettività remota di Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=517243): verificata la connettività nell'ambiente Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="fc79a-130">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Tests connectivity in your Exchange Online environment.</span></span>
    
- <span data-ttu-id="fc79a-131">Utilizzare l' [Assistente di ripristino per Office 365 e supporto tecnico clienti Microsoft](https://diagnostics.office.com/#/Download?env=SOC) per risolvere i problemi di Outlook e Office 365.</span><span class="sxs-lookup"><span data-stu-id="fc79a-131">Use the [Microsoft Support and Recovery Assistant for Office 365](https://diagnostics.office.com/#/Download?env=SOC) to fix Outlook and Office 365 problems.</span></span> 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a><span data-ttu-id="fc79a-132">Best practices for network planning and improving migration performance for Office 365</span><span class="sxs-lookup"><span data-stu-id="fc79a-132">Best practices for network planning and improving migration performance for Office 365</span></span>
<span data-ttu-id="fc79a-133"><a name="BestPractices"> </a></span><span class="sxs-lookup"><span data-stu-id="fc79a-133"></span></span>

<span data-ttu-id="fc79a-134">Approfondire in queste procedure consigliate per ulteriori informazioni su come migliorare l'esperienza di Office 365.</span><span class="sxs-lookup"><span data-stu-id="fc79a-134">Dig a little deeper into these best practices for more information about improving your Office 365 experience.</span></span>
  
1. <span data-ttu-id="fc79a-p107">Se si desidera iniziare a come consentire agli utenti subito? Per suggerimenti sull'utilizzo di Office 365, tra cui SharePoint Online, Exchange Online e Lync Online, la rete non è semplicemente collaborazione, vedere [procedure consigliate per l'utilizzo di Office 365 con reti lente](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) . In questo articolo viene collegato alle carichi di contenuto su TechNet e Support.office.com fuori per ottimizzare l'esperienza di Office 365 e sono incluse informazioni su modi semplici per personalizzare le pagine web e su come configurare le impostazioni di Internet Explorer per un'esperienza ottimale di Office 365.</span><span class="sxs-lookup"><span data-stu-id="fc79a-p107">Want to get started helping your users right away? See [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) for tips on using Office 365, including SharePoint Online, Exchange Online, and Lync Online, when your network just isn't cooperating. This article links out to loads of content on TechNet and Support.office.com for optimizing your Office 365 experience and includes information on easy ways to customize your web pages and how to set your Internet Explorer settings for the best Office 365 experience.</span></span> 
    
2. <span data-ttu-id="fc79a-p108">Leggere i [Principi di connettività di rete di Office 365](https://aka.ms/o365networkingprinciples) per comprendere i principi di connettività per la gestione del traffico di Office 365 in modo sicuro e ottenere prestazioni ottimali. In questo articolo consentono di acquisire familiarità con le indicazioni più recenti per l'ottimizzazione in modo sicuro la connettività di rete di Office 365.</span><span class="sxs-lookup"><span data-stu-id="fc79a-p108">Read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance. This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span> 
    
3. <span data-ttu-id="fc79a-p109">Migliorare le prestazioni di migrazione della posta gestendo con attenzione la pianificazione per gli aggiornamenti di Windows. È possibile aggiornare i computer client in batch e verificare che tutti i computer client vengono aggiornati prima della migrazione a Office 365 per definire quali l'utilizzo della larghezza di banda di rete. Per ulteriori informazioni, vedere [manualmente l'aggiornamento e configurazione manuale dei desktop per Office 365 per gli aggiornamenti più recenti](https://support.microsoft.com/gp/office-2013-365-update).</span><span class="sxs-lookup"><span data-stu-id="fc79a-p109">Improve mail migration performance by carefully managing the schedule for Windows Updates. You can update your client computers in batches and ensure that all client computers are updated before migrating to Office 365 to regulate the use of network bandwidth. For more information, see [Manually update and configure desktops for Office 365 for the latest updates](https://support.microsoft.com/gp/office-2013-365-update).</span></span>
    
4. <span data-ttu-id="fc79a-p110">Il traffico di rete di Office 365 offre le prestazioni migliori quando è considerato come un servizio Internet attendibile e consentiti per ignorare la maggior parte del filtro tradizionali e analisi che alcune organizzazioni archiviare il traffico di rete di servizi Internet non attendibili. In genere include la rimozione in uscita, ad esempio l'autenticazione utente proxy e controllo dei pacchetti di elaborazione, nonché verifica uscita locale su Internet con corretto Network Address Translation (NAT) e sufficiente capacità della larghezza di banda per gestire l'aumento richieste di rete. Per ulteriori informazioni sulla configurazione della rete per gestire Office 365 come servizio Internet attendibile della rete, fare riferimento agli [endpoint di gestione di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).</span><span class="sxs-lookup"><span data-stu-id="fc79a-p110">Office 365 network traffic performs best when it's treated as a trusted Internet service and allowed to bypass much of the traditional filtering and scanning that some organizations place on network traffic to untrusted Internet services. This typically includes removing outbound processing such as proxy user authentication and packet inspection, as well as ensuring local egress to the Internet with the proper Network Address Translation (NAT) and enough bandwidth capacity to handle the increased network requests. Refer to [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)for additional guidance on configuring your network to handle Office 365 as a trusted Internet service on your network.</span></span>
    
1. <span data-ttu-id="fc79a-p111">Verificare che [gli endpoint di gestione di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). Il traffico aggiuntivo continui a Office 365 comporta un aumento delle connessioni in uscita proxy, nonché un aumento del traffico protetto tramite TLS/SSL.</span><span class="sxs-lookup"><span data-stu-id="fc79a-p111">Ensure [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). The additional traffic going to Office 365 results in an increase of outbound proxy connections as well as an increase in secure traffic over TLS/SSL.</span></span>
    
2. <span data-ttu-id="fc79a-p112">Se il proxy in uscita richiede l'autenticazione degli utenti che si verifichi una perdita di funzionalità o la connettività lenta. Ignorare il requisito di autenticazione per i domini di Office 365 per ridurre il sovraccarico.</span><span class="sxs-lookup"><span data-stu-id="fc79a-p112">If your outbound proxies require user authentication you may experience slow connectivity or a loss of functionality. Bypassing the authentication requirement for the Office 365 domains can reduce this overhead.</span></span>
    
3. <span data-ttu-id="fc79a-p113">Se il numero di calendari e cassette postali condivisi è elevato, è possibile che si verifichi un aumento del numero di connessioni da Outlook a Exchange. Ad esempio, il client Outlook potrebbe aprirsi a due connessioni aggiuntive per ciascun calendario condiviso in uso. In tal caso, verificare che il proxy in uscita sia in grado di gestire le connessioni oppure escludere il proxy per le connessioni a Office 365 relative a Outlook.</span><span class="sxs-lookup"><span data-stu-id="fc79a-p113">If you have a large number of shared calendars and mailboxes, you may see an increase in the number of connections from Outlook to Exchange. For instance, the Outlook client may open up to two additional connections for each shared calendar in use. In this situation, ensure that the egress proxy can handle the connections, or bypass the proxy for connections to Office 365 for Outlook.</span></span>
    
4. <span data-ttu-id="fc79a-p114">Determinare il numero massimo di dispositivi supportati per un indirizzo IP pubblico e come bilanciare il carico tra più indirizzi IP. Per ulteriori informazioni, vedere [supporto di NAT con Office 365](nat-support-with-office-365.md).</span><span class="sxs-lookup"><span data-stu-id="fc79a-p114">Determine the maximum number of supported devices for a public IP address and how to load balance across multiple IP addresses. For more information, see [NAT support with Office 365](nat-support-with-office-365.md).</span></span>
    
5. <span data-ttu-id="fc79a-p115">Se si sta controllare le connessioni in uscita dal computer nella rete, ignorare questo filtro per i domini di Office 365 migliorare la connettività e le prestazioni. Inoltre, ignorando spesso l'ispezione in uscita consente di rimuovere la necessità di un singolo uscita Internet e consente locale uscita Internet per le richieste di rete di Office 365 destinate a.</span><span class="sxs-lookup"><span data-stu-id="fc79a-p115">If you're inspecting outbound connections from computers on your network, bypassing this filtering to the Office 365 domains will improve connectivity and performance. Additionally, bypassing outbound inspection often removes the need for a single Internet egress and enables local Internet egress for Office 365 destined network requests.</span></span>
    
6. <span data-ttu-id="fc79a-p116">Alcuni clienti trovare le impostazioni di rete interna possono influire sulle prestazioni. Impostazioni, ad esempio dimensione unità (Maximum Transmission Unit) di trasmissione massima, in rete la negoziazione automatica o il rilevamento automatico e route ottimale per Internet sono aree comuni da cercare.</span><span class="sxs-lookup"><span data-stu-id="fc79a-p116">Some customers find internal network settings may affect performance. Settings such as maximum transmission unit (MTU) size, network auto-negotiation or auto-detection, and sub-optimal routes to the Internet are common places to look.</span></span>
    
## <a name="network-planning-reference-for-office-365"></a><span data-ttu-id="fc79a-159">Riferimenti per la pianificazione della rete per Office 365</span><span class="sxs-lookup"><span data-stu-id="fc79a-159">Network planning reference for Office 365</span></span>
<span data-ttu-id="fc79a-160"><a name="NetReference"> </a></span><span class="sxs-lookup"><span data-stu-id="fc79a-160"></span></span>

<span data-ttu-id="fc79a-161">In questi argomenti contengono informazioni dettagliate sulla informazioni di riferimento di rete di Office 365.</span><span class="sxs-lookup"><span data-stu-id="fc79a-161">These topics contain detailed Office 365 network reference information.</span></span>
  
- [<span data-ttu-id="fc79a-162">Gestione di endpoint di Office 365</span><span class="sxs-lookup"><span data-stu-id="fc79a-162">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [<span data-ttu-id="fc79a-163">Connettività client</span><span class="sxs-lookup"><span data-stu-id="fc79a-163">Client connectivity</span></span>](client-connectivity.md)
    
- [<span data-ttu-id="fc79a-164">Reti per la distribuzione di contenuti</span><span class="sxs-lookup"><span data-stu-id="fc79a-164">Content delivery networks</span></span>](content-delivery-networks.md)
    
- [<span data-ttu-id="fc79a-165">Record esterno (Domain Name System) per Office 365</span><span class="sxs-lookup"><span data-stu-id="fc79a-165">External Domain Name System records for Office 365</span></span>](external-domain-name-system-records.md)
    
- [<span data-ttu-id="fc79a-166">Supporto IPv6 nei servizi Office 365</span><span class="sxs-lookup"><span data-stu-id="fc79a-166">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
    
- [<span data-ttu-id="fc79a-167">Principi della connettività di rete di Office 365</span><span class="sxs-lookup"><span data-stu-id="fc79a-167">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
    
- [<span data-ttu-id="fc79a-168">Microsoft Virtual Academy: Gestione delle prestazioni Office 365</span><span class="sxs-lookup"><span data-stu-id="fc79a-168">Microsoft Virtual Academy: Office 365 Performance Management</span></span>](https://mva.microsoft.com/en-us/training-courses/office-365-performance-management-8416)
    
- [<span data-ttu-id="fc79a-169">Rete video di Office 365 domande frequenti (FAQ)</span><span class="sxs-lookup"><span data-stu-id="fc79a-169">Office 365 video networking Frequently Asked Questions (FAQ)</span></span>](office-365-video-networking-faq.md)
    
- [<span data-ttu-id="fc79a-170">Pianificare per i dispositivi di rete che si connettono ai servizi di Office 365</span><span class="sxs-lookup"><span data-stu-id="fc79a-170">Plan for network devices that connect to Office 365 services</span></span>](plan-for-network-devices.md)
    
- [<span data-ttu-id="fc79a-171">Assistenti distribuzione per i servizi di Office 365</span><span class="sxs-lookup"><span data-stu-id="fc79a-171">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
    

