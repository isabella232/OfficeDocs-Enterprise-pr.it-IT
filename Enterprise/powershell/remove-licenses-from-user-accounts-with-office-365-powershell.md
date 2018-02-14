---
title: Rimuovere le licenze dagli account utente con Office 365 PowerShell
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Viene illustrato come per rimuovere licenze di Office 365 che sono stati precedentemente assegnate agli utenti di Office 365 PowerShell.
ms.openlocfilehash: c02d5a6cac029ce9beb8077da98418734d935ded
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2018
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Rimuovere le licenze dagli account utente con Office 365 PowerShell

**Riepilogo:** Viene illustrato come per rimuovere licenze di Office 365 che sono stati precedentemente assegnate agli utenti di Office 365 PowerShell.
  
## <a name="before-you-begin"></a>Prima di iniziare

- Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).
    
- Per visualizzare le informazioni sulla licenza piano ( **AccountSkuID** ) nella propria organizzazione, vedere gli argomenti seguenti:
    
  - [Visualizzare le licenze e i servizi con PowerShell di Office 365](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)
    
- Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro _-All_, vengono restituiti solo i primi 500 account.
    
## <a name="the-short-version-instructions-without-explanations"></a>Versione breve (istruzioni senza spiegazioni)
<a name="ShortVersion"> </a>

In questa sezione vengono illustrate le procedure in modo chiaro e senza informazioni superflue. Se si hanno altre domande o si desiderano ulteriori informazioni, è possibile leggere il resto dell'argomento.
  
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

## <a name="the-long-version-instructions-with-detailed-explanations"></a>Versione estesa (istruzioni con spiegazioni dettagliate)
<a name="LongVersion"> </a>

Nothing dura per sempre e che include le licenze di Office 365: prima o poi, vi entreranno volta quando è necessario rimuovere una licenza da un account utente. Forse l'utente sta succedendo lasciare; Forse l'utente non è più necessario licenza; forse -, esistono ovviamente svariati motivi per cui è possibile rimuovere una licenza utente.
  
Prima di continuare qualsiasi è importante tenere presente che è possibile, nonché la rimozione di una licenza richiede, rimuovere la licenza: disabilitazione di tutti i servizi relativi a una licenza non equivale alla rimozione di una licenza. Ad esempio, si supponga che è stata utilizzata backup di tutti i nostri licenze di Office 365; in altre parole, non si hanno alcuna licenza disponibile alcun tipo. Si decide di eseguire la procedura descritta in [disabilitare l'accesso ai servizi di Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) per disabilitare tutti i servizi, ad esempio, in account di Belinda Newman. Dopo che è stata eseguita che, come numero complessivo di licenze si avranno a nostra disposizione? Che è opportuno: zero. Sì, la procedura descritta in questo argomento verrà di *disabilitare* tutti i servizi in licenza di Belinda, ma non disabiliterà (vale a dire, eliminare) la licenza stesso. La licenza continueranno a essere valida e verrà assegnata a Belinda Newman. Sarà semplicemente non sarà in grado di utilizzare la licenza per accedere a tutti i servizi Office 365.
  
E che è importante: se si desidera rimuovere una licenza da un utente è necessario eseguire effettivamente *rimuovere* la licenza. Disattivazione di tutti i servizi impedisce all'utente di accedere a Office 365, ma non liberare il proprio licenza. Se si desidera riprendere il una licenza attualmente assegnato a un utente che è necessario eseguire un comando simile a questo, un comando che utilizza il parametro _RemoveLicenses_ realmente rimuovere la licenza precedentemente assegnata a Belinda:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

Eseguire il comando e Belinda Newman non è più possibile licenza per l'utilizzo di Office 365.
  
> [!NOTE]
> Come si può notare, quando si utilizza il parametro _RemoveLicenses_ che è necessario specificare il nome della licenza da rimuovere. Se non si è certi che piano di licenze è stato utilizzato per assegnare una licenza per l'utente è sufficiente eseguita un comando simile al seguente:`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`
  
Per verificare che la licenza è stata rimossa con successo, usa Get-MsolUser per controllare l'account utente in questione:
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

Se l'operazione è riuscita in base alla pianificazione, la proprietà **isLicensed** di Belinda ora essere impostata `False`:
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
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
   

