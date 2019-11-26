---
title: Configurare le proprietà degli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/07/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Sintesi: utilizzare PowerShell di Office 365 per configurare le proprietà di uno o più account utente nel tenant di Office 365.'
ms.openlocfilehash: 67ce7d3c57f286f0b2365aa2503fdf1c8bc13429
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257657"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="88b87-103">Configurare le proprietà degli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="88b87-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="88b87-104">**Sintesi:** Utilizzare PowerShell di Office 365 per configurare le proprietà di uno o più account utente nel tenant di Office 365.</span><span class="sxs-lookup"><span data-stu-id="88b87-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="88b87-105">Anche se è possibile utilizzare l'interfaccia di amministrazione di Microsoft 365 per configurare le proprietà degli account utente del tenant di Office 365, è anche possibile utilizzare PowerShell per Office 365 e fare alcuni elementi che non possono essere configurati dal centro di amministrazione.</span><span class="sxs-lookup"><span data-stu-id="88b87-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="88b87-106">Usare il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="88b87-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="88b87-107">Per configurare le proprietà degli account utente con il modulo Azure Active Directory PowerShell per Graph, utilizzare il cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) e specificare le proprietà da impostare o modificare.</span><span class="sxs-lookup"><span data-stu-id="88b87-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="88b87-108">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="88b87-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="88b87-109">Modificare le proprietà per un account utente specifico</span><span class="sxs-lookup"><span data-stu-id="88b87-109">Change properties for a specific user account</span></span>

<span data-ttu-id="88b87-p101">Identificare l'account con il parametro **-ObjectID** e impostare o modificare proprietà specifiche con ulteriori parametri. Ecco un elenco dei parametri più comuni.</span><span class="sxs-lookup"><span data-stu-id="88b87-p101">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="88b87-112">-Department "\<nome reparto>"</span><span class="sxs-lookup"><span data-stu-id="88b87-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="88b87-113">-DisplayName "\<nome utente completo>"</span><span class="sxs-lookup"><span data-stu-id="88b87-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="88b87-114">-FacsimilieTelephoneNumber "\<numero fax>"</span><span class="sxs-lookup"><span data-stu-id="88b87-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="88b87-115">-GivenName "\<nome utente>"</span><span class="sxs-lookup"><span data-stu-id="88b87-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="88b87-116">-Surname "\<cognome utente>"</span><span class="sxs-lookup"><span data-stu-id="88b87-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="88b87-117">-Mobile "\<numero cellulare>"</span><span class="sxs-lookup"><span data-stu-id="88b87-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="88b87-118">-JobTitle "\<posizione professionale>"</span><span class="sxs-lookup"><span data-stu-id="88b87-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="88b87-119">-PreferredLanguage "\<lingua>"</span><span class="sxs-lookup"><span data-stu-id="88b87-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="88b87-120">-StreetAddress "\<indirizzo>"</span><span class="sxs-lookup"><span data-stu-id="88b87-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="88b87-121">-City "\<nome città>"</span><span class="sxs-lookup"><span data-stu-id="88b87-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="88b87-122">-State "\<nome stato>"</span><span class="sxs-lookup"><span data-stu-id="88b87-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="88b87-123">-PostalCode "\<CAP>"</span><span class="sxs-lookup"><span data-stu-id="88b87-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="88b87-124">-Country "\<nome paese>"</span><span class="sxs-lookup"><span data-stu-id="88b87-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="88b87-125">-TelephoneNumber "\<numero di telefono di ufficio>"</span><span class="sxs-lookup"><span data-stu-id="88b87-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="88b87-126">-UsageLocation "\<codice paese o area geografica a 2 caratteri>"</span><span class="sxs-lookup"><span data-stu-id="88b87-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="88b87-127">Si tratta del codice paese o area geografica a due lettere ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="88b87-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="88b87-128">Per ulteriori parametri, vedere [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="88b87-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="88b87-129">Per visualizzare il nome principale degli utenti per gli account utente, eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="88b87-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="88b87-130">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="88b87-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="88b87-131">Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="88b87-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="88b87-132">Elencare i nomi principali degli utenti in ordine alfabetico ( **Sort-Object UserPrincipalName** ) e inviarli al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="88b87-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="88b87-133">Visualizzare solo la proprietà del nome principale degli utenti per ogni account ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="88b87-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="88b87-134">Visualizzare gli elementi in una schermata alla volta ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="88b87-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="88b87-p102">Con questo comando vengono elencati tutti gli account. Se si desidera visualizzare il nome principale dell'utente di un account in base al nome visualizzato (nome e cognome), inserire la variabile **$userName** sotto (rimuovendo i caratteri \< e >), quindi eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="88b87-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="88b87-137">Questo esempio permette di visualizzare il nome dell’entità utente per l’account utente con nome visualizzato Caleb Sillis.</span><span class="sxs-lookup"><span data-stu-id="88b87-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="88b87-p103">Utilizzando una variabile **$upn**, è possibile apportare modifiche ai singoli account in base al nome visualizzato. Ecco un esempio di impostazione della posizione di utilizzo di Belinda Newman in Francia, specificando il nome visualizzato anziché il nome principale dell'utente:</span><span class="sxs-lookup"><span data-stu-id="88b87-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="88b87-140">Modificare le proprietà per tutti gli account utente</span><span class="sxs-lookup"><span data-stu-id="88b87-140">Change properties for all user accounts</span></span>

