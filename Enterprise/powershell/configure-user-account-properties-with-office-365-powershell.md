---
title: Configurare le proprietà degli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Sintesi: utilizzare PowerShell di Office 365 per configurare le proprietà di uno o più account utente nel tenant di Office 365.'
ms.openlocfilehash: 5748bd382357168e4184754fb49fb7304e2d2474
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004719"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="37b3a-103">Configurare le proprietà degli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="37b3a-103">Configure user account properties with Office 365 PowerShell</span></span>

<span data-ttu-id="37b3a-104">Anche se è possibile utilizzare l'interfaccia di amministrazione di Microsoft 365 per configurare le proprietà degli account utente del tenant di Office 365, è anche possibile utilizzare PowerShell per Office 365 e fare alcuni elementi che non possono essere configurati dal centro di amministrazione.</span><span class="sxs-lookup"><span data-stu-id="37b3a-104">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="37b3a-105">Usare il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="37b3a-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="37b3a-106">Per configurare le proprietà degli account utente con il modulo Azure Active Directory PowerShell per Graph, utilizzare il cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) e specificare le proprietà da impostare o modificare.</span><span class="sxs-lookup"><span data-stu-id="37b3a-106">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="37b3a-107">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="37b3a-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="37b3a-108">Modificare le proprietà per un account utente specifico</span><span class="sxs-lookup"><span data-stu-id="37b3a-108">Change properties for a specific user account</span></span>

<span data-ttu-id="37b3a-p101">Identificare l'account con il parametro **-ObjectID** e impostare o modificare proprietà specifiche con ulteriori parametri. Ecco un elenco dei parametri più comuni.</span><span class="sxs-lookup"><span data-stu-id="37b3a-p101">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="37b3a-111">-Department "\<nome reparto>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-111">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="37b3a-112">-DisplayName "\<nome utente completo>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-112">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="37b3a-113">-FacsimilieTelephoneNumber "\<numero fax>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-113">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="37b3a-114">-GivenName "\<nome utente>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-114">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="37b3a-115">-Surname "\<cognome utente>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-115">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="37b3a-116">-Mobile "\<numero cellulare>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-116">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="37b3a-117">-JobTitle "\<posizione professionale>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-117">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="37b3a-118">-PreferredLanguage "\<lingua>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-118">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="37b3a-119">-StreetAddress "\<indirizzo>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-119">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="37b3a-120">-City "\<nome città>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-120">-City "\<city name>"</span></span>
    
- <span data-ttu-id="37b3a-121">-State "\<nome stato>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-121">-State "\<state name>"</span></span>
    
