---
title: Ambiente di sviluppo/test di Office 365 e Dynamics 365
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
- Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: 'Riepilogo: Utilizzare questa guida del laboratorio di testing per aggiungere Dynamics 365 all''ambiente di sviluppo/test di Office 365.'
ms.openlocfilehash: d903d9ba268eca27baaaf12a003896990447a620
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="9f118-103">Ambiente di sviluppo/test di Office 365 e Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="9f118-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="9f118-104">**Riepilogo:** Utilizzare questa guida del laboratorio di testing per aggiungere Dynamics 365 all'ambiente di sviluppo/test di Office 365.</span><span class="sxs-lookup"><span data-stu-id="9f118-104">**Summary:** Use this Test Lab Guide to add Dynamics 365 to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="9f118-105">Con le istruzioni disponibili in questo articolo, è possibile aggiungere una sottoscrizione di valutazione di Dynamics 365 alla stessa organizzazione dell'ambiente di sviluppo/test di Office 365, creando un ambiente di sviluppo/test di Office 365 e Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="9f118-105">With the instructions in this article, you add a Dynamics 365 trial subscription to the same organization as your Office 365 dev/test environment, creating an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
<span data-ttu-id="9f118-p101">È possibile utilizzare una sottoscrizione di valutazione per Dynamics 365 per illustrare le funzionalità e le capacità di Dynamics 365. Le soluzioni seguenti sono incluse in una versione di valutazione di Dynamics 365 Plan 1 Enterprise Edition:</span><span class="sxs-lookup"><span data-stu-id="9f118-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="9f118-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Aumentare le vendite tramite l'automazione e l'intelligence digitale, consentendo ai venditori di restare concentrati e lavorare con maggiore efficienza.</span><span class="sxs-lookup"><span data-stu-id="9f118-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="9f118-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Conquista la fedeltà degli agenti fornendo loro le informazioni complete e l'intelligence digitale di cui hanno bisogno per offrire un servizio continuo.</span><span class="sxs-lookup"><span data-stu-id="9f118-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="9f118-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Padroneggiare le chiamate del servizio, ottimizzando pianificazioni, equipaggiando i dipendenti e usando strumenti predittivi per aumentare il profitto.</span><span class="sxs-lookup"><span data-stu-id="9f118-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="9f118-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/it-IT/dynamics365/project-service-automation). Completare correttamente i progetti e creare relazioni redditizie con dipendenti produttivi e strumenti intelligenti.</span><span class="sxs-lookup"><span data-stu-id="9f118-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/it-IT/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="9f118-116">Per la sottoscrizione di valutazione per 365 Dynamics, è possibile esplorare una o più delle soluzioni riportate.</span><span class="sxs-lookup"><span data-stu-id="9f118-116">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Guide dei laboratori di testing nel cloud Microsoft](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="9f118-118">Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9f118-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="9f118-119">Fase 1: creare l'ambiente di sviluppo/test di Office 365 aziendale leggero o simulato</span><span class="sxs-lookup"><span data-stu-id="9f118-119">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="9f118-120">Se si vuole semplicemente testare Office 365 e Dynamics 365 con i requisiti minimi, seguire le istruzioni riportate nelle fasi 2 e 3 di [Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="9f118-120">If you just want to test Office 365 and Dynamics 365 in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="9f118-121">Se si desidera testare Office 365 e Dynamics 365 per un'azienda simulata, seguire le istruzioni in [DirSync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="9f118-121">If you want to test Office 365 and Dynamics 365 for a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="9f118-p106">La configurazione riportata in questo articolo non richiede l'ambiente di sviluppo/test aziendale simulato, che include una rete Intranet simulata connessa a Internet e la sincronizzazione della directory per una foresta di Windows Server AD. Qui viene fornito come un'opzione in modo da poter sperimentare Office 365 e Dynamics 365 in un ambiente che rappresenta un'organizzazione tipica.</span><span class="sxs-lookup"><span data-stu-id="9f118-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="9f118-124">Fase 2: aggiungere una sottoscrizione di valutazione Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="9f118-124">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="9f118-125">In questa fase, è possibile iscriversi per la sottoscrizione di valutazione di Dynamics 365 e aggiungerla alla stessa organizzazione delle sottoscrizioni di prova di Office 365.</span><span class="sxs-lookup"><span data-stu-id="9f118-125">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="9f118-126">Iscriversi a  una sottoscrizione di valutazione Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="9f118-126">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="9f118-127">Utilizzando un browser sul computer desktop (configurazione leggera) o da CLIENT1 (configurazione aziendale simulata), accedere al portale di Office 365 su [https://portal.office.com](https://portal.office.com) con le credenziali dell'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="9f118-127">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="9f118-128">Fare clic sul riquadro **Amministratore**.</span><span class="sxs-lookup"><span data-stu-id="9f118-128">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="9f118-129">Nella scheda dell' **interfaccia di amministrazione di Office**, nella barra di spostamento sinistra, fare clic su **Fatturazione > Acquisto di servizi**.</span><span class="sxs-lookup"><span data-stu-id="9f118-129">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="9f118-p107">Nella pagina **Acquisto di servizi**, individuare la voce **Dynamics 365 Plan 1 Enterprise Edition**. Posizionare il puntatore del mouse su di essa e fare clic su **Avvia la versione di valutazione gratuita**.</span><span class="sxs-lookup"><span data-stu-id="9f118-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="9f118-132">Nella pagina **Conferma l'ordine**, fare clic su **Prova adesso**.</span><span class="sxs-lookup"><span data-stu-id="9f118-132">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="9f118-133">Nella pagina **Ricevuta ordine**, fare clic su **Continua**.</span><span class="sxs-lookup"><span data-stu-id="9f118-133">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="9f118-p108">La sottoscrizione di valutazione Dynamics 365 Plan 1 Enterprise Edition è valida per 30 giorni. È possibile estendere la sottoscrizione di prova per altri 30 giorni. Per un ambiente di sviluppo/test permanente, creare una nuova sottoscrizione a pagamento con un numero limitato di licenze.</span><span class="sxs-lookup"><span data-stu-id="9f118-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="9f118-137">Fase 3: Assegnare licenze Dynamics 365 e amministratori di sistema</span><span class="sxs-lookup"><span data-stu-id="9f118-137">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="9f118-138">In questa fase, vengono assegnate le licenze Dynamics 365 all'amministratore globale e agli account User 2 e User 3 rendendoli amministratori di sistema.</span><span class="sxs-lookup"><span data-stu-id="9f118-138">In this phase, you assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="9f118-139">Utilizzare questa procedura per assegnare le licenze Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="9f118-139">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="9f118-140">Nella scheda dell' **interfaccia di amministrazione di Office**, fare clic su **Utenti > Utenti attivi**.</span><span class="sxs-lookup"><span data-stu-id="9f118-140">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="9f118-141">Nell'elenco di utenti attivi, fare clic sull'account dell'amministratore globale, quindi su **Modifica** per **Licenze per i prodotti**.</span><span class="sxs-lookup"><span data-stu-id="9f118-141">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="9f118-142">Nel riquadro **Licenze per i prodotti**, impostare la licenza per i prodotti di **Dynamics 365 Plan 1 Enterprise Edition** su **Attiva**, fare clic su **Salva** e quindi fare doppio clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="9f118-142">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="9f118-143">Eseguire i passaggi 2 e 3 per gli account User 2 e User 3.</span><span class="sxs-lookup"><span data-stu-id="9f118-143">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="9f118-144">Chiudere la scheda dell' **interfaccia di amministrazione di Office**.</span><span class="sxs-lookup"><span data-stu-id="9f118-144">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="9f118-145">Seguire questi passaggi per configurare gli account User 2 e User 3 come amministratori di sistema di Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="9f118-145">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="9f118-146">Dalla scheda **Microsoft Office Home**, fare clic su **Amministratore**.</span><span class="sxs-lookup"><span data-stu-id="9f118-146">From the **Microsoft Office Home** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="9f118-147">Nella scheda dell' **interfaccia di amministrazione di Office**, nella barra di spostamento sinistra, fare clic su **Interfacce di amministrazione**, quindi su **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="9f118-147">On the **Office Admin center** tab, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="9f118-148">Potrebbe essere necessario attendere il completamento del provisioning di Dynamics 365 prima che Dynamics 365 venga visualizzato nel menu.</span><span class="sxs-lookup"><span data-stu-id="9f118-148">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="9f118-149">Nella scheda Dynamics 365, fare clic su **Tutti**, quindi su **Completa impostazione.**</span><span class="sxs-lookup"><span data-stu-id="9f118-149">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="9f118-150">Attendere il completamento dell'impostazione.</span><span class="sxs-lookup"><span data-stu-id="9f118-150">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="9f118-p109">Al termine dell'operazione, viene visualizzato un Dashboard impegni di vendita in base ai dati di esempio che fa parte della sottoscrizione di prova. Attendere alcuni minuti per visualizzare il video di **introduzione alla valutazione**. Al termine, chiudere la finestra del video.</span><span class="sxs-lookup"><span data-stu-id="9f118-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="9f118-154">Nella barra degli strumenti nella parte superiore, fare clic sulla freccia in giù accanto a **Vendite**, fare clic su **Impostazioni**, quindi su **Sicurezza**.</span><span class="sxs-lookup"><span data-stu-id="9f118-154">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="9f118-155">Nella pagina **Sicurezza**, fare clic su **Utenti**.</span><span class="sxs-lookup"><span data-stu-id="9f118-155">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="9f118-156">Nell'elenco di utenti, fare clic su **User 2**.</span><span class="sxs-lookup"><span data-stu-id="9f118-156">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="9f118-157">Nella barra degli strumenti, fare clic su **Gestisci ruoli**.</span><span class="sxs-lookup"><span data-stu-id="9f118-157">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="9f118-158">In **Gestisci ruoli**, fare clic su **Amministratore di sistema** e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="9f118-158">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="9f118-159">Nella barra degli strumenti nella parte superiore fare clic su **Sicurezza**.</span><span class="sxs-lookup"><span data-stu-id="9f118-159">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="9f118-160">Ripetere i passaggi 5-8 per l'account User 3.</span><span class="sxs-lookup"><span data-stu-id="9f118-160">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="9f118-161">Chiudere la scheda **Utente: Scheda User3**.</span><span class="sxs-lookup"><span data-stu-id="9f118-161">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="9f118-162">All'account di amministratore globale di Office 365 è stato assegnato automaticamente il ruolo di amministratore di sistema di Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="9f118-162">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="9f118-163">L’ambiente di sviluppo/test di Office 365 e Dynamics 365 ora dispone di:</span><span class="sxs-lookup"><span data-stu-id="9f118-163">Your Office 365 and Dynamics 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="9f118-164">Sottoscrizioni di valutazione di Office 365 E5 Enterprise e Dynamics 365 che condividono la stessa organizzazione e lo stesso tenant di Azure AD con l'elenco di account utente in uso.</span><span class="sxs-lookup"><span data-stu-id="9f118-164">Office 365 E5 Enterprise and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="9f118-165">Gli account di amministratore globale dell'organizzazione, User 2 e User 3 sono abilitati per l'utilizzo di Office 365 E5 Enterprise e Dynamics 365 e sono amministratori di sistema di Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="9f118-165">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use both Office 365 E5 Enterprise and Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="9f118-166">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="9f118-166">Next step</span></span>

<span data-ttu-id="9f118-167">Configurare e illustrare in che modo Office 365 e Dynamics 365 interagiscono nelle cassette postali di Exchange Online con [Integrazione di Exchange Online per il proprio ambiente di sviluppo/test di Office 365 e Dynamics 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span><span class="sxs-lookup"><span data-stu-id="9f118-167">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9f118-168">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9f118-168">See Also</span></span>

[<span data-ttu-id="9f118-169">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="9f118-169">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="9f118-170">Ambiente di sviluppo/test della configurazione di base</span><span class="sxs-lookup"><span data-stu-id="9f118-170">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="9f118-171">Ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="9f118-171">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="9f118-172">DirSync per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="9f118-172">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="9f118-173">Gestione della sottoscrizione per Dynamics 365 (Online)</span><span class="sxs-lookup"><span data-stu-id="9f118-173">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="9f118-174">Amministrare Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="9f118-174">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


