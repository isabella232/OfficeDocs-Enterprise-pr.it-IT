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
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: 'Riepilogo: Office 365 dati ed etichette perdita criterio DLP criteri applicati ai siti dei team SharePoint Online con diversi livelli di protezione delle informazioni.'
ms.openlocfilehash: a6413ac556cf63cbe7491180d65b4425cd0dba3d
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a>Proteggere i file di SharePoint Online con Office 365 etichette e DLP

 **Riepilogo:** Office 365 dati ed etichette perdita criterio DLP criteri applicati ai siti dei team SharePoint Online con diversi livelli di protezione delle informazioni.
  
Utilizzare i passaggi descritti in questo articolo per progettare e distribuire le etichette di Office 365 e criteri DLP per la linea di base, importanti o altamente riservati team siti di SharePoint Online. Per ulteriori informazioni su questi tre livelli di protezione, vedere [file e siti di SharePoint Online sicura](secure-sharepoint-online-sites-and-files.md).
  
## <a name="office-365-labels-for-your-sharepoint-online-sites"></a>Etichette di Office 365 per i siti di SharePoint Online

Esistono tre fasi per creare e poi assegnare le etichette di Office 365 ai siti del team di SharePoint Online.
  
### <a name="phase-1-determine-the-office-365-label-names"></a>Fase 1: Determinare i nomi delle etichette di Office 365

In questa fase si definiscono i nomi etichette di Office 365 per i quattro livelli di protezione delle informazioni applicati ai siti del team di SharePoint Online. La tabella seguente elenca i nomi consigliati per ogni livello.
  
|**Livello di protezione del sito del team di SharePoint Online**|**Nome etichetta**|
|:-----|:-----|
|Pubblico di base  <br/> |Pubblico interno  <br/> |
|Privato di base  <br/> |Private  <br/> |
|Dati sensibili  <br/> |Dati sensibili  <br/> |
|Highly Confidential (Riservatezza elevata)  <br/> |Highly Confidential (Riservatezza elevata)  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a>Fase 2: creare le etichette di Office 365

In questa fase si creano e poi pubblicano le etichette specificate per i diversi livelli di protezione delle informazioni.
  
Per creare le etichette, è possibile utilizzare l'interfaccia di amministrazione di Office 365 o Microsoft PowerShell.
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a>Creare etichette di Office 365 con l'interfaccia di amministrazione di Office 365

