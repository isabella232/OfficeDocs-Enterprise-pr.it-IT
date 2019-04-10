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
description: "Riepilogo: informazioni sull'architettura ibrida e sugli scenari per le offerte cloud di Microsoft Infrastructure as a Service (IaaS) in Azure."
ms.openlocfilehash: d3f4b4ccbc9dbfa54e6f1d0988624aeb71f27106
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741362"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a>Scenari cloud ibridi per Azure IaaS

 **Riepilogo:** Comprendere l'architettura ibrida e gli scenari per le offerte cloud basate su servizi infrastruttura di Microsoft come servizio (IaaS) in Azure.
  
Estendere l'infrastruttura di gestione delle identità e di calcolo locale nel cloud ospitando i carichi di lavoro IT in esecuzione su reti virtuali Azure cross-premise.  
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a>Architettura per scenario ibrido in IaaS di Azure

La figura 1 mostra l'architettura di scenari ibridi Microsoft basati su IaaS in Azure.
  
**Figura 1: Scenari ibridi Microsoft basati su IaaS in Azure**

![Scenari ibridi basati su Microsoft IaaS in Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
Per ogni livello dell'architettura:
  
- App e scenari
    
    In genere, un carico di lavoro IT è un'applicazione a disponibilità elevata multilivello composta da macchine virtuali di Azure.
    
- Identità
    
    Aggiungere server di identità, ad esempio controller di dominio di servizi di dominio Active Directory, al set di server in esecuzione in Azure reti virtuali per l'autenticazione locale.
    
- Rete
    
    Usa una connessione VPN da sito a sito su Internet o una connessione ExpressRoute con peer privato in IaaS di Azure.
    
- Locale
    
    Contiene identità server che vengono sincronizzate con il server di identità in Azure. Può inoltre contenere risorse cui possono accedere le macchine virtuali in esecuzione in Azure, ad esempio la risorsa di archiviazione e l’infrastruttura di gestione dei sistemi.
    
## <a name="directory-synchronization-server-for-office-365"></a>Server di sincronizzazione della directory per Office 365

L'esecuzione del server di sincronizzazione della directory da una rete virtuale di Azure, come illustrato nella figura 2, è un esempio di estensione dell'infrastruttura di elaborazione e identità al cloud.
  
**Figura 2: server di sincronizzazione della directory per Office 365 in Azure IaaS**

![Server di sincronizzazione della directory per Office 365 in IaaS di Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
Nella figura 2, una rete locale ospita un'infrastruttura di servizi di dominio Active Directory, con un server proxy e un router ai suoi margini. Il router si connette a un gateway di Azure sul bordo di una rete virtuale di Azure con una connessione VPN da sito a sito o ExpressRoute. All'interno di rete virtuale, un server di sincronizzazione della directory esegue Azure AD Connect.
  
Un server di sincronizzazione della directory per Office 365 sincronizza l'elenco degli account in AD DS con il tenant di Azure AD di una sottoscrizione a Office 365.
  
Un server di sincronizzazione della directory è un server basato su Windows che esegue Azure AD Connect. Per il provisioning più rapido o per ridurre il numero di server locali nell'organizzazione, distribuire il server di sincronizzazione della directory in una rete virtuale (rete virtuale) in IaaS di Azure.
  
Il server di sincronizzazione della directory esegue il polling di AD DS per le modifiche e quindi li sincronizza con la sottoscrizione di Office 365.
  
Per ulteriori informazioni, vedere [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).
  
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
    
    Per informazioni sui vantaggi derivanti dall'esecuzione di SharePoint Server 2016 in Azure, vedere [SharePoint server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) .
    
    Vedere [Intranet SharePoint Server 2016 in Azure Dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) per creare un ambiente di sviluppo/test simulato
    
2. Struttura
    
    Vedere [progettazione di una farm di SharePoint Server 2016 in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) per eseguire un processo per determinare il set di elementi di rete, di computo e di archiviazione di IaaS di Azure per ospitare la farm e le relative impostazioni.
    
3. Distribuzione
    
    Vedere [deployIng SharePoint server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) to step through the end-to-end Configuration della farm a disponibilità elevata in cinque fasi.
    
## <a name="federated-identity-for-office-365-in-azure"></a>Identità federata per Office 365 in Azure

Un altro esempio di un'applicazione LOB a più livelli e a disponibilità elevata in Azure è l'identità federata per Office 365.
  
**Figura 5: infrastruttura di identità federata a disponibilità elevata per Office 365 in Azure IaaS**

![Un'infrastruttura di autenticazione federata a disponibilità elevata di Office 365 in Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
Nella figura 5, una rete locale ospita un'infrastruttura di identità e gli utenti. È collegato a un gateway IaaS di Azure con una connessione VPN da sito a sito o ExpressRoute. Rete virtuale di Azure contiene server proxy Web, server Active Directory Federation Services (AD FS) e controller di dominio Active Directory Domain Services (AD DS).
  
Questa configurazione offre i seguenti attributi delle applicazioni LOB in Azure: 
  
- **Livelli:** Esistono livelli per i server proxy Web, per i server AD FS e per i controller di dominio AD DS.
    
- **Distribuzione del carico:** Un bilanciamento del carico di Azure esterno distribuisce le richieste di autenticazione del client in arrivo ai proxy Web e un bilanciamento del carico di Azure interno distribuisce le richieste di autenticazione ai server ADFS.
    
Seguire questo percorso per l’adozione:
  
1. Valutare e sperimentare
    
    Vedere [l'identità federata per l'ambiente di sviluppo/test di office 365](federated-identity-for-your-office-365-dev-test-environment.md) per creare un ambiente di sviluppo/test simulato per l'autenticazione federata con Office 365.
    
2. Distribuzione
    
    Vedere [deploy High Availability Federated Authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) per passare alla configurazione end-to-end dell'infrastruttura ad FS a disponibilità elevata in cinque fasi.
    
    
## <a name="see-also"></a>Vedere anche

[Cloud ibrido Microsoft per Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)


