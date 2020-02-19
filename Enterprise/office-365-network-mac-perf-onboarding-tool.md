---
title: Strumento di onboarding di rete di Office 365 nell'interfaccia di amministrazione di M365 (anteprima)
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
description: Strumento di onboarding di rete di Office 365 nell'interfaccia di amministrazione di M365 (anteprima)
ms.openlocfilehash: 7ead201d78c1a6ce971c6ff09d4be9c0d2c76be6
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106352"
---
# <a name="office-365-network-onboarding-tool-in-the-m365-admin-center-preview"></a>Strumento di onboarding di rete di Office 365 nell'interfaccia di amministrazione di M365 (anteprima)

Lo strumento di onboarding di rete di Office 365 <https://connectivity.office.com>è disponibile all'indirizzo. Si tratta di uno strumento aggiunto alle informazioni sulla rete e sui punteggi di rete disponibili nell'interfaccia di amministrazione di Microsoft 365 nell'area **integrità | Menu prestazioni di rete** .

Le informazioni sulla rete nell'interfaccia di amministrazione di Microsoft 365 si basano sulle misure del prodotto per il tenant di Office 365. In confronto, le informazioni di rete provenienti dallo strumento di onboarding di rete di Office 365 vengono eseguite localmente nello strumento. Il testing che può essere eseguito in-Product è limitato e eseguendo i test locali all'utente è possibile raccogliere più dati con conseguente approfondimento delle informazioni. Si consideri quindi che l'interfaccia di amministrazione di Microsoft 365 dimostrerà che è presente un problema di rete per l'utilizzo di Office 365 in una posizione specifica di Office. Lo strumento di onboarding di rete di Office 365 può essere utile per identificare la causa principale del problema che porta a un'azione consigliata per il miglioramento delle prestazioni della rete.

È consigliabile utilizzare questi strumenti insieme in cui è possibile valutare lo stato della qualità di rete per ogni posizione di Office nell'interfaccia di amministrazione di Microsoft 365 e trovare ulteriori specifiche dopo la distribuzione dei test basati sullo strumento di onboarding di rete di Office 365.

>[!IMPORTANT]
>Suggerimenti per le prestazioni di rete, approfondimenti e valutazioni nell'interfaccia di amministrazione di Microsoft 365 è attualmente in stato di anteprima ed è disponibile solo per i tenant di Office 365 che sono stati registrati nel programma di anteprima delle funzionalità.

## <a name="the-advanced-tests-client-application"></a>Applicazione client test avanzati

Sono disponibili due parti per lo strumento di onboarding di rete di Office 365. È disponibile il sito <https://connectivity.office.com> Web ed è disponibile un'applicazione client Windows scaricabile. Il client scaricabile esegue test di connettività di rete avanzati e la maggior parte dei test richiede l'esecuzione di questa operazione.

È possibile eseguire il test client avanzato dal sito Web e i risultati vengono inseriti di nuovo nella pagina Web durante l'esecuzione.

![Esempi di test di O365 di rete di onboarding](Media/m365-mac-perf/m365-mac-perf-onboarding-tool-tests.png)

## <a name="user-office-location"></a>Posizione dell'ufficio per gli utenti

La posizione dell'ufficio dell'utente viene rilevata dal Web browser utenti. Viene utilizzato per identificare la distanza di rete verso parti specifiche del perimetro della rete aziendale.

La posizione dell'ufficio utente è visualizzata nella visualizzazione mappa.

## <a name="distance-to-the-network-egress-location"></a>Distanza dalla posizione di uscita di rete

Identifichiamo l'indirizzo IP dell'uscita di rete sul server. I database delle posizioni vengono utilizzati per cercare il percorso approssimativo per l'uscita di rete e determinare la distanza tra tale percorso e l'ubicazione dell'ufficio. Questo viene visualizzato come Insight di rete se la distanza è maggiore di 500 miglia (800 km).

Il percorso di uscita della rete è visualizzato sulla visualizzazione mappa e connesso alla posizione dell'ufficio utenti che indica il backhaul della rete all'interno della WAN aziendale.

La posizione individuata dall'indirizzo IP della rete di uscita potrebbe non essere accurata e ciò porterebbe a un falso risultato di questo test. Per convalidare se questo errore si verifica per uno specifico indirizzo IP, è possibile utilizzare siti Web di indirizzi IP di rete accessibili pubblicamente.

