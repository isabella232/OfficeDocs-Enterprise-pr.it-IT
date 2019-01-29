---
title: Assistenti distribuzione per i servizi di Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid:
- MET150
- MET150
- BCS160
ms.assetid: 165f46e8-3533-4d76-be57-97f81ebd40f2
description: Procedure guidate di distribuzione per Office 365 forniscono supporto self-guidata per la configurazione di Office 365.
ms.openlocfilehash: 7b677e70332c7a28156c572bb9daf5cc6c9e4e91
ms.sourcegitcommit: 792fe2ccc860517fe3dcbc9c668bae97f39ae7c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2019
ms.locfileid: "29604497"
---
# <a name="deployment-advisors-for-office-365-services"></a>Assistenti distribuzione per i servizi di Office 365

Consulenti distribuzione per Office 365 forniscono supporto self-guidata per la configurazione di Office 365 per l'organizzazione. È sufficiente selezionare una procedura guidata e accedere a Office 365. 

Mentre si selezionano le caratteristiche e le opzioni di distribuzione, la procedura guidata crea un piano di procedura di configurazione personalizzato in base alle esigenze. Verrà visualizzato un insieme completo di istruzioni, video, articoli di riferimento e gli script. Alcune procedure guidate sono automazione che verrà modificate alcune impostazioni, mentre in altre aree delle procedure guidate vengono modificate le impostazioni e dati con la procedura guidata Guida. È possibile utilizzare queste procedure guidate in qualsiasi momento, anche durante la pianificazione o dopo aver già configurato i servizi per ulteriori informazioni sulle opzioni e funzionalità di Office 365.
  
## <a name="windows-10-with-office-365"></a>Windows 10 con Office 365

