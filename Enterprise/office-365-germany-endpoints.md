---
title: Endpoint di Office 365 Germany
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/01/2018
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
ms.openlocfilehash: 080f37d8f8cc6ad201ec9fd65489072c0ec1e585
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933113"
---
# <a name="office-365-germany-endpoints"></a>Endpoint di Office 365 Germany

 *Si applica a: Amministrazione di Office 365*

**Riepilogo:** Office 365 richiede la connettività a Internet. Endpoint riportata di seguito devono essere raggiungibili per i clienti che utilizzano solo i piani di **Office 365 Germania** .
  
> [!NOTE]
> Microsoft ha rilasciato un servizio web basato su REST per l'indirizzo IP e le voci FQDN in questa pagina. Questo nuovo servizio consentono di configurare e aggiornare i dispositivi di rete perimetrale, ad esempio firewall e server proxy. È possibile scaricare l'elenco di endpoint, la versione corrente dell'elenco o modifiche specifiche. Questo servizio sostituisce il documento XML correlato a questa pagina, il 2 ottobre 2018 è diventato obsoleto. Per provare a utilizzare questo nuovo servizio, accedere al [servizio Web](office-365-ip-web-service.md).
  
 **Endpoint di Office 365:** [Worldwide (compreso GCC)](urls-and-ip-address-ranges.md)  | [Office 365 gestito da 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germany* | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**Ultimo aggiornamento:** 11/1/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [sottoscrizione registro modifiche](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) |**Download:** tutte le destinazioni obbligatori e facoltative di un elenco [formattato JSON](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) .  <br/> |

Iniziare con [gli endpoint di gestione di Office 365](managing-office-365-endpoints.md) acquisire familiarità con i suggerimenti per la gestione di connettività di rete con questi dati. Aggiornamento dei dati di endpoint all'inizio di ogni mese, nuovi indirizzi IP e gli URL pubblicati 30 giorni prima fase attiva. In tal modo gli utenti che hanno ancora non si dispongono automatica degli aggiornamenti per eseguire i processi prima è necessaria una nuova connessione. È anche possibile aggiornare gli endpoint nel corso del mese se necessari per la risoluzione di supporto, problemi di protezione o altri requisiti operativi immediati. È sempre possibile consultare per la [Modifica l'iscrizione al registro](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

I dati riportati in questa pagina riportata di seguito viene generati dai servizi web basato su REST. Se si utilizza un dispositivo di rete o di uno script di accedere a tali dati, deve accedere direttamente al [servizio Web](office-365-ip-web-service.md) .

I dati degli endpoint riportati di seguito elencano i requisiti di connessione del computer di un utente a Office 365. Non sono incluse le connessioni di rete da Microsoft a una rete cliente, a volte chiamate connessioni di rete ibride o in ingresso.

Gli endpoint sono raggruppati in quattro aree del servizio. Le prime tre aree del servizio possono essere selezionate in modo indipendente per la connessione. La quarta area del servizio è una dipendenza comune (denominata Microsoft 365 Common e Office Online) e deve avere sempre la connessione di rete.

Le colonne di dati visualizzate sono le seguenti:

- **ID**: il numero ID della riga, noto anche come set di endpoint. Questo ID è uguale a quello restituito dal servizio Web per il set di endpoint.

- **Categoria**: indica se il set di endpoint è categorizzato come "Optimize", "Allow" o "Default". Sono disponibili informazioni su queste categorie e linee guida per la loro gestione nell'articolo [http://aka.ms/pnc](http://aka.ms/pnc). Inoltre, in questa colonna sono elencati i set di endpoint necessari per la connessione di rete. Per i set di endpoint non necessari per la connessione di rete, in questo campo sono fornite delle note che indicano quale funzionalità non sarebbe disponibile se il set di endpoint fosse bloccato. Se si esclude un'intera area del servizio, i set di endpoint elencati come necessari non richiedono la connessione.

- **ER**: presenta **Sì** se il set di endpoint è supportato su Azure ExpressRoute con i prefissi di route Office 365. La community BGP che include i prefissi di route mostrati si allinea con l'area del servizio elencata. Se ER presenta **No**, significa che ExpressRoute non è supportata per il set di endpoint. Tuttavia, non è detto che non vengano annunciate route per un set di endpoint in cui ER presenta **No**.

- **Indirizzi**: sono elencati i nomi di dominio completo (FQDN) o con caratteri jolly e gli intervalli di indirizzi IP per il set di endpoint. Tenere presente che un intervallo di indirizzi IP è in formato CIDR e potrebbe includere più indirizzi IP nella rete specificata.
 
- **Porte**: sono elencate le porte TCP o UDP combinate con gli indirizzi per formare l'endpoint di rete. Si potrebbero notare dei duplicati negli intervalli di indirizzi IP in cui sono presenti diverse porte.

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