- <span data-ttu-id="37b3a-122">-PostalCode "\<CAP>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-122">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="37b3a-123">-Country "\<nome paese>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-123">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="37b3a-124">-TelephoneNumber "\<numero di telefono di ufficio>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-124">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="37b3a-125">-UsageLocation "\<codice paese o area geografica a 2 caratteri>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-125">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="37b3a-126">Si tratta del codice paese o area geografica a due lettere ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="37b3a-126">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="37b3a-127">Per ulteriori parametri, vedere [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="37b3a-127">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="37b3a-128">Per visualizzare il nome principale degli utenti per gli account utente, eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="37b3a-128">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="37b3a-129">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="37b3a-129">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="37b3a-130">Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="37b3a-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="37b3a-131">Ordinare l'elenco dei nomi delle entità utente in ordine alfabetico ( **Sort userPrincipalName** ) e inviarlo al comando **|** successivo ().</span><span class="sxs-lookup"><span data-stu-id="37b3a-131">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="37b3a-132">Visualizzare solo la proprietà del nome dell'entità utente per ogni account ( **selezionare userPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="37b3a-132">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>

- <span data-ttu-id="37b3a-133">Visualizzare gli elementi in una schermata alla volta ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="37b3a-133">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="37b3a-p102">Con questo comando vengono elencati tutti gli account. Se si desidera visualizzare il nome principale dell'utente di un account in base al nome visualizzato (nome e cognome), inserire la variabile **$userName** sotto (rimuovendo i caratteri \< e >), quindi eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="37b3a-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="37b3a-136">Questo esempio permette di visualizzare il nome dell’entità utente per l’account utente con nome visualizzato Caleb Sillis.</span><span class="sxs-lookup"><span data-stu-id="37b3a-136">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="37b3a-p103">Utilizzando una variabile **$upn**, è possibile apportare modifiche ai singoli account in base al nome visualizzato. Ecco un esempio di impostazione della posizione di utilizzo di Belinda Newman in Francia, specificando il nome visualizzato anziché il nome principale dell'utente:</span><span class="sxs-lookup"><span data-stu-id="37b3a-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="37b3a-139">Modificare le proprietà per tutti gli account utente</span><span class="sxs-lookup"><span data-stu-id="37b3a-139">Change properties for all user accounts</span></span>

<span data-ttu-id="37b3a-p104">Per modificare le proprietà per tutti gli utenti, è possibile utilizzare la combinazione di cmdlet **Get-AzureADUser** e **Set-AzureADUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti in Francia:</span><span class="sxs-lookup"><span data-stu-id="37b3a-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="37b3a-142">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="37b3a-142">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="37b3a-143">Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="37b3a-143">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="37b3a-144">Impostare la posizione dell'utente in Francia ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="37b3a-144">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="37b3a-145">Modificare le proprietà per un set specifico di account utente</span><span class="sxs-lookup"><span data-stu-id="37b3a-145">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="37b3a-p105">Per modificare le proprietà per un set specifico di account utente, è possibile utilizzare la combinazione di cmdlet **Get-AzureADUser**, **Where** e **Set-AzureADUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti del reparto Contabilità in Francia:</span><span class="sxs-lookup"><span data-stu-id="37b3a-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="37b3a-148">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="37b3a-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="37b3a-149">Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="37b3a-149">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="37b3a-150">Individuare tutti gli account utente con la proprietà Department impostata su "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) e inviare le informazioni risultanti al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="37b3a-150">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="37b3a-151">Impostare la posizione dell'utente in Francia ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="37b3a-151">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="37b3a-152">Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="37b3a-152">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="37b3a-153">Per configurare le proprietà degli account utente con il modulo di Microsoft Azure Active Directory per Windows PowerShell, utilizzare il cmdlet **set-MsolUser** e specificare le proprietà da impostare o modificare.</span><span class="sxs-lookup"><span data-stu-id="37b3a-153">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the **Set-MsolUser** cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="37b3a-154">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="37b3a-154">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="37b3a-155">PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per Windows PowerShell e i cmdlet con **MSOL** all'interno del nome.</span><span class="sxs-lookup"><span data-stu-id="37b3a-155">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="37b3a-156">Per continuare a usare i cmdlet, è necessario eseguirli in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="37b3a-156">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="37b3a-157">Modificare le proprietà per un account utente specifico</span><span class="sxs-lookup"><span data-stu-id="37b3a-157">Change properties for a specific user account</span></span>

