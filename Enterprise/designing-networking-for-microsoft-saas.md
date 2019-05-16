---
title: Progettazione di rete per Microsoft SaaS
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
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: "Riepilogo: informazioni su come ottimizzare la rete per l'accesso ai servizi SaaS di Microsoft, tra cui Office 365, Microsoft Intune e Dynamics 365."
ms.openlocfilehash: 695e3255bf1afcb5314985caccb15ead410d93f6
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067772"
---
# <a name="designing-networking-for-microsoft-saas"></a>Progettazione di rete per Microsoft SaaS

 **Riepilogo:** Informazioni su come ottimizzare la rete per l'accesso ai servizi SaaS di Microsoft, tra cui Office 365, Microsoft Intune e Dynamics 365.
  
Ottimizzare la rete per servizi SaaS Microsoft richiede la configurazione di dispositivi interni e periferici per instradare le diverse categorie di traffico ai servizi SaaS Microsoft.
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>Passaggi per preparare la rete per i servizi SaaS di Microsoft

Seguire questa procedura per ottimizzare la rete per i servizi SaaS di Microsoft:
  
1. Consultare la sezione **Procedura per predisporre la rete per i servizi cloud Microsoft** in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).
    
2. Aggiungere una connessione Internet a ciascuno degli uffici.
    
3. Verificare che gli ISP per tutte le connessioni Internet utilizzino un server DNS con un indirizzo IP locale.
    
4. Esaminare i tornanti di rete, le destinazioni intermedie, ad esempio i servizi di sicurezza basati sul cloud, ed eliminarli se possibile.
    
5. Configurare i dispositivi perimetrali in modo da ignorare l'elaborazione per le categorie ottimizzazione e Consenti del traffico SaaS di Microsoft.

## <a name="optimizing-traffic-to-microsofts-saas-services"></a>Ottimizzazione del traffico per i servizi SaaS di Microsoft    

Esistono tre categorie di traffico SaaS Microsoft:

- Ottimizzazione

  Necessario per la connettività a tutti i servizi SaaS di Microsoft e rappresentare oltre il 75% della larghezza di banda, delle connessioni e del volume di dati di Microsoft SaaS.

- Consenti

  Necessario per la connettività a specifici servizi e caratteristiche di Microsoft SaaS, ma non sono sensibili alle prestazioni e alla latenza di rete come quelli della categoria optimize.

- Predefinita

  Rappresentano i servizi e le dipendenze di Microsoft SaaS che non richiedono alcuna ottimizzazione. È possibile gestire il traffico di categoria predefinito come il traffico Internet normale.


**Figura 1: configurazione consigliata per il traffico SaaS di Microsoft per tutte le sedi**

![Figura 1: configurazione consigliata per il traffico SaaS di Microsoft per tutte le sedi](media/Network-Poster/SaaS1.png)

Nella figura 1 viene illustrata la configurazione consigliata di tutti gli uffici, tra cui le succursali e quelle regionali o centrali, in cui:

- La categoria **predefinita** e il traffico Internet generale vengono instradati agli uffici che dispongono di server proxy e di altri dispositivi perimetrali per garantire la protezione contro i rischi di sicurezza basati su Internet.
- **Ottimizzare** e **consentire** il traffico delle categorie viene inoltrato direttamente al server perimetrale di Microsoft Network front-end più vicino all'ufficio che contiene l'utente che esegue la connessione, ignorando il proxy e altri dispositivi perimetrali.

I dispositivi di rete wide area (SD-WAN) definiti dal software nelle succursali distaccano il traffico in modo che: 

- La categoria **predefinita** e il traffico Internet generale passano a un ufficio centrale o regionale sulla backbone WAN. 
- **Ottimizzare** e **consentire** il traffico di categoria passa all'ISP che fornisce la connessione Internet locale.
  
Per ulteriori informazioni, vedere:
  
- [Principi di connettività di rete](https://aka.ms/expressrouteoffice365)

- [Pianificazione della rete e della migrazione per Office 365](https://aka.ms/tune)
    
## <a name="next-step"></a>Passaggio successivo

[Progettazione di rete per Microsoft Azure PaaS](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>Vedere anche

[Rete di Microsoft Cloud per Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

