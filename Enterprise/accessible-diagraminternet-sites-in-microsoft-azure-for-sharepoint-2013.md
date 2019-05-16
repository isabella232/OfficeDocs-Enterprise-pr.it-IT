---
title: Diagramma accessibile-siti Internet in Microsoft Azure per SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
description: Questo articolo è una versione di testo accessibile del diagramma denominato siti Internet in Microsoft Azure per SharePoint 2013.
ms.openlocfilehash: 1d18ad73502c7e21c1c0825e3e56e4faac2a4a09
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068642"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Diagramma accessibile-siti Internet in Microsoft Azure per SharePoint 2013

**Riepilogo:** Questo articolo è una versione di testo accessibile del diagramma denominato siti Internet in Microsoft Azure per SharePoint 2013.
  
Questo poster descrive e illustra come i siti Internet con accesso pubblico traggono vantaggio dall'elasticità cloud e da Azure AD per gli account dei clienti. Esistono sei diversi scenari che descrivono come i siti Internet traggono vantaggio da Azure: 
  
- Progettare e ridimensionare la topologia della farm. 
    
- Ottimizzare la precisione per Azure. 
    
- Scegliere il modello di Active Directory. 
    
- Progettazione per la gestione delle identità, le aree e l'autenticazione. 
    
- Progettare siti e URL per la pubblicazione intersito. 
    
- Progettare l'ambiente di Azure. 
    
## <a name="design-and-size-the-farm-topology"></a>Progettare e ridimensionare la topologia della farm

Utilizzare le linee guida per la topologia, la capacità e le prestazioni per SharePoint 2013 su TechNet per progettare la topologia della farm. 
  
Verificare che la farm che si progetta soddisfi gli obiettivi di capacità e prestazioni. 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a>Esempio: farm di siti Internet di medie dimensioni (~ 85 visualizzazioni di pagina al secondo)

Questa farm fornisce una topologia della farm di ricerca di SharePoint 2013 con tolleranza di errore che è ottimizzata per un corpo contenente 3,4 milioni elementi. 
  
La farm di esempio elabora 100-200 documenti al secondo, a seconda della lingua, e ospita 85 visualizzazioni di pagina al secondo e 100 query al secondo. 
  
Nel diagramma di accompagnamento viene illustrata una farm di siti Internet di medie dimensioni con tre tipi di server: 
  
- Server Web 
    
- Server applicazioni 
    
- Server di database 
    
#### <a name="web-servers"></a>Server Web

Nella sezione server Web sono disponibili tre server Web, host A, host B e host C. Ogni server Web contiene una cache distribuita, profili utente, metadati gestiti e funzionalità di elaborazione delle query. Contengono anche una replica di partizione di indice presente in ogni server. 
  
Per eseguire la scalabilità orizzontale, aggiungere un ulteriore server Web con le stesse funzionalità, che consente di ottenere altre 28 visualizzazioni di pagina al secondo. 
  
#### <a name="application-servers"></a>Server applicazioni

Nella sezione Server applicazioni esistono tre server applicazioni, host D, host E e host F. host D contenente i componenti di ricerca per indicizzazione, amministrazione, analisi e elaborazione del contenuto. Host E contiene componenti di ricerca per indicizzazione, amministrazione e elaborazione del contenuto. Host F contiene i componenti di ricerca per indicizzazione e elaborazione del contenuto. 
  
Per eseguire la scalabilità orizzontale, aggiungere un server applicazioni con un componente di ricerca per indicizzazione e un componente di elaborazione del contenuto per elaborare un ulteriore 40 documenti al secondo. 
  
#### <a name="database-servers"></a>Server di database

Nella sezione Server database sono disponibili due server, ovvero host G e host H. I server di database sono inclusi in host associati per la tolleranza di errore. 
  
L'host G contiene tutti i database di SharePoint, inclusi il database di amministrazione della ricerca, il database dei collegamenti, due database per indicizzazione, un database di analisi e tutti i database di SharePoint. Host H contiene tutti i database di SharePoint, incluse le copie ridondanti di tutti i database che utilizzano il clustering SQL, il mirroring o SQL Server 2012 AlwaysOn. 
  
## <a name="fine-tune-for-azure"></a>Ottimizzazione per Azure

Potrebbe essere necessario ottimizzare la farm di SharePoint per i set di disponibilità nella piattaforma di Azure. Per garantire la disponibilità elevata di tutti i componenti, verificare che i ruoli del server siano tutti configurati in modo identico. 
  
Nella topologia di esempio nel diagramma: 
  
- I server Web e i server di database sono configurati in modo identico. 
    
- I tre server applicazioni non sono configurati in modo identico. Questi ruoli del server richiedono l'ottimizzazione per i set di disponibilità in Azure. 
    
### <a name="before"></a>Prima

