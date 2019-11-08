---
title: Diagramma accessibile-opzioni della piattaforma Microsoft Exchange 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: Questo articolo è una versione di testo accessibile del diagramma denominato opzioni della piattaforma Microsoft Exchange 2013, disponibile nei diagrammi tecnici.
ms.openlocfilehash: ce1fe525b6a339c64d757b82a6f1c9ea4b82d23e
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "38027570"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a>Diagramma accessibile-opzioni della piattaforma Microsoft Exchange 2013

**Riepilogo:** Questo articolo è una versione di testo accessibile del diagramma denominato opzioni della piattaforma Microsoft Exchange 2013, disponibile nei [diagrammi tecnici](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).
  
In questo poster vengono descritti i responsabili decisionali aziendali (BDMs) e gli architetti che devono essere a conoscenza delle distribuzioni di Exchange Online e Exchange Server e include: 
  
- Confronto tra quattro opzioni della piattaforma disponibili per Exchange 2013: Exchange Online (Office 365), Exchange ibrido, Exchange Server locale e Exchange ospitato dal provider. 
    
- Descrizioni di tre funzionalità nuove o aggiornate in Exchange 2013. 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a>Confronto tra quattro distribuzioni diverse per la piattaforma Exchange 2013

Il confronto fornisce informazioni su ogni opzione di distribuzione nelle aree seguenti: 
  
- Panoramica delle diverse funzionalità di distribuzione 
    
- Vantaggi dell'implementazione di ogni opzione di distribuzione 
    
- Requisiti relativi alle licenze 
    
- Attività di architettura necessarie 
    
- Responsabilità per i professionisti IT per l'implementazione di ogni opzione di distribuzione 
    
### <a name="overview"></a>Panoramica

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

Aumentare l'efficienza e ridurre i costi con Office 365.
  
Nel diagramma di accompagnamento viene mostrato Exchange Online con un tenant di Azure Active Directory che sincronizza i nomi e le password degli account tra l'ambiente Servizi di dominio Active Directory locale e il tenant di Azure Active Directory. Active Directory Federation Services (ADFS) è necessario per l'accesso Single Sign-on. 
  
Descrizione delle funzionalità e delle funzionalità:
  
- Il funzionamento dei server e del software server è gestito da Microsoft.
    
- Set di funzionalità RTF di Exchange Server 2013 come servizio basato su cloud.
    
- Sempre aggiornate con le funzionalità più recenti.
    
- Exchange Online Protection (EOP) è incluso per la protezione da posta indesiderata e anti-malware.
    
- Disponibilità elevata integrata con contratto di servizio (SLA, Service Level Agreement) 99,9%.
    
- Sincronizzazione della directory, tra cui le password tra i servizi di dominio Active Directory locale e il tenant di Azure Active Directory. Active Directory Federation Services (ADFS) è necessario per l'accesso Single Sign-on.
    
#### <a name="exchange-hybrid"></a>Ambiente Exchange ibrido

È possibile sfruttare i vantaggi di Office 365 durante la gestione di Exchange Server locale.
  
Nel diagramma di accompagnamento viene mostrato Office 365 con Exchange online in cui alcuni utenti sono ospitati in locale e alcuni utenti sono alloggiati online. Viene inoltre visualizzato un tenant di Azure Active Directory che sincronizza i nomi e le password degli account tra l'ambiente Servizi di dominio Active Directory locale e il tenant di Azure Active Directory.
  
Descrizione delle funzionalità e delle funzionalità:
  
- Alcuni utenti sono ospitati in locale e alcuni utenti sono ospitati online e gli utenti condividono lo stesso spazio di indirizzi di posta elettronica.
    
- Sfrutta l'infrastruttura di Exchange Server esistente.
    
- Eseguire la migrazione da Exchange locale a Exchange Online nel corso del tempo, nella pianificazione.
    
- Integrazione con altre applicazioni di Office 365, tra cui Lync Online e SharePoint Online.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server locale

È possibile progettare e gestire un'infrastruttura di Exchange Server 2013.
  
Il diagramma di accompagnamento Visualizza un'infrastruttura di Exchange Server con un ambiente Servizi di dominio Active Directory (AD DS) locale in cui gli utenti sono ospitati in locale.
  
Descrizione delle funzionalità e delle funzionalità:
  
- Maggiore grado di controllo e personalizzazione per la configurazione.
    
- Nessuna dipendenza dalla gestione dell'affinità di sessione al livello di bilanciamento del carico.
    
- Disponibilità elevata semplice e resilienza del sito mediante i gruppi di disponibilità del database (DAG).
    
- Disponibilità gestita che consente di mantenere un'esperienza utente ottimale.
    
- Sfruttare l'infrastruttura hardware e di archiviazione esistente.
    
#### <a name="provider-hosted-exchange"></a>Exchange ospitato dal provider

È possibile esternalizzare il carico di lavoro del server Exchange a un provider di soluzioni di Exchange Server.
  
Il diagramma di accompagnamento Visualizza un ambiente di Exchange Server gestito e gestito da un provider.
  
Descrizione delle funzionalità e delle funzionalità:
  
