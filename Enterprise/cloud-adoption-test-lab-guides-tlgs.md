---
title: Test Lab Guide (TLG) per l’adozione del cloud
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: "Sintesi: utilizzare queste Test Lab Guide per l'adozione del cloud per configurare dimostrazioni o ambienti di sviluppo/test per i prodotti Office 365, Enterprise Mobility + \nSuite (EMS), Dynamics 365 e Office Server."
ms.openlocfilehash: ac48a9d3d0941b1152aa2bc22a8d9aa5dde7ad77
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188164"
---
# <a name="cloud-adoption-test-lab-guides-tlgs"></a>Test Lab Guide (TLG) per l’adozione del cloud

 **Sintesi:** utilizzare queste Test Lab Guide per l'adozione del cloud per configurare dimostrazioni o ambienti di sviluppo e di testing per i prodotti Office 365, Enterprise Mobility + Suite (EMS), Dynamics 365 e Office Server.
  
Le Test Lab Guide sono utili per imparare velocemente a usare i prodotti Microsoft. Sono ideali quando si ha la necessità di valutare una tecnologia oppure una configurazione, prima di stabilire se è adatta alle proprie esigenze oppure prima di distribuirla ai propri utenti. L'esperienza pratica e manuale consente di comprendere i requisiti di implementazione relativi a un nuovo prodotto oppure a una nuova soluzione; in questo modo è possibile pianificare al meglio l'hosting in produzione.
  
Queste guide permettono di creare anche ambienti appositi per lo sviluppo e per il test delle applicazioni, noti anche con il nome di ambienti sviluppo/test.
  
