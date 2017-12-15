---
title: Diagramma accessibile - ripristino di emergenza di SharePoint in Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: "In questo articolo è una versione testo accessibile del diagramma denominata SharePoint il ripristino di emergenza in Microsoft Azure."
ms.openlocfilehash: 2babb1910b0cd8dcbfe4cc0bf32de7c714c05fc0
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a>Diagramma accessibile - ripristino di emergenza di SharePoint in Microsoft Azure

**Riepilogo:** In questo articolo è una versione testo accessibile del diagramma denominata SharePoint il ripristino di emergenza in Microsoft Azure.
  
Questo poster vengono forniti esempi di architetture per la creazione di un ambiente di ripristino di Azure. 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a>Ambiente locale con un ambiente di ripristino di Azure

Il diagramma mostra un esempio di architettura, utilizzata per l'ambiente di produzione di un ambiente locale che utilizza Azure per il ripristino. 
  
### <a name="on-premises-production-environment"></a>Ambiente di produzione in locale

Nella figura relativa viene illustrato un ambiente di produzione con quattro livelli di server in una server farm. 
  
#### <a name="tier-1"></a>Livello 1

Esistono due server per i servizi front-end e di elaborazione delle query. Esiste una partizione di indice che fornisce una replica di entrambi i server. 
  
#### <a name="tier-2"></a>Livello 2

Esistono due server per la cache distribuita in questo livello. 
  
#### <a name="tier-3"></a>Livello 3

Esistono tre server in questo livello. Ogni server fornisce i servizi seguenti: 
  
- Servizi back-end 
    
- Admin 
    
- Gestione flusso di lavoro 
    
- Ricerca per indicizzazione 
    
- Elaborazione del contenuto 
    
- Analisi 
    
#### <a name="tier-4"></a>Livello 4

In questo livello sono disponibili due server. Entrambi i server presenti tre gruppi di disponibilità, come indicato di seguito: 
  
- Gruppo di disponibilità #1 fornisce funzionalità di ricerca. 
    
- Gruppo di disponibilità #2 fornisce contenuto, la configurazione e le applicazioni di servizio. 
    
- Gruppo di disponibilità #3 fornisce contenuto. 
    
È inoltre disponibile un file server in questo livello di condivisione. I server di livello 4 utilizzano la distribuzione dei log per comunicare con tale server. Il server, a sua volta, comunica su Distributed File System replica (che il servizio) a un server di condivisione di file nell'ambiente di Azure ripristino con warm standby, come descritto nella sezione seguente. 
  
### <a name="azure-recovery-environment"></a>Ambiente di ripristino di Azure

#### <a name="warm-standby-environment-running-virtual-machines"></a>Con warm standby ambiente macchine virtuali in esecuzione

La relativa diagramma dell'ambiente locale replicato esattamente nell'ambiente di ripristino Azure. Il server di condivisione di file in questo ambiente è collegato l'ambiente locale e che il servizio. Che il servizio trasferisce registri dall'ambiente di produzione per l'ambiente di ripristino tramite il server di condivisione di file. 
  
### <a name="overview"></a>Panoramica

L'ambiente di ripristino di emergenza per una farm di SharePoint 2013 locali può essere ospitata in Azure. 
  
-  Servizi di infrastruttura Azure offre un centro dati secondario.
    
- Prestare solo per le risorse utilizzate. 
    
- Farm di piccole dimensioni ripristino può essere scalata dopo una situazione di emergenza per soddisfare gli obiettivi di capacità e scalabilità. 
    
La farm di ripristino in Azure è configurata come in modo identico possibile nella farm di produzione in locale. 
  
- Stessa rappresentazione dei ruoli del server. 
    
- Stessa configurazione di personalizzazioni. 
    
- Stessa configurazione delle funzionalità di ricerca (possibile in una versione ridotta di farm di produzione). 
    
La distribuzione dei log e che il servizio vengono utilizzati per copiare i log delle transazioni e dei backup di database alla farm di Azure. 
  
- Che il servizio viene utilizzato per trasferire i registri dall'ambiente di produzione per l'ambiente di ripristino. In uno scenario WAN, che il servizio è più efficiente log direttamente al server secondario in Azure. 
    
- I registri vengono riprodotti nei computer basato su Azure SQL Server. 
    
- Database con log Shipping vengono collegati alla farm finché non viene eseguito un esercizio di ripristino. 
    
Procedure di failover: 
  
1. Arrestare il log shipping 
    
2. Smettere di accettare il traffico alla farm primaria. 
    
3. Riprodurre i registri di transazioni finali. 
    
4. Collegare i database di contenuto alla farm. 
    
5. Avviare una ricerca per indicizzazione completa. 
    
6. Ripristinare le applicazioni di servizio dai database di servizi replicati. 
    
Obiettivi del recupero forniti da questa soluzione includono: 
  
- Siti e contenuto 
    
- Ricerca (nuovamente a ricerca per indicizzazione, nessuna cronologia ricerca) 
    
- Servizi
    
Ulteriori elementi che possono essere risolti da Microsoft Consulting Services o un partner: 
  
- Sincronizzazione di soluzioni farm personalizzate 
    
