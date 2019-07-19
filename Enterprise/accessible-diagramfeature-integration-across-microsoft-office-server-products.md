---
title: Diagramma accessibile-integrazione delle funzionalità tra i prodotti di Microsoft Office Server
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: d78983fa-0951-49b8-b890-d76a44c70035
description: Questo articolo è una versione di testo accessibile del diagramma denominato Feature Integration tra i prodotti Microsoft Office Server-SharePoint Server, Exchange Server, Lync Server e Office Online Server.
ms.openlocfilehash: bbc50c397b85f355cc54103902a3b56258e915ea
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782246"
---
# <a name="accessible-diagram---feature-integration-across-microsoft-office-server-products"></a>Diagramma accessibile-integrazione delle funzionalità tra i prodotti di Microsoft Office Server

**Riepilogo:** Questo articolo è una versione di testo accessibile del diagramma denominato Feature Integration tra i prodotti Microsoft Office Server-SharePoint Server, Exchange Server, Lync Server e Office Online Server.
  
Il diagramma è costituito da diverse schede, come indicato dai titoli di sezione di questo documento.
  
## <a name="introduction-tab"></a>Scheda Introduzione

### <a name="illustrations-for-cross-server-features"></a>Illustrazioni per le funzionalità tra server

Questo file di Visio (o file PDF MultiPage) contiene nove schede, ognuna delle quali contiene informazioni e un diagramma su una funzionalità che è compatibile con i prodotti di Office Server.
  
Le caratteristiche e le schede sono: 
  
- Introduzione
    
- Autenticazione da server a server 
    
- Foto degli utenti ad alta risoluzione 
    
- Archivio contatti unificato 
    
- Cassette postali del sito 
    
- Sincronizzazione delle attività di Exchange 
    
- Presenza di Lync in Outlook Web App 
    
- Segreteria telefonica
    
- Registrazioni di riunioni 
    
Inviare commenti e suggerimenti su questa soluzione o richieste per soluzioni aggiuntive a MODAContent@microsoft.com. 
  
### <a name="tips-for-printing"></a>Suggerimenti per la stampa

Le dimensioni della pagina di ogni scheda sono 22 x 17 pollici (circa un quarto delle dimensioni di un diagramma ANSI Engineering). Questa pagina può essere stampata su due fogli di dimensioni di un formato tabloid (17 x 11 cm) o su quattro fogli di dimensioni lettera (11 x 8,5 pollici). Se si dispone di un plotter, è possibile stampare tali poster a grandezza intera. Se non si dispone di un plotter, eseguire la procedura seguente per stampare su carta di dimensioni più piccole. 
  
 **Stampare poster su carta di dimensioni più piccole**
  
1. Aprire il poster in Visio. 
    
2. Scegliere **Imposta pagina** dal menu **File**. 
    
3. Nella sezione **Formato carta stampante** della scheda **Imposta stampante** selezionare il formato carta su cui stampare.
    
4. Nella sezione **Proporzioni** della scheda **Imposta stampante** fare clic su **Adatta a** e quindi specificare **1 pagine di larghezza per 1 di altezza**. 
    
5. Nella scheda **Dimensioni** fare clic su **Adatta a contenuto del disegno** e quindi su **OK**. 
    
6. Scegliere **Apri** dal menu **File**. 
    
### <a name="microsoft-tags-and-qr-codes"></a>Tag Microsoft e codici QR

Utilizzare Windows Phone o scaricare un lettore di codici QR per ottenere ulteriori informazioni sull'implementazione di queste funzionalità. 
  
### <a name="cross-server-features"></a>Funzionalità tra server

In una tabella sono riportate le caratteristiche e i prodotti di Office Server che li utilizzano. Le caratteristiche sono: 
  
Autenticazione da server a server. Questa funzionalità è applicabile a: 
  
- SharePoint 
    
- Exchange
    
- Lync
    
- Office Online Server (in precedenza noto come Office Web Apps) 
    
Foto degli utenti ad alta risoluzione. Questa funzionalità è applicabile a: 
  
- SharePoint
    
- Exchange
    
- Lync
    
Archivio contatti unificato. Questa funzionalità è applicabile a: 
  
- Exchange
    
- Lync
    
Cassette postali del sito. Questa funzionalità è applicabile a: 
  
- SharePoint
    
- Exchange
    
Sincronizzazione delle attività di Exchange. Questa funzionalità è applicabile a: 
  
- SharePoint
    
- Exchange
    
Presenza di Lync in Outlook Web App. Questa funzionalità è applicabile a: 
  
- Lync
    
Voicemail. Questa funzionalità è applicabile a: 
  
- Lync
    
