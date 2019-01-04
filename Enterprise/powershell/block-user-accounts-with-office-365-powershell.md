---
title: Bloccare gli account utente con Office 365 PowerShell
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
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Questo articolo viene illustrato come utilizzare Office 365 PowerShell per bloccare e sbloccare l'accesso agli account di Office 365.
ms.openlocfilehash: 0e1ac3f61acafedd77c2af760b8316aa6b936e7b
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546477"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="b6243-103">Bloccare gli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b6243-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="b6243-104">**Riepilogo:**  Questo articolo viene illustrato come utilizzare Office 365 PowerShell per bloccare e sbloccare l'accesso agli account di Office 365.</span><span class="sxs-lookup"><span data-stu-id="b6243-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="b6243-p101">Bloccare l'accesso a un account di Office 365 consente di evitare di utilizzare l'account per l'accesso e accedere ai servizi e dati all'interno dell'organizzazione Office 365. È possibile utilizzare Office 365 PowerShell per bloccare l'accesso a singoli e più account utente.</span><span class="sxs-lookup"><span data-stu-id="b6243-p101">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization. You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="b6243-107">Utilizzare grafico modulo di Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="b6243-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="b6243-108">Primo, [la connessione al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="b6243-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="b6243-109">Bloccare l'accesso a singoli account utente</span><span class="sxs-lookup"><span data-stu-id="b6243-109">Block access to individual user accounts</span></span>

<span data-ttu-id="b6243-110">Per bloccare un singolo account utente, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="b6243-110">Use the following syntax to block an individual user account:</span></span>
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="b6243-111">Il parametro - ObjectID nel cmdlet Set-AzureAD accetta uno l'account nome di accesso, anche noto come il nome dell'entità utente o l'ID oggetto. dell'account</span><span class="sxs-lookup"><span data-stu-id="b6243-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="b6243-112">Questo esempio consente di bloccare l'accesso all'account utente fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="b6243-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="b6243-113">Per sbloccare questo account utente, eseguire il comando riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="b6243-113">To unblock this user account, run the following command:</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="b6243-114">Per visualizzare l'account utente che UPN in base al nome visualizzato dell'utente, utilizzare i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="b6243-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="b6243-115">In questo esempio viene visualizzato l'account utente UPN per l'utente denominato di Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="b6243-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="b6243-116">Per bloccare un account in base al nome visualizzato dell'utente, utilizzare i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="b6243-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="b6243-117">In qualsiasi momento, è possibile controllare lo stato bloccato di un account utente con il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="b6243-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="b6243-118">Bloccare l'accesso a più account utente</span><span class="sxs-lookup"><span data-stu-id="b6243-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="b6243-119">Per bloccare l'accesso a più account utente, creare un file di testo contenente un account nome di accesso su ogni riga simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="b6243-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="b6243-p102">Nei comandi seguenti, il file di testo di esempio è C:\My Documents\Accounts.txt. Sostituire con il percorso e il nome del file di testo.</span><span class="sxs-lookup"><span data-stu-id="b6243-p102">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="b6243-122">Per bloccare l'accesso agli account elencati nel file di testo, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="b6243-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="b6243-123">Per sbloccare gli account elencati nel file di testo, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="b6243-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="b6243-124">Utilizzare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b6243-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="b6243-125">Primo, [la connessione al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="b6243-125">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="b6243-126">Bloccare l'accesso a singoli account utente</span><span class="sxs-lookup"><span data-stu-id="b6243-126">Block access to individual user accounts</span></span>

<span data-ttu-id="b6243-127">Per bloccare l'accesso a un singolo account utente, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="b6243-127">Use the following syntax to block access to an individual user account:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

<span data-ttu-id="b6243-128">Questo esempio consente di bloccare l'accesso all'account utente fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="b6243-128">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="b6243-129">Per sbloccare l'account utente, eseguire il comando riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="b6243-129">To unblock the user account, run the following command:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="b6243-130">In qualsiasi momento, è possibile controllare lo stato bloccato di un account utente con il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="b6243-130">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="b6243-131">Bloccare l'accesso a più account utente</span><span class="sxs-lookup"><span data-stu-id="b6243-131">Block access to multiple user accounts</span></span>

<span data-ttu-id="b6243-132">Per prima cosa, creare un file di testo contenente un account su ogni riga simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="b6243-132">First, create a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="b6243-p103">Nei comandi seguenti, il file di testo di esempio è C:\My Documents\Accounts.txt. Sostituire con il percorso e il nome del file di testo.</span><span class="sxs-lookup"><span data-stu-id="b6243-p103">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="b6243-135">Per bloccare l'accesso agli account elencati nel file di testo, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="b6243-135">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="b6243-136">Per sbloccare gli account elencati nel file di testo, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="b6243-136">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="b6243-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b6243-137">See also</span></span>

[<span data-ttu-id="b6243-138">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b6243-138">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="b6243-139">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="b6243-139">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="b6243-140">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="b6243-140">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
