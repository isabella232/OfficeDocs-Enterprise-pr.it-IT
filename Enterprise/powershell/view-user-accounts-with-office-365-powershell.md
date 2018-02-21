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
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="f3dd9-103">Visualizzare gli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3dd9-103">View user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="f3dd9-104">**Riepilogo:** Consente di visualizzare, elencare o visualizzare gli account utente in vari modi con Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3dd9-104">**Summary:** View, list, or display your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="f3dd9-105">Sebbene sia possibile utilizzare l'interfaccia di amministrazione di Office 365 per visualizzare gli account per il tenant di Office 365, è possibile utilizzare Office 365 PowerShell ed effettuare alcune operazioni che non è l'interfaccia di amministrazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="f3dd9-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="f3dd9-106">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="f3dd9-106">Before you begin</span></span>

<span data-ttu-id="f3dd9-p101">Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="display-office-365-user-account-information"></a><span data-ttu-id="f3dd9-109">Visualizzare informazioni sull'account utente di Office 365</span><span class="sxs-lookup"><span data-stu-id="f3dd9-109">Display Office 365 user account information</span></span>

<span data-ttu-id="f3dd9-110">Per visualizzare un elenco completo degli account utente, eseguire questo comando nel prompt dei comandi di Office 365 PowerShell oppure PowerShell Integrated Script Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="f3dd9-110">To display the full list of user accounts, run this command in your Office 365 PowerShell command prompt or the PowerShell Integrated Script Environment (ISE).</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="f3dd9-111">Dovrebbero essere visualizzate informazioni analoghe alle seguenti:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-111">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="f3dd9-p102">Il cmdlet **Get-MsolUser** ha inoltre un set di parametri per filtrare il set di account utente visualizzato. Ad esempio, per l'elenco di utenti senza licenza (gli utenti che sono stati aggiunti a Office 365, ma non sono ancora stati concessi in licenza per utilizzare uno qualsiasi dei servizi), eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p102">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="f3dd9-114">Dovrebbero essere visualizzate informazioni analoghe alle seguenti:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-114">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="f3dd9-115">Per ulteriori informazioni su ulteriori parametri per filtrare la visualizzazione dei set di account utente visualizzata, vedere [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) .</span><span class="sxs-lookup"><span data-stu-id="f3dd9-115">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) .</span></span>
  
