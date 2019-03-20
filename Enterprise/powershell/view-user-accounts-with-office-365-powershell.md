---
title: Visualizzare gli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/19/2019
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
description: 'Riepilogo: visualizzare, elencare o visualizzare gli account utente in vari modi con Office 365 PowerShell.'
ms.openlocfilehash: 717a7c11f4e7f6d2e5e0c452854df7d4c419007e
ms.sourcegitcommit: 1dc7b4731cf9899c5ae867624ed142dbab0c517f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "30683703"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="903e3-103">Visualizzare gli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="903e3-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="903e3-104">**Riepilogo:** Visualizzare gli account utente in vari modi con Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="903e3-104">**Summary:** View your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="903e3-105">Anche se è possibile utilizzare l'interfaccia di amministrazione di Office 365 per visualizzare gli account per il tenant di Office 365, è possibile utilizzare anche Office 365 PowerShell e fare alcuni elementi che l'interfaccia di amministrazione di Office 365 non è in grado di eseguire.</span><span class="sxs-lookup"><span data-stu-id="903e3-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="903e3-106">Usare il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="903e3-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="903e3-107">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="903e3-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="903e3-108">Visualizzazione di tutti gli account</span><span class="sxs-lookup"><span data-stu-id="903e3-108">View all accounts</span></span>

<span data-ttu-id="903e3-109">Per visualizzare l'elenco completo degli account utente, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="903e3-109">To display the full list of user accounts, run this command:</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="903e3-110">Dovrebbero essere visualizzate informazioni analoghe alle seguenti:</span><span class="sxs-lookup"><span data-stu-id="903e3-110">You should see information similar to this:</span></span>
  
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

### <a name="view-a-specific-account"></a><span data-ttu-id="903e3-111">Visualizzazione di un account specifico</span><span class="sxs-lookup"><span data-stu-id="903e3-111">View a specific account</span></span>

<span data-ttu-id="903e3-112">Per visualizzare un account utente specifico, immettere il nome account di accesso dell'account utente, noto anche come nome dell'entità utente (UPN), rimuovere i caratteri "<" e ">" ed eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="903e3-112">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="903e3-113">Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="903e3-113">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="903e3-114">Visualizzare i valori di proprietà aggiuntivi per un account specifico</span><span class="sxs-lookup"><span data-stu-id="903e3-114">View additional property values for a specific account</span></span>

<span data-ttu-id="903e3-115">Per impostazione predefinita, il cmdlet **Get-AzureADUser** consente di visualizzare solo le proprietà ObjectID, DisplayName e userPrincipalName degli account.</span><span class="sxs-lookup"><span data-stu-id="903e3-115">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="903e3-116">Per essere più selettivi sull'elenco delle proprietà da visualizzare, è possibile utilizzare il cmdlet **Select-Object** in combinazione con il cmdlet **Get-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="903e3-116">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="903e3-117">Per combinare i due cmdlet, viene utilizzato il carattere "pipe" "|", che indica a Azure Active Directory PowerShell per Graph di prendere i risultati di un comando e inviarlo al comando successivo.</span><span class="sxs-lookup"><span data-stu-id="903e3-117">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="903e3-118">Di seguito è riportato un comando di esempio che consente di visualizzare il DisplayName, il reparto e UsageLocation per ogni account utente:</span><span class="sxs-lookup"><span data-stu-id="903e3-118">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="903e3-119">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="903e3-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="903e3-120">Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="903e3-120">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="903e3-121">Visualizzare solo il nome dell'account utente, il reparto e il percorso di utilizzo ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="903e3-121">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="903e3-122">Per visualizzare tutte le proprietà degli account utente, utilizzare il cmdlet **Select-Object** e il carattere jolly (\*) per visualizzarli tutti per un account utente specifico.</span><span class="sxs-lookup"><span data-stu-id="903e3-122">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="903e3-123">Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="903e3-123">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="903e3-124">Come un altro esempio, è possibile controllare lo stato abilitato di un account utente specifico con il seguente comando:</span><span class="sxs-lookup"><span data-stu-id="903e3-124">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="903e3-125">Visualizzare alcuni account basati su una proprietà comune</span><span class="sxs-lookup"><span data-stu-id="903e3-125">View some accounts based on a common property</span></span>

