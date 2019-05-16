---
title: Rimozione o disabilitazione dell'autenticazione moderna ibrida da Skype for Business ed Exchange
ms.author: tracyp
author: MSFTTracyP
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
description: Se è stata abilitata l'autenticazione moderna ibrida (HMA) solo per scoprire che non è adatta per l'ambiente corrente, è possibile disabilitare HMA. In questo articolo viene illustrato come.
ms.openlocfilehash: 011e24c546fede11177e49ce8b36599d7d81d121
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070982"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Rimozione o disabilitazione dell'autenticazione moderna ibrida da Skype for Business ed Exchange

Se è stata abilitata l'autenticazione moderna ibrida (HMA) solo per scoprire che non è adatta per l'ambiente corrente, è possibile disabilitare HMA. In questo articolo viene illustrato come.
  
## <a name="who-is-this-article-for"></a>Per chi è questo articolo?

Se è stata abilitata l'autenticazione moderna in Skype for business online o locale e/o Exchange Online o in locale e si è trovato che è necessario disabilitare HMA, questi passaggi sono disponibili per l'utente.

> [!IMPORTANT]
> Vedere l'articolo relativo alle topologie di[Skype for business supportate con l'autenticazione moderna](https://technet.microsoft.com/en-us/library/mt803262.aspx)se si è in Skype for business online o in locale, è presente una HMA a topologia mista ed è necessario esaminare le topologie supportate prima di iniziare.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Come disabilitare l'autenticazione moderna ibrida (Exchange)

1. **Exchange locale**: aprire Exchange Management Shell ed eseguire i comandi seguenti: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [connettersi a Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) con Remote PowerShell. Eseguire il seguente comando per trasformare il flag *OAuth2ClientProfileEnabled* su' false ':

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Come disabilitare l'autenticazione moderna ibrida (Skype for business)

1. **Skype for business locale**: eseguire i comandi seguenti in Skype for Business Management Shell:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype for business online**: [connettersi a Skype for business online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) con Remote PowerShell. Eseguire il seguente comando per disabilitare l'autenticazione moderna:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Collegare di nuovo la panoramica dell'autenticazione moderna](hybrid-modern-auth-overview.md) . 
  

