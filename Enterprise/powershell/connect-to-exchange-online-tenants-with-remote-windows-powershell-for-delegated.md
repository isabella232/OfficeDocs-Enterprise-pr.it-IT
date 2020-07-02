---
title: Connettersi ai tenant Exchange Online con Windows PowerShell remoto per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 'Sintesi: utilizzare Windows PowerShell remoto per connettersi a Exchange Online tramite il valore DelegatedOrg.'
ms.openlocfilehash: 4a9f08325fc56308b27467423b047375985562c5
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997372"
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="1cb37-103">Connettersi ai tenant Exchange Online con Windows PowerShell remoto per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)</span><span class="sxs-lookup"><span data-stu-id="1cb37-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1cb37-104">The procedures in this topic are only for Delegated Access Permission (DAP) partners.</span><span class="sxs-lookup"><span data-stu-id="1cb37-104">The procedures in this topic are only for Delegated Access Permission (DAP) partners.</span></span> <span data-ttu-id="1cb37-105">If you aren't a DAP partner, don't use the procedures in this topic.</span><span class="sxs-lookup"><span data-stu-id="1cb37-105">If you aren't a DAP partner, don't use the procedures in this topic.</span></span> 
  
<span data-ttu-id="1cb37-106">I partner DAP sono partner di Syndication e Cloud Solution Providers (CSP).</span><span class="sxs-lookup"><span data-stu-id="1cb37-106">DAP partners are Syndication and Cloud Solution Providers (CSP) partners.</span></span> <span data-ttu-id="1cb37-107">Di solito, rappresentano fornitori di rete o telecomunicazioni di altre aziende.</span><span class="sxs-lookup"><span data-stu-id="1cb37-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="1cb37-108">Consentono di raggruppare le sottoscrizioni nelle offerte di servizio per i clienti.</span><span class="sxs-lookup"><span data-stu-id="1cb37-108">They bundle subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="1cb37-109">Possiedono un contratto di locazione dei partner che viene automaticamente concesso amministrare per conto di (AOBO) le autorizzazioni per i propri clienti Microsoft 365 locazione in modo che possano amministrare e riferire su tutti i loro clienti locazione.</span><span class="sxs-lookup"><span data-stu-id="1cb37-109">They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Microsoft 365 customer tenancies so they can administer and report on all of their customer tenancies.</span></span>

<span data-ttu-id="1cb37-110">DAP Partners è in grado di utilizzare Exchange Online PowerShell per gestire le impostazioni di Exchange Online dei clienti e ottenere i report di Microsoft 365 dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="1cb37-110">DAP partners can use Exchange Online PowerShell to manage customer Exchange Online settings and get Microsoft 365 reports from the command line.</span></span> <span data-ttu-id="1cb37-111">È possibile usare Windows PowerShell in un computer locale per creare una sessione di PowerShell remota in Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="1cb37-111">You use Windows PowerShell on your local computer to create a remote PowerShell session to Exchange Online.</span></span> <span data-ttu-id="1cb37-112">Si tratta di un semplice processo in tre passaggi in cui immettere le credenziali, fornire le impostazioni di connessione necessarie e quindi importare i cmdlet di Exchange Online nella sessione locale di Windows PowerShell in modo che sia possibile utilizzarli.</span><span class="sxs-lookup"><span data-stu-id="1cb37-112">It's a simple three-step process where you enter your credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>

> [!NOTE]
> <span data-ttu-id="1cb37-113">DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1cb37-113">DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell.</span></span> <span data-ttu-id="1cb37-114">MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.</span><span class="sxs-lookup"><span data-stu-id="1cb37-114">MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="1cb37-115">Che cosa è necessario sapere prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="1cb37-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="1cb37-116">Tempo stimato per il completamento: 5 minuti</span><span class="sxs-lookup"><span data-stu-id="1cb37-116">Estimated time to complete: 5 minutes</span></span>

- <span data-ttu-id="1cb37-117">È possibile utilizzare le seguenti versioni di Windows:</span><span class="sxs-lookup"><span data-stu-id="1cb37-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="1cb37-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="1cb37-118">Windows 10</span></span>

  - <span data-ttu-id="1cb37-119">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="1cb37-119">Windows 8.1</span></span>

  - <span data-ttu-id="1cb37-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="1cb37-120">Windows Server 2016</span></span>

  - <span data-ttu-id="1cb37-121">Windows Server 2012 o Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="1cb37-121">Windows Server 2012 or Windows Server 2012 R2</span></span>

  - <span data-ttu-id="1cb37-122">Windows 7 Service Pack 1 (SP1)<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="1cb37-122">Windows 7 Service Pack 1 (SP1)<sup>\*</sup></span></span>

  - <span data-ttu-id="1cb37-123">Windows Server 2008 R2 SP1<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="1cb37-123">Windows Server 2008 R2 SP1<sup>\*</sup></span></span>

    <span data-ttu-id="1cb37-124"><sup>\*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one).</span><span class="sxs-lookup"><span data-stu-id="1cb37-124"><sup>\*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one).</span></span> <span data-ttu-id="1cb37-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span><span class="sxs-lookup"><span data-stu-id="1cb37-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span></span>

