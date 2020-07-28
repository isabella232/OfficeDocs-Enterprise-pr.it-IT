---
title: Quote di archiviazione di SharePoint in ambienti multi-geo
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Normal
description: Informazioni sulle Quote di archiviazione di SharePoint in ambienti multi-geo.
ms.openlocfilehash: f0463797dd3471f349e60d8f029b7ae2fa4b65a6
ms.sourcegitcommit: aac21bb1a7c1dfc3ba76a2db883e0457037c5667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/28/2020
ms.locfileid: "45433737"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a>Quote di archiviazione di SharePoint in ambienti multi-geo

Per impostazione predefinita, tutti i percorsi di un ambiente multi-geo condividono la Quota di archiviazione disponibile per il tenant.

Con l'impostazione di quota di archiviazione geografica di SharePoint, è possibile gestire la Quota di archiviazione per ogni posizione geografica. Quando si assegna una quota di archiviazione per una posizione geografica, diventa la quantità massima di spazio di archiviazione disponibile per quella posizione geografica e viene sottratta dalla Quota di archiviazione disponibile per il tenant. La Quota di archiviazione disponibile per il tenant rimanente verrà quindi condivisa tra le posizioni geografiche configurate a cui non è stata assegnata una quota di archiviazione.

La Quota di archiviazione di SharePoint per qualsiasi posizione geografica può essere assegnata dall'amministratore di SharePoint Online connettendosi alla posizione centrale. Gli amministratori di posizioni geografiche satellitari possono visualizzare la Quota di archiviazione, ma non possono assegnarla.

## <a name="configure-a-storage-quota-for-a-geo-location"></a>Configurare una quota di archiviazione per una posizione geografica.

Usare il [Modulo di Microsoft Office SharePoint Online](https://www.microsoft.com/download/details.aspx?id=35588 ) e connettersi alla posizione centrale per assegnare la Quota di archiviazione ad una posizione geografica. 

Per assegnare una Quota di archiviazione ad un percorso, eseguire il cmdlet:

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>`

Per visualizzare la Quota di archiviazione della posizione geografica attuale, eseguire:

`Get-SPOGeoStorageQuota`

![Schermata della finestra di PowerShell che mostra il cmdlet Get-SPOGeoStorageQuota](media/multi-geo-storage-quota.png)

Per visualizzare la Quota di archiviazione per tutte le posizioni geografiche attuali, eseguire:

`Get-SPOGeoStorageQuota -AllLocations`

Per rimuovere la quota di archiviazione assegnata ad una posizione geografica, impostare `StorageQuota value = 0`:

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0`
