---
title: Assegnare i ruoli agli account utente con Office 365 PowerShell
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 'Sintesi: utilizzare PowerShell di Office 365 e il cmdlet Add-MsolRoleMember per assegnare ruoli agli account utente.'
ms.openlocfilehash: 97ecf29e10d14843322f3062ef16da14f16f7a2a
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2018
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="afd82-103">Assegnare i ruoli agli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="afd82-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="afd82-104">**Sintesi:** utilizzare PowerShell di Office 365 e il cmdlet **Add-MsolRoleMember** per assegnare ruoli agli account utente.</span><span class="sxs-lookup"><span data-stu-id="afd82-104">**Summary:** Use Office 365 PowerShell and the **Add-MsolRoleMember** cmdlet to assign roles to user accounts.</span></span>
  
<span data-ttu-id="afd82-105">È possibile rapidamente e facilmente assegnare ruoli agli account utente tramite PowerShell di Office 365 identificando il nome visualizzato dell'account utente e il nome del ruolo.</span><span class="sxs-lookup"><span data-stu-id="afd82-105">You can quickly and easily assign roles to user accounts using Office 365 PowerShell by identifying the user account's display name and the role name.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="afd82-106">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="afd82-106">Before you begin</span></span>

<span data-ttu-id="afd82-p101">Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365 utilizzando un account amministratore globale. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="afd82-p101">The procedures in this topic require you to connect to Office 365 PowerShell using a global administrator account. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="for-a-single-role-change"></a><span data-ttu-id="afd82-109">Per una singola modifica del ruolo</span><span class="sxs-lookup"><span data-stu-id="afd82-109">For a single role change</span></span>

<span data-ttu-id="afd82-110">Determinare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="afd82-110">Determine the following:</span></span>
  
- <span data-ttu-id="afd82-111">L'account utente da configurare.</span><span class="sxs-lookup"><span data-stu-id="afd82-111">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="afd82-p102">Per specificare l'account utente, è necessario determinare il nome visualizzato. Per ottenere un elenco completo di account, utilizzare questo comando:</span><span class="sxs-lookup"><span data-stu-id="afd82-p102">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="afd82-p103">Questo comando elenca il nome visualizzato degli account utente, ordinati per nome visualizzato, una schermata alla volta. È possibile filtrare l'elenco in un set più piccolo utilizzando il cmdlet **Where**. Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="afd82-p103">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="afd82-117">Questo comando elenca solo gli account utente per cui il nome visualizzato inizia con "John".</span><span class="sxs-lookup"><span data-stu-id="afd82-117">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="afd82-118">Il ruolo da assegnare.</span><span class="sxs-lookup"><span data-stu-id="afd82-118">The role you want to assign.</span></span>
    
    <span data-ttu-id="afd82-119">Per visualizzare l'elenco dei ruoli disponibili che è possibile assegnare agli account utente, usare il comando:</span><span class="sxs-lookup"><span data-stu-id="afd82-119">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="afd82-120">Dopo aver determinato il nome visualizzato dell'account e il nome del ruolo, è possibile utilizzare questi comandi per assegnare il ruolo all'account:</span><span class="sxs-lookup"><span data-stu-id="afd82-120">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="afd82-p104">Copiare i comandi e incollarli nel blocco note. Per le variabili **$dispName** e **$roleName**, sostituire il testo della descrizione con i rispettivi valori, rimuovere i caratteri \< e > e lasciare le virgolette. Copiare le righe modificate e incollarle nel modulo di Windows Azure Active Directory modulo affinché Windows PowerShell le esegua. È anche possibile utilizzare Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="afd82-p104">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="afd82-125">Segue un esempio di un set di comandi completati:</span><span class="sxs-lookup"><span data-stu-id="afd82-125">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a><span data-ttu-id="afd82-126">Per più modifiche di ruoli</span><span class="sxs-lookup"><span data-stu-id="afd82-126">For multiple role changes</span></span>

<span data-ttu-id="afd82-127">Determinare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="afd82-127">Determine the following:</span></span>
  
- <span data-ttu-id="afd82-128">Quali account utente configurare.</span><span class="sxs-lookup"><span data-stu-id="afd82-128">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="afd82-p105">Per specificare l'account utente, è necessario determinare il nome visualizzato. Per ottenere un elenco di account, utilizzare questo comando:</span><span class="sxs-lookup"><span data-stu-id="afd82-p105">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="afd82-p106">Questo comando elenca il nome visualizzato di tutti gli account utente, ordinati per nome visualizzato, una schermata alla volta. È possibile filtrare l'elenco in un set più piccolo utilizzando il cmdlet **Where**. Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="afd82-p106">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="afd82-134">Questo comando elenca solo gli account utente per cui il nome visualizzato inizia con "John".</span><span class="sxs-lookup"><span data-stu-id="afd82-134">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="afd82-135">Ruoli che si desidera assegnare a ogni account utente.</span><span class="sxs-lookup"><span data-stu-id="afd82-135">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="afd82-136">Per visualizzare l'elenco dei ruoli disponibili che è possibile assegnare agli account utente, usare il comando:</span><span class="sxs-lookup"><span data-stu-id="afd82-136">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="afd82-p107">Successivamente, creare un file CSV che includa i campi Nome visualizzato e Nome del ruolo. Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="afd82-p107">Next, create a comma-separated value (CSV) text file that contains the DisplayName and role Name fields. Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="afd82-139">Successivamente, immettere il percorso del file CSV ed eseguire i comandi risultanti nel prompt dei comandi di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="afd82-139">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="afd82-140">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="afd82-140">See also</span></span>

#### 

[<span data-ttu-id="afd82-141">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="afd82-141">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="afd82-142">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="afd82-142">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="afd82-143">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="afd82-143">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
#### 

[<span data-ttu-id="afd82-144">Add-MsolRoleMember</span><span class="sxs-lookup"><span data-stu-id="afd82-144">Add-MsolRoleMember</span></span>](https://msdn.microsoft.com/library/dn194120.aspx)

