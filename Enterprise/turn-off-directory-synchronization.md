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
# <a name="turn-off-directory-synchronization-for-office-365"></a>Disabilitare la sincronizzazione della directory per Office 365
È possibile utilizzare PowerShell per disattivare la sincronizzazione della directory. Tuttavia, non è consigliabile disattivare la sincronizzazione delle directory come un passaggio di risoluzione dei problemi. Se è necessaria assistenza nella risoluzione dei problemi di sincronizzazione della directory, vedere l'articolo di [correzione dei problemi con la sincronizzazione delle directory per Office 365](fix-problems-with-directory-synchronization.md) . 
  
[Supporto di contatto](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) per i prodotti di business, se necessario.
  
## <a name="turn-off-directory-synchronization"></a>Consente di disattivare la sincronizzazione delle directory  
Per disattivare la sincronizzazione delle Directory:
  
1. Per prima cosa, installare il software necessario e connettersi alla sottoscrizione Office 365. Per istruzioni per l'altro, vedere [connettersi a Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).
    
2. Utilizzare [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) per disattivare la sincronizzazione delle directory: 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```