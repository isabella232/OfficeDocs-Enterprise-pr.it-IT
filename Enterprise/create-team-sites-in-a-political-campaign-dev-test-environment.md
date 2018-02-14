---
title: Creare siti del team in un ambiente di sviluppo/test per la campagna politica
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: 'Riepilogo: Creare siti del team SharePoint Online pubblici, privati, riservati e altamente riservati nell''ambiente di sviluppo e di testing politici campagne.'
ms.openlocfilehash: 3a2e507d17a558452fe0c2f0a062098e7c9c6407
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2018
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a><span data-ttu-id="f8b13-103">Creare siti del team in un ambiente di sviluppo/test per la campagna politica</span><span class="sxs-lookup"><span data-stu-id="f8b13-103">Create team sites in a political campaign dev/test environment</span></span>

 <span data-ttu-id="f8b13-104">**Riepilogo:** Creare siti del team SharePoint Online pubblici, privati, riservati e altamente riservati nell'ambiente di sviluppo e di testing politici campagne.</span><span class="sxs-lookup"><span data-stu-id="f8b13-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in your political campaign dev/test environment.</span></span> 
  
<span data-ttu-id="f8b13-p101">Utilizzare le istruzioni riportate in questo articolo per creare un ambiente di sviluppo e di testing che include quattro diversi tipi di siti di team di SharePoint Online per [Microsoft Security Guidance for campagne politici, ricchi e altre organizzazioni Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) soluzione. Tali siti vengono descritte in dettaglio in 10 argomento, intitolato **SharePoint e OneDrive for Business**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-p101">Use the instructions in this article to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution. These sites are described in detail on Topic 10, titled **SharePoint and OneDrive for Business**.</span></span>
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a><span data-ttu-id="f8b13-107">Fase 1: creare l'ambiente di sviluppo/test per la campagna politica</span><span class="sxs-lookup"><span data-stu-id="f8b13-107">Phase 1: Create your political campaign dev/test environment</span></span>

<span data-ttu-id="f8b13-108">Per prima cosa, seguire le istruzioni in [configurare gruppi e gli utenti per un ambiente di sviluppo e di testing campagne politici](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) per creare le sottoscrizioni, gli utenti e gruppi.</span><span class="sxs-lookup"><span data-stu-id="f8b13-108">First, follow the instructions in [Configure groups and users for a political campaign dev/test environment](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) to create your subscriptions, users, and groups.</span></span>
  
## <a name="phase-2-create-office-365-labels"></a><span data-ttu-id="f8b13-109">Fase 2: creare etichette di Office 365</span><span class="sxs-lookup"><span data-stu-id="f8b13-109">Phase 2: Create Office 365 labels</span></span>

<span data-ttu-id="f8b13-110">In questa fase è creare etichette per i diversi livelli di sicurezza per le cartelle di documenti del sito del team SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="f8b13-110">In this phase, you create the labels for the different levels of security for SharePoint Online team site document folders.</span></span>
  
1. <span data-ttu-id="f8b13-p102">Se necessario, accedere al portale di Office 365 con le credenziali dell'account amministratore globale della sottoscrizione di prova. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="f8b13-p102">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="f8b13-113">Nella scheda **Home page di Microsoft Office** , fare clic su tessera di **amministrazione** .</span><span class="sxs-lookup"><span data-stu-id="f8b13-113">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="f8b13-114">Scheda di **interfaccia di amministrazione di Office** nuovo del browser fare clic su **Admin Center > sicurezza &amp; conformità**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-114">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="f8b13-115">Dalla nuova **Home - sicurezza &amp; conformità** scheda del browser, fare clic su **classificazioni > etichette**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-115">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="f8b13-116">Dal **Home > etichette** riquadro, fare clic su **Crea un'etichetta**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-116">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="f8b13-117">Nel riquadro **nome dell'etichetta** digitare **interno**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-117">On the **Name your label** pane, type **Internal**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="f8b13-118">Nel riquadro di **impostazioni dell'etichetta** , fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-118">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="f8b13-119">Nel riquadro di **Rivedere le impostazioni** , fare clic su **Crea l'etichetta**e quindi fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-119">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="f8b13-120">Ripetere i passaggi 5-8 per queste etichette aggiuntive:</span><span class="sxs-lookup"><span data-stu-id="f8b13-120">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="f8b13-121">Privato</span><span class="sxs-lookup"><span data-stu-id="f8b13-121">Private</span></span>
    
  - <span data-ttu-id="f8b13-122">Riservato</span><span class="sxs-lookup"><span data-stu-id="f8b13-122">Sensitive</span></span>
    
  - <span data-ttu-id="f8b13-123">Dati estremamente riservati</span><span class="sxs-lookup"><span data-stu-id="f8b13-123">Highly Confidential</span></span>
    
