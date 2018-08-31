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
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="77366-103">Utilizzare popouts snella per ridurre la memoria utilizzata durante la lettura di messaggi di posta</span><span class="sxs-lookup"><span data-stu-id="77366-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="77366-p101">In questo articolo sono contenute informazioni per migliorare le prestazioni di download di messaggi in Outlook sul web. In questo articolo fa parte del progetto di [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="77366-p101">This article contains information for improving message download performance in Outlook on the web. This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="77366-p102">Amministratore globale di Office 365, è possibile configurare Outlook sul web per il recapito *popouts snella* , valore più piccolo, meno versione memoria di alcuni messaggi di posta elettronica in Microsoft Edge o Internet Explorer. Quando popouts snella sono configurate per Outlook sul web, viene eseguito il rendering componenti sul lato server vengono caricati che ottimizzare le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="77366-p102">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer. When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="77366-108">A partire da marzo 2018 popouts snella non sono attualmente disponibili per i messaggi che specificano limitazioni dei diritti di utilizzo, ad esempio Information Rights Management (IRM).</span><span class="sxs-lookup"><span data-stu-id="77366-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="77366-109">Queste funzionalità continueranno a funzionare nella finestra principale, ma non sono disponibili nel popouts snella:</span><span class="sxs-lookup"><span data-stu-id="77366-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="77366-110">Componenti aggiuntivi di Outlook</span><span class="sxs-lookup"><span data-stu-id="77366-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="77366-111">Skype per presenza aziendale</span><span class="sxs-lookup"><span data-stu-id="77366-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="77366-112">**Per configurare snella popouts per tutti gli utenti all'interno dell'organizzazione Office 365**</span><span class="sxs-lookup"><span data-stu-id="77366-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="77366-113">[Connessione a Exchange Online tramite Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span><span class="sxs-lookup"><span data-stu-id="77366-113">[Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="77366-114">Eseguire il cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) con il parametro LeanPopoutEnabled come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="77366-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

    <span data-ttu-id="77366-115">Ad esempio, per abilitare snella popouts per tutti gli utenti nell'organizzazione:</span><span class="sxs-lookup"><span data-stu-id="77366-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

    <span data-ttu-id="77366-116">Per disattivare snella popouts per tutti gli utenti nell'organizzazione:</span><span class="sxs-lookup"><span data-stu-id="77366-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


