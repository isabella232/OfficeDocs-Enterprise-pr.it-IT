---
title: "Protezione dei file sensibili nell’ambiente di sviluppo/test di Office 365"
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
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: 'Riepilogo: Configurare e illustrare come Information Rights Management di Office 365 consente di proteggere i file riservati, anche quando vengono registrate per la raccolta siti di SharePoint Online non corretto.'
ms.openlocfilehash: eb456c86b118556abde6a887fe8b9ab68300740b
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Protezione dei file sensibili nell’ambiente di sviluppo/test di Office 365

 **Riepilogo:** Configurare e illustrare come Information Rights Management di Office 365 consente di proteggere i file riservati, anche quando vengono registrate per la raccolta siti di SharePoint Online non corretto.
  
Information Rights Management (IRM) in Office 365 è un set di funzionalità per proteggere i documenti che vengono scaricati dalle raccolte e dagli elenchi di SharePoint Online. I file scaricati vengono crittografati e includono le autorizzazioni per aprire, copiare, salvare e stampare che riflettono la raccolta di SharePoint Online in cui sono stati salvati.
  
Con le istruzioni disponibili in questo articolo, è possibile abilitare e testare Information Rights Management in Office 365 per i file contenenti possibili informazioni riservate nella sottoscrizione di valutazione di Office 365.
  
> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Fase 1: creare l'ambiente di sviluppo/testing di Office 365