<span data-ttu-id="88b87-p104">Per modificare le proprietà per tutti gli utenti, è possibile utilizzare la combinazione di cmdlet **Get-AzureADUser** e **Set-AzureADUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti in Francia:</span><span class="sxs-lookup"><span data-stu-id="88b87-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="88b87-143">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="88b87-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="88b87-144">Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="88b87-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="88b87-145">Impostare la posizione dell'utente in Francia ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="88b87-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="88b87-146">Modificare le proprietà per un set specifico di account utente</span><span class="sxs-lookup"><span data-stu-id="88b87-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="88b87-p105">Per modificare le proprietà per un set specifico di account utente, è possibile utilizzare la combinazione di cmdlet **Get-AzureADUser**, **Where** e **Set-AzureADUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti del reparto Contabilità in Francia:</span><span class="sxs-lookup"><span data-stu-id="88b87-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="88b87-149">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="88b87-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="88b87-150">Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="88b87-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="88b87-151">Individuare tutti gli account utente con la proprietà Department impostata su "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) e inviare le informazioni risultanti al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="88b87-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="88b87-152">Impostare la posizione dell'utente in Francia ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="88b87-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="88b87-153">Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="88b87-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="88b87-154">Per configurare le proprietà degli account utente con il modulo di Microsoft Azure Active Directory per Windows PowerShell, utilizzare il cmdlet Set-MsolUser e specificare le proprietà da impostare o modificare.</span><span class="sxs-lookup"><span data-stu-id="88b87-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="88b87-155">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="88b87-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="88b87-156">PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per il modulo di Windows PowerShell e i cmdlet con **MSOL** nel proprio nome.</span><span class="sxs-lookup"><span data-stu-id="88b87-156">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="88b87-157">Per continuare a utilizzare questi cmdlet, è necessario eseguirli da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88b87-157">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="88b87-158">Modificare le proprietà per un account utente specifico</span><span class="sxs-lookup"><span data-stu-id="88b87-158">Change properties for a specific user account</span></span>

<span data-ttu-id="88b87-159">Per configurare le proprietà per un account utente specifico, utilizzare il cmdlet [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) e specificare le proprietà da impostare o modificare.</span><span class="sxs-lookup"><span data-stu-id="88b87-159">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="88b87-p107">Identificare l'account con il parametro **-UserPrincipalName** e impostare o modificare proprietà specifiche con ulteriori parametri. Ecco un elenco dei parametri più comuni.</span><span class="sxs-lookup"><span data-stu-id="88b87-p107">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="88b87-162">-City "\<nome città>"</span><span class="sxs-lookup"><span data-stu-id="88b87-162">-City "\<city name>"</span></span>
    
- <span data-ttu-id="88b87-163">-Country "\<nome paese>"</span><span class="sxs-lookup"><span data-stu-id="88b87-163">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="88b87-164">-Department "\<nome reparto>"</span><span class="sxs-lookup"><span data-stu-id="88b87-164">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="88b87-165">-DisplayName "\<nome utente completo>"</span><span class="sxs-lookup"><span data-stu-id="88b87-165">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="88b87-166">-Fax "\<numero fax>"</span><span class="sxs-lookup"><span data-stu-id="88b87-166">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="88b87-167">-FirstName "\<nome utente>"</span><span class="sxs-lookup"><span data-stu-id="88b87-167">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="88b87-168">-LastName "\<cognome utente>"</span><span class="sxs-lookup"><span data-stu-id="88b87-168">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="88b87-169">-MobilePhone "\<numero cellulare>"</span><span class="sxs-lookup"><span data-stu-id="88b87-169">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="88b87-170">-Office "\<ubicazione ufficio>"</span><span class="sxs-lookup"><span data-stu-id="88b87-170">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="88b87-171">-PhoneNumber "\<numero di telefono di ufficio>"</span><span class="sxs-lookup"><span data-stu-id="88b87-171">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="88b87-172">-PostalCode "\<CAP>"</span><span class="sxs-lookup"><span data-stu-id="88b87-172">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="88b87-173">-PreferredLanguage "\<lingua>"</span><span class="sxs-lookup"><span data-stu-id="88b87-173">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="88b87-174">-State "\<nome stato>"</span><span class="sxs-lookup"><span data-stu-id="88b87-174">-State "\<state name>"</span></span>
    
