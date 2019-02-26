---
title: Autenticazione a più fattori per l'ambiente di sviluppo/test di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/20/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: "Riepilogo: Configurare l'autenticazione a più fattori tramite messaggi di testo inviati a uno smartphone in un ambiente di sviluppo e testing di Office 365."
ms.openlocfilehash: 453dbc6bda3cfbc6806159d53c9a805c4c6cac97
ms.sourcegitcommit: 8e2760cbcaf564923595147ccf6da468edaed364
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/25/2019
ms.locfileid: "30242078"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a><span data-ttu-id="2d59f-103">Autenticazione a più fattori per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="2d59f-103">Multi-factor authentication for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="2d59f-104">**Riepilogo:** Configurare l'autenticazione a più fattori tramite messaggi di testo inviati a uno smartphone in un ambiente di sviluppo e testing di Office 365.</span><span class="sxs-lookup"><span data-stu-id="2d59f-104">**Summary:** Configure multi-factor authentication using text messages sent to a smart phone in an Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="2d59f-p101">Per un ulteriore livello di sicurezza per l'accesso all'abbonamento a Office 365, è possibile abilitare l'autenticazione a più fattori di Azure, che richiede più di un semplice nome utente e password per l'autenticazione di un account. Con l'autenticazione a più fattori per Office 365, agli utenti viene richiesto di riconoscere una telefonata, digitare un codice di verifica inviato in un messaggio di testo oppure specificare una password per l'app negli Smart Phone dopo aver inserito correttamente le password. Sono in grado di accedere solo dopo che questo secondo fattore di autenticazione è stato soddisfatto.</span><span class="sxs-lookup"><span data-stu-id="2d59f-p101">For an additional level of security for signing in to your Office 365 subscription, you can enable Azure multi-factor authentication, which requires more than just a username and password to authenticate an account. With multi-factor authentication for Office 365, users are required to acknowledge a phone call, type a verification code sent in a text message, or specify an app password on their smart phones after correctly entering their passwords. They can sign in only after this second authentication factor has been satisfied.</span></span> 
  
<span data-ttu-id="2d59f-108">In questo articolo viene illustrato come abilitare e testare l'autenticazione basata su messaggi di testo per uno specifico account di Office 365.</span><span class="sxs-lookup"><span data-stu-id="2d59f-108">This article describes how to enable and test text message-based authentication for a specific Office 365 account.</span></span>
  
<span data-ttu-id="2d59f-109">Le fasi di configurazione dell’autenticazione a più fattori per Office 365 in un ambiente di sviluppo e testing sono due:</span><span class="sxs-lookup"><span data-stu-id="2d59f-109">There are two phases to setting up multi-factor authentication for Office 365 in a dev/test environment:</span></span>
  
1. <span data-ttu-id="2d59f-110">Creare l'ambiente di sviluppo/testing di Office 365</span><span class="sxs-lookup"><span data-stu-id="2d59f-110">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="2d59f-111">Abilitare e testare l'autenticazione a più fattori per l'account User 2.</span><span class="sxs-lookup"><span data-stu-id="2d59f-111">Enable and test multi-factor authentication for the User 2 account.</span></span>
    
