---
title: Proteggere gli account di amministratore globale di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
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
description: Protezione dell'accesso da parte dell'amministratore globale all'abbonamento a Office 365.
ms.openlocfilehash: a428f3d70e87744c33c5fb5187dc869f3b2029e1
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2019
ms.locfileid: "39814604"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>Proteggere gli account di amministratore globale di Office 365

*Questo articolo si applica sia a Office 365 Enterprise che a Microsoft 365 Enterprise*.

Le violazioni della sicurezza di un abbonamento a Office 365, incluse le informazioni sulla raccolta e gli attacchi di phishing, vengono in genere eseguite compromettendo le credenziali di un account di amministratore globale di Office 365. La sicurezza nel cloud è una partnership tra l'utente e Microsoft:
  
- I servizi cloud Microsoft sono basati su una base di attendibilità e sicurezza. Microsoft fornisce controlli e funzionalità di sicurezza che consentono di proteggere i dati e le applicazioni.
    
- Possiedi i dati e le identità e la responsabilità di proteggerli, la sicurezza delle risorse locali e la sicurezza dei componenti cloud che controlli.
    
Microsoft fornisce funzionalità che consentono di proteggere l'organizzazione, ma sono effettive solo se vengono utilizzate. Se non vengono utilizzati, potrebbe essere vulnerabile all'attacco. Per proteggere gli account di amministratore globale, Microsoft è qui per informazioni dettagliate su come eseguire le operazioni seguenti:
  
1. Creare account di amministratore globale di Office 365 dedicati e utilizzarli solo quando necessario.
    
2. Configurare l'autenticazione a più fattori per gli account di amministratore globale di Office 365 dedicati e utilizzare la forma più complessa di autenticazione secondaria.
    
> [!NOTE]
> Anche se questo articolo è concentrato sugli account di amministratore globale, è opportuno considerare se sono presenti account aggiuntivi con autorizzazioni di ampio respiro per accedere ai dati dell'abbonamento, ad esempio amministratore di eDiscovery o amministratore di sicurezza o conformità. gli account devono essere protetti nello stesso modo. 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>Passaggio 1. Creare account di amministratore globale di Office 365 dedicati e utilizzarli solo se necessario

Vi sono relativamente poche attività amministrative, ad esempio l'assegnazione di ruoli agli account utente, che richiedono privilegi di amministratore globale. Pertanto, anziché utilizzare gli account utente giornalieri a cui è stato assegnato il ruolo di amministratore globale, procedere come segue:
  
1. Determinare il set di account utente a cui è stato assegnato il ruolo di amministratore globale. È possibile eseguire questa operazione con il comando di PowerShell Active Azure (Azure AD) per l'elenco dei grafici:
  
  ```
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

2. Accedere all'abbonamento a Office 365 con un account utente a cui è stato assegnato il ruolo di amministratore globale.
    
3. Creare almeno un massimo di cinque account utente di amministratore globale dedicati. **Utilizzare password complesse con una lunghezza di almeno 12 caratteri.** Per ulteriori informazioni, vedere [creare una password complessa](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) . Archiviare le password per i nuovi account in una posizione sicura. 
    
4. Assegnare il ruolo di amministratore globale a ognuno dei nuovi account utente di amministratore globale dedicato.
    
5. Disconnettersi da Office 365.
    
6. Accedere con uno dei nuovi account utente di amministratore globale dedicati.
    
7. Per ogni account utente esistente a cui è stato assegnato il ruolo di amministratore globale dal passaggio 1:
    
  - Rimuovere il ruolo di amministratore globale.
    
  - Assegnare i ruoli di amministratore all'account appropriato per la funzione e la responsabilità del processo dell'utente. Per ulteriori informazioni sui vari ruoli di amministratore in Office 365, vedere [informazioni sui ruoli di amministratore](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles).
    
8. Disconnettersi da Office 365.
    
Il risultato deve essere:
  
- Gli unici account utente dell'abbonamento a cui è assegnato il ruolo di amministratore globale sono i nuovi account di amministratore globale dedicati. Verificarlo con il seguente comando di PowerShell:
    
  ```
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

- A tutti gli altri account utente quotidiani che gestiscono l'abbonamento sono assegnati ruoli di amministratore associati ai propri ruoli professionali.
    
Da questo momento in poi, si accede con gli account amministratore globale dedicato solo per le attività che richiedono privilegi di amministratore globale. Tutte le altre attività di amministrazione di Office 365 devono essere eseguite assegnando altri ruoli di amministrazione agli account utente.
  
> [!NOTE]
> In questo modo, è necessario eseguire ulteriori passaggi per disconnettersi come account utente giornaliero e accedere con un account di amministratore globale dedicato. Tuttavia, è necessario eseguire questa operazione solo occasionalmente per le operazioni di amministratore globale. Si consideri che il ripristino dell'abbonamento a Office 365 dopo una violazione di un account amministratore globale richiede passaggi molto più.
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>Passaggio 2. Configurare l'autenticazione a più fattori per gli account di amministratore globale di Office 365 dedicati e utilizzare la forma più complessa di autenticazione secondaria

L'autenticazione a più fattori richiede ulteriori informazioni oltre il nome e la password dell'account. Office 365 supporta questi metodi di verifica:
  
- Una telefonata
    
- Un passcode generato casualmente
    
- Una smart card virtuale o fisica
    
