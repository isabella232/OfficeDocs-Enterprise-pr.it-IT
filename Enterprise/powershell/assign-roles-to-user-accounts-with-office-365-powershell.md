---
title: Assegnare i ruoli agli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 'Sintesi: usare Office 365 PowerShell per assegnare ruoli agli account utente.'
ms.openlocfilehash: 3b57862d78d8699da033ed016338a449650e7140
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841673"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="f33fc-103">Assegnare i ruoli agli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f33fc-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="f33fc-104">Per assegnare ruoli agli account utente in modo semplice e rapido, è possibile usare Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f33fc-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="f33fc-105">Usare il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="f33fc-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="f33fc-106">In primo luogo, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) con un account amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="f33fc-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="f33fc-p101">Determinare quindi il nome di accesso dell'account utente da aggiungere a un ruolo (ad esempio mario@contoso.com). Questo nome di accesso è noto anche come nome dell'entità utente (UPN).</span><span class="sxs-lookup"><span data-stu-id="f33fc-p101">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com). This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="f33fc-109">Successivamente, determinare il nome del ruolo.</span><span class="sxs-lookup"><span data-stu-id="f33fc-109">Next, determine the name of the role.</span></span> <span data-ttu-id="f33fc-110">Usare questo [elenco di autorizzazioni del ruolo di amministratore in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span><span class="sxs-lookup"><span data-stu-id="f33fc-110">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="f33fc-111">Prestare attenzione alle note in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="f33fc-111">Pay attention to the notes in this article.</span></span> <span data-ttu-id="f33fc-112">Alcuni nomi di ruoli sono diversi per Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f33fc-112">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="f33fc-113">Ad esempio, il ruolo "Amministratore di SharePoint" nell'interfaccia di amministrazione di Microsoft 365 è denominato "Amministratore del servizio SharePoint" in Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f33fc-113">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="f33fc-114">Immettere quindi i nomi di accesso e di ruolo ed eseguire questi comandi.</span><span class="sxs-lookup"><span data-stu-id="f33fc-114">Next, fill in the sign-in and role names and run these commands.</span></span>
  
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

<span data-ttu-id="f33fc-115">Di seguito è riportato un esempio di un set di comandi completato che assegna il ruolo di amministratore del servizio di SharePoint all'account belindan@contoso.com:</span><span class="sxs-lookup"><span data-stu-id="f33fc-115">Here is an example of a completed command set that assigns the SharePoint Service Administrator role to the belindan@contoso.com account:</span></span>
  
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

<span data-ttu-id="f33fc-116">Per visualizzare l'elenco dei nomi utente per un ruolo specifico, usare questi comandi.</span><span class="sxs-lookup"><span data-stu-id="f33fc-116">To display the list of user names for a specific role, use these commands.</span></span>

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="f33fc-117">Usare il Modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f33fc-117">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="f33fc-118">In primo luogo, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) con un account amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="f33fc-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="f33fc-119">Per una singola modifica del ruolo</span><span class="sxs-lookup"><span data-stu-id="f33fc-119">For a single role change</span></span>

<span data-ttu-id="f33fc-120">La modalità più comune di un account utente specifico è il nome visualizzato o il nome di posta elettronica, noto anche come nome di accesso o nome dell'entità utente (UPN).</span><span class="sxs-lookup"><span data-stu-id="f33fc-120">The most common ways of specific user account is with its display name or its email name, also known its sign-in name or user principal name (UPN).</span></span>

#### <a name="display-names-of-user-accounts"></a><span data-ttu-id="f33fc-121">Visualizzazione dei nomi degli account utente</span><span class="sxs-lookup"><span data-stu-id="f33fc-121">Display names of user accounts</span></span>

