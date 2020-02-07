---
title: Visualizzare gli utenti con e senza licenza con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/18/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Viene spiegato come utilizzare PowerShell di Office 365 per visualizzare gli account utente con e senza licenza.
ms.openlocfilehash: 4b2f2b5b3898b9f800cc3fb9416c5b666472d907
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844147"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a>Visualizzare gli utenti con e senza licenza con PowerShell di Office 365

Gli account utente nell'organizzazione di Office 365 possono disporre di alcune, tutte o nessuna licenza in base ai piani di gestione delle licenze nell'organizzazione. È possibile utilizzare PowerShell di Office 365 per individuare rapidamente gli utenti dotati di licenza o meno all'interno dell'organizzazione.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Usare il modulo di Azure Active Directory PowerShell per Graph

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
Per visualizzare l'elenco di tutti gli account utente all'interno dell'organizzazione a cui non è stato assegnato alcun piano di gestione delle licenze (utenti senza licenza), eseguire il comando riportato di seguito:
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

Per visualizzare l'elenco di tutti gli account utente all'interno dell'organizzazione a cui sono stati assegnati i piani di gestione delle licenze (utenti con licenza), eseguire il comando riportato di seguito:
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
>Per elencare tutti gli utenti dell'abbonamento, utilizzare il `Get-AzureAdUser -All $true` comando.
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Per visualizzare l'elenco di tutti gli account utente e dei relativi stati di licenza nell'organizzazione, eseguire il comando seguente in PowerShell di Office 365:
  
```powershell
Get-MsolUser -All
```

>[!Note]
>PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per Windows PowerShell e i cmdlet con **MSOL** all'interno del nome. Per continuare a usare i cmdlet, è necessario eseguirli in Windows PowerShell.
>

Per visualizzare l'elenco di tutti gli account utente senza licenza nell'organizzazione, eseguire il comando seguente:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Per visualizzare l'elenco di tutti gli account utente con licenza nell'organizzazione, eseguire il comando seguente:
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>Vedere anche

[Gestire gli account utente, le licenze e i gruppi con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)
