---
title: Utilizzo di Lean popout per ridurre la memoria utilizzata per la lettura dei messaggi di posta elettronica
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
description: In questo articolo sono contenute informazioni per migliorare le prestazioni di download dei messaggi in Outlook sul Web.
ms.openlocfilehash: 55cbdec3dc994f3301afaf1bf0a261de446d522a
ms.sourcegitcommit: a35d23929bfbfd956ee853b5e828b36e2978bf36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2019
ms.locfileid: "33655780"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="67f7a-103">Utilizzo di Lean popout per ridurre la memoria utilizzata per la lettura dei messaggi di posta elettronica</span><span class="sxs-lookup"><span data-stu-id="67f7a-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="67f7a-104">In questo articolo sono contenute informazioni per migliorare le prestazioni di download dei messaggi in Outlook sul Web.</span><span class="sxs-lookup"><span data-stu-id="67f7a-104">This article contains information for improving message download performance in Outlook on the web.</span></span> <span data-ttu-id="67f7a-105">Questo articolo fa parte del progetto di [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="67f7a-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="67f7a-106">In qualità di amministratore globale di Office 365, è possibile configurare Outlook sul Web per la distribuzione di *Lean popout* , una versione di alcuni messaggi di posta elettronica di Microsoft Edge o Internet Explorer meno intensiva per la memoria.</span><span class="sxs-lookup"><span data-stu-id="67f7a-106">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer.</span></span> <span data-ttu-id="67f7a-107">Quando Lean popout sono configurati per Outlook sul Web, i componenti di rendering sul fianco del server vengono caricati in modo da ottimizzare le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="67f7a-107">When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="67f7a-108">Al 2018 marzo, Lean popout non è attualmente disponibile per i messaggi che specificano le restrizioni relative ai diritti di utilizzo, ad esempio Information Rights Management (IRM).</span><span class="sxs-lookup"><span data-stu-id="67f7a-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="67f7a-109">Queste funzionalità continueranno a funzionare nella finestra principale, ma non sono disponibili in Lean popout:</span><span class="sxs-lookup"><span data-stu-id="67f7a-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="67f7a-110">Componenti aggiuntivi di Outlook</span><span class="sxs-lookup"><span data-stu-id="67f7a-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="67f7a-111">Presenza di Skype for business</span><span class="sxs-lookup"><span data-stu-id="67f7a-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="67f7a-112">**Per configurare Lean popout per tutti gli utenti all'interno dell'organizzazione di Office 365**</span><span class="sxs-lookup"><span data-stu-id="67f7a-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="67f7a-113">[Connettersi a Exchange Online tramite Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span><span class="sxs-lookup"><span data-stu-id="67f7a-113">[Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="67f7a-114">Eseguire il cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) con il parametro LeanPopoutEnabled, come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="67f7a-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  <span data-ttu-id="67f7a-115">Ad esempio, per abilitare Lean popout per tutti gli utenti dell'organizzazione:</span><span class="sxs-lookup"><span data-stu-id="67f7a-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  <span data-ttu-id="67f7a-116">Per disabilitare Lean popout per tutti gli utenti dell'organizzazione:</span><span class="sxs-lookup"><span data-stu-id="67f7a-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


