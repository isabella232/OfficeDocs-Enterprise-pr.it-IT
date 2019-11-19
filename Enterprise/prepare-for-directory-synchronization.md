---
title: Preparare la sincronizzazione della directory a Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/18/2019
audience: Admin
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
ms.openlocfilehash: 22db70d659d74e6d0f37f54a7743a562f220565d
ms.sourcegitcommit: 23c8781d1a2b0472612c3a2cb6e5d13edb03e236
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2019
ms.locfileid: "38702237"
---
# <a name="prepare-for-directory-synchronization-to-office-365"></a>Preparare la sincronizzazione della directory a Office 365

I vantaggi dell'identità ibrida e della sincronizzazione della directory dell'organizzazione includono:
  
- Riduzione dei programmi amministrativi nell'organizzazione
- Opzione che consente di abilitare lo scenario Single Sign-on
- Automatizzare le modifiche dell'account in Office 365
    
Per ulteriori informazioni sui vantaggi derivanti dall'utilizzo della sincronizzazione della directory, vedere [Directory Synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Hybrid identity for Office 365](plan-for-directory-synchronization.md).

Tuttavia, la sincronizzazione della directory richiede la pianificazione e la preparazione per garantire che i servizi di dominio Active Directory vengano sincronizzati con il tenant di Azure Active Directory (Azure AD) dell'abbonamento a Office 365 con un minimo di errori. 

Seguire questi passaggi per ottenere risultati ottimali.
  
## <a name="1-directory-cleanup-tasks"></a>1. attività di pulizia della directory

Prima di sincronizzare servizi di dominio Active Directory con il tenant di Azure AD, è necessario eseguire la pulizia di servizi di dominio Active Directory.

> [!IMPORTANT]
> Se non si esegue la pulizia di servizi di dominio Active Directory prima di eseguire la sincronizzazione, il processo di distribuzione può avere un effetto negativo significativo. Potrebbero essere necessari giorni o persino settimane per eseguire il ciclo di sincronizzazione della directory, l'identificazione dei relativi errori e la ripetizione della sincronizzazione. 
  
In servizi di dominio Active Directory, completare le seguenti attività di pulizia per ogni account utente a cui viene assegnata una licenza di Office 365:
  
1. Verificare l'indirizzo di posta elettronica valido e univoco nell'attributo **proxyAddresses** . 

  >[!Note]
  >Un carattere tilde (~) negli indirizzi di posta elettronica verrà ignorato. Ciò può comportare errori di sincronizzazione della directory falsi positivi relativi a proxyAddresses duplicati.
    
2. Rimuovere tutti i valori duplicati nell'attributo **proxyAddresses**. 
    
3.  Se possibile, garantire un valore valido e univoco per l'attributo **userPrincipalName** nell'oggetto **utente** dell'utente. Per un'esperienza di sincronizzazione ottimale, verificare che l'UPN di servizi di dominio Active Directory corrisponda all'UPN di Azure AD. Se un utente non dispone di un valore per l'attributo **userPrincipalName**, l'oggetto **user** deve contenere un valore univoco e valido per l'attributo **sAMAccountName**. Rimuovere tutti i valori duplicati nell'attributo **userPrincipalName**. 
    
4. Per un utilizzo ottimale dell'elenco indirizzi globale (GAL, Global Address List), assicurarsi che le informazioni contenute nei seguenti attributi dell'account utente di servizi di dominio Active Directory siano corrette:
    
  - givenName
  - Cognome
  - displayName
  - Professione
  - Reparto
  - Ufficio
  - Telefono ufficio
  - Cellulare
  - Numero fax
  - Via e numero civico
  - Città
  - Stato o provincia
  - CAP
  - Paese
    
## <a name="2-directory-object-and-attribute-preparation"></a>2. la preparazione degli attributi e degli oggetti directory

La corretta sincronizzazione della directory tra il servizio AD DS e Office 365 richiede la corretta preparazione degli attributi di AD DS. Ad esempio, è necessario assicurarsi che i caratteri specifici non vengano utilizzati in alcuni attributi sincronizzati con l'ambiente Office 365. I caratteri imprevisti non determinano il failover della sincronizzazione della directory ma potrebbero restituire un avviso. I caratteri non validi sono responsabili dell'esito negativo della sincronizzazione della directory.
  
La sincronizzazione della directory avrà esito negativo anche se alcuni degli utenti di AD DS dispongono di uno o più attributi duplicati. Ogni utente deve disporre di attributi univoci.
  
Gli attributi necessari per la preparazione sono elencati di seguito:
  
