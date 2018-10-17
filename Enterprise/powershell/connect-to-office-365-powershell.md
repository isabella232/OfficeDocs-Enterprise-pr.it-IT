---
title: Connettersi a PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
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
description: "Riepilogo: Connettersi all'organizzazione Office 365 con Office 365 PowerShell per eseguire attività di interfaccia di amministrazione da riga di comando."
ms.openlocfilehash: e35dfd48f86cd4767f2e87786c4a6d1ea3aa608b
ms.sourcegitcommit: 22db89d5b13f7d85e03f35f21f25fa288aadf1b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2018
ms.locfileid: "25575280"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="362e1-103">Connettersi a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="362e1-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="362e1-104">**Riepilogo:** Connettersi all'organizzazione Office 365 con Office 365 PowerShell per eseguire attività di amministrazione da riga di comando.</span><span class="sxs-lookup"><span data-stu-id="362e1-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="362e1-p101">Office 365 PowerShell consente di gestire le impostazioni di Office 365 dalla riga di comando. Connessione a Office 365 PowerShell è una semplice procedura di cui si installa il software necessario e quindi connettersi all'organizzazione Office 365.</span><span class="sxs-lookup"><span data-stu-id="362e1-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="362e1-107">Esistono due versioni del modulo di PowerShell utilizzabile per connettersi a Office 365 e amministrare le licenze, gruppi e gli account utente:</span><span class="sxs-lookup"><span data-stu-id="362e1-107">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="362e1-108">Azure Active Directory PowerShell di grafico (cmdlet includono **AzureAD** nel nome)</span><span class="sxs-lookup"><span data-stu-id="362e1-108">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span> 
- <span data-ttu-id="362e1-109">Microsoft Azure Active Directory Module per Windows PowerShell (cmdlet includono **MSol** nel nome)</span><span class="sxs-lookup"><span data-stu-id="362e1-109">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="362e1-p102">Alla data attuale di questo articolo, Azure Active Directory PowerShell modulo grafico non sostituisce completamente la funzionalità nei cmdlet della funzionalità di Microsoft Azure Active Directory Module per Windows PowerShell per utente, gruppo e amministrazione di licenza . In molti casi, è necessario utilizzare entrambe le versioni. È possibile installare correttamente entrambe le versioni nello stesso computer.</span><span class="sxs-lookup"><span data-stu-id="362e1-p102">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration. In many cases, you need to use both versions. You can safely install both versions on the same computer.</span></span>

