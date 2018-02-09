---
title: "Diagramma accessibile - funzionalità di integrazione tra prodotti Microsoft Office Server"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: d78983fa-0951-49b8-b890-d76a44c70035
description: "In questo articolo è una versione testo accessibile del diagramma denominato funzionalità di integrazione tra Office prodotti Server Microsoft - Server di SharePoint, Exchange Server, Lync Server e Office Online."
ms.openlocfilehash: 809a9272d7088ac069aad6b64daedfe059188247
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---feature-integration-across-microsoft-office-server-products"></a>Diagramma accessibile - funzionalità di integrazione tra prodotti Microsoft Office Server

**Riepilogo:** In questo articolo è una versione testo accessibile del diagramma denominato funzionalità di integrazione tra Office prodotti Server Microsoft - Server di SharePoint, Exchange Server, Lync Server e Office Online.
  
Nel diagramma include diverse schede, come indicato dei titoli delle sezioni del documento.
  
## <a name="introduction-tab"></a>Scheda introduzione

### <a name="illustrations-for-cross-server-features"></a>Nelle figure per le funzionalità tra server

In questo file di Visio (o più pagine file PDF) ha nove schede, ognuno con informazioni e un diagramma sulla caratteristica che funzioni correttamente sui prodotti Server di Office.
  
Le caratteristiche e le schede sono: 
  
- Introduzione
    
- Autenticazione tra server 
    
- Foto dell'utente ad alta risoluzione 
    
- Archivio unico dei contatti 
    
- Cassette postali del sito 
    
- Sincronizzazione delle attività di Exchange 
    
- Presenza di Lync in Outlook Web App 
    
- Segreteria telefonica
    
- Registrazioni delle riunioni 
    
Invia commenti su questo soluzione o richieste per le soluzioni aggiuntive a MODAContent@microsoft.com. 
  
### <a name="tips-for-printing"></a>Suggerimenti per la stampa

Le dimensioni della pagina di ogni scheda sono 22 x 17 pollici (su un quarto della dimensione di un diagramma ANSI ingegneristiche). In questa pagina è possibile stampare su due pollici fogli dimensioni tabloid (11 x 17)) o quattro fogli formato lettera (11 x 8,5 pollici). Se si dispone di un plotter, è possibile stampare questi poster nelle dimensioni massime. Se non disponi di plotter, utilizzare la procedura seguente per stampare su carta di dimensioni ridotte. 
  
 **Stampare poster su carta di dimensioni ridotte**
  
1. Aprire il poster in Visio. 
    
2. Scegliere **Imposta pagina**dal menu **File** . 
    
3. Nella scheda **Imposta stampante** selezionare il formato della carta che su cui stampare nella sezione **formato carta stampante** .
    
4. Nella sezione **proporzioni** della scheda **Imposta stampante** fare clic su **Adatta a**e quindi specificare **1 pagine di larghezza per 1 di altezza**. 
    
5. Nella scheda **Dimensioni** fare clic su **Adatta a contenuto disegno**e quindi fare clic su **OK**. 
    
6. Scegliere **Stampa**dal menu **File** . 
    
### <a name="microsoft-tags-and-qr-codes"></a>I tag di Microsoft e i codici QR

Utilizzare il telefono di Windows o scaricare un lettore codice QR per ottenere ulteriori informazioni sull'implementazione di queste funzionalità. 
  
### <a name="cross-server-features"></a>Funzionalità tra server

Una tabella mostra le funzionalità e i prodotti Server di Office che li utilizzano. Le funzionalità sono: 
  
Autenticazione da server a server. Questa caratteristica è applicabile a: 
  
- SharePoint 
    
- Exchange
    
- Lync
    
- Office Online (precedentemente noto come Office Web Apps) 
    
Foto dell'utente ad alta risoluzione. Questa caratteristica è applicabile a: 
  
- SharePoint
    
- Exchange
    
- Lync
    
Archivio contatto unificato. Questa caratteristica è applicabile a: 
  
- Exchange
    
- Lync
    
Cassette postali del sito. Questa caratteristica è applicabile a: 
  
- SharePoint
    
- Exchange
    
Sincronizzazione delle attività di Exchange. Questa caratteristica è applicabile a: 
  
- SharePoint
    
- Exchange
    
Presenza di Lync in Outlook Web App. Questa caratteristica è applicabile a: 
  
- Lync
    
Segreteria telefonica. Questa caratteristica è applicabile a: 
  
- Lync
    
Registrazioni delle riunioni. Questa caratteristica è applicabile a: 
  
- SharePoint
    
