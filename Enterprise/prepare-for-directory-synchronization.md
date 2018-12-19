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
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Viene descritto come preparare il provisioning degli utenti a Office 365 tramite la sincronizzazione delle directory e i vantaggi a lungo termine di questo metodo.
ms.openlocfilehash: 8e84f4602b79ce321cd9a71e6c35331baf40f7f0
ms.sourcegitcommit: c5761d3c41aa2d26815f0d24c73dbcd53ab37957
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2018
ms.locfileid: "27371120"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a>Preparazione per il provisioning degli utenti verso Office 365 tramite la sincronizzazione della directory

Provisioning degli utenti alla sincronizzazione della directory richiede pianificazione e preparazione rispetto alla gestione semplicemente l'account di lavoro o della scuola direttamente in Office 365 più. Le attività di pianificazione e preparazione aggiuntive sono necessari per verificare che Active Directory locale viene sincronizzata correttamente su Azure Active Directory. I vantaggi sono stati aggiunti all'organizzazione includono:
  
- Riduzione dei programmi amministrativi nell'organizzazione
- Se lo si desidera abilitare uno scenario single sign-on
- Automatizzare le modifiche dell'account in Office 365
    
Per ulteriori informazioni sui vantaggi dell'utilizzo di sincronizzazione della directory, vedere [Guida di orientamento alla sincronizzazione della Directory]( https://go.microsoft.com/fwlink/p/?LinkId=525398) e [delle identità Office 365 e Azure Active Directory](about-office-365-identity.md).
  
Per determinare lo scenario è ottimale per l'organizzazione, esaminare il [confronto tra gli strumenti di integrazione di directory](https://go.microsoft.com/fwlink/p/?LinkId=525320).
  
## <a name="directory-cleanup-tasks"></a>Attività di pulizia directory

Prima di avviare la sincronizzazione della directory, è necessario eseguire la pulizia della directory.
  
Vedere anche [gli attributi sincronizzati con Azure Active Directory per Azure Active Directory Connetti](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).
  
> [!IMPORTANT]
> Se non si esegue la pulitura directory prima della sincronizzazione, può esistere un effetto negativo significativo sul processo di distribuzione. Potrebbe richiedere giorni o persino settimane, passi attraverso il ciclo di sincronizzazione della directory, che identifica gli errori e risincronizzazione. 
  
Nella directory locale, completare le attività di pulizia seguenti:
  
1. Verificare che ogni utente a cui verranno assegnate offerte di servizio di Office 365 abbia un indirizzo di posta elettronica valido e univoco nell'attributo **proxyAddresses**. 
    
2. Rimuovere tutti i valori duplicati nell'attributo **proxyAddresses**. 
    
3.  Se possibile, verificare che ogni utente cui verrà assegnate offerte di servizi di Office 365 abbia un valore per l'attributo **userPrincipalName** valido e univoco nell'oggetto **utente** dell'utente. Per un'esperienza ottimale sincronizzazione, verificare che l'UPN di on-premise Active Directory corrispondente nel cloud UPN. Se un utente non dispone di un valore per l'attributo **userPrincipalName** , l'oggetto **utente** deve contenere un valore valido e univoco per l'attributo **sAMAccountName** . Rimuovere tutti i valori duplicati nell'attributo **userPrincipalName** . 
    
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

Sincronizzazione della directory ha esito positivo tra la directory locale e Office 365 è necessario preparare correttamente che agli attributi di directory locale. Ad esempio, è necessario assicurarsi che i caratteri specifici non vengono utilizzati in alcuni attributi che vengono sincronizzati con l'ambiente Office 365. Caratteri imprevisti non impediscono la sincronizzazione delle directory errore, ma possono restituire ad esempio un messaggio di avviso. Caratteri non validi comporterà la sincronizzazione delle directory di esito negativo.
  
La sincronizzazione delle directory avrà esito negativo anche se alcuni utenti Active Directory dispongono di uno o più attributi duplicati. Ogni utente deve disporre gli attributi univoci.
  
Gli attributi che è necessario preparare sono elencati di seguito:
  
 **Nota:** È inoltre possibile utilizzare lo [strumento IdFix](install-and-run-idfix.md) per semplificare notevolmente questo processo. 
  
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
    > Se sono presenti valori duplicati, il primo utente con il valore verrà sincronizzato. Gli utenti successivi non verranno visualizzato in Office 365. È necessario modificare il valore in Office 365 o modificare entrambi i valori nella directory locale in modo che entrambi gli utenti dalla finestra di Office 365. 
  
