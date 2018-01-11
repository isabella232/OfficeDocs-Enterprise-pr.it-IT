---
title: Creare siti del team in un ambiente di sviluppo/test per la campagna politica
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: 'Riepilogo: Creare siti del team SharePoint Online pubblici, privati, riservati e altamente riservati nell''ambiente di sviluppo e di testing politici campagne.'
ms.openlocfilehash: 4f89fd29103756a33aa15e8e5e2976c521d69baa
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a>Creare siti del team in un ambiente di sviluppo/test per la campagna politica

 **Riepilogo:** Creare siti del team SharePoint Online pubblici, privati, riservati e altamente riservati nell'ambiente di sviluppo e di testing politici campagne. 
  
Utilizzare le istruzioni riportate in questo articolo per creare un ambiente di sviluppo e di testing che include quattro diversi tipi di siti di team di SharePoint Online per [Microsoft Security Guidance for campagne politici, ricchi e altre organizzazioni Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) soluzione. Tali siti vengono descritte in dettaglio in 10 argomento, intitolato **SharePoint e OneDrive for Business**.
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a>Fase 1: creare l'ambiente di sviluppo/test per la campagna politica

Per prima cosa, seguire le istruzioni in [configurare gruppi e gli utenti per un ambiente di sviluppo e di testing campagne politici](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) per creare le sottoscrizioni, gli utenti e gruppi.
  
## <a name="phase-2-create-office-365-labels"></a>Fase 2: creare etichette di Office 365

In questa fase è creare etichette per i diversi livelli di sicurezza per le cartelle di documenti del sito del team SharePoint Online.
  
1. Se necessario, accedere al portale di Office 365 con le credenziali dell'account amministratore globale della sottoscrizione di prova. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Nella scheda **Home page di Microsoft Office** , fare clic su tessera di **amministrazione** .
    
3. Scheda di **interfaccia di amministrazione di Office** nuovo del browser fare clic su **Admin Center > sicurezza &amp; conformità**.
    
4. Dalla nuova **Home - sicurezza &amp; conformità** scheda del browser, fare clic su **classificazioni > etichette**.
    
5. Dal **Home > etichette** riquadro, fare clic su **Crea un'etichetta**.
    
6. Nel riquadro **nome dell'etichetta** digitare **interno**e quindi fare clic su **Avanti**.
    
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
    
16. Nel riquadro **nome del criterio** digitare **campagne** nella **casella Nome**e quindi fare clic su **Avanti**.
    
17. Nel riquadro di **Rivedere le impostazioni** , fare clic su **etichette pubblica**e quindi fare clic su **Chiudi**.
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a>Fase 3: creare i siti del team di SharePoint Online

In questa fase, vengono creati e configurati i siti del team di SharePoint Online per la campagna politica corrispondente ai quattro tipi di siti del team di SharePoint Online.
  
### <a name="campaign-wide-team-site"></a>Sito del team per la campagna su vasta scala

Per creare un sito del team di SharePoint Online pubblico di base, eseguire le operazioni seguenti:
  
1. Se necessario, utilizzare un browser nel computer locale e accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) utilizzando l'account amministratore globale.
    
2. Nell'elenco delle sezioni, fare clic su **SharePoint**.
    
3. Nella scheda **SharePoint** nuovo nel browser, fare clic su **Crea sito +**.
    
4. Nella pagina **Crea sito** fare clic su **sito del Team**.
    
5. In **nome sito**digitare **campagne wide**. 
    
6. Nella **descrizione del sito del Team**, digitare **il sito di SharePoint per l'intera campagna**.
    
7. In **impostazioni di Privacy**, selezionare **Pubblica - tutti gli utenti dell'organizzazione possono accedere al sito**e quindi fare clic su **Avanti**.
    
8. Nella **che si desidera aggiungere?** riquadro, fare clic su **Fine**.
    
Successivamente, configurare la cartella dei documenti del sito del team Campagna su vasta scala per l'etichetta Interno.
  
1. Nella scheda **campagna home page di livello** del browser fare clic su **documenti**.
    
2. Fare clic sull'icona impostazioni e quindi fare clic su **Impostazioni raccolta**.
    
3. Nella sezione **autorizzazioni e gestione**, fare clic su **Applica etichetta agli elementi della raccolta**.
    
4. In **Applica impostazioni etichetta**, selezionare **interno**e quindi fare clic su **Salva**.
    
### <a name="campaign-project-1-team-site"></a>Sito del team 1 del progetto della campagna

Per creare un sito del team di SharePoint Online privato di base per un progetto all'interno della campagna, eseguire le operazioni seguenti:
  
1. Se necessario, utilizzare un browser nel computer locale e accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) utilizzando l'account amministratore globale.
    
