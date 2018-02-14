---
title: Cloud App Security per l'ambiente di sviluppo/test di Office 365
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
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: 'Riepilogo: Configurare ed effettuare una dimostrazione di sicurezza di Office 365 Cloud App nell''ambiente di sviluppo e di testing di Office 365.'
ms.openlocfilehash: ac5f5c25ecb4d97ac1c8fe3b48096ee02da2ec3e
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2018
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a><span data-ttu-id="78eda-103">Cloud App Security per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="78eda-103">Cloud App Security for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="78eda-104">**Riepilogo:** Configurare ed effettuare una dimostrazione di sicurezza di Office 365 Cloud App nell'ambiente di sviluppo e di testing di Office 365.</span><span class="sxs-lookup"><span data-stu-id="78eda-104">**Summary:** Configure and demonstrate Office 365 Cloud App Security in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="78eda-p101">Protezione di Office 365 Cloud App, in precedenza noto come Office 365 Advanced Security Management, consente di creare i criteri che per monitorare e informano l'utente delle attività potenzialmente dannoso nella sottoscrizione a Office 365, in modo da poter analizzare e richiedere possibili azione di risoluzione dei problemi. Per ulteriori informazioni, vedere [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span><span class="sxs-lookup"><span data-stu-id="78eda-p101">Office 365 Cloud App Security, previously known as Office 365 Advanced Security Management, allows you to create policies that monitor for and inform you of suspicious activities in your Office 365 subscription, so that you can investigate and take possible remediation action. For more information, see [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
  
<span data-ttu-id="78eda-107">Con le istruzioni disponibili in questo articolo, è possibile abilitare e testare Cloud App Security nella sottoscrizione di valutazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="78eda-107">With the instructions in this article, you enable and test Cloud App Security in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="78eda-108">Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.</span><span class="sxs-lookup"><span data-stu-id="78eda-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="78eda-109">Fase 1: creare l'ambiente di sviluppo/test di Office 365 aziendale leggero o simulato</span><span class="sxs-lookup"><span data-stu-id="78eda-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="78eda-110">Se si desidera testare Cloud App sicurezza in un modo semplice con i requisiti minimi, seguire le istruzioni in fasi 2 e 3 [dell'ambiente di sviluppo e di testing di Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="78eda-110">If you just want to test Cloud App Security in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="78eda-111">Se si desidera testare Cloud App protezione in un'azienda simulata, seguire le istruzioni in [DirSync per l'ambiente di sviluppo e di testing di Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="78eda-111">If you want to test Cloud App Security in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="78eda-p102">Il test di Cloud App Security non richiede l'ambiente di sviluppo/test aziendale simulato, che include una rete Intranet simulata connessa a Internet e la sincronizzazione della directory per una foresta di Windows Server AD. Qui viene fornito come un'opzione in modo da poter testare Cloud App Security e sperimentarlo in un ambiente che rappresenta un'organizzazione tipica.</span><span class="sxs-lookup"><span data-stu-id="78eda-p102">Testing Cloud App Security does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test Cloud App Security and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a><span data-ttu-id="78eda-114">Fase 2: prima di abilitare Cloud App Security e creare un criterio</span><span class="sxs-lookup"><span data-stu-id="78eda-114">Phase 2: Before enabling Cloud App Security and creating a policy</span></span>

<span data-ttu-id="78eda-115">In questa procedura si dimostrano che prima di abilitare Cloud App sicurezza, la modifica ruolo dell'utente non fornisce alcuna notifica tramite posta elettronica all'amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="78eda-115">In this procedure, you demonstrate that before enabling Cloud App Security, changing a user's role provides no email notification to the global administrator.</span></span>
  
### <a name="test-the-default-notification-behavior-of-office-365"></a><span data-ttu-id="78eda-116">Testare il comportamento di notifica predefinito di Office 365</span><span class="sxs-lookup"><span data-stu-id="78eda-116">Test the default notification behavior of Office 365</span></span>

1. <span data-ttu-id="78eda-117">Accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) e accedere alla sottoscrizione di prova di Office 365 con l'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="78eda-117">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="78eda-118">Se è in uso l'ambiente di sviluppo/test di Office 365 leggero, accedere dal computer locale.</span><span class="sxs-lookup"><span data-stu-id="78eda-118">If you are using the lightweight Office 365 dev/test environment, sign in from your local computer.</span></span>
    
  - <span data-ttu-id="78eda-119">Se si utilizza l'ambiente di sviluppo e di testing di Office 365 enterprise simulato, utilizzare il [portale Azure](https://portal.azure.com) per connettersi alla macchina virtuale CLIENT1 e quindi effettuare l'accesso da CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="78eda-119">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="78eda-120">Dalla pagina principale del portale, fare clic su **Admin**.</span><span class="sxs-lookup"><span data-stu-id="78eda-120">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="78eda-121">Nel riquadro di spostamento sinistro fare clic su **Utenti > Utenti attivi**.</span><span class="sxs-lookup"><span data-stu-id="78eda-121">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="78eda-122">Fare clic sull'account **utente 4** .</span><span class="sxs-lookup"><span data-stu-id="78eda-122">Click the **User 4** account.</span></span>
    
5. <span data-ttu-id="78eda-123">Nella pagina **utente 4** , fare clic su **Modifica** per la riga di **ruoli** .</span><span class="sxs-lookup"><span data-stu-id="78eda-123">On the **User 4** page, click **Edit** for the **Roles** row.</span></span>
    
6. <span data-ttu-id="78eda-p103">Nella pagina **Modifica ruoli utente** fare clic su **amministratore globale**, digitare l' **indirizzo di posta elettronica alternativi** **user4@contoso.com** e quindi fare clic su **Salva**. Fare doppio clic su **Chiudi** .</span><span class="sxs-lookup"><span data-stu-id="78eda-p103">On the **Edit user roles** page, click **Global administrator**, type **user4@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
7. <span data-ttu-id="78eda-126">Selezionare l'icona di avvio di app in alto a sinistra e scegliere **posta elettronica**.</span><span class="sxs-lookup"><span data-stu-id="78eda-126">Select the app launcher icon in the upper-left and choose **Mail**.</span></span>
    
8. <span data-ttu-id="78eda-p104">Attendere 30 minuti. Si noti che non esiste alcun messaggio di posta elettronica in arrivo di notifica della modifica nel ruolo utente 4 come amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="78eda-p104">Wait 30 minutes. Notice that there is no email message in the inbox notifying you of the change in User 4's role as a global administrator.</span></span>
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a><span data-ttu-id="78eda-129">Fase 3: abilitare Cloud App Security e creare un criterio</span><span class="sxs-lookup"><span data-stu-id="78eda-129">Phase 3: Enable Cloud App Security and create a policy</span></span>

<span data-ttu-id="78eda-p105">In questa procedura, viene abilitato Cloud App Security e viene creato un nuovo criterio per inviare messaggi di notifica all'account di amministratore globale per le modifiche dei ruoli degli account utente. Per questa procedura è necessario:</span><span class="sxs-lookup"><span data-stu-id="78eda-p105">In this procedure, you enable Cloud App Security and create a new policy to send email notifications to your global administrator account for changes in user account roles. This procedure requires:</span></span>
  
- <span data-ttu-id="78eda-132">Il nome e la password dell'account di amministratore globale della sottoscrizione di valutazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="78eda-132">The global administrator account name and password of your Office 365 trial subscription.</span></span>
    
- <span data-ttu-id="78eda-133">Il nome e la password dell'account di User 5 della sottoscrizione di valutazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="78eda-133">The name and password of the User 5 account of your Office 365 trial subscription.</span></span>
    
### <a name="enable-and-configure-cloud-app-security"></a><span data-ttu-id="78eda-134">Abilitare e configurare Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="78eda-134">Enable and configure Cloud App Security</span></span>

1. <span data-ttu-id="78eda-135">Accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) e accedere alla sottoscrizione di prova di Office 365 con l'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="78eda-135">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="78eda-136">Fare clic sul **protezione &amp; conformità** affiancate.</span><span class="sxs-lookup"><span data-stu-id="78eda-136">Click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="78eda-137">Nel riquadro di spostamento sinistra fare clic su **avvisi > Gestisci avanzate avvisi**.</span><span class="sxs-lookup"><span data-stu-id="78eda-137">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
4. <span data-ttu-id="78eda-138">Nella pagina **Gestisci avvisi avanzate** fare clic **su Office 365 Cloud App protezione attiva**e quindi fare clic su **Vai alla protezione di Office 365 Cloud App**.</span><span class="sxs-lookup"><span data-stu-id="78eda-138">On the **Manage advanced alerts** page, click **Turn on Office 365 Cloud App Security**, and then click **Go to Office 365 Cloud App Security**.</span></span>
    
5. <span data-ttu-id="78eda-139">Nella scheda nuovo **Dashboard** , fare clic su **controllo > criteri**.</span><span class="sxs-lookup"><span data-stu-id="78eda-139">On the new **Dashboard** tab, click **Control > Policies**.</span></span>
    
6. <span data-ttu-id="78eda-140">Nella pagina **criteri** fare clic su **Crea un criterio**e quindi fare clic su **criteri di attività**.</span><span class="sxs-lookup"><span data-stu-id="78eda-140">On the **Policy** page, click **Create policy**, and then click **Activity policy**.</span></span>
    
7. <span data-ttu-id="78eda-141">In **Nome criterio**digitare **attività amministrative**.</span><span class="sxs-lookup"><span data-stu-id="78eda-141">In **Policy name**, type **Administrative activity**.</span></span>
    
8. <span data-ttu-id="78eda-142">**Gravità criteri**, fare clic su **High**.</span><span class="sxs-lookup"><span data-stu-id="78eda-142">In **Policy severity**, click **High**.</span></span>
    
9. <span data-ttu-id="78eda-143">Nella **categoria**, fare clic su **account privilegiato**.</span><span class="sxs-lookup"><span data-stu-id="78eda-143">In **Category**, click **Privileged accounts**.</span></span>
    
10. <span data-ttu-id="78eda-144">**Creare filtri per i criteri** **delle attività corrispondenti a tutte le condizioni seguenti**, fare clic **sull'attività amministrative**.</span><span class="sxs-lookup"><span data-stu-id="78eda-144">In **Create filters for the policy**, in **Activities matching all of the following**, click **Administrative activity**.</span></span>
    
11. <span data-ttu-id="78eda-p106">Negli **avvisi**, fare clic su **Invia avviso come messaggio di posta elettronica**. Nella casella **a**digitare l'indirizzo di posta elettronica dell'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="78eda-p106">In **Alerts**, click **Send alert as email**. In **To**, type the email address of your global administrator account.</span></span>
    
12. <span data-ttu-id="78eda-147">Nella parte inferiore della pagina, fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="78eda-147">At the bottom of the page, click **Create**.</span></span>
    
## <a name="phase-4-show-cloud-app-security-in-action"></a><span data-ttu-id="78eda-148">Fase 4: Visualizzare Cloud App Security in azione</span><span class="sxs-lookup"><span data-stu-id="78eda-148">Phase 4: Show Cloud App Security in action</span></span>

<span data-ttu-id="78eda-149">In questa procedura, viene mostrato come Cloud App Security crea avvisi e invia notifiche tramite posta elettronica all'account di amministratore globale quando User 4 rende User 5 un amministratore della gestione di utenti e password.</span><span class="sxs-lookup"><span data-stu-id="78eda-149">In this procedure, you demonstrate how Cloud App Security creates alerts and sends email notifications to the global administrator account when User 4 makes User 5 a password and user management administrator.</span></span>
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a><span data-ttu-id="78eda-150">Mostrare la notifica tramite posta elettronica per una modifica di ruoli degli account utente</span><span class="sxs-lookup"><span data-stu-id="78eda-150">Demonstrate email notification for a change in user account roles</span></span>

1. <span data-ttu-id="78eda-151">In alto a destra, fare clic sull'icona utente e quindi fare clic su **Esci**.</span><span class="sxs-lookup"><span data-stu-id="78eda-151">In the upper-right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="78eda-152">Passare al [https://portal.office.com](https://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="78eda-152">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
3. <span data-ttu-id="78eda-153">Nella pagina di accesso di Office 365, fare clic su **utilizza un altro account**.</span><span class="sxs-lookup"><span data-stu-id="78eda-153">On the Office 365 sign in page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="78eda-154">Digitare il nome dell'account utente 4 e la relativa password e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="78eda-154">Type the User 4 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="78eda-155">Se necessario, modificare la password dell'account utente 4 e quindi fare clic su **Aggiorna password ed effettuare l'accesso**.</span><span class="sxs-lookup"><span data-stu-id="78eda-155">If needed, change the User 4 account password, and then click **Update password and sign in**.</span></span>
    
6. <span data-ttu-id="78eda-156">Nella pagina del portale di Office 365, fare clic su **amministratore**.</span><span class="sxs-lookup"><span data-stu-id="78eda-156">On the Office 365 portal page, click **Admin**.</span></span>
    
7. <span data-ttu-id="78eda-157">Se necessario, fare clic su **Annulla** quando viene richiesto di aggiornare le informazioni di contatto di amministrazione.</span><span class="sxs-lookup"><span data-stu-id="78eda-157">If needed, click **cancel** when prompted to update your admin contact info.</span></span>
    
8. <span data-ttu-id="78eda-158">Dalla pagina principale del portale, fare clic su **Admin**.</span><span class="sxs-lookup"><span data-stu-id="78eda-158">From the main portal page, click **Admin**.</span></span>
    
9. <span data-ttu-id="78eda-159">Nel riquadro di spostamento sinistro fare clic su **Utenti > Utenti attivi**.</span><span class="sxs-lookup"><span data-stu-id="78eda-159">In the left navigation, click **Users > Active users**.</span></span>
    
10. <span data-ttu-id="78eda-160">Fare clic sull'account **utente 5** .</span><span class="sxs-lookup"><span data-stu-id="78eda-160">Click the **User 5** account.</span></span>
    
11. <span data-ttu-id="78eda-161">Nella pagina **5 utente** fare clic su **Modifica** per la riga di **ruoli** .</span><span class="sxs-lookup"><span data-stu-id="78eda-161">On the **User 5** page, click **Edit** for the **Roles** row.</span></span>
    
12. <span data-ttu-id="78eda-p107">Nella pagina **Modifica ruoli utente** fare clic su **amministratore personalizzato**, fare clic su **amministratore Gestione utenti**e **amministratore Password** , digitare l' **indirizzo di posta elettronica alternativi** **user5@contoso.com** e quindi fare clic su **Salvare**. Fare doppio clic su **Chiudi** .</span><span class="sxs-lookup"><span data-stu-id="78eda-p107">On the **Edit user roles** page, click **Customized administrator**, click **Password administrator** and **User management administrator**, type **user5@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
13. <span data-ttu-id="78eda-164">Fare clic sull'icona utente in alto a destra e quindi fare clic su **Esci**.</span><span class="sxs-lookup"><span data-stu-id="78eda-164">Click the user icon in the upper-right, and then click **Sign out**.</span></span> 
    
14. <span data-ttu-id="78eda-165">Passare al [https://portal.office.com](https://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="78eda-165">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
15. <span data-ttu-id="78eda-166">Scegliere il nome dell'account amministratore globale nella pagina **Office 365 accedere** .</span><span class="sxs-lookup"><span data-stu-id="78eda-166">On the **Office 365 sign in** page, click your global administrator account name.</span></span>
    
16. <span data-ttu-id="78eda-167">Digitare la password e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="78eda-167">Type the password, and then click **Sign in**.</span></span>
    
17. <span data-ttu-id="78eda-168">Dalla pagina principale del portale, fare clic su **Admin**.</span><span class="sxs-lookup"><span data-stu-id="78eda-168">From the main portal page, click **Admin**.</span></span>
    
18. <span data-ttu-id="78eda-169">Fare clic sul **protezione &amp; conformità** affiancate.</span><span class="sxs-lookup"><span data-stu-id="78eda-169">Click the **Security &amp; Compliance** tile.</span></span>
    
19. <span data-ttu-id="78eda-170">Nel riquadro di spostamento sinistra fare clic su **avvisi > Gestisci avanzate avvisi**.</span><span class="sxs-lookup"><span data-stu-id="78eda-170">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
20. <span data-ttu-id="78eda-171">Nella pagina **Gestisci avvisi avanzate** , fare clic su **Vai alla protezione di Office 365 Cloud App**.</span><span class="sxs-lookup"><span data-stu-id="78eda-171">On the **Manage advanced alerts** page, click **Go to Office 365 Cloud App Security**.</span></span>
    
21. <span data-ttu-id="78eda-172">Nella scheda nuovo **Dashboard** , osservare le due nuovi avvisi per **l'attività di amministrazione**.</span><span class="sxs-lookup"><span data-stu-id="78eda-172">On the new **Dashboard** tab, notice the two new alerts for **Administrative activity**.</span></span>
    
22. <span data-ttu-id="78eda-p108">Nella scheda **Home page di Microsoft Office** , fare clic su **posta elettronica**. Attendere fino a 30 minuti.</span><span class="sxs-lookup"><span data-stu-id="78eda-p108">From the **Microsoft Office Home** tab, click **Mail**. Wait up to 30 minutes.</span></span> 
    
    <span data-ttu-id="78eda-p109">Dovrebbe essere visibile due nuovi messaggi di posta elettronica nella posta in arrivo con il titolo del **Servizio di notifica di Microsoft Azure Active Directory**. Un messaggio indica che l'account utente 5 è stato aggiunto al ruolo **Amministratore Password** e un altro messaggio indica che l'account utente 5 è stato aggiunto al ruolo **Amministratore utenti** (uguale al ruolo di amministratore Gestione utente nel Office 365 Admin center).</span><span class="sxs-lookup"><span data-stu-id="78eda-p109">You should see two new email messages in the inbox with the title **Microsoft Azure AD Notification Service**. One message indicates that the User 5 account was added to the **Password Administrator** role and another message indicates that the User 5 account was added to the **User Administrator** role (equal to the User management administrator role in the Office 365 Admin center).</span></span>
    
<span data-ttu-id="78eda-p110">È ora possibile utilizzare questo ambiente per creare nuovi criteri e sperimentare ulteriormente sicurezza App Cloud di Office 365. Per i collegamenti agli articoli per la configurazione aggiuntivi, vedere [prepararsi per la protezione di Office 365 Cloud App](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) .</span><span class="sxs-lookup"><span data-stu-id="78eda-p110">You can now use this environment to create new policies and further experiment with Office 365 Cloud App Security. See [Get ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) for links to additional configuration articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="78eda-179">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="78eda-179">See Also</span></span>

[<span data-ttu-id="78eda-180">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="78eda-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="78eda-181">Ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="78eda-181">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="78eda-182">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="78eda-182">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="78eda-183">Panoramica della protezione App Cloud in Office 365</span><span class="sxs-lookup"><span data-stu-id="78eda-183">Overview of Cloud App Security in Office 365</span></span>](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


