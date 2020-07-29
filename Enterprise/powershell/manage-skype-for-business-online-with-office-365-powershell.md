---
title: Gestire Skype for business online con PowerShell
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
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Riepilogo: utilizzare PowerShell per Microsoft 365 per gestire i criteri di Skype for business online, i criteri per utente e le impostazioni delle riunioni.'
ms.openlocfilehash: 0701fdb8a0a1f588e1c113ad7050ed516638aebc
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502611"
---
# <a name="manage-skype-for-business-online-with-powershell"></a><span data-ttu-id="00688-103">Gestire Skype for business online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="00688-103">Manage Skype for Business Online with PowerShell</span></span>

<span data-ttu-id="00688-104">*Questo articolo si applica sia a Microsoft 365 Enterprise che a Office 365 Enterprise*.</span><span class="sxs-lookup"><span data-stu-id="00688-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="00688-105">Una delle attività principali di qualsiasi amministratore di Skype for Business online è la gestione dei criteri.</span><span class="sxs-lookup"><span data-stu-id="00688-105">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="00688-106">Anche se è possibile eseguire alcune di queste attività nell'interfaccia di amministrazione di Microsoft 365, altre attività sono molto più rapide e più semplici in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00688-106">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="00688-107">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="00688-107">Before you start</span></span>

<span data-ttu-id="00688-108">Scaricare e installare il [modulo del connettore di Skype for business online](https://www.microsoft.com/download/details.aspx?id=39366), quindi riavviare il computer.</span><span class="sxs-lookup"><span data-stu-id="00688-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="00688-109">Connettersi utilizzando un nome e una password dell'account di amministratore di Skype for business online</span><span class="sxs-lookup"><span data-stu-id="00688-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="00688-110">Aprire il prompt dei comandi Windows PowerShell ed eseguire quanto segue:</span><span class="sxs-lookup"><span data-stu-id="00688-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
   ```powershell
   Import-Module SkypeOnlineConnector
   $userCredential = Get-Credential
   $sfbSession = New-CsOnlineSession -Credential $userCredential
   Import-PSSession $sfbSession
   ```

2. <span data-ttu-id="00688-111">Nella finestra di dialogo **richiesta credenziali di Windows PowerShell** , digitare il nome e la password dell'account di amministratore di Skype for business online, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="00688-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a><span data-ttu-id="00688-112">Connettersi utilizzando un account di amministratore di Skype for business online con l'autenticazione a più fattori</span><span class="sxs-lookup"><span data-stu-id="00688-112">Connect using a Skype for Business Online administrator account with multi-factor authentication</span></span>

1. <span data-ttu-id="00688-113">Aprire il prompt dei comandi Windows PowerShell ed eseguire quanto segue:</span><span class="sxs-lookup"><span data-stu-id="00688-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

   ```powershell
   Import-Module SkypeOnlineConnector
   $sfbSession = New-CsOnlineSession
   Import-PSSession $sfbSession
   ```

2. <span data-ttu-id="00688-114">Quando viene richiesto dal comando **New-CsOnlineSession** , immettere il nome dell'account di amministratore di Skype for business online.</span><span class="sxs-lookup"><span data-stu-id="00688-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="00688-115">Nella finestra **di dialogo Accedi all'account** Digitare la password di amministratore di Skype for business online e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="00688-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="00688-116">Seguire le istruzioni riportate nella finestra di dialogo **Accedi alla tua account** per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica, e quindi fare clic su **Verifica**.</span><span class="sxs-lookup"><span data-stu-id="00688-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="00688-117">Per ulteriori informazioni, vedere i seguenti argomenti:</span><span class="sxs-lookup"><span data-stu-id="00688-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="00688-118">Gestire i criteri di Skype for business online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="00688-118">Manage Skype for Business Online policies with PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="00688-119">Assegnare criteri Skype for business online per utente con PowerShell</span><span class="sxs-lookup"><span data-stu-id="00688-119">Assign per-user Skype for Business Online policies with PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="00688-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="00688-120">See also</span></span>

[<span data-ttu-id="00688-121">Gestire Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="00688-121">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="00688-122">Guida introduttiva a PowerShell per Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="00688-122">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="00688-123">Riferimenti ai cmdlet di PowerShell per Skype for business</span><span class="sxs-lookup"><span data-stu-id="00688-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

