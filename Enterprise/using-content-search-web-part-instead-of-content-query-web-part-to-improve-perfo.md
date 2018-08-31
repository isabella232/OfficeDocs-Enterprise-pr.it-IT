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
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a><span data-ttu-id="b8d87-103">Utilizzo di Web Part ricerca contenuto invece di Web Part Query contenuto per migliorare le prestazioni di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b8d87-103">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>

<span data-ttu-id="b8d87-104">In questo articolo viene descritto come migliorare le prestazioni, sostituendo la Web Part Query contenuto con Web Part ricerca contenuto in SharePoint Server 2013 e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="b8d87-104">This article describes how to increase performance by replacing the Content Query Web Part with the Content Search Web Part in SharePoint Server 2013 and SharePoint Online.</span></span>
  
<span data-ttu-id="b8d87-p101">Tra le nuove funzionalità più avanzate di SharePoint Server 2013 e SharePoint Online è contenuto ricerca Web Part (CSWP). Questa Web Part utilizza l'indice di ricerca per recuperare rapidamente i risultati che vengono visualizzati all'utente. Utilizzare invece il contenuto Query Web Part (CQWP) nelle pagine Web Part ricerca contenuto per migliorare le prestazioni per gli utenti.</span><span class="sxs-lookup"><span data-stu-id="b8d87-p101">One of the most powerful new features of SharePoint Server 2013 and SharePoint Online is the Content Search Web Part (CSWP). This Web Part uses the search index to quickly retrieve results which are shown to the user. Use the Content Search Web Part instead of the Content Query Web Part (CQWP) in your pages to improve performance for your users.</span></span>
  
<span data-ttu-id="b8d87-p102">Utilizzo di una Web Part ricerca contenuto in una Web Part Query contenuto quasi sempre genererà in modo significativo migliorare le prestazioni di carico di pagina in SharePoint Online. Non esiste un poche attività di configurazione aggiuntive per ottenere la query destra, ma vantaggi sono soddisfatti utenti e ottimizzare le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="b8d87-p102">Using a Content Search Web Part over a Content Query Web Part will almost always result in significantly better page load performance on SharePoint Online. There is a little additional configuration to get the right query, but the rewards are improved performance and happier users.</span></span>
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a><span data-ttu-id="b8d87-110">Confronto tra il miglioramento delle prestazioni che ottenere dall'utilizzo di Web Part ricerca contenuto invece di Web Part Query contenuto</span><span class="sxs-lookup"><span data-stu-id="b8d87-110">Comparing the performance gain you get from using Content Search Web Part instead of Content Query Web Part</span></span>

<span data-ttu-id="b8d87-p103">Nell'esempio seguente mostra i miglioramenti a livello di prestazioni relative che venga visualizzato quando si utilizza una Web Part ricerca contenuto anziché una Web Part Query contenuto. Gli effetti sono più ovvi con una struttura del sito complessa e vastissima query contenuta.</span><span class="sxs-lookup"><span data-stu-id="b8d87-p103">The following examples show the relative performance gains you may receive when you use a Content Search Web Part instead of a Content Query Web Part. The effects are more obvious with a complex site structure and very broad content queries.</span></span>
  
<span data-ttu-id="b8d87-113">Questo sito di esempio presenta le caratteristiche seguenti:</span><span class="sxs-lookup"><span data-stu-id="b8d87-113">This example site has the following characteristics:</span></span>
  
- <span data-ttu-id="b8d87-114">8 livelli di siti secondari.</span><span class="sxs-lookup"><span data-stu-id="b8d87-114">8 levels of subsites.</span></span>
    
- <span data-ttu-id="b8d87-115">Vengono elencati utilizzando un tipo di contenuto personalizzati "frutto".</span><span class="sxs-lookup"><span data-stu-id="b8d87-115">Lists using a custom "fruit" content type.</span></span>
    
- <span data-ttu-id="b8d87-116">Nella Web Part query contenuto è ampie, restituzione di tutti gli elementi con il tipo di contenuto del "frutto".</span><span class="sxs-lookup"><span data-stu-id="b8d87-116">In the Web Part, the content query is broad, returning all items with the content type of "fruit".</span></span>
    
