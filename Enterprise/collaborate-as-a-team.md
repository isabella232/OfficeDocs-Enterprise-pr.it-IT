---
title: Collaborare con gli ospiti in un team
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Informazioni su come collaborare con gli utenti in teams.
ms.openlocfilehash: 9a169e33a9cbd8f079966443bd3d830aa79f4971
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992415"
---
# <a name="collaborate-with-guests-in-a-team"></a><span data-ttu-id="5ae4d-103">Collaborare con gli ospiti in un team</span><span class="sxs-lookup"><span data-stu-id="5ae4d-103">Collaborate with guests in a team</span></span>

<span data-ttu-id="5ae4d-104">Se è necessario collaborare con gli utenti tra documenti, attività e conversazioni, è consigliabile utilizzare Microsoft teams.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-104">If you need to collaborate with guests across documents, tasks, and conversations, we recommend using Microsoft Teams.</span></span> <span data-ttu-id="5ae4d-105">Teams offre tutte le funzionalità di collaborazione disponibili in Office e SharePoint con chat persistente e un set di strumenti di collaborazione personalizzabile ed estensibile in un'esperienza utente unificata.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-105">Teams provides all of the collaboration features available in Office and SharePoint with persistent chat and a customizable and extensible set of collaboration tools in a unified user experience.</span></span>

<span data-ttu-id="5ae4d-106">In questo articolo verranno illustrati i passaggi di configurazione di Microsoft 365 necessari per configurare un team per la collaborazione con gli utenti.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a team for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="5ae4d-107">Impostazioni delle relazioni organizzative di Azure</span><span class="sxs-lookup"><span data-stu-id="5ae4d-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="5ae4d-108">La condivisione in Microsoft 365 è regolata al livello più alto dalle impostazioni delle relazioni organizzative in Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="5ae4d-109">Se la condivisione Guest è disabilitata o limitata in Azure AD, queste verranno sostituite da tutte le impostazioni di condivisione configurate in Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="5ae4d-110">Controllare le impostazioni delle relazioni organizzative per garantire che la condivisione con gli ospiti non sia bloccata.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Schermata della pagina delle impostazioni delle relazioni organizzative di Azure Active Directory](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="5ae4d-112">Per impostare le impostazioni delle relazioni organizzative</span><span class="sxs-lookup"><span data-stu-id="5ae4d-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="5ae4d-113">Accedere a Microsoft Azure all'indirizzo [https://portal.azure.com](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="5ae4d-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="5ae4d-114">Nel riquadro di spostamento a sinistra, fare clic su **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="5ae4d-115">Nel riquadro **Panoramica** fare clic su **relazioni organizzative**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="5ae4d-116">Nel riquadro **relazioni organizzative** fare clic su **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="5ae4d-117">Verificare che **gli amministratori e gli utenti del ruolo invitato ospite possano invitare** e che **i membri possano invitare** siano entrambi impostati su **Sì**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="5ae4d-118">Se sono state apportate modifiche, fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="5ae4d-119">Prendere nota delle impostazioni nella sezione **vincoli di collaborazione** .</span><span class="sxs-lookup"><span data-stu-id="5ae4d-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="5ae4d-120">Verificare che i domini degli utenti con cui si desidera collaborare non siano bloccati.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="teams-guest-access-settings"></a><span data-ttu-id="5ae4d-121">Impostazioni di accesso Guest Teams</span><span class="sxs-lookup"><span data-stu-id="5ae4d-121">Teams guest access settings</span></span>

<span data-ttu-id="5ae4d-122">I team dispongono di un'opzione Master di attivazione/disattivazione dell'accesso guest e di una serie di impostazioni disponibili per controllare gli utenti che possono eseguire in un team.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-122">Teams has a master on/off switch for guest access and a variety of settings available to control what guests can do in a team.</span></span> <span data-ttu-id="5ae4d-123">L'opzione master **consente all'accesso guest nei team** di essere **attiva** per l'accesso guest per il lavoro in teams.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-123">The master switch, **Allow guest access in Teams** must be **On** for guest access to work in Teams.</span></span>

<span data-ttu-id="5ae4d-124">Verificare che l'accesso Guest sia abilitato nei team e apportare eventuali adeguamenti alle impostazioni guest in base alle esigenze aziendali.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-124">Check to ensure that guest access is enabled in Teams and make any adjustment to the guest settings based on your business needs.</span></span> <span data-ttu-id="5ae4d-125">Tenere presente che queste impostazioni influiscono su tutti i team.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-125">Keep in mind that these settings affect all teams.</span></span>

![Schermata del disattivatore accesso Guest Teams](media/teams-guest-access-toggle-on.png)

<span data-ttu-id="5ae4d-127">Per impostare le impostazioni di accesso guest di Teams</span><span class="sxs-lookup"><span data-stu-id="5ae4d-127">To set Teams guest access settings</span></span>

