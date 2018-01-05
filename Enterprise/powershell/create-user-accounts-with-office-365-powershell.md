---
title: Creare account utente con Office 365 PowerShell
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
- apr17entnews
- Ent_Office_Other
- DecEntMigration
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Informazioni su come usare PowerShell di Office 365 per creare account utente in Office 365.
ms.openlocfilehash: 9f6eb4cafa82ae511e806b7e32f2ed98a065d52e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="create-user-accounts-with-office-365-powershell"></a>Creare account utente con Office 365 PowerShell

**Sintesi**: Informazioni su come usare PowerShell di Office 365 per creare account utente in Office 365.
  
È possibile utilizzare PowerShell di Office 365 per creare in modo efficiente account utente, in particolare di tipo multiplo. Quando si creano account utente in PowerShell di Office 365, alcune proprietà dell'account sono sempre richieste. Altre proprietà non sono necessarie per creare l'account, ma sono comunque importanti. Tali proprietà sono descritte nella tabella seguente.
  
****

|**Nome della proprietà**|**Obbligatorio?**|**Descrizione**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |Sì  <br/> |Si tratta del nome visualizzato usato nei servizi Office 365. Ad esempio, Caleb Sills.  <br/> |
|**UserPrincipalName** <br/> |Sì  <br/> |Si tratta del nome dell'account utilizzato per accedere ai servizi Office 365. Ad esempio, CalebS@contoso.onmicrosoft.com.  <br/> |
|**FirstName** <br/> |No  <br/> ||
|**LastName** <br/> |No  <br/> ||
|**LicenseAssignment** <br/> |No  <br/> |Questo è il piano di gestione delle licenze (detto anche piano di licenze, piano Office 365 o SKU) dal quale una licenza disponibile viene assegnata all'account utente. La licenza definisce i servizi Office 365 che sono disponibili per l'account. Non è necessario assegnare una licenza a un utente, quando si crea l'account. Tuttavia, l'account richiede una licenza per accedere ai servizi Office 365. Si hanno a disposizione 30 giorni di tempo per assegnare la licenza all'account utente, dopo averlo creato.<br/> Utilizzare il cmdlet **Get-MsolAccountSku** per visualizzare i piani di gestione delle licenze ( **AccountSkuId** ) e le licenze disponibili nell'organizzazione. Per ulteriori informazioni, vedere [Visualizzare le licenze e i servizi con PowerShell di Office 365](view-licenses-and-services-with-office-365-powershell.md).  <br/> |
|**Password** <br/> |No  <br/> | Se non si specifica una password, all'account utente ne viene assegnata una casuale, visibile nei risultati del comando. Se si specifica una password, è necessario che rispetti i seguenti requisiti di complessità: <br/>  Da 8 a 16 caratteri di testo ASCII. <br/>  Caratteri di uno dei tre tipi seguenti: lettere minuscole: lettere minuscole, lettere maiuscole, numeri e simboli. <br/> |
|**UsageLocation** <br/> |No  <br/> |Si tratta di un codice paese ISO 3166-1 alpha-2. Ad esempio, US per gli Stati Uniti e FR per la Francia. È importante indicare questo valore, poiché alcuni servizi Office 365 non sono visibili in determinati paesi. In questo caso, è possibile assegnare una licenza a un account utente solo se l'account stesso dispone di un valore configurato. Per altre informazioni, vedere [Informazioni sulle restrizioni di licenza](https://go.microsoft.com/fwlink/p/?LinkId=691730).<br/> |
   
## <a name="before-you-begin"></a>Prima di iniziare

Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a>Utilizzare PowerShell di Office 365 per creare account utente individuali

Per creare un singolo account, utilizzare la sintassi seguente:
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

In questo esempio viene creato un account per l'utente degli Stati Uniti chiamato Caleb Sills. Inoltre, gli viene assegnata una licenza dal piano  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3).
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a>Utilizzare PowerShell di Office 365 per creare più account utente

1. Creare un file CSV che includa le necessarie informazioni sull'account utente. Ad esempio:
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
>I nomi della colonna e il loro ordina nella prima riga del file CVS sono arbitrari. Tuttavia, è opportuno assicurarsi che i dati nel resto del file corrispondano all'ordine relativo ai nomi della colonna e li utilizzino per i valori del parametro nel comando PowerShell di Office 365.
    
2. Utilizzare la sintassi seguente:
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

In questo esempio, vengono creati gli account utente dal file denominato C:\My Documents\NewAccounts.csv, quindi vengono registrati i risultati nel file C:\My Documents\NewAccountResults.csv
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. Esaminare il file di output per visualizzare i risultati. Non sono state indicate password, quindi quelle casuali assegnate sono visibili nel file di output.
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a>Utilizzare il modulo Azure Active Directory V2 PowerShell per creare account utente individuali

Per utilizzare il cmdlet **New-AzureADUser** dal modulo Azure Active Directory V2 PowerShell, è necessario innanzitutto connettersi alla propria sottoscrizione. Per visualizzare le istruzioni, consultare [Connettersi con il modulo Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
Una volta stabilita la connessione, utilizzare la sintassi seguente per creare un singolo account:
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

In questo esempio viene creato un account per l'utente degli Stati Uniti chiamato Caleb Sills:
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a>Vedere anche

Vedere i seguenti argomenti aggiuntivi sulla gestione degli utenti con Office 365 PowerShell:
  
- [Eliminare e ripristinare account utente con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloccare gli account utente con Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Assegnare le licenze agli account utente con Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Rimuovere le licenze dagli account utente con Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Per ulteriori informazioni sui cmdlet utilizzati in questa procedura, vedere i seguenti argomenti:
  
- [Export-Csv](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- [Import-Csv]((https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv))
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

