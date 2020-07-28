---
title: Gestire Microsoft teams con PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Riepilogo: utilizzare PowerShell per gestire Microsoft teams.'
ms.openlocfilehash: 8958c6ec6f0c17c21461cbee4cb1a6441ceed8d6
ms.sourcegitcommit: 132c97bd5e0dbe469da64356ace5084b71419cea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/28/2020
ms.locfileid: "45429199"
---
# <a name="manage-microsoft-teams-with-powershell"></a>Gestire Microsoft teams con PowerShell

*Questo articolo si applica sia a Microsoft 365 Enterprise che a Office 365 Enterprise*.

È possibile gestire Microsoft teams con PowerShell.
  
Innanzitutto, installare il [modulo Microsoft teams](https://www.powershellgallery.com/packages/MicrosoftTeams/).
    
## <a name="sign-in-with-a-user-name-and-password"></a>Accedere con un nome utente e una password

Per il cloud Office 365 Worldwide (+ GCC):

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

Per il cloud del DoD del governo degli Stati Uniti di Office 365: 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

Per l'Office 365 US Government high cloud GCC:

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a>Accedere con l'autenticazione a più fattori (AMF)

Per il cloud Office 365 Worldwide (+ GCC):

```powershell
Connect-MicrosoftTeams
```

Per il cloud del DoD del governo degli Stati Uniti di Office 365: 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

Per l'Office 365 US Government high cloud GCC:

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a>Disconnessione da Microsoft Teams

Utilizzare questo comando:

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a>Vedere anche

[Panoramica di PowerShell Teams](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[Gestire Microsoft 365 con PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell per Microsoft 365](getting-started-with-office-365-powershell.md)