> [!TIP]
> <span data-ttu-id="362e1-p103">**Nuovo PowerShell?** Visualizzare una [Panoramica video di PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)per offerto da Learning LinkedIn.</span><span class="sxs-lookup"><span data-stu-id="362e1-p103">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="362e1-115">Che cosa è necessario sapere prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="362e1-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="362e1-116">Tempo stimato per il completamento: 5 minuti</span><span class="sxs-lookup"><span data-stu-id="362e1-116">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="362e1-117">È possibile utilizzare le seguenti versioni di Windows:</span><span class="sxs-lookup"><span data-stu-id="362e1-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="362e1-118">Windows 10, Windows 8.1, Windows 8 o Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="362e1-118">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="362e1-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="362e1-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="362e1-p104">Utilizzare una versione a 64 bit di Windows. È stato rimosso il supporto per la versione a 32 bit di Microsoft Azure Active Directory Module per Windows PowerShell ottobre del 2014.</span><span class="sxs-lookup"><span data-stu-id="362e1-p104">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="362e1-p105">Queste procedure sono progettate per gli utenti che sono membri di un ruolo di amministrazione di Office 365. Per ulteriori informazioni, vedere [ruoli di amministratore su Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="362e1-p105">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="362e1-124">Collegarsi con Azure Active Directory PowerShell modulo grafico</span><span class="sxs-lookup"><span data-stu-id="362e1-124">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="362e1-125">Comandi del modulo di [Azure Active Directory PowerShell di grafico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) hanno **AzureAD** nel loro nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="362e1-125">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="362e1-126">Per le procedure necessarie per i nuovi cmdlet di Azure Active Directory PowerShell modulo grafico, utilizzare la procedura seguente per installare il modulo ed eseguire la connessione alla sottoscrizione Office 365.</span><span class="sxs-lookup"><span data-stu-id="362e1-126">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="362e1-127">Per informazioni sul supporto per diverse versioni di Microsoft Windows, vedere [Azure Active Directory PowerShell modulo grafico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) .</span><span class="sxs-lookup"><span data-stu-id="362e1-127">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="362e1-128">Passaggio 1: Installazione del software necessario</span><span class="sxs-lookup"><span data-stu-id="362e1-128">Step 1: Install required software</span></span>

<span data-ttu-id="362e1-p106">È sufficiente effettuare questa procedura solo una volta, non ogni volta che ci si connette. Tuttavia, probabilmente sarà necessario installare periodicamente le versioni più recenti del software.</span><span class="sxs-lookup"><span data-stu-id="362e1-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="362e1-131">Aprire un prompt dei comandi di Windows PowerShell con privilegi elevati (eseguire Windows PowerShell come amministratore).</span><span class="sxs-lookup"><span data-stu-id="362e1-131">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="362e1-132">Nella **amministratore: Windows PowerShell** finestra prompt dei comandi eseguita il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="362e1-132">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="362e1-133">Se richiesto sull'installazione di un modulo da un archivio non attendibile, digitare **s** e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="362e1-133">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="362e1-134">Passaggio 2: Connettersi a Azure Active Directory per la sottoscrizione a Office 365</span><span class="sxs-lookup"><span data-stu-id="362e1-134">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="362e1-135">Per connettersi a Azure Active Directory per la sottoscrizione a Office 365 con un nome di account e una password o con *l'autenticazione a più fattori (MFA)*, eseguire questo comando da un prompt dei comandi di Windows PowerShell (non è necessario essere con privilegi elevati):</span><span class="sxs-lookup"><span data-stu-id="362e1-135">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run this command from a Windows PowerShell command prompt (it does not have to be elevated):</span></span>
    
```
Connect-AzureAD
```

<span data-ttu-id="362e1-136">Nella finestra di dialogo **accesso all'account** , digitare il lavoro di Office 365 o nome utente dell'account scuola e la password e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="362e1-136">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="362e1-137">Se si utilizza MFA, seguire le istruzioni nelle finestre di dialogo aggiuntive per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica.</span><span class="sxs-lookup"><span data-stu-id="362e1-137">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>
    
<span data-ttu-id="362e1-138">Dopo la connessione, è possibile utilizzare i cmdlet di nuovi per [Azure Active Directory PowerShell modulo grafico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="362e1-138">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="362e1-139">Connessione con il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="362e1-139">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="362e1-140">I comandi di Microsoft Azure Active Directory Module per Windows PowerShell dispongono **Msol** nel loro nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="362e1-140">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="362e1-141">Passaggio 1: Installazione del software necessario</span><span class="sxs-lookup"><span data-stu-id="362e1-141">Step 1: Install required software</span></span>

<span data-ttu-id="362e1-p107">È sufficiente effettuare questa procedura solo una volta, non ogni volta che ci si connette. Tuttavia, probabilmente sarà necessario installare periodicamente le versioni più recenti del software.</span><span class="sxs-lookup"><span data-stu-id="362e1-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="362e1-144">Installare la versione a 64 bit dell'Assistente di accesso a Microsoft Online Services: [Microsoft Online Services Assistente per l'accesso per RTW i professionisti IT](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="362e1-144">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="362e1-145">Installare il Microsoft Azure Active Directory Module per Windows PowerShell con la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="362e1-145">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="362e1-146">Aprire un prompt dei comandi di Windows PowerShell con privilegi elevati (eseguire Windows PowerShell come amministratore).</span><span class="sxs-lookup"><span data-stu-id="362e1-146">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="362e1-147">Eseguire il comando **Install-modulo MSOnline** .</span><span class="sxs-lookup"><span data-stu-id="362e1-147">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="362e1-148">Se viene richiesto di installare il provider NuGet, digitare **s** e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="362e1-148">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="362e1-149">Se viene richiesto di installare il modulo da PSGallery, digitare **s** e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="362e1-149">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="362e1-150">Passaggio 2: Connettersi a Azure Active Directory per la sottoscrizione a Office 365</span><span class="sxs-lookup"><span data-stu-id="362e1-150">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="362e1-151">Per connettersi a Azure Active Directory per la sottoscrizione a Office 365 con un nome di account e una password o con *l'autenticazione a più fattori (MFA)*, eseguire questo comando da un prompt dei comandi di Windows PowerShell (non è necessario essere con privilegi elevati):</span><span class="sxs-lookup"><span data-stu-id="362e1-151">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run this command from a Windows PowerShell command prompt (it does not have to be elevated):</span></span>
    
```
Connect-MsolService
```

<span data-ttu-id="362e1-152">Nella finestra di dialogo **accesso all'account** , digitare il lavoro di Office 365 o nome utente dell'account scuola e la password e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="362e1-152">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="362e1-153">Se si utilizza MFA, seguire le istruzioni nelle finestre di dialogo aggiuntive per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica.</span><span class="sxs-lookup"><span data-stu-id="362e1-153">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

    
### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="362e1-154">Come verificare se l'operazione ha avuto esito positivo</span><span class="sxs-lookup"><span data-stu-id="362e1-154">How do you know this worked?</span></span>

<span data-ttu-id="362e1-p108">Se non di errori, l'utente connesso correttamente. Una prova veloce consiste nell'eseguire un cmdlet di Office 365, ad esempio, **Get-MsolUser** - e visualizzare i risultati.</span><span class="sxs-lookup"><span data-stu-id="362e1-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="362e1-157">Se non vengono visualizzati errori, controllare i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="362e1-157">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="362e1-p109">**Un problema comune è rappresentato da una password errata**. Ripetere il passaggio 3 e prestare particolare attenzione al nome utente e alla password immessi.</span><span class="sxs-lookup"><span data-stu-id="362e1-p109">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="362e1-p110">\* *The Microsoft Azure Active Directory Module per Windows PowerShell è necessario Microsoft .NET Framework 3.5.* funzione x \* è abilitata per il computer \* *. È probabile che il computer sia installata una versione più recente (ad esempio, 4 o 4.5.* x \*), ma con le versioni precedenti la compatibilità con le versioni precedenti di .NET Framework può essere attivata o disattivata. Per ulteriori informazioni, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="362e1-p110">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="362e1-163">Per Windows Server 2012 o Windows Server 2012 R2, vedere [abilitare .NET Framework 3.5 con l'aggiunta di ruoli e guidata funzionalità](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="362e1-163">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="362e1-164">Per Windows 7 o Windows Server 2008 R2, vedere [non è possibile aprire il Azure Active Directory Module per Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="362e1-164">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="362e1-165">Per Windows 10, Windows 8.1 e Windows 8, vedere [installare .NET Framework 3.5 10 Windows, Windows 8.1, e Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span><span class="sxs-lookup"><span data-stu-id="362e1-165">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="362e1-p111">**La versione del Microsoft Azure Active Directory Module per Windows PowerShell potrebbe non essere aggiornata.** Per controllare, eseguire il comando seguente in Office 365 PowerShell o il Microsoft Azure Active Directory Module per Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="362e1-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="362e1-168">Se il numero di versione restituito è inferiore al valore 1.0.8070.2, disinstallare il Microsoft Azure Active Directory Module per Windows PowerShell e installare la versione più recente dal collegamento al passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="362e1-168">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="362e1-169">**Se si riceve un errore di connessione, vedere l'argomento:** ["Connect-MsolService: eccezione di tipo" errore](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="362e1-169">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="362e1-170">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="362e1-170">See also</span></span>

- [<span data-ttu-id="362e1-171">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="362e1-171">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="362e1-172">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="362e1-172">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="362e1-173">Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="362e1-173">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="362e1-174">Ottieni credenziali</span><span class="sxs-lookup"><span data-stu-id="362e1-174">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="362e1-175">Connettere-MsolService</span><span class="sxs-lookup"><span data-stu-id="362e1-175">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

