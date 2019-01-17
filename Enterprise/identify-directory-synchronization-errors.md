---
title: Visualizzare gli errori di sincronizzazione della directory in Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
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
ms.openlocfilehash: 8beeeebbb24936abd7c93f4c04c0fa4e27c85c12
ms.sourcegitcommit: c5ee713709d76f519cb77de0e12c435d8409f571
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2019
ms.locfileid: "28327338"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a>Visualizzare gli errori di sincronizzazione della directory in Office 365

È possibile visualizzare gli errori di sincronizzazione di directory nell'interfaccia di amministrazione di Office 365. Vengono visualizzati solo gli errori di oggetti utente. Per visualizzare gli errori tramite PowerShell, vedere [oggetti identità con DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

Dopo la visualizzazione, vedere [risoluzione dei problemi relativi alla sincronizzazione della directory per Office 365](fix-problems-with-directory-synchronization.md) per correggere eventuali problemi identificati.
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>Visualizzare gli errori di sincronizzazione di directory nell'interfaccia di amministrazione

Per visualizzare gli eventuali errori nell'interfaccia di amministrazione:
  
1. Accedere a Office 365 con l'account aziendale o dell'istituto di istruzione. 
    
2. Passare al [Centro di amministrazione su Office 365](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).
    
3. Nella Home **page** verrà visualizzato sezioni **Lo stato di DirSync** . 
    
    ![Lo stato di DirSync affiancate nella visualizzazione Anteprima di amministrazione centrale](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. Nella finestra affiancata, scegliere **Lo stato di DirSync** per passare alla pagina **Dello stato di sincronizzazione delle Directory** . 
    
    Nella parte inferiore della pagina è possibile visualizzare se sono presenti errori di DirSync.
    
    ![Nella pagina dello stato di sincronizzazione delle Directory è possibile visualizzare se vi sono errori di oggetti di DirSync](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    Scegliere **è stato rilevato gli errori di DirSync oggetto** per passare a una descrizione dettagliata degli errori di sincronizzazione della directory. 
    
    > [!NOTE]
    > Inoltre consente di passare alla pagina di **DirSync errori** se si sceglie **è stato rilevato errori oggetti DirSync** nella porzione **lo stato di DirSync** . 
  
![Pagina di errori di DirSync](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. Nella pagina **DirSync errori** , scegliere uno degli errori elencati per visualizzare il riquadro dei dettagli con le informazioni sugli errori e suggerimenti su come risolvere il problema. 
