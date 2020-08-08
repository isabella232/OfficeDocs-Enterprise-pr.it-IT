---
title: Configurare la rete per Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 'Riepilogo: vedere questi articoli per comprendere la rete per Microsoft 365.'
ms.openlocfilehash: b1497c214777e34ce4a85701ce6596f50e59910d
ms.sourcegitcommit: 839236443410eb804372c4aae969ac9a82ba683b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/07/2020
ms.locfileid: "46592150"
---
# <a name="set-up-your-network-for-microsoft-365"></a><span data-ttu-id="a0acc-103">Configurare la rete per Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="a0acc-103">Set up your network for Microsoft 365</span></span>

<span data-ttu-id="a0acc-104">*Questo articolo si riferisce sia a Microsoft 365 Enterprise che a Office 365 Enterprise*.</span><span class="sxs-lookup"><span data-stu-id="a0acc-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="a0acc-p101">Una parte importante dell'onboarding di Microsoft 365 è garantire che le connessioni di rete e Internet siano configurate per l'accesso ottimizzato. La configurazione della rete locale per l'accesso a un cloud SaaS (software-as-a-Service) distribuito a livello globale è diversa da una rete tradizionale ottimizzata per il traffico verso i centri dati locali e una connessione Internet centralizzata.</span><span class="sxs-lookup"><span data-stu-id="a0acc-p101">An important part of your Microsoft 365 onboarding is to ensure that your network and Internet connections are set up for optimized access. Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters and a central Internet connection.</span></span> 

<span data-ttu-id="a0acc-107">Consultare questi articoli per comprendere le differenze principali e per modificare i dispositivi periferici, i computer client e la rete locale in uso per prestazioni ottimali per gli utenti locali.</span><span class="sxs-lookup"><span data-stu-id="a0acc-107">Use these articles to understand the key differences and to modify your edge devices, client computers, and on-premises network to get the best performance for your on-premises users.</span></span>

## <a name="how-microsoft-365-networking-works"></a><span data-ttu-id="a0acc-108">Funzionamento della rete Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="a0acc-108">How Microsoft 365 networking works</span></span>

<span data-ttu-id="a0acc-109">Per una panoramica della connettività per Microsoft 365, vedere gli articoli seguenti:</span><span class="sxs-lookup"><span data-stu-id="a0acc-109">See these articles for an overview of connectivity for Microsoft 365:</span></span>

- [<span data-ttu-id="a0acc-110">Informazioni generali sulla connettività di rete di Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="a0acc-110">Microsoft 365 networking connectivity overview</span></span>](office-365-networking-overview.md)
- [<span data-ttu-id="a0acc-111">Principi di connettività di rete Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="a0acc-111">Microsoft 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)
- [<span data-ttu-id="a0acc-112">Valutazione della connettività di rete di Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="a0acc-112">Assessing Microsoft 365 network connectivity</span></span>](assessing-network-connectivity.md)

<span data-ttu-id="a0acc-113">Per informazioni su come migliorare le prestazioni, vedere [pianificazione della rete e ottimizzazione delle prestazioni per Microsoft 365](network-planning-and-performance.md).</span><span class="sxs-lookup"><span data-stu-id="a0acc-113">For advice on enhancing performance, see [Network planning and performance tuning for Microsoft 365](network-planning-and-performance.md).</span></span>

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a><span data-ttu-id="a0acc-114">Supporto di Microsoft 365 networking come fornitore di apparecchiature di rete</span><span class="sxs-lookup"><span data-stu-id="a0acc-114">Support Microsoft 365 networking as a network equipment vendor</span></span>

