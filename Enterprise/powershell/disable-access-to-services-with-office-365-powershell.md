---
title: Disattivare l'accesso ai servizi con PowerShell di Office 365
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
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Viene illustrato come utilizzare Office 365 PowerShell per aggiungere o rimuovere l'accesso ai servizi di Office 365 per gli utenti nell'organizzazione.
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Disattivare l'accesso ai servizi con PowerShell di Office 365

**Riepilogo:** Viene illustrato come utilizzare Office 365 PowerShell per aggiungere o rimuovere l'accesso ai servizi di Office 365 per gli utenti nell'organizzazione.
  
Quando un account Office 365 viene assegnato una licenza da un piano di licenze, servizi di Office 365 vengono resi disponibili per l'utente da tale licenza. Tuttavia, è possibile controllare i servizi di Office 365 che l'utente può accedere. Ad esempio, anche se la licenza consente l'accesso a SharePoint Online, è possibile disattivare l'accesso a esso. In realtà, è possibile utilizzare Office 365 PowerShell per disabilitare l'accesso a un numero qualsiasi di servizi per:
- Un singolo account.
    
- Un gruppo di account.
    
- Tutti gli account nell'organizzazione.
    
 **Contenuto:** [La versione breve (istruzioni senza spiegazioni)](disable-access-to-services-with-office-365-powershell.md#ShortVersion) [Versione estesa (istruzioni con spiegazioni dettagliate)](disable-access-to-services-with-office-365-powershell.md#LongVersion) [Vedere anche](disable-access-to-services-with-office-365-powershell.md#SeeAlso)
## <a name="before-you-begin"></a>Prima di iniziare
<a name="RTT"> </a>

- Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).
    
