---
title: Quote di archiviazione di SharePoint in ambienti multi-geo
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
localization_priority: Priority
description: Informazioni sulle Quote di archiviazione di SharePoint in ambienti multi-geo.
ms.openlocfilehash: 1e9c24cac43f5376fcef35782b3b024ab10cef58
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843987"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a><span data-ttu-id="6852c-103">Quote di archiviazione di SharePoint in ambienti multi-geo</span><span class="sxs-lookup"><span data-stu-id="6852c-103">SharePoint storage quotas in multi-geo environments</span></span>

<span data-ttu-id="6852c-104">Per impostazione predefinita, tutti i percorsi di un ambiente multi-geo condividono la Quota di archiviazione disponibile per il tenant.</span><span class="sxs-lookup"><span data-stu-id="6852c-104">By default, all geo locations of a multi-geo environment share the available tenant storage quota.</span></span>

<span data-ttu-id="6852c-105">Con l'impostazione di quota di archiviazione geografica di SharePoint, è possibile gestire la Quota di archiviazione per ogni posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="6852c-105">With the SharePoint geo storage quota setting, you can manage the storage quota for each geo location.</span></span> <span data-ttu-id="6852c-106">Quando si assegna una quota di archiviazione per una posizione geografica, diventa la quantità massima di spazio di archiviazione disponibile per quella posizione geografica e viene sottratta dalla Quota di archiviazione disponibile per il tenant.</span><span class="sxs-lookup"><span data-stu-id="6852c-106">When you allocate a storage quota for a geo location, it becomes the maximum amount of storage available for that geo location, and is deducted from the available tenant storage quota.</span></span> <span data-ttu-id="6852c-107">La Quota di archiviazione disponibile per il tenant rimanente verrà quindi condivisa tra le posizioni geografiche configurate a cui non è stata assegnata una quota di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="6852c-107">The remaining available tenant storage quota is then shared across the configured geo locations for which a specific storage quota has not been allocated.</span></span>

<span data-ttu-id="6852c-108">La Quota di archiviazione di SharePoint per qualsiasi posizione geografica può essere assegnata dall'amministratore di SharePoint Online connettendosi alla posizione centrale.</span><span class="sxs-lookup"><span data-stu-id="6852c-108">The SharePoint storage quota for any geo location can be allocated by the SharePoint Online administrator by connecting to the central location.</span></span> <span data-ttu-id="6852c-109">Gli amministratori di posizioni geografiche satellitari possono visualizzare la Quota di archiviazione, ma non possono assegnarla.</span><span class="sxs-lookup"><span data-stu-id="6852c-109">Geo administrators for satellite locations can view the storage quota but cannot allocate it.</span></span>

## <a name="configure-a-storage-quota-for-a-geo-location"></a><span data-ttu-id="6852c-110">Configurare una quota di archiviazione per una posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="6852c-110">Configure a storage quota for a geo location</span></span>

<span data-ttu-id="6852c-111">Usare il [Modulo di Microsoft Office SharePoint Online](https://www.microsoft.com/download/details.aspx?id=35588 ) e connettersi alla posizione centrale per assegnare la Quota di archiviazione ad una posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="6852c-111">Use the [Microsoft SharePoint Online Module](https://www.microsoft.com/download/details.aspx?id=35588 ) and connect to the central location to allocate the storage quota for a geo location.</span></span> 

<span data-ttu-id="6852c-112">Per assegnare una Quota di archiviazione ad un percorso, eseguire il cmdlet:</span><span class="sxs-lookup"><span data-stu-id="6852c-112">To allocate Storage Quota for a location, run cmdlet:</span></span>

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>`

<span data-ttu-id="6852c-113">Per visualizzare la Quota di archiviazione della posizione geografica attuale, eseguire:</span><span class="sxs-lookup"><span data-stu-id="6852c-113">To view Storage Quota for the current geo location, run:</span></span>

`Get-SPOGeoStorageQuota`

![Schermata della finestra di PowerShell che mostra il cmdlet Get-SPOGeoStorageQuota](media/multi-geo-storage-quota.png)

<span data-ttu-id="6852c-115">Per visualizzare la Quota di archiviazione per tutte le posizioni geografiche attuali, eseguire:</span><span class="sxs-lookup"><span data-stu-id="6852c-115">To view Storage Quota for all geo locations, run:</span></span>

`Get-SPOGeoStorageQuota -AllLocations`

<span data-ttu-id="6852c-116">Per rimuovere la quota di archiviazione assegnata ad una posizione geografica, impostare `StorageQuota value = 0`:</span><span class="sxs-lookup"><span data-stu-id="6852c-116">To remove the allocated storage quota for a geo location, set `StorageQuota value = 0`:</span></span>

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0`
