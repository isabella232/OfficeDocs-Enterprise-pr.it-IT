---
title: Informazioni sull'identità di Office 365 e Azure Active Directory
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Informazioni sul modo in cui l'identità dell'utente viene gestita in Office 365.
ms.openlocfilehash: 0b0dd133979a5f94f7f8322c532c61fd24719359
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085425"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a>Informazioni sull'identità di Office 365 e Azure Active Directory

Office 365 utilizza l'identità utente basata sul cloud e il servizio di autenticazione Azure Active Directory (Azure AD) per gestire gli utenti. Scegliere se la gestione delle identità è configurata tra l'organizzazione locale e Office 365 è una decisione iniziale che rappresenta uno dei fondamenti dell'infrastruttura cloud. Poiché la modifica di questa configurazione in un secondo momento può essere difficile, prendere in considerazione le opzioni per determinare cosa funziona meglio per le esigenze dell'organizzazione. È possibile scegliere tra due modelli di autenticazione principali di Office 365 per configurare e gestire gli account utente. **autenticazione del cloud** e **autenticazione federata**.
  
È importante considerare attentamente quali di questi modelli di autenticazione e identità utilizzare per l'esecuzione. Si pensi all'ora, alla complessità esistente e ai costi per implementare e gestire le opzioni di autenticazione e identità. Questi fattori sono diversi per ogni organizzazione; è necessario comprendere i concetti principali per le opzioni di identità che consentono di scegliere il modello di autenticazione e identità che si desidera utilizzare per la distribuzione.
  
## <a name="cloud-authentication"></a>Autenticazione del cloud

Se si dispone o non si dispone di un ambiente Active Directory esistente in locale, sono disponibili diverse opzioni per gestire l'autenticazione e i servizi di identità per gli utenti con Office 365.
  
### <a name="cloud-only"></a>Solo cloud

Con il modello solo cloud, è possibile gestire gli account utente solo in Office 365. Non sono necessari server locali. è tutto gestito nel cloud da Azure AD. È possibile creare e gestire gli utenti nell'interfaccia di amministrazione di Office 365 o utilizzando i [cmdlet di PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell) di Windows PowerShell e l'identità e l'autenticazione vengono gestiti completamente nel cloud da Azure ad. Il modello solo cloud è in genere una buona scelta se: 
  
- Non si dispone di altre directory degli utenti locali.
    
- Si dispone di una directory locale molto complessa e si vuole semplicemente evitare che il lavoro venga integrato con esso.
    
- Si dispone di una directory locale esistente, ma si desidera eseguire una valutazione o un pilota di Office 365. Successivamente, è possibile associare gli utenti cloud agli utenti locali quando si è pronti per la connessione alla directory locale.
    
Per iniziare a utilizzare l'identità cloud, vedere [set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa).
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a>Sincronizzazione hash delle password con Single Sign-on senza soluzione di continuità

Il modo più semplice per abilitare l'autenticazione per gli oggetti directory locali in Azure AD. Con la sincronizzazione degli hash delle password (pH), è possibile sincronizzare gli oggetti dell'account utente di Active Directory locale con Office 365 e gestire gli utenti in locale. Gli hash delle password degli utenti vengono sincronizzati da Active Directory locale ad Azure AD in modo che gli utenti abbiano la stessa password locale e nel cloud. Quando le password vengono modificate o reimpostate in locale, i nuovi hash delle password vengono sincronizzati con Azure AD, in modo che gli utenti possano sempre utilizzare la stessa password per le risorse cloud e le risorse locali. Le password non vengono mai inviate ad Azure AD o archiviate in Azure AD in testo non crittografato. Alcune funzionalità Premium di Azure AD, ad esempio la protezione delle identità, richiedono pH indipendentemente dal metodo di autenticazione selezionato. Con l'accesso Single Sign-on, gli utenti vengono automaticamente connessi a Azure AD quando sono presenti nei propri dispositivi aziendali e collegati alla rete aziendale.
  
