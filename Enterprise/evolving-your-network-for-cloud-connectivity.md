---
title: Trasformazione della tua rete per la connettività cloud
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: "Riepilogo: informazioni su come l'adozione del cloud richiede un nuovo approccio agli investimenti dell'infrastruttura di rete."
ms.openlocfilehash: c8fba120292b89894850312a84fd6067d925a07f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487242"
---
# <a name="evolving-your-network-for-cloud-connectivity"></a>Trasformazione della tua rete per la connettività cloud

 **Riepilogo:** Comprendere in che modo l'adozione del cloud richiede un nuovo approccio agli investimenti dell'infrastruttura di rete.
  
La migrazione cloud cambia il volume e la natura dei flussi del traffico all'interno e all'esterno di una rete aziendale. Influisce, inoltre, sugli approcci finalizzati alla mitigazione dei rischi per la sicurezza.
  
- Prima del cloud
    
    La maggior parte degli investimenti dell'infrastruttura di rete è stata spesa per garantire la connettività disponibile, affidabile e performante ai datacenter locali. Per molte organizzazioni, la connettività Internet non è stata critica per le operazioni aziendali interne. I limiti di rete sono stati le difese primarie rispetto alle violazioni della sicurezza.
    
- Dopo il cloud
    
    Con la produttività e i carichi di lavoro IT nuovi e migrati in esecuzione nel cloud, gli investimenti nell'infrastruttura si spostano dai data center locali alla connettività Internet, che ora è fondamentale per le operazioni aziendali interne. La connettività federata consente di spostare la strategia di protezione per proteggere le identità e i dati che scorrono attraverso la rete e i punti di connettività ai servizi cloud Microsoft.
    
Gli investimenti dell'infrastruttura di rete iniziano con la connettività. Gli investimenti aggiuntivi dipendono dalla categoria del servizio cloud.
  
- **Software come servizio (SaaS)** I servizi SaaS di Microsoft includono Office 365, Microsoft Intune e Microsoft Dynamics 365. Un'adozione soddisfacente dei servizi SaaS da parte degli utenti dipende da una connettività a Internet efficiente e ad elevata disponibilità o direttamente ai servizi cloud di Microsoft.
    
    L'architettura di rete è incentrata su connettività affidabile e ridondante e larghezza di banda ampia. Gli investimenti in esecuzione includono il monitoraggio delle prestazioni e l'ottimizzazione.
    
- **Piattaforma di Azure come servizio (PaaS)** Oltre agli investimenti per i servizi SaaS di Microsoft, le applicazioni di PaaS multi-site o geograficamente distribuite potrebbero richiedere a Architecting Azure Traffic Manager la distribuzione del traffico client. Gli investimenti in esecuzione includono il monitoraggio delle prestazioni e della distribuzione del traffico e il test di failover.
    
- **Infrastruttura di Azure come servizio (IaaS)** Oltre agli investimenti per i servizi SaaS e PaaS di Microsoft, l'esecuzione dei carichi di lavoro IT in IaaS richiede la progettazione e la configurazione di reti virtuali di Azure che ospitano macchine virtuali, la connettività sicura per le applicazioni in esecuzione su di essi, routing, IP indirizzamento, DNS e bilanciamento del carico. Gli investimenti in esecuzione includono il monitoraggio delle prestazioni e della sicurezza e la risoluzione dei problemi.