- **mailNickname** (alias di Exchange) 
    
  - Il valore dell'attributo non può iniziare con un punto (.).
  - Il valore dell'attributo deve essere univoco all'interno della directory.
    
- **proxyAddresses **
    
  - Attributo multivalore
  - Numero massimo di caratteri per valore: 256
  - Il valore dell'attributo non deve contenere uno spazio.
  - Il valore dell'attributo deve essere univoco all'interno della directory.
  - Caratteri non validi: \< \> (); , [ ] "
    
    Si noti che si applicano i caratteri non validi per i caratteri che seguono delimitatore tipo e ":", in modo che SMTP:User@contso.com è consentita, ma non è SMTP:user:M@contoso.com.
    
    > [!IMPORTANT]
    > Tutti gli indirizzi SMTP Simple Mail Transport Protocol () devono essere conformi agli standard di messaggistica di posta elettronica. Se gli indirizzi duplicati o esistono, vedere l' argomento della Guida [rimozione duplicati e indesiderati proxy gli indirizzi di Exchange](https://go.microsoft.com/fwlink/?LinkId=293860). 
  
- **sAMAccountName**
    
  - Numero massimo di caratteri: 20
  - Il valore dell'attributo deve essere univoco all'interno della directory.
  - Caratteri non validi: [\ "|, /: \< \> + =;? \* ]
  - Se un utente ha un attributo **sAMAccountName** non valido, ma anche un attributo **userPrincipalName** valido, l'account utente verrà creato in Office 365. 
  - Se entrambi gli **attributi sAMAccountName** e **userPrincipalName** non sono validi, è necessario aggiornarli l'attributo **userPrincipalName** di Active Directory locale. 
    
- **sn** (cognome) 
    
  - Se l'attributo è presente nell'oggetto utente, viene sincronizzato con Office 365 ma quest'ultimo non lo richiede o utilizza.
    
- **targetAddress**
    
    È necessario che l'attributo **targetAddress** (ad esempio SMTP:tom@contoso.com) popolato per l'utente deve essere inserita in Office 365 dell'elenco indirizzi globale. Negli scenari migrazione messaggistica di terze parti, ciò richiederebbe l'estensione dello schema di Office 365 per la directory locale. L'estensione dello schema di Office 365 sarebbe inoltre aggiungere gli altri attributi utili per gestire gli oggetti di Office 365 che vengono popolati utilizzando uno strumento di sincronizzazione della directory dalla directory locale. Ad esempio, viene aggiunta l'attributo **msExchHideFromAddressLists** per gestire le cassette postali nascoste o i gruppi di distribuzione. 
   
  - Numero massimo di caratteri: 256
  - Il valore dell'attributo non deve contenere uno spazio.
  - Il valore dell'attributo deve essere univoco all'interno della directory.
  - Caratteri non validi: \ \< \> (); , [ ] "
  - Tutti gli indirizzi SMTP (Simple Mail Transport Protocol) devono essere conformi agli standard di messaggistica di posta elettronica
    
- **userPrincipalName**
    
  - L'attributo **userPrincipalName** deve essere nel tipo Internet accesso formato dove il nome utente è seguito dal simbolo chiocciola (@) e un nome di dominio: ad esempio, user@contoso.com. Tutti gli indirizzi SMTP Simple Mail Transport Protocol () devono essere conformi agli standard di messaggistica di posta elettronica.
  - Il numero massimo di caratteri per l'attributo **userPrincipalName** è 113. È consentito un numero specifico di caratteri prima e dopo il simbolo di chiocciola (@), come riportato di seguito: 
  - Numero massimo di caratteri per il nome utente prima del simbolo chiocciola (@): 64
  - Numero massimo di caratteri per il nome di dominio dopo il simbolo chiocciola (@): 48
  - Caratteri non validi: \ % &amp; \* + / =? { } | \< \> ( ) ; : , [ ] "
  - Un umlaut è anche un carattere non valido.
  - Il carattere @ è necessario in ogni valore **userPrincipalName** . 
  - Il carattere @ non può essere il primo carattere in ogni valore **userPrincipalName**. 
  - Il nome utente non può terminare con un punto (.), una e commerciale (&amp;), uno spazio o un simbolo chiocciola (@).
  - Il nome utente non può contenere spazi.
  - È necessario utilizzare instradabili; ad esempio, locali o interni domini non possono essere utilizzati.
  - Unicode viene convertito in caratteri di sottolineatura.
  - **userPrincipalName** non può contenere valori duplicati nella directory. 
    
## <a name="prepare-the-userprincipalname-attribute"></a>Preparazione dell'attributo userPrincipalName

Active Directory è progettato per consentire agli utenti dell'organizzazione per accedere alla directory utilizzando **sAMAccountName** o **userPrincipalName**. Allo stesso modo, gli utenti finali possono accedere a Office 365 utilizzando il nome principale utente (UPN) del proprio lavoro o scuola account. La sincronizzazione delle directory tenta di creare nuovi utenti in Azure Active Directory utilizzando il nome principale utente stesso nella directory locale. L'UPN è formattato come un indirizzo di posta elettronica. 

In Office 365, l'UPN è l'attributo predefinito utilizzato per generare l'indirizzo di posta elettronica. È facile da ottenere **userPrincipalName** (locale e in Azure Active Directory) e l'indirizzo di posta elettronica principale in **proxyAddresses** impostati su valori diversi. Quando sono impostati su valori diversi, potrebbe essere necessario confusione per gli amministratori e utenti finali. 
  
È consigliabile allineare questi attributi in modo da ridurre la confusione. Soddisfare i requisiti di single sign-on con Active Directory Federation Services (ADFS) 2.0, è necessario verificare che l'UPN in Azure Active Directory e di Active Directory locale corrispondono e utilizza uno spazio dei nomi di dominio validi.
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a>Aggiungere un suffisso UPN alternativo AD DS

Potrebbe essere necessario aggiungere un suffisso UPN alternativo per associare le credenziali dell'utente aziendale con l'ambiente Office 365. Un suffisso UPN fa parte di un UPN a destra del carattere @. UPN utilizzati per single sign-on può contenere lettere, numeri, periodi, trattini e caratteri di sottolineatura, ma non gli altri tipi di caratteri.
  
Per ulteriori informazioni su come aggiungere un suffisso UPN alternativo ad Active Directory, vedere [Preparazione per la sincronizzazione delle directory]( https://go.microsoft.com/fwlink/p/?LinkId=525430).
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a>Corrispondenti l'UPN locale con Office 365 UPN

Se già stato configurato la sincronizzazione delle directory, UPN dell'utente per Office 365 possono non corrispondere UPN locale dell'utente che definiti nel servizio directory locale. Ciò può verificarsi quando un utente è stato assegnato una licenza prima che il dominio è stato verificato. Per risolvere questo problema, utilizzare [PowerShell per correggere UPN duplicati](https://go.microsoft.com/fwlink/p/?LinkId=396730) per aggiornare l'UPN dell'utente per verificare che l'UPN di Office 365 corrisponde al nome utente aziendale e al dominio. Se si sta aggiornando l'UPN nel servizio directory locale e come eseguire la sincronizzazione con l'identità di Azure Active Directory, è necessario rimuovere la licenza dell'utente in Office 365 prima di apportare le modifiche apportate in locale. 
  
Vedere anche [come preparare un dominio non instradabili (ad esempio domain Local) per la sincronizzazione delle directory](prepare-a-non-routable-domain-for-directory-synchronization.md).
  
## <a name="directory-integration-tools"></a>Strumenti di integrazione directory

La sincronizzazione delle directory è la sincronizzazione degli oggetti directory (utenti, gruppi e contatti) da un ambiente Active Directory locale per l'infrastruttura di directory di Office 365, Azure Active Directory. Per un elenco di strumenti disponibili e le relative funzionalità, vedere [Strumenti di integrazione di Directory](https://go.microsoft.com/fwlink/p/?LinkID=510956) . Lo strumento consigliato è [Azure Active Directory connettersi](https://go.microsoft.com/fwlink/p/?LinkID=510956). Per ulteriori informazioni sulla connessione Azure Active Directory, vedere [integrazione le identità in locale con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).
  
Quando gli account utente vengono sincronizzati con la directory di Office 365 per la prima volta, sono contrassegnati come non attivato. Non possono inviare o ricevere posta elettronica e non utilizzano licenze di sottoscrizione. Quando si è pronti per assegnare sottoscrizioni a Office 365 per utenti specifici, è necessario selezionare e attivarle da [assegnare licenze agli utenti di Office 365 per aziende](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).
  
È anche possibile utilizzare [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) per assegnare licenze. Per una soluzione automatizzata, vedere [come utilizzare PowerShell per assegnare automaticamente licenze agli utenti di Office 365](https://go.microsoft.com/fwlink/p?LinkID=329805) .