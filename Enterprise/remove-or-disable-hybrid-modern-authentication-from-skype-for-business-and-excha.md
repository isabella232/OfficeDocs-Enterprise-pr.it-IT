---
title: Rimozione o disabilitazione dell'autenticazione moderna ibrida da Skype for Business ed Exchange
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/3/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
description: Se è stato abilitato ibrida moderno autenticazione (alta) solo per trovare che è adatto per l'ambiente corrente, è possibile disattivare alta. In questo articolo viene illustrato come.
ms.openlocfilehash: fff9599641630386183ab9e1a0b8f597f0ba6e5b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541359"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="ee290-104">Rimozione o disabilitazione dell'autenticazione moderna ibrida da Skype for Business ed Exchange</span><span class="sxs-lookup"><span data-stu-id="ee290-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="ee290-p102">Se è stato abilitato ibrida moderno autenticazione (alta) solo per trovare che è adatto per l'ambiente corrente, è possibile disattivare alta. In questo articolo viene illustrato come.</span><span class="sxs-lookup"><span data-stu-id="ee290-p102">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA. This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="ee290-107">A chi è in questo articolo per?</span><span class="sxs-lookup"><span data-stu-id="ee290-107">Who is this article for?</span></span>

<span data-ttu-id="ee290-108">Se si è stata abilitata l'autenticazione moderno in Skype per Business Online o locale, e/o Exchange Online o locale e trovato che è necessario disabilitare alta, questi passaggi vengono automaticamente.</span><span class="sxs-lookup"><span data-stu-id="ee290-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>
  
 <span data-ttu-id="ee290-109">**Importante** Se si sta effettuando Skype per Business Online o locale, vedere l'articolo ' [Skype per le topologie di Business è supportato con l'autenticazione moderno](https://technet.microsoft.com/en-us/library/mt803262.aspx)', dispone di una topologia mista alta e necessario esaminare le topologie supportate prima di iniziare.</span><span class="sxs-lookup"><span data-stu-id="ee290-109">**Important** See the ' [Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="ee290-110">Come disabilitare l'autenticazione moderno ibrida (Exchange)</span><span class="sxs-lookup"><span data-stu-id="ee290-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="ee290-111">**Exchange in locale**: aprire Exchange Management Shell ed eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="ee290-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following command.</span></span> 
    
1. <span data-ttu-id="ee290-112">Set-OrganizationConfig-OAuth2ClientProfileEnabled $false</span><span class="sxs-lookup"><span data-stu-id="ee290-112">Set-OrganizationConfig -OAuth2ClientProfileEnabled $false</span></span>
    
2. <span data-ttu-id="ee290-113">Set-AuthServer-Identity evoSTS - IsDefaultAuthorizationEndpoint $false</span><span class="sxs-lookup"><span data-stu-id="ee290-113">Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false</span></span>
    
2. <span data-ttu-id="ee290-p103">**Exchange Online**: connettersi a Exchange Online PowerShell remoto. Eseguire il comando seguente per attivare il contrassegno *OAuth2ClientProfileEnabled* su 'false'.</span><span class="sxs-lookup"><span data-stu-id="ee290-p103">**Exchange Online**: Connect to Exchange Online with Remote PowerShell. Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false'.</span></span> 
    
1. <span data-ttu-id="ee290-116">Set-OrganizationConfig-OAuth2ClientProfileEnabled: $false</span><span class="sxs-lookup"><span data-stu-id="ee290-116">Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false</span></span>
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="ee290-117">Come disabilitare l'autenticazione moderno ibrida (Skype per le aziende)</span><span class="sxs-lookup"><span data-stu-id="ee290-117">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="ee290-118">**Skype aziendali locali**: eseguire i seguenti comandi in Skype per Business Management Shell.</span><span class="sxs-lookup"><span data-stu-id="ee290-118">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell.</span></span>
    
1. <span data-ttu-id="ee290-119">Set-CsOAuthConfiguration - ClientAuthorizationOAuthServerIdentity ""</span><span class="sxs-lookup"><span data-stu-id="ee290-119">Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""</span></span>
    
2. <span data-ttu-id="ee290-p104">**Skype per le aziende Online**: connettersi a Skype for Business in linea con Remote PowerShell. Eseguire il seguente comando per disabilitare l'autenticazione moderno.</span><span class="sxs-lookup"><span data-stu-id="ee290-p104">**Skype for Business Online**: Connect to Skype for Business Online with Remote PowerShell. Run the following command to disable Modern Authentication.</span></span> 
    
1. <span data-ttu-id="ee290-122">Set-CsOAuthConfiguration - ClientAdalAuthOverride non consentito</span><span class="sxs-lookup"><span data-stu-id="ee290-122">Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed</span></span>
    
<span data-ttu-id="ee290-123">[Collegamento a ritroso alla panoramica autenticazione moderno](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="ee290-123">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

