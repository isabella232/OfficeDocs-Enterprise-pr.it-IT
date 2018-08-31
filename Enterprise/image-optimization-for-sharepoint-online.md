---
title: Ottimizzazione delle immagini per SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/19/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: Informazioni su come utilizzare il rendering e sprite per migliorare le prestazioni immagine i siti Web di SharePoint Online.
ms.openlocfilehash: 313046dec885a38062635254699301bcf556d698
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541138"
---
# <a name="image-optimization-for-sharepoint-online"></a>Ottimizzazione delle immagini per SharePoint Online

La velocità di caricamento di una pagina Web dipende dalle dimensioni combinata di tutti i componenti necessari per il rendering della pagina, ad esempio immagini, HTML, JavaScript e CSS. Le immagini sono una fantastica opportunità per rendere il proprio sito più interessante, ma le dimensioni possono influire sulle prestazioni. Per ottimizzare le immagini con la compressione ridimensionamento e utilizzo di sprite, è possibile spostare gli effetti delle immagini di grandi dimensioni. Utilizza il rendering di immagini di SharePoint, è possibile caricare una singola immagine di grandi dimensioni e visualizzare le sezioni dell'immagine in modo che possa essere riutilizzata anziché ricaricato.
  
## <a name="using-sprites-to-speed-up-image-loading-in-sharepoint-online"></a>Utilizzo di sprite per accelerare il caricamento delle immagini in SharePoint Online

|||
|:-----|:-----|
| Sprite un'immagine contiene molte immagini più piccole. Tramite CSS selezionare una parte dell'immagine composta da visualizzare in una determinata parte della pagina con posizionamento assoluto. In pratica, spostare una sola immagine intorno alla pagina anziché caricare più immagini e rendere visibile una piccola parte di tale immagine attraverso un piccola finestra in cui è visualizzata la parte obbligatoria dell'immagine sprite all'utente finale. SharePoint Online utilizza sprite per visualizzare le icone diverse in spcommon.png sprite.  <br/>  Che cosa viene descritto di seguito:  <br/>  Compressione delle immagini  <br/>  Ottimizzazione dell'immagine  <br/>  Rendering di immagini di SharePoint  <br/> |![Cattura di schermata del spcommon](media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)|
   
