---
title: Informazioni sull'identità di Office 365 e Azure Active Directory
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Informazioni su come identità utente viene gestito in Office 365.
ms.openlocfilehash: 0fb6e77aef4495b2284256c13cb21320e6292746
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914981"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a>Informazioni sull'identità di Office 365 e Azure Active Directory

Office 365 utilizza utente basata su cloud identità e autenticazione servizio Azure Active Directory (Azure Active Directory) per gestire gli utenti. Scelta se è configurata la gestione delle identità tra l'organizzazione locale e Office 365 è una decisione anticipata tra la base dell'infrastruttura cloud. Poiché la modifica più avanti in questo configurazione può essere difficile, valutare attentamente le opzioni per determinare le soluzioni migliori per soddisfare le esigenze dell'organizzazione. È possibile scegliere tra due modelli di autenticazione principale in Office 365 per impostare e gestire account utente. **l'autenticazione cloud** e **l'autenticazione federata**.
  
È importante valutare con attenzione quale di questi modelli di autenticazione e identità da utilizzare per la configurazione e in esecuzione. Prendere in considerazione l'ora, complessità esistente e costo per implementare e gestire tutte le opzioni di autenticazione e identità. Questi fattori sono diversi per le organizzazioni. ed è consigliabile acquisire familiarità con i concetti chiave per le opzioni di identità che consentono di scegliere l'autenticazione e il modello di identità che si desidera utilizzare per la distribuzione.
  
## <a name="cloud-authentication"></a>Autenticazione cloud

A seconda se si dispone o non dispongono di un esistente Active Directory ambiente locale, sono disponibili diverse opzioni per gestire i servizi di autenticazione e identità per gli utenti con Office 365.
  
### <a name="cloud-only"></a>Solo cloud

Con il modello cloud-only, vengono gestiti solo gli account utente in Office 365. Nessun server locali sono necessari; viene tutto gestito nel cloud per Azure Active Directory. Creare e gestire gli utenti nell'interfaccia di amministrazione di Office 365 o tramite Windows PowerShell [i cmdlet di PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell) e l'autenticazione e identità vengono gestite completamente nel cloud per Azure Active Directory. Il modello solo cloud in genere è una buona scelta se: 
  
- È non necessario alcun altro directory utente locale.
    
- Si dispone di una directory locale molto complessa e si desidera evitare il lavoro per l'integrazione con lo.
    
- Si dispone di una directory locale esistente, ma si desidera eseguire una versione di valutazione o pilota di Office 365. In seguito, è possibile associare gli utenti di cloud per gli utenti locali quando si è pronti per la connessione alla directory locale.
    
Per informazioni introduttive sull'identità cloud, vedere [configurare Office 365 per aziende](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa).
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a>Sincronizzazione delle password hash con single sign-on semplice

Il modo più semplice per abilitare l'autenticazione per gli oggetti directory locale in Azure Active Directory. Con sincronizzazione delle hash password (PHS), sincronizzare gli oggetti di account utente di Active Directory locale con Office 365 e gestire gli utenti locale. Gli hash password utente vengono sincronizzati da Active Directory locale con Azure Active Directory in modo che gli utenti hanno lo stessa password in locale e nel cloud. Quando le password vengono modificate o reimpostare locale, i nuovi hash password vengono sincronizzate con Azure Active Directory in modo che gli utenti possono utilizzare sempre la stessa password per le risorse cloud e le risorse locali. Le password sono mai inviate per Azure Active Directory o archiviate in Azure Active Directory in testo non crittografato. Alcune funzionalità premium di Azure Active Directory, ad esempio la protezione dell'identità, richiedono PHS indipendentemente dal fatto che sia selezionato il metodo di autenticazione. Con agevole single sign-on, gli utenti vengono connessi automaticamente al Azure Active Directory quando vengono nei rispettivi dispositivi aziendali e connessi alla rete aziendale.
  
Ulteriori informazioni sulla [scelta di sincronizzazione delle password hash](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) e [senza problemi servizio single sign-on](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a>Autenticazione pass-through con single sign-on semplice

Fornisce una convalida password semplice per i servizi di autenticazione Azure AD utilizzando un agente di software in esecuzione su uno o più server locali per convalidare gli utenti direttamente con Active Directory locale. Con l'autenticazione pass-through (PTA), sincronizzare gli oggetti account utente di Active Directory locale con Office 365 e gestire gli utenti locale. Consente agli utenti di accedere alla sia in locale e risorse di Office 365 e le applicazioni con il proprio account locale e una password. Questa configurazione consente di convalidare le password degli utenti direttamente a fronte di Active Directory locale senza inviare gli hash password a Office 365. Indica le società con un requisito di protezione per applicare immediatamente l'account utente locali, criteri password e le ore di accesso utilizzerà questo metodo di autenticazione. Con agevole single sign-on, gli utenti vengono connessi automaticamente al Azure Active Directory quando vengono nei rispettivi dispositivi aziendali e connessi alla rete aziendale.
  
Ulteriori informazioni sulla [scelta dell'autenticazione pass-through](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) e [single sign-on senza problemi](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).
  
## <a name="federated-authentication-options"></a>Opzioni di autenticazione federata

Se si dispongono di un esistente Active Directory ambiente locale, è possibile integrare con la directory di Office 365 utilizzando l'autenticazione federata per gestire i servizi di autenticazione e identità per gli utenti di Office 365.
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a>Identità federata con Active Directory Federation Services (ADFS)

Principalmente per grandi aziende con requisiti di autenticazione più complessi, locale oggetti directory sono sincronizzati con Office 365 e gli account utente sono gestiti in locale. Con ADFS, gli utenti hanno lo stessa password in locale e nel cloud e non è necessario accedere nuovamente a utilizzare Office 365. In questo modello di autenticazione federativa può offrire i requisiti di autenticazione aggiuntivi, ad esempio l'autenticazione basata su smart card o un'autenticazione a più fattori di terze parti ed è in genere necessario quando le organizzazioni sono un requisito di autenticazione non in modo nativo supportato da Azure Active Directory.
  
Ulteriori informazioni sulla [scelta di identità federata con ADFS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn).
  
### <a name="third-party-authentication-and-identity-providers"></a>Provider di autenticazione e identità di terze parti

Locale oggetti directory possono essere sincronizzati con Office 365 e l'accesso alle risorse cloud principalmente gestito da un provider di identità di terze parti (IdP). Se l'organizzazione utilizza una soluzione di federazione di terze parti, è possibile configurare sign-on con tale soluzione per Office 365 a condizione che la soluzione di terze parti federazione sia compatibile con Azure Active Directory.
  
Ulteriori informazioni sulla [compatibilità di federazione di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility).
  
## <a name="configuring-identity-and-authentication-with-office-365"></a>Configurazione di identità e autenticazione con Office 365

Integrare le directory locali con Office 365 e Azure Active Directory è stata semplificata con [Azure Active Directory Connetti](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect). Connetti Azure Active Directory sono il modo migliore per connettere le directory ed sono consigliato per le organizzazioni di sincronizzare gli utenti nel cloud.
  
È inoltre possibile utilizzare i consulenti Azure Active Directory: [Preparazione di Azure Active Directory Connect](https://aka.ms/aadconnectpwsync), [advisor distribuzione ADFS](https://aka.ms/adfsguidance)e la [Guida all'installazione di Azure Active Directory Premium](https://aka.ms/aadpguidance).
  
## <a name="video-training"></a>Formazione video

Per ulteriori informazioni, vedere il corso video [Office 365: gestire le identità con Azure Active Directory Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), per offerto da Learning LinkedIn.
