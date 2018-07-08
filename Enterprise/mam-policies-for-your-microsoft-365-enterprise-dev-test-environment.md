---
title: Criteri MAM per l'ambiente di sviluppo e test di Microsoft 365 Enterprise
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
description: "Riepilogo: Utilizzare questa guida dei laboratori di testing per aggiungere criteri di gestione (MAM) mobili applicazione EMS all'ambiente di sviluppo e di testing Microsoft 365."
ms.openlocfilehash: 0a5c81665edf06631b8cebc57c9e715c78d3d85e
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188154"
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a>Criteri MAM per l'ambiente di sviluppo e test di Microsoft 365 Enterprise

 **Riepilogo:** Utilizzare questa guida dei laboratori di testing per aggiungere criteri di gestione (MAM) mobili applicazione EMS all'ambiente di sviluppo e di testing Microsoft 365.
  
La mobilità aziendale Microsoft + sicurezza (EMS) contribuisce a migliorare la produttività utilizzando le applicazioni preferite e dispositivi proteggendo al contempo i dati dell'organizzazione i dipendenti. Per ulteriori informazioni, vedere [Security (EMS) + mobilità aziendale](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Con le istruzioni riportate in questo articolo, è aggiungere criteri di gestione (MAM) applicazione per dispositivi mobili per l'ambiente di sviluppo e di testing Microsoft 365.
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a>Fase 1: Preparare l'ambiente di sviluppo e di testing Microsoft 365

Seguire le istruzioni [nell'ambiente di sviluppo e di testing The Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a>Fase 2: creare e distribuire criteri MAM per i dispositivi iOS e Android

In questa fase, è possibile creare e distribuire due diversi criteri MAM: uno per i dispositivi iOS e uno per i dispositivi Android.
  
1. Accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) ed eseguire l'accesso alla sottoscrizione di prova di Office 365 con l'account di amministratore globale.
    
2. In una nuova scheda del browser, aprire il portale di Azure ([https://azure.portal.com](https://azure.portal.com)) ed eseguire l'accesso utilizzando l'account amministratore globale di Office 365.
    
3. Nella scheda Azure portale in Internet Explorer, nel riquadro di spostamento fare clic su **tutti i servizi**, digitare **Intune**e quindi fare clic su **Intune**.
    
4. Nel riquadro di spostamento a sinistra fare clic su **Gruppi**.
    
5. Su blade **gruppi a tutti i gruppi** , fare clic su **+ nuovo gruppo**.
    
6. Su blade **gruppo** , selezionare **Office 365** per **gruppo tipo?**, digitare **gestiti gli utenti di dispositivi iOS** nella casella **nome**, selezionare **assegnato** nel **tipo di appartenenza**e quindi fare clic su **Crea**. 
    
7. Chiudere il pannello **Gruppo**.
    
8. Su blade **gruppi a tutti i gruppi** , fare clic su **Aggiungi**.
    
9. Su blade **gruppo** , selezionare **Office 365** per **gruppo tipo?**, digitare **gestiti Android utente dispositivo** in **nome**, selezionare **assegnato** nel **tipo di appartenenza**e quindi fare clic su **Crea**.
    
10. Chiudere blade **gruppi a tutti i gruppi** .
    
11. Nel pannello **Intune**, nell'elenco **Attività rapide** fare clic su **Crea nuovi criteri di conformità**.
    
12. Nel pannello **Profili dei criteri di conformità**, fare clic su **Crea criterio**.
    
13. Nel pannello **Crea criterio**, in **Nome** digitare **iOS**. In **Piattaforma**, selezionare **iOS**, fare clic su **OK** nel pannello **Criteri di conformità di iOS**, quindi fare clic su **Crea**.
    
14. Nel pannello **Profili dei criteri di conformità**, fare clic su **Crea criterio**.
    
15. Nel pannello **Crea criterio**, in **Nome** digitare **Android**. In **Piattaforma**, selezionare **Android**, fare clic su **OK** nel pannello **Criteri di conformità di Android**, quindi fare clic su **Crea**.
    
16. Nel pannello **Profili dei criteri di conformità**, fare clic sul nome del criterio **Android**.
    
17. Nella barra di spostamento a sinistra del pannello **Android - Proprietà**, fare clic su **Assegnazioni**, quindi su **Seleziona gruppi**.
    
18. Nel pannello **Seleziona gruppi**, fare clic sul gruppo **Utenti dei dispositivi Android gestiti**, quindi fare clic su **Seleziona**.
    
19. Fare clic su **Salva**e quindi chiudere blade **Android - assegnazioni** .
    
20. Nel pannello **Profili dei criteri di conformità**, fare clic sul nome del criterio **iOS**.
    
21. Nella barra di spostamento a sinistra del pannello **iOS - Proprietà**, fare clic su **Assegnazioni**, quindi su **Seleziona gruppi**.
    
22. Nel pannello **Seleziona gruppi**, fare clic sul gruppo **Utenti dei dispositivi iOS gestiti**, quindi fare clic su **Seleziona**.
    
23. Fare clic su **Salva**e quindi chiudere blade **iOS - assegnazioni** .
    
24. Chiudere il pannello **Profili dei criteri di conformità**.
    
25. Nel pannello **Intune**, fare clic su **Gestisci app** nella barra di spostamento a sinistra.
    
26. Nel pannello **App mobili**, fare clic su **App**.
    
27. Nell'elenco delle app, fare clic su **PowerPoint**,  
    
28. Nel pannello **Panoramica di PowerPoint**, fare clic su **Assegnazioni > Seleziona gruppi > Dispositivi iOS gestiti > Seleziona**. In **Tipo**, selezionare **Disponibile**, quindi fare clic su **Salva**.
    
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
    
30. Chiudere il pannello **App mobili - App**.
    
31. Nel pannello **App mobili**, fare clic su **Criteri di protezione delle app**.
    
32. Nel pannello **Criteri di protezione delle app**, fare clic su **Aggiungi un criterio**.
    
33. Nel pannello **Aggiungi un criterio**, digitare **iOS**, quindi fare clic su **Selezionare le app richieste**.
    
34. Nel pannello **App**, fare clic su **PowerPoint**, **Microsoft Dynamics CRM su iPhone**, **Excel**, **Microsoft Dynamics CRM su iPhone**, **Word**, **OneNote** e **Outlook**, quindi fare clic su **Seleziona**.
    
35. Nel pannello **Aggiungi un criterio**, fare clic su **Crea**.
    
36. Nel pannello **Criteri di protezione delle app**, fare clic su **Aggiungi un criterio**.
    
37. Nel pannello **Aggiungi un criterio**, digitare **Android**, selezionare **Android** in **Piattaforma**, quindi fare clic su **Selezionare le app richieste**.
    
38. Nel pannello **App**, fare clic su **PowerPoint**, **Dynamics CRM per tablet**, **Excel**, **Word**, **Outlook** e **Dynamics CRM per cellulari**, quindi fare clic su **Seleziona**.
    
39. Nel pannello **Aggiungi un criterio**, fare clic su **Crea**.
    
Ora si dispone di due criteri MAM, uno per i dispositivi iOS e uno per i dispositivi Android, e sono pronti per essere utilizzati con le impostazioni di testing per le app selezionate.
  
> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
  
## <a name="see-also"></a>Vedere anche

[Ambiente di sviluppo/test di Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Registrazione dei dispositivi iOS e Android nell'ambiente di sviluppo e test di Microsoft 365 Enterprise](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)

[Sicurezza (EMS) + mobilità aziendale](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


