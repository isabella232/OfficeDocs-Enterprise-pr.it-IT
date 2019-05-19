---
title: Advanced eDiscovery per l'ambiente di sviluppo/test di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: "Riepilogo: configurazione e dimostrazione di Office 365 Advanced eDiscovery con dati di esempio nell'ambiente di sviluppo/test di Office 365."
ms.openlocfilehash: dc783672f8f667e424ad738d8eb9091732537ebe
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162409"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>Advanced eDiscovery per l'ambiente di sviluppo/test di Office 365

 **Riepilogo:** configurazione e dimostrazione di Office 365 Advanced eDiscovery con dati di esempio nell'ambiente di sviluppo/test di Office 365.
  
Office 365 Advanced eDiscovery consente di trovare e analizzare rapidamente le informazioni rilevanti tra i dati archiviati in Office 365, inclusi i messaggi di posta elettronica e i documenti. Ciò consente di ridurre notevolmente la quantità necessaria di tempo e di spese, in particolare nelle situazioni di controversie legali. Per ulteriori informazioni, vedere [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).
  
Con le istruzioni disponibili in questo articolo, è possibile creare un insieme limitato di dati per una controversia fittizia relativa a un contratto e analizzarli con Advanced eDiscovery.
  
> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli nella serie di guide dei lab di test di Office 365.
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Fase 1: creare l'ambiente di sviluppo/test di Office 365

Se si desidera semplicemente testare Advanced eDiscovery con i requisiti minimi, seguire le istruzioni riportate nella fase 2 e nella fase 3 dell' [ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md).
  
Se si desidera testare Advanced eDiscovery in un'azienda simulata, seguire le istruzioni in [dirsync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Testing Advanced eDiscovery non richiede l'ambiente aziendale simulato, che include una rete Intranet simulata connessa a Internet e la sincronizzazione della directory per una foresta di servizi di dominio Active Directory (AD DS). Viene fornito come opzione in modo che sia possibile eseguire test e sperimentazione in un ambiente che rappresenta un'organizzazione tipica. 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>Fase 2: creare dati di esempio per Advanced eDiscovery

In questa procedura, è possibile creare messaggi di posta elettronica che in seguito verranno analizzati in un caso di Advanced eDiscovery.
  
