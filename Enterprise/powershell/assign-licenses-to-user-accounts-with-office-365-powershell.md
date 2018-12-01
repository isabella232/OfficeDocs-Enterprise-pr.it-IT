---
title: Assegnare le licenze agli account utente con Office 365 PowerShell
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
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: Questo articolo viene illustrato come utilizzare Office 365 PowerShell assegna una licenza di Office 365 per gli utenti senza licenza.
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123293"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Assegnare le licenze agli account utente con Office 365 PowerShell

**Riepilogo:**  Questo articolo viene illustrato come utilizzare Office 365 PowerShell assegna una licenza di Office 365 per gli utenti senza licenza.
  
Gestione delle licenze gli account utente in Office 365 è importante in quanto gli utenti non possono utilizzare i servizi di Office 365 fino a quando non è stato concesso in licenza il proprio account. È possibile utilizzare Office 365 PowerShell in modo efficiente assegnare licenze agli account senza licenza, soprattutto più account. 

## <a name="before-you-begin"></a>Prima di iniziare
<a name="RTT"> </a>

- Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).
    
- Utilizzare il cmdlet **Get-MsolAccountSku** per visualizzare i piani di gestione delle licenze disponibili e il numero di licenze disponibili in ogni piano all'interno dell'organizzazione. Il numero di licenze disponibili in ogni piano è **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Per ulteriori informazioni sulle licenze di piani, le licenze e servizi, vedere [le licenze di visualizzazione e dei servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Per trovare gli account senza licenza all'interno dell'organizzazione, eseguire il comando`Get-MsolUser -All -UnlicensedUsersOnly`
    
- È possibile assegnare licenze solo per gli account utente con la proprietà **UsageLocation** impostata su un valido ISO 3166-1 alpha-codice di paese 2. Ad esempio, ci per gli Stati Uniti e FR per Francia. Alcuni servizi di Office 365 non sono disponibili in alcune nazioni. Per ulteriori informazioni, vedere [About restrizioni relative alla licenza](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
    Per trovare gli account di cui non sono un valore **UsageLocation** , eseguire il comando `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Per impostare il valore **UsageLocation** su un account, utilizzare la sintassi `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Ad esempio `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.
    
- Se si utilizza il cmdlet **Get-MsolUser** senza utilizzare il `-All` parametro, vengono restituiti solo i primi 500 account.

## <a name="assigning-licenses-to-user-accounts"></a>Assegnazione delle licenze agli account utente
    
Per assegnare una licenza a un utente, utilizzare la sintassi seguente in Office 365 PowerShell:
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

Questo esempio viene assegnata una licenza per il `litwareinc:ENTERPRISEPACK` piano di licenze (Office 365 Enterprise E3) all'utente senza licenza `belindan@litwareinc.com`.
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Per assegnare una licenza a più utenti privi di licenza, utilizzare la sintassi seguente:
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 **Note**
  
- Non è possibile assegnare più licenze a un utente dallo stesso piano di gestione delle licenze.
    
- Se non si dispone di una quantità sufficiente di licenze disponibili, le licenze vengono assegnate agli utenti nell'ordine in cui vengono restituiti dal cmdlet **Get-MsolUser** finché non vengono esaurite le licenze disponibili.
    
In questo esempio consente di assegnare licenze dal `litwareinc:ENTERPRISEPACK` piano di licenze (Office 365 Enterprise E3) a tutti gli utenti senza licenza.
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

In questo esempio vengono assegnate le stesse licenze agli utenti senza licenza del reparto vendite negli Stati Uniti.
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a>Nuovo utente di Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Vedere anche
<a name="SeeAlso"> </a>

Vedere i seguenti argomenti aggiuntivi sulla gestione degli utenti con Office 365 PowerShell:
  
- [Creare gli account utente](create-user-accounts-with-office-365-powershell.md)
    
- [Eliminare e ripristinare gli account utente](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Account utente di blocco](block-user-accounts-with-office-365-powershell.md)
    
- [Rimuovere licenze dagli account utente](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Per ulteriori informazioni sui cmdlet utilizzati in questa procedura, vedere i seguenti argomenti:
  
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

