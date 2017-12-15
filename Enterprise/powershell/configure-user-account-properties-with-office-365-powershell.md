---
title: "Configurare le proprietà degli account utente con Office 365 PowerShell"
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
- DecEntMigration
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- apr17entnews
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "Sintesi: utilizzare PowerShell di Office 365 per configurare le proprietà di uno o più account utente nel tenant di Office 365."
ms.openlocfilehash: d9e817530f3b1554cb757720f01afec5ed3b63ef
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>Configurare le proprietà degli account utente con Office 365 PowerShell

 **Riepilogo:** Utilizzare Office 365 PowerShell per configurare le proprietà delle singole o più account utente in Office 365 tenant.
  
Sebbene sia possibile utilizzare l'interfaccia di amministrazione di Office 365 per configurare le proprietà degli account utente del tenant di Office 365, è possibile utilizzare anche PowerShell di Office 365 ed eseguire delle operazioni che non sono possibili nell'interfaccia di amministrazione di Office 365.
  
## <a name="before-you-begin"></a>Informazioni preliminari

Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).
  
## <a name="change-properties-for-a-specific-user-account"></a>Modificare le proprietà per un account utente specifico

Per configurare le proprietà per un account utente specifico, utilizzare il cmdlet [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) e specificare le proprietà da impostare o modificare. In questo esempio viene modificata la posizione di utilizzo di Belinda Newman in Francia:
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

Identificare l'account con il parametro **-UserPrincipalName** e impostare o modificare proprietà specifiche con ulteriori parametri. Ecco un elenco dei parametri più comuni.
  
- -Città "\<città >"
    
- -Paese "\<nome del paese >"
    
- -Reparto "\<Nome reparto >"
    
- -DisplayName "\<nome utente completo >"
    
- -Fax "\<numero di fax >"
    
- -FirstName "\<nome utente >"
    
- -LastName "\<cognome utente >"
    
- -MobilePhone "\<numero di cellulare >"
    
- -Office "\<sede >"
    
- -PhoneNumber "\<il numero di telefono di office >"
    
- -PostalCode "\<CAP >"
    
- -PreferredLanguage "\<language >"
    
- -Stato "\<nome stato >"
    
- -StreetAddress "\<indirizzo >"
    
- -Title "\<nome titolo >"
    
- -UsageLocation "\<codice del paese carattere 2 >"
    
    Si tratta del codice paese o area geografica a due lettere ISO 3166-1 alpha-2 (A2).
    
Per ulteriori parametri, vedere [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).
  
Per visualizzare i nomi principali di tutti gli utenti, eseguire il comando seguente.
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Questo comando indica a PowerShell di Office 365 di:
  
- Ottenere tutte le informazioni sugli account utente ( **Get-MsolUser** ) e inviarlo al comando successivo ( **|** ).
    
- Ordinare l'elenco dei nomi dell'entità utente in ordine alfabetico ( **Oggetto Sort UserPrincipalName** ) e inviarlo al comando successivo ( **|** ).
    
- Visualizzare solo la proprietà del nome principale degli utenti per ogni account ( **Select-Object UserPrincipalName** ).
    
- Visualizzare gli elementi in una schermata alla volta ( **More** ).
    
Questo comando vengono elencati tutti gli account di posta. Se si desidera venga visualizzato il nome dell'entità utente di un account basato su una visualizzazione personalizzata nome (nome e cognome), immettere la variabile **$userName** riportata di seguito (rimuovere il \< e > caratteri), e quindi eseguire i comandi seguenti:
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Questo esempio permette di visualizzare il nome principale dell'utente denominato Caleb Sillis.
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Utilizzando una variabile **$upn**, è possibile apportare modifiche ai singoli account in base al nome visualizzato. Ecco un esempio di impostazione della posizione di utilizzo di Belinda Newman in Francia, specificando il nome visualizzato anziché il nome principale dell'utente:
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a>Modificare le proprietà per tutti gli account utente

Per modificare le proprietà per tutti gli utenti, è possibile utilizzare la combinazione di cmdlet **Get-MsolUser** e **Set-MsolUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti in Francia:
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

Questo comando indica a PowerShell di Office 365 di:
  
- Ottenere tutte le informazioni sugli account utente ( **Get-MsolUser** ) e inviarlo al comando successivo ( **|** ).
    
- Impostare la posizione dell'utente in Francia ( **Set-MsolUser -UsageLocation "FR"** ).
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Modificare le proprietà per un set specifico di account utente

Per modificare le proprietà per un set specifico di account utente, è possibile utilizzare la combinazione di cmdlet **Get-MsolUser**, **Where-Object** e **Set-MsolUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti del reparto Contabilità in Francia:
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Questo comando indica a PowerShell di Office 365 di:
  
- Ottenere tutte le informazioni sugli account utente ( **Get-MsolUser** ) e inviarlo al comando successivo ( **|** ).
    
