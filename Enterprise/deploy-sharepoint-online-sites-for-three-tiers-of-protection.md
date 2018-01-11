---
title: Distribuzione di siti di SharePoint Online per tre livelli di protezione
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: 'Riepilogo: Creare e configurare siti del team SharePoint Online per i diversi livelli di protezione delle informazioni.'
ms.openlocfilehash: 7aa0107222454383abe0c1284b66ec0c4b808595
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a><span data-ttu-id="28723-103">Distribuzione di siti di SharePoint Online per tre livelli di protezione</span><span class="sxs-lookup"><span data-stu-id="28723-103">Deploy SharePoint Online sites for three tiers of protection</span></span>

 <span data-ttu-id="28723-104">**Riepilogo:** Creare e configurare siti del team SharePoint Online per i diversi livelli di protezione delle informazioni.</span><span class="sxs-lookup"><span data-stu-id="28723-104">**Summary:** Create and configure SharePoint Online team sites for various levels of information protection.</span></span>
  
<span data-ttu-id="28723-p101">Utilizzare i passaggi descritti in questo articolo per progettare e distribuire previsto, importanti o altamente riservati team siti di SharePoint Online. Per ulteriori informazioni su questi tre livelli di protezione, vedere [file e siti di SharePoint Online sicura](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="28723-p101">Use the steps in this article to design and deploy baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="baseline-sharepoint-online-team-sites"></a><span data-ttu-id="28723-107">Siti del team di SharePoint Online di base</span><span class="sxs-lookup"><span data-stu-id="28723-107">Baseline SharePoint Online team sites</span></span>

<span data-ttu-id="28723-p102">La protezione di base include siti del team pubblici e privati. I siti del team pubblici possono essere individuati e sono accessibili da chiunque nell'organizzazione. I siti privati possono essere individuati e sono accessibili solo dai membri del gruppo Office 365 associato al sito del team. Entrambi questi tipi di siti del team consentono ai membri di condividere il sito con altri utenti.</span><span class="sxs-lookup"><span data-stu-id="28723-p102">Baseline protection includes both public and private team sites. Public team sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the Office 365 group associated with the team site. Both of these types of team sites allow members to share the site with others.</span></span>
  
### <a name="public"></a><span data-ttu-id="28723-112">Pubblico</span><span class="sxs-lookup"><span data-stu-id="28723-112">Public</span></span>

<span data-ttu-id="28723-113">Per creare un sito del team di SharePoint Online di base con autorizzazioni e accesso pubblico, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="28723-113">To create a baseline SharePoint Online team site with public access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="28723-p103">Accedere al portale di Office 365 con un account che verrà utilizzato anche per amministrare il sito del team di SharePoint Online (un amministratore di SharePoint Online). Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="28723-p103">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="28723-116">Nell'elenco delle sezioni, fare clic su **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="28723-116">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="28723-117">Nella scheda **SharePoint** nuovo nel browser, fare clic su **Crea sito +**.</span><span class="sxs-lookup"><span data-stu-id="28723-117">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="28723-118">Nella pagina **Crea sito** fare clic su **sito del Team**.</span><span class="sxs-lookup"><span data-stu-id="28723-118">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="28723-119">In **nome sito**digitare un nome per il sito del team pubblica.</span><span class="sxs-lookup"><span data-stu-id="28723-119">In **Site name**, type a name for the public team site.</span></span> 
    
6. <span data-ttu-id="28723-120">Nella **descrizione del sito del Team**, digitare una descrizione dello scopo del sito.</span><span class="sxs-lookup"><span data-stu-id="28723-120">In **Team site description**, type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="28723-121">In **impostazioni di Privacy**, selezionare **Pubblica - tutti gli utenti dell'organizzazione possono accedere al sito**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28723-121">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="28723-122">Nella **che si desidera aggiungere?** riquadro, fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="28723-122">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="28723-123">Di seguito è riportata la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="28723-123">Here is your resulting configuration.</span></span>
  
![Protezione di livello di base per un sito del team di SharePoint Online pubblico.](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a><span data-ttu-id="28723-125">Privato</span><span class="sxs-lookup"><span data-stu-id="28723-125">Private</span></span>

<span data-ttu-id="28723-126">Per creare un sito del team di SharePoint Online di base con autorizzazioni e accesso privato, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="28723-126">To create a baseline SharePoint Online team site with private access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="28723-p104">Accedere al portale di Office 365 con un account che verrà utilizzato anche per amministrare il sito del team di SharePoint Online (un amministratore di SharePoint Online). Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="28723-p104">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="28723-129">Nell'elenco delle sezioni, fare clic su **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="28723-129">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="28723-130">Nella scheda **SharePoint** nuovo nel browser, fare clic su **Crea sito +**.</span><span class="sxs-lookup"><span data-stu-id="28723-130">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="28723-131">Nella pagina **Crea sito** fare clic su **sito del Team**.</span><span class="sxs-lookup"><span data-stu-id="28723-131">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="28723-132">In **nome sito**digitare un nome per il sito del team privata.</span><span class="sxs-lookup"><span data-stu-id="28723-132">In **Site name**, type a name for the private team site.</span></span> 
    
6. <span data-ttu-id="28723-133">Nella **casella Descrizione sito del Team,** digitare una descrizione dello scopo del sito.</span><span class="sxs-lookup"><span data-stu-id="28723-133">In **Team site description,** type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="28723-134">**Le impostazioni di Privacy**, selezionare **privato: solo membri possono accedere al sito**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28723-134">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="28723-135">Nella **che si desidera aggiungere?** riquadro, **aggiungere membri**, digitare i nomi degli account utente che dispongono dell'accesso al sito del team privata.</span><span class="sxs-lookup"><span data-stu-id="28723-135">On the **Who do you want to add?** pane, in **Add members**, type the names of user accounts that have access to this private team site.</span></span>
    
9. <span data-ttu-id="28723-136">Dopo aver aggiungendo l'insieme iniziale di membri per il sito, fare clic su **Fine**</span><span class="sxs-lookup"><span data-stu-id="28723-136">When you are done adding the initial set of members to the site, click **Finish**</span></span>
    
<span data-ttu-id="28723-137">Di seguito è riportata la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="28723-137">Here is your resulting configuration.</span></span>
  
![Protezione di livello di base per un sito del team di SharePoint Online privato.](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a><span data-ttu-id="28723-139">Siti del team di SharePoint Online riservati</span><span class="sxs-lookup"><span data-stu-id="28723-139">Sensitive SharePoint Online team sites</span></span>

<span data-ttu-id="28723-140">Un sito del team di SharePoint Online riservato è un sito del team isolato. Ciò significa che le autorizzazioni vengono controllate tramite l'appartenenza ai gruppi di SharePoint anziché tramite l’appartenenza al gruppo di Office 365 associato al sito del team.</span><span class="sxs-lookup"><span data-stu-id="28723-140">A sensitive SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="28723-141">Per creare un sito del team isolato, sono disponibili due passaggi principali.</span><span class="sxs-lookup"><span data-stu-id="28723-141">To create an isolated team site, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="28723-142">Passaggio 1: Progettare il sito isolato</span><span class="sxs-lookup"><span data-stu-id="28723-142">Step 1: Design your isolated site</span></span>

<span data-ttu-id="28723-143">Per progettare il sito del team isolato, è necessario determinare:</span><span class="sxs-lookup"><span data-stu-id="28723-143">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="28723-144">I gruppi di SharePoint e i livelli di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="28723-144">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="28723-145">Il set di gruppi di accesso che saranno membri dei gruppi di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="28723-145">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="28723-146">Il set di gruppi di accesso consigliato è un modello per i membri del sito, uno per i visualizzatori del sito e uno per gli amministratori del sito.</span><span class="sxs-lookup"><span data-stu-id="28723-146">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="28723-147">Se si utilizzeranno o meno gruppi annidati all'interno dei gruppi di accesso.</span><span class="sxs-lookup"><span data-stu-id="28723-147">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="28723-148">Ad esempio, i livelli di struttura e autorizzazione del gruppo consigliati sono analoghi a quanto segue:</span><span class="sxs-lookup"><span data-stu-id="28723-148">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="28723-149">**Gruppo di SharePoint**</span><span class="sxs-lookup"><span data-stu-id="28723-149">**SharePoint group**</span></span>|<span data-ttu-id="28723-150">**Livello di autorizzazione**</span><span class="sxs-lookup"><span data-stu-id="28723-150">**Permission level**</span></span>|<span data-ttu-id="28723-151">**Gruppo di accesso (esempi)**</span><span class="sxs-lookup"><span data-stu-id="28723-151">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="28723-152">[nome sito] Membri</span><span class="sxs-lookup"><span data-stu-id="28723-152">[site name] Members</span></span>  <br/> |<span data-ttu-id="28723-153">Modifica</span><span class="sxs-lookup"><span data-stu-id="28723-153">Edit</span></span>  <br/> |<span data-ttu-id="28723-154">[nome sito] Membri</span><span class="sxs-lookup"><span data-stu-id="28723-154">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="28723-155">[nome sito] Visitatori di</span><span class="sxs-lookup"><span data-stu-id="28723-155">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="28723-156">Lettura</span><span class="sxs-lookup"><span data-stu-id="28723-156">Read</span></span>  <br/> |<span data-ttu-id="28723-157">[nome sito] Visualizzatori</span><span class="sxs-lookup"><span data-stu-id="28723-157">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="28723-158">[nome sito] Proprietari</span><span class="sxs-lookup"><span data-stu-id="28723-158">[site name] Owners</span></span>  <br/> |<span data-ttu-id="28723-159">Controllo completo</span><span class="sxs-lookup"><span data-stu-id="28723-159">Full control</span></span>  <br/> |<span data-ttu-id="28723-160">[nome sito] Amministratori</span><span class="sxs-lookup"><span data-stu-id="28723-160">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="28723-p105">I gruppi di SharePoint e i livelli di autorizzazione vengono creati per impostazione predefinita per un sito del team. È necessario determinare i nomi dei gruppi di accesso.</span><span class="sxs-lookup"><span data-stu-id="28723-p105">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="28723-163">Per i dettagli del processo di progettazione, vedere [Progettazione di un sito del team di SharePoint Online isolato](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="28723-163">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="28723-164">Passaggio 2: Implementare il sito isolato</span><span class="sxs-lookup"><span data-stu-id="28723-164">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="28723-165">Per implementare il sito isolato, è innanzitutto necessario:</span><span class="sxs-lookup"><span data-stu-id="28723-165">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="28723-166">Determinare gli account utente e i gruppi da aggiungere a tutti i gruppi di accesso.</span><span class="sxs-lookup"><span data-stu-id="28723-166">Determine the user accounts and groups to add to each of your access groups.</span></span>
    
- <span data-ttu-id="28723-167">Creare gruppi di accesso e aggiungere l’utente e i membri dei gruppi.</span><span class="sxs-lookup"><span data-stu-id="28723-167">Create the access groups and add the user and group members.</span></span>
    
<span data-ttu-id="28723-168">Per ulteriori informazioni, vedere la **fase 1** di [distribuire un sito del team di SharePoint Online isolato](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="28723-168">For the detailed steps, see **Phase 1** of [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="28723-169">Successivamente, creare il sito del team di SharePoint Online seguendo questi passaggi.</span><span class="sxs-lookup"><span data-stu-id="28723-169">Next, you create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="28723-p106">Accedere al portale di Office 365 con un account che verrà utilizzato anche per amministrare il sito del team di SharePoint Online (un amministratore di SharePoint Online). Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="28723-p106">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="28723-172">Nell'elenco delle sezioni, fare clic su **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="28723-172">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="28723-173">In una nuova scheda **SharePoint** del browser, fare clic su **Crea sito +**.</span><span class="sxs-lookup"><span data-stu-id="28723-173">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="28723-174">Nella pagina **Crea sito** fare clic su **sito del Team**.</span><span class="sxs-lookup"><span data-stu-id="28723-174">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="28723-175">In **nome sito**digitare un nome per il sito del team privata.</span><span class="sxs-lookup"><span data-stu-id="28723-175">In **Site name**, type a name for the private team site.</span></span>
    
6. <span data-ttu-id="28723-176">Nella **descrizione del sito del Team**, digitare una descrizione facoltativa.</span><span class="sxs-lookup"><span data-stu-id="28723-176">In **Team site description**, type an optional description.</span></span>
    
7. <span data-ttu-id="28723-177">**Le impostazioni di Privacy**, selezionare **privato: solo membri possono accedere al sito**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28723-177">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="28723-178">Nella **che si desidera aggiungere?** riquadro, fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="28723-178">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="28723-179">Successivamente, dal nuovo sito del team di SharePoint Online configurare le autorizzazioni seguendo questi passaggi.</span><span class="sxs-lookup"><span data-stu-id="28723-179">Next, from the new SharePoint Online team site, configure permissions with these steps.</span></span>
  
1. <span data-ttu-id="28723-p107">Determinare il Nome dell'entità utente (UPN) di cui l'amministratore IT o altra persona sarà responsabile per rispondere a e indirizzare le richieste di accesso al sito (un esempio di UPN è belindan@contoso.com). Scrivere l’UPN di seguito: _________________________________________.</span><span class="sxs-lookup"><span data-stu-id="28723-p107">Determine the User Principal Name (UPN) of the IT administrator or other person who will be responsible for responding to and addressing requests for access to the site (belindan@contoso.com is an example of a UPN). Write that UPN here: _________________________________________.</span></span>
    
2. <span data-ttu-id="28723-182">Nella barra degli strumenti, fare clic sull'icona impostazioni e quindi fare clic su **autorizzazioni sito**.</span><span class="sxs-lookup"><span data-stu-id="28723-182">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
3. <span data-ttu-id="28723-183">Nel riquadro **autorizzazioni sito** fare clic su **impostazioni di autorizzazioni avanzate**.</span><span class="sxs-lookup"><span data-stu-id="28723-183">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
4. <span data-ttu-id="28723-184">Nella scheda **autorizzazioni** nuova del browser, fare clic su **Impostazioni richieste di accesso**.</span><span class="sxs-lookup"><span data-stu-id="28723-184">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
5. <span data-ttu-id="28723-185">Nella finestra di dialogo **Impostazioni di richieste di accesso** :</span><span class="sxs-lookup"><span data-stu-id="28723-185">In the **Access Requests Settings** dialog box:</span></span>
    
  - <span data-ttu-id="28723-186">Deselezionare le caselle di controllo **Consenti ai membri di condividere il sito e i singoli file e cartelle** e i **membri Consenti per invitare altre persone al gruppo membri del sito** .</span><span class="sxs-lookup"><span data-stu-id="28723-186">Clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes.</span></span>
    
  - <span data-ttu-id="28723-187">**Inviare tutte le richieste di accesso**digitare l'UPN dell'amministratore IT nel passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="28723-187">Type the UPN of your IT administrator from step 1 in **Send all requests for access**.</span></span>
    
  - <span data-ttu-id="28723-188">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="28723-188">Click **OK**.</span></span>
    
6. <span data-ttu-id="28723-189">Nella scheda **autorizzazioni** del browser fare clic su **[nome sito] membri** nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="28723-189">On the **Permissions** tab of your browser, click **[site name] Members** in the list.</span></span>
    
7. <span data-ttu-id="28723-190">In **utenti e gruppi**fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="28723-190">In **People and Groups**, click **New**.</span></span>
    
8. <span data-ttu-id="28723-191">Nella finestra di dialogo **condivisione** digitare il nome del gruppo di accesso membri del sito per il sito, selezionarlo e fare clic su **Condividi**.</span><span class="sxs-lookup"><span data-stu-id="28723-191">In the **Share** dialog box, type the name of your site members access group for this site, select it, and then click **Share**.</span></span>
    
9. <span data-ttu-id="28723-192">Fare clic sul pulsante Indietro del browser.</span><span class="sxs-lookup"><span data-stu-id="28723-192">Click the back button on your browser.</span></span>
    
10. <span data-ttu-id="28723-193">Fare clic su **[nome sito] proprietari** nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="28723-193">Click **[site name] Owners** in the list.</span></span>
    
11. <span data-ttu-id="28723-194">In **utenti e gruppi**fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="28723-194">In **People and Groups**, click **New**.</span></span>
    
12. <span data-ttu-id="28723-195">Nella finestra di dialogo **condivisione** digitare il nome del gruppo di accesso degli amministratori del sito per il sito, selezionarlo e fare clic su **Condividi**.</span><span class="sxs-lookup"><span data-stu-id="28723-195">In the **Share** dialog box, type the name of the site administrators access group for this site, select it, and then click **Share**.</span></span>
    
13. <span data-ttu-id="28723-196">Fare clic sul pulsante Indietro del browser.</span><span class="sxs-lookup"><span data-stu-id="28723-196">Click the back button on your browser.</span></span>
    
14. <span data-ttu-id="28723-197">Fare clic su **visitatori di [nome sito]** nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="28723-197">Click **[site name] Visitors** in the list.</span></span>
    
15. <span data-ttu-id="28723-198">In **utenti e gruppi**fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="28723-198">In **People and Groups**, click **New**.</span></span>
    
16. <span data-ttu-id="28723-199">Nella finestra di dialogo **condivisione** digitare il nome del gruppo di accesso i visualizzatori del sito per il sito, selezionarlo e fare clic su **Condividi**.</span><span class="sxs-lookup"><span data-stu-id="28723-199">In the **Share** dialog box, type the name of the site viewers access group for this site, select it, and then click **Share**.</span></span>
    
17. <span data-ttu-id="28723-200">Chiudere la scheda **autorizzazioni** della finestra del browser.</span><span class="sxs-lookup"><span data-stu-id="28723-200">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="28723-201">I risultati di queste impostazioni delle autorizzazioni sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="28723-201">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="28723-202">Gruppo di SharePoint **proprietari di [nome sito]** contiene gruppo access gli amministratori del sito, in cui tutti i membri dispongono del livello di autorizzazione **controllo completo** .</span><span class="sxs-lookup"><span data-stu-id="28723-202">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="28723-203">Gruppo di SharePoint **membri di [nome sito]** contiene il gruppo di accesso membri del sito, in cui tutti i membri dispongono del livello di autorizzazione **Modifica** .</span><span class="sxs-lookup"><span data-stu-id="28723-203">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="28723-204">Gruppo di SharePoint **visitatori di [nome sito]** contiene il gruppo di accesso i visualizzatori del sito, in cui tutti i membri dispongono del livello di autorizzazione **lettura** .</span><span class="sxs-lookup"><span data-stu-id="28723-204">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="28723-205">La possibilità per i membri di invitare altri membri è disattivata.</span><span class="sxs-lookup"><span data-stu-id="28723-205">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="28723-206">La possibilità per gli utenti non membri richiedere l'accesso è abilitata.</span><span class="sxs-lookup"><span data-stu-id="28723-206">The ability for non-members to request access is enabled.</span></span>
    
<span data-ttu-id="28723-207">Di seguito è riportata la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="28723-207">Here is your resulting configuration.</span></span>
  
![Protezione di livello riservato per un sito del team di SharePoint Online isolato.](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
<span data-ttu-id="28723-209">I membri del sito, tramite l'appartenenza a uno dei gruppi di accesso, possono, a questo punto, collaborare in tutta sicurezza utilizzando le risorse del sito.</span><span class="sxs-lookup"><span data-stu-id="28723-209">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a><span data-ttu-id="28723-210">Siti del team di SharePoint Online estremamente riservati</span><span class="sxs-lookup"><span data-stu-id="28723-210">Highly confidential SharePoint Online team sites</span></span>

<span data-ttu-id="28723-211">Un sito del team di SharePoint Online estremamente riservato è un sito del team isolato. Ciò significa che le autorizzazioni vengono controllate tramite l'appartenenza ai gruppi di SharePoint anziché tramite l’appartenenza al gruppo di Office 365 associato al sito del team.</span><span class="sxs-lookup"><span data-stu-id="28723-211">A highly confidential SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="28723-212">Per creare un sito del team isolato per informazioni estremamente riservate e collaborazioni, sono disponibili due passaggi principali.</span><span class="sxs-lookup"><span data-stu-id="28723-212">To create an isolated team site for highly confidential information and collaboration, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="28723-213">Passaggio 1: Progettare il sito isolato</span><span class="sxs-lookup"><span data-stu-id="28723-213">Step 1: Design your isolated site</span></span>

<span data-ttu-id="28723-214">Per progettare il sito del team isolato, è necessario determinare:</span><span class="sxs-lookup"><span data-stu-id="28723-214">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="28723-215">I gruppi di SharePoint e i livelli di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="28723-215">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="28723-216">Il set di gruppi di accesso che saranno membri dei gruppi di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="28723-216">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="28723-217">Il set di gruppi di accesso consigliato è un modello per i membri del sito, uno per i visualizzatori del sito e uno per gli amministratori del sito.</span><span class="sxs-lookup"><span data-stu-id="28723-217">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="28723-218">Se si utilizzeranno o meno gruppi annidati all'interno dei gruppi di accesso.</span><span class="sxs-lookup"><span data-stu-id="28723-218">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="28723-219">Ad esempio, i livelli di struttura e autorizzazione del gruppo consigliati sono analoghi a quanto segue:</span><span class="sxs-lookup"><span data-stu-id="28723-219">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="28723-220">**Gruppo di SharePoint**</span><span class="sxs-lookup"><span data-stu-id="28723-220">**SharePoint group**</span></span>|<span data-ttu-id="28723-221">**Livello di autorizzazione**</span><span class="sxs-lookup"><span data-stu-id="28723-221">**Permission level**</span></span>|<span data-ttu-id="28723-222">**Gruppo di accesso (esempi)**</span><span class="sxs-lookup"><span data-stu-id="28723-222">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="28723-223">[nome sito] Membri</span><span class="sxs-lookup"><span data-stu-id="28723-223">[site name] Members</span></span>  <br/> |<span data-ttu-id="28723-224">Modifica</span><span class="sxs-lookup"><span data-stu-id="28723-224">Edit</span></span>  <br/> |<span data-ttu-id="28723-225">[nome sito] Membri</span><span class="sxs-lookup"><span data-stu-id="28723-225">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="28723-226">[nome sito] Visitatori di</span><span class="sxs-lookup"><span data-stu-id="28723-226">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="28723-227">Lettura</span><span class="sxs-lookup"><span data-stu-id="28723-227">Read</span></span>  <br/> |<span data-ttu-id="28723-228">[nome sito] Visualizzatori</span><span class="sxs-lookup"><span data-stu-id="28723-228">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="28723-229">[nome sito] Proprietari</span><span class="sxs-lookup"><span data-stu-id="28723-229">[site name] Owners</span></span>  <br/> |<span data-ttu-id="28723-230">Controllo completo</span><span class="sxs-lookup"><span data-stu-id="28723-230">Full control</span></span>  <br/> |<span data-ttu-id="28723-231">[nome sito] Amministratori</span><span class="sxs-lookup"><span data-stu-id="28723-231">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="28723-p108">I gruppi di SharePoint e i livelli di autorizzazione vengono creati per impostazione predefinita per un sito del team. È necessario determinare i nomi dei gruppi di accesso.</span><span class="sxs-lookup"><span data-stu-id="28723-p108">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="28723-234">Per i dettagli del processo di progettazione, vedere [Progettazione di un sito del team di SharePoint Online isolato](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="28723-234">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="28723-235">Passaggio 2: Implementare il sito isolato</span><span class="sxs-lookup"><span data-stu-id="28723-235">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="28723-236">Per implementare il sito isolato, è innanzitutto necessario:</span><span class="sxs-lookup"><span data-stu-id="28723-236">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="28723-237">Determinare l’utente e i membri del gruppo di ciascun gruppo di accesso</span><span class="sxs-lookup"><span data-stu-id="28723-237">Determine the user and group members of each of your access groups</span></span>
    
- <span data-ttu-id="28723-238">Creare gruppi di accesso e aggiungere l’utente e i membri dei gruppi</span><span class="sxs-lookup"><span data-stu-id="28723-238">Create the access groups and add the user and group members</span></span>
    
- <span data-ttu-id="28723-239">Creare un sito del team isolato che utilizzi i gruppi di accesso</span><span class="sxs-lookup"><span data-stu-id="28723-239">Create an isolated team site that uses your access groups</span></span>
    
<span data-ttu-id="28723-240">Per ulteriori informazioni, vedere [distribuzione di un sito del team di SharePoint Online isolato](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="28723-240">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="28723-241">I risultati di queste impostazioni delle autorizzazioni sono:</span><span class="sxs-lookup"><span data-stu-id="28723-241">The results of the permission settings are:</span></span>
  
- <span data-ttu-id="28723-242">Gruppo di SharePoint **proprietari di [nome sito]** contiene gruppo access gli amministratori del sito, in cui tutti i membri dispongono del livello di autorizzazione **controllo completo** .</span><span class="sxs-lookup"><span data-stu-id="28723-242">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="28723-243">Gruppo di SharePoint **membri di [nome sito]** contiene il gruppo di accesso membri del sito, in cui tutti i membri dispongono del livello di autorizzazione **Modifica** .</span><span class="sxs-lookup"><span data-stu-id="28723-243">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="28723-244">Gruppo di SharePoint **visitatori di [nome sito]** contiene il gruppo di accesso i visualizzatori del sito, in cui tutti i membri dispongono del livello di autorizzazione **lettura** .</span><span class="sxs-lookup"><span data-stu-id="28723-244">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="28723-245">La possibilità per i membri di invitare altri membri è disattivata.</span><span class="sxs-lookup"><span data-stu-id="28723-245">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="28723-246">La possibilità per gli utenti non membri richiedere l'accesso è disattivata.</span><span class="sxs-lookup"><span data-stu-id="28723-246">The ability for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="28723-247">Di seguito è riportata la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="28723-247">Here is your resulting configuration.</span></span>
  
![Protezione di livello estremamente riservato per un team di SharePoint Online isolato.](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
<span data-ttu-id="28723-249">I membri del sito, tramite l'appartenenza a uno dei gruppi di accesso, possono, a questo punto, collaborare in tutta sicurezza utilizzando le risorse del sito.</span><span class="sxs-lookup"><span data-stu-id="28723-249">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="28723-250">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="28723-250">Next step</span></span>

[<span data-ttu-id="28723-251">Proteggere i file di SharePoint Online con Office 365 etichette e DLP</span><span class="sxs-lookup"><span data-stu-id="28723-251">Protect SharePoint Online files with Office 365 labels and DLP</span></span>](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a><span data-ttu-id="28723-252">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="28723-252">See Also</span></span>

[<span data-ttu-id="28723-253">Protezione di file e siti di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="28723-253">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="28723-254">Proteggere i siti di SharePoint Online in un ambiente di sviluppo e di testing</span><span class="sxs-lookup"><span data-stu-id="28723-254">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="28723-255">Guida sulla sicurezza Microsoft per organizzazioni che si occupano della campagna politica, no profit e altre organizzazioni agili</span><span class="sxs-lookup"><span data-stu-id="28723-255">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="28723-256">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="28723-256">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




