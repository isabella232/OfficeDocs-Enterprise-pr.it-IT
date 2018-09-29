---
title: Come configurare Exchange Server locale per utilizzare l'autenticazione moderna ibrida
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 09/28/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: Ibrida moderno autenticazione (alta), è un metodo di gestione delle identità che offre maggiore protezione l'autenticazione degli utenti e l'autorizzazione ed è disponibile per le distribuzioni ibride di Exchange server locale.
ms.openlocfilehash: 4267eaff8dfce71461f230310141a98be8a39e80
ms.sourcegitcommit: 9f921c0cae9a5dd4e66ec1a1261cb88284984a91
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/28/2018
ms.locfileid: "25347606"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Come configurare Exchange Server locale per utilizzare l'autenticazione moderna ibrida

Ibrida moderno autenticazione (alta), è un metodo di gestione delle identità che offre maggiore protezione l'autenticazione degli utenti e l'autorizzazione ed è disponibile per le distribuzioni ibride di Exchange server locale.
  
## <a name="fyi"></a>MONEY

Prima di procedere, è possibile chiamare:
  
- Autenticazione moderno ibrida \> alta
    
- Exchange locale \> EXCH
    
- Exchange Online \> EXO
    
Inoltre, *che se un'immagine in questo articolo include un oggetto che è "inattivo" o inattivo pertanto, l'elemento visualizzato in grigio non è incluso nella configurazione alta specifiche* . 
  
## <a name="enabling-hybrid-modern-authentication"></a>Abilitazione dell'autenticazione moderno ibrido

Attivazione alta indica:
  
1. Verificando che vengano soddisfatti i prerequisiti prima di iniziare.
    
1. Rispetto a molti **Prerequisiti** sono comuni per entrambi Skype per le aziende ed Exchange, [Panoramica dell'autenticazione moderno ibrida e prerequisiti per l'utilizzo con locale Skype per Business ed Exchange Server](hybrid-modern-auth-overview.md). Eseguire questa operazione prima di eseguire le procedure descritte in questo articolo.
    
2. Aggiunta di locale URL del servizio web come nomi delle entità servizio (SPN) in Azure Active Directory.
    
3. Verifica tutte le directory virtuali sono abilitate per alta
    
4. Verifica dell'oggetto Server di autenticazione EvoSTS
    
