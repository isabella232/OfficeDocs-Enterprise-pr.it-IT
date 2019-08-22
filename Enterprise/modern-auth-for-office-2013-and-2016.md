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
description: Informazioni sulle differenze di funzionamento dell'autenticazione moderna di Office 365 nelle applicazioni client di Office 2013 e 2016.
ms.openlocfilehash: 17a6713fe12e7cdb1fe0355dd38b44b4cb93be54
ms.sourcegitcommit: 756f1713cab2e46be948f91f6dd87fd60197c4a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2019
ms.locfileid: "36491295"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>Funzionamento dell'autenticazione moderna per le applicazioni client di Office 2013 e Office 2016

Leggere questo articolo per informazioni sul modo in cui le app client di Office 2013 e Office 2016 usano le caratteristiche di autenticazione moderna basate sulla configurazione dell'autenticazione nel tenant di Office 365 per Exchange Online, SharePoint Online e Skype for business online.

> [!NOTE]
> Le app client legacy, come Office 2010 e Microsoft Office per Mac 2011, non supportano l'autenticazione moderna e possono essere usate solo con l'autenticazione di base.

## <a name="availability-of-modern-authentication-for-office-365-services"></a>Disponibilità dell'autenticazione moderna per servizi di Office 365.

Per i servizi di Office 365, lo stato predefinito di autenticazione moderna è:
  
- **Attivata** per Exchange Online per impostazione predefinita. Vedere [Abilitare o disabilitare l’autenticazione moderna in Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) per attivarla o disattivarla. 
    
- **Attivata** per SharePoint Online per impostazione predefinita. 
    
