---
title: "Evoluzione della rete per la connettività cloud"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: concetpual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: 'Riepilogo: Informazioni su come l''adozione cloud richiede un nuovo approccio agli investimenti nell''infrastruttura di rete.'
ms.openlocfilehash: 810640ab3b870759424af2f88392bbaf0b0e11c7
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="evolving-your-network-for-cloud-connectivity"></a>Evoluzione della rete per la connettività cloud

 **Riepilogo:** Informazioni su come l'adozione cloud richiede un nuovo approccio agli investimenti nell'infrastruttura di rete.
  
La migrazione cloud cambia il volume e la natura dei flussi del traffico all'interno e all'esterno di una rete aziendale. Influisce, inoltre, sugli approcci finalizzati alla mitigazione dei rischi per la sicurezza.
  
- Prima di nel cloud
    
    La maggior parte degli investimenti nell'infrastruttura di rete sono state dedicate a garantire disponibili e affidabile e la connettività ad alte prestazioni a centri dati locali. Per molte organizzazioni, la connettività Internet non è stato critica per le operazioni aziendali interne. I confini della rete sono state principale difesa contro le violazioni della protezione.
    
- Dopo aver nel cloud
    
    Con carichi di lavoro IT in esecuzione nel cloud e produttività nuove e sottoposti a migrazione, gli investimenti vengono spostate dall'infrastruttura locale centri dati per la connettività Internet, che ora è fondamentale per operazioni aziendali interne. Connettività federati Sposta strategia di protezione per proteggere le identità e dati quando circolano attraverso la rete e i punti di connettività ai servizi cloud Microsoft.
    
Gli investimenti nell'infrastruttura di rete iniziano con la connettività. Ulteriori investimenti variano a seconda della categoria del servizio cloud.
  
- **Software come servizio (SaaS)** Servizi Microsoft SaaS includono Office 365, Microsoft Intune e Microsoft Dynamics 365. Un'adozione dei servizi SaaS dagli utenti dipende dalla disponibilità elevata e la connettività ad alte prestazioni a Internet o direttamente a servizi cloud Microsoft.
    
    Architettura di rete è incentrata su connettività affidabile e ridondanti e la larghezza di banda ampio. Costante investimento include monitoraggio e ottimizzazione delle prestazioni.
    
- **Piattaforma Azure as a Service (PaaS)** Oltre che per i servizi Microsoft SaaS gli investimenti multisite o geograficamente distribuite applicazioni PaaS potrebbe essere necessario architettura Azure Traffic Managerhttp per distribuire il traffico client. Costante investimento include le prestazioni e monitoraggio del traffico di distribuzione e test di failover.
    
- **Infrastruttura come servizio (IaaS)** Oltre a investimenti per i servizi Microsoft SaaS e PaaS, l'esecuzione di carichi di lavoro IT in IaaS richiede la progettazione e configurazione di Azure virtual reti di ospitare macchine virtuali, la connettività protetta per le applicazioni in esecuzione su di essi, routing, IP risoluzione DNS e bilanciamento del carico. Costante investimento include il monitoraggio e risoluzione dei problemi di protezione e le prestazioni.
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a>Aree di rete investimento per il successo nel cloud

Le organizzazioni aziendali può risultare vantaggiosa un approccio metodico per ottimizzare velocità effettiva della rete attraverso una rete intranet e Internet. È possibile traggono vantaggio da una connessione ExpressRoute.
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a>Ottimizzare la connettività di rete intranet alla rete perimetrale

Nel corso degli anni, molte organizzazioni sono ottimizzate intranet connettività e le prestazioni per le applicazioni in esecuzione in locale datacenter. Con la produttività e IT carichi di lavoro in esecuzione nel cloud Microsoft, ulteriori investimenti devono garantire la disponibilità elevata connettività e che le prestazioni del traffico tra la rete perimetrale e gli utenti intranet sono ottimale.
  
### <a name="optimize-throughput-at-your-edge-network"></a>Ottimizzazione della velocità effettiva alla rete perimetrale

Come più il traffico di produttività quotidiane viaggia nel cloud, è necessario esaminare l'insieme di sistemi strettamente nella rete perimetrale per verificare che siano corrente, garantire una disponibilità elevata e avere sufficiente capacità per soddisfare i carichi di picco.
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a>Per un contratto di servizio elevata Dynamics 365, Office 365 e Azure, utilizzare ExpressRoute

Anche se è possibile utilizzare la connessione a Internet corrente dalla rete perimetrale, il traffico da e verso servizi cloud Microsoft deve condividere pipe con altri del traffico intranet in Internet. Inoltre, il traffico ai servizi cloud Microsoft è soggetto a congestione traffico Internet.
  
Per ottenere prestazioni ottimali e un contratto di servizio elevata, utilizzare ExpressRoute, una singola connessione WAN tra la rete e Azure, Office 365, Dynamics 365 o tutti e tre. 
  
ExpressRoute può utilizzare il provider di rete esistente per una connessione dedicata. Risorse connessione tramite ExpressRoute vengono visualizzate come se sono sulla WAN, anche per le organizzazioni geograficamente distribuita.
  
Per ulteriori informazioni, vedere [ExpressRoute per la connettività cloud Microsoft](expressroute-for-microsoft-cloud-connectivity.md).
  
## <a name="scope-of-network-investments"></a>Ambito degli investimenti di rete

L'ambito degli investimenti rete variano a seconda della categoria del servizio cloud. Investire in cloud Microsoft ingrandita gli investimenti del team di rete. Gli investimenti per i servizi IaaS, ad esempio, si applicano a tutte le aree di investimento.
  
|||||
|:-----|:-----|:-----|:-----|
|Aree di investimento  <br/> |SaaS  <br/> |PaaS  <br/> |IaaS  <br/> |
|Progettare la connettività Internet affidabile e ridondante con larghezza di banda ampio  <br/> |Si applica  <br/> |Si applica  <br/> |Si applica  <br/> |
|Monitorare e ottimizzare la velocità effettiva Internet per le prestazioni  <br/> |Si applica  <br/> |Si applica  <br/> |Si applica  <br/> |
|Risoluzione dei problemi di connettività e la velocità effettiva Internet  <br/> |Si applica  <br/> |Si applica  <br/> |Si applica  <br/> |
|Gestione del traffico Azure progettazione per il carico del traffico bilanciare agli endpoint diversi  <br/> ||Si applica  <br/> |Si applica  <br/> |
|Connettività architetto affidabile e ridondante e ad alte prestazioni a Azure virtual Network  <br/> |||Si applica  <br/> |
|Progettare la connettività protetta per macchine virtuali di Azure  <br/> |||Si applica  <br/> |
|Progettare e implementare il routing tra le posizioni in locale e reti virtuali  <br/> |||Si applica  <br/> |
|Progettare e implementare il bilanciamento del carico per carichi di lavoro IT interni e con connessione Internet  <br/> |||Si applica  <br/> |
|Risoluzione dei problemi di connettività e velocità effettiva delle macchine virtuali  <br/> |||Si applica  <br/> |
   
## <a name="see-also"></a>See Also

[Microsoft Cloud per architetti di rete](microsoft-cloud-networking-for-enterprise-architects.md)
  
[ExpressRoute per la connettività cloud Microsoft](expressroute-for-microsoft-cloud-connectivity.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT](https://sway.com/FJ2xsyWtkJc2taRD)



