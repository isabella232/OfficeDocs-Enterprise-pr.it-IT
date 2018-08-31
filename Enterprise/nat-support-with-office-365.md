---
title: Supporto di NAT con Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: "Riepilogo: In questo articolo vengono fornite informazioni dettagliate su come calcolare il numero approssimativo di client che è possibile utilizzare per ciascun indirizzo IP all'interno dell'organizzazione utilizzando NAT (Network Address Translation)."
ms.openlocfilehash: 733d591bded599cfaece988a624baa7a3c0d4b06
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541100"
---
# <a name="nat-support-with-office-365"></a><span data-ttu-id="75e86-103">Supporto di NAT con Office 365</span><span class="sxs-lookup"><span data-stu-id="75e86-103">NAT support with Office 365</span></span>

 <span data-ttu-id="75e86-104">**Riepilogo:** In questo articolo vengono fornite informazioni dettagliate su come calcolare il numero approssimativo di client che è possibile utilizzare per ciascun indirizzo IP all'interno dell'organizzazione utilizzando NAT (Network Address Translation).</span><span class="sxs-lookup"><span data-stu-id="75e86-104">**Summary:** Provides details about how to approximate the correct number of clients you can use per IP address within your organization using Network Address Translation (NAT).</span></span> 
  
<span data-ttu-id="75e86-105">Indicazioni suggerito in precedenza, che il numero massimo di client di Exchange per ogni indirizzo IP da utilizzare per connettersi a Office 365 è stata client circa 2.000 per porta di rete.</span><span class="sxs-lookup"><span data-stu-id="75e86-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="75e86-106">Perché utilizzare NAT?</span><span class="sxs-lookup"><span data-stu-id="75e86-106">Why use NAT?</span></span>

<span data-ttu-id="75e86-107">Tramite NAT migliaia di persone in una rete aziendale può "condividere" pochi indirizzi IP instradabili pubblicamente.</span><span class="sxs-lookup"><span data-stu-id="75e86-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="75e86-p101">La maggior parte delle reti aziendali utilizza spazio degli indirizzi IP privato (RFC1918). Lo spazio degli indirizzi IP privato viene assegnato dalla Internet Assigned Numbers Authority (IANA) ed è destinato esclusivamente alle reti che non indirizzano direttamente a e da Internet globale.</span><span class="sxs-lookup"><span data-stu-id="75e86-p101">Most corporate networks use private (RFC1918) IP address space. Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="75e86-p102">Per fornire l'accesso a Internet per i dispositivi in uno spazio di indirizzi IP privato, le organizzazioni utilizzare tecnologie gateway come firewall e proxy che forniscono (NAT) network address translation o porta address translation (PAT) servizi. Questi gateway verificare il traffico dall'interno ai dispositivi di Internet (tra Office 365) sembrano provenire da uno o più indirizzi IP instradabili pubblicamente. Ogni connessione in uscita dal dispositivo interno viene convertita in una porta TCP origine diversa l'indirizzo IP pubblico.</span><span class="sxs-lookup"><span data-stu-id="75e86-p102">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services. These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses. Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="75e86-113">Perché è necessario presenti numerose eccessivo di connessioni aperte a Office 365 contemporaneamente?</span><span class="sxs-lookup"><span data-stu-id="75e86-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="75e86-p103">Outlook potrebbe aprire otto o più connessioni (in situazioni dove sono presenti componenti aggiuntivi, calendari condivisi, cassette postali e così via). Poiché esistono massimo 64.000 porte disponibili in un dispositivo NAT basato su Windows, possono esistere massimo 8000 utenti dietro un indirizzo IP prima che le porte si esauriscano. Tenere presente che se i clienti utilizzano dispositivi basati su sistema operativo diverso da Windows, il numero di porte disponibili dipenderà dal dispositivo NAT o dal software utilizzato. In questo scenario, il numero massimo di porte potrebbe essere inferiore a 64.000. La disponibilità delle porte è inoltre influenzata da altri fattori, come ad esempio la limitazione da parte di Windows di 4.000 porte a suo uso esclusivo, che riduce il numero totale di porte disponibili a 60.000. Potrebbero esistere altre applicazioni, come ad esempio Internet Explorer, che potrebbero connettersi contemporaneamente, richiedendo porte aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="75e86-p103">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.). Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted. Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used. In this scenario, the maximum number of ports could be less than 64,000. Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="75e86-119">Calcolare il numero massimo di dispositivi supportati dietro un unico indirizzo IP pubblico con Office 365</span><span class="sxs-lookup"><span data-stu-id="75e86-119">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="75e86-p104">Per determinare il numero massimo di dispositivi dietro un unico indirizzo IP pubblico, è necessario monitorare il traffico di rete per determinare il consumo di picco porta per ogni client. Inoltre, un fattore di picco deve essere utilizzato per l'utilizzo di porta (minimo 4).</span><span class="sxs-lookup"><span data-stu-id="75e86-p104">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client. Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="75e86-122">**Per calcolare il numero di dispositivi supportati per ogni indirizzo IP, utilizzare la formula seguente:**</span><span class="sxs-lookup"><span data-stu-id="75e86-122">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="75e86-123">Numero massimo di dispositivi supportati dietro un unico indirizzo IP pubblico = (64.000 - porte riservate) / (picco di consumo Dell porte + fattore di picco)</span><span class="sxs-lookup"><span data-stu-id="75e86-123">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="75e86-124">**Se ad esempio le operazioni seguenti sono stati true:**</span><span class="sxs-lookup"><span data-stu-id="75e86-124">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="75e86-125">**Porte riservate:** 4.000 per il sistema operativo</span><span class="sxs-lookup"><span data-stu-id="75e86-125">**Restricted ports:** 4,000 for the operating system</span></span> 
    