- **displayName**
    
  - Se l'attributo è presente nell'oggetto utente, verrà sincronizzato con Office 365.
  - A un attributo presente nell'oggetto utente deve corrispondere un valore. Ovvero, l'attributo non deve essere vuoto.
  - Numero massimo di caratteri: 256
    
- **givenName**
    
  - Se l'attributo è presente nell'oggetto utente, viene sincronizzato con Office 365 ma quest'ultimo non lo richiede o utilizza.
  - Numero massimo di caratteri: 64
    
- **posta elettronica**
    
  - Il valore dell'attributo deve essere univoco all'interno della directory.
    
    > [!NOTE]
    > Se sono presenti valori duplicati, il primo utente con il valore è sincronizzato. Gli utenti successivi non verranno visualizzati in Office 365. È necessario modificare il valore di Office 365 o modificare entrambi i valori in servizi di dominio Active Directory per consentire la visualizzazione di entrambi gli utenti in Office 365. 
  
- **mailNickname** (alias di Exchange) 
    
  - Il valore dell'attributo non può iniziare con un punto (.).
  - Il valore dell'attributo deve essere univoco all'interno della directory.
    
- **proxyAddresses**
    
  - Attributo con più valori
  - Numero massimo di caratteri per valore: 256
  - Il valore dell'attributo non deve contenere uno spazio.
  - Il valore dell'attributo deve essere univoco all'interno della directory.
  - Caratteri non validi \< \> : (); , [ ] " '
    
    Si noti che i caratteri non validi si applicano ai caratteri che seguono il delimitatore di tipo e ":", in modo che SMTP:User@contso.com sia consentita, ma SMTP:user:M@contoso.com non lo è.
    
    > [!IMPORTANT]
    > Tutti gli indirizzi SMTP (Simple Mail Transport Protocol) devono essere conformi agli standard di messaggistica di posta elettronica Se esistono indirizzi duplicati o indesiderati, vedere l'argomento della Guida relativo alla [rimozione di indirizzi proxy duplicati e indesiderati in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860). 
  
