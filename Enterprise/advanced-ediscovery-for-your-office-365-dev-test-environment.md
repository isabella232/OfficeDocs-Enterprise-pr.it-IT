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
description: "Riepilogo: configurazione e dimostrazione di Office 365 Advanced eDiscovery con dati di esempio nell'ambiente di sviluppo/test di Office 365."
ms.openlocfilehash: 6c52c7c7fdc31616e58f186484d2d8c4506b7ea6
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573820"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a><span data-ttu-id="723e2-103">Advanced eDiscovery per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="723e2-103">Advanced eDiscovery for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="723e2-104">**Riepilogo:** configurazione e dimostrazione di Office 365 Advanced eDiscovery con dati di esempio nell'ambiente di sviluppo/test di Office 365.</span><span class="sxs-lookup"><span data-stu-id="723e2-104">**Summary:** Configure and demonstrate Office 365 Advanced eDiscovery with sample data in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="723e2-105">Office 365 Advanced eDiscovery consente di trovare e analizzare rapidamente le informazioni rilevanti tra i dati archiviati in Office 365, inclusi i messaggi di posta elettronica e i documenti.</span><span class="sxs-lookup"><span data-stu-id="723e2-105">Office 365 Advanced eDiscovery lets you quickly find and analyze relevant information across the data that is stored in Office 365, including email and documents.</span></span> <span data-ttu-id="723e2-106">Ciò consente di ridurre notevolmente la quantità necessaria di tempo e di spese, in particolare nelle situazioni di controversie legali.</span><span class="sxs-lookup"><span data-stu-id="723e2-106">This can save enormous amounts of time and expense, especially in litigation situations.</span></span> <span data-ttu-id="723e2-107">Per ulteriori informazioni, vedere [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span><span class="sxs-lookup"><span data-stu-id="723e2-107">For more information, see [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span></span>
  
<span data-ttu-id="723e2-108">Con le istruzioni disponibili in questo articolo, è possibile creare un insieme limitato di dati per una controversia fittizia relativa a un contratto e analizzarli con Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="723e2-108">With the instructions in this article, you create a small set of data for a fictional contract dispute and analyze it with Advanced eDiscovery.</span></span>
  
