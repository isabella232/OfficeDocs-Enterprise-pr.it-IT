---
title: Testare Office 365 con le guide al lab di test (TLG) per l'adozione del cloud
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/13/2019
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: "Riepilogo: utilizzare queste guide al lab di test (TLG) per l'adozione del cloud per configurare dimostrazioni, modelli di verifica o ambienti di sviluppo/test per i prodotti di Office 365, Dynamics 365 e Office Server."
ms.openlocfilehash: 9d3423c1dadf95cd744a393c08b4303bc5cb8832
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573750"
---
# <a name="test-office-365-with-cloud-adoption-test-lab-guides-tlgs"></a>Testare Office 365 con le guide al lab di test (TLG) per l'adozione del cloud

 **Riepilogo:** utilizzare queste guide al lab di test (TLG) per l'adozione del cloud per configurare dimostrazioni, modelli di verifica o ambienti di sviluppo/test per i prodotti di Office 365, Dynamics 365 e Office Server.
  
Le Test Lab Guide sono utili per imparare velocemente a usare i prodotti Microsoft. Sono ideali quando si ha la necessità di valutare una tecnologia oppure una configurazione, prima di stabilire se è adatta alle proprie esigenze oppure prima di distribuirla ai propri utenti. L'esperienza pratica e manuale consente di comprendere i requisiti di implementazione relativi a un nuovo prodotto oppure a una nuova soluzione; in questo modo è possibile pianificare al meglio l'hosting in produzione.
  
Queste guide permettono di creare anche ambienti appositi per lo sviluppo e per il test delle applicazioni, noti anche con il nome di ambienti sviluppo/test.
  
![Test Lab Guide nel cloud Microsoft](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi al Test Lab Guide di One Microsoft Cloud.
    
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
    
    Configurare e dimostrare Office 365 Cloud App Security, che consente di creare criteri per monitorare e segnalare eventuali attività sospette nell'abbonamento a Office 365.
    
- [Protezione avanzata dalle minacce per l'ambiente di sviluppo/test di Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    Configurare e dimostrare Advanced Threat Protection, una funzionalità di Exchange Online Protection (EOP) che consente di bloccare il malware nei messaggi di posta elettronica.
    
- [Advanced eDiscovery per l'ambiente di sviluppo/test di Office 365](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    Aggiungere dati di esempio e dimostrare Advanced eDiscovery che permette di trovare e analizzare rapidamente i dati archiviati in Office 365, compresi documenti e messaggi di posta elettronica.
    
- [Protezione dei file sensibili nell’ambiente di sviluppo/test di Office 365](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    mostrare come è possibile usare Information Rights Management di Office 365 per proteggere i dati di documenti sensibili, anche quando vengono pubblicati per errore nella cartella sbagliata.
    
- [Classificazione e assegnazione di etichette ai dati nell'ambiente di sviluppo/test di Office 365 ](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    Dimostrare in che modo il client Azure Information Protection (AIP) può essere usato per classificare documenti con vari livelli di sicurezza.
    
- [Sito del team SharePoint Online isolato nell'ambiente di sviluppo/test](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    Dimostrare in che modo si crea un sito del team SharePoint Online che è isolato dal resto dell'organizzazione.
    
## <a name="the-microsoft-365-enterprise-test-environment"></a>Ambiente di test di Microsoft 365 Enterprise

Creare un ambiente di test per [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) con [questi articoli](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides).
 
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a>Ambiente di sviluppo/test di Office 365 e Dynamics 365

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
    
    Creare farm di base e a disponibilità elevata di SharePoint Server 2013 nei servizi di infrastruttura di Azure.
    
## <a name="see-also"></a>Vedere anche

[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Modelli architetturali per SharePoint, Exchange, Skype for Business e Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Soluzioni ibride](hybrid-solutions.md)


