---
title: Guida sulla sicurezza Microsoft per organizzazioni che si occupano della campagna politica, no profit e altre organizzazioni agili
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.custom: Strat_O365_Enterprise
ms.assetid: 10d1004b-42b6-4e2b-aaa2-18ddd9118f64
description: 'Riepilogo: Pianificazione e implementazione per lo spostamento di fast organizzazioni che dispongono di un profilo di rischio maggiore.'
ms.openlocfilehash: 7b400a1c097bb1d3906a59dfd21461df0568c76a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations"></a><span data-ttu-id="51fab-103">Guida sulla sicurezza Microsoft per organizzazioni che si occupano della campagna politica, no profit e altre organizzazioni agili</span><span class="sxs-lookup"><span data-stu-id="51fab-103">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>

 <span data-ttu-id="51fab-104">**Riepilogo:** Pianificazione e implementazione istruzioni relative allo spostamento fast organizzazioni che dispongono di un profilo di rischio maggiore.</span><span class="sxs-lookup"><span data-stu-id="51fab-104">**Summary:** Planning and implementation guidance for fast-moving organizations that have an increased threat profile.</span></span>
  
<span data-ttu-id="51fab-p101">Questa guida è utile se la propria organizzazione è agile, si dispone di un piccolo team IT e il proprio profilo è più a rischio rispetto alla media. Questa soluzione mostra come creare rapidamente un ambiente con i servizi cloud essenziali che includono controlli della sicurezza. Questa guida comprende suggerimenti sulla sicurezza per proteggere i dati, le identità, i messaggi di posta elettronica e l'accesso dai dispositivi mobili.</span><span class="sxs-lookup"><span data-stu-id="51fab-p101">If your organization is agile, you have a small IT team, and your threat profile is higher than average, this guidance is designed for you. This solution demonstrates how to quickly build an environment with essential cloud services that include secure controls from the start. This guidance includes prescriptive security recommendations for protecting data, identities, email, and access from mobile devices.</span></span>
  
## <a name="security-solution-guidance"></a><span data-ttu-id="51fab-108">Guida alle soluzioni di protezione</span><span class="sxs-lookup"><span data-stu-id="51fab-108">Security solution guidance</span></span>