<span data-ttu-id="903e3-126">Per selezionare in modo più restrittivo l'elenco di account da visualizzare, è possibile utilizzare il cmdlet **Where-Object** insieme al cmdlet **Get-AzureADUser**.</span><span class="sxs-lookup"><span data-stu-id="903e3-126">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="903e3-127">Per combinare i due cmdlet, viene utilizzato il carattere "pipe" "|", che indica a Azure Active Directory PowerShell per Graph di prendere i risultati di un comando e inviarlo al comando successivo.</span><span class="sxs-lookup"><span data-stu-id="903e3-127">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="903e3-128">Ecco un comando di esempio che visualizza soltanto gli account utente con un percorso di utilizzo non specificato:</span><span class="sxs-lookup"><span data-stu-id="903e3-128">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="903e3-129">Questo comando indica a Azure Active Directory PowerShell per Graph di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="903e3-129">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="903e3-130">Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="903e3-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="903e3-131">Individuare tutti gli account utente che dispongono di una posizione di utilizzo non specificata ( **Where-Object {\_$. UsageLocation-eq $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="903e3-131">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="903e3-132">All'interno delle parentesi graffe, il comando indica a Office 365 PowerShell di trovare solo il set di account in cui la proprietà dell'account utente di UsageLocation ( \*\* $ \_. UsageLocation\*\* ) non è specificato ( **-eq $null** ).</span><span class="sxs-lookup"><span data-stu-id="903e3-132">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="903e3-133">La proprietà **UsageLocation** è solo una delle tante associate a un account utente.</span><span class="sxs-lookup"><span data-stu-id="903e3-133">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="903e3-134">Per visualizzare tutte le proprietà degli account utente, utilizzare il cmdlet **Select-Object** e il carattere jolly (\*) per visualizzarli tutti per un account utente specifico.</span><span class="sxs-lookup"><span data-stu-id="903e3-134">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="903e3-135">Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="903e3-135">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="903e3-p106">In questo elenco, **City** è il nome di una proprietà dell'account utente. Questo significa che è possibile usare il comando seguente per elencare tutti gli account degli utenti che vivono a Londra:</span><span class="sxs-lookup"><span data-stu-id="903e3-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="903e3-138">La sintassi del cmdlet **Where-Object** mostrato in questi esempi è **Where-Object {$\_.**</span><span class="sxs-lookup"><span data-stu-id="903e3-138">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="903e3-139">[nome della proprietà dell'account utente] [operatore di confronto] valore **}**. > [operatore di confronto] è **-EQ** per Equals, **-ne** per non uguale a, **-lt** per meno di, **-gT** per maggiore di e altri.</span><span class="sxs-lookup"><span data-stu-id="903e3-139">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="903e3-140">[valore] è in genere una stringa (una sequenza di lettere, numeri e altri caratteri), un valore numerico oppure **$null** per Unspecified> vedere [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) per ulteriori informazioni.</span><span class="sxs-lookup"><span data-stu-id="903e3-140">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="903e3-141">Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="903e3-141">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="903e3-142">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="903e3-142">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="903e3-143">Visualizzazione di tutti gli account</span><span class="sxs-lookup"><span data-stu-id="903e3-143">View all accounts</span></span>

