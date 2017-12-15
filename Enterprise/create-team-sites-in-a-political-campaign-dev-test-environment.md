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
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: 'Riepilogo: Creare siti del team SharePoint Online pubblici, privati, riservati e altamente riservati nell''ambiente di sviluppo e di testing politici campagne.'
ms.openlocfilehash: 82e671af271508dfdecac6169a7892a8a12b7865
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
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
    
2. Fare clic sull'icona impostazioni e quindi fare clic su **Impostazioni raccolta**.
    
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
    
22. Chiudere la scheda **utenti e gruppi** nel browser, fare clic sulla scheda **Home page di marketing campagne** nel browser e quindi chiudere il riquadro **autorizzazioni sito** .
    
Ecco i risultati della configurazione delle autorizzazioni:
  
- Al gruppo di SharePoint **Membri di marketing campagna** contiene solo il **Senior e personale strategico** gruppo (che contiene gli account utente Candidate, ChiefOfStaff e Strategic1), il gruppo di **marketing campagne** (che include il account di utente amministratore globale), il gruppo di **agenti Analitica** (che include l'account utente DataScientist1) e l'account utente **Regular1** .
    
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
    
### <a name="campaign-strategy-team-site"></a>Sito del team per la strategia della campagna

Per creare un sito del team di SharePoint Online isolato al livello estremamente riservato per le risorse relative alla strategia della campagna, eseguire le operazioni seguenti:
  
1. Se necessario, utilizzare un browser nel computer locale e accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) utilizzando l'account amministratore globale.
    
2. Nell'elenco delle sezioni, fare clic su **SharePoint**.
    
3. Nella scheda **SharePoint** nuovo nel browser, fare clic su **Crea sito +**.
    
4. Nella pagina **Crea sito** fare clic su **sito del Team**.
    
5. **Nome del sito del Team**, digitare **strategia campagne**.
    
6. Nella **descrizione del sito del Team**, digitare **il sito di SharePoint per la strategia di campagne (altamente riservato)**.
    
7.  **Le impostazioni di Privacy**, selezionare **privato: solo membri possono accedere al sito**e quindi fare clic su **Avanti**.
    
8. Nella **che si desidera aggiungere?** riquadro, fare clic su **Fine**.
    
9. Nella scheda **strategia campagna di** nuovo nel browser, nella barra degli strumenti, fare clic sull'icona impostazioni e quindi fare clic su **autorizzazioni sito**.
    
10. Nel riquadro **autorizzazioni sito** fare clic su **impostazioni di autorizzazioni avanzate**.
    
11. Nella scheda **autorizzazioni** nuova nel browser, fare clic su **Impostazioni richieste di accesso**.
    
12. Nella finestra di dialogo **Impostazioni richieste di accesso** , deselezionare **Consenti ai membri di condividere il sito e i singoli file e cartelle** e **Consenti ai membri per invitare altre persone al gruppo membri del sito** (in modo che tutti i tre caselle di controllo è deselezionate), quindi fare clic su ** OK**.
    
13. Fare clic su **strategia campagna membri** nell'elenco.
    
14. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
15. Nella finestra di dialogo **Condividi** digitare **Senior e personale strategico**, selezionarlo e fare clic su **Condividi**.
    
16. Nell'elenco, fare clic su **strategia campagna proprietari** .
    
17. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
18. Nella finestra di dialogo **condivisione** digitare **il personale IT**, selezionarlo e fare clic su **Condividi**.
    
19. Fare clic sul pulsante Indietro del browser.
    
20. Chiudere la scheda **utenti e gruppi** nel browser, fare clic sulla scheda **home page della strategia di campagna** nel browser e quindi chiudere il riquadro **autorizzazioni sito** .
    
Ecco i risultati della configurazione delle autorizzazioni:
  
