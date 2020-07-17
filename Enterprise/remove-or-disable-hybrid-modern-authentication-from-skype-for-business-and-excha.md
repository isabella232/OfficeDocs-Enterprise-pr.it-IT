---
title: Rimozione o disabilitazione dell'autenticazione moderna ibrida da Skype for Business ed Exchange
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: Se è stata abilitata l'autenticazione moderna ibrida (HMA) solo per scoprire che non è adatta per l'ambiente corrente, è possibile disabilitare HMA. In questo articolo viene illustrato come.
ms.openlocfilehash: ad9db5894670b49d2d9a1f385cd9f6acd43ea00f
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998205"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="2fc7d-104">Rimozione o disabilitazione dell'autenticazione moderna ibrida da Skype for Business ed Exchange</span><span class="sxs-lookup"><span data-stu-id="2fc7d-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="2fc7d-105">*Questo articolo si applica sia a Microsoft 365 Enterprise che a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="2fc7d-105">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="2fc7d-106">Se è stata abilitata l'autenticazione moderna ibrida (HMA) solo per scoprire che non è adatta per l'ambiente corrente, è possibile disabilitare HMA.</span><span class="sxs-lookup"><span data-stu-id="2fc7d-106">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA.</span></span> <span data-ttu-id="2fc7d-107">In questo articolo viene illustrato come.</span><span class="sxs-lookup"><span data-stu-id="2fc7d-107">This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="2fc7d-108">Per chi è questo articolo?</span><span class="sxs-lookup"><span data-stu-id="2fc7d-108">Who is this article for?</span></span>

<span data-ttu-id="2fc7d-109">Se è stata abilitata l'autenticazione moderna in Skype for business online o locale e/o Exchange Online o in locale e si è trovato che è necessario disabilitare HMA, questi passaggi sono disponibili per l'utente.</span><span class="sxs-lookup"><span data-stu-id="2fc7d-109">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2fc7d-110">Vedere l'articolo relativo alle topologie di[Skype for business supportate con l'autenticazione moderna](https://technet.microsoft.com/library/mt803262.aspx)se si è in Skype for business online o in locale, è presente una HMA a topologia mista ed è necessario esaminare le topologie supportate prima di iniziare.</span><span class="sxs-lookup"><span data-stu-id="2fc7d-110">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="2fc7d-111">Come disabilitare l'autenticazione moderna ibrida (Exchange)</span><span class="sxs-lookup"><span data-stu-id="2fc7d-111">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="2fc7d-112">**Exchange locale**: aprire Exchange Management Shell ed eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="2fc7d-112">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="2fc7d-113">**Exchange Online**: [connettersi a Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) con Remote PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fc7d-113">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="2fc7d-114">Eseguire il seguente comando per trasformare il flag *OAuth2ClientProfileEnabled* su' false ':</span><span class="sxs-lookup"><span data-stu-id="2fc7d-114">Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="2fc7d-115">Come disabilitare l'autenticazione moderna ibrida (Skype for business)</span><span class="sxs-lookup"><span data-stu-id="2fc7d-115">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="2fc7d-116">**Skype for business locale**: eseguire i comandi seguenti in Skype for Business Management Shell:</span><span class="sxs-lookup"><span data-stu-id="2fc7d-116">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="2fc7d-117">**Skype for business online**: [connettersi a Skype for business online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) con Remote PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fc7d-117">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="2fc7d-118">Eseguire il seguente comando per disabilitare l'autenticazione moderna:</span><span class="sxs-lookup"><span data-stu-id="2fc7d-118">Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="2fc7d-119">[Collegare di nuovo la panoramica dell'autenticazione moderna](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="2fc7d-119">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

