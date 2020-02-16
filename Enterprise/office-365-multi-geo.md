---
title: Office 365 Multi-Geo
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
localization_priority: Priority
description: Con Office 365 Multi-Geo si può espandere la propria presenza Office 365 a più paesi/aree geografiche.
ms.openlocfilehash: 62aa890bb3bb8bfcabd13285814b72c7000047dc
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2020
ms.locfileid: "41974059"
---
# <a name="office-365-multi-geo"></a><span data-ttu-id="a43fa-103">Office 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="a43fa-103">Office 365 Multi-Geo</span></span>

<span data-ttu-id="a43fa-104">Con Office 365 Multi-Geo l'organizzazione può espandere la presenza di Office 365 a più paesi/aree geografiche all'interno del tenant esistente.</span><span class="sxs-lookup"><span data-stu-id="a43fa-104">With Office 365 Multi-Geo, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant.</span></span> <span data-ttu-id="a43fa-105">Invitare il team degli account Microsoft ad iscrivere la propria società multi-nazionale a Office 365 Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="a43fa-105">Reach out to your Microsoft Account Team to sign up your Multi-National Company for Office 365 Multi-Geo.</span></span>
  
<span data-ttu-id="a43fa-106">Con Office 365 Multi-Geo, è possibile effettuare il provisioning e archiviare i dati a riposo nelle località geografiche scelte per soddisfare i requisiti di residenza dei dati e allo stesso tempo sbloccare lo sviluppo globale delle esperienze di produttività moderna per i dipendenti.</span><span class="sxs-lookup"><span data-stu-id="a43fa-106">With Office 365 Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>

#### <a name="video-introducing-office-365-multi-geo"></a><span data-ttu-id="a43fa-107">Video: Introduzione a Office 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="a43fa-107">Video: Introducing Office 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1Yk6B?autoplay=false]

