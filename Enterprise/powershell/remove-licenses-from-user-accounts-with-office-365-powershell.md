---
title: Rimuovere le licenze dagli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/29/2019
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
ms.openlocfilehash: 5b5f4550a5fade7f95669ad455aebd5d5f7fbf34
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651220"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Rimuovere le licenze dagli account utente con Office 365 PowerShell

**Riepilogo:** Viene illustrato come per rimuovere licenze di Office 365 che sono stati precedentemente assegnate agli utenti di Office 365 PowerShell.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Usare il modulo di Azure Active Directory PowerShell per Graph

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Successivamente, elencare i piani di licenza per il tenant con questo comando.

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Successivamente, ottenere il nome di accesso dell'account per cui si desidera rimuovere una licenza, noto anche come il nome principale (UPN).

Infine, specificare l'accesso e la licenza per pianificare i nomi utente, rimuovere i caratteri lt"e gt _" ed eseguire questi comandi.

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

   
Per visualizzare le informazioni sulla licenza piano (**AccountSkuID** ) nella propria organizzazione, vedere gli argomenti seguenti:
    
  - [Visualizzare le licenze e i servizi con PowerShell di Office 365](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)
    
Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro _-All_, vengono restituiti solo i primi 500 account.
    
### <a name="removing-licenses-from-user-accounts"></a>Rimozione di licenze dall'account utente

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

[Gestire gli account utente e le licenze con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)

    
## <a name="new-to-office-365"></a>Nuovo utente di Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

