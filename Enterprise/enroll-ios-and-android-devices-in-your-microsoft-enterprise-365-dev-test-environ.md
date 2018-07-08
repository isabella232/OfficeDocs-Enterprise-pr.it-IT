---
title: Registrazione dei dispositivi iOS e Android nell'ambiente di sviluppo e test di Microsoft 365 Enterprise
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
ms.openlocfilehash: a5d43a0ef3ed090f84c8415de3ac26f53fdafe0a
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188104"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a>Registrazione dei dispositivi iOS e Android nell'ambiente di sviluppo e test di Microsoft 365 Enterprise

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

3. Nel riquadro **Gruppi**, aprire **Tutti i dispositivi > Tutti i dispositivi mobili > Tutti i dispositivi gestiti direttamente**.
    
4. Nel riquadro **Tutti i dispositivi gestiti direttamente**, fare clic sulla scheda **Dispositivi**.
    
5. Nell'elenco dei dispositivi, fare clic sul dispositivo iOS.  
    
6. Dal dispositivo iOS, verificare che sia nella schermata principale.  
    
7. Dal computer di amministrazione, nella barra delle applicazioni fare clic su **Attività remote > Blocco remoto**. Verificare che il dispositivo iOS passi alla schermata di blocco.
    
Per rimuovere il passcode:
  
1. Dal computer di amministrazione, nel riquadro **Tutti i dispositivi gestiti direttamente**, fare clic sulla scheda **Dispositivi**.
    
2. Nell'elenco, fare clic sul dispositivo iOS. Nella barra delle applicazioni fare clic su **Attività remote > Reimpostazione passcode**. Attendere un minuto.
    
3. Dal dispositivo iOS, sbloccarlo e notare che non è più presente un passcode. Per modificare nuovamente il passcode, passare a **Impostazioni**, quindi a **Passcode**.
    
Per bloccare un dispositivo Android in remoto:
  
1. Dalla console di amministrazione di Microsoft Intune del browser, fare clic su **gruppi** nel riquadro di spostamento sinistro.
    
2. Nel riquadro **Gruppi**, aprire **Tutti i dispositivi > Tutti i dispositivi mobili > Tutti i dispositivi gestiti direttamente**.
    
3. Nel riquadro **Tutti i dispositivi gestiti direttamente**, fare clic sulla scheda **Dispositivi**.
    
4. Nell'elenco dei dispositivi, fare clic sul dispositivo Android.  
    
5. Dal dispositivo Android, verificare che sia nella schermata principale.  
    
6. Dal computer di amministrazione, nella barra delle applicazioni fare clic su **Attività remote > Blocco remoto**. Quando viene richiesto, fare clic su **Sì**.
    
7. Verificare che il dispositivo Android passi alla schermata di blocco.
    
Quando si reimposta il passcode per i dispositivi Android, il portale di amministrazione Intune genera e consente di configurare un passcode complessa.
  
Per reimpostare il passcode in remoto:
  
1. Dal computer di amministrazione, nella scheda della console di amministrazione di Microsoft Intune del browser, nel riquadro **Tutti i dispositivi gestiti direttamente** fare clic sul dispositivo Android.
    
2. Nella barra delle applicazioni fare clic su **Attività remote > Reimpostazione passcode**.
    
3. Nel prompt **Attività remota: Reimpostazione passcode**, fare clic su **Sì**. Attendere un minuto.
    
4. Nel riquadro **Tutti i dispositivi gestiti direttamente**, fare clic su **Visualizza proprietà**.
    
5. In **Reimpostazione passcode**, notare il nuovo passcode.
    
6. Dal dispositivo Android, immettere il nuovo passcode nella schermata di blocco.  
    
7. Per modificare nuovamente il passcode, accedere a **Impostazioni**, toccare **Dispositivo**, **Schermata di blocco**, reimmettere il nuovo passcode, toccare **Blocco per lo schermo** e infine la scelta per il passcode.
    

> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
  
## <a name="see-also"></a>Vedere anche

[Ambiente di sviluppo/test di Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Criteri MAM per l'ambiente di sviluppo e test di Microsoft 365 Enterprise](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)

[Sicurezza (EMS) + mobilità aziendale](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


