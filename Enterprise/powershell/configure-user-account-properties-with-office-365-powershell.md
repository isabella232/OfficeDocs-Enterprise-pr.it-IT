---
title: Configurare le proprietà degli account utente con Office 365 PowerShell
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Sintesi: utilizzare PowerShell di Office 365 per configurare le proprietà di uno o più account utente nel tenant di Office 365.'
ms.openlocfilehash: 53a99c33dcebebc87e12a468d56e5460b8a0c111
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782606"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="348b4-103">Configurare le proprietà degli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="348b4-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="348b4-104">**Sintesi:** Utilizzare PowerShell di Office 365 per configurare le proprietà di uno o più account utente nel tenant di Office 365.</span><span class="sxs-lookup"><span data-stu-id="348b4-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="348b4-105">Anche se è possibile utilizzare l'interfaccia di amministrazione di Microsoft 365 per configurare le proprietà degli account utente del tenant di Office 365, è anche possibile utilizzare PowerShell per Office 365 e fare alcuni elementi che non possono essere configurati dal centro di amministrazione.</span><span class="sxs-lookup"><span data-stu-id="348b4-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="348b4-106">Usare il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="348b4-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="348b4-107">Per configurare le proprietà degli account utente con il modulo Azure Active Directory PowerShell per Graph, utilizzare il cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) e specificare le proprietà da impostare o modificare.</span><span class="sxs-lookup"><span data-stu-id="348b4-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="348b4-108">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="348b4-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="348b4-109">Modificare le proprietà per un account utente specifico</span><span class="sxs-lookup"><span data-stu-id="348b4-109">Change properties for a specific user account</span></span>

<span data-ttu-id="348b4-p101">Identificare l'account con il parametro **-ObjectID** e impostare o modificare proprietà specifiche con ulteriori parametri. Ecco un elenco dei parametri più comuni.</span><span class="sxs-lookup"><span data-stu-id="348b4-p101">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="348b4-112">-Department "\<nome reparto>"</span><span class="sxs-lookup"><span data-stu-id="348b4-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="348b4-113">-DisplayName "\<nome utente completo>"</span><span class="sxs-lookup"><span data-stu-id="348b4-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="348b4-114">-FacsimilieTelephoneNumber "\<numero fax>"</span><span class="sxs-lookup"><span data-stu-id="348b4-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="348b4-115">-GivenName "\<nome utente>"</span><span class="sxs-lookup"><span data-stu-id="348b4-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="348b4-116">-Surname "\<cognome utente>"</span><span class="sxs-lookup"><span data-stu-id="348b4-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="348b4-117">-Mobile "\<numero cellulare>"</span><span class="sxs-lookup"><span data-stu-id="348b4-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="348b4-118">-JobTitle "\<posizione professionale>"</span><span class="sxs-lookup"><span data-stu-id="348b4-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="348b4-119">-PreferredLanguage "\<lingua>"</span><span class="sxs-lookup"><span data-stu-id="348b4-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="348b4-120">-StreetAddress "\<indirizzo>"</span><span class="sxs-lookup"><span data-stu-id="348b4-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="348b4-121">-City "\<nome città>"</span><span class="sxs-lookup"><span data-stu-id="348b4-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="348b4-122">-State "\<nome stato>"</span><span class="sxs-lookup"><span data-stu-id="348b4-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="348b4-123">-PostalCode "\<CAP>"</span><span class="sxs-lookup"><span data-stu-id="348b4-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="348b4-124">-Country "\<nome paese>"</span><span class="sxs-lookup"><span data-stu-id="348b4-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="348b4-125">-TelephoneNumber "\<numero di telefono di ufficio>"</span><span class="sxs-lookup"><span data-stu-id="348b4-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="348b4-126">-UsageLocation "\<codice paese o area geografica a 2 caratteri>"</span><span class="sxs-lookup"><span data-stu-id="348b4-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="348b4-127">Si tratta del codice paese o area geografica a due lettere ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="348b4-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="348b4-128">Per ulteriori parametri, vedere [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="348b4-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="348b4-129">Per visualizzare il nome principale degli utenti per gli account utente, eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="348b4-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="348b4-130">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="348b4-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="348b4-131">Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="348b4-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="348b4-132">Elencare i nomi principali degli utenti in ordine alfabetico ( **Sort-Object UserPrincipalName** ) e inviarli al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="348b4-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="348b4-133">Visualizzare solo la proprietà del nome principale degli utenti per ogni account ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="348b4-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="348b4-134">Visualizzare gli elementi in una schermata alla volta ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="348b4-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="348b4-p102">Con questo comando vengono elencati tutti gli account. Se si desidera visualizzare il nome principale dell'utente di un account in base al nome visualizzato (nome e cognome), inserire la variabile **$userName** sotto (rimuovendo i caratteri \< e >), quindi eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="348b4-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="348b4-137">Questo esempio permette di visualizzare il nome dell’entità utente per l’account utente con nome visualizzato Caleb Sillis.</span><span class="sxs-lookup"><span data-stu-id="348b4-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="348b4-p103">Utilizzando una variabile **$upn**, è possibile apportare modifiche ai singoli account in base al nome visualizzato. Ecco un esempio di impostazione della posizione di utilizzo di Belinda Newman in Francia, specificando il nome visualizzato anziché il nome principale dell'utente:</span><span class="sxs-lookup"><span data-stu-id="348b4-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="348b4-140">Modificare le proprietà per tutti gli account utente</span><span class="sxs-lookup"><span data-stu-id="348b4-140">Change properties for all user accounts</span></span>