- <span data-ttu-id="b8d87-p104">Nell'esempio viene utilizzato solo 50 elementi tra i 8 siti. Gli effetti saranno ancora più evidente per i siti con altro contenuto.</span><span class="sxs-lookup"><span data-stu-id="b8d87-p104">The example only uses 50 items across the 8 sites. The effects will be even more pronounced for sites with more content.</span></span>
    
<span data-ttu-id="b8d87-119">Ecco una schermata dei risultati della Web Part Query contenuto.</span><span class="sxs-lookup"><span data-stu-id="b8d87-119">Here is a screen shot of the results of the Content Query Web Part.</span></span>
  
![Grafico con la query contenuto della web part](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
<span data-ttu-id="b8d87-p105">In Internet Explorer, utilizzare la scheda di **rete** F12 gli strumenti di sviluppo per esaminare i dettagli per l'intestazione risposta. Nella cattura di schermata seguente, il valore **SPRequestDuration** per il caricamento di questa pagina è 924 millisecondi.</span><span class="sxs-lookup"><span data-stu-id="b8d87-p105">In Internet Explorer, use the **Network** tab of the F12 developer tools to look at the details for the response header. In the following screen shot, the value for the **SPRequestDuration** for this page load is 924 milliseconds.</span></span> 
  
![Schermata durata della richiesta di 924](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 <span data-ttu-id="b8d87-p106">**SPRequestDuration** indica la quantità di lavoro che viene eseguita nel server per preparare la pagina. Passare il contenuto da Web part Query contenuto dalla Web part di ricerca in modo significativo consente di ridurre il tempo che necessario per il rendering della pagina. Una pagina con un equivalente Web Part ricerca contenuto, al contrario, restituisce lo stesso numero di risultati ha un valore di **SPRequestDuration** di 106 millisecondi come illustrato in questa schermata:</span><span class="sxs-lookup"><span data-stu-id="b8d87-p106">**SPRequestDuration** indicates the amount of work that is done on the server to prepare the page. Switching Content by Query Web Parts with Content by Search Web Parts dramatically reduces the time it takes to render the page. By contrast, a page with an equivalent Content Search Web Part, returning the same number of results has an **SPRequestDuration** value of 106 milliseconds as shown in this screen shot:</span></span> 
  
![Schermata durata della richiesta di 106](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a><span data-ttu-id="b8d87-128">Aggiunta di una Web Part ricerca contenuto in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b8d87-128">Adding a Content Search Web Part in SharePoint Online</span></span>

<span data-ttu-id="b8d87-p107">Aggiunta di una Web Part ricerca contenuto è molto simile a una normale Web Part Query contenuto. Vedere la sezione *"aggiungere una Web Part ricerca contenuto"* in [configurare una Web Part ricerca contenuto in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span><span class="sxs-lookup"><span data-stu-id="b8d87-p107">Adding a Content Search Web Part is very similar to a regular Content Query Web Part. See the section  *"Add a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a><span data-ttu-id="b8d87-131">Creazione di query di ricerca appropriata per la Web Part ricerca contenuto</span><span class="sxs-lookup"><span data-stu-id="b8d87-131">Creating the right search query for your Content Search Web Part</span></span>

<span data-ttu-id="b8d87-p108">Dopo aver aggiunto una Web Part ricerca contenuto, è possibile restringere la ricerca e gli elementi da restituire. Per istruzioni dettagliate su come eseguire questa operazione, vedere la sezione *"Contenuto visualizzato mediante la configurazione di una query in una Web Part ricerca contenuto avanzata"* in [configurare una Web Part ricerca contenuto in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span><span class="sxs-lookup"><span data-stu-id="b8d87-p108">Once you have added a Content Search Web Part, you can refine the search and return the items you want. For detailed instructions on how to do this, see the section,  *"Display content by configuring an advanced query in a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="query-building-and-testing-tool"></a><span data-ttu-id="b8d87-134">Creazione e testing dello strumento di query</span><span class="sxs-lookup"><span data-stu-id="b8d87-134">Query building and testing tool</span></span>

<span data-ttu-id="b8d87-135">Per uno strumento creare e testare query complesse, vedere lo [Strumento di Query di ricerca](https://sp2013searchtool.codeplex.com/) in Codeplex.</span><span class="sxs-lookup"><span data-stu-id="b8d87-135">For a tool to build and test complex queries, see the [Search Query Tool](https://sp2013searchtool.codeplex.com/) on Codeplex.</span></span> 
  

