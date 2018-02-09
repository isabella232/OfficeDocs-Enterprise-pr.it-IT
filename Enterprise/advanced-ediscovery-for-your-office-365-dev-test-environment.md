---
title: Advanced eDiscovery per l'ambiente di sviluppo/test di Office 365
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
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: 'Riepilogo: Configurare e illustrare eDiscovery avanzate di Office 365 con dati di esempio nell''ambiente di sviluppo e di testing di Office 365.'
ms.openlocfilehash: c55a466f05eba4e9f06ce2930dfc7c762d7fceae
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>Advanced eDiscovery per l'ambiente di sviluppo/test di Office 365

 **Riepilogo:** Configurare e dimostrare l'utilizzo di Office 365 avanzate eDiscovery con dati di esempio nell'ambiente di sviluppo e di testing di Office 365.
  
Office 365 eDiscovery avanzate consente di trovare rapidamente e analizzare le informazioni pertinenti attraverso i dati archiviati in Office 365, inclusi documenti e posta elettronica. Questo può salvare un'elevata quantità di tempo e denaro, soprattutto nelle situazioni di conservazione per controversia. Per ulteriori informazioni, vedere [eDiscovery avanzate di Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).
  
Con le istruzioni disponibili in questo articolo, è possibile creare un insieme limitato di dati per una controversia fittizia relativa a un contratto e analizzarli con Advanced eDiscovery.
  
> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Fase 1: creare l'ambiente di sviluppo/test di Office 365

