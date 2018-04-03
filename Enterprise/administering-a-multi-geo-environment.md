---
title: Amministrazione di un ambiente multi-geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Informazioni sull'amministrazione di servizi di SharePoint e OneDrive in un ambiente multi-geo.
ms.openlocfilehash: f49cf35503ee6495b5982dc7d72f9b1936f564c6
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="b2b86-103">Amministrazione di un ambiente multi-geo</span><span class="sxs-lookup"><span data-stu-id="b2b86-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="b2b86-104">Di seguito vengono esaminate funzionamento OneDrive e SharePoint services in un ambiente multi-geo.</span><span class="sxs-lookup"><span data-stu-id="b2b86-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="b2b86-105">Esperienza dell'amministratore OneDrive</span><span class="sxs-lookup"><span data-stu-id="b2b86-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="b2b86-p101">[Interfaccia di amministrazione di OneDrive](https://admin.onedrive.com) è disponibile una scheda **percorsi Geo** nel riquadro di spostamento sinistra le caratteristiche di mappare una località geografica dove è possibile visualizzare e gestire le posizioni geo. Utilizzare questa pagina per aggiungere o eliminare geo percorsi per il tenant.</span><span class="sxs-lookup"><span data-stu-id="b2b86-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo-locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="b2b86-108">Tassonomia</span><span class="sxs-lookup"><span data-stu-id="b2b86-108">Taxonomy</span></span>

<span data-ttu-id="b2b86-p102">È supportata una [tassonomia](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) unificato per i metadati aziendali gestiti da diverse ubicazioni geo, con il master ospitato in una posizione centralizzata per la propria azienda. È consigliabile gestire la tassonomia globale da una posizione centrale e tassonomia dell'ubicazione geografica satellitari solo aggiungere condizioni specifiche di una posizione. Termini tassonomia globali verranno sincronizzati per i percorsi di geo satellitari.</span><span class="sxs-lookup"><span data-stu-id="b2b86-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite geo location’s Taxonomy. Global taxonomy terms will synchronize to the satellite geo locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="b2b86-112">Condivisione</span><span class="sxs-lookup"><span data-stu-id="b2b86-112">Sharing</span></span>

<span data-ttu-id="b2b86-p103">Gli amministratori possono impostare e gestire i criteri di condivisione per ognuno dei rispettivi percorsi. I siti di OneDrive in ogni località geografica rispetta solo il corrispondente geo specifiche impostazioni di condivisione. Ad esempio, è possibile consentire [condivisione esterna](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) per la propria posizione centrale, ma non per la viceversa satellitari posizione o viceversa. Per OneDrive Multi-Geo, è necessario gestire le impostazioni di condivisione in ogni punto geo come questi non sono sincronizzati tra il tenant.</span><span class="sxs-lookup"><span data-stu-id="b2b86-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa. For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant.</span></span>