Ciò può migliorare le prestazioni perché si scarica solo un'immagine anziché diverse e quindi memorizzare nella cache e riutilizzare l'immagine. Anche se l'immagine non rimangono memorizzati nella cache, facendo in modo che una singola immagine anziché più immagini, questo metodo consente di ridurre il numero totale di richieste HTTP al server che consente di ridurre i tempi di caricamento della pagina. Si tratta veramente di un modulo di vendita abbinata immagine. Questa è una tecnica molto utile se le immagini non modifica molto spesso, ad esempio, le icone, come illustrato nell'esempio SharePoint fornita in precedenza. È possibile come utilizzare [Essentials Web](http://vswebessentials.com/), un progetto di terze parti, open source, basate sulla community per ottenere questo risultato facilmente in Microsoft Visual Studio. Per ulteriori informazioni, vedere [la riduzione e vendita abbinata in SharePoint Online](https://go.microsoft.com/fwlink/?LinkId=708698).
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading-in-sharepoint"></a>Utilizzo di ottimizzazione e compressione delle immagini per accelerare il caricamento delle immagini in SharePoint

Per quanto riguarda l'ottimizzazione e la compressione delle immagini, si tratta della riduzione delle dimensioni dei file di immagini utilizzate nel proprio sito. Spesso, la tecnica migliore per ridurre le dimensioni di un'immagine è riportare l'immagine alle dimensioni massime in cui verrà visualizzata nel sito. Non ha alcun senso disporre di un'immagine in dimensioni superiori rispetto a quelle in cui verrà mai visualizzata. Accertarsi che le immagini siano nelle dimensioni corrette utilizzando un editor di immagini è un modo rapido e facile per ridurre le dimensioni della propria pagina.
  
Dopo che le immagini sono le dimensioni corrette, il passaggio successivo è per ottimizzare la compressione di queste immagini. Sono disponibili diversi strumenti disponibili da utilizzare per la compressione e ottimizzazione, tra cui raccolta foto e gli strumenti di terze parti. La chiave di compressione è per ridurre le dimensioni del file per quanto possibile senza compromettere la qualità visibile per gli utenti finali. Verificare che si testa i file compressi in una visualizzazione ad alta definizione per garantire che ancora appare buona.
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>Velocizzare i download delle pagine tramite rendering delle immagini di SharePoint

Rendering di immagini è una funzionalità di SharePoint Online che consente di utilizzare backup di versioni diverse di immagini in base alle dimensioni predefinite immagine. Ciò è particolarmente importante quando le dimensioni dell'immagine, ad esempio la larghezza e altezza risolti dal foglio di stile CSS nel sito o non disponibile il contenuto dell'immagine generato dall'utente. Anche se un'immagine risolto da CSS, l'immagine ad alta risoluzione è ancora stato caricato. In questo caso è possono ridurre le dimensioni del file utilizzando il rendering di immagini.
  
> [!NOTE]
> Il rendering di è disponibile solo per SharePoint quando è abilitata la pubblicazione. È possibile abilitare la pubblicazione in impostazioni \> Impostazioni sito \> Gestisci caratteristiche sito \> pubblicazione SharePoint Server. L'opzione non verrà visualizzato in caso contrario. 
  
Il ridimensionamento del rendering delle immagini parte dalla dimensione minima definita dall'utente (larghezza o altezza), per poi ridimensionare l'immagine in modo che l'altra dimensione venga automaticamente ridimensionata in base alle proporzioni bloccate. Per impostazione predefinita, l'immagine verrà ritagliata dal centro alle dimensioni rimanenti. Ad esempio, se si definisce un rendering di 100 px di larghezza e 50 px di altezza e l'immagine originale è di 1000 px di larghezza e 800 px di altezza, verrà ridimensionata in modo che la dimensione di 800 px diventi 50 px e quella di 1000 px (ora 62,5 px) venga ritagliata dal centro dell'immagine.
  
La procedura è relativamente semplice ma, per utilizzare il rendering delle immagini, il rendering deve trovarsi nel sito di SharePoint prima di aggiungere le immagini. Inoltre, è necessario disporre anche dell'Infrastruttura di pubblicazione SharePoint Server (livello della raccolta siti) e la funzionalità Pubblicazione SharePoint Server (livello di sito) attivate.
  
 **Aggiungere un rendering di immagini per velocizzare il caricamento della pagina**
  
1. Verificare che l'account utente che esegue questa procedura disponga, almeno le autorizzazioni di progettazione per il sito principale della raccolta siti e che il sito in fase di pubblicazione a una pagina Web.
    
2. In un browser Web, andare al sito principale della raccolta siti di pubblicazione.
    
3. Scegliere l'icona **Impostazioni**. 
    
4. Nella pagina **Impostazioni sito**, nella sezione **Aspetto**, vengono visualizzati i rendering delle immagini incorporate. 
    
    È possibile utilizzare la parte esterna dei rendering della casella oppure selezionare **Rendering di immagini** per crearne uno nuovo. 
    
    ![Cattura di schermata del rendering di immagini](media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. Nella pagina **Rendering di immagini**, selezionare **Aggiungi nuovo elemento**.
    
    ![Schermata Aggiungi nuovo elemento](media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. Nella pagina **Nuovo rendering immagine**, nella casella **Nome** immettere un nome per il rendering. 
    
7. Nelle caselle di testo **Larghezza** e **Altezza** immettere le rispettive dimensioni in pixel del rendering, quindi selezionare **Salva**.
    
    ![Schermata del nome di rendering di immagine](media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions-in-sharepoint"></a>Personalizzare il ritaglio con i rendering di immagini in SharePoint

Per impostazione predefinita, viene generato una copia immagine dal centro dell'immagine. È possibile modificare il rendering di immagini per le singole immagini da parte dell'immagine che si desidera utilizzare il ritaglio. È possibile ritagliare le immagini singolarmente, per ogni copia trasformata. Ritaglio le immagini di velocizzare caricamento mediante l'utilizzo della cache blob di SharePoint per creare una versione dell'immagine per ciascuna copia della pagina. In questo modo il carico del server è ridotto perché l'immagine viene ridimensionata solo una volta e quindi è pronto per servire più volte per gli utenti finali. Per ulteriori informazioni su come ritagliare un rendering di immagini, vedere [ritagliare un rendering di immagini](https://go.microsoft.com/fwlink/p/?LinkId=525626).
  

