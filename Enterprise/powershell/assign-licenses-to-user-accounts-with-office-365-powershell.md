---
title: Assegnare le licenze agli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/05/2019
audience: Admin
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
search.appverid:
- MET150
description: Informazioni su come utilizzare Office 365 PowerShell per assegnare una licenza di Office 365 a utenti senza licenza.
ms.openlocfilehash: 4351feaa1dbe9d657ed8df54a74410991834ea5d
ms.sourcegitcommit: c16ab90d0b9902228ce4337f1c64900592936cce
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2019
ms.locfileid: "37108216"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Assegnare le licenze agli account utente con Office 365 PowerShell

**Riepilogo:**  Informazioni su come utilizzare Office 365 PowerShell per assegnare una licenza di Office 365 a utenti senza licenza.
  
Gli utenti non possono utilizzare i servizi di Office 365 finché all'account non è stata assegnata una licenza da un piano di gestione delle licenze. È possibile utilizzare Office 365 PowerShell per assegnare rapidamente le licenze agli account senza licenza. 

>[!Note]
>Gli account utente devono essere assegnati a un percorso. È possibile eseguire questa operazione dalle proprietà di un account utente nell'interfaccia di amministrazione di Microsoft 365 o da PowerShell.
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Usare il modulo di Azure Active Directory PowerShell per Graph

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Successivamente, elencare i piani di licenza per il tenant con questo comando.

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Successivamente, ottenere il nome di accesso dell'account a cui si desidera aggiungere una licenza, noto anche come nome dell'entità utente (UPN).

Successivamente, verificare che l'account utente disponga di una posizione di utilizzo assegnata.

```
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

Se non è stata assegnata alcuna posizione di utilizzo, è possibile assegnarne una con questi comandi:

```
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

Infine, specificare il nome di accesso dell'utente e il nome del piano di licenza ed eseguire questi comandi.

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

Eseguire il comando **Get-MsolAccountSku** per visualizzare i piani di gestione delle licenze disponibili e il numero di licenze disponibili in ogni piano dell'organizzazione. Il numero di licenze disponibili in ogni piano è **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Per ulteriori informazioni sui piani di licenza, le licenze e i servizi, vedere [View licences and Services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
Per trovare gli account senza licenza nell'organizzazione, eseguire questo comando.

```
Get-MsolUser -All -UnlicensedUsersOnly
```

È possibile assegnare licenze solo agli account utente con la proprietà **UsageLocation** impostata su un codice paese ISO 3166-1 Alpha-2 valido. Ad esempio, US per gli Stati Uniti e FR per la Francia. Alcuni servizi di Office 365 non sono disponibili in alcuni paesi. Per ulteriori informazioni, vedere [informazioni sulle restrizioni di licenza](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
Per trovare account che non dispongono di un valore **UsageLocation** , eseguire il comando seguente.

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

### <a name="assigning-licenses-to-user-accounts"></a>Assegnazione di licenze agli account utente
    
Per assegnare una licenza a un utente, utilizzare il seguente comando in Office 365 PowerShell.
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

In questo esempio viene assegnata una licenza dal piano di gestione delle licenze **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) all'utente non autorizzato **\@litwareinc.com**:
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Per assegnare una licenza a molti utenti senza licenza, eseguire questo comando.
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>Non è possibile assegnare più licenze a un utente dallo stesso piano di gestione delle licenze. Se non si dispone di una quantità sufficiente di licenze disponibili, le licenze vengono assegnate agli utenti nell'ordine in cui vengono restituiti dal cmdlet **Get-MsolUser** finché non vengono esaurite le licenze disponibili.
>

In questo esempio vengono assegnate le licenze dal piano di gestione delle licenze **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) a tutti gli utenti senza licenza:
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

In questo esempio vengono assegnate le stesse licenze agli utenti senza licenza del reparto vendite negli Stati Uniti:
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="new-to-office-365"></a>Nuovo utente di Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Vedere anche

[Gestire gli account utente e le licenze con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)