- **sAMAccountName**
    
  - Numero massimo di caratteri: 20
  - Il valore dell'attributo deve essere univoco all'interno della directory.
  - Caratteri non validi: [\ "|,/ \< \> : + =;? \* ']
  - Se un utente ha un attributo **sAMAccountName** non valido, ma anche un attributo **userPrincipalName** valido, l'account utente verrà creato in Office 365. 
  - Se **sAMAccountName** e **userPrincipalName** non sono validi, è necessario aggiornare l'attributo **userPrincipalName** di servizi di dominio Active Directory. 
    
- **sn** (cognome) 
    
  - Se l'attributo è presente nell'oggetto utente, viene sincronizzato con Office 365 ma quest'ultimo non lo richiede o utilizza.
    
- **targetAddress**
    
    È necessario che l'attributo **targetAddress** , ad esempio SMTP:Tom@contoso.com, popolato per l'utente, venga visualizzato nell'elenco indirizzi globale di Office 365. Negli scenari di migrazione della messaggistica di terze parti, è necessaria l'estensione dello schema di Office 365 per servizi di dominio Active Directory. L'estensione dello schema di Office 365 aggiungerà anche altri attributi utili per la gestione degli oggetti di Office 365 che vengono popolati tramite uno strumento di sincronizzazione della directory da AD DS. Verrebbe ad esempio aggiunto l'attributo **msExchHideFromAddressLists** per gestire i gruppi di distribuzione o le cassette postali nascoste. 
   
  - Numero massimo di caratteri: 256
  - Il valore dell'attributo non deve contenere uno spazio.
  - Il valore dell'attributo deve essere univoco all'interno della directory.
  - Caratteri non validi: \< \> \ (); , [ ] "
  - Tutti gli indirizzi SMTP (Simple Mail Transport Protocol) devono essere conformi agli standard di messaggistica di posta elettronica
    
- **userPrincipalName**
    
  - L'attributo **userPrincipalName** deve trovarsi nel formato di accesso di tipo Internet, in cui il nome utente è seguito dal segno di chiocciola (@) e dal nome di dominio: ad esempio, user@contoso.com. Tutti gli indirizzi SMTP (Simple Mail Transport Protocol) devono essere conformi agli standard di messaggistica di posta elettronica
  - Il numero massimo di caratteri per l'attributo **userPrincipalName** è 113. È consentito un numero specifico di caratteri prima e dopo il simbolo di chiocciola (@), come riportato di seguito: 
  - Numero massimo di caratteri per il nome utente che si trova di fronte al segno di chiocciola (@): 64
  - Numero massimo di caratteri per il nome di dominio dopo il simbolo chiocciola (@): 48
  - Caratteri non validi: \ &amp; \* % +/=? { } | \< \> ( ) ; : , [ ] " '
  - Anche la dieresi è un carattere non valido.
  - Il carattere @ è necessario in ogni valore **userPrincipalName**. 
  - Il carattere @ non può essere il primo carattere in ogni valore **userPrincipalName**. 
  - Il nome utente non può terminare con un punto (.), una&amp;e commerciale (), uno spazio o un segno di chiocciola (@).
  - Il nome utente non può contenere spazi.
  - I domini instradabili devono essere utilizzati. ad esempio, non è possibile utilizzare i domini locali o interni.
  - Unicode viene convertito in caratteri di sottolineatura.
  - **userPrincipalName** non può contenere valori duplicati nella directory. 

Vedere [preparare gli attributi della directory con lo strumento IdFix](prepare-directory-attributes-for-synch-with-idfix.md) per utilizzare lo strumento IdFix per identificare gli errori negli attributi di ad DS.
    
## <a name="3-prepare-the-userprincipalname-attribute"></a>3. preparare l'attributo userPrincipalName

Active Directory è stato creato per consentire agli utenti finali dell'organizzazione di accedere alla directory tramite **sAMAccountName** o **userPrincipalName**. Analogamente, gli utenti finali possono accedere a Office 365 utilizzando il nome dell'entità utente (UPN) dell'account aziendale o dell'Istituto di istruzione. La sincronizzazione della directory tenta di creare nuovi utenti in Azure Active Directory utilizzando lo stesso UPN presente in servizi di dominio Active copia. L'UPN viene formattato come un indirizzo di posta elettronica. 

In Office 365, l'UPN è l'attributo predefinito utilizzato per generare l'indirizzo di posta elettronica. È facile ottenere **userPrincipalName** (in servizi di dominio Active Directory e in Azure ad) e l'indirizzo di posta elettronica principale in **proxyAddresses** impostato su valori diversi. Quando sono impostati su valori diversi, possono generare confusione per amministratori e utenti finali. 
  
È consigliabile allineare questi attributi per ridurre la confusione. Per soddisfare i requisiti del servizio Single Sign-on con Active Directory Federation Services (AD FS) 2,0, è necessario assicurarsi che UPN in Azure Active Directory e la corrispondenza di AD DS e utilizzino uno spazio dei nomi di dominio valido.
  
## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a>4. aggiungere un suffisso UPN alternativo a servizi di dominio Active Directory

Potrebbe essere necessario aggiungere un suffisso UPN alternativo per associare le credenziali aziendali dell'utente all'ambiente Office 365. Il suffisso UPN è la parte di un UPN che si trova a destra del carattere @. Gli UPN utilizzati per Single Sign-On possono includere lettere, numeri, punti, trattini e caratteri di sottolineatura, ma nessun altro tipo di carattere.
  
Per ulteriori informazioni su come aggiungere un suffisso UPN alternativo ad Active Directory, vedere [Prepare for Directory Synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).
  
## <a name="5-match-the-ad-ds-upn-with-the-office-365-upn"></a>5. corrispondere all'UPN di servizi di dominio Active Directory con l'UPN di Office 365

Se è già stata configurata la sincronizzazione della directory, l'UPN dell'utente per Office 365 potrebbe non corrispondere all'UPN di servizi di dominio utente di AD DS definito in AD DS. Questa situazione può verificarsi quando a un utente viene assegnata una licenza prima della verifica del dominio. Per risolvere questo risultato, utilizzare [PowerShell per correggere l'UPN duplicato](https://go.microsoft.com/fwlink/p/?LinkId=396730) per aggiornare l'UPN dell'utente per verificare che l'UPN di Office 365 corrisponda al nome utente aziendale e al dominio. Se si esegue l'aggiornamento dell'UPN in servizi di dominio Active Directory e si desidera che venga sincronizzato con l'identità di Azure, è necessario rimuovere la licenza dell'utente in Office 365 prima di apportare le modifiche in AD DS. 
  
Vedere anche [come preparare un dominio non instradabile (ad esempio, dominio locale) per la sincronizzazione della directory](prepare-a-non-routable-domain-for-directory-synchronization.md).


## <a name="next-steps"></a>Passaggi successivi

Vedere [Prepare Directory Attributes with the IdFix Tool](prepare-directory-attributes-for-synch-with-idfix.md) per correggere gli errori negli attributi di ad DS prima della sincronizzazione della directory.

Se sono stati corretti tutti gli errori degli attributi identificati con lo strumento IdFix e sono stati eseguiti i passaggi da 1 a 5, vedere [configurare la sincronizzazione della directory](set-up-directory-synchronization.md).
