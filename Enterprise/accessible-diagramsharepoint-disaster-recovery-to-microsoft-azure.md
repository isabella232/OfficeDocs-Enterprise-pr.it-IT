---
title: Diagramma accessibile-ripristino di emergenza di SharePoint in Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: Questo articolo è una versione di testo accessibile del diagramma denominato ripristino di emergenza di SharePoint in Microsoft Azure.
ms.openlocfilehash: d7df0f44dd4e7f0cbb8580029991bc9280892afb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068522"
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a>Diagramma accessibile-ripristino di emergenza di SharePoint in Microsoft Azure

**Riepilogo:** Questo articolo è una versione di testo accessibile del diagramma denominato ripristino di emergenza di SharePoint in Microsoft Azure.
  
Questo poster fornisce esempi di architetture per la creazione di un ambiente di ripristino in Azure. 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a>Ambiente locale con un ambiente di ripristino di Azure

Nel diagramma viene illustrato un esempio di architettura utilizzata per l'ambiente di produzione di un ambiente locale che utilizza Azure per il ripristino. 
  
### <a name="on-premises-production-environment"></a>Ambiente di produzione locale

Nel diagramma di accompagnamento viene mostrato un ambiente di produzione in tempo reale con quattro livelli di server in una server farm. 
  
#### <a name="tier-1"></a>Livello 1

Sono disponibili due server per i servizi front-end e per l'elaborazione delle query. È presente una partizione di indice che fornisce una replica di entrambi i server. 
  
#### <a name="tier-2"></a>Livello 2

In questo livello sono disponibili due server per la cache distribuita. 
  
#### <a name="tier-3"></a>Livello 3   

Esistono tre server in questo livello. Ogni server fornisce i servizi seguenti: 
  
- Servizi back-end 
    
- Amministratore 
    
- Gestione flusso di lavoro 
    
- Ricerca per indicizzazione 
    
- Elaborazione del contenuto 
    
- Analisi 
    
#### <a name="tier-4"></a>Tier 4

Esistono due server in questo livello. In entrambi i server sono disponibili tre gruppi di disponibilità, come indicato di seguito: 
  
- Il gruppo di disponibilità #1 fornisce le funzionalità di ricerca. 
    
- Il gruppo di disponibilità #2 fornisce le applicazioni di contenuto, configurazione e di servizio. 
    
- Il gruppo di disponibilità #3 fornisce contenuto. 
    
Esiste anche un server di condivisione file in questo livello. I server Tier 4 utilizzano log shipping per comunicare con il server. Questo server, a sua incirca, comunica tramite la replica del file System distribuito (DFSR) a un server di condivisione file nell'ambiente di ripristino di emergenza con warm standby di Azure, come descritto nella sezione seguente. 
  
### <a name="azure-recovery-environment"></a>Ambiente di ripristino di Azure

#### <a name="warm-standby-environment-running-virtual-machines"></a>Ambiente caldo di standby in esecuzione macchine virtuali

Nel diagramma di accompagnamento viene illustrato l'ambiente locale replicato esattamente nell'ambiente di ripristino di Azure. Il server di condivisione file in questo ambiente è collegato all'ambiente locale tramite DFSR. DFSR trasferisce i registri dall'ambiente di produzione all'ambiente di ripristino tramite il server di condivisione file. 
  
### <a name="overview"></a>Panoramica

L'ambiente di ripristino di emergenza per una farm di SharePoint 2013 locale può essere ospitato in Azure. 
  
-  Servizi di infrastruttura di Azure fornisce un datacenter secondario.
    
- Paghi solo per le risorse che utilizzi. 
    
- È possibile eseguire la scalabilità delle farm di ripristino di piccole dimensioni dopo una catastrofe per raggiungere gli obiettivi di scalabilità e capacità. 
    
La farm di ripristino in Azure è configurata nel modo più identico possibile alla farm di produzione locale. 
  
- Stessa rappresentazione dei ruoli del server. 
    
- Stessa configurazione delle personalizzazioni. 
    
- Stessa configurazione delle funzionalità di ricerca (possono trovarsi in una versione ridotta della farm di produzione). 
    
I log shipping e DFSR vengono utilizzati per copiare i backup di database e i registri delle transazioni nella farm di Azure. 
  
- DFSR viene utilizzato per trasferire i log dall'ambiente di produzione all'ambiente di ripristino. In uno scenario WAN, Replica DFS è più efficiente della spedizione diretta dei registri al server secondario in Azure. 
    
- I registri vengono riprodotti nei computer SQL Server basati su Azure. 
    
- I database di log shipping non vengono associati alla farm fino a quando non viene eseguito un esercizio di ripristino. 
    
Procedure di failover: 
  
1. Arrestare il log shipping 
    
2. Smettere di accettare il traffico alla farm primaria. 
    
3. Riprodurre i registri di transazioni finali. 
    
4. Collegare i database di contenuto alla farm. 
    
5. Avviare una ricerca per indicizzazione completa. 
    
6. Ripristinare le applicazioni di servizio dai database di servizi replicati. 
    
Gli obiettivi di ripristino forniti da questa soluzione includono: 
  
- Siti e contenuto 
    
- Ricerca (sottoposto a ricerca per indicizzazione, nessuna cronologia ricerche) 
    
- Servizi
    
Elementi aggiuntivi che possono essere indirizzati da Microsoft Consulting Services o da un partner: 
  
