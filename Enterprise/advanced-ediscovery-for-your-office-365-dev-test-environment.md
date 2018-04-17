---
title: Advanced eDiscovery per l'ambiente di sviluppo/test di Office 365
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
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: "Riepilogo: Configurare e illustrare eDiscovery avanzate di Office 365 con dati di esempio nell'ambiente di sviluppo e di testing di Office 365."
ms.openlocfilehash: e850cf7ebab806d8ff51176a3e88077a692c41ef
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a><span data-ttu-id="ca6e7-103">Advanced eDiscovery per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="ca6e7-103">Advanced eDiscovery for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="ca6e7-104">**Riepilogo:** Configurare e dimostrare l'utilizzo di Office 365 avanzate eDiscovery con dati di esempio nell'ambiente di sviluppo e di testing di Office 365.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-104">**Summary:** Configure and demonstrate Office 365 Advanced eDiscovery with sample data in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="ca6e7-p101">Office 365 eDiscovery avanzate consente di trovare rapidamente e analizzare le informazioni pertinenti attraverso i dati archiviati in Office 365, inclusi documenti e posta elettronica. Questo può salvare un'elevata quantità di tempo e denaro, soprattutto nelle situazioni di conservazione per controversia. Per ulteriori informazioni, vedere [eDiscovery avanzate di Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span><span class="sxs-lookup"><span data-stu-id="ca6e7-p101">Office 365 Advanced eDiscovery allows you to quickly find and analyze relevant information across the data that is stored in Office 365, including email and documents. This can save enormous amounts of time and expense, especially in litigation situations. For more information, see [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span></span>
  
<span data-ttu-id="ca6e7-108">Con le istruzioni disponibili in questo articolo, è possibile creare un insieme limitato di dati per una controversia fittizia relativa a un contratto e analizzarli con Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-108">With the instructions in this article, you create a small set of data for a fictional contract dispute and analyze it with Advanced eDiscovery.</span></span>
  
> [!TIP]
> <span data-ttu-id="ca6e7-109">Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi al Test Lab Guide di One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-109">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="ca6e7-110">Fase 1: creare l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="ca6e7-110">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="ca6e7-111">Se si desidera testare avanzate eDiscovery in un modo semplice con i requisiti minimi, seguire le istruzioni nella fase 2 e la fase 3 [dell'ambiente di sviluppo e di testing di Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="ca6e7-111">If you just want to test Advanced eDiscovery in a lightweight way with the minimum requirements, follow the instructions in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="ca6e7-112">Se si desidera testare avanzate eDiscovery in un'azienda simulata, seguire le istruzioni in [DirSync per l'ambiente di sviluppo e di testing di Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="ca6e7-112">If you want to test Advanced eDiscovery in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="ca6e7-p102">Test eDiscovery avanzate non sono necessari nell'ambiente aziendale simulato, che include una rete intranet simulata connessione a Internet e la sincronizzazione delle directory per una foresta Windows Server Active Directory. Viene fornito qui come un'opzione in modo che è possibile eseguire il test e la sperimentazione in un ambiente che rappresenta una tipica organizzazione.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-p102">Testing Advanced eDiscovery does not require the simulated enterprise environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can perform testing and experimentation in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a><span data-ttu-id="ca6e7-115">Fase 2: creare dati di esempio per Advanced eDiscovery</span><span class="sxs-lookup"><span data-stu-id="ca6e7-115">Phase 2: Create example data for Advanced eDiscovery</span></span>

