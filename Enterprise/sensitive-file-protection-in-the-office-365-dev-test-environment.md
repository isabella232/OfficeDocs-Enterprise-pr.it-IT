---
title: Protezione dei file sensibili nell’ambiente di sviluppo/test di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- SPO_Content
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: 'Riepilogo: configurare e illustrare in che modo Office 365 Information Rights Management protegge i file sensibili, anche quando vengono pubblicati nella raccolta siti di SharePoint Online errata.'
ms.openlocfilehash: b8cb56a69a04133b2863c31da9e359c2272d4fc5
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078125"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Protezione dei file sensibili nell'ambiente di sviluppo/test di Office 365

 **Riepilogo:** Configurare e illustrare in che modo Office 365 Information Rights Management protegge i file sensibili, anche quando vengono inseriti nella raccolta siti di SharePoint Online errata.
  
Information Rights Management (IRM) in Office 365 è un set di funzionalità per proteggere i documenti che vengono scaricati dalle raccolte e dagli elenchi di SharePoint Online. I file scaricati vengono crittografati e includono le autorizzazioni per aprire, copiare, salvare e stampare che riflettono la raccolta di SharePoint Online in cui sono stati salvati.
  
Con le istruzioni disponibili in questo articolo, è possibile abilitare e testare Information Rights Management in Office 365 per i file contenenti possibili informazioni riservate nella sottoscrizione di valutazione di Office 365.
  
