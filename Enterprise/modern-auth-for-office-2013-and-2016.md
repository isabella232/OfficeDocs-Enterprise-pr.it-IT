---
title: Funzionamento dell'autenticazione moderna per le applicazioni client di Office 2013 e Office 2016
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/1/2017
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- GMA150
- GPA150
- GEA150
- BCS160
ms.assetid: e4c45989-4b1a-462e-a81b-2a13191cf517
description: Informazioni su Office 365 moderno funzionamento dell'autenticazione in modo diverso per Office 2013 e applicazioni client 2016.
ms.openlocfilehash: 2a5e218ca751f341e2a3a0ffd164f000ee503279
ms.sourcegitcommit: fd7a56f38ba2c2d2e7fcd6e165ec58b31be299d9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2018
ms.locfileid: "27378502"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>Funzionamento dell'autenticazione moderna per le applicazioni client di Office 2013 e Office 2016

Leggere questo articolo per informazioni su come utilizzano funzionalità di autenticazione moderno Office 2013 e applicazioni client di Office 2016 in base alla configurazione di autenticazione nel tenant di Office 365 per Exchange Online, SharePoint Online e Skype Business online.
  
## <a name="availability-of-modern-authentication-for-office-365-services"></a>Disponibilità dell'autenticazione moderno per servizi di Office 365

Per i servizi di Office 365, lo stato predefinito di autenticazione moderno è:
  
