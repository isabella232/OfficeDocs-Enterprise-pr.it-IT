---
title: Automatizzare la raccolta di file di eDiscovery
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
description: 'Riepilogo: Informazioni su come automatizzare la raccolta di file dal computer degli utenti di eDiscovery.'
ms.openlocfilehash: bb93bed80ec95511c6bbf4307d1f0c9e1d4f82cb
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="automate-file-collection-for-ediscovery"></a><span data-ttu-id="ce4c1-103">Automatizzare la raccolta di file di eDiscovery</span><span class="sxs-lookup"><span data-stu-id="ce4c1-103">Automate file collection for eDiscovery</span></span>

 <span data-ttu-id="ce4c1-104">**Riepilogo:** Informazioni su come automatizzare la raccolta di file dal computer degli utenti di eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-104">**Summary:** Learn how to automate file collection from user computers for eDiscovery.</span></span>
  
<span data-ttu-id="ce4c1-p101">Tutte le aziende devono affrontare la possibilità di azioni legali o altri tipi di azioni legali. Mentre è possibile utilizzare i reparti legali per riduzione dell'esposizione, conservazione per controversia è un fatto del ciclo di vita di business. Quando una società con un'azione legale, sono necessari passaggi del processo di esibizione, per fornire tutte le prime documentali rilevanti per il corso e del consulente opposto.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p101">All companies face the potential of lawsuits or other types of legal action. While legal departments work to reduce that exposure, litigation is a fact of business life. When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span></span> 
  
<span data-ttu-id="ce4c1-p102">eDiscovery è il processo di cui società inventario, di ricerca, identificano, conservare, filtrare e rendere disponibile il materiale documentale esistenti in formato elettronico. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online ed Exchange Online può contenere grandi quantità di contenuto documentale. A seconda della versione, questi prodotti può supportare eDiscovery e dell'archiviazione sul posto (Lync tramite Exchange Server), renderla più semplice per i team legali indicizzare, identificano, premere e filtrare il contenuto per un determinato caso più pertinente.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p102">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content. Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span></span>
  
<span data-ttu-id="ce4c1-p103">Numero di documenti viene archiviati in degli utenti (depositari) computer locale, non in una posizione centralizzata. In questo modo essenzialmente impedisce per SharePoint 2013 per la ricerca e se non possono essere ricercata, non possono essere incluse nel eDiscovery. Questa soluzione viene illustrato come utilizzare gli script di accesso, System Center agente di orchestrazione 2012 R2 e Windows PowerShell per Exchange Server per automatizzare l'identificazione e l'insieme di materiale documentali dai computer degli utenti.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p103">Many documents are stored on users' (Custodians) local computers, not in a centralized location. This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery. This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span></span>
  
## <a name="what-this-solution-does"></a><span data-ttu-id="ce4c1-114">Questa soluzione non</span><span class="sxs-lookup"><span data-stu-id="ce4c1-114">What this solution does</span></span>

<span data-ttu-id="ce4c1-p104">Questa soluzione utilizza un gruppo, gruppo di protezione globale criteri e uno script di Windows PowerShell per individuare, preparare un inventario e raccogliere contenuto e i file di archivio personale (PST) di Outlook dal computer locale di utenti in una condivisione file nascosti. Da quest'ultimo, è possibile importare i file PST in Exchange Server 2013 o Exchange Online. Tutti i file vengono spostati utilizzando un runbook di System Center agente di orchestrazione 2012 R2 in un altro condivisione di file in Microsoft Azure per indicizzazione da SharePoint 2013 e l'archiviazione a lungo termine. Utilizzare quindi centri eDiscovery della distribuzione di SharePoint 2013 in locale o in SharePoint Online come regolarmente per eseguire eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p104">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share. From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online. All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013. You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="ce4c1-p105">Questa soluzione utilizza robocopy per copiare i file dai computer del depositaria in una condivisione file centralizzata. Poiché robocopy non vengono copiati file aperto o bloccato, i file, inclusi i file PST, che il depositaria sia aperto non saranno raccolti. È necessario raccolgono i dati manualmente. Questa soluzione fornire un elenco che identifica in modo esplicito i file che non può copiare e il percorso completo di tutti i file.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p105">This solution uses robocopy to copy files from custodian's computers to a centralized file share. Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected. You will have to collect them manually. This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span></span> 
  
<span data-ttu-id="ce4c1-123">Nel diagramma seguente illustra tutti i passaggi e gli elementi della soluzione.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-123">The following diagram walks you through all the steps and elements of the solution.</span></span>
  