- Sincronizzazione di soluzioni farm personalizzate 
    
- Connessioni a origini dati in locale (integrazione applicativa dei dati (BDC) e fonti di contenuto di ricerca) 
    
- Scenari di ripristino di ricerca 
    
- Obiettivi per il tempo di ripristino (RTO) e gli obiettivi del punto di ripristino (RPO) 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a>Ambiente di standby freddo in esecuzione macchine virtuali

Gli ambienti Cold standby richiedono più tempo per iniziare ma sono meno costosi. 
  
- La farm è completamente compilata, ma le macchine virtuali vengono arrestate dopo la creazione della farm. Si pagano solo i costi di elaborazione quando le macchine virtuali sono in esecuzione, ma vengono applicati i costi di archiviazione e trasferimento dei dati di rete. 
    
- In caso di emergenza, tutte le macchine virtuali della farm vengono avviate e patchate. 
    
- I backup e i registri delle transazioni vengono applicati ai database della farm. 
    
Nell'elenco seguente vengono descritte le procedure aggiuntive per gli ambienti Cold standby: 
  
- Abilitare regolarmente le macchine virtuali per la patch, l'aggiornamento e la verifica dell'ambiente. 
    
- Eseguire le procedure per aggiornare DNS e gli indirizzi IP. 
    
- Configurare SQL AlwaysOn dopo un failover. 
    
Il diagramma di accompagnamento Visualizza un ambiente di ripristino replicato nelle macchine virtuali. Dopo il failover in un ambiente di standby freddo, vengono avviate tutte le macchine virtuali e i gruppi di disponibilità vengono configurati utilizzando i registri di riesecuzione per rendere disponibili i server di database. 
  
## <a name="sharepoint-recovery-environment-in-azure"></a>Ambiente di ripristino di SharePoint in Azure

Progettare e creare l'ambiente di failover in Azure. 
  
- Creare una rete virtuale in Azure. 
    
- Connettere la rete locale alla rete virtuale in Azure con una connessione VPN da sito a sito. Questa connessione utilizza un gateway dinamico in Azure. 
    
- Distribuire uno o più controller di dominio nella rete virtuale di Azure e configurarli in modo che funzionino con il dominio locale. Questi controller di dominio sono server di catalogo. 
    
- Adattare la farm di SharePoint per i set di disponibilità e servizi cloud. 
    
- Distribuire la farm di SharePoint e un file server per ospitare le condivisioni di file. 
    
- Configurare il log shipping e DFSR tra l'ambiente locale e l'ambiente di ripristino basato su Azure. 
    
Nel diagramma di accompagnamento viene illustrato l'ambiente locale e la rete virtuale di Azure con le caratteristiche seguenti: 
  
### <a name="on-premises-environment"></a>Ambiente locale

- Windows Server 2012 RRAS 
    
- Server Active Directory 
    
Le interfacce di rete locali con la rete virtuale di Azure su un gateway VPN (Virtual Private Network). 
  
### <a name="azure-virtual-network"></a>Rete virtuale di Azure

Il gateway VPN si interfaccia con una subnet del gateway VPN attiva. 
  
Nella rete virtuale di Azure sono disponibili tre servizi cloud: 
  
- Il primo servizio cloud dispone di due server Active Directory e DNS con un set di disponibilità. 
    
- Nel secondo servizio cloud sono disponibili tre gruppi di server: due server di cache distribuita con un set di disponibilità. Due server front-end con un set di disponibilità. Tre server back-end con un set di disponibilità.
    
- Il terzo servizio cloud dispone di tre server di database con un set di disponibilità. Uno di questi server di database è una condivisione file per il log shipping e un terzo nodo di una maggioranza dei nodi per SQL Server AlwaysOn. 
    
### <a name="build-the-ad-ds-hybrid-environment"></a>Creare l'ambiente ibrido di servizi di dominio Active Directory

La configurazione di servizi di dominio Active Directory per questa soluzione costituisce uno scenario di distribuzione ibrida in cui AD DS è in parte distribuito in locale e in parte distribuito in macchine virtuali di Azure. 
  
Importante: prima di distribuire servizi di dominio Active Directory in Azure, vedere linee guida per la distribuzione di Windows Server attivo nellehttp://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx)macchine virtuali di Microsoft Azure (. 
  
Per istruzioni complete sulla progettazione e la distribuzione di ambienti Active Directory http://TechNet.microsoft.com, vedere. 
  
Questa architettura di riferimento include due macchine virtuali configurate come controller di dominio. Ognuna è configurata come indicato di seguito: 
  
- Dimensioni: piccolo. 
    
- Sistema operativo-Windows Server 2012. 
    
- Role-controller di dominio AD DS designato come server di catalogo globale. Questa configurazione riduce il traffico in uscita attraverso la connessione VPN. In un ambiente con più domini con alti tassi di modifica, configurare i controller di dominio locali in modo che non vengano sincronizzati con i server di catalogo globale in Azure. 
    
- Dischi di dati: posizionare il database di servizi di dominio Active Directory, i registri e SYSVOL nei dischi di dati di Azure. Non posizionarli sul disco del sistema operativo o sui dischi temporanei forniti da Azure. Questo è importante. 
    
- Ruolo: installazione e configurazione di Windows DNS sui controller di dominio. 
    
- Indirizzi IP: utilizzare indirizzi IP dinamici. In questo modo è necessario creare una rete virtuale di Azure. 
    

