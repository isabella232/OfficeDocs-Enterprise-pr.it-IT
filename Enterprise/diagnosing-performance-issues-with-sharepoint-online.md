---
title: Diagnosi dei problemi delle prestazioni con SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 2/23/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: In questo articolo viene illustrato come eseguire la diagnostica problemi comuni con il sito di SharePoint Online mediante strumenti di sviluppo di Internet Explorer.
ms.openlocfilehash: 89d4544bfabf6424b5f401bad7d63bd7fa41b5ca
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541272"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a><span data-ttu-id="3b2f9-103">Diagnosi dei problemi delle prestazioni con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3b2f9-103">Diagnosing performance issues with SharePoint Online</span></span>

<span data-ttu-id="3b2f9-104">In questo articolo viene illustrato come eseguire la diagnostica problemi comuni con il sito di SharePoint Online mediante strumenti di sviluppo di Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="3b2f9-104">This article shows you how you can diagnose common issues with your SharePoint Online site using Internet Explorer developer tools.</span></span>
  
<span data-ttu-id="3b2f9-105">Esistono tre modi per identificare che una pagina in un sito di SharePoint Online presenta di un problema di prestazioni con le personalizzazioni.</span><span class="sxs-lookup"><span data-stu-id="3b2f9-105">There are three different ways that you can identify that a page on a SharePoint Online site has a performance problem with the customizations.</span></span>
  
- <span data-ttu-id="3b2f9-106">Il network monitor della barra degli strumenti F12</span><span class="sxs-lookup"><span data-stu-id="3b2f9-106">The F12 tool bar network monitor</span></span>
    
- <span data-ttu-id="3b2f9-107">Confronto di una linea di base non personalizzata</span><span class="sxs-lookup"><span data-stu-id="3b2f9-107">Comparison to a non-customized baseline</span></span>
    
- <span data-ttu-id="3b2f9-108">Metrica dell'intestazione delle risposte di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3b2f9-108">SharePoint Online response header metrics</span></span>
    
<span data-ttu-id="3b2f9-p101">In questo argomento viene descritto come utilizzare ciascuno di questi metodi per la diagnosi di problemi di prestazioni. Dopo aver ancora stabilito la causa del problema, è possibile adottare una soluzione utilizzando gli articoli sull'ottimizzazione delle prestazioni di SharePoint che è possibile trovare su http://aka.ms/tune.</span><span class="sxs-lookup"><span data-stu-id="3b2f9-p101">This topic describes how to use each of these methods to diagnose performance issues. Once you've figured out the cause of the problem, you can work toward a solution using the articles about improving SharePoint performance that you can find on http://aka.ms/tune.</span></span>
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a><span data-ttu-id="3b2f9-111">Utilizzo della barra degli strumenti F12 per diagnosticare le prestazioni in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3b2f9-111">Using the F12 tool bar to diagnose performance in SharePoint Online</span></span>
<span data-ttu-id="3b2f9-112"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="3b2f9-112"></span></span>

<span data-ttu-id="3b2f9-p102">In questo articolo si utilizza Internet Explorer 11. Le versioni degli strumenti di sviluppo F12 su altri browser dispongono di caratteristiche simili, anche se potrebbero apparire leggermente diversi. Per informazioni sugli strumenti di sviluppo F12, vedere:</span><span class="sxs-lookup"><span data-stu-id="3b2f9-p102">In this article we use Internet Explorer 11. Versions of the F12 developer tools on other browsers have similar features though they may look slightly different. For information on the F12 developer tools, see:</span></span>
  