1. <span data-ttu-id="5ae4d-128">Accedere all'interfaccia di amministrazione di Microsoft 365 all' [https://admin.microsoft.com](https://admin.microsoft.com)indirizzo.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-128">Log in to the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
2. <span data-ttu-id="5ae4d-129">Nella barra di spostamento a sinistra, fare clic su **Mostra tutto**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-129">In the left navigation, click **Show all**.</span></span>
3. <span data-ttu-id="5ae4d-130">In interfaccia di **Amministrazione**fare clic su **Team**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-130">Under **Admin centers**, click **Teams**.</span></span>
4. <span data-ttu-id="5ae4d-131">Nell'interfaccia di amministrazione di teams, nella barra di spostamento a sinistra, espandere **impostazioni a livello di organizzazione** e fare clic su **accesso Guest**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-131">In the Teams admin center, in the left navigation, expand **Org-wide settings** and click **Guest access**.</span></span>
5. <span data-ttu-id="5ae4d-132">Verificare che **Consenti accesso guest in teams** sia impostato **su**attivato.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-132">Ensure that **Allow guest access in Teams** is set to **On**.</span></span>
6. <span data-ttu-id="5ae4d-133">Apportare le modifiche desiderate alle impostazioni aggiuntive per gli ospiti e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-133">Make any desired changes to the additional guest settings, and then click **Save**.</span></span>

> [!NOTE]
> <span data-ttu-id="5ae4d-134">Dopo l'attivazione, potrebbero essere necessarie fino a ventiquattro ore affinché l'impostazione Guest teams diventi attiva.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-134">It may take up to twenty-four hours for the Teams guest setting to become active after you turn it on.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="5ae4d-135">Office 365 gruppi Guest Settings</span><span class="sxs-lookup"><span data-stu-id="5ae4d-135">Office 365 Groups guest settings</span></span>

<span data-ttu-id="5ae4d-136">Teams utilizza i gruppi di Office 365 per l'appartenenza al team.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-136">Teams uses Office 365 Groups for team membership.</span></span> <span data-ttu-id="5ae4d-137">È necessario che le impostazioni Guest dei gruppi di Office 365 siano attivate affinché l'accesso guest nei team funzioni.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-137">The Office 365 Groups guest settings must be turned on in order for guest access in Teams to work.</span></span>

![Schermata di Office 365 gruppi Guest Settings in Microsoft 365 Admin Center](media/office-365-groups-guest-settings.png)

<span data-ttu-id="5ae4d-139">Per impostare le impostazioni di Office 365 groups Guest</span><span class="sxs-lookup"><span data-stu-id="5ae4d-139">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="5ae4d-140">Nell'interfaccia di amministrazione di Microsoft 365, nel riquadro di spostamento a sinistra, espandere **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-140">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="5ae4d-141">Fare clic su **servizi & componenti**aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-141">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="5ae4d-142">Nell'elenco, fare clic su **gruppi di Office 365**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-142">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="5ae4d-143">Verificare che i membri del gruppo Consenti al di **fuori dell'organizzazione accedano al contenuto del gruppo** e che i proprietari del **gruppo aggiungano persone all'esterno dell'organizzazione ai gruppi di caselle di** controllo siano entrambe controllate.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-143">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="5ae4d-144">Se sono state apportate modifiche, fare clic su **Salva modifiche**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-144">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="5ae4d-145">Impostazioni di condivisione a livello di organizzazione di SharePoint</span><span class="sxs-lookup"><span data-stu-id="5ae4d-145">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="5ae4d-146">Affinché gli utenti dispongano dell'accesso ai file nei team, le impostazioni di condivisione a livello di organizzazione di SharePoint devono consentire la condivisione con gli utenti.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-146">In order for guests to have access to files in Teams, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="5ae4d-147">Le impostazioni a livello di organizzazione determinano le impostazioni disponibili per i singoli siti, inclusi i siti associati ai team.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-147">The organization-level settings determine what settings are available for individual sites, including sites associated with teams.</span></span> <span data-ttu-id="5ae4d-148">Le impostazioni del sito non possono essere più permissive rispetto alle impostazioni a livello di organizzazione.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-148">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="5ae4d-149">Se si desidera consentire la condivisione di file e cartelle con utenti anonimi, scegliere **nessuno**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-149">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="5ae4d-150">Se si desidera garantire che tutti gli utenti siano in grado di eseguire l'autenticazione, scegliere **clienti nuovi ed esistenti**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-150">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="5ae4d-151">Scegliere l'impostazione più permissiva che sarà necessaria per qualsiasi sito dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-151">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Schermata delle impostazioni di condivisione a livello di organizzazione di SharePoint](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="5ae4d-153">Per impostare le impostazioni di condivisione a livello di organizzazione di SharePoint</span><span class="sxs-lookup"><span data-stu-id="5ae4d-153">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="5ae4d-154">Nell'interfaccia di amministrazione di Microsoft 365, nella barra di spostamento a sinistra, in interfaccia di **Amministrazione**, fare clic su **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-154">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="5ae4d-155">Nell'interfaccia di amministrazione di SharePoint, nella barra di spostamento a sinistra, fare clic su **condivisione**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-155">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="5ae4d-156">Assicurarsi che la condivisione esterna per SharePoint sia impostata su **tutti gli utenti** o **gli ospiti nuovi e esistenti**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-156">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="5ae4d-157">Se sono state apportate modifiche, fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-157">If you made changes, click **Save**.</span></span>


## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="5ae4d-158">Impostazioni di collegamento predefinite a livello di organizzazione di SharePoint</span><span class="sxs-lookup"><span data-stu-id="5ae4d-158">SharePoint organization level default link settings</span></span>

<span data-ttu-id="5ae4d-159">Le impostazioni predefinite per il collegamento di file e cartelle determinano l'opzione di collegamento visualizzata all'utente per impostazione predefinita quando condividono un file o una cartella.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-159">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="5ae4d-160">Gli utenti possono modificare il tipo di collegamento in una delle altre opzioni prima della condivisione, se necessario.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-160">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="5ae4d-161">Tenere presente che questa impostazione ha effetto su tutti i team e i siti di SharePoint dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-161">Keep in mind that this setting affects all teams and SharePoint sites in your organization.</span></span>

<span data-ttu-id="5ae4d-162">Scegliere il tipo di collegamento selezionato per impostazione predefinita quando gli utenti condividono file e cartelle:</span><span class="sxs-lookup"><span data-stu-id="5ae4d-162">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="5ae4d-163">**Tutti gli utenti con il collegamento** : scegliere questa opzione se si prevede di condividere un gran quantità di file e cartelle in modo anonimo.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-163">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="5ae4d-164">Se si desidera consentire collegamenti a *tutti gli utenti* , ma sono preoccupati per la condivisione accidentale anonima, prendere in considerazione una delle altre opzioni come impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-164">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="5ae4d-165">Questo tipo di collegamento è disponibile solo se è stata abilitata la condivisione di **utenti** .</span><span class="sxs-lookup"><span data-stu-id="5ae4d-165">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="5ae4d-166">**Solo persone nell'organizzazione** : scegliere questa opzione se si prevede che la maggior parte della condivisione di file e cartelle sia con le persone all'interno dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-166">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="5ae4d-167">**Persone specifiche** : considerare questa opzione se si prevede di eseguire un sacco di condivisione di file e cartelle con gli utenti.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-167">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="5ae4d-168">Questo tipo di collegamento è compatibile con gli utenti e richiede l'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-168">This type of link works with guests and requires them to authenticate.</span></span>
 
![Schermata di impostazioni di condivisione di file e cartelle a livello di organizzazione di SharePoint](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="5ae4d-170">Per impostare le impostazioni dei collegamenti predefiniti a livello di organizzazione di SharePoint</span><span class="sxs-lookup"><span data-stu-id="5ae4d-170">To set the SharePoint organization level default link settings</span></span>

1. <span data-ttu-id="5ae4d-171">Passare alla pagina condivisione nell'interfaccia di amministrazione di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-171">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="5ae4d-172">In **collegamenti a file e cartelle**selezionare il collegamento di condivisione predefinito che si desidera utilizzare.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-172">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="5ae4d-173">Se sono state apportate modifiche, fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-173">If you made changes, click **Save**.</span></span>

## <a name="create-a-team"></a><span data-ttu-id="5ae4d-174">Creare un team</span><span class="sxs-lookup"><span data-stu-id="5ae4d-174">Create a team</span></span>

<span data-ttu-id="5ae4d-175">Il passaggio successivo consiste nel creare il team che si intende utilizzare per la collaborazione con gli utenti.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-175">The next step is to create the team that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="5ae4d-176">Per creare un team</span><span class="sxs-lookup"><span data-stu-id="5ae4d-176">To create a team</span></span>
1. <span data-ttu-id="5ae4d-177">In teams fare clic su **join oppure creare un team** nella parte inferiore del riquadro sinistro nella scheda **Teams** .</span><span class="sxs-lookup"><span data-stu-id="5ae4d-177">In Teams, on the **Teams** tab, click **Join or create a team** at the bottom of the left pane.</span></span>
2. <span data-ttu-id="5ae4d-178">Fare clic su **Crea team**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-178">Click **Create a team**.</span></span>
3. <span data-ttu-id="5ae4d-179">Fare clic su **Crea un team da zero**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-179">Click **Build a team from scratch**.</span></span>
4. <span data-ttu-id="5ae4d-180">Scegliere **privato** o **pubblico**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-180">Choose **Private** or **Public**.</span></span>
5. <span data-ttu-id="5ae4d-181">Digitare un nome e una descrizione per il team, quindi fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-181">Type a name and description for the team, and then click **Create**.</span></span>
6. <span data-ttu-id="5ae4d-182">Fare clic su **Ignora**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-182">Click **Skip**.</span></span>

<span data-ttu-id="5ae4d-183">Gli utenti verranno invitati in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-183">We'll invite users later.</span></span> <span data-ttu-id="5ae4d-184">Successivamente, è importante controllare le impostazioni di condivisione a livello di sito per il sito di SharePoint associato al team.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-184">Next, it's important to check the site-level sharing settings for the SharePoint site that is associated with the team.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="5ae4d-185">Impostazioni di condivisione a livello di sito di SharePoint</span><span class="sxs-lookup"><span data-stu-id="5ae4d-185">SharePoint site level sharing settings</span></span>

<span data-ttu-id="5ae4d-186">Controllare le impostazioni di condivisione a livello di sito per assicurarsi che consentano il tipo di accesso desiderato per il team.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-186">Check the site-level sharing settings to make sure that they allow the type of access that you want for this team.</span></span> <span data-ttu-id="5ae4d-187">Ad esempio, se si impostano le impostazioni a livello di organizzazione per tutti gli **utenti**, ma si desidera che tutti gli ospiti eseguano l'autenticazione per questo team, assicurarsi che le impostazioni di condivisione a livello di sito siano impostate su **Guest nuovi e esistenti**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-187">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this team, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

![Schermata delle impostazioni di condivisione esterna del sito di SharePoint](media/sharepoint-site-external-sharing-settings.png)


<span data-ttu-id="5ae4d-189">Per impostare le impostazioni di condivisione a livello di sito</span><span class="sxs-lookup"><span data-stu-id="5ae4d-189">To set site-level sharing settings</span></span>
1. <span data-ttu-id="5ae4d-190">Nell'interfaccia di amministrazione di SharePoint, nella barra di spostamento sinistra, espandere **siti** e fare clic su **siti attivi**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-190">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="5ae4d-191">Selezionare il sito del team appena creato.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-191">Select the site for the team that you just created.</span></span>
3. <span data-ttu-id="5ae4d-192">Sulla barra multifunzione fare clic su **condivisione**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-192">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="5ae4d-193">Verificare che la condivisione sia impostata su **tutti gli utenti** o **gli ospiti nuovi e esistenti**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-193">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="5ae4d-194">Se sono state apportate modifiche, fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-194">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="5ae4d-195">Invitare gli utenti</span><span class="sxs-lookup"><span data-stu-id="5ae4d-195">Invite users</span></span>

<span data-ttu-id="5ae4d-196">Le impostazioni di condivisione Guest sono ora configurate, quindi è possibile iniziare ad aggiungere utenti interni e ospiti al team.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-196">Guest sharing settings are now configured, so you can start adding internal users and guests to your team.</span></span> 

<span data-ttu-id="5ae4d-197">Per invitare gli utenti interni a un team</span><span class="sxs-lookup"><span data-stu-id="5ae4d-197">To invite internal users to a team</span></span>
1. <span data-ttu-id="5ae4d-198">Nel team, fare clic su **altre opzioni** (**\*\***), quindi fare clic su **Aggiungi membro**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-198">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="5ae4d-199">Digitare il nome della persona che si desidera invitare.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-199">Type the name of the person who you want to invite.</span></span>
3. <span data-ttu-id="5ae4d-200">Fare clic su **Aggiungi**, quindi fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-200">Click **Add**, and then click **Close**.</span></span>

<span data-ttu-id="5ae4d-201">Per invitare gli ospiti a un team</span><span class="sxs-lookup"><span data-stu-id="5ae4d-201">To invite guests to a team</span></span>
1. <span data-ttu-id="5ae4d-202">Nel team, fare clic su **altre opzioni** (**\*\***), quindi fare clic su **Aggiungi membro**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-202">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="5ae4d-203">Digitare l'indirizzo di posta elettronica dell'ospite che si desidera invitare.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-203">Type the email address of the guest who you want to invite.</span></span>
3. <span data-ttu-id="5ae4d-204">Fare clic su **modifica informazioni Guest**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-204">Click **Edit guest information**.</span></span>
4. <span data-ttu-id="5ae4d-205">Digitare il nome completo dell'ospite e fare clic sul segno di spunta.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-205">Type the guest's full name and click the check mark.</span></span>
5. <span data-ttu-id="5ae4d-206">Fare clic su **Aggiungi**, quindi fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="5ae4d-206">Click **Add**, and then click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ae4d-207">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5ae4d-207">See Also</span></span>

