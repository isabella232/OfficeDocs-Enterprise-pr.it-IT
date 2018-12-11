---
title: Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Questo articolo viene illustrato come utilizzare Office 365 PowerShell per determinare i servizi di Office 365 che sono stati assegnati agli utenti.
ms.openlocfilehash: 5d575ea9e0b45ddc453b3b1c73bd53bf73adab2e
ms.sourcegitcommit: 16806849f373196797d65e63ced825d547aef956
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2018
ms.locfileid: "27213953"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell

**Riepilogo:** Questo articolo viene illustrato come utilizzare Office 365 PowerShell per determinare i servizi di Office 365 che sono stati assegnati agli utenti.
  
In Office 365, concede in licenza da Gestione licenze piani (anche denominato SKU o Office 365 dei piani) è possibile accedere ai servizi definiti per i piani di Office 365. Tuttavia, un utente potrebbe non avere accesso a tutti i servizi disponibili in una licenza attualmente assegnati a loro. È possibile utilizzare Office 365 PowerShell per visualizzare lo stato dei servizi per gli account utente. 

## <a name="before-you-begin"></a>Prima di iniziare

- Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).
    
- Utilizzare i comandi `Get-MsolAccountSku` e `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` per trovare le informazioni seguenti:
    
  - I piani di gestione delle licenze che sono disponibili nell'organizzazione.
    
  - I servizi che sono disponibili in ogni piano di gestione delle licenze e l'ordine in cui sono elencati (il numero di indice).
    
     Per ulteriori informazioni sulle licenze di piani di licenza e servizi, vedere [le licenze di visualizzazione e dei servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Utilizzare il comando `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` per individuare le licenze che sono assegnate a un utente e l'ordine in cui sono elencati (numero di indice).
    
- Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro _All_, vengono restituiti solo i primi 500 account.
    

## <a name="to-view-services-for-a-user-account"></a>Per visualizzare i servizi per un account utente

Per visualizzare tutti i servizi di Office 365 che un utente ha accesso, utilizzare la sintassi seguente:
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

In questo esempio vengono illustrati i servizi al quale BelindaN@litwareinc.com l'utente dispone dell'accesso. Mostra i servizi associati a tutte le licenze che sono assegnate al suo account.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

Questo esempio mostra i servizi ai quali l'utente BelindaN@litwareinc.com ha accesso dalla prima licenza assegnata al suo account (il numero di indice è 0).
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Per visualizzare tutti i servizi per un utente che è stato assegnato *più licenze*, utilizzare la sintassi seguente:

```
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

  
## <a name="see-also"></a>Vedere anche

Vedere i seguenti argomenti aggiuntivi sulla gestione degli utenti con Office 365 PowerShell:
  
- [Creare account utente con Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Eliminare e ripristinare account utente con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloccare gli account utente con Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Assegnare le licenze agli account utente con Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Rimuovere le licenze dagli account utente con Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Per ulteriori informazioni sui cmdlet utilizzati in questa procedura, vedere i seguenti argomenti:
  
- [ConvertTo-Html](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [Format-List](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>Nuovo utente di Office 365?


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]