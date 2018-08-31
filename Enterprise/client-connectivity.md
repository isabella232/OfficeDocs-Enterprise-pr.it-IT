---
title: Connettività dei client
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
ms.audience: ITPro
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
description: 'Riepilogo: Illustra la modalità di connessione dei computer client ai tenant di Office 365, in base al percorso del computer client e ai datacenter dei tenant di Office 365.'
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223038"
---
# <a name="client-connectivity"></a>Connettività dei client

 **Riepilogo:** Illustra la modalità di connessione dei computer client ai tenant di Office 365, in base al percorso del computer client e ai datacenter dei tenant di Office 365.
  
Office 365 si trova in datacenter Microsoft in tutto il mondo che assicurano il servizio di backup e in esecuzione anche quando si verifica un problema importante in un'area, ad esempio un terremoto o un'interruzione dell'alimentazione. Quando si connette al tenant di Office 365, la connessione client verrà indirizzata al datacenter appropriato ospitato tenant. Le regole che determinano dove possono essere ospitati tenant vengono definite dal contratto di licenza Microsoft. Le regole per determinare come il client acquisisce i dati da tale posizione datacenter dipendono l'architettura del servizio che si sta utilizzando.
  
Ad esempio, quando accede al portale di Office 365, in genere connessi al datacenter più vicino al client che quindi indirizzata a seconda del servizio che si utilizzano Avanti. Se si avvia posta elettronica, la connessione per visualizzare l'interfaccia utente può comunque provengono da datacenter più vicino, ma potrebbe essere aperta una connessione seconda tra datacenter più vicino e il centro dati dove si trova il tenant per mostrare a cosa si intende nei messaggi di posta elettronica è di lettura. Microsoft opera una delle dieci reti principali del mondo conseguenti estremamente fast datacenter per Data Center connessioni veloci.
  
Dopo aver letto l'articolo, è probabile che saranno comprendere perché Microsoft non fornisce [gli intervalli di indirizzi IP e gli URL di Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) per Data Center, semplicemente sono troppo interconnesse e basati su interagiscono per verificare che il realizzabile.
  
Se si utilizza ExpressRoute Azure per Office 365, nella maggior parte dei casi la connettività verrà inoltrate tramite una connessione privata a Office 365 anziché la connessione pubblica descritta di seguito. I principi sulla modalità di connessione client sono ancora precisi. Ulteriori informazioni sulle [ExpressRoute Azure per Office 365](azure-expressroute.md).
  
Per ulteriori profondità su Skype per le richieste di rete aziendale, leggere l'articolo [della qualità multimediale e le prestazioni di connettività di rete in Skype Business online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).

||
|:-----|
| In questo articolo fa parte della [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune).|