2. Nell'elenco delle sezioni, fare clic su **SharePoint**.
    
3. Nella scheda **SharePoint** nuovo nel browser, fare clic su **Crea sito +**.
    
4. Nella pagina **Crea sito** fare clic su **sito del Team**.
    
5. In **nome sito**digitare **project campagne 1**. 
    
6. Nella **descrizione del sito del Team,** digitare **il sito di SharePoint per il progetto campagne 1**.
    
7. **Le impostazioni di Privacy**, selezionare **privato: solo membri possono accedere al sito**e quindi fare clic su **Avanti**.
    
8. Nella **che si desidera aggiungere?** riquadro, fare clic su **Fine**.
    
Successivamente, configurare la cartella dei documenti del sito del team Progetto della campagna 1 per l'etichetta Privato.
  
1. Nella scheda **campagna 1-Home page di project** del browser fare clic su **documenti**.
    
2. Click the settings icon, and then click **Library settings**.
    
3. Nella sezione **autorizzazioni e gestione**, fare clic su **Applica etichetta agli elementi della raccolta**.
    
4. In **Applica impostazioni etichetta**, selezionare **privata**e quindi fare clic su **Salva**.
    
### <a name="campaign-marketing-team-site"></a>Sito del team per il marketing della campagna

Per creare un sito del team di SharePoint Online isolato riservato per le risorse marketing della campagna, eseguire le operazioni seguenti:
  
1. Utilizzando un browser nel computer locale, accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) utilizzando l'account amministratore globale.
    
2. Nell'elenco delle sezioni, fare clic su **SharePoint**.
    
3. Nella scheda **SharePoint** nuovo nel browser, fare clic su **Crea sito +**.
    
4. Nella pagina **Crea sito** fare clic su **sito del Team**.
    
5. **Nome del sito del Team**, digitare **marketing campagne**.
    
6. Nella **descrizione del sito del Team**, digitare **sito di SharePoint per campagne di marketing (maiuscole/minuscole)**.
    
7.  **Le impostazioni di Privacy**, selezionare **privato: solo membri possono accedere al sito**e quindi fare clic su **Avanti**.
    
8. Nella **che si desidera aggiungere?** riquadro, fare clic su **Fine**.
    
9. Nella scheda **marketing campagne** nuovo nel browser, nella barra degli strumenti, fare clic sull'icona impostazioni e quindi fare clic su **autorizzazioni sito**.
    
10. Nel riquadro **autorizzazioni sito** fare clic su **impostazioni di autorizzazioni avanzate**.
    
11. Nella scheda **autorizzazioni** nuova nel browser, fare clic su **Impostazioni richieste di accesso**.
    
12. Nella finestra di dialogo **Impostazioni richieste di accesso** , deselezionare le caselle di controllo **Consenti ai membri di condividere il sito e i singoli file e cartelle** e i **membri Consenti per invitare altre persone al gruppo membri del sito** , digitare **ITAdmin1 @** <your organization name> **. onmicrosoft.com** di **inviare tutte le richieste di accesso**, quindi scegliere **OK**.
    
13. Fare clic su **campagne di marketing membri** nell'elenco.
    
14. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
15. Nella finestra di dialogo **Condividi** digitare **Senior e personale strategico**, selezionarlo e fare clic su **Condividi**.
    
16. Ripetere i passaggi 14 e 15 per il gruppo di **agenti Analitica** e l'account utente **Regular1** .
    
17. Fare clic sul pulsante Indietro del browser.
    
18. Nell'elenco, fare clic su **campagne di marketing proprietari** .
    
19. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
20. Nella finestra di dialogo **condivisione** digitare **il personale IT**, selezionarlo e fare clic su **Condividi**.
    
21. Fare clic sul pulsante Indietro del browser.
    
22. Close the **People and Groups** tab in your browser, click the **Campaign marketing-Home** tab in your browser, and then close the **Site permissions** pane.
    
Ecco i risultati della configurazione delle autorizzazioni:
  
- The **Campaign marketing-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains the Candidate, ChiefOfStaff, and Strategic1 user accounts), the **Campaign marketing** group (which contains the global administrator user account), the **Analytics staff** group (which contains the DataScientist1 user account), and the **Regular1** user account.
    
- Gruppo di SharePoint **Proprietari di marketing campagna** contiene solo il gruppo di **personale IT** (che include solo gli account utente ITAdmin1 e ITAdmin2).
    
- Gruppo di SharePoint **Visitatori di marketing campagne** non contiene gruppi o gli account utente.
    
- Membri non possono modificare le autorizzazioni a livello di sito (ciò può essere eseguita solo dai membri del gruppo **Proprietari di marketing campagna** ).
    
