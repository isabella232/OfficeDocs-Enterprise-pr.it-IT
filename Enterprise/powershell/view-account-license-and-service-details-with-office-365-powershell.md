---
title: Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Viene illustrato come utilizzare Office 365 PowerShell per determinare i servizi di Office 365 assegnati agli utenti.
ms.openlocfilehash: f73acb5a107aa6ef970046a371b7a722a6abc8d9
ms.sourcegitcommit: 460c722d63e7e604ef0a57ec18fa7900fa6a4157
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2019
ms.locfileid: "39655868"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell

In Office 365, le licenze provenienti da piani di licenza (denominati anche SKU o piani di Office 365) offrono agli utenti l'accesso ai servizi di Office 365 definiti per tali piani. Tuttavia, un utente potrebbe non avere accesso a tutti i servizi disponibili in una licenza che gli è attualmente assegnata. È possibile utilizzare Office 365 PowerShell per visualizzare lo stato dei servizi negli account utente. 

Per ulteriori informazioni sui piani di licenza, la licenza e i servizi, vedere [View licences and Services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Usare il modulo di Azure Active Directory PowerShell per Graph

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Successivamente, elencare i piani di licenza per il tenant con questo comando.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Utilizzare questi comandi per elencare i servizi disponibili in ogni piano di gestione delle licenze.

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

Utilizzare questi comandi per elencare le licenze assegnate a un account utente.

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Successivamente, eseguire il comando seguente per elencare i piani di gestione delle licenze disponibili nell'organizzazione. 

```powershell
Get-MsolAccountSku
```
>[!Note]
>PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per Windows PowerShell e i cmdlet con **MSOL** all'interno del nome. Per continuare a usare i cmdlet, è necessario eseguirli in Windows PowerShell.
>

Successivamente, eseguire il comando seguente per elencare i servizi disponibili in ogni piano di licenze e l'ordine in cui sono elencati (il numero di indice).

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus
```
  
Utilizzare questo comando per elencare le licenze assegnate a un utente e l'ordine in cui sono elencate (il numero di indice).

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

>[!Note]
>Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro _All_, vengono restituiti solo i primi 500 account.
>
   

### <a name="to-view-services-for-a-user-account"></a>Per visualizzare i servizi per un account utente

Per visualizzare tutti i servizi di Office 365 a cui un utente ha accesso, utilizzare la sintassi seguente:
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

In questo esempio vengono illustrati i servizi ai quali l'utente BelindaN@litwareinc.com ha accesso. Vengono indicati i servizi associati a tutte le licenze assegnate al suo account.
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

Questo esempio mostra i servizi ai quali l'utente BelindaN@litwareinc.com ha accesso dalla prima licenza assegnata al suo account (il numero di indice è 0).
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Per visualizzare tutti i servizi per un utente a cui sono state assegnate *più licenze*, utilizzare la sintassi seguente:

```powershell
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="new-to-office-365"></a>Nuovo utente di Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Vedere anche

[Gestire gli account utente e le licenze con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)
