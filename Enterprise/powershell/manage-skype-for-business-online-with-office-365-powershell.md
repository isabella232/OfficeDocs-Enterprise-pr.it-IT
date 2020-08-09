---
title: Gestire Skype for Business Online con PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Sintesi: Utilizzare PowerShell per Microsoft 365 per gestire i criteri, i criteri per gli utenti e le impostazioni delle riunioni di Skype for Business online.'
ms.openlocfilehash: 10587dad171c3df9de6985ad314bc1791080b8a1
ms.sourcegitcommit: 839236443410eb804372c4aae969ac9a82ba683b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/07/2020
ms.locfileid: "46592210"
---
# <a name="manage-skype-for-business-online-with-powershell"></a><span data-ttu-id="5f8da-103">Gestire Skype for Business Online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f8da-103">Manage Skype for Business Online with PowerShell</span></span>

<span data-ttu-id="5f8da-104">*Questo articolo può essere applicato sia a Microsoft 365 Enterprise che a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="5f8da-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="5f8da-105">Una delle attività principali di qualsiasi amministratore di Skype for Business Online è la gestione dei criteri.</span><span class="sxs-lookup"><span data-stu-id="5f8da-105">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="5f8da-106">Anche se è possibile eseguire alcune di queste operazioni nell'interfaccia di amministrazione di Microsoft 365, altre attività sono molto più rapide e semplici in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f8da-106">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="5f8da-107">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="5f8da-107">Before you start</span></span>

<span data-ttu-id="5f8da-108">Scaricare e installare il [Modulo di Windows PowerShell per Skype for Business Online](https://www.microsoft.com/download/details.aspx?id=39366), quindi riavviare il computer.</span><span class="sxs-lookup"><span data-stu-id="5f8da-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="5f8da-109">Accedere usando il nome utente e la password di un account amministratore di Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="5f8da-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="5f8da-110">Aprire il prompt dei comandi Windows PowerShell ed eseguire quanto segue:</span><span class="sxs-lookup"><span data-stu-id="5f8da-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
   ```powershell
   Import-Module SkypeOnlineConnector
   $userCredential = Get-Credential
   $sfbSession = New-CsOnlineSession -Credential $userCredential
   Import-PSSession $sfbSession
   ```

2. <span data-ttu-id="5f8da-111">Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell**, scrivere nome utente e password dell'account amministratore di Skype for Business, e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="5f8da-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a><span data-ttu-id="5f8da-112">Accedere con un account amministratore di Skype for Business Online usando l'autenticazione a più fattori</span><span class="sxs-lookup"><span data-stu-id="5f8da-112">Connect using a Skype for Business Online administrator account with multi-factor authentication</span></span>

1. <span data-ttu-id="5f8da-113">Aprire il prompt dei comandi Windows PowerShell ed eseguire quanto segue:</span><span class="sxs-lookup"><span data-stu-id="5f8da-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

   ```powershell
   Import-Module SkypeOnlineConnector
   $sfbSession = New-CsOnlineSession
   Import-PSSession $sfbSession
   ```

2. <span data-ttu-id="5f8da-114">Quando richiesto dal comando **New-CsOnlineSession**, immettere il nome dell'account amministratore di Skype for Business Online.</span><span class="sxs-lookup"><span data-stu-id="5f8da-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="5f8da-115">Nella finestra di dialogo **Accedi al tuo account**, scrivere la password dell'account amministratore di Skype for Business Online e cliccare su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="5f8da-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="5f8da-116">Seguire le istruzioni della finestra di dialogo **Accedi al tuo account** per fornire informazioni di autenticazione aggiuntive, come un codice di verifica, quindi fare clic su **Verifica**.</span><span class="sxs-lookup"><span data-stu-id="5f8da-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="5f8da-117">Per ulteriori informazioni, vedere i seguenti argomenti:</span><span class="sxs-lookup"><span data-stu-id="5f8da-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="5f8da-118">Gestire i criteri di Skype for Business Online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f8da-118">Manage Skype for Business Online policies with PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="5f8da-119">Assegnare i criteri di Skype for Business Online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f8da-119">Assign per-user Skype for Business Online policies with PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="5f8da-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5f8da-120">See also</span></span>

[<span data-ttu-id="5f8da-121">Gestire Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f8da-121">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="5f8da-122">Guida introduttiva a PowerShell per Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="5f8da-122">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="5f8da-123">Riferimenti per i cmdlet di PowerShell per Skype for Business</span><span class="sxs-lookup"><span data-stu-id="5f8da-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

