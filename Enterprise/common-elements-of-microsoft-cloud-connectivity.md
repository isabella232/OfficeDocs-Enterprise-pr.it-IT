---
title: "Elementi comuni della connettività cloud Microsoft"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: 'Riepilogo: Informazioni su come preparare la rete e gli elementi comuni dell''infrastruttura di rete.'
ms.openlocfilehash: b630daad3292976245c8cb5d3f493c32ad5be8a6
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2018
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a>Elementi comuni della connettività cloud Microsoft

 **Riepilogo:** Informazioni su come preparare la rete e gli elementi comuni dell'infrastruttura di rete.
  
L'integrazione della rete con il cloud di Microsoft consente di accedere facilmente a una vasta gamma di servizi.
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a>Passaggi per preparare la rete di servizi cloud Microsoft
<a name="steps"> </a>

Per la rete locale:
  
1. Analizzare i computer client e ottimizzare per l'hardware di rete, driver software, le impostazioni del protocollo e browser Internet.
    
2. Analisi della rete locale per il traffico latenza e il routing ottimale per il dispositivo edge Internet.
    
3. Analizzare le capacità e prestazioni del dispositivo edge Internet e ottimizzare per più alti livelli di traffico.
    
Per la connessione a Internet:
  
1. Analizzare la latenza tra il dispositivo edge Internet (ad esempio, il firewall esterno) e i percorsi regionali del servizio cloud Microsoft a cui si effettua la connessione.
    
2. Analizzare le capacità e l'utilizzo della connessione Internet corrente e, se necessario, aggiungere capacità. In alternativa, aggiungere una connessione ExpressRoute.
    
## <a name="microsoft-cloud-connectivity-options"></a>Opzioni di integrazione applicativa Microsoft cloud
<a name="steps"> </a>

Utilizzare il canale Internet esistente o una connessione ExpressRoute a Office 365 e Azure Dynamics 365.
  
**Figura 1: Opzioni per la connettività cloud Microsoft**

![Figura 1:  Opzioni per la connettività di Microsoft Cloud](images/Network_Poster/CommonElements.png)

  
Nella figura 1 viene illustrato come una rete locale può essere connesso a offerte cloud Microsoft utilizzando la propria pipe Internet esistente o ExpressRoute. Il canale Internet rappresenta una DMZ e può avere i seguenti componenti:
  
- **Firewall interno:** Barriera tra la rete attendibile e uno non attendibile. Esegue il traffico filtro (in base alle regole) e il monitoraggio.
    
- **Il carico di lavoro esterno:** Siti Web o altri carichi di lavoro rese disponibili per gli utenti esterni su Internet.
    
- **Server proxy:** Gestisce le richieste di contenuto web per conto degli utenti intranet. Un proxy inverso consente le richieste in ingresso non richiesto.
    
- **Firewall esterno:** Consente il traffico in uscita e il traffico in ingresso specificato. Consente di eseguire conversione degli indirizzi.
    
- **Connessione WAN al provider di servizi Internet:** Una connessione basata su gestore di telefonia per un provider di servizi Internet, che peer per il routing e la connettività Internet.
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a>Aree di rete comune a tutti i servizi cloud Microsoft
<a name="steps"> </a>

È necessario prendere in considerazione queste aree di rete adottando uno dei servizi cloud Microsoft.
  
- **Delle prestazioni di rete intranet:** Per le risorse basate su Internet rallentamento delle prestazioni se la rete intranet, tra cui i computer client, non è ottimizzata.
    
- **Dispositivi di server perimetrali:** Dispositivi in corrispondenza del bordo della rete sono i punti di uscita e possono includere (Network Address Translator), server proxy (inclusi i proxy inversi), i firewall, i dispositivi di rilevamento delle intrusioni o una combinazione.
    
- **Connessione Internet:** Connessione WAN al provider di servizi Internet e Internet dovrebbe avere sufficiente capacità per gestire i carichi di picco. È inoltre possibile utilizzare una connessione ExpressRoute.
    
- **Internet DNS:** A, AAAA, CNAME, MX, PTR e altri record per individuare Microsoft cloud o i servizi ospitati nel cloud. Ad esempio, si potrebbe essere necessario un record CNAME per l'app ospitate in Azure PaaS.
    

## <a name="next-step"></a>Passaggio successivo

[ExpressRoute per la connettività cloud Microsoft](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a>Vedere anche

<a name="steps"> </a>

[Rete cloud Microsoft per Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)


