---
title: Abilitazione di SharePoint Multi-Geo in una posizione geografica satellite
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Abilitazione di SharePoint Multi-Geo in una posizione geografica satellite.
ms.openlocfilehash: 98666f76a5b3ec055a6f26d30f502c3cc6b6d3bb
ms.sourcegitcommit: 0ddd9b0c9c23dc6479dce9f5701b69d533d76127
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "31025190"
---
# <a name="enabling-sharepoint-multi-geo-in-your-satellite-geo-location"></a><span data-ttu-id="d6be2-103">Abilitazione di SharePoint Multi-Geo in una posizione geografica satellite</span><span class="sxs-lookup"><span data-stu-id="d6be2-103">Enabling SharePoint Multi-Geo in your satellite geo location</span></span>

<span data-ttu-id="d6be2-104">Questo articolo è rivolto agli amministratori globali o di SharePoint che hanno creato una località satellite Multi-Geo **prima** che la funzionalità di SharePoint diventasse disponibile il 27 marzo 2019 e che non hanno abilitato SharePoint Multi-Geo nella/e posizione/i geografica/che satellite.</span><span class="sxs-lookup"><span data-stu-id="d6be2-104">This article is for Global or SharePoint administrators who have created a Multi-Geo satellite location **before** SharePoint Multi-Geo capabilities became generally available on March 27, 2019, and who have not enabled SharePoint Multi-Geo in their satellite geo location(s).</span></span> 

>[!Note]
><span data-ttu-id="d6be2-105">Se è stata aggiunta una nuova posizione geografica **dopo il 27 marzo**, non è necessario eseguire queste istruzioni, poiché la nuova posizione sarà stata già attivata per Multi-Geo di OneDrive e SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d6be2-105">If you have added a new geo location **after March 27th**, you do not need to perform these instructions, as your new geo location will already be enabled for OneDrive and SharePoint Multi-Geo.</span></span>

<span data-ttu-id="d6be2-106">Queste istruzioni consentono di abilitare SharePoint nella posizione satellite, per consentire agli utenti di Multi-Geo di usufruire della funzionalità di OneDrive e SharePoint in O365.</span><span class="sxs-lookup"><span data-stu-id="d6be2-106">These instructions will allow you to enable SharePoint in your satellite location, so your Multi-Geo satellite users can take advantage of both OneDrive and SharePoint Multi-Geo capabilities in O365.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="d6be2-107">Tenere presente che si tratta di un'abilitazione unidirezionale.</span><span class="sxs-lookup"><span data-stu-id="d6be2-107">Please note that this is a one way enablement.</span></span> <span data-ttu-id="d6be2-108">Dopo aver impostato la modalità SPO, non sarà più possibile ripristinare il tenant in modalità Multi-Geo solo per OneDrive senza il ricorso all’assistenza.</span><span class="sxs-lookup"><span data-stu-id="d6be2-108">Once you set SPO mode, you will not be able to revert your tenant to OneDrive only Multi-Geo mode without an escalation with support.</span></span> 

## <a name="to-set-a-geo-location-into-spo-mode"></a><span data-ttu-id="d6be2-109">Impostare una posizione geografica in modalità SPO</span><span class="sxs-lookup"><span data-stu-id="d6be2-109">To set a geo location into SPO Mode</span></span>

<span data-ttu-id="d6be2-110">Per impostare una posizione geografica in modalità SPO, connettersi alla posizione geografica che si vuole impostare:</span><span class="sxs-lookup"><span data-stu-id="d6be2-110">To set a geo location into SPO mode, connect to the geo location you want to set in SPO Mode:</span></span>

1.  <span data-ttu-id="d6be2-111">Aprire SharePoint Online Management Shell.</span><span class="sxs-lookup"><span data-stu-id="d6be2-111">Open your SharePoint Online Management Shell</span></span> 
2.  <span data-ttu-id="d6be2-112">Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com"-Credential $credential</span><span class="sxs-lookup"><span data-stu-id="d6be2-112">Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -Credential $credential</span></span>
3.  <span data-ttu-id="d6be2-113">Set-SPOMultiGeoExperience</span><span class="sxs-lookup"><span data-stu-id="d6be2-113">Set-SPOMultiGeoExperience</span></span></br></br>
<span data-ttu-id="d6be2-114">![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)</span><span class="sxs-lookup"><span data-stu-id="d6be2-114">![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)</span></span>
4.  <span data-ttu-id="d6be2-115">Questa operazione in genere richiede circa un'ora, mentre si eseguono varie pubblicazioni nel servizio e viene ricopiato il tenant.</span><span class="sxs-lookup"><span data-stu-id="d6be2-115">This operation usually takes about an hour while we perform various publish backs in the service and re-stamp your tenant.</span></span> <span data-ttu-id="d6be2-116">Dopo circa 1 ora, eseguire un Get-SPOMultiGeoExperience.</span><span class="sxs-lookup"><span data-stu-id="d6be2-116">After at least 1 hour, please perform a Get-SPOMultiGeoExperience.</span></span>  <span data-ttu-id="d6be2-117">Servirà per visualizzare se la posizione geografica è in modalità di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="d6be2-117">This will show you whether this geo location is in SPO mode.</span></span></br></br>
<span data-ttu-id="d6be2-118">![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)</span><span class="sxs-lookup"><span data-stu-id="d6be2-118">![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)</span></span>

 
 
 
>[!Note]
><span data-ttu-id="d6be2-119">Alcune cache del servizio eseguono aggiornamenti ogni 24 ore, quindi è possibile durante questo periodo di 24 ore che la posizione geografica satellite occasionalmente si comporti come se fosse ancora in modalità ODB.</span><span class="sxs-lookup"><span data-stu-id="d6be2-119">Certain caches in the service update every 24 hours, so it is possible that for a period of up to 24 hours, your satellite geo may intermittently behave as if it was still in ODB mode.</span></span> <span data-ttu-id="d6be2-120">Questo non causa problemi tecnici.</span><span class="sxs-lookup"><span data-stu-id="d6be2-120">This does not cause any technical issues.</span></span> 
 
<span data-ttu-id="d6be2-121">Per ulteriori informazioni su SharePoint Multi-Geo visitare [aka.ms/sharepointmultigeo](https://docs.microsoft.com/it-IT/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)</span><span class="sxs-lookup"><span data-stu-id="d6be2-121">For additional information regarding SharePoint Multi-Geo, please refer to [aka.ms/sharepointmultigeo](https://docs.microsoft.com/it-IT/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)</span></span>


