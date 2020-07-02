---
title: URL e intervalli di indirizzi IP di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/29/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: 8548a211-3fe7-47cb-abb1-355ea5aa88a2
description: 'Summary: Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 plans, including Government Community Cloud (GCC).'
hideEdit: true
ms.openlocfilehash: d75fa6d88255ff5df785fa335a9976c4bcca309d
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997444"
---
# <a name="office-365-urls-and-ip-address-ranges"></a>URL e intervalli di indirizzi IP di Office 365

Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 plans, including Government Community Cloud (GCC).
  
> [!NOTE]
> Come parte della risposta di Microsoft alla crisi COVID-19, Microsoft ha dichiarato una moratoria temporanea su alcune modifiche pianificate di URL e indirizzi IP. Questa moratoria ha lo scopo di fornire ai team IT dei clienti sicurezza e semplicità nell'implementazione delle ottimizzazioni di rete consigliate per gli scenari di Office 365 per il lavoro da casa. Dal 24 marzo 2020 al 30 giugno 2020 questa moratoria interromperà le modifiche per i principali servizi di Office 365 (Exchange Online, SharePoint Online e Microsoft Teams) agli intervalli IP e agli URL inclusi nella categoria Ottimizzazione. Le modifiche all'interno di altre categorie di endpoint avverranno come al solito. Durante questo periodo, i clienti possono usare le definizioni di endpoint del servizio della categoria Ottimizzazione di Office 365 in modo statico per eseguire ottimizzazioni di rete mirate come prenotazioni di larghezza di banda o configurazione di split tunneling per VPN con rischi minimi per la connettività di Office 365 a causa di modifiche della rete lato cloud. Per garantire che non si verifichino interruzioni del servizio al termine del periodo di moratoria, Microsoft consiglia vivamente ai clienti di implementare processi di gestione delle modifiche e/o di automazione per gli endpoint dei servizi di Office 365 seguendo le indicazioni fornite in [Gestione degli endpoint di Office 365](managing-office-365-endpoints.md).

> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
  
*Office 365 internazionale (+GCC)* | [Office 365 gestito da 21Vianet](urls-and-ip-address-ranges-21vianet.md) | [Office 365 Germany](office-365-germany-endpoints.md) | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md)  | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |
  
||||
|:-----|:-----|:-----|
|**Ultimo aggiornamento:** 06/29/2020- ![ RSS ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Change log Subscription](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**Download:** tutte le destinazioni obbligatorie e facoltative in un unico elenco in [formato JSON](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).  <br/> | **Uso:** i nostri [file PAC ](managing-office-365-endpoints.md#pacfiles) proxy <br/> |

 Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](office-365-ip-web-service.md) directly.

Endpoint data below lists requirements for connectivity from a user's machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections. See [Additional endpoints](additional-office365-ip-addresses-and-urls.md) for more information.

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

Le colonne di dati visualizzate sono le seguenti:

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as "Optimize", "Allow", or "Default". You can read about these categories and guidance for management of them at [New Office 365 endpoint categories](https://docs.microsoft.com/office365/enterprise/office-365-network-connectivity-principles#new-office-365-endpoint-categories). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.

[!INCLUDE [Office 365 worldwide endpoints](./includes/office-365-worldwide-endpoints.md)]

>[!Note]
>Per suggerimenti sugli URL e indirizzi IP di Yammer, vedere [Questo post di blog](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592).
>

## <a name="related-topics"></a>Argomenti correlati

[Gestione degli endpoint di Office 365](managing-office-365-endpoints.md)
  
[Risoluzione dei problemi di connettività di Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[Connettività client](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Reti per la distribuzione di contenuti](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Intervalli IP del data center di Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Spazio IP pubblico di Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
