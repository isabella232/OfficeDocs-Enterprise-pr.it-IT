---
title: Utilizzo di Web Part ricerca contenuto invece di Web Part Query contenuto per migliorare le prestazioni di SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: In questo articolo viene descritto come migliorare le prestazioni, sostituendo la Web Part Query contenuto con Web Part ricerca contenuto in SharePoint Server 2013 e SharePoint Online.
ms.openlocfilehash: f86a4b75c4bf75ebaa99924411d017c7eb7b6760
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541435"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>Utilizzo di Web Part ricerca contenuto invece di Web Part Query contenuto per migliorare le prestazioni di SharePoint Online

In questo articolo viene descritto come migliorare le prestazioni, sostituendo la Web Part Query contenuto con Web Part ricerca contenuto in SharePoint Server 2013 e SharePoint Online.
  
Tra le nuove funzionalità più avanzate di SharePoint Server 2013 e SharePoint Online è contenuto ricerca Web Part (CSWP). Questa Web Part utilizza l'indice di ricerca per recuperare rapidamente i risultati che vengono visualizzati all'utente. Utilizzare invece il contenuto Query Web Part (CQWP) nelle pagine Web Part ricerca contenuto per migliorare le prestazioni per gli utenti.
  
Utilizzo di una Web Part ricerca contenuto in una Web Part Query contenuto quasi sempre genererà in modo significativo migliorare le prestazioni di carico di pagina in SharePoint Online. Non esiste un poche attività di configurazione aggiuntive per ottenere la query destra, ma vantaggi sono soddisfatti utenti e ottimizzare le prestazioni.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>Confronto tra il miglioramento delle prestazioni che ottenere dall'utilizzo di Web Part ricerca contenuto invece di Web Part Query contenuto

Nell'esempio seguente mostra i miglioramenti a livello di prestazioni relative che venga visualizzato quando si utilizza una Web Part ricerca contenuto anziché una Web Part Query contenuto. Gli effetti sono più ovvi con una struttura del sito complessa e vastissima query contenuta.
  
Questo sito di esempio presenta le caratteristiche seguenti:
  
- 8 livelli di siti secondari.
    
- Vengono elencati utilizzando un tipo di contenuto personalizzati "frutto".
    
- Nella Web Part query contenuto è ampie, restituzione di tutti gli elementi con il tipo di contenuto del "frutto".
    
- Nell'esempio viene utilizzato solo 50 elementi tra i 8 siti. Gli effetti saranno ancora più evidente per i siti con altro contenuto.
    
Ecco una schermata dei risultati della Web Part Query contenuto.
  
![Grafico con la query contenuto della web part](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
In Internet Explorer, utilizzare la scheda di **rete** F12 gli strumenti di sviluppo per esaminare i dettagli per l'intestazione risposta. Nella cattura di schermata seguente, il valore **SPRequestDuration** per il caricamento di questa pagina è 924 millisecondi. 
  
![Schermata durata della richiesta di 924](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration** indica la quantità di lavoro che viene eseguita nel server per preparare la pagina. Passare il contenuto da Web part Query contenuto dalla Web part di ricerca in modo significativo consente di ridurre il tempo che necessario per il rendering della pagina. Una pagina con un equivalente Web Part ricerca contenuto, al contrario, restituisce lo stesso numero di risultati ha un valore di **SPRequestDuration** di 106 millisecondi come illustrato in questa schermata: 
  
![Schermata durata della richiesta di 106](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>Aggiunta di una Web Part ricerca contenuto in SharePoint Online

Aggiunta di una Web Part ricerca contenuto è molto simile a una normale Web Part Query contenuto. Vedere la sezione *"aggiungere una Web Part ricerca contenuto"* in [configurare una Web Part ricerca contenuto in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>Creazione di query di ricerca appropriata per la Web Part ricerca contenuto

Dopo aver aggiunto una Web Part ricerca contenuto, è possibile restringere la ricerca e gli elementi da restituire. Per istruzioni dettagliate su come eseguire questa operazione, vedere la sezione *"Contenuto visualizzato mediante la configurazione di una query in una Web Part ricerca contenuto avanzata"* in [configurare una Web Part ricerca contenuto in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="query-building-and-testing-tool"></a>Creazione e testing dello strumento di query

Per uno strumento creare e testare query complesse, vedere lo [Strumento di Query di ricerca](https://sp2013searchtool.codeplex.com/) in Codeplex. 
  

