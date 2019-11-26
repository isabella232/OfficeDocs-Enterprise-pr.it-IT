---
title: Eliminare account utente con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Informazioni su come usare PowerShell di Office 365 per eliminare gli account utente di Office 365.
ms.openlocfilehash: e62c06981a861580804dde852ad3da7bd729fdbe
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257647"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a>Eliminare account utente con PowerShell di Office 365

È possibile usare PowerShell di Office 365 per eliminare un account utente.
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Usare il modulo di Azure Active Directory PowerShell per Graph

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Una volta stabilita la connessione, utilizzare la sintassi seguente per rimuovere un singolo account utente:
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

>[!Note]
>PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per il modulo di Windows PowerShell e i cmdlet con **MSOL** nel proprio nome. Per continuare a utilizzare questi cmdlet, è necessario eseguirli da Windows PowerShell.
>

Questo esempio consente di rimuovere l'account utente fabricec@litwareinc.com.
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> Il parametro **-ObjectID** nel cmdlet **Remove-AzureAD** accetta sia il nome utente dell’account, noto anche come Nome dell'entità utente, sia l'ID oggetto dell'account.
  
Per visualizzare il nome dell'account in base al nome dell'utente, usare i comandi seguenti:
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Questo esempio permette di visualizzare il nome dell'account per l'utente Caleb Sillis.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Per rimuovere un account in base al nome visualizzato dell'utente, utilizzare i comandi seguenti:
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell

Quando si elimina un account utente con il modulo di Microsoft Azure Active Directory per Windows PowerShell, questo non viene rimosso in modo definitivo. È possibile ripristinare l’account utente eliminato entro 30 giorni.

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).


Per eliminare un account utente, utilizzare la sintassi riportata di seguito:
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

Questo esempio elimina l'account utente BelindaN@litwareinc.com.
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

Per ripristinare un account utente eliminato entro la fine del periodo di tolleranza di 30 giorni, utilizzare la sintassi seguente:
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

Questo esempio consente di ripristinare l'account utente eliminato BelindaN@litwareinc.com.
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 **Note:**
  
- Per visualizzare un elenco di utenti eliminati che possono essere ripristinati, eseguire il comando seguente:
    
  ```powershell
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- Se il nome dell'entità utente originale di un account viene usato da un altro account, fare ricorso al parametro _NewUserPrincipalName_ invece che a quello _UserPrincipalName_ per specificare un differente nome principale dell'utente, quando si ripristina l'account utente.


## <a name="see-also"></a>Vedere anche

[Gestire gli account utente e le licenze con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)

