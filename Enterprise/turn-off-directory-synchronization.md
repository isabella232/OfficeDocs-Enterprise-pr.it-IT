---
title: Disabilitare la sincronizzazione della directory per Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Informazioni su come utilizzare PowerShell per disattivare la sincronizzazione della directory per Office 365
ms.openlocfilehash: f47209dd8b6be47b7ae7a4b63a9fae38c5cb498f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541351"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="79668-103">Disabilitare la sincronizzazione della directory per Office 365</span><span class="sxs-lookup"><span data-stu-id="79668-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="79668-p101">È possibile utilizzare PowerShell per disattivare la sincronizzazione della directory. Tuttavia, non è consigliabile disattivare la sincronizzazione delle directory come un passaggio di risoluzione dei problemi. Se è necessaria assistenza nella risoluzione dei problemi di sincronizzazione della directory, vedere l'articolo di [correzione dei problemi con la sincronizzazione delle directory per Office 365](fix-problems-with-directory-synchronization.md) .</span><span class="sxs-lookup"><span data-stu-id="79668-p101">You can use PowerShell to turn off directory synchronization. However, it is not recommended that you turn off directory synchronization as a troubleshooting step. If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="79668-107">[Supporto di contatto](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) per i prodotti di business, se necessario.</span><span class="sxs-lookup"><span data-stu-id="79668-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="79668-108">Consente di disattivare la sincronizzazione delle directory</span><span class="sxs-lookup"><span data-stu-id="79668-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="79668-109">Per disattivare la sincronizzazione delle Directory:</span><span class="sxs-lookup"><span data-stu-id="79668-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="79668-p102">Per prima cosa, installare il software necessario e connettersi alla sottoscrizione Office 365. Per istruzioni per l'altro, vedere [connettersi a Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span><span class="sxs-lookup"><span data-stu-id="79668-p102">First, install the required software and connect to your Office 365 subscription. For instructions for both, see [connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span></span>
    
2. <span data-ttu-id="79668-112">Utilizzare [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) per disattivare la sincronizzazione delle directory:</span><span class="sxs-lookup"><span data-stu-id="79668-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```