[Preparazione distribuzione Microsoft 365](https://aka.ms/microsoft365setupguide)
  
Microsoft 365 è una soluzione completa e intelligente che include Office 365, Windows 10 e mobilità aziendale + sicurezza. Consente di Microsoft 365 tutti si trovino creative e lavoro contemporaneamente, in modo protetto. Utilizzare questa guida per configurare i dispositivi Windows 10 o l'aggiornamento nei computer degli utenti a Windows 10, optional distribuzione di Office apps Analitica Windows e Defender avanzate rischio la protezione di Windows (Microsoft 365 Enterprise E5 plan solo).


## <a name="mail-migration-and-protection"></a>Migrazione della posta e protezione

### <a name="prepare-your-environment"></a>Predisporre l'ambiente 
[Guida ambiente Prepare](https://go.microsoft.com/fwlink/?linkid=2005213) è il punto di partenza. Commenti degli obiettivi di pianificazione per assicurarsi di aggiungere domini, gli utenti di creare e assegnare licenze nell'ordine corretto. Ciò è particolarmente importante se si prevede di eseguire la migrazione di posta elettronica o configurare una distribuzione ibrida. 

### <a name="exchange-migration-advisor"></a>Assistente migrazione di Exchange
[Advisor migrazione della posta di Office 365](https://aka.ms/office365setup) consentono di spostare le cassette postali di sistema di posta elettronica corrente a Exchange Online in Office 365 con strumenti automatici e istruzioni dettagliate. Consigliabile sarà il percorso di migrazione migliore per l'organizzazione in base al sistema di posta elettronica corrente, il numero di cassette postali che si desidera eseguire la migrazione e come si prevede di gestire utenti e l'accesso degli utenti.
  
Gli [contatti Gmail e dell'Assistente del calendario](https://aka.ms/gmailcontactscalendar) vengono fornite istruzioni dettagliate per la migrazione dei contatti Gmail e gli elementi del calendario di Google a Office 365. Quando si esegue la migrazione delle cassette postali Gmail dell'utente a Office 365, vengono eseguita la migrazione di messaggi di posta elettronica, ma contatti ed elementi del calendario non sono. La procedura guidata vengono fornite le procedure per l'importazione dei contatti Gmail e gli elementi del calendario di Google a Office 365.
  
### <a name="exchange-online-protection"></a>Exchange Online Protection
Microsoft [Exchange Online Protection (EOP)](https://aka.ms/EOPguidance) è una basata su cloud filtro della posta elettronica servizio che consente di proteggere l'organizzazione da posta indesiderata e malware e include funzionalità per proteggere l'organizzazione di violazioni dei criteri di messaggistica.
  

## <a name="file-creation-storage-and-sharing"></a>Creazione di file, archiviazione e la condivisione

### <a name="office-365-proplus"></a>Office 365 ProPlus
[Office ProPlus quick start guide](https://aka.ms/OPPquickstartguide) illustra i passaggi per l'installazione di Office in un PC o Mac per la propria azienda e include suggerimenti per sfruttare tutti introduttiva a Office.

[Office ProPlus advisor distribuzione](https://aka.ms/o365proplusdeploy) consente di ottenere gli utenti rendano le ultime versioni di Office. In questo advisor illustra i passaggi che consentono agli utenti di installare Office direttamente dal portale di Office 365 online o per la distribuzione di Office per gli utenti da una posizione locale. Sono incluse istruzioni per l'utilizzo di System Center Configuration Manager, uno script di avvio di criteri di gruppo, un'immagine del disco del sistema operativo o Remote Desktop Services (RDS) condivisi attivazione.

### <a name="onedrive-for-business"></a>OneDrive for Business
Utilizzare [OneDrive for Business quick start guide](https://aka.ms/ODfBquickstartguide) per iniziare rapidamente a OneDrive for Business per l'archiviazione dei file, condivisione e la sincronizzazione.
  
### <a name="sharepoint-online"></a>SharePoint Online
  
[Avviare SharePoint Online veloce](https://aka.ms/SPOquickstartguide) viene illustrato come impostare SharePoint nel cloud per la memorizzazione dei documenti e gestione del contenuto. Questa configurazione di base è sufficiente se non si dispone di una grande quantità di dati per la migrazione o un Server di SharePoint locale che si desidera continuare l'esecuzione di una configurazione ibrida.
  
[SharePoint Online advisor distribuzione](https://aka.ms/spoguidance) consente di scegliere l'opzione di distribuzione che risultati ottimali per l'organizzazione e vengono forniti i passaggi per la configurazione delle funzionalità di SharePoint Online per soddisfare le esigenze aziendali. Scegliere la distribuzione in cloud, distribuzione ibrida o migrazione in locale-al cloud. Quindi seguire le istruzioni per la configurazione delle funzionalità di SharePoint Online, ad esempio la memorizzazione dei file e la condivisione, la condivisione di file esterno, raccolte siti, le impostazioni globali e profili utente e il sito del team di Office 365.
  
## <a name="security-and-identity"></a>Identità e protezione

### <a name="azure-active-directory-connect-azure-ad-connect-advisor"></a>Preparazione di Active Directory connettersi (Azure Active Directory Connect) Azure
[Preparazione di Azure Active Directory Connect](https://aka.ms/aadconnectpwsync) è una Guida passo passo che illustra come aggiungere informazioni sull'account utente a Office 365 senza creare manualmente ogni utente. Viene inoltre illustrato come configurare l'autenticazione di sincronizzazione o pass-through di hash password, in modo che gli utenti possono accedere alla posta elettronica e il dominio utilizzando la stessa password. Se si sceglie di impostare federati sign-in con ADFS, in questa guida offre anche la procedura seguente per la distribuzione di ADFS in un nuovo server o in una farm di Windows Server 2012 R2 esistente. Azure Active Directory Connect sostituisce le versioni precedenti di strumenti di integrazione di identità, ad esempio DirSync e sincronizzazione di Azure Active Directory e viene utilizzato principalmente per l'aggiunta di utenti e altri dati di Azure Active Directory per Office 365.
  
### <a name="azure"></a>Azure
La [Guida all'installazione di base di Azure Active Directory](https://aka.ms/azureadbasic) consente di configurare la funzionalità di gestione dell'accesso basato sui gruppo, self-service la reimpostazione della password per le applicazioni cloud e il Proxy di applicazione di Azure Active Directory per la pubblicazione di applicazioni web locale.
  
La [Guida all'installazione di Azure Active Directory Premium](https://aka.ms/aadpguidance) consente di abilitare le caratteristiche di Azure Active Directory Premium (Azure Active Directory Premium), che offre funzionalità di gestione come autenticazione a più fattori, single sign-on (SSO), la registrazione di dispositivi, di identità password self-service e gestione dei gruppi, il monitoraggio della protezione.
  
### <a name="verify-your-domain"></a>Verify your domain
Lo strumento di [verifica del dominio in Office 365](https://aka.ms/verifyyourdomaino365) advisor consente di personalizzare Office 365 aggiungendo il proprio nome di dominio (detto anche il nome del sito Web).
  
## <a name="communication-and-online-conferencing"></a>La comunicazione e le conferenze online

### <a name="office-365-groups"></a>Gruppi di Office 365
[Guida all'installazione di Office 365 gruppi](https://aka.ms/groupsguide)

Office 365 gruppi è un'area di lavoro condivisa per la posta elettronica, le conversazioni, i file e gli eventi dove membri del gruppo collettivamente possono ottenere stampe fine. I gruppi in Office 365 consentono di scegliere un gruppo di persone che si desiderano collaborare con e organizzare facilmente una raccolta di risorse per le persone da condividere. Non è necessario preoccupare manualmente assegnazione delle autorizzazioni per tutte le risorse poiché consente di aggiungere membri al gruppo automaticamente si attribuisce loro le autorizzazioni necessarie per gli strumenti del gruppo.
  
### <a name="microsoft-teams"></a>Microsoft Teams

[Preparazione distribuzione team](https://aka.ms/teamsguidance)
  
Microsoft Teams è il servizio di collaborazione basato su chat in Office 365 che fornisce le aree di lavoro del team per le chat, le chiamate, le riunioni e messaggi privati. Preparazione distribuzione per i team consente di impostare e configurare l'esperienza di team ottimale con Exchange Online, SharePoint Online, OneDrive for Business e gruppi di Office 365. Sono incluse informazioni sulla configurazione delle impostazioni di tenant, team e i canali per i progetti, schede per accedere rapidamente al messaggio App, robot informativo e connettori ai servizi di terze parti e le riunioni, messaggistica, le chiamate.
  
### <a name="skype-for-business"></a>Skype for Business

[Skype per la Guida di avvio rapido](https://aka.ms/SfBquickstartguide)
  
Introduzione veloce con Skype for Business per la messaggistica immediata, presenza, riunioni in linea e condivisione dello schermo. Se non è necessario funzioni avanzate, il programma di installazione di base è è sufficiente.
  
[Skype per consulente di distribuzione aziendale](https://aka.ms/skypeguidance)
  
Skype per consulente di distribuzione aziendale consente di ottenere rendano con Skype per Business Online. La procedura guidata viene illustrato come configurare Skype per caratteristiche di Business, ad esempio messaggistica immediata (IM), riunioni in linea, le conferenze video, servizi di conferenza public switched telephone network (PSTN), cloud privata brand exchange (PBX) e Skype riunione trasmissione. Passaggi sono inclusi per la configurazione di un ambiente ibrido di cui si connette Skype Business online le Skype locale per la distribuzione aziendale.
  
### <a name="yammer"></a>Yammer

[Introduzione a Yammer: proprio social network aziendale](https://aka.ms/yamquickstartguide)
  
In questa Guida rapida viene illustrato come distribuire correttamente Yammer all'interno dell'organizzazione. Se non si dispone di tutte le reti Yammer esistenti per consolidare o eseguire la migrazione, il programma di installazione di base è è sufficiente.
  
[Guida all'installazione di Yammer Enterprise](https://aka.ms/yammerdeploy)
  
Verificato la distribuzione di Yammer Enterprise consente di ottenere l'organizzazione attivo e in esecuzione con Yammer Enterprise. Sono incluse indicazioni su reti Yammer esistenti, che potrebbe essere la connessione a Office 365 o impostazione di un nuovo dominio Yammer. Se si dispone di più reti Yammer, viene inoltre descritto consolidare le reti di Yammer in un'unica rete Yammer Enterprise.
  
## <a name="business-apps"></a>Applicazioni aziendali

[Guida all'installazione di Microsoft StaffHub](https://aka.ms/staffhubguide)
  
Microsoft StaffHub è una piattaforma basata su cloud che può essere utilizzato in tutti i dispositivi. Consente ai lavoratori firstline (dipendenti con ruoli che non richiedono un computer) e dei responsabili per gestire le pianificazioni di MAIUSC, comunicare con i team e condivisione del contenuto.
  
## <a name="videos-for-it-pros"></a>Video per professionisti IT

### <a name="admin-center"></a>Interfaccia di amministrazione
[Orientamento di amministrazione centrale](https://www.microsoft.com/en-us/videoplayer/embed/RWfMut)

[Creare gli utenti nell'interfaccia di amministrazione](https://aka.ms/ac-createusers)

[Record DNS e l'interfaccia di amministrazione](https://aka.ms/ac-dnsrecords)

[Verifica del dominio nell'interfaccia di amministrazione](https://aka.ms/ac-verifydns)


### <a name="device-security"></a>Sicurezza dei dispositivi

[Intune](https://go.microsoft.com/fwlink/?linkid=2054124)


### <a name="mail-migration-and-protection"></a>Migrazione della posta e protezione

[Predisporre l'ambiente](https://go.microsoft.com/fwlink/?linkid=2043822)


### <a name="office-365-proplus"></a>Office 365 ProPlus

[Utilizzo di Office come un servizio di sottoscrizione](https://aka.ms/qo45jf)
  
[Panoramica di Office 365 ProPlus](https://aka.ms/r359zr)
  

### <a name="onedrive-for-business"></a>OneDrive for Business

[OneDrive for Business integrato vantaggio](https://aka.ms/f66hqa)

[Benvenuti OneDrive: provenienti da un altro provider di archiviazione cloud](https://videoplayercdn.osi.office.net/embed/6b11f30b-725a-4145-8b72-45a41793a432)


### <a name="outlook"></a>Outlook

[Outlook per l'introduzione iOS e il programma di installazione](https://aka.ms/mpuwwm)

[Outlook per Android introduzione e il programma di installazione](https://aka.ms/qrbfm3)

[Outlook per l'introduzione di Windows Phone e il programma di installazione](https://aka.ms/kkw96x)


### <a name="sharepoint"></a>SharePoint

[SharePoint: Panoramica](https://go.microsoft.com/fwlink/?linkid=2005315)

[SharePoint: ibrido](https://go.microsoft.com/fwlink/?linkid=2005219)

[SharePoint: risoluzione dei problemi](https://go.microsoft.com/fwlink/?linkid=2005220)

  
### <a name="skype-for-business"></a>Skype for Business

[Skype per l'avvio veloce potenziamento](https://aka.ms/cjfutd)

[Guida introduttiva a Skype](https://aka.ms/ofg77x)


### <a name="teams"></a>Teams

[Guida introduttiva a team](https://youtu.be/ENEQzM2u_vA)

    
## <a name="walkthroughs-for-users"></a>Procedure dettagliate per gli utenti

[App di Office per dispositivi mobili](https://aka.ms/officemobileappsetup)

[Raccolta di risorse relative alla produttività](https://aka.ms/productivitylibraryguidance)
