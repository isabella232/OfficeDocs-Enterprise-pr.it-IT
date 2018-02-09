---
title: Proteggere i siti del team di SharePoint Online per risorse estremamente riservate e sensibili
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8c088e88-a9ba-4044-bced-722196f4496d
description: "Sintesi: informazioni su come Contoso ha implementato siti del team di SharePoint Online estremamente riservati e sensibili per una collaborazione più facile, ma comunque sicura, per i dirigenti e i rispettivi centri di ricerca."
ms.openlocfilehash: c615280d39117f68515fb13d4ba83428d73e4fd3
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="secure-sharepoint-online-team-sites-for-sensitive-and-highly-confidential-assets"></a><span data-ttu-id="a0739-103">Proteggere i siti del team di SharePoint Online per risorse estremamente riservate e sensibili</span><span class="sxs-lookup"><span data-stu-id="a0739-103">Secure SharePoint Online team sites for sensitive and highly confidential assets</span></span>

 <span data-ttu-id="a0739-104">**Sintesi:** informazioni su come Contoso ha implementato siti del team di SharePoint Online estremamente riservati e sensibili per una collaborazione più facile, ma comunque sicura, per i dirigenti e i rispettivi centri di ricerca.</span><span class="sxs-lookup"><span data-stu-id="a0739-104">**Summary:** How Contoso implemented sensitive protection and highly confidential SharePoint Online team sites for easier, yet secure, collaboration for executives and its research centers.</span></span>
  
<span data-ttu-id="a0739-p101">La direzione esecutiva di Contoso desidera utilizzare Office 365 e archiviare i propri file in un unico posto per la collaborazione, indipendentemente dalla posizione di un dirigente. Analogamente, i reparti di ricerca di Contoso (con divisioni a Parigi, Mosca, New York, Pechino e Bangalore) desiderano spostare le proprie risorse digitali locali nel cloud per un accesso più semplice e una collaborazione migliore tra i team.</span><span class="sxs-lookup"><span data-stu-id="a0739-p101">The executive leadership of Contoso want to use Office 365 and store their files in a single location for collaboration, regardless of where an executive might be. Similarly, Contoso's research departments—with divisions in Paris, Moscow, New York, Beijing, and Bangalore—would like to transition their on-premises digital assets to the cloud for easier access and more open collaboration across teams.</span></span>
  
<span data-ttu-id="a0739-p102">Tuttavia, in entrambi i casi, l'accesso a tali risorse deve essere limitato al subset di persone autorizzate a visualizzarle o modificarle, con autorizzazioni valide per il sito gestito dallo staff IT. Inoltre, anche se alcune risorse sono distribuite intenzionalmente o meno, devono essere crittografate e dotate di autorizzazioni per evitare che gli utenti senza autorizzazioni possano visualizzare o modificare il loro contenuto.</span><span class="sxs-lookup"><span data-stu-id="a0739-p102">However, in both of these cases, access to these resources must be restricted to the subset of people who are allowed to view or change them, with ongoing permissions for the site administered by IT staff. Additionally, even if some resources are intentionally or unintentionally distributed, they must be encrypted and have permissions to prevent those who do not have access to view or change their contents.</span></span>
  
<span data-ttu-id="a0739-109">Gli amministratori della sicurezza e di SharePoint nel reparto IT di Contoso hanno deciso di utilizzare i siti del team di SharePoint Online estremamente riservati e sensibili, come mostrato nella figura 1.</span><span class="sxs-lookup"><span data-stu-id="a0739-109">Security and SharePoint administrators in Contoso's IT department decided to use sensitive protection and highly-confidential SharePoint Online team sites, as shown in Figure 1.</span></span>
  
<span data-ttu-id="a0739-110">**Figura 1: Confronto tra siti del team di SharePoint Online estremamente riservati e sensibili**</span><span class="sxs-lookup"><span data-stu-id="a0739-110">**Figure 1: Comparison of sensitive protection and highly confidential SharePoint Online team sites**</span></span>

![Siti del team di SharePoint Online estremamente riservati e sensibili](images/Contoso_Poster/SP_Solution.png)
  
<span data-ttu-id="a0739-112">Contoso ha utilizzato questa procedura per creare siti del team di SharePoint Online sicuri per i dirigenti e i team di ricerca:</span><span class="sxs-lookup"><span data-stu-id="a0739-112">Contoso used these steps to create secure SharePoint Online team sites for their executives and research teams:</span></span>
  