<span data-ttu-id="ca6e7-116">In questa procedura, è possibile creare messaggi di posta elettronica che in seguito verranno analizzati in un caso di Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-116">In this procedure, you create email messages that will you later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="ca6e7-117">Aprire Internet Explorer e accedere a [https://outlook.com](https://outlook.com) all'account di Outlook creata nella fase 2[dell'ambiente di sviluppo e di testing di Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="ca6e7-117">Open Internet Explorer and sign in at [https://outlook.com](https://outlook.com) to the Outlook account you created in Phase 2 of[Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="ca6e7-118">Se è in uso l'ambiente di sviluppo/test leggero, aprire una sessione privata di Internet Explorer e accedere dal computer locale.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-118">If you are using the lightweight dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="ca6e7-119">Se si utilizza l'ambiente di sviluppo e di testing enterprise simulato, utilizzare il portale di Azure ([https://portal.azure.com](https://portal.azure.com)) per connettersi alla macchina virtuale CLIENT1 e quindi effettuare l'accesso da CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-119">If you are using the simulated enterprise dev/test environment, use the Azure portal ([https://portal.azure.com](https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="ca6e7-120">Nella scheda **Posta elettronica di Outlook** fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-120">On the **Outlook Mail** tab, click **New**.</span></span>
    
3. <span data-ttu-id="ca6e7-p103">Nella casella **a**digitare l'indirizzo di posta elettronica dell'account User6 dell'abbonamento valutazione ( **user6 @.** <organization name> **. onmicrosoft.com**).</span><span class="sxs-lookup"><span data-stu-id="ca6e7-p103">In **To**, type the email address of the User6 account of your trial subscription ( **user6@.**<organization name> **.onmicrosoft.com**).</span></span>
    
4. <span data-ttu-id="ca6e7-123">Per l'oggetto, digitare **1 e-mail di prova**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-123">For the subject, type **Test email 1**.</span></span>
    
5. <span data-ttu-id="ca6e7-124">Nel corpo, digitare **bozza contratto Tailspin**e quindi fare clic su **Invia**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-124">In the body, type **Tailspin contract draft**, and then click **Send**.</span></span>
    
6. <span data-ttu-id="ca6e7-125">Nella scheda **Posta elettronica di Outlook** fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-125">On the **Outlook Mail** tab, click **New**.</span></span>
    
7. <span data-ttu-id="ca6e7-126">Nella casella **a**digitare l'indirizzo di posta elettronica dell'account User6 della sottoscrizione di prova.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-126">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
8. <span data-ttu-id="ca6e7-127">Per l'oggetto, digitare **Test e-mail 2**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-127">For the subject, type **Test email 2**.</span></span>
    
9. <span data-ttu-id="ca6e7-128">Nel corpo, digitare **convocazione di riunione pranzo Tailspin**e quindi fare clic su **Invia**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-128">In the body, type **Tailspin lunch meeting**, and then click **Send**.</span></span>
    
10. <span data-ttu-id="ca6e7-129">Nella scheda **Posta elettronica di Outlook** fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-129">On the **Outlook Mail** tab, click **New**.</span></span>
    
11. <span data-ttu-id="ca6e7-130">Nella casella **a**digitare l'indirizzo di posta elettronica dell'account User6 della sottoscrizione di prova.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-130">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
12. <span data-ttu-id="ca6e7-131">Per l'oggetto, digitare **3 e-mail di prova**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-131">For the subject, type **Test email 3**.</span></span>
    
13. <span data-ttu-id="ca6e7-132">Nel corpo, digitare **disaccordo contratto Tailspin**e quindi fare clic su **Invia**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-132">In the body, type **Tailspin contract disagreement**, and then click **Send**.</span></span>
    
14. <span data-ttu-id="ca6e7-133">Fare clic sull'icona utente nell'angolo superiore destro e quindi fare clic su **Esci**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-133">Click the user icon in the upper right corner, and then click **Sign out**.</span></span>
    
15. <span data-ttu-id="ca6e7-134">Aprire una nuova scheda e accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) con il nome dell'account e la password dell'account User6 della sottoscrizione di prova.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-134">Open a new tab and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with the account name and password of the User6 account of your trial subscription.</span></span>
    
