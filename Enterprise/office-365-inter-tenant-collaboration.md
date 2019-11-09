---
title: Collaborazione tra tenant in Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 11/08/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-collaboration
- M365-subscription-management
- SPO_Content
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
description: Scopri come funziona la collaborazione tra tenant e organizzazioni in Office 365.
ms.openlocfilehash: b232cd2202f1b4e13102fd33ba545cfdcbb2edfe
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078175"
---
# <a name="office-365-inter-tenant-collaboration"></a>Collaborazione tra tenant in Office 365

Questo articolo descrive diverse modalità di collaborazione tra due tenant di Office 365. È destinato agli amministratori di Office 365.
  
Si supponga che due organizzazioni, Fabrikam e Contoso, abbiano un tenant di Office 365 per le aziende ciascuno e vogliano collaborare su progetti diversi, alcuni di durata limitata e altri continuativi. Quale soluzione possono adottare Fabrikam e Contoso per consentire a utenti e team di collaborare in modo efficace e sicuro in diversi tenant di Office 365? Office 365, insieme alla Collaborazione B2B di Azure Active Directory, offre diverse opzioni. Questo articolo descrive alcuni scenari chiave che Fabrikam e Contoso possono prendere in considerazione.
  
Le opzioni di collaborazione tra tenant di Office 365 includono l'utilizzo di una posizione centralizzata per i file e le conversazioni, la condivisione dei calendari, l'uso di messaggistica istantanea e di chiamate audio/video per le comunicazioni e la protezione dell'accesso a risorse e applicazioni. Usare le tabelle seguenti per selezionare le soluzioni e ottenere altre informazioni.
  
## <a name="exchange-online-collaboration-options"></a>Opzioni di collaborazione di Exchange Online

