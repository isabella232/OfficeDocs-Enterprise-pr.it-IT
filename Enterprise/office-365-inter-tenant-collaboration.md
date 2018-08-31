---
title: Collaborazione tra tenant di Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/28/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
description: Informazioni sul funzionamento di Office 365 collaborazione tra tenant e organizzazioni.
ms.openlocfilehash: 932c837f9dc09dd0469a17ad4e6a05f09966d29c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541181"
---
# <a name="office-365-inter-tenant-collaboration"></a>Collaborazione tra tenant di Office 365

In questo articolo vengono descritti diversi modi per collaborare tra due tenant di Office 365. È destinato agli amministratori di Office 365.
  
Si supponga che le due organizzazioni Fabrikam e Contoso, avere un tenant business di Office 365 e desidera collaborare a progetti diversi. alcuni dei quali eseguire per un periodo limitato e alcuni dei quali è in corso. Come Fabrikam e Contoso abilitare le persone e team di collaborare in modo più efficace tra i diversi tenant di Office 365 in modo sicuro? Office 365, in combinazione con Azure Active Directory B2B collaborazione, sono disponibili diverse opzioni. In questo articolo vengono descritti diversi scenari principali che possono prendere in considerazione Fabrikam e Contoso.
  
Opzioni di collaborazione tra tenant Office 365 includono l'utilizzo di una posizione centralizzata per file e le conversazioni, condivisione di calendari, utilizzo della messaggistica Istantanea, chiamate audio/video per la comunicazione e la protezione dell'accesso alle risorse e applicazioni. Utilizzare le tabelle seguenti per selezionare soluzioni e ulteriori informazioni.
  
## <a name="exchange-online-collaboration-options"></a>Opzioni di collaborazione in linea di Exchange

