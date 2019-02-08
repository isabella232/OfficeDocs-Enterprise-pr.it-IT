---
title: Cloud App Security per l'ambiente di sviluppo/test di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/05/2018
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
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: "Sintesi: configurazione e dimostrazione di Office 365 Cloud App Security nell'ambiente di sviluppo/test di Office 365."
ms.openlocfilehash: 2c29e650233348e44bf72adcb8b18580e1de8802
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897059"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a><span data-ttu-id="c930b-103">Cloud App Security per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="c930b-103">Cloud App Security for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="c930b-104">**Sintesi:** configurazione e dimostrazione di Office 365 Cloud App Security nell'ambiente di sviluppo/test di Office 365.</span><span class="sxs-lookup"><span data-stu-id="c930b-104">**Summary:** Configure and demonstrate Office 365 Cloud App Security in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="c930b-p101">Protezione di Office 365 Cloud App, in precedenza noto come Office 365 Advanced Security Management, consente di creare criteri per monitorare e informano l'utente delle attività potenzialmente dannoso nella sottoscrizione a Office 365, in modo da poter analizzare e richiedere possibili correzione dei problemi azione. Per ulteriori informazioni, vedere [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span><span class="sxs-lookup"><span data-stu-id="c930b-p101">Office 365 Cloud App Security, previously known as Office 365 Advanced Security Management, lets you create policies that monitor for and inform you of suspicious activities in your Office 365 subscription, so that you can investigate and take possible remediation action. For more information, see [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
  
<span data-ttu-id="c930b-107">Con le istruzioni disponibili in questo articolo, è possibile abilitare e testare Cloud App Security nella sottoscrizione di valutazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="c930b-107">With the instructions in this article, you enable and test Cloud App Security in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="c930b-108">Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c930b-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="c930b-109">Fase 1: creare l'ambiente di sviluppo/test di Office 365 aziendale leggero o simulato</span><span class="sxs-lookup"><span data-stu-id="c930b-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="c930b-110">Se si desidera testare Cloud App sicurezza in un modo semplice con i requisiti minimi, seguire le istruzioni in fasi 2 e 3 [dell'ambiente di sviluppo e di testing di Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="c930b-110">If you just want to test Cloud App Security in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="c930b-111">Se si desidera testare Cloud App protezione in un'azienda simulata, seguire le istruzioni in [DirSync per l'ambiente di sviluppo e di testing di Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="c930b-111">If you want to test Cloud App Security in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="c930b-p102">Il test di Cloud App Security non richiede l'ambiente di sviluppo/test aziendale simulato, che include una rete Intranet simulata connessa a Internet e la sincronizzazione della directory per una foresta di Windows Server AD. Qui viene fornito come un'opzione in modo da poter testare Cloud App Security e sperimentarlo in un ambiente che rappresenta un'organizzazione tipica.</span><span class="sxs-lookup"><span data-stu-id="c930b-p102">Testing Cloud App Security does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test Cloud App Security and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a><span data-ttu-id="c930b-114">Fase 2: prima di abilitare Cloud App Security e creare un criterio</span><span class="sxs-lookup"><span data-stu-id="c930b-114">Phase 2: Before enabling Cloud App Security and creating a policy</span></span>

<span data-ttu-id="c930b-115">In questa procedura si dimostrano che prima di abilitare Cloud App sicurezza, la modifica ruolo dell'utente non fornisce alcuna notifica tramite posta elettronica all'amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="c930b-115">In this procedure, you demonstrate that before enabling Cloud App Security, changing a user's role provides no email notification to the global administrator.</span></span>
  
### <a name="test-the-default-notification-behavior-of-office-365"></a><span data-ttu-id="c930b-116">Testare il comportamento di notifica predefinito di Office 365</span><span class="sxs-lookup"><span data-stu-id="c930b-116">Test the default notification behavior of Office 365</span></span>

