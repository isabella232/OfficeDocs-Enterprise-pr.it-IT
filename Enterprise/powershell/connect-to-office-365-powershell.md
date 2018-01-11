---
title: Connettersi a PowerShell di Office 365
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
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: "Riepilogo: Connettersi all'organizzazione Office 365 con Office 365 PowerShell per eseguire attività di Office 365 admin center dalla riga di comando."
ms.openlocfilehash: 942c128d8cfbcf4e78f054a0ab3a51b05173073f
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="b60ab-103">Connettersi a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="b60ab-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="b60ab-104">**Riepilogo:** Connettersi all'organizzazione Office 365 con Office 365 PowerShell per eseguire attività di amministrazione di Office 365 dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="b60ab-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform Office 365 administration tasks from the command line.</span></span>
  
<span data-ttu-id="b60ab-p101">Office 365 PowerShell consente di gestire le impostazioni di Office 365 dalla riga di comando. Connessione a Office 365 PowerShell è una semplice tre passaggi cui installare il software necessario, eseguire il software necessario e quindi connettersi all'organizzazione Office 365.</span><span class="sxs-lookup"><span data-stu-id="b60ab-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="b60ab-107">Notare che queste istruzioni di connessione sono identiche a quelle nell'argomento [Azure Active Directory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).</span><span class="sxs-lookup"><span data-stu-id="b60ab-107">Note that these connection instructions are the same as those in the topic [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).</span></span>
  
