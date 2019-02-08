---
title: Utilizzare la rete di distribuzione del contenuto di Office 365 con SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Viene descritto l'utilizzo incorporati contenuto rete di Office 365 (CDN) per velocizzare il recapito delle risorse di SharePoint Online per tutti gli utenti indipendentemente dalla posizione in cui si trova o dalla modalità di accesso ai contenuti.
ms.openlocfilehash: fd118e8df404961e1c35c6297a788397f810d1a2
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "29547114"
---
# <a name="use-the-office-365-content-delivery-network-with-sharepoint-online"></a><span data-ttu-id="67835-103">Utilizzare la rete di distribuzione del contenuto di Office 365 con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="67835-103">Use the Office 365 content delivery network with SharePoint Online</span></span>

<span data-ttu-id="67835-p101">È possibile ospitare statiche risorse della rete di distribuzione del contenuto di Office 365 (CDN) per garantire prestazioni migliori per le pagine di SharePoint Online. Risorse statiche sono file che non cambiano frequentemente, ad esempio immagini, video e audio, fogli di stile, tipi di carattere e i file JavaScript. La rete CDN funziona come un proxy di memorizzazione nella cache geograficamente distribuiti, la memorizzazione nella cache statiche risorse più vicino per i browser che ne fanno richiesta.</span><span class="sxs-lookup"><span data-stu-id="67835-p101">You can host static assets in the Office 365 content delivery network (CDN) to provide better performance for your SharePoint Online pages. Static assets are files that don't change very often, like images, video and audio, style sheets, fonts, and JavaScript files. The CDN works as a geographically distributed caching proxy, by caching static assets closer to the browsers requesting them.</span></span> 
  
