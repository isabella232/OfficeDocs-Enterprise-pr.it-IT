---
title: "Configurare le proprietà degli account utente con Office 365 PowerShell"
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
- DecEntMigration
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- apr17entnews
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "Sintesi: utilizzare PowerShell di Office 365 per configurare le proprietà di uno o più account utente nel tenant di Office 365."
ms.openlocfilehash: d9e817530f3b1554cb757720f01afec5ed3b63ef
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="d9697-103">Configurare le proprietà degli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d9697-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="d9697-104">**Riepilogo:** Utilizzare Office 365 PowerShell per configurare le proprietà delle singole o più account utente in Office 365 tenant.</span><span class="sxs-lookup"><span data-stu-id="d9697-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="d9697-105">Sebbene sia possibile utilizzare l'interfaccia di amministrazione di Office 365 per configurare le proprietà degli account utente del tenant di Office 365, è possibile utilizzare anche PowerShell di Office 365 ed eseguire delle operazioni che non sono possibili nell'interfaccia di amministrazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="d9697-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="d9697-106">Informazioni preliminari</span><span class="sxs-lookup"><span data-stu-id="d9697-106">Before you begin</span></span>

<span data-ttu-id="d9697-p101">Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="d9697-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="d9697-109">Modificare le proprietà per un account utente specifico</span><span class="sxs-lookup"><span data-stu-id="d9697-109">Change properties for a specific user account</span></span>

<span data-ttu-id="d9697-p102">Per configurare le proprietà per un account utente specifico, utilizzare il cmdlet [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) e specificare le proprietà da impostare o modificare. In questo esempio viene modificata la posizione di utilizzo di Belinda Newman in Francia:</span><span class="sxs-lookup"><span data-stu-id="d9697-p102">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change. This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="d9697-p103">Identificare l'account con il parametro **-UserPrincipalName** e impostare o modificare proprietà specifiche con ulteriori parametri. Ecco un elenco dei parametri più comuni.</span><span class="sxs-lookup"><span data-stu-id="d9697-p103">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="d9697-114">-Città "\<città >"</span><span class="sxs-lookup"><span data-stu-id="d9697-114">-City "\<city name>"</span></span>
    
- <span data-ttu-id="d9697-115">-Paese "\<nome del paese >"</span><span class="sxs-lookup"><span data-stu-id="d9697-115">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="d9697-116">-Reparto "\<Nome reparto >"</span><span class="sxs-lookup"><span data-stu-id="d9697-116">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="d9697-117">-DisplayName "\<nome utente completo >"</span><span class="sxs-lookup"><span data-stu-id="d9697-117">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="d9697-118">-Fax "\<numero di fax >"</span><span class="sxs-lookup"><span data-stu-id="d9697-118">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="d9697-119">-FirstName "\<nome utente >"</span><span class="sxs-lookup"><span data-stu-id="d9697-119">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="d9697-120">-LastName "\<cognome utente >"</span><span class="sxs-lookup"><span data-stu-id="d9697-120">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="d9697-121">-MobilePhone "\<numero di cellulare >"</span><span class="sxs-lookup"><span data-stu-id="d9697-121">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="d9697-122">-Office "\<sede >"</span><span class="sxs-lookup"><span data-stu-id="d9697-122">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="d9697-123">-PhoneNumber "\<il numero di telefono di office >"</span><span class="sxs-lookup"><span data-stu-id="d9697-123">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="d9697-124">-PostalCode "\<CAP >"</span><span class="sxs-lookup"><span data-stu-id="d9697-124">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="d9697-125">-PreferredLanguage "\<language >"</span><span class="sxs-lookup"><span data-stu-id="d9697-125">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="d9697-126">-Stato "\<nome stato >"</span><span class="sxs-lookup"><span data-stu-id="d9697-126">-State "\<state name>"</span></span>
    
- <span data-ttu-id="d9697-127">-StreetAddress "\<indirizzo >"</span><span class="sxs-lookup"><span data-stu-id="d9697-127">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="d9697-128">-Title "\<nome titolo >"</span><span class="sxs-lookup"><span data-stu-id="d9697-128">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="d9697-129">-UsageLocation "\<codice del paese carattere 2 >"</span><span class="sxs-lookup"><span data-stu-id="d9697-129">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="d9697-130">Si tratta del codice paese o area geografica a due lettere ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="d9697-130">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="d9697-131">Per ulteriori parametri, vedere [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).</span><span class="sxs-lookup"><span data-stu-id="d9697-131">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="d9697-132">Per visualizzare i nomi principali di tutti gli utenti, eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="d9697-132">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="d9697-133">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="d9697-133">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d9697-134">Ottenere tutte le informazioni sugli account utente ( **Get-MsolUser** ) e inviarlo al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-134">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d9697-135">Ordinare l'elenco dei nomi dell'entità utente in ordine alfabetico ( **Oggetto Sort UserPrincipalName** ) e inviarlo al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-135">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d9697-136">Visualizzare solo la proprietà del nome principale degli utenti per ogni account ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-136">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="d9697-137">Visualizzare gli elementi in una schermata alla volta ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-137">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="d9697-p104">Questo comando vengono elencati tutti gli account di posta. Se si desidera venga visualizzato il nome dell'entità utente di un account basato su una visualizzazione personalizzata nome (nome e cognome), immettere la variabile **$userName** riportata di seguito (rimuovere il \< e > caratteri), e quindi eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="d9697-p104">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d9697-140">Questo esempio permette di visualizzare il nome principale dell'utente denominato Caleb Sillis.</span><span class="sxs-lookup"><span data-stu-id="d9697-140">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d9697-p105">Utilizzando una variabile **$upn**, è possibile apportare modifiche ai singoli account in base al nome visualizzato. Ecco un esempio di impostazione della posizione di utilizzo di Belinda Newman in Francia, specificando il nome visualizzato anziché il nome principale dell'utente:</span><span class="sxs-lookup"><span data-stu-id="d9697-p105">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="d9697-143">Modificare le proprietà per tutti gli account utente</span><span class="sxs-lookup"><span data-stu-id="d9697-143">Change properties for all user accounts</span></span>