10. <span data-ttu-id="f8b13-124">Dal **Home > etichette** riquadro, fare clic su **pubblica etichette**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-124">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="f8b13-125">Nel riquadro di **scegliere le etichette per la pubblicazione** , fare clic su **etichette scegliere per la pubblicazione**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-125">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="f8b13-126">Nel riquadro **scegliere etichette** , fare clic su **Aggiungi** e selezionare tutte le etichette di quattro.</span><span class="sxs-lookup"><span data-stu-id="f8b13-126">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="f8b13-127">Fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-127">Click **Done**.</span></span>
    
14. <span data-ttu-id="f8b13-128">Nel riquadro di **scegliere le etichette per la pubblicazione** , fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-128">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="f8b13-129">Nel riquadro **scegliere percorsi** , fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-129">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="f8b13-130">Nel riquadro **nome del criterio** digitare **campagne** nella **casella Nome**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-130">On the **Name your policy** pane, type **Campaign** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="f8b13-131">Nel riquadro di **Rivedere le impostazioni** , fare clic su **etichette pubblica**e quindi fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-131">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="f8b13-132">Fase 3: creare i siti del team di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="f8b13-132">Phase 3: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="f8b13-133">In questa fase, vengono creati e configurati i siti del team di SharePoint Online per la campagna politica corrispondente ai quattro tipi di siti del team di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="f8b13-133">In this phase, you create and configure SharePoint Online team sites for your political campaign corresponding to the four types of SharePoint Online team sites.</span></span>
  
### <a name="campaign-wide-team-site"></a><span data-ttu-id="f8b13-134">Sito del team per la campagna su vasta scala</span><span class="sxs-lookup"><span data-stu-id="f8b13-134">Campaign wide team site</span></span>

<span data-ttu-id="f8b13-135">Per creare un sito del team di SharePoint Online pubblico di base, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f8b13-135">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="f8b13-136">Se necessario, utilizzare un browser nel computer locale e accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) utilizzando l'account amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="f8b13-136">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="f8b13-137">Nell'elenco delle sezioni, fare clic su **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-137">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="f8b13-138">Nella scheda **SharePoint** nuovo nel browser, fare clic su **Crea sito +**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-138">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="f8b13-139">Nella pagina **Crea sito** fare clic su **sito del Team**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-139">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="f8b13-140">In **nome sito**digitare **campagne wide**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-140">In **Site name**, type **Campaign wide**.</span></span> 
    
6. <span data-ttu-id="f8b13-141">Nella **descrizione del sito del Team**, digitare **il sito di SharePoint per l'intera campagna**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-141">In **Team site description**, type **SharePoint site for the entire campaign**.</span></span>
    
7. <span data-ttu-id="f8b13-142">In **impostazioni di Privacy**, selezionare **Pubblica - tutti gli utenti dell'organizzazione possono accedere al sito**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-142">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="f8b13-143">Nella **che si desidera aggiungere?** riquadro, fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-143">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="f8b13-144">Successivamente, configurare la cartella dei documenti del sito del team Campagna su vasta scala per l'etichetta Interno.</span><span class="sxs-lookup"><span data-stu-id="f8b13-144">Next, configure the documents folder of the Campaign wide team site for the Internal label.</span></span>
  
1. <span data-ttu-id="f8b13-145">Nella scheda **campagna home page di livello** del browser fare clic su **documenti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-145">In the **Campaign wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="f8b13-146">Fare clic sull'icona impostazioni e quindi fare clic su **Impostazioni raccolta**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-146">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="f8b13-147">Nella sezione **autorizzazioni e gestione**, fare clic su **Applica etichetta agli elementi della raccolta**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-147">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="f8b13-148">In **Applica impostazioni etichetta**, selezionare **interno**e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-148">In **Settings-Apply Label**, select **Internal**, and then click **Save**.</span></span>
    
### <a name="campaign-project-1-team-site"></a><span data-ttu-id="f8b13-149">Sito del team 1 del progetto della campagna</span><span class="sxs-lookup"><span data-stu-id="f8b13-149">Campaign project 1 team site</span></span>

<span data-ttu-id="f8b13-150">Per creare un sito del team di SharePoint Online privato di base per un progetto all'interno della campagna, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f8b13-150">To create a baseline private SharePoint Online team site for a project within the campaign, do the following:</span></span>
  
