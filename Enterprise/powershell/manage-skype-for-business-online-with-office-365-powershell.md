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
# <a name="manage-skype-for-business-online-with-powershell"></a>Gestire Skype for business online con PowerShell

*Questo articolo si applica sia a Microsoft 365 Enterprise che a Office 365 Enterprise*.

Una delle attività principali di qualsiasi amministratore di Skype for Business online è la gestione dei criteri. Anche se è possibile eseguire alcune di queste attività nell'interfaccia di amministrazione di Microsoft 365, altre attività sono molto più rapide e più semplici in PowerShell. 

## <a name="before-you-start"></a>Prima di iniziare

Scaricare e installare il [modulo del connettore di Skype for business online](https://www.microsoft.com/download/details.aspx?id=39366), quindi riavviare il computer.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Connettersi utilizzando un nome e una password dell'account di amministratore di Skype for business online

1. Aprire il prompt dei comandi Windows PowerShell ed eseguire quanto segue: 
    
   ```powershell
   Import-Module SkypeOnlineConnector
   $userCredential = Get-Credential
   $sfbSession = New-CsOnlineSession -Credential $userCredential
   Import-PSSession $sfbSession
   ```

2. Nella finestra di dialogo **richiesta credenziali di Windows PowerShell** , digitare il nome e la password dell'account di amministratore di Skype for business online, quindi fare clic su **OK**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a>Connettersi utilizzando un account di amministratore di Skype for business online con l'autenticazione a più fattori

1. Aprire il prompt dei comandi Windows PowerShell ed eseguire quanto segue:

   ```powershell
   Import-Module SkypeOnlineConnector
   $sfbSession = New-CsOnlineSession
   Import-PSSession $sfbSession
   ```

2. Quando viene richiesto dal comando **New-CsOnlineSession** , immettere il nome dell'account di amministratore di Skype for business online.

3. Nella finestra **di dialogo Accedi all'account** Digitare la password di amministratore di Skype for business online e quindi fare clic su **Accedi**.

4. Seguire le istruzioni riportate nella finestra di dialogo **Accedi alla tua account** per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica, e quindi fare clic su **Verifica**.

Per ulteriori informazioni, vedere i seguenti argomenti:
  
- [Gestire i criteri di Skype for business online con PowerShell](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Assegnare criteri Skype for business online per utente con PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>Vedere anche

[Gestire Microsoft 365 con PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell per Microsoft 365](getting-started-with-office-365-powershell.md)

[Riferimenti ai cmdlet di PowerShell per Skype for business](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

