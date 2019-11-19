---
title: Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/28/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: "Riepilogo: connettere Windows PowerShell a tutti i servizi di Office 365 in un'unica finestra di Windows PowerShell."
ms.openlocfilehash: f64a29bb0594694c5a6b6e2dff8d0f7611fdf11e
ms.sourcegitcommit: 21901808f112dd1d8d01617c4be37911efc379f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2019
ms.locfileid: "38707063"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="1c9ec-103">Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c9ec-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="1c9ec-104">**Riepilogo:** Invece di gestire diversi servizi di Office 365 in finestre separate della console PowerShell, è possibile connettersi a tutti i servizi di Office 365 e gestirli da una singola finestra della console.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="1c9ec-105">Quando si utilizza PowerShell per gestire Office 365, è possibile che siano disponibili fino a cinque sessioni di Windows PowerShell diverse contemporaneamente corrispondenti all'interfaccia di amministrazione di Microsoft 365, SharePoint Online, Exchange Online, Skype for business online e il Centro sicurezza &amp; e conformità.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-105">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="1c9ec-106">Con cinque diversi metodi di connessione in sessioni di Windows PowerShell separate, il desktop potrebbe essere simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="1c9ec-106">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinque console di Windows PowerShell in esecuzione contemporaneamente](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="1c9ec-108">Questo non è ottimale per la gestione di Office 365 perché non è possibile scambiare dati tra queste cinque finestre per la gestione interservizi.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-108">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="1c9ec-109">In questo argomento viene descritto come utilizzare una singola istanza di Windows PowerShell da cui è possibile gestire Office 365, Skype for business online, Exchange Online, SharePoint Online e il centro &amp; sicurezza e conformità.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-109">This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="1c9ec-110">Questo articolo contiene attualmente solo i comandi per la connessione al cloud Office 365 Worldwide (+ GCC).</span><span class="sxs-lookup"><span data-stu-id="1c9ec-110">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="1c9ec-111">Altre note forniscono collegamenti ad articoli contenenti informazioni sulla connessione alle altre cloud di Office 365.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-111">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="1c9ec-112">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="1c9ec-112">Before you begin</span></span>

