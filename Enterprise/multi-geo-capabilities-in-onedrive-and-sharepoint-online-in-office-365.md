---
title: Multi-Geo Capabilities in OneDrive e SharePoint Online
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Con Multi-Geo Capabilities in OneDrive Online l'organizzazione può espandere la propria presenza Office 365 a più paesi/aree geografiche.
ms.openlocfilehash: 15dcb44943fa1bf331ef6260946f7c3a632d3c4a
ms.sourcegitcommit: dffbcfb1cbc9776a29229a787c1eab4192e55cff
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2019
ms.locfileid: "30948587"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a>Multi-Geo Capabilities in OneDrive e SharePoint Online

La funzionalità Multi-Geo in OneDrive e SharePoint Online consente di controllare il paese/area geografica in cui sono archiviate le risorse condivise, ad esempio dei team di SharePoint e delle cassette postali di gruppo di Office 365.

Ogni utente, ogni cassetta postale di gruppo e ogni sito SharePoint ha una PDL (Preferred Data Location, posizione dei dati preferita), che indica la posizione geografica in cui i dati correlati vengono archiviati. I dati personali degli utenti (cassetta postale di Exchange e OneDrive) insieme ai siti SharePoint o ai gruppi di Office 365 creati, possono essere archiviati nella posizione geografica specificata per soddisfare i requisiti di residenza dei dati. È possibile [specificare amministratori diversi per ogni posizione geografica](add-a-sharepoint-geo-admin.md).

In questo modo gli utenti avranno una esperienza uniforme usando i servizi di Office 365, incluse le applicazioni Office, OneDrive e Search. Per i dettagli vedere [Esperienza utente in un ambiente multi-geografico](multi-geo-user-experience.md).

## <a name="onedrive"></a>OneDrive

Ogni utente di OneDrive può effettuare il provisioning o [essere spostato da un amministratore](move-onedrive-between-geo-locations.md) in una posizione satellite in base alla propria PDL. I file personali vengono quindi mantenuti in tale posizione geografica, ma possono essere condivisi con utenti in altre posizioni geografiche.

## <a name="sites-and-groups"></a>Utenti e gruppi

Quando un utente crea un sito connesso a un gruppo di SharePoint, la PDL viene usata per determinare la posizione geografica in cui sono stati creati il sito e la cassetta postale di gruppo. (Se la PDL dell'utente non è stata impostata o è stata impostata una posizione geografica non configurata come posizione satellite, il sito e le cassette postali vengono create nella posizione centrale.)

Solo i servizi Exchange, OneDrive e SharePoint di Office 365 dispongono della funzionalità Multi-Geo. Tuttavia, i gruppi di Office 365 creati con questi servizi riportano la PDL dell'autore e le cassette postali dei gruppi di Exchange e il sito del gruppo SharePoint di O365 effettuano il provisioning nella posizione geografica corrispondente. 

## <a name="managing-the-multi-geo-environment"></a>Gestione dell'ambiente multi-geografico

La configurazione e la gestione dell'ambiente multi-geo vengono eseguite tramite l'interfaccia di amministrazione di SharePoint. 

![Schermata della pagina con le località geografiche nell'interfaccia di amministrazione di SharePoint](media/sharepoint-multi-geo-admin-center.png)

(Per alcune azioni, ad esempio lo spostamento di un sito di SharePoint o OneDrive, è necessario Microsoft PowerShell.)

## <a name="see-also"></a>Vedere anche

[Aka.ms/GetMultiGeo ](https://Aka.ms/GetMultiGeo)

[Amministrare un ambiente multi-geo](administering-a-multi-geo-environment.md)

[Quote di archiviazione di SharePoint in ambienti multi-geo ](sharepoint-multi-geo-storage-quota.md)

[Amministrazione delle cassette postali di Exchange Online in un ambiente multi-geo](administering-exchange-online-multi-geo.md)
