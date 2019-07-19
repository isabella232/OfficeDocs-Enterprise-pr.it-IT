---
title: Gestire Skype for Business Online con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Riepilogo: utilizzare PowerShell di Office 365 per gestire i criteri, i criteri per utente e le impostazioni relative alle riunioni di Skype for Business online.'
ms.openlocfilehash: 80d8308a1c9b32fcafd47d1df2f699141e41accd
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782136"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>Gestire Skype for Business Online con PowerShell di Office 365

 **Sintesi:**: Utilizzare PowerShell di Office 365 per gestire i criteri, i criteri per utente e le impostazioni relative alle riunioni di Skype for Business online.
  
Una delle attività principali di qualsiasi amministratore di Skype for Business online è la gestione dei criteri. Anche se è possibile eseguire alcune di queste operazioni nell'interfaccia di amministrazione di Microsoft 365, altre attività sono molto più rapide e semplici in PowerShell di Office 365. 

## <a name="before-you-start"></a>Prima di iniziare

Scaricare e installare il [modulo del connettore di Skype for business online](https://www.microsoft.com/en-us/download/details.aspx?id=39366), quindi riavviare il computer se richiesto.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Connettersi utilizzando un nome e una password dell'account di amministratore di Skype for business online

1. Aprire il prompt dei comandi Windows PowerShell ed eseguire quanto segue: 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. Nella finestra di dialogo **richiesta credenziali di Windows PowerShell** , digitare il nome e la password dell'account di amministratore di Skype for business online, quindi fare clic su **OK**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a>Connettersi utilizzando un account di amministratore di Skype for business online con l'autenticazione a più fattori

1. Aprire il prompt dei comandi Windows PowerShell ed eseguire quanto segue:

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. Quando viene richiesto dal comando **New-CsOnlineSession** , immettere il nome dell'account di amministratore di Skype for business online.

3. Nella finestra **di dialogo Accedi all'account** Digitare la password di amministratore di Skype for business online e quindi fare clic su **Accedi**.

4. Seguire le istruzioni riportate nella finestra di dialogo **Accedi alla tua account** per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica, e quindi fare clic su **Verifica**.

Per ulteriori informazioni, vedere i seguenti argomenti:
  
- [Gestire criteri Skype for Business Online con PowerShell di Office 365](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Assegnare criteri Skype for Business Online con PowerShell di Office 365](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>Vedere anche

[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)

[Riferimenti ai cmdlet di PowerShell per Skype for business](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