Se si desidera testare protezione file riservati in un modo semplice con i requisiti minimi, seguire le istruzioni in fasi 2 e 3 [dell'ambiente di sviluppo e di testing di Office 365](office-365-dev-test-environment.md).
  
Se si desidera testare protezione file riservati in un'azienda simulata, seguire le istruzioni in [DirSync per l'ambiente di sviluppo e di testing di Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Il test della protezione dei file sensibili non richiede l'ambiente di sviluppo/testing aziendale simulato, che include una rete Intranet simulata connessa a Internet e la sincronizzazione directory per una foresta di Windows Server AD. Questo test viene fornito qui come opzione in modo per consentire di testare la protezione dei file sensibili e sperimentarla in un ambiente che rappresenta un'organizzazione tipica. 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>Fase 2: dimostrare in che modo i documenti dei siti protetti possono andare persi

In questa fase si dimostra che un utente può scaricare un documento da un sito protetto da autorizzazioni e quindi caricarlo in un sito con autorizzazioni aperte.
  
È innanzitutto necessario aggiungere tre nuovi account utente che rappresentano i dirigenti e assegnare loro le licenze di Office 365 E5.
  
Utilizzare le istruzioni riportate in [connessione a Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) per installare i moduli di PowerShell (se necessario) e connettersi a tua nuova sottoscrizione di Office 365 da:
  
- Dal computer (per l'ambiente di sviluppo/test di Office 365 leggero).
    
- Dalla macchina virtuale CLIENT1 (per l'ambiente di sviluppo/test di Office 365 aziendale simulato).
    
Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell** digitare il nome di amministratore globale di Office 365 (esempio: jdoe@contosotoycompany.onmicrosoft.com) e la password dell'abbonamento prova Office 365.
  
Immettere il nome dell'organizzazione (ad esempio: contosotoycompany) e il prefisso internazionale a due caratteri, quindi eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

La visualizzazione del comando **New-MsolUser** , annotare la password generata per l'account di amministratore delegato e registrarlo in un percorso sicuro.
  
Eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Dalla visualizzazione del comando **New-MsolUser** , tenere presente la password generata per l'account di amministratore e registrarlo in un percorso sicuro.
  
Eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Dalla visualizzazione del comando **New-MsolUser** , tenere presente la password generata per l'account COO e registrarlo in un percorso sicuro.
  
Successivamente, si crea un gruppo di dirigenti privato e vi si aggiungono i nuovi account dirigente.
  
1. Nel browser, accedere al portale di Office in [http://portal.office.com](http://portal.office.com) e accedere alla sottoscrizione di prova di Office 365 con l'account di amministratore globale.
    
  - Se è in uso l'ambiente di sviluppo/test di Office 365 leggero, aprire una sessione privata di Internet Explorer o del proprio browser e accedere dal computer locale.
    
  - Se è in uso l'ambiente di sviluppo/test di Office 365 aziendale simulato, utilizzare il Portale di Azure per connettersi alla macchina virtuale CLIENT1, quindi accedere da CLIENT1.
    
2. Nella scheda **Home page di Microsoft Office** , fare clic su **Amministrazione > gruppi > gruppi**e quindi fare clic su **Aggiungi gruppo**.
    
3. Nella finestra **Aggiungi gruppo**, selezionare **il gruppo di Office 365** per il tipo di gruppo, digitare **dirigenti** in **nome** e l' **Id di gruppo**, selezionare **privata** di **Privacy**e quindi fare clic su **Seleziona proprietario**.
    
4. Nell'elenco, fare clic sul nome dell'account di amministratore globale.
    
5. Fare clic su **Aggiungi**e quindi fare clic su **Chiudi**.
    
6. Nell'elenco gruppi fare clic su **dirigenti**.
    
7. Fare clic su **Modifica per i membri**.
    
8. Fare clic su **Aggiungi membri**. Nell'elenco dei membri, selezionare l'account utente seguenti:
    
  - Amministratore delegato
    
  - Direttore finanziario
    
  - Responsabile produzione
    
9. Fare clic su **Salva**e quindi fare clic su **Chiudi**.
    
10. Chiudere la scheda di **interfaccia di amministrazione di Office** .
    
Successivamente, creare una raccolta siti dirigenti e consentire solo ai membri del gruppo Dirigenti di accedervi.
  
1. Nella scheda **Microsoft Office Home**, fare clic sulla sezione **Amministrazione**.
    
2. Nella scheda di **interfaccia di amministrazione di Office** , fare clic su **Admin Center > SharePoint**.
    
3. Nella scheda di **interfaccia di amministrazione di SharePoint** , fare clic su **Nuovo > raccolta siti privata**.
    
4. Nel nuovo riquadro di raccolta siti, digitare **dirigenti** **titolo**, dirigenti nella casella URL specificare il nome dell'account di amministratore globale di **amministratore**e quindi fare clic su **OK**.
    
5. Attendere che la nuova raccolta siti è stata creata. Al termine, copiare l'URL della nuova raccolta di siti dirigenti e incollarlo in una nuova scheda del browser.
    
6. In alto a destra della raccolta siti **dirigenti** , fare clic sull'icona impostazioni e quindi fare clic su **condiviso con**.
    
7. In **condivisione "Executives"**fare clic su **Avanzate**.
    
8. Nell'elenco dei gruppi di SharePoint fare clic su **Dirigenti membri**.
    
9. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
10. In **condivisione "Executives"**, digitare **dirigenti**, fare clic sul gruppo **dirigenti** e fare clic su **Condividi**.
    
11. Chiudere la scheda **utenti e gruppi** .
    
Successivamente, consentire a tutti gli utenti di accedere alla raccolta siti vendite.
  
1. Dalla scheda di **interfaccia di amministrazione di SharePoint** , copiare l'URL della raccolta siti di vendita e incollarlo in una nuova scheda del browser..
    
2. In alto a destra, fare clic sull'icona impostazioni e quindi fare clic su **condiviso con**.
    
3. In **condivisione "Collection sito vendite"**, fare clic su **Avanzate**.
    
4. Nell'elenco dei gruppi di SharePoint, fare clic su **raccolta membri siti Sales**.
    
5. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
6. In **condivisione "Collection sito vendite"**, digitare **tutti**, fare clic su **tutti tranne agli utenti esterni**e quindi fare clic su **Condividi**.
    
7. Chiudere le schede **SharePoint** e **raccolta siti di Sales** .
    
Successivamente, accedere con un account dirigente e creare un documento nella raccolta siti dirigenti.
  
1. Nella scheda **Home page di Microsoft Office** , fare clic sull'icona utente in alto a destra e fare clic su **Esci**.
    
2. Visitare [http://portal.office.com](http://portal.office.com).
    
3. Nella pagina **Office 365 accedere** , fare clic su **utilizza un altro account**.
    
4. Digitare il nome dell'account **amministratore delegato** e la relativa password e quindi fare clic su **Accedi**.
    
5. In una nuova scheda del browser, digitare l'URL della raccolta siti dirigenti ( **https://**\<nome organizzazione >**.sharepoint.com/sites/executives**).
    
6. Fare clic su **documenti**, fare clic su **Nuovo** e quindi fare clic su **Documenti di Word**.
    
7. Fare clic sulla barra del titolo e digitare **SensitiveData BeforeIRM**.
    
8. Fare clic su nel corpo del documento e digitare **minuti dalla riunione più recente di area**e quindi fare clic su **dirigenti**.
    
     Dovrebbe essere visibile **SensitiveData BeforeIRM.docx** nella cartella **documenti** .
    
Quindi scaricare una copia locale del documento SensitiveData-BeforeIRM.docx e quindi pubblicarla accidentalmente nella raccolta siti vendite.
  
1. Creare una nuova cartella nel computer locale (ad esempio, c\\laboratori\\SensitiveDataTestFiles).
    
2. Nella scheda **documenti** del browser, selezionare il documento **SensitiveData BeforeIRM.docx** , fare clic sui puntini di sospensione e quindi fare clic su **Download**.
    
3. Archiviare i documenti **SensitiveData BeforeIRM.docx** nella cartella creata nel passaggio 1.
    
4. In una nuova scheda del browser, digitare l'URL della raccolta siti di vendite ( **https://**\<nome organizzazione >**.sharepoint.com/sites/sales**).
    
5. Fare clic sulla cartella **documenti** della **raccolta siti di Sales**.
    
6. Fare clic su **Carica**e quindi specificare **SensitiveData BeforeIRM.docx** documento nella cartella creata nel passaggio 1 e quindi fare clic su **OK**.
    
7. Verificare che il documento **SensitiveData BeforeIRM.docx** sia nella cartella **documenti** .
    
8. Chiudere le schede **vendite** e **SharePoint** .
    
Successivamente, accedere come User5 e provare ad aprire il documento SensitiveData-BeforeIRM.docx nella raccolta siti vendite.
  
1. Nella scheda **Home page di Microsoft Office** , fare clic sull'icona utente in alto a destra e fare clic su **Esci**.
    
2. Visitare [http://portal.office.com](http://portal.office.com).
    
3. Nella pagina **Office 365 accedere** , fare clic su **utilizza un altro account**.
    
4. Digitare il nome dell'account User5 e la relativa password e quindi fare clic su **Accedi**.
    
5. In una nuova scheda del browser, digitare l'URL della raccolta siti di Sales.
    
6. Nella cartella **documenti** di **vendita raccolta siti**, fare clic sul documento **SensitiveData BeforeIRM.docx** .
    
    Dovrebbero essere visualizzati i relativi contenuti.
    
7. Chiudere le schede di **documenti** e **raccolta siti di Sales** .
    
Registrando accidentalmente il documento SensitiveData-BeforeIRM.docx nella raccolta siti vendite, il CEO ha ignorato la sicurezza delle autorizzazioni della raccolta siti dirigenti.
  
Per preparare Office 365 per le fasi 3 e 4, abilitare IRM per SharePoint Online.
  
1. Nella scheda **Home page di Microsoft Office** , fare clic sull'icona utente in alto a destra e fare clic su **Esci**.
    
2. Visitare [http://portal.office.com](http://portal.office.com).
    
3. Nella pagina **Office 365 accedere** fare clic sul nome di account amministratore globale, digitare la password e quindi fare clic su **Accedi**.
    
4. Nella scheda **Home page di Microsoft Office** , fare clic su **Amministrazione > Admin Center > SharePoint**.
    
5. Nella scheda di **interfaccia di amministrazione di SharePoint** fare clic su **Impostazioni**.
    
6. Nella sezione **Information Rights Management (IRM)** della pagina **Impostazioni** selezionare **utilizza il servizio IRM specificato nella configurazione**e quindi selezionare **Aggiorna le impostazioni di IRM**.
    
7. Chiudere la scheda di **interfaccia di amministrazione di SharePoint** .
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>Fase 3: usare Information Rights Management di SharePoint con un gruppo privato di Office 365

In questa fase, si utilizza SharePoint Information Rights Management con un gruppo privato di Office 365 per proteggere l'accesso a un documento con informazioni riservate, anche quando viene pubblicato in un sito con autorizzazioni aperte.
  
Innanzitutto, abilitare e configurare IRM per la raccolta documenti della raccolta siti dirigenti.  
  
1. In una nuova scheda del browser, digitare l'URL della raccolta siti dirigenti.
    
2. Fare clic su **documenti**.
    
3. In alto a destra, fare clic sull'icona impostazioni e quindi fare clic su **Impostazioni raccolta**.
    
4. Nella pagina **Impostazioni** in **autorizzazioni e gestione**fare clic su **Information Rights Management**.
    
5. Nella pagina **Impostazioni di Information Rights Management** :
    
  - Selezionare **Limita le autorizzazioni per i documenti al momento del download della raccolta**.
    
  - Per **creare un titolo di criteri di autorizzazione**digitare **dirigenti**.
    
  - Per **una descrizione dei criteri di autorizzazione Aggiungi**, digitare **IRM per i dirigenti**.
    
6. Fare clic su **Mostra opzioni**.
    
7. In **impostazioni aggiuntive IRM raccolta**, selezionare **non consentire agli utenti di caricare documenti che non supportano IRM**.
    
8. In **Configura diritti di accesso di documento**, selezionare **Consenti visualizzatori di stampa** e **Consenti visualizzatori di scrittura su una copia del documento scaricato**.
    
9. In **impostare la protezione di gruppo e l'intervallo delle credenziali**, selezionare **Consenti la protezione di gruppo** e nel **gruppo predefinito**, digitare **dirigenti**.
    
10. Fare clic su **OK**.
    
Successivamente, agendo da CEO, si carica un nuovo documento nella cartella documenti Dirigenti, lo si scarica, quindi lo si carica accidentalmente nella cartella documenti Vendite.
  
1. Aprire la cartella locale in cui sono memorizzati i documenti **SensitiveData BeforeIRM.docx** .
    
2. Pulsante destro del mouse **SensitiveData BeforeIRM.docx**e quindi fare clic su **Copia**.
    
3. Pulsante destro del mouse all'interno della cartella e quindi scegliere **Incolla**.
    
4. Rinominare il nuovo file **SensitiveData-BeforeIRM - Copy.docx** a **SensitiveData AfterIRM.docx**.
    
5. Nella scheda **Home page di Microsoft Office** nel browser, fare clic sull'icona utente in alto a destra e quindi fare clic su **Esci**.
    
6. Visitare [http://portal.office.com](http://portal.office.com).
    
7. Nella pagina **Office 365 accedere** fare clic sul nome di account di amministratore delegato, digitare la password e quindi fare clic su **Accedi**.
    
8. In una nuova scheda del browser, digitare l'URL della raccolta siti dirigenti.
    
9. Nella pagina **documenti** fare clic su **Carica**, specificare il documento **SensitiveData AfterIRM.docx** nella cartella locale e quindi fare clic su **Apri**.
    
10. Selezionare il nuovo documento **SensitiveData AfterIRM.docx** nella pagina **documenti** , fare clic sui puntini di sospensione (...) nella barra dei menu e quindi fare clic su **Download**.
    
11. Quando richiesto, salvare il documento **SensitiveData AfterIRM.docx** nella cartella locale, sovrascrivendo la versione originale.
    
12. Chiudere la scheda per la pagina **documenti** .
    
13. In una nuova scheda del browser, digitare l'URL della raccolta siti di Sales.
    
14. Fare clic su **documenti**.
    
15. Nella pagina **documenti** fare clic su **Carica**, specificare il documento **SensitiveData AfterIRM.docx** nella cartella locale e quindi fare clic su **Apri**.
    
16. Chiudere le schede **SharePoint** e **raccolta siti di Sales** .
    
Successivamente, opera come utente normale, si tenta di accedere al documento **SensitiveData AfterIRM.docx** nella cartella del documento Sales.
  
1. Nella scheda **Home page di Microsoft Office** nel browser, fare clic sull'icona utente in alto a destra e quindi fare clic su **Esci**.
    
2. Visitare [http://portal.office.com](http://portal.office.com).
    
3. Nella pagina **Office 365 accedere** fare clic sul nome di account User5, digitare la password e quindi fare clic su **Accedi**.
    
4. In una nuova scheda del browser, digitare l'URL della raccolta siti di Sales.
    
5. Fare clic su **documenti**.
    
6. Nella pagina **documenti** , aprire il documento **SensitiveData AfterIRM.docx** .
    
    Verrà visualizzato un messaggio di errore "Impossibile aprire il documento in Word Online perché è protetto con Information Rights Management (IRM)".  
    
7. Fare clic su **Modifica in Word**. Viene chiesto se si desidera aprire il file. Fare clic su **Sì**.
    
8. Viene richiesto di accesso. digitare il nome dell'account User5 e quindi fare clic su **Avanti**.
    
9. Viene chiesto di immettere la password. Digitare la password per l'account User5 e quindi fare clic su **Accedi**. 
    
    Verrà visualizzato un messaggio di errore che informa: "L'utente non dispone delle credenziali per aprire il documento".
    
10. Fare clic su **No**.
    
Per vedere la protezione IRM, è necessario esaminare i file nella cartella locale. **SensitiveData AfterIRM.docx** deve essere maggiore del file **SensitiveData BeforeIRM.docx** . Il file **SensitiveData AfterIRM.docx** è crittografato e aggiunte le informazioni di protezione IRM a tale.
  
## <a name="see-also"></a>Vedere anche

[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente di sviluppo/test della configurazione di base](base-configuration-dev-test-environment.md)
  
[Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)


