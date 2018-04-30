---
title: Aggiungere o rimuovere un amministratore geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Informazioni su come aggiungere o rimuovere un amministratore geo in OneDrive per Business Multi-Geo.
ms.openlocfilehash: 7630597654df9ad78619b94fedc9e18d5b0b721e
ms.sourcegitcommit: 886b23f590f6187f7a98c1083a3b49359ec2a5c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a>Aggiungere o rimuovere un amministratore geo in OneDrive per Busniess Multi-Geo

È possibile configurare gli amministratori separati per ogni località geografica contenenti nel tenant. Gli amministratori potranno accedere alle impostazioni di SharePoint Online e OneDrive specifici di posizione geografica.

Alcuni servizi, ad esempio l'archivio termini - vengono amministrati dalla posizione centrale e replicati località. Admin geografica relativo alla posizione centrale dispone dell'accesso a queste, mentre non geo admins per i percorsi satellitari.

Gli amministratori globali e gli amministratori di SharePoint Online continuano ad accedere alle impostazioni in tutte le posizioni geo.

## <a name="configuring-geo-administrators"></a>Configurazione geografica amministratori

Configurazione geografica admins richiede il modulo di PowerShell per SharePoint Online.

Utilizzare [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) per la connessione all'interfaccia di amministrazione della località geografica cui si desidera aggiungere l'amministratore geo. (Ad esempio Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)

Per visualizzare gli amministratori geo esistente di una posizione, eseguire`Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>Aggiunta di un utente come un amministratore geo

Per aggiungere un utente come un amministratore di livello geografico, eseguire`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

Per rimuovere un utente come un Admin geografica di una posizione, eseguire`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>Aggiunta di un gruppo come un amministratore geo

È possibile aggiungere un gruppo di protezione o un gruppo di protezione abilitati alla posta elettronica come un amministratore geo. (Office 365 gruppi e i gruppi di distribuzione non sono supportati).

Per aggiungere un gruppo come un amministratore di livello geografico, eseguire`Add-SPOGeoAdministrator -GroupAlias <alias>`

Per rimuovere un gruppo come un amministratore di livello geografico, eseguire`Remove-SPOGeoAdministrator -GroupAlias <alias>`

Si noti che non tutti i gruppi di sicurezza abbiano un alias di gruppo. Se si desidera aggiungere un gruppo di protezione che non dispone di un alias, eseguire [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) per recuperare un elenco dei gruppi, trovare ObjectID del gruppo di sicurezza e quindi eseguire:

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

Per rimuovere un gruppo utilizzando il parametro ObjectID, eseguire`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

## <a name="see-also"></a>Vedere anche

[Aggiungere SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[Impostare un alias (MailNickName) per un gruppo di sicurezza](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)