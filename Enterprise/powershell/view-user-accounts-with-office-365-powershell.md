---
title: Visualizzare gli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
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
ms.openlocfilehash: e95353602b96babe5c80f7d57462370636dd26fa
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730321"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="e798f-103">Visualizzare gli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e798f-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="e798f-104">**Riepilogo:** Visualizzare gli account utente in vari modi con Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e798f-104">**Summary:** View your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="e798f-105">Sebbene sia possibile utilizzare l'interfaccia di amministrazione di Office 365 per visualizzare gli account per il tenant di Office 365, è possibile utilizzare Office 365 PowerShell ed effettuare alcune operazioni che non è l'interfaccia di amministrazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="e798f-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e798f-106">Utilizzare grafico modulo di Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="e798f-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e798f-107">Primo, [la connessione al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="e798f-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="e798f-108">Visualizzare tutti gli account</span><span class="sxs-lookup"><span data-stu-id="e798f-108">View all accounts</span></span>

<span data-ttu-id="e798f-109">Per visualizzare un elenco completo degli account utente, eseguire questo comando:</span><span class="sxs-lookup"><span data-stu-id="e798f-109">To display the full list of user accounts, run this command:</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="e798f-110">Dovrebbero essere visualizzate informazioni analoghe alle seguenti:</span><span class="sxs-lookup"><span data-stu-id="e798f-110">You should see information similar to this:</span></span>
  
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

### <a name="view-a-specific-account"></a><span data-ttu-id="e798f-111">Visualizzare un account specifico</span><span class="sxs-lookup"><span data-stu-id="e798f-111">View a specific account</span></span>

<span data-ttu-id="e798f-112">Per visualizzare un account utente specifico, riempimento in nome account di accesso dell'account utente, noto anche come il nome principale (UPN), rimuovere il "<" e ">" caratteri e di eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="e798f-112">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="e798f-113">Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="e798f-113">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="e798f-114">Visualizzare i valori di proprietà aggiuntive per un account specifico</span><span class="sxs-lookup"><span data-stu-id="e798f-114">View additional property values for a specific account</span></span>

<span data-ttu-id="e798f-115">Per impostazione predefinita, il cmdlet **Get-AzureADUser** Visualizza solo le proprietà ObjectID, DisplayName e UserPrincipalName dell'account.</span><span class="sxs-lookup"><span data-stu-id="e798f-115">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="e798f-p101">Per essere più selettiva relative all'elenco delle proprietà per visualizzare, è possibile utilizzare il cmdlet **Select-Object** in combinazione con il cmdlet **Get-AzureADUser** . Per combinare i due cmdlet, si utilizza il carattere "pipe" "|", che indica di Azure Active Directory PowerShell di grafico dei risultati di un comando e inviarlo al comando successivo. Ecco un comando di esempio che mostra il DisplayName, reparto e UsageLocation per ogni account utente:</span><span class="sxs-lookup"><span data-stu-id="e798f-p101">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="e798f-119">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="e798f-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e798f-120">Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="e798f-120">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e798f-121">Visualizza solo posizione dell'account utente nome, reparto e dati di utilizzo ( **Select-Object DisplayName, reparto, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="e798f-121">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="e798f-p102">Per visualizzare tutte le proprietà degli account utente, utilizzare il cmdlet **Select-Object** e il carattere jolly (\*) per visualizzare tutte per un account utente specifico. Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="e798f-p102">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="e798f-124">Come ulteriore esempio, è possibile controllare lo stato di attivazione di un account utente specifico utilizzando il seguente comando:</span><span class="sxs-lookup"><span data-stu-id="e798f-124">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="e798f-125">Visualizzare alcuni account basato su una proprietà comune</span><span class="sxs-lookup"><span data-stu-id="e798f-125">View some accounts based on a common property</span></span>

<span data-ttu-id="e798f-p103">Per essere più selettiva relative all'elenco di account da visualizzare, è possibile utilizzare il cmdlet **Where-Object** in combinazione con il cmdlet **Get-AzureADUser** . Per combinare i due cmdlet, si utilizza il carattere "pipe" "|", che indica di Azure Active Directory PowerShell di grafico dei risultati di un comando e inviarlo al comando successivo. Ecco un comando di esempio che consente di visualizzare solo gli account utente con un percorso di utilizzo non specificata:</span><span class="sxs-lookup"><span data-stu-id="e798f-p103">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="e798f-129">Questo comando consente di Azure Active Directory PowerShell di grafico per:</span><span class="sxs-lookup"><span data-stu-id="e798f-129">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="e798f-130">Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="e798f-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e798f-p104">Trovare tutti gli account utente con un percorso di utilizzo non specificata ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Parentesi graffe, il comando consente di indicare a Office 365 PowerShell per trovare solo il set di account in cui gli account utente UsageLocation proprietà ( \*\* $ \_. UsageLocation\*\* ) non è specificata ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="e798f-p104">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="e798f-p105">La proprietà **UsageLocation** è solo una delle numerose proprietà associate a un account utente. Per visualizzare tutte le proprietà degli account utente, utilizzare il cmdlet **Select-Object** e il carattere jolly (\*) per visualizzare tutte per un account utente specifico. Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="e798f-p105">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="e798f-p106">In questo elenco, **City** è il nome di una proprietà dell'account utente. Questo significa che è possibile usare il comando seguente per elencare tutti gli account degli utenti che vivono a Londra:</span><span class="sxs-lookup"><span data-stu-id="e798f-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="e798f-p107">La sintassi per il cmdlet **Where-Object** illustrato negli esempi seguenti è **Where-Object {$\_.** [nome proprietà dell'account utente] [operatore di confronto] [valore] **}**. > [operatore di confronto] è **-eq** per uguale a, **-ne** per non equivale a, **-lt** minore di **-gt** per maggiore e altri utenti.  [valore] viene in genere una stringa (una sequenza di lettere, numeri e altri caratteri), un valore numerico o **$Null** per non viene specificato > Per ulteriori informazioni, vedere [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) .</span><span class="sxs-lookup"><span data-stu-id="e798f-p107">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e798f-141">Utilizzare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e798f-141">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e798f-142">Primo, [la connessione al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="e798f-142">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="e798f-143">Visualizzare tutti gli account</span><span class="sxs-lookup"><span data-stu-id="e798f-143">View all accounts</span></span>

<span data-ttu-id="e798f-144">Per visualizzare un elenco completo degli account utente, eseguire questo comando:</span><span class="sxs-lookup"><span data-stu-id="e798f-144">To display the full list of user accounts, run this command:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="e798f-145">Dovrebbero essere visualizzate informazioni analoghe alle seguenti:</span><span class="sxs-lookup"><span data-stu-id="e798f-145">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="e798f-p108">Il cmdlet **Get-MsolUser** ha inoltre un set di parametri per filtrare il set di account utente visualizzato. Ad esempio, per l'elenco di utenti senza licenza (gli utenti che sono stati aggiunti a Office 365, ma non sono ancora stati concessi in licenza per utilizzare uno qualsiasi dei servizi), eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="e798f-p108">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="e798f-148">Dovrebbero essere visualizzate informazioni analoghe alle seguenti:</span><span class="sxs-lookup"><span data-stu-id="e798f-148">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="e798f-149">Per ulteriori informazioni su ulteriori parametri per filtrare la visualizzazione dei set di account utente visualizzata, vedere [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="e798f-149">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="e798f-150">Visualizzare un account specifico</span><span class="sxs-lookup"><span data-stu-id="e798f-150">View a specific account</span></span>

<span data-ttu-id="e798f-151">Per visualizzare un account utente specifico, compilare il nome di accesso dell'account utente dell'account utente, noto anche come il nome principale (UPN), rimuovere il "<" e ">" caratteri e di eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="e798f-151">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="e798f-152">Visualizzare alcuni account basato su una proprietà comune</span><span class="sxs-lookup"><span data-stu-id="e798f-152">View some accounts based on a common property</span></span>

<span data-ttu-id="e798f-p109">Per essere più selettiva relative all'elenco di account da visualizzare, è possibile utilizzare il cmdlet **Where-Object** in combinazione con il cmdlet **Get-MsolUser** . Per combinare i due cmdlet, si utilizza il carattere "pipe" "|", che indica a Office 365 PowerShell i risultati di un comando e inviarlo al comando successivo. Ecco un comando di esempio che consente di visualizzare solo gli account utente con un percorso di utilizzo non specificata:</span><span class="sxs-lookup"><span data-stu-id="e798f-p109">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="e798f-156">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="e798f-156">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e798f-157">Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="e798f-157">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e798f-p110">Trovare tutti gli account utente con un percorso di utilizzo non specificata ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Parentesi graffe, il comando consente di indicare a Office 365 PowerShell per trovare solo il set di account in cui gli account utente UsageLocation proprietà ( \*\* $ \_. UsageLocation\*\* ) non è specificata ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="e798f-p110">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="e798f-160">Dovrebbero essere visualizzate informazioni analoghe alle seguenti:</span><span class="sxs-lookup"><span data-stu-id="e798f-160">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="e798f-p111">La proprietà **UsageLocation** è solo una delle numerose proprietà associate a un account utente. Per visualizzare tutte le proprietà degli account utente, utilizzare il cmdlet **Select-Object** e il carattere jolly (\*) per visualizzare tutte per un account utente specifico. Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="e798f-p111">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="e798f-p112">In questo elenco, **City** è il nome di una proprietà dell'account utente. Questo significa che è possibile usare il comando seguente per elencare tutti gli account degli utenti che vivono a Londra:</span><span class="sxs-lookup"><span data-stu-id="e798f-p112">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="e798f-p113">La sintassi per il cmdlet **Where-Object** illustrato negli esempi seguenti è **Where-Object {$\_.** [nome proprietà dell'account utente] [operatore di confronto] [valore] **}**.  [operatore di confronto] è **-eq** per uguale a, **-ne** per non equivale a, **-lt** minore di **-gt** per maggiore e altri utenti.  [valore] è in genere una stringa (una sequenza di lettere, numeri e altri caratteri), un valore numerico o **$Null** per non viene specificato. Per ulteriori informazioni, vedere [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .</span><span class="sxs-lookup"><span data-stu-id="e798f-p113">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified. See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="e798f-171">È possibile controllare lo stato bloccato di un account utente con il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="e798f-171">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="e798f-172">Visualizzare i valori di proprietà aggiuntive per gli account</span><span class="sxs-lookup"><span data-stu-id="e798f-172">View additional property values for accounts</span></span>

<span data-ttu-id="e798f-173">Il cmdlet **Get-MsolUser** per impostazione predefinita vengono visualizzati tre proprietà degli account utente:</span><span class="sxs-lookup"><span data-stu-id="e798f-173">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="e798f-174">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="e798f-174">UserPrincipalName</span></span>
    
- <span data-ttu-id="e798f-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e798f-175">DisplayName</span></span>
    
- <span data-ttu-id="e798f-176">isLicensed</span><span class="sxs-lookup"><span data-stu-id="e798f-176">isLicensed</span></span>
    
<span data-ttu-id="e798f-p114">Se è necessario proprietà aggiuntive, ad esempio il reparto può essere utilizzato per l'utente e il paese/area geografica in cui l'utente utilizza servizi di Office 365, è possibile eseguire **Get-MsolUser** in combinazione con il cmdlet **Select-Object** per specificare l'elenco di account utente proprietà. Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="e798f-p114">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="e798f-179">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="e798f-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e798f-180">Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="e798f-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e798f-181">Visualizza solo posizione dell'account utente nome, reparto e dati di utilizzo ( **Select-Object DisplayName, reparto, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="e798f-181">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="e798f-182">Dovrebbero essere visualizzate informazioni analoghe alle seguenti:</span><span class="sxs-lookup"><span data-stu-id="e798f-182">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="e798f-p115">Il cmdlet **Select-Object** consente di scegliere le proprietà da un comando da visualizzare. Per visualizzare tutte le proprietà degli account utente, utilizzare il carattere jolly (\*) per visualizzarli tutti per un account utente specifico. Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="e798f-p115">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="e798f-p116">Per selezionare in modo più restrittivo l'elenco di account da visualizzare, è possibile utilizzare il cmdlet **Where-Object**. Ecco un comando di esempio che visualizza soltanto gli account utente con un percorso di utilizzo non specificato:</span><span class="sxs-lookup"><span data-stu-id="e798f-p116">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="e798f-188">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="e798f-188">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e798f-189">Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="e798f-189">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e798f-p117">Trovare tutti gli account utente con un percorso di utilizzo non specificata ( **Where-Object {$\_. UsageLocation - eq $Null}** ) e inviare le informazioni ottenute con il comando successivo ( **|** ). Parentesi graffe, il comando è indica a Office 365 PowerShell per trovare solo il set di account in cui gli account utente UsageLocation proprietà ( \*\* $ \_. UsageLocation\*\* ) non è specificata ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="e798f-p117">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="e798f-192">Visualizza solo posizione dell'account utente nome, reparto e dati di utilizzo ( **Select-Object DisplayName, reparto, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="e798f-192">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="e798f-193">Dovrebbero essere visualizzate informazioni analoghe alle seguenti:</span><span class="sxs-lookup"><span data-stu-id="e798f-193">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="e798f-p118">Se si utilizza la sincronizzazione delle directory per creare e gestire gli utenti di Office 365, è possibile visualizzare quale account locale è in stato piano da un utente di Office 365. Il seguente esempio si presuppone che Connetti Azure Active Directory sono stato configurato per utilizzare l'ancoraggio origine predefinita della ObjectGUID (per ulteriori informazioni sulla configurazione di un punto di ancoraggio di origine, vedere [Connetti Azure Active Directory: progettare concetti](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) e si presuppone che il modulo di Active Directory per powershell stati installati (vedere [Strumenti RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span><span class="sxs-lookup"><span data-stu-id="e798f-p118">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from. The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="see-also"></a><span data-ttu-id="e798f-196">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e798f-196">See also</span></span>

[<span data-ttu-id="e798f-197">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e798f-197">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e798f-198">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="e798f-198">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e798f-199">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="e798f-199">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

