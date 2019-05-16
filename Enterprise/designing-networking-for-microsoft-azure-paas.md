---
title: Progettazione di rete per Microsoft Azure PaaS
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
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: "Riepilogo: informazioni su come ottimizzare la rete per l'accesso a Microsoft Azure PaaS."
ms.openlocfilehash: fafc3de1c5f755e891da6c07ae8993fb869bc5e1
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067822"
---
# <a name="designing-networking-for-microsoft-azure-paas"></a>Progettazione di rete per Microsoft Azure PaaS

 **Riepilogo:** Informazioni su come ottimizzare la rete per l'accesso a Microsoft Azure PaaS.
  
L'ottimizzazione della rete per le app PaaS di Azure necessita di una larghezza di banda Internet adeguata e può richiedere la distribuzione del traffico di rete in più siti o app.
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a>Procedura di pianificazione per l'hosting di applicazioni PaaS dell'organizzazione in Azure

1. Consultare la sezione **Procedura per predisporre la rete per i servizi cloud Microsoft** in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).
    
2. Ottimizzare la larghezza di banda Internet utilizzando i passaggi 2-4 della **procedura per preparare la rete per i servizi SaaS di Microsoft** nella sezione [progettazione di rete per Microsoft SaaS](designing-networking-for-microsoft-saas.md).
    
3. Determinare se è necessaria una connessione di ExpressRoute a Azure.
    
4. Per i carichi di lavoro basati sul Web, determinare se è necessario il gateway dell'applicazione Azure.
    
5. Per la distribuzione del traffico verso endpoint diversi in diversi Data Center, determinare se è necessario Azure Traffic Manager.
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a>Larghezza di banda Internet per le applicazioni di PaaS dell'organizzazione

Le applicazioni dell'organizzazione ospitate in Azure PaaS richiedono la larghezza di banda Internet per gli utenti Intranet. Esistono due opzioni:
  
- **Opzione 1:** Utilizzare la tubazione esistente, ottimizzata per il traffico Internet con la capacità di gestire i carichi di picco. Vedere[progettazione della rete per](designing-networking-for-microsoft-saas.md) le considerazioni relative a Microsoft SaaS per Internet Edge, utilizzo client e operazioni it.
    
- **Opzione 2:** Per le esigenze di bassa latenza e larghezza di banda elevata, utilizzare una connessione ExpressRoute a Azure.
    
**Figura 1: opzioni di connessione per la connessione dei servizi di PaaS di Azure**

![Figura 1: opzioni di connessione per i servizi di PaaS di Azure](media/Network-Poster/PaaS1.png)
  
Nella figura 1 viene illustrata una rete locale che si connette ai servizi di PaaS di Azure su una pipe Internet o ExpressRoute.
  
## <a name="azure-application-gateway"></a>Gateway dell'applicazione di Azure

Servizi di routing a livello di applicazione e di bilanciamento del carico che consentono di creare un front-end Web scalabile e a disponibilità elevata in Azure per le applicazioni Web, i servizi cloud e le macchine virtuali. 
  
**Figura 2: gateway di applicazioni di Azure**

![Figura 2: servizio gateway dell'applicazione Azure](media/Network-Poster/PaaS2.png)
  
Nella figura 2 viene mostrato il gateway dell'applicazione di Azure e come le richieste degli utenti da Internet possono essere instradate a Azure Web Apps, servizi cloud o macchine virtuali.
  
Il gateway applicazione supporta attualmente il recapito delle applicazioni Layer 7 per gli elementi seguenti:
  
- Bilanciamento del carico HTTP
    
- Affinità di sessione basata su cookie
    
- Offload SSL
    
Per ulteriori informazioni, vedere [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).
  
## <a name="azure-traffic-manager"></a>Azure Traffic Manager

Distribuzione del traffico verso endpoint diversi, che possono includere servizi cloud o Azure Web Apps ubicati in diversi Data Center o endpoint esterni.
  
Traffic Manager utilizza i seguenti metodi di routing:
  
- **Failover:** Gli endpoint sono nello stesso datacenter di Azure o in altri centri dati e si desidera utilizzare un endpoint primario per tutto il traffico, ma fornire backup nel caso in cui gli endpoint primari o di backup non siano disponibili.
    
- **Round Robin:** Si desidera distribuire il carico in un set di endpoint nello stesso datacenter o in diversi datacenter.
    
- **Prestazioni:** Si dispone di endpoint in diverse posizioni geografiche e si desidera richiedere ai client di utilizzare l'endpoint "più vicino" in termini di latenza più bassa.
    
Di seguito è riportato un esempio per tre app Web geograficamente distribuite.
  
**Figura 3: gestione traffico di Azure**

![Figura 3: gestione traffico di Azure](media/Network-Poster/PaaS3.png)
  
Nella figura 3 viene illustrato il processo di base utilizzato da Traffic Manager per instradare le richieste a tre diverse app Web di Azure in Stati Uniti, Europa e Asia. Nell'esempio seguente:
  
1. Una query DNS dell'utente per l'URL di un sito Web viene indirizzata a Azure Traffic Manager, che restituisce il nome di un'app web regionale, in base al metodo di routing delle prestazioni.
    
2. L'utente avvia il traffico con l'app web regionale in Europa.
    
Per ulteriori informazioni, vedere [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).

## <a name="next-step"></a>Passaggio successivo

[Progettazione di rete per Microsoft Azure IaaS](designing-networking-for-microsoft-azure-iaas.md)
 
## <a name="see-also"></a>Vedere anche

[Rete di Microsoft Cloud per Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

