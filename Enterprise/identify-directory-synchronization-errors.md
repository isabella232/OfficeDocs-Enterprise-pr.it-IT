---
title: Visualizzare gli errori di sincronizzazione della directory in Office 365
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Informazioni su come visualizzare gli errori di sincronizzazione di directory nell'interfaccia di amministrazione di Office 365.
ms.openlocfilehash: 62f1135568261eccf0e7e66b78c5aaff966c7281
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541267"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="933be-103">Visualizzare gli errori di sincronizzazione della directory in Office 365</span><span class="sxs-lookup"><span data-stu-id="933be-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="933be-p101">È possibile visualizzare gli errori di sincronizzazione di directory nell'interfaccia di amministrazione di Office 365. Vengono visualizzati solo gli errori di oggetti utente. Per visualizzare gli errori tramite PowerShell, vedere [oggetti identità con DirSyncProvisioningErrors](https://go.microsoft.com/fwlink/p/?LinkId=798300).</span><span class="sxs-lookup"><span data-stu-id="933be-p101">You can view directory synchronization errors in the Office 365 admin center. Only the User object errors are displayed. To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://go.microsoft.com/fwlink/p/?LinkId=798300).</span></span>

<span data-ttu-id="933be-107">Dopo la visualizzazione, vedere [risoluzione dei problemi relativi alla sincronizzazione della directory per Office 365](fix-problems-with-directory-synchronization.md) per correggere eventuali problemi identificati.</span><span class="sxs-lookup"><span data-stu-id="933be-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="933be-108">Visualizzare gli errori di sincronizzazione di directory nell'interfaccia di amministrazione</span><span class="sxs-lookup"><span data-stu-id="933be-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="933be-109">Per visualizzare gli eventuali errori nell'interfaccia di amministrazione:</span><span class="sxs-lookup"><span data-stu-id="933be-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="933be-110">Accedere a Office 365 con l'account di lavoro o della scuola.</span><span class="sxs-lookup"><span data-stu-id="933be-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="933be-111">Passare al [Centro di amministrazione su Office 365](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span><span class="sxs-lookup"><span data-stu-id="933be-111">Go to the [About the Office 365 admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="933be-112">Nella Home **page** verrà visualizzato sezioni **Lo stato di DirSync** .</span><span class="sxs-lookup"><span data-stu-id="933be-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![Lo stato di DirSync affiancate nella visualizzazione Anteprima di amministrazione centrale](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="933be-114">Nella finestra affiancata, scegliere **Lo stato di DirSync** per passare alla pagina **Dello stato di sincronizzazione delle Directory** .</span><span class="sxs-lookup"><span data-stu-id="933be-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="933be-115">Nella parte inferiore della pagina è possibile visualizzare se sono presenti errori di DirSync.</span><span class="sxs-lookup"><span data-stu-id="933be-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![Nella pagina dello stato di sincronizzazione delle Directory è possibile visualizzare se vi sono errori di oggetti di DirSync](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="933be-117">Scegliere **è stato rilevato gli errori di DirSync oggetto** per passare a una descrizione dettagliata degli errori di sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="933be-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="933be-118">Inoltre consente di passare alla pagina di **DirSync errori** se si sceglie **è stato rilevato errori oggetti DirSync** nella porzione **lo stato di DirSync** .</span><span class="sxs-lookup"><span data-stu-id="933be-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![Pagina di errori di DirSync](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="933be-120">Nella pagina **DirSync errori** , scegliere uno degli errori elencati per visualizzare il riquadro dei dettagli con le informazioni sugli errori e suggerimenti su come risolvere il problema.</span><span class="sxs-lookup"><span data-stu-id="933be-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
