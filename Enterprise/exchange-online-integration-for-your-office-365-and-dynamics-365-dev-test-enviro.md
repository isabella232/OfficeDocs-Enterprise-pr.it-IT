---
title: Integrazione di Exchange Online per il proprio ambiente di sviluppo/test di Office 365 e Dynamics 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: "Riepilogo: Usare questa Guida del laboratorio di testing per attivare l'integrazione di Dynamics 365 per Exchange Online nella sottoscrizione di valutazione di Office 365."
ms.openlocfilehash: 320a59043ab2a8810f9bfc03fdcf896241ec6b20
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915501"
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a>Integrazione di Exchange Online per il proprio ambiente di sviluppo/test di Office 365 e Dynamics 365

 **Riepilogo:** Usare questa Guida del laboratorio di testing per attivare l'integrazione di Dynamics 365 per Exchange Online nella sottoscrizione di valutazione di Office 365.
  
Per un miglior utilizzo di Microsoft Dynamics 365 occorre memorizzare tutte le comunicazioni con il cliente in un'unica posizione, in modo che tutti gli utenti dotati delle autorizzazioni appropriate possono vedere tutti i record del cliente pertinente. Ad esempio, visualizzare tutti i messaggi associati a un particolare contatto, account, opportunità o pratica.
  
Per archiviare posta elettronica e altri record di messaggistica in Dynamics 365, è necessario sincronizzare il sistema di posta elettronica con Dynamics 365. La sincronizzazione sul lato server è il metodo di scelta per la sincronizzazione della posta elettronica.
  
Usare questa Guida del laboratorio di testing per configurare e dimostrare come Exchange Online e il client Outlook Online possono sfruttare le informazioni archiviate in Dynamics 365. 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a>Fase 1: Creare l'ambiente di sviluppo/test di Office 365 e Dynamics 365

Seguire le istruzioni riportate in [Ambiente di sviluppo/test di Office 365 e Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md) per creare una versione aziendale leggera o simulata di un ambiente di sviluppo/test di Office 365 e Dynamics 365.
  
> [!NOTE]
> La configurazione riportata in questo articolo non richiede l'ambiente di sviluppo/test aziendale simulato, che include una rete Intranet simulata connessa a Internet e la sincronizzazione della directory per una foresta di Windows Server Active Directory (AD). Qui viene fornito come un'opzione in modo da poter sperimentare Office 365 e Dynamics 365 in un ambiente che rappresenta un'organizzazione tipica 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a>Fase 2: Configurare e dimostrare l0integrazione di Dynamics 365 in Exchange Online

Seguire questi passaggi per configurare la cassetta postale dell'amministratore globale per l'integrazione di Dynamics 365 ed Exchange Online:
  