- **Attivato per Exchange Online per impostazione predefinita.** Vedere [abilitare o disabilitare l'autenticazione moderno di Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) per attivarlo o attiva. 
    
- **Attivato per SharePoint Online per impostazione predefinita.** 
    
- **Attivato per Skype Business online per impostazione predefinita.** Vedere [Abilitare Skype Business online per l'autenticazione moderno ](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)alla sua attivazione o disattivazione.
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Comportamento di accesso delle applicazioni client di Office

Applicazioni client di Office 2013 supportano l'autenticazione legacy per impostazione predefinita. Legacy significa che supportano entrambi Sign-in di Microsoft Online Assistente o basic authentication. Affinché tali client di utilizzare le caratteristiche di autenticazione moderno, le finestre client ha dispongono di chiavi del Registro di sistema. Per istruzioni, vedere [Abilitare moderno Authentication for Office 2013 su dispositivi di Windows.](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910)
  
Informazioni su [come utilizzare moderno autenticazione (ADAL) con Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=785431) per informazioni su come utilizzarlo con Skype per le aziende. 
  
I client Office 2016 supportano l'autenticazione moderno per impostazione predefinita e nessuna azione necessaria per il client di utilizzare questi nuovi flussi. Azione esplicita, tuttavia, è necessario affinché utilizzino l'autenticazione legacy.
  
Fare clic sui collegamenti seguenti per vedere come funziona l'autenticazione del client Office 2013 e Office 2016 con i servizi di Office 365 a seconda se l'autenticazione moderno è attivata.
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [Skype for Business online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
### <a name="exchange-online"></a>Exchange Online

Nella tabella seguente viene descritto il comportamento di autenticazione per le applicazioni client di Office 2013 o 2016 Office quando si connettono a Exchange Online con o senza autenticazione moderno.
  
|Office client app versione * * *|Chiave del Registro di sistema attuale? * * *|Autenticazione moderno su? * * *|Comportamento di autenticazione con l'autenticazione moderno attivato per il tenant (impostazione predefinita) * * *|Comportamento di autenticazione con autenticazione moderno è disattivata per il tenant * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |No, o EnableADAL = 1  <br/> |Sì  <br/> |Innanzitutto viene tentata autenticazione moderno. Se il server rifiuta una connessione di autenticazione moderno, viene utilizzata l'autenticazione di base. Autenticazione moderno viene rifiutata dal server quando non è abilitato il tenant.  <br/> |Innanzitutto viene tentata autenticazione moderno. Se il server rifiuta una connessione di autenticazione moderno, viene utilizzata l'autenticazione di base. Autenticazione moderno viene rifiutata dal server quando non è abilitato il tenant.  <br/> |
|Office 2016  <br/> |Sì, EnableADAL = 1  <br/> |Sì  <br/> |Innanzitutto viene tentata autenticazione moderno. Se il server rifiuta una connessione di autenticazione moderno, viene utilizzata l'autenticazione di base. Autenticazione moderno viene rifiutata dal server quando non è abilitato il tenant.  <br/> |Innanzitutto viene tentata autenticazione moderno. Se il server rifiuta una connessione di autenticazione moderno, viene utilizzata l'autenticazione di base. Autenticazione moderno viene rifiutata dal server quando non è abilitato il tenant.  <br/> |
|Office 2016  <br/> |Sì, EnableADAL = 0  <br/> |No  <br/> |Autenticazione di base  <br/> |Autenticazione di base  <br/> |
|Office 2013  <br/> |No  <br/> |No  <br/> |Autenticazione di base  <br/> |Autenticazione di base  <br/> |
|Office 2013  <br/> |Sì, EnableADAL = 1  <br/> |Sì  <br/> |Innanzitutto viene tentata autenticazione moderno. Se il server rifiuta una connessione di autenticazione moderno, viene utilizzata l'autenticazione di base. Autenticazione moderno viene rifiutata dal server quando non è abilitato il tenant.  <br/> |Innanzitutto viene tentata autenticazione moderno. Se il server rifiuta una connessione di autenticazione moderno, viene utilizzata l'autenticazione di base. Autenticazione moderno viene rifiutata dal server quando non è abilitato il tenant.  <br/> |
   
### <a name="sharepoint-online"></a>SharePoint Online
<a name="BK_SharePointOnline"> </a>

Nella tabella seguente viene descritto il comportamento di autenticazione per le applicazioni client di Office 2013 o 2016 Office quando si connettono a SharePoint Online con o senza autenticazione moderno.
  
|Office client app versione * * *|Chiave del Registro di sistema attuale? * * *|Autenticazione moderno su? * * *|Comportamento di autenticazione con l'autenticazione moderno attivato per il tenant (impostazione predefinita) * * *|Comportamento di autenticazione con autenticazione moderno è disattivata per il tenant * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |No, o EnableADAL = 1  <br/> |Sì  <br/> |Autenticazione moderno.  <br/> |Impossibilità di connettersi.  <br/> |
|Office 2016  <br/> |Sì, EnableADAL = 1  <br/> |Sì  <br/> |Autenticazione moderno.  <br/> |Impossibilità di connettersi.  <br/> |
|Office 2016  <br/> |Sì, EnableADAL = 0  <br/> |No  <br/> |Microsoft Online Assistente per l'accesso solo.  <br/> |Microsoft Online Assistente per l'accesso solo.  <br/> |
|Office 2013  <br/> |No  <br/> |No  <br/> |Microsoft Online Assistente per l'accesso solo.  <br/> |Microsoft Online Assistente per l'accesso solo.  <br/> |
|Office 2013  <br/> |Sì, EnableADAL = 1  <br/> |Sì  <br/> |Autenticazione moderno.  <br/> |Impossibilità di connettersi.  <br/> |
   
### <a name="skype-for-business-online"></a>Skype for Business online
<a name="BK_SFBO"> </a>

Nella tabella seguente viene descritto il comportamento di autenticazione per Office 2013 o applicazioni client di Office 2016 quando si connettono a Skype Business online con o senza autenticazione moderno.
  
|Office client app versione * * *|Chiave del Registro di sistema attuale? * * *|Autenticazione moderno su? * * *|Comportamento di autenticazione con l'autenticazione moderno attivato per il tenant * * *|Comportamento di autenticazione con l'autenticazione moderno disattivato per il tenant (impostazione predefinita) * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |No, o EnableADAL = 1  <br/> |Sì  <br/> |Innanzitutto viene tentata autenticazione moderno. Se il server rifiuta una connessione di autenticazione moderno, viene utilizzato l'Assistente per l'accesso Microsoft Online. Autenticazione moderno viene rifiutata dal server quando Skype per tenant Business Online non sono abilitati.  <br/> |Innanzitutto viene tentata autenticazione moderno. Se il server rifiuta una connessione di autenticazione moderno, viene utilizzato l'Assistente per l'accesso Microsoft Online. Autenticazione moderno viene rifiutata dal server quando Skype per tenant Business Online non sono abilitati.  <br/> |
|Office 2016  <br/> |Sì, EnableADAL = 1  <br/> |Sì  <br/> |Innanzitutto viene tentata autenticazione moderno. Se il server rifiuta una connessione di autenticazione moderno, viene utilizzato l'Assistente per l'accesso Microsoft Online. Autenticazione moderno viene rifiutata dal server quando Skype per tenant Business Online non sono abilitati.  <br/> |Innanzitutto viene tentata autenticazione moderno. Se il server rifiuta una connessione di autenticazione moderno, viene utilizzato l'Assistente per l'accesso Microsoft Online. Autenticazione moderno viene rifiutata dal server quando Skype per tenant Business Online non sono abilitati.  <br/> |
|Office 2016  <br/> |Sì, EnableADAL = 0  <br/> |No  <br/> |Microsoft Online Assistente per l'accesso solo.  <br/> |Microsoft Online Assistente per l'accesso solo.  <br/> |
|Office 2013  <br/> |No  <br/> |No  <br/> |Microsoft Online Assistente per l'accesso solo.  <br/> |Microsoft Online Assistente per l'accesso solo.  <br/> |
|Office 2013  <br/> |Sì, EnableADAL = 1  <br/> |Sì  <br/> |Innanzitutto viene tentata autenticazione moderno. Se il server rifiuta una connessione di autenticazione moderno, viene utilizzato l'Assistente per l'accesso Microsoft Online. Autenticazione moderno viene rifiutata dal server quando Skype per tenant Business Online non sono abilitati.  <br/> |Microsoft Online Assistente per l'accesso solo.  <br/> |
   
## <a name="see-also"></a>Vedere anche

[Abilitare l'autenticazione moderna per Office 2013 nei dispositivi Windows](https://support.office.com/article/enable-modern-authentication-for-office-2013-on-windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910)

[Pianificare l'autenticazione a più fattori per le distribuzioni di Office 365 (per gli amministratori di Office 365)](https://support.office.com/article/plan-for-multi-factor-authentication-for-office-365-deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

[Accedere a Office 365 con verifica passaggio 2 (per gli utenti finali)](https://support.office.com/article/sign-in-to-office-365-with-2-step-verification-2b856342-170a-438e-9a4f-3c092394d3cb)