<span data-ttu-id="f33fc-122">Se si è abituati a utilizzare i nomi visualizzati degli account utente, determinare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="f33fc-122">If you are used to working with the display names of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="f33fc-123">L'account utente da configurare.</span><span class="sxs-lookup"><span data-stu-id="f33fc-123">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="f33fc-p104">Per specificare l'account utente, è necessario determinare il nome visualizzato. Per ottenere un elenco completo di account, utilizzare questo comando:</span><span class="sxs-lookup"><span data-stu-id="f33fc-p104">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="f33fc-p105">Questo comando elenca il nome visualizzato degli account utente, ordinati per nome visualizzato, una schermata alla volta. È possibile filtrare l'elenco in un set più piccolo utilizzando il cmdlet **Where**. Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="f33fc-p105">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>

   >[!Note]
   ><span data-ttu-id="f33fc-129">PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per Windows PowerShell e i cmdlet con **MSOL** all'interno del nome.</span><span class="sxs-lookup"><span data-stu-id="f33fc-129">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="f33fc-130">Per continuare a usare i cmdlet, è necessario eseguirli in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f33fc-130">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="f33fc-131">Questo comando elenca solo gli account utente per cui il nome visualizzato inizia con "John".</span><span class="sxs-lookup"><span data-stu-id="f33fc-131">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="f33fc-132">Il ruolo da assegnare.</span><span class="sxs-lookup"><span data-stu-id="f33fc-132">The role you want to assign.</span></span>
    
    <span data-ttu-id="f33fc-133">Per visualizzare l'elenco dei ruoli disponibili che è possibile assegnare agli account utente, usare il comando:</span><span class="sxs-lookup"><span data-stu-id="f33fc-133">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="f33fc-134">Dopo aver determinato il nome visualizzato dell'account e il nome del ruolo, è possibile utilizzare questi comandi per assegnare il ruolo all'account:</span><span class="sxs-lookup"><span data-stu-id="f33fc-134">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="f33fc-p107">Copiare i comandi e incollarli nel blocco note. Per le variabili **$dispName** e **$roleName**, sostituire il testo della descrizione con i rispettivi valori, rimuovere i caratteri \< e > e lasciare le virgolette. Copiare le righe modificate e incollarle nel modulo di Windows Azure Active Directory modulo affinché Windows PowerShell le esegua. È anche possibile utilizzare Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="f33fc-p107">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="f33fc-139">Segue un esempio di un set di comandi completati:</span><span class="sxs-lookup"><span data-stu-id="f33fc-139">Here is an example of a completed command set:</span></span>
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a><span data-ttu-id="f33fc-140">Nomi di accesso degli account utente</span><span class="sxs-lookup"><span data-stu-id="f33fc-140">Sign-in names of user accounts</span></span>

<span data-ttu-id="f33fc-141">Se si è abituati a utilizzare i nomi di accesso o gli account utente di UPN, determinare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="f33fc-141">If you are used to working with the sign-in names or UPNs of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="f33fc-142">UPN dell'account utente.</span><span class="sxs-lookup"><span data-stu-id="f33fc-142">The user account's UPN.</span></span>
    
    <span data-ttu-id="f33fc-143">Se non si conosce già l'UPN, utilizzare il seguente comando:</span><span class="sxs-lookup"><span data-stu-id="f33fc-143">If you don't already know the UPN, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="f33fc-144">Questo comando consente di elencare l'UPN degli account utente, ordinati in base all'UPN, una schermata alla volta.</span><span class="sxs-lookup"><span data-stu-id="f33fc-144">This command lists the UPN of your user accounts, sorted by the UPN, one screen at a time.</span></span> <span data-ttu-id="f33fc-145">È possibile filtrare l'elenco in un set più piccolo utilizzando il cmdlet **Where**.</span><span class="sxs-lookup"><span data-stu-id="f33fc-145">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="f33fc-146">Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="f33fc-146">Here is an example:</span></span>
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="f33fc-147">Questo comando elenca solo gli account utente per cui il nome visualizzato inizia con "John".</span><span class="sxs-lookup"><span data-stu-id="f33fc-147">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="f33fc-148">Il ruolo da assegnare.</span><span class="sxs-lookup"><span data-stu-id="f33fc-148">The role you want to assign.</span></span>
    
    <span data-ttu-id="f33fc-149">Per visualizzare l'elenco dei ruoli disponibili che è possibile assegnare agli account utente, usare il comando:</span><span class="sxs-lookup"><span data-stu-id="f33fc-149">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="f33fc-150">Una volta che si dispone dell'UPN dell'account e del nome del ruolo, utilizzare questi comandi per assegnare il ruolo all'account:</span><span class="sxs-lookup"><span data-stu-id="f33fc-150">Once you have the UPN of the account and the name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