- Altri account utente non possono accedere al sito o alle sue risorse, ma possono richiedere l'accesso al sito, che invierà un'e-mail alla cassetta postale dell'account utente ITAdmin1.
    
Successivamente, configurare la cartella dei documenti del sito del team Marketing della campagna per l'etichetta Riservato.
  
1. Nella scheda **Home page di marketing campagne** del browser fare clic su **documenti**.
    
2. Fare clic sull'icona impostazioni e quindi fare clic su **Impostazioni raccolta**.
    
3. Nella sezione **autorizzazioni e gestione**, fare clic su **Applica etichetta agli elementi della raccolta**.
    
4. In **Applica impostazioni etichetta**, selezionare **riservati**e quindi fare clic su **Salva**.
    
Successivamente, configurare un criterio di criterio DLP perdita di dati che informa gli utenti quando si condivide un documento in un sito del team di SharePoint Online con l'etichetta sensibile all'esterno dell'organizzazione. Tale criterio DLP verrà applicato alle risorse nel sito per campagne di marketing.
  
1. Nella scheda **Home page di Microsoft Office** nel browser, fare clic sul **protezione &amp; conformità** affiancate.
    
2. Nel nuovo computer **protezione &amp; conformità** nel browser, fare clic **prevenzione della perdita di dati > criteri**.
    
3. Nel riquadro di **prevenzione della perdita di dati** , fare clic su **+ Crea un criterio**.
    
4. Nella **iniziare con un modello o creare un criterio personalizzato** riquadro, fare clic su **personalizzata**e quindi fare clic su **Avanti**.
    
5. In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.
    
6. In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.
    
7. Nell'elenco delle posizioni, disattivare i percorsi di **posta elettronica di Exchange** e **gli account di OneDrive** e quindi fare clic su **Avanti**.
    
8. In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.
    
9. In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.
    
10. In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.
    
11. In the **Choose the types of content to protect** pane, click **Save**.
    
12. In the **Customize the types of sensitive info you want to protect** pane, click **Next**.
    
13. In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.
    
14. In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.
    
15. In the text box, type or paste in the following:
    
  - Per condividere con un utente esterno all'organizzazione, scaricare il file e quindi aprirlo. Fare clic su File, Proteggi documento, Crittografa con password, quindi specificare una password complessa. Inviare la password in un'e-mail separata o con altri mezzi di comunicazione.
    
16. Fare clic su **OK**.
    
17. In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.
    
18. In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.
    
19. In the **Review your settings** pane, click **Create**, and then click **Close**.
    
### <a name="campaign-strategy-team-site"></a>Sito del team per la strategia della campagna

Per creare un sito del team di SharePoint Online isolato al livello estremamente riservato per le risorse relative alla strategia della campagna, eseguire le operazioni seguenti:
  
1. Se necessario, utilizzare un browser nel computer locale e accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) utilizzando l'account amministratore globale.
    
2. In the list of tiles, click **SharePoint**.
    
3. On the new **SharePoint** tab in your browser, click **+ Create site**.
    
4. On the **Create a site** page, click **Team site**.
    
5. In **Team site name**, type **Campaign strategy**.
    
6. In **Team site description**, type **SharePoint site for campaign strategy (highly confidential)**.
    
7.  In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.
    
8. On the **Who do you want to add?** pane, click **Finish**.
    
9. On the new **Campaign strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.
    
10. In the **Site permissions** pane, click **Advanced permissions settings**.
    
11. In the new **Permissions** tab in your browser, click **Access Request Settings**.
    
12. In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.
    
13. Click **Campaign strategy Members** in the list.
    
14. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
15. In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.
    
16. Click **Campaign strategy Owners** in the list.
    
17. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
18. In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.
    
19. Fare clic sul pulsante Indietro del browser.
    
20. Close the **People and Groups** tab in your browser, click the **Campaign strategy-Home** tab in your browser, and then close the **Site permissions** pane.
    
Ecco i risultati della configurazione delle autorizzazioni:
  
- The **Campaign strategy-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains only the Candidate, ChiefOfStaff, and Strategic1 user accounts) and the **Campaign strategy** group (which contains only the global administrator user account).
    
- The **Campaign strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).
    
- The **Campaign strategy-Visitors** SharePoint group contains no groups or user accounts.
    
- Members cannot modify site-level permissions (this can only be done by members of the **Campaign strategy-Owners** group).
    
- Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Campaign strategy-Owners** group.
    
Successivamente, configurare la cartella dei documenti del sito del team Strategia della campagna per l'etichetta Estremamente riservato.
  
1. In the **Campaign strategy-Home** tab of your browser, click **Documents**.
    