1. <span data-ttu-id="f8b13-151">Se necessario, utilizzare un browser nel computer locale e accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) utilizzando l'account amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="f8b13-151">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="f8b13-152">Nell'elenco delle sezioni, fare clic su **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-152">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="f8b13-153">Nella scheda **SharePoint** nuovo nel browser, fare clic su **Crea sito +**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-153">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="f8b13-154">Nella pagina **Crea sito** fare clic su **sito del Team**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-154">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="f8b13-155">In **nome sito**digitare **project campagne 1**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-155">In **Site name**, type **Campaign project 1**.</span></span> 
    
6. <span data-ttu-id="f8b13-156">Nella **descrizione del sito del Team,** digitare **il sito di SharePoint per il progetto campagne 1**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-156">In **Team site description,** type **SharePoint site for Campaign project 1**.</span></span>
    
7. <span data-ttu-id="f8b13-157">**Le impostazioni di Privacy**, selezionare **privato: solo membri possono accedere al sito**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-157">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="f8b13-158">Nella **che si desidera aggiungere?** riquadro, fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-158">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="f8b13-159">Successivamente, configurare la cartella dei documenti del sito del team Progetto della campagna 1 per l'etichetta Privato.</span><span class="sxs-lookup"><span data-stu-id="f8b13-159">Next, configure the documents folder of the Campaign project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="f8b13-160">Nella scheda **campagna 1-Home page di project** del browser fare clic su **documenti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-160">In the **Campaign project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="f8b13-161">Fare clic sull'icona impostazioni e quindi fare clic su **Impostazioni raccolta**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-161">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="f8b13-162">Nella sezione **autorizzazioni e gestione**, fare clic su **Applica etichetta agli elementi della raccolta**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-162">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="f8b13-163">In **Applica impostazioni etichetta**, selezionare **privata**e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-163">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
### <a name="campaign-marketing-team-site"></a><span data-ttu-id="f8b13-164">Sito del team per il marketing della campagna</span><span class="sxs-lookup"><span data-stu-id="f8b13-164">Campaign marketing team site</span></span>

<span data-ttu-id="f8b13-165">Per creare un sito del team di SharePoint Online isolato riservato per le risorse marketing della campagna, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f8b13-165">To create a sensitive-level isolated SharePoint Online team site for campaign marketing resources, do the following:</span></span>
  
1. <span data-ttu-id="f8b13-166">Utilizzando un browser nel computer locale, accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) utilizzando l'account amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="f8b13-166">Using a browser on your local computer, sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="f8b13-167">Nell'elenco delle sezioni, fare clic su **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-167">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="f8b13-168">Nella scheda **SharePoint** nuovo nel browser, fare clic su **Crea sito +**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-168">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="f8b13-169">Nella pagina **Crea sito** fare clic su **sito del Team**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-169">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="f8b13-170">**Nome del sito del Team**, digitare **marketing campagne**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-170">In **Team site name**, type **Campaign marketing**.</span></span>
    
6. <span data-ttu-id="f8b13-171">Nella **descrizione del sito del Team**, digitare **sito di SharePoint per campagne di marketing (maiuscole/minuscole)**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-171">In **Team site description**, type **SharePoint site for campaign marketing (sensitive)**.</span></span>
    
7.  <span data-ttu-id="f8b13-172">**Le impostazioni di Privacy**, selezionare **privato: solo membri possono accedere al sito**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-172">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="f8b13-173">Nella **che si desidera aggiungere?** riquadro, fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-173">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="f8b13-174">Nella scheda **marketing campagne** nuovo nel browser, nella barra degli strumenti, fare clic sull'icona impostazioni e quindi fare clic su **autorizzazioni sito**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-174">On the new **Campaign marketing** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="f8b13-175">Nel riquadro **autorizzazioni sito** fare clic su **impostazioni di autorizzazioni avanzate**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-175">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="f8b13-176">Nella scheda **autorizzazioni** nuova nel browser, fare clic su **Impostazioni richieste di accesso**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-176">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="f8b13-177">Nella finestra di dialogo **Impostazioni richieste di accesso** , deselezionare le caselle di controllo **Consenti ai membri di condividere il sito e i singoli file e cartelle** e i **membri Consenti per invitare altre persone al gruppo membri del sito** , digitare **ITAdmin1 @** <your organization name> **. onmicrosoft.com** di **inviare tutte le richieste di accesso**, quindi scegliere **OK**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-177">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**<your organization name> **.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="f8b13-178">Fare clic su **campagne di marketing membri** nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="f8b13-178">Click **Campaign marketing Members** in the list.</span></span>
    
14. <span data-ttu-id="f8b13-179">Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-179">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="f8b13-180">Nella finestra di dialogo **Condividi** digitare **Senior e personale strategico**, selezionarlo e fare clic su **Condividi**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-180">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="f8b13-181">Ripetere i passaggi 14 e 15 per il gruppo di **agenti Analitica** e l'account utente **Regular1** .</span><span class="sxs-lookup"><span data-stu-id="f8b13-181">Repeat steps 14 and 15 for the **Analytics staff** group and the **Regular1** user account.</span></span>
    
