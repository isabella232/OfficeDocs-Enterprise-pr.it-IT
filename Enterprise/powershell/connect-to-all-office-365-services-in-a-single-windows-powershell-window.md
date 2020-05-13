---
title: Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: "Riepilogo: connettere Windows PowerShell a tutti i servizi di Office 365 in un'unica finestra di Windows PowerShell."
ms.openlocfilehash: 47fd2be814b446cf12b136e359cdadc9374a7ab6
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/12/2020
ms.locfileid: "44208807"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="d7cef-103">Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7cef-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

<span data-ttu-id="d7cef-104">Quando si utilizza PowerShell per gestire Office 365, è possibile che siano disponibili fino a cinque sessioni di Windows PowerShell diverse contemporaneamente corrispondenti all'interfaccia di amministrazione di Microsoft 365, SharePoint Online, Exchange Online, Skype for business online, Microsoft teams e il Centro sicurezza e &amp; conformità.</span><span class="sxs-lookup"><span data-stu-id="d7cef-104">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="d7cef-105">Con cinque diversi metodi di connessione in sessioni di Windows PowerShell separate, il desktop potrebbe essere simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="d7cef-105">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinque console di Windows PowerShell in esecuzione contemporaneamente](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="d7cef-107">Questo non è ottimale per la gestione di Office 365 perché non è possibile scambiare dati tra queste cinque finestre per la gestione interservizi.</span><span class="sxs-lookup"><span data-stu-id="d7cef-107">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="d7cef-108">In questo argomento viene descritto come utilizzare una singola istanza di Windows PowerShell da cui è possibile gestire Office 365, Skype for business online, Exchange Online, SharePoint Online, Microsoft teams e il &amp; Centro sicurezza e conformità.</span><span class="sxs-lookup"><span data-stu-id="d7cef-108">This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="d7cef-109">Questo articolo contiene attualmente solo i comandi per la connessione al cloud Office 365 Worldwide (+ GCC).</span><span class="sxs-lookup"><span data-stu-id="d7cef-109">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="d7cef-110">Altre note forniscono collegamenti ad articoli contenenti informazioni sulla connessione alle altre cloud di Office 365.</span><span class="sxs-lookup"><span data-stu-id="d7cef-110">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="d7cef-111">Informazioni preliminari</span><span class="sxs-lookup"><span data-stu-id="d7cef-111">Before you begin</span></span>

