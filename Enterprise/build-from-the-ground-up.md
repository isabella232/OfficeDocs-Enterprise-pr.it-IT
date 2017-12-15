---
title: Creare da zero
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: "Riepilogo: Ottenere informazioni dettagliate sul set di cloud blocchi predefiniti di archiviazione che è possibile utilizzare per creare una soluzione o il proprio servizio di archiviazione."
ms.openlocfilehash: 18aa8cb7fa0dda05302a88487dcc69bdbcb174d5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="build-from-the-ground-up"></a><span data-ttu-id="b503c-103">Creare da zero</span><span class="sxs-lookup"><span data-stu-id="b503c-103">Build from the ground up</span></span>

 <span data-ttu-id="b503c-104">**Riepilogo:** Ottenere informazioni dettagliate sul set di cloud blocchi predefiniti di archiviazione che è possibile utilizzare per creare una soluzione o il proprio servizio di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="b503c-104">**Summary:** Get the details on the set of cloud storage building blocks that you can use to create your own storage service or solution.</span></span>
  
<span data-ttu-id="b503c-105">Soluzioni di archiviazione "Creare da zero":</span><span class="sxs-lookup"><span data-stu-id="b503c-105">"Build from the ground up" storage solutions:</span></span>
  
- <span data-ttu-id="b503c-106">Consente di creare la propria soluzione di archiviazione da zero.</span><span class="sxs-lookup"><span data-stu-id="b503c-106">Allow you to create your own storage solution from scratch.</span></span> 
    
- <span data-ttu-id="b503c-107">Richiede una programmazione tramite l'API REST.</span><span class="sxs-lookup"><span data-stu-id="b503c-107">Requires programming using the REST APIs.</span></span>
    
- <span data-ttu-id="b503c-108">Fornire il massimo di personalizzazione e flessibilità.</span><span class="sxs-lookup"><span data-stu-id="b503c-108">Provide the ultimate in customization and flexibility.</span></span>
    
<span data-ttu-id="b503c-109">Le sezioni seguenti descrivono i dettagli di ciascuna opzione di archiviazione "Creare da zero".</span><span class="sxs-lookup"><span data-stu-id="b503c-109">The following sections describe the details of each "Build from the ground up" storage option.</span></span>
  
## <a name="azure-storage-files"></a><span data-ttu-id="b503c-110">Spazio di archiviazione di Azure (file)</span><span class="sxs-lookup"><span data-stu-id="b503c-110">Azure Storage (files)</span></span>

### <a name="features"></a><span data-ttu-id="b503c-111">Caratteristiche</span><span class="sxs-lookup"><span data-stu-id="b503c-111">Features</span></span>

- <span data-ttu-id="b503c-112">Semplifica lo spostamento delle applicazioni legacy nel cloud</span><span class="sxs-lookup"><span data-stu-id="b503c-112">Makes it easier to move legacy applications to the cloud</span></span>
    
- <span data-ttu-id="b503c-113">Archiviazione BLOB preferita per le nuove applicazioni</span><span class="sxs-lookup"><span data-stu-id="b503c-113">Blob storage preferred for new applications</span></span>
    
- <span data-ttu-id="b503c-114">Può essere installato da una macchina virtuale Azure</span><span class="sxs-lookup"><span data-stu-id="b503c-114">Can mount from an Azure virtual machine</span></span>
    
- <span data-ttu-id="b503c-115">Può essere installato in locale con SMB 3.0</span><span class="sxs-lookup"><span data-stu-id="b503c-115">Can mount on-premises with SMB 3.0</span></span>
    
- <span data-ttu-id="b503c-116">Funziona con Linux e Windows</span><span class="sxs-lookup"><span data-stu-id="b503c-116">Works with Linux and Windows</span></span>
    
- <span data-ttu-id="b503c-117">Non supporta l'autenticazione basata su Active Directory Azure o gli elenchi ACL (archiviazione Azure account chiavi consentono l'autenticazione e accesso autorizzato alla condivisione file)</span><span class="sxs-lookup"><span data-stu-id="b503c-117">Doesn't support Azure AD-based authentication or ACLs (Azure Storage account keys provide authentication and authorized access to the file share)</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="b503c-118">Utilizzi comuni</span><span class="sxs-lookup"><span data-stu-id="b503c-118">Common uses</span></span>