<span data-ttu-id="a0acc-p102">Se si è un fornitore di apparecchiature di rete, partecipare a [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Iscriversi al programma per creare i principi di connettività di rete Office 365 ne propri prodotti e soluzioni.</span><span class="sxs-lookup"><span data-stu-id="a0acc-p102">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span></span> 

## <a name="office-365-endpoints"></a><span data-ttu-id="a0acc-117">Endpoint di Office 365</span><span class="sxs-lookup"><span data-stu-id="a0acc-117">Office 365 endpoints</span></span>

<span data-ttu-id="a0acc-118">Gli endpoint sono il set di indirizzi IP di destinazione, i nomi di dominio DNS e gli URL per il traffico di Office 365 su Internet.</span><span class="sxs-lookup"><span data-stu-id="a0acc-118">Endpoints are the set of destination IP addresses, DNS domain names, and URLs for Office 365 traffic on the Internet.</span></span> 

<span data-ttu-id="a0acc-p103">Per ottimizzare le prestazioni di servizi basati sul cloud di Office 365, alcuni endpoint richiedono una gestione speciale da parte dei i browser client e dei dispositivi nella propria rete perimetrale. Questi dispositivi includono firewall, SSL Break and Inspect, dispositivi di ispezione dei pacchetti e sistemi di prevenzione della perdita di dati.</span><span class="sxs-lookup"><span data-stu-id="a0acc-p103">To optimize performance to Office 365 cloud-based services, some endpoints need special handling by your client browsers and the devices in your edge network. These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span></span>

<span data-ttu-id="a0acc-121">Vedere [Gestione degli endpoint di Office 365](managing-office-365-endpoints.md) per i dettagli.</span><span class="sxs-lookup"><span data-stu-id="a0acc-121">See [Managing Office 365 endpoints](managing-office-365-endpoints.md) for the details.</span></span>

<span data-ttu-id="a0acc-p104">Esistono attualmente cinque cloud di Office 365 diversi. Questa tabella consente di accedere all'elenco di endpoint per ciascuno di essi.</span><span class="sxs-lookup"><span data-stu-id="a0acc-p104">There are currently five different Office 365 clouds. This table takes you to the list of endpoints for each one.</span></span>

|||
|:-------|:-----|
| [<span data-ttu-id="a0acc-124">Endpoint in tutto il mondo</span><span class="sxs-lookup"><span data-stu-id="a0acc-124">Worldwide endpoints</span></span>](urls-and-ip-address-ranges.md) | <span data-ttu-id="a0acc-125">Gli endpoint per abbonamenti a Office 365 nel mondo, tra cui US Government Community Cloud (GCC).</span><span class="sxs-lookup"><span data-stu-id="a0acc-125">The endpoints for worldwide Office 365 subscriptions, which include the United States Government Community Cloud (GCC).</span></span> |
| [<span data-ttu-id="a0acc-126">Endpoint del U.S. Government DoD</span><span class="sxs-lookup"><span data-stu-id="a0acc-126">U.S. Government DoD endpoints</span></span>](office-365-u-s-government-dod-endpoints.md) | <span data-ttu-id="a0acc-127">Gli endpoint per gli abbonamenti del Dipartimento della Difesa degli Stati Uniti (DoD).</span><span class="sxs-lookup"><span data-stu-id="a0acc-127">The endpoints for United States Department of Defense (DoD) subscriptions.</span></span> |
| [<span data-ttu-id="a0acc-128">Endpoint del U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="a0acc-128">U.S. Government GCC High endpoints</span></span>](office-365-u-s-government-gcc-high-endpoints.md) | <span data-ttu-id="a0acc-129">Gli endpoint per gli abbonamenti di US Government Community Cloud High (GCC High).</span><span class="sxs-lookup"><span data-stu-id="a0acc-129">The endpoints for United States Government Community Cloud High (GCC High) subscriptions.</span></span> |
| [<span data-ttu-id="a0acc-130">Office 365 gestito dagli endpoint di 21Vianet</span><span class="sxs-lookup"><span data-stu-id="a0acc-130">Office 365 operated by 21Vianet endpoints</span></span>](urls-and-ip-address-ranges-21vianet.md) | <span data-ttu-id="a0acc-131">Gli endpoint di Office 365 gestiti da 21Vianet, progettato per soddisfare le esigenze di Office 365 in Cina.</span><span class="sxs-lookup"><span data-stu-id="a0acc-131">The endpoints for Office 365 operated by 21Vianet, which is designed to meet the needs for Office 365 in China.</span></span> |
| [<span data-ttu-id="a0acc-132">Endpoint di Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="a0acc-132">Office 365 Germany endpoints</span></span>](office-365-germany-endpoints.md) | <span data-ttu-id="a0acc-133">Gli endpoint di un cloud separato in Europa per i clienti più regolamentati in Germania, l’Unione Europea (UE) e l'Associazione europea di libero scambio (EFTA).</span><span class="sxs-lookup"><span data-stu-id="a0acc-133">The endpoints for a separate cloud in Europe for the most regulated customers in Germany, the European Union (EU), and the European Free Trade Association (EFTA).</span></span> |
|||

<span data-ttu-id="a0acc-134">Per ottenere automaticamente l'elenco più recente degli endpoint per il cloud di Office 365, vedere il [Servizio Web di indirizzo IP e URL di Office 365](office-365-ip-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="a0acc-134">To automate getting the latest list of endpoints for your Office 365 cloud, see the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

<span data-ttu-id="a0acc-135">Per altri endpoint, vedere gli articoli:</span><span class="sxs-lookup"><span data-stu-id="a0acc-135">For additional endpoints, see these articles:</span></span>

- [<span data-ttu-id="a0acc-136">Altri endpoint non inclusi nel servizio Web</span><span class="sxs-lookup"><span data-stu-id="a0acc-136">Additional endpoints not included in the Web service</span></span>](additional-office365-ip-addresses-and-urls.md)
- [<span data-ttu-id="a0acc-137">Richieste di rete in Office 2016 per Mac</span><span class="sxs-lookup"><span data-stu-id="a0acc-137">Network requests in Office 2016 for Mac</span></span>](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a><span data-ttu-id="a0acc-138">Ulteriori argomenti per Microsoft 365 networking</span><span class="sxs-lookup"><span data-stu-id="a0acc-138">Additional topics for Microsoft 365 networking</span></span>

<span data-ttu-id="a0acc-139">Per ulteriori informazioni, vedere gli articoli relativi a argomenti specializzati in Microsoft 365 Networking:</span><span class="sxs-lookup"><span data-stu-id="a0acc-139">See these articles for specialized topics in Microsoft 365 networking:</span></span>

- [<span data-ttu-id="a0acc-140">Reti per la distribuzione di contenuti</span><span class="sxs-lookup"><span data-stu-id="a0acc-140">Content delivery networks</span></span>](content-delivery-networks.md)
- [<span data-ttu-id="a0acc-141">Supporto IPv6 nei servizi Office 365</span><span class="sxs-lookup"><span data-stu-id="a0acc-141">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
- [<span data-ttu-id="a0acc-142">Supporto NAT con Office 365</span><span class="sxs-lookup"><span data-stu-id="a0acc-142">NAT support with Office 365</span></span>](nat-support-with-office-365.md)

## <a name="expressroute-for-microsoft-365"></a><span data-ttu-id="a0acc-143">ExpressRoute per Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="a0acc-143">ExpressRoute for Microsoft 365</span></span>

<span data-ttu-id="a0acc-144">Per informazioni sull'uso di ExpressRoute per il traffico di Office 365, consultare gli articoli seguenti:</span><span class="sxs-lookup"><span data-stu-id="a0acc-144">See these articles for information on the use of ExpressRoute for Office 365 traffic:</span></span>

- [<span data-ttu-id="a0acc-145">Azure ExpressRoute per Office 365</span><span class="sxs-lookup"><span data-stu-id="a0acc-145">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
- [<span data-ttu-id="a0acc-146">Implementazione di ExpressRoute per Office 365</span><span class="sxs-lookup"><span data-stu-id="a0acc-146">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)
- [<span data-ttu-id="a0acc-147">Pianificazione della rete con ExpressRoute per Office 365</span><span class="sxs-lookup"><span data-stu-id="a0acc-147">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
- [<span data-ttu-id="a0acc-148">Routing con ExpressRoute per Office 365</span><span class="sxs-lookup"><span data-stu-id="a0acc-148">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