La parte superiore del diagramma Visualizza la farm di SharePoint prima che sia stata ottimizzata per i set di disponibilità in Azure. Nel diagramma, i tre server applicazioni host non sono configurati in modo identico. Il numero di componenti è determinato dagli obiettivi di prestazioni e capacità per la farm. I tre server sono configurati come indicato di seguito: 
  
- Host D Application Server è configurato con ruoli di ricerca per indicizzazione, amministrazione, analisi e elaborazione del contenuto. 
    
- Host E Application Server è configurato con i ruoli di elaborazione di ricerca per indicizzazione, amministrazione e contenuto. 
    
- Il server applicazioni F host è configurato con i ruoli di ricerca per indicizzazione e elaborazione del contenuto. 
    
### <a name="after"></a>Dopo

Questa parte del diagramma Visualizza la farm di SharePoint dopo che è stata ottimizzata per i set di disponibilità in Azure. Per adattare questa architettura per Azure, è possibile replicare i quattro componenti in tutti e tre i server. Questo aumenta il numero di componenti oltre ciò che è necessario per le prestazioni e la capacità. Il compromesso è che questa struttura garantisce una disponibilità elevata di tutti e quattro i componenti della piattaforma di Azure quando queste tre macchine virtuali vengono assegnate a un set di disponibilità. 
  
I tre server sono configurati per tutti i ruoli di ricerca per indicizzazione, amministrazione, analisi e elaborazione del contenuto. 
  
## <a name="choose-the-active-directory-model"></a>Scegliere il modello di Active Directory

Tutte le soluzioni di SharePoint richiedono Windows Active Directory Domain Services (AD DS). In questo momento, sono disponibili due opzioni per le soluzioni SharePoint in Azure. 
  
- Opzione 1: dominio dedicato-è possibile distribuire un dominio dedicato e isolato in Azure per supportare una farm di SharePoint. Questa è una buona scelta per i siti Internet di pubblico dominio. 
    
- Opzione 2: estendere il dominio locale tramite una connessione VPN da sito a sito. Quando si estende il dominio locale tramite una connessione VPN da sito a sito, gli utenti accedono alla farm di SharePoint come se fossero ospitati in locale. È possibile usufruire delle implementazioni di Active Directory e DNS esistenti. 
    
## <a name="design-for-identity-management-zones-and-authentication"></a>Progettazione per la gestione delle identità, le aree e l'autenticazione

### <a name="design-for-accounts-and-authentication"></a>Progettazione per account e autenticazione

Determinare la modalità di gestione degli account e il tipo di autenticazione da utilizzare. 
  
#### <a name="accounts-for-site-developers-and-authors"></a>Account per sviluppatori e autori di siti

- Aggiungere account al dominio in Azure. 
    
- Utilizzare Active Directory Federation Services (ADFS) in locale per la Federazione degli account interni per il dominio in Azure. 
    
- Se nella struttura è inclusa una connessione VPN da sito a sito, utilizzare gli account interni. 
    
#### <a name="accounts-for-customers"></a>Account per i clienti

- Utilizzare Azure Active Directory. 
    
- Utilizzare un altro provider basato su SAML. 
    
### <a name="design-for-zones"></a>Progettazione per le aree

In SharePoint 2013, la gestione delle identità viene fattorizzata nella configurazione delle aree e dell'autenticazione. 
  
Questa struttura fornisce una chiara separazione degli account dei clienti da tutti gli altri account. 
  
- Utilizzare questa struttura se si desidera che gli account dei clienti vengano trattati completamente diversi dagli account interni per autori e sviluppatori di siti. 
    
- Se si utilizza questa struttura, è possibile utilizzare i criteri di area per limitare le azioni dei clienti all'interno di un'applicazione Web. 
    
- Questa struttura genera URL diversi per gli account dei clienti e gli account interni. 
    
In questo esempio: 
  
- Configurare l'area predefinita per gli account interni. 
    
- Configurare l'area Extranet per l'accesso con autenticazione dei clienti. Utilizzare Azure Active Directory (AD) per gli account dei clienti oppure utilizzare un altro provider basato su SAML. 
    
- Configurare l'area Internet per l'accesso anonimo. 
    
Non utilizzare una struttura a due aree in cui tutti gli utenti autenticati sono configurati per l'utilizzo dell'area predefinita. 
  
Il diagramma di accompagnamento Visualizza una struttura a tre aree con la separazione degli account interni e dei clienti. 
  
I visitatori e i clienti accedono al tenant di Azure AD nella farm di SharePoint 2013 tramite le applicazioni Web in una delle due aree. Tra le due aree sono incluse le seguenti: 
  
- Area: Internet per gli utenti anonimi 
    
- Area: Extranet per gli utenti autenticati 
    
Gli utenti con account interni accedono al tenant di Azure Active Directory da AD DS e AD FS nell'ambiente locale tramite il tunnel VPN ad Azure AD. L'area predefinita fornisce l'autenticazione di Windows (NTLM). 
  
