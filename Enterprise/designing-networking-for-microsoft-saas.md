---
title: Progettazione di rete per Microsoft SaaS
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
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: "Riepilogo: Informazioni su come ottimizzare la rete per l'accesso ai servizi SaaS di Microsoft, tra cui Office 365, Microsoft Intune e Dynamics 365."
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872267"
---
# <a name="designing-networking-for-microsoft-saas"></a>Progettazione di rete per Microsoft SaaS

 **Riepilogo:** Informazioni su come ottimizzare la rete per l'accesso ai servizi SaaS di Microsoft, tra cui Office 365, Microsoft Intune e Dynamics 365.
  
Ottimizzazione della rete per i servizi Microsoft SaaS richiede la configurazione di interno e ai dispositivi di indirizzare le diverse categorie di traffico ai servizi Microsoft SaaS edge.
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>Passaggi di preparazione della rete per i servizi Microsoft SaaS

Eseguire la procedura seguente per ottimizzare la rete per i servizi Microsoft SaaS:
  
1. Consultare la sezione **Procedura per predisporre la rete per i servizi cloud Microsoft** in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).
    
2. Aggiungere una connessione Internet a ciascuno degli uffici.
    
3. Verificare che il provider di servizi Internet per tutte le connessioni Internet utilizzare un server DNS con un indirizzo IP locale.
    
4. Esaminare i hairpins di rete, intermedie destinazioni, ad esempio servizi di protezione basato su cloud ed eliminarle se possibile.
    
5. Configurare i dispositivi edge per ignorare l'elaborazione per l'ottimizzazione e consentire le categorie di traffico SaaS Microsoft.

## <a name="optimizing-traffic-to-microsofts-saas-services"></a>Ottimizzare il traffico ai SaaS servizi di Microsoft    

Esistono tre categorie di traffico SaaS Microsoft:

- Ottimizzazione

  Necessario per la connettività a ogni servizio Microsoft SaaS e rappresentano oltre il 75% di larghezza di banda SaaS Microsoft, le connessioni e volume di dati.

- Consenti

  Necessari per la connettività a specifici SaaS Microsoft dei servizi e funzionalità ma non sono i cursori sensibili alle prestazioni di rete e latenza a quelli della categoria Ottimizza.

- Predefinita

  Rappresentano SaaS Microsoft services e le dipendenze esistenti che non richiedono alcun ottimizzazione. È inoltre possibile considerare il traffico di categoria predefinita come normale traffico Internet.


**Nella figura 1: Configurazione consigliata per il traffico SaaS Microsoft per tutti gli uffici**

![Nella figura 1: Configurazione consigliata per il traffico SaaS Microsoft per tutti gli uffici](media/Network-Poster/SaaS1.png)

Nella figura 1 viene illustrata la configurazione consigliata di tutti gli uffici, incluse le succursali e quelle regionale o centrale, in cui:

- Categorie **predefinite** e generale traffico Internet viene indirizzato a sedi che utilizzano i server proxy e ad altri dispositivi edge per garantire la protezione contro i rischi di sicurezza basato su Internet.
- **Ottimizza** e **Consenti** traffico categoria viene inoltrato direttamente al bordo del Microsoft network front-end più vicina office contenente l'utente connesso, ignorando proxy server e altri dispositivi edge.

Dispositivi di rete (WAN SD) definito software WAN nelle succursali separano il traffico in modo che: 

- Categorie **predefinite** e generale Internet del traffico a un ufficio centrale o internazionale tramite backbone WAN. 
- Traffico categoria **Ottimizza** e **Consenti** passa al provider di servizi Internet che fornisce la connessione a Internet locale.
  
Per altre informazioni, vedere:
  
- [Principi di connettività di rete](https://aka.ms/expressrouteoffice365)

- [Pianificazione della rete e della migrazione per Office 365](https://aka.ms/tune)
    
## <a name="next-step"></a>Passaggio successivo

[Progettazione di rete per Microsoft Azure PaaS](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>Vedere anche

[Rete di Microsoft Cloud per Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Risorse sull'architettura IT di Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