1. Mediante una sessione di private del browser, accedere a [http://portal.office.com](http://portal.office.com) e accedere utilizzando l'account amministratore globale di Office 365.
    
2. Nella pagina **Microsoft Office Home**, fare clic sulla sezione **Posta di Outlook**.
    
3. Nella nuova scheda **Posta di Outlook** nel browser, fare clic su **Nuovo** e notare come l'angolo inferiore del riquadro sotto la casella per digitare un messaggio contiene un'icona per modelli personali.
    
     ![Un nuovo messaggio e-mail vuoto e privo d'integrazione con Dynamics 365.](media/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. Fare clic su **Ignora** e lasciare la scheda **Posta di Outlook** aperta.
    
5. Fare clic sulla scheda **Microsoft Office Home** visualizzata nel browser, quindi fare clic sulla sezione **Amministratore**.
    
6. Nella barra di spostamento a sinistra della scheda **Interfaccia di amministrazione di Office**, fare clic su **Interfacce di amministrazione > Dynamics 365**.
    
7. Nella nuova scheda **365 Dynamics** visualizzata nel browser, nell'elenco delle istanze di Dynamics 365 fare clic su **Apri**.
    
8. Nella nuova scheda **Amministrazione** visualizzata nel browser, nella barra di spostamento, fare clic sulla freccia in giù accanto a **Impostazioni**, quindi fare clic su **Configurazione e-mail** in **Sistema**.
    
9.  Nella pagina **Configurazione e-mail**, fare clic su **Impostazioni di configurazione e-mail**.
    
10. Nella scheda **E-mail** nella finestra di dialogo **Impostazioni di sistema**, modificare **Appuntamenti, contatti e attività** in **Sincronizzazione lato Server**, quindi fare clic su **OK**.
    
11. Nella pagina **Configurazione e-mail**, fare clic su **Cassette postali**.
    
12. Selezionare il nome di un amministratore globale di Office 365 nella colonna sinistra con segno di spunta, fare clic su **Applica impostazioni e-mail predefinite** nella barra degli strumenti, quindi fare clic su **OK**.
    
13. Fare clic su **Approva indirizzo e-mail** nella barra degli strumenti, quindi fare clic su **OK**.
    
14. Selezionare il nome di un amministratore globale di Office 365 nella colonna sinistra con segno di spunta, fare clic su **Verifica e abilita cassette postali** nella barra degli strumenti, quindi fare clic su **OK**.
    
15. Fare clic sulla scheda **Posta di Outlook** e verificare che l'amministratore globale abbia ricevuto un messaggio di prova.
    
16. Tornare alla scheda **Cassette postali Cassette postali personali attive** nel browser e aggiornare la pagina. Le colonne **Stato messaggi e-mail in arrivo** e **Stato messaggi e-mail in uscita** devono essere impostate su **Operazione riuscita** per il nome dell'account amministratore globale. Tenere presente che possono essere necessari fino a 15 minuti per completare entrambi i test.
    
Seguire questi passaggi per installare l'App Dynamics 365 per Outlook e dimostrare le funzionalità di Dynamics 365 all'interno della cassetta postale dell'amministratore globale:
  
1. Nella scheda **Cassette postali Cassette postali personali attive** visualizzata nel browser, fare clic sulla freccia in giù accanto a **Impostazioni**, quindi fare clic su **App Dynamics 365 per Outlook** in **Sistema**.
    
2. Nella pagina **Introduzione all'app Microsoft Dynamics 365 per Outlook** pagina, fare clic sul nome dell'amministratore globale, quindi fare clic su **Aggiungi app a Outlook**. La colonna **Stato** cambierà in **In sospeso**.
    
3. Aggiornare la pagina finché non assume lo stato di **Aggiunto a Outlook**. Tenere presente che possono essere necessari fino a 15 minuti per completare la configurazione.
    
4. Fare clic sulla scheda **Posta di Outlook** visualizzata nel browser, quindi chiuderla.
    
5. Fare clic sulla scheda **Microsoft Office Home** visualizzata nel browser, quindi fare clic sulla sezione **Posta di Outlook**.
    
6. Nella nuova scheda **Posta di Outlook**, fare clic su **Nuovo**. Tenere presente che l'angolo inferiore del riquadro sotto la casella per digitare un messaggio ora contiene un'icona per Dynamics 365.
    
     ![Un nuovo messaggio e-mail vuoto dotato d'integrazione con Dynamics 365; visualizzazione della nuova icona.](media/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. Fare clic sull'icona Dynamics 365. Verrà visualizzato un riquadro **Dynamics 365**, da cui è possibile tenere traccia della posta elettronica e accedere a modelli, documentazione di vendita o articoli.
    
8. Nel campo **A** del messaggio di posta elettronica, digitare **alex.y.wu@outlook.com**, quindi fare clic su **Riprova** nel riquadro **Dynamics 365**. Verrà visualizzata una sezione **Destinatari** nel riquadro **Dynamics 365** con le informazioni su Alex Wu, un contatto dall'applicazione vendita fornito con i dati di esempio per la sottoscrizione di valutazione.
    
     ![Riquadro informazioni di Dynamics 365 relativo a un contatto di vendita memorizzato in Dynamics 365.](media/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. Fare clic su **Ignora**.

> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
    
## <a name="see-also"></a>Vedere anche

[Ambiente di sviluppo/test di Office 365 e Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md)
  
[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente di sviluppo/test della configurazione di base](base-configuration-dev-test-environment.md)
  
[Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
  
[DirSync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md)

[Gestione della sottoscrizione per Dynamics 365 (Online)](https://technet.microsoft.com/library/jj679903.aspx)
  
[Amministrare Dynamics 365](https://technet.microsoft.com/library/dn531101.aspx)