<span data-ttu-id="b2b86-p104">Per gestire condivisione visita la pagina di [interfaccia di amministrazione di OneDrive impostazioni di condivisione](https://admin.onedrive.com/?v=SharingSettings) . Per impostazione predefinita condivisione esterna è compatibile con tutti gli utenti in ogni punto satellitari.</span><span class="sxs-lookup"><span data-stu-id="b2b86-p104">To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="b2b86-119">Applicazione profili utente</span><span class="sxs-lookup"><span data-stu-id="b2b86-119">User Profile Application</span></span>

<span data-ttu-id="b2b86-p105">In ogni località geografica esiste un' [applicazione profili utente](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) . Informazioni sul profilo di ogni utente è ospitati nella posizione geografica e disponibili per l'amministratore di tale posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="b2b86-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="b2b86-122">Se si dispone di proprietà di profilo personalizzate, è consigliabile utilizzare lo stesso schema di profili in aree geografiche e popolare la proprietà di profilo personalizzate in tutti i percorsi geo o in caso di necessità.</span><span class="sxs-lookup"><span data-stu-id="b2b86-122">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed.</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="b2b86-123">Servizi di integrazione Applicativa, servizio di archiviazione sicura, App</span><span class="sxs-lookup"><span data-stu-id="b2b86-123">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="b2b86-124">Servizi di integrazione Applicativa, servizio di archiviazione sicura e App presenti istanze geo separato, pertanto l'amministratore di SharePoint Online deve gestire e configurare questi servizi da ogni istanza geografica in cui si desidera visualizzarli deve essere presente.</span><span class="sxs-lookup"><span data-stu-id="b2b86-124">BCS, Secure Store, and Apps all have separate geo instances, therefore the SharePoint Online administrator should manage and configure these services from each geo instance where they want them to be present.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="b2b86-125">Sicurezza e conformità Admin Center</span><span class="sxs-lookup"><span data-stu-id="b2b86-125">Security and Compliance Admin Center</span></span>

<span data-ttu-id="b2b86-126">Non esiste un solo centro conformità centrale per il tenant Multi-Geo: [centro conformità e sicurezza di Office 365](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span><span class="sxs-lookup"><span data-stu-id="b2b86-126">There is one central compliance center for the Multi-Geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="b2b86-127">Criteri di criterio DLP perdita di dati di informazioni protezione IP)</span><span class="sxs-lookup"><span data-stu-id="b2b86-127">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="b2b86-p106">È possibile impostare il DLP IP criteri relativi a OneDrive for Business in Centro protezione e la conformità ambito criteri in base alle esigenze per il tenant intero o a utenti applicabili. Ad esempio: se si desidera selezionare un criterio per un utente di OneDrive in una posizione satellitare, selezionare questa opzione per applicare il criterio a una specifica OneDrive e immettere il nome utente dell'url OneDrive. Per indicazioni generali per la creazione di criteri DLP, vedere [Panoramica di criteri di prevenzione della perdita di dati](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) .</span><span class="sxs-lookup"><span data-stu-id="b2b86-p106">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="b2b86-131">I criteri DLP sono sincronizzati automaticamente in base alle loro applicabilità per ogni località geografica.</span><span class="sxs-lookup"><span data-stu-id="b2b86-131">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="b2b86-132">L'implementazione dei criteri di prevenzione della perdita di dati e la protezione delle informazioni per tutti gli utenti in una posizione geografica, non è un'opzione disponibile nell'interfaccia utente, ma è necessario selezionare l'account OneDrive applicabile per il criterio o applicare i criteri a livello globale per tutti gli account OneDrive.</span><span class="sxs-lookup"><span data-stu-id="b2b86-132">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="b2b86-133">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="b2b86-133">eDiscovery</span></span> 

<span data-ttu-id="b2b86-p107">Per impostazione predefinita, una ricerca eDiscovery responsabile o amministratore di un tenant multi-geo sarà in grado di condurre eDiscovery solo in una posizione centrale che tenant. Per supportare la possibilità di eseguire eDiscovery per i percorsi satellitare, è disponibile tramite PowerShell un nuovo parametro di filtro di sicurezza per conformità denominato "Region".</span><span class="sxs-lookup"><span data-stu-id="b2b86-p107">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="b2b86-136">Amministratore globale di Office 365 necessario assegnare le autorizzazioni di gestione di eDiscovery per consentire ad altri eseguire eDiscovery e assegnare un parametro "Region" nel loro applicabile filtro di protezione di conformità per specificare il paese per eseguire eDiscovery come satellitari posizione, in caso contrario che non eDiscovery verranno eseguite per la posizione satellitare.</span><span class="sxs-lookup"><span data-stu-id="b2b86-136">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="b2b86-p108">Quando il ruolo di responsabile o amministratore di eDiscovery è impostato per una posizione geografica particolare, eDiscovery responsabile o amministratore solo sarà in grado di eseguire operazioni di ricerca di eDiscovery contro i siti di SharePoint e i siti OneDrive disponibile in tale posizione geografica. Se un amministratore o eDiscovery Manager tenta di cercare i siti di SharePoint o OneDrive all'esterno della regione specificato, non verrà restituito alcun risultato. Inoltre, quando eDiscovery responsabile o amministratore di un'area attiva un'esportazione, dati vengono esportati in Azure istanza di tale area. Consente alle organizzazioni di mantenere in conformità non consentendo contenuto tra i bordi controllati da esportare.</span><span class="sxs-lookup"><span data-stu-id="b2b86-p108">When the eDiscovery Manager or Administrator role is set for a particular-geo location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that geo-location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified region, no results will be returned. Also, when the eDiscovery Manager or Administrator for a region triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="b2b86-141">Se è necessario che una responsabile per la ricerca in più aree di SharePoint di eDiscovery, sarà necessario un account utente diverso da creare per la gestione che specifica la regione alternativa in cui si trovano i siti di SharePoint o OneDrive eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="b2b86-141">If it's necessary for an eDiscovery Manager to search across multiple SharePoint regions, another user account will need to be created for the eDiscovery Manager which specifies the alternate region where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="b2b86-142"><strong>Multi-Geo supportati Geo percorsi</strong></span><span class="sxs-lookup"><span data-stu-id="b2b86-142"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="b2b86-143"><strong>sarà eDiscovery per SharePoint esportati i dati in questo percorso di dati Blob di Azure...</strong></span><span class="sxs-lookup"><span data-stu-id="b2b86-143"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="b2b86-144"><strong>NOME</strong></span><span class="sxs-lookup"><span data-stu-id="b2b86-144"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="b2b86-145">Usa Data Center</span><span class="sxs-lookup"><span data-stu-id="b2b86-145">US Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b2b86-146"><strong>EUR</strong></span><span class="sxs-lookup"><span data-stu-id="b2b86-146"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="b2b86-147">Europa Data Center</span><span class="sxs-lookup"><span data-stu-id="b2b86-147">Europe Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b2b86-148"><strong>APC</strong></span><span class="sxs-lookup"><span data-stu-id="b2b86-148"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="b2b86-149">Sud-Est o centri dati Asia orientale</span><span class="sxs-lookup"><span data-stu-id="b2b86-149">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b2b86-150"><strong>POSSIBILE</strong></span><span class="sxs-lookup"><span data-stu-id="b2b86-150"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="b2b86-151">Usa Data Center</span><span class="sxs-lookup"><span data-stu-id="b2b86-151">US Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b2b86-152"><strong>AUSTRALIA</strong></span><span class="sxs-lookup"><span data-stu-id="b2b86-152"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="b2b86-153">Sud-Est o centri dati Asia orientale</span><span class="sxs-lookup"><span data-stu-id="b2b86-153">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b2b86-154"><strong>(COREANO)</strong></span><span class="sxs-lookup"><span data-stu-id="b2b86-154"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="b2b86-155">Percorso dei dati del tenant predefinito</span><span class="sxs-lookup"><span data-stu-id="b2b86-155">Tenant's default data location</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b2b86-156"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="b2b86-156"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="b2b86-157">Europa Data Center</span><span class="sxs-lookup"><span data-stu-id="b2b86-157">Europe Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b2b86-158"><strong>GIAPPONESE</strong></span><span class="sxs-lookup"><span data-stu-id="b2b86-158"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="b2b86-159">Sud-Est o centri dati Asia orientale</span><span class="sxs-lookup"><span data-stu-id="b2b86-159">South East or East Asia Data Centers</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="b2b86-160">Per impostare il filtro di protezione di conformità per un'area:</span><span class="sxs-lookup"><span data-stu-id="b2b86-160">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="b2b86-161">Apri Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b2b86-161">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="b2b86-162">Immetti </span><span class="sxs-lookup"><span data-stu-id="b2b86-162">Enter</span></span>  
    <span data-ttu-id="b2b86-163">$s = New-PSSession - ConfigurationName Microsoft.Exchange - ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -credenziali $cred-autenticazione base - AllowRedirection - SessionOption (PSSessionOption New - SkipCACheck - SkipCNCheck - SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="b2b86-163">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="b2b86-164">$un = Import-PSSession $s - AllowClobber</span><span class="sxs-lookup"><span data-stu-id="b2b86-164">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="b2b86-165">**Nuovo ComplianceSecurityFilter** **-Azione** TUTTO **- FilterName** EnterTheNameYouWantToAssign **-area** EnterTheRegionParameter **-utenti** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="b2b86-165">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="b2b86-166">Ad esempio: **Nuovo ComplianceSecurityFilter-azione** NAMEDISCOVERYMANAGERS **- FilterName** tutti **-area** nome **-gli utenti** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="b2b86-166">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="b2b86-167">Vedere l'articolo [New ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) per altri parametri e sintassi</span><span class="sxs-lookup"><span data-stu-id="b2b86-167">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="b2b86-168">Ricerca dei log di controllo</span><span class="sxs-lookup"><span data-stu-id="b2b86-168">Audit log search</span></span>

<span data-ttu-id="b2b86-p109">Un unificato di [Registro di controllo](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) per tutti i percorsi geo è disponibile nella pagina ricerca di Office 365 audit log. È possibile visualizzare tutte le voci del Registro di controllo da tra geos, ad esempio, attività nomi & EUR geo degli utenti verrà visualizzata in una singola visualizzazione org e quindi è possibile applicare filtri esistenti per visualizzare le attività dell'utente specifico.</span><span class="sxs-lookup"><span data-stu-id="b2b86-p109">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your geo locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
