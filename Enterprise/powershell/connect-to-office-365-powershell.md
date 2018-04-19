---
title: Connettersi a PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: "Riepilogo: Connettersi all'organizzazione Office 365 con Office 365 PowerShell per eseguire attività di Office 365 admin center dalla riga di comando."
ms.openlocfilehash: 71b8c8d61a914fa7fd036fadb7e17ca3f66cd639
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="660fe-103">Connettersi a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="660fe-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="660fe-104">**Riepilogo:** Connettersi all'organizzazione Office 365 con Office 365 PowerShell per eseguire attività di amministrazione di Office 365 dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="660fe-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform Office 365 administration tasks from the command line.</span></span>
  
<span data-ttu-id="660fe-p101">Office 365 PowerShell consente di gestire le impostazioni di Office 365 dalla riga di comando. Connessione a Office 365 PowerShell è una semplice tre passaggi cui installare il software necessario, eseguire il software necessario e quindi connettersi all'organizzazione Office 365.</span><span class="sxs-lookup"><span data-stu-id="660fe-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

  
> [!TIP]
> <span data-ttu-id="660fe-p102">**Nuovo PowerShell?** Visualizzare una [Panoramica video di PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)per offerto da Learning LinkedIn.</span><span class="sxs-lookup"><span data-stu-id="660fe-p102">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="660fe-109">Che cosa è necessario sapere prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="660fe-109">What do you need to know before you begin?</span></span>

- <span data-ttu-id="660fe-110">Tempo stimato per il completamento: 5 minuti</span><span class="sxs-lookup"><span data-stu-id="660fe-110">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="660fe-111">È possibile utilizzare le seguenti versioni di Windows:</span><span class="sxs-lookup"><span data-stu-id="660fe-111">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="660fe-112">10 Windows, Windows 8.1, Windows 8 o Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="660fe-112">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="660fe-113">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="660fe-113">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="660fe-p103">Utilizzare una versione a 64 bit di Windows. È stato rimosso il supporto per la versione a 32 bit di Microsoft Azure Active Directory Module per Windows PowerShell ottobre del 2014.</span><span class="sxs-lookup"><span data-stu-id="660fe-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="660fe-p104">Queste procedure sono progettate per gli utenti che sono membri di un ruolo di amministrazione di Office 365. Per ulteriori informazioni, vedere [ruoli di amministratore su Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="660fe-p104">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="660fe-118">Connessione con il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="660fe-118">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="660fe-119">I comandi di Microsoft Azure Active Directory Module per Windows PowerShell dispongono **Msol** nel loro nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="660fe-119">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="660fe-120">Passaggio 1: Installazione del software necessario</span><span class="sxs-lookup"><span data-stu-id="660fe-120">Step 1: Install required software</span></span>

<span data-ttu-id="660fe-p105">È sufficiente effettuare questa procedura solo una volta, non ogni volta che ci si connette. Tuttavia, probabilmente sarà necessario installare periodicamente le versioni più recenti del software.</span><span class="sxs-lookup"><span data-stu-id="660fe-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="660fe-123">Installare la versione a 64 bit dell'Assistente di accesso a Microsoft Online Services: [Microsoft Online Services Assistente per l'accesso per RTW i professionisti IT](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="660fe-123">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="660fe-124">Installare il Microsoft Azure Active Directory Module per Windows PowerShell con la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="660fe-124">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="660fe-125">Aprire un prompt dei comandi di PowerShell di livello amministrativo.</span><span class="sxs-lookup"><span data-stu-id="660fe-125">Open an administrator-level PowerShell command prompt.</span></span>
  - <span data-ttu-id="660fe-126">Eseguire il comando **Install-modulo MSOnline** .</span><span class="sxs-lookup"><span data-stu-id="660fe-126">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="660fe-127">Se viene richiesto di installare il provider NuGet, digitare **s** e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="660fe-127">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="660fe-128">Se viene richiesto di installare il modulo da PSGallery, digitare **s** e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="660fe-128">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="660fe-129">Dopo l'installazione, chiudere la finestra di comando PowerShell.</span><span class="sxs-lookup"><span data-stu-id="660fe-129">After installation, close the PowerShell command window.</span></span>
    
