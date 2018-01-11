---
title: Registrare iOS e dispositivi Android nell'ambiente di sviluppo e di testing Microsoft Enterprise 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "Riepilogo: Utilizzare questa guida dei laboratori di testing per registrare i dispositivi nell'ambiente di sviluppo e di testing Microsoft 365 e gestirle in modalità remota."
ms.openlocfilehash: 71d04b0d2a59683ff09ad4256ed8fc82e89e876a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a>Registrare iOS e dispositivi Android nell'ambiente di sviluppo e di testing Microsoft Enterprise 365

 **Riepilogo:** Utilizzare questa guida dei laboratori di testing per registrare i dispositivi nell'ambiente di sviluppo e di testing Microsoft 365 e gestirle in modalità remota.
  
Microsoft Enterprise mobilità famiglia di prodotti (EMS) contribuisce a migliorare la produttività utilizzando le applicazioni preferite e dispositivi proteggendo al contempo i dati dell'organizzazione i dipendenti. Per ulteriori informazioni, vedere [Security (EMS) + mobilità aziendale](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Se è necessario applicare criteri di sicurezza a livello di dispositivi, è necessario registrare i dispositivi in Microsoft Intune. La registrazione dei dispositivi non consente solo di gestire i dispositivi aziendali, ma anche quelli personali (BYOD) e condivisi, a seconda dei criteri legali dell'organizzazione.
  
Seguendo le istruzioni fornite in questo articolo, sarà possibile registrare e verificare le funzionalità di gestione di dispositivi mobili base iOS e dei dispositivi Android nell'ambiente di sviluppo e di testing Microsoft 365.
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>Fase 1: Creare l'ambiente di sviluppo e di testing Microsoft 365

