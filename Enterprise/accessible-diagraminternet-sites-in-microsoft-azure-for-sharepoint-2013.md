---
title: Diagramma accessibile - siti Internet in Microsoft Azure per SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
description: In questo articolo è una versione testo accessibile del diagramma denominato siti Internet in Microsoft Azure per SharePoint 2013.
ms.openlocfilehash: 59c84e34ab4d748a80ab0a597817ae4d3464a43c
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
ms.locfileid: "17503049"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Diagramma accessibile - siti Internet in Microsoft Azure per SharePoint 2013

**Riepilogo:** In questo articolo è una versione testo accessibile del diagramma denominato siti Internet in Microsoft Azure per SharePoint 2013.
  
Questo poster descrive e illustra i benefici ai siti Internet pubblico come la flessibilità cloud e Azure Active Directory per gli account dei clienti. Esistono sei diversi scenari che illustrano come siti Internet traggono vantaggio da Azure: 
  
- Progettare e scegliere la topologia della farm. 
    
- Ottimizzare per Azure. 
    
- Scegliere il modello di Active Directory. 
    
- Progettazione della gestione delle identità, aree e autenticazione. 
    
- La progettazione di siti e gli URL per la pubblicazione intersito. 
    
- Progettare l'ambiente Azure. 
    
## <a name="design-and-size-the-farm-topology"></a>Progettare e scegliere la topologia della farm

Utilizzare le informazioni della topologia, capacità e prestazioni per SharePoint 2013 in TechNet per progettare la topologia della farm. 
  
Verificare che la farm che è progettare soddisfi gli obiettivi di capacità e prestazioni. 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a>Esempio: Farm di medie dimensioni siti Internet (~ 85 visualizzazioni pagina al secondo)

Questa farm renderà disponibili una tolleranza SharePoint 2013 farm topologia di ricerca è ottimizzata per un corpo che contiene 3,400,000 elementi. 
  
La farm di esempio di elaborazione dei documenti di 100-200 al secondo, a seconda della lingua e tiene conto 85 visualizzazioni pagina al seconda e 100 query al secondo. 
  
Nella figura relativa viene illustrata una farm di siti internet medie dimensioni con tre tipi di server: 
  
- Server Web 
    
- Server applicazioni 
    
- Server di database 
    
#### <a name="web-servers"></a>Server Web

Nella sezione server web, esistono tre server web, Host A, Host B e c Host. Ogni server web contiene una cache distribuita, profili utente, metadati gestiti e le funzionalità di elaborazione delle query. Contengono anche una replica della partizione di indice in ogni server. 
  
Per implementare la scalabilità, aggiungere un server web aggiuntivi con le stesse funzionalità, permettendo un 28 aggiuntive visualizzazioni di pagine al secondo. 
  
#### <a name="application-servers"></a>Server applicazioni

Nella sezione Server applicazioni, sono disponibili tre server applicazioni, D Host, Host E e Host F. Host G include i componenti di elaborazione della ricerca per indicizzazione, amministrazione, Analitica e contenuto. Host E include i componenti di elaborazione della ricerca per indicizzazione, amministrazione e il contenuto. Host F include i componenti di elaborazione del contenuto e ricerca per indicizzazione. 
  
Per la scalabilità, aggiungere un server applicazioni con un componente di ricerca per indicizzazione e un componente per elaborare un ulteriori documenti 40 al secondo di elaborazione del contenuto. 
  
#### <a name="database-servers"></a>Server di database

Nella sezione server di database, sono disponibili due server, G Host e Host H. I server di database sono negli host accoppiati della tolleranza di errore. 
  
Host G contiene tutti i database di SharePoint, inclusi il database di amministrazione della ricerca, database dei collegamenti, due database di ricerca per indicizzazione, un database Analitica e tutti gli altri database di SharePoint. Host H contiene tutti i database di SharePoint, tra cui le copie ridondanti di tutti i database tramite SQL clustering, mirroring o SQL Server 2012 AlwaysOn. 
  
## <a name="fine-tune-for-azure"></a>Ottimizzare per Azure

Farm di SharePoint potrebbe essere necessario ottimizzato per set di disponibilità nella piattaforma Azure. Per garantire la disponibilità elevata di tutti i componenti, verificare che i ruoli del server siano configurati tutti in modo identico. 
  
Nella topologia di esempio nel diagramma: 
  
- I server web e i server di database vengono configurati in modo identico. 
    
- I server tre applicazioni non sono configurati in modo identico. Questi ruoli del server richiedono ottimizzazione per la disponibilità viene impostata in Azure. 
    
### <a name="before"></a>Before

Nella parte superiore del diagramma mostra la farm di SharePoint prima che è stato ottimizzato per la disponibilità viene impostata in Azure. Nel diagramma, i server applicazioni tre host non sono configurati in modo identico. Il numero di componenti dipende dagli obiettivi di prestazioni e capacità per la farm. I tre server sono configurati come indicato di seguito: 
  
