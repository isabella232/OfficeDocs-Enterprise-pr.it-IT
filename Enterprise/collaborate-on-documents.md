---
title: Collaborare con gli utenti in un documento
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Informazioni su come collaborare con gli utenti di un documento in SharePoint e OneDrive.
ms.openlocfilehash: c0c74f2457e9b25b37355c58ed18f120261e3364
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992405"
---
# <a name="collaborate-with-guests-on-a-document"></a><span data-ttu-id="6eecd-103">Collaborare con gli utenti in un documento</span><span class="sxs-lookup"><span data-stu-id="6eecd-103">Collaborate with guests on a document</span></span>

<span data-ttu-id="6eecd-104">Se è necessario collaborare con gli ospiti nei documenti di SharePoint o OneDrive, è possibile inviare un collegamento di condivisione al documento.</span><span class="sxs-lookup"><span data-stu-id="6eecd-104">If you need to collaborate with guests on documents in SharePoint or OneDrive, you can send them a sharing link to the document.</span></span> <span data-ttu-id="6eecd-105">In questo articolo verranno illustrati i passaggi di configurazione di Microsoft 365 necessari per configurare i collegamenti di condivisione per SharePoint e OneDrive.</span><span class="sxs-lookup"><span data-stu-id="6eecd-105">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up sharing links for SharePoint and OneDrive.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="6eecd-106">Impostazioni delle relazioni organizzative di Azure</span><span class="sxs-lookup"><span data-stu-id="6eecd-106">Azure Organizational relationships settings</span></span>

