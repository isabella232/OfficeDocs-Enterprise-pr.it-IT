---
title: Connettersi ai tenant Exchange Online con Windows PowerShell remoto per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 'Riepilogo: utilizzare Windows PowerShell remoto per connettersi a Exchange Online tramite il parametro DelegatedOrg.'
ms.openlocfilehash: d8cbb6640419ba2f1de868ae88b0a273c3f71ae7
ms.sourcegitcommit: f3f81d2c2e8290948d93f3f787a679c804840256
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/23/2018
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="754ee-103">Connettersi ai tenant Exchange Online con Windows PowerShell remoto per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)</span><span class="sxs-lookup"><span data-stu-id="754ee-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="754ee-104">**Sintesi:** Utilizzare Windows PowerShell remoto per connettersi a Exchange Online tramite il parametro _DelegatedOrg_.</span><span class="sxs-lookup"><span data-stu-id="754ee-104">**Summary:** Use remote Windows PowerShell to connect to Exchange Online by using the _DelegatedOrg_ parameter.</span></span>
  
<span data-ttu-id="754ee-p101">Windows PowerShell remoto consente di gestire le impostazioni di Exchange Online dalla riga di comando. Per creare una sessione remota in Exchange Online, utilizzare Windows PowerShell sul computer locale. È un processo di tre passaggi nel quale si inseriscono le credenziali di Exchange Online, vengono fornite le impostazioni di connessione necessarie e poi vengono importati i cmdlet di Exchange Online nella sessione di Windows PowerShell locale per poterli usare.</span><span class="sxs-lookup"><span data-stu-id="754ee-p101">Remote Windows PowerShell lets you manage your Exchange Online settings from the command line. You use Windows PowerShell on your local computer to create a remote session to Exchange Online. It's a three-step process where you enter your Exchange Online credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="754ee-108">Che cosa è necessario sapere prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="754ee-108">What do you need to know before you begin?</span></span>

