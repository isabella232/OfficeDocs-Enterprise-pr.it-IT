---
title: Amministrare un ambiente multi-geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Informazioni sull'amministrazione di servizi SharePoint e OneDrive in un ambiente multi-geo.
ms.openlocfilehash: 596db0e2cffedc74a4840ae4427a3350ba1e27d8
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="179fd-103">Amministrare un ambiente multi-geo</span><span class="sxs-lookup"><span data-stu-id="179fd-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="179fd-104">Di seguito viene descritto come funzionano i servizi OneDrive e SharePoint in un ambiente multi-geo.</span><span class="sxs-lookup"><span data-stu-id="179fd-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="179fd-105">Esperienza dell'amministratore OneDrive</span><span class="sxs-lookup"><span data-stu-id="179fd-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="179fd-p101">L'[Interfaccia di amministrazione di OneDrive](https://admin.onedrive.com) è una scheda di **posizioni geografiche** nel riquadro di spostamento di sinistra che include una mappa delle posizioni geografiche in cui è possibile visualizzare e gestire le proprie posizioni geografiche. Utilizzare questa pagina per aggiungere o eliminare posizioni geografiche nel tenant.</span><span class="sxs-lookup"><span data-stu-id="179fd-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo-locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="179fd-108">Tassonomia</span><span class="sxs-lookup"><span data-stu-id="179fd-108">Taxonomy</span></span>

<span data-ttu-id="179fd-p102">Microsoft offre supporto per una [tassonomia](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) unificata per i metadati gestiti dell'organizzazione tra più posizioni geografiche, ospitando la scheda nella posizione centrale dell'azienda. È consigliabile gestire la tassonomia globale da una posizione centrale e aggiungere solo termini specifici sulla posizione alla tassonomia delle posizioni geografiche satelliti. I termini di tassonomia globale verranno sincronizzati con la posizione geografica satellite.</span><span class="sxs-lookup"><span data-stu-id="179fd-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite geo location’s Taxonomy. Global taxonomy terms will synchronize to the satellite geo locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="179fd-112">Condivisione</span><span class="sxs-lookup"><span data-stu-id="179fd-112">Sharing</span></span>

<span data-ttu-id="179fd-p103">Gli amministratori possono impostare e gestire criteri di condivisione per ognuna delle posizioni. I siti di OneDrive in ogni posizione geografica rispetteranno solo le impostazioni di condivisione specifiche per posizioni geografiche corrispondenti. Ad esempio, è possibile consentire la [condivisione esterna](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) per la posizione centrale, ma non per la posizione satellite o viceversa.) Si noti che le impostazioni di condivisione non consentono la configurazione delle limitazioni per la condivisione tra le posizioni geografiche.</span><span class="sxs-lookup"><span data-stu-id="179fd-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. (For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa.) Note that the sharing settings do not allow configuring sharing limitations between geo-locations.</span></span>

