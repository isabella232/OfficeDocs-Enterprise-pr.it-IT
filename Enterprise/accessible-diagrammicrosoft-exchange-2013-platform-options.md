---
title: Diagramma accessibile - opzioni della piattaforma di Microsoft Exchange 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: "In questo articolo è una versione testo accessibile del diagramma denominato opzioni della piattaforma di Microsoft Exchange 2013, disponibile all'indirizzo Technical Diagrams."
ms.openlocfilehash: e1c4957c9152c5a23008c657d7e2d0d47b5cce0f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a>Diagramma accessibile - opzioni della piattaforma di Microsoft Exchange 2013

**Riepilogo:** In questo articolo è una versione testo accessibile del diagramma denominato opzioni della piattaforma di Microsoft Exchange 2013, disponibile all'indirizzo [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).
  
Questo poster viene descritto cosa decisori aziendali (hanno) e progettisti devono essere a conoscenza le distribuzioni di Exchange Online ed Exchange Server e sono incluse: 
  
- Confronto di quattro opzioni della piattaforma disponibili per Exchange 2013: Exchange Online (Office 365), Exchange Hybrid Server Exchange locale ed Exchange Provider-Hosted. 
    
- Descrizioni di tre le caratteristiche nuove o aggiornate in Exchange 2013. 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a>Confronto tra quattro diverse distribuzioni per la piattaforma Exchange 2013

Il confronto vengono fornite informazioni su ogni opzione di distribuzione nelle aree seguenti: 
  
- Panoramica delle funzionalità di distribuzione diversi 
    
- Vantaggi dell'implementazione di ogni opzione di distribuzione 
    
- Requisiti relativi alle licenze 
    
- Richiesta attività dell'architettura 
    
- Responsabilità di professionisti IT per l'implementazione di ogni opzione di distribuzione 
    
### <a name="overview"></a>Panoramica

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

Maggiore efficienza e ridurre i costi con Office 365.
  
Nella figura relativa Mostra Exchange Online con un tenant di Azure Active Directory che consente di sincronizzare i nomi degli account e password tra l'ambiente di servizi di dominio Active Directory (AD DS) locali e il tenant di Azure Active Directory. Active Directory Federation Services (ADFS) è necessario per single sign-on. 
  
Descrizione delle funzionalità e caratteristiche:
  
- Il funzionamento del server e il software del server viene gestito da Microsoft.
    
- Set di caratteristiche complete di Exchange Server 2013 come un servizio basato su cloud.
    
- Sempre aggiornati con le funzionalità più recente.
    
- Exchange Online Protection (EOP) è incluso per la protezione da posta indesiderata/protezione anti malware.
    
- Disponibilità elevata incorporata con 99,9% Service Level Agreement (SLA).
    
- Sincronizzazione delle directory tra cui le password tra locali Active Directory Domain Services (AD DS) e il tenant di Azure Active Directory. Active Directory Federation Services (ADFS) è necessario per single sign-on.
    
#### <a name="exchange-hybrid"></a>Ibrida di Exchange

È possibile sfruttare i vantaggi di Office 365 durante la gestione di Exchange Server locale.
  
Il diagramma accompagnamento Mostra Office 365 con Exchange Online in cui alcuni utenti sono in locale e alcuni utenti ospitati in linea. Viene inoltre un tenant di Azure Active Directory che consente di sincronizzare i nomi degli account e password tra l'ambiente di servizi di dominio Active Directory (AD DS) locali e il tenant di Azure Active Directory.
  
Descrizione delle funzionalità e caratteristiche:
  
- Alcuni utenti sono ospitati in locale e alcuni utenti ospitati in linea e gli utenti hanno lo stesso spazio degli indirizzi di posta elettronica.
    
- Sfrutta l'infrastruttura di Exchange Server esistente.
    
- Eseguire la migrazione di Exchange locale a Exchange Online nel tempo, al calendario.
    
