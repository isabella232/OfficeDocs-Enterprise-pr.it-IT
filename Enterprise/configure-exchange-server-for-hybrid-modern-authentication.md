---
title: Come configurare Exchange Server locale per utilizzare l'autenticazione moderna ibrida
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/16/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
description: L'autenticazione moderna ibrida (HMA), è un metodo di gestione delle identità che offre un'autenticazione e un'autorizzazione utente più sicure ed è disponibile per le distribuzioni ibride locali di Exchange Server.
ms.openlocfilehash: 44061a8b75a07283c36d02812488441d40f9c9c3
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2019
ms.locfileid: "38746219"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Come configurare Exchange Server locale per utilizzare l'autenticazione moderna ibrida

*Questo articolo si applica sia a Office 365 Enterprise che a Microsoft 365 Enterprise.*

L'autenticazione moderna ibrida (HMA), è un metodo di gestione delle identità che offre un'autenticazione e un'autorizzazione utente più sicure ed è disponibile per le distribuzioni ibride locali di Exchange Server.
  
## <a name="fyi"></a>FYI

Prima di iniziare, chiamo:
  
- HMA di autenticazione \> moderna ibrida
    
- Exch locale \> di Exchange
    
- ESO di \> Exchange Online
    
Inoltre, *se un elemento grafico di questo articolo contiene un oggetto che è' grigio ' o ' oscurato ' che indica che il componente visualizzato in grigio non è incluso nella configurazione specifica di HMA* . 
  
## <a name="enabling-hybrid-modern-authentication"></a>Abilitazione dell'autenticazione moderna ibrida

Se si attiva HMA, significa:
  
1. Assicurarsi di conoscere le prerequisiti prima di iniziare.
    
1. Poiché molti **prerequisiti** sono comuni sia per Skype for business che per Exchange, [Panoramica dell'autenticazione moderna ibrida e prerequisiti per l'utilizzo con i server Skype for business e Exchange locali](hybrid-modern-auth-overview.md). Eseguire questa operazione prima di iniziare una delle procedure descritte in questo articolo.
    
2. Aggiunta di URL di servizi Web locali come nomi dell'entità servizio (SPN, Service Principal Name) in Azure AD.
    
3. Garantire che tutte le directory virtuali siano abilitate per HMA
    
4. Verifica dell'oggetto EvoSTS Auth server
    
