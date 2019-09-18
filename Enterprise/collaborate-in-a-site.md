---
title: Collaborare con gli utenti in un sito
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Informazioni su come collaborare con gli utenti in un sito di SharePoint.
ms.openlocfilehash: 4b68b50fec4322f12c24969bdd71e7d9c0fda245
ms.sourcegitcommit: d388c76d25ca67f240db97f7bfc90f0991b0e7f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "37017314"
---
# <a name="collaborate-with-guests-in-a-site"></a><span data-ttu-id="32ba9-103">Collaborare con gli utenti in un sito</span><span class="sxs-lookup"><span data-stu-id="32ba9-103">Collaborate with guests in a site</span></span>

<span data-ttu-id="32ba9-104">Se è necessario collaborare con gli utenti tra documenti, dati ed elenchi, è possibile utilizzare un sito di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="32ba9-104">If you need to collaborate with guests across documents, data, and lists, you can use a SharePoint site.</span></span> <span data-ttu-id="32ba9-105">I siti di SharePoint moderni sono connessi a gruppi di Office 365 che possono gestire l'appartenenza al sito e fornire strumenti di collaborazione aggiuntivi quali una cassetta postale condivisa e un calendario.</span><span class="sxs-lookup"><span data-stu-id="32ba9-105">Modern SharePoint sites are connected to Office 365 Groups which can manage the site membership and provide additional collaboration tools such as a shared mailbox and calendar.</span></span>

<span data-ttu-id="32ba9-106">In questo articolo verranno illustrati i passaggi di configurazione di Microsoft 365 necessari per configurare un sito di SharePoint per la collaborazione con gli utenti.</span><span class="sxs-lookup"><span data-stu-id="32ba9-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a SharePoint site for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="32ba9-107">Impostazioni delle relazioni organizzative di Azure</span><span class="sxs-lookup"><span data-stu-id="32ba9-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="32ba9-108">La condivisione in Microsoft 365 è regolata al livello più alto dalle impostazioni delle relazioni organizzative in Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="32ba9-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="32ba9-109">Se la condivisione Guest è disabilitata o limitata in Azure AD, queste verranno sostituite da tutte le impostazioni di condivisione configurate in Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="32ba9-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="32ba9-110">Controllare le impostazioni delle relazioni organizzative per garantire che la condivisione con gli ospiti non sia bloccata.</span><span class="sxs-lookup"><span data-stu-id="32ba9-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Schermata della pagina delle impostazioni delle relazioni organizzative di Azure Active Directory](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="32ba9-112">Per impostare le impostazioni delle relazioni organizzative</span><span class="sxs-lookup"><span data-stu-id="32ba9-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="32ba9-113">Accedere a Microsoft Azure all'indirizzo [https://portal.azure.com](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="32ba9-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="32ba9-114">Nel riquadro di spostamento a sinistra, fare clic su **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="32ba9-115">Nel riquadro **Panoramica** fare clic su **relazioni organizzative**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="32ba9-116">Nel riquadro **relazioni organizzative** fare clic su **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="32ba9-117">Verificare che **gli amministratori e gli utenti del ruolo invitato ospite possano invitare** e che **i membri possano invitare** siano entrambi impostati su **Sì**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="32ba9-118">Se sono state apportate modifiche, fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="32ba9-119">Prendere nota delle impostazioni nella sezione **vincoli di collaborazione** .</span><span class="sxs-lookup"><span data-stu-id="32ba9-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="32ba9-120">Verificare che i domini degli utenti con cui si desidera collaborare non siano bloccati.</span><span class="sxs-lookup"><span data-stu-id="32ba9-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="32ba9-121">Office 365 gruppi Guest Settings</span><span class="sxs-lookup"><span data-stu-id="32ba9-121">Office 365 Groups guest settings</span></span>

