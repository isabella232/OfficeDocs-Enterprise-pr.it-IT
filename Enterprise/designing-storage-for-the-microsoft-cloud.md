---
title: Progettazione dello spazio di archiviazione per il cloud Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 7e511118-1b75-413a-b959-ad0d3ffc9516
description: "Sintesi: vengono fornite informazioni sul perché sia necessaria l'archiviazione cloud e l'elenco delle opzioni di archiviazione cloud di Microsoft e gli scenari di archiviazione chiave."
ms.openlocfilehash: ed816743e2d85a622a3fbfbb129bf90a7db93881
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="designing-storage-for-the-microsoft-cloud"></a><span data-ttu-id="de795-103">Progettazione dello spazio di archiviazione per il cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="de795-103">Designing storage for the Microsoft cloud</span></span>

 <span data-ttu-id="de795-104">**Sintesi:** vengono fornite informazioni sul perché sia necessaria l'archiviazione cloud e l'elenco delle opzioni di archiviazione cloud di Microsoft e gli scenari di archiviazione chiave.</span><span class="sxs-lookup"><span data-stu-id="de795-104">**Summary:** Understand why you need cloud storage and review the list of Microsoft's cloud storage options and the key storage scenarios.</span></span>
  
<span data-ttu-id="de795-105">L'integrazione dello spazio di archiviazione con servizi cloud Microsoft consente di accedere a una vasta gamma di servizi e opzioni della piattaforma cloud.</span><span class="sxs-lookup"><span data-stu-id="de795-105">Integrating your storage with Microsoft cloud services gives you access to a broad range of services and cloud platform options.</span></span>
  
## <a name="why-cloud-storage"></a><span data-ttu-id="de795-106">Spazio di archiviazione cloud, perché?</span><span class="sxs-lookup"><span data-stu-id="de795-106">Why cloud storage?</span></span>

<span data-ttu-id="de795-107">Esistono due motivi principali per utilizzare l'archiviazione cloud.</span><span class="sxs-lookup"><span data-stu-id="de795-107">There are two key reasons to use cloud storage.</span></span>
  
1. <span data-ttu-id="de795-108">Velocità di commercializzazione</span><span class="sxs-lookup"><span data-stu-id="de795-108">Speed to market:</span></span>
    
  - <span data-ttu-id="de795-109">Configurazione più rapida per disponibilità elevata e ripristino di emergenza</span><span class="sxs-lookup"><span data-stu-id="de795-109">Faster configuration for high availability and disaster recovery</span></span>
    
  - <span data-ttu-id="de795-110">Nessun hardware di archiviazione da acquistare</span><span class="sxs-lookup"><span data-stu-id="de795-110">No storage hardware to purchase</span></span>
    
  - <span data-ttu-id="de795-111">Plumbing incorporato fornito da offerte cloud di Microsoft</span><span class="sxs-lookup"><span data-stu-id="de795-111">Built-in plumbing provided by Microsoft's cloud offerings</span></span>
    
  - <span data-ttu-id="de795-112">Disponibile in qualsiasi posto del mondo</span><span class="sxs-lookup"><span data-stu-id="de795-112">Available from anywhere in the world</span></span>
    
2. <span data-ttu-id="de795-113">Costi ridotti per la manutenzione</span><span class="sxs-lookup"><span data-stu-id="de795-113">Lower costs to maintain:</span></span>
    
  - <span data-ttu-id="de795-114">Elasticità nell'aumentare o ridurre le richieste di spazio di archiviazione</span><span class="sxs-lookup"><span data-stu-id="de795-114">Elasticity to scale up and down your storage demands</span></span>
    
  - <span data-ttu-id="de795-115">Nessun hardware di archiviazione da mantenere o migrare</span><span class="sxs-lookup"><span data-stu-id="de795-115">No storage hardware to maintain or migrate</span></span>
    
  - <span data-ttu-id="de795-116">Microsoft è il plumber incorporato che consente di mantenere e migliorare l'infrastruttura</span><span class="sxs-lookup"><span data-stu-id="de795-116">Microsoft is your built-in plumber to maintain and improve infrastructure</span></span>
    
  - <span data-ttu-id="de795-117">Maggiore sicurezza dello spazio di archiviazione nel marketplace con miglioramenti continui</span><span class="sxs-lookup"><span data-stu-id="de795-117">Best storage security in the marketplace with ongoing improvements</span></span>
    