16. <span data-ttu-id="ca6e7-135">Nella scheda **portale di Office 365** , fare clic su **posta elettronica**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-135">On the **Office 365 portal** tab, click **Mail**.</span></span>
    
17. <span data-ttu-id="ca6e7-136">Nella scheda **- User6 - posta elettronica Outlook** , verificare che User6 ricevuto tutti i messaggi di posta tre elettronica dall'account di posta elettronica di Outlook.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-136">On the **Mail - User6 - Outlook** tab, verify that User6 received all three emails from the Outlook email account.</span></span>
    
18. <span data-ttu-id="ca6e7-137">Passare alla **scheda portale Office 365** per User6.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-137">Switch back to the **Office 365 portal tab** for User6.</span></span>
    
19. <span data-ttu-id="ca6e7-138">Fare clic sull'icona utente nell'angolo superiore destro e quindi fare clic su **disconnettersi.**</span><span class="sxs-lookup"><span data-stu-id="ca6e7-138">Click the user icon in the upper right corner, and then click **Sign out.**</span></span>
    
<span data-ttu-id="ca6e7-139">In questa procedura, è possibile creare due documenti Word che in seguito verranno analizzati in un caso di Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-139">In this procedure, you create two Word documents that will you will later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="ca6e7-140">Nella pagina **Office** , fare clic su **Accedi,** accedere con le credenziali dell'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-140">On the **Office** page, click **Sign in,** sign in with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="ca6e7-141">Accedere all'URL del sito di SharePoint di produzione in una nuova scheda: **https://** <fictional organization name> **.sharepoint.com/sites/production**</span><span class="sxs-lookup"><span data-stu-id="ca6e7-141">On a new tab, access the URL of your Production SharePoint site: **https://**<fictional organization name> **.sharepoint.com/sites/production**</span></span>
    
3. <span data-ttu-id="ca6e7-142">Nella scheda **raccolta siti di produzione** , in **documenti**, fare clic su **Nuovo > documento di Word**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-142">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
4. <span data-ttu-id="ca6e7-143">Nella pagina **Word Online** digitare **Tailspin bozza di contratto**, attendere finché non viene visualizzato **Saved** del titolo e quindi chiudere la scheda pagina **Word Online** .</span><span class="sxs-lookup"><span data-stu-id="ca6e7-143">On the **Word Online** page, type **Tailspin draft contract**, wait until it displays **Saved** in the title, and then close the **Word Online** page tab.</span></span>
    
5. <span data-ttu-id="ca6e7-144">Nella scheda **raccolta siti di produzione** , in **documenti**, fare clic su **Nuovo > documento di Word**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-144">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
6. <span data-ttu-id="ca6e7-145">Nella scheda **Word Online** digitare **Tailspin contratto controversia note**, attendere finché non viene visualizzato **Saved** del titolo e quindi chiudere la scheda **Word Online** .</span><span class="sxs-lookup"><span data-stu-id="ca6e7-145">On the **Word Online** tab, type **Tailspin contract dispute notes**, wait until it displays **Saved** in the title, and then close the **Word Online** tab.</span></span>
    
7. <span data-ttu-id="ca6e7-146">Nella scheda **raccolta siti di produzione** , si dovrebbero essere visualizzati **documento** e **Documento1** nell'elenco dei documenti.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-146">On the **Production site collection** tab, you should see **Document** and **Document1** in the list of documents.</span></span>
    
8. <span data-ttu-id="ca6e7-147">Chiudere la scheda **raccolta siti di produzione** .</span><span class="sxs-lookup"><span data-stu-id="ca6e7-147">Close the **Production site collection** tab.</span></span>
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a><span data-ttu-id="ca6e7-148">Fase 3: Utilizzare eDiscovery avanzate per una controversia legale</span><span class="sxs-lookup"><span data-stu-id="ca6e7-148">Phase 3: Use Advanced eDiscovery for a legal dispute</span></span>

