---
title: Aggiungere o rimuovere un amministratore geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Informazioni su come aggiungere o rimuovere un amministratore geo in OneDrive per Business Multi-Geo.
ms.openlocfilehash: 0007f1ac3c73fa7a2ada562f8da65215f80744ca
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a>Aggiungere o rimuovere un amministratore geo in OneDrive per Busniess Multi-Geo

È possibile configurare gli amministratori separati per ogni località geografica contenenti nel tenant. Gli amministratori potranno accedere alle impostazioni di SharePoint Online e OneDrive specifici di posizione geografica.

Alcuni servizi, ad esempio l'archivio termini - vengono amministrati dalla posizione centrale e replicati località. Admin geografica relativo alla posizione centrale dispone dell'accesso a queste, mentre non geo admins per i percorsi satellitari.

Gli amministratori globali e gli amministratori di SharePoint Online continuano ad accedere alle impostazioni in tutte le posizioni geo.

## <a name="configuring-geo-administrators"></a>Configurazione geografica amministratori

Configurazione geografica admins richiede il modulo di PowerShell per SharePoint Online.

Utilizzare [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) per la connessione all'interfaccia di amministrazione della località geografica cui si desidera aggiungere l'amministratore geo. (Ad esempio Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)

Per aggiungere un utente come un amministratore di livello geografico, eseguire`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

Per visualizzare gli amministratori geo esistente di una posizione, eseguire`Get-SPOGeoAdministrators`

Per rimuovere un utente come un Admin geografica di una posizione, eseguire`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

## <a name="see-also"></a>Vedere anche

[Aggiungere SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)