### <a name="step-2-connect-to-your-office-365-subscription"></a><span data-ttu-id="660fe-130">Passaggio 2: Connessione per la sottoscrizione a Office 365</span><span class="sxs-lookup"><span data-stu-id="660fe-130">Step 2: Connect to your Office 365 subscription</span></span>
<span data-ttu-id="660fe-131"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="660fe-131"></span></span>

<span data-ttu-id="660fe-132">Per la connessione con solo un *nome di account e password*:</span><span class="sxs-lookup"><span data-stu-id="660fe-132">To connect with just an *account name and password*:</span></span>
  
1. <span data-ttu-id="660fe-133">Eseguire un prompt dei comandi di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="660fe-133">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="660fe-134">Nella finestra di comando **Windows PowerShell** , eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="660fe-134">In the **Windows PowerShell** command window, run the following commands:</span></span>
    
```
$UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
```

3. <span data-ttu-id="660fe-135">Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell** digitare il lavoro di Office 365 o nome utente dell'account scuola e la password e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="660fe-135">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="660fe-136">Per la connessione con *l'autenticazione a più fattori (MFA)*:</span><span class="sxs-lookup"><span data-stu-id="660fe-136">To connect with *multi-factor authentication (MFA)*:</span></span>
  
1. <span data-ttu-id="660fe-137">Eseguire un prompt dei comandi di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="660fe-137">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="660fe-138">Nella finestra di comando **Microsoft Azure Active Directory Module per Windows PowerShell** eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="660fe-138">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following command.</span></span>
    
```
Connect-MsolService
```

3. <span data-ttu-id="660fe-139">Nella finestra di dialogo **Azure Active Directory PowerShell** digitare il lavoro di Office 365 o nome utente dell'account scuola e la password e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="660fe-139">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="660fe-140">Seguire le istruzioni nella finestra di dialogo **Azure Active Directory PowerShell** per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="660fe-140">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="660fe-141">Come verificare se l'operazione ha avuto esito positivo</span><span class="sxs-lookup"><span data-stu-id="660fe-141">How do you know this worked?</span></span>
<span data-ttu-id="660fe-142"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="660fe-142"></span></span>