- Il cmdlet **Get-MsolAccountSku** per visualizzare i piani di gestione delle licenze disponibili e i servizi di Office 365 disponibili in questi piani. Per ulteriori informazioni, vedere[le licenze di visualizzazione e dei servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Per visualizzare la prima e dopo i risultati delle procedure di questo argomento, vedere [visualizzare i dettagli di licenza e il servizio di account con Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
- È disponibile uno script di PowerShell che consente di automatizzare le procedure descritte in questo argomento. In particolare, lo script consente di visualizzare e disabilitare i servizi nella propria organizzazione Office 365, tra cui oscillazione. Per ulteriori informazioni, vedere [disattivare l'accesso a oscillazione con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
- Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro _All_, vengono restituiti solo i primi 500 account.
    
## <a name="the-short-version-instructions-without-explanations"></a>Versione breve (istruzioni senza spiegazioni)
<a name="ShortVersion"> </a>

In questa sezione vengono illustrate le procedure in modo chiaro e senza informazioni superflue. Se si hanno altre domande o si desiderano ulteriori informazioni, è possibile leggere il resto dell'argomento.
  
Per disabilitare i servizi di Office 365 per gli utenti da un singolo piano di licenze, eseguire le operazioni seguenti:
  
1. Identificare i servizi indesiderati nel piano di licenze utilizzando la sintassi seguente:
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    Questo esempio viene creato un oggetto **LicenseOptions** che consente di disabilitare i servizi Office Online e SharePoint Online nel piano di licenze denominato `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. Utilizzare l'oggetto **LicenseOptions** dal passaggio 1 in uno o più utenti.
    
  - Per creare un nuovo account con i servizi disabilitati, utilizzare la sintassi seguente:
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    In questo esempio viene creato un nuovo account per Allie Bellew che consente di assegnare la licenza e disabilitare i servizi descritti nel passaggio 1.
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    Per ulteriori informazioni sulla creazione di account utente in Office 365 PowerShell, vedere [creare gli account utente con Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).
    
  - Per disabilitare i servizi per un utente dotato di una licenza esistente, utilizzare la sintassi seguente:
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    In questo esempio vengono disabilitati i servizi per l'utente BelindaN@litwareinc.com.
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - Per disabilitare i servizi descritti nel passaggio 1 per tutti gli utenti con licenza esistenti, specificare il nome del piano di Office 365 dalla visualizzazione del cmdlet **Get-MsolAccountSku** (ad esempio **litwareinc: enterprisepack** ) e quindi eseguire i comandi seguenti:
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - Per disabilitare i servizi per un gruppo di utenti esistenti, utilizzare uno dei metodi seguenti per identificare gli utenti:
    
  - **Filtrare gli account in base a un attributo account esistente** A tale scopo, utilizzare la sintassi seguente:
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    In questo esempio vengono disabilitati i servizi per gli utenti nel reparto vendite degli Stati Uniti.
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **Utilizzare un elenco di account specifici** A tale scopo, eseguire le operazioni seguenti:
    
1. Creare un file di testo contenente un account su ogni riga come riportato di seguito:
    
  ```
  akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

    In questo esempio il file di testo è c:\\documenti\\Accounts.txt.
    
2. Eseguire il comando seguente:
    
  ```
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Per disabilitare i servizi di Office 365 per gli utenti mentre sono assegnandoli a un piano di licenze, vedere [disabilitare l'accesso ai servizi durante l'assegnazione delle licenze utente](disable-access-to-services-while-assigning-user-licenses.md).
  
Per disabilitare i servizi di Office 365 per gli utenti in tutti i piani di gestione delle licenze disponibili, eseguire le operazioni seguenti:
  
1. Copiare e incollare lo script seguente nel Blocco note.
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. Personalizzare i valori seguenti per il proprio ambiente:
    
  -  _<UndesirableService>_In questo esempio, utilizzeremo Office Online e SharePoint Online.
    
  -  _<Account>_In questo esempio, utilizzeremo belindan@litwareinc.com.
    
    Lo script personalizzato avrà l'aspetto seguente:
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. Salvare lo script come `RemoveO365Services.ps1` in un percorso facile da trovare. In questo esempio, si verrà salvare il file in " `C:\\O365 Scripts`".
    
4. Eseguire lo script in Office 365 PowerShell utilizzando il comando seguente.
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> Per annullare gli effetti di una di queste procedure (vale a dire per abilitare di nuovo i servizi disattivati), eseguire di nuovo la procedura, ma utilizzare il valore `$null` per il parametro _DisabledPlans_ .
  
[Torna all'inizio](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a>Versione estesa (istruzioni con spiegazioni dettagliate)
<a name="LongVersion"> </a>

Per impostazione predefinita, tutti i servizi vengono attivati quando si esegue una licenza tramite Office 365 PowerShell. E spesso che è un'ottima soluzione: ciò significa che è possibile in modo semplice e rapido assegnare licenze agli utenti senza dover specificare l'attivazione lungo il modo in cui ogni servizio.
  
Detto che, tuttavia, è anche vero che si desidera limitare i servizi disponibili alcuni utenti; ad esempio, forse alcuni utenti devono disporre di accesso a Office Professional Plus, Skype per Business Online ed Exchange Online, ma gli stessi utenti non hanno accesso a SharePoint Online o in Office Online. È possibile limitare gli account in che modo? In realtà, è possibile. Per spiegare il funzionamento, è necessario un approccio in due passaggi per affrontare il problema:
  
1. Assegna all'utente una licenza di Office 365 che attiva automaticamente tutti i servizi.
    
2. Esegui un paio di comandi di Office 365 PowerShell che disattivano servizi specifici per tale utente.
    
È stata già inclusi nel file passaggio 1: il nostro utente (Belinda Newman) dispone di una licenza di Office 365 che lei consente di accedere a tutti i servizi di Office 365. Tuttavia, si desidera modificare l'account di Belinda in modo che l'utente non dispone dell'accesso a SharePoint Online ( `SHAREPOINTENTERPRISE`) o in Office Online ( `SHAREPOINTWAC`). Ma come stiamo è previsto?
  
Ecco come. Per iniziare, dobbiamo utilizzare il cmdlet **New-MsolLicenseOptions** per creare un oggetto **LicenseOption** contenente i servizi in cui deve essere disabilitati. In caso di Belinda, si desidera disabilitare `SHAREPOINTENTERPRISE` e `SHAREPOINTWAC`, in modo che si utilizza questo comando:
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

Vedere come funziona? Si specifica il piano di licenze ( `litwareinc:ENTERPRISEPACK`) e indica ogni dei servizi da disabilitato, separando i servizi di con una virgola.
  
> [!NOTE]
> Verificare che il nuovo oggetto **LicenseOption** sono archiviati in una variabile. Nell'esempio precedente è stato utilizzato `$x`, sebbene sia possibile utilizzare qualsiasi nome di variabile valido di Windows PowerShell. 
  
A questo punto è possibile utilizzare il seguente comando per disabilitare l'accesso di Belinda per i due servizi:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

Nulla di complicato in questo caso, entrambi: è sufficiente chiamare il cmdlet **Set-MsolUserLicense** e includere il parametro _LicenseOptions_ , con la variabile ( `$x`) contenente i piani di cui si desidera disabilitare. E cosa è visualizzata ora se si analizzerà in informazioni sulla licenza di Belinda eseguendo il comando: `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? Viene visualizzato questo:
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

Molto interessante, vero? E, naturalmente, è possibile eseguire la stessa operazione a più utenti se si desidera. Ad esempio, questi comandi disabilitino gli stessi due servizi tutti gli utenti con licenza. Specificare il nome del piano di Office 365 dalla visualizzazione del cmdlet **Get-MsolAccountSku** (ad esempio **litwareinc: enterprisepack** ) e quindi eseguire tali programmi.
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

Tenere presente che Belinda ancora disponga di una licenza di Office 365 valida; è sufficiente che ora che dispone dell'accesso ai servizi di un numero inferiore. Prima che è stato disabilitato i due servizi, Belinda disponeva newsfeed, OneDrive e SharePoint Online siti:
  
![Utente con accesso a SharePoint.](images/o365_powershell_with_sharepoint.png)
  
Ora queste opzioni non sono più disponibili per lei:
  
![Utente senza accesso a SharePoint.](images/o365_powershell_without_sharepoint.png)
  
Questo è esattamente ciò che volevamo accadesse.
  
E se si modifica il presente in un secondo momento: è possibile abilitare di nuovo questi servizi? Ma certo. Per riattivare tutti i servizi per un utente, è sufficiente utilizzare questo comando per creare l'oggetto **LicenseOption** seguente:
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

Qual è il comando? Per iniziare con la costante di Windows PowerShell `$null` significa "nothing". (Oppure nel leggermente più tecnico Java significa "valore null.") Come si ricorderà, quando si utilizza il cmdlet **New-MsolLicenseOptions** è disponibile indicare i servizi che si desidera disattivata. In questo caso, non vogliamo che uno dei servizi da disabilitare. Che possono provocare a pensare che è possibile utilizzare un comando simile al seguente, un comando di cui non viene specificato un valore per il parametro _DisabledPlans_ :
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

Tuttavia, che non funzionano. Al contrario, verrà generato un messaggio di errore:
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
Fortunatamente per noi, impostare il valore del parametro `$null` funziona:
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

Ciò significa semplicemente che, quando eseguiamo il cmdlet **Set-MsolUserLicense** , si stiamo dicendo a **Set-MsolUserLicense** che non vogliamo che venga disattivato alcun servizio per Belinda:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

E, logicamente, se nessuno dei servizi viene disattivato significa che tutti i servizi sono attivati.
  
Ora che comprendere come funziona tutto ciò, verrà illustrato come è possibile rilasciare una licenza e disattivare i servizi specificati e tutti con lo stesso comando. Che sembra molto importante, ma, in realtà, questa operazione è molto ad esso: è sufficiente includere sia _AddLicenses_ e _LicenseOptions_ parametri nello stesso comando. In altre parole, creare innanzitutto l'oggetto **LicenseOption** :
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

E, come detto in precedenza, si utilizza sia _AddLicenses_ e _LicenseOptions_ parametri nel comando:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

Che comando invierà a Belinda Newman una nuova licenza, ma una licenza in cui Skype Business online ( `SHAREPOINTWAC`) e SharePoint Online ( `SHAREPOINTENTERPRISE`) sono entrambi disattivati.
  
[Torna all'inizio](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a>Nuovo utente di Office 365?
<a name="LongVersion"> </a>

||
|:-----|
|![L'icona breve di apprendimento LinkedIn](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New a Office 365?**         Scopri corsi video gratuiti per **i professionisti IT e gli amministratori di Office 365**, per offerto da Learning LinkedIn. |
   
## <a name="see-also"></a>See also
<a name="SeeAlso"> </a>

Vedere i seguenti argomenti aggiuntivi sulla gestione degli utenti con Office 365 PowerShell:
  
- [Eliminare e ripristinare account utente con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Eliminare e ripristinare account utente con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloccare gli account utente con Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Assegnare le licenze agli account utente con Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Creare account utente con Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
Per ulteriori informazioni sui cmdlet utilizzati in questa procedura, vedere i seguenti argomenti:
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Nuovo MsolLicenseOptions](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
[Torna all'inizio](disable-access-to-services-with-office-365-powershell.md#RTT)
  