## <a name="microsoft-cloud-storage-options"></a><span data-ttu-id="de795-118">Opzioni dello spazio di archiviazione cloud di Microsoft</span><span class="sxs-lookup"><span data-stu-id="de795-118">Microsoft cloud storage options</span></span>

<span data-ttu-id="de795-119">Per comprendere meglio l'ampia gamma di opzioni relative all'archiviazione cloud, verrà usata un'analogia con la costruzione.</span><span class="sxs-lookup"><span data-stu-id="de795-119">To help you understand the wide variety of cloud storage options, we use a construction analogy.</span></span>
  
### <a name="move-in-ready"></a><span data-ttu-id="de795-120">Pronto per l'utilizzo</span><span class="sxs-lookup"><span data-stu-id="de795-120">Move-in ready</span></span>

<span data-ttu-id="de795-p101">Utilizzare queste soluzioni predefinite fornite con i servizi esistenti. Usare immediatamente e con la configurazione minima.</span><span class="sxs-lookup"><span data-stu-id="de795-p101">Use these prepackaged solutions that are bundled with existing services. Use immediately and with minimal configuration.</span></span>
  
- <span data-ttu-id="de795-123">Office 365</span><span class="sxs-lookup"><span data-stu-id="de795-123">Office 365</span></span>
    
- <span data-ttu-id="de795-124">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="de795-124">Microsoft Intune</span></span>
    
- <span data-ttu-id="de795-125">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="de795-125">OneDrive for Business</span></span>
    
- <span data-ttu-id="de795-126">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="de795-126">Dynamics 365</span></span>
    
- <span data-ttu-id="de795-127">Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="de795-127">Visual Studio Team Services</span></span>
    
- <span data-ttu-id="de795-128">Ripristino del sito di Azure</span><span class="sxs-lookup"><span data-stu-id="de795-128">Azure Site Recovery</span></span>
    
- <span data-ttu-id="de795-129">Condivisione del sito di Yammer</span><span class="sxs-lookup"><span data-stu-id="de795-129">Yammer Site Sharing</span></span>
    
- <span data-ttu-id="de795-130">Backup di Azure</span><span class="sxs-lookup"><span data-stu-id="de795-130">Azure Backup</span></span>
    
