---
title: Infrastruttura IT ed esigenze di Contoso
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5d6a58b8-bec3-4629-9737-8733c7b7ec92
description: "Riepilogo: Comprendere la struttura di base di Contoso locale come la propria attività è necessario possono essere soddisfatti dall'offerte cloud di Microsoft e l'infrastruttura IT."
ms.openlocfilehash: e500aa1f3105c1e605d0d3c1d5f66651acb82b34
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915731"
---
# <a name="contosos-it-infrastructure-and-needs"></a>Infrastruttura IT ed esigenze di Contoso

 **Riepilogo:** Acquisire familiarità con la struttura di base di Contoso locale come la propria attività è necessario possono essere soddisfatti dall'offerte cloud di Microsoft e l'infrastruttura IT.
  
Contoso è in fase di transizione da un locale, l'infrastruttura IT centralizzata per uno inclusi cloud che incorpora carichi di lavoro per la produttività personale basato su cloud, le applicazioni e gli scenari ibridi.
  
## <a name="contosos-existing-it-infrastructure"></a>Infrastruttura IT esistente di Contoso

Contoso utilizza un principalmente centralizzato sull'infrastruttura IT, con centri dati applicazione nella sede centrale Parigi locale.
  
**Nella figura 1: Infrastruttura IT Contoso**

![Infrastruttura IT esistente di Contoso](media/Contoso-Poster/Existing-IT.png)
  
Nella figura 1 viene illustrata una sede con centri dati applicazione, DMZ e Internet.
  
In Contoso DMZ, fornire diversi set dei server:
  
- Accesso remoto per l'inoltro di intranet e del web Contoso per i propri colleghi in sede Paris.
    
- Hosting per il sito web pubblico Contoso, da cui i clienti possono ordinare prodotti, Web part o forniture.
    
- Per i partner di Contoso extranet per partner comunicazione e collaborazione di hosting.
    
## <a name="contosos-business-needs"></a>Esigenze aziendali di Contoso

Di seguito sono le esigenze aziendali di Contoso in ordine di priorità:
  
1. Rispettare le normative internazionali
    
    Per evitare multe e mantenere una buona relazioni con gli enti pubblici hanno locale, Contoso deve garantire la conformità alle normative di archiviazione e la crittografia dei dati.
    
2. Migliorare la gestione di fornitori e partner
    
    Partner extranet è durata e costosa da gestire. Contoso desidera sostituire con una soluzione basata su cloud che utilizza l'autenticazione federata.
    
3. Migliorare la produttività della forza lavoro mobile, la gestione dei dispositivi e accesso
    
    Forza lavoro mobile sola Contoso è l'espansione ed è la gestione dei dispositivi per garantire un accesso più efficiente alle risorse e protezione della proprietà intellettuale.
    
4. Riduzione dell'infrastruttura di accesso remoto
    
    Spostando le risorse normalmente utilizzate da dipendenti remoti nel cloud, Contoso verrà risparmiare denaro grazie alla riduzione dei costi di manutenzione e supporto per la propria soluzione di accesso remoto.
    
5. Implementare la scalabilità verso il basso centri dati locali
    
    Datacenter Contoso contenere centinaia di server, alcuni dei quali esegue legacy o archiviazione funzioni che distrarre il personale IT di gestione dei carichi di lavoro valore elevato per l'azienda.
    
6. Risorse di elaborazione e di archiviazione di implementare la scalabilità verticale per l'elaborazione di fine del quarto
    
    Proiezione di elaborazione e gestione dell'inventario e contabilità fine del quarto è necessario aumentare a breve termine nel server e archiviazione.
    
## <a name="mapping-contosos-business-needs-to-microsofts-cloud-offerings"></a>Mapping aziendali di Contoso è necessario offerte cloud di Microsoft

Basato su un'analisi delle offerte cloud di Microsoft, Contoso del reparto IT determinato il mapping seguente:
  
|**Software come servizio (SaaS)**|**Piattaforma as a Service (PaaS Azure)**|**Infrastructure as a Service (Azure IaaS)**|
|:-----|:-----|:-----|
|**Office 365:** Applicazioni di principale per la produttività personale e di gruppo nel cloud. <br/> Le esigenze aziendali: 1 3 5  <br/> |Ospitare vendite e supporto di documenti e informazioni sui sistemi utilizzando applicazioni basate su cloud.  <br/> Esigenza azienda: 3  <br/> |Spostare i sistemi legacy e archiviare i server basati su cloud.  <br/> Esigenza azienda: 5  <br/> |
|**Dynamics 365:** Utilizzare la gestione di fornitori e clienti basata su cloud. Rimuovere partner extranet nella DMZ.<br/> Esigenza azienda: 2  <br/> |Applicazioni per dispositivi mobili sono basati sul cloud, anziché Parigi basate su Data Center.  <br/> Le esigenze aziendali: 4 3  <br/> |Eseguire la migrazione dei dati da centri dati locali e le applicazioni di utilizzo poco.  <br/> Esigenza azienda: 5  <br/> |
|**Intune/EMS:** Gestire iOS e dispositivi Android. <br/> Esigenza azienda: 3  <br/> ||Aggiungere server temporanei e archiviazione per esigenze di elaborazione di fine del trimestre.  <br/> Esigenza azienda: 6  <br/> |
   
## <a name="see-also"></a>Vedere anche

[Contoso nel Microsoft Cloud](contoso-in-the-microsoft-cloud.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT](https://sway.com/FJ2xsyWtkJc2taRD)


