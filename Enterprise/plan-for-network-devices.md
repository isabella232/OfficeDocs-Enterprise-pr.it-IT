---
title: Pianificazione dei dispositivi di rete che si connettono ai servizi di Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 'Riepilogo: vengono illustrate alcune considerazioni relative alla capacità della rete, agli acceleratori WAN e ai dispositivi di bilanciamento del carico utilizzati per la connessione a Office 365.'
ms.openlocfilehash: 023eb3f5ed4d81d1d49d18c69ef8c81032fd5851
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933123"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a><span data-ttu-id="5bb63-103">Pianificazione dei dispositivi di rete che si connettono ai servizi di Office 365</span><span class="sxs-lookup"><span data-stu-id="5bb63-103">Plan for network devices that connect to Office 365 services</span></span>

 <span data-ttu-id="5bb63-104">**Riepilogo**: vengono illustrate alcune considerazioni relative alla capacità della rete, agli acceleratori WAN e ai dispositivi di bilanciamento del carico utilizzati per la connessione a Office 365.</span><span class="sxs-lookup"><span data-stu-id="5bb63-104">**Summary**: Describes considerations for network capacity, WAN accelerators, and load balancing devices that are used to connect to Office 365.</span></span>
  
<span data-ttu-id="5bb63-p101">Alcuni componenti hardware di rete potrebbe essere limitazioni al numero di sessioni simultanee supportate. Per le organizzazioni con più di 2.000 utenti, è consigliabile che controllano i dispositivi di rete per verificare che siano in grado di gestire il traffico di servizio aggiuntivo di Office 365. SNMP Simple Network Management Protocol () software di monitoraggio consentono di eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="5bb63-p101">Some network hardware may have limitations on the number of concurrent sessions that are supported. For organizations having more than 2,000 users, we recommend that they monitor their network devices to ensure they are capable of handling the additional Office 365 service traffic. Simple Network Management Protocol (SNMP) monitoring software can help you do this.</span></span>

