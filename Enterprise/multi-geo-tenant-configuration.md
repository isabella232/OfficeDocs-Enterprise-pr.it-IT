---
title: OneDrive per la configurazione tenant Business Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Informazioni su come configurare OneDrive per Business Multi-Geo.
ms.openlocfilehash: 56268acd319684ecb713e674b8accbe311d08dce
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="de7b5-103">OneDrive per la configurazione tenant Business Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="de7b5-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="de7b5-p101">Prima di configurare il tenant di OneDrive per Business Multi-Geo, è necessario che leggere [Plan for OneDrive per Business Multi-Geo](plan-for-multi-geo.md). Per eseguire la procedura descritta in questo articolo, è necessario un elenco di utenti di test che si desidera eseguire il provisioning per i percorsi e i percorsi che si desidera abilitare.</span><span class="sxs-lookup"><span data-stu-id="de7b5-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the locations that you want to enable and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="de7b5-106">Aggiungere la funzionalità Multi-Geo nel piano di Office 365 tenant di</span><span class="sxs-lookup"><span data-stu-id="de7b5-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="de7b5-p102">Per utilizzare OneDrive per Business Multi-Geo, è necessario pianificare _Funzionalità Multi-Geo in Office 365_ . Lavorare con il team di account da aggiungere questo piano per il tenant. Il team di account verrà la connessione con lo specialista di licenze appropriato e ottenere il tenant configurato.</span><span class="sxs-lookup"><span data-stu-id="de7b5-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="de7b5-p103">Si noti che il piano di _Funzionalità Multi-Geo in Office 365_ è un piano di servizio a livello utente. È necessaria una licenza per ogni utente che si desidera ospitare in una posizione satellitare. È possibile aggiungere altre licenze nel tempo mentre si aggiungono utenti nelle posizioni satellitari.</span><span class="sxs-lookup"><span data-stu-id="de7b5-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="de7b5-113">Una volta tenant è stato fornito con il piano di _Funzionalità Multi-Geo in Office 365_ , la scheda **percorsi Geo** diventerà disponibile nell' [interfaccia di amministrazione di OneDrive](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="de7b5-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a><span data-ttu-id="de7b5-114">Impostare consentito dati posizioni (ADL) per il tenant</span><span class="sxs-lookup"><span data-stu-id="de7b5-114">Set the Allowed Data Locations (ADL) to your tenant</span></span>

<span data-ttu-id="de7b5-p104">È necessario impostare una posizione di dati consentita per SharePoint per ogni località geografica cui si desidera utilizzare OneDrive for Business. Località geografica disponibili sono illustrate nella tabella seguente:</span><span class="sxs-lookup"><span data-stu-id="de7b5-p104">You must set an Allowed Data Location for SharePoint for each geo-location where you want to use OneDrive for Business. Available geo-locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="de7b5-117"><strong>Percorso</strong></span><span class="sxs-lookup"><span data-stu-id="de7b5-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="de7b5-118"><strong>Codice</strong></span><span class="sxs-lookup"><span data-stu-id="de7b5-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="de7b5-119">Nord America</span><span class="sxs-lookup"><span data-stu-id="de7b5-119">North America</span></span></td>
<td align="left"><span data-ttu-id="de7b5-120">NOME</span><span class="sxs-lookup"><span data-stu-id="de7b5-120">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="de7b5-121">Europa / Allinea al centro est / Africa</span><span class="sxs-lookup"><span data-stu-id="de7b5-121">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="de7b5-122">EUR</span><span class="sxs-lookup"><span data-stu-id="de7b5-122">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="de7b5-123">Asia-Pacifico</span><span class="sxs-lookup"><span data-stu-id="de7b5-123">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="de7b5-124">APC</span><span class="sxs-lookup"><span data-stu-id="de7b5-124">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="de7b5-125">Australia</span><span class="sxs-lookup"><span data-stu-id="de7b5-125">Australia</span></span></td>
<td align="left"><span data-ttu-id="de7b5-126">AUSTRALIA</span><span class="sxs-lookup"><span data-stu-id="de7b5-126">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="de7b5-127">Giappone</span><span class="sxs-lookup"><span data-stu-id="de7b5-127">Japan</span></span></td>
<td align="left"><span data-ttu-id="de7b5-128">GIAPPONESE</span><span class="sxs-lookup"><span data-stu-id="de7b5-128">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="de7b5-129">Canada</span><span class="sxs-lookup"><span data-stu-id="de7b5-129">Canada</span></span></td>
<td align="left"><span data-ttu-id="de7b5-130">POSSIBILE</span><span class="sxs-lookup"><span data-stu-id="de7b5-130">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="de7b5-131">Regno Unito</span><span class="sxs-lookup"><span data-stu-id="de7b5-131">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="de7b5-132">GBR</span><span class="sxs-lookup"><span data-stu-id="de7b5-132">GBR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="de7b5-133">Corea</span><span class="sxs-lookup"><span data-stu-id="de7b5-133">Korea</span></span></td>
<td align="left"><span data-ttu-id="de7b5-134">(COREANO)</span><span class="sxs-lookup"><span data-stu-id="de7b5-134">KOR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="de7b5-135">Per aggiungere una posizione geografica satellitari</span><span class="sxs-lookup"><span data-stu-id="de7b5-135">To add a satellite geo location</span></span>

