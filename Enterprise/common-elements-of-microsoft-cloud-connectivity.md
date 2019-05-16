---
title: Elementi comuni della connettività cloud Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: "Riepilogo: informazioni sugli elementi comuni dell'infrastruttura di rete e su come preparare la rete."
ms.openlocfilehash: f092e3fb0a2f009aa7c6bbb14229fe98b35700ea
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068112"
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a>Elementi comuni della connettività cloud Microsoft

 **Riepilogo:** Comprendere gli elementi comuni dell'infrastruttura di rete e come preparare la rete.
  
L'integrazione della rete con il cloud di Microsoft consente di accedere facilmente a una vasta gamma di servizi.
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a>Passaggi per preparare la rete per i servizi cloud Microsoft
<a name="steps"> </a>

Per la rete locale:
  
1. Analizzare i computer client e ottimizzare l'hardware di rete, i driver software, le impostazioni del protocollo e i browser Internet.
    
2. Analizzare la rete locale per la latenza del traffico e il routing ottimale per il dispositivo perimetrale Internet.
    
3. Analizzare la capacità e le prestazioni del dispositivo perimetrale Internet e ottimizzare i livelli di traffico più alti.
    
Per la connessione a Internet:
  
1. Analizzare la latenza tra il dispositivo perimetrale Internet (ad esempio il firewall esterno) e le posizioni internazionali del servizio cloud Microsoft a cui ci si connette.
    
2. Analizzare la capacità e l'utilizzo della connessione Internet corrente e aggiungere capacità, se necessario. In alternativa, aggiungere una connessione ExpressRoute.
    
## <a name="microsoft-cloud-connectivity-options"></a>Opzioni di connettività cloud Microsoft
<a name="steps"> </a>

Utilizzare la pipe Internet esistente o una connessione ExpressRoute a Office 365, Azure e Dynamics 365.
  
**Figura 1: opzioni per la connettività cloud Microsoft**

![Figura 1: opzioni per la connettività cloud Microsoft](media/Network-Poster/CommonElements.png)

  
Nella figura 1 viene illustrato come è possibile connettere una rete locale a offerte cloud di Microsoft utilizzando la propria pipe Internet o ExpressRoute esistente. La pipe Internet rappresenta una DMZ e può disporre dei componenti seguenti:
  
- **Firewall interno:** Una barriera tra la rete attendibile e quella non attendibile. Esegue il filtraggio del traffico (in base alle regole) e il monitoraggio.
    
- **Carico di lavoro esterno:** Siti Web o altri carichi di lavoro resi disponibili per gli utenti esterni su Internet.
    
- **Server proxy:** Richieste di servizi per il contenuto Web per conto di utenti Intranet. Un proxy inverso consente richieste inbound indesiderate.
    
- **Firewall esterno:** Consente il traffico in uscita e il traffico in ingresso specificato. È in grado di eseguire la conversione degli indirizzi, l'ispezione dei pacchetti, la rottura SSL e il controllo o la prevenzione della perdita di
    
- **Connessione WAN a ISP:** Una connessione basata su portatore a un ISP, che si occupa di peer con Internet per la connettività e il routing.
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a>Aree di rete comuni a tutti i servizi cloud Microsoft
<a name="steps"> </a>

È necessario prendere in considerazione queste aree di networking quando si adotta uno dei servizi cloud di Microsoft.
  
- **Prestazioni Intranet:** Le prestazioni alle risorse basate su Internet soffriranno se la rete Intranet, compresi i computer client, non è ottimizzata.
    
- **Dispositivi perimetrali:** I dispositivi ai margini della rete sono punti di uscita e possono includere i NAT (Network Address Translator), i server proxy (inclusi i proxy inversi), i firewall, i dispositivi di rilevamento delle intrusioni o una combinazione.
    
- **Connessione Internet:** La connessione WAN all'ISP e a Internet deve disporre di capacità sufficiente per gestire i carichi di picco. È inoltre possibile utilizzare una connessione ExpressRoute.
    
- **DNS Internet:** A, AAAA, CNAME, MX, PTR e altri record per individuare Microsoft Cloud o i servizi ospitati nel cloud. Ad esempio, potrebbe essere necessario un record CNAME per l'app ospitata in Azure PaaS.
    

## <a name="next-step"></a>Passaggio successivo

[ExpressRoute per la connettività cloud di Microsoft](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a>Vedere anche

<a name="steps"> </a>

[Rete di Microsoft Cloud per Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)