1. <span data-ttu-id="a0739-113">Creare un sito del team di SharePoint Online riservato **Dirigenti**</span><span class="sxs-lookup"><span data-stu-id="a0739-113">Create an **Executives** sensitive SharePoint Online team site</span></span>
    
    <span data-ttu-id="a0739-114">Il nuovo sito del team utilizza i gruppi di Azure Active Directory (AD) esistenti per i dirigenti come membri con il livello di autorizzazione Modifica di SharePoint e un piccolo set di account Administrator di SharePoint come proprietari con il livello di autorizzazione Controllo completo.</span><span class="sxs-lookup"><span data-stu-id="a0739-114">The new team site uses existing Azure Active Directory (AD) groups for executives as members with the Edit SharePoint permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level.</span></span>
    
2. <span data-ttu-id="a0739-115">Eseguire la migrazione di file dei dirigenti</span><span class="sxs-lookup"><span data-stu-id="a0739-115">Migrate executives files</span></span>
    
    <span data-ttu-id="a0739-116">Spostare i file e le cartelle dei dirigenti locali esistenti nel nuovo sito del team Dirigenti di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="a0739-116">Move existing on-premises executive files and folders to the new Executives SharePoint Online team site.</span></span>
    
3. <span data-ttu-id="a0739-117">Creare un sito del team di SharePoint Online estremamente riservato **Ricerca**</span><span class="sxs-lookup"><span data-stu-id="a0739-117">Create a **Research** highly confidential SharePoint Online team site</span></span>
    
    <span data-ttu-id="a0739-p103">Il nuovo sito del team utilizza i gruppi di team di ricerca Azure AD esistenti come membri con il livello di autorizzazione Modifica e un piccolo set di account Administrator di SharePoint come proprietari con il livello di autorizzazione Controllo completo. Un'etichetta AIP assegnata ai file di ricerca garantisce che questi siano crittografati e solo i membri di un gruppo di ricerca possono aprirli.</span><span class="sxs-lookup"><span data-stu-id="a0739-p103">The new team site uses existing Azure AD research team groups as members with the Edit permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level. An AIP label assigned to research files ensures that they are encrypted and only members of a research group can open them.</span></span>
    
4. <span data-ttu-id="a0739-120">Eseguire la migrazione di file di ricerca</span><span class="sxs-lookup"><span data-stu-id="a0739-120">Migrate research files</span></span>
    
    <span data-ttu-id="a0739-121">Spostare i file e le cartelle locali del team di ricerca esistenti nel nuovo sito del team Ricerca di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="a0739-121">Move existing research team on-premises files and folders to the new Research SharePoint Online team site.</span></span>
    
<span data-ttu-id="a0739-p104">Si ottengono due siti di collaborazione il cui accesso è rigidamente controllato dagli amministratori della sicurezza e di SharePoint. I file con l'etichetta Riservatezza elevata, anche se sono distribuiti all'esterno del sito del team Ricerca, sono crittografati e possono essere aperti solo da un membro di un team di ricerca.</span><span class="sxs-lookup"><span data-stu-id="a0739-p104">The result is two collaboration sites whose access is tightly controlled by security and SharePoint administrators. For files with the Highly Confidential AIP label, even if they are distributed outside the Research team site, they are encrypted and can only be opened by a member of a research team.</span></span>
  
<span data-ttu-id="a0739-124">Per ulteriori informazioni, vedere [Proteggere siti e file di SharePoint Online](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files).</span><span class="sxs-lookup"><span data-stu-id="a0739-124">For more information, see [Secure SharePoint Online sites and files](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files).</span></span>
  
 <span data-ttu-id="a0739-125">Per configurarli per una dimostrazione, un modello di verifica o sviluppo/test, vedere [Proteggere i siti di SharePoint Online in un ambiente di sviluppo/test](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test).</span><span class="sxs-lookup"><span data-stu-id="a0739-125">To set this up for demonstration, proof-of-concept, or dev/test, see [Secure SharePoint Online sites in a dev/test environment](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a0739-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a0739-126">See Also</span></span>

[<span data-ttu-id="a0739-127">Scenari aziendali per Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="a0739-127">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="a0739-128">Contoso nel Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="a0739-128">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="a0739-129">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="a0739-129">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="a0739-130">Stretch Database</span><span class="sxs-lookup"><span data-stu-id="a0739-130">Stretch Database</span></span>](https://msdn.microsoft.com/library/dn935011.aspx)
  
[<span data-ttu-id="a0739-131">Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT</span><span class="sxs-lookup"><span data-stu-id="a0739-131">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




