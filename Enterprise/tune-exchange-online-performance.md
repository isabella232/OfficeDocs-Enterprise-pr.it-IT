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
# <a name="tune-exchange-online-performance"></a><span data-ttu-id="36cc3-103">Ottimizzare le prestazioni di Exchange Online</span><span class="sxs-lookup"><span data-stu-id="36cc3-103">Tune Exchange Online performance</span></span>

<span data-ttu-id="36cc3-p101">In questo articolo contiene suggerimenti generali e collegamenti ad altre risorse che informazioni utili migliorare le prestazioni di Exchange Online. In questo articolo fa parte del progetto di [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="36cc3-p101">This article contains general tips and links to other resources that tell you how to improve performance of Exchange Online. This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a><span data-ttu-id="36cc3-106">Aspetti da considerare per migliorare le prestazioni di Exchange Online</span><span class="sxs-lookup"><span data-stu-id="36cc3-106">Things to consider in order to improve Exchange Online performance</span></span>

<span data-ttu-id="36cc3-107">Per migliorare la velocità di migrazione e ridurre i vincoli di larghezza di banda dell'organizzazione di Exchange Online, considerare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="36cc3-107">To improve the speed of migration and reduce your organization's bandwidth constraints for Exchange Online, consider the following:</span></span>
  
- <span data-ttu-id="36cc3-p102">**Ridurre le dimensioni delle cassette postali.** Cassette postali di dimensioni più piccole migliorano la velocità di migrazione.</span><span class="sxs-lookup"><span data-stu-id="36cc3-p102">**Reduce mailbox sizes.** Smaller mailbox size improves migration speed.</span></span> 
    
- <span data-ttu-id="36cc3-p103">**Utilizzare le funzionalità per spostare la cassetta postale con una distribuzione ibrida di Exchange.** Con una distribuzione ibrida di Exchange, la posta offline (sotto forma di file .OST) non deve essere scaricata nuovamente dopo la migrazione a Exchange Online. In questo modo vengono ridotti in modo significativo i requisiti di larghezza di banda per il download.</span><span class="sxs-lookup"><span data-stu-id="36cc3-p103">**Use the mailbox move capabilities with an Exchange hybrid deployment.** With an Exchange hybrid deployment, offline mail (in the form of .OST files) does not require re-download when migrating to Exchange Online. This significantly reduces your download bandwidth requirements.</span></span> 
    
- <span data-ttu-id="36cc3-p104">**Pianificare gli spostamenti di cassette postali in modo che avvengano durante i periodi di traffico Internet scarso e utilizzo locale scarso di Exchange.** Quando si pianificano gli spostamenti, tenere presente che le richieste di migrazione vengono inviate al proxy di replica della cassetta postale e potrebbero non verificarsi immediatamente.</span><span class="sxs-lookup"><span data-stu-id="36cc3-p104">**Schedule mailbox moves to occur during periods of low Internet traffic and low on-premises Exchange use.** When scheduling moves, migration requests are submitted to the mailbox replication proxy and may not take place immediately.</span></span> 
    
- <span data-ttu-id="36cc3-p105">**Utilizzare popouts snella per Outlook sul web.** Popouts snella fornire dimensioni inferiori, meno versioni di memoria di alcuni messaggi di posta elettronica in Microsoft Edge o Internet Explorer mediante il rendering di alcuni componenti del server. Per ulteriori informazioni, vedere [utilizzo popouts snella per ridurre la memoria utilizzata durante la lettura di messaggi di posta elettronica](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span><span class="sxs-lookup"><span data-stu-id="36cc3-p105">**Use lean popouts for Outlook on the web.** Lean popouts provide smaller, less memory-intensive versions of certain email messages in Microsoft Edge or Internet Explorer by rendering some components on the server. For more information, see [Use lean popouts to reduce memory used when reading mail messages](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span></span>
    
<span data-ttu-id="36cc3-118">Per ulteriori informazioni sulle prestazioni della migrazione di Exchange, vedere [prestazioni della migrazione a Office 365 e le procedure consigliate](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span><span class="sxs-lookup"><span data-stu-id="36cc3-118">For more information about Exchange migration performance, see [Office 365 migration performance and best practices](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span></span>
  