- Connessioni a origini dati in locale (origine contenuti di integrazione applicativa dei dati (BDC) e ricerca) 
    
- Scenari di ripristino di ricerca 
    
- Gli obiettivi di tempo di ripristino (RTO) e obiettivi del punto di ripristino (RPO) 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a>Ambiente di standby fredda macchine virtuali in esecuzione

Cold standby ambienti richiedono più tempo per avviare ma sono meno costosi. 
  
- Viene creata completamente la farm, ma le macchine virtuali vengono arrestate dopo la creazione della farm. Corrisposto solo i costi di elaborazione per le macchine virtuali sono in esecuzione, ma si applicano i costi di archiviazione e di rete trasferimento di dati. 
    
- In caso di emergenza, tutte le macchine virtuali della farm vengono avviate e un'applicazione di patch. 
    
- Backup e i registri delle transazioni vengono applicati ai database della farm. 
    
Nell'elenco seguente vengono descritte le procedure aggiuntive per con cold standby ambienti: 
  
- Attivare le macchine virtuali regolarmente di patch, aggiornare e verifica dell'ambiente. 
    
- Eseguire le procedure per aggiornare DNS e gli indirizzi IP. 
    
- Configurare SQL AlwaysOn dopo il failover. 
    
Nella figura relativa viene illustrato un ambiente di ripristino replicato nelle macchine virtuali. Dopo il failover in un ambiente con cold standby, tutte le macchine virtuali siano state avviate e configurati i gruppi di disponibilità utilizzando i registri di riesecuzione per rendere disponibili i server di database. 
  
## <a name="sharepoint-recovery-environment-in-azure"></a>Ambiente di ripristino di SharePoint in Azure

Progettare e creare l'ambiente di failover in Azure. 
  
- Creare una rete virtuale in Azure. 
    
- Connettersi alla rete locale con la rete virtuale in Azure con una connessione VPN del sito per sito. La connessione utilizza un gateway dinamico in Azure. 
    
- Distribuire uno o più controller di dominio per la rete virtuale Azure e configurare questi per l'utilizzo con il dominio locale. I controller di dominio sono i server di catalogo. 
    
- Adattare la farm di SharePoint per i set di disponibilità e servizi cloud. 
    
- Distribuire la farm di SharePoint e un file server a condivisioni file host. 
    
- Configurare la distribuzione dei log e che il servizio tra l'ambiente locale e l'ambiente di ripristino basato su Azure. 
    
Figura relativa che mostra l'ambiente locale e la rete virtuale Azure con le caratteristiche seguenti: 
  
### <a name="on-premises-environment"></a>Ambiente locale

- Configurazione di Windows Server 2012 
    
- Server Active Directory 
    
Le interfacce di rete locale con la rete virtuale Azure tramite un gateway di rete privata virtuale (VPN). 
  
### <a name="azure-virtual-network"></a>Rete virtuale Azure

Le interfacce di gateway VPN con una subnet di gateway VPN attiva. 
  
Esistono tre servizi cloud nella rete virtuale Azure: 
  
- Il primo servizio cloud dispone di due Active Directory e dei server DNS con una disponibilità impostato. 
    
- Il servizio cloud secondo presenta tre gruppi di server: due distribuiti i server della cache con un gruppo di disponibilità. Due server front-end con un gruppo di disponibilità. Tre server back-end con un gruppo di disponibilità.
    
- Il terzo servizio cloud con tre server di database con un gruppo di disponibilità. Uno di questi server di database è una condivisione file per nodo log shipping e un terzo di una maggioranza dei nodi per SQL Server AlwaysOn. 
    
### <a name="build-the-ad-ds-hybrid-environment"></a>Creare l'ambiente ibrido di servizi di dominio Active Directory

La configurazione di AD DS per questa soluzione costituisce uno scenario di distribuzione ibrida, in cui è parzialmente distribuiti in locale di dominio Active Directory e parzialmente distribuiti nelle macchine virtuali Azure. 
  
Importante: Prima di distribuire Active Directory in Azure, leggere le linee guida per la distribuzione di Windows Server Active Directory in Microsoft macchine virtuali di Azure (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx). 
  
Per indicazioni dettagliate sulla progettazione e distribuzione di ambienti Active Directory, vedere http://TechNet.microsoft.com. 
  
Questa architettura di riferimento include due macchine virtuali configurate come controller di dominio. È stata configurata come indicato di seguito: 
  
- Dimensioni, ovvero piccola. 
    
- Sistema operativo: Windows Server 2012. 
    
- Ruolo, ovvero i controller di dominio Active Directory designato come server di catalogo globale. Questa configurazione consente di ridurre il traffico in uscita attraverso la connessione VPN. In un ambiente con più domini con modifiche molto frequenti, configurare domain controller locale non sincronizzare con il server di catalogo globale in Azure. 
    
- Dischi dati, posizionare il database di dominio Active Directory, log e SYSVOL su dischi dati Azure. Non collocare questi del disco di sistema operativo o i dischi temporanei forniti da Azure. Questo è importante. 
    
- Ruolo, Installare e configurare Windows DNS nei controller di dominio. 
    
- Indirizzi IP, utilizzare gli indirizzi IP dinamici. È necessario creare una rete virtuale Azure. 
    

