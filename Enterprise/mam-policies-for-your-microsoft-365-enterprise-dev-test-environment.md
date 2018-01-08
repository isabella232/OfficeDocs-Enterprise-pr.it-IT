---
title: Criteri MAM per l'ambiente di sviluppo e di testing Microsoft 365 Enterprise
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
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: 'Riepilogo: Utilizzare questa guida dei laboratori di testing per aggiungere criteri di gestione (MAM) mobili applicazione EMS all''ambiente di sviluppo e di testing Microsoft 365.'
ms.openlocfilehash: d088970dca1ec55212642f16d0519e89bd9591e5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="51145-103">Criteri MAM per l'ambiente di sviluppo e di testing Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="51145-103">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="51145-104">**Riepilogo:** Utilizzare questa guida dei laboratori di testing per aggiungere criteri di gestione (MAM) mobili applicazione EMS all'ambiente di sviluppo e di testing Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="51145-104">**Summary:** Use this Test Lab Guide to add EMS mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
<span data-ttu-id="51145-p101">La mobilità aziendale Microsoft + sicurezza (EMS) contribuisce a migliorare la produttività utilizzando le applicazioni preferite e dispositivi proteggendo al contempo i dati dell'organizzazione i dipendenti. Per ulteriori informazioni, vedere [Security (EMS) + mobilità aziendale](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="51145-p101">The Microsoft Enterprise Mobility + Security (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="51145-107">Con le istruzioni riportate in questo articolo, è aggiungere criteri di gestione (MAM) applicazione per dispositivi mobili per l'ambiente di sviluppo e di testing Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="51145-107">With the instructions in this article, you add mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a><span data-ttu-id="51145-108">Fase 1: Preparare l'ambiente di sviluppo e di testing Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="51145-108">Phase 1: Build out your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="51145-109">Seguire le istruzioni [nell'ambiente di sviluppo e di testing The Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="51145-109">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a><span data-ttu-id="51145-110">Fase 2: creare e distribuire criteri MAM per i dispositivi iOS e Android</span><span class="sxs-lookup"><span data-stu-id="51145-110">Phase 2: Create and deploy MAM policies for iOS and Android devices</span></span>

<span data-ttu-id="51145-111">In questa fase, è possibile creare e distribuire due diversi criteri MAM: uno per i dispositivi iOS e uno per i dispositivi Android.</span><span class="sxs-lookup"><span data-stu-id="51145-111">In this phase, you create and deploy two different MAM policies: one for iOS devices and one for Android devices.</span></span>
  
