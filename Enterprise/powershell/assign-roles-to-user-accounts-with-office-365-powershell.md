---
title: Assegnare i ruoli agli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/31/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 'Sintesi: usare Office 365 PowerShell per assegnare ruoli agli account utente.'
ms.openlocfilehash: 702c7358ccca9bb36bd106d742b5c454283ee8b4
ms.sourcegitcommit: d0c870c7a487eda48b11f649b30e4818fd5608aa
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2019
ms.locfileid: "29690437"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="eb2b6-103">Assegnare i ruoli agli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb2b6-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="eb2b6-104">Per assegnare ruoli agli account utente in modo semplice e rapido, è possibile usare Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell by identifying the user account's display name and the role name.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="eb2b6-105">Usare il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="eb2b6-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="eb2b6-106">In primo luogo, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) con un account amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="eb2b6-p101">Determinare quindi il nome di accesso dell'account utente da aggiungere a un ruolo (ad esempio mario@contoso.com). Questo nome di accesso è noto anche come nome dell'entità utente (UPN).</span><span class="sxs-lookup"><span data-stu-id="eb2b6-p101">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com). This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="eb2b6-p102">Determinare il nome del ruolo. Usare questo comando per elencare i ruoli che è possibile assegnare con PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-p102">Next, determine the name of the role. Use this command to list the roles that you can assign with PowerShell.</span></span>

````
Get-AzureADDirectoryRole
````

<span data-ttu-id="eb2b6-111">Immettere quindi i nomi di accesso e di ruolo ed eseguire questi comandi.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-111">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```
$userName="<sign-in name of the account>"
$roleName="<role name>"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="eb2b6-112">Ecco un esempio di un set di comandi completato:</span><span class="sxs-lookup"><span data-stu-id="eb2b6-112">Here is an example of a completed command set:</span></span>
  
```
$userName="belindan@contoso.com"
$roleName="Lync Service Administrator"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="eb2b6-113">Per visualizzare l'elenco dei nomi utente per un ruolo specifico, usare questi comandi.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-113">To display the list of user names for a specific role, use these commands.</span></span>

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="eb2b6-114">Usare il Modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb2b6-114">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="eb2b6-115">In primo luogo, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) con un account amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-115">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="eb2b6-116">Per una singola modifica del ruolo</span><span class="sxs-lookup"><span data-stu-id="eb2b6-116">For a single role change</span></span>

<span data-ttu-id="eb2b6-117">Determinare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="eb2b6-117">Determine the following:</span></span>
  
- <span data-ttu-id="eb2b6-118">L'account utente da configurare.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-118">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="eb2b6-p103">Per specificare l'account utente, è necessario determinare il nome visualizzato. Per ottenere un elenco completo di account, utilizzare questo comando:</span><span class="sxs-lookup"><span data-stu-id="eb2b6-p103">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="eb2b6-p104">Questo comando elenca il nome visualizzato degli account utente, ordinati per nome visualizzato, una schermata alla volta. È possibile filtrare l'elenco in un set più piccolo utilizzando il cmdlet **Where**. Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="eb2b6-p104">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="eb2b6-124">Questo comando elenca solo gli account utente per cui il nome visualizzato inizia con "John".</span><span class="sxs-lookup"><span data-stu-id="eb2b6-124">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="eb2b6-125">Il ruolo da assegnare.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-125">The role you want to assign.</span></span>
    
    <span data-ttu-id="eb2b6-126">Per visualizzare l'elenco dei ruoli disponibili che è possibile assegnare agli account utente, usare il comando:</span><span class="sxs-lookup"><span data-stu-id="eb2b6-126">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="eb2b6-127">Dopo aver determinato il nome visualizzato dell'account e il nome del ruolo, è possibile utilizzare questi comandi per assegnare il ruolo all'account:</span><span class="sxs-lookup"><span data-stu-id="eb2b6-127">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="eb2b6-p105">Copiare i comandi e incollarli nel blocco note. Per le variabili **$dispName** e **$roleName**, sostituire il testo della descrizione con i rispettivi valori, rimuovere i caratteri \< e > e lasciare le virgolette. Copiare le righe modificate e incollarle nel modulo di Windows Azure Active Directory modulo affinché Windows PowerShell le esegua. È anche possibile utilizzare Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="eb2b6-p105">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="eb2b6-132">Segue un esempio di un set di comandi completati:</span><span class="sxs-lookup"><span data-stu-id="eb2b6-132">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="eb2b6-133">Per più modifiche di ruoli</span><span class="sxs-lookup"><span data-stu-id="eb2b6-133">For multiple role changes</span></span>

<span data-ttu-id="eb2b6-134">Determinare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="eb2b6-134">Determine the following:</span></span>
  
- <span data-ttu-id="eb2b6-135">Quali account utente configurare.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-135">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="eb2b6-p106">Per specificare l'account utente, è necessario determinare il nome visualizzato. Per ottenere un elenco di account, utilizzare questo comando:</span><span class="sxs-lookup"><span data-stu-id="eb2b6-p106">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="eb2b6-p107">Questo comando elenca il nome visualizzato di tutti gli account utente, ordinati per nome visualizzato, una schermata alla volta. È possibile filtrare l'elenco in un set più piccolo utilizzando il cmdlet **Where**. Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="eb2b6-p107">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="eb2b6-141">Questo comando elenca solo gli account utente per cui il nome visualizzato inizia con "John".</span><span class="sxs-lookup"><span data-stu-id="eb2b6-141">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="eb2b6-142">Ruoli che si desidera assegnare a ogni account utente.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-142">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="eb2b6-143">Per visualizzare l'elenco dei ruoli disponibili che è possibile assegnare agli account utente, usare questo comando:</span><span class="sxs-lookup"><span data-stu-id="eb2b6-143">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="eb2b6-p108">Creare quindi un file CSV che include i campi Nome visualizzato e Nome del ruolo. Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="eb2b6-p108">Next, create a comma-separated value (CSV) text file that contains the DisplayName and role Name fields. Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="eb2b6-146">Immettere infine il percorso del file CSV ed eseguire i comandi risultanti al prompt dei comandi di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb2b6-146">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="eb2b6-147">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="eb2b6-147">See also</span></span>

- [<span data-ttu-id="eb2b6-148">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb2b6-148">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="eb2b6-149">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="eb2b6-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="eb2b6-150">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="eb2b6-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
