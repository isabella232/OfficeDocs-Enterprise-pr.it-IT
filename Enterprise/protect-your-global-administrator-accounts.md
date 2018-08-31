---
title: Proteggere gli account di amministrazione globale di Office 365.
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
description: Proteggere l'accesso di amministratore globale per la sottoscrizione a Office 365 con i tre passaggi successivi.
ms.openlocfilehash: 7260e903ea007735c87ab8aa826e3b97e7bd28c1
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541370"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>Proteggere gli account di amministrazione globale di Office 365.

 **Riepilogo:** Impedisce la sottoscrizione a Office 365 attacchi in violazione di un account amministratore globale. 
  
Violazioni della protezione di una sottoscrizione a Office 365, tra cui la raccolta di informazioni e phishing e sono in genere eseguita da compromettere le credenziali dell'account amministratore globale di Office 365. Sicurezza nel cloud è una relazione tra l'utente e Microsoft:
  
- Servizi cloud Microsoft parti basati su una base di sicurezza e attendibilità. Microsoft fornisce funzionalità che consentono di proteggere i dati e le applicazioni e controlli di sicurezza.
    
- Si è proprietari dei dati e le identità e la responsabilità per la protezione di essi, la sicurezza delle risorse locali e la sicurezza dei componenti cloud che è possibile controllare.
    
Microsoft offre funzionalità che consentono di proteggere l'organizzazione, ma è effettiva solo se si utilizza. Se non si utilizza tali, potrebbe essere vulnerabile ad attacchi. Per proteggere gli account di amministratore globale, Microsoft è seguito con istruzioni dettagliate per informazioni su:
  
1. Creare gli account amministratore globale di Office 365 dedicati e utilizzarli solo quando necessario.
    
2. Configurare l'autenticazione a più fattori per gli account di amministratore globale di Office 365 dedicati e utilizzare il modulo più sicuro dell'autenticazione secondario.
    
3. Abilitare e configurare la sicurezza di Office 365 Cloud App da monitorare per attività dell'account amministratore globale potenzialmente dannoso.
    
> [!NOTE]
> Benché questo articolo viene trattata principalmente l'account amministratore globale, è necessario considerare anche se altri account con autorizzazioni ampie per accedere ai dati in abbonamento, ad esempio eDiscovery amministratore o conformità o sicurezza account amministratore, devono essere protette nello stesso modo. 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>Passaggio 1. Creare gli account amministratore globale di Office 365 dedicati e utilizzarli solo quando necessario

Esistono relativamente poche attività di amministrazione, ad esempio l'assegnazione di ruoli agli account utente, che richiedono i privilegi di amministratore globale. Pertanto, anziché utilizzare gli account utente quotidiane che sono stati assegnati il ruolo amministratore globale, eseguire la procedura seguente:
  
1. Determinare il set di account utente che è stato assegnato il ruolo amministratore globale. È possibile farlo con questo comando al prompt dei comandi di Microsoft Azure Active Directory Module per Windows PowerShell:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. Accedere alla sottoscrizione a Office 365 con un account utente che è stato assegnato il ruolo amministratore globale.
    
3. Creare almeno uno e fino a un massimo di cinque dedicata gli account utente amministratore globale. **Utilizzare password complesse almeno 12 caratteri lungo** Per ulteriori informazioni, vedere [creare una password complessa](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) . Memorizzare le password per i nuovi account in un luogo sicuro. 
    
4. Assegnare il ruolo amministratore globale per ognuno degli account utente amministratore globale nuovo dedicato.
    
5. Disconnettersi da Office 365.
    
6. Accedere con uno dei nuovi account utente amministratore globale dedicato.
    
7. Per ogni account utente che era stato assegnato il ruolo amministratore globale nel passaggio 1:
    
  - Rimuovere il ruolo amministratore globale.
    
  - Assegnare ruoli amministratore per l'account appropriati per la funzione e responsabilità dell'utente. Per ulteriori informazioni sui diversi ruoli di amministratore in Office 365, vedere [ruoli di amministratore su Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).
    