- Lync
    
### <a name="office-web-apps-server"></a>server Office Web Apps

Office Web Apps Server è un prodotto di server di Office che sono disponibili file basato su browser visualizzazione e modifica di servizi per i file di Office. Office Web Apps Server funziona con prodotti e servizi che supportano il Web Application Open piattaforma interfaccia protocollo WOPI (). Questi prodotti, noti come host, includono SharePoint 2013, Lync Server 2013 ed Exchange Server 2013. 
  
Per ulteriori informazioni su Office Web Apps Server, scaricare il poster semplificato distribuzione di Office Web Apps in http://aka.ms/OfficeWebAppsPoster. 
  
## <a name="server-to-server-authentication-tab"></a>Scheda autenticazione da server a Server

### <a name="servicing-resource-requests-between-servers"></a>Per gestire le richieste di risorse tra server

Autenticazione da server a server è una nuova funzionalità di Exchange Server 2013, Lync Server 2013 e SharePoint Server 2013 che consente a un server per richiedere le risorse di un altro server per conto di un utente. Questa funzionalità utilizza il settore standard Open Authorization (OAuth) 2.0 protocollo. Autenticazione da server a server consente a nuovi scenari, ad esempio eDiscovery, foto dell'utente ad alta risoluzione e cassette postali del sito. 
  
 **Prodotti server**
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
- Lync Server 2013 
    
### <a name="server-to-server-trust-relationships"></a>Relazioni di trust da server a server

Per un server di servizi di una richiesta di risorse in arrivo, è necessario considerare attendibile il server effettua la richiesta. Per stabilire una relazione di trust, è necessario configurare le relazioni di trust da server a server. 
  
Una relazione di trust da server a server è un modo. Quando si configura un server che esegue SharePoint 2013 affinché consideri attendibile un server Exchange 2013, il server che esegue SharePoint Server trust tra le richieste di risorse del server di Exchange, ma il server di Exchange non è considerata attendibile dal server che esegue le richieste di risorse SharePoint Server. Per una facile integrazione, è necessario stabilire relazioni di trust bidirezionale. 
  
Nella figura relativa Mostra le relazioni di trust da server a server che stabilite come trust bidirezionale. Le relazioni di trust bidirezionale riportate sono compresi tra un Server di Exchange, SharePoint Server e Lync Server. Ogni tipo di server dispone di un trust bidirezionale con ognuno dei due server. 
  
### <a name="configuration"></a>Configurazione

Per configurare una relazione di trust di autenticazione da server a server, è necessario aggiungere un nuovo emittente di token di sicurezza trusted corrispondente a ogni server che invia le richieste di risorse per conto di utenti. Ogni tipo di server dispone di un endpoint dei metadati JavaScript Object Notation (JSON) contenente le informazioni di configurazione e una parte pubblica del certificato di firma il token di accesso. Parte della configurazione di una relazione di trust di autenticazione da server a server è che specifica l'endpoint dei metadati JSON di altro server. 
  
Nella tabella seguente sono elencati l'endpoint dei metadati JSON per ogni server. Nella tabella seguente: 
  
- Un server di Exchange con un endpoint dei metadati JSON https://<server name>/autodiscover/metadata/json/1 
    
- Lync server con un endpoint dei metadati JSON https://<server name>/metadata/json/1 
    
- SharePoint server con un endpoint dei metadati JSON https://<web app name>/_layouts/15/metadata/json/1 
    
### <a name="example-how-server-to-server-authentication-works-for-ediscovery-between-sharepoint-and-exchange"></a>Esempio: Come server a server l'autenticazione funzioni eDiscovery tra Exchange e SharePoint

In questo esempio, il server Exchange 2013 è stato configurato per considerare attendibile il server che esegue SharePoint Server con una relazione di trust da server a server. Un centro eDiscovery sul server che esegue SharePoint Server è stato configurato in modo da includere dati nelle cassette postali in Exchange server. 
  
Le richieste di risorse in un altro server sotto forma di token di accesso vengono inviate al servizio server web nel server di destinazione. 
  
Nella figura relativa viene illustrato come le query e il token di accesso di viaggio tra i due server. 
  
1. Un amministratore di eDiscovery invia una query nel server che esegue SharePoint Server in cui vengono indicate le risorse in un server Exchange. 
    
2. Il server che esegue SharePoint Server genera un token di accesso, che identifica l'utente e la risorsa richiesta. 
    
3. Il server che esegue SharePoint Server invia il token di accesso al server di Exchange. 
    
4. Exchange server convalida il token di accesso e invia i risultati delle query. 
    
