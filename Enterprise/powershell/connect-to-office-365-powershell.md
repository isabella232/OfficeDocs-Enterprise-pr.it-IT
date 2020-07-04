---
title: Connettersi a PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/30/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Connettersi all'organizzazione di Office 365 con PowerShell di Office 365 per eseguire le attività dell'interfaccia di amministrazione dalla riga di comando.
ms.openlocfilehash: 0906da2b8773973236bc8cb6ef273d1a14528bfd
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997422"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="7d713-103">Connettersi a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="7d713-103">Connect to Office 365 PowerShell</span></span>

<span data-ttu-id="7d713-104">Office 365 PowerShell lets you manage your Office 365 settings from the command line.</span><span class="sxs-lookup"><span data-stu-id="7d713-104">Office 365 PowerShell lets you manage your Office 365 settings from the command line.</span></span> <span data-ttu-id="7d713-105">Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span><span class="sxs-lookup"><span data-stu-id="7d713-105">Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="7d713-106">Sono disponibili due versioni del modulo di PowerShell da utilizzare per connettersi a Office 365 e gestire gli account utente, i gruppi e le licenze:</span><span class="sxs-lookup"><span data-stu-id="7d713-106">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="7d713-107">Azure Active Directory PowerShell per Graph (i cmdlet includono **AzureAD** nel nome)</span><span class="sxs-lookup"><span data-stu-id="7d713-107">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span>
- <span data-ttu-id="7d713-108">Modulo di Microsoft Azure Active Directory per Windows PowerShell (i cmdlet includono **MSol** nel nome)</span><span class="sxs-lookup"><span data-stu-id="7d713-108">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="7d713-109">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration.</span><span class="sxs-lookup"><span data-stu-id="7d713-109">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration.</span></span> <span data-ttu-id="7d713-110">In many cases, you need to use both versions.</span><span class="sxs-lookup"><span data-stu-id="7d713-110">In many cases, you need to use both versions.</span></span> <span data-ttu-id="7d713-111">You can safely install both versions on the same computer.</span><span class="sxs-lookup"><span data-stu-id="7d713-111">You can safely install both versions on the same computer.</span></span>

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="7d713-112">Che cosa è necessario sapere prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="7d713-112">What do you need to know before you begin?</span></span>

<span data-ttu-id="7d713-113">È possibile utilizzare le seguenti versioni di Windows:</span><span class="sxs-lookup"><span data-stu-id="7d713-113">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="7d713-114">Windows 10, Windows 8.1, Windows 8 o Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="7d713-114">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="7d713-115">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="7d713-115">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>

    > [!NOTE]
    > <span data-ttu-id="7d713-116">Per il modulo Azure Active Directory PowerShell per Graph, è necessario usare PowerShell versione 5.1 o successive.</span><span class="sxs-lookup"><span data-stu-id="7d713-116">For the Azure Active Directory PowerShell for Graph module, you must use PowerShell version 5.1 or later.</span></span> <span data-ttu-id="7d713-117">Per il modulo di Microsoft Azure Active Directory per Windows PowerShell, è necessario usare PowerShell versione 5.1 o successive fino alla versione 6.</span><span class="sxs-lookup"><span data-stu-id="7d713-117">For the Microsoft Azure Active Directory Module for Windows PowerShell module, you must use PowerShell version 5.1 or later up to PowerShell version 6.</span></span> <span data-ttu-id="7d713-118">Non è possibile usare la versione 7 di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d713-118">You cannot use PowerShell version 7.</span></span> <span data-ttu-id="7d713-119">Per Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012 e Windows Server 2008 R2 SP1, scaricare e installare [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span><span class="sxs-lookup"><span data-stu-id="7d713-119">For Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012, and Windows Server 2008 R2 SP1, download and install the [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="7d713-120">Use a 64-bit version of Windows.</span><span class="sxs-lookup"><span data-stu-id="7d713-120">Use a 64-bit version of Windows.</span></span> <span data-ttu-id="7d713-121">Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span><span class="sxs-lookup"><span data-stu-id="7d713-121">Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