|**Obiettivo di condivisione**|**Azione amministrativa**|**Informazioni sulle procedure**|
|:-----|:-----|:-----|
|Condividere i calendari con un'altra organizzazione di Office 365  <br/> |Gli amministratori possono configurare diversi livelli di accesso al calendario di Exchange Online per consentire alle aziende di collaborare con altre aziende e per consentire agli utenti di condividere le pianificazioni (informazioni sulla disponibilità) con altri utenti  <br/> |[Condivisione in Exchange Online](https://technet.microsoft.com/en-us/library/jj916670%28v=exchg.150%29.aspx) <br/> [Relazioni dell'organizzazione in Exchange Online](https://technet.microsoft.com/en-us/library/jj916658%28v=exchg.150%29.aspx) <br/> [Creare una relazione dell'organizzazione in Exchange Online](https://technet.microsoft.com/en-us/library/jj916671%28v=exchg.150%29.aspx) <br/> [Modificare e relazione dell'organizzazione in Exchange Online](https://technet.microsoft.com/en-us/library/jj916659%28v=exchg.150%29.aspx) <br/> [Rimuovere una relazione dell'organizzazione in Exchange Online](https://technet.microsoft.com/en-us/library/jj916657%28v=exchg.150%29.aspx) <br/> [Condividere i calendari con utenti esterni](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) <br/> |
|Controllare come utenti condividono i calendari con utenti esterni all'organizzazione  <br/> |Gli amministratori di applicano criteri di condivisione alle cassette postali degli utenti per controllare gli utenti che possono essere condivise con e il livello di accesso concesso  <br/> |[Condivisione criteri in Exchange Online](https://technet.microsoft.com/en-us/library/jj916673%28v=exchg.150%29.aspx) <br/> [Creare un criterio di condivisione in Exchange Online](https://technet.microsoft.com/en-us/library/jj916676%28v=exchg.150%29.aspx) <br/> [Applicare un criterio di condivisione alle cassette postali in Exchange Online](https://technet.microsoft.com/en-us/library/jj916672%28v=exchg.150%29.aspx) <br/> [Modificare, disabilitare o rimuovere un criterio di condivisione in Exchange Online](https://technet.microsoft.com/en-us/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|Configurare i canali di posta elettronica protetta e controllare il flusso di posta elettronica con organizzazioni partner  <br/> |Gli amministratori di creare connettori per applicare la protezione per gli scambi di posta elettronica con un'organizzazione partner provider di servizi. I connettori di applicare la crittografia tramite (TLS) transport layer security e consentendo restrizioni nomi di dominio o la posta elettronica Invia partner da gli intervalli di indirizzi IP.  <br/> |[Come viene utilizzato il TLS (Transport Layer Security) per proteggere il traffico della posta elettronica in Office 365](https://technet.microsoft.com/en-us/library/mt163898.aspx) <br/> [Configure mail flow using connectors in Office 365](https://technet.microsoft.com/en-us/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [Domini remoti in Exchange Online](https://technet.microsoft.com/en-us/library/jj966211%28v=exchg.150%29.aspx) <br/> [Configurare il connettore per il flusso della posta protetto con un'organizzazione partner](https://technet.microsoft.com/en-us/library/dn751021%28v=exchg.150%29.aspx) <br/> [Procedure consigliate di flusso di posta per Exchange Online e Office 365 (panoramica)](https://technet.microsoft.com/en-us/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint Online e OneDrive per le opzioni di collaborazione aziendale

|**Gli obiettivi di condivisione**|**Azione amministrativa**|**Informazioni sulle procedure**|
|:-----|:-----|:-----|
|Condividi siti e documenti con utenti esterni  <br/> |Gli amministratori di configurare la condivisione in tenant o livello di raccolta siti per l'account Microsoft autenticati, ufficio o scuola per gli account account autenticati o guest  <br/> |
  [Gestire la condivisione esterna per l'ambiente di SharePoint Online](https://support.office.com/en-US/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> [Domini con restrizioni di condivisione in Office 365 in SharePoint Online e OneDrive for Business](https://support.office.com/en-US/article/Restricted-Domains-Sharing-in-Office-365-SharePoint-Online-and-OneDrive-for-Business-5d7589cd-0997-4a00-a2ba-2320ec49c4e9) <br/> [Utilizzare SharePoint Online come soluzione extranet business to business (B2B)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|Gestione e del controllo condivisione esterna per gli utenti finali  <br/> |OneDrive per i proprietari dei file di Business e gli utenti finali di SharePoint Online configurare i siti e la condivisione di documenti e stabilire le notifiche per tenere traccia di condivisione  <br/> |[Configurazione delle notifiche di condivisione esterna per OneDrive for Business](https://support.office.com/en-US/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [Condividere file o cartelle di SharePoint in Office 365](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a>Skype per le opzioni di collaborazione aziendale

|**Obiettivo di condivisione**|**Azione amministrativa**|**Informazioni sulle procedure**|
|:-----|:-----|:-----|
|Skype per Online Business - messaggistica Istantanea, chiamate e presenza con altri Skype per gli utenti aziendali  <br/> |Gli amministratori possono consentire loro Skype per gli utenti aziendali Online per messaggistica immediata, effettuare chiamate audio/video e verificare la presenza con utenti in un altro tenant di Office 365.  <br/> |[Consentire agli utenti di contatti esterni Skype per gli utenti aziendali](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|Skype per Online Business - messaggistica Istantanea, chiamate e presenza con utenti Skype (consumer)  <br/> |Gli amministratori possono consentire loro Skype per gli utenti aziendali Online per messaggistica immediata, effettuare chiamate e verificare la presenza con utenti Skype (consumer).  <br/> |[Consentire Skype per gli utenti aziendali di aggiungere contatti Skype](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a>Opzioni di Azure Active Directory B2B collaborazione

|**Obiettivo di condivisione**|**Azione amministrativa**|**Informazioni sulle procedure**|
|:-----|:-----|:-----|
|Azure Active Directory B2B collaborazione - la condivisione tramite l'aggiunta di utenti esterni a un gruppo nell'elenco dell'organizzazione di contenuto  <br/> |Un amministratore globale per un tenant di Office 365 può invitare le persone in un altro tenant di Office 365 per unire le directory, aggiungere gli utenti esterni a un gruppo e concedere l'accesso al contenuto, ad esempio siti di SharePoint e raccolte per il gruppo.  <br/> |[Che cos'è l'anteprima di collaborazione di Azure Active Directory B2B?](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [Azure Active Directory B2B: Nuovi aggiornamenti semplificano la collaborazione tra business](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [Condivisione esterna di Office 365 e Azure Active Directory B2B collaborazione](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [Azure Active Directory B2B collaborazione API e la personalizzazione](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-api) <br/> [Azure Active Directory e identità Mostra: collaborazione Azure Active Directory B2B (Business to Business](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="office-365-collaboration-options"></a>Opzioni di collaborazione di Office 365

|**Obiettivo di condivisione**|**Azione amministrativa**|**Informazioni sulle procedure**|
|:-----|:-----|:-----|
|Gruppi di Office 365 - posta elettronica, calendario, OneNote e file condivisi in una posizione centrale  <br/> |I gruppi sono supportati in Essentials Business, Business Premium, formazione e i piani Enterprise E1, E3 ed E5. Utenti in un tenant di Office 365 possono creare un gruppo e invitare persone in un altro tenant di Office 365 come utenti guest. Si applica anche a Dynamics CRM.  <br/> |[Informazioni sui gruppi di Office 365](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [Accesso guest in gruppi di Office 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [Distribuire Office 365 gruppi](https://technet.microsoft.com/en-us/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a>Opzioni di collaborazione di Yammer

|**Obiettivo di condivisione**|**Azione amministrativa**|**Informazioni sulle procedure**|
|:-----|:-----|:-----|
|Yammer - collaborazione tramite un supporto di social networking aziendale  <br/> |A meno che non è disabilitata la possibilità di creare gruppi esterni da un amministratore di Yammer, gli utenti possono creare gruppi esterni per collaborare in Yammer e le conversazioni, la possibilità di like e seguire post, condivisione di file e chat.  <br/> |[Creare e gestire i gruppi esterni in Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) <br/> |
   
## <a name="teams-collaboration-options"></a>Opzioni di collaborazione team

|**Obiettivo di condivisione**|**Azione amministrativa**|**Informazioni sulle procedure**|
|:-----|:-----|:-----|
|Collaborazione in team con utenti esterni all'organizzazione  <br/> |Un amministratore globale per il tenant di Office 365 invito è necessario abilitare la collaborazione esterna in team. I proprietari di team e gli amministratori globali ora sarà in grado di invitare tutti gli utenti con un indirizzo di posta elettronica per la collaborazione in team.  <br/> Gli amministratori possono inoltre gestire e modificare ospiti già presenti nel loro tenant.  <br/> |[Autorizzare l'accesso Guest](https://docs.microsoft.com/en-us/microsoftteams/teams-dependencies) <br/> [Attivare o disattivare l'accesso Guest in team](https://docs.microsoft.com/en-us/microsoftteams/set-up-guests) <br/> [Utilizzare PowerShell per controllare l'accesso Guest](https://docs.microsoft.com/en-us/microsoftteams/guest-access-powershell) <br/> [Elenco di controllo di accesso guest](https://docs.microsoft.com/en-us/microsoftteams/guest-access-checklist) <br/> [Visualizzare gli utenti Guest](https://docs.microsoft.com/en-us/microsoftteams/view-guests) <br/> [Modifica informazioni utente guest](https://docs.microsoft.com/en-us/microsoftteams/edit-guests-information) <br/> |
|I proprietari dei team possono invitare e gestire come Guest collaborare entro i team.  <br/> |I proprietari dei team dispone di controlli aggiuntivi in operazioni eseguibili ospiti entro i team.  <br/> |[Aggiungere ospiti](https://support.office.com/en-us/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [Aggiungere guest a un team](https://docs.microsoft.com/en-us/microsoftteams/add-guests) <br/> [Gestione dell'accesso Guest in team](https://docs.microsoft.com/en-us/microsoftteams/manage-guests) <br/> [Verificare chi sta un team o in un canale](https://support.office.com/en-us/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|Accesso guest da altro tenant consente di visualizzare contenuto in team e collaborare con altri membri  <br/> |Nessuno.  <br/> |[L'esperienza di accesso guest](https://docs.microsoft.com/en-us/microsoftteams/guest-experience) <br/> |
   
## <a name="points-to-be-aware-of-about-office-365-inter-tenant-collaboration"></a>Punta a tenere conto sulla collaborazione tra tenant Office 365

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Condivisione di archiviazione, le licenze, sottoscrizioni e gli account utente

Ciascuna organizzazione gestisce il proprio account utente, le identità, gruppi di sicurezza, le sottoscrizioni, licenze e archiviazione. Utenti utilizzano le funzionalità di collaborazione in Office 365 con la condivisione di criteri e impostazioni di protezione per fornire l'accesso alle informazioni necessarie mantenendo il controllo delle risorse della società.
  
- **Gli account utente:** Gli account non possono essere condivisi e gli account non possono essere duplicati tra il tenant o partizioni in locale Directory servizi di Active Directory. 
    
- **Licenze &amp; sottoscrizioni:** In Office 365, concede in licenza da Gestione licenze piani (anche denominato SKU o Office 365 dei piani) è possibile accedere ai servizi definiti per i piani di Office 365. 
    
- **Archiviazione:** Nei piani di Office 365 e confini software per SharePoint Online vengono gestiti separatamente da limiti di archiviazione delle cassette postali. Limiti di archiviazione delle cassette postali vengono impostati e gestiti tramite Exchange Online. In entrambi gli scenari di archiviazione non possono essere condivisi tra tenant. 
    
### <a name="can-we-share-domain-namespaces-across-office-365-tenants"></a>È possibile condividere gli spazi dei nomi di dominio tra tenant di Office 365?

No. Domini di personale, ad esempio fabrikam.com o GiochiOrsetti.com solo possono essere associati e utilizzati con un solo tenant al momento. Ogni tenant deve disporre di spazio dei nomi; Spazi dei nomi UPN, SMTP e SIP non possono essere condivise tra tenant.
  
### <a name="what-about-hybrid-components-and-office-365-inter-tenant-collaboration"></a>Cosa succede componenti ibrida e la collaborazione tra tenant Office 365?

Componenti ibrida locali, ad esempio un'organizzazione di Exchange e Azure Active Directory Connect, non possono essere suddivisi tra più tenant.
  

