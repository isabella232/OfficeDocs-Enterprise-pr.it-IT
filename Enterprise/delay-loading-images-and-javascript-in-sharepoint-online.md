---
title: Ritardo caricamento immagini e JavaScript in SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: In questo articolo viene illustrato come è possibile ridurre i tempi di caricamento delle pagine di SharePoint Online mediante l'utilizzo di JavaScript per ritardare il caricamento delle immagini e caricando JavaScript non essenziali fino a dopo caricamento della pagina.
ms.openlocfilehash: b8b052d85c99e51dff4b0fc747b3b52c17de8d8b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541353"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a><span data-ttu-id="92c56-103">Ritardo caricamento immagini e JavaScript in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="92c56-103">Delay loading images and JavaScript in SharePoint Online</span></span>

<span data-ttu-id="92c56-104">In questo articolo viene illustrato come è possibile ridurre i tempi di caricamento delle pagine di SharePoint Online mediante l'utilizzo di JavaScript per ritardare il caricamento delle immagini e caricando JavaScript non essenziali fino a dopo caricamento della pagina.</span><span class="sxs-lookup"><span data-stu-id="92c56-104">This article describes how you can decrease the load time for SharePoint Online pages by using JavaScript to delay loading images and also by waiting to load non-essential JavaScript until after the page loads.</span></span> 
  
<span data-ttu-id="92c56-p101">Le immagini possono influenzare negativamente la velocità di caricamento della pagina in SharePoint Online. Per impostazione predefinita, i browser Internet più moderni pre-recuperano immagini durante il caricamento di una pagina HTML. Ciò può far sì che la pagina si carichi lentamente senza motivo se le immagini non sono visibili sullo schermo fino a quando l'utente scorre verso il basso. Le immagini possono impedire al browser di caricare la parte visibile della pagina. Per risolvere questo problema, è possibile utilizzare JavaScript per ignorare prima il caricamento delle immagini. Inoltre, anche il caricamento di JavaScript non essenziale può rallentare i tempi di caricamento delle pagine di SharePoint. In questo argomento vengono descritti alcuni metodi utilizzabili per migliorare i tempi di caricamento delle pagine con JavaScript in SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="92c56-p101">Images can negatively affect page load speeds on SharePoint Online. By default, most modern Internet browsers pre-fetch images when loading an HTML page. This can cause the page to be unnecessarily slow to load if the images are not visible on the screen until the user scrolls down. The images can block the browser from loading the visible part of the page. To work around this problem, you can use JavaScript to skip loading the images first. Also, loading non-essential JavaScript can slow down load times on your SharePoint pages too. This topic describes some methods you can use to improve page load times with JavaScript in SharePoint Online.</span></span> 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a><span data-ttu-id="92c56-112">Migliorare i tempi di caricamento delle immagini nelle pagine caricando le pagine di SharePoint Online tramite JavaScript</span><span class="sxs-lookup"><span data-stu-id="92c56-112">Improve page load times by delaying image loading in SharePoint Online pages by using JavaScript</span></span>

<span data-ttu-id="92c56-p102">È possibile utilizzare JavaScript per impedire a un web browser da immagini pre-recupero. Ciò consente di velocizzare rendering documento globale. Per ottenere questo risultato si rimuove il valore dell'attributo src dal \<img\> tag e sostituirlo con il percorso di un file in un attributo di dati ad esempio: dati src. Per esempio:</span><span class="sxs-lookup"><span data-stu-id="92c56-p102">You can use JavaScript to prevent a web browser from pre-fetching images. This speeds up overall document rendering. To do this you remove the value of the src attribute from the \<img\> tag and replace it with the path to a file in a data attribute such as: data-src. For example:</span></span>
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

<span data-ttu-id="92c56-p103">Con questo metodo, il browser non scaricare le immagini immediatamente. Se l'immagine è già nel riquadro di visualizzazione, JavaScript indica al browser per recuperare l'URL dall'attributo di dati e inserire come valore dell'attributo src. L'immagine viene caricata solo come l'utente scorre e si tratta nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="92c56-p103">By using this method, the browser doesn't download the images immediately. If the image is already in the viewport, JavaScript tells the browser to retrieve the URL from the data attribute and insert it as the value for the src attribute. The image only loads as the user scrolls and it comes into view.</span></span>
  
