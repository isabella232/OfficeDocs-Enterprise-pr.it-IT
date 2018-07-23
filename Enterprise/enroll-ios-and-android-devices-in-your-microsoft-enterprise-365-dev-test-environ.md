---
title: Registrazione dei dispositivi iOS e Android nell'ambiente di sviluppo e test di Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "Riepilogo: Utilizzare questa guida dei laboratori di testing per registrare i dispositivi nell'ambiente di sviluppo e di testing Microsoft 365 e gestirle in modalità remota."
ms.openlocfilehash: e4b8491a70d0d0177e0a434d228136243201e788
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720412"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="4baf8-103">Registrazione dei dispositivi iOS e Android nell'ambiente di sviluppo e test di Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="4baf8-103">Enroll iOS and Android devices in your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="4baf8-104">**Riepilogo:** Utilizzare questa guida dei laboratori di testing per registrare i dispositivi nell'ambiente di sviluppo e di testing Microsoft 365 e gestirle in modalità remota.</span><span class="sxs-lookup"><span data-stu-id="4baf8-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="4baf8-p101">Microsoft Enterprise mobilità famiglia di prodotti (EMS) contribuisce a migliorare la produttività utilizzando le applicazioni preferite e dispositivi proteggendo al contempo i dati dell'organizzazione i dipendenti. Per ulteriori informazioni, vedere [Security (EMS) + mobilità aziendale](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="4baf8-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="4baf8-p102">Se si desidera applicare la sicurezza a livello di dispositivi, è necessario registrare i dispositivi in Microsoft Intune. La registrazione dispositivo non solo consente di gestire i dispositivi di proprietà dell'organizzazione, ma anche personale (BYOD) e i dispositivi condivisi, a seconda dell'organizzazione del legale criteri.</span><span class="sxs-lookup"><span data-stu-id="4baf8-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="4baf8-109">Seguendo le istruzioni fornite in questo articolo, sarà possibile registrare e verificare le funzionalità di gestione di dispositivi mobili base iOS e dei dispositivi Android nell'ambiente di sviluppo e di testing Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="4baf8-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="4baf8-110">Fase 1: Creare l'ambiente di sviluppo e di testing Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="4baf8-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="4baf8-111">Seguire le istruzioni [nell'ambiente di sviluppo e di testing The Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="4baf8-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="4baf8-112">Fase 2: Registrare i iOS e i dispositivi Android</span><span class="sxs-lookup"><span data-stu-id="4baf8-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="4baf8-113">Innanzitutto, utilizzare le istruzioni riportate in [installare ed eseguire l'accesso all'app portale della società](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) per personalizzare le app portale della società Intune Microsoft per l'ambiente di testing.</span><span class="sxs-lookup"><span data-stu-id="4baf8-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your test environment.</span></span>

<span data-ttu-id="4baf8-114">Successivamente, utilizzare le istruzioni in [configurare l'accesso alle risorse della società](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) per registrare un dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="4baf8-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="4baf8-115">Successivamente, utilizzare le istruzioni nella [registrazione dispositivo Android Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) per registrare un dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="4baf8-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="4baf8-116">Fase 3: Gestire i iOS e dispositivi Android in remoto</span><span class="sxs-lookup"><span data-stu-id="4baf8-116">Phase 3: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="4baf8-p103">Intune Microsoft sono disponibili sia blocco remoto e il passcode reimpostare funzionalità. Se si perde il dispositivo, è possibile bloccare il dispositivo in modalità remota. Se si dimentica il passcode, è possibile reimpostare in remoto.</span><span class="sxs-lookup"><span data-stu-id="4baf8-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset it remotely.</span></span>
  
<span data-ttu-id="4baf8-120">Per bloccare un dispositivo Android o iOS da postazione remota:</span><span class="sxs-lookup"><span data-stu-id="4baf8-120">To lock an iOS or Android device remotely:</span></span>

1. <span data-ttu-id="4baf8-121">Accedere al portale di Azure al [https://portal.azure.com](https://portal.azure.com) con le credenziali dell'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="4baf8-121">Sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com) with the credentials of your global administrator account.</span></span>
2. <span data-ttu-id="4baf8-122">Fare clic su **tutti i servizi**, digitare **Intune**e quindi fare clic su **Intune**.</span><span class="sxs-lookup"><span data-stu-id="4baf8-122">Click **All services**, type **Intune**, and then click **Intune**.</span></span>
3. <span data-ttu-id="4baf8-123">Fare clic su **dispositivi > tutti i dispositivi**.</span><span class="sxs-lookup"><span data-stu-id="4baf8-123">Click **Devices > All devices**.</span></span>
4. <span data-ttu-id="4baf8-124">Nell'elenco dei dispositivi, fare clic su un dispositivo Android o iOS e quindi fare clic sull'azione **Blocca remoto** .</span><span class="sxs-lookup"><span data-stu-id="4baf8-124">In the list of devices, click an iOS or Android device, and then click the **Remote lock** action.</span></span>

    
<span data-ttu-id="4baf8-125">Per reimpostare il passcode in remoto:</span><span class="sxs-lookup"><span data-stu-id="4baf8-125">To reset the passcode remotely:</span></span>

1. <span data-ttu-id="4baf8-126">Se necessario, accedere al portale di Azure al [https://portal.azure.com](https://portal.azure.com) con le credenziali dell'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="4baf8-126">If needed, sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com) with the credentials of your global administrator account.</span></span>
2. <span data-ttu-id="4baf8-127">Fare clic su **tutti i servizi**, digitare **Intune**e quindi fare clic su **Intune**.</span><span class="sxs-lookup"><span data-stu-id="4baf8-127">Click **All services**, type **Intune**, and then click **Intune**.</span></span>
3. <span data-ttu-id="4baf8-128">Fare clic su **dispositivi > tutti i dispositivi**.</span><span class="sxs-lookup"><span data-stu-id="4baf8-128">Click **Devices > All devices**.</span></span>
4. <span data-ttu-id="4baf8-p104">Dall'elenco dei dispositivi di gestione, fare clic su un dispositivo Android o iOS e scegliere **... Ulteriori**. Scegliere quindi l'azione remoto dispositivo **rimuovere passcode** .</span><span class="sxs-lookup"><span data-stu-id="4baf8-p104">From the list of devices you manage, click an iOS or Android device, and choose **...More**. Then choose the **Remove passcode** device remote action.</span></span>

<span data-ttu-id="4baf8-131">Per la sperimentazione aggiuntiva, vedere [azioni disponibili dispositivi](https://docs.microsoft.com/intune/device-management#available-device-actions).</span><span class="sxs-lookup"><span data-stu-id="4baf8-131">For additional experimentation, see [Available device actions](https://docs.microsoft.com/intune/device-management#available-device-actions).</span></span>

    

> [!TIP]
> <span data-ttu-id="4baf8-132">Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4baf8-132">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4baf8-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4baf8-133">See Also</span></span>

[<span data-ttu-id="4baf8-134">Ambiente di sviluppo/test di Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="4baf8-134">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="4baf8-135">Criteri MAM per l’ambiente di sviluppo/test di Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="4baf8-135">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="4baf8-136">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="4baf8-136">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="4baf8-137">Sicurezza (EMS) + mobilità aziendale</span><span class="sxs-lookup"><span data-stu-id="4baf8-137">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