<span data-ttu-id="7d713-122">These procedures are intended for users who are members of an Office 365 admin role.</span><span class="sxs-lookup"><span data-stu-id="7d713-122">These procedures are intended for users who are members of an Office 365 admin role.</span></span> <span data-ttu-id="7d713-123">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="7d713-123">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="7d713-124">Connettersi con il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="7d713-124">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="7d713-125">I comandi nel modulo di Azure Active Directory PowerShell per Graph hanno **AzureAD** nel nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7d713-125">Commands in the Azure Active Directory PowerShell for Graph module have **AzureAD** in their cmdlet name.</span></span> <span data-ttu-id="7d713-126">È possibile installare il [modulo di Azure Active Directory PowerShell per Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) o [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.6.1).</span><span class="sxs-lookup"><span data-stu-id="7d713-126">You can install the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module or [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.6.1).</span></span>

<span data-ttu-id="7d713-127">Per le procedure che necessitano di nuovi cmdlet nel modulo di Azure Active Directory PowerShell per Graph, eseguire questi passaggi per installare il modulo e connettersi alla sottoscrizione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="7d713-127">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="7d713-128">Vedere [Modulo di Azure Active Directory PowerShell per Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) per informazioni sul supporto per le altre versioni di Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="7d713-128">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="7d713-129">Passaggio 1: installare il software necessario</span><span class="sxs-lookup"><span data-stu-id="7d713-129">Step 1: Install required software</span></span>

<span data-ttu-id="7d713-130">These steps are required once on your computer, not every time you connect.</span><span class="sxs-lookup"><span data-stu-id="7d713-130">These steps are required once on your computer, not every time you connect.</span></span> <span data-ttu-id="7d713-131">However, you'll likely need to install newer versions of the software periodically.</span><span class="sxs-lookup"><span data-stu-id="7d713-131">However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="7d713-132">Aprire un prompt dei comandi di Windows PowerShell con privilegi elevati (eseguire Windows PowerShell come amministratore).</span><span class="sxs-lookup"><span data-stu-id="7d713-132">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="7d713-133">Nella finestra di comando **Amministratore: Windows PowerShell**, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="7d713-133">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```powershell
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="7d713-134">Se viene richiesto di installare un modulo da un archivio non attendibile, digitare **Y** e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="7d713-134">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="7d713-135">Passaggio 2: connettersi ad Azure AD per la sottoscrizione a Office 365</span><span class="sxs-lookup"><span data-stu-id="7d713-135">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="7d713-136">Per connettersi ad Azure AD per la sottoscrizione a Office 365 con un nome dell'account e una password o con l'autenticazione a più fattori (MFA), eseguire uno di questi comandi da un prompt dei comandi di Windows PowerShell (che non sia con privilegi elevati).</span><span class="sxs-lookup"><span data-stu-id="7d713-136">To connect to Azure AD for your Office 365 subscription with an account name and password or with multi-factor authentication (MFA), run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="7d713-137">**Cloud di Office 365**</span><span class="sxs-lookup"><span data-stu-id="7d713-137">**Office 365 cloud**</span></span> | <span data-ttu-id="7d713-138">**Comando**</span><span class="sxs-lookup"><span data-stu-id="7d713-138">**Command**</span></span> |
| <span data-ttu-id="7d713-139">Office 365 internazionale (+GCC)</span><span class="sxs-lookup"><span data-stu-id="7d713-139">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="7d713-140">Office 365 gestito da 21 Vianet</span><span class="sxs-lookup"><span data-stu-id="7d713-140">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="7d713-141">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="7d713-141">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="7d713-142">U.S. Government DoD di Office 365 e U.S. Government GCC High di Office 365</span><span class="sxs-lookup"><span data-stu-id="7d713-142">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="7d713-143">Nella finestra di dialogo per **accedere all'account**, digitare nome utente e password dell'account dell'istituto di istruzione o aziendale di Office 365, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="7d713-143">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="7d713-144">Se si utilizza l'autenticazione a più fattori, seguire le istruzioni nelle finestre di dialogo aggiuntive per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica.</span><span class="sxs-lookup"><span data-stu-id="7d713-144">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

