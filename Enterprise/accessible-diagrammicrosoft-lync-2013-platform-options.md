---
title: Diagramma accessibile-opzioni della piattaforma Microsoft Lync 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: Questo articolo è una versione di testo accessibile del diagramma denominato opzioni della piattaforma Microsoft Lync 2013, disponibile nei diagrammi tecnici.
ms.openlocfilehash: 4993ad90307973589da6dc5081d8c2875b44ce66
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068612"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a>Diagramma accessibile-opzioni della piattaforma Microsoft Lync 2013

**Riepilogo:** Questo articolo è una versione di testo accessibile del diagramma denominato opzioni della piattaforma Microsoft Lync 2013, disponibile nei [diagrammi tecnici](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).
  
In questo poster vengono descritti i responsabili decisionali aziendali (BDMs) e gli architetti che devono essere a conoscenza delle distribuzioni di Lync Online (Office 365) e di Lync Server e include:
  
- Confronto tra quattro opzioni di distribuzione diverse: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server e Lync Server ospitato dal provider. 
    
- Due scenari di esempio per la distribuzione di Lync 2013.
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a>Confronto tra quattro distribuzioni diverse per la piattaforma Lync 2013

Il confronto fornisce informazioni su ogni opzione di distribuzione nelle aree seguenti: 
  
- Panoramica delle diverse funzionalità di distribuzione
    
- Vantaggi dell'implementazione di ogni opzione di distribuzione
    
- Requisiti relativi alle licenze
    
- Attività di architettura necessarie
    
- Responsabilità per i professionisti IT per l'implementazione di ogni opzione di distribuzione
    
### <a name="overview"></a>Panoramica

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

È possibile ottenere efficienza e ottimizzare i costi con i piani multitenant di Office 365.
  
Nel diagramma di accompagnamento viene mostrato Lync Online con un tenant di Azure Active Directory, che sincronizza i nomi degli account e le password tra l'ambiente Servizi di dominio Active Directory locale e il tenant di Azure Active Directory. 
  
Descrizione delle funzionalità e delle funzionalità:
  
- Software come servizio (SaaS).
    
- Set di funzionalità RTF sempre aggiornato.
    
- Include un tenant di Azure Active Directory per gli account online, che può essere utilizzato con altre applicazioni. 
    
- L'integrazione della directory include la sincronizzazione dei nomi degli account e delle password tra l'ambiente Servizi di dominio Active Directory locale e il tenant di Azure Active Directory.
    
- Se il servizio Single Sign-on (SSO) è un requisito, è necessario implementare Active Directory Federation Services (AD FS). 
    
- La comunicazione client su Internet è crittografata e autenticata.
    
- Apparecchiature telefoniche legacy, rete PSTN (Public Switched Telephone Network), la connettività è disponibile tramite provider di terze parti.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/server ibrido (dominio diviso)

È possibile combinare i vantaggi di Office 365 con una distribuzione locale di Lync 2013.
  
Nel diagramma di accompagnamento viene mostrato Office 365 con Lync online in cui alcuni utenti sono ospitati in locale e alcuni utenti sono alloggiati online. Viene inoltre visualizzato un server perimetrale distribuito in locale.
  
Descrizione delle funzionalità e delle funzionalità:
  
- Alcuni utenti sono ospitati in locale e alcuni utenti sono ospitati online, ma gli utenti condividono lo stesso dominio SIP, ad esempio contoso.com.
    
- Sfruttare l'infrastruttura di Lync Server 2013 esistente, incluse le connessioni alla rete PSTN.
    
- Aggiungere facilmente nuovi utenti di Lync Online quando non richiedono PSTN.
    
- Eseguire la migrazione da Lync locale a Lync Online nel tempo, nella pianificazione.
    
- Integrazione con altre applicazioni di Office 365, tra cui Exchange Online e SharePoint Online.
    
#### <a name="lync-server"></a>Lync Server

In questa distribuzione, si è proprietari di tutto. Il diagramma di accompagnamento Visualizza un'infrastruttura di Lync Server con un ambiente Servizi di dominio Active Directory (AD DS) locale in cui gli utenti sono ospitati in locale.
  
Descrizione delle funzionalità e delle funzionalità:
  
- Pianificazione della capacità e dimensionamento.
    
- Acquisizione e installazione del server.
    
- Distribuzione.
    
- Scalabilità orizzontale, applicazione di patch e operazioni.
    
- Backup dei dati.
    
- Gestione del failover e del ripristino di emergenza.
    
- Connessione dell'infrastruttura Lync Server 2013 alla rete PSTN.
    
- Integrazione con le apparecchiature telefoniche esistenti, ad esempio i sistemi PBX (Private Branch Exchange).
    
#### <a name="provider-hosted-lync-server"></a>Lync Server ospitato dal provider