|**Obiettivo della condivisione**|**Azione amministrativa**|**Informazioni sulle procedure**|
|:-----|:-----|:-----|
|Condividere i calendari con un'altra organizzazione di Office 365  <br/> |Gli amministratori possono impostare diversi livelli di accesso al calendario di Exchange Online per consentire alle società di collaborare con altre società e consentire agli utenti di condividere le pianificazioni, ossia le informazioni sui periodi di disponibilità, con altri utenti  <br/> |[Condivisione in Exchange Online](https://technet.microsoft.com/library/jj916670%28v=exchg.150%29.aspx) <br/> [Relazioni dell'organizzazione in Exchange Online](https://technet.microsoft.com/library/jj916658%28v=exchg.150%29.aspx) <br/> [Creare una relazione dell'organizzazione in Exchange Online](https://technet.microsoft.com/library/jj916671%28v=exchg.150%29.aspx) <br/> [Modificare una relazione dell’organizzazione in Exchange Online](https://technet.microsoft.com/library/jj916659%28v=exchg.150%29.aspx) <br/> [Rimuovere una relazione dell'organizzazione in Exchange Online](https://technet.microsoft.com/library/jj916657%28v=exchg.150%29.aspx) <br/> [Condividere calendari con utenti esterni](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) <br/> |
|Controllare la modalità di condivisione dei calendari con persone esterne all'organizzazione  <br/> |Gli amministratori applicano criteri di condivisione alle cassette postali degli utenti per controllare con chi possono essere condivise e il livello di accesso concesso  <br/> |[Criteri di condivisione in Exchange Online](https://technet.microsoft.com/library/jj916673%28v=exchg.150%29.aspx) <br/> [Creare un criterio di condivisione in Exchange Online](https://technet.microsoft.com/library/jj916676%28v=exchg.150%29.aspx) <br/> [Applicare un criterio di condivisione alle cassette postali in Exchange Online](https://technet.microsoft.com/library/jj916672%28v=exchg.150%29.aspx) <br/> [Modificare, disabilitare o rimuovere un criterio di condivisione in Exchange Online](https://technet.microsoft.com/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|Configurare canali di posta elettronica protetti e controllare il flusso di posta con le organizzazioni partner  <br/> |Gli amministratori creano connettori per applicare le opzioni di sicurezza agli scambi di posta elettronica con un'organizzazione partner o un provider di servizi. I connettori usano la crittografia con TLS (Transport Layer Security) e consentono di applicare restrizioni ai nomi di dominio o agli intervalli di indirizzi IP da cui i partner inviano messaggi di posta elettronica.  <br/> |[Modalità d'uso di TLS in Exchange Online per proteggere il traffico di posta elettronica in Office 365](https://technet.microsoft.com/library/mt163898.aspx) <br/> [Configurare il flusso di posta elettronica tramite connettori in Office 365](https://technet.microsoft.com/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [Domini remoti in Exchange Online](https://technet.microsoft.com/library/jj966211%28v=exchg.150%29.aspx) <br/> [Configurare i connettori per un flusso di posta elettronica sicuro con un'organizzazione partner](https://technet.microsoft.com/library/dn751021%28v=exchg.150%29.aspx) <br/> [Procedure consigliate relative al flusso di posta elettronica per Exchange Online e Office 365 (panoramica)](https://technet.microsoft.com/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>Opzioni di collaborazione di SharePoint Online e OneDrive for Business

|**Obiettivi della condivisione**|**Azione amministrativa**|**Informazioni sulle procedure**|
|:-----|:-----|:-----|
|Condividere siti e documenti con utenti esterni  <br/> |Gli amministratori configurano la condivisione a livello del tenant o della raccolta siti per gli account Microsoft autenticati, gli account aziendali o dell'istituto di istruzione autenticati o gli account guest.  <br/> |[Gestire la condivisione esterna per l'ambiente di SharePoint Online](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> [Condividere domini con restrizioni in Office 365 SharePoint Online e OneDrive for Business](https://support.office.com/article/Restricted-Domains-Sharing-in-Office-365-SharePoint-Online-and-OneDrive-for-Business-5d7589cd-0997-4a00-a2ba-2320ec49c4e9) <br/> [Usare SharePoint Online come soluzione Extranet Business to Business (B2B)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|Verifica e controllo della condivisione esterna per gli utenti finali  <br/> |I proprietari di file di OneDrive for Business e gli utenti finali di SharePoint Online configurano la condivisione di siti e documenti e specificano le notifiche per tenere traccia della condivisione.  <br/> |[Configurare le notifiche per la condivisione esterna in OneDrive for Business](https://support.office.com/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [Condividere file o cartelle di SharePoint in Office 365](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a>Opzioni di collaborazione di Skype for Business

|**Obiettivo della condivisione**|**Azione amministrativa**|**Informazioni sulle procedure**|
|:-----|:-----|:-----|
|Skype for Business Online: messaggistica istantanea, chiamate e presenza con altri utenti di Skype for Business  <br/> |Gli amministratori possono consentire agli utenti di Skype for Business Online di usare la messaggistica istantanea, effettuare chiamate audio/video e vedere la presenza degli utenti in un altro tenant di Office 365.  <br/> |[Permettere agli utenti di contattare utenti di Skype for Business esterni](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|Skype for Business Online: messaggistica istantanea, chiamate e presenza con utenti di Skype (consumer)  <br/> |Gli amministratori possono consentire agli utenti di Skype for Business Online di usare la messaggistica istantanea, effettuare chiamate e vedere la presenza con utenti di Skype (consumer).  <br/> |[Consentire agli utenti di Skype for Business di aggiungere contatti Skype](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a>Opzioni di Collaborazione B2B di Azure AD

|**Obiettivo della condivisione**|**Azione amministrativa**|**Informazioni sulle procedure**|
|:-----|:-----|:-----|
|Collaborazione B2B di Azure Active Directory: condivisione di contenuto aggiungendo utenti esterni a un gruppo nella directory di un'organizzazione  <br/> |Un amministratore globale per un tenant di Office 365 può invitare le persone in un altro tenant di Office 365 a partecipare alla propria directory, aggiungere utenti esterni a un gruppo e consentire l'accesso ai contenuti, ad esempio i siti e le raccolte di SharePoint per il gruppo.  <br/> |[Che cos'è l'anteprima di Collaborazione B2B di Azure AD?](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [Collaborazione B2B di Azure AD: nuovi aggiornamenti che facilitano la collaborazione tra aziende](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [Condivisione esterna di Office 365 e Collaborazione B2B di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [API e personalizzazione per Collaborazione B2B di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-api) <br/> [Azure AD and Identity Show: Collaborazione Business to Business (B2B) di Azure AD](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="office-365-collaboration-options"></a>Opzioni di collaborazione di Office 365

|**Obiettivo della condivisione**|**Azione amministrativa**|**Informazioni sulle procedure**|
|:-----|:-----|:-----|
|Gruppi di Office 365: posta elettronica, calendario, OneNote e file condivisi in una posizione centrale  <br/> |I gruppi sono supportati in Business Essentials, Business Premium, per l’istruzione e nei piani Enterprise E1, E3 ed E5. Gli utenti in un tenant di Office 365 possono creare un gruppo e invitare le persone di un altro tenant di Office 365 come utenti guest. Ciò si applica anche a Dynamics CRM.  <br/> |[Informazioni sui gruppi di Office 365](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [Accesso guest ai Gruppi di Office 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [Distribuire Gruppi di Office 365](https://technet.microsoft.com/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a>Opzioni di collaborazione di Yammer

|**Obiettivo della condivisione**|**Azione amministrativa**|**Informazioni sulle procedure**|
|:-----|:-----|:-----|
|Yammer: collaborazione con i social media aziendali  <br/> |Se la caratteristica non è stata disabilitata da un amministratore di Yammer, gli utenti possono creare gruppi esterni per collaborare in Yammer tramite le conversazioni, aggiungendo Mi piace e seguendo i post, condividendo i file e usando le chat online.  <br/> |[Creare e gestire gruppi esterni in Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) <br/> |
   
## <a name="teams-collaboration-options"></a>Opzioni di collaborazione di Teams

|**Obiettivo della condivisione**|**Azione amministrativa**|**Informazioni sulle procedure**|
|:-----|:-----|:-----|
|Collaborare in Teams con utenti esterni all'organizzazione  <br/> |Un amministratore globale del tenant Office 365 che manda l’invito deve abilitare la collaborazione esterna in Teams. Gli amministratori globali e i proprietari del team potranno quindi invitare utenti che dispongono di un indirizzo di posta elettronica a collaborare in Teams.  <br/> Gli amministratori possono anche gestire e modificare guest già presenti nel proprio tenant.  <br/> |[Gestire l'accesso guest](https://docs.microsoft.com/microsoftteams/teams-dependencies) <br/> [Attivare o disattivare l'accesso guest in Teams](https://docs.microsoft.com/microsoftteams/set-up-guests) <br/> [Usare PowerShell per controllare l'accesso guest](https://docs.microsoft.com/microsoftteams/guest-access-powershell) <br/> [Elenco di controllo dell’accesso guest](https://docs.microsoft.com/microsoftteams/guest-access-checklist) <br/> [Visualizzare gli utenti guest](https://docs.microsoft.com/microsoftteams/view-guests) <br/> [Modificare le informazioni degli utenti guest](https://docs.microsoft.com/microsoftteams/edit-guests-information) <br/> |
|I proprietari del team possono invitare e gestire il modo in cui gli utenti possono collaborare all'interno del team.  <br/> |I proprietari del team hanno controlli supplementari sulle operazioni che gli utenti possono eseguire all'interno del team.  <br/> |[Aggiungere un utente guest](https://support.office.com/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [Aggiungere un utente guest a un team](https://docs.microsoft.com/microsoftteams/add-guests) <br/> [Gestire l'accesso guest in Teams](https://docs.microsoft.com/microsoftteams/manage-guests) <br/> [Vedere chi è in un team o in un canale](https://support.office.com/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|Gli utenti guest di altri tenant possono visualizzare il contenuto in Teams e collaborare con altri membri  <br/> |Nessuna.  <br/> |[L'esperienza di accesso come utente guest](https://docs.microsoft.com/microsoftteams/guest-experience) <br/> |

## <a name="power-bi-collaboration-options"></a>Opzioni di collaborazione di Power BI

|**Obiettivo della condivisione**|**Azione amministrativa**|**Informazioni sulle procedure**|
|:-----|:-----|:-----|
|Power BI abilita gli utenti guest esterni a usare i contenuti condivisi tramite collegamenti. Questo consente agli utenti dell'organizzazione di distribuire contenuti in modo sicuro tra le diverse organizzazioni.<br/> | L'amministratore di Power BI può controllare se gli utenti possono invitare gli utenti esterni a visualizzare il contenuto all'interno dell'organizzazione. <br/> |[Distribuire il contenuto di Power BI a utenti guest esterni con Azure AD B2B](https://docs.microsoft.com/power-bi/service-admin-azure-ad-b2b) <br/> |
 
## <a name="points-to-be-aware-of-about-office-365-inter-tenant-collaboration"></a>Aspetti da tenere in considerazione sulla collaborazione tra tenant di Office 365

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Condivisione di account utente, licenze, sottoscrizioni e archiviazione

Ogni organizzazione gestisce i propri account utente, identità, gruppi di sicurezza, abbonamenti, licenze e archiviazione. Le persone usano le funzionalità di collaborazione in Office 365 insieme ai criteri di condivisione e alle impostazioni di sicurezza per fornire l'accesso alle informazioni necessarie mantenendo il controllo delle risorse aziendali.
  
- **Account utente:** gli account non possono essere condivisi e duplicati tra i tenant o le partizioni nei servizi directory di Active Directory locali. 
    
- **Licenze e abbonamenti:** in Office 365 le licenze dei piani di licenza, note anche come SKU o piani di Office 365, concedono agli utenti l'accesso ai servizi di Office 365 definiti per i piani. 
    
- **Archiviazione:** nei piani di Office 365 i limiti e le restrizioni del software per SharePoint Online sono gestiti separatamente dai limiti di archiviazione della cassetta postale. I limiti di archiviazione della cassetta postale vengono configurati e gestiti con Exchange Online. In entrambi i casi, lo spazio di archiviazione non può essere condiviso tra i tenant. 
    
### <a name="can-we-share-domain-namespaces-across-office-365-tenants"></a>È possibile condividere gli spazi dei nomi di dominio tra i tenant di Office 365?

No. I domini personali, come fabrikam.com o tailspintoys.com, possono essere associati e usati solo con un tenant alla volta. Ogni tenant deve avere il proprio spazio dei nomi. Gli spazi dei nomi UPN, SMTP e SIP non possono essere condivisi tra i tenant.
  
### <a name="what-about-hybrid-components-and-office-365-inter-tenant-collaboration"></a>Informazioni su componenti ibridi e la collaborazione tra tenant di Office 365

I componenti ibridi locali, ad esempio un'organizzazione di Exchange e Azure AD Connect, non possono essere suddivisi tra più tenant.
  