- <span data-ttu-id="75e86-126">**Consumo Dell porte picco:** 6 per ogni dispositivo</span><span class="sxs-lookup"><span data-stu-id="75e86-126">**Peak port consumption:** 6 per device</span></span> 
    
- <span data-ttu-id="75e86-127">**Fattore di picco:** 4</span><span class="sxs-lookup"><span data-stu-id="75e86-127">**Peak factor:** 4</span></span> 
    
<span data-ttu-id="75e86-128">Quindi, il numero massimo di dispositivi supportati dietro un unico indirizzo IP pubblico = (64.000 4.000) / (6 + 4) = 6.000</span><span class="sxs-lookup"><span data-stu-id="75e86-128">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="75e86-p105">Con la versione di Office 365 Service pack, inclusi gli aggiornamenti di settembre 2011 per Microsoft Office Outlook 2007 o novembre 2011 per Microsoft Outlook 2010 o un aggiornamento successivo, il numero di connessioni di Outlook (entrambe Office Outlook 2007 con il servizio di hosting Service Pack 2 e Outlook 2010) per Exchange può essere il minor numero 2. È necessario tenere in considerazione i sistemi operativi diversi, comportamenti degli utenti, e così via per determinare il numero minimo e massimo di porte necessarie al picco della rete.</span><span class="sxs-lookup"><span data-stu-id="75e86-p105">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2. You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="75e86-131">Se si desidera supportare più dispositivi dietro un unico indirizzo IP pubblico, seguire i passaggi indicati per determinare il numero massimo di dispositivi supportabili:</span><span class="sxs-lookup"><span data-stu-id="75e86-131">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="75e86-p106">Monitorare il traffico di rete per determinare consumo Dell porte punta al client. È consigliabile raccogliere questi dati:</span><span class="sxs-lookup"><span data-stu-id="75e86-p106">Monitor network traffic to determine peak port consumption per client. You should collect this data:</span></span>
  
- <span data-ttu-id="75e86-134">Da più posizioni</span><span class="sxs-lookup"><span data-stu-id="75e86-134">From multiple locations</span></span>
    
- <span data-ttu-id="75e86-135">Da più dispositivi</span><span class="sxs-lookup"><span data-stu-id="75e86-135">From multiple devices</span></span>
    
- <span data-ttu-id="75e86-136">In più momenti</span><span class="sxs-lookup"><span data-stu-id="75e86-136">At multiple times</span></span>
    
<span data-ttu-id="75e86-137">Utilizzare la formula precedente per calcolare il numero massimo di utenti per indirizzo IP che può essere supportato nel proprio ambiente.</span><span class="sxs-lookup"><span data-stu-id="75e86-137">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="75e86-p107">Esistono diversi metodi per la distribuzione di client carico tra gli indirizzi IP pubblici aggiuntivi. Strategie disponibili variano a seconda delle funzionalità della soluzione aziendale gateway. La soluzione più semplice è segmentare lo spazio degli indirizzi di utenti e assegnare in modo statico"" un numero di indirizzi IP per ogni gateway. In alternativa che offrono molti dispositivi gateway è la possibilità di utilizzare un pool di indirizzi IP. Il vantaggio del pool di indirizzi è è molto più dinamico e riduce la probabilità che richiedere la regolazione man mano che aumenta la base di utenti.</span><span class="sxs-lookup"><span data-stu-id="75e86-p107">There are various methods for distributing client load across additional public IP addresses. Strategies available depend on the capabilities of the corporate gateway solution. The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway. Another alternative that many gateway devices offer is the ability to use a pool of IP addresses. The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="75e86-143">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="75e86-143">See also</span></span>

[<span data-ttu-id="75e86-144">Gestione di endpoint di Office 365</span><span class="sxs-lookup"><span data-stu-id="75e86-144">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="75e86-145">Domande frequenti sugli endpoint di Office 365</span><span class="sxs-lookup"><span data-stu-id="75e86-145">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