1. <span data-ttu-id="c930b-117">Accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) ed eseguire l'accesso alla sottoscrizione di prova di Office 365 con l'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="c930b-117">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="c930b-118">Se è in uso l'ambiente di sviluppo/test di Office 365 leggero, accedere dal computer locale.</span><span class="sxs-lookup"><span data-stu-id="c930b-118">If you are using the lightweight Office 365 dev/test environment, sign in from your local computer.</span></span>
    
  - <span data-ttu-id="c930b-119">Se si utilizza l'ambiente di sviluppo e di testing di Office 365 enterprise simulato, utilizzare il [portale Azure](https://portal.azure.com) per connettersi alla macchina virtuale CLIENT1 e quindi effettuare l'accesso da CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="c930b-119">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="c930b-120">Dalla pagina principale del portale, fare clic su **Admin**.</span><span class="sxs-lookup"><span data-stu-id="c930b-120">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="c930b-121">Nel riquadro di spostamento sinistro fare clic su **Utenti > Utenti attivi**.</span><span class="sxs-lookup"><span data-stu-id="c930b-121">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="c930b-122">	Fare clic sull'account *\*User 4*\*.</span><span class="sxs-lookup"><span data-stu-id="c930b-122">Click the **User 4** account.</span></span>
    
5. <span data-ttu-id="c930b-123">Nella pagina **User 4**, fare clic su **Modifica** per la riga **Ruoli**.</span><span class="sxs-lookup"><span data-stu-id="c930b-123">On the **User 4** page, click **Edit** for the **Roles** row.</span></span>
    
6. <span data-ttu-id="c930b-p103">Nella pagina **Modifica ruoli utente**, fare clic su **Amministratore globale**, digitare **user4@contoso.com** nell'**indirizzo di posta elettronica alternativo**, quindi fare clic su **Salva**. Fare doppio clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="c930b-p103">On the **Edit user roles** page, click **Global administrator**, type **user4@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
7. <span data-ttu-id="c930b-126">	Selezionare l'icona di avvio delle app in alto a sinistra e scegliere *\*Posta*\*.</span><span class="sxs-lookup"><span data-stu-id="c930b-126">Select the app launcher icon in the upper-left and choose **Mail**.</span></span>
    
8. <span data-ttu-id="c930b-p104">Attendere 30 minuti. Si noti che non esiste alcun messaggio di posta elettronica in arrivo di notifica della modifica nel ruolo utente 4 come amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="c930b-p104">Wait 30 minutes. Notice that there is no email message in the inbox notifying you of the change in User 4's role as a global administrator.</span></span>
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a><span data-ttu-id="c930b-129">Fase 3: abilitare Cloud App Security e creare un criterio</span><span class="sxs-lookup"><span data-stu-id="c930b-129">Phase 3: Enable Cloud App Security and create a policy</span></span>

<span data-ttu-id="c930b-p105">In questa procedura, viene abilitato Cloud App Security e viene creato un nuovo criterio per inviare messaggi di notifica all'account di amministratore globale per le modifiche dei ruoli degli account utente. Per questa procedura è necessario:</span><span class="sxs-lookup"><span data-stu-id="c930b-p105">In this procedure, you enable Cloud App Security and create a new policy to send email notifications to your global administrator account for changes in user account roles. This procedure requires:</span></span>
  
- <span data-ttu-id="c930b-132">Il nome e la password dell'account di amministratore globale della sottoscrizione di valutazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="c930b-132">The global administrator account name and password of your Office 365 trial subscription.</span></span>
    
- <span data-ttu-id="c930b-133">Il nome e la password dell'account di User 5 della sottoscrizione di valutazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="c930b-133">The name and password of the User 5 account of your Office 365 trial subscription.</span></span>
    
### <a name="enable-and-configure-cloud-app-security"></a><span data-ttu-id="c930b-134">Abilitare e configurare Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="c930b-134">Enable and configure Cloud App Security</span></span>

