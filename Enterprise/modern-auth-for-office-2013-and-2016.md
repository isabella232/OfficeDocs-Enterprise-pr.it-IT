---
title: Funzionamento dell'autenticazione moderna per le applicazioni client di Office 2013 e Office 2016
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/1/2017
audience: Admin
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
ms.collection:
- M365-security-compliance
description: Informazioni su come l'autenticazione moderna di Office 365 funziona in modo diverso per le app client di Office 2013 e 2016.
ms.openlocfilehash: 25646c014fc9ff11926c0091209a3419fad811d6
ms.sourcegitcommit: b4c82c0bf61f50386e534ad23479b5cf84f4e2ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2019
ms.locfileid: "35203625"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>Funzionamento dell'autenticazione moderna per le applicazioni client di Office 2013 e Office 2016

Leggere questo articolo per informazioni su come le app client di Office 2013 e Office 2016 utilizzano le funzionalità di autenticazione moderne in base alla configurazione dell'autenticazione nel tenant di Office 365 per Exchange Online, SharePoint Online e Skype for business online.

> [!NOTE]
> Le app client legacy, come Office 2010 e Office per Mac 2011, non supportano l'autenticazione moderna e possono essere utilizzate solo con l'autenticazione di base.

## <a name="availability-of-modern-authentication-for-office-365-services"></a>Disponibilità dell'autenticazione moderna per i servizi di Office 365

Per i servizi di Office 365, lo stato predefinito dell'autenticazione moderna è il seguente:
  
