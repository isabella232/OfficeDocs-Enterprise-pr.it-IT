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
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Informazioni su come utilizzare PowerShell per disattivare la sincronizzazione della directory per Office 365
ms.openlocfilehash: 4fbfb6b9e3fcb1512fc4aa9c3d8ee6c37682e58a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085075"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="a5674-103">Disabilitare la sincronizzazione della directory per Office 365</span><span class="sxs-lookup"><span data-stu-id="a5674-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="a5674-p101">È possibile utilizzare PowerShell per disattivare la sincronizzazione della directory. Tuttavia, non è consigliabile disattivare la sincronizzazione della directory come passaggio per la risoluzione dei problemi. Se si necessita di assistenza per la risoluzione dei problemi relativi alla sincronizzazione della directory, vedere l'articolo [relativo alla correzione della sincronizzazione della directory per Office 365](fix-problems-with-directory-synchronization.md) .</span><span class="sxs-lookup"><span data-stu-id="a5674-p101">You can use PowerShell to turn off directory synchronization. However, it is not recommended that you turn off directory synchronization as a troubleshooting step. If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="a5674-107">Se necessario, [contattare il supporto](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) per i prodotti aziendali.</span><span class="sxs-lookup"><span data-stu-id="a5674-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="a5674-108">Disattiva la sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="a5674-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="a5674-109">Per disattivare la sincronizzazione della directory:</span><span class="sxs-lookup"><span data-stu-id="a5674-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="a5674-p102">Innanzitutto, installare il software necessario e connettersi alla sottoscrizione di Office 365. Per istruzioni su entrambi, vedere [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span><span class="sxs-lookup"><span data-stu-id="a5674-p102">First, install the required software and connect to your Office 365 subscription. For instructions for both, see [connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span></span>
    
2. <span data-ttu-id="a5674-112">Utilizzare [set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) per disabilitare la sincronizzazione della directory:</span><span class="sxs-lookup"><span data-stu-id="a5674-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```