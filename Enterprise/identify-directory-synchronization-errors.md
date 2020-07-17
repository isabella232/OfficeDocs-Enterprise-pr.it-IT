---
title: Visualizzare gli errori di sincronizzazione della directory in Microsoft 365
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Informazioni su come visualizzare gli errori di sincronizzazione della directory nell'interfaccia di amministrazione di Microsoft 365.
ms.openlocfilehash: 57ca9ce125679931adcca93621474cec9ee9b82f
ms.sourcegitcommit: 3349fdaff646f5f7d92c22565402dfc22c12d2ed
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2020
ms.locfileid: "44842078"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a><span data-ttu-id="e7fad-103">Visualizzare gli errori di sincronizzazione della directory in Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="e7fad-103">View directory synchronization errors in Microsoft 365</span></span>

<span data-ttu-id="e7fad-104">È possibile visualizzare gli errori di sincronizzazione della directory nell'interfaccia di amministrazione di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e7fad-104">You can view directory synchronization errors in the Microsoft 365 admin center.</span></span> <span data-ttu-id="e7fad-105">Vengono visualizzati solo gli errori degli oggetti utente.</span><span class="sxs-lookup"><span data-stu-id="e7fad-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="e7fad-106">Per visualizzare gli errori con PowerShell, vedere [identificare gli oggetti con DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span><span class="sxs-lookup"><span data-stu-id="e7fad-106">To view errors with PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a><span data-ttu-id="e7fad-107">Visualizzare gli errori di sincronizzazione della directory nell'interfaccia di amministrazione di Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="e7fad-107">View directory synchronization errors in the Microsoft 365 admin center</span></span>

<span data-ttu-id="e7fad-108">Per visualizzare gli eventuali errori nell'interfaccia di amministrazione di Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="e7fad-108">To view any errors in the Microsoft 365 admin center:</span></span>
  
1. <span data-ttu-id="e7fad-109">Accedere all'interfaccia di [amministrazione di Microsoft 365](https://admin.microsoft.com) con un account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="e7fad-109">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) with a global administrator account.</span></span> 
    
2. <span data-ttu-id="e7fad-110">Nella **Home** page verrà visualizzata la scheda di **Gestione utente** .</span><span class="sxs-lookup"><span data-stu-id="e7fad-110">On the **Home** page, you'll see the **User management** card.</span></span> 
    
    ![La scheda di gestione utente nell'interfaccia di amministrazione di Microsoft 365](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. <span data-ttu-id="e7fad-112">Sulla scheda, scegliere **Sync Errors** in **Azure ad Connect** per visualizzare gli errori nella pagina **errori di sincronizzazione della directory** .</span><span class="sxs-lookup"><span data-stu-id="e7fad-112">On the card, choose **Sync errors** under **Azure AD Connect** to see the errors on the **Directory sync errors** page.</span></span>   
    
    ![Un esempio della pagina errori di sincronizzazione della directory](media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. <span data-ttu-id="e7fad-114">Scegliere uno degli errori per visualizzare il riquadro dei dettagli con informazioni sull'errore e suggerimenti su come risolverlo.</span><span class="sxs-lookup"><span data-stu-id="e7fad-114">Choose any of the errors to display the details pane with information about the error and tips on how to fix it.</span></span>

   ![Esempio dei dettagli di un errore di sincronizzazione della directory](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
<span data-ttu-id="e7fad-116">Dopo la visualizzazione, vedere risolvere i problemi relativi alla [sincronizzazione della directory per Microsoft 365](fix-problems-with-directory-synchronization.md) per correggere eventuali problemi identificati.</span><span class="sxs-lookup"><span data-stu-id="e7fad-116">After viewing, see [fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>

