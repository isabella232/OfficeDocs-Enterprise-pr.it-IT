---
title: Limitare il contenuto a una posizione geografica
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Informazioni su come limitare i siti di SharePoint a una specifica posizione geografica in un ambiente multi-geo.
ms.openlocfilehash: 59301a591e5465bdcda4aa84a18880961c0b615b
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2019
ms.locfileid: "30934020"
---
# <a name="restrict-content-to-a-geo-location"></a><span data-ttu-id="f726c-103">Limitare il contenuto a una posizione geografica</span><span class="sxs-lookup"><span data-stu-id="f726c-103">Restrict content to a geo location</span></span>

<span data-ttu-id="f726c-104">In alcuni casi è possibile applicare a un sito e il contenuto del file per mantenere la posizione geografica in cui è stato creato il sito, e non lo spostamento del sito o impedire la memorizzazione nella cache del contenuto del sito in un'altra posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="f726c-104">Under some circumstances you may choose to enforce a site and its file content to remain in the geo location where the site was created, either by preventing the site from being moved or by preventing the caching of the site's file content in another geo location.</span></span>

<span data-ttu-id="f726c-105">È possibile farlo usando il cmdlet [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) con il parametro **RestrictedToGeo**.</span><span class="sxs-lookup"><span data-stu-id="f726c-105">You can do this by using the [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) cmdlet with the **RestrictedToGeo** parameter.</span></span> <span data-ttu-id="f726c-106">Questo parametro ha un valore predefinito NULL, ma è possibile sostituirlo con una delle opzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f726c-106">This parameter has a default value of NULL, but you can change it to one of the following:</span></span>

|<span data-ttu-id="f726c-107">Restrizione</span><span class="sxs-lookup"><span data-stu-id="f726c-107">Restriction</span></span>|<span data-ttu-id="f726c-108">Descrizione</span><span class="sxs-lookup"><span data-stu-id="f726c-108">Description</span></span>|
|:----------|:----------|
|<span data-ttu-id="f726c-109">NoRestriction</span><span class="sxs-lookup"><span data-stu-id="f726c-109">NoRestriction</span></span>|<span data-ttu-id="f726c-110">Il sito può essere spostato in un'altra posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="f726c-110">The site can be moved to another geo location.</span></span>|
|<span data-ttu-id="f726c-111">BlockMoveOnly</span><span class="sxs-lookup"><span data-stu-id="f726c-111">BlockMoveOnly</span></span>|<span data-ttu-id="f726c-112">I siti non possono essere spostati in un'altra posizione geografica, ma il contenuto dei siti può essere memorizzato nella cache in altre posizioni geografiche.</span><span class="sxs-lookup"><span data-stu-id="f726c-112">Site cannot be moved to another geo location, but site content can be cached in other geo locations.</span></span>|
|<span data-ttu-id="f726c-113">BlockFull</span><span class="sxs-lookup"><span data-stu-id="f726c-113">BlockFull</span></span>|<span data-ttu-id="f726c-114">I siti non possono essere spostati in un'altra posizione geografica e l’intero contenuto del file non viene memorizzato nella cache in altre posizioni geografiche.</span><span class="sxs-lookup"><span data-stu-id="f726c-114">Site cannot be moved to another geo location, and full file content is not cached in other geo locations.</span></span> <span data-ttu-id="f726c-115">Il titolo dei file (raccolto dal contenuto), il nome del file e altre sue proprietà possono comunque essere memorizzate nella cache in altre posizioni geografiche.</span><span class="sxs-lookup"><span data-stu-id="f726c-115">Files' title (harvested from the content), file name, and other properties of the file can still be cached in other geo-locations.</span></span><br><span data-ttu-id="f726c-116">Il contenuto del sito prima che fosse configurato per BlockFull, potrebbe continuare a essere memorizzato nella cache in altre località geografiche.</span><span class="sxs-lookup"><span data-stu-id="f726c-116">Content stored in the site before it was configured to BlockFull, may continue to be cached in other geo locations.</span></span>|

<span data-ttu-id="f726c-117">Utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="f726c-117">Use the following syntax:</span></span>

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

<span data-ttu-id="f726c-118">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f726c-118">For example:</span></span>

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`