1. <span data-ttu-id="de7b5-136">Aprire l' [interfaccia di amministrazione di OneDrive](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="de7b5-136">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="de7b5-137">Passare alla scheda **Geo predefinite** .</span><span class="sxs-lookup"><span data-stu-id="de7b5-137">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="de7b5-138">Fare clic su **Aggiungi percorso**.</span><span class="sxs-lookup"><span data-stu-id="de7b5-138">Click **Add location**.</span></span>

4. <span data-ttu-id="de7b5-139">Selezionare il percorso che si desidera aggiungere e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="de7b5-139">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="de7b5-140">Digitare il dominio che si desidera utilizzare con la posizione geografica e quindi fare clic su **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="de7b5-140">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="de7b5-141">Fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="de7b5-141">Click **Close**.</span></span>

<span data-ttu-id="de7b5-p105">Provisioning potrebbero richiedere da pochi ore a 72 ore, a seconda delle dimensioni del tenant. Una volta completato il provisioning di una posizione satellitare, si riceverà una conferma di posta elettronica. Quando viene visualizzata nella nuova posizione geografica in blu nella mappa nella scheda **percorsi Geo** nell'interfaccia di amministrazione OneDrive, è possibile procedere impostare il percorso preferito dati degli utenti a tale posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="de7b5-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo-location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="de7b5-p106">La nuova posizione geografica satellitari configurerà con le impostazioni predefinite. In questo modo è possibile configurare tale posizione geografica in base alle proprie esigenze di conformità locale.</span><span class="sxs-lookup"><span data-stu-id="de7b5-p106">Your new satellite geo location will be set up with default settings. This will allow you to configure that geo location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="de7b5-147">Impostazione della posizione preferita dati degli utenti</span><span class="sxs-lookup"><span data-stu-id="de7b5-147">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="de7b5-p107">Una volta che si abilita le posizioni dei dati necessarie, è possibile aggiornare gli account utente per utilizzare il percorso di dati appropriato. Si consiglia di impostare un percorso dati preferita per tutti gli utenti, anche se l'utente è soggiorno nel percorso dei dati predefinito.</span><span class="sxs-lookup"><span data-stu-id="de7b5-p107">Once you enable the needed data locations, you can update your user accounts to use the appropriate data location. We recommend that you set a preferred data location for every user, even if that user is staying in the default data location.</span></span>

> [!TIP]
> <span data-ttu-id="de7b5-150">È consigliabile iniziare convalida con un utente di test o di un piccolo gruppo di utenti prima di implementare le funzionalità Multi-Geo nell'organizzazione più ampia.</span><span class="sxs-lookup"><span data-stu-id="de7b5-150">We recommend that you begin validations with a test user or small group of users before rolling out Multi-Geo capabilities to your broader organization.</span></span>

<span data-ttu-id="de7b5-p108">AAD sono disponibili due tipi di oggetti utente: cloud solo gli utenti e gli utenti sincronizzati. Seguire le istruzioni appropriate per il tipo di utente.</span><span class="sxs-lookup"><span data-stu-id="de7b5-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="de7b5-153">Sincronizzazione preferito percorso dell'utente dati tramite la connessione Active Directory</span><span class="sxs-lookup"><span data-stu-id="de7b5-153">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="de7b5-p109">Se gli utenti della società vengono sincronizzati da un sistema di Active Directory (AD) locale per Azure Active Directory (AAD), le PreferredDataLocation deve essere popolata in Active Directory e sincronizzati con AAD. Attenersi al processo di [sincronizzazione di Azure Active Directory Connect: apportare una modifica alla configurazione predefinita](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) configurare preferito della sincronizzazione di percorso dati in Active Directory locale per AAD.</span><span class="sxs-lookup"><span data-stu-id="de7b5-p109">If your company’s users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) to configure Preferred Data Location sync from on-premises AD to AAD.</span></span>