8. Disconnettersi da Office 365.
    
Il risultato dovrebbe essere:
  
- Gli account utente solo dell'abbonamento con il ruolo amministratore globale sono il nuovo set di account di amministratore globale dedicato. Eseguire questa verifica con il comando PowerShell seguente:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- A tutti gli altri account utente quotidiani che gestiscono l'abbonamento sono assegnati ruoli di amministratore associati ai propri ruoli professionali.
    
Dal momento in poi, si accede con gli account di amministratore globale dedicati solo per le attività che richiedono i privilegi di amministratore globale. Tutte le altre attività amministrative di Office 365 deve essere eseguita mediante l'assegnazione di altri ruoli di amministrazione per gli account utente.
  
> [!NOTE]
> Sì, si richiede passaggi aggiuntivi per disconnettersi come account utente quotidiane e accedere con un account amministratore globale dedicato. Ma questo deve essere eseguita occasionalmente per le operazioni di amministratore globale. È consigliabile che ripristino la sottoscrizione a Office 365 dopo una violazione di account amministratore globale richiede molto più passaggi. 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>Passaggio 2. Configurare l'autenticazione a più fattori per gli account di amministratore globale di Office 365 dedicati e utilizzare il modulo più sicuro dell'autenticazione secondaria

L'autenticazione a più fattori (MFA) per gli account di amministratore globale richiede informazioni aggiuntive oltre il nome dell'account e la password. Office 365 supporta questi metodi di verifica:
  
- Una chiamata telefonica
    
- Un passcode generato casualmente
    
- Una smart card (virtuali o fisiche)
    
- Un dispositivo biometrico
    
Se si è un'azienda di piccole dimensioni che utilizza gli account utente archiviati solo nel cloud (modello di identità cloud), utilizzare la procedura seguente per configurare tramite una chiamata telefonica o un codice di verifica messaggi di testo inviato a un telefono smart MFA:
  
