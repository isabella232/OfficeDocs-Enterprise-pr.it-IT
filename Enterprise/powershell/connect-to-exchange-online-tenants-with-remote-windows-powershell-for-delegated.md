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
ms.custom: DecEntMigration
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 'Riepilogo: utilizzare Windows PowerShell remoto per connettersi a Exchange Online tramite il parametro DelegatedOrg.'
ms.openlocfilehash: 9bb6a5a316f4bc23c6586da825b8755cf755f484
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Connettersi ai tenant Exchange Online con Windows PowerShell remoto per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)

 **Riepilogo:** Utilizzare Windows PowerShell remoto per la connessione a Exchange Online utilizzando il parametro _DelegatedOrg_ .
  
Windows PowerShell remoto consente di gestire le impostazioni di Exchange Online dalla riga di comando. Per creare una sessione remota in Exchange Online, utilizzare Windows PowerShell sul computer locale. È un processo di tre passaggi nel quale si inseriscono le credenziali di Exchange Online, vengono fornite le impostazioni di connessione necessarie e poi vengono importati i cmdlet di Exchange Online nella sessione di Windows PowerShell locale per poterli usare.
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Che cosa è necessario sapere prima di iniziare

- Tempo stimato per il completamento: 5 minuti
    
- È possibile utilizzare le seguenti versioni di Windows:
    
  - Windows 10
    
  - Windows 8.1 o Windows 8
    
  - Windows Server 2012 R2 o Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    * È necessario installare NET Framework 4.5.1 o .NET Framework 4.5 e quindi Windows Management Framework 4.0 o Windows Management Framework 3.0 . Per ulteriori informazioni, vedere le risorse riportate di seguito:
    
  - [Installazione di .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
  - [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) o[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)
    
- Per informazioni sui tasti di scelta rapida applicabili alle procedure in questo argomento, vedere [Tasti di scelta rapida nell'interfaccia di amministrazione di Exchange](https://go.microsoft.com/fwlink/p/?LinkId=534017).
    
## 

> [!IMPORTANT]
> Questa procedura vale solo per ipartner di autorizzazione accesso delegato (DAP, Delegated Access Permission)Se non si è un partner DAP, non utilizzare questa procedura. 
  
I partner DAP sono partner di Syndication e Cloud Solution Providers (CSP). Di solito, rappresentano fornitori di rete o telecomunicazioni di altre aziende. Consentono di raggruppare le sottoscrizioni nelle offerte di servizio per i clienti. Possiedono un tenancy partner che garantisce autorizzazioni Amministra per conto terzi (AOBO, Administer On Behalf Of) automatiche per itenancy dei clienti di Office 365 al fine di gestire e creare report per tutti i tenancy dei clienti.
  
## <a name="connect-to-exchange-online"></a>Connessione a Exchange Online

1. Nel computer locale, aprire Windows PowerShell ed eseguire il comando seguente.
    
  ```
  $UserCredential = Get-Credential
  ```

    Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell**, digitare il nome utente e la password di amministratore DAP, quindi fare clic su **OK**.
    
2. Eseguire il comando seguente, sostituendo  _<customer tenant domain name>_ con il nome del dominio del tenant cui si desidera connettersi.
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    Il passaggio chiave in questo comando è la specificazione del cliente per il quale effettuare l'accesso per le informazioni di report. Questa operazione è possibile nel parametro  _ConnectionURI_, in cui si fornisce l'FQDN del nome di dominio iniziale come valore per il parametro  _DelegatedOrg_. Questo parametro indica a Windows PowerShell remoto per Exchange Online PowerShell l'endpoint di Windows PowerShell remoto a cui connettersi. Windows PowerShell remoto deve connettersi a Office 365 creando un report relativo a un cliente specifico ogni volta che viene eseguito un report. Dopo avere specificato il cliente, tutti i comandi seguenti vengono eseguiti nell'ambito di tale cliente. In questo modo, il partner può accedere a tutti i report disponibili per tale cliente.
    
3. Eseguire il comando riportato di seguito.
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> C'è un limite di tre sessioni simultanee che è possibile eseguire in un account. Al termine assicurarsi di chiudere la sessione remota di Windows PowerShell. Chiudendo la finestra di Windows PowerShell senza disconnettere la sessione, si rischia di esaurire tutte le sessioni remote di Windows PowerShell disponibili e di dover attendere la scadenza delle sessioni. Per disconnettere la sessione remota di Windows PowerShell, eseguire il seguente comando. >  `Remove-PSSession $Session`
  
## <a name="how-do-you-know-this-worked"></a>Come verificare se l'operazione ha avuto esito positivo

Dopo il passaggio 3, i cmdlet di Exchange Online vengono importati nella sessione locale di Windows PowerShell come indicato da una barra di avanzamento. Se non vengono visualizzati errori, la connessione è stata eseguita correttamente. Un breve test consiste nell'eseguire un cmdlet di Exchange Online (ad esempio, **Get-Mailbox** ) e vedere i risultati.
  
Se non vengono visualizzati errori, controllare i requisiti seguenti:
  
- Un problema comune è rappresentato da una password errata. Eseguire di nuovi questi tre passaggi e prestare particolare attenzione al nome utente e alla password del passaggio 1.
    
- Per evitare attacchi DoS (Denial of Service), è possibile aprire massimo tre connessioni Windows PowerShell all'organizzazione Exchange Online.
    
- Windows PowerShell deve essere configurato per poter eseguire gli script. È necessario configurare questa impostazione soltanto una volta sul computer e non ogni volta che si stabilisce una connessione. Per abilitare Windows PowerShell affinché esegua script firmati, eseguire il seguente comando in una finestra di Windows PowerShell elevata (una finestra di Windows PowerShell aperta selezionando **Esegui come amministratore**).
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- L'account utilizzato per connettersi a Exchange Online deve essere abilitato per Windows PowerShell remoto. Per ulteriori informazioni, vedere [Gestione dell'accesso remoto di PowerShell in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).
    
- Il traffico sulla porta TCP 80 deve essere aperto tra il computer locale e Exchange Online. È probabile che sia aperto, ma è bene verificare se l'organizzazione dispone di criteri restrittivi relativi all'accesso a Internet.
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>Chiamare il cmdlet direttamente con Invoke-Command

L'importazione di una sessione remota di Windows PowerShell può essere una procedura complessa poiché coinvolge tutti i cmdlet di Exchange Online. Questo può essere un problema nell'elaborazione batch, ad esempio, quando si eseguono report o si apportano modifiche in blocco per tenant diversi. Come alternativa all'utilizzo di **Import-PSSession**, è possibile chiamare i cmdlet direttamente con **Invoke-Command**. Ad esempio, per chiamare il cmdlet **get-mailbox**, sostituire la sintassi per `Import-PSSession $Session`.
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a>Ulteriori cmdlet di report

I cmdlet utilizzati in questo argomento sono cmdlet di Windows PowerShell. Per ulteriori informazioni su questi cmdlet, vedere i seguenti argomenti:
  
- [Ottieni credenziali](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [Nuovo PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [Importa PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [Rimuovi PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

