---
title: Architettura degli scenari cloud ibridi Microsoft
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
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: "Riepilogo: informazioni sull'architettura delle offerte cloud ibride di Microsoft."
ms.openlocfilehash: 513e45629a7092803cc644241d84985a37e43876
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068322"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a>Architettura degli scenari cloud ibridi Microsoft

 **Riepilogo:** Comprendere l'architettura delle offerte cloud ibride di Microsoft.
  
Utilizzare un approccio architettonico per pianificare e implementare scenari basati su cloud ibrido con i servizi cloud e le piattaforme Microsoft.
  
**Figura 1: stack cloud ibrido Microsoft**

![Stack del cloud ibrido Microsoft](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
Nella figura 1 viene mostrato lo stack del cloud ibrido Microsoft e il relativo layer, che include i locali, la rete, l'identità, le app e gli scenari e la categoria del servizio cloud (Microsoft SaaS, Azure PaaS e Azure PaaS).
  
Il livello Apps and Scenarios contiene gli scenari specifici del cloud ibrido descritti in dettaglio negli articoli aggiuntivi di questo modello. I livelli Identity, Network e on-premises possono essere comuni alle categorie del servizio cloud (SaaS, PaaS o PaaS).
  
- Locale
    
    L'infrastruttura locale per gli scenari ibridi può includere server per SharePoint, Exchange, Skype for business e applicazioni line-of-business. È inoltre possibile includere archivi dati (database, elenchi, file). Senza le connessioni di ExpressRoute, è necessario consentire l'accesso agli archivi dati locali tramite un proxy inverso o rendendo il server o i dati accessibili nella DMZ o nell'Extranet.
    
- Rete
    
    Sono disponibili due opzioni per la connettività alle piattaforme e ai servizi cloud Microsoft: la tubazione Internet esistente e la ExpressRoute. Utilizzare una connessione ExpressRoute se sono importanti le prestazioni prevedibili. È possibile utilizzare una connessione ExpressRoute per connettersi direttamente ai servizi SaaS di Microsoft (Office 365 e Dynamics 365), ai servizi di PaaS di Azure e ai servizi di IaaS di Azure.
    
- Identità
    
    Per l'infrastruttura di identità cloud, esistono due modi per andare, a seconda della piattaforma cloud Microsoft. Per SaaS e Azure PaaS, integrare l'infrastruttura di identità locale con Azure AD o con la Federazione con l'infrastruttura di identità locale o con i provider di identità di terze parti. Per le macchine virtuali in esecuzione in Azure, è possibile estendere l'infrastruttura di identità locale, ad esempio servizi di dominio Active Directory, alle reti virtuali (reti virtuali) in cui risiedono le macchine virtuali.
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a>Scenari di cloud ibridi per il processo di adozione di cloud in tre fasi

Molte imprese, tra cui quelle di Microsoft, utilizzano un approccio trifasico per l'adozione del cloud. Gli scenari di cloud ibridi possono svolgere un ruolo in ogni fase.
  
1. Spostamento dei carichi di lavoro di produttività in SaaS
    
    Per i carichi di lavoro di produttività che attualmente sono o devono rimanere in locale, gli scenari ibridi consentono di integrarli con le rispettive controparti cloud.
    
2. Sviluppare applicazioni nuove e moderne in Azure PaaS
    
    Le applicazioni ibride di PaaS di Azure possono sfruttare in modo sicuro il server locale o le risorse di archiviazione.
    
3. Spostare le applicazioni esistenti in Azure IaaS
    
    Per gli scenari di Lift-and-Shift e Build-in-the-cloud, le applicazioni basate su server in esecuzione nelle macchine virtuali di Azure offrono un semplice provisioning e ridimensionamento.
    
## <a name="see-also"></a>Vedere anche

[Cloud ibrido Microsoft per Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

