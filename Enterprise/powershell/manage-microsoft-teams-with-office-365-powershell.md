---
title: Gestire Microsoft teams con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/12/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Riepilogo: utilizzare Office 365 PowerShell per gestire Microsoft teams.'
ms.openlocfilehash: 0f15d71558ddb5166090b067da06e0a6321a2b99
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/12/2020
ms.locfileid: "44209122"
---
# <a name="manage-microsoft-teams-with-office-365-powershell"></a>Gestire Microsoft teams con Office 365 PowerShell

È possibile gestire Microsoft teams con Office 365 PowerShell.
  
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
  
[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)

