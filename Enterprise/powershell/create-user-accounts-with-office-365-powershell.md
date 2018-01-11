---
title: Creare account utente con Office 365 PowerShell
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Informazioni su come usare PowerShell di Office 365 per creare account utente in Office 365.
ms.openlocfilehash: 97830f8158f84e6978cf3f2d168aa83d9fc551e6
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="a1fe8-103">Creare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1fe8-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="a1fe8-104">**Sintesi**: Informazioni su come usare PowerShell di Office 365 per creare account utente in Office 365.</span><span class="sxs-lookup"><span data-stu-id="a1fe8-104">**Summary:** Learn how to use Office 365 PowerShell to create user accounts in Office 365.</span></span>
  
<span data-ttu-id="a1fe8-p101">È possibile utilizzare PowerShell di Office 365 per creare in modo efficiente account utente, in particolare di tipo multiplo. Quando si creano account utente in PowerShell di Office 365, alcune proprietà dell'account sono sempre richieste. Altre proprietà non sono necessarie per creare l'account, ma sono comunque importanti. Tali proprietà sono descritte nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="a1fe8-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
****

|<span data-ttu-id="a1fe8-109">**Nome della proprietà**</span><span class="sxs-lookup"><span data-stu-id="a1fe8-109">**Property name**</span></span>|<span data-ttu-id="a1fe8-110">**Obbligatorio?**</span><span class="sxs-lookup"><span data-stu-id="a1fe8-110">**Required?**</span></span>|<span data-ttu-id="a1fe8-111">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="a1fe8-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="a1fe8-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="a1fe8-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="a1fe8-113">Sì</span><span class="sxs-lookup"><span data-stu-id="a1fe8-113">Yes</span></span>  <br/> |<span data-ttu-id="a1fe8-p102">Si tratta del nome visualizzato usato nei servizi Office 365. Ad esempio, Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="a1fe8-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="a1fe8-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="a1fe8-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="a1fe8-117">Sì</span><span class="sxs-lookup"><span data-stu-id="a1fe8-117">Yes</span></span>  <br/> |<span data-ttu-id="a1fe8-p103">Si tratta del nome dell'account utilizzato per accedere ai servizi Office 365. Ad esempio, CalebS@contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="a1fe8-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="a1fe8-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="a1fe8-120">**FirstName**</span></span> <br/> |<span data-ttu-id="a1fe8-121">No</span><span class="sxs-lookup"><span data-stu-id="a1fe8-121">No</span></span>  <br/> ||
|<span data-ttu-id="a1fe8-122">**LastName**</span><span class="sxs-lookup"><span data-stu-id="a1fe8-122">**LastName**</span></span> <br/> |<span data-ttu-id="a1fe8-123">No</span><span class="sxs-lookup"><span data-stu-id="a1fe8-123">No</span></span>  <br/> ||
|<span data-ttu-id="a1fe8-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="a1fe8-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="a1fe8-125">No</span><span class="sxs-lookup"><span data-stu-id="a1fe8-125">No</span></span>  <br/> |<span data-ttu-id="a1fe8-p104">Questo è il piano di gestione delle licenze (detto anche piano di licenze, piano Office 365 o SKU) dal quale una licenza disponibile viene assegnata all'account utente. La licenza definisce i servizi Office 365 che sono disponibili per l'account. Non è necessario assegnare una licenza a un utente, quando si crea l'account. Tuttavia, l'account richiede una licenza per accedere ai servizi Office 365. Si hanno a disposizione 30 giorni di tempo per assegnare la licenza all'account utente, dopo averlo creato.</span><span class="sxs-lookup"><span data-stu-id="a1fe8-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.  </span></span><br/> <span data-ttu-id="a1fe8-p105">Utilizzare il cmdlet **Get-MsolAccountSku** per visualizzare i piani di gestione delle licenze ( **AccountSkuId** ) e le licenze disponibili nell'organizzazione. Per ulteriori informazioni, vedere [Visualizzare le licenze e i servizi con PowerShell di Office 365](view-licenses-and-services-with-office-365-powershell.md).  </span><span class="sxs-lookup"><span data-stu-id="a1fe8-p105">Use the **Get-MsolAccountSku** cmdlet to view the licensing plans ( **AccountSkuId** ) and available licenses in your organization. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).  </span></span><br/> |
|<span data-ttu-id="a1fe8-132">**Password**</span><span class="sxs-lookup"><span data-stu-id="a1fe8-132">**Password**</span></span> <br/> |<span data-ttu-id="a1fe8-133">No</span><span class="sxs-lookup"><span data-stu-id="a1fe8-133">No</span></span>  <br/> | <span data-ttu-id="a1fe8-p106">Se non si specifica una password, all'account utente ne viene assegnata una casuale, visibile nei risultati del comando. Se si specifica una password, è necessario che rispetti i seguenti requisiti di complessità:</span><span class="sxs-lookup"><span data-stu-id="a1fe8-p106">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to meet the following complexity requirements:</span></span> <br/>  <span data-ttu-id="a1fe8-136">Da 8 a 16 caratteri di testo ASCII.</span><span class="sxs-lookup"><span data-stu-id="a1fe8-136">8 to 16 ASCII text characters.</span></span> <br/>  <span data-ttu-id="a1fe8-137">Caratteri di uno dei tre tipi seguenti: lettere minuscole: lettere minuscole, lettere maiuscole, numeri e simboli.</span><span class="sxs-lookup"><span data-stu-id="a1fe8-137">Characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="a1fe8-138">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="a1fe8-138">**UsageLocation**</span></span> <br/> |<span data-ttu-id="a1fe8-139">No</span><span class="sxs-lookup"><span data-stu-id="a1fe8-139">No</span></span>  <br/> |<span data-ttu-id="a1fe8-p107">Si tratta di un codice paese ISO 3166-1 alpha-2. Ad esempio, US per gli Stati Uniti e FR per la Francia. È importante indicare questo valore, poiché alcuni servizi Office 365 non sono visibili in determinati paesi. In questo caso, è possibile assegnare una licenza a un account utente solo se l'account stesso dispone di un valore configurato. Per altre informazioni, vedere [Informazioni sulle restrizioni di licenza](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="a1fe8-p107">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   
## <a name="before-you-begin"></a><span data-ttu-id="a1fe8-144">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="a1fe8-144">Before you begin</span></span>

<span data-ttu-id="a1fe8-p108">Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="a1fe8-p108">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a><span data-ttu-id="a1fe8-147">Utilizzare PowerShell di Office 365 per creare account utente individuali</span><span class="sxs-lookup"><span data-stu-id="a1fe8-147">Use Office 365 PowerShell to create individual user accounts</span></span>

<span data-ttu-id="a1fe8-148">Per creare un singolo account, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="a1fe8-148">To create an individual account, use the following syntax:</span></span>
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

<span data-ttu-id="a1fe8-149">In questo esempio viene creato un account per l'utente degli Stati Uniti chiamato Caleb Sills. Inoltre, gli viene assegnata una licenza dal piano  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="a1fe8-149">This example creates an account for the United States user named Caleb Sills, and assigns a license from the  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a><span data-ttu-id="a1fe8-150">Utilizzare PowerShell di Office 365 per creare più account utente</span><span class="sxs-lookup"><span data-stu-id="a1fe8-150">Use Office 365 PowerShell to create multiple user accounts</span></span>

1. <span data-ttu-id="a1fe8-p109">Creare un file CSV che includa le necessarie informazioni sull'account utente. Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="a1fe8-p109">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="a1fe8-153">I nomi della colonna e il loro ordina nella prima riga del file CVS sono arbitrari. Tuttavia, è opportuno assicurarsi che i dati nel resto del file corrispondano all'ordine relativo ai nomi della colonna e li utilizzino per i valori del parametro nel comando PowerShell di Office 365.</span><span class="sxs-lookup"><span data-stu-id="a1fe8-153">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="a1fe8-154">Utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="a1fe8-154">Use the following syntax:</span></span>
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="a1fe8-155">In questo esempio, vengono creati gli account utente dal file denominato C:\My Documents\NewAccounts.csv, quindi vengono registrati i risultati nel file C:\My Documents\NewAccountResults.csv</span><span class="sxs-lookup"><span data-stu-id="a1fe8-155">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="a1fe8-p110">Esaminare il file di output per visualizzare i risultati. Non sono state indicate password, quindi quelle casuali assegnate sono visibili nel file di output.</span><span class="sxs-lookup"><span data-stu-id="a1fe8-p110">Review the output file to see the results. We didn't specify passwords, so the random passwords that were generated are visible in the output file.</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a><span data-ttu-id="a1fe8-158">Utilizzare il modulo Azure Active Directory V2 PowerShell per creare account utente individuali</span><span class="sxs-lookup"><span data-stu-id="a1fe8-158">Use the Azure Active Directory V2 PowerShell module to create individual user accounts</span></span>

<span data-ttu-id="a1fe8-p111">Per utilizzare il cmdlet **New-AzureADUser** dal modulo Azure Active Directory V2 PowerShell, è necessario innanzitutto connettersi alla propria sottoscrizione. Per visualizzare le istruzioni, consultare [Connettersi con il modulo Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="a1fe8-p111">To use the **New-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="a1fe8-161">Una volta stabilita la connessione, utilizzare la sintassi seguente per creare un singolo account:</span><span class="sxs-lookup"><span data-stu-id="a1fe8-161">After you have connected, use the following syntax to create an individual account:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="a1fe8-162">In questo esempio viene creato un account per l'utente degli Stati Uniti chiamato Caleb Sills:</span><span class="sxs-lookup"><span data-stu-id="a1fe8-162">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a><span data-ttu-id="a1fe8-163">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a1fe8-163">See also</span></span>

<span data-ttu-id="a1fe8-164">Vedere i seguenti argomenti aggiuntivi sulla gestione degli utenti con Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a1fe8-164">See these additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="a1fe8-165">Eliminare e ripristinare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1fe8-165">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a1fe8-166">Bloccare gli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1fe8-166">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a1fe8-167">Assegnare le licenze agli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1fe8-167">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a1fe8-168">Rimuovere le licenze dagli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1fe8-168">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="a1fe8-169">Per ulteriori informazioni sui cmdlet utilizzati in questa procedura, vedere i seguenti argomenti:</span><span class="sxs-lookup"><span data-stu-id="a1fe8-169">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="a1fe8-170">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="a1fe8-170">Export-Csv</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- <span data-ttu-id="a1fe8-171">[Import-Csv](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv)</span><span class="sxs-lookup"><span data-stu-id="a1fe8-171">[Import-Csv](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv)</span></span>
    
- [<span data-ttu-id="a1fe8-172">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="a1fe8-172">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="a1fe8-173">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="a1fe8-173">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="a1fe8-174">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="a1fe8-174">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

