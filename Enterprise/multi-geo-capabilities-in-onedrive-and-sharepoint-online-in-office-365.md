---
title: Multi-Geo Capabilities in OneDrive e SharePoint Online in Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Expand your Office 365 presence to multiple geographic regions with multi-geo capabilities in OneDrive and SharePoint Online.
ms.openlocfilehash: 3f72158fe05aadfe8a08a5520bf65cd2d0aaa1c6
ms.sourcegitcommit: a81d08c7e8771cb2c232435971e3169d4f7428dc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a>Multi-Geo Capabilities in OneDrive e SharePoint Online in Office 365

With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.
  
With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.
  
Here's how multi-geo features can benefit your organization:
  
- Fungere da una impresa connessa globale con un singolo tenant di Office 365 che distribuisce in più località geografiche.
    
- Soddisfare i requisiti di residenza dei dati mediante la creazione e l'hosting dei dati a riposo all'interno di località geografiche specifiche.
    
- Offrire agli utenti satellite le stesse esperienze di produttività moderna degli utenti in località centrali.
    
- Consentire agli utenti di spostarsi tra le località geografiche al cambiamento di ruolo, mentre l'accesso al contenuto viene conservato inalterato.
    
- Personalizzare i criteri di condivisione per ogni località geografica e i criteri di prevenzione della perdita dei dati per ogni sito.
    
- Designare responsabili di eDiscovery per località geografica e consentire che regolino i casi personalizzati per tale località.
    
- Scegliere spazi dei nomi dell’URL univoci (ad esempio, ContosoEUR.sharepoint.com) per le località geografiche aggiuntive.
    
- Consolidare i dati in locale dell’area nel tenant multi-geo di Office 365.
    
In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.
  
## <a name="sample-multi-geo-tenant-configuration"></a>Sample multi-geo tenant configuration

Con un tenant con posizioni geografiche diverse, Contoso, con una località centrale del Nord America, può espandere fino a località geografiche satelliti in Europa e Australia entro i limiti dell’organizzazione singola di Contoso.com. Gli utenti con un percorso dati preferito impostato su Europa avranno OneDrive in Europa, mentre gli utenti con un percorso dati preferito in Nord America avranno OneDrive negli Stati Uniti.
  
![Map of the world, showing geo locations for Contoso and other available geo locations](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a>Ottenere le funzionalità di Multi-Geo con tre semplici passaggi

Configurare multi-geo è semplice:
  
1. Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.
    
2. Aggiungere le località satellite.
    
3. Configurare gli account utente per la località appropriata.
    
## <a name="multi-geo-status-and-availability"></a>Disponibilità e stato di Multi-Geo

OneDrive Multi-Geo è attualmente disponibile in queste aree geografiche e paesi:
  
- Asia-Pacifico
    
- Australia
    
- Canada
    
- Unione Europea (EMEA)
    
- Giappone
    
- Regno Unito
    
- Stati Uniti (Nord America)
    
- Corea
      
Prossime località geografiche:
  
- Francia
- India
    
## <a name="getting-started"></a>Introduzione

To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).