- Il gruppo di SharePoint **Membri di strategia campagna** contiene solo il gruppo **Senior e personale strategico** (che include solo gli account utente Candidate, ChiefOfStaff e Strategic1) e del gruppo **strategia campagna** (che include solo l'account amministratore globale utente).
    
- Gruppo di SharePoint **Proprietari di strategia campagna** contiene solo il gruppo di **personale IT** (che include solo gli account utente ITAdmin1 e ITAdmin2).
    
- Gruppo di SharePoint **Visitatori di strategia campagna** non contiene nessun account utente o gruppi.
    
- Membri non possono modificare le autorizzazioni a livello di sito (ciò può essere eseguita solo dai membri del gruppo **Proprietari di strategia campagna** ).
    
- Altri account utente non può accedere al sito e le relative risorse o richiedere l'accesso al sito. Autorizzazioni aggiuntive per il sito devono essere eseguite dall'amministratore globale o da un membro del gruppo **Proprietari di strategia campagne** .
    
Successivamente, configurare la cartella dei documenti del sito del team Strategia della campagna per l'etichetta Estremamente riservato.
  
1. Nella scheda **home page della strategia campagna** del browser fare clic su **documenti**.
    
2. Fare clic sull'icona impostazioni e quindi fare clic su **Impostazioni raccolta**.
    
3. Nella sezione **autorizzazioni e gestione**, fare clic su **Applica etichetta agli elementi della raccolta**.
    
4. In **Applica impostazioni etichetta**, selezionare **Altamente riservati**e quindi fare clic su **Salva**.
    
Quindi, configurare un criterio DLP che gli utenti blocchi quando si condivide un documento in un sito del team di SharePoint Online con l'etichetta altamente riservati all'esterno dell'organizzazione. Tale criterio DLP verrà applicato alle risorse nel sito strategia campagne.
  
1. Se necessario, utilizzare un browser nel computer locale e accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) con un account che dispone del ruolo di amministratore della sicurezza o amministratore azienda.
    
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
    
Utilizzare le istruzioni riportate in [Attivare Azure RMS con l'interfaccia di amministrazione di Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
Configurare quindi la protezione delle informazioni di Azure con un nuovo criterio con ambito e secondaria etichetta per la protezione e autorizzazioni con le operazioni seguenti:
  
1. Accedere al portale di Office 365 con un account che dispone del ruolo Amministratore della sicurezza oppure Amministratore della società. Per informazioni, vedere [Dove accedere a Office 365 per le aziende](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. In una scheda a parte del browser, accedere al portale di Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Se è la prima volta che viene configurato Azure Information Protection, consultare queste [istruzioni](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. Nel riquadro dell'elenco, fare clic su **Ulteriori servizi**, digitare **Informazioni**, quindi fare clic su **Azure Information Protection**.
    
5. Nel pannello **Azure Information Protection**, fare clic su **Criteri con ambiti > + Aggiungi un nuovo criterio**.
    
6. Digitare **CampaignStrategy** **nome del criterio** e l' **etichetta per i documenti nel sito del team strategia campagna** nella **casella Descrizione**.
    
7. Fare clic su **Selezionare gli utenti o gruppi di ottenere il criterio > utenti/gruppi**e quindi selezionare **Senior e strategico personale**.
    
8. Fare clic su **Seleziona > OK**.
    
9. Per l'etichetta **Estremamente riservato**, fare clic sui puntini di sospensione (…), quindi su **Aggiungi un'etichetta secondaria**.
    
10. Digitare un nome per l'etichetta secondaria in **Nome** e una descrizione dell'etichetta in **Descrizione**.
    
11. In **Configurare le autorizzazioni per documenti e messaggi di posta elettronica contenenti questa etichetta** fare clic su **Proteggi**.
    
12. Nella sezione **Protezione**, fare clic su **Azure (chiave cloud)**.
    
13. Nel pannello **Protezione**, in **Impostazioni di protezione**, fare clic su **+ Aggiungi autorizzazioni**.
    
14. Nel pannello **Aggiungi autorizzazioni**, in **Specifica utenti e gruppi** fare clic su **+ Sfoglia la directory**.
    
15. Nel riquadro **AAD utenti e gruppi** selezionare **Senior e personale strategico**e quindi fare clic su **Seleziona**.
    
16. In **Scegli autorizzazioni dal set di impostazioni**, deselezionare le caselle di controllo **Stampa**, **Copia ed estrai il contenuto** e **Inoltra**.
    
17. Fare due volte clic su **OK**.
    
18. Nel pannello **Etichetta secondaria** fare clic su **Salva**.
    
19. Chiudere il pannello del nuovo criterio con ambito.
    
20. Su blade **Azure Information protection - criteri con ambiti** , fare clic su **pubblica**e quindi fare clic su **Sì**.
    
È ora possibile iniziare a creare documenti in questi quattro siti e verificare l'accesso a tali con diversi account utente nella sottoscrizione di prova. 
  
Per proteggere un documento con Azure Information Protection and questa nuova etichetta, è necessario [installare il client per la protezione delle informazioni di Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) in un computer di test, installare Office dal portale di Office 365 e quindi accedere da Microsoft Word con un account nel ** Senior e personale strategico** group dell'abbonamento prova.
  
## <a name="see-also"></a>See Also

[Guida sulla sicurezza Microsoft per organizzazioni che si occupano della campagna politica, no profit e altre organizzazioni agili](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Configurare i gruppi e gli utenti per un ambiente di sviluppo e di testing campagne politici](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)




