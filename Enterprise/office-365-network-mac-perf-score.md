---
title: Valutazione della rete di Office 365 (Preview)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Valutazione della rete di Office 365 (Preview)
ms.openlocfilehash: f919eeb2771095502865b4a5079b91eb8d7efe36
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106350"
---
# <a name="office-365-network-assessment-preview"></a>Valutazione della rete di Office 365 (Preview)

La valutazione della rete di Office 365 indica l'impatto dell'esperienza utente relativa dalla connettività di rete del cliente. L'impatto di qualsiasi connettività di rete di Microsoft è escluso da questo per consentire ai clienti di ottimizzare le progettazioni di rete per le quali sono responsabili.

Viene calcolato in base alle misure che influiscono sull'esperienza degli utenti nei carichi di lavoro chiave di Office 365 e che vengono visualizzate come percentuali con un intervallo compreso tra 0 e 100.

Un punteggio di rete molto basso suggerisce che i client di Office 365 avranno problemi significativi per la connessione o il reattivo degli utenti. Un punteggio di 80% rappresenta la connettività di rete in cui non è consigliabile ricevere reclami da parte dell'utente sull'esperienza utente di Office 365 a causa delle prestazioni di rete. Man mano che vengono apportati miglioramenti alla connettività di rete, questo punteggio aumenterà insieme all'esperienza utente.

>[!IMPORTANT]
>Suggerimenti per le prestazioni di rete, approfondimenti e valutazioni nell'interfaccia di amministrazione di Microsoft 365 è attualmente in stato di anteprima ed è disponibile solo per i tenant di Office 365 che sono stati registrati nel programma di anteprima delle funzionalità.

## <a name="exchange-online"></a>Exchange Online

Per Exchange Online, viene misurata la latenza TCP dal computer client al front end server di Exchange. Questo può influire sulla distanza che la rete percorre nei clienti LAN e WAN. Può anche essere influenzato da dispositivi o servizi di intermediazione di rete che ritardano la connettività o causano il rimandato dei pacchetti.

## <a name="sharepoint-online"></a>SharePoint Online

Per SharePoint Online, la velocità di download disponibile per un utente per l'accesso a un documento viene misurata. Questo può essere influenzato dalla larghezza di banda disponibile nei circuiti di rete tra il computer client e la rete di Microsoft. È inoltre spesso influenzato dalla congestione della rete che esiste nei colli di bottiglia nei dispositivi di rete complessi o nelle aree Wi-Fi con una copertura scadente.

## <a name="microsoft-teams"></a>Microsoft Teams

Per Microsoft teams la qualità della rete viene misurata come latenza UDP, jitter UDP e perdita di pacchetti UDP. UDP viene utilizzato per la connettività multimediale di chiamata e di audioconferenza per Microsoft teams. Questo può influire sugli stessi fattori di latenza e velocità di download, oltre agli spazi di connettività nel supporto UDP di una rete, poiché UDP è configurato separatamente per il protocollo TCP più comune.

## <a name="tenant-network-score-and-office-location-network-score"></a>Punteggio di rete tenant e posizione di rete di Office location

Un punteggio di rete misura la progettazione del perimetro di rete di una posizione di Office alla rete di Microsoft. I miglioramenti apportati al perimetro della rete sono migliori in ogni posizione di Office o in cui è possibile aggregare la connettività di rete possono essere presenti miglioramenti che influiscono su più percorsi.
Viene visualizzato un punteggio di rete per l'intero tenant di Office 365 nella pagina Panoramica delle prestazioni di rete e uno specifico punteggio di rete per ogni posizione di Office rilevata nella pagina di riepilogo di tale percorso.

## <a name="network-score-panel"></a>Pannello Punteggio di rete

Ogni punteggio di rete se per il tenant o per una specifica posizione di Office viene visualizzato un riquadro con informazioni dettagliate sul punteggio. Questo pannello Visualizza un grafico a barre dello score sia come percentuale che come punti totali per ogni carico di lavoro del componente, compresi solo i carichi di lavoro in cui sono stati ricevuti i dati di misurazione. Per un punteggio di rete per la posizione di Office viene mostrato anche un benchmark che è il mediano di tutti i client di Office 365 che hanno segnalato dati nella stessa città del percorso dell'ufficio.

La ripartizione dei punteggi nel pannello Visualizza il punteggio per ogni carico di lavoro del componente.

La cronologia dei punteggi Visualizza gli ultimi 30 giorni dello score e del benchmark.

## <a name="related-topics"></a>Argomenti correlati

[Suggerimenti relativi alle prestazioni di rete nell'interfaccia di amministrazione di Microsoft 365 (anteprima)](office-365-network-mac-perf-overview.md)

[Informazioni sulle prestazioni di rete di Office 365 (anteprima)](office-365-network-mac-perf-insights.md)

[Strumento di onboarding di rete di Office 365 nell'interfaccia di amministrazione di M365 (anteprima)](office-365-network-mac-perf-onboarding-tool.md)
