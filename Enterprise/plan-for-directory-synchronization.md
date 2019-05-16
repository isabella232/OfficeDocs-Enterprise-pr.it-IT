---
title: Pianificare la sincronizzazione della directory per Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
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
description: Descrive la sincronizzazione della directory con Office 365, la pulizia di Active Directory e lo strumento Azure Active Directory Connect.
ms.openlocfilehash: b1d48696195c572de3a87bc5acb0646fc4bd0f41
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069362"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a>Pianificare la sincronizzazione della directory per Office 365

A seconda delle esigenze aziendali e dei requisiti tecnici, la sincronizzazione della directory è la scelta di provisioning più comune per i clienti aziendali che si spostano su Office 365. La sincronizzazione della directory consente la gestione delle identità in Active Directory locale e tutti gli aggiornamenti di tale identità vengono sincronizzati con Office 365.
  
Quando si pianifica un'implementazione della sincronizzazione della directory, inclusa la preparazione della directory e i requisiti e le funzionalità di Azure Active Directory, è necessario tenere presente un paio di considerazioni. La preparazione della directory copre diverse aree. Sono inclusi gli aggiornamenti degli attributi, il controllo e la pianificazione del posizionamento dei controller di dominio. I requisiti e le funzionalità di pianificazione includono la determinazione delle autorizzazioni necessarie, la pianificazione di scenari a più foreste e directory, la pianificazione della capacità e la sincronizzazione bidirezionale.
  
## <a name="office-365-identity-models"></a>Modelli di identità di Office 365

Office 365 utilizza due principali modelli di autenticazione e identità: autenticazione del cloud e autenticazione federata.
  
### <a name="cloud-authentication"></a>Autenticazione del cloud

[Identità cloud](about-office-365-identity.md) -creare e gestire gli utenti nell'interfaccia di [amministrazione di Microsoft 365](https://admin.microsoft.com), è anche possibile utilizzare Windows PowerShell o Azure Active Directory per gestire gli utenti.
  
[Sincronizzazione hash delle password con Single Sign-on senza soluzione di continuità](about-office-365-identity.md) : il modo più semplice per abilitare l'autenticazione per gli oggetti directory locali in Azure ad. Con la sincronizzazione degli hash delle password (pH), è possibile sincronizzare gli oggetti dell'account utente di Active Directory locale con Office 365 e gestire gli utenti in locale.
  
[Autenticazione pass-through con Single Sign-on senza soluzione di continuità](about-office-365-identity.md) -fornisce una semplice convalida delle password per i servizi di autenticazione di Azure ad utilizzando un agente software in esecuzione su uno o più server locali per convalidare gli utenti direttamente con il proprio Active Directory locale.
  
### <a name="federated-authentication"></a>Autenticazione federata

[Identità federata con Active Directory Federation Services ADFS](about-office-365-identity.md) -principalmente per organizzazioni aziendali di grandi dimensioni con requisiti di autenticazione più complessi, gli oggetti directory locali sono sincronizzati con Office 365 e gli account utente sono gestito in locale.
  
[Autenticazione di terze parti e provider di identità](about-office-365-identity.md) -gli oggetti directory locali possono essere sincronizzati con Office 365 e l'accesso alle risorse cloud è gestito principalmente da un provider di identità di terze parti.
  
## <a name="active-directory-cleanup"></a>Pulizia di Active Directory

Per garantire una transizione senza problemi a Office 365 mediante la sincronizzazione, è consigliabile preparare la foresta di Active Directory prima di iniziare la distribuzione della sincronizzazione della directory di Office 365.
  
Quando si [Configura la sincronizzazione della directory in Office 365](set-up-directory-synchronization.md), uno dei passaggi è [scaricare ed eseguire lo strumento IdFix](install-and-run-idfix.md). È possibile utilizzare lo strumento IdFix per facilitare la [pulizia della directory](prepare-directory-attributes-for-synch-with-idfix.md).
  
La pulizia della directory dovrebbe concentrarsi sulle attività seguenti:

- Rimuovere gli attributi **ProxyAddress** e **userPrincipalName** duplicati.
- Aggiornare gli attributi **userPrincipalName** vuoti e non validi con gli attributi **userPrincipalName** validi.
- Rimuovere i caratteri non validi e discutibili **** nelle DATENAME, cognome ( **sn** ), **sAMAccountName**, **DisplayName**, **mail**, **proxyAddresses**, **mailNickname**e **userPrincipalName** attributi. Per informazioni dettagliate sulla preparazione degli attributi, vedere [l'elenco degli attributi sincronizzati tramite lo strumento di sincronizzazione di Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).

    > [!NOTE]
    > Questi sono gli stessi attributi che Azure AD Connect sincronizza. 
  
## <a name="multi-forest-deployment-considerations"></a>Considerazioni sulla distribuzione di più foreste

Per più foreste e opzioni SSO, utilizzare l' [installazione personalizzata di Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).
  
Se l'organizzazione dispone di più foreste per l'autenticazione (foreste di accesso), è consigliabile eseguire le operazioni seguenti:
  
- **Valutare il consolidamento delle foreste.** In generale, è necessario un sovraccarico maggiore per la gestione di più foreste. A meno che l'organizzazione non disponga di vincoli di sicurezza che determinano la necessità di foreste separate, valutare la possibilità di semplificare l'ambiente locale.
- **Utilizzare solo nella foresta di accesso principale.** Valutare la possibilità di distribuire Office 365 solo nella foresta di accesso principale per l'implementazione iniziale di Office 365. 

Se non è possibile consolidare la distribuzione di Active Directory a più foreste o se si utilizzano altri servizi directory per gestire le identità, potrebbe essere possibile sincronizzarle con l'aiuto di Microsoft o di un partner.
  
Per ulteriori informazioni, vedere [scenario di sincronizzazione della directory con Single Sign-on](https://go.microsoft.com/fwlink/p/?LinkId=525321).
  
## <a name="directory-integration-tools"></a>Strumenti di integrazione della directory

La sincronizzazione della directory è la sincronizzazione degli oggetti directory (utenti, gruppi e contatti) dall'ambiente Active Directory locale all'infrastruttura di directory di Office 365. Per un elenco degli strumenti disponibili e delle relative funzionalità, vedere [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) . Lo strumento consigliato per l'utilizzo è [Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323).
  
Quando gli account utente vengono sincronizzati con la directory di Office 365 per la prima volta, vengono contrassegnati come non attivati. Non possono inviare o ricevere messaggi di posta elettronica e non utilizzano licenze di sottoscrizione. Quando si è pronti per assegnare abbonamenti a Office 365 a utenti specifici, è necessario selezionarli e attivarli assegnando una licenza valida.
  
La sincronizzazione della directory è necessaria per le caratteristiche e le funzionalità seguenti:
  
- SSO
- Coesistenza Skype
- Distribuzione ibrida di Exchange, tra cui:
  - Elenco indirizzi globale (GAL, Global Address List) completamente condiviso tra l'ambiente Exchange locale e Office 365.
  - Sincronizzazione delle informazioni dell'elenco indirizzi globale da diversi sistemi di posta elettronica.
  - La possibilità di aggiungere gli utenti a e rimuovere gli utenti dalle offerte di servizi di Office 365. Per questo è necessario quanto segue:
  - La sincronizzazione bidirezionale deve essere configurata durante la configurazione della sincronizzazione della directory. Per impostazione predefinita, gli strumenti di sincronizzazione della directory scrivono le informazioni della directory solo nel cloud. Quando si configura la sincronizzazione bidirezionale, è possibile abilitare la funzionalità di write-back in modo che un numero limitato di attributi oggetto venga copiato dal cloud e quindi riscritto in Active Directory locale. Il write-back è noto anche come modalità ibrida di Exchange. 
  - Una distribuzione ibrida di Exchange locale
  - La possibilità di spostare le cassette postali degli utenti in Office 365 mantenendo le cassette postali degli utenti locali.
  - I mittenti attendibili e i mittenti bloccati in locale vengono replicati in Office 365.
  - La delega di base e la funzionalità di invio per conto di posta elettronica.
  - Si dispone di una soluzione di autenticazione con smart card o multi-factor integrata.
- Sincronizzazione di foto, miniature, sale conferenze e gruppi di sicurezza