1. <span data-ttu-id="c930b-135">Accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) ed eseguire l'accesso alla sottoscrizione di prova di Office 365 con l'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="c930b-135">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="c930b-p106">Fare clic su tessera di **amministrazione** . Nella scheda di **interfaccia di amministrazione di Office** , fare clic su **Admin Center gt _ sicurezza & conformità**.</span><span class="sxs-lookup"><span data-stu-id="c930b-p106">Click the **Admin** tile. On the **Office Admin center** tab, click **Admin centers > Security & Compliance**.</span></span>
    
3. <span data-ttu-id="c930b-138">Nel riquadro di spostamento a sinistra fare clic su **Avvisi > Gestisci gli avvisi avanzati**.</span><span class="sxs-lookup"><span data-stu-id="c930b-138">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
4. <span data-ttu-id="c930b-139">Nella pagina **Gestisci gli avvisi avanzati**, fare clic su **Attiva Office 365 Cloud App Security**, quindi fare clic su **Vai a Office 365 Cloud App Security**.</span><span class="sxs-lookup"><span data-stu-id="c930b-139">On the **Manage advanced alerts** page, click **Turn on Office 365 Cloud App Security**, and then click **Go to Office 365 Cloud App Security**.</span></span>
    
5. <span data-ttu-id="c930b-140">Nella nuova scheda **Dashboard**, fare clic su **Controllo > Criteri**.</span><span class="sxs-lookup"><span data-stu-id="c930b-140">On the new **Dashboard** tab, click **Control > Policies**.</span></span>
    
6. <span data-ttu-id="c930b-141">Nella pagina **Criterio**, fare clic su **Crea criterio**, quindi fare clic su **Criteri attività**.</span><span class="sxs-lookup"><span data-stu-id="c930b-141">On the **Policy** page, click **Create policy**, and then click **Activity policy**.</span></span>
    
7. <span data-ttu-id="c930b-142">In **Nome criterio**, digitare **Attività amministrativa**.</span><span class="sxs-lookup"><span data-stu-id="c930b-142">In **Policy name**, type **Administrative activity**.</span></span>
    
8. <span data-ttu-id="c930b-143">In **Gravità del criterio**, fare clic su **Elevata**.</span><span class="sxs-lookup"><span data-stu-id="c930b-143">In **Policy severity**, click **High**.</span></span>
    
9. <span data-ttu-id="c930b-144">In **Categoria**, fare clic su **Account con privilegi**.</span><span class="sxs-lookup"><span data-stu-id="c930b-144">In **Category**, click **Privileged accounts**.</span></span>
    
10. <span data-ttu-id="c930b-145">In **Crea filtri per il criterio**, in **Attività corrispondenti a tutti gli elementi seguenti**, fare clic su **Attività amministrativa**.</span><span class="sxs-lookup"><span data-stu-id="c930b-145">In **Create filters for the policy**, in **Activities matching all of the following**, click **Administrative activity**.</span></span>
    
11. <span data-ttu-id="c930b-p107">In **Avvisi**, fare clic su **Invia l'avviso come messaggio di posta elettronica**. In **A**, digitare l'indirizzo di posta elettronica dell'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="c930b-p107">In **Alerts**, click **Send alert as email**. In **To**, type the email address of your global administrator account.</span></span>
    
12. <span data-ttu-id="c930b-148">Nella parte inferiore della pagina fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="c930b-148">At the bottom of the page, click **Create**.</span></span>
    
## <a name="phase-4-show-cloud-app-security-in-action"></a><span data-ttu-id="c930b-149">Fase 4: Visualizzare Cloud App Security in azione</span><span class="sxs-lookup"><span data-stu-id="c930b-149">Phase 4: Show Cloud App Security in action</span></span>

