---
title: Ambiente di sviluppo/test One Microsoft Cloud
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: 'Riepilogo: Utilizzare questa guida dei laboratori di testing per creare un ambiente di sviluppo e di testing che includa tutte le offerte cloud di Microsoft.'
ms.openlocfilehash: c1d0e190e6d7e3871cf4289729b53cc0b4b5d04d
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="1b945-103">Ambiente di sviluppo/test One Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="1b945-103">The One Microsoft Cloud dev/test environment</span></span>

 <span data-ttu-id="1b945-104">**Riepilogo:** Utilizzare questa guida dei laboratori di testing per creare un ambiente di sviluppo e di testing che includa tutte le offerte cloud di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1b945-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes all of Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="1b945-p101">Con le istruzioni disponibili in questo articolo, si crea una rete Intranet simulata in Servizi infrastruttura di Microsoft Azure e quindi si aggiungono gli abbonamenti di Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS) e Microsoft Dynamics 365. Il risultato è un'organizzazione semplificata che utilizza tutte le offerte cloud di Microsoft contemporaneamente in un singolo ambiente di sviluppo/test. </span><span class="sxs-lookup"><span data-stu-id="1b945-p101">With the instructions in this article, you create a simulated intranet in Microsoft Azure infrastructure services and then add Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS), and Microsoft Dynamics 365 subscriptions. The result is a simplified organization that uses all Microsoft's cloud offerings at the same time in a single dev/test environment.</span></span> 
  
