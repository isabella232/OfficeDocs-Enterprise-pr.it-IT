---
title: Utilizzo di reti di distribuzione del contenuto con SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: 'Riepilogo: In questo articolo vengono descritti le reti di distribuzione del contenuto (CDN) e come è possibile utilizzare per migliorare le prestazioni di SharePoint Online.'
ms.openlocfilehash: 63062c08d0c22518eb36ea0a6faa97106fd394b4
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541228"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a><span data-ttu-id="38455-103">Utilizzo di reti di distribuzione del contenuto con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="38455-103">Using content delivery networks with SharePoint Online</span></span>

 <span data-ttu-id="38455-104">**Riepilogo:** In questo articolo vengono descritti le reti di distribuzione del contenuto (CDN) e come è possibile utilizzare per migliorare le prestazioni di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="38455-104">**Summary:** This article describes Content Delivery Networks (CDNs) and how you can use them to increase SharePoint Online performance.</span></span> 
  
<span data-ttu-id="38455-p101">Nella community di sviluppo web odierna, sono disponibili molte librerie comuni (ad esempio file JavaScript e CSS) che è possibile includere nella soluzione SharePoint. Molte di queste ospitati da Microsoft sul loro CDN ASP. Indica che è possibile fare riferimento a tali raccolte da tali server distribuiti e consentire predefinite routing sistemi DNS di internet individuare il server più vicino all'utente. Gli esempi illustrati in questo articolo viene illustrato come la differenza tra il download jQuery raccolta più richiesti dal server di SharePoint Online e la rete CDN ASP è molto importante. L'utente anche disponga già la versione CDN memorizzati nella cache del computer locale in modo che non dispongono di scaricare il file. Può essere importante se vi sono utenti distribuiti in tutto il mondo e lontano dalla Data Center che ospita il sito di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="38455-p101">In today's web development communities, there are many common libraries (such as JavaScript and CSS files) that you may include in your SharePoint solution. Many of these are hosted by Microsoft on their ASP CDN. This means you can reference these libraries from these distributed servers and allow the internet's built-in DNS routing systems to find the closest server to your user. The examples in this article demonstrate how the time difference between downloading the popular library jQuery from the SharePoint Online server versus the ASP CDN is quite significant. The user also may already have the CDN version cached on the local computer so that they do not have to download the file. This can be important if you have users distributed all over the world and far away from the datacenter that hosts your SharePoint Online site.</span></span>
  
<span data-ttu-id="38455-p102">Durante la creazione di pagine per SharePoint Online, la latenza può essere influenzata dalla distanza fisica tra gli utenti e il percorso dell'istanza di SharePoint Online. Ciò è particolarmente importante per le organizzazioni che dispongono di una presenza globale dove un sito può essere ospitato in un continente mentre gli utenti dall'altro lato del mondo accedono al contenuto. Le CDN consentono di risolvere questa situazione ospitando determinate risorse web più comuni in posizioni diverse più vicino agli utenti finali.</span><span class="sxs-lookup"><span data-stu-id="38455-p102">When creating pages for SharePoint Online, latency can be affected by the physical distance between your users and the location of the SharePoint Online instance. This is particularly important for organizations that have a global presence where a site may be hosted on one continent while users on the other side of the world are accessing its content. CDNs help mitigate this situation by hosting certain popular web assets in different locations closer to the end users.</span></span>
  
<span data-ttu-id="38455-p103">Poiché una CDN è una rete globale di server che ospitano gli stessi file, gli URL Internet per i file archiviati sulla CDN vengono interpretati dai computer client in modo che il server più vicino all'utente servi il file. Questa operazione riduce in modo significativo i ritardi dovuti ai round trip della rete.</span><span class="sxs-lookup"><span data-stu-id="38455-p103">Since a CDN is a worldwide network of servers that host the same files, Internet URLs for files stored on the CDNs are interpreted by the client machine so that the server that is closest to the user serves the file. Doing this significantly reduces delays caused by network round trips.</span></span>
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a><span data-ttu-id="38455-116">La sfida di ospitare siti di SharePoint Online per un gruppo di destinatari globale</span><span class="sxs-lookup"><span data-stu-id="38455-116">The challenge of hosting SharePoint Online sites for a global audience</span></span>

