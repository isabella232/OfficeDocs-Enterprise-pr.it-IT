---
title: Disattivare l'accesso ai servizi con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/28/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Utilizzare Office 365 PowerShell per disabilitare l'accesso ai servizi di Office 365 per gli utenti.
ms.openlocfilehash: 0f2c603edd624c9d53a28b37c1c9795bad05ec0f
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001819"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Disattivare l'accesso ai servizi con PowerShell di Office 365

**Riepilogo:** Viene illustrato come utilizzare Office 365 PowerShell per disabilitare l'accesso ai servizi di Office 365 per gli utenti dell'organizzazione.
  
Quando a un account di Office 365 viene assegnata una licenza da un piano di gestione delle licenze, i servizi di Office 365 vengono resi disponibili all'utente dalla licenza. Tuttavia, è possibile controllare i servizi di Office 365 che l'utente può accedere. Ad esempio, anche se la licenza consente l'accesso al servizio SharePoint Online, è possibile disabilitarne l'accesso. È possibile utilizzare PowerShell per disabilitare l'accesso a qualsiasi numero di servizi per uno specifico piano di gestione delle licenze per:

- Un singolo account.
    
- Un gruppo di account.
    
- Tutti gli account nell'organizzazione.

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Successivamente, utilizzare questo comando per visualizzare i piani di licenza disponibili, noti anche come AccountSkuIds:

```
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

Per ulteriori informazioni, vedere [visualizzare le licenze e i servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
Per visualizzare i risultati precedenti e successivi delle procedure descritte in questo argomento, vedere [View account License and Service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
Uno script PowerShell è disponibile per rendere automatiche le procedure descritte in questo argomento. Nello specifico, lo script consente di visualizzare e disabilitare i servizi nella propria organizzazione di Office 365, tra cui Sway. Per ulteriori informazioni, vedere [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Disabilitare servizi specifici di Office 365 per utenti specifici per uno specifico piano di gestione delle licenze
  
Per disabilitare un set specifico di servizi di Office 365 per gli utenti per uno specifico piano di gestione delle licenze, eseguire le operazioni seguenti:
  
1. Identificare i servizi indesiderati nel piano di gestione delle licenze utilizzando la sintassi seguente:
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

  Nell'esempio seguente viene creato un oggetto **LicenseOptions** che Disabilita i servizi Office Online e SharePoint Online nel piano di gestione delle licenze `litwareinc:ENTERPRISEPACK` denominato (Office 365 Enterprise E3).
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. Utilizzare l'oggetto **LicenseOptions** del passaggio 1 su uno o più utenti.
    
  - Per creare un nuovo account con i servizi disabilitati, utilizzare la sintassi seguente:
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

  Nell'esempio seguente viene creato un nuovo account per Allie Bellew che assegna la licenza e Disabilita i servizi descritti nel passaggio 1.
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

  Per ulteriori informazioni sulla creazione di account utente in Office 365 PowerShell, vedere [creare account utente con office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).
    
  - Per disabilitare i servizi per un utente dotato di una licenza esistente, utilizzare la sintassi seguente:
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

  In questo esempio vengono disabilitati i servizi per l'utente BelindaN@litwareinc.com.
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - Per disabilitare i servizi descritti nel passaggio 1 per tutti gli utenti con licenza esistenti, specificare il nome del piano di Office 365 dalla visualizzazione del cmdlet **Get-MsolAccountSku** (ad esempio **litwareinc: ENTERPRISEPACK**) e quindi eseguire i comandi seguenti:
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  Se si utilizza il cmdlet **Get-MsolUser** senza utilizzare il parametro _All_ , vengono restituiti solo i primi account utente 500.


  - Per disabilitare i servizi per un gruppo di utenti esistenti, utilizzare uno dei metodi seguenti per identificare gli utenti:
    
  - **Filtrare gli account in base a un attributo account esistente** A tale scopo, utilizzare la sintassi seguente:
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  Nell'esempio seguente vengono disabilitati i servizi per gli utenti nel reparto vendite degli Stati Uniti.
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **Utilizzare un elenco di account specifici** A tale scopo, eseguire la procedura seguente:
    
1. Creare un file di testo contenente un account su ogni riga come riportato di seguito:
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  In questo esempio, il file di testo è C\\: My\\Documents. txt.
    
2. Eseguire il comando riportato di seguito:
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Se si desidera disabilitare l'accesso ai servizi per più piani di gestione delle licenze, ripetere le istruzioni sopra riportate per ogni piano di gestione delle licenze, garantendo che:

- Agli account utente è stato assegnato il piano di gestione delle licenze.
- I servizi da disabilitare sono disponibili nel piano di gestione delle licenze.

Per disabilitare i servizi di Office 365 per gli utenti mentre si assegnano a un piano di gestione delle licenze, vedere [disabilitare l'accesso ai servizi durante l'assegnazione di licenze utente](disable-access-to-services-while-assigning-user-licenses.md).


## <a name="new-to-office-365"></a>Nuovo utente di Office 365?
<a name="LinkedIn"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>Vedere anche
<a name="SeeAlso"> </a>

Vedere i seguenti argomenti aggiuntivi sulla gestione degli utenti con Office 365 PowerShell:
  
- [Eliminare e ripristinare account utente con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Eliminare e ripristinare account utente con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloccare gli account utente con Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Assegnare le licenze agli account utente con Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Creare account utente con Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