<span data-ttu-id="179fd-p104">Per OneDrive Multi-Geo, è necessario gestire le impostazioni di condivisione in tutte le posizioni geografiche, poiché queste non sono sincronizzate tra tenant. Per gestire la condivisione, visitare la pagina relativa alle [impostazioni di condivisione dell'interfaccia di amministrazione di OneDrive](https://admin.onedrive.com/?v=SharingSettings). Per impostazione predefinita la condivisione esterna è disponibile per qualunque utente in ogni posizione satellitare.</span><span class="sxs-lookup"><span data-stu-id="179fd-p104">For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant. To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="179fd-119">Applicazione profilo utente</span><span class="sxs-lookup"><span data-stu-id="179fd-119">User Profile Application</span></span>

<span data-ttu-id="179fd-p105">Esiste un'[applicazione profilo utente](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in ogni posizione geografica. Le informazioni del profilo di ogni utente si trovano nella relativa posizione geografica e sono a disposizione dell'amministratore per tale posizione.</span><span class="sxs-lookup"><span data-stu-id="179fd-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="179fd-p106">Se si dispone di proprietà personalizzate del profilo, è consigliabile usare lo stesso schema del profilo tra le aree geografiche e popolare le proprietà personalizzate del profilo anche in tutte le posizioni geografiche o laddove necessario. Per istruzioni su come popolare i dati dei profili utente a livello di programmazione, fare riferimento a [API di aggiornamento del profilo utente in blocco](https://docs.microsoft.com/it-IT/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)</span><span class="sxs-lookup"><span data-stu-id="179fd-p106">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed. For guidance regarding how to populate user profile data programmatically, please refer to the [Bulk User Profile Update API](https://docs.microsoft.com/it-IT/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="179fd-124">BCS, Archiviazione sicura, App</span><span class="sxs-lookup"><span data-stu-id="179fd-124">BCS: Secure Store Service</span></span>

<span data-ttu-id="179fd-125">Tutti i servizi BCS, Archiviazione sicura e App presentano istanze geografiche separate, pertanto l'amministratore di SharePoint Online deve gestirli e configurarli da ogni istanza geografica in cui desidera che siano presenti.</span><span class="sxs-lookup"><span data-stu-id="179fd-125">BCS, Secure Store, and Apps all have separate geo instances, therefore the SharePoint Online administrator should manage and configure these services from each geo instance where they want them to be present.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="179fd-126">Centro sicurezza e conformità</span><span class="sxs-lookup"><span data-stu-id="179fd-126">Security and Compliance Admin Center</span></span>

<span data-ttu-id="179fd-127">Per il tenant Multi-Geo esiste un centro di conformità centrale: [Centro sicurezza e conformità di Office 365](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span><span class="sxs-lookup"><span data-stu-id="179fd-127">There is one central compliance center for the Multi-Geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="179fd-128">Criteri di protezione delle informazioni (IP) e prevenzione della perdita di dati (DLP) </span><span class="sxs-lookup"><span data-stu-id="179fd-128">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="179fd-p107">È possibile impostare i criteri IP e DLP per OneDrive for Business nel Centro sicurezza e conformità, per cercare i criteri necessari per l'intero tenant o per gli utenti validi. Ad esempio: se si desidera selezionare un criterio per un utente di OneDrive in una località satellite, selezionare questa opzione per applicare i criteri a un OneDrive specifico e immettere l'url OneDrive dell'utente. Per indicazioni generali sulla creazione di criteri, vedere [Panoramica dei criteri di prevenzione della perdita dei dati](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e).</span><span class="sxs-lookup"><span data-stu-id="179fd-p107">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="179fd-132">I criteri DLP vengono sincronizzati automaticamente in base alle loro applicabilità per ciascuna posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="179fd-132">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="179fd-133">Non è possibile implementare i criteri di prevenzione della perdita dei dati e di protezione delle informazioni a tutti gli utenti in una posizione geografica attraverso l'interfaccia utente, è invece necessario selezionare gli account OneDrive applicabili per il criterio o applicare i criteri a livello globale a tutti gli account OneDrive.</span><span class="sxs-lookup"><span data-stu-id="179fd-133">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="179fd-134">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="179fd-134">eDiscovery</span></span> 

<span data-ttu-id="179fd-p108">Per impostazione predefinita, un manager o amministratore di eDiscovery di un tenant multi-geo potrà eseguire eDiscovery solo nella posizione centrale di tale tenant. Per supportare la possibilità di eseguire eDiscovery per le posizioni satelliti, è disponibile un nuovo parametro filtro di sicurezza di conformità denominato "Area" tramite PowerShell.</span><span class="sxs-lookup"><span data-stu-id="179fd-p108">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="179fd-137">L'amministratore globale di Office 365 deve assegnare le autorizzazioni di manager di eDiscovery per consentire ad altri di eseguire eDiscovery e assegnare un parametro "Area" nel filtro di sicurezza e conformità applicabile per specificare l'area per l'esecuzione di eDiscovery come posizione satellite, in caso contrario nessuna istanza di eDiscovery verrà eseguita per la posizione geografica satellite.</span><span class="sxs-lookup"><span data-stu-id="179fd-137">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="179fd-p109">Quando è impostato il ruolo di manager o amministratore di eDiscovery per una posizione geografica specifica, sarà possibile eseguire operazioni di ricerca eDiscovery solo per i siti di SharePoint e OneDrive che si trovano in tale posizione geografica. Se un manager o amministratore di eDiscovery tenta di cercare siti di SharePoint o OneDrive all'esterno dell'area specificata, non visualizzerà alcun risultato. Inoltre, quando il manager o amministratore di eDiscovery di un'area attiva un'esportazione, i dati vengono esportati nell'istanza di Azure di quest'area. Ciò consente alle organizzazioni di rimanere conformi, non permettendo di esportare contenuti oltre i confini controllati.</span><span class="sxs-lookup"><span data-stu-id="179fd-p109">When the eDiscovery Manager or Administrator role is set for a particular-geo location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that geo-location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified region, no results will be returned. Also, when the eDiscovery Manager or Administrator for a region triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="179fd-142">Tuttavia, se dovesse essere necessario per un manager di eDiscovery effettuare una ricerca in più aree di SharePoint, sarà necessario creare un altro account utente per il manager di eDiscovery, specificando l'area alternativa in cui si trovano i siti di OneDrive o SharePoint.</span><span class="sxs-lookup"><span data-stu-id="179fd-142">If it's necessary for an eDiscovery Manager to search across multiple SharePoint regions, another user account will need to be created for the eDiscovery Manager which specifies the alternate region where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="179fd-143"><strong>Posizioni geografiche supportate da Multi-Geo</strong></span><span class="sxs-lookup"><span data-stu-id="179fd-143"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="179fd-144"><strong>I dati esportati in eDiscovery per SharePoint saranno disponibili in questa posizione dati Blob di Azure...</strong></span><span class="sxs-lookup"><span data-stu-id="179fd-144"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="179fd-145"><strong>NAM</strong></span><span class="sxs-lookup"><span data-stu-id="179fd-145"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="179fd-146">Datacenter USA</span><span class="sxs-lookup"><span data-stu-id="179fd-146">US Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="179fd-147"><strong>EUR</strong></span><span class="sxs-lookup"><span data-stu-id="179fd-147"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="179fd-148">Datacenter Europa</span><span class="sxs-lookup"><span data-stu-id="179fd-148">Europe Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="179fd-149"><strong>APC</strong></span><span class="sxs-lookup"><span data-stu-id="179fd-149"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="179fd-150">Datacenter Asia orientale o sud-orientale</span><span class="sxs-lookup"><span data-stu-id="179fd-150">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="179fd-151"><strong>CAN</strong></span><span class="sxs-lookup"><span data-stu-id="179fd-151"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="179fd-152">Datacenter USA</span><span class="sxs-lookup"><span data-stu-id="179fd-152">US Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="179fd-153"><strong>AUS</strong></span><span class="sxs-lookup"><span data-stu-id="179fd-153"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="179fd-154">Datacenter Asia orientale o sud-orientale</span><span class="sxs-lookup"><span data-stu-id="179fd-154">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="179fd-155"><strong>KOR</strong></span><span class="sxs-lookup"><span data-stu-id="179fd-155"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="179fd-156">Posizione predefinita dei dati del tenant</span><span class="sxs-lookup"><span data-stu-id="179fd-156">Tenant's default data location</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="179fd-157"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="179fd-157"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="179fd-158">Datacenter Europa</span><span class="sxs-lookup"><span data-stu-id="179fd-158">Europe Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="179fd-159"><strong>JPN </strong></span><span class="sxs-lookup"><span data-stu-id="179fd-159"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="179fd-160">Datacenter Asia orientale o sud-orientale</span><span class="sxs-lookup"><span data-stu-id="179fd-160">South East or East Asia Data Centers</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="179fd-161">Per impostare il filtro di sicurezza e conformità di un'area geografica:</span><span class="sxs-lookup"><span data-stu-id="179fd-161">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="179fd-162">Aprire Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="179fd-162">Open Windows PowerShell.</span></span>

2.  <span data-ttu-id="179fd-163">Immettere</span><span class="sxs-lookup"><span data-stu-id="179fd-163">Enter</span></span>  
    <span data-ttu-id="179fd-164">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="179fd-164">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="179fd-165">$a = Import-PSSession $s -AllowClobber</span><span class="sxs-lookup"><span data-stu-id="179fd-165">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="179fd-166">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="179fd-166">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="179fd-167">Ad esempio: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="179fd-167">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="179fd-168">Vedere l’articolo [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) per ulteriori parametri e sintassi</span><span class="sxs-lookup"><span data-stu-id="179fd-168">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="179fd-169">Ricerca dei log di controllo</span><span class="sxs-lookup"><span data-stu-id="179fd-169">Audit log search</span></span>

<span data-ttu-id="179fd-p110">Un [log di controllo](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) per tutte le posizioni geografiche è disponibile dalla pagina di ricerca dei log di controllo di Office 365. Sono disponibili tutte le voci di log di controllo tra le varie aree geografiche, ad esempio, attività di utenti dell'area geografica NAM e EUR verranno visualizzate in un'unica vista dell'organizzazione e sarà possibile applicarvi i filtri esistenti per vedere le attività di un utente specifico.</span><span class="sxs-lookup"><span data-stu-id="179fd-p110">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your geo locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