<span data-ttu-id="f3dd9-p103">Per essere più selettiva relative all'elenco di account da visualizzare, è possibile utilizzare il cmdlet **Where-Object** in combinazione con il cmdlet **Get-MsolUser** . Per combinare i due cmdlet, si utilizza il carattere "pipe" "|", che indica a Office 365 PowerShell i risultati di un comando e inviarlo al comando successivo. Ecco un comando di esempio che consente di visualizzare solo gli account utente con un percorso di utilizzo non specificata:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p103">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="f3dd9-119">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="f3dd9-120">Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="f3dd9-120">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f3dd9-p104">Trovare tutti gli account utente con un percorso di utilizzo non specificata ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Parentesi graffe, il comando consente di indicare a Office 365 PowerShell per trovare solo il set di account in cui gli account utente UsageLocation proprietà ( ** $ \_. UsageLocation** ) non è specificata ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p104">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="f3dd9-123">Dovrebbero essere visualizzate informazioni analoghe alle seguenti:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-123">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="f3dd9-p105">La proprietà **UsageLocation** è solo una delle numerose proprietà associate a un account utente. Per visualizzare tutte le proprietà degli account utente, utilizzare il cmdlet **Select-Object** e il carattere jolly (\*) per visualizzare tutte per un account utente specifico. Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p105">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="f3dd9-p106">Dall'elenco, ad esempio, **Città** è il nome di una proprietà di account utente. Ciò significa che è possibile utilizzare il comando seguente per elencare tutti gli account utente per gli utenti che risiedono nella London:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="f3dd9-p107">La sintassi per il cmdlet **Where-Object** illustrato negli esempi seguenti è **Where-Object {$\_.** [nome proprietà dell'account utente] [operatore di confronto] [valore] **}**. > [operatore di confronto] è **-eq** per uguale a, **-ne** per non equivale a, **-lt** minore di **-gt** per maggiore e ad altri > [valore] in genere è una stringa (una sequenza di lettere, numeri e altri caratteri), un valore numerico o **$Null** per non viene specificato > Per ulteriori informazioni, vedere [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p107">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others>  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="f3dd9-131">È possibile controllare lo stato bloccato di un account utente con il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-131">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a><span data-ttu-id="f3dd9-132">Selezionare le proprietà dell'account utente da visualizzare</span><span class="sxs-lookup"><span data-stu-id="f3dd9-132">Select the user account properties to display</span></span>

<span data-ttu-id="f3dd9-133">Il cmdlet [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) per impostazione predefinita vengono visualizzati tre proprietà degli account utente:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-133">The [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="f3dd9-134">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="f3dd9-134">UserPrincipalName</span></span>
    
- <span data-ttu-id="f3dd9-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f3dd9-135">DisplayName</span></span>
    
- <span data-ttu-id="f3dd9-136">isLicensed</span><span class="sxs-lookup"><span data-stu-id="f3dd9-136">isLicensed</span></span>
    
<span data-ttu-id="f3dd9-p108">Se è necessario proprietà aggiuntive, ad esempio il reparto può essere utilizzato per l'utente e il paese/area geografica in cui l'utente utilizza servizi di Office 365, è possibile eseguire **Get-MsolUser** in combinazione con il cmdlet **Select-Object** per specificare l'elenco di account utente proprietà. Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p108">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="f3dd9-139">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-139">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="f3dd9-140">Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="f3dd9-140">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f3dd9-141">Visualizza solo posizione dell'account utente nome, reparto e dati di utilizzo ( **Select-Object DisplayName, reparto, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="f3dd9-141">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="f3dd9-142">Dovrebbero essere visualizzate informazioni analoghe alle seguenti:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-142">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="f3dd9-p109">Il cmdlet **Select-Object** consente di scegliere le proprietà da un comando da visualizzare. Per visualizzare tutte le proprietà degli account utente, utilizzare il carattere jolly (\*) per visualizzarli tutti per un account utente specifico. Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p109">The **Select-Object** cmdlet allows you to pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="f3dd9-p110">Per essere più selettiva relative all'elenco di account da visualizzare, è possibile anche utilizzare il cmdlet **Where-Object** . Ecco un comando di esempio che consente di visualizzare solo gli account utente con un percorso di utilizzo non specificata:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p110">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="f3dd9-148">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="f3dd9-149">Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="f3dd9-149">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f3dd9-p111">Trovare tutti gli account utente con un percorso di utilizzo non specificata ( **Where-Object {$\_. UsageLocation - eq $Null}** ) e inviare le informazioni ottenute con il comando successivo ( **|** ). Parentesi graffe, il comando è indica a Office 365 PowerShell per trovare solo il set di account in cui gli account utente UsageLocation proprietà ( ** $ \_. UsageLocation** ) non è specificata ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p111">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="f3dd9-152">Visualizza solo posizione dell'account utente nome, reparto e dati di utilizzo ( **Select-Object DisplayName, reparto, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="f3dd9-152">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="f3dd9-153">Dovrebbero essere visualizzate informazioni analoghe alle seguenti:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-153">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a><span data-ttu-id="f3dd9-154">Utilizzare il modulo Azure Active Directory V2 PowerShell per visualizzare gli account utente</span><span class="sxs-lookup"><span data-stu-id="f3dd9-154">Use the Azure Active Directory V2 PowerShell module to display user accounts</span></span>

<span data-ttu-id="f3dd9-p112">Per visualizzare le proprietà degli account utente con il modulo di Azure Active Directory V2 PowerShell, utilizzare il cmdlet [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) . Tuttavia, è innanzitutto necessario connettersi alla sottoscrizione. Per ulteriori informazioni, vedere[Connect con il modulo di Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p112">To display properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) cmdlet. But first, you must connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="display-office-365-user-account-information"></a><span data-ttu-id="f3dd9-158">Visualizzare informazioni sull'account utente di Office 365</span><span class="sxs-lookup"><span data-stu-id="f3dd9-158">Display Office 365 user account information</span></span>

<span data-ttu-id="f3dd9-159">Per visualizzare un elenco completo degli account utente, eseguire questo comando nel prompt dei comandi di Office 365 PowerShell oppure PowerShell Integrated Script Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="f3dd9-159">To display the full list of user accounts, run this command in your Office 365 PowerShell command prompt or the PowerShell Integrated Script Environment (ISE).</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="f3dd9-160">Il cmdlet **Get-AzureADUser** per impostazione predefinita vengono visualizzati tre proprietà degli account utente:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-160">The **Get-AzureADUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="f3dd9-161">ObjectID</span><span class="sxs-lookup"><span data-stu-id="f3dd9-161">ObjectID</span></span>
    
- <span data-ttu-id="f3dd9-162">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f3dd9-162">DisplayName</span></span>
    
- <span data-ttu-id="f3dd9-163">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="f3dd9-163">UserPrincipalName</span></span>
    
<span data-ttu-id="f3dd9-p113">Per essere più selettiva relative all'elenco di account da visualizzare, è possibile utilizzare il cmdlet **Where-Object** in combinazione con il cmdlet **Get-AzureADUser** . Per combinare i due cmdlet, si utilizza il carattere "pipe" "|", che indica a Office 365 PowerShell i risultati di un comando e inviarlo al comando successivo. Ecco un comando di esempio che consente di visualizzare solo gli account utente con un percorso di utilizzo non specificata:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p113">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="f3dd9-167">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-167">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="f3dd9-168">Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="f3dd9-168">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f3dd9-p114">Trovare tutti gli account utente con un percorso di utilizzo non specificata ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Parentesi graffe, il comando consente di indicare a Office 365 PowerShell per trovare solo il set di account in cui gli account utente UsageLocation proprietà ( ** $ \_. UsageLocation** ) non è specificata ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p114">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="f3dd9-p115">La proprietà **UsageLocation** è solo una delle numerose proprietà associate a un account utente. Per visualizzare tutte le proprietà degli account utente, utilizzare il cmdlet **Select-Object** e il carattere jolly (\*) per visualizzare tutte per un account utente specifico, una pagina alla volta ( **più** ). Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p115">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account, one page at a time ( **More** ). Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

<span data-ttu-id="f3dd9-p116">Ad esempio, **la località** è il nome di una proprietà di account utente. Ciò significa che è possibile utilizzare il comando seguente per elencare tutti gli account utente per gli utenti che risiedono nella London:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p116">For example, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="f3dd9-p117">La sintassi per il cmdlet **Where-Object** illustrato negli esempi seguenti è **Where-Object {$\_.** [nome proprietà dell'account utente] [operatore di confronto] [valore] **}**. > [operatore di confronto] è **-eq** per uguale a, **-ne** per non equivale a, **-lt** minore di **-gt** per maggiore e ad altri > [valore] in genere è una stringa (una sequenza di lettere, numeri e altri caratteri), un valore numerico o **$Null** per non viene specificato > Per ulteriori informazioni, vedere[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p117">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others>  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
### <a name="select-the-user-account-properties-to-display"></a><span data-ttu-id="f3dd9-178">Selezionare le proprietà dell'account utente da visualizzare</span><span class="sxs-lookup"><span data-stu-id="f3dd9-178">Select the user account properties to display</span></span>

<span data-ttu-id="f3dd9-p118">Il cmdlet **Get-AzureADUser** per impostazione predefinita vengono visualizzate le proprietà ObjectID, DisplayName e UserPrincipalName degli account utente. Se è necessario proprietà aggiuntive, ad esempio il reparto può essere utilizzato per l'utente e il paese/area geografica in cui l'utente utilizza servizi di Office 365, è possibile eseguire **Get-AzureADUser** in combinazione con il cmdlet **Select-Object** per specificare l'elenco di utenti Proprietà account. Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p118">The **Get-AzureADUser** cmdlet by default displays the ObjectID, DisplayName, and UserPrincipalName properties of user accounts. If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-AzureADUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="f3dd9-182">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-182">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="f3dd9-183">Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="f3dd9-183">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f3dd9-184">Visualizza solo posizione dell'account utente nome, reparto e dati di utilizzo ( **Select-Object DisplayName, reparto, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="f3dd9-184">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="f3dd9-p119">Per essere più selettiva relative all'elenco di account da visualizzare, è possibile anche utilizzare il cmdlet **Where-Object** . Ecco un comando di esempio che consente di visualizzare solo gli account utente con un percorso di utilizzo non specificata:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p119">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="f3dd9-187">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="f3dd9-187">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="f3dd9-188">Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="f3dd9-188">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f3dd9-p120">Trovare tutti gli account utente con un percorso di utilizzo non specificata ( **Where-Object {$\_. UsageLocation - eq $Null}** ) e inviare le informazioni ottenute con il comando successivo ( **|** ). Parentesi graffe, il comando è indica a Office 365 PowerShell per trovare solo il set di account in cui gli account utente UsageLocation proprietà ( ** $ \_. UsageLocation** ) non è specificata ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="f3dd9-p120">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="f3dd9-191">Visualizza solo posizione dell'account utente nome, reparto e dati di utilizzo ( **Select-Object DisplayName, reparto, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="f3dd9-191">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
## <a name="new-to-office-365"></a><span data-ttu-id="f3dd9-192">Nuovo utente di Office 365?</span><span class="sxs-lookup"><span data-stu-id="f3dd9-192">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
  
## <a name="see-also"></a><span data-ttu-id="f3dd9-193">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f3dd9-193">See also</span></span>

#### 

[<span data-ttu-id="f3dd9-194">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3dd9-194">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="f3dd9-195">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="f3dd9-195">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f3dd9-196">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="f3dd9-196">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