- Server applicazioni host D è configurato con i ruoli di elaborazione della ricerca per indicizzazione, amministrazione, Analitica e contenuto. 
    
- Host E applicazione server viene configurato con i ruoli di elaborazione della ricerca per indicizzazione, amministrazione e il contenuto. 
    
- Server applicazioni host F è configurato con i ruoli di elaborazione del contenuto e ricerca per indicizzazione. 
    
### <a name="after"></a>After

In questa sezione del diagramma è illustrata la farm di SharePoint dopo che è stato ottimizzato per la disponibilità viene impostata in Azure. Per adattare questa architettura per Azure, si verranno replicare i quattro componenti in tutti i tre server. In questo modo aumenta il numero di componenti oltre quanto necessario per le prestazioni e capacità. Lo svantaggio è che questa struttura garantisce la disponibilità elevata di tutti i quattro componenti della piattaforma Azure quando questi tre macchine virtuali vengono assegnate a un set di disponibilità. 
  
Tre server sono configurati per tutti avere i ruoli di elaborazione della ricerca per indicizzazione, amministrazione, Analitica e contenuto. 
  
## <a name="choose-the-active-directory-model"></a>Scegliere il modello di Active Directory

Tutte le soluzioni di SharePoint richiedono servizi di dominio Active Directory Windows (AD DS). In questa fase sono disponibili due opzioni per le soluzioni SharePoint in Azure. 
  
- Opzione 1: Dominio dedicato, è possibile distribuire un dominio dedicato e isolato in Azure per supportare una farm di SharePoint. Si tratta di una buona scelta per siti Internet pubblico. 
    
- Opzione 2: Estendere il dominio locale tramite una connessione VPN da sito. Quando si estende il dominio locale tramite una connessione VPN a siti, gli utenti accedere alla farm di SharePoint come se fosse ospitati in locale. È possibile sfruttare le implementazioni di Active Directory e DNS esistenti. 
    
## <a name="design-for-identity-management-zones-and-authentication"></a>Progettazione della gestione delle identità, aree e autenticazione

### <a name="design-for-accounts-and-authentication"></a>Progettazione per gli account e autenticazione

Determinare la modalità di gestione di account e il tipo di autenticazione utilizzato. 
  
#### <a name="accounts-for-site-developers-and-authors"></a>Account per gli sviluppatori di siti e gli autori

- Aggiungere account al dominio in Azure. 
    
- Utilizzare Active Directory Federation Services (ADFS) locale per attuare la federazione gli account interni al dominio in Azure. 
    
- Se la progettazione include una connessione VPN da sito, utilizzare gli account interni. 
    
#### <a name="accounts-for-customers"></a>Account per i clienti

- Utilizzo di Azure Active Directory. 
    
- Utilizzare un altro provider basata su SAML. 
    
### <a name="design-for-zones"></a>Progettazione delle aree

In SharePoint 2013, la gestione delle identità è inserita nella configurazione delle aree e autenticazione. 
  
Questo tipo di progetto vengono sempre nettamente separato di account cliente da tutti gli altri account. 
  
- Se si desidera che gli account cliente deve essere considerata completamente diverso dall'account interno per gli autori e agli sviluppatori del sito, utilizzare questo tipo di progetto. 
    
- Se si utilizza questo tipo di progetto, è possibile utilizzare i criteri per le aree per limitare le azioni dei clienti in un'applicazione web. 
    
- Questo tipo di progetto di conseguenza URL diversi per conti cliente e interni. 
    
In questo esempio: 
  
- Configurare l'area predefinita per gli account interni. 
    
- Configurare l'area extranet per l'accesso autenticato cliente. Utilizzare Azure Active Directory (AD) per gli account dei clienti, oppure un altro provider basata su SAML. 
    
- Configurare l'area Internet per l'accesso anonimo. 
    
Non utilizzare un progetto di due area in cui tutti gli utenti autenticati sono configurati per utilizzare l'area predefinita. 
  
Il diagramma accompagnamento Mostra una progettazione area tre separazione di interni e gli account dei clienti. 
  
Visitatori e clienti accesso Tenant Azure Active Directory nella farm di SharePoint 2013 attraverso le applicazioni web in una delle due aree. Le due aree includono: 
  
- Area: Internet per utenti anonimi 
    
- Area: Extranet per gli utenti autenticati 
    
Gli utenti con account interno accedere Tenant di Azure Active Directory da servizi di dominio Active Directory e di ADFS nell'ambiente locale tramite il tunnel VPN per Azure Active Directory. L'area predefinita fornisce l'autenticazione di Windows (NTLM). 
  
