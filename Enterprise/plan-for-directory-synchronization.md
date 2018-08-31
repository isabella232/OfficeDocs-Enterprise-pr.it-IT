---
title: Pianificazione della sincronizzazione della directory per Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Viene descritta la sincronizzazione delle directory con Office 365, pulitura di Active Directory e dello strumento di Azure Active Directory connettersi.
ms.openlocfilehash: cc2a2ca050facaf53f0a235898c31ae7aaeff4ae
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541274"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a>Pianificazione della sincronizzazione della directory per Office 365
A seconda delle esigenze aziendali e dei requisiti tecnici, la sincronizzazione delle directory è la scelta più comune di provisioning per i clienti aziendali che passano a Office 365. La sincronizzazione delle directory consente l'identità essere gestiti in Active Directory locale e tutti gli aggiornamenti a tale identità vengono sincronizzati con Office 365.
  
Non vi sono due aspetti da tenere presenti quando si pianifica un'implementazione della sincronizzazione della directory, incluse la preparazione della directory e i requisiti e funzionalità di Azure Active Directory. Preparazione della directory sono descritte alcune aree. Sono inclusi gli aggiornamenti di attributo, pianificazione posizionamento dei controller di dominio e il controllo. Funzionalità e i requisiti di pianificazione, è necessario determinare le autorizzazioni necessarie, la pianificazione per gli scenari più foreste o directory, la pianificazione della capacità e la sincronizzazione bidirezionale.
  
## <a name="office-365-identity-models"></a>Modelli di identità di Office 365
Office 365 utilizza due modelli principali di autenticazione e identità: cloud l'autenticazione e l'autenticazione federata.
  
### <a name="cloud-authentication"></a>Autenticazione cloud
[Identità cloud](about-office-365-identity.md) - creare e gestire gli utenti nell'interfaccia di amministrazione di Office 365, è inoltre possibile utilizzare Windows PowerShell o Azure Active Directory per gestire gli utenti. 
  
[Sincronizzare il valore hash password con single sign-on agevole](about-office-365-identity.md) - il modo più semplice per abilitare l'autenticazione per gli oggetti directory locale in Azure Active Directory. Con sincronizzazione delle hash password (PHS), sincronizzare gli oggetti di account utente di Active Directory locale con Office 365 e gestire gli utenti locale. 
  
[Autenticazione pass-through con single sign-on agevole](about-office-365-identity.md) - fornisce una convalida password semplice per i servizi di autenticazione Azure AD utilizzando un agente di software in esecuzione su uno o più server locali per convalidare gli utenti direttamente con i Active Directory locale. 
  
### <a name="federated-authentication"></a>Autenticazione federata
[Identità federata con Active Directory Federation Services AD FS](about-office-365-identity.md) - principalmente per le organizzazioni di grandi imprese con requisiti di autenticazione più complessi, locale oggetti directory sono sincronizzati con Office 365 e sono gli account utente gestita locale. 
  
[Provider di autenticazione e identità di terze parti](about-office-365-identity.md) -nella directory locale oggetti possono essere sincronizzati con Office 365 e l'accesso alle risorse cloud principalmente gestito da un provider di identità di terze parti (IdP). 
  
## <a name="active-directory-cleanup"></a>Pulizia di Active Directory
Per garantire una transizione senza problemi a Office 365 utilizzando la sincronizzazione, è consigliabile preparare la foresta di Active Directory prima di iniziare la distribuzione di sincronizzazione della directory di Office 365.
  
Quando si [configurare la sincronizzazione delle directory in Office 365](set-up-directory-synchronization.md), una delle operazioni è possibile [scaricare ed eseguirla lo strumento IdFix](install-and-run-idfix.md). È possibile utilizzare lo strumento IdFix al fine di facilitare la [pulitura directory](prepare-directory-attributes-for-synch-with-idfix.md).
  
La pulitura directory dovrebbe consistere nelle attività seguenti:

- Rimozione degli attributi **proxyAddress** e **userPrincipalName** duplicati.
- Aggiornamento degli attributi **userPrincipalName** vuoti e non validi con attributi **userPrincipalName** validi.
- Rimuovere i caratteri non validi e ambigui **givenName**, cognome ( **sn** ), **sAMAccountName**, **displayName**, **posta elettronica**, **proxyAddresses**, **mailNickname**e **userPrincipalName** attributi. Per informazioni dettagliate sulla preparazione di attributi, vedere [l'elenco di attributi che vengono sincronizzati per lo strumento di sincronizzazione di Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).
    
    > [!NOTE]
    > Questi sono gli stessi attributi che esegue la sincronizzazione di Azure Active Directory Connetti. 
  
## <a name="multiforest-deployment-considerations"></a>Considerazioni sulla distribuzione a più foreste
Per più foreste e le opzioni SSO, utilizzare la [connessione Active Directory di installazione personalizzata di Azure](https://go.microsoft.com/fwlink/p/?LinkId=698430).
  
Se l'organizzazione dispone di più foreste per l'autenticazione (foreste di accesso), è consigliabile le operazioni seguenti:
  
- **Valutare le foreste di consolidamento.** In generale, non esiste più sovraccarico necessario per gestire più foreste. A meno che l'organizzazione dispone di vincoli di protezione che determinano la necessità di foreste distinte, prendere in considerazione per semplificare l'ambiente locale.
- **Usa solo nella foresta di accesso principale.** Provare a distribuire Office 365 solo in tale foresta per l'implementazione iniziale di Office 365. 
    
Se è possibile consolidare la distribuzione di Active Directory più foreste o utilizza altri servizi directory per la gestione delle identità, è possibile sincronizzare con l'aiuto di Microsoft o partner.
  
Per ulteriori informazioni, vedere [Sincronizzazione di Directory a più foreste con Scenario Single Sign-On](https://go.microsoft.com/fwlink/p/?LinkId=525321).
  
## <a name="directory-integration-tools"></a>Strumenti di integrazione directory
La sincronizzazione delle directory è la sincronizzazione degli oggetti directory (utenti, gruppi e contatti) da un ambiente Active Directory locale per l'infrastruttura di directory di Office 365. Vedere [Strumenti di integrazione della directory](https://go.microsoft.com/fwlink/p/?LinkID=510956) per un elenco di strumenti disponibili e le relative funzionalità. Lo strumento consigliato da utilizzare è [La connessione di Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=525323).
  
Quando gli account utente vengono sincronizzati con la directory di Office 365 per la prima volta, questi vengono contrassegnati come non attivato. Non possono inviare o ricevere posta elettronica e non utilizzano licenze di sottoscrizione. Quando si è pronti per assegnare sottoscrizioni a Office 365 per utenti specifici, è necessario selezionare e attivarle mediante l'assegnazione di una licenza valida.
  
La sincronizzazione delle directory è necessaria per le caratteristiche e funzionalità seguenti:
  
- SSO
    
- Coesistenza di Lync
    
- Distribuzione ibrida di Exchange tra cui:
    
  - Completamente condiviso elenco indirizzi globale (GAL) tra l'ambiente Exchange locale e Office 365.
  - Sincronizzazione dell'elenco indirizzi globale da sistemi di posta diversi.
  - Possibilità di aggiungere gli utenti e rimuovere utenti dal offerte di servizi di Office 365. È pertanto necessario quanto segue:
  - Sincronizzazione bidirezionale deve essere configurata durante l'installazione di sincronizzazione della directory. Per impostazione predefinita, gli strumenti di sincronizzazione della directory scrivere nella directory le informazioni solo nel cloud. Quando si configura la sincronizzazione bidirezionale, si abilita la funzionalità di writeback in modo che un numero limitato di attributi degli oggetti viene copiato dal cloud e quindi scritto li Active Directory locale. Writeback è detto anche come modalità ibrida. 
  - Una distribuzione ibrida di Exchange locale
  - Possibilità di spostare alcune cassette postali degli utenti a Office 365 mantenendo altre cassette postali in locale.
  - Mittenti attendibili e mittenti bloccati in locale vengono replicate a Office 365.
  - Delega di base e funzionalità della posta elettronica di autorizzazione invio per conto dell'utente.
  - Si dispone di una soluzione di autenticazione locale integrata smart card o a più fattori.
    
- Sincronizzazione di foto, miniature, sale riunioni e gruppi di sicurezza