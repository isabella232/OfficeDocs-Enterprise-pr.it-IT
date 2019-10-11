---
title: Sincronizzazione della directory e dell'identità ibrida per Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.date: 05/20/2019
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Descrive la sincronizzazione della directory con Office 365, la pulizia dei servizi di dominio Active Directory e lo strumento Azure Active Directory Connect.
ms.openlocfilehash: fda9750ae6038f062938f3c8ad92fe1859c2d7e1
ms.sourcegitcommit: 2e6fadb5b2b16619ad141b6293d3466460720cb4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2019
ms.locfileid: "37428116"
---
# <a name="hybrid-identity-and-directory-synchronization-for-office-365"></a>Sincronizzazione della directory e dell'identità ibrida per Office 365

*Questo articolo si applica sia a Office 365 Enterprise che a Microsoft 365 Enterprise*

A seconda delle esigenze aziendali e dei requisiti tecnici, il modello di identità ibrido e la sincronizzazione della directory rappresentano la scelta più comune per i clienti aziendali che adottano Office 365. La sincronizzazione della directory consente di gestire le identità nei servizi di dominio Active Directory e tutti gli aggiornamenti per gli account utente, i gruppi e i contatti vengono sincronizzati con il tenant Azure Active Directory (Azure AD) dell'abbonamento a Office 365.

>[!Note]
>Quando gli account utente di servizi di dominio Active Directory vengono sincronizzati per la prima volta, non viene assegnata automaticamente una licenza di Office 365 e non possono accedere ai servizi di Office 365, ad esempio la posta elettronica. È necessario assegnare una licenza a questi account utente, sia singolarmente che dinamicamente tramite l'appartenenza al gruppo.
>

## <a name="authentication-for-hybrid-identity"></a>Autenticazione per l'identità ibrida

Quando si utilizza il modello di identità ibrido, esistono due tipi di autenticazione:

- Autenticazione gestita

  Azure AD gestisce il processo di autenticazione utilizzando una versione con hash locale memorizzata della password o invia le credenziali a un agente software locale per l'autenticazione da parte di servizi di dominio Active Directory locale.

- Autenticazione federata

  Azure AD reindirizza il computer client che richiede l'autenticazione per contattare un altro provider di identità.

### <a name="managed-authentication"></a>Autenticazione gestita

Esistono due tipi di autenticazione gestita:

- Sincronizzazione degli hash delle password (pH)

  Azure AD esegue l'autenticazione stessa.

- Autenticazione pass-through

  Azure AD ha servizi di dominio Active Directory per eseguire l'autenticazione.


#### <a name="password-hash-synchronization"></a>Sincronizzazione hash delle password

Con la sincronizzazione degli hash delle password (pH), è possibile sincronizzare gli account utente di servizi di dominio Active Directory con Office 365 e gestire gli utenti in locale. Gli hash delle password degli utenti vengono sincronizzati da servizi di dominio Active Directory ad Azure AD in modo che gli utenti abbiano la stessa password locale e nel cloud. Questo è il modo più semplice per abilitare l'autenticazione per le identità di servizi di dominio Active Directory in Azure AD. 

![](./media/plan-for-directory-synchronization/phs-authentication.png)

Quando le password vengono modificate o reimpostate in locale, i nuovi hash delle password vengono sincronizzati con Azure AD, in modo che gli utenti possano sempre utilizzare la stessa password per le risorse cloud e le risorse locali. Le password degli utenti non vengono mai inviate ad Azure AD o archiviate in Azure AD in testo non crittografato. Alcune funzionalità Premium di Azure AD, ad esempio la protezione delle identità, richiedono pH indipendentemente dal metodo di autenticazione selezionato.
  
Per ulteriori informazioni, vedere [choosing pH](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) .
  
#### <a name="pass-through-authentication"></a>Autenticazione pass-through

L'autenticazione pass-through (PTA) fornisce una semplice convalida delle password per i servizi di autenticazione di Azure AD utilizzando un agente software in esecuzione su uno o più server locali per convalidare gli utenti direttamente con il servizio di dominio Active Directory. Con l'autenticazione pass-through (PTA), è possibile sincronizzare gli account utente di servizi di dominio Active Directory con Office 365 e gestire gli utenti in locale. 

![](./media/plan-for-directory-synchronization/pta-authentication.png)

PTA consente agli utenti di accedere alle risorse e alle applicazioni locali e di Office 365 utilizzando l'account locale e la password. Questa configurazione consente di convalidare le password degli utenti direttamente nei servizi di dominio Active Directory locali senza archiviare gli hash delle password in Azure AD. 

PTA è anche per le organizzazioni con un requisito di sicurezza per applicare immediatamente gli Stati degli account utente locali, i criteri di password e le ore di accesso. 
  
Per ulteriori informazioni, vedere [scegliere PTA](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) .
  
### <a name="federated-authentication"></a>Autenticazione federata

L'autenticazione federata è principalmente per organizzazioni aziendali di grandi dimensioni con requisiti di autenticazione più complessi. Le identità di servizi di dominio Active Directory sono sincronizzate con Office 365 e gli account utente vengono gestiti in locale. Con l'autenticazione federata, gli utenti hanno la stessa password in locale e nel cloud e non devono accedere di nuovo per utilizzare Office 365. 

L'autenticazione federata può supportare ulteriori requisiti di autenticazione, ad esempio l'autenticazione basata su smartcard o un'autenticazione a più fattori di terze parti e in genere è necessario quando le organizzazioni non dispongono di un requisito di autenticazione supportato nativamente da Azure AD.
 