- Un dispositivo biometrico
    
Se si è una società di piccole dimensioni che utilizza gli account utente archiviati solo nel cloud (modello di identità solo cloud), attenersi alla procedura seguente per configurare l'utilizzo di una chiamata telefonica o di un codice di verifica del messaggio di testo inviato a uno Smart Phone:
  
1. [Configurare l'AMF](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).
    
2. [Impostare la verifica in due passaggi per Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) per configurare ogni account amministratore globale dedicato per la chiamata telefonica o il messaggio di testo come metodo di verifica. 
    
Se si è un'organizzazione più grande che utilizza un modello di identità ibrido di Office 365, sono disponibili altre opzioni di verifica. Se l'infrastruttura di sicurezza è già attiva per un metodo di autenticazione secondario più forte, attenersi alla seguente procedura:
  
1. [Configurare l'AMF](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).
    
2. [Impostare la verifica in due passaggi per Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) per configurare ogni account amministratore globale dedicato per il metodo di verifica appropriato. 
    
Se l'infrastruttura di sicurezza per il metodo di verifica più sicuro desiderato non è in esecuzione e funziona per Office 365 AMF, è consigliabile configurare gli account di amministratore globale dedicati con AMF tramite una telefonata o un messaggio di testo codice di verifica inviato a uno Smart Phone per gli account di amministratore globale come misura di sicurezza provvisoria. Non lasciare gli account di amministratore globale dedicati senza l'ulteriore protezione fornita dall'AMF.
  
Per maggiori informazioni, vedere [Pianificare l'autenticazione a più fattori per le distribuzioni di Office 365](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan)
  
Per connettersi ai servizi di Office 365 con AMF e PowerShell, vedere gli articoli seguenti:

- [Office 365 PowerShell per gli account utente, i gruppi e le licenze](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)
- [Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-by-using-mfa)
- [SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online#to-connect-with-multifactor-authentication-mfa)
- [Skype for Business online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell#connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication)

## <a name="additional-protections-for-enterprise-organizations"></a>Protezioni aggiuntive per le organizzazioni aziendali

Dopo i passaggi 1 e 2, utilizzare questi metodi aggiuntivi per verificare che l'account di amministratore globale e la configurazione eseguita con esso siano il più sicuro possibile.
  
### <a name="privileged-access-workstation"></a>Workstation con accesso privilegiato

Per garantire che l'esecuzione di attività con privilegi elevati sia la più sicura possibile, utilizzare una workstation con accesso privilegiato (PAW). La ZAMPa è un computer dedicato utilizzato solo per le attività di configurazione sensibili, ad esempio la configurazione di Office 365 che richiede un account di amministratore globale. Poiché questo computer non viene utilizzato giornalmente per la navigazione Internet o la posta elettronica, è meglio proteggerlo dagli attacchi e dalle minacce di Internet.
  
Per istruzioni su come configurare una ZAMPa, vedere [https://aka.ms/cyberpaw](https://aka.ms/cyberpaw).
  
### <a name="azure-ad-privileged-identity-management"></a>Azure AD Privileged Identity Management

Invece di avere gli account amministratore globale assegnati definitivamente al ruolo di amministratore globale, è possibile utilizzare Azure AD Privileged Identity Management (PIM) per abilitare l'assegnazione su richiesta, just-in-Time del ruolo di amministratore globale quando è necessario.
  
Gli account di amministratore globale, invece di essere amministratori permanenti, diventano amministratori idonei. Il ruolo di amministratore globale è inattivo finché non è necessario per un utente. Completare quindi un processo di attivazione per aggiungere il ruolo di amministratore globale all'account di amministratore globale per un periodo di tempo predeterminato. Quando il tempo scade, PIM rimuove il ruolo di amministratore globale dall'account di amministratore globale.
  
L'utilizzo di PIM e questo processo riduce significativamente la quantità di tempo in cui gli account di amministratore globale sono vulnerabili all'attacco e all'utilizzo da parte di utenti malintenzionati.
  
Per ulteriori informazioni, vedere [Azure ad Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).
  
> [!NOTE]
> PIM è disponibile con Azure AD Premium P2, incluso in Microsoft 365 Enterprise E5 o Enterprise Mobility + Security (EMS) E5, oppure è possibile acquistare licenze individuali per gli account di amministratore globale. 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Software di sicurezza e gestione eventi (SIEM) per la registrazione di Office 365

Il software di SIEM eseguito su un server esegue un'analisi in tempo reale degli avvisi di sicurezza e degli eventi creati dalle applicazioni e dall'hardware di rete. Per consentire al server SIEM di includere gli avvisi e gli eventi di sicurezza di Office 365 nelle sue funzioni di analisi e Reporting, integrare Azure AD in You SEIM. Vedere [Introduzione all'integrazione del registro di Azure](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).

## <a name="next-step"></a>Passaggio successivo

Se si sta impostando Identity per l'abbonamento a Office 365, vedere:

- [Identità solo cloud](cloud-only-identities.md) se si utilizza l'identità solo cloud
- [Preparare la sincronizzazione della directory](prepare-for-directory-synchronization.md) se si utilizza l'identità ibrida

  
## <a name="see-also"></a>Vedere anche

Guida di [orientamento alla sicurezza di Office 365](https://docs.microsoft.com/office365/securitycompliance/security-roadmap).