### <a name="design-for-connecting-to-azure-ad"></a>Progettazione per la connessione ad Azure AD

 Azure AD offre funzionalità di gestione delle identità e controllo di accesso per i servizi cloud. Le funzionalità includono un archivio basato sul cloud per i dati di directory e un set di base di servizi di identità, tra cui processi di accesso degli utenti, servizi di autenticazione e AD FS. I servizi Identity inclusi in Azure AD si integrano facilmente con le distribuzioni di servizi di dominio Active Directory locali e supportano completamente i provider di identità di terze parti.
  
Nel diagramma che segue è illustrato lo scenario seguente: 
  
Quando si integra SharePoint 2013 con Azure Active Directory, un servizio di controllo di accesso di Azure serve due scopi: 
  
-  Azure AD utilizza SAML 2,0 e SharePoint funziona solo con SAML 1,1. ACS riconosce entrambi i formati e funge da intermediario per la trasformazione dei formati di token tra SharePoint e Azure AD.
    
- ACS sostituisce la necessità del servizio token di sicurezza del provider di identità per questo scenario SAML. 
    
Per ulteriori informazioni, vedere Configurare Azure AD con SharePoint 2013 nella libreria TechNet. 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a>Progettare siti e URL per la pubblicazione intersito

Per gli scenari di pubblicazione è consigliata una progettazione di un'applicazione Web. 
  
- Entrambi i siti di creazione e modifica sono presenti nella stessa applicazione Web. 
    
- La pubblicazione intersito viene utilizzata per pubblicare le risorse. 
    
Utilizzare le raccolte siti basate su percorso e con nome host. 
  
- Una raccolta siti radice è un requisito. Creare questo sito come sito basato su percorso. 
    
- Creare tutte le altre raccolte siti come raccolte siti con nome host. 
    
URL del sito radice e dell'applicazione Web 
  
- Utilizzare un nome interno per l'URL dell'applicazione Web. SharePoint utilizza il nome del computer locale come nome predefinito, a meno che non venga specificato un nome diverso. È possibile utilizzare un nome di dominio riservato per l'ambiente di rete interno. 
    
- SharePoint assegna un numero di porta non standard quando si crea l'applicazione Web. Utilizzare questo numero di porta anziché la porta 80 o la porta 443. Oppure utilizzare un numero di porta diverso ma non standard. 
    
- Utilizzare lo stesso nome e il numero di porta per la raccolta siti radice, che è una raccolta siti basata su percorso. 
    
Nel diagramma di accompagnamento vengono illustrati i servizi del pool di applicazioni, ad esempio la ricerca che interagisce con le raccolte siti tramite applicazioni Web. Le raccolte siti mostrate includono: 
  
- Raccolta siti basata su percorso disponibile in http://internal:8000 (sito radice). 
    
- Ricerca per indicizzazione: raccolte siti con nome basato sull'host https://authoring.contoso.com:8000situate in un indirizzo, ad esempio. 
    
- Query: 2 raccolte siti con nome host distinte situate in indirizzi quali: 
    
  - http://www.contoso.com 
    
  - https://secure.contoso.com 
    
  - http://www.contoso.com:8000 
    
  - http://assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - http://assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a>Progettare l'ambiente di Azure

In questo esempio di architettura sono inclusi gli elementi seguenti: 
  
- Una connessione VPN da sito a sito è facoltativa e estende l'ambiente Windows AD DS e DNS locale alla rete virtuale in Azure. 
    
- Facoltativamente, utilizzare un dominio dedicato in Azure per supportare la farm di SharePoint. 
    
- I server sono suddivisi tra i servizi cloud di Azure in base al ruolo. 
    
- I set di disponibilità garantiscono un'elevata disponibilità dei ruoli server configurati in modo identico. 
    
Per ulteriori informazioni, vedere il seguente articolo su TechNet: architetture di Azure per le soluzioni di SharePoint. 
  
Nel diagramma di accompagnamento viene illustrato un esempio di un ambiente locale che si connette a una rete virtuale di Azure. 
  
Sono inclusi nell'ambiente locale, che è un elemento facoltativo dell'ambiente di Azure, i componenti seguenti: 
  
- Windows Server 2012 RRAS 
    
- Servizi di dominio Active Directory 
    
- Un gateway VPN da Windows Server e servizi di dominio Active Directory alla subnet del gateway VPN attivo 
    
L'ambiente di rete virtuale di Azure include i componenti seguenti: 
  
- Subnet del gateway VPN attivo (sovrapposto all'ambiente locale, se applicabile) 
    
- Servizio cloud che include servizi di dominio Active Directory e set di disponibilità DNS (due server) 
    
- Servizio cloud che include il set di disponibilità del server front-end (tre SharePoint Server) e il set di disponibilità del server app (tre server di SharePoint) 
    
- Servizio cloud che contiene due set di disponibilità del database 
    