1. Accedere al portale di Office 365 con un account che dispone del ruolo Amministratore della sicurezza oppure Amministratore della società. Per informazioni, vedere [Dove accedere a Office 365 per le aziende](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dalla scheda **Microsoft Office Home** fare clic sul riquadro **Amministratore**.
    
3. Scheda di **interfaccia di amministrazione di Office** nuovo del browser fare clic su **Admin Center > sicurezza &amp; conformità**.
    
4. Dalla nuova **Home - sicurezza &amp; conformità** scheda del browser, fare clic su **classificazioni > etichette**.
    
5. Dal riquadro **Home > Etichette** fare clic su **Crea un'etichetta**.
    
6. Nel riquadro di **nome dell'etichetta** , digitare il nome dell'etichetta e quindi fare clic su **Avanti**.
    
7. Nel riquadro delle **impostazioni dell'etichetta** fare clic su **Avanti**.
    
8. Nel riquadro di **Rivedere le impostazioni** , fare clic su **Crea l'etichetta**e quindi fare clic su **Chiudi**.
    
9. Ripetere i passaggi da 5 a 8 per etichette aggiuntive.
    
### <a name="create-office-365-labels-with-powershell"></a>Creare etichette di Office 365 con PowerShell

1. [Connetti a Office 365 Security &amp; centro conformità utilizzando PowerShell remoto](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) e specificare le credenziali di un account che dispone del ruolo di amministratore della sicurezza o amministratore azienda.
    
2. Compilare l'elenco dei nomi delle etichette ed eseguire questi comandi al prompt dei comandi di PowerShell:
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

Successivamente, seguire questa procedura per pubblicare le nuove etichette di Office 365.
  
1. Dal **Home > etichette** riquadro della protezione &amp; centro conformità, fare clic su **pubblica etichette**.
    
2. Nel riquadro **Choose labels to publish** (Scegli etichette da pubblicare) fare clic su **Choose labels to publish** (Scegli etichette da pubblicare).
    
3. Nel riquadro **Choose labels** (Scegli etichette) fare clic su **Aggiungi** e selezionare le quattro etichette.
    
4. Fare clic su **Fine**.
    
5. Nel riquadro **Choose labels to publish** (Scegli etichette da pubblicare) fare clic su **Avanti**.
    
6. Nel riquadro **Choose locations** (Scegli posizioni) fare clic su **Avanti**.
    
7. Nel riquadro **nome del criterio** digitare un nome per il set di etichette di **nome**e quindi fare clic su **Avanti**.
    
8. Nel riquadro di **Rivedere le impostazioni** , fare clic su **etichette pubblica**e quindi fare clic su **Chiudi**.
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a>Fase 3: applicare le etichette di Office 365 ai siti di SharePoint Online

Seguire questa procedura per applicare le etichette di Office 365 alle cartelle di documenti dei siti del team di SharePoint Online.
  
1. Dalla scheda **Microsoft Office Home** del browser fare clic sul riquadro **SharePoint**.
    
2. Nella nuova scheda **SharePoint** del browser selezionare un sito per cui è necessario assegnare un'etichetta di Office 365.
    
3. Nella nuova scheda del sito di SharePoint del browser fare clic su **Documenti**.
    
4. Fare clic sull'icona delle impostazioni e selezionare **Impostazioni libreria**.
    
5. In **Autorizzazioni e gestione** fare clic su **Apply label to items in this library** (Applica etichetta agli elementi in questa libreria).
    
6. In **Impostazioni si applicano etichetta**, selezionare l'etichetta appropriata e quindi fare clic su **Salva**.
    
7. Chiudere la scheda per il sito di SharePoint Online.
    
8. Ripetere i passaggi da 3 a 8 per assegnare le etichette di Office 365 a siti di SharePoint Online aggiuntivi.
    
Di seguito è riportata la configurazione risultante.
  
![Etichette di Office 365 per i quattro tipi di siti del team di SharePoint Online.](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a>Criteri di prevenzione della perdita dei dati per siti di SharePoint Online

Seguire questa procedura per configurare un criterio della prevenzione della perdita dei dati che notifica agli utenti la condivisione di un documento in un sito sensibile del team di SharePoint Online all'esterno dell'organizzazione.
  
1. Nella scheda **Home page di Microsoft Office** nel browser, fare clic sul **protezione &amp; conformità** affiancate.
    
2. Nel nuovo computer **protezione &amp; conformità** nel browser, fare clic **prevenzione della perdita di dati > criteri**.
    
3. Nel riquadro **Prevenzione perdita dati** fare clic su **+ Crea un criterio**.
    
4. Nella **iniziare con un modello o creare un criterio personalizzato** riquadro, fare clic su **personalizzata**e quindi fare clic su **Avanti**.
    
5. Nel riquadro **nome del criterio** , digitare il nome per il criterio DLP livello riservato in **nome**e quindi fare clic su **Avanti**.
    
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
    
    In alternativa, digitare o incollare un suggerimento per i criteri che indica agli utenti come condividere un file all'esterno dell'organizzazione.
    
16. Fare clic su **OK**.
    
17. Nella **Selezionare l'operazione da eseguire se si rileva informazioni riservate?** riquadro, deselezionare la casella di controllo **Blocca la condivisione degli utenti e limitare l'accesso al contenuto condiviso** e quindi fare clic su **Avanti**.
    
18. Nella **si desidera attivare le operazioni criteri o di testing prima?** riquadro, fare clic su **Sì, attivarlo immediatamente**e quindi fare clic su **Avanti**.
    
19. Nel riquadro di **Rivedere le impostazioni** , fare clic su **Crea**e quindi fare clic su **Chiudi**.
    
Di seguito è riportata la configurazione risultante per i siti sensibili del team di SharePoint Online.
  
![Criteri di prevenzione della perdita dei dati per un sito del team di SharePoint Online isolato utilizzando l'etichetta Riservato Office 365.](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
Seguire questa procedura per configurare un criterio della prevenzione della perdita dei dati che blocchi gli utenti in fase di condivisione di un documento in un sito con riservatezza elevata del team di SharePoint Online all'esterno dell'organizzazione.
  
1. Nella scheda **Home page di Microsoft Office** nel browser, fare clic sul **protezione &amp; conformità** affiancate.
    
2. Nel nuovo computer **protezione &amp; conformità** nel browser, fare clic **prevenzione della perdita di dati > criteri**.
    
3. Nel riquadro **Prevenzione perdita dati** fare clic su **+ Crea un criterio**.
    
4. Nella **iniziare con un modello o creare un criterio personalizzato** riquadro, fare clic su **personalizzata**e quindi fare clic su **Avanti**.
    
5. Nel riquadro **nome del criterio** , digitare il nome per il criterio DLP livello altamente riservato in **nome**e quindi fare clic su **Avanti**.
    
6. Nel riquadro **Choose locations** (Scegli posizioni) fare clic su **Let me choose specific locations** (Consenti di scegliere posizioni specifiche) e fare clic su **Avanti**.
    
7. Nell'elenco delle posizioni, disattivare i percorsi di **posta elettronica di Exchange** e **gli account di OneDrive** e quindi fare clic su **Avanti**.
    
8. Nel riquadro **Customize the types of sensitive info you want to protect** (Personalizza i tipi di informazioni sensibili da proteggere) fare clic su **Modifica**.
    
9. Nel riquadro **scegliere i tipi di contenuto per la protezione** , fare clic su **Aggiungi** nella casella a discesa e quindi fare clic su **etichette**.
    
10. Nel riquadro **etichette** fare clic su **+ Aggiungi**, selezionare l'etichetta **Altamente riservati** , fare clic su **Aggiungi**e quindi fare clic su **Fine**.
    
11. Nel riquadro **Choose the types of content to protect** (Scegli i tipi di contenuto da proteggere) fare clic su **Salva**.
    
12. Nel riquadro **Customize the types of sensitive info you want to protect** (Personalizza i tipi di informazioni sensibili da proteggere) fare clic su **Avanti**.
    
13. Nel riquadro **What do you want to do if we detect sensitive info?** (Selezionare come procedere in caso di informazioni sensibili rilevate) fare clic su **Customize the tip and email** (Personalizza suggerimento e messaggio di posta elettronica).
    
14. Nel riquadro **Customize policy tips and email notifications** (Personalizza i suggerimenti per i criteri e le notifiche tramite posta elettronica) fare clic su **Customize the policy tip text** (Personalizza testo suggerimento per criterio).
    
15. Nella casella di testo digitare o incollare quanto segue:
    
  - Per condividere un file con un utente all'esterno dell'organizzazione, scaricare il file e aprirlo. Fare clic su File, Proteggi documento, Crittografa con password e specificare una password complessa. Inviare la password in un messaggio di posta elettronica separato o un altro mezzo di comunicazione.
    
    In alternativa, digitare o incollare un suggerimento per i criteri che indica agli utenti come condividere un file all'esterno dell'organizzazione.
    
16. Fare clic su **OK**.
    
17. Nella **Selezionare l'operazione da eseguire se si rileva informazioni riservate?** riquadro, selezionare **Richiedi motivazione aziendale per eseguire l'override**e quindi fare clic su **Avanti**.
    
18. Nella **si desidera attivare le operazioni criteri o di testing prima?** riquadro, fare clic su **Sì, attivarlo immediatamente**e quindi fare clic su **Avanti**.
    
19. Nel riquadro di **Rivedere le impostazioni** , fare clic su **Crea**e quindi fare clic su **Chiudi**.
    
Di seguito è riportata la configurazione risultante per i siti con riservatezza elevata del team di SharePoint Online.
  
![Criteri di prevenzione della perdita dei dati per un sito del team di SharePoint Online isolato utilizzando l'etichetta Estremamente riservato Office 365.](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a>Passaggio successivo

[Proteggere i file di SharePoint Online con Azure Information Protection](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a>Vedere anche

[Protezione di file e siti di SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Proteggere i siti di SharePoint Online in un ambiente di sviluppo e di testing](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Guida sulla sicurezza Microsoft per organizzazioni che si occupano della campagna politica, no profit e altre organizzazioni agili](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)