<span data-ttu-id="d9697-p106">Per modificare le proprietà per tutti gli utenti, è possibile utilizzare la combinazione di cmdlet **Get-MsolUser** e **Set-MsolUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti in Francia:</span><span class="sxs-lookup"><span data-stu-id="d9697-p106">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="d9697-146">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="d9697-146">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d9697-147">Ottenere tutte le informazioni sugli account utente ( **Get-MsolUser** ) e inviarlo al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-147">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d9697-148">Impostare la posizione dell'utente in Francia ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-148">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="d9697-149">Modificare le proprietà per un set specifico di account utente</span><span class="sxs-lookup"><span data-stu-id="d9697-149">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="d9697-p107">Per modificare le proprietà per un set specifico di account utente, è possibile utilizzare la combinazione di cmdlet **Get-MsolUser**, **Where-Object** e **Set-MsolUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti del reparto Contabilità in Francia:</span><span class="sxs-lookup"><span data-stu-id="d9697-p107">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="d9697-152">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="d9697-152">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d9697-153">Ottenere tutte le informazioni sugli account utente ( **Get-MsolUser** ) e inviarlo al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-153">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d9697-154">Trovare tutti gli account utente che il reparto proprietà è impostata su "Contabilità" ( **Where-Object {$_. Reparto - eq "Contabilità"}** ) e inviare le informazioni ottenute con il comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-154">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d9697-155">Impostare la posizione dell'utente in Francia ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-155">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
- <span data-ttu-id="d9697-156">Visualizzare gli elementi in una schermata alla volta ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-156">Display them one screen at a time ( **More** ).</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a><span data-ttu-id="d9697-157">Utilizzare il modulo Azure Active Directory V2 PowerShell per configurare le proprietà di un account utente</span><span class="sxs-lookup"><span data-stu-id="d9697-157">Use the Azure Active Directory V2 PowerShell module to configure user account properties</span></span>