2. Click the settings icon, and then click **Library settings**.
    
3. Under **Permissions and Management**, click **Apply label to items in this library**.
    
4. In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.
    
Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label outside the organization. This DLP policy will apply to resources in the Campaign strategy site.
  
1. If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with an account that has the Security Administrator or Company Administrator role.
    
2. From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.
    
3. On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.
    
4. In the **Data loss prevention** pane, click **+ Create a policy**.
    
5. In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.
    
6. In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.
    
7. In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.
    
8. In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.
    
9. In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.
    
10. In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.
    
11. In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.
    
12. Nel riquadro **scegliere i tipi di contenuto per la protezione** , fare clic su **Salva**.
    
13. Nel riquadro di **personalizzare i tipi di informazioni riservate che si desidera proteggere** , fare clic su **Avanti**.
    
14. In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.
    
15. In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.
    
16. In the text box, type or paste in the following:
    
  - Per condividere con un utente esterno all'organizzazione, scaricare il file e quindi aprirlo. Fare clic su File, Proteggi documento, Crittografa con password, quindi specificare una password complessa. Inviare la password in un'e-mail separata o con altri mezzi di comunicazione.
    
17. Fare clic su **OK**.
    
18. Nella **Selezionare l'operazione da eseguire se si rileva informazioni riservate?** riquadro, selezionare **Richiedi motivazione aziendale per eseguire l'override**e quindi fare clic su **Avanti**.
    
19. In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.
    
20. In the **Review your settings** pane, click **Create**, and then click **Close**.
    
Utilizzare le istruzioni riportate in [Attivare Azure RMS con l'interfaccia di amministrazione di Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
Configurare quindi la protezione delle informazioni di Azure con un nuovo criterio con ambito e secondaria etichetta per la protezione e autorizzazioni con le operazioni seguenti:
  
1. Accedere al portale di Office 365 con un account che dispone del ruolo Amministratore della sicurezza oppure Amministratore della società. Per informazioni, vedere [Dove accedere a Office 365 per le aziende](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. In una scheda a parte del browser, accedere al portale di Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Se è la prima volta che viene configurato Azure Information Protection, consultare queste [istruzioni](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. Nel riquadro dell'elenco, fare clic su **Ulteriori servizi**, digitare **Informazioni**, quindi fare clic su **Azure Information Protection**.
    
5. Nel pannello **Azure Information Protection**, fare clic su **Criteri con ambiti > + Aggiungi un nuovo criterio**.
    
6. Digitare **CampaignStrategy** **nome del criterio** e l' **etichetta per i documenti nel sito del team strategia campagna** nella **casella Descrizione**.
    
7. Click **Select which users or groups get this policy > User/Groups**, and then select **Senior and strategic staff**.
    
8. Fare clic su **Seleziona > OK**.
    
9. Per l'etichetta **Estremamente riservato**, fare clic sui puntini di sospensione (…), quindi su **Aggiungi un'etichetta secondaria**.
    
10. Digitare un nome per l'etichetta secondaria in **Nome** e una descrizione dell'etichetta in **Descrizione**.
    
11. In **Configurare le autorizzazioni per documenti e messaggi di posta elettronica contenenti questa etichetta** fare clic su **Proteggi**.
    
12. Nella sezione **Protezione**, fare clic su **Azure (chiave cloud)**.
    
13. Nel pannello **Protezione**, in **Impostazioni di protezione**, fare clic su **+ Aggiungi autorizzazioni**.
    
14. Nel pannello **Aggiungi autorizzazioni**, in **Specifica utenti e gruppi** fare clic su **+ Sfoglia la directory**.
    
15. On the **AAD Users and Groups** pane, select **Senior and strategic staff**, and then click **Select**.
    
16. In **Scegli autorizzazioni dal set di impostazioni**, deselezionare le caselle di controllo **Stampa**, **Copia ed estrai il contenuto** e **Inoltra**.
    
17. Fare due volte clic su **OK**.
    
18. Nel pannello **Etichetta secondaria** fare clic su **Salva**.
    
19. Chiudere il pannello del nuovo criterio con ambito.
    
20. Su blade **Azure Information protection - criteri con ambiti** , fare clic su **pubblica**e quindi fare clic su **Sì**.
    
You are now ready to begin creating documents in these four sites and test access to them with various user accounts in your trial subscription. 
  
To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **Senior and strategic staff** group of your trial subscription.
  
## <a name="see-also"></a>Vedere anche

[Guida sulla sicurezza Microsoft per organizzazioni che si occupano della campagna politica, no profit e altre organizzazioni agili](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Configurare i gruppi e gli utenti per un ambiente di sviluppo e di testing campagne politici](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)




