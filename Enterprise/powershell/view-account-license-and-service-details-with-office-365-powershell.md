---
title: Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell
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
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Questo articolo viene illustrato come utilizzare Office 365 PowerShell per determinare i servizi di Office 365 che sono stati assegnati agli utenti.
ms.openlocfilehash: 69784b43e6e2b24f776d07a937877e5ae0c74888
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2018
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell

**Riepilogo:** Questo articolo viene illustrato come utilizzare Office 365 PowerShell per determinare i servizi di Office 365 che sono stati assegnati agli utenti.
  
In Office 365, concede in licenza da Gestione licenze piani (anche denominato SKU o Office 365 dei piani) è possibile accedere ai servizi definiti per i piani di Office 365. Tuttavia, un utente potrebbe non avere accesso a tutti i servizi disponibili in una licenza attualmente assegnati a loro. È possibile utilizzare Office 365 PowerShell per visualizzare lo stato dei servizi per gli account utente. 

## <a name="before-you-begin"></a>Prima di iniziare
<a name="RTT"> </a>

- Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).
    
- Utilizzare i comandi `Get-MsolAccountSku` e `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` per trovare le informazioni seguenti:
    
  - I piani di gestione delle licenze che sono disponibili nell'organizzazione.
    
  - I servizi che sono disponibili in ogni piano di gestione delle licenze e l'ordine in cui sono elencati (il numero di indice).
    
     Per ulteriori informazioni sulle licenze di piani di licenza e servizi, vedere [le licenze di visualizzazione e dei servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Utilizzare il comando `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` per individuare le licenze che sono assegnate a un utente e l'ordine in cui sono elencati (numero di indice).
    
- Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro _All_, vengono restituiti solo i primi 500 account.
    
## <a name="the-short-version-instructions-without-explanations"></a>Versione breve (istruzioni senza spiegazioni)
<a name="ShortVersion"> </a>

Per visualizzare tutti i servizi di Office 365 PowerShell che un utente ha accesso, utilizzare la sintassi seguente:
  
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

Per trovare tutti gli utenti con licenza che sono stati abilitati o disabilitati per servizi specifici, utilizzare la sintassi seguente:
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

In questi esempi vengono usate le informazioni seguenti:
  
- La licenza che consente di accedere ai servizi di Office 365 che siamo interessati è la licenza prima che viene assegnata a tutti gli utenti (numero di indice è 0).
    
- I servizi di Office 365 che siamo interessati sono Skype per Business Online ed Exchange Online. Per le licenze che sono associate il piano di licenze, Skype Business online è il servizio 6 elencato (5 è il numero di indice), ed Exchange Online è il servizio 9 elencati (il numero di indice è 8).
    
Questo esempio vengono restituite tutte con licenza gli utenti abilitati per Skype per Business Online ed Exchange Online.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

In questo esempio restituisce tutti gli utenti con licenza non abilitati per Skype Business Online o Exchange Online.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>Versione estesa (istruzioni con spiegazioni dettagliate)
<a name="LongVersion"> </a>

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a>Individuare i servizi di Office 365 PowerShell che un utente ha accesso a

È ovviamente importante sapere quali utenti sono stati rilasciati licenze di Office 365 e gli utenti che non sono. (Vedere l'articolo [consente di visualizzare gli utenti con licenza e senza licenza con Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) per ulteriori informazioni). Tuttavia, è sufficiente disporre di una licenza Office 365 non fornisce alcuna informazione lasciare sulle operazioni che all'utente è effettivamente con Office 365. Possibile potrà utilizzare Exchange Online o Skype Business online? L'utente può accedere SharePoint Online? È necessario l'accesso a Office Professional Plus? Disporre di una licenza significa semplicemente che l'utente è in grado di accedere a tali servizi. Tuttavia, le funzionalità disponibili per un utente dipendono i servizi che sono stati abilitati per il proprio licenze.
  
Come possiamo quindi determinare quali funzionalità di Office 365 un utente ha accesso? Per eseguire che è necessario eseguire un comando simile a questo:
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

In questo comando, viene utilizzato il cmdlet **Get-MsolUser** per restituire informazioni sull'account BelindaN@litwareinc.com. Dopo la restituzione è stata tali informazioni, viene quindi inviata tramite pipe i dati di account al cmdlet **Select-Object** e chiedere a **Select-Object** per "espandere" il valore della proprietà **licenze** :
  
 `Select-Object -ExpandProperty Licenses`
  
Perché dobbiamo farlo? Allora, per impostazione predefinita le **licenze** proprietà ci dice solo il nome del pacchetto di licenze cui proviene la licenza di Belinda da:
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

"Espandiamo" la proprietà **Licenses** ci otteniamo altre informazioni:
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

E quindi, espandendo la proprietà **ServiceStatus** possiamo ottenere ancora altre informazioni:
  
|Servizio plan * * *|Descrizione * * *|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online, piano 2  <br/> |
   
> [!NOTE]
> Ad esempio, che è troppo complicato? Allora, se è possibile inserire backup di una piccola non sei pratico di Windows PowerShell, è possibile eseguire versione ridotta del comando invece: >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`
  
Nel caso in cui si desidera sapere per, è possibile "espandere" la proprietà **Licenses** perché **le licenze** è una proprietà multivalore: si tratta di una singola proprietà che possono essere archiviati più valori. Quando si espande un valore della proprietà a che è semplicemente eseguire il drill-down fino ottenere i valori aggiuntivi riportati che, per impostazione predefinita, non vengono visualizzati sullo schermo.
  
> [!NOTE]
> In che modo puoi quindi sapere se un valore è una proprietà multivalore? Allora, per scoprirlo, prova a eseguire un comando simile al seguente: > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> il cmdlet **Get-member** restituisce informazioni relative all'oggetto stesso. In questo caso, informazioni sulla proprietà valori che compongono un oggetto account utente. Ecco cosa **Get-Member** deve dire in relazione la proprietà **Licenses** : > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> Se la definizione della proprietà dice qualcosa sulle raccolte (in questo caso, `System.Collections.Generic.List`), quindi verificare se ha a che fare con una proprietà multivalore. 
  
In modo che cosa significa tutto questo? Per rispondere, possiamo prima un'altra occhiata alle informazioni restituite dal cmdlet **Get-MsolUser** :
  
```
ServicePlan                       ProvisioningStatus
-----------                       ------------------
SWAY                              Success
INTUNE_O365                       Success
YAMMER_ENTERPRISE                 PendingInput
RMS_S_ENTERPRISE                  Success
OFFICESUBSCRIPTION                Success
MCOSTANDARD                       Success
SHAREPOINTWAC                     Success
SHAREPOINTENTERPRISE              Success
EXCHANGE_S_ENTERPRISE             Success
```

Ed ecco anche una breve panoramica in una tabella in cui viene spiegato cosa questi piani di servizio strani rappresentano veramente:
  
|Servizio plan * * *|Descrizione * * *|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online, piano 2  <br/> |
   
Tutto chiaro?  `MCOSTANDARD` è solo un nome di programmazione interno per Skype per Business Online, mentre `OFFICESUSBCRIPTION` è solo il nome di programmazione interno di Office Professional Plus. Non è più intuitivo significato del mondo, ma poiché questa tabella è mantenuto utile non sarà necessario molti problemi per l'utilizzo dei servizi di Office 365.
  
Ma non è: non esiste più. Come acquisito nell'articolo [View licenze e servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), se è impostato su **ProvisioningStatus** `Success` ciò significa che il servizio è stato abilitato completamente; ad esempio se `MCOSTANDARD` è impostata su `Success` ciò significa che l'utente può accedere Skype Business online. Se è impostato su **ProvisioningStatus** `PendingInput` ciò significa che Office 365 sta ancora elaborando la richiesta di servizio. Tuttavia, l'utente può in genere accedere e accedere al servizio durante la richiesta viene terminata l'elaborazione. ( `YAMMER_ENTERPRISE` verranno sempre visualizzati come `PendingInput`, tuttavia: che non si arresta un utente di accedere a Yammer).
  
> [!IMPORTANT]
> Gli utenti possono installare e attivare una nuova installazione di Office Professional Plus mentre `OFFICESUBSCRIPTION` nel `PendingInput` informazioni sullo stato.
  
E inutile a dirsi, è un servizio è impostato su `Disabled` ciò significa che il servizio in questione non è disponibile per l'utente.
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a>Trovare gli utenti che dispongono dell'accesso a servizi di Office 365 PowerShell specifici

In un articolo separato, sono state riscontrate come è possibile utilizzare Office 365 PowerShell per disabilitare l'accesso utente ai servizi. (Se si perde suddetto articolo, vedere [disabilitare l'accesso ai servizi di Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). Che favorisce una domanda ovvia: non vi è alcun modo per determinare quali *utenti* (vale a dire più di un utente) sono i servizi abilitata o disabilitata?
  
Sono state speranza che un utente potrebbe richiedere che. Per rispondere a questa domanda, è opportuno esaminare la tabella dei servizi che viene per prima cosa nell'articolo [servizi con Office 365 PowerShell e le licenze di visualizzazione](view-licenses-and-services-with-office-365-powershell.md) per il piano di licenze disponibile solo `litwareinc:ENTERPRISEPACK`:
  
|Servizio plan * * *|Descrizione * * *|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online, piano 2  <br/> |
   
Come si ricorderà, il piano di servizio non è altro che il nome di programmazione interno di un prodotto; ad esempio `OFFICESUBSCRIPTION`, nome uno, è il nome di programmazione interno di Office Professional Plus. Se `OFFICESUBSCRIPTION` viene visualizzato come `SUCCESS` nel piano di servizio dell'utente, quindi ciò significa che l'utente possa accedere a Office Professional Plus. Se `EXCHANGE_S_ENTERPRISE` è elencato come `DISABLED` di conseguenza, l'utente non può utilizzare Exchange Online.
  
> [!IMPORTANT]
> Gli utenti possono installare e attivare una nuova installazione di Office Professional Plus mentre `OFFICESUBSCRIPTION` nel `PendingInput` informazioni sullo stato.
  
È il momento in cui è estremamente importante l'ordine in cui vengono visualizzati i servizi. Windows PowerShell viene assegnato un numero di indice per ogni voce nell'elenco. La prima voce è 0, la voce successiva è 1 e così via. Nella tabella seguente vengono descritti i risultati:
  
|Numero di indice * * *|Servizio plan * * *|
|:-----|:-----|
|0  <br/> | `SWAY` <br/> |
|1  <br/> | `INTUNE_O365` <br/> |
|2  <br/> | `YAMMER_ENTERPRISE` <br/> |
|3  <br/> | `RMS_S_ENTERPRISE` <br/> |
|4  <br/> | `OFFICESUBSCRIPTION` <br/> |
|5  <br/> | `MCOSTANDARD` <br/> |
|6  <br/> | `SHAREPOINTWAC` <br/> |
|7  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|8  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
Come si può notare, `SWAY` è il primo servizio elencato, in modo che venga assegnato il numero di indice 0.
  
> [!CAUTION]
> Perché 0 e 1 non? Questo è un aspetto programmazione. Linguaggi di programmazione indici sapere quanto un elemento "sfalsamento" l'inizio della matrice. Il primo elemento *è* l'inizio della matrice, in modo che il relativo argomento offset è 0. Il secondo elemento è 1 dall'inizio della matrice, in modo che la distanza è 1.
  
Punto provare un esempio. Si supponga che si desidera un elenco di tutti gli utenti con licenza che non sono stati abilitati per Exchange Online. A tale scopo, è possibile utilizzare il comando seguente:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

Se è un comando little strani cercando possiamo richiedere qualche minuto per descrivere le modalità di funzionamento. Questo è effettivamente un comando di due parti e la prima parte è molto semplice: viene utilizzato il cmdlet **Get-MsolUser** per restituire una raccolta di tutti gli utenti di Office 365 (concessa in licenza e senza licenza):
  
```
Get-MsolUser
```

Tali informazioni viene inviata tramite pipe al cmdlet **Where-Object** . **Where-Object** esamina tutti gli account utente e cerca tali account che soddisfano entrambi i criteri seguenti:
  
- La proprietà **isLicensed** è uguale a ( `-eq`) `True` ( `$true`). Che ci consente di eliminare gli utenti senza licenza.
    
- Il valore delle licenze **[0]. ServiceStatus [8]. ProvisioningStatus** proprietà è uguale a ( `-eq`) `Disabled`. Ai fini del presente immediate, la parte importante di questo nome di proprietà difficile da gestire è la seguente:
    
     `ServiceStatus[8]`
    
    Il `[8]` rappresenta il numero di indice per Exchange Online. (È possibile sapere che da osservando la tabella alcuni minuti). Se si desidera trovare tutti gli utenti abilitati per Skype Business online? Il numero di indice per Skype Business online è 5, pertanto è necessario utilizzare la sintassi seguente:
    
     `ServiceStatus[5]`
    
    E così via.
    
    Per inciso, `Licenses[0]` indica il piano di licenze che si desidera esaminare. Poiché il dominio di test dispone solo di un piano di licenze ciò non è rilevante. Tuttavia, si supponga un utente che è stato assegnato licenze da due diversi piani di gestione delle licenze. In tal caso, `Licenses[0]` rappresenta il primo piano di gestione delle licenze e `Licenses[1]` potrebbe rappresentare il secondo piano di licenze.
    
    Per trovare le licenze assegnate a un utente e l'ordine in cui sono elencate, esegui il comando seguente:
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

Vuoi vedere come funziona tutto ciò? Il numero di indice per Office Professional Plus è 4. Pertanto, questo comando restituisce un elenco di tutti gli utenti che non sono stati abilitati per Office Professional Plus:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

E se si desidera un elenco di utenti che sono stati *abilitati* per Office Professional Plus? Anche se è stato attivato, quindi la **ServiceStatus** essere costituiti da `PendingInput` o `Success`; in altre parole, la **ServiceStatus** verrà *non* è uguale ( `-ne`) `Disabled`. Vale a dire è sufficiente eseguire il comando precedente e lo swapping il `-eq` operatore per la `-ne` operatore:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

Come l'indica passa, che codice probabilmente non win molti concorsi vantaggio. E verità comunicato, il codice può ottenere ancora altre provare. Si supponga, ad esempio, che si desidera cercare gli utenti che sono stati abilitati per entrambi Skype per Business Online ed Exchange Online:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

Ma non bisogna preoccuparsi troppo su come processo che potrebbe essere: l'importante è che, in maniera relativamente, è possibile recuperare queste informazioni. Impossibile ottenere queste stesse informazioni tramite l'interfaccia di amministrazione di Office 365? In teoria, Sì ma, in termini pratici, no. Per ottenere queste stesse informazioni tramite l'interfaccia di amministrazione di Office 365 è necessario esaminare le informazioni sulla licenze per ogni utente, un utente alla volta e quindi manualmente tenere traccia degli utenti sono stati abilitati per *X* e che non era. Che potrebbe funzionare, ma possiamo essere accurato: se si dispone di più di 10 o 11 utenti, non sarà a tale scopo. È troppo lunghe e noiose.
  
Naturalmente, ovvero il motivo per cui si dispone di Windows PowerShell: Windows PowerShell aiuta a evitare attività lunghe e noiose come questa.
  
Mentre è ora essere, ecco il comando finale per visualizzare informazioni sul servizio:
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[0].ProvisioningStatus}}, @{Name="MDM";Expression={$_.Licenses[0].ServiceStatus[1].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[2].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[3].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[4].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[5].ProvisioningStatus}}, @{Name="OfficeWeb";Expression={$_.Licenses[0].ServiceStatus[6].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[8].ProvisioningStatus}} | ConvertTo-Html > "C:\\My Documents\\Service Info.html"
```

E si un comando molto sorta. Ma viene creato un file CSV con tutti gli utenti e tutto il relativo stato servizio.

  
## <a name="see-also"></a>Vedere anche
<a name="SeeAlso"> </a>

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