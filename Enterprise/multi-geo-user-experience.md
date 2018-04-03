---
title: Esperienza utente in un ambiente multgeo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Per conoscere l'esperienza utente di SharePoint e OneDrive in un ambiente multi-geo.
ms.openlocfilehash: 91837883ef7c970674a500afa4fda9adfafc6d5b
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a>Esperienza utente in un ambiente multi-geo

Ecco cosa gli utenti visualizzeranno in una configurazione Multi-Geo OneDrive:

#### <a name="users-onedrive-for-business-location"></a>OneDrive dell'utente per sede aziendale

Gli utenti potranno loro OneDrive for Business eseguito il provisioning nel relativo percorso dati preferita. Se un utente accede a un URL OneDrive che contiene una posizione geografica non corretta (ad esempio un segnalibro da una posizione geografica precedente), vengono reindirizzate automaticamente alla OneDrive nella posizione geografica appropriata.

#### <a name="sharing"></a>Condivisione

L'esperienza di selezione utenti Mostra tutti gli utenti indipendentemente dalla posizione geografica. Ciò consente di condividere con altri utenti nella loro geo stesso o in qualsiasi altro della località geografica del tenant. Contenuto disponibile nei geo diversa posizioni verranno visualizzata nella visualizzazione **condiviso con Me** in OneDrive dell'utente for Business ed sono accessibile con Single Sign-On esperienza indipendentemente dalla quale ubicazione geografica è ospitata in.

#### <a name="office-applications"></a>Applicazioni di Office

Applicazioni di Office come Word, Excel e PowerPoint rileva automaticamente il corretto OneDrive for Business geo-percorso per ciascun utente al momento dell'accesso. Gli utenti non devono immettere l'URL geo specifiche per i OneDrive.

#### <a name="onedrive-for-business-sync-client"></a>OneDrive for Business Client di sincronizzazione

OneDrive for Business sincronizzazione Client (versione 17.3.6943.0625 e versioni successive) rileva automaticamente il corretto OneDrive per la posizione geografica Business per l'utente.

#### <a name="office-365-app-launcher"></a>Avvio app di Office 365

Il servizio di avvio di app è Multi-Geo e otterranno indicazioni ogni tessera alla posizione geografica appropriato del carico di lavoro. I punti di sezioni OneDrive nella posizione corretta geo cui è ospitato libreria di OneDrive dell'utente, mentre le sezioni di SharePoint saranno posiziona tutti gli utenti nella posizione centrale come siti del team sono ospitati disponibili.

#### <a name="delve-user-profiles"></a>Approfondire profili utente

Informazioni dei profili utente sono gestite nella posizione geografica dell'utente. Quando si seleziona un utente, si verrà indirizzati alla posizione geografica appropriato per l'utente, dove verranno visualizzati i relativi dettagli completa dei profili.

Se Delve è disattivata, verrà visualizzato il profilo classico esperienza in SharePoint, non ovvero multi-geo.

#### <a name="delve"></a>Delve

Per gli utenti di Office 365 che si trovano in istanze satellitari, approfondire Multi-Geo è supportato con le limitazioni Delve non consente di collegarsi al post di blog di SharePoint scritti da parte di utenti in altre aree, solo per i siti blog di SharePoint.

#### <a name="search"></a>Ricerca

Ogni località geografica ha indice di ricerca e Centro ricerche. Quando un utente esegue la ricerca, la query viene inviata a tutti i percorsi geo e i risultati restituiti vengono uniti e quindi classificati in modo che l'utente ottiene risultati unificati. Gli utenti di ottenere i risultati da tutti i percorsi geo indipendentemente dalla posizione geografica. Per informazioni dettagliate, vedere [Configurare la ricerca di OneDrive per Business Multi-Geo](configure-search-for-multi-geo.md) .

Sono supportati i client di ricerca seguenti:

-   OneDrive for Business

-   Delve

-   Home page di SharePoint

-   Centro ricerche

-   Applicazioni di ricerca personalizzate che utilizzano l'API di ricerca di SharePoint

#### <a name="onedrive-ios-and-android"></a>IOS OneDrive e Android 

Il iOS OneDrive e App per dispositivi mobili Android visualizzerà i file di OneDrive e file condivisi con l'utente indipendentemente dalla posizione geografica. Ricerca dalle App per dispositivi mobili OneDrive consentirà di visualizzare risultati pertinenti da tutti i percorsi geo. Scaricare la versione più recente di queste applicazioni.

Per ulteriori informazioni, vedere Utilizzo di [OneDrive su iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) e [Utilizzare OneDrive per Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) .

#### <a name="teams-experience"></a>Esperienza di team

I team è multi-geo. Indipendentemente dalla posizione geografica dell'utente vengono visualizzati i file di OneDrive e visualizzati di recente. @ menzioni lavoro con gli utenti da tutti i percorsi di livello geografico.
