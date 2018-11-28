---
title: Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/27/2018
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
description: "Riepilogo: Connessione di Windows PowerShell per tutti i servizi di Office 365 in un'unica finestra di Windows PowerShell."
ms.openlocfilehash: 5635cf8b03490c2b2f811f22c231c271d5204552
ms.sourcegitcommit: 65de707bd1c389eea48767a68c31032dd5198359
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2018
ms.locfileid: "26706690"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell

 **Riepilogo:** Invece di gestire diversi servizi di Office 365 nelle finestre di console PowerShell separate, è possibile connettersi a tutti i servizi di Office 365 e gestirli da unica finestra della console.
  
Quando si utilizza PowerShell per gestire Office 365, è possibile avere fino a cinque sessioni diverse di Windows PowerShell aprire contemporaneamente corrispondente all'interfaccia di amministrazione di Office 365, SharePoint Online, Exchange Online, Skype Business online e la protezione &amp;Centro conformità. Con i metodi di connessione differenti cinque sessioni di Windows PowerShell distinti, il desktop è simile al seguente:
  
![Cinque console di Windows PowerShell in esecuzione contemporaneamente](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
Questo non è ottimale per la gestione di Office 365 perché non è possibile scambiare dati tra i cinque windows per la gestione dei servizi tra. In questo argomento viene descritto come utilizzare una singola istanza di Windows PowerShell da cui è possibile gestire Office 365, Skype Online Business, Exchange Online, SharePoint Online e la sicurezza &amp; centro conformità.

>[!Note]
>In questo articolo sono attualmente solo i comandi per la connessione al cloud di Office 365 nel mondo (+ GCC). Note aggiuntive disponibili collegamenti ad articoli con informazioni sulla connessione per le altre aree di Office 365.
>

## <a name="before-you-begin"></a>Prima di iniziare

Per poter gestire tutti di Office 365 da una singola istanza di Windows PowerShell, prendere in considerazione i prerequisiti seguenti:
  
- Office 365 di lavoro o scuola che l'account utilizzato per queste procedure esigenze per essere un membro di un ruolo di amministrazione di Office 365. Per ulteriori informazioni, vedere [ruoli di amministratore su Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Questo requisito per Office 365 PowerShell, non necessariamente per tutti gli altri servizi di Office 365.
    
- È possibile utilizzare le seguenti versioni a 64 bit di Windows:
    
  - Windows 10
    
  - Windows 8.1 o Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 o Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*È necessario installare Microsoft .NET Framework 4.5. *x* e quindi su Windows Management Framework 3.0 o Windows Management Framework 4.0. Per ulteriori informazioni, vedere [installazione di .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) e [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) o [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    È necessario utilizzare una versione a 64 bit di Windows per i requisiti per il Skype per la funzionalità di Business in linea e uno dei moduli di Office 365.
    
- È necessario installare i moduli che sono necessari per Azure Active Directory, SharePoint Online e Skype Business online:
    
   - [V2 Azure Active Directory](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype per le aziende in linea, modulo di Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell deve essere configurato per l'esecuzione di script con firma per Skype per Business Online, Exchange Online e la sicurezza &amp; centro conformità. A tale scopo, eseguire il comando seguente in una sessione di Windows PowerShell con privilegi elevata (una finestra di Windows PowerShell per aprire è selezionare **Esegui come amministratore**).
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a>Passaggi di connessione quando si utilizza una password

Ecco la procedura per la connessione a tutti i servizi in un'unica finestra di PowerShell.
  
1. Aprire Windows PowerShell come amministratore (utilizzare **Esegui come amministratore**).
    
2. Eseguire questo comando e immettere il lavoro di Office 365 o scuola le credenziali dell'account.
    
  ```
  $credential = Get-Credential
  ```

3. Eseguire questo comando per la connessione di Azure Active Directory (AD) con Azure Active Directory PowerShell modulo grafico.
    
  ```
   Connect-AzureAD -Credential $credential
  ```
  
  In alternativa, se si utilizza la funzionalità di Microsoft Azure Active Directory Module per Windows PowerShell, eseguire questo comando.
      
  ```
   Connect-MsolService -Credential $credential
 ```

4. Eseguire questi comandi per la connessione a SharePoint Online. Sostituire _ \<domainhost >_ con il valore effettivo per il dominio. Ad esempio, per "litwareinc.onmicrosoft.com", il _ \<domainhost >_ valore è "litwareinc".
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. Eseguire questi comandi a cui connettersi Skype Business online. Un avviso che indica l'aumento di `WSMan NetworkDelayms` valore previsto per la prima volta la connessione e deve essere ignorato.
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Eseguire questi comandi per la connessione a Exchange Online.
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession
  ```

>[!Note]
>Per connettersi a Exchange Online per Office 365 cloud diverso da tutto il mondo, vedere [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).
>

7. Eseguire questi comandi per la connessione per la protezione &amp; centro conformità.
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
>Per connettersi alla protezione &amp; centro conformità per Office 365 cloud diverso da tutto il mondo, vedere [Connect to Office 365 Security & PowerShell centro conformità](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).
>

Di seguito sono tutti i comandi in un unico blocco quando si utilizza Azure Active Directory PowerShell modulo grafico. Specificare il nome dell'host del dominio e quindi eseguire tutte contemporaneamente.
  
```
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

In alternativa, ecco tutti i comandi in un unico blocco quando si utilizza la funzionalità di Microsoft Azure Active Directory Module per Windows PowerShell. Specificare il nome dell'host del dominio e quindi eseguire tutte contemporaneamente.
  
```
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

Quando è pronti per chiudere la finestra di Windows PowerShell, eseguire questo comando per rimuovere le sessioni attive per Skype per Business Online, Exchange Online, SharePoint Online e la sicurezza &amp; centro conformità:
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Passaggi di connessione quando si utilizza l'autenticazione a più fattori

Di seguito sono tutti i comandi in un unico blocco a cui connettersi Azure Active Directory, SharePoint Online e Skype per Buiness con l'autenticazione a più fattori in un'unica finestra. Specificare il nome di utente nome principale (UPN) di un account amministratore globale e il nome host del dominio e quindi eseguire tutte contemporaneamente.

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

In alternativa, ecco tutti i comandi quando si utilizza la funzionalità di Microsoft Azure Active Directory Module per Windows PowerShell.

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

Per Exchange Online e la sicurezza &amp; centro conformità, vedere gli argomenti seguenti per la connessione con l'autenticazione a più fattori:

- [Connettersi a PowerShell di Exchange Online utilizzando l'autenticazione a più fattori](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [Connettersi alla sicurezza di Office 365 PowerShell centro conformità con l'autenticazione a più fattori](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
Si noti che in entrambi i casi, è necessario connettersi utilizzando sessioni separate di Exchange Online Remote PowerShell Module.


## <a name="see-also"></a>Vedere anche

- [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md)
- [Gestire SharePoint Online con PowerShell di Office 365](manage-sharepoint-online-with-office-365-powershell.md)
- [Gestire gli account utente e le licenze con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Utilizzo di Windows PowerShell per creare rapporti in Office 365](use-windows-powershell-to-create-reports-in-office-365.md)
