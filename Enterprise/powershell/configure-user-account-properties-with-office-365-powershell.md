---
title: Configurare le proprietà degli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/07/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Sintesi: utilizzare PowerShell di Office 365 per configurare le proprietà di uno o più account utente nel tenant di Office 365.'
ms.openlocfilehash: 67ce7d3c57f286f0b2365aa2503fdf1c8bc13429
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257657"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>Configurare le proprietà degli account utente con Office 365 PowerShell

 **Sintesi:** Utilizzare PowerShell di Office 365 per configurare le proprietà di uno o più account utente nel tenant di Office 365.
  
Anche se è possibile utilizzare l'interfaccia di amministrazione di Microsoft 365 per configurare le proprietà degli account utente del tenant di Office 365, è anche possibile utilizzare PowerShell per Office 365 e fare alcuni elementi che non possono essere configurati dal centro di amministrazione.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Usare il modulo di Azure Active Directory PowerShell per Graph

Per configurare le proprietà degli account utente con il modulo Azure Active Directory PowerShell per Graph, utilizzare il cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) e specificare le proprietà da impostare o modificare. 

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
   
### <a name="change-properties-for-a-specific-user-account"></a>Modificare le proprietà per un account utente specifico

Identificare l'account con il parametro **-ObjectID** e impostare o modificare proprietà specifiche con ulteriori parametri. Ecco un elenco dei parametri più comuni.
  
- -Department "\<nome reparto>"
    
- -DisplayName "\<nome utente completo>"
    
- -FacsimilieTelephoneNumber "\<numero fax>"
    
- -GivenName "\<nome utente>"
    
- -Surname "\<cognome utente>"
    
- -Mobile "\<numero cellulare>"
    
- -JobTitle "\<posizione professionale>"
    
- -PreferredLanguage "\<lingua>"
    
- -StreetAddress "\<indirizzo>"
    
- -City "\<nome città>"
    
- -State "\<nome stato>"
    
- -PostalCode "\<CAP>"
    
- -Country "\<nome paese>"
    
- -TelephoneNumber "\<numero di telefono di ufficio>"
    
- -UsageLocation "\<codice paese o area geografica a 2 caratteri>"
    
    Si tratta del codice paese o area geografica a due lettere ISO 3166-1 alpha-2 (A2).
    
Per ulteriori parametri, vedere [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).


Per visualizzare il nome principale degli utenti per gli account utente, eseguire il comando seguente.
  
```powershell
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Questo comando indica a PowerShell di Office 365 di:
  
- Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).
    
- Elencare i nomi principali degli utenti in ordine alfabetico ( **Sort-Object UserPrincipalName** ) e inviarli al comando successivo ( **|** ).
    
- Visualizzare solo la proprietà del nome principale degli utenti per ogni account ( **Select-Object UserPrincipalName** ).
- Visualizzare gli elementi in una schermata alla volta ( **More** ).
    
Con questo comando vengono elencati tutti gli account. Se si desidera visualizzare il nome principale dell'utente di un account in base al nome visualizzato (nome e cognome), inserire la variabile **$userName** sotto (rimuovendo i caratteri \< e >), quindi eseguire i comandi seguenti:
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Questo esempio permette di visualizzare il nome dell’entità utente per l’account utente con nome visualizzato Caleb Sillis.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Utilizzando una variabile **$upn**, è possibile apportare modifiche ai singoli account in base al nome visualizzato. Ecco un esempio di impostazione della posizione di utilizzo di Belinda Newman in Francia, specificando il nome visualizzato anziché il nome principale dell'utente:
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Modificare le proprietà per tutti gli account utente

Per modificare le proprietà per tutti gli utenti, è possibile utilizzare la combinazione di cmdlet **Get-AzureADUser** e **Set-AzureADUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti in Francia:
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

Questo comando indica a PowerShell di Office 365 di:
  
- Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).
    
- Impostare la posizione dell'utente in Francia ( **Set-AzureADUser -UsageLocation "FR"** ).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Modificare le proprietà per un set specifico di account utente

Per modificare le proprietà per un set specifico di account utente, è possibile utilizzare la combinazione di cmdlet **Get-AzureADUser**, **Where** e **Set-AzureADUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti del reparto Contabilità in Francia:
  
```powershell
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Questo comando indica a PowerShell di Office 365 di:
  
- Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).
    