Per la connettività di rete di Office 365 è consigliabile implementare l'uscita di rete locale e diretta dalle posizioni degli utenti di Office a Internet. I miglioramenti apportati alle funzionalità di uscita locali e dirette sono il modo migliore per gestire questa panoramica della rete.

## <a name="exchange-online-service-front-door"></a>Sportello anteriore del servizio Exchange Online

La porta anteriore del servizio Exchange online in uso viene identificata nello stesso modo in cui viene utilizzata da Outlook e viene misurata la latenza TCP di rete dalla posizione dell'ufficio dell'utente. Sono entrambi visualizzati e la porta anteriore del servizio Exchange online in uso viene confrontata con l'elenco delle porte frontali dei servizi ottimali consigliate per la posizione corrente. Questo viene visualizzato come una panoramica della rete se è in uso un portello anteriore del servizio Exchange Online non ottimale.

L'utilizzo di una porta anteriore del servizio Exchange Online non ottimale può essere causato da un backhaul della rete prima dell'uscita della rete aziendale, nel qual caso è consigliabile l'uscita di rete locale e diretta. Potrebbe anche essere causato dall'utilizzo di un server resolver DNS ricorsivo remoto, nel qual caso si consiglia di allineare il server resolver ricorsivo DNS con l'uscita di rete.

Viene calcolato un potenziale miglioramento della latenza TCP per il servizio Exchange Online. Per eseguire questa operazione, è possibile esaminare la latenza della rete del percorso dell'utente di Office e sottrarre la latenza di rete dal percorso corrente allo sportello principale del servizio di Exchange Online closes. La differenza rappresenta la possibilità di miglioramento.

## <a name="comparison-of-performance-of-customers-in-the-area"></a>Confronto delle prestazioni dei clienti nell'area

La latenza TCP di rete del percorso dell'utente di Office per il servizio Exchange Online porta anteriore viene confrontata con altri clienti di Office 365 nella stessa area metropolitana. Se il 10% o più clienti della stessa area metropolitana hanno prestazioni migliori, viene visualizzata una panoramica della rete.

Questo Network Insight è generato sulla base del fatto che tutti gli utenti di una città abbiano accesso alla stessa infrastruttura di telecomunicazioni e alla stessa vicinanza ai circuiti Internet e alla rete di Microsoft.

## <a name="in-use-default-gateway"></a>In USA gateway predefinito

Il gateway predefinito in uso è il router configurato dal client di test per il routing delle connessioni di rete TCP/IP.

Questa operazione viene fornita solo per informazioni e non contribuisce a qualsiasi analisi di rete.

## <a name="in-use-dns-servers"></a>In Use DNS Server (s)

In questo modo viene visualizzato il server DNS configurato nel computer client in cui sono stati eseguiti i test. Potrebbe trattarsi di un server resolver ricorsivo DNS che tuttavia non è comune. È più probabile che sia un server di inoltro DNS che memorizza nella cache i risultati DNS e inoltra tutte le richieste DNS non memorizzate nella cache a un altro server DNS.

Questa operazione viene fornita solo per informazioni e non contribuisce a qualsiasi analisi di rete.

## <a name="identified-dns-recursive-resolver-server"></a>Server resolver ricorsivo DNS identificato

Il sistema di risoluzione ricorsivo DNS in uso viene identificato facendo una richiesta DNS specifica e quindi chiedendo al server dei nomi DNS l'indirizzo IP da cui ha ricevuto la stessa richiesta. Questo indirizzo IP è il sistema di risoluzione ricorsivo DNS che verrà cercato nei database delle posizioni degli indirizzi IP per individuare il percorso. Viene quindi calcolata la distanza tra il percorso dell'utente e il percorso del server resolver ricorsivo DNS. Questo viene visualizzato come Insight di rete se la distanza è maggiore di 500 miglia (800 km).

La posizione individuata dall'indirizzo IP della rete di uscita potrebbe non essere accurata e ciò porterebbe a un falso risultato di questo test. Per convalidare se questo errore si verifica per uno specifico indirizzo IP, è possibile utilizzare siti Web di indirizzi IP di rete accessibili pubblicamente.

