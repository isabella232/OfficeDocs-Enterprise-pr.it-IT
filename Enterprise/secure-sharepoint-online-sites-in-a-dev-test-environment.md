---
title: Proteggere i siti di SharePoint Online in un ambiente di sviluppo e di testing
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.custom: Strat_O365_Enterprise
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: 'Riepilogo: Creare siti di team di SharePoint Online pubblici, privati, riservati e altamente riservati in un ambiente di sviluppo e di testing.'
ms.openlocfilehash: 55adc5f7cdbf197acf3ca68623139c01912c602f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a>Proteggere i siti di SharePoint Online in un ambiente di sviluppo e di testing

 **Riepilogo:** Creare siti di team di SharePoint Online pubblici, privati, riservati e altamente riservati in un ambiente di sviluppo e di testing.
  
In questo articolo vengono fornite istruzioni dettagliate per creare un ambiente di sviluppo e di testing che include quattro diversi tipi di siti del team SharePoint Online per la soluzione di [file e siti di SharePoint Online sicura](secure-sharepoint-online-sites-and-files.md) .
  
![Tutti i quattro siti del team nell’ambiente di sviluppo/test protetto di SharePoint Online.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
Utilizzare questo ambiente di sviluppo e di testing per sperimentare i comportamenti di protezione delle informazioni e l'ottimizzazione delle impostazioni in base alle esigenze prima della distribuzione di SharePoint Online siti del team nell'ambiente di produzione.
  
## <a name="phase-1-create-your-devtest-environment"></a>Fase 1: Creare l'ambiente di sviluppo e di testing

In questa fase è ottenere sottoscrizioni di valutazione di Office 365 e mobilità aziendale + sicurezza per le organizzazioni fittizia.
  
Per prima cosa, seguire le istruzioni nella **fase 2** dell' [ambiente di sviluppo e di testing di Office 365](office-365-dev-test-environment.md).
  
Successivamente, Esegui l'iscrizione per la sottoscrizione di prova EMS e come aggiungerla alla stessa organizzazione la sottoscrizione di prova di Office 365.
  
1. Se necessario, accedere al portale di Office 365 con le credenziali dell'account amministratore globale della sottoscrizione di prova. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Fare clic sul riquadro **Amministratore**.
    
3. Scheda di **interfaccia di amministrazione di Office** nel browser, nel riquadro di spostamento sinistra fare clic su **fatturazione > servizi di acquisto**.
    
4. Nella pagina **servizi di acquisto** individuare l'elemento di **sicurezza E5 + mobilità aziendale** . Posizionare il puntatore del mouse su di esso e fare clic su **Start versione di valutazione gratuita**.
    
5. Nella pagina **Conferma l'ordine**, fare clic su **Prova adesso**.
    
6. Nella pagina **Ricevuta ordine**, fare clic su **Continua**.
    
Successivamente, abilitare la mobilità aziendale + sicurezza E5 licenza per l'account amministratore globale.
  
1. Nella scheda **Centro di amministrazione di Office 365** nel browser, nel riquadro di spostamento sinistra fare clic su **utenti > utenti attivi**.
    
2. Fare clic sull'account di amministratore globale e quindi fare clic su **Modifica** per **le licenze del prodotto**.
    
3. Nel riquadro di **licenze per i prodotti** , attivare la licenza del prodotto per la **mobilità aziendale + E5 di sicurezza** per **in**, fare clic su **Salva** e quindi fare doppio clic su **Chiudi** .
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a>Fase 2: Creare e configurare i gruppi di Azure Active Directory (AD) e gli utenti

In questa fase, creare e configurare i gruppi di Azure Active Directory e gli utenti per l'organizzazione fittizio.
  
Creare innanzitutto un insieme di gruppi per una tipica organizzazione con il portale di Azure.
  
1. Creare una scheda separata del browser e andare al portale di Azure [all'https://portal.azure.com](https://portal.azure.com). Se necessario, accedere con le credenziali dell'account amministratore globale per la sottoscrizione di valutazione di Office 365 E5.
    
2. Nel portale di Azure, fare clic su **Azure Active Directory > utenti e gruppi > tutti i gruppi di**.
    
3. Su blade **tutti i gruppi** , fare clic su **+ nuovo gruppo**.
    
4. Su blade **gruppo** :
    
  - Tipo **Famiglia di prodotti C** nella **casella Nome**.
    
  - In **appartenenza**, selezionare **assegnato** .
    
  - Fare clic su **Sì** per **caratteristiche di attivare Office**.
    
5. Fare clic su **Crea**e quindi chiudere blade **gruppo** .
    
6. Ripetere i passaggi da 3 a 5 per i nomi dei gruppi seguenti:
    
  - Personale IT
    
  - Personale di ricerca
    
  - Regolare personale
    
  - Personale di marketing
    
  - Personale addetto alle vendite
    
7. Tenere aperto il browser nella scheda portal Azure.
    
Successivamente, si configurano le licenze automatiche in modo che ai membri dei gruppi vengano automaticamente assegnate le licenze per le sottoscrizioni di Office 365 ed EMS.
  
1. Nel portale di Azure, fare clic su **Azure Active Directory > licenze > tutti i prodotti**.
    
2. Nell'elenco, selezionare **mobilità aziendale + sicurezza E5** e **Office 365 Enterprise E5**e quindi fare clic su **Assegna**.
    
3. In blade **assegnare licenze** , fare clic su **utenti e gruppi**.
    
4. Nell'elenco dei gruppi, selezionare quanto segue:
    
  - C-famiglia di prodotti
    
  - Personale IT
    
  - Personale di ricerca
    
  - Regolare personale
    
  - Personale di marketing
    
  - Personale addetto alle vendite
    
5. Fare clic su **Seleziona**e quindi fare clic su **Assegna**.
    
6. Chiudere la scheda del portale di Azure nel browser.
    
Quindi, si [Connetti con il modulo di Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
Immettere il nome dell'organizzazione, la posizione e una password comune e quindi eseguire questi comandi dal prompt dei comandi di PowerShell o integrata Script Environment (ISE) per creare gli account utente e aggiungerli ai rispettivi gruppi:
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Research staff"
$userNames=@("Researcher1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Regular staff"
$userNames=@("Regular1", "Regular2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Sales staff"
$userNames=@("SalesPerson1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> L'utilizzo di una password comune in questo caso è per rendere automatica e facile la configurazione per un ambiente di sviluppo/test. Non è una scelta consigliata per sottoscrizioni di produzione. 
  
Utilizzare la procedura seguente per verificare che le licenze basate su gruppo funzioni correttamente.
  
1. Nella scheda **Home page di Microsoft Office** del browser, fare clic su tessera di **amministrazione** .
    
2. Dalla nuova scheda di **interfaccia di amministrazione di Office** del browser, fare clic su **utenti**.
    
3. Nell'elenco di utenti, fare clic su **amministratore delegato**.
    
4. Nel riquadro in cui sono elencati le proprietà dell'account utente **amministratore delegato** , verificare è stato assegnato le licenze **Enterprise mobilità + sicurezza E5** e **Office 365 Enterprise E5** (nelle **licenze per i prodotti**).
    
## <a name="phase-3-create-office-365-labels"></a>Fase 3: Creare etichette di Office 365

In questa fase, vengono create le etichette per i diversi livelli di sicurezza per cartelle di documenti dei siti del team di SharePoint Online.
  
1. Se necessario, utilizzare un'istanza del browser Internet privata e accedere al portale di Office 365 con l'account amministratore globale della sottoscrizione di prova di Office 365 E5. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Nella scheda **Home page di Microsoft Office** , fare clic su tessera di **amministrazione** .
    
3. Scheda di **interfaccia di amministrazione di Office** nuovo del browser fare clic su **Admin Center > sicurezza &amp; conformità**.
    
4. Dalla nuova **Home - sicurezza &amp; conformità** scheda del browser, fare clic su **classificazioni > etichette**.
    
5. Dal **Home > etichette** riquadro, fare clic su **Crea un'etichetta**.
    
6. Nel riquadro **nome dell'etichetta** digitare **Interno pubblica**e quindi fare clic su **Avanti**.
    
7. Nel riquadro di **impostazioni dell'etichetta** , fare clic su **Avanti**.
    
8. Nel riquadro di **Rivedere le impostazioni** , fare clic su **Crea l'etichetta**e quindi fare clic su **Chiudi**.
    
9. Ripetere i passaggi 5-8 per queste etichette aggiuntive:
    
  - Privato
    
  - Riservato
    
  - Dati estremamente riservati
    
10. Dal **Home > etichette** riquadro, fare clic su **pubblica etichette**.
    
11. Nel riquadro di **scegliere le etichette per la pubblicazione** , fare clic su **etichette scegliere per la pubblicazione**.
    
12. Nel riquadro **scegliere etichette** , fare clic su **Aggiungi** e selezionare tutte le etichette di quattro.
    
13. Fare clic su **Chiudi**.
    
14. Nel riquadro di **scegliere le etichette per la pubblicazione** , fare clic su **Avanti**.
    
15. Nel riquadro **scegliere percorsi** , fare clic su **Avanti**.
    
16. Nel riquadro **nome del criterio** digitare **esempio organizzazione** nella casella **nome**e quindi fare clic su **Avanti**.
    
17. Nel riquadro di **Rivedere le impostazioni** , fare clic su **etichette pubblica**e quindi fare clic su **Chiudi**.
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a>Fase 4: Creare i siti del team di SharePoint Online

In questa fase, creare e configurare i quattro tipi di siti di team di SharePoint Online per l'organizzazione di esempio.
  
### <a name="organization-wide-team-site"></a>Sito del team di livello di organizzazione

Per creare un sito del team di SharePoint Online pubblico di base, eseguire le operazioni seguenti:
  
1. Se necessario, utilizzare un browser nel computer locale e accedere al portale di Office 365 utilizzando l'account amministratore globale. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Nell'elenco delle sezioni, fare clic su **SharePoint**.
    
3. Nella scheda **SharePoint** nuovo nel browser, fare clic su **Crea sito +**.
    
4. Nella pagina **Crea sito** fare clic su **sito del Team**.
    
5. In **nome sito**digitare **a livello di organizzazione**. 
    
6. Nella **descrizione del sito del Team**, digitare **il sito di SharePoint per l'intera organizzazione**.
    
7. In **impostazioni di Privacy**, selezionare **Pubblica - tutti gli utenti dell'organizzazione possono accedere al sito**e quindi fare clic su **Avanti**.
    
8. Nella **che si desidera aggiungere?** riquadro, fare clic su **Fine**.
    
Configurare quindi la cartella documenti del sito del team ampia organizzazione per l'etichetta interno pubblica.
  
1. Nella scheda **Home page di livello di organizzazione** del browser fare clic su **documenti**.
    
2. Fare clic sull'icona impostazioni e quindi fare clic su **Impostazioni raccolta**.
    
3. Nella sezione **autorizzazioni e gestione**, fare clic su **Applica etichetta agli elementi della raccolta**.
    
4. In **Impostazioni si applicano etichetta**, selezionare **Interno pubblica**e quindi fare clic su **Salva**.
    
Di seguito è riportata la configurazione risultante.
  
![Protezione di livello di base per il sito del team di SharePoint Online pubblico a livello dell’organizzazione.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a>Sito team di progetto 1

Per creare un sito del team previsto privato SharePoint Online per un progetto all'interno dell'organizzazione, eseguire le operazioni seguenti:
  
1. Se necessario, utilizzare un browser nel computer locale e accedere al portale di Office 365 utilizzando l'account amministratore globale. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Nell'elenco delle sezioni, fare clic su **SharePoint**.
    
3. Nella scheda **SharePoint** nuovo nel browser, fare clic su **Crea sito +**.
    
4. Nella pagina **Crea sito** fare clic su **sito del Team**.
    
5. In **nome sito**digitare **Project 1**. 
    
6. Nella **descrizione del sito del Team,** digitare **il sito di SharePoint per il progetto 1**.
    
7. **Le impostazioni di Privacy**, selezionare **privato: solo membri possono accedere al sito**e quindi fare clic su **Avanti**.
    
8. Nella **che si desidera aggiungere?** riquadro, fare clic su **Fine**.
    
Configurare quindi la cartella documenti del sito del team di progetto 1 per l'etichetta privata.
  
1. Nella scheda **progetto 1 Home** del browser fare clic su **documenti**.
    
2. Fare clic sull'icona impostazioni e quindi fare clic su **Impostazioni raccolta**.
    
3. Nella sezione **autorizzazioni e gestione**, fare clic su **Applica etichetta agli elementi della raccolta**.
    
4. In **Applica impostazioni etichetta**, selezionare **privata**e quindi fare clic su **Salva**.
    
Di seguito è riportata la configurazione risultante.
  
![Protezione di livello di base per il sito del team di SharePoint Online privato Project1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a>Sito del team campagne di marketing

Per creare un livello riservati isolato SharePoint Online sito del team di risorse campagne di marketing, eseguire le operazioni seguenti:
  
1. Utilizzando un browser nel computer locale, accedere al portale di Office 365 utilizzando l'account amministratore globale. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Nell'elenco delle sezioni, fare clic su **SharePoint**.
    
3. Nella scheda **SharePoint** nuovo nel browser, fare clic su **Crea sito +**.
    
4. Nella pagina **Crea sito** fare clic su **sito del Team**.
    
5. **Nome del sito del Team**, digitare **campagne di Marketing**.
    
6. Nella **descrizione del sito del Team**, digitare **sito di SharePoint per risorse campagne di marketing (maiuscole/minuscole)**.
    
7.  **Le impostazioni di Privacy**, selezionare **privato: solo membri possono accedere al sito**e quindi fare clic su **Avanti**.
    
8. Nella **che si desidera aggiungere?** riquadro, fare clic su **Fine**.
    
9. Nella scheda **campagne di Marketing** nuovo nel browser, nella barra degli strumenti, fare clic sull'icona impostazioni e quindi fare clic su **autorizzazioni sito**.
    
10. Nel riquadro **autorizzazioni sito** fare clic su **impostazioni di autorizzazioni avanzate**.
    
11. Nella scheda **autorizzazioni** nuova nel browser, fare clic su **Impostazioni richieste di accesso**.
    
12. Nella finestra di dialogo **Impostazioni richieste di accesso** , deselezionare le caselle di controllo **Consenti ai membri di condividere il sito e i singoli file e cartelle** e i **membri Consenti per invitare altre persone al gruppo membri del sito** , digitare **ITAdmin1 @**\<il nome dell'organizzazione >**. onmicrosoft.com** di **inviare tutte le richieste di accesso**, quindi scegliere **OK**.
    
13. Fare clic su **campagne di Marketing membri** nell'elenco.
    
14. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
15. Nella finestra di dialogo **Condividi** digitare **Marketing staff**, selezionarlo e fare clic su **Condividi**.
    
16. Ripetere i passaggi 14 e 15 per l'account utente **Researcher1** .
    
17. Fare clic sul pulsante Indietro del browser.
    
18. Nell'elenco, fare clic su **campagne di Marketing proprietari** .
    
19. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
20. Nella finestra di dialogo **condivisione** digitare **il personale IT**, selezionarlo e fare clic su **Condividi**.
    
21. Fare clic sul pulsante Indietro del browser.
    
22. Chiudere la scheda **utenti e gruppi** nel browser, fare clic sulla scheda **Home campagne di Marketing** nel browser e quindi chiudere il riquadro **autorizzazioni sito** .
    
Ecco i risultati della configurazione delle autorizzazioni:
  
- Gruppo di SharePoint **Membri di campagne di Marketing** contiene solo il gruppo di **campagne di Marketing** (che include l'account utente amministratore globale), il gruppo **Marketing staff** (che contiene l'utente Marketing1 e Marketing2 account) e l'account utente **Researcher1** .
    
- Il gruppo di SharePoint **Proprietari di campagne di Marketing** contiene solo il gruppo di **personale IT** (che include solo gli account utente ITAdmin1 e ITAdmin2).
    
- Gruppo di SharePoint **Visitatori di campagne di Marketing** non contiene gruppi o gli account utente.
    
- Membri non possono modificare le autorizzazioni a livello di sito (questa operazione può essere eseguita solo dai membri del gruppo **Proprietari di campagne di Marketing** ).
    
- Altri account utente non possono accedere al sito o alle sue risorse, ma possono richiedere l'accesso al sito, che invierà un'e-mail alla cassetta postale dell'account utente ITAdmin1.
    
Configurare quindi la cartella documenti del sito del team campagne di Marketing per l'etichetta riservato.
  
1. Nella scheda **Home campagne di Marketing** del browser fare clic su **documenti**.
    
2. Fare clic sull'icona impostazioni e quindi fare clic su **Impostazioni raccolta**.
    
3. Nella sezione **autorizzazioni e gestione**, fare clic su **Applica etichetta agli elementi della raccolta**.
    
4. In **Applica impostazioni etichetta**, selezionare **riservati**e quindi fare clic su **Salva**.
    
Successivamente, configurare un criterio di criterio DLP perdita di dati che informa gli utenti quando si condivide un documento in un sito del team di SharePoint Online con etichetta sensibile, che include il sito campagne di Marketing, all'esterno dell'organizzazione.
  
1. Nella scheda **Home page di Microsoft Office** nel browser, fare clic sul **protezione &amp; conformità** affiancate.
    
2. Nel nuovo computer **protezione &amp; conformità** nel browser, fare clic **prevenzione della perdita di dati > criteri**.
    
3. Nel riquadro di **prevenzione della perdita di dati** , fare clic su **+ Crea un criterio**.
    
4. Nella **iniziare con un modello o creare un criterio personalizzato** riquadro, fare clic su **personalizzata**e quindi fare clic su **Avanti**.
    
5. Nel riquadro **nome del criterio** digitare **siti del team di SharePoint Online riservati etichetta** **nome**e quindi fare clic su **Avanti**.
    
6. Nel riquadro **scegliere percorsi** , fare clic su **Seleziona manualmente percorsi specifici**e quindi fare clic su **Avanti**.
    
7. Nell'elenco delle posizioni, disattivare i percorsi di **posta elettronica di Exchange** e **gli account di OneDrive** e quindi fare clic su **Avanti**.
    
8. Nel riquadro di **personalizzare i tipi di informazioni riservate che si desidera proteggere** , fare clic su **Modifica**.
    
9. Nel riquadro **scegliere i tipi di contenuto per la protezione** , fare clic su **Aggiungi** nella casella a discesa e quindi fare clic su **etichette**.
    
10. Nel riquadro **etichette** fare clic su **+ Aggiungi**, selezionare l'etichetta **riservati** , fare clic su **Aggiungi**e quindi fare clic su **Fine**.
    
11. Nel riquadro **scegliere i tipi di contenuto per la protezione** , fare clic su **Salva**.
    
12. Nel riquadro di **personalizzare i tipi di informazioni riservate che si desidera proteggere** , fare clic su **Avanti**.
    
13. Nella **Selezionare l'operazione da eseguire se si rileva informazioni riservate?** riquadro, fare clic su **Personalizza la descrizione e posta elettronica**.
    
14. Nel riquadro **suggerimenti sui criteri di personalizzazione e notifiche tramite posta elettronica** , fare clic su **Personalizza il testo del suggerimento criteri**.
    
15. Nella casella di testo digitare o incollare negli articoli seguenti:
    
  - Per condividere con un utente esterno all'organizzazione, scaricare il file e quindi aprirlo. Fare clic su File, Proteggi documento, Crittografa con password, quindi specificare una password complessa. Inviare la password in un'e-mail separata o con altri mezzi di comunicazione.
    
16. Fare clic su **OK**.
    
17. Nella **Selezionare l'operazione da eseguire se si rileva informazioni riservate?** riquadro, deselezionare la casella di controllo **Blocca la condivisione degli utenti e limitare l'accesso al contenuto condiviso** e quindi fare clic su **Avanti**.
    
18. Nella **si desidera attivare le operazioni criteri o di testing prima?** riquadro, fare clic su **Sì, attivarlo immediatamente**e quindi fare clic su **Avanti**.
    
19. Nel riquadro di **Rivedere le impostazioni** , fare clic su **Crea**e quindi fare clic su **Chiudi**.
    
Di seguito è riportata la configurazione risultante.
  
![Protezione di livello riservato per il sito del team di SharePoint Online isolato delle campagne di marketing.](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a>Sito team strategia aziendale

Per creare un sito del team di SharePoint Online isolato a livello di altamente riservato per risorse aziendali strategico dei dirigenti amministratore dell'organizzazione, eseguire le operazioni seguenti:
  
1. Se necessario, utilizzare un browser nel computer locale e accedere al portale di Office 365 utilizzando l'account amministratore globale. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Nell'elenco delle sezioni, fare clic su **SharePoint**.
    
3. Nella scheda **SharePoint** nuovo nel browser, fare clic su **Crea sito +**.
    
4. Nella pagina **Crea sito** fare clic su **sito del Team**.
    
5. **Nome del sito del Team**, digitare **strategia aziendale**.
    
6. Nella **descrizione del sito del Team**, digitare **il sito di SharePoint per la strategia aziendale (altamente riservato)**.
    
7.  **Le impostazioni di Privacy**, selezionare **privato: solo membri possono accedere al sito**e quindi fare clic su **Avanti**.
    
8. Nella **che si desidera aggiungere?** riquadro, fare clic su **Fine**.
    
9. Nella scheda **strategia società** nuovo nel browser, nella barra degli strumenti, fare clic sull'icona impostazioni e quindi fare clic su **autorizzazioni sito**.
    
10. Nel riquadro **autorizzazioni sito** fare clic su **impostazioni di autorizzazioni avanzate**.
    
11. Nella scheda **autorizzazioni** nuova nel browser, fare clic su **Impostazioni richieste di accesso**.
    
12. Nella finestra di dialogo **Impostazioni richieste di accesso** , deselezionare **Consenti ai membri di condividere il sito e i singoli file e cartelle** e **Consenti ai membri per invitare altre persone al gruppo membri del sito** (in modo che tutti i tre caselle di controllo è deselezionate), quindi fare clic su ** OK**.
    
13. Fare clic su **strategia società membri** nell'elenco.
    
14. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
15. Nella finestra di dialogo **Condividi** digitare **C famiglia di prodotti**, selezionarlo e quindi fare clic su **Condividi**.
    
16. Nell'elenco, fare clic su **strategia società proprietari** .
    
17. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
18. Nella finestra di dialogo **condivisione** digitare **il personale IT**, selezionarlo e fare clic su **Condividi**.
    
19. Fare clic sul pulsante Indietro del browser.
    
20. Chiudere la scheda **utenti e gruppi** nel browser, fare clic sulla scheda **Home page della strategia - società** nel browser e quindi chiudere il riquadro **autorizzazioni sito** .
    
Ecco i risultati della configurazione delle autorizzazioni:
  
- Il gruppo di SharePoint **Membri strategia aziendale** contiene solo il gruppo **C famiglia di prodotti** (che include solo gli account utente amministratore delegato, responsabile finanziario e CIO) e del gruppo **strategia società** (che contiene solo l'account utente amministratore globale).
    
- Gruppo di SharePoint **Proprietari di strategia aziendale** contiene solo il gruppo di **personale IT** (che include solo gli account utente ITAdmin1 e ITAdmin2).
    
- Gruppo di SharePoint **Visitatori di strategia società** non contiene gruppi o gli account utente.
    
- Membri non possono modificare le autorizzazioni a livello di sito (ciò può essere eseguita solo dai membri del gruppo **Proprietari di strategia aziendale** ).
    
- Altri account utente non può accedere al sito e le relative risorse o richiedere l'accesso al sito. Autorizzazioni aggiuntive per il sito devono essere eseguite dall'amministratore globale o da un membro del gruppo **Proprietari di strategia aziendale** .
    
Configurare quindi la cartella documenti del sito del team aziendale strategia per l'etichetta altamente riservati.
  
1. Nella scheda **Home page di strategia aziendale** del browser fare clic su **documenti**.
    
2. Fare clic sull'icona impostazioni e quindi fare clic su **Impostazioni raccolta**.
    
3. Nella sezione **autorizzazioni e gestione**, fare clic su **Applica etichetta agli elementi della raccolta**.
    
4. In **Applica impostazioni etichetta**, selezionare **Altamente riservati**e quindi fare clic su **Salva**.
    
Quindi, configurare un criterio DLP che gli utenti blocchi quando si condivide un documento in un sito del team di SharePoint Online con etichetta altamente riservati, che include il sito strategia aziendale, all'esterno dell'organizzazione.
  
1. Se necessario, utilizzare un browser nel computer locale e accedere al portale di Office 365 con un account che dispone del ruolo di amministratore della sicurezza o amministratore azienda. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Nella scheda **Home page di Microsoft Office** nel browser, fare clic sul **protezione &amp; conformità** affiancate.
    
3. Nel nuovo computer **protezione &amp; conformità** nel browser, fare clic **prevenzione della perdita di dati > criteri**.
    
4. Nel riquadro di **prevenzione della perdita di dati** , fare clic su **+ Crea un criterio**.
    
5. Nella **iniziare con un modello o creare un criterio personalizzato** riquadro, fare clic su **personalizzata**e quindi fare clic su **Avanti**.
    
6. Nel riquadro **nome del criterio** digitare **siti del team di SharePoint Online di altamente riservati etichetta** **nome**e quindi fare clic su **Avanti**.
    
7. Nel riquadro **scegliere percorsi** , fare clic su **Seleziona manualmente percorsi specifici**e quindi fare clic su **Avanti**.
    
8. Nell'elenco delle posizioni, disattivare i percorsi di **posta elettronica di Exchange** e **gli account di OneDrive** e quindi fare clic su **Avanti**.
    
9. Nel riquadro di **personalizzare i tipi di informazioni riservate che si desidera proteggere** , fare clic su **Modifica**.
    
10. Nel riquadro **scegliere i tipi di contenuto per la protezione** , fare clic su **Aggiungi** nella casella a discesa e quindi fare clic su **etichette**.
    
11. Nel riquadro **etichette** fare clic su **+ Aggiungi**, selezionare l'etichetta **Altamente riservati** , fare clic su **Aggiungi**e quindi fare clic su **Fine**.
    
12. Nel riquadro **scegliere i tipi di contenuto per la protezione** , fare clic su **Salva**.
    
13. Nel riquadro di **personalizzare i tipi di informazioni riservate che si desidera proteggere** , fare clic su **Avanti**.
    
14. Nella **Selezionare l'operazione da eseguire se si rileva informazioni riservate?** riquadro, fare clic su **Personalizza la descrizione e posta elettronica**.
    
15. Nel riquadro **suggerimenti sui criteri di personalizzazione e notifiche tramite posta elettronica** , fare clic su **Personalizza il testo del suggerimento criteri**.
    
16. Nella casella di testo digitare o incollare negli articoli seguenti:
    
  - Per condividere con un utente esterno all'organizzazione, scaricare il file e quindi aprirlo. Fare clic su File, Proteggi documento, Crittografa con password, quindi specificare una password complessa. Inviare la password in un'e-mail separata o con altri mezzi di comunicazione.
    
17. Fare clic su **OK**.
    
18. Nella **Selezionare l'operazione da eseguire se si rileva informazioni riservate?** riquadro, selezionare **Richiedi motivazione aziendale per eseguire l'override**e quindi fare clic su **Avanti**.
    
19. Nella **si desidera attivare le operazioni criteri o di testing prima?** riquadro, fare clic su **Sì, attivarlo immediatamente**e quindi fare clic su **Avanti**.
    
20. Nel riquadro di **Rivedere le impostazioni** , fare clic su **Crea**e quindi fare clic su **Chiudi**.
    
Successivamente, seguire le istruzioni in [Attivare Azure RMS con l'interfaccia di amministrazione di Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
Configurare quindi la protezione delle informazioni di Azure con un nuovo criterio con ambito e secondaria etichetta per la protezione e autorizzazioni con le operazioni seguenti:
  
1. Accedere al portale di Office 365 con un account che dispone del ruolo Amministratore della sicurezza oppure Amministratore della società. Per informazioni, vedere [Dove accedere a Office 365 per le aziende](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. In una scheda a parte del browser, accedere al portale di Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Se è la prima volta che viene configurato Azure Information Protection, consultare queste [istruzioni](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. Nel riquadro dell'elenco, fare clic su **Ulteriori servizi**, digitare **Informazioni**, quindi fare clic su **Azure Information Protection**.
    
5. Nel pannello **Azure Information Protection**, fare clic su **Criteri con ambiti > + Aggiungi un nuovo criterio**.
    
6. Digitare **CompanyStrategy** **nome del criterio** e l' **etichetta per i documenti nel sito del team strategia aziendale** nella **casella Descrizione**.
    
7. Fare clic su **Selezionare gli utenti o gruppi di ottenere il criterio > utenti/gruppi**, quindi selezionare **C famiglia di prodotti**.
    
8. Fare clic su **Seleziona > OK**.
    
9. Per l'etichetta **Estremamente riservato**, fare clic sui puntini di sospensione (…), quindi su **Aggiungi un'etichetta secondaria**.
    
10. Digitare un nome per l'etichetta secondaria in **Nome** e una descrizione dell'etichetta in **Descrizione**.
    
11. In **Configurare le autorizzazioni per documenti e messaggi di posta elettronica contenenti questa etichetta** fare clic su **Proteggi**.
    
12. Nella sezione **Protezione**, fare clic su **Azure (chiave cloud)**.
    
13. Nel pannello **Protezione**, in **Impostazioni di protezione**, fare clic su **+ Aggiungi autorizzazioni**.
    
14. Nel pannello **Aggiungi autorizzazioni**, in **Specifica utenti e gruppi** fare clic su **+ Sfoglia la directory**.
    
15. Nel riquadro **AAD utenti e gruppi** selezionare **C famiglia di prodotti**e quindi fare clic su **Seleziona**.
    
16. In **Scegli autorizzazioni dal set di impostazioni**, deselezionare le caselle di controllo **Stampa**, **Copia ed estrai il contenuto** e **Inoltra**.
    
17. Fare due volte clic su **OK**.
    
18. Nel pannello **Etichetta secondaria** fare clic su **Salva**.
    
19. Chiudere il pannello del nuovo criterio con ambito.
    
20. Su blade **Azure Information protection - criteri con ambiti** , fare clic su **pubblica**e quindi fare clic su **Sì**.
    
Per proteggere un documento con Azure Information Protection and questa nuova etichetta, è necessario [installare il client per la protezione delle informazioni di Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) in un computer di test, installare Office dal portale di Office 365 e quindi accedere da Microsoft Word con un account nel ** Famiglia di prodotti C** group dell'abbonamento prova.
  
Di seguito è riportata la configurazione risultante.
  
![Protezione di livello estremamente riservato per un sito del team di SharePoint Online isolato di strategia aziendale.](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
È ora possibile creare documenti in questi quattro siti e verificare l'accesso a tali con diversi account utente nella sottoscrizione di prova.
  
Di seguito è la configurazione globale per tutti i siti dei team quattro SharePoint Online.
  
![Tutti i quattro siti del team nell’ambiente di sviluppo/test protetto di SharePoint Online.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a>Passaggio successivo

Quando si è pronti per la distribuzione di produzione di protezione dei siti SharePoint Online, vedere [file e siti di SharePoint Online sicura](secure-sharepoint-online-sites-and-files.md) per informazioni dettagliate e collegamenti ad articoli sulla distribuzione dettagliate.
  
## <a name="see-also"></a>Vedere anche

[Protezione di file e siti di SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Soluzioni di sicurezza](security-solutions.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)
  
[Guida sulla sicurezza Microsoft per organizzazioni che si occupano della campagna politica, no profit e altre organizzazioni agili](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




