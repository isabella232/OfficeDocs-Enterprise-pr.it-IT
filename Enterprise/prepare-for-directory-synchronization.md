---
title: Preparazione per il provisioning degli utenti verso Office 365 tramite la sincronizzazione della directory
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Descrive come prepararsi a eseguire il provisioning degli utenti a Office 365 utilizzando la sincronizzazione della directory e i vantaggi a lungo termine dell'utilizzo di questo metodo.
ms.openlocfilehash: af402950b3681285898d0d87b897d363a693bf98
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085105"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a>Preparazione per il provisioning degli utenti verso Office 365 tramite la sincronizzazione della directory

Il provisioning degli utenti con la sincronizzazione della directory richiede una maggiore pianificazione e preparazione rispetto alla semplice gestione dell'account aziendale o dell'Istituto di istruzione direttamente in Office 365. Le attività di pianificazione e preparazione aggiuntive sono necessarie per garantire che Active Directory locale sia sincronizzato correttamente con Azure Active Directory. I vantaggi aggiuntivi per l'organizzazione includono:
  
- Riduzione dei programmi amministrativi nell'organizzazione
- Opzione che consente di abilitare lo scenario Single Sign-on
- Automatizzare le modifiche dell'account in Office 365
    
Per ulteriori informazioni sui vantaggi derivanti dall'utilizzo della sincronizzazione della directory, vedere [Directory Synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [understanding Office 365 Identity e Azure Active Directory](about-office-365-identity.md).
  
Per determinare lo scenario più appropriato per l'organizzazione, vedere il [confronto tra gli strumenti di integrazione della directory](https://go.microsoft.com/fwlink/p/?LinkId=525320).
  
## <a name="directory-cleanup-tasks"></a>Attività di pulizia della directory

Prima di iniziare la sincronizzazione della directory, è necessario pulire la directory.
  
Rivedere anche gli [attributi sincronizzati con Azure Active Directory da Azure ad Connect](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).
  
> [!IMPORTANT]
> Se non si esegue la pulizia della directory prima di eseguire la sincronizzazione, il processo di distribuzione può avere un effetto negativo significativo. Potrebbero essere necessari giorni, o addirittura settimane, per eseguire il ciclo di sincronizzazione della directory, identificare gli errori e rieseguire la sincronizzazione. 
  
Nella directory locale, completare le attività di pulizia seguenti:
  
1. Verificare che ogni utente a cui verranno assegnate offerte di servizio di Office 365 abbia un indirizzo di posta elettronica valido e univoco nell'attributo **proxyAddresses**. 
    
2. Rimuovere tutti i valori duplicati nell'attributo **proxyAddresses**. 
    
3.  Se possibile, assicurarsi che ogni utente a cui verranno assegnate le offerte di servizi di Office 365 abbia un valore valido e univoco per l'attributo **userPrincipalName** nell'oggetto **utente** dell'utente. Per un'esperienza di sincronizzazione ottimale, verificare che l'UPN di Active Directory locale corrisponda all'UPN del cloud. Se un utente non dispone di un valore per l'attributo **userPrincipalName** , l'oggetto **utente** deve contenere un valore univoco e valido per l'attributo **sAMAccountName** . Rimuovere tutti i valori duplicati nell'attributo **userPrincipalName** . 
    
4. Per un utilizzo ottimale dell'Elenco indirizzi globale (GAL), verificare che le informazioni presenti nei seguenti attributi siano corrette:
    
  - givenName 
  - cognome
  - displayName
  - Professione
  - Reparto
  - Ufficio
  - Telefono ufficio
  - Cellulare
  - Numero fax
  - Via e numero civico
  - Città
  - Provincia
  - CAP
  - Paese
    
## <a name="directory-object-and-attribute-preparation"></a>Preparazione di oggetti e attributi della directory

La corretta sincronizzazione della directory tra la directory locale e Office 365 richiede la corretta preparazione degli attributi di directory locali. Ad esempio, è necessario assicurarsi che i caratteri specifici non vengano utilizzati in alcuni attributi sincronizzati con l'ambiente Office 365. I caratteri imPrevisti non determinano il failover della sincronizzazione della directory ma potrebbero restituire un avviso. I caratteri non validi provocheranno l'esito negativo della sincronizzazione della directory.
  
La sincronizzazione della directory avrà esito negativo anche se alcuni utenti di Active Directory dispongono di uno o più attributi duplicati. Ogni utente deve disporre di attributi univoci.
  
Gli attributi necessari per la preparazione sono elencati di seguito:
  
 **Nota:** È inoltre possibile utilizzare lo [strumento IdFix](install-and-run-idfix.md) per semplificare il processo. 
  