||
|:-----|
| <span data-ttu-id="5bb63-108">In questo articolo fa parte della [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="5bb63-108">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

<span data-ttu-id="5bb63-p102">Locale in uscita le impostazioni del proxy Internet anche influire sulla connettività ai servizi di Office 365 per le applicazioni client. È inoltre necessario configurare i dispositivi proxy di rete per consentire le connessioni per gli URL di servizi cloud Microsoft e le applicazioni. Ogni organizzazione è diversa. Per avere un'idea per la modalità di gestione di questo processo e la quantità di larghezza di banda in Microsoft si effettua il provisioning, [leggere il case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span><span class="sxs-lookup"><span data-stu-id="5bb63-p102">On-premises outgoing Internet proxy settings also affect connectivity to Office 365 services for your client applications. You must also configure your network proxy devices to allow connections for Microsoft cloud services URLs and applications. Every organization is different. To get an idea for how Microsoft manages this process and the amount of bandwidth we provision, [read the case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span></span>
  
<span data-ttu-id="5bb63-113">Skype seguenti per la Guida di Business contiene ulteriori informazioni sulle Skype per le impostazioni di Business:</span><span class="sxs-lookup"><span data-stu-id="5bb63-113">The following Skype for Business Help articles have more information about Skype for Business settings:</span></span>
  
- [<span data-ttu-id="5bb63-114">Risoluzione dei problemi Skype per errori di accesso Business Online per amministratori</span><span class="sxs-lookup"><span data-stu-id="5bb63-114">Troubleshooting Skype for Business Online sign-in errors for administrators</span></span>](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [<span data-ttu-id="5bb63-115">È possibile connettersi a Skype per le aziende o per alcune caratteristiche non funzionano, poiché un firewall locale blocca la connessione</span><span class="sxs-lookup"><span data-stu-id="5bb63-115">You cannot connect to Skype for Business, or certain features do not work, because an on-premises firewall blocks the connection</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> <span data-ttu-id="5bb63-116">Anche se molte di queste impostazioni sono Skype per aziendali specifici, le informazioni generali sulla configurazione di rete sono utili per tutti i servizi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="5bb63-116">While many of these settings are Skype for Business-specific, the general guidance on network configuration is useful for all Office 365 services.</span></span>
  
## <a name="determining-network-capacity"></a><span data-ttu-id="5bb63-117">Calcolo della capacità della rete</span><span class="sxs-lookup"><span data-stu-id="5bb63-117">Determining Network Capacity</span></span>

<span data-ttu-id="5bb63-p103">Ogni dispositivo esistente sulla rete ha un limite di capacità. Questo vale per i client e server di rete nonché per le schede, i router, i commutatori e gli hub che li interconnettono. Avere una capacità di rete adeguata significa che nessuno di questi dispositivi di rete è giunto al punto di saturazione. Monitorare l'attività di rete è essenziale per garantire che i carichi effettivi su tutti i dispositivi di rete non superino la capacità massima. La capacità della rete influenza le prestazioni del dispositivo proxy.</span><span class="sxs-lookup"><span data-stu-id="5bb63-p103">Every network device that exists on a connection has its capacity limit. These devices include the client and server network adapters, routers, switches, and hubs that interconnect them. Adequate network capacity means that none of them are saturated. Monitoring network activity is essential to help ensure that the actual loads on all network devices are less than their maximum capacity. Network capacity affects proxy device performance.</span></span>
  
<span data-ttu-id="5bb63-p104">Nella maggior parte dei casi, della larghezza di banda Internet imposta il limite per la quantità di traffico. Le prestazioni debole durante le ore di punta traffico potrebbe essere dovuta a utilizzo eccessivo del collegamento Internet. Questa situazione si applica anche a filiali, branch office proxy server computer connessi al dispositivo proxy in sede della succursale su collegamenti lenti rete WAN (Wide Area).</span><span class="sxs-lookup"><span data-stu-id="5bb63-p104">In most situations, the Internet connection bandwidth sets the limit for the amount of traffic. Weak performance during peak traffic hours is probably caused by excessive use of the Internet link. This situation also applies to a branch office scenario, where branch office proxy server computers are connected to the proxy device at the branch's headquarters over a slow Wide Area Network (WAN) link.</span></span>
  
<span data-ttu-id="5bb63-p105">Per testare la capacità di rete, monitorare l'attività di rete nell'interfaccia di rete proxy. Se è superiore al 75% della larghezza di banda massima di un'interfaccia di rete, è consigliabile aumentare la larghezza di banda dell'infrastruttura di rete che non è sufficiente. In alternativa, è consigliabile utilizzare funzionalità avanzate, ad esempio la compressione HTTP.</span><span class="sxs-lookup"><span data-stu-id="5bb63-p105">To test network capacity, monitor the network activity on the proxy network interface. If it's more than 75 percent of the maximum bandwidth of any network interface, consider increasing the bandwidth of the network infrastructure that's inadequate. Or, consider using advanced features, such as HTTP compression.</span></span>
  
## <a name="wan-accelerators"></a><span data-ttu-id="5bb63-129">Acceleratori WAN</span><span class="sxs-lookup"><span data-stu-id="5bb63-129">WAN Accelerators</span></span>

<span data-ttu-id="5bb63-p106">Se l'organizzazione utilizza accessori proxy accelerazione di rete WAN WAN, possono verificarsi problemi quando per accedere ai servizi di Office 365. Potrebbe essere necessario ottimizzare la rete o dispositivi per assicurarsi che gli utenti abbiano un'esperienza coerente quando si accede a Office 365. Ad esempio servizi di Office 365 crittografare alcuni contenuti di Office 365 e l'intestazione TCP. Il dispositivo potrebbe non essere in grado di gestire questo tipo di traffico.</span><span class="sxs-lookup"><span data-stu-id="5bb63-p106">If your organization uses wide area network (WAN) acceleration proxy appliances, you may encounter issues when you access the Office 365 services. You may need to optimize your network device or devices to ensure that your users have a consistent experience when accessing Office 365. For example, Office 365 services encrypt some Office 365 content and the TCP header. Your device may not be able to handle this kind of traffic.</span></span>
  
<span data-ttu-id="5bb63-134">Leggere l'informativa supporto [sull'utilizzo di Controller di ottimizzazione della WAN o dispositivi traffico/ispezione con Office 365](https://support.microsoft.com/kb/2690045).</span><span class="sxs-lookup"><span data-stu-id="5bb63-134">Read our support statement about [Using WAN Optimization Controller or Traffic/Inspection devices with Office 365](https://support.microsoft.com/kb/2690045).</span></span>
  
## <a name="hardware-and-software-load-balancing-devices"></a><span data-ttu-id="5bb63-135">Soluzioni hardware e software per il bilanciamento del carico</span><span class="sxs-lookup"><span data-stu-id="5bb63-135">Hardware and Software Load-balancing Devices</span></span>

<span data-ttu-id="5bb63-p107">Nell'organizzazione sarà necessario utilizzare un dispositivo di bilanciamento del carico hardware (HLB) o una soluzione di bilanciamento del carico (Network Load Balancing, NLB) per distribuire le richieste ai server Active Directory Federation Services (AD FS) e/o ai server ibridi di Exchange. I dispositivi di bilanciamento del carico controllano il traffico di rete verso i server locali. Tali server sono fondamentali per garantire la disponibilità di Single Sign-On e delle distribuzioni ibride di Exchange.</span><span class="sxs-lookup"><span data-stu-id="5bb63-p107">Your organization needs to use a hardware load balancer (HLB) or a Network Load Balancing (NLB) solution to distribute requests to your Active Directory Federation Services (AD FS) servers and/or your Exchange hybrid servers. Load-balancing devices control the network traffic to the on-premises servers. These servers are crucial in helping to ensure the availability of single sign-on and Exchange hybrid deployment.</span></span>
  
<span data-ttu-id="5bb63-p108">Offriamo una soluzione di bilanciamento carico di rete basato su software integrata in Windows Server. Office 365 supporta questa soluzione per raggiungere il bilanciamento del carico.</span><span class="sxs-lookup"><span data-stu-id="5bb63-p108">We provide a software-based NLB solution built into Windows Server. Office 365 supports this solution to achieve load balancing.</span></span>
  
## <a name="firewalls-and-proxies"></a><span data-ttu-id="5bb63-141">Firewall e proxy</span><span class="sxs-lookup"><span data-stu-id="5bb63-141">Firewalls and proxies</span></span>

<span data-ttu-id="5bb63-142">Per ulteriori informazioni sulla configurazione dei firewall e i proxy per la connessione a Office 365, leggere [gli endpoint di gestione di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [la connettività di rete per Office 365](network-connectivity.md)e [gli endpoint di Office 365 domande frequenti](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) per ulteriori informazioni sui dispositivi e selezione a commutazione di circuito.</span><span class="sxs-lookup"><span data-stu-id="5bb63-142">For more details on configuring firewalls and proxies to connect to Office 365, read [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Network connectivity to Office 365](network-connectivity.md), and [Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) to learn more about devices and circuit selection.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5bb63-143">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5bb63-143">See also</span></span>

[<span data-ttu-id="5bb63-144">Assistenti distribuzione per i servizi di Office 365</span><span class="sxs-lookup"><span data-stu-id="5bb63-144">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
