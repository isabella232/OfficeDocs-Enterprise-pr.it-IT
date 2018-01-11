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
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: 'Riepilogo: Utilizzare questa guida dei laboratori di testing per aggiungere criteri di gestione (MAM) mobili applicazione EMS all''ambiente di sviluppo e di testing Microsoft 365.'
ms.openlocfilehash: cd5a9801ec7cc5c8fe287fa65015fcb02dd542bf
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a>Criteri MAM per l'ambiente di sviluppo e di testing Microsoft 365 Enterprise

 **Riepilogo:** Utilizzare questa guida dei laboratori di testing per aggiungere criteri di gestione (MAM) mobili applicazione EMS all'ambiente di sviluppo e di testing Microsoft 365.
  
La mobilità aziendale Microsoft + sicurezza (EMS) contribuisce a migliorare la produttività utilizzando le applicazioni preferite e dispositivi proteggendo al contempo i dati dell'organizzazione i dipendenti. Per ulteriori informazioni, vedere [Security (EMS) + mobilità aziendale](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Con le istruzioni riportate in questo articolo, è aggiungere criteri di gestione (MAM) applicazione per dispositivi mobili per l'ambiente di sviluppo e di testing Microsoft 365.
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a>Fase 1: Preparare l'ambiente di sviluppo e di testing Microsoft 365

Seguire le istruzioni [nell'ambiente di sviluppo e di testing The Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a>Fase 2: creare e distribuire criteri MAM per i dispositivi iOS e Android

In questa fase, è possibile creare e distribuire due diversi criteri MAM: uno per i dispositivi iOS e uno per i dispositivi Android.
  
1. Accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) e accedere alla sottoscrizione di prova di Office 365 con l'account di amministratore globale.
    
