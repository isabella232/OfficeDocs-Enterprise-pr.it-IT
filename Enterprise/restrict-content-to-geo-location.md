---
title: Limitare il contenuto del sito di SharePoint a una posizione geografica
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Informazioni su come limitare i siti di SharePoint a una specifica posizione geografica in un ambiente multi-geo.
ms.openlocfilehash: 9319ed6229acc7cda48cc52b3a27681c53f1359c
ms.sourcegitcommit: 7bb48195079ce14aabfa0384771b17db0e4908b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "36828480"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a>Limitare il contenuto del sito di SharePoint a una posizione geografica

In alcuni casi è possibile applicare a un sito e il contenuto del file per mantenere la posizione geografica in cui è stato creato il sito, e non lo spostamento del sito o impedire la memorizzazione nella cache del contenuto del sito in un'altra posizione geografica.

È possibile farlo usando il cmdlet [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) con il parametro **RestrictedToGeo**. Questo parametro ha un valore predefinito NULL, ma è possibile sostituirlo con una delle opzioni seguenti:

|Restrizione|Descrizione|
|:----------|:----------|
|NoRestriction|Il sito può essere spostato in un'altra posizione geografica.|
|BlockMoveOnly|I siti non possono essere spostati in un'altra posizione geografica, ma il contenuto dei siti può essere memorizzato nella cache in altre posizioni geografiche.|
|BlockFull|I siti non possono essere spostati in un'altra posizione geografica e l’intero contenuto del file non viene memorizzato nella cache in altre posizioni geografiche. Il titolo dei file (raccolto dal contenuto), il nome del file e altre sue proprietà possono comunque essere memorizzate nella cache in altre posizioni geografiche.<br>Il contenuto del sito prima che fosse configurato per BlockFull, potrebbe continuare a essere memorizzato nella cache in altre località geografiche.|

Utilizzare la sintassi seguente:

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

Ad esempio:

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`
