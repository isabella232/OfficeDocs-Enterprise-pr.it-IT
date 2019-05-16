---
title: Diagramma accessibile-progettare siti Internet di esempio in Microsoft Azure per SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: 'Questo articolo è una versione di testo accessibile del diagramma denominato esempio di progettazione: siti Internet in Microsoft Azure per SharePoint 2013.'
ms.openlocfilehash: 28cf28739c476638b5775d170508001f2a9730ed
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068799"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Diagramma accessibile-esempio di progettazione: siti Internet in Microsoft Azure per SharePoint 2013

**Riepilogo:** Questo articolo è una versione di testo accessibile del diagramma denominato esempio di progettazione: siti Internet in Microsoft Azure per SharePoint 2013.
  
Utilizzare questo esempio di progettazione come punto di partenza per un sito con connessione Internet in Azure con SharePoint 2013.
  
In questo poster viene illustrato un esempio di come progettare i seguenti aspetti di SharePoint 2013:
  
- Utenti
    
- Aree e autenticazione
    
- Server farm
    
- Sito di amministrazione
    
- Servizi
    
- Pool di applicazioni e applicazioni Web
    
- Raccolte siti
    
- Siti
    
- Database del contenuto
    
- Aree e URL
    
## <a name="users-zones-and-authentication"></a>Utenti, aree e autenticazione

In questa struttura sono disponibili quattro tipi di account utente. Ogni tipo di account è associato a un sito per l'accesso e a un'area in cui viene utilizzato un tipo di autenticazione specifico. 
  
- Clienti anonimi: i clienti anonimi dispongono dell'accesso tramite http://www.contoso.comun sito, ad esempio. L'area utilizzata è "Internet zone/Anonymous", che utilizza l'autenticazione anonima.
    
- Clienti autenticati: i clienti autenticati dispongono dell'accesso tramite un sito https://secure.contoso.com, ad esempio. L'area utilizzata è "area Extranet/SAML", che utilizza Azure Active Directory con l'autenticazione SAML.
    
- Autori e sviluppatori di siti: gli autori e gli sviluppatori di siti possono accedere http://authoring.contoso.com:8000 tramite http://www.contoso.com:8000siti quali o. L'area utilizzata è la "zona predefinita/integrata di Windows", che utilizza servizi di dominio Active Directory (AD DS).
    
- Account di ricerca per indicizzazione-l'account di http://authoring.contoso.com:8000 ricerca per indicizzazione ha accesso tramite siti quali o. http://www.contoso.com:8000 L'area utilizzata è l'"area predefinita/integrata di Windows", che utilizza servizi di dominio Active Directory con l'autenticazione NTLM di Windows.
    
## <a name="server-farm"></a>Server farm

Gli utenti accedono alla server farm tramite Azure. La server farm contiene uno o più server Web.
  
## <a name="administration-site"></a>Sito di amministrazione

Il sito di amministrazione contiene diversi server applicazioni, che comunicano con un pool di applicazioni (pool di applicazioni 1 nell'esempio) che utilizza il sito Amministrazione centrale dell'applicazione Web. Il sito Amministrazione centrale consente di accedere alle raccolte siti all'interno dell'organizzazione.
  
Il sito di amministrazione contiene anche server di database SQL, che sono server di database con SQL Server installato e configurato per supportare il clustering SQL, il mirroring o AlwaysOn (AlwaysOn si applica solo a SQL Server 2012).
  
## <a name="services"></a>Servizi

Nell'esempio di progettazione viene visualizzato un sito Web di Internet Information Services (IIS), servizi Web di SharePoint. Servizi Web di SharePoint include un pool di applicazioni (pool di applicazioni 2) con tre servizi, profili utente, ricerca e metadati gestiti.
  
Note sui servizi per i siti Internet:
  
> Metadati gestiti-assicurarsi di selezionare **questa applicazione di servizio è il percorso di archiviazione predefinito per i set di termini specifici della colonna**.
    
> Gestione app: non è consigliabile utilizzare le app in un sito Internet pubblico in Azure.
    
## <a name="application-pools-and-web-applications"></a>Pool di applicazioni e applicazioni Web

Il gruppo predefinito in Azure Visualizza il pool di applicazioni 3, che contiene un'applicazione Web denominata contoso sites. Questa raccolta siti basata su percorso si trova in http://internal:8000.
  
## <a name="site-collections-and-sites"></a>Raccolte e siti del sito

Le raccolte siti incluse nel pool di applicazioni includono:
  
- Raccolta siti con nome host 1 per la ricerca per indicizzazione (percorso di esempiohttp://authoring.contoso.com:8000)
    
- Raccolta siti con nome host 2 per le query (percorsi http://www.contoso.comdi https://secure.contoso.comesempio,http://www.contoso.com:8000)
    
- Raccolta siti con nome host 3 per le query (percorsi http://assets.contoso.comdi https://secureassets.contoso.comesempio,http://assets.contoso.com:8000)
    
## <a name="content-databases"></a>Database del contenuto

Nell'esempio vengono illustrati due database del contenuto. Uno è per la raccolta siti 1 utilizzata per la ricerca perhttp://authoring.contoso.com:8000)indicizzazione (. L'altro è per le due raccolte siti 2 e 3 utilizzate per le queryhttp://www.contoso.com( https://secure.contoso.com, http://www.contoso.com:8000, o http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).
  
## <a name="zones-and-urls"></a>Aree e URL

Nell'esempio vengono visualizzate tre aree con gli URL con bilanciamento del carico associati che vengono utilizzati da diversi account utente. 
  
Il primo elenco di aree e URL è correlato alla raccolta siti 1 e contiene le informazioni seguenti:
  
- Utenti-autori del sito
    
- Area-impostazione predefinita
    
- URL con bilanciamento del caricohttp://authoring.contoso.com:8000
    
Il secondo elenco di aree e URL ha tre diversi tipi di utenti in tre aree diverse. È correlata alla raccolta siti 2 e contiene le informazioni seguenti:
  
Prima area:
  
- Utenti-autori del sito
    
- Area-impostazione predefinita
    
- URL con bilanciamento del caricohttp://www.contoso.com:8000
    
Seconda area:
  
- Utenti-clienti anonimi
    
- Area-Internet
    
- URL con bilanciamento del caricohttp://www.contoso.com
    
Terza area:
  
- Clienti autenticati dagli utenti
    
- Area-Extranet
    
- URL con bilanciamento del caricohttps://secure.contoso.com
    
Il terzo elenco di aree e URL ha tre diversi tipi di utenti in tre aree diverse. È correlata alla raccolta siti 3 e contiene le informazioni seguenti:
  
Prima area:
  
- Utenti-autori del sito
    
- Area-Internet
    
- URL con bilanciamento del caricohttp://assets.contoso.com:8000
    
Seconda area:
  
- Utenti-clienti anonimi
    
- Area-Internet
    
- URL con bilanciamento del caricohttp://assets.contoso.com
    
Terza area:
  
- Clienti autenticati dagli utenti
    
- Area-Extranet
    
- URL con bilanciamento del caricohttp://secureassets.contoso.com
    

