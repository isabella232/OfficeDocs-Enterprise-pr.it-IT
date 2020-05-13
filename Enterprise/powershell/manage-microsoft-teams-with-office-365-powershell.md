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
# <a name="manage-microsoft-teams-with-office-365-powershell"></a><span data-ttu-id="039d6-103">Gestire Microsoft teams con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="039d6-103">Manage Microsoft Teams with Office 365 PowerShell</span></span>

<span data-ttu-id="039d6-104">È possibile gestire Microsoft teams con Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="039d6-104">You can manage Microsoft Teams with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="039d6-105">Innanzitutto, installare il [modulo Microsoft teams](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span><span class="sxs-lookup"><span data-stu-id="039d6-105">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="039d6-106">Accedere con un nome utente e una password</span><span class="sxs-lookup"><span data-stu-id="039d6-106">Sign in with a user name and password</span></span>

<span data-ttu-id="039d6-107">Per il cloud Office 365 Worldwide (+ GCC):</span><span class="sxs-lookup"><span data-stu-id="039d6-107">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="039d6-108">Per il cloud del DoD del governo degli Stati Uniti di Office 365:</span><span class="sxs-lookup"><span data-stu-id="039d6-108">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="039d6-109">Per l'Office 365 US Government high cloud GCC:</span><span class="sxs-lookup"><span data-stu-id="039d6-109">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="039d6-110">Accedere con l'autenticazione a più fattori (AMF)</span><span class="sxs-lookup"><span data-stu-id="039d6-110">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="039d6-111">Per il cloud Office 365 Worldwide (+ GCC):</span><span class="sxs-lookup"><span data-stu-id="039d6-111">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="039d6-112">Per il cloud del DoD del governo degli Stati Uniti di Office 365:</span><span class="sxs-lookup"><span data-stu-id="039d6-112">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="039d6-113">Per l'Office 365 US Government high cloud GCC:</span><span class="sxs-lookup"><span data-stu-id="039d6-113">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="039d6-114">Disconnessione da Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="039d6-114">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="039d6-115">Utilizzare questo comando:</span><span class="sxs-lookup"><span data-stu-id="039d6-115">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="039d6-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="039d6-116">See also</span></span>

[<span data-ttu-id="039d6-117">Panoramica di PowerShell Teams</span><span class="sxs-lookup"><span data-stu-id="039d6-117">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="039d6-118">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="039d6-118">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="039d6-119">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="039d6-119">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