![Fase 3 dell'ambiente di sviluppo/test One Microsoft Cloud con Azure, Office 365, EMS e Dynamics 365](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
<span data-ttu-id="1b945-108">È possibile utilizzare la configurazione risultante per:</span><span class="sxs-lookup"><span data-stu-id="1b945-108">You can use the resulting configuration to:</span></span>
  
- <span data-ttu-id="1b945-109">Sfruttare l'integrazione tra le offerte cloud di Microsoft, come l'infrastruttura di gestione delle identità fornita da Azure Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="1b945-109">Experience the integration across Microsoft's cloud offerings, such as the common identity infrastructure provided by Azure Active Directory (AD).</span></span>
    
- <span data-ttu-id="1b945-110">Valutare gli scenari end-to-end che includono più offerte di Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="1b945-110">Evaluate end-to-end scenarios that include multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="1b945-111">Creare una demo, un modello di verifica o una configurazione di sviluppo/test che utilizzi più offerte di Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="1b945-111">Create a demo, proof-of-concept, or dev/test configuration that uses multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="1b945-112">Compilare le competenze di Microsoft Cloud per lo sviluppo professionale.</span><span class="sxs-lookup"><span data-stu-id="1b945-112">Build your Microsoft Cloud skills for professional development.</span></span>
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a><span data-ttu-id="1b945-113">Fase 1: creare una rete Intranet simulata e aggiungere Office 365</span><span class="sxs-lookup"><span data-stu-id="1b945-113">Phase 1: Create a simulated intranet and add Office 365</span></span>

<span data-ttu-id="1b945-114">Seguire le istruzioni riportate in [DirSync per l'ambiente di sviluppo e di testing di Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="1b945-114">Follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="1b945-115">Nella figura 1 viene illustrata la configurazione risultante, che include Office 365 e una rete intranet simulata in esecuzione in servizi di infrastruttura e la sincronizzazione delle directory da una foresta di Windows Server Active Directory (AD) locale.</span><span class="sxs-lookup"><span data-stu-id="1b945-115">Figure 1 shows your resulting configuration, which includes Office 365 and a simulated intranet running in Azure infrastructure services and directory synchronization from an on-premises Windows Server Active Directory (AD) forest.</span></span>
  
<span data-ttu-id="1b945-116">**Nella figura 1: Simulata intranet in Azure con Office 365**</span><span class="sxs-lookup"><span data-stu-id="1b945-116">**Figure 1: The simulated intranet in Azure with Office 365**</span></span>

![Ambiente di sviluppo e di testing Office 365 con DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> <span data-ttu-id="1b945-p102">La versione di valutazione di Azure è 30 giorni. La sottoscrizione di valutazione di Office 365 Enterprise E5 è 30 giorni, può essere facilmente estesa per altri 30 giorni. Per un ambiente di sviluppo e di testing permanente, creare un nuovo pagamento sottoscrizione Azure e una nuova sottoscrizione di Office 365 Enterprise E5 pagamento con un piccolo numero di licenze.</span><span class="sxs-lookup"><span data-stu-id="1b945-p102">The Azure trial is 30 days. The Office 365 Enterprise E5 Trial subscription is 30 days, which can be easily extended for another 30 days. For a permanent dev/test environment, create a new paid Azure subscription and a new paid Office 365 Enterprise E5 subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="1b945-121">Fase 2: aggiungere EMS</span><span class="sxs-lookup"><span data-stu-id="1b945-121">Phase 2: Add EMS</span></span>

<span data-ttu-id="1b945-122">In questa fase, è possibile iscriversi per la sottoscrizione di valutazione di EMS e aggiungerla alla stessa organizzazione della sottoscrizione di prova di Office 365.</span><span class="sxs-lookup"><span data-stu-id="1b945-122">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="1b945-123">Con un browser di uno computer desktop o da CLIENT1, accedere al portale di Office 365 in [https://portal.office.com](https://portal.office.com) con le credenziali dell'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="1b945-123">With a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="1b945-124">Scegliere il riquadro **Amministrazione**.</span><span class="sxs-lookup"><span data-stu-id="1b945-124">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="1b945-125">Nella scheda **Interfaccia di amministrazione di Office** del browser fare clic su **Fatturazione > Servizi di acquisto** nel riquadro di spostamento di sinistra.</span><span class="sxs-lookup"><span data-stu-id="1b945-125">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="1b945-p103">Nella pagina **servizi di acquisto** individuare l'elemento di **sicurezza E5 + mobilità aziendale** . Posizionare il puntatore del mouse su di esso e fare clic su **Start versione di valutazione gratuita**.</span><span class="sxs-lookup"><span data-stu-id="1b945-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="1b945-128">Nella pagina **Conferma l'ordine**, fare clic su **Prova adesso**.</span><span class="sxs-lookup"><span data-stu-id="1b945-128">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="1b945-129">Nella pagina **Ricevuta ordine**, fare clic su **Continua**.</span><span class="sxs-lookup"><span data-stu-id="1b945-129">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="1b945-p104">La sottoscrizione di valutazione Enterprise Mobility + Security E5 è valida per 90 giorni. Per un ambiente di sviluppo/test permanente, creare una nuova sottoscrizione a pagamento con un numero limitato di licenze.</span><span class="sxs-lookup"><span data-stu-id="1b945-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="1b945-132">Successivamente, attivare la licenza Enterprise Mobility + Security E5 per tutti gli account utente.</span><span class="sxs-lookup"><span data-stu-id="1b945-132">Next, enable the Enterprise Mobility + Security E5 license for all user accounts.</span></span>
  
1. <span data-ttu-id="1b945-133">Nella scheda **Interfaccia di amministrazione di Office 365** del browser fare clic su **Utenti > Utenti attivi** nel riquadro di spostamento di sinistra.</span><span class="sxs-lookup"><span data-stu-id="1b945-133">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="1b945-134">Fare clic sull'account di amministratore globale e quindi fare clic su **Modifica** per **le licenze del prodotto**.</span><span class="sxs-lookup"><span data-stu-id="1b945-134">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="1b945-135">Nel riquadro di **licenze per i prodotti** , attivare la licenza del prodotto per la **mobilità aziendale + E5 di sicurezza** per **in**, fare clic su **Salva** e quindi fare doppio clic su **Chiudi** .</span><span class="sxs-lookup"><span data-stu-id="1b945-135">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="1b945-136">Per tutti gli altri account (User1, User 2, User 3, User 4 e User 5), eseguire i passaggi 2 e 3.</span><span class="sxs-lookup"><span data-stu-id="1b945-136">For all of your other accounts (User1, User 2, User 3, User 4, and User 5), do steps 2 and 3.</span></span>
    
<span data-ttu-id="1b945-137">A questo punto, l'ambiente di sviluppo/test dispone di:</span><span class="sxs-lookup"><span data-stu-id="1b945-137">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="1b945-138">Una rete Intranet in esecuzione nei servizi infrastruttura di Azure.</span><span class="sxs-lookup"><span data-stu-id="1b945-138">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="1b945-139">Sottoscrizioni di valutazione di Office 365 E5 Enterprise ed EMS che condividono la stessa organizzazione e lo stesso tenant di Azure AD con l'elenco di account utente in uso.</span><span class="sxs-lookup"><span data-stu-id="1b945-139">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="1b945-140">Tutti gli account utente abilitati per usare Office 365 E5 ed EMS.</span><span class="sxs-lookup"><span data-stu-id="1b945-140">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
<span data-ttu-id="1b945-141">La figura 2 mostra la configurazione risultante che consente di aggiungere EMS.</span><span class="sxs-lookup"><span data-stu-id="1b945-141">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="1b945-142">**Figura 2: Simulata intranet in Azure con Office 365 ed EMS**</span><span class="sxs-lookup"><span data-stu-id="1b945-142">**Figure 2: The simulated intranet in Azure with Office 365 and EMS**</span></span>

![Fase 2 dell'ambiente di sviluppo/test One Microsoft Cloud con Azure, Office 365 ed EMS](images/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a><span data-ttu-id="1b945-144">Fase 3: Aggiungere Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="1b945-144">Phase 3: Add Dynamics 365</span></span>

<span data-ttu-id="1b945-145">In questa fase, è possibile iscriversi per la sottoscrizione di valutazione di Dynamics 365 e aggiungerla alla stessa organizzazione delle sottoscrizioni di prova di Office 365 ed EMS.</span><span class="sxs-lookup"><span data-stu-id="1b945-145">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 and EMS trial subscriptions.</span></span>
  
1. <span data-ttu-id="1b945-146">Utilizzando un browser in un computer desktop o da CLIENT1, accedere al portale di Office 365 in [https://portal.office.com](https://portal.office.com) con le credenziali dell'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="1b945-146">Using a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="1b945-147">Fare clic sul riquadro **Amministratore**.</span><span class="sxs-lookup"><span data-stu-id="1b945-147">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="1b945-148">Nella scheda dell' **interfaccia di amministrazione di Office**, nella barra di spostamento sinistra, fare clic su **Fatturazione > Acquisto di servizi**.</span><span class="sxs-lookup"><span data-stu-id="1b945-148">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="1b945-p105">Nella pagina **Acquisto di servizi**, individuare la voce **Dynamics 365 Plan 1 Enterprise Edition**. Posizionare il puntatore del mouse su di essa e fare clic su **Avvia la versione di valutazione gratuita**.</span><span class="sxs-lookup"><span data-stu-id="1b945-p105">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="1b945-151">Nella pagina **Conferma l'ordine**, fare clic su **Prova adesso**.</span><span class="sxs-lookup"><span data-stu-id="1b945-151">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="1b945-152">Nella pagina **Ricevuta ordine**, fare clic su **Continua**.</span><span class="sxs-lookup"><span data-stu-id="1b945-152">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="1b945-p106">La sottoscrizione di valutazione Dynamics 365 Plan 1 Enterprise Edition è valida per 30 giorni. È possibile estendere la sottoscrizione di prova per altri 30 giorni. Per un ambiente di sviluppo/test permanente, creare una nuova sottoscrizione a pagamento con un numero limitato di licenze.</span><span class="sxs-lookup"><span data-stu-id="1b945-p106">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="1b945-156">Utilizzare questa procedura per assegnare le licenze Dynamics 365 all'amministratore globale e agli account User 2 e User 3 e renderli amministratori di sistema.</span><span class="sxs-lookup"><span data-stu-id="1b945-156">Use these steps to assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
1. <span data-ttu-id="1b945-157">Nella scheda dell' **interfaccia di amministrazione di Office**, fare clic su **Utenti > Utenti attivi**.</span><span class="sxs-lookup"><span data-stu-id="1b945-157">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="1b945-158">Nell'elenco di utenti attivi, fare clic sull'account dell'amministratore globale, quindi su **Modifica** per **Licenze per i prodotti**.</span><span class="sxs-lookup"><span data-stu-id="1b945-158">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="1b945-159">Nel riquadro **Licenze per i prodotti**, impostare la licenza per i prodotti di **Dynamics 365 Plan 1 Enterprise Edition** su **Attiva**, fare clic su **Salva** e quindi fare doppio clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="1b945-159">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="1b945-160">Eseguire i passaggi 2 e 3 per gli account User 2 e User 3.</span><span class="sxs-lookup"><span data-stu-id="1b945-160">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="1b945-161">Chiudere la scheda dell' **interfaccia di amministrazione di Office**.</span><span class="sxs-lookup"><span data-stu-id="1b945-161">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="1b945-162">Seguire questi passaggi per configurare gli account User 2 e User 3 come amministratori di sistema di Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="1b945-162">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="1b945-163">Nella scheda di **interfaccia di amministrazione di Office** nel browser, nel riquadro di spostamento sinistra fare clic su **Admin Center**e quindi **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="1b945-163">On the **Office Admin center** tab in your browser, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="1b945-164">Potrebbe essere necessario attendere il completamento del provisioning di Dynamics 365 prima che Dynamics 365 venga visualizzato nel menu.</span><span class="sxs-lookup"><span data-stu-id="1b945-164">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
2. <span data-ttu-id="1b945-165">Nella scheda Dynamics 365, fare clic su **Tutti**, quindi su **Completa impostazione.**</span><span class="sxs-lookup"><span data-stu-id="1b945-165">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="1b945-166">Attendere il completamento dell'impostazione.</span><span class="sxs-lookup"><span data-stu-id="1b945-166">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="1b945-p107">Al termine dell'operazione, viene visualizzato un Dashboard impegni di vendita in base ai dati di esempio che fa parte della sottoscrizione di prova. Attendere alcuni minuti per visualizzare il video di **introduzione alla valutazione**. Al termine, chiudere la finestra del video.</span><span class="sxs-lookup"><span data-stu-id="1b945-p107">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
3. <span data-ttu-id="1b945-170">Nella barra degli strumenti nella parte superiore, fare clic sulla freccia in giù accanto a **Vendite**, fare clic su **Impostazioni**, quindi su **Sicurezza**.</span><span class="sxs-lookup"><span data-stu-id="1b945-170">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
4. <span data-ttu-id="1b945-171">Nella pagina **Sicurezza**, fare clic su **Utenti**.</span><span class="sxs-lookup"><span data-stu-id="1b945-171">On the **Security** page, click **Users**.</span></span>
    
5. <span data-ttu-id="1b945-172">Nell'elenco di utenti, fare clic su **User 2**.</span><span class="sxs-lookup"><span data-stu-id="1b945-172">In the list of users, click **User 2**.</span></span>
    
6. <span data-ttu-id="1b945-173">Nella barra degli strumenti, fare clic su **Gestisci ruoli**.</span><span class="sxs-lookup"><span data-stu-id="1b945-173">In the tool bar, click **Manage Roles**.</span></span>
    
7. <span data-ttu-id="1b945-174">In **Gestisci ruoli**, fare clic su **Amministratore di sistema** e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="1b945-174">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="1b945-175">Nella barra degli strumenti nella parte superiore fare clic su **Sicurezza**.</span><span class="sxs-lookup"><span data-stu-id="1b945-175">In the tool bar at the top click **Security**.</span></span>
    
9. <span data-ttu-id="1b945-176">Ripetere i passaggi 5-8 per l'account User 3.</span><span class="sxs-lookup"><span data-stu-id="1b945-176">Repeat steps 5-8 for the User 3 account.</span></span>
    
10. <span data-ttu-id="1b945-177">Chiudere la scheda **Utente: Scheda User3**.</span><span class="sxs-lookup"><span data-stu-id="1b945-177">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="1b945-178">All'account di amministratore globale di Office 365 è stato assegnato automaticamente il ruolo di amministratore di sistema di Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="1b945-178">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="1b945-179">A questo punto, l'ambiente di sviluppo/test dispone di:</span><span class="sxs-lookup"><span data-stu-id="1b945-179">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="1b945-180">Una rete Intranet in esecuzione nei servizi infrastruttura di Azure.</span><span class="sxs-lookup"><span data-stu-id="1b945-180">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="1b945-181">Sottoscrizioni di valutazione di Office 365 E5 Enterprise, EMS e Dynamics 365 che condividono la stessa organizzazione e lo stesso tenant di Azure AD con l'elenco di account utente in uso.</span><span class="sxs-lookup"><span data-stu-id="1b945-181">Office 365 E5 Enterprise, EMS, and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="1b945-182">Tutti gli account utente abilitati per usare Office 365 E5 ed EMS.</span><span class="sxs-lookup"><span data-stu-id="1b945-182">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
- <span data-ttu-id="1b945-183">Gli account di amministratore globale dell'organizzazione, User 2 e User 3 sono abilitati per l'utilizzo di Dynamics 365 e sono amministratori di sistema di Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="1b945-183">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
<span data-ttu-id="1b945-184">Nella figura 3 è riportata la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="1b945-184">Figure 3 shows your resulting configuration.</span></span>
  
<span data-ttu-id="1b945-185">**Figura 3: Simulata intranet in Azure con Office 365, EMS e Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="1b945-185">**Figure 3: The simulated intranet in Azure with Office 365, EMS, and Dynamics 365**</span></span>

![Fase 3 dell'ambiente di sviluppo/test One Microsoft Cloud con Azure, Office 365, EMS e Dynamics 365](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a><span data-ttu-id="1b945-187">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="1b945-187">Next steps</span></span>

<span data-ttu-id="1b945-p108">È ora possibile sperimentare l'ambiente di sviluppo/test di One Microsoft Cloud. Ecco alcune idee per esperienze guidate:</span><span class="sxs-lookup"><span data-stu-id="1b945-p108">You can now experiment with your One Microsoft Cloud dev/test environment. Here are some ideas for guided experiences:</span></span>
  
- [<span data-ttu-id="1b945-190">Configurare i criteri di gestione (MAM) mobile applicazione EMS per le applicazioni di Office 365</span><span class="sxs-lookup"><span data-stu-id="1b945-190">Configure mobile application management (MAM) policies in EMS for Office 365 applications</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="1b945-191">Effettuare una dimostrazione Exchange Online in Office 365 integrazione con i contatti Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="1b945-191">Demonstrate Exchange Online in Office 365 integration with Dynamics 365 contacts</span></span>](https://technet.microsoft.com/library/mt798313.aspx)
    
- [<span data-ttu-id="1b945-192">Creare una rete simulato tra locali in servizi di infrastruttura per l'hosting dei carichi di lavoro basate su server</span><span class="sxs-lookup"><span data-stu-id="1b945-192">Create a simulated cross-premises network in Azure infrastructure services for hosting server-based workloads</span></span>](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a><span data-ttu-id="1b945-193">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1b945-193">See Also</span></span>

[<span data-ttu-id="1b945-194">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="1b945-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="1b945-195">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="1b945-195">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="1b945-196">Soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="1b945-196">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="1b945-197">Soluzioni di sicurezza</span><span class="sxs-lookup"><span data-stu-id="1b945-197">Security solutions</span></span>](security-solutions.md)