<span data-ttu-id="de7b5-156">È consigliabile includere l'impostazione percorso dati preferito dell'utente come parte del flusso di lavoro creazione utente standard.</span><span class="sxs-lookup"><span data-stu-id="de7b5-156">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="de7b5-p110">Per i nuovi utenti con alcun OneDrive il provisioning, attendere almeno 24 ore dopo PDL dell'utente viene sincronizzato con AAD le modifiche di propagare prima che l'utente accede a OneDrive for Business. (Impostazione dei dati Preferiti percorso prima che l'utente accede a fornire loro OneDrive for Business assicura di cui eseguire il provisioning nuovo OneDrive dell'utente nella posizione corretta.)</span><span class="sxs-lookup"><span data-stu-id="de7b5-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to AAD for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="de7b5-159">L'impostazione percorso dati preferito per il cloud solo gli utenti</span><span class="sxs-lookup"><span data-stu-id="de7b5-159">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="de7b5-160">Se gli utenti della società non sono sincronizzati da un sistema di Active Directory (AD) locale per Azure Active Directory (AAD), vale a dire che vengono creati in Office 365 o AAD, quindi PDL deve essere impostata utilizzando PowerShell AAD.</span><span class="sxs-lookup"><span data-stu-id="de7b5-160">If your company’s users are not synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), meaning they are created in Office 365 or AAD, then PDL must be set using AAD PowerShell.</span></span>

