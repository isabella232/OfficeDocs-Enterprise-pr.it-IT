---
title: Eliminare e ripristinare account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Informazioni su come usare PowerShell di Office 365 per eliminare e ripristinare gli account utente di Office 365.
ms.openlocfilehash: 09f3595ed7cd5434efb2897a43ba1bbca5286c25
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2018
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a>Eliminare e ripristinare account utente con Office 365 PowerShell

**Sintesi:** Informazioni su come usare PowerShell di Office 365 per eliminare e ripristinare gli account utente di Office 365.
  
Quando si utilizza PowerShell di Office 365 per eliminare un account utente, quest'ultimo non viene rimosso in modo definitivo. Infatti, si hanno a disposizione 30 giorni di tempo per ripristinare l'account utente eliminato.
  
## <a name="before-you-begin"></a>Prima di iniziare

- Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).
    
- Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro _-All_, vengono restituiti solo i primi 500 account.
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>Utilizzare PowerShell di Office 365 per bloccare l'accesso a singoli account utente
<a name="ShortVersion"> </a>

Per eliminare un account utente, utilizzare la sintassi riportata di seguito:
  
```
Remove-MsolUser -UserPrincipalName <Account>
```

Questo esempio elimina l'account utente BelindaN@litwareinc.com.
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

Per ripristinare un account utente eliminato entro la fine del periodo di tolleranza di 30 giorni, utilizzare la sintassi seguente:
  
```
Restore-MsolUser -UserPrincipalName <Account>
```

Questo esempio consente di ripristinare l'account utente eliminato BelindaN@litwareinc.com.
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 **Note:**
  
- Per visualizzare un elenco di utenti eliminati che possono essere ripristinati, eseguire il comando seguente:
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- Se il nome dell'entità utente originale di un account viene usato da un altro account, fare ricorso al parametro  _NewUserPrincipalName_ invece che a quello _UserPrincipalName_ per specificare un differente nome principale dell'utente, quando si ripristina l'account utente.
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a>Utilizzare il modulo Azure Active Directory V2 PowerShell per rimuovere un account utente
<a name="ShortVersion"> </a>

Per utilizzare il cmdlet **Remove-AzureADUser** dal modulo Azure Active Directory V2 PowerShell, è necessario innanzitutto connettersi alla propria sottoscrizione. Per visualizzare le istruzioni, consultare [Connettersi con il modulo Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
Una volta stabilita la connessione, utilizzare la sintassi seguente per rimuovere un singolo account utente:
  
```
Remove-AzureADUser -ObjectID <Account>
```

Questo esempio consente di rimuovere l'account utente fabricec@litwareinc.com.
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> Il parametro **-ObjectID** nel cmdlet **Remove-AzureAD** accetta sia il nome account (anche detto "nome dell'entità utente) sia l'ID oggetto dell'account.
  
Per visualizzare il nome dell'account in base al nome dell'utente, usare i comandi seguenti:
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Questo esempio permette di visualizzare il nome dell'account per l'utente Caleb Sillis.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Per rimuovere un account in base al nome dell'utente, utilizzare i comandi seguenti:
  
```
$userName="<User name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="see-also"></a>Vedere anche
<a name="SeeAlso"> </a>

Vedere i seguenti argomenti aggiuntivi sulla gestione degli utenti con Office 365 PowerShell:
  
- [Creare account utente con Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Bloccare gli account utente con Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Assegnare le licenze agli account utente con Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Rimuovere le licenze dagli account utente con Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Per ulteriori informazioni sui cmdlet utilizzati in questa procedura, vedere i seguenti argomenti:
  
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Remove-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [Restore-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