5. Il server che esegue SharePoint Server invia i risultati delle query eDiscovery sul computer dell'amministratore eDiscovery. 
    
## <a name="high-resolution-user-photos-tab"></a>Scheda foto dell'utente ad alta risoluzione

### <a name="larger-profile-picture-used-across-all-office-applications"></a>Immagine del profilo di dimensioni maggiori utilizzate in tutte le applicazioni di Office

Utilizzando la scheda **foto dell'utente ad alta risoluzione** , è possibile memorizzare le foto fino a 648 x 648 pixel di Exchange 2013. È quindi possibile accedervi dalle applicazioni client, inclusi Outlook, Outlook Web App, SharePoint 2013, Lync 2013 e i client di posta elettronica mobile. Una foto a bassa risoluzione inoltre viene archiviata in Active Directory.
  
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
    
- Impostare gli URL esterni di SharePoint. Si tratta utilizza SharePoint URL quando si accede mediante le foto di Exchange. 
    
 **In SharePoint Server 2013**
  
- Installare l'API gestita Exchange Web Services. Utilizzare GacUtil per caricare il Microsoft.Exchange.WebServices.dll nella Global Assembly Cache (GAC). 
    
- Utilizzare Windows PowerShell per configurare la sincronizzazione di foto con Exchange. 
    
 **Modalità di funzionamento**
  
- Gli utenti di caricare una foto utilizzando la pagina My Account in Outlook Web App (OWA) o le impostazioni degli account in Outlook 2013. 
    
- Exchange ridimensiona automaticamente l'immagine per l'utilizzo di dominio Active Directory (48 x 48 pixel) o da altre applicazioni di Office, tra cui OWA e il client di Outlook 2013 (96 x 96 pixel). 
    
Gli utenti possono caricare le immagini degli intervalli di pixel dal 48 × 48 a × 648 648. Le immagini vengono ridimensionata: 
  
- 64 x 64 viene utilizzato per l'anteprima di Active Directory. 
    
- 96 × 96 viene utilizzato per Outlook Web Access, Outlook, Lync Web Access e Lync 2013. 
    
- 648 × 648 viene utilizzato per Lync 2013 e Lync Web Access. 
    
Ad esempio gli script di configurazione, vedere articoli del blog di Jens portacampioni Rasmussen: 
  
