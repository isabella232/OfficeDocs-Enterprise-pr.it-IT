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
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Connettersi ai tenant Exchange Online con Windows PowerShell remoto per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)

> [!IMPORTANT]
> The procedures in this topic are only for Delegated Access Permission (DAP) partners. If you aren't a DAP partner, don't use the procedures in this topic. 
  
I partner DAP sono partner di Syndication e Cloud Solution Providers (CSP). Di solito, rappresentano fornitori di rete o telecomunicazioni di altre aziende. Consentono di raggruppare le sottoscrizioni nelle offerte di servizio per i clienti. Possiedono un contratto di locazione dei partner che viene automaticamente concesso amministrare per conto di (AOBO) le autorizzazioni per i propri clienti Microsoft 365 locazione in modo che possano amministrare e riferire su tutti i loro clienti locazione.

DAP Partners è in grado di utilizzare Exchange Online PowerShell per gestire le impostazioni di Exchange Online dei clienti e ottenere i report di Microsoft 365 dalla riga di comando. È possibile usare Windows PowerShell in un computer locale per creare una sessione di PowerShell remota in Exchange Online. Si tratta di un semplice processo in tre passaggi in cui immettere le credenziali, fornire le impostazioni di connessione necessarie e quindi importare i cmdlet di Exchange Online nella sessione locale di Windows PowerShell in modo che sia possibile utilizzarli.

> [!NOTE]
> DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell. MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Che cosa è necessario sapere prima di iniziare

- Tempo stimato per il completamento: 5 minuti

- È possibile utilizzare le seguenti versioni di Windows:
    
  - Windows 10

  - Windows 8.1

  - Windows Server 2016

  - Windows Server 2012 o Windows Server 2012 R2

  - Windows 7 Service Pack 1 (SP1)<sup>*</sup>

  - Windows Server 2008 R2 SP1<sup>*</sup>

    <sup>*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one). For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).

- Windows PowerShell needs to be configured to run scripts, and by default, it isn't. You'll get the following error when you try to connect:

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  Per richiedere che tutti gli script di PowerShell scaricati da internet siano firmati da un editore attendibile, eseguire il seguente comando in una finestra di Windows PowerShell elevata (una finestra di Windows PowerShell aperta selezionando **Esegui come amministratore**):

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  È necessario configurare questa impostazione soltanto una volta sul computer e non ogni volta che si stabilisce una connessione.

- Per informazioni sui tasti di scelta rapida applicabili alle procedure in questo argomento, vedere [Tasti di scelta rapida nell'interfaccia di amministrazione di Exchange](https://go.microsoft.com/fwlink/p/?LinkId=534017).

## <a name="connect-to-exchange-online-for-customer-organizations"></a>Connettersi a Exchange Online per le organizzazioni dei clienti

1. Nel computer locale, aprire Windows PowerShell ed eseguire il comando riportato di seguito.
    
    ```
    $UserCredential = Get-Credential
    ```

    Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell**, digitare il nome utente e la password di amministratore DAP, quindi fare clic su **OK**.
    
2. Sostituire _\<customer tenant domain name\>_ con il nome del dominio tenant a cui si desidera effettuare la connessione ed eseguire il comando riportato di seguito:
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    Il passaggio chiave in questo comando è la specificazione del cliente per il quale effettuare l'accesso per le informazioni di report. A tale scopo, utilizzare il parametro _ConnectionURI_ , in cui viene fornito il nome di dominio completo di FQDN come valore per `?DelegatedOrg=` . Questo valore indica l'endpoint di Exchange Online PowerShell corretto a cui connettersi. Remote PowerShell deve connettersi a Microsoft 365 Reporting nel contesto di un cliente specifico ogni volta che viene eseguito un report. Dopo aver eseguito la connessione a PowerShell di Exchange Online, tutti i comandi successivi vengono eseguiti nel contesto del cliente, che consente di accedere a tutti i report disponibili per il cliente.
    
3. Eseguire il comando riportato di seguito.
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> There's a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote PowerShell session, run the following command:

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a>Come verificare se l'operazione ha avuto esito positivo

After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.
  
Se non vengono visualizzati errori, controllare i requisiti seguenti:
  
- A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.
    
- The account you use to connect to Exchange Online must be enabled for remote PowerShell. For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).
    
- TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>Chiamare il cmdlet direttamente con Invoke-Command

Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets. This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants). As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a>Ulteriori cmdlet di report

The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:
  
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [Nuovo PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [Importa PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [Rimuovi PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