<span data-ttu-id="348b4-p104">Per modificare le proprietà per tutti gli utenti, è possibile utilizzare la combinazione di cmdlet **Get-AzureADUser** e **Set-AzureADUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti in Francia:</span><span class="sxs-lookup"><span data-stu-id="348b4-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="348b4-143">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="348b4-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="348b4-144">Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="348b4-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="348b4-145">Impostare la posizione dell'utente in Francia ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="348b4-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="348b4-146">Modificare le proprietà per un set specifico di account utente</span><span class="sxs-lookup"><span data-stu-id="348b4-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="348b4-p105">Per modificare le proprietà per un set specifico di account utente, è possibile utilizzare la combinazione di cmdlet **Get-AzureADUser**, **Where** e **Set-AzureADUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti del reparto Contabilità in Francia:</span><span class="sxs-lookup"><span data-stu-id="348b4-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="348b4-149">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="348b4-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="348b4-150">Accedere a tutte le informazioni degli account utente ( **Get-AzureADUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="348b4-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="348b4-151">Individuare tutti gli account utente con la proprietà Department impostata su "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) e inviare le informazioni risultanti al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="348b4-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="348b4-152">Impostare la posizione dell'utente in Francia ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="348b4-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="348b4-153">Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="348b4-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="348b4-154">Per configurare le proprietà degli account utente con il modulo di Microsoft Azure Active Directory per Windows PowerShell, utilizzare il cmdlet Set-MsolUser e specificare le proprietà da impostare o modificare.</span><span class="sxs-lookup"><span data-stu-id="348b4-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="348b4-155">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="348b4-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="348b4-156">Modificare le proprietà per un account utente specifico</span><span class="sxs-lookup"><span data-stu-id="348b4-156">Change properties for a specific user account</span></span>

<span data-ttu-id="348b4-157">Per configurare le proprietà per un account utente specifico, utilizzare il cmdlet [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) e specificare le proprietà da impostare o modificare.</span><span class="sxs-lookup"><span data-stu-id="348b4-157">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="348b4-p106">Identificare l'account con il parametro **-UserPrincipalName** e impostare o modificare proprietà specifiche con ulteriori parametri. Ecco un elenco dei parametri più comuni.</span><span class="sxs-lookup"><span data-stu-id="348b4-p106">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="348b4-160">-City "\<nome città>"</span><span class="sxs-lookup"><span data-stu-id="348b4-160">-City "\<city name>"</span></span>
    
- <span data-ttu-id="348b4-161">-Country "\<nome paese>"</span><span class="sxs-lookup"><span data-stu-id="348b4-161">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="348b4-162">-Department "\<nome reparto>"</span><span class="sxs-lookup"><span data-stu-id="348b4-162">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="348b4-163">-DisplayName "\<nome utente completo>"</span><span class="sxs-lookup"><span data-stu-id="348b4-163">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="348b4-164">-Fax "\<numero fax>"</span><span class="sxs-lookup"><span data-stu-id="348b4-164">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="348b4-165">-FirstName "\<nome utente>"</span><span class="sxs-lookup"><span data-stu-id="348b4-165">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="348b4-166">-LastName "\<cognome utente>"</span><span class="sxs-lookup"><span data-stu-id="348b4-166">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="348b4-167">-MobilePhone "\<numero cellulare>"</span><span class="sxs-lookup"><span data-stu-id="348b4-167">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="348b4-168">-Office "\<ubicazione ufficio>"</span><span class="sxs-lookup"><span data-stu-id="348b4-168">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="348b4-169">-PhoneNumber "\<numero di telefono di ufficio>"</span><span class="sxs-lookup"><span data-stu-id="348b4-169">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="348b4-170">-PostalCode "\<CAP>"</span><span class="sxs-lookup"><span data-stu-id="348b4-170">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="348b4-171">-PreferredLanguage "\<lingua>"</span><span class="sxs-lookup"><span data-stu-id="348b4-171">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="348b4-172">-State "\<nome stato>"</span><span class="sxs-lookup"><span data-stu-id="348b4-172">-State "\<state name>"</span></span>
    