5. Abilitazione di alta in tassi di cambio
    
 **Nota** La versione di Office supporta agente di gestione? Vedere [come moderno funzionamento dell'autenticazione per le applicazioni client di Office 2013 e Office 2016](modern-auth-for-office-2013-and-2016.md).
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a>Verificare che siano soddisfatti tutti i codice prerequisiti

Poiché molti prerequisiti sono comuni per entrambi Skype per le aziende ed Exchange, leggere [Panoramica dell'autenticazione moderno ibrida e prerequisiti per l'utilizzo con Skype locale per Business ed Exchange Server](hybrid-modern-auth-overview.md). Questo *prima di* iniziare le procedure descritte in questo articolo. 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Aggiungere locale web service URL come nomi SPN in Azure Active Directory

Eseguire i comandi che è necessario assegnare il web locale gli URL del servizio nomi SPN con Azure Active Directory nomi SPN. utilizzati dal computer client e dispositivi durante l'autenticazione e autorizzazione. Tutti gli URL che possono eventualmente essere utilizzati per la connessione in locale per Azure Active Directory (AAD) devono essere registrati in AAD (include spazi dei nomi interni ed esterni).
  
Innanzitutto, raccogliere tutti gli URL che si devono aggiungere AAD. Eseguire questi comandi locale:
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
Verificare che gli URL client possono connettersi a elencato come nomi delle entità servizio HTTPS in AAD.
  
1. Innanzitutto, connettersi a AAD con [le relative istruzioni](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell).
    
2. Per lo scambio correlati URL, digitare il comando seguente:
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

Prendere nota delle (e cattura di schermata per un confronto successivo) l'output di questo comando, che deve includere un https:// *autodiscover.yourdomain.com* e URL https:// *mail.yourdomain.com* , ma sono costituiti principalmente nomi dell'entità servizio che iniziano con 00000002-0000-0ff1-CE00-000000000000 /. Se sono presenti gli URL https:// da locale che risultano mancanti è necessario aggiungere i record specifici a questo elenco. 
  
3. Se i record MAPI su HTTP, servizi Web Exchange, ActiveSync, della Rubrica offline e l'individuazione automatica interni ed esterni in questo elenco non viene visualizzata, è necessario aggiungerli tramite il comando riportato di seguito (nell'esempio gli URL sono '`mail.corp.contoso.com`'e'`owa.contoso.com`', ma è possibile **sostituire l'URL di esempio con il proprio** ) : <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
$x.ServicePrincipalnames.Add("https://eas.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. Verificare che i nuovi record sono stati aggiunti eseguire nuovamente il comando Get-MsolServicePrincipal del passaggio 2 ed esaminando attraverso l'output. Confrontare l'elenco / schermata prima per il nuovo elenco di nomi SPN (può inoltre essere cattura di schermata del nuovo elenco per i record). Se hanno avuto esito positivo, verrà visualizzato due nuovi URL nell'elenco. Passando dall'esempio, l'elenco di nomi SPN ora includerà URL specifici `https://mail.corp.contoso.com` e `https://owa.contoso.com`. 
  
## <a name="verify-virtual-directories-are-properly-configured"></a>Verificare che le directory virtuali sono configurate correttamente

A questo punto verificare OAuth è abilitato correttamente in Exchange in tutti i Outlook le directory virtuali potrebbe utilizzare eseguendo i seguenti comandi:

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

Controllo dell'output per verificare che **OAuth** è abilitata su ciascuno di questi virtuali, sarà simile al seguente (e l'aspetto principale da esaminare 'OAuth'); 

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*
```

```
Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```
  
Se non è presente alcun server e delle directory virtuali di quattro OAuth è necessario aggiungerlo utilizzando i comandi desiderati prima di procedere.
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a>Verificare che l'oggetto Server di autenticazione EvoSTS è presente

Tornare a locale Exchange Management Shell per questo ultimo comando eseguito. È ora possibile convalidare locale che dispone di una voce per il provider di autenticazione evoSTS:
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

L'output dovrebbe essere visualizzato un AuthServer di EvoSts nome e lo stato 'Enabled' deve essere True. Se non è visualizzata, è necessario scaricare ed eseguire la versione più recente della procedura guidata di configurazione ibrida.
  
 **Importante** Se si esegue Exchange 2010 nell'ambiente in uso, non verrà creato il provider di autenticazione EvoSTS. 
  
## <a name="enable-hma"></a>Abilitare alta

Eseguire il seguente comando in Exchange Management Shell in locale:

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a>Verifica

Se si abilita alta, successivo account di accesso del client utilizzerà il nuovo flusso di autenticazione. Si noti che solo attivando alta non verrà attivato una nuova autenticazione per ogni client. Il client ad autenticarsi in base alla durata di token di autenticazione e/o hanno i certificati.
  
È inoltre deve tenere premuto il tasto CTRL contemporaneamente a destra fare clic sull'icona per il client di Outlook (anche nella barra delle applicazioni Windows Notifications) e fare clic su 'stato di connessione. Cercare l'indirizzo SMTP del client in base a un tipo di 'Uso' del ' portanti\*", che rappresenta il token portanti utilizzato in OAuth.
  
 **Nota** È necessario configurare Skype for Business con alta? È necessario due articoli: uno che elenca [topologie supportate](https://technet.microsoft.com/en-us/library/mt803262.aspx)e uno che viene illustrato [come eseguire la configurazione](configure-skype-for-business-for-hybrid-modern-authentication.md).
  

## <a name="related-topics"></a>Argomenti correlati

[Cenni preliminari sull'autenticazione moderno ibrida e prerequisiti per l'utilizzo con Skype locale per Business ed Exchange Server](hybrid-modern-auth-overview.md) 
  