<span data-ttu-id="660fe-p106">Se non di errori, l'utente connesso correttamente. Una prova veloce consiste nell'eseguire un cmdlet di Office 365, ad esempio, **Get-MsolUser** - e visualizzare i risultati.</span><span class="sxs-lookup"><span data-stu-id="660fe-p106">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="660fe-145">Se non vengono visualizzati errori, controllare i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="660fe-145">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="660fe-p107">**Un problema comune è una password non corretta**. Eseguire di nuovo passaggio 3. e prestare particolare attenzione per il nome utente e la password che immessi.</span><span class="sxs-lookup"><span data-stu-id="660fe-p107">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="660fe-p108">* *The Microsoft Azure Active Directory Module per Windows PowerShell è necessario Microsoft .NET Framework 3.5.* funzione x * è abilitata per il computer * *. È probabile che il computer sia installata una versione più recente (ad esempio, 4 o 4.5.* x *), ma con le versioni precedenti la compatibilità con le versioni precedenti di .NET Framework può essere attivata o disattivata. Per ulteriori informazioni, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="660fe-p108">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.*x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.*x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="660fe-151">Per Windows Server 2012 o Windows Server 2012 R2, vedere [abilitare .NET Framework 3.5 con l'aggiunta di ruoli e guidata funzionalità](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="660fe-151">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="660fe-152">Per Windows 8 o Windows 8.1, vedere [installazione di .NET Framework 3.5 in Windows 8 o 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span><span class="sxs-lookup"><span data-stu-id="660fe-152">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="660fe-153">Per Windows 7 o Windows Server 2008 R2, vedere [non è possibile aprire il Azure Active Directory Module per Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="660fe-153">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>
    
- <span data-ttu-id="660fe-p109">**La versione del Microsoft Azure Active Directory Module per Windows PowerShell potrebbe non essere aggiornata.** Per controllare, eseguire il comando seguente in Office 365 PowerShell o il Microsoft Azure Active Directory Module per Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="660fe-p109">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="660fe-156">Se il numero di versione restituito è inferiore al valore 1.0.8070.2, disinstallare il Microsoft Azure Active Directory Module per Windows PowerShell e installare la versione più recente dal collegamento al passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="660fe-156">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="660fe-157">**Se si riceve un errore di connessione, vedere l'argomento:** ["Connect-MsolService: eccezione di tipo" errore](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="660fe-157">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="660fe-158">Collegarsi con Azure Active Directory PowerShell modulo grafico</span><span class="sxs-lookup"><span data-stu-id="660fe-158">Connect with the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="660fe-159"><a name="ConnectV2"> </a></span><span class="sxs-lookup"><span data-stu-id="660fe-159"></span></span>

<span data-ttu-id="660fe-160">I comandi descritti in Azure Active Directory PowerShell modulo grafico dispongono "AzureAD" nel loro nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="660fe-160">Commands in the Azure Active Directory PowerShell for Graph module have "AzureAD" in their cmdlet name.</span></span>

<span data-ttu-id="660fe-161">Per le procedure necessarie per i nuovi cmdlet di Azure Active Directory PowerShell modulo grafico, utilizzare la procedura seguente per installare il modulo ed eseguire la connessione alla sottoscrizione Office 365.</span><span class="sxs-lookup"><span data-stu-id="660fe-161">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="660fe-162">Per informazioni sul supporto per diverse versioni di Microsoft Windows, vedere [Azure Active Directory PowerShell modulo grafico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) .</span><span class="sxs-lookup"><span data-stu-id="660fe-162">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="660fe-163">Passaggio 1: Installazione del software necessario</span><span class="sxs-lookup"><span data-stu-id="660fe-163">Step 1: Install required software</span></span>

<span data-ttu-id="660fe-p110">È sufficiente effettuare questa procedura solo una volta, non ogni volta che ci si connette. Tuttavia, probabilmente sarà necessario installare periodicamente le versioni più recenti del software.</span><span class="sxs-lookup"><span data-stu-id="660fe-p110">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>

  
1. <span data-ttu-id="660fe-166">Aprire un prompt dei comandi di Windows PowerShell con privilegi elevati (eseguire Windows PowerShell come amministratore).</span><span class="sxs-lookup"><span data-stu-id="660fe-166">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="660fe-167">Nella **amministratore: Windows PowerShell** finestra prompt dei comandi eseguita il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="660fe-167">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD 
  ```

<span data-ttu-id="660fe-168">Se richiesto sull'installazione di un modulo da un archivio non attendibile, digitare **s** e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="660fe-168">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>


### <a name="step-2-connect-to-office-365"></a><span data-ttu-id="660fe-169">Passaggio 2: Connettersi a Office 365</span><span class="sxs-lookup"><span data-stu-id="660fe-169">Step 2: Connect to Office 365</span></span>

<span data-ttu-id="660fe-170">Per connettersi alla sottoscrizione Office 365 con un *nome di account e password*:</span><span class="sxs-lookup"><span data-stu-id="660fe-170">To connect to your Office 365 subscription with an *account name and password*:</span></span>
    
```
$UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
```

<span data-ttu-id="660fe-171">Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell** digitare il lavoro di Office 365 o nome utente dell'account scuola e la password e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="660fe-171">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="660fe-172">Per connettersi alla sottoscrizione Office 365 con *l'autenticazione a più fattori (MFA)*:</span><span class="sxs-lookup"><span data-stu-id="660fe-172">To connect to your Office 365 subscription with *multi-factor authentication (MFA)*:</span></span>

```
Connect-AzureAD
```

<span data-ttu-id="660fe-173">Nella finestra di dialogo **Azure Active Directory PowerShell** digitare il lavoro di Office 365 o nome utente dell'account scuola e la password e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="660fe-173">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
<span data-ttu-id="660fe-174">Seguire le istruzioni nella finestra di dialogo **Azure Active Directory PowerShell** per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="660fe-174">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
<span data-ttu-id="660fe-175">Dopo la connessione, è possibile utilizzare i cmdlet di nuovi per [Azure Active Directory PowerShell modulo grafico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="660fe-175">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="660fe-176">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="660fe-176">See also</span></span>

- [<span data-ttu-id="660fe-177">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="660fe-177">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="660fe-178">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="660fe-178">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="660fe-179">Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="660fe-179">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="660fe-180">Ottieni credenziali</span><span class="sxs-lookup"><span data-stu-id="660fe-180">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="660fe-181">Connettere-MsolService</span><span class="sxs-lookup"><span data-stu-id="660fe-181">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

