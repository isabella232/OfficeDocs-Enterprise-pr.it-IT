---
title: Suggerimenti relativi alle prestazioni di rete nell'interfaccia di amministrazione di Microsoft 365 (anteprima)
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
description: Panoramica delle raccomandazioni relative alle prestazioni di rete nell'interfaccia di amministrazione di Microsoft 365 (anteprima)
ms.openlocfilehash: d944814effc62956d5047bad1f3088d0919793ee
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106351"
---
# <a name="network-performance-recommendations-in-the-microsoft-365-admin-center-preview"></a>Suggerimenti relativi alle prestazioni di rete nell'interfaccia di amministrazione di Microsoft 365 (anteprima)

La pagina prestazioni di rete nell'interfaccia di amministrazione di Microsoft 365 Mostra informazioni di rete e un punteggio di rete per i clienti aziendali. Le informazioni sulla rete sono modifiche specifiche dell'architettura di rete consigliate per migliorare l'esperienza degli utenti in relazione alla connettività di rete a Office 365 e il Punteggio di rete dimostra come la connettività di rete influisce sull'esperienza utente che consente il confronto tra connessioni di rete diverse per la posizione degli utenti. Le aziende che utilizzano Office 365 con più percorsi di Office e architetture perimetrali di rete non banali possono trarre vantaggio da questa operazione durante l'onboarding iniziale in Office 365 o per correggere i problemi di prestazioni della rete individuati con l'utilizzo crescita. In genere non è necessario per le aziende di piccole dimensioni che utilizzano Office 365 o per le aziende che dispongono già di connettività di rete semplice e diretta. Le aziende con oltre 500 utenti e più sedi di Office dovrebbero avvantaggiarsi al massimo.

>[!IMPORTANT]
>Suggerimenti per le prestazioni di rete, approfondimenti e valutazioni nell'interfaccia di amministrazione di Microsoft 365 è attualmente in stato di anteprima ed è disponibile solo per i tenant di Office 365 che sono stati registrati nel programma di anteprima delle funzionalità.

## <a name="enterprise-network-connectivity-challenges"></a>Problemi relativi alla connettività di rete aziendale

