---
title: Protezione avanzata dalle minacce per l'ambiente di sviluppo/test di Office 365
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
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: 'Riepilogo: Configurare ed effettuare una dimostrazione di protezione di Office 365 avanzate rischio nell''ambiente di sviluppo e di testing di Office 365.'
ms.openlocfilehash: 3af5255d038f5cea40242162e149a873f347203f
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a>Protezione avanzata dalle minacce per l'ambiente di sviluppo/test di Office 365

 **Riepilogo:** Configurare e illustrare la protezione di Office 365 avanzate rischio nell'ambiente di sviluppo e di testing di Office 365.
  
Office 365 avanzate Threat Protection (degli strumenti di analisi) è una funzionalità di Exchange Online Protection (EOP) che consente di mantenere malware fuori la posta elettronica. Con degli strumenti di analisi, creare criteri nell'interfaccia di amministrazione di Exchange (EAC) o la protezione &amp; centro conformità per garantire che gli utenti devono accedere solo collegamenti o allegati nei messaggi di posta elettronica che vengono identificati come non dannoso. Per ulteriori informazioni, vedere [protezione rischio avanzata per gli allegati sicuri e collegamenti sicuri](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).
  
Con le istruzioni disponibili in questo articolo, è possibile configurare e testare ATP nella sottoscrizione di valutazione di Office 365.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: creare l'ambiente di sviluppo/test di Office 365 aziendale leggero o simulato

Se si desidera testare degli strumenti di analisi in un modo semplice con i requisiti minimi, seguire le istruzioni in fasi 2 e 3 [dell'ambiente di sviluppo e di testing di Office 365](office-365-dev-test-environment.md).
  
Se si desidera testare degli strumenti di analisi in un'azienda simulata, seguire le istruzioni in [DirSync per l'ambiente di sviluppo e di testing di Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Il test di ATP non richiede l'ambiente di sviluppo/test aziendale simulato, che include una rete Intranet simulata connessa a Internet e la sincronizzazione della directory per una foresta di Windows Server AD. Qui viene fornito come un'opzione in modo da poter testare ATP e sperimentarlo in un ambiente che rappresenta un'organizzazione tipica. 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a>Fase 2: Illustrare il comportamento di recapito di posta elettronica predefinito di Office 365

In questa fase, viene mostrato che prima di configurare i criteri di ATP, i messaggi di posta elettronica potenzialmente dannosi vengono recapitati alle cassette postali di Office 365 senza essere sottoposti a screening o mitigazione.
  
1. Aprire Internet Explorer e accedere all'account di Outlook creata nella fase 2 [dell'ambiente di sviluppo e di testing di Office 365](office-365-dev-test-environment.md).
    
  - Se è in uso l'ambiente di sviluppo/test di Office 365 leggero, aprire una sessione privata di Internet Explorer e accedere dal computer locale.
    
  - Se si utilizza l'ambiente di sviluppo e di testing di Office 365 enterprise simulato, utilizzare il [portale Azure](https://portal.azure.com) per connettersi alla macchina virtuale CLIENT1 e quindi effettuare l'accesso da CLIENT1.
    
2. Eseguire Notepad e immettere del testo.
    
3. Salvare il file nella cartella documenti come **getKeys.js**.
    
4. Nella scheda posta elettronica di Outlook di Internet Explorer, fare clic su **Nuovo**.
    
5. Nella casella **a**digitare l'indirizzo di posta elettronica del nome di amministratore globale di Office 365 della sottoscrizione di prova.
    
6. Per l'oggetto, digitare **i tasti di nuovi**.
    
7. Nel corpo, digitare **che qui è il file**.
    
8. Fare clic su **Collega**, fare doppio clic su **getKeys.js** nella cartella documenti, fare clic su **Collega come copia**e quindi fare clic su **Invia**.
    
9. Fare clic su **Nuovo**.
    
10. Nella casella **a**digitare l'indirizzo di posta elettronica del nome di amministratore globale di Office 365 della sottoscrizione di prova.
    
