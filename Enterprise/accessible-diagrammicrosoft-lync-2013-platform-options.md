---
title: Diagramma accessibile - opzioni della piattaforma Microsoft Lync 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: In questo articolo è una versione testo accessibile del diagramma denominato opzioni della piattaforma Microsoft Lync 2013, disponibile all'indirizzo Technical Diagrams.
ms.openlocfilehash: 4a660df4bfacad2a00f5d9fbb5e1b668840e3b9f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
ms.locfileid: "17504089"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a>Diagramma accessibile - opzioni della piattaforma Microsoft Lync 2013

**Riepilogo:** In questo articolo è una versione testo accessibile del diagramma denominato opzioni della piattaforma Microsoft Lync 2013, disponibile all'indirizzo [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).
  
Questo poster viene descritto cosa decisori aziendali (hanno) e progettisti devono essere a conoscenza Lync Online (Office 365) e le distribuzioni di Lync Server e sono incluse:
  
- Un confronto tra quattro diverse opzioni di distribuzione: Lync Online (Office 365), Lync Online/Server ibrido, Lync Server e Provider-Hosted Lync Server. 
    
- Due scenari di esempio per la distribuzione di Lync 2013.
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a>Confronto tra quattro diverse distribuzioni per la piattaforma Lync 2013

Il confronto vengono fornite informazioni su ogni opzione di distribuzione nelle aree seguenti: 
  
- Panoramica delle funzionalità di distribuzione diversi
    
- Vantaggi dell'implementazione di ogni opzione di distribuzione
    
- Requisiti relativi alle licenze
    
- Richiesta attività dell'architettura
    
- Responsabilità di professionisti IT per l'implementazione di ogni opzione di distribuzione
    
### <a name="overview"></a>Panoramica

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Maggiore efficienza e ottimizzare per costo con Office 365 plans multi-tenant.
  
Nella figura relativa Mostra Lync Online con un tenant di Azure Active Directory, che consente di sincronizzare i nomi degli account e password tra l'ambiente di servizi di dominio Active Directory (AD DS) locali e il tenant di Azure Active Directory. 
  
Descrizione delle funzionalità e caratteristiche:
  
- Software come servizio (SaaS).
    
- RTF funzionalità set che siano sempre aggiornati.
    
- Include un tenant di Azure Active Directory per gli account in linea, che può essere utilizzato con altre applicazioni. 
    
- Integrazione di directory include la sincronizzazione dei nomi di account e password tra l'ambiente di servizi di dominio Active Directory (AD DS) locali e il tenant di Azure Active Directory.
    
- Se il single sign-on (SSO) è un requisito, è necessario implementare Active Directory Federation Services (ADFS). 
    
- La comunicazione client tramite Internet è crittografata e autenticata.
    
- Apparecchiatura, telefono legacy pubblica commutata (PSTN) telephone network, connettività è disponibile attraverso i provider di terze parti.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server ibrido (dominio diviso)

È possibile combinare i vantaggi di Office 365 per una distribuzione locale di Lync 2013.
  
Il diagramma accompagnamento Mostra Office 365 con Lync Online in cui alcuni utenti sono in locale e alcuni utenti ospitati in linea. Viene visualizzato anche un Edge Server distribuiti in locale.
  
Descrizione delle funzionalità e caratteristiche:
  
- Alcuni utenti sono ospitati in locale e alcuni utenti ospitati in linea, ma gli utenti hanno lo stesso dominio SIP (ad esempio contoso.com).
    
- Infrastruttura esistente Lync Server 2013, incluse le connessioni alla rete PSTN.
    
- Aggiungere nuovi utenti di Lync Online con facilità quando non richiedono PSTN.
    
- Eseguire la migrazione da Lync in locale con Lync Online nel tempo, al calendario.
    
- Integrazione con altre applicazioni di Office 365, inclusi Exchange Online e SharePoint Online.
    
#### <a name="lync-server"></a>Lync Server

In questa distribuzione si è proprietari tutto il contenuto. Il diagramma accompagnamento Mostra un'infrastruttura di Lync Server con un ambiente di servizi di dominio Active Directory (AD DS) locale in cui gli utenti sono in locale.
  
Descrizione delle funzionalità e caratteristiche:
  
- Pianificazione della capacità e dimensionamento.
    
- Acquisizione di server e il programma di installazione.
    
- Distribuzione.
    
- Scalabilità orizzontale, applicazione di patch e operazioni.
    
- Backup dei dati.
    
- Gestione di failover e ripristino di emergenza.
    
- Connessione alla rete PSTN dell'infrastruttura di Lync Server 2013.
    
- Integrazione con l'apparecchio telefonico esistente, ad esempio lo scambio di centralino (PBX).
    
#### <a name="provider-hosted-lync-server"></a>Ospitate da provider Lync Server

