---
title: Capacità di pianificazione test di carico e SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/18/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: In questo articolo viene descritto come distribuire in SharePoint Online senza eseguire il test di carico tradizionale poiché non è consentito.
ms.openlocfilehash: 06649942f20dc18abfcae0e56df7e3ea56ed9165
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541389"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>Capacità di pianificazione test di carico e SharePoint Online

In questo articolo viene descritto come distribuire in SharePoint Online senza eseguire il test di carico tradizionale poiché non è consentito.
  
Anche se active load test su SharePoint Online è sconsigliata, esistono altri modi che è possibile verificare che un sito non genererà un'esperienza utente scadente quando si avvia il sito. 
  
Con SharePoint Online non è necessario eseguire la pianificazione della capacità, come questa operazione viene eseguita automaticamente come parte di questo servizio. Con ambienti locali, il test di carico consente di convalidare i presupposti scala e infine individuare il punto di interruzione di una farm. per la saturazione a carico. Con SharePoint Online è necessario eseguire operazioni in modo diverso. Da un ambiente multi-tenant, è necessario proteggere tenant tutti nella stessa farm in modo che si verranno automaticamente limitare i test di carico. In questo modo si riceverà deludente e potenzialmente fuorvianti risultati se si tenta di caricare l'ambiente di testing.
  
Uno dei principali vantaggi di SharePoint Online in una distribuzione locale è la flessibilità della cloud. Ambiente su larga scala è configurato per servizio milioni di utenti a intervalli giornalieri pertanto importante è gestire in modo efficace della capacità, espandendo automaticamente le farm come e quando necessario. In questo articolo viene illustrato come si prevede di aumento di capacità e la scala con sul posto. L'articolo vengono inoltre illustrate approcci per l'utilizzo che non coinvolgono il test di carico.
  
## <a name="how-office-365-predicts-load-and-expands-capacity"></a>Modalità di Office 365 stima del carico e si espande la capacità

SharePoint Online lavoro gestione della capacità del server viene eseguita utilizzando due metodi:
  
- Previsione della capacità
    
- Bilanciamento del carico nelle farm di server singolo
    
A differenza di pianificazione per un ambiente locale, per la previsione della capacità in SharePoint Online, è in grado di compilare le statistiche e grafico potenziali requisiti di qualsiasi gruppo di server specificato. Potrebbe essere simile le richieste di domanda di aggregazione nell'area (in un'area è un gruppo di farm di SharePoint) linea crescita nell'immagine riportata di seguito:
  
![Grafico della capacità predittiva: previsione](media/ca800cb6-cc59-451f-98bd-55e035489af3.png)
  
Mentre si trova in una farm di qualsiasi imprevisto la crescita, la somma aggregata delle richieste in un'area è prevedibile. Identificare le tendenze di crescita in SharePoint Online, è possibile pianificare l'espansione futura.
  
Per poter utilizzare la capacità in modo efficiente e in relazione ai fattori di crescita imprevisti, qualsiasi farm, si dispone di automazione che tiene traccia del carico front-end e garantisce la scalabilità verticale sul posto, quando necessario. La metrica principale che viene utilizzato come un segnale per implementare la scalabilità di front end server è il carico della CPU. L'obiettivo è mantenere il carico della CPU di picco in 40%. Si tratta per avere sufficiente buffer di assorbire picchi imprevisti. Come carico approcci 40% stabile, si aggiungere server front-end alla farm.
  
![Grafico della capacità predittiva: gestione delle farm](media/6b2a8c63-24c1-4504-b7a3-3d3b3be2583a.png)
  
Ulteriori server è possibile aggiungere rapidamente a una farm con quelli che sono stati aggiunti in precedenza all'area tramite l'utilizzo di previsione. 
  
## <a name="how-do-i-plan-for-a-site-launch"></a>Come pianificare avvia un sito?

È necessario attendere che la farm in cui viene aperto il nuovo sito verrà automaticamente monitorata in modo che vengano aggiunti nuovi server front-end, come descritto in precedenza. Per questo motivo, non è necessario alcuna notifica per il lancio del nuovo sito.
  
In seguito altre procedure consigliate per una singola pagina di SharePoint Online è improbabile che avvia un sito nuovo in anche 100.000 utenti avrà effetto alla farm.
  
Esistono alcune strategie per la pianificazione per una versione di un nuovo sito di SharePoint Online. Come illustrato nella figura seguente, spesso la quantità di utenti che sono invitati è significativamente superiore a quelle che utilizzano effettivamente il sito. In questa immagine viene illustrata una strategia su come distribuire una versione precedente. Questo metodo non solo utile durante il caricamento delle prestazioni, ma consente inoltre di identificare informazioni su come migliorare il sito di SharePoint prima di grandi dimensioni dalla maggior parte degli utenti vederla.
  
![Grafico degli utenti invitati e attivi](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
Nella fase pilota, è consigliabile ottenere commenti e suggerimenti degli utenti che l'organizzazione considera attendibile e SA will essere impegnati. In questo modo è possibile misurare come il sistema viene utilizzato, nonché alle prestazioni.
  
A questo punto, inizia un (in inglese) fuori a tutti gli utenti nelle onde; come ottenere commenti ed esaminare periodicamente le prestazioni. Il vantaggio di presentazione del sistema e apportare miglioramenti come sistema ottenuto utilizzo più lentamente. In questo modo di reagire all'aumento del carico come è stato implementato il sito a più utenti.
  
Infine, durante i test di carico sono consentiti, i clienti possibile impostare periodica ping al servizio misura disponibilità e latenza. Si identifica una linea di base per il proprio sito. Tuttavia, queste devono essere conservate a bassa frequenza per evitare problemi descritti in precedenza di limitazione.
  