1. Aprire Internet Explorer e accedere all'account [https://outlook.com](https://outlook.com) di Outlook creato nella fase 2 dell'[ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md).
    
  - Se è in uso l'ambiente di sviluppo/test leggero, aprire una sessione privata di Internet Explorer e accedere dal computer locale.
    
  - Se si utilizza l'ambiente di sviluppo/testing dell'organizzazione simulata, utilizzare il portale[https://portal.azure.com](https://portal.azure.com)di Azure () per connettersi alla macchina virtuale CLIENT1 e quindi eseguire l'accesso da CLIENT1.
    
2. Nella scheda **Posta di Outlook**, fare clic su **Nuovo**.
    
3. In **a**, digitare l'indirizzo di posta elettronica dell'account di USER6 della sottoscrizione di valutazione ( **USER6 @.**<organization name> **. onmicrosoft.com**).
    
4. Per l'oggetto, digitare **Messaggio di posta elettronica di prova 1**.
    
5. Nel corpo del messaggio, digitare **Bozza contratto Tailspin**, quindi fare clic su **Invia**.
    
6. Nella scheda **Posta di Outlook**, fare clic su **Nuovo**.
    
7. In **A**, digitare l'indirizzo di posta elettronica dell'account di User6 della sottoscrizione di valutazione.
    
8. Per l'oggetto, digitare **Messaggio di posta elettronica di prova 2**.
    
9. Nel corpo del messaggio, digitare **Riunione pranzo Tailspin**, quindi fare clic su **Invia**.
    
10. Nella scheda **Posta di Outlook**, fare clic su **Nuovo**.
    
11. In **A**, digitare l'indirizzo di posta elettronica dell'account di User6 della sottoscrizione di valutazione.
    
12. Per l'oggetto, digitare **Messaggio di posta elettronica di prova 3**.
    
13. Nel corpo del messaggio, digitare **Divergenze sul contratto Tailspin**, quindi fare clic su **Invia**.
    
14. Fare clic sull'icona dell'utente nell'angolo in alto a destra, quindi su **Disconnetti**.
    
15. Aprire una nuova scheda e accedere al portale di Office 365 ([https://www.office.com](https://www.office.com)) con il nome e la password dell'account USER6 della sottoscrizione di valutazione.
    
16. Nella scheda **Portale di Office 365**, fare clic su **Posta**.
    
17. Nella scheda **mail-USER6-Outlook** verificare che USER6 abbia ricevuto tutti e tre i messaggi dall'account di posta elettronica di Outlook.
    
18. Tornare alla **scheda del portale di Office 365** per User6.
    
19. Fare clic sull'icona dell'utente nell'angolo in alto a destra, quindi su **Disconnetti.**
    
In questa procedura, è possibile creare due documenti Word che in seguito verranno analizzati in un caso di Advanced eDiscovery.
  
1. Nella pagina **Office**, fare click su **Accedi,** effettuare l'accesso con le credenziali dell'account di amministratore globale.
    
2. In una nuova scheda, accedere all'URL del sito di SharePoint di produzione: **https://** <fictional organization name> **. SharePoint.com/sites/Production**
    
3. Nella scheda **Raccolta siti di produzione**, in **Documenti**, fare clic su **Nuovo > Documento Word**.
    
4. Nella pagina **Word Online**, digitare **Bozza contratto Tailspin**, attendere finché non compare **Salvato** nel titolo, quindi chiudere la scheda della pagina **Word Online**.
    
5. Nella scheda **Raccolta siti di produzione**, in **Documenti**, fare clic su **Nuovo > Documento Word**.
    
6. 	Nella scheda **Word Online**, digitare **Note su divergenze relative al contratto Tailspin**, attendere finché non compare **Salvato** nel titolo, quindi chiudere la scheda **Word Online**.
    
7. Nella scheda **Raccolta siti di produzione**, viene visualizzato **Documento** e **Documento1** nell'elenco dei documenti.
    
8. Chiudere la scheda **Raccolta siti di produzione**.
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>Fase 3: usare Advanced eDiscovery per una controversia legale

Sfortunatamente, una controversia relativa al contratto tra l'organizzazione e Tailspin Toys è giunta a un'azione legale. In questa procedura, si crea e configura un caso avanzato di eDiscovery per cercare e analizzare la posta elettronica e i documenti che contengono il testo "contratto Tilt".
  
La procedura per l'uso di Advanced eDiscovery è la seguente:
  
- Creare una ricerca nel centro sicurezza &amp; e conformità, analizzarne i risultati e quindi preparare i risultati per Advanced eDiscovery.
    
- Creare e configurare un caso di Advanced eDiscovery e analizzare i risultati della ricerca.
    
In questa procedura, è possibile creare una ricerca nel centro &amp; sicurezza e conformità per "contratto Tilt", esaminare i risultati e quindi preparare i risultati per Advanced eDiscovery.
  
1. Dalla scheda **Portale di Office 365**, fare clic su **Admin**.
    
2. Nella barra di spostamento a sinistra della scheda dell'interfaccia di amministrazione, fare clic su **Interfacce di amministrazione > Conformità**.
    
3. Nella scheda **conformità &amp; di sicurezza** fare clic su **autorizzazioni**.
    
4. Nell'elenco **Autorizzazioni**, fare doppio click su **Gestione organizzazione**.
    
5. Nella finestra **Gruppo di ruoli**, in **Membri** fare clic sul segno più.
    
6. Nella finestra **Seleziona membri**, fare doppio clic sul nome dell'account di amministratore, quindi fare clic su **OK**.
    
7. Nella finestra **Gruppo di ruoli**, fare clic su **Salva**.
    
8. Nell'elenco **Autorizzazioni**, fare doppio clic su **Responsabile di eDiscovery**.
    
9. Nella finestra **Gruppo di ruoli**, in **Amministratore di eDiscovery**, fare clic sull'icona più.
    
10. Nella finestra **Seleziona membri**, fare doppio clic sul nome dell'account di amministratore, quindi fare clic su **OK**.
    
11. Nella finestra **Gruppo di ruoli**, fare clic su **Salva**.
    
12. Nel riquadro di spostamento a sinistra, fare clic su search ** &amp; Investigation > content search**.
    
13. Fare clic sull'icona più per aggiungere una ricerca.
    
14. Nella finestra **Nuova ricerca**, digitare **Ricerca contratto Tailspin** in **Nome**.
    
15. In **Dove vuoi effettuare la ricerca?**, fare clic su **Cerca ovunque,** selezionare **Exchange**, **SharePoint** e **Cartelle pubbliche**, quindi fare clic su **Avanti.**
    
16. In **Cosa vuoi cercare?**, digitare **Contratto Tailspin**, quindi fare clic su **Cerca**.
    
17. Nell'elenco delle ricerche, fare clic sul nome **Ricerca contratto Tailspin**.
    
18. Nel riquadro **Ricerca contratto Tailspin**, fare clic su **Anteprima risultati della ricerca** in **Risultati**. Verrà visualizzata una finestra in cui sono elencati i due documenti nel sito di SharePoint di produzione ( **documento** e **document1**) e i messaggi di posta elettronica di **test 1** e **test email 3** a USER6. Chiudere la finestra.
    
19. Nel riquadro **Ricerca contenuto**, in **Analizza i risultati con Advanced eDiscovery**, fare clic su **Anteprima risultati per analisi**.
    
20. Nella finestra **Prepara i risultati della ricerca per ricerca contratto Tailspin**, fare clic su **Prepara** e attendere il completamento dell'operazione.
    
In questa procedura, è possibile creare un nuovo caso di Advanced eDiscovery e analizzare i risultati della ricerca relativa al contratto Tailspin.
  
1. Nel riquadro di spostamento a sinistra, fare clic su **eDiscovery** in **analisi ricerca &amp; **.
    
2. Nel riquadro **eDiscovery**, fare clic su **Vai ad Advanced eDiscovery**.
    
3. Nella scheda **Advanced eDiscovery**, fare clic sull'icona più per aggiungere un nuovo caso.
    
4. 	Nel riquadro **Aggiungi caso**, digitare **Controversia relativa al contratto Tailspin** in **Nome**, quindi fare clic su **OK**. Attendere che il caso venga creato.
    
5. Fare doppio clic sul caso **Controversia relativa al contratto Tailspin** nell'elenco. 
    
6. Nell'elenco **contenitore** fare clic sul contenitore di ricerca per il **contratto Tilt** , quindi fare clic su **elabora**. Attendere il completamento dell'elaborazione.
    
7. Quando nella parte inferiore della finestra viene visualizzato **Elaborazione completata**, fare clic su **Riepilogo elaborazione** nella barra di spostamento a sinistra per visualizzare un riepilogo.
    
8. Nella barra di spostamento superiore, fare clic su **Analizza**.
    
9. Nella pagina **Configurazione**, in **Temi** digitare **3** in **Numero massimo di temi**.
    
10. Fare clic su **Analizza** e attendere il completamento dell'analisi. Viene visualizzata una serie di grafici a torta con l'analisi della popolazione target, dei documenti, dei messaggi di posta elettronica e degli allegati. Per ulteriori informazioni, vedere [viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).
    
È ora possibile usare questo ambiente per creare nuovi contenuti, nuove ricerche e casi e sperimentare ulteriormente Advanced eDiscovery in Office 365.
  
## <a name="see-also"></a>Vedere anche

[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente di sviluppo/test della configurazione di base](base-configuration-dev-test-environment.md)
  
[Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
  
[DirSync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)

[Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


