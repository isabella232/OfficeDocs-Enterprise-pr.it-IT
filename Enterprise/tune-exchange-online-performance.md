---
title: Ottimizzare le prestazioni di Exchange Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/14/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: In questo articolo contiene suggerimenti generali e collegamenti ad altre risorse che informazioni utili migliorare le prestazioni di Exchange Online.
ms.openlocfilehash: 20a3a61517212df88cb380ade47c268c429e52a8
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541483"
---
# <a name="tune-exchange-online-performance"></a>Ottimizzare le prestazioni di Exchange Online

In questo articolo contiene suggerimenti generali e collegamenti ad altre risorse che informazioni utili migliorare le prestazioni di Exchange Online. In questo articolo fa parte del progetto di [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune) .
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Aspetti da considerare per migliorare le prestazioni di Exchange Online

Per migliorare la velocità di migrazione e ridurre i vincoli di larghezza di banda dell'organizzazione di Exchange Online, considerare quanto segue:
  
- **Ridurre le dimensioni delle cassette postali.** Cassette postali di dimensioni più piccole migliorano la velocità di migrazione. 
    
- **Utilizzare le funzionalità per spostare la cassetta postale con una distribuzione ibrida di Exchange.** Con una distribuzione ibrida di Exchange, la posta offline (sotto forma di file .OST) non deve essere scaricata nuovamente dopo la migrazione a Exchange Online. In questo modo vengono ridotti in modo significativo i requisiti di larghezza di banda per il download. 
    
- **Pianificare gli spostamenti di cassette postali in modo che avvengano durante i periodi di traffico Internet scarso e utilizzo locale scarso di Exchange.** Quando si pianificano gli spostamenti, tenere presente che le richieste di migrazione vengono inviate al proxy di replica della cassetta postale e potrebbero non verificarsi immediatamente. 
    
- **Utilizzare popouts snella per Outlook sul web.** Popouts snella fornire dimensioni inferiori, meno versioni di memoria di alcuni messaggi di posta elettronica in Microsoft Edge o Internet Explorer mediante il rendering di alcuni componenti del server. Per ulteriori informazioni, vedere [utilizzo popouts snella per ridurre la memoria utilizzata durante la lettura di messaggi di posta elettronica](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).
    
Per ulteriori informazioni sulle prestazioni della migrazione di Exchange, vedere [prestazioni della migrazione a Office 365 e le procedure consigliate](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).
  