<span data-ttu-id="ca6e7-p104">Purtroppo una controversia contratto tra l'organizzazione e Tailspin Toys ha raggiunto il punto di un'azione legale. In questa procedura, creare e configurare un caso eDiscovery avanzate per cercare e analizzare il messaggio di posta elettronica e documenti che contengono il testo "Contratto Tailspin".</span><span class="sxs-lookup"><span data-stu-id="ca6e7-p104">Unfortunately, a contract dispute between your organization and Tailspin Toys has reached the point of legal action. In this procedure, you create and configure an Advanced eDiscovery case to search for and analyze email and documents that contain the text "Tailspin contract".</span></span>
  
<span data-ttu-id="ca6e7-151">La procedura per l'uso di Advanced eDiscovery è la seguente:</span><span class="sxs-lookup"><span data-stu-id="ca6e7-151">The process for using Advanced eDiscovery is the following:</span></span>
  
- <span data-ttu-id="ca6e7-152">Creare una ricerca per la protezione &amp; centro conformità, analizzare i risultati e quindi preparare i risultati eDiscovery avanzate.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-152">Create a search in the Security &amp; Compliance center, analyze its results, and then prepare the results for Advanced eDiscovery.</span></span>
    
- <span data-ttu-id="ca6e7-153">Creare e configurare un caso di Advanced eDiscovery e analizzare i risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-153">Create and configure a case in Advanced eDiscovery and analyze the search results.</span></span>
    
<span data-ttu-id="ca6e7-154">In questa procedura si crea una ricerca per la protezione &amp; conformità center per "Contratto Tailspin", consultare i risultati e quindi preparare i risultati eDiscovery avanzate.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-154">In this procedure, you create a search in the Security &amp; Compliance center for "Tailspin contract", look at the results, and then prepare the results for Advanced eDiscovery.</span></span>
  
1. <span data-ttu-id="ca6e7-155">Nella scheda **portale di Office 365** , fare clic su **amministratore**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-155">From the **Office 365 portal** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="ca6e7-156">Nel riquadro di spostamento sinistro della scheda centro di amministrazione, fare clic su **Admin Center > conformità**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-156">In the left navigation of the Admin center tab, click **Admin centers > Compliance**.</span></span>
    
3. <span data-ttu-id="ca6e7-157">Nella **protezione &amp; conformità** fare clic su **autorizzazioni**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-157">On the **Security &amp; Compliance** tab, click **Permissions**.</span></span>
    
4. <span data-ttu-id="ca6e7-158">Nella casella **autorizzazioni** fare doppio clic su **Gestione organizzazione**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-158">In the **Permissions** list, double-click **Organization Management**.</span></span>
    
5. <span data-ttu-id="ca6e7-159">Nella finestra **Gruppo di ruoli** in **membri**, fare clic sul segno più.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-159">In the **Role Group** window, under **Members**, click the plus sign.</span></span>
    
6. <span data-ttu-id="ca6e7-160">Nella finestra **Selezione membri** , fare doppio clic sul nome dell'account di amministratore e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-160">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
7. <span data-ttu-id="ca6e7-161">Nella finestra di **Gruppo di ruoli** , fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-161">In the **Role Group** window, click **Save**.</span></span>
    
8. <span data-ttu-id="ca6e7-162">Nella casella **autorizzazioni** fare doppio clic su **eDiscovery Manager**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-162">In the **Permissions** list, double-click **eDiscovery Manager**.</span></span>
    
9. <span data-ttu-id="ca6e7-163">Nella finestra del **Gruppo di ruoli** **amministratore di eDiscovery**, fare clic sull'icona più.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-163">In the **Role Group** window, under **eDiscovery Administrator**, click the plus icon.</span></span>
    
10. <span data-ttu-id="ca6e7-164">Nella finestra **Selezione membri** , fare doppio clic sul nome dell'account di amministratore e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-164">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
11. <span data-ttu-id="ca6e7-165">Nella finestra di **Gruppo di ruoli** , fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-165">In the **Role Group** window, click **Save**.</span></span>
    
