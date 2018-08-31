---
title: Endpoint di Office 365 Germany
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: Se l'organizzazione utilizza Office 365 e limita i computer della rete di connettersi a Internet, di seguito sono disponibili gli endpoint (FQDN, porte, gli URL e IPv4 e IPv6 intervalli di indirizzi) che è consigliabile includere nell'uscita consentire gli elenchi garantire la computer correttamente possono utilizzare Office 365.
hideEdit: true
ms.openlocfilehash: fa5133391a24a3b9bb82a9dc5065e4dd10bb5bfe
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541110"
---
# <a name="office-365-germany-endpoints"></a><span data-ttu-id="65d1b-103">Endpoint di Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="65d1b-103">Office 365 Germany endpoints</span></span>

 <span data-ttu-id="65d1b-104">*Si applica a: Amministrazione di Office 365*</span><span class="sxs-lookup"><span data-stu-id="65d1b-104">*Applies To: Office 365 Admin*</span></span>

<span data-ttu-id="65d1b-p101">**Riepilogo:** Office 365 richiede la connettività a Internet. Endpoint riportata di seguito devono essere raggiungibili per i clienti che utilizzano solo i piani di **Office 365 Germania** .</span><span class="sxs-lookup"><span data-stu-id="65d1b-p101">**Summary:** Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using **Office 365 Germany** plans only.</span></span>
  
