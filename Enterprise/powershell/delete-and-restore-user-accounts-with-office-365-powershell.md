---
title: Eliminare account utente con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Informazioni su come usare PowerShell di Office 365 per eliminare gli account utente di Office 365.
ms.openlocfilehash: b7c30ec422475a4cf11b28249e8a20d64a3c90a4
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2019
ms.locfileid: "38746429"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a><span data-ttu-id="d40a1-103">Eliminare account utente con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="d40a1-103">Delete user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="d40a1-104">È possibile usare PowerShell di Office 365 per eliminare un account utente.</span><span class="sxs-lookup"><span data-stu-id="d40a1-104">You can use Office 365 PowerShell to delete a user account.</span></span>
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d40a1-105">Usare il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="d40a1-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d40a1-106">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="d40a1-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="d40a1-107">Una volta stabilita la connessione, utilizzare la sintassi seguente per rimuovere un singolo account utente:</span><span class="sxs-lookup"><span data-stu-id="d40a1-107">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

<span data-ttu-id="d40a1-108">Questo esempio consente di rimuovere l'account utente fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="d40a1-108">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="d40a1-109">Il parametro **-ObjectID** nel cmdlet **Remove-AzureAD** accetta sia il nome utente dell’account, noto anche come Nome dell'entità utente, sia l'ID oggetto dell'account.</span><span class="sxs-lookup"><span data-stu-id="d40a1-109">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account's sign-in name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="d40a1-110">Per visualizzare il nome dell'account in base al nome dell'utente, usare i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="d40a1-110">To display the account name based on the user's name, use the following commands:</span></span>
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d40a1-111">Questo esempio permette di visualizzare il nome dell'account per l'utente Caleb Sillis.</span><span class="sxs-lookup"><span data-stu-id="d40a1-111">This example displays the account name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d40a1-112">Per rimuovere un account in base al nome visualizzato dell'utente, utilizzare i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="d40a1-112">To remove an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d40a1-113">Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d40a1-113">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d40a1-p101">Quando si elimina un account utente con il modulo di Microsoft Azure Active Directory per Windows PowerShell, questo non viene rimosso in modo definitivo. È possibile ripristinare l’account utente eliminato entro 30 giorni.</span><span class="sxs-lookup"><span data-stu-id="d40a1-p101">When you delete a user account with the Microsoft Azure Active Directory Module for Windows PowerShell, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>

<span data-ttu-id="d40a1-116">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="d40a1-116">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


<span data-ttu-id="d40a1-117">Per eliminare un account utente, utilizzare la sintassi riportata di seguito:</span><span class="sxs-lookup"><span data-stu-id="d40a1-117">To delete a user account, use the following syntax:</span></span>
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="d40a1-118">Questo esempio elimina l'account utente BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="d40a1-118">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="d40a1-119">Per ripristinare un account utente eliminato entro la fine del periodo di tolleranza di 30 giorni, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="d40a1-119">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="d40a1-120">Questo esempio consente di ripristinare l'account utente eliminato BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="d40a1-120">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="d40a1-121">**Note:**</span><span class="sxs-lookup"><span data-stu-id="d40a1-121">**Notes:**</span></span>
  
- <span data-ttu-id="d40a1-122">Per visualizzare un elenco di utenti eliminati che possono essere ripristinati, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="d40a1-122">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```powershell
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="d40a1-123">Se il nome dell'entità utente originale di un account viene usato da un altro account, fare ricorso al parametro _NewUserPrincipalName_ invece che a quello _UserPrincipalName_ per specificare un differente nome principale dell'utente, quando si ripristina l'account utente.</span><span class="sxs-lookup"><span data-stu-id="d40a1-123">If the user account's original user principal name is used by another account, use the _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>


## <a name="see-also"></a><span data-ttu-id="d40a1-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d40a1-124">See also</span></span>

[<span data-ttu-id="d40a1-125">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d40a1-125">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="d40a1-126">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="d40a1-126">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d40a1-127">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="d40a1-127">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