12. <span data-ttu-id="ca6e7-166">Nel riquadro di spostamento sinistra fare clic su **ricerca &amp; indagini > ricerca contenuto**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-166">In the left navigation, click **Search &amp; Investigation > Content search**.</span></span>
    
13. <span data-ttu-id="ca6e7-167">Fare clic sull'icona più per aggiungere una ricerca.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-167">Click the plus icon to add a search.</span></span>
    
14. <span data-ttu-id="ca6e7-168">Nella finestra della **nuova ricerca** , digitare **ricerca contratto Tailspin** nella **casella Nome**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-168">In the **New search** window, type **Tailspin contract search** in **Name**.</span></span>
    
15. <span data-ttu-id="ca6e7-169">In **dove si desidera di aspetto?**, fare clic su **ovunque, di ricerca** selezionare **Exchange**, **SharePoint**e **Le cartelle pubbliche**e quindi fare clic su **successivo.**</span><span class="sxs-lookup"><span data-stu-id="ca6e7-169">In **Where do you want us to look?**, click **Search everywhere,** select **Exchange**, **SharePoint**, and **Public Folders**, and then click **Next.**</span></span>
    
16. <span data-ttu-id="ca6e7-170">In **scegliere un'opzione di cercare?**digitare **contratto Tailspin**, fare clic su **Cerca**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-170">In **What do you want us to look for?**, type **Tailspin contract**, and then click **Search**.</span></span>
    
17. <span data-ttu-id="ca6e7-171">Nell'elenco delle ricerche, fare clic sul nome di **ricerca contratto Tailspin** .</span><span class="sxs-lookup"><span data-stu-id="ca6e7-171">In the list of searches, click the **Tailspin contract search** name.</span></span>
    
18. <span data-ttu-id="ca6e7-p105">Nel riquadro **Tailspin contratto ricerca** , fare clic su **Anteprima risultati di ricerca** **nell'area risultati della**. Verrà visualizzata una finestra che elenca i due documenti nel sito di SharePoint di produzione ( **documenti** e **Documento1**) e sui messaggi di **posta elettronica Test 1** e **3 e-mail di prova** a User6. Chiudere la finestra.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-p105">In the **Tailspin contract search** pane, click **Preview search results** under **Results**. You should see a window listing the two documents on the Production SharePoint site ( **Document** and **Document1**) and the **Test email 1** and **Test email 3** emails to User6. Close the window.</span></span>
    
19. <span data-ttu-id="ca6e7-175">Nel riquadro di **ricerca del contenuto** , **i risultati di analisi con eDiscovery avanzate**, fare clic su **Anteprima risultati per l'analisi**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-175">In the **Content search** pane, under **Analyze results with Advanced eDiscovery**, click **Preview results for analysis**.</span></span>
    
20. <span data-ttu-id="ca6e7-176">Nella finestra **dei risultati di preparare la ricerca per la ricerca contratto Tailspin** fare clic su **Prepara** e attendere che venga completato.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-176">In the **Prepare the search results for Tailspin contract search** window, click **Prepare** and wait for it to complete.</span></span>
    
<span data-ttu-id="ca6e7-177">In questa procedura, è possibile creare un nuovo caso di Advanced eDiscovery e analizzare i risultati della ricerca relativa al contratto Tailspin.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-177">In this procedure, you create a new case for Advanced eDiscovery and analyze the Tailspin contract search results.</span></span>
  
1. <span data-ttu-id="ca6e7-178">Nel riquadro di spostamento sinistra fare clic su **eDiscovery** in **ricerca &amp; indagini**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-178">In the left navigation, click **eDiscovery** under **Search &amp; Investigation**.</span></span>
    
