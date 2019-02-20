---
title: Oggetti e attributi esclusi e supportati di IdFix
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
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
ms.openlocfilehash: d6b7aac023e9fe96b8308483322e718937ab1355
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085085"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="0c6c9-103">Oggetti e attributi esclusi e supportati di IdFix</span><span class="sxs-lookup"><span data-stu-id="0c6c9-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="0c6c9-p101">Sono disponibili due insiemi di regole mantenute da IdFix; Multi-tenant e Dedicati/ITAR. A questo punto, le due regole impostate escludono gli stessi oggetti, attributi e valori di attributi dalla ricerca. Ciò potrebbe cambiare nelle versioni future.</span><span class="sxs-lookup"><span data-stu-id="0c6c9-p101">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR. At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search. This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="0c6c9-107">Esclusione errori Multi-tenant e Dedicati utilizzate da IdFix</span><span class="sxs-lookup"><span data-stu-id="0c6c9-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="0c6c9-p102">In questa sezione vengono elencati gli oggetti, gli attributi e i valori che IdFix esclude dalla ricerca della directory. L'asterisco (\*) è un carattere jolly che può essere sostituito da altri caratteri.</span><span class="sxs-lookup"><span data-stu-id="0c6c9-p102">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory. The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="0c6c9-110">Oggetti, attributi e valori esclusi durante una ricerca IdFix</span><span class="sxs-lookup"><span data-stu-id="0c6c9-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="0c6c9-111">**Esclusione**</span><span class="sxs-lookup"><span data-stu-id="0c6c9-111">**Exclusion**</span></span>|<span data-ttu-id="0c6c9-112">**Esempio**</span><span class="sxs-lookup"><span data-stu-id="0c6c9-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="0c6c9-113">Scelta\*</span><span class="sxs-lookup"><span data-stu-id="0c6c9-113">Admini\*</span></span> |<span data-ttu-id="0c6c9-114">Amministratore</span><span class="sxs-lookup"><span data-stu-id="0c6c9-114">Administrator</span></span> |
|<span data-ttu-id="0c6c9-115">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="0c6c9-115">CAS_{\*</span></span>  |<span data-ttu-id="0c6c9-116">CAS_{fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="0c6c9-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="0c6c9-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="0c6c9-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="0c6c9-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="0c6c9-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="0c6c9-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="0c6c9-119">FederatedEmail\*</span></span> |<span data-ttu-id="0c6c9-p103">FederatedEmail. *GUID*</span><span class="sxs-lookup"><span data-stu-id="0c6c9-p103">FederatedEmail. *GUID*</span></span> |
|<span data-ttu-id="0c6c9-122">Guest\*</span><span class="sxs-lookup"><span data-stu-id="0c6c9-122">Guest\*</span></span> ||
|<span data-ttu-id="0c6c9-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="0c6c9-123">HTTPConnector\*</span></span>  |<span data-ttu-id="0c6c9-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="0c6c9-124">HTTPConnector</span></span> |
|<span data-ttu-id="0c6c9-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="0c6c9-125">krbtgt\*</span></span> |<span data-ttu-id="0c6c9-126">ms-DS-KrbTgt-Link</span><span class="sxs-lookup"><span data-stu-id="0c6c9-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="0c6c9-127">IUSR\*</span><span class="sxs-lookup"><span data-stu-id="0c6c9-127">iusr_\*</span></span> |<span data-ttu-id="0c6c9-128">IUSR _ *machineName*</span><span class="sxs-lookup"><span data-stu-id="0c6c9-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="0c6c9-129">IWAM\*</span><span class="sxs-lookup"><span data-stu-id="0c6c9-129">iwam\*</span></span>  |<span data-ttu-id="0c6c9-130">IWAM_ *nomecomputer*</span><span class="sxs-lookup"><span data-stu-id="0c6c9-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="0c6c9-131">MSOL\*</span><span class="sxs-lookup"><span data-stu-id="0c6c9-131">msol\*</span></span> |<span data-ttu-id="0c6c9-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="0c6c9-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="0c6c9-133">supporto\*</span><span class="sxs-lookup"><span data-stu-id="0c6c9-133">support_\*</span></span> ||
|<span data-ttu-id="0c6c9-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="0c6c9-134">SystemMailbox\*</span></span> |<span data-ttu-id="0c6c9-135">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="0c6c9-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="0c6c9-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="0c6c9-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="0c6c9-137">distinto contiene "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="0c6c9-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="0c6c9-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="0c6c9-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="0c6c9-139">L'oggetto contiene l'attributo IsCriticalSystemObject</span><span class="sxs-lookup"><span data-stu-id="0c6c9-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="0c6c9-140">Vedere [attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="0c6c9-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="0c6c9-141">Oggetti e attributi Multi-Tenant e Dedicati verificati da IdFix</span><span class="sxs-lookup"><span data-stu-id="0c6c9-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="0c6c9-142">Gli attributi che vengono controllati per gli errori da IdFix sono descritti nella sezione "preparazione degli attributi e degli oggetti directory" in [Prepare Directory Attributes for Synchronization with Office 365 by using the IdFix Tool](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="0c6c9-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