<span data-ttu-id="c930b-150">In questa procedura, viene mostrato come Cloud App Security crea avvisi e invia notifiche tramite posta elettronica all'account di amministratore globale quando User 4 rende User 5 un amministratore della gestione di utenti e password.</span><span class="sxs-lookup"><span data-stu-id="c930b-150">In this procedure, you demonstrate how Cloud App Security creates alerts and sends email notifications to the global administrator account when User 4 makes User 5 a password and user management administrator.</span></span>
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a><span data-ttu-id="c930b-151">Mostrare la notifica tramite posta elettronica per una modifica di ruoli degli account utente</span><span class="sxs-lookup"><span data-stu-id="c930b-151">Demonstrate email notification for a change in user account roles</span></span>

1. <span data-ttu-id="c930b-152">In alto a destra, fare clic sull'icona dell'utente e quindi fare clic su **Disconnetti**.</span><span class="sxs-lookup"><span data-stu-id="c930b-152">In the upper-right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="c930b-153">Passare a [https://portal.office.com](https://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="c930b-153">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
3. <span data-ttu-id="c930b-154">Nella pagina di accesso di Office 365, fare clic su **Usa un altro account**.</span><span class="sxs-lookup"><span data-stu-id="c930b-154">On the Office 365 sign in page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="c930b-155">Digitare il nome dell'account di User 4 e la relativa password, quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="c930b-155">Type the User 4 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="c930b-156">Se necessario, modificare la password dell'account User 4 e fare clic su **Aggiornare la password ed eseguire l'accesso**.</span><span class="sxs-lookup"><span data-stu-id="c930b-156">If needed, change the User 4 account password, and then click **Update password and sign in**.</span></span>
    
6. <span data-ttu-id="c930b-157">Nella pagina del portale di Office 365, fare clic su **Admin**.</span><span class="sxs-lookup"><span data-stu-id="c930b-157">On the Office 365 portal page, click **Admin**.</span></span>
    
7. <span data-ttu-id="c930b-158">Se necessario, fare clic su **Annulla** quando viene richiesto di aggiornare le informazioni di contatto di amministratore.</span><span class="sxs-lookup"><span data-stu-id="c930b-158">If needed, click **cancel** when prompted to update your admin contact info.</span></span>
    
8. <span data-ttu-id="c930b-159">Dalla pagina principale del portale, fare clic su **Admin**.</span><span class="sxs-lookup"><span data-stu-id="c930b-159">From the main portal page, click **Admin**.</span></span>
    
9. <span data-ttu-id="c930b-160">Nel riquadro di spostamento sinistro fare clic su **Utenti > Utenti attivi**.</span><span class="sxs-lookup"><span data-stu-id="c930b-160">In the left navigation, click **Users > Active users**.</span></span>
    
10. <span data-ttu-id="c930b-161">Fare clic sull'account **User 5**.</span><span class="sxs-lookup"><span data-stu-id="c930b-161">Click the **User 5** account.</span></span>
    
11. <span data-ttu-id="c930b-162">Nella pagina **User 5**, fare clic su **Modifica** per la riga **Ruoli**.</span><span class="sxs-lookup"><span data-stu-id="c930b-162">On the **User 5** page, click **Edit** for the **Roles** row.</span></span>
    
12. <span data-ttu-id="c930b-p108">Nella pagina **Modifica ruoli utente**, fare clic su **Amministratore personalizzato**, selezionare **Amministratore password** e **Amministratore Gestione utenti**, digitare **user5@contoso.com** nell'**indirizzo di posta elettronica alternativo**, quindi fare clic su **Salva**. Fare doppio clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="c930b-p108">On the **Edit user roles** page, click **Customized administrator**, click **Password administrator** and **User management administrator**, type **user5@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
13. <span data-ttu-id="c930b-165">Fare clic sull'icona dell'utente in alto a destra, quindi su **Disconnetti**.</span><span class="sxs-lookup"><span data-stu-id="c930b-165">Click the user icon in the upper-right, and then click **Sign out**.</span></span> 
    
14. <span data-ttu-id="c930b-166">Passare a [https://portal.office.com](https://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="c930b-166">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
15. <span data-ttu-id="c930b-167">Nella pagina **Accesso a Office 365**, fare clic sul nome dell'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="c930b-167">On the **Office 365 sign in** page, click your global administrator account name.</span></span>
    
16. <span data-ttu-id="c930b-168">Digitare la password e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="c930b-168">Type the password, and then click **Sign in**.</span></span>
    
17. <span data-ttu-id="c930b-169">Dalla pagina principale del portale, fare clic su **Admin**.</span><span class="sxs-lookup"><span data-stu-id="c930b-169">From the main portal page, click **Admin**.</span></span>
    
18. <span data-ttu-id="c930b-170">Fare clic sul **protezione &amp; conformità** affiancate.</span><span class="sxs-lookup"><span data-stu-id="c930b-170">Click the **Security &amp; Compliance** tile.</span></span>
    
19. <span data-ttu-id="c930b-171">Nel riquadro di spostamento a sinistra fare clic su **Avvisi > Gestisci gli avvisi avanzati**.</span><span class="sxs-lookup"><span data-stu-id="c930b-171">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
20. <span data-ttu-id="c930b-172">Nella pagina **Gestisci gli avvisi avanzati**, fare clic su **Vai a Office 365 Cloud App Security**.</span><span class="sxs-lookup"><span data-stu-id="c930b-172">On the **Manage advanced alerts** page, click **Go to Office 365 Cloud App Security**.</span></span>
    
21. <span data-ttu-id="c930b-173">Nella nuova scheda **Dashboard**, notare i due nuovi avvisi per **Attività amministrativa**.</span><span class="sxs-lookup"><span data-stu-id="c930b-173">On the new **Dashboard** tab, notice the two new alerts for **Administrative activity**.</span></span>
    
22. <span data-ttu-id="c930b-p109">Dalla scheda **Microsoft Office Home**, fare clic su **Posta**. Attendere fino a 30 minuti. </span><span class="sxs-lookup"><span data-stu-id="c930b-p109">From the **Microsoft Office Home** tab, click **Mail**. Wait up to 30 minutes.</span></span> 
    
    <span data-ttu-id="c930b-p110">Dovrebbero essere visualizzati due nuovi messaggi di posta elettronica nella Posta in arrivo con il titolo **Servizio di notifica di Microsoft Azure AD**. Un messaggio indica che l'account di User 5 è stato aggiunto al ruolo **Amministratore password** e l'altro messaggio indica che l'account di User 5 è stato aggiunto al ruolo **Amministratore utenti** (equivalente al ruolo Amministratore Gestione utenti nell'interfaccia di amministrazione di Office 365).</span><span class="sxs-lookup"><span data-stu-id="c930b-p110">You should see two new email messages in the inbox with the title **Microsoft Azure AD Notification Service**. One message indicates that the User 5 account was added to the **Password Administrator** role and another message indicates that the User 5 account was added to the **User Administrator** role (equal to the User management administrator role in the Office 365 Admin center).</span></span>
    
<span data-ttu-id="c930b-p111">È ora possibile utilizzare questo ambiente per creare nuovi criteri e sperimentare ulteriormente sicurezza App Cloud di Office 365. Per i collegamenti agli articoli per la configurazione aggiuntivi, vedere [prepararsi per la protezione di Office 365 Cloud App](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) .</span><span class="sxs-lookup"><span data-stu-id="c930b-p111">You can now use this environment to create new policies and further experiment with Office 365 Cloud App Security. See [Get ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) for links to additional configuration articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c930b-180">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c930b-180">See Also</span></span>

[<span data-ttu-id="c930b-181">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="c930b-181">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="c930b-182">Ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="c930b-182">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="c930b-183">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="c930b-183">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="c930b-184">Panoramica della protezione App Cloud in Office 365</span><span class="sxs-lookup"><span data-stu-id="c930b-184">Overview of Cloud App Security in Office 365</span></span>](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


