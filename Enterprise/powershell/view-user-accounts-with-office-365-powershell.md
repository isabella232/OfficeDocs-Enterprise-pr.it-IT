---
title: Visualizzare gli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
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
ms.openlocfilehash: f2743197456cc56f654e99e682108230420384c9
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123253"
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Visualizzare gli account utente con Office 365 PowerShell

**Riepilogo:** Visualizzare gli account utente in vari modi con Office 365 PowerShell.
  
Sebbene sia possibile utilizzare l'interfaccia di amministrazione di Office 365 per visualizzare gli account per il tenant di Office 365, è possibile utilizzare Office 365 PowerShell ed effettuare alcune operazioni che non è l'interfaccia di amministrazione di Office 365.
  
## <a name="before-you-begin"></a>Prima di iniziare

Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).
  
## <a name="display-office-365-user-account-information-with-azure-active-directory-powershell-for-graph"></a>Visualizzare le informazioni sull'account utente di Office 365 con Azure Active Directory PowerShell di grafico 

Nelle sezioni seguenti viene descritto come visualizzare le informazioni sull'account utente.

### <a name="all-accounts"></a>Tutti gli account

Per visualizzare un elenco completo degli account utente, eseguire questo comando:
  
```
Get-AzureADUser
```

Dovrebbero essere visualizzate informazioni analoghe alle seguenti:
  
```
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="a-specific-account"></a>Un account specifico

Per visualizzare un account utente specifico, immettere il nome principale utente (UPN) dell'account utente, rimuovere il "<" e ">" caratteri e di eseguire il comando seguente:
  
```
Get-AzureADUser -ObjectID <UPN of user account>
```

### <a name="additional-property-values-for-a-specific-account"></a>Valori di proprietà aggiuntive per un account specifico

Per impostazione predefinita, il cmdlet **Get-AzureADUser** Visualizza solo le proprietà ObjectID, DisplayName e UserPrincipalName dell'account.

Per essere più selettiva relative all'elenco delle proprietà per visualizzare, è possibile utilizzare il cmdlet **Select-Object** in combinazione con il cmdlet **Get-AzureADUser** . Per combinare i due cmdlet, si utilizza il carattere "pipe" "|", che indica di Azure Active Directory PowerShell di grafico dei risultati di un comando e inviarlo al comando successivo. Ecco un comando di esempio che mostra il DisplayName, reparto e UsageLocation per ogni account utente:
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

Questo comando indica a PowerShell di Office 365 di:
  
- Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).
    
- Visualizza solo posizione dell'account utente nome, reparto e dati di utilizzo ( **Select-Object DisplayName, reparto, UsageLocation** ).
  
Per visualizzare tutte le proprietà degli account utente, utilizzare il cmdlet **Select-Object** e il carattere jolly (*) per visualizzare tutte per un account utente specifico. Di seguito è riportato un esempio:
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Come ulteriore esempio, è possibile controllare lo stato di attivazione di un account utente specifico utilizzando il seguente comando:
  
```
Get-AzureADUser -ObjectID <UPN of user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="some-accounts-based-on-a-common-property"></a>Alcuni account basato su una proprietà comune

Per essere più selettiva relative all'elenco di account da visualizzare, è possibile utilizzare il cmdlet **Where-Object** in combinazione con il cmdlet **Get-AzureADUser** . Per combinare i due cmdlet, si utilizza il carattere "pipe" "|", che indica di Azure Active Directory PowerShell di grafico dei risultati di un comando e inviarlo al comando successivo. Ecco un comando di esempio che consente di visualizzare solo gli account utente con un percorso di utilizzo non specificata:
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

Questo comando consente di Azure Active Directory PowerShell di grafico per:
  
- Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).
    
- Trovare tutti gli account utente con un percorso di utilizzo non specificata ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Parentesi graffe, il comando consente di indicare a Office 365 PowerShell per trovare solo il set di account in cui gli account utente UsageLocation proprietà ( ** $ \_. UsageLocation** ) non è specificata ( **-eq $Null** ).
    