- Integrazione con altre applicazioni di Office 365, tra cui Lync Online e SharePoint Online.
    
#### <a name="exchange-server-on-premises"></a>Server di Exchange in locale

È possibile progettare e gestire l'infrastruttura Exchange Server 2013.
  
Il diagramma accompagnamento Mostra un'infrastruttura di Exchange Server con un ambiente di servizi di dominio Active Directory (AD DS) locale in cui gli utenti sono in locale.
  
Descrizione delle funzionalità e caratteristiche:
  
- Massimo grado di controllo e la personalizzazione per la configurazione.
    
- Nessuna dipendenza da mantenere l'affinità di sessione a livello di bilanciamento del carico.
    
- Semplice elevata disponibilità e resilienza del sito utilizzando gruppi di disponibilità del database (DAG).
    
- Managed availability che consente di mantenere un ambiente ottimale.
    
- Utilizzare hardware esistente e l'infrastruttura di archiviazione.
    
#### <a name="provider-hosted-exchange"></a>Exchange ospitata dal provider

È possibile affidare il carico di lavoro di Exchange Server a un provider di soluzioni di Exchange Server.
  
Nella figura relativa viene illustrato un ambiente di Exchange Server di gestione e manutenzione per un provider.
  
Descrizione delle funzionalità e caratteristiche:
  
- Il funzionamento del server e il software del server viene gestito dal provider.
    
- Pianificazione, dimensioni, scalabilità e la manutenzione dell'infrastruttura di Exchange Server vengono delegate al provider.
    
- Manutenzione del servizio viene gestita dal provider.
    
- Il set di caratteristiche di Exchange è limitato alla versione software distribuita dal provider.
    
### <a name="benefits-of-implementing-each-deployment-option"></a>Vantaggi dell'implementazione di ogni opzione di distribuzione

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

Questa opzione di distribuzione è la soluzione migliore per:
  
- Le organizzazioni che desiderano ridurre i costi di operazioni locali di Exchange distribuzioni.
    
- Le organizzazioni che prevedono di utilizzare altre offerte di Office 365, ad esempio SharePoint Online e Lync Online.
    
#### <a name="exchange-hybrid"></a>Ibrida di Exchange

Questa opzione di distribuzione è la soluzione migliore per:
  
- Semplificazione di una migrazione di Exchange locale a Exchange Online.
    
- Supporto siti remoti senza investimenti nell'infrastruttura office succursale.
    
- Multinazionali con le filiali che richiedono dati si trovano in locale.
    
#### <a name="exchange-server-on-premises"></a>Server di Exchange in locale

Questa opzione di distribuzione è la soluzione migliore per:
  
- Soluzioni fortemente personalizzate.
    
- Soluzioni legacy con i componenti di terze parti che dipendono da hardware e software che non sono supportate da Exchange Online.
    
- Le organizzazioni oggetto la normativa governance dati che richiedono dati si trovano in locale.
    
- Le organizzazioni che si desiderano mantengono il controllo dell'intera piattaforma e soluzione.
    
#### <a name="provider-hosted-exchange"></a>Exchange ospitata dal provider

Questa opzione di distribuzione è la soluzione migliore per:
  
- Organizzazioni che richiedono funzionalità di Exchange Server, ma si desidera affidare la distribuzione e manutenzione.
    
- Organizzazioni che richiedono opzioni di supporto personalizzate.
    
- Le soluzioni personalizzate e l'integrazione con le applicazioni personalizzate fornito dal provider.
    
- Soluzioni legacy con i componenti di terze parti che dipendono da hardware e software che non sono supportate da Exchange Online.
    
### <a name="license-requirements"></a>Requisiti relativi alle licenze

Nella tabella seguente vengono illustrati i requisiti di licenza per ogni opzione di distribuzione.
  