<span data-ttu-id="92c56-119">Per effettuare tutte queste accadrebbe, sarà necessario utilizzare JavaScript.</span><span class="sxs-lookup"><span data-stu-id="92c56-119">To make all of this happen, you'll need to use JavaScript.</span></span>
  
<span data-ttu-id="92c56-120">In un file di testo, definire la funzione **isElementInViewport()** per controllare se un elemento fa o meno parte del browser visibile all'utente.</span><span class="sxs-lookup"><span data-stu-id="92c56-120">In a text file, define the **isElementInViewport()** function to check whether or not an element is in the part of the browser that is visible to the user.</span></span> 
  
```
function isElementInViewport(el) {
  if (!el)
    return false;
  var rect = el.getBoundingClientRect();
  return (
    rect.top >= 0 &amp;&amp;
    rect.left >= 0 &amp;&amp;
    rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &amp;&amp;
    rect.right <= (window.innerWidth || document.documentElement.clientWidth) 
  );
}

```

<span data-ttu-id="92c56-p104">Utilizzare quindi **isElementInViewport()** nella funzione **loadItemsInView()**. La funzione **loadItemsInView()** caricherà tutte le immagini con un valore per l'attributo dati-src se fanno parte del browser visibile all'utente. Aggiungere la seguente funzione al file di testo:</span><span class="sxs-lookup"><span data-stu-id="92c56-p104">Next, use **isElementInViewport()** in the **loadItemsInView()** function. The **loadItemsInView()** function will load all images that have a value for the data-src attribute if they are in the part of the browser that is visible to the user. Add the following function to the text file:</span></span> 
  
```
function loadItemsInView() {
  //Select elements by the row id.
  $("#row [data-src]").each(function () {
      var isVisible = isElementInViewport(this);
      if (isVisible) {
          if ($(this).attr("src") == undefined) {
              $(this).attr("src", $(this).data("src"));
          }
      }
  });
}
```

<span data-ttu-id="92c56-p105">Infine, chiamare **loadItemsInView()** da **window.onscroll()** come illustrato nell'esempio seguente. In questo modo tutte le immagini presenti nel riquadro di visualizzazione sono caricate quando ne ha bisogno l'utente, ma non prima. Aggiungere quanto segue al file di testo:</span><span class="sxs-lookup"><span data-stu-id="92c56-p105">Finally, call **loadItemsInView()** from within **window.onscroll()** as shown in the following example. This ensures that any images that are in the viewport are loaded as the user needs them, but not before. Add the following to the text file:</span></span> 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

<span data-ttu-id="92c56-p106">SharePoint Online, è necessario collegare la funzione seguente viene associata all'evento scorrimento #s4-workspace \<div\> tag. Ciò avviene perché gli eventi della finestra vengono sottoposto a override per garantire che la barra multifunzione rimane connessa alla parte superiore della pagina.</span><span class="sxs-lookup"><span data-stu-id="92c56-p106">For SharePoint Online, you need to attach the following function to the scroll event on the #s4-workspace \<div\> tag. This is because the window events are overridden in order to ensure the ribbon remains attached to the top of the page.</span></span>
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

<span data-ttu-id="92c56-129">Salvare il file di testo come un file JavaScript con estensione js, ad esempio delayLoadImages.js.</span><span class="sxs-lookup"><span data-stu-id="92c56-129">Save the text file as a JavaScript file with the extension .js, for example delayLoadImages.js.</span></span>
  
<span data-ttu-id="92c56-p107">Dopo aver terminato la scrittura delayLoadImages.js, è possibile aggiungere il contenuto del file a una pagina master di SharePoint Online. Ottenere questo risultato aggiungendo un collegamento di script per l'intestazione della pagina master. Una volta che si trova in una pagina master, il codice JavaScript verrà applicato a tutte le pagine del sito di SharePoint Online che utilizzano tale layout di pagina master. In alternativa, se si intende utilizzare solo questo in una pagina del sito, utilizzare l'editor dello script Web Part per incorporare JavaScript nella pagina. Vedere i seguenti argomenti per ulteriori informazioni:</span><span class="sxs-lookup"><span data-stu-id="92c56-p107">Once you've finished writing delayLoadImages.js, you can add the contents of the file to a master page in SharePoint Online. You do this by adding a script link to the header in the master page. Once it's in a master page, the JavaScript will be applied to all pages in your SharePoint Online site that use that master page layout. Alternatively, if you intend to only use this on one page of your site, use the script editor Web Part to embed the JavaScript into the page. See these topics for more information:</span></span>
  
