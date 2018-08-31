---
title: Utilizzare popouts snella per ridurre la memoria utilizzata durante la lettura di messaggi di posta
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/8/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: In questo articolo sono contenute informazioni per migliorare le prestazioni di download di messaggi in Outlook sul web.
ms.openlocfilehash: 07c427793c1cd60d25020a1ab49855ed1bc77cf6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541193"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Utilizzare popouts snella per ridurre la memoria utilizzata durante la lettura di messaggi di posta

In questo articolo sono contenute informazioni per migliorare le prestazioni di download di messaggi in Outlook sul web. In questo articolo fa parte del progetto di [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune) .
   
Amministratore globale di Office 365, è possibile configurare Outlook sul web per il recapito *popouts snella* , valore più piccolo, meno versione memoria di alcuni messaggi di posta elettronica in Microsoft Edge o Internet Explorer. Quando popouts snella sono configurate per Outlook sul web, viene eseguito il rendering componenti sul lato server vengono caricati che ottimizzare le prestazioni. 
  
> [!NOTE]
> A partire da marzo 2018 popouts snella non sono attualmente disponibili per i messaggi che specificano limitazioni dei diritti di utilizzo, ad esempio Information Rights Management (IRM). 
  
Queste funzionalità continueranno a funzionare nella finestra principale, ma non sono disponibili nel popouts snella:
  
- Componenti aggiuntivi di Outlook
    
- Skype per presenza aziendale
    
 **Per configurare snella popouts per tutti gli utenti all'interno dell'organizzazione Office 365**
  
1. [Connessione a Exchange Online tramite Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).
    
2. Eseguire il cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) con il parametro LeanPopoutEnabled come indicato di seguito: 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

    Ad esempio, per abilitare snella popouts per tutti gli utenti nell'organizzazione:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

    Per disattivare snella popouts per tutti gli utenti nell'organizzazione:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


