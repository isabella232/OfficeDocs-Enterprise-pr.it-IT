---
title: Connettersi a PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/30/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: "Riepilogo: connettersi all'organizzazione di Office 365 con PowerShell di Office 365 per eseguire le attività dell'interfaccia di amministrazione dalla riga di comando."
ms.openlocfilehash: c5bf5204d8ca1c8db35635f080031838e9fbea03
ms.sourcegitcommit: 86a740dccf273d679a8938e11e60d2a497c01689
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/30/2019
ms.locfileid: "37328154"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="b8a2d-103">Connettersi a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="b8a2d-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="b8a2d-104">**Riepilogo:** connettersi all'organizzazione di Office 365 con PowerShell di Office 365 per eseguire le attività dell'interfaccia di amministrazione dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="b8a2d-p101">PowerShell di Office 365 consente di gestire le impostazioni di Office 365 dalla riga di comando. Connettersi a PowerShell di Office 365 è un processo semplice che consiste nell'installare il software necessario e successivamente connettersi all'organizzazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-p101">Office 365 PowerShell lets you manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="b8a2d-107">Sono disponibili due versioni del modulo di PowerShell da utilizzare per connettersi a Office 365 e gestire gli account utente, i gruppi e le licenze:</span><span class="sxs-lookup"><span data-stu-id="b8a2d-107">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="b8a2d-108">Azure Active Directory PowerShell per Graph (i cmdlet includono **AzureAD** nel nome)</span><span class="sxs-lookup"><span data-stu-id="b8a2d-108">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span> 
- <span data-ttu-id="b8a2d-109">Modulo di Microsoft Azure Active Directory per Windows PowerShell (i cmdlet includono **MSol** nel nome)</span><span class="sxs-lookup"><span data-stu-id="b8a2d-109">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="b8a2d-p102">A partire dalla data di pubblicazione di questo articolo, il modulo di Azure Active Directory PowerShell per Graph non sostituisce completamente le funzionalità nei cmdlet del Modulo di Microsoft Azure Active Directory per Windows PowerShell per l'amministrazione utenti, gruppi e licenze. In molti casi, è necessario usare entrambe le versioni. È possibile installare in modo sicuro entrambe le versioni sullo stesso computer.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-p102">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration. In many cases, you need to use both versions. You can safely install both versions on the same computer.</span></span>