<span data-ttu-id="a43fa-108">In un ambiente geografico Multi tenant di Office 365 è costituito da una posizione centralizzata (in cui l'abbonamento a Office 365 è stato originariamente provisioning) e uno o più località.</span><span class="sxs-lookup"><span data-stu-id="a43fa-108">In a Multi-Geo environment, your Office 365 tenant consists of a central location (where your Office 365 subscription was originally provisioned) and one or more satellite locations.</span></span> <span data-ttu-id="a43fa-109">In un tenant Multi-Geo, le informazioni su località geografiche, gruppi e le informazioni utente, vengono acquisite in Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="a43fa-109">In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD).</span></span> <span data-ttu-id="a43fa-110">Poiché le informazioni del tenant sono acquisite in modo centralizzato e sincronizzate in ogni località geografica, la condivisione e le esperienze coinvolgono tutti gli utenti della società.</span><span class="sxs-lookup"><span data-stu-id="a43fa-110">Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

![Schermata della mappa multi-geo dall'interfaccia di amministrazione di SharePoint.](media/multi-geo-world-map.png)

<span data-ttu-id="a43fa-112">Si noti che Office 365 Multi-Geo non è progettato principalmente per ottimizzare le prestazioni, ma per soddisfare i requisiti di residenza dei dati.</span><span class="sxs-lookup"><span data-stu-id="a43fa-112">Note that Office 365 Multi-Geo is not primarily designed for performance optimization, it is designed to meet data residency requirements.</span></span> <span data-ttu-id="a43fa-113">Per informazioni sull'ottimizzazione delle prestazioni di Office 365, vedere [Pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) o contattare il gruppo di supporto.</span><span class="sxs-lookup"><span data-stu-id="a43fa-113">For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

## <a name="terminology"></a><span data-ttu-id="a43fa-114">Terminologia</span><span class="sxs-lookup"><span data-stu-id="a43fa-114">Terminology</span></span>

<span data-ttu-id="a43fa-115">Ecco i termini chiave utilizzati nella descrizione di Office 365 Multi-Geo:</span><span class="sxs-lookup"><span data-stu-id="a43fa-115">Here are the key terms used in describing Office 365 Multi-Geo:</span></span>

- <span data-ttu-id="a43fa-116">**Posizione centrale** - la posizione geografica in cui è stato effettuato originariamente il provisioning del tenant.</span><span class="sxs-lookup"><span data-stu-id="a43fa-116">**Central location** - the geo location where your tenant was originally provisioned.</span></span>
- <span data-ttu-id="a43fa-117">**Amministratore geografico** - un amministratore che può gestire una o più posizioni satellite specificato.</span><span class="sxs-lookup"><span data-stu-id="a43fa-117">**Geo administrator** - An administrator who can administer one or more specified satellite locations.</span></span>
- <span data-ttu-id="a43fa-118">**Codice geografico** - un codice di tre lettere per una posizione geografica specificata.</span><span class="sxs-lookup"><span data-stu-id="a43fa-118">**Geo code** - a three-letter code for a given geo location.</span></span>
- <span data-ttu-id="a43fa-119">**Posizione geografica** - un'area geografica che può essere usata in un tenant multi-geo per ospitare dati, tra cui cassette postali di Exchange, OneDrive e siti di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="a43fa-119">**Geo location** – A geographic location that can be used in a multi-geo tenant to host data, including Exchange mailboxes and OneDrive and SharePoint sites.</span></span>
- <span data-ttu-id="a43fa-120">**Procedure dati posizione (PDL)** - proprietà dell’utente impostata dall'amministratore che indica la posizione geografica in cui si deve eseguire il provisioning della cassetta postale di Exchange di utenti e OneDrive.</span><span class="sxs-lookup"><span data-stu-id="a43fa-120">**Preferred Data Location (PDL)** – A user property set by the administrator that indicates where the geo location where the users Exchange mailbox and OneDrive should be provisioned.</span></span> <span data-ttu-id="a43fa-121">Il PDL determina anche se è stato effettuato il provisioning dei siti di SharePoint creati dall'utente.</span><span class="sxs-lookup"><span data-stu-id="a43fa-121">The PDL also determines where SharePoint sites that are created by the user are provisioned.</span></span>
- <span data-ttu-id="a43fa-122">**Posizione satellite** - le posizioni geografiche in cui i carichi di lavoro di Office 365 consapevoli della propria ubicazione (Exchange, SharePoint e OneDrive) sono abilitati in un tenant multi-geo.</span><span class="sxs-lookup"><span data-stu-id="a43fa-122">**Satellite location** – The geo locations where the geo-aware Office 365 workloads (SharePoint, OneDrive, and Exchange) are enabled in a multi-geo tenant.</span></span>
- <span data-ttu-id="a43fa-123">**Tenant**: rappresentazione di un'organizzazione in Office 365 che in genere contiene uno o più domini associati ad essa (ad esempio contoso.com)</span><span class="sxs-lookup"><span data-stu-id="a43fa-123">**Tenant** – An organization's representation in Office 365 which typically has one or more domains associated with it (for example, contoso.com).</span></span>

## <a name="office-365-multi-geo-availability"></a><span data-ttu-id="a43fa-124">Disponibilità di Office 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="a43fa-124">Office 365 Multi-Geo availability</span></span>

<span data-ttu-id="a43fa-125">Office 365 Multi-Geo è attualmente disponibile in questi paesi/aree geografiche:</span><span class="sxs-lookup"><span data-stu-id="a43fa-125">Office 365 Multi-Geo is currently offered in these regions and countries:</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="getting-started"></a><span data-ttu-id="a43fa-126">Introduzione</span><span class="sxs-lookup"><span data-stu-id="a43fa-126">Getting started</span></span>

<span data-ttu-id="a43fa-127">Seguire questi semplici passaggi per iniziare con Multi-Geo:</span><span class="sxs-lookup"><span data-stu-id="a43fa-127">Follow these steps to get started with multi-geo:</span></span>

1. <span data-ttu-id="a43fa-128">Collaborare con il team responsabile dell'account per aggiungere _Multi-Geo Capabilities al piano di servizio di Office 365 _.</span><span class="sxs-lookup"><span data-stu-id="a43fa-128">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span> <span data-ttu-id="a43fa-129">Verranno fornite le procedure per aggiungere il numero di licenze necessarie.</span><span class="sxs-lookup"><span data-stu-id="a43fa-129">They will guide you to add the number of licenses needed.</span></span> <span data-ttu-id="a43fa-130">La funzionalità Multi-Geo Capabilities è disponibile per i clienti con un minimo di 500 abbonamenti a Office 365.</span><span class="sxs-lookup"><span data-stu-id="a43fa-130">Multi-Geo feature is available to customers with a minimum of 500 Office 365 subscriptions.</span></span>

   <span data-ttu-id="a43fa-131">Prima di iniziare a usare Office 365 Multi-Geo, Microsoft deve configurare il tenant di Exchange Online per il supporto Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="a43fa-131">Before you can start using Office 365 Multi-Geo, Microsoft needs to configure your Exchange Online tenant for multi-geo support.</span></span> <span data-ttu-id="a43fa-132">La procedura di configurazione, da effettuare una sola volta, viene attivata dopo aver ordinato il piano di servizio *Funzionalità Multi-Geo di Office 365* e le licenze saranno visualizzate nel tenant.</span><span class="sxs-lookup"><span data-stu-id="a43fa-132">This one-time configuration process is triggered after you order the *Multi-Geo Capabilities in Office 365* service plan and the licenses show up in your tenant.</span></span> <span data-ttu-id="a43fa-133">Una volta che vengono applicate le licenze Multi-Geo, si riceveranno notifiche nel [Centro messaggi di Office 365](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) e sarà quindi possibile iniziare la configurazione e l’uso della funzionalità Multi-Geo di Office 365.</span><span class="sxs-lookup"><span data-stu-id="a43fa-133">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) once your Multi-Geo licenses are applied and you then may begin configuring and using your Office 365 Multi-Geo capabilities.</span></span>

2. <span data-ttu-id="a43fa-134">Leggere [Pianificare l'ambiente Multi-Geo](plan-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="a43fa-134">Read [Plan your multi-geo environment](plan-for-multi-geo.md).</span></span>

3. <span data-ttu-id="a43fa-135">Informazioni sull’[amministrazione di un ambiente Multi-Geo](administering-a-multi-geo-environment.md) e [ sul riscontro degli utenti sull’ambiente](multi-geo-user-experience.md).</span><span class="sxs-lookup"><span data-stu-id="a43fa-135">Learn about [administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience the environment](multi-geo-user-experience.md).</span></span>

4. <span data-ttu-id="a43fa-136">Quando si è pronti per impostare su Office 365 Multi-Geo, [Configurare il tenant per Multi-Geo](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="a43fa-136">When you are ready to set up Office 365 Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md).</span></span>

5. <span data-ttu-id="a43fa-137">[Impostare la ricerca](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="a43fa-137">[Set up search](configure-search-for-multi-geo.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a43fa-138">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a43fa-138">See also</span></span>

[<span data-ttu-id="a43fa-139">Multi-Geo in Exchange Online e OneDrive</span><span class="sxs-lookup"><span data-stu-id="a43fa-139">Multi-Geo in Exchange Online and OneDrive</span></span>](https://Aka.ms/GoMultiGeo)

[<span data-ttu-id="a43fa-140">Multi-Geo Capabilities in OneDrive e SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a43fa-140">Multi-Geo Capabilities in OneDrive and SharePoint Online</span></span>](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)

[<span data-ttu-id="a43fa-141">Funzionalità Multi-Geo in Exchange Online</span><span class="sxs-lookup"><span data-stu-id="a43fa-141">Multi-Geo Capabilities in Exchange Online</span></span>](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-exchange-online)

[<span data-ttu-id="a43fa-142">Esperienza di Teams in un ambiente multi-geografico</span><span class="sxs-lookup"><span data-stu-id="a43fa-142">Teams experience in a multi-geo environment</span></span>](https://docs.microsoft.com/microsoftteams/teams-experience-o365odb-spo-multi-geo)