<span data-ttu-id="d9697-p108">Per configurare le proprietà degli account utente con il modulo di Azure Active Directory V2 PowerShell, utilizzare il cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) e specificare le proprietà per impostare o modificare. Tuttavia, è innanzitutto necessario connettersi alla sottoscrizione. Per ulteriori informazioni, vedere [Connect con il modulo di Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="d9697-p108">To configure properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change. But first, you must connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="d9697-161">Modificare le proprietà per un account utente specifico</span><span class="sxs-lookup"><span data-stu-id="d9697-161">Change properties for a specific user account</span></span>

<span data-ttu-id="d9697-162">In questo esempio viene modificata la posizione di utilizzo di Belinda Newman in Francia:</span><span class="sxs-lookup"><span data-stu-id="d9697-162">This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="d9697-p109">Identificare l'account con il parametro **-ObjectID** e impostare o modificare proprietà specifiche con ulteriori parametri. Ecco un elenco dei parametri più comuni.</span><span class="sxs-lookup"><span data-stu-id="d9697-p109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="d9697-165">-Reparto "\<Nome reparto >"</span><span class="sxs-lookup"><span data-stu-id="d9697-165">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="d9697-166">-DisplayName "\<nome utente completo >"</span><span class="sxs-lookup"><span data-stu-id="d9697-166">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="d9697-167">-FacsimilieTelephoneNumber "\<numero di fax >"</span><span class="sxs-lookup"><span data-stu-id="d9697-167">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="d9697-168">-GivenName "\<nome utente >"</span><span class="sxs-lookup"><span data-stu-id="d9697-168">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="d9697-169">-Cognome "\<cognome utente >"</span><span class="sxs-lookup"><span data-stu-id="d9697-169">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="d9697-170">-Per dispositivi mobili "\<numero di cellulare >"</span><span class="sxs-lookup"><span data-stu-id="d9697-170">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="d9697-171">-JobTitle "\<posizione >"</span><span class="sxs-lookup"><span data-stu-id="d9697-171">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="d9697-172">-PreferredLanguage "\<language >"</span><span class="sxs-lookup"><span data-stu-id="d9697-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="d9697-173">-StreetAddress "\<indirizzo >"</span><span class="sxs-lookup"><span data-stu-id="d9697-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="d9697-174">-Città "\<città >"</span><span class="sxs-lookup"><span data-stu-id="d9697-174">-City "\<city name>"</span></span>
    
- <span data-ttu-id="d9697-175">-Stato "\<nome stato >"</span><span class="sxs-lookup"><span data-stu-id="d9697-175">-State "\<state name>"</span></span>
    
- <span data-ttu-id="d9697-176">-PostalCode "\<CAP >"</span><span class="sxs-lookup"><span data-stu-id="d9697-176">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="d9697-177">-Paese "\<nome del paese >"</span><span class="sxs-lookup"><span data-stu-id="d9697-177">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="d9697-178">-TelephoneNumber "\<il numero di telefono di office >"</span><span class="sxs-lookup"><span data-stu-id="d9697-178">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="d9697-179">-UsageLocation "\<codice del paese carattere 2 >"</span><span class="sxs-lookup"><span data-stu-id="d9697-179">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="d9697-180">Si tratta del codice paese o area geografica a due lettere ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="d9697-180">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="d9697-181">Per ulteriori parametri, vedere [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="d9697-181">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="d9697-182">Per visualizzare il nome dell'entità utente per gli account utente, eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="d9697-182">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="d9697-183">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="d9697-183">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d9697-184">Ottenere tutte le informazioni sugli account utente ( **Get-AzureADUser** ) e inviarlo al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-184">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d9697-185">Ordinare l'elenco dei nomi dell'entità utente in ordine alfabetico ( **Oggetto Sort UserPrincipalName** ) e inviarlo al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-185">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d9697-186">Visualizzare solo la proprietà del nome principale degli utenti per ogni account ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-186">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="d9697-187">Visualizzare gli elementi in una schermata alla volta ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-187">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="d9697-p110">Questo comando vengono elencati tutti gli account di posta. Se si desidera venga visualizzato il nome dell'entità utente di un account basato su una visualizzazione personalizzata nome (nome e cognome), immettere la variabile **$userName** riportata di seguito (rimuovere il \< e > caratteri), e quindi eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="d9697-p110">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d9697-190">Questo esempio permette di visualizzare il nome principale dell'utente denominato Caleb Sillis.</span><span class="sxs-lookup"><span data-stu-id="d9697-190">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d9697-p111">Utilizzando una variabile **$upn**, è possibile apportare modifiche ai singoli account in base al nome visualizzato. Ecco un esempio di impostazione della posizione di utilizzo di Belinda Newman in Francia, specificando il nome visualizzato anziché il nome principale dell'utente:</span><span class="sxs-lookup"><span data-stu-id="d9697-p111">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="d9697-193">Modificare le proprietà per tutti gli account utente</span><span class="sxs-lookup"><span data-stu-id="d9697-193">Change properties for all user accounts</span></span>

<span data-ttu-id="d9697-p112">Per modificare le proprietà per tutti gli utenti, è possibile utilizzare la combinazione di cmdlet **Get-AzureADUser** e **Set-AzureADUser**. Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti in Francia:</span><span class="sxs-lookup"><span data-stu-id="d9697-p112">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="d9697-196">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="d9697-196">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d9697-197">Ottenere tutte le informazioni sugli account utente ( **Get-AzureADUser** ) e inviarlo al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-197">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d9697-198">Impostare la posizione dell'utente in Francia ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-198">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="d9697-199">Modificare le proprietà per un set specifico di account utente</span><span class="sxs-lookup"><span data-stu-id="d9697-199">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="d9697-p113">Per modificare le proprietà per un set specifico di account utente, è possibile utilizzare la combinazione dei cmdlet **Get-AzureADUser**, **dove**e **Set-AzureADUser** . Nell'esempio seguente viene modificata la posizione di utilizzo per tutti gli utenti nel reparto contabilità in Francia:</span><span class="sxs-lookup"><span data-stu-id="d9697-p113">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="d9697-202">Questo comando indica a PowerShell di Office 365 di:</span><span class="sxs-lookup"><span data-stu-id="d9697-202">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d9697-203">Ottenere tutte le informazioni sugli account utente ( **Get-AzureADUser** ) e inviarlo al comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-203">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d9697-204">Trovare tutti gli account utente la cui reparto proprietà è impostata su "Contabilità" ( **dove {$_. Reparto - eq "Contabilità"}** ) e inviare le informazioni ottenute con il comando successivo ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-204">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d9697-205">Impostare la posizione dell'utente in Francia ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="d9697-205">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="d9697-206">See also</span><span class="sxs-lookup"><span data-stu-id="d9697-206">See also</span></span>

#### 

[<span data-ttu-id="d9697-207">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d9697-207">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="d9697-208">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="d9697-208">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d9697-209">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="d9697-209">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

