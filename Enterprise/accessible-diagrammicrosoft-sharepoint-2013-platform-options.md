---
title: Diagramma accessibile - opzioni della piattaforma Microsoft SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: "In questo articolo è una versione testo accessibile del diagramma denominato opzioni della piattaforma Microsoft SharePoint 2013."
ms.openlocfilehash: 9cd282cc723376f85fe2cbc5a439ee24fd2ab883
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a>Diagramma accessibile - opzioni della piattaforma Microsoft SharePoint 2013

**Riepilogo:** In questo articolo è una versione testo accessibile del diagramma denominato opzioni della piattaforma Microsoft SharePoint 2013.
  
Quali decisori aziendali (hanno) e i progettisti devono essere a conoscenza di Office 365, Microsoft Azure e le distribuzioni locali. 
  
Questo poster composta da due sezioni: 
  
- Un confronto tra quattro diverse distribuzioni per SharePoint 2013: SharePoint in Office 365, un ambiente ibrido di Office 365 per una distribuzione locale di SharePoint 2013, Azure e una distribuzione locale di SharePoint 2013. 
    
- Descrizione delle tre tipici carichi di lavoro per spostare in Azure. 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a>Confronto tra quattro diverse distribuzioni per la piattaforma di SharePoint 2013

Il confronto vengono fornite informazioni su ogni opzione di distribuzione relative alle aree seguenti: 
  
- Panoramica delle funzionalità di distribuzione diversi 
    
- Che cos'è la soluzione migliore per ogni tipo di distribuzione 
    
- Requisiti relativi alle licenze 
    
- Attività di architettura necessarie per implementare 
    
- IT pro responsabilità per l'implementazione 
    
### <a name="overview"></a>Panoramica

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

Maggiore efficienza e ottimizzare per costo con Office 365 plans multi-tenant. 
  
Nella figura relativa Mostra SharePoint Online con un tenant di Azure Active Directory, che consente di sincronizzare i nomi degli account e password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory. 
  
Descrizione delle funzionalità: 
  
- Software come servizio (SaaS). 
    
- Set di funzionalità avanzate è sempre aggiornati. 
    
- Include un tenant di Azure Active Directory (può essere utilizzato con altre applicazioni). 
    
- Integrazione di directory include la sincronizzazione dei nomi di account e password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory. 
    
- Se il single sign-on (SSO) è un requisito, è possibile implementare Active Directory Federation Services (ADFS). 
    
- Comunicazione client tramite Internet tramite access autenticata e crittografata (porta 443). 
    
- Migrazione dei dati è limitata ai quali possono essere caricate tramite Internet. 
    
- Le personalizzazioni: App per Office, SharePoint e SharePoint Designer 2013. 
    
#### <a name="hybrid-with-office-365"></a>Ibrida con Office 365

Combinare i vantaggi di Office 365 con una distribuzione locale di SharePoint 2013. 
  
Il diagramma accompagnamento Mostra Office 365 con SharePoint Online mediante servizi di integrazione applicativa (BCS) per la connessione a una farm di SharePoint Server 2013 locale. 
  
Scegliere quali delle seguenti funzionalità per l'integrazione: 
  
Ricerca di SharePoint 
  
- Gli utenti possono visualizzare risultati di ricerca di entrambi gli ambienti. 
    
- Gli utenti Extranet in remoto possono accedere con un account di Active Directory locale e utilizzare tutte le funzionalità ibrida disponibile. 
    
Servizi di integrazione applicativa
  
SharePoint Online: Gli utenti possono eseguire lettura e operazioni di scrittura. Il servizio servizi di integrazione Applicativa si connette a una farm di SharePoint Server 2013 locale. Il servizio servizi di integrazione Applicativa configurato sul Broker farm locale la connessione all'endpoint del servizio OData locale. 
  
Duet Enterprise Online 
  
Da SharePoint Online, gli utenti possono eseguire lettura e scrittura operazioni su un sistema SAP locale. 
  
#### <a name="azure"></a>Azure

Trai vantaggio cloud mantenendo il controllo completo della piattaforma e funzionalità. 
  
Il diagramma accompagnamento Mostra Azure contenente due servizi cloud, una farm di SharePoint 2013 e Windows Server Active Directory con DNS connessione agli utenti tramite Internet o per la connessione ad Active Directory locale tramite tunnel VPN. 
  
Caratteristiche includono: 
  
-  Azure è una piattaforma che fornisce i servizi di app e l'infrastruttura necessari per ospitare una farm di SharePoint 2013.
    
- Servizi di infrastruttura. 
    
- Piattaforma cloud nativa migliore per SQL Server e SharePoint. 
    
- Risorse di elaborazione disponibili quasi immediatamente senza alcun obbligo. 
    
- Concentrarsi sulle applicazioni, invece di infrastruttura e centri dati. 
    
