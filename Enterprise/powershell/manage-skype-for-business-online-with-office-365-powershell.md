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
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>Gestire Skype for Business Online con PowerShell di Office 365

 **Sintesi:**: Utilizzare PowerShell di Office 365 per gestire i criteri, i criteri per utente e le impostazioni relative alle riunioni di Skype for Business online.
  
Una delle attività principali di qualsiasi Skype per l'amministratore aziendale Online è la gestione di criteri. Anche se è possibile eseguire alcune di queste attività nell'interfaccia di amministrazione di Office 365, altre attività sono molto più rapida e semplice in Office 365 PowerShell. 

## <a name="before-you-start"></a>Prima di iniziare

Scaricare e installare [Skype di funzionalità di Business Online Connector](https://www.microsoft.com/en-us/download/details.aspx?id=39366)e quindi riavviare il computer se richiesto.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Connettersi utilizzando un Skype Business Online nome account di amministratore e password

1. Aprire il prompt dei comandi Windows PowerShell ed eseguire quanto segue: 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell** digitare i Skype per nome dell'account amministratore aziendale Online e la password e quindi fare clic su **OK**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a>Connettersi utilizzando un Skype per account dell'amministratore aziendale Online con l'autenticazione a più fattori

1. Aprire il prompt dei comandi Windows PowerShell ed eseguire quanto segue:

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. Quando richiesto dal comando **New-CsOnlineSession** , immettere la Skype per nome dell'account amministratore aziendale Online.

3. Nella finestra di dialogo **Accedi al tuo account** digitare il Skype Business Online password di amministratore e fare clic su **Accedi**.

4. Seguire le istruzioni nella finestra di dialogo **Accedi al tuo account** per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica e quindi fare clic su **verifica**.

Per ulteriori informazioni, vedere i seguenti argomenti:
  
- [Gestire criteri Skype for Business Online con PowerShell di Office 365](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Assegnare criteri Skype for Business Online con PowerShell di Office 365](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>Vedere anche

[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)

[Skype per i riferimenti cmdlet PowerShell di Business](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

