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
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Rimozione o disabilitazione dell'autenticazione moderna ibrida da Skype for Business ed Exchange

Se è stato abilitato ibrida moderno autenticazione (alta) solo per trovare che è adatto per l'ambiente corrente, è possibile disattivare alta. In questo articolo viene illustrato come.
  
## <a name="who-is-this-article-for"></a>A chi è in questo articolo per?

Se si è stata abilitata l'autenticazione moderno in Skype per Business Online o locale, e/o Exchange Online o locale e trovato che è necessario disabilitare alta, questi passaggi vengono automaticamente.
  
 **Importante** Se si sta effettuando Skype per Business Online o locale, vedere l'articolo ' [Skype per le topologie di Business è supportato con l'autenticazione moderno](https://technet.microsoft.com/en-us/library/mt803262.aspx)', dispone di una topologia mista alta e necessario esaminare le topologie supportate prima di iniziare.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Come disabilitare l'autenticazione moderno ibrida (Exchange)

1. **Exchange in locale**: aprire Exchange Management Shell ed eseguire il comando seguente. 
    
1. Set-OrganizationConfig-OAuth2ClientProfileEnabled $false
    
2. Set-AuthServer-Identity evoSTS - IsDefaultAuthorizationEndpoint $false
    
2. **Exchange Online**: connettersi a Exchange Online PowerShell remoto. Eseguire il comando seguente per attivare il contrassegno *OAuth2ClientProfileEnabled* su 'false'. 
    
1. Set-OrganizationConfig-OAuth2ClientProfileEnabled: $false
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Come disabilitare l'autenticazione moderno ibrida (Skype per le aziende)

1. **Skype aziendali locali**: eseguire i seguenti comandi in Skype per Business Management Shell.
    
1. Set-CsOAuthConfiguration - ClientAuthorizationOAuthServerIdentity ""
    
2. **Skype per le aziende Online**: connettersi a Skype for Business in linea con Remote PowerShell. Eseguire il seguente comando per disabilitare l'autenticazione moderno. 
    
1. Set-CsOAuthConfiguration - ClientAdalAuthOverride non consentito
    
[Collegamento a ritroso alla panoramica autenticazione moderno](hybrid-modern-auth-overview.md) . 
  