<span data-ttu-id="1c9ec-113">Prima di poter gestire tutte le Office 365 da una singola istanza di Windows PowerShell, prendere in considerazione i prerequisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="1c9ec-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="1c9ec-114">L'account aziendale o dell'Istituto di istruzione di Office 365 utilizzato per queste procedure deve essere membro di un ruolo di amministratore di Office 365.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-114">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role.</span></span> <span data-ttu-id="1c9ec-115">Per ulteriori informazioni, vedere [Informazioni sui ruoli di amministratore di Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="1c9ec-115">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span> <span data-ttu-id="1c9ec-116">Questo è un requisito per Office 365 PowerShell, non necessariamente per tutti gli altri servizi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-116">This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="1c9ec-117">È possibile utilizzare le seguenti versioni a 64 bit di Windows:</span><span class="sxs-lookup"><span data-stu-id="1c9ec-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="1c9ec-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="1c9ec-118">Windows 10</span></span>
    
  - <span data-ttu-id="1c9ec-119">Windows 8.1 o Windows 8</span><span class="sxs-lookup"><span data-stu-id="1c9ec-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="1c9ec-120">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="1c9ec-120">Windows Server 2019</span></span>
    
  - <span data-ttu-id="1c9ec-121">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="1c9ec-121">Windows Server 2016</span></span>
    
  - <span data-ttu-id="1c9ec-122">Windows Server 2012 R2 o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="1c9ec-122">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="1c9ec-123">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="1c9ec-123">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="1c9ec-124">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="1c9ec-124">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="1c9ec-125">\*È necessario installare Microsoft .NET Framework 4,5. *x* e quindi Windows management Framework 3,0 o Windows management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-125">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="1c9ec-126">Per ulteriori informazioni, vedere [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) o [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="1c9ec-126">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="1c9ec-127">È necessario utilizzare una versione di Windows a 64 bit a causa dei requisiti per il modulo Skype for business online e uno dei moduli di Office 365.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-127">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="1c9ec-128">È necessario installare i moduli necessari per Azure AD, SharePoint Online e Skype for business online:</span><span class="sxs-lookup"><span data-stu-id="1c9ec-128">You need to install the modules that are required for Azure AD, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="1c9ec-129">Azure Active Directory V2</span><span class="sxs-lookup"><span data-stu-id="1c9ec-129">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="1c9ec-130">SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="1c9ec-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="1c9ec-131">Modulo di Windows PowerShell per Skype for business online</span><span class="sxs-lookup"><span data-stu-id="1c9ec-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="1c9ec-132">Windows PowerShell deve essere configurato per l'esecuzione di script firmati per Skype for business online, Exchange Online e il &amp; Centro sicurezza e conformità.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-132">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="1c9ec-133">A tale scopo, eseguire il comando riportato di seguito in una sessione di Windows PowerShell con privilegi elevati (una finestra di Windows PowerShell che si apre selezionando **Esegui come amministratore**).</span><span class="sxs-lookup"><span data-stu-id="1c9ec-133">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="1c9ec-134">Passaggi di connessione quando si utilizza una password</span><span class="sxs-lookup"><span data-stu-id="1c9ec-134">Connection steps when using a password</span></span>

<span data-ttu-id="1c9ec-135">Di seguito sono riportati i passaggi da eseguire per la connessione a tutti i servizi in una singola finestra di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-135">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="1c9ec-136">Aprire Windows PowerShell come amministratore (utilizzare **Esegui come amministratore**).</span><span class="sxs-lookup"><span data-stu-id="1c9ec-136">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="1c9ec-137">Eseguire questo comando e immettere le credenziali dell'account aziendale o dell'Istituto di istruzione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-137">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```powershell
  $credential = Get-Credential
  ```

3. <span data-ttu-id="1c9ec-138">Eseguire questo comando per connettersi ad Azure Active Directory (AD) utilizzando il modulo Azure Active Directory PowerShell per Graph.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-138">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="1c9ec-139">In alternativa, se si utilizza il modulo modulo di Microsoft Azure Active Directory per Windows PowerShell, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-139">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

4. <span data-ttu-id="1c9ec-140">Eseguire questi comandi per connettersi a SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-140">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="1c9ec-141">Sostituire _ \<DomainHost>_ con il valore effettivo per il dominio.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-141">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="1c9ec-142">Ad esempio, per "litwareinc.onmicrosoft.com", il _ \<valore di DomainHost>_ è "litwareinc".</span><span class="sxs-lookup"><span data-stu-id="1c9ec-142">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="1c9ec-143">Eseguire questi comandi per connettersi a Skype for business online.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-143">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="1c9ec-144">Un avviso relativo all'aumento `WSMan NetworkDelayms` del valore è previsto per la prima volta che si connette e deve essere ignorato.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-144">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="1c9ec-145">Eseguire questi comandi per connettersi a Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-145">Run these commands to connect to Exchange Online.</span></span>
    
  ```powershell
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

>[!Note]
><span data-ttu-id="1c9ec-146">Per connettersi a Exchange Online per le nuvole di Office 365 diverse da quelle di tutto il mondo, vedere [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="1c9ec-146">To connect to Exchange Online for Office 365 clouds other than Worldwide, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>
>

7. <span data-ttu-id="1c9ec-147">Eseguire questi comandi per connettersi al centro sicurezza &amp; e conformità.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-147">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="1c9ec-148">Per eseguire la connessione al &amp; Centro sicurezza e conformità per Office 365 cloud diversi da quelli di tutto il mondo, vedere [connect to office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="1c9ec-148">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="1c9ec-149">Di seguito sono riportati tutti i comandi in un singolo blocco quando si utilizza il modulo di Azure Active Directory PowerShell per Graph.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-149">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="1c9ec-150">Specificare il nome dell'host di dominio e quindi eseguirli contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-150">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

<span data-ttu-id="1c9ec-151">In alternativa, ecco tutti i comandi in un singolo blocco quando si utilizza il modulo modulo di Microsoft Azure Active Directory per Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-151">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="1c9ec-152">Specificare il nome dell'host di dominio e quindi eseguirli contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-152">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

<span data-ttu-id="1c9ec-153">Quando si è pronti per chiudere la finestra di Windows PowerShell, eseguire il comando seguente per rimuovere le sessioni attive in Skype for business online, Exchange Online, SharePoint Online e il centro &amp; sicurezza e conformità:</span><span class="sxs-lookup"><span data-stu-id="1c9ec-153">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="1c9ec-154">Passaggi di connessione quando si utilizza l'autenticazione a più fattori</span><span class="sxs-lookup"><span data-stu-id="1c9ec-154">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="1c9ec-155">Di seguito sono riportati tutti i comandi di un singolo blocco per la connessione ad Azure AD, SharePoint Online e Skype per buiness utilizzando l'autenticazione a più fattori in una singola finestra utilizzando il modulo di Azure Active Directory PowerShell per Graph.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-155">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="1c9ec-156">Specificare il nome dell'entità utente (UPN, User Principal Name) di un account utente e il nome host del dominio, quindi eseguirli contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-156">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

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
```

<span data-ttu-id="1c9ec-157">In alternativa, ecco tutti i comandi quando si utilizza il modulo di Microsoft Azure Active Directory Module per Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-157">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

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
```

<span data-ttu-id="1c9ec-158">Per Exchange Online e il centro &amp; sicurezza e conformità, vedere i seguenti argomenti per la connessione con l'autenticazione a più fattori:</span><span class="sxs-lookup"><span data-stu-id="1c9ec-158">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- [<span data-ttu-id="1c9ec-159">Connettersi a PowerShell di Exchange Online utilizzando l'autenticazione a più fattori</span><span class="sxs-lookup"><span data-stu-id="1c9ec-159">Connect to Exchange Online PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [<span data-ttu-id="1c9ec-160">Connettersi a Office 365 Security & Compliance Center PowerShell con l'autenticazione a più fattori</span><span class="sxs-lookup"><span data-stu-id="1c9ec-160">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="1c9ec-161">Tenere presente che, in entrambi i casi, è necessario connettersi utilizzando sessioni separate del modulo Exchange Online Remote PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c9ec-161">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="see-also"></a><span data-ttu-id="1c9ec-162">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1c9ec-162">See also</span></span>

- [<span data-ttu-id="1c9ec-163">Connettersi a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="1c9ec-163">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="1c9ec-164">Gestire SharePoint Online con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="1c9ec-164">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="1c9ec-165">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c9ec-165">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="1c9ec-166">Utilizzo di Windows PowerShell per creare rapporti in Office 365</span><span class="sxs-lookup"><span data-stu-id="1c9ec-166">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