- <span data-ttu-id="1cb37-126">Windows PowerShell needs to be configured to run scripts, and by default, it isn't.</span><span class="sxs-lookup"><span data-stu-id="1cb37-126">Windows PowerShell needs to be configured to run scripts, and by default, it isn't.</span></span> <span data-ttu-id="1cb37-127">You'll get the following error when you try to connect:</span><span class="sxs-lookup"><span data-stu-id="1cb37-127">You'll get the following error when you try to connect:</span></span>

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  <span data-ttu-id="1cb37-128">Per richiedere che tutti gli script di PowerShell scaricati da internet siano firmati da un editore attendibile, eseguire il seguente comando in una finestra di Windows PowerShell elevata (una finestra di Windows PowerShell aperta selezionando **Esegui come amministratore**):</span><span class="sxs-lookup"><span data-stu-id="1cb37-128">To require all PowerShell scripts that you download from the internet are signed by a trusted publisher, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you open by selecting **Run as administrator**):</span></span>

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  <span data-ttu-id="1cb37-129">È necessario configurare questa impostazione soltanto una volta sul computer e non ogni volta che si stabilisce una connessione.</span><span class="sxs-lookup"><span data-stu-id="1cb37-129">You need to configure this setting only once on your computer, not every time you connect.</span></span>

