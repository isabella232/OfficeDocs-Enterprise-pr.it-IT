---
title: Pianificare i certificati SSL di terze parti per Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 10/24/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 'Riepilogo: in questo articolo vengono descritti i certificati SSL necessari per Exchange locale e ibrido, SSO tramite ADFS, i servizi Exchange Online e i servizi Web Exchange.'
ms.openlocfilehash: 3c22daa2315e36c45b5b5dd6271842168c90726d
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491412"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a>Pianificare i certificati SSL di terze parti per Office 365

 **Riepilogo:** Vengono descritti i certificati SSL necessari per Exchange locale e ibrido, SSO tramite ADFS, servizi Exchange Online e servizi Web Exchange. 
  
Per crittografare le comunicazioni tra i client e l'ambiente Office 365, è necessario che i certificati SSL (Secure Socket Layer) di terze parti siano installati nei server dell'infrastruttura.

||
|:-----|
| Questo articolo fa parte della [pianificazione della rete e dell'ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune).|
   
I certificati sono necessari per i componenti di Office 365 seguenti:
  
- Exchange in locale
    
- Single Sign-on (SSO) (per i server federativi Active Directory Federation Services (AD FS) e per i proxy server federativi ADFS)
    
- Servizi di Exchange Online, ad esempio individuazione automatica, Outlook via Internet e servizi Web Exchange
    
- Server ibrido Exchange
    
## <a name="certificates-for-exchange-on-premises"></a>Certificati per Exchange in locale

Per una panoramica sull'utilizzo dei certificati digitali per rendere la comunicazione tra l'organizzazione di Exchange locale ed Exchange Online Secure, vedere l'articolo di TechNet [informazioni sui requisiti dei certificati](https://go.microsoft.com/fwlink/p/?LinkID=243657).
  
## <a name="certificates-for-single-sign-on"></a>Certificati per Single Sign-on

Per fornire agli utenti un'esperienza di Single Sign-on semplificata che includa una sicurezza robusta, i certificati riportati nella tabella seguente sono necessari nei server federativi o nei proxy server federativi. La tabella seguente si concentra su Active Directory Federation Services (AD FS), inoltre sono presenti ulteriori informazioni sull' [utilizzo di provider di identità di terze parti](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility).
  
||||
|:-----|:-----|:-----|
|**Tipo di certificato** <br/> |**Descrizione** <br/> |**Cosa è necessario sapere prima di distribuire** <br/> |
|**Certificato SSL (denominato anche certificato di autenticazione server)** <br/> |Si tratta di un certificato SSL standard utilizzato per rendere sicure le comunicazioni tra i server federativi, i client e i computer proxy server federativi.  <br/> |AD FS è necessario un certificato SSL. Per impostazione predefinita, AD FS utilizza il certificato SSL configurato per il sito Web predefinito in Internet Information Services (IIS).  <br/> Il nome del soggetto del certificato SSL viene utilizzato per determinare il nome del servizio federativo (FS) per ogni istanza di AD FS che viene distribuita. Valutare la possibilità di scegliere un nome del soggetto per qualsiasi nuova autorità di certificazione (CA): i certificati emessi che rappresentano al meglio il nome della società o dell'organizzazione in Office 365. Questo nome deve essere instradabile su Internet.  <br/>**Attenzione:** AD FS è necessario che il certificato SSL non disponga del nome del soggetto punto (short-name).          <br/> **Raccomandazione:** Poiché questo certificato deve essere considerato attendibile dai client di AD FS, è consigliabile utilizzare un certificato SSL emesso da un'autorità di certificazione pubblica (di terze parti) o da un'autorità di certificazione subordinata a una radice pubblicamente attendibile. ad esempio, VeriSign o Thawte.  <br/> |
|**Certificato per la firma di token** <br/> |Si tratta di un certificato X. 509 standard utilizzato per la firma sicura di tutti i token che il server federativo rilascia e che Office 365 accetta e convalida.  <br/> |Il certificato per la firma di token deve contenere una chiave privata che viene concatenata a una radice attendibile nel FS. Per impostazione predefinita, AD FS crea un certificato autofirmato. Tuttavia, a seconda delle esigenze dell'organizzazione, è possibile modificare questo certificato in un certificato emesso da una CA utilizzando lo snap-in di gestione AD FS.  <br/>**Attenzione:** Il certificato per la firma di token è fondamentale per la stabilità del FS. Se il certificato viene cambiato, Office 365 deve ricevere notifica di tale cambiamento. Se la notifica non viene fornita, gli utenti non potranno accedere alle offerte di servizi di Office 365.<br/>**Raccomandazione:** È consigliabile utilizzare il certificato per la firma di token autofirmato generato da AD FS. In questo modo, il certificato viene gestito automaticamente per l'utente. Ad esempio, quando il certificato sta per scadere, AD FS genererà un nuovo certificato autofirmato.  <br/> |
   
I proxy server federativi richiedono il certificato descritto nella tabella seguente.
  
||||
|:-----|:-----|:-----|
|**Tipo di certificato** <br/> |**Descrizione** <br/> |**Cosa è necessario sapere prima di distribuire** <br/> |
|Certificato SSL  <br/> |Si tratta di un certificato SSL standard che viene utilizzato per proteggere le comunicazioni tra un server federativo, un proxy server federativo e i computer client Internet.  <br/> |Questo certificato SSL deve essere associato al sito Web predefinito in IIS prima di poter eseguire correttamente la configurazione guidata del proxy server federativo di ADFS.  <br/> Questo certificato deve avere lo stesso nome del soggetto del certificato SSL configurato sul server federativo nella rete aziendale.  <br/> **Raccomandazione:** È consigliabile utilizzare lo stesso certificato di autenticazione del server configurato nel server federativo a cui si connette il proxy server federativo.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>Certificati per l'individuazione automatica, Outlook via Internet e sincronizzazione di Active Directory

I server Accesso client di Exchange 2013, Exchange 2010, Exchange 2007 ed Exchange 2003 (CASs) devono avere un certificato SSL di terze parti per le connessioni sicure per l'individuazione automatica, Outlook via Internet e servizi di sincronizzazione di Active Directory. È possibile che tale certificato sia già installato nell'ambiente locale.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Certificato per un server ibrido di Exchange

Il server o i server ibridi di Exchange con accesso esterno richiedono un certificato SSL di terze parti per garantire la connettività sicura con il servizio Exchange Online. È necessario ottenere questo certificato dal provider di terze parti SSL.
  
## <a name="office-365-certificate-chains"></a>Catene di certificati di Office 365

In questo articolo vengono illustrati i certificati che potrebbe essere necessario installare nell'infrastruttura. Per ulteriori informazioni sui certificati installati nei server di Office 365, vedere [catene di certificati di office 365](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).
  

