---
title: Utilizzo delle reti di distribuzione del contenuto con SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: 'Riepilogo: in questo articolo vengono descritte le reti di distribuzione del contenuto (reti CDN) e come è possibile utilizzarle per aumentare le prestazioni di SharePoint Online.'
ms.openlocfilehash: 24b12ae60a8c089d8e32d2609957e8b0e3420510
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070582"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a>Utilizzo delle reti di distribuzione del contenuto con SharePoint Online

 **Riepilogo:** In questo articolo vengono descritte le reti di distribuzione del contenuto (reti CDN) e come è possibile utilizzarle per aumentare le prestazioni di SharePoint Online. 
  
Nelle community di sviluppo Web di oggi esistono numerose raccolte comuni, ad esempio file JavaScript e CSS, che possono essere incluse nella soluzione SharePoint. Molte di queste sono ospitate da Microsoft sulla rete CDN ASP. Questo significa che è possibile fare riferimento a queste raccolte da questi server distribuiti e consentire ai sistemi di routing DNS incorporati di Internet di trovare il server più vicino all'utente. Negli esempi di questo articolo viene illustrato come la differenza tra il download della popolare raccolta jQuery dal server di SharePoint Online rispetto alla CDN ASP sia notevole. L'utente già potrebbe avere la versione CDN memorizzata nella cache sul computer locale in modo che non sia necessario scaricare il file. Ciò può essere importante se sono presenti utenti distribuiti in tutto il mondo e lontano dal datacenter che ospita il sito di SharePoint Online.
  
Durante la creazione di pagine per SharePoint Online, la latenza può essere influenzata dalla distanza fisica tra gli utenti e il percorso dell'istanza di SharePoint Online. Ciò è particolarmente importante per le organizzazioni che dispongono di una presenza globale dove un sito può essere ospitato in un continente mentre gli utenti dall'altro lato del mondo accedono al contenuto. Le CDN consentono di risolvere questa situazione ospitando determinate risorse web più comuni in posizioni diverse più vicino agli utenti finali.
  
Poiché una CDN è una rete globale di server che ospitano gli stessi file, gli URL Internet per i file archiviati sulla CDN vengono interpretati dai computer client in modo che il server più vicino all'utente servi il file. Questa operazione riduce in modo significativo i ritardi dovuti ai round trip della rete.
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a>La sfida di ospitare siti di SharePoint Online per un gruppo di destinatari globale

I siti di SharePoint Online sono ospitati in datacenter relativi alla posizione (specificata dall'utente) selezionata quando ci si registra a Office 365. Ad esempio, se il sito è sui server negli Stati Uniti e sono presenti utenti che accedono al sito dall'Asia orientale, potrebbero verificarsi problemi di latenza a causa della distanza che i dati devono percorrere sui cavi in fibra ottica.
  
Molti file statici utilizzati dall'interfaccia utente predefinita di SharePoint sono già ospitati nella rete globale di reti CDN di Microsoft. In questo modo verranno migliorate le prestazioni nel tempo. Tuttavia, se si utilizzano risorse popolati JavaScript e CSS (ad esempio, JQuery, Modernizr, Bootstrap o ASP.NET Ajax) è possibile migliorare i tempi di caricamento di questi file utilizzando CDN disponibili gratuitamente.
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a>Vantaggi dell'utilizzo di CDN per migliorare la velocità di download

L'utilizzo di CDN può migliorare i tempi di caricamento delle pagine per diversi motivi. Un motivo è che la distanza tra la CDN e l'utente può essere inferiore alla distanza con l'istanza di SharePoint Online. Tali reti sono altamente distribuite e sono anche progettate per avere tempi di risposta e disponibilità molto elevati. Un altro motivo è che se si utilizza una raccolta popolare di file CSS, in combinazione con una rete CDN, è possibile che la libreria venga già memorizzata nella cache e che non sia nemmeno necessario scaricarla.
  
Nelle schermate seguenti vengono illustrati i vantaggi derivanti dall'utilizzo di reti CDN. Queste schermate sono presenti nella scheda **rete** degli strumenti di sviluppo di Internet Explorer 11. Queste schermate mostrano la latenza sulla popolare libreria jQuery. Per visualizzare questa schermata, in Internet Explorer, premere **F12** e selezionare la scheda **Rete** indicata con un'icona Wi-Fi. 
  
![Schermata della rete F12](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
Questo screenshot Visualizza la raccolta caricata nella raccolta pagine master nel sito di SharePoint Online. Il tempo necessario per caricare la raccolta è 1,51 secondi.
  
![Schermata del tempo di caricamento 1.51s](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
La seconda schermata Visualizza lo stesso file recapitato dalla rete CDN di Microsoft. Questa volta la latenza è di circa 496 millisecondi. Questo è un miglioramento di grandi dimensioni e indica che un intero secondo viene tolto al tempo totale necessario per scaricare il contenuto della pagina.
  
![Schermata dei tempi di caricamento in 469 ms](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a>Utilizzo delle reti CDN con SharePoint Server 2013

L'utilizzo di reti CDN ha senso solo in un contesto di SharePoint Online e deve essere evitato con SharePoint Server 2013. Infatti, tutti i vantaggi relativi alla posizione geografica non permangono se il server è locale o geograficamente vicino. Inoltre, se esiste una connessione di rete ai server in cui è ospitata, il sito può essere utilizzato senza una connessione Internet e pertanto non è in grado di recuperare i file CDN. In caso contrario, è consigliabile utilizzare una rete CDN se disponibile e stabile per la raccolta e i file necessari per il sito.
  
## <a name="popular-cdns-and-how-to-use-them"></a>Reti CDN comuni e relativo utilizzo

La rete CDN di Microsoft AJAX offre la maggior parte delle raccolte popolari, tra cui jQuery (e tutte le sue altre raccolte), ASP.NET AJAX, bootstrap, Knockout. js e molte altre.
  
Per includere gli script nel progetto, è sufficiente sostituire i riferimenti a queste raccolte disponibili pubblicamente con riferimenti all'indirizzo della rete CDN anziché includerlo nel progetto stesso. Per creare un collegamento a jQuery, ad esempio, utilizzare il codice seguente:
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Per ulteriori informazioni su reti CDN, vedere [Content Delivery Networks](content-delivery-networks.md).
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a>Ulteriori argomenti sull'utilizzo di reti CDN con SharePoint

[Web part sul lato client di hosting dalla rete CDN di Office 365](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

