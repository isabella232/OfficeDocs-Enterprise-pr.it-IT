---
title: Esperienza utente in un ambiente multgeo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Per conoscere l'esperienza utente di SharePoint e OneDrive in un ambiente multi-geo.
ms.openlocfilehash: 91837883ef7c970674a500afa4fda9adfafc6d5b
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="98e6c-103">Esperienza utente in un ambiente multi-geo</span><span class="sxs-lookup"><span data-stu-id="98e6c-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="98e6c-104">Ecco cosa gli utenti visualizzeranno in una configurazione Multi-Geo OneDrive:</span><span class="sxs-lookup"><span data-stu-id="98e6c-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="98e6c-105">OneDrive dell'utente per sede aziendale</span><span class="sxs-lookup"><span data-stu-id="98e6c-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="98e6c-p101">Gli utenti potranno loro OneDrive for Business eseguito il provisioning nel relativo percorso dati preferita. Se un utente accede a un URL OneDrive che contiene una posizione geografica non corretta (ad esempio un segnalibro da una posizione geografica precedente), vengono reindirizzate automaticamente alla OneDrive nella posizione geografica appropriata.</span><span class="sxs-lookup"><span data-stu-id="98e6c-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="98e6c-108">Condivisione</span><span class="sxs-lookup"><span data-stu-id="98e6c-108">Sharing</span></span>

<span data-ttu-id="98e6c-p102">L'esperienza di selezione utenti Mostra tutti gli utenti indipendentemente dalla posizione geografica. Ciò consente di condividere con altri utenti nella loro geo stesso o in qualsiasi altro della località geografica del tenant. Contenuto disponibile nei geo diversa posizioni verranno visualizzata nella visualizzazione **condiviso con Me** in OneDrive dell'utente for Business ed sono accessibile con Single Sign-On esperienza indipendentemente dalla quale ubicazione geografica è ospitata in.</span><span class="sxs-lookup"><span data-stu-id="98e6c-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="98e6c-112">Applicazioni di Office</span><span class="sxs-lookup"><span data-stu-id="98e6c-112">Office applications</span></span>

<span data-ttu-id="98e6c-p103">Applicazioni di Office come Word, Excel e PowerPoint rileva automaticamente il corretto OneDrive for Business geo-percorso per ciascun utente al momento dell'accesso. Gli utenti non devono immettere l'URL geo specifiche per i OneDrive.</span><span class="sxs-lookup"><span data-stu-id="98e6c-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="98e6c-115">OneDrive for Business Client di sincronizzazione</span><span class="sxs-lookup"><span data-stu-id="98e6c-115">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="98e6c-116">OneDrive for Business sincronizzazione Client (versione 17.3.6943.0625 e versioni successive) rileva automaticamente il corretto OneDrive per la posizione geografica Business per l'utente.</span><span class="sxs-lookup"><span data-stu-id="98e6c-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="98e6c-117">Avvio app di Office 365</span><span class="sxs-lookup"><span data-stu-id="98e6c-117">Office 365 app launcher</span></span>

<span data-ttu-id="98e6c-p104">Il servizio di avvio di app è Multi-Geo e otterranno indicazioni ogni tessera alla posizione geografica appropriato del carico di lavoro. I punti di sezioni OneDrive nella posizione corretta geo cui è ospitato libreria di OneDrive dell'utente, mentre le sezioni di SharePoint saranno posiziona tutti gli utenti nella posizione centrale come siti del team sono ospitati disponibili.</span><span class="sxs-lookup"><span data-stu-id="98e6c-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="98e6c-120">Approfondire profili utente</span><span class="sxs-lookup"><span data-stu-id="98e6c-120">Delve User profiles</span></span>

<span data-ttu-id="98e6c-p105">Informazioni dei profili utente sono gestite nella posizione geografica dell'utente. Quando si seleziona un utente, si verrà indirizzati alla posizione geografica appropriato per l'utente, dove verranno visualizzati i relativi dettagli completa dei profili.</span><span class="sxs-lookup"><span data-stu-id="98e6c-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="98e6c-123">Se Delve è disattivata, verrà visualizzato il profilo classico esperienza in SharePoint, non ovvero multi-geo.</span><span class="sxs-lookup"><span data-stu-id="98e6c-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="98e6c-124">Delve</span><span class="sxs-lookup"><span data-stu-id="98e6c-124">Delve</span></span>

<span data-ttu-id="98e6c-125">Per gli utenti di Office 365 che si trovano in istanze satellitari, approfondire Multi-Geo è supportato con le limitazioni Delve non consente di collegarsi al post di blog di SharePoint scritti da parte di utenti in altre aree, solo per i siti blog di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="98e6c-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="98e6c-126">Ricerca</span><span class="sxs-lookup"><span data-stu-id="98e6c-126">Search</span></span>

<span data-ttu-id="98e6c-p106">Ogni località geografica ha indice di ricerca e Centro ricerche. Quando un utente esegue la ricerca, la query viene inviata a tutti i percorsi geo e i risultati restituiti vengono uniti e quindi classificati in modo che l'utente ottiene risultati unificati. Gli utenti di ottenere i risultati da tutti i percorsi geo indipendentemente dalla posizione geografica. Per informazioni dettagliate, vedere [Configurare la ricerca di OneDrive per Business Multi-Geo](configure-search-for-multi-geo.md) .</span><span class="sxs-lookup"><span data-stu-id="98e6c-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="98e6c-131">Sono supportati i client di ricerca seguenti:</span><span class="sxs-lookup"><span data-stu-id="98e6c-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="98e6c-132">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="98e6c-132">OneDrive for Business</span></span>

-   <span data-ttu-id="98e6c-133">Delve</span><span class="sxs-lookup"><span data-stu-id="98e6c-133">Delve</span></span>

-   <span data-ttu-id="98e6c-134">Home page di SharePoint</span><span class="sxs-lookup"><span data-stu-id="98e6c-134">SharePoint Home</span></span>

-   <span data-ttu-id="98e6c-135">Centro ricerche</span><span class="sxs-lookup"><span data-stu-id="98e6c-135">The Search Center</span></span>

-   <span data-ttu-id="98e6c-136">Applicazioni di ricerca personalizzate che utilizzano l'API di ricerca di SharePoint</span><span class="sxs-lookup"><span data-stu-id="98e6c-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="98e6c-137">IOS OneDrive e Android</span><span class="sxs-lookup"><span data-stu-id="98e6c-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="98e6c-p107">Il iOS OneDrive e App per dispositivi mobili Android visualizzerà i file di OneDrive e file condivisi con l'utente indipendentemente dalla posizione geografica. Ricerca dalle App per dispositivi mobili OneDrive consentirà di visualizzare risultati pertinenti da tutti i percorsi geo. Scaricare la versione più recente di queste applicazioni.</span><span class="sxs-lookup"><span data-stu-id="98e6c-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="98e6c-141">Per ulteriori informazioni, vedere Utilizzo di [OneDrive su iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) e [Utilizzare OneDrive per Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) .</span><span class="sxs-lookup"><span data-stu-id="98e6c-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="98e6c-142">Esperienza di team</span><span class="sxs-lookup"><span data-stu-id="98e6c-142">Teams Experience</span></span>

<span data-ttu-id="98e6c-p108">I team è multi-geo. Indipendentemente dalla posizione geografica dell'utente vengono visualizzati i file di OneDrive e visualizzati di recente. @ menzioni lavoro con gli utenti da tutti i percorsi di livello geografico.</span><span class="sxs-lookup"><span data-stu-id="98e6c-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