<span data-ttu-id="38455-p104">I siti di SharePoint Online sono ospitati in datacenter relativi alla posizione (specificata dall'utente) selezionata quando ci si registra a Office 365. Ad esempio, se il sito è sui server negli Stati Uniti e sono presenti utenti che accedono al sito dall'Asia orientale, potrebbero verificarsi problemi di latenza a causa della distanza che i dati devono percorrere sui cavi in fibra ottica.</span><span class="sxs-lookup"><span data-stu-id="38455-p104">SharePoint Online sites are hosted at datacenters relative to the location (specified by the user) selected when you signed up with Office 365. For example, if your site is on servers in the United States and you have users accessing the site from East Asia, latency issues might arise due to the distance the data has to travel over fiber optic cable.</span></span>
  
<span data-ttu-id="38455-p105">Numero di file statici utilizzato dall'interfaccia utente di SharePoint predefinito già ospitate in rete mondiale di Microsoft di CDN. In questo migliorare le prestazioni nel tempo. Tuttavia, se si utilizzano (ad esempio tutte le risorse più comuni di JavaScript e CSS JQuery, Modernizr, Bootstrap o ASP.NET Ajax) è possibile migliorare i tempi di caricamento dei file utilizzando disponibile gratuitamente CDN.</span><span class="sxs-lookup"><span data-stu-id="38455-p105">Many static files used by the default SharePoint user interface are already hosted on Microsoft's worldwide network of CDNs. This will improve performance over time. However, if you use any popular JavaScript and CSS assets (for example; JQuery, Modernizr, Bootstrap, or ASP.NET Ajax) you can improve the loading times of these files by using freely available CDNs.</span></span>
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a><span data-ttu-id="38455-122">Vantaggi dell'utilizzo di CDN per migliorare la velocità di download</span><span class="sxs-lookup"><span data-stu-id="38455-122">Advantages of using CDNs to improve download speed</span></span>

<span data-ttu-id="38455-p106">Utilizzo CDN può migliorare caricamenti delle pagine per una serie di motivi. Uno dei motivi è che la distanza tra la rete CDN e l'utente può essere inferiore a distanza per l'istanza di SharePoint Online. Tali reti altamente distribuite e sono inoltre progettate per avere estremamente elevate disponibilità e tempi di risposta. Un altro motivo è che se si utilizza una raccolta di file CSS popolari, insieme a una rete CDN, l'utente sia già installata la libreria memorizzati nella cache e non sarà più necessario avere per il download di tutti i.</span><span class="sxs-lookup"><span data-stu-id="38455-p106">Using CDNs can improve page load times for a variety of reasons. One reason is that the distance between the CDN and the user may be shorter than the distance to the SharePoint Online instance. These networks are highly distributed and are also designed to have very high availability and response times. Another reason is that if you are using a popular library of CSS files, in conjunction with a CDN, the user may already have the library cached and they won't even need to download it at all.</span></span>
  
<span data-ttu-id="38455-p107">Catture di schermata seguente sono illustrati i vantaggi derivanti dall'utilizzo CDN. Le schermate sono la scheda di **rete** in strumenti di sviluppo di Internet Explorer 11. Queste catture di schermata mostrano la latenza in jQuery raccolta più comuni. Per visualizzare questa schermata in Internet Explorer, selezionare la scheda di **rete** che symbolized con un'icona Wi-Fi premere **F12** .</span><span class="sxs-lookup"><span data-stu-id="38455-p107">The following screen shots illustrate the advantages of using CDNs. These screen shots are from the **Network** tab in the Internet Explorer 11 developer tools. These screen shots show the latency on the popular library jQuery. To bring up this screen, in Internet Explorer, press **F12** and select the **Network** tab which is symbolized with a Wi-Fi icon.</span></span> 
  
![Schermata della rete F12](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
<span data-ttu-id="38455-p108">Questa schermata viene mostrato raccolta caricata nella raccolta pagine master del sito di SharePoint Online stesso. Il tempo impiegato per caricare la libreria è 1,51 secondi.</span><span class="sxs-lookup"><span data-stu-id="38455-p108">This screen shot shows the library uploaded to the master page gallery on the SharePoint Online site itself. The time it took to upload the library is 1.51 seconds.</span></span>
  
![Schermata del tempo di caricamento 1.51s](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
<span data-ttu-id="38455-p109">Il secondo di schermata viene mostrato lo stesso file distribuito tramite Microsoft CDN. Questa volta la latenza è di circa 496 millisecondi. Si tratta di un miglioramento di grandi dimensioni e viene illustrato che un intero secondo è rasato disattiva il tempo totale necessario per scaricare il contenuto della pagina.</span><span class="sxs-lookup"><span data-stu-id="38455-p109">The second screen shot shows the same file delivered by Microsoft's CDN. This time the latency is around 496 milliseconds. This is a large improvement and shows that a whole second is shaved off the total time to download the page content.</span></span>
  
![Schermata dei tempi di caricamento in 469 ms](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a><span data-ttu-id="38455-139">Utilizzo delle reti CDN con SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="38455-139">Using CDNs with SharePoint Server 2013</span></span>

<span data-ttu-id="38455-p110">Solo tramite CDN è significativa in un contesto di SharePoint Online e deve essere evitato, con SharePoint Server 2013. Ciò avviene perché tutti i vantaggi attorno posizione geografica non ha valore true se il server è disponibile in locale o aree geografiche Chiudere comunque. Inoltre, se esiste una connessione di rete per i server che ospita, quindi il sito può essere utilizzato senza una connessione Internet e pertanto non può recuperare i file di rete CDN. In caso contrario, è consigliabile utilizzare una rete CDN se esiste un disponibili e stabili per la raccolta e i file necessari per il sito.</span><span class="sxs-lookup"><span data-stu-id="38455-p110">Using CDNs only makes sense in a SharePoint Online context and should be avoided with SharePoint Server 2013. This is because all of the advantages around geographic location do not hold true if the server is located on-premises or geographically close anyway. Additionally, if there is a network connection to the servers where it's hosted, then the site may be used without an Internet connection and therefore cannot retrieve the CDN files. Otherwise, you should use a CDN if there is one available and stable for the library and files you need for your site.</span></span>
  
## <a name="popular-cdns-and-how-to-use-them"></a><span data-ttu-id="38455-144">Reti CDN comuni e relativo utilizzo</span><span class="sxs-lookup"><span data-stu-id="38455-144">Popular CDNs and how to use them</span></span>

<span data-ttu-id="38455-145">Rete CDN Ajax di Microsoft offre la maggior parte delle librerie cui popolari inclusi jQuery e tutte le altre raccolte, ASP.NET Ajax, Bootstrap, Knockout.js e molto altro ancora.</span><span class="sxs-lookup"><span data-stu-id="38455-145">Microsoft's Ajax CDN offers most of the popular libraries including jQuery (and all of its other libraries), ASP.NET Ajax, Bootstrap, Knockout.js, and many more.</span></span>
  
<span data-ttu-id="38455-p111">Per includere gli script nel progetto, è sufficiente sostituire i riferimenti a queste raccolte disponibili pubblicamente con riferimenti all'indirizzo della rete CDN anziché includerlo nel progetto stesso. Per creare un collegamento a jQuery, ad esempio, utilizzare il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="38455-p111">To include these scripts in your project, simply replace any references to these publicly available libraries with references to the CDN address instead of including it in your project itself. For example, use the following code to link to jQuery:</span></span>
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

<span data-ttu-id="38455-148">Per ulteriori informazioni su CDN, vedere [reti di distribuzione del contenuto](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="38455-148">For more information about CDNs, see [Content delivery networks](content-delivery-networks.md).</span></span>
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a><span data-ttu-id="38455-149">Altri argomenti relativi all'utilizzo CDN con SharePoint</span><span class="sxs-lookup"><span data-stu-id="38455-149">More topics about using CDNs with SharePoint</span></span>

[<span data-ttu-id="38455-150">Hosting sul lato client web part in Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="38455-150">Hosting client-side web part from Office 365 CDN</span></span>](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

