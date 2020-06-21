---
title: Configurare la rete per Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
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
ms.openlocfilehash: 4c414d8cbf597af9165e991a71e5d6a6a330e33a
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735659"
---
# <a name="set-up-your-network-for-microsoft-365"></a>Configurare la rete per Microsoft 365

*Questo articolo si applica sia a Microsoft 365 Enterprise che a Office 365 Enterprise.*

An important part of your Microsoft 365 onboarding is to ensure that your network and Internet connections are set up for optimized access. Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters and a central Internet connection. 

Consultare questi articoli per comprendere le differenze principali e per modificare i dispositivi periferici, i computer client e la rete locale in uso per prestazioni ottimali per gli utenti locali.

## <a name="how-microsoft-365-networking-works"></a>Funzionamento della rete Microsoft 365

Per una panoramica della connettività per Microsoft 365, vedere gli articoli seguenti:

- [Informazioni generali sulla connettività di rete di Microsoft 365](office-365-networking-overview.md)
- [Principi di connettività di rete Microsoft 365](office-365-network-connectivity-principles.md)
- [Valutazione della connettività di rete di Microsoft 365](assessing-network-connectivity.md)

Per informazioni su come migliorare le prestazioni, vedere [pianificazione della rete e ottimizzazione delle prestazioni per Microsoft 365](network-planning-and-performance.md).

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a>Supporto di Microsoft 365 networking come fornitore di apparecchiature di rete

If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Enroll in the program to build Office 365 network connectivity principles into your products and solutions. 

## <a name="office-365-endpoints"></a>Endpoint di Office 365

Gli endpoint sono il set di indirizzi IP di destinazione, i nomi di dominio DNS e gli URL per il traffico di Office 365 su Internet. 

To optimize performance to Office 365 cloud-based services, some endpoints need special handling by your client browsers and the devices in your edge network. These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.

Vedere [Gestione degli endpoint di Office 365](managing-office-365-endpoints.md) per i dettagli.

There are currently five different Office 365 clouds. This table takes you to the list of endpoints for each one.

|||
|:-------|:-----|
| [Endpoint in tutto il mondo](urls-and-ip-address-ranges.md) | Gli endpoint per abbonamenti a Office 365 nel mondo, tra cui US Government Community Cloud (GCC). |
| [Endpoint del U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | Gli endpoint per gli abbonamenti del Dipartimento della Difesa degli Stati Uniti (DoD). |
| [Endpoint del U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) | Gli endpoint per gli abbonamenti di US Government Community Cloud High (GCC High). |
| [Office 365 gestito dagli endpoint di 21Vianet](urls-and-ip-address-ranges-21vianet.md) | Gli endpoint di Office 365 gestiti da 21Vianet, progettato per soddisfare le esigenze di Office 365 in Cina. |
| [Endpoint di Office 365 Germany](office-365-germany-endpoints.md) | Gli endpoint di un cloud separato in Europa per i clienti più regolamentati in Germania, l’Unione Europea (UE) e l'Associazione europea di libero scambio (EFTA). |
|||

Per ottenere automaticamente l'elenco più recente degli endpoint per il cloud di Office 365, vedere il [Servizio Web di indirizzo IP e URL di Office 365](office-365-ip-web-service.md).

Per altri endpoint, vedere gli articoli:

- [Altri endpoint non inclusi nel servizio Web](additional-office365-ip-addresses-and-urls.md)
- [Richieste di rete in Office 2016 per Mac](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a>Ulteriori argomenti per Microsoft 365 networking

Per ulteriori informazioni, vedere gli articoli relativi a argomenti specializzati in Microsoft 365 Networking:

- [Reti per la distribuzione di contenuti](content-delivery-networks.md)
- [Supporto IPv6 nei servizi Office 365](ipv6-support.md)
- [Supporto NAT con Office 365](nat-support-with-office-365.md)

## <a name="expressroute-for-microsoft-365"></a>ExpressRoute per Microsoft 365

Per informazioni sull'uso di ExpressRoute per il traffico di Office 365, consultare gli articoli seguenti:

- [Azure ExpressRoute per Office 365](azure-expressroute.md)
- [Implementazione di ExpressRoute per Office 365](implementing-expressroute.md)
- [Pianificazione della rete con ExpressRoute per Office 365](network-planning-with-expressroute.md)
- [Routing con ExpressRoute per Office 365](routing-with-expressroute.md)