Questo Network Insight avrà un impatto specifico sulla selezione del servizio Exchange Online. Per risolvere questo Insight l'uscita di rete locale e diretta dovrebbe essere un prerequisito e quindi il sistema di risoluzione ricorsivo DNS deve trovarsi vicino all'uscita di rete.

## <a name="dns-lookup-of-exchange-online-front-end-server-and-sharepoint-online-front-end-server"></a>Ricerca DNS di Exchange Online front end server e SharePoint Online front end server

Questi mostrano il record DNS per il servizio porta di ingresso per i due carichi di lavoro di Office 365. Sono disponibili solo per informazioni e non è disponibile un'analisi di rete associata.

## <a name="proxy-server-identification"></a>Identificazione del server proxy

Vengono identificati i server proxy configurati nel computer locale. Si identifica se una di queste impostazioni è configurata nel percorso di rete per ottimizzare il traffico di rete di Office 365. È possibile identificare la distanza tra la posizione dell'ufficio utente e i server proxy. La distanza viene testata prima dal ping ICMP e, in caso di esito negativo, viene testato con il ping TCP e, infine, se si verifica un errore, si cerca l'indirizzo IP del server proxy in un database del percorso dell'indirizzo IP. Viene visualizzata una panoramica della rete se il server proxy è oltre 500 miglia (800 km) dalla posizione dell'ufficio utenti.

## <a name="media-quality-checks"></a>Controlli qualità multimediale

Questo test consente di installare ed eseguire lo strumento di valutazione della rete di Skype for business e di interpretare i risultati. Lo strumento può essere trovato in [https://www.microsoft.com/download/details.aspx?id=53885](https://www.microsoft.com/download/details.aspx?id=53885).

Questi sono i test del protocollo UDP usati da Microsoft teams audio and video call and Conferencing funzionalità. Testiamo per la perdita di pacchetti UDP, la latenza della rete UDP, il tremolio UDP e il riordino dei pacchetti UDP. Se uno di questi valori è compreso nell'intervallo consentito, viene visualizzata una panoramica della rete.

## <a name="tcp-connectivity-tests"></a>Test di connettività TCP

Testiamo la connettività HTTP dalla posizione dell'ufficio utenti a tutti gli endpoint di rete di Office 365 necessari. Questi sono pubblicati su [https://aka.ms/o365ip](https://aka.ms/o365ip). Viene visualizzata una panoramica della rete per tutti gli endpoint di rete necessari che non possono essere connessi.

La connettività ay deve essere bloccata da un server proxy, un firewall o un altro dispositivo di sicurezza di rete nel perimetro della rete aziendale o in uso come proxy cloud.

## <a name="ssl-interception-tests"></a>Test di intercettazione SSL

Testiamo il certificato SSL a ogni endpoint di rete di Office 365 obbligatorio che si trova nella categoria ottimizza o Consenti come [https://aka.ms/o365ip](https://aka.ms/o365ip)definito in. Se i test non trovano un certificato SSL Microsoft, è necessario che la rete crittografata connessa sia stata intercettata da un dispositivo di rete intermediario. Un'analisi di rete viene visualizzata su tutti gli endpoint di rete crittografati intercettati.

Quando viene rilevato un certificato SSL non fornito da Microsoft, viene visualizzato il nome di dominio completo per il test e il proprietario del certificato SSL in uso. Questo proprietario del certificato SSL può essere un fornitore del server proxy oppure un certificato autofirmato Enterprise.

## <a name="network-path-diagnostics"></a>Diagnostica percorso di rete

In questa sezione vengono illustrati i risultati di un traceroute ICMP per il servizio Exchange Online, la porta di ingresso del servizio SharePoint Online e il servizio Microsoft teams front door. Viene fornito solo per informazioni e non è presente un'analisi di rete associata.

## <a name="related-topics"></a>Argomenti correlati

[Suggerimenti relativi alle prestazioni di rete nell'interfaccia di amministrazione di Microsoft 365 (anteprima)](office-365-network-mac-perf-overview.md)

[Informazioni sulle prestazioni di rete di Office 365 (anteprima)](office-365-network-mac-perf-insights.md)

[Valutazione della rete di Office 365 (Preview)](office-365-network-mac-perf-score.md)