- [<span data-ttu-id="92c56-135">Procedura: applicare una pagina master a un sito di SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="92c56-135">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [<span data-ttu-id="92c56-136">Procedura: Create a page layout in SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="92c56-136">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 <span data-ttu-id="92c56-137">**Esempio: Fare riferimento al file JavaScript delayLoadImages.js da una pagina master in SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="92c56-137">**Example: Referencing the JavaScript delayLoadImages.js file from a master page in SharePoint Online**</span></span>
  
<span data-ttu-id="92c56-p108">Affinché funzioni, è necessario fare riferimento a jQuery nella pagina master. Nell'esempio seguente, è possibile visualizzare il caricamento della pagina iniziale dove viene caricata solo un'immagine, ma ce ne sono molte altre nella pagina.</span><span class="sxs-lookup"><span data-stu-id="92c56-p108">In order for this to work, you also need to reference jQuery in the master page. In the following example, you can see in the initial page load that there is only one image loaded but there are several more on the page.</span></span>
  
![Schermata che mostra un'immagine caricata nella pagina](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
<span data-ttu-id="92c56-141">La schermata seguente mostra il resto delle immagini che vengono scaricate dopo che si scorre fino alla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="92c56-141">The following screen shot shows the rest of the images that are downloaded after they scroll into view.</span></span>
  
![Schermata che mostra varie immagini caricate nella pagina](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
<span data-ttu-id="92c56-p109">Ritardare il caricamento delle immagini tramite JavaScript può essere una tecnica efficace per aumentare le prestazioni. Tuttavia, se la tecnica viene applicata a un sito Web pubblico, allora i motori di ricerca non sono in grado di eseguire ricerche per indicizzazione delle immagini nello stesso modo in cui si farebbe una ricerca per indicizzazione di un'immagine regolarmente formata. Questo può influire sulla classificazione nei motori di ricerca perché i metadati dell'immagine stessa non sono realmente presenti fino a quando non viene caricata la pagina. I crawler dei motori di ricerca leggono solo il codice HTML e pertanto non vedranno le immagini come contenuto nella pagina. Le immagini sono uno dei fattori utilizzati per classificare le pagine nei risultati della ricerca. Un modo per risolvere il problema consiste nell'utilizzare testo introduttivo per le immagini.</span><span class="sxs-lookup"><span data-stu-id="92c56-p109">Delaying image loading by using JavaScript can be an effective technique in increasing performance; however, if the technique is applied on a public website then search engines are not able to crawl the images in the same way they would crawl a regularly formed image. This can affect rankings on search engines because metadata on the image itself is not really there until the page loads. Search engine crawlers only read the HTML and therefore will not see the images as content on the page. Images are one of the factors used to rank pages in search results. One way to work around this is to use introductory text for your images.</span></span>
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a><span data-ttu-id="92c56-148">Esempio di codice GitHub: inserimento di JavaScript per migliorare le prestazioni</span><span class="sxs-lookup"><span data-stu-id="92c56-148">GitHub code sample: Injecting JavaScript to improve performance</span></span>

<span data-ttu-id="92c56-149">Non perdere l'articolo ed esempio di codice in [JavaScript injection](https://go.microsoft.com/fwlink/p/?LinkId=524759) forniti su GitHub.</span><span class="sxs-lookup"><span data-stu-id="92c56-149">Don't miss the article and code sample on [JavaScript injection](https://go.microsoft.com/fwlink/p/?LinkId=524759) provided on GitHub.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="92c56-150">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="92c56-150">See also</span></span>

[<span data-ttu-id="92c56-151">Browser supportati in Office 2013 e Office 365 ProPlus</span><span class="sxs-lookup"><span data-stu-id="92c56-151">Supported browsers in Office 2013 and Office 365 ProPlus</span></span>](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[<span data-ttu-id="92c56-152">Procedura: applicare una pagina master a un sito di SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="92c56-152">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[<span data-ttu-id="92c56-153">Procedura: Create a page layout in SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="92c56-153">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)

