---
title: Classificazione e assegnazione di un'etichetta ai dati nell'ambiente di sviluppo/test di Office 365
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
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: 'Riepilogo: configurare e dimostrare la classificazione e l''etichettatura dei dati tramite il client Azure Information Protection (AIP) nel proprio ambiente di sviluppo e testing di Office 365.'
ms.openlocfilehash: 06f7ebefad8b4d622ab225298155b4f117ff2b75
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="e1124-103">Classificazione e assegnazione di un'etichetta ai dati nell'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="e1124-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="e1124-104">**Riepilogo:** configurare e dimostrare la classificazione e l'etichettatura dei dati tramite il client Azure Information Protection (AIP) nel proprio ambiente di sviluppo e testing di Office 365.</span><span class="sxs-lookup"><span data-stu-id="e1124-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="e1124-p101">Il client Azure Information Protection consente di classificare un documento prima di caricarlo in una cartella di SharePoint Online in Office 365. Con le istruzioni disponibili in questo articolo, si installa il client Azure Information Protection e si esegue la classificazione dei dati. Per ulteriori informazioni, vedere [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span><span class="sxs-lookup"><span data-stu-id="e1124-p101">The Azure Information Protection client allows you to classify a document before you upload it to a SharePoint Online folder in Office 365. With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification. For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="e1124-108">Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e1124-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="e1124-109">Fase 1: creare l'ambiente di sviluppo/testing di Office 365</span><span class="sxs-lookup"><span data-stu-id="e1124-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="e1124-110">Seguire le istruzioni riportate in [Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="e1124-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="e1124-111">Fase 2: aggiungere la sottoscrizione di prova ad Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="e1124-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="e1124-p102">In questa fase, è necessario aggiungere Azure Information Protection all'ambiente di sviluppo/testing di Office 365 e abilitarlo per gli account utente. Se è stato configurato l'[Ambiente di sviluppo/test di Office 365 ed EMS](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), ignorare questa fase. La sottoscrizione di prova a Enterprise Mobility Suite include le licenze per Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="e1124-p102">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts. If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase. The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="e1124-115">Innanzitutto, registrarsi per la sottoscrizione di prova ad Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="e1124-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="e1124-116">Registrarsi per la sottoscrizione di prova ad Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="e1124-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="e1124-117">Da Internet Explorer o dal browser, visitare [http://portal.office.com](http://portal.office.com) e accedere all'account di amministratore globale di Office 365.</span><span class="sxs-lookup"><span data-stu-id="e1124-117">In Internet Explorer or your browser, go to [http://portal.office.com](http://portal.office.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="e1124-118">Nella scheda **Microsoft Office Home**, fare clic sulla sezione **Amministrazione**.</span><span class="sxs-lookup"><span data-stu-id="e1124-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="e1124-119">Nella scheda Amministrazione di Office 365, nella barra di spostamento sinistra, fare clic su **Fatturazione > Acquisto di servizi**.</span><span class="sxs-lookup"><span data-stu-id="e1124-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="e1124-p103">Nella pagina **Acquisto di servizi**, individuare la voce **Azure Information Protection Premium P2**. Posizionare il mouse su di essa e fare clic su **Avvia la versione di valutazione gratuita**.</span><span class="sxs-lookup"><span data-stu-id="e1124-p103">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item. Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="e1124-122">Nella pagina **Conferma l'ordine**, fare clic su **Prova adesso**.</span><span class="sxs-lookup"><span data-stu-id="e1124-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="e1124-123">Nella pagina **Ricevuta ordine**, fare clic su **Continua**.</span><span class="sxs-lookup"><span data-stu-id="e1124-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="e1124-124">Successivamente, attivare la licenza di Azure Information Protection per tutti gli account utente.</span><span class="sxs-lookup"><span data-stu-id="e1124-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="e1124-125">Nella scheda dell'interfaccia di amministrazione di Office 365, fare clic su **Utenti**.</span><span class="sxs-lookup"><span data-stu-id="e1124-125">On the Office 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="e1124-126">Nell'elenco di account utente, selezionare l'account dell'amministratore globale, quindi su **Modifica** per **Licenze per i prodotti**.</span><span class="sxs-lookup"><span data-stu-id="e1124-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="e1124-127">Impostare la licenza del prodotto per **Azure Information Protection Premium P2** su **Attiva**, fare clic su **Salva** e fare clic su **Chiudi** due volte.</span><span class="sxs-lookup"><span data-stu-id="e1124-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="e1124-128">Ripetere i passaggi 2 e 3 per gli altri account utente (dall'utente 1 all'utente 5).</span><span class="sxs-lookup"><span data-stu-id="e1124-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="e1124-129">A questo punto, l'ambiente di sviluppo/test di Office 365 dispone di:</span><span class="sxs-lookup"><span data-stu-id="e1124-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="e1124-130">Sottoscrizioni di prova ad Azure Information Protection e Office 365 E5 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="e1124-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="e1124-131">Tutti gli account utente abilitati per usare Office 365 E5 e Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="e1124-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="e1124-132">Fase 3: eseguire la classificazione dei dati</span><span class="sxs-lookup"><span data-stu-id="e1124-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="e1124-133">In questa fase, viene eseguita la classificazione dei dati utilizzando il client Azure Information Protection e il criterio Azure Information Protection predefinito.</span><span class="sxs-lookup"><span data-stu-id="e1124-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="e1124-134">Se si usa l'ambiente di sviluppo/testing di Office 365 simulato, è necessario innanzitutto installare Office 2016 su CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="e1124-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="e1124-135">Utilizzare il browser e visitare il [portale di Azure](http://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="e1124-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="e1124-136">Fare clic su **Gruppi di risorse >** [nome del proprio gruppo di risorse] **> CLIENT1 > Connetti**.</span><span class="sxs-lookup"><span data-stu-id="e1124-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="e1124-137">Da CLIENT1, eseguire Internet Explorer, visitare il portale di Office all'indirizzo [http://portal.office.com](http://portal.office.com), quindi accedere con il nome utente e la password dell'account User5.</span><span class="sxs-lookup"><span data-stu-id="e1124-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://portal.office.com](http://portal.office.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="e1124-138">Nella scheda **Microsoft Office Home**, fare clic su **Installa Office 2016**.</span><span class="sxs-lookup"><span data-stu-id="e1124-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="e1124-p104">Avviare il download e fare clic su **Sì**, quando viene richiesto dal controllo dell'account utente. Attendere che Office si installi. Al termine dell'operazione, fare clic su **Chiudi** per due volte.</span><span class="sxs-lookup"><span data-stu-id="e1124-p104">Run the download when prompted and click **Yes** when prompted by User Account Control. Wait for Office to install. When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="e1124-142">In seguito, installare il client Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="e1124-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="e1124-143">Nel browser in uso o Internet Explorer, accedere alla [pagina di download di Microsoft Azure Information Protection](https://www.microsoft.com/download/details.aspx?id=53018).</span><span class="sxs-lookup"><span data-stu-id="e1124-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="e1124-144">Se si usa la versione semplificata dell'ambiente di sviluppo/testing di Office 365, utilizzare il browser del computer locale.</span><span class="sxs-lookup"><span data-stu-id="e1124-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="e1124-145">Se si usa l'ambiente di sviluppo/testing di Office 365 simulato, eseguire Internet Explorer dal CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="e1124-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="e1124-146">Nella pagina di download **Microsoft Azure Information Protection**, fare clic su **Download**, selezionare **AzInfoProtection.exe** e infine **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="e1124-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="e1124-147">Quando richiesto, eseguire AzInfoProtection.exe.</span><span class="sxs-lookup"><span data-stu-id="e1124-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="e1124-148">Nella casella **Installare Azure Information Protection** del client, selezionare **Accetto**, quindi fare clic su **Sì**, quando viene richiesto dal controllo dell'account utente.</span><span class="sxs-lookup"><span data-stu-id="e1124-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="e1124-149">Nella casella **Operazione completata**, fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="e1124-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="e1124-150">Successivamente, eseguire la classificazione dei documenti.</span><span class="sxs-lookup"><span data-stu-id="e1124-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="e1124-151">Fare clic sull'icona di **Word** sulla barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="e1124-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="e1124-152">Quando richiesto, accedere con il nome e la password dell'account User5.</span><span class="sxs-lookup"><span data-stu-id="e1124-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="e1124-153">Se Office 2016 è stato installato su CLIENT1, nella casella **Per iniziare** fare clic su **Accetto**.</span><span class="sxs-lookup"><span data-stu-id="e1124-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="e1124-154">Fare clic su **Documento vuoto**.</span><span class="sxs-lookup"><span data-stu-id="e1124-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="e1124-155">Annotare la sezione **Protezione** della barra multifunzione presente nella scheda **Home** e la riga della classificazione dei documenti.</span><span class="sxs-lookup"><span data-stu-id="e1124-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="e1124-156">Nel documento vuoto, digitare testo.</span><span class="sxs-lookup"><span data-stu-id="e1124-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="e1124-157">Fare clic su **File > Salva**, digitare il nome **BeforeAIP** e fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="e1124-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="e1124-158">Nella riga relativa alle classi del documento, fare clic sulla freccia verso il basso per **Segreto**, quindi fare clic su **Tutta la società**.</span><span class="sxs-lookup"><span data-stu-id="e1124-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="e1124-159">Fare clic su **File > Salva con nome**, digitare il nome **AfterAIP** e fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="e1124-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="e1124-160">Fare clic su **Esplora File** sulla barra delle applicazioni, quindi aprire la cartella **Documenti**.</span><span class="sxs-lookup"><span data-stu-id="e1124-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="e1124-p105">Annotare le differenti dimensioni dei file dei documenti **BeforeAIP** e **AfterAIP**. Il documento AfterAIP è più grande perché contiene le informazioni di classificazione.</span><span class="sxs-lookup"><span data-stu-id="e1124-p105">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents. The AfterAIP document is larger because it contains the classification information.</span></span>
    
<span data-ttu-id="e1124-163">Successivamente, consentire a tutti gli utenti di accedere alla raccolta siti di supporto.</span><span class="sxs-lookup"><span data-stu-id="e1124-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="e1124-164">Nella scheda **Microsoft Office Home**, fare clic su **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="e1124-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="e1124-165">Dalla scheda **SharePoint**, fare clic su **Raccolta siti di supporto**.</span><span class="sxs-lookup"><span data-stu-id="e1124-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="e1124-166">In alto a destra, fare clic sull'icona **Impostazioni**, quindi selezionare **Condiviso con**.</span><span class="sxs-lookup"><span data-stu-id="e1124-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="e1124-167">In **Condividi "Raccolta siti di supporto"**, fare clic su **Impostazioni avanzate**.</span><span class="sxs-lookup"><span data-stu-id="e1124-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="e1124-168">Nell'elenco dei gruppi di SharePoint, fare clic su **Supporta membri raccolta siti**.</span><span class="sxs-lookup"><span data-stu-id="e1124-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="e1124-169">Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="e1124-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="e1124-170">In **Condividi "Raccolta siti di supporto"**, digitare **Tutti**, fare clic su **Tutti tranne gli utenti esterni**, quindi selezionare **Condividi**.</span><span class="sxs-lookup"><span data-stu-id="e1124-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="e1124-171">Chiudi la scheda **Utenti e gruppi**.</span><span class="sxs-lookup"><span data-stu-id="e1124-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="e1124-172">In seguito, accedere con l'account User5 e caricare il documento con protezione AIP nella cartella Documenti della raccolta siti di supporto.</span><span class="sxs-lookup"><span data-stu-id="e1124-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="e1124-173">Nella **Microsoft Office Home** in alto a destra, fare clic sull'icona dell'utente e quindi fare clic su **Disconnetti**.</span><span class="sxs-lookup"><span data-stu-id="e1124-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="e1124-174">Visitare [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="e1124-174">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="e1124-175">Nella pagina di ** accesso a Office 365 **, fare clic sul nome dell'account User5 e accedere.</span><span class="sxs-lookup"><span data-stu-id="e1124-175">On the ** Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="e1124-176">Nella scheda **Microsoft Office Home**, fare clic su **SharePoint > Raccolta siti di supporto**.</span><span class="sxs-lookup"><span data-stu-id="e1124-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="e1124-177">Fare clic su **Documenti**, scegliere **Carica**, fare clic sul documento **AfterAIP** e scegliere **Apri**.</span><span class="sxs-lookup"><span data-stu-id="e1124-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="e1124-178">Nella cartella Documenti della raccolta siti di supporto dovrebbe essere presente il documento AfterAIP.docx.</span><span class="sxs-lookup"><span data-stu-id="e1124-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="e1124-179">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e1124-179">See Also</span></span>

[<span data-ttu-id="e1124-180">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="e1124-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="e1124-181">Ambiente di sviluppo/test di Office 365 ed EMS</span><span class="sxs-lookup"><span data-stu-id="e1124-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="e1124-182">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="e1124-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


