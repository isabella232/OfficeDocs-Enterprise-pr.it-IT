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
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Elenca gli attributi che sono esclusi e supportati dallo strumento IdFix.
ms.openlocfilehash: bf88fea3592860a89d69717177593b6553318ee4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067272"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="146e3-103">Oggetti e attributi esclusi e supportati da</span><span class="sxs-lookup"><span data-stu-id="146e3-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="146e3-p101">Sono disponibili due insiemi di regole mantenute da IdFix; Multi-tenant e Dedicati/ITAR. A questo punto, le due regole impostate escludono gli stessi oggetti, attributi e valori di attributi dalla ricerca. Ciò potrebbe cambiare nelle versioni future.</span><span class="sxs-lookup"><span data-stu-id="146e3-p101">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR. At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search. This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="146e3-107">Esclusione errori Multi-tenant e Dedicati utilizzate da IdFix</span><span class="sxs-lookup"><span data-stu-id="146e3-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="146e3-108">Questa sezione elenca oggetti, attributi e valori esclusi da IdFix dalla propria ricerca della directory.</span><span class="sxs-lookup"><span data-stu-id="146e3-108">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="146e3-109">L'asterisco (\*) è un carattere jolly che può essere sostituito da altri caratteri.</span><span class="sxs-lookup"><span data-stu-id="146e3-109">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="146e3-110">Oggetti, attributi e valori esclusi durante una ricerca IdFix</span><span class="sxs-lookup"><span data-stu-id="146e3-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="146e3-111">**Esclusione**</span><span class="sxs-lookup"><span data-stu-id="146e3-111">**Exclusion**</span></span>|<span data-ttu-id="146e3-112">**Esempio**</span><span class="sxs-lookup"><span data-stu-id="146e3-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="146e3-113">Scelta\*</span><span class="sxs-lookup"><span data-stu-id="146e3-113">Admini\*</span></span> |<span data-ttu-id="146e3-114">Amministratore</span><span class="sxs-lookup"><span data-stu-id="146e3-114">Administrator</span></span> |
|<span data-ttu-id="146e3-115">CAS_{\*</span><span class="sxs-lookup"><span data-stu-id="146e3-115">CAS_{\*</span></span>  |<span data-ttu-id="146e3-116">CAS_{fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="146e3-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="146e3-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="146e3-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="146e3-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="146e3-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="146e3-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="146e3-119">FederatedEmail\*</span></span> |<span data-ttu-id="146e3-120">FederatedEmail.</span><span class="sxs-lookup"><span data-stu-id="146e3-120">FederatedEmail.</span></span> <span data-ttu-id="146e3-121">*GUID*</span><span class="sxs-lookup"><span data-stu-id="146e3-121">*GUID*</span></span> |
|<span data-ttu-id="146e3-122">Guest\*</span><span class="sxs-lookup"><span data-stu-id="146e3-122">Guest\*</span></span> ||
|<span data-ttu-id="146e3-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="146e3-123">HTTPConnector\*</span></span>  |<span data-ttu-id="146e3-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="146e3-124">HTTPConnector</span></span> |
|<span data-ttu-id="146e3-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="146e3-125">krbtgt\*</span></span> |<span data-ttu-id="146e3-126">ms-DS-KrbTgt-Link</span><span class="sxs-lookup"><span data-stu-id="146e3-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="146e3-127">IUSR\*</span><span class="sxs-lookup"><span data-stu-id="146e3-127">iusr_\*</span></span> |<span data-ttu-id="146e3-128">IUSR _ *machineName*</span><span class="sxs-lookup"><span data-stu-id="146e3-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="146e3-129">IWAM\*</span><span class="sxs-lookup"><span data-stu-id="146e3-129">iwam\*</span></span>  |<span data-ttu-id="146e3-130">IWAM_ *nomecomputer*</span><span class="sxs-lookup"><span data-stu-id="146e3-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="146e3-131">MSOL\*</span><span class="sxs-lookup"><span data-stu-id="146e3-131">msol\*</span></span> |<span data-ttu-id="146e3-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="146e3-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="146e3-133">supporto\*</span><span class="sxs-lookup"><span data-stu-id="146e3-133">support_\*</span></span> ||
|<span data-ttu-id="146e3-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="146e3-134">SystemMailbox\*</span></span> |<span data-ttu-id="146e3-135">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="146e3-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="146e3-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="146e3-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="146e3-137">distinto contiene "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="146e3-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="146e3-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="146e3-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="146e3-139">L'oggetto contiene l'attributo IsCriticalSystemObject</span><span class="sxs-lookup"><span data-stu-id="146e3-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="146e3-140">Vedere [attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="146e3-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="146e3-141">Oggetti e attributi Multi-Tenant e Dedicati verificati da IdFix</span><span class="sxs-lookup"><span data-stu-id="146e3-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="146e3-142">Gli attributi che vengono controllati per gli errori da IdFix sono descritti nella sezione "preparazione degli attributi e degli oggetti directory" in [Prepare Directory Attributes for Synchronization with Office 365 by using the IdFix Tool](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="146e3-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

