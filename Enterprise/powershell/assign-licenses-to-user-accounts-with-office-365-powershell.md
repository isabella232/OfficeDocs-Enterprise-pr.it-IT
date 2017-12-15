---
title: Assegnare le licenze agli account utente con Office 365 PowerShell
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
- Ent_Office_Other
- LIL_Placement
- DecEntMigration
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: Questo articolo viene illustrato come utilizzare Office 365 PowerShell assegna una licenza di Office 365 per gli utenti senza licenza.
ms.openlocfilehash: 7120b5d61b98f401f9ec1830598f20fbcbecdb66
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
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
    
## <a name="the-short-version-instructions-without-explanations"></a>Versione breve (istruzioni senza spiegazioni)
<a name="ShortVersion"> </a>

In questa sezione vengono presentate le procedure senza spiegazione dettagliata. Domande o altre informazioni, è possibile leggere resto dell'argomento.
  
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
    
- Se non è sufficiente licenze disponibili, le licenze vengono assegnate agli utenti nell'ordine in cui si sta restituiti dal cmdlet **Get-MsolUser** fino ad esaurimento le licenze disponibili.
    
In questo esempio consente di assegnare licenze dal `litwareinc:ENTERPRISEPACK` piano di licenze (Office 365 Enterprise E3) a tutti gli utenti senza licenza.
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

In questo esempio vengono assegnate le stesse licenze agli utenti senza licenza del reparto vendite negli Stati Uniti.
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>Versione estesa (istruzioni con spiegazioni dettagliate)
<a name="LongVersion"> </a>

Come osservato in precedenza nell'articolo [consente di visualizzare gli utenti con licenza e senza licenza con Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md), è possibile lasciare che gli utenti che dispongono di account utente di Office 365 validi, ma che non sono state rilasciate una licenza Office 365. Ciò significa che, account o valido non valido, gli utenti non sarà in grado di accedere a Office 365. E, se non è possibile accedere, non possono trarne vantaggio dei servizi Office 365.
  
Il suddetto articolo fa notare anche che è possibile restituire un elenco di account utente senza licenza eseguendo il comando seguente:
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

Il comando restituisce informazioni su tutti gli utenti che non dispongono di licenze attualmente per Office 365:
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

Come si può notare, si dispone di un utente senza licenza: Belinda Newman. In che modo si passare sull'assegnazione di Belinda una licenza Office 365
  
Per iniziare, dobbiamo eseguire il cmdlet **Get-MsolAccountSku** descritto nell'articolo [View licenze e servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md):
  
```
Get-MsolAccountSku
```

Quel comando restituisce dati simili al seguente:
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

Perché è eseguire **Get-MsolAccountSku** ? ("Sku", nel caso in cui si desidera sapere per, è abbreviazione di "unità SKU." Ai fini del presente che è appena business-parlare "prodotto".) Esistono due motivi per cui si esegue **Get-MsolAccountSku**. Innanzitutto è necessario assicurarsi che in realtà si dispone di una licenza per assegnare Belinda. È disponibile alcun licenze che è possibile assegnare Lei? Per determinare che, è accettare il valore della proprietà **ActiveUnits** (25) e sottrarre i valori delle proprietà **ConsumedUnits** (24) e **WarningUnits** (0):
  
 `25 - 0 - 24 = 1`
  
La proprietà **ActiveUnits** indica il numero di licenze è stato acquistato e il valore combinato di **WarningUnits** e **ConsumedUnits** indica quante licenze sono attualmente in uso. Sottraendo il numero di licenze di pronunciato già dal numero di licenze che abbiamo acquistato, per ottenere il numero di licenze è ancora disponibile. Come fortuna sarebbe è disponibile, si dispone di una licenza disponibile per la distribuzione:
  
 `25 - 0 - 24 = 1`
  
Secondo, per assegnare una nuova licenza è necessario conoscere il nome di questo piano di licenze di Belinda (vale a dire, è necessario conoscere **AccountSkuId** ). In questo caso, è facile: esiste solo un singolo piano di licenze ( `litwareinc:ENTERPRISEPACK`). Tuttavia, è possibile per organizzazioni che hanno più piani di gestione delle licenze. In tal caso, **Get-MsolAccountSku** restituirebbe due diversi **AccountSkuIds**ed è necessario selezionare il piano di licenze appropriato durante l'assegnazione delle licenze. Per il momento, tuttavia, verranno esaminati osserva il caso più semplice e si presuppone che è presente un solo piano di licenze.
  
