---
title: Esperienza utente in ambiente multi-geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Informazioni sull'esperienza utente riguardo SharePoint e OneDrive in ambiente multi-geografico.
ms.openlocfilehash: 3c7e4b6802bddc78db016c9c282f5add0c71c491
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="7ba68-103">Esperienza utente in ambiente multi-geografico.</span><span class="sxs-lookup"><span data-stu-id="7ba68-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="7ba68-104">Ecco cosa gli utenti visualizzeranno in una configurazione OneDrive Multi-Geo:</span><span class="sxs-lookup"><span data-stu-id="7ba68-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="7ba68-105">Posizione di OneDrive for Business dell'utente</span><span class="sxs-lookup"><span data-stu-id="7ba68-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="7ba68-p101">Gli utenti disporranno di OneDrive for Business fornito nel percorso dati preferito. Se un utente accede a un URL OneDrive che contiene una posizione geografica errata (come un segnalibro da una precedente posizione geografica), viene automaticamente reindirizzato a OneDrive nella posizione geografica appropriata.</span><span class="sxs-lookup"><span data-stu-id="7ba68-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="7ba68-108">Condivisione</span><span class="sxs-lookup"><span data-stu-id="7ba68-108">Sharing</span></span>

<span data-ttu-id="7ba68-p102">L'esperienza di Selezione utenti mostra tutti gli utenti indipendentemente dalla posizione geografica. Questo consente all'utente di condividere contenuti con un altro utente nella stessa posizione geografica o in una qualsiasi altra posizione geografica del tenant. Verrà visualizzato il contenuto da posizioni geografiche diverse nella visualizzazione **Condivisi con me** dell’utente in OneDrive for Business e questo sarà accessibile con l'esperienza Single Sign-On indipendentemente dalla posizione geografica in cui è ospitato.</span><span class="sxs-lookup"><span data-stu-id="7ba68-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="7ba68-112">Applicazioni di Office</span><span class="sxs-lookup"><span data-stu-id="7ba68-112">Office applications</span></span>

<span data-ttu-id="7ba68-p103">Le applicazioni Office come Word, Excel e PowerPoint rileveranno automaticamente la posizione geografica corretta di OneDrive for Business per ciascun utente al momento dell'accesso. Non è necessario immettere l'URL geo-specifico per OneDrive.</span><span class="sxs-lookup"><span data-stu-id="7ba68-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="7ba68-115">Client di sincronizzazione OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="7ba68-115">OneDrive for Business Windows Sync client</span></span>

<span data-ttu-id="7ba68-116">Il client di sincronizzazione OneDrive for Business (versione 17.3.6943.0625 e successive) rileverà automaticamente la posizione geografica corretta di OneDrive for Business per l'utente.</span><span class="sxs-lookup"><span data-stu-id="7ba68-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="7ba68-117">Avvio app di Office 365</span><span class="sxs-lookup"><span data-stu-id="7ba68-117">Office 365 app launcher</span></span>

<span data-ttu-id="7ba68-p104">Il servizio avvio app ha funzionalità Multi-Geo e indirizzerà direttamente ciascun riquadro alla corretta posizione geografica del carico di lavoro. I riquadri di OneDrive indicano la corretta posizione geografica in cui si trova la raccolta OneDrive dell'utente, mentre il riquadro di SharePoint indicherà a tutti gli utenti la posizione centrale, poiché ancora ospita i siti del team.</span><span class="sxs-lookup"><span data-stu-id="7ba68-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="7ba68-120">Profili utente Delve</span><span class="sxs-lookup"><span data-stu-id="7ba68-120">Delve User profiles</span></span>

<span data-ttu-id="7ba68-p105">Le informazioni sul profilo utente sono gestite nella posizione geografica dell'utente. Quando si seleziona un utente, si verrà indirizzati alla posizione geografica corretta per l'utente, in cui sarà possibile visualizzare i dettagli del profilo completo.</span><span class="sxs-lookup"><span data-stu-id="7ba68-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="7ba68-123">Se Delve è disattivato, verrà visualizzata l'esperienza del profilo classico in SharePoint, il quale non ha funzionalità Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="7ba68-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="7ba68-124">Delve</span><span class="sxs-lookup"><span data-stu-id="7ba68-124">Delve</span></span>

<span data-ttu-id="7ba68-125">Delve Multi-Geo è supportato per gli utenti di Office 365 nelle istanze satellite, con la limitazione che Delve consente il collegamento solo ai siti di blog di SharePoint di tali utenti e non ai post di blog di SharePoint scritti dagli utenti in altre regioni.</span><span class="sxs-lookup"><span data-stu-id="7ba68-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="7ba68-126">Cerca</span><span class="sxs-lookup"><span data-stu-id="7ba68-126">Search</span></span>

<span data-ttu-id="7ba68-p106">Ogni posizione geografica ha un proprio indice di ricerca e Centro ricerche. Quando si esegue la ricerca, la query viene inviata a tutte le posizioni geografiche e i risultati restituiti vengono uniti e quindi classificati in modo che l'utente ottenga risultati unificati. Gli utenti ottengono risultati da tutte le località geografiche indipendentemente dalla posizione geografica. Vedere [Configurare la ricerca di OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) per ulteriori dettagli.</span><span class="sxs-lookup"><span data-stu-id="7ba68-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="7ba68-131">Di seguito sono elencati i client di ricerca supportati:</span><span class="sxs-lookup"><span data-stu-id="7ba68-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="7ba68-132">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="7ba68-132">OneDrive for Business</span></span>

-   <span data-ttu-id="7ba68-133">Delve</span><span class="sxs-lookup"><span data-stu-id="7ba68-133">Delve</span></span>

-   <span data-ttu-id="7ba68-134">Home page di SharePoint</span><span class="sxs-lookup"><span data-stu-id="7ba68-134">SharePoint Home</span></span>

-   <span data-ttu-id="7ba68-135">Centro ricerche</span><span class="sxs-lookup"><span data-stu-id="7ba68-135">The Search Center</span></span>

-   <span data-ttu-id="7ba68-136">Applicazioni di ricerca personalizzate che utilizzano l'API ricerca SharePoint</span><span class="sxs-lookup"><span data-stu-id="7ba68-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="7ba68-137">OneDrive per iOS e Android</span><span class="sxs-lookup"><span data-stu-id="7ba68-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="7ba68-p107">L'app OneDrive per dispositivi mobili iOS e Android illustra i file di OneDrive e i file condivisi con l'utente indipendentemente dalla posizione geografica. La ricerca dalle app OneDrive mostra risultati pertinenti da tutte le posizioni geografiche. Scaricare la versione più recente di tali applicazioni.</span><span class="sxs-lookup"><span data-stu-id="7ba68-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="7ba68-141">Vedere [Usare OneDrive in iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) e [Usare OneDrive in Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) per ulteriori informazioni.</span><span class="sxs-lookup"><span data-stu-id="7ba68-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="7ba68-142">Funzionalità di Teams</span><span class="sxs-lookup"><span data-stu-id="7ba68-142">Teams Experience</span></span>

<span data-ttu-id="7ba68-p108">Teams ha funzionalità multi-geo. I file di OneDrive e i file visualizzati recentemente.vengono mostrati indipendentemente dalla posizione geografica dell'utente. @ fa riferimento all’utilizzo con utenti da tutte le posizioni geografiche.</span><span class="sxs-lookup"><span data-stu-id="7ba68-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