Ulteriori informazioni su come [scegliere la sincronizzazione hash delle password](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) e l' [accesso Single Sign-on](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a>Autenticazione pass-through con accesso Single Sign-on senza problemi

Fornisce una semplice convalida delle password per i servizi di autenticazione di Azure AD utilizzando un agente software in esecuzione su uno o più server locali per convalidare gli utenti direttamente con Active Directory locale. Con l'autenticazione pass-through (PTA), è possibile sincronizzare gli oggetti dell'account utente di Active Directory locale con Office 365 e gestire gli utenti in locale. Consente agli utenti di accedere alle risorse e alle applicazioni locali e di Office 365 utilizzando l'account locale e la password. Questa configurazione consente di convalidare le password degli utenti direttamente nei confronti di Active Directory locale senza inviare hash delle password a Office 365. Le aziende che dispongono di un requisito di sicurezza per applicare immediatamente gli Stati degli account utente locali, i criteri di password e le ore di accesso utilizzeranno questo metodo di autenticazione. Con l'accesso Single Sign-on, gli utenti vengono automaticamente connessi a Azure AD quando sono presenti nei propri dispositivi aziendali e collegati alla rete aziendale.
  
Ulteriori informazioni su come [scegliere l'autenticazione pass-through e l'](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) [accesso Single Sign-on senza interruzioni](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).
  
## <a name="federated-authentication-options"></a>Opzioni di autenticazione federata

Se si dispone di un ambiente Active Directory esistente in locale, è possibile integrare Office 365 con la directory utilizzando l'autenticazione federata per gestire l'autenticazione e i servizi di identità per gli utenti in Office 365.
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a>Identità federata con Active Directory Federation Services (AD FS)

Principalmente per organizzazioni aziendali di grandi dimensioni con requisiti di autenticazione più complessi, gli oggetti directory locali vengono sincronizzati con gli account di Office 365 e gli utenti vengono gestiti in locale. Con AD FS, gli utenti hanno la stessa password in locale e nel cloud e non devono accedere di nuovo per usare Office 365. Questo modello di autenticazione federata può fornire ulteriori requisiti di autenticazione, ad esempio l'autenticazione basata su smartcard o un'autenticazione a più fattori di terze parti ed è in genere necessario quando le organizzazioni dispongono di un requisito di autenticazione non supportato nativamente da Azure AD.
  
Per ulteriori informazioni, vedere [scelta dell'identità federata con](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)ADFS.
  
### <a name="third-party-authentication-and-identity-providers"></a>Provider di identità e autenticazione di terze parti

Gli oggetti directory locali possono essere sincronizzati con Office 365 e l'accesso alle risorse cloud è gestito principalmente da un provider di identità di terze parti (IdP). Se nell'organizzazione viene utilizzata una soluzione di terze parti, è possibile configurare l'accesso con tale soluzione per Office 365 purché la soluzione di Federazione di terze parti sia compatibile con Azure AD.
  
Per ulteriori informazioni, vedere [compatibilità di Azure ad Federation](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility).
  
## <a name="configuring-identity-and-authentication-with-office-365"></a>Configurazione dell'identità e dell'autenticazione con Office 365

L'integrazione delle directory locali con Office 365 e Azure AD è stata semplificata con [Azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect). Azure AD Connect è il modo migliore per connettere le directory ed è la raccomandazione di Microsoft per le organizzazioni di sincronizzare gli utenti nel cloud.
  
È inoltre possibile utilizzare i consulenti di Azure AD: l' [Azure ad Connect Advisor](https://aka.ms/aadconnectpwsync), il consulente per la [distribuzione](https://aka.ms/adfsguidance)di ADFS e la guida alla configurazione di [Azure ad Premium](https://aka.ms/aadpguidance).
  
## <a name="video-training"></a>Video di formazione

Per ulteriori informazioni, vedere il corso video [Office 365: Manage identiTies using Azure ad Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), portato all'utente da LinkedIn Learning.
