---
title: Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/10/2018
ms.audience: ITPro
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
description: "Riepilogo: Connessione di Windows PowerShell per tutti i servizi di Office 365 in un'unica finestra di Windows PowerShell."
ms.openlocfilehash: ffa603ec50c95f5800315eee07b4d01e058852f3
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="ec087-103">Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec087-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="ec087-104">**Riepilogo:** Invece di gestire diversi servizi di Office 365 nelle finestre di console PowerShell separate, è possibile connettersi a tutti i servizi di Office 365 e gestirli da unica finestra della console.</span><span class="sxs-lookup"><span data-stu-id="ec087-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="ec087-p101">Quando si utilizza PowerShell per gestire Office 365, è possibile avere fino a cinque sessioni diverse di Windows PowerShell aprire contemporaneamente corrispondente all'interfaccia di amministrazione di Office 365, SharePoint Online, Exchange Online, Skype Business online e la protezione &amp;Centro conformità. Con i metodi di connessione differenti cinque sessioni di Windows PowerShell distinti, il desktop è simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="ec087-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinque console di Windows PowerShell in esecuzione contemporaneamente](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="ec087-p102">Questo non è ottimale per la gestione di Office 365 perché non è possibile scambiare dati tra i cinque windows per la gestione dei servizi tra. In questo argomento viene descritto come utilizzare una singola istanza di Windows PowerShell da cui è possibile gestire Office 365, Skype Online Business, Exchange Online, SharePoint Online e la sicurezza &amp; centro conformità.</span><span class="sxs-lookup"><span data-stu-id="ec087-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="ec087-110">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="ec087-110">Before you begin</span></span>
<span data-ttu-id="ec087-111"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="ec087-111"></span></span>

<span data-ttu-id="ec087-112">Per poter gestire tutti di Office 365 da una singola istanza di Windows PowerShell, prendere in considerazione i prerequisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="ec087-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="ec087-p103">Office 365 di lavoro o scuola che l'account utilizzato per queste procedure esigenze per essere un membro di un ruolo di amministrazione di Office 365. Per ulteriori informazioni, vedere [ruoli di amministratore su Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Questo requisito per Office 365 PowerShell, non necessariamente per tutti gli altri servizi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="ec087-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="ec087-116">È possibile utilizzare le seguenti versioni a 64 bit di Windows:</span><span class="sxs-lookup"><span data-stu-id="ec087-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="ec087-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="ec087-117">Windows 10</span></span>
    
  - <span data-ttu-id="ec087-118">Windows 8.1 o Windows 8</span><span class="sxs-lookup"><span data-stu-id="ec087-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="ec087-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="ec087-119">Windows Server 2016</span></span>
    
  - <span data-ttu-id="ec087-120">Windows Server 2012 R2 o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="ec087-120">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="ec087-121">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="ec087-121">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="ec087-122">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="ec087-122">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="ec087-p104">È necessario installare Microsoft .NET Framework 4.5. *x* e quindi su Windows Management Framework 3.0 o Windows Management Framework 4.0. Per ulteriori informazioni, vedere [installazione di .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) e [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) o [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="ec087-p104">You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="ec087-125">È necessario utilizzare una versione a 64 bit di Windows per i requisiti per il Skype per la funzionalità di Business in linea e uno dei moduli di Office 365.</span><span class="sxs-lookup"><span data-stu-id="ec087-125">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="ec087-126">È necessario installare i moduli necessari per Office 365, SharePoint Online e Skype Business online:</span><span class="sxs-lookup"><span data-stu-id="ec087-126">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="ec087-127">Microsoft Online Services Assistente per l'accesso per i professionisti IT RTW</span><span class="sxs-lookup"><span data-stu-id="ec087-127">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=286152)
   - <span data-ttu-id="ec087-128">Windows Azure Active Directory Module per Windows PowerShell (versione a 64 bit) con il comando **Install-modulo MSOnline** un prompt dei comandi PowerShell con privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="ec087-128">Windows Azure Active Directory Module for Windows PowerShell (64-bit version) with the **Install-Module MSOnline** command at an elevated PowerShell command prompt.</span></span>
   - [<span data-ttu-id="ec087-129">SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="ec087-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="ec087-130">Skype per le aziende in linea, modulo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec087-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="ec087-p105">Windows PowerShell deve essere configurato per l'esecuzione di script con firma per Skype per Business Online, Exchange Online e la sicurezza &amp; centro conformità. A tale scopo, eseguire il comando seguente in una sessione di Windows PowerShell con privilegi elevata (una finestra di Windows PowerShell per aprire è selezionare **Esegui come amministratore**).</span><span class="sxs-lookup"><span data-stu-id="ec087-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="ec087-133">Passaggi di connessione quando si utilizza una password</span><span class="sxs-lookup"><span data-stu-id="ec087-133">Connection steps when using a password</span></span>
<span data-ttu-id="ec087-134"><a name="ConnStepsPassword"> </a></span><span class="sxs-lookup"><span data-stu-id="ec087-134"></span></span>

<span data-ttu-id="ec087-135">Ecco la procedura per la connessione a tutti i servizi in un'unica finestra di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec087-135">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="ec087-136">Aprire Windows PowerShell come amministratore (utilizzare **Esegui come amministratore**).</span><span class="sxs-lookup"><span data-stu-id="ec087-136">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="ec087-137">Eseguire questo comando e immettere il lavoro di Office 365 o scuola le credenziali dell'account.</span><span class="sxs-lookup"><span data-stu-id="ec087-137">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="ec087-138">Eseguire i comandi seguenti per connettersi a Office 365.</span><span class="sxs-lookup"><span data-stu-id="ec087-138">Run these commands to connect to Office 365.</span></span>
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. <span data-ttu-id="ec087-p106">Eseguire questi comandi per la connessione a SharePoint Online. Sostituire _ \<domainhost >_ con il valore effettivo per il dominio. Ad esempio, per `litwareinc.onmicrosoft.com`, il _ \<domainhost >_ valore è `litwareinc`.</span><span class="sxs-lookup"><span data-stu-id="ec087-p106">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="ec087-p107">Eseguire questi comandi a cui connettersi Skype Business online. Un avviso che indica l'aumento di `WSMan NetworkDelayms` valore previsto per la prima volta la connessione e deve essere ignorato.</span><span class="sxs-lookup"><span data-stu-id="ec087-p107">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="ec087-144">Eseguire questi comandi per la connessione a Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="ec087-144">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession
  ```

7. <span data-ttu-id="ec087-145">Eseguire questi comandi per la connessione per la protezione &amp; centro conformità.</span><span class="sxs-lookup"><span data-stu-id="ec087-145">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
  Import-PSSession $SccSession
  ```

<span data-ttu-id="ec087-p108">Di seguito sono tutti i comandi in un unico blocco. Specificare il nome dell'host del dominio e quindi eseguire tutte contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="ec087-p108">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Import-Module MsOnline
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $SccSession
```
<span data-ttu-id="ec087-148">Quando è pronti per chiudere la finestra di Windows PowerShell, eseguire questo comando per rimuovere le sessioni attive per Skype per Business Online, Exchange Online, SharePoint Online e la sicurezza &amp; centro conformità:</span><span class="sxs-lookup"><span data-stu-id="ec087-148">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="ec087-149">Passaggi di connessione quando si utilizza l'autenticazione a più fattori</span><span class="sxs-lookup"><span data-stu-id="ec087-149">Connection steps when using multi-factor authentication</span></span>
<span data-ttu-id="ec087-150"><a name="ConnStepsMFA"> </a></span><span class="sxs-lookup"><span data-stu-id="ec087-150"></span></span>

<span data-ttu-id="ec087-p109">Di seguito sono tutti i comandi in un unico blocco a cui connettersi Azure Active Directory, SharePoint Online e Skype per Buiness con l'autenticazione a più fattori in un'unica finestra. Specificare il nome di utente nome principale (UPN) di un account amministratore globale e il nome host del dominio e quindi eseguire tutte contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="ec087-p109">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window. Specify the user principal name (UPN) name of a global administrator account and your domain host name, and then run them all at one time.</span></span>

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
#Azure Active Directory
#If you are running Office 365 commands that contain "AzureAd" in their name, use this command:
Connect-AzureAD
#If you are running Office 365 commands that contain "Msol" in their name, comment the preceding command and un-comment the following command:
#Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="ec087-153">Per Exchange Online e la sicurezza &amp; centro conformità, vedere gli argomenti seguenti per la connessione con l'autenticazione a più fattori:</span><span class="sxs-lookup"><span data-stu-id="ec087-153">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- <span data-ttu-id="ec087-154">[Connessione a Exchange Online PowerShell con l'autenticazione a più fattori](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="ec087-154">[Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell).</span></span>
- [<span data-ttu-id="ec087-155">Connettersi alla sicurezza di Office 365 PowerShell centro conformità con l'autenticazione a più fattori</span><span class="sxs-lookup"><span data-stu-id="ec087-155">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="ec087-156">Si noti che in entrambi i casi, è necessario connettersi utilizzando sessioni separate di Exchange Online Remote PowerShell Module.</span><span class="sxs-lookup"><span data-stu-id="ec087-156">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="ec087-157">Nuovo utente di Office 365?</span><span class="sxs-lookup"><span data-stu-id="ec087-157">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="ec087-158">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ec087-158">See also</span></span>

- [<span data-ttu-id="ec087-159">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="ec087-159">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="ec087-160">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="ec087-160">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="ec087-161">Gestire SharePoint Online con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="ec087-161">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="ec087-162">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec087-162">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="ec087-163">Utilizzo di Windows PowerShell per creare rapporti in Office 365</span><span class="sxs-lookup"><span data-stu-id="ec087-163">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
