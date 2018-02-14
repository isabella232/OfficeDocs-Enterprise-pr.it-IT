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
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a>Cloud App Security per l'ambiente di sviluppo/test di Office 365

 **Riepilogo:** Configurare ed effettuare una dimostrazione di sicurezza di Office 365 Cloud App nell'ambiente di sviluppo e di testing di Office 365.
  
Protezione di Office 365 Cloud App, in precedenza noto come Office 365 Advanced Security Management, consente di creare i criteri che per monitorare e informano l'utente delle attività potenzialmente dannoso nella sottoscrizione a Office 365, in modo da poter analizzare e richiedere possibili azione di risoluzione dei problemi. Per ulteriori informazioni, vedere [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).
  
Con le istruzioni disponibili in questo articolo, è possibile abilitare e testare Cloud App Security nella sottoscrizione di valutazione di Office 365.
  
> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: creare l'ambiente di sviluppo/test di Office 365 aziendale leggero o simulato

Se si desidera testare Cloud App sicurezza in un modo semplice con i requisiti minimi, seguire le istruzioni in fasi 2 e 3 [dell'ambiente di sviluppo e di testing di Office 365](office-365-dev-test-environment.md).
  
Se si desidera testare Cloud App protezione in un'azienda simulata, seguire le istruzioni in [DirSync per l'ambiente di sviluppo e di testing di Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Il test di Cloud App Security non richiede l'ambiente di sviluppo/test aziendale simulato, che include una rete Intranet simulata connessa a Internet e la sincronizzazione della directory per una foresta di Windows Server AD. Qui viene fornito come un'opzione in modo da poter testare Cloud App Security e sperimentarlo in un ambiente che rappresenta un'organizzazione tipica. 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a>Fase 2: prima di abilitare Cloud App Security e creare un criterio

In questa procedura si dimostrano che prima di abilitare Cloud App sicurezza, la modifica ruolo dell'utente non fornisce alcuna notifica tramite posta elettronica all'amministratore globale.
  
### <a name="test-the-default-notification-behavior-of-office-365"></a>Testare il comportamento di notifica predefinito di Office 365

1. Accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) e accedere alla sottoscrizione di prova di Office 365 con l'account di amministratore globale.
    
  - Se è in uso l'ambiente di sviluppo/test di Office 365 leggero, accedere dal computer locale.
    
  - Se si utilizza l'ambiente di sviluppo e di testing di Office 365 enterprise simulato, utilizzare il [portale Azure](https://portal.azure.com) per connettersi alla macchina virtuale CLIENT1 e quindi effettuare l'accesso da CLIENT1.
    
2. Dalla pagina principale del portale, fare clic su **Admin**.
    
3. Nel riquadro di spostamento sinistro fare clic su **Utenti > Utenti attivi**.
    
4. Fare clic sull'account **utente 4** .
    
5. Nella pagina **utente 4** , fare clic su **Modifica** per la riga di **ruoli** .
    
6. Nella pagina **Modifica ruoli utente** fare clic su **amministratore globale**, digitare l' **indirizzo di posta elettronica alternativi** **user4@contoso.com** e quindi fare clic su **Salva**. Fare doppio clic su **Chiudi** .
    
7. Selezionare l'icona di avvio di app in alto a sinistra e scegliere **posta elettronica**.
    
8. Attendere 30 minuti. Si noti che non esiste alcun messaggio di posta elettronica in arrivo di notifica della modifica nel ruolo utente 4 come amministratore globale.
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a>Fase 3: abilitare Cloud App Security e creare un criterio

In questa procedura, viene abilitato Cloud App Security e viene creato un nuovo criterio per inviare messaggi di notifica all'account di amministratore globale per le modifiche dei ruoli degli account utente. Per questa procedura è necessario:
  
- Il nome e la password dell'account di amministratore globale della sottoscrizione di valutazione di Office 365.
    
- Il nome e la password dell'account di User 5 della sottoscrizione di valutazione di Office 365.
    
### <a name="enable-and-configure-cloud-app-security"></a>Abilitare e configurare Cloud App Security

1. Accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) e accedere alla sottoscrizione di prova di Office 365 con l'account di amministratore globale.
    
2. Fare clic sul **protezione &amp; conformità** affiancate.
    
3. Nel riquadro di spostamento sinistra fare clic su **avvisi > Gestisci avanzate avvisi**.
    
4. Nella pagina **Gestisci avvisi avanzate** fare clic **su Office 365 Cloud App protezione attiva**e quindi fare clic su **Vai alla protezione di Office 365 Cloud App**.
    