Registrazioni di riunioni. Questa funzionalità è applicabile a: 
  
- SharePoint
    
- Lync
    
### <a name="office-web-apps-server"></a>server Office Web Apps

Il server Office Web Apps è un prodotto server di Office che offre servizi di visualizzazione e modifica dei file basati su browser per i file di Office. Il server Office Web Apps funziona con prodotti e servizi che supportano l'applicazione Web WOPI (Open Platform Interface Protocol). Questi prodotti, noti come host, includono SharePoint 2013, Lync Server 2013 e Exchange Server 2013. 
  
Per ulteriori informazioni sul server Office Web Apps, scaricare il poster semplificato per la distribuzione di http://aka.ms/OfficeWebAppsPosterOffice Web Apps all'indirizzo. 
  
## <a name="server-to-server-authentication-tab"></a>Scheda autenticazione da server a server

### <a name="servicing-resource-requests-between-servers"></a>Manutenzione delle richieste di risorse tra server

L'autenticazione da server a server è una nuova funzionalità di Exchange Server 2013, Lync Server 2013 e SharePoint Server 2013 che consente a un server di richiedere risorse di un altro server per conto di un utente. Questa caratteristica utilizza il protocollo OAuth (Industry Standard Open Authorization) 2,0. L'autenticazione da server a server consente di effettuare molti nuovi scenari, ad esempio eDiscovery, foto utente ad alta risoluzione e cassette postali del sito. 
  
 **Prodotti server**
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
- Lync Server 2013 
    
### <a name="server-to-server-trust-relationships"></a>Relazioni di trust da server a server

Affinché un server disponga di una richiesta di risorse in arrivo, deve considerare attendibile il server che effettua la richiesta. Per stabilire questa relazione di trust, è necessario configurare le relazioni di trust tra server. 
  
Una relazione di trust da server a server è unidirezionale. Quando si configura un server che esegue SharePoint 2013 in modo che consideri attendibile un server Exchange 2013, il server che esegue SharePoint Server considera attendibili le richieste di risorse dal server Exchange, ma il server di Exchange non considera attendibili le richieste di risorse dal server in esecuzione SharePoint Server. Per una perfetta integrazione, è necessario stabilire trust bidirezionali. 
  
Nel diagramma di accompagnamento vengono riportate le relazioni di trust da server a server stabilite come trust bidirezionali. Le relazioni di trust bidirezionali visualizzate sono tra un server di Exchange, un server di SharePoint e un server Lync. Ogni tipo di server dispone di una relazione di trust bidirezionale con ciascuno degli altri due server. 
  
### <a name="configuration"></a>Configurazione

Per configurare l'attendibilità dell'autenticazione da server a server, è necessario aggiungere una nuova autorità emittente di token di sicurezza attendibile corrispondente a ogni server che invia le richieste di risorse per conto di utenti. Ogni tipo di server dispone di un endpoint di metadati JSON (JavaScript Object Notation) che contiene informazioni di configurazione e una parte pubblica del certificato di firma del token di accesso. Parte della configurazione di un trust di autenticazione da server a server specifica l'endpoint dei metadati JSON dell'altro server. 
  
Nella tabella seguente sono elencati gli endpoint dei metadati JSON per ogni server. Nella tabella sono riportati i seguenti: 
  
- Un server di Exchange con un endpoint dei metadati JSON<server name>di https:///autodiscover/Metadata/JSON/1 
    
- Un server Lync con un endpoint dei metadati JSON di<server name>https:///Metadata/JSON/1 
    
- Un server di SharePoint con un endpoint dei metadati JSON<web app name>di https:///_layouts/15/Metadata/JSON/1 
    
### <a name="example-how-server-to-server-authentication-works-for-ediscovery-between-sharepoint-and-exchange"></a>Esempio: modalità di funzionamento dell'autenticazione da server a server per eDiscovery tra SharePoint ed Exchange

In questo esempio, il server Exchange 2013 è stato configurato in modo da considerare attendibile il server che esegue SharePoint Server con una relazione di trust da server a server. Un centro eDiscovery nel server che esegue SharePoint Server è stato configurato in modo da includere i dati nelle cassette postali sul server Exchange. 
  
Le richieste di risorse in un altro server assumono il formato dei token di accesso inviati al servizio server Web nel server di destinazione. 
  
Nel diagramma seguente viene illustrato il modo in cui le query e i token di accesso passano tra i due server. 
  
1. Un amministratore di eDiscovery invia una query al server che esegue SharePoint Server che include risorse in un server di Exchange. 
    
2. Il server che esegue SharePoint Server genera un token di accesso, identificando l'utente e la risorsa richiesta. 
    