- <span data-ttu-id="348b4-173">-StreetAddress "\<indirizzo>"</span><span class="sxs-lookup"><span data-stu-id="348b4-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="348b4-174">-Title "\<nome titolo>"</span><span class="sxs-lookup"><span data-stu-id="348b4-174">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="348b4-175">-UsageLocation "\<codice paese o area geografica a 2 caratteri>"</span><span class="sxs-lookup"><span data-stu-id="348b4-175">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="348b4-176">Si tratta del codice paese o area geografica a due lettere ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="348b4-176">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="348b4-177">Per ulteriori parametri, vedere [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).</span><span class="sxs-lookup"><span data-stu-id="348b4-177">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="348b4-178">Per visualizzare i nomi principali di tutti gli utenti, eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="348b4-178">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="348b4-179">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="348b4-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="348b4-180">Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="348b4-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="348b4-181">Elencare i nomi principali degli utenti in ordine alfabetico ( **Sort-Object UserPrincipalName** ) e inviarli al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="348b4-181">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="348b4-182">Visualizzare solo la proprietà del nome principale degli utenti per ogni account ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="348b4-182">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="348b4-183">Visualizzare gli elementi in una schermata alla volta ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="348b4-183">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="348b4-p107">Con questo comando vengono elencati tutti gli account. Se si desidera visualizzare il nome principale dell'utente di un account in base al nome visualizzato (nome e cognome), inserire la variabile **$userName** sotto (rimuovendo i caratteri \< e >), quindi eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="348b4-p107">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="348b4-186">Questo esempio permette di visualizzare il nome principale dell'utente denominato Caleb Sillis.</span><span class="sxs-lookup"><span data-stu-id="348b4-186">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="348b4-p108">Utilizzando una variabile **$upn**, è possibile apportare modifiche ai singoli account in base al nome visualizzato. Ecco un esempio di impostazione della posizione di utilizzo di Belinda Newman in Francia, specificando il nome visualizzato anziché il nome principale dell'utente:</span><span class="sxs-lookup"><span data-stu-id="348b4-p108">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="348b4-189">Modificare le proprietà per tutti gli account utente</span><span class="sxs-lookup"><span data-stu-id="348b4-189">Change properties for all user accounts</span></span>

<span data-ttu-id="348b4-p109">Per modificare le proprietà per tutti gli utenti, è possibile utilizzare la combinazione di cmdlet **Get-MsolUser** e **Set-MsolUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti in Francia:</span><span class="sxs-lookup"><span data-stu-id="348b4-p109">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="348b4-192">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="348b4-192">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="348b4-193">Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="348b4-193">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="348b4-194">Impostare la posizione dell'utente in Francia ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="348b4-194">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="348b4-195">Modificare le proprietà per un set specifico di account utente</span><span class="sxs-lookup"><span data-stu-id="348b4-195">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="348b4-p110">Per modificare le proprietà per un set specifico di account utente, è possibile utilizzare la combinazione di cmdlet **Get-MsolUser**, **Where-Object** e **Set-MsolUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti del reparto Contabilità in Francia:</span><span class="sxs-lookup"><span data-stu-id="348b4-p110">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="348b4-198">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="348b4-198">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="348b4-199">Accedere a tutte le informazioni degli account utente ( **Get-MsolUser** ) e inviarle al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="348b4-199">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="348b4-200">Individuare tutti gli account utente con la proprietà Department impostata su "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) e inviare le informazioni risultanti al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="348b4-200">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="348b4-201">Impostare la posizione dell'utente in Francia ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="348b4-201">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="348b4-202">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="348b4-202">See also</span></span>

[<span data-ttu-id="348b4-203">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="348b4-203">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="348b4-204">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="348b4-204">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="348b4-205">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="348b4-205">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