Per ulteriori informazioni, vedere [scelta dell'autenticazione federata](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) .
  
#### <a name="third-party-authentication-and-identity-providers"></a>Provider di identità e autenticazione di terze parti

Gli oggetti directory locali possono essere sincronizzati con Office 365 e l'accesso alle risorse cloud è gestito principalmente da un provider di identità di terze parti (IdP). Se nell'organizzazione viene utilizzata una soluzione di terze parti, è possibile configurare l'accesso con tale soluzione per Office 365 purché la soluzione di Federazione di terze parti sia compatibile con Azure AD.
  
Per ulteriori informazioni, vedere [compatibilità di Azure ad Federation](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) .
  
## <a name="ad-ds-cleanup"></a>Pulizia di servizi di dominio Active Directory

Per garantire una transizione senza problemi a Office 365 mediante la sincronizzazione, è necessario preparare la foresta di AD DS prima di iniziare la distribuzione della sincronizzazione della directory di Office 365.
  
Quando si [Configura la sincronizzazione della directory in Office 365](set-up-directory-synchronization.md), uno dei passaggi è [scaricare ed eseguire lo strumento IdFix](install-and-run-idfix.md). È possibile utilizzare lo strumento IdFix per facilitare la [pulizia della directory](prepare-directory-attributes-for-synch-with-idfix.md).
  
La pulizia della directory dovrebbe concentrarsi sulle attività seguenti:

- Rimuovere gli attributi **ProxyAddress** e **userPrincipalName** duplicati.
- Aggiornare gli attributi **userPrincipalName** vuoti e non validi con gli attributi **userPrincipalName** validi.
- Rimuovere i caratteri non validi e discutibili nelle **DATENAME**, cognome ( **sn** ), **sAMAccountName**, **DisplayName**, **mail**, **proxyAddresses**, **mailNickname**e **userPrincipalName** attributi. Per informazioni dettagliate sulla preparazione degli attributi, vedere [l'elenco degli attributi sincronizzati tramite lo strumento di sincronizzazione di Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).

    > [!NOTE]
    > Si tratta degli stessi attributi sincronizzati da Azure AD Connect. 
  
## <a name="multi-forest-deployment-considerations"></a>Considerazioni sulla distribuzione di più foreste

Per più foreste e opzioni SSO, utilizzare l' [installazione personalizzata di Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).
  
Se l'organizzazione dispone di più foreste per l'autenticazione (foreste di accesso), è consigliabile eseguire le operazioni seguenti:
  
- **Valutare la possibilità di consolidare le foreste.** In generale, è necessario un sovraccarico maggiore per la gestione di più foreste. A meno che l'organizzazione non disponga di vincoli di sicurezza che determinano la necessità di foreste separate, valutare la possibilità di semplificare l'ambiente locale.
- **Utilizzare solo nella foresta di accesso principale.** Valutare la possibilità di distribuire Office 365 solo nella foresta di accesso principale per l'implementazione iniziale di Office 365. 

Se non è possibile consolidare la distribuzione di servizi di dominio Active Directory a più foreste o se si utilizzano altre funzionalità di gestione delle identità, potrebbe essere possibile sincronizzarle con l'aiuto di Microsoft o di un partner.
  
Per ulteriori informazioni, vedere [multi-Forest Directory Sync with Single Sign-on scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321) .
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a>Caratteristiche che dipendono dalla sincronizzazione della directory
  
La sincronizzazione della directory è necessaria per le caratteristiche e le funzionalità seguenti:
  
- Accesso Single Sign-on (SSO) di Azure AD
- Coesistenza Skype
- Distribuzione ibrida di Exchange, tra cui:
  - Elenco indirizzi globale (GAL, Global Address List) completamente condiviso tra l'ambiente Exchange locale e Office 365.
  - Sincronizzazione delle informazioni dell'elenco indirizzi globale da diversi sistemi di posta elettronica.
  - La possibilità di aggiungere gli utenti a e rimuovere gli utenti dalle offerte di servizi di Office 365. Per questo è necessario quanto segue:
  - La sincronizzazione bidirezionale deve essere configurata durante la configurazione della sincronizzazione della directory. Per impostazione predefinita, gli strumenti di sincronizzazione della directory scrivono le informazioni della directory solo nel cloud. Quando si configura la sincronizzazione bidirezionale, è possibile abilitare la funzionalità di write-back in modo che un numero limitato di attributi dell'oggetto vengano copiati dal cloud e quindi riscriverli nel servizio di dominio Active Directory locale. Il write-back è noto anche come modalità ibrida di Exchange. 
  - Una distribuzione ibrida di Exchange locale
  - La possibilità di spostare le cassette postali degli utenti in Office 365 mantenendo le cassette postali degli utenti locali.
  - I mittenti attendibili e i mittenti bloccati in locale vengono replicati in Office 365.
  - La delega di base e la funzionalità di invio per conto di posta elettronica.
  - Si dispone di una soluzione di autenticazione con smart card o multi-factor integrata.
- Sincronizzazione di foto, miniature, sale conferenze e gruppi di sicurezza

## <a name="next-step"></a>Passaggio successivo

Quando si è pronti per la distribuzione dell'identità ibrida, vedere [Prepare to provisioning Users](prepare-for-directory-synchronization.md).
  
## <a name="see-also"></a>Vedere anche

[Panoramica di Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)

