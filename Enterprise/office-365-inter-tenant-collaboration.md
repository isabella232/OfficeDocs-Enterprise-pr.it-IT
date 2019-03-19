---
title: Collaborazione tra tenant di Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 11/08/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-collaboration
- M365-subscription-management
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
description: Informazioni su come funziona la collaborazione di Office 365 tra tenant e organizzazioni.
ms.openlocfilehash: d77146d4b95260e16984a76225cf24e65fe03bcc
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2019
ms.locfileid: "30665249"
---
# <a name="office-365-inter-tenant-collaboration"></a>Collaborazione tra tenant di Office 365

In questo articolo vengono descritte diverse modalità di collaborazione tra due tenant di Office 365. È destinato agli amministratori di Office 365.
  
Si supponga che due organizzazioni, Fabrikam e contoso, dispongano di un tenant di Office 365 per le aziende e che desiderino collaborare su diversi progetti. alcuni dei quali sono in esecuzione per un periodo di tempo limitato e alcuni dei quali sono in corso. In che modo Fabrikam e contoso consentono alle persone e ai team di collaborare in modo più efficace tra i diversi tenant di Office 365 in maniera sicura? Office 365, in combinazione con Azure Active Directory B2B Collaboration, offre diverse opzioni. In questo articolo vengono descritti alcuni scenari chiave che Fabrikam e Contoso possono prendere in considerazione.
  
Le opzioni di collaborazione tra tenant di Office 365 includono l'utilizzo di una posizione centrale per file e conversazioni, la condivisione di calendari, l'utilizzo di messaggistica istantanea, le chiamate audio/video per la comunicazione e la protezione dell'accesso alle risorse e alle applicazioni. Utilizzare le tabelle seguenti per selezionare soluzioni e altre informazioni.
  
## <a name="exchange-online-collaboration-options"></a>Opzioni di collaborazione di Exchange Online