- Trovare tutti gli account utente che il reparto proprietà è impostata su "Contabilità" ( **Where-Object {$_. Reparto - eq "Contabilità"}** ) e inviare le informazioni ottenute con il comando successivo ( **|** ).
    
- Impostare la posizione dell'utente in Francia ( **Set-MsolUser -UsageLocation "FR"** ).
    
- Visualizzare gli elementi in una schermata alla volta ( **More** ).
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a>Utilizzare il modulo Azure Active Directory V2 PowerShell per configurare le proprietà di un account utente

Per configurare le proprietà degli account utente con il modulo di Azure Active Directory V2 PowerShell, utilizzare il cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) e specificare le proprietà per impostare o modificare. Tuttavia, è innanzitutto necessario connettersi alla sottoscrizione. Per ulteriori informazioni, vedere [Connect con il modulo di Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
### <a name="change-properties-for-a-specific-user-account"></a>Modificare le proprietà per un account utente specifico

In questo esempio viene modificata la posizione di utilizzo di Belinda Newman in Francia:
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

Identificare l'account con il parametro **-ObjectID** e impostare o modificare proprietà specifiche con ulteriori parametri. Ecco un elenco dei parametri più comuni.
  
- -Reparto "\<Nome reparto >"
    
- -DisplayName "\<nome utente completo >"
    
- -FacsimilieTelephoneNumber "\<numero di fax >"
    
- -GivenName "\<nome utente >"
    
- -Cognome "\<cognome utente >"
    
- -Per dispositivi mobili "\<numero di cellulare >"
    
- -JobTitle "\<posizione >"
    
- -PreferredLanguage "\<language >"
    
- -StreetAddress "\<indirizzo >"
    
- -Città "\<città >"
    
- -Stato "\<nome stato >"
    
- -PostalCode "\<CAP >"
    
- -Paese "\<nome del paese >"
    
- -TelephoneNumber "\<il numero di telefono di office >"
    
- -UsageLocation "\<codice del paese carattere 2 >"
    
    Si tratta del codice paese o area geografica a due lettere ISO 3166-1 alpha-2 (A2).
    
Per ulteriori parametri, vedere [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).
  
Per visualizzare il nome dell'entità utente per gli account utente, eseguire il comando seguente.
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Questo comando indica a PowerShell di Office 365 di:
  
- Ottenere tutte le informazioni sugli account utente ( **Get-AzureADUser** ) e inviarlo al comando successivo ( **|** ).
    
- Ordinare l'elenco dei nomi dell'entità utente in ordine alfabetico ( **Oggetto Sort UserPrincipalName** ) e inviarlo al comando successivo ( **|** ).
    
- Visualizzare solo la proprietà del nome principale degli utenti per ogni account ( **Select-Object UserPrincipalName** ).
- Visualizzare gli elementi in una schermata alla volta ( **More** ).
    
Questo comando vengono elencati tutti gli account di posta. Se si desidera venga visualizzato il nome dell'entità utente di un account basato su una visualizzazione personalizzata nome (nome e cognome), immettere la variabile **$userName** riportata di seguito (rimuovere il \< e > caratteri), e quindi eseguire i comandi seguenti:
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Questo esempio permette di visualizzare il nome principale dell'utente denominato Caleb Sillis.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Utilizzando una variabile **$upn**, è possibile apportare modifiche ai singoli account in base al nome visualizzato. Ecco un esempio di impostazione della posizione di utilizzo di Belinda Newman in Francia, specificando il nome visualizzato anziché il nome principale dell'utente:
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Modificare le proprietà per tutti gli account utente

Per modificare le proprietà per tutti gli utenti, è possibile utilizzare la combinazione di cmdlet **Get-AzureADUser** e **Set-AzureADUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti in Francia:
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

Questo comando indica a PowerShell di Office 365 di:
  
- Ottenere tutte le informazioni sugli account utente ( **Get-AzureADUser** ) e inviarlo al comando successivo ( **|** ).
    
- Impostare la posizione dell'utente in Francia ( **Set-AzureADUser -UsageLocation "FR"** ).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Modificare le proprietà per un set specifico di account utente

Per modificare le proprietà per un set specifico di account utente, è possibile utilizzare la combinazione dei cmdlet **Get-AzureADUser**, **dove**e **Set-AzureADUser** . Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti nel reparto contabilità in Francia:
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Questo comando indica a PowerShell di Office 365 di:
  
- Ottenere tutte le informazioni sugli account utente ( **Get-AzureADUser** ) e inviarlo al comando successivo ( **|** ).
    
- Trovare tutti gli account utente la cui reparto proprietà è impostata su "Contabilità" ( **dove {$_. Reparto - eq "Contabilità"}** ) e inviare le informazioni ottenute con il comando successivo ( **|** ).
    
- Impostare la posizione dell'utente in Francia ( **Set-AzureADUser -UsageLocation "FR"** ).
    
## <a name="see-also"></a>See also

#### 

[Gestire gli account utente e le licenze con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)

