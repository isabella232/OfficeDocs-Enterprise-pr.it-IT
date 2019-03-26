---
title: Proteggere gli account di amministratore globale di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_IP
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: Proteggere l'accesso dell'amministratore globale all'abbonamento a Office 365 con questi tre passaggi.
ms.openlocfilehash: 23d47ec1f5fc4126113dd69e1ac6400d003ca41f
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573920"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>Proteggere gli account di amministratore globale di Office 365

 **Riepilogo:** Proteggere la sottoscrizione di Office 365 da attacchi basati sul compromesso di un account di amministratore globale. 
  
Le violazioni della sicurezza di un abbonamento a Office 365, incluse le informazioni sulla raccolta e gli attacchi di phishing, vengono in genere eseguite compromettendo le credenziali di un account di amministratore globale di Office 365. La sicurezza nel cloud è una partnership tra l'utente e Microsoft:
  
- I servizi cloud Microsoft sono basati su una base di attendibilità e sicurezza. Microsoft fornisce controlli e funzionalità di sicurezza che consentono di proteggere i dati e le applicazioni.
    
- Possiedi i dati e le identità e la responsabilità di proteggerli, la sicurezza delle risorse locali e la sicurezza dei componenti cloud che controlli.
    
Microsoft fornisce funzionalità che consentono di proteggere l'organizzazione, ma sono effettive solo se vengono utilizzate. Se non vengono utilizzati, potrebbe essere vulnerabile all'attacco. Per proteggere gli account di amministratore globale, Microsoft è qui per informazioni dettagliate su come eseguire le operazioni seguenti:
  
1. Creare account di amministratore globale di Office 365 dedicati e utilizzarli solo quando necessario.
    
2. Configurare l'autenticazione a più fattori per gli account di amministratore globale di Office 365 dedicati e utilizzare la forma più complessa di autenticazione secondaria.
    
3. Abilitare e configurare Office 365 cloud app Security per il monitoraggio dell'attività account amministratore globale sospetta.
    
> [!NOTE]
> Anche se questo articolo è concentrato sugli account di amministratore globale, è opportuno considerare anche se gli account aggiuntivi con autorizzazioni di vasta portata per accedere ai dati dell'abbonamento, ad esempio eDiscovery Administrator o la sicurezza o la conformità gli account di amministratore devono essere protetti nello stesso modo. 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>Passaggio 1. Creare account di amministratore globale di Office 365 dedicati e utilizzarli solo se necessario

Vi sono relativamente poche attività amministrative, ad esempio l'assegnazione di ruoli agli account utente, che richiedono privilegi di amministratore globale. Pertanto, anziché utilizzare gli account utente giornalieri a cui è stato assegnato il ruolo di amministratore globale, procedere come segue:
  
1. Determinare il set di account utente a cui è stato assegnato il ruolo di amministratore globale. È possibile eseguire questa operazione con questo comando nel prompt dei comandi del modulo di Microsoft Azure Active Directory per Windows PowerShell:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. Accedere all'abbonamento a Office 365 con un account utente a cui è stato assegnato il ruolo di amministratore globale.
    
3. Creare almeno un massimo di cinque account utente di amministratore globale dedicati. **Utilizzare password complesse con una lunghezza di almeno 12 caratteri.** Per ulteriori informazioni, vedere [creare una password complessa](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) . Archiviare le password per i nuovi account in una posizione sicura. 
    
4. Assegnare il ruolo di amministratore globale a ognuno dei nuovi account utente di amministratore globale dedicato.
    
5. DisConnettersi da Office 365.
    
6. Accedere con uno dei nuovi account utente di amministratore globale dedicati.
    
7. Per ogni account utente esistente a cui è stato assegnato il ruolo di amministratore globale dal passaggio 1:
    
  - Rimuovere il ruolo di amministratore globale.
    
  - Assegnare i ruoli di amministratore all'account appropriato per la funzione e la responsabilità del processo dell'utente. Per ulteriori informazioni sui vari ruoli di amministratore in Office 365, vedere [informazioni sui ruoli di amministratore di office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).
    