<span data-ttu-id="67835-p102">Se si ha già familiarità con la modalità con cui utilizzano CDN, è sufficiente eseguire alcune operazioni per impostare le. In questo argomento viene descritto come. Continuare a leggere per informazioni sulle operazioni preliminari che ospita le risorse statiche e la rete CDN di Office 365.</span><span class="sxs-lookup"><span data-stu-id="67835-p102">If you are already familiar with the way that CDNs work, you only need to complete a few steps to set it up. This topic describes how. Read on for information about the Office 365 CDN and how to get started hosting your static assets.</span></span>
  
 <span data-ttu-id="67835-110">**Eseguire il titolo in [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune).**</span><span class="sxs-lookup"><span data-stu-id="67835-110">**Head back to [Network planning and performance tuning for Office 365](https://aka.ms/tune).**</span></span>
  
## <a name="office-365-cdn-basics"></a><span data-ttu-id="67835-111">Nozioni fondamentali sulla rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="67835-111">Office 365 CDN basics</span></span>

<span data-ttu-id="67835-p103">La rete CDN di Office 365 è inclusa come parte dell'abbonamento a SharePoint Online. Non è necessario pagare molto. Office 365 fornisce supporto per entrambi privato e pubblico access ed è possibile alle risorse statica host in più posizioni o origini. La rete CDN di Office 365 non corrisponde al CDN Azure. Per ulteriori informazioni su come utilizzare una rete CDN o sui concetti generali CDN, vedere [reti di distribuzione del contenuto](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="67835-p103">The Office 365 CDN is included as part of your SharePoint Online subscription. You don't have to pay extra for it. Office 365 provides support for both private and public access and allows you to host static assets in multiple locations, or origins. The Office 365 CDN is not the same as the Azure CDN. If you need more information about why to use a CDN or about general CDN concepts, see [Content delivery networks](content-delivery-networks.md).</span></span>
  
## <a name="how-the-cdn-grants-access-to-end-users"></a><span data-ttu-id="67835-117">Come la rete CDN concede l'accesso agli utenti finali</span><span class="sxs-lookup"><span data-stu-id="67835-117">How the CDN grants access to end users</span></span>

<span data-ttu-id="67835-p104">Privata risorse statiche nella rete CDN di Office 365 accedere dai token generati da SharePoint Online. Gli utenti che dispongono dell'autorizzazione per accedere alla cartella o raccolta designato dall'origine verranno concesse automaticamente i token. SharePoint Online non supporta le autorizzazioni a livello di elemento per la rete CDN.</span><span class="sxs-lookup"><span data-stu-id="67835-p104">Private access to static assets in the Office 365 CDN is granted by tokens generated by SharePoint Online. Users who already have permission to access to the folder or library designated by the origin will automatically be granted tokens. SharePoint Online does not support item-level permissions for the CDN.</span></span>
  
<span data-ttu-id="67835-121">Ad esempio, per un file al `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, assegnate le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="67835-121">For example, for a file located at `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, given the following:</span></span>
  
- <span data-ttu-id="67835-122">1 utente dispone dell'accesso alla cartella 1 e Image1</span><span class="sxs-lookup"><span data-stu-id="67835-122">User 1 has access to folder1 and to image1.jpg</span></span>
    
- <span data-ttu-id="67835-123">L'utente 2 non dispone di accesso alla cartella 1</span><span class="sxs-lookup"><span data-stu-id="67835-123">User 2 does not have access to folder1</span></span>
    
- <span data-ttu-id="67835-124">3 l'utente non dispone dell'accesso alla cartella 1 ma viene concessa l'autorizzazione esplicita per accedere a Image1 tramite SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="67835-124">User 3 does not have access to folder1 but is granted explicit permission to access image1.jpg through SharePoint Online</span></span>
    
- <span data-ttu-id="67835-125">Utente 4 ha accesso alla cartella 1, ma è stato esplicitamente negato l'accesso a Image1</span><span class="sxs-lookup"><span data-stu-id="67835-125">User 4 has access to folder1 but has been explicitly denied access to image1.jpg</span></span>
    
<span data-ttu-id="67835-126">Quindi le seguenti condizioni sono vere:</span><span class="sxs-lookup"><span data-stu-id="67835-126">Then the following are true:</span></span>
  
- <span data-ttu-id="67835-127">L'utente 1 e 4 utente sarà in grado di accedere a Image1 tramite la rete CDN.</span><span class="sxs-lookup"><span data-stu-id="67835-127">User 1 and User 4 will be able to access image1.jpg through the CDN.</span></span>
    
- <span data-ttu-id="67835-128">L'utente 2 e 3 utente non sarà in grado di accedere a Image1 tramite la rete CDN.</span><span class="sxs-lookup"><span data-stu-id="67835-128">User 2 and User 3 will not be able to access image1.jpg through the CDN.</span></span>
    
    <span data-ttu-id="67835-129">Tuttavia, 3 utente può accedere Image1 risorse direttamente tramite SharePoint Online mentre 4 utente non può accedere bene tramite SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="67835-129">However, User 3 can still access the asset image1.jpg directly through SharePoint Online while User 4 cannot access the asset through SharePoint Online.</span></span>
    
## <a name="overview-of-working-with-the-office-365-cdn"></a><span data-ttu-id="67835-130">Panoramica dell'utilizzo con la rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="67835-130">Overview of working with the Office 365 CDN</span></span>

<span data-ttu-id="67835-131">Per configurare la rete CDN di Office 365, attenersi alla procedura riportata base:</span><span class="sxs-lookup"><span data-stu-id="67835-131">To set up the Office 365 CDN, you follow these basic steps:</span></span>
  
- <span data-ttu-id="67835-132">Pianificare la distribuzione CDN:</span><span class="sxs-lookup"><span data-stu-id="67835-132">Plan for CDN deployment:</span></span>
    
  - <span data-ttu-id="67835-p105">Determinare quali risorse statiche si desidera ospitare nella rete CDN Office 365. Per informazioni dettagliate su come effettuare queste scelte, vedere [reti di distribuzione del contenuto](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="67835-p105">Determine which static assets you want to host on the Office 365 CDN. For detailed information about how to make these choices, refer to [Content delivery networks](content-delivery-networks.md).</span></span>
    
  - <span data-ttu-id="67835-p106">[Determinare dove si desidera archiviare le risorse](use-office-365-cdn-with-spo.md#CDNStoreAssets). Questo percorso è una cartella o una raccolta di SharePoint e viene chiamato un'origine.</span><span class="sxs-lookup"><span data-stu-id="67835-p106">[Determine where you want to store your assets](use-office-365-cdn-with-spo.md#CDNStoreAssets). This location is a folder or SharePoint library and is called an origin.</span></span>
    
  - <span data-ttu-id="67835-p107">Determinare se le risorse devono essere effettuate pubbliche o mantenere private. Eseguire questa operazione quando è possibile [scegliere se ogni origine deve essere pubblica o privata](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Se si desidera, è possibile disporre di più origini alcuni sono pubblici e alcuni lavoratori sono private.</span><span class="sxs-lookup"><span data-stu-id="67835-p107">Determine whether the assets should be made public or kept private. You do this when you [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). If you want, you can have multiple origins in which some are public, and some are private.</span></span>
    
- <span data-ttu-id="67835-p108">[Impostare e configurare la rete CDN di Office 365 con SharePoint Online Management Shell](use-office-365-cdn-with-spo.md#CDNSetupinPShell). Dopo aver completato questo passaggio, è necessario:</span><span class="sxs-lookup"><span data-stu-id="67835-p108">[Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell](use-office-365-cdn-with-spo.md#CDNSetupinPShell). When you complete this step, you will have:</span></span>
    
  - <span data-ttu-id="67835-142">Abilitare la rete CDN per l'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="67835-142">Enabled the CDN for your organization.</span></span>
    
  - <span data-ttu-id="67835-p109">Aggiungere le origini. Identificare ogni origine come pubblico o privato.</span><span class="sxs-lookup"><span data-stu-id="67835-p109">Added your origins. You identify each origin as public or private.</span></span>
    
<span data-ttu-id="67835-145">Una volta termine di programma di installazione per [gestire la rete CDN di Office 365](use-office-365-cdn-with-spo.md#CDNManage) nel tempo da:</span><span class="sxs-lookup"><span data-stu-id="67835-145">Once you're done with setup, [Manage the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) over time by:</span></span> 
  
- <span data-ttu-id="67835-146">Aggiunta, l'aggiornamento e rimozione delle risorse</span><span class="sxs-lookup"><span data-stu-id="67835-146">Adding, updating, and removing assets</span></span>
    
- <span data-ttu-id="67835-147">Aggiunta e rimozione di origini</span><span class="sxs-lookup"><span data-stu-id="67835-147">Adding and removing origins</span></span>
    
- <span data-ttu-id="67835-148">Configurazione dei criteri CDN</span><span class="sxs-lookup"><span data-stu-id="67835-148">Configuring CDN policies</span></span>
    
- <span data-ttu-id="67835-149">Se necessario, disabilitare la rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="67835-149">If necessary, disabling the Office 365 CDN</span></span>
    
## <a name="determine-where-you-want-to-store-your-assets"></a><span data-ttu-id="67835-150">Determinare dove si desidera archiviare le risorse</span><span class="sxs-lookup"><span data-stu-id="67835-150">Determine where you want to store your assets</span></span>

<span data-ttu-id="67835-p110">La rete CDN recupera le risorse da una posizione denominata un'origine. Per Office 365, un'origine è una raccolta di SharePoint o una cartella in cui è possibile accedere da un URL. È necessario notevole flessibilità quando si specificano origini per l'organizzazione. Ad esempio, è possibile specificare più origini o una singola origine in cui si desidera inserire tutte le attività di rete CDN. È possibile disporre di origini pubbliche o private per l'organizzazione. La maggior parte delle organizzazioni verranno sceglie di implementare una combinazione delle due configurazioni.</span><span class="sxs-lookup"><span data-stu-id="67835-p110">The CDN fetches your assets from a location called an origin. For Office 365, an origin is a SharePoint library or folder that is accessible by a URL. You have great flexibility when you specify origins for your organization. For example, you can specify multiple origins, or, a single origin where you want to put all your CDN assets. You can choose to have both public or private origins for your organization. Most organizations will choose to implement a combination of the two.</span></span>
  
<span data-ttu-id="67835-p111">Se si definisce centinaia di origini, probabilmente avrà un impatto negativo sul tempo che necessario per elaborare le richieste. È consigliabile che se si dispone di più di circa 100 origini è possibile rivedere l'architettura.</span><span class="sxs-lookup"><span data-stu-id="67835-p111">If you define hundreds of origins, it will likely have a negative impact on the time it takes to process requests. We recommend that if you have more than about 100 origins you might want to rethink your architecture.</span></span>
  
## <a name="choose-whether-each-origin-should-be-public-or-private"></a><span data-ttu-id="67835-159">Scegliere se ogni origine deve essere pubblica o privata</span><span class="sxs-lookup"><span data-stu-id="67835-159">Choose whether each origin should be public or private</span></span>

<span data-ttu-id="67835-p112">Quando si identifica un'origine, si specifica se deve essere resa pubblica o privata. Indipendentemente dall'opzione scelta, Microsoft provvederà tutti automaticamente quando si tratta di amministrazione di rete CDN stesso. Inoltre, è possibile modificare il presente in seguito, dopo aver impostato la rete CDN e identificato le origini.</span><span class="sxs-lookup"><span data-stu-id="67835-p112">When you identify an origin, you specify whether it should be made public or private. Regardless of which option you choose, Microsoft does all the heavy lifting for you when it comes to administration of the CDN itself. Also, you can change your mind later, after you've set up the CDN and identified your origins.</span></span>
  
<span data-ttu-id="67835-163">Miglioramenti delle prestazioni fornisce la possibilità di pubblici e privati, ma ognuno presenta vantaggi e gli attributi univoci.</span><span class="sxs-lookup"><span data-stu-id="67835-163">Both public and private options provide performance improvements, but each has unique attributes and advantages.</span></span>
  
 <span data-ttu-id="67835-164">**Attributi e i vantaggi dell'hosting di risorse in un'origine pubblica**</span><span class="sxs-lookup"><span data-stu-id="67835-164">**Attributes and advantages of hosting assets in a public origin**</span></span>
  
- <span data-ttu-id="67835-165">Risorse esposte in un'origine pubblica sono accessibili a tutti gli utenti in modo anonimo.</span><span class="sxs-lookup"><span data-stu-id="67835-165">Assets exposed in a public origin are accessible by everyone anonymously.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="67835-166">Dopo aver identificato un'origine pubblica nella rete CDN, dovrebbero essere posizionati mai le risorse vengono considerate riservate dell'organizzazione in un'origine pubblico o una raccolta SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="67835-166">If you identify a public origin in your CDN, you should never place resources that are considered sensitive to your organization in a public origin or SharePoint Online library.</span></span> 
  
- <span data-ttu-id="67835-167">Se si rimuove un bene da un'origine pubblica, le risorse continui a essere disponibili fino a 30 giorni dalla cache. Tuttavia, si invalida collegamenti a risorse nella rete CDN all'interno di 15 minuti.</span><span class="sxs-lookup"><span data-stu-id="67835-167">If you remove an asset from a public origin, the asset may continue to be available for up to 30 days from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
    
- <span data-ttu-id="67835-p113">Quando si ospitano fogli di stile (file con estensione CSS) in un'origine pubblica, è possibile utilizzare percorsi relativi e gli URI all'interno del codice. Ciò significa che è possibile fare riferimento la posizione delle immagini di sfondo e altri oggetti relativi alla posizione del bene che di chiamata.</span><span class="sxs-lookup"><span data-stu-id="67835-p113">When you host style sheets (CSS files) in a public origin, you can use relative paths and URIs within the code. This means that you can reference the location of background images and other objects relative to the location of the asset that's calling it.</span></span>
    
- <span data-ttu-id="67835-p114">Mentre è possibile modificare il codice URL dell'origine un pubblica, pertanto non è consigliato. Il motivo di ciò è che se l'accesso per la rete CDN risulta disponibile, l'URL non verrà risolto automaticamente per l'organizzazione in SharePoint Online e può causare tempi di collegamenti interrotti e altri errori.</span><span class="sxs-lookup"><span data-stu-id="67835-p114">While you can hard code a public origin's URL, doing so is not recommended. The reason for this is that if access to the CDN becomes unavailable, the URL will not automatically resolve to your organization in SharePoint Online and might result in broken links and other errors.</span></span>
    
- <span data-ttu-id="67835-p115">Tipi di file predefiniti inclusi per origini pubbliche sono CSS, .eot, GIF, con estensione ico, JPEG, jpg, js, Map, PNG, SVG, ttf e .woff. È possibile specificare altri tipi di file.</span><span class="sxs-lookup"><span data-stu-id="67835-p115">The default file types that are included for public origins are .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff. You can specify additional file types.</span></span>
    
- <span data-ttu-id="67835-p116">Se si desidera, è possibile configurare un criterio per escludere risorse identificato dal classificazioni di sito specificato. Ad esempio, è possibile scegliere di escludere tutte le risorse che sono contrassegnate come "confidential" o "restricted" anche se sono un tipo di file consentiti e si trovano in un'origine pubblica.</span><span class="sxs-lookup"><span data-stu-id="67835-p116">If you want, you can configure a policy to exclude assets that have been identified by site classifications that you specify. For example, you can choose to exclude all assets that are marked as "confidential" or "restricted" even if they are an allowed file type and are located in a public origin.</span></span>
    
 <span data-ttu-id="67835-176">**Attributi e i vantaggi dell'hosting di risorse in un'origine privata**</span><span class="sxs-lookup"><span data-stu-id="67835-176">**Attributes and advantages of hosting assets in a private origin**</span></span>
  
- <span data-ttu-id="67835-p117">Gli utenti possono accedere le risorse da un'origine privata solo se è autorizzato a tale scopo. Non è consentito l'accesso anonimo a tali risorse.</span><span class="sxs-lookup"><span data-stu-id="67835-p117">Users can only access the assets from a private origin if they are authorized to do so. Anonymous access to these assets is prevented.</span></span>
    
- <span data-ttu-id="67835-179">Se si rimuove una risorsa dall'origine privata, bene continui a essere disponibile per un massimo di un'ora dalla cache. Tuttavia, si invalida collegamenti a risorse nella rete CDN all'interno di 15 minuti.</span><span class="sxs-lookup"><span data-stu-id="67835-179">If you remove an asset from the private origin, the asset may continue to be available for up to an hour from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
    
- <span data-ttu-id="67835-p118">Tipi di file predefiniti inclusi per origini private sono GIF, con estensione ico, JPEG, jpg, js e PNG. È possibile specificare altri tipi di file.</span><span class="sxs-lookup"><span data-stu-id="67835-p118">The default file types that are included for private origins are .gif, .ico, .jpeg, .jpg, .js, and .png. You can specify additional file types.</span></span>
    
- <span data-ttu-id="67835-182">Proprio come origini pubbliche, è possibile configurare un criterio per escludere risorse identificato dal classificazioni di sito specificato anche se si utilizza i caratteri jolly per includere tutte le risorse all'interno di una cartella o una raccolta siti.</span><span class="sxs-lookup"><span data-stu-id="67835-182">Just like public origins, you can configure a policy to exclude assets that have been identified by site classifications that you specify even if you use wildcards to include all assets within a folder or Site Library.</span></span>
    
## <a name="default-office-365-cdn-origins"></a><span data-ttu-id="67835-183">Origini di Office 365 CDN predefinito</span><span class="sxs-lookup"><span data-stu-id="67835-183">Default Office 365 CDN origins</span></span>

<span data-ttu-id="67835-p119">Se non diversamente specificato, Office 365 imposta alcune origini predefinito automaticamente quando si abilita la rete CDN di Office 365. Se si escludono inizialmente li, è possibile aggiungere tali origini al termine dell'installazione.</span><span class="sxs-lookup"><span data-stu-id="67835-p119">Unless you specify otherwise, Office 365 sets up some default origins for you when you enable the Office 365 CDN. If you initially exclude them, you can add these origins after you complete setup.</span></span>
  
<span data-ttu-id="67835-186">Origini private predefinito:</span><span class="sxs-lookup"><span data-stu-id="67835-186">Default private origins:</span></span>
  
- <span data-ttu-id="67835-187">\*/userphoto.aspx</span><span class="sxs-lookup"><span data-stu-id="67835-187">\*/userphoto.aspx</span></span>
    
- <span data-ttu-id="67835-188">\*/siteassets</span><span class="sxs-lookup"><span data-stu-id="67835-188">\*/siteassets</span></span>
    
<span data-ttu-id="67835-189">Origini pubbliche predefinite:</span><span class="sxs-lookup"><span data-stu-id="67835-189">Default public origins:</span></span>
  
- <span data-ttu-id="67835-190">\*/MasterPage</span><span class="sxs-lookup"><span data-stu-id="67835-190">\*/masterpage</span></span>
    
- <span data-ttu-id="67835-191">\*raccolta /Style</span><span class="sxs-lookup"><span data-stu-id="67835-191">\*/style library</span></span>

> [!NOTE]
> <span data-ttu-id="67835-p120">Clientsideassets è un'origine pubblica predefinita che è state aggiunte Dec di 2017 in modo che, se sono CDN pubblico prima di quel momento, si non visualizzata la voce aggiunta automaticamente, ma se è stato creato in un secondo momento, è possibile visualizzare questa modifica automaticamente. Se si desidera leggere un esempio dell'utilizzo di questa origine di rete CDN, vedere: [Host sul lato client web part da Office 365 CDN (Hello World parte 4)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)</span><span class="sxs-lookup"><span data-stu-id="67835-p120">Clientsideassets is a default public origin that was added in Dec of 2017 so that, if you had a public CDN before that time, you wouldn't see the entry automatically added, but if you created afterward, you'd see this change automatically. If you'd like to read an example of using this CDN origin, see: [Host your client-side web part from Office 365 CDN (Hello World part 4)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)</span></span>
    
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a><span data-ttu-id="67835-194">Impostare e configurare la rete CDN di Office 365 con SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="67835-194">Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell</span></span>

<span data-ttu-id="67835-p121">Le procedure descritte in questo argomento richiedono l'utilizzo di SharePoint Online Management Shell per la connessione a SharePoint Online. Per ulteriori informazioni, vedere [connettersi a PowerShell per SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="67835-p121">The procedures in this topic require you to use the SharePoint Online Management Shell to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>
  
<span data-ttu-id="67835-197">Completare la procedura seguente per impostare e configurare la rete CDN di Office 365 per ospitare le risorse statiche in SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="67835-197">Complete these steps to set up and configure the Office 365 CDN to host your static assets in SharePoint Online.</span></span>
  
### <a name="to-enable-your-organization-to-use-the-office-365-cdn"></a><span data-ttu-id="67835-198">Per consentire all'organizzazione di utilizzare la rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="67835-198">To enable your organization to use the Office 365 CDN</span></span>

<span data-ttu-id="67835-p122">Utilizzare il cmdlet **Set-SPOTenantCdnEnabled** per consentire all'organizzazione di utilizzare la rete CDN di Office 365. È possibile abilitare all'organizzazione di utilizzare origini pubblici, origini private o entrambi con la rete CDN. È inoltre possibile configurare la rete CDN 365 Office per ignorare l'impostazione delle origini predefinito quando si attiva. È sempre possibile aggiungere tali origini seguito come descritto in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="67835-p122">Use the **Set-SPOTenantCdnEnabled** cmdlet to enable your organization to use the Office 365 CDN. You can enable your organization to use either public origins, private origins, or both with the CDN. You can also configure the Office 365 CDN to skip the setup of default origins when you enable it. You can always add these origins later as described in this topic.</span></span> 
  
<span data-ttu-id="67835-203">In Windows Powershell per SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="67835-203">In Windows Powershell for SharePoint Online:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

<span data-ttu-id="67835-204">Ad esempio, per consentire all'organizzazione di utilizzare origini pubblici e privati con la rete CDN, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="67835-204">For example, to enable your organization to use both public and private origins with the CDN, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="67835-205">Per consentire all'organizzazione di utilizzare origini pubblici e privati con la rete CDN ma ignorare l'impostazione origini predefinito, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="67835-205">To enable your organization to use both public and private origins with the CDN but skip setting up the default origins, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

<span data-ttu-id="67835-206">Per consentire all'organizzazione di utilizzare origini pubbliche con la rete CDN, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="67835-206">To enable your organization to use public origins with the CDN, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

<span data-ttu-id="67835-207">Per consentire all'organizzazione di utilizzare origini private con la rete CDN, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="67835-207">To enable your organization to use private origins with the CDN, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

<span data-ttu-id="67835-208">Per ulteriori informazioni su questo cmdlet, vedere [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="67835-208">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
### <a name="optional-to-change-the-list-of-file-types-to-include-in-the-office-365-cdn"></a><span data-ttu-id="67835-209">(Facoltativo) Per modificare l'elenco dei tipi di file da includere nella rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="67835-209">(Optional) To change the list of file types to include in the Office 365 CDN</span></span>
<span data-ttu-id="67835-210"><a name="Office365CDNforSPOFileType"> </a></span><span class="sxs-lookup"><span data-stu-id="67835-210"></span></span>

> [!TIP]
> <span data-ttu-id="67835-p123">Quando si definiscono i tipi di file utilizzando il cmdlet **Set-SPOTenantCdnPolicy** , si sovrascrive l'elenco attualmente definito. Se si desidera aggiungere altri tipi di file all'elenco, utilizzare il cmdlet prima per scoprire quali tipi di file sono già stato abilitati e includono nell'elenco con le nuove strutture.</span><span class="sxs-lookup"><span data-stu-id="67835-p123">When you define file types by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list. If you want to add additional file types to the list, use the cmdlet first to find out what file types are already allowed and include them in the list along with your new ones.</span></span> 
  
<span data-ttu-id="67835-p124">Utilizzare il cmdlet **Set-SPOTenantCdnPolicy** per definire i tipi di file statici che possono essere ospitati da origini pubblici e privati nella rete CDN. Per impostazione predefinita, tipi di risorse comuni sono consentiti per js, GIF, jpg e CSS di esempio.</span><span class="sxs-lookup"><span data-stu-id="67835-p124">Use the **Set-SPOTenantCdnPolicy** cmdlet to define static file types that can be hosted by public and private origins in the CDN. By default, common asset types are allowed, for example .css, .gif, .jpg, and .js.</span></span> 
  
<span data-ttu-id="67835-215">In Windows PowerShell per SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="67835-215">In Windows PowerShell for SharePoint Online:</span></span>
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

<span data-ttu-id="67835-216">Per visualizzare i tipi di file attualmente consentiti per la rete CDN, utilizzare il cmdlet **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="67835-216">To see what file types are currently allowed by the CDN, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span> 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="67835-217">Per ulteriori informazioni su questi cmdlet, vedere [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) e [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="67835-217">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="optional-to-change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a><span data-ttu-id="67835-218">(Facoltativo) Per modificare l'elenco delle classificazioni dei siti che si desidera escludere dalla rete CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="67835-218">(Optional) To change the list of site classifications you want to exclude from the Office 365 CDN</span></span>
<span data-ttu-id="67835-219"><a name="Office365CDNforSPOSiteClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="67835-219"></span></span>

> [!TIP]
> <span data-ttu-id="67835-p125">Quando si escludono le classificazioni di sito utilizzando il cmdlet **Set-SPOTenantCdnPolicy** , si sovrascrive l'elenco attualmente definito. Se si desidera escludere le classificazioni di altri siti, utilizzare il cmdlet prima per scoprire le classificazioni sono già esclusi e quindi aggiungerle con le nuove strutture.</span><span class="sxs-lookup"><span data-stu-id="67835-p125">When you exclude site classifications by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list. If you want to exclude additional site classifications, use the cmdlet first to find out what classifications are already excluded and then add them along with your new ones.</span></span> 
  
<span data-ttu-id="67835-p126">Utilizzare il cmdlet **Set-SPOTenantCdnPolicy** da escludere le classificazioni di siti che non si desidera rendere disponibili tramite la rete CDN. Per impostazione predefinita, le classificazioni Nessun sito vengono esclusi.</span><span class="sxs-lookup"><span data-stu-id="67835-p126">Use the **Set-SPOTenantCdnPolicy** cmdlet to exclude site classifications that you do not want to make available over the CDN. By default, no site classifications are excluded.</span></span> 
  
<span data-ttu-id="67835-224">In Windows PowerShell per SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="67835-224">In Windows PowerShell for SharePoint Online:</span></span>
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

<span data-ttu-id="67835-225">Per visualizzare le classificazioni dei siti sono limitate, utilizzare il cmdlet **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="67835-225">To see what site classifications are currently restricted, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span> 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="67835-226">Per ulteriori informazioni su questi cmdlet, vedere [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) e [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="67835-226">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="to-add-an-origin-for-your-assets"></a><span data-ttu-id="67835-227">Per aggiungere un'origine per le risorse</span><span class="sxs-lookup"><span data-stu-id="67835-227">To add an origin for your assets</span></span>
<span data-ttu-id="67835-228"><a name="Office365CDNforSPOOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="67835-228"></span></span>

<span data-ttu-id="67835-p127">Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire un'origine. È possibile definire più origini. L'origine è un URL che punta a una raccolta SharePoint o una cartella che contiene le risorse che si desidera trovarsi la rete CDN.</span><span class="sxs-lookup"><span data-stu-id="67835-p127">Use the **Add-SPOTenantCdnOrigin** cmdlet to define an origin. You can define multiple origins. The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="67835-232">Dopo aver identificato un'origine pubblica nella rete CDN, dovrebbero essere posizionati mai le risorse sono considerate riservate dell'organizzazione nell'origine pubblica o nella raccolta di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="67835-232">If you identify a public origin in your CDN, you should never place resources that are considered sensitive to your organization in the public origin or SharePoint Online library.</span></span> 
  
```
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path >
```

<span data-ttu-id="67835-p128">Dove percorso è il percorso della cartella che contiene le risorse. È possibile utilizzare i caratteri jolly oltre ai percorsi relativi. Ad esempio, per includere tutte le risorse nella cartella masterpages per tutti i siti come un'origine pubblica entro la rete CDN, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="67835-p128">Where path is the path to the folder that contains the assets. You can use wildcards in addition to relative paths. For example, to include all of the assets in the masterpages folder for all of your sites as a public origin within the CDN, type the following command:</span></span>
  
```
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

<span data-ttu-id="67835-236">Per ulteriori informazioni sulla sintassi e questo comando, vedere [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="67835-236">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="67835-p129">Dopo aver eseguito il comando, il sistema Sincronizza la configurazione nel datacenter. Questa operazione richiede 15 minuti.</span><span class="sxs-lookup"><span data-stu-id="67835-p129">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a><span data-ttu-id="67835-239">Esempio: Configurazione di un'origine pubblica per le pagine master e per la raccolta stili per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="67835-239">Example: Configure a public origin for your master pages and for your style library for SharePoint Online</span></span>
<span data-ttu-id="67835-240"><a name="ExamplePublicOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="67835-240"></span></span>

<span data-ttu-id="67835-p130">In genere, queste origini impostati per è per impostazione predefinita quando si abilita origini pubbliche per la rete CDN di Office 365. Tuttavia, se si desidera attivarli manualmente, eseguire la procedura seguente.</span><span class="sxs-lookup"><span data-stu-id="67835-p130">Normally, these origins are set up for you by default when you enable public origins for the Office 365 CDN. However, if you want to enable them manually, follow these steps.</span></span>
  
- <span data-ttu-id="67835-243">Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire la raccolta stili di un'origine pubblica entro la rete CDN di Office 365.</span><span class="sxs-lookup"><span data-stu-id="67835-243">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the style library as a public origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- <span data-ttu-id="67835-244">Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire le pagine master di un'origine pubblica entro la rete CDN di Office 365.</span><span class="sxs-lookup"><span data-stu-id="67835-244">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the master pages as a public origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

- <span data-ttu-id="67835-245">Per ulteriori informazioni sulla sintassi e questo comando, vedere [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="67835-245">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
    
    <span data-ttu-id="67835-p131">Dopo aver eseguito il comando, il sistema Sincronizza la configurazione nel datacenter. Questa operazione richiede 15 minuti.</span><span class="sxs-lookup"><span data-stu-id="67835-p131">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
    
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a><span data-ttu-id="67835-248">Esempio: Configurazione di un'origine privata per le risorse del sito, le pagine del sito e immagini di pubblicazione per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="67835-248">Example: Configure a private origin for your site assets, site pages, and publishing images for SharePoint Online</span></span>
<span data-ttu-id="67835-249"><a name="ExamplePrivateOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="67835-249"></span></span>

- <span data-ttu-id="67835-250">Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire la cartella delle risorse del sito di un'origine privata entro la rete CDN di Office 365.</span><span class="sxs-lookup"><span data-stu-id="67835-250">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site assets folder as a private origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- <span data-ttu-id="67835-251">Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire la cartella di pagine del sito di un'origine privata entro la rete CDN di Office 365.</span><span class="sxs-lookup"><span data-stu-id="67835-251">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site pages folder as a private origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- <span data-ttu-id="67835-252">Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire la cartella di immagini pubblicazione come un'origine privata entro la rete CDN di Office 365.</span><span class="sxs-lookup"><span data-stu-id="67835-252">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the publishing images folder as a private origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

    <span data-ttu-id="67835-253">Per ulteriori informazioni sulla sintassi e questo comando, vedere [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="67835-253">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
    
    <span data-ttu-id="67835-p132">Dopo aver eseguito il comando, il sistema Sincronizza la configurazione nel datacenter. Questa operazione richiede 15 minuti.</span><span class="sxs-lookup"><span data-stu-id="67835-p132">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
    
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a><span data-ttu-id="67835-256">Esempio: Configurazione di un'origine privata per una raccolta siti per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="67835-256">Example: Configure a private origin for a site collection for SharePoint Online</span></span>
<span data-ttu-id="67835-257"><a name="ExamplePrivateOriginSiteCollection"> </a></span><span class="sxs-lookup"><span data-stu-id="67835-257"></span></span>

<span data-ttu-id="67835-p133">Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire una raccolta siti come un'origine privata entro la rete CDN di Office 365. Per esempio</span><span class="sxs-lookup"><span data-stu-id="67835-p133">Use the **Add-SPOTenantCdnOrigin** cmdlet to define a site collection as a private origin within the Office 365 CDN. For example,</span></span> 
  
```
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="67835-260">Per ulteriori informazioni sulla sintassi e questo comando, vedere [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="67835-260">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="67835-p134">Dopo aver eseguito il comando, il sistema Sincronizza la configurazione nel datacenter. Questa operazione richiede 15 minuti.</span><span class="sxs-lookup"><span data-stu-id="67835-p134">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
  
## <a name="manage-the-office-365-cdn"></a><span data-ttu-id="67835-263">Gestione di Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="67835-263">Manage the Office 365 CDN</span></span>
<span data-ttu-id="67835-264"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="67835-264"></span></span>

<span data-ttu-id="67835-265">Dopo aver configurato la rete CDN, è possibile apportare modifiche alla configurazione quando si aggiorna il contenuto o in base alle esigenze, come descritto in questa sezione.</span><span class="sxs-lookup"><span data-stu-id="67835-265">Once you've set up the CDN, you can make changes to your configuration as you update content or as your needs change, as described in this section.</span></span>
  
### <a name="to-add-update-or-remove-assets-from-the-office-365-cdn"></a><span data-ttu-id="67835-266">Per aggiungere, aggiornare o rimuovere risorse dalla rete CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="67835-266">To add, update, or remove assets from the Office 365 CDN</span></span>
<span data-ttu-id="67835-267"><a name="Office365CDNforSPOaddremoveasset"> </a></span><span class="sxs-lookup"><span data-stu-id="67835-267"></span></span>

<span data-ttu-id="67835-p135">Dopo aver completato i passaggi di installazione, è possibile aggiungere nuove risorse e aggiornare o rimuovere le risorse esistenti, ogni volta che si desidera. Per le risorse in una raccolta SharePoint identificato come origine o solo apportare le modifiche. Se si aggiunge una nuova risorsa, è disponibile attraverso la rete CDN immediatamente. Tuttavia, se si aggiorna il bene, richiede un massimo di 15 minuti per la nuova copia la propagazione e saranno disponibili nella rete CDN.</span><span class="sxs-lookup"><span data-stu-id="67835-p135">Once you've completed the setup steps, you can add new assets, and update or remove existing assets whenever you want. Just make your changes to the assets in the folder or SharePoint library that you identified as an origin. If you add a new asset, it is available through the CDN immediately. However, if you update the asset, it will take up to 15 minutes for the new copy to propagate and become available in the CDN.</span></span>
  
<span data-ttu-id="67835-p136">Se si desidera recuperare il percorso di origine, è possibile utilizzare il cmdlet **Get-SPOTenantCdnOrigins** . Per informazioni su come utilizzare questo cmdlet, vedere [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span><span class="sxs-lookup"><span data-stu-id="67835-p136">If you need to retrieve the location of the origin, you can use the **Get-SPOTenantCdnOrigins** cmdlet. For information on how to use this cmdlet, see [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span></span>
  
### <a name="to-remove-an-origin-from-the-office-365-cdn"></a><span data-ttu-id="67835-274">Per rimuovere un'origine dalla rete CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="67835-274">To remove an origin from the Office 365 CDN</span></span>
<span data-ttu-id="67835-275"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="67835-275"></span></span>

<span data-ttu-id="67835-p137">Se si desidera, è possibile rimuovere l'accesso a una cartella o una raccolta SharePoint identificato come origine. A tale scopo, utilizzare il cmdlet **Remove-SPOTenantCdnOrigin** . Per informazioni su come utilizzare questo cmdlet, vedere [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span><span class="sxs-lookup"><span data-stu-id="67835-p137">If you need to, you can remove access to a folder or SharePoint library that you identified as an origin. To do this, use the **Remove-SPOTenantCdnOrigin** cmdlet. For information on how to use this cmdlet, see [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span></span>
  
### <a name="to-modify-an-origin-in-the-office-365-cdn"></a><span data-ttu-id="67835-279">Per modificare un'origine di rete CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="67835-279">To modify an origin in the Office 365 CDN</span></span>
<span data-ttu-id="67835-280"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="67835-280"></span></span>

<span data-ttu-id="67835-p138">È possibile modificare un'origine che sono stati creati. In realtà, rimuovere l'origine e quindi aggiungere uno nuovo. Per ulteriori informazioni, vedere [per rimuovere un'origine dalla rete CDN Office 365](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) e [per aggiungere un'origine per le risorse](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span><span class="sxs-lookup"><span data-stu-id="67835-p138">You can't modify an origin you've created. Instead, remove the origin and then add a new one. For more information, see [To remove an origin from the Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) and [To add an origin for your assets](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span></span>
  
### <a name="to-disable-the-office-365-cdn"></a><span data-ttu-id="67835-284">Per disabilitare la rete CDN di Office 365</span><span class="sxs-lookup"><span data-stu-id="67835-284">To disable the Office 365 CDN</span></span>
<span data-ttu-id="67835-285"><a name="Office365CDNforSPODisable"> </a></span><span class="sxs-lookup"><span data-stu-id="67835-285"></span></span>

<span data-ttu-id="67835-p139">Utilizzare il cmdlet **Set-SPOTenantCdnEnabled** per disabilitare la rete CDN per l'organizzazione. Se si dispone di entrambe le origini pubbliche e private abilitate per la rete CDN, è necessario eseguire il cmdlet due volte come illustrato negli esempi seguenti.</span><span class="sxs-lookup"><span data-stu-id="67835-p139">Use the **Set-SPOTenantCdnEnabled** cmdlet to disable the CDN for your organization. If you have both the public and private origins enabled for the CDN, you need to run the cmdlet twice as shown in the following examples.</span></span> 
  
<span data-ttu-id="67835-288">Per disabilitare l'uso delle origini pubbliche nella rete CDN, in Windows Powershell per SharePoint Online, immettere il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="67835-288">To disable use of public origins in the CDN, in Windows Powershell for SharePoint Online, enter the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

<span data-ttu-id="67835-289">Per disabilitare l'uso delle origini di rete CDN private, immettere il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="67835-289">To disable use of the private origins in the CDN, enter the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

<span data-ttu-id="67835-290">Per ulteriori informazioni su questo cmdlet, vedere [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="67835-290">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
## <a name="troubleshooting-your-office-365-cdn-configuration"></a><span data-ttu-id="67835-291">Risoluzione dei problemi relativi alla configurazione di Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="67835-291">Troubleshooting your Office 365 CDN configuration</span></span>
<span data-ttu-id="67835-292"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="67835-292"></span></span>

<span data-ttu-id="67835-p140">Il punto finale non immediatamente sarà disponibile per l'utilizzo, come il tempo per la registrazione per la propagazione attraverso la rete CDN. Configurazione richiede 15 minuti.</span><span class="sxs-lookup"><span data-stu-id="67835-p140">The endpoint will not immediately be available for use, as it takes time for the registration to propagate through the CDN. Configuration takes 15 minutes.</span></span>
  

