---
title: "Autenticazione a più fattori per l'ambiente di sviluppo/test di Office 365"
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
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: "Riepilogo: Configurare l'autenticazione a più fattori tramite messaggi di testo inviati a uno smartphone in un ambiente di sviluppo e testing di Office 365."
ms.openlocfilehash: 66b0fadd097e6df940754c28cd7b95549eb3a761
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a>Autenticazione a più fattori per l'ambiente di sviluppo/test di Office 365

 **Riepilogo:** Configurare l'autenticazione a più fattori tramite messaggi di testo inviati a uno smartphone in un ambiente di sviluppo e testing di Office 365.
  
Per un ulteriore livello di sicurezza per l'accesso alla propria sottoscrizione di Office 365, è possibile abilitare l'autenticazione a più fattori di Azure, che richiede più di nome utente e password per la verifica di un account. Con l'autenticazione a più fattori per Office 365, agli utenti viene richiesto di confermare telefonate, digitare un codice di verifica inviato in un messaggio di testo oppure specificare una password di un'app sullo smartphone dopo aver immesso correttamente la password. L'accesso è consentito solo dopo che un secondo fattore di autenticazione viene soddisfatto. 
  
In questo articolo viene illustrato come abilitare e testare l'autenticazione basata su messaggi di testo per uno specifico account di Office 365.
  
Le fasi di configurazione dell’autenticazione a più fattori per Office 365 in un ambiente di sviluppo e testing sono due:
  
1. Creare l'ambiente di sviluppo/testing di Office 365
    
2. Abilitare e testare l'autenticazione a più fattori per l'account User 2.
    
> [!TIP]
> Fare clic [qui]((http://aka.ms/catlgstack)) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: creare l'ambiente di sviluppo/test di Office 365 aziendale leggero o simulato

Se si desidera semplicemente testare l'autenticazione a più fattori con i requisiti minimi, seguire le istruzioni riportate nelle fasi 2 e 3 di [Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md).
  
Se si desidera testare l'autenticazione a più fattori in un'azienda simulata, seguire le istruzioni in [DirSync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Il test dell’autenticazione a più fattori non richiede l'ambiente di sviluppo/testing aziendale simulato, che include una rete Intranet simulata connessa a Internet e la sincronizzazione directory per una foresta di Windows Server AD. Questo test viene fornito qui come opzione in modo per consentire di testare l’autenticazione a più fattori e sperimentarla in un ambiente che rappresenta un'organizzazione tipica. 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Fase 2: Abilitare e testare l'autenticazione a più fattori per l'account User 2

Abilitare l'autenticazione a più fattori per l'account User 2 procedendo nel modo seguente:
  
1. Aprire un'istanza separata del browser, accedere al Portale di Office 365 ([(https://portal.office.com)]((https://portal.office.com))) e accedere alla sottoscrizione di valutazione di Office 365 con l'account di amministratore globale.
    
2. Dalla pagina principale del portale, fare clic su **Admin**.
    
3. Nel riquadro di spostamento sinistro fare clic su **Utenti > Utenti attivi**.
    
4. Nel riquadro Utenti attivi, fare clic su **Altro > Configura autenticazione a più fattori Azure**.
    
5. Nell'elenco, fare clic sull'account **User 2**.
    
6. Nella sezione **User 2**, sotto **Azioni rapide**, fare clic su **Abilita**.
    
7. Nella finestra di dialogo **Informazioni sull'abilitazione dell'autenticazione più fattori** fare clic su **Abilita Multi-Factor Auth**.
    
8. Nella finestra di dialogo **Aggiornamento completato** fare clic su **Chiudi**.
    
9. Nella scheda **Microsoft Office Home** fare clic sull'icona dell'account utente in alto a destra, quindi fare clic su **Disconnetti**.
    
10. Chiudere l'istanza del browser.
    
Completare la configurazione dell'account User 2 per utilizzare un messaggio di testo per la convalida e testarla con questa procedura:
  
1. Aprire una nuova istanza del browser.
    
2. Andare al portale di Office 365 ([(https://portal.office.com)]((https://portal.office.com))) ed eseguire l'accesso con l'account User 2 (user2@\<nome organizzazione>.onmicrosoft.com) e la password.
    
3. Dopo l'accesso, viene chiesto di configurare l'account per un'ulteriore convalida di sicurezza. Fare clic su **Configura ora**.
    
4. Nella pagina **Verifica aggiuntiva di sicurezza**:
    
  - Selezionare il paese o l'area geografica.
    
  - Digitare il numero di telefono dello smartphone che riceverà i messaggi di testo.
    
  - Selezionare **Invia un codice tramite messaggio di testo**.
    
5. Fare clic su **Contattami**.
    
6. Immettere il codice di verifica del messaggio di testo ricevuto sullo smartphone e quindi fare clic su **Verifica**.
    
7. Nella pagina **Passaggio 3: Mantenere le applicazioni esistenti**, annotare la password dell'app visualizzata per l'account User 2 in una posizione sicura e fare clic su **Fine**.
    
8. Tornare alla pagina di accesso, digitare la password per l'account User 2 e fare clic su **Accedi**.
    
9. Immettere il codice di verifica riportato nel messaggio di testo ricevuto sullo smartphone, quindi fare clic su **Accedi**.
    
10. Se è la prima volta che si accede con l'account User 2, viene richiesto di modificare la password. Digitare la password originale e una nuova password due volte, quindi fare clic su **Aggiornare la password ed eseguire l'accesso**. Annotare nome e password in una posizione sicura.
    
    Verrà visualizzato il portale di Office 365 per User 2.
    
## <a name="see-also"></a>Vedere anche

[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente di sviluppo/test della configurazione di base](base-configuration-dev-test-environment.md)
  
[Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)

[Pianificare l'autenticazione a più fattori per le distribuzioni di Office 365]((https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba))