8. DisConnettersi da Office 365.
    
Il risultato deve essere:
  
- Gli unici account utente dell'abbonamento che dispongono del ruolo di amministratore globale sono il nuovo set di account di amministratore globale dedicati. Verificarlo con il seguente comando di PowerShell:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- A tutti gli altri account utente quotidiani che gestiscono l'abbonamento sono assegnati ruoli di amministratore associati ai propri ruoli professionali.
    
Da questo momento in poi, si accede con gli account amministratore globale dedicato solo per le attività che richiedono privilegi di amministratore globale. Tutte le altre attività di amministrazione di Office 365 devono essere eseguite assegnando altri ruoli di amministrazione agli account utente.
  
> [!NOTE]
> Sì, è necessario eseguire ulteriori passaggi per disconnettersi come account utente giornaliero e accedere con un account di amministratore globale dedicato. Tuttavia, è necessario eseguire questa operazione solo occasionalmente per le operazioni di amministratore globale. Si conSideri che il ripristino dell'abbonamento a Office 365 dopo una violazione di un account amministratore globale richiede passaggi molto più. 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>Passaggio 2. Configurare l'autenticazione a più fattori per gli account di amministratore globale di Office 365 dedicati e utilizzare la forma più complessa di autenticazione secondaria

L'autenticazione a più fattori per gli account di amministratore globale richiede ulteriori informazioni oltre il nome e la password dell'account. Office 365 supporta questi metodi di verifica:
  
- Una telefonata
    
- Un passcode generato casualmente
    
- Una smart card virtuale o fisica
    
- Un dispositivo biometrico
    
Se si è una società di piccole dimensioni che utilizza account utente archiviati solo nel cloud (modello di identità cloud), attenersi alla procedura seguente per configurare l'utilizzo di una chiamata telefonica o di un codice di verifica dei messaggi di testo inviati a uno Smart Phone:
  