17. <span data-ttu-id="f8b13-182">Fare clic sul pulsante Indietro del browser.</span><span class="sxs-lookup"><span data-stu-id="f8b13-182">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="f8b13-183">Nell'elenco, fare clic su **campagne di marketing proprietari** .</span><span class="sxs-lookup"><span data-stu-id="f8b13-183">Click **Campaign marketing Owners** in the list.</span></span>
    
19. <span data-ttu-id="f8b13-184">Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-184">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="f8b13-185">Nella finestra di dialogo **condivisione** digitare **il personale IT**, selezionarlo e fare clic su **Condividi**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-185">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="f8b13-186">Fare clic sul pulsante Indietro del browser.</span><span class="sxs-lookup"><span data-stu-id="f8b13-186">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="f8b13-187">Chiudere la scheda **utenti e gruppi** nel browser, fare clic sulla scheda **Home page di marketing campagne** nel browser e quindi chiudere il riquadro **autorizzazioni sito** .</span><span class="sxs-lookup"><span data-stu-id="f8b13-187">Close the **People and Groups** tab in your browser, click the **Campaign marketing-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="f8b13-188">Ecco i risultati della configurazione delle autorizzazioni:</span><span class="sxs-lookup"><span data-stu-id="f8b13-188">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="f8b13-189">Al gruppo di SharePoint **Membri di marketing campagna** contiene solo il **Senior e personale strategico** gruppo (che contiene gli account utente Candidate, ChiefOfStaff e Strategic1), il gruppo di **marketing campagne** (che include il account di utente amministratore globale), il gruppo di **agenti Analitica** (che include l'account utente DataScientist1) e l'account utente **Regular1** .</span><span class="sxs-lookup"><span data-stu-id="f8b13-189">The **Campaign marketing-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains the Candidate, ChiefOfStaff, and Strategic1 user accounts), the **Campaign marketing** group (which contains the global administrator user account), the **Analytics staff** group (which contains the DataScientist1 user account), and the **Regular1** user account.</span></span>
    