1. <span data-ttu-id="51145-112">Accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) e accedere alla sottoscrizione di prova di Office 365 con l'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="51145-112">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="51145-113">In una nuova scheda del browser, aprire il portale di Azure ([https://azure.portal.com](https://azure.portal.com)) e accedere utilizzando l'account amministratore globale di Office 365.</span><span class="sxs-lookup"><span data-stu-id="51145-113">On a new tab of your browser, open the Azure portal ([https://azure.portal.com](https://azure.portal.com)) and sign in using your Office 365 global administrator account.</span></span>
    
3. <span data-ttu-id="51145-114">Nella scheda Azure portale in Internet Explorer, nel riquadro di spostamento fare clic su **altri servizi** (o freccia destra), digitare **Intune**e quindi fare clic su **Intune**.</span><span class="sxs-lookup"><span data-stu-id="51145-114">On the Azure portal tab in Internet Explorer, in the navigation pane, click **More services** (or the right arrow), type **Intune**, and then click **Intune**.</span></span>
    
4. <span data-ttu-id="51145-115">Nel riquadro di spostamento a sinistra fare clic su **Gruppi**.</span><span class="sxs-lookup"><span data-stu-id="51145-115">In the left navigation pane, click **Groups**.</span></span>
    
5. <span data-ttu-id="51145-116">Su blade **utenti e gruppi di tutti i gruppi** , fare clic su **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="51145-116">On the **Users and groups-All groups** blade, click **Add**.</span></span>
    
6. <span data-ttu-id="51145-117">Su blade **gruppo** , digitare **gestiti gli utenti di dispositivi iOS** nella casella **nome**, selezionare **assegnato** nel **tipo di appartenenza**, selezionare **Sì** per **caratteristiche di attivare Office?**, quindi fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="51145-117">On the **Group** blade, type **Managed iOS device users** in **Name**, select **Assigned** in **Membership type**, select **Yes** for **Enable Office features?**, and then click **Create**.</span></span> 
    
7. <span data-ttu-id="51145-118">Chiudere e il **gruppo** .</span><span class="sxs-lookup"><span data-stu-id="51145-118">Close the **Group** blade.</span></span>
    
8. <span data-ttu-id="51145-119">Su blade **utenti e gruppi di tutti i gruppi** , fare clic su **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="51145-119">On the **Users and groups-All groups** blade, click **Add**.</span></span>
    
9. <span data-ttu-id="51145-120">Su blade **gruppo** , digitare **gli utenti di dispositivi Android gestiti** in **nome**, selezionare **assegnato** nel **tipo di appartenenza**, selezionare **Sì** per **caratteristiche di attivare Office?**, quindi fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="51145-120">On the **Group** blade, type **Managed Android device users** in **Name**, select **Assigned** in **Membership type**, select **Yes** for **Enable Office features?**, and then click **Create**.</span></span>
    
10. <span data-ttu-id="51145-121">Chiudere blade **utenti e gruppi di tutti i gruppi** .</span><span class="sxs-lookup"><span data-stu-id="51145-121">Close the **Users and groups-All groups** blade.</span></span>
    
11. <span data-ttu-id="51145-122">Su blade **Intune** , nell'elenco **attività veloce** , fare clic su **Crea un criterio di conformità**.</span><span class="sxs-lookup"><span data-stu-id="51145-122">On the **Intune** blade, in the **Quick tasks** list, click **Create a compliance policy**.</span></span>
    
12. <span data-ttu-id="51145-123">Su blade **Profili dei criteri di conformità** , fare clic su **Crea criterio**.</span><span class="sxs-lookup"><span data-stu-id="51145-123">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
13. <span data-ttu-id="51145-p102">In **nome**blade **Creare criteri** , digitare **iOS**. Nella **piattaforma**, selezionare **iOS**, fare clic su blade **dei criteri di conformità iOS** **OK** e quindi fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="51145-p102">On the **Create Policy** blade, in **Name**, type **iOS**. In **Platform**, select **iOS**, click **OK** on the **iOS compliance policy** blade, and then click **Create**.</span></span>
    
14. <span data-ttu-id="51145-126">Su blade **Profili dei criteri di conformità** , fare clic su **Crea criterio**.</span><span class="sxs-lookup"><span data-stu-id="51145-126">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
15. <span data-ttu-id="51145-p103">In **nome**blade **Creare criteri** , digitare **Android**. Nella **piattaforma**, selezionare **Android**, fare clic su blade **criteri di conformità Android** **OK** e quindi fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="51145-p103">On the **Create Policy** blade, in **Name**, type **Android**. In **Platform**, select **Android**, click **OK** on the **Android compliance policy** blade, and then click **Create**.</span></span>
    
16. <span data-ttu-id="51145-129">Scegliere il nome del criterio **Android** blade **Profili dei criteri di conformità** .</span><span class="sxs-lookup"><span data-stu-id="51145-129">On the **Compliance Policy Profiles** blade, click the **Android** policy name.</span></span>
    
17. <span data-ttu-id="51145-130">Nel riquadro di spostamento sinistro della stessa e **Android - proprietà** , fare clic su **assegnazioni**e quindi fare clic su **Seleziona gruppi**.</span><span class="sxs-lookup"><span data-stu-id="51145-130">In the left navigation of the **Android - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
18. <span data-ttu-id="51145-131">Su blade **Selezionare gruppi** fare clic sul gruppo di **utenti di dispositivi Android gestiti** e quindi fare clic su **Seleziona**.</span><span class="sxs-lookup"><span data-stu-id="51145-131">On the **Select groups** blade, click the **Managed Android device users** group, and then click **Select**.</span></span>
    
19. <span data-ttu-id="51145-132">Fare clic su **Salva**e quindi chiudere blade **Android - assegnazioni** .</span><span class="sxs-lookup"><span data-stu-id="51145-132">Click **Save**, and then close the **Android - Assignments** blade.</span></span>
    
20. <span data-ttu-id="51145-133">Scegliere il nome del criterio **iOS** blade **Profili dei criteri di conformità** .</span><span class="sxs-lookup"><span data-stu-id="51145-133">On the **Compliance Policy Profiles** blade, click the **iOS** policy name.</span></span>
    
21. <span data-ttu-id="51145-134">Nel riquadro di spostamento sinistra di blade **iOS - proprietà** , fare clic su **assegnazioni**e quindi fare clic su **Seleziona gruppi**.</span><span class="sxs-lookup"><span data-stu-id="51145-134">In the left navigation of the **iOS - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
22. <span data-ttu-id="51145-135">Su blade **Selezionare gruppi** fare clic sul gruppo di **utenti di dispositivi iOS gestite** e quindi fare clic su **Seleziona**.</span><span class="sxs-lookup"><span data-stu-id="51145-135">On the **Select groups** blade, click the **Managed iOS device users** group, and then click **Select**.</span></span>
    
23. <span data-ttu-id="51145-136">Fare clic su **Salva**e quindi chiudere blade **iOS - assegnazioni** .</span><span class="sxs-lookup"><span data-stu-id="51145-136">Click **Save**, and then close the **iOS - Assignments** blade.</span></span>
    
24. <span data-ttu-id="51145-137">Chiudere blade **Profili dei criteri di conformità** .</span><span class="sxs-lookup"><span data-stu-id="51145-137">Close the **Compliance Policy Profiles** blade.</span></span>
    
25. <span data-ttu-id="51145-138">Su blade **Intune** , fare clic su **Gestione applicazioni** nel riquadro di spostamento sinistro.</span><span class="sxs-lookup"><span data-stu-id="51145-138">On the **Intune** blade, click **Manage apps** in the left navigation.</span></span>
    
26. <span data-ttu-id="51145-139">Su blade **App Mobile** , fare clic su **App**.</span><span class="sxs-lookup"><span data-stu-id="51145-139">On the **Mobile Apps** blade, click **Apps**.</span></span>
    
27. <span data-ttu-id="51145-140">Nell'elenco delle App, fare clic su **PowerPoint**</span><span class="sxs-lookup"><span data-stu-id="51145-140">In the list of apps, click **PowerPoint**,</span></span> 
    
28. <span data-ttu-id="51145-p104">Su blade **Panoramica di PowerPoint** , fare clic su **assegnazioni > Seleziona gruppi > gestiti dispositivi iOS > selezionare**. In **tipo**selezionare **disponibile**e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="51145-p104">On the **PowerPoint Overview** blade, click **Assignments > Select groups > Managed iOS devices > Select**. In **Type**, select **Available**, and then click **Save**.</span></span>
    
29. <span data-ttu-id="51145-143">Ripetere il passaggio 28 per le app seguenti:</span><span class="sxs-lookup"><span data-stu-id="51145-143">Repeat step 28 for the following apps:</span></span>
    
  - <span data-ttu-id="51145-144">Outlook per Android</span><span class="sxs-lookup"><span data-stu-id="51145-144">Outlook for Android</span></span>
    
  - <span data-ttu-id="51145-145">Word per iOS</span><span class="sxs-lookup"><span data-stu-id="51145-145">Word for iOS</span></span>
    
  - <span data-ttu-id="51145-146">Excel per iOS</span><span class="sxs-lookup"><span data-stu-id="51145-146">Excel for iOS</span></span>
    
  - <span data-ttu-id="51145-147">Outlook per iOS</span><span class="sxs-lookup"><span data-stu-id="51145-147">Outlook for iOS</span></span>
    
  - <span data-ttu-id="51145-148">Microsoft Dynamics CRM su iPad per iOS</span><span class="sxs-lookup"><span data-stu-id="51145-148">Microsoft Dynamics CRM on iPad for iOS</span></span>
    
  - <span data-ttu-id="51145-149">Microsoft Dynamics CRM su iPhone per iOS</span><span class="sxs-lookup"><span data-stu-id="51145-149">Microsoft Dynamics CRM on iPhone for iOS</span></span>
    
  - <span data-ttu-id="51145-150">Dynamics CRM per telefoni per Android</span><span class="sxs-lookup"><span data-stu-id="51145-150">Dynamics CRM for Phones for Android</span></span>
    
  - <span data-ttu-id="51145-151">Dynamics CRM per tablet per Android</span><span class="sxs-lookup"><span data-stu-id="51145-151">Dynamics CRM for Tablets for Android</span></span>
    
  - <span data-ttu-id="51145-152">Excel per Android</span><span class="sxs-lookup"><span data-stu-id="51145-152">Excel for Android</span></span>
    
  - <span data-ttu-id="51145-153">Word per Android</span><span class="sxs-lookup"><span data-stu-id="51145-153">Word for Android</span></span>
    
  - <span data-ttu-id="51145-154">OneNote per iOS</span><span class="sxs-lookup"><span data-stu-id="51145-154">OneNote for iOS</span></span>
    
30. <span data-ttu-id="51145-155">Chiudere blade **Mobile Apps - App** .</span><span class="sxs-lookup"><span data-stu-id="51145-155">Close the **Mobile Apps - Apps** blade.</span></span>
    
31. <span data-ttu-id="51145-156">Su blade **App Mobile** , fare clic su **Criteri di protezione delle App**.</span><span class="sxs-lookup"><span data-stu-id="51145-156">On the **Mobile Apps** blade, click **App Protection Policies**.</span></span>
    
32. <span data-ttu-id="51145-157">Su blade **Criteri di protezione delle App** , fare clic su **Aggiungi un criterio**.</span><span class="sxs-lookup"><span data-stu-id="51145-157">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
33. <span data-ttu-id="51145-158">Su blade **Aggiungi un criterio** , digitare **iOS**e quindi fare clic su **Seleziona App necessari**.</span><span class="sxs-lookup"><span data-stu-id="51145-158">On the **Add a policy** blade, type **iOS**, and then click **Select required apps**.</span></span>
    
34. <span data-ttu-id="51145-159">Su blade **App** , fare clic su **PowerPoint** **Microsoft Dynamics CRM su iPhone**, **Excel**, **Microsoft Dynamics CRM su iPhone**, **Word**, **OneNote**, **Outlook**e quindi fare clic su **Seleziona**.</span><span class="sxs-lookup"><span data-stu-id="51145-159">On the **Apps** blade, click **PowerPoint**, **Microsoft Dynamics CRM on iPhone**, **Excel**, **Microsoft Dynamics CRM on iPhone**, **Word**, **OneNote**, and **Outlook**, and then click **Select**.</span></span>
    
35. <span data-ttu-id="51145-160">Su blade **Aggiungi un criterio** , fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="51145-160">On the **Add a policy** blade, click **Create**.</span></span>
    
36. <span data-ttu-id="51145-161">Su blade **Criteri di protezione delle App** , fare clic su **Aggiungi un criterio**.</span><span class="sxs-lookup"><span data-stu-id="51145-161">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
37. <span data-ttu-id="51145-162">Su blade **Aggiungi un criterio** , digitare **Android**, selezionare **Android** nella **piattaforma**e quindi fare clic su **Seleziona App necessari**.</span><span class="sxs-lookup"><span data-stu-id="51145-162">On the **Add a policy** blade, type **Android**, select **Android** in **Platform**, and then click **Select required apps**.</span></span>
    
38. <span data-ttu-id="51145-163">Su blade **App** , fare clic su **PowerPoint**, **Dynamics CRM per Tablet**, **Excel**, **Word**, **Outlook**e **Dynamics CRM per i telefoni**e quindi fare clic su **Seleziona**.</span><span class="sxs-lookup"><span data-stu-id="51145-163">On the **Apps** blade, click **PowerPoint**, **Dynamics CRM for tablets**, **Excel**, **Word**, **Outlook**, and **Dynamics CRM for phones**, and then click **Select**.</span></span>
    
39. <span data-ttu-id="51145-164">Su blade **Aggiungi un criterio** , fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="51145-164">On the **Add a policy** blade, click **Create**.</span></span>
    
<span data-ttu-id="51145-165">Ora si dispone di due criteri MAM, uno per i dispositivi iOS e uno per i dispositivi Android, e sono pronti per essere utilizzati con le impostazioni di testing per le app selezionate.</span><span class="sxs-lookup"><span data-stu-id="51145-165">You now have two MAM policies, one for iOS devices and one for Android devices, and are ready to experiment with testing settings for the selected apps.</span></span>
  
> [!TIP]
> <span data-ttu-id="51145-166">Fare clic [qui](http://aka.ms/catlgstack) per una rappresentazione grafica a tutti gli articoli nello stack di uno Microsoft Cloud Test Lab Guide.</span><span class="sxs-lookup"><span data-stu-id="51145-166">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="51145-167">See Also</span><span class="sxs-lookup"><span data-stu-id="51145-167">See Also</span></span>

[<span data-ttu-id="51145-168">L'ambiente di sviluppo e di testing Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="51145-168">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="51145-169">Registrare iOS e dispositivi Android nell'ambiente di sviluppo e di testing Microsoft Enterprise 365</span><span class="sxs-lookup"><span data-stu-id="51145-169">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[<span data-ttu-id="51145-170">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="51145-170">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="51145-171">Sicurezza (EMS) + mobilità aziendale</span><span class="sxs-lookup"><span data-stu-id="51145-171">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)

