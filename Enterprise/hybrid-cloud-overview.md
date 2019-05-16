---
title: Panoramica sul cloud ibrido
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3ea3ee10-411e-4690-b9e5-f1b46f1f4d59
description: 'Riepilogo: Informazioni sulla definizione e sugli elementi del cloud ibrido Microsoft.'
ms.openlocfilehash: f44251c0a0da79475c1cc391dd409db6b2faba0f
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067445"
---
# <a name="hybrid-cloud-overview"></a>Panoramica sul cloud ibrido

 **Riepilogo:** Informazioni sulla definizione e sugli elementi del cloud ibrido Microsoft.
  
Il cloud ibrido utilizza risorse di calcolo o di archiviazione sulla rete locale e nel cloud. È possibile utilizzare il cloud ibrido come percorso per eseguire la migrazione dell'azienda e il relativo fabbisogno nel cloud o integrare piattaforme e servizi cloud con l'infrastruttura locale esistente nell'ambito della strategia IT complessiva.
  
## <a name="microsoft-hybrid-cloud"></a>Cloud ibrido Microsoft

Microsoft Hybrid Cloud è una serie di scenari aziendali che combinano una piattaforma Microsoft Cloud con un componente locale, ad esempio: 
  
- Ottenere risultati di ricerca dal contenuto sia in una farm di SharePoint locale sia in SharePoint online in Office 365.
    
- Un'app per dispositivi mobili in esecuzione in Azure che esegue una query in un archivio dati locale.
    
- Un carico di lavoro IT Intranet in esecuzione su macchine virtuali di Azure.
    
**Figura 1: componenti del cloud ibrido Microsoft**

![Componenti del cloud ibrido Microsoft](media/Hybrid-Poster/MS-Hybrid-Cloud.png)
  
Nella figura 1 vengono illustrati i componenti del cloud ibrido Microsoft, da una rete locale all'insieme dei servizi di Office 365, Azure Platform as a Service (PaaS) e Azure Infrastructure as a Service (IaaS) disponibili su Internet o in una connessione di ExpressRoute.
  
Poiché Microsoft ha la soluzione cloud più completa sul mercato, tra cui il software come servizio (SaaS), PaaS e IaaS, è possibile:
  
- Sfruttare gli investimenti locali esistenti durante la migrazione dei carichi di lavoro e delle applicazioni nel cloud.
    
- Includere scenari di cloud ibridi nei piani IT a lungo termine, ad esempio quando le normative o i criteri non consentono lo spostamento di dati o carichi di lavoro specifici nel cloud.
    
- Creare ulteriori scenari ibridi che includono più servizi cloud e piattaforme Microsoft.
    
Gli scenari per il cloud ibrido con i servizi cloud Microsoft variano a seconda della piattaforma.
  
- SaaS
    
    I servizi SaaS di Microsoft includono Office 365, Microsoft Intune e Microsoft Dynamics 365. Gli scenari con cloud ibrido con Microsoft SaaS uniscono questi servizi a servizi o applicazioni locali. Ad esempio, Exchange online in esecuzione in Office 365 può essere integrato con Skype for business 2019 distribuito in locale.
    
- PaaS di Azure
    
    I servizi di PaaS di Microsoft Azure consentono di creare applicazioni basate su cloud. Gli scenari con cloud ibrido con i servizi di Azure PaaS uniscono un'app PaaS di Azure con risorse o applicazioni locali. Ad esempio, un'app di Azure PaaS potrebbe eseguire una query sicura su un archivio dati locale per ottenere informazioni necessarie per la visualizzazione agli utenti di app per dispositivi mobili.
    
- IaaS di Azure
    
    I servizi di IaaS di Azure consentono di creare e gestire carichi di lavoro IT basati su server nel cloud, anziché in un datacenter locale. Gli scenari con cloud ibrido con i servizi di IaaS di Azure in genere sono costituiti da un carico di lavoro IT eseguito su macchine virtuali collegate in modo trasparente alla rete locale. Gli utenti locali non osserveranno la differenza.
    
## <a name="elements-of-hybrid-cloud"></a>Elementi del cloud ibrido

È necessario tenere conto degli elementi seguenti durante la pianificazione e l'implementazione di scenari basati su cloud ibrido con i servizi e le piattaforme cloud di Microsoft.
  
- Rete
    
    La rete per gli scenari di cloud ibrido include la connettività a piattaforme e servizi cloud Microsoft e larghezza di banda sufficiente per essere eseguita in carichi di picco. Per ulteriori informazioni, vedere [Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md).
    
- Identità
    
    Identity for SaaS and Azure PaaS gli scenari ibridi possono includere Azure AD come provider di identità comune, che può essere sincronizzato con i servizi di dominio Active Directory locali (AD DS) o federati con AD DS o con altri provider di identità. È inoltre possibile estendere l'infrastruttura di identità locale a Azure IaaS. Per ulteriori informazioni, vedere [identità cloud Microsoft per Enterprise Architects](microsoft-cloud-it-architecture-resources.md#identity).
    
- Sicurezza
    
    La sicurezza per gli scenari di cloud ibridi include la protezione e la gestione delle identità, la protezione dei dati, la gestione dei privilegi amministrativi, la sensibilizzazione alle minacce e l'implementazione di criteri di governance e sicurezza. Per ulteriori informazioni, vedere [sicurezza cloud Microsoft per Enterprise Architects](microsoft-cloud-it-architecture-resources.md#security).
    
- Gestione
    
    La gestione degli scenari di cloud ibridi include la possibilità di gestire le impostazioni, i dati, gli account, i criteri e le autorizzazioni e di monitorare l'integrità continua degli elementi dello scenario e le relative prestazioni. È inoltre possibile utilizzare lo stesso set di strumenti, ad esempio Systems Management Server, per la gestione delle macchine virtuali in Azure IaaS.
    
## <a name="see-also"></a>Vedere anche

[Cloud ibrido Microsoft per Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

