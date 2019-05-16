---
title: Visualizzare gli errori di sincronizzazione della directory in Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Informazioni su come visualizzare gli errori di sincronizzazione della directory nell'interfaccia di amministrazione di Microsoft 365.
ms.openlocfilehash: b1cda68590131967ea2fe91506c8e71769f4c32b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067522"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="b0acb-103">Visualizzare gli errori di sincronizzazione della directory in Office 365</span><span class="sxs-lookup"><span data-stu-id="b0acb-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="b0acb-104">È possibile visualizzare gli errori di sincronizzazione della directory nell'interfaccia di [amministrazione di Microsoft 365](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="b0acb-104">You can view directory synchronization errors in the [Microsoft 365 admin center](https://admin.microsoft.com).</span></span> <span data-ttu-id="b0acb-105">Vengono visualizzati solo gli errori degli oggetti utente.</span><span class="sxs-lookup"><span data-stu-id="b0acb-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="b0acb-106">Per visualizzare gli errori tramite PowerShell, vedere [identificare gli oggetti con DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span><span class="sxs-lookup"><span data-stu-id="b0acb-106">To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="b0acb-107">Dopo la visualizzazione, vedere risolvere i problemi relativi alla [sincronizzazione della directory per Office 365](fix-problems-with-directory-synchronization.md) per correggere eventuali problemi identificati.</span><span class="sxs-lookup"><span data-stu-id="b0acb-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="b0acb-108">Visualizzare gli errori di sincronizzazione della directory nell'interfaccia di amministrazione</span><span class="sxs-lookup"><span data-stu-id="b0acb-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="b0acb-109">Per visualizzare gli errori nell'interfaccia di amministrazione:</span><span class="sxs-lookup"><span data-stu-id="b0acb-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="b0acb-110">Accedere a Office 365 con l'account di lavoro o della scuola.</span><span class="sxs-lookup"><span data-stu-id="b0acb-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="b0acb-111">Accedere all'interfaccia [di amministrazione](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span><span class="sxs-lookup"><span data-stu-id="b0acb-111">Go to the [About the admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="b0acb-112">Nella **Home** page verrà visualizzato il riquadro **stato dirsync** .</span><span class="sxs-lookup"><span data-stu-id="b0acb-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![Riquadro di stato DirSync nell'anteprima dell'interfaccia di amministrazione](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="b0acb-114">Nel riquadro, scegliere **stato dirsync** per passare alla pagina **stato sincronizzazione directory** .</span><span class="sxs-lookup"><span data-stu-id="b0acb-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="b0acb-115">Nella parte inferiore della pagina è possibile vedere se sono presenti errori di DirSync.</span><span class="sxs-lookup"><span data-stu-id="b0acb-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![Nella pagina stato sincronizzazione directory è possibile vedere se sono presenti errori degli oggetti DirSync](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="b0acb-117">Scegliere gli **errori degli oggetti dirsync trovati** per passare a una visualizzazione dettagliata degli errori di sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="b0acb-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="b0acb-118">È anche possibile passare alla pagina **errori dirsync** se si sceglie di **trovare gli errori degli oggetti dirsync** sul riquadro di **stato dirsync** .</span><span class="sxs-lookup"><span data-stu-id="b0acb-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![Pagina errori DirSync](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="b0acb-120">Nella pagina **errori dirsync** scegliere uno degli errori elencati per visualizzare il riquadro dei dettagli con informazioni sull'errore e suggerimenti su come risolverlo.</span><span class="sxs-lookup"><span data-stu-id="b0acb-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