> [!TIP]
> <span data-ttu-id="b8a2d-p103">**Nuovo utente di PowerShell?** È disponibile una [Panoramica video di PowerShell](https://support.office.com/it-IT/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), grazie a LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-p103">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/it-IT/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="b8a2d-115">Che cosa è necessario sapere prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="b8a2d-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="b8a2d-116">Tempo stimato per il completamento: 5 minuti</span><span class="sxs-lookup"><span data-stu-id="b8a2d-116">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="b8a2d-117">È possibile utilizzare le seguenti versioni di Windows:</span><span class="sxs-lookup"><span data-stu-id="b8a2d-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="b8a2d-118">Windows 10, Windows 8.1, Windows 8 o Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="b8a2d-118">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="b8a2d-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="b8a2d-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>

    > [!NOTE]
    > <span data-ttu-id="b8a2d-120">È necessario usare PowerShell 5.1 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-120">You must use PowerShell version 5.1 or later.</span></span> <span data-ttu-id="b8a2d-121">Per Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012 e Windows Server 2008 R2 SP1, scaricare e installare [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span><span class="sxs-lookup"><span data-stu-id="b8a2d-121">For Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012, and Windows Server 2008 R2 SP1, download and install the [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span></span> 
    
    > [!NOTE]
    ><span data-ttu-id="b8a2d-p105">Usare una versione a 64 bit di Windows. A ottobre del 2014 è stato sospeso il supporto per la versione a 32 bit del Modulo di Microsoft Azure Active Directory per Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-p105">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="b8a2d-p106">Queste procedure sono destinate agli utenti che sono membri di un ruolo di amministratore di Office 365. Per ulteriori informazioni, vedere [Informazioni sui ruoli di amministratore di Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="b8a2d-p106">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="b8a2d-126">Connettersi con il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="b8a2d-126">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="b8a2d-127">I comandi nel modulo di [Azure Active Directory PowerShell per Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) hanno **AzureAD** nel nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-127">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="b8a2d-128">Per le procedure che necessitano di nuovi cmdlet nel modulo di Azure Active Directory PowerShell per Graph, eseguire questi passaggi per installare il modulo e connettersi alla sottoscrizione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-128">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="b8a2d-129">Vedere [Modulo di Azure Active Directory PowerShell per Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) per informazioni sul supporto per le altre versioni di Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-129">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="b8a2d-130">Passaggio 1: installare il software necessario</span><span class="sxs-lookup"><span data-stu-id="b8a2d-130">Step 1: Install required software</span></span>

<span data-ttu-id="b8a2d-p107">È sufficiente effettuare questa procedura solo una volta, non ogni volta che ci si connette. Tuttavia, probabilmente sarà necessario installare periodicamente le versioni più recenti del software.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="b8a2d-133">Aprire un prompt dei comandi di Windows PowerShell con privilegi elevati (eseguire Windows PowerShell come amministratore).</span><span class="sxs-lookup"><span data-stu-id="b8a2d-133">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="b8a2d-134">Nella finestra di comando **Amministratore: Windows PowerShell**, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="b8a2d-134">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="b8a2d-135">Se viene richiesto di installare un modulo da un archivio non attendibile, digitare **Y** e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-135">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="b8a2d-136">Passaggio 2: connettersi ad Azure AD per la sottoscrizione a Office 365</span><span class="sxs-lookup"><span data-stu-id="b8a2d-136">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="b8a2d-137">Per connettersi ad Azure AD per la sottoscrizione a Office 365 con un nome dell'account e una password o con l'*autenticazione a più fattori (MFA)*, eseguire uno di questi comandi da un prompt dei comandi di Windows PowerShell (che non sia con privilegi elevati).</span><span class="sxs-lookup"><span data-stu-id="b8a2d-137">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="b8a2d-138">**Cloud di Office 365**</span><span class="sxs-lookup"><span data-stu-id="b8a2d-138">**Office 365 cloud**</span></span> | <span data-ttu-id="b8a2d-139">**Comando**</span><span class="sxs-lookup"><span data-stu-id="b8a2d-139">**Command**</span></span> |
| <span data-ttu-id="b8a2d-140">Office 365 internazionale (+GCC)</span><span class="sxs-lookup"><span data-stu-id="b8a2d-140">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="b8a2d-141">Office 365 gestito da 21 Vianet</span><span class="sxs-lookup"><span data-stu-id="b8a2d-141">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="b8a2d-142">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="b8a2d-142">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="b8a2d-143">U.S. Government DoD di Office 365 e U.S. Government GCC High di Office 365</span><span class="sxs-lookup"><span data-stu-id="b8a2d-143">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="b8a2d-144">Nella finestra di dialogo per **accedere all'account**, digitare nome utente e password dell'account dell'istituto di istruzione o aziendale di Office 365, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-144">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="b8a2d-145">Se si utilizza l'autenticazione a più fattori, seguire le istruzioni nelle finestre di dialogo aggiuntive per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-145">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>


<span data-ttu-id="b8a2d-146">Dopo aver eseguito la connessione, è possibile utilizzare i nuovi cmdlet per il [modulo di Azure Active Directory PowerShell per Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="b8a2d-146">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="b8a2d-147">Connettersi con il Modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8a2d-147">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="b8a2d-148">I comandi nel Modulo di Microsoft Azure Active Directory per Windows PowerShell hanno **MSol** nel nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-148">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="b8a2d-149">Passaggio 1: installare il software necessario</span><span class="sxs-lookup"><span data-stu-id="b8a2d-149">Step 1: Install required software</span></span>

<span data-ttu-id="b8a2d-p108">È sufficiente effettuare questa procedura solo una volta, non ogni volta che ci si connette. Tuttavia, probabilmente sarà necessario installare periodicamente le versioni più recenti del software.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-p108">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="b8a2d-152">Installare la versione a 64 bit dell'Assistente per l'accesso ai Microsoft Online Services: [Assistente per l'accesso ai Microsoft Online Services per professionisti IT - RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="b8a2d-152">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="b8a2d-153">Installare il Modulo di Microsoft Azure Active Directory per Windows PowerShell con la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="b8a2d-153">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="b8a2d-154">Aprire un prompt dei comandi di Windows PowerShell con privilegi elevati (eseguire Windows PowerShell come amministratore).</span><span class="sxs-lookup"><span data-stu-id="b8a2d-154">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="b8a2d-155">Eseguire il comando **Install-Module MSOnline**.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-155">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="b8a2d-156">Se viene richiesto di installare il provider NuGet, digitare **Y** e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-156">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="b8a2d-157">Se viene richiesto di installare il modulo da PSGallery, digitare **Y** e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-157">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="b8a2d-158">Passaggio 2: connettersi ad Azure AD per la sottoscrizione a Office 365</span><span class="sxs-lookup"><span data-stu-id="b8a2d-158">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="b8a2d-159">Per connettersi ad Azure AD per la sottoscrizione a Office 365 con un nome dell'account e una password o con l'*autenticazione a più fattori (MFA)*, eseguire uno di questi comandi da un prompt dei comandi di Windows PowerShell (che non sia con privilegi elevati).</span><span class="sxs-lookup"><span data-stu-id="b8a2d-159">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="b8a2d-160">**Cloud di Office 365**</span><span class="sxs-lookup"><span data-stu-id="b8a2d-160">**Office 365 cloud**</span></span> | <span data-ttu-id="b8a2d-161">**Comando**</span><span class="sxs-lookup"><span data-stu-id="b8a2d-161">**Command**</span></span> |
| <span data-ttu-id="b8a2d-162">Office 365 internazionale (+GCC)</span><span class="sxs-lookup"><span data-stu-id="b8a2d-162">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="b8a2d-163">Office 365 gestito da 21 Vianet</span><span class="sxs-lookup"><span data-stu-id="b8a2d-163">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="b8a2d-164">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="b8a2d-164">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="b8a2d-165">U.S. Government DoD di Office 365 e U.S. Government GCC High di Office 365</span><span class="sxs-lookup"><span data-stu-id="b8a2d-165">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="b8a2d-166">Nella finestra di dialogo per **accedere all'account**, digitare nome utente e password dell'account dell'istituto di istruzione o aziendale di Office 365, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-166">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="b8a2d-167">Se si utilizza l'autenticazione a più fattori, seguire le istruzioni nelle finestre di dialogo aggiuntive per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-167">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="b8a2d-168">Come verificare se l'operazione ha avuto esito positivo</span><span class="sxs-lookup"><span data-stu-id="b8a2d-168">How do you know this worked?</span></span>

<span data-ttu-id="b8a2d-p109">Se non vengono visualizzati errori vuol dire che la connessione è stata eseguita correttamente. Un breve test consiste nell'eseguire un cmdlet di Office 365 (ad esempio, **Get-MsolUser**) e vedere i risultati.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-p109">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="b8a2d-171">Se non vengono visualizzati errori, controllare i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="b8a2d-171">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="b8a2d-p110">**Un problema comune è rappresentato da una password errata**. Ripetere il passaggio 2 e prestare particolare attenzione al nome utente e alla password immessi.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-p110">**A common problem is an incorrect password**. Run Step 2 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="b8a2d-p111">**Il Modulo di Microsoft Azure Active Directory per Windows PowerShell richiede che la funzione Microsoft .NET Framework 3.5.* x* sia attiva sul computer in uso. È probabile che il computer disponga di una versione più recente (ad esempio, 4 o 4.5.\* x\*), ma la compatibilità con le versioni precedenti di .NET Framework può essere abilitata o disabilitata. Per ulteriori informazioni, vedere i seguenti argomenti:</span><span class="sxs-lookup"><span data-stu-id="b8a2d-p111">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="b8a2d-177">Per Windows Server 2012 o Windows Server 2012 R2, vedere [Abilitare .NET Framework 3.5 con Aggiunta guidata ruoli e funzionalità](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="b8a2d-177">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="b8a2d-178">Per Windows 7 o Windows Server 2008 R2, vedere [Impossibile aprire il Modulo di Azure Active Directory per Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="b8a2d-178">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="b8a2d-179">Per Windows 10, Windows 8.1 e Windows 8, vedere [Installare .NET Framework 3.5 in Windows 10, Windows 8.1 e Windows 8](https://docs.microsoft.com/it-IT/dotnet/framework/install/dotnet-35-windows-10)</span><span class="sxs-lookup"><span data-stu-id="b8a2d-179">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/it-IT/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="b8a2d-p112">**La versione del Modulo di Microsoft Azure Active Directory per Windows PowerShell potrebbe essere scaduta.** Per verificare, eseguire il comando seguente in PowerShell di Office 365 o nel Modulo di Microsoft Azure Active Directory per Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b8a2d-p112">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="b8a2d-182">Se il numero della versione restituito è inferiore al valore 1.0.8070.2, disinstallare il Modulo di Microsoft Azure Active Directory per Windows PowerShell e installare la versione più recente dal collegamento indicato nel passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="b8a2d-182">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="b8a2d-183">**Se viene visualizzato un errore di connessione, vedere l'argomento:** [Errore "La connessione-MsolService: eccezione di tipo"](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="b8a2d-183">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="b8a2d-184">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b8a2d-184">See also</span></span>

- [<span data-ttu-id="b8a2d-185">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="b8a2d-185">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="b8a2d-186">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="b8a2d-186">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="b8a2d-187">Effettuare la connessione a tutti i servizi di Office 365 in un'unica finestra di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8a2d-187">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="b8a2d-188">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="b8a2d-188">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="b8a2d-189">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="b8a2d-189">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

