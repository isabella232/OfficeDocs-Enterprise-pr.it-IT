---
title: Preparare l'implementazione di OneDrive for Business Multi-Geo
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
description: Informazioni su OneDrive for Business Multi-Geo, come funziona il tenant multi-geografico e quali posizioni geografiche sono disponibili per l'archiviazione dei dati.
ms.openlocfilehash: d40f84ea3636b4eca2711a48bd9d70c73a242cfd
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849862"
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="ec4ba-103">Preparare l'implementazione di OneDrive for Business Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="ec4ba-103">Plan for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="ec4ba-104">Questa guida è utile agli amministratori di società multinazionali che stanno preparando l'espansione del tenant di SharePoint Online in altre aree geografiche in conformità con la presenza dell'azienda per soddisfare i requisiti di residenza dei dati.</span><span class="sxs-lookup"><span data-stu-id="ec4ba-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="ec4ba-p101">Nella configurazione OneDrive Multi-Geo, Office 365 è costituito da una posizione centralizzata e una o più posizioni geografiche satellite. Si tratta di un singolo tenant che comprende diverse posizioni geografiche. In OneDrive Multi-Geo, le informazioni del tenant, incluse le posizioni geografiche, vengono gestite in Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="ec4ba-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="ec4ba-108">Ecco un glossario dei termini principali per facilitare la comprensione della configurazione multi-geografica:</span><span class="sxs-lookup"><span data-stu-id="ec4ba-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="ec4ba-109">**Tenant**: rappresentazione di un'organizzazione nel cloud di Office 365 che in genere contiene uno o più domini associati (ad esempio http://contoso.sharepoint.com).</span><span class="sxs-lookup"><span data-stu-id="ec4ba-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="ec4ba-110">**Posizioni geografiche**: le posizioni geografiche disponibili per ospitare i dati in un tenant di Office 365.</span><span class="sxs-lookup"><span data-stu-id="ec4ba-110">**Geo locations** – The geographic locations available to host data in an Office 365 tenant.</span></span>

-   <span data-ttu-id="ec4ba-p102">**Posizioni satellite**: le posizioni geografiche configurate per ospitare i dati nel tenant di Office 365. I tenant multi-geografici coprono più di una posizione geografica, ad esempio Nord America ed Europa.</span><span class="sxs-lookup"><span data-stu-id="ec4ba-p102">**Satellite locations** – The geo locations that you have configured to host data in your Office 365 tenant. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="ec4ba-p103">**Posizione dati preferita (PDL)**: la posizione geografica in cui sono archiviati i dati di OneDrive di un singolo utente. Questa funzione può essere impostata dall'amministratore a una delle posizioni dati consentite configurate per il tenant. Se si cambia la PDL di un utente che ha già un sito di OneDrive, i dati di OneDrive non vengono spostati automaticamente nella nuova posizione geografica. Per ulteriori informazioni vedere [Spostare un sito di OneDrive in un'altra posizione geografica](move-onedrive-between-geo-locations.md).</span><span class="sxs-lookup"><span data-stu-id="ec4ba-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="ec4ba-117">Per abilitare Multi-Geo sono necessarie quattro attività:</span><span class="sxs-lookup"><span data-stu-id="ec4ba-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="ec4ba-118">Collaborare con il team responsabile dell'account per aggiungere il piano servizi _Multi-Geo Capabilities in Office 365 _.</span><span class="sxs-lookup"><span data-stu-id="ec4ba-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="ec4ba-119">Scegliere le posizioni satellite desiderate e aggiungerle al tenant.</span><span class="sxs-lookup"><span data-stu-id="ec4ba-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="ec4ba-p104">Impostare la posizione dati preferita dell'utente nella posizione satellite desiderata. Quando viene eseguito il provisioning di un nuovo sito di OneDrive per un utente, viene eseguito il provisioning sulla relativa PDL.</span><span class="sxs-lookup"><span data-stu-id="ec4ba-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="ec4ba-122">Eseguire la migrazione dei siti di OneDrive esistenti dalla posizione centrale alla posizione dati preferita in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="ec4ba-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="ec4ba-123">Vedere [Configurare OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) per informazioni dettagliate su ognuno di questi passaggi.</span><span class="sxs-lookup"><span data-stu-id="ec4ba-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec4ba-p105">Office 365 Multi-Geo non è progettato per i casi di ottimizzazione delle prestazioni, ma per soddisfare i requisiti di residenza dei dati. Per informazioni sull'ottimizzazione delle prestazioni per Office 365, vedere [Pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) o contattare il servizio di supporto tecnico.</span><span class="sxs-lookup"><span data-stu-id="ec4ba-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="ec4ba-p106">È possibile configurare una delle posizioni seguenti come posizione satellite in cui ospitare i file di OneDrive. Nella pianificazione multi-geografica, è opportuno creare un elenco delle posizioni che si desidera aggiungere al tenant di Office 365. È consigliabile iniziare con una o due posizioni satellite e poi aggiungere gradualmente altre posizioni geografiche, se necessario.</span><span class="sxs-lookup"><span data-stu-id="ec4ba-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ec4ba-129"><strong>Posizione</strong></span><span class="sxs-lookup"><span data-stu-id="ec4ba-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="ec4ba-130"><strong>Codice</strong></span><span class="sxs-lookup"><span data-stu-id="ec4ba-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="ec4ba-131">Asia-Pacifico</span><span class="sxs-lookup"><span data-stu-id="ec4ba-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="ec4ba-132">APC</span><span class="sxs-lookup"><span data-stu-id="ec4ba-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ec4ba-133">Australia</span><span class="sxs-lookup"><span data-stu-id="ec4ba-133">Australia</span></span></td>
<td align="left"><span data-ttu-id="ec4ba-134">AUS</span><span class="sxs-lookup"><span data-stu-id="ec4ba-134">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ec4ba-135">Canada</span><span class="sxs-lookup"><span data-stu-id="ec4ba-135">Canada</span></span></td>
<td align="left"><span data-ttu-id="ec4ba-136">CAN</span><span class="sxs-lookup"><span data-stu-id="ec4ba-136">CAN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ec4ba-137">Europa/Medio Oriente/Africa</span><span class="sxs-lookup"><span data-stu-id="ec4ba-137">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="ec4ba-138">EUR</span><span class="sxs-lookup"><span data-stu-id="ec4ba-138">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ec4ba-139">Francia</span><span class="sxs-lookup"><span data-stu-id="ec4ba-139">France</span></span></td>
<td align="left"><span data-ttu-id="ec4ba-140">FRA</span><span class="sxs-lookup"><span data-stu-id="ec4ba-140">FRA</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ec4ba-141">Giappone</span><span class="sxs-lookup"><span data-stu-id="ec4ba-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="ec4ba-142">JPN</span><span class="sxs-lookup"><span data-stu-id="ec4ba-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ec4ba-143">Corea</span><span class="sxs-lookup"><span data-stu-id="ec4ba-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="ec4ba-144">KOR</span><span class="sxs-lookup"><span data-stu-id="ec4ba-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ec4ba-145">Nord America</span><span class="sxs-lookup"><span data-stu-id="ec4ba-145">North America</span></span></td>
<td align="left"><span data-ttu-id="ec4ba-146">NAM</span><span class="sxs-lookup"><span data-stu-id="ec4ba-146">NAM</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ec4ba-147">Regno Unito</span><span class="sxs-lookup"><span data-stu-id="ec4ba-147">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="ec4ba-148">GBR</span><span class="sxs-lookup"><span data-stu-id="ec4ba-148">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="ec4ba-149">Prossime posizioni geografiche:</span><span class="sxs-lookup"><span data-stu-id="ec4ba-149">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="ec4ba-150">India</span><span class="sxs-lookup"><span data-stu-id="ec4ba-150">India</span></span>

