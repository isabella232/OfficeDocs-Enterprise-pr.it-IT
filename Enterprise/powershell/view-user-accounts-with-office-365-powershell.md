---
title: Visualizzare gli account utente con Office 365 PowerShell
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Riepilogo: Guardare, elencare o visualizzare gli account utente in vari modi con Office 365 PowerShell.'
ms.openlocfilehash: e9ffa439c1840cbbbd8a47c2835d9427330804be
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2018
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Visualizzare gli account utente con Office 365 PowerShell

 **Riepilogo:** Consente di visualizzare, elencare o visualizzare gli account utente in vari modi con Office 365 PowerShell.
  
Sebbene sia possibile utilizzare l'interfaccia di amministrazione di Office 365 per visualizzare gli account per il tenant di Office 365, è possibile utilizzare Office 365 PowerShell ed effettuare alcune operazioni che non è l'interfaccia di amministrazione di Office 365.
  
## <a name="before-you-begin"></a>Prima di iniziare

Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).
  
## <a name="display-office-365-user-account-information"></a>Visualizzare informazioni sull'account utente di Office 365

Per visualizzare un elenco completo degli account utente, eseguire questo comando nel prompt dei comandi di Office 365 PowerShell oppure PowerShell Integrated Script Environment (ISE).
  
```
Get-MsolUser
```

Dovrebbero essere visualizzate informazioni analoghe alle seguenti:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
ZrinkaM@litwareinc.onmicrosoft.com    Zrinka Makovac        True
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Il cmdlet **Get-MsolUser** ha inoltre un set di parametri per filtrare il set di account utente visualizzato. Ad esempio, per l'elenco di utenti senza licenza (gli utenti che sono stati aggiunti a Office 365, ma non sono ancora stati concessi in licenza per utilizzare uno qualsiasi dei servizi), eseguire questo comando.
  
```
Get-MsolUser -UnlicensedUsersOnly
```

Dovrebbero essere visualizzate informazioni analoghe alle seguenti:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Per ulteriori informazioni su ulteriori parametri per filtrare la visualizzazione dei set di account utente visualizzata, vedere [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) .
  
Per essere più selettiva relative all'elenco di account da visualizzare, è possibile utilizzare il cmdlet **Where-Object** in combinazione con il cmdlet **Get-MsolUser** . Per combinare i due cmdlet, si utilizza il carattere "pipe" "|", che indica a Office 365 PowerShell i risultati di un comando e inviarlo al comando successivo. Ecco un comando di esempio che consente di visualizzare solo gli account utente con un percorso di utilizzo non specificata:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

Questo comando indica a PowerShell di Office 365 di:
  
- Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).
    
- Trovare tutti gli account utente con un percorso di utilizzo non specificata ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Parentesi graffe, il comando consente di indicare a Office 365 PowerShell per trovare solo il set di account in cui gli account utente UsageLocation proprietà ( ** $ \_. UsageLocation** ) non è specificata ( **-eq $Null** ).
    
Dovrebbero essere visualizzate informazioni analoghe alle seguenti:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