- <span data-ttu-id="88b87-175">-StreetAddress "\<indirizzo>"</span><span class="sxs-lookup"><span data-stu-id="88b87-175">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="88b87-176">-Title "\<nome titolo>"</span><span class="sxs-lookup"><span data-stu-id="88b87-176">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="88b87-177">-UsageLocation "\<codice paese o area geografica a 2 caratteri>"</span><span class="sxs-lookup"><span data-stu-id="88b87-177">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="88b87-178">Si tratta del codice paese o area geografica a due lettere ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="88b87-178">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="88b87-179">Per ulteriori parametri, vedere [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).</span><span class="sxs-lookup"><span data-stu-id="88b87-179">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>

<span data-ttu-id="88b87-180">Per visualizzare i nomi principali di tutti gli utenti, eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="88b87-180">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="88b87-181">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="88b87-181">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="88b87-182">Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="88b87-182">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="88b87-183">Elencare i nomi principali degli utenti in ordine alfabetico ( **Sort-Object UserPrincipalName** ) e inviarli al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="88b87-183">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="88b87-184">Visualizzare solo la proprietà del nome principale degli utenti per ogni account ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="88b87-184">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="88b87-185">Visualizzare gli elementi in una schermata alla volta ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="88b87-185">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="88b87-p108">Con questo comando vengono elencati tutti gli account. Se si desidera visualizzare il nome principale dell'utente di un account in base al nome visualizzato (nome e cognome), inserire la variabile **$userName** sotto (rimuovendo i caratteri \< e >), quindi eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="88b87-p108">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="88b87-188">Questo esempio permette di visualizzare il nome principale dell'utente denominato Caleb Sillis.</span><span class="sxs-lookup"><span data-stu-id="88b87-188">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="88b87-p109">Utilizzando una variabile **$upn**, è possibile apportare modifiche ai singoli account in base al nome visualizzato. Ecco un esempio di impostazione della posizione di utilizzo di Belinda Newman in Francia, specificando il nome visualizzato anziché il nome principale dell'utente:</span><span class="sxs-lookup"><span data-stu-id="88b87-p109">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="88b87-191">Modificare le proprietà per tutti gli account utente</span><span class="sxs-lookup"><span data-stu-id="88b87-191">Change properties for all user accounts</span></span>

<span data-ttu-id="88b87-p110">Per modificare le proprietà per tutti gli utenti, è possibile utilizzare la combinazione di cmdlet **Get-MsolUser** e **Set-MsolUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti in Francia:</span><span class="sxs-lookup"><span data-stu-id="88b87-p110">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="88b87-194">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="88b87-194">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="88b87-195">Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="88b87-195">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="88b87-196">Impostare la posizione dell'utente in Francia ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="88b87-196">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="88b87-197">Modificare le proprietà per un set specifico di account utente</span><span class="sxs-lookup"><span data-stu-id="88b87-197">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="88b87-p111">Per modificare le proprietà per un set specifico di account utente, è possibile utilizzare la combinazione di cmdlet **Get-MsolUser**, **Where-Object** e **Set-MsolUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti del reparto Contabilità in Francia:</span><span class="sxs-lookup"><span data-stu-id="88b87-p111">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="88b87-200">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="88b87-200">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="88b87-201">Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="88b87-201">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="88b87-202">Individuare tutti gli account utente con la proprietà Department impostata su "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) e inviare le informazioni risultanti al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="88b87-202">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="88b87-203">Impostare la posizione dell'utente in Francia ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="88b87-203">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="88b87-204">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="88b87-204">See also</span></span>

[<span data-ttu-id="88b87-205">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="88b87-205">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="88b87-206">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="88b87-206">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="88b87-207">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="88b87-207">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
