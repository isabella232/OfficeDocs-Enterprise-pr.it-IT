---
title: Proteggere i file di SharePoint Online con Office 365 etichette e DLP
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
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: 'Riepilogo: Office 365 dati ed etichette perdita criterio DLP criteri applicati ai siti dei team SharePoint Online con diversi livelli di protezione delle informazioni.'
ms.openlocfilehash: dd4f71d8fae458d6d20f7a5b35b46e14a72853f1
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a>Proteggere i file di SharePoint Online con Office 365 etichette e DLP

 **Riepilogo:** Office 365 dati ed etichette perdita criterio DLP criteri applicati ai siti dei team SharePoint Online con diversi livelli di protezione delle informazioni.
  
Utilizzare i passaggi descritti in questo articolo per progettare e distribuire le etichette di Office 365 e criteri DLP per la linea di base, importanti o altamente riservati team siti di SharePoint Online. Per ulteriori informazioni su questi tre livelli di protezione, vedere [file e siti di SharePoint Online sicura](secure-sharepoint-online-sites-and-files.md).
  
## <a name="office-365-labels-for-your-sharepoint-online-sites"></a>Etichette di Office 365 per i siti di SharePoint Online

Esistono tre fasi per creare e poi assegnare le etichette di Office 365 ai siti del team di SharePoint Online.
  
### <a name="phase-1-determine-the-office-365-label-names"></a>Fase 1: Determinare i nomi delle etichette di Office 365

In questa fase, si determinano i nomi delle etichette di Office 365 per i quattro livelli di protezione delle informazioni applicati ai siti del team di SharePoint Online. Nella tabella seguente sono riportati i nomi consigliati per ogni livello.
  
|**Livello di protezione del sito del team SharePoint Online**|**Nome di etichetta**|
|:-----|:-----|
|Pubblico di livello di base  <br/> |Pubblico di livello interno  <br/> |
|Privato di livello di base  <br/> |Privato  <br/> |
|Riservato  <br/> |Riservato  <br/> |
|Estremamente riservato  <br/> |Estremamente riservato  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a>Fase 2: creare etichette di Office 365

In questa fase, creare e poi pubblicare le etichette determinate per i diversi livelli di protezione delle informazioni.
  
Per creare le etichette, è possibile utilizzare l'interfaccia di amministrazione di Office 365 o Microsoft PowerShell.
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a>Creare etichette di Office 365 con l'interfaccia di amministrazione di Office 365

