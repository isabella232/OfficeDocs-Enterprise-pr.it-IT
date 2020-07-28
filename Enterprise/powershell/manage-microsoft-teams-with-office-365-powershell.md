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
# <a name="manage-microsoft-teams-with-powershell"></a><span data-ttu-id="c3553-103">Gestire Microsoft teams con PowerShell</span><span class="sxs-lookup"><span data-stu-id="c3553-103">Manage Microsoft Teams with PowerShell</span></span>

<span data-ttu-id="c3553-104">*Questo articolo si applica sia a Microsoft 365 Enterprise che a Office 365 Enterprise*.</span><span class="sxs-lookup"><span data-stu-id="c3553-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="c3553-105">È possibile gestire Microsoft teams con PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3553-105">You can manage Microsoft Teams with PowerShell.</span></span>
  
<span data-ttu-id="c3553-106">Innanzitutto, installare il [modulo Microsoft teams](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span><span class="sxs-lookup"><span data-stu-id="c3553-106">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="c3553-107">Accedere con un nome utente e una password</span><span class="sxs-lookup"><span data-stu-id="c3553-107">Sign in with a user name and password</span></span>

<span data-ttu-id="c3553-108">Per il cloud Office 365 Worldwide (+ GCC):</span><span class="sxs-lookup"><span data-stu-id="c3553-108">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="c3553-109">Per il cloud del DoD del governo degli Stati Uniti di Office 365:</span><span class="sxs-lookup"><span data-stu-id="c3553-109">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="c3553-110">Per l'Office 365 US Government high cloud GCC:</span><span class="sxs-lookup"><span data-stu-id="c3553-110">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="c3553-111">Accedere con l'autenticazione a più fattori (AMF)</span><span class="sxs-lookup"><span data-stu-id="c3553-111">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="c3553-112">Per il cloud Office 365 Worldwide (+ GCC):</span><span class="sxs-lookup"><span data-stu-id="c3553-112">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="c3553-113">Per il cloud del DoD del governo degli Stati Uniti di Office 365:</span><span class="sxs-lookup"><span data-stu-id="c3553-113">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="c3553-114">Per l'Office 365 US Government high cloud GCC:</span><span class="sxs-lookup"><span data-stu-id="c3553-114">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="c3553-115">Disconnessione da Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="c3553-115">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="c3553-116">Utilizzare questo comando:</span><span class="sxs-lookup"><span data-stu-id="c3553-116">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="c3553-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c3553-117">See also</span></span>

[<span data-ttu-id="c3553-118">Panoramica di PowerShell Teams</span><span class="sxs-lookup"><span data-stu-id="c3553-118">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="c3553-119">Gestire Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="c3553-119">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c3553-120">Guida introduttiva a PowerShell per Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c3553-120">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

