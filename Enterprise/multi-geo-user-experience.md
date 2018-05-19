---
title: Esperienza utente in ambiente multi-geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Informazioni sull'esperienza utente riguardo SharePoint e OneDrive in ambiente multi-geografico.
ms.openlocfilehash: 3c7e4b6802bddc78db016c9c282f5add0c71c491
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a>Esperienza utente in ambiente multi-geografico.

Ecco cosa gli utenti visualizzeranno in una configurazione OneDrive Multi-Geo:

#### <a name="users-onedrive-for-business-location"></a>Posizione di OneDrive for Business dell'utente

Gli utenti disporranno di OneDrive for Business fornito nel percorso dati preferito. Se un utente accede a un URL OneDrive che contiene una posizione geografica errata (come un segnalibro da una precedente posizione geografica), viene automaticamente reindirizzato a OneDrive nella posizione geografica appropriata.

#### <a name="sharing"></a>Condivisione

L'esperienza di Selezione utenti mostra tutti gli utenti indipendentemente dalla posizione geografica. Questo consente all'utente di condividere contenuti con un altro utente nella stessa posizione geografica o in una qualsiasi altra posizione geografica del tenant. Verrà visualizzato il contenuto da posizioni geografiche diverse nella visualizzazione **Condivisi con me** dell’utente in OneDrive for Business e questo sarà accessibile con l'esperienza Single Sign-On indipendentemente dalla posizione geografica in cui è ospitato.

#### <a name="office-applications"></a>Applicazioni di Office

Le applicazioni Office come Word, Excel e PowerPoint rileveranno automaticamente la posizione geografica corretta di OneDrive for Business per ciascun utente al momento dell'accesso. Non è necessario immettere l'URL geo-specifico per OneDrive.

#### <a name="onedrive-for-business-sync-client"></a>Client di sincronizzazione OneDrive for Business

Il client di sincronizzazione OneDrive for Business (versione 17.3.6943.0625 e successive) rileverà automaticamente la posizione geografica corretta di OneDrive for Business per l'utente.

#### <a name="office-365-app-launcher"></a>Avvio app di Office 365

Il servizio avvio app ha funzionalità Multi-Geo e indirizzerà direttamente ciascun riquadro alla corretta posizione geografica del carico di lavoro. I riquadri di OneDrive indicano la corretta posizione geografica in cui si trova la raccolta OneDrive dell'utente, mentre il riquadro di SharePoint indicherà a tutti gli utenti la posizione centrale, poiché ancora ospita i siti del team.

#### <a name="delve-user-profiles"></a>Profili utente Delve

Le informazioni sul profilo utente sono gestite nella posizione geografica dell'utente. Quando si seleziona un utente, si verrà indirizzati alla posizione geografica corretta per l'utente, in cui sarà possibile visualizzare i dettagli del profilo completo.

Se Delve è disattivato, verrà visualizzata l'esperienza del profilo classico in SharePoint, il quale non ha funzionalità Multi-Geo.

#### <a name="delve"></a>Delve

Delve Multi-Geo è supportato per gli utenti di Office 365 nelle istanze satellite, con la limitazione che Delve consente il collegamento solo ai siti di blog di SharePoint di tali utenti e non ai post di blog di SharePoint scritti dagli utenti in altre regioni.

#### <a name="search"></a>Cerca

Ogni posizione geografica ha un proprio indice di ricerca e Centro ricerche. Quando si esegue la ricerca, la query viene inviata a tutte le posizioni geografiche e i risultati restituiti vengono uniti e quindi classificati in modo che l'utente ottenga risultati unificati. Gli utenti ottengono risultati da tutte le località geografiche indipendentemente dalla posizione geografica. Vedere [Configurare la ricerca di OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) per ulteriori dettagli.

Di seguito sono elencati i client di ricerca supportati:

-   OneDrive for Business

-   Delve

-   Home page di SharePoint

-   Centro ricerche

-   Applicazioni di ricerca personalizzate che utilizzano l'API ricerca SharePoint

#### <a name="onedrive-ios-and-android"></a>OneDrive per iOS e Android 

L'app OneDrive per dispositivi mobili iOS e Android illustra i file di OneDrive e i file condivisi con l'utente indipendentemente dalla posizione geografica. La ricerca dalle app OneDrive mostra risultati pertinenti da tutte le posizioni geografiche. Scaricare la versione più recente di tali applicazioni.

Vedere [Usare OneDrive in iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) e [Usare OneDrive in Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) per ulteriori informazioni.

#### <a name="teams-experience"></a>Funzionalità di Teams

Teams ha funzionalità multi-geo. I file di OneDrive e i file visualizzati recentemente.vengono mostrati indipendentemente dalla posizione geografica dell'utente. @ fa riferimento all’utilizzo con utenti da tutte le posizioni geografiche.