1. [Abilitare MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. [Impostare la verifica passaggio 2 per Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) per configurare ciascun dedicata account amministratore globale per la chiamata telefonica o messaggio di testo come il metodo di verifica. 
    
Se si è un'organizzazione più ampia che utilizza un modello di identità ibrido di Office 365, sono disponibili ulteriori opzioni di verifica. Se si dispone già dell'infrastruttura di protezione sul posto di un metodo di autenticazione secondario più affidabile, utilizzare la procedura seguente:
  
1. [Abilitare MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. [Impostare la verifica passaggio 2 per Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) per configurare ciascun dedicata account amministratore globale per il metodo di verifica appropriati. 
    
Se l'infrastruttura di protezione per il metodo di verifica più affidabile desiderato non è disponibile in locale e sul funzionamento di Office 365 MFA, è consigliabile configurare gli account di amministratore globale dedicato con MFA tramite una chiamata telefonica o un messaggio di testo codice di verifica inviato a un telefono smart per gli account di amministratore globale come misura di sicurezza provvisorio. Non lasciare gli account di amministratore globale dedicato senza la protezione aggiuntiva fornita da MFA.
  
Per maggiori informazioni, vedere [Pianificare l'autenticazione a più fattori per le distribuzioni di Office 365](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba)
  
Per connettersi a servizi di Office 365 con MFA e PowerShell, vedere [questo articolo](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a>Passaggio 3. Monitorare l'attività account amministratore globale sospetti

Protezione di Office 365 Cloud App consente di creare i criteri per informare l'utente di comportamento potenzialmente dannoso in abbonamento. Cloud App protezione incorporata in Office 365 E5, ma è disponibile anche come servizio separato. Ad esempio, se non si dispone di Office 365 E5, è possibile acquistare singole licenze di protezione di applicazione Cloud per gli account utente assegnati l'amministratore globale, amministratore della sicurezza e ruoli di amministratore di conformità.
  
Se si dispone di protezione App Cloud nella sottoscrizione a Office 365, utilizzare la procedura seguente:
  
1. Accedere al portale di Office 365 con un account viene assegnato il ruolo di amministratore di conformità o sicurezza.
    
2. [Attivare la protezione di Office 365 Cloud App](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).
    
3. Esaminare i [criteri di rilevamento anomalia in sicurezza App Cloud di Office 365](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) per informare l'utente tramite posta elettronica di modelli anomali dell'attività di amministrazione con privilegi. 
    
Per aggiungere un account utente al ruolo di amministratore della sicurezza, [connettersi a Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) con un account amministratore globale dedicato e MFA, immettere il nome dell'entità utente dell'account utente e quindi eseguire questi comandi: 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

Per aggiungere un account utente per il ruolo di amministratore di conformità, immettere il nome dell'entità utente dell'account utente e quindi eseguire questi comandi:
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a>Altri tipi di protezione per le organizzazioni aziendali

Dopo aver passaggi da 1 a 3, utilizzare questi metodi aggiuntivi per verificare che l'account amministratore globale e la configurazione da eseguire utilizzarlo, sono la massima protezione.
  
### <a name="privileged-access-workstation-paw"></a>Workstation con privilegi di accesso (IMPRONTE)

Per verificare che l'esecuzione delle attività con privilegi elevati sia la massima protezione, utilizzare un'IMPRONTE. Un IMPRONTE è un computer dedicato che viene utilizzato solo per le attività di configurazione riservati, ad esempio la configurazione di Office 365 che richiede un account amministratore globale. Dal momento che il computer non viene utilizzato ogni giorno per l'esplorazione di Internet o di posta elettronica, è più protetto da minacce e gli attacchi via Internet.
  
Per istruzioni su come impostare un'IMPRONTE, vedere [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).
  
### <a name="azure-ad-privileged-identity-management-pim"></a>Gestione delle identità con privilegi di Azure Active Directory (personali)

Anziché gli account di amministratore globale in modo permanente assegnato il ruolo amministratore globale, è possibile utilizzare Azure Active Directory personali per consentire l'assegnazione di ruolo amministratore globale su richiesta, -in-time quando necessario.
  
Anziché gli account di amministratore globale da un amministratore permanente, questi diventano idonei agli amministratori. Il ruolo amministratore globale è inattivo fino a quando un utente deve. È quindi possibile completare il processo di attivazione per aggiungere il ruolo amministratore globale per l'account amministratore globale per un periodo di tempo predefinito. Se il tempo di scadenza, personali rimuove il ruolo amministratore globale da account amministratore globale.
  
Utilizzo di personali e questo processo riduce in modo significativo il periodo di tempo che l'account amministratore globale sono vulnerabili ad attacchi e utilizzare da utenti malintenzionati.
  
Per ulteriori informazioni, vedere [gestione delle identità configurare Azure Active Directory privilegiato](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).
  
> [!NOTE]
> Personali sono disponibile con Azure Active Directory Premium P2, che è incluso mobilità aziendale + E5 di sicurezza (EMS), oppure è possibile acquistare licenze individuali per gli account di amministratore globale. 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Sicurezza informazioni ed eventi (SIEM) il software di gestione per la registrazione di Office 365

Software SIEM eseguito su un server esegue l'analisi in tempo reale di avvisi di protezione e gli eventi creati dalle applicazioni e hardware di rete. Per consentire il server SIEM includere gli avvisi di protezione di Office 365 ed eventi dell'analisi e reporting funzioni, integrare queste SIEM nel sistema in uso:
  
- Azure AD
    
    Per ulteriori informazioni, vedere [integrazione registri Azure risorse nei sistemi del cliente SIEM](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).
    
- Office 365 Cloud App Security
    
    Per ulteriori informazioni, vedere [integrazione con Office 365 Cloud App Security sul server SIEM](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).
    
## <a name="next-step"></a>Passaggio successivo

Vedere [le procedure consigliate per Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).
  