### <a name="design-for-connecting-to-azure-ad"></a>Progettazione per la connessione a Azure Active Directory

 Azure Active Directory fornisce funzionalità di controllo di accesso e gestione identità per servizi basati su cloud. Funzionalità di includere un archivio basato su cloud per dati di directory e un set di componenti di base dei servizi di identità, tra cui i processi di accesso, servizi di autenticazione e di ADFS. L'identità integrazione dei servizi che sono inclusi con Azure Active Directory con facilità con locale distribuzioni di dominio Active Directory e nome provider di identità di terze parti di supporto.
  
Nella figura relativa viene visualizzato lo scenario seguente: 
  
Per integrare SharePoint 2013 con Azure Active Directory, un servizio di controllo accesso Azure (ACS) duplice: 
  
-  Azure Active Directory utilizza SAML 2.0 e SharePoint funziona solo con SAML 1.1. ACS conosce entrambi i formati e funge da intermediario per trasformare i token formati tra SharePoint e Azure Active Directory.
    
- ACS sostituisce la necessità di identity provider servizio token di sicurezza (STS IP) per questo scenario SAML. 
    
Per ulteriori informazioni, vedere Configure Azure Active Directory con SharePoint 2013 nella libreria TechNet. 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a>La progettazione di siti e gli URL per la pubblicazione intersito

Un'una progettazione dell'applicazione web è consigliata per gli scenari di pubblicazione. 
  
- Modifica di e i siti di pubblicazione sono della stessa applicazione web. 
    
- Pubblicazione intersito viene utilizzata per pubblicare risorse. 
    
Utilizzare raccolte siti basate su percorso e nome host. 
  
- Una raccolta siti radice è un requisito. Creare il sito come siti basati sul percorso. 
    
- Creare tutte le altre raccolte siti come raccolte siti con nome host. 
    
URL del sito radice e applicazione Web 
  
- Utilizzare un nome interno per l'URL dell'applicazione web. SharePoint utilizza il nome del computer locale come nome predefinito se non viene specificato un nome diverso. È possibile utilizzare un nome di dominio è riservato per l'ambiente di rete interna. 
    
- Quando si crea l'applicazione web, SharePoint assegnato un numero di porta non standard. Utilizzare questo numero di porta anziché la porta 80 o 443. Oppure utilizzare un numero di porta diverso, ma non standard. 
    
- Utilizzare lo stesso nome e il numero di porta per la raccolta siti radice, che corrisponde a una raccolta siti basata sul percorso. 
    
Il diagramma accompagnamento Mostra servizi dei pool di applicazioni, ad esempio ricerca interagire con le raccolte siti con le applicazioni web. Le raccolte siti riportate includono: 
  
- Raccolta siti basata su percorso all'http://internal:8000 (sito radice). 
    
- Ricerca per indicizzazione: Raccolte siti con nome Host disponibile all'indirizzo, ad esempio https://authoring.contoso.com:8000. 
    
- Query: 2 raccolte siti con nome basato sull'Host separati si trovano in indirizzi come: 
    
  - http://www.contoso.com 
    
  - https://Secure.contoso.com 
    
  - http://www.contoso.com:8000 
    
  - http://assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - http://assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a>Progettare l'ambiente Azure

Questa architettura di esempio include gli elementi seguenti: 
  
- Una connessione VPN da sito è facoltativa ed estende di Windows locale di dominio Active Directory e dell'ambiente DNS per la rete virtuale in Azure. 
    
- Facoltativamente, utilizzare un dominio dedicato in Azure per supportare la farm di SharePoint. 
    
- I server sono suddivisi in tutti i servizi cloud Azure in base al ruolo. 
    
- Set di disponibilità assicurare una disponibilità elevata dei ruoli del server configurati in modo identico. 
    
Per ulteriori informazioni, vedere l'articolo seguente nel sito TechNet: Azure Architectures for SharePoint Solutions. 
  
Nella figura relativa illustrato un esempio di un ambiente locale connessione con una rete virtuale Azure. 
  
Sono inclusi nell'ambiente locale, ovvero un elemento facoltativo dell'ambiente di Azure, i componenti seguenti: 
  
- Configurazione di Windows Server 2012 
    
- Servizi di dominio Active Directory 
    
- Un gateway VPN da Windows Server e di dominio Active Directory per la subnet attiva Gateway VPN 
    
L'ambiente di rete virtuale Azure include i componenti seguenti: 
  
- Subnet Gateway VPN attivo (la sovrapposizione con l'ambiente locale, se applicabile) 
    
- Servizio cloud che include la disponibilità di dominio Active Directory e DNS impostato (due server) 
    
- Servizio cloud che includono la disponibilità di server front-end impostato (tre SharePoint Server) e la disponibilità del server applicazioni (tre SharePoint Server) 
    
- Imposta cloud Services contenente due la disponibilità del database 
    

