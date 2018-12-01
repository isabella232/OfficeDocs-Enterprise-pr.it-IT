---
title: Architettura degli scenari cloud ibridi Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: "Riepilogo: Comprendere l'architettura di ibrida offerte cloud di Microsoft."
ms.openlocfilehash: 74fc046d1f60b29338e7f12184dec018538ba9da
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123393"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a>Architettura degli scenari cloud ibridi Microsoft

 **Riepilogo:** Acquisire familiarità con l'architettura di ibrida offerte cloud di Microsoft.
  
Utilizzare un approccio dell'architettura per pianificare e implementare scenari basati su cloud ibrida con servizi cloud Microsoft e piattaforme.
  
**Nella figura 1: Microsoft ibrida cloud stack**

![Stack cloud ibrido Microsoft](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
Nella figura 1 viene illustrato lo stack di cloud Microsoft ibrida e il relativo livello, che comprendono locale, rete, identità, applicazioni e gli scenari e la categoria del servizio cloud (SaaS Microsoft Azure PaaS e Azure PaaS).
  
Il livello applicazioni e gli scenari ha di scenari basati su cloud ibrida specifica che sono descritti negli articoli aggiuntivi di questo modello. L'identità, rete e locali livelli possono essere comuni per le categorie di servizio cloud (SaaS, PaaS o PaaS).
  
- Locale
    
    Infrastruttura locale per gli scenari ibridi può includere i server per SharePoint, Exchange, Skype per le aziende e applicazioni line of business. Inoltre possibile includere archivi dati (database, elenchi, i file). Senza connessioni ExpressRoute, è necessario consentire l'accesso per gli archivi dati locali tramite un proxy inverso o rendere il server o i dati accessibile nella DMZ o extranet.
    
- Rete
    
    Sono disponibili due opzioni per la connettività a Microsoft cloud piattaforme e servizi: il canale Internet esistente ed ExpressRoute. Utilizzare una connessione ExpressRoute se le prestazioni prevedibile sono importanti. È possibile utilizzare una connessione ExpressRoute per la connessione direttamente a Microsoft SaaS services (Office 365 e Dynamics 365), servizi di Azure PaaS e servizi di Azure IaaS.
    
- Identità
    
    Per l'infrastruttura di identità cloud, esistono due modi per accedere, a seconda della piattaforma Microsoft cloud. Per SaaS e Azure PaaS, integrare l'infrastruttura di identità in locale con Azure Active Directory o la federazione con i provider di identità locale dell'infrastruttura o di terze parti dell'identità. Per le macchine virtuali in esecuzione in Azure, è possibile estendere l'infrastruttura di identità in locale, ad esempio Windows Server Active Directory, per le reti virtuali (VNets) in cui si trovano nelle macchine virtuali.
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a>Scenari basati su cloud ibrida per il processo di adozione cloud tre fasi

Molte aziende, tra cui Microsoft, utilizzano un approccio tre fasi per adottando nel cloud. Scenari basati su cloud ibrida possono avere un ruolo di ogni fase.
  
1. Spostare i carichi di lavoro per la produttività SaaS
    
    Per la produttività dei carichi di lavoro che sono attualmente o deve rimanere in locale, scenari ibridi consentono loro di essere integrate con le relative controparti cloud.
    
2. Sviluppare applicazioni nuove e moderne in Azure PaaS
    
    Applicazioni ibrida PaaS Azure in modo sicuro utilizzo delle risorse di archiviazione o server locale.
    
3. Spostare le applicazioni esistenti per Azure IaaS
    
    Per scenari ascensore MAIUSC e compilazione nel cloud, le applicazioni basate su server in esecuzione su macchine virtuali di Azure offrono il provisioning di tipo semplice e la scala.
    
## <a name="see-also"></a>Vedere anche

[Cloud ibrido Microsoft per Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