> [!NOTE]
> <span data-ttu-id="65d1b-p102">Microsoft sta sviluppando un servizio web basato su REST per l'indirizzo IP e le voci FQDN in questa pagina. Questo nuovo servizio consentono di configurare e aggiornare i dispositivi di rete perimetrale, ad esempio firewall e server proxy. È possibile scaricare l'elenco di endpoint, la versione corrente dell'elenco o modifiche specifiche. Questo servizio in futuro sostituirà il documento XML, feed RSS e l'indirizzo IP e le voci FQDN in questa pagina. Per provare a utilizzare questo nuovo servizio, accedere al [servizio Web](managing-office-365-endpoints.md#webservice).</span><span class="sxs-lookup"><span data-stu-id="65d1b-p102">Microsoft is developing a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service will eventually replace the XML document, RSS feed, and the IP address and FQDN entries on this page. To try out this new service, go to [Web service](managing-office-365-endpoints.md#webservice).</span></span> 
  
 <span data-ttu-id="65d1b-112">**Endpoint di office 365:** [Tutto il mondo (inclusi GCC)](urls-and-ip-address-ranges.md)   |  [Office 365 gestito dal 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germania* | [DoD governo di Office 365 US](office-365-u-s-government-dod-endpoints.md) | [Le governo di Office 365 US ad alta](office-365-u-s-government-gcc-high-endpoints.md)  |</span><span class="sxs-lookup"><span data-stu-id="65d1b-112">**Office 365 endpoints:** [Worldwide (including GCC)](urls-and-ip-address-ranges.md)  | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germany* | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="65d1b-113">**Ultimo aggiornamento:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [elenco delle modifiche apportate agli endpoint di Office 365 Germania](office-365-germany-endpoints-change-log.md)</span><span class="sxs-lookup"><span data-stu-id="65d1b-113">**Last updated:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [List of changes to the Office 365 Germany endpoints](office-365-germany-endpoints-change-log.md)</span></span>||

<span data-ttu-id="65d1b-p103">Iniziare con [gli endpoint di gestione di Office 365](managing-office-365-endpoints.md) acquisire familiarità con i suggerimenti per la gestione di connettività di rete con questi dati. Aggiornamento dei dati di endpoint all'inizio di ogni mese, nuovi indirizzi IP e gli URL pubblicati 30 giorni prima fase attiva. In questo modo per i clienti che non sono ancora automazione degli aggiornamenti per eseguire i processi prima è necessaria una nuova connessione. È anche possibile aggiornare gli endpoint nel corso del mese se necessari per la risoluzione di supporto, problemi di protezione o altri requisiti operativi immediati. È sempre possibile fare riferimento all' [elenco delle modifiche apportate agli endpoint di Office 365 Germania](office-365-germany-endpoints-change-log.md).</span><span class="sxs-lookup"><span data-stu-id="65d1b-p103">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. You can always refer to the [list of changes to the Office 365 Germany endpoints](office-365-germany-endpoints-change-log.md).</span></span>

<span data-ttu-id="65d1b-p104">I dati riportati in questa pagina riportata di seguito viene generati dai servizi web basato su REST. Se si utilizza un dispositivo di rete o di uno script di accedere a tali dati, deve accedere direttamente al [servizio Web](managing-office-365-endpoints.md#webservice) .</span><span class="sxs-lookup"><span data-stu-id="65d1b-p104">The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](managing-office-365-endpoints.md#webservice) directly.</span></span>

<span data-ttu-id="65d1b-p105">Dati di endpoint riportata di seguito sono elencati i requisiti per la connettività dal computer dell'utente a Office 365. Non include le connessioni di rete da Microsoft in una rete di clienti, detta ibrido o connessioni di rete in ingresso.</span><span class="sxs-lookup"><span data-stu-id="65d1b-p105">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.</span></span>

<span data-ttu-id="65d1b-p106">I punti finali sono raggruppati nelle quattro aree del servizio. Le aree del tre servizio prima è possibile selezionare in modo indipendente per la connettività. L'area servizio quarto una dipendenza comuni (denominato Office Online e Microsoft 365 comuni) e deve disporre sempre di connettività di rete.</span><span class="sxs-lookup"><span data-stu-id="65d1b-p106">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office Online) and must always have network connectivity.</span></span>

<span data-ttu-id="65d1b-126">Vengono illustrate le colonne di dati:</span><span class="sxs-lookup"><span data-stu-id="65d1b-126">Data columns shown are:</span></span>

- <span data-ttu-id="65d1b-p107">**ID**: numero di ID della riga, nota anche come un insieme di endpoint. Questo ID è uguale a quello restituito dal servizio web per il set di endpoint.</span><span class="sxs-lookup"><span data-stu-id="65d1b-p107">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="65d1b-p108">**Categoria**: visualizza se l'insieme di endpoint è categorizzato come "Ottimizza", "Consenti" o "Default". Per ulteriori informazioni su queste categorie e le istruzioni per la gestione di essi in [http://aka.ms/pnc](http://aka.ms/pnc). Questa colonna vengono inoltre elencati i set di endpoint è necessario disporre di connettività di rete. Per i set di endpoint che non devono disporre di connettività di rete, offriamo note in questo campo per indicare quali funzionalità saranno mancante se il set di endpoint è bloccato. Se si esclusione di un'area intero servizio, gli insiemi di endpoint elencati in base alle esigenze non richiedono la connettività.</span><span class="sxs-lookup"><span data-stu-id="65d1b-p108">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [http://aka.ms/pnc](http://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="65d1b-p109">**ER**: questo è **Sì** se il set di endpoint è supportato su Azure ExpressRoute con Office 365 route prefissi. Community BGP che include i prefissi route riportati risulti allineato con l'area servizio elencato. Una volta ER **No**, ciò significa che ExpressRoute non è supportato per questo set di endpoint. Tuttavia, è necessario non considerare che le route non sono annunciate per un set di endpoint dove ER è **No**.</span><span class="sxs-lookup"><span data-stu-id="65d1b-p109">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.</span></span>

- <span data-ttu-id="65d1b-p110">**Gli indirizzi**: sono elencati i nomi FQDN o nomi di dominio con caratteri jolly e intervalli di indirizzi IP per il set di endpoint. Si noti che un intervallo di indirizzi IP nel formato CIDR e può includere molti singoli indirizzi IP nella rete specificata.</span><span class="sxs-lookup"><span data-stu-id="65d1b-p110">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="65d1b-p111">**Porte**: vengono elencati le porte TCP o UDP vengono combinate con gli indirizzi per creare l'endpoint di rete. È possibile notare alcune la duplicazione di intervalli di indirizzi IP in cui sono elencate le porte diverse.</span><span class="sxs-lookup"><span data-stu-id="65d1b-p111">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

