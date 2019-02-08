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
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Rimozione o disabilitazione dell'autenticazione moderna ibrida da Skype for Business ed Exchange

Se è stato abilitato ibrida moderno autenticazione (alta) solo per trovare che è adatto per l'ambiente corrente, è possibile disattivare alta. In questo articolo viene illustrato come.
  
## <a name="who-is-this-article-for"></a>A chi è in questo articolo per?

Se si è stata abilitata l'autenticazione moderno in Skype per Business Online o locale, e/o Exchange Online o locale e trovato che è necessario disabilitare alta, questi passaggi vengono automaticamente.

> [!IMPORTANT]
> Se si sta effettuando Skype per Business Online o locale, vedere l'articolo '[Skype per le topologie di Business è supportato con l'autenticazione moderno](https://technet.microsoft.com/en-us/library/mt803262.aspx)', dispone di una topologia mista alta e necessario esaminare le topologie supportate prima di iniziare.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Come disabilitare l'autenticazione moderno ibrida (Exchange)

1. **Exchange in locale**: aprire Exchange Management Shell ed eseguire i comandi seguenti: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [connessione a Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) PowerShell remoto. Eseguire il comando seguente per attivare il contrassegno *OAuth2ClientProfileEnabled* su 'false':

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Come disabilitare l'autenticazione moderno ibrida (Skype per le aziende)

1. **Skype aziendali locali**: eseguire i seguenti comandi in Skype per Business Management Shell:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype per le aziende Online**: [connettersi a Skype for Business in linea](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) con Remote PowerShell. Eseguire il seguente comando per disabilitare l'autenticazione moderno:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Collegamento a ritroso alla panoramica autenticazione moderno](hybrid-modern-auth-overview.md) . 
  

