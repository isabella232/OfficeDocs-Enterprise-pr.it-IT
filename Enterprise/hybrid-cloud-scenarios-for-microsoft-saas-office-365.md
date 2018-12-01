---
title: Scenari per il cloud ibrido per SaaS Microsoft (Office 365)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: "Sintesi: Comprendere l'architettura ibrida e gli scenari delle offerte cloud basate sul software distribuito come servizio Microsoft (SaaS) in Office 365."
ms.openlocfilehash: 063cbd03a2cc65a6cd278ab2efcea235079f801b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123413"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Scenari per il cloud ibrido per SaaS Microsoft (Office 365)

 **Sintesi:** Comprendere l'architettura ibrida e gli scenari delle offerte cloud basate sul software distribuito come servizio Microsoft (SaaS) in Office 365.
  
Combina le distribuzioni locali di Exchange, SharePoint o Skype for Business con le rispettive controparti in Office 365 come parte di una migrazione cloud o di una strategia di integrazione a lungo termine.
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Architettura per scenario ibrido in SaaS Microsoft

La figura 1 mostra l'architettura di scenari ibridi Microsoft basati su SaaS in Office 365.
  
**Figura 1: scenari ibridi Microsoft basati su SaaS per Office 365**

![Scenari ibridi Microsoft basati su SaaS per Office 365](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
Per ogni livello dell'architettura:
  
- App e scenari
    
    Esiste una serie di scenari ibridi basati su SaaS, che si allineano ai prodotti server Office e alle rispettive controparti in Office 365:
    
  - Exchange Server combinato con Exchange Online (Exchange Server ibrido)
    
  - Skype for Business Server combinato con Skype for Business Online e i nuovi scenari con Cloud PBX e la versione del connettore cloud
    
  - SharePoint Server 2019, 2016 Server SharePoint o SharePoint Server 2013 combinato con SharePoint Online (in diverse situazioni)
    
    Esiste anche Exchange Online con Skype for Business Server locale, uno scenario ibrido di prodotto incrociato.
    
- Identità
    
    Può includere la sincronizzazione della directory con Windows Server AD locale. In alternativa, è possibile configurare Azure AD in modo da attuare federazione con provider di identità di terze parti.
    
- Rete
    
    È costituito dalla pipe Internet esistente o da una connessione ExpressRoute con il peering Microsoft per Office 365 o Dynamics 365.
    
- Locale
    
    Può essere costituito da server esistenti di Exchange, SharePoint e Skype for Business, che devono essere aggiornati alle versioni più recenti. È quindi possibile combinarli con le rispettive controparti in Office 365 per gli scenari ibridi.
    
Configurare il proprio ambiente di sviluppo e di testing di Office 365, vedere [Guide dei laboratori di testing di Office 365](cloud-adoption-test-lab-guides-tlgs.md).
  
## <a name="skype-for-business-hybrid"></a>Versione ibrida di Skype for Business

Skype per l'ambiente ibrido Business consente di combinare una distribuzione locale esistente con Skype Business online. Alcuni utenti sono ospitati in locale e alcuni utenti ospitati in linea, ma gli utenti condividono lo stesso dominio protocollo SIP (Session Initiation), ad esempio contoso.com. È possibile utilizzare questa configurazione ibrida per eseguire la migrazione da locale a Office 365 nel tempo, al calendario. Skype per le aziende può inoltre essere integrata con [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).
  
**Figura 2: Skype per la configurazione ibrida Business**

![Skype per la configurazione ibrida Business](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
Nella figura 2 viene Skype per la configurazione ibrida Business, costituito da un Skype locale per pool front end di Business ed edge server per comunicare con Skype Business online in Office 365.
  
Per ulteriori informazioni, vedere [pianificare la connettività ibrida tra Skype per Business Server e Skype Business online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>Cloud PBX con Skype for Business Server

Cloud PBX con Skype per Business Server, è possibile effettuare la transizione di un Skype esistente per la distribuzione locale Business Server in una topologia con connettività PSTN Public Switched Telephone Network () locale. 
  
**Figura 3: cloud PBX con Skype for Business Server**

![Cloud PBX con Skype for Business Server](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
Nella figura 3 viene mostrata la configurazione di Cloud PBX con Skype for Business Server, che comprende un gateway PBX o Telco locale, uno Skype for Business Server e il PSTN connesso al Cloud PBX di Microsoft in Office 365, che include Skype for Business Online.
  
Gli utenti nell'organizzazione ospitati nel cloud possono ricevere servizi PBX (Private Branch eXchange) dal cloud Microsoft che includono segnalazione e segreteria telefonica; tuttavia, la connettività PSTN (segnale di linea) viene fornita mediante VoIP aziendale dalla distribuzione di Skype for Business Server locale.
  
Si tratta di un ottimo esempio una configurazione ibrida che consente di eseguire gradualmente la migrazione a un servizio basato su cloud. È possibile mantenere funzionalità vocali degli utenti quando si inizia a spostarli Skype Business online. È possibile spostare gli utenti al proprio ritmo sapere che le funzionalità vocali continuerà no materia cui sono ospitati. 
  
Per ulteriori informazioni, vedere [pianificare la connettività ibrida tra Skype per Business Server e Skype Business online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).
  
Se non disponi già di una distribuzione di Lync Server o Skype for Business Server esistente, puoi usare la versione del connettore cloud di Skype for Business, un set di macchine virtuali in pacchetto che implementano la connettività PSTN locale con Cloud PBX.
  
Per ulteriori informazioni, vedere [Piano per Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

  
## <a name="sharepoint-hybrid"></a>Ambiente ibrido di SharePoint

SharePoint ibrido combina SharePoint Online in Office 365 con la farm di SharePoint locale per un'esperienza ottimale che consenta di usufruire del meglio di entrambi i mondi.
  
**Figura 4: configurazione ibrida di SharePoint**

![configurazione ibrida di SharePoint](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
Nella figura 4 viene mostrata la configurazione ibrida di SharePoint, che comprende una farm di SharePoint locale che comunica con SharePoint Online in Office 365.
  
Scenari ibridi di SharePoint:
  
- [Versione ibrida di OneDrive for Business](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [Soluzione Extranet B2B ibrida](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [Ricerca ibrida](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [Profili ibridi](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [Selezione ibrida](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    È facile abilitare gli scenari ibridi con le procedure guidate che rendono automatica la configurazione ibrida, disponibili dall'interfaccia di amministrazione di SharePoint Online in Office 365.
    
- [Icona di avvio delle app estendibile ibrida](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    Consente agli utenti di visualizzare e usare i video in Office 365 e le app e le esperienze Delve nelle pagine della relativa farm di SharePoint locale.
    
Tutti questi scenari ibridi di SharePoint, ad eccezione dell'icona di avvio delle app ibrida estensibile, sono disponibili per gli utenti di SharePoint 2016 e SharePoint 2013.
  
## <a name="exchange-server-2016-hybrid"></a>Exchange Server 2016 ibrido

Con Exchange Server 2016 ibrido, puoi ottenere i vantaggi di Exchange Online in Office 365 per gli utenti online, mentre gli utenti locali continuano a usare l'infrastruttura di Exchange Server esistente. 
  
**Figura 5: configurazione ibrida di Exchange 2016**

![Configurazione ibrida di Exchange 2016](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
La figura 5 mostra la configurazione ibrida di Exchange 2016, formata da server Cassette postali di Exchange che comunicano con Exchange Online Protection e con le cassette postali di Office 365.
  
Alcuni utenti hanno un server di posta elettronica locale, altri usano Exchange Online; tuttavia, condividono tutti lo stesso spazio di indirizzi di posta elettronica.  
  
Questa configurazione ibrida:
  
- Sfrutta l'infrastruttura di Exchange Server esistente durante la migrazione a Exchange Online in base alle esigenze di pianificazione.
    
- Consente di supportare i siti remoti senza influire sull'infrastruttura per la gestione delle filiali.
    
- Consente di instradare la posta elettronica Internet in arrivo tramite Exchange Online Protection in Office 365.
    
- Risponde alle esigenze delle organizzazioni multinazionali con filiali per le quali è necessario che i dati siano conservati in locale.
    
Puoi anche integrare questa configurazione ibrida con altre applicazioni di Microsoft Office 365, tra cui Skype for Business Online e SharePoint Online.
  
Per ulteriori informazioni, vedere [Distribuzioni ibride di Exchange Server](https://docs.microsoft.com/exchange/exchange-hybrid).
  
## <a name="see-also"></a>Vedere anche

[Cloud ibrido Microsoft per Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