- **displayName**
    
  - Se l'attributo è presente nell'oggetto utente, verrà sincronizzato con Office 365.
  - A un attributo presente nell'oggetto utente deve corrispondere un valore. Ovvero, l'attributo non deve essere vuoto.
  - Numero massimo di caratteri: 256
    
- **givenName **
    
  - Se l'attributo è presente nell'oggetto utente, viene sincronizzato con Office 365 ma quest'ultimo non lo richiede o utilizza.
  - Numero massimo di caratteri: 64
    
- **posta elettronica**
    
  - Il valore dell'attributo deve essere univoco all'interno della directory.
    
    > [!NOTE]
    > Se sono presenti valori duplicati, il primo utente con il valore è sincronizzato. Gli utenti successivi non verranno visualizzati in Office 365. È necessario modificare il valore di Office 365 oppure modificare entrambi i valori nella directory locale affinché entrambi gli utenti vengano visualizzati in Office 365. 
  
- **mailNickname** (alias di Exchange) 
    
  - Il valore dell'attributo non può iniziare con un punto (.).
  - Il valore dell'attributo deve essere univoco all'interno della directory.
    
- **proxyAddresses **
    
  - Attributo con più valori
  - Numero massimo di caratteri per valore: 256
  - Il valore dell'attributo non deve contenere uno spazio.
  - Il valore dell'attributo deve essere univoco all'interno della directory.
  - Caratteri non validi \< \> : (); , [ ] "
    
    Si noti che i caratteri non validi si applicano ai caratteri che seguono il delimitatore di tipo e ":", in modo che SMTP:User@contso.com sia consentita, ma SMTP:user:M@contoso.com non lo è.
    
    > [!IMPORTANT]
    > Tutti gli indirizzi SMTP (Simple Mail Transport Protocol) devono essere conformi agli standard di messaggistica di posta elettronica. Se esistono indirizzi duplicati o indesiderati, vedere l'argomento della Guida relativo alla [rimozione di indirizzi proxy duplicati e indesiderati in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860). 
  