Se si desidera testare avanzate eDiscovery in un modo semplice con i requisiti minimi, seguire le istruzioni nella fase 2 e la fase 3 [dell'ambiente di sviluppo e di testing di Office 365](office-365-dev-test-environment.md).
  
Se si desidera testare avanzate eDiscovery in un'azienda simulata, seguire le istruzioni in [DirSync per l'ambiente di sviluppo e di testing di Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Test eDiscovery avanzate non sono necessari nell'ambiente aziendale simulato, che include una rete intranet simulata connessione a Internet e la sincronizzazione delle directory per una foresta Windows Server Active Directory. Viene fornito qui come un'opzione in modo che è possibile eseguire il test e la sperimentazione in un ambiente che rappresenta una tipica organizzazione. 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>Fase 2: creare dati di esempio per Advanced eDiscovery

In questa procedura, è possibile creare messaggi di posta elettronica che in seguito verranno analizzati in un caso di Advanced eDiscovery.
  
1. Aprire Internet Explorer e accedere a [https://outlook.com](https://outlook.com) all'account di Outlook creata nella fase 2[dell'ambiente di sviluppo e di testing di Office 365](office-365-dev-test-environment.md).
    
  - Se è in uso l'ambiente di sviluppo/test leggero, aprire una sessione privata di Internet Explorer e accedere dal computer locale.
    
  - Se si utilizza l'ambiente di sviluppo e di testing enterprise simulato, utilizzare il portale di Azure ([https://portal.azure.com](https://portal.azure.com)) per connettersi alla macchina virtuale CLIENT1 e quindi effettuare l'accesso da CLIENT1.
    
2. Nella scheda **Posta elettronica di Outlook** fare clic su **Nuovo**.
    
3. Nella casella **a**digitare l'indirizzo di posta elettronica dell'account User6 dell'abbonamento valutazione ( **user6 @.** <organization name> **. onmicrosoft.com**).
    
4. Per l'oggetto, digitare **1 e-mail di prova**.
    
5. Nel corpo, digitare **bozza contratto Tailspin**e quindi fare clic su **Invia**.
    
6. Nella scheda **Posta elettronica di Outlook** fare clic su **Nuovo**.
    
7. Nella casella **a**digitare l'indirizzo di posta elettronica dell'account User6 della sottoscrizione di prova.
    
8. Per l'oggetto, digitare **Test e-mail 2**.
    
9. Nel corpo, digitare **convocazione di riunione pranzo Tailspin**e quindi fare clic su **Invia**.
    
10. Nella scheda **Posta elettronica di Outlook** fare clic su **Nuovo**.
    
11. Nella casella **a**digitare l'indirizzo di posta elettronica dell'account User6 della sottoscrizione di prova.
    
12. Per l'oggetto, digitare **3 e-mail di prova**.
    
13. Nel corpo, digitare **disaccordo contratto Tailspin**e quindi fare clic su **Invia**.
    
14. Fare clic sull'icona utente nell'angolo superiore destro e quindi fare clic su **Esci**.
    
15. Aprire una nuova scheda e accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) con il nome dell'account e la password dell'account User6 della sottoscrizione di prova.
    
16. Nella scheda **portale di Office 365** , fare clic su **posta elettronica**.
    
17. Nella scheda **- User6 - posta elettronica Outlook** , verificare che User6 ricevuto tutti i messaggi di posta tre elettronica dall'account di posta elettronica di Outlook.
    
18. Passare alla **scheda portale Office 365** per User6.
    
19. Fare clic sull'icona utente nell'angolo superiore destro e quindi fare clic su **disconnettersi.**
    
In questa procedura, è possibile creare due documenti Word che in seguito verranno analizzati in un caso di Advanced eDiscovery.
  
1. Nella pagina **Office** , fare clic su **Accedi,** accedere con le credenziali dell'account di amministratore globale.
    
2. Accedere all'URL del sito di SharePoint di produzione in una nuova scheda: **https://** <fictional organization name> **.sharepoint.com/sites/production**
    
3. Nella scheda **raccolta siti di produzione** , in **documenti**, fare clic su **Nuovo > documento di Word**.
    
4. Nella pagina **Word Online** digitare **Tailspin bozza di contratto**, attendere finché non viene visualizzato **Saved** del titolo e quindi chiudere la scheda pagina **Word Online** .
    
5. Nella scheda **raccolta siti di produzione** , in **documenti**, fare clic su **Nuovo > documento di Word**.
    
6. Nella scheda **Word Online** digitare **Tailspin contratto controversia note**, attendere finché non viene visualizzato **Saved** del titolo e quindi chiudere la scheda **Word Online** .
    
7. Nella scheda **raccolta siti di produzione** , si dovrebbero essere visualizzati **documento** e **Documento1** nell'elenco dei documenti.
    
8. Chiudere la scheda **raccolta siti di produzione** .
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>Fase 3: Utilizzare eDiscovery avanzate per una controversia legale

Purtroppo una controversia contratto tra l'organizzazione e Tailspin Toys ha raggiunto il punto di un'azione legale. In questa procedura, creare e configurare un caso eDiscovery avanzate per cercare e analizzare il messaggio di posta elettronica e documenti che contengono il testo "Contratto Tailspin".
  
La procedura per l'uso di Advanced eDiscovery è la seguente:
  
- Creare una ricerca per la protezione &amp; centro conformità, analizzare i risultati e quindi preparare i risultati eDiscovery avanzate.
    
- Creare e configurare un caso di Advanced eDiscovery e analizzare i risultati della ricerca.
    
In questa procedura si crea una ricerca per la protezione &amp; conformità center per "Contratto Tailspin", consultare i risultati e quindi preparare i risultati eDiscovery avanzate.
  
1. Nella scheda **portale di Office 365** , fare clic su **amministratore**.
    
2. Nel riquadro di spostamento sinistro della scheda centro di amministrazione, fare clic su **Admin Center > conformità**.
    
3. Nella **protezione &amp; conformità** fare clic su **autorizzazioni**.
    
4. Nella casella **autorizzazioni** fare doppio clic su **Gestione organizzazione**.
    
5. Nella finestra **Gruppo di ruoli** in **membri**, fare clic sul segno più.
    
6. Nella finestra **Selezione membri** , fare doppio clic sul nome dell'account di amministratore e quindi fare clic su **OK**.
    
7. Nella finestra di **Gruppo di ruoli** , fare clic su **Salva**.
    
8. Nella casella **autorizzazioni** fare doppio clic su **eDiscovery Manager**.
    
9. Nella finestra del **Gruppo di ruoli** **amministratore di eDiscovery**, fare clic sull'icona più.
    
10. Nella finestra **Selezione membri** , fare doppio clic sul nome dell'account di amministratore e quindi fare clic su **OK**.
    
11. Nella finestra di **Gruppo di ruoli** , fare clic su **Salva**.
    
12. Nel riquadro di spostamento sinistra fare clic su **ricerca &amp; indagini > ricerca contenuto**.
    
13. Fare clic sull'icona più per aggiungere una ricerca.
    
14. Nella finestra della **nuova ricerca** , digitare **ricerca contratto Tailspin** nella **casella Nome**.
    
15. In **dove si desidera di aspetto?**, fare clic su **ovunque, di ricerca** selezionare **Exchange**, **SharePoint**e **Le cartelle pubbliche**e quindi fare clic su **successivo.**
    
16. In **scegliere un'opzione di cercare?**digitare **contratto Tailspin**, fare clic su **Cerca**.
    
17. Nell'elenco delle ricerche, fare clic sul nome di **ricerca contratto Tailspin** .
    
18. Nel riquadro **Tailspin contratto ricerca** , fare clic su **Anteprima risultati di ricerca** **nell'area risultati della**. Verrà visualizzata una finestra che elenca i due documenti nel sito di SharePoint di produzione ( **documenti** e **Documento1**) e sui messaggi di **posta elettronica Test 1** e **3 e-mail di prova** a User6. Chiudere la finestra.
    
19. Nel riquadro di **ricerca del contenuto** , **i risultati di analisi con eDiscovery avanzate**, fare clic su **Anteprima risultati per l'analisi**.
    
20. Nella finestra **dei risultati di preparare la ricerca per la ricerca contratto Tailspin** fare clic su **Prepara** e attendere che venga completato.
    
In questa procedura, è possibile creare un nuovo caso di Advanced eDiscovery e analizzare i risultati della ricerca relativa al contratto Tailspin.
  
1. Nel riquadro di spostamento sinistra fare clic su **eDiscovery** in **ricerca &amp; indagini**.
    
2. Nel riquadro di **eDiscovery** , fare clic su **Vai a eDiscovery avanzate**.
    
3. Nella scheda **Impostazioni avanzate di eDiscovery** , fare clic sull'icona del segno più per aggiungere un nuovo caso.
    
4. Nel riquadro **Add case** digitare **controversia contratto Tailspin** nella **casella Nome**e quindi fare clic su **OK**. Attendere il caso da creare.
    
5. Fare doppio clic sul caso di **controversia contratto Tailspin** nell'elenco.
    
6. Nell'elenco del **contenitore** , fare clic sul contenitore **ricerca contratto Tailspin** e quindi fare clic su **processo**. Attendere il completamento dell'elaborazione.
    
7. Quando si **processo: completato** viene visualizzata nella parte inferiore della finestra, fare clic su **processo riepilogo** nel riquadro di spostamento sinistro per visualizzare un riepilogo.
    
8. Nel riquadro di spostamento superiore fare clic su **Analyze**.
    
9. Nella pagina **installazione** con **i temi**, digitare **3** **numero Max di temi**.
    
10. Fare clic su **Analyze** e attendere che l'analisi per il completamento. Dovrebbe essere visibile una serie di grafici a torta con analisi della popolazione target, documenti, messaggi di posta elettronica e allegati. Per ulteriori informazioni, vedere [visualizzazione di analizzare i risultati](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).
    
È ora possibile usare questo ambiente per creare nuovi contenuti, nuove ricerche e casi e sperimentare ulteriormente Advanced eDiscovery in Office 365.
  
## <a name="see-also"></a>Vedere anche

[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente di sviluppo/test della configurazione di base](base-configuration-dev-test-environment.md)
  
[Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
  
[DirSync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Cloud App Security per l'ambiente di sviluppo/test di Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)

[EDiscovery avanzate di Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


