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
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Summary: Connect Windows PowerShell to all Office 365 services in a single Windows PowerShell window.'
ms.openlocfilehash: 2dccfc73b016cbe97436c822432331ee30ba4bcd
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell

 **Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.
  
When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:
  
![Cinque console di Windows PowerShell in esecuzione contemporaneamente](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.
  
## <a name="before-you-begin"></a>Prima di iniziare
<a name="BeforeYouBegin"> </a>

Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:
  
- The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.
    
- È possibile utilizzare le seguenti versioni a 64 bit di Windows:
    
  - Windows 10
    
  - Windows 8.1 o Windows 8
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 o Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    * You need to install the Microsoft .NET Framework 4.5. _x_ and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.
    
- You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:
    
  - [Microsoft Online Service Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)
    
  - [Windows Azure Active Directory Module for Windows PowerShell (64-bit version)](https://go.microsoft.com/fwlink/p/?linkid=236297)
    
  - [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
    
  - [Skype for Business Online, Windows PowerShell Module](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="the-short-version-instructions-without-explanations"></a>Versione breve (istruzioni senza spiegazioni)
<a name="ShortVersion"> </a>

In questa sezione vengono illustrate le procedure di connessione senza spiegazioni dettagliate. Se si hanno altre domande o si desiderano ulteriori informazioni, è possibile leggere il resto dell'argomento. I numeri dei passaggi corrispondono ai numeri dei passaggi delle sezioni del resto dell'argomento:
  
1. Open Windows PowerShell as an administrator (use **Run as administrator**).
    
2. Run this command, and enter your Office 365 work or school account credentials.
    
  ```
  $credential = Get-Credential
  ```

3. Run these commands to connect to Office 365.
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Run these commands to connect to Exchange Online.
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. Run these commands to connect to the Security &amp; Compliance Center.
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> The text prefix "cc" is added to  *all*  Security &amp; Compliance Center cmdlet names so you can run cmdlets that exist in both Exchange Online and the Security &amp; Compliance Center in the same Windows PowerShell session. For example, **Get-RoleGroup** becomes **Get-ccRoleGroup** in the Security &amp; Compliance Center.
  
Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.
  
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

When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>Versione estesa (istruzioni con spiegazioni dettagliate)
<a name="LongVersion"> </a>

### <a name="step-1-open-windows-powershell-as-an-administrator"></a>Passaggio 1: Aprire Windows PowerShell come amministratore
<a name="Step1"> </a>

If you're running Windows 10, Windows 8, Windows 8.1, Windows Server 2016, Windows Server 2012 R2, or Windows Server 2012 R2, do this:
  
1. Use any of these methods to find the shortcut for **Windows PowerShell**:
    
  - On the Start screen, click an empty area, and type Windows PowerShell.
    
  - On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Windows PowerShell.
    
  - On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and enter Windows PowerShell.
    
2. In the results, right-click **Windows PowerShell**, and select **Run as administrator**.
    
3. If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.
    
If you're running Windows 7 SP1 (or Windows Server 2008 R2 SP1), do this:
  
1. On the **Start** menu, select **All Programs** > **Accessories** > **Windows PowerShell**. Right-click **Windows PowerShell**, and then select **Run as administrator**.
    
2. If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.
    
You must run Windows PowerShell as an administrator. If you don't, you're going to get an error message similar to this when you try to import one of the required modules.
  
```
The specified module 'Microsoft.Online.SharePoint.Online.PowerShell' was not loaded because no valid module file was found in any directory.
```

The only way to remedy the situation is to close Windows PowerShell and restart it as an administrator. Here's a quick and easy way to tell if you're running Windows PowerShell as an administrator: the prompt is  `PS C:\Windows\System32>`, not  `PS C:\Users\YourUserName>`.

  
### <a name="step-2-create-a-windows-powershell-credentials-object"></a>Passaggio 2: creazione di un oggetto credenziali di Windows PowerShell
<a name="Step2"> </a>

The credentials object provides an encrypted way to pass your user name and password to Windows PowerShell. To create a credentials object, run the following command in Windows PowerShell.
  
```
$credential = Get-Credential
```

> [!NOTE]
>  `$credential` is a variable that will store the credentials object. You don't have to name the variable `$credential`, but doing so makes it easier to remember which variable contains the credentials object. (And that's important, because we'll reuse this variable several times.) That will also make it easier for you to follow our examples, because this article will always use  `$credential` to represent the credentials object.
  
Windows PowerShell will then display a dialog box that looks like this.
  
![Finestra di dialogo Richiesta credenziali vuota.](images/o365_powershell_empty_credentials_box.png)
  
Type your work or school account user name in the **User name** box, using the format _username@domainname_ (for example, kenmyer@litwareinc.onmicrosoft.com); type your password in the **Password** box; and then click **OK**:
  
![Finestra di dialogo Richiesta credenziali completata.](images/o365_powershell_completed_credentials_box.png)
  
Si noti che, quando si verifica in genere, si potrà essere visualizzato alcun tipo di conferma che sia stato creato l'oggetto credenziali. (Windows PowerShell in genere viene illustrato quando operazioni vanno male, ma non sempre a spiegare quando le cose vanno destra.) Se si desidera verificare che sia stato creato l'oggetto credenziali, digitare quanto segue in Windows PowerShell e quindi premere INVIO.
  
```
$credential
```

Quindi, sullo schermo verranno visualizzati elementi analoghi a quelli riportati di seguito.
  
```
UserName                               Password
--------                               --------
kenmyer@litwareinc.onmicrosoft.com     System.Security.SecureString
```

È necessario tenere presenti in questo caso è che il cmdlet [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618) crea solo l'oggetto credenziali. non autenticare l'utente o in caso contrario verificare che il nome utente e la password che è fornito siano corrette. Si supponga, ad esempio, che è stato digitato correttamente il nome utente come kenmyer@litwareinc.onmicrosoft.com. In caso contrario, **Get-Credential** creerà un oggetto credenziali utilizzando tale nome utente e senza controllo per verificare che sia effettivamente un nome utente valido. Non si conosce se è stato creato un oggetto credenziali valide effettivamente finché non si utilizza effettivamente tale oggetto tenti di connettersi ai servizi di Office 365.
  
### <a name="step-3-connect-to-office-365"></a>Passaggio 3: Connettersi a Office 365
<a name="Step3"> </a>

We'll start by connecting to Office 365 itself. 
  
The first thing we need to do here is import the Office 365 module (the Microsoft Azure Active Directory Module for Windows PowerShell). To do that, run this command in Windows PowerShell.
  
```
Import-Module MsOnline
```

Per verificare l'importazione del modulo, eseguire questo comando.
  
```
Get-Module
```

In un punto qualsiasi nell'elenco di moduli restituito da questo comando verrà visualizzato qualcosa di simile al seguente: `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`.
  
Se viene visualizzato `MSOnline` nell'elenco, ciò significa che tutti gli elementi che indica la presenza in base alla pianificazione.
  
With the credentials object created (see [Step 2: Create a Windows PowerShell credentials object](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) and with the  `MsOnline` module loaded, we can now connect to Office 365 by using the [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) cmdlet and the following command.
  
```
Connect-MsolService -Credential $credential
```

Notice that all you have to provide is the credentials object ( `$credential`). Based on those credentials, Office 365 will automatically connect you to the correct domain. You do not have to specify your domain name when running **Connect-MsolService**.
  
To verify that you really  *are*  connected to Office 365, run this command.
  
```
Get-MsolDomain
```

Verrà restituito un elemento analogo al seguente:
  
```
Name                         Status          Authentication
----                         ------          --------------
litwareinc.onmicrosoft.com   Verified        Managed
```

### <a name="step-4-connect-to-sharepoint-online"></a>Passaggio 4: connessione a SharePoint Online
<a name="Step4"> </a>

Importare la funzionalità di SharePoint Online con il comando seguente:
  
```
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
```

The  _DisableNameChecking_ switch suppresses this warning.
  
```
WARNING: The names of some imported commands from the module 'Microsoft.Online.SharePoint.PowerShell' include unapproved verbs that might make them less discoverable. To find the commands with unapproved verbs, run the Import-Module command again with the Verbose parameter. For a list of approved verbs, type Get-Verb.
```

In order to connect to SharePoint Online, you need to supply two pieces of information: your credentials and the URL of your SharePoint Online admin site. The credentials part is easy: we've already stored that in the variable  `$credential` (see [Step 2: Create a Windows PowerShell credentials object](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)). As for the URL of your admin site, that's easy enough to determine, as well. Suppose your Office 365 domain name is  `litwareinc.onmicrosoft.com`.
  
Per determinare l'URL del sito di amministrazione, effettuare la seguente operazione:
  
1. Innanzitutto, utilizzare il prefisso `https://`.
    
2. Aggiungere la parte host di dominio del nome del dominio. Ad esempio, per `litwareinc.onmicrosoft.com`, il nome di dominio host è `litwareinc`. Per `contoso.onmicrosoft.com`, il nome di dominio host è `contoso`.
    
3. Add a hyphen (-) followed by  `admin.sharepoint.com`.
    
In altre parole:
  
 `https://` + `litwareinc` + `-admin.sharepoint.com` = `https://litwareinc-admin.sharepoint.com`
  
Dopo aver creato l'URL, è possibile utilizzare quindi questo URL e l'oggetto credenziali per connettersi a SharePoint Online. Chiamare il cmdlet [Connect-SPOService](https://go.microsoft.com/fwlink/p/?LinkId=532436) con un comando simile al seguente.
  
```
Connect-SPOService -Url https://litwareinc-admin.sharepoint.com -credential $credential
```

Per verificare che sia stata effettuata la connessione, eseguire il seguente comando di Windows PowerShell.
  
```
Get-SPOSite
```

È consigliabile ottenere un elenco di tutti i siti di SharePoint Online. Di seguito è riportato un esempio:
  
```
Url                                       Owner          Storage Quota
---                                       -----          -------------
http://litwareinc-public.sharepoint.com/                 1000
https://litwareinc.sharepoint.com/                       1000
https://litwareinc.sharepoint.com/search                 1000
```

I comandi di Office 365 (quelle descritte in [passaggio 3: connettersi a Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) verrà funzionino come previsto. (Provare a eseguire **Get-MsolUser**e di valutare personalmente) Ciò significa che è possibile gestire Office 365 e SharePoint Online dalla stessa istanza di Windows PowerShell.
  
### <a name="step-5-connect-to-skype-for-business-online"></a>Passaggio 5: Connessione a Skype for Business online
<a name="Step5"> </a>

Connessione a Skype Business online (e per Exchange Online o la sicurezza &amp; centro conformità) è diverso rispetto alla connessione a Office 365 o SharePoint Online. Ciò avviene perché Skype per cmdlet Business Online ed Exchange Online non ottenere installato nel computer in uso come avviene per Office 365 e i cmdlet di SharePoint Online. In realtà, ogni volta che si effettua l'accesso, i cmdlet appropriati temporaneamente vengono copiati nel computer. Quando si accede, questi cmdlet vengono rimossi dal computer dell'utente.
  
Per connettersi al Skype Business online, è necessario importarlo Skype di funzionalità di Business in linea. A tale scopo, eseguire questo comando.
  
```
Import-Module SkypeOnlineConnector
```

La prima volta, potrebbe essere visualizzato il seguente messaggio di avviso, che può essere ignorato senza problemi.
  
```
WARNING: WSMan NetworkDelayms has been set to 30000 milliseconds. The previous value was 5000 milliseconds.
WARNING: To improve the performance of the Lync Online Connector, it is recommended that the network delay be set to
30000 milliseconds (30 seconds). However, you can use Set-WinRMNetworkDelayMS to change the network delay to any
integer value.
```

Una volta importato il modulo, eseguire il comando riportato di seguito.
  
```
$sfboSession = New-CsOnlineSession -Credential $credential
```

We have created a remote PowerShell session. In this case, that means that we've connected to an instance of Windows PowerShell running on one of the Office 365 servers. 
  
Anche se è stata effettuata una connessione a Office 365, è non scaricare gli script, i cmdlet e altri elementi necessari per gestire Skype Business online. A tale scopo, è necessario eseguire questo comando.
  
```
Import-PSSession $sfboSession
```

Quando si importa la sessione Windows PowerShell, è necessario visualizzare una barra di stato simile al seguente, un indicatore che segnala in tutti i Skype per cmdlet Business Online da importare nel computer.
  
![Barra di stato di Lync Online.](images/o365_powershell_lync_progress_bar.png)
  
Quando la barra di avanzamento scompare, verrà visualizzato un risultato analogo al seguente.
  
```
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     1.0        tmp_swc5mp4v.1ck  {Copy-CsVoicePolicy, Disabl...
```

### <a name="step-6-connect-to-exchange-online"></a>Passaggio 6: Connessione a Exchange Online
<a name="Step6"> </a>

Eseguire questo comando, che consente di creare una sessione remota di Windows PowerShell con Exchange Online.
  
```
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
```

> [!NOTE]
> È il comando per la connessione a Exchange Online più complicati di comando per connettersi a Skype Business online? Tecnicamente, non è: entrambi i comandi eseguono nello stesso modo. Tuttavia Skype per team Business Online creato il proprio cmdlet: **New-CsOnlineSession** , ovvero che nasconde alcuni dei parametri (ad esempio, _l'autenticazione_ e _AllowRedirection_) che vengono utilizzati durante la connessione a Exchange Online. Invece di utilizzarlo sarà necessario digitare direttamente tali informazioni, i parametri di _autenticazione_ e _AllowRedirection_ sono in modo efficace incorporati per il cmdlet **New-CsOnlineSession** . È necessario digitare questi parametri durante la connessione a Exchange Online poiché in Exchange Online, viene utilizzato il cmdlet [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621) standard per la connessione a Office 365. Lo svantaggio è la presenza di più digitando a tale. Il vantaggio è che non è necessario scaricare e installare un modulo di Exchange Online.
  
È necessario effettuare è fare importare questa sessione remota, così come sono state eseguite con Skype Business online.
  
```
Import-PSSession $exchangeSession -DisableNameChecking
```

Sullo schermo verranno visualizzati elementi analoghi a quelli riportati di seguito.
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_nweiqjvl.geu {Add-AvailabilityAddressSpace...
```

Provare ora a eseguire questo comando.
  
```
Get-AcceptedDomain
```

In return, you should see information about your Office 365 domains that are configured for email addresses in Exchange Online.
  
```
Name            DomainName          DomainType      Default
----            ----------          ----------      -------
litwareinc.com  litwareinc.com      Authoritative   True
```

### <a name="step-7-connect-to-the-security-amp-compliance-center"></a>Passaggio 7: Connessione per la protezione &amp; centro conformità
<a name="Step7"> </a>

La sicurezza &amp; centro conformità è un servizio disponibile in Office 365 che consente all'utente per gestire le funzionalità di conformità da una posizione. Per ulteriori informazioni, vedere [centro conformità di Office 365](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx).
  
Le istruzioni di connessione per la sicurezza &amp; centro conformità sono molto simili a quelle per Exchange Online, ma con una rotazione sono state aggiunte, verrà visualizzato in un momento.
  
Eseguire questo comando, che consente di creare una sessione remote PowerShell con la protezione &amp; centro conformità.
  
```
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
```

A questo punto, eseguire il comando seguente.
  
```
Import-PSSession $ccSession -Prefix cc
```

Again, this command is very similar to the command for Exchange Online. The  _DisableNameChecking_ switch isn't required because there are no unapproved verbs in the Security &amp; Compliance Center. But what about that additional `-Prefix cc` parameter and value? That's the added twist we told you about.
  
Exchange Online e la sicurezza &amp; centro conformità condividere alcuni cmdlet esattamente gli stessi nomi e fornisce le stesse funzionalità. **Get-RoleGroup** è riportato un esempio.
  
Pertanto, cosa succede se si tenta di importare le due sessioni che contengono cmdlet con lo stesso nome? Si verifica un conflitto. Verrà visualizzato un messaggio di avviso giallo big che informa che, `WARNING: Proxy creation has been skipped for the following command:` seguito dall'elenco dei cmdlet in conflitto che non è stato importato. Il risultato finale? È possibile eseguire **Get-RoleGroup** in Exchange Online perché si è connessi vi prima, ma non è possibile eseguire **Get-RoleGroup** per la protezione &amp; Allinea al centro conformità perché si è connessi vi ultimo e i cmdlet in conflitto rifiutate da importare.
  
Il modo più semplice per affrontare il problema consiste nell'aggiungere un prefisso di testo arbitrario per la protezione importata &amp; cmdlet centro conformità. Sono state eseguite che utilizzano il parametro _Prefix_ con il valore "cc" nel cmdlet **Import-PSSession** . Cosa che per noi? Eliminava conflitti modificando (leggermente) la sicurezza &amp; i nomi dei cmdlet di centro conformità per la sessione corrente. Le impostazioni di protezione importata &amp; centro conformità cmdlet ora iniziano con "cc" nella parte del nome del cmdlet sostantivo (a destra del "-"). Ad esempio, il cmdlet **Get-RoleGroup** oggetto di controversia diventa **Get-ccRoleGroup** per la sicurezza &amp; centro conformità in modo che non sia in conflitto con **Get-RoleGroup** per Exchange Online.
  
Lo svantaggio?  *Tutti i*  Protezione &amp; i nomi dei cmdlet di centro conformità viene assegnato il prefisso "cc", ovvero anche cmdlet univoco che non è necessario. Ad esempio, **Get-ComplianceSearch** diventa **Get-ccComplianceSearch** anche se non esiste alcun quali cmdlet di Exchange Online. È un po' di un riquadro, ma non male quando si considerano i vantaggi di gestione di tutti i servizi di Office 365 in una singola sessione di Windows PowerShell. Ricordare di aggiungere "cc" ai nomi di cmdlet per tutte le procedure di sicurezza &amp; centro conformità.
  
Se tutto va bene, la schermata visualizzata sarà simile alla seguente:
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_xbbx5exr.ehm {Add-ccRoleGroupMember, Get-ccAdminAuditLogConfig, Get-ccA...
```

A questo punto è disponibile gestire tutti i servizi di Office 365 in una singola sessione di Windows PowerShell.
  
### <a name="step-8-gracefully-end-your-powershell-sessions"></a>Passaggio 8: Terminare normalmente le sessioni di PowerShell
<a name="Step8"> </a>

If you just close the Windows PowerShell window, your Skype for Business Online remote connection will remain active for the next 15 minutes or so. Because Skype for Business Online limits the number of simultaneous connections that any one person or any one domain can have open, that could be a problem. With Skype for Business Online, an individual administrator can have, at most, three open connections at one time, and a domain can have a maximum of nine open connections. If you sign in to Skype for Business Online and then exit without properly closing the session, that session remains open for the next 15 minutes or so. As a result, that's one fewer connection available to you or to other administrators in your domain.
  
In realtà, possiamo chiudere le sessioni remote per Skype per Business Online, Exchange Online e la sicurezza &amp; del centro conformità normalmente. Prima di procedere è il seguente comando.
  
```
Get-PSSession
```

Il cmdlet [Get-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) dovrebbe essere inclusa la presenza di almeno tre sessioni remote Apri, uno per Skype Business online, uno per Exchange Online e uno per la sicurezza &amp; centro conformità (è possibile è possibile avere più di tre remote sessioni in esecuzione, a seconda se si utilizza questa istanza di Windows PowerShell per connettersi a un parametro oltre ai servizi Office 365). Verrà visualizzato qualcosa di simile al seguente.
  
```
Id Name     ComputerName     State   ConfigurationName    Availability
-- ----     ------------     -----   -----------------    ------------
 1 Session1 webdir0a.onl...  Opened  Microsoft.PowerShell    Available
 2 Session2 outlook.offi...  Opened  Microsoft.Exchange      Available
 3 Session3 ps.complianc...  Opened  Microsoft.Exchange      Available
```

Per chiudere le sessioni di tre, eseguire questi comandi uno alla volta. Il primo comando viene chiuso il Skype per sessione in linea aziendale, la seconda viene chiusa la sessione di Exchange Online, e la terza chiude la sicurezza &amp; sessione centro conformità.
  
```
Remove-PSSession $sfboSession
Remove-PSSession $exchangeSession
Remove-PSSession $ccSession
```

If you now run the **Get-PSSession** cmdlet, you should see nothing at all (unless you have other remote sessions up and running).
  
![Console di Windows PowerShell senza sessioni remote](images/o365_powershell_no_remote_sessions.png)
  
> [!NOTE]
> Se si preferisce chiudere tutte le sessioni remote contemporaneamente, è possibile utilizzare questo comando: >`Get-PSSession | Remove-PSSession`
  
Se si prova a eseguire un cmdlet da uno di questi chiuso sessioni (ad esempio, **Get-CsMeetingConfiguration** in Skype Business online) verrà visualizzato un messaggio di errore simile al seguente.
  
```
Get-CsMeetingConfiguration : The term 'Get-CsMeetingConfiguration' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
```

Tale messaggio di errore viene visualizzato poiché i cmdlet per Skype per Business Online, Exchange Online e la sicurezza &amp; centro conformità sono stati eliminati quando viene chiuso le sessioni remote.
  
To close the SharePoint Online session, type this command.
  
```
Disconnect-SPOService
```

If you now try to run the **Get-SPOSite** cmdlet, you'll get an error message like this.
  
```
get-sposite : No connection available. Use Connect-SPOService before running this CmdLet.
```

You can't retrieve site information because you're no longer connected to SharePoint Online.
  
As for your connection to Office 365, although there's a **Connect-MsolService** cmdlet, there's no corresponding **Disconnect-MsolService** cmdlet. So for Office 365, just close the Windows PowerShell window. Nevertheless, it's still a good idea to do this last so you can properly disconnect from SharePoint Online, Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center.
  
## <a name="new-to-office-365"></a>Nuovo utente di Office 365?
<a name="LongVersion"> </a>

||
|:-----|
|![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning. |
   
## <a name="see-also"></a>Vedere anche

#### 

[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)
  
[Gestire SharePoint Online con PowerShell di Office 365](manage-sharepoint-online-with-office-365-powershell.md)
  
[Gestire gli account utente e le licenze con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Utilizzo di Windows PowerShell per creare rapporti in Office 365](use-windows-powershell-to-create-reports-in-office-365.md)

