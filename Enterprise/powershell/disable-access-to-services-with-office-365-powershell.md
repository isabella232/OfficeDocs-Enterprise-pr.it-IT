---
title: Disattivare l'accesso ai servizi con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/20/2018
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
description: Questo articolo viene illustrato come utilizzare Office 365 PowerShell per disabilitare l'accesso ai servizi di Office 365 per gli utenti dell'organizzazione.
ms.openlocfilehash: d65308746ac5c2b60f4749588455fa66471069e3
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914991"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Disattivare l'accesso ai servizi con PowerShell di Office 365

**Riepilogo:** Questo articolo viene illustrato come utilizzare Office 365 PowerShell per disabilitare l'accesso ai servizi di Office 365 per gli utenti dell'organizzazione.
  
Quando un account Office 365 viene assegnato una licenza da un piano di licenze, servizi di Office 365 vengono resi disponibili per l'utente da tale licenza. Tuttavia, è possibile controllare i servizi di Office 365 che l'utente può accedere. Ad esempio, anche se la licenza consente di accedere al servizio di SharePoint Online, è possibile disattivare l'accesso a esso. È possibile utilizzare Office 365 PowerShell per disabilitare l'accesso a un numero qualsiasi di servizi per un piano di licenza specifico per:

- Un singolo account.
    
- Un gruppo di account.
    
- Tutti gli account nell'organizzazione.
    
## <a name="before-you-begin"></a>Informazioni preliminari
<a name="RTT"> </a>

- Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).
    
- Il cmdlet **Get-MsolAccountSku** per visualizzare i piani di gestione delle licenze disponibili e i servizi di Office 365 disponibili in questi piani. Per ulteriori informazioni, vedere [le licenze di visualizzazione e dei servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Per visualizzare la prima e dopo i risultati delle procedure di questo argomento, vedere [visualizzare i dettagli di licenza e il servizio di account con Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
- È disponibile uno script di PowerShell che consente di automatizzare le procedure descritte in questo argomento. In particolare, lo script consente di visualizzare e disabilitare i servizi nella propria organizzazione Office 365, tra cui oscillazione. Per ulteriori informazioni, vedere [disattivare l'accesso a oscillazione con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
- Se si utilizza il cmdlet **Get-MsolUser** senza utilizzare il parametro _All_ , vengono restituiti solo gli account 500 utente primo.
    
## <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Disabilitare i servizi specifici di Office 365 per utenti specifici per un piano di licenze specifico
  
Per disabilitare un set specifico di servizi di Office 365 per gli utenti di un piano di licenza specifico, eseguire le operazioni seguenti:
  
1. Identificare i servizi indesiderati nel piano di licenze utilizzando la sintassi seguente:
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    Nell'esempio seguente crea un oggetto **LicenseOptions** che consente di disabilitare i servizi Office Online e SharePoint Online nel piano di licenze denominato `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. Utilizzare l'oggetto **LicenseOptions** del passaggio 1 su uno o più utenti.
    
  - Per creare un nuovo account con i servizi disabilitati, utilizzare la sintassi seguente:
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    Nell'esempio seguente viene creato un nuovo account per Allie Bellew che consente di assegnare la licenza e di disabilitare i servizi descritti nel passaggio 1.
    
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

  - Per disabilitare i servizi descritti nel passaggio 1 per tutti gli utenti con licenza esistenti, specificare il nome del piano di Office 365 dalla visualizzazione del cmdlet **Get-MsolAccountSku** (ad esempio **litwareinc: enterprisepack**) e quindi eseguire i comandi seguenti:
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - Per disabilitare i servizi per un gruppo di utenti esistenti, utilizzare uno dei metodi seguenti per identificare gli utenti:
    
  - **Filtrare gli account in base a un attributo account esistente** A tale scopo, utilizzare la sintassi seguente:
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    Nell'esempio seguente consente di disabilitare i servizi per gli utenti del reparto vendite negli Stati Uniti.
    
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
    
2. Eseguire il comando riportato di seguito:
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Se si desidera disabilitare l'accesso ai servizi per più piani di gestione delle licenze, ripetere le istruzioni fornite in precedenza per ciascun piano di licenze, assicurarsi che:

- Gli account utente sono stati assegnati il piano di licenze.
- Per disabilitare i servizi sono disponibili nel piano di gestione delle licenze.

Per disabilitare i servizi di Office 365 per gli utenti mentre sono assegnandoli a un piano di licenze, vedere [disabilitare l'accesso ai servizi durante l'assegnazione delle licenze utente](disable-access-to-services-while-assigning-user-licenses.md).


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
    
Per ulteriori informazioni sui cmdlet utilizzati in questa procedura, vedere i seguenti argomenti:
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Nuovo MsolLicenseOptions](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

