---
title: Assegnare i ruoli agli account utente con Office 365 PowerShell
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 'Sintesi: utilizzare PowerShell di Office 365 e il cmdlet Add-MsolRoleMember per assegnare ruoli agli account utente.'
ms.openlocfilehash: dee9aede72a79a32f03c94a0793464e1393edd95
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a>Assegnare i ruoli agli account utente con Office 365 PowerShell

 **Sintesi:** utilizzare PowerShell di Office 365 e il cmdlet **Add-MsolRoleMember** per assegnare ruoli agli account utente.
  
È possibile rapidamente e facilmente assegnare ruoli agli account utente tramite PowerShell di Office 365 identificando il nome visualizzato dell'account utente e il nome del ruolo.
  
## <a name="before-you-begin"></a>Prima di iniziare

Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365 utilizzando un account amministratore globale. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).
  
## <a name="for-a-single-role-change"></a>Per una singola modifica del ruolo

Determinare quanto segue:
  
- L'account utente da configurare.
    
    Per specificare l'account utente, è necessario determinare il nome visualizzato. Per ottenere un elenco completo di account, utilizzare questo comando:
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Questo comando elenca il nome visualizzato degli account utente, ordinati per nome visualizzato, una schermata alla volta. È possibile filtrare l'elenco in un set più piccolo utilizzando il cmdlet **Where**. Ecco un esempio:
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Questo comando elenca solo gli account utente per cui il nome visualizzato inizia con "John".
    
- Il ruolo da assegnare.
    
    Per visualizzare l'elenco dei ruoli disponibili che è possibile assegnare agli account utente, usare il comando:
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Dopo aver determinato il nome visualizzato dell'account e il nome del ruolo, è possibile utilizzare questi comandi per assegnare il ruolo all'account:
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

Copiare i comandi e incollarli nel blocco note. Per le variabili **$dispName** e **$roleName**, sostituire il testo della descrizione con i rispettivi valori, rimuovere i caratteri \< e > e lasciare le virgolette. Copiare le righe modificate e incollarle nel modulo di Windows Azure Active Directory modulo affinché Windows PowerShell le esegua. È anche possibile utilizzare Windows PowerShell Integrated Scripting Environment (ISE).
  
Segue un esempio di un set di comandi completati:
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a>Per più modifiche di ruoli

Determinare quanto segue:
  
- Quali account utente configurare.
    
    Per specificare l'account utente, è necessario determinare il nome visualizzato. Per ottenere un elenco di account, utilizzare questo comando:
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Questo comando elenca il nome visualizzato di tutti gli account utente, ordinati per nome visualizzato, una schermata alla volta. È possibile filtrare l'elenco in un set più piccolo utilizzando il cmdlet **Where**. Ecco un esempio:
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Questo comando elenca solo gli account utente per cui il nome visualizzato inizia con "John".
    
- Ruoli che si desidera assegnare a ogni account utente.
    
    Per visualizzare l'elenco dei ruoli disponibili che è possibile assegnare agli account utente, usare il comando:
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Successivamente, creare un file CSV che includa i campi Nome visualizzato e Nome del ruolo. Ecco un esempio:
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

Successivamente, immettere il percorso del file CSV ed eseguire i comandi risultanti nel prompt dei comandi di PowerShell.
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>Vedere anche

#### 

[Gestire gli account utente e le licenze con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)
#### 

[Add-MsolRoleMember]((https://msdn.microsoft.com/library/dn194120.aspx))