2. In una nuova scheda del browser, aprire il portale di Azure ([https://azure.portal.com](https://azure.portal.com)) e accedere utilizzando l'account amministratore globale di Office 365.
    
3. Nella scheda Azure portale in Internet Explorer, nel riquadro di spostamento fare clic su **altri servizi** (o freccia destra), digitare **Intune**e quindi fare clic su **Intune**.
    
4. Nel riquadro di spostamento a sinistra fare clic su **Gruppi**.
    
5. Su blade **utenti e gruppi di tutti i gruppi** , fare clic su **Aggiungi**.
    
6. Su blade **gruppo** , digitare **gestiti gli utenti di dispositivi iOS** nella casella **nome**, selezionare **assegnato** nel **tipo di appartenenza**, selezionare **Sì** per **caratteristiche di attivare Office?**, quindi fare clic su **Crea**. 
    
7. Chiudere e il **gruppo** .
    
8. Su blade **utenti e gruppi di tutti i gruppi** , fare clic su **Aggiungi**.
    
9. Su blade **gruppo** , digitare **gli utenti di dispositivi Android gestiti** in **nome**, selezionare **assegnato** nel **tipo di appartenenza**, selezionare **Sì** per **caratteristiche di attivare Office?**, quindi fare clic su **Crea**.
    
10. Chiudere blade **utenti e gruppi di tutti i gruppi** .
    
11. Su blade **Intune** , nell'elenco **attività veloce** , fare clic su **Crea un criterio di conformità**.
    
12. Su blade **Profili dei criteri di conformità** , fare clic su **Crea criterio**.
    
13. In **nome**blade **Creare criteri** , digitare **iOS**. Nella **piattaforma**, selezionare **iOS**, fare clic su blade **dei criteri di conformità iOS** **OK** e quindi fare clic su **Crea**.
    
14. Su blade **Profili dei criteri di conformità** , fare clic su **Crea criterio**.
    
15. In **nome**blade **Creare criteri** , digitare **Android**. Nella **piattaforma**, selezionare **Android**, fare clic su blade **criteri di conformità Android** **OK** e quindi fare clic su **Crea**.
    
16. Scegliere il nome del criterio **Android** blade **Profili dei criteri di conformità** .
    
17. Nel riquadro di spostamento sinistro della stessa e **Android - proprietà** , fare clic su **assegnazioni**e quindi fare clic su **Seleziona gruppi**.
    
18. Su blade **Selezionare gruppi** fare clic sul gruppo di **utenti di dispositivi Android gestiti** e quindi fare clic su **Seleziona**.
    
19. Fare clic su **Salva**e quindi chiudere blade **Android - assegnazioni** .
    
20. Scegliere il nome del criterio **iOS** blade **Profili dei criteri di conformità** .
    
21. Nel riquadro di spostamento sinistra di blade **iOS - proprietà** , fare clic su **assegnazioni**e quindi fare clic su **Seleziona gruppi**.
    
22. Su blade **Selezionare gruppi** fare clic sul gruppo di **utenti di dispositivi iOS gestite** e quindi fare clic su **Seleziona**.
    
23. Fare clic su **Salva**e quindi chiudere blade **iOS - assegnazioni** .
    
24. Chiudere blade **Profili dei criteri di conformità** .
    
25. Su blade **Intune** , fare clic su **Gestione applicazioni** nel riquadro di spostamento sinistro.
    
26. Su blade **App Mobile** , fare clic su **App**.
    
27. Nell'elenco delle App, fare clic su **PowerPoint** 
    
28. Su blade **Panoramica di PowerPoint** , fare clic su **assegnazioni > Seleziona gruppi > gestiti dispositivi iOS > selezionare**. In **tipo**selezionare **disponibile**e quindi fare clic su **Salva**.
    
29. Ripetere il passaggio 28 per le app seguenti:
    
  - Outlook per Android
    
  - Word per iOS
    
  - Excel per iOS
    
  - Outlook per iOS
    
  - Microsoft Dynamics CRM su iPad per iOS
    
  - Microsoft Dynamics CRM su iPhone per iOS
    
  - Dynamics CRM per telefoni per Android
    
  - Dynamics CRM per tablet per Android
    
  - Excel per Android
    
  - Word per Android
    
  - OneNote per iOS
    
30. Chiudere blade **Mobile Apps - App** .
    
31. Su blade **App Mobile** , fare clic su **Criteri di protezione delle App**.
    
32. Su blade **Criteri di protezione delle App** , fare clic su **Aggiungi un criterio**.
    
33. Su blade **Aggiungi un criterio** , digitare **iOS**e quindi fare clic su **Seleziona App necessari**.
    
34. Su blade **App** , fare clic su **PowerPoint** **Microsoft Dynamics CRM su iPhone**, **Excel**, **Microsoft Dynamics CRM su iPhone**, **Word**, **OneNote**, **Outlook**e quindi fare clic su **Seleziona**.
    
35. Su blade **Aggiungi un criterio** , fare clic su **Crea**.
    
36. Su blade **Criteri di protezione delle App** , fare clic su **Aggiungi un criterio**.
    
37. Su blade **Aggiungi un criterio** , digitare **Android**, selezionare **Android** nella **piattaforma**e quindi fare clic su **Seleziona App necessari**.
    
38. Su blade **App** , fare clic su **PowerPoint**, **Dynamics CRM per Tablet**, **Excel**, **Word**, **Outlook**e **Dynamics CRM per i telefoni**e quindi fare clic su **Seleziona**.
    
39. Su blade **Aggiungi un criterio** , fare clic su **Crea**.
    
Ora si dispone di due criteri MAM, uno per i dispositivi iOS e uno per i dispositivi Android, e sono pronti per essere utilizzati con le impostazioni di testing per le app selezionate.
  
> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
  
## <a name="see-also"></a>Vedere anche

[L'ambiente di sviluppo e di testing Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Registrare iOS e dispositivi Android nell'ambiente di sviluppo e di testing Microsoft Enterprise 365](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)

[Sicurezza (EMS) + mobilità aziendale](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


