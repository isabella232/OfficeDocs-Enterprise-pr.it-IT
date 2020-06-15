---
title: Oggetti e attributi esclusi e supportati da
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Elenca gli attributi che sono esclusi e supportati dallo strumento IdFix.
ms.openlocfilehash: da9a59d60b1ae2f1f68803e5a10afba16207fc69
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711576"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="b2f11-103">Oggetti e attributi esclusi e supportati da</span><span class="sxs-lookup"><span data-stu-id="b2f11-103">IdFix excluded and supported objects and attributes</span></span>

<span data-ttu-id="b2f11-104">*Questo articolo si applica sia a Microsoft 365 Enterprise che a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="b2f11-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="b2f11-p101">Sono disponibili due insiemi di regole mantenute da IdFix; Multi-tenant e Dedicati/ITAR. A questo punto, le due regole impostate escludono gli stessi oggetti, attributi e valori di attributi dalla ricerca. Ciò potrebbe cambiare nelle versioni future.</span><span class="sxs-lookup"><span data-stu-id="b2f11-p101">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR. At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search. This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="b2f11-108">Esclusione errori Multi-tenant e Dedicati utilizzate da IdFix</span><span class="sxs-lookup"><span data-stu-id="b2f11-108">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="b2f11-109">Questa sezione elenca oggetti, attributi e valori esclusi da IdFix dalla propria ricerca della directory.</span><span class="sxs-lookup"><span data-stu-id="b2f11-109">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="b2f11-110">L'asterisco ( \* ) è un carattere jolly che può essere sostituito da altri caratteri.</span><span class="sxs-lookup"><span data-stu-id="b2f11-110">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="b2f11-111">Oggetti, attributi e valori esclusi durante una ricerca IdFix</span><span class="sxs-lookup"><span data-stu-id="b2f11-111">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="b2f11-112">**Esclusione**</span><span class="sxs-lookup"><span data-stu-id="b2f11-112">**Exclusion**</span></span>|<span data-ttu-id="b2f11-113">**Esempio**</span><span class="sxs-lookup"><span data-stu-id="b2f11-113">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="b2f11-114">Scelta\*</span><span class="sxs-lookup"><span data-stu-id="b2f11-114">Admini\*</span></span> |<span data-ttu-id="b2f11-115">Amministratore</span><span class="sxs-lookup"><span data-stu-id="b2f11-115">Administrator</span></span> |
|<span data-ttu-id="b2f11-116">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="b2f11-116">CAS_{\*</span></span>  |<span data-ttu-id="b2f11-117">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="b2f11-117">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="b2f11-118">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="b2f11-118">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="b2f11-119">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="b2f11-119">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="b2f11-120">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="b2f11-120">FederatedEmail\*</span></span> |<span data-ttu-id="b2f11-121">FederatedEmail.</span><span class="sxs-lookup"><span data-stu-id="b2f11-121">FederatedEmail.</span></span> <span data-ttu-id="b2f11-122">*GUID*</span><span class="sxs-lookup"><span data-stu-id="b2f11-122">*GUID*</span></span> |
|<span data-ttu-id="b2f11-123">Guest\*</span><span class="sxs-lookup"><span data-stu-id="b2f11-123">Guest\*</span></span> ||
|<span data-ttu-id="b2f11-124">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="b2f11-124">HTTPConnector\*</span></span>  |<span data-ttu-id="b2f11-125">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="b2f11-125">HTTPConnector</span></span> |
|<span data-ttu-id="b2f11-126">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="b2f11-126">krbtgt\*</span></span> |<span data-ttu-id="b2f11-127">ms-DS-KrbTgt-Link</span><span class="sxs-lookup"><span data-stu-id="b2f11-127">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="b2f11-128">iusr_\*</span><span class="sxs-lookup"><span data-stu-id="b2f11-128">iusr_\*</span></span> |<span data-ttu-id="b2f11-129">iusr_ *nomecomputer*</span><span class="sxs-lookup"><span data-stu-id="b2f11-129">iusr_ *machinename*</span></span> |
|<span data-ttu-id="b2f11-130">IWAM\*</span><span class="sxs-lookup"><span data-stu-id="b2f11-130">iwam\*</span></span>  |<span data-ttu-id="b2f11-131">IWAM_ *nomecomputer*</span><span class="sxs-lookup"><span data-stu-id="b2f11-131">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="b2f11-132">MSOL\*</span><span class="sxs-lookup"><span data-stu-id="b2f11-132">msol\*</span></span> |<span data-ttu-id="b2f11-133">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="b2f11-133">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="b2f11-134">support_\*</span><span class="sxs-lookup"><span data-stu-id="b2f11-134">support_\*</span></span> ||
|<span data-ttu-id="b2f11-135">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="b2f11-135">SystemMailbox\*</span></span> |<span data-ttu-id="b2f11-136">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="b2f11-136">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="b2f11-137">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="b2f11-137">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="b2f11-138">distinto contiene "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="b2f11-138">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="b2f11-139">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="b2f11-139">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="b2f11-140">L'oggetto contiene l'attributo IsCriticalSystemObject</span><span class="sxs-lookup"><span data-stu-id="b2f11-140">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="b2f11-141">Vedere [attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="b2f11-141">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="b2f11-142">Oggetti e attributi Multi-Tenant e Dedicati verificati da IdFix</span><span class="sxs-lookup"><span data-stu-id="b2f11-142">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="b2f11-143">Gli attributi che vengono controllati per gli errori da IdFix sono descritti nella sezione "preparazione degli attributi e degli oggetti directory" in [Prepare Directory Attributes for Synchronization with Microsoft 365 by using the IdFix Tool](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="b2f11-143">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Microsoft 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