In questa distribuzione il provider possiede tutto. Il diagramma di accompagnamento Visualizza la rete di un provider, inclusi i server e le apparecchiature con una connessione a un ambiente locale.
  
Descrizione delle funzionalità e delle funzionalità:
  
- Pianificazione della capacità e dimensionamento.
    
- Acquisizione e installazione del server.
    
- Distribuzione.
    
- Scalabilità orizzontale, applicazione di patch e operazioni.
    
- Backup dei dati.
    
- Gestione del failover e del ripristino di emergenza.
    
- Integrazione con le apparecchiature telefoniche esistenti, ad esempio i sistemi PBX (Private Branch Exchange).
    
- Inoltre, il provider può:
    
  - Installare i propri server e le proprie apparecchiature nella propria rete con una connessione alla propria sede (linea continua).
    
  - Installare i propri server nella propria sede (linea tratteggiata).
    
### <a name="benefits-of-implementing-each-deployment-option"></a>Vantaggi dell'implementazione di ogni opzione di distribuzione

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- Nessun onere operativo dei server locali o del software del server.
    
- Funzionalità di comunicazione di Lync Server 2013 come servizio basato su cloud.
    
- Presenza di Lync, messaggistica istantanea, chiamata audio e video, riunioni online ricche e funzionalità di Web Conferencing estese.
    
- Utilizzato con organizzazioni geograficamente disperse o con dipendenti principalmente mobili.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/server ibrido (dominio diviso)

- Utilizzare Lync Online per gli utenti remoti e l'integrazione con i partner commerciali.
    
- Semplificare la migrazione da Lync locale a Lync Online.
    
- Supporto di siti remoti senza l'utilizzo di un dispositivo di succursale.
    
- Semplificazione dell'aggiunta del supporto di Lync per nuove acquisizioni aziendali.
    
#### <a name="lync-server"></a>Lync Server

- Soluzioni cloud private.
    
- Soluzioni altamente personalizzate.
    
- Soluzioni legacy con componenti di terze parti che dipendono da hardware e software che non sono supportati da Lync Online.
    
- Restrizioni sulla privacy che impediscono la sincronizzazione degli account di servizi di dominio Active Directory con Office 365.
    
- Organizzazioni che desiderano controllare l'intera piattaforma e la soluzione.
    
- Sostituzione del PBX con Lync Enterprise Voice.
    
#### <a name="provider-hosted-lync-server"></a>Lync Server ospitato dal provider

- Organizzazioni che desiderano funzionalità di Lync Server, ma che desiderano esternalizzare la distribuzione e la manutenzione.
    
- Soluzioni basate sul provider.
    
- Soluzioni altamente personalizzate.
    
- Soluzioni legacy con componenti di terze parti che dipendono da hardware e software che non sono supportati da Lync Online.
    
- Sostituzione del PBX con Lync Enterprise Voice.
    
### <a name="license-requirements"></a>Requisiti di licenza

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Modello di sottoscrizione.
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/server ibrido (dominio diviso)

- Office 365: modello di sottoscrizione. Non sono necessarie licenze aggiuntive. 
    
- Locale: vengono applicate tutte le licenze locali. 
    
#### <a name="lync-server"></a>Lync Server

- Sistema operativo del server
    
- SQL Server
    
- Licenza del server Lync 2013
    
- Licenza di accesso client Lync 2013
    
#### <a name="provider-hosted-lync-server"></a>Lync Server ospitato dal provider

I costi sono basati sull'accordo con il provider di soluzioni Lync.
  
### <a name="architecture-tasks"></a>Attività dell'architettura

In questa sezione sono elencate le attività di architettura per ogni opzione di distribuzione.
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- Pianificare e progettare la sincronizzazione della directory.
    
- Garantire la disponibilità e la capacità della rete attraverso i firewall, i server proxy, i gateway e i collegamenti WAN.
    
- Acquisizione dei certificati SSL di terze parti per fornire la sicurezza aziendale per le offerte di servizi di Office 365.
    
- Decidere se si desidera connettersi a Office 365 con Internet Protocol versione 6 (IPv6).
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/server ibrido (dominio diviso)

Oltre alle attività sia per gli ambienti Office 365 che per quelli locali:
  
- Determinare la quantità di integrazione delle funzionalità che si desidera utilizzare con le versioni locali e online di Exchange Server e SharePoint.
    
- Se necessario, determinare quale dispositivo server proxy verrà utilizzato per le richieste provenienti da Office 365.
    
#### <a name="lync-server"></a>Lync Server

Progettare l'ambiente Lync in un ambiente locale esistente:
  
- Topologia di Lync per centrali e succursali.
    
- Hardware del server, inclusa la virtualizzazione.
    
- Integrazione con servizi di dominio Active Directory (AD DS) e DNS.
    
- Bilanciamento del carico per i pool di Lync Server.
    
- Failover e ripristino di emergenza.
    
