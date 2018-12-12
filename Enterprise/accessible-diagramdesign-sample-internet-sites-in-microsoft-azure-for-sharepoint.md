---
title: Accessibile diagramma - esempio di progettazione siti Internet in Microsoft Azure per SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: 'In questo articolo è una versione testo accessibile del diagramma denominata esempio di progettazione: siti Internet in Microsoft Azure per SharePoint 2013.'
ms.openlocfilehash: 0d42a96f80d47b360084557fea47c4155d106d30
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
ms.locfileid: "17502759"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Diagramma accessibile - esempio di progettazione: siti Internet in Microsoft Azure per SharePoint 2013

**Riepilogo:** In questo articolo è una versione testo accessibile del diagramma denominata esempio di progettazione: siti Internet in Microsoft Azure per SharePoint 2013.
  
Utilizzare questo esempio di progettazione come punto di partenza per un sito Internet in Azure con SharePoint 2013.
  
Questo poster viene illustrato un esempio di come progettare gli aspetti seguenti di SharePoint 2013:
  
- Utenti
    
- Aree e autenticazione
    
- Server farm
    
- Sito di amministrazione
    
- Servizi
    
- Pool di applicazioni e le applicazioni web
    
- Raccolte siti
    
- Siti
    
- Database del contenuto
    
- Aree e URL
    
## <a name="users-zones-and-authentication"></a>Utenti, aree e autenticazione

Sono disponibili quattro tipi di account utente in questa struttura. Ogni tipo di account è associata a un sito per l'accesso e con un'area a cui viene utilizzato un tipo di autenticazione specifico. 
  
- I clienti anonimi, ovvero i clienti anonimi hanno accesso a un sito, ad esempio http://www.contoso.com. È l'area che utilizzano il "area Internet / anonimi", che utilizza l'autenticazione anonima.
    
- Autenticati clienti, ovvero con i clienti hanno accesso a un sito, ad esempio https://secure.contoso.com. È l'area che utilizzano il "area Extranet / SAML", che utilizza Azure Active Directory con autenticazione SAML.
    
- Gli autori e agli sviluppatori di sito, ovvero gli autori di siti e gli sviluppatori hanno accesso a siti, ad esempio http://authoring.contoso.com:8000 o http://www.contoso.com:8000. È l'area che utilizzano il "area predefinita / integrata di Windows", che utilizza servizi di dominio Active Directory (AD DS).
    
- Account di ricerca per indicizzazione di ricerca, ovvero L'account di ricerca per indicizzazione ricerca dispone dell'accesso a siti, ad esempio http://authoring.contoso.com:8000 o http://www.contoso.com:8000. È l'area viene utilizzato il metodo di "area predefinita / integrata di Windows", che utilizza Active Directory con l'autenticazione NTLM di Windows.
    
## <a name="server-farm"></a>Server farm

Gli utenti di accedere alla server farm tramite Azure. La server farm include uno o più server Web.
  
## <a name="administration-site"></a>Sito di amministrazione

Il sito Amministrazione contiene più server applicazioni, che comunicano con un Pool di applicazioni (Application Pool 1 nell'esempio) che utilizza l'applicazione web del sito Amministrazione centrale. Il sito Amministrazione centrale consente di accedere alle raccolte siti all'interno dell'organizzazione.
  
Il sito Amministrazione contiene anche server Database di SQL Server di database con SQL Server installato e configurato per supportare SQL clustering, mirroring o AlwaysOn (AlwaysOn solo per SQL Server 2012).
  
## <a name="services"></a>Servizi

Nell'esempio di progettazione viene illustrato un sito Web Internet Information Services (IIS), servizi Web di SharePoint. SharePoint Web Services contiene un pool di applicazioni (Application Pool 2) con tre servizi, i profili utente, ricerca e i metadati gestiti.
  
Note sui servizi per i siti Internet:
  
> Metadati gestiti, Assicurarsi di selezionare **l'applicazione di servizio è il percorso predefinito per il set di termini specifici di colonna**.
    
> Gestione di applicazioni, Non è consigliabile utilizzando applicazioni in un sito Internet pubblico in Azure.
    
## <a name="application-pools-and-web-applications"></a>Pool di applicazioni e le applicazioni web

Il gruppo predefinito in Azure Mostra 3 Pool di applicazioni, che include un'applicazione web denominata Contoso siti. Questa raccolta siti basata su percorso si trova in http://internal:8000.
  
## <a name="site-collections-and-sites"></a>Siti e raccolte siti

Sono incluse le raccolte siti contenute nel pool di applicazioni:
  
- Raccolta siti con nome host 1 per la ricerca per indicizzazione (esempio posizione http://authoring.contoso.com:8000)
    
- Raccolta siti con nome host 2 per le query (esempio percorsi http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)
    
- Raccolta siti con nome host 3 per le query (esempio percorsi http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)
    
## <a name="content-databases"></a>Database del contenuto

L'esempio mostra due database del contenuto. Uno è per la raccolta siti 1 per la ricerca per indicizzazione (http://authoring.contoso.com:8000). È l'altro per le raccolte due siti 2 e 3 per le query (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000 o http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).
  
## <a name="zones-and-urls"></a>Aree e URL

L'esempio mostra tre aree con gli URL con bilanciamento del carico associati che vengono utilizzati per gli account utente diverso. 
  
Primo elenco delle aree e URL è correlato alla raccolta siti 1 e vengono fornite le informazioni seguenti:
  
- Utenti - autori dei siti
    
- Area - predefinito
    
- URL con bilanciamento del carico - http://authoring.contoso.com:8000
    
Il secondo elenco delle aree e URL presenta tre diversi tipi di utenti in tre aree diverse. È correlata alla raccolta siti 2 e contiene le informazioni seguenti:
  
Prima area:
  
- Utenti - autori dei siti
    
- Area - predefinito
    
- URL con bilanciamento del carico - http://www.contoso.com:8000
    
Seconda area:
  
- Utenti - clienti anonimi
    
- Area - Internet
    
- -URL con bilanciamento del carico http://www.contoso.com
    
Terzo area:
  
- Utenti - clienti autenticati
    
- Area - Extranet
    
- Bilanciamento del carico URL - https://secure.contoso.com
    
Il terzo elenco delle aree e URL presenta tre diversi tipi di utenti in tre aree diverse. È correlata alla raccolta siti 3 e contiene le informazioni seguenti:
  
Prima area:
  
- Utenti - autori dei siti
    
- Area - Internet
    
- URL con bilanciamento del carico - http://assets.contoso.com:8000
    
Seconda area:
  
- Utenti - clienti anonimi
    
- Area - Internet
    
- Bilanciamento del carico URL - http://assets.contoso.com
    
Terzo area:
  
- Utenti - clienti autenticati
    
- Area - Extranet
    
- Bilanciamento del carico URL - http://secureassets.contoso.com
    