![Test Lab Guide nel cloud Microsoft](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
Consultare queste risorse aggiuntive prima di procedere:
  
- Visualizzare l’[esperienza Microsoft Cloud con Cloud Adoption Test Lab Guide](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) sessione di Microsoft Virtual Academy (solo 22 minuti).
    
- Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi al Test Lab Guide di One Microsoft Cloud.
    
## <a name="office-365-devtest-environment"></a>Ambiente di sviluppo/test di Office 365

Fare riferimento a questi articoli per creare un ambiente di sviluppo/test di Office 365:
  
- [ Configurazione di base dell’ambiente di sviluppo/test](base-configuration-dev-test-environment.md)
    
    Creare una Intranet semplice all'interno dei servizi dell'infrastruttura Microsoft Azure. Si tratta di un passaggio facoltativo, da eseguire per creare una configurazione aziendale simulata.
    
- [Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
    
    Creare un abbonamento di prova a Office 365 Enterprise E5 dal computer o dalla Intranet semplificata che usa i servizi dell'infrastruttura Azure.
    
- [DirSync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md)
    
    Installare e configurare Azure AD Connect per la sincronizzazione della directory con sincronizzazione della password. Si tratta di un passaggio facoltativo, da eseguire per creare una configurazione aziendale simulata.
    
Per l'ambiente di sviluppo/test di Office 365, utilizzare questi articoli per dimostrare le funzionalità aziendali di Office 365:
  
- [Autenticazione a più fattori per l'ambiente di sviluppo/test di Office 365. ](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Configurare e testare l'autenticazione secondaria utilizzando un SMS inviato al proprio smartphone per un account dell’abbonamento a Office 365.
    
- [Identità federata per l'ambiente di sviluppo/test di Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
    
    Configurare e dimostrare l'autenticazione federata con gli account di un dominio Windows Server Active Directory.
    
- [Cloud App Security per l'ambiente di sviluppo/test di Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    Configurare e dimostrare Office 365 Cloud App Security, che consente all'utente di creare criteri per monitorare e segnalare eventuali attività sospette nell’ambito del proprio abbonamento a Office 365.
    
- [Protezione avanzata dalle minacce per l'ambiente di sviluppo/test di Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    Configurare e dimostrare Advanced Threat Protection, una funzionalità di Exchange Online Protection (EOP) che consente di bloccare il malware nei messaggi di posta elettronica.
    
- [Advanced eDiscovery per l'ambiente di sviluppo/test di Office 365](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    Aggiungere dati di esempio e mostrare Advanced eDiscovery che permette di trovare e analizzare rapidamente i dati archiviati in Office 365, ad esempio, e-mail e documenti.
    
- [Protezione dei file sensibili nell’ambiente di sviluppo/test di Office 365](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    mostrare come è possibile usare Information Rights Management di Office 365 per proteggere i dati di documenti sensibili, anche quando vengono pubblicati per errore nella cartella sbagliata.
    
- [Classificazione e assegnazione di etichette ai dati nell'ambiente di sviluppo/test di Office 365 ](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    Dimostrare in che modo il client Azure Information Protection (AIP) può essere usato per classificare documenti con vari livelli di sicurezza.
    
- [Sito del team SharePoint Online isolato nell'ambiente di sviluppo/test](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    Dimostrare in che modo si crea un sito del team SharePoint Online che è isolato dal resto dell'organizzazione.
    
## <a name="the-microsoft-365-enterprise-devtest-environment"></a>Ambiente di sviluppo/test di Microsoft 365 Enterprise

Creare un ambiente di sviluppo/test per scenari [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) partendo da questi articoli:
  
- [Ambiente di sviluppo/test di Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
    
    Creare l'ambiente iniziale con Office 365 E5, EMS E5 e un computer che esegue Windows 10 Enterprise.
    
- [Criteri MAM per l’ambiente di sviluppo/test di Microsoft 365 Enterprise](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
    Creare gruppi utente e criteri di gestione di applicazioni mobili per dispositivi iOS e Android.
    
- [Registrazione dei dispositivi iOS e Android nell'ambiente di sviluppo e test di Microsoft 365 Enterprise](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
    
    Registrare dispositivi iOS e Android e gestirli in remoto.
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a>Ambiente di sviluppo/testing di Office 365 e Dynamics 365

Aggiungere un abbonamento di prova a Dynamics 365 e testare le funzionalità e gli scenari integrati di Office 365 e Dynamics 365 con questi articoli:
  
- [Ambiente di sviluppo/test di Office 365 e Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md)
    
    Aggiungere un abbonamento di prova a Dynamics 365 e licenze di Dynamics 365, nonché autorizzazioni ai propri account utente.
    
- [Integrazione di Exchange Online per il proprio ambiente di sviluppo/test di Office 365 e Dynamics 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    Configurare e dimostrare in che modo Office 365 e Dynamics 365 interagiscono nelle cassette postali di Exchange Online.
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a>Ambiente di sviluppo/test One Microsoft Cloud

Creare un ambiente di sviluppo/test che includa tutte le offerte cloud di Microsoft: Office 365, Azure, EMS e Dynamics 365. Vedere [ambiente di sviluppo/test di One Microsoft Cloud](the-one-microsoft-cloud-dev-test-environment.md) per istruzioni più dettagliate.
  
## <a name="simulated-cross-premises-devtest-environments"></a>Ambienti di sviluppo/test cross-premise simulati

È possibile creare un ambiente di sviluppo/test cross-premise, che include una rete virtuale di Azure e una rete locale simulata, facendo riferimento ai seguenti articoli:
  
- [Rete virtuale cross-premise simulata in Azure](simulated-cross-premises-virtual-network-in-azure.md)
    
    Creare una Intranet simulata connessa alla rete virtuale di Azure in una configurazione cloud ibrida.
    
- [Ambiente di sviluppo/test di intranet SharePoint Server 2016 in Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    Creare una farm con un solo server di SharePoint Server 2016 nella rete virtuale di Azure e testare la connettività e l'amministrazione dalla rete simulata locale.
    
## <a name="additional-cloud-based-devtest-environments"></a>Altri ambienti di sviluppo/testing basati su cloud

Di seguito sono riportati altri ambienti di sviluppo/test basati su cloud che è possibile creare nei servizi di infrastruttura di Azure:
  
- [Ambiente di sviluppo/test di SharePoint Server 2016 in Azure](https://technet.microsoft.com/library/mt723354.aspx)
    
    Creare una farm con un solo server di SharePoint Server 2016 nei servizi di infrastruttura di Azure.
    
- [Ambiente di sviluppo/test di Exchange 2016 in Azure](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    Creare un solo server Exchange 2016 nei servizi di infrastruttura di Azure.
    
- [Ambiente di sviluppo/test di SharePoint Server 2013 in Azure](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    Creare farm di SharePoint Server 2013 con disponibilità di base ed elevata nei servizi di infrastruttura di Azure.
    
**Partecipa alla discussione**

|**Contattaci**|**Descrizione**|
|:-----|:-----|
|**Ottenere la soluzione necessaria** <br/> |Microsoft sta creando documenti contenenti soluzioni che fanno riferimento a numerosi prodotti e servizi. Fornire commenti e suggerimenti sulle soluzioni tra server proposte o richiedere una soluzione specifica inviando un'e-mail all'indirizzo [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).<br/> |
|**Partecipare alla discussione sulle soluzioni** <br/> |Se si è appassionati di soluzioni basate sul cloud, prendere in considerazione l'idea di accedere al Cloud Adoption Advisory Board (CAAB) per connettersi con una community più ampia e vivace di sviluppatori di contenuti Microsoft, professionisti del settore e clienti di tutto il mondo. Per accedervi, diventare un membro dell'[area CAAB (Cloud Adoption Advisory Board)](https://aka.ms/caab) della Community tecnica Microsoft e inviare una breve e-mail all'indirizzo [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Chiunque può leggere i contenuti correlati alla community nel [blog di CAAB](https://blogs.technet.com/b/solutions_advisory_board/). Tuttavia, i membri CAAB ricevono inviti a webinar privati che descrivono le nuove soluzioni e risorse relative all'adozione del cloud.  <br/> |
|**Ottenere l'immagine visualizzata** <br/> |Se si desidera una copia modificabile dell'immagine visualizzata in questo articolo, Microsoft si occuperà di inviarla. Inviare la propria richiesta tramite e-mail, includendo l'URL e il titolo dell'immagine, all'indirizzo [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  <br/> |
   
## <a name="see-also"></a>Vedere anche

<a name="ADD_TLGs"> </a>

[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Modelli architetturali per SharePoint, Exchange, Skype for Business e Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Soluzioni ibride](hybrid-solutions.md)


