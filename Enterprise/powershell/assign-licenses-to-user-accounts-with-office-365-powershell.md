---
title: Assegnare le licenze agli account utente con Office 365 PowerShell
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
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: Questo articolo viene illustrato come utilizzare Office 365 PowerShell assegna una licenza di Office 365 per gli utenti senza licenza.
ms.openlocfilehash: ab9b66065e20d0c2d6cfb673dac24ee2ab79e831
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651181"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Assegnare le licenze agli account utente con Office 365 PowerShell

**Riepilogo:**  Questo articolo viene illustrato come utilizzare Office 365 PowerShell assegna una licenza di Office 365 per gli utenti senza licenza.
  
Gli utenti non possono utilizzare i servizi di Office 365 fino a quando il proprio account è stato assegnato una licenza da un piano di licenze. È possibile utilizzare Office 365 PowerShell rapidamente assegnare licenze agli account senza licenza. 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Usare il modulo di Azure Active Directory PowerShell per Graph

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Successivamente, elencare i piani di licenza per il tenant con questo comando.

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Successivamente, ottenere il nome di accesso dell'account che si desidera aggiungere una licenza, noto anche come il nome principale (UPN).

Infine, specificare il nome di accesso utente e il nome del piano di licenza ed eseguire questi comandi.

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Eseguire il comando **Get-MsolAccountSku** per visualizzare i piani di gestione delle licenze disponibili e il numero di licenze disponibili in ogni piano all'interno dell'organizzazione. Il numero di licenze disponibili in ogni piano è **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Per ulteriori informazioni sulle licenze di piani, le licenze e servizi, vedere [le licenze di visualizzazione e dei servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
Per trovare gli account senza licenza all'interno dell'organizzazione, eseguire questo comando.

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
È possibile assegnare solo le licenze agli account utente che la proprietà **UsageLocation** è impostata su un valido ISO 3166-1 alpha-codice di paese 2. Ad esempio, ci per gli Stati Uniti e FR per Francia. Alcuni servizi di Office 365 non sono disponibili in alcune nazioni. Per ulteriori informazioni, vedere [About restrizioni relative alla licenza](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
Per trovare gli account di cui non sono un valore **UsageLocation** , eseguire questo comando.

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

Per impostare il valore **UsageLocation** su un account, eseguire questo comando.

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

Ad esempio:

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro **-All**, vengono restituiti solo i primi 500 account.

### <a name="assigning-licenses-to-user-accounts"></a>Assegnazione delle licenze agli account utente
    
Per assegnare una licenza a un utente, utilizzare il seguente comando in Office 365 PowerShell.
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

Questo esempio viene assegnata una licenza dal **litwareinc: enterprisepack** (Office 365 Enterprise E3) licenze piano per l' utente senza licenza **belindan@litwareinc.com**:
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Per assegnare una licenza a molti utenti senza licenza, eseguire questo comando.
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | ForEach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```
  
>[!Note]
>È possibile assegnare più licenze a un utente dal piano di licenze stesso. Se non è sufficiente licenze disponibili, le licenze vengono assegnate agli utenti nell'ordine in cui si sta restituiti dal cmdlet **Get-MsolUser** fino ad esaurimento le licenze disponibili.
>

In questo esempio consente di assegnare licenze dal piano di licenze **litwareinc: enterprisepack** (Office 365 Enterprise E3) a tutti gli utenti senza licenza:
  
```
Get-MsolUser -All -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

In questo esempio consente di assegnare licenze stesse agli utenti senza licenza del reparto vendite negli Stati Uniti:
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a>Nuovo utente di Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Vedere anche

[Gestire gli account utente e le licenze con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)