<span data-ttu-id="ec4ba-p107">Quando si configura un tenant multi-geografico, valutare l'opportunità di consolidare l'infrastruttura locale durante la migrazione a Office 365. Ad esempio, se si dispone di farm locali a Singapore e in Malesia, è possibile consolidarle nella posizione satellite APC, a condizione che i requisiti di residenza dei dati consentano di farlo.</span><span class="sxs-lookup"><span data-stu-id="ec4ba-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="ec4ba-153">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="ec4ba-153">Best practices</span></span>

<span data-ttu-id="ec4ba-p108">È consigliabile creare un utente test in Office 365 per eseguire alcuni test iniziali. Verranno eseguiti alcuni passaggi di verifica con questo utente prima di procedere di caricare utenti della produzione in OneDrive Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="ec4ba-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="ec4ba-p109">Dopo aver completato la verifica con l'utente test, selezionare un gruppo pilota, magari dal proprio reparto IT, per utilizzare OneDrive in una nuova posizione geografica per la prima volta. Per questo primo gruppo, selezionare gli utenti che non hanno ancora OneDrive. È consigliabile inserire non più di cinque persone in questo gruppo iniziale e aumentare gradualmente il numero, seguendo un approccio di implementazione a fasi.</span><span class="sxs-lookup"><span data-stu-id="ec4ba-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="ec4ba-p110">Ogni utente deve avere una *posizione dati preferita* (PDL) impostata in modo che Office 365 possa determinare in quale posizione geografica effettuare il provisioning di OneDrive. La posizione dati preferita dell'utente deve corrispondere alla località satellite selezionata o alla posizione centrale. Il campo PDL non è obbligatorio ma è consigliabile impostare una PDL per tutti gli utenti. Verrà eseguito il provisioning in posizione centrale dei carichi di lavoro di un utente senza una PDL.</span><span class="sxs-lookup"><span data-stu-id="ec4ba-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="ec4ba-p111">Creare un elenco degli utenti e includere il nome dell'entità utente (UPN) e il codice di posizione per la posizione dati preferita appropriata. Includere l'utente test e il gruppo pilota iniziale per cominciare. Tale elenco è necessario per le procedure di configurazione.</span><span class="sxs-lookup"><span data-stu-id="ec4ba-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="ec4ba-p112">Se gli utenti vengono sincronizzati da un sistema di Active Directory locale per Azure Active Directory, è necessario impostare la posizione dati preferita per gli utenti sincronizzati tramite la connessione di Azure Active Directory. È possibile configurare direttamente la posizione dati preferita per gli utenti sincronizzati con Azure Active Directory PowerShell. I passaggi per configurare la PDL in AD e sincronizzarla sono trattati in [Sincronizzazione di Azure Active Directory Connect: configurare la posizione dati preferita per le risorse di Office 365](https://docs.microsoft.com/it-IT/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="ec4ba-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/it-IT/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="ec4ba-p113">L'amministrazione di un tenant multi-geografico può essere diverso da un tenant non multi-geografico, dal momento che la maggior parte delle impostazioni SharePoint e OneDrive e i servizi hanno funzionalità multi-geo. È consigliabile consultare [Amministrazione di un ambiente multi-geografico](administering-a-multi-geo-environment.md) prima di procedere con la configurazione.</span><span class="sxs-lookup"><span data-stu-id="ec4ba-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="ec4ba-171">Leggere [Esperienza utente in un ambiente multi-geografico](multi-geo-user-experience.md) per i dettagli riguardanti l'esperienza degli utenti finali in un ambiente multi-geografico.</span><span class="sxs-lookup"><span data-stu-id="ec4ba-171">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="ec4ba-172">Per iniziare a configurare OneDrive for Business Multi-Geo, vedere [Configurare OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="ec4ba-172">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="ec4ba-173">Dopo aver completato la configurazione, è necessario [eseguire la migrazione delle raccolte OneDrive dell'utente](move-onedrive-between-geo-locations.md) per consentire agli utenti di lavorare dalla propria posizione dati preferita.</span><span class="sxs-lookup"><span data-stu-id="ec4ba-173">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
