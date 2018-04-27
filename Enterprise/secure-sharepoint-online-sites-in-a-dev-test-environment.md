---
title: Proteggere i siti di SharePoint Online in un ambiente di sviluppo/test
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: 'Riepilogo: Creare siti di team di SharePoint Online pubblici, privati, riservati e altamente riservati in un ambiente di sviluppo e di testing.'
ms.openlocfilehash: 8c02f1416cb00150e68dcc27dc7afb41bf82ed21
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a>Proteggere i siti di SharePoint Online in un ambiente di sviluppo/test

 **Riepilogo:** Creare siti di team di SharePoint Online pubblici, privati, riservati e altamente riservati in un ambiente di sviluppo e di testing.
  
In questo articolo vengono fornite istruzioni dettagliate per creare un ambiente di sviluppo e di testing che include quattro diversi tipi di siti del team SharePoint Online per la soluzione di [file e siti di SharePoint Online sicura](secure-sharepoint-online-sites-and-files.md) .
  
![Tutti i quattro siti del team nell’ambiente di sviluppo/test protetto di SharePoint Online.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
Usare questo ambiente di sviluppo e test per sperimentare i comportamenti della protezione delle informazioni e ottimizzare le impostazioni in base alle esigenze specifiche prima di distribuire siti del team di SharePoint Online nell'ambiente di produzione.
  
## <a name="phase-1-create-your-devtest-environment"></a>Fase 1: Creare l'ambiente di sviluppo/test

In questa fase si ottengono le sottoscrizioni di valutazione per Office 365 ed Enterprise Mobility + Security per un'organizzazione fittizia.
  
Per prima cosa, seguire le istruzioni della **fase 2** nell'articolo relativo all'[ambiente di sviluppo e test di Office 365](office-365-dev-test-environment.md).
  
Successivamente, Esegui l'iscrizione per la sottoscrizione di prova EMS e come aggiungerla alla stessa organizzazione la sottoscrizione di prova di Office 365.
  
1. Se necessario, accedere al portale di Office 365 con le credenziali dell'account amministratore globale della sottoscrizione di prova. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Scegliere il riquadro **Amministrazione**.
    
3. Nella scheda **Interfaccia di amministrazione di Office** del browser fare clic su **Fatturazione > Servizi di acquisto** nel riquadro di spostamento di sinistra.
    
4. Nella pagina **servizi di acquisto** individuare l'elemento di **sicurezza E5 + mobilità aziendale** . Posizionare il puntatore del mouse su di esso e fare clic su **Start versione di valutazione gratuita**.
    
5. Nella pagina **Conferma l'ordine**, fare clic su **Prova adesso**.
    
6. Nella pagina **Ricevuta ordine** fare clic su **Continua**.
    
Abilitare quindi la licenza Enterprise Mobility + Security E5 per l'account amministratore globale.
  
1. Nella scheda **Interfaccia di amministrazione di Office 365** del browser fare clic su **Utenti > Utenti attivi** nel riquadro di spostamento di sinistra.
    
2. Fare clic sull'account di amministratore globale e quindi fare clic su **Modifica** per **le licenze del prodotto**.
    
3. Nel riquadro di **licenze per i prodotti** , attivare la licenza del prodotto per la **mobilità aziendale + E5 di sicurezza** per **in**, fare clic su **Salva** e quindi fare doppio clic su **Chiudi** .
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a>Fase 2: Creare e configurare gruppi e utenti di Azure Active Directory (AD)

In questa fase vengono creati e configurati i gruppi e gli utenti di Azure AD per l'organizzazione fittizia.
  
Innanzitutto, creare un set di gruppi per un'organizzazione tipica con il portale di Azure.
  
1. Creare una scheda separata del browser e andare al portale di Azure al [https://portal.azure.com](https://portal.azure.com). Se necessario, accedere con le credenziali dell'account amministratore globale per la sottoscrizione di valutazione di Office 365 E5.
    
2. Nel portale di Azure fare clic su **Azure Active Directory > Utenti e gruppi > Tutti i gruppi**.
    
3. Nel pannello **Tutti i gruppi** fare clic su **+ Nuovo gruppo**.
    
4. Nel pannello **Gruppo**:
    
  - Digitare **C-Suite** in **Nome**.
    
  - Selezionare **Assegnato** in **Appartenenza**.
    
  - Selezionare **Sì** per **Abilitare le funzionalità di Office**.
    
5. Fare clic su **Crea** e quindi chiudere il pannello **Gruppo**.
    
6. Ripetere i passaggi da 3 a 5 per i nomi dei gruppi seguenti:
    
  - IT staff
    
  - Research staff
    
  - Regular staff
    
  - Marketing staff
    
  - Sales staff
    
7. Tenere aperta la scheda del portale di Azure nel browser.
    
Successivamente, si configurano le licenze automatiche in modo che ai membri dei gruppi vengano automaticamente assegnate le licenze per le sottoscrizioni di Office 365 ed EMS.
  
1. Nel portale di Azure fare clic su **Azure Active Directory > Licenze > Tutti i prodotti**.
    
2. Nell'elenco, selezionare **mobilità aziendale + sicurezza E5** e **Office 365 Enterprise E5**e quindi fare clic su **Assegna**.
    
3. Nel pannello **Assegnare licenza** fare clic su **Utenti e gruppi**.
    
4. Nell'elenco dei gruppi selezionare gli elementi seguenti:
    
  - C-Suite
    
  - IT staff
    
  - Research staff
    
  - Regular staff
    
  - Marketing staff
    
  - Sales staff
    
5. Fare clic su **Seleziona**e quindi fare clic su **Assegna**.
    
6. Chiudere la scheda del portale di Azure nel browser.
    
È quindi necessario [connettersi al modulo PowerShell di Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).
  
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
> L'uso di una password comune qui consente l'automazione e agevola la configurazione per un ambiente di sviluppo e test. Non è consigliato per le sottoscrizioni di produzione. 
  
Utilizzare la procedura seguente per verificare che le licenze basate su gruppo funzioni correttamente.
  
1. Dalla scheda **Microsoft Office Home** del browser fare clic sul riquadro **Amministratore**.
    
2. Dalla nuova scheda **Interfaccia di amministrazione di Office** del browser fare clic su **Utenti**.
    
3. Fare clic su **CEO** nell'elenco degli utenti.
    
4. Nel riquadro in cui sono elencate le proprietà dell'account utente **CEO** verificare che all'account siano state assegnate le licenze **Enterprise Mobility + Security E5** e **Office 365 Enterprise E5** (nell'elenco delle **licenze del prodotto**).
    
## <a name="phase-3-create-office-365-labels"></a>Fase 3: Creare le etichette di Office 365

In questa fase vengono create le etichette per i diversi livelli di sicurezza per le cartelle dei documenti del sito del team di SharePoint Online.
  
1. Se necessario, utilizzare un'istanza del browser Internet privata e accedere al portale di Office 365 con l'account amministratore globale della sottoscrizione di prova di Office 365 E5. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dalla scheda **Microsoft Office Home** fare clic sul riquadro **Amministratore**.
    
3. Scheda di **interfaccia di amministrazione di Office** nuovo del browser fare clic su **Admin Center > sicurezza &amp; conformità**.
    
4. Dalla nuova **Home - sicurezza &amp; conformità** scheda del browser, fare clic su **classificazioni > etichette**.
    
5. Dal riquadro **Home > Etichette** fare clic su **Crea un'etichetta**.
    
6. Nel riquadro **nome dell'etichetta** digitare **Interno pubblica**e quindi fare clic su **Avanti**.
    
7. Nel riquadro delle **impostazioni dell'etichetta** fare clic su **Avanti**.
    
8. Nel riquadro di **Rivedere le impostazioni** , fare clic su **Crea l'etichetta**e quindi fare clic su **Chiudi**.
    
9. Ripetere i passaggi da 5 a 8 per queste etichette aggiuntive:
    
  - Private
    
  - Dati sensibili
    
  - Highly Confidential (Riservatezza elevata)
    
10. Dal riquadro **Home > Etichette** fare clic su **Publish labels** (Pubblica etichette).
    
11. Nel riquadro **Choose labels to publish** (Scegli etichette da pubblicare) fare clic su **Choose labels to publish** (Scegli etichette da pubblicare).
    
12. Nel riquadro **Choose labels** (Scegli etichette) fare clic su **Aggiungi** e selezionare le quattro etichette.
    
13. Fare clic su **Fine**.
    
14. Nel riquadro **Choose labels to publish** (Scegli etichette da pubblicare) fare clic su **Avanti**.
    
15. Nel riquadro **Choose locations** (Scegli posizioni) fare clic su **Avanti**.
    
16. Nel riquadro **nome del criterio** digitare **esempio organizzazione** nella casella **nome**e quindi fare clic su **Avanti**.
    
17. Nel riquadro di **Rivedere le impostazioni** , fare clic su **etichette pubblica**e quindi fare clic su **Chiudi**.
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a>Fase 4: Creare i siti del team di SharePoint Online

In questa fase vengono creati e configurati i quattro tipi di siti del team di SharePoint Online per l'organizzazione di esempio.
  
### <a name="organization-wide-team-site"></a>Sito del team per l'intera organizzazione

Per creare un sito pubblico iniziale per il team di SharePoint Online, eseguire queste operazioni:
  
1. Se necessario, usare un browser sul computer locale e accedere al portale di Office 365 con l'account amministratore globale. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Nell'elenco dei riquadri fare clic su **SharePoint**.
    
3. Nella nuova scheda **SharePoint** del browser fare clic su + **Crea sito**.
    
4. Nella pagina **Crea un sito** fare clic su **Sito del team**.
    
5. In **Nome sito** digitare **Organization wide**. 
    
6. Come **descrizione del sito del team** digitare **SharePoint site for the entire organization** (Sito SharePoint per l'intera organizzazione).
    
7. In **impostazioni di Privacy**, selezionare **Pubblica - tutti gli utenti dell'organizzazione possono accedere al sito**e quindi fare clic su **Avanti**.
    
8. Nel riquadro **Who do you want to add?** (Chi si desidera aggiungere?) fare clic su **Fine**.
    
Configurare quindi la cartella dei documenti del sito del team dell'intera organizzazione per l'etichetta Internal Public.
  
1. Nella scheda **Home page di livello di organizzazione** del browser fare clic su **documenti**.
    
2. Fare clic sull'icona delle impostazioni e quindi su **Impostazioni libreria**.
    
3. In **Autorizzazioni e gestione** fare clic su **Apply label to items in this library** (Applica etichetta agli elementi in questa libreria).
    
4. In **Impostazioni si applicano etichetta**, selezionare **Interno pubblica**e quindi fare clic su **Salva**.
    
Di seguito è riportata la configurazione risultante.
  
![Protezione di livello di base per il sito del team di SharePoint Online pubblico a livello dell’organizzazione.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a>Sito del team Project 1

Per creare un sito del team SharePoint Online privato iniziale per un progetto all'interno dell'organizzazione, eseguire queste operazioni:
  
1. Se necessario, usare un browser sul computer locale e accedere al portale di Office 365 con l'account amministratore globale. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Nell'elenco dei riquadri fare clic su **SharePoint**.
    
3. Nella nuova scheda **SharePoint** del browser fare clic su + **Crea sito**.
    
4. Nella pagina **Crea un sito** fare clic su **Sito del team**.
    
5. In **Nome del sito** digitare **Project 1**. 
    
6. Nella **descrizione del sito del Team,** digitare **il sito di SharePoint per il progetto 1**.
    
7. **Le impostazioni di Privacy**, selezionare **privato: solo membri possono accedere al sito**e quindi fare clic su **Avanti**.
    
8. Nel riquadro **Who do you want to add?** (Chi si desidera aggiungere?) fare clic su **Fine**.
    
Configurare quindi la cartella dei documenti del sito del team Project 1 per l'etichetta Private.
  
1. Nella scheda **Project 1: Home** del browser fare clic su **Documenti**.
    
2. Fare clic sull'icona delle impostazioni e quindi su **Impostazioni libreria**.
    
3. In **Autorizzazioni e gestione** fare clic su **Apply label to items in this library** (Applica etichetta agli elementi in questa libreria).
    
4. In **Applica impostazioni etichetta**, selezionare **privata**e quindi fare clic su **Salva**.
    
Di seguito è riportata la configurazione risultante.
  
![Protezione di livello di base per il sito del team di SharePoint Online privato Project1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a>Sito del team delle campagne di marketing

Per creare un sito del team di SharePoint Online isolato per i dati sensibili delle risorse della campagna di marketing, eseguire le operazioni seguenti:
  
1. Utilizzando un browser nel computer locale, accedere al portale di Office 365 utilizzando l'account amministratore globale. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Nell'elenco dei riquadri fare clic su **SharePoint**.
    
3. Nella nuova scheda **SharePoint** del browser fare clic su + **Crea sito**.
    
4. Nella pagina **Crea un sito** fare clic su **Sito del team**.
    
5. Come **nome del sito del team** digitare **Marketing campaigns**.
    
6. Come **descrizione del sito del team** digitare **SharePoint site for marketing campaign resources (sensitive)** (Sito SharePoint per le risorse delle campagne marketing - dati sensibili).
    
7.  **Le impostazioni di Privacy**, selezionare **privato: solo membri possono accedere al sito**e quindi fare clic su **Avanti**.
    
8. Nel riquadro **Who do you want to add?** (Chi si desidera aggiungere?) fare clic su **Fine**.
    
9. Nella scheda **campagne di Marketing** nuovo nel browser, nella barra degli strumenti, fare clic sull'icona impostazioni e quindi fare clic su **autorizzazioni sito**.
    
10. Nel riquadro **Autorizzazioni sito** fare clic su **Advanced permissions settings** (Impostazioni autorizzazioni avanzate).
    
11. Nella nuova scheda **Autorizzazioni** del browser fare clic su **Impostazioni richieste di accesso**.
    
12. Nella finestra di dialogo **Impostazioni richieste di accesso** , deselezionare le caselle di controllo **Consenti ai membri di condividere il sito e i singoli file e cartelle** e i **membri Consenti per invitare altre persone al gruppo membri del sito** , digitare **ITAdmin1 @**\<il nome dell'organizzazione >**. onmicrosoft.com** di **inviare tutte le richieste di accesso**, quindi scegliere **OK**.
    
13. Fare clic su **Marketing campaigns - Members** (Campagne di marketing - Membri) nell'elenco.
    
14. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
15. Nella finestra di dialogo **Condividi** digitare **Marketing staff**, selezionarlo e fare clic su **Condividi**.
    
16. Ripetere i passaggi 14 e 15 per l'account utente **Researcher1** .
    
17. Fare clic sul pulsante Indietro del browser.
    
18. Nell'elenco, fare clic su **campagne di Marketing proprietari** .
    
19. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
20. Nella finestra di dialogo **condivisione** digitare **il personale IT**, selezionarlo e fare clic su **Condividi**.
    
21. Fare clic sul pulsante Indietro del browser.
    
22. Chiudere la scheda **utenti e gruppi** nel browser, fare clic sulla scheda **Home campagne di Marketing** nel browser e quindi chiudere il riquadro **autorizzazioni sito** .
    
Di seguito sono riportati i risultati della configurazione delle autorizzazioni:
  
- Il gruppo **Marketing campaigns - Members** (Campagne di marketing - Membri) di SharePoint contiene solo il gruppo **Marketing campaigns**, che contiene l'account utente amministratore globale, il gruppo **Marketing staff**, che contiene gli account utente Marketing1 e Marketing2, e l'account utente **Researcher1**.
    
- Il gruppo **Marketing campaigns - Owners** (Campagne di marketing - Proprietari) di SharePoint contiene solo il gruppo **IT staff**, che a sua volta contiene solo gli account utente ITAdmin1 e ITAdmin2.
    
- Il gruppo **Marketing campaigns - Visitors** (Campagne di marketing - Visitatori) di SharePoint non contiene gruppi né account utente.
    
- I membri non possono modificare le autorizzazioni a livello di sito, operazione che può essere eseguita solo dai membri del gruppo **Marketing campaigns - Owners**.
    
- Altri account utente non possono accedere al sito o alle sue risorse, ma possono richiedere l'accesso al sito, che invierà un'e-mail alla cassetta postale dell'account utente ITAdmin1.
    
Configurare quindi la cartella dei documenti del sito del team Marketing campaigns per l'etichetta Sensitive.
  
1. Nella scheda **Marketing campaigns - Home** (Campagne di marketing - Home) del browser fare clic su **Documenti**.
    
2. Fare clic sull'icona delle impostazioni e quindi su **Impostazioni libreria**.
    
3. In **Autorizzazioni e gestione** fare clic su **Apply label to items in this library** (Applica etichetta agli elementi in questa libreria).
    
4. In **Applica impostazioni etichetta**, selezionare **riservati**e quindi fare clic su **Salva**.
    
Configurare quindi un criterio di prevenzione della perdita di dati che informa gli utenti quando condividono un documento presente su un sito del team di SharePoint Online con etichetta Sensitive, incluso il sito Marketing campaigns, all'esterno dell'organizzazione.
  
1. Nella scheda **Home page di Microsoft Office** nel browser, fare clic sul **protezione &amp; conformità** affiancate.
    
2. Nel nuovo computer **protezione &amp; conformità** nel browser, fare clic **prevenzione della perdita di dati > criteri**.
    
3. Nel riquadro **Prevenzione perdita dati** fare clic su **+ Crea un criterio**.
    
4. Nella **iniziare con un modello o creare un criterio personalizzato** riquadro, fare clic su **personalizzata**e quindi fare clic su **Avanti**.
    
5. Nel riquadro **nome del criterio** digitare **siti del team di SharePoint Online riservati etichetta** **nome**e quindi fare clic su **Avanti**.
    
6. Nel riquadro **Choose locations** (Scegli posizioni) fare clic su **Let me choose specific locations** (Consenti di scegliere posizioni specifiche) e fare clic su **Avanti**.
    
7. Nell'elenco delle posizioni, disattivare i percorsi di **posta elettronica di Exchange** e **gli account di OneDrive** e quindi fare clic su **Avanti**.
    
8. Nel riquadro **Customize the types of sensitive info you want to protect** (Personalizza i tipi di informazioni sensibili da proteggere) fare clic su **Modifica**.
    
9. Nel riquadro **scegliere i tipi di contenuto per la protezione** , fare clic su **Aggiungi** nella casella a discesa e quindi fare clic su **etichette**.
    
10. Nel riquadro **etichette** fare clic su **+ Aggiungi**, selezionare l'etichetta **riservati** , fare clic su **Aggiungi**e quindi fare clic su **Fine**.
    
11. Nel riquadro **Choose the types of content to protect** (Scegli i tipi di contenuto da proteggere) fare clic su **Salva**.
    
12. Nel riquadro **Customize the types of sensitive info you want to protect** (Personalizza i tipi di informazioni sensibili da proteggere) fare clic su **Avanti**.
    
13. Nel riquadro **What do you want to do if we detect sensitive info?** (Selezionare come procedere in caso di informazioni sensibili rilevate) fare clic su **Customize the tip and email** (Personalizza suggerimento e messaggio di posta elettronica).
    
14. Nel riquadro **Customize policy tips and email notifications** (Personalizza i suggerimenti per i criteri e le notifiche tramite posta elettronica) fare clic su **Customize the policy tip text** (Personalizza testo suggerimento per criterio).
    
15. Nella casella di testo digitare o incollare quanto segue:
    
  - Per condividere un file con un utente all'esterno dell'organizzazione, scaricare il file e aprirlo. Fare clic su File, Proteggi documento, Crittografa con password e specificare una password complessa. Inviare la password in un messaggio di posta elettronica separato o un altro mezzo di comunicazione.
    
16. Fare clic su **OK**.
    
17. Nella **Selezionare l'operazione da eseguire se si rileva informazioni riservate?** riquadro, deselezionare la casella di controllo **Blocca la condivisione degli utenti e limitare l'accesso al contenuto condiviso** e quindi fare clic su **Avanti**.
    
18. Nella **si desidera attivare le operazioni criteri o di testing prima?** riquadro, fare clic su **Sì, attivarlo immediatamente**e quindi fare clic su **Avanti**.
    
19. Nel riquadro di **Rivedere le impostazioni** , fare clic su **Crea**e quindi fare clic su **Chiudi**.
    
Di seguito è riportata la configurazione risultante.
  
![Protezione di livello riservato per il sito del team di SharePoint Online isolato delle campagne di marketing.](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a>Sito del team di strategia aziendale

Per creare un sito del team di SharePoint Online isolato per i dati altamente riservati delle risorse aziendali strategiche dei dirigenti dell'organizzazione, eseguire le operazioni seguenti:
  
1. Se necessario, usare un browser sul computer locale e accedere al portale di Office 365 con l'account amministratore globale. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Nell'elenco dei riquadri fare clic su **SharePoint**.
    
3. Nella nuova scheda **SharePoint** del browser fare clic su + **Crea sito**.
    
4. Nella pagina **Crea un sito** fare clic su **Sito del team**.
    
5. Come **nome del sito del team** digitare **Company strategy** (Strategia aziendale).
    
6. Come **descrizione del sito del team** digitare **SharePoint site for company strategy (highly confidential)** (Sito di SharePoint per la strategia aziendale - Informazioni altamente riservate).
    
7.  **Le impostazioni di Privacy**, selezionare **privato: solo membri possono accedere al sito**e quindi fare clic su **Avanti**.
    
8. Nel riquadro **Who do you want to add?** (Chi si desidera aggiungere?) fare clic su **Fine**.
    
9. Nella scheda **strategia società** nuovo nel browser, nella barra degli strumenti, fare clic sull'icona impostazioni e quindi fare clic su **autorizzazioni sito**.
    
10. Nel riquadro **Autorizzazioni sito** fare clic su **Advanced permissions settings** (Impostazioni autorizzazioni avanzate).
    
11. Nella nuova scheda **Autorizzazioni** del browser fare clic su **Impostazioni richieste di accesso**.
    
12. Nella finestra di dialogo **Impostazioni richieste di accesso** , deselezionare **Consenti ai membri di condividere il sito e i singoli file e cartelle** e **Consenti ai membri per invitare altre persone al gruppo membri del sito** (in modo che tutti i tre caselle di controllo è deselezionate), quindi fare clic su ** OK**.
    
13. Fare clic su **strategia società membri** nell'elenco.
    
14. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
15. Nella finestra di dialogo **Condividi** digitare **C famiglia di prodotti**, selezionarlo e quindi fare clic su **Condividi**.
    
16. Nell'elenco, fare clic su **strategia società proprietari** .
    
17. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
18. Nella finestra di dialogo **condivisione** digitare **il personale IT**, selezionarlo e fare clic su **Condividi**.
    
19. Fare clic sul pulsante Indietro del browser.
    
20. Chiudere la scheda **utenti e gruppi** nel browser, fare clic sulla scheda **Home page della strategia - società** nel browser e quindi chiudere il riquadro **autorizzazioni sito** .
    
Di seguito sono riportati i risultati della configurazione delle autorizzazioni:
  
- Il gruppo **Company strategy - Members** (Strategia aziendale - Membri) di SharePoint contiene solo il gruppo **C-Suite**, che contiene solo gli account utente CEO, CFO e CIO, e il gruppo **Company strategy**, che contiene solo l'account utente amministratore globale.
    
- Gruppo di SharePoint **Proprietari di strategia aziendale** contiene solo il gruppo di **personale IT** (che include solo gli account utente ITAdmin1 e ITAdmin2).
    
- Il gruppo **Company strategy - Visitors** (Strategia aziendale - Visitatori) di SharePoint non contiene gruppi né account utente.
    
- I membri non possono modificare le autorizzazioni a livello di sito, operazione che può essere eseguita solo dai membri del gruppo **Company strategy - Owners**.
    
- Gli altri account utente non possono accedere al sito o alle relative risorse né richiedere l'accesso al sito. Le autorizzazioni aggiuntive per il sito devono essere eseguite dall'amministratore globale o da un membro del gruppo **Company strategy - Owners**.
    
Configurare quindi la cartella dei documenti del sito del team di strategia aziendale per l'etichetta Highly Confidential.
  
1. Nella scheda **Company strategy - Home** (Strategia aziendale - Home) del browser fare clic su **Documenti**.
    
2. Fare clic sull'icona delle impostazioni e quindi su **Impostazioni libreria**.
    
3. In **Autorizzazioni e gestione** fare clic su **Apply label to items in this library** (Applica etichetta agli elementi in questa libreria).
    
4. In **Applica impostazioni etichetta**, selezionare **Altamente riservati**e quindi fare clic su **Salva**.
    
Configurare un criterio di prevenzione della perdita di dati che blocchi gli utenti quando condividono un documento presente su un sito del team di SharePoint Online con etichetta Highly Confidential, incluso il sito Company strategy, all'esterno dell'organizzazione.
  
1. Se necessario, utilizzare un browser nel computer locale e accedere al portale di Office 365 con un account che dispone del ruolo di amministratore della sicurezza o amministratore azienda. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Nella scheda **Home page di Microsoft Office** nel browser, fare clic sul **protezione &amp; conformità** affiancate.
    
3. Nel nuovo computer **protezione &amp; conformità** nel browser, fare clic **prevenzione della perdita di dati > criteri**.
    
4. Nel riquadro **Prevenzione perdita dati** fare clic su **+ Crea un criterio**.
    
5. Nella **iniziare con un modello o creare un criterio personalizzato** riquadro, fare clic su **personalizzata**e quindi fare clic su **Avanti**.
    
6. Nel riquadro **nome del criterio** digitare **siti del team di SharePoint Online di altamente riservati etichetta** **nome**e quindi fare clic su **Avanti**.
    
7. Nel riquadro **Choose locations** (Scegli posizioni) fare clic su **Let me choose specific locations** (Consenti di scegliere posizioni specifiche) e fare clic su **Avanti**.
    
8. Nell'elenco delle posizioni, disattivare i percorsi di **posta elettronica di Exchange** e **gli account di OneDrive** e quindi fare clic su **Avanti**.
    
9. Nel riquadro **Customize the types of sensitive info you want to protect** (Personalizza i tipi di informazioni sensibili da proteggere) fare clic su **Modifica**.
    
10. Nel riquadro **scegliere i tipi di contenuto per la protezione** , fare clic su **Aggiungi** nella casella a discesa e quindi fare clic su **etichette**.
    
11. Nel riquadro **etichette** fare clic su **+ Aggiungi**, selezionare l'etichetta **Altamente riservati** , fare clic su **Aggiungi**e quindi fare clic su **Fine**.
    
12. Nel riquadro **Choose the types of content to protect** (Scegli i tipi di contenuto da proteggere) fare clic su **Salva**.
    
13. Nel riquadro **Customize the types of sensitive info you want to protect** (Personalizza i tipi di informazioni sensibili da proteggere) fare clic su **Avanti**.
    
14. Nel riquadro **What do you want to do if we detect sensitive info?** (Selezionare come procedere in caso di informazioni sensibili rilevate) fare clic su **Customize the tip and email** (Personalizza suggerimento e messaggio di posta elettronica).
    
15. Nel riquadro **Customize policy tips and email notifications** (Personalizza i suggerimenti per i criteri e le notifiche tramite posta elettronica) fare clic su **Customize the policy tip text** (Personalizza testo suggerimento per criterio).
    
16. Nella casella di testo digitare o incollare quanto segue:
    
  - Per condividere un file con un utente all'esterno dell'organizzazione, scaricare il file e aprirlo. Fare clic su File, Proteggi documento, Crittografa con password e specificare una password complessa. Inviare la password in un messaggio di posta elettronica separato o un altro mezzo di comunicazione.
    
17. Fare clic su **OK**.
    
18. Nella **Selezionare l'operazione da eseguire se si rileva informazioni riservate?** riquadro, selezionare **Richiedi motivazione aziendale per eseguire l'override**e quindi fare clic su **Avanti**.
    
19. Nella **si desidera attivare le operazioni criteri o di testing prima?** riquadro, fare clic su **Sì, attivarlo immediatamente**e quindi fare clic su **Avanti**.
    
20. Nel riquadro di **Rivedere le impostazioni** , fare clic su **Crea**e quindi fare clic su **Chiudi**.
    
Seguire quindi le istruzioni in [Attivare Azure RMS dall'interfaccia di amministrazione di Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
Successivamente, configurare Azure Information Protection con nuovi criteri con ambito e un'etichetta secondaria per la protezione e le autorizzazioni con la procedura seguente:
  
1. Accedere al portale di Office 365 con un account che dispone del ruolo Amministratore della sicurezza oppure Amministratore della società. Per informazioni, vedere [Dove accedere a Office 365 per le aziende](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. In una scheda separata del browser, accedere al portale di Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Se è la prima volta che viene configurato Azure Information Protection, consultare queste [istruzioni](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. Nel riquadro dell'elenco, fare clic su **Ulteriori servizi**, digitare **Informazioni**, quindi fare clic su **Azure Information Protection**.
    
5. Nel pannello **Azure Information Protection**, fare clic su **Criteri con ambiti > + Aggiungi un nuovo criterio**.
    
6. Digitare **CompanyStrategy** in **Nome criterio** ed **Etichetta per i documenti nel sito del team di strategia aziendale** in **Descrizione**.
    
7. Fare clic su **Selezionare gli utenti o i gruppi a cui viene applicato il criterio > Utenti/Gruppi**, quindi selezionare **C-Suite**.
    
8. Fare clic su **Seleziona > OK**.
    
9. Per l'etichetta **Estremamente riservato**, fare clic sui puntini di sospensione (…), quindi su **Aggiungi un'etichetta secondaria**.
    
10. Digitare un nome per l'etichetta secondaria in **Nome** e una descrizione dell'etichetta in **Descrizione**.
    
11. In **Configurare le autorizzazioni per documenti e messaggi di posta elettronica contenenti questa etichetta** fare clic su **Proteggi**.
    
12. Nella sezione **Protezione** fare clic su **Azure (chiave cloud)**.
    
13. Nel pannello **Protezione** fare clic su **+ Aggiungi autorizzazioni** in **Impostazioni di protezione**.
    
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
  
A questo punto si è pronti a creare documenti in questi quattro siti e a testare l'accesso ai siti usando diversi account utente della sottoscrizione di valutazione.
  
Di seguito è riportata la configurazione completa per tutti i quattro siti del team di SharePoint Online.
  
![Tutti i quattro siti del team nell’ambiente di sviluppo/test protetto di SharePoint Online.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a>Passaggio successivo

Quando si è pronti per la distribuzione di produzione dei siti di SharePoint Online protetti, vedere [Proteggere siti e file di SharePoint Online](secure-sharepoint-online-sites-and-files.md) per informazioni dettagliate e collegamenti ad articoli relativi alle procedure di distribuzione.
  
## <a name="see-also"></a>Vedere anche

[Protezione di file e siti di SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Soluzioni di sicurezza](security-solutions.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)
  
[Guida sulla sicurezza Microsoft per organizzazioni che si occupano della campagna politica, no profit e altre organizzazioni agili](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




