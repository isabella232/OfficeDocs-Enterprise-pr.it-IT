---
title: Scenari cloud ibridi per IaaS di Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: "Riepilogo: Informazioni su architettura ibrida e gli scenari per l'infrastruttura di Microsoft come servizio (IaaS)-basato su cloud offerte in Azure."
ms.openlocfilehash: 441565adae46d50ad1b7139525ff3146c5f88ca3
ms.sourcegitcommit: 82c8fe6393457f0271d1737a09402a420a81c986
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/06/2018
ms.locfileid: "27181037"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a>Scenari cloud ibridi per Azure IaaS

 **Riepilogo:** Acquisire familiarità con l'architettura ibrida e gli scenari per l'infrastruttura di Microsoft come servizio (IaaS)-basato su cloud offerte in Azure.
  
Estendere l'infrastruttura di gestione delle identità e di calcolo locale nel cloud ospitando i carichi di lavoro IT in esecuzione su reti virtuali Azure cross-premise.  
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a>Architettura per scenario ibrido in IaaS di Azure

La figura 1 mostra l'architettura di scenari ibridi Microsoft basati su IaaS in Azure.
  
**Figura 1: Scenari ibridi Microsoft basati su IaaS in Azure**

![Scenari ibridi Microsoft basati su IaaS in Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
Per ogni livello dell'architettura:
  
- App e scenari
    
    In genere, un carico di lavoro IT è un'applicazione a disponibilità elevata multilivello composta da macchine virtuali di Azure.
    
- Identità
    
    Aggiunge server di identità, come i controller di dominio di AD di Windows Server, al set di server in esecuzione sulle reti virtuali di Azure per l'autenticazione locale.
    
- Rete
    
    Usa una connessione VPN da sito a sito su Internet o una connessione ExpressRoute con peer privato in IaaS di Azure.
    
- Locale
    
    Contiene identità server che vengono sincronizzate con il server di identità in Azure. Può inoltre contenere risorse cui possono accedere le macchine virtuali in esecuzione in Azure, ad esempio la risorsa di archiviazione e l’infrastruttura di gestione dei sistemi.
    
## <a name="directory-synchronization-server-for-office-365"></a>Server di sincronizzazione delle directory per Office 365

Esegue il server di sincronizzazione della directory da un VNet Azure, come illustrato nella figura 2 è un esempio di estensione di un'infrastruttura di elaborazione e identità per il cloud.
  
**Figura 2: Server di sincronizzazione di Directory per Office 365 in Azure IaaS**

![Server di sincronizzazione delle directory per Office 365 in Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
Nella figura 2, una rete locale ospita un'infrastruttura di Windows Server Active Directory, con un server proxy e un router in corrispondenza del bordo. Il router si connette a un gateway Azure in corrispondenza del bordo di un VNet Azure con una connessione VPN o ExpressRoute sito per sito. All'interno di VNet, un server di sincronizzazione della directory esegue Connetti Azure Active Directory.
  
Un server di sincronizzazione della directory per Office 365 consente di sincronizzare l'elenco di account in Windows Server Active Directory con il tenant di Azure Active Directory di una sottoscrizione a Office 365.
  
Un server di sincronizzazione delle directory è un server basato su Windows che esegue Connetti Azure Active Directory. Per il provisioning di più veloci o per ridurre il numero di server locali all'interno dell'organizzazione, distribuire il server di sincronizzazione della directory in una rete virtuale (VNet) in Azure IaaS.
  
Il server di sincronizzazione della directory esegue il polling Windows Server Active Directory per le modifiche e quindi si sincronizza con la sottoscrizione a Office 365.
  
Per ulteriori informazioni, vedere [Distribuzione di Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).
  
## <a name="line-of-business-lob-application"></a>Applicazione LOB (line-of-business)

La figura 3 mostra la configurazione di un'applicazione LOB basata su server in esecuzione su IaaS di Azure.
  
**Figura 3: Applicazione LOB in IaaS di Azure**

![Applicazione line-of-business basata su server in Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
Nella figura 3, una rete locale ospita un'infrastruttura di identità e utenti. È collegato a un gateway IaaS di Azure con una connessione VPN da sito a sito o ExpressRoute. IaaS di Azure ospita una rete virtuale contenente i server dell'applicazione LOB.
  
È possibile creare applicazioni LOB in esecuzione su macchine virtuali di Azure, che risiedono nelle subnet di una rete virtuale di Azure all'interno di un datacenter di Azure (noto anche come posizione).  



  
Dato che essenzialmente si sta estendendo l'infrastruttura locale ad Azure, è necessario assegnare uno spazio di indirizzi privato unico alle reti virtuali e aggiornare le tabelle di routing locali per garantire l'accessibilità a ogni rete virtuale.
  
Una volta stabilita la connessione, queste macchine virtuali possono essere gestite con connessioni desktop remoto o con un software di gestione dei sistemi, proprio come i server locali.
  
Configurando le porte pubbliche, queste macchine virtuali sono accessibili anche da Internet per utenti remoti o mobili.
  
Per una configurazione di prova, vedere [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).
  
Attributi di applicazioni LOB ospitate su macchine virtuali di Azure:
  
- Più livelli
    
    Applicazioni LOB tipiche utilizzano un approccio graduale. I set di server forniscono identità, elaborazione di database, elaborazione logica e applicazioni, server Web front-end per l'accesso di dipendenti o clienti.  
    
- Disponibilità elevata
    
    Applicazioni LOB tipiche forniscono disponibilità elevata utilizzando più server in ogni livello. IaaS di Azure fornisce un contratto di servizio di operatività del 99,9% per i server in set di disponibilità di Azure.  
    
- Distribuzione del carico
    
    Per distribuire il carico del traffico di rete tra i server di un livello, è possibile usare un bilanciamento del carico di Azure interno o con connessione Internet. In alternativa, usare un'applicazione di bilanciamento del carico dedicata disponibile in Azure Marketplace.
    
- Sicurezza
    
    Per proteggere i server dal traffico in ingresso provenienti da Internet, è possibile utilizzare gruppi di sicurezza di rete Azure. Puoi definire di concedere o negare il traffico verso una subnet o l'interfaccia di rete di una singola macchina virtuale.
    
## <a name="sharepoint-server-2016-farm-in-azure"></a>Farm di SharePoint Server 2016 in Azure

Un esempio di applicazione LOB altamente disponibile di più livelli in Azure è una farm di SharePoint Server 2016, come illustrato nella figura 4.
  
**Figura 4: Una farm di SharePoint Server 2016 a disponibilità elevata in IaaS di Azure**

![Una farm di SharePoint Server 2016 a disponibilità elevata in IaaS di Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
Nella figura 4, una rete locale ospita un'infrastruttura di identità e utenti. È collegato a un gateway IaaS di Azure con una connessione VPN da sito a sito o ExpressRoute. La rete virtuale di Azure contiene i server della farm di SharePoint Server 2016, che include livelli separati per server front-end, server di applicazioni, cluster di SQL Server e controller di dominio.
  
Questa configurazione offre i seguenti attributi delle applicazioni LOB in Azure:  
  
- Livelli
    
    Server che eseguono ruoli diversi all'interno della farm creano i livelli e ogni livello ha una propria subnet.

    
- Disponibilità elevata
    
    È ottenuta utilizzando più di un server in ogni livello e tutti i server di un livello di immissione nello stesso set di disponibilità.
    
- Distribuzione del carico
    
    Servizi di bilanciamento del carico Azure interno distribuiscono il traffico web client in arrivo ai server front-end (WEB1 e WEB2) e all'indirizzo IP del listener del cluster SQL Server (SQL1, SQL2 e MN1).
    
- Sicurezza
    
    Gruppi di sicurezza di rete per ogni subnet consentono di configurare il traffico in ingresso e in uscita consentito.
    
Seguire questo percorso per l’adozione:
  
1. Valutare e sperimentare
    
    Vedere [2016 di SharePoint Server in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) per acquisire familiarità con i vantaggi dell'esecuzione di SharePoint Server 2016 in Azure.
    
    Vedere [Intranet SharePoint Server 2016 nell'ambiente di sviluppo e di testing Azure](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) per creare un ambiente di sviluppo e di testing simulate
    
2. Struttura
    
    Vedere [Progettazione di una farm di SharePoint Server 2016 in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) per eseguire un processo per determinare il set di rete Azure IaaS, compute ed elementi di archiviazione per ospitare la farm e le relative impostazioni.
    
3. Distribuzione
    
    Vedere [distribuzione di SharePoint Server 2016 con SQL Server AlwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) per eseguire la configurazione end-to-end della farm di disponibilità elevata in cinque fasi.
    
## <a name="federated-identity-for-office-365-in-azure"></a>Identità federata per Office 365 in Azure

Un altro esempio di un'applicazione LOB a più livelli e altamente disponibile in Azure è identità federata per Office 365.
  
**Figura 5: Un'infrastruttura di identità federata di disponibilità elevata per Office 365 in Azure IaaS**

![Una disponibilità elevata Office 365 federati l'infrastruttura di autenticazione in Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
Nella figura 5, una rete locale ospita un'infrastruttura di identità e degli utenti. Si connette a un gateway Azure IaaS con una connessione VPN o ExpressRoute sito per sito. VNet Azure contiene il server proxy web, server di Active Directory Federation Services (ADFS) e i controller di dominio Windows Server Active Directory (AD).
  
Questa configurazione offre i seguenti attributi delle applicazioni LOB in Azure: 
  
- **Livelli:** Sono disponibili i livelli per server proxy web, server AD FS e controller di dominio di Windows Server Active Directory.
    
- **Distribuzione del carico:** Un servizio di bilanciamento del carico esterno Azure distribuisce le richieste di autenticazione client in ingresso per il proxy web e un servizio di bilanciamento del carico interno Azure distribuisce le richieste di autenticazione per i server ADFS.
    
Seguire questo percorso per l’adozione:
  
1. Valutare e sperimentare
    
    [Identità federata per l'ambiente di sviluppo e di testing di Office 365](federated-identity-for-your-office-365-dev-test-environment.md) per creare un ambiente di sviluppo e di testing simulato per l'autenticazione federata con Office 365, vedere.
    
2. Distribuzione
    
    Vedere [l'autenticazione federata distribuire la disponibilità elevata per Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) per eseguire la configurazione end-to-end della disponibilità elevata dell'infrastruttura ADFS in cinque fasi.
    
    
## <a name="see-also"></a>Vedere anche

[Cloud ibrido Microsoft per Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)


