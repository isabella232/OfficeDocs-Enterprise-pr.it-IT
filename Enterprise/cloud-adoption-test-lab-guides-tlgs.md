---
title: Testare Office 365 con le guide al lab di test (TLG)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/12/2019
audience: ITPro
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
description: 'Riepilogo: usare le guide dei laboratori di test (TLG) per configurare le dimostrazioni, la prova del concetto o gli ambienti di sviluppo/test per Office 365.'
ms.openlocfilehash: 32675683846789f1e7be0e398e5b140d25d7ba80
ms.sourcegitcommit: d58cdc7b2296df12f7a05d14ba05ab224ffb3e0c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2019
ms.locfileid: "36302738"
---
# <a name="test-office-365-with-test-lab-guides-tlgs"></a>Testare Office 365 con le guide al lab di test (TLG)

 **Riepilogo**: usare le guide dei laboratori di test (TLG) per configurare le dimostrazioni, la prova del concetto o gli ambienti di sviluppo/test per Office 365.
  
Le guide dei lab di test sono utili per imparare velocemente a usare i prodotti Microsoft. Sono ideali quando si ha la necessità di valutare una tecnologia o una configurazione prima di stabilire se è adatta alle proprie esigenze oppure prima di distribuirla ai propri utenti. L'esperienza pratica e manuale consente di comprendere i requisiti di implementazione relativi a un nuovo prodotto oppure a una nuova soluzione; in questo modo è possibile pianificare al meglio l'hosting in produzione.
  
Queste guide permettono di creare anche ambienti appositi per lo sviluppo e per il test delle applicazioni, noti anche con il nome di ambienti sviluppo/test.
  
![Guide dei laboratori di testing nel cloud Microsoft](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
## <a name="office-365-devtest-environment"></a>Ambiente di sviluppo/test di Office 365

Fare riferimento a questi articoli per creare un ambiente di sviluppo/test di Office 365:
  
- [ Configurazione di base dell’ambiente di sviluppo/test](base-configuration-dev-test-environment.md)
    
    Creare una Intranet semplice all'interno dei servizi dell'infrastruttura Microsoft Azure. Si tratta di un passaggio facoltativo, da eseguire per creare una configurazione aziendale simulata.
    
- [Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
    
    Creare un abbonamento di prova a Office 365 Enterprise E5 dal computer o dalla Intranet semplificata che usa i servizi dell'infrastruttura Azure.
    
- [Sincronizzazione della directory](dirsync-for-your-office-365-dev-test-environment.md)
    
    Installare e configurare Azure AD Connect per la sincronizzazione della directory con sincronizzazione dell'hash delle password. Si tratta di un passaggio facoltativo, da eseguire per creare una configurazione aziendale simulata.
    
Per l'ambiente di sviluppo/test di Office 365, utilizzare questi articoli per dimostrare le funzionalità aziendali di Office 365:
  
- [Autenticazione a più fattori](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Configurare e testare l'autenticazione secondaria utilizzando un SMS inviato al proprio smartphone per un account dell’abbonamento a Office 365.
    
- [Identità federata](federated-identity-for-your-office-365-dev-test-environment.md)
    
    Configurare e dimostrare l'autenticazione federata con gli account di un Dominio di Active Directory Domain Services.
    
- [Protezione avanzata dalle minacce](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    Configurare e dimostrare Advanced Threat Protection, una funzionalità di Exchange Online Protection (EOP) che consente di bloccare il malware nei messaggi di posta elettronica.

## <a name="simulated-cross-premises-devtest-environment"></a>Ambienti di sviluppo/test cross-premise simulati

Creare una Intranet [simulata connessa](simulated-cross-premises-virtual-network-in-azure.md) a una rete virtuale di Azure in una configurazione cloud ibrida.
    
## <a name="sharepoint-server-2016-devtest-environment"></a>ambiente di sviluppo/test di SharePoint Server 2016

Creare una farm a [server singolo di SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure) nei servizi di infrastruttura di Azure.

## <a name="microsoft-365-enterprise-devtest-environment"></a>Ambiente di sviluppo/test di Microsoft 365 Enterprise

Creare un ambiente di sviluppo test[Ambiente di sviluppo/test di Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides).  
    
## <a name="see-also"></a>Vedere anche

[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Modelli architetturali per SharePoint, Exchange, Skype for Business e Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Soluzioni ibride](hybrid-solutions.md)
