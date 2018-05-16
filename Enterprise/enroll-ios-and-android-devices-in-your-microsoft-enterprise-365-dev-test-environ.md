---
title: Registrare iOS e dispositivi Android nell'ambiente di sviluppo e di testing Microsoft Enterprise 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "Riepilogo: Utilizzare questa guida dei laboratori di testing per registrare i dispositivi nell'ambiente di sviluppo e di testing Microsoft 365 e gestirle in modalità remota."
ms.openlocfilehash: b5ceecd74ac010d787bc580054d5dd43db952fef
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a><span data-ttu-id="faf53-103">Registrare iOS e dispositivi Android nell'ambiente di sviluppo e di testing Microsoft Enterprise 365</span><span class="sxs-lookup"><span data-stu-id="faf53-103">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>

 <span data-ttu-id="faf53-104">**Riepilogo:** Utilizzare questa guida dei laboratori di testing per registrare i dispositivi nell'ambiente di sviluppo e di testing Microsoft 365 e gestirle in modalità remota.</span><span class="sxs-lookup"><span data-stu-id="faf53-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="faf53-p101">Microsoft Enterprise mobilità famiglia di prodotti (EMS) contribuisce a migliorare la produttività utilizzando le applicazioni preferite e dispositivi proteggendo al contempo i dati dell'organizzazione i dipendenti. Per ulteriori informazioni, vedere [Security (EMS) + mobilità aziendale](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="faf53-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="faf53-p102">Se si desidera applicare la sicurezza a livello di dispositivi, è necessario registrare i dispositivi in Microsoft Intune. La registrazione dispositivo non solo consente di gestire i dispositivi di proprietà dell'organizzazione, ma anche personale (BYOD) e i dispositivi condivisi, a seconda dell'organizzazione del legale criteri.</span><span class="sxs-lookup"><span data-stu-id="faf53-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="faf53-109">Seguendo le istruzioni fornite in questo articolo, sarà possibile registrare e verificare le funzionalità di gestione di dispositivi mobili base iOS e dei dispositivi Android nell'ambiente di sviluppo e di testing Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="faf53-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="faf53-110">Fase 1: Creare l'ambiente di sviluppo e di testing Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="faf53-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="faf53-111">Seguire le istruzioni [nell'ambiente di sviluppo e di testing The Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="faf53-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="faf53-112">Fase 2: Registrare i iOS e i dispositivi Android</span><span class="sxs-lookup"><span data-stu-id="faf53-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="faf53-113">Innanzitutto, utilizzare le istruzioni riportate in [installare ed eseguire l'accesso all'app portale della società](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) per personalizzare l'app portale della società Intune Microsoft per il tenant di sviluppo e di testing.</span><span class="sxs-lookup"><span data-stu-id="faf53-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your dev/test tenant.</span></span>

<span data-ttu-id="faf53-114">Successivamente, utilizzare le istruzioni in [configurare l'accesso alle risorse della società](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) per registrare un dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="faf53-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="faf53-115">Successivamente, utilizzare le istruzioni nella [registrazione dispositivo Android Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) per registrare un dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="faf53-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="faf53-116">Fase 2: Gestire i iOS e dispositivi Android in remoto</span><span class="sxs-lookup"><span data-stu-id="faf53-116">Phase 2: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="faf53-p103">Microsoft Intune fornisce sia la funzionalità di blocco remoto sia quella di reimpostazione del passcode. Se un utente perde il proprio dispositivo, è possibile bloccare il dispositivo in modalità remota. Se un utente dimentica il proprio passcode, è possibile rimuovere il passcode in modalità remota.</span><span class="sxs-lookup"><span data-stu-id="faf53-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="faf53-120">Per bloccare un dispositivo iOS in remoto:</span><span class="sxs-lookup"><span data-stu-id="faf53-120">To lock an iOS device remotely:</span></span>
  
1.  <span data-ttu-id="faf53-121">Aprire una nuova scheda e passare a http://manage.microsoft.com (se necessario).</span><span class="sxs-lookup"><span data-stu-id="faf53-121">Open a new tab and go to http://manage.microsoft.com (if needed).</span></span> 

2.  <span data-ttu-id="faf53-122">Dalla console di amministrazione di Microsoft Intune del browser, fare clic su **gruppi** nel riquadro di spostamento sinistro.</span><span class="sxs-lookup"><span data-stu-id="faf53-122">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>

3. <span data-ttu-id="faf53-123">Nel riquadro **gruppi** aprire **tutti i dispositivi > dispositivi mobili tutti > tutti i dispositivi gestiti diretto**.</span><span class="sxs-lookup"><span data-stu-id="faf53-123">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
4. <span data-ttu-id="faf53-124">Nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic sulla scheda **dispositivi** .</span><span class="sxs-lookup"><span data-stu-id="faf53-124">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
5. <span data-ttu-id="faf53-125">Nell'elenco dei dispositivi, fare clic sul dispositivo iOS. </span><span class="sxs-lookup"><span data-stu-id="faf53-125">In the devices list, click your iOS device.</span></span> 
    
6. <span data-ttu-id="faf53-126">Dal dispositivo iOS, verificare che sia nella schermata principale. </span><span class="sxs-lookup"><span data-stu-id="faf53-126">From your iOS device, make sure it is at the main screen.</span></span> 
    
7. <span data-ttu-id="faf53-p104">Dal computer di amministrazione, sulla barra delle applicazioni, fare clic su **remoto attività > blocco remoto**. Guardare il dispositivo iOS quando attivata la sullo schermo del blocco.</span><span class="sxs-lookup"><span data-stu-id="faf53-p104">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="faf53-129">Per rimuovere il passcode:</span><span class="sxs-lookup"><span data-stu-id="faf53-129">To remove the passcode:</span></span>
  
1. <span data-ttu-id="faf53-130">Dal computer di amministrazione, nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic sulla scheda **dispositivi** .</span><span class="sxs-lookup"><span data-stu-id="faf53-130">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="faf53-p105">Nell'elenco fare clic su dispositivo iOS. Nella barra delle applicazioni fare clic su **remoto attività > Passcode Reset**. Attendere un minuto.</span><span class="sxs-lookup"><span data-stu-id="faf53-p105">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="faf53-p106">Dal dispositivo iOS sbloccarlo e si noti che non è più un passcode. Per modificare nuovamente il passcode, passare a **Impostazioni**, quindi **Passcode**.</span><span class="sxs-lookup"><span data-stu-id="faf53-p106">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
<span data-ttu-id="faf53-136">Per bloccare un dispositivo Android in remoto:</span><span class="sxs-lookup"><span data-stu-id="faf53-136">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="faf53-137">Dalla console di amministrazione di Microsoft Intune del browser, fare clic su **gruppi** nel riquadro di spostamento sinistro.</span><span class="sxs-lookup"><span data-stu-id="faf53-137">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="faf53-138">Nel riquadro **gruppi** aprire **tutti i dispositivi > dispositivi mobili tutti > tutti i dispositivi gestiti diretto**.</span><span class="sxs-lookup"><span data-stu-id="faf53-138">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="faf53-139">Nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic sulla scheda **dispositivi** .</span><span class="sxs-lookup"><span data-stu-id="faf53-139">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="faf53-140">Nell'elenco dei dispositivi, fare clic sul dispositivo Android. </span><span class="sxs-lookup"><span data-stu-id="faf53-140">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="faf53-141">Dal dispositivo Android, verificare che sia nella schermata principale. </span><span class="sxs-lookup"><span data-stu-id="faf53-141">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="faf53-p107">Dal computer di amministrazione, sulla barra delle applicazioni, fare clic su **remoto attività > blocco remoto**. Quando richiesto, fare clic su **Sì**.</span><span class="sxs-lookup"><span data-stu-id="faf53-p107">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="faf53-144">Verificare che il dispositivo Android passi alla schermata di blocco.</span><span class="sxs-lookup"><span data-stu-id="faf53-144">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="faf53-145">Quando si reimposta il passcode per i dispositivi Android, il portale di amministrazione Intune genera e consente di configurare un passcode complessa.</span><span class="sxs-lookup"><span data-stu-id="faf53-145">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="faf53-146">Per reimpostare il passcode in remoto:</span><span class="sxs-lookup"><span data-stu-id="faf53-146">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="faf53-147">Dal computer di amministrazione, nella scheda console Amministrazione Microsoft Intune del browser, nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic su dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="faf53-147">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="faf53-148">Nella barra delle applicazioni fare clic su **remoto attività > Passcode Reset**.</span><span class="sxs-lookup"><span data-stu-id="faf53-148">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="faf53-p108">Nella **attività remota: Passcode Reset** prompt, fare clic su **Sì**. Attendere un minuto.</span><span class="sxs-lookup"><span data-stu-id="faf53-p108">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="faf53-151">Nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic su **Visualizza proprietà**.</span><span class="sxs-lookup"><span data-stu-id="faf53-151">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="faf53-152">In **Passcode Reset**, si noti il nuovo codice.</span><span class="sxs-lookup"><span data-stu-id="faf53-152">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="faf53-153">Dal dispositivo Android, immettere il nuovo passcode nella schermata di blocco. </span><span class="sxs-lookup"><span data-stu-id="faf53-153">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="faf53-154">Per modificare nuovamente il passcode, passare a **Impostazioni**, scegliere **dispositivo**, scegliere **schermo Blocca**, immettere nuovamente il nuovo passcode, scegliere **blocco dello schermo**e la scelta per il passcode.</span><span class="sxs-lookup"><span data-stu-id="faf53-154">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    

> [!TIP]
> <span data-ttu-id="faf53-155">Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.</span><span class="sxs-lookup"><span data-stu-id="faf53-155">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="faf53-156">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="faf53-156">See Also</span></span>

[<span data-ttu-id="faf53-157">Ambiente di sviluppo/test di Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="faf53-157">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="faf53-158">Criteri MAM per l’ambiente di sviluppo/test di Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="faf53-158">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="faf53-159">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="faf53-159">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="faf53-160">Sicurezza (EMS) + mobilità aziendale</span><span class="sxs-lookup"><span data-stu-id="faf53-160">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