- <span data-ttu-id="f8b13-190">Gruppo di SharePoint **Proprietari di marketing campagna** contiene solo il gruppo di **personale IT** (che include solo gli account utente ITAdmin1 e ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="f8b13-190">The **Campaign marketing-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="f8b13-191">Gruppo di SharePoint **Visitatori di marketing campagne** non contiene gruppi o gli account utente.</span><span class="sxs-lookup"><span data-stu-id="f8b13-191">The **Campaign marketing-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="f8b13-192">Membri non possono modificare le autorizzazioni a livello di sito (ciò può essere eseguita solo dai membri del gruppo **Proprietari di marketing campagna** ).</span><span class="sxs-lookup"><span data-stu-id="f8b13-192">Members cannot modify site-level permissions (this can only be done by members of the **Campaign marketing-Owners** group).</span></span>
    
- <span data-ttu-id="f8b13-193">Altri account utente non possono accedere al sito o alle sue risorse, ma possono richiedere l'accesso al sito, che invierà un'e-mail alla cassetta postale dell'account utente ITAdmin1.</span><span class="sxs-lookup"><span data-stu-id="f8b13-193">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="f8b13-194">Successivamente, configurare la cartella dei documenti del sito del team Marketing della campagna per l'etichetta Riservato.</span><span class="sxs-lookup"><span data-stu-id="f8b13-194">Next, configure the documents folder of the Campaign marketing team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="f8b13-195">Nella scheda **Home page di marketing campagne** del browser fare clic su **documenti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-195">In the **Campaign marketing-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="f8b13-196">Fare clic sull'icona impostazioni e quindi fare clic su **Impostazioni raccolta**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-196">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="f8b13-197">Nella sezione **autorizzazioni e gestione**, fare clic su **Applica etichetta agli elementi della raccolta**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-197">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="f8b13-198">In **Applica impostazioni etichetta**, selezionare **riservati**e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-198">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="f8b13-p103">Successivamente, configurare un criterio di criterio DLP perdita di dati che informa gli utenti quando si condivide un documento in un sito del team di SharePoint Online con l'etichetta sensibile all'esterno dell'organizzazione. Tale criterio DLP verrà applicato alle risorse nel sito per campagne di marketing.</span><span class="sxs-lookup"><span data-stu-id="f8b13-p103">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label outside the organization. This DLP policy will apply to resources in the Campaign marketing site.</span></span>
  
1. <span data-ttu-id="f8b13-201">Nella scheda **Home page di Microsoft Office** nel browser, fare clic sul **protezione &amp; conformità** affiancate.</span><span class="sxs-lookup"><span data-stu-id="f8b13-201">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="f8b13-202">Nel nuovo computer **protezione &amp; conformità** nel browser, fare clic **prevenzione della perdita di dati > criteri**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-202">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="f8b13-203">Nel riquadro di **prevenzione della perdita di dati** , fare clic su **+ Crea un criterio**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-203">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="f8b13-204">Nella **iniziare con un modello o creare un criterio personalizzato** riquadro, fare clic su **personalizzata**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-204">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="f8b13-205">Nel riquadro **nome del criterio** digitare **siti del team di SharePoint Online riservati etichetta** **nome**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-205">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="f8b13-206">Nel riquadro **scegliere percorsi** , fare clic su **Seleziona manualmente percorsi specifici**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-206">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="f8b13-207">Nell'elenco delle posizioni, disattivare i percorsi di **posta elettronica di Exchange** e **gli account di OneDrive** e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-207">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="f8b13-208">Nel riquadro di **personalizzare i tipi di informazioni riservate che si desidera proteggere** , fare clic su **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-208">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="f8b13-209">Nel riquadro **scegliere i tipi di contenuto per la protezione** , fare clic su **Aggiungi** nella casella a discesa e quindi fare clic su **etichette**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-209">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="f8b13-210">Nel riquadro **etichette** fare clic su **+ Aggiungi**, selezionare l'etichetta **riservati** , fare clic su **Aggiungi**e quindi fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-210">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="f8b13-211">Nel riquadro **scegliere i tipi di contenuto per la protezione** , fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-211">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="f8b13-212">Nel riquadro di **personalizzare i tipi di informazioni riservate che si desidera proteggere** , fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-212">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="f8b13-213">Nella **Selezionare l'operazione da eseguire se si rileva informazioni riservate?** riquadro, fare clic su **Personalizza la descrizione e posta elettronica**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-213">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="f8b13-214">Nel riquadro **suggerimenti sui criteri di personalizzazione e notifiche tramite posta elettronica** , fare clic su **Personalizza il testo del suggerimento criteri**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-214">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="f8b13-215">Nella casella di testo digitare o incollare negli articoli seguenti:</span><span class="sxs-lookup"><span data-stu-id="f8b13-215">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="f8b13-p104">Per condividere con un utente esterno all'organizzazione, scaricare il file e quindi aprirlo. Fare clic su File, Proteggi documento, Crittografa con password, quindi specificare una password complessa. Inviare la password in un'e-mail separata o con altri mezzi di comunicazione.</span><span class="sxs-lookup"><span data-stu-id="f8b13-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="f8b13-219">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="f8b13-220">Nella **Selezionare l'operazione da eseguire se si rileva informazioni riservate?** riquadro, deselezionare la casella di controllo **Blocca la condivisione degli utenti e limitare l'accesso al contenuto condiviso** e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-220">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="f8b13-221">Nella **si desidera attivare le operazioni criteri o di testing prima?** riquadro, fare clic su **Sì, attivarlo immediatamente**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="f8b13-222">Nel riquadro di **Rivedere le impostazioni** , fare clic su **Crea**e quindi fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-222">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
### <a name="campaign-strategy-team-site"></a><span data-ttu-id="f8b13-223">Sito del team per la strategia della campagna</span><span class="sxs-lookup"><span data-stu-id="f8b13-223">Campaign strategy team site</span></span>

<span data-ttu-id="f8b13-224">Per creare un sito del team di SharePoint Online isolato al livello estremamente riservato per le risorse relative alla strategia della campagna, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f8b13-224">To create an isolated SharePoint Online team site at the highly confidential level for campaign strategy resources, do the following:</span></span>
  
1. <span data-ttu-id="f8b13-225">Se necessario, utilizzare un browser nel computer locale e accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) utilizzando l'account amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="f8b13-225">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="f8b13-226">Nell'elenco delle sezioni, fare clic su **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-226">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="f8b13-227">Nella scheda **SharePoint** nuovo nel browser, fare clic su **Crea sito +**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-227">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="f8b13-228">Nella pagina **Crea sito** fare clic su **sito del Team**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-228">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="f8b13-229">**Nome del sito del Team**, digitare **strategia campagne**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-229">In **Team site name**, type **Campaign strategy**.</span></span>
    
