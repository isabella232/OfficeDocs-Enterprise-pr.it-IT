---
title: Configurare la rete per Office 365
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
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 'Riepilogo: consultare questi articoli per comprendere le funzionalità di rete per Office 365.'
ms.openlocfilehash: 725c2470644206045a40816fad3643b83d6c8ea6
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747415"
---
# <a name="set-up-your-network-for-office-365"></a>Configurare la rete per Office 365

*Questo articolo si applica sia a Office 365 Enterprise che a Microsoft 365 Enterprise*.

Una parte importante dell'onboarding di Office 365 consiste nel verificare che la rete e le connessioni Internet siano configurate per l'accesso ottimizzato. La configurazione della rete locale per accedere al cloud SaaS (Software-as-a-Service) distribuito a livello globale è diversa da una rete tradizionale ottimizzata per il traffico verso data center locali e una connessione Internet centralizzata. 

Consultare questi articoli per comprendere le differenze principali e per modificare i dispositivi periferici, i computer client e la rete locale in uso per prestazioni ottimali per gli utenti locali.

## <a name="how-office-365-networking-works"></a>Funzionamento della rete di Office 365

Per una panoramica sulla connettività per Office 365, consultare gli articoli seguenti:

- [Informazioni generali sulla connettività di rete di Office 365](office-365-networking-overview.md)
- [Principi della connettività di rete di Office 365](office-365-network-connectivity-principles.md)
- [Valutazione della connettività di rete di Office 365](assessing-network-connectivity.md)

Per informazioni sull'ottimizzazione delle prestazioni, vedere [Pianificazione della rete e ottimizzazione delle prestazioni per Office 365](network-planning-and-performance.md).

## <a name="support-office-365-networking-as-a-network-equipment-vendor"></a>Supporto della rete di Office 365 come fornitore di apparecchiature di rete

Se si è un fornitore di apparecchiature di rete, partecipare a [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Iscriversi al programma per creare i principi di connettività di rete Office 365 ne propri prodotti e soluzioni. 

## <a name="office-365-endpoints"></a>Endpoint di Office 365

Gli endpoint sono il set di indirizzi IP di destinazione, i nomi di dominio DNS e gli URL per il traffico di Office 365 su Internet. 

Per ottimizzare le prestazioni di servizi basati sul cloud di Office 365, alcuni endpoint richiedono una gestione speciale da parte dei i browser client e dei dispositivi nella propria rete perimetrale. Questi dispositivi includono firewall, SSL Break and Inspect, dispositivi di ispezione dei pacchetti e sistemi di prevenzione della perdita di dati.

Vedere [Gestione degli endpoint di Office 365](managing-office-365-endpoints.md) per i dettagli.

Esistono attualmente cinque cloud di Office 365 diversi. Questa tabella consente di accedere all'elenco di endpoint per ciascuno di essi.

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


## <a name="additional-topics-for-office-365-networking"></a>Ulteriori argomenti per la rete di Office 365

Per argomenti specializzati relativi alle funzionalità di rete di Office 365, consultare gli articoli seguenti:

- [Reti per la distribuzione di contenuti](content-delivery-networks.md)
- [Supporto IPv6 nei servizi Office 365](ipv6-support.md)
- [Supporto NAT con Office 365](nat-support-with-office-365.md)

## <a name="expressroute-for-office-365"></a>ExpressRoute per Office 365

Per informazioni sull'uso di ExpressRoute per il traffico di Office 365, consultare gli articoli seguenti:

- [Azure ExpressRoute per Office 365](azure-expressroute.md)
- [Implementazione di ExpressRoute per Office 365](implementing-expressroute.md)
- [Pianificazione della rete con ExpressRoute per Office 365](network-planning-with-expressroute.md)
- [Routing con ExpressRoute per Office 365](routing-with-expressroute.md)
