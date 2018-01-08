---
title: Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- DecEntMigration
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Riepilogo: Connessione di Windows PowerShell per tutti i servizi di Office 365 in un''unica finestra di Windows PowerShell.'
ms.openlocfilehash: 28016342fff77e33bd18369ae08b773ecea32644
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="3bfed-103">Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3bfed-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="3bfed-104">**Riepilogo:** Invece di gestire diversi servizi di Office 365 nelle finestre di console PowerShell separate, è possibile connettersi a tutti i servizi di Office 365 e gestirli da unica finestra della console.</span><span class="sxs-lookup"><span data-stu-id="3bfed-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="3bfed-p101">Quando si utilizza PowerShell per gestire Office 365, è possibile avere fino a cinque sessioni diverse di Windows PowerShell aprire contemporaneamente corrispondente all'interfaccia di amministrazione di Office 365, SharePoint Online, Exchange Online, Skype Business online e la protezione &amp;Centro conformità. Con i metodi di connessione differenti cinque sessioni di Windows PowerShell distinti, il desktop è simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="3bfed-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinque console di Windows PowerShell in esecuzione contemporaneamente](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="3bfed-p102">Questo non è ottimale per la gestione di Office 365 perché non è possibile scambiare dati tra i cinque windows per la gestione dei servizi tra. In questo argomento viene descritto come utilizzare una singola istanza di Windows PowerShell da cui è possibile gestire Office 365, Skype Online Business, Exchange Online, SharePoint Online e la sicurezza &amp; centro conformità.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="3bfed-110">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="3bfed-110">Before you begin</span></span>
<span data-ttu-id="3bfed-111"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="3bfed-111"></span></span>

<span data-ttu-id="3bfed-112">Per poter gestire tutti di Office 365 da una singola istanza di Windows PowerShell, prendere in considerazione i prerequisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="3bfed-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="3bfed-p103">Office 365 di lavoro o scuola che l'account utilizzato per queste procedure esigenze per essere un membro di un ruolo di amministrazione di Office 365. Per ulteriori informazioni, vedere [ruoli di amministratore su Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Questo requisito per Office 365 PowerShell, non necessariamente per tutti gli altri servizi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="3bfed-116">È possibile utilizzare le seguenti versioni a 64 bit di Windows:</span><span class="sxs-lookup"><span data-stu-id="3bfed-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="3bfed-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="3bfed-117">Windows 10</span></span>
    
  - <span data-ttu-id="3bfed-118">Windows 8.1 o Windows 8</span><span class="sxs-lookup"><span data-stu-id="3bfed-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="3bfed-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="3bfed-119">Windows Server 2016</span></span>
    
  - <span data-ttu-id="3bfed-120">Windows Server 2012 R2 o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="3bfed-120">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="3bfed-121">Windows 7 Service Pack 1 (SP1)*</span><span class="sxs-lookup"><span data-stu-id="3bfed-121">Windows 7 Service Pack 1 (SP1)*</span></span>
    
  - <span data-ttu-id="3bfed-122">Windows Server 2008 R2 SP1*</span><span class="sxs-lookup"><span data-stu-id="3bfed-122">Windows Server 2008 R2 SP1*</span></span>
    
    * <span data-ttu-id="3bfed-p104">È necessario installare Microsoft .NET Framework 4.5. _x_ e quindi su Windows Management Framework 3.0 o Windows Management Framework 4.0. Per ulteriori informazioni, vedere [installazione di .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) e [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) o [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="3bfed-p104">You need to install the Microsoft .NET Framework 4.5. _x_ and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="3bfed-126">È necessario utilizzare una versione a 64 bit di Windows per i requisiti per il Skype per la funzionalità di Business in linea e uno dei moduli di Office 365.</span><span class="sxs-lookup"><span data-stu-id="3bfed-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="3bfed-127">È necessario installare i moduli necessari per Office 365, SharePoint Online e Skype Business online:</span><span class="sxs-lookup"><span data-stu-id="3bfed-127">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span></span>
    
  - [<span data-ttu-id="3bfed-128">Microsoft Online Services Assistente per l'accesso per i professionisti IT RTW</span><span class="sxs-lookup"><span data-stu-id="3bfed-128">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=286152)
    
  - [<span data-ttu-id="3bfed-129">Windows Azure Active Directory Module per Windows PowerShell (versione a 64 bit)</span><span class="sxs-lookup"><span data-stu-id="3bfed-129">Windows Azure Active Directory Module for Windows PowerShell (64-bit version)</span></span>](https://go.microsoft.com/fwlink/p/?linkid=236297)
    
  - [<span data-ttu-id="3bfed-130">SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="3bfed-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
    
  - [<span data-ttu-id="3bfed-131">Skype per le aziende in linea, modulo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3bfed-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="3bfed-p105">Windows PowerShell deve essere configurato per l'esecuzione di script con firma per Skype per Business Online, Exchange Online e la sicurezza &amp; centro conformità. A tale scopo, eseguire il comando seguente in una sessione di Windows PowerShell con privilegi elevata (una finestra di Windows PowerShell per aprire è selezionare **Esegui come amministratore**).</span><span class="sxs-lookup"><span data-stu-id="3bfed-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="3bfed-134">Versione breve (istruzioni senza spiegazioni)</span><span class="sxs-lookup"><span data-stu-id="3bfed-134">The short version (instructions without explanations)</span></span>
<span data-ttu-id="3bfed-135"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="3bfed-135"></span></span>

<span data-ttu-id="3bfed-p106">In questa sezione vengono illustrate le procedure di connessione senza spiegazioni dettagliate. Se si hanno altre domande o si desiderano ulteriori informazioni, è possibile leggere il resto dell'argomento. I numeri dei passaggi corrispondono ai numeri dei passaggi delle sezioni del resto dell'argomento:</span><span class="sxs-lookup"><span data-stu-id="3bfed-p106">This section presents the connection steps without in-depth explanations. If you have questions or want more information, you can read rest of the topic. The step numbers here match the step-numbered sections in the rest of the topic:</span></span>
  
1. <span data-ttu-id="3bfed-139">Aprire Windows PowerShell come amministratore (utilizzare **Esegui come amministratore**).</span><span class="sxs-lookup"><span data-stu-id="3bfed-139">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="3bfed-140">Eseguire questo comando e immettere il lavoro di Office 365 o scuola le credenziali dell'account.</span><span class="sxs-lookup"><span data-stu-id="3bfed-140">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="3bfed-141">Eseguire i comandi seguenti per connettersi a Office 365.</span><span class="sxs-lookup"><span data-stu-id="3bfed-141">Run these commands to connect to Office 365.</span></span>
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. <span data-ttu-id="3bfed-p107">Eseguire questi comandi per la connessione a SharePoint Online. Sostituire _ \<domainhost >_ con il valore effettivo per il dominio. Ad esempio, per `litwareinc.onmicrosoft.com`, il _ \<domainhost >_ valore è `litwareinc`.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p107">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="3bfed-p108">Eseguire questi comandi a cui connettersi Skype Business online. Un avviso che indica l'aumento di `WSMan NetworkDelayms` valore previsto per la prima volta la connessione e deve essere ignorato.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p108">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="3bfed-147">Eseguire questi comandi per la connessione a Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="3bfed-147">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. <span data-ttu-id="3bfed-148">Eseguire questi comandi per la connessione per la protezione &amp; centro conformità.</span><span class="sxs-lookup"><span data-stu-id="3bfed-148">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> <span data-ttu-id="3bfed-p109">Il prefisso di testo "cc" viene aggiunto a *tutti i* sicurezza &amp; sono presenti più nomi di cmdlet centro conformità in modo che è possibile eseguire i cmdlet in Exchange Online e la sicurezza &amp; centro conformità nella stessa sessione di Windows PowerShell. Ad esempio, **Get-RoleGroup** diventa **Get-ccRoleGroup** nella protezione &amp; centro conformità.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p109">The text prefix "cc" is added to  *all*  Security &amp; Compliance Center cmdlet names so you can run cmdlets that exist in both Exchange Online and the Security &amp; Compliance Center in the same Windows PowerShell session. For example, **Get-RoleGroup** becomes **Get-ccRoleGroup** in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="3bfed-p110">Di seguito sono tutti i comandi in un unico blocco. Specificare il nome dell'host del dominio e quindi eseguire tutte contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p110">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
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
Import-PSSession $exchangeSession -DisableNameChecking
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
Import-PSSession $ccSession -Prefix cc
```

<span data-ttu-id="3bfed-153">Quando è pronti per chiudere la finestra di Windows PowerShell, eseguire questo comando per rimuovere le sessioni attive per Skype per Business Online, Exchange Online, SharePoint Online e la sicurezza &amp; centro conformità:</span><span class="sxs-lookup"><span data-stu-id="3bfed-153">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="3bfed-154">Versione estesa (istruzioni con spiegazioni dettagliate)</span><span class="sxs-lookup"><span data-stu-id="3bfed-154">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="3bfed-155"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="3bfed-155"></span></span>

### <a name="step-1-open-windows-powershell-as-an-administrator"></a><span data-ttu-id="3bfed-156">Passaggio 1: Aprire Windows PowerShell come amministratore</span><span class="sxs-lookup"><span data-stu-id="3bfed-156">Step 1: Open Windows PowerShell as an administrator</span></span>
<span data-ttu-id="3bfed-157"><a name="Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="3bfed-157"></span></span>

<span data-ttu-id="3bfed-158">Se si esegue Windows 10, Windows 8, Windows 8.1, 2016 Server Windows, Windows Server 2012 R2 o Windows Server 2012 R2, eseguire questa operazione:</span><span class="sxs-lookup"><span data-stu-id="3bfed-158">If you're running Windows 10, Windows 8, Windows 8.1, Windows Server 2016, Windows Server 2012 R2, or Windows Server 2012 R2, do this:</span></span>
  
1. <span data-ttu-id="3bfed-159">Per trovare il collegamento per **Windows PowerShell**, utilizzare uno dei seguenti metodi:</span><span class="sxs-lookup"><span data-stu-id="3bfed-159">Use any of these methods to find the shortcut for **Windows PowerShell**:</span></span>
    
  - <span data-ttu-id="3bfed-160">Nella schermata Start fare clic su un'area vuota e digitare Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3bfed-160">On the Start screen, click an empty area, and type Windows PowerShell.</span></span>
    
  - <span data-ttu-id="3bfed-p111">Nella schermata Start o il desktop, premere Windows chiave + Q. L'accesso alla ricerca, digitare Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p111">On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Windows PowerShell.</span></span>
    
  - <span data-ttu-id="3bfed-p112">Nella schermata Start o il desktop, spostare il cursore all'angolo superiore destro o scorrere rapidamente dal bordo destro dello schermo per visualizzare gli accessi da sinistra. Selezionare l'accesso alla ricerca, quindi immettere Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p112">On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and enter Windows PowerShell.</span></span>
    
2. <span data-ttu-id="3bfed-165">Nei risultati della destro **Windows PowerShell**e scegliere **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="3bfed-165">In the results, right-click **Windows PowerShell**, and select **Run as administrator**.</span></span>
    
3. <span data-ttu-id="3bfed-166">Se viene visualizzata la finestra di dialogo **Controllo Account utente** , selezionare **Sì** per confermare che si desidera eseguire Windows PowerShell con credenziali di amministratore.</span><span class="sxs-lookup"><span data-stu-id="3bfed-166">If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.</span></span>
    
<span data-ttu-id="3bfed-167">Se si esegue Windows 7 SP1 (o Windows Server 2008 R2 SP1), eseguire questa operazione:</span><span class="sxs-lookup"><span data-stu-id="3bfed-167">If you're running Windows 7 SP1 (or Windows Server 2008 R2 SP1), do this:</span></span>
  
1. <span data-ttu-id="3bfed-p113">Nel menu **Start** , scegliere **Tutti i programmi** > **Accessori** > **Windows PowerShell**. Pulsante destro del mouse **Windows PowerShell**e quindi selezionare **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p113">On the **Start** menu, select **All Programs** > **Accessories** > **Windows PowerShell**. Right-click **Windows PowerShell**, and then select **Run as administrator**.</span></span>
    
2. <span data-ttu-id="3bfed-170">Se viene visualizzata la finestra di dialogo **Controllo Account utente** , selezionare **Sì** per confermare che si desidera eseguire Windows PowerShell con credenziali di amministratore.</span><span class="sxs-lookup"><span data-stu-id="3bfed-170">If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.</span></span>
    
<span data-ttu-id="3bfed-p114">È necessario eseguire Windows PowerShell come amministratore. In caso contrario, verrà visualizzato un messaggio di errore simile al seguente quando si tenta di importare uno dei moduli necessari.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p114">You must run Windows PowerShell as an administrator. If you don't, you're going to get an error message similar to this when you try to import one of the required modules.</span></span>
  
```
The specified module 'Microsoft.Online.SharePoint.Online.PowerShell' was not loaded because no valid module file was found in any directory.
```

<span data-ttu-id="3bfed-p115">L'unico modo per risolvere il problema si chiuderà Windows PowerShell e riavviare come amministratore. Ecco un modo semplice e veloce per indicare se si esegue Windows PowerShell come amministratore: prompt dei comandi è `PS C:\Windows\System32>`, non `PS C:\Users\YourUserName>`.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p115">The only way to remedy the situation is to close Windows PowerShell and restart it as an administrator. Here's a quick and easy way to tell if you're running Windows PowerShell as an administrator: the prompt is  `PS C:\Windows\System32>`, not  `PS C:\Users\YourUserName>`.</span></span>

  
### <a name="step-2-create-a-windows-powershell-credentials-object"></a><span data-ttu-id="3bfed-175">Passaggio 2: creazione di un oggetto credenziali di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3bfed-175">Step 2: Create a Windows PowerShell credentials object</span></span>
<span data-ttu-id="3bfed-176"><a name="Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="3bfed-176"></span></span>

<span data-ttu-id="3bfed-p116">L'oggetto credenziali consente di passare il nome utente e password di Windows PowerShell in modo crittografato. Per creare un oggetto credenziali, eseguire il seguente comando di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p116">The credentials object provides an encrypted way to pass your user name and password to Windows PowerShell. To create a credentials object, run the following command in Windows PowerShell.</span></span>
  
```
$credential = Get-Credential
```

> [!NOTE]
>  <span data-ttu-id="3bfed-p117">`$credential`è una variabile di cui verrà archiviato l'oggetto credenziali. Non è necessario assegnare un nome di variabile `$credential`, ma in questo modo risulta più facile da ricordare la variabile contiene l'oggetto credenziali. (E che è importante, perché questa variabile verrà riutilizzato più volte). Che verrà inoltre rendono più semplice per poter eseguire quali ad esempio perché venga utilizzato sempre in questo articolo `$credential` per rappresentare l'oggetto credenziali.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p117">`$credential` is a variable that will store the credentials object. You don't have to name the variable `$credential`, but doing so makes it easier to remember which variable contains the credentials object. (And that's important, because we'll reuse this variable several times.) That will also make it easier for you to follow our examples, because this article will always use  `$credential` to represent the credentials object.</span></span>
  
<span data-ttu-id="3bfed-182">Windows PowerShell verrà quindi visualizzare una finestra di dialogo simile al seguente.</span><span class="sxs-lookup"><span data-stu-id="3bfed-182">Windows PowerShell will then display a dialog box that looks like this.</span></span>
  
![Finestra di dialogo Richiesta credenziali vuota.](images/o365_powershell_empty_credentials_box.png)
  
<span data-ttu-id="3bfed-184">Digitare il proprio lavoro o scuola nome utente dell'account nella casella **nome utente** , utilizzando il formato _username@domainname_ (ad esempio, kenmyer@litwareinc.onmicrosoft.com); Digitare la password nella casella **Password** . e quindi fare clic su **OK**:</span><span class="sxs-lookup"><span data-stu-id="3bfed-184">Type your work or school account user name in the **User name** box, using the format _username@domainname_ (for example, kenmyer@litwareinc.onmicrosoft.com); type your password in the **Password** box; and then click **OK**:</span></span>
  
![Finestra di dialogo Richiesta credenziali completata.](images/o365_powershell_completed_credentials_box.png)
  
<span data-ttu-id="3bfed-p118">Si noti che, quando si verifica in genere, si potrà essere visualizzato alcun tipo di conferma che sia stato creato l'oggetto credenziali. (Windows PowerShell in genere viene illustrato quando operazioni vanno male, ma non sempre a spiegare quando le cose vanno destra.) Se si desidera verificare che sia stato creato l'oggetto credenziali, digitare quanto segue in Windows PowerShell e quindi premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p118">Note that, as is often the case, you won't see any sort of confirmation that the credentials object was created. (Windows PowerShell typically tells you when things go wrong but doesn't always tell you when things go right.) If you want to verify that the credentials object was created, type the following in Windows PowerShell and then press Enter.</span></span>
  
```
$credential
```

<span data-ttu-id="3bfed-188">Quindi, sullo schermo verranno visualizzati elementi analoghi a quelli riportati di seguito.</span><span class="sxs-lookup"><span data-stu-id="3bfed-188">You should then see something similar to this on the screen.</span></span>
  
```
UserName                               Password
--------                               --------
kenmyer@litwareinc.onmicrosoft.com     System.Security.SecureString
```

<span data-ttu-id="3bfed-p119">È necessario tenere presenti in questo caso è che il cmdlet [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618) crea solo l'oggetto credenziali. non autenticare l'utente o in caso contrario verificare che il nome utente e la password che è fornito siano corrette. Si supponga, ad esempio, che è stato digitato correttamente il nome utente come kenmyer@litwareinc.onmicrosoft.com. In caso contrario, **Get-Credential** creerà un oggetto credenziali utilizzando tale nome utente e senza controllo per verificare che sia effettivamente un nome utente valido. Non si conosce se è stato creato un oggetto credenziali valide effettivamente finché non si utilizza effettivamente tale oggetto tenti di connettersi ai servizi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p119">One thing to keep in mind here is that the [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618) cmdlet only creates the credentials object; it does not authenticate you or otherwise verify that the user name and password you supplied are correct. For example, suppose you mistyped the user name as kenmyer@litwareinc.onmicrosoft.com. If you do that, **Get-Credential** will create a credentials object using that user name, and without checking to see if that is actually a valid user name. You won't know whether you have created a truly valid credentials object until you actually use that object to try to connect to the Office 365 services.</span></span>
  
### <a name="step-3-connect-to-office-365"></a><span data-ttu-id="3bfed-192">Passaggio 3: Connettersi a Office 365</span><span class="sxs-lookup"><span data-stu-id="3bfed-192">Step 3: Connect to Office 365</span></span>
<span data-ttu-id="3bfed-193"><a name="Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="3bfed-193"></span></span>

<span data-ttu-id="3bfed-194">Si verrà inizia tramite la connessione a Office 365 stesso.</span><span class="sxs-lookup"><span data-stu-id="3bfed-194">We'll start by connecting to Office 365 itself.</span></span> 
  
<span data-ttu-id="3bfed-p120">Come prima cosa che è necessario eseguire qui è importare il modulo di Office 365 (il Microsoft Azure Active Directory Module per Windows PowerShell). A tale scopo, eseguire questo comando di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p120">The first thing we need to do here is import the Office 365 module (the Microsoft Azure Active Directory Module for Windows PowerShell). To do that, run this command in Windows PowerShell.</span></span>
  
```
Import-Module MsOnline
```

<span data-ttu-id="3bfed-197">Per verificare l'importazione del modulo, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="3bfed-197">If you want to verify that the module was imported, run this command.</span></span>
  
```
Get-Module
```

<span data-ttu-id="3bfed-198">In un punto qualsiasi nell'elenco di moduli restituito da questo comando verrà visualizzato qualcosa di simile al seguente: `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`.</span><span class="sxs-lookup"><span data-stu-id="3bfed-198">Somewhere in the list of modules that are returned by this command you should see something that looks like this:  `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`.</span></span>
  
<span data-ttu-id="3bfed-199">Se viene visualizzato `MSOnline` nell'elenco, ciò significa che tutti gli elementi che indica la presenza in base alla pianificazione.</span><span class="sxs-lookup"><span data-stu-id="3bfed-199">If you see  `MSOnline` listed, that means that everything went according to plan.</span></span>
  
<span data-ttu-id="3bfed-200">Con l'oggetto credenziali creato (vedere [passaggio 2: creare un oggetto credenziali di Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) e con il `MsOnline` modulo caricati, è possibile ora connettersi a Office 365 utilizzando il cmdlet [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) e il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="3bfed-200">With the credentials object created (see [Step 2: Create a Windows PowerShell credentials object](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) and with the  `MsOnline` module loaded, we can now connect to Office 365 by using the [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) cmdlet and the following command.</span></span>
  
```
Connect-MsolService -Credential $credential
```

<span data-ttu-id="3bfed-p121">Si noti che tutto è necessario fornire sono l'oggetto credenziali ( `$credential`). In base, le credenziali di Office 365 si connetterà automaticamente si al dominio corretto. Non è necessario specificare il nome di dominio quando si esegue **Connect-MsolService**.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p121">Notice that all you have to provide is the credentials object ( `$credential`). Based on those credentials, Office 365 will automatically connect you to the correct domain. You do not have to specify your domain name when running **Connect-MsolService**.</span></span>
  
<span data-ttu-id="3bfed-204">Per verificare che si really *sono* connessi a Office 365, eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="3bfed-204">To verify that you really  *are*  connected to Office 365, run this command.</span></span>
  
```
Get-MsolDomain
```

<span data-ttu-id="3bfed-205">Verrà restituito un elemento analogo al seguente:</span><span class="sxs-lookup"><span data-stu-id="3bfed-205">In return, you should get back something similar to this.</span></span>
  
```
Name                         Status          Authentication
----                         ------          --------------
litwareinc.onmicrosoft.com   Verified        Managed
```

### <a name="step-4-connect-to-sharepoint-online"></a><span data-ttu-id="3bfed-206">Passaggio 4: connessione a SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3bfed-206">Step 4: Connect to SharePoint Online</span></span>
<span data-ttu-id="3bfed-207"><a name="Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="3bfed-207"></span></span>

<span data-ttu-id="3bfed-208">Importare la funzionalità di SharePoint Online con il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="3bfed-208">Import the SharePoint Online module with the following command:</span></span>
  
```
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
```

<span data-ttu-id="3bfed-209">L'opzione _DisableNameChecking_ consente di ignorare questo avviso.</span><span class="sxs-lookup"><span data-stu-id="3bfed-209">The  _DisableNameChecking_ switch suppresses this warning.</span></span>
  
```
WARNING: The names of some imported commands from the module 'Microsoft.Online.SharePoint.PowerShell' include unapproved verbs that might make them less discoverable. To find the commands with unapproved verbs, run the Import-Module command again with the Verbose parameter. For a list of approved verbs, type Get-Verb.
```

<span data-ttu-id="3bfed-p122">Per connettersi a SharePoint Online, è necessario specificare due tipi di informazioni: le credenziali e l'URL del sito di amministrazione di SharePoint Online. La parte di credenziali è semplice: è già stata archiviata che nella variabile `$credential` (vedere [passaggio 2: creare un oggetto credenziali di Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)). Per quanto riguarda l'URL del sito di amministrazione, è difficile determinare anche. Si supponga che il nome di dominio di Office 365 è `litwareinc.onmicrosoft.com`.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p122">In order to connect to SharePoint Online, you need to supply two pieces of information: your credentials and the URL of your SharePoint Online admin site. The credentials part is easy: we've already stored that in the variable  `$credential` (see [Step 2: Create a Windows PowerShell credentials object](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)). As for the URL of your admin site, that's easy enough to determine, as well. Suppose your Office 365 domain name is  `litwareinc.onmicrosoft.com`.</span></span>
  
<span data-ttu-id="3bfed-214">Per determinare l'URL del sito di amministrazione, effettuare la seguente operazione:</span><span class="sxs-lookup"><span data-stu-id="3bfed-214">To determine the admin site URL, do this:</span></span>
  
1. <span data-ttu-id="3bfed-215">Innanzitutto, utilizzare il prefisso `https://`.</span><span class="sxs-lookup"><span data-stu-id="3bfed-215">Start by using the prefix  `https://`.</span></span>
    
2. <span data-ttu-id="3bfed-p123">Aggiungere la parte host di dominio del nome del dominio. Ad esempio, per `litwareinc.onmicrosoft.com`, il nome di dominio host è `litwareinc`. Per `contoso.onmicrosoft.com`, il nome di dominio host è `contoso`.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p123">Add the domain host portion of your domain name. For example, for  `litwareinc.onmicrosoft.com`, the domain host name is  `litwareinc`. For  `contoso.onmicrosoft.com`, the domain host name is  `contoso`.</span></span>
    
3. <span data-ttu-id="3bfed-219">Aggiungere un segno meno (-) seguito da `admin.sharepoint.com`.</span><span class="sxs-lookup"><span data-stu-id="3bfed-219">Add a hyphen (-) followed by  `admin.sharepoint.com`.</span></span>
    
<span data-ttu-id="3bfed-220">In altre parole:</span><span class="sxs-lookup"><span data-stu-id="3bfed-220">In other words:</span></span>
  
 `https://` + `litwareinc` + `-admin.sharepoint.com` = `https://litwareinc-admin.sharepoint.com`
  
<span data-ttu-id="3bfed-p124">Dopo aver creato l'URL, è possibile utilizzare quindi questo URL e l'oggetto credenziali per connettersi a SharePoint Online. Chiamare il cmdlet [Connect-SPOService](https://go.microsoft.com/fwlink/p/?LinkId=532436) con un comando simile al seguente.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p124">After you've constructed the URL, you can then use that URL and your credentials object to connect to SharePoint Online. Just call the [Connect-SPOService](https://go.microsoft.com/fwlink/p/?LinkId=532436) cmdlet, using a command similar to this one.</span></span>
  
```
Connect-SPOService -Url https://litwareinc-admin.sharepoint.com -credential $credential
```

<span data-ttu-id="3bfed-223">Per verificare che sia stata effettuata la connessione, eseguire il seguente comando di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3bfed-223">To verify that the connection has been made, run the following command in Windows PowerShell.</span></span>
  
```
Get-SPOSite
```

<span data-ttu-id="3bfed-p125">È consigliabile ottenere un elenco di tutti i siti di SharePoint Online. Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="3bfed-p125">You should get a list of all your SharePoint Online sites. Here is an example:</span></span>
  
```
Url                                       Owner          Storage Quota
---                                       -----          -------------
http://litwareinc-public.sharepoint.com/                 1000
https://litwareinc.sharepoint.com/                       1000
https://litwareinc.sharepoint.com/search                 1000
```

<span data-ttu-id="3bfed-p126">I comandi di Office 365 (quelle descritte in [passaggio 3: connettersi a Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) verrà funzionino come previsto. (Provare a eseguire **Get-MsolUser**e di valutare personalmente) Ciò significa che è possibile gestire Office 365 e SharePoint Online dalla stessa istanza di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p126">Your Office 365 commands (the ones described in [Step 3: Connect to Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) will still work. (Try running **Get-MsolUser**, and see for yourself.) That means that you can now manage both Office 365 and SharePoint Online from the same instance of Windows PowerShell.</span></span>
  
### <a name="step-5-connect-to-skype-for-business-online"></a><span data-ttu-id="3bfed-228">Passaggio 5: Connessione a Skype for Business online</span><span class="sxs-lookup"><span data-stu-id="3bfed-228">Step 5: Connect to Skype for Business Online</span></span>
<span data-ttu-id="3bfed-229"><a name="Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="3bfed-229"></span></span>

<span data-ttu-id="3bfed-p127">Connessione a Skype Business online (e per Exchange Online o la sicurezza &amp; centro conformità) è diverso rispetto alla connessione a Office 365 o SharePoint Online. Ciò avviene perché Skype per cmdlet Business Online ed Exchange Online non ottenere installato nel computer in uso come avviene per Office 365 e i cmdlet di SharePoint Online. In realtà, ogni volta che si effettua l'accesso, i cmdlet appropriati temporaneamente vengono copiati nel computer. Quando si accede, questi cmdlet vengono rimossi dal computer dell'utente.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p127">Connecting to Skype for Business Online (and to Exchange Online or the Security &amp; Compliance Center) is different than connecting to Office 365 or to SharePoint Online. That's because the Skype for Business Online and Exchange Online cmdlets don't get installed on your computer like the Office 365 and the SharePoint Online cmdlets do. Instead, each time you sign in, the appropriate cmdlets are temporarily copied to your computer. When you sign off, those cmdlets are then removed from your computer.</span></span>
  
<span data-ttu-id="3bfed-p128">Per connettersi al Skype Business online, è necessario importarlo Skype di funzionalità di Business in linea. A tale scopo, eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p128">In order to connect to Skype for Business Online, you need to import the Skype for Business Online module. To do that, run this command.</span></span>
  
```
Import-Module SkypeOnlineConnector
```

<span data-ttu-id="3bfed-236">La prima volta, potrebbe essere visualizzato il seguente messaggio di avviso, che può essere ignorato senza problemi.</span><span class="sxs-lookup"><span data-stu-id="3bfed-236">The first time you do this, you might see the following warning message, which you can safely ignore.</span></span>
  
```
WARNING: WSMan NetworkDelayms has been set to 30000 milliseconds. The previous value was 5000 milliseconds.
WARNING: To improve the performance of the Lync Online Connector, it is recommended that the network delay be set to
30000 milliseconds (30 seconds). However, you can use Set-WinRMNetworkDelayMS to change the network delay to any
integer value.
```

<span data-ttu-id="3bfed-237">Una volta importato il modulo, eseguire il comando riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="3bfed-237">After the module has been imported, run this command.</span></span>
  
```
$sfboSession = New-CsOnlineSession -Credential $credential
```

<span data-ttu-id="3bfed-p129">È stata creata una sessione remote PowerShell. In questo caso, ciò significa che è stata connessa a un'istanza di Windows PowerShell in esecuzione su uno dei server di Office 365.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p129">We have created a remote PowerShell session. In this case, that means that we've connected to an instance of Windows PowerShell running on one of the Office 365 servers.</span></span> 
  
<span data-ttu-id="3bfed-p130">Anche se è stata effettuata una connessione a Office 365, è non scaricare gli script, i cmdlet e altri elementi necessari per gestire Skype Business online. A tale scopo, è necessario eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p130">Although we've made a connection to Office 365, we haven't downloaded the scripts, cmdlets, and other items needed to manage Skype for Business Online. To do that, we have to run this command.</span></span>
  
```
Import-PSSession $sfboSession
```

<span data-ttu-id="3bfed-242">Quando si importa la sessione Windows PowerShell, è necessario visualizzare una barra di stato simile al seguente, un indicatore che segnala in tutti i Skype per cmdlet Business Online da importare nel computer.</span><span class="sxs-lookup"><span data-stu-id="3bfed-242">When you import the Windows PowerShell session, you should see a progress bar similar to the following, a progress bar that reports on all the Skype for Business Online cmdlets being imported to your computer.</span></span>
  
![Barra di stato di Lync Online.](images/o365_powershell_lync_progress_bar.png)
  
<span data-ttu-id="3bfed-244">Quando la barra di avanzamento scompare, verrà visualizzato un risultato analogo al seguente.</span><span class="sxs-lookup"><span data-stu-id="3bfed-244">When the progress bar disappears, you should then see output similar to the following.</span></span>
  
```
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     1.0        tmp_swc5mp4v.1ck  {Copy-CsVoicePolicy, Disabl...
```

### <a name="step-6-connect-to-exchange-online"></a><span data-ttu-id="3bfed-245">Passaggio 6: Connessione a Exchange Online</span><span class="sxs-lookup"><span data-stu-id="3bfed-245">Step 6: Connect to Exchange Online</span></span>
<span data-ttu-id="3bfed-246"><a name="Step6"> </a></span><span class="sxs-lookup"><span data-stu-id="3bfed-246"></span></span>

<span data-ttu-id="3bfed-247">Eseguire questo comando, che consente di creare una sessione remota di Windows PowerShell con Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="3bfed-247">Run this command, which creates a remote Windows PowerShell session with Exchange Online.</span></span>
  
```
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
```

> [!NOTE]
> <span data-ttu-id="3bfed-p131">È il comando per la connessione a Exchange Online più complicati di comando per connettersi a Skype Business online? Tecnicamente, non è: entrambi i comandi eseguono nello stesso modo. Tuttavia Skype per team Business Online creato il proprio cmdlet: **New-CsOnlineSession** , ovvero che nasconde alcuni dei parametri (ad esempio, _l'autenticazione_ e _AllowRedirection_) che vengono utilizzati durante la connessione a Exchange Online. Invece di utilizzarlo sarà necessario digitare direttamente tali informazioni, i parametri di _autenticazione_ e _AllowRedirection_ sono in modo efficace incorporati per il cmdlet **New-CsOnlineSession** . È necessario digitare questi parametri durante la connessione a Exchange Online poiché in Exchange Online, viene utilizzato il cmdlet [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621) standard per la connessione a Office 365. Lo svantaggio è la presenza di più digitando a tale. Il vantaggio è che non è necessario scaricare e installare un modulo di Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p131">Why is the command for connecting to Exchange Online more complicated than the command to connect to Skype for Business Online? Technically, it's not: both commands do the exact same thing. However, the Skype for Business Online team created its own cmdlet— **New-CsOnlineSession** —that hides some of the parameters (like _Authentication_ and _AllowRedirection_) that are used when connecting to Exchange Online. Instead of requiring you to type that information yourself, the  _Authentication_ and _AllowRedirection_ parameters are effectively built in to the **New-CsOnlineSession** cmdlet. You have to type those parameters when connecting to Exchange Online because Exchange Online uses the standard [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621) cmdlet to connect to Office 365. The disadvantage is that you have a little more typing to do. The advantage is that you don't have to download and install an Exchange Online module.</span></span>
  
<span data-ttu-id="3bfed-255">È necessario effettuare è fare importare questa sessione remota, così come sono state eseguite con Skype Business online.</span><span class="sxs-lookup"><span data-stu-id="3bfed-255">All you have to do now is import this remote session, just like we did with Skype for Business Online.</span></span>
  
```
Import-PSSession $exchangeSession -DisableNameChecking
```

<span data-ttu-id="3bfed-256">Sullo schermo verranno visualizzati elementi analoghi a quelli riportati di seguito.</span><span class="sxs-lookup"><span data-stu-id="3bfed-256">You should see something similar to this on the screen.</span></span>
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_nweiqjvl.geu {Add-AvailabilityAddressSpace...
```

<span data-ttu-id="3bfed-257">Provare ora a eseguire questo comando.</span><span class="sxs-lookup"><span data-stu-id="3bfed-257">Now try running this command.</span></span>
  
```
Get-AcceptedDomain
```

<span data-ttu-id="3bfed-258">In cambio, visualizzate informazioni sui domini di Office 365 che sono configurati per l'indirizzo di posta elettronica di Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="3bfed-258">In return, you should see information about your Office 365 domains that are configured for email addresses in Exchange Online.</span></span>
  
```
Name            DomainName          DomainType      Default
----            ----------          ----------      -------
litwareinc.com  litwareinc.com      Authoritative   True
```

### <a name="step-7-connect-to-the-security-amp-compliance-center"></a><span data-ttu-id="3bfed-259">Passaggio 7: Connessione per la protezione &amp; centro conformità</span><span class="sxs-lookup"><span data-stu-id="3bfed-259">Step 7: Connect to the Security &amp; Compliance Center</span></span>
<span data-ttu-id="3bfed-260"><a name="Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="3bfed-260"></span></span>

<span data-ttu-id="3bfed-p132">La sicurezza &amp; centro conformità è un servizio disponibile in Office 365 che consente all'utente per gestire le funzionalità di conformità da una posizione. Per ulteriori informazioni, vedere [centro conformità di Office 365](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx).</span><span class="sxs-lookup"><span data-stu-id="3bfed-p132">The Security &amp; Compliance Center is a service in Office 365 that lets you to manage compliance features from one location. For more information, see [Office 365 compliance center](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx).</span></span>
  
<span data-ttu-id="3bfed-263">Le istruzioni di connessione per la sicurezza &amp; centro conformità sono molto simili a quelle per Exchange Online, ma con una rotazione sono state aggiunte, verrà visualizzato in un momento.</span><span class="sxs-lookup"><span data-stu-id="3bfed-263">The connection instructions for the Security &amp; Compliance Center are very similar to those for Exchange Online, but with an added twist, which you'll see in a moment.</span></span>
  
<span data-ttu-id="3bfed-264">Eseguire questo comando, che consente di creare una sessione remote PowerShell con la protezione &amp; centro conformità.</span><span class="sxs-lookup"><span data-stu-id="3bfed-264">Run this command, which creates a remote PowerShell session with the Security &amp; Compliance Center.</span></span>
  
```
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
```

<span data-ttu-id="3bfed-265">A questo punto, eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="3bfed-265">Now run this command:</span></span>
  
```
Import-PSSession $ccSession -Prefix cc
```

<span data-ttu-id="3bfed-p133">Nuovamente, questo comando è molto simile al comando per Exchange Online. L'opzione _DisableNameChecking_ non è necessaria perché non sono presenti alcun verbi non approvati la sicurezza &amp; centro conformità. Informazioni sul, ma che ulteriori `-Prefix cc` parametro e valore? È la rotazione sono state aggiunta su che avevamo detto.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p133">Again, this command is very similar to the command for Exchange Online. The  _DisableNameChecking_ switch isn't required because there are no unapproved verbs in the Security &amp; Compliance Center. But what about that additional `-Prefix cc` parameter and value? That's the added twist we told you about.</span></span>
  
<span data-ttu-id="3bfed-p134">Exchange Online e la sicurezza &amp; centro conformità condividere alcuni cmdlet esattamente gli stessi nomi e fornisce le stesse funzionalità. **Get-RoleGroup** è riportato un esempio.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p134">Exchange Online and the Security &amp; Compliance Center share some cmdlets that have exactly the same names and provide the same functionality. **Get-RoleGroup** is an example.</span></span>
  
<span data-ttu-id="3bfed-p135">Pertanto, cosa succede se si tenta di importare le due sessioni che contengono cmdlet con lo stesso nome? Si verifica un conflitto. Verrà visualizzato un messaggio di avviso giallo big che informa che, `WARNING: Proxy creation has been skipped for the following command:` seguito dall'elenco dei cmdlet in conflitto che non è stato importato. Il risultato finale? È possibile eseguire **Get-RoleGroup** in Exchange Online perché si è connessi vi prima, ma non è possibile eseguire **Get-RoleGroup** per la protezione &amp; Allinea al centro conformità perché si è connessi vi ultimo e i cmdlet in conflitto rifiutate da importare.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p135">So what happens if you try to import two sessions that contain cmdlets with the same name? They collide. You'll get a big yellow warning message that says,  `WARNING: Proxy creation has been skipped for the following command:` followed by the list of conflicting cmdlets that couldn't be imported. The end result? You can run **Get-RoleGroup** in Exchange Online because you connected there first, but you can't run **Get-RoleGroup** in the Security &amp; Compliance Center because you connected there last and the conflicting cmdlets refused to import.</span></span>
  
<span data-ttu-id="3bfed-p136">Il modo più semplice per affrontare il problema consiste nell'aggiungere un prefisso di testo arbitrario per la protezione importata &amp; cmdlet centro conformità. Sono state eseguite che utilizzano il parametro _Prefix_ con il valore "cc" nel cmdlet **Import-PSSession** . Cosa che per noi? Eliminava conflitti modificando (leggermente) la sicurezza &amp; i nomi dei cmdlet di centro conformità per la sessione corrente. Le impostazioni di protezione importata &amp; centro conformità cmdlet ora iniziano con "cc" nella parte del nome del cmdlet sostantivo (a destra del "-"). Ad esempio, il cmdlet **Get-RoleGroup** oggetto di controversia diventa **Get-ccRoleGroup** per la sicurezza &amp; centro conformità in modo che non sia in conflitto con **Get-RoleGroup** per Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p136">The easiest way to deal with this problem is to add an arbitrary text prefix to the imported Security &amp; Compliance Center cmdlets. We did that using the  _Prefix_ parameter with the value "cc" on the **Import-PSSession** cmdlet. What did that do for us? It eliminated the conflicts by (slightly) changing the Security &amp; Compliance Center cmdlet names for this session. All of the imported Security &amp; Compliance Center cmdlets now start with "cc" in the noun part of the cmdlet name (to the right of the "-"). For example, the contentious **Get-RoleGroup** cmdlet becomes **Get-ccRoleGroup** for the Security &amp; Compliance Center so it doesn't conflict with **Get-RoleGroup** for Exchange Online.</span></span>
  
<span data-ttu-id="3bfed-p137">Lo svantaggio?  *Tutti i*  Protezione &amp; i nomi dei cmdlet di centro conformità viene assegnato il prefisso "cc", ovvero anche cmdlet univoco che non è necessario. Ad esempio, **Get-ComplianceSearch** diventa **Get-ccComplianceSearch** anche se non esiste alcun quali cmdlet di Exchange Online. È un po' di un riquadro, ma non male quando si considerano i vantaggi di gestione di tutti i servizi di Office 365 in una singola sessione di Windows PowerShell. Ricordare di aggiungere "cc" ai nomi di cmdlet per tutte le procedure di sicurezza &amp; centro conformità.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p137">The downside?  *All*  Security &amp; Compliance Center cmdlet names receive the "cc" prefix—even unique cmdlets that don't need it. For example, **Get-ComplianceSearch** becomes **Get-ccComplianceSearch** even though there is no such cmdlet in Exchange Online. It's a bit of a pain, but not too bad when you consider the benefits of managing all Office 365 services in a single Windows PowerShell session. Just remember to add "cc" to the cmdlet names for all procedures in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="3bfed-288">Se tutto va bene, la schermata visualizzata sarà simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="3bfed-288">If all goes well, you'll see something similar to this:</span></span>
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_xbbx5exr.ehm {Add-ccRoleGroupMember, Get-ccAdminAuditLogConfig, Get-ccA...
```

<span data-ttu-id="3bfed-289">A questo punto è disponibile gestire tutti i servizi di Office 365 in una singola sessione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3bfed-289">Now you are free to manage all Office 365 services in a single Windows PowerShell session.</span></span>
  
### <a name="step-8-gracefully-end-your-powershell-sessions"></a><span data-ttu-id="3bfed-290">Passaggio 8: Terminare normalmente le sessioni di PowerShell</span><span class="sxs-lookup"><span data-stu-id="3bfed-290">Step 8: Gracefully end your PowerShell sessions</span></span>
<span data-ttu-id="3bfed-291"><a name="Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="3bfed-291"></span></span>

<span data-ttu-id="3bfed-p138">Se appena si chiude la finestra di Windows PowerShell, la Skype per la connessione remota Business Online rimane attiva per 15 minuti successivi o meno. Poiché Skype Business online limita il numero di connessioni simultanee che qualsiasi una persona o a qualsiasi uno dominio può essere aperti, che può essere un problema. Con Skype Business online, un amministratore singolo può avere al massimo tre connessioni alla volta, e un dominio può avere un massimo di connessioni aperte nove. Se si accedere a Skype Business online e quindi chiudere senza chiudere correttamente la sessione, tale sessione rimane aperto per 15 minuti successivi o meno. Di conseguenza, che è una sola connessione meno disponibile per l'utente o ad altri amministratori del dominio.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p138">If you just close the Windows PowerShell window, your Skype for Business Online remote connection will remain active for the next 15 minutes or so. Because Skype for Business Online limits the number of simultaneous connections that any one person or any one domain can have open, that could be a problem. With Skype for Business Online, an individual administrator can have, at most, three open connections at one time, and a domain can have a maximum of nine open connections. If you sign in to Skype for Business Online and then exit without properly closing the session, that session remains open for the next 15 minutes or so. As a result, that's one fewer connection available to you or to other administrators in your domain.</span></span>
  
<span data-ttu-id="3bfed-p139">In realtà, possiamo chiudere le sessioni remote per Skype per Business Online, Exchange Online e la sicurezza &amp; del centro conformità normalmente. Prima di procedere è il seguente comando.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p139">Instead, let's close the remote sessions for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center gracefully. Before we do that, run this command.</span></span>
  
```
Get-PSSession
```

<span data-ttu-id="3bfed-p140">Il cmdlet [Get-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) dovrebbe essere inclusa la presenza di almeno tre sessioni remote Apri, uno per Skype Business online, uno per Exchange Online e uno per la sicurezza &amp; centro conformità (è possibile è possibile avere più di tre remote sessioni in esecuzione, a seconda se si utilizza questa istanza di Windows PowerShell per connettersi a un parametro oltre ai servizi Office 365). Verrà visualizzato qualcosa di simile al seguente.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p140">The [Get-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) cmdlet should show you that you have at least three remote sessions open, one for Skype for Business Online, one for Exchange Online and one for the Security &amp; Compliance Center (it's possible you could have more than three remote sessions running, depending on whether you've used this instance of Windows PowerShell to connect to something else besides the Office 365 services). You should see something similar to the following.</span></span>
  
```
Id Name     ComputerName     State   ConfigurationName    Availability
-- ----     ------------     -----   -----------------    ------------
 1 Session1 webdir0a.onl...  Opened  Microsoft.PowerShell    Available
 2 Session2 outlook.offi...  Opened  Microsoft.Exchange      Available
 3 Session3 ps.complianc...  Opened  Microsoft.Exchange      Available
```

<span data-ttu-id="3bfed-p141">Per chiudere le sessioni di tre, eseguire questi comandi uno alla volta. Il primo comando viene chiuso il Skype per sessione in linea aziendale, la seconda viene chiusa la sessione di Exchange Online, e la terza chiude la sicurezza &amp; sessione centro conformità.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p141">To close these three sessions, run these commands one at a time. The first command closes the Skype for Business Online session, the second closes the Exchange Online session, and the third closes the Security &amp; Compliance Center session.</span></span>
  
```
Remove-PSSession $sfboSession
Remove-PSSession $exchangeSession
Remove-PSSession $ccSession
```

<span data-ttu-id="3bfed-303">Se si esegue il cmdlet **Get-PSSession** , si verrà visualizzato alcun elemento affatto (a meno che non si dispone di sessioni remote configurate e in esecuzione).</span><span class="sxs-lookup"><span data-stu-id="3bfed-303">If you now run the **Get-PSSession** cmdlet, you should see nothing at all (unless you have other remote sessions up and running).</span></span>
  
![Console di Windows PowerShell senza sessioni remote](images/o365_powershell_no_remote_sessions.png)
  
> [!NOTE]
> <span data-ttu-id="3bfed-305">Se si preferisce chiudere tutte le sessioni remote contemporaneamente, è possibile utilizzare questo comando: >`Get-PSSession | Remove-PSSession`</span><span class="sxs-lookup"><span data-stu-id="3bfed-305">If you'd prefer to close all your remote sessions at the same time, you can use this command: >  `Get-PSSession | Remove-PSSession`</span></span>
  
<span data-ttu-id="3bfed-306">Se si prova a eseguire un cmdlet da uno di questi chiuso sessioni (ad esempio, **Get-CsMeetingConfiguration** in Skype Business online) verrà visualizzato un messaggio di errore simile al seguente.</span><span class="sxs-lookup"><span data-stu-id="3bfed-306">If you now try running a cmdlet from any of these closed sessions (for example, **Get-CsMeetingConfiguration** in Skype for Business Online) you'll get an error message that's similar to this one.</span></span>
  
```
Get-CsMeetingConfiguration : The term 'Get-CsMeetingConfiguration' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="3bfed-307">Tale messaggio di errore viene visualizzato poiché i cmdlet per Skype per Business Online, Exchange Online e la sicurezza &amp; centro conformità sono stati eliminati quando viene chiuso le sessioni remote.</span><span class="sxs-lookup"><span data-stu-id="3bfed-307">We get that error message because the cmdlets for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center were deleted when we closed the remote sessions.</span></span>
  
<span data-ttu-id="3bfed-308">Per chiudere la sessione di SharePoint Online, digitare il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="3bfed-308">To close the SharePoint Online session, type this command.</span></span>
  
```
Disconnect-SPOService
```

<span data-ttu-id="3bfed-309">Se ora si tenta di eseguire il cmdlet **Get-SPOSite** , verrà visualizzato un messaggio di errore simile al seguente.</span><span class="sxs-lookup"><span data-stu-id="3bfed-309">If you now try to run the **Get-SPOSite** cmdlet, you'll get an error message like this.</span></span>
  
```
get-sposite : No connection available. Use Connect-SPOService before running this CmdLet.
```

<span data-ttu-id="3bfed-310">Perché non è più connessi a SharePoint Online non è possibile recuperare le informazioni sul sito.</span><span class="sxs-lookup"><span data-stu-id="3bfed-310">You can't retrieve site information because you're no longer connected to SharePoint Online.</span></span>
  
<span data-ttu-id="3bfed-p142">Per quanto riguarda la connessione a Office 365, anche se non esiste un cmdlet **Connect-MsolService** , non esiste alcun cmdlet **Disconnect-MsolService** corrispondente. In modo per Office 365 appena chiudere la finestra di Windows PowerShell. Tuttavia, è comunque opportuno eseguire questa operazione ultimi in modo che è possibile correttamente disconnettersi da SharePoint Online, Skype per Business Online, Exchange Online e la sicurezza &amp; centro conformità.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p142">As for your connection to Office 365, although there's a **Connect-MsolService** cmdlet, there's no corresponding **Disconnect-MsolService** cmdlet. So for Office 365, just close the Windows PowerShell window. Nevertheless, it's still a good idea to do this last so you can properly disconnect from SharePoint Online, Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center.</span></span>
  
## <a name="new-to-office-365"></a><span data-ttu-id="3bfed-314">Nuovo utente di Office 365?</span><span class="sxs-lookup"><span data-stu-id="3bfed-314">New to Office 365?</span></span>
<span data-ttu-id="3bfed-315"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="3bfed-315"></span></span>

||
|:-----|
|<span data-ttu-id="3bfed-p143">![L'icona breve di apprendimento LinkedIn](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New a Office 365?**         Scopri corsi video gratuiti per [i professionisti IT e gli amministratori di Office 365](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), per offerto da Learning LinkedIn.</span><span class="sxs-lookup"><span data-stu-id="3bfed-p143">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="3bfed-318">See also</span><span class="sxs-lookup"><span data-stu-id="3bfed-318">See also</span></span>

#### 

[<span data-ttu-id="3bfed-319">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="3bfed-319">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="3bfed-320">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="3bfed-320">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="3bfed-321">Gestire SharePoint Online con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="3bfed-321">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="3bfed-322">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3bfed-322">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="3bfed-323">Utilizzo di Windows PowerShell per creare rapporti in Office 365</span><span class="sxs-lookup"><span data-stu-id="3bfed-323">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
