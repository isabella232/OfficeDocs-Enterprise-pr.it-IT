---
title: ExpressRoute per la connettività cloud Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/12/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: 'Riepilogo: informazioni su come ExpressRoute può essere di aiuto con connessioni più veloci e affidabili ai servizi cloud e alle piattaforme Microsoft.'
ms.openlocfilehash: 0bab6cf3d400293221692a595346445afd242e48
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067682"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a>ExpressRoute per la connettività cloud Microsoft

 **Riepilogo:** Informazioni su come ExpressRoute può essere di aiuto con connessioni più veloci e affidabili ai servizi cloud e alle piattaforme Microsoft.
  
ExpressRoute fornisce una connessione di rete a elevata velocità effettiva, dedicata e privata per il cloud Microsoft.
  
## <a name="expressroute-to-the-microsoft-cloud"></a>ExpressRoute al cloud Microsoft

Di seguito è indicato il percorso di rete del cloud Microsoft senza una connessione ExpressRoute.
  
**Figura 1: percorso di rete senza ExpressRoute**

![Figura 1: percorso di rete senza ExpressRoute](media/Network-Poster/ExpressRoute.png)
  
Nella figura 1 viene illustrato il percorso tipico tra una rete locale e il cloud Microsoft. Il server perimetrale di rete locale si connette a Internet tramite un collegamento WAN a un ISP. Il traffico si sposta su Internet verso il bordo del cloud Microsoft. Le offerte cloud all'interno del cloud Microsoft includono Office 365, Microsoft Azure, Microsoft Intune e Dynamics 365. Gli utenti di un'organizzazione possono trovarsi nella rete locale o su Internet.
  
Senza una connessione ExpressRoute, l'unica parte del percorso di traffico del cloud Microsoft che è possibile controllare (e avere una relazione con il provider di servizi) è il collegamento tra il server perimetrale di rete locale e l'ISP. 
  
Il percorso tra l'ISP e Microsoft Cloud Edge è un sistema di distribuzione di Best-Effort su Internet soggetto a interruzioni, congestione del traffico e monitoraggio da parte di utenti malintenzionati.
  
Gli utenti su Internet, ad esempio il roaming o gli utenti remoti, inviano il traffico al cloud Microsoft su Internet.
  
Di seguito sono disponibili i percorsi di rete di Microsoft Cloud con una connessione ExpressRoute.
  
**Figura 2: i percorsi di rete con ExpressRoute**

![Figura 2: i percorsi di rete con ExpressRoute](media/Network-Poster/ExpressRoute-post.png)
  
Nella figura 2 sono illustrati due percorsi di rete. Il traffico verso Microsoft Intune percorre lo stesso percorso del normale traffico Internet. Il traffico verso Office 365, Microsoft Azure e Dynamics 365 attraversa la connessione ExpressRoute, un percorso dedicato tra il perimetro della rete locale e il perimetro del cloud Microsoft.
  
Con una connessione ExpressRoute, è ora possibile controllare, tramite una relazione con il provider di servizi, l'intero percorso del traffico dal server perimetrale al bordo cloud Microsoft. Questa connessione può offrire prestazioni prevedibili e un [SLA di uptime del 99,95%](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).
  
È ora possibile contare sulla velocità effettiva e sulla latenza prevedibile, in base alla connessione del provider di servizi, ai servizi di Office 365, Azure e Dynamics 365. Le connessioni di ExpressRoute a Microsoft Intune non sono supportate in questo momento.
  
Il traffico inviato tramite la connessione ExpressRoute non è più soggetto a interruzioni Internet, alla congestione del traffico e al monitoraggio.
  
Gli utenti su Internet, ad esempio il roaming o gli utenti remoti, continuano a inviare il traffico al cloud Microsoft su Internet. Un'eccezione è il traffico verso un'applicazione di linea Intranet di business ospitata in Azure IaaS, che viene inviata tramite la connessione ExpressRoute tramite una connessione di accesso remoto alla rete locale.
  
Anche se si dispone di una connessione ExpressRoute, viene comunque inviato tramite Internet, ad esempio query DNS, controllo dell'elenco di revoche di certificati e richieste della rete di distribuzione del contenuto (CDN, content deliverment Network).
  