1. [Abilitazione dell'AMF](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. [Impostare la verifica in due passaggi per Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) per configurare ogni account amministratore globale dedicato per la chiamata telefonica o il messaggio di testo come metodo di verifica. 
    
Se si è un'organizzazione più grande che utilizza un modello di identità ibrido di Office 365, sono disponibili altre opzioni di verifica. Se l'infrastruttura di sicurezza è già attiva per un metodo di autenticazione secondario più forte, attenersi alla seguente procedura:
  
1. [Abilitazione dell'AMF](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. [Impostare la verifica in due passaggi per Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) per configurare ogni account amministratore globale dedicato per il metodo di verifica appropriato. 
    
Se l'infrastruttura di sicurezza per il metodo di verifica più sicuro desiderato non è in esecuzione e funziona per Office 365 AMF, è consigliabile configurare gli account di amministratore globale dedicati con AMF tramite una telefonata o un messaggio di testo codice di verifica inviato a uno Smart Phone per gli account di amministratore globale come misura di sicurezza provvisoria. Non lasciare gli account di amministratore globale dedicati senza l'ulteriore protezione fornita dall'AMF.
  
Per maggiori informazioni, vedere [Pianificare l'autenticazione a più fattori per le distribuzioni di Office 365](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba)
  
Per connettersi ai servizi di Office 365 con AMF e PowerShell, vedere [questo articolo](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a>Passaggio 3. Monitoraggio dell'attività dell'account amministratore globale sospetto

Office 365 cloud app Security consente di creare criteri per notificare il comportamento sospetto nell'abbonamento. Cloud app Security è integrato in Office 365 E5, ma è anche disponibile come servizio separato. Ad esempio, se non si dispone di Office 365 E5, è possibile acquistare singole licenze di sicurezza delle app cloud per gli account utente a cui sono assegnati i ruoli amministratore globale, amministratore sicurezza e conformità.
  
Se si dispone di cloud app Security nell'abbonamento a Office 365, attenersi alla seguente procedura:
  
1. Accedere all'interfaccia di amministrazione di Microsoft 365 con un account a cui è stato assegnato il ruolo amministratore della sicurezza o amministratore conformità.
    
2. [Attiva la sicurezza delle app cloud di Office 365](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).
    
3. Esaminare i [criteri di rilevamento delle anomalie in Office 365 cloud app Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) per inviare una notifica tramite posta elettronica dei modelli anomali di attività amministrative privilegiate. 
    
Per aggiungere un account utente al ruolo amministratore della sicurezza, [connettersi a Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) con un account di amministratore globale dedicato e l'AMF, immettere il nome dell'entità utente dell'account utente, quindi eseguire i comandi seguenti: 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

Per aggiungere un account utente al ruolo amministratore conformità, immettere il nome dell'entità utente dell'account utente, quindi eseguire i comandi seguenti:
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a>Protezioni aggiuntive per le organizzazioni aziendali

Dopo i passaggi 1-3, utilizzare questi metodi aggiuntivi per verificare che l'account di amministratore globale e la configurazione che si esegue utilizzando l'utente siano il più sicuro possibile.
  
### <a name="privileged-access-workstation-paw"></a>Workstation con accesso privilegiato (ZAMPa)

Per garantire che l'esecuzione di attività con privilegi elevati sia la più sicura possibile, utilizzare una ZAMPa. La ZAMPa è un computer dedicato utilizzato solo per le attività di configurazione sensibili, ad esempio la configurazione di Office 365 che richiede un account di amministratore globale. Poiché questo computer non viene utilizzato giornalmente per la navigazione Internet o la posta elettronica, è meglio proteggerlo dagli attacchi e dalle minacce di Internet.
  
Per istruzioni su come configurare una ZAMPa, vedere [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).
  
### <a name="azure-ad-privileged-identity-management-pim"></a>Gestione delle identità di Azure AD Privileged Identity Management (PIM)

Invece di avere gli account di amministratore globale assegnati definitivamente al ruolo di amministratore globale, è possibile utilizzare Azure AD PIM per abilitare l'assegnazione su richiesta del ruolo di amministratore globale quando necessario.
  
Gli account di amministratore globale, invece di essere amministratori permanenti, diventano amministratori idonei. Il ruolo di amministratore globale è inattivo finché non è necessario per un utente. Completare quindi un processo di attivazione per aggiungere il ruolo di amministratore globale all'account di amministratore globale per un periodo di tempo predeterminato. Quando il tempo scade, PIM rimuove il ruolo di amministratore globale dall'account di amministratore globale.
  
L'utilizzo di PIM e questo processo riduce significativamente la quantità di tempo in cui gli account di amministratore globale sono vulnerabili all'attacco e all'utilizzo da parte di utenti malintenzionati.
  
Per ulteriori informazioni, vedere [Configure Azure ad privilegEd Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).
  
> [!NOTE]
> PIM è disponibile con Azure Active Directory Premium P2, incluso in Enterprise Mobility + Security (EMS) E5, oppure è possibile acquistare licenze individuali per gli account di amministratore globale. 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Software di sicurezza e gestione eventi (SIEM) per la registrazione di Office 365

Il software di SIEM eseguito su un server esegue un'analisi in tempo reale degli avvisi di sicurezza e degli eventi creati dalle applicazioni e dall'hardware di rete. Per consentire al server SIEM di includere gli eventi e gli avvisi di sicurezza di Office 365 nelle relative funzioni di analisi e Reporting, integrarle nel sistema SIEM:
  
- Azure AD
    
    Per ulteriori informazioni, vedere [integrare i log dalle risorse di Azure nei sistemi Siem](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).
    
- Office 365 Cloud App Security
    
    Per ulteriori informazioni, vedere [integrare il server Siem con Office 365 cloud app Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).
    
## <a name="next-step"></a>Passaggio successivo

Vedere [procedure consigliate per la sicurezza per Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).
  