- **Attivata** per Skype for Business Online per impostazione predefinita. Per disattivarla o attivarla, vedere [Abilitare Skype for Business Online per l'autenticazione moderna](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).

> [!NOTE]
> Per i tenant creati **prima** del 1° agosto 2017, l'autenticazione moderna è **disattivata** per impostazione predefinita per Exchange Online e Skype for Business Online.
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Comportamento di accesso delle app client di Office

Per impostazione predefinita, le app client di Office 2013 supportano l'autenticazione legacy. cioè supportano l'Assistente per l'accesso ai Microsoft Online Services oppure l'autenticazione di base. Per usare le funzionalità di autenticazione moderna in questi client, è necessario aver impostato le chiavi del Registro di sistema per il client Windows. Per istruzioni, vedere [Abilitare l'autenticazione moderna per Office 2013 nei dispositivi Windows](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).
  
Leggere [come usare l'autenticazione moderna (ADAL) con Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=785431) per comprenderne il funzionamento. 
  
I client di Office 2016 supportano l'autenticazione moderna per impostazione predefinita e non è necessaria alcuna azione per usare questi nuovi flussi. È tuttavia necessaria un'azione esplicita per usare l'autenticazione legacy.
  
Fare clic sui collegamenti riportati di seguito per vedere come funziona l'autenticazione del client di Office 2013 e Office 2016 con i servizi di Office 365, a seconda che l'autenticazione moderna sia attivata o no.
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [Skype for Business online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

La tabella seguente descrive il comportamento di autenticazione per le app client Office 2013 o Office 2016 quando si connettono a Exchange Online con o senza l'autenticazione moderna.
  
|****Versione dell'app client di Office****|****Chiave del Registro di sistema presente?****|****Autenticazione moderna attivata?****|****Comportamento di autenticazione con l'autenticazione moderna attivata per il tenant (impostazione predefinita)****|****Comportamento di autenticazione con l'autenticazione moderna disattivata per il tenant****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |No, o EnableADAL = 1  <br/> |Sì  <br/> |Prima di tutto viene tentata l'autenticazione moderna. Se il server rifiuta una connessione di autenticazione moderna, viene usata l'autenticazione di base. Il server rifiuta l'autenticazione moderna quando il tenant non è abilitato.  <br/> |Prima di tutto viene tentata l'autenticazione moderna. Se il server rifiuta una connessione di autenticazione moderna, viene usata l'autenticazione di base. Il server rifiuta l'autenticazione moderna quando il tenant non è abilitato.  <br/> |
|Office 2016  <br/> |Sì, o EnableADAL = 1  <br/> |Sì  <br/> |Prima di tutto viene tentata l'autenticazione moderna. Se il server rifiuta una connessione di autenticazione moderna, viene usata l'autenticazione di base. Il server rifiuta l'autenticazione moderna quando il tenant non è abilitato.  <br/> |Prima di tutto viene tentata l'autenticazione moderna. Se il server rifiuta una connessione di autenticazione moderna, viene usata l'autenticazione di base. Il server rifiuta l'autenticazione moderna quando il tenant non è abilitato.  <br/> |
|Office 2016  <br/> |Sì, EnableADAL=0  <br/> |No  <br/> |Autenticazione di base  <br/> |Autenticazione di base  <br/> |
|Impostazioni account nella visualizzazione Backstage  <br/> |No  <br/> |No  <br/> |Autenticazione di base  <br/> |Autenticazione di base  <br/> |
|Impostazioni account nella visualizzazione Backstage  <br/> |Sì, o EnableADAL = 1  <br/> |Sì  <br/> |Prima di tutto viene tentata l'autenticazione moderna. Se il server rifiuta una connessione di autenticazione moderna, viene usata l'autenticazione di base. Il server rifiuta l'autenticazione moderna quando il tenant non è abilitato.  <br/> |Prima di tutto viene tentata l'autenticazione moderna. Se il server rifiuta una connessione di autenticazione moderna, viene usata l'autenticazione di base. Il server rifiuta l'autenticazione moderna quando il tenant non è abilitato.  <br/> |
   
<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

La tabella seguente descrive il comportamento di autenticazione per le app client Office 2013 o Office 2016 quando si connettono a SharePoint Online con o senza l'autenticazione moderna.
  
|****Versione dell'app client di Office****|****Chiave del Registro di sistema presente?****|****Autenticazione moderna attivata?****|****Comportamento di autenticazione con l'autenticazione moderna attivata per il tenant (impostazione predefinita)****|****Comportamento di autenticazione con l'autenticazione moderna disattivata per il tenant****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |No, o EnableADAL = 1  <br/> |Sì  <br/> |Solo autenticazione moderna.  <br/> |Errore durante la connessione.  <br/> |
|Office 2016  <br/> |Sì, o EnableADAL = 1  <br/> |Sì  <br/> |Solo autenticazione moderna.  <br/> |Errore durante la connessione.  <br/> |
|Office 2016  <br/> |Sì, o EnableADAL = 0  <br/> |No  <br/> |Solo Assistente per l'accesso ai Microsoft Online Services.  <br/> |Solo Assistente per l'accesso ai Microsoft Online Services.  <br/> |
|Impostazioni account nella visualizzazione Backstage  <br/> |No  <br/> |No  <br/> |Solo Assistente per l'accesso ai Microsoft Online Services.  <br/> |Solo Assistente per l'accesso ai Microsoft Online Services.  <br/> |
|Impostazioni account nella visualizzazione Backstage  <br/> |Sì, o EnableADAL = 1  <br/> |Sì  <br/> |Solo autenticazione moderna.  <br/> |Errore durante la connessione.  <br/> |
   
### <a name="skype-for-business-online"></a>Skype for Business online
<a name="BK_SFBO"> </a>

La tabella seguente descrive il comportamento di autenticazione per le app client Office 2013 o Office 2016 quando si connettono a Skype for Business Online con o senza l'autenticazione moderna.
  
|****Versione dell'app client di Office****|****Chiave del Registro di sistema presente?****|****Autenticazione moderna attivata?****|****Comportamento di autenticazione con l'autenticazione moderna attivata per il tenant****|****Comportamento di autenticazione con l'autenticazione moderna disattivata per il tenant (impostazione predefinita)****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |No, o EnableADAL = 1  <br/> |Sì  <br/> |Prima di tutto viene tentata l'autenticazione moderna. Se il server rifiuta una connessione di autenticazione moderna, viene usato l'Assistente per l'accesso ai Microsoft Online Services. Il server rifiuta l'autenticazione moderna quando i tenant di Skype for Business online non sono abilitati.  <br/> |Prima di tutto viene tentata l'autenticazione moderna. Se il server rifiuta una connessione di autenticazione moderna, viene usato l'Assistente per l'accesso ai Microsoft Online Services. Il server rifiuta l'autenticazione moderna quando i tenant di Skype for Business online non sono abilitati.  <br/> |
|Office 2016  <br/> |Sì, o EnableADAL = 1  <br/> |Sì  <br/> |Prima di tutto viene tentata l'autenticazione moderna. Se il server rifiuta una connessione di autenticazione moderna, viene usato l'Assistente per l'accesso ai Microsoft Online Services. Il server rifiuta l'autenticazione moderna quando i tenant di Skype for Business online non sono abilitati.  <br/> |Prima di tutto viene tentata l'autenticazione moderna. Se il server rifiuta una connessione di autenticazione moderna, viene usato l'Assistente per l'accesso ai Microsoft Online Services. Il server rifiuta l'autenticazione moderna quando i tenant di Skype for Business online non sono abilitati.  <br/> |
|Office 2016  <br/> |Sì, o EnableADAL = 0  <br/> |No  <br/> |Solo Assistente per l'accesso ai Microsoft Online Services.  <br/> |Solo Assistente per l'accesso ai Microsoft Online Services.  <br/> |
|Impostazioni account nella visualizzazione Backstage  <br/> |No  <br/> |No  <br/> |Solo Assistente per l'accesso ai Microsoft Online Services.  <br/> |Solo Assistente per l'accesso ai Microsoft Online Services.  <br/> |
|Impostazioni account nella visualizzazione Backstage  <br/> |Sì, o EnableADAL = 1  <br/> |Sì  <br/> |Prima di tutto viene tentata l'autenticazione moderna. Se il server rifiuta una connessione di autenticazione moderna, viene usato l'Assistente per l'accesso ai Microsoft Online Services. Il server rifiuta l'autenticazione moderna quando i tenant di Skype for Business online non sono abilitati.  <br/> |Solo Assistente per l'accesso ai Microsoft Online Services.  <br/> |
   
## <a name="see-also"></a>Vedere anche

[Abilitare l'autenticazione moderna per Office 2013 nei dispositivi Windows](https://support.office.com/article/enable-modern-authentication-for-office-2013-on-windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910)

[Pianificare l'autenticazione a più fattori per le distribuzioni di Office 365 (per amministratori di Office 365)](https://support.office.com/article/plan-for-multi-factor-authentication-for-office-365-deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

[Accedere a Office 365 con la verifica in due passaggi (per gli utenti finali)](https://support.office.com/article/sign-in-to-office-365-with-2-step-verification-2b856342-170a-438e-9a4f-3c092394d3cb)