![Rete del cliente per il cloud](Media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

Molte aziende dispongono di configurazioni perimetrali di rete che sono cresciute nel tempo e sono progettate principalmente per ospitare l'accesso ai siti Web di un dipendente, in cui la maggior parte dei siti Web non è nota in anticipo e non è attendibile. Lo stato attivo prevalente e necessario è evitare attacchi di malware e di pesca da questi siti web sconosciuti. Questa strategia di configurazione della rete, sebbene utile per motivi di sicurezza, può comportare un peggioramento delle prestazioni dell'utente e dell'esperienza utente di Office 365. Le aziende possono migliorare l'esperienza degli utenti, ma anche continuare a proteggere l'ambiente seguendo i [principi di connettività di Office 365](https://aka.ms/pnc) e, a breve, utilizzando la nuova funzionalità di prestazioni di rete di interfaccia di amministrazione di Microsoft 365. Questa funzionalità contribuisce alla progettazione dell'architettura di rete che si allinea con i principi di connettività di Office 365 e dovrebbe portare a prestazioni di rete ottimizzate per la connettività a Office 365.

## <a name="how-we-can-solve-these-challenges"></a>Come risolvere queste sfide

A volte viene chiesto a Microsoft di esaminare i problemi relativi alle prestazioni di rete con Office 365 per i clienti di grandi dimensioni e spesso presentano una causa principale relativa all'infrastruttura di uscita della rete dei clienti. Quando viene trovata una causa principale comune di un problema di perimetro della rete del cliente, si cerca di identificare le misure di test semplici che lo identificano. Un test con una soglia di misurazione che identifica un problema specifico è importante perché è possibile testare la stessa misura in qualsiasi posizione, stabilire se questa causa principale è presente e condividerla come Insight di rete con l'amministratore. Alcune informazioni di rete indicano solo un problema che richiede ulteriori indagini. Un'analisi di rete in cui sono disponibili test sufficienti per visualizzare un'azione di correzione specifica per correggere la causa principale è elencata come azione consigliata. Queste informazioni sulla rete basate su misure precedenti a una soglia predeterminata sono molto più importanti dei consigli generali di Best practice, poiché non è necessario chiedere se si applicano determinate procedure consigliate e si verificherà un miglioramento significativo dell'esperienza utente .

## <a name="network-performance-overview-in-the-microsoft-365-admin-center"></a>Panoramica delle prestazioni di rete nell'interfaccia di amministrazione di Microsoft 365

Microsoft dispone di misure di rete esistenti incluse in numerosi client desktop e Web Office che supportano il funzionamento di Office 365. Queste misure vengono ora utilizzate per fornire informazioni sulla progettazione dell'architettura di rete e un punteggio delle prestazioni di rete, visualizzato nella pagina prestazioni di rete dell'interfaccia di amministrazione di Microsoft 365.

Le informazioni sulla posizione approssimative associate alle misure di rete possono identificare la città in cui si trovano i dispositivi client. Viene utilizzato per visualizzare i percorsi di Office dei clienti e le misure di rete sono raggruppati per fornire informazioni di rete per il percorso di Office. Il Punteggio di rete in ogni percorso viene visualizzato con il colore e il numero relativo di utenti in ogni posizione è rappresentato dalle dimensioni del cerchio. La pagina Panoramica Visualizza anche il Punteggio di rete per il cliente come media ponderata in tutte le posizioni di Office.

## <a name="specific-office-location-network-performance-summary-and-insights"></a>Riepilogo e informazioni dettagliate sulle prestazioni di una rete di Office location

Se si seleziona un percorso di Office, verrà aperta una pagina di riepilogo specifica percorso. Vengono illustrati i dettagli dell'uscita di rete identificata dalle misure per il percorso di Office.

La pagina di riepilogo dell'ubicazione di Office consente inoltre di visualizzare le posizioni network score, la cronologia dei punteggi di rete, un confronto tra i punti di vista di questo percorso e gli altri clienti nella stessa città, nonché un elenco di informazioni e suggerimenti specifici che il cliente può intraprendere per migliorare la connettività di rete. I confronti tra clienti nella stessa città si basano sull'aspettativa che tutti i clienti abbiano uguale accesso ai provider di servizi di rete, all'infrastruttura di telecomunicazioni e ai punti di presenza della rete Microsoft nelle vicinanze.

Nella scheda Dettagli della pagina percorso di Office sono riportati i risultati di misura specifici che sono stati utilizzati per fornire informazioni dettagliate, suggerimenti e Punteggio di rete. Questo viene fornito in modo che gli ingegneri di rete possano convalidare le raccomandazioni e il fattore in qualsiasi vincolo o specifiche nel proprio ambiente.
Per i clienti che desiderano migliorare l'accuratezza delle posizioni di Office e le raccomandazioni fornite, è possibile immettere informazioni più specifiche. A tale scopo, è possibile modificare le informazioni sulla posizione individuate e ridurre le approssimazioni inerenti alle informazioni sulla posizione disponibili per le misure di rete.

## <a name="faq"></a>Domande frequenti

### <a name="what-is-office-365-service-front-door"></a>Che cos'è Office 365 Service front door?

La porta principale del servizio Office 365 è un punto di ingresso sulla rete globale di Microsoft in cui i client e i servizi di Office terminano la connessione di rete. Per una connessione di rete ottimale a Office 365, è consigliabile che la connessione di rete venga terminata nella porta principale più vicina di Office 365 nella propria città o nella metropolitana.
Nota: Office 365 Service front door non ha alcuna relazione diretta con il prodotto "Azure front door Service" disponibile in Azure Marketplace.

### <a name="what-is-an-optimal-office-365-service-front-door"></a>Che cos'è un'ottima porta di servizio di Office 365?

Un'ottima porta di servizio di Office 365 è quella più vicina all'uscita di rete, in genere nella propria area urbana o metropolitana. Utilizzare lo strumento di prestazioni di rete di Office 365 per determinare la posizione del servizio di assistenza in uso di Office 365 e la porta anteriore del servizio ottimale. Se lo strumento determina che la porta principale in uso è ottimale, è possibile connettersi in modo ottimale alla rete globale di Microsoft.

### <a name="what-is-an-internet-egress-location"></a>Che cos'è un percorso di uscita Internet?

La posizione di uscita Internet è il percorso in cui il traffico di rete esce dalla rete aziendale e si connette a Internet. Questo è anche identificato come il percorso in cui si dispone di un dispositivo NAT (Network Address Translation) e in genere dove si è connessi con un provider di servizi Internet (ISP). Se si vede una distanza interurbana tra la posizione e la posizione di uscita Internet, potrebbe essere possibile identificare una significativa backhaul WAN.

## <a name="related-topics"></a>Argomenti correlati

[Informazioni sulle prestazioni di rete di Office 365 (anteprima)](office-365-network-mac-perf-insights.md)

[Valutazione della rete di Office 365 (Preview)](office-365-network-mac-perf-score.md)

[Strumento di onboarding di rete di Office 365 nell'interfaccia di amministrazione di M365 (anteprima)](office-365-network-mac-perf-onboarding-tool.md)
