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
description: "Riepilogo: configurazione e dimostrazione di Office 365 Advanced eDiscovery con dati di esempio nell'ambiente di sviluppo/test di Office 365."
ms.openlocfilehash: c93900e07b8b9adbe0f1120eca77019b9dcc1eda
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897509"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>Advanced eDiscovery per l'ambiente di sviluppo/test di Office 365

 **Riepilogo:** configurazione e dimostrazione di Office 365 Advanced eDiscovery con dati di esempio nell'ambiente di sviluppo/test di Office 365.
  
Office 365 eDiscovery avanzate consente di trovare rapidamente e analizzare le informazioni pertinenti attraverso i dati archiviati in Office 365, inclusi documenti e posta elettronica. Questo può salvare un'elevata quantità di tempo e denaro, soprattutto nelle situazioni di conservazione per controversia. Per ulteriori informazioni, vedere [eDiscovery avanzate di Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).
  
Con le istruzioni disponibili in questo articolo, è possibile creare un insieme limitato di dati per una controversia fittizia relativa a un contratto e analizzarli con Advanced eDiscovery.
  
> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi al Test Lab Guide di One Microsoft Cloud.
  
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
    
2. Nella scheda **Posta di Outlook**, fare clic su **Nuovo**.
    
3. Nella casella **a**digitare l'indirizzo di posta elettronica dell'account User6 dell'abbonamento valutazione ( **user6 @.** <organization name> **. onmicrosoft.com**).
    
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
    
14. Fare clic sull'icona utente nell'angolo superiore destro e quindi fare clic su **Esci**.
    
15. Aprire una nuova scheda e accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) con il nome dell'account e la password dell'account User6 della sottoscrizione di prova.
    
16. Nella scheda **Portale di Office 365**, fare clic su **Posta**.
    
17. Nella scheda **- User6 - posta elettronica Outlook** , verificare che User6 ricevuto tutti i messaggi di posta tre elettronica dall'account di posta elettronica di Outlook.
    
18. Tornare alla **scheda del portale di Office 365** per User6.
    
19. Fare clic sull'icona dell'utente nell'angolo in alto a destra, quindi su **Disconnetti.**
    
In questa procedura, è possibile creare due documenti Word che in seguito verranno analizzati in un caso di Advanced eDiscovery.
  
1. Nella pagina **Office**, fare click su **Accedi,** effettuare l'accesso con le credenziali dell'account di amministratore globale.
    
2. Accedere all'URL del sito di SharePoint di produzione in una nuova scheda: **https://** <fictional organization name> **.sharepoint.com/sites/production**
    
3. Nella scheda **Raccolta siti di produzione**, in **Documenti**, fare clic su **Nuovo > Documento Word**.
    
4. Nella pagina **Word Online**, digitare **Bozza contratto Tailspin**, attendere finché non compare **Salvato** nel titolo, quindi chiudere la scheda della pagina **Word Online**.
    
5. Nella scheda **Raccolta siti di produzione**, in **Documenti**, fare clic su **Nuovo > Documento Word**.
    
6. 	Nella scheda **Word Online**, digitare **Note su divergenze relative al contratto Tailspin**, attendere finché non compare **Salvato** nel titolo, quindi chiudere la scheda **Word Online**.
    
7. Nella scheda **Raccolta siti di produzione**, viene visualizzato **Documento** e **Documento1** nell'elenco dei documenti.
    
8. Chiudere la scheda **Raccolta siti di produzione**.
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>Fase 3: Utilizzare eDiscovery avanzate per una controversia legale

Purtroppo una controversia contratto tra l'organizzazione e Tailspin Toys ha raggiunto il punto di un'azione legale. In questa procedura, creare e configurare un caso eDiscovery avanzate per cercare e analizzare il messaggio di posta elettronica e documenti che contengono il testo "Contratto Tailspin".
  
La procedura per l'uso di Advanced eDiscovery è la seguente:
  
- Creare una ricerca per la protezione &amp; centro conformità, analizzare i risultati e quindi preparare i risultati eDiscovery avanzate.
    
- Creare e configurare un caso di Advanced eDiscovery e analizzare i risultati della ricerca.
    
In questa procedura si crea una ricerca per la protezione &amp; conformità center per "Contratto Tailspin", consultare i risultati e quindi preparare i risultati eDiscovery avanzate.
  
1. Dalla scheda **Portale di Office 365**, fare clic su **Admin**.
    
2. Nella barra di spostamento a sinistra della scheda dell'interfaccia di amministrazione, fare clic su **Interfacce di amministrazione > Conformità**.
    
