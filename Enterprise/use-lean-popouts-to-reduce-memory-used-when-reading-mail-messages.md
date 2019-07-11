---
title: Utilizzo di Lean popout per ridurre la memoria utilizzata per la lettura dei messaggi di posta elettronica
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/8/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: In questo articolo sono contenute informazioni per migliorare le prestazioni di download dei messaggi in Outlook sul Web.
ms.openlocfilehash: a9070d9aefc8e4c223667848b4af5c06518de076
ms.sourcegitcommit: 6b4c3a11ef7000480463d43a7a4bc2ced063efce
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "35616809"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Utilizzo di Lean popout per ridurre la memoria utilizzata per la lettura dei messaggi di posta elettronica

In questo articolo sono contenute informazioni per migliorare le prestazioni di download dei messaggi in Outlook sul Web. Questo articolo fa parte del progetto di [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune) .
   
In qualità di amministratore globale di Office 365, è possibile configurare Outlook sul Web per la distribuzione di *Lean popout* , una versione di alcuni messaggi di posta elettronica di Microsoft Edge o Internet Explorer meno intensiva per la memoria. Quando Lean popout sono configurati per Outlook sul Web, i componenti di rendering sul fianco del server vengono caricati in modo da ottimizzare le prestazioni. 
  
> [!NOTE]
> Al 2018 marzo, Lean popout non è attualmente disponibile per i messaggi che specificano le restrizioni relative ai diritti di utilizzo, ad esempio Information Rights Management (IRM). 
  
Queste funzionalità continueranno a funzionare nella finestra principale, ma non sono disponibili in Lean popout:
  
- Componenti aggiuntivi di Outlook
    
- Presenza di Skype for business
    
 **Per configurare Lean popout per tutti gli utenti all'interno dell'organizzazione di Office 365**
  
1. [Connettersi a Exchange Online tramite Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).
    
2. Eseguire il cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) con il parametro LeanPopoutEnabled, come indicato di seguito: 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  Ad esempio, per abilitare Lean popout per tutti gli utenti dell'organizzazione:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  Per disabilitare Lean popout per tutti gli utenti dell'organizzazione:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