- Ambienti di sviluppo e testing economici. 
    
- Soluzioni di SharePoint possono essere accessibile solo da un ambiente aziendale tramite un tunnel VPN per siti o accessibile da Internet. 
    
- Personalizzazioni non sono limitate. 
    
#### <a name="on-premises"></a>In locale

Si è proprietari tutto il contenuto. 
  
Nella figura relativa viene illustrato un ambiente locale con server web, server applicazioni e Active Directory la comunicazione con tutti i database e server applicazioni dedicato per la ricerca. 
  
Caratteristiche includono: 
  
- Pianificazione della capacità e dimensionamento. 
    
- Acquisizione di server e il programma di installazione. 
    
- Distribuzione. 
    
- Scalabilità orizzontale, applicazione di patch e operazioni. 
    
- Backup dei dati. 
    
- Gestione di un ambiente di ripristino di emergenza. 
    
- Personalizzazioni non sono limitate. 
    
### <a name="deployment-type-is-best-for---"></a>Tipo di distribuzione è la soluzione migliore per...

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

- Proteggere la collaborazione e condivisione esterna. (Caratteristica univoco!) 
    
- Intranet, ovvero Siti del Team, siti personali e collaborazione interni. 
    
- Memorizzazione dei documenti e il controllo delle versioni nel cloud. 
    
- Sito Web pubblico Basic. 
    
Funzionalità aggiuntive con piani di sottoscrizione dedicati di Office 365: 
  
- Apparecchiature datacenter Microsoft dedicata all'organizzazione e non condivisa con altre organizzazioni. 
    
- Ogni ambiente dei clienti si trova in una rete fisicamente distinta. 
    
- Comunicazione client tra un cliente di proprietà privata connessione o protetto con IPSec VPN. Autenticazione a due fattori è facoltativa. 
    
- Piani di supporto ITAR che offre. 
    
#### <a name="hybrid-with-office-365"></a>Ibrida con Office 365

- Utilizzo di Office 365 per la condivisione e collaborazione anziché configurare un ambiente extranet esterno. 
    
- Spostare i siti personali (OneDrive for Business) nel cloud per rendere più semplice per gli utenti di accedere in remoto i relativi file. 
    
- Avvio di nuovi siti del team in Office 365. 
    
- Integrare un sito di Office 365 con l'ambiente SharePoint servizi di integrazione Applicativa locale. 
    
#### <a name="azure"></a>Azure

- SharePoint per siti Internet, ovvero pubblica facing siti. Trai vantaggio di Azure Active Directory per gli account dei clienti e l'autenticazione. 
    
- Sviluppo, test e ambienti di gestione temporanea, ovvero rapidamente il provisioning e il deprovisioning degli ambienti intero. 
    
- Applicazioni ibride, ovvero le applicazioni che si estendono su cloud e i Data Center. 
    
- Ambiente di ripristino di emergenza, ripristinare rapidamente da una situazione di emergenza. Prestare solo per l'utilizzo. 
    
- Farm che richiedono sulla creazione di report o controllo. 
    
- Analitica Web. 
    
- Crittografia dei dati statici (dati vengono crittografati nei database di SQL). 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a>Crittografia dei dati statici (dati vengono crittografati nei database di SQL)