6. <span data-ttu-id="f8b13-230">Nella **descrizione del sito del Team**, digitare **il sito di SharePoint per la strategia di campagne (altamente riservato)**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-230">In **Team site description**, type **SharePoint site for campaign strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="f8b13-231">**Le impostazioni di Privacy**, selezionare **privato: solo membri possono accedere al sito**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-231">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="f8b13-232">Nella **che si desidera aggiungere?** riquadro, fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-232">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="f8b13-233">Nella scheda **strategia campagna di** nuovo nel browser, nella barra degli strumenti, fare clic sull'icona impostazioni e quindi fare clic su **autorizzazioni sito**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-233">On the new **Campaign strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="f8b13-234">Nel riquadro **autorizzazioni sito** fare clic su **impostazioni di autorizzazioni avanzate**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-234">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="f8b13-235">Nella scheda **autorizzazioni** nuova nel browser, fare clic su **Impostazioni richieste di accesso**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-235">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="f8b13-236">Nella finestra di dialogo **Impostazioni richieste di accesso** , deselezionare **Consenti ai membri di condividere il sito e i singoli file e cartelle** e **Consenti ai membri per invitare altre persone al gruppo membri del sito** (in modo che tutti i tre caselle di controllo è deselezionate), quindi fare clic su ** OK**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-236">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="f8b13-237">Fare clic su **strategia campagna membri** nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="f8b13-237">Click **Campaign strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="f8b13-238">Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-238">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="f8b13-239">Nella finestra di dialogo **Condividi** digitare **Senior e personale strategico**, selezionarlo e fare clic su **Condividi**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-239">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="f8b13-240">Nell'elenco, fare clic su **strategia campagna proprietari** .</span><span class="sxs-lookup"><span data-stu-id="f8b13-240">Click **Campaign strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="f8b13-241">Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-241">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="f8b13-242">Nella finestra di dialogo **condivisione** digitare **il personale IT**, selezionarlo e fare clic su **Condividi**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-242">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="f8b13-243">Fare clic sul pulsante Indietro del browser.</span><span class="sxs-lookup"><span data-stu-id="f8b13-243">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="f8b13-244">Chiudere la scheda **utenti e gruppi** nel browser, fare clic sulla scheda **home page della strategia di campagna** nel browser e quindi chiudere il riquadro **autorizzazioni sito** .</span><span class="sxs-lookup"><span data-stu-id="f8b13-244">Close the **People and Groups** tab in your browser, click the **Campaign strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="f8b13-245">Ecco i risultati della configurazione delle autorizzazioni:</span><span class="sxs-lookup"><span data-stu-id="f8b13-245">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="f8b13-246">Il gruppo di SharePoint **Membri di strategia campagna** contiene solo il gruppo **Senior e personale strategico** (che include solo gli account utente Candidate, ChiefOfStaff e Strategic1) e del gruppo **strategia campagna** (che include solo l'account amministratore globale utente).</span><span class="sxs-lookup"><span data-stu-id="f8b13-246">The **Campaign strategy-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains only the Candidate, ChiefOfStaff, and Strategic1 user accounts) and the **Campaign strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="f8b13-247">Gruppo di SharePoint **Proprietari di strategia campagna** contiene solo il gruppo di **personale IT** (che include solo gli account utente ITAdmin1 e ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="f8b13-247">The **Campaign strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="f8b13-248">Gruppo di SharePoint **Visitatori di strategia campagna** non contiene nessun account utente o gruppi.</span><span class="sxs-lookup"><span data-stu-id="f8b13-248">The **Campaign strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="f8b13-249">Membri non possono modificare le autorizzazioni a livello di sito (ciò può essere eseguita solo dai membri del gruppo **Proprietari di strategia campagna** ).</span><span class="sxs-lookup"><span data-stu-id="f8b13-249">Members cannot modify site-level permissions (this can only be done by members of the **Campaign strategy-Owners** group).</span></span>
    
- <span data-ttu-id="f8b13-p105">Altri account utente non può accedere al sito e le relative risorse o richiedere l'accesso al sito. Autorizzazioni aggiuntive per il sito devono essere eseguite dall'amministratore globale o da un membro del gruppo **Proprietari di strategia campagne** .</span><span class="sxs-lookup"><span data-stu-id="f8b13-p105">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Campaign strategy-Owners** group.</span></span>
    