5. Abilitazione di HMA in EXCH.
    
 **Note** La versione di MA di supporto di Office? Vedere [come funziona l'autenticazione moderna per le app client di office 2013 e office 2016](modern-auth-for-office-2013-and-2016.md).
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a>Assicurarsi di conoscere tutte le Rich

Poiché molti prerequisiti sono comuni sia per Skype for business che per Exchange, esaminare la [Panoramica dell'autenticazione moderna ibrida e i prerequisiti per l'utilizzo con i server Skype for business e Exchange locali](hybrid-modern-auth-overview.md). Eseguire questa operazione *prima* di iniziare una delle procedure descritte in questo articolo. 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Aggiungere URL dei servizi Web locali come nomi SPN in Azure AD

Eseguire i comandi che assegnano gli URL dei servizi Web locali come SPN AD Azure AD. Gli SPN vengono utilizzati dai computer e dai dispositivi client durante l'autenticazione e l'autorizzazione. Tutti gli URL che possono essere utilizzati per la connessione da locale ad Azure Active Directory (AAD) devono essere registrati in AAD (inclusi gli spazi dei nomi interni ed esterni).
  
In primo luogo, raccogliere tutti gli URL che è necessario aggiungere in AAD. Eseguire questi comandi in locale:
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
Verificare che i client URL a cui possono connettersi siano elencati come nomi dell'entità servizio HTTPS in AAD.
  
1. Per prima cosa, connettersi a AAD con [queste istruzioni](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell). 

 **Note** È necessario utilizzare l'opzione Connect-MsolService di questa pagina per poter utilizzare il comando riportato di seguito. 
    
2. Per gli URL correlati a Exchange, digitare il comando seguente:
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

Prendere nota di (e screenshot per il confronto successivo) l'output di questo comando, che dovrebbe includere un URL di *mail.yourdomain.com* di https:// *autodiscover.yourdomain.com* e https://, ma principalmente costituito da nomi SPN che iniziano con 00000002-0000-0FF1-CE00-000000000000/. Se sono presenti URL di https://da quelli locali mancanti, sarà necessario aggiungere tali record specifici a questo elenco. 
  
3. Se non si visualizzano i record MAPI/HTTP, EWS, ActiveSync, OAB e autodiscover interni ed esterni in questo elenco, è necessario aggiungerli utilizzando il comando riportato di seguito (gli URL`mail.corp.contoso.com`di esempio sono`owa.contoso.com`'' è ', ma si **sostituiscono gli URL di esempio con il proprio** ): <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. Verificare che i nuovi record siano stati aggiunti eseguendo di nuovo il comando Get-MsolServicePrincipal viene del passaggio 2 e analizzando l'output. Confrontare l'elenco/screenshot da prima al nuovo elenco di nomi SPN (è anche possibile schermare il nuovo elenco per i record). In caso di esito positivo, verranno visualizzati i due nuovi URL presenti nell'elenco. In questo esempio, l'elenco dei nomi SPN includerà ora gli URL `https://mail.corp.contoso.com` specifici e `https://owa.contoso.com`. 
  
## <a name="verify-virtual-directories-are-properly-configured"></a>Verificare che le directory virtuali siano configurate correttamente

A questo punto, verificare che OAuth sia abilitato correttamente in Exchange su tutte le directory virtuali che potrebbe essere utilizzato da Outlook eseguendo i seguenti comandi:

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

Controllare l'output per assicurarsi che **OAuth** sia abilitato su ognuna di queste VDirs, avrà un aspetto simile a questo (e la cosa fondamentale da guardare è "OAuth"); 

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
  
Se OAuth non è presente in un server e in una delle quattro directory virtuali, è necessario aggiungerlo usando i comandi rilevanti prima di continuare.
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a>Confermare che l'oggetto server EvoSTS auth sia presente

Tornare alla shell di gestione di Exchange locale per questo ultimo comando. A questo punto è possibile verificare che il provider di autenticazione di evoSTS sia presente in locale:
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

L'output deve mostrare un AuthServer del nome EvoSts e lo stato ' Enabled ' dovrebbe essere vero. Se questa operazione non viene visualizzata, è consigliabile scaricare ed eseguire la versione più recente della procedura guidata di configurazione ibrida.
  
 **Importante** Se si esegue Exchange 2010 nell'ambiente in uso, il provider di autenticazione di EvoSTS non verrà creato. 
  
## <a name="enable-hma"></a>Abilitare HMA

Eseguire il seguente comando in Exchange Management Shell, in locale:

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a>Verificare

Dopo aver abilitato HMA, l'account di accesso successivo di un client utilizzerà il nuovo flusso di autenticazione. Si noti che l'attivazione di HMA non attiverà una nuova autenticazione per un client. I client eseguono di nuovo l'autenticazione in base alla durata dei token di autenticazione e/o ai cert che dispongono.
  
È inoltre necessario tenere premuto il tasto CTRL contemporaneamente facendo clic con il pulsante destro del mouse sull'icona per il client di Outlook (anche nel vassoio notifiche di Windows) e facendo clic su' stato connessione '. Cercare l'indirizzo SMTP del client rispetto a un tipo ' AuthN ' di ' latore\*', che rappresenta il token del portatore utilizzato in OAuth.
  
 **Note** È necessario configurare Skype for business con HMA? Sono necessari due articoli: uno che elenca le [topologie supportate](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)e uno che illustra [come eseguire la configurazione](configure-skype-for-business-for-hybrid-modern-authentication.md).
  

## <a name="related-topics"></a>Argomenti correlati

[Panoramica dell'autenticazione moderna ibrida e prerequisiti per l'utilizzo con i server Skype for business e Exchange locali](hybrid-modern-auth-overview.md) 
  

