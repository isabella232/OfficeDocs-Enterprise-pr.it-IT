---
title: Aggiungere o rimuovere un amministratore geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
description: Informazioni su come aggiungere o rimuovere un amministratore geografico in Office 365 multi-geo.
ms.openlocfilehash: d10340b7fe42016710ec953f5b45110e9ea8b901
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030570"
---
# <a name="add-or-remove-a-geo-administrator-in-office-365-multi-geo"></a>Aggiungere o rimuovere un amministratore geografico in Office 365 multi-geo.

È possibile configurare amministratori separati per ogni posizione geografica disponibili nel tenant. Questi amministratori avranno accesso alle impostazioni SharePoint Online e OneDrive specifiche per la posizione geografica.

Alcuni servizi, ad esempio l'archivio termini, sono gestiti dalla posizione centrale e replicati nelle posizioni satellitari. L’amministratore geografico della sede centrale può accedere a questi criteri, mentre gli amministratori geografici per località satellitari non possono.

Gli amministratori globali e di SharePoint Online continuano ad avere accesso alle impostazioni nella posizione centrale e in tutte le località satellitari.

## <a name="configuring-geo-administrators"></a>Configurazione gli amministratori geografici

Per configurare gli amministratori geografici è necessario il modulo di PowerShell per SharePoint Online.

Utilizzare [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) per connettersi all'interfaccia di amministrazione della posizione geografica in cui si vuole aggiungere l'amministratore geografico. (Ad esempio Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)

Per visualizzare gli amministratori geografici esistenti in una posizione, eseguire `Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>Aggiunta di un utente come amministratore geografico

Per aggiungere un utente come amministratore geografico, eseguire `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

Per rimuovere un utente da amministratore geografico di una posizione, eseguire  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>Aggiunta di un gruppo come amministratore geografico

È possibile aggiungere un gruppo di sicurezza o un gruppo di sicurezza abilitato alla posta elettronica come amministratore geografico. (I gruppi di distribuzione e i Gruppi di Office 365 non sono supportati).

Per aggiungere un gruppo come amministratore geografico, eseguire `Add-SPOGeoAdministrator -GroupAlias <alias>`

Per rimuovere un gruppo da amministratore geografico, eseguire `Remove-SPOGeoAdministrator -GroupAlias <alias>`

Si noti che non tutti i gruppi di sicurezza un alias di gruppo. Per aggiungere un gruppo di sicurezza che non dispone di un alias, eseguire [Get-MsolGroup](https://docs.microsoft.com/powershell/module/msonline/get-msolgroup) per recuperare un elenco dei gruppi, trovare il valore del proprio gruppo di sicurezza e quindi eseguire:

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

Per rimuovere un gruppo usando il valore di ObjectID, eseguire `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

## <a name="see-also"></a>Vedere anche

[Add-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[Impostare un alias (MailNickName) per un gruppo di sicurezza](https://docs.microsoft.com/powershell/module/azuread/set-azureadgroup)