- [<span data-ttu-id="3b2f9-116">What's new in strumenti F12</span><span class="sxs-lookup"><span data-stu-id="3b2f9-116">What's new in F12 Tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [<span data-ttu-id="3b2f9-117">Mediante gli strumenti di sviluppo F12</span><span class="sxs-lookup"><span data-stu-id="3b2f9-117">Using the F12 developer tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
<span data-ttu-id="3b2f9-118">Per visualizzare gli strumenti di sviluppo premere **F12**, quindi fare clic sull'icona Wi-Fi: 
</span><span class="sxs-lookup"><span data-stu-id="3b2f9-118">To bring up the developer tools press **F12** and then click the Wi-Fi icon:</span></span> 
  
![Schermata dell'icona Wi-Fi di Strumenti di sviluppo F12](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
<span data-ttu-id="3b2f9-p103">Nella scheda **Rete**, premere il pulsante verde di riproduzione per caricare la pagina. Lo strumento restituisce tutti i file che il browser richiede per ottenere la pagina richiesta dall'utente. La schermata seguente mostra un elenco di questo tipo.</span><span class="sxs-lookup"><span data-stu-id="3b2f9-p103">On the **Network** tab, press the green play button to load a page. The tool returns all of the files that the browser requests in order to get the page you asked for. The following screen shot shows one such list.</span></span> 
  
![Schermata dell'elenco di file restituito con una richiesta di pagina.](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
<span data-ttu-id="3b2f9-124">È inoltre possibile visualizzare i tempi di download dei file sul lato destro, come illustrato in questa schermata.</span><span class="sxs-lookup"><span data-stu-id="3b2f9-124">You can also see the download times of the files on the right side as shown in this screen shot.</span></span>
  
![Diagramma che mostra il tempo necessario per il caricamento delle pagine richieste da SharePoint](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
<span data-ttu-id="3b2f9-p104">In questo modo, si ottiene una rappresentazione visiva del tempo impiegato per caricare il file. La linea verde segnala quando la pagina è pronta per il rendering del browser. Ciò può fornire una visualizzazione rapida dei file diversi che possono rallentare i caricamenti delle pagine sul sito.

</span><span class="sxs-lookup"><span data-stu-id="3b2f9-p104">This gives you a visual representation of how long the file took to load. The green line represents when the page is ready to be rendered by the browser. This can give you a quick view of the different files that might be causing slow page loads on your site.</span></span>
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a><span data-ttu-id="3b2f9-129">Impostazione di una linea di base non personalizzate per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3b2f9-129">Setting up a non-customized baseline for SharePoint Online</span></span>
<span data-ttu-id="3b2f9-130"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="3b2f9-130"></span></span>

<span data-ttu-id="3b2f9-p105">Il modo migliore per determinare i punti deboli delle prestazioni del sito consiste nel configurare una raccolta siti completamente out-di-predefinite in SharePoint Online. In questo modo è possibile confrontare i diversi aspetti di un sito con gli elementi restituiti con nessuna personalizzazione della pagina. OneDrive for Business della home page è un ottimo esempio di una raccolta siti distinta che viene in genere tutte le personalizzazioni.</span><span class="sxs-lookup"><span data-stu-id="3b2f9-p105">The best way to determine your site's performance weak points is to set up a completely out-of-the-box site collection in SharePoint Online. This way you can compare all the various aspects of your site with what you would get with no customization on the page. The OneDrive for Business home page is a good example of a separate site collection that is unlikely to have any customizations.</span></span>
  
## <a name="viewing-sharepoint-response-header-information"></a><span data-ttu-id="3b2f9-134">Visualizzazione delle informazioni di intestazione della risposta di SharePoint</span><span class="sxs-lookup"><span data-stu-id="3b2f9-134">Viewing SharePoint response header information</span></span>
<span data-ttu-id="3b2f9-135"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="3b2f9-135"></span></span>

<span data-ttu-id="3b2f9-p106">In SharePoint Online e SharePoint Server 2013 è possibile accedere alle informazioni inviate al browser nell'intestazione della risposta per ogni file. I due valori più utili per la diagnosi dei problemi di prestazioni sono SPRequestDuration e X-SharePointHealthScore:</span><span class="sxs-lookup"><span data-stu-id="3b2f9-p106">In SharePoint Online and SharePoint Server 2013 you can access the information that is sent back to the browser in the response header for each file. The two most useful values for diagnosing performance issues are SPRequestDuration and X-SharePointHealthScore:</span></span>
  
- <span data-ttu-id="3b2f9-138">**SPRequestDuration**</span><span class="sxs-lookup"><span data-stu-id="3b2f9-138">**SPRequestDuration**</span></span>
    
    <span data-ttu-id="3b2f9-p107">È la quantità di tempo impiegato per l'elaborazione della richiesta sul server. Ciò consente di determinare se la richiesta è molto pesante e richiede un utilizzo intensivo delle risorse. Questa è la migliore conoscenza disponibile relativa all'attività del server per visualizzare la pagina.</span><span class="sxs-lookup"><span data-stu-id="3b2f9-p107">This is the amount of time that the request took on the server to be processed. This can help determine if the request is very heavy and resource intensive. This is the best insight you have into how much work the server is doing to serve the page.</span></span>
    
- <span data-ttu-id="3b2f9-142">**X-SharePointHealthScore**</span><span class="sxs-lookup"><span data-stu-id="3b2f9-142">**X-SharePointHealthScore**</span></span>
    
    <span data-ttu-id="3b2f9-p108">Indica l'utilizzo del server o della CPU, in cui viene eseguita l'istanza di SharePoint. Questo numero compreso tra 0 e 10 dove 0 indica che il server è inattivo e 10 indica il server è occupato. Stato di integrità in modo coerente 9 o 10 potrebbe indicare un problema di prestazioni in corso con il server. Qualsiasi altro numero indica che tale server è impostato nell'intervallo previsto.</span><span class="sxs-lookup"><span data-stu-id="3b2f9-p108">This indicates the utilization of the server, or CPU, on which your SharePoint instance runs. This number ranges from 0 to 10 where 0 indicates the server is idle and 10 indicates the server is very busy. A HealthScore that is consistently 9 or 10 might indicate an ongoing performance issue with the server. Any other number indicates that server is operating within the expected range.</span></span>
    
 <span data-ttu-id="3b2f9-147">**Per visualizzare le informazioni di intestazione della risposta di SharePoint**</span><span class="sxs-lookup"><span data-stu-id="3b2f9-147">**To view SharePoint response header information**</span></span>
  
1. <span data-ttu-id="3b2f9-p109">Assicurarsi di avere installati gli strumenti di F12. Per ulteriori informazioni sul download e installazione di questi strumenti, vedere [What's new in strumenti F12](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span><span class="sxs-lookup"><span data-stu-id="3b2f9-p109">Ensure that you have the F12 tools installed. For more information on downloading and installing these tools, see [What's new in F12 tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span></span>
    
2. <span data-ttu-id="3b2f9-150">Negli strumenti F12,nella scheda **Rete**, premere il pulsante verde di riproduzione per caricare la pagina.</span><span class="sxs-lookup"><span data-stu-id="3b2f9-150">In the F12 tools, on the **Network** tab, press the green play button to load a page.</span></span> 
    
3. <span data-ttu-id="3b2f9-151">Fare clic sui file .aspx restituiti dagli strumenti, quindi fare clic su **DETTAGLI**.</span><span class="sxs-lookup"><span data-stu-id="3b2f9-151">Click one of the .aspx files returned by the tool and then click **DETAILS**.</span></span> 
    
    ![Mostra i dettagli dell'intestazione della risposta](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. <span data-ttu-id="3b2f9-153">Fare clic su **Intestazioni di risposta**.</span><span class="sxs-lookup"><span data-stu-id="3b2f9-153">Click **Response headers**.</span></span> 
    
    ![Diagramma che mostra l'URL dell'intestazione della risposta](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a><span data-ttu-id="3b2f9-155">Qual è la causa dei problemi delle prestazioni in SharePoint Online?</span><span class="sxs-lookup"><span data-stu-id="3b2f9-155">What's causing performance issues in SharePoint Online?</span></span>
<span data-ttu-id="3b2f9-156"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="3b2f9-156"></span></span>

<span data-ttu-id="3b2f9-p110">L'articolo [Opzioni di spostamento per SharePoint Online](navigation-options-for-sharepoint-online.md) è illustrato un esempio di utilizzo del valore SPRequestDuration per determinare che la struttura di spostamento complicato era causato della pagina per richiedere molto tempo per l'elaborazione sul server. Eseguendo un valore per un sito di base (senza personalizzazione), è possibile determinare se un file specifico è richiedere molto tempo per il caricamento. Nell'esempio viene utilizzato in [Opzioni di spostamento per SharePoint Online](navigation-options-for-sharepoint-online.md) è il file con estensione aspx principale. File contenente la maggior parte del codice ASP.NET esecuzione per il caricamento della pagina. In base al modello di sito che è utilizzare, potrebbe trattarsi start.aspx, aspx, default. aspx o un altro nome se si personalizza la home page. Se questo numero è notevolmente superiore a quelle del sito di base, è molto probabile che non vi è un valore complessa succedendo della pagina che causa problemi di prestazioni.</span><span class="sxs-lookup"><span data-stu-id="3b2f9-p110">The article [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) shows an example of using the SPRequestDuration value to determine that the complicated structural navigation was causing the page to take a long time to process on the server. By taking a value for a baseline site (without customization), it is possible to determine if any given file is taking a long time to load. The example used in [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) is the main .aspx file. That file contains most of the ASP.NET code that runs for your page load. Depending on the site template you use, this could be start.aspx, home.aspx, default.aspx, or another name if you customize the home page. If this number is considerably higher than your baseline site, then it's a good indication that there is something complex going on in your page that is causing performance issues.</span></span> 
  
<span data-ttu-id="3b2f9-p111">Dopo aver chiarito che si tratta di un problema specifico del sito, il metodo consigliato per individuare la causa della riduzione delle prestazioni è l'eliminazione di tutte le possibili cause, come le personalizzazioni della pagina, per poi riaggiungerle al sito una alla volta. Dopo aver rimosso sufficienti personalizzazioni soddisfacenti della pagina, sarà quindi possibile riaggiungere le personalizzazioni specifiche una alla volta.</span><span class="sxs-lookup"><span data-stu-id="3b2f9-p111">Once you have identified that an issue specific to your site, the recommended way to figure out what is causing poor performance is to eliminate all of the possible causes, like page customizations, and then add them back to the site one by one. Once you have removed enough customizations that the page is performing well, you can then add back specific customizations one by one.</span></span>
  
<span data-ttu-id="3b2f9-p112">Ad esempio, se si dispone di una struttura di spostamento molto complessa provare a modificare tale struttura per non visualizzare siti secondari, quindi controllare gli strumenti di sviluppo per vedere se ci sono differenze. In alternativa, se si dispone di una grande quantità di contenuti di aggiornamenti cumulativi provare a rimuoverli dalla pagina e vedere se si ottengono miglioramenti. Se si eliminano tutte le possibili cause e si aggiungono nuovamente una alla volta, è possibile identificare facilmente quali funzionalità sono il problema principale, per poi lavorare a una soluzione. 
</span><span class="sxs-lookup"><span data-stu-id="3b2f9-p112">For example, if you have a very complex navigation try changing the navigation to not show sub-sites then check the developer tools to see if this makes a difference. Or if you have a large amount of content roll-ups try removing them from your page and see if this improves things. If you eliminate all of the possible causes and add them back in one at a time, you can easily identify which features are the biggest problem and then work towards a solution.</span></span>
  

