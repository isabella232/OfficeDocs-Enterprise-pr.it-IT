---
title: Limitare il contenuto a una posizione geografica
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Informazioni su come limitare i siti di SharePoint a una specifica posizione geografica in un ambiente multi-geo.
ms.openlocfilehash: 59301a591e5465bdcda4aa84a18880961c0b615b
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2019
ms.locfileid: "30934020"
---
# <a name="restrict-content-to-a-geo-location"></a>Limitare il contenuto a una posizione geografica

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
