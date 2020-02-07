---
title: Visualizzare gli errori di sincronizzazione della directory in Office 365
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
ms.openlocfilehash: e270b7f1bc29d952cd07a7b3430a1a9a50b67783
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840173"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a>Visualizzare gli errori di sincronizzazione della directory in Office 365

È possibile visualizzare gli errori di sincronizzazione della directory nell'interfaccia di [amministrazione di Microsoft 365](https://admin.microsoft.com). Vengono visualizzati solo gli errori degli oggetti utente. Per visualizzare gli errori tramite PowerShell, vedere [identificare gli oggetti con DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

Dopo la visualizzazione, vedere risolvere i problemi relativi alla [sincronizzazione della directory per Office 365](fix-problems-with-directory-synchronization.md) per correggere eventuali problemi identificati.
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>Visualizzare gli errori di sincronizzazione della directory nell'interfaccia di amministrazione

Per visualizzare gli errori nell'interfaccia di amministrazione:
  
1. Accedere a Office 365 con l'account di lavoro o della scuola. 
    
2. Accedere all'interfaccia [di amministrazione](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).
    
3. Nella **Home** page verrà visualizzato il riquadro **stato dirsync** . 
    
    ![Riquadro Stato DirSync nell'anteprima dell'interfaccia di amministrazione](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. Nel riquadro, scegliere **stato dirsync** per passare alla pagina **stato sincronizzazione directory** . 
    
    Nella parte inferiore della pagina è possibile vedere se sono presenti errori di DirSync.
    
    ![Nella pagina stato sincronizzazione directory è possibile vedere se sono presenti errori degli oggetti DirSync](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    Scegliere gli **errori degli oggetti dirsync trovati** per passare a una visualizzazione dettagliata degli errori di sincronizzazione della directory. 
    
    > [!NOTE]
    > È anche possibile passare alla pagina **errori dirsync** se si sceglie di **trovare gli errori degli oggetti dirsync** sul riquadro di **stato dirsync** . 
  
![Pagina errori DirSync](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. Nella pagina **errori dirsync** scegliere uno degli errori elencati per visualizzare il riquadro dei dettagli con informazioni sull'errore e suggerimenti su come risolverlo. 
