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
ms.openlocfilehash: b88467cf2f33ec3a3a8bf6c2d6927e69e9f7af65
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="4a9b0-103">Aggiungere o rimuovere un amministratore geo in OneDrive per Busniess Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="4a9b0-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="4a9b0-p101">È possibile configurare gli amministratori separati per ogni località geografica contenenti nel tenant. Gli amministratori potranno accedere alle impostazioni di SharePoint Online e OneDrive specifici di posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="4a9b0-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo-location.</span></span>

<span data-ttu-id="4a9b0-p102">Alcuni servizi, ad esempio l'archivio termini - vengono amministrati dalla posizione centrale e replicati località. Admin geografica relativo alla posizione centrale dispone dell'accesso a queste, mentre non geo admins per i percorsi satellitari.</span><span class="sxs-lookup"><span data-stu-id="4a9b0-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="4a9b0-108">Gli amministratori globali e gli amministratori di SharePoint Online continuano ad accedere alle impostazioni in tutte le posizioni geo.</span><span class="sxs-lookup"><span data-stu-id="4a9b0-108">Global administrators and SharePoint Online administrators continue to have access to settings in all geo locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="4a9b0-109">Configurazione geografica amministratori</span><span class="sxs-lookup"><span data-stu-id="4a9b0-109">Configuring geo administrators</span></span>

<span data-ttu-id="4a9b0-110">Configurazione geografica admins richiede il modulo di PowerShell per SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="4a9b0-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="4a9b0-111">Utilizzare [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) per la connessione all'interfaccia di amministrazione della località geografica cui si desidera aggiungere l'amministratore geo. (Ad esempio Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="4a9b0-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="4a9b0-112">Per visualizzare gli amministratori geo esistente di una posizione, eseguire`Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="4a9b0-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="4a9b0-113">Aggiunta di un utente come un amministratore geo</span><span class="sxs-lookup"><span data-stu-id="4a9b0-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="4a9b0-114">Per aggiungere un utente come un amministratore di livello geografico, eseguire`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="4a9b0-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="4a9b0-115">Per rimuovere un utente come un Admin geografica di una posizione, eseguire`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="4a9b0-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="4a9b0-116">Aggiunta di un gruppo come un amministratore geo</span><span class="sxs-lookup"><span data-stu-id="4a9b0-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="4a9b0-117">È possibile aggiungere un gruppo di protezione o un gruppo di protezione abilitati alla posta elettronica come un amministratore geo. (Office 365 gruppi e i gruppi di distribuzione non sono supportati).</span><span class="sxs-lookup"><span data-stu-id="4a9b0-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="4a9b0-118">Per aggiungere un gruppo come un amministratore di livello geografico, eseguire`Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="4a9b0-118">To add a group as a geo admin, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="4a9b0-119">Per rimuovere un gruppo come un amministratore di livello geografico, eseguire`Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="4a9b0-119">To remove a group as a geo admin, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="4a9b0-p103">Si noti che non tutti i gruppi di sicurezza abbiano un alias di gruppo. Se si desidera aggiungere un gruppo di protezione che non dispone di un alias, eseguire [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) per recuperare un elenco dei gruppi, trovare ObjectID del gruppo di sicurezza e quindi eseguire:</span><span class="sxs-lookup"><span data-stu-id="4a9b0-p103">Note that not all security groups have a group alias. If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="4a9b0-122">Per rimuovere un gruppo utilizzando il parametro ObjectID, eseguire`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="4a9b0-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

### <a name="accessing-the-admin-center-for-a-specific-geo-location"></a><span data-ttu-id="4a9b0-123">Accesso al centro di amministrazione per una determinata posizione geografica</span><span class="sxs-lookup"><span data-stu-id="4a9b0-123">Accessing the admin center for a specific geo-location</span></span>

<span data-ttu-id="4a9b0-124">Per amministrare le impostazioni di OneDrive per la posizione geografica, gli amministratori devono accedere interfaccia di amministrazione di OneDrive direttamente utilizzando il formato di URL seguente:</span><span class="sxs-lookup"><span data-stu-id="4a9b0-124">To administer OneDrive settings for their geo-location, admins must access the OneDrive admin center directly using the following URL format:</span></span>

<span data-ttu-id="4a9b0-125">https://admin.onedrive.com/?geo=<*livello geografico*></span><span class="sxs-lookup"><span data-stu-id="4a9b0-125">https://admin.onedrive.com/?geo=<*geo*></span></span>

<span data-ttu-id="4a9b0-126">Ad esempio, si trova all'interfaccia di amministrazione di OneDrive per Canada: https://admin.onedrive.com/?geo=CAN.</span><span class="sxs-lookup"><span data-stu-id="4a9b0-126">For example, the OneDrive admin center for Canada is located at: https://admin.onedrive.com/?geo=CAN.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a9b0-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4a9b0-127">See Also</span></span>

[<span data-ttu-id="4a9b0-128">Aggiungere SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="4a9b0-128">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="4a9b0-129">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="4a9b0-129">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="4a9b0-130">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="4a9b0-130">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="4a9b0-131">Impostare un alias (MailNickName) per un gruppo di sicurezza</span><span class="sxs-lookup"><span data-stu-id="4a9b0-131">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)