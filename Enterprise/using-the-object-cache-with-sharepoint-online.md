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
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541270"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a><span data-ttu-id="bd1f4-103">Utilizzo della cache oggetti con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bd1f4-103">Using the object cache with SharePoint Online</span></span>

<span data-ttu-id="bd1f4-104">In questo articolo illustra la differenza tra la cache degli oggetti in SharePoint Server 2013 in locale e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bd1f4-104">This article explains the difference between using the object cache in SharePoint Server 2013 on-premises and SharePoint Online.</span></span>
  
<span data-ttu-id="bd1f4-p101">Esiste un notevole impatto negativo nell'affidarsi alla cache oggetti nella distribuzione di SharePoint Online. Qualsiasi dipendenza dalla cache oggetti in SharePoint Online riduce l'affidabilità della pagina.</span><span class="sxs-lookup"><span data-stu-id="bd1f4-p101">There is significant negative impact of relying on the object cache in SharePoint Online deployment. Any dependency on object cache in SharePoint Online will reduce the reliability of your page.</span></span> 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a><span data-ttu-id="bd1f4-107">Come oggetto funzionamento della cache di SharePoint Online e SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="bd1f4-107">How the SharePoint Online and SharePoint Server 2013 object cache works</span></span>

<span data-ttu-id="bd1f4-p102">Una volta SharePoint Server 2013 locale ospitati, il cliente può server web front-end privata che ospitano la cache degli oggetti. In questo modo la cache è dedicata a un cliente ed è limitata solo dalla quantità di memoria è disponibile e allocato per la cache degli oggetti. Poiché un solo cliente viene gestito in uno scenario in locale server web front-end in genere che gli utenti le richieste degli stessi siti più volte. Ciò significa che la cache ottiene completa rapidamente e rimane completa degli oggetti di SharePoint in cui gli utenti vengono richiesto a intervalli regolari e i risultati delle query elenco.</span><span class="sxs-lookup"><span data-stu-id="bd1f4-p102">When SharePoint Server 2013 is hosted on-premises, the customer has private front-end web servers that host the object cache. This means the cache is dedicated to one customer and is only limited by how much memory is available and allocated to the object cache. Because only one customer is served in the on-premises scenario the front-end web servers typically have users making requests to the same sites over and over. This means that the cache gets full quickly and remains full of the list query results and SharePoint objects that your users are requesting on a regular basis.</span></span>
  
![Mostra il traffico e il caricamento ai server Web front-end locali](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
<span data-ttu-id="bd1f4-p103">Di conseguenza, la seconda volta che un utente visita una pagina, il tempo di caricamento della pagina migliora. Dopo un minimo di quattro caricamenti della stessa pagina, la pagina è memorizzata nella cache su tutti i server Web front-end.</span><span class="sxs-lookup"><span data-stu-id="bd1f4-p103">As a result, the second time a user visits a page, the page load time improves. After a minimum of four loads of the same page, the page is cached on all of the front-end web servers.</span></span>
  
<span data-ttu-id="bd1f4-p104">Al contrario, in SharePoint Online sono disponibili molte più server, ma anche molti altri siti. Ogni utente può connettersi a un server web front-end diverse che non dispone di cache popolata. O, magari ottenere popolata nella cache per un server, ma l'utente successivo per il server web front-end richiede una pagina a un sito diverso. In alternativa, anche se l'utente successivo richiede la stessa pagina in base alla loro visita precedente, sono con bilanciamento del carico a un server web front-end diverse che non dispone di tale pagina nella relativa cache. In quest'ultimo caso, la memorizzazione nella cache non consentire agli utenti di affatto.</span><span class="sxs-lookup"><span data-stu-id="bd1f4-p104">In contrast, in SharePoint Online there are many more servers but also many more sites. Each user may connect to a different front-end web server that doesn't have the cache populated. Or, perhaps the cache does get populated for a server, but the the next user to that front-end web server requests a page from a different site. Or, even if the next user requests the same page as on their previous visit, they are load-balanced to a different front-end web server that doesn't have that page in its cache. In this last case, caching doesn't help the users at all.</span></span>
  
<span data-ttu-id="bd1f4-p105">Nella figura seguente, ogni punto rappresenta una pagina che richiede un utente e la cache in cui è memorizzato. Colori diversi rappresentano diversi clienti che condividono l'infrastruttura SaaS.</span><span class="sxs-lookup"><span data-stu-id="bd1f4-p105">In the following figure, each dot represents a page that a user is requesting and where it cached. Different colors represent different customers making shared use of the SaaS infrastructure.</span></span>
  
![Mostra i risultati di memorizzazione nella cache degli oggetti in SharePoint Online](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
<span data-ttu-id="bd1f4-p106">Come si può notare dal diagramma, il rischio di ogni utente da raggiungere un server con la versione memorizzata nella cache della relativa pagina è sottile. Inoltre, a causa di velocità effettiva di grandi dimensioni e dei fatti che i server sono condivise tra molti siti, la cache non ultimi tempo poiché è disponibile solo poco spazio per la memorizzazione nella cache.</span><span class="sxs-lookup"><span data-stu-id="bd1f4-p106">As you can see from the diagram, the chances of any given user hitting a server with the cached version of their page are slim. Also, due to the large throughput and fact that the servers are shared between many sites, the cache doesn't last long since there is only so much space for caching available.</span></span>
  
<span data-ttu-id="bd1f4-125">Per tutti i motivi fin qui citati, basarsi su utenti con oggetti memorizzati nella cache non è un modo efficace per garantire un'esperienza utente e dei tempi di caricamento delle pagine di qualità in SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bd1f4-125">For all of these reasons, relying on users getting cached objects is not an effective way to ensure a quality user experience and page load times in SharePoint Online.</span></span>
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a><span data-ttu-id="bd1f4-126">Se non è possibile fare affidamento sulla cache oggetti per migliorare le prestazioni in SharePoint Online, cosa sarebbe opportuno utilizzare?</span><span class="sxs-lookup"><span data-stu-id="bd1f4-126">If we can't rely on the object cache to improve performance in SharePoint Online, what do we use instead?</span></span>

<span data-ttu-id="bd1f4-p107">Dal momento che non si dovrebbe utilizzare la memorizzazione nella cache in SharePoint Online, occorre prendere in considerazione metodi di progettazione alternativi per le personalizzazioni di SharePoint che utilizzano la cache oggetti. In altri termini, occorre prendere in considerazione l'utilizzo di metodi per problemi relativi alle prestazioni che non si basano sulla memorizzazione di oggetti nella cache per produrre risultati ottimali per gli utenti. Ciò è descritto in alcuni degli ulteriori articoli in questa serie tra cui:</span><span class="sxs-lookup"><span data-stu-id="bd1f4-p107">Since you shouldn't rely on caching in SharePoint Online, you should evaluate alternative design approaches for SharePoint customizations that use the object cache. This means using approaches for performance issues which do not rely on the object caching in order to produce good results for users. This is described in some of the other articles in this series and include:</span></span>
  
- [<span data-ttu-id="bd1f4-130">Opzioni di spostamento per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bd1f4-130">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="bd1f4-131">Minimizzazione e creazione di bundle in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bd1f4-131">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="bd1f4-132">Utilizzo delle reti di distribuzione del contenuto</span><span class="sxs-lookup"><span data-stu-id="bd1f4-132">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="bd1f4-133">Ritardo caricamento immagini e JavaScript in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bd1f4-133">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

