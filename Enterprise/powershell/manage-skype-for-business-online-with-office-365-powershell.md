---
title: Gestire Skype for Business Online con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/28/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Riepilogo: utilizzare PowerShell di Office 365 per gestire i criteri, i criteri per utente e le impostazioni relative alle riunioni di Skype for Business online.'
ms.openlocfilehash: f1a5df3802d43755e81465743b81c5fbb9fff7e0
ms.sourcegitcommit: 6c7cc6aca8713e280ae6ff51226dde9db4497401
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2020
ms.locfileid: "44415938"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="d5bd6-103">Gestire Skype for Business Online con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="d5bd6-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

<span data-ttu-id="d5bd6-104">Una delle attività principali di qualsiasi amministratore di Skype for Business online è la gestione dei criteri.</span><span class="sxs-lookup"><span data-stu-id="d5bd6-104">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="d5bd6-105">Anche se è possibile eseguire alcune di queste operazioni nell'interfaccia di amministrazione di Microsoft 365, altre attività sono molto più rapide e semplici in PowerShell di Office 365.</span><span class="sxs-lookup"><span data-stu-id="d5bd6-105">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="d5bd6-106">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="d5bd6-106">Before you start</span></span>

<span data-ttu-id="d5bd6-107">Scaricare e installare il [modulo del connettore di Skype for business online](https://www.microsoft.com/download/details.aspx?id=39366), quindi riavviare il computer.</span><span class="sxs-lookup"><span data-stu-id="d5bd6-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="d5bd6-108">Connettersi utilizzando un nome e una password dell'account di amministratore di Skype for business online</span><span class="sxs-lookup"><span data-stu-id="d5bd6-108">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="d5bd6-109">Aprire il prompt dei comandi Windows PowerShell ed eseguire quanto segue:</span><span class="sxs-lookup"><span data-stu-id="d5bd6-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="d5bd6-110">Nella finestra di dialogo **richiesta credenziali di Windows PowerShell** , digitare il nome e la password dell'account di amministratore di Skype for business online, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="d5bd6-110">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a><span data-ttu-id="d5bd6-111">Connettersi utilizzando un account di amministratore di Skype for business online con l'autenticazione a più fattori</span><span class="sxs-lookup"><span data-stu-id="d5bd6-111">Connect using a Skype for Business Online administrator account with multi-factor authentication</span></span>

1. <span data-ttu-id="d5bd6-112">Aprire il prompt dei comandi Windows PowerShell ed eseguire quanto segue:</span><span class="sxs-lookup"><span data-stu-id="d5bd6-112">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```powershell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="d5bd6-113">Quando viene richiesto dal comando **New-CsOnlineSession** , immettere il nome dell'account di amministratore di Skype for business online.</span><span class="sxs-lookup"><span data-stu-id="d5bd6-113">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="d5bd6-114">Nella finestra **di dialogo Accedi all'account** Digitare la password di amministratore di Skype for business online e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="d5bd6-114">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="d5bd6-115">Seguire le istruzioni riportate nella finestra di dialogo **Accedi alla tua account** per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica, e quindi fare clic su **Verifica**.</span><span class="sxs-lookup"><span data-stu-id="d5bd6-115">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="d5bd6-116">Per ulteriori informazioni, vedere i seguenti argomenti:</span><span class="sxs-lookup"><span data-stu-id="d5bd6-116">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="d5bd6-117">Gestire criteri Skype for Business Online con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="d5bd6-117">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="d5bd6-118">Assegnare criteri Skype for Business Online con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="d5bd6-118">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="d5bd6-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d5bd6-119">See also</span></span>

[<span data-ttu-id="d5bd6-120">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="d5bd6-120">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d5bd6-121">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="d5bd6-121">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="d5bd6-122">Riferimenti ai cmdlet di PowerShell per Skype for business</span><span class="sxs-lookup"><span data-stu-id="d5bd6-122">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