<span data-ttu-id="37b3a-158">Per configurare le proprietà per un account utente specifico, utilizzare il cmdlet [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) e specificare le proprietà da impostare o modificare.</span><span class="sxs-lookup"><span data-stu-id="37b3a-158">To configure properties for a specific user account, you use the [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="37b3a-p107">Identificare l'account con il parametro **-UserPrincipalName** e impostare o modificare proprietà specifiche con ulteriori parametri. Ecco un elenco dei parametri più comuni.</span><span class="sxs-lookup"><span data-stu-id="37b3a-p107">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="37b3a-161">-City "\<nome città>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-161">-City "\<city name>"</span></span>
    
- <span data-ttu-id="37b3a-162">-Country "\<nome paese>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-162">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="37b3a-163">-Department "\<nome reparto>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-163">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="37b3a-164">-DisplayName "\<nome utente completo>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-164">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="37b3a-165">-Fax "\<numero fax>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-165">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="37b3a-166">-FirstName "\<nome utente>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-166">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="37b3a-167">-LastName "\<cognome utente>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-167">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="37b3a-168">-MobilePhone "\<numero cellulare>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-168">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="37b3a-169">-Office "\<ubicazione ufficio>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-169">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="37b3a-170">-PhoneNumber "\<numero di telefono di ufficio>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-170">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="37b3a-171">-PostalCode "\<CAP>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-171">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="37b3a-172">-PreferredLanguage "\<lingua>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="37b3a-173">-State "\<nome stato>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-173">-State "\<state name>"</span></span>
    
- <span data-ttu-id="37b3a-174">-StreetAddress "\<indirizzo>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-174">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="37b3a-175">-Title "\<nome titolo>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-175">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="37b3a-176">-UsageLocation "\<codice paese o area geografica a 2 caratteri>"</span><span class="sxs-lookup"><span data-stu-id="37b3a-176">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="37b3a-177">Si tratta del codice paese o area geografica a due lettere ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="37b3a-177">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="37b3a-178">Per ulteriori parametri, vedere [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="37b3a-178">See [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) for additional parameters.</span></span>

<span data-ttu-id="37b3a-179">Per visualizzare i nomi principali di tutti gli utenti, eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="37b3a-179">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="37b3a-180">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="37b3a-180">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="37b3a-181">Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="37b3a-181">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="37b3a-182">Ordinare l'elenco dei nomi delle entità utente in ordine alfabetico ( **Sort userPrincipalName** ) e inviarlo al comando **|** successivo ().</span><span class="sxs-lookup"><span data-stu-id="37b3a-182">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="37b3a-183">Visualizzare solo la proprietà del nome dell'entità utente per ogni account ( **selezionare userPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="37b3a-183">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="37b3a-184">Visualizzare gli elementi in una schermata alla volta ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="37b3a-184">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="37b3a-p108">Con questo comando vengono elencati tutti gli account. Se si desidera visualizzare il nome principale dell'utente di un account in base al nome visualizzato (nome e cognome), inserire la variabile **$userName** sotto (rimuovendo i caratteri \< e >), quindi eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="37b3a-p108">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="37b3a-187">Questo esempio permette di visualizzare il nome principale dell'utente denominato Caleb Sillis.</span><span class="sxs-lookup"><span data-stu-id="37b3a-187">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="37b3a-p109">Utilizzando una variabile **$upn**, è possibile apportare modifiche ai singoli account in base al nome visualizzato. Ecco un esempio di impostazione della posizione di utilizzo di Belinda Newman in Francia, specificando il nome visualizzato anziché il nome principale dell'utente:</span><span class="sxs-lookup"><span data-stu-id="37b3a-p109">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="37b3a-190">Modificare le proprietà per tutti gli account utente</span><span class="sxs-lookup"><span data-stu-id="37b3a-190">Change properties for all user accounts</span></span>

<span data-ttu-id="37b3a-p110">Per modificare le proprietà per tutti gli utenti, è possibile utilizzare la combinazione di cmdlet **Get-MsolUser** e **Set-MsolUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti in Francia:</span><span class="sxs-lookup"><span data-stu-id="37b3a-p110">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="37b3a-193">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="37b3a-193">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="37b3a-194">Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="37b3a-194">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="37b3a-195">Impostare la posizione dell'utente in Francia ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="37b3a-195">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="37b3a-196">Modificare le proprietà per un set specifico di account utente</span><span class="sxs-lookup"><span data-stu-id="37b3a-196">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="37b3a-197">Per modificare le proprietà di un determinato set di account utente, è possibile utilizzare la combinazione dei cmdlet **Get-MsolUser**, **where**e **set-MsolUser** .</span><span class="sxs-lookup"><span data-stu-id="37b3a-197">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="37b3a-198">Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti del reparto Contabilità in Francia:</span><span class="sxs-lookup"><span data-stu-id="37b3a-198">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="37b3a-199">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="37b3a-199">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="37b3a-200">Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="37b3a-200">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="37b3a-201">Individuare tutti gli account utente con la proprietà Department impostata su "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) e inviare le informazioni risultanti al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="37b3a-201">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="37b3a-202">Impostare la posizione dell'utente in Francia ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="37b3a-202">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="37b3a-203">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="37b3a-203">See also</span></span>

[<span data-ttu-id="37b3a-204">Gestire gli account utente, le licenze e i gruppi con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="37b3a-204">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="37b3a-205">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="37b3a-205">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="37b3a-206">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="37b3a-206">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