Seguire le istruzioni [nell'ambiente di sviluppo e di testing The Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-customize-the-microsoft-intune-company-portal-app"></a>Fase 2: personalizzare l'app Portale aziendale di Microsoft Intune

Seguire questa procedura per personalizzare l'app Portale aziendale di Microsoft Intune per l'azienda fittizia:
  
1. In una nuova scheda, aprire la console di amministrazione di Microsoft Intune ([https://manage.microsoft.com](https://manage.microsoft.com)).
    
2. Fare clic su **amministratore** nel riquadro di spostamento e quindi fare clic su **Gestione dei dispositivi mobili** nel riquadro **amministrazione** .
    
3. Nell'elenco **attività** selezionare **Impostare Mobile Device Management autorità**. Verificare che sia impostata su **Microsoft Intune**.
    
4. Nel riquadro **amministrazione** , fare clic su **Portale aziendale**.
    
5. Nel riquadro **Portale della società** , configurare le impostazioni seguenti:
    
  - Nome della società: \<il nome della società fittizia >
    
  - Nome del contatto reparto IT: **User5**
    
  - Numero di telefono del reparto IT: **555-1234**
    
  - Indirizzo di posta elettronica reparto IT: **User5 @**\<nome della società fittizia > **. onmicrosoft.com** (l'indirizzo di posta elettronica dell'account User5)
    
6. In **personalizzazione**, selezionare **verde** nel **colore del tema**.
    
7. Fare clic su **Salva**.
    
Successivamente, verrà installata l'app Portale aziendale di Microsoft Intune e verrà registrato un dispositivo iOS o Android; infine, verrà testata la funzionalità di gestione di base dalla console di amministrazione di Microsoft Intune.
  
## <a name="phase-3-for-ios-devices-only-enroll-and-manage-an-ios-device"></a>Fase 3 (solo per i dispositivi iOS): registrare e gestire un dispositivo iOS

Per registrare un dispositivo iOS per la gestione tramite Intune, è necessario quanto segue:
  
- Un dispositivo iOS, ad esempio un Apple iPad o un iPhone.
    
- Conoscenza del passcode del dispositivo iOS.
    
- Un ID di Apple (un nome account e password). Se non già presente, passare al [sito Web di Apple ID](https://appleid.apple.com/#!&amp;page=signin) e fare clic su **Crea il proprio ID Apple**. Creare un ID di Apple corrispondente all'account amministratore globale della sottoscrizione a Office 365. Registrare il nuovo nome di account Apple ID e la password in un luogo sicuro.
    
Per gestire i dispositivi iOS e Mac, Intune richiede un certificato di Apple Push Notification Service (APNs). Dopo aver aggiunto il certificato in Intune, gli utenti possono installare l'app Portale aziendale di Microsoft Intune per registrare i dispositivi oppure l'amministratore può configurare la gestione dei dispositivi iOS aziendali.
  
È necessario un file di richiesta di firma del certificato per richiedere un certificato di relazione di trust dal Portale Apple Push Certificates. Per ottenere un file di richiesta di firma del certificato:
  
1. Nella console di amministrazione di Microsoft Intune, fare clic su **amministratore** nel riquadro di spostamento.
    
    Nel riquadro **amministrazione** , aprire **gestione dei dispositivi mobili > iOS e Mac OS X**, quindi fare clic su **Carica un certificato APNs** nelle **attività**. 
    
2. Nel riquadro di **un certificato APNs caricato** , fare clic su **Scarica la richiesta di certificato APNs**. Salvare il file di richiesta (.csr) in locale con il nome **test di sviluppo**di firma del certificato.
    
Per ottenere il certificato del servizio APN (Apple Push Notification):
  
1. Aprire una nuova scheda, accedere al [Portale dei certificati Push Apple](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)e accedere con l'ID di Apple.
    
2. Nella pagina **Introduzione** fare clic su **Crea un certificato**.
    
3. Nella pagina **Condizioni di utilizzo** selezionare **è possibile leggere e accettare i termini e le condizioni**e quindi fare clic su **accetta**.
    
4. Nella pagina **Crea un nuovo certificato Push** fare clic su **Sfoglia** e selezionare il file di **sviluppo test.csr** salvato nella procedura precedente e quindi fare clic su **Carica**. Quando viene richiesto di aprire un file json, salvarlo nella stessa cartella in cui è memorizzato il file test.csr sviluppatori.
    
5. Aprire il [Portale dei certificati Push Apple](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) in un'altra scheda e per i **certificati per i server di terze parti**, fare clic su **Download**.
    
6. Quando viene richiesto di aprire un file .pem, salvarlo con il nome **test.pem sviluppatori** nella stessa cartella in cui è memorizzato il file test.csr sviluppatori. Si tratta del certificato APNs.
    
Per caricare il certificato APNs in Intune:
  
1. Nella scheda console Amministrazione Microsoft Intune, nella pagina **caricare un certificato APNs** fare clic su **Carica il certificato APNs**.
    
2. Fare clic su **Sfoglia** e specificare il file **test.pem sviluppatori** .
    
3. Fare clic su **Apri**, digitare il nome dell'account ID Apple e quindi fare clic su **Carica**. È consigliabile visualizzato un messaggio **pronto per la registrazione** nella pagina **iOS e il programma di installazione di MaxOS X Mobile Device Management** .
    
Con il certificato APNs installato, Intune può registrare e gestire i dispositivi iOS applicando i criteri ai dispositivi mobili registrati.
  
Per scaricare l'app Portale aziendale di Microsoft Intune e registrare il dispositivo iOS:
  
1. Dal dispositivo iOS, accedere con l'ID Apple.
    
2. Aprire l'app **Store Apple** .
    
3. Toccare **Microsoft Intune portale della società**, quindi **ottenere**e quindi **installare**digitare **intune** nella casella di ricerca.
    
4. Dopo l'installazione, scegliere **Apri**.
    
5. Nella schermata **Intune portale della società** , accedere con l'account amministratore globale di Office 365.
    
6. Nella schermata di **Installazione di accesso società** , toccare **iniziare**e quindi **Continua** due volte.
    
7. Nella **prossimamente?** dello schermo, quindi scegliere **registrazione**.
    
8. Nella **amministratore attiva?** dello schermo, quindi scegliere **Attiva**.
    
9. Nella schermata di **Gestione dei profili** , scegliere **Installa**.
    
10. **Immettere un Passcode**, digitare il codice del dispositivo iOS.
    
11. Nella schermata **prossimamente** scegliere **registrazione**.
    
12. In **Installa profilo**, scegliere **Installa**.
    
13. Nella pagina **avviso** scegliere **Installa**.
    
14. In **Gestione remota**scegliere **Trust**.
    
15. Scegliere **Fine** per completare il processo di registrazione.
    
16. Quando viene richiesto di **aprire la pagina in "Portal Comp"?**, scegliere **Apri**.
    
17. Nella schermata di **Installazione di accesso società** , toccare **iniziare**e quindi **Fine**.
    
18. Nella schermata principale dell'app Portale aziendale di Microsoft Intune, viene visualizzato:
    
  - Un banner verde.
    
  - Il nome dell'azienda fittizia in alto a sinistra.
    
  - Il nome del dispositivo iOS elencato in **Dispositivi in uso**.
    
  - Nella sezione **servizio di supporto tecnico** , il **Nome del contatto** del **User5** con il numero di telefono di **555-1234** e un pulsante **contatti tramite posta elettronica** .
    
Microsoft Intune fornisce sia la funzionalità di blocco remoto sia quella di reimpostazione del passcode. Se un utente perde il proprio dispositivo, è possibile bloccare il dispositivo in modalità remota. Se un utente dimentica il proprio passcode, è possibile rimuovere il passcode in modalità remota.
  
Per bloccare un dispositivo iOS in remoto:
  
1. Dal computer di amministrazione, scegliere la scheda console di amministrazione di Microsoft Intune del browser, fare clic su **gruppi** nel riquadro di spostamento sinistro.
    
2. Nel riquadro **gruppi** aprire **tutti i dispositivi > dispositivi mobili tutti > tutti i dispositivi gestiti diretto**.
    
3. Nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic sulla scheda **dispositivi** .
    
4. Nell'elenco dei dispositivi, fare clic sul dispositivo iOS.  
    
5. Dal dispositivo iOS, verificare che sia nella schermata principale.  
    
6. Dal computer di amministrazione, sulla barra delle applicazioni, fare clic su **remoto attività > blocco remoto**. Guardare il dispositivo iOS quando attivata la sullo schermo del blocco.
    
Per rimuovere il passcode:
  
1. Dal computer di amministrazione, nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic sulla scheda **dispositivi** .
    
2. Nell'elenco fare clic su dispositivo iOS. Nella barra delle applicazioni fare clic su **remoto attività > Passcode Reset**. Attendere un minuto.
    
3. Dal dispositivo iOS sbloccarlo e si noti che non è più un passcode. Per modificare nuovamente il passcode, passare a **Impostazioni**, quindi **Passcode**.
    
## <a name="phase-3-for-android-devices-only-enroll-and-manage-an-android-device"></a>Fase 3 (solo per i dispositivi Android): registrare e gestire un dispositivo Android

Per registrare un dispositivo Android per la gestione tramite Intune, è necessario quanto segue:
  
- Un dispositivo Android.
    
- Conoscenza del passcode del dispositivo.
    
Per scaricare l'app Portale aziendale di Intune e registrare il dispositivo Android:
  
1. Da un dispositivo Android, passare all' **Archivio per la riproduzione di Google**e quindi **Iniziare a**.
    
2. Digitare **intune** nella casella di ricerca e quindi scegliere **portale della società intune** nei risultati della ricerca.
    
3. Scegliere l'elemento **Intune portale della società** , quindi **installare**.
    
4. Sullo schermo **per completare l'installazione account** scegliere **Continua**ed **elementi da ignorare**.
    
5. Nel **Portale della società Intune**, scegliere **accetta**. Installa app.
    
6. Scegliere **Apri**, quindi **effettuare l'accesso**.
    
7. Nella schermata **Intune portale della società** , accedere con l'account amministratore globale di Office 365.
    
8. Nella schermata di **Installazione di accesso società** , toccare due volte **avviare**e quindi **Continua** .
    
9. Nella **prossimamente?** dello schermo, quindi scegliere **registrazione**.
    
10. Nella **amministratore attiva?** dello schermo, quindi scegliere **Activate.**
    
11. Nella schermata di **Criteri di Privacy** , selezionare **sono stati esaminati** e quindi toccare **Conferma**. Attendere il processo di registrazione per il completamento.
    
12. Nella schermata di **Installazione di accesso società** , scegliere **Continua**e quindi scegliere **Fine**.
    
13. Nella schermata principale dell'app Portale aziendale di Microsoft Intune, verrà visualizzato un banner verde e il nome dell'azienda fittizia in alto a sinistra.
    
14. Scegliere **i dispositivi**. Verrà visualizzato il nome del dispositivo Android nell'elenco.
    
15. Scegliere **contatto IT**. Verrà visualizzato il numero di telefono di **555-1234**, un pulsante **contatti tramite posta elettronica** e IT di contatto di **User5**.
    
Microsoft Intune fornisce sia la funzionalità di blocco remoto sia quella di reimpostazione del passcode. Se un utente perde il proprio dispositivo, è possibile bloccare il dispositivo in modalità remota. Se un utente dimentica il proprio passcode, è possibile reimpostare il passcode in modalità remota.
  
Per bloccare un dispositivo Android in remoto:
  
1. Dal computer di amministrazione, scegliere la scheda console di amministrazione di Microsoft Intune del browser, fare clic su **gruppi** nel riquadro di spostamento sinistro.
    
2. Nel riquadro **gruppi** aprire **tutti i dispositivi > dispositivi mobili tutti > tutti i dispositivi gestiti diretto**.
    
3. Nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic sulla scheda **dispositivi** .
    
4. Nell'elenco dei dispositivi, fare clic sul dispositivo Android.  
    
5. Dal dispositivo Android, verificare che sia nella schermata principale.  
    
6. Dal computer di amministrazione, sulla barra delle applicazioni, fare clic su **remoto attività > blocco remoto**. Quando richiesto, fare clic su **Sì**.
    
7. Verificare che il dispositivo Android passi alla schermata di blocco.
    
Quando si reimposta il passcode per i dispositivi Android, il portale di amministrazione Intune genera e consente di configurare un passcode complessa.
  
Per reimpostare il passcode in remoto:
  
1. Dal computer di amministrazione, nella scheda console Amministrazione Microsoft Intune del browser, nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic su dispositivo Android.
    
2. Nella barra delle applicazioni fare clic su **remoto attività > Passcode Reset**.
    
3. Nella **attività remota: Passcode Reset** prompt, fare clic su **Sì**. Attendere un minuto.
    
4. Nel riquadro di **Tutti i dispositivi con gestione diretta** , fare clic su **Visualizza proprietà**.
    
5. In **Passcode Reset**, si noti il nuovo codice.
    
6. Dal dispositivo Android, immettere il nuovo passcode nella schermata di blocco.  
    
7. Per modificare nuovamente il passcode, passare a **Impostazioni**, scegliere **dispositivo**, scegliere **schermo Blocca**, immettere nuovamente il nuovo passcode, scegliere **blocco dello schermo**e la scelta per il passcode.
    
> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
  
## <a name="see-also"></a>Vedere anche

[L'ambiente di sviluppo e di testing Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Criteri MAM per l'ambiente di sviluppo e di testing Microsoft 365 Enterprise](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)

[Sicurezza (EMS) + mobilità aziendale](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