<span data-ttu-id="903e3-144">Per visualizzare l'elenco completo degli account utente, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="903e3-144">To display the full list of user accounts, run this command:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="903e3-145">Dovrebbero essere visualizzate informazioni analoghe alle seguenti:</span><span class="sxs-lookup"><span data-stu-id="903e3-145">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="903e3-146">Il cmdlet **Get-MsolUser** dispone inoltre di un set di parametri per filtrare il gruppo di account utente visualizzato.</span><span class="sxs-lookup"><span data-stu-id="903e3-146">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="903e3-147">Ad esempio, per l'elenco degli utenti senza licenza (gli utenti che sono stati aggiunti a Office 365 ma non sono stati ancora autorizzati a utilizzare uno qualsiasi dei servizi), eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="903e3-147">For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="903e3-148">Dovrebbero essere visualizzate informazioni analoghe alle seguenti:</span><span class="sxs-lookup"><span data-stu-id="903e3-148">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="903e3-149">Per ulteriori informazioni sui parametri aggiuntivi per filtrare la visualizzazione del set di account utente visualizzato, vedere [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="903e3-149">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="903e3-150">Visualizzazione di un account specifico</span><span class="sxs-lookup"><span data-stu-id="903e3-150">View a specific account</span></span>

<span data-ttu-id="903e3-151">Per visualizzare un account utente specifico, inserire il nome di accesso dell'account utente dell'account utente, noto anche come nome dell'entità utente (UPN), rimuovere i caratteri "<" e ">" ed eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="903e3-151">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="903e3-152">Visualizzare alcuni account basati su una proprietà comune</span><span class="sxs-lookup"><span data-stu-id="903e3-152">View some accounts based on a common property</span></span>

<span data-ttu-id="903e3-153">Per selezionare in modo più restrittivo l'elenco di account da visualizzare, è possibile utilizzare il cmdlet **Where-Object** insieme al cmdlet **Get-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="903e3-153">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="903e3-154">Per combinare i due cmdlet, viene utilizzato il carattere "pipe" "|", che indica a Office 365 PowerShell di prendere i risultati di un comando e inviarlo al comando successivo.</span><span class="sxs-lookup"><span data-stu-id="903e3-154">To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="903e3-155">Ecco un comando di esempio che visualizza soltanto gli account utente con un percorso di utilizzo non specificato:</span><span class="sxs-lookup"><span data-stu-id="903e3-155">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="903e3-156">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="903e3-156">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="903e3-157">Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="903e3-157">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="903e3-158">Individuare tutti gli account utente che dispongono di una posizione di utilizzo non specificata ( **Where-Object {\_$. UsageLocation-eq $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="903e3-158">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="903e3-159">All'interno delle parentesi graffe, il comando indica a Office 365 PowerShell di trovare solo il set di account in cui la proprietà dell'account utente di UsageLocation ( \*\* $ \_. UsageLocation\*\* ) non è specificato ( **-eq $null** ).</span><span class="sxs-lookup"><span data-stu-id="903e3-159">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="903e3-160">Dovrebbero essere visualizzate informazioni analoghe alle seguenti:</span><span class="sxs-lookup"><span data-stu-id="903e3-160">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="903e3-161">La proprietà **UsageLocation** è solo una delle tante associate a un account utente.</span><span class="sxs-lookup"><span data-stu-id="903e3-161">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="903e3-162">Per visualizzare tutte le proprietà degli account utente, utilizzare il cmdlet **Select-Object** e il carattere jolly (\*) per visualizzarli tutti per un account utente specifico.</span><span class="sxs-lookup"><span data-stu-id="903e3-162">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="903e3-163">Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="903e3-163">Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="903e3-p112">In questo elenco, **City** è il nome di una proprietà dell'account utente. Questo significa che è possibile usare il comando seguente per elencare tutti gli account degli utenti che vivono a Londra:</span><span class="sxs-lookup"><span data-stu-id="903e3-p112">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="903e3-166">La sintassi del cmdlet **Where-Object** mostrato in questi esempi è **Where-Object {$\_.**</span><span class="sxs-lookup"><span data-stu-id="903e3-166">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="903e3-167">[nome della proprietà dell'account utente] [operatore di confronto] valore **}**.</span><span class="sxs-lookup"><span data-stu-id="903e3-167">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="903e3-168">[operatore di confronto] è **-EQ** per Equals, **-ne** per non uguale a, **-lt** per meno di, **-gt** per maggiore di e altri.</span><span class="sxs-lookup"><span data-stu-id="903e3-168">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="903e3-169">[valore] è in genere una stringa, ovvero una sequenza di lettere, numeri e altri caratteri, un valore numerico o **$null** per Unspecified.</span><span class="sxs-lookup"><span data-stu-id="903e3-169">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="903e3-170">Per ulteriori informazioni, vedere [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .</span><span class="sxs-lookup"><span data-stu-id="903e3-170">See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="903e3-171">È possibile controllare lo stato bloccato di un account utente con il seguente comando:</span><span class="sxs-lookup"><span data-stu-id="903e3-171">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="903e3-172">Visualizzare i valori di proprietà aggiuntivi per gli account</span><span class="sxs-lookup"><span data-stu-id="903e3-172">View additional property values for accounts</span></span>

<span data-ttu-id="903e3-173">Il cmdlet **Get-MsolUser** per impostazione predefinita visualizza tre proprietà degli account utente:</span><span class="sxs-lookup"><span data-stu-id="903e3-173">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="903e3-174">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="903e3-174">UserPrincipalName</span></span>
    
- <span data-ttu-id="903e3-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="903e3-175">DisplayName</span></span>
    
- <span data-ttu-id="903e3-176">isLicensed</span><span class="sxs-lookup"><span data-stu-id="903e3-176">isLicensed</span></span>
    
<span data-ttu-id="903e3-177">Se sono necessarie ulteriori proprietà, ad esempio il reparto utilizzato dall'utente e il paese/area geografica in cui l'utente utilizza i servizi di Office 365, è possibile eseguire **Get-MsolUser** in combinazione con il cmdlet **Select-Object** per specificare l'elenco di account utente. Proprietà.</span><span class="sxs-lookup"><span data-stu-id="903e3-177">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="903e3-178">Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="903e3-178">Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="903e3-179">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="903e3-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="903e3-180">Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="903e3-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="903e3-181">Visualizzare solo il nome dell'account utente, il reparto e il percorso di utilizzo ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="903e3-181">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="903e3-182">Dovrebbero essere visualizzate informazioni analoghe alle seguenti:</span><span class="sxs-lookup"><span data-stu-id="903e3-182">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="903e3-183">Il cmdlet **Select-Object** consente di scegliere le proprietà che si desidera visualizzare.</span><span class="sxs-lookup"><span data-stu-id="903e3-183">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="903e3-184">Per visualizzare tutte le proprietà degli account utente, utilizzare il carattere jolly (\*) per visualizzarle tutte per un account utente specifico.</span><span class="sxs-lookup"><span data-stu-id="903e3-184">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="903e3-185">Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="903e3-185">Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="903e3-p116">Per selezionare in modo più restrittivo l'elenco di account da visualizzare, è possibile utilizzare il cmdlet **Where-Object**. Ecco un comando di esempio che visualizza soltanto gli account utente con un percorso di utilizzo non specificato:</span><span class="sxs-lookup"><span data-stu-id="903e3-p116">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="903e3-188">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="903e3-188">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="903e3-189">Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="903e3-189">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="903e3-190">Individuare tutti gli account utente che dispongono di una posizione di utilizzo non specificata ( **Where-Object {\_$. UsageLocation-eq $Null}** ) e inviare le informazioni risultanti al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="903e3-190">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="903e3-191">All'interno delle parentesi graffe, il comando indica a Office 365 PowerShell di trovare solo il set di account in cui si trova la proprietà dell'account utente di UsageLocation ( \*\* $ \_. UsageLocation\*\* ) non è specificato ( **-eq $null** ).</span><span class="sxs-lookup"><span data-stu-id="903e3-191">Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="903e3-192">Visualizzare solo il nome dell'account utente, il reparto e il percorso di utilizzo ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="903e3-192">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="903e3-193">Dovrebbero essere visualizzate informazioni analoghe alle seguenti:</span><span class="sxs-lookup"><span data-stu-id="903e3-193">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="903e3-194">Se si utilizza la sincronizzazione della directory per creare e gestire gli utenti di Office 365, è possibile visualizzare l'account locale da cui è stato proiettato un utente di Office 365.</span><span class="sxs-lookup"><span data-stu-id="903e3-194">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from.</span></span> <span data-ttu-id="903e3-195">Di seguito si presuppone che Azure AD Connect sia stato configurato per l'utilizzo dell'ancoraggio di origine predefinito di ObjectGUID (per ulteriori informazioni sulla configurazione di un ancoraggio di origine, vedere [Azure ad Connect: Design Concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) e presuppone che il modulo di Active Directory per PowerShell sia stati installati (vedere [strumenti di amministrazione remota](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span><span class="sxs-lookup"><span data-stu-id="903e3-195">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

    
## <a name="see-also"></a><span data-ttu-id="903e3-196">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="903e3-196">See also</span></span>

[<span data-ttu-id="903e3-197">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="903e3-197">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="903e3-198">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="903e3-198">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="903e3-199">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="903e3-199">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

