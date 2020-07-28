---
title: Limitare il contenuto del sito di SharePoint a una posizione geografica
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Normal
description: Informazioni su come limitare i siti di SharePoint a una specifica posizione geografica in un ambiente multi-geo.
ms.openlocfilehash: 1b1b072709ee54b2a18255798995650fc9f9942e
ms.sourcegitcommit: aac21bb1a7c1dfc3ba76a2db883e0457037c5667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/28/2020
ms.locfileid: "45433477"
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