> [!TIP]
> <span data-ttu-id="723e2-109">Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida al lab test cloud di One Microsoft.</span><span class="sxs-lookup"><span data-stu-id="723e2-109">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="723e2-110">Fase 1: creare l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="723e2-110">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="723e2-111">Se si desidera semplicemente testare Advanced eDiscovery con i requisiti minimi, seguire le istruzioni riportate nella fase 2 e nella fase 3 dell' [ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="723e2-111">If you just want to test Advanced eDiscovery in a lightweight way with the minimum requirements, follow the instructions in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="723e2-112">Se si desidera testare Advanced eDiscovery in un'azienda simulata, seguire le istruzioni in [dirsync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="723e2-112">If you want to test Advanced eDiscovery in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="723e2-113">Il test di Advanced eDiscovery non richiede l'ambiente aziendale simulato, che include una rete Intranet simulata connessa a Internet e la sincronizzazione della directory per una foresta di Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="723e2-113">Testing Advanced eDiscovery does not require the simulated enterprise environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest.</span></span> <span data-ttu-id="723e2-114">Viene fornito come opzione in modo che sia possibile eseguire test e sperimentazione in un ambiente che rappresenta un'organizzazione tipica.</span><span class="sxs-lookup"><span data-stu-id="723e2-114">It is provided here as an option so that you can perform testing and experimentation in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a><span data-ttu-id="723e2-115">Fase 2: creare dati di esempio per Advanced eDiscovery</span><span class="sxs-lookup"><span data-stu-id="723e2-115">Phase 2: Create example data for Advanced eDiscovery</span></span>

<span data-ttu-id="723e2-116">In questa procedura, è possibile creare messaggi di posta elettronica che in seguito verranno analizzati in un caso di Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="723e2-116">In this procedure, you create email messages that will you later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="723e2-117">Aprire Internet Explorer e accedere all'account [https://outlook.com](https://outlook.com) di Outlook creato nella fase 2 dell'[ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="723e2-117">Open Internet Explorer and sign in at [https://outlook.com](https://outlook.com) to the Outlook account you created in Phase 2 of[Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="723e2-118">Se è in uso l'ambiente di sviluppo/test leggero, aprire una sessione privata di Internet Explorer e accedere dal computer locale.</span><span class="sxs-lookup"><span data-stu-id="723e2-118">If you are using the lightweight dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="723e2-119">Se si utilizza l'ambiente di sviluppo/testing dell'organizzazione simulata, utilizzare il portale[https://portal.azure.com](https://portal.azure.com)di Azure () per connettersi alla macchina virtuale CLIENT1 e quindi eseguire l'accesso da CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="723e2-119">If you are using the simulated enterprise dev/test environment, use the Azure portal ([https://portal.azure.com](https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="723e2-120">Nella scheda **Posta di Outlook**, fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="723e2-120">On the **Outlook Mail** tab, click **New**.</span></span>
    
3. <span data-ttu-id="723e2-121">In **a**, digitare l'indirizzo di posta elettronica dell'account di USER6 della sottoscrizione di valutazione ( **USER6 @.**<organization name></span><span class="sxs-lookup"><span data-stu-id="723e2-121">In **To**, type the email address of the User6 account of your trial subscription ( **user6@.**<organization name></span></span> <span data-ttu-id="723e2-122">**. onmicrosoft.com**).</span><span class="sxs-lookup"><span data-stu-id="723e2-122">**.onmicrosoft.com**).</span></span>
    
4. <span data-ttu-id="723e2-123">Per l'oggetto, digitare **Messaggio di posta elettronica di prova 1**.</span><span class="sxs-lookup"><span data-stu-id="723e2-123">For the subject, type **Test email 1**.</span></span>
    
5. <span data-ttu-id="723e2-124">Nel corpo del messaggio, digitare **Bozza contratto Tailspin**, quindi fare clic su **Invia**.</span><span class="sxs-lookup"><span data-stu-id="723e2-124">In the body, type **Tailspin contract draft**, and then click **Send**.</span></span>
    
6. <span data-ttu-id="723e2-125">Nella scheda **Posta di Outlook**, fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="723e2-125">On the **Outlook Mail** tab, click **New**.</span></span>
    
7. <span data-ttu-id="723e2-126">In **A**, digitare l'indirizzo di posta elettronica dell'account di User6 della sottoscrizione di valutazione.</span><span class="sxs-lookup"><span data-stu-id="723e2-126">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
8. <span data-ttu-id="723e2-127">Per l'oggetto, digitare **Messaggio di posta elettronica di prova 2**.</span><span class="sxs-lookup"><span data-stu-id="723e2-127">For the subject, type **Test email 2**.</span></span>
    
9. <span data-ttu-id="723e2-128">Nel corpo del messaggio, digitare **Riunione pranzo Tailspin**, quindi fare clic su **Invia**.</span><span class="sxs-lookup"><span data-stu-id="723e2-128">In the body, type **Tailspin lunch meeting**, and then click **Send**.</span></span>
    
10. <span data-ttu-id="723e2-129">Nella scheda **Posta di Outlook**, fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="723e2-129">On the **Outlook Mail** tab, click **New**.</span></span>
    
11. <span data-ttu-id="723e2-130">In **A**, digitare l'indirizzo di posta elettronica dell'account di User6 della sottoscrizione di valutazione.</span><span class="sxs-lookup"><span data-stu-id="723e2-130">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
12. <span data-ttu-id="723e2-131">Per l'oggetto, digitare **Messaggio di posta elettronica di prova 3**.</span><span class="sxs-lookup"><span data-stu-id="723e2-131">For the subject, type **Test email 3**.</span></span>
    
13. <span data-ttu-id="723e2-132">Nel corpo del messaggio, digitare **Divergenze sul contratto Tailspin**, quindi fare clic su **Invia**.</span><span class="sxs-lookup"><span data-stu-id="723e2-132">In the body, type **Tailspin contract disagreement**, and then click **Send**.</span></span>
    
14. <span data-ttu-id="723e2-133">Fare clic sull'icona dell'utente nell'angolo in alto a destra, quindi su **Disconnetti**.</span><span class="sxs-lookup"><span data-stu-id="723e2-133">Click the user icon in the upper right corner, and then click **Sign out**.</span></span>
    
15. <span data-ttu-id="723e2-134">Aprire una nuova scheda e accedere al portale di Office 365 ([https://www.office.com](https://www.office.com)) con il nome e la password dell'account USER6 della sottoscrizione di valutazione.</span><span class="sxs-lookup"><span data-stu-id="723e2-134">Open a new tab and sign in to the Office 365 portal ([https://www.office.com](https://www.office.com)) with the account name and password of the User6 account of your trial subscription.</span></span>
    
16. <span data-ttu-id="723e2-135">Nella scheda **Portale di Office 365**, fare clic su **Posta**.</span><span class="sxs-lookup"><span data-stu-id="723e2-135">On the **Office 365 portal** tab, click **Mail**.</span></span>
    
17. <span data-ttu-id="723e2-136">Nella scheda **mail-USER6-Outlook** verificare che USER6 abbia ricevuto tutti e tre i messaggi dall'account di posta elettronica di Outlook.</span><span class="sxs-lookup"><span data-stu-id="723e2-136">On the **Mail - User6 - Outlook** tab, check that User6 received all three emails from the Outlook email account.</span></span>
    
18. <span data-ttu-id="723e2-137">Tornare alla **scheda del portale di Office 365** per User6.</span><span class="sxs-lookup"><span data-stu-id="723e2-137">Switch back to the **Office 365 portal tab** for User6.</span></span>
    
19. <span data-ttu-id="723e2-138">Fare clic sull'icona dell'utente nell'angolo in alto a destra, quindi su **Disconnetti.**</span><span class="sxs-lookup"><span data-stu-id="723e2-138">Click the user icon in the upper right corner, and then click **Sign out.**</span></span>
    
<span data-ttu-id="723e2-139">In questa procedura, è possibile creare due documenti Word che in seguito verranno analizzati in un caso di Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="723e2-139">In this procedure, you create two Word documents that will you will later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="723e2-140">Nella pagina **Office**, fare click su **Accedi,** effettuare l'accesso con le credenziali dell'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="723e2-140">On the **Office** page, click **Sign in,** sign in with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="723e2-141">in una nuova scheda, accedere all'URL del sito di SharePoint di produzione: **https://** <fictional organization name> **. sharepoint.com/sites/production**</span><span class="sxs-lookup"><span data-stu-id="723e2-141">On a new tab, access the URL of your Production SharePoint site: **https://**<fictional organization name> **.sharepoint.com/sites/production**</span></span>
    
3. <span data-ttu-id="723e2-142">Nella scheda **Raccolta siti di produzione**, in **Documenti**, fare clic su **Nuovo > Documento Word**.</span><span class="sxs-lookup"><span data-stu-id="723e2-142">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
4. <span data-ttu-id="723e2-143">Nella pagina **Word Online**, digitare **Bozza contratto Tailspin**, attendere finché non compare **Salvato** nel titolo, quindi chiudere la scheda della pagina **Word Online**.</span><span class="sxs-lookup"><span data-stu-id="723e2-143">On the **Word Online** page, type **Tailspin draft contract**, wait until it displays **Saved** in the title, and then close the **Word Online** page tab.</span></span>
    
5. <span data-ttu-id="723e2-144">Nella scheda **Raccolta siti di produzione**, in **Documenti**, fare clic su **Nuovo > Documento Word**.</span><span class="sxs-lookup"><span data-stu-id="723e2-144">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
6. <span data-ttu-id="723e2-145">	Nella scheda *\*Word Online*\*, digitare *\*Note su divergenze relative al contratto Tailspin*\*, attendere finché non compare *\*Salvato** nel titolo, quindi chiudere la scheda *\*Word Online*\*.</span><span class="sxs-lookup"><span data-stu-id="723e2-145">On the **Word Online** tab, type **Tailspin contract dispute notes**, wait until it displays **Saved** in the title, and then close the **Word Online** tab.</span></span>
    
7. <span data-ttu-id="723e2-146">Nella scheda **Raccolta siti di produzione**, viene visualizzato **Documento** e **Documento1** nell'elenco dei documenti.</span><span class="sxs-lookup"><span data-stu-id="723e2-146">On the **Production site collection** tab, you should see **Document** and **Document1** in the list of documents.</span></span>
    
8. <span data-ttu-id="723e2-147">Chiudere la scheda **Raccolta siti di produzione**.</span><span class="sxs-lookup"><span data-stu-id="723e2-147">Close the **Production site collection** tab.</span></span>
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a><span data-ttu-id="723e2-148">Fase 3: usare Advanced eDiscovery per una controversia legale</span><span class="sxs-lookup"><span data-stu-id="723e2-148">Phase 3: Use Advanced eDiscovery for a legal dispute</span></span>

<span data-ttu-id="723e2-149">Sfortunatamente, una controversia relativa al contratto tra l'organizzazione e Tailspin Toys è giunta a un'azione legale.</span><span class="sxs-lookup"><span data-stu-id="723e2-149">Unfortunately, a contract dispute between your organization and Tailspin Toys has reached the point of legal action.</span></span> <span data-ttu-id="723e2-150">In questa procedura, si crea e configura un caso avanzato di eDiscovery per cercare e analizzare la posta elettronica e i documenti che contengono il testo "contratto Tilt".</span><span class="sxs-lookup"><span data-stu-id="723e2-150">In this procedure, you create and configure an Advanced eDiscovery case to search for and analyze email and documents that contain the text "Tailspin contract".</span></span>
  
<span data-ttu-id="723e2-151">La procedura per l'uso di Advanced eDiscovery è la seguente:</span><span class="sxs-lookup"><span data-stu-id="723e2-151">The process for using Advanced eDiscovery is the following:</span></span>
  
- <span data-ttu-id="723e2-152">Creare una ricerca nel centro sicurezza &amp; e conformità, analizzarne i risultati e quindi preparare i risultati per Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="723e2-152">Create a search in the Security &amp; Compliance center, analyze its results, and then prepare the results for Advanced eDiscovery.</span></span>
    
- <span data-ttu-id="723e2-153">Creare e configurare un caso di Advanced eDiscovery e analizzare i risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="723e2-153">Create and configure a case in Advanced eDiscovery and analyze the search results.</span></span>
    
<span data-ttu-id="723e2-154">In questa procedura, è possibile creare una ricerca nel centro &amp; sicurezza e conformità per "contratto Tilt", esaminare i risultati e quindi preparare i risultati per Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="723e2-154">In this procedure, you create a search in the Security &amp; Compliance center for "Tailspin contract", look at the results, and then prepare the results for Advanced eDiscovery.</span></span>
  
1. <span data-ttu-id="723e2-155">Dalla scheda **Portale di Office 365**, fare clic su **Admin**.</span><span class="sxs-lookup"><span data-stu-id="723e2-155">From the **Office 365 portal** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="723e2-156">Nella barra di spostamento a sinistra della scheda dell'interfaccia di amministrazione, fare clic su **Interfacce di amministrazione > Conformità**.</span><span class="sxs-lookup"><span data-stu-id="723e2-156">In the left navigation of the Admin center tab, click **Admin centers > Compliance**.</span></span>
    
3. <span data-ttu-id="723e2-157">Nella scheda **conformità &amp; di sicurezza** fare clic su **autorizzazioni**.</span><span class="sxs-lookup"><span data-stu-id="723e2-157">On the **Security &amp; Compliance** tab, click **Permissions**.</span></span>
    
4. <span data-ttu-id="723e2-158">Nell'elenco **Autorizzazioni**, fare doppio click su **Gestione organizzazione**.</span><span class="sxs-lookup"><span data-stu-id="723e2-158">In the **Permissions** list, double-click **Organization Management**.</span></span>
    
5. <span data-ttu-id="723e2-159">Nella finestra **Gruppo di ruoli**, in **Membri** fare clic sul segno più.</span><span class="sxs-lookup"><span data-stu-id="723e2-159">In the **Role Group** window, under **Members**, click the plus sign.</span></span>
    
6. <span data-ttu-id="723e2-160">Nella finestra **Seleziona membri**, fare doppio clic sul nome dell'account di amministratore, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="723e2-160">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
7. <span data-ttu-id="723e2-161">Nella finestra **Gruppo di ruoli**, fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="723e2-161">In the **Role Group** window, click **Save**.</span></span>
    
8. <span data-ttu-id="723e2-162">Nell'elenco **Autorizzazioni**, fare doppio clic su **Responsabile di eDiscovery**.</span><span class="sxs-lookup"><span data-stu-id="723e2-162">In the **Permissions** list, double-click **eDiscovery Manager**.</span></span>
    
9. <span data-ttu-id="723e2-163">Nella finestra **Gruppo di ruoli**, in **Amministratore di eDiscovery**, fare clic sull'icona più.</span><span class="sxs-lookup"><span data-stu-id="723e2-163">In the **Role Group** window, under **eDiscovery Administrator**, click the plus icon.</span></span>
    
10. <span data-ttu-id="723e2-164">Nella finestra **Seleziona membri**, fare doppio clic sul nome dell'account di amministratore, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="723e2-164">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
11. <span data-ttu-id="723e2-165">Nella finestra **Gruppo di ruoli**, fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="723e2-165">In the **Role Group** window, click **Save**.</span></span>
    
12. <span data-ttu-id="723e2-166">Nel riquadro di spostamento a sinistra, fare clic su search \*\* &amp; Investigation > content search\*\*.</span><span class="sxs-lookup"><span data-stu-id="723e2-166">In the left navigation, click **Search &amp; Investigation > Content search**.</span></span>
    
13. <span data-ttu-id="723e2-167">Fare clic sull'icona più per aggiungere una ricerca.</span><span class="sxs-lookup"><span data-stu-id="723e2-167">Click the plus icon to add a search.</span></span>
    
14. <span data-ttu-id="723e2-168">Nella finestra **Nuova ricerca**, digitare **Ricerca contratto Tailspin** in **Nome**.</span><span class="sxs-lookup"><span data-stu-id="723e2-168">In the **New search** window, type **Tailspin contract search** in **Name**.</span></span>
    
15. <span data-ttu-id="723e2-169">In **Dove vuoi effettuare la ricerca?**, fare clic su **Cerca ovunque,** selezionare **Exchange**, **SharePoint** e **Cartelle pubbliche**, quindi fare clic su **Avanti.**</span><span class="sxs-lookup"><span data-stu-id="723e2-169">In **Where do you want us to look?**, click **Search everywhere,** select **Exchange**, **SharePoint**, and **Public Folders**, and then click **Next.**</span></span>
    
16. <span data-ttu-id="723e2-170">In **Cosa vuoi cercare?**, digitare **Contratto Tailspin**, quindi fare clic su **Cerca**.</span><span class="sxs-lookup"><span data-stu-id="723e2-170">In **What do you want us to look for?**, type **Tailspin contract**, and then click **Search**.</span></span>
    
17. <span data-ttu-id="723e2-171">Nell'elenco delle ricerche, fare clic sul nome **Ricerca contratto Tailspin**.</span><span class="sxs-lookup"><span data-stu-id="723e2-171">In the list of searches, click the **Tailspin contract search** name.</span></span>
    
18. <span data-ttu-id="723e2-172">Nel riquadro **Ricerca contratto Tailspin**, fare clic su **Anteprima risultati della ricerca** in **Risultati**.</span><span class="sxs-lookup"><span data-stu-id="723e2-172">In the **Tailspin contract search** pane, click **Preview search results** under **Results**.</span></span> <span data-ttu-id="723e2-173">Verrà visualizzata una finestra in cui sono elencati i due documenti nel sito di SharePoint di produzione ( **documento** e **document1**) e i messaggi di posta elettronica di **test 1** e **test email 3** a USER6.</span><span class="sxs-lookup"><span data-stu-id="723e2-173">You should see a window listing the two documents on the Production SharePoint site ( **Document** and **Document1**) and the **Test email 1** and **Test email 3** emails to User6.</span></span> <span data-ttu-id="723e2-174">Chiudere la finestra.</span><span class="sxs-lookup"><span data-stu-id="723e2-174">Close the window.</span></span>
    
19. <span data-ttu-id="723e2-175">Nel riquadro **Ricerca contenuto**, in **Analizza i risultati con Advanced eDiscovery**, fare clic su **Anteprima risultati per analisi**.</span><span class="sxs-lookup"><span data-stu-id="723e2-175">In the **Content search** pane, under **Analyze results with Advanced eDiscovery**, click **Preview results for analysis**.</span></span>
    
20. <span data-ttu-id="723e2-176">Nella finestra **Prepara i risultati della ricerca per ricerca contratto Tailspin**, fare clic su **Prepara** e attendere il completamento dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="723e2-176">In the **Prepare the search results for Tailspin contract search** window, click **Prepare** and wait for it to complete.</span></span>
    
<span data-ttu-id="723e2-177">In questa procedura, è possibile creare un nuovo caso di Advanced eDiscovery e analizzare i risultati della ricerca relativa al contratto Tailspin.</span><span class="sxs-lookup"><span data-stu-id="723e2-177">In this procedure, you create a new case for Advanced eDiscovery and analyze the Tailspin contract search results.</span></span>
  
1. <span data-ttu-id="723e2-178">Nel riquadro di spostamento a sinistra, fare clic su **eDiscovery** in \*\*analisi ricerca &amp; \*\*.</span><span class="sxs-lookup"><span data-stu-id="723e2-178">In the left navigation, click **eDiscovery** under **Search &amp; Investigation**.</span></span>
    
2. <span data-ttu-id="723e2-179">Nel riquadro **eDiscovery**, fare clic su **Vai ad Advanced eDiscovery**.</span><span class="sxs-lookup"><span data-stu-id="723e2-179">In the **eDiscovery** pane, click **Go to Advanced eDiscovery**.</span></span>
    
3. <span data-ttu-id="723e2-180">Nella scheda **Advanced eDiscovery**, fare clic sull'icona più per aggiungere un nuovo caso.</span><span class="sxs-lookup"><span data-stu-id="723e2-180">In the **Advanced eDiscovery** tab, click the plus icon to add a new case.</span></span>
    
4. <span data-ttu-id="723e2-p106">	Nel riquadro *\*Aggiungi caso*\*, digitare *\*Controversia relativa al contratto Tailspin** in *\*Nome*\*, quindi fare clic su *\*OK*\*. Attendere che il caso venga creato.</span><span class="sxs-lookup"><span data-stu-id="723e2-p106">In the **Add case** pane, type **Tailspin contract dispute** in **Name**, and then click **OK**. Wait for the case to be created.</span></span>
    
5. <span data-ttu-id="723e2-183">Fare doppio clic sul caso **Controversia relativa al contratto Tailspin** nell'elenco. </span><span class="sxs-lookup"><span data-stu-id="723e2-183">Double click the **Tailspin contract dispute** case in the list.</span></span>
    
6. <span data-ttu-id="723e2-184">Nell'elenco **contenitore** fare clic sul contenitore di ricerca per il **contratto Tilt** , quindi fare clic su **elabora**.</span><span class="sxs-lookup"><span data-stu-id="723e2-184">In the **Container** list, click the **Tailspin contract search** container, and then click **Process**.</span></span> <span data-ttu-id="723e2-185">Attendere il completamento dell'elaborazione.</span><span class="sxs-lookup"><span data-stu-id="723e2-185">Wait for the processing to complete.</span></span>
    
7. <span data-ttu-id="723e2-186">Quando nella parte inferiore della finestra viene visualizzato **Elaborazione completata**, fare clic su **Riepilogo elaborazione** nella barra di spostamento a sinistra per visualizzare un riepilogo.</span><span class="sxs-lookup"><span data-stu-id="723e2-186">When **Process: completed** appears at the bottom of the window, click **Process summary** in the left navigation to see a summary.</span></span>
    
8. <span data-ttu-id="723e2-187">Nella barra di spostamento superiore, fare clic su **Analizza**.</span><span class="sxs-lookup"><span data-stu-id="723e2-187">In the top navigation, click **Analyze**.</span></span>
    
9. <span data-ttu-id="723e2-188">Nella pagina **Configurazione**, in **Temi** digitare **3** in **Numero massimo di temi**.</span><span class="sxs-lookup"><span data-stu-id="723e2-188">On the **Setup** page, under **Themes**, type **3** in **Max number of themes**.</span></span>
    
10. <span data-ttu-id="723e2-189">Fare clic su **Analizza** e attendere il completamento dell'analisi.</span><span class="sxs-lookup"><span data-stu-id="723e2-189">Click **Analyze** and wait for the analysis to complete.</span></span> <span data-ttu-id="723e2-190">Viene visualizzata una serie di grafici a torta con l'analisi della popolazione target, dei documenti, dei messaggi di posta elettronica e degli allegati.</span><span class="sxs-lookup"><span data-stu-id="723e2-190">You should see a series of pie charts with analysis of the target population, documents, emails, and attachments.</span></span> <span data-ttu-id="723e2-191">Per ulteriori informazioni, vedere [viewIng Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span><span class="sxs-lookup"><span data-stu-id="723e2-191">For more information, see [Viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span></span>
    
<span data-ttu-id="723e2-192">È ora possibile usare questo ambiente per creare nuovi contenuti, nuove ricerche e casi e sperimentare ulteriormente Advanced eDiscovery in Office 365.</span><span class="sxs-lookup"><span data-stu-id="723e2-192">You can now use this environment to create new content, new searches and cases, and experiment further with Advanced eDiscovery in Office 365.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="723e2-193">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="723e2-193">See Also</span></span>

[<span data-ttu-id="723e2-194">Guida al lab test (TLG) per adozione del cloud</span><span class="sxs-lookup"><span data-stu-id="723e2-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="723e2-195">Ambiente di sviluppo/test della configurazione di base</span><span class="sxs-lookup"><span data-stu-id="723e2-195">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="723e2-196">Ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="723e2-196">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="723e2-197">DirSync per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="723e2-197">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="723e2-198">Cloud App Security per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="723e2-198">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="723e2-199">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="723e2-199">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="723e2-200">Office 365 Advanced eDiscovery</span><span class="sxs-lookup"><span data-stu-id="723e2-200">Office 365 Advanced eDiscovery</span></span>](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


