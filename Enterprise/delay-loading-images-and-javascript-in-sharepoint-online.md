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
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>Ritardo caricamento immagini e JavaScript in SharePoint Online

In questo articolo viene illustrato come è possibile ridurre i tempi di caricamento delle pagine di SharePoint Online mediante l'utilizzo di JavaScript per ritardare il caricamento delle immagini e caricando JavaScript non essenziali fino a dopo caricamento della pagina. 
  
Le immagini possono influenzare negativamente la velocità di caricamento della pagina in SharePoint Online. Per impostazione predefinita, i browser Internet più moderni pre-recuperano immagini durante il caricamento di una pagina HTML. Ciò può far sì che la pagina si carichi lentamente senza motivo se le immagini non sono visibili sullo schermo fino a quando l'utente scorre verso il basso. Le immagini possono impedire al browser di caricare la parte visibile della pagina. Per risolvere questo problema, è possibile utilizzare JavaScript per ignorare prima il caricamento delle immagini. Inoltre, anche il caricamento di JavaScript non essenziale può rallentare i tempi di caricamento delle pagine di SharePoint. In questo argomento vengono descritti alcuni metodi utilizzabili per migliorare i tempi di caricamento delle pagine con JavaScript in SharePoint Online. 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>Migliorare i tempi di caricamento delle immagini nelle pagine caricando le pagine di SharePoint Online tramite JavaScript

È possibile utilizzare JavaScript per impedire a un web browser da immagini pre-recupero. Ciò consente di velocizzare rendering documento globale. Per ottenere questo risultato si rimuove il valore dell'attributo src dal \<img\> tag e sostituirlo con il percorso di un file in un attributo di dati ad esempio: dati src. Per esempio:
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

Con questo metodo, il browser non scaricare le immagini immediatamente. Se l'immagine è già nel riquadro di visualizzazione, JavaScript indica al browser per recuperare l'URL dall'attributo di dati e inserire come valore dell'attributo src. L'immagine viene caricata solo come l'utente scorre e si tratta nella visualizzazione.
  
Per effettuare tutte queste accadrebbe, sarà necessario utilizzare JavaScript.
  
In un file di testo, definire la funzione **isElementInViewport()** per controllare se un elemento fa o meno parte del browser visibile all'utente. 
  
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

Utilizzare quindi **isElementInViewport()** nella funzione **loadItemsInView()**. La funzione **loadItemsInView()** caricherà tutte le immagini con un valore per l'attributo dati-src se fanno parte del browser visibile all'utente. Aggiungere la seguente funzione al file di testo: 
  
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

Infine, chiamare **loadItemsInView()** da **window.onscroll()** come illustrato nell'esempio seguente. In questo modo tutte le immagini presenti nel riquadro di visualizzazione sono caricate quando ne ha bisogno l'utente, ma non prima. Aggiungere quanto segue al file di testo: 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

SharePoint Online, è necessario collegare la funzione seguente viene associata all'evento scorrimento #s4-workspace \<div\> tag. Ciò avviene perché gli eventi della finestra vengono sottoposto a override per garantire che la barra multifunzione rimane connessa alla parte superiore della pagina.
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

Salvare il file di testo come un file JavaScript con estensione js, ad esempio delayLoadImages.js.
  
Dopo aver terminato la scrittura delayLoadImages.js, è possibile aggiungere il contenuto del file a una pagina master di SharePoint Online. Ottenere questo risultato aggiungendo un collegamento di script per l'intestazione della pagina master. Una volta che si trova in una pagina master, il codice JavaScript verrà applicato a tutte le pagine del sito di SharePoint Online che utilizzano tale layout di pagina master. In alternativa, se si intende utilizzare solo questo in una pagina del sito, utilizzare l'editor dello script Web Part per incorporare JavaScript nella pagina. Vedere i seguenti argomenti per ulteriori informazioni:
  
- [Procedura: applicare una pagina master a un sito di SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [Procedura: Create a page layout in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 **Esempio: Fare riferimento al file JavaScript delayLoadImages.js da una pagina master in SharePoint Online**
  
Affinché funzioni, è necessario fare riferimento a jQuery nella pagina master. Nell'esempio seguente, è possibile visualizzare il caricamento della pagina iniziale dove viene caricata solo un'immagine, ma ce ne sono molte altre nella pagina.
  
![Schermata che mostra un'immagine caricata nella pagina](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
La schermata seguente mostra il resto delle immagini che vengono scaricate dopo che si scorre fino alla visualizzazione.
  
![Schermata che mostra varie immagini caricate nella pagina](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
Ritardare il caricamento delle immagini tramite JavaScript può essere una tecnica efficace per aumentare le prestazioni. Tuttavia, se la tecnica viene applicata a un sito Web pubblico, allora i motori di ricerca non sono in grado di eseguire ricerche per indicizzazione delle immagini nello stesso modo in cui si farebbe una ricerca per indicizzazione di un'immagine regolarmente formata. Questo può influire sulla classificazione nei motori di ricerca perché i metadati dell'immagine stessa non sono realmente presenti fino a quando non viene caricata la pagina. I crawler dei motori di ricerca leggono solo il codice HTML e pertanto non vedranno le immagini come contenuto nella pagina. Le immagini sono uno dei fattori utilizzati per classificare le pagine nei risultati della ricerca. Un modo per risolvere il problema consiste nell'utilizzare testo introduttivo per le immagini.
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>Esempio di codice GitHub: inserimento di JavaScript per migliorare le prestazioni

Non perdere l'articolo ed esempio di codice in [JavaScript injection](https://go.microsoft.com/fwlink/p/?LinkId=524759) forniti su GitHub. 
  
## <a name="see-also"></a>Vedere anche

[Browser supportati in Office 2013 e Office 365 ProPlus](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[Procedura: applicare una pagina master a un sito di SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[Procedura: Create a page layout in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)

