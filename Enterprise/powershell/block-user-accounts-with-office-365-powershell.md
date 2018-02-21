---
title: Bloccare gli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/10/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Questo articolo viene illustrato come utilizzare Office 365 PowerShell per bloccare e sbloccare l'accesso agli account di Office 365.
ms.openlocfilehash: 34d144c982210ddc9d557b6094f71706f8edbb7f
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2018
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Bloccare gli account utente con Office 365 PowerShell

**Riepilogo:**  Questo articolo viene illustrato come utilizzare Office 365 PowerShell per bloccare e sbloccare l'accesso agli account di Office 365.
  
Bloccare l'accesso a un account di Office 365 consente di evitare di utilizzare l'account per l'accesso e accedere ai servizi e dati all'interno dell'organizzazione Office 365. Quando si blocca l'accesso all'account, l'utente riceve il messaggio di errore quando si tenta di effettuare l'accesso:
  
![Account di Office 365 bloccato.](images/o365_powershell_account_blocked.png)
  
È possibile utilizzare Office 365 PowerShell per bloccare l'accesso a singoli e più account utente.
  
## <a name="before-you-begin"></a>Prima di iniziare

- Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).
    
- Quando si blocca un account utente, potrebbe impiegare fino a 24 ore per rendere effettive su client e dispositivi dell'utente.
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>Utilizzare PowerShell di Office 365 per bloccare l'accesso a singoli account utente

Per bloccare l'accesso a un singolo account utente, utilizzare la sintassi seguente:
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $true
```

Questo esempio consente di bloccare l'accesso all'account utente fabricec@litwareinc.com.
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Per sbloccare l'account utente, eseguire il comando riportato di seguito:
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $false
```

In qualsiasi momento, è possibile controllare lo stato bloccato di un account utente con il comando seguente:
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="use-office-365-powershell-to-block-access-to-multiple-user-accounts"></a>Utilizzo di Office 365 PowerShell per bloccare l'accesso a più account utente

Per prima cosa, creare un file di testo contenente un account su ogni riga simile alla seguente:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
Nei comandi seguenti, il file di testo di esempio è C:\My Documents\Accounts.txt. Sostituire con il percorso e il nome del file di testo.
    
Per bloccare l'accesso agli account elencati nel file di testo, eseguire il comando seguente:
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Per sbloccare gli account elencati nel file di testo, eseguire il comando seguente:
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-block-access-to-user-accounts"></a>Utilizzare il modulo Azure Active Directory V2 PowerShell per bloccare l'accesso agli account utente

Per utilizzare il cmdlet **New-AzureADUser** dal modulo Azure Active Directory V2 PowerShell, è necessario innanzitutto connettersi alla propria sottoscrizione. Per visualizzare le istruzioni, consultare[Connettersi con il modulo Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
Una volta stabilita la connessione, utilizzare la sintassi seguente per bloccare un singolo account utente:
  
```
Set-AzureADUser -ObjectID <UPN of user account> -AccountEnabled $false
```

> [!NOTE]
> Il parametro -ObjectID nel cmdlet Set-AzureAD accetta sia il nome account (anche detto "nome dell'entità utente) sia l'ID oggetto dell'account. 
  
Questo esempio consente di bloccare l'accesso all'account utente fabricec@litwareinc.com.
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

Per sbloccare questo account utente, eseguire il comando riportato di seguito:
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

Per visualizzare l'account utente che UPN in base al nome visualizzato dell'utente, utilizzare i comandi seguenti:
  
```
$userName="<user account display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

In questo esempio viene visualizzato l'account utente UPN per l'utente denominato di Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Per bloccare un account in base al nome dell'utente, utilizzare i comandi seguenti:
  
```
$userName="<user account display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

In qualsiasi momento, è possibile controllare lo stato bloccato di un account utente con il comando seguente:
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

Per bloccare l'accesso a più account utente, creare un file di testo che contiene un nome di account in ogni riga simile alla seguente:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

Nei comandi seguenti, il file di testo di esempio è C:\My Documents\Accounts.txt. Sostituire con il percorso e il nome del file di testo.
    
Per bloccare l'accesso agli account elencati nel file di testo, eseguire il comando seguente:
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

Per sbloccare gli account elencati nel file di testo, eseguire il comando seguente:
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="see-also"></a>Vedere anche
<a name="SeeAlso"> </a>

Vedere i seguenti argomenti aggiuntivi sulla gestione degli utenti con Office 365 PowerShell:
  
- [Creare account utente con Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Eliminare e ripristinare account utente con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Assegnare le licenze agli account utente con Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Rimuovere le licenze dagli account utente con Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Per ulteriori informazioni sui cmdlet utilizzati in questa procedura, vedere i seguenti argomenti:
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=113310)
    
- [Set-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691644)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