La proprietà **UsageLocation** è solo una delle numerose proprietà associate a un account utente. Per visualizzare tutte le proprietà degli account utente, utilizzare il cmdlet **Select-Object** e il carattere jolly (*) per visualizzare tutte per un account utente specifico. Di seguito è riportato un esempio:
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

In questo elenco, **City** è il nome di una proprietà dell'account utente. Questo significa che è possibile usare il comando seguente per elencare tutti gli account degli utenti che vivono a Londra:
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  La sintassi per il cmdlet **Where-Object** illustrato negli esempi seguenti è **Where-Object {$\_.** [nome proprietà dell'account utente] [operatore di confronto] [valore] **}**. > [operatore di confronto] è **-eq** per uguale a, **-ne** per non equivale a, **-lt** minore di **-gt** per maggiore e altri utenti.  [valore] viene in genere una stringa (una sequenza di lettere, numeri e altri caratteri), un valore numerico o **$Null** per non viene specificato > Per ulteriori informazioni, vedere [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) .
  

## <a name="display-office-365-user-account-information-with-microsoft-azure-active-directory-module-for-windows-powershell"></a>Visualizzare le informazioni sull'account utente di Office 365 con Microsoft Azure Active Directory Module per Windows PowerShell

Nelle sezioni seguenti viene descritto come visualizzare le informazioni sull'account utente.

### <a name="all-accounts"></a>Tutti gli account

Per visualizzare un elenco completo degli account utente, eseguire questo comando:
  
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

Per ulteriori informazioni su ulteriori parametri per filtrare la visualizzazione dei set di account utente visualizzata, vedere [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).
  

### <a name="a-specific-account"></a>Un account specifico

Per visualizzare un account utente specifico, immettere il nome principale utente (UPN) dell'account utente, rimuovere il "<" e ">" caratteri e di eseguire il comando seguente:
  
```
Get-MsolUser -UserPrincipalName <UPN of user account>
```

### <a name="some-accounts-based-on-a-common-property"></a>Alcuni account basato su una proprietà comune

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

In questo elenco, **City** è il nome di una proprietà dell'account utente. Questo significa che è possibile usare il comando seguente per elencare tutti gli account degli utenti che vivono a Londra:
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  La sintassi per il cmdlet **Where-Object** illustrato negli esempi seguenti è **Where-Object {$\_.** [nome proprietà dell'account utente] [operatore di confronto] [valore] **}**.  [operatore di confronto] è **-eq** per uguale a, **-ne** per non equivale a, **-lt** minore di **-gt** per maggiore e altri utenti.  [valore] è in genere una stringa (una sequenza di lettere, numeri e altri caratteri), un valore numerico o **$Null** per non viene specificato. Per ulteriori informazioni, vedere [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .
  
È possibile controllare lo stato bloccato di un account utente con il comando seguente:
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="additional-property-values-for-accounts"></a>Valori di proprietà aggiuntive per gli account

Il cmdlet **Get-MsolUser** per impostazione predefinita vengono visualizzati tre proprietà degli account utente:
  
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
Scott Wallace           Operations
```

Il cmdlet **Select-Object** consente di scegliere le proprietà da un comando da visualizzare. Per visualizzare tutte le proprietà degli account utente, utilizzare il carattere jolly (*) per visualizzarli tutti per un account utente specifico. Di seguito è riportato un esempio:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Per selezionare in modo più restrittivo l'elenco di account da visualizzare, è possibile utilizzare il cmdlet **Where-Object**. Ecco un comando di esempio che visualizza soltanto gli account utente con un percorso di utilizzo non specificato:
  
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

Se si utilizza la sincronizzazione delle directory per creare e gestire gli utenti di Office 365, è possibile visualizzare quale account locale è in stato piano da un utente di Office 365. Il seguente esempio si presuppone che Connetti Azure Active Directory sono stato configurato per utilizzare l'ancoraggio origine predefinita della ObjectGUID (per ulteriori informazioni sulla configurazione di un punto di ancoraggio di origine, vedere [Connetti Azure Active Directory: progettare concetti](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) e si presuppone che il modulo di Active Directory per powershell stati installati (vedere [Strumenti RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="new-to-office-365"></a>Nuovo utente di Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
  
## <a name="see-also"></a>Vedere anche

[Gestire gli account utente e le licenze con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)