<span data-ttu-id="d7cef-112">Prima di poter gestire tutte le Office 365 da una singola istanza di Windows PowerShell, prendere in considerazione i prerequisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="d7cef-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="d7cef-113">L'account aziendale o dell'Istituto di istruzione di Office 365 utilizzato per queste procedure deve essere membro di un ruolo di amministratore di Office 365.</span><span class="sxs-lookup"><span data-stu-id="d7cef-113">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role.</span></span> <span data-ttu-id="d7cef-114">Per ulteriori informazioni, vedere [Informazioni sui ruoli di amministratore di Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="d7cef-114">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span> <span data-ttu-id="d7cef-115">Questo è un requisito per Office 365 PowerShell, non necessariamente per tutti gli altri servizi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="d7cef-115">This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="d7cef-116">È possibile utilizzare le seguenti versioni a 64 bit di Windows:</span><span class="sxs-lookup"><span data-stu-id="d7cef-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="d7cef-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="d7cef-117">Windows 10</span></span>
    
  - <span data-ttu-id="d7cef-118">Windows 8.1 o Windows 8</span><span class="sxs-lookup"><span data-stu-id="d7cef-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="d7cef-119">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="d7cef-119">Windows Server 2019</span></span>
    
  - <span data-ttu-id="d7cef-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="d7cef-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="d7cef-121">Windows Server 2012 R2 o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="d7cef-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="d7cef-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="d7cef-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="d7cef-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="d7cef-123">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="d7cef-124">\*È necessario installare Microsoft .NET Framework 4,5. *x* e quindi Windows management Framework 3,0 o Windows management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="d7cef-124">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="d7cef-125">Per ulteriori informazioni, vedere [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) o [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="d7cef-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="d7cef-126">È necessario utilizzare una versione di Windows a 64 bit a causa dei requisiti per il modulo Skype for business online e uno dei moduli di Office 365.</span><span class="sxs-lookup"><span data-stu-id="d7cef-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="d7cef-127">È necessario installare i moduli necessari per Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype for business online e teams:</span><span class="sxs-lookup"><span data-stu-id="d7cef-127">You need to install the modules that are required for Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype for Business Online and Teams:</span></span>
    
   - [<span data-ttu-id="d7cef-128">Azure Active Directory V2</span><span class="sxs-lookup"><span data-stu-id="d7cef-128">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="d7cef-129">SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="d7cef-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="d7cef-130">Modulo di Windows PowerShell per Skype for business online</span><span class="sxs-lookup"><span data-stu-id="d7cef-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [<span data-ttu-id="d7cef-131">Exchange Online PowerShell V2</span><span class="sxs-lookup"><span data-stu-id="d7cef-131">Exchange Online PowerShell V2</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [<span data-ttu-id="d7cef-132">Panoramica di PowerShell Teams</span><span class="sxs-lookup"><span data-stu-id="d7cef-132">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  <span data-ttu-id="d7cef-133">Windows PowerShell deve essere configurato per l'esecuzione di script firmati per Skype for business online e il Centro sicurezza e &amp; conformità.</span><span class="sxs-lookup"><span data-stu-id="d7cef-133">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="d7cef-134">A tale scopo, eseguire il comando riportato di seguito in una sessione di Windows PowerShell con privilegi elevati (una finestra di Windows PowerShell che si apre selezionando **Esegui come amministratore**).</span><span class="sxs-lookup"><span data-stu-id="d7cef-134">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="d7cef-135">Passaggi di connessione quando si utilizza una password</span><span class="sxs-lookup"><span data-stu-id="d7cef-135">Connection steps when using a password</span></span>

<span data-ttu-id="d7cef-136">Di seguito sono riportati i passaggi da eseguire per la connessione a tutti i servizi in una singola finestra di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7cef-136">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="d7cef-137">Aprire Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7cef-137">Open Windows PowerShell.</span></span>
    
2. <span data-ttu-id="d7cef-138">Eseguire questo comando e immettere le credenziali dell'account aziendale o dell'Istituto di istruzione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="d7cef-138">Run this command and enter your Office 365 work or school account credentials.</span></span>
    
  ```powershell
  $credential = Get-Credential
  ```

3. <span data-ttu-id="d7cef-139">Eseguire questo comando per connettersi ad Azure AD utilizzando il modulo di Azure Active Directory PowerShell per Graph.</span><span class="sxs-lookup"><span data-stu-id="d7cef-139">Run this command to connect to Azure AD using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="d7cef-140">In alternativa, se si utilizza il modulo modulo di Microsoft Azure Active Directory per Windows PowerShell, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="d7cef-140">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
><span data-ttu-id="d7cef-141">PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per Windows PowerShell e i cmdlet con **MSOL** all'interno del nome.</span><span class="sxs-lookup"><span data-stu-id="d7cef-141">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="d7cef-142">Per continuare a usare i cmdlet, è necessario eseguirli in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7cef-142">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

4. <span data-ttu-id="d7cef-143">Eseguire questi comandi per connettersi a SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="d7cef-143">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="d7cef-144">Sostituire _ \< DomainHost>_ con il valore effettivo per il dominio.</span><span class="sxs-lookup"><span data-stu-id="d7cef-144">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="d7cef-145">Ad esempio, per "litwareinc.onmicrosoft.com", il valore di _ \< DomainHost>_ è "litwareinc".</span><span class="sxs-lookup"><span data-stu-id="d7cef-145">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="d7cef-146">Eseguire questi comandi per connettersi a Skype for business online.</span><span class="sxs-lookup"><span data-stu-id="d7cef-146">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="d7cef-147">Un avviso relativo all'aumento del `WSMan NetworkDelayms` valore è previsto per la prima volta che si connette e deve essere ignorato.</span><span class="sxs-lookup"><span data-stu-id="d7cef-147">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="d7cef-148">Eseguire questo comando per connettersi a Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="d7cef-148">Run this command to connect to Exchange Online.</span></span>
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
><span data-ttu-id="d7cef-149">Per connettersi a Exchange Online per le nuvole di Office 365 diverse da quelle di tutto il mondo, utilizzare il parametro **-ExchangeEnvironmentName** .</span><span class="sxs-lookup"><span data-stu-id="d7cef-149">To connect to Exchange Online for Office 365 clouds other than Worldwide, use the **-ExchangeEnvironmentName** parameter.</span></span> <span data-ttu-id="d7cef-150">Per ulteriori informazioni, vedere [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) .</span><span class="sxs-lookup"><span data-stu-id="d7cef-150">See [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) for more information.</span></span>
>

7. <span data-ttu-id="d7cef-151">Eseguire questi comandi per connettersi ai team di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7cef-151">Run these commands to connect to Teams PowerShell.</span></span>
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
><span data-ttu-id="d7cef-152">Per connettersi a cloud di Microsoft teams diversi da quelli di tutto il mondo, vedere [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span><span class="sxs-lookup"><span data-stu-id="d7cef-152">To connect to Microsoft Teams clouds other than Worldwide, see [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span></span>
>

8. <span data-ttu-id="d7cef-153">Eseguire questi comandi per connettersi al centro sicurezza e &amp; conformità.</span><span class="sxs-lookup"><span data-stu-id="d7cef-153">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="d7cef-154">Per eseguire la connessione al &amp; Centro sicurezza e conformità per office 365 cloud diversi da quelli di tutto il mondo, vedere [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="d7cef-154">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="d7cef-155">Di seguito sono riportati tutti i comandi in un singolo blocco quando si utilizza il modulo di Azure Active Directory PowerShell per Graph.</span><span class="sxs-lookup"><span data-stu-id="d7cef-155">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="d7cef-156">Specificare il nome dell'host di dominio e quindi eseguirli contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="d7cef-156">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

<span data-ttu-id="d7cef-157">In alternativa, ecco tutti i comandi in un singolo blocco quando si utilizza il modulo modulo di Microsoft Azure Active Directory per Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7cef-157">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="d7cef-158">Specificare il nome dell'host di dominio e quindi eseguirli contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="d7cef-158">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

<span data-ttu-id="d7cef-159">Quando si è pronti per chiudere la finestra di Windows PowerShell, eseguire il comando seguente per rimuovere le sessioni attive in Skype for business online, SharePoint Online, il &amp; Centro sicurezza e conformità e i team:</span><span class="sxs-lookup"><span data-stu-id="d7cef-159">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, SharePoint Online, the Security &amp; Compliance Center, and Teams:</span></span>
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="d7cef-160">Passaggi di connessione quando si utilizza l'autenticazione a più fattori</span><span class="sxs-lookup"><span data-stu-id="d7cef-160">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="d7cef-161">Di seguito sono riportati tutti i comandi di un singolo blocco per la connessione ad Azure AD, SharePoint Online, Skype for business, Exchange Online e i team che utilizzano l'autenticazione a più fattori in una singola finestra utilizzando il modulo Azure Active Directory PowerShell per Graph.</span><span class="sxs-lookup"><span data-stu-id="d7cef-161">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, Skype for Business, Exchange Online, and Teams using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="d7cef-162">Specificare il nome dell'entità utente (UPN, User Principal Name) di un account utente e il nome host del dominio, quindi eseguirli contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="d7cef-162">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

<span data-ttu-id="d7cef-163">In alternativa, ecco tutti i comandi quando si utilizza il modulo di Microsoft Azure Active Directory Module per Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7cef-163">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

<span data-ttu-id="d7cef-164">Per il &amp; Centro sicurezza e conformità, vedere [Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) to Connect using multi-factor authentication:</span><span class="sxs-lookup"><span data-stu-id="d7cef-164">For the Security &amp; Compliance Center, see [Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) to connect using multi-factor authentication:</span></span>

## <a name="see-also"></a><span data-ttu-id="d7cef-165">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d7cef-165">See also</span></span>

- [<span data-ttu-id="d7cef-166">Connettersi a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="d7cef-166">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="d7cef-167">Gestire SharePoint Online con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="d7cef-167">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="d7cef-168">Gestire gli account utente, le licenze e i gruppi con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7cef-168">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="d7cef-169">Utilizzo di Windows PowerShell per creare rapporti in Office 365</span><span class="sxs-lookup"><span data-stu-id="d7cef-169">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