|**Opzione di distribuzione**|**Requisiti relativi alle licenze**|
|:-----|:-----|
|Exchange Online (Office 365)  <br/> |Modello di sottoscrizione  <br/> |
|Ibrida di Exchange  <br/> | Office 365 - modello di sottoscrizione <br/>  Locale - tutte le licenze locali applicano (esaminare le licenze per gli scambi Server in locale) <br/>  Licenza server ibrido * <br/> |
|Server di Exchange in locale  <br/> | Sistema operativo del server <br/>  Licenza Server di Exchange 2013 <br/>  Licenza di accesso Client di Exchange 2013 <br/> |
|Exchange ospitata dal provider  <br/> |I costi basati sul contratto con il provider  <br/> |
   
### <a name="architecture-tasks"></a>Attività di architettura

In questa sezione sono elencate le attività dell'architettura per ogni opzione di distribuzione.
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- Pianificare e progettare la sincronizzazione della directory.
    
- Verificare che la capacità di rete e la connettività attraverso i firewall, server proxy, gateway e sui collegamenti WAN.
    
#### <a name="exchange-hybrid"></a>Ibrida di Exchange

Oltre alle attività di architettura per gli ambienti di Office 365 e locali:
  
- Decidere se fornire un single sign-sull'esperienza.
    
- Decidere se instradare la posta Internet in ingresso tramite un'organizzazione locale oppure tramite Exchange Online Protection.
    
#### <a name="exchange-server-on-premises"></a>Server di Exchange in locale

- Progettare la topologia di Exchange.
    
- Pianificazione della capacità per l'hardware server.
    
- Progettare la topologia di routing dei messaggi.
    
- Progettare il bilanciamento del carico per il server Accesso Client.
    
- Pianificare la disponibilità elevata utilizzando gruppi di disponibilità del database.
    
#### <a name="provider-hosted-exchange"></a>Exchange ospitata dal provider

Verificare che la capacità di rete e la disponibilità attraverso i firewall, server proxy, gateway e sui collegamenti WAN sono disponibili per il provider.
  
### <a name="it-pro-responsibilities"></a>Responsabilità di professionisti IT

In questa sezione sono elencate le responsabilità per professionisti IT per ogni opzione di distribuzione.
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- Implementare il piano di sincronizzazione della directory.
    
- Pianificare e implementare i record DNS interni ed esterni e il routing.
    
- Configurare il server proxy o del firewall per l'indirizzo IP di Office 365 e requisiti per gli URL.
    
- Amministrare gli account utente e le impostazioni di Exchange Online.
    
#### <a name="exchange-hybrid"></a>Ibrida di Exchange

Oltre alle responsabilità per professionisti IT per gli ambienti di Office 365 e locali:
  
- Configurare Active Directory Federation Services (ADFS) per single sign-in (se necessario).
    
- Configurare i certificati di Exchange per le comunicazioni protette tra i server Exchange 2013 e Office 365.
    
- Configurare i record DNS per il percorso della posta Internet in ingresso.
    
#### <a name="exchange-server-on-premises"></a>Server di Exchange in locale

- Configurare i certificati necessari per i servizi Exchange.
    
- I server di provisioning.
    
- Implementare la topologia di routing dei messaggi di Exchange.
    
- Implementazione di gruppi di disponibilità del database.
    
- Aggiornamento e la gestione di server di Exchange.
    
- A seconda dell'utilizzo, aggiungere o rimuovere i server in base alle esigenze.
    
#### <a name="provider-hosted-exchange"></a>Exchange ospitata dal provider

Responsabilità del provider includono:
  
- Manutenzione del sistema e il servizio.
    
- Caratteristica implementazioni.
    
- Ripristino di emergenza e la protezione dei dati.
    
Responsabilità del personale IT dell'organizzazione include la creazione e gestione degli account utente.
  
#### <a name="more-information"></a>Ulteriori informazioni

Per ulteriori informazioni su Exchange Online (Office 365), vedere gli argomenti seguenti:
  
