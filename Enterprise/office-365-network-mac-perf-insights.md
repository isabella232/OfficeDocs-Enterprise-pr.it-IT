---
title: Informazioni sulle prestazioni di rete di Office 365 (anteprima)
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
description: Informazioni sulle prestazioni di rete di Office 365 (anteprima)
ms.openlocfilehash: 2e57ffabec5b2172cb36f10135406ddda95bc1c5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106357"
---
# <a name="office-365-network-performance-insights-preview"></a>Informazioni sulle prestazioni di rete di Office 365 (anteprima)

Le pagine di Microsoft 365 Admin Center Network performance mostrano Office 365 Network Insights che possono essere utili per la progettazione di perimetri di rete per le posizioni di Office. Sono disponibili cinque informazioni specifiche sulla rete che possono essere visualizzate per ogni posizione di Office.

>[!IMPORTANT]
>Suggerimenti per le prestazioni di rete, approfondimenti e valutazioni nell'interfaccia di amministrazione di Microsoft 365 è attualmente in stato di anteprima ed è disponibile solo per i tenant di Office 365 che sono stati registrati nel programma di anteprima delle funzionalità.

## <a name="backhauled-network-egress"></a>Uscita di rete con backhauling

La distanza tra la posizione dell'utente e l'uscita di rete è maggiore di 500 miglia (800 km) e questo dovrebbe influire negativamente sulle prestazioni. L'uscita locale più vicina all'utente è consigliata.

Ciò indica che la distanza tra l'area di lavoro e l'uscita di rete è superiore a 500 miglia. La posizione di Office è identificata da una posizione del computer client offuscata e il percorso dell'uscita di rete viene identificato utilizzando l'indirizzo IP inverso nei database delle posizioni. La posizione di Office potrebbe non essere accurata se i servizi di posizione di Windows sono disabilitati nei computer. La posizione di uscita della rete potrebbe non essere accurata se le informazioni sul database degli indirizzi IP inversi non sono accurate.

I dettagli relativi a questa intuizione includono l'ubicazione dell'ufficio, la posizione di uscita della rete e la distanza tra di essi.

Per questa intuizione si consiglia l'uscita di rete più vicina alla posizione di Office in modo che la connettività possa essere instradata in maniera ottimale alla rete Microsoft su Internet e su Office 365 Service front doors. Dopo aver chiuso l'uscita di rete per gli utenti, le posizioni di Office consentono anche di migliorare le prestazioni in futuro, in quanto Microsoft espande entrambi i punti di rete di presenza e le porte anteriori del servizio Office 365 in futuro.

Questa intuizione è abbreviata in "uscita" in alcune visualizzazioni di riepilogo.

## <a name="better-performance-detected-for-customers-near-you"></a>Migliorare le prestazioni rilevate per i clienti nelle vicinanze

Poiché un numero significativo di clienti nell'area metropolitana ha prestazioni migliori rispetto agli utenti dell'organizzazione in questa posizione di ufficio.

In questo modo vengono analizzate le prestazioni aggregate dei clienti di Office 365 nella stessa città del percorso di Office.

![Prestazioni di rete relative](Media/m365-mac-perf/m365-mac-perf-relative-perf.png)

Viene calcolata la percentuale di clienti di Office 365 nella stessa città in bucket di prestazioni migliori. Se questo numero è pari al 10% di più, viene visualizzato l'Insight sulla rete.

Questa intuizione è abbreviata in "peer" in alcune visualizzazioni di riepilogo.

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a>Utilizzo di una porta anteriore del servizio Exchange Online non ottimale

L'utente non è connesso a un'ottima porta di servizio di Office 365 e questo dovrebbe influire negativamente sulle prestazioni.

Vengono elencate le porte anteriori del servizio Exchange Online che sono adatte per l'utilizzo da parte di Office location City con buone prestazioni. Se il test corrente Mostra l'utilizzo di una porta di ingresso del servizio Exchange Online non presente nell'elenco, verrà chiamato questo suggerimento.

L'utilizzo di una porta anteriore del servizio Exchange Online non ottimale può essere causato da un backhaul della rete prima dell'uscita della rete aziendale, nel qual caso è consigliabile l'uscita di rete locale e diretta. Potrebbe anche essere causato dall'utilizzo di un server resolver DNS ricorsivo remoto, nel qual caso si consiglia di allineare il server resolver ricorsivo DNS con l'uscita di rete.

Questa intuizione è abbreviata in "routing" in alcune visualizzazioni di riepilogo.

## <a name="use-of-non-optimal-sharepoint-online-service-front-door"></a>Utilizzo di porta anteriore del servizio SharePoint Online non ottimale

L'utente non si connette al portale principale del servizio SharePoint Online più vicino. Questo dovrebbe influire sulle prestazioni.

Identificare la porta di ingresso del servizio SharePoint Online a cui si connette il client di test. Quindi, per la città Ubicazione di Office, viene confrontato con il servizio SharePoint Online previsto per la città. In caso contrario, è consigliabile eseguire questa operazione.

Questa intuizione è abbreviata in "AFD" in alcune visualizzazioni di riepilogo.

## <a name="low-download-speed-from-sharepoint-front-door"></a>Velocità di download bassa dalla porta di ingresso di SharePoint

È stata rilevata una velocità di download di rete ottimale che ha un impatto sul tempo necessario per caricare i documenti da OneDrive for business.

La velocità di download che un utente può ottenere dalle porte frontali di servizio di SharePoint Online e OneDrive for business è misurata in megabyte al secondo (MBps). Se questo valore è inferiore a 1 MBps, verrà fornita questa panoramica.

Per migliorare la velocità di download, potrebbe essere necessario aumentare la larghezza di banda di un utente. In alternativa, è possibile che vi sia una congestione della rete tra i computer degli utenti nell'ubicazione dell'ufficio e la porta di servizio di SharePoint Online. A volte viene chiamato perdita congestizia e limita la velocità di download disponibile per gli utenti anche se è disponibile una larghezza di banda sufficiente.

Questa intuizione è abbreviata come "velocità effettiva" in alcune visualizzazioni di riepilogo.

## <a name="related-topics"></a>Argomenti correlati

[Suggerimenti relativi alle prestazioni di rete nell'interfaccia di amministrazione di Microsoft 365 (anteprima)](office-365-network-mac-perf-overview.md)

[Valutazione della rete di Office 365 (Preview)](office-365-network-mac-perf-score.md)

[Strumento di onboarding di rete di Office 365 nell'interfaccia di amministrazione di M365 (anteprima)](office-365-network-mac-perf-onboarding-tool.md)
