---
title: Creare account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Informazioni su come usare PowerShell di Office 365 per creare account utente in Office 365.
ms.openlocfilehash: 95cbefc2caeb61376ed77fe5023cb1c050a8fa07
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004689"
---
# <a name="create-user-accounts-with-office-365-powershell"></a>Creare account utente con Office 365 PowerShell

È possibile utilizzare PowerShell di Office 365 per creare in modo efficiente account utente, in particolare di tipo multiplo. Quando si creano account utente in PowerShell di Office 365, alcune proprietà dell'account sono sempre richieste. Altre proprietà non sono necessarie per creare l'account, ma sono comunque importanti. Tali proprietà sono descritte nella tabella seguente.
  
|**Nome della proprietà**|**Obbligatorio?**|**Descrizione**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |Sì  <br/> |Si tratta del nome visualizzato usato nei servizi Office 365. Ad esempio, Caleb Sills.  <br/> |
|**UserPrincipalName** <br/> |Sì  <br/> |Si tratta del nome dell'account utilizzato per accedere ai servizi Office 365. Ad esempio, CalebS@contoso.onmicrosoft.com.  <br/> |
|**FirstName** <br/> |No  <br/> ||
|**LastName** <br/> |No  <br/> ||
|**LicenseAssignment** <br/> |No  <br/> |Questo è il piano di gestione delle licenze (detto anche piano di licenze, piano Office 365 o SKU) dal quale una licenza disponibile viene assegnata all'account utente. La licenza definisce i servizi Office 365 che sono disponibili per l'account. Non è necessario assegnare una licenza a un utente, quando si crea l'account. Tuttavia, l'account richiede una licenza per accedere ai servizi Office 365. Si hanno a disposizione 30 giorni di tempo per assegnare la licenza all'account utente, dopo averlo creato. |
|**Password** <br/> |No  <br/> | Se non si specifica una password, all'account utente ne viene assegnata una casuale, visibile nei risultati del comando. Se si specifica una password, è necessario che contenga da 8 a 16 caratteri di testo ASCII di uno dei tre tipi seguenti: lettere minuscole, lettere maiuscole, numeri e simboli. <br/> |
|**UsageLocation** <br/> |No  <br/> |Si tratta di un codice paese ISO 3166-1 alpha-2. Ad esempio, US per gli Stati Uniti e FR per la Francia. È importante indicare questo valore, poiché alcuni servizi Office 365 non sono visibili in determinati paesi. In questo caso, è possibile assegnare una licenza a un account utente solo se l'account stesso dispone di un valore configurato. Per altre informazioni, vedere [Informazioni sulle restrizioni di licenza](https://go.microsoft.com/fwlink/p/?LinkId=691730).<br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Usare il modulo di Azure Active Directory PowerShell per Graph

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Una volta stabilita la connessione, utilizzare la sintassi seguente per creare un singolo account:
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

In questo esempio viene creato un account per l'utente degli Stati Uniti chiamato Caleb Sills:
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="create-an-individual-user-account"></a>Creare un account utente singolo

Per creare un singolo account, utilizzare la sintassi seguente:
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
>PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per Windows PowerShell e i cmdlet con **MSOL** all'interno del nome. Per continuare a usare i cmdlet, è necessario eseguirli in Windows PowerShell.
>

Per elencare i nomi dei piani di gestione delle licenze disponibili, usare il seguente comando:

````powershell
Get-MsolAccountSku
````

In questo esempio viene creato un account per l'utente degli Stati Uniti chiamato Caleb Sills, a cui viene assegnata una licenza dal piano `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3).
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a>Creare più account utente

1. Creare un file CSV che includa le necessarie informazioni sull'account utente. Ad esempio:
    
  ```powershell
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
>I nomi della colonna e il loro ordina nella prima riga del file CVS sono arbitrari. Tuttavia, è opportuno assicurarsi che i dati nel resto del file corrispondano all'ordine relativo ai nomi della colonna e li utilizzino per i valori del parametro nel comando PowerShell di Office 365.
    
2. Utilizzare la sintassi seguente:
    
  ```powershell
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

In questo esempio, vengono creati gli account utente dal file denominato C:\My Documents\NewAccounts.csv, quindi vengono registrati i risultati nel file C:\My Documents\NewAccountResults.csv
    
  ```powershell
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. Esaminare il file di output per visualizzare i risultati. Non sono state indicate password, quindi quelle casuali generate da Office 365 sono visibili nel file di output.
    
## <a name="see-also"></a>Vedere anche

[Gestire gli account utente, le licenze e i gruppi con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)
