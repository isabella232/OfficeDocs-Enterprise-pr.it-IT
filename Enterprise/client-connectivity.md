---
title: Connettività dei client
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: 'Riepilogo: in questo articolo viene illustrato in che modo i computer client si connettono ai tenant di Office 365, a seconda della posizione del computer client e del datacenter tenant di Office 365.'
ms.openlocfilehash: d101af5a0fdd4e29e366b34ad1ab682489f6b3ca
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068202"
---
# <a name="client-connectivity"></a>Connettività dei client

 **Riepilogo:** Viene illustrato il modo in cui i computer client si connettono ai tenant di Office 365, a seconda della posizione del computer client e del datacenter tenant di Office 365.
  
Office 365 risiede nei Data Center Microsoft di tutto il mondo che consentono di mantenere il servizio attivo e funzionante anche quando si verifica un problema importante in un'area, ad esempio un terremoto o un'interruzione di corrente. Quando si esegue la connessione al tenant di Office 365, la connessione client verrà indirizzata al centro dati appropriato in cui è ospitato il tenant. Le regole che determinano la posizione in cui il tenant può essere ospitato sono definite dal contratto con Microsoft. Le regole che determinano il modo in cui il client acquisisce i dati provenienti da tale percorso dipendono dall'architettura del servizio che si sta utilizzando.
  
Ad esempio, quando si accede al portale di Office 365, si è in genere connessi al data center più vicino al client e quindi si è diretti a seconda del servizio che si utilizza successivamente. Se si avvia il messaggio di posta elettronica, la connessione iniziale per la visualizzazione dell'interfaccia utente potrebbe provenire dal Data Center più vicino, ma potrebbe essere aperta una seconda connessione tra il centro dati più vicino e il centro dati in cui si trova il tenant per visualizzare i messaggi di posta elettronica letti. Microsoft gestisce una delle prime dieci reti nel mondo, con conseguente incredibilmente veloce connessioni datacenter-to-datacenter.
  
Dopo aver letto l'articolo, è probabile che sia possibile capire perché non si forniscono gli [URL di Office 365 e gli intervalli di indirizzi IP](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) per datacenter, ma sono troppo interconnessi e si affidano l'uno all'altro per renderlo possibile.
  
Se si utilizza Azure ExpressRoute per Office 365, nella maggior parte dei casi la connettività passerà a una connessione privata a Office 365 anziché alla connessione pubblica descritta in questo articolo. I principi sul modo in cui i client si connettono sono ancora accurati. Per ulteriori informazioni, vedere [Azure ExpressRoute per Office 365](azure-expressroute.md).
  
Per ulteriori informazioni sulle richieste di rete di Skype for business, leggere l'articolo [qualità multimediale e prestazioni della connettività di rete in Skype for business online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).

