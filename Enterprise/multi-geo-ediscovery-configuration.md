---
title: Configurare eDiscovery per Office 365 multi-geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Informazioni su come configurare eDiscovery in Office 365 multi-geo.
ms.openlocfilehash: f9d8fe8b65f5772005bf7d6a7ea3735277077d3b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069962"
---
# <a name="office-365-multi-geo-ediscovery-configuration"></a><span data-ttu-id="3b5cf-103">Configurazione di eDiscovery per Office 365 multi-geo</span><span class="sxs-lookup"><span data-stu-id="3b5cf-103">Office 365 Multi-Geo eDiscovery configuration</span></span>


<span data-ttu-id="3b5cf-p101">Per impostazione predefinita, un manager o amministratore di eDiscovery di un tenant multi-geo potrà eseguire eDiscovery solo nella posizione centrale di tale tenant. Per supportare la possibilità di eseguire eDiscovery per le posizioni satelliti, è disponibile un nuovo parametro filtro di sicurezza di conformità denominato "Area" tramite PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3b5cf-p101">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="3b5cf-106">L'amministratore globale di Office 365 deve assegnare le autorizzazioni di manager di eDiscovery per consentire ad altri di eseguire eDiscovery e assegnare un parametro "Area" nel filtro di sicurezza e conformità applicabile per specificare l'area per l'esecuzione di eDiscovery come posizione satellite, in caso contrario nessuna istanza di eDiscovery verrà eseguita per la posizione geografica satellite.</span><span class="sxs-lookup"><span data-stu-id="3b5cf-106">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="3b5cf-p102">Quando è impostato il ruolo di manager o amministratore di eDiscovery per una posizione satellite specifica, sarà possibile eseguire operazioni di ricerca eDiscovery solo per i siti di SharePoint e OneDrive che si trovano in tale posizione satellite. Se un manager o amministratore di eDiscovery tenta di cercare siti di SharePoint o OneDrive all'esterno della posizione satellite specificata, non visualizzerà alcun risultato. Inoltre, quando il manager o amministratore di eDiscovery di una posizione satellite attiva un'esportazione, i dati vengono esportati nell'istanza di Azure di quest'area. Ciò consente alle organizzazioni di rimanere conformi, non permettendo di esportare contenuti oltre i confini controllati.</span><span class="sxs-lookup"><span data-stu-id="3b5cf-p102">When the eDiscovery Manager or Administrator role is set for a particular satellite location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that satellite location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified satellite location, no results will be returned. Also, when the eDiscovery Manager or Administrator for a satellite location triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="3b5cf-111">Tuttavia, se dovesse essere necessario per un manager di eDiscovery effettuare una ricerca in più posizioni satellite di SharePoint, sarà necessario creare un altro account utente per il manager di eDiscovery, specificando la posizione satellite alternativa in cui si trovano i siti di OneDrive o SharePoint.</span><span class="sxs-lookup"><span data-stu-id="3b5cf-111">If it's necessary for an eDiscovery Manager to search across multiple SharePoint satellite locations, another user account will need to be created for the eDiscovery Manager which specifies the alternate satellite location where the OneDrive or SharePoint sites are located.</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

<span data-ttu-id="3b5cf-112">Per impostare il filtro di sicurezza di conformità per un'area geografica:</span><span class="sxs-lookup"><span data-stu-id="3b5cf-112">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="3b5cf-113">Aprire Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3b5cf-113">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="3b5cf-114">Immettere</span><span class="sxs-lookup"><span data-stu-id="3b5cf-114">Enter</span></span>  
    <span data-ttu-id="3b5cf-115">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="3b5cf-115">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="3b5cf-116">$a = Import-PSSession $s -AllowClobber</span><span class="sxs-lookup"><span data-stu-id="3b5cf-116">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="3b5cf-117">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="3b5cf-117">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="3b5cf-118">Ad esempio: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="3b5cf-118">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="3b5cf-119">Vedere l’articolo [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) per ulteriori parametri e sintassi</span><span class="sxs-lookup"><span data-stu-id="3b5cf-119">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>
