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
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: "Riepilogo: configurazione e dimostrazione di Office 365 Advanced Threat Protection nell'ambiente di sviluppo/test di Office 365."
ms.openlocfilehash: 53bff386490ed9647a511f75c997cb91b0acc181
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741342"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a>Protezione avanzata dalle minacce per l'ambiente di sviluppo/test di Office 365

 **Riepilogo:** configurazione e dimostrazione di Office 365 Advanced Threat Protection nell'ambiente di sviluppo/test di Office 365.
  
Office 365 Advanced Threat Protection (ATP) è una funzionalità di Exchange Online Protection (EOP) che consente di escludere il malware dalla posta elettronica. Con ATP, è possibile creare criteri nell'interfaccia di amministrazione di Exchange (EAC) o &amp; nel centro sicurezza e conformità che consentono agli utenti di accedere solo ai collegamenti o agli allegati nei messaggi di posta elettronica identificati come non dannosi. Per ulteriori informazioni, vedere [Protezione avanzata dalle minacce per allegati e collegamenti sicuri](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).
  
Con le istruzioni disponibili in questo articolo, è possibile configurare e testare ATP nella sottoscrizione di valutazione di Office 365.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: creare l'ambiente di sviluppo/test di Office 365 aziendale leggero o simulato

Se si desidera testare ATP in modo semplice con i requisiti minimi, seguire le istruzioni riportate nelle fasi 2 e 3 dell' [ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md).
  
Se si desidera testare ATP in un'azienda simulata, seguire le istruzioni in [dirsync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Testing ATP non richiede l'ambiente di sviluppo/testing dell'organizzazione simulata, che include una rete Intranet simulata connessa a Internet e la sincronizzazione della directory per una foresta di servizi di dominio Active Directory (AD DS). Qui viene fornito come un'opzione in modo da poter testare ATP e sperimentarlo in un ambiente che rappresenta un'organizzazione tipica. 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a>Fase 2: dimostrare il comportamento di recapito della posta elettronica predefinito di Office 365

In questa fase, viene mostrato che prima di configurare i criteri di ATP, i messaggi di posta elettronica potenzialmente dannosi vengono recapitati alle cassette postali di Office 365 senza essere sottoposti a screening o mitigazione.
  