> [!NOTE]
> È necessario prestare attenzione ideale per gestire i dati dei clienti in modo da essere protette e private nei centri dati. Ulteriori informazioni sulla procedura da intraprendere per gestire la privacy vengono inclusi nel [Centro protezione](https://go.microsoft.com/fwlink/?LinkID=397383).
  
## <a name="connecting-to-the-nearest-datacenter"></a>Connessione al datacenter più vicino

Si tratta del tipo di connessione più comune e viene utilizzata per il portale di Office 365 ed Exchange Online. In questo caso, quando i client tentano di connettersi a Office 365, query DNS del proprio computer determina l'area del mondo che proviene il computer e Office 365 reindirizza la richiesta al datacenter più vicino.
  
Connessioni al portale di arrestare in datacenter più vicino e il computer client è presentato con informazioni sul tenant del client da tale posizione.
  
Exchange Online va un passaggio. Dopo che il computer client è connesso al datacenter più vicino, un server di Exchange in tale Data Center si connette al datacenter del tenant in cui effettivamente si trova come illustrato nel *in che modo il questo utilizzo sezione* sotto. Il server di Exchange Online nel più vicino datacenter quindi proxy le richieste dal computer client al server cassette postali. Ciò consente di velocizzare l'esperienza per il computer client spostando il pesante di recupero dei messaggi di posta elettronica e gli elementi del calendario di Microsoft network.
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a>Funzionamento di offerte standard cloud?

Questo processo di connessione è standard per un traffico elevato, le applicazioni web di valore elevato come Office 365. In questa sezione è sono riportati e illustrati i passaggi del processo. Quando il computer client non è incluso nella stessa area tenant, la connessione ha un aspetto molto diversa a seconda del servizio a che client si connette.
  
 In questo diagramma illustra un cliente utilizzando una soluzione Office 365 standard con un tenant in Nord America. In questo scenario, la persona che effettua la richiesta è stato trasferito per Europa e utilizza Office 365 da tale posizione.
  
1. Il computer client chiede ai server DNS locali per l'indirizzo IP associato a Office 365.

2. Server DNS locali del computer client chiedono ai server DNS Microsoft l'indirizzo IP associato a Office 365.

3. Server DNS Microsoft restituire il nome del server regionali (in base alla posizione dei server DNS del client) e il computer client ripeterà i passaggi da 1 e 2 per ottenere l'indirizzo IP del datacenter internazionale di Office 365.

4. Il computer client si connette all'indirizzo IP del datacenter internazionale.

5. Il server di Exchange Online stabilire una connessione al datacenter attivo dove risiede il tenant del cliente.

![Data center regionale più vicino](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a>Come questo tipo di lavoro per statali cloud offerte?

La connessione è leggermente diversa per le offerte sovrani cloud quali Office 365 gestito dal Vianet 21. Con il tenant in un'istanza sovrani di Office 365, i server di Office 365 più vicini che accettano connessioni del portale sono i server all'interno dell'area sovrani in cui risiede il tenant. Allo stesso modo, i clienti accesso a SharePoint Online nel nostro cloud sovrani o offerte standard verranno indirizzati ai server front-end in cui risiede il tenant. Vedere la connessione al datacenter attivo riportata di seguito.
  
1. Il computer client chiede ai server DNS locali per l'indirizzo IP associato a Office 365.

2. Server DNS locali del computer client chiedono ai server DNS Microsoft l'indirizzo IP associato a Office 365.

3. Server DNS Microsoft restituire il nome del server regionali (in base alla posizione dei server DNS del client) e il computer client ripeterà i passaggi da 1 e 2 per ottenere l'indirizzo IP del datacenter internazionale di Office 365.

4. Il computer client si connette all'indirizzo IP del datacenter internazionale.

5. Il server di Exchange Online stabilire una connessione al datacenter attivo dove risiede il tenant del cliente.

![Data center statunitense regionale più vicino](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a>Connessione al datacenter attivo

Connessione al datacenter attivo è progettata per pesanti carichi di lavoro dati trasferimento e attualmente utilizzata da SharePoint Online. In questo caso, quando i client tentano di connettersi a Office 365, il browser viene reindirizzato al datacenter attivo per il tenant di SharePoint Online.
  
## <a name="how-does-this-work"></a>Funzionamento.

Quando il computer client si connette a SharePoint Online da un'area diversa, la connessione è reindirizzata al datacenter di SharePoint Online attivo. In questo scenario si sta utilizzando uno standard che offre, causando la connessioni portale rimanente locali e le connessioni di SharePoint Online viene reindirizzate al datacenter attivo.
  
1. Il computer client chiede ai server DNS locali per l'indirizzo IP associato a Office 365.

2. Server DNS locali del computer client chiedono ai server DNS Microsoft l'indirizzo IP associato a Office 365.

3. Server DNS Microsoft restituire il nome del server di datacenter attivo SharePoint Online (in base alla posizione del tenant di Office 365 del client) e il computer client ripeterà i passaggi da 1 e 2 per ottenere l'indirizzo IP del datacenter attivo di Office 365.

4. Il computer client si connette all'indirizzo IP del datacenter attivo.

![Data center statunitense attivo](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a>Connessione tramite reti virtuali private (VPN)

Questo tipo di connessione si applica solo quando viene utilizzata una rete privata virtuale (VPN) dai computer client. In realtà, il comportamento di Office 365 non viene modificato semplicemente poiché viene utilizzata una rete VPN, ma le reti private virtuali comunemente utilizzate per controllare come computer client stabilire connessioni a Office 365 e, in genere, i risultati in un'esperienza di degradazione, pertanto, è importante specifichi.
  
## <a name="how-does-this-work"></a>Funzionamento.

Quando il computer client stabilisce una connessione VPN alla sede in un'area diversa, vengono utilizzati i server DNS in tale office anziché ai server DNS nella posizione del computer client. Nella maggior parte dei casi, la connessione tramite VPN aggiuntiva comporta un peggioramento l'esperienza di Office 365. I servizi di Office 365 sono ottimizzati per connessioni del servizio clienti come raggiungere l'utente finale possibile. Molti servizi di sfruttano la rete perimetrale Azure, reti di distribuzione del contenuto e la capacità di rete affidabile Microsoft Network per offrire un'esperienza utente ottimale quando vengono effettuate le richieste di rete di servizi di Office 365 più vicino al computer client possibile.
  
1. Il computer client chiede DNS VPN server per l'indirizzo IP associato a Office 365.

2. Server DNS VPN del computer client chiedono ai server DNS Microsoft l'indirizzo IP associato a Office 365.

3. Server DNS Microsoft restituire il nome del server regionali (in base alla posizione dei server DNS VPN) e il computer client ripeterà i passaggi da 1 e 2 per ottenere le informazioni sull'indirizzo IP del datacenter internazionale di Office 365.

4. Il computer client si connette al datacenter indirizzo IP che è più vicino all'ufficio aziendale con che cui ha stabilito una connessione.

![Connettività data center VPN](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
Questo è un collegamento breve che è possibile utilizzare il ritorno:[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)
  
## <a name="see-also"></a>Vedere anche

[Gestione di endpoint di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Connettività di rete con Office 365](network-connectivity.md)
