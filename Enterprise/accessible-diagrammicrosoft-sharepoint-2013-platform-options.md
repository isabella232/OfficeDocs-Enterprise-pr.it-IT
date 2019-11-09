---
title: Diagramma accessibile-opzioni della piattaforma Microsoft SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- SPO_Content
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: Questo articolo è una versione di testo accessibile del diagramma denominato opzioni della piattaforma Microsoft SharePoint 2013.
ms.openlocfilehash: aeb17825efa26260422bd1407dfa71920838011d
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "38077549"
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a>Diagramma accessibile-opzioni della piattaforma Microsoft SharePoint 2013

**Riepilogo:** Questo articolo è una versione di testo accessibile del diagramma denominato opzioni della piattaforma Microsoft SharePoint 2013.
  
Quali responsabili decisionali aziendali (BDMs) e gli architetti devono conoscere le distribuzioni di Office 365, Microsoft Azure e locali. 
  
Questo poster contiene due sezioni: 
  
- Confronto tra quattro distribuzioni diverse per SharePoint 2013: SharePoint in Office 365, un ibrido di Office 365 con una distribuzione locale di SharePoint 2013, Azure e una distribuzione locale di SharePoint 2013. 
    
- Descrizione di tre carichi di lavoro tipici da spostare in Azure. 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a>Confronto tra quattro distribuzioni diverse per la piattaforma SharePoint 2013

Il confronto fornisce informazioni su ogni opzione di distribuzione relativa alle aree seguenti: 
  
- Panoramica delle diverse funzionalità di distribuzione 
    
- Cosa è meglio per ogni tipo di distribuzione 
    
- Requisiti di licenza 
    
- Attività dell'architettura necessarie per l'implementazione 
    
- Responsabilità per i professionisti IT per l'implementazione 
    
### <a name="overview"></a>Panoramica

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

Aumentare l'efficienza e ottimizzare i costi con i piani multitenant di Office 365. 
  
Nel diagramma di accompagnamento viene mostrato SharePoint Online con un tenant di Azure Active Directory, che sincronizza i nomi degli account e le password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory. 
  
Descrizione delle caratteristiche: 
  
- Software come servizio (SaaS). 
    
- Il set di funzionalità RTF è sempre aggiornato. 
    
- Include un tenant di Azure Active Directory (può essere utilizzato con altre applicazioni). 
    
- L'integrazione della directory include la sincronizzazione dei nomi degli account e delle password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory. 
    
- Se il servizio Single Sign-on (SSO) è un requisito, è possibile implementare Active Directory Federation Services (AD FS). 
    
- Comunicazione client tramite Internet tramite accesso crittografato e autenticato (porta 443). 
    
- La migrazione dei dati è limitata a ciò che può essere caricato su Internet. 
    
- Personalizzazioni: app per Office, SharePoint e SharePoint Designer 2013. 
    
#### <a name="hybrid-with-office-365"></a>Ibrido con Office 365

Combinare i vantaggi di Office 365 con una distribuzione locale di SharePoint 2013. 
  
Nel diagramma di accompagnamento viene mostrato Office 365 con SharePoint Online con servizi di integrazione applicativa (BCS) per la connessione a una farm di SharePoint Server 2013 locale. 
  
Scegliere le caratteristiche seguenti per l'integrazione: 
  
Ricerca di SharePoint 
  
- Gli utenti possono visualizzare i risultati della ricerca da entrambi gli ambienti. 
    
- Gli utenti Extranet possono accedere in remoto con un account di Active Directory locale e utilizzare tutte le funzionalità ibride disponibili. 
    
BCS
  
Da SharePoint Online: gli utenti possono eseguire entrambe le operazioni di lettura e scrittura. Il servizio BCS si connette a una farm di SharePoint Server 2013 locale. Il servizio BCS configurato nei broker della farm locale la connessione agli endpoint del servizio OData locale. 
  
Duet Enterprise Online 
  
Da SharePoint Online, gli utenti possono eseguire operazioni di lettura e scrittura su un sistema SAP locale. 
  
#### <a name="azure"></a>Azure

Sfruttare il cloud mantenendo il controllo completo della piattaforma e delle funzionalità. 
  
Il diagramma di accompagnamento Visualizza Azure, che contiene due servizi cloud, una farm di SharePoint 2013 e Windows Server Active Directory con DNS che si connette agli utenti tramite Internet o che si connette a Active Directory locale tramite il tunnel VPN. 
  
Le caratteristiche includono: 
  
-  Azure è una piattaforma che fornisce l'infrastruttura e i servizi di app necessari per ospitare una farm di SharePoint 2013.
    
- Servizi infrastrutturali. 
    
- Migliore piattaforma cloud nativa per SQL Server e SharePoint. 
    
- Le risorse di calcolo sono disponibili quasi immediatamente senza impegno. 
    
