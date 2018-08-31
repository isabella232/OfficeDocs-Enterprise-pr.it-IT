---
title: Pianificazione dei certificati SSL di terze parti per Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 10/24/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: "Riepilogo: vengono descritti i certificati SSL necessari per distribuzioni locali e ibride di Exchange, l'accesso SSO tramite ADFS, servizi di Exchange Online e Servizi Web Exchange."
ms.openlocfilehash: 5092734c66f39583d32d4cd9f926e76ed794668b
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223018"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a>Pianificazione dei certificati SSL di terze parti per Office 365

 **Riepilogo:** Vengono descritti i certificati SSL necessari per Exchange in locale e ibrido, SSO tramite ADFS, servizi Exchange Online e servizi Web Exchange. 
  
Per crittografare le comunicazioni tra i client e Office 365Office 365 ambiente, è necessario installare i certificati di terze parti Secure Socket Layer (SSL) sui server dell'infrastruttura.

||
|:-----|
| In questo articolo fa parte della [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune).|
   
I certificati sono necessari per i componenti di Office 365 seguenti:
  
- Exchange in locale
    
- Single sign-on (SSO) (per i server federativi di AD FS (Active Directory Federation Services) e per i server proxy federativi di AD FS)
    
- Servizi Exchange Online, ad esempio individuazione automatica, Outlook via Internet e servizi Web Exchange
    
- Server ibrido Exchange
    
## <a name="certificates-for-exchange-on-premises"></a>Certificati per Exchange in locale

Per una panoramica sull'utilizzo dei certificati digitali per rendere sicure le comunicazioni tra l'organizzazione Exchange locale ed Exchange Online, vedere l'articolo TechNet [Informazioni sui requisiti dei certificati](https://go.microsoft.com/fwlink/p/?LinkID=243657).
  
## <a name="certificates-for-single-sign-on"></a>Certificati per Single Sign-On

Per fornire agli utenti di single sign-on funzionalità semplificate che include l'infrastruttura di protezione, i certificati illustrati nella tabella seguente sono necessari nei server federativi o i server federativi. Nella tabella seguente è incentrata su Active Directory Federation Services (ADFS), è necessario anche ulteriori informazioni [sull'utilizzo di provider di identità di terze parti](https://go.microsoft.com/fwlink/?LinkId=532869).
  
||||
|:-----|:-----|:-----|
|**Tipo di certificato** <br/> |**Descrizione** <br/> |**Cos'è necessario sapere prima dell'implementazione** <br/> |
|**Certificato SSL (denominato anche certificato di autenticazione server)** <br/> |È un certificato SSL standard utilizzato per rendere sicure le comunicazioni tra computer server federativi, client e server proxy federativi.  <br/> |AD FS richiede un certificato SSL. Per impostazione predefinita, ADFS utilizza il certificato SSL configurato per il sito Web predefinito in Internet Information Services (IIS).<br/> Il nome soggetto del certificato SSL viene utilizzato per determinare il nome del servizio federativo (ADFS) per ogni istanza di ADFS distribuito. È consigliabile scegliere un nome soggetto per qualsiasi nuova autorità di certificazione (CA)-rilasciato certificati che meglio rappresenta il nome della società o organizzazione a Office 365. Questo nome deve essere instradabili su Internet.<br/>**Attenzione:** AD FS richiede che il certificato SSL disponibile alcun nome del soggetto senza punto (nome breve).          </br> **Suggerimento:** Dal momento che questo certificato deve essere considerato attendibile dal client di AD FS, è consigliabile utilizzare un certificato SSL rilasciato da una CA pubblica (di terze parti) o da una CA subordinata a pubblicamente attendibile; ad esempio, Thawte o VeriSign.  <br/> |
|**Certificato per la firma di token** <br/> |Si tratta di un certificato x. 509 standard utilizzato per firmare in modo sicuro tutti i token emessi dal server federativo e da Office 365 accettati e convalidati.  <br/> |Il certificato di firma di token deve contenere una chiave privata che collega a un'autorità attendibile nell'ADFS. Per impostazione predefinita, ADFS consente di creare un certificato autofirmato. Tuttavia, in base alle esigenze della propria organizzazione, è possibile modificare questo certificato a un certificato rilasciato dalla CA utilizzando lo snap-in Gestione ADFS.<br/>**Attenzione:** Il certificato di firma di token è importante per la stabilità di ADFS. Se viene modificato il certificato, Office 365 deve ricevere una notifica della modifica. Se la notifica non viene specificata, gli utenti possono accedere per le offerte di servizi di Office 365.</br>**Suggerimento:** È consigliabile utilizzare il certificato di firma di token autofirmato generata da ADFS. In questo modo, gestisce il certificato è per impostazione predefinita. Ad esempio, quando questo certificato sta per scadere, ADFS verrà generato un nuovo certificato autofirmato.<br/> |
   
I server proxy federativi richiedono il certificato descritto nella seguente tabella.
  
||||
|:-----|:-----|:-----|
|**Tipo di certificato** <br/> |**Descrizione** <br/> |**Cos'è necessario sapere prima dell'implementazione** <br/> |
|Certificato SSL  <br/> |È un certificato SSL standard utilizzato per rendere sicure le comunicazioni tra un server federativo, un server proxy federativo e i computer client di Internet.  <br/> |Questo certificato SSL deve essere associato a sito Web predefinito in IIS per poter eseguire correttamente la procedura guidata di configurazione del Proxy Server federativo ADFS Active Directory.  <br/> Il certificato deve avere lo stesso nome del soggetto del certificato SSL configurato sul server federativo nella rete dell'azienda.  <br/> **Suggerimento:** si consiglia di utilizzare lo stesso certificato di autenticazione del server configurato nel server federativo a cui è connesso questo server proxy federativo.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>Certificati per individuazione automatica, Outlook via Internet e sincronizzazione di Active Directory

Con accesso esterno Exchange 2013, Exchange 2010, Exchange 2007, Exchange 2003 Client Access Server e (classi) richiedono un certificato SSL di terze parti per le connessioni sicure per servizi di sincronizzazione di individuazione automatica, Outlook via Internet e Active Directory. Potrebbe già essere certificato installato nell'ambiente locale.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Certificato per un server ibrido Exchange

Il server ibrido Exchange con accesso esterno o server richiedono un certificato SSL di terze parti per la connettività protetta con il servizio Exchange Online. È necessario ottenere il certificato dal provider SSL di terze parti.
  
## <a name="office-365-certificate-chains"></a>Catena di certificati di Office 365

In questo articolo vengono descritti i certificati che potrebbe essere necessario installare l'infrastruttura. Per ulteriori informazioni sui certificati installati nel server Office 365, vedere [Catene di certificati di Office 365](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).
  

