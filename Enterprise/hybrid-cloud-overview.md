---
title: Panoramica del cloud ibrido
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3ea3ee10-411e-4690-b9e5-f1b46f1f4d59
description: 'Riepilogo: Informazioni sulla definizione e sugli elementi del cloud ibrido Microsoft.'
ms.openlocfilehash: b77df519dc89a5ab97d965c16dc9f54955614903
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915821"
---
# <a name="hybrid-cloud-overview"></a>Panoramica del cloud ibrido

 **Riepilogo:** Informazioni sulla definizione e sugli elementi del cloud ibrido Microsoft.
  
Cloud ibrida utilizza le risorse di archiviazione o compute nella rete locale e nel cloud. Cloud ibrida è possibile utilizzare un percorso di migrazione nel cloud le esigenze aziendali e il relativo IT o integrare le piattaforme cloud e i servizi esistenti locali dell'infrastruttura come parte della strategia IT generale.
  
## <a name="microsoft-hybrid-cloud"></a>Cloud ibrida Microsoft

Cloud ibrida Microsoft è un insieme di scenari aziendali in cui combinare piattaforma Microsoft cloud con un componente locale, ad esempio: 
  
- Ottenere risultati di ricerca di contenuti in una farm di SharePoint locale e in SharePoint Online in Office 365.
    
- App per dispositivi mobili in esecuzione in Azure che esegue la query su un archivio dati locale.
    
- Una rete intranet IT carico di lavoro in esecuzione su macchine virtuali di Azure.
    
**Figura 1: Componenti di Microsoft cloud ibrida**

![Componenti del cloud ibrido Microsoft](media/Hybrid-Poster/MS-Hybrid-Cloud.png)
  
Nella figura 1 vengono illustrati i componenti del cloud ibrida Microsoft, da una rete locale per il set di Office 365, piattaforma Azure come servizio PaaS () e l'infrastruttura di Azure come un servizio (IaaS) servizi disponibili tramite Internet o una connessione ExpressRoute.
  
Poiché Microsoft ha la soluzione cloud più completa sul mercato, incluso il Software come servizio (SaaS), PaaS e IaaS, è possibile:
  
- Sfruttare gli investimenti locali esistenti quando si esegue la migrazione dei carichi di lavoro e le applicazioni nel cloud.
    
- Incorporare scenari basati su cloud ibrida i piani IT a lungo termine, ad esempio, quando le regole o i criteri non consentono lo spostamento dei carichi di lavoro o dati specifici nel cloud.
    
- Creare uno scenario ibrido aggiuntive che includono più servizi cloud Microsoft e piattaforme.
    
Scenari per il cloud ibrida con servizi cloud Microsoft variano con la piattaforma.
  
- SaaS
    
    Servizi Microsoft SaaS includono Office 365, Microsoft Intune e Microsoft Dynamics 365. Scenari basati su cloud ibrida con Microsoft SaaS combinano questi servizi con applicazioni o servizi locali. Ad esempio, Exchange Online in esecuzione in Office 365 può essere integrata con Skype per 2015 Business che viene distribuito in locale.
    
- PaaS di Azure
    
    I servizi Microsoft Azure PaaS consentono di creare applicazioni basate su cloud. Scenari basati su cloud ibrida con i servizi di Azure PaaS combinano un'app PaaS Azure con risorse locali o applicazioni. Ad esempio, un'app di Azure PaaS potrebbe in modo sicuro interrogare un archivio dati locale per le informazioni necessarie per visualizzare agli utenti di app per dispositivi mobili.
    
- IaaS di Azure
    
    Servizi di Azure IaaS consentono di creare ed eseguire carichi di lavoro basate su server IT nel cloud, anziché nel centro dati in locale. Scenari basati su cloud ibrida con i servizi di Azure IaaS include in genere di un carico di lavoro IT che viene eseguito su macchine virtuali in modo trasparente connesso alla rete locale. Gli utenti locali non si noteranno la differenza.
    
## <a name="elements-of-hybrid-cloud"></a>Elementi del cloud ibrida

È necessario considerare gli elementi seguenti durante la pianificazione e l'implementazione di scenari basati su cloud ibrida con Microsoft cloud piattaforme e servizi.
  
- Rete
    
    La rete per scenari basati su cloud ibrida include la connettività per la piattaforma Microsoft cloud e dei servizi e larghezza di banda sufficiente per essere ad alte prestazioni con carichi di picco. Per ulteriori informazioni, vedere [Microsoft Cloud di rete per architetti Enterprise](microsoft-cloud-networking-for-enterprise-architects.md).
    
- Identità
    
    Identità per gli scenari ibridi SaaS e Azure PaaS può includere Azure Active Directory come provider di identità comuni, che possono essere sincronizzati con locale Windows Server Active Directory o federati con Windows Server Active Directory o altri provider di identità. È inoltre possibile estendere l'infrastruttura di identità in locale per Azure IaaS. Per ulteriori informazioni, vedere [Identità Cloud Microsoft per architetti Enterprise](microsoft-cloud-it-architecture-resources.md#identity).
    
- Sicurezza
    
    Protezione di scenari basati su cloud ibrida include gestione per le identità, la protezione dei dati, gestione di privilegi amministrativi, la consapevolezza delle minacce e l'implementazione della governance e criteri di sicurezza e protezione. Per ulteriori informazioni, vedere [Microsoft Security Cloud per architetti Enterprise](https://technet.microsoft.com/library/dn919927.aspx#security).
    
- Gestione
    
    Gestione di scenari basati su cloud ibrida include la possibilità di gestire le impostazioni, dati, account, criteri e le autorizzazioni e per monitorare lo stato in corso degli elementi dello scenario e le prestazioni. È inoltre possibile utilizzare il set di strumenti stesso, ad esempio Systems Management Server per la gestione delle macchine virtuali di Azure IaaS.
    
## <a name="see-also"></a>Vedere anche

[Cloud ibrido Microsoft per Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT](https://sway.com/FJ2xsyWtkJc2taRD)
 