|**Obiettivo di condivisione**|**Azione amministrativa**|**Informazioni su come eseguire la procedura**|
|:-----|:-----|:-----|
|Condividere i calendari con un'altra organizzazione di Office 365  <br/> |Gli amministratori possono configurare diversi livelli di accesso al calendario in Exchange Online per consentire alle aziende di collaborare con altre aziende e permettere agli utenti di condividere le pianificazioni (informazioni sulla disponibilità) con altre persone  <br/> |[Condivisione in Exchange Online](https://technet.microsoft.com/en-us/library/jj916670%28v=exchg.150%29.aspx) <br/> [Relazioni dell'organizzazione in Exchange Online](https://technet.microsoft.com/en-us/library/jj916658%28v=exchg.150%29.aspx) <br/> [Creare una relazione organizzativa in Exchange Online](https://technet.microsoft.com/en-us/library/jj916671%28v=exchg.150%29.aspx) <br/> [Modifica e relazione organizzativa in Exchange Online](https://technet.microsoft.com/en-us/library/jj916659%28v=exchg.150%29.aspx) <br/> [Rimuovere una relazione organizzativa in Exchange Online](https://technet.microsoft.com/en-us/library/jj916657%28v=exchg.150%29.aspx) <br/> [Condividere calendari con utenti esterni](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) <br/> |
|Controllare in che modo gli utenti condividono i propri calendari con persone esterne all'organizzazione  <br/> |Gli amministratori applicano i criteri di condivisione alle cassette postali degli utenti per controllare chi può essere condiviso e il livello di accesso concesso  <br/> |[Condivisione di criteri in Exchange Online](https://technet.microsoft.com/en-us/library/jj916673%28v=exchg.150%29.aspx) <br/> [Creare un criterio di condivisione in Exchange Online](https://technet.microsoft.com/en-us/library/jj916676%28v=exchg.150%29.aspx) <br/> [Applicare un criterio di condivisione alle cassette postali in Exchange Online](https://technet.microsoft.com/en-us/library/jj916672%28v=exchg.150%29.aspx) <br/> [Modifica, disabilitazione o rimozione di un criterio di condivisione in Exchange Online](https://technet.microsoft.com/en-us/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|Configurare i canali di posta elettronica sicuri e controllare il flusso di posta con organizzazioni partner  <br/> |Gli amministratori creano connettori per applicare la sicurezza agli scambi di posta con un'organizzazione partner o un provider di servizi. I connettori impongono la crittografia tramite TLS (Transport Layer Security) e consentono restrizioni sui nomi di dominio o intervalli di indirizzi IP che i partner inviano messaggi di posta elettronica.  <br/> |[Come viene utilizzato TLS per proteggere il traffico della posta elettronica in Office 365](https://technet.microsoft.com/en-us/library/mt163898.aspx) <br/> [Configure mail flow using connectors in Office 365](https://technet.microsoft.com/en-us/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [Domini remoti in Exchange Online](https://technet.microsoft.com/en-us/library/jj966211%28v=exchg.150%29.aspx) <br/> [Configurare il connettore per il flusso di posta sicura con un'organizzazione partner](https://technet.microsoft.com/en-us/library/dn751021%28v=exchg.150%29.aspx) <br/> [Procedure consigliate per il flusso di posta per Exchange Online e Office 365 (panoramica)](https://technet.microsoft.com/en-us/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>Opzioni di collaborazione di SharePoint Online e OneDrive for business

|**Obiettivi di condivisione**|**Azione amministrativa**|**Informazioni su come eseguire la procedura**|
|:-----|:-----|:-----|
|Condividere siti e documenti con utenti esterni  <br/> |Gli amministratori configurano la condivisione a livello di tenant o raccolta siti per account Microsoft autenticati, account di lavoro o dell'Istituto di istruzione o account Guest.  <br/> |
  [Gestire la condivisione esterna per l'ambiente di SharePoint Online](https://support.office.com/en-US/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> [Condivisione di domini con restrizioni in Office 365 SharePoint Online e OneDrive for business](https://support.office.com/en-US/article/Restricted-Domains-Sharing-in-Office-365-SharePoint-Online-and-OneDrive-for-Business-5d7589cd-0997-4a00-a2ba-2320ec49c4e9) <br/> [Utilizzo di SharePoint Online come soluzione Extranet business-to-business (B2B)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|Verifica e controllo della condivisione esterna per gli utenti finali  <br/> |I proprietari dei file di OneDrive for business e gli utenti finali di SharePoint Online configurano condivisione siti e documenti e stabiliscono notifiche per la condivisione di brani  <br/> |[Configurare le notifiche per la condivisione esterna per OneDrive for business](https://support.office.com/en-US/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [Condividere file o cartelle di SharePoint in Office 365](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a>Opzioni di collaborazione in Skype for business

|**Obiettivo di condivisione**|**Azione amministrativa**|**Informazioni su come eseguire la procedura**|
|:-----|:-----|:-----|
|Skype for business online-messaggistica istantanea, chiamate e presenza con altri utenti di Skype for business  <br/> |Gli amministratori possono abilitare gli utenti di Skype for business online a messaggistica istantanea, effettuare chiamate audio/video e visualizzare la presenza con gli utenti in un altro tenant di Office 365.  <br/> |[Permettere agli utenti di contattare utenti Skype for Business esterni](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|Skype for business online-messaggistica istantanea, chiamate e presenza con utenti Skype (consumer)  <br/> |Gli amministratori possono abilitare gli utenti di Skype for business online a messaggistica istantanea, effettuare chiamate e vedere la presenza con gli utenti Skype (consumer).  <br/> |[Consenti agli utenti di Skype for business di aggiungere contatti Skype](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a>Opzioni di collaborazione di Azure AD B2B

|**Obiettivo di condivisione**|**Azione amministrativa**|**Informazioni su come eseguire la procedura**|
|:-----|:-----|:-----|
|Collaborazione di Azure AD B2B-condivisione dei contenuti aggiungendo utenti esterni a un gruppo nella directory di un'organizzazione  <br/> |Un amministratore globale per un tenant di Office 365 può invitare persone in un altro tenant di Office 365 ad unirsi alla propria directory, aggiungere tali utenti esterni a un gruppo e concedere l'accesso al contenuto, ad esempio i siti di SharePoint e le raccolte per il gruppo.  <br/> |[Che cos'è Azure AD B2B Collaboration Preview?](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [Azure AD B2B: i nuovi aggiornamenti rendono collab Cross-Business facile](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [Condivisione esterna di Office 365 e collaborazione B2B di Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [API di collaborazione B2B di Azure Active Directory e personalizzazione](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-api) <br/> [Azure AD e Identity Show: collaborazione di Azure AD B2B (business to business](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="office-365-collaboration-options"></a>Opzioni di collaborazione di Office 365

|**Obiettivo di condivisione**|**Azione amministrativa**|**Informazioni su come eseguire la procedura**|
|:-----|:-----|:-----|
|Gruppi di Office 365: messaggi di posta elettronica, calendario, OneNote e file condivisi in una posizione centrale  <br/> |I gruppi sono supportati nei piani Business Essentials, Business Premium, Education e Enterprise E1, E3 ed E5. Gli utenti di un tenant di Office 365 possono creare un gruppo e invitare persone in un altro tenant di Office 365 come Guest. Si applica anche a Dynamics CRM.  <br/> |[Informazioni sui gruppi di Office 365](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [Accesso guest in gruppi di Office 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [Distribuire i gruppi di Office 365](https://technet.microsoft.com/en-us/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a>Opzioni di collaborazione di Yammer

|**Obiettivo di condivisione**|**Azione amministrativa**|**Informazioni su come eseguire la procedura**|
|:-----|:-----|:-----|
|Yammer-collaborazione tramite un supporto sociale aziendale  <br/> |A meno che la possibilità di creare gruppi esterni sia disattivata da un amministratore di Yammer, gli utenti possono creare gruppi esterni per collaborare in Yammer attraverso conversazioni, la possibilità di come e seguire i post, condividere file e chat online.  <br/> |[Creare e gestire gruppi esterni in Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) <br/> |
   
## <a name="teams-collaboration-options"></a>Opzioni di collaborazione per Teams

|**Obiettivo di condivisione**|**Azione amministrativa**|**Informazioni su come eseguire la procedura**|
|:-----|:-----|:-----|
|Collaborare in team con utenti esterni all'organizzazione  <br/> |Un amministratore globale per l'invitante Office 365 tenant deve abilitare la collaborazione esterna in teams. Gli amministratori globali e i proprietari del team saranno in grado di invitare tutti gli utenti con un indirizzo di posta elettronica a collaborare in teams.  <br/> Gli amministratori possono anche gestire e modificare gli ospiti già presenti nel tenant.  <br/> |[Autorizzare l'accesso Guest](https://docs.microsoft.com/en-us/microsoftteams/teams-dependencies) <br/> [Attivazione o disAttivazione dell'accesso guest in teams](https://docs.microsoft.com/en-us/microsoftteams/set-up-guests) <br/> [Utilizzo di PowerShell per controllare l'accesso Guest](https://docs.microsoft.com/en-us/microsoftteams/guest-access-powershell) <br/> [Elenco di controllo di accesso Guest](https://docs.microsoft.com/en-us/microsoftteams/guest-access-checklist) <br/> [Visualizzare gli utenti Guest](https://docs.microsoft.com/en-us/microsoftteams/view-guests) <br/> [Modificare le informazioni degli utenti Guest](https://docs.microsoft.com/en-us/microsoftteams/edit-guests-information) <br/> |
|I proprietari del team possono invitare e gestire in che modo gli ospiti collaborano all'interno del team.  <br/> |I proprietari del team dispongono di ulteriori controlli su ciò che gli utenti possono eseguire all'interno del team.  <br/> |[Aggiungere gli ospiti](https://support.office.com/en-us/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [Aggiungere un ospite a un team](https://docs.microsoft.com/en-us/microsoftteams/add-guests) <br/> [Gestire l'accesso guest in teams](https://docs.microsoft.com/en-us/microsoftteams/manage-guests) <br/> [Vedere chi è in un team o in un canale](https://support.office.com/en-us/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|Gli ospiti provenienti da altri inquilini possono visualizzare il contenuto in teams e collaborare con altri membri  <br/> |Nessuno.  <br/> |[L'esperienza di accesso Guest](https://docs.microsoft.com/en-us/microsoftteams/guest-experience) <br/> |

## <a name="power-bi-collaboration-options"></a>Opzioni di collaborazione di Power BI

|**Obiettivo di condivisione**|**Azione amministrativa**|**Informazioni su come eseguire la procedura**|
|:-----|:-----|:-----|
|Power BI consente agli utenti esterni di utilizzare i contenuti condivisi tramite collegamenti. Questo consente agli utenti dell'organizzazione di distribuire il contenuto in modo sicuro tra le organizzazioni.<br/> | L'amministratore di Power BI è in grado di controllare se gli utenti possono invitare utenti esterni a visualizzare il contenuto all'interno dell'organizzazione. <br/> |[Distribuire il contenuto di Power BI per gli utenti Guest esterni con Azure AD B2B](https://docs.microsoft.com/en-us/power-bi/service-admin-azure-ad-b2b) <br/> |
 
## <a name="points-to-be-aware-of-about-office-365-inter-tenant-collaboration"></a>Punti da tenere presenti circa la collaborazione tra tenant di Office 365

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Condivisione degli account utente, delle licenze, delle sottoscrizioni e dell'archiviazione

Ogni organizzazione gestisce gli account utente, le identità, i gruppi di sicurezza, le sottoscrizioni, le licenze e l'archiviazione. Gli utenti utilizzano le funzionalità di collaborazione di Office 365 insieme ai criteri di condivisione e alle impostazioni di sicurezza per consentire l'accesso alle informazioni necessarie mantenendo il controllo delle risorse aziendali.
  
- **Account utente:** Gli account non possono essere condivisi e gli account non possono essere duplicati tra i tenant o le partizioni nei servizi directory Active Directory locali. 
    
- **Abbonamenti alle licenze &amp; :** In Office 365, le licenze provenienti da piani di licenza (denominati anche SKU o piani di Office 365) offrono agli utenti l'accesso ai servizi di Office 365 definiti per tali piani. 
    
- **Archiviazione:** Nei piani di Office 365, i limiti del software e il limite per SharePoint Online vengono gestiti separatamente dai limiti di archiviazione delle cassette postali. I limiti di archiviazione delle cassette postali sono configurati e gestiti tramite Exchange Online. In entrambi gli scenari di archiviazione non è possibile condividere i tenant incrociati. 
    
### <a name="can-we-share-domain-namespaces-across-office-365-tenants"></a>È possibile condividere gli spazi dei nomi di dominio tra i tenant di Office 365?

No. I domini di vanità, ad esempio fabrikam.com o tailspintoys.com, possono essere associati e usati solo con un tenant al momento. Ogni tenant deve disporre di uno spazio dei nomi specifico. Gli spazi dei nomi UPN, SMTP e SIP non possono essere condivisi tra i tenant.
  
### <a name="what-about-hybrid-components-and-office-365-inter-tenant-collaboration"></a>Che cosa accade per i componenti ibridi e la collaborazione tra tenant di Office 365?

I componenti ibridi locali, ad esempio un'organizzazione di Exchange e Azure AD Connect, non possono essere divisi tra più tenant.
  

