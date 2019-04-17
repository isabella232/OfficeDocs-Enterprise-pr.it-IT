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
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a><span data-ttu-id="a43c5-103">Multi-Geo Capabilities in OneDrive e SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a43c5-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="a43c5-104">La funzionalità Multi-Geo in OneDrive e SharePoint Online consente di controllare il paese/area geografica in cui sono archiviate le risorse condivise, ad esempio dei team di SharePoint e delle cassette postali di Gruppi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="a43c5-104">Multi-Geo capabilities in OneDrive and SharePoint Online enables control of the country or region where shared resources like SharePoint team sites and Office 365 Group mailboxes are stored at rest.</span></span>

<span data-ttu-id="a43c5-105">Ogni utente, ogni cassetta postale di Gruppi e ogni sito SharePoint ha una posizione dei dati preferita che indica la posizione geografica in cui i dati associati vengono archiviati.</span><span class="sxs-lookup"><span data-stu-id="a43c5-105">Each user, Group mailbox, and SharePoint site has a Preferred Data Location (PDL) which denotes the geo location where related data is to be stored.</span></span> <span data-ttu-id="a43c5-106">I dati personali degli utenti (cassetta postale di Exchange e OneDrive) insieme ai siti SharePoint o ai gruppi di Office 365 creati, possono essere archiviati nella posizione geografica specificata per soddisfare i requisiti di residenza dei dati.</span><span class="sxs-lookup"><span data-stu-id="a43c5-106">Users' personal data (Exchange mailbox and OneDrive) along with any Office 365 Groups or SharePoint sites that they create can be stored in the specified geo location to meet data residency requirements.</span></span> <span data-ttu-id="a43c5-107">È possibile [specificare amministratori diversi per ogni posizione geografica](add-a-sharepoint-geo-admin.md).</span><span class="sxs-lookup"><span data-stu-id="a43c5-107">You can [specify different administrators for each geo location](add-a-sharepoint-geo-admin.md).</span></span>

<span data-ttu-id="a43c5-108">In questo modo gli utenti avranno un’esperienza uniforme quando usano i servizi di Office 365, incluse le applicazioni Office, OneDrive e Search.</span><span class="sxs-lookup"><span data-stu-id="a43c5-108">Users get a seamless experience when using Office 365 services, including Office applications, OneDrive, and Search.</span></span> <span data-ttu-id="a43c5-109">Per i dettagli vedere [Esperienza utente in un ambiente multi-geografico](multi-geo-user-experience.md).</span><span class="sxs-lookup"><span data-stu-id="a43c5-109">See [User experience in a multi-geo environment](multi-geo-user-experience.md) for details.</span></span>

## <a name="onedrive"></a><span data-ttu-id="a43c5-110">OneDrive</span><span class="sxs-lookup"><span data-stu-id="a43c5-110">OneDrive</span></span>

<span data-ttu-id="a43c5-111">Ogni utente di OneDrive può essere gestito o [spostato da un amministratore](move-onedrive-between-geo-locations.md) in una posizione satellite in base alla propria posizione dei dati preferita.</span><span class="sxs-lookup"><span data-stu-id="a43c5-111">Each user's OneDrive can be provisioned in or [moved by an administrator](move-onedrive-between-geo-locations.md) to a satellite location in accordance with the user's PDL.</span></span> <span data-ttu-id="a43c5-112">I file personali vengono quindi mantenuti in tale posizione geografica, ma possono essere condivisi con utenti di altre posizioni geografiche.</span><span class="sxs-lookup"><span data-stu-id="a43c5-112">Personal files are then kept in that geo location, though they can be shared with users in other geo locations.</span></span>

## <a name="sites-and-groups"></a><span data-ttu-id="a43c5-113">Utenti e gruppi</span><span class="sxs-lookup"><span data-stu-id="a43c5-113">Active Directory Sites and Routing Groups tab</span></span>

<span data-ttu-id="a43c5-114">Quando un utente crea un sito connesso a un gruppo di SharePoint, la posizione dei dati preferita viene usata per determinare la posizione geografica in cui viene creato il sito e la relativa cassetta postale di Gruppi.</span><span class="sxs-lookup"><span data-stu-id="a43c5-114">When a user creates a SharePoint group-connected site, their PDL is used to determine the geo location where the site and its associated Group mailbox is created.</span></span> <span data-ttu-id="a43c5-115">Se la posizione dei dati preferita dell'utente non è stata impostata o è stata impostata una posizione geografica non configurata come satellite, il sito e la cassetta postale vengono creati nella posizione centrale.</span><span class="sxs-lookup"><span data-stu-id="a43c5-115">(If the user's PDL value hasn't been set, or has been set to geo location that hasn't been configured as a satellite location, then the site and mailbox are created in the central location.)</span></span>

<span data-ttu-id="a43c5-116">Solo i servizi Exchange, OneDrive e SharePoint di Office 365 dispongono della funzionalità Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="a43c5-116">Office 365 services other than Exchange, OneDrive, and SharePoint are not Multi-Geo.</span></span> <span data-ttu-id="a43c5-117">Tuttavia, i gruppi di Office 365 creati con questi servizi riportano la posizione dei dati preferita dell'autore e le cassette postali dei gruppi di Exchange e il sito SharePoint dei Gruppi di O365 verranno forniti nella posizione geografica corrispondente.</span><span class="sxs-lookup"><span data-stu-id="a43c5-117">However, Office 365 Groups that are created by these services will be stamped with the PDL of the creator and their Exchange Group mailbox and SharePoint O365 Group Site provisioned in the corresponding geo.</span></span> 

## <a name="managing-the-multi-geo-environment"></a><span data-ttu-id="a43c5-118">Gestione dell'ambiente multi-geografico</span><span class="sxs-lookup"><span data-stu-id="a43c5-118">Managing the multi-geo environment</span></span>

<span data-ttu-id="a43c5-119">La configurazione e la gestione dell'ambiente multi-geo vengono eseguite tramite l'interfaccia di amministrazione di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="a43c5-119">Setting up and managing your multi-geo environment is done through the SharePoint admin center.</span></span> 

![Schermata della pagina con le posizioni geografiche nell'interfaccia di amministrazione di SharePoint](media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="a43c5-121">Per alcune azioni, come il trasferimento di un sito di SharePoint o OneDrive, è necessario Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a43c5-121">(Some actions, such as moving a SharePoint site or a OneDrive site require Microsoft PowerShell.)</span></span>

## <a name="see-also"></a><span data-ttu-id="a43c5-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a43c5-122">See also</span></span>

[<span data-ttu-id="a43c5-123">Aka.ms/GetMultiGeo </span><span class="sxs-lookup"><span data-stu-id="a43c5-123">Aka.ms/GetMultiGeo </span></span>](https://Aka.ms/GetMultiGeo)

[<span data-ttu-id="a43c5-124">Amministrare un ambiente multi-geo</span><span class="sxs-lookup"><span data-stu-id="a43c5-124">Administering a multi-geo environment</span></span>](administering-a-multi-geo-environment.md)

[<span data-ttu-id="a43c5-125">Quote di archiviazione di SharePoint in ambienti multi-geo </span><span class="sxs-lookup"><span data-stu-id="a43c5-125">SharePoint storage quotas in multi-geo environments</span></span>](sharepoint-multi-geo-storage-quota.md)

[<span data-ttu-id="a43c5-126">Amministrazione delle cassette postali di Exchange Online in un ambiente multi-geo</span><span class="sxs-lookup"><span data-stu-id="a43c5-126">Administering Exchange Online mailboxes in a multi-geo environment</span></span>](administering-exchange-online-multi-geo.md)
