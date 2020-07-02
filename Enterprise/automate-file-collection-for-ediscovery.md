---
title: Automatizzare la raccolta file per eDiscovery
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 'Riepilogo: informazioni su come automatizzare la raccolta di file dai computer degli utenti per eDiscovery.'
ms.openlocfilehash: 83bd55ff786803cfcb3eec9430d72de30179d000
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997977"
---
# <a name="automate-file-collection-for-ediscovery"></a><span data-ttu-id="6ab4a-103">Automatizzare la raccolta file per eDiscovery</span><span class="sxs-lookup"><span data-stu-id="6ab4a-103">Automate file collection for eDiscovery</span></span>

<span data-ttu-id="6ab4a-104">Tutte le aziende affrontano le potenzialità di azioni legali o di altro tipo.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-104">All companies face the potential of lawsuits or other types of legal action.</span></span> <span data-ttu-id="6ab4a-105">Mentre i reparti legali lavorano per ridurre tale esposizione, la controversia legale è una realtà aziendale.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-105">While legal departments work to reduce that exposure, litigation is a fact of business life.</span></span> <span data-ttu-id="6ab4a-106">Quando una società affronta un'azione legale, è necessario, tramite il processo di individuazione legale, fornire tutti i materiali documentario rilevanti alla Corte e opporsi ai consulenti legali.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-106">When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span></span> 
  
<span data-ttu-id="6ab4a-107">eDiscovery è il processo in base al quale le aziende inventario, ricerca, identificare, preservare, filtrare e rendere disponibili i materiali documentario rilevanti che esistono in formato elettronico.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-107">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form.</span></span> <span data-ttu-id="6ab4a-108">SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online ed Exchange Online possono contenere grandi quantità di contenuto documentario.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-108">SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content.</span></span> <span data-ttu-id="6ab4a-109">A seconda della versione, questi prodotti possono supportare eDiscovery e sul posto (Lync tramite Exchange Server), rendendo più semplice per i team legali indicizzare, identificare, conservare e filtrare i contenuti più rilevanti per un determinato caso.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-109">Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span></span>
  
<span data-ttu-id="6ab4a-110">Molti documenti vengono archiviati nei computer locali degli utenti (depositari), non in una posizione centralizzata.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-110">Many documents are stored on users' (Custodians) local computers, not in a centralized location.</span></span> <span data-ttu-id="6ab4a-111">Ciò rende sostanzialmente impossibile per SharePoint 2013 per la ricerca e, se non è possibile eseguire una ricerca, non può essere incluso in eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-111">This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery.</span></span> <span data-ttu-id="6ab4a-112">Questa soluzione illustra come utilizzare gli script di accesso, l'orchestratore di sistema System Center 2012 R2 e Windows PowerShell per Exchange Server per automatizzare l'identificazione e la raccolta dei materiali documentari dai computer degli utenti.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-112">This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span></span>
  
## <a name="what-this-solution-does"></a><span data-ttu-id="6ab4a-113">Cosa fa questa soluzione</span><span class="sxs-lookup"><span data-stu-id="6ab4a-113">What this solution does</span></span>

<span data-ttu-id="6ab4a-114">Questa soluzione utilizza un gruppo di sicurezza globale, criteri di gruppo e uno script di Windows PowerShell per individuare, inventariare e raccogliere contenuto e file PST (Outlook Personal Store) dagli utenti dei computer locali a una condivisione di file nascosta.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-114">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share.</span></span> <span data-ttu-id="6ab4a-115">Da qui, i file PST possono essere importati in Exchange Server 2013 o Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-115">From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online.</span></span> <span data-ttu-id="6ab4a-116">Tutti i file vengono quindi spostati utilizzando un orchestratore di System Center 2012 R2 Runbook in un'altra condivisione file in Microsoft Azure per l'archiviazione a lungo termine e l'indicizzazione da parte di SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-116">All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013.</span></span> <span data-ttu-id="6ab4a-117">È quindi possibile utilizzare i centri di eDiscovery nella distribuzione di SharePoint 2013 locale o in SharePoint Online come si farebbe regolarmente per eseguire eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-117">You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="6ab4a-118">Questa soluzione utilizza Robocopy per copiare i file dai computer di custode in una condivisione file centralizzata.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-118">This solution uses robocopy to copy files from custodian's computers to a centralized file share.</span></span> <span data-ttu-id="6ab4a-119">Poiché Robocopy non copia i file aperti o bloccati, tutti i file, inclusi i file PST, che il custode ha aperto non verranno raccolti.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-119">Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected.</span></span> <span data-ttu-id="6ab4a-120">Sarà necessario raccoglierli manualmente.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-120">You will have to collect them manually.</span></span> <span data-ttu-id="6ab4a-121">Questa soluzione fornisce un elenco che identifica in modo esplicito i file che non è in grado di copiare e il percorso completo di ogni file.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-121">This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span></span> 
  
<span data-ttu-id="6ab4a-122">Nel diagramma seguente vengono illustrati tutti i passaggi e gli elementi della soluzione.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-122">The following diagram walks you through all the steps and elements of the solution.</span></span>
  