<span data-ttu-id="de795-131">Per i dettagli di ognuna di queste opzioni di archiviazione cloud, vedere [Pronto per l'utilizzo](move-in-ready.md).</span><span class="sxs-lookup"><span data-stu-id="de795-131">For the details of each of these cloud storage options, see [Move-in ready](move-in-ready.md).</span></span>
  
### <a name="some-assembly-required"></a><span data-ttu-id="de795-132">Alcuni assembly richiesti</span><span class="sxs-lookup"><span data-stu-id="de795-132">Some assembly required</span></span>

<span data-ttu-id="de795-133">Usare questi servizi esistenti come punto di partenza per la soluzione di archiviazione con configurazione aggiuntiva o codifica per un adattamento personalizzato.</span><span class="sxs-lookup"><span data-stu-id="de795-133">Use these existing services as a starting point for your storage solution with additional configuration or coding for a custom fit.</span></span>
  
- <span data-ttu-id="de795-134">Rete per la distribuzione di contenuti</span><span class="sxs-lookup"><span data-stu-id="de795-134">Azure Content Delivery Network</span></span>
    
- <span data-ttu-id="de795-135">Servizi multimediali di Azure</span><span class="sxs-lookup"><span data-stu-id="de795-135">Azure Media Services</span></span>
    
- <span data-ttu-id="de795-136">HdInsight</span><span class="sxs-lookup"><span data-stu-id="de795-136">HdInsight</span></span>
    
- <span data-ttu-id="de795-137">Cache Redis di Azure</span><span class="sxs-lookup"><span data-stu-id="de795-137">Azure Redis Cache</span></span>
    
- <span data-ttu-id="de795-138">Database SQL di Azure</span><span class="sxs-lookup"><span data-stu-id="de795-138">Azure SQL Database</span></span>
    
- <span data-ttu-id="de795-139">SQL Server in una VM di Azure</span><span class="sxs-lookup"><span data-stu-id="de795-139">SQL Server on an Azure VM</span></span>
    
- <span data-ttu-id="de795-140">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="de795-140">Azure Cosmos DB</span></span>
    
- <span data-ttu-id="de795-141">StorSimple</span><span class="sxs-lookup"><span data-stu-id="de795-141">StorSimple</span></span>
    
- <span data-ttu-id="de795-142">Data Warehouse SQL Azure</span><span class="sxs-lookup"><span data-stu-id="de795-142">Azure SQL Data Warehouse</span></span>
    
- <span data-ttu-id="de795-143">Azure Data Lake Store</span><span class="sxs-lookup"><span data-stu-id="de795-143">Azure Data Lake Store</span></span>
    
<span data-ttu-id="de795-144">Per i dettagli di ognuna di queste opzioni di archiviazione cloud, vedere [Alcuni assembly richiesti](some-assembly-required.md).</span><span class="sxs-lookup"><span data-stu-id="de795-144">For the details of each of these cloud storage options, see [Some assembly required](some-assembly-required.md).</span></span>
  
### <a name="build-from-the-ground-up"></a><span data-ttu-id="de795-145">Creare da zero</span><span class="sxs-lookup"><span data-stu-id="de795-145">Build from the ground up</span></span>

<span data-ttu-id="de795-146">Usare questi blocchi predefiniti di spazio di archiviazione, insieme alla codifica, per creare una soluzione di archiviazione o app personalizzate da zero.</span><span class="sxs-lookup"><span data-stu-id="de795-146">Use these storage building blocks, along with coding, to create your own storage solution or apps from scratch.</span></span>
  
- <span data-ttu-id="de795-147">Spazio di archiviazione di Azure (file)</span><span class="sxs-lookup"><span data-stu-id="de795-147">Azure Storage (files)</span></span>
    
- <span data-ttu-id="de795-148">Spazio di archiviazione di Azure (blob)</span><span class="sxs-lookup"><span data-stu-id="de795-148">Azure Storage (blobs)</span></span>
    
- <span data-ttu-id="de795-149">Spazio di archiviazione di Azure (code)</span><span class="sxs-lookup"><span data-stu-id="de795-149">Azure Storage (queues)</span></span>
    
- <span data-ttu-id="de795-150">Spazio di archiviazione di Azure (tabelle)</span><span class="sxs-lookup"><span data-stu-id="de795-150">Azure Storage (tables)</span></span>
    
<span data-ttu-id="de795-151">Per i dettagli di ognuna di queste opzioni di archiviazione cloud, vedere [Creare da zero](build-from-the-ground-up.md).</span><span class="sxs-lookup"><span data-stu-id="de795-151">For the details of each of these cloud storage options, see [Build from the ground up](build-from-the-ground-up.md).</span></span>
  
## <a name="key-storage-scenarios"></a><span data-ttu-id="de795-152">Scenari di archiviazione chiave</span><span class="sxs-lookup"><span data-stu-id="de795-152">Key storage scenarios</span></span>

<span data-ttu-id="de795-153">Di seguito sono illustrati gli scenari principali che richiedono l'archiviazione basata sul cloud:</span><span class="sxs-lookup"><span data-stu-id="de795-153">Here are the key scenarios that require cloud-based storage:</span></span>
  
- <span data-ttu-id="de795-154">Dati della cache</span><span class="sxs-lookup"><span data-stu-id="de795-154">Cache data</span></span>
    
    <span data-ttu-id="de795-155">Accelerare l'accesso ai dati comunemente utilizzati archiviandoli in una cache ad alta velocità.</span><span class="sxs-lookup"><span data-stu-id="de795-155">Accelerate access to commonly used data by storing it in a high-speed cache.</span></span>
    
- <span data-ttu-id="de795-156">Collaborare con i membri del team</span><span class="sxs-lookup"><span data-stu-id="de795-156">Collaborate with team members</span></span>
    
    <span data-ttu-id="de795-157">Concedere a più utenti l'autorizzazione per accedere ai dati nello spazio di archiviazione cloud.</span><span class="sxs-lookup"><span data-stu-id="de795-157">Grant permission to multiple users to allow access to data in cloud storage.</span></span>
    
- <span data-ttu-id="de795-158">Gestire i dati</span><span class="sxs-lookup"><span data-stu-id="de795-158">Manage data</span></span>
    
    <span data-ttu-id="de795-159">Archiviare, spostare o eliminare i dati in blocco interni o esterni.</span><span class="sxs-lookup"><span data-stu-id="de795-159">Store, move, or delete internal or external bulk data.</span></span>
    
- <span data-ttu-id="de795-160">Gestire il codice sorgente</span><span class="sxs-lookup"><span data-stu-id="de795-160">Manage source code</span></span>
    
    <span data-ttu-id="de795-161">Caricare, collaborare ed eseguire i file di codice dell'applicazione nel cloud.</span><span class="sxs-lookup"><span data-stu-id="de795-161">Upload, collaborate, and run application code files in the cloud.</span></span>
    
- <span data-ttu-id="de795-162">File di backup</span><span class="sxs-lookup"><span data-stu-id="de795-162">Backup files</span></span>
    
    <span data-ttu-id="de795-163">Archiviare le copie dei dati interne o esterne in un altro luogo in più posizioni cloud.</span><span class="sxs-lookup"><span data-stu-id="de795-163">Store copies of internal or external data offsite in multiple cloud locations.</span></span>
    
- <span data-ttu-id="de795-164">Pubblicare le comunicazioni aziendali</span><span class="sxs-lookup"><span data-stu-id="de795-164">Publish company communications</span></span>
    
    <span data-ttu-id="de795-165">Creare un singolo punto di pubblicazione per i messaggi interni o esterni.</span><span class="sxs-lookup"><span data-stu-id="de795-165">Create a single point of publication for internal or external messages.</span></span>
    
- <span data-ttu-id="de795-166">Distribuire milioni di eventi</span><span class="sxs-lookup"><span data-stu-id="de795-166">Distribute millions of events</span></span>
    
    <span data-ttu-id="de795-167">Creare spazio di archiviazione per l'acquisizione di telemetria da siti Web, app e dispositivi.</span><span class="sxs-lookup"><span data-stu-id="de795-167">Create storage for telemetry ingestion from websites, apps, and devices.</span></span>
    
- <span data-ttu-id="de795-168">Gestire/usare i video</span><span class="sxs-lookup"><span data-stu-id="de795-168">Manage/serve videos</span></span>
    
    <span data-ttu-id="de795-169">Archiviare e usare il contenuto video per i clienti o gli utenti dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="de795-169">Store and serve video content to customers or organization users.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="de795-170">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="de795-170">Next step</span></span>

<span data-ttu-id="de795-171">Rivedere le opzioni di archiviazione cloud di [Pronto per l'utilizzo](move-in-ready.md).</span><span class="sxs-lookup"><span data-stu-id="de795-171">Review the [Move-in ready](move-in-ready.md) cloud storage options.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="de795-172">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="de795-172">See Also</span></span>

[<span data-ttu-id="de795-173">Archiviazione cloud Microsoft per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="de795-173">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="de795-174">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="de795-174">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="de795-175">Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT</span><span class="sxs-lookup"><span data-stu-id="de795-175">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