3. Nella **protezione &amp; conformità** fare clic su **autorizzazioni**.
    
4. Nell'elenco **Autorizzazioni**, fare doppio click su **Gestione organizzazione**.
    
5. Nella finestra **Gruppo di ruoli**, in **Membri** fare clic sul segno più.
    
6. Nella finestra **Seleziona membri**, fare doppio clic sul nome dell'account di amministratore, quindi fare clic su **OK**.
    
7. Nella finestra **Gruppo di ruoli**, fare clic su **Salva**.
    
8. Nell'elenco **Autorizzazioni**, fare doppio clic su **Responsabile di eDiscovery**.
    
9. Nella finestra **Gruppo di ruoli**, in **Amministratore di eDiscovery**, fare clic sull'icona più.
    
10. Nella finestra **Seleziona membri**, fare doppio clic sul nome dell'account di amministratore, quindi fare clic su **OK**.
    
11. Nella finestra **Gruppo di ruoli**, fare clic su **Salva**.
    
12. Nel riquadro di spostamento sinistra fare clic su **ricerca &amp; ricerca contenuto indagini gt _**.
    
13. Fare clic sull'icona più per aggiungere una ricerca.
    
14. Nella finestra **Nuova ricerca**, digitare **Ricerca contratto Tailspin** in **Nome**.
    
15. In **Dove vuoi effettuare la ricerca?**, fare clic su **Cerca ovunque,** selezionare **Exchange**, **SharePoint** e **Cartelle pubbliche**, quindi fare clic su **Avanti.**
    
16. In **Cosa vuoi cercare?**, digitare **Contratto Tailspin**, quindi fare clic su **Cerca**.
    
17. Nell'elenco delle ricerche, fare clic sul nome **Ricerca contratto Tailspin**.
    
18. Nel riquadro **Tailspin contratto ricerca** , fare clic su **Anteprima risultati di ricerca** **nell'area risultati della**. Verrà visualizzata una finestra che elenca i due documenti nel sito di SharePoint di produzione ( **documenti** e **Documento1**) e sui messaggi di **posta elettronica Test 1** e **3 e-mail di prova** a User6. Chiudere la finestra.
    
19. Nel riquadro **Ricerca contenuto**, in **Analizza i risultati con Advanced eDiscovery**, fare clic su **Anteprima risultati per analisi**.
    
20. Nella finestra **Prepara i risultati della ricerca per ricerca contratto Tailspin**, fare clic su **Prepara** e attendere il completamento dell'operazione.
    
In questa procedura, è possibile creare un nuovo caso di Advanced eDiscovery e analizzare i risultati della ricerca relativa al contratto Tailspin.
  
1. Nel riquadro di spostamento sinistra fare clic su **eDiscovery** in **ricerca &amp; indagini**.
    
2. Nel riquadro **eDiscovery**, fare clic su **Vai ad Advanced eDiscovery**.
    
3. Nella scheda **Advanced eDiscovery**, fare clic sull'icona più per aggiungere un nuovo caso.
    
4. 	Nel riquadro **Aggiungi caso**, digitare **Controversia relativa al contratto Tailspin** in **Nome**, quindi fare clic su **OK**. Attendere che il caso venga creato.
    
5. Fare doppio clic sul caso **Controversia relativa al contratto Tailspin** nell'elenco. 
    
6. Nell'elenco del **contenitore** , fare clic sul contenitore **ricerca contratto Tailspin** e quindi fare clic su **processo**. Attendere il completamento dell'elaborazione.
    
7. Quando nella parte inferiore della finestra viene visualizzato **Elaborazione completata**, fare clic su **Riepilogo elaborazione** nella barra di spostamento a sinistra per visualizzare un riepilogo.
    
8. Nella barra di spostamento superiore, fare clic su **Analizza**.
    
9. Nella pagina **Configurazione**, in **Temi** digitare **3** in **Numero massimo di temi**.
    
10. Fare clic su **Analyze** e attendere che l'analisi per il completamento. Dovrebbe essere visibile una serie di grafici a torta con analisi della popolazione target, documenti, messaggi di posta elettronica e allegati. Per ulteriori informazioni, vedere [visualizzazione di analizzare i risultati](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).
    
È ora possibile usare questo ambiente per creare nuovi contenuti, nuove ricerche e casi e sperimentare ulteriormente Advanced eDiscovery in Office 365.
  
## <a name="see-also"></a>Vedere anche

[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente di sviluppo/test della configurazione di base](base-configuration-dev-test-environment.md)
  
[Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
  
[DirSync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Cloud App Security per l'ambiente di sviluppo/test di Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)

[Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