> [!TIP]
> <span data-ttu-id="b60ab-p102">**Nuovo PowerShell?** Visualizzare una [Panoramica video di PowerShell](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)per offerto da Learning LinkedIn.</span><span class="sxs-lookup"><span data-stu-id="b60ab-p102">**New to PowerShell?** See a [video Overview of PowerShell](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="b60ab-110">Che cosa è necessario sapere prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="b60ab-110">What do you need to know before you begin?</span></span>

- <span data-ttu-id="b60ab-111">Tempo stimato per il completamento: 5 minuti</span><span class="sxs-lookup"><span data-stu-id="b60ab-111">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="b60ab-112">È possibile utilizzare le seguenti versioni di Windows:</span><span class="sxs-lookup"><span data-stu-id="b60ab-112">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="b60ab-113">10 Windows, Windows 8.1, Windows 8 o Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="b60ab-113">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="b60ab-114">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="b60ab-114">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="b60ab-p103">Utilizzare una versione a 64 bit di Windows. È stato rimosso il supporto per la versione a 32 bit di Microsoft Azure Active Directory Module per Windows PowerShell ottobre del 2014.</span><span class="sxs-lookup"><span data-stu-id="b60ab-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="b60ab-p104">Office 365 di lavoro o scuola che l'account utilizzato per queste procedure esigenze per essere un membro di un ruolo di amministrazione di Office 365. Per ulteriori informazioni, vedere [ruoli di amministratore su Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="b60ab-p104">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>
    
## <a name="step-1-install-required-software"></a><span data-ttu-id="b60ab-119">Passaggio 1: Installazione del software necessario</span><span class="sxs-lookup"><span data-stu-id="b60ab-119">Step 1: Install required software</span></span>

<span data-ttu-id="b60ab-p105">È sufficiente effettuare questa procedura solo una volta, non ogni volta che ci si connette. Tuttavia, probabilmente sarà necessario installare periodicamente le versioni più recenti del software.</span><span class="sxs-lookup"><span data-stu-id="b60ab-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="b60ab-122">Installare la versione a 64 bit dell'Assistente di accesso a Microsoft Online Services: [Microsoft Online Services Assistente per l'accesso per RTW i professionisti IT](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="b60ab-122">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="b60ab-123">Installare la versione a 64 bit del Microsoft Azure Active Directory Module per Windows PowerShell con la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="b60ab-123">Install the 64-bit version of the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="b60ab-124">Aprire la pagina web di [Connessione di Azure Active Directory](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185) .</span><span class="sxs-lookup"><span data-stu-id="b60ab-124">Open the [Azure Active Directory Connection](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185) web page.</span></span>
    
  - <span data-ttu-id="b60ab-125">Nella parte inferiore della pagina di **Download di file** , fare clic su **Download** del file **AdministrationConfig-V1.1.166.0-GA.msi** e quindi installare.</span><span class="sxs-lookup"><span data-stu-id="b60ab-125">In **Files in Download** at the bottom of the page, click **Download** for the **AdministrationConfig-V1.1.166.0-GA.msi** file, and then install it.</span></span>
    
## <a name="step-2-open-the-windows-azure-active-directory-module"></a><span data-ttu-id="b60ab-126">Passaggio 2: Apertura del modulo di Windows Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="b60ab-126">Step 2: Open the Windows Azure Active Directory Module</span></span>

1. <span data-ttu-id="b60ab-127">Trovare e aprire il Microsoft Azure Active Directory Module per Windows PowerShell con uno dei metodi seguenti in base alla versione di Windows:</span><span class="sxs-lookup"><span data-stu-id="b60ab-127">Find and open the Microsoft Azure Active Directory Module for Windows PowerShell by using one of the following methods based on your version of Windows:</span></span>
    
  - <span data-ttu-id="b60ab-128">**Menu di avvio** Sul desktop fare clic sul pulsante **Start**e quindi digitare Azure.</span><span class="sxs-lookup"><span data-stu-id="b60ab-128">**Start menu** From the desktop, click **Start**, and then type Azure.</span></span>
    
  - <span data-ttu-id="b60ab-129">**Menu Start n** Ricerca forAzure utilizzando uno dei seguenti metodi:</span><span class="sxs-lookup"><span data-stu-id="b60ab-129">**No Start menu** Search forAzure using any of these methods:</span></span>
    
  - <span data-ttu-id="b60ab-130">Nella schermata Start fare clic su un'area vuota e digitare Azure.</span><span class="sxs-lookup"><span data-stu-id="b60ab-130">On the Start screen, click an empty area, and type Azure.</span></span>
    
  - <span data-ttu-id="b60ab-p106">Nella schermata Start o il desktop, premere Windows chiave + Q. L'accesso alla ricerca, digitare Azure.</span><span class="sxs-lookup"><span data-stu-id="b60ab-p106">On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Azure.</span></span>
    
  - <span data-ttu-id="b60ab-p107">Nella schermata Start o il desktop, spostare il cursore all'angolo superiore destro o scorrere rapidamente dal bordo destro dello schermo per visualizzare gli accessi da sinistra. Selezionare l'accesso alla ricerca e digitare **Azure**.</span><span class="sxs-lookup"><span data-stu-id="b60ab-p107">On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and type **Azure**.</span></span>
    
2. <span data-ttu-id="b60ab-135">Nei risultati, fare clic su **Microsoft Azure Active Directory Module per Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="b60ab-135">In the results, click **Microsoft Azure Active Directory Module for Windows PowerShell**.</span></span>
    
## <a name="step-3-connect-to-your-office-365-subscription"></a><span data-ttu-id="b60ab-136">Passaggio 3: Connettere alla sottoscrizione Office 365</span><span class="sxs-lookup"><span data-stu-id="b60ab-136">Step 3: Connect to your Office 365 subscription</span></span>
<span data-ttu-id="b60ab-137"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="b60ab-137"></span></span>

<span data-ttu-id="b60ab-138">Per la connessione con solo un *nome di account e password* :</span><span class="sxs-lookup"><span data-stu-id="b60ab-138">To connect with just an  *account name and password*  :</span></span>
  
1. <span data-ttu-id="b60ab-139">Nella finestra di comando **Microsoft Azure Active Directory Module per Windows PowerShell** , eseguire i comandi seguenti.</span><span class="sxs-lookup"><span data-stu-id="b60ab-139">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following commands.</span></span>
    
  ```
  $UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
  ```

2. <span data-ttu-id="b60ab-140">Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell** digitare il lavoro di Office 365 o nome utente dell'account scuola e la password e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="b60ab-140">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="b60ab-141">Per la connessione con *l'autenticazione a più fattori (MFA)* :</span><span class="sxs-lookup"><span data-stu-id="b60ab-141">To connect with  *multi-factor authentication (MFA)*  :</span></span>
  
1. <span data-ttu-id="b60ab-142">Nella finestra di comando **Microsoft Azure Active Directory Module per Windows PowerShell** eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="b60ab-142">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following command.</span></span>
    
  ```
  Connect-MsolService
  ```

2. <span data-ttu-id="b60ab-143">Nella finestra di dialogo **Azure Active Directory PowerShell** digitare il lavoro di Office 365 o nome utente dell'account scuola e la password e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="b60ab-143">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
3. <span data-ttu-id="b60ab-144">Seguire le istruzioni nella finestra di dialogo **Azure Active Directory PowerShell** per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="b60ab-144">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="b60ab-145">Come verificare se l'operazione ha avuto esito positivo</span><span class="sxs-lookup"><span data-stu-id="b60ab-145">How do you know this worked?</span></span>
<span data-ttu-id="b60ab-146"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="b60ab-146"></span></span>

<span data-ttu-id="b60ab-p108">Se non di errori, l'utente connesso correttamente. Una prova veloce consiste nell'eseguire un cmdlet di Office 365, ad esempio, **Get-MsolUser** - e visualizzare i risultati.</span><span class="sxs-lookup"><span data-stu-id="b60ab-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="b60ab-149">Se non vengono visualizzati errori, controllare i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="b60ab-149">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="b60ab-p109">**Un problema comune è una password non corretta**. Eseguire di nuovo passaggio 3. e prestare particolare attenzione per il nome utente e la password che immessi.</span><span class="sxs-lookup"><span data-stu-id="b60ab-p109">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="b60ab-p110">**I Microsoft Azure Active Directory Module per Windows PowerShell è necessario Microsoft .NET Framework 3.5. _x_ è attivata nel computer in uso**. È probabile che il computer dispone di una versione più recente installata (ad esempio, 4 o 4.5. _x_), ma con le versioni precedenti la compatibilità con le versioni precedenti di .NET Framework può essere attivata o disattivata. Per ulteriori informazioni, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="b60ab-p110">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5. _x_ feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5. _x_), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="b60ab-157">Per Windows Server 2012 o Windows Server 2012 R2, vedere [abilitare .NET Framework 3.5 con l'aggiunta di ruoli e guidata funzionalità](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="b60ab-157">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="b60ab-158">Per Windows 8 o Windows 8.1, vedere [installazione di .NET Framework 3.5 in Windows 8 o 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span><span class="sxs-lookup"><span data-stu-id="b60ab-158">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="b60ab-159">Per Windows 7 o Windows Server 2008 R2, vedere [non è possibile aprire il Azure Active Directory Module per Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="b60ab-159">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>
    
- <span data-ttu-id="b60ab-p111">**La versione del Microsoft Azure Active Directory Module per Windows PowerShell potrebbe non essere aggiornata.** Per controllare, eseguire il comando seguente in Office 365 PowerShell o il Microsoft Azure Active Directory Module per Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b60ab-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="b60ab-162">Se il numero di versione restituito è inferiore al valore 1.0.8070.2, disinstallare il Microsoft Azure Active Directory Module per Windows PowerShell e installare la versione più recente dal collegamento al passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="b60ab-162">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="b60ab-163">**Se si riceve un errore di connessione, vedere l'argomento:** ["Connect-MsolService: eccezione di tipo" errore](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="b60ab-163">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a><span data-ttu-id="b60ab-164">Connettersi con il modulo Azure Active Directory V2 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b60ab-164">Connect with the Azure Active Directory V2 PowerShell module</span></span>
<span data-ttu-id="b60ab-165"><a name="ConnectV2"> </a></span><span class="sxs-lookup"><span data-stu-id="b60ab-165"></span></span>

<span data-ttu-id="b60ab-166">Per le procedure necessarie per i nuovi cmdlet nel [modulo di Azure Active Directory V2 PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory), utilizzare la procedura seguente per installare il modulo ed eseguire la connessione alla sottoscrizione Office 365:</span><span class="sxs-lookup"><span data-stu-id="b60ab-166">For procedures that require the new cmdlets in the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory), use these steps to install the module and connect to your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="b60ab-167">Aprire un prompt dei comandi di Windows PowerShell con privilegi elevati (eseguire Windows PowerShell come amministratore).</span><span class="sxs-lookup"><span data-stu-id="b60ab-167">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="b60ab-168">Nella **amministratore: Windows PowerShell** finestra prompt dei comandi eseguita il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="b60ab-168">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD 
  ```

<span data-ttu-id="b60ab-169">Se richiesto sull'installazione di un modulo da un archivio non attendibile, digitare **s** e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="b60ab-169">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>
    
3. <span data-ttu-id="b60ab-170">Una volta completata l'installazione del nuovo modulo, utilizzare questi comandi per connettersi alla sottoscrizione di Office 365:</span><span class="sxs-lookup"><span data-stu-id="b60ab-170">When the installation of the new module is complete, use these commands to connect to your Office 365 subscription:</span></span>
    
  -  <span data-ttu-id="b60ab-171">Con un *nome di account e password* :</span><span class="sxs-lookup"><span data-stu-id="b60ab-171">With an *account name and password*  :</span></span>
    
  ```
  $UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
  ```

 <span data-ttu-id="b60ab-172">Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell** digitare il lavoro di Office 365 o nome utente dell'account scuola e la password e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="b60ab-172">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
  - <span data-ttu-id="b60ab-173">Con l' *autenticazione a più fattori (MFA)* :</span><span class="sxs-lookup"><span data-stu-id="b60ab-173">With  *multi-factor authentication (MFA)*  :</span></span>
    
  ```
  Connect-AzureAD
  ```

<span data-ttu-id="b60ab-174">Nella finestra di dialogo **Azure Active Directory PowerShell** digitare il lavoro di Office 365 o nome utente dell'account scuola e la password e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="b60ab-174">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
<span data-ttu-id="b60ab-175">Seguire le istruzioni nella finestra di dialogo **Azure Active Directory PowerShell** per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="b60ab-175">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
<span data-ttu-id="b60ab-176">Dopo la connessione, è possibile utilizzare i cmdlet di nuovi il [modulo di Azure Active Directory V2 PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="b60ab-176">After connecting, you can use the new cmdlets for the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b60ab-177">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b60ab-177">See also</span></span>

#### 

[<span data-ttu-id="b60ab-178">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="b60ab-178">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="b60ab-179">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="b60ab-179">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="b60ab-180">Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b60ab-180">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
#### 

[<span data-ttu-id="b60ab-181">Ottieni credenziali</span><span class="sxs-lookup"><span data-stu-id="b60ab-181">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[<span data-ttu-id="b60ab-182">Connettere-MsolService</span><span class="sxs-lookup"><span data-stu-id="b60ab-182">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