La proprietà **UsageLocation** è solo una delle numerose proprietà associate a un account utente. Per visualizzare tutte le proprietà degli account utente, utilizzare il cmdlet **Select-Object** e il carattere jolly (*) per visualizzare tutte per un account utente specifico. Di seguito è riportato un esempio:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Dall'elenco, ad esempio, **Città** è il nome di una proprietà di account utente. Ciò significa che è possibile utilizzare il comando seguente per elencare tutti gli account utente per gli utenti che risiedono nella London:
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  La sintassi per il cmdlet **Where-Object** illustrato negli esempi seguenti è **Where-Object {$\_.** [nome proprietà dell'account utente] [operatore di confronto] [valore] **}**. > [operatore di confronto] è **-eq** per uguale a, **-ne** per non equivale a, **-lt** minore di **-gt** per maggiore e ad altri > [valore] in genere è una stringa (una sequenza di lettere, numeri e altri caratteri), un valore numerico o **$Null** per non viene specificato > Per ulteriori informazioni, vedere [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .
  
È possibile controllare lo stato bloccato di un account utente con il comando seguente:
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a>Selezionare le proprietà dell'account utente da visualizzare

Il cmdlet [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) per impostazione predefinita vengono visualizzati tre proprietà degli account utente:
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
Se è necessario proprietà aggiuntive, ad esempio il reparto può essere utilizzato per l'utente e il paese/area geografica in cui l'utente utilizza servizi di Office 365, è possibile eseguire **Get-MsolUser** in combinazione con il cmdlet **Select-Object** per specificare l'elenco di account utente proprietà. Di seguito è riportato un esempio:
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

Questo comando indica a PowerShell di Office 365 di:
  
- Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).
    
- Visualizza solo posizione dell'account utente nome, reparto e dati di utilizzo ( **Select-Object DisplayName, reparto, UsageLocation** ).
    
Dovrebbero essere visualizzate informazioni analoghe alle seguenti:
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
David Longmuir      Operations                               US
Scott Wallace            Operations
```

Il cmdlet **Select-Object** consente di scegliere le proprietà da un comando da visualizzare. Per visualizzare tutte le proprietà degli account utente, utilizzare il carattere jolly (*) per visualizzarli tutti per un account utente specifico. Di seguito è riportato un esempio:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Per essere più selettiva relative all'elenco di account da visualizzare, è possibile anche utilizzare il cmdlet **Where-Object** . Ecco un comando di esempio che consente di visualizzare solo gli account utente con un percorso di utilizzo non specificata:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Questo comando indica a PowerShell di Office 365 di:
  
- Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).
    
- Trovare tutti gli account utente con un percorso di utilizzo non specificata ( **Where-Object {$\_. UsageLocation - eq $Null}** ) e inviare le informazioni ottenute con il comando successivo ( **|** ). Parentesi graffe, il comando è indica a Office 365 PowerShell per trovare solo il set di account in cui gli account utente UsageLocation proprietà ( ** $ \_. UsageLocation** ) non è specificata ( **-eq $Null** ).
    
- Visualizza solo posizione dell'account utente nome, reparto e dati di utilizzo ( **Select-Object DisplayName, reparto, UsageLocation** ).
    
Dovrebbero essere visualizzate informazioni analoghe alle seguenti:
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a>Utilizzare il modulo Azure Active Directory V2 PowerShell per visualizzare gli account utente

Per visualizzare le proprietà degli account utente con il modulo di Azure Active Directory V2 PowerShell, utilizzare il cmdlet [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) . Tuttavia, è innanzitutto necessario connettersi alla sottoscrizione. Per ulteriori informazioni, vedere[Connect con il modulo di Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
### <a name="display-office-365-user-account-information"></a>Visualizzare informazioni sull'account utente di Office 365

Per visualizzare un elenco completo degli account utente, eseguire questo comando nel prompt dei comandi di Office 365 PowerShell oppure PowerShell Integrated Script Environment (ISE).
  
```
Get-AzureADUser
```

Il cmdlet **Get-AzureADUser** per impostazione predefinita vengono visualizzati tre proprietà degli account utente:
  
- ObjectID
    
- DisplayName
    
- UserPrincipalName
    
Per essere più selettiva relative all'elenco di account da visualizzare, è possibile utilizzare il cmdlet **Where-Object** in combinazione con il cmdlet **Get-AzureADUser** . Per combinare i due cmdlet, si utilizza il carattere "pipe" "|", che indica a Office 365 PowerShell i risultati di un comando e inviarlo al comando successivo. Ecco un comando di esempio che consente di visualizzare solo gli account utente con un percorso di utilizzo non specificata:
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

Questo comando indica a PowerShell di Office 365 di:
  
- Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).
    
- Trovare tutti gli account utente con un percorso di utilizzo non specificata ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Parentesi graffe, il comando consente di indicare a Office 365 PowerShell per trovare solo il set di account in cui gli account utente UsageLocation proprietà ( ** $ \_. UsageLocation** ) non è specificata ( **-eq $Null** ).
    
La proprietà **UsageLocation** è solo una delle numerose proprietà associate a un account utente. Per visualizzare tutte le proprietà degli account utente, utilizzare il cmdlet **Select-Object** e il carattere jolly (*) per visualizzare tutte per un account utente specifico, una pagina alla volta ( **più** ). Di seguito è riportato un esempio:
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

Ad esempio, **la località** è il nome di una proprietà di account utente. Ciò significa che è possibile utilizzare il comando seguente per elencare tutti gli account utente per gli utenti che risiedono nella London:
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  La sintassi per il cmdlet **Where-Object** illustrato negli esempi seguenti è **Where-Object {$\_.** [nome proprietà dell'account utente] [operatore di confronto] [valore] **}**. > [operatore di confronto] è **-eq** per uguale a, **-ne** per non equivale a, **-lt** minore di **-gt** per maggiore e ad altri > [valore] in genere è una stringa (una sequenza di lettere, numeri e altri caratteri), un valore numerico o **$Null** per non viene specificato > Per ulteriori informazioni, vedere[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .
  
### <a name="select-the-user-account-properties-to-display"></a>Selezionare le proprietà dell'account utente da visualizzare

Il cmdlet **Get-AzureADUser** per impostazione predefinita vengono visualizzate le proprietà ObjectID, DisplayName e UserPrincipalName degli account utente. Se è necessario proprietà aggiuntive, ad esempio il reparto può essere utilizzato per l'utente e il paese/area geografica in cui l'utente utilizza servizi di Office 365, è possibile eseguire **Get-AzureADUser** in combinazione con il cmdlet **Select-Object** per specificare l'elenco di utenti Proprietà account. Di seguito è riportato un esempio:
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

Questo comando indica a PowerShell di Office 365 di:
  
- Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).
    
- Visualizza solo posizione dell'account utente nome, reparto e dati di utilizzo ( **Select-Object DisplayName, reparto, UsageLocation** ).
    
Per essere più selettiva relative all'elenco di account da visualizzare, è possibile anche utilizzare il cmdlet **Where-Object** . Ecco un comando di esempio che consente di visualizzare solo gli account utente con un percorso di utilizzo non specificata:
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Questo comando indica a PowerShell di Office 365 di:
  
- Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).
    
- Trovare tutti gli account utente con un percorso di utilizzo non specificata ( **Where-Object {$\_. UsageLocation - eq $Null}** ) e inviare le informazioni ottenute con il comando successivo ( **|** ). Parentesi graffe, il comando è indica a Office 365 PowerShell per trovare solo il set di account in cui gli account utente UsageLocation proprietà ( ** $ \_. UsageLocation** ) non è specificata ( **-eq $Null** ).
    
- Visualizza solo posizione dell'account utente nome, reparto e dati di utilizzo ( **Select-Object DisplayName, reparto, UsageLocation** ).
    
## <a name="new-to-office-365"></a>Nuovo utente di Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
  
## <a name="see-also"></a>Vedere anche

#### 

[Gestire gli account utente e le licenze con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)

