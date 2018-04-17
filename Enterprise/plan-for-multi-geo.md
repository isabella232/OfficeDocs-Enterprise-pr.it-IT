---
title: Plan for OneDrive for Business Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Informazioni su OneDrive per Business Multi-livello geografico, funzionamento multi-geo e le posizioni geo sono disponibili per l'archiviazione dei dati.
ms.openlocfilehash: d7d6cfbbff4cf0ec2516f2506946c2832d96b3f2
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="890ec-103">Plan for OneDrive for Business Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="890ec-103">Plan for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="890ec-104">Questa guida è destinata agli amministratori di società multinazionale (MNCs) responsabili di preparare i tenant di SharePoint Online per essere ingrandita a ulteriori aree geografiche in conformità con presenza dell'azienda per soddisfare i requisiti di residenza dati.</span><span class="sxs-lookup"><span data-stu-id="890ec-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="890ec-p101">In una configurazione Multi-Geo OneDrive tenant Office 365 è costituita da una posizione centralizzata (noto anche come il percorso predefinito) e uno o più percorsi geo satellitari. Si tratta di un singolo tenant che si estende su più località geografica. OneDrive Multi-Geo, le informazioni di tenant, inclusi i percorsi geografica, sia gestite in Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="890ec-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="890ec-108">Ecco alcuni termini chiave multi-geo utili per comprendere i concetti di base della configurazione:</span><span class="sxs-lookup"><span data-stu-id="890ec-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="890ec-109">**Tenant** – rappresentazione dell'organizzazione nel cloud che in genere presenta uno o più domini che Office 365 (ad esempio http://contoso.sharepoint.com).</span><span class="sxs-lookup"><span data-stu-id="890ec-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="890ec-p102">**Percorsi Geo** da posizioni geografiche ospitati dati del tenant. Multi-geo tenant estendersi su più di una posizione geografica, ad esempio Nord America ed Europa.</span><span class="sxs-lookup"><span data-stu-id="890ec-p102">**Geo locations** – The geographic locations where your tenant’s data is hosted. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="890ec-112">**Percorsi di dati consentito (ADL)** – i percorsi geo per cui è stato configurato il tenant per ospitare dati OneDrive e SharePoint.</span><span class="sxs-lookup"><span data-stu-id="890ec-112">**Allowed Data Locations (ADL)** – The geo locations for which your tenant has been configured to host OneDrive and SharePoint data.</span></span>

-   <span data-ttu-id="890ec-p103">**Percorso preferito di dati (PDL)** – località geografica cui sono archiviati i dati di OneDrive un singolo utente. Può essere impostato dall'amministratore per uno dei percorsi dati consentiti che sono stati configurati per il tenant. Si noti che se si modifica il PDL per un utente che dispone già di un sito di OneDrive, i dati di OneDrive non viene spostati nella nuova posizione geografica automaticamente. Per ulteriori informazioni, vedere [spostare una raccolta di OneDrive in un'altra posizione geografica](move-onedrive-between-geo-locations.md) .</span><span class="sxs-lookup"><span data-stu-id="890ec-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="890ec-117">Abilitazione della Multi-Geo richiede quattro passaggi principali:</span><span class="sxs-lookup"><span data-stu-id="890ec-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="890ec-118">Collaborare con il team amministrativo per aggiungere il piano di servizio _Multi-Geo disponibili in Office 365_ .</span><span class="sxs-lookup"><span data-stu-id="890ec-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="890ec-119">Scegliere il desiderata satellitare posizione geografica e aggiungerli al tenant.</span><span class="sxs-lookup"><span data-stu-id="890ec-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="890ec-p104">Impostare percorso dati preferito degli utenti alla posizione geografica satellitari desiderato. Quando viene eseguito il provisioning di un nuovo sito di OneDrive per un utente, viene effettuato il provisioning di loro PDL.</span><span class="sxs-lookup"><span data-stu-id="890ec-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="890ec-122">Eseguire la migrazione siti OneDrive esistenti degli utenti dal percorso principale relativo percorso dati preferita in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="890ec-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="890ec-123">Per informazioni dettagliate su ciascuno di questi passaggi, vedere [Configurare OneDrive per Business Multi-Geo](multi-geo-tenant-configuration.md) .</span><span class="sxs-lookup"><span data-stu-id="890ec-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="890ec-p105">Si noti che le funzionalità Multi-Geo di Office 365 non progettate per i casi di ottimizzazione delle prestazioni, sono stati progettati per soddisfare i requisiti di residenza dati. Per informazioni sull'ottimizzazione delle prestazioni per Office 365, vedere [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) o contattare il supporto.</span><span class="sxs-lookup"><span data-stu-id="890ec-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="890ec-p106">È possibile configurare una delle seguenti posizioni da località geografica in cui ospitare i file di OneDrive. Durante la pianificazione per la multi-geo, creare un elenco dei percorsi che si desidera aggiungere al tenant di Office 365. È consigliabile a partire da uno o due percorsi satellitari e quindi gradualmente l'espansione in più posizioni geo, se necessario.</span><span class="sxs-lookup"><span data-stu-id="890ec-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="890ec-129"><strong>Percorso</strong></span><span class="sxs-lookup"><span data-stu-id="890ec-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="890ec-130"><strong>Codice</strong></span><span class="sxs-lookup"><span data-stu-id="890ec-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="890ec-131">Asia-Pacifico</span><span class="sxs-lookup"><span data-stu-id="890ec-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="890ec-132">APC</span><span class="sxs-lookup"><span data-stu-id="890ec-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="890ec-133">Europa / Allinea al centro est / Africa</span><span class="sxs-lookup"><span data-stu-id="890ec-133">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="890ec-134">EUR</span><span class="sxs-lookup"><span data-stu-id="890ec-134">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="890ec-135">Nord America</span><span class="sxs-lookup"><span data-stu-id="890ec-135">North America</span></span></td>
<td align="left"><span data-ttu-id="890ec-136">NOME</span><span class="sxs-lookup"><span data-stu-id="890ec-136">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="890ec-137">Australia</span><span class="sxs-lookup"><span data-stu-id="890ec-137">Australia</span></span></td>
<td align="left"><span data-ttu-id="890ec-138">AUSTRALIA</span><span class="sxs-lookup"><span data-stu-id="890ec-138">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="890ec-139">Canada</span><span class="sxs-lookup"><span data-stu-id="890ec-139">Canada</span></span></td>
<td align="left"><span data-ttu-id="890ec-140">POSSIBILE</span><span class="sxs-lookup"><span data-stu-id="890ec-140">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="890ec-141">Giappone</span><span class="sxs-lookup"><span data-stu-id="890ec-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="890ec-142">GIAPPONESE</span><span class="sxs-lookup"><span data-stu-id="890ec-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="890ec-143">Corea</span><span class="sxs-lookup"><span data-stu-id="890ec-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="890ec-144">(COREANO)</span><span class="sxs-lookup"><span data-stu-id="890ec-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="890ec-145">Regno Unito</span><span class="sxs-lookup"><span data-stu-id="890ec-145">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="890ec-146">GBR</span><span class="sxs-lookup"><span data-stu-id="890ec-146">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="890ec-147">Prossime località geografiche:</span><span class="sxs-lookup"><span data-stu-id="890ec-147">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="890ec-148">Francia</span><span class="sxs-lookup"><span data-stu-id="890ec-148">France</span></span>
- <span data-ttu-id="890ec-149">India</span><span class="sxs-lookup"><span data-stu-id="890ec-149">India</span></span>