- Concentrarsi sulle applicazioni anziché sui data center e sull'infrastruttura. 
    
- Ambiente di test e sviluppo poco costoso. 
    
- Le soluzioni di SharePoint possono essere accessibili da Internet o accessibili solo da un ambiente aziendale tramite un tunnel VPN da sito a sito. 
    
- Le personalizzazioni non sono limitate. 
    
#### <a name="on-premises"></a>Locali

Si possiede tutto. 
  
Il diagramma di accompagnamento Visualizza un ambiente locale con server Web, server applicazioni e Active Directory che comunica con tutti i database e i server applicazioni dedicati per la ricerca. 
  
Le caratteristiche includono: 
  
- Pianificazione della capacità e dimensionamento. 
    
- Acquisizione e installazione del server. 
    
- Distribuzione. 
    
- Scalabilità orizzontale, applicazione di patch e operazioni. 
    
- Backup dei dati. 
    
- Gestione di un ambiente di ripristino di emergenza. 
    
- Le personalizzazioni non sono limitate. 
    
### <a name="deployment-type-is-best-for---"></a>Il tipo di distribuzione è consigliabile. . .

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

- Condivisione e collaborazione esterne sicure. (Caratteristica univoca!) 
    
- Intranet: siti di Team, siti personali e collaborazione interna. 
    
- Archiviazione e controllo delle versioni dei documenti nel cloud. 
    
- Sito Web di base pubblico. 
    
Funzionalità aggiuntive con i piani di sottoscrizione dedicati a Office 365: 
  
- Apparecchiature di Microsoft datacenter dedicate all'organizzazione e non condivise con nessun'altra organizzazione. 
    
- Ogni ambiente del cliente risiede in una rete fisicamente separata. 
    
- Comunicazione client su una connessione VPN protetta da IPSec o privata. L'autenticazione a due fattori è facoltativa. 
    
- ITAR-piani di supporto. 
    
#### <a name="hybrid-with-office-365"></a>Ibrido con Office 365

- Utilizzare Office 365 per la condivisione e la collaborazione esterne invece di configurare un ambiente Extranet. 
    
- Spostare i siti personali (OneDrive for business) nel cloud per semplificare l'accesso dei file da parte degli utenti in remoto. 
    
- Avviare nuovi siti del team in Office 365. 
    
- Integrazione di un sito di Office 365 con l'ambiente di SharePoint BCS locale. 
    
#### <a name="azure"></a>Azure

- SharePoint per siti Internet: siti di riorientamento pubblico. Trarre vantaggio da Azure AD per gli account dei clienti e l'autenticazione. 
    
- Ambienti di sviluppo, testing e gestione temporanea: provisioning e deprovisioning rapido di interi ambienti. 
    
- Applicazioni ibride: applicazioni che si estendono al Data Center e al cloud. 
    
- Ambiente di ripristino di emergenza: ripristino rapido da una situazione di emergenza. Paghi solo per l'utilizzo. 
    
- Farm che richiedono rapporti profondi o di controllo. 
    
- Web Analytics. 
    
- Crittografia dei dati a Rest (i dati vengono crittografati nei database SQL). 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a>Crittografia dei dati a Rest (i dati vengono crittografati nei database SQL)