- Individuare tutti gli account utente con la proprietà Department impostata su "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) e inviare le informazioni risultanti al comando successivo ( **|** ).
    
- Impostare la posizione dell'utente in Francia ( **Set-AzureADUser -UsageLocation "FR"** ).
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell

Per configurare le proprietà degli account utente con il modulo di Microsoft Azure Active Directory per Windows PowerShell, utilizzare il cmdlet Set-MsolUser e specificare le proprietà da impostare o modificare. 

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
>[!Note]
>PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per il modulo di Windows PowerShell e i cmdlet con **MSOL** nel proprio nome. Per continuare a utilizzare questi cmdlet, è necessario eseguirli da Windows PowerShell.
>

### <a name="change-properties-for-a-specific-user-account"></a>Modificare le proprietà per un account utente specifico

Per configurare le proprietà per un account utente specifico, utilizzare il cmdlet [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) e specificare le proprietà da impostare o modificare. 

Identificare l'account con il parametro **-UserPrincipalName** e impostare o modificare proprietà specifiche con ulteriori parametri. Ecco un elenco dei parametri più comuni.
  
- -City "\<nome città>"
    
- -Country "\<nome paese>"
    
- -Department "\<nome reparto>"
    
- -DisplayName "\<nome utente completo>"
    
- -Fax "\<numero fax>"
    
- -FirstName "\<nome utente>"
    
- -LastName "\<cognome utente>"
    
- -MobilePhone "\<numero cellulare>"
    
- -Office "\<ubicazione ufficio>"
    
- -PhoneNumber "\<numero di telefono di ufficio>"
    
- -PostalCode "\<CAP>"
    
- -PreferredLanguage "\<lingua>"
    
- -State "\<nome stato>"
    
- -StreetAddress "\<indirizzo>"
    
- -Title "\<nome titolo>"
    
- -UsageLocation "\<codice paese o area geografica a 2 caratteri>"
    
    Si tratta del codice paese o area geografica a due lettere ISO 3166-1 alpha-2 (A2).
    
Per ulteriori parametri, vedere [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).

Per visualizzare i nomi principali di tutti gli utenti, eseguire il comando seguente.
  
```powershell
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Questo comando indica a PowerShell di Office 365 di:
  
- Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).
    
- Elencare i nomi principali degli utenti in ordine alfabetico ( **Sort-Object UserPrincipalName** ) e inviarli al comando successivo ( **|** ).
    
- Visualizzare solo la proprietà del nome principale degli utenti per ogni account ( **Select-Object UserPrincipalName** ).
    
- Visualizzare gli elementi in una schermata alla volta ( **More** ).
    
Con questo comando vengono elencati tutti gli account. Se si desidera visualizzare il nome principale dell'utente di un account in base al nome visualizzato (nome e cognome), inserire la variabile **$userName** sotto (rimuovendo i caratteri \< e >), quindi eseguire i comandi seguenti:
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Questo esempio permette di visualizzare il nome principale dell'utente denominato Caleb Sillis.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Utilizzando una variabile **$upn**, è possibile apportare modifiche ai singoli account in base al nome visualizzato. Ecco un esempio di impostazione della posizione di utilizzo di Belinda Newman in Francia, specificando il nome visualizzato anziché il nome principale dell'utente:
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Modificare le proprietà per tutti gli account utente

Per modificare le proprietà per tutti gli utenti, è possibile utilizzare la combinazione di cmdlet **Get-MsolUser** e **Set-MsolUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti in Francia:
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

Questo comando indica a PowerShell di Office 365 di:
  
- Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).
    
- Impostare la posizione dell'utente in Francia ( **Set-MsolUser -UsageLocation "FR"** ).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Modificare le proprietà per un set specifico di account utente

Per modificare le proprietà per un set specifico di account utente, è possibile utilizzare la combinazione di cmdlet **Get-MsolUser**, **Where-Object** e **Set-MsolUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti del reparto Contabilità in Francia:
  
```powershell
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Questo comando indica a PowerShell di Office 365 di:
  
- Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).
    
- Individuare tutti gli account utente con la proprietà Department impostata su "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) e inviare le informazioni risultanti al comando successivo ( **|** ).
    
- Impostare la posizione dell'utente in Francia ( **Set-MsolUser -UsageLocation "FR"** ).
    

## <a name="see-also"></a>Vedere anche

[Gestire gli account utente e le licenze con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)