![Panoramica della soluzione per la raccolta automatica dei file](images/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|<span data-ttu-id="ce4c1-125">Legenda * * *</span><span class="sxs-lookup"><span data-stu-id="ce4c1-125">****Legend****</span></span>||
|:-----|:-----|
|![callout magenta 1](images/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|<span data-ttu-id="ce4c1-127">Creare un oggetto Criteri di gruppo (GPO) e associarlo allo script di accesso della raccolta.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-127">Create a Group Policy object (GPO), and associate it with the collection logon script.</span></span>  <br/> |
|![callout magenta 2](images/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| <span data-ttu-id="ce4c1-129">Configurare il filtro di protezione oggetto Criteri di gruppo per l'oggetto Criteri di gruppo si applicano solo al gruppo depositari.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-129">Configure the GPO security filter to apply the GPO only to the Custodians group.</span></span> <br/> |
|![callout magenta 3](images/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|<span data-ttu-id="ce4c1-131">Un depositaria accede e viene eseguito l'oggetto Criteri di gruppo, lo script di accesso raccolta la chiamata.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-131">A Custodian logs on and the GPO runs, calling the collection logon script.</span></span>  <br/> |
|![callout magenta 4](images/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|<span data-ttu-id="ce4c1-133">Lo script di accesso raccolta inventario di tutte le unità collegate localmente nel computer depositari, cercare i file desiderato e relativo percorso di registrazione.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-133">The collection logon script inventories all locally attached drives on the Custodians computer, searching for the files you want, and recording their location.</span></span>  <br/> |
|![callout magenta 5](images/4bf8898c-44ad-4524-b983-70175804eb85.png)|<span data-ttu-id="ce4c1-135">Lo script di accesso raccolta copia i file di inventario in una condivisione file nascosto nel server di gestione temporanea.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-135">The collection logon script copies the inventoried files to a hidden file share on the staging server.</span></span>  <br/> |
|![callout magenta 6](images/99589726-0c7e-406b-a276-44301a135768.png)| <span data-ttu-id="ce4c1-137">(Opzione A) Eseguire manualmente lo script di importazione file PST per importare i file PST raccolti in Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-137">(Option A) Manually run the PST import script to import the collected PST files into Exchange Server 2013.</span></span> <br/> |
|![callout magenta 7](images/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|<span data-ttu-id="ce4c1-139">(Opzione B) Utilizzando lo strumento Office 365 importare e processo, importare i file PST raccolti in Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-139">(Option B) Using the Office 365 Import tool and process, import the collected PST files into Exchange Online.</span></span>  <br/> |
|![callout magenta 8](images/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|<span data-ttu-id="ce4c1-141">Spostare tutte le raccolti file a una condivisione file Azure per l'archiviazione a lungo termine con runbook MoveToColdStorage System Center agente di orchestrazione 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-141">Move all collected files to an Azure file share for long term storage with the MoveToColdStorage System Center Orchestrator 2012 R2 runbook.</span></span> <br/> |
|![callout magenta 9](images/b354642e-445e-4723-a84a-b41f7ac6e774.png)|<span data-ttu-id="ce4c1-143">Indicizzare i file nella condivisione di file di archiviazione fredda con SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-143">Index the files in the cold storage file share with SharePoint 2013.</span></span>  <br/> |
|![callout magenta 10](images/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|<span data-ttu-id="ce4c1-145">Eseguire eDiscovery sul contenuto in archiviazione fredda e in locale Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-145">Perform eDiscovery on content in cold storage and in the on-premises Exchange Server 2013.</span></span>  <br/> |
|![callout magenta 11](images/e59ab403-2f19-497a-92a5-549846dded66.png)|<span data-ttu-id="ce4c1-147">Eseguire eDiscovery sul contenuto in Office 365.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-147">Perform eDiscovery on content in Office 365.</span></span>  <br/> |
   
## <a name="prerequisites"></a><span data-ttu-id="ce4c1-148">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="ce4c1-148">Prerequisites</span></span>

<span data-ttu-id="ce4c1-p106">La configurazione di questa soluzione richiede più molti elementi di cui probabile che in vigore e configurato se si sta valutando eDiscovery. Per gli elementi che non si dispone o caratteri che richiedono una configurazione specifica, si verrà fornire i collegamenti è necessario creare fuori la configurazione di base. Prima di configurare la soluzione stessa, è necessario disporre la configurazione di base sul posto.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p106">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery. For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration. You must have the base configuration in place before you configure the solution itself.</span></span>
  
### <a name="base-configuration"></a><span data-ttu-id="ce4c1-152">Configurazione di base</span><span class="sxs-lookup"><span data-stu-id="ce4c1-152">Base configuration</span></span>

|<span data-ttu-id="ce4c1-153">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="ce4c1-153">**Element**</span></span>|<span data-ttu-id="ce4c1-154">**Collegamento**</span><span class="sxs-lookup"><span data-stu-id="ce4c1-154">**Link**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ce4c1-155">Dominio di Active Directory Domain Services (AD DS)</span><span class="sxs-lookup"><span data-stu-id="ce4c1-155">Active Directory Domain Services (AD DS) domain</span></span>  <br/> ||
|<span data-ttu-id="ce4c1-156">Connettività Internet dalla rete locale</span><span class="sxs-lookup"><span data-stu-id="ce4c1-156">Internet connectivity from your on-premises network</span></span>  <br/> ||
|<span data-ttu-id="ce4c1-157">SQL Server 2012 per il supporto di SharePoint 2013 e System Center agente di orchestrazione 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ce4c1-157">SQL Server 2012 to support SharePoint 2013 and System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="ce4c1-158">Distribuzione di agente di orchestrazione - System Center 2012</span><span class="sxs-lookup"><span data-stu-id="ce4c1-158">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| <span data-ttu-id="ce4c1-159">Locali o Azure basato su SharePoint 2013 per eDiscovery (necessario per l'opzione A)</span><span class="sxs-lookup"><span data-stu-id="ce4c1-159">On-premises or Azure based SharePoint 2013 for eDiscovery (required for Option A)</span></span> <br/> ||
|<span data-ttu-id="ce4c1-160">Server di condivisione di file locale per la gestione temporanea</span><span class="sxs-lookup"><span data-stu-id="ce4c1-160">On-premises file share server for staging</span></span>  <br/> ||
|<span data-ttu-id="ce4c1-161">Exchange Server 2013 in locale per l'importazione dei file PST A opzione</span><span class="sxs-lookup"><span data-stu-id="ce4c1-161">On-premises Exchange Server 2013 for Option A PST import</span></span>  <br/> |<span data-ttu-id="ce4c1-162">CU5 (15.913.22) è disponibile all'indirizzo [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span><span class="sxs-lookup"><span data-stu-id="ce4c1-162">CU5 (15.913.22) is available at [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span></span>  <br/> |
|<span data-ttu-id="ce4c1-163">System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ce4c1-163">System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="ce4c1-164">Distribuzione di agente di orchestrazione - System Center 2012</span><span class="sxs-lookup"><span data-stu-id="ce4c1-164">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|<span data-ttu-id="ce4c1-165">Office 365 (piano E3) con Exchange Online e SharePoint Online (necessario per l'opzione B)</span><span class="sxs-lookup"><span data-stu-id="ce4c1-165">Office 365 (E3 Plan) with Exchange Online and SharePoint Online (required for Option B)</span></span>  <br/> |<span data-ttu-id="ce4c1-166">Per l'iscrizione per una sottoscrizione a Office 365 E3, vedere [sottoscrizione a Office 365 E3](https://go.microsoft.com/fwlink/p/?LinkId=613504).</span><span class="sxs-lookup"><span data-stu-id="ce4c1-166">To sign up for an Office 365 E3 subscription, see [Office 365 E3 subscription](https://go.microsoft.com/fwlink/p/?LinkId=613504).</span></span>  <br/> |
|<span data-ttu-id="ce4c1-167">Sottoscrizione Azure con una macchina virtuale</span><span class="sxs-lookup"><span data-stu-id="ce4c1-167">Azure subscription with a virtual machine</span></span>  <br/> |<span data-ttu-id="ce4c1-168">Per l'iscrizione per un Azure, vedere [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span><span class="sxs-lookup"><span data-stu-id="ce4c1-168">To sign up for a Azure, see [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span></span> <br/> |
|<span data-ttu-id="ce4c1-169">Una connessione VPN tra la rete locale e la sottoscrizione di Azure</span><span class="sxs-lookup"><span data-stu-id="ce4c1-169">A VPN connection between your on-premises network and your Azure subscription</span></span>  <br/> |<span data-ttu-id="ce4c1-170">Per configurare un tunnel VPN tra la sottoscrizione Azure e la rete locale, vedere [Connect una rete locale a una rete virtuale Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span><span class="sxs-lookup"><span data-stu-id="ce4c1-170">To set up a VPN tunnel between your Azure subscription and your on-premises network, see [Connect an on-premises network to a Microsoft Azure virtual network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span></span>  <br/> |
|<span data-ttu-id="ce4c1-171">Configurata la ricerca tra SharePoint e quindi fare clic su Exchange Server 2013 e facoltativamente Lync Server 2013 eDiscovery di SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="ce4c1-171">SharePoint 2013 eDiscovery configured to search across SharePoint and Exchange Server 2013 and optionally Lync Server 2013</span></span>  <br/> |<span data-ttu-id="ce4c1-172">Per configurare eDiscovery in questo modo, vedere [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) e[Guida del laboratorio di testing: configurare eDiscovery per un Exchange, Lync, SharePoint e laboratorio di testing di condivisioni di File Windows](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span><span class="sxs-lookup"><span data-stu-id="ce4c1-172">To configure eDiscovery in this fashion, see [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab Guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows File Shares Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span></span>  <br/> |
|<span data-ttu-id="ce4c1-173">eDiscovery in Office 365 per Exchange Online e SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ce4c1-173">eDiscovery in Office 365 for SharePoint Online and Exchange Online</span></span>  <br/> |<span data-ttu-id="ce4c1-174">Per configurare eDiscovery in Office 365, vedere [configurare un centro eDiscovery in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span><span class="sxs-lookup"><span data-stu-id="ce4c1-174">To configure eDiscovery in Office 365, see [Set up an eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span></span>  <br/> |
   
## <a name="configure-the-environment"></a><span data-ttu-id="ce4c1-175">Configurare l'ambiente</span><span class="sxs-lookup"><span data-stu-id="ce4c1-175">Configure the environment</span></span>

<span data-ttu-id="ce4c1-176">Dopo aver creato la configurazione di base sul posto, possono passare direttamente alla configurazione della soluzione stesso.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-176">Now that you have the base configuration in place, you can move ahead to configuring the solution itself.</span></span> 
  
### <a name="staging-file-share"></a><span data-ttu-id="ce4c1-177">Condivisione di file di gestione temporanea</span><span class="sxs-lookup"><span data-stu-id="ce4c1-177">Staging file share</span></span>

1. <span data-ttu-id="ce4c1-178">Creare un gruppo di protezione globale denominato depositari nel dominio locale.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-178">In the on-premises domain, create a global security group named Custodians.</span></span>
    
2. <span data-ttu-id="ce4c1-p107">Creare una condivisione file nascosto per i file che vengono raccolti dal computer depositari. Tale indirizzo deve corrispondere in un server locale. Ad esempio, in un server denominato gestione temporanea, creare una condivisione file denominata $ casi. Il **$** è necessario impostare tale una condivisione nascosta.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p107">Create a hidden file share for the files that are collected from Custodians computers. This should be on an on-premises server. For example, on a server called Staging, create a file share called Cases$. The **$** is required to make this a hidden share.</span></span>
    
3. <span data-ttu-id="ce4c1-183">Impostare le autorizzazioni di condivisione seguenti:</span><span class="sxs-lookup"><span data-stu-id="ce4c1-183">Set the following share permissions:</span></span>
    
  - <span data-ttu-id="ce4c1-184">Depositari: Modifica, lettura</span><span class="sxs-lookup"><span data-stu-id="ce4c1-184">Custodians: Change, Read</span></span>
    
  - <span data-ttu-id="ce4c1-185">Amministratori: controllo completo</span><span class="sxs-lookup"><span data-stu-id="ce4c1-185">Administrators: Full Control</span></span>
    
  - <span data-ttu-id="ce4c1-186">Sottosistema Trusted di Exchange: Modifica, lettura</span><span class="sxs-lookup"><span data-stu-id="ce4c1-186">Exchange Trusted Subsystem: Change, Read</span></span>
    
4. <span data-ttu-id="ce4c1-p108">Aprire la scheda **protezione** , aggiungere il gruppo depositari e fare clic su **Avanzate**. Impostare le autorizzazioni per il gruppo depositari seguenti:</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p108">Open the **Security** tab, add the Custodians group, and click **Advanced**. Set the following permissions for the Custodians group:</span></span>
    
  - <span data-ttu-id="ce4c1-189">**Tipo: Nega**</span><span class="sxs-lookup"><span data-stu-id="ce4c1-189">**Type: Deny**</span></span>
    
  - <span data-ttu-id="ce4c1-190">**Si applica a: questa cartella, sottocartelle e file**</span><span class="sxs-lookup"><span data-stu-id="ce4c1-190">**Applies to: This folder, subfolders and files**</span></span>
    
5. <span data-ttu-id="ce4c1-191">Fare clic su **Autorizzazioni avanzate** e selezionare le opzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="ce4c1-191">Click **Advanced Permissions** and select the following:</span></span>
    
  - <span data-ttu-id="ce4c1-192">**Leggere gli attributi**</span><span class="sxs-lookup"><span data-stu-id="ce4c1-192">**Read attributes**</span></span>
    
  - <span data-ttu-id="ce4c1-193">**Leggi attributi estesi**</span><span class="sxs-lookup"><span data-stu-id="ce4c1-193">**Read extended attributes**</span></span>
    
  - <span data-ttu-id="ce4c1-194">**Autorizzazioni di lettura**</span><span class="sxs-lookup"><span data-stu-id="ce4c1-194">**Read permissions**</span></span>
    
6. <span data-ttu-id="ce4c1-195">Verificare l'accesso alla condivisione di file $ casi eseguendo le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="ce4c1-195">Test access to the Cases$ file share by doing the following:</span></span>
    
1. <span data-ttu-id="ce4c1-196">Aggiungere un utente al gruppo depositari.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-196">Add a user to the Custodians group.</span></span>
    
2. <span data-ttu-id="ce4c1-197">Inserire un file nella cartella dei casi.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-197">Place a file in the Cases$ folder.</span></span>
    
3. <span data-ttu-id="ce4c1-p109">Quello dell'utente, passare al server di gestione temporanea, ad esempio passare il \\ \\Condividi per vedere le condivisioni disponibili di gestione temporanea. Si non deve vedere condivisione di **$ casi** elencata.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p109">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available. You shouldn't see the **Cases$** share listed.</span></span>
    
4. <span data-ttu-id="ce4c1-p110">Digitare il percorso completo per la condivisione di $ casi manualmente in Esplora. Verrà aperto la condivisione di $ casi.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p110">Manually type the full path to the Cases$ share into Explorer. This should open the Cases$ share.</span></span>
    
5. <span data-ttu-id="ce4c1-p111">Provare ad aprire i file che precedentemente inseriti nella condivisione. Si verificherà un errore.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p111">Try to open the file you previously placed in the share. This should fail.</span></span>
    
### <a name="logon-script"></a><span data-ttu-id="ce4c1-204">Script di accesso</span><span class="sxs-lookup"><span data-stu-id="ce4c1-204">Logon script</span></span>

1. <span data-ttu-id="ce4c1-205">Copiare e incollare questo script di Windows PowerShell nel blocco note:</span><span class="sxs-lookup"><span data-stu-id="ce4c1-205">Copy and paste this Windows PowerShell script into Notepad:</span></span>
    
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
    $TargetFileCheck = Test-Path $TargetPath\\$FileName

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
$CaseRootLocation = "\\\\staging\\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\\" + $CaseNo + "\\_Log"
$CasePSTLocation = $CaseRootLocation + "\\" + $CaseNo + "\\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\\\\$_.xml -Force
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

2. <span data-ttu-id="ce4c1-206">Salvare lo script precedente come CollectionScript.ps1 in un percorso facile da trovare, ad esempio, c:\\AFCScripts.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-206">Save the above script as CollectionScript.ps1 in a location that's easy for you to find, for example, C:\\AFCScripts.</span></span>
    
3. <span data-ttu-id="ce4c1-p112">Utilizzare la funzionalità Vai a nel blocco note. Apportare le modifiche seguenti, in base alle esigenze:</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p112">Use the Go To feature in Notepad. Make the following changes, as needed:</span></span>
    
|<span data-ttu-id="ce4c1-209">**Riga #**</span><span class="sxs-lookup"><span data-stu-id="ce4c1-209">**Line #**</span></span>|<span data-ttu-id="ce4c1-210">**Che cosa è necessario modificare**</span><span class="sxs-lookup"><span data-stu-id="ce4c1-210">**What you need to change**</span></span>|<span data-ttu-id="ce4c1-211">**Facoltativo/necessari**</span><span class="sxs-lookup"><span data-stu-id="ce4c1-211">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="ce4c1-212">71</span><span class="sxs-lookup"><span data-stu-id="ce4c1-212">71</span></span>  <br/> |<span data-ttu-id="ce4c1-p113">Variabile **$FileTypes** . Include tutte le estensioni di file che si desidera che lo script per preparare un inventario e raccogliere nella variabile di matrice.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p113">**$FileTypes** variable. Include all the file type extensions that you want the script to inventory and collect in the array variable. </span></span><br/> |<span data-ttu-id="ce4c1-215">Facoltativo</span><span class="sxs-lookup"><span data-stu-id="ce4c1-215">Optional</span></span>  <br/> |
|<span data-ttu-id="ce4c1-216">76 e 77</span><span class="sxs-lookup"><span data-stu-id="ce4c1-216">76 and 77</span></span>  <br/> |<span data-ttu-id="ce4c1-p114">Modificare il modo in cui la variabile **$CaseNo** si basa adatto alle proprie esigenze. Lo script acquisisce la data e ora correnti e aggiunge il nome dell'utente.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p114">Change the way the **$CaseNo** variable is built to suit your needs. The script captures the current date and time and appends the user name to it. </span></span><br/> |<span data-ttu-id="ce4c1-219">Facoltativo</span><span class="sxs-lookup"><span data-stu-id="ce4c1-219">Optional</span></span>  <br/> |
|<span data-ttu-id="ce4c1-220">80</span><span class="sxs-lookup"><span data-stu-id="ce4c1-220">80</span></span>  <br/> |<span data-ttu-id="ce4c1-221">Condividono **$CaseRootLocation** esigenze variabili da impostare per i file della raccolta server gestione temporanea, ad esempio ** \\ \\di gestione temporanea\\casi$**.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-221">**$CaseRootLocation** variable needs to be set to your staging servers collection file share, for example **\\\\Staging\\Cases$**.</span></span> <br/> |<span data-ttu-id="ce4c1-222">Obbligatorio</span><span class="sxs-lookup"><span data-stu-id="ce4c1-222">Required</span></span>  <br/> |
   
4. <span data-ttu-id="ce4c1-223">Inserire il file CollectionScript.ps1 nella condivisione di file Netlogon nei controller di dominio.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-223">Place the CollectionScript.ps1 file in the Netlogon file share on a domain controller.</span></span> 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a><span data-ttu-id="ce4c1-224">Configurare l'oggetto Criteri di gruppo per uno script di accesso e il gruppo depositari</span><span class="sxs-lookup"><span data-stu-id="ce4c1-224">Configure GPO for the logon script and Custodians Group</span></span>

1. <span data-ttu-id="ce4c1-225">Configurare uno script di accesso per il gruppo depositari, consultare la sezione "Come assegnare script di accesso" nell'argomento [tramite avvio, arresto, accesso e script di disconnessione in Criteri di gruppo](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span><span class="sxs-lookup"><span data-stu-id="ce4c1-225">Configure a logon script for the Custodians group by following the "How to assign user logon scripts" section in the topic, [Using Startup, Shutdown, Logon, and Logoff Scripts in Group Policy](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span></span>
    
2. <span data-ttu-id="ce4c1-226">Rimuovere gli utenti autenticati da **Filtri di protezione**e aggiungere il gruppo depositari.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-226">Remove authenticated users from **Security Filtering**, and add the Custodians group.</span></span>
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a><span data-ttu-id="ce4c1-227">PST importare opzione A, lo script per Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="ce4c1-227">PST import Option A, script for Exchange Server 2013</span></span>

1.  <span data-ttu-id="ce4c1-228">Copiare e incollare il seguente script di Windows PowerShell nel blocco note:</span><span class="sxs-lookup"><span data-stu-id="ce4c1-228">Copy and paste the following Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\\PSTImport.ps1 \\\\FileShare\\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format http://<exchange server FQDN>/Powershell

$ConnectionUri = 'http://h10-exch/PowerShell'
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

2. <span data-ttu-id="ce4c1-p115">Salvare lo script come PSTImportScript.ps1 in un percorso facile da trovare. Ad esempio e la facilità di utilizzo, creare una cartella nel server temporaneo denominato \\ \\di gestione temporanea\\AFCScripts e salvarlo disponibili.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p115">Save the script as PSTImportScript.ps1 in a location that's easy for you to find. For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span></span>
    
3. <span data-ttu-id="ce4c1-231">Utilizzare la funzionalità Vai a nel blocco note e apportare le modifiche seguenti, in base alle esigenze:</span><span class="sxs-lookup"><span data-stu-id="ce4c1-231">Use the Go To feature in Notepad, and make the following changes, as needed:</span></span>
    
|<span data-ttu-id="ce4c1-232">**Riga #**</span><span class="sxs-lookup"><span data-stu-id="ce4c1-232">**Line #**</span></span>|<span data-ttu-id="ce4c1-233">**Che cosa è necessario modificare**</span><span class="sxs-lookup"><span data-stu-id="ce4c1-233">**What you need to change**</span></span>|<span data-ttu-id="ce4c1-234">**Facoltativo/necessari**</span><span class="sxs-lookup"><span data-stu-id="ce4c1-234">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="ce4c1-235">12</span><span class="sxs-lookup"><span data-stu-id="ce4c1-235">12</span></span>  <br/> |<span data-ttu-id="ce4c1-p116">**$FolderIdentifier** tag le cartelle delle cassette postali che vengono importati nel file pst. Modificare l'impostazione se necessario.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p116">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into. Change this if necessary. </span></span><br/> |<span data-ttu-id="ce4c1-238">Facoltativo</span><span class="sxs-lookup"><span data-stu-id="ce4c1-238">Optional</span></span>  <br/> |
|<span data-ttu-id="ce4c1-239">17</span><span class="sxs-lookup"><span data-stu-id="ce4c1-239">17</span></span>  <br/> |<span data-ttu-id="ce4c1-240">**$ConnectionUri** deve essere impostata al proprio server.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-240">**$ConnectionUri** needs to be set to your own server.</span></span> <br/> <span data-ttu-id="ce4c1-p117">> [!IMPORTANT]> Verificare che l' **$ConnectionUri** punta a un percorso http, https non. Non funzionerà con https:.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p117">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https. It won't work with https:.</span></span>          |<span data-ttu-id="ce4c1-243">Obbligatorio</span><span class="sxs-lookup"><span data-stu-id="ce4c1-243">Required</span></span>  <br/> |
   
4. <span data-ttu-id="ce4c1-244">Verificare che l'account di Exchange Trusted Subsystem disponga delle autorizzazioni di lettura, scrittura ed esecuzione per il \\ \\Intermédiaire\\condivisione$ casi.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-244">Verify that the Exchange Trusted Subsystem account has Read, Write, and Execute permissions to the \\\\Staging\\Cases$ share.</span></span>
    
5. <span data-ttu-id="ce4c1-245">Lo script di importazione file PST richiede due parametri di input seguenti:</span><span class="sxs-lookup"><span data-stu-id="ce4c1-245">The PST import script requires the following two input parameters:</span></span>
    
  - <span data-ttu-id="ce4c1-246">**$SourcePath** Il percorso dei file PST da importare, ad esempio \\ \\Intermédiaire\\casi$.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-246">**$SourcePath** The location of the PST files to be imported, for example \\\\Staging\\Cases$.</span></span>
    
  - <span data-ttu-id="ce4c1-247">**$MailboxAlias** Alias della cassetta postale di destinazione che verrà visualizzati gli elementi di posta elettronica importati.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-247">**$MailboxAlias** The alias of the target mailbox that will receive the imported email items.</span></span>
    
6. <span data-ttu-id="ce4c1-248">Ad esempio, se si desidera importare tutti i file PST dal percorso \\ \\Intermédiaire\\casi$ in una cassetta postale con eDiscoveryMailbox alias, eseguire lo script simile al seguente `\\\\staging\\AFCscripts\\PSTImportScript.ps1 \\\\Staging\\cases$ eDiscoveryMailbox`.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-248">For example, if you want to import all the PST files from the path \\\\Staging\\Cases$ into a mailbox with the alias eDiscoveryMailbox, you would run the script like this `\\\\staging\\AFCscripts\\PSTImportScript.ps1 \\\\Staging\\cases$ eDiscoveryMailbox`.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="ce4c1-249">Opzione di importazione di file PST B, per Exchange Online</span><span class="sxs-lookup"><span data-stu-id="ce4c1-249">PST Import Option B, for Exchange Online</span></span>

-  <span data-ttu-id="ce4c1-p118">Creare la struttura delle cassette postali per inserire i file PST importati in. Per ulteriori informazioni su come creare una cassetta postale utente in Exchange Online, vedere[Creazione di cassette postali utente in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p118">Create the mailbox structure to place the imported PST files into. For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span></span>
    
### <a name="cold-storage"></a><span data-ttu-id="ce4c1-252">Archiviazione fredda</span><span class="sxs-lookup"><span data-stu-id="ce4c1-252">Cold storage</span></span>

1. <span data-ttu-id="ce4c1-253">Creare una condivisione file in Azure Virtual Machine, in cui verranno memorizzati tutti i file raccolti, ad esempio \\ \\AZFile1\\ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-253">Create a file share on the Azure Virtual Machine, where all the collected files will be placed, for example, \\\\AZFile1\\ContentColdStorage.</span></span>
    
2. <span data-ttu-id="ce4c1-p119">Concedere all'account di accesso al contenuto predefinito almeno autorizzazioni di lettura per la condivisione e tutte le sottocartelle e i file. Per ulteriori informazioni sulla configurazione di ricerca di SharePoint 2013, vedere [creare e configurare un'applicazione di servizio di ricerca in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p119">Grant the default content access account at least Read permissions to the share and all subfolders and files. For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span></span>
    
3. <span data-ttu-id="ce4c1-256">Se si prevede che l'importazione di file PST da \\ \\AZFile1\\ContentColdStorage, concedere Exchange Trusted Subsystem leggere, scrivere ed eseguire delle autorizzazioni per la condivisione.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-256">If you anticipate importing PST files from \\\\AZFile1\\ContentColdStorage, grant the Exchange Trusted Subsystem Read, Write, and Execute permissions to the share.</span></span>
    
### <a name="orchestrator"></a><span data-ttu-id="ce4c1-257">Agente di orchestrazione</span><span class="sxs-lookup"><span data-stu-id="ce4c1-257">Orchestrator</span></span>

1. <span data-ttu-id="ce4c1-258">Scaricare[ runbook MoveToColdStorage](https://go.microsoft.com/fwlink/?LinkId=616095) da Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-258">Download the[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) from the Microsoft Download Center.</span></span>
    
2. <span data-ttu-id="ce4c1-p120">Aprire la **Finestra di progettazione Runbook**, nel riquadro **connessioni** fare clic su cartella che si desidera importare runbook in. Fare clic su dal menu **Azioni** e quindi su **Importa**. Viene visualizzata la finestra di dialogo **Importa** .</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p120">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into. Click the **Actions** menu, and the click **Import**. The **Import** dialog box appears.</span></span>
    
3. <span data-ttu-id="ce4c1-262">Nella casella **Percorso** digitare il percorso e il nome di runbook che si desidera importare o fare clic sui puntini di sospensione ( **...**) per individuare il file da importare.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-262">In the **File Location** box, type the path and file name of the runbook you want to import, or click the ellipsis ( **...**) to browse to the file you want to import.</span></span> 
    
4. <span data-ttu-id="ce4c1-p121">Selezionare **manuali operativi di importazione** e **l'agente di orchestrazione Importa i dati crittografati**. Deselezionare **contatori**, **pianificazioni**, **variabili**, **Gruppi di Computer**, **le configurazioni globale di importazione**e **configurazioni globale esistente Sovrascrivi**.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p121">Select **Import runbooks** and **Import Orchestrator encrypted data**. Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span></span>
    
5. <span data-ttu-id="ce4c1-265">Fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-265">Click **Finish**.</span></span>
    
6. <span data-ttu-id="ce4c1-266">Modificare runbook **MoveFilesToColdStorage** come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="ce4c1-266">Edit the **MoveFilesToColdStorage** runbook as follows:</span></span>
    
1. <span data-ttu-id="ce4c1-p122">**Spostare File** - set di attività il percorso del **File di origine** per la condivisione di file insieme, ad esempio \\ \\Intermédiaire\\casi$. Condividere la **Cartella di destinazione** per il file di archivio fredda in Azure, ad esempio set \\ \\AZFile1\\ContentColdStorage. Selezionare **Crea un file con un nome univoco**.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p122">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$. Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage. Select **Create a file with a unique name**.</span></span>
    
2. <span data-ttu-id="ce4c1-270">Set di attività **Elimina cartella** - il **percorso:** all'insieme condivisione file, ad esempio \\ \\Intermédiaire\\casi$\\* e selezionare **Elimina tutti i file e sottocartelle**.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-270">**Delete Folder** activity - Set the **Path:** to the collection file share, for example \\\\Staging\\cases$\\*, and select **Delete all files and sub-folders**.</span></span> 
    
7. <span data-ttu-id="ce4c1-271">Distribuire runbook **MoveToColdStorage** utilizzando le procedure descritte in[Deploying manuali operativi](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span><span class="sxs-lookup"><span data-stu-id="ce4c1-271">Deploy the **MoveToColdStorage** runbook using the procedures in[Deploying Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span></span>
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a><span data-ttu-id="ce4c1-272">Ricerca di SharePoint locale per l'archiviazione fredda</span><span class="sxs-lookup"><span data-stu-id="ce4c1-272">SharePoint on-premises search for cold storage</span></span>

1. <span data-ttu-id="ce4c1-p123">Creare una nuova origine di contenuto in una farm di SharePoint 2013 per la condivisione di archiviazione fredda in Azure, ad esempio \\ \\AZFile1\\ContentColdStorage. Per ulteriori informazioni sulla gestione di origini di contenuto, vedere [aggiungere, modificare o eliminare un'origine contenuto in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p123">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage. For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span></span>
    
2. <span data-ttu-id="ce4c1-p124">Avviare una ricerca per indicizzazione completa. Per ulteriori informazioni, vedere [Start, sospendere, riprendere o interrompere una ricerca per indicizzazione in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p124">Start a full crawl. For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
## <a name="using-the-solution"></a><span data-ttu-id="ce4c1-277">Utilizzo della soluzione</span><span class="sxs-lookup"><span data-stu-id="ce4c1-277">Using the solution</span></span>

<span data-ttu-id="ce4c1-p125">Sono disponibili cinque passaggi principali di questa soluzione, supponendo che non si desidera importare i file PST in Exchange Server 2013 ed Exchange Online. In questa sezione vengono con le procedure per tutti gli elementi. L'interazione con la soluzione principale saranno nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p125">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online. This section provides you with the procedures for all of them. Your primary interaction with the solution will be in doing the following:</span></span>
  
1. <span data-ttu-id="ce4c1-281">Gestire l'appartenenza utente al gruppo depositari.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-281">Manage user membership in the Custodians group.</span></span>
    
2. <span data-ttu-id="ce4c1-p126">Esaminare i file di registro generati dallo script di accesso. Il FileCopyErrors.log Elenca tutti i file che non sono stati copiati. È necessario decidere quali si desidera eseguire con loro</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p126">Review the log files generated by the logon script. The FileCopyErrors.log lists all the files that were not successfully copied. You need to decide what you want to do with them</span></span>
    
3. <span data-ttu-id="ce4c1-285">Gestione del processo di importazione file PST.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-285">Managing the PST import process.</span></span>
    
4. <span data-ttu-id="ce4c1-286">Spostamento dei file di raccolta in un archivio fredda.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-286">Moving the collection files to cold storage.</span></span>
    
<span data-ttu-id="ce4c1-p127">Tutti gli altri passaggi non sono specifici per la soluzione. Sono standard attività amministrative da eseguire in SharePoint 2013 e Office 365 e Azure. Sono disponibili gli elementi che questa soluzione non fornisce le informazioni che è necessario eseguire in base alle esigenze della propria azienda, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p127">All the other steps are not specific to this solution. They are standard administrative tasks that you perform in SharePoint 2013, and Office 365 and Azure. There are items that this solution does not provide any guidance that you will need to work out based on your company's needs, such as:</span></span>
  
1. <span data-ttu-id="ce4c1-290">Verifica i casi di eDiscovery e che sono associati a qual caso depositari.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-290">Tracking your eDiscovery cases, and which Custodians are associated with which case.</span></span>
    
2. <span data-ttu-id="ce4c1-291">Verifica che gli insiemi degli insiemi di file sono associa con qual caso di eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-291">Tracking which sets of file collections are associate with which eDiscovery case.</span></span>
    
3. <span data-ttu-id="ce4c1-292">Coordinamento della scadenza dell'importazione e spostamento nell'archiviazione fredda passaggi.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-292">Coordinating the timing of the Import and move to cold storage steps.</span></span>
    
4. <span data-ttu-id="ce4c1-293">Gestione dello spazio i file utilizzati per Azure.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-293">Managing the file space used in Azure.</span></span>
    
5. <span data-ttu-id="ce4c1-294">Gestione delle cassette postali che vengono importati nel file pst.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-294">Managing the mailboxes that PSTs are imported into.</span></span>
    
6. <span data-ttu-id="ce4c1-295">Backup e ripristino dei dati in locale.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-295">Backup and restoration of all on-premises data.</span></span>
    
### <a name="custodian-management"></a><span data-ttu-id="ce4c1-296">Gestione depositaria</span><span class="sxs-lookup"><span data-stu-id="ce4c1-296">Custodian management</span></span>

- <span data-ttu-id="ce4c1-p128">Per avviare il processo di raccolta di file automatico per un singolo utente, aggiungerli al gruppo depositari. Al successivo accesso dell'utente, verrà eseguito lo script di accesso assegnato al gruppo depositari tramite criteri di gruppo.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p128">To start the automated file collection process for an individual user, add them to the Custodians group. The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span></span> 
    
### <a name="monitor-collected-files-and-review-log-files"></a><span data-ttu-id="ce4c1-299">Monitorare i file raccolti ed esaminare i file di registro</span><span class="sxs-lookup"><span data-stu-id="ce4c1-299">Monitor collected files and review log files</span></span>

1. <span data-ttu-id="ce4c1-p129">Guarda il file della raccolta di condividere, ad esempio \\ \\Intermédiaire\\casi$\\*, per la cartella di raccolta da parte dell'utente. Il nome della cartella verrà formattato simile alla seguente: *yyyyMMddHHmm_UserName* .</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p129">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user. The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span></span>
    
2. <span data-ttu-id="ce4c1-p130">Al termine dell'insieme, aprire la cartella di raccolta e passare alla cartella _Log. Nella cartella _Log, verrà visualizzato quanto segue:</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p130">When the collection is completed, open the collection folder, and browse to the _Log folder. In the _Log folder, you will see the following:</span></span>
    
  - <span data-ttu-id="ce4c1-p131">Un file XML per ogni unità locale nel computer dell'utente, ad esempio **nella cartella**, **C.xml**. Questi file contengono le unità di inventario vengono denominati dopo che vengono utilizzati per l'operazione robocopy.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p131">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**. These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="ce4c1-p132">Lo script insieme creerà solo una voce nel file di inventario per i tipi di file definito nello script stesso. Non creerà una voce di inventario per ogni file nel computer dell'utente.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p132">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself. It will not create an inventory entry for every file on the user's computer.</span></span> 
  
  - <span data-ttu-id="ce4c1-p133">Un file di log denominato FileCopyErrors.log per ogni esecuzione della raccolta. Questo file è riportato un elenco dei file che robocopy potrebbe non copia all'insieme di file condividere, ad esempio \\ \\Intermédiaire\\casi$\\*. È necessario leggere questo e decidere le azioni da intraprendere per questi file senza risposta. In genere è uno necessario raccolgono i dati manualmente se si desidera, oppure è possibile decidere che non sono necessarie e pertanto può essere omesso dall'insieme.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p133">One log file named FileCopyErrors.log for each collection run. This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*. You will need to review this and decide what actions to take for these missed files. Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span></span>
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a><span data-ttu-id="ce4c1-312">Opzione di importazione di file PST A per Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="ce4c1-312">PST import option A for Exchange Server 2013</span></span>

1. <span data-ttu-id="ce4c1-p134">Accedere al server che ospita la condivisione di file insieme, ad esempio **gestione temporanea**e aprire Windows PowerShell. Per ulteriori informazioni sull'avvio di Windows PowerShell, vedere[Avvio di Windows PowerShell in Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p134">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell. For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span></span>
    
2. <span data-ttu-id="ce4c1-p135">Impostare il criterio su senza restrizioni. Tipo `Set-ExecutionPolicy Unrestricted -Scope Process` in Windows PowerShell e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p135">Set the Execution policy to Unrestricted . Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span></span>
    
3. <span data-ttu-id="ce4c1-p136">Eseguire il file PSTImportScript.ps1 e specificare i parametri **$SourcePath** e **$MailboxAlias** . Per ulteriori informazioni sull'esecuzione di script di Windows PowerShell, vedere[Esecuzione di script](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p136">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters. For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span></span>
    
4. <span data-ttu-id="ce4c1-319">Rivedere l'output di errori.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-319">Review the output for errors.</span></span>
    
5. <span data-ttu-id="ce4c1-p137">Prima di tentare di importare un file PST omonimo nella stessa cassetta postale, è necessario rimuovere la richiesta di importazione delle cassette postali. Eseguire il comando seguente per ottenere questo risultato: `Get-MailboxImportRequest | Remove-MailboxImportRequest`. Verrà chiesto di rimuovere ogni singola richiesta dalla coda. Rispondere in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p137">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request. Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. You will be prompted to remove each individual request from the queue. Respond as needed.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="ce4c1-324">Opzione di importazione di file PST B, per Exchange Online</span><span class="sxs-lookup"><span data-stu-id="ce4c1-324">PST import option B, for Exchange Online</span></span>

- <span data-ttu-id="ce4c1-325">Per inserire i file PST raccolti in Exchange Online, eseguire le procedure illustrate nei file di importazione in Office 365 tramite la sezione per il caricamento di rete del [Servizio di importazione di Office 365](https://go.microsoft.com/fwlink/p/?LinkId=614938).</span><span class="sxs-lookup"><span data-stu-id="ce4c1-325">To place the collected PST files into Exchange Online, follow the procedures in the Import files into Office 365 through the network upload section of [Office 365 Import Service](https://go.microsoft.com/fwlink/p/?LinkId=614938).</span></span>
    
### <a name="move-to-cold-storage"></a><span data-ttu-id="ce4c1-326">Spostare in un archivio fredda</span><span class="sxs-lookup"><span data-stu-id="ce4c1-326">Move to cold storage</span></span>

1. <span data-ttu-id="ce4c1-327">Eseguire runbook **MoveToColdStorage** utilizzando le procedure descritte in[Manuali operativi in esecuzione](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span><span class="sxs-lookup"><span data-stu-id="ce4c1-327">Run the **MoveToColdStorage** runbook using the procedures in[Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span></span>
    
2. <span data-ttu-id="ce4c1-p138">Guardare la condivisione file Azure in uso per l'archiviazione di termini di tempo, ad esempio \\ \\AZFile1\\ContentColdStorage e il file della raccolta locale condividere, ad esempio \\ \\Intermédiaire\\casi$. È consigliabile visualizzare i file e cartelle vengono visualizzate nella condivisione di file di archiviazione fredda e vengono rimosse dalla condivisione di file della raccolta.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p138">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$. You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span></span>
    
### <a name="ediscovery"></a><span data-ttu-id="ce4c1-330">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="ce4c1-330">eDiscovery</span></span>

1. <span data-ttu-id="ce4c1-p139">Consentire la ricerca per indicizzazione completa nella condivisione di file fredda archiviazione deve essere eseguito pianificazioni o avviare una ricerca per indicizzazione. Per ulteriori informazioni su come avviare le ricerche per indicizzazione complete o incrementale, vedere [avviare, sospendere, riprendere o interrompere una ricerca per indicizzazione in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="ce4c1-p139">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl. For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
2. <span data-ttu-id="ce4c1-333">Creare un caso eDiscovery in SharePoint 2013 se è stata utilizzata l'opzione A per l'importazione file PST o creare un caso eDiscovery in SharePoint Online, se è stata utilizzata l'opzione B.</span><span class="sxs-lookup"><span data-stu-id="ce4c1-333">Create an eDiscovery case in SharePoint 2013 if you used option A for a PST file import or create an eDiscovery case in SharePoint Online if you used option B.</span></span>
    

