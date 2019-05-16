---
title: Spostamento dei dati di base in un nuovo datacenter di Office 365 GEOS
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 03/15/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 0a35176a-e585-4dec-a90b-36be8314667f
description: "Nuovo datacenter GEOS aggiungono capacità e risorse di calcolo per supportare la crescente domanda e la crescita dell'utilizzo dei clienti. Inoltre, il nuovo datacenter GEOS offre la residenza di dati in-Geo per i dati di base dei clienti. I dati dei clienti di base sono un termine che fa riferimento a un sottoinsieme di dati dei clienti definiti nelle condizioni dei servizi online Microsoft: contenuto delle cassette postali di Exchange Online (corpo del messaggio di posta elettronica, voci del calendario e contenuto degli allegati di posta elettronica) e contenuto del sito di SharePoint Online e file archiviati all'interno del sito e i file caricati in OneDrive for business."
ms.openlocfilehash: 8dd9295618c765bb9eeaffbcec82ff83af8b2e21
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069992"
---
# <a name="moving-core-data-to-new-office-365-datacenter-geos"></a>Spostamento dei dati di base in un nuovo datacenter di Office 365 GEOS

Si continua ad aprire nuovo datacenter GEOS per i servizi di Office 365 for business. Questi nuovi datacenter GEOS aggiungono capacità e risorse di calcolo per supportare la crescita della domanda e dell'utilizzo dei clienti in continua espansione. Inoltre, il nuovo datacenter GEOS offre la residenza di dati in-Geo per i dati di base dei clienti. 