11. Per l'oggetto, digitare **New viaggi del sito web**.
    
12. Nel corpo, digitare **inoltrato questo sito**.
    
13. Nel corpo, selezionare il testo di **questo sito** e fare clic sull'icona di collegamento ipertestuale sulla barra degli strumenti.
    
14. In **URL**digitare **http://www.spamlink.contoso.com/**, fare clic su **OK**e quindi fare clic su **Invia**.
    
15. Aprire un'istanza separata di Internet Explorer in modalità di visualizzazione privata, passare al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) e accedere alla sottoscrizione di prova di Office 365 con l'account di amministratore globale.
    
16. Dalla pagina del portale principale, fare clic su sezioni App e quindi fare clic su **posta elettronica**.
    
17. Posta in arrivo, fare clic sul messaggio con l'oggetto **delle chiavi di nuove**.
    
18. Nella cartella posta indesiderata, fare clic sul messaggio con l'oggetto del **nuovo sito web di viaggio**. All'interno del messaggio, fare clic sul collegamento di **sito** . Verrà visualizzato un "Oops! Pagina di Internet Explorer Impossibile trovare spamlink.contoso.com.". Questo è il risultato corretto perché non esiste alcuna pagina web in tale posizione.
    
Si noti che entrambi questi messaggi di posta elettronica potenzialmente pericolosi sono stati recapitati correttamente. Messaggio di posta elettronica **le nuove chiavi** potrebbe contenere non rilevato malware e l'utente è stato autorizzato a fare clic sul collegamento nel messaggio di posta elettronica **nuovo sito web di viaggio** potenzialmente dannoso.
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a>Fase 3: configurare i criteri per i collegamenti sicuri e per gli allegati sicuri per ATP

In questa fase, viene creato un criterio per gli allegati sicuri per impedire il recapito di messaggi di posta elettronica contenenti allegati potenzialmente dannosi e un criterio per i collegamenti sicuri per impedire agli utenti di usare URL potenzialmente pericolosi.
  
1. Nella scheda **Home page di Microsoft Office** di Internet Explorer, fare clic su tessera di **amministrazione** .
    
2. Nel riquadro di spostamento sinistra fare clic su **Admin Center**, quindi scegliere **Exchange**.
    
3. Nel riquadro di spostamento sinistro della scheda Exchange admin center, fare clic su **Avanzate minacce**.
    
4. Fare clic sulla scheda **allegati attendibili** e quindi fare clic sul segno più.
    
5. Nella finestra **nuovo criterio di sicurezza degli allegati** , in **nome**digitare **Criteri allegato protetto - blocco**.
    
6. Per la **risposta malware sconosciuto gli allegati sicuri**, fare clic su **Blocca**.
    
7. Per **reindirizzare degli allegati nel rilevamento**, fare clic su **Abilita reindirizza** e digitare l'indirizzo di posta elettronica dell'account di amministratore globale di Office 365.
    
8. Per **applicata a**, fare clic sulla freccia e quindi **è il dominio del destinatario**. Nella finestra, scegliere il nome dell'organizzazione (ad esempio contoso.onmicrosoft.com) e quindi fare clic su **OK**.
    
9. Fare clic su **Salva**. Dopo l'aggiornamento, si dovrebbe essere visibile il nuovo e abilitato **Criteri allegato protetto - blocco**.
    
10. Fare clic sulla scheda **collegamenti attendibili** e quindi fare clic sul segno più.
    
11. Nella finestra **nuovo criterio di collegamenti sicuro** , in **nome**digitare **Criteri collegamento protetto**.
    
12. Per **Selezionare l'azione per gli URL potenzialmente pericolosi sconosciuti nei messaggi**, fare clic **su**e quindi selezionare **non consentire agli utenti di fare clic per URL originale**.
    