#### <a name="provider-hosted-lync-server"></a>Lync Server ospitato dal provider

- Per un'installazione basata sul cloud, determinare la connessione alla rete del provider di servizi.
    
- Per un'installazione locale, determinare la posizione dei server Lync del provider sulla rete.
    
- Per entrambi i tipi, determinare l'integrazione con servizi di dominio Active Directory e le apparecchiature PBX.
    
### <a name="it-pro-responsibilities"></a>Responsabilità per i professionisti IT

In questa sezione sono elencate le responsabilità per i professionisti IT per ogni opzione di distribuzione.
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Distribuire e gestire Lync Online (Office 365):
  
- Implementare il piano di sincronizzazione della directory.
    
- Pianificare e implementare i record DNS interni ed esterni e il routing.
    
- Configurare il proxy o il firewall per i requisiti di indirizzo IP e URL di Office 365.
    
- Amministrare gli account utente e le impostazioni di Lync Online.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/server ibrido (dominio diviso)

Oltre alle attività sia per gli ambienti Office 365 che per quelli locali:
  
- Configurare il dispositivo server proxy, se necessario.
    
- Configurare l'integrazione delle funzionalità con le versioni locali e online di Exchange Server e SharePoint.
    
#### <a name="lync-server"></a>Lync Server

Distribuire e gestire Lync Server in un ambiente locale:
  
- Eseguire il provisioning dei server.
    
- Distribuire la topologia di Lync.
    
- Aggiornare i server Lync.
    
- Aggiungere o rimuovere i server di topologia in base all'utilizzo.
    
- Implementare l'ambiente di failover e ripristino di emergenza.
    
#### <a name="provider-hosted-lync-server"></a>Lync Server ospitato dal provider

Collaborare con il provider per:
  
- Integrazione di Lync Server nella rete.
    
- Integrazione di Lync Server con altri prodotti Microsoft o soluzioni personalizzate.
    
- Monitorare l'aderenza con il contratto di servizio provider (SLA, Service Level Agreement).
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a>Due scenari di esempio per la distribuzione di Lync 2013

### <a name="directory-synchronization-components-in-microsoft-azure"></a>Componenti di sincronizzazione della directory in Microsoft Azure

La distribuzione dei componenti di sincronizzazione della directory di Office 365 in Azure è più veloce grazie alla possibilità di distribuire macchine virtuali su richiesta.
  
Nel diagramma di accompagnamento viene mostrato Lync Online con un tenant di Azure Active Directory, che sincronizza i nomi degli account e le password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory.
  
 **Solo server di sincronizzazione della directory**. Invece di distribuire il server di sincronizzazione della directory a 64 bit nell'ambiente locale, è possibile eseguire il provisioning di una macchina virtuale in Azure su Internet.
  
 **Sincronizzazione della directory +** ADFS. Questa opzione consente di supportare le identità federative di Office 365 senza aggiungere hardware all'infrastruttura locale. Inoltre, fornisce resilienza se l'ambiente Active Directory locale non è disponibile. Le caratteristiche di questa opzione includono:
  
- I componenti di integrazione della directory vengono eseguiti come macchine virtuali di Azure.
    
- Ad FS viene pubblicato su Internet tramite proxy ADFS in esecuzione come macchine virtuali di Azure.
    
- Il traffico di autenticazione del client, per gli utenti che si connettono da qualsiasi percorso, è gestito da server ADFS e da proxy distribuiti come macchine virtuali di Azure.
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a>Integrazione di Lync con Exchange e SharePoint in Office 365

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a>Lync Server con Exchange Online e SharePoint Online

Nel diagramma di accompagnamento viene mostrato Office 365 con Exchange Online e SharePoint Online connesso a una farm Lync Server 2013 locale.
  
I vantaggi di questa distribuzione consentono di:
  
- Utilizzare il set di funzionalità completo di Lync Server 2013.
    
- Sfruttare le apparecchiature telefoniche locali esistenti, ad esempio i sistemi PBX.
    
- Utilizzo di Exchange Online per la posta elettronica, disattivazione del carico dei server di posta elettronica locali e dell'archiviazione.
    
- Utilizzo di SharePoint Online per la collaborazione, disattivazione del carico di manutenzione dei server di SharePoint locali.
    
- Utilizzare le funzionalità integrate di Lync, Exchange e SharePoint, inclusa la messaggistica unificata (UM) in Office 365.
    
#### <a name="exchange-server-with-lync-online"></a>Server Exchange con Lync Online

Il diagramma di accompagnamento Visualizza Office 365 con Lync Online connesso a una farm di Exchange Server locale.
  
I vantaggi di questa distribuzione consentono di:
  
- Sfruttare l'infrastruttura di Exchange esistente.
    
- Utilizzare Lync Online per le funzionalità di presenza, messaggistica istantanea e conferenza.
    

