---
title: Abilitazione di SharePoint Multi-Geo in una posizione geografica satellite
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Abilitazione di SharePoint Multi-Geo in una posizione geografica satellite.
ms.openlocfilehash: 98666f76a5b3ec055a6f26d30f502c3cc6b6d3bb
ms.sourcegitcommit: 0ddd9b0c9c23dc6479dce9f5701b69d533d76127
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "31025190"
---
# <a name="enabling-sharepoint-multi-geo-in-your-satellite-geo-location"></a>Abilitazione di SharePoint Multi-Geo in una posizione geografica satellite

Questo articolo è diretto agli amministratori globali o di SharePoint che hanno creato una posizione satellite Multi-Geo **prima** che la funzionalità di SharePoint diventasse disponibile il 27 marzo 2019 e che non hanno abilitato SharePoint Multi-Geo nella posizione o nelle posizioni satellite. 

>[!Note]
>Se è stata aggiunta una nuova posizione geografica **dopo il 27 marzo**, non è necessario seguire queste istruzioni, poiché la nuova posizione sarà stata già attivata per Multi-Geo di OneDrive e SharePoint.

Queste istruzioni consentono di abilitare SharePoint nella posizione satellite, per consentire agli utenti di Multi-Geo di usufruire della funzionalità di OneDrive e SharePoint in O365. 

>[!IMPORTANT]
>Si tenga presente che si tratta di un processo non reversibile in modo autonomo. Dopo aver impostato la modalità SPO, non sarà più possibile ripristinare il tenant in modalità Multi-Geo solo per OneDrive senza richiedere assistenza. 

## <a name="to-set-a-geo-location-into-spo-mode"></a>Impostare una posizione geografica in modalità SPO

Per impostare una posizione geografica in modalità SPO, connettersi alla posizione geografica scelta:

1.  Aprire SharePoint Online Management Shell. 
2.  Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com"-Credential $credential
3.  Set-SPOMultiGeoExperience</br></br>
![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)
4.  Questa operazione in genere richiede circa un'ora. Durante questo intervallo di tempo eseguiamo alcune operazioni in background nel servizio e nel tenant. Dopo circa 1 ora, eseguire il comando Get-SPOMultiGeoExperience.  Servirà per visualizzare se la posizione geografica è in modalità di SharePoint Online.</br></br>
![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)

 
 
 
>[!Note]
>Alcune cache del servizio eseguono aggiornamenti ogni 24 ore, quindi è possibile durante questo periodo di 24 ore che la posizione geografica satellite occasionalmente si comporti come se fosse ancora in modalità ODB. Questo non causa problemi tecnici. 
 
Per ulteriori informazioni su SharePoint Multi-Geo visitare [aka.ms/sharepointmultigeo](https://docs.microsoft.com/it-IT/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)


