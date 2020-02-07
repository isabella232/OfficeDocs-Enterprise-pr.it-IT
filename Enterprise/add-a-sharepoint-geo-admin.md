---
title: Aggiungere o rimuovere un amministratore geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
localization_priority: Priority
f1.keywords:
- NOCSH
description: Informazioni su come aggiungere o rimuovere un amministratore geografico in Office 365 multi-geo.
ms.openlocfilehash: 0e0ce9166d7e290ea0f038bf8d4f20c132be2bc4
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840793"
---
# <a name="add-or-remove-a-geo-administrator-in-office-365-multi-geo"></a><span data-ttu-id="7b57f-103">Aggiungere o rimuovere un amministratore geografico in Office 365 multi-geo.</span><span class="sxs-lookup"><span data-stu-id="7b57f-103">Add or remove a geo administrator in Office 365 Multi-Geo</span></span>

<span data-ttu-id="7b57f-104">È possibile configurare amministratori separati per ogni posizione geografica disponibili nel tenant.</span><span class="sxs-lookup"><span data-stu-id="7b57f-104">You can configure separate administrators for each geo location that you have in your tenant.</span></span> <span data-ttu-id="7b57f-105">Questi amministratori avranno accesso alle impostazioni SharePoint Online e OneDrive specifiche per la posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="7b57f-105">These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="7b57f-106">Alcuni servizi, ad esempio l'archivio termini, sono gestiti dalla posizione centrale e replicati nelle posizioni satellitari.</span><span class="sxs-lookup"><span data-stu-id="7b57f-106">Some services - such as the term store - are administered from the central location and replicated to satellite locations.</span></span> <span data-ttu-id="7b57f-107">L’amministratore geografico della sede centrale può accedere a questi criteri, mentre gli amministratori geografici per località satellitari non possono.</span><span class="sxs-lookup"><span data-stu-id="7b57f-107">The geo admin for the central location has access to these, whereas geo admins for satellite locations don't.</span></span>

<span data-ttu-id="7b57f-108">Gli amministratori globali e di SharePoint Online continuano ad avere accesso alle impostazioni nella posizione centrale e in tutte le località satellitari.</span><span class="sxs-lookup"><span data-stu-id="7b57f-108">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="7b57f-109">Configurazione gli amministratori geografici</span><span class="sxs-lookup"><span data-stu-id="7b57f-109">Configuring geo administrators</span></span>

<span data-ttu-id="7b57f-110">Per configurare gli amministratori geografici è necessario il modulo di PowerShell per SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7b57f-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="7b57f-111">Utilizzare [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) per connettersi all'interfaccia di amministrazione della posizione geografica in cui si vuole aggiungere l'amministratore geografico. (Ad esempio Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="7b57f-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="7b57f-112">Per visualizzare gli amministratori geografici esistenti in una posizione, eseguire `Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="7b57f-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="7b57f-113">Aggiunta di un utente come amministratore geografico</span><span class="sxs-lookup"><span data-stu-id="7b57f-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="7b57f-114">Per aggiungere un utente come amministratore geografico, eseguire `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="7b57f-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="7b57f-115">Per rimuovere un utente da amministratore geografico di una posizione, eseguire  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="7b57f-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="7b57f-116">Aggiunta di un gruppo come amministratore geografico</span><span class="sxs-lookup"><span data-stu-id="7b57f-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="7b57f-117">È possibile aggiungere un gruppo di sicurezza o un gruppo di sicurezza abilitato alla posta elettronica come amministratore geografico. (I gruppi di distribuzione e i Gruppi di Office 365 non sono supportati).</span><span class="sxs-lookup"><span data-stu-id="7b57f-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="7b57f-118">Per aggiungere un gruppo come amministratore geografico, eseguire `Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="7b57f-118">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="7b57f-119">Per rimuovere un gruppo da amministratore geografico, eseguire `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="7b57f-119">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="7b57f-120">Si noti che non tutti i gruppi di sicurezza un alias di gruppo.</span><span class="sxs-lookup"><span data-stu-id="7b57f-120">Note that not all security groups have a group alias.</span></span> <span data-ttu-id="7b57f-121">Per aggiungere un gruppo di sicurezza che non dispone di un alias, eseguire [Get-MsolGroup](https://docs.microsoft.com/powershell/module/msonline/get-msolgroup) per recuperare un elenco dei gruppi, trovare il valore del proprio gruppo di sicurezza e quindi eseguire:</span><span class="sxs-lookup"><span data-stu-id="7b57f-121">If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="7b57f-122">Per rimuovere un gruppo usando il valore di ObjectID, eseguire `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="7b57f-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

## <a name="see-also"></a><span data-ttu-id="7b57f-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7b57f-123">See Also</span></span>

[<span data-ttu-id="7b57f-124">Add-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="7b57f-124">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="7b57f-125">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="7b57f-125">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="7b57f-126">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="7b57f-126">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="7b57f-127">Impostare un alias (MailNickName) per un gruppo di sicurezza</span><span class="sxs-lookup"><span data-stu-id="7b57f-127">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/powershell/module/azuread/set-azureadgroup)