<span data-ttu-id="32ba9-122">I siti di SharePoint moderni utilizzano i gruppi di Office 365 per controllare l'accesso al sito.</span><span class="sxs-lookup"><span data-stu-id="32ba9-122">Modern SharePoint sites use Office 365 Groups to control site access.</span></span> <span data-ttu-id="32ba9-123">Le impostazioni di Office 365 groups Guest devono essere attivate affinché l'accesso guest in siti di SharePoint funzioni.</span><span class="sxs-lookup"><span data-stu-id="32ba9-123">The Office 365 Groups guest settings must be turned on in order for guest access in SharePoint sites to work.</span></span>

![Schermata di Office 365 gruppi Guest Settings in Microsoft 365 Admin Center](media/office-365-groups-guest-settings.png)

<span data-ttu-id="32ba9-125">Per impostare le impostazioni di Office 365 groups Guest</span><span class="sxs-lookup"><span data-stu-id="32ba9-125">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="32ba9-126">Nell'interfaccia di amministrazione di Microsoft 365, nel riquadro di spostamento a sinistra, espandere **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-126">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="32ba9-127">Fare clic su **servizi & componenti**aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="32ba9-127">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="32ba9-128">Nell'elenco, fare clic su **gruppi di Office 365**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-128">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="32ba9-129">Verificare che i membri del gruppo Consenti al di **fuori dell'organizzazione accedano al contenuto del gruppo** e che i proprietari del **gruppo aggiungano persone all'esterno dell'organizzazione ai gruppi di caselle di** controllo siano entrambe controllate.</span><span class="sxs-lookup"><span data-stu-id="32ba9-129">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="32ba9-130">Se sono state apportate modifiche, fare clic su **Salva modifiche**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-130">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="32ba9-131">Impostazioni di condivisione a livello di organizzazione di SharePoint</span><span class="sxs-lookup"><span data-stu-id="32ba9-131">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="32ba9-132">Affinché gli utenti dispongano dell'accesso ai siti di SharePoint, le impostazioni di condivisione a livello dell'organizzazione di SharePoint devono consentire la condivisione con gli utenti.</span><span class="sxs-lookup"><span data-stu-id="32ba9-132">In order for guests to have access to SharePoint sites, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="32ba9-133">Le impostazioni a livello di organizzazione determinano le impostazioni disponibili per i singoli siti.</span><span class="sxs-lookup"><span data-stu-id="32ba9-133">The organization-level settings determine what settings are available for individual sites.</span></span> <span data-ttu-id="32ba9-134">Le impostazioni del sito non possono essere più permissive rispetto alle impostazioni a livello di organizzazione.</span><span class="sxs-lookup"><span data-stu-id="32ba9-134">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="32ba9-135">Se si desidera consentire la condivisione di file e cartelle con utenti anonimi, scegliere **nessuno**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-135">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="32ba9-136">Se si desidera garantire che tutti gli utenti siano in grado di eseguire l'autenticazione, scegliere **clienti nuovi ed esistenti**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-136">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="32ba9-137">Scegliere l'impostazione più permissiva che sarà necessaria per qualsiasi sito dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="32ba9-137">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Schermata delle impostazioni di condivisione a livello di organizzazione di SharePoint](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="32ba9-139">Per impostare le impostazioni di condivisione a livello di organizzazione di SharePoint</span><span class="sxs-lookup"><span data-stu-id="32ba9-139">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="32ba9-140">Nell'interfaccia di amministrazione di Microsoft 365, nella barra di spostamento a sinistra, in interfaccia di **Amministrazione**, fare clic su **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-140">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="32ba9-141">Nell'interfaccia di amministrazione di SharePoint, nella barra di spostamento a sinistra, fare clic su **condivisione**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-141">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="32ba9-142">Assicurarsi che la condivisione esterna per SharePoint sia impostata su **tutti gli utenti** o **gli ospiti nuovi e esistenti**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-142">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="32ba9-143">Se sono state apportate modifiche, fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-143">If you made changes, click **Save**.</span></span>