I dati dei clienti di base sono un termine che fa riferimento a un sottoinsieme di dati dei clienti definiti nelle [condizioni dei servizi online Microsoft](https://go.microsoft.com/fwlink/p/?LinkID=249048): 
- Contenuto delle cassette postali di Exchange Online (corpo del messaggio di posta elettronica, voci del calendario e contenuto degli allegati di posta elettronica)
- Contenuto del sito di SharePoint Online e file archiviati all'interno del sito
- File caricati in OneDrive for business 
  
I clienti esistenti che dispongono di dati di base dei clienti archiviati in un datacenter geografico già esistente non sono interessati dal lancio di un nuovo Data Center Geo. Non sono presenti funzionalità esclusive, funzionalità o certificazioni di conformità con il nuovo Data Center Geo. Come clienti in uno qualsiasi di questi due GEOS, si verificheranno gli stessi controlli di qualità dei servizi, delle prestazioni e della sicurezza come in precedenza. Offriamo ai clienti esistenti che hanno requisiti di residenza dei dati rigorosi e che sono elencati nella tabella seguente, un'opzione che consente di spostare i dati di base dei clienti nel nuovo geografico.
  
|Clienti con indirizzo di fatturazione in * * * *|Datacenter geografico precedente * * * *|Nuovo datacenter Geo * * * *|Geografica disponibile da * * * *|
|:-----|:-----|:-----|:-----|
|Giappone * * * *| Asia/Pacifico | Giappone | Dicembre 2014 |
|Australia, Nuova Zelanda, Figi * * * *| Asia/Pacifico | Australia | Marzo 2015 |
|India * * * *| Asia/Pacifico | India | Ottobre 2015 |
|Canada * * * *| Nord America | Canada | Maggio 2016 |
|Regno Unito * * * *| Europa | Regno Unito | Settembre 2016 |
|Corea del sud * * * *| Asia/Pacifico | Sud Corea | Aprile 2017 |
|Francia * * * *| Europa | Francia | Marzo 2018 |
|Emirati Arabi Uniti * * * *| Europa | Emirati Arabi Uniti | Annunciate |
|Sudafrica * * * *| Europa | Sudafrica | Annunciate |
   
> [!NOTE]
> L'opzione di residenza dei dati e la disponibilità per spostare i dati dei clienti nel nuovo Geo, non è un valore predefinito per ogni nuovo Geo che lanceremo. Man mano che si espande nel nuovo GEOS in futuro, si valuterà la disponibilità e le condizioni di spostamento dei dati su base geografica geografica. 
  
I nuovi clienti o i tenant di Office 365 creati dopo la disponibilità del nuovo datacenter Geo avranno i dati di base dei clienti archiviati a riposo nel nuovo datacenter Geo automaticamente.
  
Un elenco completo di tutti i datacenter GEOS, Datacenter e la posizione dei dati del cliente a riposo è disponibile come parte delle [mappe](https://office.com/datamaps)dei datacenter interattivi. 
  
## <a name="data-residency-option"></a>Opzione di residenza dei dati

È disponibile un'opzione di data Residency per i clienti di Office 365 esistenti che sono coperti dal centro dati GEOS elencato nella tabella precedente. Con questa opzione, i clienti con requisiti di residenza dei dati possono richiedere di spostare i dati di base dei clienti nel nuovo Geo. Si consiglia ai clienti di non intraprendere alcuna azione, a meno che l'organizzazione non necessiti di dati di base dei clienti per essere archiviati a riposo nelle rispettive nuove datacenter Geo. Scegliendo di spostare i dati, i clienti limitano le possibilità di Microsoft di ottimizzare la posizione dei dati del cliente di base a riposo nell'ambiente geografico corrente o nel nuovo datacenter Geo. Come clienti in uno qualsiasi di questi due GEOS, si verificheranno gli stessi controlli di qualità dei servizi, delle prestazioni e della sicurezza come in precedenza.
  
I clienti che hanno la necessità di spostare i dati di base nel nuovo geografico con una scadenza impegnata dalla richiesta Microsoft devono essere spostati all'interno di una finestra di registrazione impostata.  Esaminare la pagina [come richiedere lo spostamento dei dati](request-your-data-move.md) per ulteriori informazioni sulla finestra di registrazione per la propria Geo e la procedura da eseguire per iscriversi al programma.  Gli spostamenti di dati possono richiedere fino a 24 mesi dopo il completamento del periodo di richieste.

- La mancata esecuzione dei risultati di azione in Microsoft è in grado di spostare i dati dei clienti di base a riposo nel nuovo Data Center Geo nel tempo come parte della gestione e dell'ottimizzazione del servizio.I dati di csutomer di base possono essere spostati solo sul nuovo datacenter Geo, non su qualsiasi altro geografico.Gli amministratori del tenant verranno informati tramite il centro messaggi quando tale spostamento di gestione dei servizi è stato completato.
   
- Non sono presenti funzionalità esclusive, funzionalità o certificazioni di conformità con il nuovo Data Center Geo.
    
- La complessità, la precisione e la scalabilità in cui è necessario eseguire lo spostamento dei dati in un ambiente automatizzato e gestito a livello globale impediscono la condivisione quando si prevede che lo spostamento dei dati venga completato per il tenant o per qualsiasi altro tenant. I clienti riceveranno una conferma nel centro messaggi per ogni servizio di partecipazione quando il relativo spostamento dei dati è stato completato. 
    
- Gli spostamenti di dati rappresentano un'operazione del servizio back-end con un impatto minimo sugli utenti finali. Le caratteristiche che possono essere influenzate sono elencate nella pagina [durante e dopo lo spostamento dei dati](during-and-after-your-data-move.md) . Il contratto di servizio di [Microsoft Online Services (SLA, Service Level Agreement)](https://go.microsoft.com/fwlink/p/?LinkId=523897) per la disponibilità è pertanto insufficiente per consentire ai clienti di prepararsi o monitorarli durante lo spostamento. La notifica di qualsiasi manutenzione del servizio viene fatta se necessario. 
    
## <a name="related-topics"></a>Argomenti correlati 
 
[Come richiedere lo spostamento dati](request-your-data-move.md)
    
[Domande frequenti sullo spostamento dati](data-move-faq.md)
  
[Nuovo datacenter GEOS per Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Servizi di Azure in base all'area geografica](https://azure.microsoft.com/en-us/regions/)
