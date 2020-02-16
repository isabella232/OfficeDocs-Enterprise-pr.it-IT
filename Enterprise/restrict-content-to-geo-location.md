---
title: Limitare il contenuto del sito di SharePoint a una posizione geografica
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
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Informazioni su come limitare i siti di SharePoint a una specifica posizione geografica in un ambiente multi-geo.
ms.openlocfilehash: ca63f46ba45d1b3ddfdf4f676b678d62387b801f
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2020
ms.locfileid: "41973958"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a><span data-ttu-id="8f820-103">Limitare il contenuto del sito di SharePoint a una posizione geografica</span><span class="sxs-lookup"><span data-stu-id="8f820-103">Restrict SharePoint site content to a geo location</span></span>

<span data-ttu-id="8f820-104">In alcuni casi è possibile applicare a un sito e il contenuto del file per mantenere la posizione geografica in cui è stato creato il sito, e non lo spostamento del sito o impedire la memorizzazione nella cache del contenuto del sito in un'altra posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="8f820-104">Under some circumstances you may choose to enforce a site and its file content to remain in the geo location where the site was created, either by preventing the site from being moved or by preventing the caching of the site's file content in another geo location.</span></span>

<span data-ttu-id="8f820-105">È possibile farlo usando il cmdlet [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) con il parametro **RestrictedToGeo**.</span><span class="sxs-lookup"><span data-stu-id="8f820-105">You can do this by using the [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) cmdlet with the **RestrictedToGeo** parameter.</span></span> <span data-ttu-id="8f820-106">Questo parametro ha un valore predefinito NULL, ma è possibile sostituirlo con una delle opzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="8f820-106">This parameter has a default value of NULL, but you can change it to one of the following:</span></span>

|<span data-ttu-id="8f820-107">Restrizione</span><span class="sxs-lookup"><span data-stu-id="8f820-107">Restriction</span></span>|<span data-ttu-id="8f820-108">Descrizione</span><span class="sxs-lookup"><span data-stu-id="8f820-108">Description</span></span>|
|:----------|:----------|
|<span data-ttu-id="8f820-109">NoRestriction</span><span class="sxs-lookup"><span data-stu-id="8f820-109">NoRestriction</span></span>|<span data-ttu-id="8f820-110">Il sito può essere spostato in un'altra posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="8f820-110">The site can be moved to another geo location.</span></span>|
|<span data-ttu-id="8f820-111">BlockMoveOnly</span><span class="sxs-lookup"><span data-stu-id="8f820-111">BlockMoveOnly</span></span>|<span data-ttu-id="8f820-112">I siti non possono essere spostati in un'altra posizione geografica, ma il contenuto dei siti può essere memorizzato nella cache in altre posizioni geografiche.</span><span class="sxs-lookup"><span data-stu-id="8f820-112">Site cannot be moved to another geo location, but site content can be cached in other geo locations.</span></span>|
|<span data-ttu-id="8f820-113">BlockFull</span><span class="sxs-lookup"><span data-stu-id="8f820-113">BlockFull</span></span>|<span data-ttu-id="8f820-114">I siti non possono essere spostati in un'altra posizione geografica e l’intero contenuto del file non viene memorizzato nella cache in altre posizioni geografiche.</span><span class="sxs-lookup"><span data-stu-id="8f820-114">Site cannot be moved to another geo location, and full file content is not cached in other geo locations.</span></span> <span data-ttu-id="8f820-115">Il titolo dei file (raccolto dal contenuto), il nome del file e altre sue proprietà possono comunque essere memorizzate nella cache in altre posizioni geografiche.</span><span class="sxs-lookup"><span data-stu-id="8f820-115">Files' title (harvested from the content), file name, and other properties of the file can still be cached in other geo-locations.</span></span><br><span data-ttu-id="8f820-116">Il contenuto del sito prima che fosse configurato per BlockFull, potrebbe continuare a essere memorizzato nella cache in altre località geografiche.</span><span class="sxs-lookup"><span data-stu-id="8f820-116">Content stored in the site before it was configured to BlockFull, may continue to be cached in other geo locations.</span></span>|

<span data-ttu-id="8f820-117">Utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="8f820-117">Use the following syntax:</span></span>

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

<span data-ttu-id="8f820-118">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="8f820-118">For example:</span></span>

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`
