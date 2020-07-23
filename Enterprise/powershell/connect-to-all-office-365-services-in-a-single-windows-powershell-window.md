---
title: Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/10/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: "Riepilogo: connettere Windows PowerShell a tutti i servizi Microsoft 365 in un'unica finestra di Windows PowerShell."
ms.openlocfilehash: a037de53dcbf8fed95b9b4d5f05677997135dfb3
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230842"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window"></a>Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell

Quando si utilizza PowerShell per gestire Microsoft 365, è possibile che siano disponibili fino a cinque sessioni di Windows PowerShell diverse contemporaneamente corrispondenti all'interfaccia di amministrazione di Microsoft 365, SharePoint Online, Exchange Online, Skype for business online, Microsoft teams e il Centro sicurezza e &amp; conformità. Con cinque diversi metodi di connessione in sessioni di Windows PowerShell separate, il desktop potrebbe essere simile al seguente:
  
![Cinque console di Windows PowerShell in esecuzione contemporaneamente](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
Questo non è ottimale per la gestione di Microsoft 365 perché non è possibile scambiare dati tra queste cinque finestre per la gestione interservizi. In questo argomento viene descritto come utilizzare una singola istanza di Windows PowerShell da cui è possibile gestire gli account Microsoft 365, Skype for business online, Exchange Online, SharePoint Online, Microsoft teams e il Centro sicurezza e &amp; conformità.

>[!Note]
>Questo articolo contiene attualmente solo i comandi per la connessione al cloud globale (+ GCC). Altre note forniscono collegamenti ad articoli contenenti informazioni sulla connessione alle altre cloud di Microsoft 365.
>

## <a name="before-you-begin"></a>Informazioni preliminari

Prima di poter gestire tutto Microsoft 365 da una singola istanza di Windows PowerShell, prendere in considerazione i prerequisiti seguenti:
  
- L'account aziendale o dell'Istituto di istruzione Microsoft 365 utilizzato per queste procedure deve essere membro di un ruolo di amministratore di Microsoft 365. Per altre informazioni, vedere [Informazioni sui ruoli di amministratore](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide). Questo è un requisito per PowerShell per Microsoft 365, non necessariamente per tutti gli altri servizi di Microsoft 365.
    
- È possibile utilizzare le seguenti versioni a 64 bit di Windows:
    
  - Windows 10
    
  - Windows 8.1 o Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 o Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*È necessario installare Microsoft .NET Framework 4,5. *x* e quindi Windows management Framework 3,0 o Windows management Framework 4,0. Per ulteriori informazioni, vedere [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) o [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    È necessario utilizzare una versione di Windows a 64 bit a causa dei requisiti per il modulo Skype for business online e uno dei moduli di Microsoft 365.
    
- È necessario installare i moduli necessari per Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype for business online e teams:
    
   - [Azure Active Directory V2](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype for Business Online, modulo Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [Exchange Online PowerShell V2](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [Panoramica di PowerShell Teams](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  Windows PowerShell deve essere configurato per l'esecuzione di script firmati per Skype for business online e il Centro sicurezza e &amp; conformità. A tale scopo, eseguire il comando riportato di seguito in una sessione di Windows PowerShell con privilegi elevati (una finestra di Windows PowerShell che si apre selezionando **Esegui come amministratore**).
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-just-a-password"></a>Passaggi di connessione quando si utilizza solo una password

Di seguito sono riportati i passaggi da eseguire per la connessione a tutti i servizi in una singola finestra di PowerShell quando si utilizza solo una password per l'accesso.
  
1. Aprire Windows PowerShell.
    
2. Eseguire questo comando e immettere le credenziali dell'account aziendale o dell'Istituto di istruzione Microsoft 365.
    
  ```powershell
  $credential = Get-Credential
  ```

3. Eseguire questo comando per connettersi ad Azure AD utilizzando il modulo di Azure Active Directory PowerShell per Graph.
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  In alternativa, se si utilizza il modulo modulo di Microsoft Azure Active Directory per Windows PowerShell, eseguire questo comando.
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
>PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per Windows PowerShell e i cmdlet con **MSOL** all'interno del nome. Per continuare a usare i cmdlet, è necessario eseguirli in Windows PowerShell.
>

4. Eseguire questi comandi per connettersi a SharePoint Online. Specificare il nome dell'organizzazione per il dominio. Ad esempio, per "litwareinc.onmicrosoft.com", il valore del nome dell'organizzazione è "litwareinc".
    
  ```powershell
  $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
  Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $userCredential
  ```

5. Eseguire questi comandi per connettersi a Skype for business online. Un avviso relativo all'aumento del `WSMan NetworkDelayms` valore è previsto per la prima volta che si connette e deve essere ignorato.
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Eseguire questo comando per connettersi a Exchange Online.
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
>Per connettersi a Exchange Online per Microsoft 365 nuvole diverse da quelle di tutto il mondo, utilizzare il parametro **-ExchangeEnvironmentName** . Per ulteriori informazioni, vedere [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) .
>

7. Eseguire questi comandi per connettersi ai team di PowerShell.
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
>Per connettersi a cloud di Microsoft teams diversi da quelli di tutto il mondo, vedere [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).
>

8. Eseguire questi comandi per connettersi al centro sicurezza e &amp; conformità.
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
>Per connettersi al centro sicurezza e &amp; conformità per Microsoft 365 nuvole diverse da tutto il mondo, vedere [Connect to Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).
>

Di seguito sono riportati tutti i comandi in un singolo blocco quando si utilizza il modulo di Azure Active Directory PowerShell per Graph. Specificare il nome dell'host di dominio e quindi eseguirli contemporaneamente.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

In alternativa, ecco tutti i comandi in un singolo blocco quando si utilizza il modulo modulo di Microsoft Azure Active Directory per Windows PowerShell. Specificare il nome dell'host di dominio e quindi eseguirli contemporaneamente.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

Quando si è pronti per chiudere la finestra di Windows PowerShell, eseguire il comando seguente per rimuovere le sessioni attive in Skype for business online, SharePoint Online, il &amp; Centro sicurezza e conformità e i team:
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Passaggi di connessione quando si utilizza l'autenticazione a più fattori

Di seguito sono riportati tutti i comandi di un singolo blocco per la connessione ad Azure AD, SharePoint Online, Skype for business, Exchange Online e i team che utilizzano l'autenticazione a più fattori in una singola finestra utilizzando il modulo Azure Active Directory PowerShell per Graph. Specificare il nome dell'entità utente (UPN, User Principal Name) di un account utente e il nome host del dominio, quindi eseguirli contemporaneamente.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

In alternativa, ecco tutti i comandi quando si utilizza il modulo di Microsoft Azure Active Directory Module per Windows PowerShell.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

Per il &amp; Centro sicurezza e conformità, vedere [Connect to Security & Compliance Center PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) to Connect using multi-factor authentication:

## <a name="see-also"></a>Vedere anche

- [Collegare Microsoft 365 con PowerShell](connect-to-office-365-powershell.md)
- [Gestire SharePoint Online con PowerShell](manage-sharepoint-online-with-office-365-powershell.md)
- [Gestire gli account utente, le licenze e i gruppi di Microsoft 365 con PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Utilizzo di Windows PowerShell per la creazione di report in Microsoft 365](use-windows-powershell-to-create-reports-in-office-365.md)