> [!TIP]
> Fare clic [qui](https://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli nella serie di guide dei lab di test di Office 365.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Fase 1: creare l'ambiente di sviluppo/testing di Office 365

Se si desidera semplicemente testare la protezione dei file sensibili con i requisiti minimi, seguire le istruzioni nelle fasi 2 e 3 di [Office 365 dev/test environment](office-365-dev-test-environment.md).
  
Se si desidera testare la protezione dei file sensibili in un'azienda simulata, seguire le istruzioni in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> La verifica della protezione dei file sensibili non richiede l'ambiente di sviluppo/testing dell'organizzazione simulata, che include una rete Intranet simulata connessa a Internet e la sincronizzazione della directory per una foresta di servizi di dominio Active Directory (AD DS). Questo test viene fornito qui come opzione in modo per consentire di testare la protezione dei file sensibili e sperimentarla in un ambiente che rappresenta un'organizzazione tipica. 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>Fase 2: dimostrare in che modo i documenti dei siti protetti possono andare persi

In questa fase si dimostra che un utente può scaricare un documento da un sito protetto da autorizzazioni e quindi caricarlo in un sito con autorizzazioni aperte.
  
È innanzitutto necessario aggiungere tre nuovi account utente che rappresentano i dirigenti e assegnare loro le licenze di Office 365 E5.
  
Utilizzare le istruzioni in [Connect to office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) per installare i moduli di PowerShell (se necessario) e connettersi alla nuova sottoscrizione di Office 365 da:
  
- Dal computer (per l'ambiente di sviluppo/test di Office 365 leggero).
    
- Dalla macchina virtuale CLIENT1 (per l'ambiente di sviluppo/test di Office 365 aziendale simulato).
    
Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell**, digitare il nome dell'amministratore globale Office 365 (ad esempio: jdoe@contosotoycompany.onmicrosoft.com) e la password della sottoscrizione di valutazione di Office 365.
  
Immettere il nome dell'organizzazione (ad esempio: contosotoycompany) e il prefisso internazionale a due caratteri, quindi eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Dalla visualizzazione del comando **New-MsolUser**, prendere nota della password generata per l'account CEO e conservarla in una posizione sicura.
  
Eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Dalla visualizzazione del comando **New-MsolUser**, prendere nota della password generata per l'account CFO e conservarla in una posizione sicura.
  
Eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Dalla visualizzazione del comando **New-MsolUser**, prendere nota della password generata per l'account COO e conservarla in una posizione sicura.
  
Successivamente, si crea un gruppo di dirigenti privato e vi si aggiungono i nuovi account dirigente.
  
1. Nel browser, accedere al portale di Office [https://admin.microsoft.com](https://admin.microsoft.com) e accedere alla sottoscrizione di valutazione di Office 365 con l'account di amministratore globale.
    
  - Se è in uso l'ambiente di sviluppo/test di Office 365 leggero, aprire una sessione privata di Internet Explorer o del proprio browser e accedere dal computer locale.
    
  - Se è in uso l'ambiente di sviluppo/test di Office 365 aziendale simulato, utilizzare il Portale di Azure per connettersi alla macchina virtuale CLIENT1, quindi accedere da CLIENT1.
    
2. Nella scheda **Microsoft Office Home**, fare clic su **Amministratore > Gruppi > Gruppi**, quindi fare clic su **Aggiungi gruppo**.
    
3. In **Aggiungi gruppo**, selezionare **Gruppo di Office 365** per il tipo di gruppo, digitare **Dirigenti** in **Nome** e **ID gruppo**, selezionare **Privato** per **Privacy**e quindi fare clic su **Seleziona proprietario**.
    
4. Nell'elenco, fare clic sul nome dell'account di amministratore globale.
    
5. Fare clic su **Aggiungi**, quindi fare clic su **Chiudi**.
    
6. Nell'elenco di gruppi, fare clic su **Dirigenti**.
    
7. Fare clic su **Modifica per i membri**.
    
8. Fare clic su **Aggiungi membri**. Nell'elenco dei membri, selezionare i seguenti account utente:
    
  - Amministratore delegato
    
  - Direttore finanziario
    
  - Responsabile produzione
    
9. Fare clic su **Salva**, quindi fare clic su **Chiudi**.
    
10. Chiudere la scheda **Interfaccia di amministrazione di Office**.
    
Successivamente, creare una raccolta siti dirigenti e consentire solo ai membri del gruppo Dirigenti di accedervi.
  
1. Nella scheda **Microsoft Office Home**, fare clic sulla sezione **Amministrazione**.
    
2. Nella scheda dell'interfaccia di **amministrazione di Office** , fare clic su interfaccia di **Amministrazione > SharePoint**.
    
3. Nella scheda dell'interfaccia di **amministrazione di SharePoint** , fare clic su **nuovo > raccolta siti privati**.
    
4. Nel riquadro nuovo raccolta siti, digitare **dirigenti** in **titolo**, dirigenti nella casella URL, specificare il nome dell'account di amministratore globale in **Administrator**e quindi fare clic su **OK**.
    
5. Attendere che la nuova raccolta siti sia stata creata. Al termine dell'operazione, copiare l'URL della nuova raccolta siti dirigenti e incollarlo in una nuova scheda del browser.
    
6. In alto a destra della raccolta siti **Dirigenti**, fare clic sull'icona Impostazioni, quindi selezionare **Condiviso con**.
    
7. In **Condividi "dirigenti"**, fare clic su **Avanzate**.
    
8. Nell'elenco dei gruppi di SharePoint, fare clic su **Membri dirigenti**.
    
9. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
10. In **Condividi "dirigenti"**, digitare **dirigenti**, fare clic sul gruppo **dirigenti** , quindi fare clic su **Condividi**.
    
11. Chiudere la scheda **utenti e gruppi** .
    
Successivamente, consentire a tutti gli utenti di accedere alla raccolta siti vendite.
  
1. Nella scheda dell'interfaccia di **amministrazione di SharePoint** , copiare l'URL della raccolta siti di vendita e incollarlo in una nuova scheda del browser.
    
2. In alto a destra, fare clic sull'icona Impostazioni, quindi selezionare **Condiviso con**.
    
3. In **Condividi "raccolta siti vendite"**, fare clic su **Avanzate**.
    
4. Nell'elenco dei gruppi di SharePoint, fare clic su **Membri raccolta siti vendite**.
    
5. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
6. In **Condividi "raccolta siti vendite"**, digitare **tutti**, fare clic su **tutti tranne gli utenti esterni**, quindi fare clic su **Condividi**.
    
7. Chiudere le schede **Raccolta siti vendite** e **SharePoint**.
    
Successivamente, accedere con un account dirigente e creare un documento nella raccolta siti dirigenti.
  
1. Nella scheda **Microsoft Office Home** fare clic sull'icona dell'account utente in alto a destra, quindi fare clic su **Disconnetti**.
    
2. Passare a [https://admin.microsoft.com](https://admin.microsoft.com).
    
3. Nella pagina di **accesso di Office 365**, fare clic su **Usa un altro account**.
    
4. Digitare il nome dell'account **CEO** e la relativa password, quindi fare clic su **Accedi**.
    
5. In una nuova scheda del browser, digitare l'URL della raccolta siti dirigenti ( **https://**\<Organization Name>**. SharePoint.com/sites/Executives**).
    
6. Fare clic su **documenti**, fare clic su **nuovo** e quindi su **documento di Word**.
    
7. Fare clic nella barra del titolo e digitare **SensitiveData-BeforeIRM**.
    
8. Fare clic nel corpo del documento e digitare **Minuti dall'ultima riunione del consiglio di amministrazione**, quindi fare clic su **Dirigenti**.
    
      Viene visualizzato **SensitiveData-BeforeIRM.docx** nella cartella **Documenti**.
    
Quindi scaricare una copia locale del documento SensitiveData-BeforeIRM.docx e quindi pubblicarla accidentalmente nella raccolta siti vendite.
  
1. Nel computer locale, creare una nuova cartella (ad esempio, C:\\TLG\\SensitiveDataTestFiles).
    
2. Nella scheda **Documenti** del browser, selezionare il documento **SensitiveData-BeforeIRM.docx**, fare clic sui puntini di sospensione, quindi fare clic su **Scarica**.
    
3. Archiviare il documento **SensitiveData-BeforeIRM.docx** nella cartella creata nel passaggio 1.
    
4. In una nuova scheda del browser, digitare l'URL della raccolta siti di vendita ( **https://**\<Organization Name>**. SharePoint.com/sites/sales**).
    
5. Fare clic sulla cartella **Documenti** della **Raccolta siti vendite**.
    
6. Fare clic su **Carica**, quindi specificare il documento **SensitiveData-BeforeIRM.docx** nella cartella creata nel passaggio 1, quindi fare clic su **OK**.
    
7. Verificare che il documento **SensitiveData-BeforeIRM.docx** sia visualizzato nella cartella **Documenti**.
    
8. Chiudere le schede **Vendite** e **SharePoint**.
    
Successivamente, accedere come User5 e provare ad aprire il documento SensitiveData-BeforeIRM.docx nella raccolta siti vendite.
  
1. Nella scheda **Microsoft Office Home** fare clic sull'icona dell'account utente in alto a destra, quindi fare clic su **Disconnetti**.
    
2. Passare a [https://admin.microsoft.com](https://admin.microsoft.com).
    
3. Nella pagina di **accesso di Office 365**, fare clic su **Usa un altro account**.
    
4. Digitare il nome dell'account di User5 e la relativa password, quindi fare clic su **Accedi**.
    
5. In una nuova scheda del browser, digitare l'URL della raccolta siti di vendita.
    
6. Nella cartella **Documenti** della **Raccolta siti vendite**, fare clic sul documento **SensitiveData-BeforeIRM.docx**. 
    
    Dovrebbero essere visualizzati i relativi contenuti.
    
7. Chiudere le schede **Documenti** e **Raccolta siti vendite**.
    
Registrando accidentalmente il documento SensitiveData-BeforeIRM.docx nella raccolta siti vendite, il CEO ha ignorato la sicurezza delle autorizzazioni della raccolta siti dirigenti.
  
Per preparare Office 365 per le fasi 3 e 4, abilitare IRM per SharePoint Online.
  
1. Nella scheda **Microsoft Office Home** fare clic sull'icona dell'account utente in alto a destra, quindi fare clic su **Disconnetti**.
    
2. Passare a [https://admin.microsoft.com](https://admin.microsoft.com).
    
3. Nella pagina **Accesso a Office 365**, fare clic sul nome dell'account di amministratore globale, digitare la relativa password, quindi fare clic su **Accedi**.
    
4. Nella scheda **Microsoft Office Home**, fare clic su **Amministratore > Interfacce di amministrazione > SharePoint**.
    
5. Nella scheda **Interfaccia di amministrazione di SharePoint**, fare clic su **Impostazioni**.
    
6. Nella sezione **Information Rights Management (IRM)** della pagina selezionare **Usa il servizio IRM specificato nella configurazione**e quindi selezionare **Aggiorna impostazioni IRM**.
    
7. Chiudere la scheda **Interfaccia di amministrazione di SharePoint**.
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>Fase 3: usare Information Rights Management di SharePoint con un gruppo privato di Office 365

In questa fase, si utilizza SharePoint Information Rights Management con un gruppo privato di Office 365 per proteggere l'accesso a un documento con informazioni riservate, anche quando viene pubblicato in un sito con autorizzazioni aperte.
  
Innanzitutto, abilitare e configurare IRM per la raccolta documenti della raccolta siti dirigenti.  
  
1. In una nuova scheda del browser, digitare l'URL della raccolta siti dirigenti.
    
2. Fare clic su **Documenti**.
    
3. In alto a destra, fare clic sull'icona Impostazioni, quindi selezionare **Impostazioni raccolta**.
    
4. Nella pagina **Impostazioni**, in **Autorizzazioni e gestione**, fare clic su **Information Rights Management**.
    
5. Nella pagina **Information Rights Management Settings**:
    
  - Selezionare **Limita le autorizzazioni per i documenti di questa raccolta in fase di download**.
    
  - Per **Creare un titolo per i criteri di autorizzazione**, digitare **Dirigenti**.
    
  - Per **Aggiungere una descrizione per i criteri di autorizzazione**, digitare **IRM per dirigenti**.
    
6. Fare clic su **Mostra opzioni**.
    
7. In **Configurare altre impostazioni della libreria IRM**, selezionare **Non consentire il caricamento di documenti che non supportano IRM**.
    
8. In **Configura diritti di accesso al documento**, selezionare **Consenti ai visualizzatori di stampare** e **Consenti ai visualizzatori di scrivere in una copia del documento scaricato**.
    
9. In **Imposta intervallo di protezione e credenziali di gruppo**selezionare **Consenti protezione gruppo. Gruppo predefinito**e quindi digitare **dirigenti**.
    
10. Fare clic su **OK**.
    
Successivamente, agendo da CEO, si carica un nuovo documento nella cartella documenti Dirigenti, lo si scarica, quindi lo si carica accidentalmente nella cartella documenti Vendite.
  
1. Aprire la cartella locale in cui è stato salvato il documento **SensitiveData-BeforeIRM.docx**.
    
2. 	Fare clic con il pulsante destro del mouse su **SensitiveData-BeforeIRM.docx**, quindi fare clic su **Copia**.
    
3. Fare clic con il pulsante destro del mouse sulla cartella, quindi scegliere **Incolla**.
    
4. Rinominare il nuovo file **SensitiveData-BeforeIRM-Copy. docx** in **SensitiveData-AfterIRM. docx**.
    
5. Nella scheda **Microsoft Office Home** nel browser, fare clic sull'icona utente in alto a destra, quindi fare clic su **Disconnetti**.
    
6. Passare a [https://admin.microsoft.com](https://admin.microsoft.com).
    
7. Nella pagina **Accesso a Office 365**, fare clic sul nome dell'account CEO, digitare la relativa password, quindi fare clic su **Accedi**.
    
8. In una nuova scheda del browser, digitare l'URL della raccolta siti dirigenti.
    
9. Nella pagina **Documenti**, fare clic su **Carica**, specificare il documento **SensitiveData-AfterIRM.docx** nella cartella locale, quindi fare clic su **Apri**.
    
10. Selezionare il nuovo documento **SensitiveData-AfterIRM.docx** nella pagina **Documenti**, fare clic sui puntini di sospensione (…) nella barra dei menu, quindi fare clic su **Scarica**.
    
11. Quando richiesto, salvare il documento **SensitiveData-AfterIRM.docx** nella cartella locale, sovrascrivendo la versione originale.
    
12. Chiudere la scheda per la pagina **Documenti**.
    
13. In una nuova scheda del browser, digitare l'URL della raccolta siti di vendita.
    
14. Fare clic su **Documenti**.
    
15. Nella pagina **Documenti**, fare clic su **Carica**, specificare il documento **SensitiveData-AfterIRM.docx** nella cartella locale, quindi fare clic su **Apri**.
    
16. Chiudere le schede **Raccolta siti vendite** e **SharePoint**.
    
Successivamente, agendo da utente normale, provare ad accedere al documento **SensitiveData-AfterIRM.docx** nella cartella documenti Vendite.
  
1. Nella scheda **Microsoft Office Home** nel browser, fare clic sull'icona utente in alto a destra, quindi fare clic su **Disconnetti**.
    
2. Passare a [https://admin.microsoft.com](https://admin.microsoft.com).
    
3. Nella pagina di **accesso a Office 365** fare clic sul nome dell'account User5, digitare la relativa password, quindi fare clic su **Accedi**.
    
4. In una nuova scheda del browser, digitare l'URL della raccolta siti di vendita.
    
5. Fare clic su **Documenti**.
    
6. Nella pagina **Documenti**, aprire il documento **SensitiveData-AfterIRM.docx**. 
    
    Verrà visualizzato un messaggio in cui viene indicato che "spiacenti, non è possibile aprire il documento perché è protetto da Information Rights Management (IRM)". 
    
7. Selezionare **Modifica in Word**. Viene chiesto se si desidera aprire il file. Fare clic su **Sì**.
    
8. Viene richiesto di accedere. Digitare il nome dell'account utente dell'account User5, quindi fare clic su **Avanti**.
    
9. Verrà chiesto di fornire la password. Digitare la password dell'account User5, quindi fare clic su **Accedi**.  
    
    Verrà visualizzato un messaggio di errore che informa: "L'utente non dispone delle credenziali per aprire il documento".
    
10. Fare clic su **No**.
    
Un altro modo per visualizzare la protezione IRM consiste nell'esaminare i file nella cartella locale. **SensitiveData-AfterIRM.docx** deve essere molto più grande del file **SensitiveData-BeforeIRM.docx**. Il file **SensitiveData-AfterIRM.docx** è crittografato e vi sono state aggiunte le informazioni di protezione IRM.
  
## <a name="see-also"></a>Vedere anche

[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente di sviluppo/test della configurazione di base](base-configuration-dev-test-environment.md)
  
[Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)


