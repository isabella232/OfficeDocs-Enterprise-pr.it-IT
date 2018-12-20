---
title: Timeout sessione per Office 365
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
description: Timeout sessione vengono utilizzati per bilanciare protezione e semplicità di accesso in applicazioni client di Office 365.
ms.openlocfilehash: 4ef50b876fd97e2de2449d324464b466243a6691
ms.sourcegitcommit: fd7a56f38ba2c2d2e7fcd6e165ec58b31be299d9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2018
ms.locfileid: "27378492"
---
# <a name="session-timeouts-for-office-365"></a>Timeout sessione per Office 365

La durata della sessione è una parte importante di autenticazione per Office 365 e un aspetto importante di bilanciamento del carico di protezione e il numero di volte in cui gli utenti vengono richiesto per le proprie credenziali.
  
## <a name="session-times-for-office-365-services"></a>Tempi di sessione per servizi di Office 365

Quando gli utenti autenticati in le applicazioni web di Office 365 o App per dispositivi mobili, viene stabilita una sessione. Per la durata della sessione, gli utenti non devono eseguire nuovamente l'autenticazione. Sessioni possono scadere quando gli utenti sono inattivi, quando si chiude il browser o scheda o scadenza i token di autenticazione per altri motivi, ad esempio quando è stata ripristinata la propria password. I servizi di Office 365 sono i timeout di sessione diverse in modo che corrispondano con l'utilizzo tipico di ogni servizio.
  
Nella tabella seguente sono elencati la durata della sessione di servizi di Office 365:
  
|**Servizio Office 365**|**Timeout sessione**|
|:-----|:-----|
|Interfaccia di amministrazione di Office 365  <br/> |Viene chiesto di specificare le credenziali per l'interfaccia di amministrazione ogni 8 ore.  <br/> |
|SharePoint Online  <br/> |5 giorni di inattività fino a quando gli utenti sceglie **Mantieni connesso**. Se l'utente accede a SharePoint Online nuovamente dopo che sono trascorsi più di 24 ore dalla precedente sign-in, il valore di timeout viene reimpostato su 5 giorni.<br/> |
|Outlook Web App  <br/> |6 ore.  <br/> È possibile modificare questo valore utilizzando il parametro _ActivityBasedAuthenticationTimeoutInterval_ nel cmdlet [Set-OrganizationConfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) .  <br/> |
|Azure Active Directory  <br/> (Utilizzato dai client Office 2013 Windows con attivata l'autenticazione moderno)  <br/> | Autenticazione moderno utilizza i token di accesso e l'aggiornamento dei token per concedere l'accesso degli utenti alle risorse di Office 365 con Azure Active Directory. Un token di accesso è JSON Web Token fornito dopo che l'autenticazione ha esito positivo ed è valido per 1 ora. È inoltre disponibile un aggiornamento di token con una durata. Quando scade, token di accesso client di Office usare un token di aggiornamento valido per ottenere un nuovo token di accesso. Questo exchange ha esito positivo se è ancora valida autenticazione iniziale dell'utente.  <br/>  Aggiornamento dei token sono validi per 90 giorni e con un utilizzo continuo, può essere valide fino a quando non revocato.  <br/>  Aggiornare i token possono essere invalidati da diversi eventi, ad esempio:  <br/>  Password dell'utente è stato modificato dopo il token di aggiornamento è stato rilasciato.  <br/>  Un amministratore può applicare criteri di accesso condizionale che limitano l'accesso alla risorsa che l'utente sta cercando di accedere.  <br/> |
|App per dispositivi mobili SharePoint e OneDrive per Android, iOS e Windows 10  <br/> |La durata predefinita dei token di accesso è 1 ora. Il tempo di inattività massimo predefinito del token di aggiornamento è 90 giorni.<br/> [Ulteriori informazioni su come configurare le durate dei token e token](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> Per revocare l'aggiornamento dei token, è possibile reimpostare la password dell'utente Office 365  <br/> |
|Yammer con accesso di Office 365  <br/> |Durata del browser. Se gli utenti chiudere il browser e accedere Yammer in un nuovo browser, Yammer verranno nuovamente autenticati li con Office 365. Se gli utenti utilizzano browser di terze parti che i cookie di cache, potrebbe non necessario eseguire nuovamente l'autenticazione quando si riaprire il browser.<br/> > [!NOTE]> Ciò è valido solo per le reti utilizzando Sign-In Office 365 per Yammer.           |
   