*Quindi modo assegniamo quindi Belinda Newman una nuova licenza?* Così:
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

È inoltre è necessario effettuare: sufficiente chiamare il cmdlet **Set-MsolUserLicense** , assicurandosi che si specifica il parametro _UserPrincipalName_ dell'utente e il piano di licenze appropriato.
  
**Set-MsolUserLicense** termina quando in esecuzione, verrà visualizzato qualcosa di simile a questo sullo schermo:
  
 `PS C:\\windows\\system32>`
  
In altre parole, non sembra lasciare viene spiegato. Per verificare che l'utente è stata assegnata una licenza, eseguire un comando simile al seguente:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

Se tutto funziona come previsto, è consigliabile vedere che la proprietà isLicensed di Belinda è ora impostata su True:
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [! Ottima domanda Nota sulla sicurezza]: che cosa accade se si tratta di un errore e ha tentato di assegnare una licenza a un utente che dispone già di una licenza? Potrà offrendo due licenze a un singolo utente? > La risposta rapida? No. Office 365 non consentono di assegnare più di una licenza per lo stesso account utente. (Più di una licenza dal piano di licenze stesso, l'operazione è.) Se si tenta di eseguire questa operazione il comando avrà esito negativo con il messaggio di errore: > `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> Se tale messaggio di errore è apparirà fuorviante: la licenza non è in realtà non valida, è appena stato assegnato a un utente che ha già *dispone di* una licenza. Tuttavia, messaggio di errore, l'importante è che un utente non avere con licenze multiple.
  
Come si è appena visto, è molto semplice da usare Office 365 PowerShell per assegnare una singola licenza a un singolo utente. E che favorisce una domanda ovvia: non sarebbero altrettanto semplice, potrebbe essere perfino più facile, utilizzare l'interfaccia di amministrazione di Office 365 per assegnare una singola licenza a un singolo utente? Beh, forse; che dipende in parte, se si è più comodo utilizzare Windows PowerShell o preferiscano utilizzando l'interfaccia di amministrazione di Office 365. Dove indicati Windows PowerShell, è tuttavia quando è necessario assegnare licenze più a più utenti. Ad esempio, questo comando assegna una licenza Office 365 a qualsiasi utente che dispone già di una licenza:
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Nel comando precedente vengono utilizzati **Get-MsolUser** e il parametro _UnlicensedUsersOnly_ per restituire una raccolta di tutti gli account utente senza licenza. La raccolta viene quindi passato al cmdlet **Set-MsolUserLicense** ; a sua volta, **Set-MsolUserLicense** consente di assegnare una licenza (derivato dal `litwareinc:ENTERPRISEPACK` piano di licenze) per ogni utente nella raccolta.
  
AH, ma se è necessario 5 utenti senza licenza ma solo una licenza disponibile? In questo caso **Set-MsolUserLicense** per ottenere la licenza disponibile per il primo utente restituito da **Get-MsolUser**. **Set-MsolUserLicense** quindi perdersi tenterà di assegnare una licenza a quattro utenti, ma tutte e quattro i tentativi di avrà esito negativo e il messaggio di errore seguente:
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
In altri termini, Set-MsolUserLicense non appena esito negativo. In realtà, verrà assegnato il numero di licenze possa. Quindi non riuscirà.
  
Punto provare un altro esempio. Se si desidera assegnare una licenza a tutti gli utenti del reparto vendite. Non c'è problema:
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

In alternativa, se vuoi rendere le cose più semplice e ridurre al minimo i messaggi di errori e l'elaborazione del computer, ti basterà assegnare una licenza agli utenti senza licenza del reparto Vendite:
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Dopo tutto, non esiste alcun punto tenta gli utenti con licenza che dispongono già di una licenza. Come già illustrato in precedenza, che non funzionano.
  
Ecco un altro esempio. Si tratta di acquisizione della licenza per tutti gli utenti negli Stati Uniti che attualmente non dispongono di una licenza Office 365. In questo caso:
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

E così via.
  
> [!NOTE]
> Quanto tempo è necessario per eseguire un comando che, ad esempio, emette licenze per tutti gli utenti senza licenza? È difficile pronunciare: dipende da tutti gli elementi dal numero di utenti è necessario la velocità della connessione di rete. Se si dispone di due centinaia di utenti alla licenza questo verrà inoltrate ragionevolmente rapidamente (vale a dire non saranno necessarie più di uno o due minuti). Se si dispone di 10.000 utenti per la licenza ovviamente avrà più tempo. Ma lontano come dovrebbe seguire per assegnare licenze a 10.000 utenti utilizzando l'interfaccia di amministrazione di Office 365. 
  
Purché siamo sull'argomento, ecco è necessario apportare approfondire durante l'assegnazione delle licenze: se un utente non dispone di un valore configurato per la proprietà **UsageLocation** non sarà in grado di assegnare una licenza Office 365 a tale utente. Al contrario, verrà visualizzato un messaggio di errore simile al seguente:
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
In un po' rotonda, questo messaggio di errore indica che l'utente in questione non è stato assegnato un **UsageLocation**. Come è facile immaginare, la proprietà **UsageLocation** (che indica l'area o un paese in cui l'utente utilizza in genere Office 365) è estremamente importante. Perché? Poiché i servizi disponibili agli utenti dipendono non solo il pacchetto di licenze acquistate ma anche in residenza dell'utente: a causa di regole locali e le normative, alcuni servizi potrebbero non essere disponibile per alcuni utenti. Se un utente non dispone di un **UsageLocation**, Office 365 non avendo la possibilità di sapere quali servizi possono essere esposti regolarmente a tale utente. Pertanto, Office 365 non possono offrire eventuali servizi a tale utente almeno non fino a quando non è stato specificato **UsageLocation** .
  
> [!NOTE]
> Quando si configura un account utente significa immediatamente se esistono eventuali restrizioni associate alla parte specificata del mondo. Ad esempio, se si modifica l' **UsageLocation** per un utente con licenza in Iran ( `IR`), il comando non funzionerà con questo messaggio di errore: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> perché Office 365 non è attualmente disponibile per gli utenti in Iran. Per ulteriori informazioni, vedere [About restrizioni relative alla licenza](https://go.microsoft.com/fwlink/p/?LinkId=691730). Per inciso, Office 365 utilizza i codici di due lettere del paese prodotti da International Organization for Standardization (ISO). È possibile trovare i codici nel [sito web ISO](https://go.microsoft.com/fwlink/p/?LinkId=84073). 
  
Se si desidera verificare che un utente specificato è un **UsageLocation** è possibile utilizzare un comando simile al seguente:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

In alternativa, è possibile restituire un elenco di tutti gli utenti che non possiedono l' **UsageLocation** mediante questo comando:
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> Quando si assegna una licenza a un utente, l'utente, per impostazione predefinita, visualizzeranno l'accesso a tutti i servizi di Office 365 che dispone dell'accesso per l'organizzazione. Ad esempio, se è stato acquistato licenze per Office 365 Enterprise E3, l'utente con contratto multilicenza appena verrà automaticamente concessa accesso ai servizi quali Exchange Online, Skype per Business Online e SharePoint Online. Se si preferisce limitare l'accesso dell'utente a tali servizi (ad esempio, è possibile che un utente ad accedere a SharePoint Online ma *non* di Exchange Online e Skype Business online) quindi, vedere l'articolo [disattivare l'accesso ai servizi con Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md). 
  
## <a name="new-to-office-365"></a>Nuovo utente di Office 365?

||
|:-----|
|![L'icona breve di apprendimento LinkedIn](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New a Office 365?**         Scopri corsi video gratuiti per [i professionisti IT e gli amministratori di Office 365](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), per offerto da Learning LinkedIn. |
   
## <a name="see-also"></a>See Also
<a name="SeeAlso"> </a>

Vedere i seguenti argomenti aggiuntivi sulla gestione degli utenti con Office 365 PowerShell:
  
- [Creare account utente con Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Eliminare e ripristinare account utente con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloccare gli account utente con Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Rimuovere le licenze dagli account utente con Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Per ulteriori informazioni sui cmdlet utilizzati in questa procedura, vedere i seguenti argomenti:
  
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

