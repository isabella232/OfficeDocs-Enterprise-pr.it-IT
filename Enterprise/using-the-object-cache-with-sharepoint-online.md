---
title: Utilizzo della cache oggetti con SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: In questo articolo illustra la differenza tra la cache degli oggetti in SharePoint Server 2013 in locale e SharePoint Online.
ms.openlocfilehash: 8aa505645bb5f39c65684412ddebbd2b02baa13f
ms.sourcegitcommit: 7cd210c44622ea2de5fb0e8e91c7be4839c80205
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/20/2018
ms.locfileid: "24056165"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>Utilizzo della cache oggetti con SharePoint Online

In questo articolo illustra la differenza tra la cache degli oggetti in SharePoint Server 2013 in locale e SharePoint Online.
  
Esiste un notevole impatto negativo nell'affidarsi alla cache oggetti nella distribuzione di SharePoint Online. Qualsiasi dipendenza dalla cache oggetti in SharePoint Online riduce l'affidabilità della pagina. 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>Come oggetto funzionamento della cache di SharePoint Online e SharePoint Server 2013

Una volta SharePoint Server 2013 locale ospitati, il cliente può server web front-end privata che ospitano la cache degli oggetti. In questo modo la cache è dedicata a un cliente ed è limitata solo dalla quantità di memoria è disponibile e allocato per la cache degli oggetti. Poiché un solo cliente viene gestito in uno scenario in locale server web front-end in genere che gli utenti le richieste degli stessi siti più volte. Ciò significa che la cache ottiene completa rapidamente e rimane completa degli oggetti di SharePoint in cui gli utenti vengono richiesto a intervalli regolari e i risultati delle query elenco.
  
![Mostra il traffico e il caricamento ai server Web front-end locali](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
Di conseguenza, la seconda volta che un utente visita una pagina, il tempo di caricamento della pagina migliora. Dopo un minimo di quattro caricamenti della stessa pagina, la pagina è memorizzata nella cache su tutti i server Web front-end.
  
Al contrario, in SharePoint Online sono disponibili molte più server, ma anche molti altri siti. Ogni utente può connettersi a un server web front-end diverse che non dispone di cache popolata. O, magari ottenere popolata nella cache per un server, ma l'utente successivo per il server web front-end richiede una pagina a un sito diverso. In alternativa, anche se l'utente successivo richiede la stessa pagina in base alla loro visita precedente, sono con bilanciamento del carico a un server web front-end diverse che non dispone di tale pagina nella relativa cache. In quest'ultimo caso, la memorizzazione nella cache non consentire agli utenti di affatto.
  
Nella figura seguente, ogni punto rappresenta una pagina che richiede un utente e la cache in cui è memorizzato. Colori diversi rappresentano diversi clienti che condividono l'infrastruttura SaaS.
  
![Mostra i risultati di memorizzazione nella cache degli oggetti in SharePoint Online](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
Come si può notare dal diagramma, il rischio di ogni utente da raggiungere un server con la versione memorizzata nella cache della relativa pagina è sottile. Inoltre, a causa di velocità effettiva di grandi dimensioni e dei fatti che i server sono condivise tra molti siti, la cache non ultimi tempo poiché è disponibile solo poco spazio per la memorizzazione nella cache.
  
Per tutti i motivi fin qui citati, basarsi su utenti con oggetti memorizzati nella cache non è un modo efficace per garantire un'esperienza utente e dei tempi di caricamento delle pagine di qualità in SharePoint Online.
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>Se non è possibile fare affidamento sulla cache oggetti per migliorare le prestazioni in SharePoint Online, cosa sarebbe opportuno utilizzare?

Dal momento che non si dovrebbe utilizzare la memorizzazione nella cache in SharePoint Online, occorre prendere in considerazione metodi di progettazione alternativi per le personalizzazioni di SharePoint che utilizzano la cache oggetti. In altri termini, occorre prendere in considerazione l'utilizzo di metodi per problemi relativi alle prestazioni che non si basano sulla memorizzazione di oggetti nella cache per produrre risultati ottimali per gli utenti. Ciò è descritto in alcuni degli ulteriori articoli in questa serie tra cui:
  
- [Opzioni di spostamento per SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Minimizzazione e creazione di bundle in SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Utilizzo delle reti di distribuzione del contenuto](using-content-delivery-networks-with-sharepoint-online.md)
    
- [Ritardo caricamento immagini e JavaScript in SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