1. Accedere al portale di Office 365 con un account che dispone del ruolo Amministratore della sicurezza oppure Amministratore della società. Per informazioni, vedere [Dove accedere a Office 365 per le aziende](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Nella scheda **Home page di Microsoft Office** , fare clic su tessera di **amministrazione** .
    
3. Scheda di **interfaccia di amministrazione di Office** nuovo del browser fare clic su **Admin Center > sicurezza &amp; conformità**.
    
4. Dalla nuova **Home - sicurezza &amp; conformità** scheda del browser, fare clic su **classificazioni > etichette**.
    
5. Dal **Home > etichette** riquadro, fare clic su **Crea un'etichetta**.
    
6. Nel riquadro di **nome dell'etichetta** , digitare il nome dell'etichetta e quindi fare clic su **Avanti**.
    
7. Nel riquadro di **impostazioni dell'etichetta** , fare clic su **Avanti**.
    
8. Nel riquadro di **Rivedere le impostazioni** , fare clic su **Crea l'etichetta**e quindi fare clic su **Chiudi**.
    
9. Ripetere i passaggi da 5 a 8 per etichette aggiuntive.
    
### <a name="create-office-365-labels-with-powershell"></a>Creare etichette di Office 365 con PowerShell

1. [Connetti a Office 365 Security &amp; centro conformità utilizzando PowerShell remoto](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) e specificare le credenziali di un account che dispone del ruolo di amministratore della sicurezza o amministratore azienda.
    
2. Compilare l'elenco di nomi delle etichette, quindi eseguire questi comandi al prompt dei comandi di PowerShell:
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

Successivamente, seguire questi passaggi per pubblicare le nuove etichette di Office 365.
  
1. Dal **Home > etichette** riquadro della protezione &amp; centro conformità, fare clic su **pubblica etichette**.
    
2. Nel riquadro di **scegliere le etichette per la pubblicazione** , fare clic su **etichette scegliere per la pubblicazione**.
    
3. Nel riquadro **scegliere etichette** , fare clic su **Aggiungi** e selezionare tutte le etichette di quattro.
    
4. Fare clic su **Chiudi**.
    
5. Nel riquadro di **scegliere le etichette per la pubblicazione** , fare clic su **Avanti**.
    
6. Nel riquadro **scegliere percorsi** , fare clic su **Avanti**.
    
7. Nel riquadro **nome del criterio** digitare un nome per il set di etichette di **nome**e quindi fare clic su **Avanti**.
    
8. Nel riquadro di **Rivedere le impostazioni** , fare clic su **etichette pubblica**e quindi fare clic su **Chiudi**.
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a>Fase 3: Applicare le etichette di Office 365 per i siti di SharePoint Online

Seguire questi passaggi per applicare le etichette di Office 365 alle cartelle di documenti dei siti del team di SharePoint Online.
  
1. Nella scheda **Home page di Microsoft Office** del browser, fare clic su tessera di **SharePoint** .
    
2. Nella scheda **SharePoint** nuovo nel browser, fare clic su un sito in cui è necessario assegnata un'etichetta di Office 365.
    
3. Nella scheda sito di SharePoint nuovo del browser fare clic su **documenti**.
    
4. Fare clic sull'icona impostazioni e quindi fare clic su **Impostazioni raccolta**.
    
5. Nella sezione **autorizzazioni e gestione**, fare clic su **Applica etichetta agli elementi della raccolta**.
    
6. In **Impostazioni si applicano etichetta**, selezionare l'etichetta appropriata e quindi fare clic su **Salva**.
    
7. Chiudere la scheda per il sito di SharePoint Online.
    
8. Ripetere i passaggi da 3 a 8 per assegnare le etichette di Office 365 ai siti di SharePoint Online aggiuntivi.
    
Di seguito è riportata la configurazione risultante.
  
![Etichette di Office 365 per i quattro tipi di siti del team di SharePoint Online.](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a>Criteri DLP per i siti di SharePoint Online

Utilizzare la procedura seguente per configurare un criterio DLP che informa gli utenti quando si condivide un documento in un sito del team riservate SharePoint Online all'esterno dell'organizzazione.
  
1. Nella scheda **Home page di Microsoft Office** nel browser, fare clic sul **protezione &amp; conformità** affiancate.
    
2. Nel nuovo computer **protezione &amp; conformità** nel browser, fare clic **prevenzione della perdita di dati > criteri**.
    
3. Nel riquadro di **prevenzione della perdita di dati** , fare clic su **+ Crea un criterio**.
    
4. Nella **iniziare con un modello o creare un criterio personalizzato** riquadro, fare clic su **personalizzata**e quindi fare clic su **Avanti**.
    
5. Nel riquadro **nome del criterio** , digitare il nome per il criterio DLP livello riservato in **nome**e quindi fare clic su **Avanti**.
    
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
    
    In alternativa, digitare o incollare un suggerimento per i criteri che indica agli utenti come condividere un file all'esterno dell'organizzazione.
    
16. Fare clic su **OK**.
    
17. Nella **Selezionare l'operazione da eseguire se si rileva informazioni riservate?** riquadro, deselezionare la casella di controllo **Blocca la condivisione degli utenti e limitare l'accesso al contenuto condiviso** e quindi fare clic su **Avanti**.
    
18. Nella **si desidera attivare le operazioni criteri o di testing prima?** riquadro, fare clic su **Sì, attivarlo immediatamente**e quindi fare clic su **Avanti**.
    
19. Nel riquadro di **Rivedere le impostazioni** , fare clic su **Crea**e quindi fare clic su **Chiudi**.
    
Ne risulta la configurazione per i siti del team di SharePoint Online di livello riservato.
  
![Criteri di prevenzione della perdita dei dati per un sito del team di SharePoint Online isolato utilizzando l'etichetta Riservato Office 365.](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
Successivamente, seguire questi passaggi per configurare un criterio DLP che blocca gli utenti quando condividono un documento in un sito di SharePoint Online di livello riservato all'esterno dell'organizzazione.
  
1. Nella scheda **Home page di Microsoft Office** nel browser, fare clic sul **protezione &amp; conformità** affiancate.
    
2. Nel nuovo computer **protezione &amp; conformità** nel browser, fare clic **prevenzione della perdita di dati > criteri**.
    
3. Nel riquadro di **prevenzione della perdita di dati** , fare clic su **+ Crea un criterio**.
    
4. Nella **iniziare con un modello o creare un criterio personalizzato** riquadro, fare clic su **personalizzata**e quindi fare clic su **Avanti**.
    
5. Nel riquadro **nome del criterio** , digitare il nome per il criterio DLP livello altamente riservato in **nome**e quindi fare clic su **Avanti**.
    
6. Nel riquadro **scegliere percorsi** , fare clic su **Seleziona manualmente percorsi specifici**e quindi fare clic su **Avanti**.
    
7. Nell'elenco delle posizioni, disattivare i percorsi di **posta elettronica di Exchange** e **gli account di OneDrive** e quindi fare clic su **Avanti**.
    
8. Nel riquadro di **personalizzare i tipi di informazioni riservate che si desidera proteggere** , fare clic su **Modifica**.
    
9. Nel riquadro **scegliere i tipi di contenuto per la protezione** , fare clic su **Aggiungi** nella casella a discesa e quindi fare clic su **etichette**.
    
10. Nel riquadro **etichette** fare clic su **+ Aggiungi**, selezionare l'etichetta **Altamente riservati** , fare clic su **Aggiungi**e quindi fare clic su **Fine**.
    
11. Nel riquadro **scegliere i tipi di contenuto per la protezione** , fare clic su **Salva**.
    
12. Nel riquadro di **personalizzare i tipi di informazioni riservate che si desidera proteggere** , fare clic su **Avanti**.
    
13. Nella **Selezionare l'operazione da eseguire se si rileva informazioni riservate?** riquadro, fare clic su **Personalizza la descrizione e posta elettronica**.
    
14. Nel riquadro **suggerimenti sui criteri di personalizzazione e notifiche tramite posta elettronica** , fare clic su **Personalizza il testo del suggerimento criteri**.
    
15. Nella casella di testo digitare o incollare negli articoli seguenti:
    
  - Per condividere con un utente esterno all'organizzazione, scaricare il file e quindi aprirlo. Fare clic su File, Proteggi documento, Crittografa con password, quindi specificare una password complessa. Inviare la password in un'e-mail separata o con altri mezzi di comunicazione.
    
    In alternativa, digitare o incollare un suggerimento per i criteri che indica agli utenti come condividere un file all'esterno dell'organizzazione.
    
16. Fare clic su **OK**.
    
17. Nella **Selezionare l'operazione da eseguire se si rileva informazioni riservate?** riquadro, selezionare **Richiedi motivazione aziendale per eseguire l'override**e quindi fare clic su **Avanti**.
    
18. Nella **si desidera attivare le operazioni criteri o di testing prima?** riquadro, fare clic su **Sì, attivarlo immediatamente**e quindi fare clic su **Avanti**.
    
19. Nel riquadro di **Rivedere le impostazioni** , fare clic su **Crea**e quindi fare clic su **Chiudi**.
    
Ne risulta la configurazione per i siti del team di SharePoint Online di livello estremamente riservato.
  
![Criteri di prevenzione della perdita dei dati per un sito del team di SharePoint Online isolato utilizzando l'etichetta Estremamente riservato Office 365.](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a>Passaggio successivo

[Proteggere i file di SharePoint Online con la protezione delle informazioni di Azure](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a>Vedere anche

[Protezione di file e siti di SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Proteggere i siti di SharePoint Online in un ambiente di sviluppo e di testing](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Guida sulla sicurezza Microsoft per organizzazioni che si occupano della campagna politica, no profit e altre organizzazioni agili](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)