- <span data-ttu-id="1cb37-130">Per informazioni sui tasti di scelta rapida applicabili alle procedure in questo argomento, vedere [Tasti di scelta rapida nell'interfaccia di amministrazione di Exchange](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span><span class="sxs-lookup"><span data-stu-id="1cb37-130">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>

## <a name="connect-to-exchange-online-for-customer-organizations"></a><span data-ttu-id="1cb37-131">Connettersi a Exchange Online per le organizzazioni dei clienti</span><span class="sxs-lookup"><span data-stu-id="1cb37-131">Connect to Exchange Online for customer organizations</span></span>

1. <span data-ttu-id="1cb37-132">Nel computer locale, aprire Windows PowerShell ed eseguire il comando riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="1cb37-132">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```

    <span data-ttu-id="1cb37-133">Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell**, digitare il nome utente e la password di amministratore DAP, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="1cb37-133">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="1cb37-134">Sostituire _\<customer tenant domain name\>_ con il nome del dominio tenant a cui si desidera effettuare la connessione ed eseguire il comando riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="1cb37-134">Replace _\<customer tenant domain name\>_ with the name of the tenant domain that you want to connect to, and run the following command:</span></span>
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    <span data-ttu-id="1cb37-135">Il passaggio chiave in questo comando è la specificazione del cliente per il quale effettuare l'accesso per le informazioni di report.</span><span class="sxs-lookup"><span data-stu-id="1cb37-135">The key step in this command is specifying which customer to access for the reporting information.</span></span> <span data-ttu-id="1cb37-136">A tale scopo, utilizzare il parametro _ConnectionURI_ , in cui viene fornito il nome di dominio completo di FQDN come valore per `?DelegatedOrg=` .</span><span class="sxs-lookup"><span data-stu-id="1cb37-136">You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value for `?DelegatedOrg=`.</span></span> <span data-ttu-id="1cb37-137">Questo valore indica l'endpoint di Exchange Online PowerShell corretto a cui connettersi.</span><span class="sxs-lookup"><span data-stu-id="1cb37-137">This value indicates the correct Exchange Online PowerShell endpoint to connect to.</span></span> <span data-ttu-id="1cb37-138">Remote PowerShell deve connettersi a Microsoft 365 Reporting nel contesto di un cliente specifico ogni volta che viene eseguito un report.</span><span class="sxs-lookup"><span data-stu-id="1cb37-138">Remote PowerShell must connect to Microsoft 365 reporting in the context of a specific customer each time a report is run.</span></span> <span data-ttu-id="1cb37-139">Dopo aver eseguito la connessione a PowerShell di Exchange Online, tutti i comandi successivi vengono eseguiti nel contesto del cliente, che consente di accedere a tutti i report disponibili per il cliente.</span><span class="sxs-lookup"><span data-stu-id="1cb37-139">After you connect to Exchange Online PowerShell, all subsequent commands are run in the context of the customer, which gives you access to all of the available reports for the customer.</span></span>
    
3. <span data-ttu-id="1cb37-140">Eseguire il comando riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="1cb37-140">Run the following command.</span></span>
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> <span data-ttu-id="1cb37-141">There's a limit of three simultaneous sessions that can run under one account.</span><span class="sxs-lookup"><span data-stu-id="1cb37-141">There's a limit of three simultaneous sessions that can run under one account.</span></span> <span data-ttu-id="1cb37-142">Be sure to disconnect the remote PowerShell session when you're finished.</span><span class="sxs-lookup"><span data-stu-id="1cb37-142">Be sure to disconnect the remote PowerShell session when you're finished.</span></span> <span data-ttu-id="1cb37-143">If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire.</span><span class="sxs-lookup"><span data-stu-id="1cb37-143">If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire.</span></span> <span data-ttu-id="1cb37-144">To disconnect the remote PowerShell session, run the following command:</span><span class="sxs-lookup"><span data-stu-id="1cb37-144">To disconnect the remote PowerShell session, run the following command:</span></span>

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="1cb37-145">Come verificare se l'operazione ha avuto esito positivo</span><span class="sxs-lookup"><span data-stu-id="1cb37-145">How do you know this worked?</span></span>

<span data-ttu-id="1cb37-146">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar.</span><span class="sxs-lookup"><span data-stu-id="1cb37-146">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar.</span></span> <span data-ttu-id="1cb37-147">If you don't receive any errors, you connected successfully.</span><span class="sxs-lookup"><span data-stu-id="1cb37-147">If you don't receive any errors, you connected successfully.</span></span> <span data-ttu-id="1cb37-148">A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.</span><span class="sxs-lookup"><span data-stu-id="1cb37-148">A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.</span></span>
  
<span data-ttu-id="1cb37-149">Se non vengono visualizzati errori, controllare i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="1cb37-149">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="1cb37-150">A common problem is an incorrect password.</span><span class="sxs-lookup"><span data-stu-id="1cb37-150">A common problem is an incorrect password.</span></span> <span data-ttu-id="1cb37-151">Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span><span class="sxs-lookup"><span data-stu-id="1cb37-151">Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="1cb37-152">The account you use to connect to Exchange Online must be enabled for remote PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1cb37-152">The account you use to connect to Exchange Online must be enabled for remote PowerShell.</span></span> <span data-ttu-id="1cb37-153">For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span><span class="sxs-lookup"><span data-stu-id="1cb37-153">For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="1cb37-154">TCP port 80 traffic needs to be open between your local computer and Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="1cb37-154">TCP port 80 traffic needs to be open between your local computer and Exchange Online.</span></span> <span data-ttu-id="1cb37-155">It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span><span class="sxs-lookup"><span data-stu-id="1cb37-155">It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="1cb37-156">Chiamare il cmdlet direttamente con Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="1cb37-156">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="1cb37-157">Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets.</span><span class="sxs-lookup"><span data-stu-id="1cb37-157">Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets.</span></span> <span data-ttu-id="1cb37-158">This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants).</span><span class="sxs-lookup"><span data-stu-id="1cb37-158">This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants).</span></span> <span data-ttu-id="1cb37-159">As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**.</span><span class="sxs-lookup"><span data-stu-id="1cb37-159">As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**.</span></span> <span data-ttu-id="1cb37-160">For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:</span><span class="sxs-lookup"><span data-stu-id="1cb37-160">For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="1cb37-161">Ulteriori cmdlet di report</span><span class="sxs-lookup"><span data-stu-id="1cb37-161">More reporting cmdlets</span></span>

<span data-ttu-id="1cb37-162">The cmdlets that you used in this topic are Windows PowerShell cmdlets.</span><span class="sxs-lookup"><span data-stu-id="1cb37-162">The cmdlets that you used in this topic are Windows PowerShell cmdlets.</span></span> <span data-ttu-id="1cb37-163">For more information about these cmdlets, see the following topics:</span><span class="sxs-lookup"><span data-stu-id="1cb37-163">For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="1cb37-164">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="1cb37-164">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="1cb37-165">Nuovo PSSession</span><span class="sxs-lookup"><span data-stu-id="1cb37-165">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="1cb37-166">Importa PSSession</span><span class="sxs-lookup"><span data-stu-id="1cb37-166">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="1cb37-167">Rimuovi PSSession</span><span class="sxs-lookup"><span data-stu-id="1cb37-167">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="1cb37-168">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="1cb37-168">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