- <span data-ttu-id="754ee-109">Tempo stimato per il completamento: 5 minuti</span><span class="sxs-lookup"><span data-stu-id="754ee-109">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="754ee-110">È possibile utilizzare le seguenti versioni di Windows:</span><span class="sxs-lookup"><span data-stu-id="754ee-110">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="754ee-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="754ee-111">Windows 10</span></span>
    
  - <span data-ttu-id="754ee-112">Windows 8.1 o Windows 8</span><span class="sxs-lookup"><span data-stu-id="754ee-112">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="754ee-113">Windows Server 2012 R2 o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="754ee-113">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="754ee-114">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="754ee-114">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="754ee-115">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="754ee-115">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="754ee-p102">\* È necessario installare NET Framework 4.5.1 o .NET Framework 4.5 e quindi Windows Management Framework 4.0 o Windows Management Framework 3.0 . Per ulteriori informazioni, vedere le risorse riportate di seguito:</span><span class="sxs-lookup"><span data-stu-id="754ee-p102">\*You need to install the .NET Framework 4.5.1 or the .NET Framework 4.5 and then either the Windows Management Framework 4.0 or the Windows Management Framework 3.0 . For more information, see the following resources:</span></span>
    
    - [<span data-ttu-id="754ee-118">Installazione di .NET Framework</span><span class="sxs-lookup"><span data-stu-id="754ee-118">Installing the .NET Framework</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
    - <span data-ttu-id="754ee-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) o [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span><span class="sxs-lookup"><span data-stu-id="754ee-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span></span>
    
- <span data-ttu-id="754ee-120">Per informazioni sui tasti di scelta rapida applicabili alle procedure in questo argomento, vedere [Tasti di scelta rapida nell'interfaccia di amministrazione di Exchange](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span><span class="sxs-lookup"><span data-stu-id="754ee-120">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>
    
## 

> [!IMPORTANT]
> <span data-ttu-id="754ee-p103">Questa procedura vale solo per ipartner di autorizzazione accesso delegato (DAP, Delegated Access Permission)Se non si è un partner DAP, non utilizzare questa procedura.</span><span class="sxs-lookup"><span data-stu-id="754ee-p103">This procedure is only for Delegated Access Permission (DAP) partners. If you are not a DAP partner, do not use this procedure.</span></span> 
  
<span data-ttu-id="754ee-p104">I partner DAP sono partner di Syndication e Cloud Solution Providers (CSP). Di solito, rappresentano fornitori di rete o telecomunicazioni di altre aziende. Consentono di raggruppare le sottoscrizioni nelle offerte di servizio per i clienti. Possiedono un tenancy partner che garantisce autorizzazioni Amministra per conto terzi (AOBO, Administer On Behalf Of) automatiche per itenancy dei clienti di Office 365 al fine di gestire e creare report per tutti i tenancy dei clienti.</span><span class="sxs-lookup"><span data-stu-id="754ee-p104">DAP partners are Syndication and Cloud Solution Providers (CSP) partners. They are frequently network or telecom providers to other companies. They bundle subscriptions into their service offerings to their customers. They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Office 365customer tenancies so they can administer and report on all of their customer tenancies.</span></span>
  
## <a name="connect-to-exchange-online"></a><span data-ttu-id="754ee-127">Connessione a Exchange Online</span><span class="sxs-lookup"><span data-stu-id="754ee-127">Connect to Exchange Online</span></span>

1. <span data-ttu-id="754ee-128">Nel computer locale, aprire Windows PowerShell ed eseguire il comando riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="754ee-128">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
  ```
  $UserCredential = Get-Credential
  ```

    <span data-ttu-id="754ee-129">Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell**, digitare il nome utente e la password di amministratore DAP, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="754ee-129">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="754ee-130">Eseguire il comando seguente, sostituendo  _<customer tenant domain name>_ con il nome del dominio del tenant cui si desidera connettersi.</span><span class="sxs-lookup"><span data-stu-id="754ee-130">Run the following command, replacing  _<customer tenant domain name>_ with the name of the tenant domain that you want to connect to.</span></span>
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    <span data-ttu-id="754ee-p105">Il passaggio chiave in questo comando è la specificazione del cliente per il quale effettuare l'accesso per le informazioni di report. Questa operazione è possibile nel parametro  _ConnectionURI_, in cui si fornisce l'FQDN del nome di dominio iniziale come valore per il parametro  _DelegatedOrg_. Questo parametro indica a Windows PowerShell remoto per Exchange Online PowerShell l'endpoint di Windows PowerShell remoto a cui connettersi. Windows PowerShell remoto deve connettersi a Office 365 creando un report relativo a un cliente specifico ogni volta che viene eseguito un report. Dopo avere specificato il cliente, tutti i comandi seguenti vengono eseguiti nell'ambito di tale cliente. In questo modo, il partner può accedere a tutti i report disponibili per tale cliente.</span><span class="sxs-lookup"><span data-stu-id="754ee-p105">The key step in this command is specifying which customer to access for the reporting information. You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value to the _DelegatedOrg_ parameter. This tells remote Windows PowerShell for Exchange Online PowerShell remote Windows PowerShell the endpoint to connect to. remote Windows PowerShell must connect to Office 365 reporting in the context of a specific customer each time a report is run. After this customer is specified, all of the following commands are run in the context of that customer. This lets the partner to access all the available reports for this customer.</span></span>
    
3. <span data-ttu-id="754ee-137">Eseguire il comando riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="754ee-137">Run the following command.</span></span>
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> <span data-ttu-id="754ee-p106">C'è un limite di tre sessioni simultanee che è possibile eseguire in un account. Al termine assicurarsi di chiudere la sessione remota di Windows PowerShell. Chiudendo la finestra di Windows PowerShell senza disconnettere la sessione, si rischia di esaurire tutte le sessioni remote di Windows PowerShell disponibili e di dover attendere la scadenza delle sessioni. Per disconnettere la sessione remota di Windows PowerShell, eseguire il seguente comando. >  `Remove-PSSession $Session`</span><span class="sxs-lookup"><span data-stu-id="754ee-p106">There is a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote Windows PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote Windows PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote Windows PowerShell session, run the following command. >  `Remove-PSSession $Session`</span></span>
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="754ee-142">Come verificare se l'operazione ha avuto esito positivo</span><span class="sxs-lookup"><span data-stu-id="754ee-142">How do you know this worked?</span></span>

<span data-ttu-id="754ee-p107">Dopo il passaggio 3, i cmdlet di Exchange Online vengono importati nella sessione locale di Windows PowerShell come indicato da una barra di avanzamento. Se non vengono visualizzati errori, la connessione è stata eseguita correttamente. Un breve test consiste nell'eseguire un cmdlet di Exchange Online (ad esempio, **Get-Mailbox** ) e vedere i risultati.</span><span class="sxs-lookup"><span data-stu-id="754ee-p107">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet—for example, **Get-Mailbox** —and see the results.</span></span>
  
<span data-ttu-id="754ee-146">Se non vengono visualizzati errori, controllare i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="754ee-146">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="754ee-p108">Un problema comune è rappresentato da una password errata. Eseguire di nuovi questi tre passaggi e prestare particolare attenzione al nome utente e alla password del passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="754ee-p108">A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="754ee-149">Per evitare attacchi DoS (Denial of Service), è possibile aprire massimo tre connessioni Windows PowerShell all'organizzazione Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="754ee-149">To help prevent denial-of-service (DoS) attacks, you're limited to three open remote Windows PowerShell connections to your Exchange Online organization.</span></span>
    
- <span data-ttu-id="754ee-p109">Windows PowerShell deve essere configurato per poter eseguire gli script. È necessario configurare questa impostazione soltanto una volta sul computer e non ogni volta che si stabilisce una connessione. Per abilitare Windows PowerShell affinché esegua script firmati, eseguire il seguente comando in una finestra di Windows PowerShell elevata (una finestra di Windows PowerShell aperta selezionando **Esegui come amministratore**).</span><span class="sxs-lookup"><span data-stu-id="754ee-p109">Windows PowerShell needs to be configured to run scripts. You need to configure this setting only once on your computer, not every time you connect. To enable Windows PowerShell to run signed scripts, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you opened by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- <span data-ttu-id="754ee-p110">L'account utilizzato per connettersi a Exchange Online deve essere abilitato per Windows PowerShell remoto. Per ulteriori informazioni, vedere [Gestione dell'accesso remoto di PowerShell in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span><span class="sxs-lookup"><span data-stu-id="754ee-p110">The account you use to connect to Exchange Online must be enabled for remote Windows PowerShell. For more information, see [Manage Remote PowerShell Access in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="754ee-p111">Il traffico sulla porta TCP 80 deve essere aperto tra il computer locale e Exchange Online. È probabile che sia aperto, ma è bene verificare se l'organizzazione dispone di criteri restrittivi relativi all'accesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="754ee-p111">TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="754ee-157">Chiamare il cmdlet direttamente con Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="754ee-157">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="754ee-p112">L'importazione di una sessione remota di Windows PowerShell può essere una procedura complessa poiché coinvolge tutti i cmdlet di Exchange Online. Questo può essere un problema nell'elaborazione batch, ad esempio, quando si eseguono report o si apportano modifiche in blocco per tenant diversi. Come alternativa all'utilizzo di **Import-PSSession**, è possibile chiamare i cmdlet direttamente con **Invoke-Command**. Ad esempio, per chiamare il cmdlet **get-mailbox**, sostituire la sintassi per `Import-PSSession $Session`.</span><span class="sxs-lookup"><span data-stu-id="754ee-p112">Importing a remote Windows PowerShell session can be a lengthy process because it brings in all Exchange Online cmdlets. This can be an issue in batch processing—for example, when you are running reports or making bulk changes for different tenants. As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **get-mailbox** cmdlet, substitute this syntax for `Import-PSSession $Session`.</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="754ee-162">Ulteriori cmdlet di report</span><span class="sxs-lookup"><span data-stu-id="754ee-162">More reporting cmdlets</span></span>

<span data-ttu-id="754ee-p113">I cmdlet utilizzati in questo argomento sono cmdlet di Windows PowerShell. Per ulteriori informazioni su questi cmdlet, vedere i seguenti argomenti:</span><span class="sxs-lookup"><span data-stu-id="754ee-p113">The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="754ee-165">Ottieni credenziali</span><span class="sxs-lookup"><span data-stu-id="754ee-165">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="754ee-166">Nuovo PSSession</span><span class="sxs-lookup"><span data-stu-id="754ee-166">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="754ee-167">Importa PSSession</span><span class="sxs-lookup"><span data-stu-id="754ee-167">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="754ee-168">Rimuovi PSSession</span><span class="sxs-lookup"><span data-stu-id="754ee-168">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="754ee-169">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="754ee-169">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

