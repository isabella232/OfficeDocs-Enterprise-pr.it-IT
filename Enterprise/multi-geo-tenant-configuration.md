---
title: Configurazione del tenant multi-geografico di OneDrive for Business
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Informazioni sulla configurazione di OneDrive for Business Multi-Geo
ms.openlocfilehash: 561025efc38199f3a92e228d5414a28df6eb12f0
ms.sourcegitcommit: 92d16c0926e4be3fd493fe9b4eb317fb54996bca
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2018
ms.locfileid: "21549967"
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="9c5d6-103">Configurazione del tenant multi-geografico di OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="9c5d6-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="9c5d6-p101">Prima di configurare il tenant di OneDrive for Business Multi-Geo, assicurarsi di aver letto [Pianificazione di OneDrive for Business Multi-Geo](plan-for-multi-geo.md). Per seguire al procedura descritta in questo articolo, è necessario un elenco di tutte le posizioni che si desidera abilitare e testare gli utenti per i quali effettuare il provisioning di tali posizioni.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the locations that you want to enable and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="9c5d6-106">Aggiungere la funzionalità Multi-Geo nel piano di Office 365 del tenant</span><span class="sxs-lookup"><span data-stu-id="9c5d6-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="9c5d6-p102">Per usare OneDrive for Business Multi-Geo, è necessario il piano _Funzionalità Multi-Geo in Office 365_. Lavorare con il team dell'account per aggiungere questo piano al tenant. Il team dell'account connetterà l'utente con lo specialista delle licenza appropriato per far configurare il tenant.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="9c5d6-p103">Tenere presente che il piano _Funzionalità Multi-Geo in Office 365_ è un piano di servizio a livello di utente. È necessaria una licenza per ogni utente da ospitare in una posizione satellite. È possibile aggiungere più licenze nel tempo man mano che si aggiungono utenti alle posizioni satellite.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="9c5d6-113">Una volta che nel tenant è stato effettuato il provisioning del piano _Funzionalità Multi-Geo in Office 365_, la scheda **Posizioni geografiche** diventerà disponibile nell'[interfaccia di amministrazione di OneDrive](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="9c5d6-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a><span data-ttu-id="9c5d6-114">Impostare i percorsi dati consentiti nel tenant</span><span class="sxs-lookup"><span data-stu-id="9c5d6-114">Set the Allowed Data Locations (ADL) to your tenant</span></span>

<span data-ttu-id="9c5d6-p104">È necessario impostare un percorso dati consentito per SharePoint per ogni posizione geografica in cui si vuole usare OneDrive for Business. Le posizioni geografiche disponibili sono visualizzate nella tabella seguente:</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p104">You must set an Allowed Data Location for SharePoint for each geo-location where you want to use OneDrive for Business. Available geo-locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="9c5d6-117"><strong>Posizione</strong></span><span class="sxs-lookup"><span data-stu-id="9c5d6-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="9c5d6-118"><strong>Codice</strong></span><span class="sxs-lookup"><span data-stu-id="9c5d6-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="9c5d6-119">Asia-Pacifico</span><span class="sxs-lookup"><span data-stu-id="9c5d6-119">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="9c5d6-120">APC</span><span class="sxs-lookup"><span data-stu-id="9c5d6-120">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9c5d6-121">Australia</span><span class="sxs-lookup"><span data-stu-id="9c5d6-121">Australia</span></span></td>
<td align="left"><span data-ttu-id="9c5d6-122">AUS</span><span class="sxs-lookup"><span data-stu-id="9c5d6-122">AUS</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9c5d6-123">Canada</span><span class="sxs-lookup"><span data-stu-id="9c5d6-123">Canada</span></span></td>
<td align="left"><span data-ttu-id="9c5d6-124">CAN</span><span class="sxs-lookup"><span data-stu-id="9c5d6-124">CAN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9c5d6-125">Europa/Medio Oriente/Africa</span><span class="sxs-lookup"><span data-stu-id="9c5d6-125">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="9c5d6-126">EUR</span><span class="sxs-lookup"><span data-stu-id="9c5d6-126">EUR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9c5d6-127">Francia</span><span class="sxs-lookup"><span data-stu-id="9c5d6-127">France</span></span></td>
<td align="left"><span data-ttu-id="9c5d6-128">FRA</span><span class="sxs-lookup"><span data-stu-id="9c5d6-128">FRA</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9c5d6-129">Giappone</span><span class="sxs-lookup"><span data-stu-id="9c5d6-129">Japan</span></span></td>
<td align="left"><span data-ttu-id="9c5d6-130">JPN</span><span class="sxs-lookup"><span data-stu-id="9c5d6-130">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9c5d6-131">Corea</span><span class="sxs-lookup"><span data-stu-id="9c5d6-131">Korea</span></span></td>
<td align="left"><span data-ttu-id="9c5d6-132">KOR</span><span class="sxs-lookup"><span data-stu-id="9c5d6-132">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9c5d6-133">Nord America</span><span class="sxs-lookup"><span data-stu-id="9c5d6-133">North America</span></span></td>
<td align="left"><span data-ttu-id="9c5d6-134">NAM</span><span class="sxs-lookup"><span data-stu-id="9c5d6-134">NAM</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9c5d6-135">Regno Unito</span><span class="sxs-lookup"><span data-stu-id="9c5d6-135">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="9c5d6-136">GBR</span><span class="sxs-lookup"><span data-stu-id="9c5d6-136">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="9c5d6-137">Per aggiungere una posizione geografica satellite</span><span class="sxs-lookup"><span data-stu-id="9c5d6-137">To add a satellite geo location</span></span>

1. <span data-ttu-id="9c5d6-138">Aprire l'[interfaccia di amministrazione di OneDrive](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="9c5d6-138">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="9c5d6-139">Andare alla scheda **Posizioni geografiche**.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-139">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="9c5d6-140">Fare clic su **Aggiungi percorso**.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-140">Click **Add location**.</span></span>

4. <span data-ttu-id="9c5d6-141">Selezionare la posizione che si desidera aggiungere, quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-141">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="9c5d6-142">Digitare il dominio da usare con la posizione geografica, quindi fare clic su **Aggiungi**. </span><span class="sxs-lookup"><span data-stu-id="9c5d6-142">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="9c5d6-143">Fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-143">Click **Close**.</span></span>

<span data-ttu-id="9c5d6-p105">Il provisioning potrebbe richiedere dalle poche alle 72 ore, a seconda delle dimensioni del tenant. Al termine del provisioning di una posizione satellite, verrà inviato un messaggio di posta elettronica di conferma. Quando la nuova posizione geografica diventa blu sulla mappa nella scheda **Posizioni geografiche** nell'interfaccia di amministrazione di OneDrive, è possibile procedere per impostare il percorso dati preferito dell'utente su tale posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo-location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="9c5d6-p106">La nuova posizione geografica satellite sarà configurata con le impostazioni predefinite. In questo modo sarà possibile configurare tale posizione geografica in base alle proprie esigenze di conformità locale.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p106">Your new satellite geo location will be set up with default settings. This will allow you to configure that geo location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="9c5d6-149">Impostazione del percorso dati preferito dell'utente</span><span class="sxs-lookup"><span data-stu-id="9c5d6-149">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="9c5d6-p107">Dopo aver abilitato i percorsi dati necessari, è possibile aggiornare gli account utente per utilizzare il percorso dati appropriato. Si consiglia di impostare un percorso dati preferito per ogni utente, anche se l'utente si trova nel percorso dati predefinito.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p107">Once you enable the needed data locations, you can update your user accounts to use the appropriate data location. We recommend that you set a preferred data location for every user, even if that user is staying in the default data location.</span></span>

> [!TIP]
> <span data-ttu-id="9c5d6-152">Si consiglia di iniziare le convalide con un utente di test o con un gruppo limitato di utenti prima di distribuire le funzionalità Multi-Geo in tutta l'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-152">We recommend that you begin validations with a test user or small group of users before rolling out Multi-Geo capabilities to your broader organization.</span></span>

<span data-ttu-id="9c5d6-p108">In AAD sono disponibili due tipi di oggetti utente: gli utenti solo cloud e gli utenti sincronizzati. Seguire le istruzioni appropriate per il tipo di utente.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="9c5d6-155">Sincronizzare il percorso dati preferito dell'utente utilizzando AD Connect</span><span class="sxs-lookup"><span data-stu-id="9c5d6-155">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="9c5d6-p109">Se gli utenti dell'organizzazione vengono sincronizzati da un sistema Active Directory (AD) locale in Azure Active Directory (AAD), il relativo PreferredDataLocation deve essere popolato in Active Directory e sincronizzati in AAD. Seguire la procedura in [Sincronizzazione di Azure AD Connect: modificare la configurazione predefinita](https://docs.microsoft.com/it-IT/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) per configurare la sincronizzazione del percorso dati preferito da AD locale in AAD.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p109">If your company’s users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/it-IT/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) to configure Preferred Data Location sync from on-premises AD to AAD.</span></span>

<span data-ttu-id="9c5d6-158">È consigliabile includere l'impostazione del percorso dati preferito dell'utente nel flusso di lavoro di creazione di un utente standard.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-158">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9c5d6-p110">Per i nuovi utenti per cui non è stato eseguito il provisioning di OneDrive, attendere almeno 24 ore dopo la sincronizzazione del percorso dati preferito di un utente in ADD affinché le modifiche si propaghino prima che l'utente possa accedere a OneDrive for Business. Impostare il percorso dati preferito prima che l'utente acceda a l provisioning del proprio OneDrive for Business garantisce che il provisionig del nuovo OneDrive utente avvenga nella posizione corretta).</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to AAD for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="9c5d6-161">Impostazione del percorso dati preferito per utenti solo cloud</span><span class="sxs-lookup"><span data-stu-id="9c5d6-161">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="9c5d6-162">Se gli utenti dell'azienda non vengono sincronizzati da un sistema Active Directory (AD) locale ad Azure Active Directory (AAD), il che significa che sono stati creati in Office 365 o AAD, allora il percorso dati preferito deve essere impostato tramite AAD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-162">If your company’s users are not synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), meaning they are created in Office 365 or AAD, then PDL must be set using AAD PowerShell.</span></span>

<span data-ttu-id="9c5d6-p111">Le procedure descritte in questa sezione richiedono il [Modulo di Microsoft Azure Active Directory per il modulo di Windows PowerShell ](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Se AAD PowerShell è già installato, assicurarsi di effettuare l'aggiornamento alla versione più recente.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have AAD PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="9c5d6-165">Aprire il modulo Microsoft Azure Active Directory per Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-165">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="9c5d6-166">Eseguire `Connect-MsolService` e inserire le credenziali dell'amministratore globale del tenant.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-166">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="9c5d6-p112">Usare il cmdlet [Set-MsolUser](https://docs.microsoft.com/it-IT/powershell/msonline/v1/set-msoluser) per impostare il percorso dati preferito per ognuno degli utenti. Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p112">Use the [Set-MsolUser](https://docs.microsoft.com/it-IT/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="9c5d6-p113">È possibile controllare per verificare che il percorso dati preferito sia stato aggiornato correttamente con il cmdlet Get-MsolUser. Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

<span data-ttu-id="9c5d6-171">È consigliabile includere l'impostazione del percorso dati preferito dell'utente nel flusso di lavoro di creazione di un utente standard.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-171">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9c5d6-p114">Per i nuovi utenti per cui non è stato eseguito il provisioning di OneDrive, attendere almeno 24 ore dopo l'impostazione del percorso dati preferito di un utente affinché le modifiche si propaghino prima che l'utente possa accedere a SharePoint OneDrive. Impostare il percorso dati preferito prima che l'utente acceda a l provisioning del proprio OneDrive for Business garantisce che il provisionig del nuovo OneDrive utente avvenga nella posizione corretta).</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to SharePoint OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="9c5d6-174">Provisioning di OneDrive e l'effetto del percorso dati preferito</span><span class="sxs-lookup"><span data-stu-id="9c5d6-174">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="9c5d6-p115">Se l'utente ha già creato un sito OneDrive nel tenant, impostando il percorso dati preferito non verrà spostato automaticamente nel OneDrive esistente. Per spostare OneDrive di un utente, vedere [Spostamento geografico di OneDrive for Business](move-onedrive-between-geo-locations.md) e seguire le istruzioni sullo spostamento di OneDrive tra diverse posizioni geografiche.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="9c5d6-177">Se l'utente non dispone di un sito di OneDrive all'interno del tenant, il provisioning di OneDrive verrà eseguito in base al valore del percorso dati preferito, presupponendo che il percorso dati preferito dell'utente corrisponda a uno dei percorsi dati consentiti della società (ADL).</span><span class="sxs-lookup"><span data-stu-id="9c5d6-177">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s allowed data locations (ADLs).</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="9c5d6-178">Configurazione della ricerca multi-geografica</span><span class="sxs-lookup"><span data-stu-id="9c5d6-178">Configuring Multi-Geo search</span></span>

<span data-ttu-id="9c5d6-179">Il tenant multi-geografico aggregherà le funzionalità di ricerca consentendo a una query di ricerca di restituire risultati da una qualsiasi posizione nel tenant.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-179">Your Multi-Geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="9c5d6-180">Per impostazione predefinita, le ricerche da questi punti di ingresso restituiranno risultati aggregati, anche se ogni indice di ricerca si trova nella relativa posizione geografica rilevante:</span><span class="sxs-lookup"><span data-stu-id="9c5d6-180">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="9c5d6-181">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="9c5d6-181">OneDrive for business</span></span>

- <span data-ttu-id="9c5d6-182">Delve</span><span class="sxs-lookup"><span data-stu-id="9c5d6-182">Delve</span></span>

- <span data-ttu-id="9c5d6-183">Home page di SharePoint</span><span class="sxs-lookup"><span data-stu-id="9c5d6-183">SharePoint Home</span></span>

- <span data-ttu-id="9c5d6-184">Centro ricerche</span><span class="sxs-lookup"><span data-stu-id="9c5d6-184">Search Center</span></span>

<span data-ttu-id="9c5d6-185">Inoltre, le funzionalità della ricerca multi-geografica possono essere configurate per applicazioni di ricerca personalizzate che usano l'API Ricerca di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-185">Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="9c5d6-186">Consultare [Configurare la ricerca per OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) per istruzioni che includono limitazioni e differenze.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-186">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="9c5d6-187">Convalida della configurazione di OneDrive for Business Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="9c5d6-187">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="9c5d6-p116">Di seguito sono illustrati alcuni casi d'uso che si potrebbe voler includere nel piano di convalida prima di distribuire ampiamente OneDrive for Business Multi-Geo nell'azienda. Dopo aver completato questi test ed eventuali casi d'uso aggiuntivi rilevanti per la propria azienda, è possibile scegliere di continuare ad aggiungere utenti al gruppo pilota iniziale.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="9c5d6-190">**OneDrive for Business**</span><span class="sxs-lookup"><span data-stu-id="9c5d6-190">**OneDrive for Business**</span></span>

<span data-ttu-id="9c5d6-p117">Selezionare OneDrive dall'icona di avvio dell'app di Office 365 e verificare di essere automaticamente indirizzati alla posizione geografica appropriata per l'utente , in base al percorso dati preferito dell'utente. OneDrive for Business ora inizia il provisioning in tale posizione. Al termine, provare a caricare e a scaricare alcuni documenti.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo-location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="9c5d6-194">**App OneDrive per dispositivi mobili**</span><span class="sxs-lookup"><span data-stu-id="9c5d6-194">**OneDrive Mobile App**</span></span>

<span data-ttu-id="9c5d6-p118">Accedere all'app per dispositivi mobili di OneDrive con le credenziali dell'account di prova. Verificare che sia possibile visualizzare i file di OneDrive for Business e di poterli usare dal dispositivo mobile.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="9c5d6-197">**Client di sincronizzazione di OneDrive**</span><span class="sxs-lookup"><span data-stu-id="9c5d6-197">**OneDrive sync client**</span></span>

<span data-ttu-id="9c5d6-p119">Confermare che il client di sincronizzazione di OneDrive rilevi automaticamente la posizione geografica di OneDrive for Business all'accesso. Se serve scaricare il client di sincronizzazione, è possibile fare clic su **Sincronizza** nella raccolta di OneDrive.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo-location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="9c5d6-200">**Applicazioni di Office**</span><span class="sxs-lookup"><span data-stu-id="9c5d6-200">**Office applications**</span></span>

<span data-ttu-id="9c5d6-p120">Verificare di riuscire ad accedere a OneDrive for Business effettuando l'accesso da un'applicazione Office, come Word. Aprire l'applicazione Office e selezionare "OneDrive – <TenantName>". Office rileverà la posizione di OneDrive e mostrerà i file che possono essere aperti.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="9c5d6-204">**Condivisione**</span><span class="sxs-lookup"><span data-stu-id="9c5d6-204">**Sharing**</span></span>

<span data-ttu-id="9c5d6-p121">Provare a condividere i file di OneDrive. Verificare che lo strumento di selezione delle  persone mostri tutti gli utenti online di SharePoint indipendentemente dalla loro posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="9c5d6-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo-location.</span></span>