<span data-ttu-id="de7b5-p111">Le procedure descritte in questa sezione richiedono [Microsoft modulo Azure Active Directory Module per Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Se si dispone già di PowerShell AAD installati, accertarsi di aggiornare per la versione più recente.</span><span class="sxs-lookup"><span data-stu-id="de7b5-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have AAD PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="de7b5-163">Aprire il modulo di Microsoft Azure Active Directory per Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de7b5-163">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="de7b5-164">Eseguire `Connect-MsolService` e immettere le credenziali di amministratore globale per il tenant.</span><span class="sxs-lookup"><span data-stu-id="de7b5-164">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="de7b5-p112">Utilizzare il cmdlet [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) per impostare il percorso dei dati preferito per ogni utente. Per esempio:</span><span class="sxs-lookup"><span data-stu-id="de7b5-p112">Use the [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="de7b5-p113">È possibile controllare per verificare che il percorso dei dati preferito sia stato aggiornato in modo corretto utilizzando il cmdlet Get-MsolUser. Per esempio:</span><span class="sxs-lookup"><span data-stu-id="de7b5-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

<span data-ttu-id="de7b5-169">È consigliabile includere l'impostazione percorso dati preferito dell'utente come parte del flusso di lavoro creazione utente standard.</span><span class="sxs-lookup"><span data-stu-id="de7b5-169">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="de7b5-p114">Per i nuovi utenti con alcun OneDrive il provisioning, attendere almeno 24 ore dopo aver impostato le modifiche di propagare prima che l'utente accede a SharePoint OneDrive PDL dell'utente. (Impostazione dei dati Preferiti percorso prima che l'utente accede a fornire loro OneDrive for Business assicura di cui eseguire il provisioning nuovo OneDrive dell'utente nella posizione corretta.)</span><span class="sxs-lookup"><span data-stu-id="de7b5-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to SharePoint OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="de7b5-172">Il provisioning di tipo OneDrive e l'effetto di PDL</span><span class="sxs-lookup"><span data-stu-id="de7b5-172">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="de7b5-p115">Se l'utente dispone già di un sito di OneDrive creato nel tenant, l'impostazione loro PDL non passerà automaticamente loro OneDrive esistente. Per spostare OneDrive un utente, vedere [OneDrive for Business Geo spostare](move-onedrive-between-geo-locations.md) , segui le istruzioni in OneDrive lo spostamento tra le posizioni geo.</span><span class="sxs-lookup"><span data-stu-id="de7b5-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="de7b5-175">Se l'utente non dispone di un sito di OneDrive nel tenant, OneDrive eseguire il provisioning per essi in base al valore PDL supponendo che PDL per l'utente corrispondente a uno dei percorsi dei dati consentiti dell'azienda (ADLs).</span><span class="sxs-lookup"><span data-stu-id="de7b5-175">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s allowed data locations (ADLs).</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="de7b5-176">Configurazione della ricerca Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="de7b5-176">Configuring Multi-Geo search</span></span>

<span data-ttu-id="de7b5-177">Tenant Multi-Geo avranno funzionalità di ricerca aggregazione che consente una query di ricerca per restituire risultati da qualsiasi posizione all'interno del tenant.</span><span class="sxs-lookup"><span data-stu-id="de7b5-177">Your Multi-Geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="de7b5-178">Per impostazione predefinita, le ricerche di questi punti di ingresso restituirà risultati aggregati, anche se ogni indice di ricerca si trova all'interno di posizione geografica pertinenti:</span><span class="sxs-lookup"><span data-stu-id="de7b5-178">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="de7b5-179">OneDrive per aziende</span><span class="sxs-lookup"><span data-stu-id="de7b5-179">OneDrive for business</span></span>

- <span data-ttu-id="de7b5-180">Delve</span><span class="sxs-lookup"><span data-stu-id="de7b5-180">Delve</span></span>

- <span data-ttu-id="de7b5-181">Home page di SharePoint</span><span class="sxs-lookup"><span data-stu-id="de7b5-181">SharePoint Home</span></span>

- <span data-ttu-id="de7b5-182">Centro ricerche</span><span class="sxs-lookup"><span data-stu-id="de7b5-182">Search Center</span></span>

<span data-ttu-id="de7b5-183">Inoltre, le funzionalità di ricerca Multi-Geo è possibile configurare per le applicazioni di ricerca personalizzate che utilizzano l'API di ricerca di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="de7b5-183">Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="de7b5-184">Per istruzioni, incluse eventuali differenze e limitazioni, vedere [Configurare la ricerca di OneDrive per Business Multi-Geo](configure-search-for-multi-geo.md) .</span><span class="sxs-lookup"><span data-stu-id="de7b5-184">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="de7b5-185">Convalida di OneDrive for Business Multi-Geo configurazione</span><span class="sxs-lookup"><span data-stu-id="de7b5-185">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="de7b5-p116">Di seguito sono alcuni casi di utilizzo di base da includere nel piano di convalida prima largamente distribuzione OneDrive per Business Multi-Geo alla società. Dopo aver completato questi test e qualsiasi casi di utilizzo aggiuntivi rilevanti per l'azienda, è possibile procedere con l'aggiunta di utenti nel gruppo pilota iniziale.</span><span class="sxs-lookup"><span data-stu-id="de7b5-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="de7b5-188">**OneDrive for Business**</span><span class="sxs-lookup"><span data-stu-id="de7b5-188">**OneDrive for Business**</span></span>

<span data-ttu-id="de7b5-p117">Selezionare il servizio di avvio di applicazioni di Office 365 OneDrive e confermare che si verrà indirizzati automaticamente nella posizione geografica appropriata per l'utente, basato su PDL dell'utente. OneDrive for Business deve iniziare il provisioning in tale posizione. Una volta eseguito il, provare a caricare e scaricare alcuni documenti.</span><span class="sxs-lookup"><span data-stu-id="de7b5-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo-location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="de7b5-192">**Applicazione Mobile OneDrive**</span><span class="sxs-lookup"><span data-stu-id="de7b5-192">**OneDrive Mobile App**</span></span>

<span data-ttu-id="de7b5-p118">Accedere a App per dispositivi mobili di OneDrive con le credenziali dell'account di test. Verificare che è possibile visualizzare il OneDrive per i file di business e possono interagire con essi dal dispositivo mobile.</span><span class="sxs-lookup"><span data-stu-id="de7b5-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="de7b5-195">**Client di sincronizzazione OneDrive**</span><span class="sxs-lookup"><span data-stu-id="de7b5-195">**OneDrive sync client**</span></span>

<span data-ttu-id="de7b5-p119">Verificare che il client di sincronizzazione OneDrive rileva automaticamente le OneDrive for Business geo-percorso dopo l'accesso. Se è necessario scaricare il client di sincronizzazione, è possibile fare clic su **Sincronizza** nella libreria di OneDrive.</span><span class="sxs-lookup"><span data-stu-id="de7b5-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo-location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="de7b5-198">**Applicazioni di Office**</span><span class="sxs-lookup"><span data-stu-id="de7b5-198">**Office applications**</span></span>

<span data-ttu-id="de7b5-p120">Verificare di poter accedere a OneDrive for Business mediante l'accesso da un'applicazione di Office, ad esempio Word. Aprire Office dell'applicazione e seleziona "OneDrive- <TenantName>". Office rileva la posizione di OneDrive e visualizzare i file che è possibile aprire.</span><span class="sxs-lookup"><span data-stu-id="de7b5-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="de7b5-202">**Sharing**</span><span class="sxs-lookup"><span data-stu-id="de7b5-202">**Sharing**</span></span>

<span data-ttu-id="de7b5-p121">Provare a condividere i file di OneDrive. Verificare che la selezione utenti Mostra tutti gli utenti di online SharePoint indipendentemente dalla posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="de7b5-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo-location.</span></span>
