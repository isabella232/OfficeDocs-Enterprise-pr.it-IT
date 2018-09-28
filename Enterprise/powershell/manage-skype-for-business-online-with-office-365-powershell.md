---
title: Gestire Skype for Business Online con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Riepilogo: utilizzare PowerShell di Office 365 per gestire i criteri, i criteri per utente e le impostazioni relative alle riunioni di Skype for Business online.'
ms.openlocfilehash: a91803316972337aa31e2b979f841ac1cfbe8566
ms.sourcegitcommit: 053db5479f93478a65d4c36ffe44c6a7bcb60e3c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "23965193"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="52598-103">Gestire Skype for Business Online con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="52598-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

 <span data-ttu-id="52598-104">**Sintesi:**: Utilizzare PowerShell di Office 365 per gestire i criteri, i criteri per utente e le impostazioni relative alle riunioni di Skype for Business online.</span><span class="sxs-lookup"><span data-stu-id="52598-104">**Summary:** Use Office 365 PowerShell to manage Skype for Business Online policies, per-user policies, and meeting settings.</span></span>
  
<span data-ttu-id="52598-p101">Una delle attività principali di qualsiasi Skype per l'amministratore aziendale Online è la gestione di criteri. Anche se è possibile eseguire alcune di queste attività nell'interfaccia di amministrazione di Office 365, altre attività sono molto più rapida e semplice in Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52598-p101">One of the primary tasks of any Skype for Business Online administrator is managing policies. Although you can accomplish some of these tasks in the Office 365 Admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="52598-107">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="52598-107">Before you start</span></span>

<span data-ttu-id="52598-108">Scaricare e installare [Skype di funzionalità di Business Online Connector](https://www.microsoft.com/en-us/download/details.aspx?id=39366)e quindi riavviare il computer se richiesto.</span><span class="sxs-lookup"><span data-stu-id="52598-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="52598-109">Connettersi utilizzando un Skype Business Online nome account di amministratore e password</span><span class="sxs-lookup"><span data-stu-id="52598-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="52598-110">Aprire il prompt dei comandi Windows PowerShell ed eseguire quanto segue:</span><span class="sxs-lookup"><span data-stu-id="52598-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="52598-111">Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell** digitare i Skype per nome dell'account amministratore aziendale Online e la password e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="52598-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="52598-112">Connettersi utilizzando un Skype per account dell'amministratore aziendale Online con l'autenticazione a più fattori</span><span class="sxs-lookup"><span data-stu-id="52598-112">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="52598-113">Aprire il prompt dei comandi Windows PowerShell ed eseguire quanto segue:</span><span class="sxs-lookup"><span data-stu-id="52598-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="52598-114">Quando richiesto dal comando **New-CsOnlineSession** , immettere la Skype per nome dell'account amministratore aziendale Online.</span><span class="sxs-lookup"><span data-stu-id="52598-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="52598-115">Nella finestra di dialogo **Accedi al tuo account** digitare il Skype Business Online password di amministratore e fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="52598-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="52598-116">Seguire le istruzioni nella finestra di dialogo **Accedi al tuo account** per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica e quindi fare clic su **verifica**.</span><span class="sxs-lookup"><span data-stu-id="52598-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="52598-117">Per ulteriori informazioni, vedere i seguenti argomenti:</span><span class="sxs-lookup"><span data-stu-id="52598-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="52598-118">Gestire criteri Skype for Business Online con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="52598-118">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="52598-119">Assegnare criteri Skype for Business Online con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="52598-119">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="52598-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="52598-120">See also</span></span>

[<span data-ttu-id="52598-121">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="52598-121">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="52598-122">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="52598-122">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="52598-123">Skype per i riferimenti cmdlet PowerShell di Business</span><span class="sxs-lookup"><span data-stu-id="52598-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