<span data-ttu-id="51fab-p102">Questa guida viene descritto come implementare un ambiente protetto basato su cloud. Informazioni sulle soluzioni può essere utilizzato da tutte le organizzazioni. Include informazioni supplementari per le organizzazioni agile con account di accesso e guest BYOD. È possibile utilizzare questa guida come punto di partenza per la progettazione al proprio ambiente. Invitiamo i commenti e suggerimenti a [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="51fab-p102">This guidance describes how to implement a secure cloud environment. The solution guidance can be used by any organization. It includes extra help for agile organizations with BYOD access and guest accounts. You can use this guidance as a starting-point for designing your own environment. We welcome your feedback at [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span></span> 
  
|||
|:-----|:-----|
|<span data-ttu-id="51fab-114">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="51fab-114">**Item**</span></span> <br/> |<span data-ttu-id="51fab-115">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="51fab-115">**Description**</span></span> <br/> |
|<span data-ttu-id="51fab-116">**Microsoft Security Guidance for campagne politiche**</span><span class="sxs-lookup"><span data-stu-id="51fab-116">**Microsoft Security Guidance for Political Campaigns**</span></span> <br/> <span data-ttu-id="51fab-117">[![Martello generale per set di formattazione rapida poster.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span><span class="sxs-lookup"><span data-stu-id="51fab-117">[![Thumb nail for mini poster set.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span></span> <br/> <span data-ttu-id="51fab-118">[VERSIONE PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)  \\</span><span class="sxs-lookup"><span data-stu-id="51fab-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)  \\</span></span>| [<span data-ttu-id="51fab-119">Visio</span><span class="sxs-lookup"><span data-stu-id="51fab-119">Visio</span></span>](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.vsdx) <br/> |<span data-ttu-id="51fab-p103">Questa guida utilizza un'organizzazione impegnata nella campagna politica come esempio. Utilizzare questa guida come punto di partenza per qualsiasi ambiente. </span><span class="sxs-lookup"><span data-stu-id="51fab-p103">This guidance uses a political campaign organization as an example. Use this guidance as a starting point for any environment.</span></span>  <br/> |
|<span data-ttu-id="51fab-122">**Microsoft Security Guidance for ricchi**</span><span class="sxs-lookup"><span data-stu-id="51fab-122">**Microsoft Security Guidance for Nonprofits**</span></span> <br/> <span data-ttu-id="51fab-123">[![Immagine di anteprima per file scaricabili](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span><span class="sxs-lookup"><span data-stu-id="51fab-123">[![Thumnail image for downloadable file](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span></span> <br/> <span data-ttu-id="51fab-124">[VERSIONE PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)  \\</span><span class="sxs-lookup"><span data-stu-id="51fab-124">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)  \\</span></span>| [<span data-ttu-id="51fab-125">Visio</span><span class="sxs-lookup"><span data-stu-id="51fab-125">Visio</span></span>](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.vsdx) <br/> |<span data-ttu-id="51fab-p104">Questa guida è stata leggermente modificata per le organizzazioni no profit. Ad esempio, fa riferimento ai piani di Office 365 Nonprofit. Le indicazioni tecniche sono identiche a quelle fornite nella guida alle soluzioni per le campagne politiche.</span><span class="sxs-lookup"><span data-stu-id="51fab-p104">This guide is slightly revised for nonprofit organizations. For example, it references Office 365 Nonprofit plans. The technical guidance is the same as the political campaign solution guide.</span></span>  <br/> |
   
## <a name="test-lab-guides"></a><span data-ttu-id="51fab-129">Guide dei laboratori di testing</span><span class="sxs-lookup"><span data-stu-id="51fab-129">Test Lab Guides</span></span>

<span data-ttu-id="51fab-130">Per creare un ambiente di sviluppo/test per questa soluzione, utilizzare le guide di lab di test seguenti:  </span><span class="sxs-lookup"><span data-stu-id="51fab-130">To create a dev/test environment for this solution, use the following test lab guides:</span></span> 
  
- [<span data-ttu-id="51fab-131">Configurare i gruppi e gli utenti per un ambiente di sviluppo e di testing campagne politici</span><span class="sxs-lookup"><span data-stu-id="51fab-131">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
    
     <span data-ttu-id="51fab-132">Creare le sottoscrizioni di valutazione per Office 365 ed EMS e quindi creare gruppi e utenti per una campagna politico rappresentativa.</span><span class="sxs-lookup"><span data-stu-id="51fab-132">Create trial subscriptions for Office 365 and EMS and then create groups and users for a representative political campaign.</span></span>
    
- [<span data-ttu-id="51fab-133">Creare siti del team in un ambiente di sviluppo e di testing campagne politici</span><span class="sxs-lookup"><span data-stu-id="51fab-133">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
    
    <span data-ttu-id="51fab-134">Creare quattro siti del team di SharePoint Online con interno privato, riservati e altamente riservati livelli di protezione.</span><span class="sxs-lookup"><span data-stu-id="51fab-134">Create four SharePoint Online team sites with Internal, Private, Sensitive, and Highly Confidential levels of security.</span></span>
    
<span data-ttu-id="51fab-135">Per ulteriori funzionalità di protezione per la dimostrazione o modello di prova, vedere [Office 365 guide dei laboratori di testing](http://aka.ms/o365tlgs).</span><span class="sxs-lookup"><span data-stu-id="51fab-135">For additional security features for demonstration or proof of concept, see [Office 365 Test Lab Guides](http://aka.ms/o365tlgs).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="51fab-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="51fab-136">See Also</span></span>

[<span data-ttu-id="51fab-137">Soluzioni di sicurezza</span><span class="sxs-lookup"><span data-stu-id="51fab-137">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="51fab-138">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="51fab-138">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="51fab-139">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="51fab-139">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