5. Nella scheda nuovo **Dashboard** , fare clic su **controllo > criteri**.
    
6. Nella pagina **criteri** fare clic su **Crea un criterio**e quindi fare clic su **criteri di attività**.
    
7. In **Nome criterio**digitare **attività amministrative**.
    
8. **Gravità criteri**, fare clic su **High**.
    
9. Nella **categoria**, fare clic su **account privilegiato**.
    
10. **Creare filtri per i criteri** **delle attività corrispondenti a tutte le condizioni seguenti**, fare clic **sull'attività amministrative**.
    
11. Negli **avvisi**, fare clic su **Invia avviso come messaggio di posta elettronica**. Nella casella **a**digitare l'indirizzo di posta elettronica dell'account di amministratore globale.
    
12. Nella parte inferiore della pagina, fare clic su **Crea**.
    
## <a name="phase-4-show-cloud-app-security-in-action"></a>Fase 4: Visualizzare Cloud App Security in azione

In questa procedura, viene mostrato come Cloud App Security crea avvisi e invia notifiche tramite posta elettronica all'account di amministratore globale quando User 4 rende User 5 un amministratore della gestione di utenti e password.
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a>Mostrare la notifica tramite posta elettronica per una modifica di ruoli degli account utente

1. In alto a destra, fare clic sull'icona utente e quindi fare clic su **Esci**.
    
2. Passare al [https://portal.office.com](https://portal.office.com).
    
3. Nella pagina di accesso di Office 365, fare clic su **utilizza un altro account**.
    
4. Digitare il nome dell'account utente 4 e la relativa password e quindi fare clic su **Accedi**.
    
5. Se necessario, modificare la password dell'account utente 4 e quindi fare clic su **Aggiorna password ed effettuare l'accesso**.
    
6. Nella pagina del portale di Office 365, fare clic su **amministratore**.
    
7. Se necessario, fare clic su **Annulla** quando viene richiesto di aggiornare le informazioni di contatto di amministrazione.
    
8. Dalla pagina principale del portale, fare clic su **Admin**.
    
9. Nel riquadro di spostamento sinistro fare clic su **Utenti > Utenti attivi**.
    
10. Fare clic sull'account **utente 5** .
    
11. Nella pagina **5 utente** fare clic su **Modifica** per la riga di **ruoli** .
    
12. Nella pagina **Modifica ruoli utente** fare clic su **amministratore personalizzato**, fare clic su **amministratore Gestione utenti**e **amministratore Password** , digitare l' **indirizzo di posta elettronica alternativi** **user5@contoso.com** e quindi fare clic su **Salvare**. Fare doppio clic su **Chiudi** .
    
13. Fare clic sull'icona utente in alto a destra e quindi fare clic su **Esci**. 
    
14. Passare al [https://portal.office.com](https://portal.office.com).
    
15. Scegliere il nome dell'account amministratore globale nella pagina **Office 365 accedere** .
    
16. Digitare la password e quindi fare clic su **Accedi**.
    
17. Dalla pagina principale del portale, fare clic su **Admin**.
    
18. Fare clic sul **protezione &amp; conformità** affiancate.
    
19. Nel riquadro di spostamento sinistra fare clic su **avvisi > Gestisci avanzate avvisi**.
    
20. Nella pagina **Gestisci avvisi avanzate** , fare clic su **Vai alla protezione di Office 365 Cloud App**.
    
21. Nella scheda nuovo **Dashboard** , osservare le due nuovi avvisi per **l'attività di amministrazione**.
    
22. Nella scheda **Home page di Microsoft Office** , fare clic su **posta elettronica**. Attendere fino a 30 minuti. 
    
    Dovrebbe essere visibile due nuovi messaggi di posta elettronica nella posta in arrivo con il titolo del **Servizio di notifica di Microsoft Azure Active Directory**. Un messaggio indica che l'account utente 5 è stato aggiunto al ruolo **Amministratore Password** e un altro messaggio indica che l'account utente 5 è stato aggiunto al ruolo **Amministratore utenti** (uguale al ruolo di amministratore Gestione utente nel Office 365 Admin center).
    
È ora possibile utilizzare questo ambiente per creare nuovi criteri e sperimentare ulteriormente sicurezza App Cloud di Office 365. Per i collegamenti agli articoli per la configurazione aggiuntivi, vedere [prepararsi per la protezione di Office 365 Cloud App](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) .
  
## <a name="see-also"></a>Vedere anche

[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)

[Panoramica della protezione App Cloud in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


