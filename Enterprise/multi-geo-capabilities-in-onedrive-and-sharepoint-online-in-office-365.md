---
title: Multi-Geo Capabilities in OneDrive e SharePoint Online in Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Espandere la presenza di Office 365 a più aree geografiche con funzionalità multi-geo in OneDrive e SharePoint Online.
ms.openlocfilehash: 7387b267cbc925916b600a112d6911c97a971c36
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a>Multi-Geo Capabilities in OneDrive e SharePoint Online in Office 365

Con Multi-Geo Capabilities in SharePoint Online e OneDrive, l'organizzazione può espandere la presenza di Office 365 a più aree geografiche e/o paesi all'interno del tenant esistente. Al momento questa funzionalità è disponibile in anteprima. Invitare il team degli account Microsoft ad iscrivere la propria società multi-nazionale all'anteprima di OneDrive Multi-Geo.
  
Con OneDrive Multi-Geo, è possibile effettuare il provisioning e archiviano i dati statici nelle posizioni geo selezionata per soddisfare i requisiti di residenza dati e contemporaneamente sbloccare il (in inglese) globale da esperienze moderno produttività della forza lavoro consentita.
  
Ecco come possono utilizzare la funzionalità multi-geo nell'organizzazione:
  
- Fungere da una impresa connessa globale con un singolo tenant di Office 365 che distribuisce in più località geografiche.
    
- Soddisfare i requisiti di residenza dei dati mediante la creazione e l'hosting dei dati a riposo all'interno di località geografiche specifiche.
    
- Offrire agli utenti satellite le stesse esperienze di produttività moderna degli utenti in località centrali.
    
- Consentire agli utenti di spostarsi tra le località geografiche al cambiamento di ruolo, mentre l'accesso al contenuto viene conservato inalterato.
    
- Personalizzare i criteri di condivisione per ogni località geografica e i criteri di prevenzione della perdita dei dati per ogni sito.
    
- Designare responsabili di eDiscovery per località geografica e consentire che regolino i casi personalizzati per tale località.
    
- Scegliere spazi dei nomi dell’URL univoci (ad esempio, ContosoEUR.sharepoint.com) per le località geografiche aggiuntive.
    
- Consolidare i dati in locale dell’area nel tenant multi-geo di Office 365.
    
In una configurazione multi-geo tenant Office 365 è costituita da una posizione centralizzata (noto anche come il percorso predefinito) e uno o più percorsi geo satellitari. Il concetto principale di multi-geo è un singolo tenancy verrà estendersi su una più località geografica. In un tenant multi-geo, le informazioni sui percorsi geo, gruppi e informazioni utente, sono gestite in Azure Active Directory (AAD). Dal momento che le informazioni di tenant gestite centralmente e sincronizzate in ogni località geografica, condivisione ed esperienze che coinvolgono tutti gli utenti della società e contengono consapevolezza globale.
  
## <a name="sample-multi-geo-tenant-configuration"></a>Configurazione di esempio multi-geo tenant

Con un tenant con posizioni geografiche diverse, Contoso, con una località centrale del Nord America, può espandere fino a località geografiche satelliti in Europa e Australia entro i limiti dell’organizzazione singola di Contoso.com. Gli utenti con un percorso dati preferito impostato su Europa avranno OneDrive in Europa, mentre gli utenti con un percorso dati preferito in Nord America avranno OneDrive negli Stati Uniti.
  
![Mappa del mondo, che mostra geo percorsi per Contoso e gli altri percorsi geo disponibili](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a>Ottenere le funzionalità di Multi-Geo con tre semplici passaggi

Configurare multi-geo è semplice:
  
1. Collaborare con il team amministrativo per aggiungere il piano di servizio _Multi-Geo disponibili in Office 365_ . Sono contenute informazioni per aggiungere il numero di licenze necessarie.
    
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

Per iniziare a OneDrive per Business Multi-Geo, il primo passaggio consiste nel [pianificare il OneDrive for Business Multi-Geo ambiente](plan-for-multi-geo.md). Avanti, [informazioni sull'amministrazione di un ambiente multi-geo](administering-a-multi-geo-environment.md) e [come gli utenti osserveranno un ambiente multi-geo](multi-geo-user-experience.md). Quando si è pronti a impostare OneDrive per Business Multi-Geo, [configurare il tenant per multi-geo](multi-geo-tenant-configuration.md), quindi [spostare tutti i siti OneDrive esistenti per la nuova posizione geografica](move-onedrive-between-geo-locations.md) e [configurare la ricerca](configure-search-for-multi-geo.md).
