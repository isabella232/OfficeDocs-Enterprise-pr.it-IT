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
ms.openlocfilehash: 802add6295edffe3ec80e70e9bd70663479ec61a
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "25359028"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="b1d51-104">Rimozione o disabilitazione dell'autenticazione moderna ibrida da Skype for Business ed Exchange</span><span class="sxs-lookup"><span data-stu-id="b1d51-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="b1d51-p102">Se è stato abilitato ibrida moderno autenticazione (alta) solo per trovare che è adatto per l'ambiente corrente, è possibile disattivare alta. In questo articolo viene illustrato come.</span><span class="sxs-lookup"><span data-stu-id="b1d51-p102">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA. This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="b1d51-107">A chi è in questo articolo per?</span><span class="sxs-lookup"><span data-stu-id="b1d51-107">Who is this article for?</span></span>

<span data-ttu-id="b1d51-108">Se si è stata abilitata l'autenticazione moderno in Skype per Business Online o locale, e/o Exchange Online o locale e trovato che è necessario disabilitare alta, questi passaggi vengono automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b1d51-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b1d51-109">Se si sta effettuando Skype per Business Online o locale, vedere l'articolo '[Skype per le topologie di Business è supportato con l'autenticazione moderno](https://technet.microsoft.com/en-us/library/mt803262.aspx)', dispone di una topologia mista alta e necessario esaminare le topologie supportate prima di iniziare.</span><span class="sxs-lookup"><span data-stu-id="b1d51-109">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="b1d51-110">Come disabilitare l'autenticazione moderno ibrida (Exchange)</span><span class="sxs-lookup"><span data-stu-id="b1d51-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="b1d51-111">**Exchange in locale**: aprire Exchange Management Shell ed eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="b1d51-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="b1d51-p103">**Exchange Online**: [connessione a Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) PowerShell remoto. Eseguire il comando seguente per attivare il contrassegno *OAuth2ClientProfileEnabled* su 'false':</span><span class="sxs-lookup"><span data-stu-id="b1d51-p103">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell. Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="b1d51-114">Come disabilitare l'autenticazione moderno ibrida (Skype per le aziende)</span><span class="sxs-lookup"><span data-stu-id="b1d51-114">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="b1d51-115">**Skype aziendali locali**: eseguire i seguenti comandi in Skype per Business Management Shell:</span><span class="sxs-lookup"><span data-stu-id="b1d51-115">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="b1d51-p104">**Skype per le aziende Online**: [connettersi a Skype for Business in linea](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) con Remote PowerShell. Eseguire il seguente comando per disabilitare l'autenticazione moderno:</span><span class="sxs-lookup"><span data-stu-id="b1d51-p104">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell. Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="b1d51-118">[Collegamento a ritroso alla panoramica autenticazione moderno](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="b1d51-118">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

