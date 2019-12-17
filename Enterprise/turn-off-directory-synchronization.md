---
title: Disattivare la sincronizzazione della directory per Office 365
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
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Informazioni su come utilizzare PowerShell per disattivare la sincronizzazione della directory per Office 365
ms.openlocfilehash: de7cfcbc11ed281e412c68674b808613b3421041
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072398"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a>Disattivare la sincronizzazione della directory per Office 365
È possibile utilizzare PowerShell per disattivare la sincronizzazione della directory. Tuttavia, non è consigliabile disattivare la sincronizzazione della directory come passaggio per la risoluzione dei problemi. Se si necessita di assistenza per la risoluzione dei problemi relativi alla sincronizzazione della directory, vedere l'articolo [relativo alla correzione della sincronizzazione della directory per Office 365](fix-problems-with-directory-synchronization.md) . 
  
Se necessario, [contattare il supporto](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) per i prodotti aziendali.
  
## <a name="turn-off-directory-synchronization"></a>Disattivare la sincronizzazione della directory  
Per disattivare la sincronizzazione della directory:
  
1. Innanzitutto, installare il software necessario e connettersi alla sottoscrizione di Office 365. Per istruzioni su entrambi, vedere [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).
    
2. Utilizzare [set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) per disabilitare la sincronizzazione della directory: 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```