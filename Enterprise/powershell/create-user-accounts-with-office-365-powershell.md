---
title: Creare account utente con Office 365 PowerShell
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
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Informazioni su come usare PowerShell di Office 365 per creare account utente in Office 365.
ms.openlocfilehash: 618459cbf226a9a7cef0e03c7126d791f2ca8bc8
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257415"
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="f3e4d-103">Creare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3e4d-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="f3e4d-104">**Sintesi**: Informazioni su come usare PowerShell di Office 365 per creare account utente in Office 365.</span><span class="sxs-lookup"><span data-stu-id="f3e4d-104">**Summary:** Learn how to use Office 365 PowerShell to create user accounts in Office 365.</span></span>
  
<span data-ttu-id="f3e4d-p101">È possibile utilizzare PowerShell di Office 365 per creare in modo efficiente account utente, in particolare di tipo multiplo. Quando si creano account utente in PowerShell di Office 365, alcune proprietà dell'account sono sempre richieste. Altre proprietà non sono necessarie per creare l'account, ma sono comunque importanti. Tali proprietà sono descritte nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="f3e4d-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
|<span data-ttu-id="f3e4d-109">**Nome della proprietà**</span><span class="sxs-lookup"><span data-stu-id="f3e4d-109">**Property name**</span></span>|<span data-ttu-id="f3e4d-110">**Obbligatorio?**</span><span class="sxs-lookup"><span data-stu-id="f3e4d-110">**Required?**</span></span>|<span data-ttu-id="f3e4d-111">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="f3e4d-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="f3e4d-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="f3e4d-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="f3e4d-113">Sì</span><span class="sxs-lookup"><span data-stu-id="f3e4d-113">Yes</span></span>  <br/> |<span data-ttu-id="f3e4d-p102">Si tratta del nome visualizzato usato nei servizi Office 365. Ad esempio, Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="f3e4d-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="f3e4d-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="f3e4d-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="f3e4d-117">Sì</span><span class="sxs-lookup"><span data-stu-id="f3e4d-117">Yes</span></span>  <br/> |<span data-ttu-id="f3e4d-p103">Si tratta del nome dell'account utilizzato per accedere ai servizi Office 365. Ad esempio, CalebS@contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="f3e4d-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="f3e4d-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="f3e4d-120">**FirstName**</span></span> <br/> |<span data-ttu-id="f3e4d-121">No</span><span class="sxs-lookup"><span data-stu-id="f3e4d-121">No</span></span>  <br/> ||
|<span data-ttu-id="f3e4d-122">**LastName**</span><span class="sxs-lookup"><span data-stu-id="f3e4d-122">**LastName**</span></span> <br/> |<span data-ttu-id="f3e4d-123">No</span><span class="sxs-lookup"><span data-stu-id="f3e4d-123">No</span></span>  <br/> ||
|<span data-ttu-id="f3e4d-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="f3e4d-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="f3e4d-125">No</span><span class="sxs-lookup"><span data-stu-id="f3e4d-125">No</span></span>  <br/> |<span data-ttu-id="f3e4d-p104">Questo è il piano di gestione delle licenze (detto anche piano di licenze, piano Office 365 o SKU) dal quale una licenza disponibile viene assegnata all'account utente. La licenza definisce i servizi Office 365 che sono disponibili per l'account. Non è necessario assegnare una licenza a un utente, quando si crea l'account. Tuttavia, l'account richiede una licenza per accedere ai servizi Office 365. Si hanno a disposizione 30 giorni di tempo per assegnare la licenza all'account utente, dopo averlo creato.</span><span class="sxs-lookup"><span data-stu-id="f3e4d-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.</span></span> |
|<span data-ttu-id="f3e4d-130">**Password**</span><span class="sxs-lookup"><span data-stu-id="f3e4d-130">**Password**</span></span> <br/> |<span data-ttu-id="f3e4d-131">No</span><span class="sxs-lookup"><span data-stu-id="f3e4d-131">No</span></span>  <br/> | <span data-ttu-id="f3e4d-p105">Se non si specifica una password, all'account utente ne viene assegnata una casuale, visibile nei risultati del comando. Se si specifica una password, è necessario che contenga da 8 a 16 caratteri di testo ASCII di uno dei tre tipi seguenti: lettere minuscole, lettere maiuscole, numeri e simboli.</span><span class="sxs-lookup"><span data-stu-id="f3e4d-p105">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to be 8 to 16 ASCII text characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="f3e4d-134">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="f3e4d-134">**UsageLocation**</span></span> <br/> |<span data-ttu-id="f3e4d-135">No</span><span class="sxs-lookup"><span data-stu-id="f3e4d-135">No</span></span>  <br/> |<span data-ttu-id="f3e4d-p106">Si tratta di un codice paese ISO 3166-1 alpha-2. Ad esempio, US per gli Stati Uniti e FR per la Francia. È importante indicare questo valore, poiché alcuni servizi Office 365 non sono visibili in determinati paesi. In questo caso, è possibile assegnare una licenza a un account utente solo se l'account stesso dispone di un valore configurato. Per altre informazioni, vedere [Informazioni sulle restrizioni di licenza](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="f3e4d-p106">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="f3e4d-140">Usare il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="f3e4d-140">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="f3e4d-141">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="f3e4d-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="f3e4d-142">Una volta stabilita la connessione, utilizzare la sintassi seguente per creare un singolo account:</span><span class="sxs-lookup"><span data-stu-id="f3e4d-142">After you have connected, use the following syntax to create an individual account:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="f3e4d-143">In questo esempio viene creato un account per l'utente degli Stati Uniti chiamato Caleb Sills:</span><span class="sxs-lookup"><span data-stu-id="f3e4d-143">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="f3e4d-144">Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3e4d-144">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="f3e4d-145">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="f3e4d-145">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="create-an-individual-user-account"></a><span data-ttu-id="f3e4d-146">Creare un account utente singolo</span><span class="sxs-lookup"><span data-stu-id="f3e4d-146">Create an individual user account</span></span>

<span data-ttu-id="f3e4d-147">Per creare un singolo account, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="f3e4d-147">To create an individual account, use the following syntax:</span></span>
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
><span data-ttu-id="f3e4d-148">PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per il modulo di Windows PowerShell e i cmdlet con **MSOL** nel proprio nome.</span><span class="sxs-lookup"><span data-stu-id="f3e4d-148">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="f3e4d-149">Per continuare a utilizzare questi cmdlet, è necessario eseguirli da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3e4d-149">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="f3e4d-150">Per elencare i nomi dei piani di gestione delle licenze disponibili, usare il seguente comando:</span><span class="sxs-lookup"><span data-stu-id="f3e4d-150">To list the available licensing plan names, use this command:</span></span>

````powershell
Get-MsolAccountSku
````

<span data-ttu-id="f3e4d-151">In questo esempio viene creato un account per l'utente degli Stati Uniti chiamato Caleb Sills, a cui viene assegnata una licenza dal piano `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="f3e4d-151">This example creates an account for the United States user named Caleb Sills, and assigns a license from the `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a><span data-ttu-id="f3e4d-152">Creare più account utente</span><span class="sxs-lookup"><span data-stu-id="f3e4d-152">Create multiple user accounts</span></span>

1. <span data-ttu-id="f3e4d-p108">Creare un file CSV che includa le necessarie informazioni sull'account utente. Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f3e4d-p108">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```powershell
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="f3e4d-155">I nomi della colonna e il loro ordina nella prima riga del file CVS sono arbitrari. Tuttavia, è opportuno assicurarsi che i dati nel resto del file corrispondano all'ordine relativo ai nomi della colonna e li utilizzino per i valori del parametro nel comando PowerShell di Office 365.</span><span class="sxs-lookup"><span data-stu-id="f3e4d-155">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="f3e4d-156">Utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="f3e4d-156">Use the following syntax:</span></span>
    
  ```powershell
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="f3e4d-157">In questo esempio, vengono creati gli account utente dal file denominato C:\My Documents\NewAccounts.csv, quindi vengono registrati i risultati nel file C:\My Documents\NewAccountResults.csv</span><span class="sxs-lookup"><span data-stu-id="f3e4d-157">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```powershell
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="f3e4d-p109">Esaminare il file di output per visualizzare i risultati. Non sono state indicate password, quindi quelle casuali generate da Office 365 sono visibili nel file di output.</span><span class="sxs-lookup"><span data-stu-id="f3e4d-p109">Review the output file to see the results. We didn't specify passwords, so the random passwords that Office 365 generated are visible in the output file.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="f3e4d-160">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f3e4d-160">See also</span></span>

[<span data-ttu-id="f3e4d-161">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3e4d-161">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="f3e4d-162">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="f3e4d-162">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f3e4d-163">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="f3e4d-163">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
