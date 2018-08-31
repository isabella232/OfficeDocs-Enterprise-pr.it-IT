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
# <a name="office-365-germany-endpoints"></a>Endpoint di Office 365 Germany

 *Si applica a: Amministrazione di Office 365*

**Riepilogo:** Office 365 richiede la connettività a Internet. Endpoint riportata di seguito devono essere raggiungibili per i clienti che utilizzano solo i piani di **Office 365 Germania** .
  
> [!NOTE]
> Microsoft sta sviluppando un servizio web basato su REST per l'indirizzo IP e le voci FQDN in questa pagina. Questo nuovo servizio consentono di configurare e aggiornare i dispositivi di rete perimetrale, ad esempio firewall e server proxy. È possibile scaricare l'elenco di endpoint, la versione corrente dell'elenco o modifiche specifiche. Questo servizio in futuro sostituirà il documento XML, feed RSS e l'indirizzo IP e le voci FQDN in questa pagina. Per provare a utilizzare questo nuovo servizio, accedere al [servizio Web](managing-office-365-endpoints.md#webservice). 
  
 **Endpoint di office 365:** [Tutto il mondo (inclusi GCC)](urls-and-ip-address-ranges.md)   |  [Office 365 gestito dal 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germania* | [DoD governo di Office 365 US](office-365-u-s-government-dod-endpoints.md) | [Le governo di Office 365 US ad alta](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**Ultimo aggiornamento:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [elenco delle modifiche apportate agli endpoint di Office 365 Germania](office-365-germany-endpoints-change-log.md)||

Iniziare con [gli endpoint di gestione di Office 365](managing-office-365-endpoints.md) acquisire familiarità con i suggerimenti per la gestione di connettività di rete con questi dati. Aggiornamento dei dati di endpoint all'inizio di ogni mese, nuovi indirizzi IP e gli URL pubblicati 30 giorni prima fase attiva. In questo modo per i clienti che non sono ancora automazione degli aggiornamenti per eseguire i processi prima è necessaria una nuova connessione. È anche possibile aggiornare gli endpoint nel corso del mese se necessari per la risoluzione di supporto, problemi di protezione o altri requisiti operativi immediati. È sempre possibile fare riferimento all' [elenco delle modifiche apportate agli endpoint di Office 365 Germania](office-365-germany-endpoints-change-log.md).

I dati riportati in questa pagina riportata di seguito viene generati dai servizi web basato su REST. Se si utilizza un dispositivo di rete o di uno script di accedere a tali dati, deve accedere direttamente al [servizio Web](managing-office-365-endpoints.md#webservice) .

Dati di endpoint riportata di seguito sono elencati i requisiti per la connettività dal computer dell'utente a Office 365. Non include le connessioni di rete da Microsoft in una rete di clienti, detta ibrido o connessioni di rete in ingresso.

I punti finali sono raggruppati nelle quattro aree del servizio. Le aree del tre servizio prima è possibile selezionare in modo indipendente per la connettività. L'area servizio quarto una dipendenza comuni (denominato Office Online e Microsoft 365 comuni) e deve disporre sempre di connettività di rete.

Vengono illustrate le colonne di dati:

- **ID**: numero di ID della riga, nota anche come un insieme di endpoint. Questo ID è uguale a quello restituito dal servizio web per il set di endpoint.

- **Categoria**: visualizza se l'insieme di endpoint è categorizzato come "Ottimizza", "Consenti" o "Default". Per ulteriori informazioni su queste categorie e le istruzioni per la gestione di essi in [http://aka.ms/pnc](http://aka.ms/pnc). Questa colonna vengono inoltre elencati i set di endpoint è necessario disporre di connettività di rete. Per i set di endpoint che non devono disporre di connettività di rete, offriamo note in questo campo per indicare quali funzionalità saranno mancante se il set di endpoint è bloccato. Se si esclusione di un'area intero servizio, gli insiemi di endpoint elencati in base alle esigenze non richiedono la connettività.

- **ER**: questo è **Sì** se il set di endpoint è supportato su Azure ExpressRoute con Office 365 route prefissi. Community BGP che include i prefissi route riportati risulti allineato con l'area servizio elencato. Una volta ER **No**, ciò significa che ExpressRoute non è supportato per questo set di endpoint. Tuttavia, è necessario non considerare che le route non sono annunciate per un set di endpoint dove ER è **No**.

- **Gli indirizzi**: sono elencati i nomi FQDN o nomi di dominio con caratteri jolly e intervalli di indirizzi IP per il set di endpoint. Si noti che un intervallo di indirizzi IP nel formato CIDR e può includere molti singoli indirizzi IP nella rete specificata.
 
- **Porte**: vengono elencati le porte TCP o UDP vengono combinate con gli indirizzi per creare l'endpoint di rete. È possibile notare alcune la duplicazione di intervalli di indirizzi IP in cui sono elencate le porte diverse.

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

