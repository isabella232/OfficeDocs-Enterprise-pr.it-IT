---
title: Bloccare gli account utente con Office 365 PowerShell
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
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Spiega come utilizzare Office 365 PowerShell per bloccare e sbloccare gli account di accesso a Office 365.
ms.openlocfilehash: a2edecf7bc47d39aa9aeb965c7b2834e37820a36
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069212"
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Bloccare gli account utente con Office 365 PowerShell

**Riepilogo:**  Spiega come utilizzare Office 365 PowerShell per bloccare e sbloccare gli account di accesso a Office 365.
  
Se si blocca l'accesso a un account di Office 365, non è possibile utilizzare l'account per accedere ai servizi e ai dati dell'organizzazione di Office 365. È possibile utilizzare Office 365 PowerShell per bloccare l'accesso a singoli account utente e a più utenti.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Usare il modulo di Azure Active Directory PowerShell per Graph

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
### <a name="block-access-to-individual-user-accounts"></a>Blocca l'accesso a singoli account utente

Per bloccare un singolo account utente, utilizzare la sintassi seguente:
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> Il parametro-ObjectID nel cmdlet Set-AzureAD accetta sia il nome di accesso dell'account, noto anche come nome dell'entità utente, sia l'ID oggetto dell'account. 
  
Questo esempio consente di bloccare l'accesso all'account utente fabricec@litwareinc.com.
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

Per sbloccare questo account utente, eseguire il comando riportato di seguito:
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

Per visualizzare l'UPN dell'account utente in base al nome visualizzato dell'utente, utilizzare i comandi seguenti:
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

In questo esempio viene visualizzato l'UPN dell'account utente per l'utente Caleb davanzali.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Per bloccare un account in base al nome visualizzato dell'utente, utilizzare i comandi seguenti:
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

In qualsiasi momento, è possibile controllare lo stato bloccato di un account utente con il seguente comando:
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>Blocca l'accesso a più account utente

Per bloccare l'accesso a più account utente, creare un file di testo contenente un nome di accesso all'account su ogni riga simile alla seguente:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

Nei comandi seguenti, il file di testo di esempio è C:\My Documents\Accounts.txt. Sostituirlo con il percorso e il nome file del file di testo.
  
Per bloccare l'accesso agli account elencati nel file di testo, eseguire il comando seguente:
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

Per sbloccare gli account elencati nel file di testo, eseguire il comando seguente:
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

    
### <a name="block-access-to-individual-user-accounts"></a>Blocca l'accesso a singoli account utente

Per bloccare l'accesso a un singolo account utente, utilizzare la sintassi seguente:
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

Questo esempio consente di bloccare l'accesso all'account utente fabricec@litwareinc.com.
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Per sbloccare l'account utente, eseguire il comando riportato di seguito:
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

In qualsiasi momento, è possibile controllare lo stato bloccato di un account utente con il seguente comando:
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>Blocca l'accesso a più account utente

Per prima cosa, creare un file di testo contenente un account su ogni riga come riportato di questo tipo:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
Nei comandi seguenti, il file di testo di esempio è C:\My Documents\Accounts.txt. Sostituirlo con il percorso e il nome file del file di testo.
    
Per bloccare l'accesso agli account elencati nel file di testo, eseguire il comando seguente:
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Per sbloccare gli account elencati nel file di testo, eseguire il comando seguente:
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>Vedere anche

[Gestire gli account utente e le licenze con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)