In questa distribuzione, il provider è proprietario tutto il contenuto. Il diagramma accompagnamento Mostra rete del provider, inclusi i server e apparecchiature con una connessione a un ambiente locale.
  
Descrizione delle funzionalità e caratteristiche:
  
- Pianificazione della capacità e dimensionamento.
    
- Acquisizione di server e il programma di installazione.
    
- Distribuzione.
    
- Scalabilità orizzontale, applicazione di patch e operazioni.
    
- Backup dei dati.
    
- Gestione di failover e ripristino di emergenza.
    
- Integrazione con l'apparecchio telefonico esistente, ad esempio lo scambio di centralino (PBX).
    
- Inoltre, il provider può:
    
  - Installare i server e apparecchiature la propria rete con una connessione ai propri locali (linea continua).
    
  - Installare i server il locale (linea tratteggiata).
    
### <a name="benefits-of-implementing-each-deployment-option"></a>Vantaggi dell'implementazione di ogni opzione di distribuzione

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- Nessun carico operativo del server locale o software del server.
    
- Funzionalità di comunicazione di Lync Server 2013 come un servizio basato su cloud.
    
- Presenza di Lync, messaggistica immediata, audio e video di chiamata avanzate riunioni in linea e funzionalità di conferenza web estesa.
    
- Utilizzato con le organizzazioni su più aree geografiche o dipendenti principalmente per dispositivi mobili.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server ibrido (dominio diviso)

- Utilizzare Lync Online per utenti remoti e l'integrazione con i partner commerciali.
    
- Effettuare una migrazione da Lync in locale con Lync Online.
    
- Supportare siti remoti senza utilizzare un branch appliance di office.
    
- Facilità di aggiunta del supporto di Lync per nuove acquisizioni aziendali.
    
#### <a name="lync-server"></a>Lync Server

- Soluzioni basate su cloud privata.
    
- Soluzioni fortemente personalizzate.
    
- Soluzioni legacy con i componenti di terze parti che dipendono da hardware e software che non sono supportate da Lync Online.
    
- Limitazioni relative alla privacy che impediscono la sincronizzazione degli account di dominio Active Directory con Office 365.
    
- Organizzazioni che desiderano controllo dell'intera piattaforma e soluzione.
    
- Sostituzione di PBX con VoIP aziendale di Lync.
    
#### <a name="provider-hosted-lync-server"></a>Ospitate da provider Lync Server

- Organizzazioni che desiderano funzionalità di Lync Server ma si desidera affidare la distribuzione e manutenzione.
    
- Soluzioni basate su provider.
    
- Soluzioni fortemente personalizzate.
    
- Soluzioni legacy con i componenti di terze parti che dipendono da hardware e software che non sono supportate da Lync Online.
    
- Sostituzione di PBX con VoIP aziendale di Lync.
    
### <a name="license-requirements"></a>Requisiti relativi alle licenze

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Modello di sottoscrizione.
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server ibrido (dominio diviso)

- Office 365, ovvero Modello di sottoscrizione. Nessuna licenza aggiuntiva necessaria. 
    
- Locale, Si applicano tutte le licenze locali. 
    
#### <a name="lync-server"></a>Lync Server

- Sistema operativo del server
    
- SQL Server
    
- Licenza Server di Lync 2013
    
- Licenza di accesso Client di Lync 2013
    
#### <a name="provider-hosted-lync-server"></a>Ospitate da provider Lync Server

Costi sono basati sul contratto con provider di soluzioni Lync.
  
### <a name="architecture-tasks"></a>Attività di architettura

In questa sezione sono elencate le attività dell'architettura per ogni opzione di distribuzione.
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- Pianificare e progettare sincronizzazione della directory.
    
- Verificare la capacità di rete e la disponibilità attraverso i firewall, server proxy, gateway e sui collegamenti WAN.
    
- Ottenere i certificati SSL di terze parti per garantire la sicurezza aziendale per le offerte di servizi di Office 365.
    
- Decidere se si desidera connettersi a Office 365 con Internet Protocol versione 6 (IPv6).
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server ibrido (dominio diviso)

Oltre alle attività per gli ambienti di Office 365 e locali:
  
- Determinare la quantità integrazione delle funzionalità che si desidera utilizzare con organizzazioni locali e le versioni di Exchange Server e SharePoint online.
    
- Se necessario, determinare quali dispositivi server proxy da utilizzare per le richieste da Office 365.
    
#### <a name="lync-server"></a>Lync Server

Progettare l'ambiente Lync in un ambiente locale esistente:
  
- Topologie di Lync per centrali e nelle succursali.
    
- Hardware del server, tra cui la virtualizzazione.
    
- Integrazione con servizi di dominio Active Directory (AD DS) e DNS.
    
- Bilanciamento del carico per pool di Lync server.
    
