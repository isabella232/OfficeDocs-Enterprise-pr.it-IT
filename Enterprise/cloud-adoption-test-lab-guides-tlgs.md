---
title: Testare Office 365 con le guide al lab di test (TLG) per l'adozione del cloud
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/09/2019
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
description: "Riepilogo: usare le guide dei lab di test per l'adozione del cloud per configurare dimostrazioni, modelli di verifica o ambienti di sviluppo/test per Office 365."
ms.openlocfilehash: 3531a3185cd52044ee59391d676fff1a7f4a5f64
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741172"
---
# <a name="test-office-365-with-cloud-adoption-test-lab-guides-tlgs"></a>Testare Office 365 con le guide al lab di test (TLG) per l'adozione del cloud

 **Riepilogo**: usare le guide dei lab di test per l'adozione del cloud per configurare dimostrazioni, modelli di verifica o ambienti di sviluppo/test per Office 365.
  
Le guide dei lab di test sono utili per imparare velocemente a usare i prodotti Microsoft. Sono ideali quando si ha la necessità di valutare una tecnologia o una configurazione prima di stabilire se è adatta alle proprie esigenze oppure prima di distribuirla ai propri utenti. L'esperienza pratica e manuale consente di comprendere i requisiti di implementazione relativi a un nuovo prodotto oppure a una nuova soluzione; in questo modo è possibile pianificare al meglio l'hosting in produzione.
  
Queste guide permettono di creare anche ambienti appositi per lo sviluppo e per il test delle applicazioni, noti anche con il nome di ambienti sviluppo/test.
  
![Guide dei laboratori di testing nel cloud Microsoft](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli nella serie di guide dei lab di test di Office 365.
    
## <a name="office-365-devtest-environment"></a>Ambiente di sviluppo/test di Office 365

Fare riferimento a questi articoli per creare un ambiente di sviluppo/test di Office 365:
  
- [Ambiente di sviluppo/test della configurazione di base](base-configuration-dev-test-environment.md)
    
    Creare una Intranet semplice all'interno dei servizi dell'infrastruttura Microsoft Azure. Si tratta di un passaggio facoltativo, da eseguire per creare una configurazione aziendale simulata.
    
- [Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
    
    Creare un abbonamento di prova a Office 365 Enterprise E5 dal computer o dalla Intranet semplificata che usa i servizi dell'infrastruttura Azure.
    
- [DirSync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md)
    
    Installare e configurare Azure AD Connect per la sincronizzazione della directory con sincronizzazione dell'hash delle password. Si tratta di un passaggio facoltativo, da eseguire per creare una configurazione aziendale simulata.
    
Per l'ambiente di sviluppo/test di Office 365, utilizzare questi articoli per dimostrare le funzionalità aziendali di Office 365:
  
- [Autenticazione a più fattori per l'ambiente di sviluppo/test di Office 365](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Configurare e testare l'autenticazione secondaria utilizzando un SMS inviato al proprio smartphone per un account dell’abbonamento a Office 365.
    
- [Identità federata per l'ambiente di sviluppo/test di Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
    
    Configurare e dimostrare l'autenticazione federata con gli account di un dominio di Active Directory Domain Services.
    
- [Cloud App Security per l'ambiente di sviluppo/test di Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    Configurare e dimostrare Office 365 Cloud App Security, che consente di creare criteri per monitorare e segnalare eventuali attività sospette nell'abbonamento a Office 365.
    
- [Advanced Threat Protection per l'ambiente di sviluppo/test di Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    Configurare e dimostrare Advanced Threat Protection, una funzionalità di Exchange Online Protection (EOP) che consente di bloccare il malware nei messaggi di posta elettronica.
    
- [Advanced eDiscovery per l'ambiente di sviluppo/test di Office 365](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    Aggiungere dati di esempio e dimostrare Advanced eDiscovery che permette di trovare e analizzare rapidamente i dati archiviati in Office 365, compresi documenti e messaggi di posta elettronica.
    
- [Protezione dei file sensibili nell'ambiente di sviluppo/test di Office 365](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    mostrare come è possibile usare Information Rights Management di Office 365 per proteggere i dati di documenti sensibili, anche quando vengono pubblicati per errore nella cartella sbagliata.
    
- [Classificazione e assegnazione di un'etichetta ai dati nell'ambiente di sviluppo/test di Office 365](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    Dimostrare in che modo il client Azure Information Protection può essere usato per classificare documenti con vari livelli di sicurezza.
    
- [Sito del team SharePoint Online isolato nell'ambiente di sviluppo/test](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    Dimostrare in che modo si crea un sito del team SharePoint Online che è isolato dal resto dell'organizzazione.
    

## <a name="simulated-cross-premises-devtest-environments"></a>Ambienti di sviluppo/test cross-premise simulati

È possibile creare un ambiente di sviluppo/test cross-premise, che include una rete virtuale di Azure e una rete locale simulata, facendo riferimento ai seguenti articoli:
  
- [Rete virtuale tra più sedi simulata in Azure](simulated-cross-premises-virtual-network-in-azure.md)
    
    Creare una Intranet simulata connessa a una rete virtuale di Azure in una configurazione cloud ibrida.
    
- [Ambiente di sviluppo/test di Intranet SharePoint Server 2016 in Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    Creare una farm a server singolo di SharePoint Server 2016 nella rete virtuale di Azure e testare la connettività e l'amministrazione dalla rete simulata locale.
    
## <a name="sharepoint-server-2016-devtest-environments"></a>Ambienti di sviluppo/test di SharePoint Server 2016

Di seguito sono riportati altri ambienti di sviluppo/test di SharePoint Server 2016 che è possibile creare nei servizi di infrastruttura di Azure:
  
- [Ambiente di sviluppo/test di SharePoint Server 2016 in Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure)
    
    Creare una farm a server singolo di SharePoint Server 2016 nei servizi di infrastruttura di Azure.

- [Ambiente di sviluppo/test di Intranet SharePoint Server 2016 in Azure](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)
    
    Creare una farm a server singolo di SharePoint Server 2016 nei servizi di infrastruttura di Azure e accedervi da una Intranet simulata.


## <a name="the-microsoft-365-enterprise-devtest-environments"></a>Ambienti di sviluppo/test di Microsoft 365 Enterprise

Creare un ambiente di sviluppo test per [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) con [questi articoli](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides).  
    
## <a name="see-also"></a>Vedere anche

[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)
  
[Risorse sull'architettura IT di Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)
  
[Modelli architetturali per SharePoint, Exchange, Skype for Business e Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Soluzioni ibride](hybrid-solutions.md)