||
|:-----|
| Questo articolo fa parte della [pianificazione della rete e dell'ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune).|

> [!NOTE]
> È importante gestire i dati dei clienti in modo che siano sicuri e privati nei datacenter. I dettagli sulla procedura da eseguire per gestire la privacy sono inclusi nel [Centro protezione](https://go.microsoft.com/fwlink/?LinkID=397383).
  
## <a name="connecting-to-the-nearest-datacenter"></a>Connessione al datacenter più vicino

Questo è il tipo di connessione più comune e viene utilizzato sia dal portale di Office 365 sia da Exchange Online. In questa situazione, quando i client tentano di connettersi a Office 365, la query DNS del computer determina l'area geografica in cui viene il computer e Office 365 reindirizza la richiesta al centro dati più vicino.
  
Le connessioni al portale si arrestano nel centro dati più vicino e al computer client vengono fornite informazioni sul tenant del client da tale posizione.
  
Exchange Online fa un passo avanti. Una volta che il computer client è connesso al centro dati più vicino, un server di Exchange in quel centro dati si connette al centro dati in cui si trova il tenant, come illustrato nella sezione in che *modo funziona in questo articolo* . I server Exchange Online nel datacenter più vicino quindi proxy le richieste dal computer client al server cassette postali. Questo velocizza l'esperienza del computer client spostando il sollevamento di carichi di posta elettronica e gli elementi del calendario nella rete Microsoft.
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a>Come funziona per le offerte cloud standard?

Questo processo di connessione è standard per le applicazioni Web ad alto traffico, ad alto valore come Office 365. In questa sezione sono specificati ed illustrati i passaggi di questo processo. Quando il computer client non si trova nella stessa area del tenant, la connessione sembra molto diversa a seconda del servizio a cui si connette il client.
  
 Questo diagramma rappresenta un cliente che utilizza una versione standard di Office 365 con un tenant in Nord America. In questo scenario, la persona che effettua la richiesta ha viaggiato in Europa e utilizza Office 365 da tale posizione.
  
1. Il computer client chiede ai server DNS locali l'indirizzo IP associato a Office 365.

2. I server DNS locali del computer client richiedono ai server DNS Microsoft l'indirizzo IP associato a Office 365.

3. I server DNS Microsoft restituiscono il nome del server regionale (basato sulla posizione dei server DNS del client) e il computer client ripete i passaggi 1 e 2 per ottenere l'indirizzo IP del datacenter di Office 365 regionale.

4. Il computer client si connette all'indirizzo IP del datacenter internazionale.

5. I server Exchange Online stabiliscono una connessione al datacenter attivo in cui risiede il tenant del cliente.

![Data center regionale più vicino](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a>Come funziona l'offerta di Sovereign cloud?

Questa connessione è leggermente diversa per le offerte di cloud Sovereign, come Office 365 gestito da 21 Viani. Con il tenant in un'istanza Sovereign di Office 365, i server Office 365 più vicini che accetteranno le connessioni al portale sono i server all'interno dell'area Sovereign in cui risiede il tenant. Analogamente, i clienti che accedono a SharePoint Online nel cloud Sovereign o nelle offerte standard verranno indirizzati ai Front End Server in cui risiede il tenant. Per ulteriori informazioni, vedere Connecting to the Active datacenter.
  
1. Il computer client chiede ai server DNS locali l'indirizzo IP associato a Office 365.

2. I server DNS locali del computer client richiedono ai server DNS Microsoft l'indirizzo IP associato a Office 365.

3. I server DNS Microsoft restituiscono il nome del server regionale (basato sulla posizione dei server DNS del client) e il computer client ripete i passaggi 1 e 2 per ottenere l'indirizzo IP del datacenter di Office 365 regionale.

4. Il computer client si connette all'indirizzo IP del datacenter internazionale.

5. I server Exchange Online stabiliscono una connessione al datacenter attivo in cui risiede il tenant del cliente.

![Data center statunitense regionale più vicino](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a>Connessione al datacenter attivo

La connessione al datacenter attivo è progettata per carichi di lavoro di trasferimento dei dati più pesanti ed è attualmente utilizzata da SharePoint Online. In questa situazione, quando i client tentano di connettersi a Office 365, il browser viene reindirizzato al data center attivo per il tenant di SharePoint Online.
  
## <a name="how-does-this-work"></a>Funzionamento.

Quando il computer client si connette a SharePoint Online da un'area diversa, la connessione è reindirizzata al datacenter di SharePoint Online attivo. In questo scenario, il cliente utilizza un'offerta standard, risultando che le connessioni del portale siano rimaste locali e che le connessioni di SharePoint Online vengano indirizzate al data center attivo.
  
1. Il computer client chiede ai server DNS locali l'indirizzo IP associato a Office 365.

2. I server DNS locali del computer client richiedono ai server DNS Microsoft l'indirizzo IP associato a Office 365.

3. I server DNS Microsoft restituiscono il nome del server del datacenter di SharePoint Online attivo (in base alla posizione del tenant di Office 365 del client) e il computer client ripete i passaggi 1 e 2 per ottenere l'indirizzo IP del datacenter di Office 365 attivo.

4. Il computer client si connette all'indirizzo IP del datacenter attivo.

![Data center statunitense attivo](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a>Connessione tramite reti virtuali private (VPN)

Questo tipo di connessione si applica solo quando il client utilizza una rete virtuale privata (VPN). In realtà, il comportamento di Office 365 non viene modificato semplicemente perché viene utilizzata una VPN, ma le VPN vengono in genere utilizzate per controllare il modo in cui i computer client stabiliscono le connessioni a Office 365 e di solito risultano in un'esperienza degradata, quindi è importante coprirla.
  
## <a name="how-does-this-work"></a>Funzionamento.

Quando il computer client stabilisce una connessione VPN a una sede aziendale in un'area geografica diversa, vengono utilizzati i server DNS di tale ufficio anziché i server DNS nel percorso del computer client. Nella maggior parte dei casi, questa connessione aggiuntiva sulla VPN degraderà l'esperienza di Office 365. I servizi di Office 365 sono ottimizzati per il servizio delle connessioni dei clienti il più vicino possibile all'utente finale. Molti servizi sfruttano la rete Edge di Azure, le reti di distribuzione del contenuto e la capacità di rete affidabile sulla rete Microsoft per offrire la migliore esperienza utente possibile quando le richieste di rete per i servizi di Office 365 sono eseguite come vicino al computer client. possibile.
  
1. Il computer client chiede ai server DNS VPN l'indirizzo IP associato a Office 365.

2. I server DNS VPN del computer client chiedono ai server DNS Microsoft l'indirizzo IP associato a Office 365.

3. I server DNS Microsoft restituiscono il nome del server regionale (basato sulla posizione dei server DNS VPN) e il computer client ripete i passaggi 1 e 2 per ottenere le informazioni sull'indirizzo IP del datacenter di Office 365 regionale.

4. Il computer client si connette all'indirizzo IP del datacenter più vicino all'ufficio aziendale con cui ha stabilito una connessione VPN.

![Connettività data center VPN](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
Ecco un collegamento breve per tornare alla pagina: [https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)
  
## <a name="see-also"></a>Vedere anche

[Gestione degli endpoint di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Connettività di rete con Office 365](network-connectivity.md)
