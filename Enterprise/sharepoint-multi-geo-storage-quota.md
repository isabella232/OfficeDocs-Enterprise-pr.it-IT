---
title: Quote di archiviazione di SharePoint in ambienti multi-geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Informazioni sulle Quote di archiviazione di SharePoint in ambienti multi-geo.
ms.openlocfilehash: 9c43f21a844507c4de7971d70a110665ddc094ba
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2019
ms.locfileid: "30934019"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a><span data-ttu-id="d467f-103">Quote di archiviazione di SharePoint in ambienti multi-geo</span><span class="sxs-lookup"><span data-stu-id="d467f-103">SharePoint storage quotas in multi-geo environments</span></span>

<span data-ttu-id="d467f-104">Per impostazione predefinita, tutti i percorsi di un ambiente multi-geo condividono la Quota di archiviazione disponibile per il tenant.</span><span class="sxs-lookup"><span data-stu-id="d467f-104">By default, all geo locations of a multi-geo environment share the available tenant storage quota.</span></span>

<span data-ttu-id="d467f-105">Con l'impostazione di quota di archiviazione geografica di SharePoint, è possibile gestire la Quota di archiviazione per ogni posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="d467f-105">With the SharePoint geo storage quota setting, you can manage the storage quota for each geo location.</span></span> <span data-ttu-id="d467f-106">Quando si assegna una quota di archiviazione per una posizione geografica, diventa la quantità massima di spazio di archiviazione disponibile per quella posizione geografica e viene sottratta dalla Quota di archiviazione disponibile per il tenant.</span><span class="sxs-lookup"><span data-stu-id="d467f-106">When you allocate a storage quota for a geo location, it becomes the maximum amount of storage available for that geo location, and is deducted from the available tenant storage quota.</span></span> <span data-ttu-id="d467f-107">La Quota di archiviazione disponibile per il tenant rimanente verrà quindi condivisa tra le posizioni geografiche configurate a cui non è stata assegnata una quota di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="d467f-107">The remaining available tenant storage quota is then shared across the configured geo locations for which a specific storage quota has not been allocated.</span></span>

<span data-ttu-id="d467f-108">La Quota di archiviazione di SharePoint per qualsiasi posizione geografica può essere assegnata dall'amministratore di SharePoint Online connettendosi alla posizione centrale.</span><span class="sxs-lookup"><span data-stu-id="d467f-108">The SharePoint storage quota for any geo location can be allocated by the SharePoint Online administrator by connecting to the central location.</span></span> <span data-ttu-id="d467f-109">Gli amministratori di posizioni geografiche satellitari possono visualizzare la Quota di archiviazione, ma non possono assegnarla.</span><span class="sxs-lookup"><span data-stu-id="d467f-109">Geo administrators for satellite locations can view the storage quota but cannot allocate it.</span></span>

## <a name="configure-a-storage-quota-for-a-geo-location"></a><span data-ttu-id="d467f-110">Configurare una quota di archiviazione per una posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="d467f-110">Configure a storage quota for a geo location</span></span>

<span data-ttu-id="d467f-111">Usare il [Modulo di Microsoft Office SharePoint Online](https://www.microsoft.com/en-us/download/details.aspx?id=35588 ) e connettersi alla posizione centrale per assegnare la Quota di archiviazione ad una posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="d467f-111">Use the [Microsoft SharePoint Online Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588 ) and connect to the central location to allocate the storage quota for a geo location.</span></span> 

<span data-ttu-id="d467f-112">Per assegnare una Quota di archiviazione ad un percorso, eseguire il cmdlet:</span><span class="sxs-lookup"><span data-stu-id="d467f-112">To allocate Storage Quota for a location, run cmdlet:</span></span>

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>`

<span data-ttu-id="d467f-113">Per visualizzare la Quota di archiviazione della posizione geografica attuale, eseguire:</span><span class="sxs-lookup"><span data-stu-id="d467f-113">To view Storage Quota for the current geo location, run:</span></span>

`Get-SPOGeoStorageQuota`

![Schermata della finestra di PowerShell che mostra il cmdlet Get-SPOGeoStorageQuota](media/multi-geo-storage-quota.png)

<span data-ttu-id="d467f-115">Per visualizzare la Quota di archiviazione per tutte le posizioni geografiche attuali, eseguire:</span><span class="sxs-lookup"><span data-stu-id="d467f-115">To view Storage Quota for all geo locations, run:</span></span>

`Get-SPOGeoStorageQuota -AllLocations`

<span data-ttu-id="d467f-116">Per rimuovere la quota di archiviazione assegnata ad una posizione geografica, impostare `StorageQuota value = 0`:</span><span class="sxs-lookup"><span data-stu-id="d467f-116">To remove the allocated storage quota for a geo location, set `StorageQuota value = 0`:</span></span>

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0`