- **sAMAccountName**
    
  - Numero massimo di caratteri: 20
  - Il valore dell'attributo deve essere univoco all'interno della directory.
  - Caratteri non validi: [\ "|,/ \< \> : + =;? \* ]
  - Se un utente ha un attributo **sAMAccountName** non valido, ma anche un attributo **userPrincipalName** valido, l'account utente verrà creato in Office 365. 
  - Se **sAMAccountName** e **userPrincipalName** non sono validi, è necessario aggiornare l'attributo **userPrincipalName** di Active Directory locale. 
    
- **sn** (cognome) 
    
  - Se l'attributo è presente nell'oggetto utente, viene sincronizzato con Office 365 ma quest'ultimo non lo richiede o utilizza.
    
- **targetAddress**
    
    È necessario che l'attributo **targetAddress** , ad esempio SMTP:Tom@contoso.com, popolato per l'utente, venga visualizzato nell'elenco indirizzi globale di Office 365. In scenari di migrazione della messaggistica di terze parti, ciò richiederebbe l'estensione dello schema di Office 365 per la directory locale. L'estensione dello schema di Office 365 aggiungerà anche altri attributi utili per la gestione degli oggetti di Office 365 che vengono popolati tramite uno strumento di sincronizzazione della directory dalla directory locale. Ad esempio, l'attributo **msExchHideFromAddressLists** per gestire le cassette postali o i gruppi di distribuzione nascosti verrebbe aggiunto. 
   
  - Numero massimo di caratteri: 256
  - Il valore dell'attributo non deve contenere uno spazio.
  - Il valore dell'attributo deve essere univoco all'interno della directory.
  - Caratteri non validi: \< \> \ (); , [ ] "
  - Tutti gli indirizzi SMTP (Simple Mail Transport Protocol) devono essere conformi agli standard di messaggistica di posta elettronica
    
- **userPrincipalName**
    
  - L'attributo **userPrincipalName** deve trovarsi nel formato di accesso di tipo Internet, in cui il nome utente è seguito dal segno di chiocciola (@) e dal nome di dominio: ad esempio, user@contoso.com. Tutti gli indirizzi SMTP (Simple Mail Transport Protocol) devono essere conformi agli standard di messaggistica di posta elettronica.
  - Il numero massimo di caratteri per l'attributo **userPrincipalName** è 113. È consentito un numero specifico di caratteri prima e dopo il simbolo di chiocciola (@), come riportato di seguito: 
  - Numero massimo di caratteri per il nome utente prima del simbolo chiocciola (@): 64
  - Numero massimo di caratteri per il nome di dominio dopo il simbolo chiocciola (@): 48
  - Caratteri non validi: \ &amp; \* % +/=? { } | \< \> ( ) ; : , [ ] "
  - Anche la dieresi è un carattere non valido.
  - Il carattere @ è necessario in ogni valore **userPrincipalName** . 
  - Il carattere @ non può essere il primo carattere in ogni valore **userPrincipalName**. 
  - Il nome utente non può terminare con un punto (.), una e&amp;commerciale (), uno spazio o un segno di chiocciola (@).
  - Il nome utente non può contenere spazi.
  - I domini inStradabili devono essere utilizzati. ad esempio, non è possibile utilizzare i domini locali o interni.
  - Unicode viene convertito in caratteri di sottolineatura.
  - **userPrincipalName** non può contenere valori duplicati nella directory. 
    
## <a name="prepare-the-userprincipalname-attribute"></a>Preparazione dell'attributo userPrincipalName

Active Directory è stato creato per consentire agli utenti finali dell'organizzazione di accedere alla directory tramite **sAMAccountName** o **userPrincipalName**. Analogamente, gli utenti finali possono accedere a Office 365 utilizzando il nome dell'entità utente (UPN) dell'account aziendale o dell'Istituto di istruzione. La sincronizzazione della directory tenta di creare nuovi utenti in Azure Active Directory utilizzando lo stesso UPN presente nella directory locale. L'UPN è formattato come un indirizzo di posta elettronica. 

In Office 365, l'UPN è l'attributo predefinito utilizzato per generare l'indirizzo di posta elettronica. È facile ottenere **userPrincipalName** (in locale e in Azure Active Directory) e l'indirizzo di posta elettronica principale in **proxyAddresses** impostato su valori diversi. Quando sono impostati su valori diversi, è possibile creare confusione per gli amministratori e gli utenti finali. 
  
È consigliabile allineare questi attributi per ridurre la confusione. Per soddisfare i requisiti del servizio Single Sign-on con Active Directory Federation Services (AD FS) 2,0, è necessario assicurarsi che UPN in Azure Active Directory e Active Directory locale corrispondano e utilizzino uno spazio dei nomi di dominio valido.
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a>Aggiungere un suffisso UPN alternativo a servizi di dominio Active Directory

Potrebbe essere necessario aggiungere un suffisso UPN alternativo per associare le credenziali aziendali dell'utente all'ambiente Office 365. Un suffisso UPN è la parte di un UPN a destra del carattere @. UPN che vengono utilizzati per Single Sign-on possono contenere lettere, numeri, punti, trattini e caratteri di sottolineatura, ma nessun altro tipo di carattere.
  
Per ulteriori informazioni su come aggiungere un suffisso UPN alternativo ad Active Directory, vedere [Prepare for Directory Synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a>Corrispondere all'UPN locale con l'UPN di Office 365

Se è già stata configurata la sincronizzazione della directory, l'UPN dell'utente per Office 365 potrebbe non corrispondere all'UPN locale dell'utente definito nel servizio directory locale. Questo può verificarsi quando a un utente è stata assegnata una licenza prima che il dominio sia stato verificato. Per risolvere questo risultato, utilizzare [PowerShell per correggere](https://go.microsoft.com/fwlink/p/?LinkId=396730) l'UPN duplicato per aggiornare l'UPN dell'utente per verificare che l'UPN di Office 365 corrisponda al nome utente aziendale e al dominio. Se si esegue l'aggiornamento dell'UPN nel servizio directory locale e si desidera sincronizzarlo con l'identità di Azure Active Directory, è necessario rimuovere la licenza dell'utente in Office 365 prima di apportare le modifiche in locale. 
  
Vedere anche [come preparare un dominio non instradabile (ad esempio, dominio locale) per la sincronizzazione della directory](prepare-a-non-routable-domain-for-directory-synchronization.md).
  
## <a name="directory-integration-tools"></a>Strumenti di integrazione della directory

La sincronizzazione della directory è la sincronizzazione degli oggetti directory (utenti, gruppi e contatti) dall'ambiente Active Directory locale all'infrastruttura di directory di Office 365, Azure Active Directory. Per un elenco degli strumenti disponibili e delle relative funzionalità, vedere [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) . Lo strumento consigliato è [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). Per ulteriori informazioni su Azure Active Directory Connect, vedere [integrazione delle identità locali con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).
  
Quando gli account utente vengono sincronizzati con la directory di Office 365 per la prima volta, vengono contrassegnati come non attivati. Non possono inviare o ricevere messaggi di posta elettronica e non utilizzano licenze di sottoscrizione. Quando si è pronti per assegnare gli abbonamenti di Office 365 a utenti specifici, è necessario selezionarli e attivarli [assegnando licenze agli utenti in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).
  
È inoltre possibile utilizzare [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) per assegnare le licenze. Vedere [come utilizzare PowerShell per assegnare automaticamente le licenze agli utenti di Office 365](https://go.microsoft.com/fwlink/p?LinkID=329805) per una soluzione automatizzata.