- Attivata **** per Exchange Online per impostazione predefinita. Vedere [abilitare o disabilitare l'autenticazione moderna in Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) per disattivarla. 
    
- Attivata **** per SharePoint Online per impostazione predefinita. 
    
- Attivata **** per Skype for business online per impostazione predefinita. Vedere [abilitare Skype for business online per l'autenticazione moderna ](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)per disattivarla o attivarla.
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Comportamento di accesso delle app client di Office

Le app client di Office 2013 supportano l'autenticazione legacy per impostazione predefinita. Legacy significa che supportano l'assistente per l'accesso di Microsoft online o l'autenticazione di base. Affinché questi client utilizzino le funzionalità di autenticazione moderne, il client Windows dispone delle chiavi del registro di sistema impostate. Per istruzioni, vedere [abilitare l'autenticazione moderna per Office 2013 nei dispositivi Windows](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).
  
Leggere [come usare l'autenticazione moderna (adal) con Skype for business](https://go.microsoft.com/fwlink/p/?LinkId=785431) per informazioni su come funziona con Skype for business. 
  
I client di Office 2016 supportano l'autenticazione moderna per impostazione predefinita e non è necessaria alcuna azione per il client per l'utilizzo di questi nuovi flussi. Tuttavia, è necessaria un'azione esplicita per l'utilizzo dell'autenticazione legacy.
  
Fare clic sui collegamenti riportati di seguito per vedere come funziona l'autenticazione client di Office 2013 e Office 2016 con i servizi di Office 365 a seconda che l'autenticazione moderna sia attivata o meno.
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [Skype for Business online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

Nella tabella seguente viene descritto il comportamento di autenticazione per le app client di Office 2013 o Office 2016 quando si connettono a Exchange Online con o senza l'autenticazione moderna.
  
|Versione app client di Office * * * *|Chiave del registro di sistema presente? * * * *|Autenticazione moderna in? * * * *|Comportamento di autenticazione con autenticazione moderna attivata per il tenant (impostazione predefinita) * * * *|Comportamento di autenticazione con l'autenticazione moderna disattivata per il tenant * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |No, o EnableADAL = 1  <br/> |Sì  <br/> |L'autenticazione moderna viene tentata per prima. Se il server rifiuta una connessione di autenticazione moderna, viene utilizzata l'autenticazione di base. Il server rifiuta l'autenticazione moderna quando il tenant non è abilitato.  <br/> |L'autenticazione moderna viene tentata per prima. Se il server rifiuta una connessione di autenticazione moderna, viene utilizzata l'autenticazione di base. Il server rifiuta l'autenticazione moderna quando il tenant non è abilitato.  <br/> |
|Office 2016  <br/> |Sì, EnableADAL = 1  <br/> |Sì  <br/> |L'autenticazione moderna viene tentata per prima. Se il server rifiuta una connessione di autenticazione moderna, viene utilizzata l'autenticazione di base. Il server rifiuta l'autenticazione moderna quando il tenant non è abilitato.  <br/> |L'autenticazione moderna viene tentata per prima. Se il server rifiuta una connessione di autenticazione moderna, viene utilizzata l'autenticazione di base. Il server rifiuta l'autenticazione moderna quando il tenant non è abilitato.  <br/> |
|Office 2016  <br/> |Sì, EnableADAL = 0  <br/> |No  <br/> |Autenticazione di base  <br/> |Autenticazione di base  <br/> |
|Office 2013  <br/> |No  <br/> |No  <br/> |Autenticazione di base  <br/> |Autenticazione di base  <br/> |
|Office 2013  <br/> |Sì, EnableADAL = 1  <br/> |Sì  <br/> |L'autenticazione moderna viene tentata per prima. Se il server rifiuta una connessione di autenticazione moderna, viene utilizzata l'autenticazione di base. Il server rifiuta l'autenticazione moderna quando il tenant non è abilitato.  <br/> |L'autenticazione moderna viene tentata per prima. Se il server rifiuta una connessione di autenticazione moderna, viene utilizzata l'autenticazione di base. Il server rifiuta l'autenticazione moderna quando il tenant non è abilitato.  <br/> |
   
<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

Nella tabella seguente viene descritto il comportamento di autenticazione per le app client di Office 2013 o Office 2016 quando si connettono a SharePoint Online con o senza l'autenticazione moderna.
  
|Versione app client di Office * * * *|Chiave del registro di sistema presente? * * * *|Autenticazione moderna in? * * * *|Comportamento di autenticazione con autenticazione moderna attivata per il tenant (impostazione predefinita) * * * *|Comportamento di autenticazione con l'autenticazione moderna disattivata per il tenant * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |No, o EnableADAL = 1  <br/> |Sì  <br/> |Solo autenticazione moderna.  <br/> |Errore di connessione.  <br/> |
|Office 2016  <br/> |Sì, EnableADAL = 1  <br/> |Sì  <br/> |Solo autenticazione moderna.  <br/> |Errore di connessione.  <br/> |
|Office 2016  <br/> |Sì, EnableADAL = 0  <br/> |No  <br/> |Solo assistente per l'accesso di Microsoft online.  <br/> |Solo assistente per l'accesso di Microsoft online.  <br/> |
|Office 2013  <br/> |No  <br/> |No  <br/> |Solo assistente per l'accesso di Microsoft online.  <br/> |Solo assistente per l'accesso di Microsoft online.  <br/> |
|Office 2013  <br/> |Sì, EnableADAL = 1  <br/> |Sì  <br/> |Solo autenticazione moderna.  <br/> |Errore di connessione.  <br/> |
   
### <a name="skype-for-business-online"></a>Skype for Business online
<a name="BK_SFBO"> </a>

Nella tabella seguente viene descritto il comportamento di autenticazione per le app client di Office 2013 o Office 2016 quando si connettono a Skype for business online con o senza l'autenticazione moderna.
  
|Versione app client di Office * * * *|Chiave del registro di sistema presente? * * * *|Autenticazione moderna in? * * * *|Comportamento di autenticazione con autenticazione moderna attivata per il tenant * * * *|Comportamento di autenticazione con l'autenticazione moderna disattivata per il tenant (impostazione predefinita) * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |No, o EnableADAL = 1  <br/> |Sì  <br/> |L'autenticazione moderna viene tentata per prima. Se il server rifiuta una connessione di autenticazione moderna, viene utilizzato l'assistente per l'accesso di Microsoft online. Server rifiuta l'autenticazione moderna quando i tenant di Skype for business online non sono abilitati.  <br/> |L'autenticazione moderna viene tentata per prima. Se il server rifiuta una connessione di autenticazione moderna, viene utilizzato l'assistente per l'accesso di Microsoft online. Server rifiuta l'autenticazione moderna quando i tenant di Skype for business online non sono abilitati.  <br/> |
|Office 2016  <br/> |Sì, EnableADAL = 1  <br/> |Sì  <br/> |L'autenticazione moderna viene tentata per prima. Se il server rifiuta una connessione di autenticazione moderna, viene utilizzato l'assistente per l'accesso di Microsoft online. Server rifiuta l'autenticazione moderna quando i tenant di Skype for business online non sono abilitati.  <br/> |L'autenticazione moderna viene tentata per prima. Se il server rifiuta una connessione di autenticazione moderna, viene utilizzato l'assistente per l'accesso di Microsoft online. Server rifiuta l'autenticazione moderna quando i tenant di Skype for business online non sono abilitati.  <br/> |
|Office 2016  <br/> |Sì, EnableADAL = 0  <br/> |No  <br/> |Solo assistente per l'accesso di Microsoft online.  <br/> |Solo assistente per l'accesso di Microsoft online.  <br/> |
|Office 2013  <br/> |No  <br/> |No  <br/> |Solo assistente per l'accesso di Microsoft online.  <br/> |Solo assistente per l'accesso di Microsoft online.  <br/> |
|Office 2013  <br/> |Sì, EnableADAL = 1  <br/> |Sì  <br/> |L'autenticazione moderna viene tentata per prima. Se il server rifiuta una connessione di autenticazione moderna, viene utilizzato l'assistente per l'accesso di Microsoft online. Server rifiuta l'autenticazione moderna quando i tenant di Skype for business online non sono abilitati.  <br/> |Solo assistente per l'accesso di Microsoft online.  <br/> |
   
## <a name="see-also"></a>Vedere anche

[Abilitare l'autenticazione moderna per Office 2013 nei dispositivi Windows](https://support.office.com/article/enable-modern-authentication-for-office-2013-on-windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910)

[Pianificare l'autenticazione a più fattori per le distribuzioni di Office 365 (per gli amministratori di Office 365)](https://support.office.com/article/plan-for-multi-factor-authentication-for-office-365-deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

[Accedere a Office 365 con verifica in due passaggi (per gli utenti finali)](https://support.office.com/article/sign-in-to-office-365-with-2-step-verification-2b856342-170a-438e-9a4f-3c092394d3cb)