Per ulteriori informazioni, vedere queste risorse aggiuntive:
  
- [ExpressRoute per Office 365](https://aka.ms/expressrouteoffice365)
    
- [ExpressRoute per Azure](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a>Vantaggi di ExpressRoute per Azure

Di seguito sono offerti alcuni vantaggi dell'utilizzo di ExpressRoute per i servizi cloud basati su Azure:
  
- **Prestazioni prevedibili:** Con un percorso dedicato al server perimetrale di Microsoft Cloud, le prestazioni non sono soggette a interruzioni dei provider Internet e ai picchi del traffico Internet. È possibile determinare e mantenere i provider responsabili di una velocità effettiva e una latenza SLA nel cloud Microsoft.
    
- **Privacy dei dati per il traffico:** Il traffico inviato tramite la connessione ExpressRoute dedicata non è soggetto a monitoraggio Internet o all'acquisizione e all'analisi di pacchetti da parte di utenti malintenzionati. È sicura come l'utilizzo dei collegamenti WAN basati su Multiprotocol Label Switching (MPLS).
    
- **Connessioni a velocità elevata:** Con un ampio supporto per le connessioni di ExpressRoute da parte di provider di Exchange e provider di servizi di rete, è possibile ottenere fino a un collegamento a 10 Gbps per il cloud Microsoft.
    
- **Riduzione dei costi per alcune configurazioni:** Anche se le connessioni di ExpressRoute sono un costo aggiuntivo, in alcuni casi una singola connessione ExpressRoute può costare meno che aumentare la capacità Internet in più posizioni dell'organizzazione per fornire una velocità effettiva ai servizi cloud Microsoft.
    
Una connessione di ExpressRoute non garantisce prestazioni superiori in ogni configurazione. È possibile avere prestazioni più basse rispetto a una connessione ExpressRoute con larghezza di banda ridotta rispetto a una connessione Internet a larghezza di banda elevata che dista solo pochi passaggi da un datacenter Microsoft regionale.
  
Per i suggerimenti più recenti per l'utilizzo di ExpressRoute con Office 365, vedere [ExpressRoute per office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).
  
## <a name="expressroute-connectivity-models"></a>Modelli di connettività di ExpressRoute

Nella tabella 1 sono riportati i tre modelli di connettività principali per le connessioni di ExpressRoute.
  
|**Percorso condiviso in un exchange cloud**|**Ethernet Point-to-Point**|**Connessione any-to-any (VPN IP)**|
|:-----|:-----|:-----|
|![Modello di connettività ExpressRoute: si trova in un Exchange cloud](media/Network-Poster/ER-Conn1.png)|![Modello di connettività ExpressRoute: Ethernet Point-to-Point](media/Network-Poster/ER-Conn2.png)|![Modello di connettività ExpressRoute: connessione any-to-any (VPN IP)](media/Network-Poster/ER-Conn3.png)|
|Se il Data Center è posizionato in una struttura con un cloud Exchange, è possibile ordinare una connessione incrociata virtuale a Microsoft Cloud tramite lo scambio Ethernet del provider di co-location.  <br/> |Se il Data Center si trova nella propria sede, è possibile utilizzare un collegamento Ethernet Point-to-Point per la connessione al cloud Microsoft.  <br/> |Se si sta già utilizzando un provider IP VPN (MPLS) per connettere i siti dell'organizzazione, una connessione ExpressRoute al cloud Microsoft agisce come un'altra posizione sulla WAN privata.  <br/> |
   
 **Tabella 1: modelli di connettività di ExpressRoute**
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a>Relazioni di peering di ExpressRoute con i servizi cloud Microsoft

Una singola connessione di ExpressRoute supporta fino a due diverse relazioni di peering del protocollo del gateway di Border (BGP) a diverse parti del cloud Microsoft. BPG utilizza relazioni di peering per stabilire informazioni di routing di attendibilità e di Exchange.
  
**Figura 3: le due diverse relazioni BGP in una singola connessione di ExpressRoute**

![Figura 3: le due diverse relazioni BGP in una singola connessione di ExpressRoute](media/Network-Poster/ERPeering.png)
  
Nella figura 3 viene illustrata una connessione ExpressRoute da una rete locale. La connessione ExpressRoute dispone di due relazioni di peering logiche. Una relazione di peering Microsoft si collega ai servizi SaaS di Microsoft, tra cui Office 365, DYNAMCS 365 e Azure PaaS Services. Una relazione di peering privata passa a Azure IaaS e a un gateway di rete virtuale che ospita macchine virtuali.
  
La relazione Microsoft peering BGP: 
  
- È da un router della DMZ agli indirizzi pubblici di Office 365, Dynamics 365 e Azure Services. 
    
- Supporta la comunicazione con avvio bidirezionale.
    
La relazione privata di peering BGP:
  
- È da un router sul bordo della rete dell'organizzazione agli indirizzi IP privati assegnati alla reti virtuali di Azure.
    
- Supporta la comunicazione con avvio bidirezionale.
    
- È un'estensione della rete dell'organizzazione al cloud Microsoft, con indirizzamento e routing coerenti internamente.

>[!Note]
>La relazione pubblica di peering BGP descritta nelle versioni precedenti di questo articolo è obsoleta.
>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a>Esempio di distribuzione di applicazioni e flusso di traffico con ExpressRoute

La modalità di spostamento del traffico tra le connessioni di ExpressRoute e all'interno del cloud Microsoft è una funzione delle route in corrispondenza del luppolo del percorso tra il comportamento di origine e di destinazione e l'applicazione. Di seguito è riportato un esempio di un'applicazione in esecuzione su una macchina virtuale di Azure che accede a una farm di SharePoint locale tramite una connessione VPN da sito a sito.
  
**Figura 4: un'applicazione in una macchina virtuale di Azure che accede a una farm di SharePoint locale**

![Figura 4: un'applicazione in una macchina virtuale di Azure che accede a una farm di SharePoint locale](media/Network-Poster/ER-App-Flow1.png)

  
Nella figura 4 viene illustrata una farm di SharePoint locale, una connessione VPN da sito a sito tra la rete locale e una rete virtuale in Azure IaaS, un server applicazioni in esecuzione come una macchina virtuale IaaS di Azure e il flusso di traffico tra il server applicazioni e farm di SharePoint.
  
L'applicazione individua l'indirizzo IP della farm di SharePoint utilizzando il DNS locale e tutto il traffico supera la connessione VPN da sito a sito.
  
Questa organizzazione ha eseguito la migrazione della farm di SharePoint locale a SharePoint online in Office 365 e ha distribuito una connessione ExpressRoute.
  
**Figura 5: spostamento della farm di SharePoint locale in SharePoint Online**

![Figura 5: spostamento della farm di SharePoint locale in SharePoint Online](media/Network-Poster/Hairpin1.png)
  
Nella figura 5 è illustrata l'aggiunta di una connessione ExpressRoute con relazioni di peering a Microsoft SaaS e Office 365 e a Azure IaaS contenente il server applicazioni in una rete virtuale. La farm di SharePoint locale è stata migrata a Office 365.
  
Con le relazioni di peering Microsoft e private:
  
- Dal gateway di rete virtuale di Azure, le posizioni locali sono disponibili in tutta la connessione ExpressRoute.
    
- Dall'abbonamento a Office 365, gli indirizzi IP pubblici dei dispositivi perimetrali, ad esempio i server proxy, sono disponibili nella connessione ExpressRoute.
    
- Dal server perimetrale di rete locale, gli indirizzi IP privati dei rete virtuale di Azure e gli indirizzi IP pubblici di Office 365 sono disponibili nella connessione ExpressRoute.
    
Quando l'applicazione accede agli URL di SharePoint Online, inoltra il traffico attraverso la connessione ExpressRoute a un server proxy nel perimetro. 
  
Quando il server proxy individua l'indirizzo IP di SharePoint Online, inoltra il traffico sulla connessione ExpressRoute. Il traffico di risposta percorre il percorso inverso.
  
**Figura 6: flusso di traffico quando la farm di SharePoint è stata migrata a SharePoint online in Office 365**

![Figura 6: flusso di traffico quando la farm di SharePoint è stata migrata a SharePoint online in Office 365](media/Network-Poster/Hairpin2.png)

  
Nella figura 6 viene illustrato il flusso del traffico tra il server applicazioni e SharePoint online in Office 365 sulla relazione privata di peering tra il server applicazioni e il perimetro di rete locale e quindi dal bordo della relazione di peering Microsoft a Office 365.
  
Il risultato è il pinning dei capelli, una conseguenza del comportamento dell'applicazione e del routing.
  
## <a name="expressroute-and-microsofts-cloud-network"></a>ExpressRoute e la rete cloud di Microsoft

Le connessioni di ExpressRoute sono disponibili in due versioni diverse: ExpressRoute e ExpressRoute Premium.
  
### <a name="expressroute"></a>ExpressRoute

La modalità di spostamento del traffico tra la rete dell'organizzazione e un datacenter Microsoft è una combinazione di:
  
- Posizioni.
    
- Microsoft Cloud peering locations (le posizioni fisiche per la connessione a Microsoft Edge).
    
- Posizioni del datacenter Microsoft.
    
Microsoft datacenter e cloud peering locations sono tutti connessi alla rete cloud Microsoft.
  
Quando si crea una connessione ExpressRoute a un percorso peering di Microsoft Cloud, si è connessi alla rete cloud Microsoft e a tutte le posizioni del datacenter Microsoft nello stesso continente. Il traffico tra il percorso di peering cloud e il datacenter di destinazione Microsoft viene eseguito tramite la rete cloud Microsoft.
  
Questo può comportare un recapito non ottimale ai datacenter locali Microsoft per il modello di connettività any-to-any.
  
**Figura 7: esempio di un'organizzazione geograficamente distribuita che utilizza una singola connessione di ExpressRoute**

![Figura 7: esempio di un'organizzazione geograficamente distribuita che utilizza una singola connessione di ExpressRoute](media/Network-Poster/MSNet1.png)
  
Nella figura 7 è illustrata un'organizzazione con due posizioni, la posizione 1 nel nord-ovest degli Stati Uniti e la posizione 2 nel nordest. Sono connessi da un provider WAN any-to-any. Questa organizzazione dispone anche di una connessione ExpressRoute a una posizione peering Microsoft sulla West Coast. Il traffico proveniente dalla posizione 2 nel nordest destinato a un centro dati della costa est deve attraversare la WAN dell'organizzazione fino alla costa occidentale, alla posizione di peering Microsoft e quindi di nuovo in tutto il paese tramite la rete cloud Microsoft fino alla costa orientale Datacenter.
  
Per il recapito ottimale, utilizzare più connessioni di ExpressRoute a posizioni peering di Microsoft Cloud regionali. 
  
**Figura 8: l'utilizzo di più connessioni ExpressRoute per il recapito ottimale ai datacenter regionali**

![Figura 8: l'utilizzo di più connessioni ExpressRoute per il recapito ottimale ai datacenter regionali](media/Network-Poster/MSNet2.png)
  
Nella figura 8 viene illustrata la stessa organizzazione con due connessioni ExpressRoute, una per ogni posizione, per le posizioni peering locali di Microsoft regionalmente. In questa configurazione, il traffico proveniente dalla posizione 2 nel nordest destinato a un datacenter della costa est passa direttamente a una posizione peering della costa orientale, alla rete cloud Microsoft e quindi al datacenter della East Coast.
  
Per le connessioni a più ExpressRoute è possibile specificare quanto segue:
  
- Migliorare le prestazioni per le posizioni locali del datacenter Microsoft.
    
- Maggiore disponibilità al cloud Microsoft quando una connessione ExpressRoute locale non è disponibile.
    
Questo funziona bene per le organizzazioni dello stesso continente. Tuttavia, il traffico verso i centri dati Microsoft al di fuori del continente dell'organizzazione viaggia su Internet.
  
Per il traffico intercontinentale sulla rete cloud Microsoft, è necessario utilizzare le connessioni Premium di ExpressRoute.
  
### <a name="expressroute-premium"></a>ExpressRoute Premium

Per le organizzazioni distribuite a livello globale in tutti i continenti, è possibile utilizzare ExpressRoute Premium. 
  
Con ExpressRoute Premium, puoi raggiungere qualsiasi datacenter Microsoft in qualsiasi continente da qualsiasi posizione di peering Microsoft. Il traffico tra i continenti viene trasportato sulla rete cloud Microsoft.
  
Con più connessioni Premium di ExpressRoute, è possibile disporre di:
  
- Prestazioni migliori per i datacenter Microsoft locali.
    
- Maggiore disponibilità al cloud globale di Microsoft quando una connessione ExpressRoute locale non è disponibile.
    
ExpressRoute Premium è necessario per le connessioni ExpressRoute basate su Office 365.
  
**Figura 9: la rete cloud Microsoft in tutto il mondo**

![Figura 9: la rete cloud Microsoft in tutto il mondo](media/Network-Poster/MSNet3.png)
  
Nella figura 9 è illustrato un diagramma logico della rete cloud Microsoft in tutto il mondo, con reti che si estendono nei continenti e nelle aree geografiche del mondo e nelle loro interconnessioni. Con una parte della rete cloud Microsoft in ogni continente, un'organizzazione globale crea connessioni ExpressRoute Premium dalle sedi degli hub regionali alle posizioni di peering di Microsoft locali.
  
Per un ufficio regionale, il traffico di Office 365 appropriato per:
  
- I datacenter di Office 365 continentale viaggiano sulla rete cloud Microsoft all'interno del continente.
    
- I datacenter di Office 365 in un altro continente viaggiano sulla rete intercontinentale Microsoft Cloud.
    
Per ulteriori informazioni, vedere:
  
- [Formazione di Azure ExpressRoute per Office 365](https://channel9.msdn.com/series/aer/)
    
- [Pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune)
    
## <a name="expressroute-options"></a>Opzioni di ExpressRoute

È inoltre possibile incorporare le opzioni seguenti nella distribuzione di ExpressRoute:
  
- **Sicurezza al tuo margine:** Per garantire una sicurezza avanzata per il traffico inviato e ricevuto tramite la connessione ExpressRoute, ad esempio il controllo del traffico o il rilevamento di intrusioni/malware, inserire gli strumenti di sicurezza nel percorso di traffico all'interno della DMZ o al bordo della rete Intranet.
    
- **Traffico Internet per le macchine virtuali:** Per impedire che le macchine virtuali di Azure inizino il traffico direttamente con le posizioni Internet, annunciare la route predefinita a Microsoft. Il traffico su Internet viene instradato attraverso la connessione ExpressRoute e attraverso i server proxy locali. Il traffico dalle macchine virtuali di Azure ai servizi di PaaS di Azure o Office 365 viene instradato all'interno della connessione ExpressRoute.
    
- **Ottimizzatori WAN:** È possibile distribuire ottimizzatori WAN su entrambi i lati di una connessione peer privata per una rete virtuale di Azure cross-premise (rete virtuale). All'interno di rete virtuale di Azure, utilizzare un dispositivo di rete WAN Optimizer da Azure Marketplace e routing definito dall'utente per instradare il traffico tramite l'accessorio.
    
- **Qualità del servizio:** Utilizzare i valori di codice Point (DSCP) di servizi differenziati nell'intestazione IPv4 del traffico per contrassegnarla per il recapito vocale, video/Interactive o Best-Effort. Questo è particolarmente importante per la relazione di peering Microsoft e per il traffico di Skype for business online.
    
Per ulteriori informazioni, vedere queste risorse aggiuntive:
  
- [ExpressRoute per Office 365](https://aka.ms/expressrouteoffice365)
    
- [Formazione di Azure ExpressRoute per Office 365](https://channel9.msdn.com/series/aer/)
    
- [ExpressRoute per Azure](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a>Passaggio successivo

[Progettazione di rete per Microsoft SaaS](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a>Vedere anche

[Rete di Microsoft Cloud per Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

