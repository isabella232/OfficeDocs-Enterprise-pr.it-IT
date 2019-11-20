---
title: Rimuovere le licenze dagli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/23/2019
audience: Admin
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
description: Viene illustrato come utilizzare Office 365 PowerShell per rimuovere le licenze di Office 365 precedentemente assegnate agli utenti.
ms.openlocfilehash: bfd333b649df1d346a45abc3e8b9e35666f8f582
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747542"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Rimuovere le licenze dagli account utente con Office 365 PowerShell

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Usare il modulo di Azure Active Directory PowerShell per Graph

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Successivamente, elencare i piani di licenza per il tenant con questo comando.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Successivamente, ottenere il nome di accesso dell'account per il quale si desidera rimuovere una licenza, nota anche come nome dell'entità utente (UPN).

Infine, specificare i nomi di accesso dell'utente e dei piani di licenza, rimuovere i caratteri "<" e ">" ed eseguire questi comandi.

```powershell
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

   
Per visualizzare le informazioni relative al piano di gestione delle licenze (**AccountSkuID** ) nell'organizzazione, vedere i seguenti argomenti:
    
  - [Visualizzare le licenze e i servizi con PowerShell di Office 365](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)
    
Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro _-All_, vengono restituiti solo i primi 500 account.
    
### <a name="removing-licenses-from-user-accounts"></a>Rimozione di licenze dagli account utente

Per rimuovere le licenze da un account utente esistente, utilizzare la sintassi seguente:
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

In questo esempio viene `litwareinc:ENTERPRISEPACK` rimossa la licenza (Office 365 Enterprise E3) dall'account utente BelindaN@litwareinc.com.
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
>Non è possibile utilizzare il cmdlet Set-MsolUserLicense per annullare l'assegnazione di utenti dalle licenze *annullate* . È necessario eseguire questa operazione singolarmente per ogni account utente nell'interfaccia di amministrazione di Microsoft 365.
>

Per rimuovere le licenze da un gruppo di utenti con licenza esistenti, utilizzare uno dei metodi seguenti:
  
- **Filtrare gli account in base a un attributo account esistente** A tale scopo, utilizzare la sintassi seguente:
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

In questo esempio vengono `litwareinc:ENTERPRISEPACK` rimosse le licenze (Office 365 Enterprise E3) da tutti gli account per gli utenti nel reparto vendite degli Stati Uniti.
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **Utilizzare un elenco di account specifici** A tale scopo, eseguire la procedura seguente:
    
1. Creare e salvare un file di testo contenente un account su ogni riga come riportato di seguito:
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. Utilizzare la sintassi seguente:
    
  ```powershell
  Get-Content "<FileNameAndPath>" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"... }
  ```

In questo esempio viene `litwareinc:ENTERPRISEPACK` rimossa la licenza (Office 365 Enterprise E3) dagli account utente definiti nel file di testo C:\My Documents\Accounts.txt.
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "litwareinc:ENTERPRISEPACK" }
  ```

Per rimuovere le licenze da tutti gli account utente esistenti, utilizzare la sintassi seguente:
  
```powershell
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

In questo esempio viene `litwareinc:ENTERPRISEPACK` rimossa la licenza (Office 365 Enterprise E3) da tutti gli account utente con licenza esistenti.
  
```powershell
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

Un altro modo per liberare una licenza consiste nell'eliminazione dell'account utente. Per ulteriori informazioni, vedere [eliminare e ripristinare gli account utente con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>Vedere anche

[Gestire gli account utente e le licenze con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)

    
## <a name="new-to-office-365"></a>Nuovo utente di Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

