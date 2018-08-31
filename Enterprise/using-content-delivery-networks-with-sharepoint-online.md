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
# <a name="using-content-delivery-networks-with-sharepoint-online"></a>Utilizzo di reti di distribuzione del contenuto con SharePoint Online

 **Riepilogo:** In questo articolo vengono descritti le reti di distribuzione del contenuto (CDN) e come è possibile utilizzare per migliorare le prestazioni di SharePoint Online. 
  
Nella community di sviluppo web odierna, sono disponibili molte librerie comuni (ad esempio file JavaScript e CSS) che è possibile includere nella soluzione SharePoint. Molte di queste ospitati da Microsoft sul loro CDN ASP. Indica che è possibile fare riferimento a tali raccolte da tali server distribuiti e consentire predefinite routing sistemi DNS di internet individuare il server più vicino all'utente. Gli esempi illustrati in questo articolo viene illustrato come la differenza tra il download jQuery raccolta più richiesti dal server di SharePoint Online e la rete CDN ASP è molto importante. L'utente anche disponga già la versione CDN memorizzati nella cache del computer locale in modo che non dispongono di scaricare il file. Può essere importante se vi sono utenti distribuiti in tutto il mondo e lontano dalla Data Center che ospita il sito di SharePoint Online.
  
Durante la creazione di pagine per SharePoint Online, la latenza può essere influenzata dalla distanza fisica tra gli utenti e il percorso dell'istanza di SharePoint Online. Ciò è particolarmente importante per le organizzazioni che dispongono di una presenza globale dove un sito può essere ospitato in un continente mentre gli utenti dall'altro lato del mondo accedono al contenuto. Le CDN consentono di risolvere questa situazione ospitando determinate risorse web più comuni in posizioni diverse più vicino agli utenti finali.
  
Poiché una CDN è una rete globale di server che ospitano gli stessi file, gli URL Internet per i file archiviati sulla CDN vengono interpretati dai computer client in modo che il server più vicino all'utente servi il file. Questa operazione riduce in modo significativo i ritardi dovuti ai round trip della rete.
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a>La sfida di ospitare siti di SharePoint Online per un gruppo di destinatari globale

I siti di SharePoint Online sono ospitati in datacenter relativi alla posizione (specificata dall'utente) selezionata quando ci si registra a Office 365. Ad esempio, se il sito è sui server negli Stati Uniti e sono presenti utenti che accedono al sito dall'Asia orientale, potrebbero verificarsi problemi di latenza a causa della distanza che i dati devono percorrere sui cavi in fibra ottica.
  
Numero di file statici utilizzato dall'interfaccia utente di SharePoint predefinito già ospitate in rete mondiale di Microsoft di CDN. In questo migliorare le prestazioni nel tempo. Tuttavia, se si utilizzano (ad esempio tutte le risorse più comuni di JavaScript e CSS JQuery, Modernizr, Bootstrap o ASP.NET Ajax) è possibile migliorare i tempi di caricamento dei file utilizzando disponibile gratuitamente CDN.
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a>Vantaggi dell'utilizzo di CDN per migliorare la velocità di download

Utilizzo CDN può migliorare caricamenti delle pagine per una serie di motivi. Uno dei motivi è che la distanza tra la rete CDN e l'utente può essere inferiore a distanza per l'istanza di SharePoint Online. Tali reti altamente distribuite e sono inoltre progettate per avere estremamente elevate disponibilità e tempi di risposta. Un altro motivo è che se si utilizza una raccolta di file CSS popolari, insieme a una rete CDN, l'utente sia già installata la libreria memorizzati nella cache e non sarà più necessario avere per il download di tutti i.
  
Catture di schermata seguente sono illustrati i vantaggi derivanti dall'utilizzo CDN. Le schermate sono la scheda di **rete** in strumenti di sviluppo di Internet Explorer 11. Queste catture di schermata mostrano la latenza in jQuery raccolta più comuni. Per visualizzare questa schermata in Internet Explorer, selezionare la scheda di **rete** che symbolized con un'icona Wi-Fi premere **F12** . 
  
![Schermata della rete F12](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
Questa schermata viene mostrato raccolta caricata nella raccolta pagine master del sito di SharePoint Online stesso. Il tempo impiegato per caricare la libreria è 1,51 secondi.
  
![Schermata del tempo di caricamento 1.51s](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
Il secondo di schermata viene mostrato lo stesso file distribuito tramite Microsoft CDN. Questa volta la latenza è di circa 496 millisecondi. Si tratta di un miglioramento di grandi dimensioni e viene illustrato che un intero secondo è rasato disattiva il tempo totale necessario per scaricare il contenuto della pagina.
  
![Schermata dei tempi di caricamento in 469 ms](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a>Utilizzo delle reti CDN con SharePoint Server 2013

Solo tramite CDN è significativa in un contesto di SharePoint Online e deve essere evitato, con SharePoint Server 2013. Ciò avviene perché tutti i vantaggi attorno posizione geografica non ha valore true se il server è disponibile in locale o aree geografiche Chiudere comunque. Inoltre, se esiste una connessione di rete per i server che ospita, quindi il sito può essere utilizzato senza una connessione Internet e pertanto non può recuperare i file di rete CDN. In caso contrario, è consigliabile utilizzare una rete CDN se esiste un disponibili e stabili per la raccolta e i file necessari per il sito.
  
## <a name="popular-cdns-and-how-to-use-them"></a>Reti CDN comuni e relativo utilizzo

Rete CDN Ajax di Microsoft offre la maggior parte delle librerie cui popolari inclusi jQuery e tutte le altre raccolte, ASP.NET Ajax, Bootstrap, Knockout.js e molto altro ancora.
  
Per includere gli script nel progetto, è sufficiente sostituire i riferimenti a queste raccolte disponibili pubblicamente con riferimenti all'indirizzo della rete CDN anziché includerlo nel progetto stesso. Per creare un collegamento a jQuery, ad esempio, utilizzare il codice seguente:
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Per ulteriori informazioni su CDN, vedere [reti di distribuzione del contenuto](content-delivery-networks.md).
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a>Altri argomenti relativi all'utilizzo CDN con SharePoint

[Hosting sul lato client web part in Office 365 CDN](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