1. Aprire Internet Explorer e accedere all'account di Outlook creato nella fase 2 dell'ambiente di [sviluppo/test di Office 365](office-365-dev-test-environment.md).
    
  - Se è in uso l'ambiente di sviluppo/test di Office 365 leggero, aprire una sessione privata di Internet Explorer e accedere dal computer locale.
    
  - Se si utilizza l'ambiente di sviluppo/test di Office 365 per l'organizzazione simulata, utilizzare il [portale di Azure](https://portal.azure.com) per connettersi alla macchina virtuale CLIENT1 e quindi eseguire l'accesso da CLIENT1.
    
2. Eseguire Notepad e immettere del testo.
    
3. Salvare il file nella cartella Documenti come  **getKeys.js**.
    
4. Dalla scheda Posta di Outlook di Internet Explorer, fare clic su **Nuovo**.
    
5. In **A**, digitare l'indirizzo di posta elettronica dell'amministratore globale di Office 365 della sottoscrizione di valutazione.
    
6. Per l'oggetto, digitare **Nuove chiavi**.
    
7. Nel corpo del messaggio, digitare **Ecco il file**.
    
8. Fare clic su **Allega**, fare doppio clic su **getKeys.js** nella cartella Documenti, fare clic su **Allega come copia**, quindi su **Invia**.
    
9. Fare clic su **Nuova regola**.
    
10. In **A**, digitare l'indirizzo di posta elettronica dell'amministratore globale di Office 365 della sottoscrizione di valutazione.
    
11. Per l'oggetto, digitare **Nuovo sito Web di viaggi**.
    
12. Nel corpo del messaggio, digitare **Qualcuno mi ha inoltrato questo sito**.
    
13. Nel corpo del messaggio, selezionare il testo **questo sito** e fare clic sull'icona del collegamento ipertestuale nella barra degli strumenti.
    
14. In **URL**Digitare **http://www.spamlink.contoso.com/**, fare clic su **OK**, quindi fare clic su **Invia**.
    
15. Aprire un'istanza separata di Internet Explorer in modalità esplorazione privata, accedere all'interfaccia di amministrazione di Microsoft 365[https://admin.microsoft.com](https://admin.microsoft.com)() e accedere alla sottoscrizione di valutazione di Office 365 con l'account di amministratore globale.
    
16. Dalla pagina principale del portale, fare clic sul riquadro delle app, quindi su **Posta**.
    
17. Nella Posta in arrivo, fare clic sul messaggio con l'oggetto **Nuove chiavi**.
    
18. Nella cartella posta inDesiderata, fare clic sul messaggio con il **nuovo sito Web di viaggio**soggetto. All'interno del messaggio, fare clic sul collegamento **sito** . Dovrebbe essere visualizzato un "Oops! Internet Explorer non è stato in grado di trovare spamlink.contoso.com. video. Questo è il risultato corretto perché non è presente alcuna pagina Web in tale posizione.
    
Si noti che questi messaggi di posta elettronica potenzialmente dannosi sono stati recapitati correttamente. Il messaggio di posta elettronica **Nuove chiavi** potrebbe contenere malware non rilevato e l'utente ha potuto fare clic sul collegamento potenzialmente dannoso nel messaggio di posta elettronica **Nuovo sito Web di viaggi**.
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a>Fase 3: configurare i criteri per i collegamenti sicuri e per gli allegati sicuri per ATP

In questa fase, viene creato un criterio per gli allegati sicuri per impedire il recapito di messaggi di posta elettronica contenenti allegati potenzialmente dannosi e un criterio per i collegamenti sicuri per impedire agli utenti di usare URL potenzialmente pericolosi.
  
1. Nella scheda **Microsoft Office Home** di Internet Explorer, fare clic sul riquadro **amministratore** .
    
2. Nella barra di spostamento a sinistra, fare clic su **Interfacce di amministrazione**, quindi su **Exchange**.
    
3. Nella barra di spostamento a sinistra della scheda dell'interfaccia di amministrazione di Exchange, fare clic su **protezione avanzata minacce**.
    
4. Fare clic sulla scheda **allegati sicuri** e quindi fare clic sul segno più.
    
5. Nella finestra **nuovo criterio allegati sicuri** , in **nome**, digitare **Safe Attachment Policy-Block**.
    
6. Per la **risposta malware sconosciuto degli allegati sicuri**, fare clic su **blocca**.
    
7. Per **Reindirizza allegato quando rilevato**, fare clic su **Abilita reindirizzamento** e digitare l'indirizzo di posta elettronica dell'account di amministratore globale di Office 365 in uso.
    
8. Per **Applicato a**, fare clic sulla freccia in giù, quindi fare clic su **Il dominio del destinatario è**. Nella finestra fare clic sul nome dell'organizzazione, ad esempio contoso.onmicrosoft.com, e quindi fare clic su **OK**.
    
9. Fare clic su **Salva**. Dopo l'aggiornamento, dovrebbe essere visualizzato il blocco nuovo e abilitato per i **criteri degli allegati sicuri**.
    
10. Fare clic sulla scheda **collegamenti sicuri** e quindi fare clic sul segno più.
    
11. Nella finestra **nuovi criteri collegamenti sicuri**, in **Nome**, digitare **Criteri collegamenti sicuri**.
    
12. Per **Seleziona l'azione da eseguire quando vengono rilevati URL sconosciuti potenzialmente dannosi nei messaggi**, fare clic su **Attiva**, quindi selezionare **Non consentire clickthrough all'URL originale da parte degli utenti**.
    
13. Per **Applicato a**, fare clic sulla freccia in giù, quindi fare clic su **Il dominio del destinatario è**. Nella finestra fare clic sul nome dell'organizzazione, ad esempio contoso.onmicrosoft.com, e quindi fare clic su **OK**.
    
14. Fare clic su **Salva**. Verrà visualizzato il nuovo **criterio collegamenti sicuri** abilitato.
    
## <a name="phase-4-show-atp-in-action"></a>Fase 4: dimostrazione di ATP in azione

In questa fase, viene mostrato come ATP si occupa dei messaggi di posta elettronica potenzialmente dannosi.
  
1. Dall'istanza di Internet Explorer utilizzata per inviare il messaggio di posta elettronica nella fase 2, nella barra di spostamento sinistra fare clic su **elementi inviati.**
    
2. Fare clic sul messaggio di posta elettronica intitolato le **nuove chiavi**, fare clic sull'icona freccia in giù e quindi fare clic su **Avanti**.
    
3. Per il nuovo messaggio, in **A**, digitare l'indirizzo di posta elettronica dell'amministratore globale di Office 365 della sottoscrizione di valutazione, quindi fare clic su **Invia**.
    
4. Fare clic sul **sito Web di nuovo viaggio**di posta elettronica dal titolo, fare clic sull'icona freccia in giù, fare clic su **Rispondi a tutto**e quindi su **Invia**.
    
5. Dall'istanza di Internet Explorer utilizzata per configurare i criteri ATP nella fase 3, fare clic sulla scheda dell'interfaccia di amministrazione di Exchange, selezionare il riquadro delle app e infine fare clic su **Posta**. Vengono visualizzati due nuovi messaggi di posta elettronica nella Posta in arrivo:
    
  - Uno dal titolo **Fw: Nuove chiavi**
    
  - Uno dal titolo **Fw: Nuovo sito Web di viaggi**
    
6. Aprire il messaggio di posta elettronica dal titolo **FW: nuovo sito Web di viaggio** e fare clic sul collegamento **sito** . Dovrebbe essere visualizzato un "questo sito Web è stato classificato come dannoso". video. Questo dimostra che ATP impedisce di accedere al sito Web potenzialmente dannoso.
    
7. Nella scheda dell'interfaccia di amministrazione di Exchange di Internet Explorer, nella barra di spostamento a sinistra, fare clic su **flusso di posta**.
    
8. Fare clic sulla scheda **Traccia messaggio** e quindi fare clic su **ricerca**.
    
9. Nella finestra **Risultati traccia messaggi**, fare doppio clic sul messaggio con l'oggetto **Nuove chiavi**. Questo messaggio è stato correttamente recapitato nella posta in arrivo. Chiudere la finestra.
    
10. Fare doppio clic sul messaggio con l'oggetto **Nuovo sito Web di viaggi**. Questo messaggio è stato correttamente recapitato nella posta in arrivo. Chiudere la finestra.
    
11. Fare doppio clic sul messaggio con l'oggetto **Fw: Nuove chiavi**. Tenere presente che il messaggio è stato elaborato da ATP e quindi recapitato nella posta in arrivo. Chiudere la finestra.
    
    > [!NOTE]
    > Lo scopo del criterio degli allegati sicuri consisteva nell'avviare l'analisi degli allegati per il codice dannoso. L'allegato getKeys. js è stato consentito perché non è stato determinato come dannoso. In questo passaggio viene mostrato che ATP ha eseguito un'analisi dell'allegato. 
  
12. Fare doppio clic sul messaggio con l'oggetto **Fw: Nuovo sito Web di viaggi**. Tenere presente che il messaggio è stato correttamente recapitato nella posta in arrivo.
    
È ora possibile utilizzare questo ambiente per creare nuovi criteri e sperimentare ATP.
  
> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per visualizzare una mappa di tutti gli articoli della guida del laboratorio di testing di Office 365.
  
## <a name="see-also"></a>Vedere anche

[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente di sviluppo/test della configurazione di base](base-configuration-dev-test-environment.md)
  
[Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
  
[DirSync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Cloud App Security per l'ambiente di sviluppo/test di Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md) 

[Protezione avanzata dalle minacce per allegati e collegamenti sicuri](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