> [!TIP]
> <span data-ttu-id="2d59f-112">Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2d59f-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="2d59f-113">Fase 1: creare l'ambiente di sviluppo/test di Office 365 aziendale leggero o simulato</span><span class="sxs-lookup"><span data-stu-id="2d59f-113">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="2d59f-114">Se si desidera semplicemente testare l'autenticazione a più fattori con i requisiti minimi, seguire le istruzioni riportate nelle fasi 2 e 3 di [Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="2d59f-114">If you just want to test multi-factor authentication in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="2d59f-115">Se si desidera testare l'autenticazione a più fattori in un'azienda simulata, seguire le istruzioni in [DirSync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="2d59f-115">If you want to test multi-factor authentication in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="2d59f-p102">Il test dell’autenticazione a più fattori non richiede l'ambiente di sviluppo/testing aziendale simulato, che include una rete Intranet simulata connessa a Internet e la sincronizzazione directory per una foresta di Windows Server AD. Questo test viene fornito qui come opzione in modo per consentire di testare l’autenticazione a più fattori e sperimentarla in un ambiente che rappresenta un'organizzazione tipica.</span><span class="sxs-lookup"><span data-stu-id="2d59f-p102">Testing multi-factor authentication does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test multi-factor authentication and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a><span data-ttu-id="2d59f-118">Fase 2: Abilitare e testare l'autenticazione a più fattori per l'account User 2</span><span class="sxs-lookup"><span data-stu-id="2d59f-118">Phase 2: Enable and test multi-factor authentication for the User 2 account</span></span>

<span data-ttu-id="2d59f-119">Abilitare l'autenticazione a più fattori per l'account User 2 procedendo nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="2d59f-119">Enable multi-factor authentication for the User 2 account with these steps:</span></span>
  
1. <span data-ttu-id="2d59f-120">Aprire un'istanza separata del browser, accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) e quindi accedere alla sottoscrizione di valutazione di Office 365 con l'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="2d59f-120">Open a separate instance of your browser, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and then sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="2d59f-121">Dalla pagina principale del portale, fare clic su **Admin**.</span><span class="sxs-lookup"><span data-stu-id="2d59f-121">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="2d59f-122">Nel riquadro di spostamento sinistro fare clic su **Utenti > Utenti attivi**.</span><span class="sxs-lookup"><span data-stu-id="2d59f-122">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="2d59f-123">Nel riquadro utenti attivi, fare clic su **altre > configurazione di autenticazione a più fattori**.</span><span class="sxs-lookup"><span data-stu-id="2d59f-123">In the Active users pane, click **More > Multi-factor authentication setup**.</span></span>
    
5. <span data-ttu-id="2d59f-124">Nell'elenco, selezionare l'account **User 2** .</span><span class="sxs-lookup"><span data-stu-id="2d59f-124">In the list, select the **User 2** account.</span></span>
    
6. <span data-ttu-id="2d59f-125">Nella sezione **User 2**, sotto **Azioni rapide**, fare clic su **Abilita**.</span><span class="sxs-lookup"><span data-stu-id="2d59f-125">In the **User 2** section, under **Quick steps**, click **Enable**.</span></span>
    
7. <span data-ttu-id="2d59f-126">Nella finestra di dialogo **Informazioni sull'abilitazione dell'autenticazione più fattori** fare clic su **Abilita Multi-Factor Auth**.</span><span class="sxs-lookup"><span data-stu-id="2d59f-126">In the **About enabling multi-factor auth** dialog box, click **Enable multi-factor auth**.</span></span>
    
8. <span data-ttu-id="2d59f-127">Nella finestra di dialogo **aggiornamenti con esito positivo** fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="2d59f-127">In the **Updates successful** dialog box, click **Close**.</span></span>
    
9. <span data-ttu-id="2d59f-128">Nella scheda **Microsoft Office Home** fare clic sull'icona dell'account utente in alto a destra, quindi fare clic su **Disconnetti**.</span><span class="sxs-lookup"><span data-stu-id="2d59f-128">On the **Microsoft Office Home** tab, click the user account icon in the upper right, and then click **Sign out**.</span></span>
    
10. <span data-ttu-id="2d59f-129">Chiudere l'istanza del browser.</span><span class="sxs-lookup"><span data-stu-id="2d59f-129">Close your browser instance.</span></span>
    
<span data-ttu-id="2d59f-130">Completare la configurazione dell'account User 2 per utilizzare un messaggio di testo per la convalida e testarla con questa procedura:</span><span class="sxs-lookup"><span data-stu-id="2d59f-130">Complete the configuration for the User 2 account to use a text message for validation and test it with these steps:</span></span>
  
1. <span data-ttu-id="2d59f-131">Aprire una nuova istanza del browser.</span><span class="sxs-lookup"><span data-stu-id="2d59f-131">Open a new instance of your browser.</span></span>
    
2. <span data-ttu-id="2d59f-132">Accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) ed eseguire l'accesso con l'account User 2 (User2\<@ Organization name>. onmicrosoft. com) e la password.</span><span class="sxs-lookup"><span data-stu-id="2d59f-132">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in with the User 2 account (user2@\<organization name>.onmicrosoft.com) and password.</span></span>
    
3. <span data-ttu-id="2d59f-p103">Dopo l'accesso, viene chiesto di configurare l'account per un'ulteriore convalida di sicurezza. Fare clic su **Configura ora**.</span><span class="sxs-lookup"><span data-stu-id="2d59f-p103">After signing in, you are prompted to set up the account for additional security validation. Click **Set it up now**.</span></span>
    
4. <span data-ttu-id="2d59f-135">Nella pagina **Verifica aggiuntiva di sicurezza**:</span><span class="sxs-lookup"><span data-stu-id="2d59f-135">On the **Additional security verification** page:</span></span>
    
  - <span data-ttu-id="2d59f-136">Selezionare il paese o l'area geografica.</span><span class="sxs-lookup"><span data-stu-id="2d59f-136">Select your country or region.</span></span>
    
  - <span data-ttu-id="2d59f-137">Digitare il numero di telefono dello smartphone che riceverà i messaggi di testo.</span><span class="sxs-lookup"><span data-stu-id="2d59f-137">Type phone number of the smart phone that will receive text messages.</span></span>
    
  - <span data-ttu-id="2d59f-138">in **Metodo**, fare clic su **Inviami un codice tramite messaggio di testo**.</span><span class="sxs-lookup"><span data-stu-id="2d59f-138">in **Method**, click **Send me a code by text message**.</span></span>
    
5. <span data-ttu-id="2d59f-139">Fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="2d59f-139">Click **Next**.</span></span>
    
6. <span data-ttu-id="2d59f-140">Immettere il codice di verifica del messaggio di testo ricevuto sullo smartphone e quindi fare clic su **Verifica**.</span><span class="sxs-lookup"><span data-stu-id="2d59f-140">Enter the verification code from the text message received on your smart phone, and then click **Verify**.</span></span>
    
7. <span data-ttu-id="2d59f-141">Nella pagina **Passaggio 3: Mantenere le applicazioni esistenti**, annotare la password dell'app visualizzata per l'account User 2 in una posizione sicura e fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="2d59f-141">On the **Step 3: Keep your existing applications** page, record the displayed app password for the User 2 account in a secure location, and then click **Done**.</span></span>
    
8. <span data-ttu-id="2d59f-p104">Se è la prima volta che si accede con l'account User 2, viene richiesto di modificare la password. Digitare la password originale e una nuova password due volte, quindi fare clic su **Aggiornare la password ed eseguire l'accesso**. Annotare nome e password in una posizione sicura.</span><span class="sxs-lookup"><span data-stu-id="2d59f-p104">If this is the first time you signed in with the User 2 account, you are prompted to change the password. Type the original password and a new password twice, and then click **Update password and sign in**. Record the new password in a secure location.</span></span>
    
    <span data-ttu-id="2d59f-145">Verrà visualizzato il portale di Office 365 per l'utente 2 nella scheda **Microsoft Office Home** del browser.</span><span class="sxs-lookup"><span data-stu-id="2d59f-145">You should see the Office 365 portal for User 2 on the **Microsoft Office Home** tab of your browser.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="2d59f-146">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2d59f-146">See Also</span></span>

[<span data-ttu-id="2d59f-147">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="2d59f-147">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="2d59f-148">Ambiente di sviluppo/test della configurazione di base</span><span class="sxs-lookup"><span data-stu-id="2d59f-148">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="2d59f-149">Ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="2d59f-149">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="2d59f-150">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="2d59f-150">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="2d59f-151">Pianificare l'autenticazione a più fattori per le distribuzioni di Office 365</span><span class="sxs-lookup"><span data-stu-id="2d59f-151">Plan for multi-factor authentication for Office 365 Deployments</span></span>](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