2. <span data-ttu-id="ca6e7-179">Nel riquadro di **eDiscovery** , fare clic su **Vai a eDiscovery avanzate**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-179">In the **eDiscovery** pane, click **Go to Advanced eDiscovery**.</span></span>
    
3. <span data-ttu-id="ca6e7-180">Nella scheda **Impostazioni avanzate di eDiscovery** , fare clic sull'icona del segno più per aggiungere un nuovo caso.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-180">In the **Advanced eDiscovery** tab, click the plus icon to add a new case.</span></span>
    
4. <span data-ttu-id="ca6e7-p106">Nel riquadro **Add case** digitare **controversia contratto Tailspin** nella **casella Nome**e quindi fare clic su **OK**. Attendere il caso da creare.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-p106">In the **Add case** pane, type **Tailspin contract dispute** in **Name**, and then click **OK**. Wait for the case to be created.</span></span>
    
5. <span data-ttu-id="ca6e7-183">Fare doppio clic sul caso di **controversia contratto Tailspin** nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-183">Double click the **Tailspin contract dispute** case in the list.</span></span>
    
6. <span data-ttu-id="ca6e7-p107">Nell'elenco del **contenitore** , fare clic sul contenitore **ricerca contratto Tailspin** e quindi fare clic su **processo**. Attendere il completamento dell'elaborazione.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-p107">In the **Container** list, click the **Tailspin contract search** container, and then click **Process**. Wait for the processing to complete.</span></span>
    
7. <span data-ttu-id="ca6e7-186">Quando si **processo: completato** viene visualizzata nella parte inferiore della finestra, fare clic su **processo riepilogo** nel riquadro di spostamento sinistro per visualizzare un riepilogo.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-186">When **Process: completed** appears at the bottom of the window, click **Process summary** in the left navigation to see a summary.</span></span>
    
8. <span data-ttu-id="ca6e7-187">Nel riquadro di spostamento superiore fare clic su **Analyze**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-187">In the top navigation, click **Analyze**.</span></span>
    
9. <span data-ttu-id="ca6e7-188">Nella pagina **installazione** con **i temi**, digitare **3** **numero Max di temi**.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-188">On the **Setup** page, under **Themes**, type **3** in **Max number of themes**.</span></span>
    
10. <span data-ttu-id="ca6e7-p108">Fare clic su **Analyze** e attendere che l'analisi per il completamento. Dovrebbe essere visibile una serie di grafici a torta con analisi della popolazione target, documenti, messaggi di posta elettronica e allegati. Per ulteriori informazioni, vedere [visualizzazione di analizzare i risultati](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span><span class="sxs-lookup"><span data-stu-id="ca6e7-p108">Click **Analyze** and wait for the analysis to complete. You should see a series of pie charts with analysis of the target population, documents, emails, and attachments. For more information, see [Viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span></span>
    
<span data-ttu-id="ca6e7-192">È ora possibile usare questo ambiente per creare nuovi contenuti, nuove ricerche e casi e sperimentare ulteriormente Advanced eDiscovery in Office 365.</span><span class="sxs-lookup"><span data-stu-id="ca6e7-192">You can now use this environment to create new content, new searches and cases, and experiment further with Advanced eDiscovery in Office 365.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ca6e7-193">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ca6e7-193">See Also</span></span>

[<span data-ttu-id="ca6e7-194">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="ca6e7-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="ca6e7-195">Ambiente di sviluppo/test della configurazione di base</span><span class="sxs-lookup"><span data-stu-id="ca6e7-195">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="ca6e7-196">Ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="ca6e7-196">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="ca6e7-197">DirSync per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="ca6e7-197">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="ca6e7-198">Cloud App Security per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="ca6e7-198">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="ca6e7-199">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="ca6e7-199">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="ca6e7-200">EDiscovery avanzate di Office 365</span><span class="sxs-lookup"><span data-stu-id="ca6e7-200">Office 365 Advanced eDiscovery</span></span>](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