- <span data-ttu-id="b503c-119">Migrazione di applicazioni legacy nel cloud che si basano su condivisioni di file</span><span class="sxs-lookup"><span data-stu-id="b503c-119">Migrating legacy applications to the cloud that rely on file shares</span></span>
    
- <span data-ttu-id="b503c-120">Strumenti di sviluppo della condivisione e test</span><span class="sxs-lookup"><span data-stu-id="b503c-120">Share development and testing tools</span></span>
    
- <span data-ttu-id="b503c-121">Le app distribuite possono archiviare registri, dati di diagnostica e dump di arresto anomalo del sistema</span><span class="sxs-lookup"><span data-stu-id="b503c-121">Distributed apps can store logs, diagnostic data, and crash dumps</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="b503c-122">Scenari di archiviazione chiave</span><span class="sxs-lookup"><span data-stu-id="b503c-122">Key storage scenarios</span></span>

- <span data-ttu-id="b503c-123">File di backup</span><span class="sxs-lookup"><span data-stu-id="b503c-123">Backup files</span></span>
    
### <a name="resources"></a><span data-ttu-id="b503c-124">Risorse</span><span class="sxs-lookup"><span data-stu-id="b503c-124">Resources</span></span>

<span data-ttu-id="b503c-125">Per ulteriori informazioni, fare clic [qui](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span><span class="sxs-lookup"><span data-stu-id="b503c-125">For additional information, click [here](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span></span>
  
<span data-ttu-id="b503c-126">Per informazioni sui costi, fare clic [qui](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="b503c-126">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-blobs"></a><span data-ttu-id="b503c-127">Spazio di archiviazione di Azure (blob)</span><span class="sxs-lookup"><span data-stu-id="b503c-127">Azure Storage (blobs)</span></span>

### <a name="features"></a><span data-ttu-id="b503c-128">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="b503c-128">Features</span></span>

- <span data-ttu-id="b503c-129">Ogni account di archiviazione può contenere un massimo di 500 TB (una sottoscrizione può avere più account di archiviazione)</span><span class="sxs-lookup"><span data-stu-id="b503c-129">Each storage account can hold up to 500 TB (one subscription can have multiple storage accounts)</span></span>
    
- <span data-ttu-id="b503c-130">Gli account di archiviazione sono organizzati in contenitori, a cui è applicata la sicurezza e che possono contenere BLOB</span><span class="sxs-lookup"><span data-stu-id="b503c-130">Storage accounts are organized into containers, which can have security applied to them and can contain blobs</span></span>
    
- <span data-ttu-id="b503c-131">I BLOB in blocchi sono ottimizzati per lo streaming e l’archiviazione di oggetti cloud, di dimensioni fino a 200 GB</span><span class="sxs-lookup"><span data-stu-id="b503c-131">Block blobs are optimized for streaming and storing cloud objects, up to 200 GB in size</span></span>
    
- <span data-ttu-id="b503c-132">I BLOB di pagine sono ottimizzati per rappresentare dischi PaaS e supportare scritture casuali, di dimensioni fino a 1 TB</span><span class="sxs-lookup"><span data-stu-id="b503c-132">Page blobs are optimized for representing PaaS disks and supporting random writes, up to 1 TB in size</span></span>
    
- <span data-ttu-id="b503c-133">I BLOB di accodamento sono ottimizzati per accodare le operazioni, fino a 195 GB</span><span class="sxs-lookup"><span data-stu-id="b503c-133">Append blobs are optimized for append operations, up to 195 GB</span></span>
    
- <span data-ttu-id="b503c-134">L’archiviazione Premium offre IOPS più rapidi tramite lo spazio di archiviazione SSD</span><span class="sxs-lookup"><span data-stu-id="b503c-134">Premium Storage provides faster IOPS through SSD storage</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="b503c-135">Utilizzi comuni</span><span class="sxs-lookup"><span data-stu-id="b503c-135">Common uses</span></span>

- <span data-ttu-id="b503c-136">Backup dei file, computer, i database e i dispositivi immagini e testo per le applicazioni web</span><span class="sxs-lookup"><span data-stu-id="b503c-136">Backups of files, computers, databases, and devices Images and text for web applications</span></span>
    
- <span data-ttu-id="b503c-137">Dati di configurazione per applicazioni cloud</span><span class="sxs-lookup"><span data-stu-id="b503c-137">Configuration data for cloud applications</span></span>
    
- <span data-ttu-id="b503c-138">Big data, ad esempio registri e altri set di dati di grandi dimensioni</span><span class="sxs-lookup"><span data-stu-id="b503c-138">Big data, such as logs and other large datasets</span></span>
    
- <span data-ttu-id="b503c-139">Azure utilizza l’archivio BLOB per i propri servizi, ad esempio dischi HDInsight e di macchine virtuali</span><span class="sxs-lookup"><span data-stu-id="b503c-139">Azure uses blob storage for its own services, such as HDInsight and virtual machine disks</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="b503c-140">Scenari di archiviazione chiave</span><span class="sxs-lookup"><span data-stu-id="b503c-140">Key storage scenarios</span></span>

- <span data-ttu-id="b503c-141">Gestire i dati</span><span class="sxs-lookup"><span data-stu-id="b503c-141">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="b503c-142">Risorse</span><span class="sxs-lookup"><span data-stu-id="b503c-142">Resources</span></span>

<span data-ttu-id="b503c-143">Per ulteriori informazioni, fare clic [qui](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span><span class="sxs-lookup"><span data-stu-id="b503c-143">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span></span>
  
<span data-ttu-id="b503c-144">Per informazioni sui costi, fare clic [qui](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="b503c-144">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-queues"></a><span data-ttu-id="b503c-145">Spazio di archiviazione di Azure (code)</span><span class="sxs-lookup"><span data-stu-id="b503c-145">Azure Storage (queues)</span></span>

### <a name="features"></a><span data-ttu-id="b503c-146">Caratteristiche</span><span class="sxs-lookup"><span data-stu-id="b503c-146">Features</span></span>

- <span data-ttu-id="b503c-147">L’account di archiviazione può contenere qualsiasi numero di code</span><span class="sxs-lookup"><span data-stu-id="b503c-147">Storage account can contain any number of queues</span></span>
    
- <span data-ttu-id="b503c-148">La coda può contenere qualsiasi numero di messaggi (fino a riempire l'account di archiviazione)</span><span class="sxs-lookup"><span data-stu-id="b503c-148">Queue can contain any number of messages (until the storage account is full)</span></span>
    
- <span data-ttu-id="b503c-149">I messaggi in coda vengono automaticamente eliminati dopo sette giorni se non recuperati ed eliminati da un'applicazione</span><span class="sxs-lookup"><span data-stu-id="b503c-149">Queue messages are automatically deleted after seven days if not retrieved and deleted by an application</span></span>
    
- <span data-ttu-id="b503c-150">I messaggi possono essere di dimensioni fino a 64 KB</span><span class="sxs-lookup"><span data-stu-id="b503c-150">Messages may be up to 64 KB in size</span></span>
    
- <span data-ttu-id="b503c-151">Protetto a livello di account di archiviazione</span><span class="sxs-lookup"><span data-stu-id="b503c-151">Secured at storage account level</span></span>
    
- <span data-ttu-id="b503c-152">Le code sono progettate per trasmettere i messaggi di controllo, non i dati non elaborati</span><span class="sxs-lookup"><span data-stu-id="b503c-152">Queues are intended to pass control messages, not raw data</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="b503c-153">Utilizzi comuni</span><span class="sxs-lookup"><span data-stu-id="b503c-153">Common uses</span></span>

- <span data-ttu-id="b503c-154">Creare un backlog di lavoro da elaborare in modo asincrono</span><span class="sxs-lookup"><span data-stu-id="b503c-154">Create a backlog of work to process asynchronously</span></span>
    
- <span data-ttu-id="b503c-155">Elaborazione dei messaggi del registro</span><span class="sxs-lookup"><span data-stu-id="b503c-155">Processing log messages</span></span>
    
- <span data-ttu-id="b503c-156">Decuplicare le applicazioni</span><span class="sxs-lookup"><span data-stu-id="b503c-156">Decouple applications</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="b503c-157">Scenari di archiviazione chiave</span><span class="sxs-lookup"><span data-stu-id="b503c-157">Key storage scenarios</span></span>

- <span data-ttu-id="b503c-158">Distribuire gli eventi</span><span class="sxs-lookup"><span data-stu-id="b503c-158">Distribute events</span></span>
    
### <a name="resources"></a><span data-ttu-id="b503c-159">Risorse</span><span class="sxs-lookup"><span data-stu-id="b503c-159">Resources</span></span>

<span data-ttu-id="b503c-160">Per ulteriori informazioni, fare clic [qui](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span><span class="sxs-lookup"><span data-stu-id="b503c-160">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span></span>
  
<span data-ttu-id="b503c-161">Per informazioni sui costi, fare clic [qui](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="b503c-161">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-tables"></a><span data-ttu-id="b503c-162">Spazio di archiviazione di Azure (tabelle)</span><span class="sxs-lookup"><span data-stu-id="b503c-162">Azure Storage (tables)</span></span>

### <a name="features"></a><span data-ttu-id="b503c-163">Caratteristiche</span><span class="sxs-lookup"><span data-stu-id="b503c-163">Features</span></span>

- <span data-ttu-id="b503c-164">Indicato per i set di dati semi-strutturati</span><span class="sxs-lookup"><span data-stu-id="b503c-164">Best for semi-structured datasets</span></span>
    
- <span data-ttu-id="b503c-165">Costo in genere inferiore rispetto a SQL tradizionale</span><span class="sxs-lookup"><span data-stu-id="b503c-165">Typically lower cost than traditional SQL</span></span>
    
- <span data-ttu-id="b503c-166">Molto rapido se l'esecuzione di query per la chiave, lente se una query per valore</span><span class="sxs-lookup"><span data-stu-id="b503c-166">Very fast if querying for key, slow if querying for value</span></span>
    
- <span data-ttu-id="b503c-167">Ampiamente scalabile; qualsiasi quantità di tabelle entro i limiti dell'account di archiviazione</span><span class="sxs-lookup"><span data-stu-id="b503c-167">Massively scalable; any amount of tables up to the limits of the storage account</span></span>
    
- <span data-ttu-id="b503c-168">Accessibile tramite l'API REST, il protocollo oData limitato, .NET</span><span class="sxs-lookup"><span data-stu-id="b503c-168">Accessible through REST API, limited oData protocol, .NET</span></span>
    
- <span data-ttu-id="b503c-169">I valori devono essere serializzati</span><span class="sxs-lookup"><span data-stu-id="b503c-169">Values must be serialized</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="b503c-170">Utilizzi comuni</span><span class="sxs-lookup"><span data-stu-id="b503c-170">Common uses</span></span>

- <span data-ttu-id="b503c-171">Dati utente per applicazioni web</span><span class="sxs-lookup"><span data-stu-id="b503c-171">User data for web applications</span></span>
    
- <span data-ttu-id="b503c-172">Rubriche</span><span class="sxs-lookup"><span data-stu-id="b503c-172">Address books</span></span>
    
- <span data-ttu-id="b503c-173">Informazioni sul dispositivo</span><span class="sxs-lookup"><span data-stu-id="b503c-173">Device information</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="b503c-174">Scenari di archiviazione chiave</span><span class="sxs-lookup"><span data-stu-id="b503c-174">Key storage scenarios</span></span>

- <span data-ttu-id="b503c-175">Gestire i dati</span><span class="sxs-lookup"><span data-stu-id="b503c-175">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="b503c-176">Risorse</span><span class="sxs-lookup"><span data-stu-id="b503c-176">Resources</span></span>

<span data-ttu-id="b503c-177">Per ulteriori informazioni, fare clic [qui](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span><span class="sxs-lookup"><span data-stu-id="b503c-177">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span></span>
  
<span data-ttu-id="b503c-178">Per informazioni sui costi, fare clic [qui](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="b503c-178">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="microsoft-azure-storage-recommendations"></a><span data-ttu-id="b503c-179">Elementi consigliati di Archiviazione di Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="b503c-179">Microsoft Azure Storage recommendations</span></span>

<span data-ttu-id="b503c-180">Quando si progetta la soluzione di archiviazione personalizzata con l'archiviazione di Azure, tenere presente quanto segue:</span><span class="sxs-lookup"><span data-stu-id="b503c-180">When designing your custom storage solution with Azure Storage, keep the following in mind:</span></span>
  
- <span data-ttu-id="b503c-181">Utilizzare più account di archiviazione per una maggiore scalabilità, per dimensioni maggiori (> 100 TB) o per una maggiore velocità effettiva (> 5.000 operazioni al secondo).</span><span class="sxs-lookup"><span data-stu-id="b503c-181">Leverage multiple storage accounts for greater scalability, either for increased size (> 100 TB) or for more throughput (> 5,000 operations per second).</span></span>
    
- <span data-ttu-id="b503c-182">Progettare la possibilità di aggiungere account di archiviazione supplementari come una modifica della configurazione, non come una modifica del codice.</span><span class="sxs-lookup"><span data-stu-id="b503c-182">Design the ability for adding additional storage accounts as a configuration change, not as a code change.</span></span>
    
- <span data-ttu-id="b503c-183">Selezionare attentamente le funzioni di partizionamento per l'archiviazione di tabelle per abilitare la scala desiderata in termini di prestazioni di inserimento e query.</span><span class="sxs-lookup"><span data-stu-id="b503c-183">Carefully select partitioning functions for table storage to enable the desired scale in terms of insert and query performance.</span></span>
    
- <span data-ttu-id="b503c-184">Scegliere nomi di colonna brevi per le proprietà di tabella, in quanto i metadati (nomi di proprietà) vengono archiviati in banda (i nomi di colonna vengono considerati anche ai fini delle dimensioni massime di riga pari a 1 MB).</span><span class="sxs-lookup"><span data-stu-id="b503c-184">Choose short column names for table properties as the metadata (property names) are stored in-band (the column names also count towards the maximum row size of 1 MB).</span></span>
    
- <span data-ttu-id="b503c-185">Se possibile, raggruppare le operazioni nello spazio di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="b503c-185">When possible, batch operations into storage.</span></span>
    
- <span data-ttu-id="b503c-186">Memorizzare in modo aggressivo le informazioni presenti nel database di configurazione in una cache distribuita.</span><span class="sxs-lookup"><span data-stu-id="b503c-186">Aggressively cache information in the configuration database into a distributed cache.</span></span>
    
- <span data-ttu-id="b503c-187">Se le prestazioni o l’affidabilità dell'applicazione dipendono dalla disponibilità di un determinato segmento di dati presente nella cache, l'applicazione deve rifiutare le richieste in arrivo fino a quando la cache non viene prepopolata.</span><span class="sxs-lookup"><span data-stu-id="b503c-187">If application performance or reliability is dependent on having a certain segment of data available in the cache, your application should refuse incoming requests until the cache has been pre-populated.</span></span>
    
- <span data-ttu-id="b503c-188">Suddividere i dati in verticale (per tabella) o in orizzontale (segmentare la tabella in più partizioni) per distribuire il carico tra più database.</span><span class="sxs-lookup"><span data-stu-id="b503c-188">Partition the data in either vertically (by table) or horizontally (segment table across multiple shards) to spread the load across multiple databases.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="b503c-189">See Also</span><span class="sxs-lookup"><span data-stu-id="b503c-189">See Also</span></span>

[<span data-ttu-id="b503c-190">Archiviazione cloud Microsoft per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="b503c-190">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="b503c-191">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="b503c-191">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="b503c-192">Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT</span><span class="sxs-lookup"><span data-stu-id="b503c-192">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



