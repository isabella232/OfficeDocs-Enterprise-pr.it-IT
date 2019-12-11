---
title: Usare la rete per la distribuzione di contenuti di Office 365 con SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: In questo articolo viene descritto come utilizzare la rete di distribuzione del contenuto (CDN) di Office 365 per velocizzare il recapito delle risorse di SharePoint Online a tutti gli utenti, indipendentemente dal luogo in cui si trovano o dal modo in cui accedono al contenuto.
ms.openlocfilehash: de4982047e7a92d7df477128274e0037fbc86d42
ms.sourcegitcommit: 77b8fd702d3a1010d3906d4024d272ad2097f54f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2019
ms.locfileid: "39962483"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a><span data-ttu-id="ed7f6-103">Usare la rete per la distribuzione di contenuti di Office 365 con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ed7f6-103">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>

<span data-ttu-id="ed7f6-104">È possibile usare la rete per la distribuzione di contenuti di Office 365 predefinita per ospitare risorse statiche e migliorare le prestazioni delle pagine di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-104">You can use the built-in Office 365 Content Delivery Network (CDN) to host static assets to provide better performance for your SharePoint Online pages.</span></span> <span data-ttu-id="ed7f6-105">La rete per la distribuzione di contenuti di Office 365 consente di migliorare le prestazioni in quanto le risorse statiche vengono memorizzate nella cache più vicina ai browser che le richiedono. Questo consente di velocizzare i download e ridurre la latenza.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-105">The Office 365 CDN improves performance by caching static assets closer to the browsers requesting them, which helps to speed up downloads and reduce latency.</span></span> <span data-ttu-id="ed7f6-106">Inoltre, la rete CDN di Office 365 utilizza il [protocollo http/2](https://en.wikipedia.org/wiki/HTTP/2) per migliorare la compressione e il pipelining HTTP.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-106">Also, the Office 365 CDN uses the [HTTP/2 protocol](https://en.wikipedia.org/wiki/HTTP/2) for improved compression and HTTP pipelining.</span></span> <span data-ttu-id="ed7f6-107">Il servizio della rete per la distribuzione di contenuti di Office 365 è incluso nell'abbonamento a SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-107">The Office 365 CDN service is included as part of your SharePoint Online subscription.</span></span>

> [!NOTE]
> <span data-ttu-id="ed7f6-108">La rete CDN di Office 365 è disponibile solo per i tenant nel cloud di **produzione** (tutto il mondo).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-108">The Office 365 CDN is only available to tenants in the **Production** (worldwide) cloud.</span></span> <span data-ttu-id="ed7f6-109">Gli inquilini del governo degli Stati Uniti, le nuvole cinesi e tedesche attualmente non supportano la rete CDN di Office 365.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-109">Tenants in the US Government, China and Germany clouds do not currently support the Office 365 CDN.</span></span>

<span data-ttu-id="ed7f6-110">La rete per la distribuzione di contenuti di Office 365 è costituita da diverse reti per la distribuzione di contenuti che consentono di ospitare le risorse statiche in più località o _origini_ e gestirle da reti globali ad alta velocità.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-110">The Office 365 CDN is composed of multiple CDNs that allow you to host static assets in multiple locations, or _origins_, and serve them from global high-speed networks.</span></span> <span data-ttu-id="ed7f6-111">In base al tipo di contenuto che si vuole ospitare nella rete per la distribuzione di contenuti di Office 365, è possibile aggiungere origini **pubbliche**, origini **private** o entrambi.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-111">Depending on the kind of content you want to host in the Office 365 CDN, you can add **public** origins, **private** origins or both.</span></span> <span data-ttu-id="ed7f6-112">Per ulteriori informazioni sulla differenza tra origini pubbliche e private, vedere [scegliere se ogni origine deve essere pubblica o privata](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) .</span><span class="sxs-lookup"><span data-stu-id="ed7f6-112">See [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) for more information on the difference between public and private origins.</span></span>

<span data-ttu-id="ed7f6-113">![Diagramma concettuale della rete CDN di Office 365](media/O365-CDN/o365-cdn-flow-transparent.svg "Diagramma concettuale della rete CDN di Office 365")</span><span class="sxs-lookup"><span data-stu-id="ed7f6-113">![Office 365 CDN conceptual diagram](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN conceptual diagram")</span></span>

<span data-ttu-id="ed7f6-114">Se si ha già familiarità con la modalità di funzionamento di reti CDN, è necessario completare solo alcuni passaggi per abilitare la rete CDN di Office 365 per il tenant.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-114">If you are already familiar with the way that CDNs work, you only need to complete a few steps to enable the Office 365 CDN for your tenant.</span></span> <span data-ttu-id="ed7f6-115">In questo argomento viene descritto come.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-115">This topic describes how.</span></span> <span data-ttu-id="ed7f6-116">Leggere per informazioni su come iniziare a ospitare le risorse statiche.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-116">Read on for information about how to get started hosting your static assets.</span></span>

> [!TIP]
> <span data-ttu-id="ed7f6-117">Sono disponibili altri reti CDN ospitati da Microsoft che possono essere utilizzati con Office 365 per scenari di utilizzo specializzati, ma non sono descritti in questo argomento perché non rientrano nell'ambito della rete CDN di Office 365.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-117">There are other Microsoft-hosted CDNs that can be used with Office 365 for specialized usage scenarios, but are not discussed in this topic because they fall outside the scope of the Office 365 CDN.</span></span> <span data-ttu-id="ed7f6-118">Per ulteriori informazioni, vedere [other Microsoft reti CDN](content-delivery-networks.md#other-microsoft-cdns).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-118">For more information, see [Other Microsoft CDNs](content-delivery-networks.md#other-microsoft-cdns).</span></span>

 <span data-ttu-id="ed7f6-119">**Tornare a [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune).**</span><span class="sxs-lookup"><span data-stu-id="ed7f6-119">**Head back to [Network planning and performance tuning for Office 365](https://aka.ms/tune).**</span></span>

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a><span data-ttu-id="ed7f6-120">Panoramica dell'utilizzo della rete CDN di Office 365 in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ed7f6-120">Overview of working with the Office 365 CDN in SharePoint Online</span></span>

<span data-ttu-id="ed7f6-121">Per configurare la rete CDN di Office 365 per l'organizzazione, attenersi alla procedura di base riportata di seguito:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-121">To set up the Office 365 CDN for your organization, you follow these basic steps:</span></span>

+ [<span data-ttu-id="ed7f6-122">Pianificare la distribuzione della rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-122">Plan for deployment of the Office 365 CDN</span></span>](use-office-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  + <span data-ttu-id="ed7f6-123">[Determinare quali risorse statiche si desidera ospitare sulla rete CDN](use-office-365-cdn-with-spo.md#CDNAssets).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-123">[Determine which static assets you want to host on the CDN](use-office-365-cdn-with-spo.md#CDNAssets).</span></span>
  + <span data-ttu-id="ed7f6-124">[Determinare la posizione in cui si desidera archiviare i cespiti](use-office-365-cdn-with-spo.md#CDNStoreAssets).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-124">[Determine where you want to store your assets](use-office-365-cdn-with-spo.md#CDNStoreAssets).</span></span> <span data-ttu-id="ed7f6-125">Questo percorso può essere un sito, una raccolta o una cartella di SharePoint ed è denominato _origine_.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-125">This location can be a SharePoint site, library or folder and is called an _origin_.</span></span>
  + <span data-ttu-id="ed7f6-126">[Scegliere se ogni origine deve essere pubblica o privata](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-126">[Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span></span> <span data-ttu-id="ed7f6-127">È possibile aggiungere origini multiple di tipi pubblici e privati.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-127">You can add multiple origins of both public and private types.</span></span>

+ <span data-ttu-id="ed7f6-128">Impostare e configurare la rete CDN, utilizzando PowerShell o la CLI di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ed7f6-128">Set up and configure the CDN, using either PowerShell or the SharePoint Online CLI</span></span>

  + [<span data-ttu-id="ed7f6-129">Impostare e configurare la rete CDN tramite SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="ed7f6-129">Set up and configure the CDN by using the SharePoint Online Management Shell</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinPShell)
  + [<span data-ttu-id="ed7f6-130">Impostare e configurare la rete CDN tramite la CLI di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-130">Set up and configure the CDN by using the Office 365 CLI</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinCLI)

  <span data-ttu-id="ed7f6-131">Al termine di questo passaggio, si avranno le seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-131">When you complete this step, you will have:</span></span>

  + <span data-ttu-id="ed7f6-132">Abilitato la rete CDN per la propria organizzazione.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-132">Enabled the CDN for your organization.</span></span>
  + <span data-ttu-id="ed7f6-133">Sono state aggiunte le origini, identificando ogni origine come pubblico o privato.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-133">Added your origins, identifying each origin as public or private.</span></span>

<span data-ttu-id="ed7f6-134">Dopo aver completato l'installazione, è possibile [gestire la rete CDN di Office 365](use-office-365-cdn-with-spo.md#CDNManage) nel tempo:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-134">Once you're done with setup, you can [Manage the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) over time by:</span></span>
  
+ <span data-ttu-id="ed7f6-135">Aggiunta, aggiornamento e rimozione di risorse</span><span class="sxs-lookup"><span data-stu-id="ed7f6-135">Adding, updating, and removing assets</span></span>
+ <span data-ttu-id="ed7f6-136">Aggiunta e rimozione di origini</span><span class="sxs-lookup"><span data-stu-id="ed7f6-136">Adding and removing origins</span></span>
+ <span data-ttu-id="ed7f6-137">Configurazione di criteri CDN</span><span class="sxs-lookup"><span data-stu-id="ed7f6-137">Configuring CDN policies</span></span>
+ <span data-ttu-id="ed7f6-138">Se necessario, disabilitando la rete CDN</span><span class="sxs-lookup"><span data-stu-id="ed7f6-138">If necessary, disabling the CDN</span></span>

<span data-ttu-id="ed7f6-139">Infine, vedere [utilizzo delle risorse](use-office-365-cdn-with-spo.md#using-your-cdn-assets) della rete CDN per informazioni sull'accesso alle risorse della rete CDN sia dall'origine pubblica che da quella privata.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-139">Finally, see [Using your CDN assets](use-office-365-cdn-with-spo.md#using-your-cdn-assets) to learn about accessing your CDN assets from both public and private origins.</span></span>

<span data-ttu-id="ed7f6-140">Consultare [risoluzione dei problemi relativi alla rete CDN di Office 365](use-office-365-cdn-with-spo.md#CDNTroubleshooting) per indicazioni sulla risoluzione di problemi comuni.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-140">See [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) for guidance on resolving common issues.</span></span>

## <a name="plan-for-deployment-of-the-office-365-cdn"></a><span data-ttu-id="ed7f6-141">Pianificare la distribuzione della rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-141">Plan for deployment of the Office 365 CDN</span></span>

<span data-ttu-id="ed7f6-142">Prima di distribuire la rete CDN di Office 365 per il tenant di Office 365, è necessario tenere in considerazione i fattori seguenti nell'ambito del processo di pianificazione.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-142">Before you deploy the Office 365 CDN for your Office 365 tenant, you should consider the following factors as part of your planning process.</span></span>

  + [<span data-ttu-id="ed7f6-143">Determinare quali risorse statiche si desidera ospitare nella rete CDN</span><span class="sxs-lookup"><span data-stu-id="ed7f6-143">Determine which static assets you want to host on the CDN</span></span>](use-office-365-cdn-with-spo.md#CDNAssets)
  + [<span data-ttu-id="ed7f6-144">Determinare la posizione in cui si desidera archiviare le risorse</span><span class="sxs-lookup"><span data-stu-id="ed7f6-144">Determine where you want to store your assets</span></span>](use-office-365-cdn-with-spo.md#CDNStoreAssets)
  + [<span data-ttu-id="ed7f6-145">Scegliere se ogni origine deve essere pubblica o privata</span><span class="sxs-lookup"><span data-stu-id="ed7f6-145">Choose whether each origin should be public or private</span></span>](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

<span data-ttu-id="ed7f6-146"><a name="CDNAssets"> </a></span><span class="sxs-lookup"><span data-stu-id="ed7f6-146"></span></span>
### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a><span data-ttu-id="ed7f6-147">Determinare quali risorse statiche si desidera ospitare nella rete CDN</span><span class="sxs-lookup"><span data-stu-id="ed7f6-147">Determine which static assets you want to host on the CDN</span></span>

<span data-ttu-id="ed7f6-148">In generale, reti CDN è più efficace per ospitare _risorse statiche_o risorse che non cambiano molto spesso.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-148">In general, CDNs are most effective for hosting _static assets_, or assets that don't change very often.</span></span> <span data-ttu-id="ed7f6-149">Una buona regola empirica consiste nell'identificare i file che soddisfano alcune o tutte queste condizioni:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-149">A good rule of thumb is to identify files that meet some or all of these conditions:</span></span>

+ <span data-ttu-id="ed7f6-150">File statici incorporati in una pagina (come script e immagini) che potrebbero avere un impatto incrementale significativo sui tempi di caricamento delle pagine</span><span class="sxs-lookup"><span data-stu-id="ed7f6-150">Static files embedded in a page (like scripts and images) that may have a significant incremental impact on page load times</span></span>
+ <span data-ttu-id="ed7f6-151">File di grandi dimensioni come eseguibili e file di installazione</span><span class="sxs-lookup"><span data-stu-id="ed7f6-151">Large files like executables and installation files</span></span>
+ <span data-ttu-id="ed7f6-152">Raccolte di risorse che supportano il codice sul retro del client</span><span class="sxs-lookup"><span data-stu-id="ed7f6-152">Resource libraries that support client-side code</span></span>

<span data-ttu-id="ed7f6-153">Ad esempio, i file di piccole dimensioni ripetutamente richiesti come le immagini e gli script del sito possono migliorare significativamente le prestazioni di rendering dei siti e ridurre in modo incrementale il carico nei siti di SharePoint Online quando vengono aggiunti a un'origine CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-153">For example, small files that are repeatedly requested like site images and scripts can significantly improve site rendering performance and incrementally reduce the load on your SharePoint Online sites when you add them to a CDN origin.</span></span> <span data-ttu-id="ed7f6-154">I file di grandi dimensioni, ad esempio gli eseguibili di installazione, possono essere scaricati dalla rete CDN, garantendo un impatto positivo sulle prestazioni e una conseguente riduzione del carico sul sito di SharePoint Online, anche se non è possibile accedervi con la frequenza.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-154">Larger files such as installation executables can be downloaded from the CDN, delivering a positive performance impact and subsequent reduction of the load on your SharePoint Online site, even if they are not accessed as often.</span></span>

<span data-ttu-id="ed7f6-155">Il miglioramento delle prestazioni in base ai file dipende da molti fattori, tra cui la vicinanza del client all'endpoint CDN più vicino, le condizioni transitorie sulla rete locale e così via.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-155">Performance improvement on a per-file basis is dependent on many factors, including the client's proximity to the nearest CDN endpoint, transient conditions on the local network, and so forth.</span></span> <span data-ttu-id="ed7f6-156">Molti file statici sono piuttosto ridotti e possono essere scaricati da Office 365 in meno di un secondo.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-156">Many static files are quite small, and can be downloaded from Office 365 in less than a second.</span></span> <span data-ttu-id="ed7f6-157">Tuttavia, una pagina Web può contenere molti file incorporati con un tempo di download cumulativo di alcuni secondi.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-157">However, a web page may contain many embedded files with a cumulative download time of several seconds.</span></span> <span data-ttu-id="ed7f6-158">La gestione di questi file dalla rete CDN può ridurre significativamente il tempo complessivo di caricamento delle pagine.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-158">Serving these files from the CDN can significantly reduce the overall page load time.</span></span> <span data-ttu-id="ed7f6-159">Per un esempio, vedere [quali guadagni di prestazioni fornisce una rete CDN?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide)</span><span class="sxs-lookup"><span data-stu-id="ed7f6-159">See [What performance gains does a CDN provide?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) for an example.</span></span>

<span data-ttu-id="ed7f6-160"><a name="CDNStoreAssets"> </a></span><span class="sxs-lookup"><span data-stu-id="ed7f6-160"></span></span>
### <a name="determine-where-you-want-to-store-your-assets"></a><span data-ttu-id="ed7f6-161">Determinare la posizione in cui si desidera archiviare le risorse</span><span class="sxs-lookup"><span data-stu-id="ed7f6-161">Determine where you want to store your assets</span></span>

<span data-ttu-id="ed7f6-162">La rete CDN recupera le risorse da una posizione denominata _Origin_.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-162">The CDN fetches your assets from a location called an _origin_.</span></span> <span data-ttu-id="ed7f6-163">Un'origine può essere un sito di SharePoint, una raccolta documenti o una cartella accessibile da un URL.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-163">An origin can be a SharePoint site, document library or folder that is accessible by a URL.</span></span> <span data-ttu-id="ed7f6-164">Si dispone di una grande flessibilità quando si specificano le origini per l'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-164">You have great flexibility when you specify origins for your organization.</span></span> <span data-ttu-id="ed7f6-165">Ad esempio, è possibile specificare più origini o una singola origine in cui si desidera inserire tutte le risorse della rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-165">For example, you can specify multiple origins or a single origin where you want to put all your CDN assets.</span></span> <span data-ttu-id="ed7f6-166">È possibile scegliere di avere origini sia pubbliche che private per la propria organizzazione.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-166">You can choose to have both public or private origins for your organization.</span></span> <span data-ttu-id="ed7f6-167">La maggior parte delle organizzazioni sceglie di implementare una combinazione dei due.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-167">Most organizations will choose to implement a combination of the two.</span></span>

<span data-ttu-id="ed7f6-168">È possibile creare un nuovo contenitore per le origini, ad esempio le cartelle o le raccolte documenti, e aggiungere i file che si desidera rendere disponibili dalla rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-168">You can create new container for your origins such as folders or document libraries, and add files you want to make available from the CDN.</span></span> <span data-ttu-id="ed7f6-169">Questo è un buon approccio se si dispone di un insieme specifico di risorse che si desidera rendere disponibili dalla rete CDN e si desidera limitare il set di risorse della rete CDN solo ai file presenti nel contenitore.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-169">This is a good approach if you have a specific set of assets you want to be available from the CDN, and want to restrict the set of CDN assets to only those files in the container.</span></span>

<span data-ttu-id="ed7f6-170">È inoltre possibile configurare una raccolta siti, un sito, una raccolta o una cartella esistente come origine, in modo da rendere tutte le risorse idonee nel contenitore disponibili dalla rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-170">You can also configure an existing site collection, site, library or folder as an origin, which will make all eligible assets in the container available from the CDN.</span></span> <span data-ttu-id="ed7f6-171">Prima di aggiungere un contenitore esistente come origine, è importante assicurarsi di essere a conoscenza del contenuto e delle autorizzazioni in modo da non esporre inavvertitamente le risorse all'accesso anonimo o agli utenti non autorizzati.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-171">Before you add an existing container as an origin, it's important to make sure you are aware of its contents and permissions so you do not inadvertently expose assets to anonymous access or unauthorized users.</span></span>

<span data-ttu-id="ed7f6-172">È possibile definire i criteri della rete _CDN_ per escludere il contenuto nelle origini dalla rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-172">You can define _CDN policies_ to exclude content in your origins from the CDN.</span></span> <span data-ttu-id="ed7f6-173">I criteri della rete CDN escludono le risorse in origine pubblica o privata per attributi quali _tipo di file_ e _classificazione dei siti_e vengono applicati a tutte le origini del CdnType (privato o pubblico) specificato nel criterio.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-173">CDN policies exclude assets in public or private origins by attributes such as _file type_ and _site classification_, and are applied to all origins of the CdnType (private or public) you specify in the policy.</span></span> <span data-ttu-id="ed7f6-174">Ad esempio, se si aggiunge un'origine privata costituita da un sito contenente più siti secondari, è possibile definire un criterio per escludere i siti contrassegnati come **riservati** in modo che il contenuto proveniente da siti con tale classificazione applicato non venga utilizzato dalla rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-174">For example, if you add a private origin consisting of a site that contains multiple subsites, you can define a policy to exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span> <span data-ttu-id="ed7f6-175">Il criterio si applica ai contenuti di _tutte_ le origini private che sono state aggiunte alla rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-175">The policy will apply to content from _all_ private origins you have added to the CDN.</span></span>
  
<span data-ttu-id="ed7f6-176">Tenere presente che maggiore è il numero di origini, maggiore è l'impatto sul tempo impiegato dal servizio CDN per l'elaborazione delle richieste.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-176">Keep in mind that the greater the number of origins, the greater the impact on the time it takes the CDN service to process requests.</span></span> <span data-ttu-id="ed7f6-177">Si consiglia di limitare il più possibile il numero di origini.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-177">We recommend that you limit the number of origins as much as possible.</span></span>
  
<span data-ttu-id="ed7f6-178"><a name="CDNOriginChoosePublicPrivate"> </a></span><span class="sxs-lookup"><span data-stu-id="ed7f6-178"></span></span>
### <a name="choose-whether-each-origin-should-be-public-or-private"></a><span data-ttu-id="ed7f6-179">Scegliere se ogni origine deve essere pubblica o privata</span><span class="sxs-lookup"><span data-stu-id="ed7f6-179">Choose whether each origin should be public or private</span></span>

<span data-ttu-id="ed7f6-180">Quando si identifica un'origine, è necessario specificare se deve essere reso _pubblico_ o _privato_.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-180">When you identify an origin, you specify whether it should be made _public_ or _private_.</span></span> <span data-ttu-id="ed7f6-181">L'accesso alle risorse della rete CDN nelle origini pubbliche è anonimo e il contenuto della rete CDN in origine privata è protetto da token generati dinamicamente per una maggiore sicurezza.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-181">Access to CDN assets in public origins is anonymous, and CDN content in private origins is secured by dynamically generated tokens for greater security.</span></span> <span data-ttu-id="ed7f6-182">Indipendentemente dall'opzione scelta, Microsoft esegue tutte le operazioni di sollevamento dei carichi pesanti quando si tratta di amministrazione della rete CDN stessa.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-182">Regardless of which option you choose, Microsoft does all the heavy lifting for you when it comes to administration of the CDN itself.</span></span> <span data-ttu-id="ed7f6-183">Inoltre, è possibile modificare la propria mente in un secondo momento, dopo aver configurato la rete CDN e aver individuato le origini.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-183">Also, you can change your mind later, after you've set up the CDN and identified your origins.</span></span>

<span data-ttu-id="ed7f6-184">Entrambe le opzioni pubblico e privato offrono guadagni di prestazioni simili, ma ognuno ha attributi e vantaggi univoci.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-184">Both public and private options provide similar performance gains, but each has unique attributes and advantages.</span></span>

<span data-ttu-id="ed7f6-185">Le origini **pubbliche** all'interno della rete CDN di Office 365 sono accessibili in modo anonimo e le risorse ospitate possono essere accessibili da tutti gli utenti che hanno l'URL del cespite.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-185">**Public** origins within the Office 365 CDN are accessible anonymously, and hosted assets can be accessed by anyone who has the URL to the asset.</span></span> <span data-ttu-id="ed7f6-186">Dal momento che l'accesso al contenuto in origini pubbliche è anonimo, è consigliabile usarle solo per memorizzare nella cache contenuti generici non riservati, ad esempio file JavaScript, script, icone e immagini.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-186">Because access to content in public origins is anonymous, you should only use them to cache non-sensitive generic content such as javascript files, scripts, icons and images.</span></span>

<span data-ttu-id="ed7f6-187">Le origini **private** all'interno della rete CDN di Office 365 offrono accesso privato ai contenuti degli utenti, ad esempio raccolte documenti di SharePoint Online, siti e immagini proprietarie.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-187">**Private** origins within the Office 365 CDN provide private access to user content such as SharePoint Online document libraries, sites and proprietary images.</span></span> <span data-ttu-id="ed7f6-188">L'accesso al contenuto in origini private è protetto da token generati dinamicamente, in modo che sia possibile accedervi solo dagli utenti che dispongono delle autorizzazioni per la raccolta documenti originale o il percorso di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-188">Access to content in private origins is secured by dynamically generated tokens so it can only be accessed by users with permissions to the original document library or storage location.</span></span> <span data-ttu-id="ed7f6-189">L'origine privata nella rete CDN di Office 365 può essere utilizzata solo per il contenuto di SharePoint Online ed è possibile accedere solo alle risorse in origine privata tramite il reindirizzamento dal tenant di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-189">Private origins in the Office 365 CDN can only be used for SharePoint Online content, and you can only access assets in private origins through redirection from your SharePoint Online tenant.</span></span>

<span data-ttu-id="ed7f6-190">Per ulteriori informazioni, vedere come l'accesso della rete CDN ai cespiti in un'origine privata funziona [utilizzando risorse in origine privata](use-office-365-cdn-with-spo.md#using-assets-in-private-origins).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-190">You can read more about how CDN access to assets in a private origin works in [Using assets in private origins](use-office-365-cdn-with-spo.md#using-assets-in-private-origins).</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a><span data-ttu-id="ed7f6-191">Attributi e vantaggi dell'hosting di risorse in origini pubbliche</span><span class="sxs-lookup"><span data-stu-id="ed7f6-191">Attributes and advantages of hosting assets in public origins</span></span>
  
+ <span data-ttu-id="ed7f6-192">Le risorse esposte in un'origine pubblica sono accessibili da tutti in modo anonimo.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-192">Assets exposed in a public origin are accessible by everyone anonymously.</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="ed7f6-193">Non è consigliabile inserire mai risorse che contengono informazioni sugli utenti o che sono considerate sensibili all'organizzazione in un'origine pubblica.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-193">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>
+ <span data-ttu-id="ed7f6-194">Se si rimuove una risorsa da un'origine pubblica, il cespite potrebbe continuare a essere disponibile per un massimo di 30 giorni dalla cache. Tuttavia, verranno invalidati i collegamenti al cespite nella rete CDN entro 15 minuti.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-194">If you remove an asset from a public origin, the asset may continue to be available for up to 30 days from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
+ <span data-ttu-id="ed7f6-195">Quando si ospitano fogli di stile (file CSS) in un'origine pubblica, è possibile utilizzare i percorsi e gli URI relativi all'interno del codice.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-195">When you host style sheets (CSS files) in a public origin, you can use relative paths and URIs within the code.</span></span> <span data-ttu-id="ed7f6-196">Questo significa che è possibile fare riferimento alla posizione delle immagini di sfondo e di altri oggetti rispetto alla posizione del cespite che lo chiama.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-196">This means that you can reference the location of background images and other objects relative to the location of the asset that's calling it.</span></span>
+ <span data-ttu-id="ed7f6-197">Anche se è possibile eseguire il codice rigido di un URL di origine pubblica, questo non è consigliato.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-197">While you can hard code a public origin's URL, doing so is not recommended.</span></span> <span data-ttu-id="ed7f6-198">Il motivo è che se l'accesso alla rete CDN non è disponibile, l'URL non si risolverà automaticamente nell'organizzazione in SharePoint Online e potrebbe causare collegamenti interrotti e altri errori.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-198">The reason for this is that if access to the CDN becomes unavailable, the URL will not automatically resolve to your organization in SharePoint Online and might result in broken links and other errors.</span></span>
+ <span data-ttu-id="ed7f6-199">I tipi di file predefiniti inclusi per le origini pubbliche sono. CSS,. EOT,. gif,. ico,. jpeg,. jpg,. js,. map,. png,. svg,. ttf e. WOFF.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-199">The default file types that are included for public origins are .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff.</span></span> <span data-ttu-id="ed7f6-200">È possibile specificare ulteriori tipi di file.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-200">You can specify additional file types.</span></span>
+ <span data-ttu-id="ed7f6-201">È possibile configurare un criterio per escludere le risorse che sono state identificate dalle classificazioni dei siti specificate.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-201">You can configure a policy to exclude assets that have been identified by site classifications that you specify.</span></span> <span data-ttu-id="ed7f6-202">Ad esempio, è possibile scegliere di escludere tutte le risorse contrassegnate come "riservate" o "limitate" anche se si tratta di un tipo di file consentito e che si trovano in un'origine pubblica.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-202">For example, you can choose to exclude all assets that are marked as "confidential" or "restricted" even if they are an allowed file type and are located in a public origin.</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a><span data-ttu-id="ed7f6-203">Attributi e vantaggi dell'hosting di risorse in origini private</span><span class="sxs-lookup"><span data-stu-id="ed7f6-203">Attributes and advantages of hosting assets in private origins</span></span>

+ <span data-ttu-id="ed7f6-204">L'origine privata può essere utilizzata solo per le risorse di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-204">Private origins can only be used for SharePoint Online assets.</span></span>
+ <span data-ttu-id="ed7f6-205">Gli utenti possono accedere alle risorse solo da un'origine privata se dispongono delle autorizzazioni per accedere al contenitore.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-205">Users can only access the assets from a private origin if they have permissions to access the container.</span></span> <span data-ttu-id="ed7f6-206">L'accesso anonimo a tali risorse è impedito.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-206">Anonymous access to these assets is prevented.</span></span>
+ <span data-ttu-id="ed7f6-207">Le risorse in origine privata devono essere denominate dal tenant di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-207">Assets in private origins must be referred from the SharePoint Online tenant.</span></span> <span data-ttu-id="ed7f6-208">L'accesso diretto alle risorse della rete CDN privata non funziona.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-208">Direct access to private CDN assets does not work.</span></span>
+ <span data-ttu-id="ed7f6-209">Se si rimuove una risorsa dall'origine privata, il bene può continuare a essere disponibile per un massimo di un'ora dalla cache; Tuttavia, verranno invalidati i collegamenti al cespite nella rete CDN entro 15 minuti dalla rimozione del cespite.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-209">If you remove an asset from the private origin, the asset may continue to be available for up to an hour from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes of the asset's removal.</span></span>
+ <span data-ttu-id="ed7f6-210">I tipi di file predefiniti inclusi per le origini private sono. gif,. ico,. jpeg,. jpg,. js e. png.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-210">The default file types that are included for private origins are .gif, .ico, .jpeg, .jpg, .js, and .png.</span></span> <span data-ttu-id="ed7f6-211">È possibile specificare ulteriori tipi di file.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-211">You can specify additional file types.</span></span>
+ <span data-ttu-id="ed7f6-212">Analogamente alle origini pubbliche, è possibile configurare un criterio per escludere le risorse che sono state identificate dalle classificazioni dei siti specificate anche se si utilizzano caratteri jolly per includere tutte le risorse all'interno di una cartella o di una raccolta documenti.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-212">Just like with public origins, you can configure a policy to exclude assets that have been identified by site classifications that you specify even if you use wildcards to include all assets within a folder or document library.</span></span>

<span data-ttu-id="ed7f6-213">Per ulteriori informazioni sui motivi per utilizzare la rete CDN di Office 365, i concetti generali di CDN e altre reti CDN di Microsoft che è possibile utilizzare con il tenant di Office 365, vedere [Content Delivery Networks](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-213">For more information about why to use the Office 365 CDN, general CDN concepts, and other Microsoft CDNs you can use with your Office 365 tenant, see [Content Delivery Networks](content-delivery-networks.md).</span></span>

### <a name="default-cdn-origins"></a><span data-ttu-id="ed7f6-214">Origini della rete CDN predefinite</span><span class="sxs-lookup"><span data-stu-id="ed7f6-214">Default CDN origins</span></span>

<span data-ttu-id="ed7f6-215">Se non si specifica altrimenti, Office 365 configura alcune origini predefinite quando si Abilita la rete CDN di Office 365.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-215">Unless you specify otherwise, Office 365 sets up some default origins for you when you enable the Office 365 CDN.</span></span> <span data-ttu-id="ed7f6-216">Se inizialmente si sceglie di non eseguire il provisioning, è possibile aggiungere queste origini dopo aver completato l'installazione.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-216">If you initially opt not to provision them, you can add these origins after you complete setup.</span></span> <span data-ttu-id="ed7f6-217">A meno che non si comprendano le conseguenze della possibilità di ignorare la configurazione delle origini predefinite e che si disponga di un motivo specifico, è consigliabile consentirne la creazione quando si Abilita la rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-217">Unless you understand the consequences of skipping the setup of default origins and have a specific reason for doing so, you should allow them to be created when you enable the CDN.</span></span>
  
<span data-ttu-id="ed7f6-218">Origini private CDN predefinite:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-218">Default private CDN origins:</span></span>
  
+ <span data-ttu-id="ed7f6-219">\*/userphoto.aspx</span><span class="sxs-lookup"><span data-stu-id="ed7f6-219">\*/userphoto.aspx</span></span>
+ <span data-ttu-id="ed7f6-220">\*/siteassets</span><span class="sxs-lookup"><span data-stu-id="ed7f6-220">\*/siteassets</span></span>

<span data-ttu-id="ed7f6-221">Origini di CDN pubbliche predefinite:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-221">Default public CDN origins:</span></span>
  
+ <span data-ttu-id="ed7f6-222">\*/masterpage</span><span class="sxs-lookup"><span data-stu-id="ed7f6-222">\*/masterpage</span></span>
+ <span data-ttu-id="ed7f6-223">\*raccolta/Style</span><span class="sxs-lookup"><span data-stu-id="ed7f6-223">\*/style library</span></span>
+ <span data-ttu-id="ed7f6-224">\*/clientsideassets</span><span class="sxs-lookup"><span data-stu-id="ed7f6-224">\*/clientsideassets</span></span>

> [!NOTE]
> <span data-ttu-id="ed7f6-225">_clientsideassets_ è un'origine pubblica predefinita aggiunta al servizio CDN di Office 365 nel dicembre 2017.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-225">_clientsideassets_ is a default public origin that was added to the Office 365 CDN service in December 2017.</span></span> <span data-ttu-id="ed7f6-226">Questa origine deve essere presente nell'ordine in cui le soluzioni di SharePoint Framework nella rete CDN funzionino.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-226">This origin must be present in order for SharePoint Framework solutions in the CDN to work.</span></span> <span data-ttu-id="ed7f6-227">Se è stata abilitata la rete CDN di Office 365 prima del dicembre 2017 o se è stata ignorata la configurazione delle origini predefinite quando è stata abilitata la rete CDN, è possibile aggiungere manualmente questa origine.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-227">If you enabled the Office 365 CDN prior to December 2017, or if you skipped setup of default origins when you enabled the CDN, you can manually add this origin.</span></span> <span data-ttu-id="ed7f6-228">Per ulteriori informazioni, vedere [la Web part sul lato client o la soluzione di SharePoint Framework non funziona](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-228">For more information, see [My client-side web part or SharePoint Framework solution isn't working](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).</span></span>

<span data-ttu-id="ed7f6-229"><a name="CDNSetupinPShell"> </a></span><span class="sxs-lookup"><span data-stu-id="ed7f6-229"></span></span>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a><span data-ttu-id="ed7f6-230">Impostare e configurare la rete CDN di Office 365 tramite SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="ed7f6-230">Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell</span></span>

<span data-ttu-id="ed7f6-231">Le procedure descritte in questa sezione richiedono l'utilizzo di SharePoint Online Management Shell per la connessione a SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-231">The procedures in this section require you to use the SharePoint Online Management Shell to connect to SharePoint Online.</span></span> <span data-ttu-id="ed7f6-232">Per istruzioni, vedere [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-232">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

<span data-ttu-id="ed7f6-233">Completare questa procedura per impostare e configurare la rete CDN per ospitare le risorse in SharePoint Online tramite SharePoint Online Management Shell.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-233">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the SharePoint Online Management Shell.</span></span>

<details>
  <summary><span data-ttu-id="ed7f6-234">Fare clic per espandere</span><span class="sxs-lookup"><span data-stu-id="ed7f6-234">Click to expand</span></span></summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a><span data-ttu-id="ed7f6-235">Abilitazione dell'organizzazione all'utilizzo della rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-235">Enable your organization to use the Office 365 CDN</span></span>

<span data-ttu-id="ed7f6-236">Prima di apportare modifiche alle impostazioni della rete CDN del tenant, è necessario recuperare lo stato corrente della configurazione della rete CDN privata nel tenant di Office 365.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-236">Before you make changes to the tenant CDN settings, you should retrieve the current status of the private CDN configuration in your Office 365 tenant.</span></span> <span data-ttu-id="ed7f6-237">Connettersi al tenant tramite SharePoint Online Management Shell:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-237">Connect to your tenant using the SharePoint Online Management Shell:</span></span>

``` powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

<span data-ttu-id="ed7f6-238">A questo punto, utilizzare il cmdlet **Get-SPOTenantCdnEnabled** per recuperare le impostazioni di stato della rete CDN dal tenant:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-238">Now use the **Get-SPOTenantCdnEnabled** cmdlet to retrieve the CDN status settings from the tenant:</span></span>

``` powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

<span data-ttu-id="ed7f6-239">Lo stato della rete CDN per l'oggetto CdnType specificato verrà restituito allo schermo.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-239">The status of the CDN for the specified CdnType will output to the screen.</span></span>

<span data-ttu-id="ed7f6-240">Utilizzare il cmdlet **set-SPOTenantCdnEnabled** per consentire all'organizzazione di utilizzare la rete CDN di Office 365.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-240">Use the **Set-SPOTenantCdnEnabled** cmdlet to enable your organization to use the Office 365 CDN.</span></span> <span data-ttu-id="ed7f6-241">È possibile consentire all'organizzazione di utilizzare origini pubbliche, origini private o entrambe contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-241">You can enable your organization to use public origins, private origins, or both at once.</span></span> <span data-ttu-id="ed7f6-242">È inoltre possibile configurare la rete CDN per ignorare la configurazione delle origini predefinite quando viene abilitata.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-242">You can also configure the CDN to skip the setup of default origins when you enable it.</span></span> <span data-ttu-id="ed7f6-243">È sempre possibile aggiungere queste origini in un secondo momento, come descritto in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-243">You can always add these origins later as described in this topic.</span></span>
  
<span data-ttu-id="ed7f6-244">In Windows PowerShell per SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-244">In Windows Powershell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

<span data-ttu-id="ed7f6-245">Ad esempio, per consentire all'organizzazione di utilizzare origini pubbliche e private, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-245">For example, to enable your organization to use both public and private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="ed7f6-246">Per consentire all'organizzazione di utilizzare origini sia pubbliche che private, ma non impostare le origini predefinite, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-246">To enable your organization to use both public and private origins but skip setting up the default origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

<span data-ttu-id="ed7f6-247">Per informazioni sulle origini di cui è possibile eseguire il provisioning per impostazione predefinita, vedere origini della rete [CDN predefinite](use-office-365-cdn-with-spo.md#default-cdn-origins) quando si Abilita la rete CDN di Office 365 e l'impatto potenziale di ignorare la configurazione delle origini predefinite.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-247">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN, and the potential impact of skipping the setup of default origins.</span></span>

<span data-ttu-id="ed7f6-248">Per consentire all'organizzazione di utilizzare le origini pubbliche, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-248">To enable your organization to use public origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

<span data-ttu-id="ed7f6-249">Per consentire all'organizzazione di utilizzare origini private, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-249">To enable your organization to use private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

<span data-ttu-id="ed7f6-250">Per ulteriori informazioni su questo cmdlet, vedere [set-SPOTenantCdnEnabled](https://technet.microsoft.com/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-250">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/library/mt790765.aspx).</span></span>

<span data-ttu-id="ed7f6-251"><a name="Office365CDNforSPOFileType"> </a></span><span class="sxs-lookup"><span data-stu-id="ed7f6-251"></span></span>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a><span data-ttu-id="ed7f6-252">Modificare l'elenco dei tipi di file da includere nella rete CDN di Office 365 (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="ed7f6-252">Change the list of file types to include in the Office 365 CDN (Optional)</span></span>

> [!TIP]
> <span data-ttu-id="ed7f6-253">Quando si definiscono i tipi di file utilizzando il cmdlet **set-SPOTenantCdnPolicy** , si sovrascrive l'elenco attualmente definito.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-253">When you define file types by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="ed7f6-254">Se si desidera aggiungere ulteriori tipi di file all'elenco, utilizzare il cmdlet First per scoprire quali tipi di file sono già consentiti e includerli nell'elenco insieme a quelli nuovi.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-254">If you want to add additional file types to the list, use the cmdlet first to find out what file types are already allowed and include them in the list along with your new ones.</span></span>
  
<span data-ttu-id="ed7f6-255">Utilizzare il cmdlet **set-SPOTenantCdnPolicy** per definire i tipi di file statici che possono essere ospitati da origini pubbliche e private nella rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-255">Use the **Set-SPOTenantCdnPolicy** cmdlet to define static file types that can be hosted by public and private origins in the CDN.</span></span> <span data-ttu-id="ed7f6-256">Per impostazione predefinita, sono consentiti tipi di attività comuni, ad esempio CSS, gif, jpg e js.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-256">By default, common asset types are allowed, for example .css, .gif, .jpg, and .js.</span></span>

<span data-ttu-id="ed7f6-257">In Windows PowerShell per SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-257">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

<span data-ttu-id="ed7f6-258">Ad esempio, per abilitare la rete CDN per ospitare i file. CSS e. png, è necessario immettere il comando:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-258">For example, to enable the CDN to host .css and .png files, you would enter the command:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

<span data-ttu-id="ed7f6-259">Per sapere quali tipi di file sono attualmente consentiti dalla rete CDN, utilizzare il cmdlet **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="ed7f6-259">To see what file types are currently allowed by the CDN, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="ed7f6-260">Per ulteriori informazioni su questi cmdlet, vedere [set-SPOTenantCdnPolicy](https://technet.microsoft.com/library/mt800839.aspx) e [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-260">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/library/mt800838.aspx).</span></span>

<span data-ttu-id="ed7f6-261"><a name="Office365CDNforSPOSiteClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="ed7f6-261"></span></span>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a><span data-ttu-id="ed7f6-262">Modificare l'elenco di classificazioni dei siti che si desidera escludere dalla rete CDN di Office 365 (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="ed7f6-262">Change the list of site classifications you want to exclude from the Office 365 CDN (Optional)</span></span>

> [!TIP]
> <span data-ttu-id="ed7f6-263">Quando si escludono le classificazioni dei siti utilizzando il cmdlet **set-SPOTenantCdnPolicy** , si sovrascrive l'elenco attualmente definito.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-263">When you exclude site classifications by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="ed7f6-264">Se si desidera escludere altre classificazioni dei siti, utilizzare il cmdlet First per scoprire quali classificazioni sono già state escluse e quindi aggiungerle insieme a quelle nuove.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-264">If you want to exclude additional site classifications, use the cmdlet first to find out what classifications are already excluded and then add them along with your new ones.</span></span>

<span data-ttu-id="ed7f6-265">Utilizzare il cmdlet **set-SPOTenantCdnPolicy** per escludere le classificazioni dei siti che non si desidera rendere disponibili tramite la rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-265">Use the **Set-SPOTenantCdnPolicy** cmdlet to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="ed7f6-266">Per impostazione predefinita, non sono escluse le classificazioni dei siti.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-266">By default, no site classifications are excluded.</span></span>

<span data-ttu-id="ed7f6-267">In Windows PowerShell per SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-267">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

<span data-ttu-id="ed7f6-268">Per sapere quali classificazioni dei siti sono attualmente limitate, utilizzare il cmdlet **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="ed7f6-268">To see what site classifications are currently restricted, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="ed7f6-269">Le proprietà che verranno restituite sono _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ e _ExcludeIfNoScriptDisabled_.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-269">The properties that will be returned are _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ and _ExcludeIfNoScriptDisabled_.</span></span>

<span data-ttu-id="ed7f6-270">La proprietà _IncludeFileExtensions_ contiene l'elenco delle estensioni di file che verranno servite dalla rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-270">The _IncludeFileExtensions_ property contains the list of file extensions that will be served from the CDN.</span></span>

> [!NOTE]
> <span data-ttu-id="ed7f6-271">Le estensioni di file predefinite sono diverse tra pubblico e privato.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-271">The default file extensions are different between public and private.</span></span>

<span data-ttu-id="ed7f6-272">La proprietà _ExcludeRestrictedSiteClassifications_ contiene le classificazioni del sito che si desidera escludere dalla rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-272">The _ExcludeRestrictedSiteClassifications_ property contains the site classifications that you want to exclude from the CDN.</span></span> <span data-ttu-id="ed7f6-273">Ad esempio, è possibile escludere i siti contrassegnati come **riservati** in modo che il contenuto proveniente da siti con tale classificazione applicato non venga servito dalla rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-273">For example, you can exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span>

<span data-ttu-id="ed7f6-274">La proprietà _ExcludeIfNoScriptDisabled_ esclude il contenuto dalla rete CDN in base alle impostazioni degli attributi _noscript_ a livello di sito.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-274">The _ExcludeIfNoScriptDisabled_ property excludes content from the CDN based on the site-level _NoScript_ attribute settings.</span></span> <span data-ttu-id="ed7f6-275">Per impostazione predefinita, l'attributo _noscript_ è impostato su **abilitato** per i siti _moderni_ e **disabilitato** per i siti _classici_ .</span><span class="sxs-lookup"><span data-stu-id="ed7f6-275">By default, the _NoScript_ attribute is set to **Enabled** for _Modern_ sites and **Disabled** for _Classic_ sites.</span></span> <span data-ttu-id="ed7f6-276">Questo dipende dalle impostazioni del tenant.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-276">This depends on your tenant settings.</span></span>

<span data-ttu-id="ed7f6-277">Per ulteriori informazioni su questi cmdlet, vedere [set-SPOTenantCdnPolicy](https://technet.microsoft.com/library/mt800839.aspx) e [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-277">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/library/mt800838.aspx).</span></span>

<span data-ttu-id="ed7f6-278"><a name="Office365CDNforSPOOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="ed7f6-278"></span></span>
### <a name="add-an-origin-for-your-assets"></a><span data-ttu-id="ed7f6-279">Aggiungere un'origine per le risorse</span><span class="sxs-lookup"><span data-stu-id="ed7f6-279">Add an origin for your assets</span></span>

<span data-ttu-id="ed7f6-280">Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire un'origine.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-280">Use the **Add-SPOTenantCdnOrigin** cmdlet to define an origin.</span></span> <span data-ttu-id="ed7f6-281">È possibile definire origini multiple.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-281">You can define multiple origins.</span></span> <span data-ttu-id="ed7f6-282">L'origine è un URL che punta a una raccolta o a una cartella di SharePoint che contiene le risorse che si desidera ospitare dalla rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-282">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="ed7f6-283">Non è consigliabile inserire mai risorse che contengono informazioni sugli utenti o che sono considerate sensibili all'organizzazione in un'origine pubblica.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-283">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

<span data-ttu-id="ed7f6-284">Il valore di _path_ è il percorso relativo alla raccolta o alla cartella che contiene le risorse.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-284">The value of _path_ is the relative path to the library or folder that contains the assets.</span></span> <span data-ttu-id="ed7f6-285">È possibile utilizzare i caratteri jolly oltre ai percorsi relativi.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-285">You can use wildcards in addition to relative paths.</span></span> <span data-ttu-id="ed7f6-286">Origins supporta i caratteri jolly anteposti all'URL.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-286">Origins support wildcards prepended to the URL.</span></span> <span data-ttu-id="ed7f6-287">In questo modo è possibile creare origini che si estendono su più siti.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-287">This allows you to create origins that span multiple sites.</span></span> <span data-ttu-id="ed7f6-288">Ad esempio, per includere tutti i cespiti nella cartella masterpages per tutti i siti come origine pubblica all'interno della rete CDN, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-288">For example, to include all of the assets in the masterpages folder for all of your sites as a public origin within the CDN, type the following command:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ <span data-ttu-id="ed7f6-289">Il modificatore di**/** caratteri jolly \* può essere utilizzato solo all'inizio del percorso e deve corrispondere a tutti i segmenti di URL sotto l'URL specificato.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-289">The wildcard modifier \***/** can only be used at the beginning of the path, and will match all URL segments under the specified URL.</span></span>
+ <span data-ttu-id="ed7f6-290">Il percorso può puntare a una raccolta documenti, una cartella o un sito.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-290">The path can point to a document library, folder or site.</span></span> <span data-ttu-id="ed7f6-291">Ad esempio, il percorso _\*/site1_ corrisponderà a tutte le raccolte documenti del sito.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-291">For example, the path _\*/site1_ will match all the document libraries under the site.</span></span>

<span data-ttu-id="ed7f6-292">È possibile aggiungere un'origine con un percorso relativo specifico.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-292">You can add an origin with a specific relative path.</span></span> <span data-ttu-id="ed7f6-293">Non è possibile aggiungere un'origine utilizzando il percorso completo.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-293">You cannot add an origin using the full path.</span></span>

<span data-ttu-id="ed7f6-294">In questo esempio viene aggiunta un'origine privata della raccolta siteassets in un sito specifico:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-294">This example adds a private origin of the siteassets library on a specific site:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="ed7f6-295">In questo esempio viene aggiunta un'origine privata della cartella _folder1_ nella raccolta di risorse del sito dell'insieme di siti:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-295">This example adds a private origin of the _folder1_ folder in the site collection's site assets library:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

<span data-ttu-id="ed7f6-296">Se è presente uno spazio nel percorso, è possibile racchiuderlo tra virgolette doppie o sostituire lo spazio con la codifica URL %20.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-296">If there is a space in the path, you can either surround the path in double quotes or replace the space with the URL encoding %20.</span></span> <span data-ttu-id="ed7f6-297">Negli esempi riportati di seguito viene aggiunta un'origine privata della cartella _Folder 1_ nella raccolta di risorse del sito dell'insieme di siti:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-297">The following examples add a private origin of the _folder 1_ folder in the site collection's site assets library:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

<span data-ttu-id="ed7f6-298">Per ulteriori informazioni su questo comando e sulla relativa sintassi, vedere [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-298">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="ed7f6-299">In origine privata, le risorse condivise da un'origine devono avere una versione principale pubblicata prima che sia possibile accedervi dalla rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-299">In private origins, assets being shared from an origin must have a major version published before they can be accessed from the CDN.</span></span>
  
<span data-ttu-id="ed7f6-300">Dopo aver eseguito il comando, il sistema sincronizza la configurazione all'interno del datacenter.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-300">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="ed7f6-301">Questo può richiedere fino a 15 minuti.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-301">This can take up to 15 minutes.</span></span>

<span data-ttu-id="ed7f6-302"><a name="ExamplePublicOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="ed7f6-302"></span></span>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a><span data-ttu-id="ed7f6-303">Esempio: configurare un'origine pubblica per le pagine master e per la libreria di stili per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ed7f6-303">Example: Configure a public origin for your master pages and for your style library for SharePoint Online</span></span>

<span data-ttu-id="ed7f6-304">In genere, queste origini sono configurate per l'utente per impostazione predefinita quando si Abilita la rete CDN di Office 365.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-304">Normally, these origins are set up for you by default when you enable the Office 365 CDN.</span></span> <span data-ttu-id="ed7f6-305">Tuttavia, se si desidera abilitarli manualmente, attenersi alla seguente procedura.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-305">However, if you want to enable them manually, follow these steps.</span></span>
  
+ <span data-ttu-id="ed7f6-306">Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire la raccolta di stili come origine pubblica.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-306">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the style library as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ <span data-ttu-id="ed7f6-307">Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire le pagine master come origine pubblica.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-307">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the master pages as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

<span data-ttu-id="ed7f6-308">Per ulteriori informazioni su questo comando e sulla relativa sintassi, vedere [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-308">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span></span>

<span data-ttu-id="ed7f6-309">Dopo aver eseguito il comando, il sistema sincronizza la configurazione all'interno del datacenter.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-309">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="ed7f6-310">Questo può richiedere fino a 15 minuti.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-310">This can take up to 15 minutes.</span></span>

<span data-ttu-id="ed7f6-311"><a name="ExamplePrivateOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="ed7f6-311"></span></span>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a><span data-ttu-id="ed7f6-312">Esempio: configurare un'origine privata per le risorse del sito, le pagine del sito e le immagini di pubblicazione per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ed7f6-312">Example: Configure a private origin for your site assets, site pages, and publishing images for SharePoint Online</span></span>

+ <span data-ttu-id="ed7f6-313">Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire la cartella asset del sito come origine privata.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-313">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site assets folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ <span data-ttu-id="ed7f6-314">Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire la cartella pagine del sito come origine privata.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-314">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site pages folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ <span data-ttu-id="ed7f6-315">Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire la cartella delle immagini di pubblicazione come origine privata.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-315">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the publishing images folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

<span data-ttu-id="ed7f6-316">Per ulteriori informazioni su questo comando e sulla relativa sintassi, vedere [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-316">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span></span>

<span data-ttu-id="ed7f6-317">Dopo aver eseguito il comando, il sistema sincronizza la configurazione all'interno del datacenter.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-317">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="ed7f6-318">Questo può richiedere fino a 15 minuti.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-318">This can take up to 15 minutes.</span></span>

<span data-ttu-id="ed7f6-319"><a name="ExamplePrivateOriginSiteCollection"> </a></span><span class="sxs-lookup"><span data-stu-id="ed7f6-319"></span></span>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a><span data-ttu-id="ed7f6-320">Esempio: configurare un'origine privata per una raccolta siti per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ed7f6-320">Example: Configure a private origin for a site collection for SharePoint Online</span></span>

<span data-ttu-id="ed7f6-321">Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire una raccolta siti come origine privata.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-321">Use the **Add-SPOTenantCdnOrigin** cmdlet to define a site collection as a private origin.</span></span> <span data-ttu-id="ed7f6-322">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-322">For example:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="ed7f6-323">Per ulteriori informazioni su questo comando e sulla relativa sintassi, vedere [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-323">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="ed7f6-324">Dopo aver eseguito il comando, il sistema sincronizza la configurazione all'interno del datacenter.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-324">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="ed7f6-325">È possibile che venga visualizzato un messaggio di _configurazione in sospeso_ che è previsto quando il tenant di SharePoint Online si connette al servizio CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-325">You may see a _Configuration pending_ message which is expected as the SharePoint Online tenant connects to the CDN service.</span></span> <span data-ttu-id="ed7f6-326">Questo può richiedere fino a 15 minuti.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-326">This can take up to 15 minutes.</span></span>

<span data-ttu-id="ed7f6-327"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="ed7f6-327"></span></span>
### <a name="manage-the-office-365-cdn"></a><span data-ttu-id="ed7f6-328">Gestire la rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-328">Manage the Office 365 CDN</span></span>

<span data-ttu-id="ed7f6-329">Dopo aver configurato la rete CDN, è possibile apportare modifiche alla configurazione durante l'aggiornamento del contenuto o in base alle modifiche apportate alle esigenze, come descritto in questa sezione.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-329">Once you've set up the CDN, you can make changes to your configuration as you update content or as your needs change, as described in this section.</span></span>
  
<span data-ttu-id="ed7f6-330"><a name="Office365CDNforSPOaddremoveasset"> </a></span><span class="sxs-lookup"><span data-stu-id="ed7f6-330"></span></span>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a><span data-ttu-id="ed7f6-331">Aggiungere, aggiornare o rimuovere risorse dalla rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-331">Add, update, or remove assets from the Office 365 CDN</span></span>

<span data-ttu-id="ed7f6-332">Dopo aver completato la procedura di installazione, è possibile aggiungere nuove risorse e aggiornare o rimuovere le risorse esistenti ogni volta che si desidera.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-332">Once you've completed the setup steps, you can add new assets, and update or remove existing assets whenever you want.</span></span> <span data-ttu-id="ed7f6-333">È sufficiente apportare le modifiche apportate alle risorse nella cartella o nella raccolta di SharePoint identificate come origine.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-333">Just make your changes to the assets in the folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="ed7f6-334">Se si aggiunge un nuovo asset, è possibile utilizzarlo immediatamente tramite la rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-334">If you add a new asset, it is available through the CDN immediately.</span></span> <span data-ttu-id="ed7f6-335">Tuttavia, se si aggiorna la risorsa, saranno necessari fino a 15 minuti affinché la nuova copia venga propagata e diventi disponibile nella rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-335">However, if you update the asset, it will take up to 15 minutes for the new copy to propagate and become available in the CDN.</span></span>
  
<span data-ttu-id="ed7f6-336">Se è necessario recuperare il percorso dell'origine, è possibile utilizzare il cmdlet **Get-SPOTenantCdnOrigins** .</span><span class="sxs-lookup"><span data-stu-id="ed7f6-336">If you need to retrieve the location of the origin, you can use the **Get-SPOTenantCdnOrigins** cmdlet.</span></span> <span data-ttu-id="ed7f6-337">Per informazioni sull'utilizzo di questo cmdlet, vedere [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/library/mt790770.aspx).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-337">For information on how to use this cmdlet, see [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/library/mt790770.aspx).</span></span>

<span data-ttu-id="ed7f6-338"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="ed7f6-338"></span></span>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a><span data-ttu-id="ed7f6-339">Rimuovere un'origine dalla rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-339">Remove an origin from the Office 365 CDN</span></span>

<span data-ttu-id="ed7f6-340">È possibile rimuovere l'accesso a una cartella o a una raccolta di SharePoint identificata come origine.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-340">You can remove access to a folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="ed7f6-341">A tale scopo, utilizzare il cmdlet **Remove-SPOTenantCdnOrigin** .</span><span class="sxs-lookup"><span data-stu-id="ed7f6-341">To do this, use the **Remove-SPOTenantCdnOrigin** cmdlet.</span></span>

``` powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

<span data-ttu-id="ed7f6-342">Per informazioni sull'utilizzo di questo cmdlet, vedere [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790761.aspx).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-342">For information on how to use this cmdlet, see [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790761.aspx).</span></span>

<span data-ttu-id="ed7f6-343"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="ed7f6-343"></span></span>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a><span data-ttu-id="ed7f6-344">Modificare un'origine nella rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-344">Modify an origin in the Office 365 CDN</span></span>

<span data-ttu-id="ed7f6-345">Non è possibile modificare un'origine creata.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-345">You cannot modify an origin you've created.</span></span> <span data-ttu-id="ed7f6-346">Rimuovere invece l'origine e quindi aggiungerne una nuova.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-346">Instead, remove the origin and then add a new one.</span></span> <span data-ttu-id="ed7f6-347">Per ulteriori informazioni, vedere [per rimuovere un'origine dalla rete CDN di Office 365](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) e [per aggiungere un'origine per le risorse](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-347">For more information, see [To remove an origin from the Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) and [To add an origin for your assets](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span></span>

<span data-ttu-id="ed7f6-348"><a name="Office365CDNforSPODisable"> </a></span><span class="sxs-lookup"><span data-stu-id="ed7f6-348"></span></span>
#### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="ed7f6-349">Disabilitare la rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-349">Disable the Office 365 CDN</span></span>

<span data-ttu-id="ed7f6-350">Utilizzare il cmdlet **set-SPOTenantCdnEnabled** per disabilitare la rete CDN per l'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-350">Use the **Set-SPOTenantCdnEnabled** cmdlet to disable the CDN for your organization.</span></span> <span data-ttu-id="ed7f6-351">Se sono abilitate sia le origini pubbliche che quelle private per la rete CDN, è necessario eseguire il cmdlet due volte come illustrato negli esempi riportati di seguito.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-351">If you have both the public and private origins enabled for the CDN, you need to run the cmdlet twice as shown in the following examples.</span></span>
  
<span data-ttu-id="ed7f6-352">Per disabilitare l'utilizzo delle origini pubbliche nella rete CDN, immettere il seguente comando:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-352">To disable use of public origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

<span data-ttu-id="ed7f6-353">Per disabilitare l'utilizzo delle origini private nella rete CDN, immettere il seguente comando:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-353">To disable use of the private origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

<span data-ttu-id="ed7f6-354">Per ulteriori informazioni su questo cmdlet, vedere [set-SPOTenantCdnEnabled](https://technet.microsoft.com/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-354">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/library/mt790765.aspx).</span></span>

</details>

<span data-ttu-id="ed7f6-355"><a name="CDNSetupinCLI"> </a></span><span class="sxs-lookup"><span data-stu-id="ed7f6-355"></span></span>
## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a><span data-ttu-id="ed7f6-356">Impostare e configurare la rete CDN di Office 365 tramite la CLI di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-356">Set up and configure the Office 365 CDN using the Office 365 CLI</span></span>

<span data-ttu-id="ed7f6-357">Le procedure descritte in questa sezione richiedono l'installazione di [Office 365 CLI](https://aka.ms/o365cli).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-357">The procedures in this section require that you have installed the [Office 365 CLI](https://aka.ms/o365cli).</span></span> <span data-ttu-id="ed7f6-358">Successivamente, connettersi al tenant di Office 365 utilizzando il comando [login](https://pnp.github.io/office365-cli/cmd/login/) .</span><span class="sxs-lookup"><span data-stu-id="ed7f6-358">Next, connect to your Office 365 tenant using the [login](https://pnp.github.io/office365-cli/cmd/login/) command.</span></span>

<span data-ttu-id="ed7f6-359">Completare questa procedura per impostare e configurare la rete CDN per ospitare le risorse in SharePoint Online utilizzando la CLI di Office 365.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-359">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the Office 365 CLI.</span></span>

<details>
  <summary><span data-ttu-id="ed7f6-360">Fare clic per espandere</span><span class="sxs-lookup"><span data-stu-id="ed7f6-360">Click to expand</span></span></summary>

### <a name="enable-the-office-365-cdn"></a><span data-ttu-id="ed7f6-361">Abilitare la rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-361">Enable the Office 365 CDN</span></span>

<span data-ttu-id="ed7f6-362">È possibile gestire lo stato della rete CDN di Office 365 nel tenant usando il comando [set CDN di SPO](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) .</span><span class="sxs-lookup"><span data-stu-id="ed7f6-362">You can manage the state of the Office 365 CDN in your tenant using the [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) command.</span></span>

<span data-ttu-id="ed7f6-363">Per abilitare la rete CDN pubblica di Office 365 nel tenant, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-363">To enable the Office 365 Public CDN in your tenant execute:</span></span>

```sh
spo cdn set --type Public --enabled true
```

<span data-ttu-id="ed7f6-364">Per abilitare la rete CDN di Office 365 SharePoint, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-364">To enable the Office 365 SharePoint CDN, execute:</span></span>

```sh
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a><span data-ttu-id="ed7f6-365">Visualizzare lo stato corrente della rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-365">View the current status of the Office 365 CDN</span></span>

<span data-ttu-id="ed7f6-366">Per verificare se il tipo specifico di rete CDN di Office 365 è abilitato o disabilitato, utilizzare il comando per ottenere la rete [CDN](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) .</span><span class="sxs-lookup"><span data-stu-id="ed7f6-366">To check if the particular type of Office 365 CDN is enabled or disabled, use the [spo cdn get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) command.</span></span>

<span data-ttu-id="ed7f6-367">Per verificare se la rete CDN pubblica di Office 365 è abilitata, eseguire:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-367">To check if the Office 365 Public CDN is enabled, execute:</span></span>

```sh
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a><span data-ttu-id="ed7f6-368">Visualizzare le origini della rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-368">View the Office 365 CDN origins</span></span>

<span data-ttu-id="ed7f6-369">Per visualizzare l'origine della rete CDN pubblica di Office 365 correntemente configurata, eseguire:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-369">To view the currently configured Office 365 Public CDN origins execute:</span></span>

```sh
spo cdn origin list --type Public
```

<span data-ttu-id="ed7f6-370">Per informazioni sulle origini di cui è possibile eseguire il provisioning per impostazione predefinita, vedere origini della rete [CDN predefinite](use-office-365-cdn-with-spo.md#default-cdn-origins) quando si Abilita la rete CDN di Office 365.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-370">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN.</span></span>

### <a name="add-an-office-365-cdn-origin"></a><span data-ttu-id="ed7f6-371">Aggiungere un'origine della rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-371">Add an Office 365 CDN origin</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ed7f6-372">Non è consigliabile inserire mai risorse considerate sensibili all'organizzazione in una raccolta documenti di SharePoint configurata come origine pubblica.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-372">You should never place resources that are considered sensitive to your organization in a SharePoint document library configured as a public origin.</span></span>

<span data-ttu-id="ed7f6-373">Utilizzare il comando [Aggiungi origine](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) della rete CDN per definire un'origine della rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-373">Use the [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) command to define a CDN origin.</span></span> <span data-ttu-id="ed7f6-374">È possibile definire origini multiple.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-374">You can define multiple origins.</span></span> <span data-ttu-id="ed7f6-375">L'origine è un URL che punta a una raccolta o a una cartella di SharePoint che contiene le risorse che si desidera ospitare dalla rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-375">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>

```sh
spo cdn origin add --type [Public | Private] --origin <path>
```

<span data-ttu-id="ed7f6-376">Dove `path` è il percorso relativo alla cartella che contiene le risorse.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-376">Where `path` is the relative path to the folder that contains the assets.</span></span> <span data-ttu-id="ed7f6-377">È possibile utilizzare i caratteri jolly oltre ai percorsi relativi.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-377">You can use wildcards in addition to relative paths.</span></span>

<span data-ttu-id="ed7f6-378">Per includere tutte le risorse nella **raccolta pagine master** di tutti i siti come origine pubblica, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-378">To include all assets in the **Master Page Gallery** of all sites as a public origin, execute:</span></span>

```sh
spo cdn origin add --type Public --origin */masterpage
```

<span data-ttu-id="ed7f6-379">Per configurare un'origine privata per una raccolta siti specifica, eseguire:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-379">To configure a private origin for a specific site collection, execute:</span></span>

```sh
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> <span data-ttu-id="ed7f6-380">Dopo aver aggiunto un'origine CDN, potrebbero essere necessari fino a 15 minuti affinché sia possibile recuperare i file tramite il servizio CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-380">After adding a CDN origin, it might take up to 15 minutes for you to be able to retrieve files via the CDN service.</span></span> <span data-ttu-id="ed7f6-381">È possibile verificare se l'origine specifica è già stata abilitata utilizzando il comando dell' [elenco di origine](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) della rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-381">You can verify if the particular origin has already been enabled using the [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command.</span></span>

### <a name="remove-an-office-365-cdn-origin"></a><span data-ttu-id="ed7f6-382">Rimozione di un'origine CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-382">Remove an Office 365 CDN origin</span></span>

<span data-ttu-id="ed7f6-383">Utilizzare il comando [Rimuovi origine rete CDN](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) per rimuovere un'origine CDN per il tipo di rete CDN specificato.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-383">Use the [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) command to remove a CDN origin for the specified CDN type.</span></span>

<span data-ttu-id="ed7f6-384">Per rimuovere un'origine pubblica dalla configurazione della rete CDN, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-384">To remove a public origin from the CDN configuration, execute:</span></span>

```sh
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> <span data-ttu-id="ed7f6-385">La rimozione di un'origine CDN non influisce sui file archiviati in una raccolta documenti corrispondente all'origine.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-385">Removing a CDN origin doesn't affect the files stored in any document library matching that origin.</span></span> <span data-ttu-id="ed7f6-386">Se tali risorse sono state referenziate utilizzando l'URL di SharePoint, SharePoint passerà automaticamente all'URL originale che punta alla raccolta documenti.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-386">If these assets have been referenced using their SharePoint URL, SharePoint will automatically switch back to the original URL pointing to the document library.</span></span> <span data-ttu-id="ed7f6-387">Se, tuttavia, le risorse sono state referenziate con un URL pubblico della rete CDN, la rimozione dell'Origine interromperà il collegamento e sarà necessario modificarle manualmente.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-387">If, however, assets have been referenced using a public CDN URL, then removing the origin will break the link and you will need to manually change them.</span></span>

### <a name="modify-an-office-365-cdn-origin"></a><span data-ttu-id="ed7f6-388">Modificare un'origine della rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-388">Modify an Office 365 CDN origin</span></span>

<span data-ttu-id="ed7f6-389">Non è possibile modificare un'origine CDN esistente.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-389">It's not possible to modify an existing CDN origin.</span></span> <span data-ttu-id="ed7f6-390">Al contrario, è necessario rimuovere l'origine della rete CDN precedentemente `spo cdn origin remove` definita usando il comando e aggiungerne una `spo cdn origin add` nuova utilizzando il comando.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-390">Instead, you should remove the previously defined CDN origin using the `spo cdn origin remove` command and add a new one using the `spo cdn origin add` command.</span></span>

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a><span data-ttu-id="ed7f6-391">Modificare i tipi di file da includere nella rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-391">Change the types of files to include in the Office 365 CDN</span></span>

<span data-ttu-id="ed7f6-392">Per impostazione predefinita, i seguenti tipi di file sono inclusi nella rete CDN: _. CSS,. EOT,. gif,. ico,. jpeg,. jpg,. js,. map,. png,. svg,. ttf e. WOFF_.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-392">By default, the following file types are included in the CDN: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff_.</span></span> <span data-ttu-id="ed7f6-393">Se è necessario includere altri tipi di file nella rete CDN, è possibile modificare la configurazione della rete CDN utilizzando il comando [set di criteri](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) della rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-393">If you need to include additional file types in the CDN, you can change the CDN configuration using the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command.</span></span>

> [!NOTE]
> <span data-ttu-id="ed7f6-394">Quando si modifica l'elenco dei tipi di file, è necessario sovrascrivere l'elenco correntemente definito.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-394">When changing the list of file types, you overwrite the currently defined list.</span></span> <span data-ttu-id="ed7f6-395">Se si desidera includere altri tipi di file, utilizzare innanzitutto il comando dell' [elenco dei criteri](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) della rete CDN per individuare i tipi di file attualmente configurati.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-395">If you want to include additional file types, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command to find out which file types are currently configured.</span></span>

<span data-ttu-id="ed7f6-396">Per aggiungere il tipo di file _JSON_ all'elenco predefinito dei tipi di file inclusi nella rete CDN pubblica, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-396">To add the _JSON_ file type to the default list of file types included in the public CDN, execute:</span></span>

```sh
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a><span data-ttu-id="ed7f6-397">Modificare l'elenco di classificazioni dei siti che si desidera escludere dalla rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-397">Change the list of site classifications you want to exclude from the Office 365 CDN</span></span>

<span data-ttu-id="ed7f6-398">Utilizzare il comando [set di criteri](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) della rete CDN per escludere le classificazioni dei siti che non si desidera rendere disponibili tramite la rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-398">Use the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="ed7f6-399">Per impostazione predefinita, non sono escluse le classificazioni dei siti.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-399">By default, no site classifications are excluded.</span></span>

> [!NOTE]
> <span data-ttu-id="ed7f6-400">Quando si modifica l'elenco di classificazioni dei siti esclusi, è necessario sovrascrivere l'elenco attualmente definito.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-400">When changing the list of excluded site classifications, you overwrite the currently defined list.</span></span> <span data-ttu-id="ed7f6-401">Se si desidera escludere altre classificazioni, utilizzare innanzitutto il comando dell' [elenco dei criteri](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) della rete CDN per scoprire quali classificazioni sono attualmente configurate.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-401">If you want to exclude additional classifications, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) command to find out which classifications are currently configured.</span></span>

<span data-ttu-id="ed7f6-402">Per escludere i siti classificati come _le_ dalla rete CDN pubblica, eseguire</span><span class="sxs-lookup"><span data-stu-id="ed7f6-402">To exclude sites classified as _HBI_ from the public CDN, execute</span></span>

```sh
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="ed7f6-403">Disabilitare la rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-403">Disable the Office 365 CDN</span></span>

<span data-ttu-id="ed7f6-404">Per disabilitare la rete CDN di Office 365 `spo cdn set` , utilizzare il comando, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-404">To disable the Office 365 CDN use the `spo cdn set` command, for example:</span></span>

```sh
spo cdn set --type Public --enabled false
```

</details>

## <a name="using-your-cdn-assets"></a><span data-ttu-id="ed7f6-405">Utilizzo delle risorse della rete CDN</span><span class="sxs-lookup"><span data-stu-id="ed7f6-405">Using your CDN assets</span></span>

<span data-ttu-id="ed7f6-406">Dopo aver abilitato la rete CDN e le origini e i criteri configurati, è possibile iniziare a utilizzare le risorse della rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-406">Now that you have enabled the CDN and configured origins and policies, you can begin using your CDN assets.</span></span>

<span data-ttu-id="ed7f6-407">In questa sezione vengono fornite informazioni su come utilizzare gli URL della rete CDN nelle pagine e nel contenuto di SharePoint in modo che SharePoint reindirizza le richieste di risorse in origine pubblica e privata alla rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-407">This section will help you understand how to use CDN URLs in your SharePoint pages and content so that SharePoint redirects requests for assets in both public and private origins to the CDN.</span></span>

+ [<span data-ttu-id="ed7f6-408">Aggiornamento di collegamenti alle risorse della rete CDN</span><span class="sxs-lookup"><span data-stu-id="ed7f6-408">Updating links to CDN assets</span></span>](use-office-365-cdn-with-spo.md#updating-links-to-cdn-assets)
+ [<span data-ttu-id="ed7f6-409">Utilizzo delle risorse in origini pubbliche</span><span class="sxs-lookup"><span data-stu-id="ed7f6-409">Using assets in public origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-public-origins)
+ [<span data-ttu-id="ed7f6-410">Utilizzo delle risorse in origine privata</span><span class="sxs-lookup"><span data-stu-id="ed7f6-410">Using assets in private origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)

<span data-ttu-id="ed7f6-411">Per informazioni su come utilizzare la rete CDN per l'hosting di Web part sul lato client, vedere l'argomento [host your web part sul lato client da Office 365 CDN (Hello World Part 4)](https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-411">For information on how to use the CDN for hosting client-side web parts, see the topic [Host your client-side web part from Office 365 CDN (Hello World part 4)](https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).</span></span>

### <a name="updating-links-to-cdn-assets"></a><span data-ttu-id="ed7f6-412">Aggiornamento di collegamenti alle risorse della rete CDN</span><span class="sxs-lookup"><span data-stu-id="ed7f6-412">Updating links to CDN assets</span></span>

<span data-ttu-id="ed7f6-413">Per utilizzare le risorse aggiunte a un'origine, è sufficiente aggiornare i collegamenti al file originale con il percorso del file nell'origine.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-413">To use assets that you have added to an origin, you simply update links to the original file with the path to the file in the origin.</span></span>

+ <span data-ttu-id="ed7f6-414">Modificare la pagina o il contenuto che contiene collegamenti a risorse che sono state aggiunte a un'origine.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-414">Edit the page or content that contains links to assets you have added to an origin.</span></span> <span data-ttu-id="ed7f6-415">È inoltre possibile utilizzare uno dei numerosi metodi per cercare e sostituire globalmente i collegamenti tra un sito o una raccolta siti per l'aggiornamento, se si desidera aggiornare il collegamento a un determinato cespite ovunque venga visualizzato.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-415">You can also use one of several methods to globally search and replace links across an enter site or site collection if you want to update the link to a given asset everywhere it appears.</span></span>
+ <span data-ttu-id="ed7f6-416">Per ogni collegamento a una risorsa di origine, sostituire il percorso con il percorso del file nell'origine della rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-416">For each link to an asset in an origin, replace the path with the path to the file in the CDN origin.</span></span> <span data-ttu-id="ed7f6-417">È possibile utilizzare i percorsi relativi.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-417">You can use relative paths.</span></span>
+ <span data-ttu-id="ed7f6-418">Salvare la pagina o il contenuto.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-418">Save the page or content.</span></span>

<span data-ttu-id="ed7f6-419">Si consideri, ad esempio, l'immagine _/site/SiteAssets/images/image.png_, che è stata copiata nella cartella della raccolta documenti _/site/CDN_origins/public/_.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-419">For example, consider the image _/site/SiteAssets/images/image.png_, which you have copied to the document library folder _/site/CDN_origins/public/_.</span></span> <span data-ttu-id="ed7f6-420">Per utilizzare l'asset della rete CDN, sostituire il percorso originale nel percorso del file di immagine con il percorso dell'origine per rendere il nuovo URL _/site/CDN_origins/Public/Image.png_.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-420">To use the CDN asset, replace the original path to the image file location with the path to the origin to make the new URL _/site/CDN_origins/public/image.png_.</span></span>

<span data-ttu-id="ed7f6-421">Se si desidera utilizzare l'URL completo del cespite anziché un percorso relativo, creare il collegamento in questo modo:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-421">If you want to use the full URL to the asset instead of a relative path, construct the link like so:</span></span>

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> <span data-ttu-id="ed7f6-422">In generale, non è necessario impostare come hardcoded gli URL direttamente nelle risorse della rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-422">In general, you should not hardcode URLs directly to assets in the CDN.</span></span> <span data-ttu-id="ed7f6-423">Tuttavia, è possibile creare manualmente gli URL per le risorse in pubblico Origins se necessario.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-423">However, you can manually construct URLs for assets in public origins if needed.</span></span> <span data-ttu-id="ed7f6-424">Per ulteriori informazioni, vedere [hardcoded degli URL della rete CDN per le risorse pubbliche](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-424">For more information, see [Hardcoding CDN URLs for public assets](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).</span></span>

<span data-ttu-id="ed7f6-425">Per informazioni su come verificare che le risorse vengano servite dalla rete CDN, vedere [come si conferma che le risorse vengono servite dalla rete CDN?](use-office-365-cdn-with-spo.md#CDNConfirm) nella sezione [risoluzione dei problemi relativi alla rete cdn di Office 365](use-office-365-cdn-with-spo.md#CDNTroubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="ed7f6-425">To learn about how to verify that assets are being served from the CDN, see [How do I confirm that assets are being served by the CDN?](use-office-365-cdn-with-spo.md#CDNConfirm) in the [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) section.</span></span>

### <a name="using-assets-in-public-origins"></a><span data-ttu-id="ed7f6-426">Utilizzo delle risorse in origini pubbliche</span><span class="sxs-lookup"><span data-stu-id="ed7f6-426">Using assets in public origins</span></span>

<span data-ttu-id="ed7f6-427">La **caratteristica di pubblicazione** in SharePoint Online riscrive automaticamente gli URL delle risorse archiviate nelle origini pubbliche nei rispettivi EQUIVALEnti CDN in modo che le risorse vengano servite dal servizio CDN invece che da SharePoint.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-427">The **Publishing feature** in SharePoint Online automatically rewrites URLs of assets stored in public origins to their CDN equivalents so that assets are served from the CDN service instead of SharePoint.</span></span>

<span data-ttu-id="ed7f6-428">Se l'origine è in un sito in cui è abilitata la caratteristica di pubblicazione e gli asset che si desidera scaricare nella rete CDN sono presenti in una delle categorie seguenti, SharePoint riscriverà automaticamente gli URL per le risorse nell'origine, purché il cespite non sia stato escluso da una rete CDN  politica.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-428">If your origin is in a site with the Publishing feature enabled, and the assets you want to offload to the CDN are in one of the following categories, SharePoint will automatically rewrite URLs for assets in the origin, provided that the asset has not been excluded by a CDN policy.</span></span>

<span data-ttu-id="ed7f6-429">Di seguito è riportata una panoramica dei collegamenti che vengono automaticamente riscritti dalla caratteristica di pubblicazione di SharePoint:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-429">The following is an overview of which links are automatically rewritten by the SharePoint Publishing feature:</span></span>

+ <span data-ttu-id="ed7f6-430">URL IMG/LINK/CSS nella pagina di pubblicazione classica risposte HTML</span><span class="sxs-lookup"><span data-stu-id="ed7f6-430">IMG/LINK/CSS URLs in classic publishing page HTML responses</span></span>
  + <span data-ttu-id="ed7f6-431">Sono incluse le immagini aggiunte dagli autori all'interno del contenuto HTML di una pagina</span><span class="sxs-lookup"><span data-stu-id="ed7f6-431">This includes images added by authors within the HTML content of a page</span></span>
+ <span data-ttu-id="ed7f6-432">Raccolta immagini presentazione WebPart URL di immagini</span><span class="sxs-lookup"><span data-stu-id="ed7f6-432">Picture Library SlideShow webpart image URLs</span></span>
+ <span data-ttu-id="ed7f6-433">Campi immagine nei risultati dell'API REST di SPList (RenderListDataAsStream)</span><span class="sxs-lookup"><span data-stu-id="ed7f6-433">Image fields in SPList REST API (RenderListDataAsStream) results</span></span>
  + <span data-ttu-id="ed7f6-434">Utilizzare la nuova proprietà _ImageFieldsToTryRewriteToCdnUrls_ per fornire un elenco di campi separati da virgole</span><span class="sxs-lookup"><span data-stu-id="ed7f6-434">Use the new property _ImageFieldsToTryRewriteToCdnUrls_ to provide a comma separated list of fields</span></span>
  + <span data-ttu-id="ed7f6-435">Supporta campi collegamento ipertestuale e campi PublishingImage</span><span class="sxs-lookup"><span data-stu-id="ed7f6-435">Supports hyperlink fields and PublishingImage fields</span></span>
+ <span data-ttu-id="ed7f6-436">Copie trasformate di immagini di SharePoint</span><span class="sxs-lookup"><span data-stu-id="ed7f6-436">SharePoint image renditions</span></span>

<span data-ttu-id="ed7f6-437">Nel diagramma seguente viene illustrato il flusso di lavoro quando SharePoint riceve una richiesta per una pagina contenente risorse provenienti da un'origine pubblica.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-437">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a public origin.</span></span>

<span data-ttu-id="ed7f6-438">![Diagramma del flusso di lavoro: recupero delle risorse di Office 365 CDN da un'origine pubblica](media/O365-CDN/o365-cdn-public-steps-transparent.svg "Flusso di lavoro: recupero delle risorse della rete CDN di Office 365 da un'origine pubblica")</span><span class="sxs-lookup"><span data-stu-id="ed7f6-438">![Workflow diagram: Retrieving Office 365 CDN assets from a public origin](media/O365-CDN/o365-cdn-public-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a public origin")</span></span>

> [!TIP]
> <span data-ttu-id="ed7f6-439">Se si desidera disabilitare la riscrittura automatica per URL specifici in una pagina, è possibile estrarre la pagina e aggiungere il parametro della stringa di query **? NoAutoReWrites = true** alla fine di ogni collegamento che si desidera disabilitare.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-439">If you want to disable auto-rewriting for specific URLs on a page, you can check out the page and add the query string parameter **?NoAutoReWrites=true** to the end of each link you want to disable.</span></span>

#### <a name="hardcoding-cdn-urls-for-public-assets"></a><span data-ttu-id="ed7f6-440">Hardcoded degli URL della rete CDN per le risorse pubbliche</span><span class="sxs-lookup"><span data-stu-id="ed7f6-440">Hardcoding CDN URLs for public assets</span></span>

<span data-ttu-id="ed7f6-441">Se la caratteristica di _pubblicazione_ non è abilitata per un'origine pubblica o se la risorsa non è uno dei tipi di collegamento supportati dalla caratteristica di riscrittura automatica del servizio CDN, è possibile creare manualmente gli URL nel percorso CDN delle risorse e utilizzare tali URL nel contenuto.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-441">If the _Publishing_ feature is not enabled for a public origin, or the asset is not one of the link types supported by the auto-rewrite feature of the CDN service, you can manually construct URLs to the CDN location of the assets and use these URLs in your content.</span></span>

> [!NOTE]
> <span data-ttu-id="ed7f6-442">Non è possibile impostare come hardcoded gli URL della rete CDN per le risorse in un'origine privata perché il token di accesso necessario che forma l'ultima sezione dell'URL viene generato al momento della richiesta della risorsa.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-442">You cannot hardcode CDN URLs to assets in a private origin because the required access token that forms the last section of the URL is generated at the time the resource is requested.</span></span>

<span data-ttu-id="ed7f6-443">Per le risorse della rete CDN pubblica, il formato dell'URL avrà un aspetto analogo al seguente:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-443">For public CDN assets, the URL format will look like the following:</span></span>

``` html
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

<span data-ttu-id="ed7f6-444">Sostituire **TenantHostName** con il nome del tenant.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-444">Replace **TenantHostName** with your tenant name.</span></span> <span data-ttu-id="ed7f6-445">Esempio:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-445">Example:</span></span>

``` html
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

### <a name="using-assets-in-private-origins"></a><span data-ttu-id="ed7f6-446">Utilizzo delle risorse in origine privata</span><span class="sxs-lookup"><span data-stu-id="ed7f6-446">Using assets in private origins</span></span>

<span data-ttu-id="ed7f6-447">Non è necessaria alcuna configurazione aggiuntiva per l'utilizzo di risorse in origine privata.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-447">No additional configuration is required to use assets in private origins.</span></span> <span data-ttu-id="ed7f6-448">SharePoint Online riscrive automaticamente gli URL per le risorse in origine privata in modo che le richieste per tali risorse vengano sempre servite dalla rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-448">SharePoint Online automatically rewrites URLs for assets in private origins so requests for those assets will always be served from the CDN.</span></span> <span data-ttu-id="ed7f6-449">Non è possibile creare manualmente gli URL per le risorse della rete CDN in origine privata, poiché tali URL contengono token che devono essere generati automaticamente da SharePoint Online al momento della richiesta del cespite.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-449">You cannot manually build URLs to CDN assets in private origins because these URLs contain tokens that must be auto-generated by SharePoint Online at the time the asset is requested.</span></span>

<span data-ttu-id="ed7f6-450">L'accesso alle risorse in origine privata è protetto da token generati dinamicamente in base alle autorizzazioni utente per l'origine, con gli avvertimenti descritti nelle sezioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-450">Access to assets in private origins is protected by dynamically generated tokens based on user permissions to the origin, with the caveats described in the following sections.</span></span> <span data-ttu-id="ed7f6-451">Gli utenti devono disporre almeno dell'accesso in **lettura** alle origini per la rete CDN per il rendering del contenuto.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-451">Users must have at least **read** access to the origins for the CDN to render content.</span></span>

<span data-ttu-id="ed7f6-452">Nel diagramma seguente viene illustrato il flusso di lavoro quando SharePoint riceve una richiesta per una pagina contenente risorse provenienti da un'origine privata.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-452">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a private origin.</span></span>

<span data-ttu-id="ed7f6-453">![Diagramma del flusso di lavoro: recupero delle risorse della rete CDN di Office 365 da un'origine privata](media/O365-CDN/o365-cdn-private-steps-transparent.svg "Flusso di lavoro: recupero delle risorse della rete CDN di Office 365 da un'origine privata")</span><span class="sxs-lookup"><span data-stu-id="ed7f6-453">![Workflow diagram: Retrieving Office 365 CDN assets from a private origin](media/O365-CDN/o365-cdn-private-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a private origin")</span></span>

#### <a name="token-based-authorization-in-private-origins"></a><span data-ttu-id="ed7f6-454">Autorizzazione basata su token in origini private</span><span class="sxs-lookup"><span data-stu-id="ed7f6-454">Token-based authorization in private origins</span></span>

<span data-ttu-id="ed7f6-455">L'accesso alle risorse in origine privata nella rete CDN di Office 365 è concesso dai token generati da SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-455">Access to assets in private origins in the Office 365 CDN is granted by tokens generated by SharePoint Online.</span></span> <span data-ttu-id="ed7f6-456">Gli utenti che dispongono già dell'autorizzazione per l'accesso alla cartella o alla raccolta designata dall'origine vengono assegnati automaticamente i token che consentono all'utente di accedere al file in base al livello di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-456">Users who already have permission to access to the folder or library designated by the origin are automatically granted tokens that permit the user to access the file based on their permission level.</span></span> <span data-ttu-id="ed7f6-457">Questi token di accesso sono validi da 30 a 90 minuti dopo la loro generazione per impedire attacchi di riproduzione di token.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-457">These access tokens are valid for 30 to 90 minutes after they are generated to help prevent token replay attacks.</span></span>

<span data-ttu-id="ed7f6-458">Dopo la generazione del token di accesso, SharePoint Online restituisce un URI personalizzato al client contenente due parametri di autorizzazione _eat_ (token di autorizzazione Edge) e _OAT_ (token di autorizzazione di origine).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-458">Once the access token is generated, SharePoint Online returns a custom URI to the client containing two authorization parameters _eat_ (edge authorization token) and _oat_ (origin authorization token).</span></span> <span data-ttu-id="ed7f6-459">La struttura di ogni token è _<' data di scadenza nel formato tempo Epoch ' >__< >' firma sicura ' _.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-459">The structure of each token is _<'expiration time in Epoch time format'>__<'secure signature'>_.</span></span> <span data-ttu-id="ed7f6-460">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-460">For example:</span></span>

``` html
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> <span data-ttu-id="ed7f6-461">Tutti gli utenti in possesso del token possono accedere alla risorsa nella rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-461">Anyone in possession of the token can access the resource in the CDN.</span></span> <span data-ttu-id="ed7f6-462">Tuttavia, gli URL che contengono questi token di accesso vengono condivisi solo su HTTPS, quindi, a meno che l'URL non venga condiviso in modo esplicito da un utente finale prima della scadenza del token, il bene non sarà accessibile agli utenti non autorizzati.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-462">However, URLs containing these access tokens are only shared over HTTPS, so unless the URL is explicitly shared by an end user before the token expires, the asset won’t be accessible to unauthorized users.</span></span>

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a><span data-ttu-id="ed7f6-463">Le autorizzazioni a livello di elemento non sono supportate per le risorse in origine privata</span><span class="sxs-lookup"><span data-stu-id="ed7f6-463">Item-level permissions are not supported for assets in private origins</span></span>

<span data-ttu-id="ed7f6-464">È importante tenere presente che SharePoint Online non supporta le autorizzazioni a livello di elemento per le risorse in origine privata.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-464">It is important to note that SharePoint Online does not support item-level permissions for assets in private origins.</span></span> <span data-ttu-id="ed7f6-465">Ad esempio, per un file in `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`cui gli utenti hanno accesso effettivo al file, date le condizioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-465">For example, for a file located at `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, users have effective access to the file given the following conditions:</span></span>

|<span data-ttu-id="ed7f6-466">Utente</span><span class="sxs-lookup"><span data-stu-id="ed7f6-466">User</span></span>  |<span data-ttu-id="ed7f6-467">Autorizzazioni</span><span class="sxs-lookup"><span data-stu-id="ed7f6-467">Permissions</span></span>  |<span data-ttu-id="ed7f6-468">Accesso efficace</span><span class="sxs-lookup"><span data-stu-id="ed7f6-468">Effective access</span></span>  |
|---------|---------|---------|
|<span data-ttu-id="ed7f6-469">Utente 1</span><span class="sxs-lookup"><span data-stu-id="ed7f6-469">User 1</span></span>     |<span data-ttu-id="ed7f6-470">Ha accesso a Folder1</span><span class="sxs-lookup"><span data-stu-id="ed7f6-470">Has access to folder1</span></span>         |<span data-ttu-id="ed7f6-471">È possibile accedere a image1. jpg dalla rete CDN</span><span class="sxs-lookup"><span data-stu-id="ed7f6-471">Can access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="ed7f6-472">Utente 2</span><span class="sxs-lookup"><span data-stu-id="ed7f6-472">User 2</span></span>     |<span data-ttu-id="ed7f6-473">Non dispone dell'accesso a Folder1</span><span class="sxs-lookup"><span data-stu-id="ed7f6-473">Does not have access to folder1</span></span>         |<span data-ttu-id="ed7f6-474">Non è possibile accedere a image1. jpg dalla rete CDN</span><span class="sxs-lookup"><span data-stu-id="ed7f6-474">Cannot access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="ed7f6-475">Utente 3</span><span class="sxs-lookup"><span data-stu-id="ed7f6-475">User 3</span></span>     |<span data-ttu-id="ed7f6-476">Non dispone dell'accesso a Folder1, ma viene concessa l'autorizzazione esplicita per accedere a image1. jpg in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ed7f6-476">Does not have access to folder1, but is granted explicit permission to access image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="ed7f6-477">Possibile accedere all'asset image1. jpg direttamente da SharePoint Online, ma non dalla rete CDN</span><span class="sxs-lookup"><span data-stu-id="ed7f6-477">Can access the asset image1.jpg directly from SharePoint Online, but not from the CDN</span></span>         |
|<span data-ttu-id="ed7f6-478">Utente 4</span><span class="sxs-lookup"><span data-stu-id="ed7f6-478">User 4</span></span>     |<span data-ttu-id="ed7f6-479">Ha accesso a Folder1, ma è stato negato in modo esplicito l'accesso a image1. jpg in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ed7f6-479">Has access to folder1, but has been explicitly denied access to image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="ed7f6-480">Non è possibile accedere al cespite da SharePoint Online, ma è possibile accedere alla risorsa dalla rete CDN nonostante venga negato l'accesso al file in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ed7f6-480">Cannot access the asset from SharePoint Online, but can access the asset from the CDN despite being denied access to the file in SharePoint Online</span></span>         |

<span data-ttu-id="ed7f6-481"><a name="CDNTroubleshooting"> </a></span><span class="sxs-lookup"><span data-stu-id="ed7f6-481"></span></span>
## <a name="troubleshooting-the-office-365-cdn"></a><span data-ttu-id="ed7f6-482">Risoluzione dei problemi relativi alla rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-482">Troubleshooting the Office 365 CDN</span></span>

<span data-ttu-id="ed7f6-483"><a name="CDNConfirm"> </a></span><span class="sxs-lookup"><span data-stu-id="ed7f6-483"></span></span>
### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a><span data-ttu-id="ed7f6-484">Come si conferma che le risorse vengono servite dalla rete CDN?</span><span class="sxs-lookup"><span data-stu-id="ed7f6-484">How do I confirm that assets are being served by the CDN?</span></span>

<span data-ttu-id="ed7f6-485">Dopo aver aggiunto collegamenti alle risorse della rete CDN a una pagina, è possibile verificare che il bene sia stato servito dalla rete CDN esplorando la pagina, facendo clic con il pulsante destro del mouse sull'immagine dopo aver eseguito il rendering e esaminando l'URL dell'immagine.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-485">Once you have added links to CDN assets to a page, you can confirm that the asset is being served from the CDN by browsing to the page, right clicking on the image once it has rendered and reviewing the image URL.</span></span>

<span data-ttu-id="ed7f6-486">È inoltre possibile utilizzare gli strumenti di sviluppo del browser per visualizzare l'URL di ogni risorsa in una pagina o utilizzare uno strumento di traccia di rete di terze parti.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-486">You can also use your browser's developer tools to view the URL for each asset on a page, or use a third party network trace tool.</span></span>

> [!NOTE]
> <span data-ttu-id="ed7f6-487">Se si utilizza uno strumento di rete, ad esempio Fiddler, per testare le risorse all'esterno del rendering del cespite da una pagina di SharePoint, è necessario aggiungere manualmente l'intestazione `https://yourdomain.sharepoint.com`referer "Referer:" alla richiesta GET, in cui l'URL è l'URL radice del tenant di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-487">If you use a network tool such as Fiddler to test your assets outside of rendering the asset from a SharePoint page, you must manually add the referer header “Referer: `https://yourdomain.sharepoint.com`” to the GET request where the URL is the root URL of your SharePoint Online tenant.</span></span>

<span data-ttu-id="ed7f6-488">Non è possibile testare gli URL della rete CDN direttamente in un Web browser perché è necessario disporre di un Referer proveniente da SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-488">You cannot test CDN URLs directly in a web browser because you must have a referer coming from SharePoint Online.</span></span> <span data-ttu-id="ed7f6-489">Tuttavia, se si aggiunge l'URL delle risorse della rete CDN a una pagina di SharePoint e quindi si apre la pagina in un browser, verrà visualizzata la risorsa della rete CDN di cui è stato eseguito il rendering nella pagina.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-489">However, if you add the CDN asset URL to a SharePoint page and then open the page in a browser, you will see the CDN asset rendered on the page.</span></span>

<span data-ttu-id="ed7f6-490">Per ulteriori informazioni sull'utilizzo degli strumenti di sviluppo nel browser Microsoft Edge, vedere [Microsoft Edge Developer Tools](https://docs.microsoft.com/microsoft-edge/devtools-guide).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-490">For more information on using the developer tools in the Microsoft Edge browser, see [Microsoft Edge Developer Tools](https://docs.microsoft.com/microsoft-edge/devtools-guide).</span></span>

<span data-ttu-id="ed7f6-491">Per guardare un breve video ospitato nei [modelli di sviluppo di SharePoint e nelle pratiche del canale YouTube](https://aka.ms/sppnp-videos) che dimostra come verificare che la rete CDN funzioni correttamente, vedere [verifying your CDN Usage and assicuration Optimal Network Connectivity](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5).</span><span class="sxs-lookup"><span data-stu-id="ed7f6-491">To watch a short video hosted in the [SharePoint Developer Patterns and Practices YouTube channel](https://aka.ms/sppnp-videos) demonstrating how to verify that your CDN is working, please see [Verifying your CDN usage and ensuring optimal network connectivity](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5).</span></span>

### <a name="why-are-assets-from-a-new-origin-unavailable"></a><span data-ttu-id="ed7f6-492">Perché le risorse di una nuova origine non sono disponibili?</span><span class="sxs-lookup"><span data-stu-id="ed7f6-492">Why are assets from a new origin unavailable?</span></span>
<span data-ttu-id="ed7f6-493">Le risorse in nuove origini non saranno immediatamente disponibili per l'utilizzo, poiché richiede tempo affinché la registrazione venga propagata attraverso la rete CDN e che le risorse vengano caricate dall'origine all'archiviazione CDN.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-493">Assets in new origins will not immediately be available for use, as it takes time for the registration to propagate through the CDN and for the assets to be uploaded from the origin to CDN storage.</span></span> <span data-ttu-id="ed7f6-494">Il tempo necessario per la disponibilità delle risorse nella rete CDN dipende dal numero di risorse e delle dimensioni dei file.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-494">The time required for assets to be available in the CDN depends on how many assets and the files sizes.</span></span>

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a><span data-ttu-id="ed7f6-495">La Web part sul lato client o la soluzione di SharePoint Framework non funziona</span><span class="sxs-lookup"><span data-stu-id="ed7f6-495">My client-side web part or SharePoint Framework solution isn't working</span></span>

<span data-ttu-id="ed7f6-496">Quando si Abilita la rete CDN di Office 365 per le origini pubbliche, il servizio CDN crea automaticamente queste origini predefinite:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-496">When you enable the Office 365 CDN for public origins, the CDN service automatically creates these default origins:</span></span>

+ <span data-ttu-id="ed7f6-497">\*/MASTERPAGE</span><span class="sxs-lookup"><span data-stu-id="ed7f6-497">\*/MASTERPAGE</span></span>
+ <span data-ttu-id="ed7f6-498">\* LIBRERIA/STYLE</span><span class="sxs-lookup"><span data-stu-id="ed7f6-498">\*/STYLE LIBRARY</span></span>
+ <span data-ttu-id="ed7f6-499">\*/CLIENTSIDEASSETS</span><span class="sxs-lookup"><span data-stu-id="ed7f6-499">\*/CLIENTSIDEASSETS</span></span>

<span data-ttu-id="ed7f6-500">Se l'origine \*/clientsideassets è mancante, le soluzioni di SharePoint Framework avranno esito negativo e non verranno generati messaggi di avviso o di errore.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-500">If the \*/clientsideassets origin is missing, SharePoint Framework solutions will fail, and no warning or error messages are generated.</span></span> <span data-ttu-id="ed7f6-501">Questa origine potrebbe non essere presente perché la rete CDN è stata abilitata con il parametro _-NoDefaultOrigins_ impostato su **$true**oppure perché l'origine è stata eliminata manualmente.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-501">This origin may be missing either because the CDN was enabled with the _-NoDefaultOrigins_ parameter set to **$true**, or because the origin was manually deleted.</span></span>

<span data-ttu-id="ed7f6-502">È possibile verificare se l'origine \*/CLIENTSIDEASSETS è presente con il seguente comando di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-502">You can check to see if the \*/CLIENTSIDEASSETS origin is present with the following PowerShell command:</span></span>

``` powershell
Get-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="ed7f6-503">In alternativa, è possibile verificare con Office 365 CLI:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-503">Or you can check with the Office 365 CLI:</span></span>

``` powershell
spo cdn origin list
```

<span data-ttu-id="ed7f6-504">Per aggiungere l'origine in PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-504">To add the origin in PowerShell:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="ed7f6-505">Per aggiungere l'origine nella CLI di Office 365:</span><span class="sxs-lookup"><span data-stu-id="ed7f6-505">To add the origin in the Office 365 CLI:</span></span>

``` powershell
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a><span data-ttu-id="ed7f6-506">Quali moduli di PowerShell e shell CLI è necessario utilizzare con la rete CDN di Office 365?</span><span class="sxs-lookup"><span data-stu-id="ed7f6-506">What PowerShell modules and CLI shells do I need to work with the Office 365 CDN?</span></span>

<span data-ttu-id="ed7f6-507">È possibile scegliere di utilizzare la rete CDN di Office 365 utilizzando il modulo di PowerShell di **SharePoint Online Management Shell** o **Office 365 CLI**.</span><span class="sxs-lookup"><span data-stu-id="ed7f6-507">You can choose to work with the Office 365 CDN using either the **SharePoint Online Management Shell** PowerShell module or the **Office 365 CLI**.</span></span>

+ [<span data-ttu-id="ed7f6-508">Guida introduttiva a SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="ed7f6-508">Getting started with SharePoint Online Management Shell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)
+ [<span data-ttu-id="ed7f6-509">Installazione di Office 365 CLI</span><span class="sxs-lookup"><span data-stu-id="ed7f6-509">Installing the Office 365 CLI</span></span>](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a><span data-ttu-id="ed7f6-510">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ed7f6-510">See also</span></span>

[<span data-ttu-id="ed7f6-511">Reti per la distribuzione di contenuti</span><span class="sxs-lookup"><span data-stu-id="ed7f6-511">Content Delivery Networks</span></span>](https://aka.ms/o365cdns)

[<span data-ttu-id="ed7f6-512">Pianificazione della rete e ottimizzazione delle prestazioni per Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-512">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

[<span data-ttu-id="ed7f6-513">Serie di prestazioni di SharePoint-serie di video della rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="ed7f6-513">SharePoint Performance Series - Office 365 CDN video series</span></span>](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