## <a name="create-a-site"></a><span data-ttu-id="32ba9-144">Creare un sito</span><span class="sxs-lookup"><span data-stu-id="32ba9-144">Create a site</span></span>

<span data-ttu-id="32ba9-145">Il passaggio successivo consiste nel creare il sito che si intende utilizzare per la collaborazione con gli utenti.</span><span class="sxs-lookup"><span data-stu-id="32ba9-145">The next step is to create the site that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="32ba9-146">Per creare un sito</span><span class="sxs-lookup"><span data-stu-id="32ba9-146">To create a site</span></span>
1. <span data-ttu-id="32ba9-147">Nell'interfaccia di amministrazione di SharePoint, in **siti**, fare clic su **siti attivi**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-147">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="32ba9-148">Fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-148">Click **Create**.</span></span>
3. <span data-ttu-id="32ba9-149">Fare clic su **sito del team**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-149">Click **Team site**.</span></span>
4. <span data-ttu-id="32ba9-150">Digitare il nome di un sito e immettere un nome per il proprietario del gruppo (proprietario del sito).</span><span class="sxs-lookup"><span data-stu-id="32ba9-150">Type a site name and enter a name for the Group owner (site owner).</span></span>
5. <span data-ttu-id="32ba9-151">In **Impostazioni avanzate**scegliere se si desidera che sia un sito pubblico o privato.</span><span class="sxs-lookup"><span data-stu-id="32ba9-151">Under **Advanced settings**, choose if you want this to be a public or private site.</span></span>
6. <span data-ttu-id="32ba9-152">Fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-152">Click **Next**.</span></span>
7. <span data-ttu-id="32ba9-153">Fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-153">Click **Finish**.</span></span>

<span data-ttu-id="32ba9-154">Gli utenti verranno invitati in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="32ba9-154">We'll invite users later.</span></span> <span data-ttu-id="32ba9-155">Successivamente, è importante controllare le impostazioni di condivisione a livello di sito per il sito.</span><span class="sxs-lookup"><span data-stu-id="32ba9-155">Next, it's important to check the site-level sharing settings for this site.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="32ba9-156">Impostazioni di condivisione a livello di sito di SharePoint</span><span class="sxs-lookup"><span data-stu-id="32ba9-156">SharePoint site level sharing settings</span></span>

<span data-ttu-id="32ba9-157">Controllare le impostazioni di condivisione a livello di sito per assicurarsi che consentano il tipo di accesso desiderato per il sito.</span><span class="sxs-lookup"><span data-stu-id="32ba9-157">Check the site-level sharing settings to make sure that they allow the type of access that you want for this site.</span></span> <span data-ttu-id="32ba9-158">Ad esempio, se si impostano le impostazioni a livello di organizzazione per tutti gli **utenti**, ma si desidera che tutti gli ospiti eseguano l'autenticazione per questo sito, assicurarsi che le impostazioni di condivisione a livello di sito siano impostate su **ospiti nuovi e esistenti**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-158">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this site, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

<span data-ttu-id="32ba9-159">Si noti che il sito non può essere condiviso con utenti anonimi (impostazione**chiunque** ), ma è possibile eseguire singoli file e cartelle.</span><span class="sxs-lookup"><span data-stu-id="32ba9-159">Note that the site cannot be shared with anonymous users (**Anyone** setting), but individual files and folders can.</span></span>