- Farm nazionali (quando i dati devono risiedere all'interno di una giurisdizione). 
    
- Soluzioni di BI complesse che devono risiedere vicino ai dati di BI. 
    
- Soluzioni cloud private. 
    
- Soluzioni altamente personalizzate. 
    
- Soluzioni legacy con componenti di terze parti che dipendono da hardware e software che non sono supportati nei servizi di infrastruttura di Azure. 
    
- Restrizioni sulla privacy che impediscono la sincronizzazione degli account di Active Directory con Azure Active Directory (un requisito per Office 365). 
    
- Organizzazioni che preferiscono il controllo dell'intera piattaforma e della soluzione. 
    
### <a name="license-requirements"></a>Requisiti di licenza

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

Modello di sottoscrizione. Non sono necessarie licenze aggiuntive. 
  
#### <a name="hybrid-with-office-365"></a>Ibrido con Office 365

- Office 365: modello di sottoscrizione. Non sono necessarie licenze aggiuntive. 
    
- Locale: vengono applicate tutte le licenze locali. 
    
#### <a name="azure"></a>Azure

-  Sottoscrizione di Azure (include il sistema operativo del server)
    
- SQL Server 
    
- Licenza del server di SharePoint 2013 
    
- Licenza di accesso client di SharePoint 2013 
    
#### <a name="on-premises"></a>Locali

- Sistema operativo del server 
    
- SQL Server 
    
- Licenza del server di SharePoint 2013 
    
- Licenza di accesso client di SharePoint 2013 
    
### <a name="architecture-tasks"></a>Attività dell'architettura

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

- Pianificare e progettare l'integrazione di directory. Due opzioni. Entrambe le opzioni possono essere distribuite in locale o in Azure: sincronizzazione password (richiede un server a 1 64 bit). SSO (richiede ADFS e più server). 
    
- Garantire la disponibilità e la capacità della rete attraverso i firewall, i server proxy, i gateway e i collegamenti WAN. 
    
- Acquisizione dei certificati SSL di terze parti per fornire la sicurezza aziendale per le offerte di servizi di Office 365. 
    
- Pianificare il nome del tenant e progettare l'architettura e la governance della raccolta siti. 
    
- Pianificare le personalizzazioni, le soluzioni e le app per SharePoint Online. 
    
- Decidere se si desidera connettersi a Office 365 utilizzando il protocollo IPv6 (Internet Protocol 6). Non si tratta di una cosa comune. 
    
#### <a name="hybrid-with-office-365"></a>Ibrido con Office 365

Oltre alle attività sia per gli ambienti Office 365 che per quelli locali: 
  
- Determinare la quantità di integrazione delle caratteristiche desiderata e scegliere la topologia ibrida. Vedere questo poster del modello: quale topologia ibrida utilizzare? 
    
- Se necessario, determinare quale dispositivo server proxy verrà utilizzato. 
    
#### <a name="azure"></a>Azure

Progettare l'ambiente di rete di Azure: 
  
- Rete virtuale all'interno di Azure, incluse le subnet. 
    
- Ambiente di dominio e integrazione con i server locali. 
    
- Indirizzi IP e DNS. 
    
- Gruppi di affinità e account di archiviazione. 
    
Progettare l'ambiente di SharePoint in Azure: 
  
- Topologia della farm di SharePoint e architettura logica. 
    
-  I set di disponibilità di Azure e i domini di aggiornamento.
    
- Dimensioni delle macchine virtuali. 
    
- Endpoint con bilanciamento del carico. 
    
- Endpoint esterni per l'accesso pubblico, se questo è preferibile. 
    
- Ambiente di ripristino di emergenza. 
    
#### <a name="on-premises"></a>Locali

Progettare l'ambiente di SharePoint in un ambiente locale esistente: 
  
- Topologia della farm di SharePoint e architettura logica. 
    
- Hardware del server. 
    
- Ambiente virtuale, se utilizzato. 
    
- Bilanciamento del carico. 
    
- Integrazione con servizi di dominio Active Directory e DNS. 
    
- Ambiente di ripristino di emergenza. 
    
### <a name="it-pro-responsibilities"></a>Responsabilità per i professionisti IT

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

- Garantire che le workstation degli utenti soddisfino i prerequisiti client di Office 365. 
    
- Implementare il piano di integrazione della directory. 
    
- Pianificare e implementare i record DNS interni ed esterni e il routing. 
    
- Configurare il proxy o il firewall per i requisiti di indirizzo IP e URL di Office 365. 
    
- Creare e assegnare autorizzazioni per le raccolte siti. 
    
- Implementare le personalizzazioni, le soluzioni e le app per SharePoint Online. 
    
- Monitorare la disponibilità della rete e identificare i colli di bottiglia possibili. 
    
#### <a name="hybrid-with-office-365"></a>Ibrido con Office 365

Oltre alle attività sia per gli ambienti Office 365 che per quelli locali: 
  
- Configurare il dispositivo server proxy, se necessario. 
    
- Configurare l'infrastruttura di gestione delle identità ibride: SSO e l'autenticazione da server a server tra i due ambienti. 
    
- Configurare l'integrazione delle funzionalità scelte: Search, BCS, Duet Enterprise online. 
    
#### <a name="azure"></a>Azure

Distribuire e gestire l'ambiente di Azure e SharePoint: 
  
- Implementare e gestire l'ambiente di rete di Azure. 
    
- Distribuire l'ambiente di SharePoint. 
    
- Aggiornare i server della farm di SharePoint. 
    
- Aggiungere o arrestare macchine virtuali secondo necessità in base all'utilizzo della farm. 
    
- Aumentare o diminuire le dimensioni delle macchine virtuali, se necessario. 
    
- Eseguire il backup dell'ambiente di SharePoint. 
    
- Implementare l'ambiente di ripristino di emergenza e il protocollo. 
    
#### <a name="on-premises"></a>Locali

Distribuire e gestire l'ambiente SharePoint in locale: 
  
- Server di provisioning. 
    
- Distribuire l'ambiente di SharePoint. 
    
- Aggiornare i server della farm di SharePoint. 
    
- Aggiungere o rimuovere i server della farm in base all'utilizzo della farm. 
    
- Eseguire il backup dell'ambiente di SharePoint. 
    
- Implementare l'ambiente di ripristino di emergenza e il protocollo. 
    
## <a name="three-typical-workloads-to-move-to-azure"></a>Tre carichi di lavoro tipici da spostare in Azure

### <a name="office-365-plus-directory-components-in-azure"></a>Componenti di directory di Office 365 Plus in Azure

La distribuzione di componenti di integrazione della directory di Office 365 in Azure è più veloce perché è in grado di distribuire macchine virtuali su richiesta. 
  
#### <a name="directory-synchronization-server-only"></a>Solo server di sincronizzazione della directory

Invece di distribuire il server di sincronizzazione della directory a 64 bit nell'ambiente locale, eseguire il provisioning di una macchina virtuale in Azure. 
  
Nel diagramma di accompagnamento viene mostrato SharePoint Online con un tenant di Azure Active Directory, che sincronizza i nomi degli account e le password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory. 
  
#### <a name="directory-synchronization-plus-ad-fs"></a>Sincronizzazione della directory e AD FS

Questa opzione consente di supportare le identità federative di Office 365 senza aggiungere hardware all'infrastruttura locale. Inoltre, fornisce resilienza se l'ambiente Active Directory locale non è disponibile. 
  
- I componenti di integrazione della directory risiedono in Azure. 
    
- AD FS viene pubblicato su Internet tramite proxy ADFS in Azure. 
    
- Il traffico di autenticazione del client, per gli utenti che si connettono da qualsiasi percorso, è gestito da server ADFS e da proxy distribuiti in Azure. 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a>Sito Internet pubblico e Azure AD per l'autenticazione dei clienti

Approfitta della possibilità di scalare facilmente la domanda inserendo il sito Internet in Azure. Usare Azure AD per archiviare gli account dei clienti. 
  
#### <a name="azure-advantages-for-internet-sites"></a>Vantaggi di Azure per i siti Internet

- Pagare solo le risorse necessarie per la scalabilità del numero di macchine virtuali in base all'utilizzo della farm. 
    
- Aggiungere rapporti profondi e analisi Web. 
    
- Concentrarsi sullo sviluppo di un sito importante anziché sull'infrastruttura di costruzione. 
    
#### <a name="azure-ad"></a>Azure AD

Azure AD offre funzionalità di gestione delle identità e controllo di accesso per i servizi cloud. Le funzionalità includono un archivio basato sul cloud per i dati di directory e un set di base di servizi di identità, tra cui processi di accesso degli utenti, servizi di autenticazione e AD FS. I servizi Identity inclusi in Azure AD si integrano facilmente con le distribuzioni di Active Directory locali e supportano completamente i provider di identità di terze parti. 
  
Nel diagramma di accompagnamento viene illustrata la configurazione delle aree e dell'autenticazione importanti per i siti con accesso a Internet. Nel diagramma viene visualizzato il tenant di Azure Active Directory, che contiene una farm di SharePoint in Azure con due aree: 
  
- Un'area Internet che interagisce con utenti e visitatori anonimi e autenticati all'esterno della rete 
    
- Un'area predefinita che contiene NTLM per la ricerca per indicizzazione e l'autenticazione di Windows che interagiscono con la distribuzione di Active Directory locale su un tunnel VPN. 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a>Farm locale e ripristino di emergenza in Azure

Scegliere un'opzione di ripristino di emergenza che corrisponda ai requisiti aziendali. In Azure sono disponibili opzioni di ingresso per le aziende per iniziare a usare il ripristino di emergenza e le opzioni avanzate per aziende con requisiti di resilienza elevati. 
  
#### <a name="cold-standby"></a>Standby freddo

- La farm viene creata completamente, ma le macchine virtuali sono arrestate. (Paghi solo quando è in esecuzione!) 
    
- La gestione dell'ambiente include l'avvio delle macchine virtuali di tanto in tanto, l'applicazione di patch, l'aggiornamento e la verifica dell'ambiente. 
    
- Avviare l'ambiente completo in caso di calamità. 
    
#### <a name="warm-standby"></a>Standby caldo

- Include una farm di piccole dimensioni di cui è stato eseguito il provisioning e l'esecuzione. 
    
- La farm può servire immediatamente gli utenti in caso di failover. 
    
- Scalare rapidamente la farm per servire la base di utenti completa. 
    
#### <a name="hot-standby"></a>Standby caldo

Viene effettuato il provisioning e l'esecuzione di una farm di dimensioni complete in modalità standby. 
  
Nel diagramma di accompagnamento viene illustrata una farm locale che interagisce con l'ambiente di ripristino di emergenza di SharePoint in Azure. Nei database locali viene utilizzato il log shipping di SQL Server tramite il tunnel VPN per accedere all'ambiente di ripristino di emergenza di SharePoint, che include due server di database SQL che contengono i database di SharePoint, due server front-end Web e due SharePoint Server applicazioni. 
  

