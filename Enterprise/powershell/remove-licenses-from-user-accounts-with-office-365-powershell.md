---
title: Rimuovere le licenze dagli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Viene illustrato come per rimuovere licenze di Office 365 che sono stati precedentemente assegnate agli utenti di Office 365 PowerShell.
ms.openlocfilehash: a993737f4bd1186a7fb5beb7fa0f6a2ae6782618
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123303"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Rimuovere le licenze dagli account utente con Office 365 PowerShell

**Riepilogo:** Viene illustrato come per rimuovere licenze di Office 365 che sono stati precedentemente assegnate agli utenti di Office 365 PowerShell.
  
## <a name="before-you-begin"></a>Prima di iniziare

- Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).
    
- Per visualizzare le informazioni sulla licenza piano (**AccountSkuID** ) nella propria organizzazione, vedere gli argomenti seguenti:
    
  - [Visualizzare le licenze e i servizi con PowerShell di Office 365](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)
    
- Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro _-All_, vengono restituiti solo i primi 500 account.
    
## <a name="removing-licenses-from-user-accounts"></a>Rimozione di licenze dall'account utente

Per rimuovere le licenze da un account utente esistente, utilizzare la sintassi seguente:
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

In questo esempio viene rimossa la `litwareinc:ENTERPRISEPACK` licenza (Office 365 Enterprise E3) dall'account utente BelindaN@litwareinc.com.
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

Per rimuovere le licenze da un gruppo di utenti con licenza esistenti, utilizzare uno dei metodi seguenti:
  
- **Filtrare gli account in base a un attributo account esistente** A tale scopo, utilizzare la sintassi seguente:
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

In questo esempio viene rimossa la `litwareinc:ENTERPRISEPACK` le licenze (Office 365 Enterprise E3) da tutti gli account per gli utenti del reparto vendite negli Stati Uniti.
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **Utilizzare un elenco di account specifici** A tale scopo, eseguire le operazioni seguenti:
    
1. Creare e salvare un file di testo contenente un account su ogni riga come riportato di seguito:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. Utilizzare la sintassi seguente:
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

In questo esempio viene rimossa la `litwareinc:ENTERPRISEPACK` licenza (Office 365 Enterprise E3) gli account utente definito nel file C:\My Documents\Accounts.txt del testo.
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

Per rimuovere le licenze da tutti gli account utente esistenti, utilizzare la sintassi seguente:
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

In questo esempio viene rimossa la `litwareinc:ENTERPRISEPACK` licenza (Office 365 Enterprise E3) da tutti i membri esistenti con contratto multilicenza gli account utente.
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

Un altro modo per liberare una licenza è eliminando l'account utente. Per ulteriori informazioni, vedere [eliminare e ripristinare gli account utente con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>Vedere anche

Vedere i seguenti argomenti aggiuntivi sulla gestione degli utenti con Office 365 PowerShell:
  
- [Creare account utente con Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Eliminare e ripristinare account utente con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloccare gli account utente con Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Assegnare le licenze agli account utente con Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
Per ulteriori informazioni sui cmdlet utilizzati in questa procedura, vedere i seguenti argomenti:
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a>Nuovo utente di Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