<span data-ttu-id="7d713-145">Dopo aver eseguito la connessione, è possibile utilizzare i cmdlet per il [modulo di Azure Active Directory PowerShell per Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="7d713-145">After connecting, you can use the cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="7d713-146">Connettersi con il Modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7d713-146">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="7d713-147">I comandi nel Modulo di Microsoft Azure Active Directory per Windows PowerShell hanno **MSol** nel nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7d713-147">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>

<span data-ttu-id="7d713-148">PowerShell versione 7 e successive non supportano il modulo di Microsoft Azure Active Directory per Windows PowerShell e i cmdlet con **MSOL** all'interno del nome.</span><span class="sxs-lookup"><span data-stu-id="7d713-148">PowerShell version 7 and later do not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="7d713-149">Per PowerShell versione 7 e successive, è necessario usare il modulo Azure Active Directory PowerShell per Graph o Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d713-149">For PowerShell version 7 and later, you must use the Azure Active Directory PowerShell for Graph module or Azure PowerShell.</span></span>

<span data-ttu-id="7d713-150">PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per Windows PowerShell e i cmdlet con **MSOL** all'interno del nome.</span><span class="sxs-lookup"><span data-stu-id="7d713-150">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="7d713-151">Per continuare a usare i cmdlet, è necessario eseguirli in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d713-151">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span> 
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="7d713-152">Passaggio 1: installare il software necessario</span><span class="sxs-lookup"><span data-stu-id="7d713-152">Step 1: Install required software</span></span>

<span data-ttu-id="7d713-153">These steps are required once on your computer, not every time you connect.</span><span class="sxs-lookup"><span data-stu-id="7d713-153">These steps are required once on your computer, not every time you connect.</span></span> <span data-ttu-id="7d713-154">However, you'll likely need to install newer versions of the software periodically.</span><span class="sxs-lookup"><span data-stu-id="7d713-154">However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="7d713-155">Se non si esegue Windows 10, installare la versione a 64 bit dell'assistente per l'accesso ai Microsoft Online Services: [Assistente per l'accesso ai Microsoft Online Services per professionisti IT RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="7d713-155">If you are not running Windows 10, install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="7d713-156">Installare il Modulo di Microsoft Azure Active Directory per Windows PowerShell con la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="7d713-156">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="7d713-157">Aprire un prompt dei comandi di Windows PowerShell con privilegi elevati (eseguire Windows PowerShell come amministratore).</span><span class="sxs-lookup"><span data-stu-id="7d713-157">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="7d713-158">Eseguire il comando **Install-Module MSOnline**.</span><span class="sxs-lookup"><span data-stu-id="7d713-158">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="7d713-159">Se viene richiesto di installare il provider NuGet, digitare **Y** e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="7d713-159">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="7d713-160">Se viene richiesto di installare il modulo da PSGallery, digitare **Y** e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="7d713-160">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="7d713-161">Passaggio 2: connettersi ad Azure AD per la sottoscrizione a Office 365</span><span class="sxs-lookup"><span data-stu-id="7d713-161">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="7d713-162">Per connettersi ad Azure AD per la sottoscrizione a Office 365 con un nome dell'account e una password o con l'autenticazione a più fattori (MFA), eseguire uno di questi comandi da un prompt dei comandi di Windows PowerShell (che non sia con privilegi elevati).</span><span class="sxs-lookup"><span data-stu-id="7d713-162">To connect to Azure AD for your Office 365 subscription with an account name and password or with multi-factor authentication (MFA), run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="7d713-163">**Cloud di Office 365**</span><span class="sxs-lookup"><span data-stu-id="7d713-163">**Office 365 cloud**</span></span> | <span data-ttu-id="7d713-164">**Comando**</span><span class="sxs-lookup"><span data-stu-id="7d713-164">**Command**</span></span> |
| <span data-ttu-id="7d713-165">Office 365 internazionale (+GCC)</span><span class="sxs-lookup"><span data-stu-id="7d713-165">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="7d713-166">Office 365 gestito da 21 Vianet</span><span class="sxs-lookup"><span data-stu-id="7d713-166">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="7d713-167">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="7d713-167">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="7d713-168">U.S. Government DoD di Office 365 e U.S. Government GCC High di Office 365</span><span class="sxs-lookup"><span data-stu-id="7d713-168">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="7d713-169">Nella finestra di dialogo per **accedere all'account**, digitare nome utente e password dell'account dell'istituto di istruzione o aziendale di Office 365, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="7d713-169">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="7d713-170">Se si utilizza l'autenticazione a più fattori, seguire le istruzioni nelle finestre di dialogo aggiuntive per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica.</span><span class="sxs-lookup"><span data-stu-id="7d713-170">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="7d713-171">Come verificare se l'operazione ha avuto esito positivo</span><span class="sxs-lookup"><span data-stu-id="7d713-171">How do you know this worked?</span></span>

<span data-ttu-id="7d713-172">If you don't receive any errors, you connected successfully.</span><span class="sxs-lookup"><span data-stu-id="7d713-172">If you don't receive any errors, you connected successfully.</span></span> <span data-ttu-id="7d713-173">A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span><span class="sxs-lookup"><span data-stu-id="7d713-173">A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="7d713-174">Se non vengono visualizzati errori, controllare i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="7d713-174">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="7d713-175">**A common problem is an incorrect password**.</span><span class="sxs-lookup"><span data-stu-id="7d713-175">**A common problem is an incorrect password**.</span></span> <span data-ttu-id="7d713-176">Run Step 2 again.</span><span class="sxs-lookup"><span data-stu-id="7d713-176">Run Step 2 again.</span></span> <span data-ttu-id="7d713-177">and pay close attention to the user name and password you enter.</span><span class="sxs-lookup"><span data-stu-id="7d713-177">and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="7d713-178">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled.</span><span class="sxs-lookup"><span data-stu-id="7d713-178">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled.</span></span> <span data-ttu-id="7d713-179">For more information, see the following topics:</span><span class="sxs-lookup"><span data-stu-id="7d713-179">For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="7d713-180">Per Windows Server 2012 o Windows Server 2012 R2, vedere [Abilitare .NET Framework 3.5 con Aggiunta guidata ruoli e funzionalità](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="7d713-180">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="7d713-181">Per Windows 7 o Windows Server 2008 R2, vedere [Impossibile aprire il Modulo di Azure Active Directory per Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="7d713-181">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="7d713-182">Per Windows 10, Windows 8.1 e Windows 8, vedere [Installare .NET Framework 3.5 in Windows 10, Windows 8.1 e Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)</span><span class="sxs-lookup"><span data-stu-id="7d713-182">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="7d713-183">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.**</span><span class="sxs-lookup"><span data-stu-id="7d713-183">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.**</span></span> <span data-ttu-id="7d713-184">To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7d713-184">To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="7d713-185">Se il numero di versione restituito è inferiore al valore 1.0.8070.2, disinstallare il modulo di Microsoft Azure Active Directory per Windows PowerShell e installarlo dal passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="7d713-185">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install from Step 1 above.</span></span>

- <span data-ttu-id="7d713-186">**Se viene visualizzato un errore di connessione, vedere l'argomento:** [Errore "La connessione-MsolService: eccezione di tipo"](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="7d713-186">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
- <span data-ttu-id="7d713-187">**Se viene visualizzato un messaggio di errore "Get-Item: impossibile trovare il percorso", usare questo comando:**</span><span class="sxs-lookup"><span data-stu-id="7d713-187">**If you receive a "Get-Item : Cannot find path" error, use this command:**</span></span> 

```powershell
  (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
```

## <a name="see-also"></a><span data-ttu-id="7d713-188">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7d713-188">See also</span></span>

- [<span data-ttu-id="7d713-189">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="7d713-189">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="7d713-190">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="7d713-190">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="7d713-191">Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7d713-191">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
