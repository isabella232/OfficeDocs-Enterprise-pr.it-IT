---
title: Scenari cloud ibridi per Azure PaaS
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
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: 'Riepilogo: Informazioni su architettura ibrida e gli scenari per la piattaforma Microsoft come servizio (PaaS)-basato su cloud offerte in Azure.'
ms.openlocfilehash: e536d81b6b14b05bef49d7c91b0404faec64303b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123333"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a>Scenari cloud ibridi per Azure PaaS

 **Riepilogo:** Acquisire familiarità con l'architettura ibrida e gli scenari per la piattaforma Microsoft come servizio (PaaS)-basato su cloud offerte in Azure.
  
Combinare dati locali o le risorse di elaborazione con nuove o convertire applicazioni in esecuzione in Azure PaaS, che possono trarre vantaggio cloud prestazioni, l'affidabilità e la scala e fornire supporto migliorato per gli utenti mobili. 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a>Architettura di uno scenario ibrido PaaS Azure

Nella figura 1 illustra l'architettura di scenari basati su PaaS ibridi Microsoft in Azure.
  
**Nella figura 1: Scenari di ibrida basata su PaaS Microsoft in Azure**

![Scenari ibridi Microsoft basati su PaaS in Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
Per ogni livello dell'architettura:
  
- App e scenari
    
    Un ambiente ibrido applicazione PaaS viene eseguito in Azure e utilizza risorse compute o l'archiviazione in locale.
    
- Identità
    
    È costituita dalla sincronizzazione delle directory o la federazione con un provider di identità di terze parti.
    
- Rete
    
    È costituita dal canale Internet esistente o una connessione ExpressRoute con peering pubblica per Azure PaaS. È necessario includere un modo per l'applicazione PaaS Azure accedere alla risorsa compute o l'archiviazione in locale.
    
- Locale
    
    È costituita da identità e la protezione dell'infrastruttura e line-of business (LOB) applicazioni o server di database, un'applicazione di Azure PaaS può accedere in modo sicuro esistenti.
    
## <a name="azure-paas-hybrid-application"></a>Applicazione di ibrida PaaS Azure

Nella figura 2 viene illustrata la configurazione di un'applicazione ibrida in esecuzione in Azure.
  
**Nella figura 2: Applicazione ibrida basata su PaaS Azure**

![Applicazione ibrida basta su PaaS di Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
Nella figura 2, una rete locale ospita archiviazione o applicazioni server e una DMZ contenente un server proxy. Si connette ai servizi di Azure PaaS tramite Internet o con una connessione ExpressRoute.
  
Un'organizzazione, è possibile effettuare le relative risorse compute o l'archiviazione disponibili per l'applicazione ibrida PaaS Azure per:
  
- Hosting delle risorse nei server DMZ.
    
- Hosting di un server proxy inverso nella DMZ, che consente le richieste di utenti autenticate, in ingresso, basato su HTTPS per la risorsa che si trova in locale.
    
L'app Azure è possibile utilizzare le credenziali da:
  
- Azure Active Directory, che possono essere sincronizzati con il provider di identità in locale, ad esempio Windows Server Active Directory.
    
- Un provider di identità di terze parti.
    
### <a name="example-azure-paas-hybrid-application"></a>Applicazione di esempio Azure PaaS ibrida

Nella figura 3 viene mostrata un'applicazione di ibrida di esempio in esecuzione in Azure.
  
**Figura 3: Un esempio di un'applicazione basata su Azure PaaS ibrida**

![Un esempio di applicazione ibrida di Azure basata su PaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
Nella figura 3, un host di rete locale un LOB App Azure PaaS ospita un'applicazione personalizzata per dispositivi mobili. Un dispositivo smartphone su Internet accede l'app personalizzata per dispositivi mobili in Azure, che invia le richieste di dati per l'applicazione LOB locale.
  
In questo esempio Azure PaaS ibrida applicazione sia un'app per dispositivi mobili personalizzata che fornisce informazioni aggiornate sui contatti sui dipendenti. Lo scenario ibrido end-to-end è costituito da:
  
- Una smartphone app che richiede la convalida, le credenziali locali per l'esecuzione.
    
- Un'applicazione personalizzata per dispositivi mobili in esecuzione in Azure PaaS, che richiede informazioni sui dipendenti specifici in base alle query da app smartphone dell'utente.
    
- Un server proxy inverso nella DMZ che convalida l'app per dispositivi mobili personalizzato e inoltra la richiesta.
    
- Una farm di server applicazioni LOB che gestisce la richiesta di contatto, soggette alle autorizzazioni dell'account dell'utente.
    
Dal momento che il provider di identità locale è stato sincronizzato con Azure Active Directory, l'app per dispositivi mobili personalizzato e le applicazioni LOB possano convalidare il richiedente nome dell'account utente.
  
## <a name="see-also"></a>Vedere anche

[Cloud ibrido Microsoft per Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

