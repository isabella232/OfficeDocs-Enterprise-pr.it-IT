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
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="5e11d-103">Aggiungere o rimuovere un amministratore geo in OneDrive per Busniess Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="5e11d-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="5e11d-p101">È possibile configurare gli amministratori separati per ogni località geografica contenenti nel tenant. Gli amministratori potranno accedere alle impostazioni di SharePoint Online e OneDrive specifici di posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="5e11d-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo-location.</span></span>

<span data-ttu-id="5e11d-p102">Alcuni servizi, ad esempio l'archivio termini - vengono amministrati dalla posizione centrale e replicati località. Admin geografica relativo alla posizione centrale dispone dell'accesso a queste, mentre non geo admins per i percorsi satellitari.</span><span class="sxs-lookup"><span data-stu-id="5e11d-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="5e11d-108">Gli amministratori globali e gli amministratori di SharePoint Online continuano ad accedere alle impostazioni in tutte le posizioni geo.</span><span class="sxs-lookup"><span data-stu-id="5e11d-108">Global administrators and SharePoint Online administrators continue to have access to settings in all geo locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="5e11d-109">Configurazione geografica amministratori</span><span class="sxs-lookup"><span data-stu-id="5e11d-109">Configuring geo administrators</span></span>

<span data-ttu-id="5e11d-110">Configurazione geografica admins richiede il modulo di PowerShell per SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="5e11d-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="5e11d-111">Utilizzare [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) per la connessione all'interfaccia di amministrazione della località geografica cui si desidera aggiungere l'amministratore geo. (Ad esempio Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="5e11d-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="5e11d-112">Per aggiungere un utente come un amministratore di livello geografico, eseguire`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="5e11d-112">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="5e11d-113">Per visualizzare gli amministratori geo esistente di una posizione, eseguire`Get-SPOGeoAdministrators`</span><span class="sxs-lookup"><span data-stu-id="5e11d-113">To view the existing geo admins of a location, run `Get-SPOGeoAdministrators`</span></span>

<span data-ttu-id="5e11d-114">Per rimuovere un utente come un Admin geografica di una posizione, eseguire`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="5e11d-114">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

## <a name="see-also"></a><span data-ttu-id="5e11d-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5e11d-115">See Also</span></span>

[<span data-ttu-id="5e11d-116">Aggiungere SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="5e11d-116">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="5e11d-117">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="5e11d-117">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="5e11d-118">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="5e11d-118">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)