![Panoramica della soluzione di raccolta di file automatizzata](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|<span data-ttu-id="6ab4a-124">Legenda \* \* \* \*</span><span class="sxs-lookup"><span data-stu-id="6ab4a-124">\*\*\*\*Legend\*\*\*\*</span></span>||
|:-----|:-----|
|![callout Magenta 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|<span data-ttu-id="6ab4a-126">Creare un oggetto Criteri di gruppo e associarlo allo script di accesso all'insieme.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-126">Create a Group Policy object (GPO), and associate it with the collection logon script.</span></span>  <br/> |
|![callout Magenta 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| <span data-ttu-id="6ab4a-128">Configurare il filtro di sicurezza per l'oggetto Criteri di gruppo per applicare solo il criterio di associazione ai gruppi depositari.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-128">Configure the GPO security filter to apply the GPO only to the Custodians group.</span></span> <br/> |
|![callout Magenta 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|<span data-ttu-id="6ab4a-130">Un custode accede e l'oggetto Criteri di gruppo viene eseguito, chiamando lo script di accesso all'insieme.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-130">A Custodian logs on and the GPO runs, calling the collection logon script.</span></span>  <br/> |
|![callout Magenta 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|<span data-ttu-id="6ab4a-132">Lo script di accesso all'insieme consente di inventariare tutte le unità collegate localmente nel computer dei depositari, cercando i file desiderati e registrando la propria posizione.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-132">The collection logon script inventories all locally attached drives on the Custodians computer, searching for the files you want, and recording their location.</span></span>  <br/> |
|![callout Magenta 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|<span data-ttu-id="6ab4a-134">Lo script di accesso all'insieme copia i file inventariati in una condivisione file nascosta nel server di gestione temporanea.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-134">The collection logon script copies the inventoried files to a hidden file share on the staging server.</span></span>  <br/> |
|![chiamata Magenta verso l'esterno 6](media/99589726-0c7e-406b-a276-44301a135768.png)| <span data-ttu-id="6ab4a-136">(Opzione A) Eseguire manualmente lo script di importazione PST per importare i file PST raccolti in Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-136">(Option A) Manually run the PST import script to import the collected PST files into Exchange Server 2013.</span></span> <br/> |
|![callout magenta 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|<span data-ttu-id="6ab4a-138">(Opzione B) Tramite lo strumento di importazione e l'elaborazione di Microsoft 365 importare i file PST raccolti in Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-138">(Option B) Using the Microsoft 365 Import tool and process, import the collected PST files into Exchange Online.</span></span>  <br/> |
|![callout Magenta 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|<span data-ttu-id="6ab4a-140">Spostare tutti i file raccolti in una condivisione di file di Azure per l'archiviazione a lungo termine con l'orchestratore di MoveToColdStorage System Center 2012 R2 Runbook.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-140">Move all collected files to an Azure file share for long term storage with the MoveToColdStorage System Center Orchestrator 2012 R2 runbook.</span></span> <br/> |
|![callout magenta 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|<span data-ttu-id="6ab4a-142">Indicizzare i file nella condivisione file di archiviazione frigorifera con SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-142">Index the files in the cold storage file share with SharePoint 2013.</span></span>  <br/> |
|![callout Magenta 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|<span data-ttu-id="6ab4a-144">Eseguire eDiscovery sul contenuto nell'archiviazione frigorifera e nel server Exchange locale 2013.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-144">Perform eDiscovery on content in cold storage and in the on-premises Exchange Server 2013.</span></span>  <br/> |
|![callout Magenta 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|<span data-ttu-id="6ab4a-146">Eseguire eDiscovery sul contenuto in Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-146">Perform eDiscovery on content in Microsoft 365.</span></span>  <br/> |
   
## <a name="prerequisites"></a><span data-ttu-id="6ab4a-147">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="6ab4a-147">Prerequisites</span></span>

<span data-ttu-id="6ab4a-148">La configurazione di questa soluzione richiede molti elementi, la maggior parte dei quali è probabile che sia sul posto e configurati se si pensa a eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-148">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery.</span></span> <span data-ttu-id="6ab4a-149">Per gli elementi che non possono essere presenti o che richiedono una configurazione specifica, verranno forniti i collegamenti necessari per creare la configurazione di base.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-149">For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration.</span></span> <span data-ttu-id="6ab4a-150">Prima di configurare la soluzione, è necessario disporre della configurazione di base.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-150">You must have the base configuration in place before you configure the solution itself.</span></span>
  
### <a name="base-configuration"></a><span data-ttu-id="6ab4a-151">Configurazione di base</span><span class="sxs-lookup"><span data-stu-id="6ab4a-151">Base configuration</span></span>

|<span data-ttu-id="6ab4a-152">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="6ab4a-152">**Element**</span></span>|<span data-ttu-id="6ab4a-153">**Collegamenti**</span><span class="sxs-lookup"><span data-stu-id="6ab4a-153">**Link**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6ab4a-154">Dominio di servizi di dominio Active Directory (AD DS)</span><span class="sxs-lookup"><span data-stu-id="6ab4a-154">Active Directory Domain Services (AD DS) domain</span></span>  <br/> ||
|<span data-ttu-id="6ab4a-155">Connettività Internet dalla rete locale</span><span class="sxs-lookup"><span data-stu-id="6ab4a-155">Internet connectivity from your on-premises network</span></span>  <br/> ||
|<span data-ttu-id="6ab4a-156">SQL Server 2012 per il supporto di SharePoint 2013 e dell'orchestratore di System Center 2012 R2</span><span class="sxs-lookup"><span data-stu-id="6ab4a-156">SQL Server 2012 to support SharePoint 2013 and System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="6ab4a-157">Distribuzione di orchestratore di System Center-2012</span><span class="sxs-lookup"><span data-stu-id="6ab4a-157">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| <span data-ttu-id="6ab4a-158">SharePoint 2013 locale o basato su Azure per eDiscovery (obbligatorio per l'opzione A)</span><span class="sxs-lookup"><span data-stu-id="6ab4a-158">On-premises or Azure based SharePoint 2013 for eDiscovery (required for Option A)</span></span> <br/> ||
|<span data-ttu-id="6ab4a-159">Server di condivisione file locale per la gestione temporanea</span><span class="sxs-lookup"><span data-stu-id="6ab4a-159">On-premises file share server for staging</span></span>  <br/> ||
|<span data-ttu-id="6ab4a-160">Exchange Server 2013 locale per l'opzione A PST Import</span><span class="sxs-lookup"><span data-stu-id="6ab4a-160">On-premises Exchange Server 2013 for Option A PST import</span></span>  <br/> |<span data-ttu-id="6ab4a-161">CU5 (15.913.22) è disponibile su [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span><span class="sxs-lookup"><span data-stu-id="6ab4a-161">CU5 (15.913.22) is available at [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span></span>  <br/> |
|<span data-ttu-id="6ab4a-162">System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="6ab4a-162">System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="6ab4a-163">Distribuzione di orchestratore di System Center-2012</span><span class="sxs-lookup"><span data-stu-id="6ab4a-163">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|<span data-ttu-id="6ab4a-164">Microsoft 365 E3 con Exchange Online e SharePoint Online (obbligatorio per l'opzione B)</span><span class="sxs-lookup"><span data-stu-id="6ab4a-164">Microsoft 365 E3 with Exchange Online and SharePoint Online (required for Option B)</span></span>  <br/> |<span data-ttu-id="6ab4a-165">Per iscriversi a un abbonamento a Microsoft 365 E3, vedere [sottoscrizione microsoft 365 E3](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab).</span><span class="sxs-lookup"><span data-stu-id="6ab4a-165">To sign up for a Microsoft 365 E3 subscription, see [Microsoft 365 E3 subscription](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab).</span></span>  <br/> |
|<span data-ttu-id="6ab4a-166">Sottoscrizione di Azure con una macchina virtuale</span><span class="sxs-lookup"><span data-stu-id="6ab4a-166">Azure subscription with a virtual machine</span></span>  <br/> |<span data-ttu-id="6ab4a-167">Per iscriversi a un Azure, vedere [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span><span class="sxs-lookup"><span data-stu-id="6ab4a-167">To sign up for a Azure, see [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span></span> <br/> |
|<span data-ttu-id="6ab4a-168">Una connessione VPN tra la rete locale e la sottoscrizione di Azure</span><span class="sxs-lookup"><span data-stu-id="6ab4a-168">A VPN connection between your on-premises network and your Azure subscription</span></span>  <br/> |<span data-ttu-id="6ab4a-169">Per impostare un tunnel VPN tra la sottoscrizione di Azure e la rete locale, vedere [connettere una rete locale a una rete virtuale di Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span><span class="sxs-lookup"><span data-stu-id="6ab4a-169">To set up a VPN tunnel between your Azure subscription and your on-premises network, see [Connect an on-premises network to a Microsoft Azure virtual network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span></span>  <br/> |
|<span data-ttu-id="6ab4a-170">SharePoint 2013 eDiscovery configurata per la ricerca in SharePoint e Exchange Server 2013 e, facoltativamente, Lync Server 2013</span><span class="sxs-lookup"><span data-stu-id="6ab4a-170">SharePoint 2013 eDiscovery configured to search across SharePoint and Exchange Server 2013 and optionally Lync Server 2013</span></span>  <br/> |<span data-ttu-id="6ab4a-171">Per configurare eDiscovery in questo modo, vedere [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows file Shares Lab test](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span><span class="sxs-lookup"><span data-stu-id="6ab4a-171">To configure eDiscovery in this fashion, see [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab Guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows File Shares Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span></span>  <br/> |
|<span data-ttu-id="6ab4a-172">eDiscovery in Microsoft 365 per SharePoint Online ed Exchange Online</span><span class="sxs-lookup"><span data-stu-id="6ab4a-172">eDiscovery in Microsoft 365 for SharePoint Online and Exchange Online</span></span>  <br/> |<span data-ttu-id="6ab4a-173">Per configurare eDiscovery in Microsoft 365, vedere Configurare [un centro eDiscovery in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span><span class="sxs-lookup"><span data-stu-id="6ab4a-173">To configure eDiscovery in Microsoft 365, see [Set up an eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span></span>  <br/> |
   
## <a name="configure-the-environment"></a><span data-ttu-id="6ab4a-174">Configurare l'ambiente</span><span class="sxs-lookup"><span data-stu-id="6ab4a-174">Configure the environment</span></span>

<span data-ttu-id="6ab4a-175">Dopo aver posizionato la configurazione di base, è possibile procedere alla configurazione della soluzione.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-175">Now that you have the base configuration in place, you can move ahead to configuring the solution itself.</span></span> 
  
### <a name="staging-file-share"></a><span data-ttu-id="6ab4a-176">Condivisione file di gestione temporanea</span><span class="sxs-lookup"><span data-stu-id="6ab4a-176">Staging file share</span></span>

1. <span data-ttu-id="6ab4a-177">Nel dominio locale, creare un gruppo di sicurezza globale denominato depositari.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-177">In the on-premises domain, create a global security group named Custodians.</span></span>
    
2. <span data-ttu-id="6ab4a-178">Creare una condivisione file nascosta per i file raccolti dai computer depositari.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-178">Create a hidden file share for the files that are collected from Custodians computers.</span></span> <span data-ttu-id="6ab4a-179">Deve trovarsi in un server locale.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-179">This should be on an on-premises server.</span></span> <span data-ttu-id="6ab4a-180">Ad esempio, in un server denominato staging, creare una condivisione file denominata Cases $.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-180">For example, on a server called Staging, create a file share called Cases$.</span></span> <span data-ttu-id="6ab4a-181">L' **$** è necessario per renderla una condivisione nascosta.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-181">The **$** is required to make this a hidden share.</span></span>
    
3. <span data-ttu-id="6ab4a-182">Impostare le autorizzazioni di condivisione seguenti:</span><span class="sxs-lookup"><span data-stu-id="6ab4a-182">Set the following share permissions:</span></span>
    
  - <span data-ttu-id="6ab4a-183">Depositari: modifica, lettura</span><span class="sxs-lookup"><span data-stu-id="6ab4a-183">Custodians: Change, Read</span></span>
    
  - <span data-ttu-id="6ab4a-184">Amministratori: controllo completo</span><span class="sxs-lookup"><span data-stu-id="6ab4a-184">Administrators: Full Control</span></span>
    
  - <span data-ttu-id="6ab4a-185">Sottosistema attendibile di Exchange: modifica, lettura</span><span class="sxs-lookup"><span data-stu-id="6ab4a-185">Exchange Trusted Subsystem: Change, Read</span></span>
    
4. <span data-ttu-id="6ab4a-186">Aprire la scheda **sicurezza** , aggiungere il gruppo depositari e fare clic su **Avanzate**.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-186">Open the **Security** tab, add the Custodians group, and click **Advanced**.</span></span> <span data-ttu-id="6ab4a-187">Impostare le autorizzazioni seguenti per il gruppo depositari:</span><span class="sxs-lookup"><span data-stu-id="6ab4a-187">Set the following permissions for the Custodians group:</span></span>
    
  - <span data-ttu-id="6ab4a-188">**Digitare: Deny**</span><span class="sxs-lookup"><span data-stu-id="6ab4a-188">**Type: Deny**</span></span>
    
  - <span data-ttu-id="6ab4a-189">**Si applica a: cartella, sottocartelle e file**</span><span class="sxs-lookup"><span data-stu-id="6ab4a-189">**Applies to: This folder, subfolders and files**</span></span>
    
5. <span data-ttu-id="6ab4a-190">Fare clic su **autorizzazioni avanzate** e selezionare le opzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="6ab4a-190">Click **Advanced Permissions** and select the following:</span></span>
    
  - <span data-ttu-id="6ab4a-191">**Attributi di lettura**</span><span class="sxs-lookup"><span data-stu-id="6ab4a-191">**Read attributes**</span></span>
    
  - <span data-ttu-id="6ab4a-192">**Leggere gli attributi estesi**</span><span class="sxs-lookup"><span data-stu-id="6ab4a-192">**Read extended attributes**</span></span>
    
  - <span data-ttu-id="6ab4a-193">**Autorizzazioni di lettura**</span><span class="sxs-lookup"><span data-stu-id="6ab4a-193">**Read permissions**</span></span>
    
6. <span data-ttu-id="6ab4a-194">Verificare l'accesso ai casi $ condivisione file eseguendo le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="6ab4a-194">Test access to the Cases$ file share by doing the following:</span></span>
    
1. <span data-ttu-id="6ab4a-195">Aggiungere un utente al gruppo depositari.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-195">Add a user to the Custodians group.</span></span>
    
2. <span data-ttu-id="6ab4a-196">Inserire un file nella cartella Cases $.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-196">Place a file in the Cases$ folder.</span></span>
    
3. <span data-ttu-id="6ab4a-197">Come utente, passare al server di gestione temporanea, ad esempio passare alla \\ \\ condivisione di gestione temporanea per vedere quali condivisioni sono disponibili.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-197">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available.</span></span> <span data-ttu-id="6ab4a-198">Non dovrebbero essere visualizzati i **casi $** Share elencato.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-198">You shouldn't see the **Cases$** share listed.</span></span>
    
4. <span data-ttu-id="6ab4a-199">Digitare manualmente il percorso completo per la condivisione dei casi $ in Esplora.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-199">Manually type the full path to the Cases$ share into Explorer.</span></span> <span data-ttu-id="6ab4a-200">Questo dovrebbe aprire la condivisione dei casi $.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-200">This should open the Cases$ share.</span></span>
    
5. <span data-ttu-id="6ab4a-201">Provare ad aprire il file precedentemente inserito nella condivisione.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-201">Try to open the file you previously placed in the share.</span></span> <span data-ttu-id="6ab4a-202">Questo errore dovrebbe essere esito negativo.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-202">This should fail.</span></span>
    
### <a name="logon-script"></a><span data-ttu-id="6ab4a-203">Script di accesso</span><span class="sxs-lookup"><span data-stu-id="6ab4a-203">Logon script</span></span>

1. <span data-ttu-id="6ab4a-204">Copiare e incollare lo script di Windows PowerShell nel blocco note:</span><span class="sxs-lookup"><span data-stu-id="6ab4a-204">Copy and paste this Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. <span data-ttu-id="6ab4a-205">Salvare lo script di cui sopra come CollectionScript.ps1 in una posizione facile da trovare, ad esempio C: \\ AFCScripts.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-205">Save the above script as CollectionScript.ps1 in a location that's easy for you to find, for example, C:\\AFCScripts.</span></span>
    
3. <span data-ttu-id="6ab4a-206">Utilizzare la funzionalità Vai a in blocco note.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-206">Use the Go To feature in Notepad.</span></span> <span data-ttu-id="6ab4a-207">Apportare le modifiche seguenti, in base alle esigenze:</span><span class="sxs-lookup"><span data-stu-id="6ab4a-207">Make the following changes, as needed:</span></span>
    
|<span data-ttu-id="6ab4a-208">**Riga #**</span><span class="sxs-lookup"><span data-stu-id="6ab4a-208">**Line #**</span></span>|<span data-ttu-id="6ab4a-209">**Operazioni necessarie per la modifica**</span><span class="sxs-lookup"><span data-stu-id="6ab4a-209">**What you need to change**</span></span>|<span data-ttu-id="6ab4a-210">**Obbligatorio/facoltativo**</span><span class="sxs-lookup"><span data-stu-id="6ab4a-210">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="6ab4a-211">71</span><span class="sxs-lookup"><span data-stu-id="6ab4a-211">71</span></span>  <br/> |<span data-ttu-id="6ab4a-212">Variabile **$FileTypes** .</span><span class="sxs-lookup"><span data-stu-id="6ab4a-212">**$FileTypes** variable.</span></span> <span data-ttu-id="6ab4a-213">Includere tutte le estensioni di file che si desidera vengano inventariate dallo script e che vengano raccolte nella variabile di tipo Array.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-213">Include all the file type extensions that you want the script to inventory and collect in the array variable.</span></span> <br/> |<span data-ttu-id="6ab4a-214">Facoltativo</span><span class="sxs-lookup"><span data-stu-id="6ab4a-214">Optional</span></span>  <br/> |
|<span data-ttu-id="6ab4a-215">76 e 77</span><span class="sxs-lookup"><span data-stu-id="6ab4a-215">76 and 77</span></span>  <br/> |<span data-ttu-id="6ab4a-216">Modificare il modo in cui viene creata la variabile **$CaseNo** in base alle proprie esigenze.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-216">Change the way the **$CaseNo** variable is built to suit your needs.</span></span> <span data-ttu-id="6ab4a-217">Lo script acquisisce la data e l'ora correnti e aggiunge il nome dell'utente.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-217">The script captures the current date and time and appends the user name to it.</span></span> <br/> |<span data-ttu-id="6ab4a-218">Facoltativo</span><span class="sxs-lookup"><span data-stu-id="6ab4a-218">Optional</span></span>  <br/> |
|<span data-ttu-id="6ab4a-219">80</span><span class="sxs-lookup"><span data-stu-id="6ab4a-219">80</span></span>  <br/> |<span data-ttu-id="6ab4a-220">**$CaseRootLocation** variabile deve essere impostata sulla condivisione file della raccolta dei server di gestione temporanea, ad esempio per i \*\* \\ \\ casi di gestione temporanea \\ $\*\*.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-220">**$CaseRootLocation** variable needs to be set to your staging servers collection file share, for example **\\\\Staging\\Cases$**.</span></span> <br/> |<span data-ttu-id="6ab4a-221">Obbligatorio</span><span class="sxs-lookup"><span data-stu-id="6ab4a-221">Required</span></span>  <br/> |
   
4. <span data-ttu-id="6ab4a-222">Inserire il file CollectionScript.ps1 nella condivisione file Netlogon in un controller di dominio.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-222">Place the CollectionScript.ps1 file in the Netlogon file share on a domain controller.</span></span> 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a><span data-ttu-id="6ab4a-223">Configurare l'oggetto Criteri di gruppo per lo script di accesso e i gruppi di depositari</span><span class="sxs-lookup"><span data-stu-id="6ab4a-223">Configure GPO for the logon script and Custodians Group</span></span>

1. <span data-ttu-id="6ab4a-224">Configurare uno script di accesso per il gruppo depositari seguendo la sezione "come assegnare gli script di accesso degli utenti" nell'argomento [utilizzo degli script di avvio, arresto, accesso e disconnessione in criteri di gruppo](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span><span class="sxs-lookup"><span data-stu-id="6ab4a-224">Configure a logon script for the Custodians group by following the "How to assign user logon scripts" section in the topic, [Using Startup, Shutdown, Logon, and Logoff Scripts in Group Policy](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span></span>
    
2. <span data-ttu-id="6ab4a-225">Rimuovere gli utenti autenticati dai **filtri di sicurezza**e aggiungere il gruppo depositari.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-225">Remove authenticated users from **Security Filtering**, and add the Custodians group.</span></span>
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a><span data-ttu-id="6ab4a-226">Opzione di importazione PST A, script per Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="6ab4a-226">PST import Option A, script for Exchange Server 2013</span></span>

1.  <span data-ttu-id="6ab4a-227">Copiare e incollare lo script di Windows PowerShell seguente nel blocco note:</span><span class="sxs-lookup"><span data-stu-id="6ab4a-227">Copy and paste the following Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format https://<exchange server FQDN>/Powershell

$ConnectionUri = 'https://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. <span data-ttu-id="6ab4a-228">Salvare lo script come PSTImportScript.ps1 in una posizione facile da trovare.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-228">Save the script as PSTImportScript.ps1 in a location that's easy for you to find.</span></span> <span data-ttu-id="6ab4a-229">Ad esempio, per semplificare l'utilizzo, creare una cartella nel server di gestione temporanea denominato \\ \\ staging \\ AFCScripts e salvarla.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-229">For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span></span>
    
3. <span data-ttu-id="6ab4a-230">Utilizzare la funzionalità Vai a in blocco note e apportare le modifiche seguenti, in base alle esigenze:</span><span class="sxs-lookup"><span data-stu-id="6ab4a-230">Use the Go To feature in Notepad, and make the following changes, as needed:</span></span>
    
|<span data-ttu-id="6ab4a-231">**Riga #**</span><span class="sxs-lookup"><span data-stu-id="6ab4a-231">**Line #**</span></span>|<span data-ttu-id="6ab4a-232">**Operazioni necessarie per la modifica**</span><span class="sxs-lookup"><span data-stu-id="6ab4a-232">**What you need to change**</span></span>|<span data-ttu-id="6ab4a-233">**Obbligatorio/facoltativo**</span><span class="sxs-lookup"><span data-stu-id="6ab4a-233">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="6ab4a-234">12 </span><span class="sxs-lookup"><span data-stu-id="6ab4a-234">12</span></span>  <br/> |<span data-ttu-id="6ab4a-235">**$FolderIdentifier** tag le cartelle di cassette postali in cui vengono importati PST.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-235">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into.</span></span> <span data-ttu-id="6ab4a-236">Se necessario, modificare l'operazione.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-236">Change this if necessary.</span></span> <br/> |<span data-ttu-id="6ab4a-237">Facoltativo</span><span class="sxs-lookup"><span data-stu-id="6ab4a-237">Optional</span></span>  <br/> |
|<span data-ttu-id="6ab4a-238">17 </span><span class="sxs-lookup"><span data-stu-id="6ab4a-238">17</span></span>  <br/> |<span data-ttu-id="6ab4a-239">**$ConnectionURI** necessario impostare il proprio server.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-239">**$ConnectionUri** needs to be set to your own server.</span></span> <br/> <span data-ttu-id="6ab4a-240">> [!IMPORTANT]> verificare che il **$ConnectionURI** punti a una posizione http, non a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-240">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https.</span></span> <span data-ttu-id="6ab4a-241">Non funzionerà con https:.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-241">It won't work with https:.</span></span>          |<span data-ttu-id="6ab4a-242">Obbligatorio</span><span class="sxs-lookup"><span data-stu-id="6ab4a-242">Required</span></span>  <br/> |
   
4. <span data-ttu-id="6ab4a-243">Verificare che l'account di sottosistema attendibile di Exchange disponga delle autorizzazioni di lettura, scrittura ed esecuzione per i \\ \\ casi di gestione temporanea \\ $ share.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-243">Verify that the Exchange Trusted Subsystem account has Read, Write, and Execute permissions to the \\\\Staging\\Cases$ share.</span></span>
    
5. <span data-ttu-id="6ab4a-244">Lo script di importazione PST richiede i due parametri di input seguenti:</span><span class="sxs-lookup"><span data-stu-id="6ab4a-244">The PST import script requires the following two input parameters:</span></span>
    
  - <span data-ttu-id="6ab4a-245">**$SourcePath** La posizione dei file PST da importare, ad esempio i \\ \\ casi di gestione temporanea \\ $.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-245">**$SourcePath** The location of the PST files to be imported, for example \\\\Staging\\Cases$.</span></span>
    
  - <span data-ttu-id="6ab4a-246">**$MailboxAlias** L'alias della cassetta postale di destinazione che riceverà gli elementi di posta elettronica importati.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-246">**$MailboxAlias** The alias of the target mailbox that will receive the imported email items.</span></span>
    
6. <span data-ttu-id="6ab4a-247">Ad esempio, se si desidera importare tutti i file PST dal percorso \\ Staging\Cases $ in una cassetta postale con l'alias eDiscoveryMailbox, è necessario eseguire lo script in questo modo `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox` .</span><span class="sxs-lookup"><span data-stu-id="6ab4a-247">For example, if you want to import all the PST files from the path \\Staging\Cases$ into a mailbox with the alias eDiscoveryMailbox, you would run the script like this `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="6ab4a-248">Opzione di importazione PST B, per Exchange Online</span><span class="sxs-lookup"><span data-stu-id="6ab4a-248">PST Import Option B, for Exchange Online</span></span>

-  <span data-ttu-id="6ab4a-249">Creare la struttura delle cassette postali in cui inserire i file PST importati.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-249">Create the mailbox structure to place the imported PST files into.</span></span> <span data-ttu-id="6ab4a-250">Per ulteriori informazioni su come creare una cassetta postale utente in Exchange Online, vedere[creare cassette postali utente in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span><span class="sxs-lookup"><span data-stu-id="6ab4a-250">For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span></span>
    
### <a name="cold-storage"></a><span data-ttu-id="6ab4a-251">Archiviazione frigorifera</span><span class="sxs-lookup"><span data-stu-id="6ab4a-251">Cold storage</span></span>

1. <span data-ttu-id="6ab4a-252">Creare una condivisione file nella macchina virtuale di Azure, in cui verranno posizionati tutti i file raccolti, ad esempio \\ \\ AZFile1 \\ ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-252">Create a file share on the Azure Virtual Machine, where all the collected files will be placed, for example, \\\\AZFile1\\ContentColdStorage.</span></span>
    
2. <span data-ttu-id="6ab4a-253">Concedere all'account di accesso al contenuto predefinito almeno le autorizzazioni di lettura per la condivisione e tutte le sottocartelle e i file.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-253">Grant the default content access account at least Read permissions to the share and all subfolders and files.</span></span> <span data-ttu-id="6ab4a-254">Per ulteriori informazioni sulla configurazione della ricerca di SharePoint 2013, vedere [creare e configurare un'applicazione del servizio di ricerca in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span><span class="sxs-lookup"><span data-stu-id="6ab4a-254">For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span></span>
    
3. <span data-ttu-id="6ab4a-255">Se si prevede di importare i file PST da \\ \\ AZFile1 \\ ContentColdStorage, concedere al sottosistema attendibile di Exchange le autorizzazioni di lettura, scrittura ed esecuzione per la condivisione.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-255">If you anticipate importing PST files from \\\\AZFile1\\ContentColdStorage, grant the Exchange Trusted Subsystem Read, Write, and Execute permissions to the share.</span></span>
    
### <a name="orchestrator"></a><span data-ttu-id="6ab4a-256">Orchestrator</span><span class="sxs-lookup"><span data-stu-id="6ab4a-256">Orchestrator</span></span>

1. <span data-ttu-id="6ab4a-257">Scaricare la[ Runbook di MoveToColdStorage](https://go.microsoft.com/fwlink/?LinkId=616095) dall'area download Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-257">Download the[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) from the Microsoft Download Center.</span></span>
    
2. <span data-ttu-id="6ab4a-258">Aprire la **finestra di progettazione di Runbook**, nel riquadro **connessioni** , fare clic sulla cartella in cui si desidera importare i Runbook.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-258">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into.</span></span> <span data-ttu-id="6ab4a-259">Fare clic sul menu **azioni** e fare clic su **Importa**.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-259">Click the **Actions** menu, and the click **Import**.</span></span> <span data-ttu-id="6ab4a-260">Verrà visualizzata la finestra di dialogo **Importa** .</span><span class="sxs-lookup"><span data-stu-id="6ab4a-260">The **Import** dialog box appears.</span></span>
    
3. <span data-ttu-id="6ab4a-261">Nella casella **percorso file** Digitare il percorso e il nome del file di Runbook che si desidera importare oppure fare clic sui puntini di sospensione ( **...**) per passare al file che si desidera importare.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-261">In the **File Location** box, type the path and file name of the runbook you want to import, or click the ellipsis ( **...**) to browse to the file you want to import.</span></span> 
    
4. <span data-ttu-id="6ab4a-262">Selezionare **Importa Runbook** e **importare i dati crittografati dell'orchestratore**.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-262">Select **Import runbooks** and **Import Orchestrator encrypted data**.</span></span> <span data-ttu-id="6ab4a-263">Cancellare **contatori**, **pianificazioni**, **variabili**, **gruppi di computer**, **importare configurazioni globali**e **sovrascrivere le configurazioni globali esistenti**.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-263">Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span></span>
    
5. <span data-ttu-id="6ab4a-264">Fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-264">Click **Finish**.</span></span>
    
6. <span data-ttu-id="6ab4a-265">Modificare la runbook di **MoveFilesToColdStorage** come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="6ab4a-265">Edit the **MoveFilesToColdStorage** runbook as follows:</span></span>
    
1. <span data-ttu-id="6ab4a-266">**Spostamento attività file** : impostare il percorso del **file di origine** per la condivisione file di raccolta, ad esempio i casi di \\ \\ gestione temporanea \\ $.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-266">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$.</span></span> <span data-ttu-id="6ab4a-267">Impostare la **cartella di destinazione** sulla condivisione file di archiviazione fredda in Azure, ad esempio \\ \\ AZFile1 \\ ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-267">Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span></span> <span data-ttu-id="6ab4a-268">Selezionare **Crea un file con un nome univoco**.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-268">Select **Create a file with a unique name**.</span></span>
    
2. <span data-ttu-id="6ab4a-269">**Elimina attività cartella** -impostare il **percorso:** per la condivisione file di raccolta, ad esempio per i \\ \\ casi di gestione temporanea \\ $ \\ \*, e selezionare **Elimina tutti i file e le sottocartelle**.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-269">**Delete Folder** activity - Set the **Path:** to the collection file share, for example \\\\Staging\\cases$\\*, and select **Delete all files and sub-folders**.</span></span> 
    
7. <span data-ttu-id="6ab4a-270">Distribuire la runbook di **MoveToColdStorage** utilizzando le procedure descritte in[Deploying Runbook](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span><span class="sxs-lookup"><span data-stu-id="6ab4a-270">Deploy the **MoveToColdStorage** runbook using the procedures in[Deploying Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span></span>
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a><span data-ttu-id="6ab4a-271">Ricerca di SharePoint locale per l'archiviazione frigorifera</span><span class="sxs-lookup"><span data-stu-id="6ab4a-271">SharePoint on-premises search for cold storage</span></span>

1. <span data-ttu-id="6ab4a-272">Creare una nuova origine di contenuto nella farm di SharePoint 2013 per la condivisione di archiviazione frigorifera in Azure, ad esempio \\ \\ AZFile1 \\ ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-272">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span></span> <span data-ttu-id="6ab4a-273">Per ulteriori informazioni sulla gestione delle origini di contenuto, vedere [aggiungere, modificare o eliminare un'origine di contenuto in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span><span class="sxs-lookup"><span data-stu-id="6ab4a-273">For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span></span>
    
2. <span data-ttu-id="6ab4a-274">Avviare una ricerca per indicizzazione completa.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-274">Start a full crawl.</span></span> <span data-ttu-id="6ab4a-275">Per ulteriori informazioni, vedere, [avviare, sospendere, riprendere o interrompere una ricerca per indicizzazione in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="6ab4a-275">For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
## <a name="using-the-solution"></a><span data-ttu-id="6ab4a-276">Utilizzo della soluzione</span><span class="sxs-lookup"><span data-stu-id="6ab4a-276">Using the solution</span></span>

<span data-ttu-id="6ab4a-277">Sono disponibili cinque passaggi principali per l'utilizzo di questa soluzione, presupponendo che non si desideri importare i file PST in Exchange Server 2013 ed Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-277">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online.</span></span> <span data-ttu-id="6ab4a-278">In questa sezione vengono fornite le procedure per tutti.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-278">This section provides you with the procedures for all of them.</span></span> <span data-ttu-id="6ab4a-279">L'interazione principale con la soluzione consiste nell'eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="6ab4a-279">Your primary interaction with the solution will be in doing the following:</span></span>
  
1. <span data-ttu-id="6ab4a-280">Gestire l'appartenenza degli utenti al gruppo depositari.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-280">Manage user membership in the Custodians group.</span></span>
    
2. <span data-ttu-id="6ab4a-281">Esaminare i file di registro generati dallo script di accesso.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-281">Review the log files generated by the logon script.</span></span> <span data-ttu-id="6ab4a-282">FileCopyErrors. log elenca tutti i file che non sono stati copiati correttamente.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-282">The FileCopyErrors.log lists all the files that were not successfully copied.</span></span> <span data-ttu-id="6ab4a-283">È necessario decidere cosa si vuole fare con loro</span><span class="sxs-lookup"><span data-stu-id="6ab4a-283">You need to decide what you want to do with them</span></span>
    
3. <span data-ttu-id="6ab4a-284">Gestione del processo di importazione PST.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-284">Managing the PST import process.</span></span>
    
4. <span data-ttu-id="6ab4a-285">Spostamento dei file di raccolta nell'archiviazione frigorifera.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-285">Moving the collection files to cold storage.</span></span>
    
<span data-ttu-id="6ab4a-286">Tutti gli altri passaggi non sono specifici di questa soluzione.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-286">All the other steps are not specific to this solution.</span></span> <span data-ttu-id="6ab4a-287">Si tratta di attività amministrative standard eseguite in SharePoint 2013, Microsoft 365 e Azure.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-287">They are standard administrative tasks that you perform in SharePoint 2013, Microsoft 365, and Azure.</span></span> <span data-ttu-id="6ab4a-288">Vi sono elementi che questa soluzione non fornisce indicazioni che è necessario risolvere in base alle esigenze dell'azienda, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="6ab4a-288">There are items that this solution does not provide any guidance that you will need to work out based on your company's needs, such as:</span></span>
  
1. <span data-ttu-id="6ab4a-289">Verifica dei casi di eDiscovery e quali custodi sono associati a questo caso.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-289">Tracking your eDiscovery cases, and which Custodians are associated with which case.</span></span>
    
2. <span data-ttu-id="6ab4a-290">Verifica dei set di raccolte di file associate a un caso di eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-290">Tracking which sets of file collections are associate with which eDiscovery case.</span></span>
    
3. <span data-ttu-id="6ab4a-291">Coordinando la tempistica dei passaggi di importazione e spostamento a freddo.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-291">Coordinating the timing of the Import and move to cold storage steps.</span></span>
    
4. <span data-ttu-id="6ab4a-292">Gestione dello spazio dei file utilizzato in Azure.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-292">Managing the file space used in Azure.</span></span>
    
5. <span data-ttu-id="6ab4a-293">Gestione delle cassette postali in cui vengono importati PST.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-293">Managing the mailboxes that PSTs are imported into.</span></span>
    
6. <span data-ttu-id="6ab4a-294">Backup e ripristino di tutti i dati locali.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-294">Backup and restoration of all on-premises data.</span></span>
    
### <a name="custodian-management"></a><span data-ttu-id="6ab4a-295">Gestione dei depositari</span><span class="sxs-lookup"><span data-stu-id="6ab4a-295">Custodian management</span></span>

- <span data-ttu-id="6ab4a-296">Per avviare il processo di raccolta automatica dei file per un singolo utente, aggiungerli al gruppo depositari.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-296">To start the automated file collection process for an individual user, add them to the Custodians group.</span></span> <span data-ttu-id="6ab4a-297">La volta successiva che l'utente accede, viene eseguito lo script di accesso assegnato al gruppo depositari tramite criteri di gruppo.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-297">The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span></span> 
    
### <a name="monitor-collected-files-and-review-log-files"></a><span data-ttu-id="6ab4a-298">Monitorare i file raccolti e controllare i file di registro</span><span class="sxs-lookup"><span data-stu-id="6ab4a-298">Monitor collected files and review log files</span></span>

1. <span data-ttu-id="6ab4a-299">Guardare la condivisione file di raccolta, ad esempio i \\ \\ casi di gestione temporanea \\ $ \\ \*, per la cartella dell'insieme dall'utente.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-299">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user.</span></span> <span data-ttu-id="6ab4a-300">Il nome della cartella verrà formattato in questo modo: *yyyyMMddHHmm_UserName* .</span><span class="sxs-lookup"><span data-stu-id="6ab4a-300">The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span></span>
    
2. <span data-ttu-id="6ab4a-301">Al termine dell'insieme, aprire la cartella della raccolta e passare alla cartella _Log.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-301">When the collection is completed, open the collection folder, and browse to the _Log folder.</span></span> <span data-ttu-id="6ab4a-302">Nella cartella _Log verranno visualizzati gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="6ab4a-302">In the _Log folder, you will see the following:</span></span>
    
  - <span data-ttu-id="6ab4a-303">Un file XML per ogni unità locale nel computer dell'utente, ad esempio **A.xml** **C.xml**.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-303">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**.</span></span> <span data-ttu-id="6ab4a-304">Questi file contengono le unità inventariali che sono denominate dopo e vengono utilizzate per l'operazione Robocopy.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-304">These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="6ab4a-305">Lo script di raccolta creerà solo una voce nel file di inventario per i tipi di file definiti nello script stesso.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-305">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself.</span></span> <span data-ttu-id="6ab4a-306">Non verrà creata una voce di inventario per ogni file nel computer dell'utente.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-306">It will not create an inventory entry for every file on the user's computer.</span></span> 
  
  - <span data-ttu-id="6ab4a-307">Un file di registro denominato FileCopyErrors. log per ogni esecuzione della raccolta.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-307">One log file named FileCopyErrors.log for each collection run.</span></span> <span data-ttu-id="6ab4a-308">Questo file contiene un elenco dei file che Robocopy non è stato in grado di copiare nella condivisione di raccolta file, ad esempio i \\ \\ casi di gestione temporanea \\ $ \\ \*.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-308">This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*.</span></span> <span data-ttu-id="6ab4a-309">Sarà necessario esaminare questo e decidere quali azioni eseguire per questi file mancanti.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-309">You will need to review this and decide what actions to take for these missed files.</span></span> <span data-ttu-id="6ab4a-310">In genere, è necessario raccoglierli manualmente se lo si desidera oppure è possibile decidere che non sono obbligatori e pertanto possono essere omessi dall'insieme.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-310">Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span></span>
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a><span data-ttu-id="6ab4a-311">Opzione di importazione PST A per Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="6ab4a-311">PST import option A for Exchange Server 2013</span></span>

1. <span data-ttu-id="6ab4a-312">Accedere al server che ospita la condivisione file di raccolta, ad esempio la **gestione temporanea**e l'apertura di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-312">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell.</span></span> <span data-ttu-id="6ab4a-313">Per ulteriori informazioni sull'avvio di Windows PowerShell, vedere[avvio di Windows PowerShell su Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span><span class="sxs-lookup"><span data-stu-id="6ab4a-313">For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span></span>
    
2. <span data-ttu-id="6ab4a-314">Impostare il criterio di esecuzione su Unrestricted.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-314">Set the Execution policy to Unrestricted .</span></span> <span data-ttu-id="6ab4a-315">Digita `Set-ExecutionPolicy Unrestricted -Scope Process` in Windows PowerShell e premi INVIO.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-315">Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span></span>
    
3. <span data-ttu-id="6ab4a-316">Eseguire il file PSTImportScript.ps1 e fornire i parametri **$SourcePath** e **$MailboxAlias** .</span><span class="sxs-lookup"><span data-stu-id="6ab4a-316">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters.</span></span> <span data-ttu-id="6ab4a-317">Per ulteriori informazioni sull'esecuzione di script di Windows PowerShell, vedere[Running scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span><span class="sxs-lookup"><span data-stu-id="6ab4a-317">For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span></span>
    
4. <span data-ttu-id="6ab4a-318">Esaminare l'output per individuare eventuali errori.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-318">Review the output for errors.</span></span>
    
5. <span data-ttu-id="6ab4a-319">Prima di tentare di importare un file PST con nome identico nella stessa cassetta postale, è necessario rimuovere la richiesta di importazione delle cassette postali.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-319">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request.</span></span> <span data-ttu-id="6ab4a-320">Eseguire il seguente comando per eseguire le operazioni seguenti: `Get-MailboxImportRequest | Remove-MailboxImportRequest` .</span><span class="sxs-lookup"><span data-stu-id="6ab4a-320">Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`.</span></span> <span data-ttu-id="6ab4a-321">Verrà richiesto di rimuovere ogni singola richiesta dalla coda.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-321">You will be prompted to remove each individual request from the queue.</span></span> <span data-ttu-id="6ab4a-322">Rispondere in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-322">Respond as needed.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="6ab4a-323">Opzione di importazione PST B, per Exchange Online</span><span class="sxs-lookup"><span data-stu-id="6ab4a-323">PST import option B, for Exchange Online</span></span>

- <span data-ttu-id="6ab4a-324">Per inserire i file PST raccolti in Exchange Online, seguire le procedure descritte nei file di importazione in Microsoft 365 tramite [caricamento di rete](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files).</span><span class="sxs-lookup"><span data-stu-id="6ab4a-324">To place the collected PST files into Exchange Online, follow the procedures in the Import files into Microsoft 365 through [network upload](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files).</span></span>
    
### <a name="move-to-cold-storage"></a><span data-ttu-id="6ab4a-325">Passare a archiviazione frigorifera</span><span class="sxs-lookup"><span data-stu-id="6ab4a-325">Move to cold storage</span></span>

1. <span data-ttu-id="6ab4a-326">Eseguire la runbook di **MoveToColdStorage** utilizzando le procedure descritte in [Running Runbook](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span><span class="sxs-lookup"><span data-stu-id="6ab4a-326">Run the **MoveToColdStorage** runbook using the procedures in [Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span></span>
    
2. <span data-ttu-id="6ab4a-327">Guardare la condivisione di file di Azure in uso per l'archiviazione a lungo termine, ad esempio \\ \\ AZFile1 \\ ContentColdStorage e la condivisione di file di raccolta locale, ad esempio i \\ \\ casi di gestione temporanea \\ $.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-327">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$.</span></span> <span data-ttu-id="6ab4a-328">I file e le cartelle devono essere visualizzati nella condivisione file di archiviazione frigorifera e scompaiono dalla condivisione file di raccolta.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-328">You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span></span>
    
### <a name="ediscovery"></a><span data-ttu-id="6ab4a-329">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="6ab4a-329">eDiscovery</span></span>

1. <span data-ttu-id="6ab4a-330">Consente di eseguire la ricerca per indicizzazione completa della condivisione file di archiviazione frigorifera come pianificazioni oppure di avviare una ricerca per indicizzazione.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-330">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl.</span></span> <span data-ttu-id="6ab4a-331">Per ulteriori informazioni sull'avvio di ricerche per indicizzazione complete o incrementali, vedere [avviare, sospendere, riprendere o interrompere una ricerca per indicizzazione in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="6ab4a-331">For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
2. <span data-ttu-id="6ab4a-332">Creare un caso di eDiscovery in SharePoint 2013 se è stata utilizzata l'opzione A per un file PST Import o creare un caso di eDiscovery in SharePoint Online se è stata utilizzata l'opzione B.</span><span class="sxs-lookup"><span data-stu-id="6ab4a-332">Create an eDiscovery case in SharePoint 2013 if you used option A for a PST file import or create an eDiscovery case in SharePoint Online if you used option B.</span></span>
    