- Utilizzo di Exchange 2013 foto ad alta risoluzione da SharePoint Server 2013 (http://aka.ms/Bhr4d2) 
    
- Integrazione di Exchange 2013 e Lync Server 2013 (http://aka.ms/Pn08dw) 
    
Il poster contiene inoltre i codici QR per questi due articoli del blog. 
  
Nella figura relativa viene illustrato come è possibile aggiornare una foto da utilizzare per tutte le applicazioni di Office. 
  
1. Quando si aggiorna foto in Outlook, SharePoint o in Lync. Dopo aver aggiornato, viene utilizzata la foto aggiornata in tutte le applicazioni di Office. 
    
2. L'utente può utilizzare diversi metodi per l'aggiornamento di una foto: 
    
3. 
  - Client di Outlook o Outlook Web App (OWA) tramite la porta HTTP 443 a un server Accesso Client di Exchange. 
    
  - Sito personale tramite HTTP o HTTPS a un Server di SharePoint. SharePoint memorizza nella cache l'utente nel database del sito personale (Https:443). Impostare le interfacce di server di SharePoint con il Server accesso Client di Exchange utilizzando gli URL esterni di Exchange. 
    
  - Client Lync 2013, che gestisce una GetConnection con Exchange server per ottenere gli aggiornamenti foto (richiesta HTTPS Get - 443). 
    
4. Il Server accesso Client di Exchange si connette al Server di cassette postali di Exchange mediante le comunicazioni interne tra Exchange. 
    
5. Il Server cassette postali di Exchange utilizza Exchange 2013 per estrarre foto ad alta risoluzione utente di dominio Active Directory (LDAP:389). 
    
6. La foto è sincronizzata da servizi di dominio Active Directory (AD DS) per Lync indirizzo Book Service (ABS) in Lync Server in modo che i client legacy possono ottenere la stessa foto (LDAP:389). 
    
7. Il client Lync Legacy ora dispone dell'accesso per le foto. 
    
## <a name="unified-contact-store-tab"></a>Scheda archivio contatti unificata

### <a name="exchange-2013-is-the-contact-store-for-all-office-applications"></a>Exchange 2013 sia l'archivio contatti per tutte le applicazioni di Office

Archivio contatti unificato (UCS) offre un'esperienza coerente contatto tra prodotti Microsoft Office. Gli utenti archiviare delle informazioni sul contatti nella cassetta postale di Exchange 2013. Le stesse informazioni di contatto sono disponibile a livello globale in Lync, Exchange, Outlook e Outlook Web App. 
  
 **Prodotti server**
  
- Exchange Server 2013 
    
- Lync Server 2013 
    
 **Configurazione**
  
- Configurare l'autenticazione da server a server tra Exchange Server 2013 e Lync Server 2013. 
    
- In Lync 2013, attivare il criterio di archivio contatti unificato (abilitati per impostazione predefinita). 
    
Ad esempio gli script di configurazione, vedere articolo di blog del Jens portacampioni Rasmussen: 
  
- Integrazione di Exchange 2013 e Lync Server 2013 (http://aka.ms/Oyg7fh) 
    
 **Modalità di funzionamento**
  
- Contatti di Lync per un utente vengono eseguita la migrazione a Exchange 2013 automaticamente quando l'utente si disconnette con Lync 2013. 
    
- Gli utenti possono accedere e gestire i contatti di Lync di Lync 2013, Outlook 2013 o Outlook Web Access. 
    
Contatti dell'utente vengono migrati automaticamente al server Exchange 2013 quando l'utente: 
  
1. È stato assegnato un criterio Servizi utente che ha UcsAllowed impostata su **True**. 
    
2. È stato eseguito il provisioning con una cassetta postale di Exchange 2013 e ha effettuato l'accesso alla cassetta postale di almeno una volta. 
    
3. Esegue l'accesso a Lync utilizzando un rich client Lync 2013. 
    
Esegue l'accesso a Lync utilizzando un rich client Lync 2013. 
  
1. Esegue l'accesso alle cassette postali di Exchange 2013 sul Server accesso Client di Exchange, utilizzando un client Outlook o Outlook Web App (OWA) su HTTPS/443. Il Server cassette postali di Exchange utilizza le comunicazioni interne tra Exchange per comunicare con il Server accesso Client di Exchange. 
    
2. Esegue l'accesso a Lync 2013. Il client Lync contatti Lync server tramite SIP/5061 HTTPS/443. 
    
3. Il client Lync indica a Lync server che l'utente è abilitato per l'archivio contatti unificato tramite SIP/5061. 
    
4. Lync server utilizza il servizio di archiviazione di Lync per eseguire la migrazione dei contatti dell'utente per Exchange 2013 sul Server accesso Client di Exchange. 
    
5. È necessario disconnettersi e accedere a Lync 2013 le modifiche visualizzare (non illustrato nella figura). 
    
6. Dopo la migrazione, il client Lync utilizza i servizi Web Exchange (EWS) da leggere e gestire i contatti di Lync. 
    
## <a name="site-mailboxes-tab"></a>Scheda di cassette postali del sito

### <a name="a-central-filing-cabinet-for-emails-and-documents"></a>Un archivio centrale per documenti e messaggi di posta elettronica

Cassette postali del sito di migliorare la collaborazione e produttività degli utenti che consenta l'accesso ai documenti memorizzati in SharePoint e posta elettronica la memorizzazione dei messaggi di Exchange utilizzando la stessa interfaccia client. 
  
 **Prodotti server**
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
 **Configurazione**
  
Configurazione di SharePoint: 
  
- Configurare la sincronizzazione dei profili utente nella farm di SharePoint. 
    
- Configurare l'applicazione del servizio Gestione applicazioni della farm di SharePoint. 
    
- Configurare SSL per l'area predefinita per supportare l'autenticazione da server a server. 
    
- Installare l'API per servizi Web Exchange su server che eseguono SharePoint 2013. 
    
- Stabilire le autorizzazioni di protezione e il servizio OAuth su server che eseguono SharePoint 2013. 
    
Configurazione di Exchange: 
  
- Stabilire le autorizzazioni di protezione e il servizio OAuth sui server Exchange. 
    
- Creare criteri di provisioning delle cassette postali del sito. 
    
- Configurare prefisso del nome della cassetta postale del sito (facoltativo). 
    
 **Modalità di funzionamento**
  
Una cassetta postale del sito a livello funzionale è costituita da archiviazione appartenenze, i proprietari e membri, condivise del sito di SharePoint 2013 attraverso una cassetta postale di Exchange 2013 per i messaggi di posta elettronica e un sito di SharePoint 2013 per i documenti e un'interfaccia di gestione in grado di risolvere il provisioning di tipo ed è ciclo di vita. 
  
Nella figura relativa Mostra agli utenti con cassette postali del sito per accedere ai messaggi di posta elettronica in Outlook e documenti archiviati in SharePoint. 
  
1. Gli utenti possono accedere a documenti del sito del team di SharePoint tramite le cassette postali del sito in Outlook 2013 Pro Plus. 
    
2. Gli utenti possono inoltre leggere messaggi di posta elettronica in arrivo della cassetta postale del sito del sito del team di SharePoint. 
    
3. Messaggi di posta elettronica vengono archiviati in cassette postali del sito nel server di Exchange. 
    
4. Documenti vengono archiviati nelle cassette postali del sito in SharePoint Server. 
    
5. I metadati del contenuto nel sito di SharePoint viene sincronizzato con Exchange utilizzando la rappresentazione REST (State Transfer) API tramite HTTPS. 
    
### <a name="provisioning-and-management"></a>Provisioning e gestione

Cassette postali del sito sono stato eseguito il provisioning e gestite tramite SharePoint 2013. Sono disponibili le funzionalità di SharePoint e di Exchange per il provisioning e gestione. 
  
#### <a name="sharepoint"></a>SharePoint

Un diagramma vengono illustrati i componenti SharePoint necessari per eseguire il provisioning delle cassette postali del sito, tra cui: 
  
- App della cassetta postale del sito 
    
- I proprietari e i membri del sito del team 
    
- Ciclo di vita del sito del team 
    
Per eseguire il provisioning di una nuova cassetta postale del sito, installare l'app cassetta postale del sito nel sito del team e accedere almeno una volta l'app. 
  
L'appartenenza al sito di SharePoint determina che dispongono dell'accesso alla cassetta postale del sito. 
  
Conservazione delle cassette postali del sito segue lo stesso criterio del ciclo di vita configurato per il sito di SharePoint a cui è associato. 
  
#### <a name="exchange"></a>Exchange

La figura che mostra il criterio di Provisioning delle cassette postali del sito. Questo è il componente di Exchange che è necessario effettuare il provisioning delle cassette postali del sito.
  
Sul server di Exchange, è possibile definire criteri di Provisioning delle cassette postali di siti. Questi criteri determinano email caratteristiche inviati e ricevuti dalla cassetta postale del sito, la dimensione della cassetta postale del sito nel Server Exchange e consentono di definire un prefisso per gli indirizzi di posta elettronica della cassetta postale del sito. 
  
Per le distribuzioni di Exchange locale, è inoltre necessario periodicamente cercare ed eliminare le cassette postali del rito contrassegnate per l'eliminazione tramite i criteri del ciclo di vita di SharePoint. 
  
## <a name="exchange-task-synchronization-tab"></a>Scheda Exchange Task Synchronization

### <a name="synchronizing-tasks-among-sharepoint-server-2013-project-server-2013-and-exchange-server-2013"></a>Sincronizzazione delle attività tra SharePoint Server 2013, Project Server 2013 ed Exchange Server 2013

Utilizzando Exchange Task Synchronization, è possibile sincronizzare le attività di SharePoint Server 2013 e Project Server 2013 con Exchange Server 2013. Gli utenti possono visualizzare e gestire le attività di Outlook 2013 o nel proprio sito personale. 
  
 **Prodotti server**
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
- Project Server 2013 (facoltativo) 
    
 **Prerequisiti**
  
In Exchange 2013: 
  
- Configurare l'autorizzazione di protezione e il servizio OAuth. 
    
In SharePoint Server 2013: 
  
- Applicazione di servizio profili utente. 
    
- Utilizzo dell'applicazione di servizio di gestione. 
    
- Ricerca (è richiesto per le attività di SharePoint Server 2013). Configurare le ricerche per indicizzazione continue e ricerche per indicizzazione incrementali. 
    
- È necessario Secure Sockets Layer (SSL). 
    
- Gli utenti dispongono di siti personali esistenti. 
    
- Applicazione di servizio (aggregazione attività di Project Server) di Project. 
    
- API per servizi Web Exchange in ogni server front-end web (si tratta di un file separato .exe scaricabile che deve essere installato). 
    
In Project Server 2013: 
  
- Creare siti di applicazioni Web di Project. 
    
 **Modalità di funzionamento**
  
Quando la visualizzazione di attività personali nei siti personali viene aperto o aggiornamento: 
  
- Consente di sincronizzare l'applicazione di servizio di gestione del lavoro tra SharePoint Server e Project Server. 
    
- Processo Timer di sincronizzazione di Exchange chiama l'applicazione di servizio di gestione del lavoro per sincronizzare le attività con Exchange Server 2013. 
    
- La pagina attività personali nei siti personali viene aggiornata. 
    
Quando viene eseguito il processo Timer sincronizzazione di Exchange: 
  
- Consente di sincronizzare l'applicazione di servizio di gestione del lavoro tra SharePoint Server, Project Server ed Exchange Server. 
    
Nella figura relativa viene illustrata l'interazione tra SharePoint Server 2013, Exchange Server 2013, Outlook 2013 e Project Server 2013. 
  
SharePoint Server 2013 esegue i processi e le applicazioni seguenti: 
  
- Applicazione di servizio profili utente. 
    
- Applicazione del servizio di ricerca. 
    
- Utilizzo dell'applicazione di servizio di gestione, descritta di seguito. 
    
- Processo Timer di sincronizzazione di Exchange, i quali è descritto di seguito. 
    
- SharePoint Server 2013 contiene altri siti e siti personali dell'utente e viene eseguito numerose attività degli utenti. 
    
- SharePoint Server 2013 include un indice di ricerca. 
    
Exchange Server 2013 sono incluse le operazioni seguenti: 
  
- Database di Exchange con informazioni di posta elettronica utente 
    
- Attività di sincronizzazione 
    
Outlook 2013 vengono illustrate le seguenti: 
  
- Gli utenti possono optare per sincronizzare le attività, viene descritto di seguito. 
    
- Gli utenti possono visualizzare e modificare le attività di Outlook. 
    
Project Server 2013 viene illustrato di seguito: 
  
- Database di Project 
    
- Siti di Project Web Access con le attività 
    
L'applicazione di servizio di gestione del lavoro: 
  
- Consente di aggregare le attività da elenchi delle attività e gli elenchi SharePoint (non sincronizzare le attività con Exchange Server). 
    
- Sincronizza quando gli utenti visualizzano dei siti personali. 
    
- Gestisce l'elenco di utenti che hanno consenso esplicito. 
    
- Sincronizza il batch successivo di utenti. 
    
Il processo Timer di sincronizzazione di Exchange: 
  
- Determina il batch successivo di utenti. 
    
- Assicura che tutti gli utenti sono costantemente sincronizzati. 
    
- Avvia la chiamata all'applicazione di servizio di gestione del lavoro per Sincronizza attività con Exchange Server per gli utenti che si sono scelto di solo. 
    
Consentire 
  
- Gli utenti devono optare per sincronizzare le attività di Exchange con i siti personali o le attività di SharePoint Server 2013 e Project Server 2013 con Exchange Server 2013. 
    
## <a name="lync-presence-in-office-2013-outlook-web-app-and-sharepoint-server-tab"></a>Presenza di Lync nella scheda Office 2013, Outlook Web App e SharePoint Server

### <a name="lync-server-as-the-authoritative-source-of-presence-information"></a>Lync Server come origine autorevole delle informazioni sulla presenza

Utilizzando le informazioni sulla presenza di Lync, è possibile creare una visualizzazione coerenza delle informazioni sulla presenza tra Lync, Outlook e SharePoint. Informazioni sulla presenza di query Outlook direttamente da Lync in locale è installato nello stesso computer di Outlook. Quando gli utenti visualizzano le informazioni sulla presenza in SharePoint Server, le informazioni sulla presenza viene eseguita una query da Lync sul computer locale.
  
Prodotti client: 
  
- Outlook 2013 
    
- Lync 2013 
    
Prodotti server: 
  
- Exchange Server 2013 
    
- Lync Server 2013 
    
- SharePoint Server 2013 
    
 **Modalità di funzionamento**
  
Purché nel computer locale dell'utente è installato Lync 2013, Outlook e SharePoint Server automaticamente visualizzare le informazioni sulla presenza degli utenti. 
  
Per gli utenti di Outlook Web App, accesso client di Exchange esegue una query sulla presenza per conto dell'utente. 
  
 **Esistono due diagrammi corrispondente**
  
Il primo viene illustrato come un utente accede a Outlook Web App e quindi scambiare query di Lync Server per informazioni sulla presenza. 
  
1. L'utente accede a Outlook Web App. Il computer client accede il Server accesso Client di Exchange (CAS) su HTTPS/443 e anche chiama il Server cassette postali di Exchange con una comunicazione di Exchange interna. 
    
2. L'utente accede al proprio Exchange 2013 delle cassette postali e accesso client di Exchange invia query Lync Server per informazioni sulla presenza tramite SIP / MTLS:5061. 
    
Per ulteriori informazioni, vedere [integrazione di Microsoft Lync Server 2013 e Microsoft Outlook Web App 2013](https://go.microsoft.com/fwlink/?LinkId=313522).
  
Il secondo diagramma mostra come Outlook e SharePoint Server utilizzare Lync 2013 per visualizzare le informazioni sulla presenza degli utenti. 
  
1. L'utente accede a Lync 2013 su SIP / TLS:5061 che chiama Lync server. 
    
2. R. l'utente esegue l'accesso alle cassette postali di Exchange 2013 tramite Outlook in Office 2013. Il computer client accede il Server accesso Client di Exchange (CAS) su HTTPS/443 e chiama inoltre il Server cassette postali di Exchange con una comunicazione di Exchange interna. 
    
3. R. outlook chiama Lync installato nello stesso computer di Outlook per recuperare le informazioni sulla presenza. 
    
4. B. l'utente si connette a SharePoint MySite su HTTP o HTTPS, che chiama il server di SharePoint. 
    
5. B. Internet Explorer chiama Lync è installato nello stesso computer del browser, per recuperare le informazioni sulla presenza. 
    
## <a name="voicemail-tab"></a>Scheda segreteria telefonica

### <a name="exchange-um-is-the-voicemail-system-for-lync-server"></a>Messaggistica unificata di Exchange è il sistema di segreteria telefonica per Lync Server

Segreteria telefonica consente a un chiamante di lasciare un messaggio vocale per gli utenti di Lync con Exchange messaggistica unificata (UM). 
  
Prodotti client: 
  
- Lync 2013 
    
- Dispositivo di rete PSTN (PBX, cellulare, POTS) 
    
Prodotti server: 
  
- Exchange Server 2013 
    
- Exchange Server 2013 
    
 **Modalità di funzionamento**
  
Quando una chiamata non riceve risposta dal destinatario della chiamata in qualsiasi endpoint attivi del destinatario della chiamata, Lync Server indirizza la chiamata alla segreteria telefonica nella messaggistica unificata di Exchange (ad esempio Server di cassette postali di Exchange). 
  
Nella figura relativa viene illustrato il routing delle chiamate per due scenari: 
  
- Il chiamante viene inviata una chiamata con Lync 2013. 
    
- Il chiamante viene inviata una chiamata con dispositivi PSTN (PBX, cellulare, POTS). 
    
Il chiamante avvia una chiamata con Lync 2013: 
  
1. Avvia il chiamante A una chiamata al destinatario della chiamata utilizzando Lync 2013. La chiamata viene avviata e inviata a Lync Server. 
    
2. La chiamata viene indirizzata al server principale del destinatario della chiamata Lync. 
    
3. Lync Server chiama endpoint attivi del destinatario della chiamata in Lync 2013. 
    
4. Quando la chiamata non riceve risposta, la chiamata viene indirizzata alla segreteria telefonica (messaggistica unificata di Exchange) in CAS di Exchange (router di chiamata). 
    
Il chiamante avvia una chiamata con Lync 2013: 
  
1. Chiamante B compone il numero di telefono del destinatario della chiamata tramite PSTN. 
    
2. La chiamata PSTN viene instradata dal gateway IP di Mediation Server, ovvero un server Lync. 
    
3. Il server Mediation server routs la chiamata al server principale del destinatario della chiamata Lync. 
    
4. Lync Server chiama endpoint attivi del destinatario della chiamata in Lync 2013. 
    
5. Quando la chiamata non riceve risposta, la chiamata viene indirizzata alla segreteria telefonica (messaggistica unificata di Exchange) in CAS di Exchange (router di chiamata). 
    
## <a name="meeting-recordings-tab"></a>Scheda registrazioni di riunioni

### <a name="publish-your-meeting-recordings-on-your-sharepoint-team-site"></a>Pubblicare le registrazioni delle riunioni nel sito del team di SharePoint

Registrazioni delle riunioni sono un componente principale delle comunicazioni unificate. Un modo efficace per condividere le registrazioni delle riunioni consiste nell'utilizzare raccolte di risorse di SharePoint per i siti del team per archiviare le registrazioni delle riunioni. 
  
Prodotti client: 
  
- Lync 2013 
    
Prodotti server: 
  
- Prodotti server: 
    
- SharePoint 2013 
    
Prerequisiti: 
  
- Lync 2013, Registrazione delle riunioni è una funzionalità sul lato client in Lync 2013. 
    
- SharePoint 2013, È necessario il sito del team in cui si desidera archiviare le registrazioni delle riunioni già configurate e in esecuzione. 
    
 **Ciò che viene registrato?**
  
Di seguito viene registrati in un file MP4 durante la riunione (ogni punto preceduto da un'icona che rappresenta il tipo di registrazione): 
  
- Tutti i file audio 
    
- Il video, se utilizzato, di altoparlante attivo 
    
- Video panorama (se utilizzato) 
    
- Tutto il contenuto presentato 
    
- I messaggi immediati * 
    
* Solo i messaggi immediati all'interno della riunione sono inclusi. Qualsiasi messaggistica peer-to-peer tra i partecipanti alla riunione non fa parte della riunione e pertanto non viene acquisita. 
  
Il poster include due diagrammi per due diversi scenari: 
  
- Preparazione per la pubblicazione di registrazioni delle riunioni 
    
- Registrazione e la pubblicazione di una riunione utilizzando il client Lync 
    
### <a name="preparing-for-publishing-meeting-recordings"></a>Preparazione per la pubblicazione di registrazioni delle riunioni

Il diagramma mostra SharePoint Server 2013 con un sito del Team, l'interfaccia di amministrazione centrale e Server Internet Information Services (IIS). 
  
Contiene il sito del Team: 
  
- Le risorse della libreria app. 
    
- Raccolta di risorse riunioni, ai team membri inviano registrazioni delle riunioni. 
    
L'interfaccia di amministrazione centrale contiene impostazioni generali applicazione web. 
  
Il Server IIS contiene le impostazioni di IIS. 
  
Preparazione per la pubblicazione di registrazioni delle riunioni: 
  
1. Nel sito del team di SharePoint, aggiungere la raccolta di risorse App facoltativamente, se non è possibile caricare registrazioni delle riunioni a causa di limitazioni relative alle dimensioni o timeout connessioni, eseguire i passaggi aggiuntivi 2 e 3. 
    
2. In Amministrazione centrale SharePoint, modificare l'impostazione dimensioni massime di caricamento per l'applicazione web che contiene la raccolta siti del team. 
    
3. Nelle impostazioni del Server IIS, aumentare il timeout della connessione di IIS per il sito web che contiene la raccolta siti del team. 
    
 **Raccolte risorse digitali**
  
Le raccolte risorse digitali sono raccolte di risorse contenenti video che determinati negativamente sulle prestazioni e capacità. Per ulteriori informazioni, vedere Pianificare le raccolte risorse digitali in SharePoint Server 2013 che si trovano in http://aka.ms/O1vq5w. Il poster include inoltre un codice QR per accedere a queste informazioni. 
  
### <a name="recording-and-publishing-a-meeting-using-the-lync-client"></a>Registrazione e la pubblicazione di una riunione utilizzando il client Lync

Il diagramma mostra un utente utilizzando Lync di partecipare a una riunione. La riunione viene registrata con il client di Lync, che consente di creare un file MP4 con il contenuto delle riunioni. La registrazione MP4 viene salvata per la cartella delle registrazioni Lync nel computer in uso. È possibile spostare la registrazione MP4 per la raccolta di risorse di riunioni, da cui è possibile inserirlo in un wiki, pagina di SharePoint o blog. 
  
 **Per registrare e pubblicare una riunione utilizzando il client Lync**
  
1. Avviare la registrazione della riunione mediante il client Lync. 
    
2. Il contenuto delle riunioni è registrato in un file MP4 durante la riunione. 
    
3. Dopo la conclusione alla riunione, la registrazione MP4 visualizzata nella cartella di registrazione nel computer in uso (c:\\utenti\\<username>\\video\\registrazioni di Lync). Facoltativamente, è possibile personalizzare la registrazione di riunioni tramite app Lync Recording Manager Ottiene installato con client Lync. 
    
4. Trascinare e rilasciare la riunione registrando nella raccolta di risorse di SharePoint. 
    
5. Facoltativo: Dopo la registrazione è nella raccolta di risorse, è possibile inserire in tutte le pagine di SharePoint. Per ulteriori informazioni su questo passaggio, vedere la voce del blog di Office 365, creare e pubblicare i video di formazione con SharePoint e Lync Online, che si trova in http://aka.ms/R61q35. 
    
 **Anteprime video**
  
Anteprime video migliorano l'aspetto della raccolta risorse. Per ulteriori informazioni sulla creazione di miniature per le registrazioni delle riunioni, vedere Capture o modificare un'anteprima del video, disponibile all'indirizzo http://aka.ms/Kupj85. Il poster include inoltre un codice QR per accedere a queste informazioni. 
  