- Il funzionamento dei server e del software server viene gestito dal provider.
    
- La pianificazione, il ridimensionamento, la scalabilità e la manutenzione dell'infrastruttura di Exchange Server sono delegati al provider.
    
- La manutenzione del servizio è gestita dal provider.
    
- Il set di funzionalità di Exchange è limitato alla versione software distribuita dal provider.
    
### <a name="benefits-of-implementing-each-deployment-option"></a>Vantaggi dell'implementazione di ogni opzione di distribuzione

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

Questa opzione di distribuzione è la soluzione ideale per:
  
- Organizzazioni che desiderano ridurre i costi delle operazioni per le distribuzioni di Exchange locali.
    
- Organizzazioni che intendono sfruttare altre offerte di Office 365, ad esempio SharePoint Online e Lync Online.
    
#### <a name="exchange-hybrid"></a>Ambiente Exchange ibrido

Questa opzione di distribuzione è la soluzione ideale per:
  
- Facilitare la migrazione da Exchange locale a Exchange Online.
    
- Supporto di siti remoti senza investire nell'infrastruttura di succursale.
    
- Società multinazionali con filiali che richiedono l'installazione di dati in locale.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server locale

Questa opzione di distribuzione è la soluzione ideale per:
  
- Soluzioni altamente personalizzate.
    
- Soluzioni legacy con componenti di terze parti che dipendono da hardware e software che non sono supportati da Exchange Online.
    
- Organizzazioni soggette a normative sulla governance dei dati che richiedono l'installazione di dati in locale.
    
- Organizzazioni che desiderano mantenere il controllo dell'intera piattaforma e della soluzione.
    
#### <a name="provider-hosted-exchange"></a>Exchange ospitato dal provider

Questa opzione di distribuzione è la soluzione ideale per:
  
- Organizzazioni che necessitano di funzionalità di Exchange Server, ma che desiderano esternalizzare la distribuzione e la manutenzione.
    
- Organizzazioni che richiedono opzioni di supporto personalizzate.
    
- Soluzioni personalizzate e integrazione con le applicazioni personalizzate offerte dal provider.
    
- Soluzioni legacy con componenti di terze parti che dipendono da hardware e software che non sono supportati da Exchange Online.
    
### <a name="license-requirements"></a>Requisiti di licenza

Nella tabella seguente vengono illustrati i requisiti di licenza per ogni opzione di distribuzione.
  
|**Opzione di distribuzione**|**Requisiti di licenza**|
|:-----|:-----|
|Exchange Online (Office 365)  <br/> |Modello di sottoscrizione  <br/> |
|Ambiente Exchange ibrido  <br/> | Office 365-modello di sottoscrizione <br/>  On-premises-tutte le licenze locali si applicano (verifica licenze per Exchange Server locale) <br/>  Licenza del server ibrido * <br/> |
|Exchange Server locale  <br/> | Sistema operativo del server <br/>  Licenza del server di Exchange 2013 <br/>  Licenza di accesso client di Exchange 2013 <br/> |
|Exchange ospitato dal provider  <br/> |I costi sono basati sull'accordo con il provider  <br/> |
   
### <a name="architecture-tasks"></a>Attività dell'architettura

In questa sezione sono elencate le attività di architettura per ogni opzione di distribuzione.
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- Pianificare e progettare la sincronizzazione della directory.
    
- Garantire la connettività e la capacità di rete tramite firewall, server proxy, gateway e tra i collegamenti WAN.
    
#### <a name="exchange-hybrid"></a>Ambiente Exchange ibrido

Oltre alle attività dell'architettura sia per gli ambienti Office 365 che per quelli locali:
  
- Decidere se fornire un'esperienza Single Sign-on.
    
- Decidere se instradare la posta Internet in ingresso tramite un'organizzazione locale o tramite Exchange Online Protection.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server locale

- Progettare la topologia di Exchange.
    
- Pianificare la capacità per l'hardware del server.
    
- Progettare la topologia di routing dei messaggi.
    
- Progettare il bilanciamento del carico per i server Accesso client.
    
- Pianificare la disponibilità elevata utilizzando i gruppi di disponibilità del database.
    
#### <a name="provider-hosted-exchange"></a>Exchange ospitato dal provider

Garantire che la capacità e la disponibilità della rete tramite i firewall, i server proxy, i gateway e i collegamenti WAN siano disponibili per il provider.
  
### <a name="it-pro-responsibilities"></a>Responsabilità per i professionisti IT

In questa sezione sono elencate le responsabilità per i professionisti IT per ogni opzione di distribuzione.
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- Implementare il piano di sincronizzazione della directory.
    
- Pianificare e implementare i record DNS interni ed esterni e il routing.
    
- Configurare il server proxy o il firewall per i requisiti di URL e indirizzi IP di Office 365.
    
- Amministrare gli account utente e le impostazioni di Exchange Online.
    
#### <a name="exchange-hybrid"></a>Ambiente Exchange ibrido

Oltre alle responsabilità Pro IT sia per gli ambienti Office 365 che per quelli locali:
  
- Configurare Active Directory Federation Services (AD FS) per Single Sign-on (se lo si desidera).
    
