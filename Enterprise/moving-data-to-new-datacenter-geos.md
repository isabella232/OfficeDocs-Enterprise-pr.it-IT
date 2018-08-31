---
title: Spostamento dei dati di base al nuovo Office 365 datacenter geos
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 3/22/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 0a35176a-e585-4dec-a90b-36be8314667f
description: "Nuovo centro dati geos incrementare la capacità e calcolare le risorse necessarie per supportare la nostra crescita richiesta e l'utilizzo dei clienti in corso. Inoltre, il nuovo geos datacenter sono disponibili in geo residenza dati per i dati dei clienti core. Dati relativi ai clienti Core è un termine che fa riferimento a un sottoinsieme di dati relativi ai clienti definita nelle condizioni di Microsoft Online Services: Exchange Online contenuto delle cassette postali (corpo del messaggio di posta elettronica, le voci di calendario e il contenuto degli allegati di posta elettronica) e SharePoint Online di contenuto e i file di sito archiviati all'interno del sito e i file caricati in OneDrive for Business."
ms.openlocfilehash: 1f3af15852b1221daf2e2d994653c8bb9cf697e4
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541369"
---
# <a name="moving-core-data-to-new-office-365-datacenter-geos"></a>Spostamento dei dati di base al nuovo Office 365 datacenter geos

È continua aprire nuovo datacenter geos per Office 365 per servizi di business. Queste nuove geos datacenter incrementare la capacità e calcolare le risorse necessarie per supportare la nostra crescita richiesta e l'utilizzo dei clienti in corso. Inoltre, il nuovo geos datacenter sono disponibili in geo residenza dati per i dati dei clienti core. 

Dati relativi ai clienti Core è un termine che fa riferimento a un sottoinsieme di dati dei clienti definiti in [Termini di Microsoft Online Services](https://go.microsoft.com/fwlink/p/?LinkID=249048): 
- Contenuto delle cassette postali Exchange Online (corpo del messaggio di posta elettronica, le voci di calendario e il contenuto degli allegati di posta elettronica)
- Contenuto del sito SharePoint Online e i file archiviati all'interno del sito
- File caricati OneDrive for Business 
  
I clienti esistenti con i dati dei clienti core archiviati in un geo datacenter già esistente non sono interessati dal lancio di un nuovo livello geografico datacenter. Viene non introdotto Nessuna funzionalità uniche, caratteristiche o certificazioni di conformità con il nuovo livello geografico datacenter. Come cliente in uno di questi due geos, si verificherà la stessa qualità del servizio, prestazioni e controlli di sicurezza come descritto in precedenza. Offriamo esistente i clienti che hanno requisiti di residenza strict dati e che sono elencati nella tabella seguente, un'opzione per i dati relativi ai clienti core spostati geo nuovo.
  
|Considerare i clienti con fatturazione * * *|Precedente datacenter geo * * *|Nuovo centro dati geo * * *|Geo disponibile successivamente * * *|
|:-----|:-----|:-----|:-----|
|Giappone * * *| Asia/Pacifico | Giappone | Dicembre 2014 |
|Australia, Nuova Zelanda Figi * * *| Asia/Pacifico | Australia | Marzo 2015 |
|India * * *| Asia/Pacifico | India | Ottobre 2015 |
|Canada * * *| Nord America | Canada | Maggio 2016 |
|Regno Unito * * *| Europa | Regno Unito | Settembre 2016 |
|Corea del Sud * * *| Asia/Pacifico | Sud Corea | Aprile 2017 |
|Francia * * *| Europa | Francia | Marzo 2018 |
   
> [!NOTE]
> L'opzione di residenza dati e la disponibilità per spostare i dati dei clienti nella nuova geo, non è un valore predefinito per ogni nuovo geo è sulla barra di avvio. Quando si espande nel nuovo geos in futuro, valuterà la disponibilità e le condizioni di dati si sposta su un livello geografico dal livello geografico base. 
  
Nuovi clienti o tenant di Office 365 creati dopo la disponibilità di nuovi geo di datacenter avrà i dati dei clienti core memorizzati automaticamente statici nel nuovo geo di Data Center.
  
Un elenco completo di tutti i Data Center geos, centri dati e il percorso dei dati customer statici è disponibile come parte del [datacenter interattiva esegue il mapping](https://aka.ms/dcmaps). 
  
## <a name="data-residency-option"></a>Opzione di residenza dati

Microsoft fornisce un'opzione di residenza dati ai clienti di Office 365 esistenti che rientrano geos datacenter elencati nella tabella precedente. Con questa opzione, i clienti con esigenze di residenza dati possono richiedere per spostare i dati relativi ai clienti core in geo nuovo. Si consiglia ai clienti di eseguire alcuna azione, a meno che l'organizzazione richiede che i dati di analisi core archiviati statici nei rispettivi geo datacenter nuovo. Se si sceglie di spostare i dati, i clienti limitare le possibilità di Microsoft per ottimizzare la posizione dei dati dei clienti core statici nella loro corrente o nuova geo di Data Center. Come cliente in uno di questi due geos, si verificherà la stessa qualità del servizio, prestazioni e controlli di sicurezza come descritto in precedenza.
  
Per i clienti che hanno necessità di disporre dei dati di base spostati al nuovo geo:
  
- Gli utenti devono richiedere contenga i dati spostati in una finestra di registrazione set. Esaminare la pagina [come richiedere la migrazione dei dati](request-your-data-move.md) per informazioni dettagliate sulla finestra di registrazione per il livello geografico e istruzioni per la registrazione nel programma. 
    
- Spostamenti di dati possono richiedere fino a 24 mesi dopo il periodo di richiesta per il completamento.
    
- Viene non introdotto Nessuna funzionalità uniche, caratteristiche o certificazioni di conformità con il nuovo livello geografico datacenter.
    
- La complessità, precisione e scala in cui è necessario eseguire gli spostamenti di dati all'interno di un ambiente gestito a livello globale e automatizzato ci impediscono condivisione quando uno spostamento di dati è previsto per il completamento per il tenant o qualsiasi altro tenant singolo. Clienti riceveranno una conferma nell'interfaccia di messaggio per ogni servizio partecipano quando è completata la migrazione dei dati. 
    
- Spostamenti di dati sono un'operazione di servizio back-end con un impatto minimo per gli utenti finali. Nella pagina [durante e dopo la migrazione dei dati](during-and-after-your-data-move.md) sono elencate le funzionalità che possono essere influenzate. È conforme a [Microsoft Online Services Service Level Agreement (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) per garantire la disponibilità in modo che i clienti necessari per preparare o per monitorare durante lo spostamento. Se necessario, viene eseguita la notifica di manutenzione del servizio. 
    
## <a name="related-topics"></a>Argomenti correlati 
 
[Come richiedere lo spostamento dati](request-your-data-move.md)
    
[Domande frequenti sullo spostamento dati](data-move-faq.md)
  
[Nuova geos Data Center di Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Servizi di Azure dall'area](https://azure.microsoft.com/en-us/regions/)
  

