---
title: Registrare iOS e dispositivi Android nell'ambiente di sviluppo e di testing Microsoft Enterprise 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "Riepilogo: Utilizzare questa guida dei laboratori di testing per registrare i dispositivi nell'ambiente di sviluppo e di testing Microsoft 365 e gestirle in modalità remota."
ms.openlocfilehash: 8765a7ffb1bff1f257d7cd1ce5181561c2cf0080
ms.sourcegitcommit: 771f227d3049498fcbd7cfbeaf649e3d77e73c86
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a>Registrare iOS e dispositivi Android nell'ambiente di sviluppo e di testing Microsoft Enterprise 365

 **Riepilogo:** Utilizzare questa guida dei laboratori di testing per registrare i dispositivi nell'ambiente di sviluppo e di testing Microsoft 365 e gestirle in modalità remota.
  
Microsoft Enterprise mobilità famiglia di prodotti (EMS) contribuisce a migliorare la produttività utilizzando le applicazioni preferite e dispositivi proteggendo al contempo i dati dell'organizzazione i dipendenti. Per ulteriori informazioni, vedere [Security (EMS) + mobilità aziendale](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Se si desidera applicare la sicurezza a livello di dispositivi, è necessario registrare i dispositivi in Microsoft Intune. La registrazione dispositivo non solo consente di gestire i dispositivi di proprietà dell'organizzazione, ma anche personale (BYOD) e i dispositivi condivisi, a seconda dell'organizzazione del legale criteri.
  
Seguendo le istruzioni fornite in questo articolo, sarà possibile registrare e verificare le funzionalità di gestione di dispositivi mobili base iOS e dei dispositivi Android nell'ambiente di sviluppo e di testing Microsoft 365.
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>Fase 1: Creare l'ambiente di sviluppo e di testing Microsoft 365

Seguire le istruzioni [nell'ambiente di sviluppo e di testing The Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Fase 2: Registrare i iOS e i dispositivi Android

Innanzitutto, utilizzare le istruzioni riportate in [installare ed eseguire l'accesso all'app portale della società](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) per personalizzare l'app portale della società Intune Microsoft per il tenant di sviluppo e di testing.

Successivamente, utilizzare le istruzioni in [configurare l'accesso alle risorse della società](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) per registrare un dispositivo iOS.

Successivamente, utilizzare le istruzioni nella [registrazione dispositivo Android Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) per registrare un dispositivo Android.

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a>Fase 2: Gestire i iOS e dispositivi Android in remoto

Microsoft Intune fornisce sia la funzionalità di blocco remoto sia quella di reimpostazione del passcode. Se un utente perde il proprio dispositivo, è possibile bloccare il dispositivo in modalità remota. Se un utente dimentica il proprio passcode, è possibile rimuovere il passcode in modalità remota.
  
Per bloccare un dispositivo iOS in remoto:
  
1.  Aprire una nuova scheda e passare a http://manage.microsoft.com (se necessario). 

2.  Dalla console di amministrazione di Microsoft Intune del browser, fare clic su **gruppi** nel riquadro di spostamento sinistro.

3. Nel riquadro **gruppi** aprire **tutti i dispositivi > dispositivi mobili tutti > tutti i dispositivi gestiti diretto**.
    
4. Nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic sulla scheda **dispositivi** .
    
5. Nell'elenco dei dispositivi, fare clic sul dispositivo iOS.  
    
6. Dal dispositivo iOS, verificare che sia nella schermata principale.  
    
7. Dal computer di amministrazione, sulla barra delle applicazioni, fare clic su **remoto attività > blocco remoto**. Guardare il dispositivo iOS quando attivata la sullo schermo del blocco.
    
Per rimuovere il passcode:
  
1. Dal computer di amministrazione, nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic sulla scheda **dispositivi** .
    
2. Nell'elenco fare clic su dispositivo iOS. Nella barra delle applicazioni fare clic su **remoto attività > Passcode Reset**. Attendere un minuto.
    
3. Dal dispositivo iOS sbloccarlo e si noti che non è più un passcode. Per modificare nuovamente il passcode, passare a **Impostazioni**, quindi **Passcode**.
    
Per bloccare un dispositivo Android in remoto:
  
1. Dalla console di amministrazione di Microsoft Intune del browser, fare clic su **gruppi** nel riquadro di spostamento sinistro.
    
2. Nel riquadro **gruppi** aprire **tutti i dispositivi > dispositivi mobili tutti > tutti i dispositivi gestiti diretto**.
    
3. Nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic sulla scheda **dispositivi** .
    
4. Nell'elenco dei dispositivi, fare clic sul dispositivo Android.  
    
5. Dal dispositivo Android, verificare che sia nella schermata principale.  
    
6. Dal computer di amministrazione, sulla barra delle applicazioni, fare clic su **remoto attività > blocco remoto**. Quando richiesto, fare clic su **Sì**.
    
7. Verificare che il dispositivo Android passi alla schermata di blocco.
    
Quando si reimposta il passcode per i dispositivi Android, il portale di amministrazione Intune genera e consente di configurare un passcode complessa.
  
Per reimpostare il passcode in remoto:
  
1. Dal computer di amministrazione, nella scheda console Amministrazione Microsoft Intune del browser, nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic su dispositivo Android.
    
2. Nella barra delle applicazioni fare clic su **remoto attività > Passcode Reset**.
    
3. Nella **attività remota: Passcode Reset** prompt, fare clic su **Sì**. Attendere un minuto.
    
4. Nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic su **Visualizza proprietà**.
    
5. In **Passcode Reset**, si noti il nuovo codice.
    
6. Dal dispositivo Android, immettere il nuovo passcode nella schermata di blocco.  
    
7. Per modificare nuovamente il passcode, passare a **Impostazioni**, scegliere **dispositivo**, scegliere **schermo Blocca**, immettere nuovamente il nuovo passcode, scegliere **blocco dello schermo**e la scelta per il passcode.
    

> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
  
## <a name="see-also"></a>Vedere anche

[Ambiente di sviluppo/test di Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Criteri MAM per l’ambiente di sviluppo/test di Microsoft 365 Enterprise](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Test Lab Guide (TLG) per l’adozione del cloud](cloud-adoption-test-lab-guides-tlgs.md)

[Sicurezza (EMS) + mobilità aziendale](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


