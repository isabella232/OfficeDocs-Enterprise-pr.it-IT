---
title: Bloccare gli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
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
ms.openlocfilehash: 0e1ac3f61acafedd77c2af760b8316aa6b936e7b
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546477"
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Bloccare gli account utente con Office 365 PowerShell

**Riepilogo:**  Questo articolo viene illustrato come utilizzare Office 365 PowerShell per bloccare e sbloccare l'accesso agli account di Office 365.
  
Bloccare l'accesso a un account di Office 365 consente di evitare di utilizzare l'account per l'accesso e accedere ai servizi e dati all'interno dell'organizzazione Office 365. È possibile utilizzare Office 365 PowerShell per bloccare l'accesso a singoli e più account utente.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilizzare grafico modulo di Azure Active Directory PowerShell

Primo, [la connessione al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
### <a name="block-access-to-individual-user-accounts"></a>Bloccare l'accesso a singoli account utente

Per bloccare un singolo account utente, utilizzare la sintassi seguente:
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> Il parametro - ObjectID nel cmdlet Set-AzureAD accetta uno l'account nome di accesso, anche noto come il nome dell'entità utente o l'ID oggetto. dell'account 
  
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
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

In questo esempio viene visualizzato l'account utente UPN per l'utente denominato di Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Per bloccare un account in base al nome visualizzato dell'utente, utilizzare i comandi seguenti:
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

In qualsiasi momento, è possibile controllare lo stato bloccato di un account utente con il comando seguente:
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>Bloccare l'accesso a più account utente

Per bloccare l'accesso a più account utente, creare un file di testo contenente un account nome di accesso su ogni riga simile alla seguente:
    
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

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilizzare il modulo di Microsoft Azure Active Directory per Windows PowerShell

Primo, [la connessione al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

    
### <a name="block-access-to-individual-user-accounts"></a>Bloccare l'accesso a singoli account utente

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

In qualsiasi momento, è possibile controllare lo stato bloccato di un account utente con il comando seguente:
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>Bloccare l'accesso a più account utente

Per prima cosa, creare un file di testo contenente un account su ogni riga simile alla seguente:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
Nei comandi seguenti, il file di testo di esempio è C:\My Documents\Accounts.txt. Sostituire con il percorso e il nome del file di testo.
    
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