- [Descrizione servizio Exchange Online](https://aka.ms/EXOSD)
    
- [Documentazione di Exchange Online su TechNet](https://aka.ms/EXOTN)
    
- [Portale di Exchange Online](https://aka.ms/EXO)
    
Per ulteriori informazioni sull'ambiente ibrido di Exchange, vedere gli argomenti seguenti:
  
- [Distribuzioni ibride di Exchange 2013](https://aka.ms/ExchangeHybrid). Si noti che la licenza server ibrido è solo necessario per i seguenti scenari: organizzazione di Exchange 2010 con server ibrido Exchange 2013 e l'organizzazione di Exchange 2007 con server ibridi Exchange 2010 o Exchange 2013.
    
- [Accedi a Office 365](https://aka.ms/HybridKey)
    
Per ulteriori informazioni sui Server Exchange locale, vedere gli argomenti seguenti:
  
- [Documentazione di Exchange Server 2013 in TechNet](https://aka.ms/Ex2013TN)
    
- [Portale di Exchange Server 2013](https://aka.ms/Exchange2013)
    
- [Architettura di Exchange Server 2013](https://aka.ms/Ex2013SP1ArchPoster)
    
Per ulteriori informazioni su Exchange Provider-Hosted, vedere gli argomenti seguenti:
  
[Linee guida e le soluzioni di hosting e multi-tenancy di Exchange Server 2013](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a>Descrizioni di tre le caratteristiche nuove o aggiornate in Exchange 2013

### <a name="exchange-online-protection"></a>Exchange Online Protection

Exchange Online Protection (EOP) è assicurata la protezione da posta indesiderata e antimalware per qualsiasi distribuzione fornendo un livello di funzionalità di protezione che vengono distribuiti in una rete globale di data center. In questo modo è possibile semplificare la gestione dell'ambiente di messaggistica. EOP è incluso in sottoscrizioni a Exchange Online, ma è possibile utilizzare anche per le distribuzioni ibride e locali.
  
I diagrammi di accompagnamento mostrano le distribuzioni di Exchange Online, Exchange Hybrid e di Exchange in locale che include il livello di EOP in rete globale.
  
### <a name="exchange-server-deployment-assistant"></a>Assistente per la distribuzione di Exchange Server

Exchange Server Deployment Assistant è uno strumento basato su web che richiede alcune domande sull'ambiente corrente e quindi genera un elenco di controllo dettagliata personalizzato per facilitare la distribuzione di Exchange Server per diversi tipi di scenario. Se esegue la migrazione da una versione precedente di Exchange a Exchange 2013, eseguire la migrazione a Exchange Online o pianificando l'infrastruttura ibrida, Exchange Server Deployment Assistant consente di creare un elenco di controllo di distribuzione personalizzata per lo scenario.
  
Schermata relativa che mostra un elenco di controllo di esempio creato con Exchange Server Deployment Assistant.
  
### <a name="integration-with-lync-and-sharepoint"></a>Integrazione con Lync e SharePoint

Exchange Server 2013 sono incluse numerose caratteristiche che si integrano con Lync Server 2013 e SharePoint Server 2013. Insieme, questi prodotti offrono una vasta gamma di funzionalità e migliorare la collaborazione all'interno dell'organizzazione. 
  
Un diagramma di accompagnamento vengono visualizzati il poster di autenticazione da Server a Server e include un collegamento al poster. 
  
- L'archiviazione, conservazione ed eDiscovery
    
- Cassette postali del sito
    
- Archivio unico dei contatti
    
- Foto dell'utente ad alta risoluzione
    
- Presenza di Lync in Outlook e Outlook Web App
    
- Autenticazione tra server
    
- Segreteria telefonica
    
- Registrazioni delle riunioni
    
- Sincronizzazione delle attività di Exchange
    
Un diagramma di accompagnamento vengono visualizzati il poster dell'architettura di Exchange Server 2013 SP1 e include un collegamento al poster.
  

