---
title: Office 365 Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Con Office 365 Multi-Geo si può espandere la propria presenza Office 365 a più paesi/aree geografiche.
ms.openlocfilehash: eb5c28131b7ac629d9acc607c777756b8825549c
ms.sourcegitcommit: 509bcf92580d7a0bcebbf6f1d10311d6b0014984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "31992836"
---
# <a name="office-365-multi-geo"></a>Office 365 Multi-Geo

Con Office 365 Multi-Geo l'organizzazione può espandere la presenza di Office 365 a più paesi/aree geografiche all'interno del tenant esistente. Invitare il team degli account Microsoft ad iscrivere la propria società multi-nazionale a Office 365 Multi-Geo.
  
Con Office 365 Multi-Geo, è possibile effettuare il provisioning e archiviare i dati a riposo nelle località geografiche scelte per soddisfare i requisiti di residenza dei dati e allo stesso tempo sbloccare lo sviluppo globale delle esperienze di produttività moderna per i dipendenti.

#### <a name="video-introducing-office-365-multi-geo"></a>Video: Introduzione a Office 365 Multi-Geo

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]

In un ambiente geografico Multi tenant di Office 365 è costituito da una posizione centralizzata (in cui l'abbonamento a Office 365 è stato originariamente provisioning) e uno o più località. In un tenant Multi-Geo, le informazioni su località geografiche, gruppi e le informazioni utente, vengono acquisite in Azure Active Directory (AAD). Poiché le informazioni del tenant sono acquisite in modo centralizzato e sincronizzate in ogni località geografica, la condivisione e le esperienze coinvolgono tutti gli utenti della società.

![Schermata della mappa multi-geo dall'interfaccia di amministrazione di SharePoint.](media/multi-geo-world-map.png)

Si noti che Office 365 Multi-Geo non è progettato principalmente per ottimizzare le prestazioni, ma per soddisfare i requisiti di residenza dei dati. Per informazioni sull'ottimizzazione delle prestazioni di Office 365, vedere [Pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) o contattare il gruppo di supporto.

## <a name="terminology"></a>Terminologia

Ecco i termini chiave utilizzati nella descrizione di Office 365 Multi-Geo:

- **Posizione centrale** - la posizione geografica in cui è stato effettuato originariamente il provisioning del tenant.
- **Amministratore geografico** - un amministratore che può gestire una o più posizioni satellite specificato.
- **Codice geografico** - un codice di tre lettere per una posizione geografica specificata.
- **Posizione geografica** - un'area geografica che può essere usata in un tenant multi-geo per ospitare dati, tra cui cassette postali di Exchange, OneDrive e siti di SharePoint.
- **Procedure dati posizione (PDL)** - proprietà dell’utente impostata dall'amministratore che indica la posizione geografica in cui si deve eseguire il provisioning della cassetta postale di Exchange di utenti e OneDrive. Il PDL determina anche se è stato effettuato il provisioning dei siti di SharePoint creati dall'utente.
- **Posizione satellite** - le posizioni geografiche in cui i carichi di lavoro di Office 365 consapevoli della propria ubicazione (Exchange, SharePoint e OneDrive) sono abilitati in un tenant multi-geo.
- **Tenant**: rappresentazione di un'organizzazione in Office 365 che in genere contiene uno o più domini associati ad essa (ad esempio contoso.com)

## <a name="office-365-multi-geo-availability"></a>Disponibilità di Office 365 Multi-Geo

Office 365 Multi-Geo è attualmente disponibile in questi paesi/aree geografiche:

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="getting-started"></a>Introduzione

Seguire questi semplici passaggi per iniziare con Multi-Geo:

1. Collaborare con il team responsabile dell'account per aggiungere _Multi-Geo Capabilities al piano di servizio di Office 365 _. Verranno fornite le procedure per aggiungere il numero di licenze necessarie. La funzionalità Multi-Geo Capabilities è disponibile per i clienti con un minimo di 2.500 abbonamenti a Office 365.

   Prima di iniziare a usare Office 365 Multi-Geo, Microsoft deve configurare il tenant di Exchange Online per il supporto Multi-Geo. La procedura di configurazione, da effettuare una sola volta, viene attivata dopo aver ordinato il piano di servizio *Funzionalità Multi-Geo di Office 365* e le licenze saranno visualizzate nel tenant. Una volta che vengono applicate le licenze Multi-Geo, si riceveranno notifiche nel [Centro messaggi di Office 365](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) e sarà quindi possibile iniziare la configurazione e l’uso della funzionalità Multi-Geo di Office 365.

2. Leggere [Pianificare l'ambiente Multi-Geo](plan-for-multi-geo.md).

3. Informazioni sull’[amministrazione di un ambiente Multi-Geo](administering-a-multi-geo-environment.md) e [ sul riscontro degli utenti sull’ambiente](multi-geo-user-experience.md).

4. Quando si è pronti per impostare su Office 365 Multi-Geo, [Configurare il tenant per Multi-Geo](multi-geo-tenant-configuration.md).

5. [Impostare la ricerca](configure-search-for-multi-geo.md).

## <a name="see-also"></a>Vedere anche

[Multi-Geo in Exchange Online e OneDrive](https://Aka.ms/GoMultiGeo)

[Multi-Geo Capabilities in OneDrive e SharePoint Online](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)

[Funzionalità Multi-Geo in Exchange Online](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-exchange-online)