3. Il server che esegue SharePoint Server invia il token di accesso al server di Exchange. 
    
4. Il server di Exchange convalida il token di accesso e invia i risultati della query. 
    
5. Il server che esegue SharePoint Server invia i risultati della query eDiscovery al computer dell'amministratore di eDiscovery. 
    
## <a name="high-resolution-user-photos-tab"></a>Scheda foto utente ad alta risoluzione

### <a name="larger-profile-picture-used-across-all-office-applications"></a>Immagine del profilo più grande utilizzata in tutte le applicazioni di Office

Utilizzando la scheda **foto utente ad alta risoluzione** , è possibile archiviare le foto fino a 648 x 648 pixel in Exchange 2013. È quindi possibile accedere alle applicazioni client, tra cui Outlook, Outlook Web App, SharePoint 2013, Lync 2013 e client di posta elettronica per dispositivi mobili. Una foto a bassa risoluzione viene anche conservata in Active Directory.
  
 **Prodotti server**
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
- Lync Server 2013 
    
### <a name="configuration"></a>Configurazione

Configurazione dell'autenticazione da server a server: 
  
- Tra Exchange 2013 e SharePoint 2013. 
    
- Tra Exchange 2013 e Lync 2013. 
    
 **In Exchange Server 2013**
  
- Avviare e configurare il servizio di individuazione automatica di Exchange 2013. 
    
- Impostare gli URL esterni per SharePoint. Questo è l'URL utilizzato da SharePoint quando accede alle foto in Exchange. 
    
 **In SharePoint Server 2013**
  
- Installare l'API gestita di servizi Web Exchange. Utilizzare GacUtil per caricare Microsoft. Exchange. WebServices. dll nella global assembly cache (GAC). 
    
- Utilizzare Windows PowerShell per configurare la sincronizzazione delle foto con Exchange. 
    
 **Come funziona**
  
- Gli utenti caricano una foto utilizzando la pagina account personale in Outlook Web App (OWA) o le impostazioni dell'account in Outlook 2013. 
    
- Exchange consente di ridimensionare automaticamente l'immagine per l'utilizzo da servizi di dominio Active Directory (48 x 48 pixel) o da altre applicazioni di Office, tra cui OWA e il client Outlook 2013 (96 x 96 pixel). 
    
Gli utenti possono caricare immagini con intervalli di pixel compresi tra 48 × 48 e 648 × 648. Le foto vengono ridimensionate: 
  
- 64 × 64 viene utilizzato per l'anteprima di Active Directory. 
    
- 96 × 96 viene utilizzato per Outlook Web Access, Outlook, Lync Web Access e Lync 2013. 
    
- 648 × 648 viene utilizzato per Lync Web Access e Lync 2013. 
    
Ad esempio, gli script di configurazione, vedere gli articoli del Blog di Jens Trier Rasmussen: 
  