13. Per **applicata a**, fare clic sulla freccia e quindi **è il dominio del destinatario**. Nella finestra, scegliere il nome dell'organizzazione (ad esempio contoso.onmicrosoft.com) e quindi fare clic su **OK**.
    
14. Fare clic su **Salva**. Si dovrebbe essere visibile il nuovo e abilitato **Criteri collegamento protetto**.
    
## <a name="phase-4-show-atp-in-action"></a>Fase 4: dimostrazione di ATP in azione

In questa fase, viene mostrato come ATP si occupa dei messaggi di posta elettronica potenzialmente dannosi.
  
1. Dall'istanza di Internet Explorer utilizzato per inviare il messaggio nella fase 2, nel riquadro di spostamento sinistro, fare clic su **posta inviata.**
    
2. Fare clic su posta elettronica denominato **le nuove chiavi**, fare clic sull'icona di freccia verso il basso e quindi fare clic su **Avanti**.
    
3. Per i nuovi messaggi, nella casella **a**digitare l'indirizzo di posta elettronica il nome di amministratore globale di Office 365 dell'abbonamento prova e quindi fare clic su **Invia**.
    
4. Fare clic su posta elettronica denominato **New viaggi del sito web**, fare clic sull'icona di freccia verso il basso, fare clic su **Rispondi a tutti**e quindi fare clic su **Invia**.
    
5. Dall'istanza di Internet Explorer utilizzato per configurare i criteri degli strumenti di analisi nella fase 3, fare clic sulla scheda Exchange admin center, fare clic su sezioni App e quindi fare clic su **posta elettronica**. Verrà visualizzata due nuovi messaggi di posta elettronica in arrivo:
    
  - Uno intitolato **firmware: le nuove chiavi**
    
  - Uno intitolato **firmware: nuovo sito web viaggi**
    
6. Aprire il messaggio di posta elettronica denominato **firmware: nuovo sito web viaggi** e fare clic sul collegamento di **sito** . Verrà visualizzata una pagina "il sito Web è stato classificato come dannose.". Dimostra che degli strumenti di analisi è impedire l'accesso al sito web potenzialmente dannosi.
    
7. In Exchange admin center scheda di Internet Explorer, nel riquadro di spostamento sinistra fare clic su **flusso di posta**.
    
8. Fare clic sulla scheda **traccia dei messaggi** e fare clic su **Cerca**.
    
9. Nella finestra **Message Trace Results** , fare doppio clic sul messaggio con l'oggetto **delle chiavi di nuove**. Questo messaggio è stato correttamente recapitato alla posta in arrivo. Chiudere la finestra.
    
10. Fare doppio clic sul messaggio con l'oggetto del **nuovo sito web di viaggio**. Questo messaggio è stato correttamente recapitato alla posta in arrivo. Chiudere la finestra.
    
11. Fare doppio clic sul messaggio con l'oggetto **firmware: le nuove chiavi**. Si noti come questo messaggio è stato elaborato da strumenti di analisi e quindi recapitato nella posta in arrivo. Chiudere la finestra.
    
    > [!NOTE]
    > Lo scopo del criterio gli allegati sicuri era per avviare la scansione degli allegati per malware. L'allegato getKeys.js è stato consentito perché non è stata determinata da dannoso. Questo passaggio viene illustrato che degli strumenti di analisi è stato viene eseguita un'analisi dell'allegato. 
  
12. Fare doppio clic sul messaggio con l'oggetto **firmware: nuovo sito web di viaggio**. Si noti che questo messaggio è stato correttamente recapitato alla posta in arrivo.
    
È ora possibile utilizzare questo ambiente per creare nuovi criteri e sperimentare ATP.
  
> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
  
## <a name="see-also"></a>Vedere anche

[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente di sviluppo/test della configurazione di base](base-configuration-dev-test-environment.md)
  
[Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
  
[DirSync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Cloud App Security per l'ambiente di sviluppo/test di Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md) 

[Protezione avanzata dalle minacce per allegati e collegamenti sicuri](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


