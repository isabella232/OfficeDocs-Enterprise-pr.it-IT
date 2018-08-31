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
ms.openlocfilehash: 089b9771d0600f8c74bc7b4c30ff2a4931c93ae6
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915761"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a>Cloud App Security per l'ambiente di sviluppo/test di Office 365

 **Sintesi:** configurazione e dimostrazione di Office 365 Cloud App Security nell'ambiente di sviluppo/test di Office 365.
  
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

1. Accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) ed eseguire l'accesso alla sottoscrizione di prova di Office 365 con l'account di amministratore globale.
    
  - Se è in uso l'ambiente di sviluppo/test di Office 365 leggero, accedere dal computer locale.
    
  - Se si utilizza l'ambiente di sviluppo e di testing di Office 365 enterprise simulato, utilizzare il [portale Azure](https://portal.azure.com) per connettersi alla macchina virtuale CLIENT1 e quindi effettuare l'accesso da CLIENT1.
    
2. Dalla pagina principale del portale, fare clic su **Admin**.
    
3. Nel riquadro di spostamento sinistro fare clic su **Utenti > Utenti attivi**.
    
4. 	Fare clic sull'account **User 4**.
    
5. Nella pagina **User 4**, fare clic su **Modifica** per la riga **Ruoli**.
    
6. Nella pagina **Modifica ruoli utente**, fare clic su **Amministratore globale**, digitare **user4@contoso.com** nell'**indirizzo di posta elettronica alternativo**, quindi fare clic su **Salva**. Fare doppio clic su **Chiudi**.
    
7. 	Selezionare l'icona di avvio delle app in alto a sinistra e scegliere **Posta**.
    
8. Attendere 30 minuti. Si noti che non esiste alcun messaggio di posta elettronica in arrivo di notifica della modifica nel ruolo utente 4 come amministratore globale.
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a>Fase 3: abilitare Cloud App Security e creare un criterio

In questa procedura, viene abilitato Cloud App Security e viene creato un nuovo criterio per inviare messaggi di notifica all'account di amministratore globale per le modifiche dei ruoli degli account utente. Per questa procedura è necessario:
  
- Il nome e la password dell'account di amministratore globale della sottoscrizione di valutazione di Office 365.
    
- Il nome e la password dell'account di User 5 della sottoscrizione di valutazione di Office 365.
    
### <a name="enable-and-configure-cloud-app-security"></a>Abilitare e configurare Cloud App Security

1. Accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) ed eseguire l'accesso alla sottoscrizione di prova di Office 365 con l'account di amministratore globale.
    
2. Fare clic su tessera di **amministrazione** . Nella scheda di **interfaccia di amministrazione di Office** , fare clic su **Admin Center > sicurezza e conformità**.
    
3. Nel riquadro di spostamento a sinistra fare clic su **Avvisi > Gestisci gli avvisi avanzati**.
    
4. Nella pagina **Gestisci gli avvisi avanzati**, fare clic su **Attiva Office 365 Cloud App Security**, quindi fare clic su **Vai a Office 365 Cloud App Security**.
    
5. Nella nuova scheda **Dashboard**, fare clic su **Controllo > Criteri**.
    
6. Nella pagina **Criterio**, fare clic su **Crea criterio**, quindi fare clic su **Criteri attività**.
    
7. In **Nome criterio**, digitare **Attività amministrativa**.
    
8. In **Gravità del criterio**, fare clic su **Elevata**.
    
9. In **Categoria**, fare clic su **Account con privilegi**.
    
10. In **Crea filtri per il criterio**, in **Attività corrispondenti a tutti gli elementi seguenti**, fare clic su **Attività amministrativa**.
    
11. In **Avvisi**, fare clic su **Invia l'avviso come messaggio di posta elettronica**. In **A**, digitare l'indirizzo di posta elettronica dell'account di amministratore globale.
    
12. Nella parte inferiore della pagina fare clic su **Crea**.
    
## <a name="phase-4-show-cloud-app-security-in-action"></a>Fase 4: Visualizzare Cloud App Security in azione

In questa procedura, viene mostrato come Cloud App Security crea avvisi e invia notifiche tramite posta elettronica all'account di amministratore globale quando User 4 rende User 5 un amministratore della gestione di utenti e password.
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a>Mostrare la notifica tramite posta elettronica per una modifica di ruoli degli account utente

1. In alto a destra, fare clic sull'icona dell'utente e quindi fare clic su **Disconnetti**.
    
2. Accedere a [https://portal.office.com](https://portal.office.com).
    
3. Nella pagina di accesso di Office 365, fare clic su **Usa un altro account**.
    
4. Digitare il nome dell'account di User 4 e la relativa password, quindi fare clic su **Accedi**.
    
5. Se necessario, modificare la password dell'account User 4 e fare clic su **Aggiornare la password ed eseguire l'accesso**.
    
6. Nella pagina del portale di Office 365, fare clic su **Admin**.
    
7. Se necessario, fare clic su **Annulla** quando viene richiesto di aggiornare le informazioni di contatto di amministratore.
    
8. Dalla pagina principale del portale, fare clic su **Admin**.
    
9. Nel riquadro di spostamento sinistro fare clic su **Utenti > Utenti attivi**.
    
10. Fare clic sull'account **User 5**.
    
11. Nella pagina **User 5**, fare clic su **Modifica** per la riga **Ruoli**.
    
12. Nella pagina **Modifica ruoli utente**, fare clic su **Amministratore personalizzato**, selezionare **Amministratore password** e **Amministratore Gestione utenti**, digitare **user5@contoso.com** nell'**indirizzo di posta elettronica alternativo**, quindi fare clic su **Salva**. Fare doppio clic su **Chiudi**.
    
13. Fare clic sull'icona dell'utente in alto a destra, quindi su **Disconnetti**. 
    
14. Accedere a [https://portal.office.com](https://portal.office.com).
    
15. Nella pagina **Accesso a Office 365**, fare clic sul nome dell'account di amministratore globale.
    
16. Digitare la password e quindi fare clic su **Accedi**.
    
17. Dalla pagina principale del portale, fare clic su **Admin**.
    
18. Fare clic sul **protezione &amp; conformità** affiancate.
    
19. Nel riquadro di spostamento a sinistra fare clic su **Avvisi > Gestisci gli avvisi avanzati**.
    
20. Nella pagina **Gestisci gli avvisi avanzati**, fare clic su **Vai a Office 365 Cloud App Security**.
    
21. Nella nuova scheda **Dashboard**, notare i due nuovi avvisi per **Attività amministrativa**.
    
22. Dalla scheda **Microsoft Office Home**, fare clic su **Posta**. Attendere fino a 30 minuti.  
    
    Dovrebbero essere visualizzati due nuovi messaggi di posta elettronica nella Posta in arrivo con il titolo **Servizio di notifica di Microsoft Azure AD**. Un messaggio indica che l'account di User 5 è stato aggiunto al ruolo **Amministratore password** e l'altro messaggio indica che l'account di User 5 è stato aggiunto al ruolo **Amministratore utenti** (equivalente al ruolo Amministratore Gestione utenti nell'interfaccia di amministrazione di Office 365).
    
È ora possibile utilizzare questo ambiente per creare nuovi criteri e sperimentare ulteriormente sicurezza App Cloud di Office 365. Per i collegamenti agli articoli per la configurazione aggiuntivi, vedere [prepararsi per la protezione di Office 365 Cloud App](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) .
  
## <a name="see-also"></a>Vedere anche

[Guida al lab test (TLG) per adozione del cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)

[Panoramica della protezione App Cloud in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