- Utilizzo di foto ad alta risoluzione di Exchange 2013 da SharePoint Server 2013 (http://aka.ms/Bhr4d2) 
    
- Integrazione di Exchange 2013 e Lync Server 2013 (http://aka.ms/Pn08dw) 
    
Il poster contiene anche codici QR per questi due articoli del Blog. 
  
Nel diagramma seguente viene illustrato il modo in cui un utente può aggiornare una foto da utilizzare in tutte le applicazioni di Office. 
  
1. Foto degli aggiornamenti degli utenti in Outlook, SharePoint o Lync. Dopo l'aggiornamento, la foto aggiornata viene utilizzata in tutte le applicazioni di Office. 
    
2. L'utente può utilizzare diversi modi per aggiornare una foto: 
    
3. 
  - Client Outlook o Outlook Web App (OWA) tramite la porta HTTP 443 a un server Accesso client di Exchange. 
    
  - My Site over HTTP or HTTPS to a SharePoint Server. SharePoint memorizza nella cache l'utente nel database di siti personali (https: 443). Il server di SharePoint si interfaccia con il server Accesso client di Exchange utilizzando gli URL esterni impostati in Exchange. 
    
  - Client Lync 2013, che mantiene una GetConnection con il server di Exchange per ottenere gli aggiornamenti delle foto (richiesta HTTPS Get-443). 
    
4. Il server Accesso client di Exchange si connette al server cassette postali di Exchange utilizzando la comunicazione interna di Exchange. 
    
5. Il server cassette postali di Exchange utilizza Exchange 2013 per spingere la foto utente ad alta risoluzione su servizi di dominio Active Directory (LDAP: 389). 
    
6. La foto viene sincronizzata da servizi di dominio Active Directory (AD DS) al servizio Rubrica Lync (ABS) del server Lync in modo che i client legacy possano ottenere la stessa foto (LDAP: 389). 
    
7. Il client Lync Legacy ha ora accesso alla foto. 
    
## <a name="unified-contact-store-tab"></a>Scheda archivio contatti unificato

### <a name="exchange-2013-is-the-contact-store-for-all-office-applications"></a>Exchange 2013 è l'archivio contatti per tutte le applicazioni di Office

L'archivio contatti unificato (UCS) fornisce un'esperienza di contatto coerente tra i prodotti Microsoft Office. Gli utenti archiviano tutte le informazioni di contatto nella loro cassetta postale di Exchange 2013. Le stesse informazioni di contatto sono disponibili a livello globale in Lync, Exchange, Outlook e Outlook Web App. 
  
 **Prodotti server**
  
- Exchange Server 2013 
    
- Lync Server 2013 
    
 **Configurazione**
  
- Configurare l'autenticazione da server a server tra Exchange Server 2013 e Lync Server 2013. 
    
- In Lync 2013, abilitare il criterio dell'archivio contatti unificato (il valore predefinito è abilitato). 
    
Ad esempio, gli script di configurazione, vedere l'articolo del Blog di Jens Trier Rasmussen: 
  
- Integrazione di Exchange 2013 e Lync Server 2013 (http://aka.ms/Oyg7fh) 
    
 **Come funziona**
  
- I contatti di Lync per un utente vengono migrati automaticamente a Exchange 2013 quando l'utente esegue l'accesso con Lync 2013. 
    
- Gli utenti possono accedere e gestire i propri contatti di Lync da Lync 2013, Outlook 2013 o Outlook Web Access. 
    
I contatti di un utente vengono migrati automaticamente al server Exchange 2013 quando l'utente: 
  
1. È stato assegnato un criterio dei servizi utente che dispone di UcsAllowed impostato impostato su **true**. 
    
2. È stato effettuato il provisioning con una cassetta postale di Exchange 2013 e ha eseguito l'accesso almeno una volta alla cassetta postale. 
    
3. Consente di eseguire l'accesso a Lync utilizzando un rich client Lync 2013. 
    
Consente di eseguire l'accesso a Lync utilizzando un rich client Lync 2013. 
  
1. Accede alla propria cassetta postale di Exchange 2013 sul server Accesso client di Exchange, utilizzando un client di Outlook o Outlook Web App (OWA) su HTTPS/443. Il server cassette postali di Exchange utilizza una comunicazione interna di Exchange per comunicare con il server Accesso client di Exchange. 
    
2. Consente di eseguire l'accesso a Lync 2013. Il client Lync Contatta il server Lync su SIP/5061 HTTPS/443. 
    
3. Il client Lync indica al server Lync che l'utente è abilitato per l'archivio contatti unificato su SIP/5061. 
    
4. Lync Server utilizza il servizio di archiviazione di Lync per eseguire la migrazione dei contatti dell'utente a Exchange 2013 sul server Accesso client di Exchange. 
    
5. L'utente deve disconnettersi e accedere a Lync 2013 affinché le modifiche vengano visualizzate (non mostrate nel diagramma). 
    
6. Dopo la migrazione, il client Lync utilizza servizi Web Exchange (EWS) per leggere e gestire i contatti di Lync. 
    
## <a name="site-mailboxes-tab"></a>Scheda cassette postali del sito

### <a name="a-central-filing-cabinet-for-emails-and-documents"></a>Archivio centrale di archiviazione per messaggi di posta elettronica e documenti

Le cassette postali del sito migliorano la collaborazione e la produttività degli utenti consentendo l'accesso ai documenti archiviati in SharePoint e i messaggi di posta elettronica archiviati in Exchange utilizzando la stessa interfaccia client. 
  
 **Prodotti server**
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
 **Configurazione**
  
Configurazione di SharePoint: 
  
- Configurare la sincronizzazione dei profili utente nella farm di SharePoint. 
    
- Configurare l'applicazione del servizio di gestione delle app nella farm di SharePoint. 
    
- Configurare SSL per l'area predefinita per il supporto dell'autenticazione da server a server. 
    
- Installare l'API EWS nei server che eseguono SharePoint 2013. 
    
- Stabilire la relazione di trust OAuth e le autorizzazioni del servizio nei server che eseguono SharePoint 2013. 
    
Configurazione di Exchange: 
  
- Stabilire la relazione di trust OAuth e le autorizzazioni del servizio nei server Exchange. 
    
- Creare il criterio di provisioning delle cassette postali del sito. 
    
- Configurare il prefisso del nome della cassetta postale del sito (facoltativo). 
    
 **Come funziona**
  
Una cassetta postale del sito è composta dall'appartenenza al sito di SharePoint 2013 (proprietari e membri), da un archivio condiviso tramite una cassetta postale di Exchange 2013 per i messaggi di posta elettronica e un sito di SharePoint 2013 per i documenti e da un'interfaccia di gestione per i requisiti di provisioning e ciclo di vita. 
  
Il diagramma di accompagnamento Visualizza gli utenti che utilizzano le cassette postali del sito per accedere ai messaggi di posta elettronica in Outlook e documenti archiviati in SharePoint. 
  
1. Gli utenti possono accedere ai documenti del sito del team di SharePoint tramite le cassette postali del sito in Outlook 2013 Pro Plus. 
    
2. Gli utenti possono anche leggere messaggi di posta elettronica nella cassetta postale del sito del team di SharePoint. 
    
3. I messaggi di posta elettronica vengono archiviati nelle cassette postali dei server Exchange. 
    
4. I documenti vengono archiviati nelle cassette postali del sito nei server di SharePoint. 
    
5. I metadati del contenuto del sito di SharePoint vengono sincronizzati con Exchange utilizzando l'API REST (rappresentation State Transfer) su HTTPS. 
    
### <a name="provisioning-and-management"></a>Provisioning e gestione

Le cassette postali del sito sono provisioning e gestite tramite SharePoint 2013. Sono disponibili funzionalità di SharePoint e di Exchange per il provisioning e la gestione. 
  
#### <a name="sharepoint"></a>SharePoint

Un diagramma illustra i componenti di SharePoint necessari per eseguire il provisioning della cassetta postale del sito, tra cui: 
  
- App della cassetta postale del sito 
    
- Membri e proprietari del sito del team 
    
- Criteri del ciclo di vita del sito del team 
    
Per eseguire il provisioning di una nuova cassetta postale del sito, installare l'app cassetta postale del sito nel sito del team e accedere all'app almeno una volta. 
  
L'appartenenza al sito di SharePoint determina chi ha accesso alla cassetta postale del sito. 
  
La conservazione della cassetta postale del sito segue gli stessi criteri del ciclo di vita configurati per il sito di SharePoint a cui è associato. 
  
#### <a name="exchange"></a>Exchange

Nel diagramma viene illustrato il criterio di provisioning delle cassette postali del sito. Si tratta del componente di Exchange necessario per eseguire il provisioning della cassetta postale del sito.
  
Sul server Exchange, è possibile definire i criteri di provisioning delle cassette postali del sito. Questi criteri regolano le caratteristiche di posta elettronica inviate e ricevute dalla cassetta postale del sito, le dimensioni della cassetta postale del sito sul server Exchange e consentono di definire un prefisso per gli indirizzi di posta elettronica delle cassette postali del sito. 
  
Per le distribuzioni di Exchange locali, è inoltre necessario cercare ed eliminare periodicamente le cassette postali del sito contrassegnate per l'eliminazione tramite il criterio del ciclo di vita di SharePoint. 
  
## <a name="exchange-task-synchronization-tab"></a>Scheda sincronizzazione attività di Exchange

### <a name="synchronizing-tasks-among-sharepoint-server-2013-project-server-2013-and-exchange-server-2013"></a>Sincronizzazione delle attività tra SharePoint Server 2013, Project Server 2013 ed Exchange Server 2013

Se si utilizza la sincronizzazione delle attività di Exchange, è possibile sincronizzare le attività in SharePoint Server 2013 e Project Server 2013 con Exchange Server 2013. Gli utenti possono visualizzare e gestire le proprie attività in Outlook 2013 o nel proprio sito personale. 
  
 **Prodotti server**
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
- Project Server 2013 (facoltativo) 
    
 **Prerequisiti**
  
In Exchange 2013: 
  
- Configurare la relazione di trust OAuth e l'autorizzazione del servizio. 
    
In SharePoint Server 2013: 
  
- Applicazione del servizio profili utente. 
    
- Applicazione del servizio di gestione del lavoro. 
    
- Search (necessario per le attività in SharePoint Server 2013). Configurare le ricerche per indicizzazione continue e le ricerche per indicizzazione incrementali. 
    
- Secure Sockets Layer (SSL) è obbligatorio. 
    
- Gli utenti dispongono di siti personali esistenti. 
    
- Applicazione di servizio di Project (per aggregare le attività di Project Server). 
    
- API di servizi Web Exchange in ogni server Web front-end (è un file. exe separato da scaricare che deve essere installato). 
    
In Project Server 2013: 
  
- Creare siti di applicazioni Web di Project. 
    
 **Come funziona**
  
Quando la visualizzazione attività personali nei siti personali viene aperta o aggiornata: 
  
- L'applicazione del servizio di gestione del lavoro esegue la sincronizzazione tra SharePoint Server e Project Server. 
    
- Il processo timer di sincronizzazione di Exchange chiama l'applicazione del servizio di gestione del lavoro per sincronizzare le attività con Exchange Server 2013. 
    
- La pagina attività personali dei siti personali viene aggiornata. 
    
Quando viene eseguito il processo timer di sincronizzazione di Exchange: 
  
- L'applicazione del servizio di gestione del lavoro è sincronizzata tra SharePoint Server, Project Server e Exchange Server. 
    
Nel diagramma seguente viene illustrata l'interazione tra SharePoint Server 2013, Exchange Server 2013, Outlook 2013 e Project Server 2013. 
  
SharePoint Server 2013 esegue i processi e le applicazioni seguenti: 
  
- Applicazione del servizio profili utente. 
    
- Applicazione del servizio di ricerca. 
    
- Applicazione del servizio di gestione del lavoro, descritta di seguito. 
    
- Processo timer di sincronizzazione di Exchange, descritta di seguito. 
    
- SharePoint Server 2013 contiene il sito personale e gli altri siti dell'utente ed esegue numerose attività utente. 
    
- SharePoint Server 2013 contiene un indice di ricerca. 
    
Exchange Server 2013 contiene gli elementi seguenti: 
  
- Database di Exchange con informazioni sulla posta elettronica degli utenti 
    
- Attività di sincronizzazione 
    
In Outlook 2013 sono riportati gli elementi seguenti: 
  
- Gli utenti possono scegliere di sincronizzare le attività descritte di seguito. 
    
- Gli utenti possono visualizzare e modificare le attività in Outlook. 
    
In Project Server 2013 sono riportati gli elementi seguenti: 
  
- Database di Project 
    
- Siti di Project Web Access con attività 
    
Applicazione del servizio di gestione del lavoro: 
  
- Aggrega le attività degli elenchi di SharePoint e degli elenchi di attività di progetto (non sincronizza le attività con Exchange Server). 
    
- Sincronizza quando gli utenti visualizzano il proprio sito personale. 
    
- Gestisce l'elenco degli utenti che scelgono l'opt-in. 
    
- Sincronizza il prossimo batch di utenti. 
    
Processo timer di sincronizzazione di Exchange: 
  
- Determina il prossimo batch di utenti. 
    
- Garantisce che tutti gli utenti siano costantemente sincronizzati. 
    
- Avvia la chiamata all'applicazione del servizio di gestione del lavoro per sincronizzare le attività con Exchange Server per gli utenti che sono solo opt-in. 
    
Opt-in 
  
- Gli utenti devono scegliere di eseguire la sincronizzazione delle attività di Exchange con il proprio sito personale o con le attività di SharePoint Server 2013 e Project Server 2013 con Exchange Server 2013. 
    
## <a name="lync-presence-in-office-2013-outlook-web-app-and-sharepoint-server-tab"></a>Presenza di Lync in Office 2013, Outlook Web App e scheda di SharePoint Server

### <a name="lync-server-as-the-authoritative-source-of-presence-information"></a>Lync Server come origine autorevole delle informazioni sulla presenza

Utilizzando le informazioni sulla presenza di Lync, è possibile disporre di una visualizzazione coerente delle informazioni sulla presenza tra Lync, Outlook e SharePoint. Outlook esegue una query sulle informazioni sulla presenza direttamente da Lync, che è installato localmente nello stesso computer di Outlook. Quando gli utenti visualizzano le informazioni sulla presenza in SharePoint Server, le informazioni sulla presenza vengono interrogate da Lync sul computer locale.
  
Prodotti client: 
  
- Outlook 2013 
    
- Lync 2013 
    
Prodotti server: 
  
- Exchange Server 2013 
    
- Lync Server 2013 
    
- SharePoint Server 2013 
    
 **Come funziona**
  
Fintanto che Lync 2013 è installato nel computer locale dell'utente, Outlook e SharePoint Server visualizzano automaticamente le informazioni sulla presenza degli utenti. 
  
Per gli utenti di Outlook Web App, Exchange CAS interroga la presenza per conto dell'utente. 
  
 **Sono disponibili due diagrammi di accompagnamento**
  
Il primo indica come un utente accede a Outlook Web App e quindi esegue una query su Lync Server per visualizzare le informazioni sulla presenza. 
  
1. L'utente accede a Outlook Web App. Il computer client accede al server Accesso client (CAS) di Exchange su HTTPS/443 e chiama anche il server cassette postali di Exchange con una comunicazione interna di Exchange. 
    
2. L'utente accede alla propria cassetta postale di Exchange 2013 e Exchange CAS esegue una query sul server Lync per le informazioni sulla presenza su SIP/MTLS: 5061. 
    
Per ulteriori informazioni, vedere [integrazione di Microsoft Lync Server 2013 e Microsoft Outlook Web App 2013](https://go.microsoft.com/fwlink/?LinkId=313522).
  
Nel secondo diagramma viene illustrato il modo in cui Outlook e SharePoint Server utilizzano Lync 2013 per visualizzare le informazioni sulla presenza degli utenti. 
  
1. L'utente accede a Lync 2013 su SIP/TLS: 5061, che chiama il server Lync. 
    
2. R. L'utente accede alla propria cassetta postale di Exchange 2013 tramite Outlook in Office 2013. Il computer client accede al server Accesso client (CAS) di Exchange su HTTPS/443 e chiama anche il server cassette postali di Exchange con una comunicazione interna di Exchange. 
    
3. R. Outlook chiama Lync installato nello stesso computer di Outlook per recuperare le informazioni sulla presenza. 
    
4. B. L'utente si connette a un sito Web di SharePoint tramite HTTP o HTTPS, che chiama il server di SharePoint. 
    
5. B. Internet Explorer chiama Lync, che è installato nello stesso computer del browser, per recuperare le informazioni sulla presenza. 
    
## <a name="voicemail-tab"></a>Scheda segreteria telefonica

### <a name="exchange-um-is-the-voicemail-system-for-lync-server"></a>La messaggistica unificata di Exchange è il sistema di segreteria telefonica per Lync Server

La segreteria telefonica consente a un chiamante di lasciare una segreteria telefonica agli utenti di Lync utilizzando la messaggistica unificata di Exchange. 
  
Prodotti client: 
  
- Lync 2013 
    
- Dispositivo PSTN (PBX, Cellular, POTS) 
    
Prodotti server: 
  
- Exchange Server 2013 
    
- Exchange Server 2013 
    
 **Come funziona**
  
Quando una chiamata non riceve una risposta dal destinatario della chiamata su uno degli endpoint attivi del destinatario della chiamata, Lync Server instrada la chiamata alla segreteria telefonica della messaggistica unificata di Exchange (ad esempio, il server cassette postali di Exchange). 
  
Nel diagramma di accompagnamento viene illustrato il routing delle chiamate per due scenari: 
  
- Il chiamante avvia una chiamata utilizzando Lync 2013. 
    
- Il chiamante avvia una chiamata utilizzando un dispositivo PSTN (PBX, Cellular, POTS). 
    
Il chiamante avvia una chiamata utilizzando Lync 2013: 
  
1. Il chiamante A avvia una chiamata al destinatario della chiamata utilizzando Lync 2013. La chiamata viene avviata e inviata al server Lync. 
    
2. La chiamata viene instradata al Lync Home Server del destinatario della chiamata. 
    
3. Lync Server squilla gli endpoint attivi del destinatario su Lync 2013. 
    
4. Quando la chiamata non è stata risolta, la chiamata viene instradata alla segreteria telefonica (messaggistica unificata di Exchange) sul CAS di Exchange (router di chiamata). 
    
Il chiamante avvia una chiamata utilizzando Lync 2013: 
  
1. Il chiamante B compone il numero di telefono del destinatario della chiamata tramite PSTN. 
    
2. La chiamata PSTN viene instradata dal gateway IP al Mediation Server, che è un server Lync. 
    
3. Il Mediation Server instrada la chiamata al Lync Home Server del destinatario della chiamata. 
    
4. Lync Server squilla gli endpoint attivi del destinatario su Lync 2013. 
    
5. Quando la chiamata non è stata risolta, la chiamata viene instradata alla segreteria telefonica (messaggistica unificata di Exchange) sul CAS di Exchange (router di chiamata). 
    
## <a name="meeting-recordings-tab"></a>Scheda registrazioni riunioni

### <a name="publish-your-meeting-recordings-on-your-sharepoint-team-site"></a>Pubblicare le registrazioni delle riunioni nel sito del team di SharePoint

Le registrazioni delle riunioni sono un componente di base delle comunicazioni unificate. Un buon modo per condividere le registrazioni delle riunioni consiste nell'utilizzare le raccolte di risorse di SharePoint nei siti del team per archiviare le registrazioni delle riunioni. 
  
Prodotti client: 
  
- Lync 2013 
    
Prodotti server: 
  
- Prodotti server: 
    
- SharePoint 2013 
    
Prerequisiti 
  
- Lync 2013: la registrazione delle riunioni è una funzionalità sul fianco client in Lync 2013. 
    
- SharePoint 2013: si dispone del sito del team in cui si desidera archiviare le registrazioni delle riunioni già in esecuzione. 
    
 **Cosa viene registrato?**
  
Le seguenti sono registrate in un file MP4 durante la riunione (ogni punto elenco è preceduto da un'icona che rappresenta il tipo di registrazione): 
  
- Tutti gli audio 
    
- Video di un altoparlante attivo (se utilizzato) 
    
- Video panoramico (se utilizzato) 
    
- Tutto il contenuto presentato 
    
- Messaggi istantanei * 
    
* Sono inclusi solo i messaggi istantanei all'interno della riunione. Qualsiasi messaggistica peer-to-peer tra partecipanti alla riunione non fa parte della riunione e pertanto non viene acquisita. 
  
Nel poster sono disponibili due diagrammi per due diversi scenari: 
  
- Preparazione per la pubblicazione di registrazioni di riunioni 
    
- Registrazione e pubblicazione di una riunione tramite il client Lync 
    
### <a name="preparing-for-publishing-meeting-recordings"></a>Preparazione per la pubblicazione di registrazioni di riunioni

Nel diagramma viene mostrato SharePoint Server 2013 con un sito del team, un centro di amministrazione centrale e un server Internet Information Services (IIS). 
  
Il sito del team contiene: 
  
- App della raccolta di risorse. 
    
- Raccolta di risorse per riunioni, a cui i membri del team inviano le registrazioni delle riunioni. 
    
L'interfaccia di amministrazione centrale contiene le impostazioni generali dell'applicazione Web. 
  
Il server IIS contiene le impostazioni di IIS. 
  
Per preparare le registrazioni delle riunioni di pubblicazione: 
  
1. Nel sito del team di SharePoint, aggiungere l'app della raccolta di risorse. Facoltativamente, se non è possibile caricare le registrazioni delle riunioni a causa di restrizioni di dimensione o timeout di connessione, eseguire i passaggi aggiuntivi 2 e 3. 
    
2. In Amministrazione centrale SharePoint modificare l'impostazione dimensioni massime caricamento per l'applicazione Web in cui è contenuta la raccolta siti del team. 
    
3. Nelle impostazioni del server IIS, aumentare il timeout di connessione IIS per il sito Web che contiene la raccolta siti del team. 
    
 **Raccolte di risorse digitali**
  
Le raccolte di risorse digitali sono raccolte di risorse che contengono video con determinate caratteristiche di capacità e prestazioni. Per ulteriori informazioni, vedere Plan Digital Asset Libraries in SharePoint Server 2013 located http://aka.ms/O1vq5wat. Nel poster è incluso anche un codice QR che consente di accedere a queste informazioni. 
  
### <a name="recording-and-publishing-a-meeting-using-the-lync-client"></a>Registrazione e pubblicazione di una riunione tramite il client Lync

Nel diagramma viene mostrato un utente che utilizza Lync per partecipare a una riunione. La riunione viene registrata utilizzando il client Lync, che crea un file MP4 con il contenuto della riunione. La registrazione MP4 viene salvata nella cartella di registrazione di Lync nel computer in uso. È possibile spostare la registrazione MP4 nella raccolta di risorse per le riunioni, dalla quale è possibile inserirla in un wiki, in una pagina di SharePoint o in un blog. 
  
 **Per registrare e pubblicare una riunione utilizzando il client Lync**
  
1. Avviare la registrazione della riunione utilizzando il client Lync. 
    
2. Il contenuto della riunione viene registrato in un file MP4 durante la riunione. 
    
3. Dopo la conclusione della riunione, la registrazione MP4 viene visualizzata nella cartella di registrazione nel computer in uso (\\C\\<username>\\:\\utenti video di Lync Recordings). Facoltativamente, è possibile personalizzare la registrazione delle riunioni utilizzando l'app Lync Recording Manager che viene installata con il client Lync. 
    
4. Trascinare e rilasciare la registrazione riunione nella raccolta di risorse di SharePoint. 
    
5. Facoltativo: una volta che la registrazione è presente nella raccolta di risorse, è possibile inserirla in una pagina di SharePoint. Per ulteriori informazioni su questo passaggio, vedere l'articolo relativo al Blog di Office 365, creare e pubblicare video per la formazione con SharePoint e http://aka.ms/R61q35Lync Online, in cui si trova. 
    
 **Miniature video**
  
Le miniature video migliorano l'aspetto della raccolta di risorse. Per ulteriori informazioni sulla creazione di anteprime per le registrazioni delle riunioni, vedere acquisizione o modifica di una miniatura http://aka.ms/Kupj85video, in cui si trova. Nel poster è incluso anche un codice QR che consente di accedere a queste informazioni. 
  