![Schermata delle impostazioni di condivisione esterna del sito di SharePoint](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="32ba9-161">Per impostare le impostazioni di condivisione a livello di sito</span><span class="sxs-lookup"><span data-stu-id="32ba9-161">To set site-level sharing settings</span></span>
1. <span data-ttu-id="32ba9-162">Nell'interfaccia di amministrazione di SharePoint, nella barra di spostamento sinistra, espandere **siti** e fare clic su **siti attivi**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-162">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="32ba9-163">Selezionare il sito appena creato.</span><span class="sxs-lookup"><span data-stu-id="32ba9-163">Select the site that you just created.</span></span>
3. <span data-ttu-id="32ba9-164">Sulla barra multifunzione fare clic su **condivisione**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-164">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="32ba9-165">Verificare che la condivisione sia impostata su **tutti gli utenti** o **gli ospiti nuovi e esistenti**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-165">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="32ba9-166">Se sono state apportate modifiche, fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-166">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="32ba9-167">Invitare gli utenti</span><span class="sxs-lookup"><span data-stu-id="32ba9-167">Invite users</span></span>

<span data-ttu-id="32ba9-168">Le impostazioni di condivisione Guest sono ora configurate, quindi è possibile iniziare ad aggiungere utenti interni e ospiti al sito.</span><span class="sxs-lookup"><span data-stu-id="32ba9-168">Guest sharing settings are now configured, so you can start adding internal users and guests to your site.</span></span> <span data-ttu-id="32ba9-169">L'accesso al sito è controllato tramite il gruppo Office 365 associato, quindi verranno aggiunti gli utenti.</span><span class="sxs-lookup"><span data-stu-id="32ba9-169">Site access is controlled through the associated Office 365 Group, so we'll be adding users there.</span></span>

<span data-ttu-id="32ba9-170">Per invitare gli utenti interni a un gruppo</span><span class="sxs-lookup"><span data-stu-id="32ba9-170">To invite internal users to a group</span></span>
1. <span data-ttu-id="32ba9-171">Passare al sito in cui si desidera aggiungere gli utenti.</span><span class="sxs-lookup"><span data-stu-id="32ba9-171">Navigate to the site where you want to add users.</span></span>
2. <span data-ttu-id="32ba9-172">Fare clic su **membri** in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="32ba9-172">Click **Members** in the upper right.</span></span>
3. <span data-ttu-id="32ba9-173">Fare clic su **Aggiungi membri**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-173">Click **Add members**.</span></span>
4. <span data-ttu-id="32ba9-174">Digitare i nomi o gli indirizzi di posta elettronica degli utenti che si desidera invitare al sito e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-174">Type the names or email addresses of the users that you want to invite to the site, and then click **Save**.</span></span>

<span data-ttu-id="32ba9-175">Gli utenti guest non possono essere aggiunti dal sito.</span><span class="sxs-lookup"><span data-stu-id="32ba9-175">Guest users can't be added from the site.</span></span> <span data-ttu-id="32ba9-176">È necessario aggiungerli utilizzando Outlook sul Web.</span><span class="sxs-lookup"><span data-stu-id="32ba9-176">You need to add them using Outlook on the web.</span></span>

<span data-ttu-id="32ba9-177">Per invitare gli ospiti a un sito</span><span class="sxs-lookup"><span data-stu-id="32ba9-177">To invite guests to a site</span></span>
1. <span data-ttu-id="32ba9-178">In **gruppi**, in Outlook sul Web, fare clic sul gruppo in cui si desidera aggiungere i membri.</span><span class="sxs-lookup"><span data-stu-id="32ba9-178">In Outlook on the web, under **Groups**, click the group where you want to add members.</span></span>
2. <span data-ttu-id="32ba9-179">Aprire la scheda contatto di gruppo e quindi, in **altre opzioni** (...), fare clic su **Aggiungi membri**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-179">Open the group contact card, and then, under **More options** (...), click **Add members**.</span></span>
3. <span data-ttu-id="32ba9-180">Digitare gli indirizzi di posta elettronica degli utenti che si desidera invitare e quindi fare clic su **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-180">Type the email addresses of the guests that you want to invite, and then click **Add**.</span></span>
4. <span data-ttu-id="32ba9-181">Fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="32ba9-181">Click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="32ba9-182">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="32ba9-182">See Also</span></span>