- Configurare i certificati di Exchange per le comunicazioni sicure tra Exchange 2013 Servers e Office 365.
    
- Configurare i record DNS per il percorso di posta Internet in ingresso desiderato.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server locale

- Configurare i certificati necessari per i servizi di Exchange.
    
- Eseguire il provisioning dei server.
    
- Implementare la topologia di routing dei messaggi di Exchange.
    
- Implementare i gruppi di disponibilità del database.
    
- Aggiornare e gestire i server di Exchange.
    
- A seconda dell'utilizzo, aggiungere o rimuovere server in base alle esigenze.
    
#### <a name="provider-hosted-exchange"></a>Exchange ospitato dal provider

Le responsabilità del provider sono le seguenti:
  
- Manutenzione del sistema e del servizio.
    
- Feature graduali.
    
- Protezione dei dati e ripristino di emergenza.
    
Le responsabilità del personale IT nell'organizzazione includono la creazione e la gestione degli account utente.
  
#### <a name="more-information"></a>Altre informazioni

Per ulteriori informazioni su Exchange Online (Office 365), vedere gli argomenti seguenti:
  
- [Descrizione del servizio Exchange Online](https://aka.ms/EXOSD)
    
- [Libreria di Exchange Online su TechNet](https://aka.ms/EXOTN)
    
- [Portale di Exchange Online](https://aka.ms/EXO)
    
Per ulteriori informazioni su Exchange Hybrid, vedere gli argomenti seguenti:
  
- [Distribuzioni ibride di Exchange 2013](https://aka.ms/ExchangeHybrid). È necessario tenere presente che la licenza del server ibrido è necessaria solo per gli scenari seguenti: organizzazione di Exchange 2010 con Exchange 2013 Hybrid server ed Exchange 2007 Organization con Exchange 2013 o Exchange 2010 Hybrid server.
    
- [Accesso a Office 365](https://aka.ms/HybridKey)
    
Per ulteriori informazioni su Exchange Server locale, vedere gli argomenti seguenti:
  
- [Libreria di Exchange Server 2013 su TechNet](https://aka.ms/Ex2013TN)
    
- [Portale di Exchange Server 2013](https://aka.ms/Exchange2013)
    
- [Architettura di Exchange Server 2013](https://aka.ms/Ex2013SP1ArchPoster)
    
Per ulteriori informazioni su Exchange ospitato dal provider, vedere gli argomenti seguenti:
  
[Exchange Server 2013 hosting e soluzioni e linee guida per la multi-locazione](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a>Descrizioni di tre funzionalità nuove o aggiornate in Exchange 2013

### <a name="exchange-online-protection"></a>Exchange Online Protection

Exchange Online Protection (EOP) fornisce protezione da posta indesiderata e antimalware per qualsiasi distribuzione fornendo un livello di funzionalità di protezione distribuite su una rete globale di Data Center. In questo modo è possibile semplificare la gestione degli ambienti di messaggistica. EOP è incluso nelle sottoscrizioni di Exchange Online, ma è possibile utilizzarlo anche per le distribuzioni ibride e locali.
  
Nei diagrammi di accompagnamento vengono illustrate le distribuzioni per Exchange Online, Exchange Hybrid ed Exchange locale che includono il livello EOP nella rete globale.
  
### <a name="exchange-server-deployment-assistant"></a>Assistente per la distribuzione di Exchange Server

L'assistente per la distribuzione di Exchange Server è uno strumento basato sul Web che richiede alcune domande sull'ambiente corrente e quindi genera un elenco di controllo dettagliato personalizzato per facilitare la distribuzione di Exchange Server per diversi tipi di scenari. Se si esegue la migrazione da una versione precedente di Exchange a Exchange 2013, la migrazione a Exchange Online o la pianificazione di un'infrastruttura ibrida, l'assistente per la distribuzione di Exchange Server crea un elenco di controllo di distribuzione personalizzato per lo scenario.
  
Nella schermata di accompagnamento viene visualizzato un elenco di controllo di esempio creato utilizzando l'assistente per la distribuzione di Exchange Server.
  
### <a name="integration-with-lync-and-sharepoint"></a>Integrazione con Lync e SharePoint

Exchange Server 2013 include numerose funzionalità che si integrano con Lync Server 2013 e SharePoint Server 2013. Insieme, questi prodotti offrono una ricca gamma di funzionalità e migliorano la collaborazione all'interno dell'organizzazione. 
  
Un diagramma di accompagnamento Visualizza il poster di autenticazione da server a server e include un collegamento al poster. 
  
- Archiviazione, blocco e eDiscovery
    
- Cassette postali del sito
    
- Archivio contatti unificato
    
- Foto degli utenti ad alta risoluzione
    
- Presenza di Lync in Outlook e Outlook Web App
    
- Autenticazione da server a server
    
- Segreteria telefonica
    
- Registrazioni di riunioni
    
- Sincronizzazione delle attività di Exchange
    
Un diagramma di accompagnamento Visualizza il poster dell'architettura di Exchange Server 2013 SP1 e include un collegamento al poster.
  

