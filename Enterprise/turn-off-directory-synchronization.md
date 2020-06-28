---
title: Disattiva la sincronizzazione della directory per Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Informazioni su come utilizzare PowerShell per disattivare la sincronizzazione della directory per Microsoft 365
ms.openlocfilehash: 935d7e26c7b99aba876500e6b9d428557aed5b9c
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906209"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="4456e-103">Disattiva la sincronizzazione della directory per Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="4456e-103">Turn off directory synchronization for Microsoft 365</span></span>
<span data-ttu-id="4456e-104">È possibile utilizzare PowerShell per disattivare la sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="4456e-104">You can use PowerShell to turn off directory synchronization.</span></span> <span data-ttu-id="4456e-105">Tuttavia, non è consigliabile disattivare la sincronizzazione della directory come passaggio per la risoluzione dei problemi.</span><span class="sxs-lookup"><span data-stu-id="4456e-105">However, it is not recommended that you turn off directory synchronization as a troubleshooting step.</span></span> <span data-ttu-id="4456e-106">Se si necessita di assistenza per la risoluzione dei problemi relativi alla sincronizzazione della directory, vedere l'articolo [relativo alla correzione della sincronizzazione della directory per Microsoft 365](fix-problems-with-directory-synchronization.md) .</span><span class="sxs-lookup"><span data-stu-id="4456e-106">If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="4456e-107">Se necessario, [contattare il supporto](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) per i prodotti aziendali.</span><span class="sxs-lookup"><span data-stu-id="4456e-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="4456e-108">Disattivare la sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="4456e-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="4456e-109">Per disattivare la sincronizzazione della directory:</span><span class="sxs-lookup"><span data-stu-id="4456e-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="4456e-110">Innanzitutto, installare il software necessario e connettersi alla sottoscrizione Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="4456e-110">First, install the required software and connect to your Microsoft 365 subscription.</span></span> <span data-ttu-id="4456e-111">Per istruzioni, vedere [connessione con il modulo di Microsoft Azure Active Directory per Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="4456e-111">For instructions, see [Connect with the Microsoft Azure Active Directory Module for Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
2. <span data-ttu-id="4456e-112">Utilizzare [set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) per disabilitare la sincronizzazione della directory:</span><span class="sxs-lookup"><span data-stu-id="4456e-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```