[Microsoft 365](https://www.microsoft.com/microsoft-365) è una combinazione di Office 365, Enterprise Management + Security (EMS) e Windows 10. Microsoft 365 combina più servizi SaaS e Azure per una soluzione completa e intelligente che consenta a tutti di essere creativi e di lavorare insieme in modo sicuro.
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a>Aree di investimento di rete per il successo nel cloud

Le organizzazioni aziendali traggono vantaggio dall'adozione di un approccio metodico per ottimizzare la velocità effettiva di rete in tutta la Intranet e Internet. Si potrebbe anche trarre vantaggio da una connessione ExpressRoute.
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a>Ottimizzare la connettività Intranet alla rete perimetrale

Nel corso degli anni, molte organizzazioni hanno ottimizzato la connettività Intranet e le prestazioni per le applicazioni in esecuzione nei data center locali. Con la produttività e i carichi di lavoro IT in esecuzione nel cloud Microsoft, ulteriori investimenti devono garantire una disponibilità elevata della connettività e che le prestazioni del traffico tra la rete perimetrale e gli utenti Intranet siano ottimali.
  
### <a name="optimize-throughput-at-your-edge-network"></a>Ottimizzare la velocità effettiva sulla rete perimetrale

Man mano che il traffico di produttività giornaliero si sposta sul cloud, è necessario esaminare attentamente il set di sistemi della rete perimetrale per assicurarsi che siano correnti, fornire disponibilità elevata e avere una capacità sufficiente per raggiungere i carichi di picco.
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a>Per un livello di SLA elevato a Azure, Office 365 e Dynamics 365, utilizzare ExpressRoute

Anche se è possibile utilizzare la connessione Internet corrente dalla rete perimetrale, il traffico da e verso i servizi cloud di Microsoft deve condividere la pipe con altri traffici Intranet che vanno su Internet. Inoltre, il traffico verso i servizi cloud Microsoft è soggetto alla congestione del traffico Internet.
  
Per un elevato livello di SLA e le prestazioni ottimali, utilizzare ExpressRoute, una connessione WAN dedicata tra la rete e Azure, Office 365, Dynamics 365 o tutti e tre. 
  
ExpressRoute può sfruttare il provider di rete esistente per una connessione dedicata. Le risorse connesse da ExpressRoute vengono visualizzate come se fossero presenti sulla rete WAN, anche per le organizzazioni geograficamente distribuite.
  
Per ulteriori informazioni, vedere [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).
  
## <a name="scope-of-network-investments"></a>Ambito degli investimenti di rete

L'ambito degli investimenti di rete dipende dalla categoria del servizio cloud. Investire nel cloud di Microsoft massimizza gli investimenti dei team di networking. Ad esempio, gli investimenti per i servizi di IaaS si applicano a tutte le aree di investimento.
  
|||||
|:-----|:-----|:-----|:-----|
|Area di investimento  <br/> |SaaS  <br/> |PaaS  <br/> |IaaS  <br/> |
|Architetto affidabile, connettività Internet ridondante con larghezza di banda ampia  <br/> |Applica  <br/> |Applica  <br/> |Applica  <br/> |
|Monitorare e ottimizzare la velocità effettiva Internet per le prestazioni  <br/> |Applica  <br/> |Applica  <br/> |Applica  <br/> |
|Risoluzione dei problemi relativi a connettività Internet e velocità effettiva  <br/> |Applica  <br/> |Applica  <br/> |Applica  <br/> |
|Progettare Azure Traffic Manager per il bilanciamento del carico del traffico verso endpoint diversi  <br/> ||Applica  <br/> |Applica  <br/> |
|Architetto connettività affidabile, ridondante ed eseguibile per le reti virtuali di Azure  <br/> |||Applica  <br/> |
|Progettare la connettività sicura alle macchine virtuali di Azure  <br/> |||Applica  <br/> |
|Progettare e implementare il routing tra le posizioni locali e le reti virtuali  <br/> |||Applica  <br/> |
|Architetto e implementazione del bilanciamento del carico per i carichi di lavoro IT interni e con accesso a Internet  <br/> |||Applica  <br/> |
|Risoluzione dei problemi di connettività e velocità effettiva della macchina virtuale  <br/> |||Applica  <br/> |
   
## <a name="next-step"></a>Passaggio successivo

[Elementi comuni della connettività cloud di Microsoft](common-elements-of-microsoft-cloud-connectivity.md)

## <a name="see-also"></a>Vedere anche

[Rete di Microsoft Cloud per Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Risorse sull'architettura IT di Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)



