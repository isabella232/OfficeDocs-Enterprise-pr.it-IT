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
description: "Riepilogo: comprendere l'architettura ibrida e gli scenari per le offerte cloud di Microsoft come servizio (PaaS) in Azure."
ms.openlocfilehash: f4d90d51a7627063fae6fd168681bdf96cb4d6bc
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491200"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a>Scenari cloud ibridi per Azure PaaS

 **Riepilogo:** Comprendere l'architettura ibrida e gli scenari per le offerte cloud basate su PaaS (Platform as a Service) di Microsoft in Azure.
  
Combinare dati locali o risorse di elaborazione con applicazioni nuove o convertite in esecuzione in PaaS di Azure, che possono sfruttare le prestazioni, l'affidabilità e la scalabilità del cloud e fornire un supporto migliore per gli utenti di dispositivi mobili. 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a>Architettura di scenari ibridi di PaaS di Azure

Nella figura 1 viene illustrata l'architettura di scenari ibridi basati su Microsoft PaaS in Azure.
  
**Figura 1: scenari ibridi basati su Microsoft PaaS in Azure**

![Scenari ibridi basati su Microsoft PaaS in Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
Per ogni livello dell'architettura:
  
- App e scenari
    
    Un'applicazione PaaS ibrida viene eseguita in Azure e utilizza risorse di calcolo o di archiviazione locali.
    
- Identità
    
    È costituito dalla sincronizzazione della directory o dalla Federazione con un provider di identità di terze parti.
    
- Rete
    
    È costituito dalla pipe Internet esistente o da una connessione ExpressRoute con peering pubblico a Azure PaaS. È necessario includere un metodo per l'applicazione di Azure PaaS per accedere alla risorsa di archiviazione o computo locale.
    
- Locale
    
    È costituito da un'infrastruttura di identità e sicurezza e da applicazioni line-of-business (LOB) esistenti o da server di database, che un'applicazione di PaaS di Azure può accedere in modo sicuro.
    
## <a name="azure-paas-hybrid-application"></a>Applicazione ibrida di PaaS di Azure

Nella figura 2 viene illustrata la configurazione di un'applicazione ibrida in esecuzione in Azure.
  
**Figura 2: applicazione ibrida basata su PaaS di Azure**

![Applicazione ibrida basata su PaaS di Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
Nella figura 2, una rete locale ospita l'archiviazione o le app nei server e una DMZ contenente un server proxy. È collegato ai servizi di PaaS di Azure su Internet o con una connessione ExpressRoute.
  
Un'organizzazione può rendere disponibili le proprie risorse di calcolo o di archiviazione per l'applicazione ibrida di Azure PaaS per:
  
- Hosting della risorsa nei server della DMZ.
    
- Hosting di un server proxy inverso nella DMZ, che consente le richieste autenticate, in ingresso e basate su HTTPS alla risorsa che si trova in locale.
    
L'app di Azure può utilizzare le credenziali da:
  
- Azure AD, che può essere sincronizzato con il provider di identità locale, ad esempio servizi di dominio Active Directory (AD DS).
    
- Un provider di identità di terze parti.
    
### <a name="example-azure-paas-hybrid-application"></a>Esempio di applicazione ibrida di Azure PaaS

Nella figura 3 viene mostrato un esempio di applicazione ibrida in esecuzione in Azure.
  
**Figura 3: un'applicazione ibrida basata su Azure PaaS di esempio**

![Esempio di un doma ibrido basato su Azure PaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
Nella figura 3, una rete locale ospita un'app LOB. Azure PaaS ospita un'app per dispositivi mobili personalizzata. Uno smartphone su Internet accede all'app per dispositivi mobili personalizzata in Azure, che invia le richieste di dati all'app LOB locale.
  
In questo esempio, l'applicazione ibrida di Azure PaaS è un'app per dispositivi mobili personalizzata che fornisce informazioni di contatto aggiornate sui dipendenti. Lo scenario ibrido end-to-end è costituito da:
  
- App per smartphone che richiede l'esecuzione di credenziali convalidate e locali.
    
- Un'app per dispositivi mobili personalizzata in esecuzione in Azure PaaS, che richiede informazioni su specifici dipendenti in base alle query provenienti dall'app smartphone di un utente.
    
- Un server proxy inverso nella DMZ che convalida l'app per dispositivi mobili personalizzata e inoltra la richiesta.
    
- Una farm di server applicazioni LOB che assiste la richiesta di contatto, in base alle autorizzazioni dell'account dell'utente.
    
Poiché il provider di identità locale è stato sincronizzato con Azure AD, sia l'app per dispositivi mobili personalizzata che l'app LOB possono convalidare il nome dell'account dell'utente che richiede la richiesta.
  
## <a name="see-also"></a>Vedere anche

[Cloud ibrido Microsoft per Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Risorse sull'architettura IT di Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