- Farm nazionale (quando sono necessario dati che si trovano all'interno di un ufficio). 
    
- Soluzioni di Business Intelligence complesse che devono risiedere chiudere ai dati di Business Intelligence. 
    
- Soluzioni basate su cloud privata. 
    
- Soluzioni fortemente personalizzate. 
    
- Soluzioni legacy con i componenti di terze parti che dipendono da hardware e software che non sono supportati nei servizi infrastruttura di Azure. 
    
- Limitazioni relative alla privacy che impediscono la sincronizzazione degli account di Active Directory con Azure Active Directory (un requisito per Office 365). 
    
- Organizzazioni che preferiscono controllo dell'intera piattaforma e soluzione. 
    
### <a name="license-requirements"></a>Requisiti relativi alle licenze

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

Modello di sottoscrizione. Nessuna licenza aggiuntiva necessaria. 
  
#### <a name="hybrid-with-office-365"></a>Ibrida con Office 365

- Office 365, ovvero Modello di sottoscrizione. Nessuna licenza aggiuntiva necessaria. 
    
- Locale, Si applicano tutte le licenze locali. 
    
#### <a name="azure"></a>Azure

-  Sottoscrizione Azure (include il sistema operativo server)
    
- SQL Server 
    
- Licenza di SharePoint Server 2013 
    
- Licenza di accesso Client di SharePoint 2013 
    
#### <a name="on-premises"></a>In locale

- Sistema operativo del server 
    
- SQL Server 
    
- Licenza di SharePoint Server 2013 
    
- Licenza di accesso Client di SharePoint 2013 
    
### <a name="architecture-tasks"></a>Attività di architettura

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

- Pianificare e progettare integrazione di directory. Due opzioni. Entrambe le opzioni possono essere distribuite in locale o in Azure: sincronizzazione delle Password (è richiesto un server a 64 bit). SSO (richiede AD FS e più server). 
    
- Verificare la capacità di rete e la disponibilità attraverso i firewall, server proxy, gateway e sui collegamenti WAN. 
    
- Ottenere i certificati SSL di terze parti per garantire la sicurezza aziendale per le offerte di servizi di Office 365. 
    
- Il nome del tenant di pianificare e progettare l'architettura della raccolta siti e la governance. 
    
- Pianificare le personalizzazioni, soluzioni e App per SharePoint Online. 
    
- Decidere se si desidera connettersi a Office 365 utilizzando il protocollo Internet 6 (IPv6). Questa non operazione comune. 
    
#### <a name="hybrid-with-office-365"></a>Ibrida con Office 365

Oltre alle attività per gli ambienti di Office 365 e locali: 
  
- Determinare la quantità integrazione delle funzionalità desiderata e scegliere la topologia ibrida. Vedere il poster di modello: quale topologia ibrida utilizzare? 
    
- Se necessario, determinare quali dispositivi server proxy da utilizzare. 
    
#### <a name="azure"></a>Azure

Progettare l'ambiente di rete Azure: 
  
- Rete virtuale interna Azure, comprese le subnet. 
    
- Ambiente di dominio e l'integrazione con i server locali. 
    
- DNS e indirizzi IP. 
    
- Affinità gruppi e gli account di archiviazione. 
    
Progettare l'ambiente di SharePoint in Azure: 
  
- Topologia farm di SharePoint e l'architettura logica. 
    
-  Set di disponibilità Azure e i domini di aggiornamento.
    
- Dimensioni delle macchine virtuali. 
    
- Carico bilanciato endpoint. 
    
- Endpoint esterni di accesso pubblico, se è preferibile. 
    
- Ambiente di ripristino di emergenza. 
    
#### <a name="on-premises"></a>In locale

Progettare l'ambiente di SharePoint in un ambiente locale esistente: 
  
- Topologia farm di SharePoint e l'architettura logica. 
    
- Hardware del server. 
    
- Ambiente virtuale, se utilizzato. 
    
- Il bilanciamento del carico. 
    
- Integrazione con Active Directory e DNS. 
    
- Ambiente di ripristino di emergenza. 
    
### <a name="it-pro-responsibilities"></a>IT pro responsabilità

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

- Verificare le workstation degli utenti soddisfino i prerequisiti del client Office 365. 
    
- Implementare il piano di integrazione di directory. 
    
- Pianificare e implementare i record DNS interni ed esterni e il routing. 
    
- Configurare il firewall per l'indirizzo IP di Office 365 e requisiti per gli URL o il proxy. 
    
- Creare e assegnare le autorizzazioni per le raccolte siti. 
    
- Implementazione di applicazioni, le personalizzazioni e soluzioni per SharePoint Online. 
    
- Monitorare la disponibilità della rete e identificare possibili colli di bottiglia. 
    
#### <a name="hybrid-with-office-365"></a>Ibrida con Office 365

Oltre alle attività per gli ambienti di Office 365 e locali: 
  
- Configurare il dispositivo di server proxy, se necessario. 
    
- Configurare l'infrastruttura di gestione delle identità ibrida: SSO e l'autenticazione da server a server tra due ambienti. 
    
- Configurare l'integrazione delle funzionalità scelte: ricerca, servizi di integrazione Applicativa, Duet Enterprise Online. 
    
#### <a name="azure"></a>Azure

Distribuire e gestire l'ambiente Azure e SharePoint: 
  
- Implementare e gestire l'ambiente di rete di Azure. 
    
- Distribuire l'ambiente SharePoint. 
    
- Aggiornare i server della farm di SharePoint. 
    
- Aggiungere o arrestare macchine virtuali in base alle esigenze basato sull'utilizzo di farm. 
    
- Aumentare o ridurre le dimensioni delle macchine virtuali, in base alle esigenze. 
    
- Eseguire il backup dell'ambiente di SharePoint. 
    
- Implementazione di un ambiente di ripristino di emergenza e il protocollo. 
    
#### <a name="on-premises"></a>In locale

Distribuire e gestire SharePoint dall'ambiente locale: 
  
- Server di provisioning. 
    
- Distribuire l'ambiente SharePoint. 
    
- Aggiornare i server della farm di SharePoint. 
    
- Aggiungere o rimuovere server della farm in base alle esigenze basato sull'utilizzo di farm. 
    
- Eseguire il backup dell'ambiente di SharePoint. 
    
- Implementazione di un ambiente di ripristino di emergenza e il protocollo. 
    
## <a name="three-typical-workloads-to-move-to-azure"></a>Tre tipici carichi di lavoro per spostare in Azure

### <a name="office-365-plus-directory-components-in-azure"></a>Office 365 e componenti della Directory in Azure

Distribuzione di Office 365 componenti di integrazione directory in Azure è più veloce perché è possibile distribuire le macchine virtuali su richiesta. 
  
#### <a name="directory-synchronization-server-only"></a>Solo server di sincronizzazione directory

Invece di distribuire il server di sincronizzazione directory a 64 bit nell'ambiente locale, effettuare il provisioning una macchina virtuale in Azure. 
  
Nella figura relativa Mostra SharePoint Online con un tenant di Azure Active Directory, che consente di sincronizzare i nomi degli account e password tra l'ambiente Active Directory locale e il tenant di Azure Active Directory. 
  
#### <a name="directory-synchronization-plus-ad-fs"></a>La sincronizzazione delle directory oltre AD FS

Questa opzione consente di supportare le identità federata di Office 365 (SSO) senza aggiungere componenti hardware per l'infrastruttura locale. Fornisce inoltre resilienza se non è disponibile nell'ambiente Active Directory locale. 
  
- Componenti di integrazione Directory risiedono in Azure. 
    
- ADFS viene pubblicato su Internet tramite proxy AD FS in Azure. 
    
- Il traffico di autenticazione client, per gli utenti che si connettono da qualsiasi posizione, viene gestito dal server ADFS e i proxy che vengono distribuiti in Azure. 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a>Sito Internet pubblico e Azure Active Directory per l'autenticazione dei clienti

Possibilità di sfruttare la possibilità di scalabilità per richiesta inserendo il sito Internet in Azure. Utilizzare Azure Active Directory per archiviare gli account dei clienti. 
  
#### <a name="azure-advantages-for-internet-sites"></a>Vantaggi Azure per siti Internet

- Prestare solo per le risorse che necessarie quando si aumenta il numero di macchine virtuali in base sull'utilizzo di farm. 
    
- Aggiungere informazioni sui report e analitica web. 
    
- Importanza lo sviluppo di un ottimo sito anziché la creazione di infrastruttura. 
    
#### <a name="azure-ad"></a>Azure AD

Azure Active Directory fornisce funzionalità di controllo di accesso e gestione identità per servizi basati su cloud. Funzionalità di includere un archivio basato su cloud per dati di directory e un set di componenti di base dei servizi di identità, tra cui i processi di accesso, servizi di autenticazione e di ADFS. I servizi di identità inclusi con Azure Active Directory si integrano facilmente con distribuzioni di Active Directory locale e supportano i provider di identità di terze parti. 
  
Figura relativa che mostra la configurazione delle aree e autenticazione è importante per siti Internet. Il diagramma mostra Azure Active Directory Tenant, che contiene una Farm di SharePoint su Azure con due aree: 
  
- Un'area Internet che interagisce con i clienti esterni alla rete e visitatori autenticato e anonimi 
    
- Area predefinita che contiene NTLM per la ricerca per indicizzazione e l'autenticazione di Windows che interagisce con la distribuzione di Active Directory locale su un tunnel VPN. 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a>Farm locale e il ripristino di emergenza in Azure

Scegliere un'opzione di ripristino di emergenza che genera una corrispondenza per i requisiti aziendali. Azure sono disponibili opzioni semplice per le società Guida introduttiva a ripristino di emergenza e opzioni avanzate per le grandi aziende con i requisiti di resilienza elevata. 
  
#### <a name="cold-standby"></a>Data Center con cold standby

- Viene creata completamente la farm, ma le macchine virtuali vengono arrestate. (Estinguere solo quando viene eseguito!) 
    
- Gestione dell'ambiente include le macchine virtuali a partire dal momento in tanto, applicazione di patch, l'aggiornamento e la verifica dell'ambiente. 
    
- Avviare l'ambiente completo in caso di calamità. 
    
#### <a name="warm-standby"></a>Data Center con warm standby

- Sono incluse le farm di piccole dimensioni che è stato eseguito il provisioning e in esecuzione. 
    
- La farm immediatamente può supportare utenti in caso di failover. 
    
- Scalabilità orizzontale della farm rapidamente per servire base utente completa. 
    
#### <a name="hot-standby"></a>Data Center con hot standby

Una farm di dimensioni completamente è stato eseguito il provisioning e in esecuzione in modalità standby. 
  
Di accompagnamento è illustrata una farm locale interazione con l'ambiente di ripristino di emergenza di SharePoint su Azure. Utilizzano i database locale SQL Server Log Shipping sul tunnel VPN per accedere all'ambiente di ripristino di emergenza di SharePoint, che include due server di database SQL che contengono i database di SharePoint, due server Web front-End e due SharePoint Server applicazioni. 
  