<span data-ttu-id="f8b13-252">Successivamente, configurare la cartella dei documenti del sito del team Strategia della campagna per l'etichetta Estremamente riservato.</span><span class="sxs-lookup"><span data-stu-id="f8b13-252">Next, configure the documents folder of the Campaign strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="f8b13-253">Nella scheda **home page della strategia campagna** del browser fare clic su **documenti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-253">In the **Campaign strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="f8b13-254">Fare clic sull'icona impostazioni e quindi fare clic su **Impostazioni raccolta**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-254">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="f8b13-255">Nella sezione **autorizzazioni e gestione**, fare clic su **Applica etichetta agli elementi della raccolta**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-255">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="f8b13-256">In **Applica impostazioni etichetta**, selezionare **Altamente riservati**e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-256">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="f8b13-p106">Quindi, configurare un criterio DLP che gli utenti blocchi quando si condivide un documento in un sito del team di SharePoint Online con l'etichetta altamente riservati all'esterno dell'organizzazione. Tale criterio DLP verrà applicato alle risorse nel sito strategia campagne.</span><span class="sxs-lookup"><span data-stu-id="f8b13-p106">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label outside the organization. This DLP policy will apply to resources in the Campaign strategy site.</span></span>
  
1. <span data-ttu-id="f8b13-259">Se necessario, utilizzare un browser nel computer locale e accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) con un account che dispone del ruolo di amministratore della sicurezza o amministratore azienda.</span><span class="sxs-lookup"><span data-stu-id="f8b13-259">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="f8b13-260">Nella scheda **Home page di Microsoft Office** nel browser, fare clic sul **protezione &amp; conformità** affiancate.</span><span class="sxs-lookup"><span data-stu-id="f8b13-260">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="f8b13-261">Nel nuovo computer **protezione &amp; conformità** nel browser, fare clic **prevenzione della perdita di dati > criteri**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-261">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="f8b13-262">Nel riquadro di **prevenzione della perdita di dati** , fare clic su **+ Crea un criterio**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-262">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="f8b13-263">Nella **iniziare con un modello o creare un criterio personalizzato** riquadro, fare clic su **personalizzata**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-263">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="f8b13-264">Nel riquadro **nome del criterio** digitare **siti del team di SharePoint Online di altamente riservati etichetta** **nome**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-264">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="f8b13-265">Nel riquadro **scegliere percorsi** , fare clic su **Seleziona manualmente percorsi specifici**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-265">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="f8b13-266">Nell'elenco delle posizioni, disattivare i percorsi di **posta elettronica di Exchange** e **gli account di OneDrive** e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-266">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="f8b13-267">Nel riquadro di **personalizzare i tipi di informazioni riservate che si desidera proteggere** , fare clic su **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-267">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="f8b13-268">Nel riquadro **scegliere i tipi di contenuto per la protezione** , fare clic su **Aggiungi** nella casella a discesa e quindi fare clic su **etichette**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-268">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="f8b13-269">Nel riquadro **etichette** fare clic su **+ Aggiungi**, selezionare l'etichetta **Altamente riservati** , fare clic su **Aggiungi**e quindi fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-269">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="f8b13-270">Nel riquadro **scegliere i tipi di contenuto per la protezione** , fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-270">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="f8b13-271">Nel riquadro di **personalizzare i tipi di informazioni riservate che si desidera proteggere** , fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-271">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="f8b13-272">Nella **Selezionare l'operazione da eseguire se si rileva informazioni riservate?** riquadro, fare clic su **Personalizza la descrizione e posta elettronica**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-272">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="f8b13-273">Nel riquadro **suggerimenti sui criteri di personalizzazione e notifiche tramite posta elettronica** , fare clic su **Personalizza il testo del suggerimento criteri**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-273">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="f8b13-274">Nella casella di testo digitare o incollare negli articoli seguenti:</span><span class="sxs-lookup"><span data-stu-id="f8b13-274">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="f8b13-p107">Per condividere con un utente esterno all'organizzazione, scaricare il file e quindi aprirlo. Fare clic su File, Proteggi documento, Crittografa con password, quindi specificare una password complessa. Inviare la password in un'e-mail separata o con altri mezzi di comunicazione.</span><span class="sxs-lookup"><span data-stu-id="f8b13-p107">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="f8b13-278">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-278">Click **OK**.</span></span>
    