<span data-ttu-id="f33fc-151">Copiare i comandi e incollarli nel blocco note.</span><span class="sxs-lookup"><span data-stu-id="f33fc-151">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="f33fc-152">Per le variabili **$upnName** e **$roleName** , sostituire il testo della descrizione con i relativi valori, \< rimuovere i caratteri e > e lasciare le virgolette.</span><span class="sxs-lookup"><span data-stu-id="f33fc-152">For the **$upnName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="f33fc-153">Copiare le righe modificate e incollarle nel modulo di Windows Azure Active Directory modulo affinché Windows PowerShell le esegua.</span><span class="sxs-lookup"><span data-stu-id="f33fc-153">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="f33fc-154">In alternativa, è possibile utilizzare Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f33fc-154">Alternately, you can use the Windows PowerShell ISE.</span></span>
  
<span data-ttu-id="f33fc-155">Segue un esempio di un set di comandi completati:</span><span class="sxs-lookup"><span data-stu-id="f33fc-155">Here is an example of a completed command set:</span></span>
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a><span data-ttu-id="f33fc-156">Modifiche a più ruoli</span><span class="sxs-lookup"><span data-stu-id="f33fc-156">Multiple role changes</span></span>

<span data-ttu-id="f33fc-157">Per le modifiche a più ruoli, determinare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="f33fc-157">For multiple role changes, determine the following:</span></span>
  
- <span data-ttu-id="f33fc-158">Quali account utente configurare.</span><span class="sxs-lookup"><span data-stu-id="f33fc-158">Which user accounts that you want to configure.</span></span> <span data-ttu-id="f33fc-159">È possibile utilizzare i metodi descritti nella sezione precedente per raccogliere il set di nomi visualizzati o UPN.</span><span class="sxs-lookup"><span data-stu-id="f33fc-159">You can use the methods in the previous section to gather the set of display names or UPNs.</span></span>
    
- <span data-ttu-id="f33fc-160">Ruoli che si desidera assegnare a ogni account utente.</span><span class="sxs-lookup"><span data-stu-id="f33fc-160">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="f33fc-161">Per visualizzare l'elenco dei ruoli disponibili che è possibile assegnare agli account utente, usare questo comando:</span><span class="sxs-lookup"><span data-stu-id="f33fc-161">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="f33fc-162">Successivamente, creare un file di testo con valori delimitati da virgole (CSV) con il nome visualizzato o i campi UPN e nome ruolo.</span><span class="sxs-lookup"><span data-stu-id="f33fc-162">Next, create a comma-separated value (CSV) text file that has the display name or UPN and role name fields.</span></span> <span data-ttu-id="f33fc-163">È possibile eseguire questa operazione facilmente con Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="f33fc-163">You can do this easily with Microsoft Excel.</span></span>

<span data-ttu-id="f33fc-164">Di seguito è riportato un esempio per i nomi visualizzati:</span><span class="sxs-lookup"><span data-stu-id="f33fc-164">Here is an example for display names:</span></span>
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

<span data-ttu-id="f33fc-165">Immettere infine il percorso del file CSV ed eseguire i comandi risultanti al prompt dei comandi di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f33fc-165">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

<span data-ttu-id="f33fc-166">Di seguito è riportato un esempio per UPN:</span><span class="sxs-lookup"><span data-stu-id="f33fc-166">Here is an example for UPNs:</span></span>
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

<span data-ttu-id="f33fc-167">Immettere infine il percorso del file CSV ed eseguire i comandi risultanti al prompt dei comandi di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f33fc-167">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="f33fc-168">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f33fc-168">See also</span></span>

- [<span data-ttu-id="f33fc-169">Gestire gli account utente, le licenze e i gruppi con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f33fc-169">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="f33fc-170">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="f33fc-170">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="f33fc-171">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="f33fc-171">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
