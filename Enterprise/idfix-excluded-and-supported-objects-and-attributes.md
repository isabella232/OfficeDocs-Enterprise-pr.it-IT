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
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Vengono elencati gli attributi esclusi e supportati dallo strumento IdFix.
ms.openlocfilehash: de8d57bb8ad9a3097ec9da3ff2a485095a140a42
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541266"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="a6b97-103">Oggetti e attributi esclusi e supportati di IdFix</span><span class="sxs-lookup"><span data-stu-id="a6b97-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="a6b97-p101">Sono disponibili due insiemi di regole mantenute da IdFix; Multi-tenant e Dedicati/ITAR. A questo punto, le due regole impostate escludono gli stessi oggetti, attributi e valori di attributi dalla ricerca. Ciò potrebbe cambiare nelle versioni future.</span><span class="sxs-lookup"><span data-stu-id="a6b97-p101">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR. At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search. This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="a6b97-107">Esclusione errori Multi-tenant e Dedicati utilizzate da IdFix</span><span class="sxs-lookup"><span data-stu-id="a6b97-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="a6b97-p102">In questa sezione sono elencati oggetti, attributi e valori IdFix esclude la ricerca di directory. L'asterisco (\*) è un carattere jolly che può essere sostituito da altri caratteri.</span><span class="sxs-lookup"><span data-stu-id="a6b97-p102">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory. The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="a6b97-110">Oggetti, attributi e valori esclusi durante una ricerca IdFix</span><span class="sxs-lookup"><span data-stu-id="a6b97-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="a6b97-111">**Esclusione**</span><span class="sxs-lookup"><span data-stu-id="a6b97-111">**Exclusion**</span></span>|<span data-ttu-id="a6b97-112">**Esempio**</span><span class="sxs-lookup"><span data-stu-id="a6b97-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a6b97-113">Sfrutti\*</span><span class="sxs-lookup"><span data-stu-id="a6b97-113">Admini\*</span></span> |<span data-ttu-id="a6b97-114">Amministratore</span><span class="sxs-lookup"><span data-stu-id="a6b97-114">Administrator</span></span> |
|<span data-ttu-id="a6b97-115">{CAS_\*</span><span class="sxs-lookup"><span data-stu-id="a6b97-115">CAS_{\*</span></span>  |<span data-ttu-id="a6b97-116">CAS_{fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="a6b97-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="a6b97-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="a6b97-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="a6b97-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="a6b97-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="a6b97-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="a6b97-119">FederatedEmail\*</span></span> |<span data-ttu-id="a6b97-p103">FederatedEmail. *GUID*</span><span class="sxs-lookup"><span data-stu-id="a6b97-p103">FederatedEmail. *GUID*</span></span> |
|<span data-ttu-id="a6b97-122">Guest\*</span><span class="sxs-lookup"><span data-stu-id="a6b97-122">Guest\*</span></span> ||
|<span data-ttu-id="a6b97-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="a6b97-123">HTTPConnector\*</span></span>  |<span data-ttu-id="a6b97-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="a6b97-124">HTTPConnector</span></span> |
|<span data-ttu-id="a6b97-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="a6b97-125">krbtgt\*</span></span> |<span data-ttu-id="a6b97-126">Collegamento ms-DS KrbTgt</span><span class="sxs-lookup"><span data-stu-id="a6b97-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="a6b97-127">IUSR _\*</span><span class="sxs-lookup"><span data-stu-id="a6b97-127">iusr_\*</span></span> |<span data-ttu-id="a6b97-128">IUSR _ *machinename*</span><span class="sxs-lookup"><span data-stu-id="a6b97-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="a6b97-129">IWAM\*</span><span class="sxs-lookup"><span data-stu-id="a6b97-129">iwam\*</span></span>  |<span data-ttu-id="a6b97-130">IWAM_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="a6b97-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="a6b97-131">msol\*</span><span class="sxs-lookup"><span data-stu-id="a6b97-131">msol\*</span></span> |<span data-ttu-id="a6b97-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="a6b97-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="a6b97-133">support_\*</span><span class="sxs-lookup"><span data-stu-id="a6b97-133">support_\*</span></span> ||
|<span data-ttu-id="a6b97-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="a6b97-134">SystemMailbox\*</span></span> |<span data-ttu-id="a6b97-135">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="a6b97-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="a6b97-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="a6b97-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="a6b97-137">distinguishedName contiene "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="a6b97-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="a6b97-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="a6b97-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="a6b97-139">L'oggetto contiene l'attributo IsCriticalSystemObject</span><span class="sxs-lookup"><span data-stu-id="a6b97-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="a6b97-140">Vedere [attributo isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="a6b97-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="a6b97-141">Oggetti e attributi Multi-Tenant e Dedicati verificati da IdFix</span><span class="sxs-lookup"><span data-stu-id="a6b97-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="a6b97-142">Nella sezione "Oggetti e attributi preparazione Directory" in [Prepare gli attributi di directory per la sincronizzazione con Office 365 tramite lo strumento IdFix](prepare-directory-attributes-for-synch-with-idfix.md)sono descritti gli attributi che vengono controllati per gli errori da IdFix.</span><span class="sxs-lookup"><span data-stu-id="a6b97-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

