---
title: Assegnare i ruoli agli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/30/2019
audience: Admin
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
ms.openlocfilehash: 29c23e88d9b7bc2fc0030d467336e38ed413a4ab
ms.sourcegitcommit: 21901808f112dd1d8d01617c4be37911efc379f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2019
ms.locfileid: "38707033"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="a0e78-103">Assegnare i ruoli agli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0e78-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="a0e78-104">Per assegnare ruoli agli account utente in modo semplice e rapido, è possibile usare Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a0e78-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="a0e78-105">Usare il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="a0e78-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="a0e78-106">In primo luogo, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) con un account amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="a0e78-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="a0e78-p101">Determinare quindi il nome di accesso dell'account utente da aggiungere a un ruolo (ad esempio mario@contoso.com). Questo nome di accesso è noto anche come nome dell'entità utente (UPN).</span><span class="sxs-lookup"><span data-stu-id="a0e78-p101">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com). This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="a0e78-109">Successivamente, determinare il nome del ruolo.</span><span class="sxs-lookup"><span data-stu-id="a0e78-109">Next, determine the name of the role.</span></span> <span data-ttu-id="a0e78-110">Usare questo [elenco di autorizzazioni del ruolo di amministratore in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span><span class="sxs-lookup"><span data-stu-id="a0e78-110">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="a0e78-111">Prestare attenzione alle note in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="a0e78-111">Pay attention to the notes in this article.</span></span> <span data-ttu-id="a0e78-112">Alcuni nomi di ruoli sono diversi per Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a0e78-112">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="a0e78-113">Ad esempio, il ruolo "Amministratore di SharePoint" nell'interfaccia di amministrazione di Microsoft 365 è denominato "Amministratore del servizio SharePoint" in Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a0e78-113">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="a0e78-114">Immettere quindi i nomi di accesso e di ruolo ed eseguire questi comandi.</span><span class="sxs-lookup"><span data-stu-id="a0e78-114">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```powershell
$userName="<sign-in name of the account>"
$roleName="<role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="a0e78-115">Ecco un esempio di un set di comandi completato:</span><span class="sxs-lookup"><span data-stu-id="a0e78-115">Here is an example of a completed command set:</span></span>
  
```powershell
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="a0e78-116">Per visualizzare l'elenco dei nomi utente per un ruolo specifico, usare questi comandi.</span><span class="sxs-lookup"><span data-stu-id="a0e78-116">To display the list of user names for a specific role, use these commands.</span></span>

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="a0e78-117">Usare il Modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0e78-117">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="a0e78-118">In primo luogo, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) con un account amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="a0e78-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="a0e78-119">Per una singola modifica del ruolo</span><span class="sxs-lookup"><span data-stu-id="a0e78-119">For a single role change</span></span>

<span data-ttu-id="a0e78-120">La modalità più comune di un account utente specifico è il nome visualizzato o il nome di posta elettronica, noto anche come nome dell'entità utente (UPN) del nome di accesso.</span><span class="sxs-lookup"><span data-stu-id="a0e78-120">The most common ways of specific user account is with its display name or its email name, also known its sign-in name user principal name (UPN).</span></span>

#### <a name="display-names-of-user-accounts"></a><span data-ttu-id="a0e78-121">Visualizzazione dei nomi degli account utente</span><span class="sxs-lookup"><span data-stu-id="a0e78-121">Display names of user accounts</span></span>

<span data-ttu-id="a0e78-122">Se si è abituati a utilizzare i nomi visualizzati degli account utente, determinare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="a0e78-122">If you are used to working with the display names of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="a0e78-123">L'account utente da configurare.</span><span class="sxs-lookup"><span data-stu-id="a0e78-123">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="a0e78-p104">Per specificare l'account utente, è necessario determinare il nome visualizzato. Per ottenere un elenco completo di account, utilizzare questo comando:</span><span class="sxs-lookup"><span data-stu-id="a0e78-p104">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="a0e78-p105">Questo comando elenca il nome visualizzato degli account utente, ordinati per nome visualizzato, una schermata alla volta. È possibile filtrare l'elenco in un set più piccolo utilizzando il cmdlet **Where**. Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="a0e78-p105">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="a0e78-129">Questo comando elenca solo gli account utente per cui il nome visualizzato inizia con "John".</span><span class="sxs-lookup"><span data-stu-id="a0e78-129">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="a0e78-130">Il ruolo da assegnare.</span><span class="sxs-lookup"><span data-stu-id="a0e78-130">The role you want to assign.</span></span>
    
    <span data-ttu-id="a0e78-131">Per visualizzare l'elenco dei ruoli disponibili che è possibile assegnare agli account utente, usare il comando:</span><span class="sxs-lookup"><span data-stu-id="a0e78-131">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="a0e78-132">Dopo aver determinato il nome visualizzato dell'account e il nome del ruolo, è possibile utilizzare questi comandi per assegnare il ruolo all'account:</span><span class="sxs-lookup"><span data-stu-id="a0e78-132">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="a0e78-p106">Copiare i comandi e incollarli nel blocco note. Per le variabili **$dispName** e **$roleName**, sostituire il testo della descrizione con i rispettivi valori, rimuovere i caratteri \< e > e lasciare le virgolette. Copiare le righe modificate e incollarle nel modulo di Windows Azure Active Directory modulo affinché Windows PowerShell le esegua. È anche possibile utilizzare Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="a0e78-p106">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="a0e78-137">Segue un esempio di un set di comandi completati:</span><span class="sxs-lookup"><span data-stu-id="a0e78-137">Here is an example of a completed command set:</span></span>
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a><span data-ttu-id="a0e78-138">Nomi di accesso degli account utente</span><span class="sxs-lookup"><span data-stu-id="a0e78-138">Sign-in names of user accounts</span></span>

<span data-ttu-id="a0e78-139">Se si è abituati a utilizzare i nomi di accesso o gli account utente di UPN, determinare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="a0e78-139">If you are used to working with the sign-in names or UPNs of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="a0e78-140">UPN dell'account utente.</span><span class="sxs-lookup"><span data-stu-id="a0e78-140">The user account's UPN.</span></span>
    
    <span data-ttu-id="a0e78-141">Se non si conosce già l'UPN, utilizzare il seguente comando:</span><span class="sxs-lookup"><span data-stu-id="a0e78-141">If you don't already know the UPN, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="a0e78-142">Questo comando consente di elencare l'UPN degli account utente, ordinati in base all'UPN, una schermata alla volta.</span><span class="sxs-lookup"><span data-stu-id="a0e78-142">This command lists the UPN of your user accounts, sorted by the UPN, one screen at a time.</span></span> <span data-ttu-id="a0e78-143">È possibile filtrare l'elenco in un set più piccolo utilizzando il cmdlet **Where**.</span><span class="sxs-lookup"><span data-stu-id="a0e78-143">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="a0e78-144">Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="a0e78-144">Here is an example:</span></span>
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="a0e78-145">Questo comando elenca solo gli account utente per cui il nome visualizzato inizia con "John".</span><span class="sxs-lookup"><span data-stu-id="a0e78-145">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="a0e78-146">Il ruolo da assegnare.</span><span class="sxs-lookup"><span data-stu-id="a0e78-146">The role you want to assign.</span></span>
    
    <span data-ttu-id="a0e78-147">Per visualizzare l'elenco dei ruoli disponibili che è possibile assegnare agli account utente, usare il comando:</span><span class="sxs-lookup"><span data-stu-id="a0e78-147">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="a0e78-148">Una volta che si dispone dell'UPN dell'account e del nome del ruolo, utilizzare questi comandi per assegnare il ruolo all'account:</span><span class="sxs-lookup"><span data-stu-id="a0e78-148">Once you have the UPN of the account and the name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

<span data-ttu-id="a0e78-149">Copiare i comandi e incollarli nel blocco note.</span><span class="sxs-lookup"><span data-stu-id="a0e78-149">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="a0e78-150">Per le variabili **$upnName** e **$roleName** , sostituire il testo della descrizione con i relativi valori, \< rimuovere i caratteri e > e lasciare le virgolette.</span><span class="sxs-lookup"><span data-stu-id="a0e78-150">For the **$upnName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="a0e78-151">Copiare le righe modificate e incollarle nel modulo di Windows Azure Active Directory modulo affinché Windows PowerShell le esegua.</span><span class="sxs-lookup"><span data-stu-id="a0e78-151">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="a0e78-152">In alternativa, è possibile utilizzare Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a0e78-152">Alternately, you can use the Windows PowerShell ISE.</span></span>
  
<span data-ttu-id="a0e78-153">Segue un esempio di un set di comandi completati:</span><span class="sxs-lookup"><span data-stu-id="a0e78-153">Here is an example of a completed command set:</span></span>
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="a0e78-154">Per più modifiche di ruoli</span><span class="sxs-lookup"><span data-stu-id="a0e78-154">For multiple role changes</span></span>

<span data-ttu-id="a0e78-155">Determinare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="a0e78-155">Determine the following:</span></span>
  
- <span data-ttu-id="a0e78-156">Quali account utente configurare.</span><span class="sxs-lookup"><span data-stu-id="a0e78-156">Which user accounts that you want to configure.</span></span> <span data-ttu-id="a0e78-157">È possibile utilizzare i metodi descritti nella sezione precedente per raccogliere il set di nomi visualizzati o UPN.</span><span class="sxs-lookup"><span data-stu-id="a0e78-157">You can use the methods in the previous section to gather the set of display names or UPNs.</span></span>
    
- <span data-ttu-id="a0e78-158">Ruoli che si desidera assegnare a ogni account utente.</span><span class="sxs-lookup"><span data-stu-id="a0e78-158">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="a0e78-159">Per visualizzare l'elenco dei ruoli disponibili che è possibile assegnare agli account utente, usare questo comando:</span><span class="sxs-lookup"><span data-stu-id="a0e78-159">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="a0e78-160">Successivamente, creare un file di testo con valori delimitati da virgole (CSV) con il nome visualizzato o i campi UPN e nome ruolo.</span><span class="sxs-lookup"><span data-stu-id="a0e78-160">Next, create a comma-separated value (CSV) text file that has the display name or UPN and role name fields.</span></span> <span data-ttu-id="a0e78-161">È possibile eseguire questa operazione facilmente con Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="a0e78-161">You can do this easily with Microsoft Excel.</span></span>

<span data-ttu-id="a0e78-162">Di seguito è riportato un esempio per i nomi visualizzati:</span><span class="sxs-lookup"><span data-stu-id="a0e78-162">Here is an example for display names:</span></span>
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

<span data-ttu-id="a0e78-163">Immettere infine il percorso del file CSV ed eseguire i comandi risultanti al prompt dei comandi di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a0e78-163">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

<span data-ttu-id="a0e78-164">Di seguito è riportato un esempio per UPN:</span><span class="sxs-lookup"><span data-stu-id="a0e78-164">Here is an example for UPNs:</span></span>
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

<span data-ttu-id="a0e78-165">Immettere infine il percorso del file CSV ed eseguire i comandi risultanti al prompt dei comandi di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a0e78-165">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```


## <a name="see-also"></a><span data-ttu-id="a0e78-166">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a0e78-166">See also</span></span>

- [<span data-ttu-id="a0e78-167">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0e78-167">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="a0e78-168">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="a0e78-168">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="a0e78-169">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="a0e78-169">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