<span data-ttu-id="6eecd-107">La condivisione in Microsoft 365 è regolata al livello più alto dalle impostazioni delle relazioni organizzative in Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="6eecd-107">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="6eecd-108">Se la condivisione Guest è disabilitata o limitata in Azure AD, queste verranno sostituite da tutte le impostazioni di condivisione configurate in Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="6eecd-108">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="6eecd-109">Controllare le impostazioni delle relazioni organizzative per garantire che la condivisione con gli ospiti non sia bloccata.</span><span class="sxs-lookup"><span data-stu-id="6eecd-109">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Schermata della pagina delle impostazioni delle relazioni organizzative di Azure Active Directory](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="6eecd-111">Per impostare le impostazioni delle relazioni organizzative</span><span class="sxs-lookup"><span data-stu-id="6eecd-111">To set organizational relationship settings</span></span>

1. <span data-ttu-id="6eecd-112">Accedere a Microsoft Azure all'indirizzo [https://portal.azure.com](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="6eecd-112">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="6eecd-113">Nel riquadro di spostamento a sinistra, fare clic su **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="6eecd-113">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="6eecd-114">Nel riquadro **Panoramica** fare clic su **relazioni organizzative**.</span><span class="sxs-lookup"><span data-stu-id="6eecd-114">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="6eecd-115">Nel riquadro **relazioni organizzative** fare clic su **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="6eecd-115">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="6eecd-116">Verificare che **gli amministratori e gli utenti del ruolo invitato ospite possano invitare** e che **i membri possano invitare** siano entrambi impostati su **Sì**.</span><span class="sxs-lookup"><span data-stu-id="6eecd-116">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="6eecd-117">Se sono state apportate modifiche, fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="6eecd-117">If you made changes, click **Save**.</span></span>

<span data-ttu-id="6eecd-118">Prendere nota delle impostazioni nella sezione **vincoli di collaborazione** .</span><span class="sxs-lookup"><span data-stu-id="6eecd-118">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="6eecd-119">Verificare che i domini degli utenti con cui si desidera collaborare non siano bloccati.</span><span class="sxs-lookup"><span data-stu-id="6eecd-119">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="6eecd-120">Impostazioni di condivisione a livello di organizzazione di SharePoint</span><span class="sxs-lookup"><span data-stu-id="6eecd-120">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="6eecd-121">Affinché gli utenti dispongano dell'accesso a un documento in SharePoint o OneDrive, è necessario che le impostazioni di condivisione a livello di organizzazione di SharePoint e OneDrive consentano la condivisione con gli utenti.</span><span class="sxs-lookup"><span data-stu-id="6eecd-121">In order for guests to have access to a document in SharePoint or OneDrive, the SharePoint and OneDrive organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="6eecd-122">Le impostazioni a livello di organizzazione per SharePoint determinano le impostazioni disponibili per i singoli siti di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6eecd-122">The organization-level settings for SharePoint determine what settings are available for individual SharePoint sites.</span></span> <span data-ttu-id="6eecd-123">Le impostazioni del sito non possono essere più permissive rispetto alle impostazioni a livello di organizzazione.</span><span class="sxs-lookup"><span data-stu-id="6eecd-123">Site settings cannot be more permissive than the organization-level settings.</span></span> <span data-ttu-id="6eecd-124">L'impostazione a livello di organizzazione per OneDrive determina il livello di condivisione disponibile nelle raccolte OneDrive degli utenti.</span><span class="sxs-lookup"><span data-stu-id="6eecd-124">The organization-level setting for OneDrive determines what level of sharing is available in users' OneDrive libraries.</span></span>

<span data-ttu-id="6eecd-125">Per SharePiont e OneDrive, se si desidera consentire la condivisione di file e cartelle con utenti anonimi, scegliere **chiunque**.</span><span class="sxs-lookup"><span data-stu-id="6eecd-125">For SharePiont and OneDrive, if you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="6eecd-126">Se si desidera garantire che tutti gli utenti siano in grado di eseguire l'autenticazione, scegliere **clienti nuovi ed esistenti**.</span><span class="sxs-lookup"><span data-stu-id="6eecd-126">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> 

<span data-ttu-id="6eecd-127">Per SharePoint, scegliere l'impostazione più permissiva che sarà necessaria per qualsiasi sito dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="6eecd-127">For SharePoint, choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Schermata delle impostazioni di condivisione a livello di organizzazione di SharePoint](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="6eecd-129">Per impostare le impostazioni di condivisione a livello di organizzazione di SharePoint</span><span class="sxs-lookup"><span data-stu-id="6eecd-129">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="6eecd-130">Nell'interfaccia di amministrazione di Microsoft 365, nella barra di spostamento a sinistra, in interfaccia di **Amministrazione**, fare clic su **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6eecd-130">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="6eecd-131">Nell'interfaccia di amministrazione di SharePoint, nella barra di spostamento a sinistra, fare clic su **condivisione**.</span><span class="sxs-lookup"><span data-stu-id="6eecd-131">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="6eecd-132">Verificare che la condivisione esterna per SharePoint o OneDrive sia impostata su chiunque o su un **utente** **nuovo o esistente**.</span><span class="sxs-lookup"><span data-stu-id="6eecd-132">Ensure that external sharing for SharePoint or OneDrive is set to **Anyone** or **New and existing guests**.</span></span> <span data-ttu-id="6eecd-133">Si noti che l'impostazione di OneDrive non può essere più permissiva dell'impostazione di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6eecd-133">(Note that the OneDrive setting cannot be more permissive than the SharePoint setting.)</span></span>
4. <span data-ttu-id="6eecd-134">Se sono state apportate modifiche, fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="6eecd-134">If you made changes, click **Save**.</span></span>

## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="6eecd-135">Impostazioni di collegamento predefinite a livello di organizzazione di SharePoint</span><span class="sxs-lookup"><span data-stu-id="6eecd-135">SharePoint organization level default link settings</span></span>

<span data-ttu-id="6eecd-136">Le impostazioni predefinite per il collegamento di file e cartelle determinano l'opzione di collegamento visualizzata all'utente per impostazione predefinita quando condividono un file o una cartella.</span><span class="sxs-lookup"><span data-stu-id="6eecd-136">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="6eecd-137">Gli utenti possono modificare il tipo di collegamento in una delle altre opzioni prima della condivisione, se necessario.</span><span class="sxs-lookup"><span data-stu-id="6eecd-137">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="6eecd-138">Tenere presente che questa impostazione influisce sui siti di SharePoint nell'organizzazione, nonché OneDrive.</span><span class="sxs-lookup"><span data-stu-id="6eecd-138">Keep in mind that this setting affects SharePoint sites in your organization, as well as OneDrive.</span></span>

<span data-ttu-id="6eecd-139">Scegliere il tipo di collegamento selezionato per impostazione predefinita quando gli utenti condividono file e cartelle:</span><span class="sxs-lookup"><span data-stu-id="6eecd-139">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="6eecd-140">**Tutti gli utenti con il collegamento** : scegliere questa opzione se si prevede di condividere un gran quantità di file e cartelle in modo anonimo.</span><span class="sxs-lookup"><span data-stu-id="6eecd-140">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="6eecd-141">Se si desidera consentire collegamenti a *tutti gli utenti* , ma sono preoccupati per la condivisione accidentale anonima, prendere in considerazione una delle altre opzioni come impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="6eecd-141">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="6eecd-142">Questo tipo di collegamento è disponibile solo se è stata abilitata la condivisione di **utenti** .</span><span class="sxs-lookup"><span data-stu-id="6eecd-142">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="6eecd-143">**Solo persone nell'organizzazione** : scegliere questa opzione se si prevede che la maggior parte della condivisione di file e cartelle sia con le persone all'interno dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="6eecd-143">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="6eecd-144">**Persone specifiche** : considerare questa opzione se si prevede di eseguire un sacco di condivisione di file e cartelle con gli utenti.</span><span class="sxs-lookup"><span data-stu-id="6eecd-144">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="6eecd-145">Questo tipo di collegamento è compatibile con gli utenti e richiede l'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="6eecd-145">This type of link works with guests and requires them to authenticate.</span></span>
 
![Schermata di impostazioni di condivisione di file e cartelle a livello di organizzazione di SharePoint](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="6eecd-147">Per impostare le impostazioni dei collegamenti predefiniti a livello di organizzazione di SharePoint e OneDrive</span><span class="sxs-lookup"><span data-stu-id="6eecd-147">To set the SharePoint and OneDrive organization level default link settings</span></span>

1. <span data-ttu-id="6eecd-148">Passare alla pagina condivisione nell'interfaccia di amministrazione di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6eecd-148">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="6eecd-149">In **collegamenti a file e cartelle**selezionare il collegamento di condivisione predefinito che si desidera utilizzare.</span><span class="sxs-lookup"><span data-stu-id="6eecd-149">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="6eecd-150">Se sono state apportate modifiche, fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="6eecd-150">If you made changes, click **Save**.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="6eecd-151">Impostazioni di condivisione a livello di sito di SharePoint</span><span class="sxs-lookup"><span data-stu-id="6eecd-151">SharePoint site level sharing settings</span></span>

<span data-ttu-id="6eecd-152">Se si condividono file e fodlers che si trovano in un sito di SharePoint, è necessario controllare anche le impostazioni di condivisione a livello di sito per il sito.</span><span class="sxs-lookup"><span data-stu-id="6eecd-152">If you're sharing files and fodlers that are in a SharePoint site, you also need to check the site-level sharing settings for that site.</span></span>

![Schermata delle impostazioni di condivisione esterna del sito di SharePoint](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="6eecd-154">Per impostare le impostazioni di condivisione a livello di sito</span><span class="sxs-lookup"><span data-stu-id="6eecd-154">To set site-level sharing settings</span></span>
1. <span data-ttu-id="6eecd-155">Nell'interfaccia di amministrazione di SharePoint, nella barra di spostamento sinistra, espandere **siti** e fare clic su **siti attivi**.</span><span class="sxs-lookup"><span data-stu-id="6eecd-155">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="6eecd-156">Selezionare il sito appena creato.</span><span class="sxs-lookup"><span data-stu-id="6eecd-156">Select the site that you just created.</span></span>
3. <span data-ttu-id="6eecd-157">Sulla barra multifunzione fare clic su **condivisione**.</span><span class="sxs-lookup"><span data-stu-id="6eecd-157">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="6eecd-158">Verificare che la condivisione sia impostata su **tutti gli utenti** o **gli ospiti nuovi e esistenti**.</span><span class="sxs-lookup"><span data-stu-id="6eecd-158">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="6eecd-159">Se sono state apportate modifiche, fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="6eecd-159">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="6eecd-160">Invitare gli utenti</span><span class="sxs-lookup"><span data-stu-id="6eecd-160">Invite users</span></span>

<span data-ttu-id="6eecd-161">Le impostazioni di condivisione Guest sono ora configurate, quindi gli utenti possono ora condividere file e cartelle con gli ospiti.</span><span class="sxs-lookup"><span data-stu-id="6eecd-161">Guest sharing settings are now configured, so users can now share files and folders with guests.</span></span> <span data-ttu-id="6eecd-162">Per ulteriori informazioni, vedere [condivisione di file e cartelle di OneDrive](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) e [condivisione di file o cartelle di SharePoint](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) .</span><span class="sxs-lookup"><span data-stu-id="6eecd-162">See [Share OneDrive files and folders](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) and [Share SharePoint files or folders](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="6eecd-163">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6eecd-163">See Also</span></span>