<span data-ttu-id="890ec-p107">Quando si configura multi-geo, prendere in considerazione avere l'opportunità di consolidamento dell'infrastruttura locale durante la migrazione a Office 365. Ad esempio, se si dispone di farm locale in Singapore e Malaysia, quindi è possibile consolidare loro posizione satellitare APC, requisiti di residenza dati consentono di eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="890ec-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="890ec-152">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="890ec-152">Best practices</span></span>

<span data-ttu-id="890ec-p108">È consigliabile creare un utente di test in Office 365 per eseguire alcuni test iniziale. Verrà esaminato alcuni passaggi di testing e la verifica con l'utente prima di procedere con gli utenti di produzione incorporato nella funzionalità Multi-Geo OneDrive.</span><span class="sxs-lookup"><span data-stu-id="890ec-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="890ec-p109">Dopo aver completato il test con l'utente di test, selezionare un gruppo pilota – forse il reparto IT: la prima di utilizzare OneDrive in una nuova posizione geografica. Per il primo gruppo, selezionare gli utenti che non hanno ancora un OneDrive. È consigliabile non più di cinque utenti nel gruppo iniziale e gradualmente espandere dopo un approccio di implementazione in batch.</span><span class="sxs-lookup"><span data-stu-id="890ec-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="890ec-p110">Ogni utente deve avere un *percorso dati preferito* (PDL) impostato in modo che Office 365 può determinare in quale posizione geografica per fornire loro OneDrive. Percorso dei dati Preferiti dell'utente deve corrispondere a uno dei percorsi di satellitari scelti o la posizione centrale. Mentre il campo PDL non è obbligatorio, è consigliabile che un PDL da impostare per tutti gli utenti. Eseguire il provisioning dei carichi di lavoro di un utente senza un PDL nella posizione centrale in base alla Multi-Geo logica.</span><span class="sxs-lookup"><span data-stu-id="890ec-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="890ec-p111">Creare un elenco degli utenti e includere il nome dell'entità utente (UPN) e il codice di posizione per il percorso dati preferito appropriato. Includere per iniziare con l'utente di test e il gruppo pilota iniziale. In questo elenco sono necessari per le procedure di configurazione.</span><span class="sxs-lookup"><span data-stu-id="890ec-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="890ec-p112">Se gli utenti vengono sincronizzati da un sistema di Active Directory (AD) locale per Azure Active Directory (AAD), è necessario impostare il percorso dati preferito per gli utenti sincronizzati tramite la connessione di Azure Active Directory. È possibile configurare direttamente il percorso dati preferito per gli utenti sincronizzati con Azure Active Directory PowerShell. I passaggi per configurare PDL in Active Directory e sincronizzarlo sono trattati nei [connettersi Azure Active Directory sync: configurare la posizione dei dati preferito per le risorse di Office 365](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="890ec-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="890ec-p113">L'amministrazione di un tenant multi-geo può essere diverso da un tenant di livello geografico multi, la maggior parte delle impostazioni SharePoint e OneDrive e i servizi sono multi-geo. È consigliabile consultare [amministrazione di un ambiente multi-geo](administering-a-multi-geo-environment.md) prima di procedere con la configurazione.</span><span class="sxs-lookup"><span data-stu-id="890ec-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="890ec-170">Per informazioni dettagliate sull'esperienza degli utenti finali in un ambiente multi-geo, leggere [l'esperienza utente in un ambiente multgeo](multi-geo-user-experience.md) .</span><span class="sxs-lookup"><span data-stu-id="890ec-170">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="890ec-171">Per iniziare a configurare OneDrive per Business Multi-Geo, vedere [Configurare OneDrive per Business Multi-Geo](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="890ec-171">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="890ec-172">Dopo aver completato la configurazione, ricordarsi di [eseguire la migrazione di raccolte di OneDrive degli utenti](move-onedrive-between-geo-locations.md) in base alle esigenze per ottenere gli utenti lavorano dai percorsi dei dati preferito.</span><span class="sxs-lookup"><span data-stu-id="890ec-172">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