18. <span data-ttu-id="f8b13-279">Nella **Selezionare l'operazione da eseguire se si rileva informazioni riservate?** riquadro, selezionare **Richiedi motivazione aziendale per eseguire l'override**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-279">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="f8b13-280">Nella **si desidera attivare le operazioni criteri o di testing prima?** riquadro, fare clic su **Sì, attivarlo immediatamente**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-280">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="f8b13-281">Nel riquadro di **Rivedere le impostazioni** , fare clic su **Crea**e quindi fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-281">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="f8b13-282">Utilizzare le istruzioni riportate in [Attivare Azure RMS con l'interfaccia di amministrazione di Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="f8b13-282">Use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="f8b13-283">Configurare quindi la protezione delle informazioni di Azure con un nuovo criterio con ambito e secondaria etichetta per la protezione e autorizzazioni con le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f8b13-283">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="f8b13-p108">Accedere al portale di Office 365 con un account che dispone del ruolo Amministratore della sicurezza oppure Amministratore della società. Per informazioni, vedere [Dove accedere a Office 365 per le aziende](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="f8b13-p108">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="f8b13-286">In una scheda a parte del browser, accedere al portale di Azure ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="f8b13-286">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="f8b13-287">Se è la prima volta che viene configurato Azure Information Protection, consultare queste [istruzioni](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="f8b13-287">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="f8b13-288">Nel riquadro dell'elenco, fare clic su **Ulteriori servizi**, digitare **Informazioni**, quindi fare clic su **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-288">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="f8b13-289">Nel pannello **Azure Information Protection**, fare clic su **Criteri con ambiti > + Aggiungi un nuovo criterio**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-289">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="f8b13-290">Digitare **CampaignStrategy** **nome del criterio** e l' **etichetta per i documenti nel sito del team strategia campagna** nella **casella Descrizione**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-290">Type **CampaignStrategy** in **Policy name** and **Label for documents in the Campaign strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="f8b13-291">Fare clic su **Selezionare gli utenti o gruppi di ottenere il criterio > utenti/gruppi**e quindi selezionare **Senior e strategico personale**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-291">Click **Select which users or groups get this policy > User/Groups**, and then select **Senior and strategic staff**.</span></span>
    
8. <span data-ttu-id="f8b13-292">Fare clic su **Seleziona > OK**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-292">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="f8b13-293">Per l'etichetta **Estremamente riservato**, fare clic sui puntini di sospensione (…), quindi su **Aggiungi un'etichetta secondaria**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-293">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="f8b13-294">Digitare un nome per l'etichetta secondaria in **Nome** e una descrizione dell'etichetta in **Descrizione**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-294">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="f8b13-295">In **Configurare le autorizzazioni per documenti e messaggi di posta elettronica contenenti questa etichetta** fare clic su **Proteggi**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-295">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="f8b13-296">Nella sezione **Protezione** fare clic su **Azure (chiave cloud)**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-296">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="f8b13-297">Nel pannello **Protezione** fare clic su **+ Aggiungi autorizzazioni** in **Impostazioni di protezione**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-297">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="f8b13-298">Nel pannello **Aggiungi autorizzazioni**, in **Specifica utenti e gruppi** fare clic su **+ Sfoglia la directory**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-298">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="f8b13-299">Nel riquadro **AAD utenti e gruppi** selezionare **Senior e personale strategico**e quindi fare clic su **Seleziona**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-299">On the **AAD Users and Groups** pane, select **Senior and strategic staff**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="f8b13-300">In **Scegli autorizzazioni dal set di impostazioni**, deselezionare le caselle di controllo **Stampa**, **Copia ed estrai il contenuto** e **Inoltra**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-300">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="f8b13-301">Fare due volte clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-301">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="f8b13-302">Nel pannello **Etichetta secondaria** fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-302">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="f8b13-303">Chiudere il pannello del nuovo criterio con ambito.</span><span class="sxs-lookup"><span data-stu-id="f8b13-303">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="f8b13-304">Su blade **Azure Information protection - criteri con ambiti** , fare clic su **pubblica**e quindi fare clic su **Sì**.</span><span class="sxs-lookup"><span data-stu-id="f8b13-304">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="f8b13-305">È ora possibile iniziare a creare documenti in questi quattro siti e verificare l'accesso a tali con diversi account utente nella sottoscrizione di prova.</span><span class="sxs-lookup"><span data-stu-id="f8b13-305">You are now ready to begin creating documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span> 
  
<span data-ttu-id="f8b13-306">Per proteggere un documento con Azure Information Protection and questa nuova etichetta, è necessario [installare il client per la protezione delle informazioni di Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) in un computer di test, installare Office dal portale di Office 365 e quindi accedere da Microsoft Word con un account nel ** Senior e personale strategico** group dell'abbonamento prova.</span><span class="sxs-lookup"><span data-stu-id="f8b13-306">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **Senior and strategic staff** group of your trial subscription.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f8b13-307">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f8b13-307">See Also</span></span>

[<span data-ttu-id="f8b13-308">Guida sulla sicurezza Microsoft per organizzazioni che si occupano della campagna politica, no profit e altre organizzazioni agili</span><span class="sxs-lookup"><span data-stu-id="f8b13-308">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="f8b13-309">Configurare i gruppi e gli utenti per un ambiente di sviluppo e di testing campagne politici</span><span class="sxs-lookup"><span data-stu-id="f8b13-309">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="f8b13-310">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="f8b13-310">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="f8b13-311">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="f8b13-311">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




