---
title: Registrare iOS e dispositivi Android nell'ambiente di sviluppo e di testing Microsoft Enterprise 365
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
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "Riepilogo: Utilizzare questa guida dei laboratori di testing per registrare i dispositivi nell'ambiente di sviluppo e di testing Microsoft 365 e gestirle in modalità remota."
ms.openlocfilehash: 8ad22ed62d8e7cac8aca225af42e389dc05cb2b5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a><span data-ttu-id="097a8-103">Registrare iOS e dispositivi Android nell'ambiente di sviluppo e di testing Microsoft Enterprise 365</span><span class="sxs-lookup"><span data-stu-id="097a8-103">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>

 <span data-ttu-id="097a8-104">**Riepilogo:** Utilizzare questa guida dei laboratori di testing per registrare i dispositivi nell'ambiente di sviluppo e di testing Microsoft 365 e gestirle in modalità remota.</span><span class="sxs-lookup"><span data-stu-id="097a8-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="097a8-p101">Microsoft Enterprise mobilità famiglia di prodotti (EMS) contribuisce a migliorare la produttività utilizzando le applicazioni preferite e dispositivi proteggendo al contempo i dati dell'organizzazione i dipendenti. Per ulteriori informazioni, vedere [Security (EMS) + mobilità aziendale](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="097a8-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="097a8-p102">Se è necessario applicare criteri di sicurezza a livello di dispositivi, è necessario registrare i dispositivi in Microsoft Intune. La registrazione dei dispositivi non consente solo di gestire i dispositivi aziendali, ma anche quelli personali (BYOD) e condivisi, a seconda dei criteri legali dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="097a8-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage corporate-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="097a8-109">Seguendo le istruzioni fornite in questo articolo, sarà possibile registrare e verificare le funzionalità di gestione di dispositivi mobili base iOS e dei dispositivi Android nell'ambiente di sviluppo e di testing Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="097a8-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="097a8-110">Fase 1: Creare l'ambiente di sviluppo e di testing Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="097a8-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="097a8-111">Seguire le istruzioni [nell'ambiente di sviluppo e di testing The Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="097a8-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-customize-the-microsoft-intune-company-portal-app"></a><span data-ttu-id="097a8-112">Fase 2: personalizzare l'app Portale aziendale di Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="097a8-112">Phase 2: Customize the Microsoft Intune Company Portal app</span></span>

<span data-ttu-id="097a8-113">Seguire questa procedura per personalizzare l'app Portale aziendale di Microsoft Intune per l'azienda fittizia:</span><span class="sxs-lookup"><span data-stu-id="097a8-113">Use these steps to customize the Microsoft Intune Company Portal app for your fictional company:</span></span>
  
1. <span data-ttu-id="097a8-114">In una nuova scheda, aprire la console di amministrazione di Microsoft Intune ([https://manage.microsoft.com](https://manage.microsoft.com)).</span><span class="sxs-lookup"><span data-stu-id="097a8-114">On a new tab, open the Microsoft Intune administration console ([https://manage.microsoft.com](https://manage.microsoft.com)).</span></span>
    
2. <span data-ttu-id="097a8-115">Fare clic su **amministratore** nel riquadro di spostamento e quindi fare clic su **Gestione dei dispositivi mobili** nel riquadro **amministrazione** .</span><span class="sxs-lookup"><span data-stu-id="097a8-115">Click **Admin** in the navigation pane, and then click **Mobile Device Management** in the **Administration** pane.</span></span>
    
3. <span data-ttu-id="097a8-p103">Nell'elenco **attività** selezionare **Impostare Mobile Device Management autorità**. Verificare che sia impostata su **Microsoft Intune**.</span><span class="sxs-lookup"><span data-stu-id="097a8-p103">In the **Tasks** list, select **Set Mobile Device Management Authority**. Ensure that it is set to **Microsoft Intune**.</span></span>
    
4. <span data-ttu-id="097a8-118">Nel riquadro **amministrazione** , fare clic su **Portale aziendale**.</span><span class="sxs-lookup"><span data-stu-id="097a8-118">In the **Administration** pane, click **Company Portal**.</span></span>
    
5. <span data-ttu-id="097a8-119">Nel riquadro **Portale della società** , configurare le impostazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="097a8-119">In the **Company Portal** pane, configure the following settings:</span></span>
    
  - <span data-ttu-id="097a8-120">Nome della società: \<il nome della società fittizia ></span><span class="sxs-lookup"><span data-stu-id="097a8-120">Company name: \<your fictional company name></span></span>
    
  - <span data-ttu-id="097a8-121">Nome del contatto reparto IT: **User5**</span><span class="sxs-lookup"><span data-stu-id="097a8-121">IT department contact name: **User5**</span></span>
    
  - <span data-ttu-id="097a8-122">Numero di telefono del reparto IT: **555-1234**</span><span class="sxs-lookup"><span data-stu-id="097a8-122">IT department phone number: **555-1234**</span></span>
    
  - <span data-ttu-id="097a8-123">Indirizzo di posta elettronica reparto IT: **User5 @**\<nome della società fittizia > **. onmicrosoft.com** (l'indirizzo di posta elettronica dell'account User5)</span><span class="sxs-lookup"><span data-stu-id="097a8-123">IT department e-mail address: **User5@**\<fictional organization name> **.onmicrosoft.com** (the email address of the User5 account)</span></span>
    
6. <span data-ttu-id="097a8-124">In **personalizzazione**, selezionare **verde** nel **colore del tema**.</span><span class="sxs-lookup"><span data-stu-id="097a8-124">In **Customization**, select **Green** in **Theme color**.</span></span>
    
7. <span data-ttu-id="097a8-125">Fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="097a8-125">Click **Save**.</span></span>
    
<span data-ttu-id="097a8-126">Successivamente, verrà installata l'app Portale aziendale di Microsoft Intune e verrà registrato un dispositivo iOS o Android; infine, verrà testata la funzionalità di gestione di base dalla console di amministrazione di Microsoft Intune.</span><span class="sxs-lookup"><span data-stu-id="097a8-126">Next, you will install the Microsoft Intune Company Portal app and enroll an iOS or Android device, and then test basic management functionality from the Microsoft Intune administration console.</span></span>
  
## <a name="phase-3-for-ios-devices-only-enroll-and-manage-an-ios-device"></a><span data-ttu-id="097a8-127">Fase 3 (solo per i dispositivi iOS): registrare e gestire un dispositivo iOS</span><span class="sxs-lookup"><span data-stu-id="097a8-127">Phase 3 (for iOS devices only): Enroll and manage an iOS device</span></span>

<span data-ttu-id="097a8-128">Per registrare un dispositivo iOS per la gestione tramite Intune, è necessario quanto segue:</span><span class="sxs-lookup"><span data-stu-id="097a8-128">To enroll an iOS device for management by Intune, you will need the following:</span></span>
  
- <span data-ttu-id="097a8-129">Un dispositivo iOS, ad esempio un Apple iPad o un iPhone.</span><span class="sxs-lookup"><span data-stu-id="097a8-129">An iOS device such as an Apple iPad or iPhone.</span></span>
    
- <span data-ttu-id="097a8-130">Conoscenza del passcode del dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="097a8-130">Knowledge of the iOS device's passcode.</span></span>
    
- <span data-ttu-id="097a8-p104">Un ID di Apple (un nome account e password). Se non già presente, passare al [sito Web di Apple ID](https://appleid.apple.com/#!&amp;page=signin) e fare clic su **Crea il proprio ID Apple**. Creare un ID di Apple corrispondente all'account amministratore globale della sottoscrizione a Office 365. Registrare il nuovo nome di account Apple ID e la password in un luogo sicuro.</span><span class="sxs-lookup"><span data-stu-id="097a8-p104">An Apple ID (an account name and password). If you do not already have one, go to the [Apple ID website](https://appleid.apple.com/#!&amp;page=signin) and click **Create your Apple ID**. Create an Apple ID corresponding to the global administrator account of your Office 365 subscription. Record your new Apple ID account name and password in a secure location.</span></span>
    
<span data-ttu-id="097a8-p105">Per gestire i dispositivi iOS e Mac, Intune richiede un certificato di Apple Push Notification Service (APNs). Dopo aver aggiunto il certificato in Intune, gli utenti possono installare l'app Portale aziendale di Microsoft Intune per registrare i dispositivi oppure l'amministratore può configurare la gestione dei dispositivi iOS aziendali.</span><span class="sxs-lookup"><span data-stu-id="097a8-p105">An Apple Push Notification service (APNs) certificate is required for Intune to manage iOS and Mac devices. Once the certificate is added to Intune, users can install the Microsoft Intune Company Portal app to enroll their devices or the administrator can set up corporate-owned iOS device management.</span></span>
  
<span data-ttu-id="097a8-p106">È necessario un file di richiesta di firma del certificato per richiedere un certificato di relazione di trust dal Portale Apple Push Certificates. Per ottenere un file di richiesta di firma del certificato:</span><span class="sxs-lookup"><span data-stu-id="097a8-p106">You need a certificate signing request file to request a trust relationship certificate from the Apple Push Certificates Portal. To get a certificate signing request file:</span></span>
  
1. <span data-ttu-id="097a8-139">Nella console di amministrazione di Microsoft Intune, fare clic su **amministratore** nel riquadro di spostamento.</span><span class="sxs-lookup"><span data-stu-id="097a8-139">In the Microsoft Intune administration console, click **Admin** in the navigation pane.</span></span>
    
    <span data-ttu-id="097a8-140">Nel riquadro **amministrazione** , aprire **gestione dei dispositivi mobili > iOS e Mac OS X**, quindi fare clic su **Carica un certificato APNs** nelle **attività**.</span><span class="sxs-lookup"><span data-stu-id="097a8-140">In the **Administration** pane, open **Mobile Device Management > iOS and Mac OS X**, and then click **Upload an APNs Certificate** in **Tasks**.</span></span> 
    
2. <span data-ttu-id="097a8-p107">Nel riquadro di **un certificato APNs caricato** , fare clic su **Scarica la richiesta di certificato APNs**. Salvare il file di richiesta (.csr) in locale con il nome **test di sviluppo**di firma del certificato.</span><span class="sxs-lookup"><span data-stu-id="097a8-p107">In the **Upload an APNs Certificate** pane, click **Download the APNs certificate request**. Save the certificate signing request (.csr) file locally with the name **dev-test**.</span></span>
    
<span data-ttu-id="097a8-143">Per ottenere il certificato del servizio APN (Apple Push Notification):</span><span class="sxs-lookup"><span data-stu-id="097a8-143">To get an Apple Push Notification service certificate:</span></span>
  
1. <span data-ttu-id="097a8-144">Aprire una nuova scheda, accedere al [Portale dei certificati Push Apple](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)e accedere con l'ID di Apple.</span><span class="sxs-lookup"><span data-stu-id="097a8-144">Open a new tab, go to the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2), and sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="097a8-145">Nella pagina **Introduzione** fare clic su **Crea un certificato**.</span><span class="sxs-lookup"><span data-stu-id="097a8-145">On the **Get Started** page, click **Create a Certificate**.</span></span>
    
3. <span data-ttu-id="097a8-146">Nella pagina **Condizioni di utilizzo** selezionare **è possibile leggere e accettare i termini e le condizioni**e quindi fare clic su **accetta**.</span><span class="sxs-lookup"><span data-stu-id="097a8-146">On the **Terms of Use** page, select **I have read and agree to these terms and conditions**, and then click **Accept**.</span></span>
    
4. <span data-ttu-id="097a8-p108">Nella pagina **Crea un nuovo certificato Push** fare clic su **Sfoglia** e selezionare il file di **sviluppo test.csr** salvato nella procedura precedente e quindi fare clic su **Carica**. Quando viene richiesto di aprire un file json, salvarlo nella stessa cartella in cui è memorizzato il file test.csr sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="097a8-p108">On the **Create a New Push Certificate** page, click **Browse** and select the **dev-test.csr** file saved in the previous procedure, and then click **Upload**. When prompted to open a json file, save it to the same folder where the dev-test.csr file is stored.</span></span>
    
5. <span data-ttu-id="097a8-149">Aprire il [Portale dei certificati Push Apple](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) in un'altra scheda e per i **certificati per i server di terze parti**, fare clic su **Download**.</span><span class="sxs-lookup"><span data-stu-id="097a8-149">Open the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) in a different tab and for **Certificates for Third-Party Servers**, click **Download**.</span></span>
    
6. <span data-ttu-id="097a8-p109">Quando viene richiesto di aprire un file .pem, salvarlo con il nome **test.pem sviluppatori** nella stessa cartella in cui è memorizzato il file test.csr sviluppatori. Si tratta del certificato APNs.</span><span class="sxs-lookup"><span data-stu-id="097a8-p109">When prompted to open a .pem file, save it with the name **dev-test.pem** to the same folder where the dev-test.csr file is stored. This is your APNs certificate.</span></span>
    
<span data-ttu-id="097a8-152">Per caricare il certificato APNs in Intune:</span><span class="sxs-lookup"><span data-stu-id="097a8-152">To upload the APNs certificate into Intune:</span></span>
  
1. <span data-ttu-id="097a8-153">Nella scheda console Amministrazione Microsoft Intune, nella pagina **caricare un certificato APNs** fare clic su **Carica il certificato APNs**.</span><span class="sxs-lookup"><span data-stu-id="097a8-153">On the Microsoft Intune administration console tab, on the **Upload an APNs Certificate** page, click **Upload the APNs certificate**.</span></span>
    
2. <span data-ttu-id="097a8-154">Fare clic su **Sfoglia** e specificare il file **test.pem sviluppatori** .</span><span class="sxs-lookup"><span data-stu-id="097a8-154">Click **Browse** and specify the **dev-test.pem** file.</span></span>
    
3. <span data-ttu-id="097a8-p110">Fare clic su **Apri**, digitare il nome dell'account ID Apple e quindi fare clic su **Carica**. È consigliabile visualizzato un messaggio **pronto per la registrazione** nella pagina **iOS e il programma di installazione di MaxOS X Mobile Device Management** .</span><span class="sxs-lookup"><span data-stu-id="097a8-p110">Click **Open**, type your Apple ID account name, and then click **Upload**. You should see a **Ready for enrollment** message on the **iOS and MaxOS X Mobile Device Management Setup** page.</span></span>
    
<span data-ttu-id="097a8-157">Con il certificato APNs installato, Intune può registrare e gestire i dispositivi iOS applicando i criteri ai dispositivi mobili registrati.</span><span class="sxs-lookup"><span data-stu-id="097a8-157">With the APNs certificate installed, Intune can now enroll and manage iOS devices by pushing policy to enrolled mobile devices.</span></span>
  
<span data-ttu-id="097a8-158">Per scaricare l'app Portale aziendale di Microsoft Intune e registrare il dispositivo iOS:</span><span class="sxs-lookup"><span data-stu-id="097a8-158">To download the Microsoft Intune Company portal app and enroll the iOS device:</span></span>
  
1. <span data-ttu-id="097a8-159">Dal dispositivo iOS, accedere con l'ID Apple.</span><span class="sxs-lookup"><span data-stu-id="097a8-159">From your iOS device, sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="097a8-160">Aprire l'app **Store Apple** .</span><span class="sxs-lookup"><span data-stu-id="097a8-160">Open the **Apple Store** app.</span></span>
    
3. <span data-ttu-id="097a8-161">Toccare **Microsoft Intune portale della società**, quindi **ottenere**e quindi **installare**digitare **intune** nella casella di ricerca.</span><span class="sxs-lookup"><span data-stu-id="097a8-161">Type **intune** in the search box and tap **Microsoft Intune Company Portal**, then **Get**, and then **Install**.</span></span>
    
4. <span data-ttu-id="097a8-162">Dopo l'installazione, scegliere **Apri**.</span><span class="sxs-lookup"><span data-stu-id="097a8-162">After it installs, tap **Open**.</span></span>
    
5. <span data-ttu-id="097a8-163">Nella schermata **Intune portale della società** , accedere con l'account amministratore globale di Office 365.</span><span class="sxs-lookup"><span data-stu-id="097a8-163">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
6. <span data-ttu-id="097a8-164">Nella schermata di **Installazione di accesso società** , toccare **iniziare**e quindi **Continua** due volte.</span><span class="sxs-lookup"><span data-stu-id="097a8-164">On the **Company Access Setup** screen, tap **Begin**, and then tap **Continue** twice.</span></span>
    
7. <span data-ttu-id="097a8-165">Nella **prossimamente?** dello schermo, quindi scegliere **registrazione**.</span><span class="sxs-lookup"><span data-stu-id="097a8-165">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
8. <span data-ttu-id="097a8-166">Nella **amministratore attiva?** dello schermo, quindi scegliere **Attiva**.</span><span class="sxs-lookup"><span data-stu-id="097a8-166">On the **Activate device administrator?** screen, tap **Activate**.</span></span>
    
9. <span data-ttu-id="097a8-167">Nella schermata di **Gestione dei profili** , scegliere **Installa**.</span><span class="sxs-lookup"><span data-stu-id="097a8-167">On the **Management Profile** screen, tap **Install**.</span></span>
    
10. <span data-ttu-id="097a8-168">**Immettere un Passcode**, digitare il codice del dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="097a8-168">In **Enter Passcode**, type your iOS device passcode.</span></span>
    
11. <span data-ttu-id="097a8-169">Nella schermata **prossimamente** scegliere **registrazione**.</span><span class="sxs-lookup"><span data-stu-id="097a8-169">On the **What comes next** screen, tap **Enroll**.</span></span>
    
12. <span data-ttu-id="097a8-170">In **Installa profilo**, scegliere **Installa**.</span><span class="sxs-lookup"><span data-stu-id="097a8-170">In **Install Profile**, tap **Install**.</span></span>
    
13. <span data-ttu-id="097a8-171">Nella pagina **avviso** scegliere **Installa**.</span><span class="sxs-lookup"><span data-stu-id="097a8-171">On the **Warning** page, tap **Install**.</span></span>
    
14. <span data-ttu-id="097a8-172">In **Gestione remota**scegliere **Trust**.</span><span class="sxs-lookup"><span data-stu-id="097a8-172">In **Remote Management**, tap **Trust**.</span></span>
    
15. <span data-ttu-id="097a8-173">Scegliere **Fine** per completare il processo di registrazione.</span><span class="sxs-lookup"><span data-stu-id="097a8-173">Tap **Done** to complete the enrollment process.</span></span>
    
16. <span data-ttu-id="097a8-174">Quando viene richiesto di **aprire la pagina in "Portal Comp"?**, scegliere **Apri**.</span><span class="sxs-lookup"><span data-stu-id="097a8-174">When prompted to **Open this page in "Comp Portal"?**, tap **Open**.</span></span>
    
17. <span data-ttu-id="097a8-175">Nella schermata di **Installazione di accesso società** , toccare **iniziare**e quindi **Fine**.</span><span class="sxs-lookup"><span data-stu-id="097a8-175">On the **Company Access Setup** screen, tap **Begin**, and then tap **Done**.</span></span>
    
18. <span data-ttu-id="097a8-176">Nella schermata principale dell'app Portale aziendale di Microsoft Intune, viene visualizzato:</span><span class="sxs-lookup"><span data-stu-id="097a8-176">On the main screen of the Microsoft Intune Company Portal app, you should see:</span></span>
    
  - <span data-ttu-id="097a8-177">Un banner verde.</span><span class="sxs-lookup"><span data-stu-id="097a8-177">A green banner.</span></span>
    
  - <span data-ttu-id="097a8-178">Il nome dell'azienda fittizia in alto a sinistra.</span><span class="sxs-lookup"><span data-stu-id="097a8-178">Your fictional company name in the upper left.</span></span>
    
  - <span data-ttu-id="097a8-179">Il nome del dispositivo iOS elencato in **Dispositivi in uso**.</span><span class="sxs-lookup"><span data-stu-id="097a8-179">Your iOS device name listed in **My Devices**.</span></span>
    
  - <span data-ttu-id="097a8-180">Nella sezione **servizio di supporto tecnico** , il **Nome del contatto** del **User5** con il numero di telefono di **555-1234** e un pulsante **contatti tramite posta elettronica** .</span><span class="sxs-lookup"><span data-stu-id="097a8-180">In the **Helpdesk** section, the **Contact Name** of **User5** with the phone number of **555-1234** and a **Contact by email** button.</span></span>
    
<span data-ttu-id="097a8-p111">Microsoft Intune fornisce sia la funzionalità di blocco remoto sia quella di reimpostazione del passcode. Se un utente perde il proprio dispositivo, è possibile bloccare il dispositivo in modalità remota. Se un utente dimentica il proprio passcode, è possibile rimuovere il passcode in modalità remota.</span><span class="sxs-lookup"><span data-stu-id="097a8-p111">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="097a8-184">Per bloccare un dispositivo iOS in remoto:</span><span class="sxs-lookup"><span data-stu-id="097a8-184">To lock an iOS device remotely:</span></span>
  
1. <span data-ttu-id="097a8-185">Dal computer di amministrazione, scegliere la scheda console di amministrazione di Microsoft Intune del browser, fare clic su **gruppi** nel riquadro di spostamento sinistro.</span><span class="sxs-lookup"><span data-stu-id="097a8-185">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="097a8-186">Nel riquadro **gruppi** aprire **tutti i dispositivi > dispositivi mobili tutti > tutti i dispositivi gestiti diretto**.</span><span class="sxs-lookup"><span data-stu-id="097a8-186">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="097a8-187">Nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic sulla scheda **dispositivi** .</span><span class="sxs-lookup"><span data-stu-id="097a8-187">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="097a8-188">Nell'elenco dei dispositivi, fare clic sul dispositivo iOS. </span><span class="sxs-lookup"><span data-stu-id="097a8-188">In the devices list, click your iOS device.</span></span> 
    
5. <span data-ttu-id="097a8-189">Dal dispositivo iOS, verificare che sia nella schermata principale. </span><span class="sxs-lookup"><span data-stu-id="097a8-189">From your iOS device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="097a8-p112">Dal computer di amministrazione, sulla barra delle applicazioni, fare clic su **remoto attività > blocco remoto**. Guardare il dispositivo iOS quando attivata la sullo schermo del blocco.</span><span class="sxs-lookup"><span data-stu-id="097a8-p112">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="097a8-192">Per rimuovere il passcode:</span><span class="sxs-lookup"><span data-stu-id="097a8-192">To remove the passcode:</span></span>
  
1. <span data-ttu-id="097a8-193">Dal computer di amministrazione, nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic sulla scheda **dispositivi** .</span><span class="sxs-lookup"><span data-stu-id="097a8-193">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="097a8-p113">Nell'elenco fare clic su dispositivo iOS. Nella barra delle applicazioni fare clic su **remoto attività > Passcode Reset**. Attendere un minuto.</span><span class="sxs-lookup"><span data-stu-id="097a8-p113">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="097a8-p114">Dal dispositivo iOS sbloccarlo e si noti che non è più un passcode. Per modificare nuovamente il passcode, passare a **Impostazioni**, quindi **Passcode**.</span><span class="sxs-lookup"><span data-stu-id="097a8-p114">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
## <a name="phase-3-for-android-devices-only-enroll-and-manage-an-android-device"></a><span data-ttu-id="097a8-199">Fase 3 (solo per i dispositivi Android): registrare e gestire un dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="097a8-199">Phase 3 (for Android devices only): Enroll and manage an Android device</span></span>

<span data-ttu-id="097a8-200">Per registrare un dispositivo Android per la gestione tramite Intune, è necessario quanto segue:</span><span class="sxs-lookup"><span data-stu-id="097a8-200">You will need the following to enroll an Android device for management by Intune:</span></span>
  
- <span data-ttu-id="097a8-201">Un dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="097a8-201">An Android device.</span></span>
    
- <span data-ttu-id="097a8-202">Conoscenza del passcode del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="097a8-202">Knowledge of the device's passcode.</span></span>
    
<span data-ttu-id="097a8-203">Per scaricare l'app Portale aziendale di Intune e registrare il dispositivo Android:</span><span class="sxs-lookup"><span data-stu-id="097a8-203">To download the Intune Company portal app and enroll the Android device:</span></span>
  
1. <span data-ttu-id="097a8-204">Da un dispositivo Android, passare all' **Archivio per la riproduzione di Google**e quindi **Iniziare a**.</span><span class="sxs-lookup"><span data-stu-id="097a8-204">From your Android device, go to the **Google Play Store**, and then tap **Get Started**.</span></span>
    
2. <span data-ttu-id="097a8-205">Digitare **intune** nella casella di ricerca e quindi scegliere **portale della società intune** nei risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="097a8-205">Type **intune** in the search box, and then tap **intune company portal** in the search results.</span></span>
    
3. <span data-ttu-id="097a8-206">Scegliere l'elemento **Intune portale della società** , quindi **installare**.</span><span class="sxs-lookup"><span data-stu-id="097a8-206">Tap the **Intune Company Portal** item, and then tap **Install**.</span></span>
    
4. <span data-ttu-id="097a8-207">Sullo schermo **per completare l'installazione account** scegliere **Continua**ed **elementi da ignorare**.</span><span class="sxs-lookup"><span data-stu-id="097a8-207">On the **For Complete account setup** screen, tap **Continue**, and then **Skip**.</span></span>
    
5. <span data-ttu-id="097a8-p115">Nel **Portale della società Intune**, scegliere **accetta**. Installa app.</span><span class="sxs-lookup"><span data-stu-id="097a8-p115">In **Intune Company Portal**, tap **Accept**. The app installs.</span></span>
    
6. <span data-ttu-id="097a8-210">Scegliere **Apri**, quindi **effettuare l'accesso**.</span><span class="sxs-lookup"><span data-stu-id="097a8-210">Tap **Open**, and then tap **Sign in**.</span></span>
    
7. <span data-ttu-id="097a8-211">Nella schermata **Intune portale della società** , accedere con l'account amministratore globale di Office 365.</span><span class="sxs-lookup"><span data-stu-id="097a8-211">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="097a8-212">Nella schermata di **Installazione di accesso società** , toccare due volte **avviare**e quindi **Continua** .</span><span class="sxs-lookup"><span data-stu-id="097a8-212">On the **Company Access Setup** screen, tap **Begin**, and then **Continue** twice.</span></span>
    
9. <span data-ttu-id="097a8-213">Nella **prossimamente?** dello schermo, quindi scegliere **registrazione**.</span><span class="sxs-lookup"><span data-stu-id="097a8-213">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
10. <span data-ttu-id="097a8-214">Nella **amministratore attiva?** dello schermo, quindi scegliere **Activate.**</span><span class="sxs-lookup"><span data-stu-id="097a8-214">On the **Activate device administrator?** screen, tap **Activate.**</span></span>
    
11. <span data-ttu-id="097a8-p116">Nella schermata di **Criteri di Privacy** , selezionare **sono stati esaminati** e quindi toccare **Conferma**. Attendere il processo di registrazione per il completamento.</span><span class="sxs-lookup"><span data-stu-id="097a8-p116">On the **Privacy Policy** screen, select **I acknowledge** and then tap **Confirm**. Wait for the enrollment process to complete.</span></span>
    
12. <span data-ttu-id="097a8-217">Nella schermata di **Installazione di accesso società** , scegliere **Continua**e quindi scegliere **Fine**.</span><span class="sxs-lookup"><span data-stu-id="097a8-217">In the **Company Access Setup** screen, tap **Continue**, and then tap **Done**.</span></span>
    
13. <span data-ttu-id="097a8-218">Nella schermata principale dell'app Portale aziendale di Microsoft Intune, verrà visualizzato un banner verde e il nome dell'azienda fittizia in alto a sinistra.</span><span class="sxs-lookup"><span data-stu-id="097a8-218">On the main screen of the Microsoft Intune Company Portal app, you should see a green banner and your fictional company name in the upper left.</span></span>
    
14. <span data-ttu-id="097a8-p117">Scegliere **i dispositivi**. Verrà visualizzato il nome del dispositivo Android nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="097a8-p117">Tap **My devices**. You should see your Android device name in the list.</span></span>
    
15. <span data-ttu-id="097a8-p118">Scegliere **contatto IT**. Verrà visualizzato il numero di telefono di **555-1234**, un pulsante **contatti tramite posta elettronica** e IT di contatto di **User5**.</span><span class="sxs-lookup"><span data-stu-id="097a8-p118">Tap **Contact IT**. You should see the phone number of **555-1234**, a **Contact by email** button, and the IT contact of **User5**.</span></span>
    
<span data-ttu-id="097a8-p119">Microsoft Intune fornisce sia la funzionalità di blocco remoto sia quella di reimpostazione del passcode. Se un utente perde il proprio dispositivo, è possibile bloccare il dispositivo in modalità remota. Se un utente dimentica il proprio passcode, è possibile reimpostare il passcode in modalità remota.</span><span class="sxs-lookup"><span data-stu-id="097a8-p119">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset the passcode remotely.</span></span>
  
<span data-ttu-id="097a8-226">Per bloccare un dispositivo Android in remoto:</span><span class="sxs-lookup"><span data-stu-id="097a8-226">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="097a8-227">Dal computer di amministrazione, scegliere la scheda console di amministrazione di Microsoft Intune del browser, fare clic su **gruppi** nel riquadro di spostamento sinistro.</span><span class="sxs-lookup"><span data-stu-id="097a8-227">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="097a8-228">Nel riquadro **gruppi** aprire **tutti i dispositivi > dispositivi mobili tutti > tutti i dispositivi gestiti diretto**.</span><span class="sxs-lookup"><span data-stu-id="097a8-228">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="097a8-229">Nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic sulla scheda **dispositivi** .</span><span class="sxs-lookup"><span data-stu-id="097a8-229">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="097a8-230">Nell'elenco dei dispositivi, fare clic sul dispositivo Android. </span><span class="sxs-lookup"><span data-stu-id="097a8-230">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="097a8-231">Dal dispositivo Android, verificare che sia nella schermata principale. </span><span class="sxs-lookup"><span data-stu-id="097a8-231">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="097a8-p120">Dal computer di amministrazione, sulla barra delle applicazioni, fare clic su **remoto attività > blocco remoto**. Quando richiesto, fare clic su **Sì**.</span><span class="sxs-lookup"><span data-stu-id="097a8-p120">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="097a8-234">Verificare che il dispositivo Android passi alla schermata di blocco.</span><span class="sxs-lookup"><span data-stu-id="097a8-234">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="097a8-235">Quando si reimposta il passcode per i dispositivi Android, il portale di amministrazione Intune genera e consente di configurare un passcode complessa.</span><span class="sxs-lookup"><span data-stu-id="097a8-235">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="097a8-236">Per reimpostare il passcode in remoto:</span><span class="sxs-lookup"><span data-stu-id="097a8-236">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="097a8-237">Dal computer di amministrazione, nella scheda console Amministrazione Microsoft Intune del browser, nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic su dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="097a8-237">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="097a8-238">Nella barra delle applicazioni fare clic su **remoto attività > Passcode Reset**.</span><span class="sxs-lookup"><span data-stu-id="097a8-238">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="097a8-p121">Nella **attività remota: Passcode Reset** prompt, fare clic su **Sì**. Attendere un minuto.</span><span class="sxs-lookup"><span data-stu-id="097a8-p121">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="097a8-241">Nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic su **Visualizza proprietà**.</span><span class="sxs-lookup"><span data-stu-id="097a8-241">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="097a8-242">In **Passcode Reset**, si noti il nuovo codice.</span><span class="sxs-lookup"><span data-stu-id="097a8-242">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="097a8-243">Dal dispositivo Android, immettere il nuovo passcode nella schermata di blocco. </span><span class="sxs-lookup"><span data-stu-id="097a8-243">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="097a8-244">Per modificare nuovamente il passcode, passare a **Impostazioni**, scegliere **dispositivo**, scegliere **schermo Blocca**, immettere nuovamente il nuovo passcode, scegliere **blocco dello schermo**e la scelta per il passcode.</span><span class="sxs-lookup"><span data-stu-id="097a8-244">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    
> [!TIP]
> <span data-ttu-id="097a8-245">Fare clic [qui](http://aka.ms/catlgstack) per una rappresentazione grafica a tutti gli articoli nello stack di uno Microsoft Cloud Test Lab Guide.</span><span class="sxs-lookup"><span data-stu-id="097a8-245">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="097a8-246">See Also</span><span class="sxs-lookup"><span data-stu-id="097a8-246">See Also</span></span>

[<span data-ttu-id="097a8-247">L'ambiente di sviluppo e di testing Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="097a8-247">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="097a8-248">Criteri MAM per l'ambiente di sviluppo e di testing Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="097a8-248">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="097a8-249">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="097a8-249">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="097a8-250">Sicurezza (EMS) + mobilità aziendale</span><span class="sxs-lookup"><span data-stu-id="097a8-250">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