- Failover e ripristino di emergenza.
    
#### <a name="provider-hosted-lync-server"></a>Ospitate da provider Lync Server

- Determinare la connessione alla rete del provider di servizi per un'installazione basata su cloud.
    
- Per un'installazione locale, determinare la posizione dei server di Lync Server del provider nella rete.
    
- Per entrambi i tipi, determinare l'integrazione con Active Directory e il dispositivo il PBX.
    
### <a name="it-pro-responsibilities"></a>Responsabilità di professionisti IT

In questa sezione sono elencate le responsabilità per professionisti IT per ogni opzione di distribuzione.
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Distribuire e gestire Lync Online (Office 365):
  
- Implementare il piano di sincronizzazione della directory.
    
- Pianificare e implementare i record DNS interni ed esterni e il routing.
    
- Configurare il proxy o del firewall per l'indirizzo IP di Office 365 e requisiti per gli URL.
    
- Gestire gli account utente e le impostazioni di Lync Online.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server ibrido (dominio diviso)

Oltre alle attività per gli ambienti di Office 365 e locali:
  
- Configurare il dispositivo di server proxy, se necessario.
    
- Configurare l'integrazione delle funzionalità con le versioni di Exchange Server e SharePoint online e locale.
    
#### <a name="lync-server"></a>Lync Server

Distribuzione e la gestione di Lync Server in un ambiente locale:
  
- I server di provisioning.
    
- Distribuire la topologia di Lync.
    
- Aggiornare i server Lync.
    
- Aggiungere o rimuovere i server della topologia in base alle esigenze basato sull'utilizzo.
    
- Implementare l'ambiente di ripristino di emergenza e failover.
    
#### <a name="provider-hosted-lync-server"></a>Ospitate da provider Lync Server

È possibile utilizzare con il provider di:
  
- Integrazione di Lync Server nella rete.
    
- Integrazione di Lync Server con altri prodotti Microsoft o soluzioni personalizzate.
    
- Monitoraggio della conformità con provider contratto di servizio (SLA).
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a>Due scenari di esempio per la distribuzione di Lync 2013

### <a name="directory-synchronization-components-in-microsoft-azure"></a>Componenti della sincronizzazione della directory in Microsoft Azure

Distribuzione di Office 365 componenti di sincronizzazione della directory in Azure è superiore a causa la possibilità di distribuire le macchine virtuali su richiesta.
  
Nella figura relativa Mostra Lync Online con un tenant di Azure Active Directory, che consente di sincronizzare i nomi degli account e password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory.
  
 **Solo i server di sincronizzazione della directory**. Invece di distribuire il server di sincronizzazione directory a 64 bit nell'ambiente locale, eseguire il provisioning una macchina virtuale in Azure tramite Internet.
  
 **La sincronizzazione delle directory + ADFS**. Questa opzione consente di supportare le identità federata di Office 365 (SSO) senza aggiungere componenti hardware per l'infrastruttura locale. Fornisce inoltre resilienza se non è disponibile nell'ambiente Active Directory locale. Le funzionalità di questa opzione includono:
  
- Componenti di integrazione directory eseguire con macchine virtuali di Azure.
    
- ADFS viene pubblicato su Internet tramite proxy AD FS in esecuzione come macchine virtuali di Azure.
    
- Il traffico di autenticazione client, per gli utenti che si connettono da qualsiasi posizione, viene gestito dal server ADFS e i proxy che vengono distribuiti come macchine virtuali di Azure.
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a>Integrazione di Lync con Exchange e SharePoint in Office 365

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a>Lync Server con Exchange Online e SharePoint Online

Il diagramma accompagnamento mostra che Office 365 con Exchange Online e SharePoint Online connessa a una farm di Lync Server 2013 locale.
  
I vantaggi della distribuzione consentono di:
  
- Utilizzare il set completo di funzionalità di Lync Server 2013.
    
- Utilizzare l'apparecchio telefonico locale esistente, ad esempio PBX.
    
- Utilizzare Exchange Online per la posta elettronica, gestione il carico dei server di posta elettronica locale e l'archiviazione.
    
- Utilizzare SharePoint Online per la collaborazione, gestione il carico di lavoro di gestione di server di SharePoint locali.
    
- Utilizzare Lync, Exchange e SharePoint integrato funzionalità, inclusi messaggistica unificata (UM) in Office 365.
    
#### <a name="exchange-server-with-lync-online"></a>Server di Exchange con Lync Online

Il diagramma accompagnamento mostra che Office 365 con Lync Online connessa a una farm di Server di Exchange locale.
  
I vantaggi della distribuzione consentono di:
  
- Infrastruttura esistente Exchange.
    
- Utilizzare Lync Online per la presenza, messaggistica immediata e le funzionalità di conferenza.
    

